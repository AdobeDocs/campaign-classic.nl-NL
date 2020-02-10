---
title: Workflows controleren
seo-title: Workflows controleren
description: Workflows controleren
seo-description: null
page-status-flag: never-activated
uuid: e16d1c40-50ae-4c3d-95df-fac62f987a15
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: 978cbe62-f06a-46a6-b8a1-e30a65b8470a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: cfb1b02a6261c001392b5cc6430f00206e802bb8

---


# Workflows controleren{#supervising-workflows}

In dit geval wordt het maken van een workflow beschreven waarmee u de status kunt controleren van een set werkstromen die worden gepauzeerd, gestopt of met fouten.

Het doel van de verordening is:

* Gebruik een werkschema om een groep bedrijfswerkschema&#39;s te controleren.
* Verzend een bericht naar een supervisor via een &quot;levering&quot;activiteit.

Als u de status van een set workflows wilt controleren, moet u de volgende stappen uitvoeren:

1. Maak de controleworkflow.
1. Schrijf JavaScript om te bepalen of werkstromen worden gepauzeerd, tegengehouden of met fouten.
1. Maak de **[!UICONTROL Test]** activiteit.
1. Bereid het leveringsmalplaatje voor.

>[!NOTE]
>
>Naast het werkschema, staat de Heatmap **van het** Werkschema van de Campagne u toe om in details de werkschema&#39;s te analyseren die momenteel lopen. Raadpleeg de [desbetreffende sectie](../../workflow/using/heatmap.md)voor meer informatie hierover.
>
>Raadpleeg **deze sectie** voor meer informatie over hoe u de uitvoering [van uw workflows kunt](../../workflow/using/monitoring-workflow-execution.md)controleren.

## Stap 1: De controleworkflow maken {#step-1--creating-the-monitoring-workflow}

De werkschemamap die wij gaan controleren is de omslag **&quot;CustomWorkflows&quot;** die in het **Beleid > Productie > de knoop van Technische werkschema** wordt opgeslagen. Deze map bevat een set bedrijfsworkflows.

De **monitoringworkflow** wordt in de hoofdmap van de map Technical Workflows opgeslagen. Het gebruikte label is **&quot;Controle&quot;**.

Het volgende schema toont de opeenvolging van activiteiten:

![](assets/uc_monitoring_workflow_overview.png)

Deze workflow bestaat uit:

* een activiteit **&quot;Start&quot;** .
* een activiteit **&quot;JavaScript code&quot;** verantwoordelijk voor het analyseren van de omslag van bedrijfswerkschema&#39;s.
* een **&quot;Test&quot;** activiteit om een levering naar de supervisor te verzenden of het werkschema opnieuw te beginnen.
* a **&quot;Leveringsactiviteit&quot;** verantwoordelijk voor berichtlay-out.
* een activiteit **&quot;wacht&quot;** die de lood tijden tussen werkschemariteraties controleert.

## Stap 2: JavaScript schrijven {#step-2--writing-the-javascript}

Het eerste deel van de JavaScript-code valt samen met een **query (queryDef)** waarmee u de workflows kunt identificeren met de status &quot;pause&quot; (@state == 13), &quot;error&quot; (@failed == 1) of &quot;stopped&quot; (@state == 20).

De **interne naam** van de te controleren werkschemamap wordt gegeven in de volgende voorwaarde:

```
<condition boolOperator="AND" expr="[folder/@name] = 'Folder20'" internalId="1"/>
```

```
var strError = "";
var strPaused = "";
var strStop = "";

var queryWkfError = xtk.queryDef.create(
  <queryDef schema="xtk:workflow" operation="select">
    <select>
      <node expr="@internalName"/>
      <node expr="@state"/>
      <node expr="@label"/>
      <node expr="@failed"/>
      <node expr="@state"/>   
    </select>
    <where id="12837805386">
      <condition boolOperator="AND" expr="[folder/@name] = 'Folder20'" internalId="1"/>
        <condition boolOperator="AND" internalId="2">
          <condition boolOperator="OR" expr="@state = 20" internalId="3"/>
          <condition expr="@state = 13" internalId="4"/>
        </condition>  
    </where>
  </queryDef>
);
var ndWkfError = queryWkfError.ExecuteQuery(); 
```

In het tweede deel van de JavaScript-code kunt u voor elke workflow **een bericht** weergeven op basis van de status die tijdens de query is hersteld.

>[!NOTE]
>
>De gemaakte tekenreeksen moeten worden geladen in de gebeurtenisvariabelen van de workflow.

