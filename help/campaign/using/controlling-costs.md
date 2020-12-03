---
solution: Campaign Classic
product: campaign
title: Kosten beheren
description: Kosten beheren
audience: campaign
content-type: reference
topic-tags: tasks--resources-and-budgets
translation-type: tm+mt
source-git-commit: c625b4109e2cb47446331cd009ff9827c8267c93
workflow-type: tm+mt
source-wordcount: '2468'
ht-degree: 0%

---


# Kosten beheren{#controlling-costs}

## Informatie over kostenbeheersing {#about-cost-control}

Adobe Campaign laat u geplande, geëngageerde en gefactureerde marketing kosten controleren en om hen door categorie te verdelen gebruikend de module van het Beheer van het Middel van de Marketing.

De kosten die voor de verschillende processen van een campagne zijn vastgelegd, komen ten laste van een vooraf door de marketingafdeling vastgestelde begroting. De bedragen kunnen in verschillende categorieën worden onderverdeeld om de informatie leesbaarder te maken en om een gedetailleerdere rapportage van de marketinginvesteringen mogelijk te maken.

Het beheer en bijhouden van budgetten is gecentraliseerd in een speciaal knooppunt van de Adobe Campaign-structuur. Hiermee kunt u de toegewezen, gereserveerde, vastgelegde en bestede bedragen vanuit dezelfde visie en voor alle begrotingen controleren.

![](assets/s_ncs_user_budget_node_02.png)

Voor de uitvoering van het begrotingsbeheer met behulp van MRM moeten de volgende stappen worden genomen:

