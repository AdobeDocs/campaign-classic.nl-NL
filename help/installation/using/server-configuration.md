---
solution: Campaign Classic
product: campaign
title: Serverbeveiligingsconfiguratie
description: Meer informatie over best practices voor serverconfiguratie
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: e1aff73a-54fb-444e-b183-df11c9b3df31
translation-type: tm+mt
source-git-commit: ae4f86f3703b9bfe7f08fd5c2580dd5da8c28cbd
workflow-type: tm+mt
source-wordcount: '625'
ht-degree: 3%

---

# Beveiligingsinstellingen van server {#server-configuration}

## Beveiliging bestandsupload

Controleer met operationele gebruikers welk type bestanden zij naar de server uploaden met de Campagne Client Console of de webinterface. Ter herinnering, bedrijfsbehoeften kunnen zijn:

* afbeeldingen (jpg, gif, png, ...)
* content (zip, html, css, ...)
* marketingactiva (doc, xls, pdf, psd, tiff, ...)
* e-mailbijlage (doc, pdf, ...)
* ETL (txt, csv, tab, ...)
* enz.

Voeg alle tags toe in serverConf/shared/datastore/@uploadAllowlist (geldige reguliere Java-expressie). Meer informatie vindt u op [deze pagina](../../installation/using/file-res-management.md).

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
