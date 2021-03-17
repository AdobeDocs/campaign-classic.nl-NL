---
solution: Campaign Classic
product: campaign
title: Serverconfiguratie
description: Meer informatie over best practices voor serverconfiguratie.
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
translation-type: tm+mt
source-git-commit: d88815e36f7be1b010dcaeee51013a5da769b4a8
workflow-type: tm+mt
source-wordcount: '1156'
ht-degree: 3%

---


# Serverconfiguratie {#server-configuration}

## Beveiligingszones configureren

>[!IMPORTANT]
>
>Vanaf build 8977 is de gebruikersinterface van de Zones Self Service niet meer beschikbaar.
>
>* Als u op AWS wordt ontvangen, moet het toevoegen van IP aan de lijst van gewenste personen in Controlebord worden uitgevoerd. Raadpleeg de [desbetreffende documentatie](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/ip-allow-listing-instance-access.html) voor meer informatie.
>* Als u niet op AWS wordt ontvangen, bereik aan het ondersteuningsteam van Adobe om IP aan de lijst van gewenste personen toe te voegen.

>
>
Als u wilt controleren of uw instantie wordt gehost op AWS, voert u de stappen uit die in [deze sectie](https://experienceleague.adobe.com/docs/control-panel/using/faq.html) worden beschreven.

* Zorg ervoor dat de reverse-proxy niet is toegestaan in subNetwork. Als het het geval is, zal **all** verkeer worden ontdekt zoals komend van dit lokale IP, zodat zal worden vertrouwd.

* Gebruik sessionTokenOnly=&quot;true&quot; minimaliseren:

   * Waarschuwing: Als dit attribuut aan waar wordt geplaatst, kan de exploitant aan een **CRSF aanval** worden blootgesteld.
   * Bovendien wordt het sessionToken koekje niet geplaatst met een markering httpOnly, zodat kan sommige cliënt-kant javascript code het lezen.
   * Nochtans vereist het Centrum van het Bericht op veelvoudige uitvoeringscellen sessionTokenOnly: creeer een nieuwe veiligheidsstreek met sessionTokenOnly die aan &quot;waar&quot;wordt geplaatst en voeg **slechts noodzakelijke IP(s)** in deze streek toe.

* Indien mogelijk, plaats allen allowHTTP, showErrors om vals (niet voor localhost) te zijn en hen te controleren.

   * allowHTTP = &quot;false&quot;: exploitanten dwingen HTTPS te gebruiken
   * showErrors = &quot;false&quot;: Hiermee verbergt u technische fouten (waaronder SQL-fouten). Het verhindert het tonen van teveel informatie, maar vermindert het vermogen voor de teller om fouten op te lossen (zonder om meer informatie van een beheerder te vragen)

* Plaats allowDebug aan waar slechts op IPs die door marketing gebruikers/beheerders wordt gebruikt die (in feite voorproef) onderzoeken, webApps en rapporten moeten tot stand brengen. Deze vlag staat deze IPs toe om relaisregels te krijgen die worden getoond en hen te zuiveren.

* Stel allowEmptyPassword, allowUserPassword, allowSQLInjection nooit in op true. Deze kenmerken zijn alleen hier voor een vloeiende migratie vanaf v5 en v6.0:

   * **Operatoren** allowEmptyPasswordlets hebben een leeg wachtwoord. Als dit voor u het geval is, breng al uw exploitanten op de hoogte om hen te vragen om een wachtwoord met een deadline te plaatsen. Als deze deadline is verstreken, wijzigt u dit kenmerk in false.

   * **Operatoren** allowUserPasswordlets verzenden hun gegevens als parameters (zodat deze door apache/IIS/proxy worden geregistreerd). Deze functie is in het verleden gebruikt om het gebruik van de API te vereenvoudigen. U kunt in uw kookboek (of in de specificatie) controleren of sommige derdetoepassingen dit gebruiken. Als dat het geval is, moet u de gebruiker een melding sturen om de manier waarop hij of zij de API gebruikt te wijzigen en deze functie zo snel mogelijk verwijderen.

   * **Met** allowSQLInjectionnlets kan de gebruiker SQL-injecties uitvoeren met behulp van een oude syntaxis. Voer zo snel mogelijk de correcties uit die in [deze pagina](../../migration/using/general-configurations.md) worden beschreven om deze eigenschap aan vals te kunnen plaatsen. U kunt /nl/jsp/ping.jsp gebruiken?zones=true om uw configuratie van de veiligheidsstreek te controleren. Deze pagina toont de actieve status van veiligheidsmaatregelen (die met deze veiligheidsvlaggen worden gegevens verwerkt) voor huidige IP.

* HttpOnly cookie/useSecurityToken: verwijs naar **sessionTokenOnly** vlag.

* Minimaliseer IPs die aan de lijst van gewenste personen wordt toegevoegd: Uit de doos, in veiligheidszones, hebben wij de 3 waaiers voor privé netwerken toegevoegd. Het is onwaarschijnlijk dat u al deze IP adressen zult gebruiken. Bewaar dus alleen die dingen die je nodig hebt.

* webApp/internal-operator bijwerken zodat deze alleen toegankelijk is in localhost.

## Beveiliging bestandsupload

Vraag de operationele gebruikers welk type bestanden zij via de client/webinterface naar de server uploaden. Ter herinnering, bedrijfsbehoeften kunnen zijn:

* afbeeldingen (jpg, gif, png, ...)
* content (zip, html, css, ...)
* marketingactiva (doc, xls, pdf, psd, tiff, ...)
* e-mailbijlage (doc, pdf, ...)
* ETL (txt, csv, tab, ...)
* enz.

Voeg alle tags toe in serverConf/shared/datastore/@uploadAllowlist (geldige reguliere Java-expressie). Meer informatie vindt u op [deze pagina](../../installation/using/configuring-campaign-server.md#limiting-uploadable-files).

Adobe Campaign beperkt de bestandsgrootte niet. Maar u kunt het doen door IIS/Apache te vormen. Meer informatie vindt u in [deze sectie](../../installation/using/web-server-configuration.md).

## Betaling

Raadpleeg [deze pagina](../../installation/using/configuring-campaign-server.md#dynamic-page-security-and-relays) voor meer informatie.

Door gebrek, worden alle dynamische pagina&#39;s automatisch afgelost aan de lokale server van Tomcat van de machine de waarvan module van het Web is begonnen. U kunt er ook voor kiezen om sommige ervan niet door te geven. Als u niet bepaalde Adobe Campaign-modules gebruikt (zoals webapp, interactie, sommige jsp), kunt u deze verwijderen uit de relayregels.

Uit de doos, hebben wij het vermogen gedwongen om eindgebruikersmiddelen te tonen gebruikend http (httpAllowed= &quot;waar&quot;). Aangezien op deze pagina&#39;s sommige PII&#39;s kunnen worden weergegeven (zoals e-mailinhoud, adres), kunt u coupon inwisselen en het aanbod wijzigen, moet u HTTPS op deze paden opnieuw forceren.

Als u verschillende gastheernamen (één openbaar en één voor exploitanten) gebruikt, kunt u het opnieuw verdelen van sommige middelen ook verhinderen nodig door exploitanten over de openbare DNS naam.

## Uitgaande verbindingsbeveiliging

De standaardlijst met URL’s die via JavaScript-codes kunnen worden aangeroepen (workflows, enz.) is beperkt. Als u een nieuwe URL wilt toestaan, moet de beheerder ernaar verwijzen in het bestand [serverConf.xml](../../installation/using/the-server-configuration-file.md).

Er zijn drie modi voor verbindingsbeveiliging:

* **Blokkeren** : alle URL&#39;s die niet bij de lijst van gewenste personen horen, worden geblokkeerd, met een foutbericht. Dit is de standaardwijze na een postupgrade.
* **Toestemming** : alle URL&#39;s die niet bij de lijst van gewenste personen horen, zijn toegestaan.
* **Waarschuwing** : alle URL&#39;s die zich niet op de lijst van gewenste personen bevinden, zijn toegestaan, maar de JS-interpreter geeft een waarschuwing weer, zodat de beheerder deze kan verzamelen. In deze modus worden JST-310027-waarschuwingsberichten toegevoegd.

```
<urlPermission action="warn" debugTrace="true">
  <url dnsSuffix="abc.company1.com" urlRegEx=".*" />
  <url dnsSuffix="def.partnerA_company1.com" urlRegEx=".*" />
  <url dnsSuffix="xyz.partnerB_company1.com" urlRegEx=".*" />
</urlPermission>
```

De nieuwe cliënten zullen de blokkerende wijze gebruiken. Als zij een nieuwe URL willen toestaan, moeten zij hun beheerder contacteren om het aan de lijst van gewenste personen toe te voegen.

Bestaande klanten die uit een migratie komen, kunnen de waarschuwingsmodus een tijdje gebruiken. Ondertussen moeten zij het uitgaande verkeer analyseren alvorens URL toe te laten.

## Opdrachtbeperking (server-kant)

Verschillende opdrachten staan op de zwarte lijst en kunnen niet worden uitgevoerd met de functie execCommand. Een extra-veiligheid wordt verstrekt door een specifieke gebruiker van Unix om externe bevelen uit te voeren. Deze beperking wordt automatisch toegepast op gehoste installaties. Voor installaties op locatie kunt u deze beperking handmatig instellen door de instructies van [deze pagina](../../installation/using/configuring-campaign-server.md#restricting-authorized-external-commands) te volgen. Daarnaast zijn de **[!UICONTROL Script]**- en **[!UICONTROL External task]**-workflowactiviteiten niet beschikbaar (nieuw geïnstalleerde exemplaren).

## Andere configuraties

U kunt extra HTTP-headers toevoegen voor alle pagina&#39;s (zie [deze pagina](../../installation/using/configuring-campaign-server.md#restricting-authorized-external-commands) voor meer informatie):

* U kunt enkele extra kopteksten toevoegen, zoals HSTS, X-FRAME-OPTIONS, CSP..
* U moet ze in een testomgeving testen voordat u ze in de productie toepast.

   >[!IMPORTANT]
   >
   >Adobe Campaign kan worden verbroken door bepaalde kopteksten toe te voegen.

Met Adobe Campaign kunt u een leeg wachtwoord instellen in het element `<dbcnx .../>`. Gebruik deze functie niet.

Adobe Campaign hecht standaard geen sessie aan een specifiek IP, maar u kunt deze activeren om te voorkomen dat de sessie wordt gestolen. U doet dit door in het bestand [serverConf.xml](../../installation/using/the-server-configuration-file.md) het kenmerk checkIPConsistent in te stellen op **true** in het knooppunt `<authentication>`.

Standaard gebruikt Adobe Campaign MTA geen beveiligde verbinding om inhoud naar de SMTP-server te verzenden. U moet deze functie inschakelen (dit kan de snelheid van de levering verlagen). Om dit te doen, plaats **enableTLS** aan **true** in de `<smtp ...>` knoop.

U kunt de levensduur van een sessie in het verificatieknooppunt (kenmerk sessionTimeOutSec) verminderen.
