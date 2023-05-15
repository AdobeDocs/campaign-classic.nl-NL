---
product: campaign
title: Een aanbieding maken
description: Een aanbieding maken
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: interaction
content-type: reference
topic-tags: managing-an-offer-catalog
exl-id: c6dd2709-06e3-4227-bbec-99f3d80144fe
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '803'
ht-degree: 3%

---

# Een aanbieding maken{#creating-an-offer}



## De aanbieding maken {#creating-the-offer}

Voer de volgende stappen uit om een aanbieding te maken:

1. Ga naar de **[!UICONTROL Campaigns]** en klik op de knop **[!UICONTROL Offers]** koppeling.

   ![](assets/offer_create_001.png)

1. Klik op de knop **[!UICONTROL Create]**.

   ![](assets/offer_create_005.png)

1. Wijzig het label en selecteer de categorie waartoe de aanbieding moet behoren.

   ![](assets/offer_create_002.png)

1. Klikken **[!UICONTROL Save]** om het voorstel te maken.

   ![](assets/offer_create_003.png)

   De aanbieding is beschikbaar in het platform en zijn inhoud kan worden gevormd.

   ![](assets/offer_create_004.png)

## Geschiktheid van aanbieding configureren {#configuring-offer-eligibility}

In de **[!UICONTROL Eligibility]** , bepaalt u voor welke periode de aanbieding geldig is en kan worden gepresenteerd, welke filters op het doel en het aanbiedingsgewicht moeten worden toegepast.

### Vaststelling van de subsidiabiliteitsperiode van een aanbieding {#defining-the-eligibility-period-of-an-offer}

Om de subsidiabiliteitsperiode van de aanbieding te bepalen, gebruikt u de vervolgkeuzelijsten en selecteert u een begin- en einddatum in de kalender.

![](assets/offer_eligibility_create_002.png)

Buiten deze datums wordt de aanbieding niet geselecteerd door de interactie-engine. Als u ook de toelatingsdata voor de categorie van aanbiedingen hebt gevormd, zal de meest beperkende periode van toepassing zijn.

### Filters op het doel {#filters-on-the-target}

U kunt filters op het aanbiedingsdoel toepassen.

