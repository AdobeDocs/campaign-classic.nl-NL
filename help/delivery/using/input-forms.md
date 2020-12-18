---
solution: Campaign Classic
product: campaign
title: Invoerformulieren
description: Invoerformulieren
audience: delivery
content-type: reference
topic-tags: content-management
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '818'
ht-degree: 2%

---


# Invoerformulieren{#input-forms}

Hieronder volgen enkele algemene beginselen voor het gebruik van inputformulieren in Adobe Campaign.

Forms worden beschreven in [deze sectie](../../configuration/using/identifying-a-form.md).

## Formulierstructuur {#form-structure}

Het XML-document van een invoerformulier moet het basiselement **`<form>`** bevatten met de kenmerken **name** en **namespace** om respectievelijk de formuliernaam en de bijbehorende naamruimte te vullen.

```
<form name="form_name" namespace="name_space">
...
</form>
```

Standaard is een formulier gekoppeld aan het gegevensschema met dezelfde naam en naamruimte. Als u een formulier wilt koppelen aan een andere naam, voert u de schemasleutel in het **entiteitsschema**-kenmerk van het **`<form>`**-element in.

Om de structuur van een invoerformulier te illustreren, beschrijven we een interface op basis van ons voorbeeldschema &quot;cus:book&quot;:

![](assets/d_ncs_content_form1.png)

Dit is het corresponderende invoerformulier:

```
<form name="book" namespace="cus" type="contentForm">
  <input xpath="@name"/>
  <input xpath="@date"/>
  <input xpath="@language"/>
</form>
```

De beschrijving van de bewerkingselementen begint met het basiselement **`<form>`**.

Een bewerkingscontrole is ingegaan in een **`<input>`** element met het **xpath** attribuut dat de weg van het gebied in zijn schema bevat.

**Herinnering voor XPath-syntaxis:**

De XPath-taal wordt in Adobe Campaign gebruikt om naar een element of kenmerk te verwijzen dat of dat tot een gegevensschema behoort.

XPath is een syntaxis waarmee u een knooppunt in de boomstructuur van een XML-document kunt zoeken.

Elementen worden aangeduid met hun naam en kenmerken worden aangeduid met de naam voorafgegaan door het teken &quot;@&quot;.

Voorbeelden:

* **@date**: selecteert het kenmerk met de naam &quot;date&quot;
* **hoofdstuk/@titel**: selecteert het kenmerk &quot;title&quot; onder het  `<chapter>` element
* **../@datum**: selecteert de datum uit het bovenliggende element van het huidige element

Het bewerkingsbesturingselement past zich automatisch aan het overeenkomstige gegevenstype aan en gebruikt het label dat in het schema is gedefinieerd.

Elk veld wordt standaard op één regel weergegeven en neemt alle beschikbare ruimte in beslag, afhankelijk van het type gegevens.

>[!CAUTION]
>
>Het invoerformulier moet verwijzen naar een **type=&quot;contentForm&quot;**-kenmerk op het **`<form>`**-element om automatisch het frame toe te voegen dat vereist is voor de inhoud die moet worden ingevoerd.

## Opmaak {#formatting}

De rangschikking van de besturingselementen ten opzichte van elkaar lijkt op de rangschikking die wordt gebruikt in HTML-tabellen, met de mogelijkheid om een besturingselement in meerdere kolommen te verdelen, elementen te interliniëren of de bezetting van de beschikbare ruimte op te geven. Houd er echter rekening mee dat de opmaak alleen de verdeling van de verhoudingen toestaat; u kunt geen vaste afmetingen opgeven voor een object.

