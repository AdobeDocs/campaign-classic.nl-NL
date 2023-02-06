---
product: campaign
title: Quarantainebeheer begrijpen
description: Quarantainebeheer begrijpen
feature: Monitoring, Deliverability
exl-id: cfd8f5c9-f368-4a31-a1e2-1d77ceae5ced
source-git-commit: c84f48ebdd66524e8dd6c39c88ae29565d11c9b2
workflow-type: tm+mt
source-wordcount: '2997'
ht-degree: 9%

---

# Quarantainebeheer begrijpen{#understanding-quarantine-management}

![](../../assets/common.svg)

Adobe Campaign beheert een lijst met in quarantaine geplaatste adressen. Ontvangers van wie het adres in quarantaine is geplaatst, worden standaard tijdens de leveringsanalyse uitgesloten, en zullen niet doelgericht worden benaderd. Een e-mailadres kan in quarantaine worden geplaatst, bijvoorbeeld, wanneer het postvak vol is of als het adres niet bestaat. In elk geval voldoet de quarantaineprocedure aan de hieronder beschreven specifieke voorschriften.

>[!NOTE]
>
>Deze sectie is van toepassing op online kanalen: e-mail, SMS, pushmelding.

## De levering optimaliseren via quarantainebeheer {#optimizing-your-delivery-through-quarantines}

