---
product: campaign
title: Kosten beheersen
description: Leer hoe u kosten kunt beheersen
audience: campaign
content-type: reference
topic-tags: tasks--resources-and-budgets
exl-id: 6765e307-915a-44d2-a486-85c64e8ec52e
source-git-commit: f000cb8bae164c22d1ede15db4e763cf50530674
workflow-type: tm+mt
source-wordcount: '2468'
ht-degree: 0%

---

# Kosten beheersen{#controlling-costs}

![](../../assets/v7-only.svg)

Adobe Campaign laat u geplande, geëngageerde en gefactureerde marketing kosten controleren en om hen door categorie te verdelen gebruikend de module van het Beheer van het Middel van de Marketing.

De kosten die voor de verschillende processen van een campagne zijn vastgelegd, komen ten laste van een vooraf door de marketingafdeling vastgestelde begroting. De bedragen kunnen in verschillende categorieën worden onderverdeeld om de informatie leesbaarder te maken en om een gedetailleerdere rapportage van de marketinginvesteringen mogelijk te maken.

Het beheer en bijhouden van budgetten is gecentraliseerd in een speciaal knooppunt van de Adobe Campaign-structuur. Hiermee kunt u de toegewezen, gereserveerde, vastgelegde en bestede bedragen vanuit dezelfde visie en voor alle begrotingen controleren.

![](assets/s_ncs_user_budget_node_02.png)

Voor de uitvoering van het begrotingsbeheer met behulp van MRM moeten de volgende stappen worden genomen:

