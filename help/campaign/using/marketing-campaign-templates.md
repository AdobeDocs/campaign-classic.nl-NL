---
product: campaign
title: Sjablonen voor marketingcampagnes
description: Sjablonen voor marketingcampagnes
role: User
feature: Campaigns, Templates
hide: true
hidefromtoc: true
exl-id: d272d4b9-f1b2-4fb2-9ed9-91a4aea7eca3
source-git-commit: 4f809011a8b4cb3803c4e8151e358e5fd73634e4
workflow-type: tm+mt
source-wordcount: '1128'
ht-degree: 0%

---

# Campagnesjablonen maken en configureren {#campaign-templates}

Alle marketing campagnes zijn gebaseerd op een malplaatje, dat belangrijkste kenmerken en mogelijkheden opslaat. Campagnersjablonen worden gecentraliseerd in het knooppunt **[!UICONTROL Resources > Templates > Campaign templates]** . Een standaardsjabloon wordt standaard verschaft. U kunt hiermee een nieuwe campagne maken met alle beschikbare modules (Documenten, Taken, zaadadressen, enz.), maar de aangeboden modules zijn afhankelijk van uw rechten en de configuratie van uw Adobe Campaign-platform.

![](assets/s_ncs_user_campaign_op_template_node.png)

>[!NOTE]
>
>De structuur wordt weergegeven wanneer u op het pictogram **[!UICONTROL Explorer]** op de startpagina klikt.

Een ingebouwde sjabloon wordt geleverd om een campagne te maken waarvoor geen specifieke configuratie is gedefinieerd. U kunt uw campagnemalplaatjes tot stand brengen en vormen en dan campagnes van deze malplaatjes tot stand brengen.

