---
solution: Campaign Classic
product: campaign
title: Abonnementsservices
description: Meer informatie over de workflowactiviteiten van Subscription Services
audience: workflow
content-type: reference
topic-tags: targeting-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 2%

---


# Abonnementsservices{#subscription-services}

Met een activiteit van het type **Subscription Services** kunt u een abonnement op een informatieservice maken of verwijderen voor de bevolking die in de overgang is opgegeven.

Om het te vormen, geef de activiteit uit en ga zijn etiket in, dan selecteer de uit te voeren actie (Abonnement of Unsubscription) en de dienst in kwestie, zoals in het volgende voorbeeld:

![](assets/edit_service_inscription.png)

1. Voer het label van de activiteit in.
1. Selecteer **[!UICONTROL Generate an outbound transition]** als u een overgang aan het eind van de uitvoering wilt tot stand brengen.

   Over het algemeen markeert een abonnement van een doel op een informatiedienst het einde van de doelworkflow. Daarom wordt de optie niet standaard geactiveerd.

1. Klik op **[!UICONTROL Subscription]** of **[!UICONTROL Unsubscription]** als u een abonnement wilt nemen op de opgegeven populatie of dit wilt opzeggen voor de geselecteerde informatieservice.
1. Selecteer **[!UICONTROL Send a confirmation message]** om ontvangers op de hoogte te stellen van het feit dat zij zijn geabonneerd op of zich niet hebben geabonneerd op een service.

   De inhoud van dit bericht wordt gespecificeerd in een leveringsmalplaatje met betrekking tot de informatiedienst. Raadpleeg deze [sectie](../../delivery/using/managing-subscriptions.md) voor meer informatie.

## Voorbeeld: Abonneren op een lijst met ontvangers voor een nieuwsbrief {#example--subscribe-a-list-of-recipients-to-a-newsletter}

In één enkele operatie is de volgende workflow bedoeld om een lijst op te stellen van ontvangers die in aanmerking komen voor een nieuwsbrief, gericht op werkende mensen die in Parijs wonen, om hen te laten inschrijven.

Hiervoor moet u ook ontvangers uitsluiten die al zijn geabonneerd.

>[!CAUTION]
>
>Alvorens manueel ontvangers aan de dienst in te tekenen, verifieer dat deze ontvangers goedkeuren om mededelingen van u te ontvangen.

![](assets/subscription_services_example.png)

1. Voeg de volgende drie vragen toe:

   * Eén gericht op ontvangers in de leeftijd van 18 tot 60 jaar.
   * Een tweede gericht op ontvangers die in Parijs wonen.
   * Een derde gericht op ontvangers die momenteel niet aan de nieuwsbrief worden geabonneerd.

1. Voeg een doorsnedeactiviteit toe om de verschillende resultaten te verwijzen.
1. Voeg desgewenst een lijst bij om de lijst met de meest recente abonnees up-to-date te houden.
1. Voeg een activiteit van de abonnementsdiensten in, dan klik dit tweemaal om het te vormen.
1. Voer het activiteitlabel in en selecteer **[!UICONTROL Subscription]**.

   Als u wilt, kunt u ontvangers op de hoogte stellen van hun abonnement op nieuwsbrief door het vakje **[!UICONTROL Send a confirmation message]** in te schakelen.

1. Selecteer de map waarin de nieuwsbrief zich bevindt en selecteer vervolgens de nieuwsbrief in de lijst die wordt weergegeven.
1. Laat **[!UICONTROL Generate outbound transition]** uitgeschakeld zodat deze activiteit het einde van de workflow markeert en klik vervolgens op **[!UICONTROL Ok]**.

Tijdens werkschemauitvoering, worden de ontvangers die aan alle drie vragen beantwoorden toegevoegd aan de lijst en aan nieuwsbrief geabonneerd.

U kunt controleren of het abonnement is gelukt door naar het tabblad **[!UICONTROL Subscription]** voor uw ontvangers te gaan.

## Invoerparameters {#input-parameters}

* tableName
* schema

Elke binnenkomende gebeurtenis moet een doel specificeren dat door deze parameters wordt bepaald.
