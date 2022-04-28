---
product: campaign
title: Technote - Adobe Campaign - Beveiligingsupdate Apache-versie
description: Adobe Campaign - Beveiligingsupdate Apache-versie
hide: true
hidefromtoc: true
source-git-commit: 086d03cf0ceb5c2db7ded0c2bedb1b0514257d8a
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# Adobe Campaign - Beveiligingsupdate Apache-versie {#apache-update}

Campaign Classic werkt met hulpmiddelen van derden en de compatibiliteit wordt regelmatig bijgewerkt, zodat alleen ondersteunde versies kunnen worden geïmplementeerd en de nieuwste correcties en verbeteringen kunnen worden toegepast.

Adobe Campaign bevat Apache Tomcat, die via HTTP als ingangspunt fungeert in de toepassingsserver, en die is geïntegreerd met Apache Web-server. De Apache Software Foundation heeft Apache HTTP Server 2.4.53 uitgebracht. Deze versie verhelpt kwetsbaarheden —CVE-2021-44790 en CVE-2021-44224— waarvan er één een externe aanvaller in staat kan stellen de controle over een beïnvloed systeem te verkrijgen. Meer informatie in [Apache 2.4.53](https://downloads.apache.org/httpd/Announcement2.4.html){target=&quot;_blank&quot;}.

Het Adobe Campaign-team voert de upgradeactiviteiten voor de Apache-versie uit door **31 mei 2022** om deze Apache-kwetsbaarheid te beperken en uw instantieomgeving veiliger te maken. Deze upgrade is van toepassing op alle Managed Services-klanten die op een kwetsbare versie van Apache HHTP Server werken. Als dit gevolgen heeft, heeft Adobe al contact met u opgenomen om u op de hoogte te stellen van deze upgrade.

Van deze upgrade wordt verwacht dat deze automatisch buiten de normale kantooruren wordt uitgevoerd, zodat u de Campagneservice zonder onderbreking kunt blijven gebruiken.

Uw niet-productie-instantie(s) worden eerst door onze teams geüpgraded voordat we uw productie-instantie(s) upgraden. Aangezien dit een auto verbeteringsproces is, is er geen actie van uw kant wordt vereist. Als u echter problemen ondervindt, kunt u contact opnemen met [Adobe Klantenservice](https://experienceleague.adobe.com/?support-solution=Campaign#support).

Aangezien de upgrade de Apache opnieuw moet starten, verwachten we dat de downtime niet langer zal zijn dan 10 minuten binnen de hieronder vermelde periode.

## Veelgestelde vragen {#apache-faq}

* **Waarom is dit een verplichte upgrade?**

   De huidige Apache-versie is kwetsbaar en heeft een potentieel veiligheidsrisico. Het is belangrijk dat uw instantie(s) van de Campagne wordt (worden) geüpgraded naar de meest recente toepasselijke Apache-versie om het beveiligingsrisico te verhelpen.


* **Welke klanten worden gericht voor veiligheidsupgrades?**

   Alle klanten wier Campagneomgevingen zijn geïmplementeerd op oudere Apache-versies worden geüpgraded naar de meest recente toepasselijke Apache-versie.

* **Wat is de verwachte onderbreking?**

   De verwachte downtime is minder dan 10 minuten.


* **Zijn er om het even welke acties die door de klant voor deze veiligheidsverbetering worden vereist?**

   Er zijn geen handelingen vereist omdat de beveiligingsupgrade automatisch wordt uitgevoerd.


* **Welke bevestigingen moeten door de klanten worden in werking gesteld?**

   Er is geen specifieke test nodig voor deze beveiligingsupgrade. Indien een probleem wordt vastgesteld, kunt u contact opnemen met [Adobe Klantenservice](https://experienceleague.adobe.com/?support-solution=Campaign#support)


* **Kan ik om een verandering in Datum/Tijd in de geplande groef van de veiligheidsverbetering verzoeken?**

   Aangezien dit een veiligheidsmoeilijke situatie is, adviseren wij u sterk aan het bestaande programma aan te passen.


Voor elke andere vraag kunt u zich tot [Adobe Klantenservice](https://experienceleague.adobe.com/?support-solution=Campaign#support).
