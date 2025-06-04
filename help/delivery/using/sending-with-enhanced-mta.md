---
product: campaign
title: Verzenden met de verbeterde MTA in Adobe Campaign Classic
description: Meer informatie over de reikwijdte en de specifieke kenmerken van het verzenden van e-mails met de Adobe Campaign Enhanced MTA
feature: Email
role: User, Admin, Developer
exl-id: 58cc23f4-9ab0-45c7-9aa2-b08487ec7e91
source-git-commit: b353b562bd2f0b0bd2dfde22c6477ab66d499483
workflow-type: tm+mt
source-wordcount: '1368'
ht-degree: 0%

---

# Verzenden met de verbeterde MTA {#sending-with-enhanced-mta}

**Adobe Campaign Verbeterde MTA** (de Agent van de Overdracht van de Post) verstrekt een bevorderen verzendende infrastructuur die voor betere leverbaarheid, reputatie, productie, rapportering, stuitbehandeling, IP opwaartse en verbinding plaatsend beheer toestaat.

Het is geïmplementeerd om de schaalbaarheid te verbeteren, de doorvoer van de levering te verhogen en meer e-mails sneller te verzenden. Dit wordt bereikt met nieuwe adaptieve leveringstechnieken die e-mailverzendende montages in real time veranderen gebaseerd op terugkoppelen van de Dienstverleners van Internet.

>[!IMPORTANT]
>
>De Adobe Campaign Enhanced MTA is alleen beschikbaar voor door Campaign Classic gehoste of hybride klanten. Campaign Classic on-premise installaties kunnen niet worden geüpgraded om de Enhanced MTA te gebruiken.

