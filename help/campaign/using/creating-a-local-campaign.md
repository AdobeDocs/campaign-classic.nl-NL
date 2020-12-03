---
solution: Campaign Classic
product: campaign
title: Een lokale campagne maken
description: Een lokale campagne maken
audience: campaign
content-type: reference
topic-tags: distributed-marketing
translation-type: tm+mt
source-git-commit: c625b4109e2cb47446331cd009ff9827c8267c93
workflow-type: tm+mt
source-wordcount: '1567'
ht-degree: 1%

---


# Een lokale campagne maken{#creating-a-local-campaign}

Een lokale campagne is een instantie die is gemaakt van een sjabloon waarnaar wordt verwezen in de lijst van **[!UICONTROL campaign packages]** met een **specifiek uitvoeringsschema**. Zijn doel is om aan een lokale communicatie behoefte te voldoen gebruikend een campagnemalplaatje dat opstelling en gevormd door de centrale entiteit was. De belangrijkste fasen voor de uitvoering van een lokale actie zijn:

**Voor de centrale entiteit**

1. Een lokale campagnemalplaatje maken.
1. Campagnepakket maken op basis van een sjabloon.
1. Een campagnepakket publiceren.
1. Bevestigingsopdrachten.

**Voor de lokale entiteit**

1. De campagne bestellen.
1. Bezig met uitvoeren van campagnes.

## Een lokale campagnemplate maken {#creating-a-local-campaign-template}

Als u een campagnepakket wilt maken, moet u eerst de **campagnemalplaatje** via het knooppunt **[!UICONTROL Resources > Templates]** maken.

Als u een nieuwe lokale sjabloon wilt maken, dupliceert u de standaardsjabloon **[!UICONTROL Local campaign (opLocal)]**.

![](assets/mkg_dist_local_op_creation.png)

Geef uw campagnemalplaatje een naam en vul de beschikbare velden in.

![](assets/mkg_dist_local_op_creation1.png)

Klik in het campagnevenster op het tabblad **[!UICONTROL Edit]** en klik vervolgens op de koppeling **[!UICONTROL Advanced campaign settings...]**.

![](assets/mkt_distr_4.png)

### Webinterface {#web-interface}

Op **Verdeelde marketing** tabel, kunt u het type van de interface van het Web kiezen en de standaardwaarden en parameters specificeren die moeten worden ingegaan wanneer een lokale entiteit een orde plaatst.

De webinterface komt overeen met een formulier dat door de lokale entiteit moet worden ingevuld bij het bestellen van de campagne.

Selecteer het type webinterface dat moet worden toegepast op de campagnes die op basis van de sjabloon worden gemaakt:

![](assets/mkt_distr_1.png)

Er zijn vier typen webinterfaces beschikbaar:

* **[!UICONTROL By brief]** : de lokale entiteit moet een beschrijving verstrekken waarmee zij de campagneconfiguraties beschrijft. Zodra de orde is goedgekeurd, vormt de centrale entiteit en voert de campagne als geheel uit.

   ![](assets/mkt_distr_6.png)

