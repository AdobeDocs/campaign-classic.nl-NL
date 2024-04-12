---
product: campaign
title: Aan de slag met build-upgrades
description: Leer belangrijke stappen om aan een nieuwe bouwstijl te bevorderen
feature: Monitoring, Upgrade
badge-v7-prem: label="op locatie en hybride" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=nl" tooltip="Alleen van toepassing op on-premise en hybride implementaties"
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
exl-id: c5a9c99a-4078-45d8-847b-6df9047a2fe2
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '2323'
ht-degree: 0%

---

# Een build-upgrade uitvoeren{#performing-a-build-upgrade}



Deze sectie zal u van een diepgaande analyse op het verbeteringsproces en de stappen voorzien om conflicten te identificeren en op te lossen.

De verbetering van de bouw moet met voorzichtigheid worden uitgevoerd, de gevolgen ervan moeten vooraf volledig in overweging worden genomen en de procedure moet met een hoge mate van discipline worden afgerond. Zorg ervoor dat alleen deskundige gebruikers de hieronder beschreven stappen uitvoeren om ervoor te zorgen dat de upgrade is geslaagd. Daarnaast raden we u ten zeerste aan contact te houden met [Klantenservice Adoben](https://helpx.adobe.com/nl/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) voordat u een upgrade start.

De volgende voorwaarden zijn vereist:

* Inzicht in de campagnearchitectuur
* Kennis van systemen en servers
* Administratieve rechten en machtigingen

Meer informatie vindt u in de volgende secties: [Adobe Campaign bijwerken](../../production/using/upgrading.md), [Migreren naar een nieuwe versie](../../migration/using/about-migration.md).

Voor ontvangen en hybride instanties, moet u om de bouwstijlverbetering aan het team van de Technische Verrichtingen van de Adobe verzoeken. Raadpleeg voor meer informatie de sectie Veelgestelde vragen onderaan op deze pagina. Raadpleeg ook de [Veelgestelde vragen over upgrades maken](../../platform/using/faq-build-upgrade.md).

## De upgrade voorbereiden

![](assets/do-not-localize/icon_planification.png)

Voordat u de upgrade van de build start, moet u een volledige voorbereiding uitvoeren zoals hieronder wordt beschreven.
Zodra het systeem klaar is om te worden bevorderd, neemt een bouwstijlverbetering **ten minste** 2 uur.

Voor het upgradeproces voor build zijn de volgende bronnen vereist:

* een architect van de Adobe - om de gegevensbestandstructuren (out-of-the-box schema&#39;s en om het even welke extra schema&#39;s te begrijpen die zijn toegevoegd, campagneontwerpen, en om het even welke kritieke wegfunctionaliteit die in een specifieke orde moet worden begonnen en worden getest).
* een projectmanager - in het geval waar de bouwstijlverbetering vele verschillende instanties (productie, het opvoeren, het testen) en andere derdesservers en toepassingen (gegevensbestanden, de plaatsen van SFTP, overseinendienstverleners) impliceert, wordt het hebben van een projectmanager om alle het testen te coördineren beschouwd als beste praktijken.
* een Adobe Campaign-beheerder - uw beheerder kent de configuratie van de server, inclusief maar niet beperkt tot: beveiliging, maplay-out, rapportage en import-\exportvereisten. Voer geen upgrade voor build uit zonder uw beheerder.
* een Adobe Campaign-operator (marketinggebruiker) - een geslaagde upgrade is afhankelijk van het vermogen van de gebruiker om zijn dagelijkse taken met succes uit te voeren. Daarom moet u altijd ten minste een van uw dagelijkse operatoren opnemen in de tests van de bijgewerkte servers.

### Planning

Hier zijn de belangrijkste punten op hoe te om een bouwstijlverbetering te plannen:

1. Reserveer minstens 2 uur voor de upgrade.
1. Verdeel contactdetails voor Adobe en klantenpersoneel.
1. Voor gehoste instanties: Adobe en het klantenpersoneel zullen de tijd voor de verbetering coördineren en wie zal uitvoeren.
1. Voor on-premise gevallen: het personeel van de klant beheert het volledige proces - als hulp bij het testen van aangepaste workflows en leveringslogica nodig is, zouden de raadplegende diensten moeten worden geïntroduceerd.
1. Bepaal en bevestig naar welke versie van Adobe Campaign u wilt upgraden - raadpleeg de [Opmerkingen bij de release van Adobe Campaign Classic](../../rn/using/rn-overview.md).
1. Bevestig bezit van verbeterings uitvoerbare voorwerpen.

### Belangrijkste mensen

Voor het upgradeproces voor build moeten de volgende personen worden betrokken:

* Adobe architect: voor gehoste of hybride architecturen moet de architect coördineren met Adobe Campaign Client Care.

* Projectmanager:
   * voor installaties op locatie: de interne projectleider van de klant leidt de upgrade en beheert de levenscyclustests.

   * voor gehoste installatie: het hostingteam zal samenwerken met het Adobe Campaign Client Care-team en de klant om de tijdlijn van de upgrade voor alle instanties te coördineren.

* Adobe Campaign-beheerder:
   * voor installaties op locatie: de beheerder voert de upgrade uit.

   * voor gehoste installaties: het hostingteam voert de upgrade uit.

* Adobe Campaign operator\marketing user: de operator voert tests uit op ontwikkelings-, test- en productieinstanties.

### De upgrade van de build voorbereiden

Alvorens de bouwstijlverbetering te beginnen, moeten de klanten op-gebouw de volgende voorbereiding uitvoeren:

1. Zorg ervoor dat alle ontwikkelingswerk vóór de upgrade kan worden geëxporteerd en exporteer als pakketten.

1. Voer een volledige steun van de gegevensbestanden voor alle instanties van de bron en doelmilieu&#39;s uit.

1. De nieuwste versie van uw [serverconfiguratiebestand](../../installation/using/the-server-configuration-file.md).

1. [Download de nieuwste build](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html). [Meer informatie](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html).

U moet ook alle [nuttige opdrachtregels](../../installation/using/command-lines.md) voordat u een upgrade voor build start:

* **nlserver pdump**: maakt een lijst met actieve processen
* **nlserver pdump -who**: geeft actieve clientsessies weer
* **nlserver monitor ontbreekt**: in lijsten ontbreken eigenschappen
* **nlserver start process@instance-name**: start een proces
* **nlserver stop process@instance-name**: stopt een proces
* **process@instance-name opnieuw starten op de server**: start een proces opnieuw
* **Uitschakelen van server**: stopt alle Campagne-processen
* **nlserver waakhond - svc**: start de controlehond (alleen UNIX)

## De upgrade uitvoeren

![](assets/do-not-localize/icon_process.png)

De onderstaande procedures worden alleen uitgevoerd door **op locatie** klanten. Voor gehoste klanten is dit een taak van het hostingteam. Om Adobe Campaign bij te werken naar een nieuwe build, wordt de gedetailleerde procedure hieronder beschreven.

### De omgeving dupliceren

Hieronder wordt beschreven hoe u een Adobe Campaign-omgeving dupliceert om een bronomgeving te herstellen naar een doelomgeving, wat resulteert in twee identieke werkomgevingen.

Hiervoor voert u de volgende stappen uit:

1. Maak een kopie van de databases op alle instanties in de bronomgeving.

1. Herstel deze kopieën op alle exemplaren van de doelomgeving.

1. Voer de **nms:vriesinstantie.js** het waarschuwings manuscript op het doelmilieu alvorens het op te starten. Hiermee wordt een einde gemaakt aan alle processen die met de buitenkant communiceren: logboeken, tracering, leveringen, workflows voor campagnes, enz.

   ```
   nlserverjavacsriptnms:freezeInstance.js–instance:<dev> -arg:run
   ```

1. Controleer de opwarming als volgt:

   * Controleren of het enige leveringsgedeelte de id is waarop de id is ingesteld **0**:

     ```
     SELECT * FROM neolane.nmsdeliverypart;
     ```

   * Controleer of de update van de leveringsstatus correct is:

     ```
     SELECT iSate, count(*) FROM neolane.nmsdeliveryGroup By iProd;
     ```

   * Controleer of de update van de workflowstatus correct is:

     ```
     SELECT iState, count (*) FROM neolane.xtkworkflowGROUP BY iState;
     SELECT iStatus, count (*) FROM neolane.xtkworkflowGROUP BY iStatus;
     ```

### Afsluiten van services

Als u alle bestanden wilt vervangen door de nieuwe versie, moet u alle instanties van de service nlserverservice afsluiten.

1. Sluit de volgende services af:

   * Webservices (IIS): **iisreset /stop**
   * Adobe Campaign-service: **netstop nlserver6**

   >[!NOTE]
   >
   >Controleer of de omleidingsserver (webmdl) is gestopt, zodat het bestand nlsrvmod.dll dat door IIS wordt gebruikt, kan worden vervangen door de nieuwe versie.
   >

1. Valideren dat geen taken actief zijn door het **nlserver pdump** gebruiken. Als er geen taken zijn, dan zou de output op het volgende moeten lijken:

   ```
   C:\<installation path>\bin>nlserverpdump HH:MM:SS > Application Server for Adobe Campaign version x.x (build xxx) dated xx/xx/xxxx No tasks
   ```

1. Controleer de Manager van de Taak van Vensters om te bevestigen dat alle processen zijn tegengehouden.

### De Adobe Campaign Server-toepassing upgraden

1. Voer de **Setup.exe** bestand. Als u dit bestand moet downloaden, gaat u naar [het Downloadcentrum](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html).

1. Selecteer de installatiemodus: **Bijwerken** of **Repareren**.

1. Klikken **Volgende**.

1. Klikken **Voltooien**: de nieuwe bestanden worden gekopieerd in het installatieprogramma.

1. Klik op **Voltooien**.

### Bronnen synchroniseren

1. Open de opdrachtregel.

1. Uitvoeren **nlserver config -postupgrade -allinstances** om het volgende uit te voeren:

   * Bronnen synchroniseren
   * Schema&#39;s bijwerken
   * De database bijwerken

   >[!NOTE]
   >
   >Deze bewerking mag maar één keer worden uitgevoerd op een nlserverwebtoepassingsserver.
   >

   Als u slechts één database wilt synchroniseren, voert u de volgende opdracht uit:

   ```
   nlserver config -postupgrade -instance: <instance_name>
   ```

1. Controleer of de synchronisatie fouten of waarschuwingen heeft gegenereerd.

### Herstartservices

De volgende diensten moeten opnieuw worden opgestart:

* Webservices (IIS): **issreset /start**
* Adobe Campaign-service: **netwerkbeginserver6**

### Update voor clientconsoles

De cliëntconsole moet op de zelfde bouwstijl zoals de serverinstantie zijn.

Download en kopieer het bestand op de computer waarop de Adobe Campaign-toepassingsserver is geïnstalleerd (nlserverweb):

```
Setup-client-7.xxxx.exe in [path of the application]\datakit\nl\en\jsp
```

De volgende keer dat clientconsoles worden aangesloten, wordt gebruikers in een venster geïnformeerd over de beschikbaarheid van een nieuwe update en kunnen ze deze downloaden en installeren.

### Specifieke aanvullende taken

Sommige configuraties vereisen specifieke extra taken om aan een nieuwe bouwstijl bij te werken.

#### Transactieberichten

Wanneer het Transactionele Overseinen (het Centrum van het Bericht) op uw instantie van de Campagne wordt toegelaten, moet u deze extra stappen uitvoeren om te bevorderen:

1. Werk de de productieserver van het Centrum van het Bericht aan de gekozen versie bij.
1. Voer de scripts voor na de upgrade uit.
1. Voer tests uit en controleer of de e-mails zijn ontvangen via de productie-instantie van Message Center.
1. Clients upgraden en cache wissen.
1. Pakketten exporteren:
   * Pakketten exporteren met het exportgereedschap voor clientpakketten
   * Schema-pakket importeren
   * Verbinding met client verbreken en opnieuw verbinden
   * Database bijwerken
   * Verbinding verbreken en opnieuw verbinden
   * Admin-pakket importeren
   * Inhoudspakket importeren
   * Het pakket Inhoudsbeheer importeren
   * Verbinding verbreken en opnieuw verbinden
   * Een snelle controle van de hygiëne van workflows uitvoeren

1. Publiceer de malplaatjes van het Centrum van het Bericht om ervoor te zorgen dat de interface tussen servers en de instantie van het Centrum van het Bericht werkt.
1. Voer tests uit om ervoor te zorgen dat e-mails met succes worden ontvangen via de productie-instantie van Message Center.
1. Voer workflowtests uit tijdens de productie om te controleren of leveringen zijn ontvangen.

#### Midden-sourcing

In de context van een omgeving voor midsourcing moet u de volgende aanvullende stappen uitvoeren om een upgrade uit te voeren:

1. Contact [Klantenservice Adoben](https://helpx.adobe.com/nl/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) om de upgrade van de Midden-Bronsserver te coördineren.
1. Valideer of de versie is bijgewerkt door een testkoppeling uit te voeren. Bijvoorbeeld:

   ```
   http://[InsertServerURL]/r/test
   ```

>[!NOTE]
>
>De server voor middensegment moet altijd dezelfde versie (of recenter) gebruiken als voor de marketingservers.
>

## In geval van conflicten

### Conflicten identificeren

U moet het synchronisatieresultaat controleren. Deze procedure wordt slechts uitgevoerd door on-premise klanten. Voor gehoste klanten is dit een taak van het hostingteam. Er zijn twee manieren om het synchronisatieresultaat weer te geven:

In de opdrachtregelinterface worden fouten geconcretiseerd door een drievoudig chevron &#39;>>&#39; en wordt de synchronisatie automatisch gestopt. Waarschuwingen worden geconcretiseerd door een dubbel chevron &#39;>&#39; en moeten worden opgelost zodra de synchronisatie is voltooid. Aan het eind van postupgrade, wordt een samenvatting getoond in de bevelherinnering. Het kan er als volgt uitzien:

```
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 info log =========Summary of the update==========
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 info log <instance name> instance, 6 warning(s) and 0 error(s) during the update.
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 warning log The document with identifier 'mobileAppDeliveryFeedback' and type 'xtk:report' is in conflict with the new version.
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 warning log The document with identifier 'opensByUserAgent' and type 'xtk:report' is in conflict with the new version.
YYYY-MM-DD HH:MM:SS.750Z 00002E7A 1 warning log The document with identifier 'deliveryValidation' and type 'nms:webApp' is in conflict with the new version.
YYYY-MM-DD HH:MM:SS.750Z 00002E7A 1 warning log Document of identifier 'nms:includeView‘ and type 'xtk:srcSchema' updated in the database and found in the file system. You will have to merge the two versions manually.
```

Als de waarschuwing een conflict van middelen betreft, wordt de aandacht van de gebruiker vereist om het op te lossen.

De **postupgrade_ServerVersionNumber_TimeOfPostupgrade.log** bevat het synchronisatieresultaat. Deze is standaard beschikbaar in de volgende map: **installDirectory/var/`<instance-name>`/postupgrade**. Fouten en waarschuwingen worden aangegeven door de fout- en waarschuwingskenmerken.

### Conflicten analyseren

**Hoe wordt een conflict gevonden?**

Conflicten kunnen worden gevonden binnen postupgrade.log op de server in kwestie of binnen de cliëntinterface van de Campagne (Beleid > Configuratie > het Beheer van het Pakket > geeft conflicten uit).

Het document met de id &quot;stockOverview&quot; en het type &quot;nms:webApp&quot; is in strijd met de nieuwe versie.

Als er een conflict wordt gevonden, controleert u of de volgende voorwaarden overeenkomen:

* Is het object gewijzigd of aangepast door de klant?
* Is het object in het product gewijzigd?

Als geen van beide voorwaarden van toepassing is, is dit een fout-positief. Als beide voorwaarden van toepassing zijn, is er een echt conflict gevonden.

**Is het object gewijzigd door de klant?**

1. Identificeer het conflicterende object.
1. Vraag de klant of deze het object heeft gewijzigd.
1. Is er iets ongebruikelijks met het object?
1. Is de datum van de laatste wijziging ingesteld in de code van het object?
1. Onderzoek de code van XML van het conflict voor &quot;_conflict&quot;attributen. Ziet het eruit als een aanpassing?

**Is het object gewijzigd in de nieuwe build?**

1. Zijn er &quot;gewone verdachten&quot;? Ingebouwde webtoepassingen of -rapporten (bijv. &#39;deliveryValidation&#39;, &#39;deliveryOverview&#39;, &#39;budget&#39;).
1. Onderzoek de veranderingslogboeken voor om het even welke updates.
1. Vraag het Adobe Campaign-experts.
1. Voer een &quot;diff&quot;op de code uit.

### Een conflict oplossen

Pas het volgende proces toe om conflicten op te lossen:

1. Ga in de Adobe Campaign explorer naar **Beheer > Configuration > Package Management > Edit conflicts**.

1. Selecteer het conflict dat u wilt oplossen in de lijst.
Er zijn drie opties om conflicten op te lossen: **De nieuwe versie accepteren**, **Huidige versie behouden**, **De code samenvoegen (en declareren als opgelost)**, **Conflict negeren (niet aanbevolen)**.

**Wanneer kan ik de nieuwe versie accepteren?**

* Als u de standaardfuncties wilt gebruiken.
* Als u geen aanpassingen hebt (alle aanpassingen worden verwijderd)

**Wanneer kan ik de huidige versie behouden?**

* Als u aanpassingen hebt
* Als u niet wilt samenvoegen
* Als u geen correcties op het conflicterende object van de upgrade nodig hebt

**Wanneer wordt een samenvoeging uitgevoerd?**

* Alleen formulieren, rapporten en webtoepassingen kunnen worden samengevoegd.
* Sommige kleine fusies kunnen worden opgelost zonder de code te begrijpen.
* Complexere fusies moeten worden uitgevoerd door iemand met de juiste vaardigheden en bekwaamheid.
* Zie [Samenvoegen uitvoeren](#perform-a-merge).

**Wat als ik de conflicten negeer?**

* Het conflict zal blijven
* Het object wordt niet bijgewerkt
* Gevolgen op lange termijn: de onverenigbaarheden van de versie, de klant zal niet van insectenmoeilijke situaties profiteren.

>[!IMPORTANT]
>Het wordt ten zeerste aanbevolen conflicten op te lossen.
>

### Samenvoegen uitvoeren{#perform-a-merge}

Er zijn verschillende soorten samenvoegingen:

1. Eenvoudig samenvoegen: aangepaste en nieuwe elementen zijn klein en niet gerelateerd en er is geen codering vereist.
1. Geen wijzigingen: nieuwe versie accepteren, alleen laatste bijgewerkte datum wijzigen, alleen opmerkingen, tabs, spaties of nieuwe regels. Voorbeeld: opslaan als gevolg van een ongeluk.
1. Tijdelijke wijzigingen: slechts één regel is gewijzigd. Voorbeeld: xpathToLoad
1. Complexe samenvoeging: wanneer codering is vereist. Er zijn ontwikkelingsvaardigheden nodig. Zie [Complexe samenvoegingen](#complex-merges).

#### Hoe samenvoegen?

1. Alle drie de versies ophalen: de oorspronkelijke versie, de nieuwe versie en de aangepaste versie.
1. Voer een &#39;diff&#39; uit tussen de oorspronkelijke en de nieuwe versie.
1. De wijzigingen isoleren.
1. Als er geen wijzigingen worden aangebracht, moet u deze oplossen door de huidige versie te behouden.

#### Waar vindt u de code?

1. De ingebouwde code wordt opgeslagen in de dossiers van XML in de datakit omslag. Zoek het XML-bestand dat overeenkomt met het conflicterende object. Voorbeeld: installationDirectory\datakit\nms\fra\form\recipient.xml
1. De originele versie ophalen: via de [Downloadcentrum](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) of een andere installatie van het product zonder upgrade.
1. De nieuwe versie ophalen: via de [Downloadcentrum](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) of de geïnstalleerde bestanden van de klant.
1. Haal de aangepaste versie op: haalt de broncode van het object op vanuit de campagneclient.

### Hoe maak je een diff?

1. Installeer een tekst- of samenvoegeditor, bijvoorbeeld Kladblok ++, AraxisMerge, WinMerge.
1. Open het oorspronkelijke bestand en het nieuwe bestand in de editor.
1. Voer het diff uit (vergelijk de twee dossiers).
1. Eventuele verschillen identificeren.

### Hoe samenvoegen?

1. Begin bij de aangepaste versie.
1. Pas de wijzigingen toe.
1. Los het conflict op door het als opgelost te verklaren.
1. Controleren op niet-regressies.

Ga als volgt te werk als u het conflict handmatig wilt oplossen:

1. Zoek in de onderste sectie van het venster naar de **_conflict_string_** om de entiteiten met conflicten te zoeken. De entiteit die met de nieuwe versie is geïnstalleerd, bevat het nieuwe argument. De entiteit die met de vorige versie overeenkomt, bevat het aangepaste argument.
1. Verwijder de versie die u niet wilt behouden. Verwijder de **_conflict_argument_** tekenreeks van de entiteit die u bewaart.
1. Ga naar het conflict dat u hebt opgelost. Klik op de knop **Handelingen** pictogram en selecteer **Opgeven als opgelost**.
1. Sla uw wijzigingen op: het conflict is nu opgelost.

#### Complexe samenvoegingen{#complex-merges}

1. Begrijp wat de verandering doet: omgekeerd-ingenieer de veranderingen, onderzoek de veranderingslogboeken, follow-up met de deskundigen van Adobe Campaign.
1. Bepaal wat u met de wijziging wilt doen.
1. Begrijp wat de aanpassingen doen: omgekeerde ingenieur de veranderingen

Hier volgen de stappen voor het uitvoeren van een complexe samenvoeging:

1. bits met code uit de set met wijzigingen kopiëren
1. Plakken naar de aangepaste versie
1. Test op niet-regressies van aanpassingen
1. Testen op de functie van wijzigingen
1. Testen van gebruikersacceptatie uitvoeren
1. Uitvoeren in testomgeving


>[!IMPORTANT]
>De ontwikkelingsvaardigheden worden vereist om complexe fusies uit te voeren.
>

**Verwante onderwerpen**

* [Veelgestelde vragen over buildupgrades](../../platform/using/faq-build-upgrade.md)
* [Opmerkingen bij de release Campaign Classic](../../rn/using/rn-overview.md)
* [Help- en ondersteuningsopties voor Campaign Classic](../../support.md)
* [Campagne Yearly Upgrade program](../../rn/using/rn-overview.md)
