---
title: Hoe te om gevolgde verbindingen te vormen
seo-title: Hoe te om gevolgde verbindingen te vormen
description: Hoe te om gevolgde verbindingen te vormen
seo-description: null
page-status-flag: never-activated
uuid: 0fb41a43-8a84-4a61-bf93-97e1d448a5ec
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: tracking-messages
discoiquuid: 9cae3861-88eb-447a-aa23-9d1de0710eec
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 3522f4f50770dde220610cd5f1c4084292d8f1f5
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---


# Hoe te om gevolgde verbindingen te vormen{#how-to-configure-tracked-links}

Voor elke levering, kunt u de ontvangst van berichten en de activering van de verbindingen volgen die in de berichtinhoud worden opgenomen. Hierdoor kunt u het gedrag van ontvangers volgen na de leveringsacties waarop ze waren gericht.

>[!NOTE]
>
>Het volgen is op berichten van toepassing, maar Webtracking laat u controleren hoe de ontvangers door een website (bezochte pagina&#39;s, aankopen) bladeren.
>
>De configuratie van webtracking wordt in [deze sectie](../../configuration/using/about-web-tracking.md)weergegeven.

Berichten bijhouden is standaard ingeschakeld. Volg onderstaande stappen om de manier waarop URL&#39;s worden bijgehouden aan te passen:

1. Selecteer de **[!UICONTROL Display URLs]** optie in de onderste sectie van de leveringstovenaar, onder de berichtinhoud.

   ![](assets/s_ncs_user_email_del_display_urls.png)

   Wanneer u een URL selecteert in de lijst met bijgehouden URL&#39;s, wordt deze gemarkeerd in de leveringsinhoud - behalve de koppeling op de spiegelpagina en de koppeling voor het opzeggen van het abonnement die standaard wordt aangeboden.

   ![](assets/s_ncs_user_email_del_show_urls.png)

1. Geef voor elke URL van het bericht op of u reeksspatiëring wilt activeren.

   >[!IMPORTANT]
   >
   >Wanneer de URL van de koppeling als een label wordt gebruikt, wordt aangeraden het bijhouden van gegevens te desactiveren om het risico van afwijzing door phishing te voorkomen.
   >
   >Als bijvoorbeeld de URL www.adobe.com in het bericht wordt ingevoegd en de URL wordt gevolgd, wordt de inhoud van de hypertekstkoppeling gewijzigd in https://nlt.adobe.net/r/?id=xxxxxx. Dit betekent dat het als frauduleus kan worden beschouwd door ontvangers van berichten.

1. Wijzig zo nodig het trackinglabel, dubbelklik op het label en voer een nieuw label in.

   >[!NOTE]
   >
   >De labels van de bijgehouden URL&#39;s en de labels kunnen worden gewijzigd om het lezen van informatie bij het bijhouden van leveringen te vereenvoudigen. Twee URL&#39;s of twee labels met dezelfde naam worden bij het berekenen van het aantal klikken opgeteld.

1. Wijzig zo nodig de modus Tekstspatiëring en selecteer een nieuwe modus in de **[!UICONTROL Tracking]** kolom die overeenkomt met de doelkoppeling, zoals hieronder wordt getoond:

   ![](assets/s_ncs_user_select_tracking_mode.png)

   Voor elke afzonderlijke URL kunt u de modus Tekstspatiëring instellen op een van de volgende waarden:

   * **[!UICONTROL Enabled]** : activeert tracking op deze URL.
   * **[!UICONTROL Not tracked]** : activeert tracering op deze URL niet.
   * **[!UICONTROL Always enabled]** : activeert het bijhouden van deze URL altijd. Deze informatie wordt opgeslagen zodat de volgende keer, als de URL opnieuw wordt weergegeven in een toekomstige berichtinhoud, de tekstspatiëring automatisch wordt geactiveerd.
   * **[!UICONTROL Never tracked]** : activeert het bijhouden van deze URL nooit. Deze informatie wordt opgeslagen zodat de volgende keer dat de URL opnieuw wordt weergegeven in een toekomstig bericht, de URL automatisch wordt gedeactiveerd.
   * **[!UICONTROL Opt-out]** : beschouwt deze URL als een opt-out- of niet-abonnements-URL.
   * **[!UICONTROL Mirror page]** : beschouwt deze URL als een URL van een spiegelpagina.

1. Bovendien kunt u een categorie selecteren voor elke bijgehouden URL in de vervolgkeuzelijst van de **[!UICONTROL Category]** kolom. Deze categorieën kunnen rapporten worden getoond, zoals bijvoorbeeld in **[!UICONTROL URLs and click streams]** (zie [deze sectie](../../reporting/using/reports-on-deliveries.md#urls-and-click-streams)). Categorieën worden gedefinieerd in een specifieke opsomming: **[!UICONTROL urlCategory]** (Zie [Opsommingen](../../platform/using/managing-enumerations.md)beheren).
