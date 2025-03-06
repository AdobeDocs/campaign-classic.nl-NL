---
product: campaign
title: Documenten en overzichten van de marketingcampagne
description: Meer informatie over documenten en overzichten van marketingcampagnes
role: User
feature: Campaigns
hide: true
hidefromtoc: true
exl-id: 891252b0-4700-4a2a-a632-63aad5ce75d7
source-git-commit: 4f809011a8b4cb3803c4e8151e358e5fd73634e4
workflow-type: tm+mt
source-wordcount: '755'
ht-degree: 0%

---

# Gekoppelde documenten beheren {#managing-associated-documents}

U kunt verschillende documenten aan een campagne koppelen: rapporten, foto&#39;s, webpagina&#39;s, diagrammen, enz. Deze documenten kunnen elke gewenste indeling hebben (Microsoft Word, PowerPoint, PNG, JPG, Acrobat PDF, enz.).

>[!IMPORTANT]
>
>Deze mogelijkheid is gereserveerd voor kleine elementen en documenten.

In een campagne kunt u ook andere objecten bekijken, zoals promotiecoupons, speciale aanbiedingen voor een bepaald merk of een bepaalde winkel, enzovoort. Wanneer deze elementen in een overzicht worden opgenomen, kunnen zij met een directe postlevering worden geassocieerd. Zie [ verbind en structuurmiddelen die via een leveringsoverzicht ](#associating-and-structuring-resources-linked-via-a-delivery-outline) worden verbonden.

>[!NOTE]
>
>Als u de module van het Beheer van het Middel van de Marketing van de Campagne gebruikt, kunt u een bibliotheek van marketing middelen ook beheren die voor verscheidene gebruikers voor samenwerkingswerk beschikbaar zijn. [Meer informatie](../../mrm/using/managing-marketing-resources.md).

## Documenten toevoegen {#adding-documents}

Documenten kunnen worden gekoppeld op campagneniveau (contextuele documenten) of op programmaniveau (algemene documenten).

Het tabblad **[!UICONTROL Documents]** bevat:

* De lijst met alle documenten die vereist zijn voor de inhoud (sjabloon, afbeeldingen, enz.) die lokaal kunnen worden gedownload door Adobe Campaign-operatoren met de juiste rechten,
* Documenten die informatie voor de router bevatten, als om het even welk.

De documenten zijn gekoppeld aan het programma of de campagne via het tabblad **[!UICONTROL Edit > Documents]** .

![](assets/s_ncs_user_op_add_document.png)

U kunt ook een document aan een campagne toevoegen via de koppeling die in het dashboard wordt aangeboden.

![](assets/add_a_document_in_op.png)

Klik op het pictogram **[!UICONTROL Details]** om de inhoud van een bestand weer te geven en informatie toe te voegen:

![](assets/s_ncs_user_op_add_document_details.png)

In het dashboard worden documenten die bij de campagne horen gegroepeerd in de sectie **[!UICONTROL Document(s)]** , zoals in het volgende voorbeeld:

![](assets/s_ncs_user_op_edit_document.png)

U kunt ze ook vanuit deze weergave bewerken en wijzigen.

## Bronnen koppelen en structureren via een leveringsoverzicht {#associating-and-structuring-resources-linked-via-a-delivery-outline}

>[!NOTE]
>
>De leveringsschema&#39;s worden uitsluitend gebruikt in het kader van direct-mailcampagnes.

Een leveringsoverzicht geeft een gestructureerde reeks elementen aan (documenten, winkels, promotionele coupons, enz.) die door het bedrijf en voor een bepaalde campagne zijn gemaakt.

Deze elementen worden gegroepeerd in leveringsoverzichten, en elk leveringsoverzicht zal met een levering worden geassocieerd; het zal in het winningsdossier worden van verwijzingen voorzien dat naar de **wordt verzonden dienstverlener** om aan de levering in bijlage te zijn. U kunt bijvoorbeeld een leveringsoverzicht maken dat verwijst naar een vertakking en de marketingbrochures die erin worden gebruikt.

Voor een campagne, laten de leveringsoutlines u externe elementen structureren die met de levering volgens bepaalde criteria moeten worden geassocieerd: verwante tak, promotieaanbieding die, uitnodiging aan een lokale gebeurtenis, enz. wordt verleend.

### Een omtrek maken {#creating-an-outline}

Als u een omtrek wilt maken, klikt u op het subtabblad **[!UICONTROL Delivery outlines]** op het tabblad **[!UICONTROL Edit > Documents]** van de desbetreffende campagne.

>[!NOTE]
>
>Als dit tabblad niet aanwezig is, is deze functie niet beschikbaar voor deze campagne. Verwijs naar de configuratie van het campagnemalplaatje.
>   
>Voor meer op malplaatjes, verwijs naar [ deze sectie ](../../campaign/using/marketing-campaign-templates.md#campaign-templates).

![](assets/s_ncs_user_op_composition_link.png)

Klik vervolgens op **[!UICONTROL Add a delivery outline]** en maak een hiërarchie van contouren voor de campagne:

1. Klik met de rechtermuisknop op de basis van de structuur en selecteer **[!UICONTROL New > Delivery outlines]** .
1. Klik met de rechtermuisknop op de omtrek die u zojuist hebt gemaakt en selecteer **[!UICONTROL New > Item]** of **[!UICONTROL New > Personalization fields]** .

![](assets/s_ncs_user_op_add_composition.png)

Een overzicht kan punten en verpersoonlijkingsgebieden, middelen en aanbiedingen bevatten:

* Items kunnen bijvoorbeeld fysieke documenten zijn waarnaar hier wordt verwezen en die hier worden beschreven en die aan de levering worden gekoppeld.
* Met velden voor personalisatie kunt u personalisatie-elementen maken die te maken hebben met leveringen in plaats van met ontvangers. Het is dus mogelijk waarden te creëren die in leveringen voor een specifiek doel moeten worden gebruikt (welkomstaanbod, korting, enz.) Ze worden gemaakt in Adobe Campaign en geïmporteerd in de omtrek via de koppeling **[!UICONTROL Import personalization fields...]** .

  ![](assets/s_ncs_user_op_add_composition_field.png)

  U kunt ze ook rechtstreeks in de omtrek maken door op het pictogram **[!UICONTROL Add]** rechts van de lijstzone te klikken.

  ![](assets/s_ncs_user_op_add_composition_field_button.png)

* De bronnen zijn marketingbronnen die zijn gegenereerd in het dashboard voor marketingbronnen en die via de koppeling **[!UICONTROL Resources]** op het tabblad **[!UICONTROL Campaigns]** kunnen worden benaderd.

  ![](assets/s_ncs_user_mkg_resource_ovv.png)

  >[!NOTE]
  >
  >Voor meer op marketing middelen, verwijs naar [ deze sectie ](../../mrm/using/managing-marketing-resources.md).

### Een omtrek selecteren {#selecting-an-outline}

Voor elke levering, kunt u het overzicht selecteren om van de sectie te associëren die voor het extractieoverzicht wordt gereserveerd, zoals in het volgende voorbeeld:

![](assets/s_ncs_user_op_select_composition.png)

De geselecteerde omtrek wordt vervolgens weergegeven in de onderste sectie van het venster. U kunt de afbeelding bewerken met het pictogram rechts van het veld of wijzigen met de vervolgkeuzelijst:

![](assets/s_ncs_user_op_select_composition_b.png)

Het tabblad **[!UICONTROL Summary]** van de levering geeft ook deze informatie weer:

![](assets/s_ncs_user_op_select_composition_c.png)

### Extractie-resultaat {#extraction-result}

In het uitgepakt en aan de dienstverlener verzonden dossier worden de naam van het overzicht en, in voorkomend geval, zijn kenmerken (kosten, beschrijving, enz.) toegevoegd aan de inhoud volgens de informatie in het uitvoermalplaatje verbonden aan de dienstverlener.

In het volgende voorbeeld worden het label, de geschatte kosten en de beschrijving van de omtrek die aan de levering is gekoppeld, toegevoegd aan het extractiebestand.

![](assets/s_ncs_user_op_composition_in_export_template.png)

Het exportmodel moet worden gekoppeld aan de dienstverlener die voor de betrokken levering is geselecteerd. Zie [ deze sectie ](../../campaign/using/providers-stocks-and-budgets.md#creating-service-providers-and-their-cost-structures).

>[!NOTE]
>
>Voor meer op de uitvoer, verwijs naar [ deze sectie ](../../platform/using/get-started-data-import-export.md) sectie.
