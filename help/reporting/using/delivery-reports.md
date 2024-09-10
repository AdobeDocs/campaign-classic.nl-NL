---
product: campaign
title: Leveringsrapporten
description: Leveringsrapporten
badge-v8: label="Ook van toepassing op v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
feature: Reporting, Monitoring
exl-id: 74feb13f-0994-4a6a-ae4f-2538b07cc9c0
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '1461'
ht-degree: 1%

---

# Leveringsrapporten {#delivery-reports}



U kunt de uitvoering van leveringen bijhouden via verschillende rapporten die toegankelijk zijn vanuit het leveringsoverzicht. Pas de volgende procedure toe om rapporten weer te geven:

1. Ga naar het tabblad **[!UICONTROL Campaigns]** en klik op de koppeling **[!UICONTROL Delivery]** om de lijst met leveringen weer te geven.
1. Klik op de naam van de levering die u wilt weergeven om de details weer te geven.

   ![](assets/s_ncs_user_detailled_report.png)

1. Selecteer het tabblad **[!UICONTROL Summary]** en klik op de koppeling **[!UICONTROL Reports]** om de specifieke rapporten voor de levering te openen.

   ![](assets/s_ncs_user_detailled_report2.png)

   Standaard zijn de volgende rapporten beschikbaar:

   * **[!UICONTROL Delivery throughput]** : verwijs naar [ productie van de Levering ](../../reporting/using/global-reports.md#delivery-throughput).
   * **[!UICONTROL Sharing to social networks]** : verwijs naar [ het Delen aan sociale netwerken ](../../reporting/using/global-reports.md#sharing-to-social-networks).
   * **[!UICONTROL Statistics on sharing activities]** : verwijs naar [ Statistieken over het delen van activiteiten ](../../reporting/using/global-reports.md#statistics-on-sharing-activities).
   * **[!UICONTROL Hot clicks]** : verwijs naar [ Hete kliks ](#hot-clicks).
   * **[!UICONTROL Tracking statistics]** : verwijs naar [ het Volgen statistieken ](#tracking-statistics)
   * **[!UICONTROL URLs and click streams]** : verwijs naar [ URLs en klik stromen ](#urls-and-click-streams).
   * **[!UICONTROL Tracking indicators]** : verwijs naar [ het Volgen indicatoren ](#tracking-indicators).
   * **[!UICONTROL Non-deliverables and bounces]** : verwijs naar [ Niet-te leveren punten en stuitingen ](../../reporting/using/global-reports.md#non-deliverables-and-bounces).
   * **[!UICONTROL User activities]** : verwijs naar [ activiteiten van de Gebruiker ](../../reporting/using/global-reports.md#user-activities).
   * **[!UICONTROL Delivery summary]** : verwijs naar [ Overzicht van de Levering ](#delivery-summary).
   * **[!UICONTROL Subscription tracking]** : verwijs naar [ het volgen van het Abonnement ](../../reporting/using/global-reports.md#subscription-tracking).
   * **[!UICONTROL Delivery statistics]** : verwijs naar [ statistieken van de Levering ](../../reporting/using/global-reports.md#delivery-statistics).
   * **[!UICONTROL Breakdown of opens]** : verwijs naar [ Uitsplitsing van opent ](../../reporting/using/global-reports.md#breakdown-of-opens).

## Trackingsindicatoren {#tracking-indicators}

Dit rapport combineert de belangrijkste indicatoren voor het volgen van het gedrag van ontvangers bij het ontvangen van de levering. Het geeft toegang tot levering en ontvangststatistieken, open en klikthrough tarieven, geproduceerde klikstromen, Web het volgen en het delen van activiteiten aan sociale netwerken.

>[!NOTE]
>
>Waarden die worden berekend op basis van berichten die worden geopend, zijn altijd schattingen, vanwege de foutmarge die is gekoppeld aan e-mails in tekstindeling. In de **[!UICONTROL Distinct opens/Sum of opens for the population reached]** -indicatoren wordt rekening gehouden met deze foutmarge. Voor meer informatie bij het volgen opent, verwijs naar [ het Volgen opent ](../../reporting/using/indicator-calculation.md#tracking-opens-).

![](assets/s_ncs_user_tracking_synth_report.png)

**[!UICONTROL 1. Delivery statistics]**

* **[!UICONTROL Messages to deliver]** : Het totale aantal berichten dat na leveringsanalyse moet worden geleverd.
* **[!UICONTROL Success]** : aantal berichten dat correct is verwerkt.

**[!UICONTROL 2. Reception statistics]**

>[!NOTE]
>
>De bijbehorende percentages worden berekend op basis van het aantal berichten dat met succes is doorgestuurd.

* **[!UICONTROL Distinct opens for the population reached]** : Schatting van het aantal ontvangers aan wie een bericht is gericht dat minstens één keer is geopend. Er wordt rekening gehouden met klikken op bijgehouden URL&#39;s omdat e-mails moeten worden geopend om op een koppeling te klikken.
* **[!UICONTROL Sum of opens for the population reached]** : Schatting van het totale aantal dat door beoogde ontvangers wordt geopend.
* **[!UICONTROL Clicks on opt-out link]** : Het aantal klikken op de koppeling voor het opzeggen van abonnementen.
* **[!UICONTROL Clicks on the mirror page link]** : Het aantal klikken op de koppeling naar de spiegelpagina. Om in aanmerking te worden genomen, moet de verbinding als dusdanig in de leveringsmedewerker (bijgehouden URLs) worden bepaald. Verwijs naar deze [ pagina ](../../delivery/using/about-delivery-monitoring.md).
* **[!UICONTROL Estimation of forwards]** : schatting van het aantal e-mails dat door de beoogde ontvangers is doorgestuurd. Deze waarde wordt berekend door het aantal verschillende personen en het aantal verschillende ontvangers af te trekken die in de e-mail hebben geklikt.

  >[!NOTE]
  >
  >Voor meer informatie over het verschil tussen verschillende mensen en gerichte ontvangers, verwijs naar [ Gerichte personen/ontvangers ](../../reporting/using/indicator-calculation.md#targeted-persons---recipients).

**[!UICONTROL 3. Open and click-through rate]**

Deze waardetabel toont de uitsplitsing van leveringen, opent, klikt en ruwe reactiviteit per domein van Internet. De volgende indicatoren worden gebruikt:

* **[!UICONTROL Sent]** : Het totale aantal berichten dat op dit domein wordt verzonden.
* **[!UICONTROL Complaints]** : aantal berichten voor dit domein dat door de ontvanger als ongewenst is gerapporteerd. Het tarief wordt berekend gebaseerd op het totale aantal berichten die op dit domein worden verzonden.
* **[!UICONTROL Opens]** : aantal verschillende beoogde ontvangers voor dit domein die een bericht minstens één keer hebben geopend. Het tarief wordt berekend gebaseerd op het totale aantal berichten die op dit domein worden verzonden.
* **[!UICONTROL Clicks]** : aantal verschillende beoogde ontvangers die minstens één keer in dezelfde levering hebben geklikt. Het tarief wordt berekend gebaseerd op het totale aantal berichten die op dit domein worden verzonden
* **[!UICONTROL Raw reactivity]** : percentage van het aantal ontvangers dat ten minste één keer op een levering heeft geklikt in vergelijking met het aantal ontvangers dat een levering ten minste één keer heeft geopend.

>[!NOTE]
>
>De domeinnamen die in dit rapport worden weergegeven, worden gedefinieerd in de gespecificeerde lijst die op kubusniveau wordt gebruikt. Als u standaarddomeinen wilt wijzigen, toevoegen of verwijderen, bewerkt u de **[!UICONTROL Domains]** gespecificeerde lijst en wijzigt u waarden en aliassen. Voor meer op dit, verwijs naar [ deze sectie ](../../platform/using/managing-enumerations.md). De categorie **[!UICONTROL Others]** bevat domeinnamen die niet tot een waarde in de opgegeven lijst behoren.

**[!UICONTROL 4. Generated click streams]**

>[!NOTE]
>
>De bijbehorende percentages worden berekend op basis van het aantal berichten dat met succes is doorgestuurd.

* **[!UICONTROL Distinct clicks for the population reached]** : aantal verschillende personen dat ten minste één keer in een levering heeft geklikt.
* **[!UICONTROL Cumulated clicks]** : Het totale aantal klikken van beoogde ontvangers, exclusief koppelingen zonder abonnement en spiegel.
* **[!UICONTROL Recipient clicks]** : aantal verschillende beoogde ontvangers die minstens één keer in dezelfde levering hebben geklikt.
* **[!UICONTROL Estimated recipient reactivity]** : verhouding tussen het aantal ontvangers dat ten minste één keer in een levering heeft geklikt en het geschatte aantal ontvangers dat een levering ten minste één keer heeft geopend. Er wordt geen rekening gehouden met de klikken op de pagina-link Weigeren en de koppeling spiegelen.

**[!UICONTROL 5. Web tracking]**

* **[!UICONTROL Visited pages]** : aantal bezochte webpagina&#39;s na berichtontvangst.
* **[!UICONTROL Transactions]** : aantal aankopen na ontvangst van bericht.
* **[!UICONTROL Total amount]** : Totale hoeveelheid aankopen na ontvangst van bericht.
* **[!UICONTROL Average transaction amount]** : gemiddelde aanschaf door verschillende ontvangers.
* **[!UICONTROL Articles]** : aantal artikelen dat is aangeschaft door de ontvangers van de levering.
* **[!UICONTROL Average count of articles per transaction]** : gemiddeld aantal items per aankoop dat door verschillende ontvangers is gemaakt.
* **[!UICONTROL Average amount per message]** : Gemiddelde hoeveelheid aankopen die per bericht wordt gegenereerd.

  >[!NOTE]
  >
  >Als u een bezochte pagina, transactie, hoeveelheid of artikel in aanmerking wilt nemen, moet een webtrackingtag in de bijbehorende webpagina worden ingevoegd. Webvolgende configuratie wordt voorgesteld in [ deze sectie ](../../configuration/using/about-web-tracking.md).

**[!UICONTROL 6. Sharing activities to email and social networks]**

Deze sectie toont het aantal berichten die op elk sociaal netwerk worden gedeeld. Voor meer op dit, verwijs naar [ het Delen aan sociale netwerken ](../../reporting/using/global-reports.md#sharing-to-social-networks).

## URL&#39;s en klikpaden {#urls-and-click-streams}

Dit rapport bevat de lijst met bezochte pagina&#39;s na een levering.

![](assets/s_ncs_user_url_report.png)

U kunt de inhoud van dit rapport configureren door het volgende te selecteren: het scorediagram dat moet worden weergegeven, het tijdfilter (sinds het starten van de actie, gedurende de eerste 6 uur na het starten, enz.) en de weergavemodus voor gegevens (op label, op URL, op categorie). Klik op **[!UICONTROL Refresh]** om uw selectie te bevestigen.

De volgende tarieven worden getoond in de hogere sectie van het rapport:

* **[!UICONTROL Reactivity]** : Verhouding van het aantal beoogde ontvangers dat op een levering heeft geklikt, in verhouding tot het geschatte aantal beoogde ontvangers dat een levering heeft geopend. Klikken op de opt-out-koppeling en op de spiegelpagina worden niet in aanmerking genomen.

  >[!NOTE]
  >
  >Voor meer informatie bij het volgen opent, verwijs naar [ het Volgen opent ](../../reporting/using/indicator-calculation.md#tracking-opens-).

* **[!UICONTROL Distinct clicks]** : Aantal verschillende personen dat ten minste één keer heeft geklikt (exclusief koppeling zonder abonnement en spiegel) in een levering. De getoonde snelheid wordt berekend op basis van het aantal berichten dat met succes is afgeleverd.
* **[!UICONTROL Cumulated clicks]** : Het totale aantal klikken door de beoogde ontvangers (met uitzondering van de koppeling zonder abonnement en de spiegel). Het getoonde tarief wordt berekend gebaseerd op het aantal berichten met succes door:sturen.

**[!UICONTROL Platform average]** : Dit gemiddelde tarief, dat onder elk tarief wordt getoond (reactiviteit, verschillende kliks, en gecumuleerde kliks), wordt berekend voor leveringen die over de voorafgaande zes maanden worden verzonden. Alleen leveringen met dezelfde typologie en op hetzelfde kanaal worden in aanmerking genomen. Proefdrukken zijn uitgesloten.

De centrale tabel bevat de volgende informatie:

* **[!UICONTROL Clicks]** : aantal gecumuleerde klikken per koppeling.
* **[!UICONTROL Clicks (in %)]** : Uitsplitsing van het aantal klikken per koppeling, in verhouding tot het totale aantal gecumuleerde klikken.

**[!UICONTROL Breakdown of clicks in time]**

Dit diagram toont de uitsplitsing van gecumuleerde klikken per dag.

## Leveringsoverzicht {#delivery-summary}

Dit rapport bevat alle belangrijke informatie over de levering.

![](assets/s_ncs_user_synth_report.png)

**[!UICONTROL Target population]**

Deze sectie heeft twee indicatoren:

* **[!UICONTROL Initial population]** : Het totale aantal ontvangers dat de levering als doel heeft.
* **[!UICONTROL Messages rejected by the rule]** : Het aantal adressen dat tijdens de analyse wordt genegeerd wanneer het toepassen van typologische regels: adres ontbreekt, in quarantaine geplaatst, op lijst van gewezen personen, enz. Voor meer informatie over typologische regels, verwijs naar deze [ pagina ](../../delivery/using/steps-validating-the-delivery.md#validation-process-with-typologies).

**[!UICONTROL Causes of exclusion]**

Het middelste diagram toont de uitsplitsing per regel van berichten die tijdens de analyse worden verworpen.

**[!UICONTROL Delivery statistics]**

Dit deel omvat de volgende indicatoren:

* **[!UICONTROL Messages to be delivered]** : Het totale aantal berichten dat na leveringsanalyse moet worden geleverd.
* **[!UICONTROL Success]** : aantal berichten dat is verwerkt. Het bijbehorende tarief is de verhouding met het aantal te leveren berichten.
* **[!UICONTROL Errors]** : Totaal aantal fouten gecumuleerd tijdens leveringen en automatische oplaadbewerkingen. Het bijbehorende tarief is de verhouding met het aantal te leveren berichten.
* **[!UICONTROL New quarantines]** : aantal adressen dat in quarantaine wordt geplaatst na een mislukte levering (onbekend gebruiker, ongeldig domein). Het bijbehorende tarief is de verhouding met het aantal te leveren berichten.

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

* **[!UICONTROL Opens]** : Schatting van de tijd die nodig is om een percentage van het totale aantal geopende berichten te bereiken. E-mails in tekstindeling worden niet in aanmerking genomen. Voor meer informatie bij het volgen opent, verwijs naar [ het Volgen opent ](../../reporting/using/indicator-calculation.md#tracking-opens-).
* **[!UICONTROL Clicks]** : Schatting van de tijd die nodig is om een percentage van het totale aantal geregistreerde klikken te bereiken. Klikken op de opt-out-koppeling en de spiegelpagina worden niet in aanmerking genomen.
* **[!UICONTROL Transactions]** : tijd vereist om een percentage van het totale aantal transacties na berichtontvangst te bereiken. Om een transactie in aanmerking te nemen, moet een webtrackingtag van het transactietype in de overeenkomstige Web-pagina worden opgenomen. Webvolgende configuratie wordt voorgesteld in [ deze sectie ](../../configuration/using/about-web-tracking.md).