![](assets/do-not-localize/how-to-video.png) voor meer op campagneverwezenlijking, verwijs naar [ deze video ](../../campaign/using/marketing-campaign-deliveries.md#create-email-video).

## Een campagnemalplaatje maken {#creating-or-duplicating-a-campaign-template}

Volg onderstaande stappen om een campagnemalplaatje te maken:

1. Open Campagne **Ontdekkingsreiziger**.
1. In **Middelen > Malplaatjes > de malplaatjes van de Campagne**, klik **Nieuw** in de toolbar boven de lijst van malplaatjes.

   ![](assets/create_campaign_template_1.png)

1. Voer het label van uw nieuwe campagnemalplaatje in.
1. Klik **sparen** en open uw malplaatje opnieuw.
1. In **geef** lusje uit, ga de **Interne naam** en andere waarden in, indien nodig.
1. Selecteer **Geavanceerde campagnemontages** om een werkschema aan uw campagnemalplaatje toe te voegen.

   ![](assets/create_campaign_template_2.png)

1. Verander **het richten en werkschema&#39;s** waarde in **ja**.

   ![](assets/create_campaign_template_3.png)

1. In het **richten en werkschema&#39;s** lusje, klik **een werkschema toevoegen...**.

   ![](assets/create_campaign_template_4.png)

1. Voltooi het **Etiket** gebied en klik **O.K.**.
1. Maak uw workflow naar wens.
1. Klik **sparen**. Uw sjabloon is nu klaar om in een campagne te worden gebruikt.

U kunt **&#x200B;**&#x200B;het standaardmalplaatje ook dupliceren om zijn configuratie opnieuw te gebruiken en aan te passen.

De diverse lusjes en sub-tabs van het campagnemalplaatje staan u toe om tot zijn montages toegang te hebben, die in [ Algemene configuratie ](#general-configuration) worden beschreven.

![](assets/s_ncs_user_new_op_template_duplicate.png)

## Modules selecteren {#select-modules}

Met de koppeling **[!UICONTROL Advanced campaign settings...]** kunt u taken voor de campagnes op basis van deze sjabloon in- en uitschakelen. Selecteer de mogelijkheden die u wilt inschakelen in de campagnes die op deze sjabloon zijn gebaseerd.

![](assets/s_ncs_user_op_template_tab1.3.png)

Als een mogelijkheid niet is geselecteerd, worden de elementen met betrekking tot het proces (menu&#39;s, pictogrammen, opties, tabs, subtabs, enz.) niet weergegeven in de interface van de sjabloon of in campagnes op basis van deze sjabloon. De lusjes links van de campagnedetails vallen gewoonlijk met de processen samen die in het malplaatje worden geselecteerd. Bijvoorbeeld, als **Uitgaven en doelstellingen** niet wordt geselecteerd, zal het overeenkomstige **[!UICONTROL Budget]** lusje niet in campagnes worden getoond die op dit malplaatje worden gebaseerd.

Bovendien worden de kortere weg aan de configuratievensters toegevoegd aan het campagnesdashboard. Wanneer een functionaliteit wordt toegelaten, geeft een directe verbinding toegang tot het van het campagnesdashboard.

Bijvoorbeeld met de onderstaande configuratie:

![](assets/s_ncs_user_op_template_tab1.4.png)

De volgende koppelingen worden weergegeven in het campagnesashboard (de koppeling **[!UICONTROL Add a task]** ontbreekt):

![](assets/s_ncs_user_op_template_tab1.3ex.png)

En alleen de volgende tabbladen worden weergegeven:

![](assets/s_ncs_user_op_template_tab1.4ex.png)

Nochtans, met dit soort configuratie:

![](assets/s_ncs_user_op_template_tab2.2ex.png)

De volgende koppelingen en tabbladen worden weergegeven:

![](assets/s_ncs_user_op_template_tab2.3ex.png)

## Typologie van modules {#typology-of-enabled-modules}

* **de groep van de Controle**

  Wanneer deze module wordt geselecteerd, wordt een extra lusje toegevoegd aan de geavanceerde montages van het malplaatje en de campagnes die op dit malplaatje worden gebaseerd. De configuratie kan via het malplaatje of individueel voor elke campagne worden bepaald. Leer meer over controlegroepen in [ deze sectie ](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group).

  ![](assets/s_ncs_user_op_template_activate_1.png)

* **Seed-adressen**

  Wanneer deze module wordt geselecteerd, wordt een extra lusje toegevoegd aan de geavanceerde montages van het malplaatje en de campagnes die op dit malplaatje worden gebaseerd. De configuratie kan via het malplaatje of individueel voor elke campagne worden bepaald. Leer meer over zaadadressen in [ deze sectie ](../../delivery/using/about-seed-addresses.md).

  ![](assets/s_ncs_user_op_template_activate_2.png)

* **Documenten**

  Als deze module is geselecteerd, wordt een extra tabblad toegevoegd aan het tabblad **[!UICONTROL Edition]** van de sjabloon en aan de campagnes op basis van deze sjabloon. Bijgevoegde documenten kunnen worden toegevoegd vanuit de sjabloon of afzonderlijk voor elke campagne. Leer meer over documenten in [ deze sectie ](../../campaign/using/marketing-campaign-deliveries.md#managing-associated-documents).

  ![](assets/s_ncs_user_op_template_activate_3.png)

* **Overzicht**

  Wanneer deze module is geselecteerd, wordt een subtab **[!UICONTROL Delivery outlines]** toegevoegd aan het tabblad **[!UICONTROL Documents]** om de leveringscontouren voor de campagne te definiëren. Leer meer over leveringsoverzichten in [ deze sectie ](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline).

  ![](assets/s_ncs_user_op_template_activate_4.png)

* **het richten en werkschema&#39;s**

  Wanneer u de module **[!UICONTROL Targeting and workflows]** selecteert, wordt een tabblad toegevoegd waarop u een of meer workflows kunt maken voor campagnes die op deze sjabloon zijn gebaseerd. De werkschema&#39;s kunnen ook individueel voor elke campagne worden gevormd die op dit malplaatje wordt gebaseerd.Leer meer over campagnewerkschema&#39;s in [ deze sectie ](../../campaign/using/marketing-campaign-deliveries.md#building-the-main-target-in-a-workflow).

  ![](assets/s_ncs_user_op_template_activate_5.png)

  Wanneer deze module wordt toegelaten, wordt een lusje toegevoegd aan de geavanceerde montages van de campagne om de opeenvolging van de procesuitvoering te bepalen.

  ![](assets/s_ncs_user_op_template_activate_5a.png)

* **Goedkeuring**

  Als u **[!UICONTROL Approval]** selecteert, kunt u de processen selecteren die u wilt goedkeuren en de operatoren die verantwoordelijk zijn voor goedkeuringen. Leer meer over goedkeuringen in [ deze sectie ](../../campaign/using/marketing-campaign-approval.md#selecting-reviewers).

  ![](assets/s_ncs_user_op_template_activate_5b.png)

  U kunt kiezen of u procesgoedkeuring al dan niet wilt inschakelen via het tabblad **[!UICONTROL Approvals]** van de sectie Geavanceerde instellingen voor sjablonen. De banen waarvoor goedkeuring wordt geselecteerd moeten voor berichtlevering worden goedgekeurd om te worden toegelaten.

  U moet een revisoroperator of groep operatoren aan elke ingeschakelde goedkeuring koppelen.

* **Uitgaven en doelstellingen**

  Als deze module is geselecteerd, wordt een tabblad **[!UICONTROL Budget]** toegevoegd aan de details van de sjabloon en worden campagnes gebaseerd op deze sjabloon, zodat het bijbehorende budget kan worden geselecteerd.

  ![](assets/s_ncs_user_op_template_activate_7.png)

## Eigenschappen en uitvoering {#general-configuration}

### Sjablooneigenschappen {#template-properties}

![](assets/s_ncs_user_op_new_template.png)

Wanneer u een campagnemalplaatje creeert, moet u de volgende informatie ingaan:

* Ga het **etiket** van het malplaatje in: dit etiket zal door gebrek aan alle campagnes worden toegewezen die via dit malplaatje worden gecreeerd.
* Selecteer de campagne **aard** van de drop-down lijst. De waarden in deze lijst zijn die welke zijn opgeslagen in de opsomming **[!UICONTROL natureOp]** .

  >[!NOTE]
  >
  >Voor meer informatie over opsommingen, verwijs naar [ Begonnen het Worden ](../../platform/using/managing-enumerations.md) sectie.

* Selecteer het **type van campagne**: uniek, terugkerend, of periodiek. Standaard worden campagnemasjablonen toegepast op unieke campagnes. Het terugkomen en periodieke campagnes worden gedetailleerd in [ deze sectie ](../../campaign/using/setting-up-marketing-campaigns.md#recurring-and-periodic-campaigns).
* Geef de duur van de campagne op, d.w.z. het aantal dagen waarop de campagne zal plaatsvinden. Wanneer u een campagne maakt op basis van deze sjabloon, worden de begin- en einddatums van de campagne automatisch ingevuld.

  Als de campagne terugkerend is, moet u de begin en einddata van de campagne direct in het malplaatje specificeren.

* Specificeer het **verwante programma** van het malplaatje: de campagnes die op dit malplaatje worden gebaseerd zullen met het geselecteerde programma worden verbonden.

### Parameters voor sjabloonuitvoering {#template-execution-parameters}

Met de koppeling **[!UICONTROL Advanced campaign settings...]** kunt u de geavanceerde opties van de sjabloon configureren voor de verwerking van het leveringsdoel (controlegroep, zaadadressen, enz.) en de configuratie van de meting van de campagne en de uitvoering van de workflow.

![](assets/s_ncs_user_op_template_tab1.2.png)

## Uitvoering van campagne bijhouden{#campaign-reverse-scheduling}

U kunt een programma voor een campagne en spoorprestaties tot stand brengen, bijvoorbeeld om een gebeurtenisprogramma voor een specifieke datum voor te bereiden. De malplaatjes van de campagne laten u nu de begindatum van een taak berekenen die op de einddatum van een campagne wordt gebaseerd.

Ga in het vak Taakconfiguratie naar het **[!UICONTROL Implementation schedule]** -gebied en schakel het selectievakje **[!UICONTROL The start date is calculated based on the campaign end date]** in. (Hier is &quot;begindatum&quot; de begindatum van de taak.) Ga naar het **[!UICONTROL Start]** gebied en ga een interval in: de taak zal lang vóór de campagneeinddatum beginnen. Als u een periode ingaat die langer is dan de campagne aan laatste wordt geplaatst, zal de taak vóór de campagne beginnen.

![](assets/mrm_task_in_template_start_date.png)

Wanneer u een campagne gebruikend dit malplaatje creeert, zal de datum van de taakaanvang automatisch worden berekend. U kunt deze echter altijd later wijzigen.
