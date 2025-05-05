---
title: Migreren naar Adobe Identity Management System (IMS)
description: Leer hoe u uw verificatieproces kunt migreren naar Adobe Identity Management System (IMS)
exl-id: 84853dbe-8b6f-4875-b29a-c1b755423a3c
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%

---

# Migreren naar Adobe Identity Management System (IMS) {#migrate-to-ims}

Als deel van de inspanning om veiligheid en authentificatieproces te versterken, adviseert Adobe Campaign hoogst om de wijze van de eindgebruikersauthentificatie van login/wachtwoord inheemse authentificatie aan [ Adobe Identity Management Systeem (IMS) te migreren ](https://helpx.adobe.com/enterprise/using/identity.html){target="_blank"} .

Bovendien roept de Adobe Campaign-clienttoepassing nu de campagne-API&#39;s rechtstreeks aan met behulp van het technische IMS-accounttoken. U moet uw technische operatoren migreren naar Adobe Developer Console.

>[!CAUTION]
>
>Deze verandering is reeds van toepassing in Campaign Classic v7, en zal **verplicht** zijn om zich naar Campagne v8 te bewegen. Eigen gebruikers-/wachtwoordverificatie is niet toegestaan in Campagne v8. **Adobe adviseert om deze migratie uit te voeren die Campagne v7.3.5 beginnen om vlot aan Campagne v8 te kunnen migreren.**
>

## Migratiestappen {#ims-steps}

De migratie aan [ Systeem van Identity Management van de Adobe (IMS) ](https://helpx.adobe.com/enterprise/using/identity.html){target="_blank"}  is een veiligheidsvereiste om uw milieu&#39;s veilig en gestandaardiseerd te maken, aangezien de meeste andere oplossingen en apps van Adobe Experience Cloud reeds op IMS zijn.

Adobe ondersteunt u bij deze migratieinspanning. In de volgende artikelen vindt u gedetailleerde context- en stapsgewijze richtlijnen:

* De migratie voor eindgebruikerauthentificatie wordt gedetailleerd in [ deze pagina ](migrate-users-to-ims.md).
* De migratie voor technische operatorauthentificatie wordt gedetailleerd in [ deze pagina ](ims-migration.md).
* Beginnende Campagne v7.4.1, laat de gebruikersinterface en API beperkingen toe om opties en mogelijkheden te verwijderen die voor inheemse authentificatie specifiek zijn, zoals die in [ wordt gedetailleerd deze pagina ](impact-ims-migration.md).


## Met IMS compatibele versies voor migratie {#ims-versions}

Een eerste vereiste voor deze migratie is het upgraden van uw omgeving naar een van de volgende productversies:

* Campagne v7.4.1 (aanbevolen)
* Campagne v7.3.5
* Campagne v7.3.3.IMS
* Campagne v7.3.2.IMS

Deze versies van de Campagne zijn gedetailleerd in de [ Nota&#39;s van de Versie ](../../rn/using/latest-release.md).

## Veelgestelde vragen {#ims-migration-faq}

### Wanneer kan ik de migratie starten? {#ims-migration-start}

Een aanbeveling voor de migratie aan [ het Systeem van Identity Management van de Adobe (IMS) ](https://helpx.adobe.com/enterprise/using/identity.html){target="_blank"}  moet uw milieu aan Campaign Classic v7.4.1 (of een [ IMS migratie compatibele versie ](#ims-versions) bevorderen).

U kunt IMS-migratie starten in uw werkgebiedomgeving, zodra deze is bijgewerkt naar de nieuwste versie, en dienovereenkomstig plannen voor de productieomgeving.

### Wat gebeurt er na de upgrade van de build naar Campaign Classic v7.4.1? {#ims-migration-after-upgrade}

Nadat uw milieu&#39;s aan Campaign Classic v7.4.1 (of een [ IMS migratie compatibele versie ](#ims-versions)) zijn bevorderd, kunt u uw overgang aan [ in werking stellen Identity Management Systeem van de Adobe (IMS) ](https://helpx.adobe.com/enterprise/using/identity.html){target="_blank"} .

### Wanneer is de migratie voltooid? {#ims-migration-end}

Wanneer de migratie van eindgebruikers en de migratie van technische operatoren naar het Adobe Identity Management System (IMS) is voltooid, moet u uw omgeving bijwerken om opties te verwijderen die specifiek zijn voor de native verificatie en niet meer van toepassing zijn met IMS-verificatie. Deze update is slechts beschikbaar beginnend Campagne v7.4.1. [ leer meer ](impact-ims-migration.md)



## Nuttige koppelingen {#ims-useful-links}

* [Migratie van eindgebruikers naar IMS](migrate-users-to-ims.md)
* [Migratie van technische operatoren naar Adobe Developer-console](ims-migration.md)
* [Opmerkingen bij de nieuwste release van Adobe Campaign Classic v7](../../rn/using/latest-release.md)
* [ wat is het Systeem van Identity Management van de Adobe (IMS) ](https://helpx.adobe.com/enterprise/using/identity.html){target="_blank"} 
