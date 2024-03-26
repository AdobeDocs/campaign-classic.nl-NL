---
product: campaign
title: Importtaken configureren
description: Leer hoe u importtaken configureert en uitvoert in Campagne
feature: Overview
badge-v7: label="v7" type="Informative" tooltip="Is van toepassing op Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: 05909ea6-2c93-42ff-9142-1dd14fa6fdec
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '2976'
ht-degree: 0%

---

# Importtaken configureren {#executing-import-jobs}



Met Adobe Campaign kunt u gegevens uit een of meer bestanden in tekst-, CSV-, TAB- of XML-indeling importeren in de database. Deze bestanden zijn gekoppeld aan een tabel (hoofd of gekoppeld) en elk veld van het bronbestand of de bronbestanden is gekoppeld aan een veld van de database.

>[!NOTE]
>
>U kunt gegevens importeren zonder deze toe te wijzen aan de databasegegevens met behulp van de **[!UICONTROL Import a list]** functie. De gegevens kunnen vervolgens uitsluitend in workflows worden gebruikt via de **[!UICONTROL Read list]** object. Raadpleeg [deze pagina](../../workflow/using/read-list.md) voor meer informatie.

Met de wizard Importeren kunt u een importbewerking configureren, de opties ervan (zoals gegevenstransformatie) definiëren en uitvoering starten. Het is een reeks schermen waarvan de inhoud afhankelijk is van het type import (enkelvoudig of meervoudig) en de rechten van de operator.

