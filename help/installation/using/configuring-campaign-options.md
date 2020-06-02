---
title: Campagneopties configureren
seo-title: Campagneopties configureren
description: Campagneopties configureren
seo-description: null
page-status-flag: never-activated
uuid: 32e85e41-6898-4fb3-90c8-2201ceea2e91
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: appendices
discoiquuid: 9c1884f6-1dd8-41ab-b8dc-604c8cc2dc89
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 5b6b4fd2b21f90a88744736b499eab1b0764774e
workflow-type: tm+mt
source-wordcount: '3740'
ht-degree: 0%

---


# Lijst met klassieke opties voor campagne{#configuring-campaign-options}

Met het **[!UICONTROL Administration / Platform / Options]** knooppunt kunt u de opties voor Adobe-campagnes configureren.

>[!NOTE]
>
>U kunt de opties voor Adobe-campagnes alleen aanpassen of bijwerken door deskundige gebruikers.

Sommige hiervan zijn ingebouwd tijdens de installatie van Campagne en andere kunnen handmatig worden toegevoegd wanneer dat nodig is. Welke opties beschikbaar zijn, is afhankelijk van de pakketten die bij de instantie worden geïnstalleerd.

## Aflevering {#delivery}

<table> 
 <thead> 
  <tr> 
   <th> Naam van optie </th> 
   <th> Beschrijving </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">Deliverability_LastBroadLogMsgDate</span> <br /> </td> 
   <td> Datum van laatste wideLogMsg die van de leveringsinstantie wordt teruggewonnen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Deliverability_LastBroadLogMsgSent</span> <br /> </td> 
   <td> Datum van laatste wideLogMsg die naar de leveringsinstantie wordt verzonden.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">DmRendering_cuid</span> <br /> </td> 
   <td> Id van leveringsrapporten. Neem contact op met de technische ondersteuning voor uw id.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">DmRendering_SeedTargets</span> <br /> </td> 
   <td> Lijst van schema's waarvoor u testadressen voor het Teruggeven Inbox wilt gebruiken. (elementnamen worden met komma's van elkaar gescheiden), bijvoorbeeld: custom_nms_receiving.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NMS_ActivateOwnerConfirmation</span> <br /> </td> 
   <td><p> Hiermee kunt u toestaan dat de exploitant die verantwoordelijk is voor de levering de verzending bevestigt, als een specifieke exploitant of groep exploitanten is aangewezen voor het starten van een levering in de eigendommen van de levering.</p><p> Hiervoor activeert u de optie door "1" als waarde in te voeren. Voer 0 in om deze optie te deactiveren.</p><p> Het proces voor bevestiging verzenden werkt dan als standaard: alleen de exploitant of groep van exploitanten die voor de verzending zijn aangewezen in de leveringseigenschappen (of een beheerder) kan de verzending bevestigen en uitvoeren. Zie <a href="../../campaign/using/marketing-campaign-deliveries.md#starting-an-online-delivery">deze sectie</a>.</p> </td> 
   <tr> 
   <td> <span class="uicontrol">Nms_DefaultRcpSchema</span> <br /> </td> 
   <td> Adobe Campagne gebruikt een globale variabele "Nms_DefaultRcpSchema"aan dialoog met het gebrek ontvankelijke gegevensbestand (nms:ontvanger).<br /> De waarde van de optie moet overeenkomen met de naam van het schema dat overeenkomt met de tabel voor externe ontvangers.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBilling_MainActionThreshold</span> <br /> </td> 
   <td> Minimumaantal ontvangers om een levering als belangrijkste in het factureringsrapport te beschouwen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_DefaultProvider</span> <br /> </td> 
   <td> Standaard verpletterend dienstverlener voor de nieuwe malplaatjes.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_LogsPerTransac</span> <br /> </td> 
   <td> Aantal bredeLogboeken die voor een levering in één keer worden gecreeerd.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_MaxDelayPerTransac</span> <br /> </td> 
   <td> Invoeging (in lijst) van logboeken (wideLogs) per transacties: aantal rijen dat per batch moet worden verwerkt.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_MidAnalyzeBatchSize</span> <br /> </td> 
   <td> Groepering van de grootte van de leveringsonderdelen bij het analyseren van leveringen uit de midsourcing.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_MsgValidityDuration</span> <br /> </td> 
   <td> Standaardleveringsperiode voor een levering (in seconden).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_RegexRules</span> <br /> </td> 
   <td> Reguliere expressies voor het normaliseren van leveringsberichten.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_RemoveBlackList</span> <br /> </td> 
   <td> Als u "1" opgeeft als waarde, kunt u ontvangers uitsluiten die niet langer contact met u willen opnemen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_RemoveDuplicatesRecipients</span> <br /> </td> 
   <td> Als u "1" opgeeft als waarde, kunt u dubbele waarden automatisch negeren.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_ErrorAddressMasks</span> <br /> </td> 
   <td> Hiermee kunt u de syntaxis definiëren van het adres Fout dat wordt gebruikt bij het beantwoorden van een bericht.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_FromAddressMasks</span> <br /> </td> 
   <td> Hier kunt u de syntaxis definiëren van het adres Van dat wordt gebruikt bij het verzenden van een bericht.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MaxRetry</span> <br /> </td> 
   <td> Maximumaantal pogingen tijdens de analyse.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_PublishingScript</span> <br /> </td> 
   <td> Publicatiescript.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_NoCountBroadLogMsgPush</span> <br /> </td> 
   <td> Schakel het aantal wideLogMsg voor pushberichten uit.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDeliveryWizard_ShowDeliveryWeight</span> <br /> </td> 
   <td> Geef het gewicht van het bericht weer in de wizard voor aflevering.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_DefaultErrorAddr</span> <br /> </td> 
   <td> Het standaard 'fout'-e-mailadres op instantieniveau wordt gebruikt voor e-maillevering als dit door de gebruiker leeg wordt gelaten.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_DefaultFromAddr</span> <br /> </td> 
   <td> Het standaard e-mailadres 'van' op instantieniveau wordt gebruikt voor e-maillevering als deze door de gebruiker leeg wordt gelaten.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_DefaultReplyToAddr</span> <br /> </td> 
   <td> Het standaard e-mailadres 'repliek' op instantieniveau dat wordt gebruikt voor e-maillevering als deze door de gebruiker leeg wordt gelaten.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_ExpOrganization</span> <br /> </td> 
   <td> Algemene naam van de klant. Gebruikt in sommige waarschuwingsberichten die aan de ontvangers worden getoond.<br /> "Je ontvangt dit bericht omdat je contact hebt gehad met ***** of een gelieerde onderneming. Geen berichten meer ontvangen van *****".<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_FromName</span> <br /> </td> 
   <td> Het standaard e-maillabel 'from' op instantieniveau wordt gebruikt voor e-maillevering als dit door de gebruiker leeg wordt gelaten.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_ReplyToName</span> <br /> </td> 
   <td> Het standaard e-maillabel 'repliek' op instantieniveau wordt gebruikt voor e-maillevering als dit door de gebruiker leeg wordt gelaten.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_RetryCount</span> <br /> </td> 
   <td> Periode tussen twee pogingen van een e-mailbericht (in seconden).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_RetryPeriod</span> <br /> </td> 
   <td> Periode van opnieuw proberen voor e-mailberichten.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsForecast_MsgWeightFormula</span> <br /> </td> 
   <td> Formule die wordt gebruikt om de weging van een bericht voor voorlopige levering te berekenen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInmail_WhitelistEmails</span> <br /> </td> 
   <td> Lijst van geoorloofde het door:sturen e-mailadressen (van de binnenkomende module van de postverwerking). De adressen moeten door komma's (of * worden gescheiden om allen toe te staan). Bijvoorbeeld xyz@abc.com,pqr@abc.com.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsLine_AESKey</span> <br /> </td> 
   <td> AES-sleutel die wordt gebruikt in het servlet 'lineImage' om de URL's (LINE-kanaal) te coderen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNPAI_EmailMaxError</span> <br /> </td> 
   <td> Op kanaal "email" (standaard gebruiken): Maximale aantal fouten dat wordt geaccepteerd, voor SOFT-fouten tijdens het verzenden voordat de ontvanger in quarantaine wordt geplaatst.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNPAI_EmailSignificantErrorDelay</span> <br /> </td> 
   <td> Op kanaal "email" (standaard gebruiken): Minimale periode die moet worden doorgebracht sinds de vorige SOFT-fout waarnaar wordt verwezen, voordat u rekening houdt met een nieuwe SOFT-fout.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNPAI_MobileMaxError</span> <br /> </td> 
   <td> Op kanaal "mobile": Maximale aantal fouten dat wordt geaccepteerd, voor SOFT-fouten tijdens het verzenden voordat de ontvanger in quarantaine wordt geplaatst.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNPAI_MobileSignificantErrorDelay</span> <br /> </td> 
   <td> Op kanaal "mobile": Minimale periode die moet worden doorgebracht sinds de vorige SOFT-fout waarnaar wordt verwezen, voordat u rekening houdt met een nieuwe SOFT-fout.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsMidSourcing_LogsPeriodHour</span> <br /> </td>
   <td> Staat een maximumperiode (die in uren wordt uitgedrukt) toe om te worden gespecificeerd het aantal uitzendingen te beperken die telkens als het synchronisatiewerkschema wordt uitgevoerd worden teruggekregen.</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsMidSourcing_PrepareFlow</span> <br /> </td> 
   <td> Maximum aantal vraag in sessie MidSourcing, die parallel (3 door gebrek) kan worden in werking gesteld.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsMTA_Alert_Delay</span> <br /> </td> 
   <td> Aangepaste vertraging (in minuten) waarna een levering wordt beschouwd als 'vertraagd', de standaardwaarde is 30 minuten.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_DeliveryPreparationWindow</span> <br /> </td> 
   <td><p>Deze optie wordt gebruikt door de technische workflow <span class="uicontrol"><a href="../../workflow/using/campaign.md">operationMgt</a></span> wanneer het aantal actieve leveringen wordt geteld.</p>Hiermee kunt u het aantal dagen definiëren waarboven leveringen met een inconsistente status worden uitgesloten van het aantal lopende leveringen.</p><p>De standaardwaarde is "7", wat betekent dat inconsistente leveringen ouder dan 7 dagen worden uitgesloten.</p></td> 
  </tr>
  <tr> 
   <td> <span class="uicontrol">NmsPaper_SenderLine1</span> <br /> </td> 
   <td> Regel 1 van het adres van de afzender.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsPaper_SenderLine3</span> <br /> </td> 
   <td> Regel 3 van het adres van de afzender.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsPaper_SenderLine4</span> <br /> </td> 
   <td> Regel 4 van het adres van de afzender.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsPaper_SenderLine6</span> <br /> </td> 
   <td> Regel 6 van het adres van de afzender.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsPaper_SenderLine7</span> <br /> </td> 
   <td> Regel 7 van het adres van de afzender.<br /> </td> 
  </tr>
  <tr> 
   <td> <span class="uicontrol">NmsServer_MirrorPageUrl</span> <br /> </td> 
   <td> URL van de spiegelpaginaserver (door gebrek, zou identiek moeten zijn aan NmsTracking_ServerUrl).<br /> Het is de standaardwaarde van e-mailleveringen wanneer URL niet in de verpletterende definitie wordt gespecificeerd.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsSMS_Priority</span> <br /> </td> 
   <td> Parameters van verzonden SMS-berichten: informatie die aan de gateway van SMS wordt overgebracht om op de berichtprioriteit te wijzen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsSMS_RetryCount</span> <br /> </td> 
   <td> Aantal pogingen bij het verzenden van SMS-berichten.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsSMS_RetryPeriod</span> <br /> </td> 
   <td> Periode waarin opnieuw pogingen van SMS-berichten worden uitgevoerd.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsUserAgentStats_LastConsolidation</span> <br /> </td> 
   <td> Laatste consolidatiedatum voor <span class="uicontrol">NmsUserAgent</span> -statistieken.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsWebSegments_LastStates</span> <br /> </td> 
   <td> Naam van de optie die de websegmenten en hun status bevat.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkBarcode_SpecialChar</span> <br /> </td> 
   <td> Schakel ondersteuning voor speciale tekens voor Code128 in of uit.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkEmail_Characters</span> <br /> </td> 
   <td> Geldige tekens voor een e-mailadres.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Restrict_EditXML</span> </td> 
   <td> Voeg deze optie met de waarde "0" toe om de uitgave van de XML-code van de leveringen uit te schakelen (klik met de rechtermuisknop of <span class="uicontrol">bewerk de XML-bron</span> of de sneltoets <span class="uicontrol">CTRL + F4</span> ).<br /> </td> 
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
   <td> <span class="uicontrol">NcmRessourcesDir</span> <br /> </td> 
   <td> Locatie van bronnen voor publicatie in de Adobe Campagne-clientconsole. Zie <a href="../../delivery/using/formatting.md#image-referencing">deze sectie</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NcmRessourcesDirPreview</span> <br /> </td> 
   <td> Locatie van bronnen voor voorvertoning in de Adobe Campagne-clientconsole. Zie <a href="../../delivery/using/formatting.md#image-referencing">deze sectie</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_DefaultIgnoredImage</span> <br /> </td> 
   <td> Lijst met URL-maskers voor de afbeeldingen die tijdens het uploaden zijn overgeslagen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_ImagePublishing</span> </td> 
   <td> Configuratie van het uploaden van afbeeldingen. De waarden kunnen none / tracking / script / list zijn (kan worden overschreven door de optionele instellingen van de operator). </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_ImageSubDirectory</span> <br /> </td> 
   <td> De map waarin de afbeeldingen op de server moeten worden opgeslagen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_LogoPath</span> <br /> </td> 
   <td> Ruimte voor het weergeven van logo's.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NcmPublishingDir</span> <br /> </td> 
   <td> Hoofdmap voor publicaties.<br /> Raadpleeg <a href="../../delivery/using/using-a-content-template.md">deze sectie</a>voor meer informatie over het genereren van HTML- en tekstinhoud.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkImageUrl</span> <br /> </td> 
   <td> Hiermee kunt u de server definiëren waarop de afbeeldingen worden opgeslagen die in de leveringen worden gebruikt, zodat de browser ze kan ophalen.<br /> Voor buildversies &lt;= 5098 gebruiken we de URL van de afbeeldingen die naar de instantie zijn geüpload.<br /> Voor buildversies &gt; 5098 gebruiken we in plaats daarvan de openbare URL van de levering of de URL van de optie <span class="uicontrol">XtkFileRes_Public_URL</span> .<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MediaInstance</span> <br /> </td> 
   <td> Hiermee kunt u de instantienaam configureren voor het uploaden van afbeeldingen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MediaPassword</span> <br /> </td> 
   <td> Hiermee kunt u het wachtwoord configureren voor het uploaden van afbeeldingen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MediaServers</span> <br /> </td> 
   <td> Hiermee kunt u de media-URL's configureren voor het uploaden van afbeeldingen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_MsgWebValidityDuration</span> <br /> </td> 
   <td> Standaardgeldigheidsperiode voor onlinebronnen van een levering (in seconden).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkFileRes_Public_URL</span> <br /> </td> 
   <td> Nieuwe URL voor openbare bronbestanden.<br /> </td> 
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
   <td> <span class="uicontrol">CrmMarketingActivityWindow</span> <br /> </td> 
   <td> De handelsgeschiedenis die gedurende dit aantal maanden werd getoond.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_Duration</span> <br /> </td> 
   <td> Standaardgeldigheidsperiode van een campagne (in seconden).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_LimitConcurrency</span> <br /> </td> 
   <td> Maximumaantal bezorgings-/workflow-/hypothese-/simulatietaken dat in één keer kan worden verwerkt, gestart door de workflow operationMgt.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_OperationMgtDebug</span> <br /> </td> 
   <td> Staat u toe om de technische <a href="../../workflow/using/campaign.md">werkschemauitvoering te controleren operationMgt</a> . Wanneer geactiveerd (waarde "1"), wordt de uitvoeringsinformatie geregistreerd in de logboeken van de werkschemacontrole.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_TimeRange</span> <br /> </td> 
   <td> Tijdsperiode voor het bepalen van de doelwit- en winningsomstandigheden in de geplande modus.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Workflow_AnalysisThreshold</span> <br /> </td> 
   <td> Aantal betrokken verslagen waarna de lijststatistieken automatisch worden opnieuw berekend.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkReport_Logo</span> <br /> </td> 
   <td> Logo dat in de hoogste juiste hoek van de uitgevoerde rapporten moet worden getoond.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_PausedWorkflowPeriod</span> <br /> </td> 
   <td> Aantal dagen dat moet worden gewacht tussen controles op gepauzeerde workflows.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCampaign_Activate_OwnerConfirmation</span> <br /> </td> 
   <td> Activeer de validatie van leveringen door de eigenaar van de bewerking door "1" in te voeren als waarde. Voer 0 in om deze optie te deactiveren.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsAsset_JavascriptExt</span> <br /> </td> 
   <td> Aanvullende JS-bibliotheek die moet worden geladen in de activiteit "Marketing resource notifications" in de werkstroom.<br /> </td> 
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
   <td> <span class="uicontrol">XtkAcceptOldPasswords</span> <br /> </td> 
   <td> (Compatibiliteitsmodus installeren: build&gt;6000) Als deze optie is geactiveerd (waarde "1"), kunt u oude wachtwoorden die in de database zijn opgeslagen, gebruiken voor de verbinding met externe accounts of met de instantie.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkKey</span> <br /> </td> 
   <td> Deze sleutel wordt gebruikt om de meeste wachtwoorden in het gegevensbestand te coderen. (externe accounts, LDAP-wachtwoord...)<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Allow_PrivilegeEscalation</span> <br /> </td> 
   <td> Als 1 wordt geselecteerd, deze optie om privilegeEscalation in javascript toe te staan.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Disable_ControlsOnFileDownload</span> <br /> </td> 
   <td> Als 1 wordt geselecteerd, onbruikbaar maakt deze optie ACL controles tijdens een dossierdownload (via fileDownload.jsp).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Disable_JSFileSandboxing</span> <br /> </td> 
   <td> Als 1 wordt geselecteerd, onbruikbaar deze optie het dossier het zandbakken binnen Javascript.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_SaveOptions_AllowNonAdmin</span> <br /> </td> 
   <td> Indien ingesteld op 'true', geautoriseerde niet-admin-operator om de xtkOption-waarden bij te werken via de implementatietovenaar.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSecurity_Unsafe_DecryptString</span> <br /> </td> 
   <td> Als 1 wordt geselecteerd, staat deze optie toe om decryptString te gebruiken om sommige wachtwoorden te decrypteren.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkTraceDeleteLogin</span> <br /> </td> 
   <td> Voer de waarde "1" in om de verwijdering van elementen met audittrailinformatie in de mData te traceren door de wijziging van het veld "gewijzigd door" voordat de record wordt verwijderd.<br /> </td> 
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
   <td> <span class="uicontrol">MC_EnrichmentCustomJs</span> <br /> </td> 
   <td> JavaScript-bibliotheek die moet worden gepersonaliseerd voor het verrijken van gebeurtenissen. Moet de uitvoering van deze twee functies bevatten:<br /> 
    <ul> 
     <li> <p> <span class="uicontrol">enrichRtEvents(aiEventId);</span> : Verrijkt en slaat gebeurtenissen in het gegevensbestand op (waar <span class="uicontrol">aiEventId</span> aan de verwerkte lijst van gebeurtenissen in real time beantwoordt).</p> </li> 
     <li> <p> <span class="uicontrol">enrichBatchEvents(aiEventId);</span> : Verrijkt en slaat gebeurtenissen in het gegevensbestand op (waar <span class="uicontrol">aiEventId</span> aan de lijst van identiteitskaart verwerkte partijgebeurtenissen beantwoordt).</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_LastUpdateFromBL</span> <br /> </td> 
   <td> Datum van de laatste statusupdate van de gebeurtenis via leveringslogboeken.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RoutingCustomJs</span> <br /> </td> 
   <td> JavaScript-bibliotheek die gepersonaliseerd moet worden voor het routeren van gebeurtenissen. Moet de uitvoering van deze twee functies bevatten:<br /> 
    <ul> 
     <li> <p> <span class="uicontrol">dispatchRtEvent(iEventId);</span> : retourneert de interne naam van het transactiemelding die is geselecteerd om de real-time gebeurtenis te verwerken (waarbij <span class="uicontrol">iEventId</span> overeenkomt met de id van de real-time gebeurtenis die is verwerkt).</p> </li> 
     <li> <p> <span class="uicontrol">dispatchBatchEvent(iEventId);</span> : retourneert de interne naam van het transactiemelding dat is geselecteerd om de batchgebeurtenis te verwerken (waarbij <span class="uicontrol">iEventId</span> overeenkomt met de id van de batchgebeurtenis die is verwerkt).</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgDeliveryTimeAlert</span> <br /> </td> 
   <td> Drempel voor waarschuwing van gemiddelde verzendtijd van realtime gebeurtenissen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgDeliveryTimeWarning</span> <br /> </td> 
   <td> De drempel van de waarschuwing voor gemiddelde verzendende tijd van gebeurtenissen in real time.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgProcessTimeAlert</span> <br /> </td> 
   <td> Waarschuwingsdrempel voor de gemiddelde verwerkingstijd van realtime-gebeurtenissen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgProcessTimeWarning</span> <br /> </td> 
   <td> De drempel van de waarschuwing voor de gemiddelde verwerkingstijd van gebeurtenissen in real time.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgQueueAlert</span> <br /> </td> 
   <td> Alert drempel voor het gemiddelde aantal een rij gevormde gebeurtenissen in real time.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgQueueTimeAlert</span> <br /> </td> 
   <td> Alert drempel voor gemiddelde het een rij vormen tijd van gebeurtenissen in real time.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgQueueTimeWarning</span> <br /> </td> 
   <td> De drempel van de waarschuwing voor gemiddelde het een rij vormen tijd van gebeurtenissen in real time.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgQueueWarning</span> <br /> </td> 
   <td> De drempel van de waarschuwing voor het gemiddelde aantal een rij gevormde gebeurtenissen in real time.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventErrorAlert</span> <br /> </td> 
   <td> Waarschuwingsdrempel voor het verwerken van fouten in real-time gebeurtenissen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventErrorWarning</span> <br /> </td> 
   <td> Waarschuwingsdrempel voor het verwerken van fouten in real-time gebeurtenissen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventMaxQueueAlert</span> <br /> </td> 
   <td> Waarschuwingsdrempel voor maximumaantal real-time gebeurtenissen in de wachtrij.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventMaxQueueWarning</span> <br /> </td> 
   <td> De drempel van de waarschuwing voor maximumaantal een rij gevormde gebeurtenissen in real time.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventMinQueueAlert</span> <br /> </td> 
   <td> Waarschuwingsdrempel voor minimumaantal real-time gebeurtenissen in de wachtrij.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventMinQueueWarning</span> <br /> </td> 
   <td> De drempel van de waarschuwing voor minimumaantal een rij gevormde gebeurtenissen in real time.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventQueueAlert</span> <br /> </td> 
   <td> Drempel voor kritieke voorwaarde voor de rij van hangende gebeurtenissen in real time.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventQueueWarning</span> <br /> </td> 
   <td> Drempel voor waarschuwing voor de wachtrij met openstaande real-time gebeurtenissen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventThroughputAlert</span> <br /> </td> 
   <td> Alert drempel voor gebeurtenisproductie in real time.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventThroughputWarning</span> <br /> </td> 
   <td> De drempel van de waarschuwing voor gebeurtenisproductie in real time.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsMessageCenter_RoutingBatchSize</span> <br /> </td> 
   <td> Grootte van het hergroeperen voor de gebeurtenis die verplettert.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_LastRtEventState</span> <br /> </td> 
   <td> Wijzig de aanwijzer van de RtEvent-status (laatste datum tot wanneer de gegevens zijn opgehaald).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsLine_MessageCenterURL</span> <br /> </td> 
   <td> De server-URL van het Centrum van het bericht die wordt gebruikt om welkome berichten (het kanaal van de LIJN) te verzenden.<br /> </td> 
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
   <td> <span class="uicontrol">NmsCleanup_LastCleanup</span> <br /> </td> 
   <td> Bepaalt de laatste tijd het schoonmaakbeurtproces werd in werking gesteld.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_BroadLogPurgeDelay</span> <br /> </td> 
   <td> <p>Hier kunt u de vertraging definiëren waarna de uitzending uit de database wordt verwijderd.</p><p>Deze optie wordt automatisch gecreeerd zodra de vertraging binnen de interface wordt gewijzigd. Als u de waarde in de lijst met opties wijzigt, moet deze worden uitgedrukt in seconden.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_EventHistoPurgeDelay</span> <br /> </td> 
   <td><p> Hier kunt u de vertraging definiëren waarna de gebeurtenisgeschiedenis uit de database wordt gewist.</p><p>
   Deze optie wordt automatisch gecreeerd zodra de vertraging binnen de interface wordt gewijzigd. Als u de waarde in de lijst met opties wijzigt, moet deze worden uitgedrukt in seconden.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_EventPurgeDelay</span> <br /> </td> 
   <td><p> Hiermee kunt u de vertraging definiëren waarna gebeurtenissen uit de database worden verwijderd.</p><p>Deze optie wordt automatisch gecreeerd zodra de vertraging binnen de interface wordt gewijzigd. Als u de waarde in de lijst met opties wijzigt, moet deze worden uitgedrukt in seconden.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_EventStatePurgeDelay</span> <br /> </td> 
   <td><p> Hier kunt u de vertraging definiëren waarna de gebeurtenisstatistieken uit de database worden gewist.</p><p>Deze optie wordt automatisch gecreeerd zodra de vertraging binnen de interface wordt gewijzigd. Als u de waarde in de lijst met opties wijzigt, moet deze worden uitgedrukt in seconden.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_PropositionPurgeDelay</span> <br /> </td> 
   <td><p> Hiermee kunt u de vertraging definiëren waarna voorstellingen uit de database worden verwijderd.</p><p> Deze optie wordt automatisch gecreeerd zodra de vertraging binnen de interface wordt gewijzigd. Als u de waarde in de lijst met opties wijzigt, moet deze worden uitgedrukt in seconden.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_QuarantineMailboxFull</span> <br /> </td> 
   <td> <p>Hier kunt u de vertraging definiëren waarna de quarantines uit de database worden verwijderd.</p><p> Deze optie wordt automatisch gecreeerd zodra de vertraging binnen de interface wordt gewijzigd. Als u de waarde in de lijst met opties wijzigt, moet deze worden uitgedrukt in seconden.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_RecycledDeliveryPurgeDelay</span> <br /> </td> 
   <td> <p>Hiermee kunt u de vertraging definiëren waarna gerecycleerde leveringen uit de database worden verwijderd.</p><p> Deze optie wordt automatisch gecreeerd zodra de vertraging binnen de interface wordt gewijzigd. Als u de waarde in de lijst met opties wijzigt, moet deze worden uitgedrukt in seconden.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_RejectsPurgeDelay</span> <br /> </td> 
   <td> <p>Hier kunt u de vertraging definiëren waarna de afwijzing uit de database wordt verwijderd.</p><p>Deze optie wordt automatisch gecreeerd zodra de vertraging binnen de interface wordt gewijzigd. Als u de waarde in de lijst met opties wijzigt, moet deze worden uitgedrukt in seconden.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_TrackingLogPurgeDelay</span> <br /> </td> 
   <td> <p>Hiermee kunt u de vertraging definiëren waarna trackinglogboeken uit de database worden verwijderd.</p><p>Deze optie wordt automatisch gecreeerd zodra de vertraging binnen de interface wordt gewijzigd. Als u de waarde in de lijst met opties wijzigt, moet deze worden uitgedrukt in seconden.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_TrackingStatePurgeDelay</span> <br /> </td> 
   <td><p> Hier kunt u de vertraging definiëren waarna trackingstatistieken uit de database worden verwijderd.</p><p> Deze optie wordt automatisch gecreeerd zodra de vertraging binnen de interface wordt gewijzigd. Als u de waarde in de lijst met opties wijzigt, moet deze worden uitgedrukt in seconden.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_VisitorPurgeDelay</span> <br /> </td> 
   <td> <p>Hiermee kunt u de vertraging definiëren waarna bezoekers uit de database worden verwijderd.</p><p> Deze optie wordt automatisch gecreeerd zodra de vertraging binnen de interface wordt gewijzigd. Als u de waarde in de lijst met opties wijzigt, moet deze worden uitgedrukt in seconden.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_WorkflowResultPurgeDelay</span> <br /> </td> 
   <td> <p>Hiermee kunt u de vertraging definiëren waarna de workflowresultaten uit de database worden verwijderd.</p><p> Deze optie wordt automatisch gecreeerd zodra de vertraging binnen de interface wordt gewijzigd. Als u de waarde in de lijst met opties wijzigt, moet deze worden uitgedrukt in seconden.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcCapabilities_AzureDw</span> <br /> </td> 
   <td> Azure SQL DataStore-verbindingsopties.<br /> </td> 
  </tr>
   <tr> 
   <td> <span class="uicontrol">WdbcKillSessionPolicy</span> <br /> </td> 
   <td>Laat u onvoorwaardelijk gedrag van het Einde op alle werkschema's en de gegevensbestandvragen van PostgreSQL volgens de volgende potentiële waarden beïnvloeden:<ul>
    <li><p>0 - standaard: stopt werkstroomproces, geen invloed op de database<p></li>
    <li><p>1 - pg_cancel_backend: stopt workflowproces en annuleert query in de database<p></li>
    <li><p>2 - pg_terminate_backend: stopt workflowproces en beëindigt query in de database<p></li></ul></td> 
  </tr>  
  <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceIndex</span> <br /> </td> 
   <td> Naam van de tabelruimte die de indexen van de standaardtabellen van Adobe Campagne moet bevatten.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceUser</span> <br /> </td> 
   <td> Naam van de tabelruimte die de gegevens moet bevatten van de standaardtabellen voor Adobe Campagne.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceWork</span> <br /> </td> 
   <td> Naam van de tabelruimte die de gegevens van de Adobe Campagne-werktabellen moet bevatten.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceWorkIndex</span> <br /> </td> 
   <td> Naam van de tabelruimte die de indexen van de Adobe Campagne-werktabellen moet bevatten.<br /> </td> 
  </tr> 
    <tr> 
   <td> <span class="uicontrol">WdbcOptions_TempDbName</span> <br /> </td> 
   <td> Staat u toe om een afzonderlijk gegevensbestand voor het werken van lijsten op de Server van Microsoft te vormen SQL, om steunen en replicatie te optimaliseren. De optie komt overeen met de naam van de tijdelijke database: Indien opgegeven, worden werktabellen in deze database geschreven. Voorbeeld: 'tempdb.dbo.' (de naam moet eindigen met een punt).</desc> <a href="../../production/using/rdbms-specific-recommendations.md#microsoft-sql-server">Meer informatie</a> <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcTimeZone</span> <br /> </td> 
   <td> Tijdzone van de instantie van Adobe Campaign. Zie <a href="../../installation/using/time-zone-management.md#configuration" target="_blank">Configuratie</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcUseNChar</span> <br /> </td> 
   <td> Zijn de de koordgebieden van het gegevensbestand bepaald met NChar?<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcUseTimeStampWithTZ</span> <br /> </td> 
   <td> Sla tijdzonegegevens op in de 'datetime'-velden van de database?<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkDatabaseId</span> <br /> </td> 
   <td> ID van de database. Begint met 'u' voor Unicode DataBase.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkInstancePrefix</span> <br /> </td> 
   <td> Prefix die aan automatisch gegenereerde interne namen wordt toegevoegd.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkQuery_Schema_LineCount</span> <br /> </td> 
   <td> Maximum aantal resultaten die door een vraag op xtk:schema en xtk:srcSchema zijn teruggekeerd.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkSequence_AutoGeneration</span> <br /> </td> 
   <td> Alle aangepaste schema's, die na deze tijd worden gemaakt, met automatische piloot="true" en zonder het kenmerk "pkSequence" krijgen een automatisch gegenereerde reeks "auto_ &lt;schemanamespace&gt; &lt;schemaname&gt; _seq. 
   </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NlMigration_KeepFolderStructure</span> <br /> </td> 
   <td> Tijdens migratie wordt de boomstructuur automatisch opnieuw ingedeeld op basis van de nieuwe versienormen.<br /> Met deze optie kunt u de automatische migratie van de boomstructuur uitschakelen. Als u het gebruikt, moet u na migratie verouderde mappen verwijderen, de nieuwe mappen toevoegen en alle noodzakelijke controles uitvoeren.<br /> 
    <ul> 
     <li> <p> <span class="uicontrol">Gegevenstype:</span> Geheel</p> </li> 
     <li> <p> <span class="uicontrol">Waarde (tekst)</span> : 1 </p> </li> 
    </ul> Deze optie mag alleen worden gebruikt als de uit-de-box navigatieboom te veel wijzigingen heeft ondergaan.<br /> Zie <a href="../../migration/using/specific-configurations-in-v5-11.md#campaign-vseven-tree-structure">deze sectie</a>voor meer informatie.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsLastErrorStatCoalesce</span> <br /> </td> 
   <td> Laatste verwerkingsdatum van het opruimen van de <span class="uicontrol">tabel NmsEmailErrorStat</span> .<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">PostUpgradeLastError</span> <br /> </td> 
   <td> Informatie over de fout die is opgetreden in de Postupgrade, volgens de onderstaande syntaxis:<br /> <strong>{Build number}:{mode: pre/post/...}:{The 'lessThan'/'greaterOrEquelThan' where error occurred + substep}</strong> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkCleanup_NoStats</span> <br /> </td> 
   <td> Voer de waarde "1" in, zodat de update van statistieken niet wordt uitgevoerd via de opschoonworkflow.<br /> </td> 
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
   <td> <span class="uicontrol">AEMResourceTypeFilter</span> <br /> </td> 
   <td> Typen AEM-bronnen die kunnen worden gebruikt in Adobe Campaign. Waarden moeten worden gescheiden door komma's.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">nmsPipeline_config</span> <br /> </td> 
   <td> Hiermee kunt u Experience Cloud-triggers configureren. Het gegevenstype is 'lange tekst' en moet de JSON-indeling hebben. Zie <a class="anchorLink" href="https://helpx.adobe.com/campaign/kb/triggers-and-campaign.html#PipelineoptionNmsPipelineConfig" target="_blank">Experience Cloud Triggers gebruiken met Adobe Campaign Classic</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">LASTIMPORT_&lt;%=instance.internalName%&gt;_&lt;%=activityName%&gt;</span> <br /> </td> 
   <td> Deze optie wordt gebruikt wanneer het invoeren van gegevens van een derdesysteem door een schakelaar van CRM. Als u de optie inschakelt, kunt u alleen objecten verzamelen die zijn gewijzigd sinds de laatste importbewerking. Deze optie moet handmatig worden gemaakt en als volgt worden ingevuld: 
    <ul> 
     <li> <p> <span class="uicontrol">Interne naam</span> : LASTIMPORT_&lt;%=instance.internalName%&gt;_&lt;%=activityName%&gt;</p> </li> 
     <li> <p> <span class="uicontrol">Waarde (veld)</span> : datum van de laatste invoer, met de notatie jjjj/MM/dd uu:mm:ss. </p> </li> 
    </ul><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">TNT_EdgeServer</span> <br /> </td> 
   <td> Adobe Target-server gebruikt voor de integratie. Deze optie is standaard al geselecteerd. Deze waarde komt overeen met de Adobe Target Domain Server, gevolgd door de waarde /m2. Bijvoorbeeld: tt.omtrdc.net/m2.<br /> Zie <a href="../../integrations/using/configuring-the-integration-with-adobe-target.md">deze sectie</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">TNT_TenantName</span> <br /> </td> 
   <td> Naam van Adobe Target-organisatie. Deze waarde komt overeen met de naam van de Adobe Target-client.<br /> Zie <a href="../../integrations/using/configuring-the-integration-with-adobe-target.md">deze sectie</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">AAM_DataSourceId</span> <br /> </td> 
   <td> Optie gebruikt voor de integratie met Adobe Audience Manager.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">AAM_DestinationId</span> <br /> </td> 
   <td> Optie gebruikt voor de integratie met Adobe Audience Manager.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcCapabilities_Teradata</span> <br /> </td> 
   <td> Verbindingsopties voor teragegevens.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcCapabilities_Hive</span> <br /> </td> 
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
   <td> <span class="uicontrol">NmsCoupons_MaxPerTransac</span> <br /> </td> 
   <td> Aantal coupons dat per SQL-transactie wordt bijgewerkt.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInteraction_LastPropositionSynchControl_</span> <br /> </td> 
   <td> '+ [schema van voorstel] + "_" + extAccountSource.@executeInstanceId + [proposition's schema] + "_" + vars.executeInstanceIdFilter<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInteraction_LastPropositionSynchExec_</span> <br /> </td> 
   <td> '+ [ schema van de projectie] + "_" + extAccountSource.@executeInstanceId + "_" + extAccountTarget.@executeInstanceId<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInteraction_SynchWorkflowIds</span> <br /> </td> 
   <td> Synchronisatieworkflow bijhouden.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInteraction_UseDaemon</span> <br /> </td> 
   <td> Schakel asynchrone projectietekening in/uit ("0" om uit te schakelen, "1" om in te schakelen).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsModule_CouponsEnabled</span> <br /> </td> 
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
   <td> <span class="uicontrol">NmsExecutionInstanceId</span> <br /> </td> 
   <td> Id van uitvoeringsinstantie.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_CustomerId</span> <br /> </td> 
   <td> Customer identifier die wordt gebruikt bij het verzenden van het factureringsrapport.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_IntranetURL</span> <br /> </td> 
   <td> Interne basis-URL voor toegang tot de toepassingsserver.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_LastPostUpgrade</span> <br /> </td> 
   <td> Buildnummer van de AC-instantie vóór de laatste upgrade.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_URL</span> <br /> </td> 
   <td> Basis-URL van de openbare webtoepassingsserver.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkPassUnknownSQLFunctionsToRDBMS</span> <br /> </td> 
   <td> Hiermee kunt u oude niet-gedeclareerde SQL-functies blijven gebruiken na het migreren. We raden u ten zeerste aan deze optie niet te gebruiken vanwege de beveiligingsrisico's die erin worden geïntroduceerd.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Tekstspatiëring {#tracking}

