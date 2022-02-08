---
product: campaign
title: Beschrijving van Adobe Campaign Classic-gegevensmodel
description: In dit document wordt het Adobe Campaign-gegevensmodel beschreven
feature: Data Model
exl-id: fc0fd23c-f9ea-4e30-b47b-a84143d882ca
source-git-commit: 3997412f14666fa61bf71d0f0a0653f5cc042e19
workflow-type: tm+mt
source-wordcount: '2374'
ht-degree: 1%

---

# Beschrijving van gegevensmodel campagne{#data-model-description}

![](../../assets/v7-only.svg)

Adobe Campaign bevat een vooraf gedefinieerd datamodel. In deze sectie vindt u enkele details over de ingebouwde tabellen van het Adobe Campaign-gegevensmodel en de interactie ervan.

Ga naar **[!UICONTROL Admin > Configuration > Data schemas]** selecteert u een bron in de lijst en klikt u op de knop **[!UICONTROL Documentation]** tab.

![](assets/data-model_documentation-tab.png)

>[!NOTE]
>
>De fysieke en logische structuur van de data die in de applicatie worden overgedragen, wordt in XML beschreven. Het volgt een grammatica die specifiek is voor Adobe Campaign en een schema wordt genoemd. Lees voor meer informatie over Adobe Campaign-schema&#39;s [deze sectie](../../configuration/using/about-schema-reference.md).

## Beschrijving van de belangrijkste tabellen {#description-main-tables}

Adobe Campaign vertrouwt op een relationele database die tabellen bevat die aan elkaar zijn gekoppeld.

Het volgende diagram toont de verbindingen tussen de belangrijkste bedrijfslijsten van het de gegevensmodel van Adobe Campaign met de belangrijkste gebieden voor elk.

<!--![](assets/data-model_diagram.png)-->

![](assets/data-model_simplified-diagram.png)

Het vooraf gedefinieerde Adobe Campaign-gegevensmodel bevat de onderstaande hoofdtabellen.

### NmsRecipient {#NmsRecipient}

Deze tabel komt overeen met de **nms:ontvanger** schema.

Dit is de standaardtabel die wordt gebruikt voor de **ontvangers van leveringen**. Bijgevolg bevat het de informatie die nodig is voor leveringen via de verschillende kanalen:

* sEmail: e-mailadres.
* iEmailFormat: voorkeursindeling voor e-mails (1 voor tekst, 2 voor HTML en 0 als deze niet gedefinieerd zijn).
* sAddress1, sAddress2, sAddress3, sAddress4, sZipCode, sCity wordt gebruikt om het postadres te bouwen (in overeenstemming met de norm XPZ 10-011 AFNOR van Mei 1997).
* sPhone, sMobilePhone en sFax bevatten respectievelijk de telefoon-, mobiele telefoon- en faxnummers.
* iBlackList is de standaardmarkering voor niet-deelname die wordt gebruikt voor de profielen (1 betekent &quot;niet-geabonneerd&quot;, anders 0).

