---
product: campaign
title: Problemen met prestaties en doorvoer
description: Problemen met prestaties en doorvoer
feature: Monitoring
badge-v7-prem: label="Alleen op locatie/hybride" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=nl" tooltip="Alleen van toepassing op on-premise en hybride implementaties"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: fe69efda-a052-4f67-9c13-665f011d0a2b
source-git-commit: 8b38d825aa9b0595226a444e0e463362468d51b3
workflow-type: tm+mt
source-wordcount: '738'
ht-degree: 2%

---

# Problemen met prestaties en doorvoer{#performance-and-throughput-issues}

Eerst en vooral, zou u moeten controleren dat u de recentste bouwstijl hebt geïnstalleerd. Dit zorgt ervoor dat u de recentste eigenschappen en insectenmoeilijke situaties hebt.

Verwijs naar de [&#x200B; Nota&#39;s van de Versie &#x200B;](../../rn/using/latest-release.md) voor meer informatie over de inhoud van elke versie.

## Hardware en infrastructuur {#hardware-and-infrastructure}

De algemene richtlijnen voor hardwarevereisten voor op-gebouw Campaign Classic zijn gedetailleerd op deze [&#x200B; pagina &#x200B;](https://helpx.adobe.com/nl/campaign/kb/hardware-sizing-guide.html).

Het raadplegende team kan ontvangen klanten een hulpmiddel verstrekken dat u toestaat om gemakkelijk te bekijken hoeveel ruimte door diverse types van lijsten in het gegevensbestand evenals de ruimte wordt gebruikt die op de plaats SFTP wordt gebruikt. Daarnaast beschikt de toepassing over gereedschappen waarmee u overbodige gegevens kunt opschonen. De Zorg van de Klant van het contact [&#x200B; Adobe &#x200B;](https://helpx.adobe.com/nl/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) als u dit hulpmiddel uitvoerde nodig hebt. Hier volgen enkele belangrijke zaken die u met dit gereedschap kunt controleren:

* Als de indexgrootte groter is dan de tabelgrootte, is een vacuüm vereist.
* Controleer de tabellen die het maximale bloat hebben. Als deze tabellen vaak worden gebruikt, moeten ze worden opgevuld.
* Door databaseblokkering kunnen e-mails niet meer worden verzonden.

Adobe Campaign verstrekt ook a [&#x200B; hulpmiddel &#x200B;](../../production/using/monitoring-processes.md#manual-monitoring) om het gebruik van CPU en van RAM te controleren. Gebruik dit hulpmiddel en bekijk specifieke indicatoren zoals: **Geheugen**, **Geheugen van de Wisselen**, **Schijf**, **Actieve Processen**. Als de waarden te hoog zijn, kunt u proberen het aantal werkstromen te verminderen of werkschema&#39;s plannen om op verschillende tijden te beginnen.

## Databasecontrole {#database-performances}

Meestal zijn prestatieproblemen gekoppeld aan databaseonderhoud. Hier volgen de belangrijkste onderdelen:

* Configuratie: we raden u aan de eerste configuratie van het Adobe Campaign-platform te controleren en een volledige hardwarecontrole uit te voeren.
* Installatie en configuratie van het Adobe Campaign-platform: controleer de configuratie van het netwerk en de opties voor het leveren van het platform.
* Het onderhoud van het gegevensbestand: zorg ervoor dat de taak van de gegevensbestandschoonmaakbeurt operationeel is en dat het gegevensbestandonderhoud correct gepland en uitgevoerd is. Controleer het aantal en de grootte van werktabellen.
* In real time diagnose: controleer het proces en de dossiers van het platformlogboek, controleer dan gegevensbestandactiviteit terwijl het ontspannen van de kwestie.

>[!NOTE]
>
>Voor meer informatie, verwijs naar deze sectie: [&#x200B; prestaties van het Gegevensbestand &#x200B;](../../production/using/database-performances.md).

## Toepassingsconfiguratie {#application-configuration}

Hier volgt een lijst met artikelen die betrekking hebben op de aanbevolen werkwijzen voor toepassingsconfiguratie:

* MTA en MTAChild processen en geheugen: de **mta** module verspreidt berichten aan zijn **mtachild** kindmodules. Elk **mtachild** bereidt berichten voor alvorens om een vergunning van de statistiekserver te verzoeken, en hen te verzenden. Verwijs naar deze [&#x200B; pagina &#x200B;](../../installation/using/email-deliverability.md) voor meer informatie.
* TLS-configuratie: het wereldwijd inschakelen van TLS wordt afgeraden omdat dit de doorvoer kan verminderen. In plaats daarvan moeten de TLS-instellingen per domein, beheerd door het leveringsteam, worden afgestemd op de behoeften. Verwijs naar deze [&#x200B; pagina &#x200B;](../../installation/using/email-deliverability.md#mx-configuration) voor meer informatie.

  >[!NOTE]
  >
  >De betrokkenheid van het leveringsteam is gebaseerd op een contract en klanten moeten contact opnemen met hun Adobe-vertegenwoordiger voor informatie over de leveringsservice.

* DKIM: om het beveiligingsniveau van de DKIM te garanderen, is 1024b de aanbevolen beste manier om de coderingsgrootte te bepalen. De lagere sleutels van DKIM zullen niet als geldig door de meerderheid van toegangsleveranciers worden beschouwd. Zie [deze pagina](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#authentication).

## Leverbaarheidsproblemen {#deliverability-issues}

Hier volgt een lijst met best practices en artikelen met betrekking tot de te leveren items:

* IP reputatie: als de IP reputatie niet goed genoeg is, zal er een effect op prestaties zijn. De **module van de Controle van de Levering** biedt diverse hulpmiddelen aan om de leverbaarheidsprestaties van uw platform te volgen. Verwijs naar deze [&#x200B; pagina &#x200B;](../../delivery/using/about-delivery-monitoring.md#deliverability-monitoring).
* IP opwarmen: IP opwarmen wordt uitgevoerd door het leverbaarheidsteam. Dit houdt in dat het aantal e-mails over een periode van een paar weken geleidelijk wordt verhoogd via nieuwe IP&#39;s.

  >[!NOTE]
  >
  >De betrokkenheid van het leveringsteam is gebaseerd op een contract en klanten moeten contact opnemen met hun Adobe-vertegenwoordiger voor informatie over de leveringsservice.

* IP affiniteitopstelling: een onjuiste IP affiniteitopstelling kan de e-mail volledig tegenhouden (onjuiste exploitant/affiniteitsnaam in configuratie) of de productie (klein aantal IPs in de affiniteit) verminderen. Verwijs naar deze [&#x200B; pagina &#x200B;](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use).
* E-mailformaat: e-mailgrootte speelt een belangrijke rol bij de doorvoer. De aanbevolen maximale e-mailgrootte is 60 kB. Verwijs naar deze [&#x200B; pagina &#x200B;](https://helpx.adobe.com/legal/product-descriptions/campaign.html). In het [&#x200B; rapport van de productie van de Levering &#x200B;](../../reporting/using/global-reports.md#delivery-throughput), controleer het aantal bytes die door uur worden overgebracht.
* Groot aantal ongeldige ontvangers: wanneer er een groot aantal ongeldige ontvangers is, kan dit van invloed zijn op de doorvoer. De MTA blijft het verzenden van e-mails naar ongeldige ontvangers opnieuw proberen. Controleer of de database goed wordt onderhouden.
* Hoeveelheid personalisatie: als een levering in &quot;Personalization in uitvoering&quot; blijft, controleert u de JavaScript die in verpersoonlijkingsblokken wordt gebruikt.

>[!NOTE]
>
>Zie ook de [&#x200B; sectie van de Leverbaarheid &#x200B;](../../delivery/using/about-deliverability.md). Voor een diepere duik op leverability, verwijs naar de [&#x200B; Gids van de Beste praktijken van de Levering van Adobe &#x200B;](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=nl).
