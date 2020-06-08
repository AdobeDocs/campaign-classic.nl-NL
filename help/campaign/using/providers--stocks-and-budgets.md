---
title: Leveranciers, voorraden en begrotingen
seo-title: Leveranciers, voorraden en begrotingen
description: Leveranciers, voorraden en begrotingen
seo-description: null
page-status-flag: never-activated
uuid: 6caffaaf-a6a6-40e1-8b17-07c81748382c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: orchestrate-campaigns
discoiquuid: d4627141-cef1-4ddb-ad6a-5dc217b9fa96
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: e059fc9e2bfade30454601f31990c3ec14b8a847
workflow-type: tm+mt
source-wordcount: '1906'
ht-degree: 0%

---


# Leveranciers, voorraden en begrotingen{#providers-stocks-and-budgets}

Met Adobe Campaign kunt u serviceproviders definiëren die betrokken zijn bij de taken die in de campagnes worden uitgevoerd. Informatie over de serviceproviders en de bijbehorende kostenstructuren wordt door de beheerder van de Adobe-campagne vanuit de hoofdweergave gedefinieerd. Van de levering wordt naar de dienstverlener verwezen en de kostenstructuur ervan maakt het mogelijk de kosten van deze levering te berekenen en het betrokken bestand te beheren.

## Dienstverleners en hun kostenstructuren creëren {#creating-service-providers-and-their-cost-structures}

Elke serviceprovider wordt opgeslagen in een bestand met contactgegevens, servicesjablonen en verwante taken.

De dienstverleners worden gevormd in de **[!UICONTROL Administration > Campaign management]** knoop van de boom.

De taken die tijdens de leveringen worden uitgevoerd, worden door de dienstverleners verricht, met name voor direct mail en mobiele kanalen. Deze serviceproviders kunnen bijvoorbeeld betrokken zijn bij het afdrukken of verspreiden van berichten. Deze taken omvatten configuraties en kosten die specifiek zijn voor elke dienstverlener. De configuratie van dienstverleners omvat vier fasen:

