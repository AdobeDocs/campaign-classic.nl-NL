---
title: Een aanbieding maken
seo-title: Een aanbieding maken
description: Een aanbieding maken
seo-description: null
page-status-flag: never-activated
uuid: 9e8b0351-e2a5-4043-be86-e275d2f849ea
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: managing-an-offer-catalog
discoiquuid: 010c88f4-9444-448f-bb7b-7191517d2e23
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 215e4d1ca78938b38b53cae0357612deebf7727b

---


# Een aanbieding maken{#creating-an-offer}

## De aanbieding maken {#creating-the-offer}

Voer de volgende stappen uit om een aanbieding te maken:

1. Ga naar het **[!UICONTROL Campaigns]** universum en klik op de **[!UICONTROL Offers]** link.

   ![](assets/offer_create_001.png)

1. Klik op de **[!UICONTROL Create]** knop.

   ![](assets/offer_create_005.png)

1. Wijzig het label en selecteer de categorie waartoe de aanbieding moet behoren.

   ![](assets/offer_create_002.png)

1. Klik **[!UICONTROL Save]** om het voorstel te maken.

   ![](assets/offer_create_003.png)

   De aanbieding is beschikbaar in het platform en zijn inhoud kan worden gevormd.

   ![](assets/offer_create_004.png)

## Geschiktheid van aanbieding configureren {#configuring-offer-eligibility}

Definieer op het **[!UICONTROL Eligibility]** tabblad de periode waarin de aanbieding geldig is en kan worden weergegeven, de filters die op het doel en het aanbiedingsgewicht moeten worden toegepast.

### Vaststelling van de subsidiabiliteitsperiode van een aanbieding {#defining-the-eligibility-period-of-an-offer}

Om de subsidiabiliteitsperiode van de aanbieding te bepalen, gebruikt u de vervolgkeuzelijsten en selecteert u een begin- en einddatum in de kalender.

![](assets/offer_eligibility_create_002.png)

Buiten deze datums wordt de aanbieding niet geselecteerd door de interactie-engine. Als u ook de toelatingsdata voor de categorie van aanbiedingen hebt gevormd, zal de meest beperkende periode van toepassing zijn.

### Filters op het doel {#filters-on-the-target}

U kunt filters op het aanbiedingsdoel toepassen.

