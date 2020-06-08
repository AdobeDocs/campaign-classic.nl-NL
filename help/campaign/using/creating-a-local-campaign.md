---
title: Een lokale campagne maken
seo-title: Een lokale campagne maken
description: Een lokale campagne maken
seo-description: null
page-status-flag: never-activated
uuid: 86e78d9e-26cb-4aea-b8ce-5e52ae352b48
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: distributed-marketing
discoiquuid: bd057441-8524-49e6-b5d5-fbd0ec5bca85
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: e97183256ef6d3f2068dd0fbc8eb3c3f32e0bae0
workflow-type: tm+mt
source-wordcount: '1573'
ht-degree: 0%

---


# Een lokale campagne maken{#creating-a-local-campaign}

Een lokale campagne is een instantie die is gemaakt op basis van een sjabloon waarnaar in de lijst van **[!UICONTROL campaign packages]** met een **specifiek uitvoeringsschema** wordt verwezen. Zijn doel is om aan een lokale communicatie behoefte te voldoen gebruikend een campagnemalplaatje dat opstelling en gevormd door de centrale entiteit was. De belangrijkste fasen voor de uitvoering van een lokale actie zijn:

**Voor de centrale entiteit**

1. Een lokale campagnemalplaatje maken.
1. Campagnepakket maken op basis van een sjabloon.
1. Een campagnepakket publiceren.
1. Bevestigingsopdrachten.

**Voor de lokale entiteit**

1. De campagne bestellen.
1. Bezig met uitvoeren van campagnes.

## Een lokale campagnemalplaatje maken {#creating-a-local-campaign-template}

Als u een campagnepakket wilt maken, moet u eerst de **campagnemalplaatje** maken via het **[!UICONTROL Resources > Templates]** knooppunt.

Als u een nieuwe lokale sjabloon wilt maken, dupliceert u de **[!UICONTROL Local campaign (opLocal)]** standaardsjabloon.

![](assets/mkg_dist_local_op_creation.png)

Geef uw campagnemalplaatje een naam en vul de beschikbare velden in.

![](assets/mkg_dist_local_op_creation1.png)

Klik in het campagnevenster op het **[!UICONTROL Edit]** tabblad en klik vervolgens op de **[!UICONTROL Advanced campaign settings...]** koppeling.

![](assets/mkt_distr_4.png)

### Webinterface {#web-interface}

Op het **Verdeelde marketing** lusje, kunt u het type van de interface van het Web kiezen en de standaardwaarden en parameters specificeren die moeten worden ingegaan wanneer een lokale entiteit een orde plaatst.

De interface van het Web beantwoordt aan een vorm die door de lokale entiteit moet worden ingevuld wanneer het opdracht geven tot van de campagne.

Selecteer het type van de interface van het Web dat op de campagnes moet worden toegepast die van het malplaatje worden gecreeerd:

![](assets/mkt_distr_1.png)

Er zijn vier types van beschikbare interfaces van het Web:

* **[!UICONTROL By brief]** : de lokale entiteit moet een beschrijving verstrekken waarmee zij de campagneconfiguraties beschrijft. Zodra de orde is goedgekeurd, vormt de centrale entiteit en voert de campagne als geheel uit.

   ![](assets/mkt_distr_6.png)

