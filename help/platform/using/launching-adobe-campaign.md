---
title: Adobe-campagne starten
seo-title: Adobe-campagne starten
description: Adobe-campagne starten
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
source-git-commit: 51e4d72abf3a1f48700ca38566dbf06dd24594b8

---


# Adobe-campagne starten{#launching-adobe-campaign}

## Adobe-campagne starten {#starting-adobe-campaign}

U kunt Adobe Campagne starten door te selecteren **[!UICONTROL Start / All Programs / Adobe Campaign v.X / Adobe Campaign client console]**.

In het verbindingsvenster van de clientconsole kunt u bestaande databases selecteren of configureren en er verbinding mee maken met een gebruikersnaam en wachtwoord:

![](assets/s_ncs_user_login.png)

## Verbinding maken met Adobe-campagne {#connecting-to-adobe-campaign}

U kunt verbinding maken met Adobe-campagne met uw Adobe-id. Raadpleeg [deze pagina](../../integrations/using/about-adobe-id.md)voor meer informatie.

U kunt ook verbinding maken met een toegewezen aanmelding/wachtwoord:

1. Voer de id van de operatoraccount in het **[!UICONTROL login]** veld in.

   Uw id wordt gegeven door de beheerder van uw Adobe Campagne-platform.

1. Voer uw wachtwoord in het **[!UICONTROL Password]** veld in.

   De eerste keer u tot het gegevensbestand toegang hebt, is uw wachtwoord dat aan u door de beheerder wordt gegeven. Zodra u verbonden bent, kunt u uw wachtwoord via het **[!UICONTROL Tools > Change password...]** menu veranderen. Details over operatoren en verbindingen zijn beschikbaar in [Toegangsbeheer](../../platform/using/access-management.md).

1. Klik **[!UICONTROL Log in]** om te bevestigen.

U hebt nu toegang tot de [Adobe-werkruimte](../../platform/using/adobe-campaign-workspace.md)voor campagnes.

## Verbindingen instellen {#setting-up-connections}

U hebt toegang tot de instellingen voor de serververbinding via de koppeling boven de invoerzone.

![](assets/s_ncs_user_connections_management.png)

Klik in het **[!UICONTROL Connections]** venster op **[!UICONTROL Add > Connection]**.

![](assets/s_ncs_user_add_connexion.png)

Vervolgens definieert u de verbindingsinstellingen. Dit doet u als volgt:

* Voer een naam in **[!UICONTROL Label]** om een naam toe te wijzen aan uw databaseverbinding.
* Voeg het adres van de toepassingsserver in het **[!UICONTROL URL]** veld toe. Neem contact op met de beheerder als u de verbindings-URL niet kent.
* Controleer **[!UICONTROL Connect with an Adobe ID]** of de operatoren verbinding maken met de console met hun Adobe-id. Raadpleeg [deze pagina](../../integrations/using/about-adobe-id.md)voor meer informatie.
* Klik **[!UICONTROL OK]** om te valideren.

>[!NOTE]
>
>Met de **[!UICONTROL Add]** knop kunt u al uw verbindingen ordenen **[!UICONTROL folders]** . U hoeft alleen elke verbinding naar een map te slepen.

## Operatoren en machtigingen {#operators-and-permissions}

De id&#39;s en wachtwoorden van operatoren die toegang hebben tot de software en hun respectievelijke machtigingen worden gedefinieerd door de systeembeheerder van het Adobe Campagne-systeem in het **[!UICONTROL Administration > Access management > Operators]** knooppunt van de Adobe Campagne-structuur.

Deze functionaliteit wordt gedetailleerd in de het beheerssectie van de [Toegang](../../platform/using/access-management.md) .

## Verbinding met Adobe-campagne verbreken {#disconnecting-from-adobe-campaign}

Als u de verbinding met Adobe Campaign wilt verbreken, gebruikt u het eerste pictogram in de pictogrambalk.

![](assets/s_ncs_user_deconnexion.png)

>[!NOTE]
>
>U kunt de toepassing ook sluiten zonder u eerst af te melden.

## Campagneversie ophalen {#getting-your-campaign-version}

In het **[!UICONTROL Help > About...]** menu hebt u toegang tot de volgende informatie:

* **versienummer** ,
* **buildnummer** ,
* een koppeling om contact op te nemen met de Adobe Campagne Support.

   >[!CAUTION]
   >
   >Wanneer u het team van de Steun van Adobe bereikt, moet u het versieaantal verstrekken en aantal van uw de cliëntconsole en toepassingsserver van de Campagne bouwen.

