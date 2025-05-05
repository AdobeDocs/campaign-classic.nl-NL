---
product: campaign
title: Formulierstructuur
description: Formulierstructuur
feature: Application Settings
role: Data Engineer, Developer
badge-v8: label="Ook van toepassing op v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
exl-id: e61f2b63-06d3-4b8c-867f-1c729176d2da
source-git-commit: 0fba6a2ad4ffa864e2f726f241aa9d7cd39072a6
workflow-type: tm+mt
source-wordcount: '2398'
ht-degree: 0%

---

# Formulierstructuur{#form-structure}



De beschrijving van een vorm is een gestructureerd document van XML dat de grammatica van het vormschema **xtk waarneemt:vorm**.

Het document van XML van de inputvorm moet het `<form>` wortelelement met de **naam** en **namespace** attributen bevatten om de vormnaam en namespace te bevolken.

```xml
<form name="form_name" namespace="name_space">
…
</form>
```

Een formulier is standaard gekoppeld aan het gegevensschema met dezelfde naam en naamruimte. Om een vorm met een verschillende naam te associëren, plaats het **entiteit-schema** attribuut van het `<form>` element aan de naam van de schemasleutel. Als u de structuur van een invoerformulier wilt illustreren, kunt u een interface beschrijven met het voorbeeldschema &quot;focus:receiver&quot;:

```xml
<srcSchema name="recipient" namespace="cus">
  <enumeration name="gender" basetype="byte">    
    <value name="unknown" label="Not specified" value="0"/>    
    <value name="male" label="Male" value="1"/>   
    <value name="female" label="Female" value="2"/>   
  </enumeration>

  <element name="recipient">
    <attribute name="email" type="string" length="80" label="Email" desc="Email address of recipient"/>
    <attribute name="birthDate" type="datetime" label="Date"/>
    <attribute name="gender" type="byte" label="Gender" enum="gender"/>
  </element>
</srcSchema>
```

Het invoerformulier op basis van het voorbeeldschema:

![](assets/d_ncs_integration_form_exemple1.png)

```xml
<form name="recipient" namespace="cus">
  <input xpath="@gender"/>
  <input xpath="@birthDate"/>
  <input xpath="@email"/>
</form>
```

De beschrijving van de besturingselementen voor bewerken begint bij het hoofdelement van `<form>` . Een uitgeven controle is ingegaan in een **`<input>`** element met het **xpath** attribuut dat de weg van het gebied in zijn schema bevat.

Het bewerkingsbesturingselement past zich automatisch aan het overeenkomstige gegevenstype aan en gebruikt het label dat in het schema is gedefinieerd.

>[!NOTE]
>
>U kunt het etiket overladen dat in zijn gegevensschema wordt bepaald door het **etiket** attribuut aan het `<input>` element toe te voegen dat:\
>`<input label="Email address" xpath="@name" />`

Elk veld wordt standaard weergegeven op één regel en neemt alle beschikbare ruimte in beslag, afhankelijk van het type gegevens.

## Opmaak {#formatting}

De lay-out van de controles kijkt als lay-out die in HTML lijsten wordt gebruikt, met de mogelijkheid om een controle in verscheidene kolommen te verdelen, interliniërende elementen, of het specificeren van de bezetting van beschikbare ruimte. Houd er echter rekening mee dat u met de opmaak het gebied alleen door verhoudingen kunt opsplitsen. U kunt geen vaste afmetingen voor een object opgeven.

De besturingselementen van het bovenstaande voorbeeld in twee kolommen weergeven:

![](assets/d_ncs_integration_form_exemple2.png)

```xml
<form name="recipient" namespace="cus">
  <container colcount="2">
    <input xpath="@gender"/>
    <input xpath="@birthDate"/>
    <input xpath="@email"/>
  </container>
</form>
```

Het **`<container>`** element met het **colcount** attribuut laat u de vertoning van kindcontroles op twee kolommen dwingen.

