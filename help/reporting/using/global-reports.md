---
product: campaign
title: Algemene rapporten
description: Algemene rapporten
badge: label="v7" type="Informative" tooltip="Alleen van toepassing op Campaign Classic v7"
feature: Reporting, Monitoring
exl-id: 6839fd7e-ecf4-4504-90a8-0207bc3991e4
source-git-commit: abaeef25b03a9699a4851786380d467bfa299c9f
workflow-type: tm+mt
source-wordcount: '2308'
ht-degree: 4%

---

# Algemene rapporten {#global-reports}



Deze rapporten hebben betrekking op de activiteit van de gegevens in de gehele database. Ga naar het **[!UICONTROL Reports]** tab.

![](assets/s_ncs_user_report_delivery_link.png)

Klik op de naam van de rapporten om deze weer te geven. De volgende rapporten zijn standaard beschikbaar:

![](assets/s_ncs_user_report_global_list.png)

>[!NOTE]
>
>In deze sectie worden alleen de rapporten weergegeven die betrekking hebben op leveringen.

* **[!UICONTROL Delivery throughput]** : verwijs naar [Leveringsdoorvoer](#delivery-throughput).
* **[!UICONTROL Browsers]** : verwijs naar [Browsers](#browsers).
* **[!UICONTROL Sharing to social networks]** : verwijs naar [Delen naar sociale netwerken](#sharing-to-social-networks).
* **[!UICONTROL Statistics on sharing activities]** : verwijs naar [Statistieken over de activiteiten voor het delen van diensten](#statistics-on-sharing-activities).
* **[!UICONTROL Operating systems]** : verwijs naar [Besturingssystemen](#operating-systems).
* **[!UICONTROL URLs and click streams]** : verwijs naar [URL&#39;s en klik op streams](../../reporting/using/delivery-reports.md#urls-and-click-streams).
* **[!UICONTROL Tracking indicators]** : verwijs naar [Traceringsindicatoren](../../reporting/using/delivery-reports.md#tracking-indicators).
* **[!UICONTROL Non-deliverables and bounces]** : verwijs naar [Niet-te leveren producten en bedragen](#non-deliverables-and-bounces).
* **[!UICONTROL User activities]** : verwijs naar [Gebruikersactiviteiten](#user-activities).
* **[!UICONTROL Subscription tracking]** : verwijs naar [Abonnement bijhouden](#subscription-tracking).
* **[!UICONTROL Delivery summary]** : verwijs naar [Overzicht van levering](../../reporting/using/delivery-reports.md#delivery-summary).
* **[!UICONTROL Delivery statistics]** : verwijs naar [Leveringsstatistieken](#delivery-statistics).
* **[!UICONTROL Breakdown of opens]** : verwijs naar [Indeling van openen](#breakdown-of-opens).

## Leveringsdoorvoer {#delivery-throughput}

Dit verslag bevat informatie over de leveringsproductie van het gehele platform voor een bepaalde periode. Om de snelheid te meten waarbij de berichten worden geleverd, zijn de criteria het aantal berichten die per uur worden verzonden en de grootte van de berichten (in beetjes per seconde). In het onderstaande voorbeeld ziet u in de eerste grafiek de geslaagde leveringen in blauw en het aantal onjuiste leveringen in oranje.

![](assets/s_ncs_user_report_toolbar.png)

U kunt de weergegeven waarden configureren door de tijdschaal te wijzigen: een weergave van 1 uur, een weergave van 3 uur, een weergave van 24 uur, enzovoort. Klik op **[!UICONTROL Refresh]** om uw selectie te bevestigen.

>[!NOTE]
>
>Als uw exemplaar op AWS wordt gehost, kunt u ook het aantal verzonden leveringen per uur controleren met het Campaign Classic [Deelvenster Beheer](https://experienceleague.adobe.com/docs/control-panel/using/sftp-management/sftp-storage-management.html). Controleer of uw versie wordt gehost op AWS door de volgende stappen te volgen op [deze pagina](https://experienceleague.adobe.com/docs/control-panel/using/faq.html?lang=nl).
>
>Het configuratiescherm is toegankelijk voor alle gebruikers met beheerdersrechten. De stappen om toegang met beheerdersrechten aan een gebruiker te verlenen worden gedetailleerd beschreven op [deze pagina](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html?lang=nl#discover-control-panel).
>
>Merk op dat uw instantie met recentste moet worden bevorderd [Gouden standaard](../../rn/using/gold-standard.md) of de [nieuwste GA-build (21.1.3)](../../rn/using/latest-release.md). Leer hoe u uw versie kunt controleren in [dit gedeelte](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

## Gebruikersactiviteiten {#user-activities}

Dit rapport toont de uitsplitsing van opent, klikt en transacties per half uur, uur of dag, in de vorm van een grafiek.

![](assets/s_ncs_user_user_report.png)

De volgende opties zijn beschikbaar:

* **[!UICONTROL Opens]** : Totaal aantal geopende berichten. E-mails in tekstindeling worden niet in aanmerking genomen. Voor meer informatie over het volgen opent opent, verwijs naar [Tekstspatiëring wordt geopend](../../reporting/using/indicator-calculation.md#tracking-opens-).
* **[!UICONTROL Clicks]** : Het totale aantal klikken op koppelingen in leveringen. Er wordt geen rekening gehouden met klikken op abonnementkoppelingen en spiegelpagina&#39;s.
* **[!UICONTROL Transactions]** : Totaal aantal transacties nadat een bericht is ontvangen. Om een transactie in aanmerking te nemen, moet een webtrackingtag van het transactietype in de overeenkomstige Web-pagina worden opgenomen. Webtracking-configuratie wordt weergegeven in [deze sectie](../../configuration/using/about-web-tracking.md).

## Niet-leverbare items en niet-bezorgingen {#non-deliverables-and-bounces}

Dit verslag geeft een overzicht van de niet-te leveren posten en een uitsplitsing van de bedragen per internetdomein.

De **[!UICONTROL Number of messages processed]** vertegenwoordigt het totale aantal berichten die door de leveringsserver worden verwerkt. Deze waarde is lager dan het aantal berichten dat moet worden afgeleverd wanneer bepaalde leveringen zijn gestopt of gepauzeerd (voordat deze door de server worden verwerkt).

![](assets/s_ncs_user_errors_report.png)

**[!UICONTROL Breakdown of errors by type]**

>[!NOTE]
>
>De fouten die in dit rapport worden weergegeven, activeren het quarantaineproces. Voor meer informatie over quarantainebeheer raadpleegt u [Quarantainebeheer](../../delivery/using/understanding-quarantine-management.md).

In het eerste deel van dit verslag wordt de uitsplitsing van niet-te leveren producten in de vorm van een tabel van waarden en een grafiek weergegeven.

Voor elk fouttype hebben we:

* het aantal foutberichten van dit type;
* het percentage berichten met dergelijke fouten in vergelijking met het totale aantal berichten met fouten;
* het percentage van foutenmeldingen van dit type vergeleken met het totale aantal verwerkte berichten.

De volgende indicatoren worden gebruikt:

* **[!UICONTROL User unknown]** : Fouttype dat tijdens de levering wordt gegenereerd om aan te geven dat het e-mailadres ongeldig is.
* **[!UICONTROL Invalid domain]** : Fouttype dat wordt gegenereerd bij het verzenden van een levering om aan te geven dat het domein van het e-mailadres onjuist is of niet bestaat.
* **[!UICONTROL Inbox full]** : Fouttype dat wordt gegenereerd na vijf leveringspogingen om aan te geven dat het postvak van de ontvanger te veel berichten bevat.
* **[!UICONTROL Account disabled]** : Fouttype dat wordt gegenereerd bij het verzenden van een levering om aan te geven dat het adres niet langer bestaat.
* **[!UICONTROL Rejected]** : Fouttype dat wordt gegenereerd wanneer een adres wordt afgewezen door de IAP (Internet Access Provider), bijvoorbeeld na toepassing van een beveiligingsregel (anti-spamsoftware).
* **[!UICONTROL Unreachable]** : Het type van fout dat in het koord van de berichtdistributie voorkomt: incident op het relais SMTP, domein tijdelijk onbereikbaar etc.
* **[!UICONTROL Not connected]** : Fouttype om aan te geven dat de mobiele telefoon van de ontvanger op het moment van verzending wordt uitgeschakeld of losgekoppeld van het netwerk.

  >[!NOTE]
  >
  >Deze indicator heeft alleen betrekking op leveringen op mobiele kanalen. Raadpleeg [deze sectie](../../delivery/using/sms-channel.md) voor meer informatie.

  U kunt elke regel van de waardetabel openen door op de knop `[+]` symbool. Voor elk fouttype kunt u de indeling van foutberichten per domein weergeven.

  ![](assets/s_ncs_user_errors_report_detail.png)

**[!UICONTROL Breakdown of errors per domain]**

In het tweede gedeelte van dit rapport wordt de uitsplitsing van fouten per internetdomein getoond in de vorm van een tabel met waarden en een grafiek.

Voor elke domeinnaam hebben we:

* het aantal berichten met fouten voor dit domein,
* het percentage berichten met fouten voor dit domein in vergelijking met het totale aantal berichten dat voor dit domein wordt verwerkt;
* het percentage foutberichten voor dit domein in vergelijking met het totale aantal foutberichten.

U kunt elke regel van de waardetabel openen door op de knop [+] symbool. Voor elk domeintype kunt u de indeling van foutberichten per fouttype weergeven.

![](assets/s_ncs_user_errors_report_detail2.png)

>[!NOTE]
>
>De domeinnamen die in dit rapport worden weergegeven, worden op kubusniveau gedefinieerd. Als u deze waarden wilt wijzigen, bewerkt u de **[!UICONTROL Delivery logs (broadlogrcp)]** kubus. Raadpleeg [deze sectie](../../reporting/using/ac-cubes.md) voor meer informatie. De **[!UICONTROL Others]** categorie omvat domeinnamen die niet tot een specifieke klasse behoren.

## Browsers {#browsers}

Dit verslag geeft een overzicht van de internetbrowsers die door de ontvangers van de levering voor de betrokken periode zijn gebruikt.

>[!NOTE]
>
>De waarden in dit rapport zijn schattingen: alleen ontvangers die op een levering hebben geklikt, worden in aanmerking genomen.

**Algemene statistieken**

De algemene statistieken over browsergebruik worden gepresenteerd in de vorm van een tabel met waarden en een grafiek.

![](assets/dlv_explorers_report.png)

De volgende indicatoren worden gebruikt:

* **[!UICONTROL Visitors]** : Het totale aantal beoogde ontvangers (per internetbrowser) dat minstens één keer op een levering heeft geklikt.
* **[!UICONTROL Pages viewed]** : Het totale aantal klikken op koppelingen in een levering (per internetbrowser) voor alle leveringen.
* **[!UICONTROL Usage rate]** : Dit percentage geeft de uitsplitsing weer van bezoekers (per internetbrowser) in verhouding tot het totale aantal bezoekers.

**Statistieken per browser**

In de lijst van globale statistische waarden, kunt u elke browser naam klikken om hun gebruiksstatistieken te bekijken.

![](assets/s_ncs_user_explorers_report2.png)

Statistieken worden gepresenteerd in de vorm van een curve, een grafiek en een tabel met waarden.

De **[!UICONTROL History]** De curve geeft de aanwezigheidsgraad van deze browser per dag aan. De frequentie is de verhouding tussen het aantal bezoekers per dag (in deze browser) en het aantal bezoekers dat wordt gemeten op de dag met de hoogste aanwezigheidsgraad.

De **[!UICONTROL Breakdown per version]** De grafiek geeft de uitsplitsing van bezoekers per versie weer ten opzichte van het totale aantal bezoekers (in deze browser).

In de waardetabel worden de volgende indicatoren gebruikt:

* **[!UICONTROL Global rate]** : Deze frequentie geeft de uitsplitsing van bezoekers per versie weer in vergelijking met het totale aantal bezoekers (in alle browsers).
* **[!UICONTROL Relative rate]** : Deze frequentie geeft de uitsplitsing van bezoekers per versie weer ten opzichte van het totale aantal bezoekers (in deze browser).

### Delen naar sociale netwerken {#sharing-to-social-networks}

Met virale marketing kunnen ontvangers informatie delen met hun contactnetwerk: ze kunnen een koppeling toevoegen aan hun profiel (Facebook, X - voorheen bekend als Twitter, enz.) of stuur een bericht naar een vriend. Elk aandeel en elke toegang tot gedeelde informatie wordt gevolgd binnen de levering. Raadpleeg voor meer informatie over het op de markt brengen van virale middelen [deze sectie](../../delivery/using/viral-and-social-marketing.md).

Dit rapport geeft de uitsplitsing weer van gedeelde en geopende berichten per sociaal netwerk (Facebook, X, enz.) en/of per e-mail.

![](assets/s_ncs_user_social_report.png)

**[!UICONTROL Email delivery statistics]**

In de statistieken van de e-maillevering, worden twee waarden getoond:

* **[!UICONTROL Number of messages to be delivered]** : Totaal aantal berichten dat tijdens leveringsanalyse wordt verwerkt.
* **[!UICONTROL Number of successful deliveries]** : Aantal berichten dat is verwerkt.

**[!UICONTROL Sharing activities and mail open statistics]**

De centrale tabel toont de statistieken over e-mailaandelen en wordt geopend.

In de **[!UICONTROL Shares]** kolom, hebben wij de volgende indicatoren:

* **[!UICONTROL No. of sharing activities]** : Het totale aantal berichten dat op elk sociaal netwerk wordt gedeeld. Deze waarde is gelijk aan het totale aantal klikken op het pictogram van de overeenkomst **[!UICONTROL Links for sharing to social networks]** verpersoonlijkingsblok.
* **[!UICONTROL Breakdown]** : Dit percentage vertegenwoordigt de uitsplitsing van de aandelen per sociaal netwerk in verhouding tot het totale aantal aandelen.
* **[!UICONTROL Sharing rate]** : Dit percentage geeft de uitsplitsing weer van de aandelen per sociaal netwerk in verhouding tot het aantal te leveren berichten.

In de **[!UICONTROL Opens]** kolom, hebben wij de volgende indicatoren:

* **[!UICONTROL No. of opens]** : Het totale aantal berichten dat is geopend door mensen aan wie het bericht is doorgestuurd (via de **[!UICONTROL Links for sharing to social networks]** verpersoonlijkingsblok). Deze waarde is gelijk aan het aantal keren dat de spiegelpagina is weergegeven. Opens door ontvangers van de levering worden niet in aanmerking genomen.
* **[!UICONTROL Breakdown]** : Dit percentage geeft de verdeling weer van de openingen per sociaal netwerk, in verhouding tot het totale aantal openingen.
* **[!UICONTROL Rate of opens]** : Dit percentage geeft de uitsplitsing weer van de beurzen per sociaal netwerk, in verhouding tot het totale aantal aandelen.

**[!UICONTROL Breakdown of sharing activities and opens]**

Deze sectie omvat twee grafieken die de indeling van de deelactiviteiten vertegenwoordigen en per sociaal netwerk worden geopend.

## Statistieken over de activiteiten voor het delen van diensten {#statistics-on-sharing-activities}

Dit rapport toont de evolutie van aandelen aan sociale netwerken (Facebook, X - voorheen bekend als Twitter, e-mail, enz.) op tijd.

Raadpleeg voor meer informatie over het op de markt brengen van virale middelen [deze sectie](../../delivery/using/viral-and-social-marketing.md).

![](assets/s_ncs_user_social_report2.png)

Statistieken worden gepresenteerd in de vorm van een tabel met waarden en een grafiek.

De volgende indicatoren worden gebruikt:

* **[!UICONTROL New contacts]** : Aantal nieuwe abonnementen na ontvangst van een bericht dat via e-mail wordt gedeeld. Deze waarde komt overeen met het aantal personen dat een bericht heeft ontvangen dat via e-mail is gedeeld en op de knop **[!UICONTROL Subscription link]** en vult het abonnementsformulier in.
* **[!UICONTROL Opens]** : Het totale aantal berichten dat is geopend door personen aan wie het bericht is overgedragen (via de **[!UICONTROL Link for sharing to social networks]** verpersoonlijkingsblok). Deze waarde is gelijk aan het aantal keren dat de spiegelpagina is weergegeven. Opens door ontvangers van de levering worden niet in aanmerking genomen.
* **[!UICONTROL Sharing activities]** : Het totale aantal berichten dat via sociale netwerken wordt gedeeld. Deze waarde komt overeen met het totale aantal klikken op het pictogram van het dialoogvenster **[!UICONTROL Links for sharing to social networks]** verpersoonlijkingsblok.

## Besturingssystemen {#operating-systems}

Dit verslag geeft een overzicht van de exploitatiesystemen die door de ontvangers van de levering voor de betrokken periode worden gebruikt.

>[!NOTE]
>
>De waarden in dit rapport zijn schattingen: alleen ontvangers die op een levering hebben geklikt, worden in aanmerking genomen.

**Algemene statistieken**

De algemene gebruiksstatistieken van besturingssystemen worden gepresenteerd in de vorm van een tabel met waarden en een grafiek.

![](assets/s_ncs_user_os_report.png)

De volgende indicatoren worden gebruikt:

* **[!UICONTROL Visitors]** : Daggemiddelde van het totale aantal beoogde ontvangers (per besturingssysteem) die ten minste eenmaal op een levering hebben geklikt.
* **[!UICONTROL Pages viewed]** : Daggemiddelde van het totale aantal klikken op leveringskoppelingen (per besturingssysteem) voor alle leveringen.
* **[!UICONTROL Rate of use]** : Dit percentage is de uitsplitsing van bezoekers (per besturingssysteem) in verhouding tot het totale aantal bezoekers.

**Statistieken per besturingssysteem**

In de lijst van globale statistiekwaarden, klik de naam van elk werkend systeem om de statistieken per werkend systeem te bekijken.

![](assets/s_ncs_user_os_report2.png)

Statistieken worden gepresenteerd in de vorm van een curve, een grafiek en een tabel met waarden.

De **[!UICONTROL History]** De curve geeft de gebruiksfrequentie van dit besturingssysteem per dag aan. Dit percentage is de verhouding tussen het aantal bezoekers per dag (op dit besturingssysteem) en het aantal bezoekers dat wordt gemeten op de dag met de hoogste aanwezigheid.

De **[!UICONTROL Breakdown by version]** De grafiek geeft de uitsplitsing van bezoekers per versie weer in verhouding tot het totale aantal bezoekers op dit besturingssysteem.

In de waardetabel worden de volgende indicatoren gebruikt:

* **[!UICONTROL Global rate]** : Dit percentage geeft de uitsplitsing van bezoekers (per versie) weer in verhouding tot het totale aantal bezoekers in de besturingssystemen.
* **[!UICONTROL Relative rate]** : Dit percentage geeft de uitsplitsing van bezoekers (per versie) weer ten opzichte van het totale aantal bezoekers voor dit besturingssysteem.

## Abonnement bijhouden {#subscription-tracking}

Met dit rapport kunt u abonnementen op informatieservices controleren. Er worden abonnementen en afkortingen weergegeven.

![](assets/s_ncs_user_services_report.png)

Het kan voor een abonnement worden getoond door te klikken **[!UICONTROL Profiles and targets > Services and subscriptions]** knooppunt van de startpagina of de verkenner. Selecteer het gewenste abonnement en klik op de knop **[!UICONTROL Reports]** tab. De **[!UICONTROL Subscriptions tracking]** rapport is standaard beschikbaar. Het laat u de abonnement en unsubscription tendensen en het loyaliteitstarief over een periode zien. U kunt de representatie van deze gegevens configureren via de vervolgkeuzelijst. Klikken **[!UICONTROL Refresh]** om de geselecteerde configuratie te bevestigen.

Zie voor meer informatie [deze pagina](../../delivery/using/managing-subscriptions.md).

De **[!UICONTROL Number subscribed to date]** geeft het totale aantal personen aan waarop momenteel is geabonneerd.

**[!UICONTROL Overall evolution of subscriptions]**

In de waardetabel worden de volgende indicatoren gebruikt:

* **[!UICONTROL Subscribers]** : Totaal aantal abonnees voor de betrokken periode.
* **[!UICONTROL Subscriptions]** : Aantal abonnementen voor de betrokken periode.
* **[!UICONTROL Unsubscriptions]** : Aantal aflossingen voor de betrokken periode.
* **[!UICONTROL Evolution]** : Aantal afmeldingen min het aantal abonnementen. Het tarief wordt berekend op basis van het totale aantal abonnees.
* **[!UICONTROL Loyalty]** : Loyalty voor abonnees voor de betrokken periode.

**[!UICONTROL Subscription evolution curves]**

Deze grafiek toont de ontwikkeling van de abonnementen en afboekingen voor de betrokken periode.

## Leveringsstatistieken {#delivery-statistics}

Dit rapport toont de uitsplitsing naar internetdomein van alle verwerkte en verzonden berichten, van harde en zachte geluiden, opent, klikt en afmeldt.

![](assets/s_ncs_user_broadcast_report.png)

De volgende indicatoren worden gebruikt:

* **[!UICONTROL Emails processed]** : Het totale aantal berichten dat door de leveringsserver wordt verwerkt.
* **[!UICONTROL Delivered]** : percentage van het aantal met succes verwerkte berichten in verhouding tot het totale aantal verwerkte berichten.
* **[!UICONTROL Hard bounces]** : percentage van het aantal &quot;harde&quot; bellen in vergelijking met het totale aantal verwerkte berichten.
* **[!UICONTROL Soft bounces]** : percentage van het aantal &quot;zachte&quot; grenzen in vergelijking met het totale aantal verwerkte berichten.

  >[!NOTE]
  >
  >Raadpleeg voor meer informatie over harde en zachte golven [Quarantainebeheer](../../delivery/using/understanding-quarantine-management.md).

* **[!UICONTROL Opens]** : percentage van het aantal beoogde ontvangers die een bericht ten minste eenmaal hebben geopend in vergelijking met het aantal berichten dat met succes is verwerkt.
* **[!UICONTROL Clicks]** : percentage van het aantal mensen die in een levering minstens eens in vergelijking met het aantal met succes verwerkte berichten klikte.
* **[!UICONTROL Unsubscription]** : percentage van het aantal klikken op een koppeling zonder abonnement in verhouding tot het aantal berichten dat met succes is verwerkt.

## Indeling van openen {#breakdown-of-opens}

In dit rapport wordt de uitsplitsing van de openingen per besturingssysteem, apparaat en browser voor de betrokken periode weergegeven. Voor elke categorie worden twee grafieken gebruikt. De eerste toont statistieken betreffende opent op een computer en mobiele apparaten. In het tweede voorbeeld worden alleen statistieken weergegeven over het openen op mobiele apparaten.

Het aantal openingen komt overeen met het totale aantal geopende berichten. E-mails met tekstopmaak worden niet geteld. Voor meer informatie over het Volgen opent, verwijs naar [Tekstspatiëring wordt geopend](../../reporting/using/indicator-calculation.md#tracking-opens-) sectie.

![](assets/dlv_useragent_report.png)

>[!NOTE]
>
>De namen van de browser en het besturingssysteem maken deel uit van de informatie die door de gebruikersagent van de browser is verzonden en waarnaar het bericht is geopend. Adobe Campaign brengt het type apparaat af op basis van de apparaatgegevens.
