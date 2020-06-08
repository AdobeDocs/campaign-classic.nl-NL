---
title: Databases met zwarte lijsten
seo-title: Databases met zwarte lijsten
description: Databases met zwarte lijsten
seo-description: null
page-status-flag: never-activated
uuid: 8a4a69f9-87d5-4044-bc55-76cdcb2e7800
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliverability-management
discoiquuid: eede254d-2b25-46ed-b10f-fa1d54780a75
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0386ae88a1b4d9ebda64283d874e01b14e9e5af4
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---


# Databases met zwarte lijsten{#blacklisting-databases}

Verscheidene organisaties handhaven gegevensbestanden van IP adressen en domeinen die worden genoemd om door spammers worden gebruikt. Het raadplegen van deze sites kan nuttig zijn om te begrijpen waarom bepaalde berichten zijn afgewezen als spam. Over het algemeen is het mogelijk te verzoeken dat een adres wordt verwijderd dat ten onrechte aan deze lijsten is toegevoegd.

Deze databases worden RBL&#39;s (Real-Time Blackgat Lists) genoemd en ze worden via een DNS-mechanisme geraadpleegd. Er zijn drie soorten RBLs:

* Op IP-adres: maakt een lijst IP adressen die spam verzenden of waarschijnlijk spam opnieuw zal afspelen.
* Op senderdomein: maakt een lijst van afzenderdomeinen (volledig domein van het stuiterende postadres) die spam verzenden of verkeerd gevormd.
* Op webdomein: geeft een lijst weer van de domeinen (domeinen op hoog niveau zoals geregistreerd met de registrars) die in URLs van de verbindingen en beelden worden gevonden bevat in spaminhoud. In de Campagne van Adobe, is het domein dat in overweging moet worden genomen over het algemeen het adres dat voor het volgen wordt gebruikt.

Hieronder volgt een lijst van de meest gebruikte RBL&#39;s. Voor een uitgebreidere lijst kunt u naar [https://www.dnsstuff.com/](https://tools.dnsstuff.com/) (&quot;Opzoeken via zwarte lijst van spam&quot;-formulier) gaan.

* **Spamhaus**

   Zie [https://www.spamhaus.org/](https://www.spamhaus.org/)

   De database is belangrijker. De indeling op deze lijst is over het algemeen een ernstige situatie. Als dit gebeurt, dient u ONMIDDELLIJK op te treden en de commerciële services, de te leveren items en de ondersteuning van Adobe Campagne te waarschuwen.

* **SpamCop**

   Zie [https://www.spamcop.net/](https://www.spamcop.net/)

   Het is een van de bekendste databases. Als één van uw IP adressen op deze lijst wordt geplaatst, betekent dit over het algemeen dat de gebruikers SpamCop uw berichten als spam hebben verklaard of dat u berichten naar een honeypot SpamCop hebt verzonden.

* **URIBL**

   Zie [https://www.uribl.com/](https://www.uribl.com/)

   Deze lijst identificeert de domeinen die regelmatig in berichten verschijnen die als spam worden verklaard. Als uw domein in deze lijst wordt weergegeven, kan dit van invloed zijn op de leesbaarheid. U moet de services voor levering en de ondersteuning van Adobe Campagne onmiddellijk op de hoogte stellen.

* **SURBL**

   Zie [http://www.surbl.org/](http://www.surbl.org/)

   De SURBL identificeert de websites die regelmatig in spam verschijnen. Als uw domein in deze lijst wordt weergegeven, kan dit van invloed zijn op de leesbaarheid. U moet de services voor levering en de ondersteuning van Adobe Campagne onmiddellijk op de hoogte stellen.

* **iX Manitu**

   Dit is een lijst van IP&#39;s en wordt in Duitsland op grote schaal gebruikt. Zie [https://www.heise.de/ix/nixspam/](https://www.heise.de/ix/nixspam/)

<!--* SORBS

  [https://www.nl.sorbs.net](https://www.nl.sorbs.net) compiles a list of IP addresses that are reputed to be dynamic IP address (i.e. attributed temporarily to ISP subscribers) or "open relay" addresses. Certain domains check whether the IP address of a sender is not listed on this site before accepting email. Checking the IP addresses on this site can prove useful.-->