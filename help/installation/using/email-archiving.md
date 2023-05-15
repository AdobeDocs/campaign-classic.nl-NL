---
product: campaign
title: E-mailarchivering
description: E-mailarchivering
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 424faf25-2fd5-40d1-a2fc-c715fc0b8190
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '1359'
ht-degree: 5%

---

# Bcc van e-mail configureren {#email-archiving}



U kunt Adobe Campaign zo configureren dat een kopie van de e-mails die u van uw platform hebt ontvangen, bewaard blijft.

Adobe Campaign zelf beheert gearchiveerde bestanden echter niet. Het laat u toe om de berichten van uw keus naar een specifiek adres te verzenden, van waar zij kunnen worden verwerkt en worden gearchiveerd gebruikend een extern systeem.

Hiervoor worden .eml-bestanden die overeenkomen met de verzonden e-mails, overgebracht naar een externe server, zoals een SMTP-e-mailserver. De archiveringsbestemming is een BCC e-mailadres (onzichtbaar voor de leverende ontvangers) dat u moet specificeren.

## Recommendations en beperkingen {#recommendations-and-limitations}

* BCC-functionaliteit voor e-mail is optioneel. Controleer hiervoor uw licentieovereenkomst.
* Voor **gehoste en hybride architecturen**, neemt u contact op met uw accountmanager om deze te activeren. Het BCC e-mailadres van uw keus moet aan het team van de Adobe worden verstrekt die het voor u zal vormen.
* Voor **installaties op locatie** volgt u de onderstaande richtlijnen om het te activeren - raadpleeg de [BCC via e-mail activeren (op locatie)](#activating-email-archiving--on-premise-) en [Het BCC-e-mailadres configureren (op locatie)](#configuring-the-bcc-email-address--on-premise-) secties.
* U kunt slechts één BCC-e-mailadres gebruiken.
* Zodra e-mail BCC wordt gevormd, zorg ervoor de eigenschap in het leveringsmalplaatje of in de levering door wordt toegelaten **[!UICONTROL Email BCC]** optie. Zie [deze sectie](../../delivery/using/sending-messages.md#archiving-emails)voor meer informatie.
* Er wordt alleen rekening gehouden met e-mailberichten die zijn verzonden, maar met bedragen.
* Het e-mailarchiveringssysteem is gewijzigd met Adobe Campaign 17.2 (build 8795). Als u al gebruikmaakte van e-mailarchivering, moet u handmatig upgraden naar het nieuwe BCC-systeem voor e-mail. Zie voor meer informatie de [Naar de nieuwe e-mail-BCC gaan](#updated-email-archiving-system--bcc-) sectie.

## BCC via e-mail activeren (op locatie) {#activating-email-archiving--on-premise-}

[!BADGE Op locatie en hybride]{type=Caution url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=nl" tooltip="Alleen van toepassing op on-premise en hybride implementaties"}


Volg onderstaande stappen om BCC e-mailarchivering te activeren wanneer Adobe Campaign op locatie is geïnstalleerd.

### Lokale map {#local-folder}

Als u het overbrengen van verzonden e-mails naar een BCC-e-mailadres wilt inschakelen, moeten exacte onbewerkte kopieën van verzonden e-mails eerst worden opgeslagen als .eml-bestanden naar een lokale map.

Het pad voor de lokale map moet worden opgegeven in het dialoogvenster **config-`<instance>`.xml** bestand, uit de configuratie. Bijvoorbeeld:

```
<mta dataLogPath="C:\emails">
```

>[!NOTE]
>
>Het is de verantwoordelijkheid van het team dat het project implementeert om ervoor te zorgen dat de beveiligingsinstellingen toegang verlenen tot de map die via het dialoogvenster **dataLogPath** parameters.

Het volledige pad is als volgt: **`<datalogpath>  YYYY-MM-DDHHh`**. De datum en de tijd worden geplaatst volgens de klok van de server MTA (UTC). Bijvoorbeeld:

```
C:\emails\2018-12-02\13h
```

De naam van het archiefbestand is **`<deliveryid>-<broadlogid>.eml`** wanneer de status van de e-mails niet **[!UICONTROL Sent]**. Zodra de status is gewijzigd in **[!UICONTROL Sent]**, wordt de bestandsnaam gewijzigd in **`<deliveryid>-<broadlogid>-sent.eml`**. Bijvoorbeeld:

```
C:\emails\2018-12-02\13h\4012-8040-sent.eml
```

>[!NOTE]
>
>In een mid-sourcing-instantie bevindt de directory voor de BCC-e-mails zich op de mid-sourcing-server.
>
>De deliveryID en de broadlogID komen van de mid-sourcingsserver wanneer de status van de e-mails niet wordt verzonden. Zodra de status is gewijzigd in **[!UICONTROL Sent]**, deze id&#39;s komen van de marketingserver.

### Parameters {#parameters}

Nadat het lokale mappad is gedefinieerd, voegt u de volgende elementen toe en bewerkt u deze naar wens in het dialoogvenster **config-`<instance name>.xml`** bestand. Hieronder ziet u de standaardwaarden:

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

   **0**: onbewerkte kopieën van verzonden e-mails worden opgeslagen in de indeling .eml naar de **dataLogPath** map (standaardwaarde). Een archiefkopie van de **`<deliveryid>-<broadlogid>-sent.eml`** bestand wordt opgeslagen in de **dataLogPath/archives** map. Het pad naar het verzonden e-mailbestand wordt **`<datalogpath>archivesYYYY-MM-DDHHh <deliveryid>-<broadlogid>-sent.eml`**.

   **1**: onbewerkte kopieën van verzonden e-mails worden opgeslagen in de indeling .eml naar de **dataLogPath** en worden via SMTP naar het BCC-e-mailadres verzonden. Nadat de e-mailkopieën naar het BCC-adres zijn verzonden, wordt de naam van het archiefbestand gewijzigd in **`<deliveryid>-<broadlogid>-sent-archived.eml`** en het bestand wordt verplaatst naar de **dataLogPath/archives** map. Het pad naar het verzonden en door BCC gearchiveerde e-mailbestand is dan **`<datalogpath>archivesYYYY-MM-DDHHh<deliveryid>- <broadlogid>-sent-archived.eml`**.

* **expirationDelay**: aantal dagen dat .eml-bestanden worden bewaard voor archivering. Na die vertraging worden ze automatisch naar de **dataLogPath/archives** voor compressie. .eml-bestanden verlopen standaard na twee dagen.
* **purgeArchivesDelay**: aantal dagen dat archieven worden bewaard in het **dataLogPath/`<archives>`** map. Na die periode worden zij definitief geschrapt. De zuivering begint wanneer MTA wordt begonnen. Standaard wordt het elke zeven dagen uitgevoerd.
* **pollDelay**: controlefrequentie (in seconden) voor nieuwe inkomende e-mails naar de **dataLogPath** map. Als deze parameter bijvoorbeeld op 60 is ingesteld, betekent dit dat het archiveringsproces elke minuut door de .eml-bestanden in de **dataLogPath/`<date and time>`** mappen, pas indien nodig leegmaken toe en verstuurt e-mailkopieën naar het BCC-adres en/of comprimeer de gearchiveerde bestanden wanneer dat nodig is.
* **verwervingLimit**: Het aantal eml-bestanden dat tegelijk wordt verwerkt voordat het archiveringsproces opnieuw wordt toegepast volgens het **pollDelay** parameter. Als u bijvoorbeeld de opdracht **verwervingLimit** -parameter tot en met 100 **pollDelay** parameter wordt ingesteld op 60.100.eml-bestanden per minuut.
* **smtpNbConnection**: Aantal verbindingen SMTP aan het BCC e-mailadres.

Zorg ervoor u deze parameters volgens de e-mailverzendende productie aanpast. Bijvoorbeeld, in een configuratie waar MTA 30.000 e-mail per uur verzendt, kunt u plaatsen **pollDelay** tot en met 600 **verwervingLimit** tot en met 5000 en de **smtpNbConnection** parameter t/m 2. Het betekent dat met 2 verbindingen SMTP, 5.000 e-mails naar het adres BCC om de 10 minuten zullen worden verzonden.

## Het BCC-e-mailadres configureren (op locatie) {#configuring-the-bcc-email-address--on-premise-}

[!BADGE Op locatie en hybride]{type=Caution url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=nl" tooltip="Alleen van toepassing op on-premise en hybride implementaties"}


>[!IMPORTANT]
>
>Om privacyredenen moeten BCC-e-mails worden verwerkt door een archiveringssysteem dat veilig identificeerbare informatie (PII) kan opslaan.

In de **config-`<instance name>.xml`** bestand, gebruikt u de volgende parameters om de SMTP e-mailserver te definiëren waarnaar de opgeslagen bestanden worden overgebracht:

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
>Bovendien wijst de relais een **[!UICONTROL Sent]** status voor alle e-mails, inclusief die welke niet zijn verzonden. Daarom worden alle berichten gearchiveerd.

## Naar de nieuwe e-mail-BCC gaan {#updated-email-archiving-system--bcc-}

[!BADGE Op locatie en hybride]{type=Caution url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=nl" tooltip="Alleen van toepassing op on-premise en hybride implementaties"}



>[!IMPORTANT]
>
>Het e-mailarchiveringssysteem (BCC) is gewijzigd met Adobe Campaign 17.2 (build 8795). Als u een upgrade uitvoert vanaf een oudere build en al gebruikmaakt van e-mailarchiveringsmogelijkheden, moet u de upgrade handmatig uitvoeren naar het nieuwe e-mailarchiveringssysteem (BCC).

Om dit te doen, breng de volgende veranderingen in **`config-<instance>.xml`** bestand:

1. Verwijder de **zipPath** parameter van de **`<archiving>`** knooppunt.
1. Stel de **compressionFormat** parameter to **1** indien nodig.
1. Stel de **archivingType** parameter to **1**.

Nadat e-mail BCC is geconfigureerd, selecteert u de optie **[!UICONTROL Email BCC]** in de leveringstemplate of de levering. Zie [deze sectie](../../delivery/using/sending-messages.md#archiving-emails)voor meer informatie.

## BCC-tips e-mailen {#best-practices}

* **BCC-adresvak**: ervoor te zorgen dat het voldoende opvangcapaciteit heeft om alle e-mails die door de MTA worden verzonden, te archiveren.
* **MTA-pooling**: de archiveringsfunctie van BCC werkt op MTA-niveau. Hiermee kunt u elke e-mail dupliceren die door de MTA is verzonden. Aangezien MTA over verscheidene instanties (bijvoorbeeld dev, test, of prod) of zelfs over verscheidene cliënten (in een midsourcingomgeving) kan worden samengebracht, beïnvloedt het opzetten van deze eigenschap veiligheid:

   * Als u een MTA met veelvoudige cliënten deelt en één van hen heeft deze optie geactiveerd, zal deze cliënt tot alle e-mails van de andere cliënten toegang hebben die de zelfde MTA delen. Om een dergelijke situatie te vermijden, gebruikt u een andere MTA voor elke cliënt.
   * Als u zelfde MTA over veelvoudige instanties (ontwikkeling, test, staaf) voor één enkele cliënt gebruikt, zullen de berichten die van alle drie instanties worden verzonden door de dataLogPath optie worden gedupliceerd.

* **E-mails per verbinding**: BCC e-mailarchivering werkt door een verbinding te openen en alle e-mails via die verbinding te verzenden. Adobe raadt u aan om met uw interne technische contactpersoon te controleren hoeveel e-mails worden geaccepteerd voor een bepaalde verbinding. Het verhogen van dit aantal kan een grote invloed op de productie BCC hebben.
* **BCC die IPs verzendt**: BCC-e-mailberichten worden momenteel niet verzonden via de normale MTA-proxy&#39;s. In plaats daarvan is een directe verbinding geopend van de MTA-server naar de e-mailserver van het doel. Dit betekent dat u extra IPs aan de lijst van gewenste personen op uw netwerk, afhankelijk van uw configuratie van de e-mailserver kunt moeten toevoegen.

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

* Email BCC with Enhanced MTA delivers to the BCC email address before delivering to the recipients, which can result in BCC messages being sent even though the original deliveries may have bounced. For more on bounces, see [Understanding delivery failures](../../delivery/using/understanding-delivery-failures.md).

* There is no reporting available on the delivery status of the emails sent to the BCC email address.-->