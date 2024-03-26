---
product: campaign
title: Aanbiedingen goedkeuren en activeren
description: Aanbiedingen goedkeuren en activeren
feature: Interaction, Offers
badge-v7: label="v7" type="Informative" tooltip="Is van toepassing op Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
audience: interaction
content-type: reference
topic-tags: managing-an-offer-catalog
exl-id: cf7649fe-f62a-4dfa-a19e-9c1ca545e3e3
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '634'
ht-degree: 0%

---

# Aanbiedingen goedkeuren en activeren{#approving-and-activating-an-offer}



Zodra de inhoud van het aanbod volledig is, moet u het goedkeuren voor het worden gedupliceerd in het levende milieu en worden geleverd. Goedkeuring heeft betrekking op de inhoud van het aanbod en de geschiktheid ervan.

De banner op het aanbiedingsdashboard vertelt u of de aanbieding de goedkeuringscyclus moet of niet.

![](assets/offer_validate_001.png)

## Aanbiedingsinhoud goedkeuren {#approving-offer-content}

Als u inhoud van het aanbod goedkeurt, selecteert u de representatie(s) die u in de live omgeving beschikbaar wilt maken.

De inhoud van een aanbieding heeft één representatie per ruimte. Aangezien elke aanbiedingsruimte zijn eigen structuur en zijn eigen renderingfuncties heeft, kan de aanbiedingsvertegenwoordiging variëren.

U kunt de inhoud van het voorstel op bepaalde beschikbare ruimten goedkeuren en op andere plaatsen afwijzen.

>[!IMPORTANT]
>
>Zodra de inhoud en de geschiktheid van een aanbieding zijn goedgekeurd, wordt de publicatieworkflow (kennisgeving van aanbieding) automatisch uitgevoerd en wordt de aanbieding live en beschikbaar gesteld op alle geactiveerde ruimten.

Voer de volgende stappen uit om de inhoud van de aanbieding goed te keuren:

1. Klik op de knop **[!UICONTROL Approval]** en selecteert u **[!UICONTROL Approve content]** in popup.

   ![](assets/offer_validate_002.png)

1. Selecteer in de vervolgkeuzelijst de weergaven die u wilt blijven bewerken of de weergaven die u wilt publiceren naar de live omgeving en klik op **[!UICONTROL Content approval]**.

   ![](assets/offer_validate_003.png)

   Zodra de inhoud van het voorstel wordt goedgekeurd, wordt de informatie bijgewerkt op de lijst van het aanbiedingdashboard.

   ![](assets/offer_validate_004.png)

   >[!NOTE]
   >
   >De **[!UICONTROL Content approved]** vermelding betekent niet dat alle aanbiedingsvormen zijn toegelaten en goedgekeurd. Hiermee wordt aangegeven dat het goedkeuringsproces voor inhoud is voltooid, ongeacht of alle aanbiedingen zijn ingeschakeld/goedgekeurd of niet.

## Aanbiedingsgeschiktheid voor goedkeuring {#approving-offer-eligibility}

Goedkeuring van de aanbieding betekent aanvaarding of afwijzing van de aanbiedingsgewichten en de toelatingsregels die ook in de aanbieding zijn geconfigureerd of die zijn overgenomen van de regels die in de bovenliggende categorie zijn gemaakt.

>[!IMPORTANT]
>
>Zodra de inhoud en de geschiktheid van een aanbieding zijn goedgekeurd, wordt de publicatieworkflow (kennisgeving van aanbieding) automatisch uitgevoerd en wordt de aanbieding live en beschikbaar gesteld op alle geactiveerde ruimten.

* U kunt de volledige lijst met regels weergeven door op **[!UICONTROL Schedule and eligibility rules]**.

  ![](assets/offer_validate_005.png)

* Als u de subsidiabiliteitsregels wilt wijzigen, klikt u op **[!UICONTROL Reject]** en klik vervolgens op **[!UICONTROL Eligibility approval]**.

  ![](assets/offer_validate_007.png)

  De verschillende statussen worden bijgewerkt op het aanbiedingdashboard.

  ![](assets/offer_validate_006.png)

* Klik op **[!UICONTROL Approve eligibility]**.

  ![](assets/offer_validate_008.png)

  Goedkeuren, zo nodig een opmerking toevoegen en vervolgens klikken **[!UICONTROL Eligibility approval]**.

  ![](assets/offer_validate_009.png)

  De verschillende statussen worden bijgewerkt op het aanbiedingdashboard.

  ![](assets/offer_validate_010.png)

## Goedkeuring bijhouden {#approval-tracking}

Goedkeuring kan worden gevolgd op het dashboard van de aanbieding. Klikken **[!UICONTROL Hide/display logs]** om toegang te krijgen tot het bestand.

![](assets/offer_validate_012.png)

>[!NOTE]
>
>Tekstspatiëring is ook beschikbaar in het gedeelte **[!UICONTROL Audit]** tabblad van de aanbieding, met details over de opmerkingen van de revisoren.

## De goedkeuring opnieuw starten {#restart-the-approval}

Nadat de goedkeuring is gestart, kan deze opnieuw worden gestart. Volg deze instructies om dit te doen:

1. Klikken **[!UICONTROL Content approved]** op het aanbiedingsdashboard.
1. In de **[!UICONTROL Edit]** venster dat wordt weergegeven, selecteert u de goedkeuring die u opnieuw wilt starten en klikt u vervolgens op **[!UICONTROL Re-initialize approval to submit it again]**.
1. Bevestigen door te klikken **[!UICONTROL Ok]**.

![](assets/offer_validate_013.png)

## De aanbieding publiceren {#publishing-the-offer}

Zodra de inhoud en de geschiktheid van een aanbieding allebei zijn goedgekeurd, wordt de aanbieding gepubliceerd door een werkschema dat automatisch voor elke aanbieding loopt de goedkeuringscyclus is gebeëindigd. De **[!UICONTROL Offer notification]** de workflow wordt ook elk uur uitgevoerd om (indien nodig) de ruimten en categorieën in de aanbiedingscatalogus te synchroniseren van de ontwerpomgeving naar de live omgeving.

Het dashboard van de aanbieding die beschikbaar is in de ontwerpomgeving bevat informatie over publiceren, waaronder de naam van de matching-aanbieding in de live omgeving.

![](assets/offer_golive_001.png)

Als u het aanbod wilt weergeven dat beschikbaar is in de live omgeving, klikt u op het label van het aanbod: het live aanbod heeft een dashboard dat alle relevante informatie bevat.

![](assets/offer_golive_002.png)

## Een aanbieding uitschakelen {#disabling-an-offer}

Zodra de aanbieding wordt goedgekeurd, kunt u het onbruikbaar maken.

Ga hiertoe naar het dashboard voor een online aanbieding of een aanbieding die wacht om online te gaan, en klik op **[!UICONTROL Disable offer]**.

U kunt een categorie ook rechtstreeks uitschakelen door naar de **[!UICONTROL Eligibility]** en de **[!UICONTROL Enabled]** doos.

>[!NOTE]
>
>Wanneer een aanbieding in een ontwerpomgeving wordt verwijderd, wordt deze automatisch gedeactiveerd in de gekoppelde online omgeving. Na een bewaarperiode voor voorstellen worden de gedeactiveerde aanbiedingen uit de online omgeving verwijderd.

![](assets/offer_preview_deactivate.png)
