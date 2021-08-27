---
product: campaign
title: Operatorprofielen
description: Operatorprofielen
audience: interaction
content-type: reference
topic-tags: managing-environments
exl-id: e11fb28c-d530-45a2-862a-ff1c20975577
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 5%

---

# Operatorprofielen{#operator-profiles}

![](../../assets/v7-only.svg)

Er zijn twee soorten operatoren die Interactie gebruiken: bieden managers en leveringsmanagers aan. Ze hebben elk specifieke rechten die ze slechts toegang geven tot bepaalde delen van de boom en het platform.

* **[!UICONTROL Offer manager]** : aanbiedingen maken en onderhouden. Als aanbiedingen worden gebruikt in de workflow, moet de operator zich in de operatorgroep **[!UICONTROL Administrator]** of **[!UICONTROL Offer managers]** bevinden om de workflow uit te voeren.
* **[!UICONTROL Delivery manager]** : goedkeurt en gebruikt voorstellen

De stappen voor het maken van operatoren die specifiek zijn voor Interactie zijn identiek aan de stappen die worden gebruikt om alle andere operatoren op het platform te maken. Raadpleeg [deze sectie](../../platform/using/access-management.md) voor meer informatie. De rechten worden gevormd tijdens de verwezenlijking van de exploitant.

## Aanbiedingsmanager {#offer-manager}

1. Maak een nieuwe operator.
1. Ga naar het **[!UICONTROL Groups and named rights]** venster, klik **[!UICONTROL Add]** en selecteer **[!UICONTROL Offer manager]** groep.

   ![](assets/offer_operators_create_001.png)

De aan de aanbiedingsmanager toegewezen rechten stellen hen in staat de volgende taken uit te voeren:

* Wijzig **[!UICONTROL Design]** milieu&#39;s.
* **[!UICONTROL Live]**-omgevingen weergeven.
* Vorm beleidsfuncties (vooraf bepaalde ruimten en filters).
* Categorieën maken en wijzigen.
* Maak voorstellen.
* Geschiktheid van aanbieding configureren.
* Voorstel goedkeuren.

   >[!NOTE]
   >
   >De aanbiedingsmanager kan slechts in twee gevallen een aanbieding goedkeuren. Het eerste geval was dat niemand in het bijzonder als recensent werd gespecificeerd, en het tweede is dat de exploitant die belast was met het creëren van sjablonen (met het recht om recensenten toe te wijzen) hem/haar als recensent in het aanbiedingsmalplaatje specificeerde waarop het aanbod was gebaseerd.

## Leveringsmanager {#delivery-manager}

1. Maak een nieuwe operator.
1. Ga naar het **[!UICONTROL Groups and named rights]** venster, klik **[!UICONTROL Add]** en selecteer **[!UICONTROL Delivery manager]** groep.

   ![](assets/offer_operators_create_002.png)

De aan de leveringsmanager toegewezen rechten zijn/laten hen toe om de volgende taken uit te voeren:

* Geef **[!UICONTROL Live]** omgevingen weer.
* Categorieën voorstellen weergeven en wijzigen.
* Aanbiedingen goedkeuren als s/he is opgegeven als een van de controleurs.

   >[!NOTE]
   >
   >De leveringsmanager kan een aanbieding slechts goedkeuren als hij als recensent tijdens de aanbiedingsconfiguratie is bepaald.

## Reparatie van rechten volgens exploitant {#recap-of-rights-according-to-operator}

<table> 
 <tbody> 
  <tr> 
   <td> </td> 
   <td> <strong>Aanbiedingsbeheer (bewerken)</strong><br /> </td> 
   <td> <strong>Aanbiedingsmanager (live)</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Boomstructuurniveau</strong><br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Voorstellen die worden bewerkt/Live voorstellen<br /> </td> 
   <td> Lezen/Schrijven<br /> </td> 
   <td> Lezen<br /> </td> 
  </tr> 
  <tr> 
   <td> Ontvanger - Omgeving<br /> </td> 
   <td> Lezen/Schrijven<br /> </td> 
   <td> Lezen<br /> </td> 
  </tr> 
  <tr> 
   <td> Beheer<br /> </td> 
   <td> Lezen/Schrijven<br /> </td> 
   <td> Lezen<br /> </td> 
  </tr> 
  <tr> 
   <td> Spaties<br /> </td> 
   <td> Lezen/Schrijven<br /> </td> 
   <td> Lezen<br /> </td> 
  </tr> 
  <tr> 
   <td> Vooraf gedefinieerde aanbiedingsfilters<br /> </td> 
   <td> Lezen/Schrijven<br /> </td> 
   <td> Lezen<br /> </td> 
  </tr> 
  <tr> 
   <td> Typologie<br /> </td> 
   <td> Lezen/Schrijven<br /> </td> 
   <td> Lezen<br /> </td> 
  </tr> 
  <tr> 
   <td> Typologische regels<br /> </td> 
   <td> Lezen/Schrijven<br /> </td> 
   <td> Lezen<br /> </td> 
  </tr> 
  <tr> 
   <td> Catalogus aanbod<br /> </td> 
   <td> Lezen/Schrijven<br /> </td> 
   <td> Lezen<br /> </td> 
  </tr> 
  <tr> 
   <td> Aanbiedingscategorie<br /> </td> 
   <td> Lezen/Schrijven<br /> </td> 
   <td> Lezen<br /> </td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <tbody> 
  <tr> 
   <td> </td> 
   <td> <strong>Leveringsmanager (bewerken)</strong><br /> </td> 
   <td> <strong>Leveringsmanager (live)</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Boomstructuurniveau</strong><br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Voorstellen die worden bewerkt/Live voorstellen<br /> </td> 
   <td> </td> 
   <td> Lezen<br /> </td> 
  </tr> 
  <tr> 
   <td> Ontvanger - Omgeving<br /> </td> 
   <td> </td> 
   <td> Lezen<br /> </td> 
  </tr> 
  <tr> 
   <td> Beheer<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Spaties<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Vooraf gedefinieerde aanbiedingsfilters<br /> </td> 
   <td> Lezen<br /> </td> 
   <td> Lezen<br /> </td> 
  </tr> 
  <tr> 
   <td> Typologie<br /> </td> 
   <td> Lezen<br /> </td> 
   <td> Lezen<br /> </td> 
  </tr> 
  <tr> 
   <td> Typologische regels<br /> </td> 
   <td> </td> 
   <td> Lezen<br /> </td> 
  </tr> 
  <tr> 
   <td> Catalogus aanbod<br /> </td> 
   <td> Lezen<br /> </td> 
   <td> Lezen<br /> </td> 
  </tr> 
  <tr> 
   <td> Aanbiedingscategorie<br /> </td> 
   <td> </td> 
   <td> Lezen<br /> </td> 
  </tr> 
 </tbody> 
</table>
