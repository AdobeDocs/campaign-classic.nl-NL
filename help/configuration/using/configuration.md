---
solution: Campaign Classic
product: campaign
title: Configuratie
description: Configuratie
audience: configuration
content-type: reference
topic-tags: navigation-hierarchy
translation-type: tm+mt
source-git-commit: 6e0741d13aa954e81fe6416663399ffd1a81012f
workflow-type: tm+mt
source-wordcount: '1161'
ht-degree: 1%

---


# Configuratie{#configuration}

De typen mappen die door de navigatielijst worden gebruikt, worden beschreven in een XML-document dat voldoet aan de grammatica van het schema **xtk:navtree**.

Het XML-document is als volgt gestructureerd:

```
<navtree name="name" namespace="name_space">
  <!-- Global commands -->
  <commands>
      ...
  </commands>
  
  <!-- Structured space for adding a folder -->
  <model name="<name>" label="<Label>">
    <!-- Folder type -->
    <nodeModel>
      ...
    </nodeModel>
<model name="<name>" label="<Sub model>">
      ...
    </model>
  </model> 
</navtree>
```

Het XML-document bevat het hoofdelement **`<navtree>`** met de kenmerken **name** en **namespace** om de documentnaam en naamruimte op te geven. De naam en naamruimte vormen de documentidentificatietoets.

De algemene opdrachten van de toepassing worden in het document gedeclareerd vanuit het element **`<commands>`**.

De declaratie van bestandstypen is in het document gestructureerd met de volgende elementen: **`<model>`** en **`<nodemodel>`**.

## Algemene opdrachten {#global-commands}

Met een algemene opdracht kunt u een handeling starten. Deze handeling kan een invoerformulier of een SOAP-aanroep zijn.

Algemene opdrachten zijn toegankelijk via het hoofdmenu **[!UICONTROL Tools]**.

De structuur van de bevelconfiguratie is als volgt:

```
<commands>
  <!-- Description of a command -->
  <command name="<name>" label="<label>" desc="<Description>" form="<form>" rights="<rights>">
    <soapCall name="<name>" service="<schema>">
      <param type="<type>" exprIn="<xpath>"/>  
        ...
    </soapCall>
    <enter>
      ...
    </enter>
  </command>
  <!-- Separator -->
  <command label="-" name="<name>"/>
  <!-- Command structure -->
  <command name="<name>" label="<Label>">
    <command...
  </command>
</commands>
```

De beschrijving van een globale opdracht is ingegaan in het **`<command>`** element met de volgende eigenschappen:

* **naam**: interne naam van de opdracht: de naam moet worden ingevoerd en uniek zijn
* **label**: label van de opdracht.
* **desc**: een beschrijving die zichtbaar is op de statusbalk van het hoofdscherm.
* **formulier**: te lanceren formulier: de in te voeren waarde is de identificatiecode van het invoerformulier (bv. &quot;cus:ontvanger&quot;)
* **rechten**: lijst met benoemde rechten (gescheiden door een komma) die toegang geven tot deze opdracht. De lijst met beschikbare rechten is toegankelijk via de map **[!UICONTROL Administration > Access management > Named rights]**.
* **promptLabel**: geeft een bevestigingsvak weer voordat de opdracht wordt uitgevoerd.

Een **`<command>`**-element kan **`<command>`**-subelementen bevatten. In dit geval kunt u met het bovenliggende element een submenu weergeven dat bestaat uit deze onderliggende elementen.

De opdrachten worden in dezelfde volgorde weergegeven als in het XML-document.

Met een opdrachtscheidingsteken kunt u een scheidingsbalk tussen opdrachten weergeven. Het wordt geïdentificeerd door **&#39;-&#39;** waarde in het beveletiket.

De facultatieve aanwezigheid van de **`<soapcall>`** markering met zijn inputparameters bepaalt de vraag van een methode van de ZEEP die moet worden uitgevoerd. Raadpleeg [Campagne JSAPI-documentatie](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html) voor meer informatie over de SOAP API.

De formuliercontext kan bij initialisatie worden bijgewerkt met de tag **`<enter>`**. Raadpleeg de documentatie bij invoerformulieren voor meer informatie over deze tag.

**Voorbeeld**:

* Declaratie van een algemene opdracht voor het starten van het formulier &quot;xtk:import&quot;:

   ```
   <command desc="Start the data import wizard" form="xtk:import" label="&amp;Data import..." name="import" rights="import,recipientImport"/>
   ```

   Een sneltoets wordt gedeclareerd op het teken &#39;I&#39; door de aanwezigheid van **&amp;** in het opdrachtlabel.

* Voorbeeld van een submenu met een scheidingsteken:

   ![](assets/d_ncs_integration_navigation_exemple1.png)

   ```
   <command label="Administration" name="admin">
     <command name="cmd1" label="Example 1" form="cus:example1"/>
     <command name="sep" label="-"/>
     <command name="cmd1" label="Example 2" form="cus:example2">
       <enter>
         <set xpath="@type" expr="1"/>
       </enter>
     </command>
   </command>
   ```

