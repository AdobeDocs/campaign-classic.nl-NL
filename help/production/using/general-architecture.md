---
product: campaign
title: Algemene architectuur
description: Algemene architectuur
audience: production
content-type: reference
topic-tags: introduction
exl-id: 3bfb5448-6996-4080-bf9a-434f1207637e
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 4%

---

# Algemene architectuur{#general-architecture}

![](../../assets/v7-only.svg)

## Minimale architectuur {#minimum-architecture}

In een minimale configuratie werkt Adobe Campaign met:

* de Adobe Campaign-toepassingsserver,
* de database.

   ![](assets/formation_exploitation.png)

Dit diagram toont aan dat het enige verkeer betrokken in de context van een minimumarchitectuur is:

1. HTTP-protocolverkeer naar de Adobe Campaign-server via internet,
1. SMTP protocolverkeer van en aan de server van Adobe Campaign via Internet.

## Verdeelde architectuur {#distributed-architecture}

Adobe Campaign bestaat uit meerdere modules die over meerdere machines kunnen worden verdeeld. Deze bedrijfsmodus heeft verschillende voordelen:

* taakverdeling,
* het instellen van de redundantie van de module;
* opbouw van een architectuur die is opgesplitst over verschillende dienstverleners (segmentering van de verleende diensten).

![](assets/architecturerepartie.png)

De verdeling van modules over verschillende machines biedt grote flexibiliteit bij het gebruik en een groter aanpassingsvermogen.

>[!NOTE]
>
>Raadpleeg [deze sectie](../../installation/using/general-architecture.md) voor meer informatie over de verschillende architecturen.

## Lijst met open poorten {#list-of-open-ports}

| Poortnummer | Betrokken Adobe Campaign-module of -toepassing | Configureerbaar |
|---|---|---|
| 443/tcp of 80/tcp | Webservers (Apache/IIS) | JA |
| 6666/udp (lokaal) | Adobe Campaign: Syslogd | JA |
| 8005/tcp (lokaal) | Adobe Campaign: webmodule | JA |
| 8080/tcp | Adobe Campaign: webmodule (tomcat) | JA |
| 7777 | Statistische server (Statistische server) | JA |
