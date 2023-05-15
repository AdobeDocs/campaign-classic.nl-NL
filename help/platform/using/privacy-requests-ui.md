---
product: campaign
title: Privacyverzoeken maken
description: Meer informatie over maken en beheren van privacyverzoeken
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: 73b90d79-88b6-4aaf-8103-4564de5e06be
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '771'
ht-degree: 100%

---

# Privacyverzoeken maken en beheren {#privacy-request-ui}



In dit gedeelte wordt beschreven hoe u toegangs- en verwijderingsverzoeken kunt maken en hoe Adobe Campaign deze verwerkt.

## Een privacyverzoek maken {#create-privacy-request-ui}

In de **Adobe Campaign-interface** kunt u uw verzoeken om toegang tot persoonsgegevens maken en de ontwikkeling ervan volgen. Volg deze instructies om een nieuw verzoek om toegang tot persoonsgegevens te maken:

1. Open de map voor verzoeken om toegang tot persoonsgegevens onder **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Privacy Requests]**.

   ![](assets/privacy-requests-folder.png)

1. In dit scherm kunt u alle huidige verzoeken om toegang tot persoonsgegevens, de status en logbestanden ervan bekijken. Klik op **[!UICONTROL New]** om een verzoek om toegang tot persoonsgegevens te maken.

   ![](assets/privacy-request-new.png)

1. Selecteer de **[!UICONTROL Regulation]** (AVG, CCPA, PDPA of LGPD), **[!UICONTROL Request type]** (Toegang of verwijderen), selecteer een **[!UICONTROL Namespace]** en voer de **[!UICONTROL Reconciliation value]** in. Als u e-mail als de naamruimte gebruikt, typt u het e-mailadres van de betrokkene.

   ![](assets/privacy-request-properties.png)

De technische workflows voor privacy worden één keer per dag uitgevoerd en verwerken elk nieuw verzoek:

* Verwijderingsverzoek: de in Adobe Campaign opgeslagen gegevens van de ontvanger worden gewist.
* Toegangsverzoeken: de gegevens van de ontvanger die in Adobe Campaign zijn opgeslagen, worden gegenereerd en beschikbaar gemaakt als XML-bestand in het linkergedeelte van het verzoekscherm.

![](assets/privacy-request-download.png)

## Lijst met tabellen {#list-of-tables}

Bij het uitvoeren van een verzoek om verwijdering of toegang tot persoonsgegevens zoekt Adobe Campaign alle gegevens van de betrokkene op basis van de waarde voor **[!UICONTROL Reconciliation value]** in alle tabellen die een koppeling bevatten naar de ontvangsttabel (eigen type).

Hier volgt de lijst van ingebouwde tabellen waarmee rekening wordt gehouden bij het uitvoeren van verzoeken om toegang tot persoonsgegevens:

* Ontvangers (recipient)
* Verzendingslog ontvangers (broadLogRcp)
* Trackinglog ontvangers (trackingLogRcp)
* Verzendingslog gearchiveerde gebeurtenis (broadLogEventHisto)
* Content van lijst met ontvangers (rcpGrpRel)
* Aanbiedingsvoorstel voor bezoeker (propositionVisitor)
* Bezoekers (visitor)
* Lidmaatschapsgeschiedenis (subHisto)
* Lidmaatschappen (subscription)
* Aanbiedingsvoorstel voor ontvanger (propositionRcp)

Als u aangepaste tabellen hebt gemaakt met een koppeling naar de ontvangsttabel (eigen type), wordt hiermee ook rekening gehouden. Als u bijvoorbeeld een transactietabel hebt met een koppeling naar de ontvangsttabel en een transactiedetailtabel met een koppeling naar de transactietabel, wordt met beide rekening gehouden.

>[!IMPORTANT]
>
>Als u privacybatchverzoeken uitvoert met workflows voor het verwijderen van profielen, moet u rekening houden met het volgende:
>* Bij het verwijderen van profielen via workflows worden geen onderliggende tabellen verwerkt.
>* U moet de onderliggende tabellen zelf verwijderen.
>* Adobe raadt u aan een ETL-workflow te maken waarmee de regels die u wilt verwijderen, worden toegevoegd aan de tabel Privacy Access en de **[!UICONTROL Delete privacy requests data]**-workflow de verwijdering te laten uitvoeren. We raden u aan om maximaal 200 profielen per dag te verwijderen voor optimale prestaties.


## Statussen van privacyverzoeken {#privacy-request-statuses}

Dit zijn de verschillende statussen voor verzoeken om toegang tot persoonsgegevens:

* **[!UICONTROL New]**/**[!UICONTROL Retry pending]**: in uitvoering, de workflow heeft het verzoek nog niet verwerkt.
* **[!UICONTROL Processing]**/**[!UICONTROL Retry in progress]**: de workflow verwerkt het verzoek.
* **[!UICONTROL Delete pending]**: in de workflow zijn alle te verwijderen gegevens van ontvangers geïdentificeerd.
* **[!UICONTROL Delete in progress]**: de workflow verwerkt de verwijdering.
* **[!UICONTROL Delete Confirmation Pending]** (Verwijderingsverzoek in de tweestapsmodus): de workflow heeft het toegangsverzoek verwerkt. De verwijdering moet handmatig worden bevestigd. De knop is 15 dagen beschikbaar.
* **[!UICONTROL Complete]**: de verwerking van het verzoek is zonder fout voltooid.
* **[!UICONTROL Error]**: er is een fout opgetreden in de workflow. De reden wordt weergegeven in de kolom **[!UICONTROL Request status]** in de lijst met verzoeken om toegang tot persoonsgegevens. **[!UICONTROL Error data not found]** betekent bijvoorbeeld dat er in de database geen ontvangersgegevens zijn gevonden die overeenkomen met de **[!UICONTROL Reconciliation value]** van de betrokkene.

