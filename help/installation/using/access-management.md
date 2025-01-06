---
product: campaign
title: Toegangsbeheer
description: Meer informatie over best practices voor toegangsbeheer
feature: Installation, Access Management, Permissions
exl-id: af88e4e7-0ee3-48b4-9db4-7dd390d9d46a
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 8%

---

# Toegangsbeheer {#access-management}



## Webapp-operator

De webApp-operator is een beheerder. Om de veiligheid te verbeteren, volg deze richtlijnen:

* Vervang de beheerder die aan de rechterkant van deze operator is benoemd door een nieuwe beheerder (kan de naam &#39;webapp&#39; hebben). Raadpleeg [deze sectie](../../platform/using/access-management.md) voor meer informatie.

* Voeg de webApp-operator toe in mappen (hoofdzakelijk mappen voor ontvangers) om lees- en schrijftoegang te verlenen aan ontvangers. Raadpleeg [deze pagina](../../platform/using/access-management.md) voor meer informatie.

* Als u een instantie van meerdere merken (of meerdere geo&#39;s) gebruikt, kunt u de toegang tot webtoepassingen splitsen naar verschillende mappen voor ontvangers. Dit doet u als volgt:

   1. De webApp-operator dupliceren

   1. Voer een naam in voor elk duplicaat. Bijvoorbeeld: webapp_brand, webapp_brand2, enz.

   1. Dupliceer een sjabloon van een webtoepassing om één sjabloon per merk te hebben en bewerk de eigenschappen om de operator te wijzigen door Een specifiek account gebruiken te selecteren.  Meer informatie vindt u [op deze pagina](../../web/using/defining-web-forms-properties.md).

## Beveiligingsgroepen en beheerders

Maak genoeg beveiligingsgroepen om uw operatoren de juiste rechten te geven, zodat ze kunnen doen wat ze nodig hebben, en niet meer.

Gebruik de beheeroperator niet (of deel deze niet). Creeer één exploitant per fysieke gebruiker (om een nauwkeurige controle/registreren te hebben). Voeg de nieuwe beheerders toe aan de beheerdersgroep. Als u de beheerder niet gebruikt, verwijder het niet, en maak het niet onbruikbaar: deze exploitant wordt intern gebruikt om verwerking uit te voeren. Maar u kunt zijn [ toegang tot de cliëntconsole ](../../platform/using/access-management.md) verbieden en zijn veiligheidsstreek (aan localhost) beperken.

Voeg niet te veel operatoren toe aan de beheergroep (of met benoemde beheerdersrechten). Het zijn zeer krachtige operatoren (ze kunnen alle SQL-instructies uitvoeren, opdrachten op de server uitvoeren, enz.).

Adobe Campaign verstrekt drie voorrechten op hoog niveau door [ genoemde rechten ](../../platform/using/access-management.md#named-rights):

* **BEHEER** (admin): geeft toegang tot alles en staat toe om alles te doen, die alle genoemde juiste controles omzeilt, zodat omvat het de UITVOERING VAN HET PROGRAMMA (createProcess) en SQL genoemde rechten

* **UITVOERING VAN HET PROGRAMMA** (createProcess): staat het uitvoeren van externe programma&#39;s (op de server) toe

* **SQL**: staat het runnen van SQL manuscripten op het gegevensbestand (zodat kan het veiligheidsmodel overslaan). Nota: als u complexe berekeningen (het filtreren, bijvoorbeeld) moet uitvoeren, kunt u uw gegevensbestandbeheerder vragen om een SQL functie tot stand te brengen en hen toe te voegen aan de lijst van gewenste personen. Meer informatie vindt u [op deze pagina](../../installation/using/scripting-coding-guidelines.md).

* **Verleen hen aan zeer weinig (en vertrouwde op) exploitanten**
