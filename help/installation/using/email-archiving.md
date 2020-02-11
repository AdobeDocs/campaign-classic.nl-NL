---
title: E-mailarchivering
seo-title: E-mailarchivering
description: E-mailarchivering
seo-description: null
page-status-flag: never-activated
uuid: a5ed0659-be61-4d73-98e7-db3da24d92f3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: additional-configurations
discoiquuid: d6467875-949b-4b47-940f-620efd4db5e0
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 5b9c57b3cba0e8c24300396c2abac613f6e1193a

---


# E-mailarchivering{#email-archiving}

U kunt Adobe Campaign zodanig configureren dat een kopie van de e-mails die u van uw platform hebt ontvangen, bewaard blijft.

Adobe Campaign zelf beheert echter geen gearchiveerde bestanden. Het laat u toe om de berichten van uw keus naar een specifiek adres te verzenden, van waar zij kunnen worden verwerkt en worden gearchiveerd gebruikend een extern systeem.

Hiervoor worden .eml-bestanden die overeenkomen met de verzonden e-mails, overgebracht naar een externe server, zoals een SMTP-e-mailserver. De archiveringsbestemming is een BCC e-mailadres (onzichtbaar voor de leverende ontvangers) dat u moet specificeren.

## Aanbevelingen en beperkingen {#recommendations-and-limitations}

