---
product: campaign
title: Aan de slag met bijhouden
description: Meer informatie over de algemene richtlijnen voor bijhouden in Adobe Campaign
badge-v8: label="Ook van toepassing op v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
feature: Monitoring, Email
role: User
exl-id: 43779505-9917-4e99-af25-b00a9d29a645
source-git-commit: 4d8c4ba846148d3df00a76ecc29375b9047c2b20
workflow-type: tm+mt
source-wordcount: '684'
ht-degree: 8%

---

# Aan de slag met bericht bijhouden {#get-started-tracking}



Dankzij de trackingfuncties van Adobe Campaign kunt u de verzonden berichten bijhouden en het gedrag van ontvangers controleren: openen, klikken op koppelingen, Abonnement opzeggen, enzovoort.

Deze informatie wordt opgehaald op het tabblad **[!UICONTROL Tracking]** van het profiel van elke ontvanger van de levering. Dit tabblad bevat alle URL-koppelingen die worden bijgehouden en waarop de ontvanger heeft geklikt en die in de lijst zijn geselecteerd. Dit is de accumulatie van alle URLs die in de leveringen worden gevolgd die nog in het leveringsscherm aanwezig zijn. De lijst kan worden gevormd en zal typisch bevatten: URL klikte, de datum en de tijd van de klik, en het document waarin URL werd gevonden.

Het **leveringsdashboard** is ook zeer belangrijk om uw leveringen en uiteindelijke kwesties te controleren die tijdens het verzenden van berichten worden ontmoet. Voor meer op dit verwijs naar [ deze sectie ](delivery-dashboard.md).

Het volgende diagram toont de stadia van de dialoog tussen de gebruiker en de diverse servers.

![](assets/tracking-diagram.png)

## Tracking configureren {#configure-tracking}

<img src="assets/do-not-localize/icon-configure.svg" width="60px">

**Werkwijze**

Alvorens het volgen te gebruiken, moet u het voor uw instantie eerst vormen. [Meer informatie](../../installation/using/deploying-an-instance.md#operating-principle)

**het Volgen server**

Voor het configureren van tracering moet uw instantie worden gedeclareerd en geregistreerd bij de volgende server(s). [Meer informatie](../../installation/using/deploying-an-instance.md#tracking-server)

**het Opslaan het volgen**

Zodra het volgen wordt gevormd en uw URLs bevolkt, moet de volgende server worden geregistreerd. [Meer informatie](../../installation/using/deploying-an-instance.md#saving-tracking)

## Berichten tracken {#message-tracking}

<img src="assets/do-not-localize/icon-message-tracking.svg" width="60px">

**Getraceerde verbindingen**

U kunt de ontvangst van berichten en de activering van de verbindingen volgen die in de berichtinhoud worden opgenomen om het gedrag van ontvangers beter te begrijpen. [Meer informatie](how-to-configure-tracked-links.md)

**URL het volgen**

Traceringsopties kunnen worden geconfigureerd door bijgehouden URL&#39;s te activeren of deactiveren. [Meer informatie](personalizing-url-tracking.md)

**Getraceerde verbinding verpersoonlijking**

Met de trackingsmogelijkheden van Campaign Classic kunt u koppelingen toevoegen in e-mailberichten die kunnen worden aangepast en die het bijhouden van wijzigingen ondersteunen. [Meer informatie](tracking-personalized-links.md)

**het Volgen logboeken**

Met de technische workflow voor bijhouden worden de gegevens voor bijhouden opgehaald nadat de levering is verzonden en de tekstspatiëring is geactiveerd. Deze gegevens vindt u op het tabblad Bijhouden van de levering. [Meer informatie](accessing-the-tracking-logs.md)

**Tracking van tests**

Voordat u de berichten verzendt met het bijhouden van de berichten, kunt u het bijhouden van de berichten testen op de spiegel-, e-maillogboeken en koppelingen. [Meer informatie](testing-tracking.md)

## Webtoepassing bijhouden {#web-application-tracking}

<img src="assets/do-not-localize/icon-web-app.svg" width="60px">

**Een webapplicatie opvolgen**

U kunt bezoeken op de toepassingspagina&#39;s van het Web met het volgen markeringen ook volgen en meten. Deze functionaliteit kan voor alle toepassingstypes van het Web zoals vormen en landende pagina&#39;s worden gebruikt. [Meer informatie](../../web/using/tracking-a-web-application.md)

**Opt-out voor tracking van een webapplicatie**

Met de optie Web application tracking kunt u het webgedrag van eindgebruikers die zich afmelden voor het volgen van gedragingen, niet meer volgen. U kunt de mogelijkheid opnemen om een banner weer te geven in webtoepassingen of om pagina&#39;s te landen, zodat gebruikers zich kunnen afmelden. [Meer informatie](../../web/using/web-application-tracking-opt-out.md)

## Rapporten bijhouden {#tracking-reports}

<img src="assets/do-not-localize/icon_monitor.svg" width="60px">

**het Volgen statistieken**

Dit rapport bevat statistieken over openen, klikken en transacties en geeft u inzicht in de marketingeffecten van de levering. [Meer informatie](../../reporting/using/delivery-reports.md#tracking-statistics)

**URL&#39;s en klikpaden**

Dit rapport bevat de lijst met bezochte pagina&#39;s na een levering. [Meer informatie](../../reporting/using/delivery-reports.md#urls-and-click-streams)

**Persoon/personen en ontvangers**

Met dit voorbeeld kunt u beter het verschil zien dat personen en ontvangers in Adobe Campaign kunnen bijhouden. [Meer informatie](../../reporting/using/person-people-recipients.md)

**Trackingsindicatoren**

Dit rapport combineert de belangrijkste indicatoren voor het volgen van het gedrag van ontvangers bij het ontvangen van de levering zoals open, klikthrough tarieven en klikstromen. [Meer informatie](../../reporting/using/delivery-reports.md#tracking-indicators)

**Indicatoren berekenen**

De verschillende tabellen geven u de lijst van indicatoren die in de verschillende rapporten worden gebruikt en hun berekeningsformule afhankelijk van het leveringstype. [Meer informatie](../../reporting/using/indicator-calculation.md)

## Problemen met tracking oplossen {#tracking-troubleshooting}

<img src="assets/do-not-localize/icon-troubleshooting.svg" width="60px">

De volgende tips voor het oplossen van problemen helpen u de meest voorkomende problemen op te lossen die zich voordoen bij het gebruik van tracking in Adobe Campaign Classic. Voor een geavanceerdere het oplossen van problemen, verwijs naar [ deze sectie ](tracking-troubleshooting.md).

* Controleren of het trackinglogproces wordt uitgevoerd

  Dit proces leest van het gedeelde geheugen IIS/de Server van het Web en schrijft de redirection logboeken.

  U kunt het van de Homepage tot toegang hebben door het lusje van de Controle in uw geval te selecteren. U kunt ook de volgende opdracht op de instantie uitvoeren: `<user>@<instance>:~$ nlserver pdump`

  Als het trackinglogd-proces niet in de lijst wordt weergegeven, start u het proces met de volgende opdracht in de lijst: `<user>@<instance>:~$ nlserver start trackinglogd`

* Controleer of de technische workflow voor bijhouden de laatste tijd is uitgevoerd.

  U vindt de technische workflow voor bijhouden in de mappen Beheer > Productie > Technische workflows.
