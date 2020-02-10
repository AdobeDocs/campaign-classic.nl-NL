---
title: Automatiseren via workflows
seo-title: Automatiseren via workflows
description: Automatiseren via workflows
seo-description: null
page-status-flag: never-activated
uuid: c77e8b2b-2a2c-4c6e-8497-662e7269e226
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: content-management
discoiquuid: 4abce633-647f-4ae4-9419-859f6e2e8628
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 7dbc876fae0bde78e3088ee1ab986cd09e9bcc38

---


# Automatiseren via workflows{#automating-via-workflows}

## Inhoudsbeheeractiviteiten {#content-management-activity}

Het maken, bewerken en publiceren van inhoud kan worden geautomatiseerd met behulp van een workflow die is geconfigureerd via de Adobe Campagne-clientinterface.

De activiteit van het **inhoudsbeheer** wordt betreden via de **[!UICONTROL Tools]** toolbar van het werkschemadiagram.

Activiteiteneigenschappen worden in vier stappen onderverdeeld:

* **[!UICONTROL Content]** : kunt u bestaande inhoud invoeren of inhoud maken.
* **[!UICONTROL Update content]** : Hiermee kunt u het onderwerp van de inhoud wijzigen of de inhoud bijwerken via een XML-gegevensstroom.
* **[!UICONTROL Action to execute]** : Hiermee kunt u inhoud opslaan of genereren.
* **[!UICONTROL Transition]** : Hiermee kunt u kiezen of u een uitvoerovergang wilt genereren en er een naam voor wilt opgeven.

![](assets/d_ncs_content_wf.png)

### Inhoud {#content}

* **Door de overgang opgegeven**

   De te gebruiken inhoud is eerder gemaakt. Processen hebben betrekking op de inhoudinstantie die door de binnenkomende gebeurtenis wordt doorgegeven. De inhoud-id wordt benaderd via de variabele &quot;contentId&quot; van de gebeurtenis.

* **Expliciet**

   Hiermee kunt u eerder gemaakte inhoud kiezen.

* **Berekend door een script**

   Hiermee selecteert u een inhoudsinstantie op basis van een JavaScript-sjabloon. Met de code die moet worden geëvalueerd, kunt u de inhoud-id ophalen.

* **Nieuw, gemaakt via een publicatiesjabloon**

   Hiermee maakt u nieuwe inhoud via een publicatiesjabloon. De instantie content wordt opgeslagen in de gevulde map &quot;String&quot;.

### De inhoud bijwerken {#update-the-content}

* **Onderwerp**

   Hiermee kunt u het onderwerp van de leveringsactie tijdens het publiceren wijzigen.

* **Toegang tot de gegevens van een XML-feed**

   De inhoud wordt bijgewerkt vanuit een XML-feed van een externe bron. Er moet een URL worden ingevoerd voordat gegevens kunnen worden gedownload.

   Een XSL-opmaakmodel kan worden gebruikt om de inkomende XML-gegevens te transformeren.

### Uit te voeren handeling {#action-to-execute}

* **Opslaan**

   Hiermee slaat u de gemaakte of gewijzigde inhoud op. De id van de opgeslagen inhoud wordt doorgegeven in de variabele &quot;contentId&quot; van de uitgaande gebeurtenis.

* **Genereren**

   Hiermee genereert u de uitvoerbestanden voor elk van de transformatiesjablonen met een publicatie van het type &quot;Bestand&quot;. De uitgaande overgang wordt geactiveerd voor elk geproduceerd dossier, met de volgende parameters: de id van de inhoud die is opgeslagen in de variabele &quot;contentId&quot; en de bestandsnaam in de variabele &quot;filename&quot;.

### Overgang {#transition}

Met de optie **Een uitvoerovergang** genereren kunt u een uitvoerovergang toevoegen aan de **[!UICONTROL Content management]** activiteit om een nieuwe activiteit te koppelen aan de uitvoering van de workflow. Nadat u deze optie hebt ingeschakeld, voert u een label voor de overgang in.

## Voorbeelden {#examples}

### Maken en leveren van inhoud automatiseren {#automating-content-creation-and-delivery}

In het volgende voorbeeld worden het maken en leveren van een inhoudsblok geautomatiseerd.

![](assets/d_ncs_content_workflow2.png)

De inhoud wordt geconfigureerd via de activiteit &quot;Inhoudsbeheer&quot;:

![](assets/d_ncs_content_workflow3.png)

Er wordt een nieuwe instantie van de inhoud gemaakt via het publicatiemodel en de map met de inhoudstekenreeks.