* Uitvoering van een SOAP-methode:

   ```
   <command name="cmd3" label="Example 3" promptLabel="Do you really want to execute the command?">
     <soapCall name="Execute" service="xtk:sql"/>
   </command>
   ```

## Maptype {#folder-type}

Met een maptype kunt u toegang geven tot de gegevens van een schema. De weergave die aan de map is gekoppeld, bestaat uit een lijst en een invoerformulier.

De configuratiestructuur van het maptype is als volgt:

```
<!-- Structured location to add the folder -->
<model name="name" label="Labelled">
  <!-- Type of folder -->
  <nodeModel name="<name>" label="<Labelled>" img="<image>">
    <view name="<name>" schema="<schema>" type="<listdet|list|form|editForm>">
      <columns>
        <node xpath="<field1>"/>
        ...
    </columns>
    </view> 
  </nodeModel>
  <model name="<name>" label="<Sous modèle>">
    ...
  </model>
</model>
```

De verklaring van het omslagtype moet onder een **`<model>`** element zijn ingegaan. Met dit element kunt u een hiërarchische organisatie definiëren die zichtbaar is vanuit het menu **[!UICONTROL Add new folder]**. Een **`<model>`**-element moet **`<nodemodel>`**-elementen en andere **`<model>`**-elementen bevatten.

De **name** en **label** attributen bevolken de interne naam van het element en het etiket dat in **[!UICONTROL Add new folder]** menu wordt getoond.

Het element **`<nodemodel>`** bevat de beschrijving van het maptype met de volgende eigenschappen:

* **naam**: interne naam
* **label**: gebruikt in het  **[!UICONTROL Add new folder]** menu en als standaardlabel bij het invoegen van een map.
* **img**: standaardafbeelding bij het invoegen van de map.
* **hiddenCommands**: lijst met opdrachten (gescheiden door een komma) die moeten worden gemaskeerd. Mogelijke waarden: &quot;adbnew&quot;, &quot;adbsave&quot;, &quot;adbcancel&quot; en &quot;adbdup&quot;.
* **newFolderShortCuts**: lijst met sneltoetsen op modellen (**`<nodemodel>`** gescheiden door een komma) bij het maken van mappen.
* **insertRight**,  **editRight**,  **deleteRight**: rechten voor het invoegen, bewerken en verwijderen van mappen.

Het **`<view>`** element onder het **`<nodemodel>`** element bevat de configuratie van de lijst verbonden aan de mening. Het schema van de lijst is ingegaan in het **schema** attribuut van **`<view>`** element.

Als u de records van de lijst wilt bewerken, wordt impliciet het invoerformulier met dezelfde naam als het lijstschema gebruikt. Het **type**-kenmerk op het **`<view>`**-element beïnvloedt de weergave van het formulier. Mogelijke waarden zijn:

* **keuzelijst**: Hiermee geeft u het formulier onder aan de lijst weer.
* **lijst**: geeft alleen de lijst weer. Het formulier wordt gestart door te dubbelklikken of door te klikken op Openen in het menu om de lijst te selecteren.
* **formulier**: geeft een alleen-lezen formulier weer.
* **editForm**: Hiermee geeft u een formulier weer in de bewerkingsmodus.

>[!NOTE]
>
>De naam van het invoerformulier kan worden overbelast door het kenmerk **form** in te voeren in het element **`<view>`**.

De standaardconfiguratie van de lijstkolommen is ingegaan via het **`<columns>`** element. Een kolom wordt gedeclareerd op een **`<node>`**-element dat het **xpath**-kenmerk bevat met het veld waarnaar in het schema moet worden verwezen als de waarde ervan.

**Voorbeeld**: verklaring van een omslagtype op het &quot;nms:ontvanger&quot;schema.

```
<model label="Profiles and targets" name="nmsProfiles">
  <nodeModel deleteRight="folderDelete" editRight="folderEdit" folderLink="folder"
             img="nms:folder.png" insertRight="folderInsert" label="Recipients"
             name="nmsFolder">
    <view name="listdet" schema="nms:recipient" type="listdet">
      <columns>
        <node xpath="@firstName"/>
        <node xpath="@lastName"/>
        <node xpath="@email"/>
        <node xpath="@account"/>
      </columns>
    </view>
  </nodeModel>
  <nodeModel name="nmsGroup" label="Groups"...
</model>
```

Het menu voor het invoegen van de overeenkomende map:

![](assets/d_ncs_integration_navigation_exemple2.png)

Filteren en sorteren kan worden toegepast wanneer de lijst wordt geladen:

```
<view name="listdet" schema="nms:recipient" type="listdet">
  <columns>
    ...
  </columns>

  <orderBy>
    <node expr="@lastName" desc="true"/>
</orderBy>
  <sysFilter>
    <condition expr="@type = 1"/>
  </sysFilter>
</view>  
```

