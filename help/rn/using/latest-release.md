---
solution: Campaign Classic
product: campaign
title: Laatste release
description: Nieuwste opmerkingen bij de release van Campaign Classic
feature: Overview
role: Business Practitioner
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
translation-type: tm+mt
source-git-commit: abd5c7430c3f7a1a056a014ad46a0b94157e259f
workflow-type: tm+mt
source-wordcount: '921'
ht-degree: 97%

---

# Laatste release{#latest-release}

Deze pagina bevat nieuwe mogelijkheden, verbeteringen en oplossingen die worden geleverd met de **nieuwste versie van de Campaign Classic-releasekandidaat**.

>[!NOTE]
>
>Campagne **General Availability (GA)-builds** zijn: [[!DNL Gold Standard] 11 release](../../rn/using/gold-standard.md#gs-11) en [Campagne 20.2.5 release](../../rn/using/release--20-2.md).

## ![](assets/do-not-localize/blue_2.png) Release 21.1.2 - build 9282 {#release-21-1-2-build-9282}

_15 april 2021_

* Het wachtwoordbeheer is verbeterd en de beveiliging is geoptimaliseerd.
* Probleem opgelost waarbij MTA vastliep.

## ![](assets/do-not-localize/red_2.png) Release 21.1.1 - build 9277 {#release-21-1-1-build-9277}

_22 februari 2021_

**Verbeterde beveiliging**

* Het mechanisme voor consoleverificatie is verbeterd om de beveiliging te optimaliseren. (NEO-26944)
* Er is een beveiligingsprobleem opgelost ter versterking van de bescherming tegen SSRF-aanvallen (Server Side Request Forgery). (NEO-28532)

**Compatibiliteitsupdates**

De volgende systemen worden nu ondersteund met Campaign:

* Salesforce-API-versie 49 wordt nu ondersteund bij gebruik van het externe Salesforce CRM-account.

**Afgeschafte functies**

Het rapport **Technical Deliverability Monitoring** is nu afgeschaft.

Meer informatie vindt u op de pagina [Afgeschafte en verwijderde functies](../../rn/using/deprecated-features.md).

**Verbeteringen**

**Email Feedback Service (EFS)** is een schaalbare service die rechtstreeks feedback van de Enhanced MTA vastlegt, zodat de rapporteringsnauwkeurigheid wordt verbeterd. Deze functie wordt uitgebracht als een persoonlijke bètaversie en wordt in toekomstige versies geleidelijk beschikbaar gemaakt voor alle klanten.

* Alle categorieën feedback worden nu vastgelegd voor volledige en nauwkeurige rapportage.
* De berekening van de Geleverd-indicator is nu gebaseerd op realtimefeedback van de Enhanced MTA voor verbeterde nauwkeurigheid en reactiviteit.
* EFS lost het probleem van vertragingen bij het rapporteren van synchrone soft bounces op.

Raadpleeg de [gedetailleerde documentatie](../../delivery/using/sending-with-enhanced-mta.md#efs) voor meer informatie.
Als u geïnteresseerd bent in deelname aan deze gesloten bèta, vult u dit [formulier](https://forms.office.com/Pages/ResponsePage.aspx?id=Wht7-jR7h0OUrtLBeN7O4Rol2vQGupxItW9_BerXV6VUQTJPN1Q5WUI4OFNTWkYzQjg3WllUSDAxWi4u) in. We nemen dan contact met u op.

**Overige wijzigingen**

* De overdrachtsnelheid is verbeterd voor grote trackinglogboeken door compressie te gebruiken.
* De workflowheatmap is verbeterd om time-outs te voorkomen bij het uitvoeren van workflows met meerdere activiteiten. (NEO-27423).
* Er is een probleem opgelost waarbij een aanbieding nog kon worden ingediend als de einddatum was verstreken. Campaign Classic houdt nu rekening met de volledige tijdstempel van de einddatum in plaats van alleen met de datum. (NEO-27590)
* De Google+-koppeling is verwijderd uit het gedeelte waar u **koppelingen voor het delen op sociale media** kunt aanpassen.
* Er is een probleem opgelost na de implementatie van een foutoplossing in de vorige release. Er is een controle voor de hostnaam toegevoegd bij het verbinden via SSL/TLS. Sms-berichten konden hierdoor voorheen niet worden verzonden. De hostnaamverificatie is uitgeschakeld voor de meeste protocollen zoals POP3, sms en HTTP met proxy, en de certificaatcontrole voor het externe sms-account is verbeterd met drie waarden (NEO-29581). [Meer informatie](../../delivery/using/sms-protocol.md#skip-tls)

**Patches**

* Er is een probleem opgelost waarbij de sneltoetsen Tab, Enter en Escape niet werkten op het nieuwe aanmeldingsscherm.
* Er is een probleem met vernieuwen opgelost waarbij de naam van een nieuwe workflow na het opslaan werd vervangen door de standaardwaarde (NEO-26106).
* Er is een probleem opgelost dat optrad tijdens het uitvoeren van workflows waarbij een nieuw veld werd toegevoegd als onderdeel van een **verrijkingsactiviteit** voorafgaand aan een **verzendingsactiviteit** met behulp van de doeltoewijzing **External file**: er werden ongewenste velden toegevoegd aan de doeltoewijzing **External file**. (NEO-27687)
* Er is een probleem opgelost waarbij sommige tekens in de broncode werden gewijzigd wanneer een webapplicatie die eerder was gemaakt en opgeslagen, opnieuw werd geopend. (NEO-27597)
* Er is een probleem opgelost dat zich kon voordoen bij de upgrade naar een build met het nieuwe handtekeningmechanisme voor het bijhouden van koppelingen (vanaf build 19.1.4 en Campaign 20.2): wanneer verschillende sjablonen aan een gebeurtenis waren gekoppeld, kon de upgrade ertoe leiden dat de verkeerde sjabloon werd geselecteerd tijdens het verzenden van het transactionele bericht. (NEO-28326)
* Er is een probleem opgelost waarbij de MTA niet meer reageerde en geen verzendingen kon verwerken tenzij deze opnieuw werd gestart. (NEO-27455)
* Er is een probleem opgelost met het tijdstempelbeheer van een MSSQL-database tijdens het bulksgewijs laden van een kolom van het type Datum/tijd.
* Er is een probleem opgelost met een workflowquery bij het gebruik van Redshift-xtk-functies. SubDays, SubSeconds, SubMinutes en SubHours accepteren nu beide Redshift-tijdstempeltypen (NEO-24962).
* Er is een probleem opgelost waarbij een scriptfoutbericht werd weergegeven bij een voorvertoning van een rapport met anonieme toegang. (NEO-27081)
* Er is een probleem opgelost waarbij het geheugengebruik op de server werd verminderd tijdens het uitvoeren van de verzendingsanalyse.
* Er is een probleem opgelost waardoor de instantie mogelijk niet werkte wanneer specifieke complexe query&#39;s werden uitgevoerd.
* Er is een probleem opgelost waarbij de technische workflow **Synchronizing Twitter pages** mogelijk niet werd uitgevoerd. (NEO-28634)
* Er is een probleem opgelost waarbij soms een foutbericht werd weergegeven voor de functie decryptPassword tijdens een poging om op Twitter te publiceren met de verzendingssjabloon **Tweet (twitter)**. (NEO-28216)
* Er is een probleem opgelost dat optrad bij het gebruik van een **Javascript**-activiteit om een HTTP-aanvraag in een workflow uit te voeren. De aanroep mislukte met de volgende fout (NEO-29146) na het bepalen van het poortnummer in de hostnaam:

```
IOB-090020 Error in SSL library: 'IOB-090013 error:14090086:SSL routines:ssl3_get_server_certificate:certificate verify failed (code 336134278)'
```

* Er is een probleem opgelost waardoor geen nieuwe verzendingen met personalisatie van doelgegevens konden worden verzonden (NEO-30323).
* Er is een probleem opgelost waarbij verschillende crashes optraden in de marketinginstantie waardoor dumpbestanden werden veroorzaakt.
* Er is een probleem opgelost waarbij de **Tracking**-workflow mislukte met de volgende fout (NEO-25206):

```
There is no index on the sourceId field of the 'NmsTrackingLogRcp' table required for the current Web tracking mode. Please add this index.
```

* Er is een probleem opgelost dat optrad bij het maken en opslaan van een verzending op het tabblad **Targeting &amp; Workflow** van een campagne: de voorvertoning mislukte met de volgende fout (NEO-29440):

```
XTK-170024 The temporary 'temp:deliveryEmail-all' schema is not defined in the current context
```

* Er is een probleem opgelost dat optrad bij het instellen van een extern account tussen een marketinginstantie en een Adobe Campaign Standard-instantie of een Campaign Classic-mid-sourcinginstantie, en het gebruiken van de optie DisableFOH2=1. Bij het gebruik van de optie DisableFOH2=1 in het externe account werden de verbindingen niet correct gesloten, wat resulteerde in de volgende fout (NEO-26258):

```
The maximum number of connections has been reached (50) by connections pool 'nms:extAccount:acsDefaultRelayAccount XXX'. The server is overloaded. Please try again later.
```

* Er is een sms-probleem opgelost waarbij verbindingsproblemen optraden tussen de server en de provider. De verbinding werd vervolgens door de onderliggende MTA automatisch uitgeschakeld. Adobe Campaign Classic deed geen poging om verbinding te maken met deze falende verbinding zolang er geen nieuwe onderliggende MTA werd gestart.