1. Vaststelling van de begroting

   Raadpleeg [Een budget maken](#creating-a-budget) voor meer informatie.

1. Vaststelling van de kostprijsberekeningsmethode

   Kostenstructuren worden gedefinieerd voor de dienstverleners. Zie [Een serviceprovider en de bijbehorende kostencategorieën maken](../../campaign/using/providers--stocks-and-budgets.md#creating-a-service-provider-and-its-cost-categories).

1. Campagnekosten definiëren (leveringen/taken)

   De kosten van de leveringen en taken worden individueel of globaal voor het campagnemalplaatje ingevoerd. Zie [Berekening van kosten en standen](../../campaign/using/marketing-campaign-deliveries.md#calculation-of-costs-and-stocks).

1. Consolidatie

   Afhankelijk van de stand van de uitvoering van de taken, leveringen en campagne zullen de kosten worden berekend en aan de desbetreffende begroting worden doorberekend.

   Wanneer de campagne voldoende gevorderd is, kan de voortgang van de campagnebegroting worden gewijzigd in **[!UICONTROL Specified]**. De berekende kosten van het programma worden dan automatisch geboekt met de kosten die op de campagne zijn berekend. Zie [Kostenverplichting, berekening en aanrekening](#cost-commitment--calculation-and-charging).

## Een budget {#creating-a-budget} maken

Begrotingen worden gemaakt op de kaart, via het knooppunt **[!UICONTROL Campaign management > Budgets]**. Met de knop **[!UICONTROL New]** op de werkbalk kunt u een budget maken.

* Nieuwe begroting toevoegen

   Klik op het pictogram **[!UICONTROL New]**, geef een naam en sla het budget op.

* Invoering van het oorspronkelijke bedrag

   Vermeld het toegewezen bedrag in het desbetreffende veld. De andere bedragen worden automatisch ingevoerd. Zie [Hoeveelheden berekenen](#calculating-amounts).

* Vaststelling van de geldigheidsperiode

   Geef de begin- en einddatum op. Deze informatie is slechts indicatief.

* Uitgaven

   Maak de uitgavencategorieën waarin de kosten van deze begroting voor campagnes, taken, enz. zijn ondergebracht. kan worden gekoppeld. Zie [Uitgaven categorieën](#expense-categories).

   ![](assets/s_ncs_user_budget_create_and_save.png)

>[!NOTE]
>
>U kunt een gerelateerd budget selecteren.
>
>Raadpleeg [Een budget koppelen aan een ander](#linking-a-budget-to-another) voor meer informatie.

### Hoeveelheden {#calculating-amounts} berekenen

Elke begroting wordt bepaald door een aanvangsbedrag dat wordt afgetrokken van de kosten van de verschillende campagnes, leveringen of taken die ermee verband houden nadat deze gepland of uitgevoerd zijn. De status van de (geplande, gereserveerde, vastgelegde, bestede of gefactureerde bedragen) hangt af van het soort kosten en het niveau van de vastlegging dat in de campagne, levering of taak is gedefinieerd.

>[!NOTE]
>
>De voor de categorieën ingevoerde bedragen moeten overeenkomen met de begrotingsmiddelen die in het veld **[!UICONTROL Allocated]** zijn gedefinieerd.

Voor campagnes kunnen, afhankelijk van het niveau van de verbintenis, kosten worden gepland, vastgelegd of gereserveerd voor een toekomstige actie.

![](assets/s_user_cost_op_engaged.png)

>[!CAUTION]
>
>Wanneer een campagne wordt gecreeerd, moet de vooruitgangsstatus in **[!UICONTROL Budget]** worden geplaatst aan **[!UICONTROL Defined]** om de kosten in rekening te brengen die op uitvoering moeten worden genomen. Als de status **[!UICONTROL Being edited]** is, worden de kosten niet geconsolideerd.
>   
>De optie **[!UICONTROL Commitment level]** is een projectie van de kosten in de toekomst voordat ze op de begroting worden afgeschreven. Afhankelijk van de voortgang van een campagne, taak of levering, kunt u besluiten een hoger of lager verbintenisniveau toe te wijzen (1). Geplant, 2. Gereserveerd, 3. Toegewezen) gebruikend de combodoos.

De geraamde kosten van een webcampagne bedragen bijvoorbeeld 45.000 euro.

![](assets/s_user_edit_budget_node_impact_0.png)

Wanneer voor de campagne de status van begrotingsschepping op **[!UICONTROL Defined]** is ingesteld, worden de werkelijke kosten van de campagne (of, indien dit niet het geval is, de berekende kosten) in de begrotingstotalen opgenomen.

![](assets/s_user_budget_in_op_a.png)

Afhankelijk van de mate van vastlegging van de campagnebegroting wordt het bedrag in het veld **[!UICONTROL Planned]**, **[!UICONTROL Reserved]** of **[!UICONTROL Committed]** opgenomen.

Het niveau van de verbintenis kan worden gewijzigd:

* in **campagne** niveau, in **[!UICONTROL Budget]** venster, dat in **[!UICONTROL Edit]** tabel wordt gevonden. Dit is waar begrotingen, kosten en uitgaven worden gevormd.
* in **tasks** niveau, in **[!UICONTROL Expenses and revenues]** venster.

![](assets/s_user_op_engagement_level_costs.png)

Wanneer het budget **[!UICONTROL Reserved]** is, wordt de update automatisch uitgevoerd voor het aangerekende budget.

![](assets/s_user_edit_budget_node_impact_2.png)

De procedure is op taakniveau hetzelfde.

![](assets/s_user_edit_budget_node_impact_task.png)

Wanneer een uitgave aanleiding geeft tot een factuur en de factuur wordt betaald, wordt het bedrag ervan in het veld **[!UICONTROL Invoiced]** vermeld.

### Onkostencategorieën {#expense-categories}

De bedragen kunnen in verschillende uitgavencategorieën worden verdeeld voor een betere leesbaarheid van de gegevens en voor een gedetailleerdere rapportage van marketinginvesteringen. De uitgavencategorieën worden bepaald tijdens begrotingsverwezenlijking, via **[!UICONTROL Budgets]** knoop van de boom.

Als u een categorie wilt toevoegen, klikt u op de knop **[!UICONTROL Add]** in de onderste sectie van het venster.

![](assets/s_user_budget_category.png)

U kunt een categorie uit de bestaande categorie selecteren of een nieuwe categorie definiëren door deze rechtstreeks in het veld in te voeren. Wanneer u uw invoer bevestigt, kunt u deze categorie toevoegen aan de lijst met bestaande categorieën en deze indien nodig koppelen aan een Natuur. Deze informatie zal in de begrotingsverslagen worden gebruikt.

### Een budget koppelen aan een andere {#linking-a-budget-to-another}

U kunt een begroting koppelen aan een hoofdbegroting. Hiervoor selecteert u het hoofdbudget op het gebied **[!UICONTROL related budget]** van de secundaire begrotingen.

![](assets/budget_link.png)

Er wordt een extra tabblad toegevoegd aan de hoofdbegroting om de lijst met verwante budgetten weer te geven.

![](assets/budget_link_new_tab.png)

Deze informatie wordt overgedragen naar de begrotingsverslagen.

## Onkostenposten {#adding-expense-lines} toevoegen

De begrotingslijnen worden automatisch toegevoegd. Zij worden gecreeerd tijdens leveringsanalyse en wanneer een taak wordt gebeëindigd.

![](assets/s_ncs_user_budget_line_edit.png)

Voor elke campagne, levering of taak worden de gegenereerde kosten gegroepeerd in de uitgavenposten van de begroting waarvoor ze worden aangerekend. Deze uitgavenlijnen worden gecreëerd op basis van de kostenlijnen van de betrokken dienstverlener en berekend via de bijbehorende kostenstructuren.

Elke uitgavenpost bevat daarom de volgende informatie:

* De campagne en de uitvoering of taak waarmee zij verband houdt
* Het bedrag berekend op basis van de kostenstructuur of de geraamde voorlopige kosten
* Reële kosten van de betrokken levering of taak
* De corresponderende factuurlijn (alleen MRM)
* Lijst van kosten berekend per kostencategorie (indien er een kostenstructuur bestaat)

In het bovenstaande voorbeeld bevat de bewerkte uitgavenlijn de kosten die zijn berekend voor de **New cards** levering voor de **Loyalty Spring Pack** campagne. Wanneer de levering wordt uitgegeven, laat het **[!UICONTROL Direct Mail]** lusje u zien hoe de uitgavenlijn wordt berekend.

De kostenberekening voor deze levering is gebaseerd op de kostencategorieën die voor de betrokken dienstverlener zijn geselecteerd:

![](assets/s_user_edit_del_supplier_costs.png)

Volgens de gekozen kostencategorieën worden de overeenkomstige kostenstructuren toegepast om de kostenposten te berekenen. In dit voorbeeld zijn de kostenstructuren voor de betrokken dienstverlener als volgt:

![](assets/s_user_edit_node_supplier_costs.png)

>[!NOTE]
>
>Kostencategorieën en -structuren worden weergegeven in [Een serviceprovider en de bijbehorende kostencategorieën maken](../../campaign/using/providers--stocks-and-budgets.md#creating-a-service-provider-and-its-cost-categories).

## Kostenverplichting, berekening en aanrekening {#cost-commitment--calculation-and-charging}

Kosten kunnen worden vastgelegd voor leveringen en taken. Afhankelijk van de voortgang van het proces waarmee het verband houdt, wordt de status van een kostprijs bijgewerkt.

### Kostprijsberekeningsproces {#cost-calculation-process}

De kosten zijn in drie categorieën onderverdeeld:

1. Geraamde voorlopige kosten

   De geraamde voorlopige kosten zijn een raming van de kosten voor het verloop van de campagne. Zolang deze wordt bewerkt, worden de ingevoerde bedragen niet geconsolideerd. Het moet **[!UICONTROL Specified]** status hebben om de bedragen in te brengen om in de berekeningen in aanmerking te worden genomen.

   Dit bedrag wordt handmatig ingevoerd en kan worden uitgesplitst in verschillende uitgavencategorieën. Als u de kosten omlaag wilt brengen, klikt u op de koppeling **[!UICONTROL Breakdown...]** en vervolgens op de knop **[!UICONTROL Add]** om een nieuw bedrag te definiëren.

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
   >Met de koppeling **[!UICONTROL Breakdown]** kunt u de details van de berekening en de laatste berekeningsdatum bekijken.

1. Reële kosten

   De werkelijke kosten worden handmatig ingevoerd en worden indien nodig uitgesplitst in verschillende kostencategorieën.

### Berekening en oplading {#calculation-and-charging}

De kosten worden berekend via kostenstructuren en worden in rekening gebracht op de in de betrokken campagnes, leveringen of taken geselecteerde budgetten.

De bedragen die via de goedkeuring van de begroting voor campagnes zijn vastgelegd, kunnen worden gecontroleerd. Er kunnen extra taken in de vorm van een controlepunt worden gemaakt in een campagne om andere goedkeuringen in te stellen. Zie [Typen taken](../../campaign/using/creating-and-managing-tasks.md#types-of-task).

### Voorbeeld {#example}

We gaan een campagne opzetten met:

* Een directe postlevering die de kostenstructuren van een dienstverlener gebruikt
* Een taak met vaste kosten
* Een taak met dagelijkse kosten

#### Stap 1 - Het creëren van de begroting {#step-1---creating-the-budget}

1. Maak een nieuw budget via het knooppunt **[!UICONTROL Campaign management > Budgets]**.

1. Definieer een budget van 10.000 EUR in het veld **[!UICONTROL Allocated]** van de sectie **[!UICONTROL Amounts]**. Voeg twee uitgavencategorieën in de onderste sectie van het venster toe:

![](assets/s_user_cost_mgmt_sample_1.png)

#### Stap 2 - Het vormen van de dienstverlener en het bepalen van de kostenstructuren {#step-2---configuring-the-service-provider-and-defining-the-cost-structures}

1. Creeer een dienstverlener en een de dienstmalplaatje met zijn kostenstructuur van de **[!UICONTROL Administration > Campaigns]** knoop. Raadpleeg [Een serviceprovider en de bijbehorende kostencategorieën maken](../../campaign/using/providers--stocks-and-budgets.md#creating-a-service-provider-and-its-cost-categories) voor meer informatie.

   Maak voor direct mailverkeer kostencategorieën **[!UICONTROL Envelopes]** (typen 114x229 en 162x229), **[!UICONTROL Postage]** en **[!UICONTROL Print]** (typen A3 en A4). En creeer dan de volgende kostenstructuren:

   ![](assets/s_user_cost_mgmt_sample_2.png)

1. Voeg een vaste kostprijs toe (in de kostencategorieën) waarvan de berekening vast is en waarvan het bedrag leeg is (in de desbetreffende kostenstructuur) en die voor elke levering afzonderlijk wordt gespecificeerd.

   ![](assets/s_user_cost_mgmt_sample_5.png)

   Voor taken maakt u de volgende twee kostencategorieën:

   * **[!UICONTROL Room reservation]** (Kleine kamer en Grote kamer), met een vaste  **** kostenstructuur van 300 en 500 euro:

   ![](assets/s_user_cost_mgmt_sample_6.png)

   * **[!UICONTROL Creation]** (**Inhoudsmodel** type), met een  **** dagelijkse kostenstructuur van 300 euro:

   ![](assets/s_user_cost_mgmt_sample_7.png)

#### Stap 3 - De kosten van de begroting in de campagne {#step-3---charging-the-budget-in-the-campaign}

1. Maak een campagne en selecteer het budget dat in Stap 1 wordt gemaakt.

   >[!NOTE]
   >
   >Standaard wordt het voor het programma geselecteerde budget toegepast op alle campagnes in het programma.

   ![](assets/s_user_cost_mgmt_sample_4.png)

1. Geef de geraamde voorlopige kosten op, uitgesplitst:

   ![](assets/s_user_cost_mgmt_sample_9.png)

1. Klik **[!UICONTROL Ok]** en dan **[!UICONTROL Save]** om deze informatie te bevestigen. De berekende kosten van de campagne worden vervolgens bijgewerkt met de geraamde voorlopige kosten.

#### Stap 4 - Het creëren van de directe postlevering {#step-4---creating-the-direct-mail-delivery}

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

De uitgavenlijn betreffende de levering wordt toegevoegd op **[!UICONTROL Edit > Budget]** lusje van de campagne. Bewerk de tabel om de details van de berekening weer te geven.

![](assets/s_user_cost_mgmt_sample_11.png)

De voor de levering berekende kosten worden met deze informatie bijgewerkt:

![](assets/s_user_cost_mgmt_sample_12.png)

Wanneer u de berekende kosten bewerkt, kunt u de uitsplitsing van de kosten en de status en datum van de kostenberekening controleren.

#### Stap 5 - Het creëren van taken {#step-5---creating-tasks}

Aan deze campagne, zullen wij de twee taken toevoegen waarvoor de kostenstructuren vroeger werden gecreeerd (zie [Stap 2 - het Vormen van de dienstverlener en het bepalen van de kostenstructuren](#step-2---configuring-the-service-provider-and-defining-the-cost-structures)). Klik hiertoe op de knop **[!UICONTROL Add a task]** in het campagnemdashboard. Geef de taak een naam en klik op **[!UICONTROL Save]**.

1. De taak wordt vervolgens toegevoegd aan de takenlijst. U moet het uitgeven om het te vormen.

1. Selecteer op het tabblad **[!UICONTROL Properties]** de service en de bijbehorende kostencategorie:

   ![](assets/s_user_cost_mgmt_sample_14.png)

1. Klik vervolgens op het pictogram **[!UICONTROL Expenses and revenue]** van de taak en geef de geschatte voorlopige kosten op.

   ![](assets/s_user_cost_mgmt_sample_15.png)

   Wanneer de taak is gered, worden de berekende kosten gespecificeerd met de waarde die voor de geschatte voorlopige kosten wordt ingevoerd.

   Wanneer de taak is voltooid (status **[!UICONTROL Finished]**), worden de berekende kosten automatisch bijgewerkt met de kosten van de Grote Ruimte zoals die in zijn kostenstructuur zijn ingegaan. Deze kosten worden ook in deze categorie in de uitsplitsing weergegeven.

1. Vervolgens maakt u een tweede taak volgens dezelfde procedure. die langer dan vijf dagen zijn gepland en betrekking hebben op de eerder gemaakte kostenstructuur.

   ![](assets/s_user_cost_mgmt_sample_16.png)

   Wanneer de taak is voltooid, worden de berekende kosten gespecificeerd met de waarde van de gerelateerde kostenstructuur, d.w.z. 1500 euro in ons voorbeeld (5 dagen x 300 euro):

   ![](assets/s_user_cost_mgmt_sample_17.png)

#### Stap 6 - Werk de status van het campagnebudget {#step-6---update-the-campaign-budget-status} bij

Wanneer de campagne wordt gevormd, kan zijn status worden bijgewerkt door het te plaatsen aan **[!UICONTROL Specified]**. De berekende kosten van de campagne vermelden vervolgens de som van de berekende kosten van de levering en de taken van de campagne:

![](assets/s_user_cost_mgmt_sample_18.png)

#### Begrotingsgoedkeuring {#budget-approval}

Wanneer goedkeuring wordt geactiveerd, kunt u een speciale koppeling gebruiken om het budget van het campagnesdashboard goed te keuren. Deze koppeling wordt weergegeven wanneer de doelworkflow is gestart en een direct mailbericht moet worden goedgekeurd.

![](assets/s_user_cost_mgmt_sample_19.png)

Vervolgens kunt u op de koppeling klikken om goedkeuring te verlenen of af te wijzen, of de koppeling gebruiken in de e-mail met de kennisgeving als er voor deze campagne een melding is geactiveerd.

Wanneer de begroting is goedgekeurd en de levering is voltooid, worden de kosten automatisch geüpload via een speciale technische workflow.

## Bestellingen en facturen {#orders-and-invoices}

In de context van MRM, kunt u orden bij een dienstverlener bewaren en facturen uitgeven. De volledige levenscyclus van deze bestellingen en facturen kan via de interface van Adobe Campaign worden beheerd.

### Maken van bestelling {#order-creation}

Als u een nieuwe bestelling wilt opslaan bij een serviceprovider, klikt u op het knooppunt **[!UICONTROL MRM > Orders]** van de structuur en vervolgens op de knop **[!UICONTROL New]**.

Vermeld het ordernummer, de betrokken dienstverlener en het totale bedrag van de order.

![](assets/s_user_cost_create_order.png)

### Facturen {#issuing-and-tracking-invoices} uitgeven en volgen

Voor elke dienstverlener, kunt u facturen bewaren en hun status en het in rekening gebrachte budget bepalen.

Facturen worden gemaakt en opgeslagen in het knooppunt **[!UICONTROL MRM > Invoices]** van de Adobe Campaign-structuur.

![](assets/s_user_cost_create_invoice.png)

Een factuur bestaat uit factuurlijnen waarvan het totaal automatisch het bedrag kan berekenen. Deze regels worden handmatig gemaakt op het tabblad **[!UICONTROL Invoice lines]**. Zij kunnen met een orde worden geassocieerd om de informatie aan de orden te uploaden.

![](assets/s_user_cost_invoice_add_line.png)

De facturen van elke serviceprovider worden weergegeven op het tabblad **[!UICONTROL Invoices]** van het profiel:

![](assets/s_ncs_user_invoice_from_supplier.png)

Op het tabblad **[!UICONTROL Details]** kunt u de inhoud van de factuur weergeven.

Klik op **[!UICONTROL Add]** om een nieuwe factuur te maken.
