---
solution: Campaign Classic
product: campaign
title: Verzenden met de verbeterde MTA in Adobe Campaign Classic
description: Meer informatie over de reikwijdte en de specifieke kenmerken van het verzenden van e-mails met de Adobe Campaign Enhanced MTA.
audience: delivery
content-type: reference
topic-tags: sending-emails
exl-id: 58cc23f4-9ab0-45c7-9aa2-b08487ec7e91
source-git-commit: 54d503e97a4374927c4ebe3ba4e0ec05e51d47db
workflow-type: tm+mt
source-wordcount: '1921'
ht-degree: 3%

---

# Verzenden met de Enhanced MTA {#sending-with-enhanced-mta}

De **Adobe Campaign Enhanced MTA** (Mail Transfer Agent) biedt een geüpgrade verzendende infrastructuur die verbeterde prestaties, reputatie, doorvoer, rapportering, stuiteringsafhandeling, IP-opruiming en beheer van verbindingsinstellingen mogelijk maakt.

Het is geïmplementeerd om de schaalbaarheid te verbeteren, de doorvoer van de levering te verhogen en meer e-mails sneller te verzenden. Dit wordt bereikt met nieuwe adaptieve leveringstechnieken die e-mailverzendende montages in real time veranderen gebaseerd op terugkoppelen van de Dienstverleners van Internet.

>[!IMPORTANT]
>
>De Adobe Campaign Enhanced MTA is alleen beschikbaar voor door Campaign Classic gehoste of hybride klanten. Campaign Classic-installaties op locatie kunnen niet worden bijgewerkt om de verbeterde MTA te gebruiken.

