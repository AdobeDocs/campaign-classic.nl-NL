---
product: campaign
title: Navigatiestructuur van Campagne Explorer configureren
feature: Application Settings
description: Leer hoe te om de boomstructuur van de Navigatie van de Ontdekkingsreiziger van de Campagne te vormen
role: Data Engineer, Developer
exl-id: c7ae7240-0c12-4420-bbb3-4268c9ade3e7
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '1186'
ht-degree: 0%

---

# Navigatiestructuur van Campagne Explorer configureren{#configuration}

Als deskundige gebruiker, kunt u omslagen in de ontdekkingsboomstructuur toevoegen en het aanpassen.

Leer meer over de ontdekkingsreiziger van de Campagne en navigatiehiërarchie [ in deze sectie ](../../platform/using/adobe-campaign-explorer.md#about-navigation-hierarchy).

De types van omslagen die door de navigatielijst worden gebruikt worden beschreven in een document van XML dat de grammatica van **xtk volgt:navtree** schema.

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

Het document van XML bevat het **`<navtree>`** wortelelement met **naam** en **namespace** attributen om de documentnaam en namespace te specificeren. De naam en naamruimte vormen de documentidentificatietoets.

De algemene opdrachten van de toepassing worden in het document gedeclareerd vanuit het element **`<commands>`** .

De declaratie van bestandstypen is in het document gestructureerd met de volgende elementen: **`<model>`** en **`<nodemodel>`** .

## Algemene opdrachten {#global-commands}

Met een algemene opdracht kunt u een handeling starten. Deze handeling kan een invoerformulier of een SOAP zijn.

Algemene opdrachten zijn toegankelijk via het hoofdmenu **[!UICONTROL Tools]** .

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

De beschrijving van een algemene opdracht wordt in het element **`<command>`** ingevoerd met de volgende eigenschappen:

* **naam**: interne naam van het bevel: de naam moet zijn ingegaan en uniek
* **etiket**: etiket van het bevel.
* **desc**: beschrijving zichtbaar van de statusbar van het belangrijkste scherm.
* **vorm**: vorm die moet worden gelanceerd: de in te gaan waarde is de identificatiesleutel van de inputvorm (b.v. &quot;cus:ontvanger&quot;)
* **rechten**: lijst van genoemde rechten (die door een komma worden gescheiden) die toegang tot dit bevel toestaan. De lijst met beschikbare rechten is toegankelijk via de map **[!UICONTROL Administration > Access management > Named rights]** .
* **promptLabel**: toont een bevestigingsvakje vóór uitvoering van het bevel.

Een **`<command>`** -element kan **`<command>`** -subelementen bevatten. In dit geval kunt u met het bovenliggende element een submenu weergeven dat bestaat uit deze onderliggende elementen.

De opdrachten worden in dezelfde volgorde weergegeven als in het XML-document.

Met een opdrachtscheidingsteken kunt u een scheidingsbalk tussen opdrachten weergeven. Het wordt geïdentificeerd door de **&quot;-** waarde in het beveletiket.

De optionele aanwezigheid van de tag **`<soapcall>`** met de invoerparameters definieert de aanroep van een SOAP methode die moet worden uitgevoerd. Voor verdere informatie over SOAP API, verwijs naar [ de documentatie van JSAPI van de Campagne ](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=nl).

De formuliercontext kan via de tag **`<enter>`** worden bijgewerkt bij de initialisatie. Raadpleeg de documentatie bij invoerformulieren voor meer informatie over deze tag.

**Voorbeeld**:

* Verklaring van een algemene opdracht om het formulier &quot;xtk:import&quot; te starten:

  ```
  <command desc="Start the data import assistant" form="xtk:import" label="&amp;Data import..." name="import" rights="import,recipientImport"/>
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

* Uitvoering van een SOAP:

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

De declaratie van het maptype moet worden ingevoerd onder een **`<model>`** -element. Met dit element kunt u een hiërarchische organisatie definiëren die zichtbaar is vanuit het menu **[!UICONTROL Add new folder]** . Een **`<model>`** -element moet **`<nodemodel>`** elementen en andere **`<model>`** elementen bevatten.

De **naam** en **etiket** attributen bevolken de interne naam van het element en het etiket dat in het **[!UICONTROL Add new folder]** menu wordt getoond.

Het element **`<nodemodel>`** bevat de beschrijving van het maptype met de volgende eigenschappen:

* **naam**: interne naam
* **etiket**: etiket dat in het **[!UICONTROL Add new folder]** menu en als standaardetiket wordt gebruikt wanneer het opnemen van een omslag.
* **img**: standaardbeeld op omslagtoevoeging.
* **hiddenCommands**: lijst van bevelen (die door een komma worden gescheiden) om worden gemaskeerd. Mogelijke waarden: &quot;adbnew&quot;, &quot;adbsave&quot;, &quot;adbcancel&quot; en &quot;adbdup&quot;.
* **newFolderShortCuts**: lijst van kortere weg op modellen (**`<nodemodel>`** die door een komma wordt gescheiden) in omslagverwezenlijking.
* **insertRight**, **editRight**, **deleteRight**: rechten voor het opnemen, het uitgeven en het schrappen van omslagen.

Het element **`<view>`** onder het element **`<nodemodel>`** bevat de configuratie van de lijst die aan de weergave is gekoppeld. Het schema van de lijst is ingegaan in het **schema** attribuut van het **`<view>`** element.

Als u de records van de lijst wilt bewerken, wordt impliciet het invoerformulier met dezelfde naam als het lijstschema gebruikt. Het **type** attribuut op het **`<view>`** element beïnvloedt de vertoning van de vorm. Mogelijke waarden zijn:

* **lijst**: toont de vorm bij de bodem van de lijst.
* **lijst**: toont alleen de lijst. Het formulier wordt gestart door te dubbelklikken of door te klikken op Openen in het menu om de lijst te selecteren.
* **vorm**: toont een read-only vorm.
* **editForm**: toont een vorm op geef wijze uit.

>[!NOTE]
>
>De naam van de inputvorm kan worden overbelast door het **vorm** attribuut in het **`<view>`** element in te gaan.

De standaardconfiguratie van de lijstkolommen is ingegaan via het **`<columns>`** element. Een kolom wordt verklaard op a **`<node>`** element dat het **xpath** attribuut met het gebied bevat dat in zijn schema als zijn waarde moet worden van verwijzingen voorzien.

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

Met een sneltoetsopdracht kunt u een handeling starten om de lijst te selecteren. De handeling kan een invoerformulier of een SOAP zijn.

Opdrachten zijn toegankelijk via het **[!UICONTROL Action]** -menu van de lijst of de bijbehorende menuknop.

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

De beschrijving van een opdracht wordt ingevoerd voor het element **`<command>`** met de volgende eigenschappen:

* **naam**: interne naam van het bevel: de naam moet zijn ingegaan en uniek.
* **etiket**: etiket van het bevel.
* **desc**: beschrijving zichtbaar van de statusbar van het belangrijkste scherm.
* **vorm**: vorm die moet worden gelanceerd: de in te gaan waarde is de identificatiesleutel van de inputvorm (b.v. &quot;cus:ontvanger&quot;).
* **rechten**: lijst van genoemde rechten (die door een komma worden gescheiden) die toegang tot dit bevel toestaan. De lijst met beschikbare rechten is toegankelijk via de map **[!UICONTROL Administration > Access management > Named rights]** .
* **promptLabel**: toont een bevestigingsvakje vóór uitvoering van het bevel
* **monoSelection**: krachten mono-selectie (veelvoudige selectie door gebrek).
* **refreshView**: krachten die van de lijst na uitvoering van het bevel opnieuw laden.
* **enabledIf**: activeert het bevel afhankelijk van de ingegaan uitdrukking.
* **img**: gaat een beeld in dat toegang tot het bevel van de lijsttoolbar toestaat.

Een **`<command>`** -element kan **`<command>`** -subelementen bevatten. In dit geval kunt u met het bovenliggende element een submenu weergeven dat bestaat uit deze onderliggende elementen.

De opdrachten worden in dezelfde volgorde weergegeven als in het XML-document.

Met een opdrachtscheidingsteken kunt u een scheidingsbalk tussen opdrachten weergeven. Het wordt geïdentificeerd door de **&quot;-** waarde in het beveletiket.

De optionele aanwezigheid van de tag **`<soapcall>`** met de invoerparameters definieert de aanroep van een SOAP methode die moet worden uitgevoerd. Voor verdere informatie over SOAP APIs, verwijs naar [ de documentatie van JSAPI van de Campagne ](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=nl).

De formuliercontext kan bij de initialisatie worden bijgewerkt via de tag **`<enter>`** . Raadpleeg de documentatie bij het invoerformulier voor meer informatie over deze tag.

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

Voor een verbonden omslag, moet het **folderLink** attribuut op het **`<nodemodel>`** element worden bevolkt. Dit kenmerk bevat de naam van de koppeling in de map die in het gegevensschema is geconfigureerd.

Voorbeeld van declaratie van een gekoppelde map in het gegevensschema:

```
<element default="DefaultFolder('nmsFolder', [@_folder-id])" label="Folder" name="folder" revDesc="Recipients in the folder" revIntegrity="define" revLabel="Recipients" target="xtk:folder" type="link"/>
```

De configuratie van de **`<nodemodel>`** op de koppeling van de map met de naam &quot;map&quot; is als volgt:

```
<nodeModel deleteRight="folderDelete" editRight="folderEdit" folderLink="folder"
  img="nms:folder.png" insertRight="folderInsert" label="Recipients" name="nmsFolder">
...
</nodeModel>
```
