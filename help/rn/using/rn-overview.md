---
product: campaign
title: Aan de slag met upgrades
description: Meer informatie over Campaign Classic-upgrades
feature: Release Notes
role: User
level: Beginner
exl-id: 7a05fdff-8f9d-4e8d-812e-0f1509db5499
source-git-commit: d56038fc8baf766667d89bb73747c20ec041124c
workflow-type: ht
source-wordcount: '894'
ht-degree: 100%

---

# Release-updates {#rn-overview}

Adobe Campaign Classic brengt regelmatig productupdates uit die nieuwe mogelijkheden, foutoplossingen, en betere prestaties, veiligheid, en bruikbaarheid brengen. Deze updates worden uitgebracht als **productbuilds**. Gedetailleerde informatie over elke nieuwe build is beschikbaar in het dialoogvenster [Aanvullende informatie](latest-release.md).

<!--
## Product versions

For Campaign, the version naming is the following:

1. Campaign Major version are v7 and v8.
1. A Minor version is a sub-version of a Major version. For example: v7.3, v7.4.
1. A Patch version is a post-release fix. For example: v7.3.2, v7.3.3.


Aligned with this naming, Campaign has 3 types of upgrades:

1. Major Upgrades - A major upgrade is an upgrade to a new version of Adobe Campaign (ex: v7 to v8)
1. Minor Upgrades - A minor upgrade brings new features, enhancements and fixes (ex: 7.4.X to 7.5.X)
1. Patch Upgrades - A patch upgrade includes fixes only (ex: 8.5.1 to 8.5.2)
-->

## Releasestatussen {#rn-statuses}

Elke nieuwe build wordt geleverd met een status die wordt bepaald door een kleur in het dialoogvenster [Aanvullende informatie](latest-release.md).

| Status | Beschrijving |
|---|---|
| [!BADGE Algemene beschikbaarheid]{type=Positive} | Nieuwste stabiele build, gevalideerd in productie en aanbevolen door Adobe. |
| [!BADGE Beperkte beschikbaarheid]{type=Informative} | alleen on-demand implementatie. |
| [!BADGE Afgeschaft]{type=negative} | Geen implementatie. Geen foutopsporing. Bestaande implementaties moeten worden bijgewerkt. |

## Releasecyclus {#rn-cycle}

Adobe Campaign wordt regelmatig bijgewerkt. Deze regelmatige frequentie van updates is bedoeld om u het nieuwste en beste in handen te geven, uw omgeving veilig te houden en uw ervaring met ons product te verbeteren.

Dit is de reden waarom het essentieel is dat u **de meest recente stabiele build** van Adobe Campaign gebruikt. U krijgt dan ook een betere ondersteuningservaring, aangezien het identificeren, reproduceren en oplossen van een probleem met een recente versie meestal veel sneller gaat. Bovendien zijn veel problemen die u kunt tegenkomen, in de meest recente builds al opgelost.

