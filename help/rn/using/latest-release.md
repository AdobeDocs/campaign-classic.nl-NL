---
product: campaign
title: Nieuwste release
description: De nieuwste aanvullende informatie voor Campaign Classic v7
feature: Release Notes
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: d31aa28da06e65664da655b6b082563767b35f7a
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 19%

---

# Nieuwste release {#latest-release}

Deze pagina bevat nieuwe mogelijkheden, verbeteringen en oplossingen die worden geleverd met de **nieuwste versie van Campaign Classic v7**. Elke nieuwe build heeft een status die wordt aangegeven door een kleur. Meer informatie over de build-statussen van Campaign Classic v7 vindt u op [deze pagina](rn-overview.md).

## Release 7.4.1 - build 9383 {#release-7-4-1}

[!BADGE Algemene beschikbaarheid]{type=Positive url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=nl#rn-statuses" tooltip="Algemene beschikbaarheid"}

_woensdag 18 juni 2024_

### Wijzigingen en verbeteringen {#release-7-4-1-changes}

* Omdat de credentie van de Rekening van de Dienst (JWT) door Adobe wordt afgekeurd, baseren de uitgaande integratie van de Campagne met de oplossingen van de Adobe en apps nu op server-aan-server referentie OAuth. Als u uitgaande integratie hebt geïmplementeerd, zoals de integratie van Campagne-Analytics of Experience Cloud Triggers, moet u uw Campagneomgeving upgraden naar v7.4.1 en uw Technical Account migreren naar Auth voor 27 januari 2025. [Meer informatie](../../integrations/using/oauth-technical-account.md)

* Als u eenmaal [Uw technische operatoren voor campagne zijn gemigreerd naar de Developer Console](../../technotes/using/ims-migration.md) en [overgang naar IMS voor verificatie van eindgebruikers](../../technotes/using/migrate-users-to-ims.md)kunt u nu de gebruikersinterface- en API-beperkingen inschakelen om opties en functies te verwijderen die specifiek zijn voor native verificatie. [Meer informatie](../../technotes/using/impact-ims-migration.md)



### Compatibiliteitsupdates {#release-7-4-1-compat}

De [compatibiliteitsmatrix voor Adobe Campaign](compatibility-matrix.md) is bijgewerkt met de wijzigingen die bij deze nieuwe release worden geleverd en hieronder worden vermeld.

* Adobe Campaign is nu compatibel met **Microsoft Server 2022** en **RHEL 9** als besturingssystemen.

* Adobe Campaign is nu compatibel met **Microsoft SQL Server 2022** en **Oracle 23 quater** als Relation Database Management Systems, en in Federated Data Access (FDA).

* Adobe Campaign heeft nu ten minste een Java Development Kit (JDK) 11 nodig. In Windows moet de JRE beschikbaar zijn zoals beschreven in [deze sectie](../../installation/using/application-server.md#jdk).

* De Campagne (Neolane) SDK voor mobiele toepassingen is nu afgekeurd. U moet nu overstappen op de SDK van Adobe Experience Platform. [Meer informatie](deprecated-features.md).

  Ondertussen, om de dienstcontinuïteit te verzekeren, komt Campaign v7.4 met:

   * een nieuwe campagne-SDK 1.0.27 voor iOS, compatibel met iOS 16 en 17, en de nieuwste [Apple iOS Privacy Request-vereisten](https://developer.apple.com/news/?id=r1henawx){target="_blank"}.
   * een nieuwe campagne-SDK voor Android 14.


### Patches {#release-7-4-1-patches}

Deze release bevat de volgende oplossingen:

NEO-74754, NEO-73174, NEO-72504, NEO-71534, NEO-71473, NEO-70195, NEO-6963, NEO-696 51, NEO-67620, NEO-67235, NEO-66797, NEO-64680, NEO-63706, NEO-63657, NEO-62964, NEO-6 2575, NEO-58734, NEO-40531, NEO-36189, NEO-29592

