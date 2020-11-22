---
solution: Campaign Classic
product: campaign
title: Overzicht van levering
description: Meer informatie over de workflowactiviteit van het overzicht van de levering
audience: workflow
content-type: reference
topic-tags: targeting-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 1%

---


# Overzicht van levering{#delivery-outline}

Met het **leveringsoverzicht** kunt u een omtrek gebruiken in een campagneworkflow. De contouren moeten vooraf in de campagne zijn gemaakt.

Zie deze [sectie](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline)voor meer informatie over de leveringscontouren in Adobe Campaign.

Om de activiteit te vormen, moet u eenvoudig het overzicht selecteren u evenals de geplande contactdatum houdt van. U kunt het filtreren regels toevoegen door typologieën of typologieregels toe te voegen.

## Voorbeeld: Een voorstel invoegen via een leveringsoverzicht {#example--inserting-an-offer-via-a-delivery-outline}

De activiteit van het **leveringsoverzicht** , beschikbaar in de campagnewerkschema&#39;s, laat u aanbiedingen voorstellen voorstellen die in een leveringsoverzicht van de huidige lopende campagne van verwijzingen worden voorzien.

>[!NOTE]
>
>Het **interactiepakket** moet zijn geïnstalleerd.

1. Voeg in een workflow een overzichtsactiviteit toe voordat u een leveringsactiviteit toevoegt.
1. Geef in de overzichtsactiviteit van de levering de omtrek op die u wilt gebruiken.

   Raadpleeg deze [sectie](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline)voor meer informatie over het opgeven van leveringscontouren.

1. Vul de beschikbare velden in op basis van uw levering.
1. Er zijn twee mogelijke gevallen:

   * Schakel het **[!UICONTROL Restrict the number of propositions selected]** selectievakje in als je de aanbiedingsengine wilt bellen. Geef de aanbiedingsruimte en het aantal voorstellen op dat in de levering wordt weergegeven.

      De aanbiedingsmotor zal rekening houden met het gewicht van de aanbieding en de subsidiabiliteitsregels.

   * Als u niet de doos controleert, zullen alle aanbiedingen in het leveringsoverzicht worden voorgesteld zonder een vraag aan de aanbiedingsmotor te maken.

   In de voorvertoning wordt rekening gehouden met het aantal aanbiedingen dat in de levering is opgegeven. Bij het uitvoeren van een workflow wordt rekening gehouden met het nummer dat is opgegeven in het leveringsoverzicht.

   ![](assets/int_compo_offre_wf1.png)

