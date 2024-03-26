---
product: campaign
title: Werken met Adobe Campaign en Adobe Target
description: Leer hoe u Adobe Campaign kunt integreren met Adobe Target
feature: Target Integration
badge-v7: label="v7" type="Informative" tooltip="Is van toepassing op Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
audience: integrations
content-type: reference
topic-tags: adobe-target
exl-id: 2e29d090-b87b-4cff-a703-58e1da082f04
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '204'
ht-degree: 0%

---

# Werken met campagne en doel{#integrating-with-adobe-target}



Gebruik Adobe Campaign met Adobe Target om e-mailinhoud te optimaliseren.

Als u uw e-mailinhoud wilt optimaliseren, kunt u een omleidingsvoorstel in Adobe Target maken en vervolgens Adobe Campaign gebruiken om de e-mailaanbiedingen te beheren. U kunt bijvoorbeeld verschillende aanbiedingen voor mannelijke en vrouwelijke ontvangers weergeven.

De integratie vindt plaats wanneer de e-mail wordt geopend. Wanneer de klant de e-mail opent, wordt een vraag gemaakt aan Target en een dynamische versie van de inhoud verschijnt. De inhoud bestaat uit een statische afbeelding die door alle browsers wordt ondersteund. Het doel volgt de reactie op de aanbieding op het publiek of zittingsniveau en dat de gegevens in de rapporten van het Doel beschikbaar zijn. [Meer informatie in de documentatie van Adobe Target](https://experienceleague.adobe.com/docs/target/using/integrate/campaign-and-target.html).


>[!NOTE]
>
>De integratie ondersteunt alleen statische afbeeldingen. De rest van de inhoud kan niet worden gepersonaliseerd.

Adobe Target kan verschillende gegevenstypen gebruiken:

* Gegevens uit de Adobe Campaign datamart
* Segmenten die zijn gekoppeld aan de bezoekersidentiteitskaart in Adobe Target, indien voor de gebruikte gegevens geen wettelijke beperkingen gelden
* Adobe Target-gegevens: gebruikersagent, IP-adres, geolocatiegegevens
