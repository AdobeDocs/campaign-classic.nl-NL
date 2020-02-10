---
title: Informatie over gedistribueerde marketing
seo-title: Informatie over gedistribueerde marketing
description: Informatie over gedistribueerde marketing
seo-description: null
page-status-flag: never-activated
uuid: 7f7ece67-c644-4072-a06c-c5b49f3acb5d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: distributed-marketing
discoiquuid: 6d694f5c-1d1f-4686-b3bf-8697d919a0c8
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b47dcfa0e4ee2e5e43e7aa14b94e12fd70ff9c2d

---


# Informatie over gedistribueerde marketing{#about-distributed-marketing}

## Inleiding {#introduction}

Adobe Campaign biedt een **gedistribueerde marketingtoepassing** voor het uitvoeren van samenwerkingscampagnes tussen centrale entiteiten (hoofdkantoor, marketingafdelingen, enz.) en lokale entiteiten (verkooppunten, regionale agentschappen, enz.). Deze samenwerking is gebaseerd op een gedeelde werkruimte die bekend staat als de **[!UICONTROL list of campaign packages]**, waar centraal gecreëerde campagnemalplaatjes en instanties aan lokale entiteiten worden aangeboden.

De centrale entiteit verstrekt campagnes die lokale entiteiten kunnen gebruiken. Campagnes worden geconcretiseerd door pakketten die lokale of samenwerkingscampagnes vertegenwoordigen. Om een campagne te kunnen voeren, moet de lokale entiteit deze opdracht geven en moet de bestelling worden goedgekeurd.

>[!CAUTION]
>
>De module Distributed Marketing is een optie **Campagne** . Controleer uw licentieovereenkomst.

##  Terminologie {#terminology}

### Centrale entiteiten {#central-entities}

De centrale entiteiten bestaan uit marketingexploitanten die verantwoordelijk zijn voor het specificeren van de communicatie en die lokale entiteiten bijstaan bij het uitvoeren van hun marketingcampagne.

De verdeelde marketing module staat de centrale entiteit toe om:

* het opzetten van marketingcampagnes voor lokale entiteiten;
* de mate van autonomie van lokale entiteiten ten aanzien van hun keuze in klant/vooruitzicht communicatie, het richten, inhoud, enz. te vergroten.
* beheer- en controlekosten;
* een netwerk van agentschappen te beheren.

### Lokale entiteiten {#local-entities}

Lokale entiteiten kunnen agentschappen, winkels of groepen van specifieke lokale exploitanten zijn (landelijke of regionale managers, merkbeheerders, enz.).

Met Distributed Marketing kunnen lokale entiteiten meer autonomie hebben en tegelijk de uitvoeringskosten optimaliseren.

### Lokalisatie {#localization}

Lokalisatie is de capaciteit van een lokale entiteit om het doel en de inhoud van een campagne te wijzigen. Het mogelijke niveau van localisatie hangt van het type van campagne en zijn implementatie af.

### Lijst met campagnepakketten {#list-of-campaign-packages}

De lijst met campagnepakketten bevat de campagnes die beschikbaar zijn voor lokale entiteiten.

### Campagne {#campaign-package}

Sjabloon (of campagneexemplaar) dat door een centrale entiteit is gemaakt en ter beschikking is gesteld van een set lokale entiteiten.

### Lokale campagne {#local-campaign}

Een lokale campagne is een instantie die is gemaakt op basis van een sjabloon waarnaar in de lijst van **[!UICONTROL campaign packages]** met een **specifiek uitvoeringsschema** wordt verwezen. Zijn doel is om aan een lokale communicatie behoefte te voldoen gebruikend een campagnemalplaatje dat opstelling en gevormd door de centrale entiteit was.

De mate van autonomie van de lokale entiteit hangt af van de gebruikte implementatie.

Zie [Een lokale campagne](../../campaign/using/creating-a-local-campaign.md)maken.

### Gezamenlijke campagne {#collaborative-campaign}