1. Een serviceprovider maken in Adobe Campaign

   Zie Een [serviceprovider](#adding-a-service-provider)toevoegen.

1. Bepalend kostencategorieën en structuren van bijbehorende de dienstmalplaatjes

   Zie [Het bepalen van kostencategorieën](#defining-cost-categories) en het [bepalen van de kostenstructuur](#defining-the-cost-structure).

1. Configuratie van processen

   Zie het [Vormen processen verbonden aan de dienst](#configuring-processes-associated-with-a-service).

1. Verwijzen naar de dienstverlener op campagneniveau

   Zie Een service [koppelen aan een campagne](#associating-a-service-with-a-campaign).

### Het creëren van een dienstverlener en zijn kostencategorieën {#creating-a-service-provider-and-its-cost-categories}

#### Een serviceprovider toevoegen {#adding-a-service-provider}

U kunt zoveel serviceproviders maken als nodig zijn voor uw leveringen. De procedure voor het toevoegen van een dienstverlener is als volgt:

1. Klik met de rechtermuisknop op de lijst met serviceproviders en selecteer **[!UICONTROL New]** of klik op de **[!UICONTROL New]** knop boven de lijst met serviceproviders.
1. Geef in de onderste sectie van het venster de naam en contactgegevens van de serviceprovider op.

   ![](assets/s_ncs_user_supplier_node_01.png)

1. Klik op de **[!UICONTROL Save]** knop om het servicebureau aan de lijst toe te voegen.

#### Definiëren van kostencategorieën {#defining-cost-categories}

U moet de dienstmalplaatjes met elke dienstverlener associëren. In deze templates moet u eerst de kostencategorieën en, indien nodig, de betrokken voorraad identificeren. Vervolgens moet u de regels voor kostenberekening voor elke categorie maken, via de kostenstructuren.

>[!NOTE]
>
>Voor meer op dit, verwijs naar het [Definiëren van de kostenstructuur](#defining-the-cost-structure).

Een kostencategorie is een entiteit die een reeks kosten bevat die in aanmerking komen voor een bepaalde soort levering (e-mail, direct mail, enz.) of voor een taak. De categorieën van kosten worden gegroepeerd in de malplaatjes van de diensten verbonden aan de dienstverleners. Elke dienstverlener kan één of meerdere de dienstmalplaatjes van verwijzingen voorzien.

Pas de volgende stappen toe om een servicesjabloon te maken en de inhoud ervan te definiëren:

1. Klik op het **[!UICONTROL Services]** tabblad van het servicebureau op de **[!UICONTROL Add]** knop en geef de servicesjabloon een naam.

   ![](assets/s_ncs_user_supplier_node_create_template.png)

1. Maak de kostencategorieën voor elk type proces (levering per direct mail/e-mail/enz.). of taak). Om dit te doen, klik het **[!UICONTROL Cost categories]** lusje en toen de **[!UICONTROL Add]** knoop, en ga de parameters van elke kostencategorie in.

   ![](assets/s_ncs_user_supplier_node_03.png)

   * Voer een label in voor deze kostencategorie en selecteer het type proces in kwestie: Levering door **[!UICONTROL Direct mail]**, **[!UICONTROL E-mail]**, **[!UICONTROL Mobile]**, **[!UICONTROL Telephone]** of **[!UICONTROL Task]**.
   * Klik op de **[!UICONTROL Add]** knop om de typen kosten te definiëren die aan deze categorie zijn gekoppeld.
   * Indien nodig wordt een voorraadlijn gekoppeld aan elk type kosten, zodat de gebruikte hoeveelheden automatisch aan de bestaande voorraden worden gerelateerd.

      >[!NOTE]
      >
      >De voorraadlijnen worden bepaald in de **[!UICONTROL Stock management]** knoop.\
      >Raadpleeg voor meer informatie het beheer van [voorraden en bestellingen](#stock-and-order-management).

1. U kunt een waarde voor deze kostencategorie vooraf selecteren, die standaard wordt aangeboden in de kostencategorieën van de serviceprovider (in plaats van een leeg vak). Selecteer hiertoe de optie in de **[!UICONTROL Selected]** kolom voor het betrokken type categorie:

   ![](assets/s_ncs_user_supplier_cost_structure_defaut.png)

   Op leveringsniveau wordt de waarde standaard geselecteerd:

   ![](assets/s_ncs_user_supplier_default_cost.png)

### De kostenstructuur definiëren {#defining-the-cost-structure}

Voor elk type kosten worden in een kostenstructuur de toe te passen berekeningsregels vermeld.

Klik op het **[!UICONTROL Cost structure]** tabblad om de kostenberekening voor elke kostencategorie en elk type te configureren. Klik op **[!UICONTROL Add]** en voer de kostenstructuur in.

![](assets/s_ncs_user_supplier_node_04.png)

* Om de kostenstructuur tot stand te brengen, selecteer het type van bericht en de betreffende kostencategorie van de drop-down lijsten, evenals het type van kosten waarop de berekeningsregel zal van toepassing zijn. De inhoud van deze vervolgkeuzelijsten is afkomstig van de informatie die u hebt ingevoerd via het **[!UICONTROL Cost categories]** tabblad.

   U moet een label toewijzen aan de kostenstructuur. Standaard heeft deze de volgende leveringsomtrek: **Kostencategorie - Soort kosten**.

   U kunt de naam echter wijzigen: Voer de gewenste waarde rechtstreeks in het **[!UICONTROL Label]** veld in.

* De kostenberekeningsformule wordt gedefinieerd in de onderste sectie van het venster.

   Deze formule kan worden vastgesteld (voor om het even welk aantal berichten) of berekend volgens het aantal berichten.

   Wanneer het van het aantal berichten afhangt, kan de structuur van de kostenberekening zijn, **[!UICONTROL Linear]** of **[!UICONTROL Linear by threshold]****[!UICONTROL Constant by threshold]**.

#### Lineaire structuur {#linear-structure}

Als het bedrag altijd het zelfde voor een bericht (of een partij van berichten) ongeacht het totale aantal berichten is, selecteer **[!UICONTROL Linear]** en ga de kosten van elk bericht in.

![](assets/s_ncs_user_supplier_cost_structure_calc_01.png)

Als dit bedrag op een partij berichten van toepassing is, specificeer het aantal berichten betrokken op het **[!UICONTROL for]** gebied.

![](assets/s_ncs_user_supplier_cost_structure_calc_02.png)

#### Lineaire structuur volgens drempel {#linear-structure-by-threshold}

Als het bedrag door drempel voor elk bericht van toepassing is, moet u een **[!UICONTROL Linear by threshold]** berekeningsstructuur bepalen. In dit type van kostenstructuur, zal elk bericht 0.13 kosten, bijvoorbeeld, als het totale aantal berichten tussen 1 en 100 is, en 0.12 van 100 tot 1000 verzonden berichten zal kosten, of 0.11 voorbij 1000 berichten.

De configuratie is als volgt:

![](assets/s_ncs_user_supplier_cost_structure_calc_03.png)

Als u een drempelwaarde wilt toevoegen, klikt u op de **[!UICONTROL Add]** knop rechts van de lijst.

#### Constante structuur op drempel {#constant-structure-by-threshold}

Tot slot kunt u een kostenberekening op het totale aantal berichten vormen. Selecteer hiertoe een **[!UICONTROL Constant by threshold]** berekeningsstructuur. Bijvoorbeeld, zullen de kosten aan een vast bedrag van 12.00 voor 1 tot 100 berichten, en bij 100.00 voor een levering van 101 tot 1000 berichten, en 500.00 voor om het even welke levering meer dan 1000 berichten, ongeacht het totale aantal worden geplaatst.

![](assets/s_ncs_user_supplier_cost_structure_calc_04.png)

### Het vormen processen verbonden aan de dienst {#configuring-processes-associated-with-a-service}

U kunt informatie over de processen associëren verbonden aan de dienst via het **[!UICONTROL Processes]** lusje.

Om dit te doen, klik het **[!UICONTROL Processes]** lusje om het verzenden van informatie aan de router te vormen.

![](assets/s_ncs_user_supplier_node_02.png)

* De **[!UICONTROL File extraction]** sectie geeft de exportsjabloon aan die wordt gebruikt voor levering wanneer deze service is geselecteerd. U kunt de naam van het uitvoerbestand in het **[!UICONTROL Extraction file]** veld aangeven. Met de knop rechts van het veld kunt u variabelen invoegen.

   ![](assets/s_ncs_user_supplier_node_02a.png)

* In de **[!UICONTROL Notification e-mail]** sectie kunt u de sjabloon opgeven om serviceproviders op de hoogte te stellen nadat bestanden zijn verzonden. Selecteer de sjabloon die wordt gebruikt om het waarschuwingsbericht en de groep ontvangers te maken.

   Standaard worden leveringssjablonen voor berichtberichten opgeslagen in het **[!UICONTROL Administration > Campaign management > Technical delivery templates]** knooppunt, dat toegankelijk is vanuit de algemene weergave.

* In de **[!UICONTROL Post-processing]** sectie kunt u de workflow selecteren die u wilt starten nadat de levering is goedgekeurd. Als een werkstroomsjabloon wordt ingevoerd, wordt automatisch een werkstroominstantie gemaakt en gestart zodra de goedkeuring van kracht wordt. Deze workflow kan het extractiebestand bijvoorbeeld naar een externe serviceprovider sturen voor verwerking.

### Een service koppelen aan een campagne {#associating-a-service-with-a-campaign}

Services worden gekoppeld aan campagnes via leveringen of taken. Serviceproviders zijn gekoppeld aan leveringssjablonen om hun services aan te bieden in de leveringen die via deze sjabloon zijn gemaakt.

Wanneer een dienst wordt geselecteerd, de kostencategorieën die met het type van levering (direct mail, e-mail, enz.) corresponderen worden automatisch in de centrale tabel aangegeven, samen met de verwerkingsopties die zijn gedefinieerd.

>[!NOTE]
>
>Als geen kostencategorie wordt getoond wanneer de dienst wordt geselecteerd, betekent het dat geen kostencategorie voor dit type van proces werd bepaald. Als er bijvoorbeeld geen **[!UICONTROL E-mail]** kostencategorie voor het type is gedefinieerd voor het verzenden van e-mail, wordt er geen categorie weergegeven en heeft het selecteren van de service geen effect.

* Voor een directe postlevering, kunt u de dienst van het configuratievenster selecteren.

   ![](assets/s_ncs_user_supplier_mail_delivery_select.png)

* Voor levering op mobiele kanalen of telefoon geldt dezelfde selectiemodus.
* Voor een e-maillevering wordt de service geselecteerd op het **[!UICONTROL Advanced]** tabblad in de leveringseigenschappen, zoals in het volgende voorbeeld:

   ![](assets/s_ncs_user_supplier_email_delivery_select.png)

In de **[!UICONTROL Amount to surcharge]** kolom kunt u kosten voor deze categorie toevoegen in de context van de desbetreffende levering of taak.

U kunt verplichte selectie van een kostentype tijdens de definitie van kostencategorieën voor een levering opleggen. Selecteer **[!UICONTROL A cost type must be selected]** deze optie.

![](assets/s_ncs_user_supplier_cost_structure_select.png)

## Beheer van voorraden en orders {#stock-and-order-management}

De types van kosten kunnen met voorraadlijnen worden geassocieerd om alarm, spoorlevering, en lanceringsorden te behandelen.

De procedure voor het instellen van beheer van voorraden en bestellingen in Adobe Campaign, en het waarschuwen van operatoren in geval van onvoldoende voorraad voor levering, is als volgt:

1. Aanmaak van voorraden en referentie van verbonden dienstverleners

   Zie Een [voorraad](#creating-a-stock)maken.

1. Stamlijnen toevoegen

   Zie [Stalenlijnen](#adding-stock-lines)toevoegen.

1. Aanmeldende exploitanten in geval van een waarschuwing

   Zie [Waarschuwingsoperatoren](#alerting-operators).

1. Bestellingen en levering.

   Zie [Bestellingen](#orders).

### Voorraadbeheer {#stock-management}

Adobe Campagne kan een groep operatoren waarschuwen als het bestand is uitgeput of een minimumdrempel heeft bereikt. De voorraden zijn toegankelijk via de **[!UICONTROL Stocks]** verbinding van het **[!UICONTROL Campaigns]** universum via de **[!UICONTROL Other choices]** verbinding van het navigatiegebied.

![](assets/s_ncs_user_stocks_view.png)

#### Een voorraad maken {#creating-a-stock}

Pas de volgende stappen toe om een nieuwe voorraad te maken:

1. Klik op de **[!UICONTROL Create]** knop boven de lijst met bestanden.
1. Voer het label van de voorraad in en selecteer in de vervolgkeuzelijst de serviceprovider waaraan deze is gekoppeld.

   ![](assets/s_ncs_user_stocks_add.png)

   >[!NOTE]
   >
   >Voor meer informatie hierover, verwijs naar het [Creëren van dienstverleners en hun kostenstructuren](#creating-service-providers-and-their-cost-structures).

#### Stamlijnen toevoegen {#adding-stock-lines}

Een voorraad omvat verschillende voorraadlijnen. Een voorraadlijn bevat een initiële hoeveelheid middelen die door leveringen zal worden verbruikt. Elke voorraadlijn geeft de verbruikte hoeveelheid, de voorraad en de bestelde hoeveelheid aan.

Wanneer u een voorraad maakt, klikt u op het **[!UICONTROL Stock lines]** tabblad om nieuwe regels toe te voegen.

![](assets/s_ncs_user_stocks_display_line.png)

Nadat de voorraad is gemaakt, klikt u erop om deze te bewerken en gebruikt u het dashboard om aandelenlijnen te maken en weer te geven.

Klik op de **[!UICONTROL Create]** knop om de voorraadparameters te definiëren.

![](assets/s_ncs_user_stocks_new_line.png)

* Vermeld de oorspronkelijk in voorraad zijnde hoeveelheid in het **[!UICONTROL Initial stock]** veld. De **[!UICONTROL Consumed]** velden en **[!UICONTROL In stock]** velden worden automatisch berekend en bijgewerkt naarmate de campagnes vorderen.

   ![](assets/s_ncs_user_stocks_create_line.png)

* Vermeld de drempel waarvanaf exploitanten moeten worden gewaarschuwd voor de bestelling van voorraden in het **[!UICONTROL Alert level]** veld. Wanneer het alarmniveau wordt bereikt, wordt een waarschuwingsbericht getoond in het goedkeuringsvenster van leveringen die deze voorraad gebruiken.

#### Een aandeel koppelen aan kostencategorieën {#associating-a-stock-with-cost-categories}

Voor een bepaalde dienstverlener, in een dienst, kan een voorraadlijn door één van de kostencategorieën worden van verwijzingen voorzien, als volgt:

![](assets/s_ncs_user_stocks_select_from_supplier.png)

### Tracking van materiaal {#stock-tracking}

#### Waarschuwingsoperatoren {#alerting-operators}

Er wordt een waarschuwing weergegeven wanneer een voorraad waarnaar in een levering wordt verwezen, onvoldoende is. De volgende waarschuwing wordt bijvoorbeeld weergegeven wanneer een extractiebestand wordt goedgekeurd:

![](assets/s_ncs_user_stocks_valid_alert.png)

#### Orders {#orders}

Met het **[!UICONTROL Orders]** subtabblad kunt u de huidige bestellingen weergeven en nieuwe bestellingen opslaan.

![](assets/s_ncs_user_stocks_edit_from_board.png)

Als u een bestelling wilt opslaan, bewerkt u de doelvoorraadlijn, klikt u op de **[!UICONTROL Add]** knop en geeft u de leveringsdatum en de bestelde hoeveelheid op.

![](assets/s_ncs_user_stocks_node_06.png)

>[!NOTE]
>
>Zodra de leveringsdatum wordt bereikt, verdwijnt de geordende voorraadlijn automatisch en de hoeveelheid ingegaan op het **[!UICONTROL Volume on order]** gebied wordt toegevoegd aan het **[!UICONTROL Tracking]** lusje. Deze hoeveelheid wordt automatisch toegevoegd aan het voorraadvolume.

![](assets/s_ncs_user_stocks_node_08.png)

Het **[!UICONTROL Consumptions]** tabblad bevat het volume dat per campagne wordt verbruikt. De gegevens op dit tabblad worden automatisch ingevoerd op basis van de uitgevoerde leveringen. Klik op de **[!UICONTROL Edit]** knop om de desbetreffende campagne te openen.

![](assets/s_ncs_user_stocks_edit_from_board_consumed.png)

## Begroting berekenen {#calculating-budgets}

### Beginsel {#principle}

De kosten worden beheerd voor leveringen en campagnes. Volgens de vooruitgang worden deze kosten aan de begrotingen toegerekend.

De kosten voor de uitvoering van een campagne worden geconsolideerd op het niveau van de campagne en de kosten van alle campagnes van een programma worden doorberekend aan het programma waarmee zij worden geassocieerd. Met speciale rapporten kunt u de budgetten bijhouden voor het gehele platform of voor elk plan en elk programma.

### Implementatie {#implementation}

Als u in een campagne het budget selecteert, moet u het oorspronkelijke bedrag invoeren. De berekende kosten worden automatisch bijgewerkt op basis van het niveau van de aangegane verplichtingen (gemaakte, verwachte, gereserveerde, vastgelegde kosten). Zie [Bedragen](../../campaign/using/controlling-costs.md#calculating-amounts)berekenen.

>[!NOTE]
>
>De procedure voor het opstellen van begrotingen wordt voorgesteld in het [creëren van een begroting](../../campaign/using/controlling-costs.md#creating-a-budget).

