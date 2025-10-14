---
product: campaign
title: Leveringsfouten begrijpen
description: Leer hoe u fouten met leveringen begrijpt
badge-v8: label="Ook van toepassing op v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
feature: Monitoring, Deliverability
role: User
exl-id: 86c7169a-2c71-4c43-8a1a-f39871b29856
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '2578'
ht-degree: 10%

---

# Leveringsfouten begrijpen{#understanding-delivery-failures}

## Leveringsfouten {#about-delivery-failures}

Wanneer een bericht (e-mail, SMS, pushmelding) niet naar een profiel kan worden verzonden, verstuurt de externe server automatisch een foutbericht dat door het Adobe Campaign-platform wordt opgepakt en gekwalificeerd is om te bepalen of het e-mailadres of telefoonnummer al dan niet in quarantaine moet worden geplaatst. Zie [&#x200B; stuiteren postbeheer &#x200B;](#bounce-mail-management).

>[!NOTE]
>
>**E-mailfoutberichten** (niet-bezorgde e-mails) worden gekwalificeerd door de Enhanced MTA (synchrone niet-bezorging) of door het inMail-proces (asynchrone niet-bezorging).
>
>**Sms-foutberichten** (of ‘SR’ voor ‘Statusrapport’) worden gekwalificeerd door het MTA-proces.

Zodra een bericht wordt verzonden, staat de leveringslogboeken u toe om de leveringsstatus voor elk profiel en het bijbehorende mislukkingstype en de reden te bekijken.

De berichten kunnen ook tijdens de leveringsvoorbereiding worden uitgesloten als een adres quarantined is of als een profiel op lijst van gewezen personen is. Uitgesloten berichten worden vermeld in het leveringsdashboard.

**Verwante onderwerpen:**

* [Leveringslogboeken en geschiedenis](delivery-dashboard.md#delivery-logs-and-history)
* [Mislukte status](delivery-performances.md#failed-status)
* [Typen leveringsfouten en redenen](#delivery-failure-types-and-reasons)

## Typen leveringsfouten en redenen {#delivery-failure-types-and-reasons}

Er zijn drie typen fouten wanneer een bericht mislukt. Elk fouttype bepaalt of een adres naar quarantines wordt verzonden. Voor meer op dit, verwijs naar [&#x200B; Voorwaarden om een adres naar quarantaine &#x200B;](understanding-quarantine-management.md#conditions-for-sending-an-address-to-quarantine) te verzenden

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
   <td> De account die aan het adres is gekoppeld, is niet meer actief. Wanneer de Internet Access Provider (IAP) een lange periode van inactiviteit detecteert, kan deze de account van de gebruiker sluiten. Leveringen aan het adres van de gebruiker zijn dan onmogelijk. Als de account tijdelijk is uitgeschakeld vanwege een inactiviteit van zes maanden en nog steeds kan worden geactiveerd, wordt de status Met fouten toegewezen en wordt de account opnieuw geprobeerd tot de foutenteller 5 bereikt. Als de foutensignalen dat de rekening permanent wordt gedeactiveerd, zal het direct aan Quarantine worden geplaatst.<br /> </td> 
  </tr> 
  <tr> 
   <td> Adres in quarantaine </td> 
   <td> Hard </td> 
   <td> 9 </td> 
   <td> Het adres werd geplaatst in quarantaine.<br /> </td> 
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
   <td> Het adres werd toegevoegd aan de lijst van gewezen personen op het tijdstip van verzending. Deze status wordt gebruikt voor het invoeren van gegevens van externe lijsten en externe systemen in de lijst van de Quarantaine van Adobe Campaign.<br /> </td> 
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
   <td> De ontvanger werd uitgesloten door een "arbitrage"type campagnetypologieregel.<br /> </td> 
  </tr> 
  <tr> 
   <td> Uitgesloten door een SQL-regel </td> 
   <td> Genegeerd </td> 
   <td> 11 </td> 
   <td> De ontvanger werd uitgesloten door een "SQL"regel van het type campagnetypologie.<br /> </td> 
  </tr> 
  <tr> 
   <td> Ongeldig domein </td> 
   <td> Zacht </td> 
   <td> 2 </td> 
   <td> Het domein van het e-mailadres is onjuist of bestaat niet meer. Dit profiel wordt opnieuw geactiveerd tot het aantal fouten 5 is. Na dit, zal het verslag aan de status van de Quarantaine worden geplaatst en zal geen retry volgen.<br /> </td> 
  </tr> 
  <tr> 
   <td> Postbus vol </td> 
   <td> Zacht </td> 
   <td> 5 </td> 
   <td> De brievenbus van deze gebruiker is volledig en kan niet meer berichten goedkeuren. Dit profiel wordt opnieuw geactiveerd tot het aantal fouten 5 is. Hierna wordt de record ingesteld op de status Quarantaine en wordt de levering niet opnieuw geprobeerd.<br /> Dit type fout wordt beheerd door een opschoonproces. Het adres wordt na 30 dagen ingesteld op een geldige status.<br /> Waarschuwing: als u wilt dat het adres automatisch wordt verwijderd uit de lijst met in quarantaine geplaatste adressen, moet de technische workflow voor het opschonen van databases worden gestart.<br /> </td> 
  </tr> 
  <tr> 
   <td> Niet verbonden </td> 
   <td> Genegeerd </td> 
   <td> 6 </td> 
   <td> De mobiele telefoon van de ontvanger wordt uitgezet of niet verbonden met het netwerk wanneer het bericht wordt verzonden.<br /> </td> 
  </tr> 
  <tr> 
   <td> Niet gedefinieerd </td> 
   <td> Niet gedefinieerd </td> 
   <td> 0 </td> 
   <td> Het adres is in kwalificatie omdat de fout nog niet is verhoogd. Dit type van fout komt voor wanneer een nieuw foutenbericht door de server wordt verzonden: het kan een geïsoleerde fout zijn, maar als het opnieuw voorkomt, stijgt de foutenteller, die de technische teams zal waarschuwen. Zij kunnen berichtanalyse dan uitvoeren en deze fout kwalificeren, via het <span class="uicontrol"> Beleid </span> / <span class="uicontrol"> Beheer van de Campagne </span> / <span class="uicontrol"> niet te leveren het Beheer van Beelden </span> knoop in de boomstructuur.<br /> </td> 
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
   <td> De maximumleveringsgrootte werd bereikt voor de ontvanger.<br /> </td> 
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
   <td> 1 </td> 
   <td> Het adres bestaat niet. Er worden geen verdere leveringen uitgevoerd voor dit profiel.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Retourneert na een tijdelijke leverfout {#retries-after-a-delivery-temporary-failure}

Als een bericht wegens a **Zacht** of **genegeerde** fout ontbreekt die tijdelijk is, zullen de pogingen tijdens de leveringsduur worden uitgevoerd.

>[!NOTE]
>
>Tijdelijk kunnen de ongeleverde berichten slechts met a **Zacht** of **worden verwant genegeerde** fout, maar niet a **Vaste** fout (zie [&#x200B; de mislukkingstypes en redenen van de Levering &#x200B;](#delivery-failure-types-and-reasons)).

>[!IMPORTANT]
>
>Voor ontvangen of hybride installaties, als u aan [&#x200B; Uitgebreide MTA &#x200B;](sending-with-enhanced-mta.md) hebt bevorderd, worden de retry montages in de levering niet meer gebruikt door Campagne. De zachte stuitpogingen en de tijdsduur tussen hen worden bepaald door Verbeterde MTA gebaseerd op het type en de strengheid van de stuiteringsreacties die van het e-maildomein van het bericht terugkomen.

Voor installaties op locatie en gehoste/hybride installaties die de oude Campagne MTA gebruiken, om de duur van een levering te wijzigen, ga naar de geavanceerde parameters van het leveringsmalplaatje en specificeer de gewenste duur op het overeenkomstige gebied. Zie deze [&#x200B; pagina &#x200B;](communication-channels.md) onder **Levering die** verzenden > **bepaalt de geldigheidsperiode**.

De standaardconfiguratie staat vijf herpogingen toe met intervallen van één uur, die door één herpoging per dag gedurende vier dagen worden gevolgd. Het aantal pogingen kan globaal worden veranderd (contacteer uw technische beheerder van Adobe) of voor elke levering of leveringsmalplaatje. Zie deze [&#x200B; pagina &#x200B;](communication-channels.md) onder **Levering die** verzenden > **vormen opnieuw probeert**.

## Synchrone en asynchrone fouten {#synchronous-and-asynchronous-errors}

Een bericht kan onmiddellijk (synchrone fout), of later op ontbreken, nadat het is verzonden (asynchrone fout).

* Synchrone fout: de externe mailserver waarmee contact is opgenomen door de Adobe Campaign-bezorgingsserver heeft onmiddellijk een foutbericht geretourneerd. De levering mag niet naar de server van het profiel worden verzonden. Adobe Campaign kwalificeert elke fout om te bepalen of de e-mailadressen in kwestie al dan niet in quarantaine moeten worden geplaatst. Zie [Kwalificatie van niet-bezorgde e-mails](#bounce-mail-qualification).
* Asynchrone fout: een stuiterende post of een SR werd opnieuw verzonden later door de ontvangende server. Deze post wordt geladen in een technische brievenbus de toepassing gebruikt om berichten met een fout te etiketteren. Asynchrone fouten kunnen optreden tot een week nadat een levering is verzonden.

  >[!NOTE]
  >
  >De configuratie van de stuiterende brievenbus is gedetailleerd in [&#x200B; deze sectie &#x200B;](../../installation/using/deploying-an-instance.md#managing-bounced-emails).

  De [&#x200B; terugkoppelt lijn &#x200B;](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html?lang=nl-NL#feedback-loops) werkt als stuitende e-mails. Wanneer een gebruiker een e-mail als spam kwalificeert, kunt u e-mailregels in Adobe Campaign configureren om alle leveringen aan deze gebruiker te blokkeren. Berichten die worden verzonden naar gebruikers die een e-mailbericht hebben gekwalificeerd als spam, worden automatisch omgeleid naar een e-mailvak dat speciaal voor dit doel is gemaakt. De adressen van deze gebruikers zijn op lijst van gewezen personen alhoewel zij niet de unsubscription verbinding klikten. De adressen zijn in lijst van gewezen personen in de (**NmsAddress**) quarantainelijst en niet in de (**NmsRecipient**) ontvankelijke lijst.

  >[!NOTE]
  >
  >Het beheer van de klacht is gedetailleerd in de [&#x200B; het beheerssectie van de Levering &#x200B;](about-deliverability.md).

## Bounce mail management {#bounce-mail-management}

Met het Adobe Campaign-platform kunt u mislukte e-mailleveringen beheren via de functie voor stuiterende e-mail.

Wanneer een e-mail niet aan een ontvanger kan worden geleverd, keert de verre overseinenserver automatisch een foutenmelding (stuiterende post) aan technische inbox terug die voor dit doel wordt ontworpen.

Voor installaties op locatie en gehoste/hybride installaties die gebruikmaken van de oude Campagne MTA, worden foutberichten verzameld door het Adobe Campaign-platform en gekwalificeerd door het InMail-proces om de lijst met regels voor e-mailbeheer te verrijken.

>[!IMPORTANT]
>
>Voor ontvangen of hybride installaties, als u aan [&#x200B; Verbeterde MTA &#x200B;](sending-with-enhanced-mta.md) hebt bevorderd, worden de meeste regels van het e-mailbeheer niet meer gebruikt. Zie [deze sectie](#email-management-rules)voor meer informatie.

### Bounce mail-kwalificatie {#bounce-mail-qualification}

>[!IMPORTANT]
>
>Voor ontvangen of hybride installaties, als u aan [&#x200B; Verbeterde MTA &#x200B;](sending-with-enhanced-mta.md) hebt bevorderd:
>
>* De stuitkwalificaties in de **[!UICONTROL Delivery log qualification]** lijst worden niet meer gebruikt voor **synchrone** de foutenmeldingen van de leveringsmislukking. Verbeterde MTA bepaalt het stuittype en de kwalificatie, en stuurt die informatie terug naar Campagne.
>
>* **Asynchrone** stuitingen worden nog gekwalificeerd door het inMail proces door de **[!UICONTROL Inbound email]** regels. Voor meer op dit, zie [&#x200B; E-mailbeheersregels &#x200B;](#email-management-rules).
>
>* Voor instanties die Uitgebreide MTA **zonder Webhooks** gebruiken, zullen de **[!UICONTROL Inbound email]** regels ook worden gebruikt om de synchrone stuiterende e-mails te verwerken die uit Verbeterde MTA komen, gebruikend het zelfde e-mailadres zoals voor asynchrone stuiterende e-mails.

Voor installaties op locatie en de gehoste/hybride installaties die de oude Campagne MTA gebruiken, wanneer de levering van een e-mail ontbreekt, ontvangt de de leveringsserver van Adobe Campaign een foutenmelding van de overseinenserver of de verre DNS server. De lijst met fouten bestaat uit tekenreeksen in het bericht dat door de externe server wordt geretourneerd. De types en de redenen van mislukkingen worden toegewezen aan elk foutenbericht.

Deze lijst is beschikbaar via het knooppunt **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Delivery log qualification]** . Het bevat alle regels die Adobe Campaign gebruikt om leveringsfouten te kwalificeren. Het is niet-limitatief en wordt regelmatig door Adobe Campaign bijgewerkt en kan ook door de gebruiker worden beheerd.

![](assets/tech_quarant_rules_qualif.png)

Het bericht dat door de externe server wordt geretourneerd bij de eerste instantie van dit fouttype, wordt weergegeven in de kolom **[!UICONTROL First text]** van de tabel **[!UICONTROL Delivery log qualification]** . Als deze kolom niet wordt weergegeven, klikt u op de knop **[!UICONTROL Configure list]** rechts onder aan de lijst om deze te selecteren.

![](assets/tech_quarant_rules_qualif_text.png)

Adobe Campaign filtert dit bericht om de inhoud van de variabele (zoals id&#39;s, datums, e-mailadressen, telefoonnummers, enz.) te verwijderen en geeft het gefilterde resultaat weer in de kolom **[!UICONTROL Text]** . De variabelen worden vervangen door **`#xxx#`** , behalve adressen die worden vervangen door **`*`** .

Dit proces staat toe om alle mislukkingen van het zelfde type samen te brengen en veelvoudige ingangen voor gelijkaardige fouten in de de kwalificatielijst van het Logboek van de Levering te vermijden.

>[!NOTE]
>
>In het veld **[!UICONTROL Number of occurrences]** wordt het aantal exemplaren van het bericht in de lijst weergegeven. Het is beperkt tot 100 000 voorvallen. U kunt het veld bewerken als u het bijvoorbeeld opnieuw wilt instellen.

Stuitberichten kunnen de volgende kwalificatiestatus hebben:

* **[!UICONTROL To qualify]** : de stuiterende post kan niet worden gekwalificeerd. De kwalificatie moet aan het leveringsteam worden toegewezen om efficiënte platformleverantie te waarborgen. Zolang het niet gekwalificeerd is, wordt de stuiterende post niet gebruikt om de lijst van e-mailbeheerregels te verrijken.
* **[!UICONTROL Keep]** : de stuiterende post werd gekwalificeerd en zal door **worden gebruikt verfrissen zich voor leverability** werkschema om aan bestaande e-mailbeheerregels worden vergeleken en de lijst verrijken.
* **[!UICONTROL Ignore]** : de stuiterende post wordt genegeerd door de Campagne MTA, betekenend dat deze stuit nooit het adres van de ontvanger zal veroorzaken om in quarantined te zijn. Het zal niet door **worden gebruikt verfrissen zich voor leverability** werkschema en het zal niet naar cliëntinstanties worden verzonden.

![](assets/deliverability_qualif_status.png)

>[!NOTE]
>
>In het geval van een stroomonderbreking van ISP, zullen de e-mails die door Campaign worden verzonden verkeerd als stegels worden gemerkt. U moet de stuiterkwalificatie bijwerken om dit te corrigeren. Ga voor meer informatie naar [deze pagina](update-bounce-qualification.md).

### E-mailbeheerregels {#email-management-rules}

>[!IMPORTANT]
>
>Voor ontvangen of hybride installaties, als u aan [&#x200B; Verbeterde MTA &#x200B;](sending-with-enhanced-mta.md) hebt bevorderd, worden de meeste regels van het e-mailbeheer niet meer gebruikt. Zie de volgende secties voor meer informatie.

E-mailregels zijn toegankelijk via het knooppunt **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Mail rule sets]** . De regels voor e-mailbeheer worden weergegeven in het onderste gedeelte van het venster.

![](assets/tech_quarant_rules.png)

>[!NOTE]
>
>De standaardparameters van het platform worden gevormd in de plaatsingstovenaar. Voor verdere informatie, verwijs naar [&#x200B; deze sectie &#x200B;](../../installation/using/deploying-an-instance.md).

De standaardregels zijn als volgt.

>[!IMPORTANT]
>
>* De leveringsserver (MTA) moet opnieuw worden begonnen als de parameters zijn veranderd.
>* De wijziging of invoering van beheerregels is alleen voor professionele gebruikers.

#### Binnenkomende e-mail {#inbound-email}

<!--
STATEMENT ONLY TRUE with Momentum and EFS+:
For hosted or hybrid installations, if you have upgraded to the [Enhanced MTA](sending-with-enhanced-mta.md), and if your instance has **Webhooks** functionality, the **[!UICONTROL Inbound email]** rules are no longer used for synchronous delivery failure error messages. For more on this, see [this section](#bounce-mail-qualification).

For on-premise installations and hosted/hybrid installations using the legacy Campaign MTA, these rules contain the list of character strings which can be returned by remote servers and which let you qualify the error (**Hard**, **Soft** or **Ignored**).-->

De **[!UICONTROL Inbound email]** regels bevatten de lijst van karakterkoorden die door verre servers kunnen zijn teruggekeerd en die u de fout (**Vast** laten kwalificeren, **Zacht** of **Genevend**).

Wanneer een e-mail ontbreekt, keert de verre server een stuitbericht aan het adres terug dat in de [&#x200B; platformparameters &#x200B;](../../installation/using/deploying-an-instance.md) wordt gespecificeerd. Adobe Campaign vergelijkt de inhoud van elke stuiterende post met de koorden in de lijst van regels, en wijst het dan één van de drie [&#x200B; foutentypes &#x200B;](#delivery-failure-types-and-reasons) toe.

>[!NOTE]
>
>De gebruiker kan zijn eigen regels tot stand brengen. Wanneer het invoeren van een pakket en wanneer het bijwerken van gegevens via **verfrissen zich voor leverability** werkschema, worden de user-created regels beschreven.

Voor meer bij stuiterende postkwalificatie, zie [&#x200B; deze sectie &#x200B;](#bounce-mail-qualification).

#### Domeinbeheer {#domain-management}

>[!IMPORTANT]
>
>Voor ontvangen of hybride installaties, als u aan [&#x200B; Verbeterde MTA &#x200B;](sending-with-enhanced-mta.md) hebt bevorderd, worden de **[!UICONTROL Domain management]** regels niet meer gebruikt. **DKIM (DomainKeys Identified Mail)**-e-mailverificatie wordt ondertekend door de Enhanced MTA voor alle berichten met alle domeinen. Deze ondertekent niet met **Afzender-id**, **DomainKeys** of **S/MIME**, tenzij anderszins opgegeven op Enhanced MTA-niveau.

Voor op-gebouw installaties en ontvangen/hybride installaties die de erfenis MTA van de Campagne gebruiken, past de het overseinenserver van Adobe Campaign één enkele **regel van het beheer van 0&rbrace; Domein op alle domeinen toe.**

<!--![](assets/tech_quarant_domain_rules_02.png)-->

* U kunt kiezen al dan niet om bepaalde identificatienormen en encryptiesleutels te activeren om de domeinnaam, zoals **identiteitskaart van de Afzender**, **DomainKeys**, **DKIM**, en **S/MIME** te controleren.
* De **SMTP relais** parameters laten u het IP adres en de haven van een relaisserver voor een bepaald domein vormen. Zie [deze sectie](../../installation/using/configuring-campaign-server.md#smtp-relay)voor meer informatie.

Als uw berichten in Vooruitzichten met **[!UICONTROL on behalf of]** in het afzenderadres worden getoond, zorg ervoor u uw e-mails met **identiteitskaart van de Afzender** niet ondertekent, die de verouderde merkgebonden standaard van de e-mailauthentificatie van Microsoft is. Als de **[!UICONTROL Sender ID]** optie wordt toegelaten, uncheck de overeenkomstige doos en contacteer [&#x200B; de Zorg van de Klant van Adobe &#x200B;](https://helpx.adobe.com/nl/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html). De leverbaarheid wordt niet beïnvloed.

#### MX-beheer {#mx-management}

>[!IMPORTANT]
>
>Voor ontvangen of hybride installaties, als u aan [&#x200B; Verbeterde MTA &#x200B;](sending-with-enhanced-mta.md) hebt bevorderd, worden de **[!UICONTROL MX management]** regels van de leveringsproductie niet meer gebruikt. Verbeterde MTA gebruikt zijn eigen MX regels die het toestaan om uw productie door domein aan te passen die op uw eigen historische e-mailreputatie wordt gebaseerd, en op real time terugkoppelen die uit de domeinen komt waar u e-mails verzendt.

Voor installaties op locatie en gehoste/hybride installaties die gebruikmaken van de oude Campagne MTA:

* De MX beheersregels worden gebruikt om de stroom van uitgaande e-mails voor een specifiek domein te regelen. Ze nemen een monster van de stuiterende berichten en blokkeren het verzenden, indien van toepassing.

* De het overseinenserver van Adobe Campaign past regels toe specifiek voor de domeinen, en toen de regels voor het algemene geval dat door een asterisk in de lijst van regels wordt vertegenwoordigd.

* Om MX beheersregels te vormen, plaats eenvoudig een drempel en selecteer bepaalde parameters SMTP. A **drempel** is een grens die als foutenpercentage wordt berekend waarvoorbij alle berichten naar een specifiek domein worden geblokkeerd. In het algemeen geldt dat het verzenden van e-mails voor minimaal 300 berichten drie uur wordt geblokkeerd als het foutenpercentage 90% bereikt.

Voor meer op MX beheer, verwijs naar [&#x200B; deze sectie &#x200B;](../../installation/using/email-deliverability.md#mx-configuration).
