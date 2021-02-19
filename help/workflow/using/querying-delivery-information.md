---
solution: Campaign Classic
product: campaign
title: Query’s uitvoeren op leveringsgegevens
description: Leer hoe u leveringsinformatie kunt opvragen
audience: workflow
content-type: reference
topic-tags: use-cases
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1241'
ht-degree: 1%

---


# Query’s uitvoeren op leveringsgegevens {#querying-delivery-information}

## Aantal klikken voor een specifieke levering {#number-of-clicks-for-a-specific-delivery}

In dit voorbeeld, kijken wij terug het aantal klikken voor een specifieke levering. Deze kliks worden geregistreerd dankzij ontvankelijke die logboeken volgen over een bepaalde periode worden genomen. De ontvanger wordt geïdentificeerd via zijn e-mailadres. Deze query gebruikt de tabel **[!UICONTROL Recipient tracking logs]**.

* Welke tabel moet worden geselecteerd?

   De tabel voor bijhouden van het logboek van ontvangers (**[!UICONTROL nms:trackingLogRcp]**)

* Velden die moeten worden geselecteerd voor uitvoerkolommen?

   Primaire sleutel (met aantal) en E-mail

* Op basis van welke criteria wordt de informatie gefilterd?

   Een specifieke periode en een element van het leveringsetiket

Voer de volgende stappen uit om dit voorbeeld uit te voeren:

1. Open **[!UICONTROL Generic query editor]** en selecteer het **[!UICONTROL Recipient tracking logs]** schema.

   ![](assets/query_editor_tracklog_05.png)

1. In het venster **[!UICONTROL Data to extract]**, willen wij een aggregaat tot stand brengen om informatie te verzamelen. Hiervoor voegt u de primaire sleutel toe (boven het hoofdelement **[!UICONTROL Recipient tracking logs]**): Het bijhouden van het aantal logbestanden wordt uitgevoerd in dit **[!UICONTROL Primary key]** veld. De bewerkte expressie zal **[!UICONTROL x=count(primary key)]** zijn. De som van de verschillende trackinglogboeken wordt aan één e-mailadres gekoppeld.

   Dit doet u als volgt:

   * Klik op het pictogram **[!UICONTROL Add]** rechts van het veld **[!UICONTROL Output columns]**. Selecteer in het venster **[!UICONTROL Formula type]** de optie **[!UICONTROL Edit the formula using an expression]** en klik op **[!UICONTROL Next]**. Klik in het venster **[!UICONTROL Field to select]** op **[!UICONTROL Advanced selection]**.

      ![](assets/query_editor_tracklog_06.png)

   * Voer in het venster **[!UICONTROL Formula type]** een proces uit op de statistische functie. Dit proces zal een primaire zeer belangrijke telling zijn.

      Selecteer **[!UICONTROL Process on an aggregate function]** in **[!UICONTROL Aggregate]** sectie en klik **[!UICONTROL Count]**.

      ![](assets/query_editor_nveau_18.png)

      Klik op **[!UICONTROL Next]**.

   * Selecteer het veld **[!UICONTROL Primary key (@id)]**. De **[!UICONTROL count (primary key)]** outputkolom wordt gevormd.

      ![](assets/query_editor_nveau_19.png)

1. Selecteer het andere veld dat in de uitvoerkolom moet worden weergegeven. Open in de kolom **[!UICONTROL Available fields]** het knooppunt **[!UICONTROL Recipient]** en kies **[!UICONTROL Email]**. Schakel het vakje **[!UICONTROL Group]** naar **[!UICONTROL Yes]** in om de volgende logbestanden te groeperen op e-mailadres: deze groep verbindt elk logboek aan zijn ontvanger.

   ![](assets/query_editor_nveau_20.png)

1. Vorm kolomsortering zodat de actiefste ontvangers (met de meeste het volgen logboeken) eerst worden getoond. Controleer **[!UICONTROL Yes]** in de **[!UICONTROL Descending sort]** kolom.

   ![](assets/query_editor_nveau_64.png)

