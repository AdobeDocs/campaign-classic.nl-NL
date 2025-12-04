---
product: campaign
title: E-mailarchivering
description: E-mailarchivering
feature: Installation, Instance Settings, Email
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 424faf25-2fd5-40d1-a2fc-c715fc0b8190
source-git-commit: 62ab16b206563aa25b8943e606d03a3184eb00db
workflow-type: tm+mt
source-wordcount: '1211'
ht-degree: 1%

---

# Bcc van e-mail configureren {#email-archiving}



U kunt Adobe Campaign zo configureren dat een kopie van de e-mails die u van uw platform hebt ontvangen, bewaard blijft.

Adobe Campaign zelf beheert gearchiveerde bestanden echter niet. Het laat u toe om de berichten van uw keus naar een specifiek adres te verzenden, van waar zij kunnen worden verwerkt en worden gearchiveerd gebruikend een extern systeem.

Hiervoor worden .eml-bestanden die overeenkomen met de verzonden e-mails, overgebracht naar een externe server, zoals een SMTP-e-mailserver. De archiveringsbestemming is een BCC e-mailadres (onzichtbaar voor de leverende ontvangers) dat u moet specificeren.

## Aanbevelingen en beperkingen {#recommendations-and-limitations}

* BCC-functionaliteit voor e-mail is optioneel. Controleer hiervoor uw licentieovereenkomst.
* Voor **ontvangen en hybride architecturen**, contacteer uw accountmanager om het te activeren. Het BCC e-mailadres van uw keuze moet worden opgegeven aan het Adobe-team dat het voor u zal configureren.
* Voor **op-gebouw installaties**, volg de hieronder richtlijnen om het te activeren - zie [ het Activeren e-mail BCC (op gebouw) ](#activating-email-archiving--on-premise-) en [ het Vormen van het BCC e-mailadres (op gebouw) ](#configuring-the-bcc-email-address--on-premise-) secties.
* U kunt slechts één BCC-e-mailadres gebruiken.
* Nadat e-mail-BCC is geconfigureerd, controleert u of de functie is ingeschakeld in de leveringssjabloon of in de levering via de optie **[!UICONTROL Email BCC]** . verwijs naar de [ documentatie van de Campagne v8 ](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/emails/email-bcc.html){target="_blank"}.
* Er wordt alleen rekening gehouden met e-mailberichten die zijn verzonden. Overschrijdingen worden niet meegeteld.
* Het e-mailarchiveringssysteem is gewijzigd met Adobe Campaign 17.2 (build 8795). Als u al gebruikmaakte van e-mailarchivering, moet u handmatig upgraden naar het nieuwe BCC-systeem voor e-mail. Voor meer op dit, zie [ Bewegend aan de nieuwe E-mailBCC ](#updated-email-archiving-system--bcc-) sectie.

## BCC via e-mail activeren (op locatie) {#activating-email-archiving--on-premise-}

[!BADGE  Op-gebouw &amp; Hybrid ]{type=Caution url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=nl" tooltip="Alleen van toepassing op on-premise en hybride implementaties"}


Volg onderstaande stappen om BCC e-mailarchivering te activeren wanneer Adobe Campaign op locatie is geïnstalleerd.

### Lokale map {#local-folder}

Als u het overbrengen van verzonden e-mails naar een BCC-e-mailadres wilt inschakelen, moeten exacte onbewerkte kopieën van verzonden e-mails eerst worden opgeslagen als .eml-bestanden naar een lokale map.

De weg voor de lokale omslag moet in het **config - `<instance>` .xml** dossier, van de configuratie worden gespecificeerd. Bijvoorbeeld:

```
<mta dataLogPath="C:\emails">
```

>[!NOTE]
>
>Het is de verantwoordelijkheid van het team dat het project uitvoert om ervoor te zorgen dat de veiligheidsmontages toegang tot de omslag verlenen die door de **wordt bepaald dataLogPath** parameters.

Het volledige pad is als volgt: **`<datalogpath>  YYYY-MM-DDHHh`**. De datum en de tijd worden geplaatst volgens de klok van de server MTA (UTC). Bijvoorbeeld:

```
C:\emails\2018-12-02\13h
```

De naam van het archiefbestand is **`<deliveryid>-<broadlogid>.eml`** als de status van de e-mails niet **[!UICONTROL Sent]** is. Nadat de status is gewijzigd in **[!UICONTROL Sent]** , wordt de bestandsnaam **`<deliveryid>-<broadlogid>-sent.eml`** . Bijvoorbeeld:

```
C:\emails\2018-12-02\13h\4012-8040-sent.eml
```

>[!NOTE]
>
>In een mid-sourcing-instantie bevindt de directory voor de BCC-e-mails zich op de mid-sourcing-server.
>
>De deliveryID en de broadlogID komen van de mid-sourcingsserver wanneer de status van de e-mails niet wordt verzonden. Zodra de status is gewijzigd in **[!UICONTROL Sent]** , komen deze id&#39;s van de marketingserver.

### Parameters {#parameters}

Zodra de lokale omslagweg wordt bepaald, voeg en geef de volgende elementen zoals gewenst in het **toe config-`<instance name>.xml`** dossier. Hieronder ziet u de standaardwaarden:

```
<archiving autoStart="false" compressionFormat="0" compressBatchSize="10000"
           archivingType="1" expirationDelay="2" purgeArchivesDelay="7"
           pollDelay="600" acquireLimit="5000" smtpNbConnection="2"/>
```

* **compressionFormat**: formaat dat wordt gebruikt wanneer het samenpersen van de .eml dossiers. De mogelijke waarden zijn:

  **0**: geen compressie (standaardwaarde)

  **1**: compressie (.zip formaat)

* **compressBatchSize**: aantal .eml dossiers die aan een archief (.zip- dossier) worden toegevoegd.


* **archivingType**: archiveringsstrategie die moet worden gebruikt. De enige mogelijke waarde is **1**. De ruwe exemplaren van verzonden e-mails worden bewaard in .eml formaat aan de **dataLogPath** omslag en zij worden verzonden naar het BCC e-mailadres over SMTP. Zodra de e-mailexemplaren naar het adres BCC worden verzonden, wordt de naam van het archiefdossier **`<deliveryid>-<broadlogid>-sent-archived.eml`** en het dossier wordt verplaatst naar de **dataLogPath/archives** omslag. Het pad naar het verzonden en door BCC gearchiveerde e-mailbestand is nu **`<datalogpath>archivesYYYY-MM-DDHHh<deliveryid>- <broadlogid>-sent-archived.eml`** .

  <!--
  **0**: raw copies of sent emails are saved in .eml format to the **dataLogPath** folder (default value). An archiving copy of the **`<deliveryid>-<broadlogid>-sent.eml`** file is saved to the **dataLogPath/archives** folder. The sent email file path becomes **`<datalogpath>archivesYYYY-MM-DDHHh <deliveryid>-<broadlogid>-sent.eml`**.-->

* **expirationDelay**: aantal dagen .eml- dossiers worden bewaard voor archivering. Na die vertraging, worden zij automatisch verplaatst naar de **dataLogPath/archives** omslag voor compressie. .eml-bestanden verlopen standaard na twee dagen.
* **purgeArchivesDelay**: aantal dagarchieven worden gehouden in de **dataLogPath/`<archives>`** omslag. Na die periode worden zij definitief geschrapt. De zuivering begint wanneer MTA wordt begonnen. Standaard wordt het elke zeven dagen uitgevoerd.
* **pollDelay**: het controleren van frequentie (in seconden) voor nieuwe inkomende verzonden e-mails aan de **dataLogPath** omslag. Bijvoorbeeld, als deze parameter aan 60 wordt geplaatst, betekent het dat elke minuut, het archiveringsproces door de .eml dossiers binnen de **dataLogPath/`<date and time>`** omslagen gaat, een zuivering indien nodig toepast en e-mailexemplaren naar het adres BCC verzendt en/of de gearchiveerde dossiers wanneer nodig comprimeert.
* **verwervingLimit**: aantal.eml- dossiers die onmiddellijk worden verwerkt alvorens het archiveringsproces opnieuw volgens de **pollDelay** parameter wordt toegepast. Bijvoorbeeld, als u de **parameter 0} verwervingLimit {aan 100 plaatst terwijl de** pollDelay **parameter aan 60 wordt geplaatst, zullen 100.eml- dossiers per minuut worden verwerkt.**
* **smtpNbConnection**: aantal verbindingen SMTP aan het BCC e-mailadres.

Zorg ervoor u deze parameters volgens de e-mailverzendende productie aanpast. Bijvoorbeeld, in een configuratie waar MTA 30.000 e-mails per uur verzendt, kunt u de **parameter 0} pollDelay aan 600 plaatsen, de** verwervingLimit **parameter aan 5000 en de** smtpNbConnection **parameter aan 2.** Het betekent dat met 2 verbindingen SMTP, 5.000 e-mails naar het adres BCC om de 10 minuten zullen worden verzonden.

## Het BCC-e-mailadres configureren (op locatie) {#configuring-the-bcc-email-address--on-premise-}

[!BADGE  Op-gebouw &amp; Hybrid ]{type=Caution url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=nl" tooltip="Alleen van toepassing op on-premise en hybride implementaties"}


>[!IMPORTANT]
>
>Om privacyredenen moeten BCC-e-mails worden verwerkt door een archiveringssysteem dat veilig identificeerbare informatie (PII) kan opslaan.

In het **config-`<instance name>.xml`** dossier, gebruik de volgende parameters om de SMTP e-mailserver te bepalen waarnaar de opgeslagen dossiers zullen worden overgebracht:

```
<archiving smtpBccAddress="" smtpEnableTLS="false" smtpRelayAddress="" smtpRelayPort="25"/>
```

* **smtpBccAddress**: archiverend doelbestemming
* **smtpEnableTLS**: het gebruiken van een beveiligde verbinding SMTP (protocol TLS/SSL)
* **smtpRelayAddress**: relaisadres aan gebruik
* **smtpRelayPort**: relaishaven aan gebruik

>[!NOTE]
>
>Als u een SMTP relais gebruikt, worden de veranderingen in de e-mails die door het relais worden aangebracht niet in het archiveringsproces in aanmerking genomen.
>
>Bovendien kent het relais een **[!UICONTROL Sent]** -status toe aan alle e-mails, ook aan de e-mails die niet zijn verzonden. Daarom worden alle berichten gearchiveerd.

<!--
## Moving to the new Email BCC {#updated-email-archiving-system--bcc-}

[!BADGE On-premise & Hybrid]{type=Caution url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"}

>[!IMPORTANT]
>
>The email archiving system (BCC) changed with Adobe Campaign 17.2 (build 8795). If you are upgrading from an older build and were already using email archiving capabilities, you must upgrade manually to the new email archiving system (BCC).

To do this, make the following changes to the **`config-<instance>.xml`** file:

1. Remove the **zipPath** parameter from the **`<archiving>`** node.
1. Set the **compressionFormat** parameter to **1** if needed.
1. Set the **archivingType** parameter to **1**.

Once email BCC is configured, make sure you select the **[!UICONTROL Email BCC]** option in the delivery template or the delivery. For more on this, see [this section](../../delivery/using/sending-messages.md#archiving-emails).
-->

## BCC-tips e-mailen {#best-practices}

* **BCC adresbrievenbus**: zorg ervoor het genoeg ontvangstcapaciteit heeft om alle e-mails te archiveren die door MTA worden verzonden.
* **MTA die** pooling: De BCC archiveringseigenschap werkt op het niveau MTA. Hiermee kunt u elke e-mail dupliceren die door de MTA is verzonden. Aangezien MTA over verscheidene instanties (bijvoorbeeld dev, test, of prod) of zelfs over verscheidene cliënten (in een midsourcingomgeving) kan worden samengebracht, beïnvloedt het opzetten van deze eigenschap veiligheid:

   * Als u een MTA met veelvoudige cliënten deelt en één van hen heeft deze optie geactiveerd, zal deze cliënt tot alle e-mails van de andere cliënten toegang hebben die de zelfde MTA delen. Om een dergelijke situatie te vermijden, gebruikt u een andere MTA voor elke cliënt.
   * Als u zelfde MTA over veelvoudige instanties (ontwikkeling, test, staaf) voor één enkele cliënt gebruikt, zullen de berichten die van alle drie instanties worden verzonden door de dataLogPath optie worden gedupliceerd.

* **E-mails per verbinding**: BCC e-mailarchivering werkt door een verbinding te openen en probeert om alle e-mails door die verbinding te verzenden. Adobe raadt u aan om met uw interne technische contactpersoon het aantal e-mails te controleren dat via een bepaalde verbinding wordt geaccepteerd. Het verhogen van dit aantal kan een grote invloed op de productie BCC hebben.
* **BCC die IPs** verzendt: momenteel, worden BCC e-mails niet verzonden door de normale MTA volmachten. In plaats daarvan is een directe verbinding geopend van de MTA-server naar de e-mailserver van het doel. Dit betekent dat u extra IPs aan de lijst van gewenste personen op uw netwerk, afhankelijk van uw configuratie van de e-mailserver kunt moeten toevoegen.

<!--## Email BCC with Enhanced MTA {#email-bcc-with-enhanced-mta}

For **hosted and hybrid architectures**, if you have the latest instance of Adobe Campaign, or if you have upgraded to the Enhanced MTA and using Adobe Campaign 19.2 or later, you can use Email BCC with Enhanced MTA, which is more reliable, efficient, and has lower latency.

### Activating Email BCC with Enhanced MTA

To activate this feature, you must contact your account executive to communicate the BCC email address to be used for archiving.

>[!NOTE]
>
>If you were already using BCC email archiving, you can provide the same address as you were using before or use a new one. If you keep the same, you still have to contact your account executive to set it up for you.

### Specificities and recommendations

Email BCC with Enhanced MTA is not activated at the delivery level: once this feature is enabled, **all sent deliveries** are sent to the BCC email address. There is no need to select the **[!UICONTROL Email BCC]** option in the delivery template or in the delivery.

If you were already using BCC and if you keep the same address, you could see a significant increase in the volumes sent to the BCC address.

Consequently, make sure:
* The BCC address has enough reception capacity to archive all the emails that are sent.
* You have the required MTA infrastructure capacity to receive 100% of your email volume delivered to a single address.

### Limitations

* Email BCC with Enhanced MTA delivers to the BCC email address before delivering to the recipients, which can result in BCC messages being sent even though the original deliveries may have bounced. For more on bounces, see [Understanding delivery failures](../../delivery/using/delivery-failures-quarantine.md).

* There is no reporting available on the delivery status of the emails sent to the BCC email address.-->