* **[!UICONTROL By form]** : lokale entiteit heeft toegang tot een webformulier waar ze, afhankelijk van de gebruikte sjabloon, de inhoud, het doel, de maximale grootte en de datum waarop ze zijn gemaakt en opgehaald, kunnen bewerken met verpersoonlijkingsvelden. Lokale entiteit kan het doel evalueren en de inhoud van dit webformulier voorvertonen.

   ![](assets/mkt_distr_8.png)

   Het aangeboden formulier wordt opgegeven in een webtoepassing die moet worden geselecteerd in een vervolgkeuzelijst in het veld **[!UICONTROL web Interface]** in de koppeling **[!UICONTROL Advanced campaign settings...]** van de sjabloon. Zie [Een lokale campagne maken (op formulier)](../../campaign/using/examples.md#creating-a-local-campaign--by-form-).

   >[!NOTE]
   >
   >De webtoepassing die in dit voorbeeld wordt gebruikt, is een voorbeeld. U moet een specifieke web-app maken om een formulier te kunnen gebruiken. Zie [API](../../configuration/using/about-web-services.md).

   ![](assets/mkt_distr_7.png)

* **[!UICONTROL By external form]** : de lokale entiteit heeft toegang tot campagneparameters in zijn Extranet (niet Adobe Campaign). Deze parameters zijn identiek aan die van een **lokale campagne (door vorm)**.
* **[!UICONTROL Pre-set]** : de lokale entiteit geeft opdracht tot campagne gebruikend het standaardformulier, zonder het te lokaliseren.

   ![](assets/mkt_distr_5.png)

### Standaardwaarden {#default-values}

Selecteer de **[!UICONTROL Default values]** die door lokale entiteiten moet worden ingevuld. Bijvoorbeeld:

* de datum van contact en extractie;
* doelkenmerken (leeftijdssegment enz.).

![](assets/mkg_dist_local_op_creation2.png)

Vul de velden **[!UICONTROL Parent marketing program]** en **[!UICONTROL Charge]** in.

![](assets/mkg_dist_local_op_creation3.png)

### Goedkeuring {#approvals}

Via de koppeling **[!UICONTROL Advanced parameters for campaign entry]** kunt u het maximumaantal revisoren opgeven.

![](assets/s_advuser_mkg_dist_add_valid_op1.png)

Revisoren worden door de lokale entiteit ingevoerd bij het bestellen van de campagne.

![](assets/mkt_distr_5.png)

Als u geen controleurs voor een campagne wilt noemen, ga 0 in.

### Documenten {#documents}

U kunt operatoren van lokale entiteiten toestaan om documenten (tekstbestanden, spreadsheets, afbeeldingen, campagnebeschrijvingen enzovoort) te koppelen. aan de lokale campagne wanneer het creëren van de orde. Met de koppeling **[!UICONTROL Advanced parameters for campaign entry...]** kunt u het aantal documenten beperken. Om dit te doen, ga eenvoudig het maximumaantal in toegestaan op het **[!UICONTROL Number of documents]** gebied.

![](assets/s_advuser_mkg_dist_local_docs.png)

Als u een campagnepakket bestelt, wordt in het formulier voorgesteld om zoveel documenten te koppelen als in het desbetreffende veld in de sjabloon worden aangegeven.

![](assets/s_advuser_mkg_dist_add_docs.png)

Als u geen veld voor het uploaden van documenten wilt weergeven, voert u **[!UICONTROL 0]** in het veld **[!UICONTROL Number of documents]** in.

>[!NOTE]
>
>De **[!UICONTROL Advanced parameters for campaign entry]** kan worden gedeactiveerd door **[!UICONTROL Do not display the page used to enter the campaign parameters]** te controleren.

![](assets/s_advuser_mkg_dist_disable_op_parameters.png)

### Workflow {#workflow}

Maak op het tabblad **[!UICONTROL Targeting and workflows]** de campagneworkflow die de **[!UICONTROL Default values]** verzamelt die is opgegeven in **[!UICONTROL Advanced campaign settings...]** en de leveringen maakt.

![](assets/mkg_dist_local_op_creation4b.png)

Dubbelklik op de **[!UICONTROL Query]**-activiteit om deze te configureren volgens de opgegeven **[!UICONTROL Default values]**.

![](assets/mkt_dist_local_campaign_localize_query.png)

### Levering {#delivery}

Klik op het tabblad **[!UICONTROL Audit]** op het pictogram **[!UICONTROL Detail...]** om **[!UICONTROL Scheduling]** voor de geselecteerde levering weer te geven.

![](assets/mkg_dist_local_op_creation4c.png)

Met het pictogram **[!UICONTROL Scheduling]** kunt u de contactpersoon en uitvoeringsdatum van de levering configureren.

![](assets/mkg_dist_local_op_creation4d.png)

Indien nodig, vorm de maximumgrootte van de levering:

![](assets/mkg_dist_local_op_creation4e.png)

Zoek de HTML van uw levering. Gebruik in **[!UICONTROL Delivery > Current order > Additional fields]** bijvoorbeeld het veld **[!UICONTROL Age segment]** om de levering te zoeken op basis van de leeftijd van het doel.

![](assets/mkt_dist_local_campaign_localize_html.png)

Sla uw campagnemalplaatje op. U kunt het van **Campagnepakketten** nu gebruiken mening in **Campagnes** universum, door **[!UICONTROL Create]** knoop te klikken.

![](assets/mkt_distr_9.png)

>[!NOTE]
>
>De malplaatjes van de campagne en hun algemene configuratie worden gedetailleerd in [de malplaatjes van de Campagne](../../campaign/using/marketing-campaign-templates.md#campaign-templates).

## Het campagnepakket {#creating-the-campaign-package} maken

Het campagnemalplaatje kan alleen beschikbaar worden voor lokale entiteiten als het aan de lijst wordt toegevoegd. Daartoe moet het centrale agentschap een nieuw pakket opstellen.

Voer de volgende stappen uit:

1. Klik in de sectie **[!UICONTROL Navigation]** op de pagina **Campagnes** op de koppeling **[!UICONTROL Campaign packages]**.
1. Klik op de knop **[!UICONTROL Create]**.

   ![](assets/mkg_dist_add_an_entry.png)

1. In de sectie boven het venster kunt u de eerder [opgegeven sjabloon voor het campagnepakket selecteren.](#creating-a-local-campaign-template)

   Standaard wordt de sjabloon **[!UICONTROL New local campaign package (localEmpty)]** gebruikt voor lokale campagnes.

1. Geef het label, de map en het uitvoeringsschema voor het campagnemakket op.

### Datums {#dates}

De begin- en einddatum bepalen de zichtbaarheidsperiode van de campagne in de lijst met campagnepakketten.

De beschikbaarheidsdatum is de datum waarop de campagne voor lokale entiteiten (aan orde) beschikbaar zal worden.

>[!CAUTION]
>
>Als een lokale entiteit de campagne niet vóór de deadline reserveert, zal zij deze niet kunnen gebruiken.

Deze informatie is te vinden in het aan lokale agentschappen verzonden kennisgevingsbericht, zoals hieronder wordt getoond:

![](assets/s_advuser_mkg_dist_local_notif.png)

### Doelgroep {#audience}

Voor een lokale campagne kan de centrale entiteit de betrokken lokale entiteiten specificeren door **[!UICONTROL Limit the package to a set of local entities]** te controleren.

![](assets/s_advuser_mkg_dist_create_mutual_entry3.png)

### Aanvullende instellingen {#additional-settings}

Nadat het pakket is opgeslagen, kan de centrale entiteit het bewerken via het tabblad **[!UICONTROL Edit]**.

![](assets/mkg_dist_edit_kit.png)

Vanaf het tabblad **[!UICONTROL General]** kan de centrale entiteit:

* de beoordelaar(s) van het campagnepakket configureren via de koppeling **[!UICONTROL Approval parameters...]**;
* het uitvoeringsschema te herzien;
* lokale entiteiten toevoegen of verwijderen.

>[!NOTE]
>
>Door gebrek, kan elke entiteit tot een **lokale campagne** slechts eenmaal opdracht geven.
>   
>Schakel de optie **[!UICONTROL Enable multiple creation]** in als u meerdere lokale campagnes wilt maken op basis van het campagnepakket.

![](assets/mkg_dist_local_op_multi_crea.png)

### Meldingen {#notifications}

Wanneer een campagne beschikbaar wordt of wanneer de registratietermijn wordt bereikt, wordt een bericht verzonden naar de exploitanten van de lokale berichtgroep. Raadpleeg [Organisatorische entiteiten](../../campaign/using/about-distributed-marketing.md#organizational-entities) voor meer informatie hierover.

## Bestellen van een campagne {#ordering-a-campaign}

Campagnepakketten worden toegankelijk voor lokale entiteiten zodra ze zijn goedgekeurd en de uitvoeringsperiode ervan is begonnen. Lokale entiteiten ontvangen een e-mail met de mededeling dat er een nieuw campagnepakket beschikbaar is (zodra de beschikbaarheidsdatum is bereikt).

>[!NOTE]
>
>Als sommige lokale entiteiten bij het creëren van het campagnepakket werden gespecificeerd, zullen zij de enige zijn om een bericht te ontvangen. Als er geen lokale entiteit is opgegeven, ontvangen alle lokale entiteiten een kennisgeving.

![](assets/mkg_dist_local_op_notification.png)

Om een campagne van de centrale entiteit te gebruiken, moet de lokale entiteit het bevel geven.

Een campagne bestellen:

1. Klik **[!UICONTROL Order campaign]** in het berichtbericht, of de overeenkomstige knoop in Adobe Campaign.

   Voer uw id en wachtwoord in om de campagne te bestellen. De interface bestaat uit een set pagina&#39;s die zijn gedefinieerd in een webtoepassing.

   >[!NOTE]
   >
   >Webtoepassingen worden beschreven in [deze sectie](../../web/using/about-web-applications.md).

1. Voer de benodigde informatie in de eerste pagina in (orderlabel en opmerking) en klik op **[!UICONTROL Next]**.

   ![](assets/mkg_dist_subscribe_step1.png)

1. Voltooi de beschikbare parameters en keur de volgorde goed.

1. Er wordt een kennisgeving verzonden aan de beheerder van de organisatorische entiteit waartoe de lokale entiteit behoort, om deze bestelling goed te keuren.

   ![](assets/mkg_dist_subscribe_step3.png)

1. De informatie wordt geretourneerd aan de lokale en centrale entiteiten. Hoewel lokale entiteiten alleen hun eigen orders kunnen bekijken, kan de centrale entiteit alle orders van elke lokale entiteit bekijken, zoals hieronder wordt getoond:

   ![](assets/mkg_dist_subscribe_central_view.png)

   Operatoren kunnen ordergegevens weergeven:

   ![](assets/mkg_dist_local_op_catalog_detail_1.png)

   Het tabblad **[!UICONTROL Edit]** bevat informatie die door de lokale entiteit is ingevoerd tijdens het bestellen van de campagne.

   ![](assets/mkg_dist_local_op_catalog_detail_1b.png)

1. De order moet door de centrale entiteit worden goedgekeurd.

   ![](assets/mkg_dist_local_op_catalog_detail_3.png)

   Raadpleeg voor meer informatie de sectie [Goedkeuringsproces](#approval-process).

1. De lokale exploitant wordt vervolgens op de hoogte gesteld dat de campagne beschikbaar is: de beschikbaarheid van de campagne is te vinden in de lijst van campagnepakketten binnen **Campagnes** universum. De campagne kan dan worden gebruikt. Voor meer op dit, verwijs naar [Toegang tot campagnes](../../campaign/using/accessing-campaigns.md).

   Met de optie **[!UICONTROL Start targeting with order approval]** kan de lokale entiteit de campagne uitvoeren zodra de bestelling is goedgekeurd.

   ![](assets/mkg_dist_local_op_catalog_use.png)

## Een bestelling {#approving-an-order} goedkeuren

Om een campagneorder te bevestigen, moet de centrale entiteit het goedkeuren.

In het **[!UICONTROL Campaign orders]**-overzicht, dat u kunt openen via het **universum Campagnes**, kunt u de status van campagneorders bekijken en deze goedkeuren.

>[!NOTE]
>
>Lokale entiteiten kunnen wijzigingen in de bestelling aanbrengen totdat deze is goedgekeurd.

### Goedkeuringsproces {#approval-process}

#### E-mailmelding {#email-notification}

Wanneer een campagne wordt besteld door een lokale entiteit, worden de revisoren hiervan via e-mail op de hoogte gebracht, zoals hieronder wordt getoond:

![](assets/mkg_dist_valid_notif_email.png)

>[!NOTE]
>
>Het selecteren van revisoren wordt weergegeven in de sectie [Revisors](#reviewers). Ze kunnen de bestelling accepteren of afwijzen.

![](assets/mkg_dist_command_valid_web.png)

#### Goedkeuring via de Adobe Campaign-console {#approving-via-the-adobe-campaign-console}

De bestelling kan ook worden goedgekeurd via de console, in het overzicht van de campagnevolgorde. Als u een volgorde wilt goedkeuren, selecteert u deze en klikt u op **[!UICONTROL Approve the order]**.

![](assets/mkg_dist_local_order_valid.png)

>[!NOTE]
>
>De campagne kan nog worden uitgegeven en worden aangepast tot de datum van de campagnebeschikbaarheid. Lokale entiteiten kunnen de campagne ook afwijzen door op de knop **[!UICONTROL Cancel]** te klikken.

#### Een campagne maken {#creating-a-campaign}

Zodra een campagneorde wordt goedgekeurd, kan het door de lokale entiteit worden gevormd en worden uitgevoerd.

![](assets/mkg_dist_mutual_op_created.png)

Voor meer op dit, verwijs naar [Toegang tot campagnes](../../campaign/using/accessing-campaigns.md).

### Goedkeuring {#rejecting-an-approval} afwijzen

De met de goedkeuring belaste exploitant kan een bestelling of een campagnepakket afwijzen.

![](assets/mkg_dist_do_not_valid.png)

Indien de controleur een bestelling afwijst, wordt de desbetreffende kennisgeving automatisch naar de betrokken lokale entiteiten gezonden: het bevat de opmerking die is ingevoerd door de exploitant die de goedkeuring heeft geweigerd.

De informatie wordt getoond op de lijst van campagnepakketpagina of op de pagina van de campagneorde. Als ze toegang hebben tot de Adobe Campaign-console, worden lokale entiteiten op de hoogte gesteld van deze afwijzing.

![](assets/mkg_dist_do_not_valid_view.png)

Ze kunnen de verwante opmerking weergeven op het tabblad **[!UICONTROL Edit]** van het campagnepakket.

![](assets/mkg_dist_do_not_valid_tab.png)

### Revisoren {#reviewers}

Elke keer dat goedkeuring wordt vereist, worden revisoren via e-mail op de hoogte gesteld.

Voor elke lokale entiteit worden revisoren geselecteerd voor goedkeuring van de campagneorder en goedkeuring van de campagne. Raadpleeg [Organisatorische entiteiten](../../campaign/using/about-distributed-marketing.md#organizational-entities) voor meer informatie over het selecteren van lokale revisoren.

>[!NOTE]
>
>Om deze selectie mogelijk te maken, moet de goedkeuring van de bestelling nog niet effectief zijn.

### Een bestelling {#canceling-an-order} annuleren

Het centrale bureau kan een orde annuleren gebruikend de **[!UICONTROL Delete]** knoop, die op het ordedashboard wordt gevestigd.

![](assets/mkg_dist_local_op_cancel.png)

Hiermee annuleert u de campagne in de weergave **[!UICONTROL Campaign orders]**.