Het **colspan** attribuut op een controle breidt de controle door het aantal kolommen uit ingegaan in zijn waarde:

![](assets/d_ncs_integration_form_exemple3.png)

```xml
<form name="recipient" namespace="cus">
  <container colcount="2">
    <input xpath="@gender"/>
    <input xpath="@birthDate"/>
    <input xpath="@email" colspan="2"/>
  </container>
</form> 
```

Door het **type=&quot;kader&quot;** attributen te bevolken, voegt de container een kader rond de kindcontroles met het etiket toe in het **etiket** attribuut:

![](assets/d_ncs_integration_form_exemple4.png)

```xml
<form name="recipient" namespace="cus">
  <container colcount="2" type="frame" label="General">
    <input xpath="@gender"/>
    <input xpath="@birthDate"/>
    <input xpath="@email" colspan="2"/>
  </container>
</form>
```

Een **`<static>`** -element kan worden gebruikt om het invoerformulier op te maken:

![](assets/d_ncs_integration_form_exemple5.png)

```xml
<form name="recipient" namespace="cus">
  <static type="separator" colspan="2" label="General"/>
  <input xpath="@gender"/>
  <input xpath="@birthDate"/>
  <input xpath="@email" colspan="2"/>
  <static type="help" label="General information about recipient with date of birth, gender, and email address." colspan="2"/>
</form>
```

De **`<static>`** markering met het **separator** type laat u een separatorbar met een etiket toevoegen bevat in het **etiket** attribuut.

Er is een Help-tekst toegevoegd met de tag `<static>` met het type Help. De inhoud van de tekst is ingegaan in het **etiket** attribuut.

## Containers {#containers}

Met containers kunt u een set besturingselementen groeperen. Ze worden vertegenwoordigd door het element **`<container>`** . Deze werden hierboven gebruikt om besturingselementen in te delen in meerdere kolommen.

Het **xpath** attribuut op a `<container>` laat u het van verwijzingen voorzien van kindcontroles vereenvoudigen. Het verwijzen naar besturingselementen is dan relatief ten opzichte van het bovenliggende `<container>` -element.

Voorbeeld van een container zonder &quot;xpath&quot;:

```xml
<container colcount="2">
  <input xpath="location/@zipCode"/>
  <input xpath="location/@city"/>
</container>
```

Voorbeeld met de toevoeging van &quot;xpath&quot; aan het element &quot;location&quot;:

```xml
<container colcount="2" xpath="location">
  <input xpath="@zipCode"/>
  <input xpath="@city"/>
</container>
```

### Typen containers {#types-of-container}

Containers worden gebruikt om complexe besturingselementen samen te stellen met een set velden die zijn opgemaakt in pagina&#39;s.

#### Tabcontainer {#tab-container}

Met een tabcontainer worden gegevens op pagina&#39;s opgemaakt die toegankelijk zijn via tabs.

![](assets/d_ncs_integration_form_exemple6.png)

```xml
<container type="notebook">
  <container colcount="2" label="General">
    <input xpath="@gender"/>
    <input xpath="@birthDate"/>
    <input xpath="@email" colspan="2"/>
  </container>
  <container colcount="2" label="Location">
    …
  </container>
</container>
```

De belangrijkste container wordt bepaald door **type= &quot;notitieboekje&quot;** attributen. De lusjes worden verklaard in de kindcontainers, en het etiket van de lusjes wordt bevolkt van het **etiket** attribuut.

![](assets/d_ncs_integration_form_exemple7.png)

>[!NOTE]
>
>A **style=&quot;neer|omhoog** (door gebrek) **&#x200B;**&#x200B;eigenschap dwingt de verticale plaatsing van lusjeetiketten onder of boven de controle. Deze functie is optioneel.
>`<container style="down" type="notebook">  … </container>`

#### Pictogramlijst {#icon-list}

In deze container wordt een verticale pictogrambalk weergegeven waarmee u de pagina&#39;s kunt selecteren die u wilt weergeven.

