---
product: campaign
title: Toegangsbeheer
description: Meer informatie over best practices voor toegangsbeheer.
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: af88e4e7-0ee3-48b4-9db4-7dd390d9d46a
source-git-commit: e719c8c94f1c08c6601b3386ccd99d250c9e606b
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 5%

---

# Toegangsbeheer {#access-management}

![](../../assets/v7-only.svg)

## Webapp-operator

De webApp-operator is een beheerder. Om de veiligheid te verbeteren, volg deze richtlijnen:

* Vervang de beheerder die aan de rechterkant van deze operator is benoemd door een nieuwe beheerder (kan de naam &#39;webapp&#39; hebben). Raadpleeg [deze sectie](../../platform/using/access-management.md) voor meer informatie.

* Voeg de webApp-operator toe in mappen (hoofdzakelijk mappen voor ontvangers) om lees- en schrijftoegang te verlenen aan ontvangers. Raadpleeg [deze pagina](../../platform/using/access-management.md) voor meer informatie.

* Als u een instantie van meerdere merken (of meerdere geo&#39;s) gebruikt, kunt u de toegang tot webtoepassingen splitsen naar verschillende mappen voor ontvangers. Dit doet u als volgt:

   1. De webApp-operator dupliceren

   1. Voer een naam in voor elk duplicaat. Bijvoorbeeld: webapp_brand, webapp_brand2, enz.

   1. Dupliceer een sjabloon van een webtoepassing om één sjabloon per merk te hebben en bewerk de eigenschappen om de operator te wijzigen door Een specifiek account gebruiken te selecteren.  Meer informatie in [deze pagina](../../web/using/defining-web-forms-properties.md).

## Beveiligingsgroepen en beheerders

Maak genoeg beveiligingsgroepen om uw operatoren de juiste rechten te geven, zodat ze kunnen doen wat ze nodig hebben, en niet meer.

Gebruik de beheeroperator niet (of deel deze niet). Creeer één exploitant per fysieke gebruiker (om een nauwkeurige controle/registreren te hebben). Voeg de nieuwe beheerders toe aan de beheerdersgroep. Als u de beheerder niet gebruikt, verwijder het niet, en maak het niet onbruikbaar: deze operator wordt intern gebruikt om de verwerking uit te voeren. Maar je kunt het verbieden [toegang tot de clientconsole](../../platform/using/access-management.md) en de beveiligingszone beperken (tot localhost).

Voeg niet te veel operatoren toe aan de beheergroep (of met benoemde beheerdersrechten). Het zijn zeer krachtige operatoren (ze kunnen alle SQL-instructies uitvoeren, opdrachten op de server uitvoeren, enz.).

Adobe Campaign biedt via [benoemde rechten](../../platform/using/access-management.md#named-rights):

* **ADMINISTRATIE** (beheerder): geeft toegang tot alles en staat toe om alles te doen, die alle genoemde juiste controles omzeilt, zodat omvat het de UITVOERING VAN HET PROGRAMMA (createProcess) en SQL genoemde rechten

* **UITVOERING VAN PROGRAMMA** (createProcess): staat het uitvoeren van externe programma&#39;s (op de server) toe

* **SQL**: staat het runnen van SQL manuscripten op het gegevensbestand toe (zodat kan het veiligheidsmodel overslaan). Opmerking: als u complexe berekeningen (het filtreren, bijvoorbeeld) moet uitvoeren, kunt u uw gegevensbestandbeheerder vragen om een SQL functie tot stand te brengen en hen toe te voegen aan de lijst van gewenste personen. Meer informatie in [deze pagina](../../installation/using/scripting-coding-guidelines.md).

* **Geef ze door aan zeer weinig (en vertrouwde) operatoren**
