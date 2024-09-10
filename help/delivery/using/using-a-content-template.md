---
product: campaign
title: Een contentsjabloon gebruiken
description: Een contentsjabloon gebruiken
badge-v8: label="Ook van toepassing op v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
feature: Templates
exl-id: e43dd68e-2e95-4367-9029-4622fbcb1759
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '436'
ht-degree: 2%

---

# Een contentsjabloon gebruiken{#using-a-content-template}



## Over inhoudssjablonen {#about-content-templates}

Er kan rechtstreeks naar inhoudssjablonen worden verwezen en deze kunnen worden gebruikt in leveringen. Verwijs naar [ Creërend een levering via inhoudsbeheer ](#creating-a-delivery-via-content-management)

Ze kunnen ook worden gebruikt om inhoudsinstanties te maken. Zodra zij zijn gecreeerd, zijn deze instanties klaar om te worden geleverd (verwijs naar [ leverend een inhoudsinstantie ](#delivering-a-content-instance)) of uitgevoerd (verwijs naar [ Creërend een inhoudsinstantie ](#creating-a-content-instance)).

## Levering maken via contentbeheer {#creating-a-delivery-via-content-management}

U kunt in een levering naar een inhoudssjabloon verwijzen om invoervelden te gebruiken om inhoud in te voeren. Een extra lusje wordt toegevoegd aan de leveringsmedewerker voor het bepalen van leveringsinhoud.

![](assets/s_ncs_content_deliver_a_content.png)

De lay-out wordt automatisch toegepast op basis van de geselecteerde instellingen. Als u deze wilt weergeven, klikt u op **[!UICONTROL HTML preview]** (of **[!UICONTROL Text preview]** ) en selecteert u een ontvanger om de personalisatie-elementen te testen.

![](assets/s_ncs_content_deliver_a_content_html.png)

Voor meer op dit, verwijs naar het volledige implementatievoorbeeld: [ Creërend inhoud in de leveringsmedewerker ](use-case-creating-content-management.md#creating-content-in-the-delivery-assistant).

## Inhoudsinstanties maken {#creating-a-content-instance}

U kunt inhoud direct in de boom van Adobe Campaign tot stand brengen die in werkschema&#39;s wordt gebruikt, wordt uitgevoerd, of direct in nieuwe leveringen wordt geïnjecteerd.

Voer de volgende stappen uit:

1. Selecteer het knooppunt **[!UICONTROL Resources > Contents]** van de structuur, klik met de rechtermuisknop en kies **[!UICONTROL Properties]** .

   ![](assets/s_ncs_content_folder_properties.png)

1. Selecteer de publicatiesjablonen die actief zijn voor deze map.

   ![](assets/s_ncs_content_folder_templates.png)

1. U kunt nu nieuwe inhoud maken met de knop **[!UICONTROL New]** boven de inhoudslijst.

   ![](assets/s_ncs_content_folder_create_a_template.png)

1. Voer de velden in het formulier in.

   ![](assets/s_ncs_content_folder_use_a_template.png)

1. Klik vervolgens op de tab **[!UICONTROL HTML preview]** om de rendering weer te geven. Hier, zijn de verpersoonlijkingsgebieden die uit het gegevensbestand worden genomen niet ingegaan.

   ![](assets/s_ncs_content_folder_use_a_template_preview.png)

1. Nadat de inhoud is gemaakt, wordt deze toegevoegd aan de lijst met beschikbare inhoud. Klik op de koppeling **[!UICONTROL Properties]** om het label, de status of de geschiedenis van de koppeling te wijzigen.

   ![](assets/s_ncs_content_folder_template_properties.png)

1. Indien nodig kan de inhoud worden gegenereerd met de desbetreffende knop op de werkbalk nadat de inhoud is goedgekeurd.

   ![](assets/s_ncs_content_folder_template_generate.png)

   >[!NOTE]
   >
   >U kunt het genereren van niet-goedgekeurde inhoud toestaan. Om dit te doen, verander de relevante optie in het publicatiemalplaatje. Voor meer op dit, verwijs naar [ Creërend en vormend het malplaatje ](publication-templates.md#creating-and-configuring-the-template).

   De inhoud van de HTML en van de Tekst wordt geproduceerd door gebrek in **het publiceren** omslag van de instantie van Adobe Campaign. U kunt de publicatiemap dankzij de **NcmPublishingDir** optie veranderen.

## Inhoudsinstantie leveren {#delivering-a-content-instance}

Als u een inhoudsinstantie wilt maken en leveren, moet een leveringssjabloon worden gekoppeld aan de publicatiesjabloon die wordt gebruikt om deze inhoud te genereren. Voor meer op dit, verwijs naar [ Levering ](publication-templates.md#delivery).

Bovendien moet de opslagmap voor inhoud worden toegewezen aan inhoud die is ontleend aan deze publicatiesjabloon (wanneer u met een inhoudsmap meerdere typen inhoud kunt genereren, kunnen leveringen niet automatisch worden gemaakt).

Als u de levering automatisch wilt maken op basis van de geselecteerde inhoud, klikt u op het pictogram **[!UICONTROL Delivery]** en kiest u de sjabloon.

![](assets/s_ncs_content_folder_create_the_delivery.png)

De inhoud van tekst en HTML wordt automatisch ingevoerd.