![](assets/d_ncs_integration_form_exemple8.png)

```xml
<container type="iconbox">
  <container colcount="2" label="General" img="xtk:properties.png">
    <input xpath="@gender"/>
    <input xpath="@birthDate"/>
    <input xpath="@email" colspan="2"/>
  </container>
  <container colcount="2" label="Location" img="nms:msgfolder.png">
    …
  </container>
</container>
```

De belangrijkste container wordt bepaald door **type= &quot; iconbox&quot;** attributen. De pagina&#39;s die aan de pictogrammen zijn gekoppeld, worden gedeclareerd in de onderliggende containers. Het etiket van de pictogrammen wordt bevolkt van het **etiket** attribuut.

Het pictogram van een pagina wordt gevuld vanuit het kenmerk `img="<image>"` , waarbij `<image>` de naam is van de afbeelding die overeenkomt met de sleutel waaruit de naam en naamruimte bestaan (bijvoorbeeld &quot;xtk:properties.png&quot;).

De afbeeldingen zijn beschikbaar via het knooppunt **[!UICONTROL Administration > Configuration > Images]** .

#### Visibility container {#visibility-container}

U kunt een set besturingselementen maskeren via een dynamische voorwaarde.

Dit voorbeeld illustreert de zichtbaarheid van besturingselementen voor de waarde van het veld Geslacht:

```xml
<container type="visibleGroup" visibleIf="@gender=1">
  …
</container>
<container type="visibleGroup" visibleIf="@gender=2">
  …
</container>
```

Een zichtbaarheidscontainer wordt bepaald door de attributen **type= &quot;visibleGroup&quot;**. Het **visibleIf** attribuut bevat de zichtbaarheidsvoorwaarde.

Voorbeelden van syntaxis van voorwaarde:

* **visibleIf= &quot;@email=&#39;peter.martinezATneeolane.net&quot;**: test gelijkheid op koord-type gegevens. De vergelijkingswaarde moet tussen aanhalingstekens staan.
* **visibleIf=&quot;@gender >= 1 en @gender!= 2&quot;**: voorwaarde op een numerieke waarde.
* **visibleIf= &quot;@boolean1=true of @boolean2=false&quot;**: test op de gebieden Van Boole.

#### Container inschakelen {#enabling-container}

Met deze container kunt u een set gegevens in- of uitschakelen vanuit een dynamische voorwaarde. Als u een besturingselement uitschakelt, wordt het niet bewerkt. In het volgende voorbeeld wordt getoond hoe besturingselementen kunnen worden ingeschakeld in het veld &quot;Geslacht&quot;:

```xml
<container type="enabledGroup" enabledIf="@gender=1">
  …
</container>
<container type="enabledGroup" enabledIf="@gender=2">
  …
</container>
```

Een toelatende container wordt bepaald door **type= &quot;enabledGroup&quot;** attributen. Het **enabledIf** attribuut bevat de activeringsvoorwaarde.

## Een koppeling bewerken {#editing-a-link}

Vergeet niet dat een koppeling als volgt in het gegevensschema wordt gedeclareerd:

```xml
<element label="Company" name="company" target="cus:company" type="link"/>
```

De bewerkingscontrole voor de koppeling in de invoervorm is als volgt:

![](assets/d_ncs_integration_form_exemple9.png)

```xml
<input xpath="company"/>
```

Doelselectie is toegankelijk via het bewerkingsveld. Invoer wordt ondersteund door &#39;type-ahead&#39;, zodat een doelelement gemakkelijk kan worden gevonden op basis van de eerste paar ingevoerde tekens. Het onderzoek wordt dan gebaseerd op **verwerkt koord** dat in het gerichte schema wordt bepaald. Als het schema niet bestaat na bevestiging in de controle, wordt een bevestigingsbericht van de verwezenlijking van het on-the-fly doel getoond. De bevestiging leidt tot een nieuw verslag in de doellijst en associeert het met de verbinding.

