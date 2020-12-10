---
solution: Campaign Classic
product: campaign
title: Leveringsfouten begrijpen
description: Leer hoe u fouten met leveringen begrijpt
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
translation-type: tm+mt
source-git-commit: 9ee7ef1faf06c31ec6659734582caac099a01bc1
workflow-type: tm+mt
source-wordcount: '2440'
ht-degree: 16%

---


# Leveringsfouten begrijpen{#understanding-delivery-failures}

## Leveringsfouten {#about-delivery-failures}

Wanneer een bericht (e-mail, SMS, pushmelding) niet naar een profiel kan worden verzonden, verstuurt de externe server automatisch een foutbericht dat door het Adobe Campaign-platform wordt opgepakt en gekwalificeerd is om te bepalen of het e-mailadres of telefoonnummer al dan niet in quarantaine moet worden geplaatst. Zie [Bounce mailbeheer](#bounce-mail-management).

>[!NOTE]
>
>E-mailfoutberichten (of &#39;bounces&#39;) worden gekwalificeerd door het InMail-proces. Sms-foutberichten (of ‘SR’ voor ‘Statusrapport’) worden gekwalificeerd door het MTA-proces.

Zodra een bericht wordt verzonden, staat de leveringslogboeken u toe om de leveringsstatus voor elk profiel en het bijbehorende mislukkingstype en de reden te bekijken.

De berichten kunnen ook tijdens de leveringsvoorbereiding worden uitgesloten als een adres quarantined is of als een profiel op lijst van afgewezen personen is. Uitgesloten berichten worden vermeld in het leveringsdashboard.

**Verwante onderwerpen:**

* [Leveringslogboeken en geschiedenis](../../delivery/using/delivery-dashboard.md#delivery-logs-and-history)
* [Mislukte status](../../delivery/using/delivery-performances.md#failed-status)
* [Typen leveringsfouten en redenen](#delivery-failure-types-and-reasons)

## Typen leveringsfouten en redenen {#delivery-failure-types-and-reasons}

Er zijn drie typen fouten wanneer een bericht mislukt. Elk fouttype bepaalt of een adres naar quarantines wordt verzonden. Voor meer op dit, verwijs naar [Voorwaarden om een adres naar quarantaine](../../delivery/using/understanding-quarantine-management.md#conditions-for-sending-an-address-to-quarantine) te verzenden

* **Hard**: Een ‘harde’ of permanente fout wijst op een ongeldig adres. Dit omvat een foutbericht waarin expliciet wordt aangegeven dat het adres ongeldig is, zoals een onbekende gebruiker.
* **Soft**: Dit kan een tijdelijke fout zijn of een fout die niet kan worden gecategoriseerd, zoals een ongeldig domein of een vol postvak.
* **Ignored**: Dit is een fout die doorgaans tijdelijk is, zoals een afwezigheidsbericht of een technische fout, bijvoorbeeld als het afzendertype ‘postmaster’ is.

De mogelijke redenen van een leveringsfout zijn:

<table> 
 <tbody> 
  <tr> 
   <td> Foutlabel </td> 
   <td> Fouttype </td> 
   <td> Technische waarde </td> 
   <td> Beschrijving </td> 
  </tr> 
  <tr> 
   <td> Account uitgeschakeld </td> 
   <td> Zacht/Hard </td> 
   <td> 4 </td> 
   <td> De account die aan het adres is gekoppeld, is niet meer actief. Wanneer de Internet Access Provider (IAP) een lange periode van inactiviteit detecteert, kan deze de account van de gebruiker sluiten. Leveringen aan het adres van de gebruiker zijn dan onmogelijk. Als de account tijdelijk is uitgeschakeld vanwege een inactiviteit van zes maanden en nog steeds kan worden geactiveerd, wordt de status Met fouten toegewezen en wordt de account opnieuw geprobeerd tot de foutenteller 5 bereikt. Als de fout aangeeft dat de account permanent is gedeactiveerd, wordt deze direct ingesteld op Quarantine.<br /> </td> 
  </tr> 
  <tr> 
   <td> Adres in quarantaine </td> 
   <td> Hard </td> 
   <td> 9 </td> 
   <td> Het adres is in quarantaine geplaatst.<br /> </td> 
  </tr> 
  <tr> 
   <td> Adres niet opgegeven </td> 
   <td> Hard </td> 
   <td> 7 </td> 
   <td> Geen adres wordt gegeven voor de ontvanger.<br /> </td> 
  </tr> 
  <tr> 
   <td> Adres van slechte kwaliteit </td> 
   <td> Genegeerd </td> 
   <td> 14 </td> 
   <td> De kwaliteitsbeoordeling voor dit adres is te laag.<br /> </td> 
  </tr> 
  <tr> 
   <td> Op de lijst met ongewenste personen staan adres </td> 
   <td> Hard </td> 
   <td> 8 </td> 
   <td> Het adres werd toegevoegd aan de lijst van afgewezen personen toen het verzenden. Deze status wordt gebruikt voor het importeren van gegevens van externe lijsten en externe systemen naar de lijst in Adobe Campaign Quarantine.<br /> </td> 
  </tr> 
  <tr> 
   <td> Besturingsadres </td> 
   <td> Genegeerd </td> 
   <td> 127 </td> 
   <td> Het adres van de ontvanger maakt deel uit van de controlegroep.<br /> </td> 
  </tr> 
  <tr> 
   <td> Dubbel </td> 
   <td> Genegeerd </td> 
   <td> 10 </td> 
   <td> Het adres van de ontvanger was reeds in deze levering.<br /> </td> 
  </tr> 
  <tr> 
   <td> Fout genegeerd </td> 
   <td> Genegeerd </td> 
   <td> 25 </td> 
   <td> Het adres staat op de lijst van gewenste personen. De fout wordt daarom genegeerd en er wordt een e-mail verzonden.<br /> </td> 
  </tr> 
  <tr> 
   <td> Uitgesloten na arbitrage </td> 
   <td> Genegeerd </td> 
   <td> 12 </td> 
   <td> De ontvanger werd uitgesloten door een campagnetypologieregel van het type 'arbitrage'.<br /> </td> 
  </tr> 
  <tr> 
   <td> Uitgesloten door een SQL-regel </td> 
   <td> Genegeerd </td> 
   <td> 11 </td> 
   <td> De ontvanger is uitgesloten door een 'SQL'-typologische regel voor de campagne.<br /> </td> 
  </tr> 
  <tr> 
   <td> Ongeldig domein </td> 
   <td> Zacht </td> 
   <td> 2 </td> 
   <td> Het domein van het e-mailadres is onjuist of bestaat niet meer. Dit profiel wordt opnieuw geactiveerd tot het aantal fouten 5 is. Hierna wordt de record ingesteld op de status Quarantaine en wordt de levering niet opnieuw geprobeerd.<br /> </td> 
  </tr> 
  <tr> 
   <td> Postbus vol </td> 
   <td> Zacht </td> 
   <td> 5 </td> 
   <td> De brievenbus van deze gebruiker is volledig en kan niet meer berichten goedkeuren. Dit profiel wordt opnieuw geactiveerd tot het aantal fouten 5 is. Hierna wordt de record ingesteld op de status Quarantaine en wordt de levering niet opnieuw geprobeerd.<br /> Dit type fout wordt beheerd door een schoonmaakproces, het adres wordt geplaatst aan een geldige status na 30 dagen.<br /> Waarschuwing: om het adres automatisch uit de lijst van quarantined adressen te verwijderen, moet het technische werkschema van de schoonmaakbeurt van het Gegevensbestand zijn begonnen.<br /> </td> 
  </tr> 
  <tr> 
   <td> Niet verbonden </td> 
   <td> Genegeerd </td> 
   <td> 6 </td> 
   <td> De mobiele telefoon van de ontvanger is uitgeschakeld of is niet verbonden met het netwerk wanneer het bericht wordt verzonden.<br /> </td> 
  </tr> 
  <tr> 
   <td> Niet gedefinieerd </td> 
   <td> Niet gedefinieerd </td> 
   <td> 0 </td> 
   <td> Het adres is in kwalificatie omdat de fout nog niet is verhoogd. Dit type fout treedt op wanneer een nieuw foutbericht wordt verzonden door de server: het kan een geïsoleerde fout zijn, maar als deze opnieuw voorkomt, zal de foutenteller stijgen en worden de technische teams gewaarschuwd. Ze kunnen vervolgens berichtanalyse uitvoeren en deze fout kwalificeren via het knooppunt <span class="uicontrol">Beheer</span> / <span class="uicontrol">Campagnebeheer</span> / <span class="uicontrol">Niet te leveren beheer</span> in de boomstructuur.<br /> </td> 
  </tr> 
  <tr> 
   <td> Niet in aanmerking komend voor de voorstellen </td> 
   <td> Genegeerd </td> 
   <td> 16 </td> 
   <td> De ontvanger kwam niet in aanmerking voor de aanbiedingen in de levering.<br /> </td> 
  </tr> 
  <tr> 
   <td> Geweigerd </td> 
   <td> Zacht/Hard </td> 
   <td> 20 </td> 
   <td> Het adres is in quarantaine geplaatst toe te schrijven aan een veiligheid terugkoppelt als spamrapport. Volgens de fout, zal het adres opnieuw worden geprobeerd tot de foutenteller 5 bereikt, of het zal direct naar quarantines worden verzonden.<br /> </td> 
  </tr> 
  <tr> 
   <td> Beperkte doelgrootte </td> 
   <td> Genegeerd </td> 
   <td> 17 </td> 
   <td> De maximale leveringsgrootte is bereikt voor de ontvanger.<br /> </td> 
  </tr> 
  <tr> 
   <td> Onbevoegd adres </td> 
   <td> Genegeerd </td> 
   <td> 15 </td> 
   <td> Het postadres is niet gekwalificeerd.<br /> </td> 
  </tr> 
  <tr> 
   <td> Onbereikbaar </td> 
   <td> Zacht/Hard </td> 
   <td> 3 </td> 
   <td> Er is een fout opgetreden in de berichtleveringsketen. Het zou een incident op het relais SMTP, een domein kunnen zijn dat tijdelijk onbereikbaar is, etc. Volgens de fout, zal het adres opnieuw worden geprobeerd tot de foutenteller 5 bereikt, of het zal direct naar quarantines worden verzonden.<br /> </td> 
  </tr> 
  <tr> 
   <td> Gebruiker onbekend </td> 
   <td> Hard </td> 
   <td> 3 </td> 
   <td> Het adres bestaat niet. Voor dit profiel worden geen verdere leveringen uitgevoerd.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Nieuwe pogingen na een tijdelijke leveringsfout {#retries-after-a-delivery-temporary-failure}

Als een bericht ontbreekt toe te schrijven aan een **Zachte** of **Genegeerde** fout die tijdelijk is, zullen de pogingen tijdens de leveringsduur worden uitgevoerd.

>[!NOTE]
>
>Tijdelijk niet-geleverde berichten kunnen alleen worden gerelateerd aan een **Soft**- of **Genegeerde**-fout, maar niet aan een **Hard**-fout (zie [Typen en redenen voor leveringsfouten](#delivery-failure-types-and-reasons)).

Om de duur van een levering te wijzigen, ga naar de geavanceerde parameters van het levering of leveringsmalplaatje en specificeer de gewenste duur op het overeenkomstige gebied. De geavanceerde leveringseigenschappen worden voorgesteld in [deze sectie](../../delivery/using/steps-sending-the-delivery.md#defining-validity-period).

De standaardconfiguratie staat vijf herpogingen toe met intervallen van één uur, die door één herpoging per dag gedurende vier dagen worden gevolgd. Het aantal pogingen kan globaal worden veranderd (contacteer uw Adobe technische beheerder) of voor elke levering of leveringsmalplaatje (zie [deze sectie](../../delivery/using/steps-sending-the-delivery.md#configuring-retries)).

## Synchrone en asynchrone fouten {#synchronous-and-asynchronous-errors}

Een bericht kan onmiddellijk (synchrone fout), of later op ontbreken, nadat het is verzonden (asynchrone fout).

* Synchrone fout: Als de externe mailserver waarmee contact is opgenomen door de Adobe Campaign-leveringsserver onmiddellijk een foutbericht heeft geretourneerd, mag de levering niet naar de server van het profiel worden verzonden. Adobe Campaign kwalificeert elke fout om te bepalen of de e-mailadressen in kwestie al dan niet in quarantaine moeten worden geplaatst. Zie [Kwalificatie van niet-bezorgde e-mails](#bounce-mail-qualification).
* Asynchrone fout: Een niet-bezorgde e-mail of een SR is later opnieuw verzonden door de ontvangende server. Deze post wordt geladen in een technische brievenbus de toepassing gebruikt om berichten met een fout te etiketteren. Asynchrone fouten kunnen optreden tot een week nadat een levering is verzonden.

   >[!NOTE]
   >
   >De configuratie van de stuiterende brievenbus is gedetailleerd in [deze sectie](../../installation/using/deploying-an-instance.md#managing-bounced-emails).

   De [feedbacklus](../../delivery/using/technical-recommendations.md#feedback-loop) werkt als e-mailberichten die stuiteren. Wanneer een gebruiker een e-mail als spam kwalificeert, kunt u e-mailregels in Adobe Campaign configureren om alle leveringen aan deze gebruiker te blokkeren. Berichten die worden verzonden naar gebruikers die een e-mailbericht hebben gekwalificeerd als spam, worden automatisch omgeleid naar een e-mailvak dat speciaal voor dit doel is gemaakt. De adressen van deze gebruikers zijn op lijst van afgewezen personen alhoewel zij niet de unsubscription verbinding klikten. De adressen zijn in lijst van afgewezen personen in de (**NmsAddress**) quarantainetabel en niet in (**NmsRecipient**) ontvankelijke lijst.

   >[!NOTE]
   >
   >Het klachtenbeheer wordt beschreven in de sectie [Leveringsbeheer](../../delivery/using/about-deliverability.md).

## Bounce mail management {#bounce-mail-management}

Met het Adobe Campaign-platform kunt u mislukte e-mailleveringen beheren via de functie voor stuiterende e-mail. Wanneer een e-mail niet aan een ontvanger kan worden geleverd, keert de verre overseinenserver automatisch een foutenmelding (stuiterende post) aan technische inbox terug die voor dit doel wordt ontworpen. Foutberichten worden verzameld door het Adobe Campaign-platform en gekwalificeerd door het inMail-proces om de lijst met regels voor e-mailbeheer te verrijken

### Kwalificatie van niet-bezorgde e-mails {#bounce-mail-qualification}

Wanneer de levering van een e-mail ontbreekt, ontvangt de leverings server van Adobe Campaign een foutenmelding van de overseinenserver of de verre DNS server. De lijst met fouten bestaat uit tekenreeksen in het bericht dat door de externe server wordt geretourneerd. De types en de redenen van mislukkingen worden toegewezen aan elk foutenbericht.

Deze lijst is beschikbaar via de **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Delivery log qualification]** knoop. Het bevat alle regels die door Adobe Campaign worden gebruikt om leveringsfouten te kwalificeren. Het is niet-limitatief en wordt regelmatig door Adobe Campaign bijgewerkt en kan ook door de gebruiker worden beheerd.

![](assets/tech_quarant_rules_qualif.png)

* Het bericht dat door de externe server wordt geretourneerd bij de eerste instantie van dit fouttype, wordt weergegeven in de kolom **[!UICONTROL First text]** van de tabel **[!UICONTROL Delivery log qualification]**. Als deze kolom niet wordt weergegeven, klikt u op de knop **[!UICONTROL Configure list]** rechts onder aan de lijst om deze te selecteren.

![](assets/tech_quarant_rules_qualif_text.png)

Adobe Campaign filtert dit bericht om de variabele inhoud (zoals id&#39;s, datums, e-mailadressen, telefoonnummers, enz.) te verwijderen. en geeft het gefilterde resultaat weer in de kolom **[!UICONTROL Text]**. De variabelen worden vervangen door **`#xxx#`**, behalve adressen die met **`*`** worden vervangen.

Dit proces staat toe om alle mislukkingen van het zelfde type samen te brengen en veelvoudige ingangen voor gelijkaardige fouten in de de kwalificatielijst van het Logboek van de Levering te vermijden.

>[!NOTE]
>
>In het veld **[!UICONTROL Number of occurrences]** wordt het aantal exemplaren van het bericht in de lijst weergegeven. Het is beperkt tot 100 000 voorvallen. U kunt het veld bewerken als u het bijvoorbeeld opnieuw wilt instellen.

Stuitberichten kunnen de volgende kwalificatiestatus hebben:

* **[!UICONTROL To qualify]** : de stuiterende post kon niet worden gekwalificeerd. De kwalificatie moet aan het leveringsteam worden toegewezen om efficiënte platformleverantie te waarborgen. Zolang het niet gekwalificeerd is, wordt de stuiterende post niet gebruikt om de lijst van e-mailbeheerregels te verrijken.
* **[!UICONTROL Keep]** : de stuiterende post werd gekwalificeerd en zal door  **Vernieuwen voor** leveringsworkflow worden gebruikt om met bestaande e-mailbeheerregels te worden vergeleken en de lijst te verrijken.
* **[!UICONTROL Ignore]** : de stuiterende post wordt genegeerd door de Campagne MTA, betekenend dat deze stuit nooit het adres van de ontvanger zal veroorzaken om in quarantined te zijn. Deze wordt niet gebruikt door de **Vernieuwen voor leverbaarheid**-workflow en wordt niet naar clientinstanties verzonden.

![](assets/deliverability_qualif_status.png)

>[!IMPORTANT]
>
>Voor gehoste of hybride installaties, als u aan Verbeterde MTA hebt bevorderd:
>
>* De stuiterende kwalificaties in de **[!UICONTROL Delivery log qualification]** lijst worden niet meer gebruikt voor synchrone de foutenmeldingen van de leveringsmislukking. Verbeterde MTA bepaalt het stuittype en de kwalificatie, en stuurt die informatie terug naar Campagne.
   >
   >
* Asynchrone niet-bezorgingen worden nog steeds gekwalificeerd door het inMail-proces aan de hand van de regels voor **[!UICONTROL Inbound email]**. Zie [Regels voor e-mailbeheer](#email-management-rules) voor meer informatie.
   >
   >
* Voor instanties die de verbeterde MTA zonder **Webhooks/EFS** gebruiken, zullen de **[!UICONTROL Inbound email]** regels ook worden gebruikt om de synchrone stuiterende e-mails te verwerken die uit Verbeterde MTA komen, gebruikend het zelfde e-mailadres zoals voor asynchrone stuiterende e-mails.
>
>
Raadpleeg [dit document](https://helpx.adobe.com/nl/campaign/kb/acc-campaign-enhanced-mta.html) voor meer informatie over de Adobe Campaign Enhanced MTA.

### E-mailbeheerregels {#email-management-rules}

De regels van de post worden betreden via de **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Mail rule sets]** knoop. De regels voor e-mailbeheer worden weergegeven in het onderste gedeelte van het venster.

![](assets/tech_quarant_rules.png)

>[!NOTE]
>
>De standaardparameters van het platform worden gevormd in de plaatsingstovenaar. Zie [deze sectie](../../installation/using/deploying-an-instance.md) voor meer informatie.

De standaardregels zijn als volgt.

>[!IMPORTANT]
>
>* De leveringsserver (MTA) moet opnieuw worden begonnen als de parameters zijn veranderd.
>* De wijziging of invoering van beheerregels is alleen voor professionele gebruikers.


#### Binnenkomende e-mail {#inbound-email}

Deze regels bevatten de lijst met tekenreeksen die door externe servers kunnen worden geretourneerd en waarmee u de fout (**Hard**, **Soft** of **Ignored**) kunt kwalificeren.

Wanneer een e-mail mislukt, retourneert de externe server een stuiterend bericht naar het adres dat is opgegeven in de platformparameters. Adobe Campaign vergelijkt de inhoud van elke stuiterende post met de koorden in de lijst van regels, en wijst het dan toe één van de drie [foutentypes](#delivery-failure-types-and-reasons).

>[!NOTE]
>
>De gebruiker kan zijn eigen regels tot stand brengen. Bij het invoeren van een pakket en wanneer het bijwerken van gegevens via **verfrissen zich voor leverability** werkschema, worden de user-created regels beschreven.

Zie [deze sectie](#bounce-mail-qualification) voor meer informatie over stuiterende mailkwalificatie.

>[!IMPORTANT]
>
>Voor gehoste of hybride installaties, als u aan Verbeterde MTA hebt bevorderd, en als uw instantie **Webhooks/EFS** functionaliteit heeft, worden **[!UICONTROL Inbound email]** regels niet meer gebruikt voor synchrone de foutenmeldingen van de leveringsmislukking. Zie [deze sectie](#bounce-mail-qualification)voor meer informatie.
>
>Raadpleeg [dit document](https://helpx.adobe.com/campaign/kb/acc-campaign-enhanced-mta.html) voor meer informatie over de Adobe Campaign Enhanced MTA.

#### Domeinbeheer {#domain-management}

De het overseinenserver van Adobe Campaign past één enkele **regel van het Domeinbeheer** op alle domeinen toe.

<!--![](assets/tech_quarant_domain_rules_02.png)-->

* U kunt kiezen of u bepaalde identificatienormen en coderingssleutels wilt activeren om de domeinnaam te controleren, zoals **Verzender ID**, **DomainKeys**, **DKIM** en **S/MIME**.
* Met de parameters **SMTP relais** kunt u het IP-adres en de poort van een relaisserver voor een bepaald domein configureren. Zie [deze sectie](../../installation/using/configuring-campaign-server.md#smtp-relay)voor meer informatie.

Als uw berichten in Vooruitzichten met **[!UICONTROL on behalf of]** in het afzenderadres worden getoond, zorg ervoor u niet uw e-mails met **identiteitskaart van de Afzender** ondertekent, die de verouderde merkgebonden standaard van de e-mailauthentificatie van Microsoft is. Als de optie **[!UICONTROL Sender ID]** is ingeschakeld, schakelt u het betreffende vakje uit en neemt u contact op met de Adobe Campaign-ondersteuning. De leverbaarheid wordt niet beïnvloed.

>[!IMPORTANT]
>
>Voor gehoste of hybride installaties, als u aan Verbeterde MTA hebt bevorderd, worden de **[!UICONTROL Domain management]** regels niet meer gebruikt. **DKIM (DomainKeys Identified Mail)**-e-mailverificatie wordt ondertekend door de Enhanced MTA voor alle berichten met alle domeinen. Deze ondertekent niet met **Afzender-id**, **DomainKeys** of **S/MIME**, tenzij anderszins opgegeven op Enhanced MTA-niveau.
>
>Raadpleeg [dit document](https://helpx.adobe.com/campaign/kb/acc-campaign-enhanced-mta.html) voor meer informatie over de Adobe Campaign Enhanced MTA.

#### MX-beheer {#mx-management}

* De MX beheersregels worden gebruikt om de stroom van uitgaande e-mails voor een specifiek domein te regelen. Ze nemen een monster van de stuiterende berichten en blokkeren het verzenden, indien van toepassing.

* De het overseinenserver van Adobe Campaign past regels toe specifiek voor de domeinen, en toen de regels voor het algemene geval dat door een asterisk in de lijst van regels wordt vertegenwoordigd.

* Om MX beheersregels te vormen, plaats eenvoudig een drempel en selecteer bepaalde parameters SMTP. Een **drempel** is een grens die als foutenpercentage wordt berekend waarwaarwaarvoorbij alle berichten naar een specifiek domein worden geblokkeerd. In het algemeen geldt dat het verzenden van e-mails voor minimaal 300 berichten drie uur wordt geblokkeerd als het foutenpercentage 90% bereikt.

Raadpleeg [deze sectie](../../installation/using/email-deliverability.md#mx-configuration) voor meer informatie over MX-beheer.

>[!IMPORTANT]
>
>Voor gehoste of hybride installaties, als u aan Verbeterde MTA hebt bevorderd, worden **[!UICONTROL MX management]** de regels van de leveringsproductie niet meer gebruikt. Verbeterde MTA gebruikt zijn eigen MX regels die het toestaan om uw productie door domein aan te passen die op uw eigen historische e-mailreputatie wordt gebaseerd, en op real time terugkoppelen die uit de domeinen komt waar u e-mails verzendt.
>
>Raadpleeg [dit document](https://helpx.adobe.com/campaign/kb/acc-campaign-enhanced-mta.html) voor meer informatie over de Adobe Campaign Enhanced MTA.
