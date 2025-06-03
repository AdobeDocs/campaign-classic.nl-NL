---
product: campaign
title: CRM-connectors, gegevenssynchronisatie
description: Gegevens beheren tussen Campagne en uw CRM
feature: Microsoft CRM Integration, Salesforce Integration
exl-id: 7f9eda15-76e8-40a1-8302-004cea085778
hide: true
hidefromtoc: true
source-git-commit: 42cec0e9bede94a2995a5ad442822512bda14f2b
workflow-type: tm+mt
source-wordcount: '1529'
ht-degree: 0%

---

# Gegevens tussen Campagne en CRM synchroniseren {#data-synchronization}



De synchronisatie van gegevens tussen Adobe Campaign en CRM wordt uitgevoerd via een specifieke werkschemaactiviteit: [ schakelaar CRM ](../../workflow/using/crm-connector.md).

Als u bijvoorbeeld de Microsoft Dynamics-gegevens wilt importeren in Adobe Campaign, maakt u het volgende type workflow:

![](assets/crm_connectors_msdynamics_07.png)

Deze workflow importeert de contactpersonen via Microsoft Dynamics, synchroniseert deze met de bestaande Adobe Campaign-gegevens, verwijdert dubbele contactpersonen en werkt de Adobe Campaign-database bij.

De **[!UICONTROL CRM Connector]** -activiteit moet worden geconfigureerd om gegevens te synchroniseren.

![](assets/crm_connectors_msdynamics_08.png)

Met deze activiteit kunt u:

