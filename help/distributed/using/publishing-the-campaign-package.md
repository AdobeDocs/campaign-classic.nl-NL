---
product: campaign
title: Het campagnepakket publiceren
description: Het campagnepakket publiceren
feature: Distributed Marketing
hide: true
hidefromtoc: true
exl-id: e96add16-cbc8-43af-acff-06a95d5b7749
source-git-commit: 36fe54cf6d4d762d96205bd637311a426c741427
workflow-type: tm+mt
source-wordcount: '459'
ht-degree: 2%

---

# Het campagnepakket publiceren{#publishing-the-campaign-package}



Operatoren van centrale entiteiten publiceren campagnes die ze aan lokale entiteiten in de **[!UICONTROL list of campaign packages]** willen aanbieden.

Voordat ze in de lijst met campagnepakketten kunnen worden gepubliceerd, moeten ze door de centrale entiteit worden goedgekeurd. Hiertoe kunt u een revisor of groep revisoren opgeven via de koppeling **[!UICONTROL Approval parameters]** in het campagnepakket.

## Een revisor toewijzen {#assigning-a-reviewer}

Als u de controleur wilt selecteren, klikt u op de koppeling **[!UICONTROL Approval parameters]** in het campagnepakket en kiest u de relevante controleur in de vervolgkeuzelijst.

![](assets/s_advuser_mkg_dist_define_valid.png)

Vervolgens kunt u het goedkeuringsproces starten door op **[!UICONTROL Submit for approval]** te klikken.

![](assets/s_advuser_mkg_dist_valid_process.png)

Vervolgens wordt een meldingsbericht naar de controleur verzonden om de beschikbaarheid van dit campagnepakket te bevestigen. Het bericht bevat een koppeling waarmee u de goedkeuring via webtoegang kunt accepteren of afwijzen.

![](assets/s_advuser_mkg_dist_valid_process1.png)

>[!NOTE]
>
>Op het niveau van de organisatie kunt u ook revisoren opgeven om orders goed te keuren. Voor meer op dit, verwijs naar [ Organisatorische entiteiten ](about-distributed-marketing.md#organizational-entities).

## Andere revisoren toevoegen {#adding-other-reviewers}

U kunt andere revisoren toevoegen via de koppeling **[!UICONTROL Edit...]** in het tabblad **[!UICONTROL Approval parameters...]** van het campagnemakket.

![](assets/s_advuser_mkg_dist_select_op_valid.png)

## Erkenningsperiodes {#approval-periods}

Standaard krijgen revisoren drie dagen vanaf de verzenddatum de tijd om de goedkeuring te verwerken.

In het venster Revisoren bewerken kunt u ook herinneringen instellen voor het verzenden van een of meerdere berichten als er geen campagnepakket is goedgekeurd. Klik hiertoe op de koppeling **[!UICONTROL Add reminder]** en vervolgens op de knop **[!UICONTROL Add]** .

Herinneringen kunnen of op een bepaalde datum en/of **x** dagen na de voorleggingsdatum worden verzonden. Het type herinnering kan in de eerste kolom van de lijst van herinneringen worden gevormd. In het onderstaande voorbeeld ontvangen de controleurs een herinneringsbericht op de 29/01/2014, d.w.z. twee dagen vóór de in de kolom **[!UICONTROL Date]** geselecteerde datum, en een tweede herinnering één dag vóór het einde van de goedkeuringsperiode, d.w.z. twee dagen na de indiening voor goedkeuringsdatum.

![](assets/s_advuser_mkg_dist_reminder_planning.png)

Zodra deze is gedefinieerd en het pakket ter goedkeuring is verzonden, wordt het uitvoeringsschema weergegeven op het tabblad **[!UICONTROL Audit]** . Het toont de verwerkingstijd die op vorige configuratie wordt berekend, evenals de data van alle gevormde herinneringen wordt berekend.

## Goedkeuring via de Adobe Campaign-console {#approving-via-the-adobe-campaign-console}

Als er geen controleur is opgegeven of als geen van de aangemelde operatoren het pakket heeft goedgekeurd, kunt u met de knop **[!UICONTROL Approve the package]** rechtstreeks naar de goedkeuring gaan vanuit het campagnepakket **[!UICONTROL Dashboard]** of vanuit het overzicht van de pakketten.

![](assets/s_advuser_mkg_dist_valid_button.png)

Na goedkeuring wordt de campagne gepubliceerd, toegevoegd aan de lijst en kunnen lokale entiteiten deze gebruiken zodra de beschikbaarheidsdatum is bereikt. Als de lokale entiteiten tijdens het maken van de campagne zijn opgegeven, wordt een bericht verzonden naar de operatoren in de kennisgevingsgroep om hen te laten weten dat de campagne beschikbaar is. Als er vooraf geen entiteit is opgegeven, is de campagne standaard beschikbaar voor alle lokale entiteiten. Voor meer op dit, verwijs naar [ Organisatorische entiteiten ](about-distributed-marketing.md#organizational-entities).