Een samenwerkingscampagne is een campagne waarvan het **uitvoeringsplan door de centrale entiteit wordt bepaald** , die de lokale entiteit kan gebruiken. De inhoud blijft voor elke lokale entiteit hetzelfde, maar de kosten worden gedeeld. Om deel te nemen, onderschrijven lokale entiteiten de samenwerkingscampagne.

* **[!UICONTROL Collaborative campaign (by form)]**: aanbevolen voor campagnes waarbij maximaal 300 lokale entiteiten betrokken zijn. De lokale entiteit kan vooraf bepaalde parameters voor het richten van zich en inhoudsverpersoonlijking in een vorm van het Web ingaan. Het formulier kan een Adobe Campagne-formulier of een extern formulier (extranetclient) zijn. Een functionele beheerder kan het formulier definiëren en configureren op basis van een formuliersjabloon dat door de integrator is gedefinieerd. Om tot de campagne opdracht te geven, heeft de lokale entiteit enkel de toegang van het Web nodig.
* **[!UICONTROL Collaborative campaign (by campaign)]**: aanbevolen voor campagnes gericht op tientallen lokale entiteiten. Dit type campagne leidt tot kindcampagnes voor elke lokale entiteit. Zodra de campagne door de centrale entiteit **[!UICONTROL collaborative campaign (by campaign)]** is goedgekeurd, wordt de campagne ter beschikking gesteld van de lokale entiteit, die het kan wijzigen. Uitvoering wordt automatisch gesynchroniseerd tussen bovenliggende en onderliggende campagnes. De lokale entiteit moet toegang hebben tot een instantie om een campagne te bestellen en er deel van te nemen.
* **[!UICONTROL Collaborative campaign (by target approval)]**: aanbevolen voor campagnes die gericht zijn op enkele duizenden lokale entiteiten. De lokale entiteit ontvangt een lijst van contacten die door de centrale entiteit vooraf is bepaald. De lokale entiteit besluit al dan niet om bepaalde contacten te houden die op de campagneinhoud, via een vorm van het Web worden gebaseerd. Lokale entiteiten worden afgeleid van de lijst met geselecteerde contactpersonen. Om aan de campagne deel te nemen, heeft de lokale entiteit enkel de toegang van het Web nodig.
* **[!UICONTROL Collaborative campaign (simple)]**: deze modus zorgt voor compatibiliteit met de specifieke uitvoeringsprocessen van eerdere versies.

Zie Een [samenwerkingscampagne](../../campaign/using/creating-a-collaborative-campaign.md)maken.

### Campagnepakketten ordenen {#ordering-campaign-packages}

Als een lokale entiteit zich voor een campagne registreert, wordt dit in een orde gemaakt die alle informatie met betrekking tot de campagnemelocalisatie groepeert.

## Werkruimte {#workspace}

De lijst met campagnepakketten is toegankelijk vanuit het **heelal** Campagnes: Klik op de **[!UICONTROL Campaign packages]** koppeling.

![](assets/mkg_dist_home_local_op.png)

Met dit venster kunnen alle lokale operatoren de campagnes bekijken die beschikbaar zijn voor hun lokale agentschap.

In het geval van centrale agentschappen, toont dit venster alle pakketten beschikbaar in de lijst van campagnepakketten en biedt extra verbindingen voor het uitgeven van de lijst.

## Exploitanten en entiteiten {#operators-and-entities}

Begin door de centrale en lokale entiteitexploitanten via de **[!UICONTROL Access management]** omslag te specificeren.

![](assets/s_advuser_mkg_dist_tree.png)

### Operatoren {#operators}

U moet centrale en lokale operatoren maken.

Centrale operatoren moeten tot de **[!UICONTROL Central management]** operatorgroep behoren of het **[!UICONTROL CENTRAL]** benoemde recht hebben.

Lokale operatoren moeten tot de **[!UICONTROL Local management]** operatorgroep behoren of het **[!UICONTROL LOCAL]** genoemde recht hebben. Zij moeten ook gekoppeld zijn aan hun lokale entiteit.

