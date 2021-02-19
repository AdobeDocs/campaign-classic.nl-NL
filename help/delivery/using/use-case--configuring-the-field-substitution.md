---
solution: Campaign Classic
product: campaign
title: '"Gebruiksscenario: de veldvervanging configureren"'
description: '"Gebruiksscenario: de veldvervanging configureren"'
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 4%

---


# Gebruiksscenario: de veldvervanging configureren{#use-case-configuring-the-field-substitution}

Met Willekeurige veldvervanging kunt u een waarde uit de lijst met ontvangers toewijzen aan de zaadadressen die leeg zijn wanneer de gebruiker deze waarde in een levering gebruikt (voorbeeld: naam, stad, enz.).

Met deze vervanging bespaart u tijd bij het maken van de levering: in plaats van manueel het toevoegen van de gewenste waarde aan de zaadadressen, herstelt de substitutie willekeurig deze waarde in de lijst van ontvangers die door de levering wordt gericht en past het op de zaadadressen toe.

## Context {#context}

In dit geval wil de site **Mijn onlinebibliotheek** een korting op hun favoriete literaire genre naar de klant sturen.

De leveringsmanager heeft een verpersoonlijkingsgebied met favoriete genre in zijn e-mail geïntegreerd. Hij zou graag wat zaadadressen gebruiken. Deze zaadadressen hebben het verpersoonlijkingsgebied in hun lijst maar geen waarde wordt daar bewaard.

Als u een willekeurige veldvervanging wilt gebruiken, moet u beschikken over:

* een levering met één of meerdere verpersoonlijkingsgebieden,
* zaadadressen de waarvan **gegevensschema** volgens de verpersoonlijkingsgebieden wordt gewijzigd die in de levering worden gebruikt.

## Een levering {#step-1---creating-a-delivery} maken

De stappen voor het maken van een levering worden beschreven in de sectie [Een e-maillevering maken](../../delivery/using/creating-an-email-delivery.md).

In dit voorbeeld heeft de leveringsmanager de nieuwsbrief gemaakt.

![](assets/dlv_seeds_usecase_24.png)

## Het zaadadresgegevensschema {#editing-the-seed-addresses-data-schema} bewerken

De instructies over hoe te om een gegevensschema te wijzigen zijn gedetailleerd in de sectie.

In dit voorbeeld, neemt het gegevensschema van zaadadressen een waarde die van het schema van ontvangersgegevens wordt gecreeerd:

```
 <attribute label="Favorite literary genre" length="80" name="favoriteLiteraryGenre"
               type="string" userEnum="favoriteLiteraryGenre"/>
```

Deze opsomming laat de gebruiker het favoriete literaire genre van hun cliënten specificeren.

Als u wilt dat deze wijziging van het gegevensschema kan worden weergegeven in de beginadressen **Invoerformulier**, moet u het bijwerken. Raadpleeg de sectie [Invoerformulier bijwerken](../../delivery/using/use-case--selecting-seed-addresses-on-criteria.md#updating-the-input-form).

## Aanpassing configureren {#configuring-personalization}

1. Open een levering.

   In dit voorbeeld heeft de levering twee verpersoonlijkingsgebieden: de **voornaam** van de ontvanger en **favoriete literaire genre** van de ontvanger.

   ![](assets/dlv_seeds_usecase_25.png)

1. Vorm uw leveringslijst en uw zaadadressen. Zie [Doelpopulaties identificeren](../../delivery/using/steps-defining-the-target-population.md).

   In dit voorbeeld selecteert de gebruiker gebruikers van wie **Favoriete literaire genre** Sci-Fi als belangrijkste doelpopulatie is.

   ![](assets/dlv_seeds_usecase_26.png)

   De gebruiker voegt zaadadressen aan de levering toe.

   ![](assets/dlv_seeds_usecase_27.png)

   >[!NOTE]
   >
   >Raadpleeg [Hoofdlettergebruik voor meer informatie over de **[!UICONTROL Edit the dynamic condition...]**-koppeling: het selecteren van zaadadressen op criteria](../../delivery/using/use-case--selecting-seed-addresses-on-criteria.md).

1. Klik op het tabblad **[!UICONTROL Preview]** en selecteer vervolgens een beginadres om de personalisatie te testen.

   ![](assets/dlv_seeds_usecase_28.png)

   U ziet dat een van de velden voor personalisatie leeg is. Aangezien het zaadadres geen gegevens voor dit gebied heeft, kan de voorproef van de HTML- inhoud geen waarde tonen.

   Willekeurige vervanging van velden wordt uitgevoerd **op het tijdstip van levering**.

1. Klik op de knop **[!UICONTROL Send]**.
1. Analyseer uw levering dan **bevestig levering**.

   De zaadadressen ontvangen de levering in hun inbox.

   Veldpersonalisatie is effectief.

   ![](assets/dlv_seeds_usecase_08.png)
