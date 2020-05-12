---
title: Bijlagen toevoegen aan transactieberichten met Adobe Campagne Classic
description: Leer hoe u transactie-e-mails met individuele en/of gepersonaliseerde bijlagen kunt verzenden met Adobe Campaign Classic
page-status-flag: never-activated
uuid: 4452d839-318a-49d8-8abb-4ba04c803e9f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: use-case
discoiquuid: 7b8ab9d6-e47e-46d8-99df-da793486654c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 24a50fcaad4d9081e5504652eb5b73aa7db1e65f
workflow-type: tm+mt
source-wordcount: '560'
ht-degree: 0%

---


# Hoofdlettergebruik: Transactiee-mails verzenden met bijlagen{#transactional-email-with-attachments}

Het doel van dit gebruiksgeval is het toevoegen van e-mailbijlagen tijdens de vlucht aan uitgaande verzendingen.

## Belangrijkste stappen {#key-steps}

In dit scenario leert u hoe u transactie-e-mails met individuele en/of gepersonaliseerde bijlagen kunt verzenden. De bijlagen worden niet vooraf geüpload naar de Transactieberichten-server: in plaats daarvan worden ze tijdens de vlucht gegenereerd .

Wanneer u interactie met of gegevens van klanten vastlegt, moet u deze gegevens mogelijk aan het einde van het proces terugsturen naar de klant, bijvoorbeeld in een PDF-bestand dat aan een e-mail is gekoppeld.

Hieronder volgen de belangrijkste stappen van dit scenario:

1. De klant voert de website in en zoekt een product dat hij of zij wil kopen.
1. De klant selecteert het product en past enkele opties aan.
1. De klant voltooit de transactie.
1. De klant ontvangt een e-mail waarin de transactie wordt bevestigd. Omdat het niet wordt aangeraden PII (Persoonlijke identificeerbare gegevens) in de e-mail te verzenden, wordt een beveiligde PDF gegenereerd en aan de e-mail toegevoegd.
1. De klant ontvangt de e-mail en de bijbehorende bijlage met de relevante gegevens.

In dit scenario worden de bijlagen niet vooraf gemaakt, maar direct toegevoegd aan de uitgaande e-mails, hetgeen de volgende voordelen biedt:

* Zo kunt u de inhoud van de bijlage aanpassen.
* Als de gehechtheid met een transactie (zoals in het hierboven beschreven voorbeeldscenario) wordt geassocieerd, kan het dynamische gegevens bevatten die tijdens het klantenproces worden geproduceerd.
* Als u PDF-bestanden bijvoegt, wordt de beveiliging geoptimaliseerd omdat u deze kunt versleutelen en verzenden via HTTPS.

## Aanbevelingen {#important-notes}

Lees de onderstaande richtlijnen zorgvuldig door voordat u dit scenario implementeert:

* De instanties van het Overseinen van de Transactie zouden niet moeten worden gebruikt om, dossiers of gegevens op te slaan uit te voeren of te uploaden. Ze kunnen alleen worden gebruikt voor gebeurtenisgegevens en gerelateerde informatie. Ze moeten niet worden beschouwd als een bestandsopslagsysteem.
* Aangezien er geen directe toegang tot de instanties of servers van het Overseinen van de Transactie buiten Adobe is, is er geen standaardmanier om dergelijke dossiers op deze servers (geen toegang FTP) te duwen.
* Het is contractueel niet correct om de schijfruimte op de instanties van het Overseinen van de Transactie te gebruiken om dossiers van om het even welke soort op te slaan, zelfs niet voor gehechtheid.
* U moet een ander online schijfsysteem gebruiken om deze bestanden te hosten. U hebt FTP-toegang tot dit systeem nodig en u moet bestanden kunnen schrijven en verwijderen.

## Implementatie {#implementation}

In het onderstaande diagram worden de verschillende stappen weergegeven bij de implementatie van dit scenario:

![](assets/message-center-uc1.png)

Voer de onderstaande stappen uit om een e-mailbijlage direct toe te voegen aan een transactiebericht:

1. Begin door uw bijlage te ontwerpen. Zie [deze sectie](../../delivery/using/attaching-files.md#attach-a-personalized-file)voor meer informatie.

   Hierdoor kunt u de bestanden als bijlage aan een e-mail toevoegen, zelfs als deze niet worden gehost op de uitvoeringsinstantie.

1. U kunt e-mailberichten verzenden via een SOAP-berichttrigger. In de SOAP-aanroep is er een URL-parameter (bijlageURL).

   Zie [Gebeurtenisbeschrijving](../../message-center/using/event-description.md)voor meer informatie over SOAP-aanvragen.

1. Klik tijdens het ontwerpen van uw e-mail op **[!UICONTROL Attachment]**.

1. Voer in het **[!UICONTROL Attachment definition]** scherm de parameter SOAP-bijlage in:

   ```
   <%= rtEvent.ctx.attachementUrl %>
   ```

1. Wanneer het bericht wordt verwerkt, krijgt het systeem het bestand van de externe locatie (externe server) en voegt het bestand bij het individuele bericht.

   Aangezien deze parameter een variabele kan zijn, zou het de volledig gevormde verre URL variabele van uw dossier moeten goedkeuren, die via de vraag van de ZEEP wordt verzonden.

   ![](assets/message-center-uc2.png)
