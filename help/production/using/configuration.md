---
solution: Campaign Classic
product: campaign
title: Configuratie
description: Configuratie
audience: production
content-type: reference
topic-tags: production-procedures
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '163'
ht-degree: 1%

---


# Configuratie{#configuration}

## De syslogd luisterpoort {#changing-the-syslogd-listening-port} wijzigen

Standaard is de **syslogd** luisterpoort 666 (udp). Indien nodig kunt u dit wijzigen met een omgevingsvariabele.

Zodra het wordt gevormd, wordt deze variabele in aanmerking genomen door alle modules van Adobe Campaign.

### In Linux {#in-linux}

Bewerk het bestand **customer.sh** en voeg de volgende regel toe:

```
export TRACE_ADDR=localhost:<listening port>
```

### In Windows {#in-windows}

U moet de **TRACE_ADDR** omgevingsvariabele met de **localhost** waarde tot stand brengen: **`<listening port="" />`**.

>[!IMPORTANT]
>
>We raden u aan enkele tests uit te voeren om ervoor te zorgen dat uw platform werkt nadat u deze omgevingsvariabele hebt gemaakt.

## Beveiligingszones {#configuring-security-zones} configureren

Elke exploitant moet met een streek worden verbonden om aan een geval te login en exploitant IP moet in de adressen of adresreeksen worden omvat die in de veiligheidsstreek worden bepaald. De configuratie van de technische zone wordt uitgevoerd in het configuratiedossier van de server van Adobe Campaign. De verbinding van een exploitant aan een veiligheidsstreek moet in de console worden bepaald ( **[!UICONTROL Administration > Access management > Operators]** knoop).

>[!NOTE]
>
>Raadpleeg [deze sectie](../../installation/using/configuring-campaign-server.md#defining-security-zones) voor meer informatie over het configureren van beveiligingszones.
