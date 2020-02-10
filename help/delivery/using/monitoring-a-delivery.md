---
title: Toezicht op levering
seo-title: Toezicht op levering
description: Toezicht op levering
seo-description: null
page-status-flag: never-activated
uuid: 7cb409eb-a01c-4b4d-bb62-760e0bafdc8a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
discoiquuid: 3aab3d47-76fd-4c68-add4-9c14240c936e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: f7655cd93a7dc8ecd35cd379da350ad279cae725

---


# Toezicht op levering{#monitoring-a-delivery}

Het **leveringsdashboard** is essentieel om uw leveringen en eventuele problemen te controleren die tijdens het verzenden van berichten worden ondervonden.

**Verwante onderwerpen**

* [Leveringsfouten begrijpen](../../delivery/using/understanding-delivery-failures.md)
* [Werken met quarantainebeheer](../../delivery/using/understanding-quarantine-management.md)
* [Best practices voor levering](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliveryBestPractices.html)
* [Aan de slag: Te leveren items beheren](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliverability.html)

## Delivery dashboard {#delivery-dashboard}

Als u de informatie over een levering wilt weergeven, bewerkt u deze, bekijkt u het dashboard en klikt u op de beschikbare tabbladen.

De tabinhoud kan niet meer worden gewijzigd nadat de levering is verzonden.

![](assets/s_ncs_user_del_details.png)

### Overzicht van levering {#delivery-summary}