Een vervolgkeuzelijst wordt gebruikt om een doelelement te selecteren in de lijst met records die al zijn gemaakt.

Met het pictogram **[!UICONTROL Modify the link]** (map) wordt een selectieformulier gestart met de lijst met doelelementen en een filterzone:

![](assets/d_ncs_integration_form_exemple10.png)

Met het pictogram **[!UICONTROL Edit link]** (vergrootglas) wordt de bewerkvorm van het gekoppelde element gestart. Het gebruikte formulier wordt standaard afgetrokken op de sleutel van het doelschema. Het **vorm** attribuut laat u de naam van uitgeven vorm (b.v. &quot;cus:company2&quot;) dwingen.

U kunt de keuze van doelelementen beperken door het element **`<sysfilter>`** toe te voegen van de koppelingsdefinitie in het invoerformulier:

```xml
<input xpath="company">
  <sysFilter>
    <condition expr="[location/@city] =  'Newton"/>
  </sysFilter>
</input>
```

U kunt de lijst ook sorteren met het element **`<orderby>`** :

```xml
<input xpath="company">
  <orderBy>
    <node expr="[location/@zipCode]"/>
  </orderBy>
</input>
```

### Eigenschappen van besturing {#control-properties}

* **noAutoComplete**: maakt type-vooruit (met de waarde &quot;waar&quot; onbruikbaar)
* **createMode**: leidt tot de verbinding op de vlucht als het niet bestaat. Mogelijke waarden zijn:

   * **niets**: maakt verwezenlijking onbruikbaar. Er wordt een foutbericht weergegeven als de koppeling niet bestaat
   * **gealigneerd**: leidt tot de verbinding met de inhoud op uitgeeft gebied
   * **uitgave**: toont uitgeeft vorm op de verbinding. Wanneer het formulier wordt gevalideerd, worden de gegevens opgeslagen (standaardmodus)

* **noZoom**: geen geef vorm op de verbinding uit (met de waarde &quot;waar&quot;)
* **vorm**: overlaadt de Edit vorm van het gerichte element

## Lijst met koppelingen {#list-of-links}

Een verbinding ingegaan in het gegevensschema als inzamelingselement (unbound= &quot;waar&quot;) moet door een lijst gaan om alle elementen te bekijken verbonden aan het.

Het principe bestaat uit het weergeven van de lijst met gekoppelde elementen die zijn geoptimaliseerd voor het laden van gegevens (downloaden via gegevensbatch, alleen uitvoeren van de lijst als deze zichtbaar is).

Voorbeeld van een verzamelingskoppeling in een schema:

```xml
<element label="Events" name="rcpEvent" target="cus:event" type="link" unbound="true">
…
</element>
```

De lijst in de invoervorm:

![](assets/d_ncs_integration_form_exemple11.png)

```xml
 <input xpath="rcpEvent" type="linklist">
  <input xpath="@label"/>
  <input xpath="@date"/>
</input>
```

De controle van de lijst wordt bepaald door **type= &quot;linklist&quot;** attributen. Het lijstpad moet naar de verzamelingskoppeling verwijzen.

De kolommen worden gedeclareerd via de **`<input>`** -elementen van de lijst. Het **xpath** attribuut verwijst naar de weg van het gebied in het doelschema.

Een werkbalk met een label (gedefinieerd op de koppeling in het schema) wordt automatisch boven de lijst geplaatst.

De lijst kan via de **[!UICONTROL Filters]** knoop worden gefiltreerd en worden gevormd om de kolommen toe te voegen en te sorteren.

Met de knoppen **[!UICONTROL Add]** en **[!UICONTROL Delete]** kunt u verzamelingselementen aan de koppeling toevoegen en eruit verwijderen. Standaard wordt bij het toevoegen van een element de bewerkingsvorm van het doelschema gestart.

