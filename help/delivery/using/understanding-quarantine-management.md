---
product: campaign
title: Quarantainebeheer begrijpen
description: Quarantainebeheer begrijpen
badge-v8: label="Ook van toepassing op v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
feature: Monitoring, Deliverability
role: User
exl-id: cfd8f5c9-f368-4a31-a1e2-1d77ceae5ced
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '2987'
ht-degree: 7%

---

# Quarantainebeheer begrijpen{#understanding-quarantine-management}

Adobe Campaign beheert een lijst met in quarantaine geplaatste adressen. Ontvangers van wie het adres in quarantaine is geplaatst, worden standaard tijdens de leveringsanalyse uitgesloten, en zullen niet doelgericht worden benaderd. Een e-mailadres kan in quarantaine worden geplaatst, bijvoorbeeld, wanneer de brievenbus volledig is of als het adres niet bestaat. In elk geval voldoet de quarantaineprocedure aan de hieronder beschreven specifieke voorschriften.

>[!NOTE]
>
>Deze sectie is van toepassing op online kanalen: e-mail, SMS, pushmelding.

## De levering optimaliseren via quarantainebeheer {#optimizing-your-delivery-through-quarantines}

De profielen waarvan e-mailadressen of telefoonaantal in quarantaine zijn worden automatisch uitgesloten tijdens berichtvoorbereiding (zie [ quarantined adressen voor een levering ](#identifying-quarantined-addresses-for-a-delivery) identificeren). Hierdoor wordt de levering versneld, omdat het foutenpercentage een belangrijk effect heeft op de leveringssnelheid.

Sommige internetproviders beschouwen e-mails automatisch als spam als het aantal ongeldige adressen te hoog is. Met quarantaine kunt u dus voorkomen dat deze providers aan de lijst van gewezen personen worden toegevoegd.

Bovendien zijn de verzendkosten voor sms-berichten lager doordat onjuiste telefoonnummers van de levering worden uitgesloten.

Raadpleeg [deze pagina](delivery-best-practices.md) voor meer informatie over de best practices voor het beveiligen en optimaliseren van uw leveringen.

### Quarantine versus lijst van gewezen personen {#quarantine-vs-denylist}

Quarantaine en lijst van gewezen personen zijn niet van toepassing op hetzelfde object:

* **quarantaine** is slechts op een **adres** (of telefoonaantal, enz.), niet op het profiel zelf van toepassing. Een profiel waarvan het e-mailadres in quarantaine is geplaatst, kan bijvoorbeeld zijn profiel bijwerken en een nieuw adres invoeren. Dit profiel kan dan opnieuw worden geactiveerd door leveringsacties. Eveneens, als twee profielen gebeuren om het zelfde telefoonaantal te hebben, zullen zij allebei worden beïnvloed als het aantal quarantined is.

  De quarantined adressen of telefoonaantallen worden getoond in [ uitsluitingslogboeken ](#identifying-quarantined-addresses-for-a-delivery) (voor een levering) of in de [ quarantainelijst ](#identifying-quarantined-addresses-for-the-entire-platform) (voor het volledige platform).

* Het zijn op de **lijst van gewezen personen**, anderzijds, zal in het **profiel** resulteren niet meer door de levering, zoals na een unsubscription (opt-out), voor een bepaald kanaal wordt gericht. Als een profiel op de lijst van gewezen personen voor het e-mailkanaal bijvoorbeeld twee e-mailadressen heeft, worden beide adressen van levering uitgesloten.

  In de sectie **[!UICONTROL No longer contact]** van het tabblad **[!UICONTROL General]** van het profiel kunt u controleren of er zich op de lijst van gewezen personen een of meer kanalen bevinden in de sectie  van het profiel. Zie [deze sectie](../../platform/using/editing-a-profile.md#general-tab).

>[!NOTE]
>
>Quarantaine bevat een **[!UICONTROL Denylisted]** -status die van toepassing is wanneer ontvangers uw bericht melden als spam of op een SMS-bericht reageren met een trefwoord zoals &quot;STOP&quot;. In dat geval wordt het betreffende adres of telefoonnummer van het profiel naar quarantaine verzonden met de status **[!UICONTROL Denylisted]** . Voor meer bij het beheren van STOP SMS berichten, verwijs naar [ deze sectie ](../../delivery/using/sms-send.md#processing-inbound-messages).

## In quarantaine geplaatste adressen identificeren {#identifying-quarantined-addresses}

Adressen kunnen in quarantaine worden geplaatst voor een specifieke levering of voor het volledige platform.

### Identificeer quarantined adressen voor een levering {#identifying-quarantined-addresses-for-a-delivery}

De gekwantificeerde adressen voor een specifieke levering zijn vermeld tijdens de fase van de leveringsvoorbereiding, in de leveringslogboeken van het leveringsdashboard (zie [ Logboeken van de Levering en geschiedenis ](delivery-dashboard.md#delivery-logs-and-history)).

### Identificeer quarantined adressen voor het volledige platform {#identifying-quarantined-addresses-for-the-entire-platform}

Beheerders kunnen de adressen in quarantaine weergeven voor het gehele platform vanaf het knooppunt **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]** .

>[!NOTE]
>
>Dit menu bevat quarantaine-elementen voor **e-mail**-, **sms**- en **pushberichtkanalen**.

Voor elk adres is de volgende informatie beschikbaar:

![](assets/tech_quarant_npai.png)

>[!NOTE]
>
>De toename van het aantal quarantines is een normaal effect dat gerelateerd is aan de &quot;slijtage&quot; van de database. Als de levensduur van een e-mailadres bijvoorbeeld wordt beschouwd als drie jaar en de tabel met ontvangers elk jaar met 50% toeneemt, kan de toename van quarantaine als volgt worden berekend:
>
>Eind van Jaar 1: (1 &#42; 0.33)/(1+0.5)=22%.
>
>Eind van Jaar 2: (1.22 &#42; 0.33) + 0.33)/(1.5+0.75)=32.5%.

### Identificeer quarantined adressen in leveringsrapporten {#identifying-quarantined-addresses-in-delivery-reports}

De volgende rapporten verstrekken informatie over de adressen in quarantaine:

* Voor elke levering, toont het **[!UICONTROL Delivery summary]** rapport het aantal adressen in quarantaine in het leveringsdoel. Het toont:

   * het aantal adressen dat tijdens de afleveringsanalyse in quarantaine wordt geplaatst;

   * Het aantal adressen die in quarantaine na de leveringsactie worden geplaatst.

* Het **[!UICONTROL Non-deliverables and bounces]** -rapport bevat informatie over de adressen in quarantaine, de typen fouten die zijn aangetroffen, enzovoort, en een uitsplitsing naar mislukking per domein.

U kunt deze informatie voor alle leveringen van het platform (**[!UICONTROL Home page > Reports]**) of voor een specifieke levering opzoeken. U kunt ook aangepaste rapporten maken en de informatie selecteren die moet worden weergegeven.

### Identificeer quarantined adressen voor een ontvanger {#identifying-quarantined-addresses-for-a-recipient}

U kunt de status van het e-mailadres van elke ontvanger opzoeken. Selecteer hiertoe het ontvangende profiel en klik op de tab **[!UICONTROL Deliveries]** . Voor alle leveringen aan die ontvanger, kunt u te weten komen of het ontbroken adres, tijdens analyse in quarantined, enz. was. Voor elke map kunt u alleen de ontvangers weergeven van wie het e-mailadres in quarantaine staat. Hiervoor gebruikt u het toepassingsfilter **[!UICONTROL Quarantined email address]** .

![](assets/tech_quarant_recipients_filter.png)


## Voorwaarden voor verzending van een adres naar quarantaine {#conditions-for-sending-an-address-to-quarantine}

Adobe Campaign beheert quarantaine volgens het type van de leveringsmislukking en de reden die tijdens de kwalificatie van foutenmeldingen (zie [ wordt toegewezen de postkwalificatie van de Stounce ](understanding-delivery-failures.md#bounce-mail-qualification) en [ de mislukkingstypen en redenen van de Levering ](understanding-delivery-failures.md#delivery-failure-types-and-reasons)).

* **Genegeerde fout**: bij genegeerde fouten wordt een adres niet in quarantaine geplaatst.
* **Harde fout**: het desbetreffende e-mailadres wordt onmiddellijk in quarantaine geplaatst.
* **Zachte fout**: bij zachte fouten wordt het adres niet direct in quarantaine geplaatst, maar neemt het aantal fouten op de foutenteller toe. Voor meer op dit, zie [ Zacht foutenbeheer ](#soft-error-management).

Als een gebruiker een e-mail als spam ([ kwalificeert koppelt lijn ](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html?lang=nl-NL#feedback-loops)), wordt het bericht automatisch opnieuw gericht naar een technische brievenbus die door Adobe wordt geleid. Het e-mailadres van de gebruiker wordt vervolgens automatisch in quarantaine geplaatst met de status **[!UICONTROL Denylisted]**. Deze status verwijst alleen naar het adres, het profiel staat niet op de lijst van gewezen personen, zodat de gebruiker SMS-berichten en pushberichten blijft ontvangen.

>[!NOTE]
>
>Quarantaine in Adobe Campaign is hoofdlettergevoelig. Zorg dat u de e-mailadressen in kleine letters importeert, zodat ze later niet opnieuw worden getarget.

In de lijst van quarantined adressen (zie [ het identificeren van quarantined adressen voor het volledige platform ](#identifying-quarantined-addresses-for-the-entire-platform)), wijst het **[!UICONTROL Error reason]** gebied erop waarom het geselecteerde adres in quarantaine werd geplaatst.

![](assets/tech_quarant_error_reasons.png)

### Beheer van zachte fouten {#soft-error-management}

In tegenstelling tot harde fouten, verzenden de zachte fouten onmiddellijk geen adres naar quarantaine, maar zij verhogen in plaats daarvan een foutenteller.

De pogingen zullen tijdens de [ leveringsduur ](../../delivery/using/steps-sending-the-delivery.md#defining-validity-period) worden uitgevoerd. Wanneer de foutenteller de grenswaarde bereikt, wordt het adres in quarantaine geplaatst. Voor meer op dit, verwijs naar [ probeert na een tijdelijke mislukking van de levering ](understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure).

De foutenteller wordt opnieuw geïnitialiseerd als de laatste significante fout meer dan 10 dagen geleden voorkwam. De adresstatus verandert dan in **Geldig** en het wordt geschrapt van de lijst van quarantines door het [ schoonmaakbeurt van het Gegevensbestand ](../../production/using/database-cleanup-workflow.md) werkschema.


Voor ontvangen of hybride installaties, als u aan [ Verbeterde MTA ](sending-with-enhanced-mta.md) hebt bevorderd, is het maximumaantal uit te voeren pogingen in het geval van **[!UICONTROL Erroneous]** status en de minimumvertraging tussen pogingen nu gebaseerd op hoe goed IP zowel historisch als momenteel bij een bepaald domein uitvoert.

Voor on-premise installaties en ontvangen/hybride installaties die de erfenis MTA van de Campagne gebruiken, kunt u het aantal fouten en de periode tussen twee fouten wijzigen. Om dit te doen, verander de overeenkomstige montages in de [ plaatsingstovenaar ](../../installation/using/deploying-an-instance.md) (**[!UICONTROL Email channel]** > **[!UICONTROL Advanced parameters]**) of [ op het leveringsniveau ](../../delivery/using/steps-sending-the-delivery.md#configuring-retries).


## Een adres uit quarantaine verwijderen {#removing-a-quarantined-address}

### Automatische updates {#unquarantine-auto}

Adressen die specifieke voorwaarden aanpassen worden automatisch geschrapt van de quarantainelijst door het [ schoonmaakbeurt ](../../production/using/database-cleanup-workflow.md) werkschema van het Gegevensbestand.

De adressen worden automatisch verwijderd uit de quarantainelijst in de volgende gevallen:

* Adressen in de status **[!UICONTROL With errors]** worden na een geslaagde levering uit de quarantainelijst verwijderd.
* Adressen in een status **[!UICONTROL With errors]** worden uit de quarantainelijst verwijderd als de laatste zachte stuit meer dan 10 dagen geleden plaatsvond. Voor meer op softfoutenbeheer, zie [ deze sectie ](#soft-error-management).
* Adressen in een **[!UICONTROL With errors]** -status die met de **[!UICONTROL Mailbox full]** -fout zijn gemarkeerd, worden na 30 dagen uit de quarantainelijst verwijderd.

De status verandert vervolgens in **[!UICONTROL Valid]** .

>[!IMPORTANT]
>
>Ontvangers met een adres in de status **[!UICONTROL Quarantine]** of **[!UICONTROL Denylisted]** worden nooit verwijderd, zelfs niet als ze een e-mail ontvangen.

### Handmatige updates {#unquarantine-manual}

U kunt een adres ook handmatig uit de quarantaine verwijderen. Als u een adres handmatig uit de quarantainelijst wilt verwijderen, wijzigt u de status in **[!UICONTROL Valid]** van het knooppunt **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]** .

![](assets/tech_quarant_error_status.png)

### Bulkupdates {#unquarantine-bulk}

U zou bulkupdates op de quarantainelijst, bijvoorbeeld in het geval van een ISP stroomonderbreking kunnen moeten uitvoeren. In dat geval worden e-mails ten onrechte als bonnen gemarkeerd omdat ze niet met succes aan de ontvanger kunnen worden bezorgd. Deze adressen moeten uit de quarantainelijst worden verwijderd.

Om dit te doen, creeer een werkschema en voeg een **[!UICONTROL Query]** activiteit op uw quarantainetabel toe om alle beïnvloede ontvangers uit te filteren. Als deze eenmaal zijn geïdentificeerd, kunnen ze uit de quarantainelijst worden verwijderd en worden opgenomen in toekomstige e-mailleveringen voor campagnes.

Hieronder volgen de geadviseerde richtlijnen voor deze vraag:

* Voor Campaign Classic v7-omgevingen met informatie over de regel Inbound-e-mail in het veld **[!UICONTROL Error text]** van de quarantainelijst:

   * **tekst van de Fout (quarantainetekst)** bevat &quot;Momen_Code10_InvalidRecipient&quot;
   * **E-maildomein (@domein)** is gelijk aan domain1.com OF **E-maildomein (@domein)** gelijk aan domain2.com OF **E-maildomein (@domein)** gelijk aan domain3.com
   * **status van de Update (@lastModified)** op of na `MM/DD/YYYY HH:MM:SS AM`
   * **status van de Update (@lastModified)** op of vóór `MM/DD/YYYY HH:MM:SS PM`

* Voor Campaign Classic v7-instanties met SMTP-stuitresponsinformatie in het veld **[!UICONTROL Error text]** van de quarantainelijst:

   * **de tekst van de Fout (quarantainetekst)** bevat &quot;550-5.1.1&quot;EN **Tekst van de Fout (quarantainetekst)** bevat &quot;support.ISP.com&quot;

  waar &quot;support.ISP.com&quot; kan zijn: bijvoorbeeld &quot;support.apple.com&quot; of &quot;support.google.com&quot;

   * **status van de Update (@lastModified)** op of na `MM/DD/YYYY HH:MM:SS AM`
   * **status van de Update (@lastModified)** op of vóór `MM/DD/YYYY HH:MM:SS PM`

Als u de lijst met betrokken ontvangers hebt, voegt u een **[!UICONTROL Update data]** -activiteit toe om de status van hun e-mailadres in te stellen op **[!UICONTROL Valid]** , zodat ze uit de quarantainelijst worden verwijderd via de **[!UICONTROL Database cleanup]** -workflow. U kunt ze ook gewoon uit de quarantainetabel verwijderen.

## Push notification quarantines {#push-notification-quarantines}

Het quarantainemechanisme voor pushmeldingen is over het algemeen hetzelfde als het algemene proces. Bepaalde fouten worden echter anders beheerd voor pushberichten. Voor bepaalde fouten in de software worden bijvoorbeeld geen pogingen opnieuw uitgevoerd binnen dezelfde levering. De specifieke kenmerken voor pushmeldingen worden hieronder weergegeven. Het mechanisme voor opnieuw proberen (aantal pogingen, frequentie) is hetzelfde als voor e-mailberichten.

De items die in quarantaine worden geplaatst, zijn apparaattokens.

### iOS quarantaine {#ios-quarantine}

Met het HTTP/V2-protocol kunt u rechtstreeks feedback geven en de status van elke push-levering bepalen. Als de HTTP/V2-protocolconnector wordt gebruikt, wordt de feedbackservice niet meer aangeroepen door de **[!UICONTROL mobileAppOptOutMgt]** -workflow. Een token wordt als niet-geregistreerd beschouwd wanneer een mobiele toepassing wordt verwijderd of opnieuw wordt geïnstalleerd.

Synchroon, als APNs een &quot;unregistered&quot;status voor een bericht terugkeert, zal het doelteken onmiddellijk in quarantaine worden geplaatst.

<table> 
 <tbody> 
  <tr> 
   <td> <strong> Scenario </strong><br /> </td> 
   <td> <strong> Status </strong><br /> </td> 
   <td> <strong> het bericht van de Fout </strong><br /> </td> 
   <td> <strong> Type van Mislukking </strong><br /> </td> 
   <td> <strong> reden van de Mislukking </strong><br /> </td> 
   <td> <strong> opnieuw </strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Gericht apparaat aangedreven op <br /> </td> 
   <td> OK<br /> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Gericht apparaat aangedreven weg <br /> </td> 
   <td> OK<br /> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Gebruiker maakt berichten voor de toepassing onbruikbaar <br /> </td> 
   <td> OK<br /> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Berichtaanmaak/analysefase - lading te groot <br /> </td> 
   <td> Fout <br /> </td> 
   <td> Payload te lang <br /> </td> 
   <td> Zacht <br /> </td> 
   <td> Geweigerd <br /> </td> 
   <td> Nee<br /> </td> 
  </tr> 
  <tr> 
   <td> Berichtaanmaak/analysefase - onverwachte inhoudsopmaakkwestie <br /> </td> 
   <td> Fout <br /> </td> 
   <td> Diverse foutenmeldingen volgens de fout <br /> </td> 
   <td> Zacht <br /> </td> 
   <td> Ongedefinieerd <br /> </td> 
   <td> Nee<br /> </td> 
  </tr> 
  <tr> 
   <td> Certificaatprobleem (wachtwoord, beschadiging, enz.) en testverbinding met APNs-uitgave <br /> </td> 
   <td> Fout <br /> </td> 
   <td> Diverse foutenmeldingen volgens de fout <br /> </td> 
   <td> Zacht <br /> </td> 
   <td> Geweigerd <br /> </td> 
   <td> Nee<br /> </td> 
  </tr> 
  <tr> 
   <td> Netwerkverbinding verloren tijdens verzenden <br /> </td> 
   <td> Fout <br /> </td> 
   <td> Verbindingsfout <br /> </td> 
   <td> Ongedefinieerd <br /> </td> 
   <td> Onbereikbaar <br /> </td> 
   <td> Ja<br /> </td> 
  </tr> 
  <tr> 
   <td> APNs berichtverwerping: Unregistration <br /> de gebruiker heeft de toepassing verwijderd of het teken is verlopen <br /> </td> 
   <td> Fout <br /> </td> 
   <td> Niet geregistreerd <br /> </td> 
   <td> Hard <br /> </td> 
   <td> Onbekende gebruiker <br /> </td> 
   <td> Nee<br /> </td> 
  </tr> 
  <tr> 
   <td> APNs berichtverwerping: alle andere fouten <br /> </td> 
   <td> Fout <br /> </td> 
   <td> De oorzaak van de foutenverwerping zal in het foutenbericht <br /> aanwezig zijn </td> 
   <td> Zacht <br /> </td> 
   <td> Geweigerd <br /> </td> 
   <td> Nee<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Android quarantaine {#android-quarantine}

**voor Android V1**

Voor elke melding ontvangt Adobe Campaign de synchrone fouten rechtstreeks van de FCM-server. De campagne van de Adobe behandelt hen op de vlucht en produceert harde of zachte fouten volgens de strengheid van de fout en de pogingen kunnen worden uitgevoerd:

* Payloadlengte overschreden, verbindingsprobleem, probleem met beschikbaarheid van service: opnieuw uitgevoerd, soft error, reden van fout is **[!UICONTROL Refused]** .
* Apparaatquota overschreden: geen nieuwe poging, soft error, reden van mislukking is **[!UICONTROL Refused]** .
* Ongeldige of niet-geregistreerde token, onverwachte fout, probleem met afzenderaccount: geen nieuwe poging, harde fout, reden van mislukking is **[!UICONTROL Refused]** .

De **[!UICONTROL mobileAppOptOutMgt]** werkschemalooppas om de 6 uur om de **AppSubscriptionRcp** lijst bij te werken. Voor de tekenen die niet geregistreerd of niet meer geldig worden verklaard, wordt het gebied **Gehandicapten** geplaatst aan **Waar** en het abonnement verbonden aan dat apparatenteken zal automatisch van toekomstige leveringen worden uitgesloten.

Tijdens de leveringsanalyse, worden alle apparaten die van het doel worden uitgesloten automatisch toegevoegd aan de **excludeLogAppSubRcp** lijst.

>[!NOTE]
>
>Voor klanten die de schakelaar Baidu gebruiken, zijn hier de verschillende soorten fouten:
>
>* Verbindingsprobleem aan het begin van de levering: type fout **[!UICONTROL Undefined]**, reden mislukt **[!UICONTROL Unreachable]** , wordt opnieuw geprobeerd.
>* Verbinding die tijdens een levering verloren gaat: zachte fout, reden van mislukking **[!UICONTROL Refused]**, wordt opnieuw geprobeerd wordt uitgevoerd.
>* Synchrone fout die door Baidu tijdens het verzenden is geretourneerd: harde fout, reden van mislukking **[!UICONTROL Refused]**; opnieuw proberen wordt niet uitgevoerd.
>
>Adobe Campaign neemt om de 10 minuten contact op met de Baidu-server om de status van het verzonden bericht op te halen en werkt de weblogs bij. Als een bericht wordt verklaard zoals verzonden, wordt de status van het bericht in de uitzendingen geplaatst aan **[!UICONTROL Received]**. Als Baidu een fout declareert, wordt de status ingesteld op **[!UICONTROL Failed]** .

**voor Android V2**

Het Android V2-quarantainemechanisme gebruikt hetzelfde proces als Android V1. Hetzelfde geldt voor de abonnementen en uitsluitingen-update. Voor meer op dit verwijs naar [ Android V1 ](#android-quarantine) sectie.

<table> 
 <tbody> 
  <tr> 
   <td> <strong> Scenario </strong><br /> </td> 
   <td> <strong> Status </strong><br /> </td> 
   <td> <strong> het bericht van de Fout </strong><br /> </td> 
   <td> <strong> Type van Mislukking </strong><br /> </td> 
   <td> <strong> reden van de Mislukking </strong><br /> </td> 
   <td> <strong> opnieuw </strong><br /> </td> 
  </tr> 
  <tr> 
   <td> De verwezenlijking/de analysefase van het bericht: illegale sleutelwoorden die in de douanegebieden worden gebruikt <br /> </td> 
   <td> Fout <br /> </td> 
   <td> De volgende trefwoorden kunnen niet worden gebruikt: {1}<br /> </td> 
   <td> Zacht <br /> </td> 
   <td> </td> 
   <td> Nee<br /> </td> 
  </tr> 
  <tr> 
   <td> Berichtaanmaak/analysefase: lading te groot <br /> </td> 
   <td> Fout <br /> </td> 
   <td> De melding is te zwaar: {1} beetjes, terwijl slechts \ {2 \} geoorloofd is <br /> </td> 
   <td> Zacht <br /> </td> 
   <td> Geweigerd <br /> </td> 
   <td> Nee<br /> </td> 
  </tr> 
  <tr> 
   <td> Netwerkverbinding verloren tijdens verzenden <br /> </td> 
   <td> Fout <br /> </td> 
   <td> Geen reactie van de Firebase Cloud Messaging-service op het adres: {1}<br /> </td> 
   <td> Zacht <br /> </td> 
   <td> Onbereikbaar <br /> </td> 
   <td> Ja<br /> </td> 
  </tr> 
  <tr> 
   <td> Afkeuring van FCM-berichten: De FCM-server is tijdelijk niet beschikbaar (bijvoorbeeld met time-outs). <br /> </td> 
   <td> Fout <br /> </td> 
   <td> De Firebase Cloud Messaging-service is tijdelijk niet beschikbaar <br /> </td> 
   <td> Zacht <br /> </td> 
   <td> Onbereikbaar <br /> </td> 
   <td> Ja<br /> </td> 
  </tr> 
  <tr> 
   <td> Afkeuring van FCM-berichten: Fout bij het verifiëren van de senderaccount <br /> </td> 
   <td> Fout <br /> </td> 
   <td> Kan de ontwikkelaarsaccount niet identificeren. Controleer uw id en wachtwoord <br /> </td> 
   <td> Zacht <br /> </td> 
   <td> Geweigerd <br /> </td> 
   <td> Nee<br /> </td> 
  </tr> 
  <tr> 
   <td> Afwijzing van FCM-bericht: Apparaatquota overschreden <br /> </td> 
   <td> Fout <br /> </td> 
   <td> </td> 
   <td> Zacht <br /> </td> 
   <td> Geweigerd <br /> </td> 
   <td> Ja<br /> </td> 
  </tr> 
  <tr> 
   <td> Afwijzing van FCM-bericht: Ongeldige registratie / niet geregistreerd <br /> </td> 
   <td> Fout <br /> </td> 
   <td> </td> 
   <td> Hard <br /> </td> 
   <td> Onbekende gebruiker <br /> </td> 
   <td> Nee<br /> </td> 
  </tr> 
  <tr> 
   <td> Afkeuring van FCM-berichten: Alle andere fouten <br /> </td> 
   <td> Fout <br /> </td> 
   <td> De Firebase Cloud Messaging-server heeft een onverwachte foutcode geretourneerd: {1} </td> 
   <td> </td> 
   <td> Geweigerd <br /> </td> 
   <td> Nee<br /> </td> 
  </tr> 
    <tr> 
   <td> Afkeuring van FCM-berichten: Ongeldig argument <br /> </td> 
   <td> Fout <br /> </td> 
   <td> INVALID_ARGUMENT </td> 
   <td> Genegeerd</td> 
   <td> Ongedefinieerd <br /> </td> 
   <td> Nee<br /> </td> 
  </tr>
    <tr> 
   <td> Afkeuring van FCM-berichten: Fout bij verificatie van derden <br /> </td> 
   <td> Fout <br /> </td> 
   <td> THIRD_PARTY_AUTH_ERROR </td> 
   <td> Genegeerd</td>
   <td> Geweigerd <br /> </td> 
   <td> Ja<br /> </td> 
  </tr>
    <tr> 
   <td> Afkeuring van FCM-berichten: Afzender-id komt niet overeen <br /> </td> 
   <td> Fout <br /> </td> 
   <td> SENDER_ID_MISMATCH </td> 
   <td> Zacht</td>
   <td> Onbekende gebruiker <br /> </td> 
   <td> Nee<br /> </td> 
  </tr>
    <tr> 
   <td> Afwijzing van FCM-bericht: Niet geregistreerd <br /> </td> 
   <td> Fout <br /> </td>
   <td> ONGEREGISTREERD </td> 
   <td> Hard</td> 
   <td> Onbekende gebruiker <br /> </td> 
   <td> Nee<br /> </td> 
  </tr>
    <tr> 
   <td> Afkeuring van FCM-berichten: Intern <br /> </td> 
   <td> Fout <br /> </td> 
   <td> INTERN </td> 
   <td> Genegeerd</td> 
   <td> Geweigerd <br /> </td> 
   <td> Ja<br /> </td> 
  </tr>
    <tr> 
   <td> Afkeuring van FCM-berichten: Niet beschikbaar <br /> </td> 
   <td> Fout <br /> </td> 
   <td> NIET BESCHIKBAAR</td> 
   <td> Genegeerd</td> 
   <td> Geweigerd <br /> </td> 
   <td> Ja<br /> </td> 
  </tr>
    <tr> 
   <td> Afwijzing van FCM-bericht: onverwachte foutcode <br /> </td> 
   <td> Fout <br /> </td> 
   <td> onverwachte foutcode</td> 
   <td> Genegeerd</td> 
   <td> Geweigerd <br /> </td> 
   <td> Nee<br /> </td> 
  </tr>
  <tr> 
   <td> Verificatie: Verbindingsprobleem <br /> </td> 
   <td> Fout <br /> </td> 
   <td> Kan geen verbinding maken met verificatieserver </td> 
   <td> Genegeerd</td>
   <td> Geweigerd <br /> </td> 
   <td> Ja<br /> </td> 
  </tr>
    <tr> 
   <td> Authentificatie: Onbevoegde cliënt of werkingsgebied in verzoek.<br /> </td> 
   <td> Fout <br /> </td> 
   <td> onbevoegd_client </td> 
   <td> Genegeerd</td>
   <td> Geweigerd <br /> </td> 
   <td> Nee<br /> </td> 
  </tr>
    <tr> 
   <td> Authentificatie: De cliënt is onbevoegd om toegangstokens terug te winnen gebruikend deze methode, of cliënt niet geautoriseerd voor om het even welk gevraagd werkingsgebied.<br /> </td> 
   <td> Fout <br /> </td> 
   <td> onbevoegd_client </td> 
   <td> Genegeerd</td>
   <td> Geweigerd <br /> </td> 
   <td> Nee<br /> </td> 
  </tr>
    <tr> 
   <td> Verificatie: Toegang geweigerd <br /> </td> 
   <td> Fout <br /> </td>
   <td> access_deny</td> 
   <td> Genegeerd</td>
   <td> Geweigerd <br /> </td> 
   <td> Nee<br /> </td> 
  </tr>
    <tr> 
   <td> Verificatie: Ongeldige e-mail <br /> </td> 
   <td> Fout <br /> </td> 
   <td> invalid_Grant </td> 
   <td> Genegeerd</td> 
   <td> Geweigerd <br /> </td> 
   <td> Nee<br /> </td> 
  </tr>
    <tr> 
   <td> Verificatie: Ongeldige JWT <br /> </td> 
   <td> Fout <br /> </td> 
   <td> invalid_Grant </td> 
   <td> Genegeerd</td> 
   <td> Geweigerd <br /> </td> 
   <td> Nee<br /> </td> 
  </tr>
    <tr> 
   <td> Verificatie: ongeldige JWT-handtekening <br /> </td> 
   <td> Fout <br /> </td> 
   <td> invalid_Grant </td> 
   <td> Genegeerd</td> 
   <td> Geweigerd <br /> </td> 
   <td> Nee<br /> </td> 
  </tr>
    <tr> 
   <td> Verificatie: Ongeldig OAuth werkingsgebied of verstrekt het symbolische publiek van identiteitskaart <br /> </td> 
   <td> Fout <br /> </td> 
   <td> onbevoegd_client</td> 
   <td> Genegeerd</td> 
   <td> Geweigerd <br /> </td> 
   <td> Nee<br /> </td> 
  </tr>
    <tr> 
   <td> Verificatie: OAuth-client uitgeschakeld <br /> </td> 
   <td> Fout <br /> </td> 
   <td> disabled_client</td> 
   <td> Genegeerd</td> 
   <td> Geweigerd <br /> </td> 
   <td> Nee<br /> </td> 
  </tr>
 </tbody> 
</table>

## SMS-quarantines {#sms-quarantines}

**voor standaardschakelaars**

Het quarantainemechanisme voor SMS-berichten is over het algemeen hetzelfde als het algemene proces. Zie [ Ongeveer quarantines ](#about-quarantines). De specifieke kenmerken voor SMS worden hieronder weergegeven.

>[!NOTE]
>
>De **[!UICONTROL Delivery log qualification]** lijst is niet op de **Uitgebreide generische schakelaar SMPP** van toepassing.

<table> 
 <tbody> 
  <tr> 
   <td> <strong> Scenario </strong><br /> </td> 
   <td> <strong> Status </strong><br /> </td> 
   <td> <strong> het bericht van de Fout </strong><br /> </td> 
   <td> <strong> Type van Mislukking </strong><br /> </td> 
   <td> <strong> reden van de Mislukking </strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Verzonden naar de leverancier <br /> </td> 
   <td> Verzonden<br /> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Ontvangen op mobiele apparaten <br /> </td> 
   <td> Ontvangen <br /> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Fout die door de leverancier <br /> is teruggekeerd </td> 
   <td> Fout <br /> </td> 
   <td> Fout tijdens het ontvangen van gegevens (SR of MO) <br /> </td> 
   <td> Zacht <br /> </td> 
   <td> Onbereikbaar <br /> </td> 
  </tr> 
  <tr> 
   <td> Ongeldige MT-erkenning <br /> </td> 
   <td> Fout <br /> </td> 
   <td> Fout '{1}' tijdens het verwerken van het bevestigingskader voor het verzenden van vraag <br /> </td> 
   <td> Zacht <br /> </td> 
   <td> Onbereikbaar <br /> </td> 
  </tr> 
  <tr> 
   <td> Fout tijdens verzenden van MT <br /> </td> 
   <td> Fout <br /> </td> 
   <td> Fout bij verzenden van berichten <br /> </td> 
   <td> Zacht <br /> </td> 
   <td> Onbereikbaar <br /> </td> 
  </tr> 
 </tbody> 
</table>

**voor de Uitgebreide generische schakelaar SMPP**

Wanneer het gebruiken van het protocol SMPP om de berichten van SMS te verzenden, wordt het foutenbeheer verschillend behandeld. Voor meer informatie over de Uitgebreide generische schakelaar SMPP, verwijs naar [ deze pagina ](sms-set-up.md#creating-an-smpp-external-account).

De schakelaar SMPP wint gegevens van het bericht van SR (Status Report) terug dat gebruikend regelmatige uitdrukkingen (regexes) is teruggekeerd om zijn inhoud te filtreren. Deze gegevens worden vervolgens vergeleken met de informatie in de tabel **[!UICONTROL Delivery log qualification]** (beschikbaar via het menu **[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Non deliverables Management]** ).

Alvorens een nieuw type van fout wordt gekwalificeerd, wordt de mislukkingsreden altijd geplaatst aan **Verworpen** door gebrek.

>[!NOTE]
>
>De fouttypen en -redenen zijn gelijk aan die voor e-mailberichten. Zie [ de mislukkingstypes en redenen van de Levering ](understanding-delivery-failures.md#delivery-failure-types-and-reasons).
>
>Vraag uw leverancier om een lijst van status en foutencodes om juiste mislukkingstypes en redenen voor mislukking in de de kwalificatielijst van het Logboek van de Levering te plaatsen.

Voorbeeld van een gegenereerd bericht:

```
SR Generic DELIVRD 000|#MESSAGE#
```

* Alle foutenmeldingen beginnen met **SR** om de foutencodes van SMS van e-mailfoutencodes te onderscheiden.
* Het tweede deel (**Algemeen** in dit voorbeeld) van het foutenbericht verwijst naar de naam van de implementatie SMSC zoals die in het **[!UICONTROL SMSC implementation name]** gebied van de externe rekening van SMS wordt bepaald. Zie [deze pagina](sms-set-up.md#creating-an-smpp-external-account).

  Omdat dezelfde foutcode voor elke provider een andere betekenis kan hebben, kunt u in dit veld weten welke provider de foutcode heeft gegenereerd. U kunt de fout dan vinden in de relevante documentatie van de leverancier.

* Het derde deel (**LEVERT** in dit voorbeeld) van het foutenbericht beantwoordt aan de statuscode die van SR wordt teruggewonnen gebruikend de regex van de statusextractie die in de externe rekening van SMS wordt bepaald.

  Deze regex wordt opgegeven op het tabblad **[!UICONTROL SMSC specificities]** van de externe account. Zie [deze pagina](sms-set-up.md#creating-an-smpp-external-account).

  ![](assets/tech_quarant_error_regex.png)

  Door gebrek, haalt regex de **staat:** gebied zoals die door de **wordt bepaald Bijlage B** sectie van de **3.4 specificatie van SMPP**.

* Het vierde deel (**000** in dit voorbeeld) van het foutenbericht beantwoordt aan de foutencode die uit SR wordt gehaald gebruikend de de extractieregex van de foutencode die in de externe rekening van SMS wordt bepaald.

  Deze regex wordt opgegeven op het tabblad **[!UICONTROL SMSC specificities]** van de externe account. Zie [deze pagina](sms-set-up.md#creating-an-smpp-external-account).

  Door gebrek, haalt regex **err:** gebied zoals die door de **wordt bepaald Bijlage B** sectie van de **4&rbrace; SMPP 3.4 specificatie**.

* Alles wat na het buissymbool (|) komt wordt slechts getoond in de **[!UICONTROL First text]** kolom van de **[!UICONTROL Delivery log qualification]** lijst. Deze inhoud wordt altijd vervangen door **#MESSAGE#** nadat het bericht is genormaliseerd. Dit proces voorkomt het hebben van veelvoudige ingangen voor gelijkaardige fouten en is het zelfde als voor e-mail. Voor meer op dit, zie [ de postkwalificatie van de Stuiteren ](understanding-delivery-failures.md#bounce-mail-qualification).

De uitgebreide generische schakelaar SMPP past heuristisch toe om verstandige standaardwaarden te vinden: als de status met **LEVERT** begint, wordt het beschouwd als een succes omdat het de gemeenschappelijke statussen **LEVERT** of **LEVERDE** aanpast die door de meeste leveranciers worden gebruikt. Elke andere status leidt tot een harde fout.
