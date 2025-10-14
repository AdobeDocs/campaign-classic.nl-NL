---
product: campaign
title: Beschrijving van Adobe Campaign Classic-gegevensmodel
description: Dit document beschrijft het Adobe Campaign-gegevensmodel
feature: Data Model
role: Data Engineer, Developer
exl-id: fc0fd23c-f9ea-4e30-b47b-a84143d882ca
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '2354'
ht-degree: 1%

---

# Beschrijving van gegevensmodel campagne{#data-model-description}


Adobe Campaign bevat een vooraf gedefinieerd datamodel. In deze sectie vindt u enkele details over de ingebouwde tabellen van het Adobe Campaign-gegevensmodel en de interactie ervan.

Ga naar **[!UICONTROL Admin > Configuration > Data schemas]** om de beschrijving van elke tabel te openen, selecteer een bron in de lijst en klik op de tab **[!UICONTROL Documentation]** .

![](assets/data-model_documentation-tab.png)

>[!NOTE]
>
>De fysieke en logische structuur van de data die in de applicatie worden overgedragen, wordt in XML beschreven. Het volgt een grammatica die specifiek is voor Adobe Campaign en een schema wordt genoemd. Voor meer op de schema&#39;s van Adobe Campaign, lees uit [ deze sectie ](../../configuration/using/about-schema-reference.md).

## Beschrijving van de belangrijkste tabellen {#description-main-tables}

Adobe Campaign vertrouwt op een relationele database die tabellen bevat die aan elkaar zijn gekoppeld.

Het volgende diagram toont de verbindingen tussen de belangrijkste bedrijfstabellen van het de gegevensmodel van Adobe Campaign met de belangrijkste gebieden voor elk.

<!--![](assets/data-model_diagram.png)-->

![](assets/data-model_simplified-diagram.png)

Het vooraf gedefinieerde Adobe Campaign-gegevensmodel bevat de onderstaande hoofdtabellen.

### NmsRecipient {#NmsRecipient}

Deze lijst past het **nms:recipient** schema aan.

Het is de standaardlijst die voor de **ontvangers van leveringen** wordt gebruikt. Bijgevolg bevat het de informatie die nodig is voor leveringen via de verschillende kanalen:

* sEmail: e-mailadres.
* iEmailFormat: voorkeursindeling voor e-mails (1 voor Tekst, 2 voor HTML en 0 als deze niet gedefinieerd zijn).
* sAddress1, sAddress2, sAddress3, sAddress4, sZipCode, sCity wordt gebruikt om het postadres te bouwen (in overeenstemming met de norm XPZ 10-011 AFNOR van Mei 1997).
* sPhone, sMobilePhone en sFax bevatten respectievelijk de telefoon-, mobiele telefoon- en faxnummers.
* iBlackList is de standaardmarkering voor niet-deelname die wordt gebruikt voor de profielen (1 betekent &quot;niet-geabonneerd&quot;, anders 0).

