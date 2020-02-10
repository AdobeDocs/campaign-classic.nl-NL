---
title: Configuratiebeginsel
seo-title: Configuratiebeginsel
description: Configuratiebeginsel
seo-description: null
page-status-flag: never-activated
uuid: 6315d526-b820-46ab-96c7-e64e101c6a7d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: production-procedures
discoiquuid: d08ff769-da93-4f86-8802-f0fb5b051ece
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 34cd6e6cf5652c9e2163848c2b1ef32f53ee6ca4

---


# Configuratiebeginsel{#configuration-principle}

Het Adobe Campaign-platform is gebaseerd op het concept van instanties, vergelijkbaar met dat van virtuele hosts die door Apache worden gebruikt. In deze modus kunt u een server delen door er verschillende instanties aan toe te wijzen. De instanties zijn volledig verschillend van elkaar en werken met hun eigen gegevensbestand en configuratiedossier.

Voor een bepaalde server zijn er twee gemeenschappelijke elementen voor alle instanties van de Campagne van Adobe:

* Het **interne** wachtwoord: dit is het algemene beheerderswachtwoord. Dit geldt voor alle instanties van een bepaalde toepassingsserver.

   >[!CAUTION]
   >
   >Als u zich wilt aanmelden met de **interne** id, moet u vooraf een wachtwoord hebben gedefinieerd. Zie [deze sectie](../../installation/using/campaign-server-configuration.md#internal-identifier)voor meer informatie.

* Meerdere technische serverconfiguraties: deze configuraties kunnen allen in de specifieke configuratie van een instantie worden overbelast.

De configuratiebestanden worden opgeslagen in de map **conf** van de installatiemap. De configuratie bestaat uit drie bestanden:

* **serverConf.xml**: algemene configuratie voor alle instanties.
* **config-**`<instance>`**.xml** (waar **`<instance>`** de instantienaam is): specifieke configuratie van een instantie.
* **serverConf.xml.diff**: delta tussen de aanvankelijke configuratie en de huidige configuratie. Dit bestand wordt automatisch gegenereerd door de toepassing en mag niet handmatig worden gewijzigd. Het wordt gebruikt om gebruikerswijzigingen automatisch te verspreiden wanneer het bijwerken van een bouwstijlversie.

Een instantieconfiguratie wordt als volgt geladen:

* De module laadt het bestand **serverConf.xml** om de parameters te verkrijgen die door alle instanties worden gedeeld.
* Vervolgens wordt het bestand **config-**`<instance>`**.xml** geladen. De waarden in dit bestand hebben voorrang op waarden in **serverConf.xml**.

   Deze twee bestanden hebben dezelfde indeling. Elke waarde in **serverConf.xml** kan voor een bepaalde instantie worden overgeladen in het bestand **config-`<instance>`.xml** .

Deze werkende wijze verstrekt grote flexibiliteit voor configuraties.
