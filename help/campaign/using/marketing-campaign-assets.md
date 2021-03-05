---
solution: Campaign Classic
product: campaign
title: Documenten en overzichten van de marketingcampagne
description: Meer informatie over marketingcampagnedocumenten en leveringscontouren
audience: campaign
content-type: reference
topic-tags: orchestrate-campaigns
translation-type: tm+mt
source-git-commit: 87028ec81a8cae6793d45d7c840511b59cd0287c
workflow-type: tm+mt
source-wordcount: '755'
ht-degree: 0%

---


# Gekoppelde documenten {#managing-associated-documents} beheren

U kunt verschillende documenten aan een campagne koppelen: rapporten, foto&#39;s, webpagina&#39;s, diagrammen, enz. Deze documenten kunnen elke gewenste indeling hebben (Microsoft Word, PowerPoint, PNG, JPG, Acrobat PDF, enzovoort).

>[!IMPORTANT]
>
>Deze mogelijkheid is gereserveerd voor kleine elementen en documenten.

In een campagne kunt u ook andere objecten bekijken, zoals promotiecoupons, speciale aanbiedingen voor een bepaald merk of een bepaalde winkel, enzovoort. Wanneer deze elementen in een overzicht worden opgenomen, kunnen zij met een directe postlevering worden geassocieerd. Zie [Bronnen koppelen en structureren via een leveringsoverzicht](#associating-and-structuring-resources-linked-via-a-delivery-outline).

>[!NOTE]
>
>Als u de module van het Beheer van het Middel van de Marketing van de Campagne gebruikt, kunt u een bibliotheek van marketing middelen ook beheren die voor verscheidene gebruikers voor samenwerkingswerk beschikbaar zijn. [Meer informatie](../../campaign/using/managing-marketing-resources.md).

## Documenten {#adding-documents} toevoegen

Documenten kunnen worden gekoppeld op campagneniveau (contextuele documenten) of op programmaniveau (algemene documenten).

Het tabblad **[!UICONTROL Documents]** bevat:

* De lijst met alle documenten die vereist zijn voor de inhoud (sjabloon, afbeeldingen, enz.) die door Adobe Campaign-operatoren met de juiste rechten lokaal kunnen worden gedownload,
* Documenten die informatie voor de router bevatten, als om het even welk.

De documenten zijn gekoppeld aan het programma of de campagne via het tabblad **[!UICONTROL Edit > Documents]**.

![](assets/s_ncs_user_op_add_document.png)

U kunt ook een document aan een campagne toevoegen via de koppeling die in het dashboard wordt aangeboden.

![](assets/add_a_document_in_op.png)

Klik op het pictogram **[!UICONTROL Details]** om de inhoud van een bestand weer te geven en informatie toe te voegen:

![](assets/s_ncs_user_op_add_document_details.png)

In het dashboard worden documenten die bij de campagne horen gegroepeerd in de sectie **[!UICONTROL Document(s)]**, zoals in het volgende voorbeeld:

![](assets/s_ncs_user_op_edit_document.png)

U kunt ze ook vanuit deze weergave bewerken en wijzigen.

## Bronnen koppelen en structureren via een leveringsoverzicht {#associating-and-structuring-resources-linked-via-a-delivery-outline}

>[!NOTE]
>
>De leveringsschema&#39;s worden uitsluitend gebruikt in het kader van direct-mailcampagnes.

Een leveringsoverzicht geeft een gestructureerde reeks elementen aan (documenten, opslagplaatsen, promotionele coupons, enz.) door het bedrijf en voor een bepaalde campagne worden opgericht.

Deze elementen worden gegroepeerd in leveringsoverzichten, en elk leveringsoverzicht zal met een levering worden geassocieerd; in het extractiebestand dat naar de **serviceprovider** wordt verzonden, wordt ernaar verwezen om aan de levering te worden gekoppeld. U kunt bijvoorbeeld een leveringsoverzicht maken dat verwijst naar een vertakking en de marketingbrochures die erin worden gebruikt.

Voor een campagne, laten de leveringsoverzichten u externe elementen structureren die met de levering volgens bepaalde criteria moeten worden geassocieerd: verwante branche, aangeboden promotieaanbieding, uitnodiging voor een lokale evenement, enz.

### Een omtrek maken {#creating-an-outline}

Als u een omtrek wilt maken, klikt u op het subtabblad **[!UICONTROL Delivery outlines]** op het tabblad **[!UICONTROL Edit > Documents]** van de desbetreffende campagne.

>[!NOTE]
>
>Als dit tabblad niet aanwezig is, is deze functie niet beschikbaar voor deze campagne. Verwijs naar de configuratie van het campagnemalplaatje.
>   
>Raadpleeg [deze sectie](../../campaign/using/marketing-campaign-templates.md#campaign-templates) voor meer informatie over sjablonen.

![](assets/s_ncs_user_op_composition_link.png)

Klik vervolgens op **[!UICONTROL Add a delivery outline]** en maak de hiërarchie van contouren voor de campagne:

1. Klik met de rechtermuisknop op de basis van de structuur en selecteer **[!UICONTROL New > Delivery outlines]**.
1. Klik met de rechtermuisknop op de omtrek die u net hebt gemaakt en selecteer **[!UICONTROL New > Item]** of **[!UICONTROL New > Personalization fields]**.

![](assets/s_ncs_user_op_add_composition.png)

Een overzicht kan punten en verpersoonlijkingsgebieden, middelen en aanbiedingen bevatten:

* Items kunnen bijvoorbeeld fysieke documenten zijn waarnaar hier wordt verwezen en die hier worden beschreven en die aan de levering worden gekoppeld.
* Met velden voor personalisatie kunt u personalisatie-elementen maken die te maken hebben met leveringen in plaats van met ontvangers. Het is dus mogelijk waarden te creëren die in leveringen voor een specifiek doel moeten worden gebruikt (welkomstaanbod, korting, enz.) Ze worden gemaakt in Adobe Campaign en geïmporteerd in de omtrek via de koppeling **[!UICONTROL Import personalization fields...]**.

   ![](assets/s_ncs_user_op_add_composition_field.png)

   Ze kunnen ook rechtstreeks in de omtrek worden gemaakt door op het pictogram **[!UICONTROL Add]** rechts van de lijstzone te klikken.

   ![](assets/s_ncs_user_op_add_composition_field_button.png)

* De bronnen zijn marketingbronnen die worden gegenereerd in het dashboard voor marketingbronnen dat wordt geopend via de koppeling **[!UICONTROL Resources]** van het **[!UICONTROL Campaigns]** universum.

   ![](assets/s_ncs_user_mkg_resource_ovv.png)

   >[!NOTE]
   >
   >Raadpleeg [deze sectie](../../campaign/using/managing-marketing-resources.md) voor meer informatie over marketingbronnen.

### Een omtrek selecteren {#selecting-an-outline}

Voor elke levering, kunt u het overzicht selecteren om van de sectie te associëren die voor het extractieoverzicht wordt gereserveerd, zoals in het volgende voorbeeld:

![](assets/s_ncs_user_op_select_composition.png)

De geselecteerde omtrek wordt vervolgens weergegeven in de onderste sectie van het venster. U kunt de afbeelding bewerken met het pictogram rechts van het veld of wijzigen met de vervolgkeuzelijst:

![](assets/s_ncs_user_op_select_composition_b.png)

Op het tabblad **[!UICONTROL Summary]** van de levering wordt ook deze informatie weergegeven:

![](assets/s_ncs_user_op_select_composition_c.png)

### Extractieresultaat {#extraction-result}

In het dossier dat wordt uitgepakt en aan de dienstverlener wordt toegezonden, de naam van de omtrek en, in voorkomend geval, de kenmerken ervan (kosten, beschrijving enz.) worden toegevoegd aan de inhoud volgens de informatie in het uitvoermalplaatje verbonden aan de dienstverlener.

In het volgende voorbeeld worden het label, de geschatte kosten en de beschrijving van de omtrek die aan de levering is gekoppeld, toegevoegd aan het extractiebestand.

![](assets/s_ncs_user_op_composition_in_export_template.png)

Het exportmodel moet worden gekoppeld aan de dienstverlener die voor de betrokken levering is geselecteerd. Zie [deze sectie](../../campaign/using/providers--stocks-and-budgets.md#creating-service-providers-and-their-cost-structures).

>[!NOTE]
>
>Raadpleeg [deze sectie](../../platform/using/get-started-data-import-export.md) voor meer informatie over exporteren.
