---
product: campaign
title: Migratie naar Campaign Classic
description: Leer hoe u kunt migreren naar een Campaign Classic van een vorige campagneversie
feature: Upgrade
audience: migration
content-type: reference
topic-tags: migration-overview
hide: true
hidefromtoc: true
exl-id: 3050238d-6f77-4ffa-9aef-677ab8009388
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 2%

---

# Aan de slag met de migratie{#about-migration}



In dit document worden de voorwaarden voor een migratie beschreven, de stappen voor een migratie naar Adobe Campaign Classic v7. De stappen en de facultatieve montages hangen van uw configuratie af.

Het migratieproces moet met de nodige voorzichtigheid worden uitgevoerd, de gevolgen ervan moeten van tevoren volledig in overweging worden genomen en de procedure moet strikt worden uitgevoerd. Deze mag alleen door een deskundige gebruiker worden uitgevoerd. Wij adviseren sterk in contact met [ de Zorg van de Klant van de Adobe ](https://helpx.adobe.com/nl/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) alvorens om het even welke migratieprocedure te beginnen.

De migratie moet vooraf op de test-/werkomgeving worden getest om ervoor te zorgen dat de migratie soepel en zonder fouten functioneert. Het migreren van de productieomgeving mag alleen worden uitgevoerd als de gemigreerde testomgeving volledig is gevalideerd.

>[!NOTE]
>
>De nieuwe eigenschappen en de verbeteringen die met Adobe Campaign v7 komen worden gedetailleerd in de [ Nota&#39;s van de Versie ](../../rn/using/latest-release.md).


## Vereisten

* Het migratieproces moet door deskundige gebruikers worden uitgevoerd. U moet door minstens een gegevensbestanddeskundige, een systeembeheerder en een toepassingsontwikkelaar van Adobe Campaign worden bijgestaan.
* Controleer voordat u de migratie start of de systemen en systeemonderdelen die u gebruikt compatibel zijn met versie 7. [Meer informatie](../../rn/using/compatibility-matrix.md).
* Als u Adobe Campaign Cloud Messaging (mid-sourcing implementatie) gebruikt, neemt u contact op met de klantenservice van de Adobe voordat u begint.
* Alvorens een migratieproces te beginnen, moet u **** file uw gegevens.
* Het migratieproces kan enkele dagen duren.
* Adobe Campaign v7 is een veiligere versie dan de vorige versie: dit is van invloed op configuratierichtlijnen om problemen zoals gegevenscorruptie te voorkomen en gegevensintegriteit in de database te behouden. Als klant bent u verantwoordelijk voor het testen van alle configuraties, inclusief workflows.

Meer eerste vereisten zijn beschikbaar in [ deze pagina ](../../migration/using/before-starting-migration.md).


## Moderne omgeving {#modernizing-your-environment}

Het uitvoeren van een migratie kan een kans zijn om uw omgeving (databasemotoren, besturingssystemen) bij te werken. Adobe Campaign raadt u ten zeerste aan uw productieomgevingen te upgraden naar de meest recente versies.

>[!CAUTION]
>
>Voor verdere informatie over de versies die door Adobe Campaign v7 worden gesteund, verwijs naar de [ matrijs van de Verenigbaarheid ](../../rn/using/compatibility-matrix.md).

## Belangrijke migratiestappen {#key-migration-steps}

De algemene procedure voor het migreren naar Adobe Campaign v7 wordt gedetailleerd in [ deze pagina ](../../migration/using/before-starting-migration.md).


## Specifieke configuraties {#specific-configurations}

Door de wijzigingen die Adobe Campaign v7 aanbrengt, moet u mogelijk ook bepaalde specifieke configuraties aanpassen die in eerdere versies zijn ontwikkeld. Daarom kan het nodig zijn om een controle uit te voeren op al uw configuraties vóór de migratie: neem contact op met Adobe Campaign voor hulp.

Bijvoorbeeld, zou de bijzondere aandacht aan specifieke montages voor de toepassingen van het Web, schemauitbreidingen met SQLdata of uit-van-de-doos schemakolonering moeten worden besteed. Raadpleeg [deze sectie](../../migration/using/configuring-your-platform.md) voor meer informatie.

Om te kunnen reageren op de verhoogde veiligheid in Adobe Campaign zijn enkele interne mechanismen gewijzigd: u moet deze configuraties dienovereenkomstig aanpassen.

