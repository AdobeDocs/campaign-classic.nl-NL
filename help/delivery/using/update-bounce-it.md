---
product: campaign
title: Bounce-kwalificatie bijwerken na Italia Online-uitgang
description: Leer hoe u de stuiterkwalificatie bijwerkt na Italia Online-storing
feature: Deliverability
hide: true
hidefromtow: true
source-git-commit: 0e6a46e4a0575fa5a300a952a6bb134f3426172e
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 0%

---

# Onjuiste vaste bedragen bijwerken na Italia Online-storing {#update-bounce-italia}

![](../../assets/common.svg)

## Context{#outage-context}

Sinds 22 januari (lokale tijd) heeft Italia Online een stroomstoring doorgemaakt die heeft geleid tot verschillende vertragingen en afgekeurde e-mails. De dienst begon op 26 januari met beperkte capaciteit te hervatten.

Betrokken domeinen zijn: **libero.it**, **virgilio.it**, **inwind.it**, **jol.it**, en **blu.it**.

Dit probleem heeft zich voorgedaan van 22-1-2023 tot 26-11-2023, maar het grootste deel van de ten onrechte in quarantaine gehouden dieren vond plaats op 26 januari.

Meer informatie in de officiële communicatie [hier](https://tecnologia.libero.it/avviato-il-ritorno-online-di-libero-mail-e-virgilio-mail-66832){_blank}.


## Gevolgen{#outage-impact}

Net als in de meeste gevallen waarin een internetprovider buiten beeld is, zijn sommige e-mails die via campagne zijn verzonden, ten onrechte gemarkeerd als steunkleuren. Dit was niet alleen van invloed op Adobe, maar iedereen probeerde om via e-mail aan Italia Online te worden bezorgd tijdens de periode van de storing.

Symptomen waren:

* **Uitstel** met het bericht `452 requested action aborted: try again later` - deze werden automatisch opnieuw beproefd en er zijn geen acties nodig.

* **Harde vlekken** met het bericht `550 <email address> recipient rejected` zijn teruggekeerd door ISP op 26 Januari, tussen 8h - 2 pm lokale tijd, om afzenders te verhinderen hun servers te blijven overbelasten. Zoals bevestigd door de Italia Online Postmaster, zijn dit geen echte harde bochten, dus raden we aan om alle e-mailadressen die op 26 januari 2023 zijn uitgesloten, uit de quarantaine te halen vanwege dat bericht.

## Proces voor bijwerken{#outage-update}

Adobe Campaign heeft deze ontvangers automatisch aan de quarantainelijst toegevoegd met een **[!UICONTROL Status]** instellen van **[!UICONTROL Quarantine]**. Om dit te verbeteren, moet u uw quarantainetabel in Campagne bijwerken door deze ontvangers te vinden en te verwijderen, of hun te veranderen **[!UICONTROL Status]** tot **[!UICONTROL Valid]** zodat de nachtelijke schoonmaakworkflow ze verwijdert.

Om de ontvangers te vinden die door deze kwestie werden beïnvloed, of in het geval dat dit opnieuw met andere ISP gebeurt, gelieve de instructies te zien [op deze pagina](../../delivery/using/understanding-quarantine-management.md#unquarantine-bulk).