<table> 
 <thead> 
  <tr> 
   <th> Naam van optie </th> 
   <th> Beschrijving </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_Available</span> <br /> </td> 
   <td> Optie waarmee u reeksspatiëring kunt activeren.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_ClickFormula</span> <br /> </td> 
   <td> Rekenscript met tracked-URL.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_ExtAccount</span> <br /> </td> 
   <td> Hiermee kunt u de externe account van de trackingserver definiëren.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_Instance</span> <br /> </td> 
   <td> Hiermee kunt u de instantienaam op de trackingserver definiëren.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_LastConsolidation</span> <br /> </td> 
   <td> De laatste keer dat de trackinggegevens zijn geconsolideerd met nieuwe gegevens.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_OpenFormula</span> <br /> </td> 
   <td> URL-berekeningsscript openen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_Password</span> <br /> </td> 
   <td> Wachtwoord voor de traceringsserver<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_Aanwijzer</span> <br /> </td> 
   <td> De aanwijzer houdt de laatste berichtgebeurtenissen bij die zijn verwerkt via de id's en datum.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_SecureServerUrl</span> <br /> </td> 
   <td> Beveilig URL van de frontale volgende server.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_ServerUrl</span> <br /> </td> 
   <td> URL van de frontale volgende server.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_ServerUrlList</span> <br /> </td> 
   <td> Lijst van URLs die wordt gebruikt om de volgende servers te contacteren.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_UserAgentRules</span> <br /> </td> 
   <td> Regelset voor browseridentificatie.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_WebFormula</span> <br /> </td> 
   <td> Script dat wordt gebruikt voor het berekenen van webtrackingtags.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_WebTrackingDelivery</span> <br /> </td> 
   <td> Naam van de virtuele levering die is ontworpen voor webtraceringsbeheer.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_WebTrackingMode</span> <br /> </td> 
   <td> Hiermee kunt u de webtraceringsmodus definiëren.<br /> </td> 
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
   <td> <span class="uicontrol">Privacy_Request_ConfirmDeletePending</span> <br /> </td> 
   <td> Als optie 1 wordt geselecteerd, moet u manueel de schrapping in de interface in een tweede stap bevestigen. Anders worden gegevens zonder bevestiging verwijderd.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Privacy_Request_ConfirmDeletePendingDelay</span> <br /> </td> 
   <td> De vertraging tussen verzoek wacht op het verwijderen van bevestiging en verzoek is geannuleerd.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Privacy_Request_MaxErrorAllowed</span> <br /> </td> 
   <td> Het maximale aantal toegestane fouten bij het verwerken/verwijderen van een privacyaanvraag.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Privacy_Request_PurgeDelay</span> <br /> </td> 
   <td> De vertraging tussen verzoek wordt gecreeerd op de rij en de verzoekgegevens worden geschrapt.<br /> </td> 
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
   <td> <span class="uicontrol">XtkLdap_Active</span> <br /> </td> 
   <td> Schakel LDAP-server in om gebruikers te verifiëren en gebruikers autorisaties te geven.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLoad_AppLogin</span> <br /> </td> 
   <td> Meld u aan bij de toepassing om contact op te nemen met de server voor verschillende zoekopdrachten.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLoad_AppPassword</span> <br /> </td> 
   <td> Gecodeerd wachtwoord voor de aanmelding van de toepassing.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLoad_AutoOperator</span> <br /> </td> 
   <td> Automatisch operatoren en rechten maken in Adobe Campaign.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_DN</span> <br /> </td> 
   <td> Computatieformule voor LDAP DN op basis van aanmelding.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_DNSsearch</span> <br /> </td> 
   <td> DN-zoekopdracht inschakelen in map.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLoad_DNSsearchBase</span> <br /> </td> 
   <td> Zoekbasis.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLoad_DNSsearchFilter</span> <br /> </td> 
   <td> DN-zoekfilter.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLoad_DNSsearchScope</span> <br /> </td> 
   <td> Zoekbereik.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLoad_Mechanism</span> <br /> </td> 
   <td> Type verificatie gebruikt om contact op te nemen met de LDAP-server (normaal, md5, lds, ntlm, dpa).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLoad_Rights</span> <br /> </td> 
   <td> Synchronisatie van autorisaties en groepen vanuit de LDAP-directory naar benoemde rechten in Adobe Campaign inschakelen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLoad_RightsAttr</span> <br /> </td> 
   <td> LDAP-kenmerk met de machtigingsnaam.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLoad_RightsBase</span> <br /> </td> 
   <td> Zoekbasis.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLoad_RightsFilter</span> <br /> </td> 
   <td> Filter Zoeken naar gebruikersautorisaties.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLoad_RightsMask</span> <br /> </td> 
   <td> Uitdrukking om de namen van de rechten van de Campagne van Adobe uit de vergunningen te halen LDAP.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLoad_RightsScope</span> <br /> </td> 
   <td> Zoekbereik.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLDAP_Server</span> <br /> </td> 
   <td> LDAP-serveradres (het is mogelijk een poort op te geven door ':' op te geven als scheidingsteken).<br /> </td> 
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
   <td> <span class="uicontrol">XtkUseScrollBar</span> <br /> </td> 
   <td> Met de waarde 1 kan de schuifbalk worden toegevoegd aan detailformulieren.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkWebForm_Instance</span> <br /> </td> 
   <td> Instantie die moet worden gebruikt voor validatie van webformulieren in de modus 'Andere server(s)'.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkWebForm_Password</span> <br /> </td> 
   <td> Wachtwoord van de instantie dat moet worden gebruikt voor webformuliervalidatie in de modus 'Andere server(s)'.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkWebForm_ServersMode</span> <br /> </td> 
   <td> Optie waarmee u de validatiemodus van webformulieren kunt opgeven: standaard lokaal, gebruikt trackingservers als de optie 'tracking' is en een lijst met gepersonaliseerde items gebruikt met de optie 'Andere server(s)'.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkWebForm_ServersURLs</span> <br /> </td> 
   <td> Persoonlijke adreslijst met servers waarmee contact moet worden opgenomen voor validatie van webformulieren (modus "Andere server(s)").<br /> </td> 
  </tr> 
 </tbody> 
</table>

