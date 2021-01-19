---
solution: Campaign Classic
product: campaign
title: Importtaken configureren
description: Leer hoe u importtaken configureert en uitvoert in Campaign Classic.
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
translation-type: tm+mt
source-git-commit: ba460d8347c987291681641a1be208027acf1d2f
workflow-type: tm+mt
source-wordcount: '2958'
ht-degree: 0%

---


# Importtaken configureren {#executing-import-jobs}

Met Adobe Campaign kunt u gegevens uit een of meer bestanden in tekst-, CSV-, TAB- of XML-indeling importeren in de database. Deze bestanden zijn gekoppeld aan een tabel (hoofd of gekoppeld) en elk veld van het bronbestand of de bronbestanden is gekoppeld aan een veld van de database.

>[!NOTE]
>
>U kunt gegevens importeren zonder deze toe te wijzen met de databasegegevens met behulp van de functie **[!UICONTROL Import a list]**. De gegevens kunnen vervolgens uitsluitend in workflows worden gebruikt via het object **[!UICONTROL Read list]**. Raadpleeg [deze pagina](../../workflow/using/read-list.md) voor meer informatie.

Met de wizard Importeren kunt u een importbewerking configureren, de opties ervan (zoals gegevenstransformatie) definiëren en uitvoering starten. Het is een reeks schermen waarvan de inhoud afhankelijk is van het type import (enkelvoudig of meervoudig) en de rechten van de operator.

