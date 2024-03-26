---
product: campaign
title: Gebruiksscenario
description: Gebruiksscenario
feature: Subscriptions, Email, Data Management
badge-v7: label="v7" type="Informative" tooltip="Is van toepassing op Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
audience: platform
content-type: reference
topic-tags: filtering-data
exl-id: 85ded096-7d27-41b3-8ef2-93f5ca8def82
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 2%

---

# Gebruiksscenario{#use-case}



## Een filter maken in de e-mailindeling van abonnees {#creating-a-filter-on-the-email-format-of-subscribers}

Met deze gebruiksaanwijzing kunt u zien hoe u een filter maakt voor het sorteren van nieuwsbrieven-abonnementen op basis van de e-mailindeling van de ontvanger.

Hiervoor moet een vooraf gedefinieerd filter worden gebruikt: deze filters zijn gekoppeld aan een documenttype en zijn toegankelijk via de **[!UICONTROL Administration > Configuration > Predefined filters]** knooppunt. Deze gegevensfilters kunnen worden gebruikt voor elk type editor (of document) in de toepassing.

Gegevensfilters worden op dezelfde manier gemaakt als vooraf gedefinieerde filters, maar er is een extra veld om het documenttype te selecteren waarop het filter wordt toegepast.

Voer de volgende stappen uit:

1. Een nieuw filter maken via het dialoogvenster **[!UICONTROL Administration > Configuration > Predefined filters]** knooppunt.
1. Klik op de knop **[!UICONTROL Select link]** pictogram om het betrokken document te selecteren:

   ![](assets/s_ncs_user_filter_choose_schema.png)

1. Selecteer het abonnementsschema (nms:abonnement) en klik op **[!UICONTROL OK]**.

   ![](assets/s_ncs_user_filter_select_schema.png)

1. Klikken **[!UICONTROL Edit link]** om de velden van het geselecteerde document weer te geven.

   ![](assets/s_ncs_user_filter_edit_schema.png)

   Vervolgens kunt u de inhoud van het geselecteerde document bekijken:

   ![](assets/s_ncs_user_filter_view_schema.png)

   U hebt toegang tot deze velden om filtervoorwaarden in de hoofdtekst van de filtereditor te definiëren. Een toepassingsfilter wordt op precies dezelfde manier gedefinieerd als een geavanceerd filter. Zie [Een geavanceerd filter maken](../../platform/using/creating-filters.md#creating-an-advanced-filter).

1. Maak een nieuw filter op abonnementen om alleen abonnementen met een niet-gedefinieerde e-mailindeling weer te geven:

   ![](assets/s_ncs_user_filter_parameters.png)

1. Klikken **[!UICONTROL Save]** om een filter aan de vooraf bepaalde filters voor dit type van lijst toe te voegen.
1. U kunt dit filter nu gebruiken in het dialoogvenster **[!UICONTROL Subscriptions]** tabblad van het ontvangende profiel; u kunt het filter Onbekende e-mailindeling openen door op het tabblad **[!UICONTROL Filters]** knop.

   ![](assets/s_ncs_user_filter_on_events.png)

   De naam van het huidige filter wordt boven de lijst weergegeven. Als u het filter wilt annuleren, klikt u op de knop **[!UICONTROL Delete this filter]** pictogram.

   ![](assets/s_ncs_user_filter_on_subscriptions.png)
