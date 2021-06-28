---
product: campaign
title: Anonieme tracking
description: Anonieme tracking
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
exl-id: f251eb21-0f3c-4b46-927a-57a3291e705f
source-git-commit: ee3d643e4ba607b3d7ca816eabf862b867d1f3f4
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 6%

---

# Anonieme tracking{#anonymous-tracking}

Met Adobe Campaign kunt u verzamelde webtraceringsgegevens koppelen aan een ontvanger wanneer deze anoniem door uw site bladert. Wanneer een gebruiker door de gelabelde pagina&#39;s van uw website bladert, worden deze bladergegevens verzameld. Als deze eenmaal in een e-mailbericht van Adobe Campaign klikken, worden ze geïdentificeerd en worden de gegevens automatisch aan de pagina&#39;s gekoppeld.

>[!IMPORTANT]
>
>Door anonieme tracering op een website in te stellen, kan de verzameling van een aanzienlijke hoeveelheid trackinglogbestanden worden geactiveerd, wat invloed heeft op de databasebewerking. Configureer het voorzichtig.\
>Logbestanden voor bijhouden worden opgeslagen in de database totdat de gegevens voor bijhouden zijn gewist. Gebruik de plaatsingstovenaar om de purgefrequentie te vormen. Raadpleeg [deze sectie](../../installation/using/deploying-an-instance.md#purging-data) voor meer informatie.

Om anonieme het volgen van het Web op uw instantie toe te laten, moeten de volgende elementen worden gevormd:

* De **trackWebVisitors**-parameter van het **redirection**-element van het **serverConf.xml**-bestand van de trackingserver moet zijn ingesteld op &#39;**true**&#39; om een permanente cookie (**uuuid230**) te plaatsen>) in de browsers van onbekende internetgebruikers die de site bezoeken.
* De **Anonieme wijze van het Web die** volgen moet in het volgende configuratiescherm van de plaatsingstovenaar worden geselecteerd.

   ![](assets/webtracking_anonymous_set.png)

* Webformulieren moeten worden gepubliceerd en uitgevoerd op de trackingserver. De passende optie moet in de plaatsingstovenaar worden geselecteerd.

   ![](assets/webtracking_publication_set_for_webapps.png)
