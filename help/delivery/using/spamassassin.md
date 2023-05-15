---
product: campaign
title: SpamAssassin
description: Leer hoe te opstelling e-mailspamopsporing met SpamAssassin
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Email, Deliverability
exl-id: 8be6836d-f7dc-4199-b2b2-b6a9cac9d162
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 6%

---

# SpamAssassin{#spamassassin}



Adobe Campaign kan worden geconfigureerd om te werken met [SpamAssassin](https://spamassassin.apache.org), een service van derden die wordt gebruikt voor het filteren van e-mailspam. Dit staat u toe om e-mailberichten te scoren om te bepalen of een bericht het risico loopt om als spam door de anti-anti-spamhulpmiddelen worden beschouwd die op ontvangstbewijs worden gebruikt.

SpamAssassin maakt gebruik van diverse spamdetectietechnieken, waaronder:

* DNS-gebaseerde en op vage controlesom gebaseerde spamdetectie
* Bayesiaans filteren
* Externe programma&#39;s
* Lijsten van gewezen personen
* Online databases

>[!NOTE]
>
>SpamAssassin moet op de de toepassingsserver van Adobe Campaign worden geïnstalleerd en worden gevormd. Raadpleeg [deze sectie](../../installation/using/configuring-spamassassin.md) voor meer informatie.
>
>De regels die bepalen of een element al dan niet spam is worden beheerd via SpamAssassin en kunnen door een beheerder met voorrechten worden uitgegeven.

## SpamAssassin gebruiken in campagne {#using-spamassassin}

Nadat u de e-maillevering hebt gemaakt en de inhoud ervan hebt gedefinieerd, volgt u de onderstaande stappen om de risico&#39;s te evalueren.

Raadpleeg voor meer informatie over het maken en ontwerpen van een levering [deze sectie](about-email-channel.md).

1. Ga naar het tabblad **[!UICONTROL Preview]**. 
1. Selecteer een ontvanger om een voorvertoning van uw levering weer te geven.

   ![](assets/s_tn_del_preview_spamassassin_recipient.png)

   >[!NOTE]
   >
   >Als u geen ontvanger selecteert, kan de anti-spamcontrole niet worden uitgevoerd.

1. Het resultaat van de test wordt aangegeven met een waarschuwingsbericht. Als een hoog risiconiveau wordt gedetecteerd, wordt het volgende waarschuwingsbericht weergegeven:

   ![](assets/s_tn_del_preview_spamassassin_ko.png)

1. Klik op de knop **[!UICONTROL More...]** naast de waarschuwing.
1. Selecteer het tabblad **[!UICONTROL Anti-spam checking]**. 
1. Ga naar de **[!UICONTROL Points / Rule / Description]** om de redenen voor dit risico te bekijken.

   ![](assets/s_tn_del_msg_spamassassin_ko.png)

>[!NOTE]
>
>Elke keer dat u op de knop **[!UICONTROL Anti-spam checking]**, wordt de dienst SpamAssassin geroepen en het bericht wordt opnieuw geanalyseerd voor anti-spamopsporing. Controleer of u de inhoud hebt gewijzigd voordat u de anti-spamanalyse opnieuw uitvoert.
