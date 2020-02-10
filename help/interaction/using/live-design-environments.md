---
title: Live/Design-omgevingen
seo-title: Live/Design-omgevingen
description: Live/Design-omgevingen
seo-description: null
page-status-flag: never-activated
uuid: 38ee2f6a-e446-4ac6-b962-40b648eeaf66
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: managing-environments
discoiquuid: 3cea2be4-4da4-4ebd-a241-1bbaa5abb16e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Live/Design-omgevingen{#live-design-environments}

## Exploitatiebeginsel {#operating-principle}

De interactie werkt met twee soorten aanbiedingsmilieu&#39;s:

* **[!UICONTROL Design]** bieden omgevingen aan die aanbiedingen bevatten die worden bewerkt en kunnen worden gewijzigd. Deze aanbiedingen zijn niet door de goedkeuringscyclus geweest en niet geleverd aan contacten.
* **[!UICONTROL Live]** bieden omgevingen aan die goedgekeurde aanbiedingen bevatten terwijl deze aan contactpersonen worden aangeboden. De aanbiedingen in deze omgeving zijn alleen-lezen.

![](assets/offer_environments_overview_001.png)

Elke **[!UICONTROL Design]** omgeving is gekoppeld aan een **[!UICONTROL Live]** omgeving. Wanneer een aanbieding is voltooid, worden de inhoud en de subsidiabiliteitsregels ervan onderworpen aan een goedkeuringscyclus. Zodra deze cyclus is voltooid, wordt het desbetreffende aanbod automatisch in de **[!UICONTROL Live]** omgeving geïmplementeerd. Vanaf dat moment is het beschikbaar voor levering.

Interactie wordt standaard geleverd met een **[!UICONTROL Design]** omgeving en een **[!UICONTROL Live]** omgeving die eraan gekoppeld zijn. Beide milieu&#39;s worden pre-gevormd om de uit-van-de-doos ontvankelijke lijst te richten.

>[!NOTE]
>
>Als u een andere tabel als doel wilt instellen (bezoekerstabel voor anonieme aanbiedingen of een specifieke tabel voor ontvangers), moet u de wizard voor doeltoewijzing gebruiken om de omgevingen te maken. Raadpleeg [Een aanbiedingsomgeving](#creating-an-offer-environment)maken voor meer informatie hierover.

![](assets/offer_environments_overview_002.png)

De managers van de aanbieding en de leveringsmanagers hebben toegang tot verschillende meningen van het milieu. Leveringsmanagers kunnen de **[!UICONTROL Live]** aanbiedingsomgeving en de gebruiksaanbiedingen alleen bekijken om deze te leveren. De managers van de aanbieding kunnen het **[!UICONTROL Design]** milieu bekijken en veranderen en het **[!UICONTROL Live]** milieu bekijken. Raadpleeg de profielen [van](../../interaction/using/operator-profiles.md)operatoren voor meer informatie.

## Een aanbiedingsomgeving maken {#creating-an-offer-environment}

Door gebrek, komt de Interactie met een vooraf gevormd milieu om de ontvankelijke lijst (geïdentificeerde aanbiedingen) te richten. Als u een andere tabel (bezoekerstabel voor anonieme aanbiedingen of een specifieke tabel voor ontvangers) als doel wilt instellen, moet u de volgende configuraties toepassen:

1. Plaats de cursor op het knooppunt **[!UICONTROL Administration]** > **[!UICONTROL Campaign management]** > **[!UICONTROL Delivery mappings]** . Klik met de rechtermuisknop op de leveringstoewijzing die u wilt gebruiken (**[!UICONTROL Visitors]** als u anonieme aanbiedingen wilt gebruiken) en selecteer **[!UICONTROL Actions]** > **[!UICONTROL Modify the options of the targeting dimension]**.

   ![](assets/offer_env_anonymous_001.png)

1. Klik **[!UICONTROL Next]** om door te gaan naar het volgende scherm in de tovenaar, controleer het **[!UICONTROL Generate a storage schema for propositions]** vakje en klik **[!UICONTROL Save]**.

   ![](assets/offer_env_anonymous_002.png)

   >[!NOTE]
   >
   >Als het selectievakje al is ingeschakeld, schakelt u het uit en controleert u het opnieuw.

1. Adobe Campagne leidt tot twee milieu&#39;s (**[!UICONTROL Design]** en **[!UICONTROL Live]** ) met richtingsinformatie van eerder toegelaten doelafbeelding. Het milieu wordt preconfigured met het richten informatie.

   Als u **[!UICONTROL Visitor]** toewijzing hebt geactiveerd, wordt het **[!UICONTROL Environment dedicated to incoming anonymous interactions]** vakje automatisch gecontroleerd in het **[!UICONTROL General]** lusje van het milieu.

   Met deze optie kunt u anonieme interactiespecifieke functies activeren, vooral wanneer u omgevingen configureert die spaties bieden. U kunt opties ook vormen die u toestaan om van een &quot;geïdentificeerd&quot;milieu aan een &quot;anonieme&quot;milieu over te schakelen.

   U kunt bijvoorbeeld een koppeling tot stand brengen tussen een ontvankelijke omgeving en een aanbiedingsruimte (geïdentificeerd contact) die overeenkomt met een bezoekersomgeving (niet-geïdentificeerd contact). Op deze manier zullen verschillende aanbiedingen aan de contactpersoon beschikbaar worden gesteld, afhankelijk van of s/he al dan niet wordt geïdentificeerd. Raadpleeg [Aanbiedingsruimten](../../interaction/using/creating-offer-spaces.md)maken voor meer informatie hierover.

   ![](assets/offer_env_anonymous_003.png)

>[!NOTE]
>
>Raadpleeg [Anonieme interacties](../../interaction/using/anonymous-interactions.md)voor meer informatie over anonieme interacties op een binnenkomend kanaal.

