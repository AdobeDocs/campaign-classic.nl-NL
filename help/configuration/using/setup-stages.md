---
title: Stappen instellen
seo-title: Stappen instellen
description: Stappen instellen
seo-description: null
page-status-flag: never-activated
uuid: 4111a805-95ab-4e26-be51-2db1e5c20f57
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
discoiquuid: 76174374-af73-4da0-b62b-6979bca0102b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Stappen instellen{#setup-stages}

Het basisbeginsel is dat webtrackingcodes op bepaalde pagina&#39;s van uw website worden geplaatst.

Er zijn twee typen tags:

* **WEB**: dit label geeft aan of de pagina is bezocht;
* **TRANSACTIE**: werkt als een Web-tag, maar met de mogelijkheid om informatie toe te voegen over het gegenereerde bedrijfsvolume, bijvoorbeeld (transactiebedrag, aantal gekochte items, enz.).

Pas de volgende stappen toe om deze tags in te stellen:

1. Identificeer de pagina&#39;s u wenst om hun type (WEB of TRANSACTIE) te volgen en te bepalen.
1. Bepaal welke aanvullende informatie u wilt verzamelen, en breid het schema **nms:webTrackingLog** met de beschrijving van deze informatie uit. Standaard kunnen in dit schema de transactiehoeveelheden en het aantal items per transactie worden opgeslagen.
1. De webtrackingtags maken. Er zijn twee manieren om dit te doen:

   * Voeg de URL&#39;s die overeenkomen met deze pagina&#39;s in uw Adobe Campagne-platform in en genereer en extraheer de bijbehorende tags voor webtracering (vanuit het **[!UICONTROL Campaign execution>Resources>Web tracking tags]** knooppunt van de clientconsole).
   * Maak de webtrackingtags zelf in de modus &quot;Aanmaken ter plekke&quot;: De URL&#39;s die overeenkomen met deze pagina&#39;s worden automatisch ingevoegd in uw Adobe Campagne-platform.

1. Voeg deze labels statisch of dynamisch toe aan de pagina&#39;s die u wilt bijhouden.

   >[!NOTE]
   >
   >Alle WEB-labels kunnen op dezelfde manier worden toegevoegd aan de pagina&#39;s van uw site. TRANSACTION-tags moeten dynamisch worden gewijzigd of toegevoegd om de aanvullende informatie (hoeveelheid, items, enz.) te kunnen bevatten.

**Voorbeeld**:

```
<script type="text/javascript">
var _f = "nmsWebTracking"
var _t = window.location.href.match(/.*://[^/]*(/[^?#&]*)/)[1] + "|w|" + _f
document.write("<img height='0' width='0' alt='' src='" +
window.location.protocol + "//tsupport/r/" +
Math.random().toString() + "?tagid=" + escape(_t) + "'/>")
</script>
```

