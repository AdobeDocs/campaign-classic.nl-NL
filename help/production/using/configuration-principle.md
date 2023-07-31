---
product: campaign
title: Configuratiebeginsel
description: Configuratiebeginsel
feature: Monitoring, Configuration
badge-v7-only: label="v7" type="Informative" tooltip="Alleen van toepassing op Campaign Classic v7"
badge-v7-prem: label="op locatie en hybride" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=nl" tooltip="Alleen van toepassing op on-premise en hybride implementaties"
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 03d7e579-8678-44b8-bbe7-cf4204bffb25
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 7%

---

# Configuratiebeginsel{#configuration-principle}



Het Adobe Campaign-platform is gebaseerd op het concept van instanties, vergelijkbaar met dat van virtuele hosts die door Apache worden gebruikt. In deze modus kunt u een server delen door er verschillende instanties aan toe te wijzen. De instanties zijn volledig verschillend van elkaar en werken met hun eigen gegevensbestand en configuratiedossier.

Voor een bepaalde server zijn er twee gemeenschappelijke elementen voor alle instanties van Adobe Campaign:

* De **internal** wachtwoord: dit is het algemene beheerderswachtwoord. Dit geldt voor alle instanties van een bepaalde toepassingsserver.

  >[!IMPORTANT]
  >
  >Als u zich wilt aanmelden met de **Intern** id, moet u vooraf een wachtwoord hebben bepaald. Raadpleeg [deze sectie](../../installation/using/configuring-campaign-server.md#internal-identifier) voor meer informatie.

* Meerdere technische serverconfiguraties: deze configuraties kunnen allemaal worden overbelast in de specifieke configuratie van een instantie.

De configuratiebestanden worden opgeslagen in het dialoogvenster **conf** directory van de installatiemap. De configuratie bestaat uit drie bestanden:

* **serverConf.xml**: algemene configuratie voor alle instanties.
* **config-**`<instance>`**.xml** waarbij **`<instance>`** is de instantienaam): specifieke configuratie van een instantie.
* **serverConf.xml.diff**: delta tussen de aanvankelijke configuratie en de huidige configuratie. Dit bestand wordt automatisch gegenereerd door de toepassing en mag niet handmatig worden gewijzigd. Het wordt gebruikt om gebruikerswijzigingen automatisch te verspreiden wanneer het bijwerken van een bouwstijlversie.

Een instantieconfiguratie wordt als volgt geladen:

* De module laadt de **serverConf.xml** om de parameters te verkrijgen die door alle instanties worden gedeeld.
* Het laadt vervolgens de **config-**`<instance>`**.xml** bestand. De waarden in dit bestand hebben voorrang op de waarden in **serverConf.xml**.

  Deze twee bestanden hebben dezelfde indeling. Elke waarde in **serverConf.xml** kan voor een bepaalde instantie worden overgeladen in het deelvenster **config-`<instance>`.xml** bestand.

Deze werkende wijze verstrekt grote flexibiliteit voor configuraties.
