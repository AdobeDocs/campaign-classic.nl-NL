---
solution: Campaign Classic
product: campaign
title: Voorbeelden
description: Voorbeelden
audience: campaign
content-type: reference
topic-tags: distributed-marketing
translation-type: tm+mt
source-git-commit: c625b4109e2cb47446331cd009ff9827c8267c93
workflow-type: tm+mt
source-wordcount: '1297'
ht-degree: 0%

---


# Voorbeelden{#examples}

## Een lokale campagne maken (op formulier) {#creating-a-local-campaign--by-form-}

De **Door vorm** typeWebinterface impliceert het gebruiken van **Webtoepassing**. Afhankelijk van zijn configuratie, kan deze Webtoepassing om het even welk type van bepaalde gepersonaliseerde elementen bevatten. U kunt bijvoorbeeld koppelingen voorstellen om het doel, het budget, de inhoud, enzovoort te evalueren. via specifieke API&#39;s.

>[!NOTE]
>
>API&#39;s worden beschreven in een speciaal document, waartoe de toegang afhankelijk is van uw contract. Zie [API](../../configuration/using/about-web-services.md).
>
>De toepassing van het Web die in dit voorbeeld wordt gebruikt is geen app van het Web die uit-van-de-doos met Adobe Campaign komt. Als u een formulier in een campagne wilt gebruiken, moet u de toegewijde webtoepassing maken.

Wanneer u de campagnemalplaatje maakt, klikt u op het pictogram **[!UICONTROL Zoom]** in de optie **[!UICONTROL Web interface]** van de koppeling **[!UICONTROL Advanced campaign settings...]** om details van de webtoepassing te openen.

![](assets/mkg_dist_local_op_form1.png)

>[!NOTE]
>
>De toepassingsparameters van het Web zijn slechts beschikbaar in het campagnemalplaatje.

Selecteer op het tabblad **[!UICONTROL Edit]** de **Campagnevolgorde** activiteit en open deze om de inhoud te openen.

![](assets/mkg_dist_web_app1.png)

In dit voorbeeld omvat de **Campagnevolgorde**-activiteit:

* velden die de lokale entiteit tijdens de bestelling moet invoeren;

   ![](assets/mkg_dist_web_app2.png)

* koppelingen die de lokale entiteit in staat stellen de campagne te evalueren (bijvoorbeeld het doel, het budget, de inhoud, enz.);

   ![](assets/mkg_dist_web_app3.png)

* scripts waarmee u het resultaat van deze evaluaties kunt berekenen en weergeven.

   ![](assets/mkg_dist_web_app4.png)

In dit voorbeeld worden de volgende API&#39;s gebruikt:

* Voor de doelevaluatie:

   ```
   var res = nms.localOrder.EvaluateTarget(ctx.localOrder);
   ```

* Voor de begrotingsevaluatie

   ```
   var res = nms.localOrder.EvaluateDeliveryBudget(ctx.@deliveryId, NL.XTK.parseNumber(ctx.@compt));
   ```

* Voor de evaluatie van de inhoud

   ```
   var res = nms.localOrder.EvaluateContent(ctx.localOrder, ctx.@deliveryId, "html", resSeed.@id);
   ```

## Een samenwerkingscampagne maken (door goedkeuring als doel) {#creating-a-collaborative-campaign--by-target-approval-}

### Inleiding {#introduction}

U bent de marketingmanager voor een groot kledingmerk dat een online winkel en verschillende boutiques in de hele VS heeft. Nu de lente is aangekomen, besluit u om een speciale aanbieding te maken die uw beste klanten 50% korting op alle jurken in uw catalogus zal geven.

Dit aanbod is gericht op de beste klanten van je Amerikaanse winkels, dat wil zeggen die meer dan $300 hebben uitgegeven sinds het begin van het jaar.

Daarom besluit u Distributed Marketing te gebruiken om een samenwerkingscampagne (door doelgoedkeuring) te maken waarmee u de beste klanten van uw winkels (gegroepeerd per regio) kunt selecteren, die de e-maillevering met de speciale aanbieding zullen ontvangen.

Het eerste deel van dit voorbeeld illustreert uw lokale entiteiten die het bericht van de campagneverwezenlijking ontvangen, en hoe zij het kunnen gebruiken om de campagne te evalueren en het te bestellen.

In het tweede deel van dit voorbeeld wordt uitgelegd hoe u uw campagne kunt maken.

De stappen zijn als volgt:

**Voor de lokale entiteit**

1. Gebruik het bericht van de campagneverwezenlijking om tot de lijst van contacten toegang te hebben die door de centrale entiteit wordt geselecteerd.
1. Selecteer de contacten en keur participatie goed.

**Voor de centrale entiteit:**

1. Maak een **[!UICONTROL Data distribution]**-activiteit.
1. Maak de samenwerkingscampagne.
1. Publiceer de campagne.

