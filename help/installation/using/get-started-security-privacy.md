---
solution: Campaign Classic
product: campaign
title: Aan de slag met beveiliging en privacy
description: Meer informatie over de belangrijkste elementen die gecontroleerd moeten worden met betrekking tot beveiliging en privacy.
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
translation-type: tm+mt
source-git-commit: 922603492d2c98d751683d3aa481e9ab19bca70c
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 3%

---


# Aan de slag met beveiliging en privacy {#get-started-security-privacy}

Deze sectie zal u aan de belangrijkste elementen introduceren om betreffende veiligheid en privacy te controleren. Sommige configuraties kunnen slechts door on-premise klanten worden uitgevoerd.

## Privacy

<img src="assets/do-not-localize/icon_privacy.svg" width="60px">

De configuratie van de privacy en het verharden is een zeer belangrijk element van veiligheidsoptimalisering. Hier volgen enkele aanbevolen procedures voor privacy:

* Protect uw klant PII door HTTPS in plaats van HTTP te gebruiken
* Gebruik PII-weergavebeperking om de privacy te beschermen en misbruik van gegevens te voorkomen.
* Controleer of gecodeerde wachtwoorden beperkt zijn.
* Protect de pagina&#39;s die persoonlijke gegevens kunnen bevatten, zoals spiegelpagina&#39;s, webtoepassingen, enz.

[Meer informatie](../../installation/using/privacy.md)

## Toegangscontrole

<img src="assets/do-not-localize/icon_access.svg" width="60px">

Toegangsbeheer is een belangrijk onderdeel van de beveiliging. Hier volgen enkele van de belangrijkste aanbevolen procedures:

* Maak genoeg beveiligingsgroepen
* Controleren of elke operator de juiste toegangsrechten heeft
* Vermijd het gebruik van de beheeroperator en vermijd het gebruik van te veel operatoren in de beheergroep

[Meer informatie](../../installation/using/access-management.md)

## Richtlijnen voor scripts en codering

<img src="assets/do-not-localize/icon_scripting.svg" width="60px">

Volg bij het ontwikkelen in Adobe Campaign (workflows, Javascript, JSSP, enz.) altijd de volgende richtlijnen:

* **Scripting**: Probeer SQL-instructies te vermijden, gebruik parameterized functies in plaats van tekenreekssamenvoeging en vermijd SQL-injectie door de SQL-functies toe te voegen die u aan de lijst van gewenste personen wilt gebruiken.

* **Beveilig het gegevensmodel**: gebruik genoemde rechten om exploitatoracties te beperken, systeemfilters toe te voegen (sysFilter)

* **Hoofdletters toevoegen in webtoepassingen**: Leer hoe u hoofdletters kunt toevoegen aan uw openbare bestemmingspagina&#39;s en abonnementspagina&#39;s.

[Meer informatie](../../installation/using/scripting-coding-guidelines.md)

## Netwerk, database en SSL/TLS

<img src="assets/do-not-localize/icon_network.svg" width="60px">

Een zeer belangrijk ding om te controleren wanneer het opstellen van een on-premise type van architectuur is de voorzien van een netwerkconfiguratie.

Het is ook noodzakelijk dat u de beveiliging van de database-engine volgt.

[Meer informatie](../../installation/using/network-database.md)

## Serverconfiguratie

<img src="assets/do-not-localize/icon_server.svg" width="60px">

De configuratie moet op alle servers worden uitgevoerd. De configuratiebestanden zijn van het type **serverConf.xml** en **`config-<instance>.xml`**. Hier volgen de belangrijkste elementen die moeten worden gecontroleerd:

* **Beveiligingszones**: Vorm veiligheidsstreken zodat zij direct met de IP adressen van cliënten van een volmacht rekening houden.

* **Beveiliging** bestandsupload: beperkt de typen bestanden die naar de Adobe Campaign-server kunnen worden geüpload met een nieuw kenmerk uploadAllowList. Dit kan in het dossier van de serverconfiguratie worden gebruikt.

* **Relay**: verbeter de relaisconfiguratie door de relaisregels voor ongebruikte modules/toepassingen te deactiveren.

* **Uitgaande** bescherming van de verbinding en  **Bevel beperking**  (server-kant)

* U kunt ook extra HTTP-headers toevoegen, checkIPConsistent activeren, TLS inschakelen, sessionTimeOutSec, enzovoort. Raadpleeg de [documentatie bij de configuratie van de campagneserver](../../installation/using/configuring-campaign-server.md) en de [beschrijving van het serverconfiguratiebestand](../../installation/using/the-server-configuration-file.md) voor meer informatie.

[Meer informatie](../../installation/using/server-configuration.md)

## Webserverconfiguratie

<img src="assets/do-not-localize/icon_web.svg" width="60px">

Bij het configureren van uw webserver (Apache/IIS) moeten verschillende best practices worden gevolgd:

* Oude SSL-versie en -ciphers uitschakelen
* De methode TRACE verwijderen
* De banner verwijderen
* De vraaggrootte beperken om belangrijke dossiers te verhinderen worden geupload

[Meer informatie](../../installation/using/web-server-configuration.md)