---
title: Een samenwerkingscampagne maken
seo-title: Een samenwerkingscampagne maken
description: Een samenwerkingscampagne maken
seo-description: null
page-status-flag: never-activated
uuid: 13d8ff65-1480-422a-85b6-40b553a3c151
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: distributed-marketing
discoiquuid: 01d8be92-7312-4386-b5f5-651af31308f7
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: d30de91002862b664249c5a704b7c0f521dd30f2

---


# Een samenwerkingscampagne maken{#creating-a-collaborative-campaign-intro}

De centrale entiteit creeert samenwerkingscampagnes van de **Verdeelde de campagnemalplaatjes van de Marketing** . Zie [deze pagina](../../campaign/using/about-distributed-marketing.md#collaborative-campaign).

## Een samenwerkingscampagne maken {#creating-a-collaborative-campaign}

Als u een samenwerkingscampagne wilt configureren, klikt u op het **[!UICONTROL Campaign management > Campaigns]** knooppunt en vervolgens op het **[!UICONTROL New]** pictogram.

>[!NOTE]
>
>Naast **[!UICONTROL collaborative campaigns (by campaign)]**, kunnen deze campagnes via een Webinterface worden gevormd en worden uitgevoerd.

Het configuratieproces voor een samenwerkingscampagnecadatabase is gelijkaardig aan dat van een lokaal campagnemalplaatje. De specificaties van de verschillende soorten samenwerkingscampagnes worden hieronder beschreven.

### Op formulier {#by-form}

Als u een samenwerkingscampagne wilt maken (op formulier), moet u de **[!UICONTROL Collaborative campaign (by form)]** sjabloon selecteren.

![](assets/mkg_dist_mutual_op_form2.png)

Klik op het **[!UICONTROL Edit]** tabblad op de **[!UICONTROL Advanced campaign settings...]** koppeling voor toegang tot het tabblad **Distributed Marketing** .

Selecteer de **webinterface Op formulier** . Met dit type interface kunt u verpersoonlijkingsvelden maken die door lokale entiteiten worden gebruikt wanneer ze een campagne bestellen. Zie Een lokale campagne [maken (op formulier)](../../campaign/using/examples.md#creating-a-local-campaign--by-form-).

Sla uw campagne op. U kunt het nu gebruiken vanuit de **Campagnepakketweergave** in het **Campagneuniversum** door op de **[!UICONTROL Create]** knop te klikken.

In de **[!UICONTROL Campaign Package]** weergave kunt u lokale campagnemasjablonen (out-of-the-box of gedupliceerd) gebruiken, evenals referentiecampagnes voor samenwerkingscampagnes, met als doel campagnes voor uw verschillende organisatorische entiteiten te maken.

![](assets/mkg_dist_mutual_op_form1b.png)

### Op campagne {#by-campaign}

Als u een samenwerkingscampagne wilt maken (per campagne), moet u de **[!UICONTROL Collaborative campaign (by campaign) (opCollaborativeByCampaign)]** sjabloon selecteren.

![](assets/mkg_dist_mutual_op_by_op2.png)

Wanneer het opdracht geven tot de campagne, kan de lokale entiteit de criteria voltooien die door de centrale entiteit vooraf worden bepaald, en de campagne evalueren alvorens het tot opdracht te geven.

Zodra een orde voor een **Samenwerken campagne (door campagne)** door de centrale entiteit wordt goedgekeurd, wordt een kindcampagne gecreeerd voor de lokale entiteit. Zodra zij beschikbaar zijn, kan de lokale entiteit dan wijzigen:

* de campagneworkflow;
* typologieregels;
* en personalisatievelden.

De lokale entiteit voert de onderliggende campagne uit. De centrale entiteit voert de bovenliggende campagne uit.

De centrale entiteit kan alle kindcampagnes bekijken verbonden aan een **Collaborative campagne (door campagne)** van dit dashboard (via de **[!UICONTROL List of associated campaigns]** verbinding).

![](assets/mkg_dist_mutual_op_by_op.png)

### Op doelgoedkeuring {#by-target-approval}

Als u een samenwerkingscampagne wilt maken (door goedkeuring als doel), moet de **[!UICONTROL Collaborative campaign (by target approval)]** sjabloon zijn geselecteerd.

![](assets/mkg_dist_mutual_op_by_valid.png)

>[!NOTE]
>
>In deze modus hoeft de centrale entiteit de lokale entiteiten niet op te geven.

De campagneworkflow moet activiteiten van het type **Lokale goedkeuring** integreren. De activiteitsparameters zijn als volgt:

* **[!UICONTROL Action to perform]** : Doelgoedkeuringsmelding.
* **[!UICONTROL Distribution context]** : Expliciet.
* **[!UICONTROL Data distribution]** : Distributie van lokale entiteiten.

**De verdeling** van het type gegevens van de lokale entiteitdistributie moet worden gecreeerd. Met de sjabloon voor gegevensdistributie kunt u het aantal records uit een lijst met groeperingswaarden beperken. Klik **[!UICONTROL Resources > Campaign management > Data distribution]** in op het **[!UICONTROL New]** pictogram om een nieuwe afbeelding te maken **[!UICONTROL Data distribution]**. Raadpleeg de handleiding voor [workflows](../../workflow/using/using-the-local-approval-activity.md#step-1--creating-the-data-distribution-template-) voor meer informatie over gegevensdistributie.

![](assets/mkg_dist_data_distribution.png)

Selecteer de **doeldimensie** en de **[!UICONTROL Distribution field]**. Selecteer voor de **[!UICONTROL Assignment type]** optie **Lokale entiteit**.

Voeg op het **[!UICONTROL Distribution]** tabblad een veld toe voor elke lokale entiteit en geef de waarde op.

![](assets/mkg_dist_data_distribution2.png)

U kunt een tweede goedkeuring **van het** Doel na de het type van **Levering** activiteit toevoegen om een rapport over het te vormen.

In het bericht van de campagneverwezenlijking, ontvangt de lokale entiteit een contactlijst die door de centrale entiteitparameters vooraf is bepaald.

![](assets/mkg_dist_mutual_op_by_valid1.png)

De lokale entiteit kan bepaalde contacten schrappen die op de campagneinhoud worden gebaseerd.

![](assets/mkg_dist_mutual_op_by_valid2.png)

### Eenvoudig {#simple}

Als u een eenvoudige samenwerkingscampagne wilt maken, moet u de **[!UICONTROL Collaborative campaign (simple)]** sjabloon selecteren.

## Een gezamenlijk campagnemakket maken {#creating-a-collaborative-campaign-package}

Om een campagne ter beschikking te stellen van lokale entiteiten moet de centrale entiteit een campagnepakket maken.

Voer de volgende stappen uit:

1. Klik in de **[!UICONTROL Navigation]** sectie op de pagina **Campagnes** op de **[!UICONTROL Campaign packages]** koppeling.
1. Klik op de **[!UICONTROL Create]** knop.
1. In het gedeelte boven in het venster kunt u de **[!UICONTROL New collaborative package (mutualizedEmpty)]** sjabloon selecteren.
1. Selecteer de referentiecampagne.
1. Geef het label, de map en het uitvoeringsschema voor het campagnemakket op.

### Datums {#dates}

De begin- en einddatum bepalen de zichtbaarheidsperiode van de campagne in de lijst met campagnepakketten.

Voor **samenwerkingscampagnes** moet de centrale entiteit de registratie- en personalisatietermijn specificeren.

>[!NOTE]
>
>De **[!UICONTROL Personalization deadline]** methode stelt de centrale entiteit in staat een deadline te kiezen waarbinnen de lokale entiteiten de documenten (spreadsheets, afbeeldingen) moeten hebben afgeleverd die moeten worden gebruikt om de campagne te configureren. Dit is geen verplichte optie. Zijdelingse datums hebben geen invloed op de uitvoering van de campagne.

![](assets/s_advuser_mkg_dist_create_mutual_entry.png)

### Publiek {#audience}

De centrale entiteit moet de betrokken lokale entiteiten per campagne specificeren zodra de samenwerkingscampagne is opgezet.

![](assets/s_advuser_mkg_dist_create_mutual_entry2.png)

>[!CAUTION]
>
>**[!UICONTROL Simple, by form and by campaign collaborative campaign kits]** niet kan worden goedgekeurd tenzij de betrokken lokale entiteiten zijn gespecificeerd.

### Goedkeuringsmodi {#approval-modes}

Voor **samenwerkingscampagnes** kunt u de goedkeuringsmodus voor bestellingen opgeven.

![](assets/mkg_dist_edit_kit1.png)

In de handmatige modus moet de lokale entiteit zich abonneren op de campagne om deel te kunnen nemen.

In de automatische modus wordt de lokale entiteit vooraf geabonneerd op de campagne. Het kan het campagneabonnement annuleren of zijn parameters wijzigen zonder goedkeuring van de centrale entiteit te vereisen.

![](assets/mkg_dist_edit_kit2.png)

### Meldingen {#notifications}

Configuratie voor meldingen is identiek aan meldingen voor een lokale entiteit. Zie [deze sectie](../../campaign/using/creating-a-local-campaign.md#notifications).

## Een campagne bestellen {#ordering-a-campaign}

Wanneer een samenwerkingscampagne aan de lijst van campagnepakketten wordt toegevoegd, worden de lokale entiteiten die tot het publiek behoren dat door de centrale entiteit wordt bepaald op de hoogte gebracht (de **samenwerkingscampagnes (door doelgoedkeuring)** hebben geen vooraf bepaald publiek). Het verzonden bericht bevat een koppeling waarmee u zich voor de campagne kunt registreren, zoals hieronder wordt getoond:

![](assets/mkg_dist_mutual_op_notification.png)

Met dit bericht kunnen lokale entiteiten ook de beschrijving bekijken die is ingevoerd door de centrale operator die het pakket heeft gemaakt, en documenten die aan de campagne zijn gekoppeld. Deze horen niet bij de campagne zelf, hoewel ze aanvullende informatie hierover verschaffen.

Zodra lokale operatoren zich via een webinterface hebben aangemeld, kunnen ze gepersonaliseerde informatie invoeren voor de samenwerkingscampagne die ze willen bestellen:

![](assets/mkg_dist_mutual_op_command.png)

Nadat een lokale entiteit de registratie heeft voltooid, worden centrale entiteiten via e-mail op de hoogte gebracht om hun bestelling goed te keuren.

![](assets/mkg_dist_mutual_op_valid_command.png)

Raadpleeg de sectie [Goedkeuringsproces](../../campaign/using/creating-a-local-campaign.md#approval-process) voor meer informatie.

## Een bestelling goedkeuren {#approving-an-order}

Het proces voor het goedkeuren van een collectieve campagnepakketorde is het zelfde als wanneer het doen van dit voor een lokale campagne. Zie [deze sectie](../../campaign/using/creating-a-local-campaign.md#approving-an-order).
