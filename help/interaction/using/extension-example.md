---
title: Extensievoorbeeld
seo-title: Extensievoorbeeld
description: Extensievoorbeeld
seo-description: null
page-status-flag: never-activated
uuid: 6703b6e8-4eac-4a94-a80a-a7cd71b25cdf
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: advanced-parameters
discoiquuid: 990b6cbc-9b7b-4278-a635-653d5abafe87
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

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