Het veld iFolderId is de externe sleutel die de ontvanger aan zijn uitvoeringsmap koppelt. Voor meer op dit, zie [ XtkFolder ](#XtkFolder).

Het veld sCountryCode is de 3166-1 Alpha 2 ISO-code (2 tekens) van het land dat aan de ontvanger is gekoppeld. Dit veld is in feite een buitenlandse sleutel in de referentietabel van het land (NmsCountry), die de landlabels en andere landcodegegevens bevat. Als het land niet is gevuld, wordt de waarde &#39;XX&#39; opgeslagen (en wordt gebruikt in plaats van een nul-id-record).

Voor meer op de Ontvankelijke lijst, zie [ deze sectie ](../../configuration/using/about-data-model.md#default-recipient-table).

### NmsGroup {#NmsGroup}

Deze lijst past het **nms:group** schema aan.

Het laat u toe om **statische groepen ontvangers** tot stand te brengen. Er is een veel-op-veel relatie tussen ontvangers en groepen. Eén ontvanger kan bijvoorbeeld tot meerdere groepen behoren en één groep kan meerdere ontvangers bevatten. Groepen kunnen handmatig worden gemaakt, via import of levering als doel. Groepen worden vaak gebruikt als leveringsdoelen. Er is een unieke index op het gebied die de interne naam van de sName groep vertegenwoordigt. De groep is gekoppeld aan een map (de sleutel is iFolderId. Voor meer op dit, zie [ XtkFolder ](#XtkFolder)).

### NmsRcpGrpRel {#NmsRcpGrpRel}

De NmsRcpGrpRel-relatietabel bevat alleen de twee velden die overeenkomen met de id&#39;s van de gekoppelde tabellen iRecipientId en iGroupId.

### NmsService {#NmsService}

Deze lijst past het **nms:service** schema aan.

In Adobe Campaign kunt u abonnementen op informatieservices (onderwerpen) maken en beheren. De lijst NmsService slaat de definitie van de informatiediensten (onderwerpen) op die u uw ontvangers aanbiedt om aan (een nieuwsbrief bijvoorbeeld) in te schrijven.

De diensten zijn entiteiten die aan groepen (statische ontvankelijke groeperingen) gelijkaardig zijn, behalve dat zij meer informatie verspreiden en gemakkelijke beheer van abonnementen en abonnementen via vormen toelaten.

Er is een unieke index op het gebied die de interne naam van de dienst sName vertegenwoordigt. De service is gekoppeld aan een map (de sleutel is iFolderId. Voor meer op dit, zie [ XtkFolder ](#XtkFolder)). Tot slot specificeert het iType gebied het leveringskanaal van deze dienst (0 voor e-mail, 1 voor SMS, 2 voor telefoon, 3 voor directe post en 4 voor fax).

### NmsSubscription {#NmsSubscription}

Deze lijst past het **nms:subscription** schema aan.

Het laat u toe om ontvankelijke abonnementen aan informatiediensten te beheren.

### NmsSubHisto {#NmsSubHisto}

Deze lijst past het **nms:subHisto** schema aan.

Als de abonnementen worden beheerd met behulp van webformulieren of de interface van de toepassing, worden alle abonnementen en aftekeningen in de tabel NmsSubHisto gehistoriseerd. In het veld iAction wordt de handeling (0 voor abonnement en 1 voor abonnement) opgegeven die wordt uitgevoerd op de datum die is opgeslagen in het veld tsDate.

### NmsDelivery {#NmsDelivery}

Deze lijst past het **nms:delivery** schema aan.

Elk verslag in deze lijst vertegenwoordigt a **leveringsactie** of a **leveringsmalplaatje**. Het bevat alle parameters die nodig zijn voor het uitvoeren van leveringen (doel, inhoud, enz.). Logboeken voor levering (uitzending) (NmsBroadLog) en bijbehorende URL&#39;s voor tracering (NmsTrackingUrl) worden tijdens de analysefase gemaakt (zie hieronder voor meer informatie over beide tabellen).

Er is een unieke index op het gebied die de interne naam van de levering sInternalName of het scenario vertegenwoordigt. De levering is gekoppeld aan een uitvoeringsmap (de externe sleutel is iFolderProcessId. Voor meer op dit, zie [ XtkFolder ](#XtkFolder)).

### XtkFolder {#XtkFolder}

Het bevat **alle omslagen in de boom** zichtbaar in het **3} lusje van de Navigatie {van de console.**

De mappen worden getypt: de waarde van het veld sModel geeft het type gegevens aan dat in de map kan worden opgenomen. Met dit veld kan de clientconsole de gegevens ook correct weergeven met de bijbehorende formulieren. De mogelijke waarden voor dit veld worden gedefinieerd in de navTree.

De structuur wordt beheerd door de velden iParentId en iChildCount. Het veld sFullName geeft het volledige pad van de map in de structuur. Tot slot is er een unieke index op het gebied die de interne naam van de sName omslag vertegenwoordigt.

## Aflevering en tekstspatiëring {#delivery-and-tracking}

Deze reeks lijsten is verbonden met de **Levering** module, die toestaat om leveringen en uiteindelijke kwesties te controleren wanneer de berichten worden verzonden. Voor meer op dit, zie [ Leveringen van de Controle ](../../delivery/using/about-delivery-monitoring.md). Voor meer bij het volgen, zie [ het Volgen berichten ](../../delivery/using/about-message-tracking.md).

![](assets/data-model_delivery.png)

**NmsBroadLogMsg**: Deze lijst past het **nms:broadLogMsg** schema aan. Het is een uitbreiding van de lijst van het leveringslogboek.

## Campagnebeheer {#campaign-management}

Deze reeks lijsten is verbonden met de **Marketing campagnes** module, die toestaat om mededelingen en marketing campagnes te bepalen, te optimaliseren, uit te voeren en te analyseren. Voor meer op dit, verwijs naar de [ documentatie van de Campagne v8 ](https://experienceleague.adobe.com/docs/campaign/campaign-v8/campaigns/campaigns.html){target=_blank}.

![](assets/data-model_campaign.png)

* **NmsOperation**: Deze lijst past het **nms:operation** schema aan. Het bevat de gegevens van marketingcampagnes.
* **NmsDeliveryOutline**: Deze lijst past het **nms:deliveryOutline** schema aan. Het bevat de uitgebreide eigenschappen van de levering (leveringsoverzicht).
* **NmsDlvOutlineItem**: Deze lijst past het **nms:dlvOutlineItem** schema aan. Het bevat de artikelen van een leveringsoverzicht.
* **NmsDeliveryCustomization**: Deze lijst past het **nms:deliveryCustomization** schema aan. Het bevat de verpersoonlijkingsgebieden van een levering.
* **NmsBudget**: Deze lijst past het **nms:budget** schema aan. Het bevat de gegevens van een begroting over een campagne, een plan, een programma, een taak en/of leveringen.
* **NmsDocument**: Deze lijst past het **nms:document** schema aan. Het bevat de marketingdocumenten van de campagne in de vorm van bestanden (afbeeldingen, excel- of woordbestanden, enz.)
* **XtkWorkflow**: Deze lijst past het **xtk:workflow** schema aan. Het bevat campagnedoel.
* **NmsTask**: Deze lijst past het **nms:task** schema aan. Het bevat de definitie van een marketingtaak.
* **NmsAsset**: Deze lijst past het **nms:asset** schema aan. Het bevat de definitie van een marketingmiddel.

## Communicatieconsistentie {#communication-consistency}

Deze reeks lijsten is verbonden met de **module van de Optimalisering van de Campagne**, die toestaat om het verzenden van leveringen te controleren, te filtreren en te controleren. Verwijs naar de [ documentatie van de Campagne v8 ](https://experienceleague.adobe.com/docs/campaign/automation/campaign-optimization/campaign-typologies.html){target="_blank"}.


![](assets/data-model_typology.png)

* **NmsTypologyRule**: Deze lijst past het **nms:typologyRule** schema aan. Het bevat de regels die van toepassing zijn op leveringen afhankelijk van typologieën.
* **NmsTypology**: Deze lijst past het **nms:typology** schema aan. Het bevat de regels die moeten worden toegepast op leveringen die overeenkomen met de typologie.
* **NmsTypologyRuleRel**: Deze lijst past het **nms:typologyRuleRel** schema aan. Het bevat de relaties tussen typologieën en hun regels.
* **NmsVolumeLine**: Deze lijst past het **nms:volumeLine** schema aan. Het bevat de reeks beschikbaarheidslijnen van de capaciteitsregels.
* **NmsVolumeConsumed**: Deze lijst past het **nms:volumeConsumed** schema aan. Het bevat alle verbruikslijnen van de capaciteitsregels.

## Responsbeheer {#response-management}

Deze reeks lijsten is verbonden met de **module van de Manager van de Reactie**, die toestaat om het succes en de rentabiliteit van marketing campagnes te meten of voorstellen voor alle communicatie kanalen aan te bieden. Voor meer op dit, zie [ Ongeveer reactiemanager ](../../response/using/about-response-manager.md).

![](assets/data-model_response.png)

### NmsRemaHypothesis {#NmsRemaHypothesis}

Deze lijst valt met het **nms:remaHypothesis** schema samen. Het bevat de definitie van de meethypothese.

Deze tabel bevat belangrijke informatie die is opgeslagen in XML, zoals:

**context van de Uitvoering (informatie die in XML wordt opgeslagen)**

De uitvoeringscontext vult de tabellen en velden die in aanmerking moeten worden genomen voor de meetberekening, namelijk:
* Het nms :remaMatchRcp opslagschema van het reactielogboek.
* Het schema van de transactietabel (aankopen bijvoorbeeld).
* Het vraagschema, dat u toelaat om de beginlijst van de hypothesevoorwaarden te bepalen.
* De verbindingen met individuen, die u toelaten om het individu te identificeren dat op het het vragen schema wordt gebaseerd.
* De transactiedatum. Dit veld is niet verplicht, maar u wordt aangeraden het te gebruiken om de omtrek van de berekening te beperken.
* Het transactiebedrag: het is een optioneel veld voor het automatisch berekenen van inkomstenindicatoren.

**de perimeter van de Hypothese (informatie die in XML wordt opgeslagen)**

De perimeter van de hypothese bestaat uit het filtreren van de hypothese die op de lijst van het het vragen schema wordt gebaseerd.

**Hypothesis overload manuscript (informatie die in XML wordt opgeslagen)**

Het hypotheseoverbelastingsscript is een JavaScript-code waarmee u de inhoud van de hypothese tijdens de uitvoering kunt overladen.

**indicatoren van de Meting**

De volgende indicatoren worden automatisch bijgewerkt tijdens de uitvoering van de hypothese:

* Aantal reacties: **iTransaction**. Aantal lijnen in de lijst van reactielogboeken.
* Aantal gecontacteerd: **iContactReactie**. Het aantal gerichte contacten in de hypothese.
* Aantal van de controlegroep: **iProofReactie**. Afzonderlijk aantal gerichte contacten tussen controlegroepen in de hypothese.
* Contacted reactietarief: **dContactReactieRate**. Responspercentage van de gerichte contacten in de hypothese.
* Het tarief van de reactie van de controlegroep: **dProofReactieRate**. Responspercentage van de hypothesecontrolegroep.
* Totale opbrengst van gecontacteerde bevolking: **dContactRehandeldeTotalAmount**. Totale inkomsten van de gerichte contacten in de hypothese.
* Gemiddelde opbrengst van controlegroep: **dContactRehandeldeAvgAmount**. Gemiddelde inkomsten van de doelgroep contacten in de hypothese.
* Totale opbrengst van de controlegroep: **dProofReactieTotalAmount**. Totale inkomsten van de groep hypothesecontrole.
* Gemiddelde opbrengst van controlegroep: **dProofRehandeldeAvgAmount**. Gemiddelde inkomsten van de hypothesecontrolegroep.
* Totale marge per contact: **dContactRehandeldeTotalMargin**. Totale marge per contact als bedoeld in de hypothese.
* Gemiddelde marge per contact: **dContactRehandeldeAvgMargin**. Gemiddelde marge per contact als bedoeld in de hypothese.
* Totale marge van controlegroep: **dProofRehandeldeTotalMargin**. Totale marge van de in de hypothese beoogde controlegroep.
* Gemiddelde marge van controlegroep: **dProofRehandeldeAvgMargin**. Gemiddelde marge van de in de hypothese beoogde controlegroep.
* Extra opbrengst: **dAdditionalAmount**. (Gemiddelde inkomsten van gecontacteerde onderneming - Gemiddelde inkomsten van de controlegroep) * Aantal gecontacteerde partijen.
* Extra marge: **dAdditionalMargin**. (Gemiddelde marge van gecontacteerde partij - Gemiddelde marge van controlegroep) / Aantal gecontacteerde personen.
* Gemiddelde kosten per contactpersoon (SQL-expressie). Berekende kosten van de levering / Aantal gecontacteerde personen.
* ROI (SQL-expressie). Berekende kosten van de levering/totale marge van gecontacteerd.
* Effectieve ROI (SQL-expressie). Berekende kosten van de levering / Aanvullende marge.
* Significantie: **Significativy** (SQL uitdrukking). Bevat waarden van 0 tot en met 3, afhankelijk van het belang van de campagne.

### NmsRemaMatchRcp {#NmsRemaMatchRcp}

Deze lijst past het **nms:remaMatchRcp** schema aan.

Het bevat een overzicht van de reactie van een individu op een bepaalde hypothese. Deze verslagen werden gecreeerd tijdens hypotheseuitvoering.

## Simulatie en levering {#simulation-and-delivery}

Deze reeks lijsten is verbonden met de **Simulatie** module, die toestaat om de distributie van aanbiedingen te testen die tot een categorie of een milieu behoren alvorens uw voorstel naar ontvangers te verzenden. Voor meer op dit, zie [ Ongeveer aanbiedingen simulatie ](../../interaction/using/about-offers-simulation.md).

![](assets/data-model_simulation.png)

* **NmsSimulation**: Deze lijst past het **nms:simulation** schema aan. Het is een simulatie voor een reeks leveringen of aanbiedingen voor een bepaalde populatie.
* **NmsDlvSimulationRel**: Deze lijst past het **nms:dlvSimulationRel** schema aan. Het bevat de lijst met leveringen waarmee in de simulatie rekening is gehouden. Het bereik van de simulatie wordt opgeslagen in XML.
* **NmsOfferSimulationRel**: Deze lijst past het **nms:offerSimulationRel** schema aan. Hiermee kunt u een simulatie koppelen aan een aanbieding.

## Interactiemodule {#interaction-module}

Deze reeks lijsten is verbonden aan de **module van de Interactie**, die toestaat om in echt te antwoorden - tijd tijdens een interactie met een bepaald contact door hen één of verscheidene aangepaste aanbiedingen te maken. Voor meer op dit, zie [ Interactie en bied beheer ](../../interaction/using/interaction-and-offer-management.md) aan.

* **NmsOffer**: Deze lijst past het **nms:offer** schema aan. Het bevat de definitie van elk marketingaanbod.
* **NmsPropositionRcp**: Deze lijst past het **nms:propositionRcp** schema aan. Het bevat het kanaallogboek van marketingvoorstellen die naar elk individu worden verzonden. De record wordt gemaakt wanneer een voorstel wordt voorbereid of daadwerkelijk aan een individu wordt gedaan.
* **NmsOfferSpace**: Deze lijst past het **nms:offerSpace** schema aan. Het bevat de definitie van locaties waarop voorstellen worden gedaan.
* **NmsOfferContext**: Deze lijst past het **nms:offerContext** schema aan. Het bevat aanvullende criteria betreffende de toepasselijkheid van het voorstel en de definitie van de formule voor de berekening van het gewicht.
* **NmsOfferView**: Deze lijst past **nms:offerView** aan. Het bevat de aanbiedingsvoorstellingen.
* **NmsOfferCategory**: Deze lijst past **nms:offerCategory** aan. Het bevat de aanbiedingrubrieken.
* **NmsOfferEnv**: Deze lijst past **nms:offerEnv** aan. Het bevat de aanbiedingsomgevingen.

## Module Berichtencentrum {#message-center-module}

De volgende reeks lijsten is verbonden met het **Transactionele overseinen** (Centrum van het Bericht) module, die toestaat om individuele en unieke die mededelingen te beheren aan een gebruiker worden verzonden en van gebeurtenissen worden geproduceerd die van informatiesystemen worden teweeggebracht. Voor meer op dit, zie [ Ongeveer transactioneel overseinen ](../../message-center/using/about-transactional-messaging.md).

### NmsRtEvent {#NmsRtEvent}

![](assets/data-model_message-center_rt.png)

Deze lijst past het **nms:rtEvent** schema aan. Het bevat een definitie van gebeurtenissen in real time.

### NmsBatchEvent {#NmsBatchEvent}

![](assets/data-model_message-center_batch.png)

Deze lijst past het **nms:batchEvent** schema aan. Het bevat de definitie van gebeurtenissen op batch.

<!--## Microsites Module {#microsites-module}

This set of tables is linked to the **Web applications** functionality, which allows to create and publish dynamic and interactive web applications with data from the database and content adapted to the rights of the connected user. For more on this, see [About web applications](../../web/using/about-web-applications.md).

![](assets/data-model_microsites.png)

* **NmsTrackingUrl**: This table matches the **nms:trackingUrl** schema.

* **NmsPurl**: This table matches the **nms:purl** schema.-->

## NMAC-module {#nmac-module}

Deze reeks lijsten is verbonden met het **Mobiele Kanaal van de App**, dat toestaat om gepersonaliseerde berichten naar de terminals van iOS en van Android via apps te verzenden. Voor meer op dit, zie [ Ongeveer mobiel app kanaal ](../../delivery/using/about-mobile-app-channel.md).

* **NmsMobileApp**: Deze lijst past het **nms:mobileApp** schema aan. Het bevat de mobiele toepassingen die in Adobe Campaign zijn gedefinieerd.
* **NmsAppSubscription**: Deze lijst past het **nms:appSubscription** schema aan. Het bevat de abonneeinformatie betreffende één of meerdere toepassingen.
* **NmsAppSubscriptionRcp**: Deze lijst past het **nms:appSubscriptionRcp** schema aan. Hiermee kunt u bezoekers die zijn geabonneerd op een toepassing, koppelen aan de tabel met ontvangers.
* **NmsExcludeLogAppSubRcp**: Deze lijst past het **nms:excludeLogAppSubRcp** schema aan.
* **NmsTrackingLogAppSubRcp**: Deze lijst past het **nms:trackingLogAppSubRcp** schema aan.
* **NmsBroadLogAppSubRcp**: Deze lijst past het **nms:broadLogAppSubRcp** schema aan.

## Module voor sociale marketing {#social-marketing-module}

Deze reeks lijsten is verbonden met **het Leiden sociale netwerken** module, die toestaat om met klanten en vooruitzichten via Facebook en X (vroeger gekend als Twitter) in wisselwerking te staan. Voor meer op dit, zie [ Ongeveer sociale marketing ](../../social/using/about-social-marketing.md).

![](assets/data-model_social.png)

* **NmsVisitor**: Deze lijst past het **nms:visitor** schema aan. Het bevat informatie over bezoekers.
* **NmsVisitorSub**: Deze lijst past het **nms:visitorSub** schema aan. Hiermee kunt u een bezoeker koppelen aan de services waarop ze zich hebben geabonneerd (X of Facebook).
* **NmsFriendShipRel**: Deze lijst past het **nms:friendshipRel** schema aan. Hiermee kunt u bezoekers koppelen aan hun vrienden in het kader van de Facebook-service.
* **NmsVisitorInterestRel**: Deze lijst past het **nms:visitorInterestRel** schema aan. Het stelt u in staat bezoekers en hun belangen met elkaar te verbinden.
* **NmsInterest**: Deze lijst past het **nms:interest** schema aan. Het bevat de lijst met belangen voor elke bezoeker.
