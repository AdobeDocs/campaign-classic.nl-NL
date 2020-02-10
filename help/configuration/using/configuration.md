---
title: Configuratie
seo-title: Configuratie
description: Configuratie
seo-description: null
page-status-flag: never-activated
uuid: 0f2aadc3-5199-476c-9956-6e39b899a7d0
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: navigation-hierarchy
discoiquuid: b781fd52-828c-4582-a546-a1fee7e5a26d
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 912507f25c5bc3c1ca7121b0df8182176900f4c0

---


# Configuratie{#configuration}

De typen mappen die door de navigatielijst worden gebruikt, worden beschreven in een XML-document dat voldoet aan de grammatica van het schema **xtk:navtree** .

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

Het XML-document bevat het **`<navtree>`** hoofdelement met de kenmerken **name** en **namespace** om de documentnaam en naamruimte op te geven. De naam en naamruimte vormen de documentidentificatietoets.

De algemene opdrachten van de toepassing worden in het document gedeclareerd vanuit het **`<commands>`** element.

De declaratie van bestandstypen is in het document gestructureerd met de volgende elementen: **`<model>`** en **`<nodemodel>`**.

## Algemene opdrachten {#global-commands}

Met een algemene opdracht kunt u een handeling starten. Deze handeling kan een invoerformulier of een SOAP-aanroep zijn.

Algemene opdrachten zijn toegankelijk via het **[!UICONTROL Tools]** hoofdmenu.

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
* **rechten**: lijst met benoemde rechten (gescheiden door een komma) die toegang geven tot deze opdracht. De lijst met beschikbare rechten is toegankelijk vanuit de **[!UICONTROL Administration > Access management > Named rights]** map.
* **promptLabel**: geeft een bevestigingsvak weer voordat de opdracht wordt uitgevoerd.

Een **`<command>`** element kan **`<command>`** subelementen bevatten. In dit geval kunt u met het bovenliggende element een submenu weergeven dat bestaat uit deze onderliggende elementen.

De opdrachten worden in dezelfde volgorde weergegeven als in het XML-document.

Met een opdrachtscheidingsteken kunt u een scheidingsbalk tussen opdrachten weergeven. Deze wordt aangegeven met de **&#39;-&#39;** waarde in het opdrachtlabel.

