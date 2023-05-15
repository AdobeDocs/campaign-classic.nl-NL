---
product: campaign
title: Aanbiedingsplaatsingen maken
description: Aanbiedingsplaatsingen maken
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: interaction
content-type: reference
topic-tags: managing-environments
exl-id: bdda98f7-a083-4f3b-b691-c28ec79af780
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '981'
ht-degree: 1%

---

# Aanbiedingsplaatsingen maken{#creating-offer-spaces}



Ruimtevaartaanbod mag alleen worden gedaan door een **technisch beheerder** met toegang tot de submap van de aanbiedingsruimte. De ruimten van de aanbieding kunnen slechts in het ontwerpmilieu worden gecreeerd, en automatisch in het levende milieu tijdens aanbiedingsgoedkeuring worden gedupliceerd.

De inhoud van de catalogusaanbiedingen wordt gevormd in de aanbiedingsruimten. Standaard kan de inhoud de volgende velden bevatten: **[!UICONTROL Title]**, **[!UICONTROL Destination URL]**, **[!UICONTROL Image URL]**, **[!UICONTROL HTML content]** en **[!UICONTROL Text content]**. De gebiedsopeenvolging wordt gevormd in de aanbiedingsruimte.

Met geavanceerde parameters kunt u een contactidentificatietoets opgeven (die kan bestaan uit verschillende elementen, zoals de naam en het e-mailveld). Raadpleeg voor meer informatie de [Een geïdentificeerd aanbod presenteren](../../interaction/using/integration-via-javascript--client-side-.md#presenting-an-identified-offer) sectie.

De rendering HTML of XML wordt gemaakt via een renderfunctie. De volgorde van de velden die in de renderfunctie zijn gedefinieerd, moet gelijk zijn aan de volgorde die in de inhoud is geconfigureerd.

![](assets/offer_space_create_009.png)

Pas het volgende proces toe om een nieuwe aanbiedingsruimte te maken:

1. Ga naar de lijst met aanbiedingsruimten en klik op **[!UICONTROL New]**.

   ![](assets/offer_space_create_001.png)

1. Selecteer het kanaal u wilt gebruiken en het etiket van de aanbiedingsruimte veranderen.

   ![](assets/offer_space_create_002.png)

1. Controleer de **[!UICONTROL Enable unitary mode]** vak als een van de volgende gevallen op u van toepassing is:

   * U gebruikt Interactie met het Centrum van het Bericht
   * U gebruikt de eenheidswijze van de Interactie (binnenkomende interactie)

1. Ga naar de **[!UICONTROL Content field]** venster en klik op **[!UICONTROL Add]**.

   ![](assets/offer_space_create_003.png)

1. Ga naar de **[!UICONTROL Content]** en selecteer de velden in de volgende volgorde: **[!UICONTROL Title]** vervolgens **[!UICONTROL Image URL]** vervolgens **[!UICONTROL HTML content]** vervolgens **[!UICONTROL Destination URL]**.

   ![](assets/offer_space_create_004.png)

1. Controleer de **[!UICONTROL Required]** om elk veld verplicht te maken.

   >[!NOTE]
   >
   >Deze configuratie wordt gebruikt bij de voorproef en maakt aanbiedingsruimten ongeldig wanneer het publiceren als één van de verplichte elementen van de betrokken aanbieding mist. Als een aanbieding echter al live is op een aanbiedingsruimte, worden deze criteria niet in aanmerking genomen.

   ![](assets/offer_space_create_005.png)

1. Klikken **[!UICONTROL Edit functions]** om een renderfunctie te maken.

   Deze functies worden gebruikt om aanbiedingsvertegenwoordiging op een aanbiedingsruimte te produceren. Er zijn verschillende mogelijke indelingen: HTML of tekst voor uitgaande interacties en XML voor binnenkomende interacties.

   ![](assets/offer_space_create_006.png)

1. Ga naar de **[!UICONTROL HTML rendering]** en selecteert u **[!UICONTROL Overload the HTML rendering function]**.
1. Voeg uw renderfunctie in.

   ![](assets/offer_space_create_007.png)

Indien nodig, kunt u de XML-renderfuncties voor binnenkomende interacties te veel laden. U kunt ook functies voor het renderen van HTML en tekst overladen voor uitgaande interacties. Raadpleeg voor meer informatie hierover [Over binnenkomende kanalen](../../interaction/using/about-inbound-channels.md).

## Voorzettingsstatussen voorstellen {#offer-proposition-statuses}

Een aanbiedingsvoorstel kan verschillende statussen hebben afhankelijk van de interactie met de doelpopulatie. De interactie komt met een reeks waarden die op het aanbiedingsvoorstel tijdens zijn levenscyclus kunnen worden toegepast. Nochtans, zult u het platform moeten vormen zodat de status verandert wanneer het aanbiedingsvoorstel wordt gecreeerd en wordt goedgekeurd.

>[!NOTE]
>
>De status van het voorstel wordt niet onmiddellijk bijgewerkt. Deze wordt uitgevoerd door de workflow voor het bijhouden van gegevens, die elk uur wordt geactiveerd.

### Statuslijst {#status-list}

De interactie komt met de volgende waarden die kunnen worden gebruikt om de status van een aanbiedingsvoorstel te kwalificeren:

* **[!UICONTROL Accepted]**.
* **[!UICONTROL Scheduled]**.
* **[!UICONTROL Generated]**.
* **[!UICONTROL Interested]**.
* **[!UICONTROL Presented]**.
* **[!UICONTROL Rejected]**.

Deze waarden worden niet standaard toegepast: zij moeten worden gevormd.

>[!NOTE]
>
>De status van een aanbiedingsvoorstel wordt automatisch gewijzigd in &quot;Presenteerd&quot; als de aanbieding gekoppeld is aan een levering met de status &quot;Verzonden&quot;.

### De status configureren wanneer het voorstel wordt gemaakt {#configuring-the-status-when-the-proposition-is-created}

Wanneer een aanbiedingsvoorstel door de interactiemotor wordt gecreeerd wordt zijn status veranderd, of het een binnenkomende of een uitgaande interactie is. De keuze tussen deze twee waarden is afhankelijk van de manier waarop de aanbiedingsruimten zijn geconfigureerd in het dialoogvenster **[!UICONTROL Design]** milieu

Voor elke ruimte, kunt u de status vormen u wilt toepassen wanneer een voorstel wordt gecreeerd, afhankelijk van de informatie u in de aanbiedingsrapporten wilt tonen.

Hiervoor gebruikt u het volgende proces:

1. Ga naar de **[!UICONTROL Storage]** van de gewenste ruimte.
1. Selecteer de status die u op het voorstel wilt toepassen wanneer het wordt gecreeerd.

   ![](assets/offer_update_status_001.png)

### De status configureren wanneer het voorstel wordt geaccepteerd {#configuring-the-status-when-the-proposition-is-accepted}

Zodra een aanbiedingsvoorstel is goedgekeurd, kunt u één van de waarden gebruiken die door gebrek worden verstrekt om de nieuwe status van het voorstel te vormen. De update is effectief wanneer een ontvanger op een koppeling in de aanbieding klikt, die de interactie-engine oproept.

Hiervoor gebruikt u het volgende proces:

1. Ga naar de **[!UICONTROL Storage]** van de gewenste ruimte.
1. Selecteer de status die u op het voorstel wilt toepassen wanneer het wordt goedgekeurd.

   ![](assets/offer_update_status_002.png)

**Binnenkomende interactie**

De **[!UICONTROL Storage]** kunt u statussen definiëren voor **voorgesteld** en **aanvaard** alleen voorstellen. Voor binnenkomende interactie, zou de status van aanbiedingsvoorstellen direct in URL voor het roepen van de aanbiedingsmotor, eerder dan door de interface moeten worden gespecificeerd. Op deze manier kunt u opgeven welke status in andere gevallen moet worden toegepast, bijvoorbeeld als een voorstel voor een aanbieding wordt afgewezen.

```
<BASE_URL>?a=UpdateStatus&p=<PRIMARY_KEY_OF_THE_PROPOSITION>&st=<NEW_STATUS_OF_THE_PROPOSITION>&r=<REDIRECT_URL>
```

Bijvoorbeeld, het voorstel (herkenningsteken **40004**) die overeenkomt met de **Binnenlandse verzekering** voorstel weergegeven op de **Neobank** site bevat de volgende URL:

```
<BASE_URL>?a=UpdateStatus&p=<40004>&st=<3>&r=<"http://www.neobank.com/insurance/subscribe.html">
```

Zodra een bezoeker op het aanbod klikt, en dus op de URL, wordt het **[!UICONTROL Accepted]** status (waarde) **3**) wordt toegepast op het voorstel en de bezoeker wordt omgeleid naar een nieuwe pagina van de **Neobank** plaats om de verzekeringsovereenkomst te sluiten.

