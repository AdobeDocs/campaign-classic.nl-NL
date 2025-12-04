---
product: campaign
title: Algemene rapporten
description: Algemene rapporten
badge: label="v7" type="Informative" tooltip="Alleen van toepassing op Campaign Classic v7"
feature: Reporting, Monitoring
exl-id: 6839fd7e-ecf4-4504-90a8-0207bc3991e4
source-git-commit: 2186b8a30449cb023cb07305ba64d53f2c8adab1
workflow-type: tm+mt
source-wordcount: '2292'
ht-degree: 3%

---

# Algemene rapporten {#global-reports}



Deze rapporten hebben betrekking op de activiteit van de gegevens in de gehele database. Ga naar het tabblad **[!UICONTROL Reports]** als u het dashboard met rapporten wilt weergeven.

![](assets/s_ncs_user_report_delivery_link.png)

Klik op de naam van de rapporten om deze weer te geven. De volgende rapporten zijn standaard beschikbaar:

![](assets/s_ncs_user_report_global_list.png)

>[!NOTE]
>
>In deze sectie worden alleen de rapporten weergegeven die betrekking hebben op leveringen.

* **[!UICONTROL Delivery throughput]** : verwijs naar [&#x200B; productie van de Levering &#x200B;](#delivery-throughput).
* **[!UICONTROL Browsers]** : verwijs naar [&#x200B; Browsers &#x200B;](#browsers).
* **[!UICONTROL Sharing to social networks]** : verwijs naar [&#x200B; het Delen aan sociale netwerken &#x200B;](#sharing-to-social-networks).
* **[!UICONTROL Statistics on sharing activities]** : verwijs naar [&#x200B; Statistieken over het delen van activiteiten &#x200B;](#statistics-on-sharing-activities).
* **[!UICONTROL Operating systems]** : verwijs naar [&#x200B; Werkende systemen &#x200B;](#operating-systems).
* **[!UICONTROL URLs and click streams]** : verwijs naar [&#x200B; URLs en klik stromen &#x200B;](../../reporting/using/delivery-reports.md#urls-and-click-streams).
* **[!UICONTROL Tracking indicators]** : verwijs naar [&#x200B; het Volgen indicatoren &#x200B;](../../reporting/using/delivery-reports.md#tracking-indicators).
* **[!UICONTROL Non-deliverables and bounces]** : verwijs naar [&#x200B; Niet-te leveren punten en stuitingen &#x200B;](#non-deliverables-and-bounces).
* **[!UICONTROL User activities]** : verwijs naar [&#x200B; activiteiten van de Gebruiker &#x200B;](#user-activities).
* **[!UICONTROL Subscription tracking]** : verwijs naar [&#x200B; het volgen van het Abonnement &#x200B;](#subscription-tracking).
* **[!UICONTROL Delivery summary]** : verwijs naar [&#x200B; Overzicht van de Levering &#x200B;](../../reporting/using/delivery-reports.md#delivery-summary).
* **[!UICONTROL Delivery statistics]** : verwijs naar [&#x200B; statistieken van de Levering &#x200B;](#delivery-statistics).
* **[!UICONTROL Breakdown of opens]** : verwijs naar [&#x200B; Uitsplitsing van opent &#x200B;](#breakdown-of-opens).

## Leveringsdoorvoer {#delivery-throughput}

Dit verslag bevat informatie over de leveringsproductie van het gehele platform voor een bepaalde periode. Om de snelheid te meten waarbij de berichten worden geleverd, zijn de criteria het aantal berichten die per uur worden verzonden en de grootte van de berichten (in beetjes per seconde). In het onderstaande voorbeeld ziet u in de eerste grafiek de geslaagde leveringen in blauw en het aantal onjuiste leveringen in oranje.

![](assets/s_ncs_user_report_toolbar.png)

U kunt de weergegeven waarden configureren door de tijdschaal te wijzigen: een weergave van 1 uur, een weergave van 3 uur, een weergave van 24 uur, enzovoort. Klik op **[!UICONTROL Refresh]** om uw selectie te bevestigen.

>[!NOTE]
>
>Als uw instantie op AWS wordt ontvangen, kunt u het aantal leveringen ook controleren die per uur gebruikend het Campaign Classic [&#x200B; Controlebord &#x200B;](https://experienceleague.adobe.com/docs/control-panel/using/sftp-management/sftp-storage-management.html) worden verzonden. Controleer of uw versie wordt gehost op AWS door de volgende stappen te volgen op [deze pagina](https://experienceleague.adobe.com/docs/control-panel/using/faq.html?lang=nl).
>
>Het configuratiescherm is toegankelijk voor alle gebruikers met beheerdersrechten. De stappen om toegang met beheerdersrechten aan een gebruiker te verlenen worden gedetailleerd beschreven op [deze pagina](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html?lang=nl#discover-control-panel).
>
>Merk op dat uw instantie met de recentste [&#x200B; Gouden Standaard &#x200B;](../../rn/using/gold-standard.md) bouwstijl of de [&#x200B; recentste bouw GA (21.1.3) &#x200B;](../../rn/using/latest-release.md) moet worden bevorderd. Leer hoe te om uw versie in [&#x200B; te controleren deze sectie &#x200B;](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

## Gebruikersactiviteiten {#user-activities}

Dit rapport toont de uitsplitsing van opent, klikt en transacties per half uur, uur of dag, in de vorm van een grafiek.

![](assets/s_ncs_user_user_report.png)

De volgende opties zijn beschikbaar:

* **[!UICONTROL Opens]** : Het totale aantal geopende berichten. E-mails in tekstindeling worden niet in aanmerking genomen. Voor meer informatie bij het volgen opent, verwijs naar [&#x200B; het Volgen opent &#x200B;](../../reporting/using/indicator-calculation.md#tracking-opens-).
* **[!UICONTROL Clicks]** : Het totale aantal klikken op koppelingen in leveringen. Er wordt geen rekening gehouden met klikken op abonnementkoppelingen en spiegelpagina&#39;s.
* **[!UICONTROL Transactions]** : Het totale aantal transacties nadat een bericht is ontvangen. Om een transactie in aanmerking te nemen, moet een webtrackingtag van het transactietype in de overeenkomstige Web-pagina worden opgenomen. Webvolgende configuratie wordt voorgesteld in [&#x200B; deze sectie &#x200B;](../../configuration/using/about-web-tracking.md).

## Niet-leverbare items en niet-bezorgingen {#non-deliverables-and-bounces}

Dit verslag geeft een overzicht van de niet-te leveren posten en een uitsplitsing van de bedragen per internetdomein.

**[!UICONTROL Number of messages processed]** vertegenwoordigt het totale aantal berichten die door de leveringsserver worden verwerkt. Deze waarde is lager dan het aantal berichten dat moet worden afgeleverd wanneer bepaalde leveringen zijn gestopt of gepauzeerd (voordat deze door de server worden verwerkt).

![](assets/s_ncs_user_errors_report.png)

**[!UICONTROL Breakdown of errors by type]**

>[!NOTE]
>
>De fouten die in dit rapport worden weergegeven, activeren het quarantaineproces. Voor meer op quarantainebeheer, verwijs naar [&#x200B; het beheer van de quarantaine &#x200B;](../../delivery/using/delivery-failures-quarantine.md).

In het eerste deel van dit verslag wordt de uitsplitsing van niet-te leveren producten in de vorm van een tabel van waarden en een grafiek weergegeven.

Voor elk fouttype hebben we:

* het aantal foutberichten van dit type;
* het percentage berichten met dergelijke fouten in vergelijking met het totale aantal berichten met fouten;
* het percentage van foutenmeldingen van dit type vergeleken met het totale aantal verwerkte berichten.

De volgende indicatoren worden gebruikt:

* **[!UICONTROL User unknown]** : Fouttype dat tijdens de levering wordt gegenereerd om aan te geven dat het e-mailadres ongeldig is.
* **[!UICONTROL Invalid domain]** : Fouttype dat wordt gegenereerd bij het verzenden van een levering om aan te geven dat het domein van het e-mailadres onjuist is of niet bestaat.
* **[!UICONTROL Inbox full]** : Het fouttype dat wordt gegenereerd na vijf leveringspogingen geeft aan dat het postvak van de ontvanger te veel berichten bevat.
* **[!UICONTROL Account disabled]** : Het type fout dat wordt gegenereerd bij het verzenden van een levering om aan te geven dat het adres niet langer bestaat.
* **[!UICONTROL Rejected]** : Het type fout dat wordt gegenereerd wanneer een adres wordt afgewezen door de IAP (Internet Access Provider), bijvoorbeeld na de toepassing van een beveiligingsregel (anti-spamsoftware).
* **[!UICONTROL Unreachable]** : Fouttype dat optreedt in de tekenreeks voor berichtdistributie: incident in het SMTP-relais, tijdelijk onbereikbaar domein, enz.
* **[!UICONTROL Not connected]** : Het type fout geeft aan dat de mobiele telefoon van de ontvanger op het moment van verzending wordt uitgeschakeld of losgekoppeld van het netwerk.

  >[!NOTE]
  >
  >Deze indicator heeft alleen betrekking op leveringen op mobiele kanalen. Raadpleeg [deze sectie](../../delivery/using/sms-channel.md) voor meer informatie.

  U kunt elke regel van de waardetabel openen door op het symbool `[+]` te klikken. Voor elk fouttype kunt u de indeling van foutberichten per domein weergeven.

  ![](assets/s_ncs_user_errors_report_detail.png)

**[!UICONTROL Breakdown of errors per domain]**

In het tweede gedeelte van dit rapport wordt de uitsplitsing van fouten per internetdomein getoond in de vorm van een tabel met waarden en een grafiek.

Voor elke domeinnaam hebben we:

* het aantal berichten met fouten voor dit domein,
* het percentage berichten met fouten voor dit domein in vergelijking met het totale aantal berichten dat voor dit domein wordt verwerkt;
* het percentage foutberichten voor dit domein in vergelijking met het totale aantal foutberichten.

U kunt elke lijn van de waardetabel openen door [ + ] te klikken symbool. Voor elk domeintype kunt u de indeling van foutberichten per fouttype weergeven.

![](assets/s_ncs_user_errors_report_detail2.png)

>[!NOTE]
>
>De domeinnamen die in dit rapport worden weergegeven, worden op kubusniveau gedefinieerd. Als u deze waarden wilt wijzigen, bewerkt u de kubus **[!UICONTROL Delivery logs (broadlogrcp)]** . Voor meer op dit, verwijs naar [&#x200B; deze sectie &#x200B;](../../reporting/using/ac-cubes.md). De categorie **[!UICONTROL Others]** bevat domeinnamen die niet tot een specifieke klasse behoren.

## Browsers {#browsers}

Dit verslag geeft een overzicht van de internetbrowsers die door de ontvangers van de levering voor de betrokken periode zijn gebruikt.

>[!NOTE]
>
>De waarden in dit rapport zijn schattingen: alleen ontvangers die op een levering hebben geklikt, worden in aanmerking genomen.

**Globale statistieken**

De algemene statistieken over browsergebruik worden gepresenteerd in de vorm van een tabel met waarden en een grafiek.

![](assets/dlv_explorers_report.png)

De volgende indicatoren worden gebruikt:

* **[!UICONTROL Visitors]** : Het totale aantal beoogde ontvangers (per internetbrowser) nadat u minstens één keer op een levering hebt geklikt.
* **[!UICONTROL Pages viewed]** : Het totale aantal klikken op koppelingen in een levering (per internetbrowser) voor alle leveringen.
* **[!UICONTROL Usage rate]** : Deze frequentie geeft de uitsplitsing weer van bezoekers (per internetbrowser) in verhouding tot het totale aantal bezoekers.

**Statistieken per browser**

In de lijst van globale statistische waarden, kunt u elke browser naam klikken om hun gebruiksstatistieken te bekijken.

![](assets/s_ncs_user_explorers_report2.png)

Statistieken worden gepresenteerd in de vorm van een curve, een grafiek en een tabel met waarden.

De **[!UICONTROL History]** -curve geeft de aanwezigheidsgraad van deze browser per dag aan. De frequentie is de verhouding tussen het aantal bezoekers per dag (in deze browser) en het aantal bezoekers dat wordt gemeten op de dag met de hoogste aanwezigheidsgraad.

Het **[!UICONTROL Breakdown per version]** -diagram geeft de uitsplitsing weer van bezoekers per versie in vergelijking met het totale aantal bezoekers (in deze browser).

In de waardetabel worden de volgende indicatoren gebruikt:

* **[!UICONTROL Global rate]** : Deze frequentie geeft de uitsplitsing weer van bezoekers per versie in vergelijking met het totale aantal bezoekers (in alle browsers).
* **[!UICONTROL Relative rate]** : Deze frequentie geeft de uitsplitsing weer van bezoekers per versie in vergelijking met het totale aantal bezoekers (in deze browser).

### Delen naar sociale netwerken {#sharing-to-social-networks}

Met Viral Marketing kunnen ontvangers gegevens delen met hun contactnetwerk: ze kunnen een koppeling naar hun profiel toevoegen (Facebook, X - voorheen bekend als Twitter, enz.) of een bericht naar een vriend sturen. Elk aandeel en elke toegang tot gedeelde informatie wordt gevolgd binnen de levering. Voor meer informatie over virale marketing, verwijs naar [&#x200B; deze sectie &#x200B;](../../delivery/using/viral-and-social-marketing.md).

Dit rapport toont de uitsplitsing van gedeelde en geopende berichten per sociaal netwerk (Facebook, X, enz.) en/of per e-mail.

![](assets/s_ncs_user_social_report.png)

**[!UICONTROL Email delivery statistics]**

In de statistieken van de e-maillevering, worden twee waarden getoond:

* **[!UICONTROL Number of messages to be delivered]** : Het totale aantal berichten dat tijdens de leveringsanalyse wordt verwerkt.
* **[!UICONTROL Number of successful deliveries]** : aantal berichten dat is verwerkt.

**[!UICONTROL Sharing activities and mail open statistics]**

De centrale tabel toont de statistieken over e-mailaandelen en wordt geopend.

In de kolom **[!UICONTROL Shares]** hebben we de volgende indicatoren:

* **[!UICONTROL No. of sharing activities]** : Het totale aantal berichten dat op elk sociaal netwerk wordt gedeeld. Deze waarde is gelijk aan het totale aantal klikken op het pictogram van het overeenkomende **[!UICONTROL Links for sharing to social networks]** aanpassingsblok.
* **[!UICONTROL Breakdown]** : Dit percentage geeft de uitsplitsing weer van de aandelen per sociaal netwerk in verhouding tot het totale aantal aandelen.
* **[!UICONTROL Sharing rate]** : Deze snelheid geeft de uitsplitsing weer van de aandelen per sociaal netwerk, in verhouding tot het aantal te leveren berichten.

In de kolom **[!UICONTROL Opens]** hebben we de volgende indicatoren:

* **[!UICONTROL No. of opens]** : Het totale aantal berichten dat is geopend door de personen aan wie het bericht is doorgestuurd (via het **[!UICONTROL Links for sharing to social networks]** personalisatieblok). Deze waarde is gelijk aan het aantal keren dat de spiegelpagina is weergegeven. Opens door ontvangers van de levering worden niet in aanmerking genomen.
* **[!UICONTROL Breakdown]** : Deze snelheid geeft de uitsplitsing weer van de openingen per sociaal netwerk, in verhouding tot het totale aantal openingen.
* **[!UICONTROL Rate of opens]** : Dit percentage geeft de uitsplitsing weer van de beurzen per sociaal netwerk, in verhouding tot het totale aantal aandelen.

**[!UICONTROL Breakdown of sharing activities and opens]**

Deze sectie omvat twee grafieken die de indeling van de deelactiviteiten vertegenwoordigen en per sociaal netwerk worden geopend.

## Statistieken over de activiteiten voor het delen van diensten {#statistics-on-sharing-activities}

Dit rapport laat de evolutie zien van aandelen in sociale netwerken (Facebook, X - voorheen bekend als Twitter, email, enz.) in de tijd.

Voor meer informatie over virale marketing, verwijs naar [&#x200B; deze sectie &#x200B;](../../delivery/using/viral-and-social-marketing.md).

![](assets/s_ncs_user_social_report2.png)

Statistieken worden gepresenteerd in de vorm van een tabel met waarden en een grafiek.

De volgende indicatoren worden gebruikt:

* **[!UICONTROL New contacts]** : aantal nieuwe abonnementen na ontvangst van een bericht dat via e-mail wordt gedeeld. Deze waarde komt overeen met het aantal personen dat een bericht heeft ontvangen dat via e-mail is gedeeld, op **[!UICONTROL Subscription link]** heeft geklikt en het abonnementsformulier heeft ingevuld.
* **[!UICONTROL Opens]** : Het totale aantal berichten dat is geopend door de personen naar wie het bericht is overgebracht (via het **[!UICONTROL Link for sharing to social networks]** personalisatielblok). Deze waarde is gelijk aan het aantal keren dat de spiegelpagina is weergegeven. Opens door ontvangers van de levering worden niet in aanmerking genomen.
* **[!UICONTROL Sharing activities]** : Het totale aantal berichten dat via sociale netwerken wordt gedeeld. Deze waarde komt overeen met het totale aantal klikken op het pictogram van het **[!UICONTROL Links for sharing to social networks]** aanpassingsblok.

## Besturingssystemen {#operating-systems}

Dit verslag geeft een overzicht van de exploitatiesystemen die door de ontvangers van de levering voor de betrokken periode worden gebruikt.

>[!NOTE]
>
>De waarden in dit rapport zijn schattingen: alleen ontvangers die op een levering hebben geklikt, worden in aanmerking genomen.

**Globale statistieken**

De algemene gebruiksstatistieken van besturingssystemen worden gepresenteerd in de vorm van een tabel met waarden en een grafiek.

![](assets/s_ncs_user_os_report.png)

De volgende indicatoren worden gebruikt:

* **[!UICONTROL Visitors]** : dagelijkse gemiddelde van het totale aantal beoogde ontvangers (per besturingssysteem) die ten minste één keer op een levering hebben geklikt.
* **[!UICONTROL Pages viewed]** : dagelijkse gemiddelde van het totale aantal klikken op leveringskoppelingen (per besturingssysteem) voor alle leveringen.
* **[!UICONTROL Rate of use]** : Deze frequentie geeft de uitsplitsing weer van bezoekers (per besturingssysteem) in verhouding tot het totale aantal bezoekers.

**Statistieken per werkend systeem**

In de lijst van globale statistiekwaarden, klik de naam van elk werkend systeem om de statistieken per werkend systeem te bekijken.

![](assets/s_ncs_user_os_report2.png)

Statistieken worden gepresenteerd in de vorm van een curve, een grafiek en een tabel met waarden.

De **[!UICONTROL History]** -curve geeft de gebruiksfrequentie van dit besturingssysteem per dag aan. Dit percentage is de verhouding tussen het aantal bezoekers per dag (op dit besturingssysteem) en het aantal bezoekers dat wordt gemeten op de dag met de hoogste aanwezigheid.

Het **[!UICONTROL Breakdown by version]** -diagram geeft de uitsplitsing van bezoekers per versie weer in verhouding tot het totale aantal bezoekers op dit besturingssysteem.

In de waardetabel worden de volgende indicatoren gebruikt:

* **[!UICONTROL Global rate]** : Deze frequentie geeft de uitsplitsing weer van bezoekers (per versie) in verhouding tot het totale aantal bezoekers in het besturingssysteem.
* **[!UICONTROL Relative rate]** : Deze frequentie geeft de uitsplitsing weer van bezoekers (per versie) in verhouding tot het totale aantal bezoekers voor dit besturingssysteem.

## Abonnement bijhouden {#subscription-tracking}

Met dit rapport kunt u abonnementen op informatieservices controleren. Er worden abonnementen en afkortingen weergegeven.

![](assets/s_ncs_user_services_report.png)

Deze kan voor een abonnement worden weergegeven door op het knooppunt **[!UICONTROL Profiles and targets > Services and subscriptions]** van de startpagina of de verkenner te klikken. Selecteer het gewenste abonnement en klik op de tab **[!UICONTROL Reports]** . Het rapport **[!UICONTROL Subscriptions tracking]** is standaard beschikbaar. Het laat u de abonnement en unsubscription tendensen en het loyaliteitstarief over een periode zien. U kunt de representatie van deze gegevens configureren via de vervolgkeuzelijst. Klik **[!UICONTROL Refresh]** om de geselecteerde configuratie te bevestigen.

Voor verdere informatie, verwijs naar [&#x200B; deze pagina &#x200B;](../../delivery/using/managing-subscriptions.md).

**[!UICONTROL Number subscribed to date]** vertegenwoordigt het totale aantal mensen momenteel geabonneerd.

**[!UICONTROL Overall evolution of subscriptions]**

In de waardetabel worden de volgende indicatoren gebruikt:

* **[!UICONTROL Subscribers]** : Het totale aantal abonnees voor de betrokken periode.
* **[!UICONTROL Subscriptions]** : aantal abonnementen voor de betrokken periode.
* **[!UICONTROL Unsubscriptions]** : aantal opnemingen voor de betrokken periode.
* **[!UICONTROL Evolution]** : aantal afmeldingsopties min het aantal abonnementen. Het tarief wordt berekend op basis van het totale aantal abonnees.
* **[!UICONTROL Loyalty]** : Loyalty van abonnees voor de betrokken periode.

**[!UICONTROL Subscription evolution curves]**

Deze grafiek toont de ontwikkeling van de abonnementen en afboekingen voor de betrokken periode.

## Leveringsstatistieken {#delivery-statistics}

Dit rapport toont de uitsplitsing naar internetdomein van alle verwerkte en verzonden berichten, van harde en zachte geluiden, opent, klikt en afmeldt.

![](assets/s_ncs_user_broadcast_report.png)

De volgende indicatoren worden gebruikt:

* **[!UICONTROL Emails processed]** : Het totale aantal berichten dat door de leveringsserver wordt verwerkt.
* **[!UICONTROL Delivered]** : percentage van het aantal berichten dat correct is verwerkt in verhouding tot het totale aantal verwerkte berichten.
* **[!UICONTROL Hard bounces]** : percentage van het aantal &#39;harde&#39; grenzen in vergelijking met het totale aantal verwerkte berichten.
* **[!UICONTROL Soft bounces]** : percentage van het aantal &#39;zachte&#39; grenzen in vergelijking met het totale aantal verwerkte berichten.

  >[!NOTE]
  >
  >Voor meer op harde en zachte grenzen, verwijs naar [&#x200B; het beheer van de Quarantaine &#x200B;](../../delivery/using/delivery-failures-quarantine.md).

* **[!UICONTROL Opens]** : percentage van het aantal beoogde ontvangers dat een bericht ten minste één keer heeft geopend in vergelijking met het aantal berichten dat met succes is verwerkt.
* **[!UICONTROL Clicks]** : percentage van het aantal personen dat ten minste één keer in een levering heeft geklikt in vergelijking met het aantal berichten dat met succes is verwerkt.
* **[!UICONTROL Unsubscription]** : percentage van het aantal klikken op een koppeling zonder abonnement in verhouding tot het aantal berichten dat met succes is verwerkt.

## Indeling van openen {#breakdown-of-opens}

In dit rapport wordt de uitsplitsing van de openingen per besturingssysteem, apparaat en browser voor de betrokken periode weergegeven. Voor elke categorie worden twee grafieken gebruikt. De eerste toont statistieken betreffende opent op een computer en mobiele apparaten. In het tweede voorbeeld worden alleen statistieken weergegeven over het openen op mobiele apparaten.

Het aantal openingen komt overeen met het totale aantal geopende berichten. E-mails met tekstopmaak worden niet geteld. Voor meer informatie bij het Volgen opent, verwijs naar [&#x200B; het Volgen opent &#x200B;](../../reporting/using/indicator-calculation.md#tracking-opens-) sectie.

![](assets/dlv_useragent_report.png)

>[!NOTE]
>
>De namen van de browser en het besturingssysteem maken deel uit van de informatie die door de gebruikersagent van de browser is verzonden en waarnaar het bericht is geopend. Adobe Campaign brengt het type apparaat af op basis van de apparaatgegevens.
