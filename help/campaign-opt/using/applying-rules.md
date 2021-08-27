---
product: campaign
title: Regels toepassen
description: Regels toepassen
audience: campaign
content-type: reference
topic-tags: campaign-optimization
exl-id: 09ec0fc0-76ed-4c73-8bdf-c931e2103aa9
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '977'
ht-degree: 9%

---

# Regels toepassen{#applying-rules}

![](../../assets/v7-only.svg)

## Een typologie toepassen op een levering {#applying-a-typology-to-a-delivery}

Om de gemaakte typologische regels toe te passen, moet u deze koppelen aan een typologie en vervolgens in de aflevering verwijzen naar deze typologie. Dit doet u als volgt:

1. Maak een campagnetypologie.

   Typologieën zijn toegankelijk via het knooppunt **[!UICONTROL Administration > Campaign Management > Typology management]** > **[!UICONTROL Typologies]**.

1. Ga naar het **[!UICONTROL Rules]** lusje, klik **[!UICONTROL Add]** knoop en selecteer de regels om met deze typologie toe te passen.

   ![](assets/campaign_opt_pressure_sample_1_6.png)

1. Sla de typologie op: wordt toegevoegd aan de lijst van bestaande typologieën.
1. Open de levering waarop u de regels wilt toepassen.
1. Open de leveringseigenschappen en open **[!UICONTROL Typology]** tabel.
1. Selecteer de typologie in de vervolgkeuzelijst.

   ![](assets/campaign_opt_pressure_sample_1_7.png)

   >[!NOTE]
   >
   >De typologie kan in de leveringssjabloon worden gedefinieerd, en wordt dan automatisch toegepast op alle leveringen die met deze sjabloon zijn gemaakt.

## Toepassingsvoorwaarden definiëren {#defining-application-conditions}

U kunt het toepassingsgebied van een regel afhankelijk van uw behoeften beperken (behalve controleregels).

Het is mogelijk om typologische regels zodanig te configureren dat deze alleen betrekking hebben op bepaalde leveringen die zij aan elkaar koppelen, of op bepaalde ontvangers onder het doel van een levering.

Als u de toepassingsvoorwaarden van een regel wilt definiëren, klikt u op de koppeling **[!UICONTROL Edit the rule application conditions...]** op het tabblad **[!UICONTROL General]**.

Dan gebruik de vraagredacteur om het filtreren voorwaarden te bepalen. In het volgende voorbeeld heeft de capaciteitsregel alleen betrekking op leveringen met het woord &quot;aanbieding&quot; op het etiket of op leveringen die vóór 1 april 2013 zijn gemaakt.

![](assets/campaign_opt_create_capacity_criterion.png)

