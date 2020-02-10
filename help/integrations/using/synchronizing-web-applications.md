---
title: Webtoepassingen synchroniseren
seo-title: Webtoepassingen synchroniseren
description: Webtoepassingen synchroniseren
seo-description: null
page-status-flag: never-activated
uuid: da74e4d3-e439-454a-8a43-6784e4789d1b
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: acs-connector
discoiquuid: df68ab11-7a8b-4e89-8cc4-8764e8a859b2
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0745b9c9d72538b8573ad18ff4054ecf788905f2

---


# Webtoepassingen synchroniseren{#synchronizing-web-applications}

In dit geval, zullen wij een mededeling verzenden, gebruikend de Norm van de Campagne, die een verbinding aan een het Webtoepassing van de Campagne v7 omvat. Wanneer de ontvanger op de koppeling in de e-mail klikt, geeft de webtoepassing een formulier weer dat verschillende velden bevat die zijn voorgeladen met de gegevens van de ontvanger en een abonnementkoppeling naar een nieuwsbrief. De ontvanger kan zijn gegevens bijwerken evenals aan de dienst intekenen. Zijn profiel zal in Campaign v7 worden bijgewerkt en de informatie zal in de Norm van de Campagne worden herhaald.

Als u veel services en webtoepassingen hebt in Campagne v7, kunt u deze mogelijk niet allemaal opnieuw maken in Campagnestandaard. De Schakelaar ACS staat u toe om al uw bestaande het Webtoepassingen en de diensten van de Campagne v7 te gebruiken en hen te verbinden aan een levering die door de Norm van de Campagne wordt verzonden.

## Vereisten {#prerequisites}

Hiervoor hebt u het volgende nodig:

* Ontvangers die zijn opgeslagen in de Campagne v7-database en zijn gesynchroniseerd met Campagnestandaard. Raadpleeg de sectie [Synchronizing profiles](../../integrations/using/synchronizing-profiles.md) .
* een service en een webtoepassing die zijn gemaakt en gepubliceerd in Campaign v7.
* de webtoepassing moet een **[!UICONTROL Pre-loading]** activiteit met behulp van de **[!UICONTROL Adobe Campaign encryption]** identificatiemethode bevatten.

## De webtoepassing en -service maken {#creating-the-web-application-and-service}

