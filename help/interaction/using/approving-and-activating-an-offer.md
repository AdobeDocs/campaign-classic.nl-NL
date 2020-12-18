---
solution: Campaign Classic
product: campaign
title: Een aanbieding goedkeuren en activeren
description: Een aanbieding goedkeuren en activeren
audience: interaction
content-type: reference
topic-tags: managing-an-offer-catalog
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '622'
ht-degree: 2%

---


# Een aanbieding goedkeuren en activeren{#approving-and-activating-an-offer}

Zodra de inhoud van het aanbod volledig is, moet u het goedkeuren voor het worden gedupliceerd in het levende milieu en worden geleverd. Goedkeuring heeft betrekking op de inhoud van het aanbod en de geschiktheid ervan.

De banner op het aanbiedingsdashboard vertelt u of de aanbieding de goedkeuringscyclus moet of niet.

![](assets/offer_validate_001.png)

## Aanbiedingsinhoud {#approving-offer-content} goedkeuren

Als u de inhoud van het aanbod goedkeurt, selecteert u de representatie(s) die u in de live omgeving beschikbaar wilt maken.

De inhoud van een aanbieding heeft één representatie per ruimte. Aangezien elke aanbiedingsruimte zijn eigen structuur en zijn eigen renderingfuncties heeft, kan de aanbiedingsvertegenwoordiging variëren.

U kunt de inhoud van het voorstel op bepaalde beschikbare ruimten goedkeuren en op andere plaatsen afwijzen.

>[!IMPORTANT]
>
>Zodra de inhoud en de geschiktheid van een aanbieding zijn goedgekeurd, wordt de publicatieworkflow (kennisgeving van aanbieding) automatisch uitgevoerd en wordt de aanbieding live en beschikbaar gesteld op alle geactiveerde ruimten.

Voer de volgende stappen uit om de inhoud van de aanbieding goed te keuren:

1. Klik op de knop **[!UICONTROL Approval]** en selecteer **[!UICONTROL Approve content]** in popup.

   ![](assets/offer_validate_002.png)

1. Selecteer met de vervolgkeuzelijst de representaties die u wilt blijven bewerken of de weergaven die u wilt publiceren naar de live omgeving en klik op **[!UICONTROL Content approval]**.

   ![](assets/offer_validate_003.png)

   Zodra de inhoud van het voorstel wordt goedgekeurd, wordt de informatie bijgewerkt op de lijst van het aanbiedingdashboard.

   ![](assets/offer_validate_004.png)

   >[!NOTE]
   >
   >De **[!UICONTROL Content approved]**-vermelding betekent niet dat alle aanbiedingsrepresentaties zijn ingeschakeld en goedgekeurd. Hiermee wordt aangegeven dat het goedkeuringsproces voor inhoud is voltooid, ongeacht of alle aanbiedingen zijn ingeschakeld/goedgekeurd of niet.

## Aanbiedingsgeschiktheid {#approving-offer-eligibility} goedkeuren

Goedkeuring van de aanbieding betekent aanvaarding of afwijzing van de aanbiedingsgewichten en de toelatingsregels die ook in de aanbieding zijn geconfigureerd of die zijn overgenomen van de regels die in de bovenliggende categorie zijn gemaakt.

>[!IMPORTANT]
>
>Zodra de inhoud en de geschiktheid van een aanbieding zijn goedgekeurd, wordt de publicatieworkflow (kennisgeving van aanbieding) automatisch uitgevoerd en wordt de aanbieding live en beschikbaar gesteld op alle geactiveerde ruimten.

* U kunt de volledige lijst met regels weergeven door op **[!UICONTROL Schedule and eligibility rules]** te klikken.

   ![](assets/offer_validate_005.png)

* Als u de toelatingsregels wilt wijzigen, klikt u op **[!UICONTROL Reject]** en vervolgens op **[!UICONTROL Eligibility approval]**.

   ![](assets/offer_validate_007.png)

   De verschillende statussen worden bijgewerkt op het aanboddddashboard.

   ![](assets/offer_validate_006.png)

* Klik op **[!UICONTROL Approve eligibility]** om de geschiktheid voor de aanbieding te accepteren.

   ![](assets/offer_validate_008.png)

   Goedkeuren, zo nodig een opmerking toevoegen en vervolgens op **[!UICONTROL Eligibility approval]** klikken.

   ![](assets/offer_validate_009.png)

   De verschillende statussen worden bijgewerkt op het aanboddddashboard.

   ![](assets/offer_validate_010.png)

## Goedkeuring {#approval-tracking}

Goedkeuring kan worden gevolgd op het dashboard van de aanbieding. Klik **[!UICONTROL Hide/display logs]** om tot het toegang te hebben.

![](assets/offer_validate_012.png)

>[!NOTE]
>
>Tracking is ook beschikbaar op het tabblad **[!UICONTROL Audit]** van de aanbieding, met details over de opmerkingen van de revisoren.

## Goedkeuring {#restart-the-approval} opnieuw starten

Nadat de goedkeuring is gestart, kan deze opnieuw worden gestart. Volg deze instructies om dit te doen:

1. Klik **[!UICONTROL Content approved]** op het aanbiedingdashboard.
1. Selecteer in het venster **[!UICONTROL Edit]** dat wordt weergegeven de goedkeuring die u opnieuw wilt starten en klik op **[!UICONTROL Re-initialize approval to submit it again]**.
1. Bevestig door op **[!UICONTROL Ok]** te klikken.

![](assets/offer_validate_013.png)

## De aanbieding {#publishing-the-offer} publiceren

Zodra de inhoud en de geschiktheid van een aanbieding allebei zijn goedgekeurd, wordt de aanbieding gepubliceerd door een werkschema dat automatisch voor elke aanbieding loopt de goedkeuringscyclus is gebeëindigd. De **[!UICONTROL Offer notification]** workflow wordt ook elke uur uitgevoerd om (indien nodig) de ruimten en categorieën in de aanbiedingscatalogus te synchroniseren van de ontwerpomgeving naar de live omgeving.

Het dashboard van de aanbieding die beschikbaar is in de ontwerpomgeving bevat informatie over publiceren, waaronder de naam van de matching-aanbieding in de live omgeving.

![](assets/offer_golive_001.png)

Klik op het aanbiedingslabel om het aanbod weer te geven dat beschikbaar is in de live omgeving: de live aanbieding heeft een dashboard dat alle relevante informatie bevat .

![](assets/offer_golive_002.png)

## Een aanbieding {#disabling-an-offer} uitschakelen

Zodra de aanbieding wordt goedgekeurd, kunt u het onbruikbaar maken.

Ga hiertoe naar het dashboard voor een online aanbieding of een aanbieding die wacht om online te gaan, en klik vervolgens op **[!UICONTROL Disable offer]**.

U kunt een categorie ook rechtstreeks uitschakelen door naar het tabblad **[!UICONTROL Eligibility]** te gaan en het vak **[!UICONTROL Enabled]** te selecteren.

>[!NOTE]
>
>Wanneer een aanbieding in een ontwerpomgeving wordt verwijderd, wordt deze automatisch gedeactiveerd in de gekoppelde online omgeving. Na een bewaarperiode voor voorstellen worden de gedeactiveerde aanbiedingen uit de online omgeving verwijderd.

![](assets/offer_preview_deactivate.png)

