---
solution: Campaign Classic
product: campaign
title: Een collaboratieve campagne maken
description: Een collaboratieve campagne maken
audience: campaign
content-type: reference
topic-tags: distributed-marketing
translation-type: tm+mt
source-git-commit: c625b4109e2cb47446331cd009ff9827c8267c93
workflow-type: tm+mt
source-wordcount: '912'
ht-degree: 3%

---


# Een collaboratieve campagne maken{#creating-a-collaborative-campaign-intro}

De centrale entiteit creeert samenwerkingscampagnes van **Distributed Marketing** campagnemalplaatjes. Zie [deze pagina](../../campaign/using/about-distributed-marketing.md#collaborative-campaign).

## Een collaboratieve campagne maken {#creating-a-collaborative-campaign}

Als u een samenwerkingscampagne wilt configureren, klikt u op het knooppunt **[!UICONTROL Campaign management > Campaigns]** en vervolgens op het pictogram **[!UICONTROL New]**.

>[!NOTE]
>
>Naast **[!UICONTROL collaborative campaigns (by campaign)]**, kunnen deze campagnes via een Webinterface worden gevormd en worden uitgevoerd.

Het configuratieproces voor een samenwerkingscampagnecadatabase is gelijkaardig aan dat van een lokaal campagnemalplaatje. De specificaties van de verschillende soorten samenwerkingscampagnes worden hieronder beschreven.

### Op formulier {#by-form}

Als u een samenwerkingscampagne wilt maken (op formulier), moet de sjabloon **[!UICONTROL Collaborative campaign (by form)]** zijn geselecteerd.

![](assets/mkg_dist_mutual_op_form2.png)

Klik op het tabblad **[!UICONTROL Edit]** op de koppeling **[!UICONTROL Advanced campaign settings...]** om het tabblad **Distributed Marketing** te openen.

Selecteer de **Op vorm** Webinterface. Met dit type interface kunt u verpersoonlijkingsvelden maken die door lokale entiteiten worden gebruikt wanneer ze een campagne bestellen. Zie [Een lokale campagne maken (op formulier)](../../campaign/using/examples.md#creating-a-local-campaign--by-form-).

Sla uw campagne op. U kunt het van **Campagnepakketten** nu gebruiken mening in **Campagne** universum, door **[!UICONTROL Create]** knoop te klikken.

In de weergave **[!UICONTROL Campaign Package]** kunt u lokale campagnemalplaatjes (out-of-the-box of gedupliceerd) gebruiken, evenals referentiecampagnes voor samenwerkingscampagnes, met als doel campagnes voor uw verschillende organisatorische entiteiten te maken.

![](assets/mkg_dist_mutual_op_form1b.png)

### Op campagne {#by-campaign}

Om een samenwerkingscampagne (door campagne) tot stand te brengen, moet **[!UICONTROL Collaborative campaign (by campaign) (opCollaborativeByCampaign)]** malplaatje worden geselecteerd.

![](assets/mkg_dist_mutual_op_by_op2.png)

Wanneer het opdracht geven tot de campagne, kan de lokale entiteit de criteria voltooien die door de centrale entiteit vooraf worden bepaald, en de campagne evalueren alvorens het tot opdracht te geven.

Zodra een orde voor een **Samenwerken campagne (door campagne)** door de centrale entiteit wordt goedgekeurd, wordt een kindcampagne gecreeerd voor de lokale entiteit. Zodra zij beschikbaar zijn, kan de lokale entiteit dan wijzigen:

* de campagneworkflow;
* typologieregels;
* en personalisatievelden.

De lokale entiteit voert de onderliggende campagne uit. De centrale entiteit voert de bovenliggende campagne uit.

De centrale entiteit kan alle kindcampagnes bekijken verbonden aan een **Samenwerken campagne (door campagne)** van dit dashboard (via **[!UICONTROL List of associated campaigns]** verbinding).

![](assets/mkg_dist_mutual_op_by_op.png)

### Op doelgoedkeuring {#by-target-approval}

Om een samenwerkingscampagne (door doelgoedkeuring) tot stand te brengen, moet **[!UICONTROL Collaborative campaign (by target approval)]** malplaatje worden geselecteerd.

![](assets/mkg_dist_mutual_op_by_valid.png)

>[!NOTE]
>
>In deze modus hoeft de centrale entiteit de lokale entiteiten niet op te geven.

De campagnewerkstroom moet **Lokale goedkeuring** typeactiviteit integreren. De activiteitsparameters zijn als volgt:

* **[!UICONTROL Action to perform]** : Doelgoedkeuringsmelding.
* **[!UICONTROL Distribution context]** : Expliciet.
* **[!UICONTROL Data distribution]** : Distributie van lokale entiteiten.

**De lokale entiteit** distributi de verspreiding van contacttypegegevens moet worden gecreeerd. Met de sjabloon voor gegevensdistributie kunt u het aantal records uit een lijst met groeperingswaarden beperken. Klik in **[!UICONTROL Resources > Campaign management > Data distribution]** op het pictogram **[!UICONTROL New]** om een nieuwe **[!UICONTROL Data distribution]** te maken. Raadpleeg de handleiding [Workflows](../../workflow/using/using-the-local-approval-activity.md#step-1--creating-the-data-distribution-template-) voor meer informatie over gegevensdistributie.

![](assets/mkg_dist_data_distribution.png)

Selecteer **Doeldimensie** en **[!UICONTROL Distribution field]**. Selecteer **Lokale entiteit** voor **[!UICONTROL Assignment type]**.

Voeg op het tabblad **[!UICONTROL Distribution]** een veld toe voor elke lokale entiteit en geef de waarde op.

![](assets/mkg_dist_data_distribution2.png)

U kunt een tweede **Goedkeuring van het Doel** na **Levering** typeactiviteit toevoegen om een rapport over het te vormen.

In het bericht van de campagneverwezenlijking, ontvangt de lokale entiteit een contactlijst die door de centrale entiteitparameters vooraf is bepaald.

![](assets/mkg_dist_mutual_op_by_valid1.png)

De lokale entiteit kan bepaalde contacten schrappen die op de campagneinhoud worden gebaseerd.

![](assets/mkg_dist_mutual_op_by_valid2.png)

### Eenvoudig {#simple}

Als u een eenvoudige samenwerkingscampagne wilt maken, moet de sjabloon **[!UICONTROL Collaborative campaign (simple)]** zijn geselecteerd.

## Een gezamenlijk campagnemakket maken {#creating-a-collaborative-campaign-package}

Om een campagne ter beschikking te stellen van lokale entiteiten moet de centrale entiteit een campagnepakket maken.

Voer de volgende stappen uit:

1. Klik in de sectie **[!UICONTROL Navigation]** op de pagina **Campagnes** op de koppeling **[!UICONTROL Campaign packages]**.
1. Klik op de knop **[!UICONTROL Create]**.
1. Met de sectie boven in het venster kunt u de sjabloon **[!UICONTROL New collaborative package (mutualizedEmpty)]** selecteren.
1. Selecteer de referentiecampagne.
1. Geef het label, de map en het uitvoeringsschema voor het campagnemakket op.

### Datums {#dates}

De begin- en einddatum bepalen de zichtbaarheidsperiode van de campagne in de lijst met campagnepakketten.

Voor **samenwerkingscampagnes**, moet de centrale entiteit de registratie en verpersoonlijkingsdeadline specificeren.

>[!NOTE]
>
>Met **[!UICONTROL Personalization deadline]** kan de centrale entiteit een deadline kiezen waarbinnen de lokale entiteiten de documenten (spreadsheets, afbeeldingen) moeten hebben afgeleverd om de campagne te configureren. Dit is geen verplichte optie. Zijdelingse datums hebben geen invloed op de uitvoering van de campagne.

![](assets/s_advuser_mkg_dist_create_mutual_entry.png)

### Doelgroep {#audience}

De centrale entiteit moet de betrokken lokale entiteiten per campagne specificeren zodra de samenwerkingscampagne is opgezet.

![](assets/s_advuser_mkg_dist_create_mutual_entry2.png)

>[!CAUTION]
>
>**[!UICONTROL Simple, by form and by campaign collaborative campaign kits]** niet kan worden goedgekeurd tenzij de betrokken lokale entiteiten zijn gespecificeerd.

### Goedkeuringsmodi {#approval-modes}

Voor **samenwerkingscampagnes**, kunt u de wijze van de ordegoedkeuring specificeren.

![](assets/mkg_dist_edit_kit1.png)

In de handmatige modus moet de lokale entiteit zich abonneren op de campagne om deel te kunnen nemen.

In de automatische modus wordt de lokale entiteit vooraf geabonneerd op de campagne. Het kan het campagneabonnement annuleren of zijn parameters wijzigen zonder goedkeuring van de centrale entiteit te vereisen.

![](assets/mkg_dist_edit_kit2.png)

### Meldingen {#notifications}

Configuratie voor meldingen is identiek aan meldingen voor een lokale entiteit. Zie [deze sectie](../../campaign/using/creating-a-local-campaign.md#notifications).

## Bestellen van een campagne {#ordering-a-campaign}

Wanneer een samenwerkingscampagne aan de lijst van campagnepakketten wordt toegevoegd, worden de lokale entiteiten die tot het publiek behoren dat door de centrale entiteit wordt bepaald op de hoogte gebracht (de **samenwerkingscampagnes (door doelgoedkeuring)** hebben geen vooraf bepaald publiek). Het verzonden bericht bevat een koppeling waarmee u zich voor de campagne kunt registreren, zoals hieronder wordt getoond:

![](assets/mkg_dist_mutual_op_notification.png)

Met dit bericht kunnen lokale entiteiten ook de beschrijving bekijken die is ingevoerd door de centrale operator die het pakket heeft gemaakt, en documenten die aan de campagne zijn gekoppeld. Deze horen niet bij de campagne zelf, hoewel ze aanvullende informatie hierover verschaffen.

Zodra lokale operatoren zich via een webinterface hebben aangemeld, kunnen ze gepersonaliseerde informatie invoeren voor de samenwerkingscampagne die ze willen bestellen:

![](assets/mkg_dist_mutual_op_command.png)

Nadat een lokale entiteit de registratie heeft voltooid, worden centrale entiteiten via e-mail op de hoogte gebracht om hun bestelling goed te keuren.

![](assets/mkg_dist_mutual_op_valid_command.png)

Raadpleeg voor meer informatie de sectie [Goedkeuringsproces](../../campaign/using/creating-a-local-campaign.md#approval-process).

## Een bestelling {#approving-an-order} goedkeuren

Het proces voor het goedkeuren van een collectieve campagnepakketorde is het zelfde als wanneer het doen van dit voor een lokale campagne. Zie [deze sectie](../../campaign/using/creating-a-local-campaign.md#approving-an-order).
