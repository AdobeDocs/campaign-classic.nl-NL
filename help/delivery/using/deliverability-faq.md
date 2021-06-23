---
product: campaign
title: Belangrijkste punten bij het beheren van de leverbaarbaarheid in Adobe Campaign Classic
description: Wat zijn de belangrijkste punten om te controleren wanneer het beheren van leverbaarheid in Adobe Campaign Classic?
audience: delivery
content-type: reference
topic-tags: deliverability-management
exl-id: f94897c1-b44c-4100-ac50-a89b13fa6f2f
source-git-commit: a129f49d4f045433899fd7fdbd057fb16d0ed36a
workflow-type: tm+mt
source-wordcount: '657'
ht-degree: 2%

---

# Probleemoplossing voor levering{#deliverability-faq}

Ondervindt u een probleem met de leesbaarheid? U kunt hier de oplossing vinden.

## MX-regelfout {#mx-rule-error}

**Wat betekent het foutbericht &#39;quota gehaald&#39;?**

Dit bericht geeft aan dat u de quota voor een specifieke MX hebt bereikt en dat u moet wachten om nog een e-mail naar deze provider te kunnen verzenden.

In Adobe Campaign is er een configuratie voor het aantal e-mails per uur dat kan worden verzonden. Deze configuratie moet met waakzaamheid worden gebruikt, aangezien het aantal in het geval wordt bepaald het aantal verbindingen die met ISP worden uitgevoerd en niet het aantal daadwerkelijk verzonden e-mails betreft.

Dit betekent dat een verbinding een MX-regel kan gebruiken zonder dat een e-mail is verzonden. In dit geval, zal een configuratie met IP of een domein met een lage reputatie verscheidene verbindingen moeten proberen alvorens een e-mail te verzenden. Voor elke poging, zal een berichten per uurkrediet worden gebruikt. Als gevolg hiervan zullen de prestaties van de marketingcampagne aanzienlijk worden beïnvloed.

Daarom is &#39;met quota&#39;s tegemoet gekomen&#39; niet alleen een configuratieprobleem, maar kan het ook worden gekoppeld aan reputatie. Het is belangrijk om foutenmeldingen in [SMTP logboek](../../production/using/monitoring-processes.md#smtp-errors-per-domain) te analyseren.

Zie [deze sectie](../../installation/using/email-deliverability.md#mx-configuration) voor meer informatie over MX-configuratie.

## Hetzelfde foutbericht voor een ISP {#same-error-for-an-isp}

**Waarom krijg ik altijd het zelfde foutenbericht voor bepaalde ISP?**

Als u altijd het zelfde foutenbericht voor ISP krijgt, kan uw e-mail of IP als gebrek door ISP worden ontdekt. Voer de volgende aanbevelingen uit:
* Controleer of u een groot percentage fouten ontvangt die zijn gekoppeld aan onbestaande e-mailadressen (**Onbekende gebruiker** fouten).
* Werk uw abonnementsformulieren bij om fouten in de ingevoerde domeinnamen op te sporen (bijvoorbeeld: gmaul.com of yaho.com).
* Als u fouten opmerkt die verklaren dat uw berichten als spam worden verklaard, of dat uw berichten constant worden geblokkeerd, probeer exclusief de ontvangers die niet in één van uw berichten in de laatste 12 maanden van het doel hebben geopend of geklikt.

Als het probleem aanhoudt, neemt u contact op met de service voor commercieel gebruik of voor levering, [Adobe Klantenservice](https://helpx.adobe.com/nl/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

## Lijst van gewezen personen versus quarantaine {#denylist-versus-quarantine}

* **Wat is het verschil tussen een e-mailadres op lijst van gewezen personen en een quarantined e-mailadres?**

   * De status **[!UICONTROL Denylisted]** is een resultaat van een feedbacklus (wanneer een persoon een bericht rapporteert als spam).

   * De status **[!UICONTROL Quarantined]** is het resultaat van een zachte of harde stuit.
   Zie [deze sectie](understanding-quarantine-management.md#quarantine-vs-denylist)voor meer informatie.

* **Wat betekenen de verschillende redenen voor quarantainefouten?**

   Hier volgen tien mogelijke redenen: niet bepaald, gebruiker onbekend, ongeldig domein, op lijst van gewezen personen, geweigerd, fout genegeerd, onbereikbaar, rekening gehandicapt, brievenbus volledig, niet verbonden.

   Voor meer op dit, zie [Het begrip quarantainebeheer](understanding-quarantine-management.md).

## Verwijderen uit lijst van gewezen personen {#remove-from-denylist}

* **Een van mijn ontvangers is per ongeluk aan de lijst van gewezen personen toegevoegd. Hoe verwijder ik hen uit ontkenner zodat ik kan beginnen hen berichten opnieuw te verzenden?**

   * Ga naar **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]**.
   * Stel in de details van de corresponderende record de waarde van het veld **[!UICONTROL Status]** in op **[!UICONTROL Valid]**.
   * Sla de record op.

* **Hoe kan ik te weten komen of één van mijn IPs op een lijst van gewezen personen is? Hoe verwijder ik mijn IP(s) uit een lijst van gewezen personen?**

   Om te controleren of uw IP adres op een lijst van gewezen personen is, kunt u diverse websites gebruiken om het te verifiëren, zoals:
   * [MX-gereedschapset](https://mxtoolbox.com/)
   * [Wat is mijn IP adres](https://whatismyipaddress.com)

   Over het algemeen, zal het resultaat van de IP adrescontrole een lijst terugkeren die details van de lijst van gewezen personen en ook de naam van de website bevat die het IP adres ontkende.

   Als u op de desbetreffende koppeling klikt, hebt u toegang tot de gegevens van de website. Vervolgens kunt u vragen dat uw website wordt verwijderd van de website die het IP-adres aan de lijst van gewezen personen heeft toegevoegd.

   >[!NOTE]
   >
   >Het verwijderingsproces kan afhankelijk van de website variëren. Sommige plaatsen vereisen u om een rekening tot stand te brengen, terwijl anderen enkel u nodig hebben om het IP adres te verstrekken.
