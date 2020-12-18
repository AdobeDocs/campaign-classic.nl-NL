---
solution: Campaign Classic
product: campaign
title: Providers, voorraden en budgetten
description: Providers, voorraden en budgetten
audience: campaign
content-type: reference
topic-tags: orchestrate-campaigns
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1902'
ht-degree: 0%

---


# Providers, voorraden en budgetten{#providers-stocks-and-budgets}

Met Adobe Campaign kunt u serviceproviders definiëren die betrokken zijn bij de taken die in de campagnes worden uitgevoerd. Informatie over de dienstverleners en de bijbehorende kostenstructuren wordt door de Adobe Campaign-beheerder in hoofdlijnen gedefinieerd. Van de levering wordt naar de dienstverlener verwezen en de kostenstructuur ervan maakt het mogelijk de kosten van deze levering te berekenen en het betrokken bestand te beheren.

## Serviceproviders maken en hun kostenstructuur {#creating-service-providers-and-their-cost-structures}

Elke serviceprovider wordt opgeslagen in een bestand met contactgegevens, servicesjablonen en verwante taken.

Serviceproviders worden geconfigureerd in het knooppunt **[!UICONTROL Administration > Campaign management]** van de structuur.

De taken die tijdens de leveringen worden uitgevoerd, worden door de dienstverleners verricht, met name voor direct mail en mobiele kanalen. Deze serviceproviders kunnen bijvoorbeeld betrokken zijn bij het afdrukken of verspreiden van berichten. Deze taken omvatten configuraties en kosten die specifiek zijn voor elke dienstverlener. De configuratie van dienstverleners omvat vier fasen:

