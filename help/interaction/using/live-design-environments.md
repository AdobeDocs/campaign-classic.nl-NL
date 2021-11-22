---
product: campaign
title: Live/Design-omgevingen
description: Live/Design-omgevingen
audience: interaction
content-type: reference
topic-tags: managing-environments
exl-id: 965c4a6a-6535-454d-bd37-e9c8312b4d13
source-git-commit: 8b970705f0da6a9e09de9fadb3e1a8c5f4814f9f
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 2%

---

# Live/Design-omgevingen{#live-design-environments}

![](../../assets/v7-only.svg)

## Werkwijze {#operating-principle}

De interactie werkt met twee soorten aanbiedingsmilieu&#39;s:

* **[!UICONTROL Design]** bieden omgevingen aan die aanbiedingen bevatten die worden bewerkt en kunnen worden gewijzigd. Deze aanbiedingen zijn niet door de goedkeuringscyclus geweest en niet geleverd aan contacten.
* **[!UICONTROL Live]** bieden omgevingen aan die goedgekeurde aanbiedingen bevatten terwijl deze aan contactpersonen worden aangeboden. De aanbiedingen in deze omgeving zijn alleen-lezen.

![](assets/offer_environments_overview_001.png)

Elk **[!UICONTROL Design]** milieu is gekoppeld aan een **[!UICONTROL Live]** milieu. Wanneer een aanbieding is voltooid, worden de inhoud en de subsidiabiliteitsregels ervan onderworpen aan een goedkeuringscyclus. Zodra deze cyclus is voltooid, wordt het desbetreffende aanbod automatisch aan de **[!UICONTROL Live]** milieu. Vanaf dat moment is het beschikbaar voor levering.

De interactie wordt standaard geleverd met een **[!UICONTROL Design]** milieu en **[!UICONTROL Live]** omgeving. Beide milieu&#39;s worden pre-gevormd om de uit-van-de-doos ontvankelijke lijst te richten.

>[!NOTE]
>
>Als u een andere tabel als doel wilt instellen (bezoekerstabel voor anonieme aanbiedingen of een specifieke tabel voor ontvangers), moet u de wizard voor doeltoewijzing gebruiken om de omgevingen te maken. Raadpleeg voor meer informatie hierover [Een aanbiedingsomgeving maken](#creating-an-offer-environment).

![](assets/offer_environments_overview_002.png)

De managers van de aanbieding en de leveringsmanagers hebben toegang tot verschillende meningen van het milieu. Leveringsmanagers kunnen alleen de **[!UICONTROL Live]** bieden milieu en gebruiksaanbiedingen aan om hen te leveren. Aanbiedingsmanagers kunnen de **[!UICONTROL Design]** milieu en bekijk **[!UICONTROL Live]** milieu. Raadpleeg voor meer informatie hierover [Operatorprofielen](../../interaction/using/operator-profiles.md).

## Een aanbiedingsomgeving maken {#creating-an-offer-environment}

Door gebrek, komt de Interactie met een vooraf gevormd milieu om de ontvankelijke lijst (geïdentificeerde aanbiedingen) te richten. Als u een andere tabel (bezoekerstabel voor anonieme aanbiedingen of een specifieke tabel voor ontvangers) als doel wilt instellen, moet u de volgende configuraties toepassen:

1. Plaats de cursor op de knop **[!UICONTROL Administration]** > **[!UICONTROL Campaign management]** > **[!UICONTROL Delivery mappings]** knooppunt. Klik met de rechtermuisknop op de leveringstoewijzing die u wilt gebruiken (**[!UICONTROL Visitors]** als u anonieme aanbiedingen wilt gebruiken) en selecteert u **[!UICONTROL Actions]** > **[!UICONTROL Modify the options of the targeting dimension]**.

   ![](assets/offer_env_anonymous_001.png)

1. Klikken **[!UICONTROL Next]** om naar het volgende scherm in de tovenaar te werk te gaan, controleer **[!UICONTROL Generate a storage schema for propositions]** en klik op **[!UICONTROL Save]**.

   ![](assets/offer_env_anonymous_002.png)

   >[!NOTE]
   >
   >Als het selectievakje al is ingeschakeld, schakelt u het uit en controleert u het opnieuw.

1. Adobe Campaign maakt twee omgevingen (**[!UICONTROL Design]** en **[!UICONTROL Live]** ) met doelinformatie uit de eerder ingeschakelde doeltoewijzing. Het milieu wordt preconfigured met het richten informatie.

   Als u **[!UICONTROL Visitor]** de **[!UICONTROL Environment dedicated to incoming anonymous interactions]** wordt automatisch ingeschakeld in de omgeving **[!UICONTROL General]** tab.

   Met deze optie kunt u anonieme interactiespecifieke functies activeren, vooral wanneer u omgevingen configureert die spaties bieden. U kunt opties ook vormen die u toestaan om van een &quot;geïdentificeerd&quot;milieu aan een &quot;anonieme&quot;milieu over te schakelen.

   U kunt bijvoorbeeld een koppeling tot stand brengen tussen een ontvankelijke omgeving en een aanbiedingsruimte (geïdentificeerd contact) die overeenkomt met een bezoekersomgeving (niet-geïdentificeerd contact). Op deze manier worden verschillende aanbiedingen ter beschikking gesteld van de contactpersoon, afhankelijk van of deze contactpersoon al dan niet wordt geïdentificeerd. Raadpleeg voor meer informatie hierover [Aanbiedingsruimten maken](../../interaction/using/creating-offer-spaces.md).

   ![](assets/offer_env_anonymous_003.png)

>[!NOTE]
>
>Voor meer informatie over anonieme interacties op een binnenkomend kanaal, verwijs naar [Anonieme interacties](../../interaction/using/anonymous-interactions.md).
