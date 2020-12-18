---
solution: Campaign Classic
product: campaign
title: Aangepaste tabel voor ontvangers
description: Aangepaste tabel voor ontvangers
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
translation-type: tm+mt
source-git-commit: c625b4109e2cb47446331cd009ff9827c8267c93
workflow-type: tm+mt
source-wordcount: '665'
ht-degree: 2%

---


# Aangepaste tabel voor ontvangers{#about-custom-recipient-table}

In deze sectie worden de beginselen beschreven voor het gebruik van een niet-standaardtabel voor ontvangers.

Adobe Campaign biedt standaard een standaard ontvangende tabel aan waaraan functies en processen buiten de box zijn gekoppeld. De standaard ontvankelijke lijst heeft een aantal vooraf bepaalde gebieden en lijsten die gemakkelijk kunnen worden uitgebreid gebruikend een uitbreidingslijst.

Als deze extensiemethode voldoende flexibiliteit biedt om een tabel uit te breiden, is het niet mogelijk het aantal velden of koppelingen in de tabel te beperken. Het gebruiken van een niet-standaardlijst, of &quot;externe ontvankelijke lijst&quot;, staat voor een grotere flexibiliteit toe maar vereist bepaalde voorzorgsmaatregelen wanneer het uitvoeren van het.

## Voorschriften {#precisions}

Met deze functionaliteit kan Adobe Campaign gegevens uit een externe database verwerken: deze gegevens worden gebruikt als een reeks profielen voor leveringen . Bij de implementatie van dit proces zijn verschillende definities nodig die relevant kunnen zijn voor de behoeften van de klant. Bijvoorbeeld:

* Geen updatestream van en naar de Adobe Campaign-database: gegevens uit deze tabel kunnen rechtstreeks worden bijgewerkt via de database-engine die de tabel host.
* Geen wijzigingen in de processen die op de bestaande database worden uitgevoerd.
* Een profieldatabase gebruiken met een niet-standaardstructuur: de mogelijkheid om profielen die in verschillende tabellen zijn opgeslagen, met verschillende structuren te leveren met behulp van één exemplaar.
* Geen wijzigingen of onderhoud vereist bij het bijwerken van de Adobe Campaign-database.
* De standaard ontvankelijke lijst is nutteloos als u niet de meeste lijstgebieden nodig hebt of als het gegevensbestandmalplaatje niet op de ontvangers wordt gecentreerd.
* Om efficiënt te zijn, is een lijst met weinig gebieden nodig als u een significant aantal profielen hebt. De standaard ontvangende tabel heeft te veel velden voor dit specifieke geval.

In deze sectie worden de belangrijkste punten beschreven waarmee u bestaande tabellen in Adobe Campaign kunt toewijzen en de configuratie die moet worden toegepast om leveringen uit te voeren op basis van een tabel. Tot slot beschrijft het hoe te om gebruikers van het vragen van interfaces te voorzien zoals praktisch die beschikbaar met de standaard ontvankelijke lijst. Om het materiaal te begrijpen dat in deze sectie wordt gepresenteerd, is een goede kennis van de beginselen van scherm- en schemaontwerp vereist.

## Recommendations en beperkingen {#recommendations-and-limitations}

Het gebruiken van een externe ontvankelijke lijst heeft de volgende beperkingen:

* Adobe Campaign steunt geen veelvoudige ontvankelijke schema&#39;s, weet als het richten van schema&#39;s, verbonden aan de zelfde brede en/of trackinglogschema&#39;s. Dit kan anders leiden tot anomalieën in de afstemming van gegevens achteraf.

   In de onderstaande afbeelding ziet u de vereiste relationele structuur voor elk schema voor aangepaste ontvangers:
   ![](assets/custom_recipient_limitation.png)

   We raden aan:

   * De schema&#39;s **[!UICONTROL nms:BroadLogRcp]** en **[!UICONTROL nms:TrackingLogRcp]** verwijzen naar de schema&#39;s **[!UICONTROL nms:Recipientschema]** die buiten de doos liggen. Die twee logboeklijsten zouden niet aan een extra douane ontvankelijke lijst moeten worden verbonden.
   * Het bepalen van specifieke douanerelogboek en trackinglogschema&#39;s voor elk nieuw douane ontvankelijk schema. Dit kan automatisch worden gedaan wanneer vestiging de doelafbeelding, zie [Doelafbeelding](../../configuration/using/target-mapping.md).

* U kunt de standaard **[!UICONTROL Services and Subscriptions]** niet gebruiken die in het product wordt aangeboden.

   Dit betekent dat de algemene bewerking die in [deze sectie](../../delivery/using/managing-subscriptions.md) wordt beschreven, niet van toepassing is.

* De koppeling met de tabel **[!UICONTROL visitor]** werkt niet.

   Als u dus de module **[!UICONTROL Social Marketing]** wilt gebruiken, moet u de opslagstap configureren om naar de juiste tabel te verwijzen.

   Op dezelfde manier moet bij het gebruik van verwijzingsfuncties het standaard eerste berichtoverdrachtmodel worden aangepast.

* U kunt niet handmatig profielen toevoegen aan een lijst.

   Daarom is de in [dit sectie](../../platform/using/creating-and-managing-lists.md) gedetailleerde procedure niet van toepassing zonder een extra configuratie.

   >[!NOTE]
   >
   >Met behulp van workflows kunt u nog steeds lijsten met ontvangers maken. Raadpleeg [Een profiellijst maken met een workflow](../../configuration/using/creating-a-profile-list-with-a-workflow.md) voor meer informatie.

Wij adviseren ook controlerend de standaardwaarden die in de verschillende uit-van-de-doos configuraties worden gebruikt: afhankelijk van de gebruikte functies moeten verschillende aanpassingen worden uitgevoerd .

Bijvoorbeeld:

* Bepaalde standaardrapporten, met name die welke worden aangeboden door **Interactie** en **Mobiele toepassingen** moeten opnieuw worden ontwikkeld. Raadpleeg de sectie [Rapporten beheren](../../configuration/using/managing-reports.md).
* De standaardconfiguraties voor bepaalde workflowactiviteiten verwijzen naar de standaardtabel met ontvangers (**[!UICONTROL nms:recipient]**): deze configuraties moeten worden veranderd wanneer gebruikt voor een externe ontvangerslijst. Raadpleeg de sectie [Workflows beheren](../../configuration/using/managing-workflows.md).
* Het standaardverpersoonlijkingsblok **[!UICONTROL Unsubscription link]** moet worden aangepast.
* De doelafbeelding van de standaardleveringsmalplaatjes moet worden gewijzigd.
* V4-formulieren zijn niet compatibel met een tabel met externe ontvangers: u moet webtoepassingen gebruiken.

