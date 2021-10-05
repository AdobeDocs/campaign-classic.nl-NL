---
product: campaign
title: Integreren met Adobe Target
description: Integreren met Adobe Target
audience: integrations
content-type: reference
topic-tags: adobe-target
exl-id: 2e29d090-b87b-4cff-a703-58e1da082f04
source-git-commit: 0996cc313be93300bce2f094c97e45a794cd459e
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 0%

---

# Integreren met Adobe Target{#integrating-with-adobe-target}

![](../../assets/v7-only.svg)

Dankzij de integratie tussen Adobe Campaign en Adobe Target (Classic en Standard) in Adobe Experience Cloud kunt u een aanbod van Adobe Target opnemen in een Adobe Campaign-e-maillevering.

Het operationele beginsel is als volgt: wanneer een ontvanger een e-mailbericht opent dat via Adobe Campaign is verzonden, kunt u met een aanroep naar Adobe Target een dynamische versie van de inhoud weergeven. Deze dynamische versie wordt berekend op basis van de regels die vooraf zijn opgegeven bij het maken van de e-mail.

>[!NOTE]
>
>De integratie ondersteunt alleen statische afbeeldingen. De rest van de inhoud kan niet worden gepersonaliseerd.

Adobe Target kan verschillende typen gegevens gebruiken:

* Gegevens uit de Adobe Campaign datamart
* Segmenten die zijn gekoppeld aan de bezoekersidentiteitskaart in Adobe Target, indien voor de gebruikte gegevens geen wettelijke beperkingen gelden
* Adobe Target-gegevens: gebruikersagent, IP-adres, geolocatiegegevens

>[!NOTE]
>
>Op de [Adobe Target Help-pagina&#39;s](https://experienceleague.adobe.com/docs/target/using/integrate/campaign-and-target.html) vindt u ook informatie over de integratie tussen Adobe Campaign en Adobe Target.
