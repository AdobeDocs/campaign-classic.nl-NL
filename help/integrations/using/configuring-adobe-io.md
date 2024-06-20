---
product: campaign
title: Ontwikkelaarsconsole voor Adobe Experience Cloud Triggers configureren
description: Meer informatie over het configureren van Developer Console Adobe Experience Cloud Triggers
feature: Triggers
audience: integrations
content-type: reference
index: y
internal: n
snippet: y
exl-id: ab30f697-3022-4a29-bbdb-14ca12ec9c3e
hide: true
hidefromtoc: true
source-git-commit: 8de62db2499449fc9966b6464862748e2514a774
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 1%

---

# Ontwikkelaarsconsole voor Adobe Experience Cloud Triggers configureren {#configuring-adobe-io}

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

* een geldige **Organisatie-id**: de organisatie-id is de unieke id in de Adobe Experience Cloud, die bijvoorbeeld wordt gebruikt voor de service VisitorID en de IMS Single-Sign On (SSO). [Meer informatie](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=nl)
* a **Toegang voor ontwikkelaars** aan uw organisatie. De systeembeheerder van de organisatie moet de **Ontwikkelaars toevoegen aan één productprofiel** procedure [op deze pagina](https://helpx.adobe.com/enterprise/using/manage-developers.html) om ontwikkelaarstoegang voor `Analytics - {tenantID}` Productprofiel van het Adobe Analytics-product dat is gekoppeld aan Triggers.

## Stap 1: Een OAuth-project maken/bijwerken {#creating-adobe-io-project}

>[!AVAILABILITY]
>
> De referentie van de Rekening van de Dienst (JWT) wordt afgekeurd door Adobe, de integratie van de Campagne met de oplossingen van de Adobe en apps moet nu op server-aan-server referentie van OAuth vertrouwen. </br>
>
> * Als u ingebouwde integratie met Campagne hebt uitgevoerd, moet u uw Technische Rekening migreren zoals die in [deze documentatie](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/#_blank). De bestaande geloofsbrieven van de Rekening van de Dienst (JWT) zullen tot 27 Januari, 2025 blijven werken.</br>
>
> * Als u uitgaande integratie hebt geïmplementeerd, zoals integratie met Campaign-Analytics of Experience Cloud Triggers, blijven ze tot 27 januari 2025 werken. Nochtans, vóór die datum, moet u uw milieu van de Campagne aan v7.4.1 bevorderen en uw Technische Rekening migreren aan Auth.

Als u verder wilt gaan met het configureren van uw Adobe Analytics-connector, opent u de Adobe Developer-console en maakt u uw OAuth Server-to-Server-project.

Zie [deze pagina](oauth-technical-account.md#oauth-service) voor de gedetailleerde documentatie.

## Stap 2: Voeg de projectgeloofsbrieven in Adobe Campaign toe {#add-credentials-campaign}

Voer de in [deze pagina](oauth-technical-account.md#add-credentials) om uw OAuth projectgeloofsbrieven in Adobe Campaign toe te voegen.

## Stap 3: De tag pipelined bijwerken {#update-pipelined-tag}

Bijwerken [!DNL pipelined] tag, moet u het verificatietype bijwerken naar het project Developer Console in het configuratiebestand **config-&lt; instance-name >.xml** als volgt:

```
<pipelined ... authType="imsJwtToken"  ... />
```

Voer vervolgens een `config -reload` en het opnieuw opstarten van de [!DNL pipelined] voor de in aanmerking te nemen wijzigingen.
