---
title: SpamAssassin
seo-title: SpamAssassin
description: SpamAssassin
seo-description: null
page-status-flag: never-activated
uuid: 4f439432-4215-42ed-8f92-b4ca8dd92726
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliverability-management
discoiquuid: d41658ab-ee79-4a5c-a165-d94b81eb2b33
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 7dbc876fae0bde78e3088ee1ab986cd09e9bcc38

---


# SpamAssassin{#spamassassin}

## Info over SpamAssassin {#about-spamassassin}

De Campagne van Adobe kan worden gevormd om met [SpamAssassin](https://spamassassin.apache.org)te werken, een derdedienst die voor e-mailspamfiltratie wordt gebruikt. Dit staat u toe om e-mailberichten te scoren om te bepalen of een bericht het risico loopt om als spam door de anti-anti-spamhulpmiddelen worden beschouwd die op ontvangstbewijs worden gebruikt.

SpamAssassin maakt gebruik van diverse spamdetectietechnieken, waaronder:

* DNS-gebaseerde en op vage controlesom gebaseerde spamdetectie
* Bayesiaans filteren
* Externe programma&#39;s
* Blacklists
* Online databases

>[!NOTE]
>
>SpamAssassin moet op de toepassingsserver van de Campagne van Adobe worden geïnstalleerd en worden gevormd. Zie [deze sectie](../../installation/using/configuring-spamassassin.md)voor meer informatie.
>
>De regels die bepalen of een element al dan niet spam is worden beheerd via SpamAssassin en kunnen door een beheerder met voorrechten worden uitgegeven.

## SpamAssassin gebruiken {#using-spamassassin}

Nadat u de e-maillevering hebt gemaakt en de inhoud ervan hebt gedefinieerd, volgt u de onderstaande stappen om de risico&#39;s te evalueren.

Raadpleeg [deze sectie](../../delivery/using/about-email-channel.md)voor meer informatie over het maken en ontwerpen van een levering.

1. Ga naar het **[!UICONTROL Preview]** tabblad.
1. Selecteer een ontvanger om een voorvertoning van uw levering weer te geven.

   ![](assets/s_tn_del_preview_spamassassin_recipient.png)

   >[!NOTE]
   >
   >Als u geen ontvanger selecteert, kan de anti-spamcontrole niet worden uitgevoerd.

1. Het resultaat van de test wordt aangegeven met een waarschuwingsbericht. Als een hoog risiconiveau wordt gedetecteerd, wordt het volgende waarschuwingsbericht weergegeven:

   ![](assets/s_tn_del_preview_spamassassin_ko.png)

1. Klik op de **[!UICONTROL More...]** koppeling naast de waarschuwing.
1. Selecteer het **[!UICONTROL Anti-spam checking]** tabblad.
1. Ga naar de **[!UICONTROL Points / Rule / Description]** sectie om de redenen voor dit risico te bekijken.

   ![](assets/s_tn_del_msg_spamassassin_ko.png)

>[!NOTE]
>
>Telkens als u klikt **[!UICONTROL Anti-spam checking]**, wordt de dienst SpamAssassin geroepen en het bericht wordt opnieuw geanalyseerd voor anti-spamopsporing. Controleer of u de inhoud hebt gewijzigd voordat u de anti-spamanalyse opnieuw uitvoert.