De **[!UICONTROL Detail]** knoop wordt automatisch toegevoegd wanneer **zoom= &quot;waar&quot;** attribuut op de **`<input>`** markering van de lijst wordt voltooid: het laat u de Edit vorm van de geselecteerde lijn lanceren.

Filteren en sorteren kan worden toegepast wanneer de lijst wordt geladen:

```xml
 <input xpath="rcpEvent" type="linklist">
  <input xpath="@label"/>
  <input xpath="@date"/>
  <sysFilter>
    <condition expr="@type = 1"/>
  </sysFilter>
  <orderBy>
    <node expr="@date" sortDesc="true"/>
  </orderBy>
</input>
```

### Relationeringstabel {#relationship-table}

Met een relatietabel kunt u twee tabellen koppelen aan N-N-kardinaliteit. De relatietabel bevat alleen de koppelingen naar de twee tabellen.

Als u een element aan de lijst toevoegt, kunt u daarom een lijst van een van de twee koppelingen in de relatietabel voltooien.

Voorbeeld van een relatietabel in een schema:

```xml
<srcSchema name="subscription" namespace="cus">
  <element name="recipient" type="link" target="cus:recipient" label="Recipient"/>
  <element name="service" type="link" target="cus:service" label="Subscription service"/>
</srcSchema>
```

Bij ons voorbeeld beginnen we met de invoervorm van het schema &#39;cus:receiver&#39;. De lijst moet de verenigingen met abonnementen aan de diensten tonen en moet u toestaan om een abonnement toe te voegen door een bestaande dienst te selecteren.

![](assets/d_ncs_integration_form_exemple12.png)

```xml
<input type="linklist" xpath="subscription" xpathChoiceTarget="service" xpathEditTarget="service" zoom="true">
  <input xpath="recipient"/>
  <input xpath="service"/>
</input>
```

Het **xpathChoiceTarget** attribuut laat u een selectievorm van de ingegane verbinding lanceren. Het creëren van het verslag van de relatietabel zal automatisch de verbinding aan de huidige ontvanger en de geselecteerde dienst bijwerken.

>[!NOTE]
>
>Het **xpathEditTarget** attribuut laat u het uitgeven van de geselecteerde lijn op de ingegane verbinding dwingen.

### Eigenschappen van List {#list-properties}

* **noToolbar**: verbergt de toolbar (met waarde &quot;waar&quot;)
* **toolbarCaption**: laadt het toolbaretiket over
* **toolbarAlign**: wijzigt de verticale of horizontale meetkunde van de toolbar (mogelijke waarden: &quot;verticaal&quot;|&quot;horizontaal&quot;)
* **img**: toont het beeld verbonden aan de lijst
* **vorm**: overlaadt de Edit vorm van het gerichte element
* **gezoem**: voegt de **[!UICONTROL Zoom]** knoop toe om het gerichte element uit te geven
* **xpathEditTarget**: reeksen die op de ingegane verbinding uitgeven
* **xpathChoiceTarget**: voor toevoeging, lanceert de selectievorm op de ingegane verbinding

## Besturingselementen geheugenlijst {#memory-list-controls}

Met geheugenlijsten kunt u de verzamelingselementen bewerken door de lijstelementen vooraf te laden. Deze lijst kan niet worden gefiltreerd of worden gevormd.

Deze lijsten worden gebruikt op XML in kaart gebrachte inzamelingselementen of op laag-volumeverbindingen.

### Kolomlijst {#column-list}

Met dit besturingselement wordt een bewerkbare kolomlijst weergegeven met een werkbalk die knoppen Toevoegen en Verwijderen bevat.

![](assets/d_ncs_integration_form_exemple13.png)

```xml
<input xpath="rcpEvent" type="list">
  <input xpath="@label"/>
  <input xpath="@date"/>
</input>
```

De lijstcontrole moet worden ingevuld met **type= &quot; lijst&quot;** attributen, en de weg van de lijst moet naar het inzamelingselement verwijzen.

