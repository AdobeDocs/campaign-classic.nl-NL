---
solution: Campaign Classic
product: campaign
title: Configuratiebeginsel
description: Configuratiebeginsel
audience: production
content-type: reference
topic-tags: production-procedures
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 4%

---


# Configuratiebeginsel{#configuration-principle}

Het Adobe Campaign-platform is gebaseerd op het concept van instanties, vergelijkbaar met dat van virtuele hosts die door Apache worden gebruikt. In deze modus kunt u een server delen door er verschillende instanties aan toe te wijzen. De instanties zijn volledig verschillend van elkaar en werken met hun eigen gegevensbestand en configuratiedossier.

Voor een bepaalde server zijn er twee gemeenschappelijke elementen voor alle instanties van Adobe Campaign:

* Het **interne** wachtwoord: dit is het algemene beheerderswachtwoord. Dit geldt voor alle instanties van een bepaalde toepassingsserver.

   >[!IMPORTANT]
   >
   >Als u zich wilt aanmelden met de **interne** id, moet u vooraf een wachtwoord hebben gedefinieerd. Raadpleeg [deze sectie](../../installation/using/campaign-server-configuration.md#internal-identifier) voor meer informatie.

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
