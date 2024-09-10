---
product: campaign
title: Formulieren bewerken
description: Formulieren bewerken
feature: Configuration
role: Data Engineer, Developer
badge-v8: label="Ook van toepassing op v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
exl-id: 24604dc9-f675-4e37-a848-f1911be84f3e
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '1707'
ht-degree: 1%

---


# Formulieren bewerken{#editing-forms}

## Overzicht

Marktdeelnemers en operatoren gebruiken invoerformulieren om records te maken, te wijzigen en voor te vertonen. Forms geeft een visuele weergave van informatie weer.

U kunt invoerformulieren maken en wijzigen:

* U kunt de fabrieksinvoerformulieren wijzigen die standaard worden geleverd. De fabrieksinvoerformulieren zijn gebaseerd op de fabrieksgegevensschema&#39;s.
* U kunt aangepaste invoerformulieren maken op basis van gegevensschema&#39;s die u definieert.

Forms zijn entiteiten van het type `xtk:form` . U kunt de structuur van het invoerformulier weergeven in het `xtk:form` -schema. Kies **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Data schemas]** in het menu om dit schema weer te geven. Lees meer over [ vormstructuur ](form-structure.md).

Als u invoerformulieren wilt openen, kiest u **[!UICONTROL Administration]> [!UICONTROL Configuration] >[!UICONTROL Input forms]** in het menu:

![](assets/d_ncs_integration_form_arbo.png)

Als u formulieren wilt ontwerpen, bewerkt u de XML-inhoud in de XML-editor:

![](assets/d_ncs_integration_form_edit.png)

