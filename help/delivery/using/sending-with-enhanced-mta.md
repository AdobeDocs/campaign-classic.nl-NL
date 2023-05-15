---
product: campaign
title: S met de verbeterde MTA in Adobe Campaign Classic
description: Meer informatie over de reikwijdte en de specifieke kenmerken van het verzenden van e-mails met de Adobe Campaign Enhanced MTA
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Email
exl-id: 58cc23f4-9ab0-45c7-9aa2-b08487ec7e91
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '1999'
ht-degree: 3%

---

# Verzenden met de Enhanced MTA {#sending-with-enhanced-mta}



De **Adobe Campaign Enhanced MTA** (De Agent van de Overdracht van de Post) verstrekt een bevorderde verzendende infrastructuur die voor betere levering, reputatie, productie, rapportering, stuitbehandeling, IP oprijplaat en verbinding het plaatsen beheer toestaat.

Het is geïmplementeerd om de schaalbaarheid te verbeteren, de doorvoer van de levering te verhogen en meer e-mails sneller te verzenden. Dit wordt bereikt met nieuwe adaptieve leveringstechnieken die e-mailverzendende montages in real time veranderen gebaseerd op terugkoppelen van de Dienstverleners van Internet.

>[!IMPORTANT]
>
>De Adobe Campaign Enhanced MTA is alleen beschikbaar voor door Campaign Classic gehoste of hybride klanten. Campaign Classic-installaties op locatie kunnen niet worden bijgewerkt om de verbeterde MTA te gebruiken.

