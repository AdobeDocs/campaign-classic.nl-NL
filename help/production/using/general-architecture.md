---
title: Algemene architectuur
seo-title: Algemene architectuur
description: Algemene architectuur
seo-description: null
page-status-flag: never-activated
uuid: a565a10c-cbef-455a-aa1d-9be9cd207c7a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: introduction
discoiquuid: f4879774-afe5-4556-ab60-9297cabbca2c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Algemene architectuur{#general-architecture}

## Minimale architectuur {#minimum-architecture}

In een minimale configuratie werkt Adobe Campaign met:

* de Adobe Campaign-toepassingsserver,
* de database.

   ![](assets/formation_exploitation.png)

Dit diagram toont aan dat het enige verkeer betrokken in de context van een minimumarchitectuur is:

1. HTTP-protocolverkeer naar de Adobe Campaign-server via internet,
1. SMTP-protocolverkeer van en naar de Adobe Campagneserver via internet.

## Verdeelde architectuur {#distributed-architecture}

Adobe Campaign bestaat uit meerdere modules die op meerdere computers kunnen worden gesplitst. Deze bedrijfsmodus heeft verschillende voordelen:

* taakverdeling,
* het instellen van de redundantie van de module;
* opbouw van een architectuur die is opgesplitst over verschillende dienstverleners (segmentering van de verleende diensten).

![](assets/architecturerepartie.png)

De verdeling van modules over verschillende machines biedt grote flexibiliteit bij het gebruik en een groter aanpassingsvermogen.

>[!NOTE]
>
>Raadpleeg [deze sectie](../../installation/using/general-architecture.md)voor meer informatie over de verschillende architecturen.

## Lijst met open poorten {#list-of-open-ports}

| Poortnummer | Betrokken Adobe-cameramodule of -toepassing | Configureerbaar |
|---|---|---|
| 443/tcp of 80/tcp | Webservers (Apache/IIS) | JA |
| 6666/udp (lokaal) | Adobe-campagne: Syslogd | JA |
| 8005/tcp (lokaal) | Adobe-campagne: webmodule | JA |
| 8080/tcp | Adobe-campagne: webmodule (tomcat) | JA |
| 7777 | Statistische server (Statistische server) | JA |