De kolommen worden gedeclareerd in de onderliggende **`<input>`** -tags van de lijst. Het etiket en de grootte van de kolom kunnen met het **etiket** en **colSize** attributen worden gedwongen.

>[!NOTE]
>
>De sorteren-orde pijlen worden automatisch toegevoegd wanneer het **ordered= &quot;waar&quot;** attribuut aan het inzamelingselement in het gegevensschema wordt toegevoegd.

De werkbalkknoppen kunnen horizontaal worden uitgelijnd:

![](assets/d_ncs_integration_form_exemple14.png)

```xml
<input nolabel="true" toolbarCaption="List of events" type="list" xpath="rcpEvent" zoom="true">
  <input xpath="@label"/>
  <input xpath="@date"/>
</input>
```

Het **toolbarCaption** attribuut dwingt de horizontale groepering van de toolbar en gaat de titel boven de lijst in.

#### Inzoomen op een lijst {#zoom-in-a-list}

U kunt de gegevens in een lijst invoegen en bewerken in een afzonderlijk bewerkingsformulier.

![](assets/d_ncs_integration_form_exemple15.png)

```xml
<input nolabel="true" toolbarCaption="List of events" type="list" xpath="rcpEvent" zoom="true" zoomOnAdd="true">
  <input xpath="@label"/>
  <input xpath="@date"/>

  <form colcount="2" label="Event">
    <input xpath="@label"/>
    <input xpath="@date"/>
  </form>
</input>
```

Het bewerkingsformulier wordt ingevuld vanuit het element `<form>` onder de lijstdefinitie. De structuur is identiek aan die van een invoerformulier. De **[!UICONTROL Detail]** knoop wordt automatisch toegevoegd wanneer het **zoom= &quot;waar&quot;** attribuut op de **`<input>`** markering van de lijst wordt voltooid. Met dit kenmerk kunt u het bewerkingsformulier van de geselecteerde regel starten.

>[!NOTE]
>
>Het toevoegen van **zoomOnAdd= &quot;waar&quot;** attributen dwingt de uit te geven vorm om worden geroepen wanneer een lijstelement wordt opgenomen.

### Eigenschappen van List {#list-properties-1}

* **noToolbar**: verbergt de toolbar (met waarde &quot;waar&quot;)
* **toolbarCaption**: laadt het toolbaretiket over
* **toolbarAlign**: wijzigt het plaatsen van de toolbar (mogelijke waarden: &quot;verticaal&quot;| &quot;horizontaal&quot;)
* **img**: toont het beeld verbonden aan de lijst
* **vorm**: overlaadt de Edit vorm van het gerichte element
* **gezoem**: voegt de **[!UICONTROL Zoom]** knoop toe om het gerichte element uit te geven
* **zoomOnAdd**: lanceert uitgeven vorm op de toevoeging
* **xpathChoiceTarget**: voor toevoeging, lanceert de selectievorm op de ingegane verbinding

## Niet-bewerkbare velden {#non-editable-fields}

Om een gebied te tonen en het te verhinderen worden uitgegeven, gebruik de **`<value>`** markering of voltooi **readOnly= &quot;waar&quot;** attributen op de **`<input>`** markering.

Voorbeeld op het veld &quot;Geslacht&quot;:

![](assets/d_ncs_integration_form_exemple16.png)

```xml
<value value="@gender"/>
<input xpath="@gender" readOnly="true"/>
```

## Keuzerondje {#radio-button}

Met een keuzerondje kunt u kiezen uit verschillende opties. De **`<input>`** markeringen worden gebruikt om van de mogelijke opties een lijst te maken, en het **checkedValue** attribuut specificeert de waarde verbonden aan de keus.

Voorbeeld op het veld &quot;Geslacht&quot;:

```xml
<input type="RadioButton" xpath="@gender" checkedValue="0" label="Choice 1"/>
<input type="RadioButton" xpath="@gender" checkedValue="1" label="Choice 2"/>
<input type="RadioButton" xpath="@gender" checkedValue="2" label="Choice 3"/>
```

