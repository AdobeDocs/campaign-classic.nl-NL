---
title: Werken met quarantainebeheer
seo-title: Werken met quarantainebeheer
description: Werken met quarantainebeheer
seo-description: null
page-status-flag: never-activated
uuid: 9421e26c-bdcc-4588-8e44-fa6f31051081
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
discoiquuid: 56cbf48a-eb32-4617-8f80-efbfd05976ea
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 527d2dd2296d18c8ca26745b9f87d65c6fdf480a

---


# Werken met quarantainebeheer{#understanding-quarantine-management}

## Informatie over quarantines {#about-quarantines}

Adobe Campaign beheert een lijst met in quarantaine geplaatste adressen. Ontvangers van wie adres in quarantaine is geplaatst worden door gebrek tijdens leveringsanalyse uitgesloten, en zullen niet worden gericht. Een e-mailadres kan in quarantaine worden geplaatst, bijvoorbeeld, wanneer de brievenbus volledig is of als het adres niet bestaat. In elk geval voldoet de quarantaineprocedure aan de hieronder beschreven specifieke voorschriften.

>[!NOTE]
>
>Deze sectie is van toepassing op online kanalen: e-mail, SMS, pushmelding.

### De levering optimaliseren via quarantines {#optimizing-your-delivery-through-quarantines}

