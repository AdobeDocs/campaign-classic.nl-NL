---
product: campaign
title: Overzicht van levering
description: Meer informatie over de workflowactiviteit van het overzicht van de levering
feature: Workflows, Targeting Activity
hide: true
hidefromtoc: true
exl-id: b4dee085-ccc4-43fd-850d-1501a99272aa
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 1%

---

# Overzicht van levering{#delivery-outline}



Het **leveringsoverzicht** laat u een overzicht in een campagnewerkschema gebruiken. De contouren moeten vooraf in de campagne zijn gemaakt.

Voor meer informatie over leveringsoverzichten in Adobe Campaign, verwijs naar deze [ sectie ](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline).

Om de activiteit te vormen, moet u eenvoudig het overzicht selecteren u evenals de geplande contactdatum houdt van. U kunt het filtreren regels toevoegen door typologieën of typologieregels toe te voegen.

## Voorbeeld: Een aanbieding invoegen via een leveringsoverzicht {#example--inserting-an-offer-via-a-delivery-outline}

De **leveringsoverzicht** activiteit, beschikbaar in de campagnewerkschema&#39;s, laat u aanbiedingen voorstellen voorstellen die in een leveringsoverzicht van de huidige lopende campagne van verwijzingen worden voorzien.

>[!NOTE]
>
>Het **pakket van de Interactie** moet worden geïnstalleerd.

1. Voeg in een workflow een overzichtsactiviteit toe voordat u een leveringsactiviteit toevoegt.
1. Geef in de overzichtsactiviteit van de levering de omtrek op die u wilt gebruiken.

   Voor meer informatie bij het specificeren van leveringsoverzichten, verwijs naar deze [ sectie ](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline).

1. Vul de beschikbare velden in op basis van uw levering.
1. Er zijn twee mogelijke gevallen:

   * Schakel het selectievakje **[!UICONTROL Restrict the number of propositions selected]** in als u de aanbiedingsengine wilt aanroepen. Geef de aanbiedingsruimte en het aantal voorstellen op dat in de levering wordt weergegeven.

     De aanbiedingsmotor zal rekening houden met het gewicht van de aanbieding en de subsidiabiliteitsregels.

   * Als u niet de doos controleert, zullen alle aanbiedingen in het leveringsoverzicht worden voorgesteld zonder een vraag aan de aanbiedingsmotor te maken.

   In de voorvertoning wordt rekening gehouden met het aantal aanbiedingen dat in de levering is opgegeven. Bij het uitvoeren van een workflow wordt rekening gehouden met het nummer dat is opgegeven in het leveringsoverzicht.

   ![](assets/int_compo_offre_wf1.png)
