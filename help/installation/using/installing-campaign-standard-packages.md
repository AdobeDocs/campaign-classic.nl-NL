---
product: campaign
title: Ingebouwde Campaign Classic-pakketten installeren
description: Leer hoe u geïntegreerde pakketten voor campagnes kunt installeren
feature: Installation, Application Settings
badge-v7-prem: label="Alleen op locatie/hybride" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=nl" tooltip="Alleen van toepassing op on-premise en hybride implementaties"
exl-id: 2bc077c4-ed65-4157-bfc9-df5d0442f476
source-git-commit: b11185da8236d6100d98eabcc9dc1cf2cffa70af
workflow-type: tm+mt
source-wordcount: '1264'
ht-degree: 1%

---

# Ingebouwde Campaign Classic-pakketten installeren{#installing-campaign-standard-packages}



## Ingebouwde pakketten {#campaign-standard-packages}

De ingebouwde pakketten bevatten een reeks eigenschappen die volgens uw behoeften en afhankelijk van uw contract kunnen worden geïnstalleerd. De volledige lijst van ingebouwde pakketten van de Campagne is beschikbaar hieronder.

>[!CAUTION]
>
>U mag alleen pakketten installeren die overeenkomen met de opties die in uw licentieovereenkomst zijn vermeld.
>
>De installatie van een nieuw pakket kan invloed hebben op al uw platform: het moet worden getest en gevalideerd voor de definitieve implementatie.
>
>Nadat een pakket is geïnstalleerd, kunt u het niet verwijderen.
>
>Neem als gehoste of hybride klant contact op met de Adobe om een nieuw ingebouwd pakket te implementeren.

Een ingebouwd pakket installeren:

1. De wizard Pakket importeren openen vanuit **[!UICONTROL Tools > Advanced > Import package]** in de Adobe Campaign-clientconsole.
1. Selecteer **[!UICONTROL Install a standard package]**.
1. Controleer in de pakketlijst de pakketten die u wilt installeren.
   >[!NOTE]
   >
   >Wanneer een pakket grijs wordt weergegeven, betekent dit dat het al is geïnstalleerd of niet compatibel is met uw instantie. De compatibiliteit wordt in de onderstaande tabel beschreven.
1. Klikken **[!UICONTROL Next]** vervolgens **[!UICONTROL Start]** om de pakketinstallatie te starten.

   Nadat de pakketten zijn geïnstalleerd, wordt op de voortgangsbalk weergegeven **100%** en u kunt het volgende bericht in de installatielogboeken zien: **[!UICONTROL Installation of packages successful]**.

1. **[!UICONTROL Close]** het installatievenster.

De pakketten zijn nu geïnstalleerd.

### Lijst van uit-van-de-doos Pakketten {#list-of-standard-packages}

In de volgende tabel worden alle ingebouwde pakketten voor campagnes weergegeven.

