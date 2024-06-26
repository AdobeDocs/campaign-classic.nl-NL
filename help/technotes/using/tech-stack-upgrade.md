---
product: campaign
title: Technote - Adobe Campaign-systeemupgrades
description: Adobe Campaign-systeemupgrade
feature: Technote, Upgrade
exl-id: 78949d94-60b3-44f1-8e5a-d61b5b723e87
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '502'
ht-degree: 4%

---

# Adobe Campaign 2023-upgrades voor de omgeving {#ac-system-upgrade}

De campagneinfrastructuur is afhankelijk van systemen van derden die regelmatig met de meest recente versies en correcties moeten worden bijgewerkt. Deze updates zijn verplicht om de continuïteit van de service en veilige Campagneomgevingen tegen beveiligingsrisico&#39;s te garanderen. Daarnaast is een Campagne-upgrade vereist om te zorgen voor compatibiliteit met systeemwijzigingen van derden.

Als **Klant voor gehoste of beheerde Cloud Servicen**, informeert de Adobe u over deze upgrades wanneer deze nodig zijn. U moet uw omgevingen upgraden in overeenstemming met de aanbevelingen om naleving te garanderen.

Als **Op locatie of hybride klant**, raadt de Adobe u ten zeerste aan om uw systeem- en campagneversies volgens dezelfde kalender te upgraden.

Om veiligheidsredenen moet u [De nieuwste build voor campagne installeren](#ac-upgrade)en upgrade vervolgens uw [besturingssysteem](#os-upgrade) en/of uw [Relation Database Management System (RDBMS)](#pg-upgrade).

>[!NOTE]
>
>Voor vragen over deze wijzigingen kunt u contact opnemen met [Klantenservice Adoben](https://helpx.adobe.com/nl/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html). Zie ook de [Veelgestelde vragen over upgrades samenstellen](../../platform/using/faq-build-upgrade.md).
>

## Verbetering van campagne-build {#ac-upgrade}

**Heeft dit gevolgen voor u?**

Als de [besturingssysteemupgrade](#os-upgrade) en/of de [upgrade van databasesysteem](#pg-upgrade) hieronder gedetailleerd, moet u uw Campagneomgevingen upgraden naar [de nieuwste versie 7.3.2](../../rn/using/latest-release.md#release-7-3-2), die compatibel is met deze systemen.

**Hoe kan ik bijwerken?**

* Als ontvangen of Beheerde klant van Cloud Servicen, zal de Adobe u contacteren en uw versie van de Campagne bevorderen.
* Als hybride klant, zal de Adobe u van de geplande bouwstijlverbeteringsdata voor uw midsourcingsmilieu op de hoogte brengen. U moet ook uw marketingomgeving upgraden naar dezelfde versie.
* Als klant op locatie wordt u gevraagd om uw Campagneomgevingen te upgraden naar de nieuwste versie van 7.3.2.


## Upgrade van besturingssysteem {#os-upgrade}

**Heeft dit gevolgen voor u?**

Als u Campagne op een Debian werkend systeem in werking stelt, om van de recentste beveiligingsupdates van Debian te profiteren, moet u uw infrastructuur van de Campagne verplaatsen naar **Debian 11**. De beveiligingsondersteuning voor Debian 9 is beschikbaar tot 30 juni 2023.

**Hoe kan ik bijwerken?**

* Als ontvangen of Beheerde klant van Cloud Servicen, zal de Adobe u contacteren en uw milieu bevorderen.
* Als hybride klant, zal de Adobe u van de geplande verbeteringsdata voor uw midsourcingmilieu op de hoogte brengen. Als uw marketing milieu ook op Debian loopt, moet u het aan Debian 11 ook bevorderen.
* Als klant op locatie wordt u gevraagd uw omgevingen te upgraden naar Debian 11.

## Upgrade van databasesysteem {#pg-upgrade}

**Heeft dit gevolgen voor u?**

Als uw gegevensbestandsysteem voor Campagne PostSQL is, om van recentste innovaties en veiligheidsupdates te profiteren PostgreSQL, moet u bevorderen om **PostgreSQL 14**. Merk op dat PostgreSQL 11 eind van het Leven op 9 November 2023 zal bereiken.

**Hoe kan ik bijwerken?**

* Als ontvangen of Beheerde klant van Cloud Servicen, zal de Adobe u contacteren en uw gegevensbestandsysteem van PostgreSQL 11 aan PostgreSQL 14 bevorderen.
* Als hybride klant, als uw marketing gegevensbestandsysteem PostgreSQL is, moet u het bevorderen aan PostgreSQL 14.
* Als klant op locatie wordt u gevraagd uw databasesysteem bij te werken naar PostgreSQL 14.


## Nuttige koppelingen

* [Upgrade uw omgeving](../../production/using/build-upgrade.md)
* [Veelgestelde vragen over buildupgrades](../../platform/using/faq-build-upgrade.md)
* [Download de nieuwste build van het Campaign Classic](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)
* [De nieuwe clientconsole beschikbaar maken voor gebruikers](../../installation/using/client-console-availability-for-windows.md)
