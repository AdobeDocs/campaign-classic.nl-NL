---
solution: Campaign Classic
product: campaign
title: Laatste release
description: Nieuwste opmerkingen bij de release van Campaign Classic
audience: rns
content-type: reference
topic-tags: latest-release-notes
translation-type: tm+mt
source-git-commit: 14513d5ecbfdd5637b764c8f19bc01358e63c130
workflow-type: tm+mt
source-wordcount: '903'
ht-degree: 18%

---


# Laatste release{#latest-release}

Deze pagina bevat nieuwe mogelijkheden, verbeteringen en oplossingen die worden geleverd met de **nieuwste versie van de Campaign Classic-releasekandidaat**.

Voor de Campaign Classic Gold Standard-versie (nieuwste GA-build) [raadpleegt u deze pagina](../../rn/using/gold-standard.md).

## ![](assets/do-not-localize/blue_2.png) Release 21.1.1 - build 9277 {#release-21-1-1-build-9277}

_22 februari 2021_

**Verbeterde beveiliging**

* Het mechanisme van de consoleauthentificatie is verbeterd om veiligheid te optimaliseren. (NEO-26944)
* Er is een beveiligingsprobleem opgelost ter versterking van de bescherming tegen SSRF-aanvallen (Server Side Request Forgery). (NEO-28532)

**Compatibiliteitsupdates**

De volgende systemen worden nu ondersteund met Campaign:

* Salesforce API versie 49 wordt nu ondersteund bij gebruik van de externe account van Salesforce CRM.

**Verouderde functies**

Het **Technical Deliverability Monitoring**-rapport is nu afgekeurd.

Meer informatie vindt u op de pagina [Afgeschafte en verwijderde functies](../../rn/using/deprecated-features.md).

**Verbeteringen**

**E-mailfeedbackservice (EFS)** is een schaalbare service die feedback van de verbeterde MTA rechtstreeks vastlegt, waardoor de rapportnauwkeurigheid wordt verbeterd. Deze functie wordt uitgebracht als een persoonlijke bètaversie en wordt in toekomstige versies geleidelijk beschikbaar gemaakt voor alle klanten.

* Alle categorieën feedback worden nu vastgelegd voor volledige en nauwkeurige rapportage.
* De berekening van de Geleverd-indicator is nu gebaseerd op realtimefeedback van de Enhanced MTA voor verbeterde nauwkeurigheid en reactiviteit.
* EFS lost het probleem van vertragingen bij het rapporteren van synchrone soft bounces op.