<table> 
 <thead> 
  <tr> 
   <th> Pakket </th> 
   <th> Beschrijving </th> 
   <th> Instantietype </th>
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Aflevering<br /> </td> 
   <td> Controleert leveringen en uiteindelijke problemen die worden aangetroffen wanneer berichten worden verzonden. <a href="../../delivery/using/about-delivery-monitoring.md">Meer informatie</a><br /> </td> 
   <td> Alles</td> 
  </tr> 
  <tr> 
   <td> Marketingcampagnes (Campagne)<br /> </td> 
   <td> Definieert, optimaliseert, voert en analyseert mededelingen en marketing campagnes uit. <a href="../../campaign/using/designing-marketing-campaigns.md">Meer informatie</a><br /> </td> 
   <td> Marketing</td>
  </tr> 
  <tr> 
   <td> Marketing resources (MRM)<br /> </td> 
   <td> Controls marketing actions op een samenwerkingswijze door beheer en het volgen van de taken, de begrotingen en de marketing middelen te verstrekken. <a href="../../mrm/using/about-marketing-resource-management.md">Meer informatie</a> <br /> </td> 
   <td> Marketing</td> 
  </tr> 
  <tr> 
   <td> Aanbiedingsengine (interactie)<br /> </td> 
   <td> Reageert in real time tijdens een interactie met een bepaald contact (een klant of een doel) door hen één of verscheidene aangepaste aanbiedingen te maken.  Optioneel. <a href="../../interaction/using/interaction-and-offer-management.md#packages-configuration">Meer informatie</a> <br /> </td> 
   <td> Alles<br /> </td> 
  </tr> 
  <tr> 
   <td> Besturing van de aanbiedingsengine met uitvoeringsinstantie. Optioneel.<br /> </td> 
   <td> Pakket om op controleinstantie voor de motor van de Aanbieding (interactie) te installeren. <a href="../../interaction/using/distributed-architectures.md#packages-configuration">Meer informatie</a> </td> 
   <td> Marketing<br /> </td>  
  </tr> 
  <tr> 
   <td> De engine voor uitvoeringsinstanties aanbieden. Optioneel.<br /> </td> 
   <td> Pakket maken om te installeren op uitvoeringsinstanties voor de Offertenengine (interactie). <a href="../../interaction/using/distributed-architectures.md">Meer informatie</a> </td> 
   <td> Midden, uitvoering <br /> </td>  
  </tr> 
  <!--tr> 
   <td> Lead Management (Leads) (deprecated)<br /> </td> 
   <td> Simplifies the process of building and maintaining the entire leads management life cycle. <br /> </td> 
   <td> Yes<br /> </td> 
   <td> Optional, <a href="https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html">Learn More</a> </td> 
  </tr--> 
  <tr> 
   <td> Sociale netwerken (sociale marketing) <br /> </td> 
   <td> Hiermee synchroniseert u Adobe Campaign met X (voorheen bekend als Twitter) en Facebook. <a href="../../social/using/about-social-marketing.md">Meer informatie</a> <br /> </td> 
   <td> Alles</td> 
  </tr> 
  <tr> 
   <td> Transactionaal berichtenbeheer (Berichtcentrum - Controle)<br /> </td> 
   <td> Beheert triggerberichten die worden gegenereerd door gebeurtenissen die worden geactiveerd door informatiesystemen. Optioneel. <a href="../../message-center/using/about-transactional-messaging.md">Meer informatie</a> <br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Transactiebericht uitvoeren (Berichtcentrum - Uitvoering) <br /> </td> 
   <td> Zorgt voor een hogere beschikbaarheid en een beter beheer van de belasting. Optioneel. <a href="../../message-center/using/about-transactional-messaging.md">Meer informatie</a><br /> </td> 
   <td> Uitvoering<br /> </td>
  </tr> 
  <tr> 
   <td> LINE-kanaal<br /> </td> 
   <td> Verstuurt leveringen met behulp van het LINE-kanaal met Adobe Campaign. Optioneel. Transactioneel overseinen (het pakket van het Centrum van het Bericht) verplicht. <a href="../../delivery/using/line-channel.md">Meer informatie</a> <br /> </td> 
   <td> Alles<br /> </td> 
  </tr> 
  <tr> 
   <td> Direct Mail Channel<br /> </td> 
   <td> Verstuurt leveringen via het directe-mailkanaal met Adobe Campaign. Optioneel. <a href="../../delivery/using/about-direct-mail-channel.md">Meer informatie</a><br /> </td> 
   <td> Alles<br /> </td>
  </tr> 
  <tr> 
   <td> Mobiel kanaal (SMS) <br /> </td> 
   <td> Verstuurt leveringen via het mobiele/sms-kanaal met Adobe Campaign. Optioneel. <a href="../../delivery/using/sms-channel.md">Meer informatie</a> <br /> </td> 
   <td> Alles<br /> </td> 
  </tr> 
   <tr> 
   <td> Telefoonkanaal<br /> </td> 
   <td> Verzendt leveringen via het telefoonkanaal met Adobe Campaign. Gebruikt voor callcenter. Optioneel. <a href="../../delivery/using/communication-channels.md">Meer informatie</a> <br /> </td> 
   <td> Alles<br /> </td> 
  </tr> 
  <tr> 
   <td> Mobiel App-kanaal<br /> </td> 
   <td> Gebruikt het Adobe Campaign-platform om gepersonaliseerde meldingen naar iOS- en Android-terminals te verzenden via apps. Optioneel. <a href="../../delivery/using/about-mobile-app-channel.md">Meer informatie</a> <br /> </td> 
   <td> Alles<br /> </td> 
  </tr> 
  <tr> 
   <td> Inhoudsbeheer<br /> </td> 
   <td> Hiermee maakt u periodieke nieuwsbrieven of websites en valideert en publiceert u uw berichten. <a href="../../delivery/using/about-content-management.md">Meer informatie</a> <br /> </td> 
   <td> </td>
  </tr> 
  <tr> 
   <td> Online enquêtes (Enquêtemanager)<br /> </td> 
   <td> Hiermee maakt en beheert u onlineformulieren voor het toevoegen of wijzigen van profielgegevens, voor het abonneren, voor het opzeggen van abonnementen of voor het invoeren van wedstrijden. Optioneel. <a href="../../surveys/using/about-surveys.md">Meer informatie</a> <br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Marketing Analytics<br /> </td> 
   <td> Hiermee kunt u gegevens analyseren en meten, statistieken berekenen, het maken en berekenen van rapporten vereenvoudigen en optimaliseren. U kunt ook rapporten maken en doelpopulaties maken. Optioneel. <a href="../../reporting/using/ac-cubes.md">Meer informatie</a><br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Responsbeheer<br /> </td> 
   <td> Hiermee wordt het succes en de winstgevendheid van marketingcampagnes gemeten of worden voorstellen voor alle communicatiekanalen aangeboden.  Optioneel. <a href="../../response/using/about-response-manager.md">Meer informatie</a> <br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Toegang tot externe gegevens (Federated Data Access)<br /> </td> 
   <td> Verstrekt de Federated optie van de Toegang van Gegevens (FDA) om informatie te verwerken die in één of meerdere externe gegevensbestanden wordt opgeslagen zodat u tot externe gegevens kunt toegang hebben zonder de structuur van de gegevens van Adobe Campaign te veranderen.  Optioneel. <a href="../../workflow/using/accessing-an-external-database-fda.md">Meer informatie</a> <br /> </td> 
   <td> Alles<br /> </td> 
  </tr> 
  <tr> 
   <td> Campagne optimaliseren<br /> </td> 
   <td> Controles, filters en controleren het verzenden van leveringen zodat de verzonden berichten het best aan de behoeften en de verwachtingen van klanten voldoen, in overeenstemming met het beleid van het bedrijfs communicatie. Optioneel. <a href="../../campaign-opt/using/about-campaign-typologies.md">Meer informatie</a> <br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Leverbaarheidscontrole (e-maillevering)<br /> </td> 
   <td> Meet het succes van uw campagnes die uw ontvangers' inbox zonder stuitend bereiken, of als spam worden gemerkt. Optioneel. <a href="../../delivery/using/about-deliverability.md">Meer informatie</a> <br /> </td> 
   <td> Alles </td> 
  </tr> 
  <tr> 
   <td> Couponbeheer<br /> </td> 
   <td> Hiermee maakt u een set coupons die u kunt toevoegen aan de volgende marketingaanbiedingen. Optioneel. <a href="../../delivery/using/personalized-coupons.md">Meer informatie</a> <br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Inbox Rendering (IR)<br /> </td> 
   <td> Hiermee kunt u een voorvertoning weergeven van het bericht dat is verzonden in de verschillende contexten waarin het kan worden ontvangen en de compatibiliteit van grote desktops en toepassingen controleren. Optioneel. <a href="../../delivery/using/inbox-rendering.md">Meer informatie</a><br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Centrale/lokale Marketing (Distributed Marketing)<br /> </td> 
   <td> Voert samenwerkingscampagnes uit tussen centrale entiteiten (hoofdkantoor, marketingafdelingen, enz.) en lokale entiteiten (verkooppunten, regionale agentschappen, enz.). Optioneel. <a href="../../distributed/using/about-distributed-marketing.md">Meer informatie</a><br /> </td> 
   <td> Marketing </td> 
  </tr> 
  <tr> 
   <td> CRM-connectoren<br /> </td> 
   <td> Verschillende CRM-connectors waarmee u uw Adobe Campaign-platform kunt koppelen aan systemen van derden.  <a href="../../platform/using/crm-connectors.md">Meer informatie</a> <br /> </td> 
   <td> Marketing</td> 
  </tr> 
  <tr> 
   <td> Webanalytische connectors<br /> </td> 
   <td> Hiermee staat u Adobe Campaign en Adobe Analytics toe om te communiceren via het connectorpakket Web Analytics. Niet compatibel met Transactioneel overseinen (het pakket van het Centrum van het Bericht). <a href="../../integrations/using/gs-aa.md">Meer informatie</a><br /> </td> 
   <td> Marketing </td> 
  </tr> 
  <tr> 
   <td> AEM integratie<br /> </td> 
   <td> Hiermee kunt u de inhoud van uw e-mailleveringen en uw formulieren rechtstreeks in Adobe Experience Manager beheren, zodat u kunt profiteren van AEM functies voor het bewerken van inhoud en de leveringsmogelijkheden van Adobe Campaign. <a href="../../integrations/using/about-adobe-experience-manager.md">Meer informatie</a> <br /> </td> 
   <td> Marketing</td> 
  </tr> 
  <tr> 
   <td> Integratie van Adobe Experience Cloud-publiek<br /> </td> 
   <td> Hiermee kunt u soorten publiek/segmenten uitwisselen en delen met Adobe Experience Cloud-oplossingen en -toepassingen. Vereist IMS. <a href="../../integrations/using/sharing-audiences-with-adobe-experience-cloud.md">Meer informatie</a> <br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Integratie met Adobe Experience Cloud<br /> </td> 
   <td> Hiermee kunt u soorten publiek/segmenten van verschillende Adobe Experience Cloud-oplossingen importeren en exporteren naar Adobe Campaign. Optioneel. <a href="../../integrations/using/configuring-ims.md#installing-the-package">Meer informatie</a> </td> 
   <td> Marketing</td> 
  </tr> 
  <tr> 
   <td> Privacygegevensbeschermingsverordening<br /> </td> 
   <td> Bevat extra functionaliteit om u te helpen met uw naleving van de Privacy in Campaign Classic. <a href="https://helpx.adobe.com/nl/campaign/kb/acc-privacy.html">Meer informatie</a> <br /> </td> 
   <td> Alles</td> 
  </tr> 
  <tr> 
   <td> Overschakelen naar middelmatig bronnen <br /> </td> 
   <td> Geeft details over de installatie en configuratie van een server voor midsourcing, alsook over de implementatie van een instantie die derden in staat stelt berichten te verzenden in de modus voor midsourcing. Optioneel. <a href="../../installation/using/mid-sourcing-server.md">Meer informatie</a> <br /> </td> 
   <td> Marketing </td> 
  </tr> 
  <tr> 
   <td> Middelsourcingsplatform<br /> </td> 
   <td> Deze configuratie is een optimale middenoplossing tussen een ontvangen (ASP) configuratie en internalisering. De naar buiten gerichte uitvoeringscomponenten worden uitgevoerd op een "mid-sourcing"-server die wordt gehost op Adobe Campaign. Optioneel. <a href="../../installation/using/mid-sourcing-server.md">Meer informatie</a> <br /> </td> 
   <td> Midden-sourcing </td> 
  </tr> 
  <tr> 
   <td> AMP-ondersteuning<br /> </td> 
   <td> Hiermee kunt u het nieuwe interactieve AMP gebruiken voor e-mailindeling en dynamische e-mailberichten verzenden. Optioneel. <a href="../../delivery/using/defining-interactive-content.md">Meer informatie</a> <br /> </td> 
   <td> Alles </td> 
  </tr> 
  <tr> 
   <td> ACS Connector (afgekeurd)<br /> </td> 
   <td> Bridges Adobe Campaign v7 en Adobe Campaign Standard. Het is een geïntegreerde eigenschap in Campagne v7 die automatisch gegevens aan Campaign Standard herhaalt, die het beste van beide toepassingen verenigt. Optioneel.<br /> </td> 
   <td> Marketing </td> 
  </tr> 
 </tbody> 
