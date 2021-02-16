---
solution: Campaign Classic
product: campaign
title: Aan de slag met bijhouden
description: Meer weten over de algemene richtlijnen voor bijhouden in Adobe Campaign Classic?
audience: delivery
content-type: reference
topic-tags: tracking-messages
translation-type: tm+mt
source-git-commit: 55cc09c0446e389029890e45b790bb5ec6ffdc27
workflow-type: tm+mt
source-wordcount: '690'
ht-degree: 8%

---


# Aan de slag met bericht bijhouden {#get-started-tracking}

Dankzij de trackingfuncties van Adobe Campaign kunt u de verzonden berichten traceren en het gedrag van de ontvangers controleren: openen, klikken op koppelingen, geen abonnement nemen, enz.

Deze informatie wordt teruggewonnen in **[!UICONTROL Tracking]** lusje van het profiel van elke ontvanger van de levering. Dit tabblad bevat alle URL-koppelingen die worden bijgehouden en waarop de ontvanger heeft geklikt en die in de lijst zijn geselecteerd. Dit is de accumulatie van alle URLs die in de leveringen worden gevolgd die nog in het leveringsscherm aanwezig zijn. De lijst kan worden gevormd en zal typisch bevatten: de URL waarop is geklikt, de datum en tijd van de klik en het document waarin de URL is gevonden. Raadpleeg [deze sectie](../../platform/using/editing-a-profile.md#tracking-tab) voor meer informatie.

Het **leveringsdashboard** is ook van belang om uw leveringen en eventuele problemen te controleren die tijdens het verzenden van berichten worden ondervonden. Zie [deze sectie](../../delivery/using/delivery-dashboard.md) voor meer informatie hierover.

Het volgende diagram toont de stadia van de dialoog tussen de gebruiker en de diverse servers.

![](assets/tracking-diagram.png)

## Tekstspatiëring {#configure-tracking} configureren

<img src="assets/do-not-localize/icon-configure.svg" width="60px">

**Werkwijze**

Alvorens het volgen te gebruiken, moet u het voor uw instantie eerst vormen. [Meer informatie](../../installation/using/deploying-an-instance.md#operating-principle)

**Trackingserver**

Voor het configureren van tracering moet uw instantie worden gedeclareerd en geregistreerd bij de volgende server(s). [Meer informatie](../../installation/using/deploying-an-instance.md#tracking-server)

**Tekstspatiëring opslaan**

Zodra het volgen wordt gevormd en uw URLs bevolkt, moet de volgende server worden geregistreerd. [Meer informatie](../../installation/using/deploying-an-instance.md#tracking-configuration#saving-tracking)

## Berichten bijhouden {#message-tracking}

<img src="assets/do-not-localize/icon-message-tracking.svg" width="60px">

**Bijgehouden koppelingen**

U kunt de ontvangst van berichten en de activering van de verbindingen volgen die in de berichtinhoud worden opgenomen om het gedrag van ontvangers beter te begrijpen. [Meer informatie](../../delivery/using/how-to-configure-tracked-links.md)

**URL-tracking**

Traceringsopties kunnen worden geconfigureerd door bijgehouden URL&#39;s te activeren of deactiveren. [Meer informatie](../../delivery/using/personalizing-url-tracking.md)

**Aanpassing van koppelingen**

Met de mogelijkheden voor het bijhouden van Campaign Classic kunt u koppelingen toevoegen in e-mailberichten die kunnen worden aangepast en die het bijhouden van wijzigingen ondersteunen. [Meer informatie](https://helpx.adobe.com/campaign/kb/tracking-personnalized-links.html)

**Logboeken bijhouden**

Met de technische workflow voor bijhouden worden de gegevens voor bijhouden opgehaald nadat de levering is verzonden en de tekstspatiëring is geactiveerd. Deze gegevens vindt u op het tabblad Bijhouden van de levering. [Meer informatie](../../delivery/using/accessing-the-tracking-logs.md)

**Tracking van tests**

Voordat u de berichten verzendt met het bijhouden van de berichten, kunt u het bijhouden van de berichten testen op de spiegel-, e-maillogboeken en koppelingen. [Meer informatie](../../delivery/using/testing-tracking.md)

## Webtoepassing bijhouden {#web-application-tracking}

<img src="assets/do-not-localize/icon-web-app.svg" width="60px">

**Een webapplicatie opvolgen**

U kunt bezoeken op de toepassingspagina&#39;s van het Web met het volgen markeringen ook volgen en meten. Deze functionaliteit kan voor alle toepassingstypes van het Web zoals vormen en online onderzoeken worden gebruikt. [Meer informatie](../../web/using/tracking-a-web-application.md)

**Opt-out voor tracking van een webapplicatie**

Met de optie Web application tracking kunt u het webgedrag van eindgebruikers die zich afmelden voor het volgen van gedragingen, niet meer volgen. U kunt de mogelijkheid opnemen om een banner weer te geven in webtoepassingen of om pagina&#39;s te landen, zodat gebruikers zich kunnen afmelden. [Meer informatie](../../web/using/web-application-tracking-opt-out.md)

## Rapporten bijhouden {#tracking-reports}

<img src="assets/do-not-localize/icon_monitor.svg" width="60px">

**Trackingstatistieken**

Dit rapport bevat statistieken over openen, klikken en transacties en geeft u inzicht in de marketingeffecten van de levering. [Meer informatie](../../reporting/using/delivery-reports.md#tracking-statistics)

**URL&#39;s en klikpaden**

Dit rapport bevat de lijst met bezochte pagina&#39;s na een levering. [Meer informatie](../../reporting/using/delivery-reports.md#urls-and-click-streams)

**Persoon/personen en ontvangers**

Met dit voorbeeld kunt u beter het verschil zien dat personen en ontvangers in Adobe Campaign kunnen bijhouden. [Meer informatie](../../reporting/using/person-people-recipients.md)

**Trackingsindicatoren**

Dit rapport combineert de belangrijkste indicatoren voor het volgen van het gedrag van ontvangers bij het ontvangen van de levering zoals open, klikthrough tarieven en klikstromen. [Meer informatie](../../reporting/using/delivery-reports.md#tracking-indicators)

**Indicatoren berekenen**

De verschillende tabellen geven u de lijst van indicatoren die in de verschillende rapporten worden gebruikt en hun berekeningsformule afhankelijk van het leveringstype. [Meer informatie](../../reporting/using/indicator-calculation.md)

## Problemen bijhouden {#tracking-troubleshooting}

<img src="assets/do-not-localize/icon-troubleshooting.svg" width="60px">

De volgende tips voor het oplossen van problemen helpen u de meest voorkomende problemen op te lossen die zich voordoen bij het gebruik van tracking in Adobe Campaign Classic. Raadpleeg [deze sectie](../../delivery/using/tracking-troubleshooting.md) voor een geavanceerdere probleemoplossing.

* Controleren of het trackinglogproces wordt uitgevoerd

   Dit proces leest van het gedeelde geheugen IIS/de Server van het Web en schrijft de redirection logboeken.

   U kunt het van de Homepage tot toegang hebben door het lusje van de Controle in uw geval te selecteren. U kunt ook de volgende opdracht op de instantie uitvoeren: `<user>@<instance>:~$ nlserver pdump`

   Als het trackinglogproces niet in de lijst wordt weergegeven, start u het proces met de volgende opdracht op het exemplaar: `<user>@<instance>:~$ nlserver start trackinglogd`

* Controleer of de technische workflow voor bijhouden de laatste tijd is uitgevoerd.

   U vindt de technische workflow voor bijhouden in de mappen Beheer > Productie > Technische workflows.
