---
product: campaign
title: Leveringen voor marketingcampagnes
description: Meer informatie over marketingcampagneleveringen
role: User
feature: Campaigns, Resource Management, Cross Channel Orchestration
hide: true
hidefromtoc: true
exl-id: 1dd3c080-444d-45f8-9562-d2d01a9d2860
source-git-commit: 4f809011a8b4cb3803c4e8151e358e5fd73634e4
workflow-type: tm+mt
source-wordcount: '1485'
ht-degree: 0%

---

# Leveringen voor marketingcampagnes {#marketing-campaign-deliveries}

Leveringen kunnen worden gemaakt via het campagnedashboard, een campagneworkflow of rechtstreeks via het overzicht van leveringen.

Wanneer de leveringen worden gemaakt op basis van een campagne, worden ze gekoppeld aan deze campagne en geconsolideerd op campagnereniveau.

![](assets/do-not-localize/how-to-video.png)[ ontdekt deze eigenschap in video ](#create-email-video)

## Leveringen maken {#creating-deliveries}

Als u een levering wilt maken die is gekoppeld aan een campagne, klikt u op de koppeling **[!UICONTROL Add a delivery]** in het campagnemdashboard.

![](assets/campaign_op_add_delivery.png)

De voorgestelde configuraties zijn geschikt voor de verschillende typen levering: direct mail, e-mail, mobiele kanalen. [Meer informatie](../../delivery/using/steps-about-delivery-creation-steps.md).

## Levering starten {#starting-a-delivery}

Zodra alle goedkeuringen zijn verleend, is de levering klaar om te worden begonnen. De leveringsprocedure is dan afhankelijk van het soort levering. Voor e-mail of mobiele kanaalleveringen, zie [ Beginnend een online levering ](#starting-an-online-delivery), en voor directe postleveringen, zie [ Beginnend een off-line levering ](#starting-an-offline-delivery).

### Een online levering starten {#starting-an-online-delivery}

Zodra alle goedkeuringsverzoeken zijn verleend, verandert de leveringsstatus in **[!UICONTROL Pending confirmation]** en kan door een exploitant worden begonnen. In voorkomend geval wordt de Adobe Campaign-exploitant (of groep marktdeelnemers) die als controleur is aangewezen om de levering te starten, ervan in kennis gesteld dat de levering klaar is om te worden gestart.

>[!NOTE]
>
>Als een specifieke exploitant of groep exploitanten voor het beginnen van een levering in de eigenschappen van de levering wordt aangewezen, kunt u de exploitant die voor de levering verantwoordelijk is ook toestaan om de verzending te bevestigen. Om dit te doen, activeer **NMS_ActivateOwnerConfirmation** optie door **1** als waarde in te gaan. De opties worden beheerd via het knooppunt **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Options]** in de Adobe Campaign-verkenner.
>  
>Om deze optie te deactiveren, ga **0** als waarde in. Het verzendbevestigingsproces functioneert vervolgens als standaard: alleen de exploitant of groep van exploitanten die voor de verzending zijn aangewezen in de leveringseigenschappen (of een beheerder) kan de verzending bevestigen en uitvoeren.

![](assets/s_ncs_user_edit_del_to_start_from_del.png)

De informatie verschijnt ook op het campagnedashboard. Met de koppeling **[!UICONTROL Confirm delivery]** kunt u de levering starten.

![](assets/s_ncs_user_edit_del_to_start.png)

Met een bevestigingsbericht kunt u deze handeling beveiligen.

### Offline levering starten {#starting-an-offline-delivery}

Zodra alle goedkeuringen zijn verleend, verandert de leveringsstatus in **[!UICONTROL Pending extraction]**. De extractiebestanden worden gemaakt met behulp van een speciale workflow die in de standaardconfiguratie automatisch wordt gestart wanneer een directe-maillevering in behandeling is voor extractie. Wanneer een proces bezig is, wordt het getoond in het dashboard en kan via zijn verbinding worden uitgegeven.

>[!NOTE]
>
>De technische werkschema&#39;s met betrekking tot het pakket van de Campagne worden voorgesteld in [ Lijst van technische werkschema&#39;s ](../../workflow/using/about-technical-workflows.md).

**Stap 1 - de goedkeuring van het Dossier**

Nadat de extractieworkflow is voltooid, moet het extractiebestand worden goedgekeurd (mits de goedkeuring van het extractiebestand is geselecteerd in de leveringsinstellingen).

Voor meer op dit, verwijs naar [ goedkeuren een extractiedossier ](../../campaign/using/marketing-campaign-approval.md#approving-an-extraction-file).

**Stap 2 - Goedkeuring van het bericht aan de dienstverlener**

* Zodra het extractiedossier wordt goedgekeurd, kunt u het bewijs van de e-mail van het routerbericht produceren. Dit e-mailbericht wordt samengesteld op basis van een leveringssjabloon. Het moet worden goedgekeurd.

  >[!NOTE]
  >
  >Deze stap is alleen beschikbaar als het verzenden en goedkeuren van proefdrukken is ingeschakeld in het venster Goedkeuring.

![](assets/s_ncs_user_file_valid_select_BAT.png)


* Klik op de knop **[!UICONTROL Send a proof]** om de proefdrukken te maken.

  Het proefdrukdoel moet vooraf worden gedefinieerd.

  U kunt zo veel proefdrukken maken als nodig is. Deze zijn toegankelijk via de **[!UICONTROL Direct mail...]** -koppeling van de leveringsdetails.

  ![](assets/s_ncs_user_file_notif_submit_proof.png)

* De leveringsstatus verandert in **[!UICONTROL To submit]** . Klik op de knop **[!UICONTROL Submit proofs]** om het goedkeuringsproces te starten.

  ![](assets/s_ncs_user_file_notif_submit_proof_validation.png)

* De leveringsstatus verandert in **[!UICONTROL Proof to validate]** en een knoop laat u goedkeuring goedkeuren of verwerpen.

  ![](assets/s_ncs_user_file_notif_supplier_link.png)

  U kunt deze goedkeuring accepteren of afwijzen of terugkeren naar de extractiestap.

  ![](assets/s_ncs_user_file_notif_supplier_link_confirm.png)

* Het extractiedossier wordt verzonden naar de router en de levering wordt gebeëindigd.

### Berekening van de kosten en voorraden {#calculation-of-costs-and-stocks}

Bij het uitpakken van bestanden worden twee bewerkingen gestart: budgetberekening en voorraadberekening. De begrotingsonderdelen worden bijgewerkt.

* Op het tabblad **[!UICONTROL Budget]** kunt u de budgetten voor de campagne beheren. Het totaal van de kostenvermeldingen wordt weergegeven in het veld **[!UICONTROL Calculates cost]** van het hoofdtabblad van de campagne en in het programma waartoe deze behoort. De bedragen zijn ook terug te vinden in de campagnebegroting.

  De echte kosten zullen uiteindelijk van informatie worden berekend die door de router wordt verstrekt. Alleen daadwerkelijk verzonden berichten worden gefactureerd.

* De voorraden worden gedefinieerd in het **[!UICONTROL Administration > Campaign management > Stocks]** knooppunt van de structuur en de kostenstructuren in het **[!UICONTROL Administration > Campaign management > Service providers]** -knooppunt.

  De voorraadlijnen zijn zichtbaar in de voorraadsectie. Als u de oorspronkelijke voorraad wilt definiëren, opent u een voorraadlijn. De voorraad wordt telkens verlaagd wanneer een levering plaatsvindt. U kunt een waarschuwingsniveau en meldingen definiëren.

>[!NOTE]
>
>Voor verdere informatie over kostenberekeningen en voorraadbeheer, zie [ Leveranciers, voorraden en begrotingen ](../../campaign/using/providers-stocks-and-budgets.md).

## Gekoppelde documenten beheren {#managing-associated-documents}

U kunt verschillende documenten koppelen aan een campagne: rapport, foto, webpagina, diagram, enzovoort. Deze documenten kunnen elke gewenste indeling hebben (Microsoft Word, PowerPoint, PNG, JPG, Acrobat PDF, enz.). Leer hoe te om documenten met een campagne [ in deze sectie ](../../campaign/using/marketing-campaign-assets.md) te verbinden.

>[!IMPORTANT]
>
>Deze modus is gereserveerd voor kleine documenten.

In een campagne kunt u ook andere objecten bekijken, zoals promotiecoupons, speciale aanbiedingen voor een specifieke winkel of filiaal, enzovoort. Wanneer deze elementen in een overzicht worden opgenomen, kunnen zij met een directe postlevering worden geassocieerd. [Meer informatie](#associating-and-structuring-resources-linked-via-a-delivery-outline).

>[!NOTE]
>
>Als u MRM gebruikt, kunt u een bibliotheek van marketing middelen ook beheren die voor verscheidene deelnemers voor samenwerkingswerk beschikbaar zijn. Zie [ marketing middelen beheren ](../../mrm/using/managing-marketing-resources.md).

### Documenten toevoegen {#adding-documents}

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

### Bronnen koppelen en structureren via een leveringsoverzicht {#associating-and-structuring-resources-linked-via-a-delivery-outline}

>[!NOTE]
>
>De leveringsschema&#39;s worden uitsluitend gebruikt in het kader van direct-mailcampagnes.

Een leveringsoverzicht geeft een gestructureerde reeks elementen aan (documenten, filialen/winkels, promotionele coupons, enz.) die in het bedrijf en voor een bepaalde campagne zijn gemaakt.

Deze elementen worden gegroepeerd in leveringsoverzichten, en een bepaald leveringsoverzicht zal met een levering worden geassocieerd; het zal in het winningsdossier worden van verwijzingen voorzien dat naar de **wordt verzonden dienstverlener** om aan de levering in bijlage te zijn. U kunt bijvoorbeeld een leveringsoverzicht maken dat verwijst naar een vertakking en de marketingbrochures die erin worden gebruikt.

Voor een campagne, laten de leveringsoutlines u externe elementen structureren die met de levering volgens bepaalde criteria moeten worden geassocieerd: verwante tak, promotieaanbieding die, uitnodiging aan een lokale gebeurtenis, enz. wordt verleend.

#### Een omtrek maken {#creating-an-outline}

Als u een omtrek wilt maken, klikt u op het subtabblad **[!UICONTROL Delivery outlines]** op het tabblad **[!UICONTROL Edit > Documents]** van de desbetreffende campagne.

>[!NOTE]
>
>Als dit tabblad niet aanwezig is, is deze functie niet beschikbaar voor deze campagne. Verwijs naar de configuratie van het campagnemalplaatje.
>   
>Voor meer op dit, verwijs naar [ malplaatjes van de Campagne ](../../campaign/using/marketing-campaign-templates.md#campaign-templates).

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
  >Voor meer op marketing middelen, verwijs naar [ het Leiden marketing middelen ](../../mrm/using/managing-marketing-resources.md).

#### Een omtrek selecteren {#selecting-an-outline}

Voor elke levering, kunt u het overzicht selecteren om van de sectie te associëren die voor het extractieoverzicht wordt gereserveerd, zoals in het volgende voorbeeld:

![](assets/s_ncs_user_op_select_composition.png)

De geselecteerde omtrek wordt vervolgens weergegeven in de onderste sectie van het venster. U kunt de afbeelding bewerken met het pictogram rechts van het veld of wijzigen met de vervolgkeuzelijst:

![](assets/s_ncs_user_op_select_composition_b.png)

Het tabblad **[!UICONTROL Summary]** van de levering geeft ook deze informatie weer:

![](assets/s_ncs_user_op_select_composition_c.png)

#### Extractie-resultaat {#extraction-result}

In het uitgepakt en aan de dienstverlener verzonden dossier worden de naam van het overzicht en, in voorkomend geval, zijn kenmerken (kosten, beschrijving, enz.) toegevoegd aan de inhoud volgens de informatie in het uitvoermalplaatje verbonden aan de dienstverlener.

In het volgende voorbeeld worden het label, de geschatte kosten en de beschrijving van de omtrek die aan de levering is gekoppeld, toegevoegd aan het extractiebestand.

![](assets/s_ncs_user_op_composition_in_export_template.png)

Het exportmodel moet worden gekoppeld aan de dienstverlener die voor de betrokken levering is geselecteerd. Zie [ Creërend dienstverleners en hun kostenstructuren ](../../campaign/using/providers-stocks-and-budgets.md#creating-service-providers-and-their-cost-structures).

>[!NOTE]
>
>Voor meer op de uitvoer, verwijs naar [ Begonnen het Worden ](../../platform/using/get-started-data-import-export.md) sectie.

#### Video over zelfstudie {#create-email-video}

In deze video wordt uitgelegd hoe u een campagne en een e-mail kunt maken in Adobe Campaign.

>[!VIDEO](https://video.tv.adobe.com/v/25604?quality=12)

De extra campagne hoe-aan video&#39;s is beschikbaar [ hier ](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=nl).