* De functie voor archivering van e-mail is optioneel. Controleer uw licentieovereenkomst.
* Voor **gehoste en hybride architecturen** neemt u contact op met uw accountmanager om deze te activeren. Het BCC-adres van uw keuze moet worden opgegeven aan het Adobe-team dat het voor u zal configureren.
* Voor **on-premise installaties**, volg de richtlijnen hieronder om het te activeren - zie het [Activating email archiving (op gebouw)](#activating-email-archiving--on-premise-) en het [Vormen van BCC e-mailadres (op gebouw)](#configuring-the-bcc-email-address--on-premise-) secties.
* U kunt slechts één BCC-e-mailadres gebruiken.
* Zodra e-mail BCC wordt gevormd, zorg ervoor de eigenschap in het leveringsmalplaatje of in de levering door de **[!UICONTROL Archive emails]** optie wordt toegelaten. Zie [deze sectie](../../delivery/using/sending-messages.md#archiving-emails)voor meer informatie.
* Er wordt alleen rekening gehouden met e-mailberichten die zijn verzonden, maar met bedragen.
* Het e-mailarchiveringssysteem is gewijzigd met Adobe Campaign 17.2 (build 8795). Als u al gebruikmaakte van e-mailarchivering, moet u handmatig een upgrade uitvoeren naar het nieuwe e-mailarchiveringssysteem (BCC). Zie de sectie [Bijgewerkt e-mailarchiveringssysteem (BCC)](#updated-email-archiving-system--bcc-) voor meer informatie.

## E-mailarchivering activeren (op locatie) {#activating-email-archiving--on-premise-}

Volg onderstaande stappen om BCC e-mailarchivering te activeren wanneer Adobe Campagne op locatie is geïnstalleerd.

### Lokale map {#local-folder}

Als u het overbrengen van verzonden e-mails naar een BCC-e-mailadres wilt inschakelen, moeten exacte onbewerkte kopieën van verzonden e-mails eerst worden opgeslagen als .eml-bestanden naar een lokale map.

Het pad voor de lokale map moet worden opgegeven in het bestand **config-`<instance>`.xml** , vanuit de configuratie. Bijvoorbeeld:

```
<mta dataLogPath="C:\emails">
```

>[!NOTE]
>
>Het is de verantwoordelijkheid van het team dat het project implementeert om ervoor te zorgen dat de beveiligingsinstellingen toegang verlenen tot de map die is gedefinieerd via de **parameters dataLogPath** .

Het volledige pad is als volgt: **`<datalogpath>  YYYY-MM-DDHHh`**. De datum en de tijd worden geplaatst volgens de klok van de server MTA (UTC). Bijvoorbeeld:

```
C:\emails\2018-12-02\13h
```

De naam van het archiefbestand is **`<deliveryid>-<broadlogid>.eml`** wanneer de status van de e-mails niet is **[!UICONTROL Sent]**. Nadat de status is gewijzigd in **[!UICONTROL Sent]**, wordt de bestandsnaam **`<deliveryid>-<broadlogid>-sent.eml`**. Bijvoorbeeld:

```
C:\emails\2018-12-02\13h\4012-8040-sent.eml
```

>[!NOTE]
>
>In een mid-sourcing-instantie bevindt de directory voor de gearchiveerde e-mails zich op de mid-sourcing-server.
>
>De deliveryID en de broadlogID komen van de mid-sourcingsserver wanneer de status van de e-mails niet wordt verzonden. Zodra de status is veranderd in **[!UICONTROL Sent]**, komen deze IDs van de marketing server.

### Parameters {#parameters}

Nadat het lokale mappad is gedefinieerd, voegt u de volgende elementen toe en bewerkt u deze naar wens in het **config-`<instance name>.xml`**bestand. Hieronder ziet u de standaardwaarden:

```
<archiving autoStart="false" compressionFormat="0" compressBatchSize="10000"
           archivingType="0" expirationDelay="2" purgeArchivesDelay="7"
           pollDelay="600" acquireLimit="5000" smtpNbConnection="2"/>
```

* **compressionFormat**: die wordt gebruikt bij het comprimeren van de .eml-bestanden. De mogelijke waarden zijn:

   **0**: geen compressie (standaardwaarde)

   **1**: compressie (.zip-indeling)

* **compressBatchSize**: Aantal eml-bestanden dat aan een archief is toegevoegd (.zip-bestand).
* **archivingType**: te gebruiken archiveringsstrategie. De mogelijke waarden zijn:

   **0**: Raw-kopieën van verzonden e-mailberichten worden opgeslagen in de indeling .eml naar de map **dataLogPath** (standaardwaarde). Een archiveringskopie van het **`<deliveryid>-<broadlogid>-sent.eml`** bestand wordt opgeslagen in de map **dataLogPath/archives** . Het pad naar het verzonden e-mailbestand wordt **`<datalogpath>archivesYYYY-MM-DDHHh <deliveryid>-<broadlogid>-sent.eml`**.

   **1**: Raw-kopieën van verzonden e-mailberichten worden opgeslagen in de indeling .eml naar de map **dataLogPath** en via SMTP naar het BCC-e-mailadres verzonden. Nadat de e-mailkopieën naar het BCC-adres zijn verzonden, wordt de naam van het archiefbestand gewijzigd **`<deliveryid>-<broadlogid>-sent-archived.eml`** en wordt het bestand verplaatst naar de map **dataLogPath/archives** . Het pad naar het verzonden en door BCC gearchiveerde e-mailbestand is nu **`<datalogpath>archivesYYYY-MM-DDHHh<deliveryid>- <broadlogid>-sent-archived.eml`**.

* **expirationDelay**: aantal dagen dat .eml-bestanden worden bewaard voor archivering. Na die vertraging worden ze automatisch naar de map **dataLogPath/archives** verplaatst voor compressie. .eml-bestanden verlopen standaard na twee dagen.
* **purgeArchivesDelay**: Het aantal dagen dat archiefbestanden worden bewaard in de map **dataLogPath/`<archives>`**. Na die periode worden zij definitief geschrapt. De zuivering begint wanneer MTA wordt begonnen. Standaard wordt het elke zeven dagen uitgevoerd.
* **pollDelay**: controlefrequentie (in seconden) voor nieuwe binnenkomende e-mailberichten naar de map **dataLogPath** . Als deze parameter bijvoorbeeld op 60 is ingesteld, betekent dit dat het archiveringsproces elke minuut door de .eml-bestanden in de **dataLogPath/-`<date and time>`**mappen wordt geleid, indien nodig een leegloop wordt toegepast en dat e-mailkopieën naar het BCC-adres worden verzonden en/of de gearchiveerde bestanden worden gecomprimeerd wanneer dat nodig is.
* **verwervingLimit**: Het aantal eml-bestanden dat tegelijk wordt verwerkt voordat het archiveringsproces opnieuw wordt toegepast volgens de parameter **pollDelay** . Als u bijvoorbeeld de parameter **verwervingLimit** instelt op 100 terwijl de parameter **pollDelay** is ingesteld op 60, worden 100 .eml-bestanden per minuut verwerkt.
* **smtpNbConnection**: Aantal verbindingen SMTP aan het BCC e-mailadres.

Zorg ervoor u deze parameters volgens de e-mailverzendende productie aanpast. Bijvoorbeeld, in een configuratie waar MTA 30.000 e-mail per uur verzendt, kunt u de parameter **pollDelay** aan 600 plaatsen, de parameter **verwervingLimit** aan 5000 en de parameter **smtpNbConnection** aan 2. Het betekent dat met 2 verbindingen SMTP, 5.000 e-mails naar het adres BCC om de 10 minuten zullen worden verzonden.

## Het BCC-e-mailadres configureren (op locatie) {#configuring-the-bcc-email-address--on-premise-}

>[!CAUTION]
>
>Om privacyredenen moeten BCC-e-mails worden verwerkt door een archiveringssysteem dat veilig identificeerbare informatie (PII) kan opslaan.

In het **config-`<instance name>.xml`**dossier, gebruik de volgende parameters om de SMTP e-mailserver te bepalen waarnaar de opgeslagen dossiers zullen worden overgebracht:

```
<archiving smtpBccAddress="" smtpEnableTLS="false" smtpRelayAddress="" smtpRelayPort="25"/>
```

* **smtpBccAddress**: archiveringsdoel
* **smtpEnableTLS**: gebruik maken van een beveiligde SMTP-verbinding (TLS/SSL-protocol)
* **smtpRelayAddress**: relaisadres voor gebruik
* **smtpRelayPort**: relaispoort voor gebruik

>[!NOTE]
>
>Als u een SMTP relais gebruikt, worden de veranderingen in de e-mails die door het relais worden aangebracht niet in het archiveringsproces in aanmerking genomen.
>
>Bovendien kent het relais een **[!UICONTROL Sent]** status toe aan alle e-mails, ook aan die welke niet worden verzonden. Daarom worden alle berichten gearchiveerd.

## Bijgewerkt e-mailarchiveringssysteem (BCC) {#updated-email-archiving-system--bcc-}

>[!CAUTION]
>
>Het e-mailarchiveringssysteem (BCC) is gewijzigd met Adobe Campagne 17.2 (build 8795). Als u een upgrade uitvoert vanaf een oudere build en al gebruikmaakt van e-mailarchiveringsmogelijkheden, moet u de upgrade handmatig uitvoeren naar het nieuwe e-mailarchiveringssysteem (BCC).

U doet dit door de volgende wijzigingen in het **`config-<instance>.xml`** bestand aan te brengen:

1. Verwijder de **parameter zipPath** uit het **`<archiving>`** knooppunt.
1. Stel de parameter **compressionFormat** zo nodig in op **1** .
1. Stel de parameter **archivingType** in op **1**.

Zodra e-mail BCC wordt gevormd, zorg ervoor u de **[!UICONTROL Archive emails]** optie in het leveringsmalplaatje of de levering selecteert. Zie [deze sectie](../../delivery/using/sending-messages.md#archiving-emails)voor meer informatie.

## Aanbevolen procedures {#best-practices}

* **Postvak** BCC-adres: ervoor te zorgen dat het voldoende opvangcapaciteit heeft om alle e-mails die door de MTA worden verzonden, te archiveren.
* **MTA-mutualisatie**: de archiveringsfunctie van BCC werkt op MTA-niveau. Hiermee kunt u elke e-mail dupliceren die door de MTA is verzonden. Aangezien MTA over verscheidene instanties (bijvoorbeeld dev, test, of prod) of zelfs over verscheidene cliënten (in een midsourcingomgeving) kan worden gemutualiseerd, beïnvloedt het opzetten van deze eigenschap veiligheid:

   * Als u een MTA met veelvoudige cliënten deelt en één van hen heeft deze optie geactiveerd, zal deze cliënt tot alle e-mails van de andere cliënten toegang hebben die de zelfde MTA delen. Om een dergelijke situatie te vermijden, gebruikt u een andere MTA voor elke cliënt.
   * Als u zelfde MTA over veelvoudige instanties (ontwikkeling, test, staaf) voor één enkele cliënt gebruikt, zullen de berichten die van alle drie instanties worden verzonden door de dataLogPath optie worden gedupliceerd.

* **E-mails per verbinding**: BCC e-mailarchivering werkt door een verbinding te openen en alle e-mails via die verbinding te verzenden. Adobe raadt u aan om met uw interne technische contactpersoon te controleren hoeveel e-mails worden geaccepteerd voor een bepaalde verbinding. Het verhogen van dit aantal kan een grote invloed op de productie BCC hebben.
* **BCC die IPs** verzendt: BCC-e-mailberichten worden momenteel niet verzonden via de normale MTA-proxy&#39;s. In plaats daarvan is een directe verbinding geopend van de MTA-server naar de e-mailserver van het doel. Dit betekent dat u extra IPs op uw netwerk, afhankelijk van uw configuratie van de e-mailserver kunt moeten whitelist.

