---
solution: Campaign Classic
product: campaign
title: Toegang tot een externe database
description: Toegang tot een externe database
audience: platform
content-type: reference
topic-tags: connectors
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 5%

---


# Datatoewijzing definiëren {#defining-data-mapping}

Met Adobe Campaign kunt u toewijzingen definiëren voor de gegevens in een externe tabel.

Om dit te doen, zodra het schema van de externe lijst is gecreeerd, moet u een nieuwe leveringsafbeelding tot stand brengen om de gegevens in deze lijst als leveringsdoel te gebruiken.

Hiervoor voert u de volgende stappen uit:

1. Maak een nieuwe leveringstoewijzing en kies de doeldimensie, het schema dat u net hebt gemaakt, bijvoorbeeld.

   ![](assets/wf_new_mapping_create_fda.png)

1. Geef de velden op waarin de leveringsgegevens zijn opgeslagen (achternaam, voornaam, e-mail, adres, enz.).

   ![](assets/wf_new_mapping_define_join.png)

1. Specificeer de parameters voor informatieopslag, met inbegrip van het achtervoegsel van de uitbreidingsregelingen om hen gemakkelijk identificeerbaar te zijn.

   ![](assets/wf_new_mapping_define_names.png)

   U kunt kiezen of om uitsluitingen (**excludelog**), met berichten (**broadlog**) of in een afzonderlijke lijst op te slaan.

   U kunt ook kiezen of het volgen voor deze leveringsafbeelding (**trackinglog**) te beheren.

1. Selecteer vervolgens de extensies waarmee u rekening wilt houden. Het extensietype is afhankelijk van de parameters en opties van uw platform (uw licentiecontract weergeven).

   ![](assets/wf_new_mapping_define_extensions.png)

   Klik op de knop **[!UICONTROL Save]** om het maken van de leveringstoewijzing te starten: alle gekoppelde tabellen worden automatisch gemaakt op basis van de geselecteerde parameters.
