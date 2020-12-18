---
solution: Campaign Classic
product: campaign
title: Berichtcontent maken
description: Berichtcontent maken
audience: message-center
content-type: reference
topic-tags: message-templates
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 3%

---


# Berichtcontent maken{#creating-message-content}

De definitie van de inhoud van het transactiebericht is gelijk aan die voor normale leveringen in Adobe Campaign. U kunt bijvoorbeeld voor een e-maillevering inhoud in HTML- of tekstindeling maken, bijlagen toevoegen of het bezorgingsobject aanpassen. Raadpleeg voor meer informatie het hoofdstuk over [E-maillevering](../../delivery/using/about-email-channel.md).

>[!IMPORTANT]
>
>Afbeeldingen in het bericht moeten openbaar toegankelijk zijn. Adobe Campaign biedt geen mechanisme voor het uploaden van afbeeldingen voor transactieberichten.\
>In tegenstelling tot JSSP of webApp heeft `<%=` geen standaardescaping.
>
>In dit geval moet u alle gegevens die uit de gebeurtenis komen, op de juiste wijze verwijderen. Deze escape is afhankelijk van de manier waarop dit veld wordt gebruikt. Gebruik in een URL bijvoorbeeld encodeURIComponent. U kunt escapeXMLString gebruiken om in de HTML te worden weergegeven.

Zodra u uw berichtinhoud hebt bepaald, kunt u gebeurtenisinformatie in het berichtlichaam integreren en het personaliseren. Gebeurtenisgegevens worden via personalisatietags in de tekst ingevoegd.

![](assets/messagecenter_create_content_001.png)

* Alle verpersoonlijkingsgebieden komen van de lading.
* Het is mogelijk om één of verscheidene verpersoonlijkingsblokken in een transactiebericht van verwijzingen te voorzien. De blokinhoud wordt tijdens de publicatie aan de uitvoeringsinstantie toegevoegd aan de leveringsinhoud.

Voer de volgende stappen uit om personalisatietags in te voegen in de tekst van een e-mailbericht:

1. Klik in de berichtsjabloon op het tabblad dat overeenkomt met de e-mailindeling (HTML of tekst).
1. Voer de tekst van het bericht in.
1. Voeg de tag in de tekst in met de menu&#39;s **[!UICONTROL Real time events>Event XML]**.

   ![](assets/messagecenter_create_custo_002.png)

1. Vul de tag in met de volgende syntaxis: **elementnaam**.@**kenmerknaam** zoals hieronder getoond.

   ![](assets/messagecenter_create_custo_003.png)