De wizard Importeren wordt weergegeven nadat een nieuwe importtaak is gemaakt (zie [Import- en exporttaken maken](../../platform/using/creating-import-export-jobs.md).

>[!NOTE]
>
>Als u een server van het Web IIS gebruikt, kan een configuratie noodzakelijk zijn om het uploaden van grote dossiers (>28 MB) toe te staan. Raadpleeg [deze sectie](../../installation/using/integration-into-a-web-server-for-windows.md#changing-the-upload-file-size-limit) voor meer informatie.

## Bronbestand {#source-file}

In het bronbestand valt elke regel samen met een record. De gegevens in records worden gescheiden door scheidingstekens (spatie, tab, teken, enz.). Dit betekent dat de gegevens in de vorm van kolommen worden teruggewonnen, en elke kolom wordt geassocieerd met een gebied van het gegevensbestand.

## Stap 1 - Kies de importsjabloon {#step-1---choosing-the-import-template}

Wanneer u de wizard Importeren start, moet u eerst een sjabloon selecteren. Als voorbeeld, om de invoer van ontvangers te vormen die een nieuwsbrief ontvingen, volg de stappen hieronder:

1. Selecteer de **[!UICONTROL Profiles and Targets > Job > Generic imports and exports]** map.
1. Klikken **Nieuw** en klik vervolgens op **Importeren** om de importsjabloon te maken.

   ![](assets/s_ncs_user_import_wizard01_1.png)

1. Klik op de pijl rechts van de knop **[!UICONTROL Import template]** te selecteren of klik op **[!UICONTROL Select link]** om door de boomstructuur te bladeren.

   De native sjabloon is **[!UICONTROL New text import]**. Deze sjabloon moet niet worden gewijzigd, maar u kunt het dupliceren om een nieuwe sjabloon te configureren, afhankelijk van uw vereisten. Importsjablonen worden standaard opgeslagen in de **[!UICONTROL Profiles and targets > Templates > Job templates]** knooppunt.

1. Voer een naam in voor deze importbewerking in het dialoogvenster **[!UICONTROL Label]** veld. U kunt een beschrijving toevoegen.
1. Selecteer het type import in het desbetreffende veld. Er zijn twee mogelijke typen importbewerkingen: **[!UICONTROL Simple import]** om slechts één bestand te importeren, en **[!UICONTROL Multiple import]** om meerdere bestanden in één uitvoering te importeren.

   Selecteer bij een meervoudige importbewerking **[!UICONTROL Multiple import]** van de **[!UICONTROL Import type]** vervolgkeuzelijst in het eerste scherm van de importwizard.

   ![](assets/s_ncs_user_import_wizard01_2.png)

1. Geef de velden op die u wilt importeren door op **[!UICONTROL Add]**.

   ![](assets/s_ncs_user_import_wizard01_3.png)

   Telkens wanneer een bestand wordt toegevoegd, wordt het scherm van de **[!UICONTROL File to import]** wordt weergegeven. Zie sectie [Stap 2 - Bronbestandsselectie](#step-2---source-file-selection) en voert u de stappen in de wizard uit om de importopties te definiëren als voor een eenvoudige importbewerking.

   >[!NOTE]
   >
   >Meerdere importen moeten alleen aan specifieke behoeften voldoen en worden niet aanbevolen.

### Geavanceerde parameters {#advanced-parameters}

De **[!UICONTROL Advanced parameters]** Via de koppeling hebt u toegang tot de volgende opties:

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

  U kunt variabelen definiëren die aan de taak zijn gekoppeld en die toegankelijk zijn in de query-editors en berekende velden. Klik op **[!UICONTROL Add]** en gebruikt u de variabele editor.

  >[!IMPORTANT]
  >
  >De **[!UICONTROL Variables]** tab is alleen bedoeld voor workflowtype programmering en moet alleen worden geconfigureerd door deskundige gebruikers.

## Stap 2 - Bronbestandsselectie {#step-2---source-file-selection}

Het bronbestand kan de tekstindeling (txt, csv, tab, vaste kolommen) of xml hebben.

Standaard, **[!UICONTROL Upload file on the server]** is geselecteerd. Klik op de map rechts van het dialoogvenster **[!UICONTROL Local file]** om op de lokale schijf te bladeren en het te importeren bestand te selecteren. U kunt deze optie deselecteren om het toegangspad en de naam in te voeren van het bestand als dit zich op de server bevindt.

![](assets/s_ncs_user_import_wizard02_1.png)

Wanneer het bestand is opgegeven, kunt u de gegevens in het onderste gedeelte van het venster bekijken door op **[!UICONTROL Auto-detect format]**. In deze voorvertoning worden de eerste 200 regels van het bronbestand weergegeven.

![](assets/s_ncs_user_import_wizard02_2.png)

Gebruik de opties boven deze weergave om het importeren te configureren. De parameters die via deze opties worden gedefinieerd, worden overgebracht naar de voorvertoning. De volgende opties zijn beschikbaar:

* **[!UICONTROL Click here to change the file format...]** Hiermee kunt u de bestandsindeling controleren en de configuratie perfectioneren.
* **[!UICONTROL Update on server...]** Hiermee kunt u het lokale bestand overbrengen naar de server. Deze optie is alleen beschikbaar als **[!UICONTROL Upload file on the server]** is geselecteerd.
* **[!UICONTROL Download]** is alleen beschikbaar als het bestand op de server is geüpload.
* **[!UICONTROL Auto-detect format]** wordt gebruikt om het formaat van de gegevensbron opnieuw te initialiseren. Met deze optie kunt u de oorspronkelijke indelingen opnieuw toepassen op gegevens die zijn opgemaakt via het dialoogvenster **[!UICONTROL Click here to change the file format...]** -optie.
* De **[!UICONTROL Advanced parameters]** Met de koppeling kunt u de brongegevens filteren en geavanceerde opties gebruiken. Vanuit dit scherm kunt u ervoor kiezen om slechts een deel van het bestand te importeren. U kunt ook een filter definiëren, bijvoorbeeld om alleen gebruikers van het type Prospect of Klant te importeren, op basis van de waarde van de corresponderende regel. Deze opties mogen alleen worden gebruikt door deskundige JavaScript-gebruikers.

### De bestandsindeling wijzigen {#changing-the-file-format}

De **[!UICONTROL Click here to change the file format...]** Met deze optie kunt u de gegevens van het bronbestand opmaken, en met name het kolomscheidingsteken en het type gegevens voor elk veld opgeven. Deze configuratie wordt uitgevoerd via het volgende venster:

![](assets/s_ncs_user_import_wizard02_3.png)

In deze stap kunt u beschrijven hoe de waarden van de bestandsvelden moeten worden gelezen. In het geval van een datum kunnen de datum- of datum- en tijdgegevens bijvoorbeeld worden gekoppeld aan een notatie (dd/mm/jjjj, mm/dd/jj, enz.). Als de invoergegevens niet overeenkomen met de verwachte indeling, worden deze tijdens het importeren geweigerd.

U kunt het resultaat van de configuratie weergeven in de voorvertoningszone in het onderste gedeelte van het venster.

Klikken **[!UICONTROL OK]** om de opmaak op te slaan, klikt u vervolgens op **[!UICONTROL Next]** de volgende stap weergeven.

## Stap 3 - Toewijzing van velden {#step-3---field-mapping}

U moet dan het bestemmingsschema selecteren en de gegevens van elke kolom op gebieden in het gegevensbestand in kaart brengen.

![](assets/s_ncs_user_import_wizard03_1.png)

* De **[!UICONTROL Destination schema]** kunt u het schema selecteren waarin de gegevens worden geïmporteerd. Deze informatie is verplicht. Klik op de knop **[!UICONTROL Select link]** om een van de bestaande schema&#39;s te selecteren. Klikken **[!UICONTROL Edit link]** om de inhoud van de geselecteerde tabel weer te geven.
* In de centrale tabel staan alle velden die in het bronbestand zijn gedefinieerd. Selecteer de velden die u wilt importeren om er een doelbestand aan te koppelen. Deze velden kunnen handmatig of automatisch worden toegewezen.

  Als u een veld handmatig wilt toewijzen, klikt u op het selectievakje om het bronveld te selecteren en klikt u op de tweede kolom om de cel te activeren die overeenkomt met het geselecteerde veld. Klik op de knop **[!UICONTROL Edit expression]** om alle velden van de huidige tabel weer te geven. Selecteer het doelveld en klik op **[!UICONTROL OK]** om de toewijzing te valideren.

  Als u de bronvelden en doelvelden automatisch wilt koppelen, klikt u op de knop **[!UICONTROL Guess the destination fields]** rechts van de lijst met velden. De voorgestelde velden kunnen indien nodig worden gewijzigd.

  >[!IMPORTANT]
  >
  >Het resultaat van deze bewerking moet altijd worden gevalideerd voordat u verdergaat met de volgende stap.

* U kunt een transformatie toepassen op de geïmporteerde velden. Klik hiertoe in de cel van het dialoogvenster **[!UICONTROL Transformation]** kolom die betrekking heeft op het betrokken veld, en selecteer de toe te passen transformatie.

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
* **[!UICONTROL JavaScript expression]**: de waarde van het berekende veld is het resultaat van de evaluatie van een JavaScript-functie. De geretourneerde waarde kan een getal, een datum enzovoort zijn.
* **[!UICONTROL Enumeration]**: de waarde van het veld wordt toegewezen aan de waarde in het bronbestand. De redacteur laat u de bronkolom specificeren en de lijst van opsommingswaarden ingaan, zoals in het volgende voorbeeld:

  ![](assets/s_ncs_user_import_wizard03_3.png)

  De **[!UICONTROL Preview]** kunt u het resultaat van de gedefinieerde configuratie weergeven. Hier, **[!UICONTROL Subscription]** kolom is toegevoegd. De waarde wordt berekend op basis van de **Status** veld.

  ![](assets/s_ncs_user_import_wizard03_4.png)

## Stap 4 - Verzoening {#step-4---reconciliation}

Met de afstemmingsstap van de importwizard kunt u de modus definiëren waarmee de gegevens uit het bestand worden afgestemd op de bestaande gegevens in de database en kunt u de prioriteitsregels instellen tussen de bestandsgegevens en de databasegegevens. Het configuratievenster ziet er als volgt uit:

![](assets/s_ncs_user_import_wizard04_1.png)

Het centrale gedeelte van het scherm bevat een structuur met de velden en tabellen van de Adobe Campaign-database waarnaar de gegevens worden geïmporteerd.

Er zijn speciale opties beschikbaar voor elk knooppunt (tabel of veld). Wanneer u op het betrokken knooppunt klikt in de lijst, worden de parameters en een korte beschrijving ervan hieronder weergegeven. Het gedrag dat voor elk element wordt gedefinieerd, wordt weergegeven in het corresponderende **[!UICONTROL Behavior]** kolom.

![](assets/s_ncs_user_import_wizard04_2.png)

### Soorten bewerkingen {#types-of-operation}

Voor elke tabel waarop de invoer betrekking heeft, moet u het type bewerking definiëren. De volgende bewerkingen zijn beschikbaar voor het hoofdelement van de database:

* **[!UICONTROL Update or insertion]**: werkt de record bij als deze in de database bestaat en maakt deze zo niet.
* **[!UICONTROL Insertion]**: voegt records in de database in.
* **[!UICONTROL Update]**: werkt alleen bestaande records bij (negeert andere records).
* **[!UICONTROL Reconciliation only]**: zoekt naar de record in de database, maar voert geen update uit. Hiermee kunt u bijvoorbeeld de map met ontvangers koppelen om te importeren volgens een kolom van het bestand zonder de gegevens in de mappen bij te werken.
* **[!UICONTROL Deletion]**: hiermee kunt u records in de database vernietigen.

De volgende opties zijn beschikbaar voor elk veld in de tabel waarop de invoer betrekking heeft:

* **[!UICONTROL Update (empty) if source value is empty]**: in het geval van een update verwijdert de waarde in het veld de databasewaarde als het veld leeg is in het bronbestand. Anders wordt het databaseveld bewaard.
* **[!UICONTROL Update only if destination is empty]**: de waarde van het bronbestand overschrijft de waarde in het databaseveld niet, tenzij het databaseveld leeg is. In dat geval wordt de waarde van het bronbestand gebruikt.
* **[!UICONTROL Update the field only when the record is inserted]**: tijdens een update- of invoegbewerking worden alleen nieuwe bronbestandsrecords geïmporteerd.

>[!NOTE]
>
>De definitie van een verzoeningssleutel is altijd **verplicht**, behalve in geval van invoeging zonder deduplicatie.

### Afstemmingssleutels {#reconciliation-keys}

Er moet ten minste één afstemmingssleutel worden ingevuld om deduplicatie te beheren.

Een afstemmingssleutel is een set velden die wordt gebruikt om een record te identificeren. Als u bijvoorbeeld ontvangers wilt importeren, kan de afstemmingssleutel het rekeningnummer, het veld E-mail of de velden Achternaam, Voornaam, Bedrijf zijn, enzovoort.

In dit geval vergelijkt de importengine de waarden van het bestand met die van de database voor alle velden van de sleutel om te zien of een regel van een bestand overeenkomt met een bestaande ontvanger in de database. Wanneer velden specifiek zijn voor een record, kan een nauwkeurige vergelijking tussen de bron- en de doelgegevens worden uitgevoerd, zodat de integriteit van de gegevens na het importeren wordt gegarandeerd. Een tweede afstemmingssleutel kan worden ingevuld voor dezelfde tabel; deze wordt gebruikt voor de regels waarvan de eerste sleutel leeg is.

Kies geen veld dat tijdens het importeren kan worden gewijzigd. Als dit gebeurt, kan de engine aanvullende records maken.

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

De **[!UICONTROL Management of doubles]** kunt u de deduplicatie van gegevens configureren. Deduplicatie betreft records die meerdere keren worden weergegeven **in het bronbestand** (of bronbestanden in geval van een import van meerdere bestanden), d.w.z. regels waarvoor de velden van de afstemmingssleutel identiek zijn.

* Dubbel beheer in **[!UICONTROL Update]** in de modus (de standaardmodus) wordt geen deduplicatie uitgevoerd. De laatste record heeft daarom prioriteit (omdat deze de gegevens van de voorgaande records bijwerkt). Het tellen van duplicaten wordt niet uitgevoerd in deze modus.
* Dubbel beheer in **[!UICONTROL Ignore]** modus of **[!UICONTROL Reject entity]** Hiermee worden duplicaten van de import uitgesloten. In dit geval wordt geen record geïmporteerd.
* In **[!UICONTROL Reject entity]** in de modus, wordt het element niet geïmporteerd en wordt een fout gegenereerd in de importlogboeken.
* In **[!UICONTROL Ignore]** in de modus, wordt het element niet geïmporteerd, maar wordt geen spoor van de fout behouden. In deze modus kunt u de prestaties optimaliseren.

>[!IMPORTANT]
>
>Deduplicatie wordt alleen in het geheugen uitgevoerd. De omvang van een invoer met deduplicatie is daarom beperkt. De limiet is afhankelijk van verschillende parameters (capaciteit van de toepassingsserver, activiteit, aantal velden in de sleutel, enz.). De maximale grootte voor een deduplicatie is ongeveer 1.000.000 regels.

Deduplicatie heeft betrekking op een record die zowel in het bronbestand als in de database aanwezig is. Het betreft bewerkingen met alleen updates (d.w.z. **[!UICONTROL Update and insertion]** of **[!UICONTROL Update]**). De **[!UICONTROL Duplicate management]** Met deze optie kunt u de record bijwerken of negeren als deze zich in zowel het bronbestand als de database bevindt. De **[!UICONTROL Update or insert based on origin]** Deze optie behoort tot de optionele module en kan niet worden gebruikt in een standaardcontext.

De opties **[!UICONTROL Reject]** en **[!UICONTROL Ignore]** werken zoals hierboven beschreven.

### In geval van fout {#behavior-in-the-event-of-an-error}

De meeste gegevensoverdrachtsbewerkingen genereren verschillende soorten fouten (incoherente regelindeling, ongeldig e-mailadres, enz.). Alle fouten en waarschuwingen die door de importengine worden gegenereerd, worden opgeslagen en gekoppeld aan het importexemplaar.

![](assets/s_ncs_user_import_general_tab.png)

Details van deze afwijzingen kunnen worden bekeken via de **[!UICONTROL Rejects]** tab.

![](assets/s_ncs_user_import_rejets_tab.png)

Er zijn twee typen afwijzing (het type wordt weergegeven in het dialoogvenster **[!UICONTROL Connector]** kolom):

* Afwijzingen van de tekstconnector hebben betrekking op fouten die optreden tijdens het verwerken van de bestandsregel (berekend veld, gegevensanalyse, enz.). In dit geval wordt bij een fout de hele regel altijd geweigerd.
* Afkeuringen van databaseverbindingen hebben betrekking op fouten die optreden tijdens het afstemmen van gegevens of het schrijven naar de database. In het geval van een import naar meerdere tabellen kan de afwijzing alleen betrekking hebben op een deel van de record (bijvoorbeeld bij het importeren van ontvangers en bijbehorende gebeurtenissen kan een fout het bijwerken van een gebeurtenis voorkomen zonder de ontvanger te negeren).

Op de pagina voor het afstemmen van gegevens kunt u het gewenste veld voor het type foutbeheer per veld en tabel per tabel definiëren.

* **[!UICONTROL Ignore and log a warning]**: alle velden worden geïmporteerd in de database, behalve de velden die een fout hebben gegenereerd.
* **[!UICONTROL Reject parent element]**: de gehele regel van de record wordt afgewezen, niet alleen het veld dat een fout heeft veroorzaakt.
* **[!UICONTROL Reject all elements]**: de importstop en alle elementen van de record worden geweigerd.

  ![](assets/s_ncs_user_import_wizard04_4.png)

De structuur in het afstotingsscherm van een importinstantie geeft aan welke velden zijn geweigerd en waar de fouten zijn opgetreden.

U kunt een bestand met deze records genereren via het dialoogvenster **[!UICONTROL Export rejects]** pictogram:

![](assets/s_ncs_user_import_errors_export.png)

## Stap 5 - Extra stap bij het importeren van ontvangers {#step-5---additional-step-when-importing-recipients}

In de volgende stap van de wizard Importeren kunt u de map selecteren of maken waarin gegevens worden geïmporteerd, geïmporteerde ontvangers automatisch toewijzen met een (nieuwe of bestaande) lijst en ontvangers abonneren op een service.

![](assets/s_ncs_user_import_wizard05_1.png)

>[!NOTE]
>
>Deze stap wordt alleen weergegeven wanneer u ontvangers importeert en wanneer u de standaardtabel voor Adobe Campaign-ontvangers gebruikt (**nms:ontvanger**).

* Klik op de knop **[!UICONTROL Edit]** koppelingen maken om de map, de lijst of de service te selecteren waaraan u de ontvangers wilt koppelen of zich erop wilt abonneren.

   1. Importeren in een map

      De **[!UICONTROL Edit...]** koppeling van de **[!UICONTROL Import into a folder]** kunt u de map selecteren of maken waarin de ontvangers worden geïmporteerd. Als standaard geen partitie is gedefinieerd, worden de gegevens geïmporteerd in de standaardmap van de operator.

      >[!NOTE]
      >
      >De standaardmap voor een operator is de eerste map waarvoor de operator schrijftoegang heeft. Meer informatie in [Toegangsbeheer voor mappen](../../platform/using/access-management-folders.md).

      Als u de importmap wilt selecteren, klikt u op de pijl rechts van de knop **[!UICONTROL Folder]** en selecteer de desbetreffende map. U kunt ook de opdracht **[!UICONTROL Select link]** om de structuur weer te geven in een nieuw venster of een nieuwe map te maken.

      ![](assets/s_ncs_user_import_wizard05_2.png)

      Als u een nieuwe map wilt maken, selecteert u het knooppunt waaruit u een map wilt toevoegen en klikt u met de rechtermuisknop. Selecteer **[!UICONTROL Create a new 'Recipients' folder]**.

      ![](assets/s_ncs_user_import_wizard05_3.png)

      De map wordt toegevoegd onder het huidige knooppunt. Voer de naam van de nieuwe map in, klik op Enter om te bevestigen en klik vervolgens op **[!UICONTROL OK]**.

      ![](assets/s_ncs_user_import_wizard05_4.png)

   1. Koppelen aan een lijst

      De **[!UICONTROL Edit...]** in de **[!UICONTROL Add recipients to a list]** kunt u een lijst selecteren of maken waarin de ontvangers worden geïmporteerd.

      ![](assets/s_ncs_user_import_wizard05_5.png)

      U kunt een nieuwe lijst voor deze ontvangers maken door op **[!UICONTROL Select link]** vervolgens **[!UICONTROL Create]**. De opstelling en het beheer van lijsten worden weergegeven in [deze sectie](../../platform/using/creating-and-managing-lists.md).

      ![](assets/s_ncs_user_import_wizard05_6.png)

      U kunt besluiten om de ontvangers aan degenen toe te voegen die reeds in een lijst aanwezig zijn, of de lijst met de nieuwe ontvangers opnieuw te maken. In dit geval worden ontvangers verwijderd en vervangen door de geïmporteerde ontvangers als de lijst al ontvangers bevatte.

   1. Abonneren op een service

      Als u alle geïmporteerde ontvangers wilt abonneren op een inlichtingenservice, klikt u op de knop **[!UICONTROL Edit...]** koppeling van de **[!UICONTROL Subscribe recipients to a service]** om de informatiedienst te selecteren of te creëren waarop de ontvangers zullen worden geabonneerd. U kunt de **[!UICONTROL Send a confirmation message]** optie: De inhoud van dit bericht wordt bepaald in het leveringsmalplaatje verbonden aan de abonnementsdienst.

      ![](assets/s_ncs_user_import_wizard05_7.png)

      U kunt een nieuwe service voor deze ontvangers maken door op **[!UICONTROL Select link]** en vervolgens de **[!UICONTROL Create]** pictogram. Het beheer van de informatiediensten is te vinden in [deze sectie](../../delivery/using/managing-subscriptions.md).

* Gebruik de **[!UICONTROL Origin]** veld voor het toevoegen van informatie over de oorsprong van ontvangers aan hun profielen. Deze informatie is met name nuttig in het kader van een meervoudige import.

Klikken **[!UICONTROL Next]** om deze stap te valideren en de volgende stap weer te geven.

## Stap 6 - Het importeren starten {#step-6---launching-the-import}

In de laatste stap van de wizard kunt u gegevensimport starten. Om dit te doen, klik **[!UICONTROL Start]** knop.

![](assets/s_ncs_user_import_wizard06_1.png)

U kunt vervolgens de uitvoering van de importtaak controleren (zie [Uitvoering van taken controleren](../../platform/using/monitoring-jobs-execution.md).