![](assets/d_ncs_integration_form_exemple17.png)

## Selectievakje {#checkbox}

Een selectievakje geeft een Booleaanse status weer (geselecteerd of niet). Dit besturingselement wordt standaard gebruikt door Booleaanse velden (true/false). Een variabele met de standaardwaarde 0 of 1 kan aan deze knop worden gekoppeld. Deze waarde kan via de **checkValue** attributen worden overbelast.

```xml
<input xpath="@boolean1"/>
<input xpath="@field1" type="checkbox" checkedValue="Y"/>
```

![](assets/d_ncs_integration_form_exemple20.png)

## Opsomming {#enumeration}

<!-- to be completed -->

## Navigatiehiërarchie bewerken {#navigation-hierarchy-edit}

Deze controle bouwt een boom op een reeks gebieden om uit te geven.

De besturingselementen die moeten worden bewerkt, worden gegroepeerd in een **`<container>`** -item dat wordt ingevoerd onder de **`<input>`** -tag van het structuurbesturingselement:

```xml
<input nolabel="true" type="treeEdit">
  <container label="Text fields">
    <input xpath="@text1"/>
    <input xpath="@text2"/>
  </container>
  <container label="Boolean fields">
    <input xpath="@boolean1"/>
    <input xpath="@boolean2"/>
  </container>
</input>
```

![](assets/d_ncs_integration_form_exemple18.png)

## Expressieveld {#expression-field}

Een uitdrukkingsgebied werkt dynamisch een gebied van een uitdrukking bij; de **`<input>`** markering wordt gebruikt met een **xpath** attribuut om de weg van het gebied in te gaan dat moet worden bijgewerkt en een **expo** attribuut dat de updateuitdrukking bevat.

```xml
<!-- Example: updating the boolean1 field from the value contained in the field with path /tmp/@flag -->
<input expr="Iif([/tmp/@flag]=='On', true, false)" type="expr" xpath="@boolean1"/>
<input expr="[/ignored/@action] == 'FCP'" type="expr" xpath="@launchFCP"/>
```

## Context van formulieren {#context-of-forms}

Door het uitvoeren van een invoerformulier wordt een XML-document geïnitialiseerd dat de gegevens bevat van de entiteit die wordt bewerkt. Dit document vertegenwoordigt de context van het formulier en kan als werkruimte worden gebruikt.

### De context bijwerken {#updating-the-context}

Als u de context van het formulier wilt wijzigen, gebruikt u de tag `<set expr="<value>" xpath="<field>"/>` , waarbij `<field>` het doelveld is en `<value>` de update-expressie of -waarde.

Voorbeelden van het gebruik van de tag `<set>` :

* **`<set expr="'Test'" xpath="/tmp/@test" />`**: plaatst de waarde &#39;Test&#39; op een tijdelijke locatie /tmp/@test1
* **`<set expr="'Test'" xpath="@lastName" />`**: werkt de entiteit in het kenmerk &quot;lastName&quot; bij met de waarde &quot;Test&quot;
* **`<set expr="true" xpath="@boolean1" />`**: stelt de waarde van het veld &quot;boolean1&quot; in op &quot;true&quot;
* **`<set expr="@lastName" xpath="/tmp/@test" />`**: werkt bij met de inhoud van het kenmerk &quot;lastName&quot;

De context van het formulier kan worden bijgewerkt tijdens het initialiseren en sluiten van het formulier via de tags **`<enter>`** en **`<leave>`** .

```xml
<form name="recipient" namespace="cus">
  <enter>
    <set…
  </enter>
  …
  <leave>
    <set…
  </leave>
</form>
```

>[!NOTE]
>
>De tags `<enter>` en `<leave>` kunnen worden gebruikt op de `<container>` -pagina&#39;s (&quot;laptop&quot;- en &quot;iconbox&quot;-typen).

### Expressietaal {#expression-language-}

