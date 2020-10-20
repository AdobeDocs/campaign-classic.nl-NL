---
title: Adobe Campaign starten
seo-title: Adobe Campaign starten
description: Adobe Campaign starten
seo-description: null
page-status-flag: never-activated
uuid: c1c5bb0d-ae8e-4b0e-ab39-8b2291162557
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
discoiquuid: 6652b081-66b6-47a8-97e5-383e3251647e
translation-type: tm+mt
source-git-commit: 87ad4d4fc69d75e4367e7467ce27de29f58f9445
workflow-type: tm+mt
source-wordcount: '501'
ht-degree: 7%

---


# Adobe Campaign starten{#launching-adobe-campaign}

De console van de Cliënt van de campagne is een rijke cliënt die u toelaat om met uw de toepassingsserver(s) van de Campagne te verbinden. Leer hoe u de clientconsole op [deze pagina](../../installation/using/installing-the-client-console.md)downloadt en configureert.

## Starting Adobe Campaign {#starting-adobe-campaign}

Je kunt Adobe Campaign starten door te selecteren **[!UICONTROL Start / All Programs / Adobe Campaign v.X / Adobe Campaign client console]**.

In het verbindingsvenster van de clientconsole kunt u bestaande databases selecteren of configureren en er verbinding mee maken met een gebruikersnaam en wachtwoord:

![](assets/s_ncs_user_login.png)

## Verbinding maken met Adobe Campaign {#connecting-to-adobe-campaign}

U kunt verbinding maken met Adobe Campaign via uw Adobe ID. Raadpleeg [deze pagina](../../integrations/using/about-adobe-id.md) voor meer informatie.

U kunt ook verbinding maken met een toegewezen aanmelding/wachtwoord:

1. Voer de id van de operatoraccount in het **[!UICONTROL login]** veld in.

   De beheerder van uw Adobe Campaign-platform geeft uw id op.

1. Voer uw wachtwoord in het **[!UICONTROL Password]** veld in.

   De eerste keer u tot het gegevensbestand toegang hebt, is uw wachtwoord dat aan u door de beheerder wordt gegeven. Zodra u verbonden bent, kunt u uw wachtwoord via het **[!UICONTROL Tools > Change password...]** menu veranderen. Details over operatoren en verbindingen zijn beschikbaar in [Toegangsbeheer](../../platform/using/access-management.md).

1. Klik **[!UICONTROL Log in]** om te bevestigen.

U hebt nu toegang tot de [Adobe Campaign-werkruimte](../../platform/using/adobe-campaign-workspace.md).

## Verbindingen instellen {#setting-up-connections}

U hebt toegang tot de instellingen voor de serververbinding via de koppeling boven de invoerzone.

![](assets/s_ncs_user_connections_management.png)

In the **[!UICONTROL Connections]** window, click **[!UICONTROL Add > Connection]**.

![](assets/s_ncs_user_add_connexion.png)

Vervolgens definieert u de verbindingsinstellingen. Dit doet u als volgt:

1. Voer een naam in **[!UICONTROL Label]** om een naam toe te wijzen aan uw databaseverbinding.

1. Voeg het adres van de toepassingsserver in het **[!UICONTROL URL]** veld toe. Neem contact op met de beheerder als u de verbindings-URL niet kent.

1. Controleer **[!UICONTROL Connect with an Adobe ID]** of de operatoren verbinding maken met de console via hun Adobe ID. Raadpleeg [deze pagina](../../integrations/using/about-adobe-id.md) voor meer informatie.

1. Klik **[!UICONTROL OK]** om te valideren.

## Operatoren en machtigingen {#operators-and-permissions}

De id&#39;s en wachtwoorden van operatoren met toegang tot de software en hun respectieve machtigingen worden gedefinieerd door uw Adobe Campaign-systeembeheerder in het **[!UICONTROL Administration > Access management > Operators]** knooppunt van de Adobe Campaign-structuur.

Deze functionaliteit wordt gedetailleerd in de het beheerssectie van de [Toegang](../../platform/using/access-management.md) .

## Verbinding met Adobe Campaign verbreken {#disconnecting-from-adobe-campaign}

Als u de verbinding met Adobe Campaign wilt verbreken, gebruikt u het eerste pictogram in de pictogrambalk.

![](assets/s_ncs_user_deconnexion.png)

>[!NOTE]
>
>U kunt de toepassing ook sluiten zonder u eerst af te melden.

## Adobe Campaign-versie ophalen {#getting-your-campaign-version}

In het **[!UICONTROL Help > About...]** menu hebt u toegang tot de volgende informatie:

* **versienummer** voor de clientconsole en toepassingsserver van Campagne
* **buildnummer** voor Campagne-clientconsole en toepassingsserver
* een koppeling om contact op te nemen met de klantenservice van Adobe
* koppelingen naar het privacybeleid van Adobe, de Gebruiksvoorwaarden en het Cookies-beleid

![](assets/about-acc.png)

Wanneer u het team van de Zorg van de Adobe klant bereikt, moet u het versieaantal verstrekken en aantal van uw de cliëntconsole en toepassingsserver van de Campagne bouwen.

Als u werkt met de versie [](../../rn/using/gold-standard.md)Campaign Gold Standard, moet u ook de SHA/1-tekens delen die in het **[!UICONTROL About]** vak worden weergegeven. Voor de Gold **Standard 10-release** toont het buildnummer bijvoorbeeld de **build 9032@efd8a94**, zoals hieronder wordt getoond:

![](assets/about-acc-gs.png)

Meer informatie over Gold Standard vindt u [in dit artikel](https://helpx.adobe.com/nl/campaign/kb/gold-standard.html).

**Verwante onderwerpen**:

* [Ondersteuningsopties voor campagnes](https://helpx.adobe.com/campaign/kb/ac-support.html#acc-support)
* [Softwaredistributie](https://docs.adobe.com/content/help/en/experience-cloud/software-distribution/home.html)
* [Experience Cloud-ondersteuning en sessies met experts](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)
