---
title: Technische controle
seo-title: Technische controle
description: Technische controle
seo-description: null
page-status-flag: never-activated
uuid: 44ac7cf0-1d44-4656-b137-f3008be32e1d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliverability-management
discoiquuid: 008d6a63-68cd-4e87-8adb-9642e2f9bb2a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 38700b79aeb19c75d10d2f5eb60c1efdb12e62e3

---


# Technische controle{#technical-monitoring}

## Technisch rapport over de aflevering {#technical-deliverability-monitoring}

Het technische rapport voor de bewaking van de leverantie wordt dagelijks bijgewerkt en is beschikbaar door naar **[!UICONTROL Monitoring]** > **[!UICONTROL Overview]** te navigeren en op de **[!UICONTROL Technical monitoring]** koppeling op het **[!UICONTROL Home]** tabblad Adobe Campagne te klikken. Het bevat een aantal kwaliteitsindicatoren voor de prestaties van uw platform.

Deze indicatoren worden dagelijks om 9.00 uur bijgewerkt.

>[!NOTE]
>
>Bovendien kunt u een dagelijks rapport per e-mail op een bepaald adres ontvangen. Laat ons het gewenste e-mailadres weten via e-mail of via het Adobe Campagne Extranet.

![](assets/s_tn_del_monitoring.png)

In het verslag worden de volgende indicatoren gebruikt:

* **[!UICONTROL Reverse DNS]** : De Campagne van Adobe controleert of omgekeerde DNS voor een IP adres wordt gegeven en dat dit correct naar IP wijst.

* **[!UICONTROL SPF]** (Beleidskader voor verzender): Een authentificatiemechanisme dat ISPs en brievenbusleveranciers toelaat om te controleren of de e-mailafzender op het verzendende domein wordt gemachtigd.

   <!--
    >[!NOTE]
    >
    >The SPF may look **[!UICONTROL Acceptable]** (instead of **[!UICONTROL Good]**) since the report is currently unable to detect the presence of a “redirect” or “include” mechanism. This bug has been submitted to Adobe Campaign R&D to be fixed. In the meantime, please feel free to add 15 points to your global score to obtain your real rating (a **[!UICONTROL Good]** one corresponds to 96 points or higher).
    -->

* **[!UICONTROL DomainKeys]** : Een service die door Yahoo is ontwikkeld en waarmee de identiteit van een e-mailafzender wordt gecertificeerd.

* **[!UICONTROL IP and RBL domain]** (Lijst voor realtime zwarte gaten): Een lijst van IP adressen en domeinen die door blocklist organisaties voor slechte verzendende reputatie zijn gemarkeerd. Deze lijsten worden bijgehouden door speciale organisaties zoals Spamhaus, Spamcop, SURBL/URIBL, enz. De Campagne van Adobe verwerkt momenteel controles tegen RBLs die een significant leverbaarheidseffect hebben. Deze RBLs wijzen op het verzenden van reputatie, en kan door ISPs worden van verwijzingen voorzien alvorens om uw e-mails te aanvaarden.

* **[!UICONTROL SNDS]** (Smart Network Data Services): Een [Windows Live Hotmail-service](https://sendersupport.olc.protection.outlook.com/snds/FAQ.aspx)tegen spam. Hotmail is enige ISP die dit type van informatie verstrekt. Benchmarkscores zijn een groen filterresultaat, een klachtenpercentage van minder dan 0,1% en geen spamvallen.

<!--
* **[!UICONTROL Reputation Authority]**: This WatchGuard’s score is calculated in real time according to the feedback received from their network worldwide, and also from the different users who use their software.

    Administrators can use such tools to apply a first level filter on their messaging servers.
    If you click on the IP link within the technical report, it will lead you to reputationauthority.org, where you will have the possibility to clean the IP history and get a neutral score again.
    Nevertheless, this action is limited to a number of times per month.
    Please also be aware there is no support provided by WatchGuard‘s Reputation Authority (sending delisting requests is therefore useless). Otherwise, this scoring is based on the following: 
    * Message content (for example: presence of spam words). 
    * IP/Domains reputation (for example: your IPs are listed on an RBL). 
    * IP configuration (for example: IPs associated to different domains). 
    * Volumes sent by IP (for example: presence of peaks or significant variations).
    
    * **[!UICONTROL Sender Score]** : A database of reputed servers ([https://www.senderscore.org/](https://www.senderscore.org/)) issuing a score created by Return Path about your reputation. Think of it like a credit score, but for email senders.-->

<!--## Delivery Reports - Broadcast Statistics {#delivery-reports-broadcast-statistics}

Each delivery will generate a broadcast statistics report when you open a delivery in the “Deliveries List”, which includes some reputation metrics that may impact your deliverability:

![](assets/s_tn_del_monitoring.png)-->
