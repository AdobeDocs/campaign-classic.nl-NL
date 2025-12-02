---
product: campaign
title: Stappen voor instellen
description: Stappen voor instellen
feature: Configuration
role: Developer
exl-id: a5ae0b61-3377-46d9-a327-6c897eeda770
source-git-commit: 9f5205ced6b8d81639d4d0cb6a76905a753cddac
workflow-type: tm+mt
source-wordcount: '233'
ht-degree: 2%

---

# Stappen voor instellen{#setup-stages}

Het basisbeginsel is dat webtrackingcodes op bepaalde pagina&#39;s van uw website worden geplaatst.

Er zijn twee typen tags:

* **WEB**: deze markering vertelt u als de pagina is bezocht,
* **TRANSACTIE**: werkt als een Webmarkering, maar met de mogelijkheid om informatie over het geproduceerde bedrijfsvolume, bijvoorbeeld (transactiehoeveelheid, aantal aangekochte punten, enz.) toe te voegen.

Pas de volgende stappen toe om deze tags in te stellen:

1. Identificeer de pagina&#39;s u wenst om hun type (WEB of TRANSACTIE) te volgen en te bepalen.
1. Bepaal welke extra informatie u wenst te verzamelen, en het **nms:webTrackingLog** schema met de beschrijving van deze informatie uit te breiden. Standaard kunnen in dit schema de transactiehoeveelheden en het aantal items per transactie worden opgeslagen.
1. De webtrackingtags maken. Er zijn twee manieren om dit te doen:

   * Voeg de URL&#39;s die overeenkomen met deze pagina&#39;s in uw Adobe Campaign-platform in en genereer en extraheer de bijbehorende tags voor webtracering (vanuit het knooppunt **[!UICONTROL Campaign execution>Resources>Web tracking tags]** van de clientconsole).
   * Maak de webtrackingtags zelf in de modus &quot;Aanmaken ter plekke&quot;: de URL&#39;s die overeenkomen met deze pagina&#39;s worden automatisch ingevoegd in uw Adobe Campaign-platform.

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
