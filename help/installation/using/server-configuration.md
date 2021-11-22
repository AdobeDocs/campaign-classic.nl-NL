---
product: campaign
title: Serverbeveiligingsconfiguratie
description: Meer informatie over best practices voor serverconfiguratie
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: e1aff73a-54fb-444e-b183-df11c9b3df31
source-git-commit: 4661a65c83f3b9b7da9ea902f387155c5933e59f
workflow-type: tm+mt
source-wordcount: '621'
ht-degree: 3%

---

# Beveiligingsinstellingen van server {#server-configuration}

![](../../assets/v7-only.svg)

## Beveiliging bestandsupload

Controleer met operationele gebruikers welk type bestanden zij naar de server uploaden met de Campagne Client Console of de webinterface. Ter herinnering, bedrijfsbehoeften kunnen zijn:

* afbeeldingen (jpg, gif, png, ...)
* content (zip, html, css, ...)
* marketingactiva (doc, xls, pdf, psd, tiff, ...)
* e-mailbijlage (doc, pdf, ...)
* ETL (txt, csv, tab, ...)
* enz.

Voeg alle tags toe in serverConf/shared/datastore/@uploadAllowlist (geldige reguliere Java-expressie). Meer informatie in [deze pagina](../../installation/using/file-res-management.md).

Adobe Campaign beperkt de bestandsgrootte niet. Maar u kunt het doen door IIS/Apache te vormen. Meer informatie in [deze sectie](../../installation/using/web-server-configuration.md).

## Betaling

Zie [deze pagina](../../installation/using/configuring-campaign-server.md#dynamic-page-security-and-relays) voor meer informatie .

Door gebrek, worden alle dynamische pagina&#39;s automatisch afgelost aan de lokale server van Tomcat van de machine de waarvan module van het Web is begonnen. U kunt er ook voor kiezen om sommige ervan niet door te geven. Als u niet bepaalde Adobe Campaign-modules gebruikt (zoals webapp, interactie, sommige jsp), kunt u deze verwijderen uit de relayregels.

Uit de doos, hebben wij het vermogen gedwongen om eindgebruikersmiddelen te tonen gebruikend http (httpAllowed= &quot;waar&quot;). Aangezien op deze pagina&#39;s sommige PII&#39;s kunnen worden weergegeven (zoals e-mailinhoud, adres), kunt u coupon inwisselen en het aanbod wijzigen, moet u HTTPS op deze paden opnieuw forceren.

Als u verschillende gastheernamen (één openbaar en één voor exploitanten) gebruikt, kunt u het opnieuw verdelen van sommige middelen ook verhinderen nodig door exploitanten over de openbare DNS naam.

## Uitgaande verbindingsbeveiliging

De standaardlijst met URL’s die via JavaScript-codes kunnen worden aangeroepen (workflows, enz.) is beperkt. Als u een nieuwe URL wilt toestaan, moet de beheerder ernaar verwijzen in het dialoogvenster [serverConf.xml, bestand](../../installation/using/the-server-configuration-file.md).

Er zijn drie modi voor verbindingsbeveiliging:

* **Blokkeren** : alle URL&#39;s die niet bij de lijst van gewenste personen horen, worden geblokkeerd, met een foutbericht. Dit is de standaardwijze na een postupgrade.
* **Permissief** : alle URL&#39;s die niet bij de lijst van gewenste personen horen, zijn toegestaan.
* **Waarschuwing** : alle URL&#39;s die zich niet op de lijst van gewenste personen bevinden, zijn toegestaan, maar de JS-interpreter geeft een waarschuwing weer, zodat de beheerder ze kan verzamelen. In deze modus worden JST-310027-waarschuwingsberichten toegevoegd.

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

Verschillende opdrachten staan op de zwarte lijst en kunnen niet worden uitgevoerd met de functie execCommand. Een extra-veiligheid wordt verstrekt door een specifieke gebruiker van Unix om externe bevelen uit te voeren. Deze beperking wordt automatisch toegepast op gehoste installaties. Voor installaties op locatie kunt u deze beperking handmatig instellen door de instructies van [deze pagina](../../installation/using/configuring-campaign-server.md#restricting-authorized-external-commands). Daarnaast **[!UICONTROL Script]** en **[!UICONTROL External task]** workflowactiviteiten zijn niet beschikbaar (nieuw geïnstalleerde instanties).

## Andere configuraties

U kunt extra HTTP-headers toevoegen voor alle pagina&#39;s (zie voor meer informatie [deze pagina](../../installation/using/configuring-campaign-server.md#restricting-authorized-external-commands)):

* U kunt enkele extra kopteksten toevoegen, zoals HSTS, X-FRAME-OPTIONS, CSP..
* U moet ze in een testomgeving testen voordat u ze in de productie toepast.

   >[!IMPORTANT]
   >
   >Adobe Campaign kan worden verbroken door bepaalde kopteksten toe te voegen.

Met Adobe Campaign kunt u een leeg wachtwoord instellen in het dialoogvenster `<dbcnx .../>` element. Gebruik deze functie niet.

Adobe Campaign hecht standaard geen sessie aan een specifiek IP, maar u kunt deze activeren om te voorkomen dat de sessie wordt gestolen. Om het te doen, in [serverConf.xml, bestand](../../installation/using/the-server-configuration-file.md), stelt u het kenmerk checkIPConsistent in op **true** in de `<authentication>` knooppunt.

Standaard gebruikt Adobe Campaign MTA geen beveiligde verbinding om inhoud naar de SMTP-server te verzenden. U moet deze functie inschakelen (dit kan de snelheid van de levering verlagen). Om dit te doen, stelt u **enableTLS** tot **true** in de `<smtp ...>` knooppunt.

U kunt de levensduur van een sessie in het verificatieknooppunt (kenmerk sessionTimeOutSec) verminderen.
