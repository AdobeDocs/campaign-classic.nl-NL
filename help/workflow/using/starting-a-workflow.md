---
product: campaign
title: Een workflow starten
description: Leer hoe u een workflow start en werkstroomhandelingen ontdekt op de werkbalk en met de rechtermuisknop op het menu klikt
feature: Workflows
hide: true
hidefromtoc: true
exl-id: d345ba62-c2fb-43df-a2a1-e9e4292d301a
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '1179'
ht-degree: 1%

---

# Een workflow starten {#starting-a-workflow}



Een workflow wordt altijd handmatig gestart. Wanneer begonnen, kan het echter inactief afhankelijk van de informatie blijven die via een planner wordt gespecificeerd (zie [ Planner ](scheduler.md)) of activiteit die plannen.

De acties met betrekking tot het richten van werkschemauitvoering (lancering, einde, pauze, enz.) zijn **asynchrone** processen: de orde wordt geregistreerd en zal van kracht zijn zodra de server beschikbaar is om het toe te passen.

Met de werkbalk kunt u de uitvoering van de workflow starten en volgen.

De lijst met opties in het menu **[!UICONTROL Actions]** en in het menu Klikken met de rechtermuisknop vindt u hieronder in detail.

>[!IMPORTANT]
>
>Houd in mening dat, wanneer een exploitant een actie op een werkschema (begin, einde, pauze, enz.) uitvoert, de actie niet onmiddellijk wordt uitgevoerd, maar in plaats daarvan in een rij geplaatst om door de [ werkschemamodule ](architecture.md) te worden verwerkt.

## Werkbalk Handelingen {#actions-toolbar}

