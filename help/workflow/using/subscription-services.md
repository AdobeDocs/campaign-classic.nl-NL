---
title: Abonnementsservices
seo-title: Abonnementsservices
description: Abonnementsservices
seo-description: null
page-status-flag: never-activated
uuid: f8c05f8a-0791-4294-8aa3-69b7325e4d43
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: 940bec7e-e3f0-4251-b7fe-72bf188743a7
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# Abonnementsservices{#subscription-services}

Met een activiteit van het type **Subscription Services** kunt u een abonnement op een informatieservice maken of verwijderen voor de bevolking die in de overgang is opgegeven.

Om het te vormen, geef de activiteit uit en ga zijn etiket in, dan selecteer de uit te voeren actie (Abonnement of Unsubscription) en de dienst in kwestie, zoals in het volgende voorbeeld:

![](assets/edit_service_inscription.png)

1. Voer het label van de activiteit in.
1. Selecteer **[!UICONTROL Generate an outbound transition]** als u een overgang wilt maken aan het einde van de uitvoering.

   Over het algemeen markeert een abonnement van een doel op een informatiedienst het einde van de doelworkflow. Daarom wordt de optie niet standaard geactiveerd.

1. Klik **[!UICONTROL Subscription]** of **[!UICONTROL Unsubscription]** als u een abonnement wilt nemen op of een abonnement wilt nemen op de opgegeven populatie van of naar de geselecteerde informatiedienst.
1. Selecteer **[!UICONTROL Send a confirmation message]** om ontvangers op de hoogte te stellen van het feit dat ze zijn geabonneerd op of geen abonnement hebben op een service.

   De inhoud van dit bericht wordt gespecificeerd in een leveringsmalplaatje met betrekking tot de informatiedienst. Zie deze [sectie](../../delivery/using/managing-subscriptions.md)voor meer informatie.

## Voorbeeld: Een lijst met ontvangers abonneren op een nieuwsbrief {#example--subscribe-a-list-of-recipients-to-a-newsletter}

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
1. Voer het activiteitenlabel in en selecteer **[!UICONTROL Subscription]**.

   U kunt ontvangers desgewenst informeren over hun abonnement op de nieuwsbrief door het **[!UICONTROL Send a confirmation message]** selectievakje in te schakelen.

1. Selecteer de map waarin de nieuwsbrief zich bevindt en selecteer vervolgens de nieuwsbrief in de lijst die wordt weergegeven.
1. Laat het **[!UICONTROL Generate outbound transition]** selectievakje uitgeschakeld zodat deze activiteit het einde van de workflow markeert en klik op **[!UICONTROL Ok]**.

Tijdens werkschemauitvoering, worden de ontvangers die aan alle drie vragen beantwoorden toegevoegd aan de lijst en aan nieuwsbrief geabonneerd.

U kunt controleren of het abonnement is gelukt door naar het **[!UICONTROL Subscription]** tabblad voor de ontvangers te gaan.

## Invoerparameters {#input-parameters}

* tableName
* schema

Elke binnenkomende gebeurtenis moet een doel specificeren dat door deze parameters wordt bepaald.