```
for each ( var wkf in ndWkfError.workflow ) 
{
  if ( wkf.@state == 13 )  // Status 13 = paused
  {
    if ( wkf.@failed == 1 )
      strError += "<li>Workflow '" + wkf.@internalName + "' with the label '" + wkf.@label + "'</li>";
    else
      strPaused += "<li>Workflow '" + wkf.@internalName + "' with the label '" + wkf.@label + "'</li>";
  }
  
  if ( wkf.@state == 20 )  // Status 20 = stop
    strStop += "<li>Workflow '" + wkf.@internalName + "' with the label '" + wkf.@label + "'</li>";
}

vars.strWorkflowError = strError;
vars.strWorkflowPaused = strPaused;
vars.strWorkflowStop = strStop;
```

## Stap 3: De &#39;Test&#39;-activiteit maken {#step-3--creating-the--test--activity}

De &quot;Test&quot;activiteit laat u bepalen of een levering moet worden verzonden of of het controlewerkschema een andere die cyclus moet in werking stellen op de &quot;Wacht&quot;activiteit wordt gebaseerd.

Een levering wordt verzonden naar de supervisor **als minstens één van de drie gebeurtenisvariabelen &quot;vars.strWorkflowError&quot;, &quot;vars.strWorkflowPaused&quot;, of &quot;vars.strWorkflowStop&quot; niet-void is.**

![](assets/uc_monitoring_workflow_test.png)

De activiteit &quot;wacht&quot;kan worden gevormd om het controlewerkschema met regelmatige intervallen opnieuw te beginnen. Voor dit gebruik wordt **de wachttijd ingesteld op één uur**.

![](assets/uc_monitoring_workflow_attente.png)

## Stap 4: De levering voorbereiden {#step-4--preparing-the-delivery}

De activiteit van de &quot;Levering&quot;is gebaseerd op een **leveringsmalplaatje** dat in de **Middelen > Malplaatjes > de knoop van de malplaatjes** van de Levering wordt opgeslagen.

Deze sjabloon moet het volgende bevatten:

* **het e-mailadres van de toezichthouder**.
* **HTML-inhoud** voor het invoegen van gepersonaliseerde tekst.

   ![](assets/uc_monitoring_workflow_variables_diffusion.png)

   De drie gedeclareerde variabelen (WF_Stop, WF_Paused, WF_Error) komen overeen met de drie workflowgebeurtenisvariabelen.

   Deze variabelen moeten worden gedeclareerd op het tabblad **Variabelen** van de eigenschappen van de leveringssjabloon.

   Als u **de inhoud van de workflowgebeurtenisvariabelen** wilt herstellen, moet u de variabelen declareren die specifiek zijn voor de levering en die worden geïnitialiseerd met waarden die door de JavaScript-code worden geretourneerd.

   De leveringssjabloon heeft de volgende inhoud:

   ![](assets/uc_monitoring_workflow_model_diffusion.png)

Zodra het malplaatje is gecreeerd en goedgekeurd, moet u de activiteit van de **Levering** vormen aan:

* Koppel de activiteit van de &quot;Levering&quot;aan eerder gecreeerd leveringsmalplaatje.
* Koppel de de gebeurtenisvariabelen van het werkschema aan die specifiek voor het leveringsmalplaatje.

Dubbelklik op de activiteit **Levering** en selecteer de volgende opties:

* Aflevering: Selecteer **Nieuw, gecreeerd van een malplaatje**, en selecteer eerder gecreeerd leveringsmalplaatje.
* Selecteer voor de velden **Ontvangers en Inhoud** de optie **Opgegeven in de aflevering**.
* Uit te voeren handeling: Selecteer **Voorbereiden en starten**.
* Schakel de optie **Procesfouten** uit.

   ![](assets/uc_monitoring_workflow_optionmodel.png)

* Ga naar het tabblad **Script** van de activiteit **Aflevering** en voeg drie variabelen van het type **tekenreeks** toe via het menu van het veld voor aanpassen.

   ![](assets/uc_monitoring_workflow_selectlinkvariables.png)

   ![](assets/uc_monitoring_workflow_linkvariables.png)

   De drie gedeclareerde variabelen zijn:

   ```
   delivery.variables._var[0].stringValue = vars.strWorkflowError;
   delivery.variables._var[1].stringValue = vars.strWorkflowPaused;
   delivery.variables._var[2].stringValue = vars.strWorkflowStop; 
   ```

Zodra deze controlewerkstroom wordt gelanceerd, verzendt het het volgende overzicht naar de ontvanger:

![](assets/uc_monitoring_workflow_mailfinal.png)