1. Vervolgens filtert u de logboeken die u interesseert, dat wil zeggen de logboeken die jonger zijn dan twee weken en die betrekking hebben op leveranties.

   Dit doet u als volgt:

   * Gegevensfiltering configureren. Selecteer **[!UICONTROL Filter conditions]** en klik op **[!UICONTROL Next]** om dit te doen.

      ![](assets/query_editor_nveau_22.png)

   * Herstel het volgen logboeken over een bepaalde periode voor een specifieke levering. Er zijn drie filtervoorwaarden nodig: twee datumvoorwaarden om de zoekperiode in te stellen tussen twee weken vóór de huidige datum en de dag vóór de huidige datum; en een andere voorwaarde om de zoekopdracht te beperken tot een bepaalde levering.

      Configureer in het venster **[!UICONTROL Target element]** de datum vanaf wanneer er rekening wordt gehouden met trackinglogboeken. Klik op **[!UICONTROL Add]**. Er wordt een voorwaardelijn weergegeven. Bewerk de kolom **[!UICONTROL Expression]** door op de functie **[!UICONTROL Edit expression]** te klikken. Kies **[!UICONTROL Date (@logDate)]** in het venster **[!UICONTROL Field to select]**.

      ![](assets/query_editor_nveau_23.png)

      Selecteer de operator **[!UICONTROL greater than]**. Klik in de kolom **[!UICONTROL Value]** op **[!UICONTROL Edit expression]** en selecteer **[!UICONTROL Process on dates]** in het venster **[!UICONTROL Formula type]**. Voer in **[!UICONTROL Current date minus n days]** ten slotte &quot;15&quot; in.

      Klik op **[!UICONTROL Finish]**.

      ![](assets/query_editor_nveau_24.png)

   * Als u de einddatum van het zoeken van het trackinglogboek wilt selecteren, maakt u een tweede voorwaarde door op **[!UICONTROL Add]** te klikken. Kies **[!UICONTROL Date (@logDate)]** nogmaals in de kolom **[!UICONTROL Expression]**.

      Selecteer de operator **[!UICONTROL less than]**. Klik in de kolom **[!UICONTROL Value]** op **[!UICONTROL Edit expression]**. Ga voor datumverwerking naar het venster **[!UICONTROL Formula type]** en voer &quot;1&quot; in **[!UICONTROL Current date minus n days]** in.

      Klik op **[!UICONTROL Finish]**.

      ![](assets/query_editor_nveau_65.png)

      Nu willen wij de derde filtervoorwaarde, d.w.z. het leveringsetiket vormen dat onze vraag betrekking heeft.

   * Klik op de functie **[!UICONTROL Add]** om een andere filtervoorwaarde te maken. Klik in de kolom **[!UICONTROL Expression]** op **[!UICONTROL Edit expression]**. Kies in het venster **[!UICONTROL Field to select]** de optie **[!UICONTROL Label]** in het knooppunt **[!UICONTROL Delivery]**.

      Klik op **[!UICONTROL Finish]**.

      ![](assets/query_editor_nveau_66.png)

      Zoek naar een levering die het woord &quot;verkoop&quot;bevat. Aangezien u niet zijn nauwkeurige etiket herinnert, kunt u **[!UICONTROL contains]** exploitant kiezen en &quot;verkoop&quot;in **[!UICONTROL Value]** kolom ingaan.

      ![](assets/query_editor_nveau_25.png)

1. Klik **[!UICONTROL Next]** tot u aan het **[!UICONTROL Data preview]** venster krijgt: hier is geen opmaak nodig .
1. Klik in het venster **[!UICONTROL Data preview]** op **[!UICONTROL Start the preview of the data]** om het aantal trackinglogboeken voor elke ontvanger van de levering weer te geven.

   Het resultaat wordt in aflopende volgorde weergegeven.

   ![](assets/query_editor_tracklog_04.png)

   Het hoogste aantal logboeken voor een gebruiker is 6 voor deze levering. Vijf verschillende gebruikers hebben het bezorgingsbericht geopend of op een van de koppelingen in het e-mailbericht geklikt.

## Ontvangers die geen levering {#recipients-who-did-not-open-any-delivery} hebben geopend

In dit voorbeeld willen we ontvangers filteren die de afgelopen 7 dagen geen e-mail hebben geopend.

U kunt dit voorbeeld maken door de volgende stappen toe te passen:

1. Sleep een **[!UICONTROL Query]** activiteit in een werkstroom en open de activiteit.
1. Klik op **[!UICONTROL Edit query]** en stel de doel- en filterafmetingen in op **[!UICONTROL Recipients]**.

   ![](assets/query_recipients_1.png)

