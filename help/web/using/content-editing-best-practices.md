---
title: Aanbevolen werkwijzen voor het bewerken van inhoud
seo-title: Aanbevolen werkwijzen voor het bewerken van inhoud
description: Aanbevolen werkwijzen voor het bewerken van inhoud
seo-description: null
page-status-flag: never-activated
uuid: badc6806-b474-4cad-94a3-003a50271281
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: editing-html-content
discoiquuid: 3ad38469-8e22-4bfc-8029-5d360f76d6bb
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c9c9d5f96856ce9e19571bad032d2bf04eaa60bd

---


# Aanbevolen werkwijzen voor het bewerken van inhoud{#content-editing-best-practices}

Om de optimale werking van de redacteur te verzekeren, adviseren wij het naleven van de volgende richtlijnen:

* Voordat u een HTML-paginasjabloon **** importeert in Adobe Campaign, moet u ervoor zorgen dat de sjabloon wordt geopend en correct wordt weergegeven in de verschillende browsers.
* Als de HTML-pagina **JavaScript-scripts** bevat, moeten deze **zonder fouten** buiten de editor worden uitgevoerd.
* Wanneer het bouwen van een malplaatje, adviseren wij toevoegend een **&#39;type&#39;** attribuut aan `<input>` markeringen. Deze informatie zal door de redacteur worden verwerkt en zal de gebruiker helpen om een gebied van het gegevensbestand aan het gebied van de vorm te verbinden wanneer het vormen van de toepassing van het Web.

   Voorbeeld van HTML-code in de sjabloon:

   ```
   <input id="email" type="email" name="email"/>
   ```

   Het kenmerk **&#39;type&#39;** is zichtbaar in de interface in de volgende vorm:

   ![](assets/dce_sidebar_inputtypechanges.png)

   De officiële lijst met &#39;type&#39;-kenmerken is beschikbaar [op deze website](https://www.w3schools.com/tags/att_input_type.asp).

* Stappen om een eindpagina met DCE te simuleren:

   ![](assets/dce_enchainement.png)

* Zorg ervoor dat er slechts één `<body> </body>` op de pagina is.
* Wanneer een CSS- of JS-bestand wordt geüpload, worden de afbeeldingen in het .zip-bestand niet geüpload. De verwijzingen naar deze afbeeldingen in de CSS worden daarom niet bijgewerkt.

## Ondersteunde indelingen voor de inhoudseditor {#content-editor-supported-formats}

De Digital Content Editor ondersteunt de HTML-indeling: u kunt op elk ogenblik overschakelen naar de **bronmodus** .

De functie voor importeren van Digital Content Editor werkt als volgt met de volgende ondersteunde indelingen:

* CSS: de afbeeldingen in het ZIP-bestand worden niet geïmporteerd. De verwijzingen naar deze afbeeldingen in de CSS worden niet bijgewerkt.
* JS: de afbeeldingen in het ZIP-bestand worden niet geïmporteerd. De verwijzingen naar deze afbeeldingen in de JS worden niet bijgewerkt.
* iFrame: de gekoppelde pagina&#39;s worden niet geïmporteerd.
* Openingspagina&#39;s en webapps: als een **formuliertag** ontbreekt, verschijnt er een waarschuwing. A `<form> </form>` moet altijd aanwezig in het berichtlichaam zijn.

De Editor voor digitale inhoud werkt ook met de volgende ondersteunde codepagina&#39;s:

* iso-8859-1
* iso-8859-2
* utf-7
* utf-8 (aanbevolen bij gebruik van een BOM)
* iso-8859-15
* us-ascii
* shift-jis
* iso-2022-jp
* big-5
* euc-kr
* utf-16

>[!NOTE]
>
>De HTML-codepagina moet worden gedefinieerd in een metatag (HTML 4 of HTML 5) of in de BOM. Als er geen codepagina beschikbaar is, opent u het bestand in latin1.

## HTML-inhoudsstatussen {#html-content-statuses}

In het bovenste gedeelte van de editor worden berichten weergegeven die betrekking hebben op de status van de inhoud. De kleurcodes voor de berichten zijn als volgt:

* **Grijsbericht**: informatiebericht, er hoeven geen acties in de redactie te worden uitgevoerd.
* **Blauw bericht**: informatief bericht met betrekking tot de inhoud die wordt bewerkt.
* **Geel bericht**: waarschuwing of foutbericht dat actie namens de gebruiker vereist.

### Lijst met berichten tijdens het bewerken van een webtoepassing {#list-of-messages-when-editing-a-web-application}

* De HTML-inhoud is functioneel.
* De webtoepassing is niet gepubliceerd en kan niet online worden geopend.
* De webtoepassing is online. Publiceer deze opnieuw om eventuele wijzigingen toe te passen.
* De pagina-inhoud is niet functioneel. Het moet een HTML-formulier (`<form>`) bevatten
* Er zijn geen invoerzone(s) of knoppen om te configureren.
* Als u de overgang naar de volgende pagina wilt inschakelen, moet u de actie Volgende pagina koppelen aan een knop of een koppeling op de huidige pagina.

### Lijst met berichten tijdens het bewerken van een levering {#list-of-messages-when-editing-a-delivery}

* De inhoud van de levering is functioneel
* Er zijn geen gebieden of verpersoonlijkingsblokken om te vormen.
* De inhoud van de levering is klaar. Voer de analyse opnieuw uit om eventuele wijzigingen toe te passen.
* De levering is klaar om te worden verzonden.