Als u een instantie van de Campaign Classic na September 2018 provisioned was, gebruikt u Verbeterde MTA. Voor alle andere klanten van Campaign Classic, zie [Veelgestelde vragen](#enhanced-mta-faq) hieronder.

De verbeterde implementatie MTA kan enkele bestaande functionaliteit van de Campagne beïnvloeden. Zie voor meer informatie de [Verbeterde specifieke kenmerken van MTA](#enhanced-mta-impacts).

>[!NOTE]
>
>Als u een eindgebruiker van Adobe Campaign bent en u wilt weten of uw instantie aan Verbeterde MTA is bevorderd, contacteer uw interne beheerder van de Campagne.

## Veelgestelde vragen {#enhanced-mta-faq}

### Gebruik en voordelen

**Wat is de verbeterde MTA?**

Adobe Campaign kan nu worden geüpgraded om een nieuwe MTA (Mail Transfer Agent) te gebruiken die de commerciële e-mail MTA van SparkPost met de naam **Momentum**.

Momentum vertegenwoordigt innovatieve, krachtige MTA-technologie, die slimmere stuiterende behandeling en een geautomatiseerde optimaliseringscapaciteit van de leverbaarheid omvat die afzenders helpt optimale inbusleversnelheden te bereiken en te handhaven. <!--More than 37% of the world's business email is sent using SparkPost's MTA technology.-->

**Wat zijn de voordelen?**

* Adobe Campaign-clients die gebruikmaken van de Enhanced MTA hebben een <!--300%-->een enorme toename van de totale doorvoersnelheid en een <!--90%+-->aanzienlijke vermindering van zachte grenzen.
* De verbeterde MTA gebruikt de recentste technologie MTA om u van de optimale productiesnelheden voor uw e-maillevering te voorzien.
* Door zich direct en automatisch aan te passen aan de feedback die het ontvangt, zorgt het er ook voor dat de e-mail nauwkeuriger en intelligenter wordt geleverd met realtime leveringsgegevens.

**Kan ik tegelijkertijd de native Adobe Campaign MTA en de Enhanced MTA gebruiken?**

Nee. Alleen de verbeterde MTA kan worden gebruikt voor uw e-mailleveringen nadat uw exemplaar is bijgewerkt.

<!--
**Is there a fee associated with upgrading my instance to and subsequent use of the Enhanced MTA?**
No, there is no extra fee associated with the upgrade process to enable the use of the Enhanced MTA.

**When will the Enhanced MTA be available to me?**

* If you are new to Adobe Campaign Classic, you are already using the Enhanced MTA.

* For Adobe Campaign Classic existing customers, we've implemented a phased rollout that covers all hosted or partially hosted (hybrid) instances. If you're not already using it, we'll be contacting you in the near future with the dates and details for upgrading your Adobe Campaign Classic instances to the Enhanced MTA.
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

## Verbeterde specifieke kenmerken van MTA {#enhanced-mta-impacts}

### Verbeterde MTA-headers

De recentste instanties van de Campaign Classic omvatten code die de vereiste Verbeterde kopballen MTA aan elk bericht toevoegt. Als u Adobe Campaign 19.1 (build 9032) of hoger gebruikt en als dit niet het geval is, moet u [Adobe Klantenservice](https://helpx.adobe.com/nl/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) om de parameter &quot;useMomentum=true&quot; toe te voegen aan de configuratie van de uitvoeringsinstantie (in het gedeelte [serverConf.xml](../../installation/using/the-server-configuration-file.md#mta) bestand), wat uw marketingexemplaar kan zijn, [mid-sourcing-instantie](../../installation/using/mid-sourcing-server.md), of [instantie voor het uitvoeren van transactieberichten](../../message-center/using/configuring-instances.md#execution-instance), afhankelijk van uw configuratie.

Als u echter een oudere instantie gebruikt die deze code niet bevat, wordt een nieuwe typologieregel met de naam **[!UICONTROL Typology Rule for Enhanced MTAs]** moet worden toegevoegd aan alle bestaande typologieën in uw instantie van de Campagne.
Deze regel wordt toegevoegd door een **[!UICONTROL Typology]** pakket geïnstalleerd als deel van de verbetering aan Verbeterde MTA.

>[!IMPORTANT]
>
>Als u deze typologieregel in uw typologieën ziet, schrap of wijzig het op geen enkele manier. Anders kunnen de e-mailleveringen nadelig worden beïnvloed.

Dit **[!UICONTROL Typology]** -pakket moet worden geïnstalleerd op het marketingexemplaar van Adobe Campaign.

Als u een hybride client bent, geeft het Adobe Campaign-team u instructies over het installeren van de **[!UICONTROL Typology]** pakket op uw marketing instantie als deel van de verbetering aan Verbeterde MTA. Neem contact op met uw accountmanager voor de volledige instructies.

>[!IMPORTANT]
>
>Instructies van het Adobe Campaign-team over het installeren van de **[!UICONTROL Typology]** De verpakking dient zorgvuldig gevolgd te worden. Anders kunnen er grote problemen optreden met uw IP&#39;s die worden gebruikt om e-mails te verzenden.

Voor meer over typologieën, zie [deze sectie](../../campaign-opt/using/about-campaign-typologies.md).

### Nieuwe MX-regels

De MX regels van de het beheersleveringsproductie worden niet meer gebruikt. Verbeterde MTA heeft zijn eigen MX regels die het toestaan om uw productie door domein aan te passen die op uw eigen historische e-mailreputatie wordt gebaseerd, en op real time terugkoppelen die uit de domeinen komt waar u e-mails verzendt.

Voor meer op MX configuratie, zie [deze sectie](../../installation/using/email-deliverability.md#mx-configuration).

### Stuitkwalificatie

De stuitende kwalificaties in de campagne **[!UICONTROL Delivery log qualification]** tabel wordt niet meer gebruikt voor **synchroon** foutberichten over leveringsfout. Verbeterde MTA bepaalt het stuittype en de kwalificatie, en stuurt die informatie terug naar Campagne.

>[!NOTE]
>
>Verbeterde MTA kwalificeert de stuit SMTP en verzendt die kwalificatie terug naar Campagne in de vorm van een stuitercode die aan een de stuiteringsreden en kwalificatie van de Campagne in kaart wordt gebracht.

Zie voor meer informatie over stuiteren [deze sectie](understanding-delivery-failures.md#bounce-mail-qualification).

### Leveringsdoorvoer

De grafiek van de productie van de Levering van de Campagne zal niet meer de productie aan uw e-mailontvangers tonen. Die grafiek zal nu de productiesnelheid voor het relais van uw berichten van Campaign over aan Verbeterde MTA tonen.

Voor meer op de leveringsproductie, zie [deze sectie](../../reporting/using/global-reports.md#delivery-throughput).

>[!NOTE]
>
>Met de [E-mailfeedbackservice](#email-feedback-service) (EFS) capaciteit (momenteel beschikbaar als bèta), toont de grafiek van de productie van de Levering van de Campagne nog de productie aan uw e-mailontvangers.

### Hernieuwde pogingen

De instellingen voor Opnieuw proberen in de levering worden niet meer gebruikt door de campagne. De zachte stuitpogingen en de tijdsduur tussen hen worden bepaald door Verbeterde MTA gebaseerd op het type en de strengheid van de stuiteringsreacties die van het e-maildomein van het bericht terugkomen.

Voor meer informatie over pogingen raadpleegt u [deze sectie](steps-sending-the-delivery.md#configuring-retries).

### Geldigheidsperiode

De geldigheidsperiode die in uw campagneleveringen wordt ingesteld, wordt alleen door de verbeterde MTA gebruikt als deze is ingesteld op **3,5 dagen of minder**. Als u in Campagne een waarde definieert die hoger is dan 3,5 dagen, wordt hiermee geen rekening gehouden.

Bijvoorbeeld, als de geldigheidsperiode aan de standaardwaarde van 5 dagen in Campagne wordt geplaatst, zullen de zachte-stuiterende berichten in de Verbeterde MTA hertry rij gaan en slechts 3.5 dagen worden opnieuw geprobeerd vanaf toen dat bericht Verbeterde MTA bereikte. In dat geval wordt de waarde die is ingesteld in Campaign niet gebruikt.

Wanneer een bericht gedurende 3,5 dagen in de wachtrij van de Enhanced MTA heeft gestaan en niet is geleverd, treedt er een time-out op en zal de status van het bericht worden bijgewerkt van **[!UICONTROL Sent]** naar **[!UICONTROL Failed]** in de leveringslogboeken.

Voor meer informatie over de geldigheidsperiode raadpleegt u [deze sectie](steps-sending-the-delivery.md#defining-validity-period).

### DKIM-ondertekening

DKIM (DomainKeys Identified Mail) e-mailverificatie wordt ondertekend door de Enhanced MTA. DKIM-signing door de native Campagne MTA zal worden uitgezet binnen de beheerlijst van het Domein als deel van de Verbeterde verbetering MTA.
Voor meer informatie over DKIM raadpleegt u de [Adobe Handleiding voor beste praktijken voor aflevering](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#authentication).

### Leveringssuccesrapportage

In de **[!UICONTROL Summary]** weergave van een e-maillevering [dashboard](delivery-dashboard.md)de **[!UICONTROL Success]** het percentage begint bij 100% en daalt geleidelijk gedurende de hele levering. [geldigheidsperiode](steps-sending-the-delivery.md#defining-validity-period), terwijl de zachte en harde grenzen worden gemeld van de Enhanced MTA naar Campaign.

Alle berichten worden zelfs als **[!UICONTROL Sent]** in de [verzenden, logbestanden](delivery-dashboard.md#delivery-logs-and-history) zodra zij met succes van Campaign aan de Verbeterde MTA worden opnieuw aangeboden. Zij blijven deze status behouden, tenzij of totdat [stuiten](understanding-delivery-failures.md#delivery-failure-types-and-reasons) voor dat bericht wordt meegedeeld terug van Verbeterde MTA aan Campaign.

Wanneer hard-stuiterende berichten van Verbeterde MTA worden gemeld, verandert hun status van **[!UICONTROL Sent]** tot **[!UICONTROL Failed]** en de **[!UICONTROL Success]** het percentage wordt dienovereenkomstig verlaagd.

Wanneer de zachte die berichten terug van Verbeterde MTA worden gemeld, tonen zij nog **[!UICONTROL Sent]** en de **[!UICONTROL Success]** percentage is nog niet bijgewerkt. De zachte die berichten van het stuiteren zijn dan [opnieuw](understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure) gedurende de gehele geldigheidsduur van de levering:

* Als een nieuwe poging voor het eind van de geldigheidsperiode succesvol is, blijft de berichtstatus zoals **[!UICONTROL Sent]** en de **[!UICONTROL Success]** percentage blijft ongewijzigd.

* Anders verandert de status in **[!UICONTROL Failed]** en de **[!UICONTROL Success]** het percentage wordt dienovereenkomstig verlaagd.

Daarom moet u tot het einde van de geldigheidsperiode wachten om de definitieve **[!UICONTROL Success]** percentage en het uiteindelijke aantal **[!UICONTROL Sent]** en **[!UICONTROL Failed]** berichten.

<!--The fact that the Success percentage will go to 100% very quickly indicates that your instance has been upgraded to the Enhanced MTA.-->

### E-mailfeedbackservice (bèta) {#email-feedback-service}

Met de e-mailfeedbackservice (EFS) wordt de status van elke e-mail correct gerapporteerd, omdat feedback rechtstreeks wordt vastgelegd via de Enhanced MTA (Message Transfer Agent).

>[!IMPORTANT]
>
>De e-mailfeedbackservice is momenteel beschikbaar als bètafunctie.
>
>Vul het veld in als u geïnteresseerd bent in deelname aan dit bètaprogramma. [dit formulier](https://forms.office.com/Pages/ResponsePage.aspx?id=Wht7-jR7h0OUrtLBeN7O4Rol2vQGupxItW9_BerXV6VUQTJPN1Q5WUI4OFNTWkYzQjg3WllUSDAxWi4u) en we komen terug bij je .

Wanneer de levering is gestart, is er geen wijziging in de **[!UICONTROL Success]** percentage wanneer het bericht met succes van Campagne aan Verbeterde MTA wordt afgelost.

<!--![](assets/efs-sending.png)-->

De leveringslogboeken tonen de **[!UICONTROL Taken into account by the service provider]** status voor elk gericht adres.

<!--![](assets/efs-pending.png)-->

Wanneer het bericht werkelijk aan de gerichte profielen wordt geleverd en zodra deze informatie in echt - tijd van Verbeterde MTA wordt gemeld, tonen de leveringslogboeken **[!UICONTROL Sent]** status voor elk adres dat met succes het bericht ontving. De **[!UICONTROL Success]** het percentage wordt dienovereenkomstig verhoogd bij elke succesvolle levering.

Wanneer hard-bouncing berichten terug van Verbeterde MTA worden gemeld, verandert hun logboekstatus van **[!UICONTROL Taken into account by the service provider]** tot **[!UICONTROL Failed]**<!-- and the **[!UICONTROL Bounces + errors]** percentage is increased accordingly-->.

Wanneer de zachte die berichten terug van Verbeterde MTA worden gemeld, blijft hun logboekstatus onveranderd (**[!UICONTROL Taken into account by the service provider]**): alleen [oorzaak van fout](understanding-delivery-failures.md#delivery-failure-types-and-reasons) is bijgewerkt<!-- and the **[!UICONTROL Bounces + errors]** percentage is increased accordingly-->. De **[!UICONTROL Success]** percentage blijft ongewijzigd. De zachte die berichten bewegen worden dan opnieuw geprobeerd door de levering [geldigheidsperiode](steps-sending-the-delivery.md#defining-validity-period):

* Als een nieuwe poging is gelukt vóór het einde van de geldigheidsperiode, verandert de berichtstatus in **[!UICONTROL Sent]** en de **[!UICONTROL Success]** het percentage wordt dienovereenkomstig verhoogd.

* Anders verandert de status in **[!UICONTROL Failed]**. De **[!UICONTROL Success]** <!--and **[!UICONTROL Bounces + errors]** -->percentage blijft ongewijzigd.

>[!NOTE]
>
>Zie voor meer informatie over harde en zachte golven [deze sectie](understanding-delivery-failures.md#delivery-failure-types-and-reasons).
>
>Voor meer informatie over pogingen na een tijdelijke mislukking van de levering, zie [deze sectie](understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure).


De lijsten hieronder tonen de veranderingen in KPIs en het verzenden van logboekstatussen die door het vermogen EFS worden geïntroduceerd.

**Met e-mailfeedbackservice**

| Stap in het verzendende proces | KPI-overzicht | Status van logboeken verzenden |
|--- |--- |--- |
| Het bericht wordt met succes afgelost van Campagne aan Verbeterde MTA | **[!UICONTROL Success]** percentage wordt niet weergegeven (begint bij 0%) | Door de dienstverlener in aanmerking genomen |
| Fel-stuiterende berichten worden gemeld terug van Verbeterde MTA | Geen wijziging in **[!UICONTROL Success]** percentage | Mislukt |
| De zachte die berichten bewegen worden gemeld terug van Verbeterde MTA | Geen wijziging in **[!UICONTROL Success]** percentage | Door de dienstverlener in aanmerking genomen |
| Opnieuw proberen van zachte berichten is geslaagd | **[!UICONTROL Success]** percentage dienovereenkomstig verhoogd | Verzonden |
| Opnieuw proberen van zachte berichten mislukt | Geen wijziging in **[!UICONTROL Success]** percentage | Mislukt |

**Zonder e-mailfeedbackservice**

| Stap in het verzendende proces | KPI-overzicht | Status van logboeken verzenden |
|--- |--- |--- |
| Het bericht wordt met succes afgelost van Campagne aan Verbeterde MTA | **[!UICONTROL Success]** percentage begint bij 100% | Verzonden |
| Fel-stuiterende berichten worden gemeld terug van Verbeterde MTA | **[!UICONTROL Success]** percentage wordt dienovereenkomstig verlaagd | Mislukt |
| De zachte die berichten bewegen worden gemeld terug van Verbeterde MTA | Geen wijziging in **[!UICONTROL Success]** percentage | Verzonden |
| Opnieuw proberen van zachte berichten is geslaagd | Geen wijziging in **[!UICONTROL Success]** percentage | Verzonden | **[!UICONTROL Success]** percentage dienovereenkomstig verhoogd | Verzonden |
| Opnieuw proberen van zachte berichten mislukt | **[!UICONTROL Success]** percentage wordt dienovereenkomstig verlaagd | Mislukt |
