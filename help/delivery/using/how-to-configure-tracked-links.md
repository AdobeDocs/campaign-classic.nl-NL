---
product: campaign
title: Bijgehouden koppelingen configureren
description: Bijgehouden koppelingen configureren
badge-v8: label="Ook van toepassing op v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
feature: Monitoring
role: User, Developer
exl-id: ed88e1d6-c0d5-4a85-9f3e-be670f4bcc10
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '583'
ht-degree: 10%

---

# Bijgehouden koppelingen configureren{#how-to-configure-tracked-links}



Voor elke levering kunt u de ontvangst van berichten en de activering van de koppelingen die in de berichtcontent zijn opgenomen, opvolgen. Hierdoor kunt u het gedrag van ontvangers volgen na de leveringsacties waarvoor ze als doel zijn opgegeven.

Het volgen is op berichten van toepassing, maar het Web volgen laat u controleren hoe de ontvangers door een website (bezochte pagina&#39;s, aankopen) doorbladeren. De configuratie van webtracking wordt weergegeven in [deze sectie](../../configuration/using/about-web-tracking.md).

>[!NOTE]
>
>De koppelingen in e-mailinhoud die personalisatie bevatten, moeten specifiek worden gesynchroniseerd om te worden bijgehouden. Voor meer op hoe te om verbindingen in e-mails toe te voegen die kunnen worden gepersonaliseerd en die steun het volgen, verwijs naar [ deze sectie ](tracking-personalized-links.md).

We raden u ten zeerste aan URL&#39;s op te nemen in scheidingstekens op het tabblad **[!UICONTROL Text content]** voordat u de volgende formule toepast. De URL-scheidingstekens die u op dit tabblad invoert, worden door Adobe Campaign gebruikt om URL&#39;s binnen tekenreeksen te identificeren. U kunt deze paren scheidingstekens gebruiken:
* Haakjes ( )
* Haakjes [ ]
* Accolades { }

In dit voorbeeld wordt de URL https://www.adobe.com gevolgd door een puntkomma. De puntkomma kan door ontvangers e-mailcliënten als deel van URL worden geïnterpreteerd. Hierdoor kan de koppeling worden verbroken. U kunt dit probleem voorkomen door de URL op een van de volgende manieren in te sluiten in scheidingstekens:
* (https://www.adobe.com);
* [ https://www.adobe.com];
* {https://www.adobe.com};

Berichten bijhouden is standaard ingeschakeld. Volg onderstaande stappen om de manier waarop URL&#39;s worden bijgehouden aan te passen:

1. Selecteer de optie **[!UICONTROL Display URLs]** in de onderste sectie van de leveringsassistent, onder de berichtinhoud.

   ![](assets/s_ncs_user_email_del_display_urls.png)

   Wanneer u een URL selecteert in de lijst met bijgehouden URL&#39;s, wordt deze gemarkeerd in de leveringsinhoud - behalve de koppeling op de spiegelpagina en de koppeling voor het opzeggen van het abonnement die standaard wordt aangeboden.

   ![](assets/s_ncs_user_email_del_show_urls.png)

1. Geef voor elke URL van het bericht op of u reeksspatiëring wilt activeren.

   >[!IMPORTANT]
   >
   >Wanneer de URL van de koppeling als een label wordt gebruikt, wordt aangeraden de tracering te deactiveren om het risico van afkeuring door phishing te voorkomen.
   >
   >Als bijvoorbeeld de URL www.adobe.com in het bericht wordt ingevoegd en de URL wordt gevolgd, wordt de inhoud van de hypertekstkoppeling gewijzigd in https://nlt.adobe.net/r/?id=xxxxxx. Dit betekent dat het als frauduleus kan worden beschouwd door ontvangers van berichten.

1. Wijzig zo nodig het trackinglabel, dubbelklik op het label en voer een nieuw label in.

   >[!NOTE]
   >
   >De labels van de bijgehouden URL&#39;s en de labels kunnen worden gewijzigd om het lezen van informatie bij het bijhouden van leveringen te vereenvoudigen. Twee URL&#39;s of twee labels met dezelfde naam worden bij het berekenen van het aantal klikken opgeteld.

1. Wijzig zo nodig de modus Tekstspatiëring en selecteer een nieuwe modus in de kolom **[!UICONTROL Tracking]** die overeenkomt met de doelkoppeling, zoals hieronder wordt getoond:

   ![](assets/s_ncs_user_select_tracking_mode.png)

   Voor elke afzonderlijke URL kunt u de modus Tekstspatiëring instellen op een van de volgende waarden:

   * **[!UICONTROL Enabled]** : activeert tracering op deze URL.
   * **[!UICONTROL Not tracked]** : activeert het bijhouden van wijzigingen op deze URL.
   * **[!UICONTROL Always enabled]** : activeert het bijhouden van deze URL altijd. Deze informatie wordt opgeslagen zodat de volgende keer, als de URL opnieuw wordt weergegeven in een toekomstige berichtinhoud, de tekstspatiëring automatisch wordt geactiveerd.
   * **[!UICONTROL Never tracked]** : activeert nooit het bijhouden van deze URL. Deze informatie wordt opgeslagen zodat de volgende keer dat de URL opnieuw wordt weergegeven in een toekomstig bericht, de URL automatisch wordt gedeactiveerd.
   * **[!UICONTROL Opt-out]** : beschouwt deze URL als een opt-out- of niet-abonnements-URL.
   * **[!UICONTROL Mirror page]** : beschouwt deze URL als een URL van een spiegelpagina.

1. Bovendien kunt u een categorie selecteren voor elke bijgehouden URL in de vervolgkeuzelijst van de kolom **[!UICONTROL Category]** . Deze categorieën kunnen rapporten, zoals bijvoorbeeld in **[!UICONTROL URLs and click streams]** worden getoond (zie [ deze sectie ](../../reporting/using/reports-on-deliveries.md#urls-and-click-streams)). De categorieën worden bepaald in een specifieke opsomming: **[!UICONTROL urlCategory]** (zie [ Leidend opsommingen ](../../platform/using/managing-enumerations.md)).