Om dit te doen, klik **[!UICONTROL Edit query]** en selecteer het filter dat u wilt toepassen. (Zie [deze sectie](../../platform/using/steps-to-create-a-query.md#step-4---filter-data)).

![](assets/offer_eligibility_create_003.png)

Als er al vooraf gedefinieerde filters zijn gemaakt, kunt u deze selecteren in de lijst met gebruikersfilters. Raadpleeg voor meer informatie hierover [Vooraf gedefinieerde filters maken](../../interaction/using/creating-predefined-filters.md).

![](assets/offer_eligibility_create_004.png)

### Aanbiedingsgewicht {#offer-weight}

Om de motor in staat te stellen tussen verscheidene aanbiedingen te beslissen dat het doel verkiesbaar is, moet u één of meerdere gewichten aan de aanbieding toewijzen. U kunt filters op het doel indien nodig ook toepassen of de aanbiedingsruimte beperken waarop het gewicht van toepassing is. Een aanbod met een groter gewicht krijgt de voorkeur boven een aanbod met minder gewicht.

U kunt veelvoudige gewichten voor de zelfde aanbieding vormen, bijvoorbeeld om sup-periodes, specifieke doelstellingen of zelfs een aanbiedingsruimte te onderscheiden.

Bijvoorbeeld, kan een aanbieding een gewicht van A voor contacten hebben tussen 18 en 25 jaar en een gewicht van B voor contacten boven dat gamma. Als een aanbieding de hele zomer in aanmerking komt, kan zij ook een gewicht van A in juli en een gewicht van B in augustus hebben.

>[!NOTE]
>
>Het toegewezen gewicht kan tijdelijk worden gewijzigd op basis van de parameters van de categorie waartoe de aanbieding behoort. Raadpleeg voor meer informatie hierover [Categorieën voorstellen maken](../../interaction/using/creating-offer-categories.md).

Voer de volgende stappen uit om een dikte in een aanbieding te maken:

1. Klik op **[!UICONTROL Add]**.

   ![](assets/offer_weight_create_001.png)

1. Wijzig het label en wijs een gewicht toe. Standaard is dit 1.

   ![](assets/offer_weight_create_006.png)

   >[!IMPORTANT]
   >
   >Indien geen gewicht wordt opgegeven (0), wordt het streefcijfer niet in aanmerking genomen voor de aanbieding.

1. Als u het gewicht gedurende een bepaalde periode wilt toepassen, definieert u de toelatingsdata.

   ![](assets/offer_weight_create_002.png)

1. Beperk zo nodig het gewicht tot een specifieke aanbiedingsruimte.

   ![](assets/offer_weight_create_003.png)

1. Pas een filter toe op een doel.

   ![](assets/offer_weight_create_004.png)

1. Klikken **[!UICONTROL OK]** om het gewicht te verlagen.

   ![](assets/offer_weight_create_005.png)

   >[!NOTE]
   >
   >Als een doel in aanmerking komt voor meerdere gewichten voor een geselecteerde aanbieding, behoudt de motor het beste (hoogste) gewicht. Bij het oproepen van de aanbiedingsmotor, wordt een aanbieding een maximum van eens per contact geselecteerd.

### Samenvatting van de regels inzake de subsidiabiliteit van aanbiedingen {#a-summary-of-offer-eligibility-rules}

Zodra de configuratie is voltooid, zal een samenvatting van de subsidiabiliteitsregels beschikbaar zijn op het biederdashboard.

Klik op de knop **[!UICONTROL Schedule and eligibility rules]** koppeling.

![](assets/offer_eligibility_create_005.png)

## De inhoud van de aanbieding maken {#creating-the-offer-content}

1. Klik op de knop **[!UICONTROL Edit]** en klikt u op de knop **[!UICONTROL Content]** tab.

   ![](assets/offer_content_create_001.png)

1. Vul de verschillende velden van de inhoud van de aanbieding in.

   * **[!UICONTROL Title]** : Geef de titel op die je wilt maken en die je in je voorstel wilt opnemen. Waarschuwing: dit verwijst niet naar het label van de aanbieding , dat in het **[!UICONTROL General]** tab.
   * **[!UICONTROL Destination URL]** : Geef de URL van je voorstel op. Om correct te worden verwerkt, moet het met &quot;http://&quot;of &quot;https://&quot;beginnen.
   * **[!UICONTROL Image URL]** : Geef een URL of een toegangspad op naar de afbeelding van uw aanbieding.
   * **[!UICONTROL HTML content]** / **[!UICONTROL Text content]** : Voer de tekst van je voorstel in op het tabblad dat je wilt. Om het volgen te produceren, **[!UICONTROL HTML content]** moet bestaan uit HTML-elementen die kunnen worden ingesloten in een `<div>` type-element. Het resultaat van bijvoorbeeld een `<table>` Het element op de pagina HTML is als volgt:

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

   Het definiëren van de acceptatie-URL wordt weergegeven in het dialoogvenster [De status configureren wanneer het voorstel wordt geaccepteerd](../../interaction/using/creating-offer-spaces.md#configuring-the-status-when-the-proposition-is-accepted) sectie.

   ![](assets/offer_content_create_002.png)

   Om de vereiste gebieden te vinden aangezien zij tijdens de configuratie van de aanbiedingsruimte werden bepaald, klik **[!UICONTROL Content definitions]** koppeling om de lijst weer te geven. Raadpleeg voor meer informatie hierover [Aanbiedingsruimten maken](../../interaction/using/creating-offer-spaces.md).

   ![](assets/offer_content_create_003.png)

   In dit voorbeeld moet de aanbieding een titel, een afbeelding, HTML-inhoud en een doel-URL bevatten.

## Voorbeeld van de aanbieding bekijken {#previewing-the-offer}

Zodra de inhoud van uw voorstel is geconfigureerd, kunt u een voorbeeld van het voorstel bekijken zoals het voor de ontvanger wordt weergegeven. Dit doet u als volgt:

1. Klik op de knop **[!UICONTROL Preview]** tab.

   ![](assets/offer_preview_create_001.png)

1. Selecteer de representatie van het voorstel dat u wilt bekijken.

   ![](assets/offer_preview_create_002.png)

1. Als u de inhoud van de aanbieding hebt gepersonaliseerd, selecteer het doel van de aanbieding om personalisatie te bekijken.

   ![](assets/offer_preview_create_003.png)

## Het creëren van een hypothese over een aanbieding {#creating-a-hypothesis-on-an-offer}

Je kunt hypothesen maken voor je voorstellen. Hiermee kunt u de gevolgen van uw aanbiedingen voor de aankopen van het betrokken product bepalen.

>[!NOTE]
>
>Deze hypothesen worden uitgevoerd via Response Manager. Controleer hiervoor uw licentieovereenkomst.

In hun voorstel wordt verwezen naar de hypothesen die op een aanbiedingsvoorstel zijn toegepast **[!UICONTROL Measure]** tab.

Het maken van hypothesen wordt nader beschreven in [deze pagina](../../response/using/about-response-manager.md).

![](assets/offer_hypothesis_001.png)