>[!NOTE]
>
>Voor filterregels kunt u de toepassingsvoorwaarde van filtercriteria selecteren: zij kunnen afhangen van de levering of het leveringsoverzicht . Voor meer op dit, verwijs naar [Conditioning een het filtreren regel](filtering-rules.md#conditioning-a-filtering-rule).

## Rekenfrequentie aanpassen {#adjusting-calculation-frequency}

Arbitrages worden elke avond automatisch opnieuw uitgevoerd via de workflow voor het opschonen van databases. Waarden kunnen echter ook na deze periode worden opgeslagen.

Sommige berekeningen gebruiken namelijk waarden die niet dagelijks veranderen. Het zou daarom irrelevant zijn om de gegevens elke dag opnieuw te berekenen en de database voor niets te overladen. Bijvoorbeeld, als een proces het marketing gegevensbestand met klantennestscores verrijkt en informatie op een wekelijkse basis koopt, te hoeven de gegevens die op deze waarden worden gebaseerd niet elke dag opnieuw te worden berekend.

Hiervoor definieert u in het veld **[!UICONTROL Frequency]** van het tabblad **[!UICONTROL General]** een maximumperiode waarin het doel wordt opgeslagen. Standaard geeft de waarde **0** aan dat de berekening geldig blijft tot de volgende uitvoering van dagelijkse herarbitrage.

Als u de resultaten na deze periode wilt opslaan, geeft u een waarde groter dan 12 op in het veld **[!UICONTROL Frequency]**: zodra deze termijn is verstreken, worden alle regels opnieuw toegepast.

Met de optie **[!UICONTROL Re-apply the rule at the start of personalization]** kunt u de regel automatisch toepassen tijdens de verpersoonlijkingsfase, ook als de periode die in het veld **[!UICONTROL Frequency]** wordt vermeld, nog geldig is.

## Het selecteren van de fase van de regeltoepassing {#selecting-the-rule-application-phase}

De typologieregels worden in een specifieke volgorde toegepast tijdens de fase waarin de producten waarop zij betrekking hebben, worden gericht, geanalyseerd en gepersonaliseerd.

### Uitvoeringsopdracht {#execution-order}

In de standaardbewerkingsmodus worden de regels in de volgende volgorde toegepast:

1. Controleregels, indien toegepast aan het begin van targeting.
1. Filterregels:

   * Native toepassingsregels voor adreskwalificatie: bepaald adres / niet-geverifieerd adres / adres op de lijst van gewezen personen / quarantined adres / adreskwaliteit.
   * Filterregels die door de gebruiker zijn gedefinieerd.
   * Deduplicatieregel op het adres of de id (indien nodig toegepast).

1. Drukregels.
1. Capaciteitsregels.
1. Controleregels, indien toegepast aan het einde van targeting.
1. Controleregels, indien toegepast aan het begin van personalisatie. Als de gebruikersregels (filtreren/druk/capacitief) zijn verlopen en opnieuw moeten worden berekend, zullen zij tijdens deze stap worden toegepast.
1. Controlevoorschriften, als zij aan het eind van verpersoonlijking van toepassing zijn.

>[!NOTE]
>
>Als u met de module van de Interactie van de Campagne werkt, aanbiedingsontvankelijkheidsregels worden toegepast tezelfdertijd zoals het filtreren regels (voor aanbiedingen die in de leveringsoverzichten worden gevonden) of tijdens de verpersoonlijkingsfase, tijdens de vraag aan de aanbiedingsmotor.

U kunt de uitvoeringsopeenvolging van regels aanpassen die het zelfde type hebben gebruikend het aangewezen gebied op het **[!UICONTROL General]** lusje van de regel. Wanneer verscheidene regels tijdens de zelfde fase van de berichtverwerking worden uitgevoerd, kunt u hun uitvoeringsopeenvolging op het **[!UICONTROL Execution sequence]** gebied vormen.

Bijvoorbeeld, zal een drukregel met een uitvoeringsorde van 20 vóór een drukregel met een uitvoeringsorde van 30 worden uitgevoerd.

### Controleregels {#control-rules}

Voor **[!UICONTROL Control]** regels, kunt u beslissen op welk punt van de cyclus van het leveringsleven de regel zal worden toegepast (vóór of na het richten, bij het begin van verpersoonlijking, aan het eind van de analyse). Selecteer de waarde die u wilt toepassen in de vervolgkeuzelijst van het veld **[!UICONTROL Phase]** op het tabblad **[!UICONTROL General]** van de typologieregel.

![](assets/campaign_opt_define_control_phase.png)

Mogelijke waarden zijn:

* **[!UICONTROL At the start of targeting]**

   Om de verpersoonlijkingsstap te verhinderen in het geval van fouten worden uitgevoerd, kunt u de controleregel hier toepassen.

* **[!UICONTROL After targeting]**

   Als u het volume van het doel moet kennen om de controleregel toe te passen, selecteer deze fase.

   De besturingsregel **[!UICONTROL Check proof size]** wordt bijvoorbeeld toegepast na elk doelstadium: deze regel verhindert berichtverpersoonlijking als er teveel proefontvangers zijn.

* **[!UICONTROL At the start of personalization]**

   Deze fase moet worden geselecteerd als de controle de goedkeuring van berichtverpersoonlijking betreft. De personalisatie van berichten wordt uitgevoerd tijdens de analysefase.

* **[!UICONTROL At the end of the analysis]**

   Wanneer een controle berichtverpersoonlijking om vereist te zijn volledig, selecteer deze fase.

## Aanvullende configuraties {#additional-configurations}

### Het uitgaande verkeer SMTP van de controle {#control-outgoing-smtp-traffic}

Als optie, kunt u het **[!UICONTROL Managing affinities with IP addresses]** gebied gebruiken om leveringen aan de leveringsserver (MTA) deze affiniteit te verbinden. Hiermee kunt u het aantal e-mails voor specifieke leveringen beperken tot computers of uitvoeradressen.

![](assets/campaign_opt_select_ip_affinity.png)

>[!NOTE]
>
>Affinity-beheer is niet van toepassing op typologieën **[!UICONTROL Filtering]**.\
>Affinities worden gedefinieerd in het configuratiebestand van de instantie, op de Adobe Campaign-server. Raadpleeg [deze sectie](../../installation/using/about-initial-configuration.md) voor meer informatie.

### Campagne optimaliseren en Distribueren {#campaign-optimization-and-distributed-marketing}

Met het tabblad **[!UICONTROL Distributed Marketing]** kunt u typologieën en/of regels opnieuw toewijzen die van toepassing zijn wanneer een gedeelde campagne wordt besteld en/of gereserveerd. Voor een lokale entiteit gedefinieerde typologieën/regels (gekoppeld aan die welke voor de centrale entiteit zijn gedefinieerd) vervangen regels/typologieën die aan de centrale entiteit zijn gekoppeld. Met Opnieuw toewijzen kunt u de regels van de centrale entiteit aanpassen aan de lokale entiteiten die de campagne bestellen.

![](assets/simu_campaign_opti_distrib_mkg.png)

>[!NOTE]
>
>In typologieën en typologieregels wordt het tabblad **[!UICONTROL Distributed Marketing]** toegevoegd als uw licentie deze optie bevat: gelieve uw vergunningsovereenkomst te controleren.\
>Raadpleeg [Informatie over gedistribueerde marketing](../../distributed/using/about-distributed-marketing.md) voor meer informatie over gedistribueerde marketing.