### Sneltoetsopdrachten {#shortcut-commands}

Met een sneltoetsopdracht kunt u een handeling starten om de lijst te selecteren. De handeling kan een invoerformulier of een SOAP-aanroep zijn.

Opdrachten zijn toegankelijk via het menu **[!UICONTROL Action]** van de lijst of de bijbehorende menuknop.

De structuur van de bevelconfiguratie is als volgt:

```
<nodeModel...
  ...
  <command name="<name>" label="<label>" desc="<Description>" form="<form>" rights="<rights>">
    <soapCall name="<name>" service="<schema>">
      <param type="<type>" exprIn="<xpath>"/>  
        ...
    </soapCall>
    <enter>
      ...
    </enter>
  </command>
</nodeModel>
```

De beschrijving van een bevel is ingegaan op het **`<command>`** element met de volgende eigenschappen:

* **naam**: interne naam van de opdracht: de naam moet worden ingevoerd en uniek zijn.
* **label**: label van de opdracht.
* **desc**: een beschrijving die zichtbaar is op de statusbalk van het hoofdscherm.
* **formulier**: te lanceren formulier: de in te voeren waarde is de identificatiecode van het invoerformulier (bv. &quot;cus:ontvanger&quot;).
* **rechten**: lijst met benoemde rechten (gescheiden door een komma) die toegang geven tot deze opdracht. De lijst met beschikbare rechten is toegankelijk via de map **[!UICONTROL Administration > Access management > Named rights]**.
* **promptLabel**: geeft een bevestigingsvak weer voordat de opdracht wordt uitgevoerd
* **monoSelection**: Hiermee wordt monoselectie geforceerd (standaard meerdere selecties).
* **refreshView**: dwingt het opnieuw laden van de lijst na uitvoering van het bevel.
* **enabledIf**: activeert de opdracht afhankelijk van de ingevoerde expressie.
* **img**: voert een afbeelding in die toegang biedt tot de opdracht via de lijstwerkbalk.

Een **`<command>`**-element kan **`<command>`**-subelementen bevatten. In dit geval kunt u met het bovenliggende element een submenu weergeven dat bestaat uit deze onderliggende elementen.

De opdrachten worden in dezelfde volgorde weergegeven als in het XML-document.

Met een opdrachtscheidingsteken kunt u een scheidingsbalk tussen opdrachten weergeven. Het wordt geïdentificeerd door **&#39;-&#39;** waarde in het beveletiket.

De facultatieve aanwezigheid van de **`<soapcall>`** markering met zijn inputparameters bepaalt de vraag van een methode van de ZEEP die moet worden uitgevoerd. Raadpleeg [Campagne JSAPI-documentatie](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html) voor meer informatie over SOAP API&#39;s.

De formuliercontext kan bij initialisatie worden bijgewerkt met de tag **`<enter>`**. Raadpleeg de documentatie bij het invoerformulier voor meer informatie over deze tag.

**Voorbeeld**:

```
<command desc="Cancel execution of the job" enabledIf="EV(@status, 'running')"
         img="nms:difstop.bmp" label="Cancel..." name="cancelJob" 
         promptLabel="Do you really want to cancel this job?" refreshView="true">
  <soapCall name="Cancel" service="xtk:jobInterface"/>
</command>
<command label="-" name="sep1"/>
<command desc="Execute selected template" form="cus:form" lmonoSelection="true" name="executeModel"
         rights="import,export,aggregate">
  <enter>
    <set expr="0" xpath="@status"/>
  </enter>
</command>
```

### Gekoppelde map {#linked-folder}

Er zijn twee typen bewerkingen voor mapbeheer:

1. De map is een weergave: in de lijst worden alle records weergegeven die aan het schema zijn gekoppeld, met de mogelijkheid om het systeem te filteren dat in de mapeigenschappen is ingevoerd.
1. De map is gekoppeld: de records in de lijst worden impliciet gefilterd op de mapkoppeling.

Voor een verbonden omslag, moet **folderLink** attribuut op **`<nodemodel>`** element worden bevolkt. Dit kenmerk bevat de naam van de koppeling in de map die in het gegevensschema is geconfigureerd.

Voorbeeld van declaratie van een gekoppelde map in het gegevensschema:

```
<element default="DefaultFolder('nmsFolder')" label="Folder" name="folder" revDesc="Recipients in the folder" revIntegrity="own" revLabel="Recipients" target="xtk:folder" type="link"/>
```

De configuratie van **`<nodemodel>`** op de verbinding van de omslag genoemd &quot;omslag&quot;is als volgt:

```
<nodeModel deleteRight="folderDelete" editRight="folderEdit" folderLink="folder"
  img="nms:folder.png" insertRight="folderInsert" label="Recipients" name="nmsFolder">
...
</nodeModel>
```

