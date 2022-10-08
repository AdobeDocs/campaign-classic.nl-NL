---
product: campaign
title: Aanvullende configuratie
description: Configuratie
exl-id: 80d388fd-873c-4a08-b8b6-697988f2a18c
source-git-commit: 40da5774c8a6a228992c4aa400e2d9924215611e
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 1%

---

# Configuratie{#configuration}

![](../../assets/v7-only.svg)

## De syslogd-luisterpoort wijzigen {#changing-the-syslogd-listening-port}

Standaard worden de **syslogd** de luisterpoort is 666 (udp). Indien nodig kunt u dit wijzigen met een omgevingsvariabele.

Zodra het wordt gevormd, wordt deze variabele in aanmerking genomen door alle modules van Adobe Campaign.

### In Linux {#in-linux}

Bewerk de **klant.sh** en voeg de volgende regel toe:

```
export TRACE_ADDR=localhost:<listening port>
```

### In Windows {#in-windows}

U moet de **TRACE_ADDR** omgevingsvariabele met de **localhost** waarde: **`<listening port="" />`**.

>[!IMPORTANT]
>
>We raden u aan enkele tests uit te voeren om ervoor te zorgen dat uw platform werkt nadat u deze omgevingsvariabele hebt gemaakt.

## Beveiligingszones configureren {#configuring-security-zones}

Elke exploitant moet met een streek worden verbonden om aan een geval te login en exploitant IP moet in de adressen of adresreeksen worden omvat die in de veiligheidsstreek worden bepaald. De configuratie van de technische zone wordt uitgevoerd in het configuratiedossier van de server van Adobe Campaign. De koppeling van een exploitant aan een veiligheidsstreek moet in de console worden bepaald ( **[!UICONTROL Administration > Access management > Operators]** knooppunt).

>[!NOTE]
>
>Voor meer bij het vormen van veiligheidsstreken, verwijs naar [deze sectie](../../installation/using/security-zones.md).
