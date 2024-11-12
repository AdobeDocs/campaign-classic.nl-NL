---
product: campaign
title: SMS maken met campagne
description: Meer informatie over het maken van SMS met campagne
feature: SMS
role: User
exl-id: 94aa4628-d973-433d-b963-b078e2d6672b
source-git-commit: 41296a0acaee93d31874bf58287e51085c6c1261
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 2%

---

# Een sms-levering maken {#creating-a-sms-delivery}

## Het leveringskanaal selecteren {#selecting-the-delivery-channel}

Volg onderstaande stappen om een nieuwe SMS-levering te maken:

>[!NOTE]
>
>De globale concepten op leveringsverwezenlijking worden voorgesteld in [ deze sectie ](steps-about-delivery-creation-steps.md).

1. Maak een nieuwe levering, bijvoorbeeld via het dashboard Levering.
1. Selecteer het leveringsmalplaatje **Verzonden aan mobiele telefoons (SMPP)** dat u vroeger creeerde. Voor meer op dit, verwijs naar [ Verandering de 1} sectie van het leveringsmalplaatje.](sms-set-up.md#changing-the-delivery-template)

   ![](assets/s_user_mobile_wizard.png)

1. Identificeer uw levering met een etiket, code, en beschrijving. Raadpleeg [deze sectie](steps-create-and-identify-the-delivery.md#identifying-the-delivery) voor meer informatie.
1. Klik op **[!UICONTROL Continue]** om deze informatie te bevestigen en het venster voor berichtconfiguratie weer te geven.

## De SMS-inhoud definiëren {#defining-the-sms-content}

Voer de volgende stappen uit om de inhoud van het SMS te maken:

1. Voer de inhoud van het bericht in in de sectie **[!UICONTROL Text content]** van de assistent. Met de werkbalkknoppen kunt u inhoud importeren, opslaan of doorzoeken. De laatste knoop wordt gebruikt om verpersoonlijkingsgebieden op te nemen.

   ![](assets/s_ncs_user_wizard_sms01_138.png)

   Het gebruik van verpersoonlijkingsgebieden wordt voorgesteld in [ Ongeveer verpersoonlijkings ](about-personalization.md) sectie.

1. Klik op **[!UICONTROL Preview]** onder aan de pagina om het bericht met de bijbehorende personalisatie weer te geven. Selecteer een ontvanger met de knop **[!UICONTROL Test personalization]** op de werkbalk om de voorvertoning te starten. U kunt een ontvanger selecteren uit de gedefinieerde doelen of een andere ontvanger kiezen.

   ![](assets/s_ncs_user_wizard_sms01_139.png)

   Je kunt het SMS-bericht goedkeuren. U kunt de inhoud van SMS ook bekijken op het scherm van de mobiele telefoon dat op het recht van de inhoudredacteur wordt getoond. Klik op het scherm en schuif met de muis door de inhoud.

   ![](assets/s_ncs_user_wizard_sms01_140.png)

1. Klik op de koppeling **[!UICONTROL Data loaded]** om de informatie over de ontvanger weer te geven.

   ![](assets/s_user_mobile_wizard_sms_02.png)

   >[!NOTE]
   >
   >SMS-berichten mogen niet langer zijn dan 160 tekens als de codepagina Latin-1 (ISO-8859-1) wordt gebruikt. Als het bericht in Unicode wordt geschreven, moet het niet 70 karakters overschrijden. Bepaalde speciale tekens kunnen de lengte van het bericht beïnvloeden. Voor meer informatie over berichtlengte, verwijs naar de [ het karaktervertaling van SMS ](#about-character-transliteration) sectie.
   >
   >Wanneer verpersoonlijkingsgebieden of voorwaardelijke inhoudsgebieden aanwezig zijn, varieert de grootte van het bericht van één ontvanger aan andere. De lengte van het bericht moet worden geëvalueerd wanneer de personalisatie is uitgevoerd.
   >
   >Wanneer u de analyse start, wordt de lengte van berichten gecontroleerd en wordt een waarschuwing weergegeven in geval van overloop.

1. Als u de schakelaar NetSize of een schakelaar SMPP gebruikt, kunt u de naam van de leveringsafzender personaliseren. Voor meer op dit, verwijs naar de [ Geavanceerde parameters ](#advanced-parameters) sectie.

## Doelpopulatie selecteren {#selecting-the-target-population}

Het gedetailleerde proces wanneer het selecteren van de doelbevolking van een levering wordt voorgesteld in [ deze sectie ](steps-defining-the-target-population.md).

Voor meer op het gebruik van verpersoonlijkingsgebieden, verwijs naar [ deze sectie ](about-personalization.md).

Voor meer op de opneming van een zaadlijst, verwijs naar [ deze pagina ](about-seed-addresses.md).
