---
product: campaign
title: Stappen voor instellen
description: Stappen voor instellen
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
exl-id: a5ae0b61-3377-46d9-a327-6c897eeda770
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 2%

---

# Stappen voor instellen{#setup-stages}

![](../../assets/v7-only.svg)

Het basisbeginsel is dat webtrackingcodes op bepaalde pagina&#39;s van uw website worden geplaatst.

Er zijn twee typen tags:

* **WEB**: dit label geeft aan of de pagina is bezocht;
* **TRANSACTIE**: werkt als een webtag, maar met de mogelijkheid om informatie toe te voegen over het gegenereerde bedrijfsvolume, bijvoorbeeld (transactiebedrag, aantal gekochte items, enz.).

Pas de volgende stappen toe om deze tags in te stellen:

1. Identificeer de pagina&#39;s u wenst om hun type (WEB of TRANSACTIE) te volgen en te bepalen.
1. Bepaal welke aanvullende informatie u wenst te verzamelen, en breid **nms:webTrackingLog** schema met de beschrijving van deze informatie uit. Standaard kunnen in dit schema de transactiehoeveelheden en het aantal items per transactie worden opgeslagen.
1. De webtrackingtags maken. Er zijn twee manieren om dit te doen:

   * Voeg de URL&#39;s die overeenkomen met deze pagina&#39;s in uw Adobe Campaign-platform in en genereer en extraheer de bijbehorende tags voor webtracering (uit het knooppunt **[!UICONTROL Campaign execution>Resources>Web tracking tags]** van de clientconsole).
   * Maak de webtrackingtags zelf in de modus &quot;Aanmaken ter plekke&quot;: De URL&#39;s die overeenkomen met deze pagina&#39;s worden automatisch ingevoegd in uw Adobe Campaign-platform.

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
