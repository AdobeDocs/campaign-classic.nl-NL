---
solution: Campaign Classic
product: campaign
title: Het campagnepakket publiceren
description: Het campagnepakket publiceren
audience: campaign
content-type: reference
topic-tags: distributed-marketing
translation-type: tm+mt
source-git-commit: c625b4109e2cb47446331cd009ff9827c8267c93
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 2%

---


# Het campagnepakket publiceren{#publishing-the-campaign-package}

Operatoren van centrale entiteiten publiceren campagnes die ze aan lokale entiteiten in de **[!UICONTROL list of campaign packages]** willen aanbieden.

Voordat ze in de lijst met campagnepakketten kunnen worden gepubliceerd, moeten ze door de centrale entiteit worden goedgekeurd. Hiervoor kunt u een revisor of groep revisoren opgeven via de koppeling **[!UICONTROL Approval parameters]** in het campagnepakket.

## Een revisor {#assigning-a-reviewer} toewijzen

Als u de controleur wilt selecteren, klikt u op de koppeling **[!UICONTROL Approval parameters]** in het campagnepakket en kiest u de relevante controleur in de vervolgkeuzelijst.

![](assets/s_advuser_mkg_dist_define_valid.png)

U kunt dan met het goedkeuringsproces beginnen door **[!UICONTROL Submit for approval]** te klikken.

![](assets/s_advuser_mkg_dist_valid_process.png)

Vervolgens wordt een meldingsbericht naar de controleur verzonden om de beschikbaarheid van dit campagnepakket te bevestigen. Het bericht bevat een koppeling waarmee u de goedkeuring via webtoegang kunt accepteren of afwijzen.

![](assets/s_advuser_mkg_dist_valid_process1.png)

>[!NOTE]
>
>Op het niveau van de organisatie kunt u ook revisoren opgeven om orders goed te keuren. Raadpleeg [Organisatorische entiteiten](../../campaign/using/about-distributed-marketing.md#organizational-entities) voor meer informatie hierover.

## Andere revisoren toevoegen {#adding-other-reviewers}

U kunt andere revisoren toevoegen via de koppeling **[!UICONTROL Edit...]** in het tabblad **[!UICONTROL Approval parameters...]** van het campagnepakket.

![](assets/s_advuser_mkg_dist_select_op_valid.png)

## Goedkeuringsperioden {#approval-periods}

Standaard krijgen revisoren drie dagen vanaf de verzenddatum de tijd om de goedkeuring te verwerken.

In het venster Revisoren bewerken kunt u ook herinneringen instellen voor het verzenden van een of meerdere berichten als er geen campagnepakket is goedgekeurd. Om dit te doen, klik **[!UICONTROL Add reminder]** verbinding, dan **[!UICONTROL Add]** knoop.

Herinneringen kunnen worden verzonden op een bepaalde datum en/of **x** dagen na de verzenddatum. Het type herinnering kan in de eerste kolom van de lijst van herinneringen worden gevormd. In het onderstaande voorbeeld ontvangen de controleurs een herinneringsbericht op de 29/01/2014, d.w.z. twee dagen vóór de in de kolom **[!UICONTROL Date]** geselecteerde datum, en een tweede herinnering één dag vóór het einde van de goedkeuringsperiode, d.w.z. twee dagen na de indiening voor de goedkeuringsdatum.

![](assets/s_advuser_mkg_dist_reminder_planning.png)

Nadat het pakket is gedefinieerd en ter goedkeuring is ingediend, wordt het uitvoeringsschema weergegeven op het tabblad **[!UICONTROL Audit]**. Het toont de verwerkingstijd die op vorige configuratie wordt berekend, evenals de data van alle gevormde herinneringen wordt berekend.

## Goedkeuring via de Adobe Campaign-console {#approving-via-the-adobe-campaign-console}

Als er geen controleur is opgegeven of als geen van de aangemelde operatoren het pakket heeft goedgekeurd, kunt u met de knop **[!UICONTROL Approve the package]** rechtstreeks naar de goedkeuring gaan vanuit het campagnepakket **[!UICONTROL Dashboard]** of vanuit het overzicht van de pakketten.

![](assets/s_advuser_mkg_dist_valid_button.png)

Na goedkeuring wordt de campagne gepubliceerd, toegevoegd aan de lijst en kunnen lokale entiteiten deze gebruiken zodra de beschikbaarheidsdatum is bereikt. Als de lokale entiteiten tijdens het maken van de campagne zijn opgegeven, wordt een bericht verzonden naar de operatoren in de kennisgevingsgroep om hen te laten weten dat de campagne beschikbaar is. Als er vooraf geen entiteit is opgegeven, is de campagne standaard beschikbaar voor alle lokale entiteiten. Raadpleeg [Organisatorische entiteiten](../../campaign/using/about-distributed-marketing.md#organizational-entities) voor meer informatie hierover.
