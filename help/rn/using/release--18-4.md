---
title: Release 18.4
seo-title: Release 18.4
description: Release 18.4
seo-description: null
page-status-flag: never-activated
uuid: d132570e-20e6-4550-95bd-176701f43b19
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: rn
content-type: reference
topic-tags: latest-release-notes
discoiquuid: 4dc87ff3-eb6a-40ac-97ee-00b64cd7718d
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 3801665574d0cdc9c0caf46fb2f0eede38f1b2cc

---


# Release 18.4{#release-18-4}

## Release 18.4.5 - build 8937{#release-18-4-5-build-8937}

21 november 2018

**Verbeteringen**

* Verschillende problemen verholpen bij het uitvoeren van workflows met MySQL op FDA. (NEO-11652)
* Probleem verholpen waarbij een deel van de leveringspopulatie in bepaalde gevallen in behandeling bleef. (NEO-11336)
* Correctie van een periodiek probleem met de automatische reactie van SMS. (NEO-11811)
* Probleem verholpen met uitputting van id&#39;s bij gebruik van zaadadressen in een levering. (NEO-11842)
* Oplossing voor een syntaxisfout bij het sorteren in een verrijkingswerkstroomactiviteit. (NEO-11394)
* Probleem verholpen waarbij een webserver vastliep als IIS opnieuw wordt gestart. (NEO-10862)
* Probleem verholpen waarbij de traceringsworkflow mislukte na een upgrade van de build (FDA - SQL). (NEO-11635)
* Probleem verholpen waarbij gegevens uit de workflowlijst verloren konden gaan. (NEO-11696)
* Probleem met prestaties verholpen bij het verzenden van pushberichten. (NEO-11787)
* Probleem verholpen waarbij webtracering niet werkte voor &#39;com.au&#39;-domeinen (NEO-4385).
* Oplossing voor een probleem met de blokkering van clients dat zich kon voordoen bij het gebruik van complexe workflows. (NEO-11847)
* Oplossing voor een Oracle-fout bij het opslaan van een nieuwe levering na het selecteren van een element van een specifiek schema (NEO-11682).
* Probleem verholpen bij het opvragen van een veld met tekens met accenten (FDA/Teradata). Met de externe account kunt u nu de codering wijzigen die wordt gebruikt voor de communicatie met het stuurprogramma voor metagegevens. (NEO-11818).
* Probleem met bijhouden bij het doorgeven van URL&#39;s in extra variabelen in een pushmelding verholpen dat kan leiden tot onjuiste of onjuiste gegevens die door de mobiele toepassing worden ontvangen. (NEO-11468, NEO-11960)
* Probleem verholpen dat een weergaveprobleem veroorzaakte bij het gebruik van een verdeling van waarden met een koppeling 1:N. (NEO-11820)
* Probleem verholpen waarbij bulkbelasting niet kon werken op Teradata 16.
* De buffergrootte voor timestamp op Teradata is verhoogd om bindingsproblemen met 15.10 stuurprogramma te voorkomen.
* Verbeterde het beheer van lange naamindexen die postupgrade-problemen kunnen veroorzaken.
* Verbeterde beschikbare tijd voor gedeeld geheugen tijdens dood verwerken van kinderen (MTA).
* Oplossing voor een mogelijke impasse in Apache (tracking).

## Release 18.4.4 - build 8936{#release-18-4-4-build-8936}

1 augustus 2018

**Verbeteringen**

