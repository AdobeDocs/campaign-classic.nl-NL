---
product: campaign
title: Controlelijst voor beveiliging en privacy
description: Meer informatie over de belangrijkste elementen die gecontroleerd moeten worden op het gebied van beveiliging en privacy
feature: Installation, Privacy, Access Management, Privacy Tools
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: ec40498e-e673-4792-8dcf-8bb7e852b532
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 7%

---

# Controlelijst voor beveiliging en privacy{#get-started-security-privacy}



Deze sectie zal u aan de belangrijkste elementen introduceren om betreffende veiligheid en privacy te controleren. Sommige configuraties kunnen slechts door on-premise klanten worden uitgevoerd.

## Privacy

<img src="assets/do-not-localize/icon_privacy.svg" width="60px">

De configuratie van de privacy en het verharden is een zeer belangrijk element van veiligheidsoptimalisering. Hier volgen enkele aanbevolen procedures voor privacy:

* Protect uw klant PII door HTTPS in plaats van HTTP te gebruiken
* Gebruik PII-weergavebeperking om de privacy te beschermen en misbruik van gegevens te voorkomen.
* Controleer of gecodeerde wachtwoorden beperkt zijn.
* Protect de pagina&#39;s die persoonlijke gegevens kunnen bevatten, zoals spiegelpagina&#39;s, webtoepassingen, enz.

[Meer informatie](../../installation/using/privacy.md)

## Toegangsbeheer

<img src="assets/do-not-localize/icon_access.svg" width="60px">

Toegangsbeheer is een belangrijk onderdeel van de beveiliging. Hier volgen enkele van de belangrijkste aanbevolen procedures:

* Maak genoeg beveiligingsgroepen
* Controleren of elke operator de juiste toegangsrechten heeft
* Vermijd het gebruik van de beheeroperator en vermijd het gebruik van te veel operatoren in de beheergroep

[Meer informatie](../../installation/using/access-management.md)

## Richtlijnen voor scripting en versleuteling

<img src="assets/do-not-localize/icon_scripting.svg" width="60px">

Volg bij het ontwikkelen in Adobe Campaign (workflows, Javascript, JSSP, enz.) altijd de volgende richtlijnen:

* **Scripting**: probeer om SQL verklaringen te vermijden, gebruik geparameterized functies in plaats van koordaaneenschakeling, vermijd SQL injectie door de SQL functies toe te voegen aan de lijst van gewenste personen te gebruiken.

* **beveilig het gegevensmodel**: gebruik genoemde rechten om exploitantacties te beperken, systeemfilters (sysFilter) toe te voegen

* **voegt kapitalen in Webtoepassingen** toe: leer hoe te om kapitalen in uw openbare het landen pagina&#39;s en abonnementspagina&#39;s toe te voegen.

[Meer informatie](../../installation/using/scripting-coding-guidelines.md)

## Netwerk, database en SSL/TLS

<img src="assets/do-not-localize/icon_network.svg" width="60px">

Een zeer belangrijk ding om te controleren wanneer het opstellen van een on-premise type van architectuur is de voorzien van een netwerkconfiguratie.

Het is ook noodzakelijk dat u de beveiliging van de database-engine volgt.

[Meer informatie](../../installation/using/network-database.md)


## Serverconfiguratie

<img src="assets/do-not-localize/icon_server.svg" width="60px">

De configuratie moet op alle servers worden uitgevoerd. De configuratiedossiers zijn van het type **serverConf.xml** en **`config-<instance>.xml`**. Hier volgen de belangrijkste elementen die moeten worden gecontroleerd:

* **de streken van de Veiligheid**: Vorm veiligheidsstreken zodat zij direct met de IP adressen van cliënten van een volmacht rekening houden.

* **het uploadt van het Dossier bescherming**: beperkt de types van dossiers die aan de server van Adobe Campaign kunnen worden geupload gebruikend een nieuw uploadAllowList attribuut. Dit kan in het dossier van de serverconfiguratie worden gebruikt.

* **Verhouding**: verbeter de relaisconfiguratie door de relaisregels voor ongebruikte modules/toepassingen te deactiveren.

* **Uitgaande verbindingsbescherming** en **beperking van het Bevel** (server-kant)

* U kunt ook extra HTTP-headers toevoegen, checkIPConsistent activeren, TLS inschakelen, sessionTimeOutSec, enzovoort. Verwijs naar de [ documentatie van de de serverconfiguratie van de Campagne ](../../installation/using/configuring-campaign-server.md) en de [ beschrijving van het de configuratiedossier van de Server ](../../installation/using/the-server-configuration-file.md) voor meer informatie.

[Meer informatie](../../installation/using/server-configuration.md)

## Webserverconfiguratie

<img src="assets/do-not-localize/icon_web.svg" width="60px">

Bij het configureren van uw webserver (Apache/IIS) moeten verschillende best practices worden gevolgd:

* Oude SSL-versie en -ciphers uitschakelen
* De methode TRACE verwijderen
* De banner verwijderen
* De vraaggrootte beperken om belangrijke dossiers te verhinderen worden geupload

[Meer informatie](../../installation/using/web-server-configuration.md)
