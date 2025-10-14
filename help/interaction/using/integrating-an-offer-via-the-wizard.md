---
product: campaign
title: Integreer een aanbieding via de assistent
description: Integreer een aanbieding via de assistent
feature: Interaction, Offers
audience: interaction
content-type: reference
topic-tags: delivering-an-offer
exl-id: 64aea8b9-7f06-4db0-a3e6-6a0e17c3ddcb
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '807'
ht-degree: 0%

---

# Integreer een aanbieding via de assistent{#integrating-an-offer-via-the-assistant}



Wanneer het creëren van een levering, zijn er twee mogelijke methodes om aanbiedingen te integreren:

* De aanbiedingsmotor aanroepen in de hoofdtekst van een levering.
* Verwijzen naar aanbiedingen via de leveringscontouren van een campagne. Deze methode wordt over het algemeen gebruikt voor papiercampagnes.

## Het leveren met een vraag aan de aanbiedingsmotor {#delivering-with-a-call-to-the-offer-engine}

Als u een aanbieding wilt presenteren tijdens een marketingcampagne, maakt u gewoon een klassieke leveringsactie op basis van het gekozen kanaal. De aanbiedingsengine wordt aangeroepen wanneer de leveringsinhoud wordt gedefinieerd door op het pictogram **[!UICONTROL Offers]** op de werkbalk te klikken.

![](assets/offer_delivery_009.png)

