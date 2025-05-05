---
product: campaign
title: Technote - Adobe Campaign - Beveiligingsupdate Apache-versie
description: Adobe Campaign - Beveiligingsupdate Apache-versie
feature: Technote, Upgrade
hide: true
hidefromtoc: true
exl-id: 3d2f5d1d-4b31-4cc6-b6fb-13589856e00c
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '529'
ht-degree: 0%

---

# Adobe Campaign - Beveiligingsupdate Apache-versie {#apache-update}

>[!CAUTION]
>Dit artikel is van toepassing op: **Campaign Classic v7 Managed Services** klanten, **Campagne v8** klanten en **Campaign Standard** klanten.

Adobe Campaign werkt met hulpprogramma&#39;s van derden en de compatibiliteit wordt regelmatig bijgewerkt, zodat alleen ondersteunde versies kunnen worden geïmplementeerd en de nieuwste correcties en verbeteringen kunnen worden toegepast.

Adobe Campaign bevat Apache Tomcat, die via HTTP als ingangspunt fungeert in de toepassingsserver, en die is geïntegreerd met Apache Web-server. De Apache Software Foundation heeft Apache HTTP Server 2.4.53 uitgebracht. Deze versie verhelpt kwetsbaarheden die een externe aanvaller in staat kunnen stellen de controle over een beïnvloed systeem te verkrijgen. Meer informatie in [Apache 2.4.53](https://downloads.apache.org/httpd/Announcement2.4.html){target="_blank"}.

Het Adobe Campaign-team voert de upgradeactiviteiten voor de Apache-versie uit door **15 juni 2022** om deze Apache-kwetsbaarheid te beperken en uw instantieomgeving veiliger te maken. Deze upgrade is van toepassing op alle Campaign Classic v7 Managed Services-klanten, Campaign v8 en klanten van het Campaign Standard die op een kwetsbare versie van Apache HTTP Server werken. Als dit gevolgen heeft, heeft de Adobe al contact met u opgenomen om u op de hoogte te stellen van deze upgrade.

Van deze upgrade wordt verwacht dat deze automatisch buiten de normale kantooruren wordt uitgevoerd, zodat u de Campagneservice zonder onderbreking kunt blijven gebruiken.

De niet-productie-instantie(s) worden eerst door de Adobe bijgewerkt, waarna de productie-instantie(s) worden bijgewerkt. Aangezien dit een automatisch upgradeproces is dat eigendom is van de Adobe, is er geen actie van uw kant vereist. Als u echter problemen ondervindt, kunt u contact opnemen met [Klantenservice Adoben](https://experienceleague.adobe.com/nl?support-solution=Campaign#support).


>[!NOTE]
>Deze upgrade vereist om de Apache-webserver opnieuw te starten. De downtime zal niet langer zijn dan 10 minuten binnen de hieronder vermelde periode.
> 

## Veelgestelde vragen {#apache-faq}

* **Waarom is dit een verplichte upgrade?**

  De huidige Apache-versie is kwetsbaar en heeft een potentieel veiligheidsrisico. Het is belangrijk dat uw instantie(s) van de Campagne wordt (worden) geüpgraded naar de meest recente toepasselijke Apache-versie om het beveiligingsrisico te verhelpen.

* **Welke klanten worden gericht voor veiligheidsupgrades?**

  Alle klanten die gebruikmaken van Campagne-omgevingen die zijn geïmplementeerd in oudere Apache-versies, worden geüpgraded naar de nieuwste Apache-versie die van toepassing is.

* **Wat is de verwachte onderbreking?**

  De verwachte downtime is minder dan 10 minuten.

* **Zijn er om het even welke acties die door de klant voor deze veiligheidsverbetering worden vereist?**

  Er zijn geen handelingen vereist omdat de beveiligingsupgrade automatisch wordt uitgevoerd.

* **Wat is het effect op de lopende campagnes/werkschema&#39;s tijdens het onderhoudsvenster?**

  Tijdens het onderhoudsvenster worden de workflow en de e-mailservices stopgezet en worden de geplande activiteiten niet uitgevoerd. Om het even welke aan de gang zijnde activiteiten of lopende processen zullen tijdens onderbreking worden gestopt tot de server opnieuw begint. Zodra de activiteit wordt voltooid en de server opnieuw is begonnen, zullen alle diensten hervatten.

* **Welke bevestigingen moeten door de klanten worden in werking gesteld?**

  Er is geen specifieke test nodig voor deze beveiligingsupgrade. Indien een probleem wordt vastgesteld, kunt u contact opnemen met [Klantenservice Adoben](https://experienceleague.adobe.com/nl?support-solution=Campaign#support).


* **Kan ik om een verandering in Datum/Tijd in de geplande groef van de veiligheidsverbetering verzoeken?**

  Aangezien dit een veiligheidsmoeilijke situatie is, adviseren wij u sterk aan het bestaande programma aan te passen.


Voor elke andere vraag kunt u zich tot [Klantenservice Adoben](https://experienceleague.adobe.com/nl?support-solution=Campaign#support).
