---
product: campaign
title: Campagneopties configureren
description: Leer hoe u de opties voor campagne configureert
feature: Installation, Application Settings
audience: installation
content-type: reference
topic-tags: appendices
exl-id: a979cd99-afa7-4ce6-ba0f-9495089cba08
source-git-commit: 0fba6a2ad4ffa864e2f726f241aa9d7cd39072a6
workflow-type: tm+mt
source-wordcount: '3831'
ht-degree: 0%

---

# Lijst met opties voor Campaigns Classic{#configuring-campaign-options}

Met het knooppunt **[!UICONTROL Administration / Platform / Options]** kunt u Adobe Campaign-opties configureren. Sommige hiervan zijn ingebouwd tijdens de installatie van Campagne en andere kunnen handmatig worden toegevoegd wanneer dat nodig is. Welke opties beschikbaar zijn, is afhankelijk van de pakketten die bij de instantie worden geïnstalleerd.


>[!CAUTION]
>
>* De opties die niet in deze pagina worden vermeld zijn intern slechts en **moeten niet worden gewijzigd**.
>
>* U kunt Adobe Campaign-opties alleen wijzigen of bijwerken door experts.

## Levering {#delivery}

<table> 
 <thead> 
  <tr> 
   <th> Naam van optie </th> 
   <th> Beschrijving </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol"> Deliverability_LastBrowserLogMsgDate </span> <br /> </td> 
   <td> Datum van laatste wideLogMsg die van de leverbaarheidsinstantie wordt teruggewonnen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> Deliverability_LastBrowserLogMsgSent </span> <br /> </td> 
   <td> Datum van laatste wideLogMsg die naar de leveringsinstantie wordt verzonden.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> DmRendering_cuid </span> <br /> </td> 
   <td> Id van leveringsrapporten. Neem contact op met de technische ondersteuning voor uw id.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> DmRendering_SeedTargets </span> <br /> </td> 
   <td> Lijst van schema's waarvoor u testadressen voor het Teruggeven Inbox wilt gebruiken. (elementnamen worden met komma's van elkaar gescheiden), bijv.: custom_nms_receiver.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> EMTA_BCC_ADDRESS </span> </td> 
   <td> BCC e-mailadres waarnaar de verbeterde MTA een onbewerkte kopie van de verzonden e-mails verzendt. <br /> </td> 
  </tr>
  <tr> 
   <td> <span class="uicontrol"> NMS_ActivateOwnerConfirmation </span> <br /> </td> 
   <td><p> Hiermee kunt u toestaan dat de exploitant die verantwoordelijk is voor de levering de verzending bevestigt, als een specifieke exploitant of groep exploitanten is aangewezen voor het starten van een levering in de eigendommen van de levering.</p><p> Hiervoor activeert u de optie door "1" als waarde in te voeren. Voer "0" in om deze optie te deactiveren.</p><p> Het verzendbevestigingsproces functioneert vervolgens als standaard: alleen de exploitant of groep van exploitanten die voor de verzending zijn aangewezen in de leveringseigenschappen (of een beheerder) kan de verzending bevestigen en uitvoeren. Zie <a href="../../campaign/using/marketing-campaign-deliveries.md#starting-an-online-delivery">deze sectie</a>.</p> </td> 
   <tr> 
   <td> <span class="uicontrol"> Nms_DefaultRcpSchema </span> <br /> </td> 
   <td> Adobe Campaign gebruikt een globale variabele "Nms_DefaultRcpSchema"aan dialoog met het standaard ontvankelijke gegevensbestand (nms:ontvanger).<br /> De waarde van de optie moet overeenkomen met de naam van het schema dat overeenkomt met de tabel voor externe ontvangers. <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsBilling_MainActionThreshold </span> <br /> </td> 
   <td> Het minimum aantal ontvangers opdat een levering als belangrijkste in het het facturerings rapport moet worden beschouwd.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsBroadcast_DefaultProvider </span> <br /> </td> 
   <td> Standaard verpletterend dienstverlener voor de nieuwe malplaatjes.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsBroadcast_LogsPerTransac </span> <br /> </td> 
   <td> Minimale partijgrootte (aantal rijen) voor de toevoeging van wideLogs tijdens een leveringsvoorbereiding.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsBroadcast_MaxDelayPerTransac </span> <br /> </td> 
   <td> De drempel van de duur van de partij (aantal milliseconden) waaronder de partijgrootte voor de toevoeging van wideLogs tijdens een leveringsvoorbereiding wordt verdubbeld.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsBroadcast_MidAnalyzeBatchSize </span> <br /> </td> 
   <td> Groepering grootte van leveringsdelen wanneer het analyseren van middelsourcingleveringen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsBroadcast_MsgValidityDuration </span> <br /> </td> 
   <td> Standaard leveringsperiode voor een levering (in seconden).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsBroadcast_RegexRules </span> <br /> </td> 
   <td> Reguliere expressies voor het normaliseren van leveringsberichten.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsBroadcast_RemoveBlackList </span> <br /> </td> 
   <td> Het ingaan van "1"als waarde laat u ontvangers uitsluiten die niet meer wensen om worden gecontacteerd.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsBroadcast_RemoveDuplicatesRecipients </span> <br /> </td> 
   <td> Door "1" in te voeren als waarde, kunt u automatisch dubbele gegevens negeren.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsDelivery_ErrorAddressMasks </span> <br /> </td> 
   <td> Laat u de syntaxis van het adres bepalen van de Fout die wanneer het antwoorden op een bericht wordt gebruikt.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsDelivery_FromAddressMasks </span> <br /> </td> 
   <td> Laat u de syntaxis van Van adres bepalen dat wanneer het verzenden van een bericht wordt gebruikt.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsDelivery_ImageServerTimeout </span> <br /> </td> 
   <td> Hiermee kunt u een time-outlimiet (in seconden) definiëren voor het ophalen van een reactie van de server wanneer een afbeelding wordt opgehaald die is gedownload van een gepersonaliseerde URL en die is gekoppeld aan een e-mail. Als deze waarde wordt overschreden, kan het bericht niet worden verzonden. De standaardwaarde is 60 seconden.<br /> </td> 
  </tr> 
 <tr> 
   <td> <span class="uicontrol"> NmsDelivery_MaxDownloadedImageSize </span> <br /> </td> 
   <td> Hiermee kunt u de maximale grootte (in bytes) definiëren die is toegestaan voor afbeeldingen die zijn gedownload van een gepersonaliseerde URL en die zijn gekoppeld aan een e-mail. De standaardwaarde is 100.000 bytes (100 KB). Als een proefdruk wordt verzonden en de afbeelding(en) wordt (worden) gedownload om de e-mail te verwerken, als de grootte van een afbeelding deze waarde overschrijdt of als er een downloadprobleem is, wordt een fout weergegeven in de leveringslogboeken en mislukt de proefaflevering.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsDelivery_MaxRecommendedAttachments </span> <br /> </td> 
   <td> Hiermee kunt u een maximum aantal bijlagen instellen in een e-mailsjabloon of transactiesjabloon. Als deze waarde wordt overschreden, zal een waarschuwing in de logboeken van de leveringsanalyse of wanneer het publiceren van het transactionele e-mailmalplaatje worden getoond. De standaardwaarde is 1 gehechtheid.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsDelivery_MaxRetry </span> <br /> </td> 
   <td> Maximum aantal pogingen tijdens analyse.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsDelivery_PublishingScript </span> <br /> </td> 
   <td> Publicatiescript.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsDelivery_NoCountBroadLogMsgPush </span> <br /> </td> 
   <td> Schakel het aantal wideLogMsg voor pushberichten uit.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsDeliveryWizard_ShowDeliveryWeight </span> <br /> </td> 
   <td> Toon het berichtgewicht in de leveringsmedewerker.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsEmail_DefaultErrorAddr </span> <br /> </td> 
   <td> Het standaard "fout"e-mailadres op het niveau van de instantie dat voor e-maillevering wordt gebruikt als verlaten leeg door gebruiker.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsEmail_DefaultFromAddr </span> <br /> </td> 
   <td> Het standaard e-mailadres 'van' op instantieniveau wordt gebruikt voor e-maillevering als deze door de gebruiker leeg wordt gelaten.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsEmail_DefaultReplyToAddr </span> <br /> </td> 
   <td> Het standaard "antwoord-aan"e-mailadres op het niveau van instance dat voor e-maillevering wordt gebruikt als verlaten leeg door gebruiker.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsEmail_ExpOrganization </span> <br /> </td> 
   <td> Algemene naam van de klant. Gebruikt in sommige waarschuwingsberichten die aan de ontvangers worden getoond.<br /> "U ontvangt dit bericht omdat u met ` Organisatie"of een verbonden bedrijf hebt contact gehad. Om geen berichten van ` organisatie ` meer te ontvangen ` <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsEmail_FromName </span> <br /> </td> 
   <td> Standaard e-maillabel 'from' op instantieniveau wordt gebruikt voor e-maillevering als dit door de gebruiker leeg wordt gelaten.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsEmail_ReplyToName </span> <br /> </td> 
   <td> Het standaard e-mailetiket "antwoord-aan"op het niveau van instance dat voor e-maillevering wordt gebruikt als verlaten leeg door gebruiker.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsEmail_RetryCount </span> <br /> </td> 
   <td> Periode tussen twee pogingen van een e-mailbericht (in seconden).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsEmail_RetryPeriod </span> <br /> </td> 
   <td> Periode van herpogingen voor e-mailberichten.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsForecast_MsgWeightFormula </span> <br /> </td> 
   <td> Formule die wordt gebruikt om het wegen van een bericht voor een voorlopige levering te berekenen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsInmail_AllowlistEmails </span> <br /> </td> 
   <td> Lijst van geoorloofde het door:sturen e-mailadressen (van de binnenkomende module van de postverwerking). De adressen moeten door komma's (of * worden gescheiden om allen toe te staan). Bijvoorbeeld xyz@abc.com,pqr@abc.com.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsLine_AESKey </span> <br /> </td> 
   <td> AES sleutel die in het "lineImage"servlet wordt gebruikt om URLs (het kanaal van de LIJN) te coderen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsNPAI_EmailMaxError </span> <br /> </td> 
   <td> Op kanaal "e-mail"(gebruik als gebrek): Maximaal aantal fouten die, voor de fouten van SOFT tijdens het verzenden worden goedgekeurd alvorens de ontvanger in quarantaine te zetten.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsNPAI_EmailSignificantErrorDelay </span> <br /> </td> 
   <td> Op kanaal "e-mail"(gebruik als gebrek): Minimale periode aan besteed sinds de vorige referenced fout SOFT, alvorens rekening te houden met een nieuwe fout SOFT.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsNPAI_MobileMaxError </span> <br /> </td> 
   <td> Op kanaal "mobiel": Maximaal aantal fouten dat wordt aanvaard, voor de fouten van SOFT tijdens het verzenden alvorens de ontvanger in quarantaine te zetten.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsNPAI_MobileSignificantErrorDelay </span> <br /> </td> 
   <td> Op kanaal "mobiel": Minimale periode aan besteed sinds de vorige referenced fout SOFT, alvorens rekening te houden met een nieuwe fout SOFT.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsMidSourcing_LogsPeriodHour </span> <br /> </td>
   <td> Staat een maximumperiode (die in uren wordt uitgedrukt) toe om het aantal uitzendingen te beperken wordt teruggekregen telkens als het synchronisatiewerkschema wordt uitgevoerd.</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsMidSourcing_PrepareFlow </span> <br /> </td> 
   <td> Maximum aantal vraag in sessie MidSourcing, die parallel (3 door gebrek) kan worden in werking gesteld.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsMTA_Alert_Delay </span> <br /> </td> 
   <td> De vertraging van de douane (in notulen) waarna een levering als "vertraagd"wordt beschouwd, gebrek die 30 minuten is.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsOperation_DeliveryPreparationWindow </span> <br /> </td> 
   <td><p>Deze optie wordt gebruikt door het </a></span> technische werkschema 0&rbrace; operationMgt &lbrace;wanneer het tellen van het aantal lopende leveringen.<span class="uicontrol"><a href="../../workflow/using/about-technical-workflows.md"></p>Hiermee kunt u het aantal dagen definiëren waarboven leveringen met een inconsistente status worden uitgesloten van het aantal lopende leveringen.</p><p>De standaardwaarde is "7", wat betekent dat inconsistente leveringen ouder dan 7 dagen worden uitgesloten.</p></td> 
  </tr>
  <tr> 
   <td> <span class="uicontrol"> NmsPaper_SenderLine1 </span> <br /> </td> 
   <td> Lijn 1 van het adres van de afzender.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsPaper_SenderLine3 </span> <br /> </td> 
   <td> Lijn 3 van het adres van de afzender.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsPaper_SenderLine4 </span> <br /> </td> 
   <td> Lijn 4 van het adres van de afzender.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsPaper_SenderLine6 </span> <br /> </td> 
   <td> Lijn 6 van het adres van de afzender.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsPaper_SenderLine7 </span> <br /> </td> 
   <td> Lijn 7 van het adres van de afzender.<br /> </td> 
  </tr>
  <tr> 
   <td> <span class="uicontrol"> NmsServer_MirrorPageUrl </span> <br /> </td> 
   <td> URL van de spiegelpaginaserver (door gebrek, zou identiek moeten zijn aan NmsTracking_ServerUrl).<br /> Het is de standaardwaarde van e-mailleveringen wanneer URL niet in de verpletterende definitie wordt gespecificeerd.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsSMS_Priority </span> <br /> </td> 
   <td> Parameters van verzonden berichten van SMS: informatie die aan de gateway van SMS wordt overgebracht om op de berichtprioriteit te wijzen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsSMS_RetryCount </span> <br /> </td> 
   <td> Aantal pogingen wanneer het verzenden van de berichten van SMS.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsSMS_RetryPeriod </span> <br /> </td> 
   <td> Periode waarin de pogingen van SMS berichten zullen worden uitgevoerd.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsUserAgentStats_LastConsolidation </span> <br /> </td> 
   <td> Laatste consolidatiedatum voor <span class="uicontrol"> NmsUserAgent </span> statistieken.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsWebSegments_LastStates </span> <br /> </td> 
   <td> Naam van de optie die de Websegmenten en hun staten bevat.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> XtkBarcode_SpecialChar </span> <br /> </td> 
   <td> Laat/maak steun voor speciale karakters voor Code128 toe onbruikbaar.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> XtkEmail_Characters </span> <br /> </td> 
   <td> Geldige tekens voor een e-mailadres.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> XtkSecurity_Restrict_EditXML </span> </td> 
   <td> Voeg deze optie met de "0"waarde toe om de uitgave van de code van XML van leveringen onbruikbaar te maken (klik met de rechtermuisknop / <span class="uicontrol"> geef de bron van XML </span> of <span class="uicontrol"> CTRL + F4 </span> kortere weg uit).<br /> </td> 
  </tr>  
 </tbody> 
</table>

<!--<tr> 
   <td> <span class="uicontrol">EMTA_BCC_ADDRESS</span> </td> 
   <td> BCC email address for Momentum to send a raw copy of the sent emails. <br /> </td> 
  </tr>
-->

## Bronnen {#resources}

<table> 
 <thead> 
  <tr> 
   <th> Naam van optie </th> 
   <th> Beschrijving </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol"> NcmRessourcesDir </span> <br /> </td> 
   <td> Locatie van bronnen voor publicatie in de Adobe Campaign-clientconsole. Zie <a href="../../delivery/using/formatting.md#image-referencing"> deze sectie </a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NcmRessourcesDirPreview </span> <br /> </td> 
   <td> Locatie van bronnen voor voorvertoning in de Adobe Campaign-clientconsole. Zie <a href="../../delivery/using/formatting.md#image-referencing"> deze sectie </a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsDelivery_DefaultIgnoredImage </span> <br /> </td> 
   <td> Lijst met URL-maskers voor de afbeeldingen die tijdens het uploaden zijn overgeslagen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsDelivery_ImagePublishing </span> </td> 
   <td> Configuratie van het uploaden van afbeeldingen. De waarden kunnen none / tracking / script / list zijn (kan worden overschreven door de optionele instellingen van de operator). </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsDelivery_ImageSubDirectory </span> <br /> </td> 
   <td> De omslag waarin de beelden op de server moeten worden opgeslagen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsServer_LogoPath </span> <br /> </td> 
   <td> Ruimte om logo's te tonen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NcmPublishingDir </span> <br /> </td> 
   <td> Hoofdmap voor publicaties.<br /> voor meer op HTML en de inhoudsgeneratie van de Tekst, verwijs naar <a href="../../delivery/using/using-a-content-template.md"> deze sectie </a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> XtkImageUrl </span> <br /> </td> 
   <td> Hiermee kunt u de server definiëren waarop de afbeeldingen worden opgeslagen die in de leveringen worden gebruikt, zodat de browser ze kan ophalen.<br /> Voor buildversies &lt;= 5098 gebruiken we de URL van de afbeeldingen die naar de instantie zijn geüpload.<br /> voor bouwstijlversies &gt; 5098, gebruiken wij in plaats daarvan openbare URL van de levering of <span class="uicontrol"> XtkFileRes_Public_URL </span> optie URL.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsDelivery_MediaInstance </span> <br /> </td> 
   <td> Hier kunt u de instantienaam configureren voor het uploaden van afbeeldingen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsDelivery_MediaPassword </span> <br /> </td> 
   <td> Laat u het wachtwoord voor beeld het uploaden vormen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsDelivery_MediaServers </span> <br /> </td> 
   <td> Hiermee kunt u de media-URL's configureren voor het uploaden van afbeeldingen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsBroadcast_MsgWebValidityDuration </span> <br /> </td> 
   <td> De standaard geldigheidsduur voor online middelen van een levering (in seconden).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> XtkFileRes_Public_URL </span> <br /> </td> 
   <td> Nieuwe URL voor openbare middeldossiers.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Campagne- en workflowbeheer {#campaign-e-workflow-management}

<table> 
 <thead> 
  <tr> 
   <th> Naam van optie </th> 
   <th> Beschrijving </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol"> CrmMarketingActivityWindow </span> <br /> </td> 
   <td> De geschiedenis van de marketing die voor dit aantal maanden wordt getoond.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsOperation_Duration </span> <br /> </td> 
   <td> De standaard geldigheidsperiode van een campagne (in seconden).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsOperation_LimitConcurrency </span> <br /> </td> 
   <td> Maximum aantal levering/werkschema/hypothese/simulatietaken die in een tijd kunnen worden verwerkt, die door workflow operationMgt. <br /> is begonnen </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsOperation_OperationMgtDebug </span> <br /> </td> 
   <td> Staat u toe om de </a> technische werkschemauitvoering te controleren 0&rbrace; operationMgt. <a href="../../workflow/using/about-technical-workflows.md"> Wanneer geactiveerd (waarde "1"), wordt de uitvoeringsinformatie het programma geopend in de logboeken van de werkschemacontrole.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsOperation_TimeRange </span> <br /> </td> 
   <td> Tijdsperiode voor het richten en extractie voorwaarden op geplande wijze.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> Workflow_AnalysisThreshold </span> <br /> </td> 
   <td> Aantal beïnvloede verslagen waarna de lijststatistieken automatisch worden opnieuw berekend.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> XtkReport_Logo </span> <br /> </td> 
   <td> Logo dat in de hoogste juiste hoek van de uitgevoerde rapporten moet worden getoond.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsServer_PausedWorkflowPeriod </span> <br /> </td> 
   <td> Aantal dagen tussen controles op gepauzeerde werkschema's te wachten.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsCampaign_Activate_OwnerConfirmation </span> <br /> </td> 
   <td> Activeer de validatie van leveringen door de eigenaar van de bewerking door "1" in te voeren als waarde. Voer "0" in om deze optie te deactiveren.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsAsset_JavascriptExt </span> <br /> </td> 
   <td> Aanvullende JS-bibliotheek die moet worden geladen in de activiteit "Marketing resource notifications" van de workflow.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Beveiliging {#security}

<table> 
 <thead> 
  <tr> 
   <th> Naam van optie </th> 
   <th> Beschrijving </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol"> RestrictEditingOOTBSchema </span> <br /> </td> 
   <td> (beginnend versie 21.1.3) als 1 (standaardwaarde) wordt geselecteerd, maakt deze optie uitgave van ingebouwde schema's onbruikbaar.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> RestrictEditingOOTBJavascript </span> <br /> </td> 
   <td> (vanaf versie 21.1.3) Als 1 is geselecteerd (standaardwaarde), schakelt deze optie de uitgave van ingebouwde JavaScript-codes uit.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> XtkAcceptOldPasswords </span> <br /> </td> 
   <td> (Compatibiliteitsmodus installeren: build&gt;6000) Wanneer deze optie is geactiveerd (waarde "1"), kunt u oude wachtwoorden die in de database zijn opgeslagen, gebruiken voor de verbinding met externe accounts of met de instantie.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> XtkKey </span> <br /> </td> 
   <td> Deze sleutel wordt gebruikt om de meeste wachtwoorden in het gegevensbestand te coderen. (externe accounts, LDAP-wachtwoord...).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> XtkSecurity_Allow_PrivilegeEscalation </span> <br /> </td> 
   <td> Als 1 wordt geselecteerd, deze optie om privilegeEscalation in JavaScript toe te staan.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> XtkSecurity_Disable_ControlsOnFileDownload </span> <br /> </td> 
   <td> Als 1 wordt geselecteerd, onbruikbaar maakt deze optie ACL controles tijdens een dossierdownload (via fileDownload.jsp).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> XtkSecurity_Disable_JSFileSandboxing </span> <br /> </td> 
   <td> Als 1 wordt geselecteerd, maakt deze optie het dossier het zandbakken binnen Javascript onbruikbaar.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> XtkSecurity_SaveOptions_AllowNonAdmin </span> <br /> </td> 
   <td> Indien geplaatst aan "waar", geautoriseerde niet-admin exploitant om de waarden xtkOption door de plaatsingstovenaar bij te werken.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> XtkSecurity_Unsafe_DecryptString </span> <br /> </td> 
   <td> Als 1 wordt geselecteerd, staat deze optie toe om decryptString te gebruiken om sommige wachtwoorden te decrypteren.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> XtkTraceDeleteLogin </span> <br /> </td> 
   <td> Ga de "1"waarde in om de schrapping van elementen met de spoorinformatie van de Controle in mData, door de wijziging van zijn "gewijzigd door"gebied vóór de schrapping van het verslag te vinden.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Berichtencentrum {#message-center}

<table> 
 <thead> 
  <tr> 
   <th> Naam van optie </th> 
   <th> Beschrijving </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol"> MC_EnrichmentCustomJs </span> <br /> </td> 
   <td> De JavaScript-bibliotheek moet worden gepersonaliseerd voor het verrijken van gebeurtenissen. Moet de implementatie van deze twee functies bevatten:<br /> 
    <ul> 
     <li> <p> <span class="uicontrol"> enrichRtEvents (aiEventId);</span> : verrijkt en bewaart gebeurtenissen in het gegevensbestand (waar <span class="uicontrol"> aiEventId </span> aan de lijst van verwerkte gebeurtenissen in real time beantwoordt).</p> </li> 
     <li> <p> <span class="uicontrol"> enrichBatchEvents (aiEventId);</span> : verrijkt en bewaart gebeurtenissen in het gegevensbestand (waar <span class="uicontrol"> aiEventId </span> aan de lijst van identiteitskaart van verwerkte partijgebeurtenissen beantwoordt).</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> MC_LastUpdateFromBL </span> <br /> </td> 
   <td> Datum van de laatste update van de gebeurtenisstatus via leveringslogboeken.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> MC_RoutingCustomJs </span> <br /> </td> 
   <td> De bibliotheek van JavaScript die voor het verpletteren van gebeurtenissen moet worden gepersonaliseerd. Moet de implementatie van deze twee functies bevatten:<br /> 
    <ul> 
     <li> <p> <span class="uicontrol"> dispatchRtEvent(iEventId);</span> : keert de interne naam van het transactiemelding terug die wordt geselecteerd om de gebeurtenis in real time (waar <span class="uicontrol"> iEventId </span> aan identiteitskaart van de verwerkte gebeurtenis in real time beantwoordt) te verwerken.</p> </li> 
     <li> <p> <span class="uicontrol"> dispatchBatchEvent (iEventId);</span> : keert de interne naam van het transactiemelding terug die wordt geselecteerd om de partijgebeurtenis te verwerken (waar <span class="uicontrol"> iEventId </span> aan identiteitskaart van de verwerkte partijgebeurtenis beantwoordt).</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> MC_RtEventAvgDeliveryTimeAlert </span> <br /> </td> 
   <td> De drempel van de alarm van gemiddelde verzendende tijd van gebeurtenissen in real time.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> MC_RtEventAvgDeliveryTimeWarning </span> <br /> </td> 
   <td> De drempel van de waarschuwing voor gemiddelde verzendende tijd van gebeurtenissen in real time.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> MC_RtEventAvgProcessTimeAlert </span> <br /> </td> 
   <td> Alert drempel voor de gemiddelde verwerkingstijd van gebeurtenissen in real time.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> MC_RtEventAvgProcessTimeWarning </span> <br /> </td> 
   <td> De drempel van de waarschuwing voor de gemiddelde verwerkingstijd van gebeurtenissen in real time.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> MC_RtEventAvgQueueAlert </span> <br /> </td> 
   <td> Alert drempel voor het gemiddelde aantal een rij gevormde gebeurtenissen in real time.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> MC_RtEventAvgQueueTimeAlert </span> <br /> </td> 
   <td> Alert drempel voor gemiddelde het een rij vormen tijd van gebeurtenissen in real time.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> MC_RtEventAvgQueueTimeWarning </span> <br /> </td> 
   <td> De drempel van de waarschuwing voor gemiddelde het een rij vormen tijd van gebeurtenissen in real time.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> MC_RtEventAvgQueueWarning </span> <br /> </td> 
   <td> De drempel van de waarschuwing voor het gemiddelde aantal een rij gevormde gebeurtenissen in real time.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> MC_RtEventErrorAlert </span> <br /> </td> 
   <td> Alert drempel voor verwerkingsfouten van gebeurtenissen in real time.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> MC_RtEventErrorWarning </span> <br /> </td> 
   <td> De drempel van de waarschuwing voor verwerkingsfouten van gebeurtenissen in real time.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> MC_RtEventMaxQueueAlert </span> <br /> </td> 
   <td> Alert drempel voor maximumaantal een rij gevormde gebeurtenissen in real time.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> MC_RtEventMaxQueueWarning </span> <br /> </td> 
   <td> De drempel van de waarschuwing voor maximumaantal een rij gevormde gebeurtenissen in real time.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> MC_RtEventMinQueueAlert </span> <br /> </td> 
   <td> Alert drempel voor minimumaantal een rij gevormde gebeurtenissen in real time.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> MC_RtEventMinQueueWarning </span> <br /> </td> 
   <td> De drempel van de waarschuwing voor minimumaantal een rij gevormde gebeurtenissen in real time.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> MC_RtEventQueueAlert </span> <br /> </td> 
   <td> Drempel vóór kritieke voorwaarde voor de rij van hangende gebeurtenissen in real time.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> MC_RtEventQueueWarning </span> <br /> </td> 
   <td> Drempel vóór waarschuwing voor de wachtrij met openstaande real-time gebeurtenissen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> MC_RtEventThroughputAlert </span> <br /> </td> 
   <td> Alert drempel voor gebeurtenisproductie in real time.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> MC_RtEventThroughputWarning </span> <br /> </td> 
   <td> De drempel van de waarschuwing voor gebeurtenisproductie in real time.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsMessageCenter_RoutingBatchSize </span> <br /> </td> 
   <td> Grootte van het hergroeperen voor de gebeurtenis die verplettert.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> MC_LastRtEventState </span> <br /> </td> 
   <td> Werk wijzer van status RtEvent bij (laatste datum tot wanneer de gegevens werden teruggewonnen).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsLine_MessageCenterURL </span> <br /> </td> 
   <td> De server URL van het Centrum van het bericht die wordt gebruikt om welkome berichten (het kanaal van de LIJN) te verzenden.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Database {#database}

<table> 
 <thead> 
  <tr> 
   <th> Naam van optie </th> 
   <th> Beschrijving </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol"> NmsCleanup_LastCleanup </span> <br /> </td> 
   <td> Bepaalt de laatste tijd het schoonmaakbeurtproces in werking werd gesteld.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsCleanup_BroadLogPurgeDelay </span> <br /> </td> 
   <td> <p>Hier kunt u de vertraging definiëren waarna de uitzending uit de database wordt verwijderd.</p><p>Deze optie wordt automatisch gecreeerd zodra de vertraging binnen de interface wordt gewijzigd. Als u de waarde in de lijst met opties wijzigt, moet deze worden uitgedrukt in seconden.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsCleanup_EventHistoPurgeDelay </span> <br /> </td> 
   <td><p> Hier kunt u de vertraging definiëren waarna de gebeurtenisgeschiedenis uit de database wordt gewist.</p><p>
   Deze optie wordt automatisch gecreeerd zodra de vertraging binnen de interface wordt gewijzigd. Als u de waarde in de lijst met opties wijzigt, moet deze worden uitgedrukt in seconden.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsCleanup_EventPurgeDelay </span> <br /> </td> 
   <td><p> Hiermee kunt u de vertraging definiëren waarna gebeurtenissen uit de database worden verwijderd.</p><p>Deze optie wordt automatisch gecreeerd zodra de vertraging binnen de interface wordt gewijzigd. Als u de waarde in de lijst met opties wijzigt, moet deze worden uitgedrukt in seconden.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsCleanup_EventStatePurgeDelay </span> <br /> </td> 
   <td><p> Hier kunt u de vertraging definiëren waarna de gebeurtenisstatistieken uit de database worden gewist.</p><p>Deze optie wordt automatisch gecreeerd zodra de vertraging binnen de interface wordt gewijzigd. Als u de waarde in de lijst met opties wijzigt, moet deze worden uitgedrukt in seconden.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsCleanup_PropositionPurgeDelay </span> <br /> </td> 
   <td><p> Hier kunt u de vertraging definiëren waarna voorstellingen uit de database worden verwijderd.</p><p> Deze optie wordt automatisch gecreeerd zodra de vertraging binnen de interface wordt gewijzigd. Als u de waarde in de lijst met opties wijzigt, moet deze worden uitgedrukt in seconden.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsCleanup_QuarantineMailboxFull </span> <br /> </td> 
   <td> <p>Hier kunt u de vertraging definiëren waarna de quarantines uit de database worden verwijderd.</p><p> Deze optie wordt automatisch gecreeerd zodra de vertraging binnen de interface wordt gewijzigd. Als u de waarde in de lijst met opties wijzigt, moet deze worden uitgedrukt in seconden.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsCleanup_RecycledDeliveryPurgeDelay </span> <br /> </td> 
   <td> <p>Hiermee kunt u de vertraging definiëren waarna gerecycleerde leveringen uit de database worden verwijderd.</p><p> Deze optie wordt automatisch gecreeerd zodra de vertraging binnen de interface wordt gewijzigd. Als u de waarde in de lijst met opties wijzigt, moet deze worden uitgedrukt in seconden.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsCleanup_RejectsPurgeDelay </span> <br /> </td> 
   <td> <p>Hier kunt u de vertraging definiëren waarna de afwijzing uit de database wordt verwijderd.</p><p>Deze optie wordt automatisch gecreeerd zodra de vertraging binnen de interface wordt gewijzigd. Als u de waarde in de lijst met opties wijzigt, moet deze worden uitgedrukt in seconden.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsCleanup_TrackingLogPurgeDelay </span> <br /> </td> 
   <td> <p>Hiermee kunt u de vertraging definiëren waarna trackinglogboeken uit de database worden verwijderd.</p><p>Deze optie wordt automatisch gecreeerd zodra de vertraging binnen de interface wordt gewijzigd. Als u de waarde in de lijst met opties wijzigt, moet deze worden uitgedrukt in seconden.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsCleanup_TrackingStatePurgeDelay </span> <br /> </td> 
   <td><p> Hier kunt u de vertraging definiëren waarna trackingstatistieken uit de database worden verwijderd.</p><p> Deze optie wordt automatisch gecreeerd zodra de vertraging binnen de interface wordt gewijzigd. Als u de waarde in de lijst met opties wijzigt, moet deze worden uitgedrukt in seconden.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsCleanup_VisitorPurgeDelay </span> <br /> </td> 
   <td> <p>Hiermee kunt u de vertraging definiëren waarna bezoekers uit de database worden verwijderd.</p><p> Deze optie wordt automatisch gecreeerd zodra de vertraging binnen de interface wordt gewijzigd. Als u de waarde in de lijst met opties wijzigt, moet deze worden uitgedrukt in seconden.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsCleanup_WorkflowResultPurgeDelay </span> <br /> </td> 
   <td> <p>Hiermee kunt u de vertraging definiëren waarna de workflowresultaten uit de database worden verwijderd.</p><p> Deze optie wordt automatisch gecreeerd zodra de vertraging binnen de interface wordt gewijzigd. Als u de waarde in de lijst met opties wijzigt, moet deze worden uitgedrukt in seconden.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> WdbcCapabilities_AzureDw </span> <br /> </td> 
   <td> Azure SQL Datawarehouse-verbindingsopties.<br /> </td> 
  </tr>
   <tr> 
   <td> <span class="uicontrol"> WdbcKillSessionPolicy </span> <br /> </td> 
   <td>Laat u onvoorwaardelijk gedrag van het Einde op alle werkschema's en de gegevensbestandvragen van PostgreSQL volgens de volgende potentiële waarden beïnvloeden:<ul>
    <li><p>0 - standaard: stopt werkstroomproces, geen invloed op de database<p></li>
    <li><p>1 - pg_cancel_backend: stopt workflowproces en annuleert query in de database<p></li>
    <li><p>2 - pg_terminate_backend: stopt het werkstroomproces en beëindigt de query in de database<p></li></ul></td> 
  </tr>  
    <tr> 
   <td> <span class="uicontrol"> WdbcOptions_TableSpaceUser </span> <br /> </td> 
   <td> Naam van de tabelruimte die de gegevens van de Adobe Campaign-tabbladen moet bevatten.<br /> zie <a href="../../installation/using/creating-and-configuring-the-database.md"> Creërend en vormend het gegevensbestand </a>.</td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> WdbcOptions_TableSpaceIndex </span> <br /> </td> 
   <td> Naam van de tabelruimte die de indexen van de Adobe Campaign-tabbladen moet bevatten.<br /> zie <a href="../../installation/using/creating-and-configuring-the-database.md"> Creërend en vormend het gegevensbestand </a>.</td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> WdbcOptions_TableSpaceWork </span> <br /> </td> 
   <td> Naam van de tabelruimte die de gegevens van de Adobe Campaign-werktabellen moet bevatten.<br /> zie <a href="../../installation/using/creating-and-configuring-the-database.md"> Creërend en vormend het gegevensbestand </a>.</td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> WdbcOptions_TableSpaceWorkIndex </span> <br /> </td> 
   <td> Naam van de tabelruimte die de indexen van de Adobe Campaign-werktabellen moet bevatten.<br /> zie <a href="../../installation/using/creating-and-configuring-the-database.md"> Creërend en vormend het gegevensbestand </a>.</td> 
  </tr> 
    <tr> 
   <td> <span class="uicontrol"> WdbcOptions_TempDbName </span> <br /> </td> 
   <td> Staat u toe om een afzonderlijk gegevensbestand voor het werken van lijsten op de Server van Microsoft te vormen SQL, om steunen en replicatie te optimaliseren. De optie komt overeen met de naam van de tijdelijke database: werktabellen worden in deze database geschreven, indien opgegeven. Voorbeeld: 'tempdb.dbo'. (de naam moet eindigen met een punt). <a href="../../production/using/rdbms-specific-recommendations.md#microsoft-sql-server"> las meer </a> <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> WdbcTimeZone </span> <br /> </td> 
   <td> Tijdzone van de instantie Adobe Campaign. Zie <a href="../../installation/using/time-zone-management.md#configuration" target="_blank"> Configuratie </a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> WdbcUseNChar </span> <br /> </td> 
   <td> Zijn de het koordgebieden van het gegevensbestand die met NChar worden bepaald?<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> WdbcUseTimeStampWithTZ </span> <br /> </td> 
   <td> Sla de "datetime"gebieden van het gegevensbestand timezone info op?<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> XtkDatabaseId </span> <br /> </td> 
   <td> ID van de database. Begint bij 'u' voor Unicode DataBase.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> XtkInstancePrefix </span> <br /> </td> 
   <td> Prefix die aan automatisch geproduceerde interne namen wordt toegevoegd.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> XtkQuery_Schema_LineCount </span> <br /> </td> 
   <td> Maximum aantal resultaten die door een vraag op xtk:schema en xtk:srcSchema zijn teruggekeerd.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> XtkSequence_AutoGeneration </span> <br /> </td> 
   <td> Alle aangepaste schema's, die na deze tijd worden gemaakt, met automatische piloot="true" en zonder het kenmerk "pkSequence" krijgen een automatisch gegenereerde reeks "auto_ 
    &lt;schemanamespace&gt; 
     &lt;schemaname&gt;
       _seq. 
   </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NlMigration_KeepFolderStructure </span> <br /> </td> 
   <td> Tijdens migratie wordt de boomstructuur automatisch opnieuw ingedeeld op basis van de nieuwe versienormen.<br /> Met deze optie kunt u de automatische migratie van de boomstructuur uitschakelen. Als u het gebruikt, na migratie zult u verouderde omslagen moeten schrappen, de nieuwe omslagen toevoegen en alle noodzakelijke controles in werking stellen.<br /> 
    <ul> 
     <li> <p> <span class="uicontrol"> Type van Gegevens:</span> Geheel</p> </li> 
     <li> <p> <span class="uicontrol"> Waarde (tekst) </span> : 1 </p> </li> 
    </ul> Deze optie zou slechts moeten worden gebruikt als de uit-van-de-doos navigatieboom teveel veranderingen heeft ondergaan.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsLastErrorStatCoalesce </span> <br /> </td> 
   <td> Laatste verwerkingsdatum van <span class="uicontrol"> NmsEmailErrorStat </span> lijstschoonmaakbeurt.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> PostUpgradeLastError </span> <br /> </td> 
   <td> Informatie betreffende de fout die in Postupgrade, volgende de syntaxis hieronder voorkwam:<br /> <strong> {Build number}:{mode: pre/post/...}:{The 'lessThan'/'greaterOrEquelThan' where error occurred + sub-step} </strong> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> XtkCleanup_NoStats </span> <br /> </td> 
   <td> Ga de "1"waarde in zodat de update van statistieken niet door het schoonmaakbeurtwerkschema wordt uitgevoerd.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Integratie {#integration}

<table> 
 <thead> 
  <tr> 
   <th> Naam van optie </th> 
   <th> Beschrijving </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol"> AEMResourceTypeFilter </span> <br /> </td> 
   <td> Typen AEM die in Adobe Campaign kunnen worden gebruikt. Waarden moeten door komma's worden gescheiden.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> nmsPipeline_config </span> <br /> </td> 
   <td> Hiermee kunt u Experience Cloud Triggers configureren. Het gegevenstype is 'lange tekst' en moet de JSON-indeling hebben. Zie <a class="anchorLink" href="https://helpx.adobe.com/campaign/kb/triggers-and-campaign.html#PipelineoptionNmsPipelineConfig" target="_blank"> hoe te om de Trekkers van het Experience Cloud met Adobe Campaign Classic </a> te gebruiken.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> LASTIMPORT_&lt;%=instance.internalName%&gt;_&lt;%=activityName%&gt; </span> <br /> </td> 
   <td> Deze optie wordt gebruikt wanneer het invoeren van gegevens van een derdesysteem door een schakelaar van CRM. Als u de optie inschakelt, kunt u alleen objecten verzamelen die zijn gewijzigd sinds de laatste importbewerking. Deze optie moet handmatig worden gemaakt en als volgt worden ingevuld: 
    <ul> 
     <li> <p> <span class="uicontrol"> Interne naam </span> : LASTIMPORT_&lt;%=instance.internalName%&gt;_&lt;%=activityName%&gt;</p> </li> 
     <li> <p> <span class="uicontrol"> Waarde (gebied) </span> : datum van de laatste invoer, met het 2&rbrace; s formaat van yyyy/MM/dd hh.:mm: </p> </li> 
    </ul><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> TNT_EdgeServer </span> <br /> </td> 
   <td> Adobe Target-server gebruikt voor integratie. Deze optie is standaard al geselecteerd. Deze waarde komt overeen met de Adobe Target Domain Server, gevolgd door de waarde /m2. Bijvoorbeeld: tt.omtrdc.net/m2.<br /> zie <a href="../../integrations/using/configuring-the-integration-with-adobe-target.md"> deze sectie </a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> TNT_TenantName </span> <br /> </td> 
   <td> Naam van Adobe Target-organisatie. Deze waarde komt overeen met de naam van de Adobe Target-client.<br /> zie <a href="../../integrations/using/configuring-the-integration-with-adobe-target.md"> deze sectie </a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> AAM_DataSourceId </span> <br /> </td> 
   <td> Optie die voor de integratie met Adobe Audience Manager wordt gebruikt.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> AAM_DestinationId </span> <br /> </td> 
   <td> Optie die voor de integratie met Adobe Audience Manager wordt gebruikt.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> WdbcCapabilities_Teradata </span> <br /> </td> 
   <td> Verbindingsopties voor teradata.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> WdbcCapabilities_Hive </span> <br /> </td> 
   <td> Verbindingsopties voor Hive.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Aanbiedingen {#offers}

<table> 
 <thead> 
  <tr> 
   <th> Naam van optie </th> 
   <th> Beschrijving </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol"> NmsCoupons_MaxPerTransac </span> <br /> </td> 
   <td> Aantal coupons dat per SQL transactie wordt bijgewerkt.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsInteraction_LastPropositionSynchControl_ </span> <br /> </td> 
   <td> '+ [schema van voorstel] + "_" + extAccountSource.@executeInstanceId + [het schema van het voorstel] + "_" + vars.executeInstanceIdFilter <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsInteraction_LastPropositionSynchExec_</span> <br /> </td> 
   <td> '+ [ schema van de projectie] + "_" + extAccountSource.@executeInstanceId + "_" + extAccountTarget.@executeInstanceId<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsInteraction_SynchWorkflowIds </span> <br /> </td> 
   <td> Synchronization workflow tracking.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsInteraction_UseDaemon </span> <br /> </td> 
   <td> Laat/maak asynchrone het schrijven van het voorstel toe onbruikbaar ("0"om onbruikbaar te maken, "1"om toe te laten).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsModule_CouponsEnabled </span> <br /> </td> 
   <td> Hiermee kunt u coupons inschakelen.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Server {#server}

<table> 
 <thead> 
  <tr> 
   <th> Naam van optie </th> 
   <th> Beschrijving </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol"> NmsExecutionInstanceId </span> <br /> </td> 
   <td> Id van uitvoeringsinstantie.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsServer_CustomerId </span> <br /> </td> 
   <td> De identiteitskaart van de klant gebruikte toen het verzenden van het het facturerings rapport.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsServer_IntranetURL </span> <br /> </td> 
   <td> Interne basis-URL voor toegang tot de toepassingsserver.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsServer_LastPostUpgrade </span> <br /> </td> 
   <td> Bouwt aantal van de AC instantie vóór de laatste verbetering.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsServer_URL </span> <br /> </td> 
   <td> Basis URL van de openbare server van de Webtoepassing.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> XtkPassUnknownSQLFunctionsToRDBMS </span> <br /> </td> 
   <td> Hiermee kunt u oude niet-gedeclareerde SQL-functies blijven gebruiken na het migreren. Wij adviseren sterk tegen het gebruiken van deze optie wegens de veiligheidsrisico's het introduceert.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Tracking {#tracking}

<table> 
 <thead> 
  <tr> 
   <th> Naam van optie </th> 
   <th> Beschrijving </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol"> NmsTracking_Available </span> <br /> </td> 
   <td> Optie waarmee u reeksspatiëring kunt activeren.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsTracking_ClickFormula </span> <br /> </td> 
   <td> Het getraceerde-URL berekeningsmanuscript.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsTracking_ExtAccount </span> <br /> </td> 
   <td> Hiermee kunt u de externe account van de trackingserver definiëren.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsTracking_Instance </span> <br /> </td> 
   <td> Hier kunt u de instantienaam op de trackingserver definiëren.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsTracking_LastConsolidation </span> <br /> </td> 
   <td> De laatste keer is de het volgen informatie met nieuwe gegevens geconsolideerd.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsTracking_OpenFormula </span> <br /> </td> 
   <td> URL-berekeningsscript openen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsTracking_Password </span> <br /> </td> 
   <td> Wachtwoord voor de volgende server <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsTracking_Pointer </span> <br /> </td> 
   <td> De wijzer houdt spoor van de laatste berichtgebeurtenissen die door hun IDs en datum werden verwerkt.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsTracking_SecureServerUrl </span> <br /> </td> 
   <td> Beveilig URL van de frontal volgende server.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsTracking_ServerUrl </span> <br /> </td> 
   <td> URL van de frontale volgende server.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsTracking_ServerUrlList </span> <br /> </td> 
   <td> Lijst van URLs die wordt gebruikt om de volgende servers te contacteren.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsTracking_UserAgentRules </span> <br /> </td> 
   <td> Browser-identificatie regelreeks.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsTracking_WebFormula </span> <br /> </td> 
   <td> Script dat wordt gebruikt om Web het volgen markeringen gegevens te verwerken.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsTracking_WebTrackingDelivery </span> <br /> </td> 
   <td> Naam van de virtuele levering die voor Web het volgen beheer wordt ontworpen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> NmsTracking_WebTrackingMode </span> <br /> </td> 
   <td> Laat u de Web het volgen wijze bepalen.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Privacy {#privacy}

<table> 
 <thead> 
  <tr> 
   <th> Naam van optie </th> 
   <th> Beschrijving </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol"> Privacy_Request_ConfirmDeletePending </span> <br /> </td> 
   <td> Als optie 1 wordt geselecteerd, moet u manueel de schrapping in de interface in een tweede stap bevestigen. Anders, zullen de gegevens zonder bevestiging worden geschrapt.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> Privacy_Request_ConfirmDeletePendingDelay </span> <br /> </td> 
   <td> De vertraging tussen verzoek wacht op het schrappen van bevestiging en verzoek wordt geannuleerd.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> Privacy_Request_MaxErrorAllowed </span> <br /> </td> 
   <td> Het maximumaantal toegestane fouten wanneer het verwerken/het schrappen van een privacyverzoek.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> Privacy_Request_PurgeDelay </span> <br /> </td> 
   <td> De vertraging tussen verzoek wordt gecreeerd op de rij en de verzoekgegevens wordt geschrapt.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## LDAP {#ldap}

<table> 
 <thead> 
  <tr> 
   <th> Naam van optie </th> 
   <th> Beschrijving </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol"> XtkLoad_Active </span> <br /> </td> 
   <td> Schakel LDAP-server in om gebruikers te verifiëren en gebruikers autorisaties te geven.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> XtkLoad_AppLogin </span> <br /> </td> 
   <td> Login van de toepassing om de server voor diverse onderzoeken te contacteren.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> XtkLoad_AppPassword </span> <br /> </td> 
   <td> Gecodeerd wachtwoord voor de toepassingsaanmelding.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> XtkLoad_AutoOperator </span> <br /> </td> 
   <td> Automatisch aanmaken van operatoren en rechten inschakelen in Adobe Campaign.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> XtkLDAP_DN </span> <br /> </td> 
   <td> De formule van de berekening voor LDAP DN wordt gebaseerd op login.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> XtkLdap_DNSsearch </span> <br /> </td> 
   <td> DN-zoekopdracht inschakelen in map.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> XtkLdap_DNSsearchBase </span> <br /> </td> 
   <td> Zoekbasis.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> XtkLDAP_DNSsearchFilter </span> <br /> </td> 
   <td> DN-zoekfilter.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> XtkLdap_DNSsearchScope </span> <br /> </td> 
   <td> Zoekbereik.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> XtkLDAP_Mechanism </span> <br /> </td> 
   <td> Het type van authentificatie dat wordt gebruikt om de server te contacteren LDAP (onbewerkt, md5, lds, ntlm, dpa).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> XtkLDAP_Rights </span> <br /> </td> 
   <td> Laat synchronisatie van vergunningen en groepen van LDAP folder aan genoemde rechten in Adobe Campaign toe.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> XtkLoad_RightsAttr </span> <br /> </td> 
   <td> LDAP-kenmerk met de machtigingsnaam.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> XtkLoad_RightsBase </span> <br /> </td> 
   <td> Zoekbasis.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> XtkLoad_RightsFilter </span> <br /> </td> 
   <td> Filter van het onderzoek naar gebruikersvergunningen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> XtkLoad_RightsMask </span> <br /> </td> 
   <td> Uitdrukking om de namen van de rechten van Adobe Campaign uit de toestemmingen te halen LDAP.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> XtkLoad_RightsScope </span> <br /> </td> 
   <td> Zoekbereik.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> XtkLDAP_Server </span> <br /> </td> 
   <td> LDAP-serveradres (het is mogelijk om een poort op te geven door ':' als scheidingsteken op te geven).<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Webformulieren {#web-forms}

<table> 
 <thead> 
  <tr> 
   <th> Naam van optie </th> 
   <th> Beschrijving </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol"> XtkUseScrollBar </span> <br /> </td> 
   <td> De waarde die is ingesteld op 1, staat toe dat de schuifbalk wordt toegevoegd aan detailformulieren.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> XtkWebForm_Instance </span> <br /> </td> 
   <td> Instance to be used for web form invalidation in 'other server(s)' mode.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> XtkWebForm_Password </span> <br /> </td> 
   <td> Wachtwoord van de instantie dat moet worden gebruikt voor webformuliervalidatie in de modus 'Andere server(s)'.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> XtkWebForm_ServersMode </span> <br /> </td> 
   <td> Optie waarmee u de validatiemodus van webformulieren kunt opgeven: standaard lokaal, gebruikt u trackingservers als de optie 'tracking' is en gebruikt u een gepersonaliseerde lijst met de optie 'Andere server(s)'.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol"> XtkWebForm_ServersURLs </span> <br /> </td> 
   <td> Persoonlijke adreslijst van servers waarmee contact moet worden opgenomen voor validatie van webformulieren (modus "Andere server(s)").<br /> </td> 
  </tr> 
 </tbody> 
</table>