1. Opzetten van een serviceprovider in Adobe Campaign

   Zie [Een serviceprovider toevoegen](#adding-a-service-provider).

1. Bepalend kostencategorieën en structuren van bijbehorende de dienstmalplaatjes

   Zie [kostencategorieën definiëren](#defining-cost-categories) en [De kostenstructuur definiëren](#defining-the-cost-structure).

1. Configuratie van processen

   Zie [Processen configureren die zijn gekoppeld aan een service](#configuring-processes-associated-with-a-service).

1. Verwijzen naar de dienstverlener op campagneniveau

   Zie [Een service koppelen aan een campagne](#associating-a-service-with-a-campaign).

### Een serviceprovider en de bijbehorende kostencategorieën maken {#creating-a-service-provider-and-its-cost-categories}

#### Een serviceprovider {#adding-a-service-provider} toevoegen

U kunt zoveel serviceproviders maken als nodig zijn voor uw leveringen. De procedure voor de toevoeging van een dienstverlener is als volgt:

1. Klik met de rechtermuisknop op de lijst met serviceproviders en selecteer **[!UICONTROL New]** of klik op de knop **[!UICONTROL New]** boven de lijst met serviceproviders.
1. Geef in de onderste sectie van het venster de naam en contactgegevens van de serviceprovider op.

   ![](assets/s_ncs_user_supplier_node_01.png)

1. Klik op de knop **[!UICONTROL Save]** om de serviceprovider aan de lijst toe te voegen.

#### Definiëren van kostencategorieën {#defining-cost-categories}

U moet de dienstmalplaatjes met elke dienstverlener associëren. In deze templates moet u eerst de kostencategorieën en, indien nodig, de betrokken voorraad identificeren. Vervolgens moet u de regels voor kostenberekening voor elke categorie maken, via de kostenstructuren.

>[!NOTE]
>
>Raadpleeg [De kostenstructuur definiëren](#defining-the-cost-structure) voor meer informatie.

Een kostencategorie is een entiteit die een reeks kosten bevat die in aanmerking komen voor een bepaalde soort levering (e-mail, direct mail, enz.) of voor een taak. De categorieën van kosten worden gegroepeerd in de malplaatjes van de diensten verbonden aan de dienstverleners. Elke dienstverlener kan één of meerdere de dienstmalplaatjes van verwijzingen voorzien.

Pas de volgende stappen toe om een servicesjabloon te maken en de inhoud ervan te definiëren:

1. Klik op het tabblad **[!UICONTROL Services]** van het servicebureau op de knop **[!UICONTROL Add]** en geef een naam op voor de servicesjabloon.

   ![](assets/s_ncs_user_supplier_node_create_template.png)

1. Maak de kostencategorieën voor elk type proces (levering per direct mail/e-mail/enz.). of taak). Om dit te doen, klik **[!UICONTROL Cost categories]** tabel en dan **[!UICONTROL Add]** knoop, en ga de parameters van elke kostencategorie in.

   ![](assets/s_ncs_user_supplier_node_03.png)

   * Voer een label in voor deze kostencategorie en selecteer het type proces in kwestie: Levering door **[!UICONTROL Direct mail]**, **[!UICONTROL E-mail]**, **[!UICONTROL Mobile]**, **[!UICONTROL Telephone]** of **[!UICONTROL Task]**.
   * Klik op de knop **[!UICONTROL Add]** om de typen kosten te definiëren die aan deze categorie zijn gekoppeld.
   * Indien nodig wordt een voorraadlijn gekoppeld aan elk type kosten, zodat de gebruikte hoeveelheden automatisch aan de bestaande voorraden worden gerelateerd.

      >[!NOTE]
      >
      >De voorraadlijnen worden bepaald in **[!UICONTROL Stock management]** knoop.\
      >Raadpleeg [Stock- en orderbeheer](#stock-and-order-management) voor meer informatie hierover.

1. U kunt een waarde voor deze kostencategorie vooraf selecteren, die standaard wordt aangeboden in de kostencategorieën van de serviceprovider (in plaats van een leeg vak). Selecteer hiertoe de optie in de kolom **[!UICONTROL Selected]** voor het betrokken type categorie:

   ![](assets/s_ncs_user_supplier_cost_structure_defaut.png)

   Op leveringsniveau wordt de waarde standaard geselecteerd:

   ![](assets/s_ncs_user_supplier_default_cost.png)

### De kostenstructuur {#defining-the-cost-structure} definiëren

Voor elk type kosten worden in een kostenstructuur de toe te passen berekeningsregels vermeld.

Klik op het tabblad **[!UICONTROL Cost structure]** om de kostenberekening voor elke kostencategorie en elk type te configureren. Klik op **[!UICONTROL Add]** en voer de kostenstructuur in.

![](assets/s_ncs_user_supplier_node_04.png)

* Om de kostenstructuur tot stand te brengen, selecteer het type van bericht en de betreffende kostencategorie van de drop-down lijsten, evenals het type van kosten waarop de berekeningsregel zal van toepassing zijn. De inhoud van deze vervolgkeuzelijsten is afkomstig van de gegevens die zijn ingevoerd via het tabblad **[!UICONTROL Cost categories]**.

   U moet een label toewijzen aan de kostenstructuur. Standaard heeft deze de volgende leveringsomtrek: **Kostencategorie - Soort kosten**.

   U kunt de naam echter wijzigen: Voer de gewenste waarde rechtstreeks in het veld **[!UICONTROL Label]** in.

* De kostenberekeningsformule wordt gedefinieerd in de onderste sectie van het venster.

   Deze formule kan worden vastgesteld (voor om het even welk aantal berichten) of berekend volgens het aantal berichten.

   Wanneer deze afhankelijk is van het aantal berichten, kan de kostenberekeningsstructuur **[!UICONTROL Linear]**, **[!UICONTROL Linear by threshold]**, of **[!UICONTROL Constant by threshold]** zijn.

#### Lineaire structuur {#linear-structure}

Als het bedrag altijd het zelfde voor een bericht (of een partij van berichten) ongeacht het totale aantal berichten is, uitgezocht **[!UICONTROL Linear]** en ga de kosten van elk bericht in.

![](assets/s_ncs_user_supplier_cost_structure_calc_01.png)

Als dit bedrag op een partij berichten van toepassing is, specificeer het aantal berichten betrokken op **[!UICONTROL for]** gebied.

![](assets/s_ncs_user_supplier_cost_structure_calc_02.png)

#### Lineaire structuur op drempel {#linear-structure-by-threshold}

Als het bedrag door drempel voor elk bericht van toepassing is, moet u een **[!UICONTROL Linear by threshold]** berekeningsstructuur bepalen. In dit type van kostenstructuur, zal elk bericht 0.13 kosten, bijvoorbeeld, als het totale aantal berichten tussen 1 en 100 is, en 0.12 van 100 tot 1000 verzonden berichten zal kosten, of 0.11 voorbij 1000 berichten.

De configuratie is als volgt:

![](assets/s_ncs_user_supplier_cost_structure_calc_03.png)

Als u een drempelwaarde wilt toevoegen, klikt u op de knop **[!UICONTROL Add]** rechts van de lijst.

#### Constante structuur op drempel {#constant-structure-by-threshold}

Tot slot kunt u een kostenberekening op het totale aantal berichten vormen. Selecteer hiertoe een **[!UICONTROL Constant by threshold]**-berekeningsstructuur. Bijvoorbeeld, zullen de kosten aan een vast bedrag van 12.00 voor 1 tot 100 berichten, en bij 100.00 voor een levering van 101 tot 1000 berichten, en 500.00 voor om het even welke levering meer dan 1000 berichten, ongeacht het totale aantal worden geplaatst.

![](assets/s_ncs_user_supplier_cost_structure_calc_04.png)

### Aan een service gekoppelde processen configureren {#configuring-processes-associated-with-a-service}

U kunt informatie over de processen associëren verbonden aan de dienst via **[!UICONTROL Processes]** tabel.

Om dit te doen, klik **[!UICONTROL Processes]** lusje om het verzenden van informatie aan de router te vormen.

![](assets/s_ncs_user_supplier_node_02.png)

* De sectie **[!UICONTROL File extraction]** geeft de exportsjabloon aan die wordt gebruikt voor levering wanneer deze service is geselecteerd. U kunt de naam van het uitvoerbestand aangeven in het veld **[!UICONTROL Extraction file]**. Met de knop rechts van het veld kunt u variabelen invoegen.

   ![](assets/s_ncs_user_supplier_node_02a.png)

* In de sectie **[!UICONTROL Notification e-mail]** kunt u de sjabloon opgeven om serviceproviders op de hoogte te stellen nadat bestanden zijn verzonden. Selecteer de sjabloon die wordt gebruikt om het waarschuwingsbericht en de groep ontvangers te maken.

   Standaard worden leveringssjablonen voor berichtberichten opgeslagen in het knooppunt **[!UICONTROL Administration > Campaign management > Technical delivery templates]**, dat toegankelijk is vanuit de algemene weergave.

* In de sectie **[!UICONTROL Post-processing]** kunt u de workflow selecteren die u wilt starten nadat de levering is goedgekeurd. Als een werkstroomsjabloon wordt ingevoerd, wordt automatisch een werkstroominstantie gemaakt en gestart zodra de goedkeuring van kracht wordt. Deze workflow kan het extractiebestand bijvoorbeeld naar een externe serviceprovider sturen voor verwerking.

### Een service koppelen aan een campagne {#associating-a-service-with-a-campaign}

Services worden gekoppeld aan campagnes via leveringen of taken. Serviceproviders zijn gekoppeld aan leveringssjablonen om hun services aan te bieden in de leveringen die via deze sjabloon zijn gemaakt.

Wanneer een dienst wordt geselecteerd, de kostencategorieën die met het type van levering (direct mail, e-mail, enz.) corresponderen worden automatisch in de centrale tabel aangegeven, samen met de verwerkingsopties die zijn gedefinieerd.

>[!NOTE]
>
>Als geen kostencategorie wordt getoond wanneer de dienst wordt geselecteerd, betekent het dat geen kostencategorie voor dit type van proces werd bepaald. Als er bijvoorbeeld geen kostencategorie voor het type **[!UICONTROL E-mail]** is gedefinieerd voor het verzenden van e-mail, wordt geen categorie weergegeven en heeft het selecteren van de service geen effect.

* Voor een directe postlevering, kunt u de dienst van het configuratievenster selecteren.

   ![](assets/s_ncs_user_supplier_mail_delivery_select.png)

* Voor levering op mobiele kanalen of telefoon geldt dezelfde selectiemodus.
* Voor een e-maillevering wordt de service geselecteerd op het tabblad **[!UICONTROL Advanced]** in de leveringseigenschappen, zoals in het volgende voorbeeld:

   ![](assets/s_ncs_user_supplier_email_delivery_select.png)

In de kolom **[!UICONTROL Amount to surcharge]** kunt u kosten voor deze categorie toevoegen in de context van de desbetreffende levering of taak.

U kunt verplichte selectie van een kostentype tijdens de definitie van kostencategorieën voor een levering opleggen. Selecteer **[!UICONTROL A cost type must be selected]** om dit te doen.

![](assets/s_ncs_user_supplier_cost_structure_select.png)

## Beheer van aandelen en orders {#stock-and-order-management}

De types van kosten kunnen met voorraadlijnen worden geassocieerd om alarm, spoorlevering, en lanceringsorden te behandelen.

De procedure voor het opzetten van het beheer van de voorraden en de orders in Adobe Campaign en voor het waarschuwen van de marktdeelnemers in geval van ontoereikende leveranties is als volgt:

1. Aanmaak van voorraden en referentie van verbonden dienstverleners

   Zie [Een bestand maken](#creating-a-stock).

1. Stamlijnen toevoegen

   Zie [Stamlijnen toevoegen](#adding-stock-lines).

1. Aanmeldende exploitanten in geval van een waarschuwing

   Zie [Waarschuwingsoperatoren](#alerting-operators).

1. Bestellingen en levering.

   Zie [Orders](#orders).

### Bestandsbeheer {#stock-management}

Adobe Campaign kan een groep operatoren waarschuwen als het bestand is uitgeput of een minimumdrempel heeft bereikt. De voorraadniveaus zijn toegankelijk via de **[!UICONTROL Stocks]** verbinding van **[!UICONTROL Campaigns]** universum via de **[!UICONTROL Other choices]** verbinding van het navigatiegebied.

![](assets/s_ncs_user_stocks_view.png)

#### Een bestand {#creating-a-stock} maken

Pas de volgende stappen toe om een nieuwe voorraad te maken:

1. Klik op de knop **[!UICONTROL Create]** boven de lijst met bestanden.
1. Voer het label van de voorraad in en selecteer in de vervolgkeuzelijst de serviceprovider waaraan deze is gekoppeld.

   ![](assets/s_ncs_user_stocks_add.png)

   >[!NOTE]
   >
   >Raadpleeg [Serviceproviders en hun kostenstructuren maken](#creating-service-providers-and-their-cost-structures) voor meer informatie.

#### Stamlijnen {#adding-stock-lines} toevoegen

Een voorraad omvat verschillende voorraadlijnen. Een voorraadlijn bevat een initiële hoeveelheid middelen die door leveringen zal worden verbruikt. Elke voorraadlijn geeft de verbruikte hoeveelheid, de voorraad en de bestelde hoeveelheid aan.

Wanneer u een voorraad maakt, klikt u op het tabblad **[!UICONTROL Stock lines]** om nieuwe regels toe te voegen.

![](assets/s_ncs_user_stocks_display_line.png)

Nadat de voorraad is gemaakt, klikt u erop om deze te bewerken en gebruikt u het dashboard om aandelenlijnen te maken en weer te geven.

Klik op de knop **[!UICONTROL Create]** om de voorraadparameters te definiëren.

![](assets/s_ncs_user_stocks_new_line.png)

* Vermeld de oorspronkelijk in voorraad zijnde hoeveelheid in het veld **[!UICONTROL Initial stock]**. De velden **[!UICONTROL Consumed]** en **[!UICONTROL In stock]** worden automatisch berekend en bijgewerkt naarmate de campagnes vorderen.

   ![](assets/s_ncs_user_stocks_create_line.png)

* Vermeld de drempel waarvanaf exploitanten moeten worden gewaarschuwd voor het bestellen van voorraden in het veld **[!UICONTROL Alert level]**. Wanneer het alarmniveau wordt bereikt, wordt een waarschuwingsbericht getoond in het goedkeuringsvenster van leveringen die deze voorraad gebruiken.

#### Een aandeel koppelen aan kostencategorieën {#associating-a-stock-with-cost-categories}

Voor een bepaalde dienstverlener, in een dienst, kan een voorraadlijn door één van de kostencategorieën worden van verwijzingen voorzien, als volgt:

![](assets/s_ncs_user_stocks_select_from_supplier.png)

### Stock tracking {#stock-tracking}

#### Waarschuwingsoperatoren {#alerting-operators}

Er wordt een waarschuwing weergegeven wanneer een voorraad waarnaar in een levering wordt verwezen, onvoldoende is. De volgende waarschuwing wordt bijvoorbeeld weergegeven wanneer een extractiebestand wordt goedgekeurd:

![](assets/s_ncs_user_stocks_valid_alert.png)

#### Bestellingen {#orders}

Met het subtabblad **[!UICONTROL Orders]** kunt u de huidige bestellingen weergeven en nieuwe bestellingen opslaan.

![](assets/s_ncs_user_stocks_edit_from_board.png)

Als u een bestelling wilt opslaan, bewerkt u de doelvoorraadlijn, klikt u op de knop **[!UICONTROL Add]** en geeft u de leveringsdatum en de bestelde hoeveelheid op.

![](assets/s_ncs_user_stocks_node_06.png)

>[!NOTE]
>
>Zodra de leveringsdatum wordt bereikt, verdwijnt de geordende voorraadlijn automatisch en de hoeveelheid ingegaan op **[!UICONTROL Volume on order]** gebied wordt toegevoegd aan **[!UICONTROL Tracking]** tabel. Deze hoeveelheid wordt automatisch toegevoegd aan het voorraadvolume.

![](assets/s_ncs_user_stocks_node_08.png)

Het tabblad **[!UICONTROL Consumptions]** bevat het volume dat per campagne wordt verbruikt. De gegevens op dit tabblad worden automatisch ingevoerd op basis van de uitgevoerde leveringen. Klik op de knop **[!UICONTROL Edit]** om de betreffende campagne te openen.

![](assets/s_ncs_user_stocks_edit_from_board_consumed.png)

## Begroting {#calculating-budgets}

### Beginsel {#principle}

De kosten worden beheerd voor leveringen en campagnes. Volgens de vooruitgang worden deze kosten aan de begrotingen toegerekend.

De kosten voor de uitvoering van een campagne worden geconsolideerd op het niveau van de campagne en de kosten van alle campagnes van een programma worden doorberekend aan het programma waarmee zij worden geassocieerd. Met speciale rapporten kunt u de budgetten bijhouden voor het gehele platform of voor elk plan en elk programma.

### Implementatie {#implementation}

Als u in een campagne het budget selecteert, moet u het oorspronkelijke bedrag invoeren. De berekende kosten worden automatisch bijgewerkt op basis van het niveau van de aangegane verplichtingen (gemaakte, verwachte, gereserveerde, vastgelegde kosten). Zie [Hoeveelheden berekenen](../../campaign/using/controlling-costs.md#calculating-amounts).

>[!NOTE]
>
>De procedure voor het maken van budgetten wordt weergegeven in [Een budget maken](../../campaign/using/controlling-costs.md#creating-a-budget).