In Campagne v7, kunt u Webtoepassingen tot stand brengen die ontvangers toestaan om aan de dienst in te tekenen. De webtoepassing en -service zijn ontworpen en opgeslagen in Campagne v7 en u kunt deze service bijwerken via een standaardcommunicatie voor campagnes. Raadpleeg [deze sectie](../../web/using/adding-fields-to-a-web-form.md#subscription-checkboxes)voor meer informatie over webtoepassingen in Campagne v7.

In Campaign v7 zijn de volgende objecten gemaakt:

* een nieuwsbrief
* een webtoepassing die een **[!UICONTROL Pre-loading]**, een **[!UICONTROL Page]** en een **[!UICONTROL Storage]** activiteit bevat.

1. Ga naar **[!UICONTROL Resources > Online > Web applications]** en selecteer een bestaande webtoepassing.

   ![](assets/acs_connect_lp_2.png)

1. Bewerk de **[!UICONTROL Preloading]** activiteit. Het **[!UICONTROL Auto-load data referenced in the form]** selectievakje is ingeschakeld en de **[!UICONTROL Adobe Campaign encryption]** identificatiemethode is geselecteerd. Hierdoor kan de webtoepassing de formuliervelden vooraf laden met de gegevens die zijn opgeslagen in de Adobe Campagne-database. Zie [dit document](../../web/using/publishing-a-web-form.md#pre-loading-the-form-data).

   ![](assets/acs_connect_lp_4.png)

1. Bewerk de **[!UICONTROL Page]**. Er zijn drie velden (Naam, E-mail en Telefoon) opgenomen, evenals een selectievakje om de ontvanger uit te nodigen zich in te schrijven op een nieuwsbrief (**[!UICONTROL Newsletter]** service).

   ![](assets/acs_connect_lp_3.png)

1. Ga naar **[!UICONTROL Profiles and Target > Services and subscriptions]** en open de **[!UICONTROL Newsletter]** service. Dit is de dienst die van de Standaardmededeling van de Campagne zal worden bijgewerkt. U kunt zien dat geen ontvanger zich op deze service heeft geabonneerd.

   ![](assets/acs_connect_lp_5.png)

1. Ga naar **[!UICONTROL Profiles and Targets > Recipient]** en selecteer een ontvanger. U kunt zien dat hij nog niet aan de dienst heeft geabonneerd.

   ![](assets/acs_connect_lp_6.png)

## De gegevens repliceren {#replicating-the-data}

Om de vereiste gegevens tussen Campagne v7 en de Standaard van de Campagne te herhalen, zijn verscheidene malplaatjes van het replicatiewerkschema beschikbaar. In de **[!UICONTROL Profiles replication]** workflow worden automatisch alle campagneontvangers van versie 7 naar de campagnestandaard gerepliceerd. Zie [Technische workflows en replicatieworkflows](../../integrations/using/acs-connector-principles-and-data-cycle.md#technical-and-replication-workflows). De **[!UICONTROL Landing pages replication]** workflow maakt het mogelijk de webtoepassingen die we in Campagnestandaard willen gebruiken, te repliceren.

![](assets/acs_connect_lp_1.png)

Ga als volgt te werk om te controleren of de gegevens correct zijn gerepliceerd:

1. Klik op het beginscherm **[!UICONTROL Customer profiles]**.

   ![](assets/acs_connect_lp_7.png)

1. Zoek naar uw ontvanger van de Campagne v7 en controleer dat hij in de Norm van de Campagne verschijnt.

   ![](assets/acs_connect_lp_8.png)

1. Klik in de bovenste balk op de webtoepassing Campagne v7 **[!UICONTROL Marketing activities]** en zoek deze. Deze wordt weergegeven als een openingspagina in de campagnestandaard.

   ![](assets/acs_connect_lp_9.png)

1. Klik in de linkerbovenhoek op het **[!UICONTROL Adobe Campaign]** logo en selecteer **Profielen en publiek > Services** . Controleer ook of de nieuwsbrief beschikbaar is.

   ![](assets/acs_connect_lp_10.png)

## De e-mail ontwerpen en verzenden {#designing-and-sending-the-email}

In dit deel, zullen wij zien hoe te om een verbinding, in een Standaard e-mail van de Campagne te omvatten, aan de landingspagina die van een de Webtoepassing van de Campagne v7 wordt herhaald.

De stappen voor het maken, ontwerpen en verzenden van de e-mail zijn dezelfde als voor een klassieke e-mail. Raadpleeg de documentatie bij [Adobe Campaign Standard](https://helpx.adobe.com/support/campaign/standard.html) .

1. Maak een nieuwe e-mail en kies een of meer gerepliceerde profielen als het publiek.
1. Bewerk de inhoud en voeg een **[!UICONTROL Link to a landing page]** sjabloon in.

   ![](assets/acs_connect_lp_12.png)

1. Selecteer de bestemmingspagina die van de het Webtoepassing van de Campagne v7 werd herhaald.

   ![](assets/acs_connect_lp_13.png)

1. Bereid uw e-mail voor, verzend uw proefdrukken en verzend het definitieve e-mailbericht.
1. Een van de ontvangers opent de e-mail en klikt op de koppeling naar het abonnement op de nieuwsbrief.

   ![](assets/acs_connect_lp_14.png)

1. Hij voegt een telefoonnummer toe en controleert het abonnementsvak voor nieuwsbrieven.

   ![](assets/acs_connect_lp_15.png)

## De bijgewerkte gegevens ophalen {#retrieving-the-updated-information}

Wanneer de ontvanger zijn gegevens bijwerkt via de webtoepassing, haalt Adobe Campagne v7 synchroon de bijgewerkte informatie op. Het wordt dan herhaald van Campaign v7 aan de Norm van de Campagne.

1. Ga in Campaign v7 naar **[!UICONTROL Profiles and Target > Services and subscriptions]** en open de **[!UICONTROL Newsletter]** service. U ziet dat de ontvanger nu in de lijst met abonnees wordt weergegeven.

   ![](assets/acs_connect_lp_16.png)

1. Ga naar **[!UICONTROL Profiles and Targets > Recipient]** en selecteer de ontvanger. U kunt zien dat het telefoonnummer nu is opgeslagen.

   ![](assets/acs_connect_lp_17.png)

1. Op het **[!UICONTROL Subscriptions]** tabblad zien we ook dat hij zich heeft geabonneerd op de nieuwsbrief.

   ![](assets/acs_connect_lp_18.png)

1. Wacht een paar minuten totdat de workflow voor profielreplicatie wordt uitgevoerd.
1. In de Norm van de Campagne, heb toegang tot uw ontvankelijk profiel om te controleren dat de bijgewerkte gegevens correct van Campagne v7 zijn herhaald.

   ![](assets/acs_connect_lp_19.png)

1. Bewerk het profiel. U kunt zien dat het telefoonnummer is bijgewerkt.

   ![](assets/acs_connect_lp_20.png)

1. Klik op het **[!UICONTROL Subscriptions]** tabblad. De nieuwsbrief wordt nu weergegeven.

   ![](assets/acs_connect_lp_21.png)

