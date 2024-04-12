---
product: campaign
title: Verklarende woordenlijst voor de interliniëring van campagnes
description: Verklarende woordenlijst voor de interliniëring van campagnes
feature: Interaction, Offers
audience: interaction
content-type: reference
topic-tags: interaction-overview
exl-id: 9e199b7c-9307-4797-bf86-7940388555bc
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '1103'
ht-degree: 0%

---

# Verklarende woordenlijst voor de interliniëring van campagnes{#i-glossary}



Hieronder vindt u de definitie van de belangrijkste interactieelementen.

* **Omgeving**: set met een aanbiedingscatalogus en haken (aanbiedingsruimten). U moet één milieu tot stand brengen door dimensie te richten. Er zijn twee soorten omgevingen:

   * **Ontwerpomgeving**: omgeving waarin aanbiedingen worden gemaakt en/of typologieregels worden vastgesteld (regels die bepalen welke aanbiedingen aan een doelpersoon moeten worden gepresenteerd of niet). In deze tabel wordt ook de tabel van de personen voor wie de aanbiedingen bestemd zijn, en de tabel voor het opslaan van alle voorstellen voor aanbiedingen, gedefinieerd. De **[!UICONTROL Design environment]** De node bevat submappen voor de aanbiedingsruimte, vooraf gedefinieerde filters en categorieën aanbiedingen. Voor elke **[!UICONTROL Design environment]** er is één overeenkomende alleen-lezen **[!UICONTROL Live environment]**, op basis van dezelfde **[!UICONTROL Design environment]**.
   * **Live omgeving**: milieu gekoppeld aan een **[!UICONTROL Design environment]**. Het bevat alleen-lezen aanbiedingen waarvan de inhoud en geschiktheid zijn goedgekeurd via de **[!UICONTROL Design environment]**. Zij moeten worden geselecteerd om op een Website worden voorgesteld of in een bericht worden opgenomen.

* **Ruimte voor aanbod**: map waarin de locatie wordt gedefinieerd waar de aanbieding wordt weergegeven. Als u een spatie definieert, kunt u het gebruikte kanaal opgeven, opgeven of het kan worden gebruikt in de eenheidsmodus (standaard: alleen in de batchmodus), de inhoud van de aanbieding samenstellen met behulp van renderfuncties en de aanbieding van de aangeboden aanbiedingen specificeren. Een ruimte is een interface tussen het kanaal en de aanbiedingsmotor.

  >[!IMPORTANT]
  >
  >Een aanbiedingsruimte is geen communicatiekanaal, maar valt samen met een specifieke expositielocatie op het kanaal. Aanbiedingen die op een website worden weergegeven, kunnen bijvoorbeeld twee spaties op dezelfde pagina beslaan. In dit geval hebben we dan twee spaties voor hetzelfde kanaal.
  >
  >De ruimten moeten in de specificaties worden gedefinieerd en mogen tijdens het project niet worden gewijzigd.

* **Aanbiedingscatalogus**: set met in Adobe Campaign gedefinieerde aanbiedingen die tijdens een interactie kan worden geselecteerd. De catalogus is hiërarchisch geordend met elk knooppunt dat overeenkomt met een categorie.
* **Categorie**: een map die gekoppeld is aan de aanbiedingscatalogus in een omgeving waarin aanbiedingen worden georganiseerd op basis van de aard, de datum waarop de aanbieding in aanmerking komt en het thema van de toepassing. Een categorie kan subcategorieën bevatten, die alle kenmerken van de bovenliggende categorie overnemen. Voor een categorie kunnen subsidiabiliteitsregels worden vastgesteld om deze voor meerdere aanbiedingen te delen.
* **Toepassingsthema&#39;s**: de sleutelwoorden die in de categorie worden bepaald, die u aanbiedingen laten filtreren wanneer zij aan een binnenkomend of uitgaand kanaal worden voorgesteld door de selectie van aanbiedingen tot één of twee categorieën te beperken.

  >[!NOTE]
  >
  >De categorieën van het kind erven de thema&#39;s die in de oudercategorie worden geïdentificeerd.

* **Subsidiabiliteitsregels**: beperkingen die van toepassing zijn op een omgeving, categorie of aanbieding met betrekking tot de geldigheidsperiode, het doel en het gewicht. Hiermee kunt u ervoor zorgen dat een aanbieding in overeenstemming is met de beoogde contactpersoon.

  In de omgeving omvatten de subsidiabiliteitsregels presentatieregels die worden toegepast op de aanbiedingen en de doelgroepen.

  In de categorieën kunt u met de subsidiabiliteitsregels de geldigheid van de categorie in de tijd beperken, toepassingsthema&#39;s definiëren en bepalen welke personen het doelwit moeten zijn. Zij kunnen ook gedurende een bepaalde periode een vermenigvuldigingsgewicht krijgen. Op deze manier kunt u de regels voor aanbiedingen in andere rubrieken delen en wordt het beheer ervan vereenvoudigd.

  In de aanbiedingen kunt u met de subsidiabiliteitsregels de geldigheid van de aanbiedingen in de tijd beperken en bepalen welke personen het doelwit zijn.

