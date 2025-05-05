---
product: campaign
title: Workflows controleren
description: Leer hoe u toezicht houdt op de workflows voor campagnes
feature: Workflows
hide: true
hidefromtoc: true
exl-id: ca6d4bf4-7b3a-4d36-9fc3-0b83531d0132
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '650'
ht-degree: 0%

---

# Hoofdlettergebruik: toezicht op uw workflows{#supervising-workflows}



In dit geval wordt het maken van een workflow beschreven waarmee u de status kunt controleren van een set werkstromen die worden gepauzeerd, gestopt of met fouten.

Het doel van de verordening is:

* Gebruik een werkschema om een groep bedrijfswerkschema&#39;s te controleren.
* Verzend een bericht naar een supervisor via een &quot;levering&quot;activiteit.

Als u de status van een set workflows wilt controleren, moet u de volgende stappen uitvoeren:

1. Maak de controleworkflow.
1. Schrijf de JavaScript om te bepalen of workflows worden gepauzeerd, gestopt of met fouten.
1. Maak de **[!UICONTROL Test]** -activiteit.
1. Bereid het leveringsmalplaatje voor.

>[!NOTE]
>
>Naast het werkschema, staat de Heatmap van het Werkschema van de Campagne **&#x200B;**&#x200B;u toe om in details de werkschema&#39;s te analyseren die momenteel lopen. Voor meer op dit, verwijs naar de [ specifieke sectie ](heatmap.md).
>
>Voor meer op hoe te **om de uitvoering van uw werkschema&#39;s** te controleren, verwijs naar [ deze sectie ](monitoring-workflow-execution.md).

## Stap 1: De controleworkflow maken {#step-1--creating-the-monitoring-workflow}

De werkschemamap die wij gaan controleren is **&quot;CustomWorkflows&quot;** omslag die in het **Beleid > Productie > Technische werkschema&#39;s** knoop wordt opgeslagen. Deze map bevat een set bedrijfsworkflows.

Het **werkschema van de Controle** wordt opgeslagen bij de wortel van de omslag van Technische Werkschema&#39;s. Het gebruikte etiket is **&quot;Controle&quot;**.

Het volgende schema toont de opeenvolging van activiteiten:

![](assets/uc_monitoring_workflow_overview.png)

Deze workflow bestaat uit:

* a **&quot;Begin&quot;** activiteit.
* a **&quot;JavaScript code&quot;** activiteit verantwoordelijk voor het analyseren van de omslag van bedrijfswerkschema&#39;s.
* a **&quot;Test&quot;** activiteit om een levering naar de supervisor te verzenden of het werkschema opnieuw te beginnen.
* a **&quot;Levering&quot;** activiteit verantwoordelijk voor berichtlay-out.
* a **&quot;wacht&quot;** activiteit die de loodtijden tussen werkschemariteraties controleert.

## Stap 2: De JavaScript schrijven {#step-2--writing-the-javascript}

Het eerste deel van de code van JavaScript valt met a **vraag (queryDef)** samen die u de werkschema&#39;s met een &quot;pauze&quot;laat identificeren (@state == 13), &quot;fout&quot; (@failed == 1) of &quot;tegengehouden&quot; (@state == 20) status.

De **interne naam** van de werkschemamap aan controle wordt gegeven in de volgende voorwaarde:

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

Het tweede deel van de code van JavaScript laat u **een bericht voor elk werkschema** tonen dat op de status wordt gebaseerd die tijdens de vraag wordt teruggekregen.

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

## Stap 3: De &#39;test&#39;-activiteit maken {#step-3--creating-the--test--activity}

De &quot;Test&quot;activiteit laat u bepalen of een levering moet worden verzonden of of het controlewerkschema een andere die cyclus moet in werking stellen op de &quot;Wacht&quot;activiteit wordt gebaseerd.

Een levering wordt verzonden naar de supervisor **als minstens één van de drie gebeurtenisvariabelen &quot;vars.strWorkflowError&quot;, &quot;vars.strWorkflowPaused&quot;, of &quot;vars.strWorkflowStop&quot;niet-void is.**

![](assets/uc_monitoring_workflow_test.png)

De activiteit &quot;wacht&quot;kan worden gevormd om het controlewerkschema met regelmatige intervallen opnieuw te beginnen. Voor dit gebruiksgeval, **de wachttijdtijd wordt geplaatst aan één uur**.

![](assets/uc_monitoring_workflow_attente.png)

## Stap 4: De levering voorbereiden {#step-4--preparing-the-delivery}

De &quot;activiteit van de Levering&quot;is gebaseerd op a **leveringsmalplaatje** opgeslagen in de **Middelen > Malplaatjes > de malplaatjes van de Levering** knoop.

Deze sjabloon moet het volgende bevatten:

* **het e-mailadres van de supervisor**.
* **inhoud van HTML** voor het opnemen van gepersonaliseerde tekst.

  ![](assets/uc_monitoring_workflow_variables_diffusion.png)

  De drie gedeclareerde variabelen (WF_Stop, WF_Paused, WF_Error) komen overeen met de drie workflowgebeurtenisvariabelen.

  Deze variabelen moeten in het **lusje van Variabelen** van de eigenschappen van het leveringsmalplaatje worden verklaard.

  Om **de inhoud van de variabelen van de werkschemagebeurtenis** terug te krijgen, moet u de variabelen verklaren specifiek voor de levering die met waarden zullen worden geïnitialiseerd die door de code van JavaScript zijn teruggekeerd.

  De leveringssjabloon heeft de volgende inhoud:

  ![](assets/uc_monitoring_workflow_model_diffusion.png)

Zodra het malplaatje is gecreeerd en goedgekeurd, moet u de **activiteit van de Levering** vormen aan:

* Koppel de activiteit van de &quot;Levering&quot;aan eerder gecreeerd leveringsmalplaatje.
* Koppel de de gebeurtenisvariabelen van het werkschema aan die specifiek voor het leveringsmalplaatje.

Dubbelklik de **activiteit van de Levering** en selecteer de volgende opties:

* Levering: selecteer **Nieuw, die van een malplaatje** wordt gecreeerd, en selecteer het eerder gecreeerde leveringsmalplaatje.
* Voor de **Ontvangers en de gebieden van de Inhoud**, uitgezocht **die in de levering** wordt gespecificeerd.
* Uit te voeren actie: selecteer **voorbereidingen treffen en beginnen**.
* Uncheck de **optie van de Fouten van het Proces**.

  ![](assets/uc_monitoring_workflow_optionmodel.png)

* Ga naar het **lusje van het Manuscript** van de **Levering** activiteit, voeg drie **karakterkoord** typevariabelen via het menu van het verpersoonlijkingsgebied toe.

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
