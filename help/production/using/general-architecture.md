---
product: campaign
title: Algemene architectuur
description: Algemene architectuur
feature: Monitoring, Architecture
audience: production
content-type: reference
topic-tags: introduction
exl-id: 3bfb5448-6996-4080-bf9a-434f1207637e
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 3%

---

# Algemene architectuur{#general-architecture}



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
>Voor meer op de diverse architectuur, verwijs naar [ deze sectie ](../../installation/using/general-architecture.md).

## Lijst met open poorten {#list-of-open-ports}

| Poortnummer | Betrokken Adobe Campaign-module of -toepassing | Configureerbaar |
|---|---|---|
| 443/tcp of 80/tcp | Webservers (Apache/IIS) | JA |
| 6666/udp (lokaal) | Adobe Campaign: Syslogd | JA |
| 8005/tcp (lokaal) | Adobe Campaign: webmodule | JA |
| 8080/tcp | Adobe Campaign: webmodule (tomcat) | JA |
| 7777 | Statistische server (Statistische server) | JA |
