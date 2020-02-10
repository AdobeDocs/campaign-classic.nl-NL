---
title: Webtraceringsmodus
seo-title: Webtraceringsmodus
description: Webtraceringsmodus
seo-description: null
page-status-flag: never-activated
uuid: 51b889d3-28f8-480a-a614-10c8eb3128ac
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
discoiquuid: efeef54b-925d-4654-8601-52a73539b41f
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 912507f25c5bc3c1ca7121b0df8182176900f4c0

---


# Webtraceringsmodus{#web-tracking-mode}

Met Adobe Campaign kunt u een webtraceringsmodus selecteren waarmee wordt gedefinieerd hoe trackinglogbestanden in de toepassing worden verwerkt.

Er zijn drie beschikbare wijzen het volgen van het Web: **&quot;Sessiespatiëring&quot;**,**&quot;Permanente tracking&quot;** en **&quot;Anonieme tracking&quot;**.

![](assets/s_ncs_install_deployment_wiz_tracking_mode.png)

Elke modus heeft specifieke kenmerken. De &quot;permanente&quot;het volgen van het Web wijze omvat de kenmerken van de &quot;zitting&quot;Web het volgen wijze, terwijl de &quot;anonieme&quot;wijze de kenmerken van &quot;permanent&quot;en &quot;zitting&quot;wijzen omvat.

>[!CAUTION]
>
>De &quot;anonieme&quot;wijze van het Web het volgen wordt toegelaten door gebrek als het &quot;Leads&quot;pakket wordt toegelaten. In alle andere gevallen, wordt de &quot;zitting&quot;Web het volgen wijze toegelaten door gebrek.
>
>Op elk gewenst moment kan de standaardmodus worden gewijzigd in de wizard voor de implementatie van instanties.

Als u de **permanente web** - of **anonieme** traceringsmodus gebruikt, moet u een index toevoegen aan de kolom &quot;sourceID&quot; (uuid230) in de volgende tabellen (trackingLogXXX):

1. Identificeer de volgende tabel(len) waarop permanente tracering betrekking heeft.
1. Breid de schema&#39;s uit die deze lijsten aanpassen door de volgende lijnen toe te voegen:

```
<dbindex name="sourceId">
 <keyfield xpath="@sourceId"/>
</dbindex>
```

**De permanente** en **Anonieme** wijzen van het Web volgen omvatten twee opties: **Geforceerde levering** en **Laatste levering**.

Met de optie **Geforceerde levering** kunt u de id van de levering (@jobid) tijdens het bijhouden opgeven.

Met de optie **Laatste levering** kunt u het huidige trackinglogboek koppelen aan de laatst bijgehouden levering.

**Kenmerken van webtracking voor sessies:**

In deze modus wordt een trackinglogboek gemaakt voor mensen met een sessiecookie. Dit zijn mensen die op een URL hebben geklikt in een e-mail die door Adobe Campaign is verzonden, zodat we de volgende informatie kunnen bijhouden:

* Leverings-id
* Contactpersoon-id
* leveringslogboek
* permanent cookie (uuid230)
* URL bijhouden
* datum van het trackinglogboek

Met deze Web het volgen wijze, als een deel van de informatie mist, zal geen volgend logboek in de toepassing worden gecreeerd.

Deze modus is voordelig in termen van volume (beperkt aantal records in de tabel trackingLog) en berekening (geen afstemming).

**Kenmerken van de permanente webtraceringsmodus:**

Met deze webtraceringsmodus kunt u een traceringslogboek maken op basis van de aanwezigheid van het permanente uuuid230-cookie. Als een bezoeker zijn sessie sluit, gebruikt Adobe Campaign het permanente cookie om informatie over deze bestanden te herstellen op basis van eerdere trackinglogboeken. Adobe Campaign voegt een trackinglogbestand opnieuw in als de uuid230 van de huidige sessie dezelfde waarde heeft als een uuid230 die al in de tabel tracking is opgeslagen.

Dit betekent dat de bezoeker eerder in de Campagne van Adobe (via een levering) moet zijn geïdentificeerd om verzoening op uuid230 waarden toe te laten.

Standaard worden zoekopdrachten in vorige logbestanden voor bijhouden uitgevoerd in de tabel &quot;trackingLog&quot;. Als het Leads-pakket is ingeschakeld, zoekt Adobe Campagne voordat u de tabel &quot;trackingLog&quot; doorzoekt, naar de tabel &quot;innerLead&quot; voor vorige trackinglogrecords.

Deze methode is duur in termen van berekening tijdens logboekaanpassing.

**Kenmerken van de anonieme webtraceringsmodus:**

Met deze webtraceringsmodus kunt u een traceringslogboek ophalen dat is gekoppeld aan anonieme navigatie in Adobe Campaign. Er wordt automatisch een traceringslogboek gemaakt voor elke klik op een bijgehouden URL. Dit logboek heeft slechts de waarde van uuid230. Tijdens een marketing campagne, wordt een het volgen logboek gecreeerd automatisch met alle identiteitsinformatie (verwijs naar zitting het volgen). Adobe Campaign zoekt automatisch naar eerdere logs voor een waarde &quot;uuid230&quot; die gelijk is aan de waarde in het logbestand voor bijhouden van deze marketingcampagne. Als identieke waarden worden gevonden, worden alle vorige het volgen logboeken ingegaan met alle informatie van het het volgen van de marketingcampagne logboek.

Deze wijze is het duurst in termen van berekening en volume.

>[!NOTE]
>
>Als het **[!UICONTROL Leads]** pakket is geïnstalleerd, moet u hetzelfde doen voor de tabel met activiteiten (**crm:inkomendLead**)

Het volgende schema vat de functionaliteit van alle drie het volgen wijzen van het Web samen:

![](assets/s_ncs_install_deployment_wiz_tracking_schema_mode.png)

**Voorbeeld van permanente webtracering op basis van de laatste levering:**

Florence ontvangt een levering, opent de e-mail, klikt op de koppeling, doorbladert op de website van de detailhandel, maar koopt geen aankopen. De volgende dag keert Florence terug naar de winkelsite, bladert en koopt ze. Aangezien het permanent Web volgen (laatste levering) wordt toegelaten, zullen alle logboeken voor haar tweede bezoek aan de levering worden verbonden die aan haar de vorige dag werd verzonden.
