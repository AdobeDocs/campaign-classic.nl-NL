---
product: campaign
title: Berichtlevering optimaliseren
description: Leer hoe u de levering van berichten kunt optimaliseren
badge-v7: label="v7" type="Informative" tooltip="Is van toepassing op Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
feature: Deliverability
role: User
exl-id: 24b2ee47-bec7-43ce-81b3-0b2d1a5cebae
source-git-commit: d2f5f2a662c022e258fb3cc56c8502c4f4cb2849
workflow-type: tm+mt
source-wordcount: '748'
ht-degree: 7%

---

# Levering optimaliseren {#optimize-delivery}

Voordat u zelfs begint met het maken van leveringen, kunt u verschillende acties uitvoeren om het verzendingsproces te beveiligen en te optimaliseren.

In de volgende sectie worden aanbevolen procedures en aanbevolen procedures voor de optimale configuratie van Adobe Campaign beschreven. Als u deze praktijken volgt, worden de problemen die u later tegenkomt, tot een minimum beperkt.

## Platformprestaties

Verschillende factoren kunnen de serverprestaties rechtstreeks beïnvloeden en het platform vertragen:

* Het aantal en het type van verpersoonlijkingselementen: de verpersoonlijking in e-mail trekt gegevens uit het gegevensbestand voor elke ontvanger. Als er vele verpersoonlijkingselementen zijn, verhoogt dat de hoeveelheid gegevens nodig om de levering voor te bereiden.  Meer informatie over personalisatie in [deze sectie](about-personalization.md)

* De server wordt geladen: wanneer de marketingserver meerdere taken tegelijk uitvoert, kunnen de prestaties afnemen. De marketingserver moet alle inkomende en uitgaande gegevens voor alle leveringen coördineren om ervoor te zorgen dat de gegevens correct en op tijd zijn.

  **TIP** - Om dit te voorkomen, coördineert u de planning van de leveringen met de andere leden van uw team om de beste prestaties te garanderen.

* De workflowuitvoering: het controleren van uw workflows is essentieel om problemen met de prestaties van het platform te voorkomen. Volg de vermelde richtlijnen [in dit document](../../workflow/using/workflow-best-practices.md#execution-and-performance).

* Als je hiervoor in aanmerking komt, kun je gebruikmaken van [Mogelijkheden van het bedieningspaneel voor campagnes](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/key-features.html) om uw platform te controleren, gebruiken [prestatiebewaking](https://experienceleague.adobe.com/docs/control-panel/using/performance-monitoring/about-performance-monitoring.html?lang=nl) functies.

## Netwerkconfiguratie controleren {#network-config}

Om levering te optimaliseren wanneer het behandelen van e-mails in grote volumes en vermijd wordt verward voor spammer, zorg ervoor dat u een wettige netwerkconfiguratie hebt die niet probeert om de identiteit van de server te verbergen.

**Tip**: Gebruik een transparant adres van de afzender dat overeenkomt met de website van uw merk. Het bedrijf TravelAgency beheert bijvoorbeeld de hotelketen Valentino. Zijn bezit het valentino.com domein voor zijn website. Om het hotel Valentino in Parijs te promoten, gebruikt het subdomein paris.valentino.com. Daarom kan een relevant afzenderadres hotel@paris.valentino.com zijn.

## Afleverbaarheidsbeheer {#deliverability-management}

Om uw ontvangers&#39; te bereiken inbox zonder te stuiteren of als spam worden gemerkt, moet u het leverbaarheidstarief van uw berichten verbeteren.

* Wat is leverbaarheid?

   * Het verwijst naar de factoren van een e-mail die zijn capaciteit bepalen om door de server van een ontvanger worden goedgekeurd. ISPs (de Dienstverleners van Internet) filter uit e-mails die zij als SPAM identificeren, of zij blokkeren beelden van het downloaden. Als ze vaststellen dat een bepaald domein te veel e-mails verzendt, stellen ze een limiet in voor het aantal e-mails dat ze van die afzender accepteren.

   * Wanneer u uw e-mail controleert op leverbaarheid, wilt u zich op vier hoofdcategorieën concentreren: gegevenskwaliteit, bericht en inhoud, verzendende infrastructuur, en reputatie. Voor een diepere bespreking van dit onderwerp, verwijs naar [deze sectie](about-deliverability.md).

* De gedetailleerde aanbevelingen toepassen [in dit document](about-deliverability.md).

* Neem contact op met uw Adobe voor hulp.

## Quarantainebeheer {#quarantine-management}

Het is in uw belang om goede processen van het quarantainebeheer te handhaven.

Wanneer u e-mailberichten op een nieuw platform gaat verzenden, kunt u een lijst met adressen gebruiken die niet volledig zijn gekwalificeerd. Als u naar ongeldige adressen of naar honeypot-adressen (brievenbussen slechts die aan truc spammers worden gecreeerd) verzendt, zal dit de reputatie van uw platform beginnen te verminderen. Goede quarantainebeheerprocessen helpen: de adreskwaliteit handhaven, lijst van gewezen personen door internettoegangsproviders vermijden, en uw foutenpercentage verminderen, leveringen en productie versnellen.

**Tips**

* Als u een lijst met ongeldige adressen hebt, raadt de Adobe u aan deze te importeren in de quarantainetabel, via **[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Non deliverables Management]** > **[!UICONTROL Non deliverables and addresses]**.

* De ontvangers de waarvan adressen in quarantined zijn uitgesloten door gebrek tijdens de leveringsanalyse: zij worden niet gericht. Hierdoor wordt de levering versneld, omdat het foutenpercentage een belangrijk effect heeft op de leveringssnelheid. Een e-mailadres kan in quarantaine worden geplaatst bijvoorbeeld wanneer inbox volledig is of als het adres niet bestaat. [Meer informatie](#identifying-quarantined-addresses-for-a-delivery)

* Adobe Campaign beheert onjuiste adressen op basis van het type geretourneerde fout. Raadpleeg [deze sectie](understanding-quarantine-management.md) voor meer informatie.


* Sommige internetproviders beschouwen e-mails automatisch als spam als het aantal ongeldige adressen te hoog is. Met quarantaine kunt u dus voorkomen dat deze providers aan de lijst van gewezen personen worden toegevoegd.

* Het beheer van quarantaines zal ook de verzendkosten van SMS helpen verminderen door onjuiste telefoonnummers uit te sluiten van leveringen.

## Dubbele opt-in-regeling {#double-opt-in}

Om te voorkomen dat berichten naar ongeldige adressen worden verzonden, onjuiste communicatie wordt beperkt en de reputatie van de afzender wordt verbeterd, raadt de Adobe aan een dubbele opt-in-mechanisme in te voeren voor bevestiging na abonnementen. Zo weet u zeker dat een ontvanger met opzet is geabonneerd.

Nadere bijzonderheden over de toepassing van dit mechanisme worden uiteengezet in [deze sectie](../../web/using/use-cases--web-forms.md).