![](assets/s_advuser_mkg_dist_local_create.png)

### Organisatorische entiteiten {#organizational-entities}

Als u een organisatie-entiteit wilt maken, klikt u op het **[!UICONTROL Administration > Access management > Organizational entities]** knooppunt en klikt u op het **[!UICONTROL New]** pictogram boven de lijst met entiteiten.

![](assets/s_advuser_mkg_dist_local_list.png)

Elke organisatie bevat identificatiegegevens (label, interne naam, contactgegevens enz.) en groepen die betrokken zijn bij het goedkeuringsproces voor orders. Deze worden gedefinieerd in de **[!UICONTROL Notifications and approvals]** sectie op het **[!UICONTROL General]** tabblad.

* Definieer een groep met pakketmeldingen: elke keer dat een nieuw pakket wordt toegevoegd aan de lijst van campagnepakketten en elke keer dat een campagne beschikbaar komt , ontvangen de exploitanten in deze groep een bericht .
* Selecteer de groep van controleurs die belast is met de goedkeuring van orders, d.w.z. de controleurs die verantwoordelijk zijn voor de goedkeuring van door de lokale entiteit bestelde campagnes.
* Tot slot selecteert u de groep van controleurs die verantwoordelijk is voor de goedkeuring van de lokale campagne (doel, inhoud, budget, enz.). Afhankelijk van de sjabloon kan deze groep worden toegevoegd aan het bestellen van een campagne.

>[!NOTE]
>
>Het goedkeuringsproces wordt beschreven in het gedeelte [Goedkeuringsproces](../../campaign/using/creating-a-local-campaign.md#approval-process) .

## Implementatie {#implementation}

De verdeelde campagnes van de Marketing worden gecreeerd en door de centrale entiteit gepubliceerd. Zij kunnen door zowel lokale als centrale entiteiten worden gebruikt wanneer dat nodig is.

De procedure voor de tenuitvoerlegging hangt af van het type campagnemakket dat wordt gebruikt en het niveau van de delegaties van de lokale entiteit.

### Integrator-zijde {#integrator-side}

1. Lokale entiteiten maken.
1. Ontvangers koppelen aan de operatoren die lokale entiteiten beheren.

   ![](assets/mkg_dist_local_entity_association.png)

1. Rechten en bladerregels voor lokale entiteiten opgeven
1. Geef de set velden op die nodig zijn voor de lokalisatie van de campagne:

   * definitie van het doel en maximumgrootte;
   * inhoudsdefinitie,
   * uitvoeringsschema (contactdatum en uitwinningsdatum), alleen **voor lokale marktdeelnemers**;
   * uitbreiding van het bestelschema met alle noodzakelijke extra gebieden.

1. Maak een webformulier (Adobe of extranet) waarmee u lokalisatieparameters kunt weergeven, het doel en het budget kunt evalueren en een voorvertoning van de inhoud kunt weergeven en de volgorde kunt goedkeuren.

   Voor **samenwerkingscampagnes (door doelgoedkeuring)**, creeer de lijst waar de goedkeuringen voor elke lokale entiteit zullen worden bewaard.

### Functionele beheerderszijde {#functional-administrator-side}

Deze stappen moeten worden uitgevoerd bij het opzetten van elke campagne.

1. Werk het formulier bij met de velden die worden gebruikt voor de lokalisatie van de campagne.
1. Maak een instantie van een geschikt campagnemalplaatje (samenwerkingscampagne) of dupliceer de campagnemalplaatje (lokale campagne).
1. Configureer de campagne met de lokalisatievelden en de formulierverwijzing.
1. Publiceer de campagne.

### Lokale operatorzijde {#local-operator-side}

Deze stappen moeten voor elke campagne worden uitgevoerd.

1. Nadat u een melding hebt ontvangen over de beschikbaarheid van het campagnepakket, geeft u de locatie van de campagne op (optioneel).
1. Evalueer het doel, de begroting, enz.
1. Voorbeeld van inhoud campagne.
1. De campagne bestellen.

