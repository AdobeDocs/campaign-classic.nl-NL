---
title: Bewerking
seo-title: Bewerking
description: Bewerking
seo-description: null
page-status-flag: never-activated
uuid: df9298fc-5f62-4afb-8118-ca7e3987e81f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: navigation-hierarchy
discoiquuid: 820be231-af76-44ce-8f4d-cd5eae1eb169
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '120'
ht-degree: 3%

---


# Bewerking{#edition}

Het scherm voor het creëren van en het vormen van de configuratiedocumenten van de navigatiehiërarchie is toegankelijk via de **[!UICONTROL Administration > Configuration > Navigation hierarchies]** knoop:

![](assets/d_ncs_integration_navigation_arbo.png)

De configuratie van de navigatiehiërarchie is verdeeld over verscheidene documenten van XML. Het werkt op een gelijkaardig beginsel zoals schemauitbreiding: alle documenten worden samengevoegd om één document te genereren dat de volledige configuratie bevat. Dit document kan niet worden bewerkt en wordt weergegeven via het tabblad Voorbeeld.

Het bewerkingsveld bevat de inhoud van het XML-document:

![](assets/d_ncs_integration_navigation_edit.png)

>[!NOTE]
>
>Met het besturingselement Naam bewerken kunt u de documentsleutel invoeren die bestaat uit de naam en naamruimte. De kenmerken &quot;name&quot; en &quot;namespace&quot; van het **`<navtree>`** element worden automatisch bijgewerkt in het XML-bewerkingsveld van het schema.

In de voorvertoning wordt automatisch het samengevoegde document met de volledige configuratie gegenereerd:

![](assets/d_ncs_integration_navigation_preview.png)