* Logbestanden voor e-mailarchivering zijn verbeterd, waardoor het eenvoudiger en duidelijker wordt om te controleren welke e-mails met succes zijn geleverd of niet zijn gearchiveerd via BCC-archivering. (NEO-10675)
* Probleem verholpen dat leidde tot de weergave van IP&#39;s van het taakverdelingsmechanisme in plaats van IP&#39;s van de klant in de weblogs voor het bijhouden van berichten. (NEO-11295)
* Oplossing voor een fout met LATIN1-codering bij gebruik van een FDA-verbinding met een PostSQL-database. (NEO-11299)
* Probleem verholpen dat optrad bij gebruik van de **[!UICONTROL Prepare the personalization data with a workflow]** leveringsoptie. (NEO-11047, NEO-11301)
* Probleem verholpen waarbij een willekeurig probleem werd opgelost waardoor de eigenschappen van een levering onjuist werden overschreven. (NEO-11015)
* Probleem verholpen bij het gebruik van berekende velden in een **[!UICONTROL Survey answers]** workflowactiviteit. (NEO-11382)
* Probleem verholpen bij het gebruik van in XML opgeslagen gegevens in een **[!UICONTROL Survey answers]** workflowactiviteit. (NEO-10816)
* Probleem verholpen bij het uitvoeren van de serverupgrade met build 8935.
* Probleem verholpen waarbij nutteloze fouten in het postupgradelogboek werden weergegeven wanneer een **[!UICONTROL Survey answers]** workflowactiviteit niet volledig was geconfigureerd.
* FDA-gegevens: Probleem verholpen met automatisch verhoogde velden en indexen in SQL-tabellen.

## Release 18.4.3 - build 8935{#release-18-4-3-build-8935}

22 juni 2018

**Verbeteringen**

* Probleem met codering van bijhouden opgelost met Microsoft Edge en Internet Explorer. (NEO-11257)
* Probleem verholpen met aanpassen van afbeeldingskoppelingen in lijnleveringen. (NEO-11077)
* Probleem verholpen waardoor het genereren van de id-reeks niet correct werkte. (NEO-11115)
* Probleem verholpen waarbij privacyverzoeken (GDPR) niet werkten bij het gebruik van een aangepaste naamruimte met een combinatietoets. (NEO-11123)
* Oplossing voor een fout die kan optreden wanneer de **[!UICONTROL Distribution of values]** optie wordt gebruikt bij **[!UICONTROL Query]** workflowactiviteiten. (NEO-10958)
* Probleem verholpen bij het synchroniseren van aanbiedingsruimten van de marketinginstantie naar de interactie-instantie. (NEO-11162)
* Verbeterd beheer van lange naamindexen tijdens postupgrade

## Release 18.4.2 - build 8932{#release-18-4-2-build-8932}

22 mei 2018

**Verbeteringen**

* Probleem verholpen waarbij de Windows Server-update niet correct werkte.
* Probleem opgelost in de **[!UICONTROL Survey Result]** activiteit bij het gebruik van gegevens die zijn opgeslagen in XML. Het rapport is onjuist weergegeven. (NEO-10816)
* Oplossing voor een prestatieprobleem dat met het InMail-proces kon optreden bij het gebruik van een stuiterende mailserver. (NEO-10641)
* Oplossing voor een probleem met een databaseupgrade dat zich kon voordoen wanneer u meer dan 1000 schema&#39;s bijwerkte.

## Release 18.4 - build 8931{#release-18-4-build-8931}

24 apr. 2018

**Wat is nieuw?**

