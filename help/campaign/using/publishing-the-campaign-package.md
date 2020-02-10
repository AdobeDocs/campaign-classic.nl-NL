---
title: Het campagnepakket publiceren
seo-title: Het campagnepakket publiceren
description: Het campagnepakket publiceren
seo-description: null
page-status-flag: never-activated
uuid: f2d35a8d-191f-4c53-8682-7ccce2a94257
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: distributed-marketing
discoiquuid: 8653d4fc-e47f-451a-95f2-c9209a252664
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: d30de91002862b664249c5a704b7c0f521dd30f2

---


# Het campagnepakket publiceren{#publishing-the-campaign-package}

Operatoren van centrale entiteiten publiceren campagnes die zij aan lokale entiteiten in de **[!UICONTROL list of campaign packages]** Gemeenschap willen aanbieden.

Voordat ze in de lijst met campagnepakketten kunnen worden gepubliceerd, moeten ze door de centrale entiteit worden goedgekeurd. Hiertoe kunt u een revisor of groep revisoren opgeven via de **[!UICONTROL Approval parameters]** koppeling in het campagnepakket.

## Een revisor toewijzen {#assigning-a-reviewer}

Als u de controleur wilt selecteren, klikt u op de **[!UICONTROL Approval parameters]** koppeling in het campagnepakket en kiest u de relevante controleur in de vervolgkeuzelijst.

![](assets/s_advuser_mkg_dist_define_valid.png)

Vervolgens kunt u het goedkeuringsproces starten door op **[!UICONTROL Submit for approval]** te klikken.

![](assets/s_advuser_mkg_dist_valid_process.png)

Vervolgens wordt een meldingsbericht naar de controleur verzonden om de beschikbaarheid van dit campagnepakket te bevestigen. Het bericht bevat een verbinding om de goedkeuring via de toegang van het Web goed te keuren of te verwerpen.

![](assets/s_advuser_mkg_dist_valid_process1.png)

>[!NOTE]
>
>Op het niveau van de organisatie kunt u ook revisoren opgeven om orders goed te keuren. Raadpleeg [Organisatorische entiteiten](../../campaign/using/about-distributed-marketing.md#organizational-entities)voor meer informatie hierover.

## Andere revisoren toevoegen {#adding-other-reviewers}

U kunt andere revisoren toevoegen via de **[!UICONTROL Edit...]** koppeling op het **[!UICONTROL Approval parameters...]** tabblad van het campagnepakket.

![](assets/s_advuser_mkg_dist_select_op_valid.png)

## Erkenningsperioden {#approval-periods}

Standaard krijgen revisoren drie dagen vanaf de verzenddatum de tijd om de goedkeuring te verwerken.

In het venster Revisoren bewerken kunt u ook herinneringen instellen voor het verzenden van een of meerdere berichten als er geen campagnepakket is goedgekeurd. Klik hiertoe op de **[!UICONTROL Add reminder]** koppeling en vervolgens op de **[!UICONTROL Add]** knop.

Herinneringen kunnen op een bepaalde datum en/of **x** dagen na de verzenddatum worden verzonden. Het type herinnering kan in de eerste kolom van de lijst van herinneringen worden gevormd. In het onderstaande voorbeeld ontvangen de controleurs een herinneringsbericht op de 29/01/2014, d.w.z. twee dagen vóór de in de **[!UICONTROL Date]** kolom geselecteerde datum, en een tweede herinnering één dag vóór het einde van de goedkeuringsperiode, d.w.z. twee dagen na de datum van indiening voor goedkeuring.

![](assets/s_advuser_mkg_dist_reminder_planning.png)

Zodra het wordt bepaald en het pakket ter goedkeuring is voorgelegd, wordt het uitvoeringsprogramma getoond op het **[!UICONTROL Audit]** lusje. Het toont de verwerkingstijd die op vorige configuratie wordt berekend, evenals de data van alle gevormde herinneringen wordt berekend.

## Goedkeuren via de Adobe Campaign-console {#approving-via-the-adobe-campaign-console}

Als er geen controleur is opgegeven of als geen van de aangemelde exploitanten het pakket heeft goedgekeurd, kunt u met de **[!UICONTROL Approve the package]** knop rechtstreeks naar de goedkeuring gaan vanuit het campagnepakket **[!UICONTROL Dashboard]** of vanuit het overzicht van het pakket.

![](assets/s_advuser_mkg_dist_valid_button.png)

Na goedkeuring wordt de campagne gepubliceerd, toegevoegd aan de lijst en kunnen lokale entiteiten deze gebruiken zodra de beschikbaarheidsdatum is bereikt. Als de lokale entiteiten tijdens het maken van de campagne zijn opgegeven, wordt een bericht verzonden naar de operatoren in de kennisgevingsgroep om hen te laten weten dat de campagne beschikbaar is. Als er vooraf geen entiteit is opgegeven, is de campagne standaard beschikbaar voor alle lokale entiteiten. Raadpleeg [Organisatorische entiteiten](../../campaign/using/about-distributed-marketing.md#organizational-entities)voor meer informatie hierover.
