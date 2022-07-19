---
product: campaign
title: Leveringen voor marketingcampagnes
description: Meer informatie over marketingcampagneleveringen
feature: Campaigns, Resource Management, Cross Channel Orchestration
exl-id: 1dd3c080-444d-45f8-9562-d2d01a9d2860
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: tm+mt
source-wordcount: '1487'
ht-degree: 2%

---

# Leveringen voor marketingcampagnes {#marketing-campaign-deliveries}

![](../../assets/v7-only.svg)

Leveringen kunnen worden gemaakt via het campagnedashboard, een campagneworkflow of rechtstreeks via het overzicht van leveringen.

Wanneer de leveringen worden gemaakt op basis van een campagne, worden ze gekoppeld aan deze campagne en geconsolideerd op campagnereniveau.

![](assets/do-not-localize/how-to-video.png)[ Ontdek deze functie in video](#create-email-video)

## Leveringen maken {#creating-deliveries}

Als u een levering wilt maken die is gekoppeld aan een campagne, klikt u op de knop **[!UICONTROL Add a delivery]** koppeling in het campagnedashboard.

![](assets/campaign_op_add_delivery.png)

De voorgestelde configuraties zijn geschikt voor de verschillende typen levering: direct mail, e-mail, mobiele kanalen. [Meer informatie](../../delivery/using/steps-about-delivery-creation-steps.md).

## Levering starten {#starting-a-delivery}

Zodra alle goedkeuringen zijn verleend, is de levering klaar om te worden begonnen. De leveringsprocedure is dan afhankelijk van het soort levering. Voor e-mail- of mobiele-kanaalleveringen raadpleegt u [Een online levering starten](#starting-an-online-delivery)en voor direct mail-bezorging raadpleegt u [Offline levering starten](#starting-an-offline-delivery).

### Een online levering starten {#starting-an-online-delivery}

Zodra alle goedkeuringsverzoeken zijn verleend, verandert de leveringsstatus in **[!UICONTROL Pending confirmation]** en kan worden gestart door een operator. In voorkomend geval wordt de Adobe Campaign-exploitant (of groep marktdeelnemers) die als controleur is aangewezen om de levering te starten, ervan in kennis gesteld dat de levering klaar is om te worden gestart.

>[!NOTE]
>
>Als een specifieke exploitant of groep exploitanten voor het beginnen van een levering in de eigenschappen van de levering wordt aangewezen, kunt u de exploitant die voor de levering verantwoordelijk is ook toestaan om de verzending te bevestigen. Om dit te doen, activeer **NMS_ActivateOwnerConfirmation** optie door **1** als de waarde. De opties worden beheerd via de **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Options]** in de Adobe Campaign Explorer.
>  
>Als u deze optie wilt deactiveren, voert u **0** als de waarde. Het proces voor bevestiging verzenden werkt dan als standaard: alleen de exploitant of groep van exploitanten die voor de verzending zijn aangewezen in de leveringseigenschappen (of een beheerder) kan de verzending bevestigen en uitvoeren.

![](assets/s_ncs_user_edit_del_to_start_from_del.png)

De informatie verschijnt ook op het campagnedashboard. De **[!UICONTROL Confirm delivery]** Met deze koppeling kunt u de levering starten.

![](assets/s_ncs_user_edit_del_to_start.png)

Met een bevestigingsbericht kunt u deze handeling beveiligen.

### Offline levering starten {#starting-an-offline-delivery}

Zodra alle goedkeuringen zijn verleend, verandert de leveringsstatus in **[!UICONTROL Pending extraction]**. De extractiebestanden worden gemaakt met behulp van een speciale workflow die in de standaardconfiguratie automatisch wordt gestart wanneer een directe-maillevering in behandeling is voor extractie. Wanneer een proces bezig is, wordt het getoond in het dashboard en kan via zijn verbinding worden uitgegeven.

>[!NOTE]
>
>De technische workflows met betrekking tot het campagnepakket worden weergegeven in [Lijst van technische werkstromen](../../workflow/using/about-technical-workflows.md).

**Stap 1 - Goedkeuring van bestanden**

Nadat de extractieworkflow is voltooid, moet het extractiebestand worden goedgekeurd (mits de goedkeuring van het extractiebestand is geselecteerd in de leveringsinstellingen).

Raadpleeg voor meer informatie hierover [Een extractiebestand goedkeuren](../../campaign/using/marketing-campaign-approval.md#approving-an-extraction-file).

**Stap 2 - Goedkeuring van het bericht aan de dienstverlener**

* Zodra het extractiedossier wordt goedgekeurd, kunt u het bewijs van de e-mail van het routerbericht produceren. Dit e-mailbericht wordt samengesteld op basis van een leveringssjabloon. Het moet worden goedgekeurd.

   >[!NOTE]
   >
   >Deze stap is alleen beschikbaar als het verzenden en goedkeuren van proefdrukken is ingeschakeld in het venster Goedkeuring.

![](assets/s_ncs_user_file_valid_select_BAT.png)


* Klik op de knop **[!UICONTROL Send a proof]** om de proefdrukken te maken.

   Het proefdrukdoel moet vooraf worden gedefinieerd.

   U kunt zo veel proefdrukken maken als nodig is. Deze zijn toegankelijk via de **[!UICONTROL Direct mail...]** link van de leveringsgegevens.

   ![](assets/s_ncs_user_file_notif_submit_proof.png)

* De leveringsstatus verandert in **[!UICONTROL To submit]**. Klik op de knop **[!UICONTROL Submit proofs]** om het goedkeuringsproces te starten.

   ![](assets/s_ncs_user_file_notif_submit_proof_validation.png)

* De leveringsstatus verandert in **[!UICONTROL Proof to validate]** en met een knop kunt u goedkeuring accepteren of afwijzen.

   ![](assets/s_ncs_user_file_notif_supplier_link.png)

   U kunt deze goedkeuring accepteren of afwijzen of terugkeren naar de extractiestap.

   ![](assets/s_ncs_user_file_notif_supplier_link_confirm.png)

* Het extractiedossier wordt verzonden naar de router en de levering wordt gebeëindigd.

### Berekening van de kosten en voorraden {#calculation-of-costs-and-stocks}

Met de uitname van het bestand worden twee bewerkingen gestart: begrotingsberekening en voorraadberekening. De begrotingsonderdelen worden bijgewerkt.

* De **[!UICONTROL Budget]** kunt u de budgetten voor de campagne beheren. Het totaal van de kostenposten wordt weergegeven in het **[!UICONTROL Calculates cost]** veld van het hoofdtabblad van de campagne en het programma waartoe deze behoort. De bedragen zijn ook terug te vinden in de campagnebegroting.

   De echte kosten zullen uiteindelijk van informatie worden berekend die door de router wordt verstrekt. Alleen daadwerkelijk verzonden berichten worden gefactureerd.

* De voorraden worden gedefinieerd in de **[!UICONTROL Administration > Campaign management > Stocks]** knooppunt van de boomstructuur en kostenstructuren in de **[!UICONTROL Administration > Campaign management > Service providers]** knooppunt.

   De voorraadlijnen zijn zichtbaar in de voorraadsectie. Als u de oorspronkelijke voorraad wilt definiëren, opent u een voorraadlijn. De voorraad wordt telkens verlaagd wanneer een levering plaatsvindt. U kunt een waarschuwingsniveau en meldingen definiëren.

>[!NOTE]
>
>Voor meer informatie over kostenberekeningen en voorraadbeheer raadpleegt u [Leveranciers, voorraden en begrotingen](../../campaign/using/providers--stocks-and-budgets.md).

## Gekoppelde documenten beheren {#managing-associated-documents}

U kunt verschillende documenten aan een campagne koppelen: rapport, foto, webpagina, diagram, enz. Deze documenten kunnen elke gewenste indeling hebben (Microsoft Word, PowerPoint, PNG, JPG, Acrobat PDF, enz.). Leer hoe u documenten kunt koppelen aan een campagne [in deze sectie](../../campaign/using/marketing-campaign-assets.md).

>[!IMPORTANT]
>
>Deze modus is gereserveerd voor kleine documenten.

In een campagne kunt u ook andere objecten bekijken, zoals promotiecoupons, speciale aanbiedingen voor een specifieke winkel of filiaal, enzovoort. Wanneer deze elementen in een overzicht worden opgenomen, kunnen zij met een directe postlevering worden geassocieerd. [Meer informatie](#associating-and-structuring-resources-linked-via-a-delivery-outline).

>[!NOTE]
>
>Als u MRM gebruikt, kunt u een bibliotheek van marketing middelen ook beheren die voor verscheidene deelnemers voor samenwerkingswerk beschikbaar zijn. Zie [Marketing-resources beheren](../../mrm/using/managing-marketing-resources.md).

### Documenten toevoegen {#adding-documents}

Documenten kunnen worden gekoppeld op campagneniveau (contextuele documenten) of op programmaniveau (algemene documenten).

De **[!UICONTROL Documents]** bevat:

* De lijst met alle documenten die vereist zijn voor de inhoud (sjabloon, afbeeldingen, enz.) die door Adobe Campaign-operatoren met de juiste rechten lokaal kunnen worden gedownload,
* Documenten die informatie voor de router bevatten, als om het even welk.

De documenten houden verband met het programma of de campagne via de **[!UICONTROL Edit > Documents]** tab.

![](assets/s_ncs_user_op_add_document.png)

U kunt ook een document aan een campagne toevoegen via de koppeling die in het dashboard wordt aangeboden.

![](assets/add_a_document_in_op.png)

Klik op de knop **[!UICONTROL Details]** pictogram om de inhoud van een bestand weer te geven en informatie toe te voegen:

![](assets/s_ncs_user_op_add_document_details.png)

In het dashboard worden de documenten die bij de campagne horen gegroepeerd in de **[!UICONTROL Document(s)]** , zoals in het volgende voorbeeld:

![](assets/s_ncs_user_op_edit_document.png)

U kunt ze ook vanuit deze weergave bewerken en wijzigen.

### Bronnen koppelen en structureren via een leveringsoverzicht {#associating-and-structuring-resources-linked-via-a-delivery-outline}

>[!NOTE]
>
>De leveringsschema&#39;s worden uitsluitend gebruikt in het kader van direct-mailcampagnes.

Een leveringsoverzicht geeft een gestructureerde reeks elementen aan (documenten, filialen/winkels, promotionele coupons, enz.) opgericht in het bedrijf en voor een bepaalde campagne.

Deze elementen worden gegroepeerd in leveringsschema&#39;s, en een bepaald leveringsoverzicht zal met een levering worden geassocieerd; er wordt naar verwezen in het extractiebestand dat naar de **serviceprovider** om bij de levering te worden gevoegd. U kunt bijvoorbeeld een leveringsoverzicht maken dat verwijst naar een vertakking en de marketingbrochures die erin worden gebruikt.

Voor een campagne, laten de leveringsoverzichten u externe elementen structureren die met de levering volgens bepaalde criteria moeten worden geassocieerd: verwante branche, aangeboden promotieaanbieding, uitnodiging voor een lokale evenement, enz.

#### Een omtrek maken {#creating-an-outline}

Als u een omtrek wilt maken, klikt u op de knop **[!UICONTROL Delivery outlines]** subtab in het dialoogvenster **[!UICONTROL Edit > Documents]** tabblad van de desbetreffende campagne.

>[!NOTE]
>
>Als dit tabblad niet aanwezig is, is deze functie niet beschikbaar voor deze campagne. Verwijs naar de configuratie van het campagnemalplaatje.
>   
>Raadpleeg voor meer informatie hierover [Campagnersjablonen](../../campaign/using/marketing-campaign-templates.md#campaign-templates).

![](assets/s_ncs_user_op_composition_link.png)

Klik op Volgende **[!UICONTROL Add a delivery outline]** en maak de hiërarchie van contouren voor de campagne:

1. Klik met de rechtermuisknop op de basis van de structuur en selecteer **[!UICONTROL New > Delivery outlines]**.
1. Klik met de rechtermuisknop op de omtrek die u zojuist hebt gemaakt en selecteer **[!UICONTROL New > Item]** of **[!UICONTROL New > Personalization fields]**.

![](assets/s_ncs_user_op_add_composition.png)

Een overzicht kan punten en verpersoonlijkingsgebieden, middelen en aanbiedingen bevatten:

* Items kunnen bijvoorbeeld fysieke documenten zijn waarnaar hier wordt verwezen en die hier worden beschreven en die aan de levering worden gekoppeld.
* Met velden voor personalisatie kunt u personalisatie-elementen maken die te maken hebben met leveringen in plaats van met ontvangers. Het is dus mogelijk waarden te creëren die in leveringen voor een specifiek doel moeten worden gebruikt (welkomstaanbod, korting, enz.) Ze zijn gemaakt in Adobe Campaign en geïmporteerd in de omtrek via de **[!UICONTROL Import personalization fields...]** koppeling.

   ![](assets/s_ncs_user_op_add_composition_field.png)

   Ze kunnen ook rechtstreeks in de omtrek worden gemaakt door op de knop **[!UICONTROL Add]** rechts van de lijstzone.

   ![](assets/s_ncs_user_op_add_composition_field_button.png)

* De middelen zijn marketing middelen die in het marketing middeldashboard worden geproduceerd dat via **[!UICONTROL Resources]** koppeling van de **[!UICONTROL Campaigns]** tab.

   ![](assets/s_ncs_user_mkg_resource_ovv.png)

   >[!NOTE]
   >
   >Voor meer informatie over marketingbronnen raadpleegt u [Marketing-bronnen beheren](../../mrm/using/managing-marketing-resources.md).

#### Een omtrek selecteren {#selecting-an-outline}

Voor elke levering, kunt u het overzicht selecteren om van de sectie te associëren die voor het extractieoverzicht wordt gereserveerd, zoals in het volgende voorbeeld:

![](assets/s_ncs_user_op_select_composition.png)

De geselecteerde omtrek wordt vervolgens weergegeven in de onderste sectie van het venster. U kunt de afbeelding bewerken met het pictogram rechts van het veld of wijzigen met de vervolgkeuzelijst:

![](assets/s_ncs_user_op_select_composition_b.png)

De **[!UICONTROL Summary]** tabblad van de levering geeft ook deze informatie weer:

![](assets/s_ncs_user_op_select_composition_c.png)

#### Extractieresultaat {#extraction-result}

In het dossier dat wordt uitgepakt en aan de dienstverlener wordt toegezonden, de naam van de omtrek en, in voorkomend geval, de kenmerken ervan (kosten, beschrijving enz.) worden toegevoegd aan de inhoud volgens de informatie in het uitvoermalplaatje verbonden aan de dienstverlener.

In het volgende voorbeeld worden het label, de geschatte kosten en de beschrijving van de omtrek die aan de levering is gekoppeld, toegevoegd aan het extractiebestand.

![](assets/s_ncs_user_op_composition_in_export_template.png)

Het exportmodel moet worden gekoppeld aan de dienstverlener die voor de betrokken levering is geselecteerd. Zie [Dienstverleners en hun kostenstructuren creëren](../../campaign/using/providers--stocks-and-budgets.md#creating-service-providers-and-their-cost-structures).

>[!NOTE]
>
>Raadpleeg voor meer informatie over exporteren de [Aan de slag](../../platform/using/get-started-data-import-export.md) sectie.

#### Video over zelfstudie {#create-email-video}

In deze video wordt uitgelegd hoe u een campagne en een e-mail maakt in Adobe Campaign.

>[!VIDEO](https://video.tv.adobe.com/v/25604?quality=12)

Er zijn aanvullende instructievideo&#39;s beschikbaar voor campagnes [hier](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=nl).
