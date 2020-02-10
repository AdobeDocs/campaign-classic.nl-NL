---
title: Doel
seo-title: Doel
description: Doel
seo-description: null
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
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Doel{#purpose}

Het doel van dit gebruiksgeval is het toevoegen van e-mailbijlagen tijdens de vlucht aan uitgaande verzendingen.

In dit scenario, zullen wij zien hoe te om transactie-e-mail met individuele/gepersonaliseerde gehechtheid te verzenden. De bijlagen worden niet vooraf geüpload op de Transactieberichten-server, maar worden direct gegenereerd.

Wanneer u interactie of details van klanten vastlegt, moet u deze informatie mogelijk aan het einde van het proces terugsturen naar de klant, bijvoorbeeld in een PDF-bestand dat aan een e-mail is gekoppeld. Hier volgen de algemene stappen van dit scenario.

1. De klant voert de website in en zoekt een product dat hij of zij wil kopen.
1. De klant selecteert het product en past enkele opties aan.
1. De klant voltooit de transactie.
1. De klant ontvangt een e-mail waarin de transactie wordt bevestigd. We willen geen PII (Persoonlijke identificeerbare informatie) in de e-mail verzenden zodat we een beveiligde PDF genereren en deze als bijlage aan de e-mail toevoegen.
1. De klant ontvangt het e-mailbericht en de bijbehorende bijlage met alle benodigde gegevens.

In dit scenario worden de bijlagen niet vooraf gemaakt, maar direct toegevoegd aan de uitgaande e-mails. Hierdoor kunt u ook de inhoud van de bijlage aanpassen. Ook, als de gehechtheid met een transactie (zoals in het bovenstaande voorbeeld) wordt geassocieerd, dan kunt u het nodig hebben om dynamische gegevens te bevatten die tijdens het klantenproces worden geproduceerd. Als u PDF&#39;s op deze manier bijvoegt, wordt ook de beveiliging geoptimaliseerd, aangezien u deze kunt versleutelen en verzenden via HTTPS.
