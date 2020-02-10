---
title: Indicatoren maken
seo-title: Indicatoren maken
description: Indicatoren maken
seo-description: null
page-status-flag: never-activated
uuid: 3caaba6b-b6c8-4b64-b123-d7098e9ddc7a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: designing-reports-with-cubes
discoiquuid: a5fc6c78-b4fb-41fd-a072-7be4ece3c554
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 209ac4d81d2d27c264ee6b288bcb7fcb1900ffc5

---


# Indicatoren maken{#creating-indicators}

Om een kubus functioneel te maken, moet u de relevante afmetingen en de maatregelen identificeren en hen creëren in de kubus.

Voer de volgende stappen uit om een kubus te maken:

1. Selecteer de werktabel. Zie De werktabel [](#selecting-the-work-table)selecteren.
1. Definieer de afmetingen. Zie [Afmetingen](#defining-dimensions)definiëren.
1. Bepaal maatregelen. Zie [Gebouwenindicatoren](#building-indicators).
1. Maak aggregaten (optioneel). Zie [Berekenen en gebruiken van aggregaten](../../reporting/using/concepts-and-methodology.md#calculating-and-using-aggregates).

In dit voorbeeld ziet u hoe u snel een eenvoudige kubus in een rapport kunt maken om de bijbehorende maatregelen te exporteren.

De implementatiestappen worden hieronder beschreven. In de andere secties van dit hoofdstuk vindt u uitgebreide opties en beschrijvingen.

## De werktabel selecteren {#selecting-the-work-table}

Als u een kubus wilt maken, klikt u op de **[!UICONTROL New]** knop boven de lijst met kubussen.

![](assets/s_advuser_cube_create.png)

Selecteer het feitenschema, d.w.z. het schema dat de elementen bevat u wilt onderzoeken. In dit voorbeeld wordt de tabel **Ontvanger** geselecteerd.

![](assets/s_advuser_cube_wz_02.png)

Klik **[!UICONTROL Save]** om de kubus te maken: het zal op de lijst van Kubussen verschijnen en kan dan worden gevormd gebruikend de aangewezen lusjes.

Klik op de **[!UICONTROL Filter the source data...]** koppeling om de berekeningen van deze kubus toe te passen op een selectie gegevens in de database.

![](assets/s_advuser_cube_wz_03.png)

## Afmetingen definiëren {#defining-dimensions}

Dimensies vallen samen met analysegassen die voor elke kubus zijn gedefinieerd op basis van het bijbehorende feitelijke schema. Dit zijn de dimensies die in de analyse worden onderzocht, zoals tijd (jaar, maand, datum...), een classificatie van producten of contracten (familie, referentie, enz.), een bevolkingssegment (per stad, leeftijdsgroep, status, enz.).

Deze analysegassen worden gedefinieerd op het **[!UICONTROL Dimension]** tabblad Kubus.

Klik op de **[!UICONTROL Add]** knop om een nieuwe dimensie te maken en klik vervolgens in het **[!UICONTROL Expression field]** pictogram op het **[!UICONTROL Edit expression]** pictogram om het veld te selecteren dat de betrokken gegevens bevat.

![](assets/s_advuser_cube_wz_04.png)

* Selecteer eerst de **leeftijd** van de ontvanger. Voor dit gebied, kunt u het binden aan groepspagina&#39;s bepalen en informatie het lezen gemakkelijker maken. We raden u aan binden te gebruiken wanneer er meerdere afzonderlijke waarden mogelijk zijn.

   Schakel de **[!UICONTROL Enable binning]** optie in om dit te doen. Bindingsmodi worden gedetailleerd weergegeven in [Gegevensbinding](../../reporting/using/concepts-and-methodology.md#data-binning).

   ![](assets/s_advuser_cube_wz_05.png)

* Voeg een dimensie van het type **Datum** toe. Hier willen we datums weergeven waarop het ontvangende profiel is gemaakt

   Klik hiertoe op het **[!UICONTROL Add]** veld in de tabel met ontvangers **[!UICONTROL Creation date]** en selecteer dit.

   ![](assets/s_advuser_cube_wz_06.png)

   Het is mogelijk om de modus voor datumweergave te selecteren. Selecteer hiervoor de hiërarchie die u wilt gebruiken en de niveaus die u wilt genereren:

   ![](assets/s_advuser_cube_wz_07.png)

   In ons voorbeeld willen we alleen jaren, maanden en dagen weergeven omdat het niet mogelijk is om met weken en semesters/maanden tegelijk te werken: deze niveaus zijn niet compatibel .

* Een andere dimensie maken voor het analyseren van gegevens ten opzichte van de stad van de ontvanger

   Om dit te doen, voeg een nieuwe dimensie toe en selecteer de stad in de **[!UICONTROL Location]** knoop van het ontvankelijke schema.

   ![](assets/s_advuser_cube_wz_08.png)

   U kunt het binden toelaten om informatie het lezen gemakkelijker te maken en de waarden aan een opsomming te verbinden.

   ![](assets/s_advuser_cube_wz_09.png)

   Selecteer de opsomming in de vervolgkeuzelijst

   ![](assets/s_advuser_cube_wz_10.png)

   Alleen de waarden in de opsomming worden weergegeven. De overige worden gegroepeerd onder het label dat in het **[!UICONTROL Label of the other values]** veld is gedefinieerd.

   Raadpleeg [Dynamisch beheren van bins](../../reporting/using/concepts-and-methodology.md#dynamically-managing-bins)voor meer informatie hierover.

## Bouwindicatoren {#building-indicators}

Wanneer de afmetingen zijn gedefinieerd, moet u een berekeningsmodus opgeven voor de waarden die in de cellen moeten worden weergegeven. Hiertoe maakt u de overeenkomende indicatoren op het **[!UICONTROL Measures]** tabblad: zoveel maatregelen te treffen als er kolommen in het rapport staan die de kubus zullen gebruiken.

Hiervoor voert u de volgende stappen uit:

1. Klik op de **[!UICONTROL Add]** knop.
1. Selecteer het type maatregel en de formule die u wilt toepassen. Hier willen we het aantal vrouwen bij de ontvangers tellen.

   Onze maatregel is gebaseerd op het feitenschema en gebruikt de **[!UICONTROL Count]** exploitant.

   ![](assets/s_advuser_cube_wz_11.png)

   Met de **[!UICONTROL Filter the measure data...]** koppeling kunt u alleen vrouwen selecteren. Voor meer informatie over het bepalen van maatregelen en de beschikbare opties, verwijs naar het [Definiëren van maatregelen](../../reporting/using/concepts-and-methodology.md#defining-measures).

   ![](assets/s_advuser_cube_wz_12.png)

1. Voer het label van de maatregel in en sla deze op.

   ![](assets/s_advuser_cube_wz_13.png)

1. Sla de kubus op.

## Een rapport maken op basis van een kubus {#creating-a-report-based-on-a-cube}

Zodra de kubus wordt gevormd, kan het als malplaatje worden gebruikt voor het creëren van een nieuw rapport.

Dit doet u als volgt:

1. Klik op de **[!UICONTROL Create]** knop van het **[!UICONTROL Reports]** universum en selecteer de kubus die u zojuist hebt gemaakt.

   ![](assets/s_advuser_cube_wz_14.png)

1. Klik op de **[!UICONTROL Create]** knop ter bevestiging: dit zal u aan de rapportconfiguratie en het bekijken pagina brengen.

   Standaard worden de eerste twee beschikbare afmetingen aangeboden in lijnen en kolommen, maar er wordt geen waarde weergegeven in de tabel. Klik op het hoofdpictogram om de tabel te genereren:

   ![](assets/s_advuser_cube_wz_15.png)

1. U kunt de assen van de dimensie veranderen, hen schrappen, nieuwe maatregelen toevoegen, etc. Hier worden mogelijke bewerkingen beschreven: Kubussen [gebruiken om gegevens](../../reporting/using/using-cubes-to-explore-data.md)te verkennen.

   Gebruik hiervoor de juiste pictogrammen.

   ![](assets/s_advuser_cube_wz_16.png)

