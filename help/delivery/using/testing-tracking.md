---
title: Tekstspatiëring
seo-title: Tekstspatiëring
description: Tekstspatiëring
seo-description: null
page-status-flag: never-activated
uuid: 76d84ab4-b632-4498-96a1-ce9c773ec125
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: tracking-messages
discoiquuid: 4ed23249-4ecf-4e57-91b3-6fae1387bd6a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Tekstspatiëring{#testing-tracking}

U kunt het bijhouden van wijzigingen testen op spiegelpagina&#39;s, e-maillogboeken en koppelingen. Dit doet u als volgt:

1. Maak een nieuwe e-maillevering die wordt gebruikt voor het testen.
1. Geef de gebruiker op die de e-mail zal ontvangen. Aangezien deze gebruiker het e-mailbericht moet openen en op de koppelingen moet klikken die het bevat, moet u een adres voor de testontvanger selecteren dat u beheert.
1. Voeg een spiegelpagina (MirrorPage) verpersoonlijkingsblok in de e-mailinhoud toe.
1. Verzend de levering die een verbinding aan de spiegelpagina bevat.
1. Nadat u het e-mailbericht hebt ontvangen, opent u het en klikt u op de koppeling naar de spiegelpagina.
1. Nadat u correct aan de spiegelpagina wordt opnieuw gericht, open het **Beleid > de omslag van Technische werkschema** en open het **Volgen** werkschema.
1. Start de workflow, klik met de rechtermuisknop op de activiteit **Planner** en selecteer **Taak die in behandeling is nu** uitvoeren.
1. Wacht ongeveer 30 seconden, dan selecteer de **Controle** tabel. Zorg ervoor dat ten minste één logrecord voor bijhouden is gevonden.

   Klik op **Vernieuwen** als er geen nieuwe logbestanden worden weergegeven.

1. Ga naar de profielpagina van de ontvanger u voor de test gebruikte, en selecteer het **Volgen** lusje. Sommige records moeten worden weergegeven met de waarde voor **Pagina** spiegelen in de kolom **Type** .

   >[!NOTE]
   >
   >De profielpagina van de ontvanger bevindt zich standaard in de map **Profielen en doelen > Ontvangers** .

   Als u het bijhouden van e-maillogbestanden wilt controleren, zoekt u de waarden **Open** en **[!UICONTROL Email click]** in de kolom **Type** .

   Als de geopende logboeken niet worden weergegeven, gaat u naar de levering en opent u de bijbehorende **eigenschappen** om ervoor te zorgen dat zowel de optie **Tekstspatiëring** activeren als de **[!UICONTROL Opens tracking]** opties zijn ingeschakeld.

