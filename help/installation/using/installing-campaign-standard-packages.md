---
solution: Campaign Classic
product: campaign
title: Ingebouwde Campaign Classic-pakketten installeren
description: Leer hoe u geïntegreerde pakketten voor campagnes kunt installeren
audience: installation
content-type: reference
topic-tags: initial-configuration
translation-type: tm+mt
source-git-commit: 6d5dbc16ed6c6e5a2e62ceb522e2ccd64b142825
workflow-type: tm+mt
source-wordcount: '1154'
ht-degree: 5%

---


# Ingebouwde Campaign Classic-pakketten installeren{#installing-campaign-standard-packages}

## Ingebouwde pakketten {#campaign-standard-packages}

De ingebouwde pakketten bevatten een reeks eigenschappen die volgens uw behoeften en afhankelijk van uw contract kunnen worden geïnstalleerd. De volledige lijst van ingebouwde pakketten van de Campagne is beschikbaar hieronder.

>[!CAUTION]
>
>U mag alleen pakketten installeren die overeenkomen met de opties die in uw licentieovereenkomst zijn vermeld.
>
>Het installeren van een nieuw pakket kan al uw platform beïnvloeden: het moet worden getest en gevalideerd vóór de definitieve implementatie.
>
>Nadat een pakket is geïnstalleerd, kunt u het niet verwijderen.

Een ingebouwd pakket installeren:

1. Open de wizard voor het importeren van pakketten vanuit **[!UICONTROL Tools > Advanced > Package import...]** in de Adobe Campaign-clientconsole.
1. Selecteer **[!UICONTROL Install a standard package]**.
1. Controleer in de pakketlijst de pakketten die u wilt installeren.
   >[!NOTE]
   >
   >Wanneer een pakket grijs wordt weergegeven, betekent dit dat het al is geïnstalleerd of niet compatibel is met uw instantie. De compatibiliteit wordt in de onderstaande tabel beschreven.
