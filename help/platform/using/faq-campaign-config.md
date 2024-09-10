---
product: campaign
title: Veelgestelde vragen over Campaign-instellingen
description: Veelgestelde vragen over Campaign Classic
feature: Troubleshooting, Application Settings
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: 50bed489-2a0f-4123-a326-3d68c8295662
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '752'
ht-degree: 72%

---

# Veelgestelde vragen over Campaign-instellingen {#settings-faq}



Ontdek de belangrijkste configuraties om uw instantie van Campaign aan uw behoeften aan te passen.

## Kan ik de taal van de interface van de Campagne veranderen? {#can-i-change-the-language-of-campaign-interface-}

De taal van Campaign wordt geselecteerd wanneer u de instantie maakt. U kunt deze naderhand niet wijzigen. Raadpleeg [deze sectie](../../installation/using/creating-an-instance-and-logging-on.md) voor meer informatie.

De Adobe Campaign-gebruikersinterface is beschikbaar in vier talen: Engels, Frans, Duits en Japans. De clientconsole en de server moeten in dezelfde taal zijn ingesteld. Elke Campaign-instantie kan slechts in één taal worden uitgevoerd.

Voor het Engels kunt u bij de installatie van Campaign Engels voor de VS of Engels voor het VK selecteren, die verschillende datumnotaties en tijdnotaties hebben. Raadpleeg [deze sectie](../../platform/using/adobe-campaign-workspace.md#date-and-time) voor meer informatie over deze verschillen.

## Kan ik Campaign Classic met andere Adobe oplossingen gebruiken? {#can-i-use-campaign-classic-with-other-adobe-solutions-}

U kunt de leveringsfuncties en de functies voor geavanceerd campagnebeheer van Adobe Campaign combineren met een reeks oplossingen die u helpen uw gebruikerservaring aan te passen.

Klik hier om te leren [hoe u met andere Adobe-oplossingen werkt](../../integrations/using/about-campaign-integrations.md) en [hoe u IMS instelt in Campaign](../../integrations/using/about-adobe-id.md).

## Hoe kan ik het volgen mogelijkheden op mijn instantie van de Campagne plaatsen? {#how-can-i-set-up-tracking-capabilities-on-my-campaign-instance-}

Als ervaren gebruiker kunt u trackingmogelijkheden configureren op uw instantie van Campaign.

[Klik hier voor meer informatie](../../installation/using/deploying-an-instance.md#tracking-configuration).

## Hoe te om e-mailleverbaarheid te vormen? {#how-to-configure-email-deliverability-}

Naast de [ Gids van de Beste praktijken van de Levering van de Adobe de Beste van de Praktijk van de Levering ](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=nl), lees de leverbaarheid technische aanbevelingen om te begrijpen hoe te om uw instantie te vormen om Campagne te maximaliseren leverend mogelijkheden.

[Klik hier voor meer informatie](../../delivery/using/about-deliverability.md).

## Hoe kan ik inhoudsgoedkeuring implementeren? {#how-can-i-implement-content-approval-}

Met Campaign kunt u goedkeuringsprocessen instellen voor de belangrijkste stappen van de marketingcampagne in de collaboratieve modus. Voor elke campagne kunt u het leveringsdoel, de content en de kosten goedkeuren. Adobe Campaign-operatoren die met de goedkeuring zijn belast, kunnen via e-mail op de hoogte worden gesteld en kunnen goedkeuring van de console of via een webverbinding accepteren of afwijzen.

[Klik hier voor meer informatie](../../campaign/using/marketing-campaign-approval.md#checking-and-approving-deliveries) en ontdek de stappen om goedkeuring van de leveringscontent in Campaign uit te voeren.

## Hoe kan ik tot gegevens toegang hebben die in een extern gegevensbestand worden opgeslagen? {#how-can-i-access-data-stored-in-an-external-database-}

Adobe Campaign biedt de FDA-optie (Federated Data Access) om informatie die is opgeslagen in een of meer externe databases te verwerken: u hebt toegang tot externe data zonder de structuur van Adobe Campaign-data te wijzigen.

[Klik hier voor meer informatie](../../installation/using/connecting-to-database.md).

## Met welke externe databases kan ik een campagne verbinden? {#which-external-databases-can-i-connect-campaign-to-}

De externe databases die compatibel zijn met Campaign via FDA (Federated Data Access) worden vermeld in de [compatibiliteitsmatrix](../../rn/using/compatibility-matrix.md).

## Kan Adobe Campaign integreren met LDAP? {#can-adobe-campaign-integrate-with-ldap-}

Als on-premise/hybride klant kunt u Campaign Classic integreren met uw LDAP-directory.

[Klik hier voor meer informatie](../../installation/using/connecting-through-ldap.md).

## Hoe kan ik schakelaars van opstellingsCRM in Campaign? {#how-can-i-set-up-crm-connectors-in-campaign-}

Adobe Campaign biedt verschillende CRM-connectoren waarmee u uw Adobe Campaign-platform kunt koppelen aan systemen van derden. Deze CRM-connectoren laten u toe om contactpersonen, accounts, aankopen, enzovoort, te synchroniseren. Ze zorgen ervoor dat uw applicatie eenvoudig kan worden geïntegreerd met verschillende externe en zakelijke applicaties.

Deze schakelaars laten snelle en gemakkelijke gegevensintegratie toe: Adobe Campaign verstrekt een specifieke medewerker voor het verzamelen van en het selecteren van uit de lijsten beschikbaar in CRM. Dit garandeert tweerichtingssynchronisatie om ervoor te zorgen dat de data altijd up-to-date zijn in alle systemen.

Lees uit [ vorm de schakelaars van CRM ](../../platform/using/crm-connectors.md) om te leren hoe te om uw hulpmiddel van CRM met Adobe Campaign te synchroniseren.

![](assets/do-not-localize/how-to-video.png) bekijk dit gebruiksgeval video op [ Adobe Campaign en Microsoft Dynamics 365 integratie ](https://helpx.adobe.com/campaign/kt/acc/using/acc-integrate-dynamics365-with-acc-feature-video-set-up.html).

## Hoe te om Zacht Geheime voorgeheugen Duidelijk uit te voeren wanneer de kwesties machine-specifiek of gebruiker-specifiek zijn? {#perform-soft-cache-clear}

Als u problemen hebt met bijvoorbeeld de correcte weergave van de nieuwe logo’s of het exporteren van data die machinespecifiek of gebruikerspecifiek zijn, moet u mogelijk de soft cache wissen met Windows (Windows 7, Windows XP, Windows 10).

Nadat u zich hebt aangemeld, gaat u naar **[!UICONTROL File]** > **[!UICONTROL Clear the local cache]**. Meld u vervolgens af en meld u weer aan.

![](assets/faq_soft_cache.png)

Als dit nog steeds niet helpt, probeert u de hard cache te wissen door de onderstaande stappen uit te voeren.

## Hoe te om het Geheime voorgeheugen Duidelijk uit te voeren wanneer de kwesties machine-specifiek of gebruiker-specifiek zijn? {#perform-hard-cache-clear}

Als u problemen hebt met bijvoorbeeld de correcte weergave van de nieuwe logo’s of het exporteren van data die machinespecifiek of gebruikerspecifiek zijn, moet u mogelijk de hard cache wissen met Windows (Windows 7, Windows XP, Windows 10).

1. Kies in de clientconsole **[!UICONTROL File]** > **[!UICONTROL Clear the local cache]**.

1. Meld u af en sluit de clientconsole (rich client).

1. Ga naar de volgende locaties op basis van uw versie van het besturingssysteem:

   * Windows 7: C:\Users\&lt; Gebruikersnaam >\AppData\Roaming\Neolane\NL_5\
   * Windows XP: C:\Documents and Settings\&lt; Gebruikersnaam >\Application Data\Neolane\NL_5

   Hier ziet u verschillende XML-bestanden met de naam nlclient-config-&lt; alfanumerieke waarde >.xml.

1. Verwijder deze XML-bestanden en de bijbehorende mappen.

   >[!IMPORTANT]
   >
   >Verwijder het bestand nlclient_cnx.xml niet.

1. Meld u aan bij de clientconsole.
