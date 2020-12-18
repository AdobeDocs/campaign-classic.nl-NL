---
solution: Campaign Classic
product: campaign
title: Publicatiesjablonen
description: Publicatiesjablonen
audience: delivery
content-type: reference
topic-tags: content-management
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '824'
ht-degree: 0%

---


# Publicatiesjablonen{#publication-templates}

## Informatie over publicatiesjablonen {#about-publication-templates}

De publicatiesjabloon is de identiteitskaart van de te publiceren inhoud. Zij verwijst naar de middelen die in het publicatieproces worden gebruikt, d.w.z.:

* het gegevensschema,
* het invoerformulier,
* de transformatiesjablonen voor elk uitvoerdocument.

## Identificatie van een publicatiesjabloon {#identification-of-a-publication-template}

Een publicatiesjabloon wordt aangeduid met de naam en naamruimte ervan.

De identificatiesleutel van een stijlpagina is een tekenreeks die bestaat uit de naamruimte en de naam die door een dubbele punt wordt gescheiden. bijvoorbeeld: **cus:nieuwsbrief**.

>[!NOTE]
>
>In de praktijk wordt het aanbevolen dezelfde sleutel te gebruiken voor het schema, het formulier en de publicatiesjabloon.

## De sjabloon {#creating-and-configuring-the-template} maken en configureren

Publicatiesjablonen worden standaard opgeslagen in het knooppunt **[!UICONTROL Administration > Configuration > Publication templates]**. Als u een nieuwe sjabloon wilt maken, klikt u op de knop **[!UICONTROL New]** boven de lijst met sjablonen.

Als u de publicatiesjabloon wilt configureren, vult u de naam van de sjabloon (d.w.z. de identificatiecode die bestaat uit de naam en de naamruimte), het label, het gegevensschema en het invoerformulier waaraan de sjabloon is gekoppeld.

![](assets/d_ncs_content_model.png)

>[!NOTE]
>
>Het label wordt weergegeven wanneer inhoud wordt gemaakt op basis van deze publicatiesjabloon.

