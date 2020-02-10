---
title: Over aangepaste tabel voor ontvangers
seo-title: Over aangepaste tabel voor ontvangers
description: Over aangepaste tabel voor ontvangers
seo-description: null
page-status-flag: never-activated
uuid: 4b162da4-90d2-44ff-9f89-ff0275540359
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
discoiquuid: c3ff8462-e47e-4637-8213-769fdeb86a57
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 668a0093616e1a2b49623b010ae5055f4d43d9b9

---


# Over aangepaste tabel voor ontvangers{#about-custom-recipient-table}

In deze sectie worden de beginselen beschreven voor het gebruik van een niet-standaardtabel voor ontvangers.

Standaard biedt Adobe Campagne een standaard ontvangende tabel waaraan functies en processen buiten de box zijn gekoppeld. De standaard ontvankelijke lijst heeft een aantal vooraf bepaalde gebieden en lijsten die gemakkelijk kunnen worden uitgebreid gebruikend een uitbreidingslijst.

Als deze extensiemethode voldoende flexibiliteit biedt om een tabel uit te breiden, is het niet mogelijk het aantal velden of koppelingen in de tabel te beperken. Het gebruiken van een niet-standaardlijst, of &quot;externe ontvankelijke lijst&quot;, staat voor een grotere flexibiliteit toe maar vereist bepaalde voorzorgsmaatregelen wanneer het uitvoeren van het.

## Voorzorgsmaatregelen {#precisions}

Met deze functionaliteit kan Adobe Campaign gegevens uit een externe database verwerken: deze gegevens worden gebruikt als een reeks profielen voor leveringen . Bij de implementatie van dit proces zijn verschillende definities nodig die relevant kunnen zijn voor de behoeften van de klant. Bijvoorbeeld:

* Geen updatestream van en naar de Adobe Campagne-database: gegevens uit deze tabel kunnen rechtstreeks worden bijgewerkt via de database-engine die de tabel host.
* Geen wijzigingen in de processen die op de bestaande database worden uitgevoerd.
* Een profieldatabase gebruiken met een niet-standaardstructuur: de mogelijkheid om profielen die in verschillende tabellen zijn opgeslagen, met verschillende structuren te leveren met behulp van één exemplaar.
* Er zijn geen wijzigingen of onderhoud vereist tijdens het bijwerken van de Adobe Campagne-database.
* De standaard ontvankelijke lijst is nutteloos als u niet de meeste lijstgebieden nodig hebt of als het gegevensbestandmalplaatje niet op de ontvangers wordt gecentreerd.
* Om efficiënt te zijn, is een lijst met weinig gebieden nodig als u een significant aantal profielen hebt. De standaard ontvangende tabel heeft te veel velden voor dit specifieke geval.

In deze sectie worden de belangrijkste punten beschreven waarmee u bestaande tabellen in Adobe Campaign kunt toewijzen en de configuratie die u wilt toepassen om leveringen uit te voeren op basis van een tabel. Tot slot beschrijft het hoe te om gebruikers van het vragen van interfaces te voorzien zoals praktisch die beschikbaar met de standaard ontvankelijke lijst. Om het materiaal te begrijpen dat in deze sectie wordt gepresenteerd, is een goede kennis van de beginselen van scherm- en schemaontwerp vereist.

## Aanbevelingen en beperkingen {#recommendations-and-limitations}

Het gebruiken van een externe ontvankelijke lijst heeft de volgende beperkingen:

* De Campagne van Adobe steunt veelvoudige ontvankelijke schema&#39;s, die als richtingsschema&#39;s worden bekend, verbonden aan de zelfde brede en/of trackinglogschema&#39;s. Dit kan anders leiden tot anomalieën in de afstemming van gegevens achteraf.

   In de onderstaande afbeelding ziet u de vereiste relationele structuur voor elk schema voor aangepaste ontvangers:
   ![](assets/custom_recipient_limitation.png)

   We raden aan:

   * De schema&#39;s **[!UICONTROL nms:BroadLogRcp]** en schema&#39;s aan de out-of-the-box **[!UICONTROL nms:TrackingLogRcp]** **[!UICONTROL nms:Recipientschema]**. Die twee logboeklijsten zouden niet aan een extra douane ontvankelijke lijst moeten worden verbonden.
   * Het bepalen van specifieke douanerelogboek en trackinglogschema&#39;s voor elk nieuw douane ontvankelijk schema. Dit kan automatisch worden gedaan wanneer vestiging de doelafbeelding, zie [Afbeelding](../../configuration/using/target-mapping.md)van het Doel.

* U kunt de standaard **[!UICONTROL Services and Subscriptions]** die in het product wordt aangeboden niet gebruiken.

   Dit betekent dat de in [dit punt](../../delivery/using/managing-subscriptions.md) beschreven algemene bewerking niet van toepassing is.

* De koppeling met de **[!UICONTROL visitor]** tabel werkt niet.

   Aldus, om de **[!UICONTROLSsociale module van de Marketing]** te gebruiken moet u de opslagstap vormen om de correcte lijst van verwijzingen te voorzien.

   Op dezelfde manier moet bij het gebruik van verwijzingsfuncties het standaard eerste berichtoverdrachtmodel worden aangepast.

* U kunt niet handmatig profielen toevoegen aan een lijst.

   Daarom is de in [dit deel](../../platform/using/creating-and-managing-lists.md) beschreven procedure niet van toepassing zonder een extra configuratie.

   >[!NOTE]
   >
   >Met behulp van workflows kunt u nog steeds lijsten met ontvangers maken. Zie Een profiellijst [maken met een workflow](../../configuration/using/creating-a-profile-list-with-a-workflow.md)voor meer informatie.

Wij adviseren ook controlerend de standaardwaarden die in de verschillende uit-van-de-doos configuraties worden gebruikt: afhankelijk van de gebruikte functies moeten verschillende aanpassingen worden uitgevoerd .

Bijvoorbeeld:

* Bepaalde standaardrapporten, met name die van **Interaction** en de **Mobiele Toepassingen** , moeten opnieuw worden ontwikkeld. Raadpleeg de sectie [Rapporten](../../configuration/using/managing-reports.md) beheren.
* De standaardconfiguraties voor bepaalde workflowactiviteiten verwijzen naar de standaardtabel met ontvangers (**[!UICONTROL nms:recipient]**): deze configuraties moeten worden veranderd wanneer gebruikt voor een externe ontvangerslijst. Raadpleeg de sectie [Workflows](../../configuration/using/managing-workflows.md) beheren.
* Het standaard **[!UICONTROL Unsubscription link]** verpersoonlijkingsblok moet worden aangepast.
* De doelafbeelding van de standaardleveringsmalplaatjes moet worden gewijzigd.
* V4-formulieren zijn niet compatibel met een tabel met externe ontvangers: u moet de toepassingen van het Web gebruiken.

