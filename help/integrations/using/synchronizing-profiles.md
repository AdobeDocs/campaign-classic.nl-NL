---
product: campaign
title: Profielen synchroniseren
description: Leer hoe te om profielen met Schakelaar ACS te synchroniseren
feature: ACS Connector
hide: true
hidefromtoc: true
exl-id: 27970a6f-fb22-4418-b29c-c687fd62a78e
source-git-commit: 4d8c4ba846148d3df00a76ecc29375b9047c2b20
workflow-type: tm+mt
source-wordcount: '1155'
ht-degree: 1%

---

# Profielen synchroniseren{#synchronizing-profiles}



ACS Connector repliceert gegevens van Campaign v7 aan Campaign Standard. De gegevens die zijn ontvangen van Campaign v7 kunnen in Campaign Standard worden gebruikt om leveringen te maken. U kunt zien hoe profielen worden gesynchroniseerd door de hieronder vermelde bewerkingen uit te voeren.

* **voeg nieuwe ontvangers** toe: Creeer een nieuwe ontvanger in Campagne v7 en bevestig dat een overeenkomstig profiel aan Campaign Standard is herhaald. Zie [ een nieuwe ontvanger ](#creating-a-new-recipient) creëren.
* **de ontvangers van de Update**: geef een nieuwe ontvanger in Campagne v7 uit en bekijk het overeenkomstige profiel in Campaign Standard om te bevestigen dat de update is herhaald. Zie [ een ontvanger ](#editing-a-recipient) uitgeven.
* **bouwt een werkschema in Campaign Standard**: Creeer een werkschema in Campaign Standard dat een vraag met een publiek of profielen omvat die van Campagne v7 worden herhaald. Zie [ een werkschema ](#creating-a-workflow) creëren.
* **creeer een levering in Campaign Standard**: Volg het werkschema aan voltooiing om een levering te verzenden. Zie [ een levering ](#creating-a-delivery) creëren.
* **verifieer de unsubscription verbinding**: Gebruik een het Webtoepassing van de Campagne v7 om ervoor te zorgen dat de keus van de ontvanger om aan de dienst af te melden wordt verzonden naar het gegevensbestand van de Campagne v7. De optie om de service niet meer te ontvangen, wordt naar Campaign Standard gerepliceerd. Zie [ Verandering de unsubscription verbinding ](#changing-the-unsubscription-link).

## Vereisten {#prerequisites}

De volgende secties beschrijven hoe de Schakelaar ACS u helpt ontvangers in Campagne v7 toevoegen en uitgeven en dan hen in een levering van Campaign Standard gebruiken. ACS Connector vereist het volgende:

* Ontvangers in Campaign v7 zijn overgenomen in Campaign Standard.
* Gebruikersrechten om workflows uit te voeren in zowel Campagne v7 als Campaign Standard.
* Gebruikersrechten om een levering te maken en uit te voeren in Campaign Standard.

## De koppeling voor het opzeggen van abonnementen wijzigen {#changing-the-unsubscription-link}

Wanneer een ontvanger in een e-mailbericht van Campaign Standard op de koppeling voor het opzeggen van een abonnement klikt, wordt het bijbehorende profiel in Campaign Standard bijgewerkt. Om ervoor te zorgen dat een gerepliceerd profiel de keuze van de gebruiker bevat om zich af te melden voor een service, moet de informatie naar Campagne v7 worden verzonden in plaats van naar Campaign Standard. Om de wijziging uit te voeren, wordt de service voor het opzeggen van abonnementen gekoppeld aan een Campagne v7-webtoepassing in plaats van aan Campaign Standard.

>[!NOTE]
>
>Vraag uw consultant om de webtoepassing voor de service voor abonnementen te configureren voordat u de onderstaande stappen uitvoert.

## Een nieuwe ontvanger maken {#creating-a-new-recipient}

1. Maak een nieuwe ontvanger in Campagne v7 voor replicatie naar Campaign Standard. Voer zoveel mogelijk gegevens in, zoals de achternaam, voornaam, e-mailadres en postadres van de ontvanger. Nochtans, kies geen a **[!UICONTROL Salutation]** aangezien het in de volgende sectie zal worden toegevoegd, [ geef een ontvanger ](#editing-a-recipient) uit.

   ![](assets/acs_connect_profile_sync_01.png)

1. Bevestig dat de nieuwe ontvanger aan Campaign Standard is toegevoegd. Controleer bij het bekijken van het profiel of de gegevens die u hebt ingevoerd in Campaign v7, ook beschikbaar zijn in Campaign Standard. Leren waar te om profielen in Campaign Standard te vinden, zie [ Grondbeginselen van de Navigatie ](https://experienceleague.adobe.com/docs/campaign-standard/using/getting-started/discovering-the-interface/interface-description.html?lang=nl).

   ![](assets/acs_connect_profile_sync_02.png)

   Door gebrek, is de periodieke replicatie voor Schakelaar ACS eens om de 15 minuten. Voor verdere informatie, zie [ replicatie van Gegevens ](../../integrations/using/acs-connector-principles-and-data-cycle.md#data-replication).

## Een ontvanger bewerken {#editing-a-recipient}

De stappen hieronder voor het veranderen van één enkel punt van gegevens bieden een eenvoudig voorbeeld van hoe Campagne v7 het primaire gegevensbestand voor Campaign Standard wordt wanneer het gebruiken van gegevensreplicatie. Het wijzigen of verwijderen van herhaalde gegevens in Campagne v7 heeft hetzelfde effect op de overeenkomstige gegevens in Campaign Standard.

1. Kies de pas gecreëerde ontvanger van [ creeer een nieuwe ontvanger ](#creating-a-new-recipient) en geef de naam van de ontvanger uit. Kies bijvoorbeeld een **[!UICONTROL Salutation]** voor de ontvanger (bijvoorbeeld de heer of mevrouw).

   ![](assets/acs_connect_profile_sync_03.png)

1. Bevestig dat de naam van de ontvanger is bijgewerkt in Campaign Standard. Leren waar te om profielen in Campaign Standard te vinden, zie [ Grondbeginselen van de Navigatie ](https://experienceleague.adobe.com/docs/campaign-standard/using/getting-started/discovering-the-interface/interface-description.html?lang=nl).

   ![](assets/acs_connect_profile_sync_04.png)

   Door gebrek, is de periodieke replicatie voor Schakelaar ACS eens om de 15 minuten. Voor verdere informatie, zie [ replicatie van Gegevens ](../../integrations/using/acs-connector-principles-and-data-cycle.md#data-replication).

## Een workflow maken {#creating-a-workflow}

Profielen en services die zijn gerepliceerd vanuit Campaign v7, zijn beschikbaar voor digitale marketers om de rijke gegevens in Campaign Standard te benutten. In de onderstaande instructies ziet u hoe u een query toevoegt aan een Campaign Standard-workflow en deze vervolgens gebruikt met de gerepliceerde database.

Voor verdere informatie en volledige instructies betreffende de werkschema&#39;s van Campaign Standard, zie [ Werkschema&#39;s ](../../workflow/using/about-workflows.md).

1. Ga naar Campaign Standard en klik op **[!UICONTROL Marketing Activities]** .
1. Klik op **[!UICONTROL Create]** rechtsboven.
1. Klik op **[!UICONTROL Workflow]**.
1. Klik op **[!UICONTROL New workflow]** en **[!UICONTROL Next]** .
1. Voer in het veld **[!UICONTROL Label]** een naam voor de workflow in en geef desgewenst aanvullende informatie op. Klik op **[!UICONTROL Next]**.
1. Sleep een **[!UICONTROL Targeting]** -doel vanuit **[!UICONTROL Query]** aan de linkerkant naar de werkruimte.

   ![](assets/acs_connect_profile_sync_05.png)

1. Dubbelklik op de **[!UICONTROL Query]** -activiteit en kies een parameter die kan worden gebruikt met de gerepliceerde database. U kunt bijvoorbeeld:

   * Sleep **[!UICONTROL Profiles]** naar de werkruimte. Kies in het keuzemenu met velden de optie **[!UICONTROL Is external resource]** om te zoeken naar profielen die zijn gerepliceerd vanuit Campagne v7.
   * Sleep andere queryparameters om de gekopieerde profielen verder te activeren.

## Een levering maken {#creating-a-delivery}

>[!NOTE]
>
>De instructies voor het creëren van de levering gaan het werkschema voort dat met [ is begonnen creeer een werkschema ](#creating-a-workflow).

Digitale marketers kunnen een Campagne v7-webtoepassing gebruiken om ervoor te zorgen dat de keuze van een ontvanger om zich af te melden voor een service naar de Campagne v7-database wordt verzonden. Nadat de ontvanger op de verbinding klikt unsubscription, wordt de optie om op te houden die de dienst ontvangt herhaald van Campagne v7 aan Campaign Standard. Voor extra details, zie [ Verandering de unsubscription verbinding ](#changing-the-unsubscription-link).

Voer de onderstaande stappen uit om een e-maillevering toe te voegen aan een bestaande workflow met de service voor het opzeggen van abonnementen die is gemaakt in Campagne v7. Voor verdere informatie en volledige instructies betreffende de werkschema&#39;s van Campaign Standard, zie dit [ document ](../../workflow/using/about-workflows.md).

>[!NOTE]
>
>Vraag uw consultant om de webtoepassing voor de service voor abonnementen te configureren voordat u de onderstaande stappen uitvoert.

1. Klik op **[!UICONTROL Channels]** aan de linkerkant.
1. Sleep **[!UICONTROL Email delivery]** naar de bestaande workflow in de werkruimte.

   ![](assets/acs_connect_profile_sync_07.png)

1. Dubbelklik op de **[!UICONTROL Email delivery]** -activiteit en kies **[!UICONTROL Single send email]** of **[!UICONTROL Recurring email]** . Selecteer de gewenste opties en klik op **[!UICONTROL Next]** .
1. Klik **[!UICONTROL Send via email]** en klik **[!UICONTROL Next]**.

   ![](assets/acs_connect_profile_sync_08.png)

1. Voer in het veld **[!UICONTROL Label]** een naam voor de levering in en geef desgewenst aanvullende informatie op. Klik op **[!UICONTROL Next]**.

   ![](assets/acs_connect_profile_sync_09.png)

1. Voer in het veld **[!UICONTROL Subject]** het onderwerp in dat wordt weergegeven in het Postvak IN van de ontvanger.
1. Klik op **[!UICONTROL Change content]** om een HTML-sjabloon toe te voegen.

   ![](assets/acs_connect_profile_sync_10.png)

1. Kies inhoud die de koppeling bevat om het abonnement op de service op te zeggen. Klik op **[!UICONTROL Confirm]**.

   ![](assets/acs_connect_profile_sync_11.png)

1. De huidige koppeling voor het opzeggen van abonnementen moet worden vervangen door een nieuwe koppeling die gebruikmaakt van de webtoepassing die door uw consultant is gemaakt. Zoek de koppeling voor het opzeggen van abonnementen onder aan de e-mailinhoud en klik eenmaal op deze koppeling. Klik op het prullenbakpictogram om de koppeling te verwijderen.

   ![](assets/acs_connect_profile_sync_12.png)

1. Klik binnen het zelfde inhoudsgebied en type **Verbinding Unsubscription**.

   ![](assets/acs_connect_profile_sync_13.png)

1. Markeer de tekst met de cursor en klik op het ketingpictogram.
1. Klik op **[!UICONTROL Link to a landing page]**.

   ![](assets/acs_connect_profile_sync_14.png)

1. Klik op het mappictogram om de openingspagina te kiezen.

   ![](assets/acs_connect_profile_sync_15.png)

1. Kies de webtoepassing die door de consultant is gemaakt en klik op **[!UICONTROL Confirm]** .

   ![](assets/acs_connect_profile_sync_16.png)

1. Klik op **[!UICONTROL Create]**.
1. Ga terug naar de workflow door op de naam van de levering te klikken.

   ![](assets/acs_connect_profile_sync_17.png)

1. Klik op **[!UICONTROL Start]** om de levering te verzenden. Het pictogram voor verzending via e-mail knippert om aan te geven dat het wordt voorbereid voor levering.

   ![](assets/acs_connect_profile_sync_18.png)

1. Dubbelklik op het kanaal **[!UICONTROL Email delivery]** en kies **[!UICONTROL Confirm]** om de e-mail te verzenden. Klik op **[!UICONTROL OK]** om de berichten te verzenden.

   ![](assets/acs_connect_profile_sync_19.png)

## Verifieer de unsubscription-service {#verifying-the-unsubscription-service}

Volg de instructies in [ creeer een werkschema ](#creating-a-workflow) en [ creeer een levering ](#creating-a-delivery) alvorens aan de hieronder stappen te bewegen.

1. De ontvanger klikt op de koppeling om het abonnement op te zeggen in de e-maillevering.

   ![](assets/acs_connect_profile_sync_20.png)

1. De ontvanger bevestigt het abonnement.

   ![](assets/acs_connect_profile_sync_21.png)

1. De ontvankelijke gegevens in Campagne v7 worden bijgewerkt om erop te wijzen dat de gebruiker heeft geabonneerd. Bevestig dat het vak **[!UICONTROL No longer contact (by any channel)]** is ingeschakeld voor de ontvanger.

   ![](assets/acs_connect_profile_sync_22.png)

1. Ga naar Campaign Standard en open de profieldetails voor de ontvanger. Controleer of naast **[!UICONTROL No longer contact (by any channel)]** een selectievakje wordt weergegeven. Leren waar te om profielen in Campaign Standard te vinden, zie [ Grondbeginselen van de Navigatie ](https://experienceleague.adobe.com/docs/campaign-standard/using/getting-started/discovering-the-interface/interface-description.html?lang=nl).

   ![](assets/acs_connect_profile_sync_23.png)