In ons voorbeeld hebben we het bezorgingsonderwerp overbelast. In plaats van de in de **[!UICONTROL Delivery]** template ingevoerde waarde wordt hiermee rekening gehouden.

De inhoud wordt automatisch ingevuld door een XML-feed die afkomstig is van de ingevoerde URL:

```
<?xml version='1.0' encoding='ISO-8859-1'?>
<book name="Content automation test" date="2008/06/08" language="eng" computeString="Content automation test">
  <section id="1" name="Introduction">
    <page>Introduction to input forms.</page>
  </section>
</book>
```

De gegevensindeling komt niet overeen met het gegevensschema dat is ingevoerd in de publicatiesjabloon (**focus:book** in ons voorbeeld). het **`<section>`** element moet door het **`<chapter>`** element worden vervangen. We moeten de stijlpagina &quot;cus:book-workflow.xsl&quot; toepassen om de benodigde wijzigingen aan te brengen.

Broncode van de gebruikte XSLT-stijlpagina:

```
<?xml version="1.0" encoding="utf-8"?>
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
 <xsl:output indent="yes" method="xml"  encoding="ISO-8859-1"/>

 <xsl:template match="text()|@*"/>

  <xsl:template match="*">
    <xsl:variable name="element.name" select="name(.)"/>
    <xsl:element name="{$element.name}">
      <xsl:copy-of select="text()|@*"/>
      <xsl:apply-templates/>
    </xsl:element>
  </xsl:template>

  <xsl:template match="book">
  <book name="test">
     <xsl:apply-templates/>
    <book>
 </xsl:template>

  <xsl:template match="section">
    <chapter>
      <xsl:for-each select="@*">
        <xsl:copy-of select="."/>
      </xsl:for-each>
       <xsl:apply-templates/>
    </chapter>
  </xsl:template>
  
</xsl:stylesheet>
```

De laatste actie van de activiteit is het opslaan van het inhoudsexemplaar en doorgaan naar de volgende taak.

Het richten wordt uitgevoerd via de activiteit van de **Vraag** .

Er is een **AND-join** -activiteit toegevoegd om ervoor te zorgen dat de levering pas wordt gestart als het zoeken naar doelen en het bijwerken van de inhoud zijn voltooid.

De leveringsactie wordt gevormd via de activiteit van de **Levering** :

![](assets/d_ncs_content_workflow4.png)

Er wordt een nieuwe leveringsactie gemaakt op basis van een sjabloon.

De leveringssjabloon van de activiteit wordt gebruikt om de transformatiesjablonen van de publicatiesjabloon te selecteren. Bij het genereren van inhoud wordt rekening gehouden met alle HTML- en tekstsjablonen zonder leveringssjablonen of met sjablonen waarnaar wordt verwezen met dezelfde sjabloon als de activiteit.

Het te leveren doel wordt ingevoerd via de binnenkomende gebeurtenis.

De inhoud van de levering wordt via de binnenkomende gebeurtenis gevuld.

De laatste stap tot het voltooien van de activiteit is het voorbereiden en dan de levering lanceren.

### Inhoud maken en later publiceren {#creating-content-and-publishing-it-later}

In dit voorbeeld wordt een inhoudsblok gemaakt en wordt de bestandspublicatie na een bepaalde tijdvertraging gestart.

![](assets/d_ncs_content_workflow5.png)

Bij de eerste **taak voor inhoudsbeheer** wordt een exemplaar van de inhoud gemaakt.

![](assets/d_ncs_content_workflow6.png)

>[!NOTE]
>
>Het **[!UICONTROL Publication]** tabblad van het venster met transformatiesjablonen moet worden gevuld met de locatie van het te genereren doel.

Een wachtende activiteit wordt toegevoegd om de volgende overgang voor een week te pauzeren.

![](assets/d_ncs_content_workflow7.png)

De inhoud wordt tijdens deze periode handmatig ingevoerd.

De volgende taak start het genereren van inhoud.

![](assets/d_ncs_content_workflow8.png)

De te publiceren inhoud wordt ingevoerd via de inkomende overgang.

De laatste actie bestaat uit het genereren van deze inhoud door de publicatiedirectory te forceren.

Met de **JavaScript-codeactiviteit** wordt de volledige naam van elk gegenereerd bestand opgehaald.

![](assets/d_ncs_content_workflow9.png)

### De levering en de inhoud ervan maken {#creating-the-delivery-and-its-content}

In dit voorbeeld wordt hetzelfde concept gebruikt als in het eerste voorbeeld, alleen wordt de actie voor levering in de eerste stap gemaakt.

![](assets/d_ncs_content_workflow10.png)

