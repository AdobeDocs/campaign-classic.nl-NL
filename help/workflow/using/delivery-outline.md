---
title: Overzicht van levering
seo-title: Overzicht van levering
description: Overzicht van levering
seo-description: null
page-status-flag: never-activated
uuid: 2b924cc6-6b71-481e-acab-2d035bbc2852
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: a2a65f97-425b-44b2-8cf4-beea850423bc
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 67dce820b7a90163032ee72263a9dd23b521ea69

---


# Overzicht van levering{#delivery-outline}

Met het leveringsoverzicht kunt u een omtrek gebruiken in een campagneworkflow. De contouren moeten vooraf in de campagne zijn gemaakt.

Raadpleeg deze [sectie](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline)voor meer informatie over de leveringscontouren in Adobe Campaign.

Om de activiteit te vormen, moet u eenvoudig het overzicht selecteren u evenals de geplande contactdatum houdt van. U kunt het filtreren regels toevoegen door typologieën of typologieregels toe te voegen.

## Voorbeeld: Een voorstel invoegen via een leveringsoverzicht {#example--inserting-an-offer-via-a-delivery-outline}

Met de overzichtsactiviteit van de levering, die beschikbaar is in de workflows van de campagne, kunt u aanbiedingen presenteren waarnaar wordt verwezen in een leveringsoverzicht van de lopende campagne.

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

