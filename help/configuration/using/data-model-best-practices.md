---
title: De klassieke-ontvangertabel van Adobe Campagne gebruiken
description: Leer hoe u de tabel met ontvangers buiten de doos in Adobe Campagne Classic kunt gebruiken bij het ontwerpen van uw gegevensmodel.
page-status-flag: never-activated
uuid: faddde15-59a1-4d2c-8303-5b3e470a0c51
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: schema-reference
discoiquuid: 5957b39e-c2c6-40a2-b81a-656e9ff7989c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 15581517df8d2f397285bbadebd83b7f4539dfd7
workflow-type: tm+mt
source-wordcount: '3997'
ht-degree: 0%

---


# Aanbevolen werkwijzen voor gegevensmodellen{#data-model-best-practices}

In dit document worden belangrijke aanbevelingen beschreven tijdens het ontwerpen van uw Adobe Campagne-gegevensmodel.

Raadpleeg de sectie Klassieke [gegevensmodel](../../configuration/using/about-data-model.md) van Campagne voor een beter begrip van geïntegreerde tabellen en hun interactie.

Lees [deze documentatie](../../configuration/using/about-schema-reference.md) om aan de slag te gaan met campagnereschema&#39;s. Leer hoe u extensieschema&#39;s configureert om het conceptuele gegevensmodel van de Adobe Campagne-database uit te breiden in [dit document](../../configuration/using/about-schema-edition.md).

## Overzicht {#overview}

Het Adobe Campagne-systeem is bijzonder flexibel en kan worden uitgebreid tot na de initiële implementatie. Hoewel de mogelijkheden oneindig zijn, is het echter van essentieel belang om verstandige beslissingen te nemen en sterke fundamenten te leggen voor het ontwerpen van uw gegevensmodel.

In dit document worden veelgebruikte praktijkvoorbeelden en tips en trucs gegeven voor het op de juiste wijze maken van uw Adobe-campagne.

## Gegevensmodelarchitectuur {#data-model-architecture}

Adobe Campaign Standard is een krachtig campagnebeheersysteem voor meerdere kanalen waarmee u uw online- en offlinestrategieën kunt uitlijnen en persoonlijke ervaringen voor klanten kunt creëren.

### klantgerichte benadering {#customer-centric-approach}

Hoewel de meeste e-mailserviceproviders via een op lijst gerichte benadering communiceren met klanten, is Adobe Campaign afhankelijk van een relationele database om een bredere visie op de klanten en hun kenmerken te kunnen gebruiken.

Deze klantgerichte benadering wordt getoond in de grafiek hieronder. De grijze tabel **Ontvanger** vertegenwoordigt de hoofdtabel van de klant waarin alles wordt samengesteld:

![](assets/customer-centric-data-model.png)

Om tot de beschrijving van elke lijst toegang te hebben, ga naar **[!UICONTROL Admin > Configuration > Data schemas]**, selecteer een middel van de lijst en klik de **[!UICONTROL Documentation]** tabel.

Het standaardgegevensmodel van de Campagne van Adobe wordt voorgesteld in [dit document](../../configuration/using/data-model-description.md).

