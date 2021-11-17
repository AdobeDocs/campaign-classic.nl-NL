---
product: campaign
title: Adobe Campaign starten
description: Adobe Campaign starten
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: 4d9c5b24-83a2-4495-a56c-5bc376d69703
source-git-commit: 8491b3a5d1333f4445f90a8a051cd1f5149691bc
workflow-type: tm+mt
source-wordcount: '529'
ht-degree: 8%

---

# Adobe Campaign starten{#launching-adobe-campaign}

![](../../assets/v7-only.svg)

Campagne-clientconsole is

>[!CAUTION]
>
>Controleer de compatibiliteit van uw systeem en hulpprogramma&#39;s met de Adobe Campaign Client Console in het dialoogvenster [Compatibiliteitsmatrix](../../rn/using/compatibility-matrix.md#ClientConsoleoperatingsystems)

## Adobe Campaign starten {#starting-adobe-campaign}

U kunt Adobe Campaign starten door **[!UICONTROL Start / All Programs / Adobe Campaign v.X / Adobe Campaign client console]**.

In het verbindingsvenster van de clientconsole kunt u bestaande databases selecteren of configureren en er verbinding mee maken met een gebruikersnaam en wachtwoord:

![](assets/acc-logon.png)

## Verbinding maken met Adobe Campaign {#connecting-to-adobe-campaign}

U kunt verbinding maken met Adobe Campaign via uw Adobe ID. Raadpleeg [deze pagina](../../integrations/using/about-adobe-id.md) voor meer informatie.

U kunt ook verbinding maken met een toegewezen aanmelding/wachtwoord:

1. Voer de id van de operatoraccount in het dialoogvenster **[!UICONTROL Login]** veld.

   De beheerder van uw Adobe Campaign-platform geeft uw id op.

1. Voer uw wachtwoord in het dialoogvenster **[!UICONTROL Password]** veld.

   De eerste keer u tot het gegevensbestand toegang hebt, is uw wachtwoord dat aan u door de beheerder wordt gegeven. Wanneer u verbinding hebt, kunt u uw wachtwoord wijzigen via het dialoogvenster **[!UICONTROL Tools > Change password...]** -menu. Details over operatoren en aansluitingen zijn beschikbaar in [Toegangsbeheer](../../platform/using/access-management.md).

1. Klikken **[!UICONTROL LOG IN]** ter bevestiging.<!--You can also press the **Enter** key to launch connection.-->

U hebt nu toegang tot [Adobe Campaign-werkruimte](../../platform/using/adobe-campaign-workspace.md).

Sommige sneltoetsen zijn beschikbaar op het tabblad **[!UICONTROL Sign in screen]**:
* Alle activeerbare punten zijn selecteerbaar door **Tab** (van boven naar beneden) of de **Tab** + **Shift** (van beneden naar boven).
* Als u de verbinding wilt starten, kunt u ook op de knop **Enter** toets.
* U kunt de **Escape** toets om de **[!UICONTROL Login]** en **[!UICONTROL Password]** velden naar de laatst succesvolle verbindingswaarden.

## Verbindingen instellen {#setting-up-connections}

U hebt toegang tot de instellingen voor de serververbinding via de koppeling boven de invoerzone.

![](assets/s_ncs_user_connections_management.png)

In de **[!UICONTROL Connections]** venster, klikt u op **[!UICONTROL Add > Connection]**.

Vervolgens definieert u de verbindingsinstellingen. Dit doet u als volgt:

1. Voer een **[!UICONTROL Label]** om een naam toe te wijzen aan uw databaseverbinding.

1. Voeg het adres van de toepassingsserver toe in de **[!UICONTROL URL]** veld. Neem contact op met de beheerder als u de verbindings-URL niet kent.

1. Controleren **[!UICONTROL Connect with an Adobe ID]** voor de operatoren om verbinding te maken met de console met behulp van hun Adobe ID. Raadpleeg [deze pagina](../../integrations/using/about-adobe-id.md) voor meer informatie.

1. Klikken **[!UICONTROL OK]** om te valideren.

## Operatoren en machtigingen {#operators-and-permissions}

De id&#39;s en wachtwoorden van operatoren die toegang hebben tot de software en hun respectievelijke machtigingen zijn gedefinieerd door de systeembeheerder van Adobe Campaign in het dialoogvenster **[!UICONTROL Administration > Access management > Operators]** knooppunt van de boomstructuur Adobe Campaign.

Deze functionaliteit wordt gedetailleerd beschreven in de [Toegangsbeheer](../../platform/using/access-management.md) sectie.

## Verbinding met Adobe Campaign verbreken {#disconnecting-from-adobe-campaign}

Als u de verbinding met Adobe Campaign wilt verbreken, gebruikt u het eerste pictogram in de pictogrambalk.

![](assets/s_ncs_user_deconnexion.png)

>[!NOTE]
>
>U kunt de toepassing ook sluiten zonder u eerst af te melden.

## Adobe Campaign-versie ophalen {#getting-your-campaign-version}

De **[!UICONTROL Help > About...]** kunt u de volgende informatie gebruiken:

* **versie** aantal voor de cliëntconsole van de Campagne en toepassingsserver
* **build** aantal voor de cliëntconsole van de Campagne en toepassingsserver
* een koppeling om contact op te nemen met de klantenservice van Adobe
* koppelingen naar het privacybeleid van Adobe, de Gebruiksvoorwaarden en het Cookies-beleid

![](assets/about-acc.png)

Wanneer u het team van de Zorg van de Adobe klant bereikt, moet u het versieaantal verstrekken en aantal van uw de cliëntconsole en toepassingsserver van Adobe Campaign bouwen.

Als u aan loopt [Campagne [!DNL Gold Standard] versie](../../rn/using/gold-standard.md), moet u ook de SHA/1-tekens delen die worden weergegeven in het dialoogvenster **[!UICONTROL About]** doos. Bijvoorbeeld voor **Gold Standard 12** release, kan dit buildnummer worden weergegeven: &quot;build 9032@554dbcd&quot;.

![](assets/about-acc-gs.png)

Meer informatie over [!DNL Gold Standard] [in dit artikel](../../rn/using/gs-overview.md).

**Verwante onderwerpen**:

* [Adobe Campaign - Opties voor Help en ondersteuning](../../support.md)
* [Adobe Campaign-softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)
* [Adobe Experience Cloud-ondersteuning en sessies met experts](https://helpx.adobe.com/nl/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)