Een macrotaal kan in formulierdefinitie worden gebruikt om voorwaardelijke tests uit te voeren.

De tag **`<if expr="<expression>" />`** voert de instructies uit die onder de tag zijn opgegeven als de expressie wordt geverifieerd:

```xml
<if expr="([/tmp/@test] == 'Test' or @lastName != 'Doe') and @boolean2 == true">
  <set xpath="@boolean1" expr="true"/>
</if>
```

De tag **`<check expr="<condition>" />`** in combinatie met de tag **`<error>`** voorkomt validatie van het formulier en geeft een foutbericht weer als niet aan de voorwaarde wordt voldaan:

```xml
<leave>
  <check expr="/tmp/@test != ''">
    <error>You must populate the 'Test' field!</error> 
  </check>
</leave>
```

<!-- changer exemple par un exemple plus parlant. cf. vidéo validation 02:27. noter aussi l'attribut required dans l'exemple de la vidéo. -->

## Wizards {#wizards}

Een assistent begeleidt u door een reeks gegevensinvoerstappen in de vorm van pagina&#39;s. De ingevoerde gegevens worden opgeslagen wanneer u het formulier valideert.

Een medewerker heeft de volgende structuur:

```xml
<form type="wizard" name="example" namespace="cus" img="nms:rcpgroup32.png" label="Assistant example" entity-schema="nms:recipient">
  <container title="Title of page 1" desc="Long description of page 1">
    <input xpath="@lastName"/>
    <input xpath="comment"/>
  </container>
  <container title="Title of page 2" desc="Long description of page 2">
    …
  </container>
  …
</form>
```

![](assets/d_ncs_integration_form_exemple19.png)

De aanwezigheid van **type= &quot;tovenaar&quot;** attributen op het `<form>` element laat u de hulpwijze in de bouw van de vorm bepalen. De pagina&#39;s worden voltooid vanuit `<container>` -elementen, onderliggende elementen van het `<form>` -element. Het element `<container>` van een pagina wordt gevuld met de titelkenmerken voor de titel en het desc om de beschrijving onder de paginatitel weer te geven. De knoppen **[!UICONTROL Previous]** en **[!UICONTROL Next]** worden automatisch toegevoegd om te kunnen bladeren tussen pagina&#39;s.

Met de knop **[!UICONTROL Finish]** slaat u de ingevoerde gegevens op en sluit u het formulier.

### SOAP {#soap-methods}

SOAP methode-uitvoering kan worden gestart vanuit een gevulde **`<leave>`** -tag aan het einde van een pagina.

De tag **`<soapcall>`** bevat de aanroep van de methode met de volgende invoerparameters:

```xml
<soapCall name="<name>" service="<schema>">
  <param  type="<type>" exprIn="<xpath>"/>  
  …
</soapCall>
```

De naam van de dienst en zijn implementatieschema zijn ingegaan via de **naam** en **dienst** attributen van de **`<soapcall>`** markering.

De invoerparameters worden beschreven in de **`<param>`** -elementen onder de **`<soapcall>`** -tag.

Het parametertype moet via het **type** attribuut worden gespecificeerd. De mogelijke typen zijn:

* **koord**: karakterkoord
* **boolean**: Boolean
* **byte**: 8 beetjegeheel
* **kort**: 16 beetjegeheel
* **lang**: geheel met 32 bits
* **kort**: 16 beetjegeheel
* **dubbel**: dubbel-precisie drijvende puntaantal
* **DOMElement**: element-type knoop

Het **exprIn** attribuut bevat de plaats van de gegevens die als parameter moeten worden overgegaan.

**Voorbeeld**:

```xml
<leave>
  <soapCall name="RegisterGroup" service="nms:recipient">         
    <param  type="DOMElement"    exprIn="/tmp/entityList"/>         
    <param  type="DOMElement"    exprIn="/tmp/choiceList"/>         
    <param  type="boolean"       exprIn="true"/>       
  </soapCall>
</leave>
```