Het veld iFolderId is de externe sleutel die de ontvanger aan zijn uitvoeringsmap koppelt. Zie voor meer informatie [XtkFolder](#XtkFolder).

Het veld sCountryCode is de ISO-code 3166-1 Alpha 2 (2 tekens) van het land dat aan de ontvanger is gekoppeld. Dit veld is in feite een buitenlandse sleutel in de referentietabel van het land (NmsCountry), die de landlabels en andere landcodegegevens bevat. Als het land niet is gevuld, wordt de waarde &#39;XX&#39; opgeslagen (en wordt gebruikt in plaats van een nul-id-record).

Voor meer informatie over de tabel Ontvanger raadpleegt u [deze sectie](../../configuration/using/about-data-model.md#default-recipient-table).

### NmsGroup {#NmsGroup}

Deze tabel komt overeen met de **nms:groep** schema.

Hiermee kunt u **statistische groepen ontvangers**. Er is een veel-op-veel relatie tussen ontvangers en groepen. Eén ontvanger kan bijvoorbeeld tot meerdere groepen behoren en één groep kan meerdere ontvangers bevatten. Groepen kunnen handmatig worden gemaakt, via import of levering als doel. Groepen worden vaak gebruikt als leveringsdoelen. Er is een unieke index op het gebied die de interne naam van de sName groep vertegenwoordigt. De groep is gekoppeld aan een map (de sleutel is iFolderId. Zie voor meer informatie [XtkFolder](#XtkFolder)).

### NmsRcpGrpRel {#NmsRcpGrpRel}

De NmsRcpGrpRel-relatietabel bevat alleen de twee velden die overeenkomen met de id&#39;s van de gekoppelde tabellen iRecipientId en iGroupId.

### NmsService {#NmsService}

Deze tabel komt overeen met de **nms:service** schema.

In Adobe Campaign kunt u abonnementen op informatieservices (onderwerpen) maken en beheren. De lijst NmsService slaat de definitie van de informatiediensten (onderwerpen) op die u uw ontvangers aanbiedt om aan (een nieuwsbrief bijvoorbeeld) in te schrijven.

De diensten zijn entiteiten die aan groepen (statische ontvankelijke groeperingen) gelijkaardig zijn, behalve dat zij meer informatie verspreiden en gemakkelijke beheer van abonnementen en abonnementen via vormen toelaten.

Er is een unieke index op het gebied die de interne naam van de dienst sName vertegenwoordigt. De service is gekoppeld aan een map (de sleutel is iFolderId. Zie voor meer informatie [XtkFolder](#XtkFolder)). Tot slot specificeert het iType gebied het leveringskanaal van deze dienst (0 voor e-mail, 1 voor SMS, 2 voor telefoon, 3 voor directe post en 4 voor fax).

### NmsSubscription {#NmsSubscription}

Deze tabel komt overeen met de **nms:abonnement** schema.

Het laat u toe om ontvankelijke abonnementen aan informatiediensten te beheren.

### NmsSubHisto {#NmsSubHisto}

Deze tabel komt overeen met de **nms:subHisto** schema.

Als de abonnementen worden beheerd met behulp van webformulieren of de interface van de toepassing, worden alle abonnementen en aftekeningen in de tabel NmsSubHisto gehistoriseerd. In het veld iAction wordt de handeling (0 voor abonnement en 1 voor abonnement) opgegeven die wordt uitgevoerd op de datum die is opgeslagen in het veld tsDate.

### NmsDelivery {#NmsDelivery}

Deze tabel komt overeen met de **nms:levering** schema.

Elke record in deze tabel vertegenwoordigt een **actie voor levering** of **leveringssjabloon**. Het bevat alle parameters die nodig zijn voor het uitvoeren van leveringen (doel, inhoud, enz.). Logboeken voor levering (uitzending) (NmsBroadLog) en bijbehorende URL&#39;s voor tracering (NmsTrackingUrl) worden tijdens de analysefase gemaakt (zie hieronder voor meer informatie over beide tabellen).

Er is een unieke index op het gebied die de interne naam van de levering sInternalName of het scenario vertegenwoordigt. De levering is gekoppeld aan een uitvoeringsmap (de externe sleutel is iFolderProcessId. Zie voor meer informatie [XtkFolder](#XtkFolder)).

### XtkFolder {#XtkFolder}

Bevat **alle mappen in de structuur** zichtbaar in het **Navigatie** tabblad van de console.

De mappen worden getypt: De waarde van het veld sModel geeft het type gegevens aan dat in de map kan worden opgenomen. Met dit veld kan de clientconsole de gegevens ook correct weergeven met de bijbehorende formulieren. De mogelijke waarden voor dit veld worden gedefinieerd in de navTree.

De structuur wordt beheerd door de velden iParentId en iChildCount. Het veld sFullName geeft het volledige pad van de map in de structuur. Tot slot is er een unieke index op het gebied die de interne naam van de sName omslag vertegenwoordigt.

## Aflevering en tekstspatiëring {#delivery-and-tracking}

Deze set tabellen is gekoppeld aan de **Aflevering** -module, waarmee u leveringen en eventuele problemen kunt controleren die optreden wanneer berichten worden verzonden. Zie voor meer informatie [Bewaking van leveringen](../../delivery/using/about-delivery-monitoring.md). Zie voor meer informatie over bijhouden [Berichten bijhouden](../../delivery/using/about-message-tracking.md).

![](assets/data-model_delivery.png)

**NmsBroadLogMsg**: Deze tabel komt overeen met de **nms:wideLogMsg** schema. Het is een uitbreiding van de lijst van het leveringslogboek.

## Campagnebeheer {#campaign-management}

Deze set tabellen is gekoppeld aan de **Marketingscampagnes** -module, waarmee communicatie- en marketingcampagnes kunnen worden gedefinieerd, geoptimaliseerd, uitgevoerd en geanalyseerd. Zie voor meer informatie [Informatie over marketingcampagnes](../../campaign/using/designing-marketing-campaigns.md).

![](assets/data-model_campaign.png)

* **NmsOperation**: Deze tabel komt overeen met de **nms:bewerking** schema. Het bevat de gegevens van marketingcampagnes.
* **NmsDeliveryOutline**: Deze tabel komt overeen met de **nms:deliveryOutline** schema. Het bevat de uitgebreide eigenschappen van de levering (leveringsoverzicht).
* **NmsDlvOutlineItem**: Deze tabel komt overeen met de **nms:dlvOutlineItem** schema. Het bevat de artikelen van een leveringsoverzicht.
* **NmsDeliveryCustomization**: Deze tabel komt overeen met de **nms:deliveryCustomization** schema. Het bevat de verpersoonlijkingsgebieden van een levering.
* **NmsBudget**: Deze tabel komt overeen met de **nms:budget** schema. Het bevat de gegevens van een begroting over een campagne, een plan, een programma, een taak en/of leveringen.
* **NmsDocument**: Deze tabel komt overeen met de **nms:document** schema. Het bevat de marketingdocumenten van de campagne in de vorm van bestanden (afbeeldingen, excel- of woordbestanden, enz.)
* **XtkWorkflow**: Deze tabel komt overeen met de **xtk:workflow** schema. Het bevat campagnedoel.
* **NmsTask**: Deze tabel komt overeen met de **nms:taak** schema. Het bevat de definitie van een marketingtaak.
* **NmsAsset**: Deze tabel komt overeen met de **nms:element** schema. Het bevat de definitie van een marketingmiddel.

## Communicatieconsistentie {#communication-consistency}

Deze set tabellen is gekoppeld aan de **Campagne optimaliseren** -module, waarmee de verzending van leveringen kan worden gecontroleerd, gefilterd en gecontroleerd. Zie voor meer informatie [Informatie over campagetypologieën](../../campaign-opt/using/about-campaign-typologies.md).

![](assets/data-model_typology.png)

* **NmsTypologyRule**: Deze tabel komt overeen met de **nms:typologyRule** schema. Het bevat de regels die van toepassing zijn op leveringen afhankelijk van typologieën.
* **NmsTypology**: Deze tabel komt overeen met de **nms:typologie** schema. Het bevat de regels die moeten worden toegepast op leveringen die overeenkomen met de typologie.
* **NmsTypologyRuleRel**: Deze tabel komt overeen met de **nms:typologyRuleRel** schema. Het bevat de relaties tussen typologieën en hun regels.
* **NmsVolumeLine**: Deze tabel komt overeen met de **nms:volumeLine** schema. Het bevat de reeks beschikbaarheidslijnen van de capaciteitsregels.
* **NmsVolumeConsumed**: Deze tabel komt overeen met de **nms:volumeConsumed** schema. Het bevat alle verbruikslijnen van de capaciteitsregels.

## Responsbeheer {#response-management}

Deze set tabellen is gekoppeld aan de **Responsbeheer** -module, waarmee het succes en de winstgevendheid van marketingcampagnes kan worden gemeten of voorstellen voor alle communicatiekanalen kunnen worden gedaan. Zie voor meer informatie [Over responsbeheer](../../response/using/about-response-manager.md).

![](assets/data-model_response.png)

### NmsRemaHypothesis {#NmsRemaHypothesis}

Deze tabel valt samen met de **nms:remaHypothesis** schema. Het bevat de definitie van de meethypothese.

Deze tabel bevat belangrijke informatie die is opgeslagen in XML, zoals:

**Uitvoercontext (informatie opgeslagen in XML)**

De uitvoeringscontext vult de tabellen en velden die in aanmerking moeten worden genomen voor de meetberekening, namelijk:
* Het opslagschema van het nms:remaMatchRcp-reactielogbestand.
* Het schema van de transactietabel (aankopen bijvoorbeeld).
* Het vraagschema, dat u toelaat om de beginlijst van de hypothesevoorwaarden te bepalen.
* De verbindingen met individuen, die u toelaten om het individu te identificeren dat op het het vragen schema wordt gebaseerd.
* De transactiedatum. Dit veld is niet verplicht, maar u wordt aangeraden het te gebruiken om de omtrek van de berekening te beperken.
* Het transactiebedrag: het is een facultatief veld voor de automatische berekening van inkomstenindicatoren .

**Hypothese-omtrek (informatie opgeslagen in XML)**

De perimeter van de hypothese bestaat uit het filtreren van de hypothese die op de lijst van het het vragen schema wordt gebaseerd.

**Hypothesis overload-script (informatie opgeslagen in XML)**

Het hypotheseoverbelastingsscript is een JavaScript-code waarmee u de inhoud van de hypothese tijdens de uitvoering kunt overladen.

**Meetindicatoren**

De volgende indicatoren worden automatisch bijgewerkt tijdens de uitvoering van de hypothese:

* Aantal reacties: **iTransaction**. Aantal lijnen in de lijst van reactielogboeken.
* Aantal gecontacteerde personen: **iContactRehandelde**. Afzonderlijk aantal gerichte contacten in de hypothese.
* Aantal controlegroepen: **iProofReactie**. Afzonderlijk aantal gerichte contacten tussen controlegroepen in de hypothese.
* Behandelde responspercentage: **dContactRehandelingsnelheid**. Responspercentage van de gerichte contacten in de hypothese.
* Responspercentage van de controlegroep: **dProofRehandelingsnelheid**. Responspercentage van de hypothesecontrolegroep.
* Totale gecontacteerde inkomsten van de bevolking: **dContactRehandeldeTotalAmount**. Totale inkomsten van de gerichte contacten in de hypothese.
* Gemiddelde inkomsten van de controlegroep: **dContactRehandeldeAvgAmount**. Gemiddelde inkomsten van de doelgroep contacten in de hypothese.
* Totale ontvangsten van de controlegroep: **dProofReactieTotalAmount**. Totale inkomsten van de groep hypothesecontrole.
* Gemiddelde inkomsten van de controlegroep: **dProofReactieAvgAmount**. Gemiddelde inkomsten van de hypothesecontrolegroep.
* Totale marge per contactpersoon: **dContactRehandeldeTotalMargin**. Totale marge per contact als bedoeld in de hypothese.
* Gemiddelde marge per contact: **dContactRehandeldeAvgMargin**. Gemiddelde marge per contact als bedoeld in de hypothese.
* Totale marge van de controlegroep: **dProofRehandeldeTotalMargin**. Totale marge van de in de hypothese beoogde controlegroep.
* Gemiddelde marge van de controlegroep: **dProofReactieAvgMargin**. Gemiddelde marge van de in de hypothese beoogde controlegroep.
* Aanvullende inkomsten: **dAdditionnalAmount**. (Gemiddelde inkomsten van gecontacteerde onderneming - Gemiddelde inkomsten van de controlegroep) * Aantal gecontacteerde partijen.
* Aanvullende marge: **dAdditionalMargin**. (Gemiddelde marge van gecontacteerde partij - Gemiddelde marge van controlegroep) / Aantal gecontacteerde personen.
* Gemiddelde kosten per contactpersoon (SQL-expressie). Berekende kosten van de levering / Aantal gecontacteerde personen.
* ROI (SQL-expressie). Berekende kosten van de levering/totale marge van gecontacteerd.
* Effectieve ROI (SQL-expressie). Berekende kosten van de levering / Aanvullende marge.
* Significantie: **Significativy** (SQL-expressie). Bevat waarden van 0 tot en met 3, afhankelijk van het belang van de campagne.

### NmsRemaMatchRcp {#NmsRemaMatchRcp}

Deze tabel komt overeen met de **nms:remaMatchRcp** schema.

Het bevat een overzicht van de reactie van een individu op een bepaalde hypothese. Deze verslagen werden gecreeerd tijdens hypotheseuitvoering.

## Simulatie en levering {#simulation-and-delivery}

Deze set tabellen is gekoppeld aan de **Simulatie** , waarmee u de distributie van aanbiedingen die tot een categorie of omgeving behoren, kunt testen voordat u uw voorstel naar ontvangers verzendt. Zie voor meer informatie [Informatie over simulatie van aanbiedingen](../../interaction/using/about-offers-simulation.md).

![](assets/data-model_simulation.png)

* **NmsSimulation**: Deze tabel komt overeen met de **nms:simulatie** schema. Het is een simulatie voor een reeks leveringen of aanbiedingen voor een bepaalde populatie.
* **NmsDlvSimulationRel**: Deze tabel komt overeen met de **nms:dlvSimulationRel** schema. Het bevat de lijst met leveringen waarmee in de simulatie rekening is gehouden. Het bereik van de simulatie wordt opgeslagen in XML.
* **NmsOfferSimulationRel**: Deze tabel komt overeen met de **nms:aanbiedingSimulationRel** schema. Hiermee kunt u een simulatie koppelen aan een aanbieding.

## Interactiemodule {#interaction-module}

Deze set tabellen is gekoppeld aan de **Interactie** -module, die het mogelijk maakt in real time te reageren tijdens een interactie met een bepaald contact door er één of meerdere aangepaste aanbiedingen van te maken. Zie voor meer informatie [Interactie- en aanbiedingsbeheer](../../interaction/using/interaction-and-offer-management.md).

* **NmsOffer**: Deze tabel komt overeen met de **nms:aanbieding** schema. Het bevat de definitie van elk marketingaanbod.
* **NmsPropositionRcp**: Deze tabel komt overeen met de **nms:propositionRcp** schema. Het bevat het kanaallogboek van marketingvoorstellen die naar elk individu worden verzonden. De record wordt gemaakt wanneer een voorstel wordt voorbereid of daadwerkelijk aan een individu wordt gedaan.
* **NmsOfferSpace**: Deze tabel komt overeen met de **nms:offerSpace** schema. Het bevat de definitie van locaties waarop voorstellen worden gedaan.
* **NmsOfferContext**: Deze tabel komt overeen met de **nms:aanbiedingContext** schema. Het bevat aanvullende criteria betreffende de toepasselijkheid van het voorstel en de definitie van de formule voor gewichtsberekening.
* **NmsOfferView**: Deze tabel komt overeen met de **nms:offerView**. Het bevat de aanbiedingsverklaringen.
* **NmsOfferCategory**: Deze tabel komt overeen met de **nms:aanbiedingenCategorie**. Het bevat de aanbiedingrubrieken.
* **NmsOfferEnv**: Deze tabel komt overeen met de **nms:aanbiedingEnv**. Het bevat de aanbiedingsomgevingen.

## Module Berichtencentrum {#message-center-module}

De volgende set tabellen is gekoppeld aan de **Transactieberichten** (Berichtencentrum) module, die toestaat om individuele en unieke die mededelingen te beheren aan een gebruiker worden verzonden en van gebeurtenissen worden geproduceerd die van informatiesystemen worden teweeggebracht. Zie voor meer informatie [Informatie over transactieberichten](../../message-center/using/about-transactional-messaging.md).

### NmsRtEvent {#NmsRtEvent}

![](assets/data-model_message-center_rt.png)

Deze tabel komt overeen met de **nms:rtEvent** schema. Het bevat een definitie van gebeurtenissen in real time.

### NmsBatchEvent {#NmsBatchEvent}

![](assets/data-model_message-center_batch.png)

Deze tabel komt overeen met de **nms:batchEvent** schema. Het bevat de definitie van gebeurtenissen op batch.

<!--## Microsites Module {#microsites-module}

This set of tables is linked to the **Web applications** functionality, which allows to create and publish dynamic and interactive web applications with data from the database and content adapted to the rights of the connected user. For more on this, see [About web applications](../../web/using/about-web-applications.md).

![](assets/data-model_microsites.png)

* **NmsTrackingUrl**: This table matches the **nms:trackingUrl** schema.

* **NmsPurl**: This table matches the **nms:purl** schema.-->

## NMAC-module {#nmac-module}

Deze set tabellen is gekoppeld aan de **Mobiel App-kanaal**, waarmee gepersonaliseerde meldingen kunnen worden verzonden naar iOS- en Android-terminals via apps. Zie voor meer informatie [Mobiel toepassingskanaal](../../delivery/using/about-mobile-app-channel.md).

* **NmsMobileApp**: Deze tabel komt overeen met de **nms:mobileApp** schema. Het bevat de mobiele toepassingen die in Adobe Campaign zijn gedefinieerd.
* **NmsAppSubscription**: Deze tabel komt overeen met de **nms:appSubscription** schema. Het bevat de abonneeinformatie betreffende één of meerdere toepassingen.
* **NmsAppSubscriptionRcp**: Deze tabel komt overeen met de **nms:appSubscriptionRcp** schema. Hiermee kunt u bezoekers die zijn geabonneerd op een toepassing, koppelen aan de tabel met ontvangers.
* **NmsExcludeLogAppSubRcp**: Deze tabel komt overeen met de **nms:excludeLogAppSubRcp** schema.
* **NmsTrackingLogAppSubRcp**: Deze tabel komt overeen met de **nms:trackingLogAppSubRcp** schema.
* **NmsBroadLogAppSubRcp**: Deze tabel komt overeen met de **nms:wideLogAppSubRcp** schema.

## Module voor sociale marketing {#social-marketing-module}

Deze set tabellen is gekoppeld aan de **Sociale netwerken beheren** -module, waarmee u via Facebook en Twitter met klanten en vooruitzichten kunt communiceren. Zie voor meer informatie [Sociale marketing](../../social/using/about-social-marketing.md).

![](assets/data-model_social.png)

* **NmsVisitor**: Deze tabel komt overeen met de **nms:bezoeker** schema. Het bevat informatie over bezoekers.
* **NmsVisitorSub**: Deze tabel komt overeen met de **nms:bezoekerSub** schema. Hiermee kunt u een bezoeker koppelen aan de services waarop ze zich hebben geabonneerd (Twitter of Facebook).
* **NmsFriendShipRel**: Deze tabel komt overeen met de **nms:vriendshipRel** schema. Met deze service kunt u bezoekers in het kader van de Facebook-service koppelen aan hun vrienden.
* **NmsVisitorInterestRel**: Deze tabel komt overeen met de **nms:bezoekerInterestRel** schema. U kunt bezoekers en hun belangen met elkaar verbinden.
* **NmsInterest**: Deze tabel komt overeen met de **nms:interesse** schema. Het bevat de lijst met belangen voor elke bezoeker.