1. Selecteer **[!UICONTROL Filtering conditions]** en klik dan **[!UICONTROL Next]**.
1. Klik op de knop **[!UICONTROL Add]** en selecteer **[!UICONTROL Tracking logs]**.
1. Stel de **[!UICONTROL Operator]** van de expressie **[!UICONTROL Tracking logs]** in op **[!UICONTROL Do not exist such as]**.

   ![](assets/query_open_1.png)

1. Voeg nog een expressie toe. Selecteer **[!UICONTROL Type]** in **[!UICONTROL URL]** categorie.
1. Stel vervolgens **[!UICONTROL Operator]** in op **[!UICONTROL equal to]** en **[!UICONTROL Value]** op **[!UICONTROL Open]**.

   ![](assets/query_open_2.png)

1. Voeg nog een expressie toe en selecteer **[!UICONTROL Date]**. **[!UICONTROL Operator]** moet worden ingesteld op  **[!UICONTROL on or after]**.

   ![](assets/query_open_3.png)

1. Als u de waarde van 7 dagen wilt instellen, klikt u op de knop **[!UICONTROL Edit expression]** in het veld **[!UICONTROL Value]**.
1. Selecteer in de categorie **[!UICONTROL Function]** **[!UICONTROL Current date minus n days]** en voeg het aantal dagen toe dat u als doel wilt instellen. Hier willen we ons richten op de laatste 7 dagen.

   ![](assets/query_open_4.png)

De uitgaande overgang bevat ontvangers die de afgelopen 7 dagen geen e-mail hebben geopend.

Als u daarentegen ontvangers wilt filteren die ten minste één e-mail hebben geopend, moet uw query er als volgt uitzien. Houd er rekening mee dat in dit geval de **[!UICONTROL Filtering dimension]** moet worden ingesteld op **[!UICONTROL Tracking logs (Recipients)]**.

![](assets/query_open_5.png)

## Ontvangers die een levering {#recipients-who-have-opened-a-delivery} hebben geopend

In het volgende voorbeeld ziet u hoe u zich kunt richten op profielen die de levering in de afgelopen twee weken hebben geopend:

1. Als u profielen wilt aanwijzen die een levering hebben geopend, moet u trackinglogboeken gebruiken. ze worden opgeslagen in een gekoppelde tabel: begin door deze lijst in de drop-down lijst van het **[!UICONTROL Filtering dimension]** gebied, zoals hieronder getoond te selecteren:

   ![](assets/s_advuser_query_sample1.0.png)

1. Voor filtervoorwaarden klikt u op het pictogram **[!UICONTROL Edit expression]** van de criteria die worden weergegeven in de subboomstructuur van de trackinglogboeken. Selecteer het veld **[!UICONTROL Date]**.

   ![](assets/s_advuser_query_sample1.1.png)

   Klik **[!UICONTROL Finish]** om de selectie te bevestigen.

   Selecteer de operator **[!UICONTROL Greater than]** om alleen de traceringslogboeken van minder dan twee weken oud te herstellen.

   ![](assets/s_advuser_query_sample1.4.png)

   Klik vervolgens op het pictogram **[!UICONTROL Edit expression]** in de kolom **[!UICONTROL Value]** om de toe te passen berekeningsformule te definiëren. Selecteer de formule **[!UICONTROL Current date minus n days]** en typ 15 in het verwante veld.

   ![](assets/s_advuser_query_sample1.5.png)

   Klik op de knop **[!UICONTROL Finish]** van het formulevenster. Klik in het filtervenster op het tabblad **[!UICONTROL Preview]** om het aanwijzen van criteria te controleren.

   ![](assets/s_advuser_query_sample1.6.png)

## Gedrag van ontvangers filteren na levering {#filtering-recipients--behavior-folllowing-a-delivery}

In een werkstroom kunt u met de vakken **[!UICONTROL Query]** en **[!UICONTROL Split]** een gedrag na een vorige levering selecteren. Deze selectie wordt uitgevoerd via het filter **[!UICONTROL Delivery recipient]**.

* Doel van het voorbeeld

   In een leveringswerkstroom zijn er verschillende manieren om een eerste e-mailcommunicatie te volgen. Bij dit type bewerking wordt het tekstvak **[!UICONTROL Split]** gebruikt.

