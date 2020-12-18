---
solution: Campaign Classic
product: campaign
title: Live/Design-omgevingen
description: Live/Design-omgevingen
audience: interaction
content-type: reference
topic-tags: managing-environments
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 2%

---


# Live/Design-omgevingen{#live-design-environments}

## Werkwijze {#operating-principle}

De interactie werkt met twee soorten aanbiedingsmilieu&#39;s:

* **[!UICONTROL Design]** bieden omgevingen aan die aanbiedingen bevatten die worden bewerkt en kunnen worden gewijzigd. Deze aanbiedingen zijn niet door de goedkeuringscyclus geweest en niet geleverd aan contacten.
* **[!UICONTROL Live]** bieden omgevingen aan die goedgekeurde aanbiedingen bevatten terwijl deze aan contactpersonen worden aangeboden. De aanbiedingen in deze omgeving zijn alleen-lezen.

![](assets/offer_environments_overview_001.png)

Elke **[!UICONTROL Design]**-omgeving is gekoppeld aan een **[!UICONTROL Live]**-omgeving. Wanneer een aanbieding is voltooid, worden de inhoud en de subsidiabiliteitsregels ervan onderworpen aan een goedkeuringscyclus. Zodra deze cyclus volledig is, wordt de betrokken aanbieding automatisch opgesteld aan het **[!UICONTROL Live]** milieu. Vanaf dat moment is het beschikbaar voor levering.

Door gebrek, komt de Interactie met een **[!UICONTROL Design]** milieu en een **[!UICONTROL Live]** milieu verbonden aan het. Beide milieu&#39;s worden pre-gevormd om de uit-van-de-doos ontvankelijke lijst te richten.

>[!NOTE]
>
>Als u een andere tabel als doel wilt instellen (bezoekerstabel voor anonieme aanbiedingen of een specifieke tabel voor ontvangers), moet u de wizard voor doeltoewijzing gebruiken om de omgevingen te maken. Voor meer op dit, verwijs naar [Creërend een aanbiedingsmilieu](#creating-an-offer-environment).

![](assets/offer_environments_overview_002.png)

De managers van de aanbieding en de leveringsmanagers hebben toegang tot verschillende meningen van het milieu. Leveringsmanagers kunnen de **[!UICONTROL Live]** aanbiedingsomgeving en gebruiksaanbiedingen alleen bekijken om deze te leveren. De managers van de aanbieding kunnen het **[!UICONTROL Design]** milieu bekijken en veranderen en het **[!UICONTROL Live]** milieu bekijken. Raadpleeg [Operator-profielen](../../interaction/using/operator-profiles.md) voor meer informatie.

## Aanbiedingsomgeving {#creating-an-offer-environment} maken

Door gebrek, komt de Interactie met een vooraf gevormd milieu om de ontvankelijke lijst (geïdentificeerde aanbiedingen) te richten. Als u een andere tabel (bezoekerstabel voor anonieme aanbiedingen of een specifieke tabel voor ontvangers) als doel wilt instellen, moet u de volgende configuraties toepassen:

1. Plaats de cursor op het knooppunt **[!UICONTROL Administration]** > **[!UICONTROL Campaign management]** > **[!UICONTROL Delivery mappings]**. Klik met de rechtermuisknop op de leveringstoewijzing die u wilt gebruiken (**[!UICONTROL Visitors]** als u anonieme aanbiedingen wilt gebruiken) en selecteer **[!UICONTROL Actions]** > **[!UICONTROL Modify the options of the targeting dimension]**.

   ![](assets/offer_env_anonymous_001.png)

1. Klik **[!UICONTROL Next]** om aan het volgende scherm in de tovenaar te werk te gaan, **[!UICONTROL Generate a storage schema for propositions]** doos te controleren en **[!UICONTROL Save]** te klikken.

   ![](assets/offer_env_anonymous_002.png)

   >[!NOTE]
   >
   >Als het selectievakje al is ingeschakeld, schakelt u het uit en controleert u het opnieuw.

1. Adobe Campaign maakt twee omgevingen (**[!UICONTROL Design]** en **[!UICONTROL Live]**) met doelinformatie uit de eerder ingeschakelde doeltoewijzing. Het milieu wordt preconfigured met het richten informatie.

   Als u **[!UICONTROL Visitor]**-toewijzing hebt geactiveerd, wordt de **[!UICONTROL Environment dedicated to incoming anonymous interactions]**-doos automatisch ingeschakeld op de tab **[!UICONTROL General]** van de omgeving.

   Met deze optie kunt u anonieme interactiespecifieke functies activeren, vooral wanneer u omgevingen configureert die spaties bieden. U kunt opties ook vormen die u toestaan om van een &quot;geïdentificeerd&quot;milieu aan een &quot;anonieme&quot;milieu over te schakelen.

   U kunt bijvoorbeeld een koppeling tot stand brengen tussen een ontvankelijke omgeving en een aanbiedingsruimte (geïdentificeerd contact) die overeenkomt met een bezoekersomgeving (niet-geïdentificeerd contact). Op deze manier zullen verschillende aanbiedingen aan de contactpersoon beschikbaar worden gesteld, afhankelijk van of s/he al dan niet wordt geïdentificeerd. Raadpleeg [Aanbiedingsruimten maken](../../interaction/using/creating-offer-spaces.md) voor meer informatie.

   ![](assets/offer_env_anonymous_003.png)

>[!NOTE]
>
>Voor meer informatie over anonieme interacties op een binnenkomend kanaal, verwijs naar [Anonieme interacties](../../interaction/using/anonymous-interactions.md).