Als u na september 2018 een Campaign Classic-instantie hebt ingericht, gebruikt u de Enhanced MTA. Voor alle andere klanten van Campaign Classic, zie [ vaak gestelde vragen ](#enhanced-mta-faq) hieronder.

De verbeterde implementatie MTA kan enkele bestaande functionaliteit van de Campagne beïnvloeden. Voor meer op dit, zie de [ Verbeterde specialiteiten MTA ](#enhanced-mta-impacts).

>[!NOTE]
>
>Als u een eindgebruiker van Adobe Campaign bent en u wilt weten of uw instantie aan Verbeterde MTA is bevorderd, contacteer uw interne beheerder van de Campagne.

## Veelgestelde vragen {#enhanced-mta-faq}

### Gebruik en voordelen

**wat is Verbeterde MTA?**

Adobe Campaign kan nu worden bevorderd om een nieuwe MTA (de Agent van de Overdracht van de Post) te gebruiken die commerciële e-mail MTA van SparkPost genoemd **Momentum** in werking stelt.

Momentum vertegenwoordigt innovatieve, krachtige MTA-technologie, die slimmere stuiterende behandeling en een geautomatiseerde optimaliseringscapaciteit van de leverbaarheid omvat die afzenders helpt optimale inbusleversnelheden te bereiken en te handhaven. <!--More than 37% of the world's business email is sent using SparkPost's MTA technology.-->

**wat zijn de voordelen?**

* De cliënten van Adobe Campaign die Verbeterde MTA gebruiken hebben a <!--300%--> enorme verhoging van algemene productiesnelheid gezien, en a <!--90%+--> significante vermindering van zachte grenzen.
* De verbeterde MTA gebruikt de recentste technologie MTA om u van de optimale productiesnelheden voor uw e-maillevering te voorzien.
* Door zich direct en automatisch aan te passen aan de feedback die het ontvangt, zorgt het er ook voor dat de e-mail nauwkeuriger en intelligenter wordt geleverd met realtime leveringsgegevens.

**kan ik inheemse Adobe Campaign MTA en Verbeterde MTA tezelfdertijd gebruiken?**

Nee. Alleen de verbeterde MTA kan worden gebruikt voor uw e-mailleveringen nadat uw exemplaar is bijgewerkt.

<!--
**Is there a fee associated with upgrading my instance to and subsequent use of the Enhanced MTA?**
No, there is no extra fee associated with the upgrade process to enable the use of the Enhanced MTA.

**When will the Enhanced MTA be available to me?**

* If you are new to Adobe Campaign Classic, you are already using the Enhanced MTA.

* For Adobe Campaign Classic existing customers, we've implemented a phased rollout that covers all hosted or partially hosted (hybrid) instances. If you're not already using it, we'll be contacting you in the near future with the dates and details for upgrading your Adobe Campaign Classic instances to the Enhanced MTA.
-->

### Verbetering van de verbeterde MTA

**wat wordt vereist om aan Verbeterde MTA te bevorderen?**

Als u na september 2018 een Campaign Classic-instantie hebt ingericht, is geen actie vereist omdat u de Enhanced MTA al gebruikt.

Voor alle andere gehoste of gedeeltelijk gehoste (hybride) klanten bereikt het Adobe Campaign-team een datum voor de migratie en geeft het details over de juiste stappen die nodig zijn voor de migratie.

>[!IMPORTANT]
>
>De verbeterde MTA is niet beschikbaar voor installaties op locatie.

**wat is het proces om mijn instantie aan Verbeterde MTA te bevorderen?**

Het gehele proces voor de gehoste exemplaren vereist een paar minuten downtime. Adobe controleert tot 24 uur na de upgrade de e-maildoorvoer en de leveringsmogelijkheden om de gevolgen voor uw e-mailleveringen te beoordelen.

Als er problemen worden ontdekt, kan Adobe uw exemplaar snel en tijdelijk terugzetten naar de native Adobe Campaign MTA.

Momenteel heeft de verbeterde MTA alleen invloed op het e-mailkanaal. Uw pushberichten en SMS-leveringen blijven gebruikmaken van de native Campagne MTA en worden op geen enkele wijze beïnvloed door de upgrade.

**moet ik opnieuw door IP opwarmen na bevordering aan Verbeterde MTA gaan?**

Nee. De bevordering vereist geen omschakeling aan nieuwe IPs, zodat kunt u blijven gebruikend uw bestaande, verwarmde e-mailIPs.

**zal bevordering aan de Verbeterde invloed MTA om het even welke campagnes of leveringen momenteel lopend?**

Voor klanten die de functionaliteit van het de transactieoverseinen van Adobe Campaign gebruiken, zullen om het even welke API vraag om een e-mail teweeg te brengen tijdens de zeer korte verbeteringsonderbreking in de rij worden geplaatst en zullen na voltooiing van de verbetering worden geprobeerd.

## Verbeterde specifieke kenmerken van MTA {#enhanced-mta-impacts}

### Nieuwe MX-regels

De MX regels van de het beheersleveringsproductie worden niet meer gebruikt. Verbeterde MTA heeft zijn eigen MX regels die het toestaan om uw productie door domein aan te passen die op uw eigen historische e-mailreputatie wordt gebaseerd, en op real time terugkoppelen die uit de domeinen komt waar u e-mails verzendt.

Voor meer op MX configuratie, zie [ deze sectie ](../../installation/using/email-deliverability.md#mx-configuration).

### Stuitkwalificatie

De stuitkwalificaties in de lijst van de Campagne **[!UICONTROL Delivery log qualification]** worden niet meer gebruikt voor **synchrone** de foutenmeldingen van de leveringsmislukking. Verbeterde MTA bepaalt het stuittype en de kwalificatie, en stuurt die informatie terug naar Campagne.

>[!NOTE]
>
>Verbeterde MTA kwalificeert de stuit SMTP en verzendt die kwalificatie terug naar Campagne in de vorm van een stuitercode die aan een de stuiteringsreden en kwalificatie van de Campagne in kaart wordt gebracht.

Voor meer bij stuitkwalificatie, zie [ deze sectie ](understanding-delivery-failures.md#bounce-mail-qualification).

### Levering

Een levering kan niet worden gestopt wanneer deze is overgebracht naar de verbeterde MTA, ook al wordt deze weergegeven met de status **[!UICONTROL Stopped]** in Campagne.

### Leveringsdoorvoer

De grafiek van de productie van de Levering van de Campagne zal niet meer de productie aan uw e-mailontvangers tonen. Die grafiek zal nu de productiesnelheid voor het relais van uw berichten van Campaign over aan Verbeterde MTA tonen.

Voor meer op de leveringsproductie, zie [ deze sectie ](../../reporting/using/global-reports.md#delivery-throughput).

### Opnieuw

De instellingen voor Opnieuw proberen in de levering worden niet meer gebruikt door de campagne. De zachte stuitpogingen en de tijdsduur tussen hen worden bepaald door Verbeterde MTA gebaseerd op het type en de strengheid van de stuiteringsreacties die van het e-maildomein van het bericht terugkomen.

Voor meer op pogingen, zie [ deze sectie ](steps-sending-the-delivery.md#configuring-retries).

### Geldigheidsperiode

De geldigheidsperiode die in uw levering van de Campagne plaatst zal door Verbeterde MTA slechts worden gebruikt als reeks aan **3.5 dagen of minder**. Als u in Campagne een waarde definieert die hoger is dan 3,5 dagen, wordt hiermee geen rekening gehouden.

Bijvoorbeeld, als de geldigheidsperiode aan de standaardwaarde van 5 dagen in Campagne wordt geplaatst, zullen de zachte-stuiterende berichten in de Verbeterde MTA hertry rij gaan en slechts 3.5 dagen worden opnieuw geprobeerd vanaf toen dat bericht Verbeterde MTA bereikte. In dat geval wordt de waarde die is ingesteld in Campaign niet gebruikt.

Zodra een bericht 3.5 dagen in de Verbeterde MTA rij is geweest en niet heeft geleverd, zal het uit tijd en zijn status van **[!UICONTROL Sent]** aan **[!UICONTROL Failed]** in de leveringslogboeken worden bijgewerkt.

Voor meer op de geldigheidsperiode, zie [ deze sectie ](steps-sending-the-delivery.md#defining-validity-period).

### DKIM-ondertekening

Ondertekening van de DKIM-e-mailverificatie (DomainKeys Identified Mail) wordt uitgevoerd door de Enhanced MTA. DKIM-signing door de native Campagne MTA zal worden uitgezet binnen de beheerlijst van het Domein als deel van de Verbeterde verbetering MTA.
Voor meer op DKIM, zie de [ Gids van de Beste praktijken van de Levering van Adobe ](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html?lang=nl-NL#authentication).

### Leveringssuccesrapportage

In de **[!UICONTROL Summary]** mening van een e-maillevering [ dashboard ](delivery-dashboard.md), begint het **[!UICONTROL Success]** percentage bij 100% en gaat dan progressief door de levering [ geldigheidsperiode ](steps-sending-the-delivery.md#defining-validity-period), aangezien de zachte en harde grenzen terug van Verbeterde MTA aan Campagne worden gemeld.

Sterker nog, tonen alle berichten als **[!UICONTROL Sent]** in [ verzendend logboeken ](delivery-dashboard.md#delivery-logs-and-history) zodra zij met succes van Campagne aan Verbeterde MTA worden afgelost. Zij blijven in die status tenzij of tot a [ stuiteren ](understanding-delivery-failures.md#delivery-failure-types-and-reasons) voor dat bericht terug van Verbeterde MTA aan Campagne wordt meegedeeld.

Wanneer hard-bouncing berichten van Verbeterde MTA worden gemeld, verandert hun status van **[!UICONTROL Sent]** in **[!UICONTROL Failed]** en **[!UICONTROL Success]** percentage wordt dienovereenkomstig verminderd.

Wanneer soft-bouncing berichten terug van Verbeterde MTA worden gemeld, tonen zij nog steeds als **[!UICONTROL Sent]** en het **[!UICONTROL Success]** percentage wordt nog niet bijgewerkt. De soft-bouncing berichten worden dan [ opnieuw geprobeerd ](understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure) door de periode van de leveringsgeldigheid:

* Als het opnieuw proberen is gelukt vóór het einde van de geldigheidsperiode, blijft de status van het bericht behouden als **[!UICONTROL Sent]** en blijft het percentage **[!UICONTROL Success]** ongewijzigd.

* Anders verandert de status in **[!UICONTROL Failed]** en wordt het percentage **[!UICONTROL Success]** dienovereenkomstig verlaagd.

Daarom moet u wachten tot het einde van de geldigheidsperiode om het uiteindelijke percentage **[!UICONTROL Success]** en het uiteindelijke aantal berichten **[!UICONTROL Sent]** en **[!UICONTROL Failed]** weer te geven.

In de onderstaande tabel staan de verschillende stappen in het verzendingsproces met de overeenkomende KPI&#39;s en het verzenden van logbestanden.

| Stap in het verzendende proces | KPI-overzicht | Status van logboeken verzenden |
|--- |--- |--- |
| Het bericht wordt met succes afgelost van Campagne aan Verbeterde MTA | **[!UICONTROL Success]** percentage begint bij 100% | Verzonden |
| Fel-stuiterende berichten worden gemeld terug van Verbeterde MTA | **[!UICONTROL Success]** percentage is dienovereenkomstig verlaagd | Mislukt |
| De zachte die berichten bewegen worden gemeld terug van Verbeterde MTA | Geen wijziging in **[!UICONTROL Success]** percentage | Verzonden |
| Herhalingen van soft-bouncing berichten zijn succesvol | Geen wijziging in **[!UICONTROL Success]** percentage | Verzonden | **[!UICONTROL Success]** percentage wordt dienovereenkomstig verhoogd | Verzonden |
| Herhalingen van soft-bouncing berichten mislukken | **[!UICONTROL Success]** percentage is dienovereenkomstig verlaagd | Mislukt |

