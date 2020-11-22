---
solution: Campaign Classic
product: campaign
title: Extensievoorbeeld
description: Extensievoorbeeld
audience: interaction
content-type: reference
topic-tags: advanced-parameters
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 3%

---


# Extensievoorbeeld{#extension-example}

In het geval van een binnenkomend contact (callcenter of website) worden de meest relevante aanbiedingen aan een bepaald contact voorgesteld met behulp van een reeks subsidiabiliteitsregels. Als u de geschiktheidscriteria van uw aanbiedingen wilt verrijken, breidt u het schema **nms:interaction** uit.

* Als u een nieuwe interactiecontext wilt toevoegen, breidt u het **nms:interactieschema** uit en maakt u zoveel **kenmerkelementen** als nodig is in het schema.

   In het volgende voorbeeld zijn de toegevoegde criteria de landcode en de laatste bezochte pagina.

   ![](assets/s_ncs_configuration_offer_schemas.png)

* Vervolgens kunt u de eerder gemaakte kenmerken gebruiken bij het definiëren van de definitie van geschiktheidscriteria.

   In het volgende voorbeeld kunnen we geschiktheidscriteria maken om een aanbieding weer te geven op basis van het land van de gebruiker of op de laatste webpagina die ze hebben weergegeven.

   ![](assets/s_ncs_configuration_offer_context.png)

* Wanneer het vormen van de vraag van de ZEEP, neem het **** contextXML element aan verwijzingscontextinformatie op die in het interactieschema wordt toegevoegd. Voor meer informatie, verwijs naar [Integratie via ZEEP (server kant)](../../interaction/using/integration-via-soap--server-side-.md).

