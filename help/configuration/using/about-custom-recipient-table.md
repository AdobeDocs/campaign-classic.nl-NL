---
product: campaign
title: Aangepaste tabel voor ontvangers
description: Aangepaste tabel voor ontvangers
feature: Configuration, Custom Resources
role: User, Data Engineer, Developer
badge-v7: label="v7" type="Informative" tooltip="Is van toepassing op Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
exl-id: d8cea496-b3f3-420a-bf6e-b7cbb321b30d
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '679'
ht-degree: 2%

---

# Een aangepaste tabel voor ontvangers gebruiken{#about-custom-recipient-table}

In deze sectie worden de beginselen beschreven voor het gebruik van een aangepaste (of externe) tabel voor ontvangers.

Adobe Campaign biedt standaard een ingebouwde tabel voor ontvangers waaraan functies en processen buiten de box zijn gekoppeld. De ingebouwde ontvankelijke lijst heeft een aantal vooraf bepaalde gebieden en lijsten die gemakkelijk kunnen worden uitgebreid gebruikend een uitbreidingslijst.

Als deze extensiemethode voldoende flexibiliteit biedt om een tabel uit te breiden, is het niet mogelijk het aantal velden of koppelingen in de tabel te beperken. Het gebruiken van een niet-standaardlijst, of &quot;externe ontvankelijke lijst&quot;, staat voor een grotere flexibiliteit toe maar vereist bepaalde voorzorgsmaatregelen wanneer het uitvoeren van het.

Met deze functionaliteit kan Adobe Campaign gegevens uit een externe database verwerken: deze gegevens worden gebruikt als een set profielen voor leveringen. Bij de implementatie van dit proces zijn verschillende definities nodig die relevant kunnen zijn voor de behoeften van de klant. Bijvoorbeeld:

* Geen updatestroom van en naar de Adobe Campaign-database: gegevens uit deze tabel kunnen rechtstreeks worden bijgewerkt via de database-engine die de database host.
* Geen wijzigingen in de processen die op de bestaande database worden uitgevoerd.
* Een profieldatabase met een niet-standaardstructuur gebruiken: mogelijkheid om profielen die zijn opgeslagen in verschillende tabellen met verschillende structuren, met één exemplaar te leveren.
* Geen wijzigingen of onderhoud vereist bij het bijwerken van de Adobe Campaign-database.
* De ingebouwde ontvankelijke lijst is nutteloos als u niet de meeste lijstgebieden nodig hebt of als het gegevensbestandmalplaatje niet op de ontvangers wordt gecentreerd.
* Om efficiënt te zijn, is een lijst met weinig gebieden nodig als u een significant aantal profielen hebt. De ingebouwde ontvankelijke lijst heeft teveel gebieden voor dit specifieke geval.

In deze sectie worden de belangrijkste punten beschreven waarmee u bestaande tabellen in Adobe Campaign kunt toewijzen en de configuratie die moet worden toegepast om leveringen uit te voeren op basis van een tabel. Tot slot beschrijft het hoe te om gebruikers van het vragen van interfaces te voorzien zoals praktisch die beschikbaar met de ingebouwde ontvankelijke lijst. Om het materiaal te begrijpen dat in deze sectie wordt gepresenteerd, is een goede kennis van de beginselen van scherm- en schemaontwerp vereist.

## Recommendations en beperkingen {#recommendations-and-limitations}

Het gebruiken van een douane ontvankelijke lijst heeft de volgende beperkingen:

* Adobe Campaign steunt geen veelvoudige ontvankelijke schema&#39;s, weet als het richten van schema&#39;s, verbonden aan de zelfde brede en/of trackinglogschema&#39;s. Dit kan anders leiden tot anomalieën in de afstemming van gegevens achteraf.

  In de onderstaande afbeelding ziet u de vereiste relationele structuur voor elk schema voor aangepaste ontvangers:
  ![](assets/custom_recipient_limitation.png)

  We raden aan:

   * De **[!UICONTROL nms:BroadLogRcp]** en **[!UICONTROL nms:TrackingLogRcp]** schema&#39;s voor de uit-van-de-doos **[!UICONTROL nms:Recipientschema]**. Die twee logboeklijsten zouden niet aan een extra douane ontvankelijke lijst moeten worden verbonden.
   * Het bepalen van specifieke douanerelogboek en trackinglogschema&#39;s voor elk nieuw douane ontvankelijk schema. Dit kan automatisch worden gedaan wanneer het plaatsen van de doelafbeelding, zie [Doeltoewijzing](../../configuration/using/target-mapping.md).

* U kunt de standaard niet gebruiken **[!UICONTROL Services and Subscriptions]** aangeboden in het product.

  Dit betekent dat de in [deze sectie](../../delivery/using/managing-subscriptions.md) is niet van toepassing.

* De koppeling met de **[!UICONTROL visitor]** tabel werkt niet.

  Om de **[!UICONTROL Social Marketing]** moet u de opslagstap configureren om naar de juiste tabel te verwijzen.

  Op dezelfde manier moet bij het gebruik van verwijzingsfuncties het standaard eerste berichtoverdrachtmodel worden aangepast.

* U kunt niet handmatig profielen toevoegen aan een lijst.

  Daarom wordt de in [deze sectie](../../platform/using/creating-and-managing-lists.md) is niet van toepassing zonder een extra configuratie.

  >[!NOTE]
  >
  >Met behulp van workflows kunt u nog steeds lijsten met ontvangers maken. Raadpleeg voor meer informatie hierover [Een profiellijst maken met een workflow](../../configuration/using/creating-a-profile-list-with-a-workflow.md).

We raden ook aan de standaardwaarden te controleren die worden gebruikt in de verschillende configuraties buiten de box: afhankelijk van de gebruikte functies moeten verschillende aanpassingen worden uitgevoerd.

Bijvoorbeeld:

* Bepaalde standaardverslagen, met name die van **Interactie** en de **Mobiele toepassingen** moet worden vernieuwd. Zie de [Rapporten beheren](../../configuration/using/managing-reports.md) sectie.
* De standaardconfiguraties voor bepaalde workflowactiviteiten verwijzen naar de standaardtabel met ontvangers (**[!UICONTROL nms:recipient]**): deze configuraties moeten worden gewijzigd wanneer deze worden gebruikt voor een tabel met externe ontvangers. Zie de [Workflows beheren](../../configuration/using/managing-workflows.md) sectie.
* De norm **[!UICONTROL Unsubscription link]** het personaliseringsblok moet worden aangepast .
* De doelafbeelding van de standaardleveringsmalplaatjes moet worden gewijzigd.
* V4-formulieren zijn niet compatibel met een tabel met externe ontvangers: u moet webtoepassingen gebruiken.