1. Klik **[!UICONTROL Next]**, dan **[!UICONTROL Start]** om de pakketinstallatie te beginnen.

   Zodra de pakketten worden geïnstalleerd, toont de vooruitgangsbar **100%** en u kunt het volgende bericht in de installatielogboeken zien: **[!UICONTROL Installation of packages successful]**.

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
   <td> Levering<br /> </td> 
   <td> Controleert leveringen en uiteindelijke problemen die worden aangetroffen wanneer berichten worden verzonden. <a href="../../delivery/using/about-delivery-monitoring.md">Meer informatie</a><br /> </td> 
   <td> Alles</td> 
  </tr> 
  <tr> 
   <td> Marketingcampagnes (Campagne)<br /> </td> 
   <td> Definieert, optimaliseert, voert en analyseert mededelingen en marketing campagnes uit. <a href="../../campaign/using/designing-marketing-campaigns.md">Meer informatie</a><br /> </td> 
   <td> Marketing</td>
  </tr> 
  <tr> 
   <td> Marketingbronnen (MRM)<br /> </td> 
   <td> Controls marketing actions op een samenwerkingswijze door beheer en het volgen van de taken, de begrotingen en de marketing middelen te verstrekken. <a href="../../campaign/using/about-marketing-resource-management.md">Meer informatie</a> <br /> </td> 
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
   <td> Synchroniseert Adobe Campaign met Twitter en Facebook. <a href="../../social/using/about-social-marketing.md">Meer informatie</a> <br /> </td> 
   <td> Alles</td> 
  </tr> 
  <tr> 
   <td> Transactieberichtencontrole (Berichtcentrum - Besturing)<br /> </td> 
   <td> Beheert triggerberichten die worden gegenereerd door gebeurtenissen die worden geactiveerd door informatiesystemen. Optioneel. <a href="../../message-center/using/about-transactional-messaging.md">Meer informatie</a> <br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Transactiebericht-uitvoering (Berichtcentrum - Uitvoering) <br /> </td> 
   <td> Zorgt voor hogere beschikbaarheid en beter beheer van de belasting. Optioneel. <a href="../../message-center/using/about-transactional-messaging.md">Meer informatie</a><br /> </td> 
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
   <td> Kanaal voor mobiele apps<br /> </td> 
   <td> Gebruikt het Adobe Campaign-platform om gepersonaliseerde meldingen naar iOS- en Android-terminals te verzenden via apps. Optioneel. <a href="../../delivery/using/about-mobile-app-channel.md">Meer informatie</a> <br /> </td> 
   <td> Alles<br /> </td> 
  </tr> 
  <tr> 
   <td> Inhoudsbeheer<br /> </td> 
   <td> Hiermee maakt u periodieke nieuwsbrieven of websites en valideert en publiceert u uw berichten. <a href="../../delivery/using/about-content-management.md">Meer informatie</a> <br /> </td> 
   <td> </td>
  </tr> 
  <tr> 
   <td> Online enquêtes (Beoordelingsmanager)<br /> </td> 
   <td> Hiermee maakt en beheert u onlineformulieren voor het toevoegen of wijzigen van profielgegevens, voor het abonneren, voor het opzeggen van abonnementen of voor het invoeren van wedstrijden. Optioneel. <a href="../../web/using/about-surveys.md">Meer informatie</a> <br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Marketing Analytics<br /> </td> 
   <td> Hiermee kunt u gegevens analyseren en meten, statistieken berekenen, het maken en berekenen van rapporten vereenvoudigen en optimaliseren. U kunt ook rapporten maken en doelpopulaties maken. Optioneel. <a href="../../reporting/using/about-cubes.md">Meer informatie</a><br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Responsbeheer<br /> </td> 
   <td> Hiermee wordt het succes en de winstgevendheid van marketingcampagnes gemeten of worden voorstellen voor alle communicatiekanalen aangeboden.  Optioneel. <a href="../../campaign/using/about-response-manager.md">Meer informatie</a> <br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Toegang tot externe gegevens (Federated Data Access)<br /> </td> 
   <td> Verstrekt de Federated optie van de Toegang van Gegevens (FDA) om informatie te verwerken die in één of meerdere externe gegevensbestanden wordt opgeslagen zodat u tot externe gegevens kunt toegang hebben zonder de structuur van de gegevens van Adobe Campaign te veranderen.  Optioneel. <a href="../../workflow/using/accessing-an-external-database--fda-.md">Meer informatie</a> <br /> </td> 
   <td> Alles<br /> </td> 
  </tr> 
  <tr> 
   <td> Campagnes optimaliseren<br /> </td> 
   <td> Controles, filters en controleren het verzenden van leveringen zodat de verzonden berichten het best aan de behoeften en de verwachtingen van klanten voldoen, in overeenstemming met het beleid van het bedrijfs communicatie. Optioneel. <a href="../../campaign/using/about-campaign-typologies.md">Meer informatie</a> <br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Bewaking van de aflevering (e-maillevering)<br /> </td> 
   <td> Meet het succes van uw campagnes die uw ontvangers' inbox zonder stuitend bereiken, of als spam worden gemerkt. Optioneel. <a href="../../delivery/using/about-deliverability.md">Meer informatie</a> <br /> </td> 
   <td> Alles </td> 
  </tr> 
  <tr> 
   <td> Couponbeheer<br /> </td> 
   <td> Hiermee maakt u een set coupons die u kunt toevoegen aan toekomstige marketingaanbiedingen. Optioneel. <a href="../../delivery/using/personalized-coupons.md">Meer informatie</a> <br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Inbox Rendering (IR)<br /> </td> 
   <td> Hiermee kunt u een voorvertoning weergeven van het bericht dat is verzonden in de verschillende contexten waarin het kan worden ontvangen en de compatibiliteit van grote desktops en toepassingen controleren. Optioneel. <a href="../../delivery/using/inbox-rendering.md">Meer informatie</a><br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Centrale/lokale Marketing (Distributed Marketing)<br /> </td> 
   <td> Voert samenwerkingscampagnes uit tussen centrale entiteiten (hoofdkantoor, marketingafdelingen, enz.) en lokale entiteiten (verkooppunten, regionale agentschappen, enz.). Optioneel. <a href="../../campaign/using/about-distributed-marketing.md">Meer informatie</a><br /> </td> 
   <td> Marketing </td> 
  </tr> 
  <tr> 
   <td> CRM-connectoren<br /> </td> 
   <td> Verschillende CRM-connectors waarmee u uw Adobe Campaign-platform kunt koppelen aan systemen van derden.  <a href="../../platform/using/crm-connectors.md">Meer informatie</a> <br /> </td> 
   <td> Marketing</td> 
  </tr> 
  <tr> 
   <td> Web Analytics-connectors<br /> </td> 
   <td> Hiermee staat u Adobe Campaign en Adobe Analytics toe om te communiceren via het connectorpakket Web Analytics. Niet compatibel met Transactioneel overseinen (het pakket van het Centrum van het Bericht). <a href="../../platform/using/adobe-analytics-data-connector.md">Meer informatie</a><br /> </td> 
   <td> Marketing </td> 
  </tr> 
  <tr> 
   <td> AEM integratie<br /> </td> 
   <td> Hiermee kunt u de inhoud van uw e-mailleveringen en uw formulieren rechtstreeks in Adobe Experience Manager beheren, zodat u kunt profiteren van AEM functies voor het bewerken van inhoud en de leveringsmogelijkheden van Adobe Campaign. <a href="../../integrations/using/about-adobe-experience-manager.md">Meer informatie</a> <br /> </td> 
   <td> Marketing</td> 
  </tr> 
  <tr> 
   <td> Adobe Experience Cloud-integratie van gedeelde soorten publiek<br /> </td> 
   <td> Hiermee kunt u soorten publiek/segmenten uitwisselen en delen met Adobe Experience Cloud-oplossingen en kernservices. Vereist IMS. <a href="../../integrations/using/sharing-audiences-with-adobe-experience-cloud.md">Meer informatie</a> <br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Integratie met Adobe Experience Cloud<br /> </td> 
   <td> Hiermee kunt u soorten publiek/segmenten van verschillende Adobe Experience Cloud-oplossingen importeren en exporteren naar Adobe Campaign. Optioneel. <a href="../../integrations/using/configuring-ims.md#installing-the-package">Meer informatie</a> </td> 
   <td> Marketing</td> 
  </tr> 
  <tr> 
   <td> Verordening inzake bescherming van privacydata<br /> </td> 
   <td> Bevat extra functionaliteit om met uw naleving van de Privacy in Campaign Classic te helpen. <a href="https://helpx.adobe.com/nl/campaign/kb/acc-privacy.html">Meer informatie</a> <br /> </td> 
   <td> Alles</td> 
  </tr> 
  <tr> 
   <td> Overdracht naar middelste bron <br /> </td> 
   <td> Geeft details over de installatie en configuratie van een server voor midsourcing, alsook over de implementatie van een instantie die derden in staat stelt berichten te verzenden in de modus voor midsourcing. Optioneel. <a href="../../installation/using/mid-sourcing-server.md">Meer informatie</a> <br /> </td> 
   <td> Marketing </td> 
  </tr> 
  <tr> 
   <td> Midsourcingplatform<br /> </td> 
   <td> Deze configuratie is een optimale middenoplossing tussen een ontvangen (ASP) configuratie en internalisering. De naar buiten gerichte uitvoeringscomponenten worden uitgevoerd op een "mid-sourcing"-server die wordt gehost op Adobe Campaign. Optioneel. <a href="../../installation/using/mid-sourcing-server.md">Meer informatie</a> <br /> </td> 
   <td> Midden-sourcing </td> 
  </tr> 
  <tr> 
   <td> AMP-ondersteuning<br /> </td> 
   <td> Hiermee kunt u het nieuwe interactieve AMP gebruiken voor e-mailindeling en dynamische e-mailberichten verzenden. Optioneel. <a href="../../delivery/using/defining-interactive-content.md">Meer informatie</a> <br /> </td> 
   <td> Alles </td> 
  </tr> 
  <tr> 
   <td> ACS Connector<br /> </td> 
   <td> Bridges Adobe Campaign v7 en Adobe Campaign Standard. Het is een geïntegreerde eigenschap in Campagne v7 die automatisch gegevens aan Campaign Standard herhaalt, die het beste van beide toepassingen verenigt. Optioneel. <a href="../../integrations/using/acs-connector-principles-and-data-cycle.md">Meer informatie</a> <br /> </td> 
   <td> Marketing </td> 
  </tr> 
 </tbody> 
