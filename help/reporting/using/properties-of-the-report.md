---
product: campaign
title: Eigenschappen van het rapport
description: Meer informatie over de instellingen van de rapporteigenschappen
audience: reporting
content-type: reference
topic-tags: creating-new-reports
exl-id: dfa9d329-1086-4f6d-9d03-df159cad5495
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 1%

---

# Eigenschappen van het rapport{#properties-of-the-report}

![](../../assets/common.svg)

U kunt volledig uw rapport personaliseren en vormen om uw behoeften aan te passen. Hiervoor bewerkt u de eigenschappen. De eigenschappen van het rapport worden betreden via de **[!UICONTROL Properties]** knoop boven de grafiek van de activiteitenopeenvolging.

![](assets/s_ncs_advuser_report_properties_01.png)

Algemene eigenschappen worden hieronder beschreven. Geavanceerde mogelijkheden die zijn geconfigureerd op de tabbladen **[!UICONTROL Parameters]**, **[!UICONTROL Variables]** en **[!UICONTROL Scripts]** worden [in deze sectie](../../reporting/using/advanced-functionalities.md) beschreven.

## Algemene eigenschappen {#overall-properties}

Op het tabblad **[!UICONTROL General]** van de rapporteigenschappen kunt u de onderstaande instellingen bewerken:

* Het label en de interne naam van het rapport. **[!UICONTROL Internal name]** wordt gebruikt in het rapport definitieve URL. Het mag niet worden gewijzigd na de opstelling van het verslag.

* Het rapport **Folder** wordt geselecteerd tijdens rapportverwezenlijking. De beste praktijken moeten een specifieke omslag voor douanerapporten tot stand brengen zodat zij niet met [ingebouwde rapporten](../../reporting/using/about-campaign-built-in-reports.md) worden gemengd.

* De **Opslag** wordt geselecteerd wanneer het creëren van het rapport. Als u de gegevenstabel van het rapport wilt wijzigen, klikt u op het pictogram **[!UICONTROL Select link]** rechts van het veld **[!UICONTROL Document type]**.

   ![](assets/s_ncs_advuser_report_properties_02.png)

* De **Toegangsbeheer** parameters. Deze instellingen worden hieronder beschreven.

## Toegang tot het rapport beheren {#report-accessibility}

Een rapport kan in de console van Adobe Campaign of met Webbrowser worden betreden. In dit geval, kan het noodzakelijk zijn om het controle van de rapporttoegang zoals hieronder getoond te vormen.

![](assets/s_ncs_advuser_report_properties_02b.png)

Mogelijke opties zijn:

* **[!UICONTROL Anonymous access]**: deze optie maakt onbeperkte toegang tot het rapport mogelijk . Er is echter geen manipulatie mogelijk.

   Machtigingen van de technische operator &#39;webapp&#39; worden gebruikt om rapportelementen weer te geven. Meer informatie [in deze sectie](../../platform/using/access-management-operators.md).

* **[!UICONTROL Access control]**: met deze optie kunnen Adobe Campaign-operatoren de toepassing openen nadat ze zijn aangemeld.
* **[!UICONTROL Specific account]**: met deze optie kunt u het rapport uitvoeren met de rechten van de operator die in het  **[!UICONTROL Operator]** veld is geselecteerd.

## De lokalisatie van rapporten beheren {#managing-report-localization}

U kunt de talen vormen waarin u het rapport wilt worden vertaald. Klik hiertoe op het tabblad **[!UICONTROL Localization]**.

![](assets/s_ncs_advuser_report_properties_06.png)

De bewerkingstaal is de taal waarin u schrijft. Wanneer u een taal toevoegt, wordt het subtabblad weergegeven in de pagina voor het bewerken van rapporten.

![](assets/s_ncs_advuser_report_properties_05a.png)

>[!NOTE]
>
>Raadpleeg [deze sectie](../../web/using/translating-a-web-form.md) voor meer informatie over de lokalisatie van webpagina&#39;s in Campagne.

## HTML-rendering aanpassen {#personalizing-html-rendering}

Op het tabblad **[!UICONTROL Rendering]** kunt u de weergavemodus voor de pagina aanpassen. U kunt selecteren:

* De engine voor het renderen van grafieken: standaard is de renderingengine HTML 5.
* Het navigatietype in het rapport: via knoppen of koppelingen.
* De standaardpositie van labels voor rapportelementen. Deze positie kan voor elk element worden overbelast.
* De sjabloon of het thema dat wordt gebruikt voor het genereren van rapportpagina&#39;s.

![](assets/s_ncs_advuser_report_properties_08.png)

## De foutpagina aanpassen {#personalizing-the-error-page}

Het **[!UICONTROL Error page]** lusje laat u het bericht vormen dat omhoog in het geval van een fout in de rapportvertoning zal komen.

U kunt teksten bepalen en hen verbinden met specifieke herkenningstekens om rapportlocalisatie te beheren. Raadpleeg [Koptekst en voettekst toevoegen](../../reporting/using/element-layout.md#adding-a-header-and-a-footer) voor meer informatie.

![](assets/s_ncs_advuser_report_properties_11.png)
