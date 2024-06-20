---
title: Migreren naar Adobe Identity Management System (IMS)
description: Leer hoe u uw verificatieproces kunt migreren naar Adobe Identity Management System (IMS)
source-git-commit: 106f0409f452595209f0e2aa2fa187a2e04338a9
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%

---

# Migreren naar Adobe Identity Management System (IMS) {#migrate-to-ims}

Als onderdeel van de inspanning om veiligheid en authentificatieproces te versterken, adviseert Adobe Campaign hoogst om de wijze van de eindgebruikerauthentificatie van login/wachtwoord inheemse authentificatie aan te migreren [Adobe Identity Management System (IMS)](https://helpx.adobe.com/enterprise/using/identity.html){target="_blank"}.

Bovendien roept de Adobe Campaign-clienttoepassing nu de campagne-API&#39;s rechtstreeks aan met behulp van het technische IMS-accounttoken. U moet uw technische operatoren migreren naar Adobe Developer Console.

>[!CAUTION]
>
>Deze wijziging is al van toepassing in Campaign Classic v7 en zal **verplicht** om naar Campagne v8 te gaan. Eigen gebruikers-/wachtwoordverificatie is niet toegestaan in Campagne v8. **Adobe raadt aan om deze migratie uit te voeren vanaf Campagne v7.3.5, zodat u probleemloos kunt migreren naar Campagne v8.**
>

## Migratiestappen {#ims-steps}

Migratie naar [Adobe Identity Management System (IMS)](https://helpx.adobe.com/enterprise/using/identity.html){target="_blank"} is een beveiligingsvereiste om uw omgevingen veilig en gestandaardiseerd te maken, aangezien de meeste andere Adobe Experience Cloud-oplossingen en -toepassingen al op IMS zijn geïnstalleerd.

Adobe ondersteunt u bij deze migratieinspanning. In de volgende artikelen vindt u gedetailleerde context- en stapsgewijze richtlijnen:

* De migratie voor de authentificatie van eindgebruikers wordt gedetailleerd in [deze pagina](migrate-users-to-ims.md).
* De migratie voor technische operatoren wordt in detail beschreven in [deze pagina](ims-migration.md).
* Vanaf Campagne v7.4.1, laat de gebruikersinterface en API beperkingen toe om opties en mogelijkheden te verwijderen die voor inheemse authentificatie specifiek zijn, zoals die in [deze pagina](impact-ims-migration.md).


## Met IMS compatibele versies voor migratie {#ims-versions}

Een eerste vereiste voor deze migratie is het upgraden van uw omgeving naar een van de volgende productversies:

* Campagne v7.4.1 (aanbevolen)
* Campagne v7.3.5
* Campagne v7.3.3.IMS
* Campagne v7.3.2.IMS

Deze campagneversies worden gedetailleerd beschreven in de [Opmerkingen bij de release](../../rn/using/latest-release.md).

## Veelgestelde vragen {#ims-migration-faq}

### Wanneer kan ik de migratie starten? {#ims-migration-start}

Een aanbeveling voor de migratie naar [Adobe Identity Management System (IMS)](https://helpx.adobe.com/enterprise/using/identity.html){target="_blank"} is uw omgeving te upgraden naar Campaign Classic v7.4.1 (of een [Compatibele versie van IMS-migratie](#ims-versions)).

U kunt IMS-migratie starten in uw werkgebiedomgeving, zodra deze is bijgewerkt naar de nieuwste versie, en dienovereenkomstig plannen voor de productieomgeving.

### Wat gebeurt er na de upgrade van de build naar Campaign Classic v7.4.1? {#ims-migration-after-upgrade}

Nadat uw omgevingen zijn bijgewerkt naar Campaign Classic v7.4.1 (of een [Compatibele versie van IMS-migratie](#ims-versions)), kunt u de overgang starten naar [Adobe Identity Management System (IMS)](https://helpx.adobe.com/enterprise/using/identity.html){target="_blank"}.

### Wanneer is de migratie voltooid? {#ims-migration-end}

Wanneer de migratie van eindgebruikers en de migratie van technische operatoren naar het Adobe Identity Management System (IMS) is voltooid, moet u uw omgeving bijwerken om opties te verwijderen die specifiek zijn voor de native verificatie en niet meer van toepassing zijn met IMS-verificatie. Deze update is alleen beschikbaar vanaf Campagne versie 7.4.1. [Meer informatie](impact-ims-migration.md)



## Nuttige koppelingen {#ims-useful-links}

* [Migratie van eindgebruikers naar IMS](migrate-users-to-ims.md)
* [Migratie van technische operatoren naar Adobe Developer-console](ims-migration.md)
* [Opmerkingen bij de nieuwste release van Adobe Campaign Classic v7](../../rn/using/latest-release.md)
* [Wat is Adobe Identity Management System (IMS)](https://helpx.adobe.com/enterprise/using/identity.html){target="_blank"}