De profielen waarvan e-mailadressen of telefoonaantal in quarantaine zijn worden automatisch uitgesloten tijdens berichtvoorbereiding (zie het [identificeren van quarantined adressen voor een levering](#identifying-quarantined-addresses-for-a-delivery)). Dit zal leveranties versnellen, aangezien het foutenpercentage een significant effect op leveringssnelheid heeft.

Sommige internetproviders beschouwen e-mails automatisch als spam als de snelheid van ongeldige adressen te hoog is. Met quarantaine kunt u dus voorkomen dat deze providers op zwarte lijsten worden gezet.

Bovendien helpen quarantines de verzendkosten van SMS te verminderen door onjuiste telefoonaantallen van leveringen uit te sluiten. Raadpleeg [deze pagina](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliveryBestPractices.html)voor meer informatie over tips en trucs voor het beveiligen en optimaliseren van leveringen.

### Quarantine versus zwarte lijst {#quarantine-vs-blacklisting}

**Quarantaine** is alleen van toepassing op een adres, niet op het profiel zelf. Dit betekent dat twee profielen met hetzelfde e-mailadres worden beïnvloed als het adres in quarantaine wordt geplaatst.

Op dezelfde manier kan een profiel waarvan het e-mailadres in quarantaine is geplaatst, zijn profiel bijwerken en een nieuw adres invoeren. Dit profiel kan vervolgens opnieuw worden geactiveerd door leveringsacties.

**Wanneer je een abonnement** op een object verkoopt, wordt het profiel niet meer geactiveerd door levering, bijvoorbeeld na een abonnement (opt-out).

>[!NOTE]
>
>Wanneer een gebruiker op een SMS-bericht reageert met een trefwoord zoals &quot;STOP&quot; om zich af te melden voor SMS-leveringen, wordt dit profiel niet op de zwarte lijst weergegeven, zoals in het e-mailuitschakelproces. Het profieltelefoonnummer wordt naar quarantaine verzonden, zodat de gebruiker e-mailberichten blijft ontvangen.

## In quarantaine geplaatste adressen identificeren {#identifying-quarantined-addresses}

De gekwalificeerde adressen kunnen voor een specifieke levering of voor het volledige platform worden vermeld.

### Het identificeren van quarantined adressen voor een levering {#identifying-quarantined-addresses-for-a-delivery}

De gekwantificeerde adressen voor een specifieke levering zijn vermeld tijdens de leveringsvoorbereidingsfase, in de leveringslogboeken van het leveringsdashboard (zie [leveringslogboeken en geschiedenis](../../delivery/using/monitoring-a-delivery.md#delivery-logs-and-history)).

### Het identificeren van quarantined adressen voor het volledige platform {#identifying-quarantined-addresses-for-the-entire-platform}

De beheerders kunnen van de adressen in quarantaine voor het volledige platform van de **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]** knoop een lijst maken.

>[!NOTE]
>
>Dit menu bevat quarantaine-elementen voor **e-mail**-, **SMS** - en **pushberichtkanalen** .

Voor elk adres is de volgende informatie beschikbaar:

![](assets/tech_quarant_npai.png)

>[!NOTE]
>
>De toename van het aantal quarantines is een normaal effect dat gerelateerd is aan de &quot;slijtage&quot; van de database. Als de levensduur van een e-mailadres bijvoorbeeld wordt beschouwd als drie jaar en de tabel met ontvangers elk jaar met 50% toeneemt, kan de toename van quarantaine als volgt worden berekend:
>
>Einde van jaar 1: (1*0,33)/(1+0,5)=22%.
Einde van jaar 2: (1,22*0,33)+0,33)/(1,5+0,75)=32,5%.

### Het identificeren van quarantined adressen in leveringsrapporten {#identifying-quarantined-addresses-in-delivery-reports}

De volgende rapporten verstrekken informatie over de adressen in quarantaine:

* Voor elke levering, toont het **[!UICONTROL Delivery summary]** rapport het aantal adressen in quarantaine in het leveringsdoel. Het toont:

   * het aantal adressen dat tijdens de afleveringsanalyse in quarantaine wordt geplaatst;

   * Het aantal adressen die in quarantaine na de leveringsactie worden geplaatst.

* Het **[!UICONTROL Non-deliverables and bounces]** rapport bevat informatie over de adressen in quarantaine, de typen fouten die zijn aangetroffen, enz. en een uitsplitsing naar domein van fouten.

U kunt deze informatie opzoeken voor alle leveringen van het platform (**Startpagina>Rapporten**) of voor een specifieke levering. U kunt ook aangepaste rapporten maken en de informatie selecteren die moet worden weergegeven.

### Het identificeren van quarantined adressen voor een ontvanger {#identifying-quarantined-addresses-for-a-recipient}

U kunt de status van het e-mailadres van elke ontvanger opzoeken. Selecteer hiertoe het profiel van de ontvanger en klik op het **[!UICONTROL Deliveries]** tabblad. Voor alle leveringen aan die ontvanger, kunt u te weten komen of het ontbroken adres, tijdens analyse in quarantined, enz. was. Voor elke map kunt u alleen de ontvangers weergeven van wie het e-mailadres in quarantaine staat. Gebruik hiervoor het **[!UICONTROL Quarantined email address]** toepassingsfilter.

![](assets/tech_quarant_recipients_filter.png)

### Het verwijderen van een quarantined adres {#removing-a-quarantined-address}

Als u een adres uit quarantaine moet verwijderen, verander zijn status manueel in **[!UICONTROL Valid]**.

![](assets/tech_quarant_error_status.png)

Als u de status wijzigt in **[!UICONTROL Whitelisted]**, wordt het adres systematisch geactiveerd, zelfs als er een fout optreedt.

>[!CAUTION]
De adressen op de zwarte lijst worden niet betrokken bij het quarantainesysteem en zijn niet gericht, zelfs als u de status van het adres verandert.

U kunt ook het aantal fouten en de periode tussen fouten wijzigen. Hiervoor wijzigt u de instellingen van de implementatietovenaar (instellingen voor E-mailkanaal/Geavanceerd). Raadpleeg [deze sectie](../../installation/using/deploying-an-instance.md)voor meer informatie over de implementatietovenaar.

## Voorwaarden voor verzending van een adres naar quarantaine {#conditions-for-sending-an-address-to-quarantine}

Adobe Campagne beheert quarantaine volgens het type van leveringsmislukking en de reden die tijdens de kwalificatie van foutenmeldingen (zie de kwalificatie [van de post van de](../../delivery/using/understanding-delivery-failures.md#bounce-mail-qualification)Stuiteren) en de types en de redenen [van de](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons)Leveringsmislukking wordt toegewezen.

* **Genegeerde fout**: genegeerde fouten sturen geen adres naar quarantaine.
* **Harde fout**: het desbetreffende e-mailadres wordt onmiddellijk naar quarantaine verzonden.
* **Zachte fout**: de zachte fouten verzenden onmiddellijk geen adres naar quarantaine, maar zij verhogen een foutenteller. Zie [Foutenbeheer](#soft-error-management)voor meer informatie.

Als een gebruiker een e-mailbericht kwalificeert als een spam (**feedbacklus**), wordt het bericht automatisch doorgestuurd naar een technische mailbox die door Adobe wordt beheerd. Het e-mailadres van de gebruiker wordt vervolgens automatisch naar quarantaine verzonden.

In de lijst van quarantined adressen, wijst het **[!UICONTROL Error reason]** gebied erop waarom het geselecteerde adres in quarantaine werd geplaatst. Quarantaine in Adobe Campaign is hoofdlettergevoelig. Importeer e-mailadressen in kleine letters, zodat ze later niet opnieuw worden toegewezen.

![](assets/tech_quarant_error_reasons.png)

### Beheer van zachte fouten {#soft-error-management}

In tegenstelling tot harde fouten, verzenden de zachte fouten onmiddellijk geen adres naar quarantaine, maar zij verhogen in plaats daarvan een foutenteller.

* Wanneer de foutenteller de grensdrempel bereikt, dan gaat het adres in quarantaine.
* In de standaardconfiguratie is de drempel ingesteld op vijf fouten, waarbij twee fouten significant zijn als ze zich op een afstand van minstens 24 uur bevinden. Het adres wordt in quarantaine geplaatst bij de vijfde fout.
* De drempelwaarde voor de foutteller kan worden gewijzigd. Raadpleeg voor meer informatie [Retries na tijdelijke mislukking](../../delivery/using/understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure)van levering.

De foutenteller wordt opnieuw geïnitialiseerd als de laatste significante fout meer dan 10 dagen geleden voorkwam. De adresstatus verandert dan in **Geldig** en het wordt geschrapt van de lijst van quarantines door het de schoonmaakbeurt **van het** Gegevensbestand werkschema.

## Push notification quarantines {#push-notification-quarantines}

Het quarantainemechanisme voor pushmeldingen is over het algemeen hetzelfde als het algemene proces. Zie [Informatie over quarantines](#about-quarantines). Bepaalde fouten worden echter anders beheerd voor pushberichten. Voor bepaalde fouten in de software worden bijvoorbeeld geen pogingen opnieuw uitgevoerd binnen dezelfde levering. De specifieke kenmerken voor pushmeldingen worden hieronder weergegeven. Het mechanisme voor opnieuw proberen (aantal pogingen, frequentie) is hetzelfde als voor e-mailberichten.

De items die in quarantaine worden geplaatst, zijn apparaattokens.

### iOS-quarantaine {#ios-quarantine}

**Voor iOS - binaire connector**

Voor elk bericht ontvangt Adobe Campaign de synchrone en asynchrone fouten van de APNS-server. Voor de volgende synchrone fouten genereert Adobe Campaign zachte fouten:

* Problemen met de lengte van de lading: niet opnieuw proberen, de oorzaak van de fout is **[!UICONTROL Unreachable]**.
* Problemen met certificaatvervaldatum: niet opnieuw proberen, de oorzaak van de fout is **[!UICONTROL Unreachable]**.
* Verbinding verloren tijdens levering: opnieuw uitgevoerd, de reden van de fout is **[!UICONTROL Unreachable]**.
* Uitgave serviceconfiguratie (ongeldig certificaat, ongeldig certificaatwachtwoord, geen certificaat): niet opnieuw proberen, de oorzaak van de fout is **[!UICONTROL Unreachable]**.

De APNS-server waarschuwt Adobe Campaign asynchroon dat een apparaattoken niet is geregistreerd (wanneer de mobiele toepassing door de gebruiker is verwijderd). De **[!UICONTROL mobileAppOptOutMgt]** workflow wordt elke 6 uur uitgevoerd om contact op te nemen met de APNS-feedbackservices om de **AppSubscriptionRcp** -tabel bij te werken. Voor alle gedeactiveerde tokens, wordt het gebied **Uitgeschakeld** geplaatst aan **Waar** en het abonnement verbonden aan dat apparatenteken zal automatisch van toekomstige leveringen worden uitgesloten.

**Voor iOS - HTTP/2-connector**

Met het http/2-protocol kunt u rechtstreeks feedback geven en de status van elke push-levering bepalen. Als de HTTP/2 protocolschakelaar wordt gebruikt, koppelt de dienst niet meer door het **[!UICONTROL mobileAppOptOutMgt]** werkschema terug. De niet-geregistreerde tokens worden verschillend afgehandeld tussen de binaire iOS-connector en de iOS http/2-connector. Een token wordt als niet-geregistreerd beschouwd wanneer een mobiele toepassing wordt verwijderd of opnieuw wordt geïnstalleerd.

Als APNS synchroon een &quot;niet-geregistreerde&quot; status voor een bericht retourneert, wordt het doeltoken onmiddellijk in quarantaine geplaatst.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Scenario</strong><br /> </td> 
   <td> <strong>Status</strong><br /> </td> 
   <td> <strong>Foutbericht</strong><br /> </td> 
   <td> <strong>Type fout</strong><br /> </td> 
   <td> <strong>Mislukt</strong><br /> </td> 
   <td> <strong>Opnieuw</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Gericht apparaat ingeschakeld<br /> </td> 
   <td> OK<br /> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Gericht apparaat uitgeschakeld<br /> </td> 
   <td> OK<br /> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Gebruiker schakelt meldingen voor de toepassing uit<br /> </td> 
   <td> OK<br /> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Berichtontwerp/analysefase - lading te groot<br /> </td> 
   <td> Mislukt<br /> </td> 
   <td> Payload te lang<br /> </td> 
   <td> Zacht<br /> </td> 
   <td> Geweigerd<br /> </td> 
   <td> Nee<br /> </td> 
  </tr> 
  <tr> 
   <td> Berichtaanmaak/analysefase - onverwachte inhoudsopmaakkwestie<br /> </td> 
   <td> Mislukt<br /> </td> 
   <td> Verschillende foutberichten op basis van de fout<br /> </td> 
   <td> Zacht<br /> </td> 
   <td> Ongedefinieerd<br /> </td> 
   <td> Nee<br /> </td> 
  </tr> 
  <tr> 
   <td> Certificaatafgifte (wachtwoord, beschadiging, enz.) en de verbinding met APNS-probleem testen<br /> </td> 
   <td> Mislukt<br /> </td> 
   <td> Verschillende foutberichten op basis van de fout<br /> </td> 
   <td> Zacht<br /> </td> 
   <td> Geweigerd<br /> </td> 
   <td> Nee<br /> </td> 
  </tr> 
  <tr> 
   <td> Netwerkverbinding verloren tijdens verzenden<br /> </td> 
   <td> Mislukt<br /> </td> 
   <td> Verbindingsfout<br /> </td> 
   <td> Ongedefinieerd<br /> </td> 
   <td> Onbereikbaar<br /> </td> 
   <td> Ja<br /> </td> 
  </tr> 
  <tr> 
   <td> APNS-bericht afgewezen: De registratie<br /> ongedaan maken wanneer de gebruiker de toepassing heeft verwijderd of het token is verlopen<br /> </td> 
   <td> Mislukt<br /> </td> 
   <td> Niet geregistreerd<br /> </td> 
   <td> Hard<br /> </td> 
   <td> Gebruiker onbekend<br /> </td> 
   <td> Nee<br /> </td> 
  </tr> 
  <tr> 
   <td> APNS-bericht afgewezen: alle andere fouten<br /> </td> 
   <td> Mislukt<br /> </td> 
   <td> De oorzaak van de foutafstoting komt voor in het foutbericht<br /> </td> 
   <td> Zacht<br /> </td> 
   <td> Geweigerd<br /> </td> 
   <td> Nee<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Android-quarantaine {#android-quarantine}

**Voor Android V1**

Voor elke melding ontvangt Adobe Campaign de synchrone fouten rechtstreeks van de FCM-server. De campagne van Adobe behandelt hen op de vlucht en produceert harde of zachte fouten volgens de strengheid van de fout en de pogingen kunnen worden uitgevoerd:

* Lengte van lading overschreden, verbindingskwestie, de kwestie van de de dienstbeschikbaarheid: opnieuw uitgevoerd, soft error, error reason is **[!UICONTROL Refused]**.
* Apparaatquota overschreden: niet opnieuw proberen, soft error, error reason is **[!UICONTROL Refused]**.
* Ongeldige of niet-geregistreerde token, onverwachte fout, probleem met afzenderaccount: geen nieuwe poging, harde fout, mislukkingsreden is **[!UICONTROL Refused]**.

De **[!UICONTROL mobileAppOptOutMgt]** workflow wordt elke 6 uur uitgevoerd om de **AppSubscriptionRcp** -tabel bij te werken. Voor de tokens die niet-geregistreerd of niet meer geldig zijn verklaard, wordt het gebied **Uitgeschakeld** geplaatst aan **Waar** en het abonnement verbonden aan dat apparatenteken zal automatisch van toekomstige leveringen worden uitgesloten.

Tijdens de leveringsanalyse, worden alle apparaten die van het doel worden uitgesloten automatisch toegevoegd aan de **excludeLogAppSubRcp** lijst.

>[!NOTE]
Voor klanten die de schakelaar Baidu gebruiken, zijn hier de verschillende soorten fouten:
* Verbindingsprobleem aan het begin van de levering: type fout **[!UICONTROL Undefined]**, reden van fout **[!UICONTROL Unreachable]**, opnieuw proberen wordt uitgevoerd.
* Verbinding verloren tijdens een levering: soft error, failure reason **[!UICONTROL Refused]**, re try wordt uitgevoerd.
* Synchrone fout die door Baidu tijdens het verzenden is geretourneerd: harde fout, mislukkingsreden **[!UICONTROL Refused]**, wordt niet opnieuw uitgevoerd.

Adobe Campagne neemt om de 10 minuten contact op met de Baidu-server om de status van het verzonden bericht op te halen en werkt de weblogs bij. Als een bericht wordt verklaard zoals verzonden, wordt de status van het bericht in de uitzendingen geplaatst aan **[!UICONTROL Received]**. Als Baidu een fout declareert, wordt de status ingesteld op **[!UICONTROL Failed]**.

**Voor Android V2**

Android V2-quarantainemomechanisme gebruikt hetzelfde proces als Android V1. Hetzelfde geldt voor de update voor abonnementen en uitsluitingen. Raadpleeg de sectie [Android V1](#android-quarantine) voor meer informatie hierover.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Scenario</strong><br /> </td> 
   <td> <strong>Status</strong><br /> </td> 
   <td> <strong>Foutbericht</strong><br /> </td> 
   <td> <strong>Type fout</strong><br /> </td> 
   <td> <strong>Mislukt</strong><br /> </td> 
   <td> <strong>Opnieuw</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Berichtenaanmaak/analyse fase: ongeldige trefwoorden gebruikt in aangepaste velden<br /> </td> 
   <td> Mislukt<br /> </td> 
   <td> De volgende trefwoorden kunnen niet worden gebruikt: {1}<br /> </td> 
   <td> Zacht<br /> </td> 
   <td> </td> 
   <td> Nee<br /> </td> 
  </tr> 
  <tr> 
   <td> Berichtenaanmaak/analyse fase: lading te groot<br /> </td> 
   <td> Mislukt<br /> </td> 
   <td> De aanmelding is te zwaar: {1} bits, while only {2} are authorised<br /> </td> 
   <td> Zacht<br /> </td> 
   <td> Geweigerd<br /> </td> 
   <td> Nee<br /> </td> 
  </tr> 
  <tr> 
   <td> Netwerkverbinding verloren tijdens verzenden<br /> </td> 
   <td> Mislukt<br /> </td> 
   <td> Geen reactie van de Firebase Cloud Messaging-service op het adres: {1}<br /> </td> 
   <td> Zacht<br /> </td> 
   <td> Onbereikbaar<br /> </td> 
   <td> Ja<br /> </td> 
  </tr> 
  <tr> 
   <td> Afkeuring van FCM-berichten: De FCM-server is tijdelijk niet beschikbaar (bijvoorbeeld met time-outs). <br /> </td> 
   <td> Mislukt<br /> </td> 
   <td> De Firebase Cloud Messaging-service is tijdelijk niet beschikbaar<br /> </td> 
   <td> Zacht<br /> </td> 
   <td> Onbereikbaar<br /> </td> 
   <td> Ja<br /> </td> 
  </tr> 
  <tr> 
   <td> Afkeuring van FCM-berichten: Fout bij verifiëren van senderaccount<br /> </td> 
   <td> Mislukt<br /> </td> 
   <td> Kan de ontwikkelaarsaccount niet identificeren. Controleer uw id en wachtwoord<br /> </td> 
   <td> Zacht<br /> </td> 
   <td> Geweigerd<br /> </td> 
   <td> Nee<br /> </td> 
  </tr> 
  <tr> 
   <td> Afkeuring van FCM-berichten: Apparaatquota overschreden<br /> </td> 
   <td> Mislukt<br /> </td> 
   <td> </td> 
   <td> Zacht<br /> </td> 
   <td> Geweigerd<br /> </td> 
   <td> Ja<br /> </td> 
  </tr> 
  <tr> 
   <td> Afkeuring van FCM-berichten: Ongeldige registratie / niet geregistreerd<br /> </td> 
   <td> Mislukt<br /> </td> 
   <td> </td> 
   <td> Hard<br /> </td> 
   <td> Gebruiker onbekend<br /> </td> 
   <td> Nee<br /> </td> 
  </tr> 
  <tr> 
   <td> Afkeuring van FCM-berichten: Alle andere fouten<br /> </td> 
   <td> Mislukt<br /> </td> 
   <td> De Firebase Cloud Messaging-server heeft een onverwachte foutcode geretourneerd: {1} </td> 
   <td> </td> 
   <td> Geweigerd<br /> </td> 
   <td> Nee<br /> </td> 
  </tr> 
 </tbody> 
</table>

## SMS-quarantines {#sms-quarantines}

**Voor standaardconnectors**

Het quarantainemechanisme voor SMS-berichten is over het algemeen hetzelfde als het algemene proces. Zie [Informatie over quarantines](#about-quarantines). De specifieke kenmerken voor SMS worden hieronder weergegeven.

>[!NOTE]
De **[!UICONTROL Delivery log qualification]** lijst is niet op de **Uitgebreide generische schakelaar SMPP** van toepassing.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Scenario</strong><br /> </td> 
   <td> <strong>Status</strong><br /> </td> 
   <td> <strong>Foutbericht</strong><br /> </td> 
   <td> <strong>Type fout</strong><br /> </td> 
   <td> <strong>Mislukt</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Verzonden naar de provider<br /> </td> 
   <td> Verzonden<br /> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Ontvangen op de mobiele telefoon<br /> </td> 
   <td> Ontvangen<br /> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Fout geretourneerd door provider<br /> </td> 
   <td> Mislukt<br /> </td> 
   <td> Fout bij het ontvangen van gegevens (SR of MO)<br /> </td> 
   <td> Zacht<br /> </td> 
   <td> Onbereikbaar<br /> </td> 
  </tr> 
  <tr> 
   <td> Ongeldige MT-bevestiging<br /> </td> 
   <td> Mislukt<br /> </td> 
   <td> Fout '{1}' tijdens het verwerken van het bevestigingsframe voor het verzenden van de query<br /> </td> 
   <td> Zacht<br /> </td> 
   <td> Onbereikbaar<br /> </td> 
  </tr> 
  <tr> 
   <td> Fout tijdens het verzenden van de MT<br /> </td> 
   <td> Mislukt<br /> </td> 
   <td> Fout tijdens verzenden van berichten<br /> </td> 
   <td> Zacht<br /> </td> 
   <td> Onbereikbaar<br /> </td> 
  </tr> 
 </tbody> 
</table>

**Voor de Uitgebreide generische schakelaar SMPP**

Wanneer het gebruiken van het protocol SMPP om de berichten van SMS te verzenden, wordt het foutenbeheer verschillend behandeld. Voor meer informatie over de Uitgebreide generische schakelaar SMPP, verwijs naar [deze pagina](../../delivery/using/sms-channel.md#creating-an-smpp-external-account).

De schakelaar SMPP wint gegevens van het bericht van SR (Status Report) terug dat gebruikend regelmatige uitdrukkingen (regexes) is teruggekeerd om zijn inhoud te filtreren. Deze gegevens worden vervolgens vergeleken met de gegevens in de **[!UICONTROL Delivery log qualification]** tabel (beschikbaar via **[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Non deliverables Management]** menu).

Voordat een nieuw type fout wordt gekwalificeerd, is de reden van de fout altijd ingesteld op **Geweigerd** .

>[!NOTE]
De fouttypen en -redenen zijn gelijk aan die voor e-mailberichten. Zie Typen [leveringsfouten en redenen](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons).
Vraag uw leverancier om een lijst van status en foutencodes om juiste mislukkingstypes en redenen voor mislukking in de de kwalificatielijst van het Logboek van de Levering te plaatsen.

Voorbeeld van een gegenereerd bericht:

```
SR Generic DELIVRD 000|#MESSAGE#
```

* Alle foutberichten beginnen met **SR** om SMS-foutcodes te onderscheiden van e-mailfoutcodes.
* Het tweede deel (**Algemeen** in dit voorbeeld) van het foutbericht verwijst naar de naam van de SMSC-implementatie, zoals gedefinieerd in het **[!UICONTROL SMSC implementation name]** veld van de externe SMS-rekening. Zie [deze pagina](../../delivery/using/sms-channel.md#creating-an-smpp-external-account).

   Omdat dezelfde foutcode voor elke provider een andere betekenis kan hebben, kunt u in dit veld weten welke provider de foutcode heeft gegenereerd. U kunt de fout dan vinden in de relevante documentatie van de leverancier.

* Het derde deel (**DELIVRD** in dit voorbeeld) van het foutbericht komt overeen met de statuscode die wordt opgehaald uit de SR met behulp van het statusextractieoverzicht dat is gedefinieerd in de externe SMS-account.

   Deze regex wordt opgegeven op het **[!UICONTROL SMSC specificities]** tabblad van de externe account. Zie [deze pagina](../../delivery/using/sms-channel.md#creating-an-smpp-external-account).

   ![](assets/tech_quarant_error_regex.png)

   Standaard extraheert de regex de **status:** veld zoals gedefinieerd in het **aanhangsel B** van de **SMPP 3.4-specificatie**.

* Het vierde deel (**000** in dit voorbeeld) van het foutbericht komt overeen met de foutcode die uit de SR is geëxtraheerd met behulp van het extractieoverzicht van de foutcode dat in de externe SMS-account is gedefinieerd.

   Deze regex wordt opgegeven op het **[!UICONTROL SMSC specificities]** tabblad van de externe account. Zie [deze pagina](../../delivery/using/sms-channel.md#creating-an-smpp-external-account).

   Standaard extraheert de regex de **err:** veld zoals gedefinieerd in het **aanhangsel B** van de **SMPP 3.4-specificatie**.

* Alles wat na het pijlsymbool (|) komt wordt slechts getoond in de **[!UICONTROL First text]** kolom van de **[!UICONTROL Delivery log qualification]** lijst. Deze inhoud wordt altijd vervangen door **#MESSAGE#** nadat het bericht is genormaliseerd. Dit proces voorkomt het hebben van veelvoudige ingangen voor gelijkaardige fouten en is het zelfde als voor e-mail. Zie [Bounce mail-kwalificatie](../../delivery/using/understanding-delivery-failures.md#bounce-mail-qualification)voor meer informatie.

De uitgebreide generische schakelaar SMPP past heuristisch toe om verstandige standaardwaarden te vinden: als de status met **DELIV** begint, wordt het beschouwd als een succes omdat het de gemeenschappelijke status **LEVERT** of **LEVERING** aanpast die door de meeste leveranciers wordt gebruikt. Elke andere status leidt tot een harde fout.
