---
product: campaign
title: Extensievoorbeeld
description: Extensievoorbeeld
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: interaction
content-type: reference
topic-tags: advanced-parameters
exl-id: d4acf99b-cef4-48f7-b4cd-c032ec12592f
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 3%

---

# Extensievoorbeeld{#extension-example}



In het geval van een binnenkomend contact (callcenter of website) worden de meest relevante aanbiedingen aan een bepaald contact voorgesteld met behulp van een reeks subsidiabiliteitsregels. Als u de geschiktheidscriteria voor uw aanbiedingen wilt verrijken, breidt u de **nms:interactie** schema.

* Als u een nieuwe interactiecontext wilt toevoegen, breidt u de **nms:interactie** schema en maak zoveel **attribute** elementen in het schema.

   In het volgende voorbeeld zijn de toegevoegde criteria de landcode en de laatste bezochte pagina.

   ![](assets/s_ncs_configuration_offer_schemas.png)

* Vervolgens kunt u de eerder gemaakte kenmerken gebruiken bij het definiëren van de definitie van geschiktheidscriteria.

   In het volgende voorbeeld kunnen we geschiktheidscriteria maken om een aanbieding weer te geven op basis van het land van de gebruiker of op de laatste webpagina die ze hebben weergegeven.

   ![](assets/s_ncs_configuration_offer_context.png)

* Wanneer het vormen van de vraag van de ZEEP, neem **context** XML-element voor verwijzing naar contextinformatie die is toegevoegd in het interactieschema. Zie voor meer informatie [Integratie via SOAP (serverzijde)](../../interaction/using/integration-via-soap--server-side-.md).
