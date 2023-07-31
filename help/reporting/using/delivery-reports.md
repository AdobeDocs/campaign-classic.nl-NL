---
product: campaign
title: Leveringsrapporten
description: Leveringsrapporten
badge-v7: label="v7" type="Informative" tooltip="Van toepassing op Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
feature: Reporting, Monitoring
exl-id: 74feb13f-0994-4a6a-ae4f-2538b07cc9c0
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '1463'
ht-degree: 2%

---

# Leveringsrapporten {#delivery-reports}



U kunt de uitvoering van leveringen bijhouden via verschillende rapporten die toegankelijk zijn vanuit het leveringsoverzicht. Pas de volgende procedure toe om rapporten weer te geven:

1. Ga naar de **[!UICONTROL Campaigns]** en klik op de knop **[!UICONTROL Delivery]** koppeling om de lijst met leveringen weer te geven.
1. Klik op de naam van de levering die u wilt weergeven om de details weer te geven.

   ![](assets/s_ncs_user_detailled_report.png)

1. Selecteer de **[!UICONTROL Summary]** en klik op de knop **[!UICONTROL Reports]** link naar de specifieke rapporten over de levering.

   ![](assets/s_ncs_user_detailled_report2.png)

   Standaard zijn de volgende rapporten beschikbaar:

   * **[!UICONTROL Delivery throughput]** : verwijs naar [Leveringsdoorvoer](../../reporting/using/global-reports.md#delivery-throughput).
   * **[!UICONTROL Sharing to social networks]** : verwijs naar [Delen naar sociale netwerken](../../reporting/using/global-reports.md#sharing-to-social-networks).
   * **[!UICONTROL Statistics on sharing activities]** : verwijs naar [Statistieken over de activiteiten voor het delen van diensten](../../reporting/using/global-reports.md#statistics-on-sharing-activities).
   * **[!UICONTROL Hot clicks]** : verwijs naar [Hot kliks](#hot-clicks).
   * **[!UICONTROL Tracking statistics]** : verwijs naar [Trackingstatistieken](#tracking-statistics)
   * **[!UICONTROL URLs and click streams]** : verwijs naar [URL&#39;s en klik op streams](#urls-and-click-streams).
   * **[!UICONTROL Tracking indicators]** : verwijs naar [Traceringsindicatoren](#tracking-indicators).
   * **[!UICONTROL Non-deliverables and bounces]** : verwijs naar [Niet-te leveren producten en bedragen](../../reporting/using/global-reports.md#non-deliverables-and-bounces).
   * **[!UICONTROL User activities]** : verwijs naar [Gebruikersactiviteiten](../../reporting/using/global-reports.md#user-activities).
   * **[!UICONTROL Delivery summary]** : verwijs naar [Overzicht van levering](#delivery-summary).
   * **[!UICONTROL Subscription tracking]** : verwijs naar [Abonnement bijhouden](../../reporting/using/global-reports.md#subscription-tracking).
   * **[!UICONTROL Delivery statistics]** : verwijs naar [Leveringsstatistieken](../../reporting/using/global-reports.md#delivery-statistics).
   * **[!UICONTROL Breakdown of opens]** : verwijs naar [Indeling van openen](../../reporting/using/global-reports.md#breakdown-of-opens).

## Trackingsindicatoren {#tracking-indicators}

Dit rapport combineert de belangrijkste indicatoren voor het volgen van het gedrag van ontvangers bij het ontvangen van de levering. Het geeft toegang tot levering en ontvangststatistieken, open en klikthrough tarieven, geproduceerde klikstromen, Web het volgen en het delen van activiteiten aan sociale netwerken.

>[!NOTE]
>
>Waarden die worden berekend op basis van berichten die worden geopend, zijn altijd schattingen, vanwege de foutmarge die is gekoppeld aan e-mails in tekstindeling. De **[!UICONTROL Distinct opens/Sum of opens for the population reached]** deze foutenmarge wordt in aanmerking genomen. Voor meer informatie over het volgen opent opent, verwijs naar [Tekstspatiëring wordt geopend](../../reporting/using/indicator-calculation.md#tracking-opens-).

![](assets/s_ncs_user_tracking_synth_report.png)

**[!UICONTROL 1. Delivery statistics]**

* **[!UICONTROL Messages to deliver]** : Totaal aantal berichten dat na leveringsanalyse moet worden bezorgd.
* **[!UICONTROL Success]** : Het aantal berichten dat is verwerkt.

**[!UICONTROL 2. Reception statistics]**

>[!NOTE]
>
>De bijbehorende percentages worden berekend op basis van het aantal berichten dat met succes is doorgestuurd.

* **[!UICONTROL Distinct opens for the population reached]** : Schatting van het aantal beoogde ontvangers dat een bericht ten minste één keer heeft geopend. Er wordt rekening gehouden met klikken op bijgehouden URL&#39;s omdat e-mails moeten worden geopend om op een koppeling te klikken.
* **[!UICONTROL Sum of opens for the population reached]** : Schatting van het totale aantal openingen door de beoogde ontvangers.
* **[!UICONTROL Clicks on opt-out link]** : Het aantal klikken op de koppeling voor het opzeggen van abonnementen.
* **[!UICONTROL Clicks on the mirror page link]** : Het aantal klikken op de koppeling naar de spiegelpagina. Om in aanmerking te worden genomen, moet de verbinding als dusdanig in de leveringstovenaar (bijgehouden URLs) worden bepaald. Zie dit [page](../../delivery/using/about-delivery-monitoring.md).
* **[!UICONTROL Estimation of forwards]** : Schatting van het aantal e-mails dat door de beoogde ontvangers is doorgestuurd. Deze waarde wordt berekend door het aantal verschillende personen en het aantal verschillende ontvangers af te trekken die in de e-mail hebben geklikt.

  >[!NOTE]
  >
  >Voor meer informatie over het verschil tussen verschillende personen en beoogde ontvangers raadpleegt u [Gerichte personen/ontvangers](../../reporting/using/indicator-calculation.md#targeted-persons---recipients).

**[!UICONTROL 3. Open and click-through rate]**

Deze waardetabel toont de uitsplitsing van leveringen, opent, klikt en ruwe reactiviteit per domein van Internet. De volgende indicatoren worden gebruikt:

* **[!UICONTROL Sent]** : Het totale aantal berichten dat op dit domein wordt verzonden.
* **[!UICONTROL Complaints]** : Het aantal berichten voor dit domein dat door de ontvanger als ongewenst is gemeld. Het tarief wordt berekend gebaseerd op het totale aantal berichten die op dit domein worden verzonden.
* **[!UICONTROL Opens]** : Aantal verschillende beoogde ontvangers voor dit domein die een bericht minstens één keer hebben geopend. Het tarief wordt berekend gebaseerd op het totale aantal berichten die op dit domein worden verzonden.
* **[!UICONTROL Clicks]** : Aantal verschillende beoogde ontvangers die minstens één keer op dezelfde levering hebben geklikt. Het tarief wordt berekend gebaseerd op het totale aantal berichten die op dit domein worden verzonden
* **[!UICONTROL Raw reactivity]** : Percentage van het aantal ontvangers dat ten minste één keer op een levering heeft geklikt in vergelijking met het aantal ontvangers dat een levering ten minste één keer heeft geopend.

>[!NOTE]
>
>De domeinnamen die in dit rapport worden weergegeven, worden gedefinieerd in de gespecificeerde lijst die op kubusniveau wordt gebruikt. Als u standaarddomeinen wilt wijzigen, toevoegen of verwijderen, bewerkt u de **[!UICONTROL Domains]** gespecificeerde lijst en wijzigt waarden en aliassen. Raadpleeg [deze sectie](../../platform/using/managing-enumerations.md) voor meer informatie. De **[!UICONTROL Others]** de categorie omvat domeinnamen die niet tot om het even welke waarde van de gespecificeerde lijst behoren.

**[!UICONTROL 4. Generated click streams]**

>[!NOTE]
>
>De bijbehorende percentages worden berekend op basis van het aantal berichten dat met succes is doorgestuurd.

* **[!UICONTROL Distinct clicks for the population reached]** : Aantal verschillende personen dat ten minste één keer op een levering heeft geklikt.
* **[!UICONTROL Cumulated clicks]** : Het totale aantal klikken door de beoogde ontvangers, exclusief koppelingen zonder abonnement en spiegel.
* **[!UICONTROL Recipient clicks]** : Aantal verschillende beoogde ontvangers die minstens één keer op dezelfde levering hebben geklikt.
* **[!UICONTROL Estimated recipient reactivity]** Verhouding tussen het aantal ontvangers dat ten minste eenmaal in een levering heeft geklikt en het geschatte aantal ontvangers dat een levering ten minste eenmaal heeft geopend. Er wordt geen rekening gehouden met de klikken op de pagina-link Weigeren en de koppeling spiegelen.

**[!UICONTROL 5. Web tracking]**

* **[!UICONTROL Visited pages]** : Aantal bezochte webpagina&#39;s na ontvangst van bericht.
* **[!UICONTROL Transactions]** : Aantal aankopen na ontvangst van bericht.
* **[!UICONTROL Total amount]** : Totaal aantal aankopen na ontvangst van bericht.
* **[!UICONTROL Average transaction amount]** : Gemiddelde aankoop door verschillende ontvangers van de levering.
* **[!UICONTROL Articles]** : Aantal artikelen dat door de ontvangers van de levering is aangeschaft.
* **[!UICONTROL Average count of articles per transaction]** : Gemiddeld aantal artikelen per aankoop door verschillende ontvangers.
* **[!UICONTROL Average amount per message]** : Gemiddelde hoeveelheid aankopen die per bericht wordt gegenereerd.

  >[!NOTE]
  >
  >Als u een bezochte pagina, transactie, hoeveelheid of artikel in aanmerking wilt nemen, moet een webtrackingtag in de bijbehorende webpagina worden ingevoegd. Webtracking-configuratie wordt weergegeven in [deze sectie](../../configuration/using/about-web-tracking.md).

**[!UICONTROL 6. Sharing activities to email and social networks]**

Deze sectie toont het aantal berichten die op elk sociaal netwerk worden gedeeld. Raadpleeg voor meer informatie hierover [Delen naar sociale netwerken](../../reporting/using/global-reports.md#sharing-to-social-networks).

## URL&#39;s en klikpaden {#urls-and-click-streams}

Dit rapport bevat de lijst met bezochte pagina&#39;s na een levering.

![](assets/s_ncs_user_url_report.png)

U kunt de inhoud van dit rapport configureren door het volgende te selecteren: het scorediagram dat moet worden weergegeven, het tijdfilter (sinds het starten van de actie, gedurende de eerste 6 uur na het starten, enz.) en de weergavemodus voor gegevens (op label, op URL, op categorie). Klik op **[!UICONTROL Refresh]** om uw selectie te bevestigen.

De volgende tarieven worden getoond in de hogere sectie van het rapport:

* **[!UICONTROL Reactivity]** : Verhouding van het aantal beoogde ontvangers dat op een levering heeft geklikt, in verhouding tot het geschatte aantal beoogde ontvangers dat een levering heeft geopend. Klikken op de opt-out-koppeling en op de spiegelpagina worden niet in aanmerking genomen.

  >[!NOTE]
  >
  >Voor meer informatie over het volgen opent opent, verwijs naar [Tekstspatiëring wordt geopend](../../reporting/using/indicator-calculation.md#tracking-opens-).

* **[!UICONTROL Distinct clicks]** : Aantal verschillende personen dat ten minste één keer heeft geklikt (exclusief koppeling zonder abonnement en spiegel) in een levering. De getoonde snelheid wordt berekend op basis van het aantal berichten dat met succes is afgeleverd.
* **[!UICONTROL Cumulated clicks]** : Totaal aantal klikken door beoogde ontvangers (exclusief koppeling zonder abonnement en spiegel). Het getoonde tarief wordt berekend gebaseerd op het aantal berichten met succes door:sturen.

**[!UICONTROL Platform average]** : Dit gemiddelde tarief, dat onder elk tarief wordt getoond (reactiviteit, verschillende kliks, en gecumuleerde kliks), wordt berekend voor leveringen die in de voorafgaande zes maanden werden verzonden. Alleen leveringen met dezelfde typologie en op hetzelfde kanaal worden in aanmerking genomen. Proefdrukken zijn uitgesloten.

De centrale tabel bevat de volgende informatie:

* **[!UICONTROL Clicks]** : Aantal gecumuleerde klikken per koppeling.
* **[!UICONTROL Clicks (in %)]** : Uitsplitsing van het aantal klikken per link in verhouding tot het totale aantal gecumuleerde klikken.

**[!UICONTROL Breakdown of clicks in time]**

Dit diagram toont de uitsplitsing van gecumuleerde klikken per dag.

## Leveringsoverzicht {#delivery-summary}

Dit rapport bevat alle belangrijke informatie over de levering.

![](assets/s_ncs_user_synth_report.png)

**[!UICONTROL Target population]**

Deze sectie heeft twee indicatoren:

* **[!UICONTROL Initial population]** : Totaal aantal ontvangers voor de levering.
* **[!UICONTROL Messages rejected by the rule]** : Het aantal adressen dat tijdens de analyse tijdens het toepassen van typologische regels wordt genegeerd: adres ontbreekt, in quarantaine geplaatst, op lijst van gewezen personen, enz. Zie voor meer informatie over typologische regels [page](../../delivery/using/steps-validating-the-delivery.md#validation-process-with-typologies).

**[!UICONTROL Causes of exclusion]**

Het middelste diagram toont de uitsplitsing per regel van berichten die tijdens de analyse worden verworpen.

**[!UICONTROL Delivery statistics]**

Dit deel omvat de volgende indicatoren:

* **[!UICONTROL Messages to be delivered]** : Totaal aantal berichten dat na leveringsanalyse moet worden bezorgd.
* **[!UICONTROL Success]** : Aantal berichten dat is verwerkt. Het bijbehorende tarief is de verhouding met het aantal te leveren berichten.
* **[!UICONTROL Errors]** : Totaal aantal fouten gecumuleerd tijdens leveringen en automatische ophoudverwerking. Het bijbehorende tarief is de verhouding met het aantal te leveren berichten.
* **[!UICONTROL New quarantines]** : Aantal adressen dat na een mislukte levering in quarantaine is geplaatst (onbekend, ongeldig domein). Het bijbehorende tarief is de verhouding met het aantal te leveren berichten.

## Hot clicks {#hot-clicks}

Dit rapport toont de berichtinhoud (HTML en/of tekst) met, op elke verbinding, het percentage klikt op verbindingen. De belemmeringen van de verpersoonlijking unsubscription verbindingen, spiegelpaginakoppelingen en aanbiedingsverbindingen worden in de totale gecumuleerde kliks in aanmerking genomen maar niet getoond in het rapport.

>[!NOTE]
>
>Als uw levering voorstellen (Interactie) bevat, verschijnt een doos in het deel boven het rapport tonend het percentage van kliks op de aanbiedingen.

![](assets/s_ncs_user_clic_report.png)

## Trackingstatistieken {#tracking-statistics}

Dit rapport bevat statistieken over openen, klikken en transacties.

![](assets/s_ncs_user_stat_report.png)

Hiermee kunt u de marketingeffecten van de levering volgen. U kunt configureren hoe waarden worden weergegeven door de tijdschaal te wijzigen (1 uur, 3 uur of 24 uur, enz.). Klik op **[!UICONTROL Refresh]** om uw selectie te bevestigen.

Dit rapport bevat een tabel met waarden en een Pareto-grafiek met de tijd die nodig is voor de levering om de maximale efficiëntie te bereiken. De volgende indicatoren worden gebruikt:

* **[!UICONTROL Opens]** : Schatting van de tijd die nodig is om een percentage van het totale aantal geopende berichten te bereiken. E-mails in tekstindeling worden niet in aanmerking genomen. Voor meer informatie over het volgen opent opent, verwijs naar [Tekstspatiëring wordt geopend](../../reporting/using/indicator-calculation.md#tracking-opens-).
* **[!UICONTROL Clicks]** : Schatting van de tijd die nodig is om een percentage van het totale aantal geregistreerde klikken te bereiken. Klikken op de opt-out-koppeling en de spiegelpagina worden niet in aanmerking genomen.
* **[!UICONTROL Transactions]** : Tijd die nodig is om een percentage van het totale aantal transacties na ontvangst van berichten te bereiken. Om een transactie in aanmerking te nemen, moet een webtrackingtag van het transactietype in de overeenkomstige Web-pagina worden opgenomen. Webtracking-configuratie wordt weergegeven in [deze sectie](../../configuration/using/about-web-tracking.md).
