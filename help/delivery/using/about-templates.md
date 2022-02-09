---
product: campaign
title: Sjablonen
description: Aan de slag met leveringssjablonen
feature: Delivery Templates
exl-id: d943898c-06fe-451d-aa28-8a95665f4112
source-git-commit: f05eefc9945c4ead89eb448b6e28c3523559e055
workflow-type: tm+mt
source-wordcount: '276'
ht-degree: 1%

---

# Sjablonen{#about-templates}

![](../../assets/common.svg)

Een leveringsconfiguratie kan in een leveringsmalplaatje worden bewaard om opnieuw te worden gebruikt. De sjabloon kan een volledige of gedeeltelijke configuratie van de levering bevatten.

Het leveringsmalplaatje kan manueel, zoals beschreven in dit hoofdstuk, of volgens een gebeurtenis (gelanceerd op een bepaald tijdstip, bij aankomst van een dossier bij een server, enz.) worden uitgevoerd. De malplaatjes van de levering kunnen via worden gevormd **[!UICONTROL Resources > Templates > Delivery templates]** knooppunt in de structuur.

![](assets/s_user_template_list.png)

Er zijn twee typen sjablonen:

1. Native leversjablonen van Adobe Campaign

   Native sjablonen MOGEN NIET uit het systeem worden verwijderd. Zij omvatten een minimumconfiguratie voor elk leveringskanaal. De beheerder kan echter bepaalde functies beperken of standaardwaarden aanbieden aan gebruikers (activering volgen, e-mailadressen van de afzender enz.). Native scenario&#39;s worden vet weergegeven in de lijst met sjablonen. Ze moeten worden gedupliceerd om ze te kunnen wijzigen.

1. Vooraf gedefinieerde leveringssjablonen

   De Adobe Campaign-beheerder kan nieuwe leveringssjablonen maken. Ze kunnen opnieuw worden gebruikt door operatoren (die met geschikte toegangsrechten) of automatisch door serverprocessen. Bijvoorbeeld, kunt u een malplaatje van de e-maillevering vormen, en wanneer de gebruikers tot levering gebruikend dit malplaatje leiden, moeten zij eenvoudig de tekst of de inhoud van de HTML ingaan en dan het leveren; de overige keuzen zijn al door de beheerder gedefinieerd.

>[!NOTE]
>
>De beschikbare malplaatjes hangen van uw toegangsrechten, van uw instantieconfiguratie, en van de context af. Wanneer u bijvoorbeeld een informatiedienst maakt, kunt u een leveringssjabloon koppelen voor bevestigingsberichten: u kunt dan slechts tot de malplaatjes toegang hebben waarvan doelafbeelding de abonnementstoewijzing is. Raadpleeg voor meer informatie hierover [Doeltoewijzing selecteren](selecting-a-target-mapping.md) en [Services en abonnementen](about-services-and-subscriptions.md).
