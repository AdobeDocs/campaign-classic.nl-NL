---
product: campaign
title: Leveringssjablonen gebruiken
audience: delivery
content-type: reference
topic-tags: deliveries-best-practices
exl-id: a5da3f29-5eab-428c-b7c3-d9e4243fe628
source-git-commit: bd9f035db1cbad883e1f27fe901e34dfbc9c1229
workflow-type: tm+mt
source-wordcount: '577'
ht-degree: 0%

---

# Sjablonen gebruiken {#use-templates}

![](../../assets/common.svg)

De malplaatjes van de levering staan voor verhoogde efficiency toe door kant-en-klare scenario&#39;s voor de meeste gemeenschappelijke soorten activiteiten te verstrekken. Met malplaatjes, kunnen de marketers nieuwe campagnes met minimale aanpassing in een kortere hoeveelheid tijd opstellen.

Meer informatie over leveringssjablonen vindt u in [deze sectie](creating-a-delivery-template.md).

## Aan de slag met leveringssjablonen {#gs-templates}

Met een [leveringssjabloon](creating-a-delivery-template.md) kunt u één keer een set technische en functionele eigenschappen definiëren die aan uw behoeften voldoen en die opnieuw kunnen worden gebruikt voor toekomstige leveringen. U kunt dan tijd besparen en leveringen standaardiseren wanneer dat nodig is.

Als u meerdere merken beheert in Adobe Campaign, raadt Adobe aan één subdomein per merk te hebben. Een bank kan bijvoorbeeld verschillende subdomeinen hebben die overeenkomen met elk van haar regionale agentschappen. Als een bank eigenaar is van het domein bluebank.com, kunnen de subdomeinen @ny.bluebank.com, @ma.bluebank.com, @ca.bluebank.com, enz. zijn. Als u één leveringssjabloon per subdomein hebt, kunt u altijd de juiste vooraf geconfigureerde parameters voor elk merk gebruiken. Hierdoor worden fouten voorkomen en bespaart u tijd.

**Tip**: Om configuratiefouten te vermijden, adviseren wij dat u een inheemse malplaatje dupliceert en zijn eigenschappen veranderen eerder dan een nieuw malplaatje tot stand te brengen.

## Adressen configureren

* Het adres van de afzender is verplicht om het verzenden van een e-mail toe te staan.

* Sommige ISPs (de Dienstverleners van Internet) controleren de geldigheid van het afzenderadres alvorens berichten goed te keuren.

* Een slecht geformuleerd adres kan ertoe leiden dat het door de ontvangende server wordt verworpen. U moet ervoor zorgen een correct adres wordt gegeven.

* Het adres moet de afzender uitdrukkelijk identificeren. Het domein moet eigendom zijn van en geregistreerd zijn bij de afzender.

* Adobe raadt u aan e-mailaccounts te maken die overeenkomen met de adressen die zijn opgegeven voor leveringen en antwoorden. Vraag de beheerder van het berichtensysteem om advies.

Voer de onderstaande stappen uit om adressen in de Campagne-interface te configureren:

1. Klik in de [leveringssjabloon](creating-a-delivery-template.md) op de koppeling **[!UICONTROL From]**. Vul in het venster **[!UICONTROL Email header parameters]** de volgende velden in:

   ![](assets/d_best_practices_email_header.png)

1. Controleer in het veld **[!UICONTROL Sender address]** of het adresdomein hetzelfde is als het subdomein dat u aan Adobe hebt gedelegeerd. U kunt het deel vóór &#39;@&#39; maar niet het domeinadres wijzigen.

1. Gebruik in het veld **[!UICONTROL From]** een naam die gemakkelijk kan worden herkend door de ontvangers, zoals de naam van uw merk, om de openingsfrequentie van uw leveringen te verhogen. Om de ervaring van de ontvanger verder te verbeteren, kunt u de naam van een persoon toevoegen, bijvoorbeeld &quot;Emma van Megastore&quot;.

1. In de **[!UICONTROL Reply address text]** gebieden, wordt het adres van de afzender gebruikt door gebrek voor antwoorden. Adobe raadt echter aan een bestaand reëel adres te gebruiken, zoals de klantenservice van uw merk. In dit geval, als een ontvanger een antwoord verzendt, zal de klantenzorg het kunnen behandelen.

### Een controlegroep instellen

Nadat de levering is verzonden, kunt u het gedrag van de uitgesloten ontvangers vergelijken met de ontvangers die de levering wel hebben ontvangen. Vervolgens kunt u de efficiëntie van uw campagnes meten. Meer informatie over besturingsgroepen [deze sectie](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group).

Klik op de koppeling **[!UICONTROL To]** om een besturingsgroep in te stellen. Selecteer in het venster **[!UICONTROL Select target]** de tab **[!UICONTROL Control group]**. U kunt een gedeelte van het doel extraheren, bijvoorbeeld een willekeurig monster van 5%.

![](assets/d_best_practices_control_group.png)

## Typologieën gebruiken om filters of controleregels toe te passen

Een typologie bevat controleregels die tijdens de analysefase worden toegepast, alvorens om het even welk bericht te verzenden.

Wijzig op het tabblad **[!UICONTROL Typology]** van de eigenschappen van de sjabloon de standaardtypologie naar wens.

Bijvoorbeeld, om het uitgaande verkeer beter te controleren, kunt u bepalen welke IP adressen kunnen worden gebruikt door één affiniteit per subdomein te bepalen en één typologie per affiniteit te creëren. De affiniteiten worden gedefinieerd in het configuratiebestand van de instantie. Neem contact op met uw Adobe Campaign-beheerder.

Raadpleeg [deze sectie](../../campaign-opt/using/about-campaign-typologies.md) voor meer informatie over typologieën.