* De invoer van CRM - [ leert meer ](#importing-from-the-crm)
* De uitvoer naar CRM - [ leert meer ](#exporting-to-the-crm)
* De voorwerpen van de invoer die in CRM worden geschrapt - [ leren meer ](#importing-objects-deleted-in-the-crm)
* De voorwerpen van de schrapping in CRM - [ leren meer ](#deleting-objects-in-the-crm)

![](assets/crm_task_select_op.png)

Selecteer de externe rekening die CRM aanpast dat u synchronisatie met wilt vormen, dan het te synchroniseren voorwerp selecteren: rekeningen, kansen, lood, contacten, enz.

![](assets/crm_task_select_obj.png)

De configuratie van deze activiteit hangt af van het uit te voeren proces. Hieronder worden verschillende configuraties beschreven.

## Invoer uit de BCR {#importing-from-the-crm}

Om gegevens via CRM in Adobe Campaign te importeren, moet u het volgende type workflow maken:

![](assets/crm_wf_import.png)

Voor een importactiviteit zijn de stappen in de **[!UICONTROL CRM Connector]** activity configuration:

1. Selecteer een bewerking **[!UICONTROL Import from the CRM]** .
1. Ga naar de vervolgkeuzelijst **[!UICONTROL Remote object]** en selecteer het object waarop het proces betrekking heeft. Dit object valt samen met een van de tabellen die in Adobe Campaign worden gemaakt tijdens de verbindingsconfiguratie.
1. Ga naar de sectie **[!UICONTROL Remote fields]** en voer de velden in die u wilt importeren.

   Als u een veld wilt toevoegen, klikt u op de knop **[!UICONTROL Add]** op de werkbalk en vervolgens op het pictogram **[!UICONTROL Edit expression]** .

   ![](assets/crm_task_import_add_field.png)

   Wijzig zo nodig de gegevensindeling in de vervolgkeuzelijst met de kolommen **[!UICONTROL Conversion]** . De mogelijke omzettingstypes zijn gedetailleerd in [ formaat van Gegevens ](#data-format).

   >[!IMPORTANT]
   >
   >De identificator van de record in de CRM is verplicht voor het koppelen van objecten in CRM en in Adobe Campaign. Deze wordt automatisch toegevoegd wanneer het vak wordt goedgekeurd.
   >
   >De laatste wijzigingsdatum aan de CRM-zijde is ook verplicht voor de incrementele invoer van gegevens.

1. U kunt de te importeren gegevens ook filteren op basis van uw behoeften. Klik hiertoe op de koppeling **[!UICONTROL Edit the filter...]** .

   In het volgende voorbeeld importeert Adobe Campaign alleen contactpersonen waarvoor enige activiteit is opgenomen sinds 1 november 2012.

   ![](assets/crm_task_import_filter.png)

   >[!IMPORTANT]
   >
   >De beperkingen verbonden aan gegevens het filtreren wijzen zijn gedetailleerd in [ het Filtreren gegevens ](#filtering-data).

1. Met de optie **[!UICONTROL Use automatic index...]** kunt u automatisch incrementele objectsynchronisatie tussen de CRM en Adobe Campaign beheren, afhankelijk van de datum en de laatste wijziging.

   Voor meer op dit, verwijs naar [ veranderlijk beheer ](#variable-management).

### Variabelen beheren {#variable-management}

Schakel de optie **[!UICONTROL Automatic index]** in om alleen objecten te verzamelen die zijn gewijzigd sinds de laatste import.

![](assets/crm_task_import_option.png)

De datum van de laatste synchronisatie wordt opgeslagen in een optie die in het configuratievenster wordt gespecificeerd, door gebrek: **LASTIMPORT_&lt;%=instance.internalName%>_&lt;%=activityName%>**.

>[!NOTE]
>
>Deze opmerking is alleen van toepassing op de algemene **[!UICONTROL CRM Connector]** -activiteit. Voor andere CRM-activiteiten is het proces automatisch.
>
>Deze optie moet handmatig worden gemaakt en ingevuld onder **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Options]** . Dit moet een tekstoptie zijn en de waarde ervan moet overeenkomen met de volgende indeling: **`yyyy/MM/dd hh:mm:ss`** .
> 
>U moet deze optie handmatig bijwerken als u wilt doorgaan met importeren.

U kunt het verre gebied van CRM specificeren dat in aanmerking moet worden genomen om de meest recente veranderingen te identificeren.

Standaard worden de volgende velden gebruikt (in de opgegeven volgorde):

* Voor Microsoft Dynamics: **gewijzigd**,
* Voor Salesforce.com: **LastModifiedDate**, **SystemModstamp**.

Als u de optie **[!UICONTROL Automatic index]** activeert, worden drie variabelen gegenereerd die in de synchronisatieworkflow kunnen worden gebruikt via een **[!UICONTROL JavaScript code]** -type-activiteit. Deze activiteiten zijn:

* **vars.crmOptionName**: vertegenwoordigt de naam van de optie die de laatste invoerdatum bevat.
* **vars.crmStartImport**: vertegenwoordigt de begindatum (inbegrepen) van de laatste gegevensherstel.
* **vars.crmEndDate**: vertegenwoordigt de (uitgesloten) einddatum van de laatste gegevensherstel.

  >[!NOTE]
  >
  >Deze datums worden weergegeven in de volgende notatie: **`yyyy/MM/dd hh:mm:ss`** .

### Gegevens filteren {#filtering-data}

Om efficiënte werking met diverse CRMs te verzekeren, moeten de filters worden gecreeerd gebruikend de volgende regels:

* Elk filterniveau mag slechts één type operator gebruiken.
* De operator AND NOT wordt niet ondersteund.
* Vergelijkingen mogen alleen betrekking hebben op null-waarden (&#39;is leeg&#39;/&#39;is geen leeg&#39; type) of getallen. Dit betekent dat de waarde (rechterkolom) wordt beoordeeld en dat het resultaat van deze beoordeling een getal moet zijn. Vergelijking van JOIN-typen wordt daarom niet ondersteund.
* De waarde in de rechterkolom wordt beoordeeld in JavaScript.
* JOIN-vergelijkingen worden niet ondersteund.
* De expressie in de linkerkolom moet een veld zijn. Het kan geen combinatie zijn van verschillende expressies, een getal, enzovoort.

De volgende filtervoorwaarden zijn bijvoorbeeld NIET geldig voor een CRM-import, omdat de OR-operator op hetzelfde niveau wordt geplaatst als de AND-operatoren:

* De operator OR wordt op hetzelfde niveau geplaatst als de operator AND
* Vergelijkingen worden uitgevoerd op tekenreeksen

![](assets/crm_import_wrong_filter.png)

### Volgorde van {#order-by}

In Microsoft Dynamics en Salesforce.com kunt u de externe velden die u wilt importeren in oplopende of aflopende volgorde sorteren.

Klik hiertoe op de koppeling **[!UICONTROL Order by]** en voeg de kolommen toe aan de lijst.

De volgorde van de kolommen in de lijst is de sorteervolgorde:

![](assets/crm_import_order.png)

### Registeridentificatie {#record-identification}

In plaats van elementen te importeren die in de CRM zijn opgenomen (en mogelijk zijn gefilterd), kunt u een populatie gebruiken die vooraf in de workflow is berekend.

Selecteer hiertoe de optie **[!UICONTROL Use the population calculated upstream]** en geef het veld op dat de externe id bevat.

Selecteer vervolgens de velden van de binnenkomende populatie die u wilt importeren, zoals hieronder wordt weergegeven:

![](assets/crm_wf_import_calculated_population.png)

## Exporteren naar de CRM {#exporting-to-the-crm}

Het uitvoeren van de gegevens van Adobe Campaign in CRM laat u volledige inhoud aan een gegevensbestand van CRM kopiëren.

Als u gegevens naar CRM wilt exporteren, moet u het volgende type workflow maken:

![](assets/crm_export_diagram.png)

Pas voor een exportbewerking de volgende configuratie toe op de **[!UICONTROL CRM Connector]** -activiteit:

1. Selecteer een bewerking **[!UICONTROL Export to CRM]** .
1. Ga naar de vervolgkeuzelijst **[!UICONTROL Remote object]** en selecteer het object waarop het proces betrekking heeft. Dit object valt samen met een van de tabellen die in Adobe Campaign worden gemaakt tijdens de verbindingsconfiguratie.

   >[!IMPORTANT]
   >
   >De exportfunctie van de **[!UICONTROL CRM Connector]** -activiteit kan velden invoegen of bijwerken aan de CRM-zijde. Om gebiedsupdates in CRM toe te laten, moet u de primaire sleutel van de verre lijst specificeren. Als de sleutel ontbreekt, worden gegevens ingevoegd (in plaats van bijgewerkt).

1. Schakel **[!UICONTROL Export in Batches]** in als u sneller wilt exporteren.

   ![](assets/crm_export_config_2.png)

1. Klik in de sectie **[!UICONTROL Mapping]** op **[!UICONTROL New]** om de velden op te geven die u wilt exporteren en de toewijzing ervan in de CRM-component.

   ![](assets/crm_export_config.png)

   Als u een veld wilt toevoegen, klikt u op de knop **[!UICONTROL Add]** op de werkbalk en vervolgens op het pictogram **[!UICONTROL Edit expression]** .

   >[!NOTE]
   >
   >Voor een bepaald veld kunnen de waarden niet worden bijgewerkt als er geen overeenkomst aan de CRM-zijde is gedefinieerd: ze worden rechtstreeks in de CRM ingevoegd.

   Wijzig zo nodig de gegevensindeling in de vervolgkeuzelijst met de kolommen **[!UICONTROL Conversion]** . De mogelijke omzettingstypes zijn gedetailleerd in [ formaat van Gegevens ](#data-format).

   >[!NOTE]
   >
   >De lijst met te exporteren records en het resultaat van de export worden opgeslagen in een tijdelijk bestand dat toegankelijk blijft totdat de workflow is voltooid of opnieuw is gestart. Hierdoor kunt u het proces opnieuw starten in het geval van fouten zonder dat u het risico loopt dezelfde record meerdere keren te exporteren of gegevens te verliezen.

## Aanvullende configuraties {#additional-configurations}

### Gegevensindeling {#data-format}

U kunt gegevensindeling direct omzetten wanneer u deze importeert in of vanuit de CRM.

Selecteer hiertoe de conversie die in de overeenkomende kolom moet worden toegepast.

![](assets/crm_task_import.png)

In de modus **[!UICONTROL Default]** worden automatisch gegevens omgezet. In de meeste gevallen is dit gelijk aan een kopie/plakbewerking van de gegevens. Tijdzonebeheer wordt echter toegepast.

Andere mogelijke omzettingen zijn:

* **[!UICONTROL Date only]**: in deze modus verwijdert u velden voor datum- en tijdtype.
* **[!UICONTROL Without time offset]**: in deze modus wordt het tijdzonebeheer geannuleerd dat in de standaardmodus wordt toegepast.
* **[!UICONTROL Copy/Paste]**: in deze modus worden onbewerkte gegevens gebruikt, zoals tekenreeksen (geen conversie).

### Fout bij verwerken {#error-processing}

In het kader van de invoer of de uitvoer van gegevens, kunt u een specifiek proces op fouten en verwerpingen toepassen. Selecteer hiertoe de opties **[!UICONTROL Process rejects]** en **[!UICONTROL Process errors]** op het tabblad **[!UICONTROL Behavior]** .

![](assets/crm_export_options.png)

Met deze opties worden de overeenkomende uitvoerovergangen geplaatst.

![](assets/crm_export_transitions.png)

Plaats vervolgens de activiteiten die relevant zijn voor de processen die u wilt toepassen.

Als u bijvoorbeeld fouten wilt verwerken, kunt u een wachtdoos toevoegen en opnieuw een poging plannen.

Afwijzingen worden verzameld met hun foutcode en het bijbehorende bericht. Dit betekent dat u de registratie van afwijzingen kunt instellen om het synchronisatieproces te optimaliseren.

>[!NOTE]
>
>Zelfs als de optie **[!UICONTROL Process rejects]** niet is ingeschakeld, wordt een waarschuwing gegenereerd voor elke geweigerde kolom met een foutcode en een foutbericht.

Met de uitvoerovergang **[!UICONTROL Reject]** hebt u toegang tot het uitvoerschema dat de specifieke kolommen bevat die relevant zijn voor foutberichten en -codes. Voor Salesforce.com, is deze kolom **errorSymbol** (foutensymbool, verschillend van de foutencode), **errorMessage** (beschrijving van de foutencontext).

## Objecten importeren die zijn verwijderd in de CRM {#importing-objects-deleted-in-the-crm}

Om het opzetten van een uitgebreid proces van de gegevenssynchronisatie toe te laten, kunt u voorwerpen invoeren die in CRM worden geschrapt in Adobe Campaign.

Hiervoor voert u de volgende stappen uit:

1. Selecteer een bewerking **[!UICONTROL Import objects deleted in the CRM]** .
1. Ga naar de vervolgkeuzelijst **[!UICONTROL Remote object]** en selecteer het object waarop het proces betrekking heeft. Dit object valt samen met een van de tabellen die in Adobe Campaign worden gemaakt tijdens de verbindingsconfiguratie.
1. Geef de verwijderingsperiode op waarmee rekening moet worden gehouden in de velden **[!UICONTROL Start date]** en **[!UICONTROL End date]** . Deze data worden in de periode opgenomen.

   ![](assets/crm_import_deleted_obj.png)

   >[!IMPORTANT]
   >
   >De periode voor het verwijderen van elementen moet samenvallen met de specifieke beperkingen van de BCR. Dit betekent bijvoorbeeld dat elementen die meer dan 30 dagen geleden zijn verwijderd, niet kunnen worden hersteld.

## Objecten verwijderen in de CRM-toepassing {#deleting-objects-in-the-crm}

Om voorwerpen op de kant van CRM te schrappen, moet u de primaire sleutel van de verre te schrappen elementen specificeren.

![](assets/crm_delete_in_crm.png)

Op het tabblad **[!UICONTROL Behavior]** kunt u de verwerking van afwijzingen inschakelen. Met deze optie wordt een tweede uitvoerovergang voor de **[!UICONTROL CRM connector]** -activiteit gegenereerd. Voor meer op dit, verwijs naar [ verwerking van de Fout ](#error-processing).

>[!NOTE]
>
>Zelfs wanneer de optie **[!UICONTROL Process rejects]** is uitgeschakeld, wordt een waarschuwing gegenereerd voor elke geweigerde kolom.
>
