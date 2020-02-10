---
title: Configuratie
seo-title: Configuratie
description: Configuratie
seo-description: null
page-status-flag: never-activated
uuid: 4316d4b2-0964-4e25-9e4f-f2378f044c85
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: production-procedures
discoiquuid: 12f13b8d-afc3-4b55-a31b-080d31f84fc9
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 779d9162b7296339a796512838612ede1186ddcc

---


# Configuratie{#configuration}

## De syslogd-luisterpoort wijzigen {#changing-the-syslogd-listening-port}

Standaard is de **syslogd** luisterpoort 666 (udp). Indien nodig kunt u dit wijzigen met een omgevingsvariabele.

Zodra het wordt gevormd, wordt deze variabele in aanmerking genomen door alle modules van de Campagne van Adobe.

### In Linux {#in-linux}

Bewerk het bestand **customer.sh** en voeg de volgende regel toe:

```
export TRACE_ADDR=localhost:<listening port>
```

### In Windows {#in-windows}

U moet de de omgevingsvariabele **TRACE_ADDR.** met de **localhost** waarde tot stand brengen: **`<listening port="" />`**.

>[!CAUTION]
>
>We raden u aan enkele tests uit te voeren om ervoor te zorgen dat uw platform werkt nadat u deze omgevingsvariabele hebt gemaakt.

## Beveiligingszones configureren {#configuring-security-zones}

Elke exploitant moet met een streek worden verbonden om aan een geval te login en exploitant IP moet in de adressen of adresreeksen worden omvat die in de veiligheidsstreek worden bepaald. Configuratie van de technische zones wordt uitgevoerd in het configuratiebestand van de Adobe Campagneserver. De verbinding van een exploitant met een veiligheidsstreek moet in de console ( **[!UICONTROL Administration > Access management > Operators]** knoop) worden bepaald.

>[!NOTE]
>
>Raadpleeg [deze sectie](../../installation/using/configuring-campaign-server.md#defining-security-zones)voor meer informatie over het configureren van beveiligingszones.

