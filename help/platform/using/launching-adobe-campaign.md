---
product: campaign
title: Adobe Campaign starten
description: Adobe Campaign starten
feature: Access Management, Permissions
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: 4d9c5b24-83a2-4495-a56c-5bc376d69703
source-git-commit: b4059e43d98643f0f8b5b3f68f03e10b755e8ba3
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 1%

---

# Adobe Campaign starten {#launching-adobe-campaign}

De console van de Cliënt van de campagne is een rijke cliënt die u toelaat om met uw de toepassingsserver(s) van de Campagne te verbinden. Leer hoe te om de cliëntconsole in [ te downloaden en te vormen deze pagina ](../../installation/using/installing-the-client-console.md).

>[!CAUTION]
>
>Controleer uw systeem en hulpmiddelverenigbaarheid met de Console van de Cliënt van Adobe Campaign in de [ matrijs van de Verenigbaarheid ](../../rn/using/compatibility-matrix.md#ClientConsoleoperatingsystems)

## Adobe Campaign starten {#starting-adobe-campaign}

U kunt Adobe Campaign starten door **[!UICONTROL Start / All Programs / Adobe Campaign v.X / Adobe Campaign client console]** te selecteren.

In het verbindingsvenster van de clientconsole kunt u bestaande databases selecteren of configureren en er verbinding mee maken met een gebruikersnaam en wachtwoord:

![](assets/acc-logon.png)

## Verbinding maken met Adobe Campaign {#connecting-to-adobe-campaign}

### Verbinding maken met uw Adobe ID

Campagnegebruikers maken via hun Adobe ID verbinding met de Adobe Campaign-console via Adobe Identity Management System (IMS). Ze kunnen dezelfde id gebruiken voor alle Adobe-oplossingen. De verbinding wordt bewaard wanneer het gebruiken van Adobe Campaign met andere oplossingen. Leer meer over Adobe IMS [ op deze pagina ](https://helpx.adobe.com/enterprise/using/identity.html).

Om Campaign Classic v7 verbinding met de Dienst van Identity Management van Adobe (IMS) te vormen, verwijs naar [ deze pagina ](../../integrations/using/about-adobe-id.md).

Zodra de configuratie wordt gedaan, leer hoe te om met uw Adobe ID in de [ Campagne v8 (console) documentatie ](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/new/connect){target=_blank} te verbinden.


### Verbinding maken met een aanmelding/wachtwoord

U kunt ook verbinding maken met een toegewezen aanmelding/wachtwoord. Deze verbinding wordt de campagne &#39;Native Authentificatie&#39; genoemd:

1. Voer de id van de operatoraccount in het veld **[!UICONTROL Login]** in.

   De beheerder van uw Adobe Campaign-platform geeft uw id op.

1. Voer uw wachtwoord in het veld **[!UICONTROL Password]** in.

   De eerste keer u tot het gegevensbestand toegang hebt, is uw wachtwoord dat aan u door de beheerder wordt gegeven. Nadat u verbinding hebt gemaakt, kunt u uw wachtwoord wijzigen via het menu **[!UICONTROL Tools > Change password...]** . De details op exploitanten en de verbindingen zijn beschikbaar in [ beheer van de Toegang ](../../platform/using/access-management.md).

1. Klik op **[!UICONTROL LOG IN]** om te bevestigen.

U kunt tot [ werkruimte van Adobe Campaign ](../../platform/using/adobe-campaign-workspace.md) nu toegang hebben.

## Verbindingen instellen {#setting-up-connections}

U hebt toegang tot de instellingen voor de serververbinding via de koppeling boven de invoerzone.

![](assets/s_ncs_user_connections_management.png)

Leer hoe te opstellingsverbindingen in de [ Campagne v8 (console) documentatie ](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/new/connect#create-your-connection){target=_blank}.

## Operatoren en machtigingen {#operators-and-permissions}

De id&#39;s en wachtwoorden van operatoren die toegang hebben tot de software en hun respectievelijke machtigingen worden gedefinieerd door uw Adobe Campaign-systeembeheerder in het knooppunt **[!UICONTROL Administration > Access management > Operators]** van de Adobe Campaign-structuur.

Deze functionaliteit is gedetailleerd in de [ het beheerssectie van de Toegang ](../../platform/using/access-management.md).

## Adobe Campaign-versie ophalen {#getting-your-campaign-version}

Via het menu **[!UICONTROL Help > About...]** hebt u toegang tot de volgende informatie:

* **versie** aantal voor de cliëntconsole van de Campagne en toepassingsserver
* **bouwt** aantal voor de cliëntconsole van de Campagne en toepassingsserver
* een link naar Adobe Customer Care
* koppelingen naar het privacybeleid, de Gebruiksvoorwaarden en het Cookies-beleid van Adobe

![](assets/about-acc.png)

Telkens wanneer u het team van de klantendienst van Adobe bereikt, moet u het versieaantal verstrekken en aantal van uw de cliëntconsole en toepassingsserver van Adobe Campaign bouwen.