* **[!UICONTROL By form]** : de lokale entiteit heeft toegang tot een vorm van het Web waar, afhankelijk van het gebruikte malplaatje, zij de inhoud, het doel, zijn maximumgrootte, evenals verwezenlijking en extractiedata kunnen uitgeven gebruikend verpersoonlijkingsgebieden. De lokale entiteit kan het doel evalueren en inhoud van voorproef van dit formulier van Web.

   ![](assets/mkt_distr_8.png)

   Het aangeboden formulier wordt opgegeven in een webtoepassing die moet worden geselecteerd in een vervolgkeuzelijst in het **[!UICONTROL Web Interface]** veld in de **[!UICONTROL Advanced campaign settings...]** koppeling van de sjabloon. Zie Een lokale campagne [maken (op formulier)](../../campaign/using/examples.md#creating-a-local-campaign--by-form-).

   >[!NOTE]
   >
   >De toepassing van het Web die in dit voorbeeld wordt gebruikt is een voorbeeld. U moet een specifieke webapp maken om een formulier te kunnen gebruiken. Zie [API](../../configuration/using/about-web-services.md).

   ![](assets/mkt_distr_7.png)

* **[!UICONTROL By external form]** : de lokale entiteit heeft toegang tot campagneparameters in zijn Extranet (niet de Campagne van Adobe). Deze parameters zijn identiek aan die van een **lokale campagne (door vorm)**.
* **[!UICONTROL Pre-set]** : de lokale entiteit geeft opdracht tot campagne gebruikend het standaardformulier, zonder het te lokaliseren.

   ![](assets/mkt_distr_5.png)

### Standaardwaarden {#default-values}

Selecteer de code **[!UICONTROL Default values]** die lokale entiteiten moeten invullen. Bijvoorbeeld:

* de datum van contact en extractie;
* doelkenmerken (leeftijdssegment enz.).

![](assets/mkg_dist_local_op_creation2.png)

Vul de velden **[!UICONTROL Parent marketing program]** en **[!UICONTROL Charge]** velden in.

![](assets/mkg_dist_local_op_creation3.png)

### Goedkeuringen {#approvals}

Via de **[!UICONTROL Advanced parameters for campaign entry]** koppeling kunt u het maximumaantal revisoren opgeven.

![](assets/s_advuser_mkg_dist_add_valid_op1.png)

Revisoren worden door de lokale entiteit ingevoerd bij het bestellen van de campagne.

![](assets/mkt_distr_5.png)

Als u geen controleurs voor een campagne wilt noemen, ga 0 in.

### Documenten {#documents}

U kunt operatoren van lokale entiteiten toestaan om documenten (tekstbestanden, spreadsheets, afbeeldingen, campagnebeschrijvingen enzovoort) te koppelen. aan de lokale campagne wanneer het creëren van de orde. Met de **[!UICONTROL Advanced parameters for campaign entry...]** koppeling kunt u het aantal documenten beperken. U doet dit door het maximum toegestane aantal in te voeren in het **[!UICONTROL Number of documents]** veld.

![](assets/s_advuser_mkg_dist_local_docs.png)

Als u een campagnepakket bestelt, wordt in het formulier voorgesteld om zoveel documenten te koppelen als in het desbetreffende veld in de sjabloon worden aangegeven.

![](assets/s_advuser_mkg_dist_add_docs.png)

Als u geen veld voor het uploaden van documenten wilt weergeven, voert u dit veld **[!UICONTROL 0]** **[!UICONTROL Number of documents]** in.

>[!NOTE]
>
>Het **[!UICONTROL Advanced parameters for campaign entry]** kan worden gedeactiveerd door te controleren **[!UICONTROL Do not display the page used to enter the campaign parameters]**.

![](assets/s_advuser_mkg_dist_disable_op_parameters.png)

### Workflow {#workflow}

Maak op het **[!UICONTROL Targeting and workflows]** tabblad de campagneworkflow die de **[!UICONTROL Default values]** opgegeven gegevens in het bestand verzamelt **[!UICONTROL Advanced campaign settings...]** en de leveringen maakt.

![](assets/mkg_dist_local_op_creation4b.png)

Dubbelklik op de **[!UICONTROL Query]** activiteit om deze te configureren volgens de opgegeven **[!UICONTROL Default values]** procedure.

![](assets/mkt_dist_local_campaign_localize_query.png)

### Aflevering {#delivery}

Klik op het **[!UICONTROL Audit]** tabblad op het **[!UICONTROL Detail...]** pictogram om de **[!UICONTROL Scheduling]** voor de geselecteerde levering te bekijken.

![](assets/mkg_dist_local_op_creation4c.png)

Met het **[!UICONTROL Scheduling]** pictogram kunt u de contactpersoon en uitvoeringsdatum van de levering configureren.

![](assets/mkg_dist_local_op_creation4d.png)

Indien nodig, vorm de maximumgrootte van de levering:

![](assets/mkg_dist_local_op_creation4e.png)

Zoek de HTML van uw levering. Gebruik in **[!UICONTROL Delivery > Current order > Additional fields]****[!UICONTROL Age segment]** het veld bijvoorbeeld om de levering te zoeken op basis van de leeftijd van het doel.

![](assets/mkt_dist_local_campaign_localize_html.png)

Sla uw campagnemalplaatje op. U kunt het nu gebruiken vanuit de **Campagnepakketweergave** in het **Campagneuniversum** door op de **[!UICONTROL Create]** knop te klikken.

![](assets/mkt_distr_9.png)

>[!NOTE]
>
>De malplaatjes van de campagne en hun algemene configuratie zijn gedetailleerd in de malplaatjes [van de](../../campaign/using/marketing-campaign-templates.md#campaign-templates)Campagne.

## Het campagnepakket maken {#creating-the-campaign-package}

Het campagnemalplaatje kan alleen beschikbaar worden voor lokale entiteiten als het aan de lijst wordt toegevoegd. Daartoe moet het centrale agentschap een nieuw pakket opstellen.

Voer de volgende stappen uit:

1. Klik in de **[!UICONTROL Navigation]** sectie op de pagina **Campagnes** op de **[!UICONTROL Campaign packages]** koppeling.
1. Klik op de **[!UICONTROL Create]** knop.

   ![](assets/mkg_dist_add_an_entry.png)

1. In de sectie boven het venster kunt u de [eerder](#creating-a-local-campaign-template) opgegeven sjabloon voor het campagnepakket selecteren.

   Standaard wordt de **[!UICONTROL New local campaign package (localEmpty)]** sjabloon gebruikt voor lokale campagnes.

1. Geef het label, de map en het uitvoeringsschema voor het campagnemakket op.

### Datums {#dates}

De begin- en einddatum bepalen de zichtbaarheidsperiode van de campagne in de lijst met campagnepakketten.

De beschikbaarheidsdatum is de datum waarop de campagne voor lokale entiteiten (aan orde) beschikbaar zal worden.

>[!CAUTION]
>
>Als een lokale entiteit de campagne niet vóór de deadline reserveert, zal zij deze niet kunnen gebruiken.

Deze informatie is te vinden in het aan lokale agentschappen verzonden kennisgevingsbericht, zoals hieronder wordt getoond:

![](assets/s_advuser_mkg_dist_local_notif.png)

### Publiek {#audience}

Voor een lokale campagne kan de centrale entiteit de betrokken lokale entiteiten specificeren door het **[!UICONTROL Limit the package to a set of local entities]** te controleren.

![](assets/s_advuser_mkg_dist_create_mutual_entry3.png)

### Aanvullende instellingen {#additional-settings}

Nadat het pakket is opgeslagen, kan de centrale entiteit het op het **[!UICONTROL Edit]** tabblad bewerken.

![](assets/mkg_dist_edit_kit.png)

Vanaf het **[!UICONTROL General]** tabblad kan de centrale entiteit:

* de beoordelaar(s) van het campagnepakket configureren via de **[!UICONTROL Approval parameters...]** koppeling;
* het uitvoeringsschema te herzien;
* lokale entiteiten toevoegen of verwijderen.

>[!NOTE]
>
>Standaard kan elke entiteit slechts één keer een **lokale campagne** bestellen.
>   
>Schakel de **[!UICONTROL Enable multiple creation]** optie in als u meerdere lokale campagnes wilt maken op basis van het campagnepakket.

![](assets/mkg_dist_local_op_multi_crea.png)

### Meldingen {#notifications}

Wanneer een campagne beschikbaar wordt of wanneer de registratietermijn wordt bereikt, wordt een bericht verzonden naar de exploitanten van de lokale berichtgroep. Raadpleeg [Organisatorische entiteiten](../../campaign/using/about-distributed-marketing.md#organizational-entities)voor meer informatie hierover.

## Een campagne bestellen {#ordering-a-campaign}

Campagnepakketten worden toegankelijk voor lokale entiteiten zodra ze zijn goedgekeurd en de uitvoeringsperiode ervan is begonnen. Lokale entiteiten ontvangen een e-mail met de mededeling dat er een nieuw campagnepakket beschikbaar is (zodra de beschikbaarheidsdatum is bereikt).

>[!NOTE]
>
>Als sommige lokale entiteiten bij het creëren van het campagnepakket werden gespecificeerd, zullen zij de enige zijn om een bericht te ontvangen. Als er geen lokale entiteit is opgegeven, ontvangen alle lokale entiteiten een kennisgeving.

![](assets/mkg_dist_local_op_notification.png)

Om een campagne van de centrale entiteit te gebruiken, moet de lokale entiteit het bevel geven.

Een campagne bestellen:

1. Klik **[!UICONTROL Order campaign]** in het berichtbericht, of de overeenkomstige knoop in de Campagne van Adobe.

   Voer uw id en wachtwoord in om de campagne te bestellen. De interface bestaat uit een set pagina&#39;s die zijn gedefinieerd in een webtoepassing.

   >[!NOTE]
   >
   >De toepassingen van het Web zijn gedetailleerd in de [functionaliteitengids](../../web/using/about-web-applications.md) van het Web.

1. Voer de benodigde gegevens in op de eerste pagina (orderlabel en opmerking) en klik op **[!UICONTROL Next]**.

   ![](assets/mkg_dist_subscribe_step1.png)

1. Voltooi de beschikbare parameters en keur de volgorde goed.

1. Er wordt een kennisgeving verzonden aan de beheerder van de organisatorische entiteit waartoe de lokale entiteit behoort, om deze bestelling goed te keuren.

   ![](assets/mkg_dist_subscribe_step3.png)

1. De informatie wordt geretourneerd aan de lokale en centrale entiteiten. Hoewel lokale entiteiten alleen hun eigen orders kunnen bekijken, kan de centrale entiteit alle orders van elke lokale entiteit bekijken, zoals hieronder wordt getoond:

   ![](assets/mkg_dist_subscribe_central_view.png)

   Operatoren kunnen ordergegevens weergeven:

   ![](assets/mkg_dist_local_op_catalog_detail_1.png)

   Het **[!UICONTROL Edit]** tabblad bevat informatie die de lokale entiteit heeft ingevoerd bij het bestellen van de campagne.

   ![](assets/mkg_dist_local_op_catalog_detail_1b.png)

1. De order moet door de centrale entiteit worden goedgekeurd.

   ![](assets/mkg_dist_local_op_catalog_detail_3.png)

   Raadpleeg de sectie [Goedkeuringsproces](#approval-process) voor meer informatie.

1. De lokale exploitant wordt vervolgens op de hoogte gesteld dat de campagne beschikbaar is: de beschikbaarheid van campagnes is te vinden in de lijst van campagnepakketten binnen het **Campagne** universum. De campagne kan dan worden gebruikt. Raadpleeg [Toegankelijkheidscampagnes](../../campaign/using/accessing-campaigns.md)voor meer informatie.

   Met deze **[!UICONTROL Start targeting with order approval]** optie kan de lokale entiteit de campagne uitvoeren zodra de bestelling is goedgekeurd.

   ![](assets/mkg_dist_local_op_catalog_use.png)

## Een bestelling goedkeuren {#approving-an-order}

Om een campagneorder te bevestigen, moet de centrale entiteit het goedkeuren.

Het **[!UICONTROL Campaign orders]** overzicht, dat via het **Campagne** heelal wordt betreden laat u de status van campagneorden bekijken en hen goedkeuren.

>[!NOTE]
>
>Lokale entiteiten kunnen wijzigingen in de bestelling aanbrengen totdat deze is goedgekeurd.

### Goedkeuringsproces {#approval-process}

#### E-mailmelding {#email-notification}

Wanneer een campagne wordt besteld door een lokale entiteit, worden de revisoren hiervan via e-mail op de hoogte gebracht, zoals hieronder wordt getoond:

![](assets/mkg_dist_valid_notif_email.png)

>[!NOTE]
>
>Het selecteren van revisoren wordt weergegeven in de sectie [Revisoren](#reviewers) . Ze kunnen de bestelling accepteren of afwijzen.

![](assets/mkg_dist_command_valid_web.png)

#### Goedkeuren via de Adobe Campaign-console {#approving-via-the-adobe-campaign-console}

De bestelling kan ook worden goedgekeurd via de console, in het overzicht van de campagnevolgorde. Als u een bestelling wilt goedkeuren, selecteert u deze en klikt u op **[!UICONTROL Approve the order]**.

![](assets/mkg_dist_local_order_valid.png)

>[!NOTE]
>
>De campagne kan nog worden uitgegeven en worden aangepast tot de datum van de campagnebeschikbaarheid. Lokale entiteiten kunnen de campagne ook afwijzen door op de **[!UICONTROL Cancel]** knop te klikken.

#### Een campagne maken {#creating-a-campaign}

Zodra een campagneorde wordt goedgekeurd, kan het door de lokale entiteit worden gevormd en worden uitgevoerd.

![](assets/mkg_dist_mutual_op_created.png)

Raadpleeg [Toegankelijkheidscampagnes](../../campaign/using/accessing-campaigns.md)voor meer informatie.

### Afwijzing van een goedkeuring {#rejecting-an-approval}

De met de goedkeuring belaste exploitant kan een bestelling of een campagnepakket afwijzen.

![](assets/mkg_dist_do_not_valid.png)

Indien de controleur een bestelling afwijst, wordt de desbetreffende kennisgeving automatisch naar de betrokken lokale entiteiten gezonden: het bevat de opmerking die is ingevoerd door de exploitant die de goedkeuring heeft geweigerd.

De informatie wordt getoond op de lijst van campagnepakketpagina of op de pagina van de campagneorde. Als ze toegang hebben tot de Adobe Campaign-console, worden lokale entiteiten op de hoogte gesteld van deze afwijzing.

![](assets/mkg_dist_do_not_valid_view.png)

Ze kunnen de verwante opmerking weergeven op het **[!UICONTROL Edit]** tabblad van het campagnepakket.

![](assets/mkg_dist_do_not_valid_tab.png)

### Revisoren {#reviewers}

Elke keer dat goedkeuring wordt vereist, worden revisoren via e-mail op de hoogte gesteld.

Voor elke lokale entiteit worden revisoren geselecteerd voor goedkeuring van de campagneorder en goedkeuring van de campagne. Raadpleeg [Organisatorische entiteiten](../../campaign/using/about-distributed-marketing.md#organizational-entities)voor meer informatie over het selecteren van lokale revisoren.

>[!NOTE]
>
>Om deze selectie mogelijk te maken, moet de goedkeuring van de bestelling nog niet effectief zijn.

### Een bestelling annuleren {#canceling-an-order}

Het centrale bureau kan een orde annuleren gebruikend de **[!UICONTROL Delete]** knoop, die op het ordedashboard wordt gevestigd.

![](assets/mkg_dist_local_op_cancel.png)

Hierdoor wordt de campagne in de **[!UICONTROL Campaign orders]** weergave geannuleerd.
