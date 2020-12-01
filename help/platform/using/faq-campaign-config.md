---
solution: Campaign Classic
product: campaign
title: Veelgestelde vragen over Campaign-instellingen
description: Veelgestelde vragen over Campaign Classic
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
translation-type: tm+mt
source-git-commit: 20dcdd91d71158bc373db68c3f61f6808b240bd2
workflow-type: tm+mt
source-wordcount: '750'
ht-degree: 100%

---


# Veelgestelde vragen over Campaign-instellingen {#settings-faq}

Ontdek de belangrijkste configuraties om uw instantie van Campaign aan uw behoeften aan te passen.

## Kan ik de taal van de Campaign-interface wijzigen? {#can-i-change-the-language-of-campaign-interface-}

De taal van Campaign wordt geselecteerd wanneer u de instantie maakt. U kunt deze naderhand niet wijzigen. Raadpleeg [deze sectie](../../installation/using/creating-an-instance-and-logging-on.md) voor meer informatie.

De Adobe Campaign-gebruikersinterface is beschikbaar in vier talen: Engels, Frans, Duits en Japans. De clientconsole en de server moeten in dezelfde taal zijn ingesteld. Elke Campaign-instantie kan slechts in één taal worden uitgevoerd.

Voor het Engels kunt u bij de installatie van Campaign Engels voor de VS of Engels voor het VK selecteren, die verschillende datumnotaties en tijdnotaties hebben. Raadpleeg [deze sectie](../../platform/using/adobe-campaign-workspace.md#date-and-time) voor meer informatie over deze verschillen.

## Kan ik Campaign Classic gebruiken met andere Adobe-oplossingen? {#can-i-use-campaign-classic-with-other-adobe-solutions-}

U kunt de leveringsfuncties en de functies voor geavanceerd campagnebeheer van Adobe Campaign combineren met een reeks oplossingen die u helpen uw gebruikerservaring aan te passen.

Klik hier om te leren [hoe u met andere Adobe-oplossingen werkt](../../integrations/using/about-campaign-integrations.md) en [hoe u IMS instelt in Campaign](../../integrations/using/about-adobe-id.md).

## Hoe kan ik trackingmogelijkheden op mijn instantie van Campaign instellen? {#how-can-i-set-up-tracking-capabilities-on-my-campaign-instance-}

Als ervaren gebruiker kunt u trackingmogelijkheden configureren op uw instantie van Campaign.

[Klik hier voor meer informatie](../../installation/using/deploying-an-instance.md#tracking-configuration).

## Hoe kan ik e-mailleverbaarheid configureren? {#how-to-configure-email-deliverability-}

Lees naast de sectie over [Configuratie van de leverbaarheid](../../delivery/using/about-deliverability.md#configuration) ook de technische aanbevelingen inzake leverbaarheid om te begrijpen hoe u uw instantie kunt configureren om de leveringsmogelijkheden van uw instantie te maximaliseren.

[Klik hier voor meer informatie](../../delivery/using/technical-recommendations.md).

## Hoe kan ik contentgoedkeuring implementeren? {#how-can-i-implement-content-approval-}

Met Campaign kunt u goedkeuringsprocessen instellen voor de belangrijkste stappen van de marketingcampagne in de collaboratieve modus. Voor elke campagne kunt u het leveringsdoel, de content en de kosten goedkeuren. Adobe Campaign-operatoren die met de goedkeuring zijn belast, kunnen via e-mail op de hoogte worden gesteld en kunnen goedkeuring via de console of via een webverbinding accepteren of afwijzen.

[Klik hier voor meer informatie](../../campaign/using/marketing-campaign-approval.md#checking-and-approving-deliveries) en ontdek de stappen om goedkeuring van de leveringscontent in Campaign uit te voeren.

## Hoe kan ik toegang krijgen tot data die in een externe database zijn opgeslagen? {#how-can-i-access-data-stored-in-an-external-database-}

Adobe Campaign biedt de FDA-optie (Federated Data Access) om informatie die is opgeslagen in een of meer externe databases te verwerken: u hebt toegang tot externe data zonder de structuur van Adobe Campaign-data te wijzigen.

[Klik hier voor meer informatie](../../installation/using/connecting-to-database.md).

## Met welke externe databases kan ik Campaign verbinden? {#which-external-databases-can-i-connect-campaign-to-}

De externe databases die compatibel zijn met Campaign via FDA (Federated Data Access) worden vermeld in de [compatibiliteitsmatrix](../../rn/using/compatibility-matrix.md).

## Kan Adobe Campaign integreren met LDAP? {#can-adobe-campaign-integrate-with-ldap-}

Als on-premise/hybride klant kunt u Campaign Classic integreren met uw LDAP-directory.

[Klik hier voor meer informatie](../../installation/using/connecting-through-ldap.md).

## Hoe kan ik CRM-connectoren instellen in Campaign? {#how-can-i-set-up-crm-connectors-in-campaign-}

Adobe Campaign biedt verschillende CRM-connectoren waarmee u uw Adobe Campaign-platform kunt koppelen aan systemen van derden. Deze CRM-connectoren laten u toe om contactpersonen, accounts, aankopen, enzovoort, te synchroniseren. Ze zorgen ervoor dat uw applicatie eenvoudig kan worden geïntegreerd met verschillende externe en zakelijke applicaties.

Deze connectoren maken snelle en eenvoudige data-integratie mogelijk: Adobe Campaign verstrekt een specifieke wizard voor het verzamelen en selecteren van data uit de lijsten die beschikbaar zijn in het CRM-systeem. Dit garandeert tweerichtingssynchronisatie om ervoor te zorgen dat de data altijd up-to-date zijn in alle systemen.

Lees [CRM-connectoren configureren](../../platform/using/crm-connectors.md) om te ontdekken hoe u uw CRM-tool met Adobe Campaign kunt synchroniseren.

![](assets/do-not-localize/how-to-video.png) Bekijk deze video met gebruiksscenario’s over [de integratie van Adobe Campaign en Microsoft Dynamics 365](https://helpx.adobe.com/campaign/kt/acc/using/acc-integrate-dynamics365-with-acc-feature-video-set-up.html).

## Hoe kan ik de soft cache wissen wanneer de problemen machinespecifiek of gebruikerspecifiek zijn? {#perform-soft-cache-clear}

Als u problemen hebt met bijvoorbeeld de correcte weergave van de nieuwe logo’s of het exporteren van data die machinespecifiek of gebruikerspecifiek zijn, moet u mogelijk de soft cache wissen met Windows (Windows 7, Windows XP, Windows 10).

Nadat u zich hebt aangemeld, gaat u naar **[!UICONTROL File]** > **[!UICONTROL Clear the local cache]**. Meld u vervolgens af en meld u weer aan.

![](assets/faq_soft_cache.png)

Als dit nog steeds niet helpt, probeert u de hard cache te wissen door de onderstaande stappen uit te voeren.

## Hoe kan ik de hard cache wissen wanneer de problemen machinespecifiek of gebruikerspecifiek zijn? {#perform-hard-cache-clear}

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