>[!NOTE]
>
>Als u een andere status in de URL wilt opgeven (bijvoorbeeld als een aanbiedingsvoorstel wordt afgewezen), gebruikt u de waarde die overeenkomt met de gewenste status. Voorbeeld: **[!UICONTROL Rejected]** = &quot;5&quot;, **[!UICONTROL Presented]** = &quot;1&quot; enzovoort.
>
>Statussen en hun waarden kunnen worden opgehaald in het dialoogvenster **[!UICONTROL Offer propositions (nms)]** gegevensschema. Raadpleeg [deze pagina](../../configuration/using/data-schemas.md) voor meer informatie.

**Uitgaande interactie**

In het geval van een uitgaande interactie, kunt u automatisch toepassen **[!UICONTROL Interested]** status aan een voorstel als de levering een koppeling bevat. Voeg eenvoudig de **_urlType=&quot;11&quot;** waarde voor de koppeling:

```
<a _urlType="11" href="<DEST_URL>">Link inserted into the delivery</a>
```

## Voorvertoning aanbod per ruimte {#offer-preview-per-space}

Op dit tabblad kunt u de aanbiedingen bekijken waarvoor de ontvanger in aanmerking komt via een gekozen methode. In het onderstaande voorbeeld komt de begunstigde in aanmerking voor drie voorstellen per post.

![](assets/offer_space_overview_002.png)

Als een ontvanger niet in aanmerking komt voor een voorstel, wordt dit weergegeven in de voorvertoning.

![](assets/offer_space_overview_001.png)

In de voorvertoning kunnen contexten worden genegeerd wanneer deze beperkt zijn tot een spatie. Dit is het geval wanneer het interactieschema is uitgebreid om velden toe te voegen waarnaar in een ruimte wordt verwezen met een binnenkomend kanaal (zie voor meer informatie hierover [Extensievoorbeeld](../../interaction/using/extension-example.md)).
