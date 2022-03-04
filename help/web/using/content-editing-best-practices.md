---
product: campaign
title: Best practices voor het bewerken van content
description: Best practices voor het bewerken van content
feature: Web Apps, Web Forms, Landing Pages
exl-id: c1eccb48-59bf-412f-9c18-9cda2a022096
source-git-commit: b6f1556cf49492cefaf61c29a058584b0ccee16a
workflow-type: tm+mt
source-wordcount: '548'
ht-degree: 6%

---

# Best practices voor het bewerken van content{#content-editing-best-practices}

![](../../assets/common.svg)

Om de optimale werking van de redacteur te verzekeren, adviseren wij het naleven van de volgende richtlijnen:

* Voor **een HTML-paginasjabloon importeren** in Adobe Campaign moet u ervoor zorgen dat de sjabloon wordt geopend en correct wordt weergegeven in de verschillende browsers.
* Als de pagina HTML bevat **JavaScript-scripts** moeten worden uitgevoerd **zonder fouten** buiten de editor.
* Bij het samenstellen van een sjabloon wordt aangeraden een **&#39;type’**-attribuut toe te voegen aan tags. `<input>` Deze informatie zal door de redacteur worden verwerkt en zal de gebruiker helpen om een gebied van het gegevensbestand aan het gebied van de vorm te verbinden wanneer het vormen van de toepassing van het Web.

   Voorbeeld van HTML-code in de sjabloon:

   ```
   <input id="email" type="email" name="email"/>
   ```

   De **&#39;type&#39;** Het kenmerk is zichtbaar in de interface in het volgende formulier:

   ![](assets/dce_sidebar_inputtypechanges.png)

   De officiële lijst met &#39;type&#39;-kenmerken is beschikbaar [op deze website](https://www.w3schools.com/tags/att_input_type.asp).

* Stappen om een eindpagina met DCE te simuleren:

   ![](assets/dce_enchainement.png)

* Zorg ervoor dat er slechts één is `<body> </body>` op de pagina.
* Wanneer een CSS- of JS-bestand wordt geüpload, worden de afbeeldingen in het .zip-bestand niet geüpload. De verwijzingen naar deze afbeeldingen in de CSS worden daarom niet bijgewerkt.

## Ondersteunde indelingen voor de inhoudseditor {#content-editor-supported-formats}

De Editor voor digitale inhoud ondersteunt de HTML-indeling: u kunt overschakelen op **bron** op elk gewenst moment.

De functie voor importeren van Digital Content Editor werkt als volgt met de volgende ondersteunde indelingen:

* CSS: de afbeeldingen in het ZIP-bestand worden niet geïmporteerd. De verwijzingen naar deze afbeeldingen in de CSS worden niet bijgewerkt.
* JS: de afbeeldingen in het ZIP-bestand worden niet geïmporteerd. De verwijzingen naar deze afbeeldingen in het JS worden niet bijgewerkt.
* iFrame: de gekoppelde pagina&#39;s worden niet geïmporteerd.
* Openingspagina&#39;s en webapps: als **formulier** -tag ontbreekt. Er wordt een waarschuwing weergegeven. A `<form> </form>` moet altijd aanwezig zijn in de berichttekst.

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
>De pagina met de HTML-code moet worden gedefinieerd in een metatag (HTML 4 of HTML 5) of in de BOM. Als er geen codepagina beschikbaar is, opent u het bestand in latin1.

## HTML-inhoudsstatus {#html-content-statuses}

In het bovenste gedeelte van de editor worden berichten weergegeven die betrekking hebben op de status van de inhoud. De kleurcodes voor de berichten zijn als volgt:

* **Grijsbericht**: informatiebericht, er hoeven geen acties in de redactie te worden uitgevoerd.
* **Blauw bericht**: informatief bericht met betrekking tot de inhoud die wordt bewerkt.
* **Geel bericht**: waarschuwing of foutbericht dat actie namens de gebruiker vereist.

### Lijst met berichten tijdens het bewerken van een webtoepassing {#list-of-messages-when-editing-a-web-application}

* De inhoud van de HTML is functioneel.
* De webtoepassing is niet gepubliceerd en kan niet online worden geopend.
* De webtoepassing is online. Publiceer deze opnieuw om eventuele wijzigingen toe te passen.
* De pagina-inhoud is niet functioneel. Het moet een HTML-formulier bevatten (`<form>`)
* Er zijn geen invoerzone(s) of knoppen om te configureren.
* Als u de overgang naar de volgende pagina wilt inschakelen, moet u de actie Volgende pagina koppelen aan een knop of een koppeling op de huidige pagina.

### Lijst met berichten tijdens het bewerken van een levering {#list-of-messages-when-editing-a-delivery}

* De inhoud van de levering is functioneel
* Er zijn geen gebieden of verpersoonlijkingsblokken om te vormen.
* De inhoud van de levering is klaar. Voer de analyse opnieuw uit om eventuele wijzigingen toe te passen.
* De levering is klaar om te worden verzonden.
