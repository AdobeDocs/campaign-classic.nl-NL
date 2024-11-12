---
product: campaign
title: Leveringssjablonen gebruiken
description: Leveringssjablonen gebruiken
badge-v8: label="Ook van toepassing op v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
feature: Delivery Templates
hide: true
hidefromtoc: true
exl-id: a5da3f29-5eab-428c-b7c3-d9e4243fe628
source-git-commit: f469689f9e8a4d805fb95a1ae120ccd35aba3731
workflow-type: tm+mt
source-wordcount: '590'
ht-degree: 0%

---

# Sjablonen gebruiken {#use-templates}



De malplaatjes van de levering staan voor verhoogde efficiency toe door kant-en-klare scenario&#39;s voor de meeste gemeenschappelijke soorten activiteiten te verstrekken. Met malplaatjes, kunnen de marketers nieuwe campagnes met minimale aanpassing in een kortere hoeveelheid tijd opstellen.

Leer meer over leveringsmalplaatjes in [ deze sectie ](about-templates.md).

## Aan de slag met leveringssjablonen {#gs-templates}

A [ leveringsmalplaatje ](about-templates.md) laat u toe om eens een reeks van technische en functionele eigenschappen te bepalen die uw behoeften aanpassen en die voor toekomstige leveringen kunnen worden opnieuw gebruikt. U kunt dan tijd besparen en leveringen standaardiseren wanneer dat nodig is.

Wanneer u meerdere merken beheert in Adobe Campaign, raadt Adobe aan één subdomein per merk te hebben. Een bank kan bijvoorbeeld verschillende subdomeinen hebben die overeenkomen met elk van haar regionale agentschappen. Als een bank eigenaar is van het bluebank.com-domein, kunnen de subdomeinen @ny.bluebank.com, @ma.bluebank.com, @ca.bluebank.com enzovoort zijn. Als u één leveringssjabloon per subdomein hebt, kunt u altijd de juiste vooraf geconfigureerde parameters voor elk merk gebruiken. Hierdoor worden fouten voorkomen en bespaart u tijd.

**Uiteinde**: Om configuratiefouten te vermijden, adviseren wij dat u een inheems malplaatje dupliceert en zijn eigenschappen verandert eerder dan tot een nieuw malplaatje leidt.

## Adressen configureren

* Het adres van de afzender is verplicht om het verzenden van een e-mail toe te staan.

* Sommige ISPs (de Dienstverleners van Internet) controleren de geldigheid van het afzenderadres alvorens berichten goed te keuren.

* Een slecht geformuleerd adres kan ertoe leiden dat het door de ontvangende server wordt verworpen. U moet ervoor zorgen een correct adres wordt gegeven.

* Het adres moet de afzender uitdrukkelijk identificeren. Het domein moet eigendom zijn van en geregistreerd zijn bij de afzender.

* Adobe raadt u aan e-mailaccounts te maken die overeenkomen met de adressen die zijn opgegeven voor leveringen en antwoorden. Vraag de beheerder van het berichtensysteem om advies.

Voer de onderstaande stappen uit om adressen in de Campagne-interface te configureren:

1. In het [ leveringsmalplaatje ](about-templates.md), klik de **[!UICONTROL From]** verbinding. Vul in het venster **[!UICONTROL Email header parameters]** de volgende velden in:

   ![](assets/d_best_practices_email_header.png)

1. Controleer in het veld **[!UICONTROL Sender address]** of het adresdomein hetzelfde is als het subdomein dat u aan de Adobe hebt gedelegeerd. U kunt het deel vóór &#39;@&#39; maar niet het domeinadres wijzigen.

1. Gebruik in het veld **[!UICONTROL From]** een naam die gemakkelijk kan worden herkend door de ontvangers, zoals de naam van uw merk, om de openingsfrequentie van uw leveringen te verhogen. Om de ervaring van de ontvanger verder te verbeteren, kunt u de naam van een persoon toevoegen, bijvoorbeeld &quot;Emma van Megastore&quot;.

1. In de velden **[!UICONTROL Reply address text]** wordt standaard het adres van de afzender gebruikt voor antwoorden. Adobe raadt echter aan een bestaand reëel adres te gebruiken, zoals de klantenservice van uw merk. In dit geval, als een ontvanger een antwoord verzendt, zal de klantenzorg het kunnen behandelen.

### Een controlegroep instellen

Nadat de levering is verzonden, kunt u het gedrag van de uitgesloten ontvangers vergelijken met de ontvangers die de levering wel hebben ontvangen. Vervolgens kunt u de efficiëntie van uw campagnes meten. Leer meer over controlegroepen [ deze sectie ](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group).

Klik op de koppeling **[!UICONTROL To]** om een besturingsgroep in te stellen. Selecteer in het **[!UICONTROL Select target]** -venster de tab **[!UICONTROL Control group]** . U kunt een gedeelte van het doel extraheren, bijvoorbeeld een willekeurig monster van 5%.

![](assets/d_best_practices_control_group.png)

## Typologieën gebruiken om filters of controleregels toe te passen

Een typologie bevat controleregels die tijdens de analysefase worden toegepast, alvorens om het even welk bericht te verzenden.

Wijzig de standaardtypologie naar wens op het tabblad **[!UICONTROL Typology]** van de sjablooneigenschappen.

Bijvoorbeeld, om het uitgaande verkeer beter te controleren, kunt u bepalen welke IP adressen kunnen worden gebruikt door één affiniteit per subdomein te bepalen en één typologie per affiniteit te creëren. De affiniteiten worden gedefinieerd in het configuratiebestand van de instantie. Neem contact op met uw Adobe Campaign-beheerder.

Voor meer op typologieën, verwijs naar [ deze sectie ](../../campaign-opt/using/about-campaign-typologies.md).
