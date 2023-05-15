---
product: campaign
title: Een instellen voor terugkerende importactiviteiten
description: Leer hoe u een workflowsjabloon voor terugkerende import configureert
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows, Data Management
exl-id: e6e140cb-8de0-4ab9-bddc-95abe04124c6
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '1020'
ht-degree: 1%

---

# Een workflow instellen voor terugkerende importactiviteiten {#setting-up-a-recurring-import}



Het gebruik van een werkstroomsjabloon is de beste manier als u regelmatig bestanden met dezelfde structuur moet importeren.

In dit voorbeeld ziet u hoe u een workflow instelt die opnieuw kan worden gebruikt voor het importeren van profielen die afkomstig zijn van een CRM in de Adobe Campaign-database. Raadpleeg deze voor meer informatie over alle mogelijke instellingen voor elke activiteit [sectie](about-activities.md).

1. Een nieuw werkstroomsjabloon maken op basis van **[!UICONTROL Resources > Templates > Workflow templates]**.
1. Voeg de volgende activiteiten toe:

   * **[!UICONTROL Data loading (file)]**: Definieer de verwachte structuur van het bestand met de gegevens die u wilt importeren.
   * **[!UICONTROL Enrichment]**: De geïmporteerde gegevens afstemmen op de databasegegevens.
   * **[!UICONTROL Split]**: Maak filters om records op een andere manier te verwerken, afhankelijk van de vraag of ze met elkaar in overeenstemming kunnen worden gebracht.
   * **[!UICONTROL Deduplication]**: Dupliceer de gegevens uit het binnenkomende bestand voordat deze in de database worden ingevoegd.
   * **[!UICONTROL Update data]**: Werk de database bij met de geïmporteerde profielen.

   ![](assets/import_template_example0.png)

1. Configureer de **[!UICONTROL Data Loading (file)]** activiteit:

   * Definieer de verwachte structuur door een voorbeeldbestand te uploaden. Het voorbeeldbestand mag slechts een paar regels bevatten, maar alle kolommen die nodig zijn voor het importeren. Controleer en bewerk de bestandsindeling om te controleren of het type van elke kolom correct is ingesteld: tekst, datum, geheel getal, enz. Bijvoorbeeld:

      ```
      lastname;firstname;birthdate;email;crmID
      Smith;Hayden;23/05/1989;hayden.smith@mailtest.com;123456
      ```

   * In de **[!UICONTROL Name of the file to load]** sectie, selecteert u **[!UICONTROL Upload a file from the local machine]** en laat het veld leeg. Telkens wanneer een nieuwe werkstroom van dit malplaatje wordt gecreeerd, kunt u hier het dossier specificeren u wilt, zolang het aan de bepaalde structuur beantwoordt.

      U kunt alle opties gebruiken, maar u moet de sjabloon dienovereenkomstig aanpassen. Als u bijvoorbeeld **[!UICONTROL Specified in the transition]** kunt u een **[!UICONTROL File Transfer]** activiteit voor het ophalen van het bestand dat moet worden geïmporteerd van een FTP-/SFTP-server. Met S3- of SFTP-verbinding kunt u ook segmentgegevens importeren naar Adobe Campaign met het Adobe Real-Time Customer Data-platform. Raadpleeg de volgende secties voor meer informatie [documentatie](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email-marketing/adobe-campaign.html).

      ![](assets/import_template_example1.png)

1. Configureer de **[!UICONTROL Enrichment]** activiteit. Het doel van deze activiteit in dit verband is de identificatie van de binnenkomende gegevens.

   * In de **[!UICONTROL Enrichment]** tab, selecteert u **[!UICONTROL Add data]** en definieert u een koppeling tussen de geïmporteerde gegevens en de ontvangers voor dimensie. In dit voorbeeld wordt **CRM-id** Het aangepaste gebied wordt gebruikt om tot de te verbinden voorwaarde te leiden. Gebruik het veld of de combinatie van velden die u nodig hebt, zolang u unieke records kunt identificeren.
   * In de **[!UICONTROL Reconciliation]** tabblad, laat de **[!UICONTROL Identify the document from the working data]** optie uitgeschakeld.

   ![](assets/import_template_example2.png)

