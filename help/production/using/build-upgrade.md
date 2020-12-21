---
solution: Campaign Classic
product: campaign
title: Aan de slag met build-upgrades
description: Leer belangrijke stappen om aan een nieuwe bouwstijl te bevorderen
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
translation-type: tm+mt
source-git-commit: 5639f08ad709597d5f5c9e6bbd6932cffcbde40f
workflow-type: tm+mt
source-wordcount: '2368'
ht-degree: 0%

---


# Een build-upgrade uitvoeren{#performing-a-build-upgrade}

Deze sectie zal u van een diepgaande analyse op het verbeteringsproces en de stappen voorzien om conflicten te identificeren en op te lossen.

De verbetering van de bouw moet met voorzichtigheid worden uitgevoerd, de gevolgen ervan moeten vooraf volledig in overweging worden genomen en de procedure moet met een hoge mate van discipline worden afgerond. Zorg ervoor dat alleen deskundige gebruikers de hieronder beschreven stappen uitvoeren om ervoor te zorgen dat de upgrade is geslaagd. Daarnaast raden we u ten zeerste aan contact op te nemen met [Adobe Customer Care](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) voordat u een upgrade start.

De volgende voorwaarden zijn vereist:

* Inzicht in de campagnearchitectuur
* Kennis van systemen en servers
* Administratieve rechten en machtigingen

Meer informatie vindt u in de volgende secties: [Adobe Campaign](../../production/using/upgrading.md) bijwerken, [Migreren naar een nieuwe versie](../../migration/using/about-migration.md).

Voor ontvangen en hybride instanties, moet u om de bouwstijlverbetering aan het team van de Technische Verrichtingen van Adobe verzoeken. Raadpleeg voor meer informatie de sectie Veelgestelde vragen onderaan op deze pagina. Raadpleeg ook [Veelgestelde vragen over upgrades voor build](../../platform/using/faq-build-upgrade.md).

## De upgrade voorbereiden

![](assets/do-not-localize/icon_planification.png)

Voordat u de upgrade van de build start, moet u een volledige voorbereiding uitvoeren zoals hieronder wordt beschreven.
Wanneer het systeem klaar is om te worden geüpgraded, duurt een upgrade **ten minste** 2 uur.

Voor het upgradeproces voor build zijn de volgende bronnen vereist:

