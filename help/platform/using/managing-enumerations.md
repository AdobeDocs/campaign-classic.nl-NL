---
product: campaign
title: Opsommingen beheren
description: Opsommingen beheren
feature: Data Management
badge: label="v7" type="Informative" tooltip="Alleen van toepassing op Campaign Classic v7"
audience: platform
content-type: reference
topic-tags: administration-basics
exl-id: 2ece058d-b493-4fea-b3db-322cf7ea7f4f
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '882'
ht-degree: 0%

---

# Opsommingen beheren{#managing-enumerations}



Een opsomming (ook wel &#39;gespecificeerde lijst&#39; genoemd) is een lijst met waarden die door het systeem worden voorgesteld om bepaalde velden te vullen. Met opsommingen kunt u de waarden van deze velden standaardiseren en informatie invoeren of gebruiken binnen query&#39;s.

De lijst met waarden wordt weergegeven als een vervolgkeuzelijst waaruit u de waarde kunt selecteren die in het veld moet worden ingevoerd. De vervolgkeuzelijst maakt ook voorspellende invoer mogelijk, waarbij de operator de eerste paar letters invoert en de toepassing de rest invult.

Sommige consolevelden zijn gedefinieerd met dit type opsommingen. Opsommingen worden &quot;open&quot; genoemd als u waarden kunt toevoegen door de gegevens rechtstreeks in het desbetreffende veld in te voeren.

## Toegang tot waarden {#access-to-values}

De waarden voor dit type veld worden gedefinieerd en het algemene beheer van deze velden (het toevoegen/verwijderen van een waarde) wordt uitgevoerd via de **[!UICONTROL Administration > Platform > Enumerations]** knooppunt van de structuur.

![](assets/s_ncs_user_itemized_list_node.png)

* De bovenste sectie bevat een lijst met velden waarvoor een gespecificeerde lijst is gedefinieerd.
* In de onderste sectie worden de voorgestelde waarden weergegeven. Deze waarden worden herhaald in de editors die dit veld gebruiken.

  ![](assets/s_ncs_user_itemized_list_values.png)

  Als u een nieuwe opsommingswaarde wilt maken, klikt u op **[!UICONTROL Add]**.

  ![](assets/s_ncs_user_itemized_list.png)

  Als de **[!UICONTROL Open]** is geselecteerd, kan de gebruiker een nieuwe gespecificeerde lijstwaarde direct op het overeenkomstige gebied toevoegen. Met een bevestigingsbericht kunt u deze waarde maken.

  ![](assets/s_ncs_user_itemized_list_new_value.png)

* Als de **[!UICONTROL Closed]** is geselecteerd, kunnen gebruikers geen nieuwe waarden maken, maar alleen een keuze maken uit de beschikbare waarden.

## Gegevens standaardiseren {#standardizing-data}

### Informatie over het opschonen van aliassen {#about-alias-cleansing}

In de gespecificeerde lijstgebieden, kunt u waarden buiten opsommingswaarden ingaan. Deze kunnen worden opgeslagen zoals ze zijn of worden gereinigd.

>[!CAUTION]
>
>Het zuiveren van gegevens is een kritiek proces dat de gegevens in het gegevensbestand beïnvloedt. Adobe Campaign voert massagegevensupdates uit, wat ertoe kan leiden dat sommige waarden worden verwijderd. Deze bewerking is daarom voorbehouden aan professionele gebruikers.

De ingevoerde waarde is dan:

* Toegevoegd aan de gespecificeerde lijstwaarden: in dit geval **[!UICONTROL Open]** moet worden geselecteerd,
* of wordt automatisch vervangen door de bijbehorende alias: In dit geval moet dit geval worden gedefinieerd in het **[!UICONTROL Alias]** tabblad van de gespecificeerde lijst,
* of wordt opgeslagen in de lijst met aliassen: er wordt later een alias aan toegewezen.

  >[!NOTE]
  >
  >Als u mogelijkheden voor gegevenszuivering moet gebruiken, selecteert u de optie **[!UICONTROL Alias cleansing]** in de gespecificeerde lijst.

### Aliassen gebruiken {#using-aliases}

De optie **[!UICONTROL Alias cleansing]** maakt het mogelijk aliassen te gebruiken voor de geselecteerde gespecificeerde lijst. Als deze optie is geselecteerd, wordt **[!UICONTROL Alias]** wordt onder in het venster weergegeven.

![](assets/s_ncs_user_itemized_list_alias_option.png)

#### Een alias maken {#creating-an-alias}

Klik op **[!UICONTROL Add]**.

![](assets/s_ncs_user_itemized_list_alias_create.png)

Voer de alias die u wilt omzetten en de waarde in die u wilt toepassen en klik op **[!UICONTROL Ok]**.

![](assets/s_ncs_user_itemized_list_alias_create_2.png)

Controleer parameters voordat u deze bewerking bevestigt.

>[!CAUTION]
>
>Zodra dit stadium is bevestigd, kunnen de eerder ingevoerde waarden niet worden teruggevorderd: zij zijn vervangen.

![](assets/s_ncs_user_itemized_list_alias_create_3.png)

Wanneer een gebruiker de waarde invoert **NEILSEN** in een &quot;bedrijf&quot;gebied (in de console van Adobe Campaign of in een vorm), zal het automatisch door de waarde vervangen **NIELSEN Ltd**. De vervanging van de waarde wordt uitgevoerd door **Aliasreiniging** workflow. Zie [Gegevens wissen](#running-data-cleansing).

![](assets/s_ncs_user_itemized_list_alias_use.png)

#### Waarden omzetten in aliassen {#converting-values-into-aliases}

Als u een opsommingswaarde wilt omzetten in een alias, klikt u met de rechtermuisknop in de lijst met waarden en kiest u **[!UICONTROL Convert values into aliases...]**.

![](assets/s_ncs_user_itemized_list_alias_detail.png)

Kies de waarden die u wilt omzetten en klik op **[!UICONTROL Next]**.

![](assets/s_ncs_user_itemized_list_alias_transform.png)

Klikken **[!UICONTROL Start]** om de conversie uit te voeren.

![](assets/s_ncs_user_itemized_list_alias_detail1.png)

Zodra de uitvoering is voltooid, wordt de alias toegevoegd aan de lijst met aliassen.

![](assets/s_ncs_user_itemized_list_alias_detail2.png)

#### Aliasresultaten ophalen {#retrieving-alias-hits}

De waarden die door de gebruikers worden ingevoerd, kunnen in aliassen worden omgezet. Wanneer de gebruiker een waarde invoert die niet in de gespecificeerde lijst is opgenomen, wordt de waarde opgeslagen in het dialoogvenster **[!UICONTROL Alias]** tab.

De **Aliasreiniging** de technische workflow herstelt deze waarden elke nacht om de gespecificeerde lijst bij te werken. Zie [Gegevens wissen](#running-data-cleansing)

Indien nodig **[!UICONTROL Hits]** Deze kolom kan het aantal keren weergeven dat deze waarde is ingevoerd. Het berekenen van deze waarde kan tijd en geheugen vergen. Raadpleeg voor meer informatie hierover [Voorvallen van item berekenen](#calculating-entry-occurrences).

### Gegevens wissen {#running-data-cleansing}

De gegevens worden gewist door de **[!UICONTROL Alias cleansing]** technische workflow. De configuraties die voor opsommingen worden gedefinieerd, worden tijdens de uitvoering toegepast. Zie [Workflow voor Aliasverwijdering](#alias-cleansing-workflow).

De reiniging kan worden geactiveerd via de **[!UICONTROL Cleanse values...]** koppeling.

![](assets/s_ncs_user_itemized_list_alias_start_normalize.png)

De **[!UICONTROL Advanced parameters...]** Met de koppeling kunt u de datum instellen vanaf welke verzamelde waarden in aanmerking worden genomen.

![](assets/s_ncs_user_itemized_list_alias_normalize.png)

Klik op de knop **[!UICONTROL Start]** om gegevens te wissen.

#### Voorvallen van item berekenen {#calculating-entry-occurrences}

De **[!UICONTROL Alias]** Het subtabblad van een gespecificeerde lijst kan het aantal exemplaren van een alias onder alle ingevoerde waarden weergeven. Deze informatie is een schatting en wordt weergegeven in de **[!UICONTROL Hits]** kolom.

>[!CAUTION]
>
>Het berekenen van voorvallen van aliasinggegevens kan lang duren. Daarom is voorzichtigheid geboden wanneer het gebruiken van deze functie.

U kunt de aanraakberekening handmatig uitvoeren via de **[!UICONTROL Cleanse values...]** koppeling. Om dit te doen, klik **[!UICONTROL Advanced parameters...]** en selecteer de gewenste optie(s).

![](assets/s_ncs_user_itemized_list_alias_hits.png)

* **[!UICONTROL Update the number of alias hits]**: hiermee kunt u treffers bijwerken die al zijn berekend op basis van de ingevoerde datum.
* **[!UICONTROL Recalculate the number of alias hits from the start]**: hiermee kunt u berekeningen uitvoeren op het hele Adobe Campaign-platform.

U kunt ook een specifieke workflow maken, zodat de berekening automatisch gedurende een bepaalde periode wordt uitgevoerd, bijvoorbeeld eenmaal per week.

Hiertoe maakt u een kopie van het **[!UICONTROL Alias cleansing]** de werkstroom, verandert de planner en gebruikt de volgende montages in **[!UICONTROL Enumeration value cleansing]** activiteit:

* **-updateHits** om het aantal aliashits bij te werken,
* **-updateHits:full** om alle aliashits opnieuw te berekenen.

#### Workflow voor Aliasverwijdering {#alias-cleansing-workflow}

De **Aliasreiniging** in de workflow worden opsommingswaarden gewist. Standaard wordt de transactie dagelijks uitgevoerd.

Het is toegankelijk via de **[!UICONTROL Administration > Production > Technical workflows]** knooppunt.

![](assets/s_ncs_user_itemized_list_alias_wf.png)