1. Vaststelling van de begroting

   Raadpleeg voor meer informatie hierover [Een budget maken](#creating-a-budget).

1. Vaststelling van de kostprijsberekeningsmethode

   Kostenstructuren worden gedefinieerd voor de dienstverleners. Zie [Een serviceprovider en de bijbehorende kostencategorieën maken](../../campaign/using/providers--stocks-and-budgets.md#creating-a-service-provider-and-its-cost-categories).

1. Campagnekosten definiëren (leveringen/taken)

   De kosten van de leveringen en taken worden individueel of globaal voor het campagnemalplaatje ingevoerd. Zie [Berekening van de kosten en voorraden](../../campaign/using/marketing-campaign-deliveries.md#calculation-of-costs-and-stocks).

1. Consolidatie

   Afhankelijk van de stand van de uitvoering van de taken, leveringen en campagne zullen de kosten worden berekend en aan de desbetreffende begroting worden doorberekend.

   Wanneer de campagne voldoende gevorderd is, kan de stand van de uitvoering van de begroting voor de campagne worden gewijzigd in **[!UICONTROL Specified]**. De berekende kosten van het programma worden dan automatisch geboekt met de kosten die op de campagne zijn berekend. Zie [Vastleggingsverplichting, berekening en toerekening van kosten](#cost-commitment--calculation-and-charging).

## Een budget maken {#creating-a-budget}

Op de kaart worden budgetten gecreëerd via de **[!UICONTROL Campaign management > Budgets]** knooppunt. De **[!UICONTROL New]** in de werkbalk kunt u een budget maken.

* Nieuwe begroting toevoegen

   Klik op de knop **[!UICONTROL New]** en sla het budget op.

* Invoering van het oorspronkelijke bedrag

   Vermeld het toegewezen bedrag in het desbetreffende veld. De andere bedragen worden automatisch ingevoerd. Zie [Bedragen berekenen](#calculating-amounts).

* Vaststelling van de geldigheidsperiode

   Geef de begin- en einddatum op. Deze informatie is slechts indicatief.

* Uitgaven

   Maak de uitgavencategorieën waarin de kosten van deze begroting voor campagnes, taken, enz. zijn ondergebracht. kan worden gekoppeld. Zie [Categorieën kosten](#expense-categories).

   ![](assets/s_ncs_user_budget_create_and_save.png)

>[!NOTE]
>
>U kunt een gerelateerd budget selecteren.
>
>Raadpleeg voor meer informatie hierover [Een begroting koppelen aan een andere begroting](#linking-a-budget-to-another).

### Bedragen berekenen {#calculating-amounts}

Elke begroting wordt bepaald door een aanvangsbedrag dat wordt afgetrokken van de kosten van de verschillende campagnes, leveringen of taken die ermee verband houden nadat deze gepland of uitgevoerd zijn. De status van de (geplande, gereserveerde, vastgelegde, bestede of gefactureerde bedragen) hangt af van het soort kosten en het niveau van de vastlegging dat in de campagne, levering of taak is gedefinieerd.

>[!NOTE]
>
>De voor de categorieën opgenomen bedragen moeten overeenkomen met de in de **[!UICONTROL Allocated]** veld.

Voor campagnes kunnen, afhankelijk van het niveau van de verbintenis, kosten worden gepland, vastgelegd of gereserveerd voor een toekomstige actie.

![](assets/s_user_cost_op_engaged.png)

>[!CAUTION]
>
>Wanneer een campagne wordt gemaakt, wordt de status van de voortgang in **[!UICONTROL Budget]** moet worden ingesteld op **[!UICONTROL Defined]** de kosten die bij de uitvoering in aanmerking moeten worden genomen. Als de status **[!UICONTROL Being edited]** De kosten worden niet geconsolideerd.
>   
>De optie **[!UICONTROL Commitment level]** staat voor een kostenprognose in de toekomst voordat deze ten laste van de begroting komen . Afhankelijk van de voortgang van een campagne, taak of levering, kunt u besluiten een hoger of lager verbintenisniveau toe te wijzen (1). Geplant, 2. Gereserveerd, 3. Toegewezen) gebruikend de combodoos.

De geraamde kosten van een webcampagne bedragen bijvoorbeeld 45.000 euro.

![](assets/s_user_edit_budget_node_impact_0.png)

Voor de campagne, wanneer de status van begrotingscreatie is ingesteld op **[!UICONTROL Defined]** De werkelijke kosten van de campagne (of, indien geen, de berekende kosten) worden in de begrotingstotalen opgenomen.

![](assets/s_user_budget_in_op_a.png)

Afhankelijk van het niveau van de vastlegging van de campagnebegroting wordt het bedrag in de **[!UICONTROL Planned]**, **[!UICONTROL Reserved]** of **[!UICONTROL Committed]** veld.

Het niveau van de verbintenis kan worden gewijzigd:

* in de **campagne** in de **[!UICONTROL Budget]** venster, gevonden in het **[!UICONTROL Edit]** tab. Dit is waar begrotingen, kosten en uitgaven worden gevormd.
* in de **taken** in de **[!UICONTROL Expenses and revenues]** venster.

![](assets/s_user_op_engagement_level_costs.png)

Wanneer de begroting **[!UICONTROL Reserved]**, wordt de update automatisch uitgevoerd voor het aangerekende budget.

![](assets/s_user_edit_budget_node_impact_2.png)

De procedure is op taakniveau hetzelfde.

![](assets/s_user_edit_budget_node_impact_task.png)

Wanneer een uitgave aanleiding geeft tot een factuur en de factuur wordt betaald, wordt het bedrag ervan in de **[!UICONTROL Invoiced]** veld.

### Categorieën kosten {#expense-categories}

De bedragen kunnen in verschillende uitgavencategorieën worden verdeeld voor een betere leesbaarheid van de gegevens en voor een gedetailleerdere rapportage van marketinginvesteringen. De kostencategorieën worden tijdens het creëren van de begroting gedefinieerd via de **[!UICONTROL Budgets]** knooppunt van de structuur.

Als u een categorie wilt toevoegen, klikt u op de knop **[!UICONTROL Add]** in de onderste sectie van het venster.

![](assets/s_user_budget_category.png)

U kunt een categorie uit de bestaande categorie selecteren of een nieuwe categorie definiëren door deze rechtstreeks in het veld in te voeren. Wanneer u uw invoer bevestigt, kunt u deze categorie toevoegen aan de lijst met bestaande categorieën en deze indien nodig koppelen aan een Natuur. Deze informatie zal in de begrotingsverslagen worden gebruikt.

### Een budget koppelen aan een ander budget {#linking-a-budget-to-another}

U kunt een begroting koppelen aan een hoofdbegroting. Selecteer hiertoe het hoofdbudget in het dialoogvenster **[!UICONTROL related budget]** van de secundaire begrotingen.

![](assets/budget_link.png)

Er wordt een extra tabblad toegevoegd aan de hoofdbegroting om de lijst met verwante budgetten weer te geven.

![](assets/budget_link_new_tab.png)

Deze informatie wordt overgedragen naar de begrotingsverslagen.

## Kosten toevoegen {#adding-expense-lines}

De begrotingslijnen worden automatisch toegevoegd. Zij worden gecreeerd tijdens leveringsanalyse en wanneer een taak wordt gebeëindigd.

![](assets/s_ncs_user_budget_line_edit.png)

Voor elke campagne, levering of taak worden de gegenereerde kosten gegroepeerd in de uitgavenposten van de begroting waarvoor ze worden aangerekend. Deze uitgavenlijnen worden gecreëerd op basis van de kostenlijnen van de betrokken dienstverlener en berekend via de bijbehorende kostenstructuren.

Elke uitgavenpost bevat daarom de volgende informatie:

* De campagne en de uitvoering of taak waarmee zij verband houdt
* Het bedrag berekend op basis van de kostenstructuur of de geraamde voorlopige kosten
* Reële kosten van de betrokken levering of taak
* De corresponderende factuurlijn (alleen MRM)
* Lijst van kosten berekend per kostencategorie (indien er een kostenstructuur bestaat)

In het bovenstaande voorbeeld bevat de bewerkte uitgavenlijn de kosten die zijn berekend voor de **Nieuwe kaarten** levering voor de **Loyalty Spring Pack** campagne. Wanneer de levering wordt bewerkt, **[!UICONTROL Direct Mail]** kunt u zien hoe de onkostenregel wordt berekend.

De kostenberekening voor deze levering is gebaseerd op de kostencategorieën die voor de betrokken dienstverlener zijn geselecteerd:

![](assets/s_user_edit_del_supplier_costs.png)

Volgens de gekozen kostencategorieën worden de overeenkomstige kostenstructuren toegepast om de kostenposten te berekenen. In dit voorbeeld zijn de kostenstructuren voor de betrokken dienstverlener als volgt:

![](assets/s_user_edit_node_supplier_costs.png)

>[!NOTE]
>
>Kostencategorieën en -structuren worden weergegeven in [Een serviceprovider en de bijbehorende kostencategorieën maken](../../campaign/using/providers--stocks-and-budgets.md#creating-a-service-provider-and-its-cost-categories).

## Vastleggingsverplichting, berekening en toerekening van kosten {#cost-commitment--calculation-and-charging}

Kosten kunnen worden vastgelegd voor leveringen en taken. Afhankelijk van de voortgang van het proces waarmee het verband houdt, wordt de status van een kostprijs bijgewerkt.

### Kostprijsberekeningsproces {#cost-calculation-process}

De kosten zijn in drie categorieën onderverdeeld:

1. Geraamde voorlopige kosten

   De geraamde voorlopige kosten zijn een raming van de kosten voor het verloop van de campagne. Zolang deze wordt bewerkt, worden de ingevoerde bedragen niet geconsolideerd. Het moet **[!UICONTROL Specified]** status van de bij de berekeningen in aanmerking te nemen bedragen.

   Dit bedrag wordt handmatig ingevoerd en kan worden uitgesplitst in verschillende uitgavencategorieën. Klik op de knop **[!UICONTROL Breakdown...]** en vervolgens de **[!UICONTROL Add]** om een nieuwe hoeveelheid te definiëren.

   ![](assets/s_user_edit_budget_tab_ventil.png)

   U kunt elke kosten aan een categorie koppelen zodat de kostenindeling per uitgavencategorie later kan worden bekeken in de desbetreffende begroting en begrotingsrapporten.

1. Berekende kosten

   De berekende kosten zijn afhankelijk van het betrokken element (campagne, levering, taak, enz.) en de status ervan (wordt bewerkt, wordt uitgevoerd, is voltooid). In elk geval, als de reële kosten worden gespecificeerd, zullen de berekende kosten dit bedrag gebruiken.

   Indien de reële kosten niet worden opgegeven, gelden de volgende regels:

   * Voor een campagne die wordt bewerkt, zijn de berekende kosten de geraamde voorlopige kosten van de campagne of, indien deze kosten niet zijn vastgesteld, zijn de berekende kosten de som van alle voorlopige kosten van de leveringen en taken van de campagne. Als de campagne klaar is, zijn de berekende kosten van de campagne de som van alle berekende kosten.
   * Voor een levering die nog niet is geanalyseerd, zijn de berekende kosten de geraamde voorlopige kosten. Als de analyse al is uitgevoerd, zijn de berekende kosten de som van alle kosten die uit de dienst zijn berekend, kostenstructuren en het aantal beoogde ontvangers.
   * Voor een lopende taak maken de berekende kosten gebruik van de geraamde voorlopige kosten. Als de taak is voltooid, zijn de berekende kosten de som van alle kosten die zijn berekend op basis van de kostenstructuur van de dienstverlener en het aantal voltooide dagen.
   * Voor het marketingplan is, net als voor het programma, de berekende kosten de som van de voor de campagnes berekende kosten. Indien deze kosten niet worden gespecificeerd, worden voor de berekening van de kosten de geraamde voorlopige kosten gebruikt.

   >[!NOTE]
   >
   >De **[!UICONTROL Breakdown]** met de koppeling kunt u de details van de berekening en de laatste berekeningsdatum bekijken.

1. Reële kosten

   De werkelijke kosten worden handmatig ingevoerd en worden indien nodig uitgesplitst in verschillende kostencategorieën.

### Berekening en oplegging {#calculation-and-charging}

De kosten worden berekend via kostenstructuren en worden in rekening gebracht op de in de betrokken campagnes, leveringen of taken geselecteerde budgetten.

De bedragen die via de goedkeuring van de begroting voor campagnes zijn vastgelegd, kunnen worden gecontroleerd. Er kunnen extra taken in de vorm van een controlepunt worden gemaakt in een campagne om andere goedkeuringen in te stellen. Zie [Typen taken](../../mrm/using/creating-and-managing-tasks.md#types-of-task).

### Voorbeeld {#example}

We gaan een campagne opzetten met:

* Een directe postlevering die de kostenstructuren van een dienstverlener gebruikt
* Een taak met vaste kosten
* Een taak met dagelijkse kosten

#### Stap 1 - Maak de begroting {#step-1---creating-the-budget}

1. Maak een nieuwe begroting via de **[!UICONTROL Campaign management > Budgets]** knooppunt.

1. Definieer een begroting van 10.000 euro in de **[!UICONTROL Allocated]** van het **[!UICONTROL Amounts]** sectie. Voeg twee uitgavencategorieën in de onderste sectie van het venster toe:

![](assets/s_user_cost_mgmt_sample_1.png)

#### Stap 2 - vorm de dienstverlener en bepaal de kostenstructuren {#step-2---configuring-the-service-provider-and-defining-the-cost-structures}

1. Creeer een dienstverlener en een de dienstmalplaatje met zijn kostenstructuur van **[!UICONTROL Administration > Campaigns]** knooppunt. Raadpleeg voor meer informatie hierover [Een serviceprovider en de bijbehorende kostencategorieën maken](../../campaign/using/providers--stocks-and-budgets.md#creating-a-service-provider-and-its-cost-categories).

   Maak kostencategorieën voor directe mailleveringen **[!UICONTROL Envelopes]** (typen 114x229 en 162x229), **[!UICONTROL Postage]** en **[!UICONTROL Print]** (typen A3 en A4). En creeer dan de volgende kostenstructuren:

   ![](assets/s_user_cost_mgmt_sample_2.png)

1. Voeg een vaste kostprijs toe (in de kostencategorieën) waarvan de berekening vast is en waarvan het bedrag leeg is (in de desbetreffende kostenstructuur) en die voor elke levering afzonderlijk wordt gespecificeerd.

   ![](assets/s_user_cost_mgmt_sample_5.png)

   Voor taken maakt u de volgende twee kostencategorieën:

   * **[!UICONTROL Room reservation]** (Kleine kamer en Grote kamer), met een **vast** kostenstructuur ten bedrage van 300 en 500 EUR:

   ![](assets/s_user_cost_mgmt_sample_6.png)

   * **[!UICONTROL Creation]** (**Inhoudssjabloon** tekst), met een **dagelijks** kostenstructuur van 300 EUR:

   ![](assets/s_user_cost_mgmt_sample_7.png)

#### Stap 3 - Het budget in de campagne in rekening brengen {#step-3---charging-the-budget-in-the-campaign}

1. Maak een campagne en selecteer het budget dat in Stap 1 wordt gemaakt.

   >[!NOTE]
   >
   >Standaard wordt het voor het programma geselecteerde budget toegepast op alle campagnes in het programma.

   ![](assets/s_user_cost_mgmt_sample_4.png)

1. Geef de geraamde voorlopige kosten op, uitgesplitst:

   ![](assets/s_user_cost_mgmt_sample_9.png)

1. Klikken **[!UICONTROL Ok]** en vervolgens **[!UICONTROL Save]** om deze informatie te bevestigen. De berekende kosten van de campagne worden vervolgens bijgewerkt met de geraamde voorlopige kosten.

#### Stap 4 - de directe postlevering creëren {#step-4---creating-the-direct-mail-delivery}

1. Maak een workflow voor de campagne en plaats de query-activiteiten om het doel te selecteren (waarschuwingsbericht: de geadresseerde postadressen moeten worden opgegeven).

1. Creeer een directe postlevering en selecteer de dienstverlener die in Stap 2 wordt gecreeerd: de kostencategorieën worden automatisch weergegeven.

1. Overschrijf de kosten van de enveloppen en voeg vaste kosten toe. Selecteer ook de categorieën waarop deze kosten betrekking hebben.

   ![](assets/s_user_cost_mgmt_sample_3.png)

   >[!NOTE]
   >
   >Als een van de kostencategorieën niet wordt gebruikt, zal dit geen kosten genereren.

1. Start de workflow die u zojuist hebt gemaakt om de analyse te starten en de kosten te berekenen.

   ![](assets/s_user_cost_mgmt_sample_10.png)

1. Als voor deze campagne begrotingsgoedkeuring is ingeschakeld, keurt u de begroting van het dashboard goed. Je kunt de goedkeuring van kostencategorieën controleren.

   ![](assets/s_user_cost_mgmt_sample_10b.png)

De uitgavenpost voor de levering wordt toegevoegd aan de **[!UICONTROL Edit > Budget]** tabblad van de campagne. Bewerk de tabel om de details van de berekening weer te geven.

![](assets/s_user_cost_mgmt_sample_11.png)

De voor de levering berekende kosten worden met deze informatie bijgewerkt:

![](assets/s_user_cost_mgmt_sample_12.png)

Wanneer u de berekende kosten bewerkt, kunt u de uitsplitsing van de kosten en de status en datum van de kostenberekening controleren.

#### Stap 5 - Taken maken {#step-5---creating-tasks}

Aan deze campagne zullen wij de twee taken toevoegen waarvoor de kostenstructuren eerder zijn gecreëerd (zie [Stap 2 - vorm de dienstverlener en bepaal de kostenstructuren](#step-2---configuring-the-service-provider-and-defining-the-cost-structures)). Klik hiertoe op het campagnemarkeerteken op de knop **[!UICONTROL Add a task]** knop. Geef een naam op voor de taak en klik op **[!UICONTROL Save]**.

1. De taak wordt vervolgens toegevoegd aan de takenlijst. U moet het uitgeven om het te vormen.

1. In de **[!UICONTROL Properties]** selecteert u de service en de bijbehorende kostencategorie:

   ![](assets/s_user_cost_mgmt_sample_14.png)

1. Klik op de knop **[!UICONTROL Expenses and revenue]** pictogram van de taak en vermelding van de geraamde voorlopige kosten.

   ![](assets/s_user_cost_mgmt_sample_15.png)

   Wanneer de taak is gered, worden de berekende kosten gespecificeerd met de waarde die voor de geschatte voorlopige kosten wordt ingevoerd.

   Wanneer de taak is voltooid (status **[!UICONTROL Finished]** ), worden de berekende kosten automatisch bijgewerkt met de kosten van de Grote Ruimte zoals die in zijn kostenstructuur zijn vermeld. Deze kosten worden ook in deze categorie in de uitsplitsing weergegeven.

1. Vervolgens maakt u een tweede taak volgens dezelfde procedure. die langer dan vijf dagen zijn gepland en betrekking hebben op de eerder gemaakte kostenstructuur.

   ![](assets/s_user_cost_mgmt_sample_16.png)

   Wanneer de taak is voltooid, worden de berekende kosten gespecificeerd met de waarde van de gerelateerde kostenstructuur, d.w.z. 1500 euro in ons voorbeeld (5 dagen x 300 euro):

   ![](assets/s_user_cost_mgmt_sample_17.png)

#### Stap 6 - De begrotingsstatus van de campagne bijwerken {#step-6---update-the-campaign-budget-status}

Wanneer de campagne wordt gevormd, kan zijn status worden bijgewerkt door het te plaatsen aan **[!UICONTROL Specified]**. De berekende kosten van de campagne vermelden vervolgens de som van de berekende kosten van de levering en de taken van de campagne:

![](assets/s_user_cost_mgmt_sample_18.png)

#### Begrotingsgoedkeuring {#budget-approval}

Wanneer goedkeuring wordt geactiveerd, kunt u een speciale koppeling gebruiken om het budget van het campagnesdashboard goed te keuren. Deze koppeling wordt weergegeven wanneer de doelworkflow is gestart en een direct mailbericht moet worden goedgekeurd.

![](assets/s_user_cost_mgmt_sample_19.png)

U kunt dan op de koppeling klikken om goedkeuring te verlenen of af te wijzen, of de koppeling gebruiken in de e-mail met kennisgeving als er een melding is geactiveerd voor deze campagne.

Wanneer de begroting is goedgekeurd en de levering is voltooid, worden de kosten automatisch geüpload via een speciale technische workflow.

## Orders en facturen {#orders-and-invoices}

In de context van MRM, kunt u orden bij een dienstverlener bewaren en facturen uitgeven. De volledige levenscyclus van deze bestellingen en facturen kan via de interface van Adobe Campaign worden beheerd.

### Maken van bestellingen {#order-creation}

Als u een nieuwe bestelling wilt opslaan bij een serviceprovider, klikt u op de knop **[!UICONTROL MRM > Orders]** knoop van de boom, en klik dan **[!UICONTROL New]** knop.

Vermeld het ordernummer, de betrokken dienstverlener en het totale bedrag van de order.

![](assets/s_user_cost_create_order.png)

### Uitgeven en facturen bijhouden {#issuing-and-tracking-invoices}

Voor elke dienstverlener, kunt u facturen bewaren en hun status en het in rekening gebrachte budget bepalen.

Facturen worden gemaakt en opgeslagen in de **[!UICONTROL MRM > Invoices]** knooppunt van de boomstructuur Adobe Campaign.

![](assets/s_user_cost_create_invoice.png)

Een factuur bestaat uit factuurlijnen waarvan het totaal automatisch het bedrag kan berekenen. Deze regels worden handmatig gemaakt op basis van de **[!UICONTROL Invoice lines]** tab. Zij kunnen met een orde worden geassocieerd om de informatie aan de orden te uploaden.

![](assets/s_user_cost_invoice_add_line.png)

De facturen van elke dienstverlener worden weergegeven in de **[!UICONTROL Invoices]** tabblad van het profiel:

![](assets/s_ncs_user_invoice_from_supplier.png)

De **[!UICONTROL Details]** kunt u de inhoud van de factuur weergeven.

Klikken **[!UICONTROL Add]** om een nieuwe factuur te maken.
