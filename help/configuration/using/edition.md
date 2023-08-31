---
product: campaign
title: Navigatiestructuur van Campagneverkenner bewerken
description: Navigatiestructuur van Campagneverkenner bewerken
feature: Application Settings
role: Data Engineer, Developer
badge-v7-only: label="v7" type="Informative" tooltip="Alleen van toepassing op Campaign Classic v7"
exl-id: 204d4a24-267c-4976-90d9-7bf5bee8d116
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '138'
ht-degree: 5%

---


# Navigatiestructuur van Campagneverkenner bewerken{#edition}

Het scherm voor het maken en configureren van de configuratiedocumenten voor de navigatiehiërarchie is toegankelijk via **[!UICONTROL Administration > Configuration > Navigation hierarchies]** knooppunt:

![](assets/d_ncs_integration_navigation_arbo.png)

De configuratie van de navigatiehiërarchie is verdeeld over verscheidene documenten van XML. Het werkt op een gelijkaardig principe aan schemaverlenging: alle documenten worden samengevoegd om één enkel document te produceren dat de volledige configuratie bevat. Dit document kan niet worden bewerkt en wordt weergegeven via het tabblad Voorbeeld.

Het bewerkingsveld bevat de inhoud van het XML-document:

![](assets/d_ncs_integration_navigation_edit.png)

>[!NOTE]
>
>Met het besturingselement Naam bewerken kunt u de documentsleutel invoeren die bestaat uit de naam en naamruimte. De kenmerken &quot;name&quot; en &quot;namespace&quot; van de **`<navtree>`** het element wordt automatisch bijgewerkt in het XML-bewerkingsveld van het schema.

In de voorvertoning wordt automatisch het samengevoegde document met de volledige configuratie gegenereerd:

![](assets/d_ncs_integration_navigation_preview.png)
