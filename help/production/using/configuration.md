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
translation-type: tm+mt
source-git-commit: 849e1ebf14f707d9e86c5a152de978acb6f1cb35
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 2%

---


# Configuratie{#configuration}

## De syslogd-luisterpoort wijzigen {#changing-the-syslogd-listening-port}

Standaard is de **syslogd** luisterpoort 666 (udp). Indien nodig kunt u dit wijzigen met een omgevingsvariabele.

Zodra het wordt gevormd, wordt deze variabele in aanmerking genomen door alle modules van Adobe Campaign.

### In Linux {#in-linux}

Bewerk het bestand **customer.sh** en voeg de volgende regel toe:

```
export TRACE_ADDR=localhost:<listening port>
```

### In Windows {#in-windows}

U moet de omgevingsvariabele **TRACE_ADDR.** met de **localhost** -waarde maken: **`<listening port="" />`**.

>[!IMPORTANT]
>
>We raden u aan enkele tests uit te voeren om ervoor te zorgen dat uw platform werkt nadat u deze omgevingsvariabele hebt gemaakt.

## Beveiligingszones configureren {#configuring-security-zones}

Elke exploitant moet met een streek worden verbonden om aan een geval te login en exploitant IP moet in de adressen of adresreeksen worden omvat die in de veiligheidsstreek worden bepaald. De configuratie van de technische zone wordt uitgevoerd in het configuratiedossier van de server van Adobe Campaign. De verbinding van een exploitant met een veiligheidsstreek moet in de console ( **[!UICONTROL Administration > Access management > Operators]** knoop) worden bepaald.

>[!NOTE]
>
>Raadpleeg [deze sectie](../../installation/using/configuring-campaign-server.md#defining-security-zones)voor meer informatie over het configureren van beveiligingszones.
