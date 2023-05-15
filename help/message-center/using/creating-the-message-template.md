---
product: campaign
title: Transactieberichtsjablonen ontwerpen
description: Leer hoe u een transactiemalplaatje maakt en ontwerpt in Adobe Campaign Classic
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Transactional Messaging
exl-id: a52bc140-072e-4f81-b6da-f1b38662bce5
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '498'
ht-degree: 0%

---

# Transactieberichtsjablonen ontwerpen {#creating-the-message-template}



Om ervoor te zorgen dat elke gebeurtenis in een gepersonaliseerd bericht kan worden veranderd, moet u een berichtmalplaatje creëren om elk gebeurtenistype aan te passen.

>[!IMPORTANT]
>
>Gebeurtenistypen moeten vooraf worden gemaakt. Raadpleeg voor meer informatie hierover [Gebeurtenistypen maken](../../message-center/using/creating-event-types.md).

De transactionele berichtmalplaatjes bevatten de noodzakelijke informatie voor het personaliseren van het transactionele bericht. U kunt malplaatjes ook gebruiken om de berichtvoorproef te testen en proeven te verzenden gebruikend zaadadressen alvorens aan het definitieve doel te leveren. Zie voor meer informatie [Transactieberichtsjablonen testen](../../message-center/using/testing-message-templates.md).

## De berichtsjabloon maken {#creating-message-template}

1. Ga naar de **[!UICONTROL Message Center >Transactional message templates]** in de Adobe Campaign-structuur.

1. Klik in de lijst met transactiemalesjablonen met de rechtermuisknop en selecteer **[!UICONTROL New]** in het vervolgkeuzemenu of klik op de knop **[!UICONTROL New]** boven de lijst met transactiemalusjablonen voor berichten.

   ![](assets/messagecenter_create_model_001.png)

1. Selecteer in het leveringsvenster de leveringssjabloon die geschikt is voor het kanaal dat u wilt gebruiken.

   ![](assets/messagecenter_create_model_002.png)

1. Wijzig indien nodig het label.

1. Selecteer het type gebeurtenis dat overeenkomt met het bericht dat u wilt verzenden.

   ![](assets/messagecenter_create_model_003.png)

   Gebeurtenistypen moeten vooraf in de console worden gemaakt. Raadpleeg voor meer informatie hierover [Gebeurtenistypen maken](../../message-center/using/creating-event-types.md).

   >[!IMPORTANT]
   >
   >Een gebeurtenistype kan niet aan meer dan één malplaatje worden verbonden.

1. Voer een aard en beschrijving in en klik vervolgens op **[!UICONTROL Continue]** om het berichtlichaam tot stand te brengen (verwijs naar [Berichtinhoud maken](#creating-message-content)).

   ![](assets/messagecenter_create_model_004.png)

## Berichtinhoud maken {#creating-message-content}

De definitie van de inhoud van het transactiebericht is gelijk aan die voor normale leveringen in Adobe Campaign. Voor een e-maillevering kunt u bijvoorbeeld inhoud in HTML- of tekstindeling maken, bijlagen toevoegen of het bezorgingsobject aanpassen. Raadpleeg voor meer informatie de [E-maillevering](../../delivery/using/about-email-channel.md) hoofdstuk

>[!IMPORTANT]
>
>Afbeeldingen in het bericht moeten openbaar toegankelijk zijn. Adobe Campaign biedt geen mechanisme voor het uploaden van afbeeldingen voor transactieberichten.\
>In tegenstelling tot JSSP of webApp, `<%=` heeft geen standaardescape.
>
>In dit geval moet u alle gegevens die uit de gebeurtenis komen, op de juiste wijze verwijderen. Deze escape is afhankelijk van de manier waarop dit veld wordt gebruikt. Gebruik in een URL bijvoorbeeld encodeURIComponent. U kunt escapeXMLString gebruiken om in de HTML te worden weergegeven.

Zodra u uw berichtinhoud hebt bepaald, kunt u gebeurtenisinformatie in het berichtlichaam integreren en het personaliseren. Gebeurtenisgegevens worden via personalisatietags in de tekst ingevoegd.

![](assets/messagecenter_create_content_001.png)

* Alle verpersoonlijkingsgebieden komen van de lading.
* Het is mogelijk om één of verscheidene verpersoonlijkingsblokken in een transactiebericht van verwijzingen te voorzien. De blokinhoud wordt tijdens de publicatie aan de uitvoeringsinstantie toegevoegd aan de leveringsinhoud.

Voer de volgende stappen uit om personalisatietags in te voegen in de tekst van een e-mailbericht:

1. Klik in de berichtsjabloon op het tabblad dat overeenkomt met de e-mailindeling (HTML of tekst).

1. Voer de tekst van het bericht in.

1. Voeg in de tekst de tag in met behulp van de **[!UICONTROL Real time events > Event XML]** -menu.

   ![](assets/messagecenter_create_custo_002.png)

1. Vul de tag in met de volgende syntaxis: **elementnaam**.@**kenmerknaam** zoals hieronder weergegeven.

   ![](assets/messagecenter_create_custo_003.png)

1. Sla uw inhoud op.

Uw bericht is nu klaar om te worden [getest](../../message-center/using/testing-message-templates.md).
