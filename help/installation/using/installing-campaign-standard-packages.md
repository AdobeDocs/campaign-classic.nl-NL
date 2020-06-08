---
title: Campagne Classic-standaardpakketten installeren
seo-title: Campagne Classic-standaardpakketten installeren
description: Campagne Classic-standaardpakketten installeren
seo-description: null
page-status-flag: never-activated
uuid: 1cba9487-52fc-442f-ae99-f8a2c157f25e
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: initial-configuration
discoiquuid: dd8f9adf-208c-42d9-b1a7-bfc8a690687e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: e059fc9e2bfade30454601f31990c3ec14b8a847
workflow-type: tm+mt
source-wordcount: '1212'
ht-degree: 0%

---


# Campagne Classic-standaardpakketten installeren{#installing-campaign-standard-packages}

## Informatie over standaardpakketten {#campaign-standard-packages}

Pakketten zijn een reeks functies die naar wens kunnen worden geïnstalleerd. Hiermee kunt u meer opties aan uw instantie toevoegen.

>[!CAUTION]
>
>U mag alleen pakketten installeren die overeenkomen met de opties die in uw licentiecontract zijn vermeld.
>
>Nadat een pakket is geïnstalleerd, kunt u het niet verwijderen. Het installeren van een nieuw pakket kan al uw platform beïnvloeden: het moet worden getest en gevalideerd vóór de definitieve implementatie.

Een standaardpakket installeren:

1. Open de wizard voor het importeren van pakketten vanuit **[!UICONTROL Tools > Advanced > Package import...]** de Adobe Campagne-clientconsole.
1. Selecteer **[!UICONTROL Install a standard package]**.
1. Controleer in de lijst die wordt weergegeven de pakketten die u wilt installeren.
   >[!NOTE]
   >
   >Als een pakket grijs wordt weergegeven, kunt u het niet installeren. Dit betekent dat het al is geïnstalleerd of niet compatibel is met uw instantie. U kunt bijvoorbeeld het pakket met het platform **voor** midsourcing niet installeren op een marketingexemplaar. Deze gegevens vindt u in de onderstaande tabel.
1. Klik **[!UICONTROL Next]** en vervolgens **[!UICONTROL Start]** om de pakketinstallatie te starten.

   Nadat de pakketten zijn geïnstalleerd, wordt op de voortgangsbalk **100%** weergegeven. In de installatielogboeken ziet u het volgende bericht: **[!UICONTROL Installation of packages successful]**.

1. **[!UICONTROL Close]** het installatievenster.

De pakketten zijn nu geïnstalleerd.

### Lijst van uit-van-de-doos Pakketten {#list-of-standard-packages}

De volgende tabel bevat een lijst met alle standaardpakketten met hun beschrijving, het instantietype waarop ze kunnen worden geïnstalleerd (Marketing, Midden, enz.) en aanvullende informatie.

