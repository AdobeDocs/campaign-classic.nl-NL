---
title: Geavanceerde functies
seo-title: Geavanceerde functies
description: Geavanceerde functies
seo-description: null
page-status-flag: never-activated
uuid: 4dbf4750-0226-4f96-98d8-ec49b20374ac
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: creating-new-reports
discoiquuid: 0c264783-2775-4ec6-8d49-cd9a45a18d60
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: af768da6ee8cc0ca2ea1f24f297239b974c113a5

---


# Geavanceerde functies{#advanced-functionalities}

## Een script toevoegen {#adding-a-script}

### Scriptactiviteit {#script-activity}

Deze activiteit laat u toe om gegevens te verwerken en gemakkelijk complexe vragen tot stand te brengen die SQL taal niet toelaten.

Voer gewoon uw query in het scriptvenster in.

Op het **[!UICONTROL Texts]** tabblad kunt u tekstreeksen definiëren. Deze kunnen vervolgens met de volgende syntaxis worden gebruikt: **$(id)**. Zie Koptekst en voettekst [toevoegen voor meer informatie over het gebruik van tekst](../../reporting/using/element-layout.md#adding-a-header-and-a-footer).

>[!CAUTION]
>
>We raden u NIET aan JavaScript-code te gebruiken om aggregaten te maken.

Als u een geschiedenis van uw rapport wilt maken, voegt u de volgende regel toe aan uw JavaScript-query om uw gearchiveerde gegevens op te slaan:

```
if( ctx.@_historyId.toString().length == 0 )
```

Anders worden de huidige gegevens weergegeven.

### Extern script {#external-script}

Het is mogelijk een extern script te gebruiken dat aan de server- en/of clientzijde wordt uitgevoerd. Dit doet u als volgt:

1. Bewerk de rapporteigenschappen en klik op de **[!UICONTROL Scripts]** knop.
1. Klik **[!UICONTROL Add]** en selecteer het script waarnaar moet worden verwezen.
1. Selecteer vervolgens de uitvoeringsmodus.

   Als u meerdere scripts toevoegt, gebruikt u de pijlen van de werkbalk om de desbetreffende uitvoeringsvolgorde te definiëren.

   ![](assets/reporting_custom_js.png)

## Een ander rapport opvragen {#calling-up-another-report}

### Snelheid {#jump-activity}

Een sprong is als een overgang zonder pijl: het laat u van één activiteit naar een andere gaan of tot een ander rapport toegang hebben.