### Plaatselijke entiteitzijde {#local-entity-side}

1. De lokale entiteiten die zijn gekozen om deel te nemen aan de campagne ontvangen een e-mailkennisgeving.

   ![](assets/mkg_dist_use_case_target_valid8.png)

1. Door op de koppeling **[!UICONTROL Access your contact list and approve targeting]** te klikken krijgt de lokale entiteit toegang (via webbrowser) tot de lijst met clients die voor de campagne zijn geselecteerd.

   ![](assets/mkg_dist_use_case_target_valid9.png)

1. De lokale entiteit maakt de controle van bepaalde contacten uit de lijst ongedaan omdat er al sinds het begin van het jaar contact met hen is opgenomen voor een soortgelijk aanbod.

   ![](assets/mkg_dist_use_case_target_valid10.png)

Zodra de controles zijn goedgekeurd, kan de campagne automatisch beginnen.

### Centrale zijde entiteit {#central-entity-side}

#### Een gegevensdistributieactiviteit {#creating-a-data-distribution-activity} maken

1. Als u een samenwerkingscampagne wilt instellen (door goedkeuring als doel), moet u eerst een **[!UICONTROL Data distribution activity]** maken. Klik op het pictogram **[!UICONTROL New]** in het knooppunt **[!UICONTROL Resources > Campaign management > Data distribution]**.

   ![](assets/mkg_dist_use_case_target_valid3.png)

1. Op het tabblad **[!UICONTROL General]** moet u het volgende opgeven:

   * de **[!UICONTROL Targeting dimension]**. Hier wordt de **Gegevensdistributie** uitgevoerd op **Ontvangers**.
   * de **[!UICONTROL Distribution type]**. U kunt een **Vaste grootte** of een **Grootte als percentage** kiezen.
   * de **[!UICONTROL Assignment type]**. Selecteer de optie **Lokale entiteit**.
   * de **[!UICONTROL Distribution type]**. Hier is het veld **[!UICONTROL Origin (@origin)]** aanwezig in de tabel Ontvanger waarmee u de relatie tussen de contactpersoon en de lokale entiteit kunt identificeren.
   * Het veld **[!UICONTROL Approval storage]**. Selecteer de optie **Lokale goedkeuring van ontvanger**.

1. Geef op het tabblad **[!UICONTROL Breakdown]** het volgende op:

   * de **[!UICONTROL Distribution field value]**, die overeenkomt met de lokale entiteiten die betrokken zijn bij de komende campagne.
   * de lokale entiteit **[!UICONTROL label]**.
   * de **[!UICONTROL Size]** (vast of als percentage). De standaardwaarde **0** omvat het selecteren van alle ontvangers verbonden aan de lokale entiteit.

   ![](assets/mkg_dist_use_case_target_valid4.png)

1. Sla de nieuwe gegevensdistributie op.

#### Een collaboratieve campagne maken {#creating-a-collaborative-campaign}

1. Van **[!UICONTROL Campaign management > Campaign]** knoop, creeer nieuw **[!UICONTROL collaborative campaign (by target approval)]**.
1. Maak op het tabblad **[!UICONTROL Targeting and workflows]** een workflow voor uw campagne. Dit moet een **Splitsing** activiteit bevatten waarin **[!UICONTROL Record count limitation]** door de **[!UICONTROL Data distribution]** activiteit wordt bepaald.

   ![](assets/mkg_dist_use_case_target_valid5.png)

1. Voeg een **[!UICONTROL Local approval]** actie toe waar u kunt specificeren:

   * de inhoud van het bericht die naar de lokale entiteiten in de kennisgeving zal worden verzonden;
   * de goedkeuringsherinnering;
   * de verwachte verwerking van de campagne.

   ![](assets/mkg_dist_use_case_target_valid7.png)

1. Sla uw record op.

#### De campagne {#publishing-the-campaign} publiceren

U kunt nu een **campagnepakket** van **Campagnes** universum toevoegen.

1. Kies uw **[!UICONTROL Reference campaign]**. Op het tabblad **[!UICONTROL Edit]** van uw pakket kunt u **[!UICONTROL Approval mode]** selecteren voor uw campagne:

   * in de modus **Handmatig** nemen de lokale entiteiten deel aan de campagne als ze de uitnodiging van de centrale entiteit accepteren. Zij kunnen vooraf geselecteerde contacten schrappen als zij willen en goedkeuring van de manager noodzakelijk is om hun deelname aan de campagne te bevestigen.
   * in de modus **Automatisch** moeten de lokale entiteiten deelnemen aan de campagne, tenzij ze zichzelf uit de campagne verwijderen. Ze kunnen contacten verwijderen zonder goedkeuring.

   ![](assets/mkg_dist_use_case_target_valid.png)

1. Op het tabblad **[!UICONTROL Description]** kunt u zowel een beschrijving voor uw campagne als alle documenten toevoegen die naar de lokale entiteiten moeten worden verzonden.

   ![](assets/mkg_dist_use_case_target_valid1.png)