1. Configureer de **[!UICONTROL Split]** activiteit om verenigde ontvangers in één overgang en ontvangers terug te winnen die niet in overeenstemming konden worden gebracht maar die genoeg gegevens in een tweede overgang hebben.

   De overgang met onderling verzochte ontvangers kan dan worden gebruikt om het gegevensbestand bij te werken. De overgang met onbekende ontvangers kan dan worden gebruikt om nieuwe ontvankelijke ingangen in het gegevensbestand tot stand te brengen als een minimumreeks informatie in het dossier beschikbaar is.

   Ontvangers die niet in overeenstemming kunnen worden gebracht en niet genoeg gegevens hebben, worden in een complementaire uitgaande overgang geselecteerd en kunnen in een afzonderlijk bestand worden geëxporteerd of eenvoudig worden genegeerd.

   * In de **[!UICONTROL General]** tabblad van de activiteit, selecteert u **[!UICONTROL Use the additional data only]** als het filtreren plaatsen en zorg ervoor dat **[!UICONTROL Targeting dimension]** wordt automatisch ingesteld op **[!UICONTROL Enrichment]**.

      Controleer de **[!UICONTROL Generate complement]** om te kunnen zien of kan om het even welk verslag niet in het gegevensbestand worden opgenomen. Indien nodig kunt u de aanvullende gegevens verder verwerken: bestand exporteren, lijst bijwerken, enz.

   * In de eerste subset van het dialoogvenster **[!UICONTROL Subsets]** tab, voeg een het filtreren voorwaarde op de binnenkomende bevolking toe om slechts verslagen te selecteren waarvoor de ontvankelijke primaire sleutel niet gelijk aan 0 is. Op deze manier worden gegevens uit het bestand die in overeenstemming zijn met ontvangers uit de database, geselecteerd in die subset.

      ![](assets/import_template_example3.png)

   * Voeg een tweede subset toe die onverzochte records selecteert die voldoende gegevens bevatten om in de database te worden ingevoegd. Bijvoorbeeld: e-mailadres, voornaam en achternaam.

      Subsets worden verwerkt in hun aanmaakvolgorde. Dit houdt in dat wanneer deze tweede subset wordt verwerkt, alle records die al in de database bestaan al in de eerste subset zijn geselecteerd.

      ![](assets/import_template_example3_2.png)

   * Alle records die niet in de eerste twee subsets zijn geselecteerd, worden geselecteerd in het dialoogvenster **[!UICONTROL Complement]**.

1. Configureer de **[!UICONTROL Update data]** activiteit die na de eerste uitgaande overgang van wordt gevestigd **[!UICONTROL Split]** eerder geconfigureerde activiteit.

   * Selecteren **[!UICONTROL Update]** als **[!UICONTROL Operation type]** aangezien de binnenkomende overgang slechts ontvangers bevat die reeds in het gegevensbestand aanwezig zijn.
   * In de **[!UICONTROL Record identification]** sectie, selecteert u **[!UICONTROL Using reconciliation keys]** en definieert u een sleutel tussen de doeldimensie en de koppeling die in het dialoogvenster **[!UICONTROL Enrichment]**. In dit voorbeeld wordt **CRM-id** aangepast veld wordt gebruikt.
   * In de **[!UICONTROL Fields to update]** , geeft u de velden in de dimensie Ontvangers aan die moeten worden bijgewerkt met de waarde van de corresponderende kolom in het bestand. Als de namen van de bestandskolommen identiek of bijna identiek zijn aan de namen van de afmetingsvelden van de ontvangers, kunt u de toverknop gebruiken om de verschillende velden automatisch aan te passen.

      ![](assets/import_template_example6.png)

1. Configureer de **[!UICONTROL Deduplication]** activiteit die zich na de overgang bevindt en die niet-verzochte ontvangers bevat:

   * Selecteren **[!UICONTROL Edit configuration]** en stelt de doeldimensie in op het tijdelijke schema dat wordt gegenereerd op basis van het **[!UICONTROL Enrichment]** activiteit van de workflow.

      ![](assets/import_template_example4.png)

   * In dit voorbeeld wordt het e-mailveld gebruikt om unieke profielen te zoeken. U kunt elk veld gebruiken waarvan u zeker weet dat het is ingevuld en deel uitmaakt van een unieke combinatie.
   * In de **[!UICONTROL Deduplication method]** scherm, selecteren **[!UICONTROL Advanced parameters]** en de **[!UICONTROL Disable automatic filtering of 0 ID records]** optie om ervoor te zorgen dat records met een primaire sleutel gelijk aan 0 (die alle records van deze overgang moeten zijn) niet worden uitgesloten.

   ![](assets/import_template_example7.png)

1. Configureer de **[!UICONTROL Update data]** activiteit die zich na de **[!UICONTROL Deduplication]** eerder geconfigureerde activiteit.

   * Selecteren **[!UICONTROL Insert]** als **[!UICONTROL Operation type]** aangezien de binnenkomende overgang slechts ontvangers bevat die niet in het gegevensbestand aanwezig zijn.
   * In de **[!UICONTROL Record identification]** sectie, selecteert u **[!UICONTROL Directly using the targeting dimension]** en kiest u **[!UICONTROL Recipients]** dimensie.
   * In de **[!UICONTROL Fields to update]** , geeft u de velden in de dimensie Ontvangers aan die moeten worden bijgewerkt met de waarde van de corresponderende kolom in het bestand. Als de namen van de bestandskolommen identiek of bijna identiek zijn aan de namen van de afmetingsvelden van de ontvangers, kunt u de toverknop gebruiken om de verschillende velden automatisch aan te passen.

      ![](assets/import_template_example8.png)

1. Na de derde overgang van de **[!UICONTROL Split]** activiteit, voeg een **[!UICONTROL Data extraction (file)]** en **[!UICONTROL File transfer]** activiteit als u spoor van gegevens wilt houden die niet in het gegevensbestand worden opgenomen. Configureer die activiteiten om de kolom die u nodig hebt te exporteren en om het bestand over te brengen naar een FTP- of SFTP-server waar u het bestand kunt ophalen.
1. Een **[!UICONTROL End]** en sla het werkstroomsjabloon op.

De sjabloon kan nu worden gebruikt en is beschikbaar voor elke nieuwe workflow. Het bestand met de gegevens die u wilt importeren in het dialoogvenster **[!UICONTROL Data loading (file)]** activiteit.

![](assets/import_template_example9.png)
