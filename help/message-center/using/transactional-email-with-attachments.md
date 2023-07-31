---
product: campaign
title: Transactionele e-mails verzenden met bijlagen
description: Leer hoe je transactie-e-mails kunt verzenden met individuele en/of gepersonaliseerde bijlagen met Adobe Campaign
feature: Transactional Messaging, Message Center
badge-v7-only: label="v7" type="Informative" tooltip="Alleen van toepassing op Campaign Classic v7"
exl-id: 755d2364-f6c4-4943-97e8-3ed52a0f2665
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '670'
ht-degree: 2%

---

# Hoofdlettergebruik: transactie-e-mails met bijlagen verzenden {#transactional-email-with-attachments}



Het doel van dit gebruiksgeval is het toevoegen van e-mailbijlagen tijdens de vlucht aan uitgaande verzendingen.

## Belangrijkste stappen {#key-steps}

In dit scenario leert u hoe u transactie-e-mails met individuele en/of gepersonaliseerde bijlagen kunt verzenden. De bijlagen worden niet vooraf geüpload op de Transactionele berichtenserver: ze worden direct gegenereerd.

Wanneer u klanteninteractie of details vangt, kunt u deze informatie naar de klant aan het eind van het proces moeten terugsturen, bijvoorbeeld in een dossier van PDF in bijlage aan een e-mail.

Hieronder volgen de belangrijkste stappen van dit scenario:

1. De klant voert de website in en zoekt een product dat hij of zij wil kopen.
1. De klant selecteert het product en past enkele opties aan.
1. De klant voltooit de transactie.
1. Er wordt een e-mail naar de klant verzonden waarin de transactie wordt bevestigd. Omdat het niet wordt aanbevolen PII (Persoonlijke Identificeerbare Informatie) in e-mail te verzenden, wordt een veilige PDF gegenereerd en aan de e-mail toegevoegd.
1. De klant ontvangt de e-mail en de bijbehorende bijlage met de relevante gegevens.

In dit scenario worden de bijlagen niet vooraf gemaakt, maar direct toegevoegd aan de uitgaande e-mails, hetgeen de volgende voordelen biedt:

* Zo kunt u de inhoud van de bijlage aanpassen.
* Als de gehechtheid met een transactie (zoals in het hierboven beschreven voorbeeldscenario) wordt geassocieerd, kan het dynamische gegevens bevatten die tijdens het klantenproces worden geproduceerd.
* Als u PDF-bestanden koppelt, wordt de beveiliging geoptimaliseerd omdat u deze kunt versleutelen en verzenden via HTTPS.

## Recommendations en guardrails {#important-notes}

Om prestatieproblemen te voorkomen, mogen afbeeldingen in e-mailberichten niet groter zijn dan 100 kB. Deze standaard ingestelde limiet kan worden gewijzigd in `NmsDelivery_MaxDownloadedImageSize` -optie. Adobe raadt echter ten zeerste aan om grote afbeeldingen in uw e-mailleveringen te voorkomen.

Adobe raadt ook aan de grootte en het aantal bijgevoegde bestanden te beperken. Standaard kunt u slechts één bestand als bijlage aan een e-mailbericht toevoegen. Deze drempel kan vanaf de `NmsDelivery_MaxRecommendedAttachments` -optie.

Meer informatie in [de lijst met Campaign Classic-opties](../../installation/using/configuring-campaign-options.md#delivery).

Lees de onderstaande richtlijnen zorgvuldig door voordat u dit scenario implementeert:

* De instanties van het Transactionele overseinen zouden niet moeten worden gebruikt om, dossiers of gegevens op te slaan uit te voeren of te uploaden. Ze kunnen alleen worden gebruikt voor gebeurtenisgegevens en gerelateerde informatie. Ze moeten niet worden beschouwd als een bestandsopslagsysteem.
* Aangezien er geen directe toegang tot de Transactionele overseineninstanties of servers buiten Adobe is, is er geen standaardmanier om dergelijke dossiers op deze servers (geen toegang van FTP) te duwen.
* Het is contractueel niet correct om de schijfruimte op de Transactionele overseineninstanties te gebruiken om dossiers van om het even welke soort op te slaan, zelfs niet voor gehechtheid.
* U moet een ander online schijfsysteem gebruiken om deze bestanden te hosten. U hebt FTP-toegang tot dit systeem nodig en u moet bestanden kunnen schrijven en verwijderen.

>[!NOTE]
>
>Om prestatieproblemen te voorkomen, wordt aanbevolen niet meer dan één bijlage per e-mail op te nemen. De aanbevolen drempelwaarde kan worden geconfigureerd vanuit [de lijst met Campaign Classic-opties](../../installation/using/configuring-campaign-options.md#delivery).

## Implementatie {#implementation}

In het onderstaande diagram worden de verschillende stappen weergegeven bij de implementatie van dit scenario:

![](assets/message-center-uc1.png)

Voer de onderstaande stappen uit om een e-mailbijlage direct toe te voegen aan een transactiebericht:

1. Begin door uw bijlage te ontwerpen. Zie [deze sectie](../../delivery/using/attaching-files.md#attach-a-personalized-file)voor meer informatie.

   Hierdoor kunt u de bestanden als bijlage aan een e-mail toevoegen, zelfs als deze niet worden gehost op de uitvoeringsinstantie.

1. U kunt e-mailberichten verzenden via een SOAP-berichttrigger. In de SOAP-aanroep is er een URL-parameter (bijlageURL).

   Zie voor meer informatie over SOAP-aanvragen [Beschrijving van gebeurtenis](../../message-center/using/event-description.md).

1. Klik tijdens het ontwerpen van uw e-mail op **[!UICONTROL Attachment]**.

1. In de **[!UICONTROL Attachment definition]** scherm, ga de parameter van de gehechtheid van de ZEEP in:

   ```
   <%= rtEvent.ctx.attachmentUrl %>
   ```

1. Wanneer het bericht wordt verwerkt, krijgt het systeem het bestand van de externe locatie (externe server) en voegt het bestand bij het individuele bericht.

   Aangezien deze parameter een variabele kan zijn, zou het de volledig gevormde verre URL variabele van uw dossier moeten goedkeuren, die via de vraag van de ZEEP wordt verzonden.

   ![](assets/message-center-uc2.png)
