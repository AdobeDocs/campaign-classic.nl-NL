---
product: campaign
title: Navigatiestructuur van Campagne Explorer configureren
feature: Application Settings
description: Leer hoe te om de boomstructuur van de Navigatie van de Ontdekkingsreiziger van de Campagne te vormen
role: Data Engineer, Developer
badge-v7-only: label="v7" type="Informative" tooltip="Alleen van toepassing op Campaign Classic v7"
exl-id: c7ae7240-0c12-4420-bbb3-4268c9ade3e7
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '1193'
ht-degree: 0%

---

# Navigatiestructuur van Campagne Explorer configureren{#configuration}

Als deskundige gebruiker, kunt u omslagen in de ontdekkingsboomstructuur toevoegen en het aanpassen.

Meer informatie over de campagnedeskundige en navigatiehiërarchie [in deze sectie](../../platform/using/adobe-campaign-explorer.md#about-navigation-hierarchy).

De typen mappen die door de navigatielijst worden gebruikt, worden beschreven in een XML-document dat de grammatica van de **xtk:navtree** schema.

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

Het XML-document bevat de **`<navtree>`** hoofdelement met de **name** en **namespace** kenmerken om de documentnaam en naamruimte op te geven. De naam en naamruimte vormen de documentidentificatietoets.

De algemene opdrachten van de toepassing worden in het document gedeclareerd vanuit het **`<commands>`** element.

De declaratie van bestandstypen is in het document gestructureerd met de volgende elementen: **`<model>`** en **`<nodemodel>`**.

## Algemene opdrachten {#global-commands}

Met een algemene opdracht kunt u een handeling starten. Deze handeling kan een invoerformulier of een SOAP-aanroep zijn.

Algemene opdrachten zijn toegankelijk vanuit de hoofdmap **[!UICONTROL Tools]** -menu.

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

De beschrijving van een algemene opdracht is ingevoerd in het dialoogvenster **`<command>`** element met de volgende eigenschappen:

* **name**: interne naam van de opdracht: de naam moet worden ingevoerd en uniek zijn
* **label**: label van de opdracht.
* **desc**: beschrijving zichtbaar vanaf de statusbalk van het hoofdscherm.
* **formulier**: formulier dat moet worden gestart: de in te voeren waarde is de identificatiesleutel van het invoerformulier (bijv. &quot;cus:receiving&quot;)
* **rechten**: lijst met benoemde rechten (gescheiden door een komma) voor toegang tot deze opdracht. De lijst met beschikbare rechten kan worden geraadpleegd op **[!UICONTROL Administration > Access management > Named rights]** map.
* **promptLabel**: geeft een bevestigingsvak weer voordat de opdracht wordt uitgevoerd.

A **`<command>`** element kan bevatten **`<command>`** subelementen. In dit geval kunt u met het bovenliggende element een submenu weergeven dat bestaat uit deze onderliggende elementen.

De opdrachten worden in dezelfde volgorde weergegeven als in het XML-document.

Met een opdrachtscheidingsteken kunt u een scheidingsbalk tussen opdrachten weergeven. Het wordt door de **&#39;-&#39;** waarde in het opdrachtlabel.

De facultatieve aanwezigheid van de **`<soapcall>`** -tag met de invoerparameters definieert de aanroep van een SOAP-methode die moet worden uitgevoerd. Raadpleeg voor meer informatie over de SOAP API [JSAPI-documentatie voor campagne](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=nl).

De formuliercontext kan bij initialisatie worden bijgewerkt via de **`<enter>`** -tag. Raadpleeg de documentatie bij invoerformulieren voor meer informatie over deze tag.

**Voorbeeld**:

* Verklaring van een algemene opdracht om het formulier &quot;xtk:import&quot; te starten:

  ```
  <command desc="Start the data import wizard" form="xtk:import" label="&amp;Data import..." name="import" rights="import,recipientImport"/>
  ```

  Een sneltoets wordt op het teken I gedeclareerd door de aanwezigheid van **&amp;** in het opdrachtlabel.

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

De declaratie van het maptype moet worden ingevoerd onder een **`<model>`** element. Met dit element kunt u een hiërarchische organisatie definiëren die zichtbaar is vanuit de **[!UICONTROL Add new folder]** -menu. A **`<model>`** element must contain **`<nodemodel>`** elementen en andere **`<model>`** elementen.

De **name** en **label** de kenmerken vullen de interne naam van het element en het label dat in het dialoogvenster **[!UICONTROL Add new folder]** -menu.

De **`<nodemodel>`** element bevat de beschrijving van het omslagtype met de volgende eigenschappen:

* **name**: interne naam
* **label**: label dat wordt gebruikt in de **[!UICONTROL Add new folder]** en als standaardlabel bij het invoegen van een map.
* **img**: standaardafbeelding bij het invoegen van de map.
* **hiddenCommands**: lijst met opdrachten (gescheiden door een komma) die moeten worden gemaskeerd. Mogelijke waarden: &quot;adbnew&quot;, &quot;adbsave&quot;, &quot;adbcancel&quot; en &quot;adbdup&quot;.
* **newFolderShortCuts**: lijst met sneltoetsen voor modellen (**`<nodemodel>`** gescheiden door een komma) in het maken van mappen.
* **insertRight**, **editRight**, **deleteRight**: rechten voor het invoegen, bewerken en verwijderen van mappen.

De **`<view>`** element onder de **`<nodemodel>`** -element bevat de configuratie van de lijst die aan de weergave is gekoppeld. Het schema van de lijst is ingevoerd in het dialoogvenster **schema** kenmerk van de **`<view>`** element.

Als u de records van de lijst wilt bewerken, wordt impliciet het invoerformulier met dezelfde naam als het lijstschema gebruikt. De **type** kenmerk op de **`<view>`** Het element is van invloed op de weergave van het formulier. Mogelijke waarden zijn:

* **keuzelijst**: geeft het formulier onder aan de lijst weer.
* **list**: geeft alleen de lijst weer. Het formulier wordt gestart door te dubbelklikken of door te klikken op Openen in het menu om de lijst te selecteren.
* **formulier**: geeft een alleen-lezen formulier weer.
* **editForm**: geeft een formulier weer in de bewerkingsmodus.

>[!NOTE]
>
>De naam van het invoerformulier kan worden overgeladen door het invoerformulier in te voeren **formulier** in het dialoogvenster **`<view>`** element.

De standaardconfiguratie van de lijstkolommen is ingegaan via **`<columns>`** element. Een kolom wordt gedeclareerd op een **`<node>`** element met het **xpath** kenmerk met het veld waarnaar in het schema moet worden verwezen als waarde.

**Voorbeeld**: declaratie van een maptype in het schema &quot;nms:ontvanger&quot;.

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

Opdrachten zijn toegankelijk via de **[!UICONTROL Action]** menu van de lijst of de bijbehorende menuknop.

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

De beschrijving van een opdracht is ingevoerd in het dialoogvenster **`<command>`** element met de volgende eigenschappen:

* **name**: interne naam van de opdracht: u moet een unieke naam invoeren.
* **label**: label van de opdracht.
* **desc**: beschrijving zichtbaar vanaf de statusbalk van het hoofdscherm.
* **formulier**: formulier dat moet worden gestart: de in te voeren waarde is de identificatiesleutel van het invoerformulier (bv. &quot;cus:receiving&quot;).
* **rechten**: lijst met benoemde rechten (gescheiden door een komma) voor toegang tot deze opdracht. De lijst met beschikbare rechten kan worden geraadpleegd op **[!UICONTROL Administration > Access management > Named rights]** map.
* **promptLabel**: geeft een bevestigingsvak weer voordat de opdracht wordt uitgevoerd
* **monoSelection**: forceert monoselectie (standaard meerdere selecties).
* **refreshView**: forceert het opnieuw laden van de lijst na uitvoering van de opdracht.
* **enabledIf**: activeert de opdracht afhankelijk van de ingevoerde expressie.
* **img**: voert een afbeelding in die toegang geeft tot de opdracht via de lijstwerkbalk.

A **`<command>`** element kan bevatten **`<command>`** subelementen. In dit geval kunt u met het bovenliggende element een submenu weergeven dat bestaat uit deze onderliggende elementen.

De opdrachten worden in dezelfde volgorde weergegeven als in het XML-document.

Met een opdrachtscheidingsteken kunt u een scheidingsbalk tussen opdrachten weergeven. Het wordt door de **&#39;-&#39;** waarde in het opdrachtlabel.

De facultatieve aanwezigheid van de **`<soapcall>`** -tag met de invoerparameters definieert de aanroep van een SOAP-methode die moet worden uitgevoerd. Voor meer informatie over SOAP API&#39;s raadpleegt u [JSAPI-documentatie voor campagne](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=nl).

De formuliercontext kan bij initialisatie worden bijgewerkt via de **`<enter>`** -tag. Raadpleeg de documentatie bij het invoerformulier voor meer informatie over deze tag.

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

1. De map is een weergave: in de lijst worden alle records weergegeven die aan het schema zijn gekoppeld, met de mogelijkheid van systeemfiltering die in de mapeigenschappen is ingevoerd.
1. De map is gekoppeld: de records in de lijst worden impliciet gefilterd op de mapkoppeling.

Voor een gekoppelde map **folderLink** kenmerk op de **`<nodemodel>`** element moet worden gevuld. Dit kenmerk bevat de naam van de koppeling in de map die in het gegevensschema is geconfigureerd.

Voorbeeld van declaratie van een gekoppelde map in het gegevensschema:

```
<element default="DefaultFolder('nmsFolder', [@_folder-id])" label="Folder" name="folder" revDesc="Recipients in the folder" revIntegrity="define" revLabel="Recipients" target="xtk:folder" type="link"/>
```

De configuratie van de **`<nodemodel>`** op de koppeling van de map met de naam &quot;map&quot; ziet u als volgt:

```
<nodeModel deleteRight="folderDelete" editRight="folderEdit" folderLink="folder"
  img="nms:folder.png" insertRight="folderInsert" label="Recipients" name="nmsFolder">
...
</nodeModel>
```
