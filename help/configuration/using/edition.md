---
solution: Campaign Classic
product: campaign
title: Bewerking
description: Bewerking
audience: configuration
content-type: reference
topic-tags: navigation-hierarchy
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '119'
ht-degree: 2%

---


# Bewerking{#edition}

Het scherm voor het creëren van en het vormen van de configuratiedocumenten van de navigatiehiërarchie is toegankelijk via de **[!UICONTROL Administration > Configuration > Navigation hierarchies]** knoop:

![](assets/d_ncs_integration_navigation_arbo.png)

De configuratie van de navigatiehiërarchie is verdeeld over verscheidene documenten van XML. Het werkt op een gelijkaardig beginsel zoals schemauitbreiding: alle documenten worden samengevoegd om één document te genereren dat de volledige configuratie bevat. Dit document kan niet worden bewerkt en wordt weergegeven via het tabblad Voorbeeld.

Het bewerkingsveld bevat de inhoud van het XML-document:

![](assets/d_ncs_integration_navigation_edit.png)

>[!NOTE]
>
>Met het besturingselement Naam bewerken kunt u de documentsleutel invoeren die bestaat uit de naam en naamruimte. De kenmerken &quot;name&quot; en &quot;namespace&quot; van het element **`<navtree>`** worden automatisch bijgewerkt in het XML-bewerkingsveld van het schema.

In de voorvertoning wordt automatisch het samengevoegde document met de volledige configuratie gegenereerd:

![](assets/d_ncs_integration_navigation_preview.png)

