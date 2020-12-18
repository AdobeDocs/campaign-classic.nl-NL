---
solution: Campaign Classic
product: campaign
title: Sjablonen
description: Sjablonen
audience: delivery
content-type: reference
topic-tags: using-delivery-templates
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '275'
ht-degree: 2%

---


# Sjablonen{#about-templates}

Een leveringsconfiguratie kan in een leveringsmalplaatje worden bewaard om opnieuw te worden gebruikt. De sjabloon kan een volledige of gedeeltelijke configuratie van de levering bevatten.

Het leveringsmalplaatje kan manueel, zoals beschreven in dit hoofdstuk, of volgens een gebeurtenis (gelanceerd op een bepaald tijdstip, bij aankomst van een dossier bij een server, enz.) worden uitgevoerd. De malplaatjes van de levering kunnen via de **[!UICONTROL Resources > Templates > Delivery templates]** knoop in de boom worden gevormd.

![](assets/s_user_template_list.png)

Er zijn twee typen sjablonen:

1. Native leversjablonen van Adobe Campaign

   Native sjablonen MOGEN NIET uit het systeem worden verwijderd. Zij omvatten een minimumconfiguratie voor elk leveringskanaal. De beheerder kan echter bepaalde functies beperken of standaardwaarden aanbieden aan gebruikers (activering volgen, e-mailadressen van de afzender enz.). Native scenario&#39;s worden vet weergegeven in de lijst met sjablonen. Ze moeten worden gedupliceerd om ze te kunnen wijzigen.

1. Vooraf gedefinieerde leveringssjablonen

   De Adobe Campaign-beheerder kan nieuwe leveringssjablonen maken. Ze kunnen opnieuw worden gebruikt door operatoren (die met geschikte toegangsrechten) of automatisch door serverprocessen. Bijvoorbeeld, kunt u een malplaatje van de e-maillevering vormen, en wanneer de gebruiker een levering gebruikend dit malplaatje creeert, moet hij eenvoudig de tekst of de inhoud van HTML ingaan en dan het leveren; de overige keuzen zijn al door de beheerder gedefinieerd.

>[!NOTE]
>
>De beschikbare malplaatjes hangen van uw toegangsrechten, van uw instantieconfiguratie, en van de context af. Wanneer u bijvoorbeeld een informatiedienst maakt, kunt u een leveringssjabloon koppelen voor bevestigingsberichten: u kunt dan slechts tot de malplaatjes toegang hebben waarvan doelafbeelding de abonnementstoewijzing is. Raadpleeg [Een doeltoewijzing selecteren](../../delivery/using/selecting-a-target-mapping.md) en [Informatie over services en abonnementen](../../delivery/using/about-services-and-subscriptions.md) voor meer informatie.
