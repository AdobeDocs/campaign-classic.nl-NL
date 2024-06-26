---
product: campaign
title: "Gebruik gevallen: webformulieren"
description: "Gebruik gevallen: webformulieren"
badge-v8: label="Ook van toepassing op v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
feature: Web Forms
exl-id: 7aa4646d-1325-47c2-b553-6fe375c48973
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '970'
ht-degree: 0%

---

# Gebruiksscenario: webformulieren{#use-cases-web-forms}



## Abonnementsformulieren met dubbele aanmelding maken {#create-a-subscription--form-with-double-opt-in}

Wanneer u de informatiediensten aanbiedt, moeten de ontvangers intekenen om alle verbonden mededelingen te ontvangen. Om onjuiste mededelingen te vermijden en ervoor te zorgen de ontvanger opzettelijk wordt ingetekend, adviseren wij het verzenden van een verzoek van de abonnementsbevestiging om tot een dubbele opt-in te leiden. Het abonnement wordt pas van kracht nadat de gebruiker op de koppeling klikt die in het bevestigingsbericht is opgenomen.

Dit voorbeeld is gebaseerd op het volgende scenario:

1. Een abonnementsformulier voor nieuwsbrieven maken op een website die een selectievakje bevat voor het abonneren op een tijdelijke service. Met deze service kunt u berichten voor abonnementsbevestiging verzenden.
1. Het creëren van de levering van de abonnementsbevestiging met een leveringsmalplaatje verbonden aan de vorm van het Web. Het bevat de bevestigingskoppeling die het formulier oproept voor een abonnement op een nieuwsbrief en een goedkeuringsbericht voor een abonnement weergeeft.

### Stap 1 - Informatiediensten maken {#step-1---creating-information-services}

1. Maak de service voor abonnementen op nieuwsbrieven die aan uw ontvangers moet worden aangeboden. Voor meer informatie over het maken van een nieuwsbrief raadpleegt u [deze sectie](../../delivery/using/about-services-and-subscriptions.md).

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_1.png)

1. Maak een tweede informatieservice, een tijdelijke service die is gekoppeld aan een leveringssjabloon voor het verzenden van abonnementsbevestigingsberichten.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_1c.png)

### Stap 2 - Bevestigingsberichten maken {#step-2---creating-confirmation-messages}

De berichten van de bevestiging worden verzonden via een specifiek leveringsmalplaatje dat op het tijdelijke de dienstniveau van verwijzingen wordt voorzien.

1. In de **[!UICONTROL Explorer]** , selecteert u **[!UICONTROL Resources > Templates > Delivery templates]**.
1. Maak een leveringssjabloon voor het verzenden van de bevestigingsberichten voor abonnementen.
1. Klik op de knop **[!UICONTROL To]** in de **[!UICONTROL Email parameters]** om de leveringsmalplaatje met de het doelafbeelding van Abonnementen in plaats van Ontvangers te associëren.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_1d.png)

1. Aangezien de ontvangers van deze levering hun goedkeuring niet hebben bevestigd, zijn zij nog op de lijst van gewezen personen van het gegevensbestand. Voor hen om deze mededeling te ontvangen, moet u leveringen toelaten die op dit malplaatje aan doelontvangers op lijst van gewezen personen worden gebaseerd.

   Om dit te doen, klik **[!UICONTROL Exclusions]** tab.

1. Klik op de knop **[!UICONTROL Edit...]** koppeling en schakel de **[!UICONTROL Exclude recipients who no longer want to be contacted]** -optie.

   <!-- ![](assets/s_ncs_admin_survey_double-opt-in_sample_4d.png)-->

   >[!IMPORTANT]
   >
   >Deze optie kan alleen in dit type context worden uitgeschakeld.

1. Pas de levering aan en voeg de bevestigingskoppeling in de inhoud van het bericht in. Met deze koppeling hebt u toegang tot het webformulier om de bevestiging van uw abonnement op te nemen.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_1b.png)

1. Koppel uw URL met de DCE aan het webformulier. Aangezien het formulier Web nog niet is gemaakt, vervangt u de waarde zodra u het maakt.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_3.png)

1. Tot slot verbind dit malplaatje met de tijdelijke dienst eerder gecreeerd.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_3c.png)

### Stap 3 - Het abonnementsformulier maken {#step-3---creating-the-subscription-form}

In het webformulier zijn zowel een abonnement als een bevestiging van een abonnement voor de ontvanger ingeschakeld.

De webformulierworkflow omvat de volgende activiteiten:

![](assets/s_ncs_admin_survey_double-opt-in_sample_4c.png)

Hiervoor voert u de volgende stappen uit:

1. Een webformulier maken en de sjabloon kiezen **[!UICONTROL Newsletter subscription (subNewsletter)]**.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_5a.png)

1. In de **[!UICONTROL Edit]** tab, moeten we de bestaande workflow configureren omdat we een bevestigingsbericht willen toevoegen aan de ontvangers die zich willen abonneren.

   Dubbelklik hiertoe op de knop **[!UICONTROL Preloading]** en configureert u deze als volgt.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_5b.png)

   Dit betekent dat als de gebruiker dit formulier opent via de koppeling in het bevestigingsbericht, de profielgegevens worden geladen. Als zij tot het formulier van het Web via een pagina van de website toegang hebben, zal geen informatie worden geladen.

1. Voeg een **[!UICONTROL Test]** activiteit aan uw werkschema.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_6e.png)

   De **[!UICONTROL Test]** activiteit kan de ontvanger e-mail betreffen. In dit geval, vorm het als volgt:

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_6d.png)