<table> 
 <thead> 
  <tr> 
   <th> Functionaliteit<br /> </th> 
   <th> Beschrijving<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Algemene EU-verordening inzake gegevensbescherming (GDPR)<br /> </td> 
   <td> <p>GDPR is de nieuwe privacywet van de Europese Unie (EU) die de vereisten inzake gegevensbescherming harmoniseert en moderniseert en op 25 mei 2018 van kracht wordt. GDPR is van toepassing op klanten van de Campagne van Adobe die gegevens voor de Onderwerpen van Gegevens in de EU houden.</p> <p>Naast de privacymogelijkheden die reeds beschikbaar zijn in de Campagne van Adobe (met inbegrip van toestemmingsbeheer, montages van het gegevensbehoud, en gebruikersrollen), nemen wij deze kans in onze rol als Bewerker van Gegevens om extra mogelijkheden te omvatten, helpen uw bereidheid als Controlemechanisme voor bepaalde GDPR- verzoeken vergemakkelijken:</p> 
    <ul> 
     <li> <p>Recht op toegang: Hiermee kan de betrokkene een kopie ontvangen van zijn/haar persoonlijke gegevens die zijn vastgelegd door gegevenscontrollers, waaronder mogelijk gegevens die zijn opgeslagen in Adobe Campaign.</p> </li> 
     <li> <p>Rechts om te verwijderen: geeft de betrokkene het recht om zijn/haar persoonlijke gegevens die door gegevenscontrollers zijn vastgelegd, te laten wissen, mogelijk met inbegrip van gegevens die in Adobe Campaign zijn opgeslagen.</p> </li> 
    </ul> Raadpleeg de <a href="https://helpx.adobe.com/campaign/kb/acc-privacy.html">gedetailleerde documentatie</a>voor meer informatie.<br /> </td> 
  </tr> 
  <tr> 
   <td> Actieve profielen<br /> </td> 
   <td> <p>Adobe Campaign bevat nu de lijst met actieve profielen, die elke maand wordt bijgewerkt via een speciale workflow.</p> <p>Raadpleeg de <a href="../../platform/using/about-profiles.md#active-profiles">gedetailleerde documentatie</a>voor meer informatie.</p> </td> 
  </tr> 
  <tr> 
   <td> Verbetering Android-pushconnector<br /> </td> 
   <td> <p>De Android-connector is verbeterd en biedt nu ondersteuning voor een hogere doorvoer. </p> <p>Raadpleeg de <a href="../../delivery/using/configuring-the-mobile-application.md">gedetailleerde documentatie</a>voor meer informatie.</p> </td> 
  </tr> 
 </tbody> 
</table>

**Verbeterde beveiliging**

* De uitbreiding van externe entiteiten is nu uitgeschakeld om potentiële aanvallen van niet-geverifieerde gebruikers te voorkomen. (NEO-10173)
* Verharde machtigingen om te voorkomen dat standaardgebruikers de parameters voor de instantieconfiguratie kunnen wijzigen, zoals toegangs-URL&#39;s voor toepassingen, LDAP-instellingen, enz. (NEO-10171)
* Probleem verholpen waarbij gevoelige informatie via stacktraceringen kon worden weergegeven. De details van de fout worden nu het programma geopend in het achterste eind aan een plaats ontoegankelijk van het externe netwerk. (NEO-10176)
* Verharde machtigingen om te voorkomen dat standaardgebruikers de geüploade documenten en/of geëxporteerde pakketten van een beheerder kunnen bekijken. (NEO-10170)

**Verbeteringen**

* **LINE-kanaal - architectuurverbetering**: Net als bij alle andere kanalen in Adobe Campaign wordt het LINE-kanaal nu ondersteund voor alle implementatietypen: gehost, hybride en op locatie.
* **Volgorde automatisch genereren**: Het mechanisme voor het genereren van id&#39;s is verbeterd en vergroot de levensduur van campagneinstanties met grote volumes objecten. Raadpleeg dit [technische artikel](https://helpx.adobe.com/campaign/kb/sequence_auto_generation.html)voor meer informatie.

**Overige wijzigingen**