* Context

   Er wordt een aanbod voor de zomersport verzonden. Vier dagen na de levering worden twee andere leveringen verzonden. Een daarvan is &quot;watersportaanbod&quot;, de andere is een follow-up van de eerste &quot;Zomersportaanbieding&quot;.

   De levering &quot;Watersportaanbod&quot; wordt verzonden naar ontvangers die bij de eerste levering op de link &quot;Watersport&quot; hebben geklikt. Deze kliks tonen aan dat de ontvanger in het onderwerp geinteresseerd is. Het heeft zin om ze naar soortgelijke aanbiedingen te sturen. Ontvangers die niet op het zomersportaanbod hebben geklikt, krijgen echter weer dezelfde inhoud.

De volgende stappen tonen u hoe te om **[!UICONTROL Split]** doos te vormen door twee verschillende gedrag te integreren:

1. Plaats het tekstvak **[!UICONTROL Split]** in de workflow. Deze doos zal de ontvangers van de eerste levering in de volgende twee leveringen verdelen. De onderbreking komt voor gebaseerd op de het filtreren voorwaarden verbonden aan ontvankelijk gedrag tijdens de eerste levering.

   ![](assets/query_editor_ex_09.png)

1. Open het tekstvak **[!UICONTROL Split]**. Voer op het tabblad **[!UICONTROL General]** een label in: **Splitsen op basis van bijvoorbeeld gedrag**.

   ![](assets/query_editor_ex_04.png)

1. Definieer op het tabblad **[!UICONTROL Subsets]** de eerste gesplitste vertakking. Voer bijvoorbeeld het label **Kliked** voor deze vertakking in.
1. Selecteer de optie **[!UICONTROL Add a filtering condition on the incoming population]**. Klik op **[!UICONTROL Edit]**.
1. Dubbelklik in het venster **[!UICONTROL Targeting and filtering dimension]** op het filter **[!UICONTROL Recipients of a delivery]**.

   ![](assets/query_editor_ex_05.png)

1. Selecteer in het venster **[!UICONTROL Target element]** het gedrag dat u op deze vertakking wilt toepassen: **[!UICONTROL Recipients having clicked (email)]**.

   Selecteer hieronder de optie **[!UICONTROL Delivery specified by the transition]**. Deze functionaliteit zal automatisch de mensen herstellen die tijdens de eerste levering worden gericht.

   Dit is de levering van het &quot;Watersportaanbod&quot;.

   ![](assets/query_editor_ex_08.png)

1. De tweede vertakking definiëren. Deze vertakking bevat de e-mail met follow-up met dezelfde inhoud als voor de eerste levering. Ga naar het tabblad **[!UICONTROL Subsets]** en klik **[!UICONTROL Add]** om het te maken.

   ![](assets/query_editor_ex_06.png)

1. Er wordt een ander subtabblad weergegeven. Noem het &quot;**Kon niet**&quot;.
1. Klik op **[!UICONTROL Add a filtering condition for the incoming population]**. Klik vervolgens op **[!UICONTROL Edit...]**.

   ![](assets/query_editor_ex_07.png)

1. Klik **[!UICONTROL Delivery recipients]** in het **[!UICONTROL Targeting and filtering dimension]** venster.
1. Selecteer in het venster **[!UICONTROL Target element]** het gedrag **[!UICONTROL Recipients who did not click (email)]**. Selecteer de optie **[!UICONTROL Delivery specified by the transition]** zoals weergegeven voor de laatste vertakking.

   De **[!UICONTROL Split]** doos wordt nu volledig gevormd.

   ![](assets/query_editor_ex_03.png)

Hieronder ziet u de lijst met de diverse componenten die standaard zijn geconfigureerd:

* **[!UICONTROL All recipients]**
* **[!UICONTROL Recipients of successfully sent messages,]**
* **[!UICONTROL Recipients who opened or clicked (email),]**
* **[!UICONTROL Recipients who clicked (email),]**
* **[!UICONTROL Recipients of a failed message,]**
* **[!UICONTROL Recipients who didn't open or click (email),]**
* **[!UICONTROL Recipients who didn't click (email).]**

   ![](assets/query_editor_ex_02.png)