De eerste **leveringstaak** maakt de handeling voor levering.

Met de vorkactiviteit kunt u de doelberekening starten en tegelijkertijd de inhoudsinstantie maken.

Zodra de taken zijn uitgevoerd, activeert het EN-sluit vakje de taak van de **Levering** om eerder gecreeerde levering op inhoud en het richten te lanceren.

![](assets/d_ncs_content_workflow11.png)

De te starten leveringsactie wordt via de overgang gevuld.

Het te leveren doel wordt ingevoerd via de binnenkomende gebeurtenis.

De inhoud van de levering wordt via de binnenkomende gebeurtenis gevuld.

De laatste actie van de activiteit is het voorbereiden en lanceren van de levering.

### Inhoud importeren vanuit FTP {#importing-content-from-ftp}

Als uw leveringsinhoud beschikbaar is in een HTML-bestand dat zich op FTP- of SFTP-servers bevindt, kunt u deze inhoud gemakkelijk laden in Adobe Campagne-leveringen. Zie [dit voorbeeld](../../workflow/using/loading-delivery-content.md).

### Inhoud importeren vanuit de Amazon Simple Storage Service (S3)-connector {#importing-content-from-amazon-simple-storage-service--s3--connector}

Als uw leveringsinhoud zich op de emmers van de Eenvoudige Opslagdienst van Amazon (S3) bevindt, kunt u deze inhoud in de levering van de Campagne van Adobe gemakkelijk laden. Zie [dit voorbeeld](../../workflow/using/loading-delivery-content.md).

## Halfautomatische update {#semi-automatic-update}

Inhoudsgegevens kunnen worden bijgewerkt in de modus &quot;semi-automatisch&quot;. De gegevens worden via een URL hersteld via een XML-feed.

De activering van gegevensherstel wordt handmatig uitgevoerd via het invoerformulier.

Het doel is om een **bewerkingstype** in **`<input>`** het formulier te declareren. Dit besturingselement bestaat uit een bewerkingszone en een knop om de verwerking te starten.

In de bewerkingszone kunt u variabele gegevens vullen die worden gebruikt om de URL van de XML-feed met gegevens te maken die moeten worden opgehaald.

De knoop voert de methode van de ZEEP **GetAndTransform** uit die onder de **`<input>`** markering wordt bevolkt.

De controleverklaring is als volgt:

```
<input type="editbtn" xpath="<path>">
  <enter>
    <soapCall name="GetAndTransform" service="ncm:content">
      <param exprIn="<url>" type="string"/>
      <param exprIn="'xtk:xslt|<style sheet>'" type="string"/>
      <param type="DOMElement" xpathOut="<output path>"/>
    </soapCall>
  </enter>
</input>
```

De **methode GetAndTransform** moet onder het **`<enter>`** element van de **`<input>`** markering worden verklaard. Deze tag gebruikt als parameters de URL voor het herstellen van XML-gegevens van een dynamisch geconstrueerde expressie. De tweede parameter van de functie is optioneel en verwijst naar een opmaakmodel dat wordt gebruikt voor een tussenliggende transformatie wanneer de inkomende XML-gegevens niet in dezelfde indeling staan als de inhoud.

De uitvoer werkt de inhoud bij op basis van het pad dat in de laatste parameter is ingevoerd.

**Voorbeeld**: Om dit voorbeeld te illustreren, beginnen we met het schema &quot;cus:book&quot;.

Er wordt een half-automatisch invoerformulier voor het bewerken van updates toegevoegd:

![](assets/d_ncs_content_exemple9.png)

```
<input label="File name" type="editbtn" xpath="/tmp/@name">
  <enter>
    <soapCall name="GetAndTransform" service="ncm:content">
      <param exprIn="'https://server/incoming/' + [/tmp/@name] + '.xml'" type="string"/>
      <param exprIn="'xtk:xslt|cus:book-workflow.xsl'" type="string"/>
      <param type="DOMElement" xpathOut="."/>
    </soapCall>
  </enter>
</input>
```

In de bewerkingszone kunt u de naam invoeren van het bestand dat moet worden opgehaald. De URL wordt samengesteld op basis van bijvoorbeeld deze naam: https://server/incomin/data.xml

De indeling van de gegevens die moeten worden opgehaald, is dezelfde als in voorbeeld 1 van workflowautomatisering. We gebruiken de stijlpagina &#39;cus:book-workflow.xsl&#39; die in dit voorbeeld wordt weergegeven.

Het resultaat van het uitvoeren van een taak is dat de instantie content wordt bijgewerkt met het pad &#39;.&#39;.
