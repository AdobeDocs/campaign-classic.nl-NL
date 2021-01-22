---
solution: Campaign Classic
product: campaign
title: Microsoft Dynamics CRM Connector
description: Connect-campagne en Microsoft Dynamics
audience: platform
content-type: reference
topic-tags: connectors
translation-type: tm+mt
source-git-commit: 521bc3bf9b2507947007d7f458679275d407f910
workflow-type: tm+mt
source-wordcount: '958'
ht-degree: 0%

---


# Connect-campagne en Microsoft Dynamics 365{#connect-to-msdyn}

In deze pagina, zult u leren hoe te om Campaign Classic met **de Dynamica CRM 365** van Microsoft te verbinden.

Mogelijke implementaties zijn:

* via **Web API** (aanbevolen). Verwijs naar [de sectie onder](#microsoft-dynamics-implementation-step) om stappen te leren aan opstelling de verbinding met de Dynamica van Microsoft.
* met **Office 365**. Raadpleeg [deze video](#microsoft-dynamics-office-365) om belangrijke stappen te leren om deze integratie in te stellen.
* voor een **On-premise** plaatsing, pas Bureau 365 belangrijkste stappen toe.

Gegevenssynchronisatie wordt uitgevoerd via een specifieke werkstroomactiviteit. [Meer informatie](../../platform/using/crm-data-sync.md).


>[!NOTE]
>
> De systeemversie van CRM die compatibel is met Campagne wordt vermeld in [Compatibility matrix](../../rn/using/compatibility-matrix.md#CRMconnectors).


## Implementatiestappen{#microsoft-dynamics-implementation-steps}

Als u Microsoft Dynamics 365 wilt verbinden om te werken met Adobe Campaign via **Web API**, moet u de volgende stappen toepassen:

In Microsoft Dynamics CRM:
1. Client-id voor Microsoft Dynamics ophalen
1. Microsoft Dynamics Client Secret genereren
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

>



## Microsoft Dynamics CRM {#config-crm-microsoft} configureren

Als u het toegangstoken en de sleutels voor het instellen van de account wilt genereren, moet u zich aanmelden bij [Microsoft Azure Directory](https://portal.azure.com) met behulp van een **Global Administrator**-referenties. Voer vervolgens de hieronder beschreven stappen uit.

### Client-id voor Microsoft Dynamics {#get-client-id-microsoft} ophalen

Om identiteitskaart van de Cliënt te krijgen, moet u een App in Azure Actieve Folder registreren. Client ID is hetzelfde als Application ID.

1. Navigeer naar **Azure Active Directory > App Registrations** en klik op **New Application Registration**.
1. Geef een unieke naam die u kunt helpen bij het identificeren van een instantie, zoals **adobecampagne`<instance identifier>`**.
1. Kies **Toepassingstype** als **Web-app / API**.
1. Gebruik `http://localhost` voor **Sign-On URL**.

Zodra u sparen, krijgt u **toepassings identiteitskaart** die het Herkenningsteken van de Cliënt voor Campagne is.

Meer informatie vindt u op [deze pagina](https://docs.microsoft.com/en-us/powerapps/developer/common-data-service/walkthrough-register-app-azure-active-directory).

### Microsoft Dynamics Client Secret {#config-client-secret-microsoft} genereren

Het clientgeheim is de sleutel die uniek is voor de client-id. Volg onderstaande stappen om de id van de certificaatsleutel op te halen:

1. Navigeer naar **Azure Active Directory > App Registrations** en selecteer de toepassing die eerder is gemaakt.
1. Klik op **Certificaten en Geheim**.
1. Klik op **Certificaat uploaden** en doorblader en upload dan uw geproduceerd openbaar certificaat.
1. U kunt open gebruiken om het certificaat te genereren.

   Bijvoorbeeld:

   ```
   - openssl req -x509 -sha256 -nodes -days 365 -newkey rsa:2048 -keyout '<'private key name'>' -out '<'public certificate name'>
   ```

1. Klik op de koppeling **manifest** om de **certificaatsleutel-id** en de **sleutel-id** op te halen.

### Machtigingen {#config-permissions-microsoft} configureren

U moet de **Vereiste toestemmingen** voor app vormen die werd gecreeerd.

1. Navigeer naar **Azure Active Directory > App Registrations** en selecteer de toepassing die eerder is gemaakt.
1. Klik op **Instellingen** linksboven.
1. Klik op **Vereiste machtigingen** op **Toevoegen** en **Selecteer een API > Dynamische CRM online**.
1. Klik vervolgens op **Select**, schakel **Access Dynamics 365 as organisation users** in en klik op **Select**.

### Creeer een Gebruiker {#create-app-user-microsoft}

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

## Campagne {#configure-acc-for-microsoft} configureren

Om de Dynamiek 365 van Microsoft en Campagne te verbinden, moet u een specifieke Externe Rekening in Campagne creëren en vormen.

1. Ga naar **[!UICONTROL Administration > Platform > External accounts]**.

1. Maak een nieuwe externe account en selecteer het type **[!UICONTROL Microsoft Dynamics CRM]** en de optie **[!UICONTROL Enable]**.

1. Selecteer het implementatietype **[!UICONTROL Web API]**:

   Adobe Campaign Classic steunt de Dynamica 365 REST interface met protocol OAuth voor authentificatie met **[!UICONTROL Certificate]** of **[!UICONTROL Password Credentials]**.

   Gebruik de instellingen [die eerder zijn gedefinieerd](#get-client-id-microsoft) in Azure Directory om de externe account te configureren.

   ![](assets/crm-ms-dynamics-ext-account.png)

   >[!NOTE]
   >
   >De Externe rekeningsconfiguratie van CRM van de Dynamica van Microsoft is gedetailleerd [in deze sectie](../../installation/using/external-accounts.md#microsoft-dynamics-crm-external-account).

1. Klik op de koppeling **[!UICONTROL Microsoft CRM configuration wizard...]**: Adobe Campaign ontdekt automatisch de lijsten van het de gegevensmalplaatje van de Dynamica van Microsoft.

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

## Integratie van Microsoft Dynamics CRM Office 365{#microsoft-dynamics-office-365} configureren

Bekijk deze video om te leren hoe u Dynamics 365 met Adobe Campaign Classic kunt integreren, in de context van een Office 365-implementatie.

>[!VIDEO](https://video.tv.adobe.com/v/23837?quality=12)


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
