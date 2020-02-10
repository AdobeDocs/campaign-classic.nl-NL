---
title: Implementatie
seo-title: Implementatie
description: Implementatie
seo-description: null
page-status-flag: never-activated
uuid: 12b5fbbf-fe0d-4598-8845-f7b8ee7672c3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: use-case
discoiquuid: ac1c0a00-41ef-4cc2-bb51-2808ef400bb1
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Implementatie{#implementation}

Hier is een diagram met de verschillende stappen betrokken in dit scenario.

![](assets/message-center-uc1.png)

Eerst, begin door uw gehechtheid te ontwerpen. Zie dit [artikel](../../delivery/using/attaching-files.md#attach-a-personalized-file). Hierdoor kunt u de bestanden als bijlage aan een e-mail toevoegen, zelfs als deze niet worden gehost op de uitvoeringsinstantie.

U kunt e-mailberichten verzenden via een SOAP-berichttrigger. Zie [Gebeurtenisbeschrijving](../../message-center/using/event-description.md)voor meer informatie over SOAP-aanvragen. In de SOAP-aanroep is er een URL-parameter (bijlageURL).

Klik op **[!UICONTROL Attachment]** . Voer in het **[!UICONTROL Attachment definition]** scherm de parameter SOAP-bijlage in:

```
<%= rtEvent.ctx.attachementUrl %>
```

Wanneer het bericht wordt verwerkt/opgesteld, zal het systeem het dossier van de verre plaats (derdenserver) krijgen en het aan het individuele bericht vastmaken.

Aangezien deze parameter een variabele kan zijn, zou het de volledig gevormde verre URL variabele van uw dossier moeten goedkeuren, die via de vraag van de ZEEP wordt verzonden.

![](assets/message-center-uc2.png)

