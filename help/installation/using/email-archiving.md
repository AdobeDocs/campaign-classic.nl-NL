---
solution: Campaign Classic
product: campaign
title: E-mailarchivering
description: E-mailarchivering
audience: installation
content-type: reference
topic-tags: additional-configurations
translation-type: tm+mt
source-git-commit: 5fa848d86f951cb9dc40eb7981abea29c1092291
workflow-type: tm+mt
source-wordcount: '1304'
ht-degree: 2%

---


# E-mailBCC {#email-archiving}

U kunt Adobe Campaign zo configureren dat een kopie van de e-mails die u van uw platform hebt ontvangen, bewaard blijft.

Adobe Campaign zelf beheert gearchiveerde bestanden echter niet. Het laat u toe om de berichten van uw keus naar een specifiek adres te verzenden, van waar zij kunnen worden verwerkt en worden gearchiveerd gebruikend een extern systeem.

Hiervoor worden .eml-bestanden die overeenkomen met de verzonden e-mails, overgebracht naar een externe server, zoals een SMTP-e-mailserver. De archiveringsbestemming is een BCC e-mailadres (onzichtbaar voor de leverende ontvangers) dat u moet specificeren.

## Recommendations en beperkingen {#recommendations-and-limitations}

* BCC-functionaliteit voor e-mail is optioneel. Controleer hiervoor uw licentieovereenkomst.
* Neem voor **gehoste en hybride architecturen** contact op met uw accountmanager om deze te activeren. Het BCC e-mailadres van uw keus moet aan het team van de Adobe worden verstrekt die het voor u zal vormen.
* Voor **on-premise installaties**, volg de hieronder richtlijnen om het te activeren - zie [Het activeren van e-mail BCC (op gebouw)](#activating-email-archiving--on-premise-) en [Het vormen van het BCC e-mailadres (op gebouw)](#configuring-the-bcc-email-address--on-premise-) secties.
* U kunt slechts één BCC-e-mailadres gebruiken.
* Zodra e-mail BCC wordt gevormd, zorg ervoor de eigenschap in het leveringsmalplaatje of in de levering door de **[!UICONTROL Email BCC]** optie wordt toegelaten. Zie [deze sectie](../../delivery/using/sending-messages.md#archiving-emails)voor meer informatie.
* Er wordt alleen rekening gehouden met e-mailberichten die zijn verzonden, maar met bedragen.
* Het e-mailarchiveringssysteem is gewijzigd met Adobe Campaign 17.2 (build 8795). Als u al gebruikmaakte van e-mailarchivering, moet u handmatig upgraden naar het nieuwe BCC-systeem voor e-mail. Zie [Verplaatsen naar de nieuwe sectie BCC](#updated-email-archiving-system--bcc-) voor meer informatie.

## E-mail BCC activeren (op locatie) {#activating-email-archiving--on-premise-}

Volg onderstaande stappen om BCC e-mailarchivering te activeren wanneer Adobe Campaign op locatie is geïnstalleerd.

### Lokale map {#local-folder}

Als u het overbrengen van verzonden e-mails naar een BCC-e-mailadres wilt inschakelen, moeten exacte onbewerkte kopieën van verzonden e-mails eerst worden opgeslagen als .eml-bestanden naar een lokale map.

Het pad voor de lokale map moet worden opgegeven in het bestand **config-`<instance>`.xml** uit de configuratie. Bijvoorbeeld:

```
<mta dataLogPath="C:\emails">
```

>[!NOTE]
>
>Het is de verantwoordelijkheid van het team dat het project implementeert om ervoor te zorgen dat de beveiligingsinstellingen toegang verlenen tot de map die is gedefinieerd via de parameters **dataLogPath**.

Het volledige pad is als volgt: **`<datalogpath>  YYYY-MM-DDHHh`**. De datum en de tijd worden geplaatst volgens de klok van de server MTA (UTC). Bijvoorbeeld:

```
C:\emails\2018-12-02\13h
```

De naam van het archiefbestand is **`<deliveryid>-<broadlogid>.eml`** wanneer de status van de e-mails niet **[!UICONTROL Sent]** is. Nadat de status is gewijzigd in **[!UICONTROL Sent]**, wordt de bestandsnaam **`<deliveryid>-<broadlogid>-sent.eml`**. Bijvoorbeeld:

```
C:\emails\2018-12-02\13h\4012-8040-sent.eml
```

>[!NOTE]
>
>In een mid-sourcing-instantie bevindt de directory voor de BCC-e-mails zich op de mid-sourcing-server.
>
>De deliveryID en de broadlogID komen van de mid-sourcingsserver wanneer de status van de e-mails niet wordt verzonden. Zodra de status is gewijzigd in **[!UICONTROL Sent]**, komen deze id&#39;s van de marketingserver.

### Parameters {#parameters}

Nadat het lokale mappad is gedefinieerd, voegt u de volgende elementen toe en bewerkt u deze naar wens in het bestand **config-`<instance name>.xml`**. Hieronder ziet u de standaardwaarden:

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

   **0**: Raw-kopieën van verzonden e-mailberichten worden opgeslagen in de indeling .eml naar de map  **** dataLogPathfolder (standaardwaarde). Een archiveringskopie van het **`<deliveryid>-<broadlogid>-sent.eml`**-bestand wordt opgeslagen in de map **dataLogPath/archives**. Het verzonden pad naar het e-mailbestand wordt **`<datalogpath>archivesYYYY-MM-DDHHh <deliveryid>-<broadlogid>-sent.eml`**.

   **1**: Raw-kopieën van verzonden e-mailberichten worden opgeslagen in de indeling .eml naar de map  **** dataLogPathfolder en worden via SMTP naar het BCC-e-mailadres verzonden. Nadat de e-mailkopieën naar het BCC-adres zijn verzonden, wordt de naam van het archiefbestand **`<deliveryid>-<broadlogid>-sent-archived.eml`** en wordt het bestand verplaatst naar de map **dataLogPath/archives**. Het pad naar het verzonden en door BCC gearchiveerde e-mailbestand is **`<datalogpath>archivesYYYY-MM-DDHHh<deliveryid>- <broadlogid>-sent-archived.eml`**.

* **expirationDelay**: aantal dagen dat .eml-bestanden worden bewaard voor archivering. Na die vertraging worden ze automatisch voor compressie naar de map **dataLogPath/archives** verplaatst. .eml-bestanden verlopen standaard na twee dagen.
* **purgeArchivesDelay**: Het aantal dagen dat archiefbestanden worden bewaard in de  **dataLogPath/`<archives>`** map. Na die periode worden zij definitief geschrapt. De zuivering begint wanneer MTA wordt begonnen. Standaard wordt het elke zeven dagen uitgevoerd.
* **pollDelay**: controleren van de frequentie (in seconden) voor nieuwe inkomende e-mails naar de  **** dataLogPathfolder. Als deze parameter bijvoorbeeld op 60 wordt ingesteld, betekent dit dat het archiveringsproces elke minuut door de .eml-bestanden in de mappen **dataLogPath/`<date and time>`** gaat, indien nodig een zuiveringsbewerking toepast en e-mailkopieën verzendt naar het BCC-adres en/of de gearchiveerde bestanden indien nodig comprimeert.
* **verwervingLimit**: Het aantal eml-bestanden dat tegelijk wordt verwerkt voordat het archiveringsproces opnieuw wordt toegepast volgens de parameter  **** pollDelayout. Als u bijvoorbeeld de parameter **verwervingLimit** instelt op 100 terwijl de parameter **pollDelay** is ingesteld op 60, worden 100 .eml-bestanden per minuut verwerkt.
* **smtpNbConnection**: Aantal verbindingen SMTP aan het BCC e-mailadres.

Zorg ervoor u deze parameters volgens de e-mailverzendende productie aanpast. Bijvoorbeeld, in een configuratie waar MTA 30.000 e-mail per uur verzendt, kunt u **pollDelay** parameter aan 600 plaatsen, **verwervingLimit** parameter aan 5000 en **smtpNbConnection** parameter aan 2. Het betekent dat met 2 verbindingen SMTP, 5.000 e-mails naar het adres BCC om de 10 minuten zullen worden verzonden.

## Het BCC e-mailadres (op gebouw) {#configuring-the-bcc-email-address--on-premise-} vormen

>[!IMPORTANT]
>
>Om privacyredenen moeten BCC-e-mails worden verwerkt door een archiveringssysteem dat veilig identificeerbare informatie (PII) kan opslaan.

In **config-`<instance name>.xml`** dossier, gebruik de volgende parameters om de SMTP e-mailserver te bepalen waarnaar de opgeslagen dossiers zullen worden overgebracht:

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
>Bovendien wijst het relais een **[!UICONTROL Sent]** status aan alle e-mails toe, met inbegrip van die die niet worden verzonden. Daarom worden alle berichten gearchiveerd.

## Naar de nieuwe e-mail-BCC {#updated-email-archiving-system--bcc-} gaan

>[!IMPORTANT]
>
>Het e-mailarchiveringssysteem (BCC) is gewijzigd met Adobe Campaign 17.2 (build 8795). Als u een upgrade uitvoert vanaf een oudere build en al gebruikmaakt van e-mailarchiveringsmogelijkheden, moet u de upgrade handmatig uitvoeren naar het nieuwe e-mailarchiveringssysteem (BCC).

Hiervoor brengt u de volgende wijzigingen aan in het **`config-<instance>.xml`**-bestand:

1. Verwijder de parameter **zipPath** uit de **`<archiving>`** knoop.
1. Stel de parameter **compressionFormat** in op **1** indien nodig.
1. Stel de parameter **archivingType** in op **1**.

Zodra e-mail BCC wordt gevormd, zorg ervoor u **[!UICONTROL Email BCC]** optie in het leveringsmalplaatje of de levering selecteert. Zie [deze sectie](../../delivery/using/sending-messages.md#archiving-emails)voor meer informatie.

## Beste werkwijzen voor BCC via e-mail {#best-practices}

* **Postvak** BCC-adres: ervoor te zorgen dat het voldoende opvangcapaciteit heeft om alle e-mails die door de MTA worden verzonden, te archiveren.
* **MTA-mutualisatie**: de archiveringsfunctie van BCC werkt op MTA-niveau. Hiermee kunt u elke e-mail dupliceren die door de MTA is verzonden. Aangezien MTA over verscheidene instanties (bijvoorbeeld dev, test, of prod) of zelfs over verscheidene cliënten (in een midsourcingomgeving) kan worden gemutualiseerd, beïnvloedt het opzetten van deze eigenschap veiligheid:

   * Als u een MTA met veelvoudige cliënten deelt en één van hen heeft deze optie geactiveerd, zal deze cliënt tot alle e-mails van de andere cliënten toegang hebben die de zelfde MTA delen. Om een dergelijke situatie te vermijden, gebruikt u een andere MTA voor elke cliënt.
   * Als u zelfde MTA over veelvoudige instanties (ontwikkeling, test, staaf) voor één enkele cliënt gebruikt, zullen de berichten die van alle drie instanties worden verzonden door de dataLogPath optie worden gedupliceerd.

* **E-mails per verbinding**: BCC e-mailarchivering werkt door een verbinding te openen en alle e-mails via die verbinding te verzenden. Adobe raadt u aan om met uw interne technische contactpersoon te controleren hoeveel e-mails worden geaccepteerd voor een bepaalde verbinding. Het verhogen van dit aantal kan een grote invloed op de productie BCC hebben.
* **BCC die IPs** verzendt: BCC-e-mailberichten worden momenteel niet verzonden via de normale MTA-proxy&#39;s. In plaats daarvan is een directe verbinding geopend van de MTA-server naar de e-mailserver van het doel. Dit betekent dat u extra IPs aan de lijst van gewenste personen op uw netwerk, afhankelijk van uw configuratie van de e-mailserver kunt moeten toevoegen.

