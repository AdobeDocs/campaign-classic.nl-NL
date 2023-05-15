---
product: campaign
title: Migratie naar Campaign Classic
description: Leer hoe u van een vorige campagneversie naar Campaign Classic migreert
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: migration
content-type: reference
topic-tags: migration-overview
hide: true
hidefromtoc: true
exl-id: 3050238d-6f77-4ffa-9aef-677ab8009388
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 3%

---

# Aan de slag met de migratie{#about-migration}



In dit document worden de voorwaarden voor een migratie beschreven, de stappen voor een migratie naar Adobe Campaign Classic v7. De stappen en de facultatieve montages hangen van uw configuratie af.

Het migratieproces moet met de nodige voorzichtigheid worden uitgevoerd, de gevolgen ervan moeten van tevoren volledig in overweging worden genomen en de procedure moet strikt worden uitgevoerd. Deze mag alleen door een deskundige gebruiker worden uitgevoerd. We raden u aan contact op te nemen met [Adobe Klantenservice](https://helpx.adobe.com/nl/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) voordat een migratieprocedure wordt gestart.

De migratie moet vooraf op de test-/werkomgeving worden getest om ervoor te zorgen dat de migratie soepel en zonder fouten functioneert. Het migreren van de productieomgeving mag alleen worden uitgevoerd als de gemigreerde testomgeving volledig is gevalideerd.

>[!NOTE]
>
>De nieuwe functies en verbeteringen die met Adobe Campaign v7 worden geleverd, worden beschreven in het gedeelte [Opmerkingen bij de release](../../rn/using/latest-release.md).


## Vereisten

* Het migratieproces moet door deskundige gebruikers worden uitgevoerd. U moet door minstens een gegevensbestanddeskundige, een systeembeheerder en een toepassingsontwikkelaar van Adobe Campaign worden bijgestaan.
* Controleer voordat u de migratie start of de systemen en systeemonderdelen die u gebruikt compatibel zijn met versie 7. [Meer informatie](../../rn/using/compatibility-matrix.md).
* Als u Adobe Campaign Cloud Messaging (mid-sourcing implementatie) gebruikt, neemt u contact op met de klantenservice van de Adobe voordat u begint.
* Voordat u een migratieproces start, **moet** Maak een back-up van uw gegevens.
* Het migratieproces kan enkele dagen duren.
* Adobe Campaign v7 is een veiligere versie dan de vorige versie: dit is van invloed op configuratierichtlijnen om problemen zoals gegevenscorruptie te voorkomen en de gegevensintegriteit in de database te behouden . Als klant bent u verantwoordelijk voor het testen van alle configuraties, inclusief workflows.

Meer voorwaarden zijn beschikbaar in [deze pagina](../../migration/using/before-starting-migration.md).


## Moderne omgeving {#modernizing-your-environment}

Het uitvoeren van een migratie kan een kans zijn om uw omgeving (databasemotoren, besturingssystemen) bij te werken. Adobe Campaign raadt u ten zeerste aan uw productieomgevingen te upgraden naar de meest recente versies.

>[!CAUTION]
>
>Raadpleeg voor meer informatie over de versies die door Adobe Campaign v7 worden ondersteund de [Compatibiliteitsmatrix](../../rn/using/compatibility-matrix.md).

## Belangrijke migratiestappen {#key-migration-steps}

De algemene procedure voor migratie naar Adobe Campaign v7 wordt beschreven in [deze pagina](../../migration/using/before-starting-migration.md).


## Specifieke configuraties {#specific-configurations}

Door de wijzigingen die Adobe Campaign v7 aanbrengt, moet u mogelijk ook bepaalde specifieke configuraties aanpassen die in eerdere versies zijn ontwikkeld. Daarom kan het noodzakelijk zijn om een controle op al uw configuraties vóór de migratie uit te voeren: Neem contact op met Adobe Campaign voor hulp.

Bijvoorbeeld, zou de bijzondere aandacht aan specifieke montages voor de toepassingen van het Web, schemauitbreidingen met SQLdata of uit-van-de-doos schemakolonering moeten worden besteed. Raadpleeg [deze sectie](../../migration/using/configuring-your-platform.md) voor meer informatie.

Om te reageren op de toegenomen veiligheid in Adobe Campaign zijn ook enkele interne mechanismen gewijzigd: u moet deze configuraties dienovereenkomstig aanpassen.