Met de optie **Status controleren om het genereren van inhoud te valideren** wordt een controle van de status &quot;Gevalideerd&quot; van de inhoudsinstanties gedwongen om het genereren van bestanden toe te staan. Raadpleeg [Publicatie](#publication) voor meer informatie hierover.

Voor elk uitvoerdocument moet een transformatiesjabloon worden toegevoegd. U kunt zo veel transformatiesjablonen maken als nodig is.

Het veld **[!UICONTROL Name of template]** is een gratis label dat het type rendering bij de uitvoer beschrijft. Voor elke transformatiesjabloon zijn de publicatie-instellingen beschikbaar op de tabbladen.

### Renderen {#rendering}

Kies het tabblad **[!UICONTROL Rendering]**:

* het type rendering dat wordt gebruikt voor de projectie van het uitvoerdocument: XSL-opmaakmodel of JavaScript-sjabloon,
* de indeling van het uitvoerdocument: HTML, Text, XML of RTF,
* de sjabloon die de constructiegegevens bevat, d.w.z. de te gebruiken stijlpagina of JavaScript-sjabloon.

### Publicatie {#publication}

Bij publicatie wordt het uitvoerdocument gegenereerd in de vorm van een bestand als het geselecteerde type **[!UICONTROL File]** is.

![](assets/d_ncs_content_model2.png)

De volgende publicatieopties zijn beschikbaar:

* De tekenset voor het coderen van uitvoerbestanden kan worden afgedwongen via het veld **[!UICONTROL Encoding]**. De tekenset Latin 1 (1252) wordt standaard gebruikt.
* Met de optie **[!UICONTROL Multi-file generation]** activeert u een speciale documentpublicatiemodus. Deze optie bestaat uit het vullen van een verdelingstag aan het begin van elke pagina van het uitvoerdocument. Als u de inhoud genereert, wordt er een bestand gemaakt voor elke gevulde partitioneringstag. Deze modus wordt gebruikt om mini-sites te genereren op basis van een inhoudsblok. Raadpleeg [Genereren van meerdere bestanden](#multi-file-generation) voor meer informatie hierover.
* Het veld **[!UICONTROL Location]** bevat de naam van het uitvoerbestand. De naam kan uit variabelen worden samengesteld om een automatische filename te produceren.

   Een variabele wordt gevuld met de volgende indeling: **`$(<xpath>)`**, waarbij **`<xpath>`** het pad is van een veld van het gegevensschema van de publicatiesjabloon.

   De naam van een bestand kan een datumveld zijn. Om dit gebied correct te formatteren, gebruik **$date-format** functie, gebruikend de weg van het gebied en het outputformaat als parameters.

   Standaard gebruikt de constructieindeling van de bestandsnaam de variabelen in de velden &quot;@name&quot; en &quot;@date&quot;:

   ```
   ct_$(@name)_$date-format(@date,'%4Y%2M%2D').htm
   ```

   De gegenereerde bestandsnaam ziet er als volgt uit: ct_news12_20110901.htm.

   >[!NOTE]
   >
   >Raadpleeg [Een inhoudsinstantie maken](../../delivery/using/using-a-content-template.md#creating-a-content-instance) voor meer informatie over het genereren van inhoud.

### Levering {#delivery}

Op dit tabblad kunt u een scenario selecteren om een levering rechtstreeks op de inhoud te starten. De inhoud van de e-mail wordt automatisch ingevuld op basis van de uitvoerindeling (HTML of Tekst).

![](assets/d_ncs_content_model3.png)

>[!NOTE]
>
>Raadpleeg [Inhoudsinstantie leveren](../../delivery/using/using-a-content-template.md#delivering-a-content-instance) voor een voorbeeld van het maken van een levering op basis van inhoud.

### Samenvoeging {#aggregator}

Door de gegevens uit een script of querylijst te bundelen, kunt u het XML-document verrijken met de inhoudsgegevens. Het doel is bepaalde informatie waarnaar wordt verwezen door links aan te vullen of elementen uit de database toe te voegen.

### Genereren van meerdere bestanden {#multi-file-generation}

Als u meerdere bestanden wilt genereren, selecteert u de optie **[!UICONTROL Multi-file generation]** in het publicatiemodel. Met deze optie kunt u scheidingsmarkeringen opgeven in de stijlpagina voor het begin van elke pagina van het uitvoerdocument. Het genereren van de inhoud levert een bestand op voor elke partitioneringstag die wordt aangetroffen.

De partitioneringstag die in de stijlpagina moet worden geïntegreerd, ziet er als volgt uit:

**`<xsl:comment> #nl:output_replace(<name_of_file>) </xsl:comment>`** waarbij  **`<name_of_file>`** is de bestandsnaam van de pagina die moet worden gegenereerd.

**Voorbeeld:** Meerdere bestanden genereren met het schema &quot;cus:book&quot;.

Het beginsel is dat een hoofdpagina met een lijst van de hoofdstukken wordt gemaakt, met de mogelijkheid om de details van het hoofdstuk op een externe pagina weer te geven.

![](assets/d_ncs_content_chunk.png)

De bijbehorende stijlpagina (&quot;cus:book.xsl&quot;) ziet er als volgt uit:

```
<?xml version="1.0" encoding="ISO-8859-1" ?>
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">
  <xsl:output encoding="ISO-8859-1" method="html"/>

  <!-- Style sheet entry point -->
  <xsl:template match="/book">
    <html>
      <body>
        <h1><xsl:value-of select="@name"/></h1>
        <lu>
          <xsl:for-each select="chapter">
            <li><a target="_blank" href="chapter{@id}.htm"><xsl:value-of select="@name"/></a></li>  
          </xsl:for-each>
       </lu>
      </body>
    </html>
   </xsl:template>
</xsl:stylesheet>
```

Een tweede stijlblad (&quot;cus:chapter.xsl&quot;) is vereist om de details van de hoofdstukken te produceren:

```
<?xml version="1.0" encoding="ISO-8859-1" ?>
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">
  <xsl:output encoding="ISO-8859-1" method="html"/>

  <!-- Detail of a chapter -->
  <xsl:template match="chapter">
    <!-- Cut tag -->   
    <xsl:comment> #nl:output_replace($(path)/chapter<xsl:value-of select="@id"/>.htm)</xsl:comment>
    
    <html>
      <body>
        <h1><xsl:value-of select="@name"/></h1>
        <xsl:value-of select="page" disable-output-escaping="yes"/>
      </body>
    </html>
  </xsl:template>

  <!-- Style sheet entry point -->
  <xsl:template match="/book">
    <xsl:apply-templates/>
   </xsl:template>
</xsl:stylesheet>
```

De partitioneringstag wordt gevuld aan het begin van de pagina die moet worden opgenomen in het te genereren bestand.

```
<xsl:comment> #nl:output_replace($(path)/<xsl:value-of select="@id"/>.htm)</xsl:comment>
```

De bestandsnaam wordt samengesteld met de variabele **$(path)** die het publicatiepad bevat en **`<xsl:value-of select="@id" />`**, die overeenkomt met de id van het hoofdstuk in het invoerdocument.

In het publicatiemodel moeten de twee opmaakmodellen &quot;cus:book.xsl&quot; en &quot;cus:chapter.xsl&quot; worden ingevuld.

De optie **[!UICONTROL Multi-file generation]** moet actief zijn op het model van de hoofdstuktransformatie:

![](assets/d_ncs_content_chunk2.png)

Het veld **[!UICONTROL Location]** wordt niet gebruikt bij het genereren van meerdere bestanden, maar u moet dit veld toch vullen om een fout bij het publiceren te voorkomen.
