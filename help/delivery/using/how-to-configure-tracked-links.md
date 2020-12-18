---
solution: Campaign Classic
product: campaign
title: Getraceerde koppelingen configureren
description: Getraceerde koppelingen configureren
audience: delivery
content-type: reference
topic-tags: tracking-messages
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 11%

---


# Getraceerde koppelingen configureren{#how-to-configure-tracked-links}

Voor elke levering kunt u de ontvangst van berichten en de activering van de koppelingen die in de berichtcontent zijn opgenomen, opvolgen. Hierdoor kunt u het gedrag van ontvangers volgen na de leveringsacties waarvoor ze als doel zijn opgegeven.

>[!NOTE]
>
>Het volgen is op berichten van toepassing, maar het Web volgen laat u controleren hoe de ontvangers door een website (bezochte pagina&#39;s, aankopen) doorbladeren.
>
>De configuratie van web tracking wordt weergegeven in [deze sectie](../../configuration/using/about-web-tracking.md).

Berichten bijhouden is standaard ingeschakeld. Volg onderstaande stappen om de manier waarop URL&#39;s worden bijgehouden aan te passen:

1. Selecteer de optie **[!UICONTROL Display URLs]** in de onderste sectie van de leveringstovenaar, onder de berichtinhoud.

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

1. Wijzig zo nodig de modus Tekstspatiëring en selecteer een nieuwe modus in de kolom **[!UICONTROL Tracking]** die overeenkomt met de doelkoppeling, zoals hieronder wordt getoond:

   ![](assets/s_ncs_user_select_tracking_mode.png)

   Voor elke afzonderlijke URL kunt u de modus Tekstspatiëring instellen op een van de volgende waarden:

   * **[!UICONTROL Enabled]** : activeert tracking op deze URL.
   * **[!UICONTROL Not tracked]** : activeert tracering op deze URL niet.
   * **[!UICONTROL Always enabled]** : activeert het bijhouden van deze URL altijd. Deze informatie wordt opgeslagen zodat de volgende keer, als de URL opnieuw wordt weergegeven in een toekomstige berichtinhoud, de tekstspatiëring automatisch wordt geactiveerd.
   * **[!UICONTROL Never tracked]** : activeert het bijhouden van deze URL nooit. Deze informatie wordt opgeslagen zodat de volgende keer dat de URL opnieuw wordt weergegeven in een toekomstig bericht, de URL automatisch wordt gedeactiveerd.
   * **[!UICONTROL Opt-out]** : beschouwt deze URL als een opt-out- of niet-abonnements-URL.
   * **[!UICONTROL Mirror page]** : beschouwt deze URL als een URL van een spiegelpagina.

1. Daarnaast kunt u een categorie selecteren voor elke bijgehouden URL in de vervolgkeuzelijst van de kolom **[!UICONTROL Category]**. Deze categorieën kunnen rapporten, zoals bijvoorbeeld in **[!UICONTROL URLs and click streams]** (zie [deze sectie](../../reporting/using/reports-on-deliveries.md#urls-and-click-streams)) worden getoond. Categorieën worden gedefinieerd in een specifieke opsomming: **[!UICONTROL urlCategory]** (zie [Opsommingen beheren](../../platform/using/managing-enumerations.md)).