De facultatieve aanwezigheid van de **`<soapcall>`** markering met zijn inputparameters bepaalt de vraag van een methode van de ZEEP die moet worden uitgevoerd. Raadpleeg de documentatie [van](http://docs.campaign.adobe.com/doc/AC/en/jsapi/index.html)Campagne JSAPI voor meer informatie over de SOAP API.

De formuliercontext kan via de **`<enter>`** tag worden bijgewerkt bij de initialisatie. Raadpleeg de documentatie bij invoerformulieren voor meer informatie over deze tag.

**Voorbeeld**:

* Declaratie van een algemene opdracht voor het starten van het formulier &quot;xtk:import&quot;:

   ```
   <command desc="Start the data import wizard" form="xtk:import" label="&amp;Data import..." name="import" rights="import,recipientImport"/>
   ```

   Een sneltoets wordt op het teken &#39;I&#39; gedeclareerd door de aanwezigheid van **&amp;** in het opdrachtlabel.

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

De verklaring van het omslagtype moet onder een **`<model>`** element zijn ingegaan. Met dit element kunt u een hiërarchische organisatie definiëren die zichtbaar is vanuit het **[!UICONTROL Add new folder]** menu. Een **`<model>`** element moet **`<nodemodel>`** elementen en andere **`<model>`** elementen bevatten.

De **naam** en de **etiketattributen** bevolken de interne naam van het element en het etiket dat in het **[!UICONTROL Add new folder]** menu wordt getoond.

Het **`<nodemodel>`** element bevat de beschrijving van het maptype met de volgende eigenschappen:

* **naam**: interne naam
* **label**: gebruikt in het **[!UICONTROL Add new folder]** menu en als standaardlabel bij het invoegen van een map.
* **img**: standaardafbeelding bij het invoegen van de map.
* **hiddenCommands**: lijst met opdrachten (gescheiden door een komma) die moeten worden gemaskeerd. Mogelijke waarden: &quot;insert&quot;, &quot;delete&quot;, &quot;update&quot; en &quot;duplicate&quot;.
* **newFolderShortCuts**: lijst met sneltoetsen op modellen (**`<nodemodel>`** gescheiden door een komma) in het maken van mappen.
* **insertRight**, **editRight**, **deleteRight**: rechten voor het invoegen, bewerken en verwijderen van mappen.

Het **`<view>`** element onder het **`<nodemodel>`** element bevat de configuratie van de lijst die aan de weergave is gekoppeld. Het schema van de lijst is ingegaan in de **schemaattributen** van het **`<view>`** element.

Als u de records van de lijst wilt bewerken, wordt impliciet het invoerformulier met dezelfde naam als het lijstschema gebruikt. Het **kenmerk type** op het **`<view>`** element is van invloed op de weergave van het formulier. Mogelijke waarden zijn:

* **keuzelijst**: Hiermee geeft u het formulier onder aan de lijst weer.
* **lijst**: geeft alleen de lijst weer. Het formulier wordt gestart door te dubbelklikken of door te klikken op Openen in het menu om de lijst te selecteren.
* **formulier**: geeft een alleen-lezen formulier weer.
* **editForm**: Hiermee geeft u een formulier weer in de bewerkingsmodus.

>[!NOTE]
>
>De naam van het invoerformulier kan worden overbelast door het **formulierkenmerk** in het **`<view>`** element in te voeren.

De standaardconfiguratie van de lijstkolommen is ingegaan via het **`<columns>`** element. Een kolom wordt gedeclareerd op een **`<node>`** element dat het kenmerk **xpath** bevat en waarnaar in het schema moet worden verwezen als waarde.

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

Opdrachten zijn toegankelijk via het **[!UICONTROL Action]** menu van de lijst of de bijbehorende menuknop.

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

De beschrijving van een opdracht is ingevoerd voor het **`<command>`** element met de volgende eigenschappen:

* **naam**: interne naam van de opdracht: de naam moet worden ingevoerd en uniek zijn.
* **label**: label van de opdracht.
* **desc**: een beschrijving die zichtbaar is op de statusbalk van het hoofdscherm.
* **formulier**: te lanceren formulier: de in te voeren waarde is de identificatiecode van het invoerformulier (bv. &quot;cus:ontvanger&quot;).
* **rechten**: lijst met benoemde rechten (gescheiden door een komma) die toegang geven tot deze opdracht. De lijst met beschikbare rechten is toegankelijk vanuit de **[!UICONTROL Administration > Access management > Named rights]** map.
* **promptLabel**: geeft een bevestigingsvak weer voordat de opdracht wordt uitgevoerd
* **monoSelection**: Hiermee wordt monoselectie geforceerd (standaard meerdere selecties).
* **refreshView**: dwingt het opnieuw laden van de lijst na uitvoering van het bevel.
* **enabledIf**: activeert de opdracht afhankelijk van de ingevoerde expressie.
* **img**: voert een afbeelding in die toegang geeft tot de opdracht via de lijstwerkbalk.

Een **`<command>`** element kan **`<command>`** subelementen bevatten. In dit geval kunt u met het bovenliggende element een submenu weergeven dat bestaat uit deze onderliggende elementen.

De opdrachten worden in dezelfde volgorde weergegeven als in het XML-document.

Met een opdrachtscheidingsteken kunt u een scheidingsbalk tussen opdrachten weergeven. Deze wordt aangegeven met de **&#39;-&#39;** waarde in het opdrachtlabel.

De facultatieve aanwezigheid van de **`<soapcall>`** markering met zijn inputparameters bepaalt de vraag van een methode van de ZEEP die moet worden uitgevoerd. Raadpleeg de documentatie [van](http://docs.campaign.adobe.com/doc/AC/en/jsapi/index.html)Campagne JSAPI voor meer informatie over SOAP API&#39;s.

De formuliercontext kan worden bijgewerkt bij initialisatie via de **`<enter>`** tag. Raadpleeg de documentatie bij het invoerformulier voor meer informatie over deze tag.

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

Voor een verbonden omslag, moet de **folderLink** attributen op het **`<nodemodel>`** element worden bevolkt. Dit kenmerk bevat de naam van de koppeling in de map die in het gegevensschema is geconfigureerd.

Voorbeeld van declaratie van een gekoppelde map in het gegevensschema:

```
<element default="DefaultFolder('nmsFolder')" label="Folder" name="folder" revDesc="Recipients in the folder" revIntegrity="own" revLabel="Recipients" target="xtk:folder" type="link"/>
```

De configuratie van de map **`<nodemodel>`** op de koppeling van de map met de naam &quot;map&quot; is als volgt:

```
<nodeModel deleteRight="folderDelete" editRight="folderEdit" folderLink="folder"
  img="nms:folder.png" insertRight="folderInsert" label="Recipients" name="nmsFolder">
...
</nodeModel>
```