<table> 
 <thead> 
  <tr> 
   <th> Pakket </th> 
   <th> Beschrijving </th> 
   <th> Instantietype </th> 
   <th> Meer informatie </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Aflevering<br /> </td> 
   <td> Controleert leveringen en uiteindelijke problemen die worden aangetroffen wanneer berichten worden verzonden.<br /> </td> 
   <td> Alles</td> 
   <td> <a href="../../delivery/using/monitoring-a-delivery.md">Meer informatie</a></td> 
  </tr> 
  <tr> 
   <td> Marketingcampagnes (Campagne)<br /> </td> 
   <td> Definieert, optimaliseert, voert en analyseert mededelingen en marketing campagnes uit.<br /> </td> 
   <td> Marketing</td> 
   <td> <a href="../../campaign/using/designing-marketing-campaigns.md">Meer informatie</a> </td> 
  </tr> 
  <tr> 
   <td> Marketing resources (MRM)<br /> </td> 
   <td> Controls marketing actions op een samenwerkingswijze door beheer en het volgen van de taken, de begrotingen en de marketing middelen te verstrekken.<br /> </td> 
   <td> Marketing</td> 
   <td> <a href="../../campaign/using/about-marketing-resource-management.md">Meer informatie</a> </td> 
  </tr> 
  <tr> 
   <td> Aanbiedingsengine (interactie)<br /> </td> 
   <td> Reageert in real time tijdens een interactie met een bepaald contact (een klant of een doel) door hen één of verscheidene aangepaste aanbiedingen te maken. <br /> </td> 
   <td> Alles<br /> </td> 
   <td> Optioneel, <a href="../../interaction/using/interaction-and-offer-management.md">Meer informatie</a></td> 
  </tr> 
  <tr> 
   <td> Besturing van de aanbiedingsengine met uitvoeringsinstantie<br /> </td> 
   <td> </td> 
   <td> Marketing<br /> </td> 
   <td> Optioneel</td> 
  </tr> 
  <tr> 
   <td> De engine voor uitvoeringsinstanties aanbieden<br /> </td> 
   <td> </td> 
   <td> Midden, uitvoering <br /> </td> 
   <td> Optioneel</td> 
  </tr> 
  <!--tr> 
   <td> Lead Management (Leads) (deprecated)<br /> </td> 
   <td> Simplifies the process of building and maintaining the entire leads management life cycle. <br /> </td> 
   <td> Yes<br /> </td> 
   <td> Optional, <a href="https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html">Learn More</a> </td> 
  </tr--> 
  <tr> 
   <td> Sociale netwerken (sociale marketing) <br /> </td> 
   <td> Synchroniseert Adobe Campaign met Twitter en Facebook.<br /> </td> 
   <td> Alles</td> 
   <td> <a href="../../social/using/about-social-marketing.md">Meer informatie</a> </td> 
  </tr> 
  <tr> 
   <td> Transactionaal berichtenbeheer (Berichtcentrum - Controle)<br /> </td> 
   <td> Beheert triggerberichten die worden gegenereerd door gebeurtenissen die worden geactiveerd door informatiesystemen.<br /> </td> 
   <td> Marketing<br /> </td> 
   <td> Optioneel, <a href="../../message-center/using/about-transactional-messaging.md">Meer informatie</a> </td> 
  </tr> 
  <tr> 
   <td> Transactiebericht uitvoeren (Berichtcentrum - Uitvoering) <br /> </td> 
   <td> Zorgt voor hogere beschikbaarheid en beter beheer van de belasting.<br /> </td> 
   <td> Uitvoering<br /> </td> 
   <td> Optioneel, <a href="../../message-center/using/about-transactional-messaging.md">Meer informatie</a> </td> 
  </tr> 
  <tr> 
   <td> LINE-kanaal<br /> </td> 
   <td> Verstuurt leveringen via het LINE-kanaal met Adobe Campaign.<br /> </td> 
   <td> Alles<br /> </td> 
   <td> Optioneel, berichtcentrum verplicht</td> 
  </tr> 
  <tr> 
   <td> Direct Mail Channel<br /> </td> 
   <td> Verstuurt leveringen via het directe-mailkanaal via Adobe Campaign.<br /> </td> 
   <td> Alles<br /> </td> 
   <td> Optioneel, <a href="../../delivery/using/about-direct-mail-channel.md">Meer informatie</a> </td> 
  </tr> 
  <tr> 
   <td> Mobiel kanaal (SMS) <br /> </td> 
   <td> Verstuurt leveringen via het mobiele/sms-kanaal met Adobe Campaign.<br /> </td> 
   <td> Alles<br /> </td> 
   <td> Optioneel, <a href="../../delivery/using/sms-channel.md">Meer informatie</a> </td> 
  </tr> 
  <tr> 
   <td> Telefoonkanaal<br /> </td> 
   <td> Verzendt leveringen via het telefoonkanaal met de Campagne van Adobe.<br /> </td> 
   <td> Alles<br /> </td> 
   <td> Optioneel</td> 
  </tr>
  <tr> 
   <td> Mobiel App-kanaal<br /> </td> 
   <td> Gebruikt het Adobe Campaign-platform om persoonlijke meldingen naar iOS- en Android-terminals te verzenden via apps. <br /> </td> 
   <td> Alles<br /> </td> 
   <td> Optioneel, <a href="../../delivery/using/about-mobile-app-channel.md">Meer informatie</a> </td> 
  </tr> 
  <tr> 
   <td> Inhoudsbeheer<br /> </td> 
   <td> Hiermee maakt u periodieke nieuwsbrieven of websites en valideert en publiceert u uw berichten.<br /> </td> 
   <td> </td> 
   <td> <a href="../../delivery/using/about-content-management.md">Meer informatie</a> </td> 
  </tr> 
  <tr> 
   <td> Online enquêtes (Enquêtemanager)<br /> </td> 
   <td> Hiermee maakt en beheert u onlineformulieren voor het toevoegen of wijzigen van profielgegevens, voor het abonneren, voor het opzeggen van abonnementen of voor het invoeren van wedstrijden.<br /> </td> 
   <td> Marketing<br /> </td> 
   <td> Optioneel, <a href="../../web/using/about-surveys.md">Meer informatie</a> </td> 
  </tr> 
  <tr> 
   <td> Marketing Analytics<br /> </td> 
   <td> Hiermee kunt u gegevens analyseren en meten, statistieken berekenen, het maken en berekenen van rapporten vereenvoudigen en optimaliseren. U kunt ook rapporten maken en doelpopulaties maken. <br /> </td> 
   <td> Marketing<br /> </td> 
   <td> Optioneel, <a href="../../reporting/using/about-cubes.md">Meer informatie</a> </td> 
  </tr> 
  <tr> 
   <td> Responsbeheer<br /> </td> 
   <td> Hiermee wordt het succes en de winstgevendheid van marketingcampagnes gemeten of worden voorstellen voor alle communicatiekanalen aangeboden.<br /> </td> 
   <td> Marketing<br /> </td> 
   <td> Optioneel, <a href="../../campaign/using/about-response-manager.md">Meer informatie</a> </td> 
  </tr> 
  <tr> 
   <td> Toegang tot externe gegevens (Federated Data Access)<br /> </td> 
   <td> Biedt de FDA-optie (Federated Data Access) om gegevens te verwerken die zijn opgeslagen in een of meer externe databases, zodat u toegang hebt tot externe gegevens zonder de structuur van Adobe Campagne-gegevens te wijzigen.<br /> </td> 
   <td> Alles<br /> </td> 
   <td> Optioneel, <a href="../../workflow/using/accessing-an-external-database--fda-.md">Meer informatie</a> </td> 
  </tr> 
  <tr> 
   <td> Campagne optimaliseren<br /> </td> 
   <td> Controles, filters en controleren het verzenden van leveringen zodat de verzonden berichten het best aan de behoeften en de verwachtingen van klanten voldoen, in overeenstemming met het beleid van het bedrijfs communicatie. <br /> </td> 
   <td> Marketing<br /> </td> 
   <td> Optioneel, <a href="../../campaign/using/about-campaign-typologies.md">Meer informatie</a> </td> 
  </tr> 
  <tr> 
   <td> Leverbaarheidscontrole (e-maillevering)<br /> </td> 
   <td> Meet het succes van uw campagnes die uw ontvangers' inbox zonder stuitend bereiken, of als spam worden gemerkt.<br /> </td> 
   <td> Alles </td> 
   <td> Optioneel, <a href="https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliverability.html">Meer informatie</a> </td> 
  </tr> 
  <tr> 
   <td> Couponbeheer<br /> </td> 
   <td> Hiermee maakt u een set coupons die u kunt toevoegen aan toekomstige marketingaanbiedingen.<br /> </td> 
   <td> Marketing<br /> </td> 
   <td> Optioneel, <a href="../../delivery/using/personalized-coupons.md">Meer informatie</a> </td> 
  </tr> 
  <tr> 
   <td> Inbox Rendering (IR)<br /> </td> 
   <td> Hiermee kunt u een voorvertoning weergeven van het bericht dat is verzonden in de verschillende contexten waarin het kan worden ontvangen en de compatibiliteit van grote desktops en toepassingen controleren. U hebt een Litmus-account nodig.<br /> </td> 
   <td> Marketing<br /> </td> 
   <td> Optioneel, <a href="../../delivery/using/inbox-rendering.md">Meer informatie</a> </td> 
  </tr> 
  <tr> 
   <td> Centrale/lokale Marketing (Distributed Marketing)<br /> </td> 
   <td> Voert samenwerkingscampagnes uit tussen centrale entiteiten (hoofdkantoor, marketingafdelingen, enz.) en lokale entiteiten (verkooppunten, regionale agentschappen, enz.).<br /> </td> 
   <td> Marketing </td> 
   <td> Optioneel, <a href="../../campaign/using/about-distributed-marketing.md">Meer informatie</a> </td> 
  </tr> 
  <tr> 
   <td> CRM-connectors<br /> </td> 
   <td> Verschillende CRM-connectors waarmee u uw Adobe Campagne-platform kunt koppelen aan systemen van derden.<br /> </td> 
   <td> Marketing</td> 
   <td> <a href="../../platform/using/crm-connectors.md">Meer informatie</a> </td> 
  </tr> 
  <tr> 
   <td> Webanalytische connectors<br /> </td> 
   <td> Hiermee staat u Adobe Campaign en Adobe Analytics toe om te communiceren via het connectorpakket Web Analytics.<br /> </td> 
   <td> Marketing </td> 
   <td> Niet compatibel met Transactieberichten, <a href="../../platform/using/adobe-analytics-data-connector.md">Meer informatie</a> </td> 
  </tr> 
  <tr> 
   <td> AEM-integratie<br /> </td> 
   <td> Hiermee kunt u de inhoud van uw e-mailleveringen en uw formulieren rechtstreeks beheren in Adobe Experience Manager, zodat u kunt profiteren van de functionaliteit van AEM voor het bewerken van inhoud en de leveringsmogelijkheden van Adobe Campaign.<br /> </td> 
   <td> Marketing</td> 
   <td> <a href="../../integrations/using/about-adobe-experience-manager.md">Meer informatie</a> </td> 
  </tr> 
  <tr> 
   <td> Integratie van gedeelde soorten publiek in Adobe Marketing Cloud<br /> </td> 
   <td> Hiermee kunt u soorten publiek en segmenten uitwisselen en delen met Adobe Experience Cloud-oplossingen en kernservices.<br /> </td> 
   <td> Marketing<br /> </td> 
   <td> Vereist IMS, <a href="../../integrations/using/sharing-audiences-with-adobe-experience-cloud.md">Meer informatie</a> </td> 
  </tr> 
  <tr> 
   <td> Integratie met Adobe Marketing Cloud<br /> </td> 
   <td> Hiermee kunt u soorten publiek/segmenten van verschillende Adobe Marketing Cloud-oplossingen importeren en exporteren naar Adobe Campagne. </td> 
   <td> Marketing</td> 
   <td> Optioneel, <a href="../../integrations/using/configuring-ims.md#installing-the-package">Meer informatie</a> </td> 
  </tr> 
  <tr> 
   <td> Privacy Data Protection-verordening<br /> </td> 
   <td> Bevat extra functionaliteit om met uw naleving van de Privacy in Classic van de Campagne te helpen.<br /> </td> 
   <td> Alles</td> 
   <td> <a href="https://helpx.adobe.com/campaign/kb/acc-privacy.html">Meer informatie</a> </td> 
  </tr> 
  <tr> 
   <td> Overschakelen naar middelmatig bronnen <br /> </td> 
   <td> Geeft details over de installatie en configuratie van een server voor midsourcing, alsook over de implementatie van een instantie die derden in staat stelt berichten te verzenden in de modus voor midsourcing.<br /> </td> 
   <td> Marketing </td> 
   <td> Optioneel, <a href="../../installation/using/mid-sourcing-server.md">Meer informatie</a> </td> 
  </tr> 
  <tr> 
   <td> Middelsourcingsplatform<br /> </td> 
   <td> Deze configuratie is een optimale middenoplossing tussen een ontvangen (ASP) configuratie en internalisering. De naar buiten gerichte uitvoeringscomponenten worden uitgevoerd op een "mid-sourcing"-server die wordt gehost in Adobe Campaign.<br /> </td> 
   <td> Midden-sourcing </td> 
   <td> Optioneel, <a href="../../installation/using/mid-sourcing-server.md">Meer informatie</a> </td> 
  </tr> 
  <tr> 
   <td> ACS-connector<br /> </td> 
   <td> Bridge Bridge Bridge Adobe Campaign v7 en Adobe Campaign Standard. Het is een geïntegreerde eigenschap in Campagne v7 die automatisch gegevens aan de Norm van de Campagne herhaalt, die het beste van beide toepassingen verenigt. <br /> </td> 
   <td> Marketing </td> 
   <td> Optioneel, <a href="../../integrations/using/acs-connector-principles-and-data-cycle.md">Meer informatie</a> </td> 
  </tr> 
 </tbody> 