</table>

### Message Center-pakket {#message-center-package}

U moet leveringskanalen installeren (E-mail, Mobiel kanaal, Mobiel App-kanaal, enz.) voordat u het Transactiebericht installeert (Message Center-pakket). Als u een project van het Centrum van het Bericht van het e-mail-enige bent begonnen, en een nieuw kanaal daarna moet toevoegen, moet u deze stappen volgen:

1. Installeer het nieuwe kanaal, bijvoorbeeld het **Mobiel kanaal**, met de wizard Pakket importeren ( **[!UICONTROL Tools > Advanced > Import package > Adobe Campaign package]**).
1. Importeer het bestand ( **[!UICONTROL Tools > Advanced > Import package > File]**) en selecteer:

   ```
   \datakit\nms\[Your language]\package\messageCenter.xml
   ```

1. Bewaar in **[!UICONTROL XML data content to import]** alleen de leveringssjabloon van het Berichtencentrum die overeenkomt met het gerelateerde kanaal. Als u bijvoorbeeld het **Mobiel kanaal** hebt toegevoegd, houdt u alleen het **entities**-element dat overeenkomt met de **[!UICONTROL Mobile transactional message]** (smsTriggerMessage)-sjabloon. Als u de **Mobile App Channel** hebt toegevoegd, bewaart u alleen het **iOS-transactiebericht**-sjablonen (iosTriggerMessage) en **Transactiebericht voor Android** (androidTriggerMessage).

   ![](assets/messagecenter_install_channel.png)

>[!CAUTION]
>
>De leveringsmalplaatjes van het Centrum van het Bericht voor LIJN zullen niet beschikbaar zijn als de pakketten van het Centrum van het Bericht vóór LIJN worden geïnstalleerd

