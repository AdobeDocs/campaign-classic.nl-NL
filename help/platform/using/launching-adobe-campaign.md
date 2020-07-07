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
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 84f06afb36aa6a9fa13db1fda7034389b762eb99
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---


# Adobe Campaign starten{#launching-adobe-campaign}

De console van de Cliënt van de campagne is een rijke cliënt die u toelaat om met uw de toepassingsserver(s) van de Campagne te verbinden. Leer hoe u de clientconsole op [deze pagina](../../installation/using/installing-the-client-console.md)downloadt en configureert.

## Adobe Campaign starten {#starting-adobe-campaign}

Je kunt Adobe Campaign starten door te selecteren **[!UICONTROL Start / All Programs / Adobe Campaign v.X / Adobe Campaign client console]**.

In het verbindingsvenster van de clientconsole kunt u bestaande databases selecteren of configureren en er verbinding mee maken met een gebruikersnaam en wachtwoord:

![](assets/s_ncs_user_login.png)

## Verbinding maken met Adobe Campaign {#connecting-to-adobe-campaign}

U kunt verbinding maken met Adobe Campaign via uw Adobe ID. For more on this, refer to [this page](../../integrations/using/about-adobe-id.md).

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

Klik in het **[!UICONTROL Connections]** venster op **[!UICONTROL Add > Connection]**.

![](assets/s_ncs_user_add_connexion.png)

Vervolgens definieert u de verbindingsinstellingen. Dit doet u als volgt:

1. Voer een naam in **[!UICONTROL Label]** om een naam toe te wijzen aan uw databaseverbinding.

1. Voeg het adres van de toepassingsserver in het **[!UICONTROL URL]** veld toe. Neem contact op met de beheerder als u de verbindings-URL niet kent.

1. Controleer **[!UICONTROL Connect with an Adobe ID]** of de operatoren verbinding maken met de console met hun Adobe ID. For more on this, refer to [this page](../../integrations/using/about-adobe-id.md).

1. Klik **[!UICONTROL OK]** om te valideren.

## Operatoren en machtigingen {#operators-and-permissions}

De id&#39;s en wachtwoorden van operatoren met toegang tot de software en hun respectieve machtigingen worden gedefinieerd door uw Adobe Campaign-systeembeheerder in het **[!UICONTROL Administration > Access management > Operators]** knooppunt van de Adobe Campaign-structuur.

Deze functionaliteit wordt gedetailleerd in de sectie van het Beheer van de [Toegang](../../platform/using/access-management.md) .

## Verbinding met Adobe Campaign verbreken {#disconnecting-from-adobe-campaign}

Als u de verbinding met Adobe Campaign wilt verbreken, gebruikt u het eerste pictogram in de pictogrambalk.

![](assets/s_ncs_user_deconnexion.png)

>[!NOTE]
>
>U kunt de toepassing ook sluiten zonder u eerst af te melden.

## Campagneversie ophalen {#getting-your-campaign-version}

In het **[!UICONTROL Help > About...]** menu hebt u toegang tot de volgende informatie:

* **versienummer** ,
* **buildnummer** ,
* een koppeling om contact op te nemen met Adobe Campaign Support.

   >[!CAUTION]
   >
   >Wanneer u het team van de Steun van Adobe bereikt, moet u het versieaantal verstrekken en aantal van uw de cliëntconsole en toepassingsserver van de Campagne bouwen.

