---
solution: Campaign Classic
product: campaign
title: Tracking van tests
description: Tracking van tests
audience: delivery
content-type: reference
topic-tags: tracking-messages
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '250'
ht-degree: 3%

---


# Tracking van tests{#testing-tracking}

U kunt het bijhouden van wijzigingen testen op spiegelpagina&#39;s, e-maillogboeken en koppelingen. Dit doet u als volgt:

1. Maak een nieuwe e-maillevering die wordt gebruikt voor het testen.
1. Geef de gebruiker op die de e-mail zal ontvangen. Aangezien deze gebruiker het e-mailbericht moet openen en op de koppelingen moet klikken die het bevat, moet u een adres voor de testontvanger selecteren dat u beheert.
1. Voeg een spiegelpagina (MirrorPage) verpersoonlijkingsblok in de e-mailinhoud toe.
1. Verzend de levering die een verbinding aan de spiegelpagina bevat.
1. Nadat u het e-mailbericht hebt ontvangen, opent u het en klikt u op de koppeling naar de spiegelpagina.
1. Nadat u correct aan de spiegelpagina wordt opnieuw gericht, heb toegang tot **Beheer > Technische werkschema&#39;s** omslag en open **Tracking** werkschema.
1. Start de workflow, klik met de rechtermuisknop op **Scheduler** en selecteer **Taak in behandeling nu uitvoeren**.
1. Wacht ongeveer 30 seconden, dan selecteer **Audit** tabel. Zorg ervoor dat ten minste één logrecord voor bijhouden is gevonden.

   Klik **Vernieuwen** als u geen nieuwe logboeken ziet.

1. Ga naar de profielpagina van de ontvanger u voor de test gebruikte, en selecteer **Tracking** tabel. Sommige records moeten worden weergegeven met de waarde **Pagina spiegelen** in de kolom **Type**.

   >[!NOTE]
   >
   >De profielpagina van de ontvanger bevindt zich standaard in de map **Profielen en doelen > Ontvangers**.

   Als u het bijhouden van e-maillogbestanden wilt controleren, zoekt u de waarden **Open** en **[!UICONTROL Email click]** in de kolom **Type**.

   Als de open logboeken niet verschijnen, ga naar de levering en open zijn **Eigenschappen** om ervoor te zorgen dat zowel **het volgen** als **[!UICONTROL Opens tracking]** opties wordt gecontroleerd.