De de invoertovenaar toont na het creëren van een nieuwe de invoerbaan (zie [het Creëren van de invoer en de uitvoerbanen](../../platform/using/creating-import-export-jobs.md).

>[!NOTE]
>
>Als u een server van het Web IIS gebruikt, kan een configuratie noodzakelijk zijn om het uploaden van grote dossiers (>28 MB) toe te staan. Raadpleeg [deze sectie](../../installation/using/integration-into-a-web-server-for-windows.md#changing-the-upload-file-size-limit) voor meer informatie.

## Bronbestand {#source-file}

In het bronbestand valt elke regel samen met een record. De gegevens in records worden gescheiden door scheidingstekens (spatie, tab, teken enz.). Dit betekent dat de gegevens in de vorm van kolommen worden teruggewonnen, en elke kolom wordt geassocieerd met een gebied van het gegevensbestand.

## Stap 1 - Het kiezen van het invoermalplaatje {#step-1---choosing-the-import-template}

Wanneer u de wizard Importeren start, moet u eerst een sjabloon selecteren. Als voorbeeld, om de invoer van ontvangers te vormen die een nieuwsbrief ontvingen, volg de stappen hieronder:

1. Selecteer de map **[!UICONTROL Profiles and Targets > Job > Generic imports and exports]**.
1. Klik **Nieuw** en klik dan **Invoer** om het de invoermalplaatje tot stand te brengen.

   ![](assets/s_ncs_user_import_wizard01_1.png)

1. Klik op de pijl rechts van het veld **[!UICONTROL Import template]** om de sjabloon te selecteren of klik **[!UICONTROL Select link]** om door de structuur te bladeren.

   De native sjabloon is **[!UICONTROL New text import]**. Deze sjabloon moet niet worden gewijzigd, maar u kunt het dupliceren om een nieuwe sjabloon te configureren, afhankelijk van uw vereisten. Importeersjablonen worden standaard opgeslagen in het knooppunt **[!UICONTROL Profiles and targets > Templates > Job templates]**.

1. Voer in het veld **[!UICONTROL Label]** een naam in voor deze importbewerking. U kunt een beschrijving toevoegen.
1. Selecteer het type import in het desbetreffende veld. Er zijn twee mogelijke typen importbewerkingen: **[!UICONTROL Simple import]** om slechts één dossier in te voeren, en **[!UICONTROL Multiple import]** om verscheidene dossiers in één enkele uitvoering in te voeren.

   Selecteer **[!UICONTROL Multiple import]** in de vervolgkeuzelijst **[!UICONTROL Import type]** in het eerste scherm van de wizard Importeren voor meerdere importbewerkingen.

   ![](assets/s_ncs_user_import_wizard01_2.png)

1. Geef de velden op die u wilt importeren door op **[!UICONTROL Add]** te klikken.

   ![](assets/s_ncs_user_import_wizard01_3.png)

   Elke keer dat een bestand wordt toegevoegd, wordt het scherm van de wizard **[!UICONTROL File to import]** weergegeven. Zie sectie [Stap 2 - Brondossierselectie](#step-2---source-file-selection) en volg de stappen in de tovenaar om de de invoeropties zoals voor eenvoudige invoer te bepalen.

   >[!NOTE]
   >
   >Meerdere importen moeten alleen aan specifieke behoeften voldoen en worden niet aanbevolen.

### Geavanceerde parameters {#advanced-parameters}

Met de koppeling **[!UICONTROL Advanced parameters]** hebt u toegang tot de volgende opties:

* **[!UICONTROL General]** tab

   * **[!UICONTROL Stop execution if there are too many rejects]**

      Deze optie is standaard ingeschakeld. U kunt de selectie opheffen als u het importeren wilt blijven uitvoeren, ongeacht het aantal afwijzingen. De uitvoering wordt standaard gestopt wanneer de eerste 100 regels worden geweigerd.

   * **[!UICONTROL Trace mode]**

      Selecteer deze optie om de uitvoering van het importeren voor elke regel bij te houden.

   * **[!UICONTROL Start the job in a detached process]**

      Deze optie is standaard ingeschakeld. Hiermee kunt u de uitvoering van het importeren loskoppelen, zodat dit geen invloed heeft op andere taken in de database.

   * **[!UICONTROL Do not update enumerations]**

      Selecteer deze optie om te voorkomen dat de lijst met opgesomde waarden in de database wordt verrijkt. Zie [Opsommingen beheren](../../platform/using/managing-enumerations.md).

* **[!UICONTROL Variables]** tab

   U kunt variabelen definiëren die aan de taak zijn gekoppeld en die toegankelijk zijn in de query-editors en berekende velden. Als u een variabele wilt maken, klikt u op **[!UICONTROL Add]** en gebruikt u de variabele-editor.

   >[!IMPORTANT]
   >
   >Het **[!UICONTROL Variables]** lusje is voor slechts werkstroomtype programmeringsgebruik, en zou door deskundige slechts gebruikers moeten worden gevormd.

## Stap 2 - Bronbestandsselectie {#step-2---source-file-selection}

Het bronbestand kan de tekstindeling (txt, csv, tab, vaste kolommen) of xml hebben.

Standaard is **[!UICONTROL Upload file on the server]** geselecteerd. Klik op de map rechts van het veld **[!UICONTROL Local file]** om naar de lokale schijf te bladeren en het bestand te selecteren dat u wilt importeren. U kunt deze optie deselecteren om het toegangspad en de naam in te voeren van het bestand als dit zich op de server bevindt.

![](assets/s_ncs_user_import_wizard02_1.png)

Wanneer het bestand is opgegeven, kunt u de gegevens ervan weergeven in de onderste sectie van het venster door op **[!UICONTROL Auto-detect format]** te klikken. In deze voorvertoning worden de eerste 200 regels van het bronbestand weergegeven.

![](assets/s_ncs_user_import_wizard02_2.png)

Gebruik de opties boven deze weergave om het importeren te configureren. De parameters die via deze opties worden gedefinieerd, worden overgebracht naar de voorvertoning. De volgende opties zijn beschikbaar:

* **[!UICONTROL Click here to change the file format...]** Hiermee kunt u de bestandsindeling controleren en de configuratie perfectioneren.
* **[!UICONTROL Update on server...]** Hiermee kunt u het lokale bestand overbrengen naar de server. Deze optie is alleen beschikbaar als **[!UICONTROL Upload file on the server]** is geselecteerd.
* **[!UICONTROL Download]** is alleen beschikbaar als het bestand op de server is geüpload.
* **[!UICONTROL Auto-detect format]** wordt gebruikt om het formaat van de gegevensbron opnieuw te initialiseren. Met deze optie kunt u de oorspronkelijke indelingen opnieuw toepassen op gegevens die zijn opgemaakt met de optie **[!UICONTROL Click here to change the file format...]**.
* Met de koppeling **[!UICONTROL Advanced parameters]** kunt u de brongegevens filteren en geavanceerde opties gebruiken. Vanuit dit scherm kunt u ervoor kiezen om slechts een deel van het bestand te importeren. U kunt ook een filter definiëren, bijvoorbeeld om alleen gebruikers van het type Prospect of Klant te importeren, op basis van de waarde van de corresponderende regel. Deze opties mogen alleen worden gebruikt door deskundige JavaScript-gebruikers.

### De bestandsindeling wijzigen {#changing-the-file-format}

Met de optie **[!UICONTROL Click here to change the file format...]** kunt u de gegevens van het bronbestand opmaken, en met name het kolomscheidingsteken en het type gegevens voor elk veld opgeven. Deze configuratie wordt uitgevoerd via het volgende venster:

![](assets/s_ncs_user_import_wizard02_3.png)

In deze stap kunt u beschrijven hoe de waarden van de bestandsvelden moeten worden gelezen. In het geval van een datum kunnen de datum- of datum- en tijdgegevens bijvoorbeeld worden gekoppeld aan een notatie (dd/mm/jjjj, mm/dd/jj, enz.). Als de invoergegevens niet overeenkomen met de verwachte indeling, worden deze tijdens het importeren geweigerd.

U kunt het resultaat van de configuratie weergeven in de voorvertoningszone in het onderste gedeelte van het venster.

Klik **[!UICONTROL OK]** om het formatteren te bewaren, dan klik **[!UICONTROL Next]** om de volgende stap te tonen.

## Stap 3 - Veld toewijzen {#step-3---field-mapping}

U moet dan het bestemmingsschema selecteren en de gegevens van elke kolom op gebieden in het gegevensbestand in kaart brengen.

![](assets/s_ncs_user_import_wizard03_1.png)

* In het veld **[!UICONTROL Destination schema]** kunt u het schema selecteren waarin de gegevens worden geïmporteerd. Deze informatie is verplicht. Klik op het pictogram **[!UICONTROL Select link]** om een van de bestaande schema&#39;s te selecteren. Klik op **[!UICONTROL Edit link]** om de inhoud van de geselecteerde tabel weer te geven.
* In de centrale tabel staan alle velden die in het bronbestand zijn gedefinieerd. Selecteer de velden die u wilt importeren om er een doelbestand aan te koppelen. Deze velden kunnen handmatig of automatisch worden toegewezen.

   Als u een veld handmatig wilt toewijzen, klikt u op het selectievakje om het bronveld te selecteren en klikt u op de tweede kolom om de cel te activeren die overeenkomt met het geselecteerde veld. Klik vervolgens op het pictogram **[!UICONTROL Edit expression]** om alle velden van de huidige tabel weer te geven. Selecteer het doelveld en klik op **[!UICONTROL OK]** om de toewijzing te valideren.

   Als u de bronvelden en doelvelden automatisch wilt koppelen, klikt u op het pictogram **[!UICONTROL Guess the destination fields]** rechts van de lijst met velden. De voorgestelde velden kunnen indien nodig worden gewijzigd.

   >[!IMPORTANT]
   >
   >Het resultaat van deze bewerking moet altijd worden gevalideerd voordat u verdergaat met de volgende stap.

* U kunt een transformatie toepassen op de geïmporteerde velden. Klik hiertoe in de cel van de kolom **[!UICONTROL Transformation]** die op het betrokken gebied betrekking heeft, en selecteer de toe te passen transformatie.

   ![](assets/s_ncs_user_import_wizard03_2.png)

   >[!IMPORTANT]
   >
   >De transformatie wordt toegepast op het moment van importeren. Als beperkingen op het bestemmingsgebied, echter (in het bovenstaande voorbeeld, op het @lastname gebied) zijn bepaald, nemen deze beperkingen prioriteit.

* U kunt berekende velden toevoegen met het juiste pictogram rechts van de centrale tabel. Met berekende velden kunt u complexe transformaties uitvoeren, virtuele kolommen toevoegen of de gegevens van meerdere kolommen samenvoegen. Raadpleeg de volgende secties voor meer informatie over de verschillende mogelijkheden.

### Berekende velden {#calculated-fields}

Berekende velden zijn nieuwe kolommen die aan het bronbestand worden toegevoegd en uit andere kolommen worden berekend. Berekende velden kunnen vervolgens worden gekoppeld aan velden in de Adobe Campaign-database. Afstemmingen zijn echter niet mogelijk op berekende velden.

Er zijn vier typen berekende velden:

* **[!UICONTROL Fixed string]**: de waarde van het berekende veld is gelijk voor alle regels van het bronbestand. Hiermee kunt u de waarde instellen van een veld met records die zijn ingevoegd of bijgewerkt. U kunt bijvoorbeeld voor alle geïmporteerde records een markering instellen op &quot;ja&quot;.
* **[!UICONTROL String with JavaScript tags]**: de waarde van het berekende veld is een tekenreeks met JavaScript-opdrachten.
* **[!UICONTROL JavaScript expression]**: De waarde van het berekende veld is het resultaat van de evaluatie van een JavaScript-functie. De geretourneerde waarde kan een getal, een datum enzovoort zijn.
* **[!UICONTROL Enumeration]**: de waarde van het veld wordt toegewezen aan de waarde in het bronbestand. De redacteur laat u de bronkolom specificeren en de lijst van opsommingswaarden ingaan, zoals in het volgende voorbeeld:

   ![](assets/s_ncs_user_import_wizard03_3.png)

   Met het tabblad **[!UICONTROL Preview]** kunt u het resultaat van de gedefinieerde configuratie weergeven. Hier is de kolom **[!UICONTROL Subscription]** toegevoegd. De waarde wordt berekend uit het veld **Status**.

   ![](assets/s_ncs_user_import_wizard03_4.png)

## Stap 4 - Afstemming {#step-4---reconciliation}

Met de afstemmingsstap van de importwizard kunt u de modus definiëren waarmee de gegevens uit het bestand worden afgestemd op de bestaande gegevens in de database en kunt u de prioriteitsregels instellen tussen de bestandsgegevens en de databasegegevens. Het configuratievenster ziet er als volgt uit:

![](assets/s_ncs_user_import_wizard04_1.png)

Het centrale gedeelte van het scherm bevat een structuur met de velden en tabellen van de Adobe Campaign-database waarnaar de gegevens worden geïmporteerd.

Er zijn speciale opties beschikbaar voor elk knooppunt (tabel of veld). Wanneer u op het betrokken knooppunt klikt in de lijst, worden de parameters en een korte beschrijving ervan hieronder weergegeven. Het gedrag dat voor elk element wordt bepaald wordt getoond in de overeenkomstige **[!UICONTROL Behavior]** kolom.

![](assets/s_ncs_user_import_wizard04_2.png)

### Soorten bewerkingen {#types-of-operation}

Voor elke tabel waarop de invoer betrekking heeft, moet u het type bewerking definiëren. De volgende bewerkingen zijn beschikbaar voor het hoofdelement van de database:

* **[!UICONTROL Update or insertion]**: werkt het verslag bij als het in het gegevensbestand bestaat, en leidt tot het als niet.
* **[!UICONTROL Insertion]**: voegt records in de database in.
* **[!UICONTROL Update]**: werkt alleen bestaande records bij (negeert andere records).
* **[!UICONTROL Reconciliation only]**: zoekt naar de record in de database, maar voert geen update uit. Hiermee kunt u bijvoorbeeld de map met ontvangers koppelen om te importeren volgens een kolom van het bestand zonder de gegevens in de mappen bij te werken.
* **[!UICONTROL Deletion]**: Hiermee kunt u records in de database vernietigen.

De volgende opties zijn beschikbaar voor elk veld in de tabel waarop de invoer betrekking heeft:

* **[!UICONTROL Update (empty) if source value is empty]**: in het geval van een update verwijdert de waarde in het veld de databasewaarde als het veld leeg is in het bronbestand. Anders wordt het databaseveld bewaard.
* **[!UICONTROL Update only if destination is empty]**: de waarde van het bronbestand overschrijft de waarde in het databaseveld niet, tenzij het databaseveld leeg is. In dat geval wordt de waarde van het bronbestand gebruikt.
* **[!UICONTROL Update the field only when the record is inserted]**: tijdens een update- of invoegbewerking worden alleen nieuwe bronbestandsrecords geïmporteerd.

>[!NOTE]
>
>De definitie van een afstemmingssleutel is altijd **verplicht**, behalve in het geval van invoeging zonder deduplicatie.

### Afstemmingssleutels {#reconciliation-keys}

Er moet ten minste één afstemmingssleutel worden ingevuld om deduplicatie te beheren.

Een afstemmingssleutel is een set velden die wordt gebruikt om een record te identificeren. Als u bijvoorbeeld ontvangers wilt importeren, kan de afstemmingssleutel het rekeningnummer, het veld E-mail of de velden Achternaam, Voornaam, Bedrijf zijn, enzovoort.

In dit geval vergelijkt de importengine de waarden van het bestand met die van de database voor alle velden van de sleutel om te zien of een regel van een bestand overeenkomt met een bestaande ontvanger in de database. Wanneer velden specifiek zijn voor een record, kan een nauwkeurige vergelijking tussen de bron- en de doelgegevens worden uitgevoerd, zodat de integriteit van de gegevens na het importeren wordt gegarandeerd. Voor dezelfde tabel kan een tweede afstemmingssleutel worden ingevuld; wordt gebruikt voor de lijnen waarvan de eerste sleutel leeg is.

Kies geen veld dat tijdens het importeren kan worden gewijzigd. als dit gebeurt , kan de engine aanvullende records maken .

![](assets/s_ncs_user_import_wizard04_3.png)

>[!NOTE]
>
>Voor het importeren van ontvangers wordt de id van de geselecteerde map impliciet aan de sleutel toegevoegd.
>
>Afstemming wordt daarom alleen op deze map uitgevoerd (tenzij er geen map is geselecteerd).

### Deduplicatie {#deduplication}

>[!NOTE]
>
>Een &#39;dubbel&#39; is een item dat twee of meer keren voorkomt in het bestand dat moet worden geïmporteerd.
>
>Een &#39;duplicaat&#39; is een item dat aanwezig is in het bestand dat moet worden geïmporteerd en in de database.

Met het veld **[!UICONTROL Management of doubles]** kunt u de deduplicatie van gegevens configureren. Deduplicatie heeft betrekking op records die verschillende keren **in het bronbestand** (of bronbestanden in geval van een import van meerdere bestanden) voorkomen, d.w.z. lijnen waarvoor de velden van de afstemmingssleutel identiek zijn.

* Duplicaat beheer in **[!UICONTROL Update]** wijze (de standaardwijze) voert geen deduplicatie uit. De laatste record heeft daarom prioriteit (omdat deze de gegevens van de voorgaande records bijwerkt). Het tellen van duplicaten wordt niet uitgevoerd in deze modus.
* Duplicaat beheer in **[!UICONTROL Ignore]** wijze of **[!UICONTROL Reject entity]** sluit duplicaten van de invoer uit. In dit geval wordt geen record geïmporteerd.
* In de modus **[!UICONTROL Reject entity]** wordt het element niet geïmporteerd en wordt een fout gegenereerd in de importlogboeken.
* In de modus **[!UICONTROL Ignore]** wordt het element niet geïmporteerd, maar wordt geen spoor van de fout behouden. In deze modus kunt u de prestaties optimaliseren.

>[!IMPORTANT]
>
>Deduplicatie wordt alleen in het geheugen uitgevoerd. De omvang van een invoer met deduplicatie is daarom beperkt. De limiet is afhankelijk van verschillende parameters (capaciteit van de toepassingsserver, activiteit, aantal velden in de sleutel, enz.). De maximale grootte voor een deduplicatie is ongeveer 1.000.000 regels.

Deduplicatie heeft betrekking op een record die zowel in het bronbestand als in de database aanwezig is. Het betreft bewerkingen met alleen updates (d.w.z. **[!UICONTROL Update and insertion]** of **[!UICONTROL Update]**). Met de optie **[!UICONTROL Duplicate management]** kunt u de record bijwerken of negeren als deze zich in zowel het bronbestand als de database bevindt. De optie **[!UICONTROL Update or insert based on origin]** behoort tot de optionele module en kan niet worden gebruikt in een standaardcontext.

De opties **[!UICONTROL Reject]** en **[!UICONTROL Ignore]** werken zoals hierboven beschreven.

### Gedrag in geval van een fout {#behavior-in-the-event-of-an-error}

De meeste gegevensoverdrachtsbewerkingen genereren verschillende soorten fouten (incoherente regelindeling, ongeldig e-mailadres, enz.). Alle fouten en waarschuwingen die door de importengine worden gegenereerd, worden opgeslagen en gekoppeld aan het importexemplaar.

![](assets/s_ncs_user_import_general_tab.png)

De details van deze verwerpingen kunnen via **[!UICONTROL Rejects]** tabel worden bekeken.

![](assets/s_ncs_user_import_rejets_tab.png)

Er zijn twee soorten verwerpingen (het type wordt getoond in **[!UICONTROL Connector]** kolom):

* Afwijzingen van de tekstconnector hebben betrekking op fouten die optreden tijdens het verwerken van de bestandsregel (berekend veld, gegevensanalyse, enz.). In dit geval wordt bij een fout de hele regel altijd geweigerd.
* Afkeuringen van databaseverbindingen hebben betrekking op fouten die optreden tijdens het afstemmen van gegevens of het schrijven naar de database. In het geval van een import naar meerdere tabellen kan de afwijzing alleen betrekking hebben op een deel van de record (bijvoorbeeld bij het importeren van ontvangers en bijbehorende gebeurtenissen kan een fout het bijwerken van een gebeurtenis voorkomen zonder de ontvanger te negeren).

Op de pagina voor het afstemmen van gegevens kunt u het gewenste veld voor het type foutbeheer per veld en tabel per tabel definiëren.

* **[!UICONTROL Ignore and log a warning]**: alle velden worden geïmporteerd in de database, behalve de velden die een fout hebben gegenereerd.
* **[!UICONTROL Reject parent element]**: de gehele regel van de record wordt geweigerd, niet alleen het veld dat een fout heeft veroorzaakt.
* **[!UICONTROL Reject all elements]**: de importstops en alle elementen van de record worden afgewezen.

   ![](assets/s_ncs_user_import_wizard04_4.png)

De structuur in het afstotingsscherm van een importinstantie geeft aan welke velden zijn geweigerd en waar de fouten zijn opgetreden.

U kunt een bestand met deze records genereren via het pictogram **[!UICONTROL Export rejects]**:

![](assets/s_ncs_user_import_errors_export.png)

## Stap 5 - Extra stap bij het importeren van ontvangers {#step-5---additional-step-when-importing-recipients}

In de volgende stap van de wizard Importeren kunt u de map selecteren of maken waarin gegevens worden geïmporteerd, geïmporteerde ontvangers automatisch toewijzen met een (nieuwe of bestaande) lijst en ontvangers abonneren op een service.

![](assets/s_ncs_user_import_wizard05_1.png)

>[!NOTE]
>
>Deze stap wordt alleen weergegeven wanneer u ontvangers importeert en wanneer u de standaard Adobe Campaign-tabel voor ontvangers gebruikt (**nms:ontvanger**).

* Klik op de koppelingen **[!UICONTROL Edit]** om de map, de lijst of de service te selecteren waaraan u de ontvangers wilt koppelen of zich erop wilt abonneren.

   1. Importeren in een map

      Met de koppeling **[!UICONTROL Edit...]** van de sectie **[!UICONTROL Import into a folder]** kunt u de map selecteren of maken waarin de ontvangers worden geïmporteerd. Als standaard geen partitie is gedefinieerd, worden de gegevens geïmporteerd in de standaardmap van de operator.

      >[!NOTE]
      >
      >De standaardmap voor een operator is de eerste map waarvoor de operator schrijftoegang heeft. Zie [Beheer van maptoegang](../../platform/using/access-management.md#folder-access-management).

      Als u de importmap wilt selecteren, klikt u op de pijl rechts van het veld **[!UICONTROL Folder]** en selecteert u de desbetreffende map. U kunt het **[!UICONTROL Select link]** pictogram ook gebruiken om de boom in een nieuw venster te tonen of een nieuwe omslag tot stand te brengen.

      ![](assets/s_ncs_user_import_wizard05_2.png)

      Als u een nieuwe map wilt maken, selecteert u het knooppunt waaruit u een map wilt toevoegen en klikt u met de rechtermuisknop. Selecteer **[!UICONTROL Create a new 'Recipients' folder]**.

      ![](assets/s_ncs_user_import_wizard05_3.png)

      De map wordt toegevoegd onder het huidige knooppunt. Voer de naam van de nieuwe map in, klik op Enter om te bevestigen en klik op **[!UICONTROL OK]**.

      ![](assets/s_ncs_user_import_wizard05_4.png)

   1. Koppelen aan een lijst

      Met de koppeling **[!UICONTROL Edit...]** in de sectie **[!UICONTROL Add recipients to a list]** kunt u een lijst selecteren of maken waarin de ontvangers worden geïmporteerd.

      ![](assets/s_ncs_user_import_wizard05_5.png)

      U kunt een nieuwe lijst voor deze ontvangers tot stand brengen door **[!UICONTROL Select link]**, dan **[!UICONTROL Create]** te klikken. Het maken en beheren van lijsten wordt weergegeven in [Lijsten maken en beheren](../../platform/using/creating-and-managing-lists.md).

      ![](assets/s_ncs_user_import_wizard05_6.png)

      U kunt besluiten om de ontvangers aan degenen toe te voegen die reeds in een lijst aanwezig zijn, of de lijst met de nieuwe ontvangers opnieuw te maken. In dit geval worden ontvangers verwijderd en vervangen door de geïmporteerde ontvangers als de lijst al ontvangers bevatte.

   1. Abonneren op een service

      Als u alle geïmporteerde ontvangers wilt abonneren op een informatieservice, klikt u op de koppeling **[!UICONTROL Edit...]** van de sectie **[!UICONTROL Subscribe recipients to a service]** om de informatieservice te selecteren of te maken waarop de ontvangers worden geabonneerd. U kunt de optie **[!UICONTROL Send a confirmation message]** selecteren: De inhoud van dit bericht wordt bepaald in het leveringsmalplaatje verbonden aan de abonnementsdienst.

      ![](assets/s_ncs_user_import_wizard05_7.png)

      U kunt een nieuwe service voor deze ontvangers maken door op **[!UICONTROL Select link]** en vervolgens op het pictogram **[!UICONTROL Create]** te klikken. Het beheer van informatieservices wordt beschreven in [deze sectie](../../delivery/using/managing-subscriptions.md).

* Gebruik het veld **[!UICONTROL Origin]** om informatie over de oorsprong van ontvangers toe te voegen aan hun profielen. Deze informatie is met name nuttig in het kader van een meervoudige import.

Klik **[!UICONTROL Next]** om deze stap te bevestigen en de volgende stap te tonen.

## Stap 6 - De import starten {#step-6---launching-the-import}

In de laatste stap van de wizard kunt u gegevensimport starten. Klik op de knop **[!UICONTROL Start]** om dit te doen.

![](assets/s_ncs_user_import_wizard06_1.png)

U kunt de uitvoering van de importtaak vervolgens controleren (zie [De uitvoering van taken controleren](../../platform/using/monitoring-jobs-execution.md).
