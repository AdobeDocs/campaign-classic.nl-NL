---
product: campaign
title: Veelgestelde vragen over Campaign Classic
description: Specifieke vragen over Adobe Campaign Classic v7-architectuur, -implementatie en -functies
feature: Overview, Troubleshooting
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
source-git-commit: 295e3596d9291cbcc55e2d264309141526c3806b
workflow-type: tm+mt
source-wordcount: '1527'
ht-degree: 1%

---

# Veelgestelde vragen over Campaign Classic v7 {#campaign-classic-v7-faq}

In deze veelgestelde vragen wordt ingegaan op specifieke vragen met betrekking tot Adobe Campaign Classic v7-architectuur, implementatiemodellen en v7-specifieke functies.

**voor uitvoerige antwoorden aan gemeenschappelijke vragen van de Campagne** (werkschema&#39;s, leveringen, publiek, het melden, verpersoonlijking, enz.), gelieve te verwijzen naar [**Uitgebreide FAQ van de Campagne v8** ](https://experienceleague.adobe.com/docs/campaign/campaign-v8/start/campaign-faq-comprehensive.html){target="_blank"}, die gedetailleerde antwoorden verstrekt die door onderwerp worden georganiseerd.

## Campaign Classic v7-architectuur en -implementatie {#v7-architecture}

### Welke hostmodellen zijn beschikbaar in Campaign Classic v7? {#what-are-the-hosting-models-available-in-campaign-classic-v7}

Adobe Campaign Classic v7 biedt drie implementatiemodellen:

* **Gehost (Managed Services)** - volledig beheerd door Adobe op de infrastructuur van Adobe
* **op-gebouw** - Geïnstalleerd en beheerd op uw eigen infrastructuur
* **Hybride** - Midden-sourcende architectuur met mengeling van wolk en on-premise componenten

Elk implementatiemodel heeft verschillende mogelijkheden en beheerverantwoordelijkheden. De beschikbaarheid van modules, opties, en configuraties hangt van uw plaatsingstype af.

[ klik hier om meer ](../../installation/using/hosting-models.md) over het ontvangen van modellen en hun verschillen te leren.

**Nota:** de Campagne v8 is uitsluitend beschikbaar als Beheerde Diensten van de Wolk. [ leer over Campagne v8 ](https://experienceleague.adobe.com/docs/campaign/campaign-v8/new/whats-new.html){target="_blank"}.

### Wat zijn de verschillen wanneer het werken op-gebouw tegenover in een ontvangen milieu? {#what-are-the-differences-when-working-on-premise-vs-in-a-hosted-environment}

Adobe Campaign Classic v7 wordt geleverd met een aantal modules en opties. De beschikbaarheid van deze modules en hun configuratie hangt van het [ type van plaatsing ](../../installation/using/hosting-models.md) van uw installatie af: ontvangen (Managed Services), hybride of op-gebouw.

Belangrijkste verschillen:

* **op-gebouw** - Volledige controle over installatie, infrastructuur, en configuratie. Vereist interne IT-middelen voor onderhoud, upgrades en beveiliging.
* **Gehost/Managed Services** - Infrastructuur en onderhoud die door Adobe wordt beheerd. Automatische upgrades en verbeterde beveiliging. Beperkte directe servertoegang.
* **Hybride** - combineert voordelen van beide modellen. Marketing-exemplaar gehost door Adobe, uitvoering/medio-sourcing afzonderlijk beheerd.

[ klik hier voor de volledige vermogensmatrijs ](../../installation/using/capability-matrix.md).

### Hoe migreer ik van op-gebouw/hybride naar Adobe Managed Services? {#how-do-i-migrate-from-on-premise-hybrid-to-adobe-managed-services}

Migratie naar Adobe Managed Services biedt verbeterde schaalbaarheid, beveiliging en lagere IT-overhead. Het is vaak een springplank voor de overgang naar Campaign v8.

**Zeer belangrijke punten:**

* Geen geautomatiseerd migratiehulpmiddel beschikbaar - handmatige planning en uitvoering vereist
* Adobe Professional Services-ondersteuning wordt sterk aanbevolen
* Tot de voordelen behoren cloudinfrastructuur, automatische beveiligingspatches, ondersteuning door experts en een eenvoudiger pad naar v8
* De migratie omvat zorgvuldigheid, milieucontrole, gegevenszuivering, werkgebiedmigratie en productiedruk

**Begonnen het worden:** contacteer uw vertegenwoordiger van Adobe om uw milieu te beoordelen en een gedetailleerd migratieplan met Adobe Professional Services te ontwikkelen.

Leer meer over [ migrerend aan Managed Services ](https://experienceleaguecommunities.adobe.com/t5/adobe-campaign-classic-blogs/migrate-your-adobe-campaign-v7-onprem-hybrid-environment-to/ba-p/681605){target="_blank"}.

## Upgrades voor build (Campaign Classic v7) {#build-upgrades-v7}

### Wat is een build-upgrade in Campaign Classic v7? {#what-is-a-build-upgrade-v7}

Een Build Upgrade is wanneer de Adobe Campaign Classic v7-software wordt bijgewerkt naar het nieuwste beveiligde buildnummer, maar blijft op hetzelfde grote/kleine buildniveau. Bijvoorbeeld: Campaign Classic v7 build 9026 to Campaign v7 build 9032.

Adobe Campaign wordt regelmatig bijgewerkt. Kleine versies worden vrijgegeven met nieuwe functies, verbeteringen en oplossingen. Daarnaast worden builds met cumulatieve correcties alleen periodiek vrijgegeven.

Leer meer [ in deze sectie ](../../rn/using/rn-overview.md).

### Hoe kan ik Campaign Classic v7 upgraden naar de nieuwste versie? {#how-can-i-upgrade-campaign-classic-v7}

Adobe Campaign Classic gebruikt een scala aan technologie om waarde te bieden. Deze combinatie van technologieën vereist dat u uw Campaign Classic v7-exemplaar(s) regelmatig upgradet om ervoor te zorgen dat de meest recente versies worden gebruikt voor superieure beveiliging, stabiliteit en prestaties.

**voor ontvangen klanten:** u profiteert automatisch van de jaarlijkse verbetering van de Campagne met de recentste stabiele versie. Adobe beheert het upgradeproces en coördineert de timing met u.

**voor op-gebouw/hybride klanten:** u bent verantwoordelijk voor het uitvoeren van verbeteringen. Adobe beveelt ten minste eenmaal per jaar een upgrade aan.

[ leest deze sectie ](../../production/using/build-upgrade.md) om te leren hoe te om uw milieu bij te werken en [ te lezen Veelgestelde vragen van de Verbetering van de Bouwstijl ](../../platform/using/faq-build-upgrade.md) voor gedetailleerde vragen over dit specifieke onderwerp.

### Wat is de nieuwste versie van Adobe Campaign Classic v7? {#what-is-the-latest-version-v7}

De recentste versie van Campaign Classic v7, met inbegrip van nieuwe eigenschappen en documentatie, is gedetailleerd in de recentste [ Nota&#39;s van de Versie ](../../rn/using/latest-release.md).

### Hoe weet ik welke versie van Campaign Classic v7 ik heb? {#how-do-i-know-which-version-v7}

Controleer uw versie en buildnummer via het menu **[!UICONTROL Help > About...]** in de Adobe Campaign Client Console. Het vak **[!UICONTROL About]** bevat gedetailleerde informatie over de versie en build die u uitvoert voor zowel de console als de server.

Leer meer [ in deze sectie ](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

### Is een bouwstijlverbetering het zelfde als een versieverbetering? {#is-build-upgrade-same-as-version-upgrade}

Nee. Een bouwstijlverbetering is een stijgende update binnen een bepaalde belangrijke versie, terwijl een versieverbetering een verandering van één belangrijke versie aan een andere is. De verbeteringen van de bouw zijn ongecompliceerd en typisch impliceren geen belangrijke architecturale, technische, of veranderingen van het gegevensmodel.

De verbeteringen van de versie (b.v., v7 aan v8) komen gewoonlijk met significante technische veranderingen en kunnen configuratieveranderingen of gedeeltelijke re-implementatie afhankelijk van uw aanpassingen vereisen.

## Campaign Classic v7-configuratie {#v7-configuration}

### Kan ik de taal van de Campaign Classic v7-interface wijzigen? {#can-i-change-language-v7}

De Campaign Classic v7-taal wordt geselecteerd wanneer u de instantie maakt. **u kunt niet het achteraf veranderen.**

De gebruikersinterface van Adobe Campaign v7 is beschikbaar in vier talen: Engels, Frans, Duits en Japans. De clientconsole en de server moeten in dezelfde taal zijn ingesteld. Elke Campaign Classic v7-instantie kan slechts in één taal worden uitgevoerd.

Voor het Engels kunt u bij de installatie van Campaign v7 Amerikaans Engels of Brits Engels selecteren: ze verschillen per datum- en tijdnotatie.

[ leer meer in deze sectie ](../../installation/using/creating-an-instance-and-logging-on.md).

**Nota:** het Web UI van de Campagne v8 staat gebruikers toe om hun interfacetaal onafhankelijk te veranderen. [Meer informatie](https://experienceleague.adobe.com/docs/campaign/campaign-v8/start/connect.html#language-pref){target="_blank"}.

### Hoe kan ik beveiligingszones configureren in Campaign Classic v7? {#how-can-i-configure-security-zones-v7}

De zelfbedieningsinterface van de Zones van de Veiligheid kan worden gebruikt om ingangen in de configuratie van de Zone van de Veiligheid van VPN van een plaatsing van Adobe Campaign Classic v7 te beheren. Dit is vooral relevant voor on-premise en hybride plaatsingen.

Lees [ deze sectie ](../../installation/using/security-zones.md) om over veiligheidsstreken in Campagne v7 te leren.

[ klik hier om meer ](https://helpx.adobe.com/nl/campaign/kb/configuring-security-zones-self-service.html){target="_blank"} over de zelfbediening UI van de Zone van de Veiligheid te leren.

**Nota:** Gehoste/klanten van Managed Services zouden Adobe moeten contacteren om veiligheidsstreken te vormen.

### Kan Adobe Campaign Classic v7 integreren met LDAP? {#can-campaign-classic-integrate-with-ldap}

Ja. Als **op-gebouw/hybride klant**, kunt u Campaign Classic v7 met uw folder integreren LDAP voor gecentraliseerde authentificatie en gebruikersbeheer.

Deze integratie maakt het mogelijk:

* Gebruikers die op basis van uw LDAP-directory moeten worden geverifieerd
* Gecentraliseerd gebruikers- en rechtenbeheer
* Automatische synchronisatie van gebruikersgroepen en machtigingen
* Single Sign-On-mogelijkheden

[ klik hier om te leren hoe ](../../installation/using/connecting-through-ldap.md) aan opstellingsLDAP integratie in Campaign Classic v7.

**Nota:** integratie LDAP is beschikbaar voor op-gebouw en hybride plaatsingen. Gehoste klanten gebruiken Adobe IMS voor verificatie.

### Wat zijn best practices voor beveiliging voor on-premise implementaties? {#security-best-practices-on-premise}

Voor on-premise en hybride implementaties zijn aanvullende beveiligingsconfiguratie en hardware nodig in vergelijking met gehoste omgevingen.

**Zeer belangrijke veiligheidsgebieden:**

* Netwerkbeveiliging en firewallconfiguratie
* Toegang tot en beveiliging van databases
* Besturingssysteem hardt
* Bestandsmachtigingen en toegangsbeheer
* Configuratie van beveiligingszones
* Versleuteling (gegevens in rust en in doorvoer)
* Toegangsbeheer van gebruikers
* Regelmatige beveiligingspatches
* Controle registreren en controleren

Lees de [ controlelijst van de Configuratie van de Veiligheid ](https://helpx.adobe.com/nl/campaign/kb/acc-security.html){target="_blank"} om zeer belangrijke elementen te ontdekken om betreffende veiligheidsconfiguratie en het verharden voor plaatsingen op-gebouw te controleren.

### Hoe kan ik de cache van de clientconsole wissen? {#how-do-i-clear-console-cache}

Als u het cachegeheugen van de Campagne-clientconsole wist, worden veel algemene problemen met weergave en functionaliteit opgelost. Het geheime voorgeheugen slaat lokale configuratiedossiers op die soms bedorven of verouderd kunnen worden.

**Wanneer om geheim voorgeheugen te ontruimen:**

* Nieuwe branding-elementen worden niet correct weergegeven
* Functies voor exporteren/importeren zijn onverwacht mislukt
* Interface-elementen die niet worden bijgewerkt na configuratiewijzigingen
* Prestatieproblemen of trage reactie op de console
* Na de upgrade naar een nieuwe versie van de clientconsole

**hoe te geheim voorgeheugen ontruimen:**

1. **Zacht Geheime voorgeheugen Duidelijk (probeer dit eerst):**
   * De clientconsole van de campagne openen
   * Ga naar het menu **[!UICONTROL File]**
   * Selecteren **[!UICONTROL Clear the local cache...]**
   * De handeling bevestigen wanneer hierom wordt gevraagd
   * De clientconsole opnieuw starten

2. **Ontruim van het Geheime voorgeheugen (als de zachte duidelijk niet de kwestie) oplost:**
   * Zachte cache wissen eerst uitvoeren
   * Afmelden en de clientconsole volledig sluiten
   * Navigeren naar:
      * Windows 7/10: `C:\Users\<Username>\AppData\Roaming\Neolane\NL_5\`
      * Windows XP: `C:\Documents and Settings\<Username>\Application Data\Neolane\NL_5\`
   * Alle XML-bestanden met de naam `nlclient-config-<alphanumerical value>.xml` en de bijbehorende mappen verwijderen
   * **Belangrijk:** schrapt `nlclient_cnx.xml` geen dossier
   * Client-console opnieuw starten

Leer meer in [ de documentatie van de cliëntconsole van de Campagne ](../../platform/using/launching-adobe-campaign.md).

## Help opvragen {#getting-help}

### Waar vind ik meer informatie over Campaign Classic v7? {#where-to-find-more-info-v7}

**Documentatie en middelen:**

* [ de Documentatie van Campaign Classic v7 ](https://experienceleague.adobe.com/docs/campaign-classic/using/campaign-classic-home.html?lang=nl){target="_blank"} - Volledige documentatie
* [ de Nota&#39;s van de Versie van Campaign Classic v7 ](../../rn/using/latest-release.md) - de recentste versieinformatie
* [ de Matrijs van de Verenigbaarheid van Campaign Classic ](../../rn/using/compatibility-matrix.md) - Ondersteunde systemen en versies
* [ Zelfstudies van Campaign Classic ](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=nl){target="_blank"} - Videozelfstudies

**voor gemeenschappelijke vragen van de Campagne:**

Gelieve te verwijzen naar [**Uitgebreide FAQ van de Campagne v8** ](https://experienceleague.adobe.com/docs/campaign/campaign-v8/start/campaign-faq-comprehensive.html){target="_blank"} die gedetailleerde antwoorden op verstrekt:

* Aan de slag met campagne
* Profielen en doelgroepen
* Ontwerp en levering van berichten
* Werkstromen en automatisering
* Rapportage en analyse
* Campagne-instellingen en configuratie
* Bronnen voor ontwikkelaars
* Privacy en naleving

**Gemeenschap en steun:**

* [ Forums van de Gemeenschap van de Campagne ](https://experienceleaguecommunities.adobe.com/t5/adobe-campaign-classic/ct-p/adobe-campaign-classic-community){target="_blank"}
* [ de Steun van Adobe ](https://helpx.adobe.com/nl/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html){target="_blank"}
* [ Controlebord (Gehoste klanten) ](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=nl){target="_blank"}

### Moet ik migreren van Campaign Classic v7 naar Campaign v8? {#should-i-migrate-to-v8}

Campagne v8 is een strategisch Adobe-platform dat ideaal is voor organisaties die grootschalige campagnes, moderne webinterface, voordelen in de cloud en ondersteuning op lange termijn nodig hebben. Campaign Classic v7 zal het einde van de steun in de komende jaren bereiken.

**overweegt migrerend aan Campagne v8 als u:**

* Grote gegevensvolumes verwerken of prestatieproblemen ervaren
* Wil IT-overhead en infrastructuurbeheer verminderen (v8 is alleen Managed Cloud Services)
* Moderne UI- en Adobe Experience Platform-integratie vereist
* Kies voor toekomstbestendige technologie met automatische updates
* Momenteel op ontvangen/beheerde diensten (gemakkelijkere migratieweg)

**Belangrijke overwegingen:**

* Campagne v8 is uitsluitend beschikbaar als Beheerde Cloud Services (geen opties op locatie/hybride)
* Vereist planning voor migratie van aanpassingen en integratie
* De FFDA-architectuur levert prestaties, maar vereist enige workflow-/API-aanpassingen

**Volgende stappen:** Contacteer uw vertegenwoordiger van Adobe om migratiebereidheid en toegangsmigratiehulpmiddelen te beoordelen.

Meer informatie:

* [ het Overzicht van de Campagne v8 ](https://experienceleague.adobe.com/docs/campaign/campaign-v8/new/whats-new.html){target="_blank"}
* [ Overgang van Campaign Classic v7 aan v8 ](https://experienceleague.adobe.com/docs/campaign/campaign-v8/start/v7-to-v8.html){target="_blank"}
* [ Campagne v8 Uitgebreide FAQ ](https://experienceleague.adobe.com/docs/campaign/campaign-v8/start/campaign-faq-comprehensive.html){target="_blank"}

**voor gedetailleerde antwoorden op gemeenschappelijke vragen van de Campagne over werkschema&#39;s, leveringen, publiek, het melden, verpersoonlijking, en meer**, bezoek [ Uitgebreide FAQ van de Campagne v8 ](https://experienceleague.adobe.com/docs/campaign/campaign-v8/start/campaign-faq-comprehensive.html){target="_blank"}.
