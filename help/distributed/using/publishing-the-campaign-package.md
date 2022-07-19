---
product: campaign
title: Het campagnepakket publiceren
description: Het campagnepakket publiceren
feature: Distributed Marketing
exl-id: e96add16-cbc8-43af-acff-06a95d5b7749
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 2%

---

# Het campagnepakket publiceren{#publishing-the-campaign-package}

![](../../assets/v7-only.svg)

Operatoren van centrale entiteiten publiceren campagnes die zij aan lokale entiteiten in de **[!UICONTROL list of campaign packages]**.

Voordat ze in de lijst met campagnepakketten kunnen worden gepubliceerd, moeten ze door de centrale entiteit worden goedgekeurd. Hiertoe kunt u een revisor of groep revisoren opgeven via de **[!UICONTROL Approval parameters]** koppeling in het campagnepakket .

## Een revisor toewijzen {#assigning-a-reviewer}

Als u de controleur wilt selecteren, klikt u op de knop **[!UICONTROL Approval parameters]** in het campagnepakket en kiest u de relevante revisor in de vervolgkeuzelijst.

![](assets/s_advuser_mkg_dist_define_valid.png)

Vervolgens kunt u het goedkeuringsproces starten door op **[!UICONTROL Submit for approval]**.

![](assets/s_advuser_mkg_dist_valid_process.png)

Vervolgens wordt een meldingsbericht naar de controleur verzonden om de beschikbaarheid van dit campagnepakket te bevestigen. Het bericht bevat een koppeling waarmee u de goedkeuring via webtoegang kunt accepteren of afwijzen.

![](assets/s_advuser_mkg_dist_valid_process1.png)

>[!NOTE]
>
>Op het niveau van de organisatie kunt u ook revisoren opgeven om orders goed te keuren. Raadpleeg voor meer informatie hierover [Organisatorische entiteiten](about-distributed-marketing.md#organizational-entities).

## Andere revisoren toevoegen {#adding-other-reviewers}

U kunt andere revisoren toevoegen van de **[!UICONTROL Edit...]** link in het campagnepakket **[!UICONTROL Approval parameters...]** tab.

![](assets/s_advuser_mkg_dist_select_op_valid.png)

## Erkenningsperioden {#approval-periods}

Standaard krijgen revisoren drie dagen vanaf de verzenddatum de tijd om de goedkeuring te verwerken.

In het venster Revisoren bewerken kunt u ook herinneringen instellen voor het verzenden van een of meerdere berichten als er geen campagnepakket is goedgekeurd. Om dit te doen, klik **[!UICONTROL Add reminder]** dan de koppeling **[!UICONTROL Add]** knop.

Herinneringen kunnen op een bepaalde datum worden verzonden en/of **x** dagen na de verzenddatum. Het type herinnering kan in de eerste kolom van de lijst van herinneringen worden gevormd. In het onderstaande voorbeeld ontvangen de controleurs een herinneringsbericht op de website op 29/01/2014, d.w.z. twee dagen voor de datum die is geselecteerd in het **[!UICONTROL Date]** kolom en een tweede herinnering één dag vóór het einde van de goedkeuringsperiode, d.w.z. twee dagen na de datum van indiening voor goedkeuring.

![](assets/s_advuser_mkg_dist_reminder_planning.png)

Als het pakket eenmaal is gedefinieerd en ter goedkeuring is ingediend, wordt het uitvoeringsschema weergegeven in het dialoogvenster **[!UICONTROL Audit]** tab. Het toont de verwerkingstijd die op vorige configuratie wordt berekend, evenals de data van alle gevormde herinneringen wordt berekend.

## Goedkeuring via de Adobe Campaign-console {#approving-via-the-adobe-campaign-console}

Als er geen controleur is opgegeven of als geen van de aangemelde exploitanten het pakket heeft goedgekeurd, **[!UICONTROL Approve the package]** de knoop laat u rechtstreeks aan goedkeuring van het campagnepakket verdergaan **[!UICONTROL Dashboard]** of uit het overzicht van de pakketten.

![](assets/s_advuser_mkg_dist_valid_button.png)

Na goedkeuring wordt de campagne gepubliceerd, toegevoegd aan de lijst en kunnen lokale entiteiten deze gebruiken zodra de beschikbaarheidsdatum is bereikt. Als de lokale entiteiten tijdens het maken van de campagne zijn opgegeven, wordt een bericht verzonden naar de operatoren in de kennisgevingsgroep om hen te laten weten dat de campagne beschikbaar is. Als er vooraf geen entiteit is opgegeven, is de campagne standaard beschikbaar voor alle lokale entiteiten. Raadpleeg voor meer informatie hierover [Organisatorische entiteiten](about-distributed-marketing.md#organizational-entities).