* **Arbitrage**: aanbiedingen selecteren die in een omgeving worden weergegeven (in aanmerking komende aanbiedingen). Het arbitragebeginsel rangschikt de aanbiedingen naar prioriteit op basis van de criteria die in de categorieën, aanbiedingen en contextaanbiedingen zijn vastgesteld.
* **Contact**: een contact van een binnenkomende interactie. Tijdens de verwerking van de motorvraag, wordt het contact geassocieerd aan een gericht afmeting. Er zijn twee soorten contacten:

   * **[!UICONTROL Identified contact]** : een contact dat vrijwillig op het kanaal is geïdentificeerd. In uitgaande interactie, wordt het contact automatisch geïdentificeerd.
   * **[!UICONTROL Anonymous contact]** : een contactpersoon die niet vrijwillig via het kanaal is geabonneerd, maar impliciet via een cookie kan worden geïdentificeerd. Deze terminologie wordt alleen gebruikt voor binnenkomende interacties.

     >[!NOTE]
     >
     >Niet-geïdentificeerde, anonieme contacten worden toegeschreven aan de bezoeker richtend dimensie.

* **Uitgaande interactie**: oproep aan de interactie-engine vanuit een lijst met contactpersonen (wordt gebruikt voor het verzenden van e-mails, e-mail, enz.). De zelfde regels en de processen worden toegepast op elk contact. Dit type interactie wordt over het algemeen verwerkt in batchmodus.
* **Binnenkomende interactie**: interactie na een inkomende vraag die door de actie van een contact op het kanaal wordt geproduceerd. Dit type interactie wordt over het algemeen in de monistische modus verwerkt.
* **Batchmodus**: in de batchmodus kunt u de beste aanbieding voor een set contactpersonen selecteren. De regels voor geschiktheid/prioritering worden toegepast op alle contactpersonen in de set. Deze wijze wordt over het algemeen gebruikt voor uitgaande interactie.
* **Eenvoudige modus**: er wordt één contactpersoon tegelijk verwerkt. Deze wijze wordt over het algemeen gebruikt voor binnenkomende interactie en transactieberichten.
* **Identificatiemodus**: verwijst naar de status van een contactpersoon.

   * **[!UICONTROL explicit]** : het contact wordt geïdentificeerd na hun login op de kanaalinterface.
   * **[!UICONTROL implicit]** : de contactpersoon is geïdentificeerd door een cookie (permanent of sessie). Het kan als anoniem of geïdentificeerd contact worden verwerkt.
   * **[!UICONTROL anonymous]** : de contactpersoon kan niet worden geïdentificeerd.

* **In aanmerking komende aanbieding**: bied aan die aan de beperkingen voldoen die stroomopwaarts worden bepaald die aan een doel constant kunnen worden aangeboden.
* **Presentatieregels**: typologische regels waarnaar in de aanbiedingsomgeving wordt verwezen, waarmee u bepaalde aanbiedingen kunt uitsluiten door rekening te houden met de voorpositiegeschiedenis.
* **Dikte**: formules waarmee u de relevantie van een aanbieding nauwkeurig kunt berekenen, zodat u de meest relevante aanbieding kunt selecteren. Het gewicht wordt gedefinieerd in de aanbiedingen. In aanmerking komende aanbiedingen worden in afnemende gewichtsvolgorde in aanmerking genomen.
* **Renderfunctie**: functie die in de aanbiedingsruimte is gedefinieerd om de aanbiedingsweergave te construeren op basis van de kenmerken die in de aanbieding zijn gedefinieerd. Er zijn drie verschillende renderingfuncties: HTML, XML en tekst.
* **Voorstel**: resultaat van de actie die bestaat uit het aanbieden van een of meer aanbiedingen aan een contactpersoon in een bepaalde ruimte (bijvoorbeeld banner op een website, e-mail of SMS). Dit resultaat wordt opgeslagen in de lijst met aanbiedingsvoorstellen. Het is echter niet verplicht de voorstellen op te slaan.
* **Simulatie**: module waarmee u de aanbiedingspresentatie op de beoogde ontvangers kunt testen voordat u de aanbiedingen daadwerkelijk verzendt.
* **Voorvertoning**: voorbeeld van de aanbieding zoals deze in de bijbehorende map wordt weergegeven. Het is toegankelijk vanuit het venster met aanbiedingsinstellingen of het contactprofiel.
* **Vooraf gedefinieerde filters**: vooraf gedefinieerde filterregels kunnen rekening houden met aanbiedingsparameters (bijvoorbeeld een aanbiedingscode). Ze kunnen opnieuw worden gebruikt nadat voorstellen zijn gemaakt.
* **Voorstelling**: informatie die door het kanaal wordt gebruikt om de aanbieding weer te geven. De aanbiedingsvertegenwoordiging kan van de teruggevende functie van de ruimte worden geconstrueerd waarop de aanbieding wordt vertegenwoordigd of direct in de interface (bijvoorbeeld, in het blok van HTML) ingegaan. Een aanbieding kan door de ruimte worden vertegenwoordigd.
* **Wijzigingsproces**: een geactiveerd proces in een geïdentificeerd milieu, verantwoordelijk voor het leiden van de vraag aan een anoniem milieu als het contact niet uitdrukkelijk en/of impliciet geïdentificeerd is.