De profielen waarvan e-mailadressen of telefoonaantal in quarantaine zijn zijn automatisch uitgesloten tijdens berichtvoorbereiding (zie [Identificeer quarantined adressen voor een levering](#identifying-quarantined-addresses-for-a-delivery)). Hierdoor wordt de levering versneld, omdat het foutenpercentage een belangrijk effect heeft op de leveringssnelheid.

Sommige internetproviders beschouwen e-mails automatisch als spam als het aantal ongeldige adressen te hoog is. Met quarantaine kunt u dus voorkomen dat u door deze providers aan de lijst van gewezen personen wordt toegevoegd.

Bovendien zijn de verzendkosten voor sms-berichten lager doordat onjuiste telefoonnummers van de levering worden uitgesloten.

Raadpleeg [deze pagina](delivery-best-practices.md) voor meer informatie over de best practices voor het beveiligen en optimaliseren van uw leveringen.

### Quarantine versus lijst van gewezen personen {#quarantine-vs-denylist}

Quarantaine en lijst van gewezen personen zijn niet van toepassing op hetzelfde object:

* **Quarantine** alleen van toepassing op een **adres** (of telefoonnummer, enz.), niet naar het profiel zelf. Een profiel waarvan het e-mailadres in quarantaine is geplaatst, kan bijvoorbeeld zijn profiel bijwerken en een nieuw adres invoeren. Dit profiel kan dan opnieuw worden geactiveerd door leveringsacties. Eveneens, als twee profielen gebeuren om het zelfde telefoonaantal te hebben, zullen zij allebei worden beïnvloed als het aantal quarantined is.

   De in quarantaine geplaatste adressen of telefoonaantallen worden getoond in [uitsluitingslogboeken](#identifying-quarantined-addresses-for-a-delivery) (voor levering) of in de [quarantainelijst](#identifying-quarantined-addresses-for-the-entire-platform) (voor het gehele platform).

* Aan de slag **lijst van gewezen personen** anderzijds zal **profiel** niet langer het doelwit is van de levering, bijvoorbeeld na een abonnement (opt-out), voor een bepaald kanaal. Als een profiel op de lijst van gewezen personen voor het e-mailkanaal bijvoorbeeld twee e-mailadressen heeft, worden beide adressen van levering uitgesloten.

   U kunt controleren of een profiel op de lijst van gewezen personen voor een of meer kanalen in het dialoogvenster **[!UICONTROL No longer contact]** van het profiel **[!UICONTROL General]** tab. Zie [deze sectie](../../platform/using/editing-a-profile.md#general-tab).

>[!NOTE]
>
>Quarantine bevat een **[!UICONTROL Denylisted]** status, die van toepassing is wanneer ontvangers uw bericht melden als spam of op een SMS-bericht reageren met een trefwoord zoals &quot;STOP&quot;. In dat geval wordt het betreffende adres of telefoonnummer van het profiel verzonden naar quarantaine met de **[!UICONTROL Denylisted]** status. Voor meer informatie over het beheren van SMS-berichten van STOP raadpleegt u [deze sectie](../../delivery/using/sms-send.md#processing-inbound-messages).

## In quarantaine geplaatste adressen identificeren {#identifying-quarantined-addresses}

Adressen kunnen in quarantaine worden geplaatst voor een specifieke levering of voor het volledige platform.

### Identificeer quarantined adressen voor een levering {#identifying-quarantined-addresses-for-a-delivery}

De gekwantificeerde adressen voor een specifieke levering zijn vermeld tijdens de leveringsvoorbereidingsfase, in de leveringslogboeken van het leveringsdashboard (zie [Leveringslogboeken en geschiedenis](delivery-dashboard.md#delivery-logs-and-history)).

### Identificeer quarantined adressen voor het volledige platform {#identifying-quarantined-addresses-for-the-entire-platform}

De beheerders kunnen van de adressen in quarantaine voor het volledige platform van een lijst maken **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]** knooppunt.

>[!NOTE]
>
>Dit menu bevat quarantaine-elementen voor **e-mail**-, **sms**- en **pushberichtkanalen**.

Voor elk adres is de volgende informatie beschikbaar:

![](assets/tech_quarant_npai.png)

>[!NOTE]
>
>De toename van het aantal quarantines is een normaal effect dat gerelateerd is aan de &quot;slijtage&quot; van de database. Als de levensduur van een e-mailadres bijvoorbeeld wordt beschouwd als drie jaar en de tabel met ontvangers elk jaar met 50% toeneemt, kan de toename van quarantaine als volgt worden berekend:
>
>Einde van jaar 1: 1&#42;0,33)/(1+0,5)=22%.
>
>Einde van jaar 2: (1,22)&#42;0,33)+0,33)/(1,5+0,75)=32,5%.

### Identificeer quarantined adressen in leveringsrapporten {#identifying-quarantined-addresses-in-delivery-reports}

De volgende rapporten verstrekken informatie over de adressen in quarantaine:

* Voor elke levering **[!UICONTROL Delivery summary]** het rapport toont het aantal adressen in quarantaine in het leveringsdoel. Het toont:

   * het aantal adressen dat tijdens de afleveringsanalyse in quarantaine wordt geplaatst;

   * Het aantal adressen die in quarantaine na de leveringsactie worden geplaatst.

* De **[!UICONTROL Non-deliverables and bounces]** het rapport toont informatie over de adressen in quarantaine, de types van aangetroffen fout, enz., en een mislukkingsonderbreking door domein.

U kunt deze informatie opzoeken voor alle leveringen van het platform (**[!UICONTROL Home page > Reports]**) of voor een specifieke levering. U kunt ook aangepaste rapporten maken en de informatie selecteren die moet worden weergegeven.

### Identificeer quarantined adressen voor een ontvanger {#identifying-quarantined-addresses-for-a-recipient}

U kunt de status van het e-mailadres van elke ontvanger opzoeken. Selecteer hiertoe het ontvangende profiel en klik op de knop **[!UICONTROL Deliveries]** tab. Voor alle leveringen aan die ontvanger, kunt u te weten komen of het ontbroken adres, tijdens analyse in quarantined, enz. was. Voor elke map kunt u alleen de ontvangers weergeven van wie het e-mailadres in quarantaine staat. Om dit te doen, gebruik **[!UICONTROL Quarantined email address]** toepassingsfilter.

![](assets/tech_quarant_recipients_filter.png)


## Voorwaarden voor het in quarantaine plaatsen van een adres {#conditions-for-sending-an-address-to-quarantine}

Adobe Campaign beheert quarantaine volgens het type van leveringsmislukking en de reden die tijdens de kwalificatie van foutenmeldingen wordt toegewezen (zie [Bounce mail-kwalificatie](understanding-delivery-failures.md#bounce-mail-qualification) en [Typen leveringsfouten en redenen](understanding-delivery-failures.md#delivery-failure-types-and-reasons)).

* **Genegeerde fout**: bij genegeerde fouten wordt een adres niet in quarantaine geplaatst.
* **Harde fout**: het desbetreffende e-mailadres wordt onmiddellijk in quarantaine geplaatst.
* **Zachte fout**: bij zachte fouten wordt het adres niet direct in quarantaine geplaatst, maar neemt het aantal fouten op de foutenteller toe. Zie voor meer informatie [Beheer van zachte fouten](#soft-error-management).

Als een gebruiker een e-mailbericht kwalificeert als spam ([feedbacklus](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#feedback-loops)), wordt het bericht automatisch opnieuw gericht naar een technische brievenbus die door Adobe wordt beheerd. Het e-mailadres van de gebruiker wordt vervolgens automatisch in quarantaine geplaatst met de status **[!UICONTROL Denylisted]**. Deze status verwijst alleen naar het adres, het profiel staat niet op de lijst van gewezen personen, zodat de gebruiker SMS-berichten en pushberichten blijft ontvangen.

>[!NOTE]
>
>Quarantaine in Adobe Campaign is hoofdlettergevoelig. Zorg dat u de e-mailadressen in kleine letters importeert, zodat ze later niet opnieuw worden getarget.

In de lijst van quarantined adressen (zie [Het identificeren van quarantined adressen voor het volledige platform](#identifying-quarantined-addresses-for-the-entire-platform)), de **[!UICONTROL Error reason]** geeft aan waarom het geselecteerde adres in quarantaine is geplaatst.

![](assets/tech_quarant_error_reasons.png)

### Beheer van zachte fouten {#soft-error-management}

In tegenstelling tot harde fouten, verzenden de zachte fouten onmiddellijk geen adres naar quarantaine, maar zij verhogen in plaats daarvan een foutenteller.

Opnieuw proberen wordt uitgevoerd tijdens de [leveringsduur](../../delivery/using/steps-sending-the-delivery.md#defining-validity-period). Wanneer de foutenteller de grenswaarde bereikt, wordt het adres in quarantaine geplaatst. Raadpleeg voor meer informatie hierover [Retourneert na een tijdelijke leverfout](understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure).

De foutenteller wordt opnieuw geïnitialiseerd als de laatste significante fout meer dan 10 dagen geleden voorkwam. De adresstatus verandert vervolgens in **Geldig** en wordt door de [Database opschonen](../../production/using/database-cleanup-workflow.md) workflow.


Voor gehoste of hybride installaties, als u hebt geüpgraded naar de [Enhanced MTA](sending-with-enhanced-mta.md), het maximumaantal opnieuw uit te voeren pogingen in geval van **[!UICONTROL Erroneous]** status en de minimumvertraging tussen pogingen zijn nu gebaseerd op hoe goed IP zowel historisch als momenteel bij een bepaald domein presteert.

Voor on-premise installaties en ontvangen/hybride installaties die de erfenis MTA van de Campagne gebruiken, kunt u het aantal fouten en de periode tussen twee fouten wijzigen. Hiervoor wijzigt u de bijbehorende instellingen in het dialoogvenster [implementatiewizard](../../installation/using/deploying-an-instance.md) (**[!UICONTROL Email channel]** > **[!UICONTROL Advanced parameters]**) of [op het leveringsniveau](../../delivery/using/steps-sending-the-delivery.md#configuring-retries).


## Een adres uit quarantaine verwijderen {#removing-a-quarantined-address}

### Automatische updates {#unquarantine-auto}

Adressen die aan specifieke voorwaarden voldoen, worden automatisch uit de quarantainelijst verwijderd door de [Database opschonen](../../production/using/database-cleanup-workflow.md) workflow.

De adressen worden automatisch verwijderd uit de quarantainelijst in de volgende gevallen:

* Adressen in een **[!UICONTROL With errors]** de status wordt na een geslaagde levering uit de quarantainelijst verwijderd .
* Adressen in een **[!UICONTROL With errors]** de status wordt uit de quarantainelijst verwijderd als de laatste zachte stuit meer dan tien dagen geleden heeft plaatsgevonden . Zie voor meer informatie over softerror management [deze sectie](#soft-error-management).
* Adressen in een **[!UICONTROL With errors]** status die met de **[!UICONTROL Mailbox full]** De fout wordt na 30 dagen uit de quarantainelijst verwijderd.

Hun status verandert vervolgens in **[!UICONTROL Valid]**.

>[!IMPORTANT]
>
>Ontvangers met een adres in een **[!UICONTROL Quarantine]** of **[!UICONTROL Denylisted]** de status wordt nooit verwijderd, zelfs niet als ze een e-mail ontvangen.

### Handmatige updates {#unquarantine-manual}

U kunt een adres ook handmatig uit de quarantaine verwijderen. Als u een adres handmatig uit de quarantainelijst wilt verwijderen, wijzigt u de status in **[!UICONTROL Valid]** van de **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]** knooppunt.

![](assets/tech_quarant_error_status.png)

### Bulkupdates {#unquarantine-bulk}

U zou bulkupdates op de quarantainelijst, bijvoorbeeld in het geval van een ISP stroomonderbreking kunnen moeten uitvoeren. In dat geval worden e-mails ten onrechte als bonnen gemarkeerd omdat ze niet met succes aan de ontvanger kunnen worden bezorgd. Deze adressen moeten uit de quarantainelijst worden verwijderd.

Om dit te doen, creeer een werkschema en voeg toe **[!UICONTROL Query]** activiteit op uw quarantainetabel om alle getroffen ontvangers uit te filteren. Als deze eenmaal zijn geïdentificeerd, kunnen ze uit de quarantainelijst worden verwijderd en worden opgenomen in toekomstige e-mailleveringen voor campagnes.

Hieronder volgen de geadviseerde richtlijnen voor deze vraag:

* Voor Campaign Classic v7-omgevingen met informatie over de regels voor inkomende e-mail in de **[!UICONTROL Error text]** veld van de quarantainelijst:

   * **Fouttekst (quarantainetekst)** bevat &quot;Momen_Code10_InvalidRecipient&quot;
   * **E-maildomein (@domein)** is gelijk aan domain1.com OR **E-maildomein (@domein)** is gelijk aan domain2.com OR **E-maildomein (@domein)** is gelijk aan domain3.com
   * **Status bijwerken (@lastModified)** op of na MM/DD/YYYY HH:MM:SS AM
   * **Status bijwerken (@lastModified)** op of vóór MM/DD/YYYY HH:MM:SS PM

* Voor Campaign Classic v7-instanties met SMTP-responsgegevens voor stuiteren in het dialoogvenster **[!UICONTROL Error text]** veld van de quarantainelijst:

   * **Fouttekst (quarantainetekst)** bevat &quot;550-5.1.1&quot; EN **Fouttekst (quarantainetekst)** bevat &quot;support.ISP.com&quot;

   waar &quot;support.ISP.com&quot; kan zijn: bijvoorbeeld &quot;support.apple.com&quot; of &quot;support.google.com&quot;

   * **Status bijwerken (@lastModified)** op of na MM/DD/YYYY HH:MM:SS AM
   * **Status bijwerken (@lastModified)** op of vóór MM/DD/YYYY HH:MM:SS PM


Als u de lijst met betrokken ontvangers hebt, voegt u een **[!UICONTROL Update data]** activiteit om hun e-mailadresstatus in te stellen op **[!UICONTROL Valid]** zodat zij uit de quarantainelijst worden verwijderd door **[!UICONTROL Database cleanup]** workflow. U kunt ze ook gewoon uit de quarantainetabel verwijderen.

## Push notification quarantines {#push-notification-quarantines}

Het quarantainemechanisme voor pushmeldingen is over het algemeen hetzelfde als het algemene proces. Bepaalde fouten worden echter anders beheerd voor pushberichten. Voor bepaalde fouten in de software worden bijvoorbeeld geen pogingen opnieuw uitgevoerd binnen dezelfde levering. De specifieke kenmerken voor pushmeldingen worden hieronder weergegeven. Het mechanisme voor opnieuw proberen (aantal pogingen, frequentie) is hetzelfde als voor e-mailberichten.

De items die in quarantaine worden geplaatst, zijn apparaattokens.

### iOS quarantaine {#ios-quarantine}

Met het HTTP/V2-protocol kunt u rechtstreeks feedback geven en de status van elke push-levering bepalen. Als de HTTP/V2 protocolschakelaar wordt gebruikt, koppelt de dienst niet meer wordt geroepen door **[!UICONTROL mobileAppOptOutMgt]** workflow. Een token wordt als niet-geregistreerd beschouwd wanneer een mobiele toepassing wordt verwijderd of opnieuw wordt geïnstalleerd.

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
   <td> Certificaatafgifte (wachtwoord, beschadiging, enz.) en testverbinding met APNs-probleem<br /> </td> 
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
   <td> APNs-berichtafwijzing: Registratie ongedaan maken<br /> de gebruiker de toepassing heeft verwijderd of het token is verlopen<br /> </td> 
   <td> Mislukt<br /> </td> 
   <td> Niet geregistreerd<br /> </td> 
   <td> Hard<br /> </td> 
   <td> Gebruiker onbekend<br /> </td> 
   <td> Nee<br /> </td> 
  </tr> 
  <tr> 
   <td> APNs-berichtafwijzing: alle andere fouten<br /> </td> 
   <td> Mislukt<br /> </td> 
   <td> De oorzaak van de fout-afwijzing komt voor in het foutbericht<br /> </td> 
   <td> Zacht<br /> </td> 
   <td> Geweigerd<br /> </td> 
   <td> Nee<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Android-quarantaine {#android-quarantine}

**Voor Android V1**

Voor elke melding ontvangt Adobe Campaign de synchrone fouten rechtstreeks van de FCM-server. Met de Adobe-campagne worden ze direct afgehandeld en worden harde of zachte fouten gegenereerd op basis van de ernst van de fout. U kunt het opnieuw proberen:

* Lengte van lading overschreden, verbindingskwestie, de kwestie van de de dienstbeschikbaarheid: opnieuw uitgevoerd, soft error, failure reason **[!UICONTROL Refused]**.
* Apparaatquota overschreden: niet opnieuw proberen, soft error, error reason is **[!UICONTROL Refused]**.
* Ongeldige of niet-geregistreerde token, onverwachte fout, probleem met afzenderaccount: niet opnieuw proberen, harde fout, mislukkingsreden is **[!UICONTROL Refused]**.

De **[!UICONTROL mobileAppOptOutMgt]** werkstroom wordt elke 6 uur uitgevoerd om de **AppSubscriptionRcp** tabel. Voor tokens die niet zijn geregistreerd of niet meer geldig zijn, wordt het veld **Uitgeschakeld** is ingesteld op **Waar** en het abonnement op dat apparaattoken wordt automatisch uitgesloten van toekomstige leveringen.

Tijdens de leveringsanalyse, worden alle apparaten die van het doel worden uitgesloten automatisch toegevoegd aan **excludeLogAppSubRcp** tabel.

>[!NOTE]
>
>Voor klanten die de schakelaar Baidu gebruiken, zijn hier de verschillende soorten fouten:
>
>* Verbindingsprobleem aan het begin van de levering: fouttype **[!UICONTROL Undefined]**, reden van fout **[!UICONTROL Unreachable]**, wordt opnieuw geprobeerd.
>* Verbinding verloren tijdens een levering: soft error, error reason **[!UICONTROL Refused]**, wordt opnieuw geprobeerd.
>* Synchrone fout die door Baidu tijdens het verzenden is geretourneerd: harde fout, reden van fout **[!UICONTROL Refused]**, wordt het opnieuw proberen niet uitgevoerd.
>
>Adobe Campaign neemt om de 10 minuten contact op met de Baidu-server om de status van het verzonden bericht op te halen en werkt de weblogs bij. Als een bericht wordt verklaard zoals verzonden, wordt het statuut van het bericht in de uitzendingen geplaatst aan **[!UICONTROL Received]**. Als Baidu een fout declareert, wordt de status ingesteld op **[!UICONTROL Failed]**.

**Voor Android V2**

Het Android V2-quarantainemechanisme gebruikt hetzelfde proces als Android V1. Hetzelfde geldt voor de update voor abonnementen en uitsluitingen. Zie voor meer informatie de [Android V1](#android-quarantine) sectie.

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
    <tr> 
   <td> Afkeuring van FCM-berichten: Ongeldig argument<br /> </td> 
   <td> Mislukt<br /> </td> 
   <td> INVALID_ARGUMENT </td> 
   <td> Genegeerd</td> 
   <td> Ongedefinieerd<br /> </td> 
   <td> Nee<br /> </td> 
  </tr>
    <tr> 
   <td> Afkeuring van FCM-berichten: Verificatiefout van derden<br /> </td> 
   <td> Mislukt<br /> </td> 
   <td> THIRD_PARTY_AUTH_ERROR </td> 
   <td> Genegeerd</td>
   <td> Geweigerd<br /> </td> 
   <td> Ja<br /> </td> 
  </tr>
    <tr> 
   <td> Afkeuring van FCM-berichten: Afzender-id komt niet overeen<br /> </td> 
   <td> Mislukt<br /> </td> 
   <td> SENDER_ID_MISMATCH </td> 
   <td> Zacht</td>
   <td> Gebruiker onbekend<br /> </td> 
   <td> Nee<br /> </td> 
  </tr>
    <tr> 
   <td> Afkeuring van FCM-berichten: Niet geregistreerd<br /> </td> 
   <td> Mislukt<br /> </td>
   <td> ONGEREGISTREERD </td> 
   <td> Hard</td> 
   <td> Gebruiker onbekend<br /> </td> 
   <td> Nee<br /> </td> 
  </tr>
    <tr> 
   <td> Afkeuring van FCM-berichten: Intern<br /> </td> 
   <td> Mislukt<br /> </td> 
   <td> INTERN </td> 
   <td> Genegeerd</td> 
   <td> Geweigerd<br /> </td> 
   <td> Ja<br /> </td> 
  </tr>
    <tr> 
   <td> Afkeuring van FCM-berichten: Niet beschikbaar<br /> </td> 
   <td> Mislukt<br /> </td> 
   <td> NIET BESCHIKBAAR</td> 
   <td> Genegeerd</td> 
   <td> Geweigerd<br /> </td> 
   <td> Ja<br /> </td> 
  </tr>
    <tr> 
   <td> Afkeuring van FCM-berichten: onverwachte foutcode<br /> </td> 
   <td> Mislukt<br /> </td> 
   <td> onverwachte foutcode</td> 
   <td> Genegeerd</td> 
   <td> Geweigerd<br /> </td> 
   <td> Nee<br /> </td> 
  </tr>
  <tr> 
   <td> Verificatie: Verbindingsprobleem<br /> </td> 
   <td> Mislukt<br /> </td> 
   <td> Kan geen verbinding maken met verificatieserver </td> 
   <td> Genegeerd</td>
   <td> Geweigerd<br /> </td> 
   <td> Ja<br /> </td> 
  </tr>
    <tr> 
   <td> Verificatie: Niet-geautoriseerde client of bereik in aanvraag.<br /> </td> 
   <td> Mislukt<br /> </td> 
   <td> onbevoegd_client </td> 
   <td> Genegeerd</td>
   <td> Geweigerd<br /> </td> 
   <td> Nee<br /> </td> 
  </tr>
    <tr> 
   <td> Verificatie: De cliënt is onbevoegd om toegangstokens terug te winnen gebruikend deze methode, of cliënt geautoriseerd niet voor om het even welk gevraagd werkingsgebied.<br /> </td> 
   <td> Mislukt<br /> </td> 
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
   <td> Nee<br /> </td> 
  </tr>
    <tr> 
   <td> Verificatie: Ongeldig e-mailadres<br /> </td> 
   <td> Mislukt<br /> </td> 
   <td> invalid_Grant </td> 
   <td> Genegeerd</td> 
   <td> Geweigerd<br /> </td> 
   <td> Nee<br /> </td> 
  </tr>
    <tr> 
   <td> Verificatie: Ongeldige JWT<br /> </td> 
   <td> Mislukt<br /> </td> 
   <td> invalid_Grant </td> 
   <td> Genegeerd</td> 
   <td> Geweigerd<br /> </td> 
   <td> Nee<br /> </td> 
  </tr>
    <tr> 
   <td> Verificatie: Ongeldige JWT-handtekening<br /> </td> 
   <td> Mislukt<br /> </td> 
   <td> invalid_Grant </td> 
   <td> Genegeerd</td> 
   <td> Geweigerd<br /> </td> 
   <td> Nee<br /> </td> 
  </tr>
    <tr> 
   <td> Verificatie: Ongeldig OAuth-bereik of publiek voor ID-token opgegeven<br /> </td> 
   <td> Mislukt<br /> </td> 
   <td> onbevoegd_client</td> 
   <td> Genegeerd</td> 
   <td> Geweigerd<br /> </td> 
   <td> Nee<br /> </td> 
  </tr>
    <tr> 
   <td> Verificatie: OAuth-client uitgeschakeld<br /> </td> 
   <td> Mislukt<br /> </td> 
   <td> disabled_client</td> 
   <td> Genegeerd</td> 
   <td> Geweigerd<br /> </td> 
   <td> Nee<br /> </td> 
  </tr>
 </tbody> 
</table>

## SMS-quarantines {#sms-quarantines}

**Voor standaardconnectors**

Het quarantainemechanisme voor SMS-berichten is over het algemeen hetzelfde als het algemene proces. Zie [Informatie over quarantines](#about-quarantines). De specifieke kenmerken voor SMS worden hieronder weergegeven.

>[!NOTE]
>
>De **[!UICONTROL Delivery log qualification]** de tabel is niet van toepassing op **Uitgebreide algemene SMPP** -aansluiting.

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

Wanneer het gebruiken van het protocol SMPP om de berichten van SMS te verzenden, wordt het foutenbeheer verschillend behandeld. Voor meer informatie over de Uitgebreide generische schakelaar SMPP, verwijs naar [deze pagina](sms-set-up.md#creating-an-smpp-external-account).

De schakelaar SMPP wint gegevens van het bericht van SR (Status Report) terug dat gebruikend regelmatige uitdrukkingen (regexes) is teruggekeerd om zijn inhoud te filtreren. Deze gegevens worden vervolgens vergeleken met de gegevens in het dialoogvenster **[!UICONTROL Delivery log qualification]** tabel (beschikbaar via **[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Non deliverables Management]** ).

Voordat een nieuw type fout wordt gekwalificeerd, is de reden van de fout altijd ingesteld op **Geweigerd** standaard.

>[!NOTE]
>
>De fouttypen en -redenen zijn gelijk aan die voor e-mailberichten. Zie [Typen leveringsfouten en redenen](understanding-delivery-failures.md#delivery-failure-types-and-reasons).
>
>Vraag uw leverancier om een lijst van status en foutencodes om juiste mislukkingstypes en redenen voor mislukking in de de kwalificatielijst van het Logboek van de Levering te plaatsen.

Voorbeeld van een gegenereerd bericht:

```
SR Generic DELIVRD 000|#MESSAGE#
```

* Alle foutberichten beginnen met **SR** om SMS-foutcodes te onderscheiden van e-mailfoutcodes.
* Het tweede deel (**Algemeen** in dit voorbeeld) van het foutbericht verwijst naar de naam van de SMSC-implementatie, zoals gedefinieerd in de **[!UICONTROL SMSC implementation name]** veld van de externe SMS-rekening. Zie [deze pagina](sms-set-up.md#creating-an-smpp-external-account).

   Omdat dezelfde foutcode voor elke provider een andere betekenis kan hebben, kunt u in dit veld weten welke provider de foutcode heeft gegenereerd. U kunt de fout dan vinden in de relevante documentatie van de leverancier.

* Het derde deel (**LEVERING** in dit voorbeeld) van het foutbericht komt overeen met de statuscode die uit de SR is opgehaald met behulp van het statusextractieoverzicht dat in de externe SMS-account is gedefinieerd.

   Deze regex wordt gespecificeerd in **[!UICONTROL SMSC specificities]** tabblad van de externe account. Zie [deze pagina](sms-set-up.md#creating-an-smpp-external-account).

   ![](assets/tech_quarant_error_regex.png)

   Standaard extraheert de regex de **Status:** veld zoals gedefinieerd door de **Aanhangsel B** van de **SMPP 3.4-specificatie**.

* Het vierde deel (**000** in dit voorbeeld) van het foutbericht komt overeen met de foutcode die uit de SR is geëxtraheerd met behulp van het extraheren van de foutcode die in de externe SMS-account is gedefinieerd.

   Deze regex wordt gespecificeerd in **[!UICONTROL SMSC specificities]** tabblad van de externe account. Zie [deze pagina](sms-set-up.md#creating-an-smpp-external-account).

   Standaard extraheert de regex de **fout:** veld zoals gedefinieerd door de **Aanhangsel B** van de **SMPP 3.4-specificatie**.

* Alles wat na het buissymbool (|) komt wordt slechts getoond in **[!UICONTROL First text]** kolom van de **[!UICONTROL Delivery log qualification]** tabel. Deze inhoud wordt altijd vervangen door **#MESSAGE#** nadat het bericht is genormaliseerd. Dit proces voorkomt het hebben van veelvoudige ingangen voor gelijkaardige fouten en is het zelfde als voor e-mail. Zie voor meer informatie [Bounce mail-kwalificatie](understanding-delivery-failures.md#bounce-mail-qualification).

De uitgebreide generische schakelaar SMPP past heuristisch toe om verstandige standaardwaarden te vinden: als de status begint met **DELIV**, wordt het als een succes beschouwd omdat het overeenkomt met de gemeenschappelijke status **LEVERING** of **AFGELEVERD** door de meeste aanbieders worden gebruikt. Elke andere status leidt tot een harde fout.
