---
product: campaign
title: Gebruiksscenario
description: Gebruiksscenario
feature: Subscriptions, Email, Data Management
badge-v8: label="Ook van toepassing op v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
audience: platform
content-type: reference
topic-tags: filtering-data
exl-id: 85ded096-7d27-41b3-8ef2-93f5ca8def82
hide: true
hidefromtoc: true
source-git-commit: 42cec0e9bede94a2995a5ad442822512bda14f2b
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 2%

---

# Gebruiksscenario{#use-case}



## Een filter maken in de e-mailindeling van abonnees {#creating-a-filter-on-the-email-format-of-subscribers}

Met deze gebruiksaanwijzing kunt u zien hoe u een filter maakt voor het sorteren van nieuwsbrieven-abonnementen op basis van de e-mailindeling van de ontvanger.

Hiervoor moet een vooraf gedefinieerd filter worden gebruikt: deze filters zijn gekoppeld aan een documenttype en zijn toegankelijk via het knooppunt **[!UICONTROL Administration > Configuration > Predefined filters]** . Deze gegevensfilters kunnen worden gebruikt voor elk type editor (of document) in de toepassing.

Gegevensfilters worden op dezelfde manier gemaakt als vooraf gedefinieerde filters, maar er is een extra veld om het documenttype te selecteren waarop het filter wordt toegepast.

Voer de volgende stappen uit:

1. Maak een nieuw filter via het knooppunt **[!UICONTROL Administration > Configuration > Predefined filters]** .
1. Klik op het pictogram **[!UICONTROL Select link]** om het desbetreffende document te selecteren:

   ![](assets/s_ncs_user_filter_choose_schema.png)

1. Selecteer het abonnementsschema (nms:abonnement) en klik op **[!UICONTROL OK]** .

   ![](assets/s_ncs_user_filter_select_schema.png)

1. Klik op **[!UICONTROL Edit link]** om de velden van het geselecteerde document weer te geven.

   ![](assets/s_ncs_user_filter_edit_schema.png)

   Vervolgens kunt u de inhoud van het geselecteerde document bekijken:

   ![](assets/s_ncs_user_filter_view_schema.png)

   U hebt toegang tot deze velden om filtervoorwaarden in de hoofdtekst van de filtereditor te definiëren. Een toepassingsfilter wordt op precies dezelfde manier gedefinieerd als een geavanceerd filter. Zie [ een geavanceerd filter ](../../platform/using/creating-filters.md#creating-an-advanced-filter) creëren.

1. Maak een nieuw filter op abonnementen om alleen abonnementen met een niet-gedefinieerde e-mailindeling weer te geven:

   ![](assets/s_ncs_user_filter_parameters.png)

1. Klik op **[!UICONTROL Save]** om een filter toe te voegen aan de vooraf gedefinieerde filters voor dit type lijst.
1. U kunt dit filter nu gebruiken op het tabblad **[!UICONTROL Subscriptions]** van het ontvangende profiel. U kunt het filter &quot;Onbekende e-mailindeling&quot; openen door op de knop **[!UICONTROL Filters]** te klikken.

   ![](assets/s_ncs_user_filter_on_events.png)

   De naam van het huidige filter wordt boven de lijst weergegeven. Als u het filter wilt annuleren, klikt u op het pictogram **[!UICONTROL Delete this filter]** .

   ![](assets/s_ncs_user_filter_on_subscriptions.png)
