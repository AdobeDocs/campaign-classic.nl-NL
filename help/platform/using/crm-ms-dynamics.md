---
product: campaign
title: Campagne - Microsoft Dynamics CRM Connector
description: Leer hoe u Campagne en Microsoft Dynamics kunt verbinden
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Microsoft CRM Integration
exl-id: 26737940-b3ce-425c-9604-f4cefd19afaa
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '1111'
ht-degree: 2%

---

# Connect-campagne en Microsoft Dynamics 365{#connect-to-msdyn}



Op deze pagina leert u hoe u Campaign Classic kunt verbinden met **Microsoft Dynamics CRM 365**.

Mogelijke implementatie vindt plaats via **Web-API** (aanbevolen). Zie [het onderstaande gedeelte](#microsoft-dynamics-implementation-step) voor meer informatie over het instellen van de verbinding met Microsoft Dynamics.

Gegevenssynchronisatie wordt uitgevoerd via een specifieke werkstroomactiviteit. [Meer informatie](../../platform/using/crm-data-sync.md).

## Implementatiestappen{#microsoft-dynamics-implementation-steps}

Microsoft Dynamics 365 verbinden om met Adobe Campaign te werken via **Web-API** dient u de volgende stappen toe te passen:

In Microsoft Dynamics CRM:
1. Client-id voor Microsoft Dynamics ophalen
1. Sleutel-id voor Microsoft Dynamics Certificate en Key ID genereren
1. Machtigingen configureren
1. Een App-gebruiker maken
1. De persoonlijke sleutel coderen

[Meer informatie in dit gedeelte](#config-crm-microsoft)

In Campaign Classic:
1. Een nieuwe externe account maken
1. De externe account configureren met Microsoft Dynamics-instellingen
1. Gebruik de configuratietovenaar om lijsten in kaart te brengen en opsommingen te synchroniseren
1. De synchronisatieworkflow maken

[Meer informatie in dit gedeelte](#configure-acc-for-microsoft)


>[!CAUTION]
> Wanneer u Adobe Campaign verbindt met Microsoft Dynamics, kunt u het volgende niet doen:
> * Plug-ins installeren die het gedrag van CRM kunnen wijzigen en compatibiliteitsproblemen met Adobe Campaign kunnen veroorzaken
> * Meerdere opsommingen selecteren


## Microsoft Dynamics CRM configureren {#config-crm-microsoft}

Als u het toegangstoken en de sleutels voor het instellen van de account wilt genereren, moet u zich aanmelden bij [Microsoft Azure Directory](https://portal.azure.com) met een **Algemene beheerder** referenties. Voer vervolgens de hieronder beschreven stappen uit.

### Client-id voor Microsoft Dynamics ophalen {#get-client-id-microsoft}

Om identiteitskaart van de Cliënt te krijgen, moet u een App in Azure Actieve Folder registreren. Client ID is hetzelfde als Application ID.

1. Navigeren naar **Azure Active Directory > App-registraties** en klik op  **Nieuwe toepassingsregistratie**.
1. Geef een unieke naam die u kunt helpen bij het identificeren van een instantie, zoals **adobecampagne`<instance identifier>`**.
1. Kies **Toepassingstype** als **Web-app / API**.
1. Gebruiken `http://localhost` for **Aanmeldings-URL**.

Wanneer u het bestand hebt opgeslagen, krijgt u een **Toepassings-id** Dit is de client-id voor campagne.

Meer informatie in [deze pagina](https://docs.microsoft.com/powerapps/developer/common-data-service/walkthrough-register-app-azure-active-directory).

### Sleutel-id voor Microsoft Dynamics Certificate en Key ID genereren {#config-certificate-key-id}

Om de **Id van certificaatsleutel (customKeyIdentifier)** en de **Sleutel-id (keyId)** volgt u de onderstaande stappen:

1. Navigeren naar **Azure Active Directory > App-registraties** en selecteer de toepassing die eerder is gemaakt.
1. Klikken op **Certificaten en geheim**.
1. Klikken op **Certificaat uploaden** en bladert en uploadt u vervolgens het gegenereerde openbare certificaat.
1. U kunt open gebruiken om het certificaat te genereren.

   Bijvoorbeeld:

   ```
   - openssl req -x509 -sha256 -nodes -days 365 -newkey rsa:2048 -keyout '<'private key name'>' -out '<'public certificate name'>
   ```

   >[!NOTE]
   >
   >U kunt hier het aantal dagen wijzigen `-days 365`, in de voorbeeldcode voor een langere geldigheidsperiode van het certificaat.

1. U zult dan het in base64 moeten coderen. Om dit te doen, kunt u de hulp van een Codeur gebruiken Base64 of de bevellijn gebruiken `base64 -w0 private.key` voor Linux.

1. Klik op de knop **Manifest** koppeling om de **Id van certificaatsleutel (customKeyIdentifier)** en de **Sleutel-id (keyId)**.

De **Id van certificaatsleutel (customKeyIdentifier)** en de **Sleutel-id (keyId)** zal later nodig zijn om uw externe rekening van CRM van de Dynamica van Microsoft te vormen gebruikend het Certificaat **[!UICONTROL CRM O-Auth type]**.

### Machtigingen configureren {#config-permissions-microsoft}

**Stap 1**: Configureer de **Vereiste machtigingen** voor de app die is gemaakt.

1. Navigeren naar **Azure Active Directory > App-registraties** en selecteer de toepassing die eerder is gemaakt.
1. Klikken **Instellingen** links boven.
1. Aan **Vereiste machtigingen**, klikt u op **Toevoegen** en **Selecteer een API > Dynamics CRM Online**.
1. Klikken **Selecteren**, enable **De Dynamica 365 van de toegang als organisatiegebruikers** selectievakje en klik op **Selecteren**.
1. Selecteer vervolgens in uw app de optie **Manifest** onder de **Beheren** -menu.

1. Van de **Manifest** editor, stelt de `allowPublicClient` eigenschap van `null` tot `true` en klik op **Opslaan**.

**Stap 2**: Toelating beheerder

1. Navigeren naar **Azure Active Directory > Enterprise-toepassingen**.

1. Selecteer de toepassing waaraan u admin toestemming voor de gehele huurder wilt verlenen.

1. Selecteer in het menu van het linkerdeelvenster de optie **Machtigingen** krachtens **Beveiliging**.

1. Klikken **Toelating beheerder**.

Raadpleeg voor meer informatie hierover [Azure-documentatie](https://docs.microsoft.com/azure/active-directory/manage-apps/grant-admin-consent#grant-admin-consent-from-the-azure-portal).

### Een App-gebruiker maken {#create-app-user-microsoft}

>[!NOTE]
>
> Deze stap is optioneel met **[!UICONTROL Password credentials]** verificatie.

De gebruiker van de app is de gebruiker die de hierboven geregistreerde toepassing zal gebruiken. Wijzigingen die met de bovenstaande app zijn aangebracht in Microsoft Dynamics, worden via deze gebruiker doorgevoerd.

**Stap 1**: Een niet-interactieve gebruiker maken in de azure actieve map

1. Klikken **Azure Active Directory > Users** en klik op **Nieuwe gebruiker**.
1. Geef een juiste naam die u wilt gebruiken en de gebruikersnaam moet een e-mailindeling zijn.
1. Kies **Dynamics 365 Administrator** in de **Maprol**.

**Stap 2**: Een juiste licentie toewijzen aan de nieuwe gebruiker

1. Van [Microsoft Azure](https://portal.azure.com), klikt u op **Admin-app**.
1. Ga naar **Gebruikers > Actieve gebruikers** en klik op de nieuwe gebruiker.
1. Klikken op **Productlicenties bewerken** en selecteert u de **Dynamics 365 Customer Engagement Plan**.
1. Klikken **Sluiten**.

**Stap 3**: Creeer een toepassingsgebruiker op Dynamica CRM

1. Van [Microsoft Azure](https://portal.azure.com), navigeer naar **Instellingen > Beveiliging > Gebruikers**.
1. Klik in de vervolgkeuzelijst en selecteer **Toepassingsgebruikers** en klik op **Nieuw**.
1. Dezelfde gebruikersnaam gebruiken als de gebruiker die hierboven in de actieve map is gemaakt

   >[!NOTE]
   >
   >Als dezelfde naam wordt gebruikt, treedt een dubbele toetsfout op. Gebruik dus een andere gebruikersnaam en ga verder totdat u bevestigt dat deze stap nodig is.

1. Wijs het **Toepassings-id** for [de toepassing die u eerder hebt gemaakt](#get-client-id-microsoft).
1. Klikken op **Rollen beheren** en kiest u **Systeembeheerder** rol voor de gebruiker.

## Campaign configureren {#configure-acc-for-microsoft}

>[!NOTE]
>
> Na de ontmanteling van [RDS uit Microsoft](https://docs.microsoft.com/previous-versions/dynamicscrm-2016/developers-guide/dn281891%28v=crm.8%29#microsoft-dynamics-crm-2011-endpoint), zijn de On-premise en Bureau 365 types van plaatsingen van CRM niet meer compatibel met Campagne. Adobe Campaign ondersteunt nu alleen Web API-implementatie voor de CRM-versie **Dynamische CRM 365**. [Meer informatie](../../rn/using/deprecated-features.md#crm-connectors).

Om de Dynamiek 365 van Microsoft en Campagne te verbinden, moet u tot stand brengen en een specifieke vorm vormen **[!UICONTROL External Account]** in Campaign.

1. Ga naar **[!UICONTROL Administration > Platform > External accounts]**.

1. Selecteer **[!UICONTROL Microsoft Dynamics CRM]** externe rekening. Schakel de optie **[!UICONTROL Enabled]** in.

1. Vul de gegevens in die nodig zijn om verbinding te maken met Microsoft Dynamics 365 en Campaign.

   >[!NOTE]
   >
   >Microsoft Dynamics CRM External account configuration met elke **[!UICONTROL CRM O-Auth type]** is gedetailleerd [in deze sectie](../../installation/using/external-accounts.md#microsoft-dynamics-crm-external-account).

   ![](assets/crm-ms-dynamics-ext-account.png)

1. Klik op de koppeling **[!UICONTROL Microsoft CRM configuration wizard...]**. Adobe Campaign detecteert automatisch de tabellen in de gegevenssjabloon voor Microsoft Dynamics.

   ![](assets/crm_connectors_msdynamics_02.png)

1. Selecteer de tabellen die u wilt herstellen.

   ![](assets/crm_connectors_msdynamics_03.png)

1. Klikken **[!UICONTROL Next]** om het corresponderende schema te gaan maken.

   ![](assets/crm_connectors_msdynamics_04.png)

   >[!NOTE]
   >
   >Als u de configuratie wilt goedkeuren, moet u de verbinding met de Adobe Campaign-console verbreken of opnieuw tot stand brengen.

   U kunt controleren of het overeenkomende gegevensschema beschikbaar wordt in Adobe Campaign.

   ![](assets/crm_connectors_msdynamics_05.png)

1. Klik op de knop **[!UICONTROL Synchronizing enumerations...]** koppeling om opsommingen te synchroniseren tussen Adobe Campaign en Microsoft Dynamics.

   ![](assets/crm_connectors_msdynamics_06.png)

Campagne en Microsoft Dynamics zijn nu verbonden. U kunt gegevenssynchronisatie tussen de twee systemen instellen. Meer informatie in het dialoogvenster [Gegevenssynchronisatie](../../platform/using/crm-data-sync.md) sectie.

>[!NOTE]
>
> U moet ervoor zorgen om aan de lijst van gewenste personen twee URLs toe te voegen: de server-URL en `login.microsoftonline.com` in de serverconfiguratie. Voor meer informatie over hoe te om toestemmingen URL te vormen, verwijs naar dit [page](../../installation/using/url-permissions.md).

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
| MultiSelect Option-set | Nee |
