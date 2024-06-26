---
product: campaign
title: Testen van berichten
description: Leer hoe u berichttracering kunt testen
badge-v8: label="Ook van toepassing op v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
feature: Monitoring
role: User
exl-id: 16ad36b7-c13e-4b77-86ca-41c9ef174172
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 1%

---

# Testen van berichten{#testing-tracking}

U kunt het bijhouden van wijzigingen testen op spiegelpagina&#39;s, e-maillogboeken en koppelingen. Dit doet u als volgt:

1. Maak een nieuwe e-maillevering die wordt gebruikt voor het testen.
1. Geef de gebruiker op die de e-mail zal ontvangen. Aangezien deze gebruiker het e-mailbericht moet openen en op de koppelingen moet klikken die het bevat, moet u een adres voor de testontvanger selecteren dat u beheert.
1. Voeg een spiegelpagina (MirrorPage) verpersoonlijkingsblok in de e-mailinhoud toe.
1. Verzend de levering die een verbinding aan de spiegelpagina bevat.
1. Nadat u het e-mailbericht hebt ontvangen, opent u het en klikt u op de koppeling naar de spiegelpagina.
1. Nadat u correct aan de spiegelpagina wordt opnieuw gericht, open **Beheer > Technische workflows** en opent u de **Tekstspatiëring** workflow.
1. Start de workflow en klik met de rechtermuisknop op de knop **Planner** activiteit en selecteer **Taak die in behandeling is nu uitvoeren**.
1. Wacht ongeveer 30 seconden, dan selecteer **Audit** tab. Zorg ervoor dat ten minste één logrecord voor bijhouden is gevonden.

   Klikken **Vernieuwen** als er geen nieuwe logbestanden worden weergegeven.

1. Ga naar de profielpagina van de ontvanger u voor de test gebruikte, en selecteer **Tekstspatiëring** tab. Sommige records moeten worden weergegeven bij de **Pagina spiegelen** waarde in de **Type** kolom.

   >[!NOTE]
   >
   >De profielpagina van de ontvanger bevindt zich in de **Profielen en doelen > Ontvangers** map standaard.

   Als u het bijhouden van het e-maillogboek wilt controleren, zoekt u de waarden **Openen** en **[!UICONTROL Email click]** in de **Type** kolom.

   Als de open logboeken niet verschijnen, ga naar de levering en open tot zijn **Eigenschappen** om ervoor te zorgen dat beide **Tekstspatiëring activeren** en **[!UICONTROL Opens tracking]** opties zijn ingeschakeld.