Raadpleeg [deze sectie](../../configuration/using/form-structure.md#formatting) voor meer informatie.

## Besturingselementen voor lijsttypen {#list-type-controls}

Om een inzamelingselement uit te geven, moet u een lijsttypecontrole gebruiken.

### Kolomlijst {#column-list}

Met dit besturingselement wordt een bewerkbare kolomlijst weergegeven met een werkbalk die knoppen Toevoegen en Verwijderen bevat.

![](assets/d_ncs_content_form4.png)

```
<input xpath="chapter" type="list">
  <input xpath="@name"/>
  <input xpath="@number"/>
</input>
```

De lijstcontrole moet met **type= &quot;lijst&quot;** attributen worden ingevuld, en de weg van de lijst moet naar het inzamelingselement verwijzen.

De kolommen worden gedeclareerd door de onderliggende **`<input>`**-elementen van de lijst.

>[!NOTE]
>
>De pijl-omhoog en pijl-omlaag worden automatisch toegevoegd wanneer het kenmerk **ordered=&quot;true&quot;** voor het verzamelingselement in het gegevensschema wordt voltooid.

Standaard worden de werkbalkknoppen verticaal uitgelijnd. Ze kunnen ook horizontaal worden uitgelijnd:

![](assets/d_ncs_content_form5.png)

```
<input nolabel="true" toolbarCaption="List of chapters" type="list" xpath="chapter">
  <input xpath="@name"/>
  <input xpath="@number"/>
</input>
```

Met het kenmerk **toolbarCaption** wordt de horizontale uitlijning van de werkbalk geforceerd en wordt de titel boven de lijst gevuld.

>[!NOTE]
>
>Voor het etiket van het inzamelingselement dat niet aan de linkerzijde van de controle moet worden getoond, voeg **nolabel= &quot;waar&quot;** attribuut toe.

#### Een lijst inzoomen {#zoom-in-a-list}

Het invoegen en bewerken van lijstgegevens kan in een afzonderlijk bewerkingsformulier worden uitgevoerd.

In de volgende gevallen worden formulieren in lijsten bewerken gebruikt:

* Ter vergemakkelijking van de invoer van informatie,
* Aanwezigheid van een meerregelig besturingselement
* De kolommen in de lijst bevatten alleen de hoofdvelden en in het formulier worden alle velden van het verzamelingselement weergegeven.

![](assets/d_ncs_content_form7.png)

```
<input nolabel="true" toolbarCaption="List of chapters" type="list" xpath="chapter" zoom="true" zoomOnAdd="true">
  <input xpath="@name"/>
  <input xpath="@number"/>

  <form colcount="2" label="Editing a chapter">
    <input xpath="@name"/>
    <input xpath="@number"/>
    <input colspan="2" xpath="page"/>
  </form>
</input>
```

De definitie van het bewerkingsformulier wordt opgegeven via het element **`<form>`** onder het lijstelement. De structuur ervan is identiek aan de structuur van een invoerformulier.

Een **[!UICONTROL Detail]** knoop wordt automatisch toegevoegd wanneer **zoom=&quot;waar&quot;** attribuut in de lijstdefinitie is ingegaan. Hiermee kunt u het bewerkingsformulier openen op de geselecteerde regel.

>[!NOTE]
>
>Als u het kenmerk **zoomOnAdd=&quot;true&quot;** toevoegt, wordt het bewerkingsformulier afgedwongen bij het invoegen van een element in de lijst.

### Tablijst {#tab-list}

In deze lijst wordt het bewerken van verzamelingselementen weergegeven in de vorm van tabbladen.

![](assets/d_ncs_content_form6.png)

```
<container toolbarCaption="List of chapters" type="notebooklist" xpath="chapter" xpath-label="@name">
  <container colcount="2">
    <input xpath="@name"/>
    <input xpath="@number"/>
    <input colspan="2" xpath="page"/>
  </container>
</container>
```

Het lijstbesturingselement moet worden ingevuld met het **type=&quot;notebooklist&quot;**-kenmerk en het pad van de lijst moet naar het verzamelingselement verwijzen.

De titel van het tabblad bevat de waarde van de gegevens die zijn ingevoerd via het kenmerk **xpath-label**.

De bewerkingsbesturingselementen moeten worden gedeclareerd onder een element **`<container>`** dat een onderliggend element is van het lijstbesturingselement.

Met de werkbalkknoppen kunt u lijstelementen toevoegen of verwijderen.

>[!NOTE]
>
>De linker en juiste het ordenen pijlen worden automatisch toegevoegd wanneer **ordered=&quot;waar&quot;** attribuut voor het inzamelingselement in het gegevensschema wordt bevolkt.

## Containers {#containers}

Met containers kunt u een set besturingselementen groeperen. Ze bestaan via het element **`<container>`**. Zij zijn reeds gebruikt om controles in verscheidene kolommen en voor de controle van de lusjelijst te formatteren.

Raadpleeg [deze sectie](../../configuration/using/form-structure.md#containers) voor meer informatie over containers en hoe u deze kunt gebruiken in invoerformulieren.

## Formulieren bewerken {#editing-forms}

In de bewerkingszone kunt u de XML-inhoud van het invoerformulier invoeren:

![](assets/d_ncs_content_form12.png)

Op het tabblad **[!UICONTROL Preview]** kunt u het invoerformulier weergeven:

![](assets/d_ncs_content_form13.png)
