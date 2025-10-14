---
product: campaign
title: 'Gebruiksscenario: de veldvervanging configureren'
description: 'Gebruiksscenario: de veldvervanging configureren'
badge-v8: label="Ook van toepassing op v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
feature: Seed Address
exl-id: 3f567b2d-6f98-4831-af84-7db17fd12c6e
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 4%

---

# Gebruiksscenario: de veldvervanging configureren{#use-case-configuring-the-field-substitution}



Met de functie voor willekeurige veldvervanging kunt u een waarde uit de lijst met ontvangers toewijzen aan de zaadadressen die leeg zijn wanneer de gebruiker deze waarde in een levering gebruikt (bijvoorbeeld: naam, plaats, enz.).

Deze vervanging laat u tijd besparen wanneer het creëren van de levering: in plaats van manueel het toevoegen van de gewenste waarde aan de zaadadressen, herstelt de substitutie willekeurig deze waarde in de lijst van ontvangers die door de levering worden gericht en past het op de zaadadressen toe.

## Context {#context}

In dit gebruiksgeval, zou de plaats **Mijn online bibliotheek** een korting naar zijn cliënten willen verzenden, die op hun favoriete literaire genre wordt gebaseerd.

De leveringsmanager heeft een verpersoonlijkingsgebied met favoriete genre in hun e-mail geïntegreerd. Het doel is om sommige zaadadressen te gebruiken: deze zaadadressen hebben het verpersoonlijkingsgebied in hun lijst maar geen waarde wordt bewaard daar.

Als u een willekeurige veldvervanging wilt gebruiken, moet u beschikken over:

* een levering met een of meer personalisatievelden;
* zaadadressen de waarvan **gegevensschema** volgens de verpersoonlijkingsgebieden wordt gewijzigd die in de levering worden gebruikt.

## Een levering maken {#step-1---creating-a-delivery}

De stappen voor het creëren van een levering zijn gedetailleerd in de [&#x200B; documentatie van de Campagne v8 &#x200B;](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/email.html?lang=nl-NL){target="_blank"}.

In dit voorbeeld heeft de leveringsmanager de nieuwsbrief gemaakt.

![](assets/dlv_seeds_usecase_24.png)

## Het gegevensschema van de zaadadressen bewerken {#editing-the-seed-addresses-data-schema}

De instructies over hoe te om een gegevensschema te wijzigen zijn gedetailleerd in de sectie.

In dit voorbeeld, neemt het gegevensschema van zaadadressen een waarde die van het schema van ontvangersgegevens wordt gecreeerd:

```
 <attribute label="Favorite literary genre" length="80" name="favoriteLiteraryGenre"
               type="string" userEnum="favoriteLiteraryGenre"/>
```

Deze opsomming laat de gebruiker het favoriete literaire genre van hun cliënten specificeren.

Voor deze wijziging van gegevensschema om in de zaadadressen **vorm van de Input** te kunnen bekijken, moet u het bijwerken. Verwijs naar de [&#x200B; Update de sectie van de inputvorm &#x200B;](use-case-selecting-seed-addresses-on-criteria.md#updating-the-input-form).

## Aanpassing configureren {#configuring-personalization}

1. Open een levering.

   In dit voorbeeld, heeft de levering twee verpersoonlijkingsgebieden: de eerste naam van de ontvanger **&#x200B;**&#x200B;en de favoriete literaire genre van de ontvanger **&#x200B;**.

   ![](assets/dlv_seeds_usecase_25.png)

1. Vorm uw leveringslijst en uw zaadadressen. Verwijs naar [&#x200B; identificeer doelpopulaties &#x200B;](steps-defining-the-target-population.md).

   In dit voorbeeld, selecteert de gebruiker gebruikers de waarvan **favoriete literaire genre** Sci-Fi als belangrijkste doelbevolking is.

   ![](assets/dlv_seeds_usecase_26.png)

   De gebruiker voegt zaadadressen aan de levering toe.

   ![](assets/dlv_seeds_usecase_27.png)

   >[!NOTE]
   >
   >Voor meer informatie over de **[!UICONTROL Edit the dynamic condition...]** verbinding, verwijs naar [&#x200B; geval van het Gebruik: uitgezochte zaadadressen op criteria &#x200B;](use-case-selecting-seed-addresses-on-criteria.md).

1. Klik op het tabblad **[!UICONTROL Preview]** en selecteer een beginadres om de personalisatie te testen.

   ![](assets/dlv_seeds_usecase_28.png)

   U ziet dat een van de velden voor personalisatie leeg is. Aangezien het zaadadres geen gegevens voor dit gebied heeft, kan de voorproef van de inhoud van HTML geen waarde tonen.

   De willekeurige substitutie van gebieden wordt uitgevoerd **op het tijdstip van levering**.

1. Klik op de knop **[!UICONTROL Send]**.
1. Analyseer uw levering toen **bevestig levering**.

   De zaadadressen ontvangen de levering in hun inbox.

   Veldpersonalisatie is effectief.

   ![](assets/dlv_seeds_usecase_08.png)