</table>

### Message Center-pakket {#message-center-package}

Om een leveringskanaal (Mobiel kanaal, Mobiel App kanaal, enz.) toe te voegen, moet dit worden uitgevoerd alvorens het pakket van het Centrum van het Bericht te installeren. Als u een project van het Centrum van het Bericht op het e-mailkanaal bent begonnen, dan, in het midden van het project, besluit u om een nieuw kanaal toe te voegen, moet u deze stappen volgen:

1. Installeer het kanaal dat u wilt, bijvoorbeeld het **mobiele kanaal**, met de wizard voor het importeren van pakketten ( **[!UICONTROL Tools > Advanced > Import package > Adobe Campaign package]**).
1. Importeer het bestand ( **[!UICONTROL Tools > Advanced > Import package > File]**) en selecteer:

   ```
   \datakit\nms\[Your language]\package\messageCenter.xml
   ```

1. Houd in het **[!UICONTROL XML data content to import]** venster alleen de leveringssjabloon van het Berichtencentrum bij die overeenkomt met het gekoppelde kanaal. Als u bijvoorbeeld het **mobiele kanaal** hebt toegevoegd, houdt u alleen het element **entities** die overeenkomen met de sjabloon **[!UICONTROL Mobile transactional message]** (smsTriggerMessage). Als u het **Mobile App Channel** hebt toegevoegd, houdt u alleen het **iOS-transactiemalplaatje** (iosTriggerMessage) en het **Android-transactiebericht** (androidTriggerMessage).

   ![](assets/messagecenter_install_channel.png)

### LINE-pakket {#line-package}

Als u leveringen wilt kunnen verzenden via het LINE-kanaal met Adobe Campagne, moet u het LINE-pakket installeren.

De installatie van het LINE-pakket is een standaardinstallatie die wordt beschreven in de sectie [Pakketten](../../platform/using/working-with-data-packages.md#importing-packages) importeren.

![](assets/line_config_1.png)

>[!CAUTION]
>
>De leveringsmalplaatjes van het Centrum van het Bericht voor LIJN zullen niet beschikbaar zijn als de pakketten van het Centrum van het Bericht vóór LIJN worden geïnstalleerd.
