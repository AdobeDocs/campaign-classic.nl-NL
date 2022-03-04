---
product: campaign
title: Een contentsjabloon gebruiken
description: Een contentsjabloon gebruiken
feature: Templates
exl-id: e43dd68e-2e95-4367-9029-4622fbcb1759
source-git-commit: 9839dbacda475c2a586811e3c4f686b1b1baab05
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 2%

---

# Een contentsjabloon gebruiken{#using-a-content-template}

![](../../assets/common.svg)

## Over inhoudssjablonen {#about-content-templates}

Er kan rechtstreeks naar inhoudssjablonen worden verwezen en deze kunnen worden gebruikt in leveringen. Zie [Levering maken via contentbeheer](#creating-a-delivery-via-content-management)

Ze kunnen ook worden gebruikt om inhoudsinstanties te maken. Zodra zij zijn gecreeerd, zijn deze instanties klaar om te worden geleverd (verwijs naar [Inhoudsinstantie leveren](#delivering-a-content-instance)) of geëxporteerd (zie [Inhoudsinstanties maken](#creating-a-content-instance)).

## Levering maken via contentbeheer {#creating-a-delivery-via-content-management}

U kunt in een levering naar een inhoudssjabloon verwijzen om invoervelden te gebruiken om inhoud in te voeren. Er wordt een extra tabblad toegevoegd aan de wizard voor levering voor het definiëren van inhoud voor levering.

![](assets/s_ncs_content_deliver_a_content.png)

De lay-out wordt automatisch toegepast op basis van de geselecteerde instellingen. Klik op de knop **[!UICONTROL HTML preview]** (of **[!UICONTROL Text preview]** ) en selecteer een ontvanger om personalisatie-elementen te testen.

![](assets/s_ncs_content_deliver_a_content_html.png)

Raadpleeg het voorbeeld van de volledige implementatie voor meer informatie hierover: [Inhoud maken in de wizard voor levering](use-case--creating-content-management.md#creating-content-in-the-delivery-wizard).

## Inhoudsinstanties maken {#creating-a-content-instance}

U kunt inhoud direct in de boom van Adobe Campaign tot stand brengen die in werkschema&#39;s wordt gebruikt, wordt uitgevoerd, of direct in nieuwe leveringen wordt geïnjecteerd.

Voer de volgende stappen uit:

1. Selecteer **[!UICONTROL Resources > Contents]** knoop van de boom, klik met de rechtermuisknop aan en kies **[!UICONTROL Properties]**.

   ![](assets/s_ncs_content_folder_properties.png)

1. Selecteer de publicatiesjablonen die actief zijn voor deze map.

   ![](assets/s_ncs_content_folder_templates.png)

1. U kunt nu nieuwe inhoud maken met de opdracht **[!UICONTROL New]** boven de inhoudslijst.

   ![](assets/s_ncs_content_folder_create_a_template.png)

1. Voer de velden in het formulier in.

   ![](assets/s_ncs_content_folder_use_a_template.png)

1. Klik vervolgens op de knop **[!UICONTROL HTML preview]** om de rendering weer te geven. Hier, zijn de verpersoonlijkingsgebieden die uit het gegevensbestand worden genomen niet ingegaan.

   ![](assets/s_ncs_content_folder_use_a_template_preview.png)

1. Nadat de inhoud is gemaakt, wordt deze toegevoegd aan de lijst met beschikbare inhoud. Klik op de knop **[!UICONTROL Properties]** koppeling gebruiken om het label, de status of de geschiedenis ervan te wijzigen.

   ![](assets/s_ncs_content_folder_template_properties.png)

1. Indien nodig kan de inhoud worden gegenereerd met de desbetreffende knop op de werkbalk nadat de inhoud is goedgekeurd.

   ![](assets/s_ncs_content_folder_template_generate.png)

   >[!NOTE]
   >
   >U kunt het genereren van niet-goedgekeurde inhoud toestaan. Om dit te doen, verander de relevante optie in het publicatiemalplaatje. Raadpleeg voor meer informatie hierover [De sjabloon maken en configureren](publication-templates.md#creating-and-configuring-the-template).

   De inhoud van HTML en Tekst wordt standaard gegenereerd in het dialoogvenster **publiceren** map van het Adobe Campaign-exemplaar. U kunt de publicatiemap wijzigen met de opdracht **NcmPublishingDir** optie.

## Inhoudsinstantie leveren {#delivering-a-content-instance}

Als u een inhoudsinstantie wilt maken en leveren, moet een leveringssjabloon worden gekoppeld aan de publicatiesjabloon die wordt gebruikt om deze inhoud te genereren. Raadpleeg voor meer informatie hierover [Aflevering](publication-templates.md#delivery).

Bovendien moet de opslagmap voor inhoud worden toegewezen aan inhoud die is ontleend aan deze publicatiesjabloon (wanneer u met een inhoudsmap meerdere typen inhoud kunt genereren, kunnen leveringen niet automatisch worden gemaakt).

Als u de levering automatisch wilt maken op basis van de geselecteerde inhoud, klikt u op de knop **[!UICONTROL Delivery]** en kiest u de sjabloon.

![](assets/s_ncs_content_folder_create_the_delivery.png)

De inhoud van tekst en HTML wordt automatisch ingevoerd.
