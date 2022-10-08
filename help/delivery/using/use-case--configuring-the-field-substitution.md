---
product: campaign
title: "Gebruiksscenario: de veldvervanging configureren"
description: "Gebruiksscenario: de veldvervanging configureren"
feature: Seed Address
exl-id: 3f567b2d-6f98-4831-af84-7db17fd12c6e
source-git-commit: 9839dbacda475c2a586811e3c4f686b1b1baab05
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 4%

---

# Gebruiksscenario: de veldvervanging configureren{#use-case-configuring-the-field-substitution}

![](../../assets/common.svg)

Met Willekeurige veldvervanging kunt u een waarde uit de lijst met ontvangers toewijzen aan de zaadadressen die leeg zijn wanneer de gebruiker deze waarde in een levering gebruikt (voorbeeld: naam, stad, enz.).

Met deze vervanging bespaart u tijd bij het maken van de levering: in plaats van manueel het toevoegen van de gewenste waarde aan de zaadadressen, herstelt de substitutie willekeurig deze waarde in de lijst van ontvangers die door de levering wordt gericht en past het op de zaadadressen toe.

## Context {#context}

In dit geval, de plaats **Mijn onlinebibliotheek** Ik wil haar klanten een korting geven op basis van hun favoriete literaire genre.

De leveringsmanager heeft een verpersoonlijkingsgebied met favoriete genre in hun e-mail geïntegreerd. Het doel is om enkele adressen van zaden te gebruiken: deze zaadadressen hebben het verpersoonlijkingsgebied in hun lijst maar geen waarde wordt bewaard daar.

Als u een willekeurige veldvervanging wilt gebruiken, moet u beschikken over:

* een levering met één of meerdere verpersoonlijkingsgebieden,
* zaadadressen waarvan **gegevensschema** wordt gewijzigd op basis van de personalisatievelden die in de levering worden gebruikt.

## Een levering maken {#step-1---creating-a-delivery}

De stappen voor het maken van een levering worden beschreven in het dialoogvenster [Een e-maillevering maken](creating-an-email-delivery.md) sectie.

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

Voor deze wijziging van het gegevensschema om in de zaadadressen te bekijken **Invoerformulier**, moet u deze bijwerken. Zie de [Het invoerformulier bijwerken](use-case--selecting-seed-addresses-on-criteria.md#updating-the-input-form) sectie.

## Aanpassing configureren {#configuring-personalization}

1. Open een levering.

   In dit voorbeeld heeft de levering twee verpersoonlijkingsgebieden: de begunstigde **voornaam** en de **favoriete literatuurgenre**.

   ![](assets/dlv_seeds_usecase_25.png)

1. Vorm uw leveringslijst en uw zaadadressen. Zie [Doelpopulaties identificeren](steps-defining-the-target-population.md).

   In dit voorbeeld selecteert de gebruiker de gebruikers van wie de **favoriete literatuurgenre** is Sci-Fi als belangrijkste doelpopulatie.

   ![](assets/dlv_seeds_usecase_26.png)

   De gebruiker voegt zaadadressen aan de levering toe.

   ![](assets/dlv_seeds_usecase_27.png)

   >[!NOTE]
   >
   >Voor meer informatie over de **[!UICONTROL Edit the dynamic condition...]** koppeling, verwijzen naar [Hoofdlettergebruik: zaadadressen selecteren op criteria](use-case--selecting-seed-addresses-on-criteria.md).

1. Klik op de knop **[!UICONTROL Preview]** selecteert u vervolgens een zaadadres om de personalisatie te testen.

   ![](assets/dlv_seeds_usecase_28.png)

   U ziet dat een van de velden voor personalisatie leeg is. Aangezien het zaadadres geen gegevens voor dit gebied heeft, kan de voorproef van de inhoud van de HTML geen waarde tonen.

   De velden worden willekeurig vervangen **op het tijdstip van levering**.

1. Klik op de knop **[!UICONTROL Send]**.
1. Uw levering vervolgens analyseren **bevestig levering**.

   De zaadadressen ontvangen de levering in hun inbox.

   Veldpersonalisatie is effectief.

   ![](assets/dlv_seeds_usecase_08.png)