1. Twee toevoegen **[!UICONTROL Script]** activiteiten aan uw werkstroom.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_6f.png)

   De eerste **[!UICONTROL Script]** activiteit zal ontvangers op lijst van gewezen personen toevoegen tot zij hun abonnement op de nieuwsbrief bevestigen . De inhoud ervan moet als volgt zijn:

   ```
   ctx.recipient.@blackList=1
   ```

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_6bbis.png)

   De tweede **[!UICONTROL Script]** de activiteit staat toe dat leveringen naar de gebruikers worden verzonden en deze aan de nieuwsbrief abonneren . Met de laatste twee regels van het script kunt u de ontvangers van de tijdelijke map overbrengen naar een andere map en worden ze afgestemd op bestaande profielen zodra ze het abonnement hebben bevestigd.

   ```
   ctx.recipient.@blackList=0
   nms.subscription.Subscribe("INTERNAL_NAME_OF_THE_NEWSLETTER", ctx.recipient, false)
   ctx.recipient.folder = <folder name="nmsRootRecipient"/>
   nms.subscription.Unsubscribe("TEMP", ctx.recipient)
   ```

   >[!NOTE]
   >
   >De **[!UICONTROL Temp]** partitie kan ook regelmatig worden gewist met behulp van een workflow.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_6b.png)

1. Dubbelklik op de knop **[!UICONTROL Subscription]** activiteit om het abonnementsformulier aan te passen en een selectievakje te koppelen aan de eerder gemaakte tijdelijke service.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_5c.png)

1. Vorm **[!UICONTROL Storage]** activiteit om de informatie te bewaren ingegaan op de vormpagina.

   Deze activiteit laat u ontvankelijke profielen in een specifieke tijdelijke omslag tot stand brengen om hen los van de profielen in het gegevensbestand te plaatsen, waarnaar de mededelingen kunnen worden verzonden.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_5g.png)

   >[!NOTE]
   >
   >U mag geen afstemmingsopties definiëren.

1. Twee toevoegen **[!UICONTROL End]** activiteiten om een bericht voor de gebruiker te tonen.

   De tweede **[!UICONTROL End]** verschijnt het bevestigingsbericht zodra het abonnement is voltooid.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_5h.png)

1. Zodra de vorm van het Web wordt gecreeerd en gevormd, kunt u het in het leveringsmalplaatje nu van verwijzingen voorzien om bevestigingsberichten te verzenden.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_7b.png)

### Stap 4 - Het formulier publiceren en testen {#step-4---publishing-and-testing-the-form}

U kunt het formulier nu publiceren om het toegankelijk te maken voor gebruikers.

![](assets/s_ncs_admin_survey_double-opt-in_sample_8b.png)

Het abonnement op de nieuwsbrief omvat de volgende stappen:

1. De gebruiker van de website meldt zich aan bij de abonnementspagina en keurt het formulier goed.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_8c.png)

   Zij worden via een bericht in hun browser op de hoogte gesteld dat met hun verzoek rekening is gehouden.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_8d.png)

   De gebruiker wordt toegevoegd aan de Adobe Campaign-database in het dialoogvenster **[!UICONTROL Temp]** en het bijbehorende profiel is in de lijst van gewezen personen totdat ze hun abonnement via e-mail bevestigen.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_8f.png)

1. Een bevestigingsbericht met een koppeling voor het goedkeuren van hun abonnement wordt naar hen verzonden.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_8e.png)

1. Wanneer ze op deze koppeling klikken, wordt de goedkeuringspagina in hun browser weergegeven.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_8.png)

   In Adobe Campaign wordt het gebruikersprofiel bijgewerkt:

   * zij niet langer in de lijst van gewezen personen zijn,
   * zij zijn geabonneerd op de informatiedienst .

     ![](assets/s_ncs_admin_survey_double-opt-in_sample_9.png)

## Verschillende opties weergeven, afhankelijk van de geselecteerde waarden {#displaying-different-options-depending-on-the-selected-values}

In het volgende voorbeeld wordt de gebruiker gevraagd een voertuigtype te selecteren. U kunt de beschikbare voertuigcategorieën weergeven op basis van het geselecteerde type. Dit betekent dat de items die in de rechterkolom worden weergegeven, afhankelijk zijn van de keuze van de gebruiker:

![](assets/s_ncs_admin_survey_condition_sample0.png)

* Wanneer de gebruiker &#39;Private Vehicle&#39; selecteert, wordt de keuze tussen &#39;Compact&#39; en &#39;Minivan&#39; aangeboden.

  ![](assets/s_ncs_admin_survey_condition_sample2.png)

* Wanneer de gebruiker &#39;bedrijfsvoertuig&#39; selecteert, wordt een selectie weergegeven in een vervolgkeuzelijst:

  ![](assets/s_ncs_admin_survey_condition_sample1.png)

In dit voorbeeld wordt het voertuigtype niet in de database opgeslagen. De vervolgkeuzelijst is als volgt geconfigureerd:

![](assets/s_ncs_admin_survey_condition_config1.png)

Deze informatie wordt opgeslagen in een lokale variabele.

De voorwaardelijke vertoning van de rechterkolom wordt gevormd in de containers:

![](assets/s_ncs_admin_survey_condition_config1bis.png)

* Voorwaardelijke zichtbaarheid van velden voor een particulier voertuig:

  ![](assets/s_ncs_admin_survey_condition_config2.png)

* Voorwaardelijke zichtbaarheid van velden voor bedrijfsvoertuigen:

  ![](assets/s_ncs_admin_survey_condition_config3.png)