Als u een instantie van de Campaign Classic na September 2018 provisioned was, gebruikt u Verbeterde MTA. Zie de [Veelgestelde vragen](#enhanced-mta-faq) hieronder voor alle andere Campaign Classic-klanten.

De verbeterde implementatie MTA kan enkele bestaande functionaliteit van de Campagne beïnvloeden. Zie [Verbeterde specifieke kenmerken van MTA](#enhanced-mta-impacts) voor meer informatie.

>[!NOTE]
>
>Als u een eindgebruiker van Adobe Campaign bent en u wilt weten of uw instantie aan Verbeterde MTA is bevorderd, contacteer uw interne beheerder van de Campagne.

## Veelgestelde vragen {#enhanced-mta-faq}

### Gebruik en voordelen

**Wat is de verbeterde MTA?**

Adobe Campaign kan nu worden bevorderd om een nieuwe MTA (de Agent van de Overdracht van de Post) te gebruiken die commerciële e-mail MTA van SparkPost genoemd **Momentum** in werking stelt.

Momentum vertegenwoordigt innovatieve, krachtige MTA-technologie, die slimmere stuiterende behandeling en een geautomatiseerde optimaliseringscapaciteit van de leverbaarheid omvat die afzenders helpt optimale inbusleversnelheden te bereiken en te handhaven. <!--More than 37% of the world’s business email is sent using SparkPost’s MTA technology.-->

**Wat zijn de voordelen?**

* Adobe Campaign-clients die gebruikmaken van de Enhanced MTA hebben een enorme toename van de totale doorvoersnelheid gezien en een <!--90%+-->aanzienlijke vermindering van zachte grenzen.<!--300%-->
* De verbeterde MTA gebruikt de recentste technologie MTA om u van de optimale productiesnelheden voor uw e-maillevering te voorzien.
* Door zich direct en automatisch aan te passen aan de feedback die het ontvangt, zorgt het er ook voor dat de e-mail nauwkeuriger en intelligenter wordt geleverd met realtime leveringsgegevens.

**Kan ik tegelijkertijd de native Adobe Campaign MTA en de Enhanced MTA gebruiken?**

Nee. Alleen de verbeterde MTA kan worden gebruikt voor uw e-mailleveringen nadat uw exemplaar is bijgewerkt.

<!--
**Is there a fee associated with upgrading my instance to and subsequent use of the Enhanced MTA?**
No, there is no extra fee associated with the upgrade process to enable the use of the Enhanced MTA.

**When will the Enhanced MTA be available to me?**

* If you are new to Adobe Campaign Classic, you are already using the Enhanced MTA.

* For Adobe Campaign Classic existing customers, we’ve implemented a phased rollout that covers all hosted or partially hosted (hybrid) instances. If you’re not already using it, we’ll be contacting you in the near future with the dates and details for upgrading your Adobe Campaign Classic instances to the Enhanced MTA.
-->

### Verbetering van de verbeterde MTA

**Wat wordt vereist om aan Verbeterde MTA te bevorderen?**

Als u na september 2018 een instantie van Campaign Classic was voorzien, wordt geen actie vereist aangezien u reeds Uitgebreide MTA gebruikt.

Voor alle andere gehoste of gedeeltelijk gehoste (hybride) klanten bereikt het Adobe Campaign-team een datum voor de migratie en geeft het details over de juiste stappen die nodig zijn voor de migratie.

>[!IMPORTANT]
>
>De verbeterde MTA is niet beschikbaar voor installaties op locatie.

**Wat is het proces om mijn instantie aan Verbeterde MTA te bevorderen?**

Het gehele proces voor de gehoste exemplaren vereist een paar minuten downtime. Adobe controleert de e-maildoorvoer en de leveringscapaciteit tot 24 uur na de upgrade om de impact op uw e-mailleveringen te beoordelen.

Als er problemen worden ontdekt, kan Adobe uw exemplaar snel en tijdelijk terugzetten naar de native Adobe Campaign MTA.

Momenteel heeft de verbeterde MTA alleen invloed op het e-mailkanaal. Uw pushberichten en SMS-leveringen blijven gebruikmaken van de native Campagne MTA en worden op geen enkele wijze beïnvloed door de upgrade.

**Moet ik opnieuw door IP opwarming na verbetering aan Verbeterde MTA gaan?**

Nee. De bevordering vereist geen omschakeling aan nieuwe IPs, zodat kunt u blijven gebruikend uw bestaande, verwarmde e-mailIPs.

**Zal de upgrade naar de uitgebreide overeenkomst inzake commercieel vervoer gevolgen hebben voor campagnes of leveringen die momenteel worden uitgevoerd?**

Alle leveringen die waren voorbereid voordat uw instantie werd geüpgraded om de verbeterde MTA te gebruiken, moeten opnieuw worden voorbereid om de nieuwe MTA correct te kunnen gebruiken.

Voor klanten die de functionaliteit van het de transactieoverseinen van Adobe Campaign gebruiken, zullen om het even welke API vraag om een e-mail teweeg te brengen tijdens de zeer korte verbeteringsonderbreking in de rij worden geplaatst en zullen na voltooiing van de verbetering worden geprobeerd.

## Verbeterde specifieke kenmerken voor MTA {#enhanced-mta-impacts}

### Verbeterde MTA-headers

De recentste instanties van de Campaign Classic omvatten code die de vereiste Verbeterde kopballen MTA aan elk bericht toevoegt. Als u Adobe Campaign 19.1 (build 9032) of hoger gebruikt en dit niet het geval is, moet u [Adobe Klantzorg ](https://helpx.adobe.com/nl/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) verzoeken om de parameter &quot;useMomentum=true&quot; toe te voegen aan de configuratie van de uitvoeringsinstantie (in het bestand [serverConf.xml](../../installation/using/the-server-configuration-file.md#mta)), wat uw marketinginstantie kan zijn, [-sourcing instantie](../../installation/using/mid-sourcing-server.md), of [instantie voor het uitvoeren van transactieberichten](../../message-center/using/configuring-instances.md#execution-instance), afhankelijk van uw configuratie.

Nochtans, als u een oudere instantie gebruikt die deze code niet omvat, moet een nieuwe typologieregel genoemd **[!UICONTROL Typology Rule for Enhanced MTAs]** aan alle bestaande typologieën in uw instantie van de Campagne worden toegevoegd.
Deze regel wordt toegevoegd door een **[!UICONTROL Typology]** pakket dat als deel van de verbetering aan Verbeterde MTA wordt geïnstalleerd.

>[!IMPORTANT]
>
>Als u deze typologieregel in uw typologieën ziet, schrap of wijzig het op geen enkele manier. Anders kunnen de e-mailleveringen nadelig worden beïnvloed.

Dit **[!UICONTROL Typology]**-pakket moet worden geïnstalleerd op het marketingexemplaar van Adobe Campaign.

Als u een hybride client bent, geeft het Adobe Campaign-team u instructies voor het installeren van het **[!UICONTROL Typology]**-pakket op uw marketingexemplaar als onderdeel van de upgrade naar de verbeterde MTA. Neem contact op met uw accountmanager voor de volledige instructies.

>[!IMPORTANT]
>
>Instructies die door het Adobe Campaign-team worden verstrekt over de installatie van het **[!UICONTROL Typology]**-pakket moeten zorgvuldig worden opgevolgd. Anders kunnen er grote problemen optreden met uw IP&#39;s die worden gebruikt om e-mails te verzenden.

Zie [deze sectie](../../campaign/using/about-campaign-typologies.md) voor meer informatie over typologieën.

### Nieuwe MX-regels

De MX regels van de het beheersleveringsproductie worden niet meer gebruikt. Verbeterde MTA heeft zijn eigen MX regels die het toestaan om uw productie door domein aan te passen die op uw eigen historische e-mailreputatie wordt gebaseerd, en op real time terugkoppelen die uit de domeinen komt waar u e-mails verzendt.

Zie [deze sectie](../../installation/using/email-deliverability.md#mx-configuration) voor meer informatie over MX-configuratie.

### Stuitkwalificatie

De stuiterkwalificaties in de tabel Campagne **[!UICONTROL Delivery log qualification]** worden niet meer gebruikt voor foutberichten van **synchrone**-leveringsfout. Verbeterde MTA bepaalt het stuittype en de kwalificatie, en stuurt die informatie terug naar Campagne.

>[!NOTE]
>
>Verbeterde MTA kwalificeert de stuit SMTP en verzendt die kwalificatie terug naar Campagne in de vorm van een stuitercode die aan een de stuiteringsreden en kwalificatie van de Campagne in kaart wordt gebracht.

Zie [deze sectie](../../delivery/using/understanding-delivery-failures.md#bounce-mail-qualification) voor meer informatie over stuitkwalificatie.

### Leveringsdoorvoer

De grafiek van de productie van de Levering van de Campagne zal niet meer de productie aan uw e-mailontvangers tonen. Die grafiek zal nu de productiesnelheid voor het relais van uw berichten van Campaign over aan Verbeterde MTA tonen.

Zie [deze sectie](../../reporting/using/global-reports.md#delivery-throughput) voor meer informatie over de doorvoer van de levering.

### Geldigheidsperiode

De geldigheidsperiode die in uw campagneleveringen wordt ingesteld, wordt alleen door de verbeterde MTA gebruikt als deze is ingesteld op **3,5 dagen of minder**. Als u in Campagne een waarde definieert die hoger is dan 3,5 dagen, wordt hiermee geen rekening gehouden.

Bijvoorbeeld, als de geldigheidsperiode aan de standaardwaarde van 5 dagen in Campagne wordt geplaatst, zullen de zachte-stuiterende berichten in de Verbeterde MTA hertry rij gaan en slechts 3.5 dagen worden opnieuw geprobeerd vanaf toen dat bericht Verbeterde MTA bereikte. In dat geval wordt de waarde die is ingesteld in Campaign niet gebruikt.

Wanneer een bericht gedurende 3,5 dagen in de wachtrij van de Enhanced MTA heeft gestaan en niet is geleverd, treedt er een time-out op en zal de status van het bericht worden bijgewerkt van **[!UICONTROL Sent]** naar **[!UICONTROL Failed]** in de leveringslogboeken.

Zie [deze sectie](../../delivery/using/steps-sending-the-delivery.md#defining-validity-period) voor meer informatie over de geldigheidsperiode.

### DKIM-ondertekening

DKIM (DomainKeys Identified Mail) e-mailverificatie wordt ondertekend door de Enhanced MTA. DKIM-signing door de native Campagne MTA zal worden uitgezet binnen de beheerlijst van het Domein als deel van de Verbeterde verbetering MTA.
Voor meer op DKIM, zie [de Gids van de Beste praktijken van de Levering van de Adobe ](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#authentication).

### Leveringssuccesrapportage

In **[!UICONTROL Summary]** mening van een e-maillevering [dashboard](../../delivery/using/delivery-dashboard.md), begint **[!UICONTROL Success]** percentage bij 100% en gaat dan geleidelijk door de levering [geldigheidsperiode ](../../delivery/using/steps-sending-the-delivery.md#defining-validity-period), aangezien de zachte en harde grenzen van Verbeterde MTA aan Campagne worden gemeld.

Alle berichten worden namelijk als **[!UICONTROL Sent]** weergegeven in de [verzendende logbestanden](../../delivery/using/delivery-dashboard.md#delivery-logs-and-history) zodra deze zijn afgespeeld vanuit Campagne naar de Enhanced MTA. Zij blijven in die status tenzij of tot een [bounce](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons) voor dat bericht wordt meegedeeld terug van Verbeterde MTA aan Campagne.

Wanneer hard-bouncing berichten van Verbeterde MTA worden gemeld, verandert hun status van **[!UICONTROL Sent]** in **[!UICONTROL Failed]** en **[!UICONTROL Success]** percentage dienovereenkomstig wordt verminderd.

Wanneer de soft-bouncing berichten terug van Verbeterde MTA worden gemeld, tonen zij nog als **[!UICONTROL Sent]** en **[!UICONTROL Success]** percentage wordt nog niet bijgewerkt. Zachte berichten worden dan [opnieuw geprobeerd](../../delivery/using/understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure) door de periode van de leveringsgeldigheid:

* Als een nieuwe poging voor het eind van de geldigheidsperiode succesvol is, blijft de berichtstatus zoals **[!UICONTROL Sent]** en **[!UICONTROL Success]** percentage blijft onveranderd.

* Anders verandert de status in **[!UICONTROL Failed]** en wordt het **[!UICONTROL Success]** percentage dienovereenkomstig verlaagd.

Daarom moet u wachten tot het einde van de geldigheidsperiode om het laatste **[!UICONTROL Success]**-percentage en het uiteindelijke aantal feitelijk **[!UICONTROL Sent]**- en **[!UICONTROL Failed]**-berichten weer te geven.

<!--The fact that the Success percentage will go to 100% very quickly indicates that your instance has been upgraded to the Enhanced MTA.-->

### E-mailfeedbackservice (bèta) {#email-feedback-service}

Met de e-mailfeedbackservice (EFS) wordt de status van elke e-mail correct gerapporteerd, omdat feedback rechtstreeks wordt vastgelegd via de Enhanced MTA (Message Transfer Agent).

>[!IMPORTANT]
>
>De e-mailfeedbackservice is momenteel beschikbaar als bètafunctie.
>
>Als u geïnteresseerd bent in deelname aan dit bètaprogramma, vult u [dit formulier](https://forms.office.com/Pages/ResponsePage.aspx?id=Wht7-jR7h0OUrtLBeN7O4Rol2vQGupxItW9_BerXV6VUQTJPN1Q5WUI4OFNTWkYzQjg3WllUSDAxWi4u) in en keert u terug.

Zodra de levering is begonnen, is er geen verandering in **[!UICONTROL Success]** percentage wanneer het bericht met succes van Campagne aan Verbeterde MTA wordt afgelost.

<!--![](assets/efs-sending.png)-->

De leveringslogboeken tonen de status **[!UICONTROL Taken into account by the service provider]** voor elk gericht adres.

<!--![](assets/efs-pending.png)-->

Wanneer het bericht eigenlijk aan de gerichte profielen wordt geleverd en zodra deze informatie in echt - tijd van Verbeterde MTA wordt gemeld, tonen de leveringslogboeken de status **[!UICONTROL Sent]** voor elk adres dat met succes het bericht ontving. Het percentage **[!UICONTROL Success]** wordt dienovereenkomstig verhoogd bij elke succesvolle levering.

Wanneer hard-stuiterende berichten van Verbeterde MTA worden gemeld, verandert hun logboekstatus van **[!UICONTROL Taken into account by the service provider]** in **[!UICONTROL Failed]**<!-- and the **[!UICONTROL Bounces + errors]** percentage is increased accordingly-->.

Wanneer de zachte die berichten terug van Verbeterde MTA worden gemeld, blijft hun logboekstatus onveranderd (**[!UICONTROL Taken into account by the service provider]**): alleen de [error reason](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons) wordt bijgewerkt<!-- and the **[!UICONTROL Bounces + errors]** percentage is increased accordingly-->. Het percentage **[!UICONTROL Success]** blijft ongewijzigd. Zachte berichten worden dan opnieuw geprobeerd door de levering [geldigheidsperiode](../../delivery/using/steps-sending-the-delivery.md#defining-validity-period):

* Als een nieuwe poging vóór het eind van de geldigheidsperiode succesvol is, verandert de berichtstatus in **[!UICONTROL Sent]** en **[!UICONTROL Success]** percentage wordt dienovereenkomstig verhoogd.

* Anders verandert de status in **[!UICONTROL Failed]**. Het **[!UICONTROL Success]** <!--and **[!UICONTROL Bounces + errors]** -->percentage blijft ongewijzigd.

>[!NOTE]
>
>Zie [deze sectie](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons) voor meer informatie over harde en zachte grenzen.
>
>Zie [deze sectie](../../delivery/using/understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure) voor meer informatie over pogingen na een tijdelijke leveringsfout.


De lijsten hieronder tonen de veranderingen in KPIs en het verzenden van logboekstatussen die door het vermogen EFS worden geïntroduceerd.

**Met e-mailfeedbackservice**

| Stap in het verzendende proces | KPI-overzicht | Status van logboeken verzenden |
|--- |--- |--- |
| Het bericht wordt met succes afgelost van Campagne aan Verbeterde MTA | **[!UICONTROL Success]** percentage wordt niet weergegeven (begint bij 0%) | Door de dienstverlener in aanmerking genomen |
| Fel-stuiterende berichten worden gemeld terug van Verbeterde MTA | Geen wijziging in **[!UICONTROL Success]** percentage | Mislukt |
| De zachte die berichten bewegen worden gemeld terug van Verbeterde MTA | Geen wijziging in **[!UICONTROL Success]** percentage | Door de dienstverlener in aanmerking genomen |
| Opnieuw proberen van zachte berichten is geslaagd | **[!UICONTROL Success]** percentage dienovereenkomstig verhoogd | Verzonden |
| Opnieuw proberen van zachte berichten mislukt | Geen wijziging in **[!UICONTROL Success]** percentage | Mislukt |

**Zonder e-mailfeedbackservice**

| Stap in het verzendende proces | KPI-overzicht | Status van logboeken verzenden |
|--- |--- |--- |
| Het bericht wordt met succes afgelost van Campagne aan Verbeterde MTA | **[!UICONTROL Success]** percentage begint bij 100% | Verzonden |
| Fel-stuiterende berichten worden gemeld terug van Verbeterde MTA | **[!UICONTROL Success]** percentage wordt dienovereenkomstig verlaagd | Mislukt |
| De zachte die berichten bewegen worden gemeld terug van Verbeterde MTA | Geen wijziging in **[!UICONTROL Success]** percentage | Verzonden |
| Opnieuw proberen van zachte berichten is geslaagd | Geen wijziging in **[!UICONTROL Success]** percentage | Verzonden | **[!UICONTROL Success]** percentage dienovereenkomstig verhoogd | Verzonden |
| Opnieuw proberen van zachte berichten mislukt | **[!UICONTROL Success]** percentage wordt dienovereenkomstig verlaagd | Mislukt |