* Er is een nieuwe modus beschikbaar voor het importeren van pakketten via de opdrachtregel, zodat ronde afhankelijkheden mogelijk zijn (niet aanbevolen voor grote pakketten). Zie de sectie &#39;Technische ontwikkelingen&#39; voor meer informatie. (NEO-8979)
* Verbeterde prestaties voor een grote hoeveelheid gegevens die in Teradata worden geladen en verholpen een probleem waardoor de juiste waarde van de gegevens die in het logbestand zijn verwerkt, niet kon worden weergegeven. (NEO-10429)
* Het importeren van soorten publiek vanuit Audience Manager werkt nu met gesplitste bestanden. Eerder werd alleen het laatste bestand van het segment geïmporteerd door de technische workflow van importSharedAudience. (NEO-10156)
* In Windows is het standaardinstallatiepad van de Campagneserver gewijzigd. Wanneer u de installatie van de 64-bits versie start, is het standaardinstallatiepad nu: **C:\Program Files\Adobe\Adobe Campaign Classic v7** in plaats van **C:\Program Files (x86)\Adobe\Adobe Campaign Classic v7**
* De standaard MX regels zijn verbeterd om meer domeinen te omvatten en productie te optimaliseren.
* Afgedwongen toegangsbeperkingen voor de SOAP-aanroep van de implementatiewizard (xtk:serverOptions#SaveOptions).
* De verouderde bibliotheek weka.jar is verwijderd en de OpenSSL-bibliotheek is bijgewerkt voor optimalisatie van de beveiliging.
* Verbeterde technische workflow voor facturering om uitvoeringen van instanties te beveiligen.
* De mogelijkheid voor beheerders om het wachtwoord van een operator in te stellen of opnieuw in te stellen, is hersteld. Klik hiertoe met de rechtermuisknop op een operator, selecteer **[!UICONTROL Actions]** > **[!UICONTROL Reset password]** en stel het nieuwe wachtwoord van de operator in. We raden operatoren aan hun wachtwoord te wijzigen wanneer ze opnieuw verbinden. Raadpleeg de [gedetailleerde documentatie](../../production/using/lost-password.md)voor meer informatie.
* Ter ondersteuning van de nieuwe functie voor meervoud in Adobe Target kan nu een nieuwe parameter &quot;at_property&quot; aan URL&#39;s worden toegevoegd wanneer u opties en externe accounts voor de integratie met Target configureert. De waarde die voor deze parameter moet worden gebruikt, vindt u in Adobe Target en wordt door Campagne gebruikt bij het uitvoeren van aanroepen naar Doel. Raadpleeg de [gedetailleerde documentatie](../../integrations/using/inserting-a-dynamic-image.md)voor meer informatie.
* U kunt nu een standaard openingspagina opgeven die moet worden geopend wanneer u klikt op een afbeelding die wordt geleverd door Adobe Target. Als u voorheen op die afbeelding klikte, werd de standaardafbeeldingsset gebruikt bij het maken van de e-mail. Raadpleeg de [gedetailleerde documentatie](../../integrations/using/inserting-a-dynamic-image.md)voor meer informatie.
* Het selectievakje **SMPP-sporen** inschakelen in de externe account is toegevoegd om de uitvoer te forceren. Raadpleeg de [gedetailleerde documentatie](../../delivery/using/sms-channel.md#creating-an-smpp-external-account)voor meer informatie.

**Technische ontwikkelingen**

queryDef

queryDef is gewijzigd met betrekking tot de &quot;orderBy&quot;clausule. Vóór de wijziging zou de primaire sleutel van de betwiste lijst impliciet aan de &quot;orderBy&quot;clausules worden toegevoegd. Bij sommige database-engines (ten minste postgressief) wordt het gebruik van indexen voorkomen (alle velden van de orderBy-component moeten door dezelfde index worden gedekt). Als u van dit gedrag afhankelijk was, zult u de primaire sleutel in uw &quot;orderBy&quot;clausule uitdrukkelijk moeten toevoegen.

Bijvoorbeeld, als u de volgende vraag hebt:

```
<queryDef operation="select" schema="xtk:job" startPath="/" xtkschema="xtk:queryDef">
  <select>
     <node expr="@id"/>
   </select>
   <orderBy>
     <node expr="@logDate"/>
   </orderBy>
</queryDef>`
```

Het zou impliciet worden overhandigd als (vóór de wijzigingen van 18.4):

```
<queryDef operation="select" schema="xtk:job" startPath="/" xtkschema="xtk:queryDef">
  <select>
     <node expr="@id"/>
   </select>
   <orderBy>
      <node expr="@logDate"/>
      <node expr="@id"/> <!-- implicitely added before 18.4, you can add it manually on your query, if you relied on this implicit order clauses --!>
   </orderBy>
</queryDef>
```

urlEncode, functie

De JavaScript-functie urlEncode werkt niet correct voor niet-ASCII-tekens. Deze is gecorrigeerd en werkt nu met alle Unicode-tekens (inclusief Japanse tekens). Als u op het gedrag &quot;urlEncode&quot;voor niet karakter ASCII vertrouwde, zult u uw code moeten aanpassen.

Nieuwe modus voor importeren pakket

Er is een nieuwe modus beschikbaar voor het importeren van pakketten via de opdrachtregel, zodat ronde afhankelijkheden mogelijk zijn (niet aanbevolen voor grote pakketten). De bestaande functionaliteit blijft behouden. Voor dergelijke pakketten met circulaire afhankelijkheden is een nieuwe markering **-usejs** toegevoegd aan het importeren van het opdrachtregelpakket. Wanneer uitgevoerd, zal het JSEngine als gebruiken wanneer de pakketinvoer van de interface wordt uitgevoerd.

```
nlserver package -instance:fresh -import:sup-packInstallTest.xml -verbose -usejs
```

**Patches**

* Oplossing voor een synchronisatieprobleem bij het repliceren van bezorgings- en trackinglogs van Adobe Campaign Standard naar Adobe Campaign Classic. (NEO-10023)
* Probleem verholpen met de verwerking van de tabellen met fouten en logbestanden in Teradata toen een ETL-workflow werd hervat na een fout bij een snelle laadbewerking. De tabellen Error en Log worden nu op de juiste wijze verwijderd telkens wanneer de workflow wordt hervat. (NEO-10672)
* Probleem verholpen na upgrade waarbij het Hive-pakket automatisch werd geïnstalleerd (nodig voor Hadoop) als het FDA-pakket is geïnstalleerd. (NEO-10592)
* Probleem verholpen waarbij ongeldige domeinen werden behandeld als een **niet-gedefinieerde** fout. (NEO-10248)
* Probleem verholpen waarbij logboekbestanden in de tabel deliveryLogStats werden gedupliceerd bij het verzenden van Anroid-pushleveringen. (NEO-10234)
* Probleem verholpen waarbij bepaalde streepjescode-indelingen niet leesbaar werden door streepjescodescanners. (NEO-10125)
* Probleem verholpen met de JavaScript-functie urlEncode wanneer niet-ASCII-tekens werden gebruikt. Zie de sectie &#39;Technische ontwikkelingen&#39; voor meer informatie. (NEO-10123)
* Probleem verholpen bij het uitvoeren van een query, waaronder sha256-functies in Teradata-databases. (NEO-10119)
* De fouten van het werkschemamegeheugen die in de activiteit SalesForce konden voorkomen wanneer het gebruiken van zeer grote lijsten SalesForce. (NEO-9900)
* Probleem verholpen met de optie **Generate complement** bij het activeren van workflowactiviteiten bij gebruik van FDA. (NEO-9878)
* Probleem verholpen waarbij de metriek **Verwerkt** en **Succes** niet werd bijgewerkt op het marketingexemplaar wanneer gebruik werd gemaakt van mid-sourcing. (NEO-9454)
* Regels inzake vaste interactienon-repropositie wanneer in het platform in totaal meer dan 10.000 aanbiedingen worden gedaan (NEO-9352)
* Probleem verholpen waarbij het doel van een levering niet kon worden opgegeven bij gebruik van een extern XML-bestand. (NEO-9312)
* Probleem verholpen dat tot workflowfouten kon leiden wanneer een hypothese over een aanbieding werd uitgevoerd en de status van het voorstel werd bijgewerkt. (NEO-9304)
* Fouten verholpen die optraden tijdens de afleveringsanalyse bij het gebruik van drukregels op basis van een kenmerk van de Android-aflevering. (NEO-9202)
* Probleem verholpen bij het sorteren op kolommen in de lijst met ontvangers die tot prestatieproblemen kunnen leiden. Zie de sectie &#39;Technische ontwikkelingen&#39; hieronder voor meer informatie over de wijzigingen queryDef. (NEO-9042)
* Probleem verholpen waarbij de koppelingen in een goedkeurings-e-mail zouden kunnen verwijzen naar een onjuiste aanmeldings-URL, vooral wanneer u een aanmeldingstype voor een id met licentie gebruikt. (NEO-9011)
* Probleem opgelost waarbij onjuiste datums werden weergegeven in de datumkiezers van rapporten voor bepaalde tijdzones. (NEO-9007)
* Probleem verholpen waarbij het doel van een uitgaande database niet kon worden weergegeven bij gebruik van een FDA SQL-database. (NEO-8924)
* Probleem verholpen waardoor de MS Dynamics CRM-connector er niet in slaagde gegevens te verzamelen gedurende de eerste 7 dagen van de maand. (NEO-8803)
* Probleem verholpen met integratie met Analytics waardoor gebruikers internationale tekens niet konden opnemen. (NEO-8719)
* Probleem opgelost waarbij workflowbewerking zonder de juiste rechten mogelijk was. (NEO-8708)
* Probleem verholpen met FDA via HTTP&#39;s bij gebruik van Message Center in een hybride architectuur, wat leidde tot het neerzetten of het verlies van verbinding (timeout). (NEO-8438)
* Workflowfouten die optraden bij incrementele queryactiviteit voor negatieve id&#39;s. Dit probleem is nu opgelost. (NEO-8229)
* Probleem verholpen dat tot de weergave van dubbele schuifbalken in bepaalde schermen kan leiden. (NEO-8208)
* Probleem verholpen die ertoe leidde dat een foutbericht werd weergegeven wanneer de wizard voor updatedatabasestructuur werd uitgevoerd. De PostUpgrade voert een nieuwe naam van indexen uit met namen die langer zijn dan 30. Houd er rekening mee dat voor grote tabellen de indexvervanging tijd in beslag neemt. (NEO-7983)
* Probleem verholpen waarbij trackinglogboeken niet correct werden gesynchroniseerd van de uitvoeringsinstantie van het Centrum van het Bericht om instantie te besturen. (NEO-7286)
* Oplossing voor een prestatieprobleem met de activiteit van de aanbiedingsverrijking. (NEO-7263)
* Probleem verholpen waarbij de functie DaysAgo niet kon worden gebruikt bij het opvragen van een Redshift-database via FDA. (NEO-7099)
* Oplossing voor een regressie in gegevensbeheer die het maken van indexen op verrijkingsachtige werkstroomactiviteiten verhinderde.
* Probleem opgelost dat zich kon voordoen bij het maken van externe bronnen met de titel @id
* Probleem verholpen die kan optreden wanneer gecomprimeerde bestanden worden geüpload via een FTP-server of wanneer bestanden met jokertekens in de bestandsnaam worden geüpload.
* Probleem verholpen met lange opsommingen van basistypen in externe aangepaste bronnen die zijn gemaakt in Campagnestandaard.
* Probleem verholpen dat ertoe kon leiden dat SMS werd verzonden, zelfs wanneer de verbinding met de provider niet tot SMS-verlies leidde.
* Probleem verholpen waarbij een SMTP-verbinding voor onbepaalde tijd vastliep.
* Probleem verholpen met druktypologische regels tijdens de voorbereiding van berichten bij het gebruik van een LIJN-toewijzing of bij het filteren en aanwijzen van schema&#39;s die verschillen.
