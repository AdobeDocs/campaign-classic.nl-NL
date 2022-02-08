---
product: campaign
title: SMS maken met campagne
description: Meer informatie over het maken van SMS met campagne
feature: SMS
exl-id: 94aa4628-d973-433d-b963-b078e2d6672b
source-git-commit: 1e11b7419388698f5de366cbeddf2be88ef12873
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 3%

---

# Een sms-levering maken {#creating-a-sms-delivery}

![](../../assets/common.svg)

## Het leveringskanaal selecteren {#selecting-the-delivery-channel}

Volg onderstaande stappen om een nieuwe SMS-levering te maken:

>[!NOTE]
>
>Algemene concepten voor het creëren van levering worden weergegeven in [deze sectie](steps-about-delivery-creation-steps.md).

1. Maak een nieuwe levering, bijvoorbeeld via het dashboard Levering.
1. Selecteer de leveringssjabloon **Verzonden naar mobiele apparaten (SMPP)** die u eerder hebt gemaakt. Raadpleeg voor meer informatie de [De leveringssjabloon wijzigen](sms-set-up.md#changing-the-delivery-template) sectie.

   ![](assets/s_user_mobile_wizard.png)

1. Identificeer uw levering met een etiket, code, en beschrijving. Raadpleeg [deze sectie](steps-create-and-identify-the-delivery.md#identifying-the-delivery) voor meer informatie.
1. Klikken **[!UICONTROL Continue]** om deze informatie te bevestigen en het venster van de berichtconfiguratie te tonen.

## Definieer de content van de sms {#defining-the-sms-content}

Voer de volgende stappen uit om de inhoud van het SMS te maken:

1. Voer de inhoud van het bericht in het dialoogvenster **[!UICONTROL Text content]** van de wizard. Met de werkbalkknoppen kunt u inhoud importeren, opslaan of doorzoeken. De laatste knoop wordt gebruikt om verpersoonlijkingsgebieden op te nemen.

   ![](assets/s_ncs_user_wizard_sms01_138.png)

   Het gebruik van personalisatievelden wordt weergegeven in de [Over personalisatie](about-personalization.md) sectie.

1. Klikken **[!UICONTROL Preview]** onder aan de pagina om de weergave van het bericht met de personalisatie weer te geven. Als u de voorvertoning wilt starten, selecteert u een ontvanger met de **[!UICONTROL Test personalization]** in de werkbalk. U kunt een ontvanger selecteren uit de gedefinieerde doelen of een andere ontvanger kiezen.

   ![](assets/s_ncs_user_wizard_sms01_139.png)

   Je kunt het SMS-bericht goedkeuren. U kunt de inhoud van SMS ook bekijken op het scherm van de mobiele telefoon dat op het recht van de inhoudredacteur wordt getoond. Klik op het scherm en gebruik de muis om door de inhoud te schuiven.

   ![](assets/s_ncs_user_wizard_sms01_140.png)

1. Klik op de knop **[!UICONTROL Data loaded]** link naar de informatie over de ontvanger.

   ![](assets/s_user_mobile_wizard_sms_02.png)

   >[!NOTE]
   >
   >SMS-berichten mogen niet langer zijn dan 160 tekens als de codepagina Latin-1 (ISO-8859-1) wordt gebruikt. Als het bericht in Unicode wordt geschreven, moet het niet 70 karakters overschrijden. Bepaalde speciale tekens kunnen de lengte van het bericht beïnvloeden. Voor meer informatie over berichtlengte, verwijs naar [Vertaling van SMS-tekens](#about-character-transliteration) sectie.
   >
   >Wanneer verpersoonlijkingsgebieden of voorwaardelijke inhoudsgebieden aanwezig zijn, varieert de grootte van het bericht van één ontvanger aan andere. De lengte van het bericht moet worden geëvalueerd wanneer de personalisatie is uitgevoerd.
   >
   >Wanneer u de analyse start, wordt de lengte van berichten gecontroleerd en wordt een waarschuwing weergegeven in geval van overloop.

1. Als u de schakelaar NetSize of een schakelaar SMPP gebruikt, kunt u de naam van de leveringsafzender personaliseren. Raadpleeg voor meer informatie de [Geavanceerde parameters](#advanced-parameters) sectie.

## Doelpopulatie selecteren {#selecting-the-target-population}

Het gedetailleerde proces bij de selectie van de doelpopulatie van een levering wordt weergegeven in [deze sectie](steps-defining-the-target-population.md).

Voor meer informatie over het gebruik van verpersoonlijkingsgebieden, verwijs naar [deze sectie](about-personalization.md).

Voor meer informatie over het opnemen van een zaadlijst raadpleegt u [deze pagina](about-seed-addresses.md).
