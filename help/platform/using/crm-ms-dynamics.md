---
product: campaign
title: Campagne - de Schakelaar van CRM van de Dynamica van Microsoft
description: Connect-campagne en Microsoft Dynamics
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 26737940-b3ce-425c-9604-f4cefd19afaa
source-git-commit: 7adde72f615e7c697fa2284235e180c29bc6d470
workflow-type: tm+mt
source-wordcount: '1097'
ht-degree: 1%

---

# Connect-campagne en Microsoft Dynamics 365{#connect-to-msdyn}

In deze pagina, zult u leren hoe te om Campaign Classic met **de Dynamica CRM 365** van Microsoft te verbinden.

De mogelijke plaatsing is via **Web API** (geadviseerd). Verwijs naar [de sectie onder](#microsoft-dynamics-implementation-step) om stappen te leren aan opstelling de verbinding met de Dynamica van Microsoft.

Gegevenssynchronisatie wordt uitgevoerd via een specifieke werkstroomactiviteit. [Meer info](../../platform/using/crm-data-sync.md).

## Implementatiestappen{#microsoft-dynamics-implementation-steps}

Als u Microsoft Dynamics 365 wilt verbinden om te werken met Adobe Campaign via **Web API**, moet u de volgende stappen toepassen:

In Microsoft Dynamics CRM:
1. Client-id voor Microsoft Dynamics ophalen
1. Sleutel-id voor certificaat en sleutel-id voor Microsoft Dynamics genereren
1. Machtigingen configureren
1. Een App-gebruiker maken
1. De persoonlijke sleutel coderen

[Meer informatie in deze sectie](#config-crm-microsoft)

In Campaign Classic:
1. Een nieuwe externe account maken
1. De externe account configureren met Microsoft Dynamics-instellingen
1. Gebruik de configuratietovenaar om lijsten in kaart te brengen en opsommingen te synchroniseren
1. De synchronisatieworkflow maken

[Meer informatie in deze sectie](#configure-acc-for-microsoft)


>[!CAUTION]
> Wanneer u Adobe Campaign verbindt met Microsoft Dynamics, kunt u het volgende niet doen:
> * Plug-ins installeren die het gedrag van CRM kunnen wijzigen en compatibiliteitsproblemen met Adobe Campaign kunnen veroorzaken
> * Meerdere opsommingen selecteren


## Microsoft Dynamics CRM configureren {#config-crm-microsoft}

Als u het toegangstoken en de sleutels voor het instellen van de account wilt genereren, moet u zich aanmelden bij [Microsoft Azure Directory](https://portal.azure.com) met behulp van een **Global Administrator**-referenties. Voer vervolgens de hieronder beschreven stappen uit.

### Client-id voor Microsoft Dynamics ophalen {#get-client-id-microsoft}

Om identiteitskaart van de Cliënt te krijgen, moet u een App in Azure Actieve Folder registreren. Client ID is hetzelfde als Application ID.

1. Navigeer naar **Azure Active Directory > App Registrations** en klik op **New Application Registration**.
1. Geef een unieke naam die u kunt helpen bij het identificeren van een instantie, zoals **adobecampagne`<instance identifier>`**.
1. Kies **Toepassingstype** als **Web-app / API**.
1. Gebruik `http://localhost` voor **Sign-On URL**.

Zodra u sparen, krijgt u **toepassings identiteitskaart** die het Herkenningsteken van de Cliënt voor Campagne is.

Meer informatie vindt u op [deze pagina](https://docs.microsoft.com/en-us/powerapps/developer/common-data-service/walkthrough-register-app-azure-active-directory).

### Sleutel-id voor certificaat en sleutel-id voor Microsoft Dynamics genereren {#config-certificate-key-id}

Voer de volgende stappen uit om de **Certificaatsleutel-id (customKeyIdentifier)** en de **Sleutel-id (keyId)** op te halen:

1. Navigeer naar **Azure Active Directory > App Registrations** en selecteer de toepassing die eerder is gemaakt.
1. Klik op **Certificaten en Geheim**.
1. Klik op **Certificaat uploaden** en doorblader en upload dan uw geproduceerd openbaar certificaat.
1. U kunt open gebruiken om het certificaat te genereren.

   Bijvoorbeeld:

   ```
   - openssl req -x509 -sha256 -nodes -days 365 -newkey rsa:2048 -keyout '<'private key name'>' -out '<'public certificate name'>
   ```

   >[!NOTE]
   >
   >U kunt het aantal dagen, hier `-days 365`, in de codesteekproef voor een langere periode van de certificaatgeldigheid veranderen.

1. U zult dan het in base64 moeten coderen. Om dit te doen, kunt u de hulp van een Codeur gebruiken Base64 of de bevellijn `base64 -w0 private.key` voor Linux gebruiken.

1. Klik op de **Manifest**-koppeling om de **Certificaat sleutelid (customKeyIdentifier)** en **Sleutel ID (keyId)** te krijgen.

**Certificaat zeer belangrijke herkenningsteken (customKeyIdentifier)** en **Zeer belangrijke identiteitskaart (keyId)** zullen later worden vereist om uw externe rekening van CRM van de Dynamica van Microsoft te vormen gebruikend het Certificaat **[!UICONTROL CRM O-Auth type]**.

### Machtigingen configureren {#config-permissions-microsoft}

**Stap 1**: Configureer de  **vereiste** machtigingen voor de app die is gemaakt.

1. Navigeer naar **Azure Active Directory > App Registrations** en selecteer de toepassing die eerder is gemaakt.
1. Klik op **Instellingen** linksboven.
1. Klik op **Vereiste machtigingen** op **Toevoegen** en **Selecteer een API > Dynamische CRM online**.
1. Klik **Selecteer**, schakel **Access Dynamics 365 in als gebruikers van de organisatie** en klik op **Select**.
1. Selecteer vervolgens in uw app **Manifest** onder het menu **Beheren**.

1. Stel in de **Manifest**-editor de `allowPublicClient`-eigenschap in van `null` naar `true` en klik op **Save**.

**Stap 2**: Toelating beheerder

1. Navigeer naar **Azure Active Directory > Enterprise applications**.

1. Selecteer de toepassing waaraan u admin toestemming voor de gehele huurder wilt verlenen.

1. Selecteer **Machtigingen** onder **Beveiliging** in het menu van het linkerdeelvenster.

1. Klik **Beheertoestemming verlenen**.

Raadpleeg [Azure-documentatie](https://docs.microsoft.com/en-us/azure/active-directory/manage-apps/grant-admin-consent#grant-admin-consent-from-the-azure-portal) voor meer informatie hierover.

### Een App-gebruiker maken {#create-app-user-microsoft}

>[!NOTE]
>
> Deze stap is optioneel met **[!UICONTROL Password credentials]**-verificatie.

De gebruiker van de app is de gebruiker die de hierboven geregistreerde toepassing zal gebruiken. Alle wijzigingen die met de hierboven geregistreerde toepassing zijn aangebracht in Microsoft Dynamics worden doorgevoerd via deze gebruiker.

**Stap 1**: Een niet-interactieve gebruiker maken in de azure actieve map

1. Klik **Azure Active Directory > Users** en klik **New User**.
1. Geef een juiste naam die u wilt gebruiken en de gebruikersnaam moet een e-mailindeling zijn.
1. Kies **Dynamics 365 Administrator** in **Directory Role**.

**Stap 2**: Een juiste licentie toewijzen aan de nieuwe gebruiker

1. Van [Microsoft Azure](https://portal.azure.com), klik op **Admin app**.
1. Ga naar **Gebruikers > Actieve Gebruikers** en klik op de pas gecreëerde gebruiker.
1. Klik op **Productlicenties bewerken** en selecteer **Dynamics 365 Customer Engagement Plan**.
1. Klik **Close**.

**Stap 3**: Creeer een toepassingsgebruiker op Dynamica CRM

1. Navigeer vanuit [Microsoft Azure](https://portal.azure.com) naar **Instellingen > Beveiliging > Gebruikers**.
1. Klik op vervolgkeuzelijst, selecteer **Toepassingsgebruikers** en klik **Nieuw**.
1. Dezelfde gebruikersnaam gebruiken als de gebruiker die hierboven in de actieve map is gemaakt

   >[!NOTE]
   >
   >Als dezelfde naam wordt gebruikt, treedt een dubbele toetsfout op. Gebruik dus een andere gebruikersnaam en ga verder totdat u bevestigt dat deze stap nodig is.

1. Wijs **Toepassings-id** toe voor [de toepassing die u eerder hebt gemaakt](#get-client-id-microsoft).
1. Klik op **Rollen beheren** en kies de rol **Systeembeheerder** aan de gebruiker.

## Campaign configureren {#configure-acc-for-microsoft}

>[!NOTE]
>
> Post de buitenbedrijfstelling van [RDS van Microsoft](https://docs.microsoft.com/en-us/previous-versions/dynamicscrm-2016/developers-guide/dn281891(v=crm.8)?redirectedfrom=MSDN#microsoft-dynamics-crm-2011-endpoint), de On-premise en Bureau 365 types van de plaatsingen van CRM zijn niet meer compatibel met Campagne. Adobe Campaign ondersteunt nu alleen Web API-implementatie voor de CRM-versie **Dynamic CRM 365**. [Meer info](../../rn/using/deprecated-features.md#crm-connectors).

Om de Dynamiek 365 van Microsoft en Campagne te verbinden, moet u een specifieke **[!UICONTROL External Account]** in Campagne creëren en vormen.

1. Ga naar **[!UICONTROL Administration > Platform > External accounts]**.

1. Selecteer de externe account **[!UICONTROL Microsoft Dynamics CRM]**. Schakel de optie **[!UICONTROL Enabled]** in.

1. Vul de informatie in die wordt vereist om de Dynamica 365 van Microsoft en Campagne te verbinden.

   >[!NOTE]
   >
   >De Externe rekeningsconfiguratie van CRM van de Dynamica van Microsoft van CRM met elke **[!UICONTROL CRM O-Auth type]** is gedetailleerd [in deze sectie](../../installation/using/external-accounts.md#microsoft-dynamics-crm-external-account).

   ![](assets/crm-ms-dynamics-ext-account.png)

1. Klik op de koppeling **[!UICONTROL Microsoft CRM configuration wizard...]**. Adobe Campaign ontdekt automatisch de lijsten van het de gegevensmalplaatje van de Dynamica van Microsoft.

   ![](assets/crm_connectors_msdynamics_02.png)

1. Selecteer de tabellen die u wilt herstellen.

   ![](assets/crm_connectors_msdynamics_03.png)

1. Klik **[!UICONTROL Next]** beginnen het overeenkomstige schema tot stand te brengen.

   ![](assets/crm_connectors_msdynamics_04.png)

   >[!NOTE]
   >
   >Als u de configuratie wilt goedkeuren, moet u de verbinding met de Adobe Campaign-console verbreken of opnieuw tot stand brengen.

   U kunt controleren of het overeenkomende gegevensschema beschikbaar wordt in Adobe Campaign.

   ![](assets/crm_connectors_msdynamics_05.png)

1. Klik op de koppeling **[!UICONTROL Synchronizing enumerations...]** om opsommingen te synchroniseren tussen Adobe Campaign en Microsoft Dynamics.

   ![](assets/crm_connectors_msdynamics_06.png)

Campagne en de Dynamica van Microsoft zijn nu verbonden. U kunt gegevenssynchronisatie tussen de twee systemen instellen. Meer informatie vindt u in de sectie [Gegevenssynchronisatie](../../platform/using/crm-data-sync.md).

>[!NOTE]
>
> U moet ervoor zorgen om aan de lijst van gewenste personen twee URLs toe te voegen: de server-URL en `login.microsoftonline.com` in de serverconfiguratie.

## Ondersteunde veldgegevenstypen {#ms-dyn-supported-types}

Voor Microsoft Dynamics 365 worden de ondersteunde/niet-ondersteunde kenmerktypen hieronder vermeld:


| Type kenmerk | Ondersteund |
| --------------------------------------------------------------------------------- | --------- |
| Basistypen: boolean, datetime, decimal, float, double, integer, bigint , string | Ja |
| Geld (als dubbel) | Ja |
| memo, entiteitsnaam, primarykey, uniqueidentifier (als tekenreeksen) | Ja |
| Status, picklist (we slaan de mogelijke waarden op in opsommingen), state (string) | Ja |
| owner (als string) | Ja |
| Opzoeken (alleen zoeken naar verwijzingen naar één entiteit) | Ja |
| klant | Nee |
| Betreffende | Nee |
| PartyList | Nee |
| ManagedProperty | Nee |