* een architect van Adobe - om de gegevensbestandstructuren (uit-van-de-doosschema&#39;s en om het even welke extra schema&#39;s te begrijpen die zijn toegevoegd, campagneontwerpen, en om het even welke kritieke wegfunctionaliteit die in een specifieke orde moet worden begonnen en worden getest).
* een projectmanager - in het geval waar de bouwstijlverbetering vele verschillende instanties (productie, het opvoeren, het testen) en andere derdesservers en toepassingen (gegevensbestanden, de plaatsen van SFTP, overseinendienstverleners) impliceert, wordt het hebben van een projectmanager om alle het testen te coördineren beschouwd als beste praktijken.
* een Adobe Campaign-beheerder - uw beheerder kent de configuratie van de server inclusief maar niet beperkt tot: vereisten voor beveiliging, maplay-out, rapportage en importeren\exporteren. Gelieve te voeren geen bouwstijlverbetering zonder uw beheerder uit.
* een Adobe Campaign-operator (marketinggebruiker) - een geslaagde upgrade is afhankelijk van het vermogen van de gebruiker om zijn dagelijkse taken met succes uit te voeren. Daarom moet u altijd ten minste een van uw dagelijkse operatoren opnemen in de tests van de bijgewerkte servers.

### Planning

Hier zijn de belangrijkste punten op hoe te om een bouwstijlverbetering te plannen:

1. Reserveer minstens 2 uur voor de upgrade.
1. Verdeel contactdetails voor Adobe en klantenpersoneel.
1. Voor gehoste instanties: Adobe en het klantenpersoneel zullen de tijd voor de verbetering coördineren en wie zal uitvoeren.
1. Voor instanties op locatie: het personeel van de klant beheert het gehele proces - als hulp bij het testen van aangepaste workflows en leveringslogica nodig is , moeten consultingservices worden ingevoerd .
1. Bepaal en bevestig welke versie van Adobe Campaign u wilt bevorderen aan - raadpleeg [de versienota&#39;s van Adobe Campaign Classic](../../rn/using/rn-overview.md).
1. Bevestig bezit van verbeterings uitvoerbare voorwerpen.

### Belangrijke mensen

Voor het upgradeproces voor build moeten de volgende personen worden betrokken:

* Adobe architect: voor gehoste of hybride architecturen moet de architect coördineren met Adobe Campaign Client Care.

* Projectmanager:
   * voor installaties op locatie: de interne projectleider van de klant leidt de upgrade en beheert de levenscyclustests.

   * voor gehoste installatie: het hostingteam zal samenwerken met het Adobe Campaign Client Care-team en de klant om de upgradetijdlijn voor alle gevallen te coördineren.

* Adobe Campaign-beheerder:
   * voor installaties op locatie: de beheerder voert de verbetering uit.

   * voor gehoste installaties: het hostingteam voert de upgrade uit.

* Adobe Campaign-operator\marketinggebruiker: de exploitant voert tests uit op ontwikkelings-, test- en productieinstanties.

### De upgrade van de build voorbereiden

Alvorens de bouwstijlverbetering te beginnen, moeten de klanten op-gebouw de volgende voorbereiding uitvoeren:

1. Zorg ervoor dat alle ontwikkelingswerk vóór de upgrade kan worden geëxporteerd en exporteer als pakketten.

1. Voer een volledige steun van de gegevensbestanden voor alle instanties van de bron en doelmilieu&#39;s uit.

1. Krijg de recentste versie van uw [dossier van de serverconfiguratie](../../installation/using/the-server-configuration-file.md).

1. Download de nieuwste build. [Meer weten over het Downloadcentrum](https://docs.adobe.com/content/help/en/experience-cloud/software-distribution/home.html)?

U moet ook alle [nuttige bevellijnen ](../../installation/using/command-lines.md) kennen alvorens een bouwstijlverbetering te beginnen:

* **pdump** nlserver: lijsten lopende processen
* **nlserver pdump -who**: lijsten actieve cliëntzittingen
* **nlserver monitor - ontbreekt**: lijsten ontbrekende eigenschappen
* **nlserver start process@instanceName**: start een proces
* **nlserver stop process@instanceName**: stopt een proces
* **process@instanceName** opnieuw starten op de server: start een proces opnieuw
* **Uitschakelen** van server: stopt alle Campagneprocessen
* **nlserver watchdog -svc**: start de waakhond (alleen UNIX)

## De upgrade uitvoeren

![](assets/do-not-localize/icon_process.png)

De onderstaande procedures worden alleen uitgevoerd door **on-premise** klanten. Voor gehoste klanten is dit een taak van het hostingteam. Om Adobe Campaign bij te werken naar een nieuwe build, wordt de gedetailleerde procedure hieronder beschreven.

### De omgeving dupliceren

Hieronder wordt beschreven hoe u een Adobe Campaign-omgeving dupliceert om een bronomgeving te herstellen naar een doelomgeving, wat resulteert in twee identieke werkomgevingen.

Volg de onderstaande stappen om dit te doen:

1. Maak een kopie van de databases op alle instanties in de bronomgeving.

1. Herstel deze kopieën op alle exemplaren van de doelomgeving.

1. Voer het **nms:vriesinstance.js**-waarschuwingsscript uit op de doelomgeving voordat u het opstart. Hiermee wordt een einde gemaakt aan alle processen die op de buitenkant reageren: logboeken, tracering, leveringen, campagneworkflows, enz.

   ```
   nlserverjavacsriptnms:freezeInstance.js–instance:<dev> -arg:run
   ```

1. Controleer de opwarming als volgt:

   * Controleer of het enige leveringsgedeelte de id is die is ingesteld op **0**:

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
   * Adobe Campaign-service: **net stop nlserver6**

   >[!NOTE]
   >
   >Controleer of de omleidingsserver (webmdl) is gestopt, zodat het bestand nlsrvmod.dll dat door IIS wordt gebruikt, kan worden vervangen door de nieuwe versie.

1. Valideer dat geen taken door **nlserver PDump** bevel in werking te stellen actief zijn. Als er geen taken zijn, dan zou de output op het volgende moeten lijken:

   ```
   C:\<installation path>\bin>nlserverpdump HH:MM:SS > Application Server for Adobe Campaign version x.x (build xxx) dated xx/xx/xxxx No tasks
   ```

1. Controleer de Manager van de Taak van Vensters om te bevestigen dat alle processen zijn tegengehouden.

### De Adobe Campaign Server-toepassing upgraden

1. Voer het bestand **Setup.exe** uit. Als u dit bestand moet downloaden, opent u [het Downloadcentrum](https://docs.adobe.com/content/help/en/experience-cloud/software-distribution/home.html).

1. Selecteer de installatiemodus: **Bijwerken** of **Herstellen**.

1. Klik **Volgende**.

1. Klik **Voltooien**: de nieuwe bestanden worden gekopieerd in het installatieprogramma .

1. Als de bewerking is voltooid, klikt u op **Voltooien**.

### Bronnen synchroniseren

1. Open de opdrachtregel.

1. Voer **nlserver config -postupgrade -allinstances** uit om het volgende uit te voeren:

   * Bronnen synchroniseren
   * Schema&#39;s bijwerken
   * De database bijwerken

   >[!NOTE]
   >
   >Deze bewerking mag maar één keer worden uitgevoerd op een nlserverwebtoepassingsserver.

   Voer de volgende opdracht uit om slechts één database te synchroniseren:

   ```
   nlserver config -postupgrade -instance: <instance_name>
   ```

1. Controleer of de synchronisatie fouten of waarschuwingen heeft gegenereerd.

### Herstartservices

De volgende diensten moeten opnieuw worden opgestart:

* Webservices (IIS): **issreset /start**
* Adobe Campaign-service: **net start nlserver6**

### Update voor clientconsoles

De cliëntconsole moet op de zelfde bouwstijl zoals de serverinstantie zijn.

Download en kopieer het bestand op de computer waarop de Adobe Campaign-toepassingsserver is geïnstalleerd (nlserverweb):

```
Setup-client-7.xxxx.exe in [path of the application]\datakit\nl\en\jsp
```

De volgende keer dat clientconsoles worden aangesloten, wordt gebruikers in een venster geïnformeerd over de beschikbaarheid van een nieuwe update en kunnen ze deze downloaden en installeren.

### Specifieke aanvullende taken

Sommige configuraties vereisen specifieke extra taken om aan een nieuwe bouwstijl bij te werken.

#### Transactionele berichten

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

In de context van een omgeving voor midsourcing moet u de volgende aanvullende stappen uitvoeren om te upgraden:

1. Neem contact op met de [Adobe-klantenservice](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) om de upgrade van de Midden-Bronserver te coördineren.
1. Valideer of de versie is bijgewerkt door een testkoppeling uit te voeren. Bijvoorbeeld:

   ```
   http://[InsertServerURL]/r/test
   ```

>[!NOTE]
>
>De server voor middensegment moet altijd dezelfde versie (of recenter) gebruiken als voor de marketingservers.


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

Het **postupgrade_ServerVersionNumber_TimeOfPoint.log**-bestand bevat het synchronisatieresultaat. Deze is standaard beschikbaar in de volgende map: **installationDirectory/var/instanceName/postupgrade**. Fouten en waarschuwingen worden aangegeven door de fout- en waarschuwingskenmerken.

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

1. Zijn er &quot;gewone verdachten&quot;? Ingebouwde webtoepassingen of -rapporten (bijvoorbeeld: &#39;deliveryValidation&#39;, &#39;deliveryOverview&#39;, &#39;budget&#39;).
1. Onderzoek de veranderingslogboeken voor om het even welke updates.
1. Vraag het Adobe Campaign-experts.
1. Voer een &quot;diff&quot;op de code uit.

### Een conflict oplossen

Pas het volgende proces toe om conflicten op te lossen:

1. Ga in de Adobe Campaign-verkenner naar **Beheer > Configuratie > Pakketbeheer > Conflicten bewerken**.

1. Selecteer het conflict dat u wilt oplossen in de lijst.
Er zijn drie opties om conflicten op te lossen: **Accepteer de nieuwe versie**, **De huidige versie** behouden, **De code samenvoegen (en declareren als opgelost)**, **Het conflict negeren (niet aanbevolen)**.

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
* Zie [Samenvoegen](#perform-a-merge) uitvoeren.

**Wat als ik de conflicten negeer?**

* Het conflict zal blijven
* Het object wordt niet bijgewerkt
* Effecten op lange termijn: de incompatibiliteiten van de versie, zal de klant niet van insectenmoeilijke situaties profiteren.

>[!IMPORTANT]
>Het wordt ten zeerste aanbevolen conflicten op te lossen.


### Samenvoegen{#perform-a-merge} uitvoeren

Er zijn verschillende soorten samenvoegingen:

1. Eenvoudig samenvoegen: aangepaste en nieuwe elementen zijn klein en staan los van elkaar en er is geen codering vereist.
1. Geen wijzigingen: accepteert nieuwe versie, alleen de laatste bijgewerkte datum wordt gewijzigd, alleen opmerkingen, tabs, spaties of nieuwe regels. Voorbeeld: opslaan per ongeluk.
1. Tijdelijke veranderingen: er is slechts één regel gewijzigd. Voorbeeld: xpathToLoad
1. Complexe samenvoeging: wanneer codering vereist is. Ontwikkeling is vereist. Zie [Complexe samenvoegingen](#complex-merges).

#### Hoe samenvoegen?

1. Alle drie de versies ophalen: de oorspronkelijke versie, de nieuwe versie en de aangepaste versie.
1. Voer een &#39;diff&#39; uit tussen de oorspronkelijke en de nieuwe versie.
1. De wijzigingen isoleren.
1. Als er geen wijzigingen worden aangebracht, moet u deze oplossen door de huidige versie te behouden.

#### Waar vindt u de code?

1. De ingebouwde code wordt opgeslagen in de dossiers van XML in de datakit omslag. Zoek het XML-bestand dat overeenkomt met het conflicterende object. Voorbeeld: installationDirectory\datakit\nms\fra\form\recipient.xml
1. De originele versie ophalen: via het [Downloadcentrum](https://docs.adobe.com/content/help/en/experience-cloud/software-distribution/home.html) of een andere niet-geüpgrade installatie van het product.
1. De nieuwe versie ophalen: via het [Downloadcentrum](https://docs.adobe.com/content/help/en/experience-cloud/software-distribution/home.html) of de geïnstalleerde bestanden van de klant.
1. De aangepaste versie ophalen: Haal de broncode van het object op vanuit de campagneclient.

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

1. Zoek in de onderste sectie van het venster naar **_conflict_string_** om de entiteiten met conflicten te zoeken. De entiteit die met de nieuwe versie is geïnstalleerd, bevat het nieuwe argument. De entiteit die met de vorige versie overeenkomt, bevat het aangepaste argument.
1. Verwijder de versie die u niet wilt behouden. Verwijder de **_conflict_argument_**-tekenreeks van de entiteit die u bewaart.
1. Ga naar het conflict dat u hebt opgelost. Klik op het pictogram **Acties** en selecteer **Als opgelost declareren**.
1. Sla uw wijzigingen op: het conflict is nu opgelost .

#### Complexe samenvoegingen{#complex-merges}

1. Begrijp wat de verandering doet: reverse-engineeren de wijzigingen, de wijzigingslogboeken bekijken, opvolgen met Adobe Campaign-experts.
1. Bepaal wat u met de wijziging wilt doen.
1. Begrijp wat de aanpassingen doen: reverse-engineeren van de wijzigingen

Hier volgen de stappen voor het uitvoeren van een complexe samenvoeging:

1. bits met code uit de set met wijzigingen kopiëren
1. Plakken naar de aangepaste versie
1. Test op niet-regressies van aanpassingen
1. Testen op de functie van wijzigingen
1. Testen van gebruikersacceptatie uitvoeren
1. Uitvoeren in testomgeving


>[!IMPORTANT]
>De ontwikkelingsvaardigheden worden vereist om complexe fusies uit te voeren.


**Verwante onderwerpen**

* [Veelgestelde vragen over upgrades samenstellen](../../platform/using/faq-build-upgrade.md)
* [Opmerkingen bij de release Campaign Classic](../../rn/using/rn-overview.md)
* [Help- en ondersteuningsopties voor Campaign Classic](https://helpx.adobe.com/campaign/kb/ac-support.html#acc-support-req)
* [Gold Standard-programma](https://helpx.adobe.com/nl/campaign/kb/gold-standard.html)