## Tweestapsproces {#two-step-process}

Het **tweestapsproces** is standaard geactiveerd. Wanneer u met deze modus een nieuw verwijderingsverzoek maakt, voert Adobe Campaign altijd eerst een toegangsverzoek uit. Op deze manier kunt u de gegevens controleren voordat u de verwijdering bevestigt.

U kunt deze modus wijzigen vanuit het bewerkingsscherm voor verzoeken om toegang tot persoonsgegevens. Klik op **[!UICONTROL Advanced settings]**.

![](assets/privacy-request-advanced-settings.png)

Als de tweestapsmodus is geactiveerd, verandert de status van een nieuw verwijderingsverzoek in **[!UICONTROL Confirm Delete Pending]**. Download het gegenereerde XML-bestand in het scherm voor verzoeken om toegang tot persoonsgegevens en controleer de gegevens. Klik op de knop **[!UICONTROL Confirm delete data]** om het wissen van de gegevens te bevestigen.

![](assets/privacy-request-delete-data.png)

## JSSP-URL {#jspp-url}

Bij het verwerken van toegangsverzoeken produceert Adobe Campaign een JSSP die de gegevens van de ontvanger uit de database ophaalt. Deze gegevens worden geëxporteerd naar een XML-bestand dat op de lokale machine wordt opgeslagen. De JSSP-URL wordt als volgt gedefinieerd:

```
"$(serverUrl)+'/nms/gdpr.jssp?id='+@id"
```

waarbij @id de id voor het verzoek om toegang tot persoonsgegevens is.

Deze URL wordt opgeslagen in het veld **[!UICONTROL "File location" (@urlFile)]** van het schema **[!UICONTROL Privacy Requests (gdprRequest)]**.

De informatie is 90 dagen beschikbaar in de database. Zodra het verzoek door de technische workflow correct is verwerkt, wordt de informatie verwijderd uit de database en wordt de URL onbruikbaar. Controleer of de URL nog geldig is voordat u de gegevens van een webpagina downloadt.

Hier volgt een voorbeeld van het gegevensbestand van een betrokkene:

![](assets/do-not-localize/privacy-access-file.png)

Gegevenscontrollers kunnen eenvoudig een webapplicatie maken, inclusief de bijbehorende JSSP-URL, om het gegevensbestand van de betrokkene beschikbaar te maken via een webpagina.

![](assets/privacy-gdpr-jssp.png)

Hier volgt een codefragment dat u als voorbeeld kunt gebruiken voor de **[!UICONTROL Page]**-activiteit in de webapplicatie.

![](assets/privacy-page-activity.png)

```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd"> <html xmlns="http://www.w3.org/1999/xhtml"> <head> <meta http-equiv="Content-Language" content="en"> <meta http-equiv="Content-Type" content="text/html; charset=utf-8" /> <link rel="stylesheet" type="text/css" href="/nl/webForms/landingPage.css"/> <title>Clickthrough</title> <style type="text/css" media="all"> /* override formulary area */ .formulary { top: 200px; position: absolute; left: 0; } </style> </head> <body style="" class="">
<center>
<div id="wrap">
<div id="header"><img class="nlui-widget" alt="placeholder_header" src="/nms/img/contentModels/placeholder_header.png" unselectable="on" />
<div class="header-title center-title">DOWNLOAD GDPR DATA</div>
<div class="formulary center-formulary"><form>
<div class="button large-button"><a href=[SERVER_URL]/nms/gdpr.jssp?id=13000" data-nl-type="externalLink">CLICK TO DOWNLOAD</a></div>
</form></div>
</div>
<div id="content">
<div class="row">
<div class="info">
<div class="desc">
<div class="title">EFFICIENCY</div>
<div class="desc">Our service is guaranteed to improve your efficiency. Increase performance and use our high-technology service to implement even the most ambitious of projects.</div>
</div>
</div>
</div>
</div>
<div id="footer">
<div style="text-align: center;">
<div style="float: left;"><a href="#">Contact us</a></div>
<div style="float: right;">&copy; Copyrights</div>
<div><a href="#"><img title="facebook" class="nlui-widget" alt="facebook" src="/xtk/img/facebook.png" unselectable="on" /></a> <a href="#"><img title="Twitter" class="nlui-widget" alt="twitter" src="/xtk/img/twitter.png" unselectable="on" /></a> <a href="#"><img title="Google" class="nlui-widget" alt="google_plus" src="/xtk/img/google_plus.png" unselectable="on" /></a> <a href="#"><img title="Linkedin" class="nlui-widget" alt="Linkedin" src="/xtk/img/linkedin.png" unselectable="on" /></a></div>
</div>
</div>
</div>
</center>
</body> </html>
```

Aangezien de toegang tot het gegevensbestand van de betrokkene beperkt is, moet anonieme toegang tot de webpagina worden uitgeschakeld. Alleen een operator met het opgegeven recht **[!UICONTROL Privacy Data Right]** kan zich aanmelden bij de pagina en de gegevens downloaden.