Als gehoste klant profiteert u automatisch van de upgrade met de nieuwste stabiele build zonder enige actie. Lees meer in het [gedeelte Jaarlijkse upgrade](#yearly-upgrade). Als u migreert van een oude build, raadt Adobe u aan eerst naar deze build te upgraden.

## Aanbevelingen {#rn-recommendations}

Voor een stabiele configuratie raadt Adobe aan om **dezelfde build** te installeren op alle servers die op dezelfde clientconfiguratie worden uitgevoerd.

Bovendien, tenzij anders vermeld in de [Aanvullende informatie](latest-release.md), moet de clientconsole zich in **dezelfde build** bevinden als de serverinstantie.

Houd uw implementatie up-to-date door de pagina’s [Verouderde en verwijderde functies](../../rn/using/deprecated-features.md) en [Compatibiliteitsmatrix](../../rn/using/compatibility-matrix.md) te lezen bij elke nieuwe release.

## Upgradeproces{#process-upgrade}

Als gehoste klant (Managed Service of hybride) moet u contact opnemen met de Adobe-klantenservice om uw omgeving te laten upgraden.

Als on-premise gebruiker kunt u de upgrade zelf uitvoeren. Hiervoor moet u de [nieuwste stabiele build (GA) downloaden](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) en al uw omgevingen upgraden.

Lees meer over het [upgradeproces](../../production/using/build-upgrade.md) en raadpleeg de [veelgestelde vragen over build-upgrades](../../platform/using/faq-build-upgrade.md).

## Jaarlijkse upgrade {#yearly-upgrade}

Adobe wil u met onze softwareoplossing(en) de beste ervaring en waarde bieden. De organisatie doet er alles aan om ervoor te zorgen dat u toegang hebt tot de nieuwste versies van gerelateerde technologie die onze oplossingen gebruiken om taken uit te voeren.

Adobe Campaign Classic gebruikt met name een scala aan technologische oplossingen om waarde te creëren. Deze combinatie van technologieën vereist dat u uw Campaign Classic-instantie(s) regelmatig bijwerkt, zodat de meest actuele versies worden gebruikt voor betere beveiliging, stabiliteit en prestaties.

Als gehoste gebruiker profiteert u automatisch van de upgrade met de nieuwste GA-build zonder enige actie te hoeven ondernemen. Meer informatie vindt u in de volgende veelgestelde vragen.

### Waarom heeft mijn organisatie deze upgrade nodig?

Als u een gehoste klant bent en als er wordt vastgesteld dat uw account voor een of meer van de technologieën met betrekking tot Campaign Classic moet worden bijgewerkt en uw infrastructuur moet worden bijgewerkt naar de huidige build (bijvoorbeeld van v7.2.1 naar v7.3.3) en/of versie (van v7 naar v8), stelt Adobe u rechtstreeks op de hoogte.

Adobe raadt on-premise of hybride klanten die een oudere build gebruiken, aan om over te stappen naar de nieuwste stabiele build (GA).

Zo wordt uw account beschermd tegen kwetsbaarheden en gebruikt u de nieuwste prestatietechnologie. Met deze upgrade komt uw account in de toekomst ook in aanmerking voor eenvoudige, regelmatige upgrades die minder handmatig werk en tussenkomst vereisen.

### Wat zijn de procedure en de tijdlijn voor deze upgrade?

Het team van Adobe begeleidt uw organisatie tijdens dit traject.

Een speciaal team van klantenservicemedewerkers, productmanagers, engineers, technische specialisten en productconsultants biedt u ondersteuning en zorgt voor een probleemloze ervaring.

### Voordelen

<tr>
  <td>
      <img alt="Beveiliging" src="assets/do-not-localize/security.png"/>
    <div>
    <strong>Verbeterde beveiliging</strong>
    </div>
    <ul>
    <li>De verschillende technologieën van Adobe Campaign Classic werken samen om waarde te bieden.</li>
    <li>Al uw instanties moeten worden bijgewerkt om de beveiliging te optimaliseren.</li>
    <li>De beveiliging vereist een constante focus en proactief onderhoud. </li>
    <li>Beveiligingsrisico's zijn overal en kunnen niet worden genegeerd: elke upgrade voor Campaign Classic verbetert de beveiliging.</li>
    </ul>
  </td>

<td>
      <img alt="Ondersteuning" src="assets/do-not-localize/support.png" />
    <div>
    <strong>Verbeterde ondersteuning</strong>
    </div>
    <ul>
    <li>De meeste kritieke problemen worden gewoon opgelost met upgrades en kunnen worden vermeden.</li>
    <li>Met regelmatige upgrades loopt u tegen minder problemen aan waardoor u ook de efficiëntie verbetert.</li>
    <li>De klantenservice wordt minder belast waardoor we sneller kunnen reageren en meer aandacht kunnen besteden aan problemen die geen verband houden met upgrades.</li>
    </ul>
  </td>
</tr>

<tr>
  <td>
      <img alt="Onderhoud" src="assets/do-not-localize/maintenance.png"/>
    <div>
    <strong>Verbeterd onderhoud en verbeterde stabiliteit</strong>
    </div>
    <ul>
    <li>In de loop der tijd identificeert het Adobe Campaign-team manieren om de stabiliteit en de prestaties van het product te verbeteren en bekende problemen op te lossen.</li>
    <li>Door uw instantie te upgraden krijgt u deze nieuwste verbeteringen. U voorkomt zo bovendien veelvoorkomende problemen binnen organisaties die een snelle groei doormaken en/of tegen moeilijkheden aanlopen in hun Campaign Classic-instanties.</li>
    <li>De verbeteringen in de technologie achter Campaign Classic zullen zowel bij de marketing- als IT-teams binnen uw organisatie merkbaar zijn.</li>
    </ul>
  </td>

<td>
      <img alt="Buildupgrade" src="assets/do-not-localize/upgrades.png" />
    <div>
    <strong>Eenvoudigere upgrades</strong>
    </a>
    </div>
    <ul>
    <li>Hoe groter het verschil tussen twee versies, hoe complexer het is om uw Campaign Classic-instantie bij te werken.</li>
    <li>Hoe langer uw organisatie wacht, des te complexer de upgrade wordt (en hoe kwetsbaarder u bent voor beveiligingsrisico's).</li>
    <li>Regelmatige updates verminderen de downtime tijdens upgrades en het risico op regressie.</li>
    </ul>
  </td>
</tr>
</table>

## Aanvullende bronnen{#support}

* [Uw Campaign-versie zoeken](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).
* [Help en ondersteuning](../../support.md)
* [Configuratiescherm-releases](https://experienceleague.adobe.com/docs/control-panel/using/release-notes.html?lang=nl)
* [Afgeschafte en verwijderde functies](../../rn/using/deprecated-features.md)
* [Veelgestelde vragen over buildupgrades](../../platform/using/faq-build-upgrade.md)

Word lid van de [Adobe Priority Product Update](https://www.adobe.com/nl/subscription/priority-product-update.html) om op de hoogte te blijven van nieuwe releases van Experience Cloud-oplossingen.