De toolbarknopen zijn gedetailleerd in deze [ sectie ](../../campaign/using/marketing-campaign-deliveries.md#building-the-main-target-in-a-workflow). Met de knop **[!UICONTROL Actions]** hebt u toegang tot extra uitvoeringsopties voor het reageren op geselecteerde workflows. U kunt ook het menu **[!UICONTROL File > Actions]** gebruiken of met de rechtermuisknop op een workflow klikken en **[!UICONTROL Actions]** selecteren.

![](assets/purge_historique.png)

* **[!UICONTROL Start]**

  Deze actie laat u de uitvoering van een werkschema beginnen: een werkschema dat **&#x200B;**&#x200B;wordt geëindigd, **wordt uitgegeven** of **Gepauzeerde** verandert status in **Begonnen**. De workflow-engine handelt vervolgens de uitvoering van deze workflow af. Als de werkstroom is gepauzeerd, wordt deze hervat, anders wordt de werkstroom van het begin gestart en worden de initiële activiteiten geactiveerd.

  Starten is een asynchroon proces: de aanvraag wordt opgeslagen en zo snel mogelijk verwerkt door een workflowserver.

* **[!UICONTROL Pause]**

  Deze actie plaatst het statuut van het werkschema aan **Gepauzeerde**. Er worden geen activiteiten geactiveerd totdat de werkstroom wordt hervat; de lopende bewerkingen worden echter niet gepauzeerd.

* **[!UICONTROL Stop]**

  Met deze handeling wordt een workflow gestopt die momenteel wordt uitgevoerd. Het statuut van de instantie wordt geplaatst aan **Voltooid**. Bewerkingen die worden uitgevoerd, worden indien mogelijk gestopt. Importeren en SQL-query&#39;s worden onmiddellijk geannuleerd.

  >[!IMPORTANT]
  >
  >Het beëindigen van een workflow is een asynchroon proces: de aanvraag wordt geregistreerd en vervolgens worden bewerkingen door de workflowserver(s) geannuleerd. Het stoppen van een werkstroominstantie kan daarom tijd in beslag nemen, vooral als de werkstroom op meerdere servers wordt uitgevoerd, die elk de controle moeten krijgen om de actieve taken te annuleren. U voorkomt problemen door te wachten tot de stopbewerking is voltooid en geen meerdere stopaanvragen uit te voeren in dezelfde workflow.

* **[!UICONTROL Unconditional stop]**

  Met deze optie wijzigt u de workflowstatus in **[!UICONTROL Finished]** . Deze handeling mag alleen als laatste redmiddel worden gebruikt als het normale stopproces na enkele minuten mislukt. Gebruik de onvoorwaardelijke stop alleen als u zeker weet dat er geen werkstroomtaken worden uitgevoerd.

  >[!CAUTION]
  >
  >De onvoorwaardelijke stop is beperkt tot Admin gebruikers.

* **[!UICONTROL Restart]**

  Deze actie stopt en start de workflow opnieuw. Doorgaans kunt u sneller opnieuw opstarten. Het is ook handig om opnieuw starten te automatiseren wanneer het stoppen enige tijd in beslag neemt. Dit komt omdat de opdracht Stoppen niet beschikbaar is wanneer de workflow wordt gestopt.

  De **[!UICONTROL Start / Pause / Stop / Restart]** -acties zijn ook beschikbaar via de uitvoeringspictogrammen op de werkbalk. Raadpleeg deze [sectie](../../campaign/using/marketing-campaign-deliveries.md#creating-a-targeting-workflow) voor meer informatie.

  Merk op dat het **Begin** actie niet de variabelen van de werkschemainstantie in vergelijking met **Uitvoering** ontruimt, **Einde**, en **Begin** acties (de instantievariabelen die op actie van het Begin) ontruimen. Wanneer u een werkstroom opnieuw start, zijn instantievariabelen nog steeds beschikbaar voor gebruik met opgeslagen waarden. U kunt deze wissen door:
   * Voer **Stoppen** en **3&rbrace; acties van het Begin uit**.
   * Voeg onder javascript-code toe aan het einde van de workflowuitvoering:

     ```
     var wkf = xtk.workflow.load(instance.id)
     wkf.variables='<variables/>'
     wkf.save()
     ```

* **[!UICONTROL Purge history]**

  Met deze handeling kunt u de historie van de workflow wissen. Voor meer op dit, verwijs naar [ het Schrappen van de logboeken ](monitoring-workflow-execution.md#purging-the-logs).

* **[!UICONTROL Start in simulation mode]**

  Met deze optie kunt u de workflow starten in de simulatiemodus in plaats van in de echte modus. Dit betekent dat wanneer u deze modus inschakelt, alleen activiteiten worden uitgevoerd die geen invloed hebben op de database of het bestandssysteem (bijvoorbeeld **[!UICONTROL Query]** , **[!UICONTROL Union]** , **[!UICONTROL Intersection]** , enz.). Activiteiten die wel van invloed zijn (bijvoorbeeld **[!UICONTROL Export]** , **[!UICONTROL Import]** , enz.), en activiteiten die erna plaatsvinden (in dezelfde vertakking), worden niet uitgevoerd.

* **[!UICONTROL Execute pending tasks now]**

  Met deze handeling kunt u alle lopende taken zo snel mogelijk starten. Als u een specifieke taak wilt starten, klikt u met de rechtermuisknop op de desbetreffende activiteit en selecteert u **[!UICONTROL Execute pending task(s) now]** .

* **[!UICONTROL Save as template]**

  Met deze actie maakt u een nieuw werkstroomsjabloon op basis van de geselecteerde workflow. U moet de map opgeven waarin deze wordt opgeslagen (in het veld **[!UICONTROL Folder]** ).

  De opties **[!UICONTROL Mass update of selected lines]** en **[!UICONTROL Merge selected lines]** zijn algemene platformopties die beschikbaar zijn in alle **[!UICONTROL Actions]** -menu&#39;s. Raadpleeg deze [sectie](../../platform/using/updating-data.md) voor meer informatie.


## Best practices voor workflowuitvoering {#workflow-execution-best-practices}

**om geen werkschema te plannen om meer dan om de 15 minuten** in werking te stellen omdat het algemene systeemprestaties kan belemmeren en blokken in het gegevensbestand tot stand brengen.

**vermijd het verlaten van uw werkschema&#39;s in een gepauzeerde staat**. Als u een tijdelijke werkstroom creeert, zorg ervoor het correct zal kunnen voltooien en niet in een **[!UICONTROL paused]** staat blijven. Als het wordt gepauzeerd, zou het impliceren dat u de tijdelijke lijsten moet houden en zo de grootte van het gegevensbestand verhogen. Wijs onder Workfloweigenschappen workflowtoezichthouders toe om een waarschuwing te verzenden wanneer een workflow mislukt of wordt gepauzeerd door het systeem.

U voorkomt als volgt dat workflows worden gepauzeerd:

* Controleer uw workflows regelmatig om te controleren of er geen onverwachte fouten zijn.
* Houd uw workflows zo eenvoudig mogelijk, bijvoorbeeld door grote workflows te splitsen in verschillende workflows. U kunt **[!UICONTROL External signal]** -activiteiten gebruiken om de uitvoering ervan te activeren op basis van de uitvoering van andere workflows.
* Vermijd het hebben van gehandicapte activiteiten met stromen in uw werkschema&#39;s die draden open verlaten en tot vele tijdelijke lijsten leiden die veel ruimte kunnen verbruiken. Bewaar activiteiten niet in de **[!UICONTROL Do not enable]** - of **[!UICONTROL Enable but do not execute]** -status in uw workflows.

**Stop ongebruikte werkschema&#39;s**. Workflows die actief blijven, onderhouden verbindingen met de database.

**gebruikt slechts onvoorwaardelijke stop in de rastergevallen**. Deze optie is beperkt tot Admin-gebruikers. Deze handeling niet regelmatig gebruiken. Het niet uitvoeren van een schone sluiting op verbindingen die door werkstromen aan het gegevensbestand worden geproduceerd beïnvloedt prestaties.

**voert geen veelvoudige eindeverzoeken op het zelfde werkschema** uit. Het beëindigen van een workflow is een asynchroon proces: de aanvraag wordt geregistreerd en vervolgens worden bewerkingen door de workflowserver(s) geannuleerd. Het stoppen van een werkstroominstantie kan daarom tijd in beslag nemen, vooral als de werkstroom op meerdere servers wordt uitgevoerd, die elk de controle moeten krijgen om de actieve taken te annuleren. U voorkomt problemen door te wachten tot de stopbewerking is voltooid en te voorkomen dat een workflow meerdere keren wordt gestopt.

## Klikken met rechtermuisknop {#right-click-menu}

Wanneer een of meer workflowactiviteiten zijn geselecteerd, kunt u met de rechtermuisknop klikken om op uw selectie te reageren.

![](assets/contextual_menu.png)

De volgende opties zijn beschikbaar in het klikmenu met de rechtermuisknop:

**[!UICONTROL Open]** : met deze optie hebt u toegang tot de eigenschappen activity.

**[!UICONTROL Display logs:]** met deze optie kunt u het logboek voor taakuitvoering weergeven voor de geselecteerde activiteit. Verwijs naar [ Weergevend logboeken ](monitoring-workflow-execution.md#displaying-logs).

**[!UICONTROL Execute pending task(s) now:]** hiermee kunt u taken die in behandeling zijn, zo snel mogelijk starten.

**[!UICONTROL Workflow restart from a task:]** Met deze optie kunt u de workflow opnieuw starten met de resultaten die eerder voor deze activiteit zijn opgeslagen.

**[!UICONTROL Cut/Copy/Paste/Delete:]** Met deze opties kunt u activiteiten knippen, kopiëren, plakken en verwijderen.

Met deze optie kunt u een screenshot maken van alle activiteiten. **[!UICONTROL Copy as bitmap:]**

**[!UICONTROL Normal execution / Enable but do not execute / Do not enable:]** deze opties zijn ook beschikbaar op het tabblad **[!UICONTROL Advanced]** van de eigenschappen activity. Zij zijn gedetailleerd in [ Uitvoering ](advanced-parameters.md#execution).

Met **[!UICONTROL Save / Cancel:]** kunt u de wijzigingen in een workflow opslaan of annuleren.

>[!NOTE]
>
>U kunt een groep activiteiten selecteren en er een van deze opdrachten op toepassen.

Het met de rechtermuisknop aanklikken menu is ook gedetailleerd in deze [ sectie ](../../campaign/using/marketing-campaign-deliveries.md#executing-a-workflow).