>[!NOTE]
>
>Met Adobe Campaign Classic kunt u een aangepaste klantentabel maken. In de meeste gevallen wordt echter aanbevolen de standaard [ontvangertabel](../../configuration/using/about-data-model.md#default-recipient-table) te gebruiken, die al vooraf gebouwde aanvullende tabellen en functies bevat.

### Gegevens voor Adobe-campagne {#data-for-campaign}

Welke gegevens moeten naar Adobe Campaign worden verzonden? Het is van essentieel belang om de gegevens te bepalen die nodig zijn voor uw marketingactiviteiten.

>[!NOTE]
>
>Adobe Campaign is geen gegevenspaket of rapportagetool. Probeer daarom niet alle mogelijke klanten en de bijbehorende informatie te importeren in Adobe Campagne of gegevens te importeren die alleen worden gebruikt om rapporten samen te stellen.

Als u wilt bepalen of een kenmerk al dan niet nodig is in Adobe Campaign, vraagt u zich af of het kenmerk onder een van de volgende categorieën valt:

* Kenmerk dat wordt gebruikt voor **segmentatie**
* Kenmerk dat wordt gebruikt voor **gegevensbeheerprocessen** (bijvoorbeeld geaggregeerde berekening)
* Kenmerk dat wordt gebruikt voor **personalisatie**

Als er niet in een van deze elementen valt, hebt u dit kenmerk waarschijnlijk niet nodig in Adobe Campaign.

### Keuze van gegevenstypen {#data-types}

Volg de onderstaande aanbevolen procedures om gegevens in te stellen in Adobe Campagne voor een goede architectuur en goede prestaties van uw systeem.

* Een grote tabel moet meestal numerieke velden bevatten en koppelingen naar referentietabellen bevatten (wanneer u werkt met een lijst met waarden).
* Met het kenmerk **expr** kunt u een schemakenmerk definiëren als een berekend veld in plaats van als een fysieke setwaarde in een tabel. Op deze manier hebt u toegang tot informatie in een andere indeling (bijvoorbeeld voor leeftijd en geboortedatum) zonder dat u beide waarden hoeft op te slaan. Dit is een goede manier om te voorkomen dat velden worden gedupliceerd. De tabel Ontvanger gebruikt bijvoorbeeld een expressie voor het domein, die al aanwezig is in het e-mailveld.
* Wanneer de expressieberekening echter complex is, wordt het niet aanbevolen het kenmerk **expr** te gebruiken omdat de berekening ter plekke de prestaties van uw query&#39;s kan beïnvloeden.
* Het type **XML** is een goede manier om te voorkomen dat u te veel velden maakt. Maar het neemt ook schijfruimte op aangezien het een kolom CLOB in het gegevensbestand gebruikt. Het kan ook tot complexe SQL vragen leiden en prestaties kunnen beïnvloeden.
* De lengte voor een **tekenreeksveld** moet altijd met de kolom worden gedefinieerd. Standaard is de maximumlengte in Adobe Campaign 255, maar Adobe raadt u aan het veld korter te houden als u al weet dat de grootte een kortere lengte niet overschrijdt.
* Een veld dat korter is in Adobe Campaign is dan in het bronsysteem, is acceptabel als u zeker weet dat de grootte in het bronsysteem is overschat en niet wordt bereikt. Dit kan een kortere tekenreeks of een kleiner geheel getal in Adobe Campagne betekenen.

### Keuze van velden {#choice-of-fields}

Een veld moet in een tabel worden opgeslagen als het een doel of een doel voor personalisatie heeft. Met andere woorden, als een veld niet wordt gebruikt om een gepersonaliseerde e-mail te verzenden of als criterium wordt gebruikt in een query, neemt het schijfruimte in beslag terwijl het nutteloos is.

Voor hybride en op-gebouw instanties, behandelt FDA (Federated Data Access, een facultatieve eigenschap die om tot externe gegevens) toegang te hebben de behoefte om een gebied &quot;op-de&quot;tijdens een campagneproces toe te voegen. U hoeft niet alles te importeren als u FDA hebt. Voor meer op dit, zie [over Federated Toegang](../../platform/using/about-fda.md)van Gegevens.

### Keuze van sleutels {#choice-of-keys}

Naast de **automatische controle** die door gebrek in de meeste lijsten wordt bepaald, zou u moeten overwegen wat logische of bedrijfssleutels (rekeningsaantal, cliëntaantal, etc.) toe te voegen. Het kan later worden gebruikt voor invoer/verzoening of gegevenspakketten. Zie [Id&#39;s](#identifiers)voor meer informatie hierover.

Efficiënte toetsen zijn essentieel voor de prestaties. Numerieke gegevenstypen verdienen altijd de voorkeur als toetsen voor tabellen.

Voor het gegevensbestand SQLServer, kon u het gebruiken van &quot;gegroepeerde index&quot;overwegen als de prestaties nodig zijn. Omdat Adobe dit niet afhandelt, moet u het maken in SQL.

### Speciale tabelruimten {#dedicated-tablespaces}

Met het kenmerk tabelruimte in het schema kunt u een specifieke tabelruimte voor een tabel opgeven.

Met de installatiewizard kunt u objecten opslaan op type (gegevens, tijdelijk en index).

Speciale tabelruimten zijn beter voor partitionering, beveiligingsregels en bieden vloeiend en flexibel beheer, betere optimalisatie en prestaties.

## Id&#39;s {#identifiers}

Bronnen voor Adobe Campagne hebben drie id&#39;s en u kunt een extra id toevoegen.

In de volgende tabel worden deze id&#39;s en hun doel beschreven.

| Id | Beschrijving | Aanbevolen procedures |
|--- |--- |--- |
| Id | <ul><li>De id is de fysieke primaire sleutel van een Adobe Campagne-tabel. Voor out-of-the-box lijsten, is het een geproduceerd aantal met 32 bits van een opeenvolging</li><li>Deze id is gewoonlijk uniek voor een specifieke Adobe Campagne-instantie. </li><li>Een automatisch gegenereerde id kan zichtbaar zijn in een schemadefinitie. Zoek in het *attribuut &quot;* true&quot; van de automatische controle.</li></ul> | <ul><li>Automatisch gegenereerde id&#39;s mogen niet worden gebruikt als een referentie in een workflow of in een pakketdefinitie.</li><li>Er mag niet worden aangenomen dat de id altijd een toenemend aantal zal zijn.</li><li>De id in een tabel buiten het vak is een 32-bits getal en dit type mag niet worden gewijzigd. Dit nummer is afkomstig uit een &#39;reeks&#39; die in de sectie met dezelfde naam is opgenomen.</li></ul> |
| Naam (of interne naam) | <ul><li>Deze informatie is een unieke id van een record in een tabel. Deze waarde kan handmatig worden bijgewerkt, meestal met een gegenereerde naam.</li><li>Deze id behoudt de waarde wanneer deze wordt geïmplementeerd in een andere instantie van Adobe Campaign en mag niet leeg zijn.</li></ul> | <ul><li>Wijzig de naam van de record die wordt gegenereerd door Adobe Campaign als het object moet worden geïmplementeerd vanuit een omgeving naar een andere.</li><li>Wanneer een object een naamruimteattribuut heeft (bijvoorbeeld *schema* ), wordt deze gemeenschappelijke naamruimte benut voor alle aangepaste objecten die zijn gemaakt. Bepaalde gereserveerde naamruimten mogen niet worden gebruikt: *nms*, *xtk*.</li><li>Wanneer een object geen naamruimte heeft (bijvoorbeeld *workflow* of *levering* ), wordt dit naamruimtebegrip toegevoegd als voorvoegsel van een intern naamobject: *namespaceMyObjectName*.</li><li>Gebruik geen speciale tekens zoals spatie &quot;&quot;, puntkolom &quot;:&quot; of afbreekstreepje &quot;-&quot;. Al deze tekens worden vervangen door een onderstrepingsteken &quot;_&quot; (toegestaan teken). &quot;abc-def&quot; en &quot;abc:def&quot; worden bijvoorbeeld opgeslagen als &quot;abc_def&quot; en worden elkaar overschreven.</li></ul> |
| Label | <ul><li>Het label is de bedrijfsidentificatie van een object of record in Adobe Campaign.</li><li>Voor dit object zijn spaties en speciale tekens toegestaan.</li><li>Het garandeert niet dat een record uniek is.</li></ul> | <ul><li>Het wordt aanbevolen een structuur voor de objectlabels te bepalen.</li><li>Dit is de meest gebruikersvriendelijke oplossing om een record of object voor een Adobe Campagnegebruiker te identificeren.</li></ul> |

## Aangepaste interne sleutels {#custom-internal-keys}

Voor elke tabel die u in Adobe Campaign maakt, zijn primaire sleutels vereist.

De meeste organisaties voeren verslagen van externe systemen in. Terwijl de fysieke sleutel van de Ontvangerlijst het &quot;id&quot;attribuut is, is het mogelijk om een douanetoets extra te bepalen.

Deze aangepaste sleutel is de primaire sleutel voor de feitelijke record in het externe systeem dat Adobe Campagne voert.

Wanneer een out-of-the-box lijst zowel een automatische als een interne sleutel heeft, zal de interne sleutel als unieke index in de fysieke gegevensbestandlijst worden geplaatst.

Bij het maken van een aangepaste tabel hebt u twee opties:
* Een combinatie van automatisch gegenereerde sleutel (id) en interne sleutel (aangepast). Deze optie is interessant als uw systeemsleutel een samengestelde sleutel of niet een geheel is. Geheel getal zorgt voor hogere prestaties in grote tabellen en sluit zich aan bij andere tabellen.
* De primaire sleutel gebruiken als de primaire sleutel van het externe systeem. Deze oplossing heeft doorgaans de voorkeur, omdat deze de aanpak van het importeren en exporteren van gegevens vereenvoudigt, met een consistente sleutel tussen verschillende systemen. De autopk zou moeten worden onbruikbaar gemaakt als de sleutel &quot;id&quot;wordt genoemd en met externe waarden (niet auto-geproduceerd) zou moeten worden gevuld.

>[!IMPORTANT]
>
>Een automatische piloot mag niet worden gebruikt als referentie in werkstromen.

## Reeksen {#sequences}

De primaire sleutel van de Campagne van Adobe is auto-geproduceerde identiteitskaart voor alle uit-van-de-doos lijsten en kan het zelfde voor douanetabellen zijn. Zie [deze sectie](#identifiers)voor meer informatie.

Deze waarde is ontleend aan wat een **opeenvolging** wordt genoemd, die een gegevensbestandvoorwerp is dat wordt gebruikt om een aantalopeenvolging te produceren.

Er zijn twee typen reeksen:
* **Gedeeld**: meerdere tabellen zouden hun id uit dezelfde reeks kiezen . Dit betekent dat als id &#39;X&#39; door één tabel wordt gebruikt, geen andere tabel die dezelfde reeks deelt, een record met die id &#39;X&#39; heeft. **XtkNewId** is de standaard gedeelde reeks die beschikbaar is in Adobe Campaign.
* **Specifiek**: maar één tafel haalt zijn id uit de reeks . De reeksnaam bevat gewoonlijk de tabelnaam.

>[!IMPORTANT]
>
>De reeks bestaat uit een geheel 32-bits waarde, met een eindig maximum aantal beschikbare waarden: 2,14 miljard. Nadat de maximumwaarde is bereikt, gaat de reeks terug naar 0 om id&#39;s te recyclen.
>
>Als de oude gegevens niet zijn gewist, is het resultaat een unieke-sleutelfout, die een blokkering wordt voor de gezondheid en het gebruik van het platform. Adobe Campagne zou geen communicatie kunnen verzenden (wanneer het leveringstabel beïnvloedt) en de prestaties zouden zeer worden beïnvloed.

Een klant die jaarlijks 6 miljard e-mails met een bewaartermijn van 180 dagen voor zijn logboeken verzendt, zou daarom in 4 maanden niet meer in de tijd zijn. Om een dergelijke uitdaging te voorkomen, moet u de instellingen voor leegmaken aanpassen aan uw volumes. Zie [deze sectie](#data-retention)voor meer informatie.

Wanneer een aangepaste tabel wordt gemaakt in Adobe Campaign met een primaire sleutel als een autoPK, moet er systematisch een aangepaste, toegewijde reeks aan die tabel worden gekoppeld.

Een aangepaste reeks heeft standaard waarden tussen +1.000 en +2.1BB. Technisch gezien is het mogelijk om een volledig bereik van 4BB te krijgen door negatieve id&#39;s toe te staan. Dit moet met zorg worden gebruikt en er zal één id verloren gaan bij het oversteken van negatieve naar positieve getallen: record 0 wordt doorgaans genegeerd door Adobe Campagne Classic in gegenereerde SQL-query&#39;s.

**Verwante onderwerpen:**
* Zie **dit document** voor meer informatie over de functie voor automatisch genereren [](https://helpx.adobe.com/campaign/kb/sequence_auto_generation.html)van reeksen.
* Kijk naar [deze video](https://helpx.adobe.com/customer-care-office-hours/campaign/sequences-exhaustion-campaign-classic.html)voor meer informatie over de uitputting van reeksen.

## Indexen {#indexes}

Indexen zijn essentieel voor de prestaties. Wanneer u een sleutel in het schema declareert, wordt automatisch een index voor de velden van de sleutel gemaakt. U kunt meer indexen voor vragen ook verklaren die niet de sleutel gebruiken.

Adobe raadt u aan aanvullende indexen te definiëren, omdat dit de prestaties kan verbeteren.

Houd echter rekening met het volgende:

* Het indexgebruik is gebonden aan uw toegangspatroon. Het optimaliseren van indexering is vaak een belangrijk onderdeel van het databaseontwerp en moet door experts worden verwerkt. Het toevoegen van indexen is vaak een herhalende werkstroom verbonden aan gegevensbestandonderhoud. Het wordt gedaan in tijd, stap voor stap, om prestatieskwesties te richten wanneer het gebeuren.
* Met indexen wordt de tabel groter (om de index zelf op te slaan).
* Het toevoegen van index op kolommen kan de prestaties van gegevens verbeteren leest toegang (SELECT), maar het kan de prestaties van gegevens verminderen schrijven toegang (UPDATE).
* Omdat dit de prestaties tijdens het opnemen van gegevens beïnvloedt, zouden de indexen in grootte en aantal moeten worden beperkt.
* Voeg geen indexen toe wanneer dat niet nodig is. Zorg ervoor het wordt vereist en het verhoogt de algemene prestaties van uw vragen (test en leer).
* Over het algemeen is een index efficiënt als u weet dat de query&#39;s niet meer dan 10% van de records terugbrengen.
* Selecteer zorgvuldig de indexen die moeten worden gedefinieerd.
* Native indexen niet uit tabellen buiten de box verwijderen.

<!--When you are performing an initial import with very high volumes of data insert in Adobe Campaign database, it is recommended to run that import without custom indexes at first. It will allow to accelerate the insertion process. Once you’ve completed this important import, it is possible to enable the index(es).-->

### Voorbeeld

Het beheren van indexen kan zeer complex worden, daarom is het belangrijk om te begrijpen hoe zij werken. Om deze ingewikkeldheid te illustreren, nemen een basisvoorbeeld zoals het zoeken ontvangers door op de voornaam en achternaam te filtreren. Dit doet u als volgt:
1. Ga naar de map met alle ontvangers in de database. Zie Profielen [](../../platform/using/managing-profiles.md)beheren voor meer informatie.
1. Klik met de rechtermuisknop op het **[!UICONTROL First name]** veld.
1. Selecteer **[!UICONTROL Filter on this field]**.

   ![](assets/data-model-index-example.png)

1. Herhaal deze bewerking voor het **[!UICONTROL Last name]** veld.

De twee bijbehorende filters worden boven op het scherm toegevoegd.

![](assets/data-model-index-search.png)

U kunt nu zoekfilters toepassen op de velden **[!UICONTROL First name]** **[!UICONTROL Last name]** en op basis van de verschillende filtervoorwaarden.

Nu kunt u indexen toevoegen om het zoeken op deze filters te versnellen. Maar welke indexen moeten worden gebruikt?

>[!NOTE]
>
>Dit voorbeeld is van toepassing op gehoste klanten die een PostSQL-database gebruiken.

In de volgende tabel wordt aangegeven in welke gevallen de drie hieronder beschreven indexen al dan niet worden gebruikt op basis van het toegangspatroon dat in de eerste kolom wordt weergegeven.

| Zoekcriteria | Index 1 (Voornaam + Achternaam) | Index 2 (alleen voornaam) | Index 3 (alleen achternaam) | Opmerkingen |
|--- |--- |--- |--- |--- |
| Voornaam is gelijk aan &quot;Johnny&quot; | Gebruikt | Gebruikt | Niet gebruikt | Aangezien de voornaam zich op de eerste positie op index 1 bevindt, wordt deze toch gebruikt: er hoeft geen criterium aan de achternaam te worden toegevoegd . |
| Voornaam is gelijk aan &quot;Johnny&quot; EN Achternaam is gelijk aan &quot;Smith&quot; | Gebruikt | Niet gebruikt | Niet gebruikt | Aangezien beide attributen in de zelfde vraag worden gezocht, slechts zal de index die beide attributen combineert worden gebruikt. |
| Achternaam is gelijk aan &quot;Smith&quot; | Niet gebruikt | Niet gebruikt | Gebruikt | Er wordt rekening gehouden met de volgorde van de kenmerken in de index. Als u deze volgorde niet aanpast, wordt de index mogelijk niet gebruikt. |
| Voornaam begint met &quot;Joh&quot; | Gebruikt | Gebruikt | Niet gebruikt | Met &#39;Links zoeken&#39; worden indexen ingeschakeld. |
| Voornaam eindigt met &#39;nny&#39; | Niet gebruikt | Niet gebruikt | Niet gebruikt | Met de optie &quot;Rechts zoeken&quot; worden indexen uitgeschakeld en wordt een volledige scan uitgevoerd. Bepaalde specifieke indextypen kunnen dit gebruik van hoofdletters en kleine letters afhandelen, maar zijn niet standaard beschikbaar in Adobe Campagne. |
| Voornaam bevat &quot;John&quot; | Niet gebruikt | Niet gebruikt | Niet gebruikt | Dit is een combinatie van &#39;links&#39;- en &#39;rechts&#39;-zoekopdrachten. Wegens het laatste, zal het indexen onbruikbaar maken en een volledige aftasten zal worden uitgevoerd. |
| Voornaam is gelijk aan &quot;john&quot; | Niet gebruikt | Niet gebruikt | Niet gebruikt | Indexen zijn hoofdlettergevoelig. Als u deze niet hoofdlettergevoelig wilt maken, moet u een specifieke index maken die een SQL-functie bevat, zoals &quot;upper(firstname)&quot;. U moet hetzelfde doen met andere gegevenstransformaties, zoals &quot;unaccent(firstname)&quot;. |

## Koppelingen en kardinaliteit {#links-and-cardinality}

### Koppelingen {#links}

Let op de &#39;eigen&#39; integriteit voor grote tabellen. Als u records verwijdert die brede tabellen in &#39;eigen&#39; integriteit hebben, kan de instantie worden gestopt. De tabel is vergrendeld en de verwijderingen worden een voor een gemaakt. Het is dus beter om &quot;neutrale&quot;integriteit op kindlijsten te gebruiken die grote volumes hebben.

Het declareren van een koppeling als externe verbinding is niet geschikt voor de prestaties. De nul-id verslag emuleert de externe aansluit zich aan bij functionaliteit. Het is niet nodig om externe verbindingen te verklaren als de verbinding de automatisch uitgevoerde controle gebruikt.

Hoewel u zich kunt aansluiten bij een tabel in een workflow, raadt Adobe aan om gemeenschappelijke koppelingen tussen bronnen rechtstreeks in de definitie van de gegevensstructuur te definiëren.

De verbinding zou in groepering met de daadwerkelijke gegevens in uw lijsten moeten worden bepaald. Een verkeerde definitie kan van invloed zijn op gegevens die via koppelingen zijn opgehaald, bijvoorbeeld gegevens die onverwacht worden gedupliceerd.

Geef de koppeling een naam die consistent is met de tabelnaam: de naam van de koppeling moet helpen begrijpen wat de verre tabel is.

Geef een koppeling met &quot;id&quot; geen naam als achtervoegsel. Geef de naam bijvoorbeeld &quot;transactie&quot; en niet &quot;transactie-id&quot;.

Standaard wordt in Adobe Campagne een koppeling gemaakt met de primaire sleutel van de externe tabel. Voor meer duidelijkheid, is het verkieslijk om uitdrukkelijk te bepalen toetreedt in de verbindingsdefinitie.

Er wordt een index toegevoegd aan de kenmerken die in een koppeling worden gebruikt.

De gemaakte en laatst gewijzigde koppelingen zijn aanwezig in veel tabellen. Het is mogelijk om de index onbruikbaar te maken door het attribuut noDbIndex op de verbinding te gebruiken, als deze informatie niet door de zaken wordt gebruikt.

### Kardinaal {#cardinality}

Wanneer u een verbinding ontwerpt, zorg ervoor dat het doelverslag uniek is wanneer een 1-1 verhouding is verklaard. Anders kan verbinden veelvoudige verslagen terugkeren wanneer slechts één wordt verwacht. Dit resulteert in fouten tijdens leveringsvoorbereiding wanneer de vraag meer rijen dan verwacht terugkeert. Stel de naam van de koppeling in op dezelfde naam als het doelschema.

Definieer een koppeling met een kardinaliteit (1-N) in het schema aan de (1) zijde. De relatie Ontvanger (1) - (N) Transactie moet bijvoorbeeld in het transactieschema worden gedefinieerd.

Een omgekeerde kardinaliteit van een koppeling is standaard (N). Het is mogelijk om een verbinding (1-1) te bepalen door de attributen revCardinality=&#39;single&quot;aan de verbindingsdefinitie toe te voegen.

Als de omgekeerde verbinding niet aan de gebruiker zichtbaar zou moeten zijn, kunt u het met de verbindingsdefinitie revLink=&#39;_NONE_&#39; verbergen. Een goed gebruiksgeval voor dit is een verbinding van ontvanger aan de laatste uitgevoerde transactie te bepalen bijvoorbeeld. U hoeft alleen de koppeling van de ontvanger naar de laatste transactie te zien en er is geen omgekeerde koppeling vereist om zichtbaar te zijn vanuit de transactietabel.

Koppelingen die een externe verbinding (1-0..1) uitvoeren, moeten met de nodige voorzichtigheid worden gebruikt omdat dit van invloed is op de systeemprestaties.

## Bewaren van gegevens - opschonen en wissen {#data-retention}

Adobe Campaign is geen gegevenspaket of rapportagetool. Daarom moet de databasegroei onder controle blijven om de goede prestaties van de Adobe Campagne-oplossing te garanderen. Om dit te bereiken, kan het volgen van een aantal van de onderstaande beste praktijken helpen.

Standaard hebben de leverings- en trackinglogboeken van Adobe Campagne een retentieduur van 180 dagen. Een schoonmaakproces loopt om het even welk logboek ouder dan dat te verwijderen.

* Als u logboeken langer wilt houden, zou dit besluit zorgvuldig afhankelijk van de gegevensbestandgrootte en het volume van verzonden berichten moeten worden genomen. Ter herinnering, de opeenvolging van de Campagne van Adobe is een geheel met 32 bits.
* Aanbevolen wordt niet meer dan 1 miljard records tegelijk in deze tabellen te hebben (ongeveer 50% van de 2,14 miljard beschikbare ids) om het risico van het gebruik van alle beschikbare id&#39;s te beperken. Dit zal voor sommige klanten vereisen om de bewaarduur onder 180 dagen te verminderen.

>[!IMPORTANT]
>
>Aangepaste tabellen worden niet gewist met het standaardopschoonproces. Hoewel dit niet op dag één vereist zou kunnen zijn, vergeet niet om een zuiveringsproces voor uw douanetabellen te bouwen aangezien dit tot prestatiesuitdagingen zou kunnen leiden.

Er zijn een paar oplossingen om de behoefte aan verslagen in de Campagne van Adobe te minimaliseren:
* Exporteer de gegevens in een gegevensopslagruimte buiten de Adobe-campagne.
* Genereer geaggregeerde waarden die minder ruimte gebruiken en toch voldoende zijn voor uw marketingactiviteiten. U hebt bijvoorbeeld niet de volledige transactiegeschiedenis van klanten in Adobe Campaign nodig om de laatste aankopen bij te houden.

U kunt het kenmerk &quot;deleteStatus&quot; in een schema declareren. Het is efficiënter om het verslag te merken zoals geschrapt, dan de schrapping in de schoonmaakbeurt uit te stellen taak.

## Prestaties {#performance}

Volg onderstaande aanbevolen procedures om te zorgen voor betere prestaties op elk gewenst moment.

### Algemene aanbevelingen {#general-recommendations}

* Gebruik geen bewerkingen zoals &quot;CONTAINS&quot; in query&#39;s. Als u weet waarvoor wordt verwacht en waarvoor wordt gefilterd, past u dezelfde voorwaarde toe met een &quot;GELIJK AAN&quot; of andere specifieke filteroperatoren.
* Vermijd het samenvoegen met niet-geïndexeerde velden terwijl u gegevens samenstelt in workflows.
* Probeer en zorg ervoor de processen zoals de invoer en de uitvoer van bedrijfsuren gebeuren.
* Zorg ervoor dat er een schema is voor alle dagelijkse activiteiten en houd zich aan het schema.
* Als een of weinig van de dagelijkse processen mislukken en als het verplicht is om het op die zelfde dag in werking te stellen, zorg ervoor er geen conflicterende processen lopen wanneer het handproces wordt opgeheven aangezien dit de systeemprestaties zou kunnen beïnvloeden.
* Zorg ervoor dat de dagelijkse campagne niet wordt uitgevoerd tijdens het importproces of wanneer een handmatig proces wordt uitgevoerd.
* Gebruik een of meer referentietabellen in plaats van een veld in elke rij te dupliceren. Wanneer u sleutel-/waardeparen gebruikt, verdient het de voorkeur een numerieke sleutel te kiezen.
* Een korte tekenreeks blijft acceptabel. Als referentietabellen al in een extern systeem zijn geïnstalleerd, kunt u dit hergebruiken om de gegevensintegratie met Adobe Campagne te vergemakkelijken.

### Een-op-veel relaties {#one-to-many-relationships}

* Gegevensontwerp beïnvloedt bruikbaarheid en functionaliteit. Als u uw gegevensmodel met vele één-aan-vele verhoudingen ontwerpt, maakt het voor gebruikers moeilijker om zinvolle logica in de toepassing te construeren. Een-op-veel filterlogica kan voor niet-technische marketers moeilijk zijn om correct te construeren en te begrijpen.
* Het is goed om alle essentiële gebieden in één lijst te hebben omdat het het voor gebruikers gemakkelijker maakt om vragen te bouwen. Soms is het ook handig om bepaalde velden te dupliceren naar andere tabellen als u samenvoeging kunt voorkomen.
* Bepaalde ingebouwde functies kunnen niet verwijzen naar een-op-een-relatie, zoals de formule en levering van de Afweging van aanbiedingen.

## Grote tabellen {#large-tables}

Adobe Campaign is afhankelijk van externe databasemotoren. Afhankelijk van de leverancier, kan het optimaliseren van prestaties voor grotere lijsten een specifiek ontwerp vereisen.

Hieronder vindt u een aantal aanbevolen procedures die moeten worden gevolgd bij het ontwerpen van uw gegevensmodel met behulp van grote tabellen en complexe verbindingen.

* Wanneer het gebruiken van extra douane ontvankelijke lijsten, zorg ervoor u een specifieke logboeklijst voor elke leveringsafbeelding hebt.
* Verminder het aantal kolommen, met name door de kolommen te identificeren die niet worden gebruikt.
* Optimaliseer de relaties van het gegevensmodel door complexe verbindingen, zoals verbindingen op verschillende voorwaarden en/of meerdere kolommen te vermijden.
* Voor verbindingssleutels, gebruik altijd numerieke gegevens eerder dan karakterkoorden.
* Verminder zoveel u de diepte van logboekbehoud kunt. Als u een diepere geschiedenis nodig hebt, kunt u berekeningen samenvoegen en/of aangepaste logboektabellen verwerken om de grotere geschiedenis op te slaan.

### Grootte van tabellen {#size-of-tables}

De tabelgrootte is een combinatie van het aantal records en het aantal kolommen per record. Beide kunnen de prestaties van vragen beïnvloeden.

* Een **kleine tabel** is vergelijkbaar met de leveringstabel.
* Een tabel van **gemiddelde grootte** is hetzelfde als de grootte van de tabel Ontvanger. Het heeft één verslag per klant.
* Een **grote** tabel lijkt op de grote logtabel. Het heeft vele verslagen per klant.
Bijvoorbeeld, als uw gegevensbestand 10 miljoen ontvangers bevat, bevat de Grote logboeklijst ongeveer 100 tot 200 miljoen berichten, en de lijst van de Levering bevat een paar duizend verslagen.

Voor PostgreSQL, zou een rij 8 KB moeten niet overschrijden om [TOAST](https://wiki.postgresql.org/wiki/TOAST) mechanisme te vermijden. Probeer daarom om het aantal kolommen en de grootte van elke rij zo veel mogelijk te verminderen om optimale prestaties van het systeem (geheugen en cpu) te bewaren.

Het aantal rijen heeft ook invloed op de prestaties. De Adobe Campagne-database is niet ontworpen voor het opslaan van historische gegevens die niet actief worden gebruikt voor het maken van doelen of persoonlijke instellingen. Dit is een operationele database.

Om prestatieskwestie te verhinderen met betrekking tot het hoge aantal rijen, slechts de noodzakelijke verslagen in het gegevensbestand houden. Alle andere records moeten worden geëxporteerd naar een extern gegevenspakhuis en uit de operationele database van Adobe Campagne worden verwijderd.

Hier volgen enkele tips en trucs voor de grootte van tabellen:

* Ontwerp grote tabellen met minder velden en meer numerieke gegevens.
* Gebruik geen groot aantal kolommen (bijv. Int64) om kleine aantallen zoals booleaanse waarden op te slaan.
* Verwijder niet-gebruikte kolommen uit de tabeldefinitie.
* Bewaar geen historische of inactieve gegevens in uw Adobe Campagne-database (exporteren en opschonen).

Hier volgt een voorbeeld:

![](assets/transaction-table-example.png)

In dit voorbeeld:
* De tabellen *Transactie* en *Transactie-item* zijn groot: meer dan 10 miljoen.
* De tabellen *Product* en *Winkel* zijn kleiner: minder dan 10.000.
* Het etiket en de referentie van het product zijn in de *producttabel* opgenomen.
* De tabel *Transactie-item* heeft alleen een koppeling naar de tabel *Product* . Deze tabel is numeriek.

<!--For more detailed best practices on how to optimize the database design for larger volumes, see [Campaign Classic Data model Best practices](https://helpx.adobe.com/campaign/kb/acc-data-model-best-practices.html).-->