1. Goedkeuren, vervolgens start u de workflow om het pakket te publiceren en beschikbaar te maken voor alle lokale entiteiten in een lijst met pakketten.

   ![](assets/mkg_dist_use_case_target_valid2.png)

## Een samenwerkingscampagne maken (op formulier) {#creating-a-collaborative-campaign--by-form-}

### Inleiding {#introduction-1}

U bent de marketingmanager voor een groot make-upmerk met een online winkel en verschillende boutiques in de hele VS. Als u uw wintervoorraad wilt verwijderen en ruimte wilt maken voor uw nieuwe voorraad, kiest u voor een speciale aanbieding die betrekking heeft op twee categorieën klanten: de ouder dan 30 jaar, aan wie je leeftijdsgevoelige huidverzorgingsproducten zult aanbieden, en de jonger dan 30 jaar, aan wie je de meest elementaire huidverzorgingsproducten zult aanbieden.

Daarom besluit u om Distributed Marketing te gebruiken om een samenwerkingscampagne (per formulier) te maken waarmee u clients van uw verschillende winkels kunt selecteren op basis van het leeftijdsbereik. Deze klanten ontvangen een e-maillevering met een speciaal voorstel dat op basis van hun leeftijdsbereik is aangepast.

Het eerste deel van dit voorbeeld illustreert uw lokale entiteiten die het bericht van de campagneverwezenlijking ontvangen, en hoe zij het kunnen gebruiken om de campagne te evalueren en het te bestellen.

In het tweede deel van dit voorbeeld wordt uitgelegd hoe u uw campagne kunt maken.

De stappen zijn als volgt:

**Voor de lokale entiteit**

1. Gebruik het bericht voor het maken van de campagne om het onlineformulier te openen.
1. Pas de campagne aan (doel, inhoud, leveringsvolume).
1. Controleer deze velden en wijzig deze indien nodig.
1. Uw deelname goedkeuren.
1. De manager van de lokale entiteit (of de centrale entiteit) keurt uw configuratie en participatie goed.

**Voor de centrale entiteit:**

1. Maak de samenwerkingscampagne.
1. Configureer **[!UICONTROL Advanced campaign settings...]** zoals u zou doen voor een lokale campagne.
1. Configureer de campagneworkflow en de levering op dezelfde manier als voor een lokale campagne.
1. Het webformulier bijwerken.
1. Maak het campagnepakket en publiceer het.

### Plaatselijke entiteitzijde {#local-entity-side-1}

1. De lokale entiteiten die voor deelname aan de campagne zijn geselecteerd, ontvangen een e-mailbericht waarin ze op de hoogte worden gesteld van hun deelname aan de campagne.

   ![](assets/mkg_dist_use_case_form_7.png)

1. De lokale entiteiten vullen het gepersonaliseerde formulier in en daarna:

   * het streefcijfer en de begroting te evalueren;
   * een voorvertoning van de inhoud van de levering;
   * hun deelname goedkeuren.

      ![](assets/mkg_dist_use_case_form_8.png)

1. De exploitant die belast is met het valideren van orders, keurt hun deelname goed.

   ![](assets/mkg_dist_use_case_form_9.png)

### Centrale zijde entiteit {#central-entity-side-1}

1. Als u een samenwerkingscampagne wilt implementeren (op formulier), moet u een campagne maken met de sjabloon **Samenwerken (op formulier)**.

   ![](assets/mkg_dist_use_case_form_1.png)

1. Klik op het tabblad **[!UICONTROL Edit]** van de campagne op de koppeling **[!UICONTROL Advanced campaign settings...]** om deze te configureren als een lokale campagne. Zie [Een lokale campagne maken (op formulier)](#creating-a-local-campaign--by-form-).

   ![](assets/mkg_dist_use_case_form_2.png)

1. Configureer de campagneworkflow en het webformulier. Zie [Een lokale campagne maken (op formulier)](#creating-a-local-campaign--by-form-).
1. Maak uw campagnepakket door het uitvoeringsschema en de betrokken lokale entiteiten op te geven.

   ![](assets/mkg_dist_use_case_form_3.png)

1. Voltooi de pakketconfiguratie door de goedkeuringswijze op **[!UICONTROL Edit]** tabel te selecteren.

   ![](assets/mkg_dist_use_case_form_4.png)

1. Op het tabblad **[!UICONTROL Description]** kunt u een beschrijving van het campagnepakket invoeren, een meldingsbericht dat naar lokale entiteiten moet worden verzonden wanneer het pakket wordt gepubliceerd en informatieve documenten aan uw campagnepakket toevoegen.

   ![](assets/mkg_dist_use_case_form_5.png)

1. Goedkeuren van het pakket om het te publiceren.

   ![](assets/mkg_dist_use_case_form_6.png)

