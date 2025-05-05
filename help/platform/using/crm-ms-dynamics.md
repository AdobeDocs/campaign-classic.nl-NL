---
product: campaign
title: Campagne - Microsoft Dynamics CRM-connector
description: Leer hoe u campagne en Microsoft Dynamics kunt verbinden
feature: Microsoft CRM Integration
exl-id: 26737940-b3ce-425c-9604-f4cefd19afaa
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '1104'
ht-degree: 1%

---

# Connect-campagne en Microsoft Dynamics 365{#connect-to-msdyn}



In deze pagina, zult u leren hoe te om Campaign Classic met **te verbinden Microsoft Dynamics CRM 365**.

De mogelijke plaatsing is via **Web API** (geadviseerd). Verwijs naar [ de sectie hieronder ](#microsoft-dynamics-implementation-step) om stappen te leren aan opstelling de verbinding met Microsoft Dynamics.

Gegevenssynchronisatie wordt uitgevoerd via een toegewijde werkstroomactiviteit. [Meer informatie](../../platform/using/crm-data-sync.md).

## Implementatiestappen{#microsoft-dynamics-implementation-steps}

Om Microsoft Dynamics 365 aan het werk met Adobe Campaign via **Web API** te verbinden, moet u de volgende stappen toepassen:

In Microsoft Dynamics CRM:
1. Microsoft Dynamics-client-id ophalen
1. Sleutel-id voor certificaat en sleutel-id voor Microsoft Dynamics genereren
1. Machtigingen configureren
1. Een App-gebruiker maken
1. De persoonlijke sleutel coderen

[Meer informatie in deze sectie](#config-crm-microsoft)

In Campaign Classic:
1. Een nieuwe externe account maken
1. De externe account configureren met Microsoft Dynamics-instellingen
1. Gebruik de configuratiemedewerker om lijsten in kaart te brengen en opsommingen te synchroniseren
1. De synchronisatieworkflow maken

[Meer informatie in deze sectie](#configure-acc-for-microsoft)


>[!CAUTION]
> Wanneer u Adobe Campaign met Microsoft Dynamics verbindt, kunt u niet:
> * Plug-ins installeren die het gedrag van CRM kunnen wijzigen en compatibiliteitsproblemen met Adobe Campaign kunnen veroorzaken
> * Meerdere opsommingen selecteren

## Microsoft Dynamics CRM configureren {#config-crm-microsoft}

Om het toegangstoken en de sleutels te produceren om de rekening in te stellen, moet u login aan [ Microsoft Azure Folder ](https://portal.azure.com) gebruikend a **Globale beheerder** geloofsbrieven. Voer vervolgens de hieronder beschreven stappen uit.

### Microsoft Dynamics-client-id ophalen {#get-client-id-microsoft}

Om identiteitskaart van de Cliënt te krijgen, moet u een App in Azure Actieve Folder registreren. Client ID is hetzelfde als Application ID.

1. Navigeer aan **Azure Actieve Folder > de Registraties van de App**, en klik **Nieuwe Registratie van de Toepassing**.
1. Geef een unieke naam die kan helpen een instantie identificeren, zoals **adobecampagne`<instance identifier>`**.
1. Kies **Type van Toepassing** als **Web app / API**.
1. Gebruik `http://localhost` voor **Sign-On URL**.

Zodra u sparen, krijgt u een **identiteitskaart van de Toepassing** die het Herkenningsteken van de Cliënt voor Campagne is.

Meer informatie vindt u [op deze pagina](https://docs.microsoft.com/powerapps/developer/common-data-service/walkthrough-register-app-azure-active-directory).

### Sleutel-id voor certificaat en sleutel-id voor Microsoft Dynamics genereren {#config-certificate-key-id}

Om het **belangrijkste herkenningsteken van het Certificaat (customKeyIdentifier)** en **Zeer belangrijke identiteitskaart (keyId)** te krijgen, volg hieronder de stappen:

1. Navigeer aan **Azure Actieve Folder > de Registraties van de App** en selecteer de Toepassing die vroeger werd gecreeerd.
1. Klik op **Certificaten en Geheim**.
1. Klik op **uploadt certificaat** en doorblader en upload dan uw openbaar geproduceerd certificaat.
1. U kunt open gebruiken om het certificaat te genereren.

   Bijvoorbeeld:

   ```
   - openssl req -x509 -sha256 -nodes -days 365 -newkey rsa:2048 -keyout '<'private key name'>' -out '<'public certificate name'>
   ```

   >[!NOTE]
   >
   >U kunt het aantal dagen hier `-days 365` in het codevoorbeeld wijzigen voor een langere geldigheidsperiode van het certificaat.

1. U zult dan het in base64 moeten coderen. Hiertoe kunt u de hulp van een Base64-encoder gebruiken of de opdrachtregel `base64 -w0 private.key` voor Linux.

1. Klik op de **Duidelijke** verbinding om het **belangrijkste herkenningsteken van het Certificaat (customKeyIdentifier)** en **Zeer belangrijke identiteitskaart (keyId)** te krijgen.

Het **belangrijkste herkenningsteken van het Certificaat (customKeyIdentifier)** en **Zeer belangrijke identiteitskaart (keyId)** zal later worden vereist om uw externe rekening van Microsoft Dynamics CRM te vormen gebruikend het Certificaat **[!UICONTROL CRM O-Auth type]**.

### Machtigingen configureren {#config-permissions-microsoft}

**Stap 1**: Vorm **Vereiste Toestemmingen** voor app die werd gecreeerd.

1. Navigeer aan **Azure Actieve Folder > de Registraties van de App** en selecteer de Toepassing die vroeger werd gecreeerd.
1. Klik **Montages** op de hoogste linkerzijde.
1. Op **Vereiste Toestemmingen**, klik **&#x200B;**&#x200B;toevoegen en **selecteer online API > Dynamische CRM**.
1. Klik **Uitgezochte**, laat **Dynamica 365 van de Toegang als organisatiegebruikers** checkbox toe en klik **Uitgezochte**.
1. Dan, van uw app, selecteer **Manifest** onder **leidt** menu.

1. Van de **Manifest** redacteur, plaats het `allowPublicClient` bezit van `null` aan `true` en klik **sparen**.

**Stap 2**: De toestemming van het beheerder van de subsidie

1. Navigeer aan **Azure Actieve Folder > de toepassingen van de Onderneming**.

1. Selecteer de toepassing waaraan u admin toestemming voor de gehele huurder wilt verlenen.

1. Van het linkerpaneelmenu, uitgezochte **Toestemmingen** onder **Veiligheid**.

1. Klik **verlenen admin toestemming**.

Voor meer informatie over dit, verwijs naar [ Azure documentatie ](https://docs.microsoft.com/azure/active-directory/manage-apps/grant-admin-consent#grant-admin-consent-from-the-azure-portal).

### Een App-gebruiker maken {#create-app-user-microsoft}

>[!NOTE]
>
> Deze stap is optioneel met **[!UICONTROL Password credentials]** -verificatie.

De gebruiker van de app is de gebruiker die de hierboven geregistreerde toepassing zal gebruiken. Alle wijzigingen die met de hierboven geregistreerde toepassing zijn aangebracht in Microsoft Dynamics worden doorgevoerd via deze gebruiker.

**Stap 1**: Creeer een niet-interactieve gebruiker op azure actieve folder

1. Klik **Azure Actieve Folder > Gebruikers** en klik **Nieuwe Gebruiker**.
1. Geef een juiste naam die u wilt gebruiken en de gebruikersnaam moet een e-mailindeling zijn.
1. Kies **Beheerder 365 van de Dynamiek 365** in de **Rol van de Folder**.

**Stap 2**: Wijs een juiste vergunning aan de gecreeerde gebruiker toe

1. Van [ Microsoft Azure ](https://portal.azure.com), klik op **Admin app**.
1. Ga naar **Gebruikers > Actieve Gebruikers** en klik op de pas gecreëerde gebruiker.
1. Klik op **geef productvergunningen** uit en selecteer de **Dynamiek 365 Plan van de Betrokkenheid van de Klant**.
1. Klik **dicht**.

**Stap 3**: Creeer een toepassingsgebruiker op Dynamica CRM

1. Van [ Microsoft Azure ](https://portal.azure.com), navigeer aan **Montages > Veiligheid > Gebruikers**.
1. Klik op drop down, uitgezochte **gebruikers van de Toepassing** en klik **Nieuw**.
1. Dezelfde gebruikersnaam gebruiken als de gebruiker die hierboven in de actieve map is gemaakt

   >[!NOTE]
   >
   >Als dezelfde naam wordt gebruikt, treedt een dubbele toetsfout op. Gebruik dus een andere gebruikersnaam en ga verder totdat u bevestigt dat deze stap nodig is.
   >

1. Wijs **identiteitskaart van de Toepassing** voor [ toe de toepassing u vroeger ](#get-client-id-microsoft) creeerde.
1. Klik op **leiden Rollen** en kies de **beheerder van het Systeem** rol aan de gebruiker.

## Campagne configureren {#configure-acc-for-microsoft}

>[!NOTE]
>
> Post de ontmanteling van [ RDS van Microsoft ](https://docs.microsoft.com/previous-versions/dynamicscrm-2016/developers-guide/dn281891%28v=crm.8%29#microsoft-dynamics-crm-2011-endpoint), de On-premise en Bureau 365 types van plaatsingen van CRM zijn niet meer compatibel met Campagne. Adobe Campaign steunt nu slechts de plaatsing van Web API voor versie van CRM **Dynamische CRM 365**. [Meer informatie](../../rn/using/deprecated-features.md#crm-connectors).

Als u Microsoft Dynamics 365 en Campagne wilt verbinden, moet u een toegewezen **[!UICONTROL External Account]** maken en configureren in Campagne.

1. Navigeer naar **[!UICONTROL Administration > Platform > External accounts]** .

1. Selecteer de **[!UICONTROL Microsoft Dynamics CRM]** externe account. Schakel de optie **[!UICONTROL Enabled]** in.

1. Vul de gegevens in die nodig zijn voor de verbinding tussen Microsoft Dynamics 365 en Campagne.

   >[!NOTE]
   >
   >De Externe rekeningsconfiguratie van Microsoft Dynamics CRM met elk **[!UICONTROL CRM O-Auth type]** is gedetailleerd [ in deze sectie ](../../installation/using/external-accounts.md#microsoft-dynamics-crm-external-account).

   ![](assets/crm-ms-dynamics-ext-account.png)

1. Klik op de koppeling **[!UICONTROL Microsoft CRM configuration assistant...]** . Adobe Campaign detecteert de tabellen automatisch via de Microsoft Dynamics-gegevenssjabloon.

   ![](assets/crm_connectors_msdynamics_02.png)

1. Selecteer de tabellen die u wilt herstellen.

   ![](assets/crm_connectors_msdynamics_03.png)

1. Klik op **[!UICONTROL Next]** om het bijbehorende schema te maken.

   ![](assets/crm_connectors_msdynamics_04.png)

   >[!NOTE]
   >
   >Als u de configuratie wilt goedkeuren, moet u de verbinding met de Adobe Campaign-console verbreken of opnieuw tot stand brengen.

   U kunt controleren of het overeenkomende gegevensschema beschikbaar wordt in Adobe Campaign.

   ![](assets/crm_connectors_msdynamics_05.png)

1. Klik op de koppeling **[!UICONTROL Synchronizing enumerations...]** om opsommingen te synchroniseren tussen Adobe Campaign en Microsoft Dynamics.

   ![](assets/crm_connectors_msdynamics_06.png)

Campagne en Microsoft Dynamics zijn nu verbonden. U kunt gegevenssynchronisatie tussen de twee systemen instellen. Leer meer in de [ synchronisatie van Gegevens ](../../platform/using/crm-data-sync.md) sectie.

>[!NOTE]
>
> U moet ervoor zorgen om aan de lijst van gewenste personen twee URLs toe te voegen: server URL en `login.microsoftonline.com` in de configuratie van de Server. Voor meer informatie over hoe te om toestemmingen te vormen URL, verwijs naar deze [ pagina ](../../installation/using/url-permissions.md).

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
