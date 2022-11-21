---
product: campaign
title: TechNote - Adobe Campaign-systeemupgrades
description: Adobe Campaign-systeemupgrade
hide: true
hidefromtoc: true
source-git-commit: b119d52b94d95086261fcdc1744698a78296df9c
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 9%

---

# Adobe Campaign 2023-systeemupgrade {#ac-system-upgrade}

De campagneinfrastructuur is afhankelijk van systemen van derden die regelmatig moeten worden bijgewerkt met de systeemversies en -oplossingen. Deze updates zijn verplicht om de continuïteit van de service en veilige Campagneomgevingen tegen beveiligingsrisico&#39;s te garanderen. Daarnaast zijn upgrades vereist om deze uit te lijnen met systeemwijzigingen van derden.

Als **Ontvangen of Beheerde klant van Cloud Services** Adobe informeert u over deze upgrades wanneer deze nodig zijn. U moet uw omgevingen upgraden in overeenstemming met de aanbevelingen om naleving te garanderen.

Als **Op locatie of hybride klant** Adobe raadt u dan ook ten zeerste aan uw systeem- en campagneversies volgens dezelfde kalender te upgraden.

Om veiligheidsredenen moet u [De nieuwste build voor campagne installeren](#ac-upgrade)en upgrade vervolgens uw [besturingssysteem](#os-upgrade) en/of uw [Relation Database Management System (RDBMS)](#pg-upgrade).

>[!NOTE]
>
>Voor vragen over deze wijzigingen neemt u contact op met de [Adobe-klantenservice](https://helpx.adobe.com/nl/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

## Verbetering van campagne-build {#ac-upgrade}

**Heeft dit gevolgen voor u?**

Als de [besturingssysteemupgrade](#os-upgrade) en/of de [upgrade van databasesysteem](#pg-upgrade) hieronder beschreven, moet u uw milieu&#39;s van de Campagne aan de recentste versie 7.3.2 bevorderen, die met deze systemen compatibel is.

**Hoe kan ik bijwerken?**

* Als ontvangen of Beheerde klant van Cloud Services, zal Adobe u contacteren en uw versie van de Campagne bevorderen.
* Als hybride klant, zal Adobe u van de geplande bouwstijlverbeteringsdata voor uw midsourcingmilieu op de hoogte brengen. U moet ook uw marketingomgeving upgraden naar dezelfde versie.
* Als klant op locatie wordt u gevraagd om uw Campagneomgevingen te upgraden naar de nieuwste versie van 7.3.2.


## Upgrade van besturingssysteem {#os-upgrade}

**Heeft dit gevolgen voor u?**

Als u Campagne op een Debian werkend systeem in werking stelt, om van de recentste beveiligingsupdates van Debian te profiteren, moet u uw infrastructuur van de Campagne verplaatsen naar **Debian 11**. Merk op dat Debian 9 Einde van het Leven op 30 juni 2022 bereikte, en niet meer veiligheidsmoeilijke situaties verstrekt.

**Hoe kan ik bijwerken?**

* Als ontvangen of Beheerde klant van Cloud Services, zal Adobe u contacteren en uw milieu bevorderen.
* Als hybride klant, zal Adobe u van de geplande verbeteringsdata voor uw midsourcingmilieu op de hoogte brengen. Als uw marketing milieu ook op Debian loopt, moet u het aan Debian 11 ook bevorderen.
* Als klant op locatie wordt u gevraagd uw omgevingen te upgraden naar Debian 11.

## Upgrade van databasesysteem {#pg-upgrade}

**Heeft dit gevolgen voor u?**

Als uw gegevensbestandsysteem voor Campagne PostSQL is, om van recentste innovaties en veiligheidsupdates te profiteren PostgreSQL, moet u bevorderen om **PostgreSQL 14**. Merk op dat PostreSQL 11 op 30 november 2022 het Eind van het Leven zal bereiken.

**Hoe kan ik bijwerken?**

* Als ontvangen of Beheerde klant van Cloud Services, zal Adobe u contacteren en uw gegevensbestandsysteem van PostgreSQL 11 aan PostgreSQL 14 bevorderen.
* Als hybride klant, als uw marketing gegevensbestandsysteem PostgreSQL is, moet u het bevorderen aan PostgreSQL 14.
* Als klant op locatie wordt u gevraagd uw databasesysteem bij te werken naar PostgreSQL 14. ../integrations/using/configuring-adobe-io.md).


## Nuttige koppelingen

* [Upgrade uw omgeving](../../production/using/build-upgrade.md)
* [Veelgestelde vragen over buildupgrades](../../platform/using/faq-build-upgrade.md)
* [Campaign Classic-build downloaden](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)
* [De nieuwe clientconsole beschikbaar maken voor gebruikers](../../installation/using/client-console-availability-for-windows.md)
