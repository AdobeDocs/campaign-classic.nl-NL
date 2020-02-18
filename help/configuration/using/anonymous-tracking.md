---
title: Anonieme tracking
seo-title: Anonieme tracking
description: Anonieme tracking
seo-description: null
page-status-flag: never-activated
uuid: 21ba3657-eabf-4228-9fc0-e72712bf8fe7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
discoiquuid: 2d2c6ae9-4dba-4b82-a25e-eda65a49572d
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: dbff132e3bf88c408838f91e50e4b047947ee32a

---


# Anonieme tracking{#anonymous-tracking}

Met Adobe Campaign kunt u verzamelde webtraceringsgegevens koppelen aan een ontvanger wanneer deze anoniem door uw site bladert. Wanneer een gebruiker door de gelabelde pagina&#39;s van uw website bladert, worden deze bladergegevens verzameld, zodat deze worden geïdentificeerd en de informatie automatisch wordt gekoppeld aan de pagina&#39;s nadat de gebruiker in een e-mailbericht van Adobe Campaign heeft geklikt.

>[!IMPORTANT]
>
>Door anonieme tracering op een website in te stellen, kan de verzameling van een aanzienlijke hoeveelheid trackinglogbestanden worden geactiveerd, wat invloed heeft op de databasebewerking. Configureer het voorzichtig.\
>Logbestanden voor bijhouden worden opgeslagen in de database totdat de gegevens voor bijhouden zijn gewist. Gebruik de plaatsingstovenaar om de purgefrequentie te vormen. Zie [deze sectie](../../installation/using/deploying-an-instance.md#purging-data)voor meer informatie.

Om anonieme het volgen van het Web op uw instantie toe te laten, moeten de volgende elementen worden gevormd:

* De parameter **trackWebVisitors** van het **omleidingselement** van het **serverConf.xml** - dossier van de volgende server moet aan &quot;**waar**&quot;worden geplaatst, om een permanent koekje (**uuid230**) in browsers van onbekende internetgebruikers te plaatsen die de plaats bezoeken.
* De **Anonieme wijze van het Volgen** van het Web moet in het volgende configuratiescherm van de plaatsingstovenaar worden geselecteerd.

   ![](assets/webtracking_anonymous_set.png)

* Webformulieren en enquêtes moeten worden gepubliceerd en uitgevoerd op de trackingserver. De passende optie moet in de plaatsingstovenaar worden geselecteerd.

   ![](assets/webtracking_publication_set_for_webapps.png)

