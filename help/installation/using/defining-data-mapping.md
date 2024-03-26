---
product: campaign
title: Externe gegevenstoewijzing definiëren
description: Leer hoe u gegevens in een externe database kunt toewijzen
feature: Installation, Instance Settings
badge-v7-only: label="v7" type="Informative" tooltip="Alleen van toepassing op Campaign Classic v7"
exl-id: a7253ca7-47e5-4def-849d-3ce1c9b948fb
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '201'
ht-degree: 6%

---

# Externe gegevenstoewijzing definiëren {#defining-data-mapping}



Met Adobe Campaign kunt u toewijzingen definiëren voor de gegevens in een externe tabel.

Om dit te doen, zodra het schema van de externe lijst is gecreeerd, moet u een nieuwe leveringsafbeelding tot stand brengen om de gegevens in deze lijst als leveringsdoel te gebruiken.

Hiervoor voert u de volgende stappen uit:

1. Maak een nieuwe leveringstoewijzing en kies de doeldimensie, het schema dat u net hebt gemaakt, bijvoorbeeld.

   ![](assets/wf_new_mapping_create_fda.png)

1. Geef de velden op waarin de leveringsgegevens zijn opgeslagen (achternaam, voornaam, e-mail, adres, enz.).

   ![](assets/wf_new_mapping_define_join.png)

1. Specificeer de parameters voor informatieopslag, met inbegrip van het achtervoegsel van de uitbreidingsregelingen om hen gemakkelijk identificeerbaar te zijn.

   ![](assets/wf_new_mapping_define_names.png)

   U kunt kiezen of u uitsluitingen wilt opslaan (**excludelog**), met berichten (**uitzenden**) of in een aparte tabel.

   U kunt ook kiezen of u het bijhouden van gegevens voor deze leveringstoewijzing wilt beheren (**trackinglog**).

1. Selecteer vervolgens de extensies waarmee u rekening wilt houden. Het extensietype is afhankelijk van de parameters en opties van uw platform (uw licentiecontract weergeven).

   ![](assets/wf_new_mapping_define_extensions.png)

   Klik op de knop **[!UICONTROL Save]** knop om het maken van de leveringstoewijzing te starten: alle gekoppelde tabellen worden automatisch gemaakt op basis van de geselecteerde parameters.