Leer meer over directe postleveringen [ in deze sectie ](../../delivery/using/about-direct-mail-channel.md). Leer meer over marketing campagnes in de [ documentatie van de Campagne v8 ](https://experienceleague.adobe.com/docs/campaign/automation/campaign-orchestration/set-up-campaigns.html){target=_blank}.

### Belangrijkste stappen voor het invoegen van een aanbieding in een levering {#main-steps-for-inserting-an-offer-into-a-delivery}

Voer de volgende stappen uit om voorstellen voor aanbiedingen in te voegen in een levering:

1. Klik in het leveringsvenster op het pictogram Aanbiedingen.

   ![](assets/offer_delivery_001.png)

1. Selecteer de ruimte die overeenkomt met uw aanbiedingsomgeving.

   ![](assets/offer_delivery_002.png)

1. Als u de keuze van de motor van de aanbiedingen wilt verfijnen, selecteert u de categorie waaruit de aan te bieden aanbieding(en) deel uitmaakt of een of meer thema&#39;s. We raden u aan slechts één van deze velden tegelijk te gebruiken om overbelasting van de beperkingen te voorkomen.

   ![](assets/offer_delivery_003.png)

   ![](assets/offer_delivery_004.png)

1. Geef het aantal voorstellen op dat u in de leveringstekst wilt invoegen.

   ![](assets/offer_delivery_005.png)

1. Selecteer indien nodig de optie **[!UICONTROL Exclude non-eligible recipients]** . Voor meer op dit, verwijs naar [ Parameters voor het roepen van aanbiedingsmotor ](#parameters-for-calling-offer-engine).

   ![](assets/offer_delivery_006.png)

1. Selecteer indien nodig de optie **[!UICONTROL Do not display anything if no offers are selected]** . Voor meer op dit, verwijs naar [ Parameters voor het roepen van aanbiedingsmotor ](#parameters-for-calling-offer-engine).

   ![](assets/offer_delivery_007.png)

1. Voeg de eigenschap(pen) in de leveringsinhoud in met de samenvoegvelden. Het aantal beschikbare voorstellen hangt van de manier af de motorvraag wordt gevormd en hun orde hangt van de prioriteit van aanbiedingen af.

   ![](assets/offer_delivery_008.png)

1. Voltooi de inhoud en verzend uw levering zoals gewoonlijk.

   ![](assets/offer_delivery_010.png)

### Parameters voor het aanroepen van de aanbiedingsengine {#parameters-for-calling-offer-engine}

* **[!UICONTROL Space]** : ruimte van de aanbiedingsomgeving die moet worden geselecteerd om de aanbiedingsengine te activeren.
* **[!UICONTROL Category]** : specifieke map waarin aanbiedingen worden gesorteerd. Als er geen categorie is opgegeven, zal de aanbiedingsengine rekening houden met alle aanbiedingen in de omgeving, tenzij een thema wordt geselecteerd.
* **[!UICONTROL Themes]** : sleutelwoorden die stroomopwaarts zijn gedefinieerd in de categorieën. Deze fungeren als een filter en u kunt het aantal aanbiedingen dat moet worden weergegeven, verfijnen door ze in een set categorieën te selecteren.
* **[!UICONTROL Number of propositions]** : het aantal aanbiedingen dat door de engine wordt geretourneerd en dat in de hoofdtekst van de levering kan worden ingevoegd. Als zij niet in het bericht worden opgenomen, zullen de aanbiedingen nog worden geproduceerd, maar niet voorgesteld.
* **[!UICONTROL Exclude non-eligible recipients]** : met deze optie kunt u de uitsluiting activeren of deactiveren van ontvangers voor wie er onvoldoende geschikte voorstellen zijn. Het aantal in aanmerking komende voorstellen kan lager zijn dan het gevraagde aantal voorstellen. Als deze doos wordt gecontroleerd, zullen de ontvangers die niet genoeg voorstellen hebben van de levering worden uitgesloten. Als u deze optie niet selecteert, worden deze ontvangers niet uitgesloten, maar hebben ze niet het gewenste aantal voorstellen.
* **[!UICONTROL Do not display anything if no offer is selected]** : met deze optie kunt u kiezen hoe het bericht wordt verwerkt als een van de voorstellen niet bestaat. Als dit selectievakje is ingeschakeld, wordt de representatie van het ontbrekende voorstel niet weergegeven en wordt er geen inhoud weergegeven in het bericht voor dit voorstel. Als de doos niet wordt gecontroleerd, wordt het bericht zelf geannuleerd tijdens het verzenden en de ontvangers zullen geen berichten meer ontvangen.

### Een voorstel invoegen in een levering {#inserting-an-offer-proposition-into-a-delivery}

De weergave van de aanbiedingen die moeten worden gepresenteerd, wordt in de hoofdtekst van de levering ingevoegd via de samenvoegvelden. Het aantal voorstellen wordt bepaald in de parameters van de vraag van de aanbiedingsmotor.

De levering kan worden gepersonaliseerd met de velden van de aanbieding of, in het geval van een e-mail, met de renderfuncties.

![](assets/offer_delivery_011.png)

## Leveren met leveringscontouren {#delivering-with-delivery-outlines}

Je kunt ook voorstellen in een levering presenteren met een leveringsoverzicht.

Voor meer informatie over leveringsoverzichten, verwijs naar de [ documentatie van de Campagne v8 ](https://experienceleague.adobe.com/docs/campaign/automation/campaign-orchestration/marketing-campaign-assets#delivery-outlines.html){target="_blank"}.

1. Maak een nieuwe campagne of open een bestaande campagne.
1. Open de leveringscontouren via het tabblad **[!UICONTROL Edit]** > **[!UICONTROL Documents]** van de campagne.
1. Voeg een omtrek toe en voeg zoveel aanbiedingen in als u wilt door met de rechtermuisknop op de omtrek te klikken en **[!UICONTROL New]** > **[!UICONTROL Offer]** te selecteren en vervolgens de campagne op te slaan.

   ![](assets/int_compo_offre1.png)

1. Maak een levering waarvan u de leveringscontouren kunt bekijken (bijvoorbeeld een direct-maillevering).
1. Klik op **[!UICONTROL Select a delivery outline]** wanneer u de levering bewerkt.

   >[!NOTE]
   >
   >Afhankelijk van het type levering vindt u deze optie in het menu **[!UICONTROL Properties]** > **[!UICONTROL Advanced]** (bijvoorbeeld voor e-mailleveringen).

   ![](assets/int_compo_offre2.png)

1. Met de knop **[!UICONTROL Offers]** kunt u vervolgens de aanbiedingsruimte en het aantal aanbiedingen voor de levering configureren.

   ![](assets/int_compo_offre3.png)

1. Voeg de voorstellen in het leveringslichaam toe gebruikend de verpersoonlijkingsgebieden (voor meer op dit, verwijs naar het [ Opnemen van een aanbiedingsvoorstel in een levering ](#inserting-an-offer-proposition-into-a-delivery) sectie), of in het geval van een directe postlevering, door het formaat van het extractiedossier uit te geven.

   De voorstellen zullen van de aanbiedingen worden geselecteerd waarnaar in het leveringsoverzicht wordt verwezen.

   >[!NOTE]
   >
   >Informatie over de rankings- en gewichten van de aanbieding wordt alleen in de tabel met voorstellen opgeslagen als de aanbiedingen rechtstreeks in de levering worden gegenereerd.
