---
product: campaign
title: Leveringssjablonen gebruiken
description: Leveringssjablonen gebruiken
badge-v7: label="v7" type="Informative" tooltip="Is van toepassing op Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
feature: Delivery Templates
exl-id: a5da3f29-5eab-428c-b7c3-d9e4243fe628
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '593'
ht-degree: 0%

---

# Sjablonen gebruiken {#use-templates}



De malplaatjes van de levering staan voor verhoogde efficiency toe door kant-en-klare scenario&#39;s voor de meeste gemeenschappelijke soorten activiteiten te verstrekken. Met malplaatjes, kunnen de marketers nieuwe campagnes met minimale aanpassing in een kortere hoeveelheid tijd opstellen.

Meer informatie over leveringssjablonen vindt u in [deze sectie](creating-a-delivery-template.md).

## Aan de slag met leveringssjablonen {#gs-templates}

A [leveringssjabloon](creating-a-delivery-template.md) kunt u een reeks technische en functionele eigenschappen definiëren die aan uw behoeften voldoen en die opnieuw kunnen worden gebruikt voor toekomstige leveringen. U kunt dan tijd besparen en leveringen standaardiseren wanneer dat nodig is.

Wanneer u meerdere merken beheert in Adobe Campaign, raadt Adobe aan één subdomein per merk te hebben. Een bank kan bijvoorbeeld verschillende subdomeinen hebben die overeenkomen met elk van haar regionale agentschappen. Als een bank eigenaar is van het bluebank.com-domein, kunnen de subdomeinen @ny.bluebank.com, @ma.bluebank.com, @ca.bluebank.com enzovoort zijn. Als u één leveringssjabloon per subdomein hebt, kunt u altijd de juiste vooraf geconfigureerde parameters voor elk merk gebruiken. Hierdoor worden fouten voorkomen en bespaart u tijd.

**Tip**: Om configuratiefouten te voorkomen, raden we u aan een native sjabloon te dupliceren en de eigenschappen ervan te wijzigen in plaats van een nieuwe sjabloon te maken.

## Adressen configureren

* Het adres van de afzender is verplicht om het verzenden van een e-mail toe te staan.

* Sommige ISPs (de Dienstverleners van Internet) controleren de geldigheid van het afzenderadres alvorens berichten goed te keuren.

* Een slecht geformuleerd adres kan ertoe leiden dat het door de ontvangende server wordt verworpen. U moet ervoor zorgen een correct adres wordt gegeven.

* Het adres moet de afzender uitdrukkelijk identificeren. Het domein moet eigendom zijn van en geregistreerd zijn bij de afzender.

* Adobe raadt u aan e-mailaccounts te maken die overeenkomen met de adressen die zijn opgegeven voor leveringen en antwoorden. Vraag de beheerder van het berichtensysteem om advies.

Voer de onderstaande stappen uit om adressen in de Campagne-interface te configureren:

1. In de [leveringssjabloon](creating-a-delivery-template.md)klikt u op de knop **[!UICONTROL From]** koppeling. In de **[!UICONTROL Email header parameters]** venster, vult de volgende velden in:

   ![](assets/d_best_practices_email_header.png)

1. In de **[!UICONTROL Sender address]** , zorgt u ervoor dat het adresdomein hetzelfde is als het subdomein dat u aan de Adobe hebt gedelegeerd. U kunt het deel vóór &#39;@&#39; maar niet het domeinadres wijzigen.

1. In de **[!UICONTROL From]** gebruiken, een naam die gemakkelijk door de ontvangers, zoals de naam van uw merk, kan worden geïdentificeerd om het openingstarief van uw leveringen te verhogen. Om de ervaring van de ontvanger verder te verbeteren, kunt u de naam van een persoon toevoegen, bijvoorbeeld &quot;Emma van Megastore&quot;.

1. In de **[!UICONTROL Reply address text]** in velden wordt standaard het adres van de afzender gebruikt voor antwoorden. Adobe raadt echter aan een bestaand reëel adres te gebruiken, zoals de klantenservice van uw merk. In dit geval, als een ontvanger een antwoord verzendt, zal de klantenzorg het kunnen behandelen.

### Een controlegroep instellen

Nadat de levering is verzonden, kunt u het gedrag van de uitgesloten ontvangers vergelijken met de ontvangers die de levering wel hebben ontvangen. Vervolgens kunt u de efficiëntie van uw campagnes meten. Meer informatie over controlegroepen [deze sectie](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group).

Als u een controlegroep wilt instellen, klikt u op de knop **[!UICONTROL To]** koppeling. In de **[!UICONTROL Select target]** venster, selecteert u de **[!UICONTROL Control group]** tab. U kunt een gedeelte van het doel extraheren, bijvoorbeeld een willekeurig monster van 5%.

![](assets/d_best_practices_control_group.png)

## Typologieën gebruiken om filters of controleregels toe te passen

Een typologie bevat controleregels die tijdens de analysefase worden toegepast, alvorens om het even welk bericht te verzenden.

In de **[!UICONTROL Typology]** wijzigt u de standaardtypologie naar wens.

Bijvoorbeeld, om het uitgaande verkeer beter te controleren, kunt u bepalen welke IP adressen kunnen worden gebruikt door één affiniteit per subdomein te bepalen en één typologie per affiniteit te creëren. De affiniteiten worden gedefinieerd in het configuratiebestand van de instantie. Neem contact op met uw Adobe Campaign-beheerder.

Raadpleeg voor meer informatie over typologieën [deze sectie](../../campaign-opt/using/about-campaign-typologies.md).