Klik hiertoe op de **[!UICONTROL Edit query]** koppeling en selecteer het filter dat u wilt toepassen. (Zie [deze sectie](../../platform/using/steps-to-create-a-query.md#step-4---filter-data)).

![](assets/offer_eligibility_create_003.png)

Als er al vooraf gedefinieerde filters zijn gemaakt, kunt u deze selecteren in de lijst met gebruikersfilters. Zie Vooraf gedefinieerde filters [maken voor meer informatie over dit onderwerp](../../interaction/using/creating-predefined-filters.md).

![](assets/offer_eligibility_create_004.png)

### Aanbiedingsgewicht {#offer-weight}

Om de motor in staat te stellen tussen verscheidene aanbiedingen te beslissen dat het doel verkiesbaar is, moet u één of meerdere gewichten aan de aanbieding toewijzen. U kunt filters op het doel indien nodig ook toepassen of de aanbiedingsruimte beperken waarop het gewicht van toepassing is. Een aanbod met een groter gewicht krijgt de voorkeur boven een aanbod met minder gewicht.

U kunt veelvoudige gewichten voor de zelfde aanbieding vormen, bijvoorbeeld om sup-periodes, specifieke doelstellingen of zelfs een aanbiedingsruimte te onderscheiden.

Bijvoorbeeld, kan een aanbieding een gewicht van A voor contacten hebben tussen 18 en 25 jaar en een gewicht van B voor contacten boven dat gamma. Als een aanbieding de hele zomer in aanmerking komt, kan zij ook een gewicht van A in juli en een gewicht van B in augustus hebben.

>[!NOTE]
>
>Het toegewezen gewicht kan tijdelijk worden gewijzigd op basis van de parameters van de categorie waartoe de aanbieding behoort. Zie Aanbiedingscategorieën [maken voor meer informatie](../../interaction/using/creating-offer-categories.md).

Voer de volgende stappen uit om een dikte in een aanbieding te maken:

1. Klik **[!UICONTROL Add]**.

   ![](assets/offer_weight_create_001.png)

1. Wijzig het label en wijs een gewicht toe. Standaard is dit 1.

   ![](assets/offer_weight_create_006.png)

   >[!CAUTION]
   >
   >Indien geen gewicht wordt opgegeven (0), wordt het streefcijfer niet in aanmerking genomen voor de aanbieding.

1. Als u het gewicht gedurende een bepaalde periode wilt toepassen, definieert u de toelatingsdata.

   ![](assets/offer_weight_create_002.png)

1. Beperk zo nodig het gewicht tot een specifieke aanbiedingsruimte.

   ![](assets/offer_weight_create_003.png)

1. Pas een filter toe op een doel.

   ![](assets/offer_weight_create_004.png)

1. Klik **[!UICONTROL OK]** om de dikte op te slaan.

   ![](assets/offer_weight_create_005.png)

   >[!NOTE]
   >
   >Als een doel in aanmerking komt voor meerdere gewichten voor een geselecteerde aanbieding, behoudt de motor het beste (hoogste) gewicht. Bij het oproepen van de aanbiedingsmotor, wordt een aanbieding een maximum van eens per contact geselecteerd.

### Een samenvatting van de regels inzake de subsidiabiliteit van aanbiedingen {#a-summary-of-offer-eligibility-rules}

Zodra de configuratie is voltooid, zal een samenvatting van de subsidiabiliteitsregels beschikbaar zijn op het biederdashboard.

Klik op de **[!UICONTROL Schedule and eligibility rules]** koppeling om deze weer te geven.

![](assets/offer_eligibility_create_005.png)

## De inhoud van de aanbieding maken {#creating-the-offer-content}

1. Klik op het **[!UICONTROL Edit]** tabblad en klik vervolgens op het **[!UICONTROL Content]** tabblad.

   ![](assets/offer_content_create_001.png)

1. Vul de verschillende velden van de inhoud van de aanbieding in.

   * **[!UICONTROL Title]** : Geef de titel op die je wilt maken en die je in je voorstel wilt opnemen. Waarschuwing: dit verwijst niet naar het label van de aanbieding, dat in het **[!UICONTROL General]** lusje wordt bepaald.
   * **[!UICONTROL Destination URL]** : Geef de URL van je voorstel op. Om correct te worden verwerkt, moet het met &quot;http://&quot;of &quot;https://&quot;beginnen.
   * **[!UICONTROL Image URL]** : Geef een URL of een toegangspad op naar de afbeelding van uw aanbieding.
   * **[!UICONTROL HTML content]** / **[!UICONTROL Text content]** : Voer de tekst van je voorstel in op het tabblad dat je wilt. Voor het genereren van reeksspatiëring **[!UICONTROL HTML content]** moet de URL bestaan uit HTML-elementen die kunnen worden ingesloten in een `<div>` tekstelement. Het resultaat van een `<table>` element in de HTML-pagina is bijvoorbeeld als volgt:

   ```
      <div> 
       <table>
        <tr>
         <th>Month</th>
         <th>Savings</th>   
        </tr>   
        <tr>    
         <td>January</td>
         <td>$100</td>   
        </tr> 
       </table> 
      </div>
   ```

   Het bepalen van goedkeurings URL wordt voorgesteld in het [Vormen van de status wanneer het voorstel wordt goedgekeurd](../../interaction/using/creating-offer-spaces.md#configuring-the-status-when-the-proposition-is-accepted) sectie.

   ![](assets/offer_content_create_002.png)

   Als u de vereiste velden wilt zoeken zoals deze tijdens de configuratie van de aanbiedingsruimte zijn gedefinieerd, klikt u op de **[!UICONTROL Content definitions]** koppeling om de lijst weer te geven. Raadpleeg [Aanbiedingsruimten](../../interaction/using/creating-offer-spaces.md)maken voor meer informatie hierover.

   ![](assets/offer_content_create_003.png)

   In dit voorbeeld moet de aanbieding een titel, een afbeelding, HTML-inhoud en een doel-URL bevatten.

## Voorbeeld van de aanbieding bekijken {#previewing-the-offer}

Zodra de inhoud van uw voorstel is geconfigureerd, kunt u een voorbeeld van het voorstel bekijken zoals het voor de ontvanger wordt weergegeven. Dit doet u als volgt:

1. Klik op het **[!UICONTROL Preview]** tabblad.

   ![](assets/offer_preview_create_001.png)

1. Selecteer de representatie van het voorstel dat u wilt bekijken.

   ![](assets/offer_preview_create_002.png)

1. Als u de inhoud van de aanbieding hebt gepersonaliseerd, selecteer het doel van de aanbieding om personalisatie te bekijken.

   ![](assets/offer_preview_create_003.png)

## Het creëren van een hypothese over een aanbieding {#creating-a-hypothesis-on-an-offer}

Je kunt hypothesen maken voor je voorstellen. Hiermee kunt u de gevolgen van uw aanbiedingen voor de aankopen van het betrokken product bepalen.

>[!NOTE]
>
>Deze hypothesen worden uitgevoerd via Response Manager. Controleer uw licentieovereenkomst.

Op hun **[!UICONTROL Measure]** tabblad wordt verwezen naar de hypothesen die zijn uitgevoerd op een aanbiedingsvoorstel.

Het maken van hypothesen wordt beschreven in [deze pagina](../../campaign/using/about-response-manager.md).

![](assets/offer_hypothesis_001.png)

