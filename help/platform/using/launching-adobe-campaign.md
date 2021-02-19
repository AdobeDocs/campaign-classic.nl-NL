---
solution: Campaign Classic
product: campaign
title: Adobe Campaign starten
description: Adobe Campaign starten
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '504'
ht-degree: 8%

---


# Adobe Campaign starten{#launching-adobe-campaign}

De console van de Cliënt van de campagne is een rijke cliënt die u toelaat om met uw de toepassingsserver(s) van de Campagne te verbinden. Leer hoe u de clientconsole downloadt en configureert in [deze pagina](../../installation/using/installing-the-client-console.md).

## Adobe Campaign {#starting-adobe-campaign} starten

U kunt Adobe Campaign starten door **[!UICONTROL Start / All Programs / Adobe Campaign v.X / Adobe Campaign client console]** te selecteren.

In het verbindingsvenster van de clientconsole kunt u bestaande databases selecteren of configureren en er verbinding mee maken met een gebruikersnaam en wachtwoord:

![](assets/acc-logon.png)

## Verbinding maken met Adobe Campaign {#connecting-to-adobe-campaign}

U kunt verbinding maken met Adobe Campaign via uw Adobe ID. Raadpleeg [deze pagina](../../integrations/using/about-adobe-id.md) voor meer informatie.

U kunt ook verbinding maken met een toegewezen aanmelding/wachtwoord:

1. Voer de id van de operatoraccount in het veld **[!UICONTROL login]** in.

   De beheerder van uw Adobe Campaign-platform geeft uw id op.

1. Voer in het veld **[!UICONTROL Password]** uw wachtwoord in.

   De eerste keer u tot het gegevensbestand toegang hebt, is uw wachtwoord dat aan u door de beheerder wordt gegeven. Nadat u verbinding hebt gemaakt, kunt u uw wachtwoord wijzigen via het menu **[!UICONTROL Tools > Change password...]**. Details over operators en verbindingen zijn beschikbaar in [Toegangsbeheer](../../platform/using/access-management.md).

1. Klik **[!UICONTROL LOG IN]** om te bevestigen.

U hebt nu toegang tot [Adobe Campaign-werkruimte](../../platform/using/adobe-campaign-workspace.md).

## Verbindingen {#setting-up-connections} instellen

U hebt toegang tot de instellingen voor de serververbinding via de koppeling boven de invoerzone.

![](assets/s_ncs_user_connections_management.png)

Klik in het venster **[!UICONTROL Connections]** op **[!UICONTROL Add > Connection]**.

Vervolgens definieert u de verbindingsinstellingen. Dit doet u als volgt:

1. Voer een **[!UICONTROL Label]** in om een naam toe te wijzen aan uw databaseverbinding.

1. Voeg het adres van de toepassingsserver in het **[!UICONTROL URL]** gebied toe. Neem contact op met de beheerder als u de verbindings-URL niet kent.

1. Controleer **[!UICONTROL Connect with an Adobe ID]** of de operatoren via hun Adobe ID verbinding maken met de console. Raadpleeg [deze pagina](../../integrations/using/about-adobe-id.md) voor meer informatie.

1. Klik **[!UICONTROL OK]** om te bevestigen.

## Operatoren en machtigingen {#operators-and-permissions}

De id&#39;s en wachtwoorden van operatoren met toegang tot de software en hun respectievelijke machtigingen worden gedefinieerd door uw Adobe Campaign-systeembeheerder in het knooppunt **[!UICONTROL Administration > Access management > Operators]** van de Adobe Campaign-structuur.

Deze functionaliteit wordt beschreven in [Toegangsbeheer](../../platform/using/access-management.md) sectie.

## Verbinding met Adobe Campaign {#disconnecting-from-adobe-campaign} verbreken

Als u de verbinding met Adobe Campaign wilt verbreken, gebruikt u het eerste pictogram in de pictogrambalk.

![](assets/s_ncs_user_deconnexion.png)

>[!NOTE]
>
>U kunt de toepassing ook sluiten zonder u eerst af te melden.

## Uw Adobe Campaign-versie ophalen {#getting-your-campaign-version}

Met het menu **[!UICONTROL Help > About...]** hebt u toegang tot de volgende informatie:

* **** versienummer voor de clientconsole en toepassingsserver van de campagne
* **** buildnummer voor Campagne-clientconsole en toepassingsserver
* een koppeling om contact op te nemen met de klantenservice van Adobe
* koppelingen naar het privacybeleid van Adobe, de Gebruiksvoorwaarden en het Cookies-beleid

![](assets/about-acc.png)

Wanneer u het team van de Zorg van de Adobe klant bereikt, moet u het versieaantal verstrekken en aantal van uw de cliëntconsole en toepassingsserver van Adobe Campaign bouwen.

Als u op [Campagne Gouden Standaard versie](../../rn/using/gold-standard.md) loopt, moet u ook de karakters delen SHA/1 die in **[!UICONTROL About]** doos worden getoond. Als voorbeeld, voor Gouden **Standaard 10 versie**, zal het bouwstijlaantal **build 9032@efd8a94** tonen, zoals hieronder getoond:

![](assets/about-acc-gs.png)

Meer informatie over Gold Standard [in dit artikel](https://helpx.adobe.com/nl/campaign/kb/gold-standard.html).

**Verwante onderwerpen**:

* [Adobe Campaign - Opties voor Help en ondersteuning](https://helpx.adobe.com/nl/campaign/kb/ac-support.html#acc-support)
* [Adobe-softwaredistributie](https://docs.adobe.com/content/help/en/experience-cloud/software-distribution/home.html)
* [Adobe Experience Cloud-ondersteuning en sessies met experts](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)