</table>

### Message Center-pakket {#message-center-package}

U moet leveringskanalen installeren (E-mail, Mobiel kanaal, Mobiel App-kanaal, LINE, enz.) voordat u het Transactiebericht installeert (Message Center-pakket). Als u een project van het Centrum van het Bericht van het e-mail-enige bent begonnen, en een nieuw kanaal daarna moet toevoegen, moet u deze stappen volgen:

1. Installeer het nieuwe kanaal, bijvoorbeeld **Mobiel kanaal**, met de wizard Pakket importeren ( **[!UICONTROL Tools > Advanced > Import package > Adobe Campaign package]**).
1. Het bestand importeren ( **[!UICONTROL Tools > Advanced > Import package > File]**) en selecteer:

   ```
   \datakit\nms\[Your language]\package\messageCenter.xml
   ```

1. In de **[!UICONTROL XML data content to import]**, slechts het leveringsmalplaatje houden van het Centrum van het Bericht dat aan het verwante kanaal beantwoordt. Als u bijvoorbeeld de opdracht **Mobiel kanaal**, alleen de **entiteiten** element dat overeenkomt met het **[!UICONTROL Mobile transactional message]** (smsTriggerMessage) sjabloon. Als u de **Mobiel App-kanaal**, alleen de **Transactiebericht van iOS** sjablonen (iosTriggerMessage) en **Transactiebericht van Android** (androidTriggerMessage).

   ![](assets/messagecenter_install_channel.png)


### [!DNL LINE] kanaalinstelling{#line-package}

Als u de opdracht [!DNL LINE] kanaal, moet u eerst installeren [!DNL LINE] pakket.

In de context van een midsourcingconfiguratie, moet u:

* Installeer de [!DNL LINE] pakket op zowel de Marketing als de instantie MID

* Stel de [!DNL LINE] externe rekening op de markt om naar het midden van de instantie te wijzen door de leveringsmodus te wijzigen. [Meer informatie](../../delivery/using/line-channel.md#configure-line-external)

* Stel de [!DNL LINE] referenties in de externe account op de instantie MID.

>[!CAUTION]
>
>De leveringsmalplaatjes van het Centrum van het Bericht voor [!DNL LINE] kanaal is niet beschikbaar als de pakketten van het Berichtencentrum zijn geïnstalleerd vóór [!DNL LINE].