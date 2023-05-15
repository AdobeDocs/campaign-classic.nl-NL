---
product: campaign
title: Aanvullende configuratie
description: Configuratie
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
exl-id: 80d388fd-873c-4a08-b8b6-697988f2a18c
source-git-commit: a5762cd21a1a6d5a5f3a10f53a5d1f43542d99d4
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 1%

---

# Configuratie{#configuration}



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
