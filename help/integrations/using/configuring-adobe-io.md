---
product: campaign
title: Developer Console voor Adobe Experience Cloud Triggers configureren
description: Leer hoe u Developer Console Adobe Experience Cloud Triggers configureert
feature: Triggers
audience: integrations
content-type: reference
index: y
internal: n
snippet: y
exl-id: ab30f697-3022-4a29-bbdb-14ca12ec9c3e
hide: true
hidefromtoc: true
source-git-commit: 8d15a5666b5768bc0f17a4391061c4fcb9f76811
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Developer Console voor Adobe Experience Cloud Triggers configureren {#configuring-adobe-io}

<!--
>[!CAUTION]
>
>If you are using an older version of Triggers integration through oAuth authentication, **you need to move to Adobe I/O as described below**. 
>Note that during this move to [!DNL Adobe I/O], some incoming triggers may be lost.
>
>Legacy oAuth authentication mode with Campaign has been retired on **October 20, 2021**. Hosted environments benefit from an extension until **May 25, 2022**. As an on-premise or hybrid customer, contact Adobe Customer Care to extend support to **May 2022**. You must [provide the AppID of the OAuth application](../../integrations/using/configuring-pipeline.md#step-optional) to Adobe.
-->

## Vereisten {#adobe-io-prerequisites}

<!--
This integration only applies starting **Campaign Classic 20.2.4 and above, 19.1.8 and Gold Standard 11 releases**.
-->

Controleer voordat u met deze implementatie begint of:

* a geldig **herkenningsteken van de Organisatie**: identiteitskaart van de Organisatie is het unieke herkenningsteken binnen Adobe Experience Cloud, dat bijvoorbeeld voor de dienst VisitorID en IMS wordt gebruikt Single-Sign On (SSO). [Meer informatie](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=nl)
* a **toegang van de Ontwikkelaar** tot uw Organisatie. De beheerder van het Systeem van de organisatie moet **volgen ontwikkelaars aan één enkel productprofiel** gedetailleerde procedure [ in deze pagina ](https://helpx.adobe.com/enterprise/using/manage-developers.html) toevoegen om ontwikkelaartoegang voor het `Analytics - {tenantID}` Profiel van het Product van Adobe Analytics verbonden aan Trekkers te verlenen.

## Stap 1: Een OAuth-project maken/bijwerken {#creating-adobe-io-project}

>[!AVAILABILITY]
>
> De referentie van de Rekening van de Dienst (JWT) wordt afgekeurd door Adobe, de integratie van de Campagne met de oplossingen van de Adobe en apps moet nu op server-aan-server referentie van OAuth vertrouwen. </br>
>
> * Als u binnenkomende integratie met Campagne hebt uitgevoerd, moet u uw Technische Rekening zoals die in [ wordt gedetailleerd deze documentatie ](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/#_blank) migreren. De bestaande [ geloofsbrieven van de Rekening van de Dienst (JWT) ](oauth-technical-account.md) zullen tot 27 Januari, 2025 blijven werken.</br>
>
> * Als u uitgaande integratie hebt geïmplementeerd, zoals integratie met Campaign-Analytics of Experience Cloud Triggers, blijven ze tot 27 januari 2025 werken. Nochtans, vóór die datum, moet u uw milieu van de Campagne aan v7.4.1 bevorderen en uw Technische Rekening migreren aan Auth.

Als u verder wilt gaan met het configureren van uw Adobe Analytics-connector, opent u de Adobe Developer-console en maakt u uw OAuth Server-to-Server-project.

Verwijs naar [ deze pagina ](oauth-technical-account.md#oauth-service) voor de gedetailleerde documentatie.

## Stap 2: Voeg de projectgeloofsbrieven in Adobe Campaign toe {#add-credentials-campaign}

Volg de stappen die in [ worden gedetailleerd deze pagina ](oauth-technical-account.md#add-credentials) om uw OAuth projectgeloofsbrieven in Adobe Campaign toe te voegen.

## Stap 3: De tag pipelined bijwerken {#update-pipelined-tag}

Om [!DNL pipelined] markering bij te werken, moet u het authentificatietype aan het de consoleproject van de Ontwikkelaar in het configuratiedossier **config-&lt; instantie-name >.xml** als volgt bijwerken:

```
<pipelined ... authType="imsJwtToken"  ... />
```

Voer vervolgens een `config -reload` en een nieuwe start van de [!DNL pipelined] uit om rekening te houden met de wijzigingen.
