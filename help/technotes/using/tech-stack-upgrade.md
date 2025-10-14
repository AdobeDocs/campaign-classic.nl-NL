---
product: campaign
title: Technote - Adobe Campaign-systeemupgrades
description: Adobe Campaign-systeemupgrade
feature: Technote, Upgrade
hide: true
hidefromtoc: true
exl-id: 78949d94-60b3-44f1-8e5a-d61b5b723e87
source-git-commit: 62fc46e45078fce56eadda3518251e61244bf5d0
workflow-type: tm+mt
source-wordcount: '502'
ht-degree: 4%

---

# Adobe Campaign 2023-upgrades voor de omgeving {#ac-system-upgrade}

De campagneinfrastructuur is afhankelijk van systemen van derden die regelmatig met de meest recente versies en correcties moeten worden bijgewerkt. Deze updates zijn verplicht om de continuïteit van de service en veilige Campagneomgevingen tegen beveiligingsrisico&#39;s te garanderen. Daarnaast is een Campagne-upgrade vereist om te zorgen voor compatibiliteit met systeemwijzigingen van derden.

Als a **Gehoste of Beheerde klant van de Diensten van de Wolk**, informeert Adobe u over deze verbeteringen wanneer zij nodig zijn. U moet uw omgevingen upgraden in overeenstemming met de aanbevelingen om naleving te garanderen.

Als **op-gebouw of Hybride klant**, adviseert Adobe hoogst dat u uw systeem en de versies van de Campagne volgens de zelfde kalender bevordert.

Voor veiligheidsredenen, moet u [&#x200B; de recentste Bouwstijl van de Campagne &#x200B;](#ac-upgrade) installeren, en dan uw [&#x200B; werkend systeem &#x200B;](#os-upgrade) en/of uw [&#x200B; Systeem van het Beheer van het Gegevensbestand van de Verhouding (RDBMS) &#x200B;](#pg-upgrade) bevorderen.

>[!NOTE]
>
>Voor om het even welke vragen over deze veranderingen, contacteer [&#x200B; de Zorg van de Klant van Adobe &#x200B;](https://helpx.adobe.com/nl/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html). Zie ook de [&#x200B; verbetering FAQ van de Bouwstijl &#x200B;](../../platform/using/faq-build-upgrade.md).
>

## Verbetering van campagne-build {#ac-upgrade}

**Heeft dit gevolgen voor u?**

Als u door de [&#x200B; werkend systeemverbetering &#x200B;](#os-upgrade) en/of de [&#x200B; hieronder gedetailleerde verbetering van het gegevensbestandsysteem &#x200B;](#pg-upgrade) wordt beïnvloed, moet u uw milieu&#39;s van de Campagne aan [&#x200B; recentste versie 7.3.2 &#x200B;](../../rn/using/latest-release.md#release-7-3-2) bevorderen, die met deze systemen compatibel is.

**Hoe kan ik bijwerken?**

* Als gehoste of beheerde klant van de Cloud Services zal Adobe contact met u opnemen en uw versie van de Campagne upgraden.
* Als hybride klant zal Adobe u op de hoogte stellen van de geplande upgradedata voor uw omgeving voor midsourcing. U moet ook uw marketingomgeving upgraden naar dezelfde versie.
* Als klant op locatie wordt u gevraagd om uw Campagneomgevingen te upgraden naar de nieuwste versie van 7.3.2.


## Upgrade van besturingssysteem {#os-upgrade}

**Heeft dit gevolgen voor u?**

Als u Campagne op een Debian werkend systeem in werking stelt, om van recentste Debian veiligheidsupdates te profiteren, moet u uw infrastructuur van de Campagne aan **Debian 11** bewegen. De beveiligingsondersteuning voor Debian 9 is beschikbaar tot 30 juni 2023.

**Hoe kan ik bijwerken?**

* Als gehoste of beheerde klant van Cloud Services zal Adobe contact met u opnemen en uw omgeving upgraden.
* Als hybride klant zal Adobe u op de hoogte stellen van de geplande upgradedata voor uw omgeving voor midsourcing. Als uw marketing milieu ook op Debian loopt, moet u het aan Debian 11 ook bevorderen.
* Als klant op locatie wordt u gevraagd uw omgevingen te upgraden naar Debian 11.

## Upgrade van databasesysteem {#pg-upgrade}

**Heeft dit gevolgen voor u?**

Als uw gegevensbestandsysteem voor Campagne PostSQL is, om van recentste innovaties en veiligheidsupdates te profiteren PostgreSQL, moet u aan **PostgreSQL 14** bevorderen. Merk op dat PostgreSQL 11 eind van het Leven op 9 November 2023 zal bereiken.

**Hoe kan ik bijwerken?**

* Als gehoste of beheerde klant van Cloud Services zal Adobe contact met u opnemen en uw databasesysteem upgraden van PostgreSQL 11 naar PostgreSQL 14.
* Als hybride klant, als uw marketing gegevensbestandsysteem PostgreSQL is, moet u het bevorderen aan PostgreSQL 14.
* Als klant op locatie wordt u gevraagd uw databasesysteem bij te werken naar PostgreSQL 14.


## Nuttige koppelingen

* [Upgrade uw omgeving](../../production/using/build-upgrade.md)
* [Veelgestelde vragen over buildupgrades](../../platform/using/faq-build-upgrade.md)
* [&#x200B; Download de recentste Campaign Classic bouwt &#x200B;](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)
* [De nieuwe clientconsole beschikbaar maken voor gebruikers](../../installation/using/client-console-availability-for-windows.md)
