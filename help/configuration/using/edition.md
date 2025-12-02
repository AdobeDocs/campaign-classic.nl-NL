---
product: campaign
title: Navigatiestructuur van Campagneverkenner bewerken
description: Navigatiestructuur van Campagneverkenner bewerken
feature: Application Settings
role: Developer
exl-id: 204d4a24-267c-4976-90d9-7bf5bee8d116
source-git-commit: 9f5205ced6b8d81639d4d0cb6a76905a753cddac
workflow-type: tm+mt
source-wordcount: '131'
ht-degree: 0%

---


# Navigatiestructuur van Campagneverkenner bewerken{#edition}

Het scherm voor het maken en configureren van de configuratiedocumenten van de navigatiehiërarchie is toegankelijk via het knooppunt **[!UICONTROL Administration > Configuration > Navigation hierarchies]** :

![](assets/d_ncs_integration_navigation_arbo.png)

De configuratie van de navigatiehiërarchie is verdeeld over verscheidene documenten van XML. Het werkt op een gelijkaardig principe aan schemaverlenging: alle documenten worden samengevoegd om één enkel document te produceren dat de volledige configuratie bevat. Dit document kan niet worden bewerkt en wordt weergegeven via het tabblad Voorbeeld.

Het bewerkingsveld bevat de inhoud van het XML-document:

![](assets/d_ncs_integration_navigation_edit.png)

>[!NOTE]
>
>Met het besturingselement Naam bewerken kunt u de documentsleutel invoeren die bestaat uit de naam en naamruimte. De kenmerken &quot;name&quot; en &quot;namespace&quot; van het **`<navtree>`** -element worden automatisch bijgewerkt in het XML-bewerkingsveld van het schema.

In de voorvertoning wordt automatisch het samengevoegde document met de volledige configuratie gegenereerd:

![](assets/d_ncs_integration_navigation_preview.png)
