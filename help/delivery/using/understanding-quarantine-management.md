---
solution: Campaign Classic
product: campaign
title: Werken met quarantainebeheer
description: Werken met quarantainebeheer
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
translation-type: tm+mt
source-git-commit: 6d5dbc16ed6c6e5a2e62ceb522e2ccd64b142825
workflow-type: tm+mt
source-wordcount: '2799'
ht-degree: 14%

---


# Werken met quarantainebeheer{#understanding-quarantine-management}

## Quarantaine {#about-quarantines}

Adobe Campaign beheert een lijst met in quarantaine geplaatste adressen. Ontvangers van wie het adres in quarantaine is geplaatst, worden standaard tijdens de leveringsanalyse uitgesloten, en zullen niet doelgericht worden benaderd. Een e-mailadres kan in quarantaine worden geplaatst, bijvoorbeeld, wanneer het postvak vol is of als het adres niet bestaat. In elk geval voldoet de quarantaineprocedure aan de hieronder beschreven specifieke voorschriften.

>[!NOTE]
>
>Deze sectie is van toepassing op online kanalen: e-mail, SMS, pushmelding.

### Uw levering optimaliseren via quarantaine {#optimizing-your-delivery-through-quarantines}

De profielen waarvan de e-mailadressen of telefoonnummers in quarantaine zijn geplaatst, worden automatisch uitgesloten tijdens de voorbereiding van berichten (zie [In quarantaine geplaatste adressen voor een levering identificeren](#identifying-quarantined-addresses-for-a-delivery)). Hierdoor wordt de levering versneld, omdat het foutenpercentage een belangrijk effect heeft op de leveringssnelheid.

Sommige internetproviders beschouwen e-mails automatisch als spam als het aantal ongeldige adressen te hoog is. Met quarantaine kunt u dus voorkomen dat u door deze providers aan de lijst van afgewezen personen wordt toegevoegd.

Bovendien zijn de verzendkosten voor sms-berichten lager doordat onjuiste telefoonnummers van de levering worden uitgesloten. Raadpleeg [deze pagina](../../delivery/using/delivery-best-practices.md) voor meer informatie over de best practices voor het beveiligen en optimaliseren van uw leveringen .

### Quarantaine versus lijst van afgewezen personen {#quarantine-vs-denylist}

**Quarantaine** is alleen van toepassing op een adres, niet op het profiel zelf. Wanneer twee profielen hetzelfde e-mailadres hebben, worden ze dus allebei beïnvloed als het adres in quarantaine wordt geplaatst.

Op dezelfde manier kan een profiel waarvan het e-mailadres in quarantaine is geplaatst, zijn profiel bijwerken en een nieuw adres invoeren. Dit profiel kan dan opnieuw worden getarget door leveringsacties.

Als u op de **lijst van afgewezen personen** staat, wordt het profiel echter niet meer gericht op levering, bijvoorbeeld na een abonnement (opt-out).

>[!NOTE]
>
>Wanneer een gebruiker op een SMS-bericht reageert met een trefwoord zoals &quot;STOP&quot; om zich af te melden voor SMS-leveringen, wordt dit profiel niet toegevoegd aan de lijst van afgewezen personen, zoals in het e-mailuitschakelproces. Het profieltelefoonnummer wordt naar quarantaine verzonden, zodat de gebruiker e-mailberichten blijft ontvangen.

## In quarantaine geplaatste adressen identificeren {#identifying-quarantined-addresses}

Adressen kunnen in quarantaine worden geplaatst voor een specifieke levering of voor het volledige platform.

### In quarantaine geplaatste adressen voor een levering identificeren {#identifying-quarantined-addresses-for-a-delivery}

Gegarandeerde adressen voor een specifieke levering zijn vermeld tijdens de leveringsvoorbereidingsfase, in de leveringslogboeken van het leveringsdashboard (zie [leveringslogboeken en geschiedenis](../../delivery/using/delivery-dashboard.md#delivery-logs-and-history)).

### In quarantaine geplaatste adressen voor het volledige platform identificeren {#identifying-quarantined-addresses-for-the-entire-platform}

Beheerders kunnen de adressen in quarantaine weergeven voor het gehele platform vanaf het knooppunt **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]**.

>[!NOTE]
>
>Dit menu bevat quarantaine-elementen voor **e-mail**-, **sms**- en **pushberichtkanalen**.

Voor elk adres is de volgende informatie beschikbaar:

![](assets/tech_quarant_npai.png)

>[!NOTE]
>
>De toename van het aantal quarantines is een normaal effect dat gerelateerd is aan de &quot;slijtage&quot; van de database. Als de levensduur van een e-mailadres bijvoorbeeld wordt beschouwd als drie jaar en de tabel met ontvangers elk jaar met 50% toeneemt, kan de toename van quarantaine als volgt worden berekend:
>
>Einde van jaar 1: (1*0,33)/(1+0,5)=22%.
Einde van jaar 2: ((1,22*0,33)+0,33)/(1,5+0,75)=32,5%.

### Het identificeren van quarantined adressen in leveringsrapporten {#identifying-quarantined-addresses-in-delivery-reports}

De volgende rapporten verstrekken informatie over de adressen in quarantaine:

* Voor elke levering, toont het **[!UICONTROL Delivery summary]** rapport het aantal adressen in quarantaine in het leveringsdoel. Het toont:

   * het aantal adressen dat tijdens de afleveringsanalyse in quarantaine wordt geplaatst;

   * Het aantal adressen die in quarantaine na de leveringsactie worden geplaatst.

* Het **[!UICONTROL Non-deliverables and bounces]** rapport toont informatie over de adressen in quarantaine, de types van aangetroffen fout, enz., en een mislukkingsonderbreking door domein.

U kunt deze informatie voor alle leveringen van het platform (**[!UICONTROL Home page > Reports]**) of voor een specifieke levering opzoeken. U kunt ook aangepaste rapporten maken en de informatie selecteren die moet worden weergegeven.

### Het identificeren van quarantined adressen voor een ontvanger {#identifying-quarantined-addresses-for-a-recipient}

U kunt de status van het e-mailadres van elke ontvanger opzoeken. Selecteer hiertoe het ontvangende profiel en klik op het tabblad **[!UICONTROL Deliveries]**. Voor alle leveringen aan die ontvanger, kunt u te weten komen of het ontbroken adres, tijdens analyse in quarantined, enz. was. Voor elke map kunt u alleen de ontvangers weergeven van wie het e-mailadres in quarantaine staat. Hiervoor gebruikt u het toepassingsfilter **[!UICONTROL Quarantined email address]**.

![](assets/tech_quarant_recipients_filter.png)

### Het verwijderen van een quarantined adres {#removing-a-quarantined-address}

Indien nodig, kunt u een adres uit de quarantainelijst manueel verwijderen. Daarnaast worden adressen die overeenkomen met specifieke voorwaarden automatisch uit de quarantainelijst verwijderd door de workflow **[!UICONTROL Database cleanup]**.

Een adres handmatig uit de quarantainelijst verwijderen:

* U kunt zijn status in **[!UICONTROL Valid]** van **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]** knoop veranderen.

   ![](assets/tech_quarant_error_status.png)

* U kunt ook de status wijzigen in **[!UICONTROL Allowlisted]**. In dit geval blijft het adres op de quarantainelijst staan, maar het wordt systematisch als doel gebruikt, zelfs als er een fout optreedt.

De adressen worden automatisch verwijderd uit de quarantainelijst in de volgende gevallen:

* Adressen in een status **[!UICONTROL With errors]** zullen uit de quarantainelijst na succesvolle levering worden verwijderd.
* Adressen in een status **[!UICONTROL With errors]** worden uit de quarantainelijst verwijderd als de laatste zachte stuit meer dan 10 dagen geleden plaatsvond. Zie [deze sectie](#soft-error-management) voor meer informatie over softerror management.
* Adressen in een status **[!UICONTROL With errors]** die met de fout **[!UICONTROL Mailbox full]** zijn verworpen zullen na 30 dagen uit de quarantainelijst worden verwijderd.

Hun status verandert dan in **[!UICONTROL Valid]**.

>[!IMPORTANT]
Ontvangers met een adres in de status **[!UICONTROL Quarantine]** of **[!UICONTROL On denylist]** worden nooit verwijderd, zelfs niet als ze een e-mail ontvangen.

U kunt het aantal fouten en de periode tussen twee fouten wijzigen. Om dit te doen, verander de overeenkomstige montages in de plaatsingstovenaar (**[!UICONTROL Email channel]** > **[!UICONTROL Advanced parameters]**). Raadpleeg [deze sectie](../../installation/using/deploying-an-instance.md) voor meer informatie over de implementatietovenaar.

## Voorwaarden voor het in quarantaine plaatsen van een adres {#conditions-for-sending-an-address-to-quarantine}

Adobe Campaign beheert quarantaine volgens het type van de leveringsmislukking en de reden die tijdens de kwalificatie van foutenmeldingen wordt toegewezen (zie [Bounce postkwalificatie](../../delivery/using/understanding-delivery-failures.md#bounce-mail-qualification)) en [De types en redenen van de leveringsmislukking ](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons).

* **Genegeerde fout**: bij genegeerde fouten wordt een adres niet in quarantaine geplaatst.
* **Harde fout**: het desbetreffende e-mailadres wordt onmiddellijk in quarantaine geplaatst.
* **Zachte fout**: bij zachte fouten wordt het adres niet direct in quarantaine geplaatst, maar neemt het aantal fouten op de foutenteller toe. Zie [Zwak foutenbeheer](#soft-error-management) voor meer informatie.

Als een gebruiker een e-mail als spam ([Feedback lijn](../../delivery/using/technical-recommendations.md#feedback-loop)) kwalificeert, wordt het bericht automatisch opnieuw gericht naar een technische brievenbus die door Adobe wordt geleid. Het e-mailadres van de gebruiker wordt vervolgens automatisch naar quarantaine verzonden.

In de lijst van quarantined adressen, wijst het **[!UICONTROL Error reason]** gebied erop waarom het geselecteerde adres in quarantaine werd geplaatst. Quarantaine in Adobe Campaign is hoofdlettergevoelig. Zorg dat u de e-mailadressen in kleine letters importeert, zodat ze later niet opnieuw worden getarget.

![](assets/tech_quarant_error_reasons.png)

### Beheer van zachte fouten {#soft-error-management}

In tegenstelling tot harde fouten, verzenden de zachte fouten onmiddellijk geen adres naar quarantaine, maar zij verhogen in plaats daarvan een foutenteller.

* Wanneer de foutenteller de grensdrempel bereikt, dan gaat het adres in quarantaine.
* In de standaardconfiguratie is de drempel ingesteld op vijf fouten, waarbij twee fouten significant worden bij een tussenliggende periode van minstens 24 uur. Het adres wordt bij de vijfde fout in quarantaine geplaatst.
* De drempelwaarde voor de foutenteller kan worden gewijzigd. Voor meer op dit, verwijs naar [Opnieuw na een levering tijdelijke mislukking](../../delivery/using/understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure).

De foutenteller wordt opnieuw geïnitialiseerd als de laatste significante fout meer dan 10 dagen geleden voorkwam. De adresstatus verandert dan in **Geldig** en het wordt geschrapt uit de lijst van quarantines door **Opschonen van het Gegevensbestand** werkschema.

## Push notification quarantines {#push-notification-quarantines}

Het quarantainemechanisme voor pushmeldingen is over het algemeen hetzelfde als het algemene proces. Zie [Informatie over quarantines](#about-quarantines). Bepaalde fouten worden echter anders beheerd voor pushberichten. Voor bepaalde fouten in de software worden bijvoorbeeld geen pogingen opnieuw uitgevoerd binnen dezelfde levering. De specifieke kenmerken voor pushmeldingen worden hieronder weergegeven. Het mechanisme voor opnieuw proberen (aantal pogingen, frequentie) is hetzelfde als voor e-mailberichten.

De items die in quarantaine worden geplaatst, zijn apparaattokens.

### iOS-quarantaine {#ios-quarantine}

**Voor iOS - binaire connector**

>[!NOTE]
Vanaf Campaign versie 20.3 is de verouderde binaire iOS-connector van iOS afgeschaft. Als u deze connector gebruikt, moet u uw implementatie dienovereenkomstig aanpassen. [Meer informatie](https://helpx.adobe.com/campaign/kb/migrate-to-apns-http2.html)

Voor elk bericht ontvangt Adobe Campaign de synchrone en asynchrone fouten van de APNs-server. Bij de volgende synchrone fouten genereert Adobe Campaign schermfouten:

* Problemen met de lengte van de lading: niet opnieuw proberen, is de mislukkingsreden **[!UICONTROL Unreachable]**.
* Problemen met certificaatvervaldatum: niet opnieuw proberen, is de mislukkingsreden **[!UICONTROL Unreachable]**.
* Verbinding verloren tijdens levering: opnieuw uitgevoerd, is de mislukkingsreden **[!UICONTROL Unreachable]**.
* Uitgave serviceconfiguratie (ongeldig certificaat, ongeldig certificaatwachtwoord, geen certificaat): niet opnieuw proberen, is de mislukkingsreden **[!UICONTROL Unreachable]**.

De APNs-server meldt Adobe Campaign asynchroon dat een apparaattoken niet is geregistreerd (wanneer de mobiele toepassing door de gebruiker is verwijderd). De **[!UICONTROL mobileAppOptOutMgt]** werkschema loopt om de 6 uur om APNs te contacteren terugkoppelt diensten om de **AppSubscriptionRcp** lijst bij te werken. Voor alle gedeactiveerde tokens, wordt het gebied **Disabled** geplaatst aan **True** en het abonnement verbonden aan dat apparatenteken zal automatisch van toekomstige leveringen worden uitgesloten.

**Voor iOS - HTTP/V2-connector**

Met het HTTP/V2-protocol kunt u rechtstreeks feedback geven en de status van elke push-levering bepalen. Als de HTTP/V2 protocolschakelaar wordt gebruikt, koppelt de dienst niet meer door **[!UICONTROL mobileAppOptOutMgt]** werkschema wordt geroepen. De niet-geregistreerde tokens worden verschillend afgehandeld tussen de binaire iOS-connector en de iOS HTTP/V2-connector. Een token wordt als niet-geregistreerd beschouwd wanneer een mobiele toepassing wordt verwijderd of opnieuw wordt geïnstalleerd.

Synchroon, als APNs een &quot;unregistered&quot;status voor een bericht terugkeert, zal het doelteken onmiddellijk in quarantaine worden geplaatst.

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
   <td> Gericht apparaat ingeschakeld op<br /> </td> 
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
   <td> Gebruiker schakelt berichten voor de toepassing<br /> uit </td> 
   <td> OK<br /> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Berichtaanmaak/analysefase - lading te groot<br /> </td> 
   <td> Mislukt<br /> </td> 
   <td> Payload te lang<br /> </td> 
   <td> Zwak<br /> </td> 
   <td> Geweigerd<br /> </td> 
   <td> Geen<br /> </td> 
  </tr> 
  <tr> 
   <td> Berichtaanmaak/analysefase - onverwachte inhoudsopmaakkwestie<br /> </td> 
   <td> Mislukt<br /> </td> 
   <td> Verschillende foutberichten volgens de fout<br /> </td> 
   <td> Zwak<br /> </td> 
   <td> Ongedefinieerd<br /> </td> 
   <td> Geen<br /> </td> 
  </tr> 
  <tr> 
   <td> Certificaatafgifte (wachtwoord, beschadiging, enz.) en test verbinding aan de kwestie van APN<br /> </td> 
   <td> Mislukt<br /> </td> 
   <td> Verschillende foutberichten volgens de fout<br /> </td> 
   <td> Zwak<br /> </td> 
   <td> Geweigerd<br /> </td> 
   <td> Geen<br /> </td> 
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
   <td> APNs-berichtafwijzing: Unregistration<br /> de gebruiker heeft de toepassing verwijderd of het teken is verlopen<br /> </td> 
   <td> Mislukt<br /> </td> 
   <td> Niet geregistreerd<br /> </td> 
   <td> Hard<br /> </td> 
   <td> Gebruiker onbekend<br /> </td> 
   <td> Geen<br /> </td> 
  </tr> 
  <tr> 
   <td> APNs-berichtafwijzing: alle andere fouten<br /> </td> 
   <td> Mislukt<br /> </td> 
   <td> De oorzaak van de foutenverwerping zal in het foutenbericht <br /> aanwezig zijn </td> 
   <td> Zwak<br /> </td> 
   <td> Geweigerd<br /> </td> 
   <td> Geen<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Android-quarantaine {#android-quarantine}

**Voor Android V1**

Voor elke melding ontvangt Adobe Campaign de synchrone fouten rechtstreeks van de FCM-server. Met de Adobe-campagne worden ze direct afgehandeld en worden harde of zachte fouten gegenereerd op basis van de ernst van de fout. U kunt het opnieuw proberen:

* Lengte van lading overschreden, verbindingskwestie, de kwestie van de de dienstbeschikbaarheid: uitgevoerd opnieuw proberen, zachte fout, mislukkingsreden is **[!UICONTROL Refused]**.
* Apparaatquota overschreden: geen herpoging, zachte fout, mislukkingsreden is **[!UICONTROL Refused]**.
* Ongeldige of niet-geregistreerde token, onverwachte fout, probleem met afzenderaccount: geen herpoging, harde fout, mislukkingsreden is **[!UICONTROL Refused]**.

De **[!UICONTROL mobileAppOptOutMgt]** werkschema loopt om de 6 uur om de **AppSubscriptionRcp** lijst bij te werken. Voor tokens die niet geregistreerd of niet langer geldig zijn verklaard, wordt het gebied **Disabled** geplaatst aan **True** en het abonnement verbonden aan dat apparatenteken zal automatisch van toekomstige leveringen worden uitgesloten.

Tijdens de leveringsanalyse, worden alle apparaten die van het doel worden uitgesloten automatisch toegevoegd aan **excludeLogAppSubRcp** lijst.

>[!NOTE]
Voor klanten die de schakelaar Baidu gebruiken, zijn hier de verschillende soorten fouten:
* Verbindingsprobleem aan het begin van de levering: type fout **[!UICONTROL Undefined]**, reden van mislukking **[!UICONTROL Unreachable]**, wordt opnieuw uitgevoerd.
* Verbinding verloren tijdens een levering: soft error, failure reason **[!UICONTROL Refused]**, re try wordt uitgevoerd.
* Synchrone fout die door Baidu tijdens het verzenden is geretourneerd: harde fout, mislukkingsreden **[!UICONTROL Refused]**, wordt niet opnieuw uitgevoerd.

Adobe Campaign neemt om de 10 minuten contact op met de Baidu-server om de status van het verzonden bericht op te halen en werkt de weblogs bij. Als een bericht zoals verzonden wordt verklaard, wordt het statuut van het bericht in de uitzendingen geplaatst aan **[!UICONTROL Received]**. Als Baidu een fout declareert, wordt de status ingesteld op **[!UICONTROL Failed]**.

**Voor Android V2**

Android V2-quarantainemomechanisme gebruikt hetzelfde proces als Android V1. Hetzelfde geldt voor de update voor abonnementen en uitsluitingen. Raadpleeg voor meer informatie de sectie [Android V1](#android-quarantine).

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
   <td> Berichtenaanmaak/analyse fase: ongeldige trefwoorden die worden gebruikt in aangepaste velden<br /> </td> 
   <td> Mislukt<br /> </td> 
   <td> De volgende trefwoorden kunnen niet worden gebruikt: {1}<br /> </td> 
   <td> Zwak<br /> </td> 
   <td> </td> 
   <td> Geen<br /> </td> 
  </tr> 
  <tr> 
   <td> Berichtenaanmaak/analyse fase: lading te groot<br /> </td> 
   <td> Mislukt<br /> </td> 
   <td> De aanmelding is te zwaar: {1} beetjes, terwijl slechts \ {2 \} wordt geautoriseerd<br /> </td> 
   <td> Zwak<br /> </td> 
   <td> Geweigerd<br /> </td> 
   <td> Geen<br /> </td> 
  </tr> 
  <tr> 
   <td> Netwerkverbinding verloren tijdens verzenden<br /> </td> 
   <td> Mislukt<br /> </td> 
   <td> Geen reactie van de Firebase Cloud Messaging-service op het adres: {1}<br /> </td> 
   <td> Zwak<br /> </td> 
   <td> Onbereikbaar<br /> </td> 
   <td> Ja<br /> </td> 
  </tr> 
  <tr> 
   <td> Afkeuring van FCM-berichten: De FCM-server is tijdelijk niet beschikbaar (bijvoorbeeld met time-outs). <br /> </td> 
   <td> Mislukt<br /> </td> 
   <td> De Firebase Cloud Messaging-service is tijdelijk niet beschikbaar<br /> </td> 
   <td> Zwak<br /> </td> 
   <td> Onbereikbaar<br /> </td> 
   <td> Ja<br /> </td> 
  </tr> 
  <tr> 
   <td> Afkeuring van FCM-berichten: Fout bij het verifiëren van het senderaccount<br /> </td> 
   <td> Fout<br /> </td> 
   <td> Kan het ontwikkelaarsaccount niet identificeren. Controleer uw id en wachtwoord<br /> </td> 
   <td> Zacht<br /> </td> 
   <td> Geweigerd<br /> </td> 
   <td> Nee<br /> </td> 
  </tr> 
  <tr> 
   <td> Afwijzing van FCM-bericht: Apparaatquota overschreden<br /> </td> 
   <td> Fout<br /> </td> 
   <td> </td> 
   <td> Zacht<br /> </td> 
   <td> Geweigerd<br /> </td> 
   <td> Ja<br /> </td> 
  </tr> 
  <tr> 
   <td> Afwijzing van FCM-bericht: Ongeldige registratie / niet geregistreerd<br /> </td> 
   <td> Fout<br /> </td> 
   <td> </td> 
   <td> Hard<br /> </td> 
   <td> Gebruiker onbekend<br /> </td> 
   <td> Nee<br /> </td> 
  </tr> 
  <tr> 
   <td> Afwijzing van FCM-bericht: Alle andere fouten<br /> </td> 
   <td> Fout<br /> </td> 
   <td> De Firebase Cloud Messaging-server heeft een onverwachte foutcode geretourneerd: {1} </td> 
   <td> </td> 
   <td> Geweigerd<br /> </td> 
   <td> Nee<br /> </td> 
  </tr> 
    <tr> 
   <td> Afwijzing van FCM-bericht: Ongeldig argument<br /> </td> 
   <td> Fout<br /> </td> 
   <td> INVALID_ARGUMENT </td> 
   <td> Genegeerd</td> 
   <td> Ongedefinieerd<br /> </td> 
   <td> Nee<br /> </td> 
  </tr>
    <tr> 
   <td> Afwijzing van FCM-bericht: Verificatiefout van derden<br /> </td> 
   <td> Fout<br /> </td> 
   <td> THIRD_PARTY_AUTH_ERROR </td> 
   <td> Genegeerd</td>
   <td> Geweigerd<br /> </td> 
   <td> Ja<br /> </td> 
  </tr>
    <tr> 
   <td> Afwijzing van FCM-bericht: Afzender-id komt niet overeen<br /> </td> 
   <td> Fout<br /> </td> 
   <td> SENDER_ID_MISMATCH </td> 
   <td> Zacht</td>
   <td> Gebruiker onbekend<br /> </td> 
   <td> Nee<br /> </td> 
  </tr>
    <tr> 
   <td> Afwijzing van FCM-bericht: Niet geregistreerd<br /> </td> 
   <td> Fout<br /> </td>
   <td> ONGEREGISTREERD </td> 
   <td> Hard</td> 
   <td> Gebruiker onbekend<br /> </td> 
   <td> Nee<br /> </td> 
  </tr>
    <tr> 
   <td> Afwijzing van FCM-bericht: Intern<br /> </td> 
   <td> Fout<br /> </td> 
   <td> INTERN </td> 
   <td> Genegeerd</td> 
   <td> Geweigerd<br /> </td> 
   <td> Ja<br /> </td> 
  </tr>
    <tr> 
   <td> Afwijzing van FCM-bericht: Niet beschikbaar<br /> </td> 
   <td> Fout<br /> </td> 
   <td> ONBESCHIKBAAR</td> 
   <td> Genegeerd</td> 
   <td> Geweigerd<br /> </td> 
   <td> Ja<br /> </td> 
  </tr>
    <tr> 
   <td> Afwijzing van FCM-bericht: onverwachte foutcode<br /> </td> 
   <td> Fout<br /> </td> 
   <td> onverwachte foutcode</td> 
   <td> Genegeerd</td> 
   <td> Geweigerd<br /> </td> 
   <td> Nee<br /> </td> 
  </tr>
  <tr> 
   <td> Verificatie: Verbindingsprobleem<br /> </td> 
   <td> Fout<br /> </td> 
   <td> Kan geen verbinding maken met verificatieserver </td> 
   <td> Genegeerd</td>
   <td> Geweigerd<br /> </td> 
   <td> Ja<br /> </td> 
  </tr>
    <tr> 
   <td> Verificatie: Niet-geautoriseerde client of bereik in verzoek.<br /> </td> 
   <td> Fout<br /> </td> 
   <td> onbevoegd_client </td> 
   <td> Genegeerd</td>
   <td> Geweigerd<br /> </td> 
   <td> Nee<br /> </td> 
  </tr>
    <tr> 
   <td> Verificatie: De client is niet geautoriseerd om toegangstokens op te halen met deze methode of de client is niet geautoriseerd voor een van de gevraagde bereiken.<br /> </td> 
   <td> Fout<br /> </td> 
   <td> onbevoegd_client </td> 
   <td> Genegeerd</td>
   <td> Geweigerd<br /> </td> 
   <td> Nee<br /> </td> 
  </tr>
    <tr> 
   <td> Verificatie: Toegang geweigerd<br /> </td> 
   <td> Mislukt<br /> </td>
   <td> access_deny</td> 
   <td> Genegeerd</td>
   <td> Geweigerd<br /> </td> 
   <td> Geen<br /> </td> 
  </tr>
    <tr> 
   <td> Verificatie: Ongeldige e-mail<br /> </td> 
   <td> Mislukt<br /> </td> 
   <td> invalid_Grant </td> 
   <td> Genegeerd</td> 
   <td> Geweigerd<br /> </td> 
   <td> Geen<br /> </td> 
  </tr>
    <tr> 
   <td> Verificatie: Ongeldige JWT<br /> </td> 
   <td> Mislukt<br /> </td> 
   <td> invalid_Grant </td> 
   <td> Genegeerd</td> 
   <td> Geweigerd<br /> </td> 
   <td> Geen<br /> </td> 
  </tr>
    <tr> 
   <td> Verificatie: Ongeldige JWT-handtekening<br /> </td> 
   <td> Mislukt<br /> </td> 
   <td> invalid_Grant </td> 
   <td> Genegeerd</td> 
   <td> Geweigerd<br /> </td> 
   <td> Geen<br /> </td> 
  </tr>
    <tr> 
   <td> Verificatie: Ongeldig OAuth werkingsgebied of het symbolische publiek van identiteitskaart verstrekte<br /> </td> 
   <td> Mislukt<br /> </td> 
   <td> onbevoegd_client</td> 
   <td> Genegeerd</td> 
   <td> Geweigerd<br /> </td> 
   <td> Geen<br /> </td> 
  </tr>
    <tr> 
   <td> Verificatie: OAuth-client uitgeschakeld<br /> </td> 
   <td> Mislukt<br /> </td> 
   <td> disabled_client</td> 
   <td> Genegeerd</td> 
   <td> Geweigerd<br /> </td> 
   <td> Geen<br /> </td> 
  </tr>
 </tbody> 
</table>

## SMS-quarantines {#sms-quarantines}

**Voor standaardconnectors**

Het quarantainemechanisme voor SMS-berichten is over het algemeen hetzelfde als het algemene proces. Zie [Informatie over quarantines](#about-quarantines). De specifieke kenmerken voor SMS worden hieronder weergegeven.

>[!NOTE]
De tabel **[!UICONTROL Delivery log qualification]** is niet van toepassing op de **Extended generische SMPP**-connector.

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
   <td> Ontvangen op de mobiele<br /> </td> 
   <td> Ontvangen<br /> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Fout geretourneerd door provider<br /> </td> 
   <td> Mislukt<br /> </td> 
   <td> Fout bij het ontvangen van gegevens (SR of MO)<br /> </td> 
   <td> Zwak<br /> </td> 
   <td> Onbereikbaar<br /> </td> 
  </tr> 
  <tr> 
   <td> Ongeldige MT-bevestiging<br /> </td> 
   <td> Mislukt<br /> </td> 
   <td> Fout '\{1 \}' terwijl het verwerken van erkenningskader voor verzendt vraag<br /> </td> 
   <td> Zwak<br /> </td> 
   <td> Onbereikbaar<br /> </td> 
  </tr> 
  <tr> 
   <td> Fout tijdens het verzenden van de MT<br /> </td> 
   <td> Mislukt<br /> </td> 
   <td> Fout tijdens verzenden van berichten<br /> </td> 
   <td> Zwak<br /> </td> 
   <td> Onbereikbaar<br /> </td> 
  </tr> 
 </tbody> 
</table>

**Voor de Uitgebreide generische schakelaar SMPP**

Wanneer het gebruiken van het protocol SMPP om de berichten van SMS te verzenden, wordt het foutenbeheer verschillend behandeld. Voor meer informatie over de Uitgebreide generische schakelaar SMPP, verwijs naar [deze pagina](../../delivery/using/sms-channel.md#creating-an-smpp-external-account).

De schakelaar SMPP wint gegevens van het bericht van SR (Status Report) terug dat gebruikend regelmatige uitdrukkingen (regexes) is teruggekeerd om zijn inhoud te filtreren. Deze gegevens worden vervolgens vergeleken met de informatie in de tabel **[!UICONTROL Delivery log qualification]** (beschikbaar via het menu **[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Non deliverables Management]**).

Voordat een nieuw type fout wordt gekwalificeerd, is de reden van de fout altijd ingesteld op **Geweigerd** standaard.

>[!NOTE]
De fouttypen en -redenen zijn gelijk aan die voor e-mailberichten. Zie [Typen leveringsfouten en redenen](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons).
Vraag uw leverancier om een lijst van status en foutencodes om juiste mislukkingstypes en redenen voor mislukking in de de kwalificatielijst van het Logboek van de Levering te plaatsen.

Voorbeeld van een gegenereerd bericht:

```
SR Generic DELIVRD 000|#MESSAGE#
```

* Alle foutberichten beginnen met **SR** om SMS-foutcodes te onderscheiden van e-mailfoutcodes.
* Het tweede deel (**Generic** in dit voorbeeld) van het foutbericht verwijst naar de naam van de SMSC-implementatie zoals gedefinieerd in het veld **[!UICONTROL SMSC implementation name]** van de externe SMS-account. Zie [deze pagina](../../delivery/using/sms-channel.md#creating-an-smpp-external-account).

   Omdat dezelfde foutcode voor elke provider een andere betekenis kan hebben, kunt u in dit veld weten welke provider de foutcode heeft gegenereerd. U kunt de fout dan vinden in de relevante documentatie van de leverancier.

* Het derde deel (**DELIVRD** in dit voorbeeld) van het foutbericht komt overeen met de statuscode die wordt opgehaald uit de SR met behulp van het statusextractieoverzicht dat is gedefinieerd in de externe SMS-account.

   Deze regex wordt opgegeven op het tabblad **[!UICONTROL SMSC specificities]** van de externe account. Zie [deze pagina](../../delivery/using/sms-channel.md#creating-an-smpp-external-account).

   ![](assets/tech_quarant_error_regex.png)

   Standaard extraheert de regex het veld **stat:** zoals gedefinieerd in de sectie **Bijlage B** van de **SMPP 3.4-specificatie**.

* Het vierde deel (**000** in dit voorbeeld) van het foutbericht komt overeen met de foutcode die uit de SR is geëxtraheerd met behulp van het extractieoverzicht van de foutcode dat in de externe SMS-account is gedefinieerd.

   Deze regex wordt opgegeven op het tabblad **[!UICONTROL SMSC specificities]** van de externe account. Zie [deze pagina](../../delivery/using/sms-channel.md#creating-an-smpp-external-account).

   Standaard extraheert de regex het veld **err:** zoals gedefinieerd in de sectie **Bijlage B** van de **SMPP 3.4-specificatie**.

* Alles wat na het pijpsymbool (|) komt wordt slechts getoond in **[!UICONTROL First text]** kolom van **[!UICONTROL Delivery log qualification]** lijst. Deze inhoud wordt altijd vervangen door **#MESSAGE#** nadat het bericht is genormaliseerd. Dit proces voorkomt het hebben van veelvoudige ingangen voor gelijkaardige fouten en is het zelfde als voor e-mail. Zie [Bounce mailkwalificatie](../../delivery/using/understanding-delivery-failures.md#bounce-mail-qualification) voor meer informatie.

De uitgebreide generische schakelaar SMPP past heuristisch toe om verstandige standaardwaarden te vinden: als de status met **DELIV** begint, wordt het beschouwd als een succes omdat het de gemeenschappelijke status **DELIVRD** of **DELIVERED** aanpast die door de meeste leveranciers wordt gebruikt. Elke andere status leidt tot een harde fout.