[Meer informatie](form-structure.md#formatting).

Klik op het tabblad **[!UICONTROL Preview]** als u een voorbeeld van een formulier wilt bekijken:

![](assets/d_ncs_integration_form_preview.png)

## Formuliertypen

U kunt verschillende typen invoerformulieren maken. Het formuliertype bepaalt hoe gebruikers door het formulier navigeren:

* Consolescherm

  Dit is het standaardformuliertype. Het formulier bestaat uit één pagina.

  ![](assets/console_screen_form.png)

* Contentmanagement

  Gebruik dit formuliertype voor inhoudsbeheer. Zie dit [ gebruiksgeval ](../../delivery/using/use-case-creating-content-management.md).

  ![](../../delivery/using/assets/d_ncs_content_form13.png)

* Assistent

  Dit formulier bestaat uit meerdere zwevende schermen die in een bepaalde reeks zijn geordend. Gebruikers navigeren van het ene scherm naar het andere. [Meer informatie](form-structure.md#wizards).

* Iconbox

  Dit formulier bestaat uit meerdere pagina&#39;s. Gebruikers kunnen door het formulier navigeren door pictogrammen links van het formulier te selecteren.

  ![](assets/iconbox_form_preview.png)

* Laptop

  Dit formulier bestaat uit meerdere pagina&#39;s. Als gebruikers in het formulier willen navigeren, selecteren ze boven aan het formulier tabbladen.

  ![](assets/notebook_form_preview.png)

* Verticaal deelvenster

  In dit formulier wordt een boomstructuur weergegeven.

* Horizontaal venster

  Dit formulier bevat een lijst met items.

## Containers

In formulieren kunt u containers voor verschillende doeleinden gebruiken:

* Inhoud indelen in formulieren
* Toegang tot invoervelden definiëren
* Formulieren nesten in andere formulieren

[Meer informatie](form-structure.md#containers).

### Inhoud ordenen

Gebruik containers om inhoud in formulieren te ordenen:

* U kunt velden groeperen in secties.
* U kunt pagina&#39;s toevoegen aan formulieren met meerdere pagina&#39;s.

Als u een container wilt invoegen, gebruikt u het element `<container>` . [Meer informatie](form-structure.md#containers).

#### Velden groeperen

Gebruik containers om invoervelden te groeperen in georganiseerde secties.

Als u een sectie in een formulier wilt invoegen, gebruikt u het volgende element: `<container type="frame">` . Als u een sectietitel wilt toevoegen, gebruikt u het attribuut `label` .

Syntaxis: `<container type="frame" label="`*section_title*`"> […] </container>`

In dit voorbeeld, bepaalt een container de **sectie van de Aanmaak**, die uit **[!UICONTROL Created by]** en **[!UICONTROL Name]** inputgebieden bestaat:

```xml
<form _cs="Coupons (nms)" entitySchema="xtk:form" img="xtk:form.png" label="Coupons"
      name="coupon" namespace="nms" type="default" xtkschema="xtk:form">
  <input xpath="@code"/>
  <input xpath="@type"/>
  <container label="Creation" type="frame">
    <input xpath="createdBy"/>
    <input xpath="createdBy/@name"/>
  </container>
</form>
```

![](assets/console_screen_form.png)

#### Pagina&#39;s toevoegen aan formulieren met meerdere pagina&#39;s

Voor formulieren met meerdere pagina&#39;s gebruikt u een container om een formulierpagina te maken.

Dit voorbeeld toont containers voor **Algemene** en **Details** pagina&#39;s van een vorm:

```xml
<container img="ncm:book.png" label="General">
[…]
</container>
<container img="ncm:detail.png" label="Details">
[…]
</container>
```

### Toegang tot velden definiëren

Gebruik containers om te definiëren wat zichtbaar is en om de toegang tot velden te definiëren. U kunt groepen velden in- of uitschakelen.

### Formulieren nesten

Gebruik containers om formulieren in andere formulieren te nesten. [Meer informatie](#add-pages-to-multipage-forms).

## Verwijzingen naar afbeeldingen

Als u afbeeldingen wilt zoeken, kiest u **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Images]** in het menu.

Als u een afbeelding wilt koppelen aan een element in het formulier, bijvoorbeeld een pictogram, kunt u een verwijzing naar een afbeelding toevoegen. Gebruik bijvoorbeeld het kenmerk `img` in het element `<container>` .

Syntaxis: `img="`*`namespace`*`:`*`filename`*`.`*`extension`*`"`

In dit voorbeeld worden verwijzingen naar de `book.png` - en `detail.png` -afbeeldingen van de naamruimte `ncm` getoond:

```xml
<container img="ncm:book.png" label="General">
[…]
</container>
<container img="ncm:detail.png" label="Details">
[…]
</container>
```

Deze afbeeldingen worden gebruikt voor pictogrammen waarop gebruikers klikken om door een formulier met meerdere pagina&#39;s te navigeren:

![](assets/nested_forms_preview.png)


## Een eenvoudig formulier maken {#create-simple-form}

Voer de volgende stappen uit om een formulier te maken:

1. Kies in het menu **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Input forms]** .
1. Klik op de knop **[!UICONTROL New]** rechtsboven in de lijst.

   ![](assets/input-form-create-1.png)

1. Geef de formuliereigenschappen op:

   * Geef de naam van het formulier en de naamruimte op.

     De formuliernaam en de naamruimte kunnen overeenkomen met het gerelateerde gegevensschema.  In dit voorbeeld ziet u een formulier voor het `cus:order` -gegevensschema:

     ```xml
     <form entitySchema="xtk:form" img="xtk:form.png" label="Order" name="order" namespace="cus" type="iconbox" xtkschema="xtk:form">
       […]
     </form>
     ```

     U kunt het gegevensschema ook expliciet opgeven in het kenmerk `entity-schema` .

     ```xml
     <form entity-schema="cus:stockLine" entitySchema="xtk:form" img="xtk:form.png" label="Stock order" name="stockOrder" namespace="cus" xtkschema="xtk:form">
       […]
     </form>
     ```

   * Geef het label op dat op het formulier moet worden weergegeven.
   * Geef desgewenst het formuliertype op. Als u geen formuliertype opgeeft, wordt standaard het schermtype voor de console gebruikt.

     ![](assets/input-form-create-2.png)

     Als u een formulier met meerdere pagina&#39;s ontwerpt, kunt u het formuliertype weglaten in het element `<form>` en het type opgeven in een container.

1. Klik op **[!UICONTROL Save]**.

1. Voeg de formulierelementen in.

   Als u bijvoorbeeld een invoerveld wilt invoegen, gebruikt u het element `<input>` . Stel het kenmerk `xpath` in op de veldverwijzing als een XPath-expressie. [Meer informatie](schema-structure.md#referencing-with-xpath).

   In dit voorbeeld worden invoervelden weergegeven op basis van het schema `nms:recipient` .

   ```xml
   <input xpath="@firstName"/>
   <input xpath="@lastName"/>
   ```

1. Als het formulier is gebaseerd op een specifiek schematype, kunt u de velden voor dit schema opzoeken:

   1. Klik op **[!UICONTROL Insert]** > **[!UICONTROL Document fields]** .

      ![](assets/input-form-create-4.png)

   1. Selecteer het veld en klik op **[!UICONTROL OK]** .

      ![](assets/input-form-create-5.png)

1. Geef desgewenst de veldeditor op.

   Een standaardeditor voor velden wordt aan elk gegevenstype gekoppeld:
   * Voor een datumveld wordt in het formulier een invoerkalender weergegeven.
   * Voor een veld van het type opsomming wordt in het formulier een selectielijst weergegeven.

   U kunt de volgende veldeditortypen gebruiken:

   | Veldeditor | Formulierkenmerk |
   | --- | --- |
   | Keuzerondje | `type="radiobutton"` |
   | Selectievakje | `type="checkbox"` |
   | Boomstructuur bewerken | `type="tree"` |

   Lees meer over [ controles van de geheugenlijst ](form-structure.md#memory-list-controls).

1. U kunt ook toegang tot de velden definiëren:

   | Element | Kenmerk | Beschrijving |
   | --- | --- | --- |
   | `<input>` | `read-only="true"` | Biedt alleen-lezen toegang tot een veld |
   | `<container>` | `type="visibleGroup" visibleIf="`*uitgeven-expr*`"` | Hiermee geeft u een groep velden voorwaardelijk weer |
   | `<container>` | `type="enabledGroup" enabledIf="`*uitgeven-expr*`"` | Hiermee wordt een groep velden voorwaardelijk ingeschakeld |

   Voorbeeld:

   ```xml
   <container type="enabledGroup" enabledIf="@gender=1">
     […]
   </container>
   <container type="enabledGroup" enabledIf="@gender=2">
     […]
   </container>
   ```

1. U kunt containers ook gebruiken om velden te groeperen in secties.

   ```xml
   <container type="frame" label="Name">
      <input xpath="@firstName"/>
      <input xpath="@lastName"/>
   </container>
   <container type="frame" label="Contact details">
      <input xpath="@email"/>
      <input xpath="@phone"/>
   </container>
   ```

   ![](assets/input-form-create-3.png)

## Een formulier met meerdere pagina&#39;s maken {#create-multipage-form}

U kunt formulieren met meerdere pagina&#39;s maken. U kunt formulieren ook nesten binnen andere formulieren.

### Een `iconbox` -formulier maken

Met het `iconbox` -formuliertype geeft u pictogrammen weer links van het formulier. Hiermee gaan gebruikers naar verschillende pagina&#39;s in het formulier.

![](assets/iconbox_form_preview.png)

Ga als volgt te werk als u het type van een bestaand formulier wilt wijzigen in `iconbox` :

1. Wijzig het kenmerk `type` van het element `<form>` in `iconbox` :

   ```xml
   <form […] type="iconbox">
   ```

1. Stel een container in voor elke formulierpagina:

   1. Voeg een element `<container>` toe als een onderliggend element van het element `<form>` .
   1. Als u een label en een afbeelding voor het pictogram wilt definiëren, gebruikt u de kenmerken `label` en `img` .

      ```xml
      <form entitySchema="xtk:form" name="Service provider" namespace="nms" type="iconbox" xtkschema="xtk:form">
          <container img="xtk:properties.png" label="General">
              <input xpath="@label"/>
              <input xpath="@name"/>
              […]
          </container>
          <container img="nms:msgfolder.png" label="Details">
              <input xpath="@address"/>
              […]
          </container>
          <container img="nms:supplier.png" label="Services">
              […]
          </container>
      </form>
      ```

   U kunt ook het kenmerk `type="frame"` verwijderen uit de bestaande `<container>` -elementen.

### Een laptopformulier maken

Gebruik het `notebook` -formuliertype om tabbladen boven aan het formulier weer te geven. Hiermee gaan gebruikers naar verschillende pagina&#39;s.

![](assets/notebook_form_preview.png)

Ga als volgt te werk als u het type van een bestaand formulier wilt wijzigen in `notebook` :

1. Wijzig het kenmerk `type` van het element `<form>` in `notebook` :

   ```xml
   <form […] type="notebook">
   ```

1. Voeg een container toe voor elke formulierpagina:

   1. Voeg een element `<container>` toe als een onderliggend element van het element `<form>` .
   1. Gebruik de kenmerken `label` en `img` om het label en de afbeelding voor het pictogram te definiëren.

   ```xml
     <form entitySchema="xtk:form" name="Service provider" namespace="nms" type="notebook" xtkschema="xtk:form">
         <container label="General">
             <input xpath="@label"/>
             <input xpath="@name"/>
             […]
         </container>
         <container label="Details">
             <input xpath="@address"/>
             […]
         </container>
         <container label="Services">
             […]
         </container>
     </form>
   ```

   U kunt ook het kenmerk `type="frame"` verwijderen uit de bestaande `<container>` -elementen.

### Formulieren nesten

U kunt formulieren nesten binnen andere formulieren. U kunt bijvoorbeeld laptopformulieren nesten in iconbox-formulieren.

Het niveau van het nesten controleert navigatie. Gebruikers kunnen naar subformulieren gaan.

Als u een formulier in een ander formulier wilt nesten, voegt u een `<container>` -element in en stelt u het `type` -kenmerk in op het formuliertype. Voor het formulier op het hoogste niveau kunt u het formuliertype instellen in een buitencontainer of in het element `<form>` .

### Voorbeeld

In dit voorbeeld wordt een complex formulier getoond:

* De vorm op hoofdniveau is een iconbox-vorm. Deze vorm bestaat uit twee containers geëtiketteerd **Algemeen** en **Details**.

  Dientengevolge, toont de buitenvorm de **Algemene** en **Details** pagina&#39;s op het hoogste niveau. Gebruikers kunnen deze pagina&#39;s openen door op de pictogrammen links van het formulier te klikken.

* Het subform is een notitieboekjevorm die binnen de **Algemene** container wordt genest. Het subform bestaat uit twee containers die **Naam** en **Contact** worden geëtiketteerd.

```xml
<form _cs="Profile (nms)" entitySchema="xtk:form" img="xtk:form.png" label="Profile" name="profile" namespace="nms" xtkschema="xtk:form">
  <container type="iconbox">
    <container img="ncm:general.png" label="General">
      <container type="notebook">
        <container label="Name">
          <input xpath="@firstName"/>
          <input xpath="@lastName"/>
        </container>
        <container label="Contact">
          <input xpath="@email"/>
        </container>
      </container>
    </container>
    <container img="ncm:detail.png" label="Details">
      <input xpath="@birthDate"/>
    </container>
  </container>
</form>
```

Dientengevolge, toont de **Algemene** pagina van de buitenvorm de **Naam** en **de lusjes van het Contact**.

![](assets/nested_forms_preview.png)

Als u een formulier in een ander formulier wilt nesten, voegt u een `<container>` -element in en stelt u het `type` -kenmerk in op het formuliertype. Voor het formulier op het hoogste niveau kunt u het formuliertype instellen in een buitencontainer of in het element `<form>` .

### Voorbeeld

In dit voorbeeld wordt een complex formulier getoond:

* De vorm op hoofdniveau is een iconbox-vorm. Deze vorm bestaat uit twee containers geëtiketteerd **Algemeen** en **Details**.

  Dientengevolge, toont de buitenvorm de **Algemene** en **Details** pagina&#39;s op het hoogste niveau. Gebruikers kunnen deze pagina&#39;s openen door op de pictogrammen links van het formulier te klikken.

* Het subform is een notitieboekjevorm die binnen de **Algemene** container wordt genest. Het subform bestaat uit twee containers die **Naam** en **Contact** worden geëtiketteerd.

```xml
<form _cs="Profile (nms)" entitySchema="xtk:form" img="xtk:form.png" label="Profile" name="profile" namespace="nms" xtkschema="xtk:form">
  <container type="iconbox">
    <container img="ncm:general.png" label="General">
      <container type="notebook">
        <container label="Name">
          <input xpath="@firstName"/>
          <input xpath="@lastName"/>
        </container>
        <container label="Contact">
          <input xpath="@email"/>
        </container>
      </container>
    </container>
    <container img="ncm:detail.png" label="Details">
      <input xpath="@birthDate"/>
    </container>
  </container>
</form>
```

Dientengevolge, toont de **Algemene** pagina van de buitenvorm de **Naam** en **de lusjes van het Contact**.

![](assets/nested_forms_preview.png)



## Een fabrieksinvoerformulier wijzigen {#modify-factory-form}

Voer de volgende stappen uit om een fabrieksformulier te wijzigen:

1. Het fabrieksinvoerformulier wijzigen:

   1. Kies in het menu **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Input forms]** .
   1. Selecteer een invoerformulier en wijzig dit.

   U kunt schema&#39;s met fabrieksgegevens uitbreiden, maar u kunt geen formulieren met fabrieksinvoer uitbreiden. We raden u aan fabrieksinvoerformulieren rechtstreeks te wijzigen zonder ze opnieuw te maken. Tijdens software-upgrades worden uw wijzigingen in de fabrieksinvoerformulieren samengevoegd met de upgrades. Als het automatisch samenvoegen mislukt, kunt u de conflicten oplossen. [Meer informatie](../../production/using/upgrading.md#resolving-conflicts).

   Als u bijvoorbeeld een fabrieksschema met een extra veld uitbreidt, kunt u dit veld toevoegen aan het gerelateerde fabrieksformulier.

## Formulieren valideren {#validate-forms}

U kunt validatiecontroles opnemen in formulieren.

### Alleen-lezen toegang verlenen tot velden

Gebruik het attribuut `readOnly="true"` om alleen-lezen toegang tot een veld te verlenen. U kunt bijvoorbeeld de primaire sleutel van een record weergeven, maar dan met alleen-lezen toegang. [Meer informatie](form-structure.md#non-editable-fields).

In dit voorbeeld wordt de primaire sleutel (`iRecipientId`) van het `nms:recipient` -schema weergegeven in alleen-lezen toegang:

```xml
<value xpath="@iRecipientId" readOnly="true"/>
```

### Verplichte velden controleren

U kunt verplichte gegevens controleren:

* Gebruik het kenmerk `required="true"` voor de vereiste velden.
* Gebruik het knooppunt `<leave>` om deze velden te controleren en foutberichten weer te geven.

In dit voorbeeld is het e-mailadres vereist en wordt een foutbericht weergegeven als de gebruiker deze informatie niet heeft opgegeven:

```xml
<input xpath="@email" required="true"/>
<leave>
  <check expr="@email!=''">
    <error>The email address is required.</error>
  </check>
</leave>
```

Lees meer over [ uitdrukkingsgebieden ](form-structure.md#expression-field) en [ vormcontext ](form-structure.md#context-of-forms).

### Waarden valideren

U kunt JavaScript-SOAP gebruiken om formuliergegevens te valideren vanuit de Console. Gebruik deze aanroepen voor complexe validatie, bijvoorbeeld om een waarde te controleren op basis van een lijst met toegestane waarden. [Meer informatie](form-structure.md#soap-methods).

1. Maak een validatiefunctie in een JS-bestand.

   Voorbeeld:

   ```js
   function nms_recipient_checkValue(value)
   {
     logInfo("checking value " + value)
     if (…)
     {
       logError("Value " + value + " is not valid")
     }
     return 1
   }
   ```

   In dit voorbeeld heeft de functie de naam `checkValue` . Deze functie wordt gebruikt om het gegevenstype `recipient` in de naamruimte `nms` te controleren. De waarde die wordt gecontroleerd wordt geregistreerd. Als de waarde niet geldig is, wordt een foutbericht geregistreerd. Als de waarde geldig is, wordt de waarde 1 geretourneerd.

   U kunt de geretourneerde waarde gebruiken om het formulier te wijzigen.

1. Voeg in het formulier het element `<soapCall>` toe aan het element `<leave>` .

   In dit voorbeeld wordt een SOAP aanroep gebruikt om de tekenreeks `@valueToCheck` te valideren:

   ```xml
   <form name="recipient" (…)>
   (…)
     <leave>
       <soapCall name="checkValue" service="nms:recipient">
         <param exprIn="@valueToCheck" type="string"/>
       </soapCall>
     </leave>
   </form>
   ```

   In dit voorbeeld worden de methode `checkValue` en de service `nms:recipient` gebruikt:

   * De dienst is namespace en het gegevenstype.
   * De methode is de functienaam. De naam is hoofdlettergevoelig.

   De vraag wordt uitgevoerd synchroon.

   Alle uitzonderingen worden weergegeven. Als u het element `<leave>` gebruikt, kunnen gebruikers het formulier pas opslaan nadat de ingevoerde gegevens zijn gevalideerd.

In dit voorbeeld wordt getoond hoe u serviceaanroepen kunt uitvoeren vanuit formulieren:

```xml
<enter>
  <soapCall name="client" service="c4:ybClient">
    <param exprIn="@id" type="string"/>
    <param type="boolean" xpathOut="/tmp/@count"/>
  </soapCall>
</enter>
```

In dit voorbeeld is de invoer een id, die een primaire sleutel is. Wanneer gebruikers het formulier voor deze id invullen, wordt een SOAP aanroep met deze id uitgevoerd als invoerparameter. De uitvoer is een Booleaanse waarde die naar dit veld wordt geschreven: `/tmp/@count` . U kunt deze Booleaanse waarde in het formulier gebruiken. Lees meer over [ vormcontext ](form-structure.md#context-of-forms).