Het **[!UICONTROL Summary]** tabblad bevat de kenmerken van de levering: leveringsstatus, gebruikt kanaal, informatie over de afzender, onderwerp, informatie over uitvoering. Raadpleeg voor meer informatie het [aantal verzonden](#number-of-messages-sent)berichten.

Met de **[!UICONTROL reports]** koppeling kunt u een set rapporten bekijken over de leveringsactie: algemeen leveringsrapport, gedetailleerd rapport, leveringsrapport, verspreiding van mislukte berichten, openingsfrequentie, klikken en transacties, enz. De inhoud van dit lusje kan volgens uw vereisten worden gevormd. Zie [deze sectie](../../reporting/using/delivery-reports.md)voor meer informatie.

### Leveringslogboeken en geschiedenis {#delivery-logs-and-history}

Op het **[!UICONTROL Delivery]** tabblad vindt u een overzicht van de gebeurtenissen in deze levering. Het bevat de leveringslogboeken, d.w.z. de lijst van verzonden berichten en hun status en de bijbehorende berichten.

Voor een levering kunt u (bijvoorbeeld) alleen ontvangers met een mislukte levering of een adres in quarantaine weergeven. Klik hiertoe op de **[!UICONTROL Filters]** knop en selecteer **[!UICONTROL By state]**. Selecteer vervolgens het frame in de vervolgkeuzelijst.

![](assets/s_ncs_user_delivery_delivery_tab.png)

Verschillende statussen worden weergegeven op [deze pagina](#delivery-statuses).

>[!NOTE]
>
>Met de **[!UICONTROL Display the mirror page for this message...]** koppeling kunt u de spiegelpagina weergeven voor de inhoud van de levering die in de lijst is geselecteerd, in een nieuw venster. De spiegelpagina is alleen beschikbaar voor leveringen waarvoor HTML-inhoud is gedefinieerd. Raadpleeg [De spiegelpagina](../../delivery/using/sending-messages.md#generating-the-mirror-page)genereren voor meer informatie.

### Logboeken bijhouden {#tracking-logs}

Op het **[!UICONTROL Tracking]** tabblad vindt u de volggeschiedenis voor deze levering. Op dit tabblad vindt u de volggegevens van de verzonden berichten, dus alle URL&#39;s die door Adobe Campaign moeten worden gevolgd. De volgende gegevens worden per uur bijgewerkt.

>[!NOTE]
>
>Als &#39;tracking&#39; niet is ingeschakeld voor levering, wordt dit tabblad niet weergegeven.

De volgende configuratie wordt uitgevoerd in het aangewezen stadium in de leveringstovenaar. Zie [Hoe te om gevolgde verbindingen](../../delivery/using/how-to-configure-tracked-links.md)te vormen.

**[!UICONTROL Tracking]** gegevens worden geïnterpreteerd in de leveringsrapporten. Zie [deze sectie](../../reporting/using/delivery-reports.md).

![](assets/s_ncs_user_delivery_tracking_tab.png)

### Afleveringscontrole {#delivery-audit-}

Het **[!UICONTROL Audit]** tabblad bevat het leveringslogboek en alle berichten met betrekking tot de proefdrukken. Met de **[!UICONTROL Refresh]** knop kunt u de gegevens bijwerken. Gebruik de **[!UICONTROL Filters]** knop om een filter op de gegevens te definiëren.

Met speciale pictogrammen kunt u fouten of waarschuwingen herkennen. Zie De levering [analyseren](../../delivery/using/steps-validating-the-delivery.md#analyzing-the-delivery).

Op het **[!UICONTROL Proofs]** subtabblad kunt u de lijst met proefdrukken weergeven die zijn verzonden.

![](assets/s_ncs_user_delivery_log_tab.png)

U kunt de informatie wijzigen die in dit venster (en die van de **[!UICONTROL Delivery]** **[!UICONTROL Tracking]** tabbladen) wordt weergegeven door de kolommen te selecteren die moeten worden weergegeven. Klik hiertoe op het **[!UICONTROL Configure list]** pictogram in de rechterbenedenhoek. Raadpleeg [deze sectie](../../platform/using/adobe-campaign-workspace.md#configuring-lists)voor meer informatie over het configureren van de lijstweergave.

### Synchronisatie van het dashboard voor levering {#delivery-dashboard-synchronization}

Van uw leveringsdashboard, wilt u de verwerkte berichten en leveringslogboeken controleren om ervoor te zorgen dat uw levering met succes werd verzonden.

Sommige indicatoren of status kunnen onjuist of niet bijgewerkt zijn, dit kan met de volgende oplossingen worden opgelost:

* Als uw leveringsstatus onjuist is, controleer dat alle noodzakelijke goedkeuringen voor deze levering zijn gedaan of de **[!UICONTROL operationMgt]** en **[!UICONTROL deliveryMgt]** werkschema&#39;s zonder fouten lopen. Dit kan ook zijn toe te schrijven aan de levering gebruikend een affiniteit die niet op de verzendende instantie wordt gevormd.
* Als uw leveringsindicatoren nog bij nul zijn en als u op een midsourcingconfiguratie bent, controleer het **[!UICONTROL Mid-sourcing (delivery counters)]** technische werkschema. Start het als de status niet is ingesteld **[!UICONTROL Started]**. Vervolgens kunt u proberen de indicatoren opnieuw te berekenen door met de rechtermuisknop op de relevante levering in de Adobe Campagneverkenner te klikken en **[!UICONTROL Actions]** > **[!UICONTROL Recompute delivery and tracking indicators]** te selecteren. Raadpleeg deze [sectie](../../reporting/using/reports-on-deliveries.md#tracking-indicators)voor meer informatie over trackingindicatoren.
* Als uw leveringsteller niet overeenkomt met uw levering, probeert u de indicatoren opnieuw te berekenen door met de rechtermuisknop op de desbetreffende levering te klikken in de Adobe Campagneverkenner en **[!UICONTROL Actions]** > te selecteren **[!UICONTROL Recompute delivery and tracking indicators]** om opnieuw te synchroniseren. Raadpleeg deze [sectie](../../reporting/using/reports-on-deliveries.md#tracking-indicators)voor meer informatie over trackingindicatoren.
* Als uw leveringsteller niet bijgewerkt is voor midsourcingimplementaties, controleert u of de **[!UICONTROL Mid-Sourcing (Delivery counters)]** technische workflow actief is. Raadpleeg deze [pagina](../../installation/using/mid-sourcing-deployment.md)voor meer informatie.

U kunt uw leveringen ook bijhouden met verschillende rapporten via het leveringsdashboard. Zie deze [sectie](../../reporting/using/reports-on-deliveries.md#accessing-existing-reports)voor meer informatie.

## Prestatieproblemen {#performance-issues}

### Checklist {#checklist-}

Als de leveringsprestaties slecht zijn, kunt u controleren:

* **De omvang van de levering**: Het voltooien van grote leveringen kan langer duren. De kinderen MTA worden gevormd om een standaardpartijgrootte te behandelen, die voor de meeste instanties werkt, maar moet worden gecontroleerd wanneer de leveringen constant langzaam zijn.
* **Het doel van de levering**: Het verbod op leveringsprestaties wordt beïnvloed door zachte stuiterfouten, die worden afgehandeld volgens de configuratie voor opnieuw proberen. Hoe groter het aantal fouten, hoe meer pogingen nodig zijn.
* **De totale platformbelasting**: Wanneer meerdere grote leveringen worden verzonden, kan dit gevolgen hebben voor het hele platform. U kunt IP reputatie en leveringsproblemen ook controleren. Raadpleeg voor meer informatie de handleiding [over de beste praktijken bij de](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliverability.html) uitvoering van Adobe Campagne en [deze pagina](../../delivery/using/about-deliverability.md).

Het onderhoud van platforms en databases kan ook van invloed zijn op de verzendprestaties van de levering. Raadpleeg [deze pagina](../../production/using/database-performances.md)voor meer informatie.

### Trage leveringen {#slow-deliveries}

Nadat je op de **[!UICONTROL Send]** button hebt geklikt, lijkt het langer te duren voordat je levering is uitgevoerd. Dit kan worden veroorzaakt door verschillende elementen:

* Sommige e-mailproviders hebben uw IP-adressen mogelijk op de zwarte lijst gezet. In dit geval, controleer uw uitzendingen en raadpleeg [dit begonnen](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliverability.html) worden.
* Uw levering is mogelijk te groot om snel te worden verwerkt, dit kan gebeuren met een hoge mate van personalisatie in JavaScript of als uw levering meer dan 60 kbytes weegt. Raadpleeg de best practices [van Adobe Campagne](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliveryBestPractices.html) Delivery voor meer informatie over de richtlijnen voor inhoud.
* Throttling zou binnen de Campagne MTA van Adobe kunnen voorgekomen zijn. Dit wordt veroorzaakt door:

   * Berichten gepend (**[!UICONTROL quotas met]** bericht): er is voldaan aan de quota die zijn aangegeven in de declaratieve MX-regels die in de campagne zijn vastgesteld. Raadpleeg [deze pagina](../../delivery/using/technical-recommendations.md#quota-met)voor meer informatie over dit bericht. Raadpleeg [deze pagina](../../delivery/using/technical-recommendations.md#mx-rules)voor meer informatie over MX-regels.
   * Berichten gepend (**[!UICONTROL dynamic flow control]** bericht): Campagne MTA heeft fouten ontmoet toen het proberen om berichten voor bepaalde ISP te leveren die een vertraging veroorzaakt om te grote van een foutendichtheid te vermijden en zo het onder ogen zien van potentiële zwarte lijst.

* Door een systeemprobleem kunnen servers niet met elkaar communiceren: dit kan het hele verzendingsproces vertragen . Controleer de servers om ervoor te zorgen dat er geen geheugen of middelkwesties zijn die Campagne in het proces kunnen beïnvloeden om de verpersoonlijkingsgegevens bijvoorbeeld te krijgen.

### Aanbevolen werkwijzen voor prestaties {#best-practices-performance}

* Bewaar de levering niet in mislukte staat op het geval, aangezien dit tijdelijke lijsten handhaaft en de prestaties beïnvloedt.

* Leveringen verwijderen die niet meer nodig zijn.

* Inactieve ontvangers in de laatste 12 maanden die uit het gegevensbestand moeten worden verwijderd om adreskwaliteit te handhaven.

* Probeer geen grote leveringen samen te plannen. Er is een tussenruimte van 5-10 minuten om de belasting gelijkmatig over het systeem te spreiden. Coördineer het plannen van leveringen met de andere leden van uw team om de beste prestaties te verzekeren. Wanneer de marketingserver meerdere taken tegelijk uitvoert, kan dit de prestaties vertragen.

* Houd je e-mailadres zo klein mogelijk. De aanbevolen maximale grootte van een e-mailbericht is ongeveer 35 kB. De grootte van een e-maillevering genereert een bepaalde hoeveelheid volume in de verzendende servers.

* De grote leveringen, zoals leveringen aan meer dan één miljoen ontvangers, hebben ruimte in de verzendende rijen nodig. Dit is op zich geen probleem voor de server, maar in combinatie met tientallen andere grote leveringen die allemaal tegelijk worden uitgevoerd, kan er een vertraging bij het verzenden ontstaan.

* Personalisatie in e-mailberichten haalt gegevens uit de database voor elke ontvanger. Als er vele verpersoonlijkingselementen zijn, verhoogt dat de hoeveelheid gegevens nodig om de levering voor te bereiden.

* Indexadressen. Om de prestaties van de SQL vragen te optimaliseren die in de toepassing worden gebruikt, kan een index van het belangrijkste element van het gegevensschema worden verklaard.

>[!NOTE]
>
>ISPs zou adressen na een periode van inactiviteit deactiveren. De berichten van de vlag worden verzonden naar afzenders om hen over deze nieuwe status te informeren.

## Leveringsstatus {#delivery-statuses}

Tijdens het verzenden van een levering krijgt u mogelijk de volgende status op het dashboard voor levering:

<table> 
 <thead> 
  <tr> 
   <th> Status<br /> </th> 
   <th> Definities en oplossingen<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Niet van toepassing<br /> </td> 
   <td> De levering werd in aanmerking genomen door de server (MTA) maar niet verwerkt.<br /> </td> 
  </tr> 
  <tr> 
   <td> Genegeerd<br /> </td> 
   <td> De levering is niet naar de ontvanger verzonden vanwege een fout met zijn adres. Het was op de zwarte lijst geplaatst, in quarantaine geplaatst, niet geleverd of een duplicaat. <br /> </td> 
  </tr> 
  <tr> 
   <td> Verzonden<br /> </td> 
   <td> De levering werd correct verzonden naar de berichtenleverancier (maar de ontvanger ontving het niet noodzakelijk).<br /> </td> 
  </tr> 
  <tr> 
   <td> Mislukt<br /> </td> 
   <td> De levering kan de ontvanger bijvoorbeeld niet bereiken vanwege een ongeldig adres of een volledig postvak. Het kan ook met een kwestie met verpersoonlijkingsblokken worden verbonden aangezien zij fouten kunnen produceren wanneer de schema's niet de leveringsafbeelding aanpassen. Zie <a href="#failed-status" target="_blank">Mislukte status</a><br /> </td> 
  </tr> 
  <tr> 
   <td> Door de dienstverlener in aanmerking genomen<br /> </td> 
   <td> De SMS-serviceprovider heeft de levering ontvangen.<br /> </td> 
  </tr> 
  <tr> 
   <td> Ontvangen op mobiel<br /> </td> 
   <td> De ontvanger heeft het SMS op zijn mobiele apparaat ontvangen.<br /> </td> 
  </tr> 
  <tr> 
   <td> In behandeling<br /> </td> 
   <td> De levering is klaar om te worden verzonden en zal door de leveringsserver (MTA) worden verwerkt. Zie Status <a href="#pending-status" target="_blank">in</a>behandeling.<br /> </td> 
  </tr> 
  <tr> 
   <td> Aflevering geannuleerd<br /> </td> 
   <td> De levering is geannuleerd door een operator.<br /> </td> 
  </tr> 
  <tr> 
   <td> Voorbereid<br /> </td> 
   <td> De intermediaire status die slechts voor externe schakelaars zoals het mobiele kanaal wordt gebruikt. Het volgt de status "In afwachting"en is de externe schakelaar die de volgende status zal bepalen.<br /> </td> 
  </tr> 
  <tr> 
   <td> Verzonden naar de serviceprovider<br /> </td> 
   <td> De levering werd verzonden naar de dienstverlener van SMS maar nog niet ontvangen.<br /> </td> 
  </tr> 
 </tbody> 
</table>

Raadpleeg de handleiding [over de beste praktijken bij de](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliverability.html) levering van Adobe Campagne en naar [deze pagina](../../delivery/using/about-deliverability.md)voor informatie over het optimaliseren van de leverbaarheid van e-mails voor uw Adobe Campagne.

### Status in behandeling {#pending-status}

Nadat u de levering hebt bevestigd, ziet u dat de status van de levering **[!UICONTROL Pending]** is. Deze status houdt in dat het uitvoeringsproces wacht op de beschikbaarheid van bepaalde bronnen.

De **[!UICONTROL Pending]** status kan eerst betekenen dat de levering gepland is en in behandeling is tot de opgegeven datum. Raadpleeg voor meer informatie de sectie [Leveringsplanning](../../delivery/using/steps-sending-the-delivery.md#scheduling-the-delivery-sending) .

Als de levering niet wordt verzonden en de status van de levering blijft behouden, kan dit het gevolg zijn van: **[!UICONTROL Pending]**

* MTA (de Agent van de Transfert van het Bericht), die modules en processen op de leveringsserver in werking stelt en die e-mail het verzenden beheert, kan niet zijn begonnen, of moet opnieuw worden begonnen. Voer de volgende stappen uit om dit te controleren en de module indien nodig te starten:

   * Controleer of uw `mta@<instance>` modules op uw servers MTA worden gelanceerd.

   ```
   nlserver pdump
   HH:MM:SS > Application server for Adobe Campaign Classic (X.Y.Z YY.R build nnnn@SHA1) of DD/MM/YYYY
   [...]
   mta@<INSTANCENAME> (9268) - 23.0 Mb
   [...]
   ```

   * Als MTA niet vermeld is, begin het met het volgende bevel:

   ```
   nlserver start mta@<INSTANCENAME>
   ```

   >[!NOTE]
   >
   >Vervangen `<INSTANCENAME>` door de naam van uw instantie (productie, ontwikkeling, enz.). De instantienaam wordt geïdentificeerd via de configuratiebestanden: `[path of application]nl6/conf/config-<INSTANCENAME>.xml`

* De levering kan een affiniteit gebruiken die niet op de verzendende server wordt gevormd. In dit geval, controleer de configuratie van het verkeersbeheer (IP affiniteit) en gebruik het **[!UICONTROL Managing affinities with IP addresses]** gebied om leveringen aan MTA te verbinden die de affiniteit beheert. Zie [deze rubriek](../../installation/using/configuring-campaign-server.md#personalizing-delivery-parameters)voor meer informatie over affiniteiten.
* Wanneer de voorbereiding van de levering in behandeling is, kunnen er te veel campagnes lopen, die de statusupdate van de levering blokkeerden. Om dit op te lossen, ga naar **[!UICONTROL Options]** en verhoog de waarde van **[!UICONTROL NmsOperation_LimitConcurrency]** (gebrek is 10). Voer niet meer campagnes uit dan de waarde die aan deze specifieke optie is toegewezen.

### Mislukte status {#failed-status}

Als de status van een e-maillevering is **[!UICONTROL Failed]**, kan deze worden gekoppeld aan een uitgave met verpersoonlijkingsblokken. De blokken van de verpersoonlijking in een levering kunnen fouten produceren wanneer de schema&#39;s niet de leveringsafbeelding aanpassen, bijvoorbeeld.

De logboeken van de levering zijn zeer belangrijk om te leren waarom een levering ontbrak. Hier zijn mogelijke fouten die u van leveringslogboeken kunt ontdekken:

* Als de ontvankelijke berichten met een &quot;Onbereikbare&quot;fout die ontbreken verklaart: Fout bij **compileren van script &#39;content htmlContent&#39; regel X: is`[table]`niet gedefinieerd. JavaScript: fout terwijl het evalueren van manuscript &#39;content htmlContent**, is de oorzaak van deze kwestie bijna altijd een verpersoonlijking binnen HTML die op een lijst of een gebied probeert te roepen dat niet is bepaald of in kaart gebracht in het stroomopwaartse richten of in de het doelafbeelding van de levering.

   Om dit te verbeteren, moeten de werkschema en leveringsinhoud worden herzien om specifiek te bepalen welke verpersoonlijking probeert om de lijst in kwestie te roepen en of de lijst of niet kan worden in kaart gebracht. Van daar, of het verwijderen van de vraag aan deze lijst in HTML of het bevestigen van de afbeelding aan de levering zou de weg aan resolutie zijn.

* In het midsourcingimplementatiemodel kan het volgende bericht worden weergegeven in de leveringslogboeken: **Fout tijdens het aanroepen van methode &#39;AppendDeliveryPart&#39; op de server voor midsourcing: &#39;Communicatiefout met de server: Controleer of deze correct is geconfigureerd. Code HTTP 408 &#39;Service tijdelijk niet beschikbaar&#39;**.

   De oorzaak hangt samen met prestatieproblemen. Het betekent dat de marketinginstantie te veel tijd besteedt aan het samenstellen van gegevens voordat ze deze naar de server voor midsourcing verzenden.

   Om dit op te lossen, adviseren wij een vacuüm en een herdex op het gegevensbestand uit te voeren. Raadpleeg [deze sectie](../../production/using/recommendations.md)voor meer informatie over databaseonderhoud.

   U moet ook alle werkstromen met een geplande activiteit opnieuw beginnen, en alle werkschema&#39;s in ontbroken status. Zie [deze sectie](../../workflow/using/scheduler.md).

* Wanneer een levering mislukt, kan de volgende fout in de leveringslogboeken verschijnen: **DLV-XXXX Het aantal voorbereid bericht (123) is groter dan het aantal te verzenden berichten (111). Neem contact op met de technische ondersteuning.**

   Gewoonlijk betekent deze fout dat er een verpersoonlijkingsgebied of een blok binnen e-mail is dat meer dan één waarden voor de ontvanger heeft. Er wordt een verpersoonlijkingsblok gebruikt en het haalt meer dan één record op voor een bepaalde ontvanger.

   Om dit op te lossen, controleer de gebruikte verpersoonlijkingsgegevens, en controleer dan het doel voor ontvangers die meer dan één ingang voor om het even welk van die gebieden hebben. U kunt een **[!UICONTROL Deduplication]** activiteit in het richten werkschema vóór de leveringsactiviteit ook gebruiken om te controleren er slechts één verpersoonlijkingsgebied tegelijkertijd is. Raadpleeg [deze pagina](../../workflow/using/deduplication.md)voor meer informatie over deduplicatie.

* Sommige levering kan mislukken met een &quot;Onbereikbare&quot;fout die verklaart: &quot;Binnenkomende e-mailstuit (regel &#39;Auto_responses&#39; komt overeen met deze stuit). Dit betekent dat de levering is gelukt, maar dat Adobe Campagne een automatisch antwoord van de ontvanger heeft ontvangen (bijvoorbeeld een antwoord &quot;Buiten-kantoor&quot;) dat overeenkwam met de regels voor inkomende e-mail &quot;Auto_responses&quot;. Het e-mailbericht waarin automatisch wordt gereageerd, wordt genegeerd door Adobe Campaign en het adres van de ontvanger wordt niet verzonden naar quarantines.

**Verwante onderwerpen:**

* [Leveringslogboeken en geschiedenis](#delivery-logs-and-history)
* [Leveringsfouten begrijpen](../../delivery/using/understanding-delivery-failures.md)
* [Typen leveringsfouten en redenen](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons)

## Aantal verzonden berichten {#number-of-messages-sent}

U kunt tot leveringen van de leveringslijst, via de **[!UICONTROL Campaign Management > Deliveries]** knoop van de boom toegang hebben.

Standaard bevat de lijst met leveringen de namen en statussen van de leveringen die in het geselecteerde knooppunt zijn gemaakt. Het toont ook het aantal berichten om te verzenden, te verwerken en met succes te verzenden.

* Het aantal ontvangers **[!UICONTROL Messages to send]** komt overeen met het aantal ontvangers dat na analyse en vóór levering wordt gevaccineerd.
* Het aantal berichten in de **[!UICONTROL success]** kolom komt overeen met het aantal berichten dat door de server wordt verzonden en door de ontvangers wordt ontvangen.
* Het aantal **[!UICONTROL processed]** berichten komt overeen met het aantal ontvangen berichten plus het aantal berichten met fouten.

Het leveringsdashboard laat u het aantal verzonden berichten volgen.

>[!NOTE]
>
>Voor grote leveringen wilt u deze waarden mogelijk bijwerken. U doet dit door de desbetreffende levering te selecteren en er vervolgens met de rechtermuisknop op te klikken. Selecteer **[!UICONTROL Action > Recompute delivery and tracking indicators...]** en gebruik de wizard om deze gegevens bij te werken.

## Geplande leveringen {#scheduled-deliveries-}

Als de leveringen niet op nauwkeurige geplande datum uitvoeren, kan het met een verschil tussen de tijdzone van servers verwant zijn. De instantie voor midsourcing en de productie-instantie kunnen zich in verschillende tijdzones bevinden.

Als de instantie van de midsourcing zich bijvoorbeeld in de tijdzone van Brisbane bevindt en de productie-instantie zich in de tijdzone van Darwin bevindt, zijn beide tijdzones een half uur van elkaar verwijderd, dan zou u in het auditlogboek duidelijk zien dat als de levering gepland is voor productie om 11:56, de zelfde levering gepland voor midden om 12:26 zou zijn die een verschil van een half uur heeft.
