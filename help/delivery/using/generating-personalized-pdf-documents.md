---
product: campaign
title: Gepersonaliseerde PDF-documenten genereren
description: Leer hoe u persoonlijke PDF-documenten kunt genereren
badge-v7: label="v7" type="Informative" tooltip="Is van toepassing op Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
feature: Personalization
role: User
exl-id: e5239d99-256b-412b-be20-f64f822da9c3
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '455'
ht-degree: 1%

---

# Gepersonaliseerde PDF-documenten genereren{#generating-personalized-pdf-documents}

## Variabele PDF-documenten {#about-variable-pdf-documents}

Met Adobe Campaign kunt u variabele PDF-documenten voor e-mailbijlagen genereren vanuit LibreOffice- of Microsoft Word-documenten.

De volgende extensies worden ondersteund: &quot;.docx&quot;, &quot;.doc&quot; en &quot;.odt&quot;.

Voor het aanpassen van uw documenten zijn dezelfde JavaScript-functies beschikbaar als voor het aanpassen van e-mails.

U moet de **[!UICONTROL "The content of the file is personalized and converted to PDF during the delivery of each message"]** -optie. Deze optie is toegankelijk wanneer u het bestand bijvoegt bij de e-mail voor levering. Voor meer informatie over het bijvoegen van een berekend bestand raadpleegt u de [Bestanden bijvoegen](attaching-files.md) sectie.

Voorbeeld van een personalisatie van de factuurheader:

![](assets/s_ncs_pdf_simple.png)

Als u dynamische tabellen wilt genereren of afbeeldingen wilt opnemen via een URL, moet u een specifiek proces volgen.

## Dynamische tabellen genereren {#generating-dynamic-tables}

De procedure voor het genereren van dynamische tabellen is als volgt:

* Maak een tabel met drie regels en zoveel kolommen als nodig zijn en configureer de indeling (randen, enzovoort).
* Plaats de cursor op de tabel en klik op de knop **[!UICONTROL Table > Table properties]** -menu. Ga naar de **[!UICONTROL Table]** en voert u een naam in die begint met **NlJsTable**.
* Definieer in de eerste cel van de eerste regel een lus (&quot;for&quot;, bijvoorbeeld) die herhaling mogelijk maakt voor de waarden die u in de tabel wilt weergeven.
* Voeg in elke cel van de tweede regel van de tabel scripts in die de waarden retourneren die u wilt weergeven.
* Sluit de lus in de derde en laatste regel van de tabel.

  Voorbeeld van een dynamische tabeldefinitie:

  ![](assets/s_ncs_pdf_table.png)

## Externe afbeeldingen invoegen {#inserting-external-images}

Het invoegen van externe afbeeldingen is handig als u bijvoorbeeld een document wilt personaliseren met een afbeelding waarvan de URL is ingevoerd in een veld van de ontvanger.

Om dit te doen, moet u een verpersoonlijkingsblok vormen, dan een vraag aan het verpersoonlijkingsblok in de gehechtheid omvatten.

**Voorbeeld: een gepersonaliseerd logo invoegen, afhankelijk van het land van de ontvanger**

**Stap 1: maak de bijlage:**

* Neem de vraag aan het verpersoonlijkingsblok op: **&lt;%@ include view=&quot;blockname&quot; %>**.
* Plaats de (al dan niet gepersonaliseerde) inhoud in de hoofdtekst van het bestand.

![](assets/s_ncs_open_office_blocdeperso.png)

**Stap 2: creeer het verpersoonlijkingsblok:**

* Ga naar de **[!UICONTROL Resources > Campaign management > Personalization blocks]** menu van de Adobe Campaign-console.
* Maak een nieuw &#39;Mijn logo&#39;-personalisatieblok met &#39;Mijn logo&#39; als interne naam.
* Klik op de knop **[!UICONTROL Advanced parameters...]** de verbinding controleert dan **[!UICONTROL "The content of the block is included in an attachment"]** -optie. Hierdoor kunt u de definitie van het verpersoonlijkingsblok rechtstreeks naar de inhoud van het OpenOffice-bestand kopiëren.

  ![](assets/s_ncs_pdf_bloc_option.png)

  U moet twee soorten verklaringen binnen het verpersoonlijkingsblok onderscheiden:

   * De Adobe Campaign-code van de personalisatievelden waarvoor de &quot;open&quot; en &quot;gesloten&quot; haakjes moeten worden vervangen door escape-tekens (respectievelijk `&lt;` en `&gt;`).
   * De volledige XML-code van OpenOffice wordt naar het OpenOffice-document gekopieerd.

In het voorbeeld ziet het verpersoonlijkingsblok er als volgt uit:

```
<% if (recipient.country.label == "Germany") { %>
<draw:frame svg:width="4cm" svg:height="3cm">
<draw:image xlink:href=https://..../logo_germany.png />
</draw:frame>
<% } else
if (recipient.country.label == "USA")
{ %>
<draw:frame svg:width="4cm" svg:height="3cm">
<draw:image xlink:href=https://..../logo_USA.png />
</draw:frame>
<% } %>
```

Afhankelijk van het land van de ontvanger is personalisatie zichtbaar in het document dat aan de levering is gekoppeld:

![](assets/s_ncs_pdf_result.png)
