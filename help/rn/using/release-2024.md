---
product: campaign
title: Releases van Campaign Classic 2024
description: Meer informatie over releases van Campaign Classic 2024
feature: Release Notes
role: User
level: Beginner
exl-id: 8e20391d-3628-4d0c-b413-c34e046ae810
source-git-commit: bf45c8bcdd41e614f9be09bc0fd6385707159841
workflow-type: ht
source-wordcount: '387'
ht-degree: 100%

---

# Releases van 2024{#release-2024}

## Release 7.4.1 - build 9383 {#release-7-4-1}

[!BADGE Algemene beschikbaarheid]{type=Positive url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=nl#rn-statuses" tooltip="Algemene beschikbaarheid"}

_Woensdag 18 juni 2024_

### Wijzigingen en verbeteringen {#release-7-4-1-changes}

* Omdat de aanmeldingsgegevens van het serviceaccount (JWT) door Adobe worden beëindigd, zijn de uitgaande integraties van Campaign met oplossingen en apps van Adobe nu gebaseerd op de OAuth-server-naar-server-aanmeldingsgegevens. Als u uitgaande integraties hebt uitgevoerd, zoals de integratie Campaign-Analytics of Experience Cloud Triggers, moet u uw Campaign-omgeving voor 27 januari 2025 upgraden naar v7.4.1 en uw technische account migreren naar oAuth.  [Meer informatie](../../integrations/using/oauth-technical-account.md)

* Nadat u [uw technische operatoren van Campaign hebt gemigreerd naar Developer Console](../../technotes/using/ims-migration.md) en [bent overgestapt naar IMS voor de verificatie van eindgebruikers](../../technotes/using/migrate-users-to-ims.md), kunt u de gebruikersinterface- en API-beperkingen inschakelen om opties en functies te verwijderen die specifiek zijn voor native verificatie. [Meer informatie](../../technotes/using/impact-ims-migration.md)


### Compatibiliteitsupdates {#release-7-4-1-compat}

De [compatibiliteitsmatrix voor Adobe Campaign](compatibility-matrix.md) is bijgewerkt met de wijzigingen die bij deze nieuwe release worden geleverd en hieronder worden vermeld.

* Adobe Campaign is nu compatibel met **Microsoft Server 2022** als besturingssysteem.
* Adobe Campaign is nu compatibel met **RHEL 9** als besturingssysteem.

  >[!CAUTION]
  >
  >Als u als on-premise klant met RHEL 9 DKIM-verificatie (Domain Keys Identified Mail) wilt gebruiken, moet u uw systeeminstellingen bijwerken zoals beschreven in [deze sectie](../../installation/using/installing-packages-with-linux.md#rhel-9-update).


* Adobe Campaign is nu compatibel met **Microsoft SQL Server 2022** en **Oracle 23c** als relationele databasemanagementsystemen en in Federated Data Access (FDA).

* Adobe Campaign heeft nu ten minste één Java Development Kit (JDK) 11 nodig. In Windows moet de JRE beschikbaar zijn zoals beschreven in [deze sectie](../../installation/using/application-server.md#jdk).

* De Campaign-SDK voor mobiele applicaties (Neolane) is nu afgeschaft. U moet nu overstappen op de Adobe Experience Platform SDK. [Meer informatie](deprecated-features.md).

  Inmiddels wordt Campaign v7.4 voor het garanderen van de servicecontinuïteit geleverd met:

   * een nieuwe Campaign SDK 1.0.27 voor iOS, compatibel met iOS 16 en 17, en de recentste [eisen aan Apple iOS-privacyverzoeken](https://developer.apple.com/news/?id=r1henawx){target="_blank"}.
   * een nieuwe Campaign-SDK voor Android 14.

### Andere wijzigingen {#release-7-4-1-other}

Vanaf v7.4.1 worden XML-bibliotheken voor RPM Linux-pakketten niet meer opgenomen in Campaign. Als on-premise of hybride klant moet uw beheerder deze bibliotheken installeren. [Meer informatie](../../installation/using/installing-packages-with-linux.md)

### Patches {#release-7-4-1-patches}

Deze release bevat de volgende oplossingen:

NEO-74754, NEO-73174, NEO-72504, NEO-71534, NEO-71473, NEO-70195, NEO-69663, NEO-69651, NEO-67620, NEO-67235, NEO-66797, NEO-64680, NEO-63706, NEO-63657, NEO-62964, NEO-62575, NEO-58734, NEO-40531, NEO-36189, NEO-29592