Raadpleeg de [gedetailleerde documentatie](../../delivery/using/sending-with-enhanced-mta.md#efs) voor meer informatie.
Als u geïnteresseerd bent in deelname aan deze persoonlijke bètaversie, vult u dit [formulier](https://forms.office.com/Pages/ResponsePage.aspx?id=Wht7-jR7h0OUrtLBeN7O4Rol2vQGupxItW9_BerXV6VUQTJPN1Q5WUI4OFNTWkYzQjg3WllUSDAxWi4u) in en ontvangt u hiervan een melding.

**Overige wijzigingen**

* De overdrachtsnelheid is verbeterd voor grote het volgen logboeken door compressie te gebruiken.
* Workflowwarmteoverzicht is verbeterd om onderbrekingen te voorkomen bij het uitvoeren van workflows met meerdere activiteiten. (NEO-27423).
* Probleem verholpen waarbij een aanbod kon worden ingediend, zelfs als de einddatum was verstreken. Campaign Classic neemt nu de volledige tijdstempel van de einddatum in plaats van alleen de datum in aanmerking. (NEO-27590)
* De Google+-koppeling is verwijderd uit het **sociale netwerk-delende koppelingen**-aanpassingsblok.
* Probleem verholpen na de implementatie van een foutoplossing in de laatste release. Er is een controle toegevoegd op de hostnaam bij het maken van verbinding met SSL/TLS, waardoor SMS-leveringen mislukten. Hostnaamverificatie is uitgeschakeld voor de meeste protocollen zoals POP3, SMS en HTTP met proxy en de certificaatcontrole voor de externe SMS-account is verbeterd met drie waarden (NEO-29581). [Meer informatie](../../delivery/using/sms-protocol.md#skip-tls)

**Patches**

* Probleem verholpen waarbij de sneltoetsen Tab, Enter en Escape niet konden werken op het nieuwe aanmeldingsscherm.
* Probleem verfrissde waarbij de naam van een nieuwe workflow na het opslaan werd vervangen door de standaardwaarde (NEO-26106).
* Probleem verholpen die optrad tijdens het uitvoeren van workflows waarbij een nieuw veld werd toegevoegd als onderdeel van een **Verrijking** activiteit voorafgaand aan een **Delivery** activiteit met behulp van een **External file** target mapping: Er zijn ongewenste velden toegevoegd aan de doeltoewijzing **Extern bestand**. (NEO-27687)
* Probleem verholpen waarbij sommige tekens in de broncode werden gewijzigd wanneer een webtoepassing die eerder is gemaakt en opgeslagen, opnieuw werd geopend. (NEO-27597)
* Oplossing voor een probleem dat zich kon voordoen bij de upgrade naar een build, inclusief het nieuwe handtekeningmechanisme voor het bijhouden van koppelingen (van build 19.1.4 en campagne 20.2): wanneer verschillende sjablonen aan een gebeurtenis zijn gekoppeld, kan de upgrade ertoe leiden dat de verkeerde sjabloon wordt geselecteerd tijdens het verzenden van het transactiebericht. (NEO-28326)
* Probleem opgelost waarbij de MTA niet meer reageerde en geen leveringen kon verwerken tenzij deze opnieuw werden gestart. (NEO-27455)
* Probleem verholpen met een MSSQL-database die te maken had met tijdstempelbeheer tijdens bulklaadbewerkingen voor een kolom van het datetime-type.
* Probleem met workflowquery verholpen bij gebruik van Redshift Xtk-functies. De SubDays, SubSeconds, SubMinutes en SubHours accepteren nu beide tijdstempeltypen voor opnieuw plaatsen (NEO-24962).
* Probleem verholpen waarbij een scriptfoutbericht werd weergegeven bij een voorvertoning van een rapport met anonieme toegang. (NEO-27081)
* Probleem verholpen waarbij het geheugengebruik op de server tijdens de uitvoering van de leveringsanalyse kon worden verminderd.
* Probleem verholpen waardoor de instantie mogelijk niet werkt wanneer wordt geprobeerd specifieke complexe query&#39;s uit te voeren.
* Probleem verholpen waarbij de technische workflow van **Twitter-pagina&#39;s synchroniseren** mogelijk niet wordt uitgevoerd. (NEO-28634)
* Probleem verholpen waarbij een foutbericht kon worden weergegeven met betrekking tot de functie decryptPassword tijdens een poging om op Twitter te publiceren met de leveringssjabloon **Tweet (twitter)**. (NEO-28216)
* Oplossing voor een probleem dat optrad bij het gebruik van een **Javascript**-activiteit om een HTTP-aanvraag in een workflow uit te voeren. Na het bepalen van het havenaantal in de naam van de Gastheer, zou de vraag met de volgende fout (NEO-29146) ontbreken:

```
IOB-090020 Error in SSL library: 'IOB-090013 error:14090086:SSL routines:ssl3_get_server_certificate:certificate verify failed (code 336134278)'
```

* Probleem verholpen waardoor geen nieuwe leveringen met doelgegevensupitalisatie konden worden verzonden.
* Probleem verholpen waarbij verschillende vastlopen optraden in de marketinginstantie die kernbestanden veroorzaakte.
* Probleem verholpen waardoor de **Tracking**-workflow mislukte met de volgende fout (NEO-25206):

```
There is no index on the sourceId field of the 'NmsTrackingLogRcp' table required for the current Web tracking mode. Please add this index.
```

* Oplossing voor een probleem dat optrad bij het maken en opslaan van een levering op het tabblad **Doelstelling &amp; workflow** van een campagne: de voorvertoning zou mislukken met de volgende fout (NEO-29440):

```
XTK-170024 The temporary 'temp:deliveryEmail-all' schema is not defined in the current context
```

* Oplossing voor een fout die optrad bij het instellen van een externe account tussen een marketinginstantie en een Adobe Campaign Standard-instantie of een Campaign Classic mid-sourcing-instantie en het gebruik van de optie &quot;DisableFOH2=1&quot;. Wanneer u de optie &quot;DisableFOH2=1&quot; in de externe account gebruikt, werden de verbindingen niet correct gesloten en worden deze omhoog geplakt, wat resulteert in de volgende fout (NEO-26258):

```
The maximum number of connections has been reached (50) by connections pool 'nms:extAccount:acsDefaultRelayAccount XXX'. The server is overloaded. Please try again later.
```

* Correctie van een fout met SMS toen verbindingsproblemen optraden tussen de server en de provider. De verbinding zou dan automatisch door het kind MTA worden onbruikbaar gemaakt. Adobe Campaign Classic probeert geen verbinding te maken met deze falende verbinding zolang er geen nieuw kind is gestart.
