---
title: Campagnebeheerders migreren naar Adobe Identity Management System (IMS)
description: Leer hoe u campagneoperatoren kunt migreren naar Adobe Identity Management System (IMS)
exl-id: f01948c7-b523-492d-a4e8-67f4adde5fc5
source-git-commit: 9083c9c11b6b9c695cc98882e99ceb3cffc20ec7
workflow-type: tm+mt
source-wordcount: '1221'
ht-degree: 0%

---

# Campagnebeheerders migreren naar Adobe Identity Management System (IMS) {#migrate-users-to-ims}

Als onderdeel van de inspanning om veiligheid en authentificatieproces te versterken, adviseert Adobe Campaign hoogst om de wijze van de eindgebruikerauthentificatie van login/wachtwoord inheemse authentificatie aan het Systeem van AdobeIdentity Management (IMS) te migreren. Alle exploitanten moeten [Adobe Identity Management System (IMS)](https://helpx.adobe.com/enterprise/using/identity.html){target="_blank"} om verbinding te maken met Campagne.

In Campagne v8 is het niet langer toegestaan verbinding te maken met gebruiker/wachtwoord (ook wel native verificatie genoemd). **Adobe raadt aan deze migratie uit te voeren in Campagne v7.3.5 om probleemloos te kunnen migreren naar Campagne v8.**



## Wat is er veranderd?{#move-to-ims-changes}

Met Campaign Classic kunnen alle gewone gebruikers al verbinding maken met de Adobe Campaign-clientconsole via hun Adobe ID, via Adobe Identity Management System (IMS). De gebruikers-/wachtwoordverbindingen zijn echter nog steeds beschikbaar. Dit is niet langer toegestaan in Campaign v8.

Daarnaast roept de Adobe Campaign-clienttoepassing als onderdeel van de inspanningen om het beveiligings- en verificatieproces te versterken nu de campagne-API&#39;s rechtstreeks aan met het token van de technische IMS-account. Migratie voor technische operatoren wordt beschreven in een speciaal artikel, dat beschikbaar is in [deze pagina](ims-migration.md).

Deze wijziging is al van toepassing in Campaign Classic v7 en zal **verplicht** om naar Campagne v8 te gaan.

Adobe ondersteunt u bij deze migratieinspanning. In het onderstaande artikel vindt u gedetailleerde context- en stapsgewijze richtlijnen.

## Heb je invloed op?{#migrate-ims-impacts}

Deze procedure is van toepassing op alle campagnegebruikers die nog geen verbinding maken met Campagne met hun Adobe ID.

Als de exploitanten in uw organisatie met de cliëntconsole van de Campagne gebruikend hun login/wachtwoord verbinden (alias. (native verificatie), heeft dit invloed op u en moet u deze operator(s) migreren naar Adobe IMS, zoals hieronder beschreven.

Migratie naar [Adobe Identity Management System (IMS)](https://helpx.adobe.com/enterprise/using/identity.html){target="_blank"} is een beveiligingsvereiste om uw omgevingen veilig en gestandaardiseerd te maken, aangezien de meeste andere Adobe Experience Cloud-oplossingen en -toepassingen al op IMS zijn geïnstalleerd.

## Hoe migreren naar gehoste en Managed Services-omgevingen? {#ims-migration-procedure}

### Vereisten {#ims-migration-prerequisites}

Voordat u het migratieproces start, moet u contact opnemen met uw Adobe Transition Manager (voor Managed Services-klanten) of met de klantenservice van de Adobe (voor andere gehoste klanten), zodat de Adobe technische teams uw bestaande groepen Operator en benoemde rechten op het Adobe Identity Management System (IMS) kunnen migreren.

### Met IMS compatibele versies voor migratie {#ims-versions}

Een eerste vereiste voor deze migratie is het upgraden van uw omgeving naar een van de volgende productversies:

* Campagne v7.3.5 (aanbevolen)
* Campagne v7.3.3.IMS
  <!--* Campaign v7.3.2.IMS-->

Deze campagneversies worden gedetailleerd beschreven in de [Opmerkingen bij de release](../../rn/using/latest-release.md).

### Belangrijkste stappen {#ims-migration-steps}

De belangrijkste stappen voor deze migratie worden hieronder weergegeven:

1. Adobe verbetert uw omgevingen naar Campagne v7.3.5 (of een [Compatibele versie van IMS-migratie](#ims-versions)).
1. Na de upgrade kunt u nog steeds nieuwe gebruikers maken met beide methoden, als native gebruiker of met IMS.
1. Uw interne beheerder van de Campagne moet unieke e-mails toevoegen aan alle native gebruikers op de Campagne clientconsole en aan uw Adobe vertegenwoordiger/klantenservice bevestigen zodra dit is gebeurd.  Deze stap wordt beschreven in [deze sectie](#ims-migration-id).
1. Werk samen met uw Adobe-medewerker/klantenservice om een datum te beveiligen waarop de Adobe voor uw niet-technische gebruikers (operators) en productprofielen automatisch kan worden uitgevoerd. Deze stap vereist een uurvenster zonder onderbreking aan om het even welk van uw diensten.
1. Uw interne beheerder van de Campagne bevestigt deze veranderingen, en verstrekt aftekening. Na deze migratie moet u geen andere operator meer maken die wordt geverifieerd met zijn aanmeldingsnaam en wachtwoord.

U kunt uw technische operator(s) ook migreren naar Adobe Developer Console, zoals beschreven in [dit technote](ims-migration.md).

Zodra deze migratie is voltooid, moet u dit bevestigen bij uw Adobe Transition Manager (voor Managed Services-gebruikers) of bij de Adobe van de klantenservice (voor gehoste klanten). De Adobe markeert de migratie vervolgens als voltooid. Uw omgeving wordt dan beveiligd en gestandaardiseerd.


## Hoe kan ik hybride en onbedwingbare omgevingen migreren? {#ims-migration-procedure-on-prem}

De belangrijkste stappen voor deze migratie worden hieronder weergegeven:

1. Upgrade uw omgevingen naar Campagne versie 7.3.5 (of een [Compatibele versie van IMS-migratie](#ims-versions)).
1. Na de upgrade kunt u nog steeds nieuwe gebruikers maken met beide methoden, als native gebruiker of met IMS.
1. Uw interne Campagnebeheerder moet Adobe IMS configureren zoals beschreven in [deze sectie](../../integrations/using/configuring-ims.md).
1. Voeg vervolgens unieke e-mailberichten toe aan alle native gebruikers op de Campagne-clientconsole. Deze stap wordt beschreven in [deze sectie](#ims-migration-id).
1. Gebruikers en productprofielen maken in Adobe Admin Console, zoals beschreven in [Campagne v8-documentatie](https://experienceleague.adobe.com/docs/campaign/campaign-v8/admin/permissions/manage-permissions.html){target="_blank"}.
1. De optie **Verbinding maken met Adobe ID** voor alle operatoren.
1. Adobe IMS implementeren voor uw verbinding zoals beschreven in [deze pagina](../../integrations/using/implementing-ims.md).

U kunt uw technische operator(s) ook migreren naar Adobe Developer Console, zoals beschreven in [dit technote](ims-migration.md).


## Veelgestelde vragen {#ims-migration-faq}

### Wanneer kan ik de migratie starten? {#ims-migration-start}

Een aanbeveling voor de migratie naar [Adobe Identity Management System (IMS)](https://helpx.adobe.com/enterprise/using/identity.html){target="_blank"} is uw omgeving te upgraden naar Campaign Classic v7.3.5 (of een [Compatibele versie van IMS-migratie](#ims-versions)).

U kunt IMS-migratie starten in uw werkgebiedomgeving, zodra deze is bijgewerkt naar de nieuwste versie, en dienovereenkomstig plannen voor de productieomgeving.

### Wat gebeurt er na de upgrade van de build naar Campaign Classic v7.3.5? {#ims-migration-after-upgrade}

Nadat uw omgevingen zijn bijgewerkt naar Campaign Classic v7.3.5 (of een [Compatibele versie van IMS-migratie](#ims-versions)), kunt u de overgang starten naar [Adobe Identity Management System (IMS)](https://helpx.adobe.com/enterprise/using/identity.html){target="_blank"}.

### Wanneer is de migratie voltooid? {#ims-migration-end}

Zodra de migratie van eindgebruikers en de migratie van technische gebruikers naar het Adobe Identity Management System (IMS) is voltooid, moet u contact opnemen met uw Adobe/klantenondersteuning zodat de Adobe uw migratie als voltooid kan markeren.

### Hoe kunt u na de migratie gebruikers maken? {#ims-migration-native}

Adobe raadt aan alleen IMS-gebruikers te maken na upgrade naar Campaign Classic v7.3.5 (of een [Compatibele versie van IMS-migratie](#ims-versions)).

Als beheerder van de Campagne, kunt u toestemmingen aan de gebruikers van uw organisatie via Adobe Admin Console en de Console van de Cliënt van de Campagne verlenen. Gebruikers melden zich aan bij Adobe Campaign met hun Adobe ID. Leer hoe u machtigingen voor IMS instelt in [Campagne v8-documentatie](https://experienceleague.adobe.com/docs/campaign/campaign-v8/admin/permissions/gs-permissions.html){target="_blank"}.

### E-mails toevoegen voor huidige native gebruikers? {#ims-migration-id}

Als Campagnebeheerder moet u e-mailadressen toevoegen aan alle native gebruikers vanaf de clientconsole. Volg onderstaande stappen om dit te doen:

1. Verbinding maken met de clientconsole en bladeren naar **Beheer > Toegangsbeheer > Operatoren**.
1. Selecteer de operator die u wilt bijwerken in de lijst met operatoren.
1. Voer de e-mail van de operator in het dialoogvenster **Contactpunten** van het formulier met operatoren.
1. Sla uw wijzigingen op.

<!--You can also import a CSV file to update all your operator profiles with their email.-->


### Hoe u zich via IMS aanmeldt bij Campaign? {#ims-migration-log}

Leer hoe u verbinding kunt maken met uw Adobe ID in [deze sectie](../../integrations/using/implementing-ims.md).

### Zal er tijdens deze migratie een onderbreking plaatsvinden? {#ims-migration-downtime}

Om de migratie af te ronden (migreren van gebruikers en productprofielen), heeft de Adobe voor klanten van de Hosted en Managed Services een uur lang zonder downtime nodig (workflows, enz.).

Tijdens dit tijdsbestek moeten alle Campagnegebruikers zich afmelden en zich opnieuw aanmelden bij hun Adobe ID zodra de migratie naar IMS is voltooid.

Adobe raadt alle gebruikers sterk aan zich af te melden tijdens het migratievenster.

### De gebruikers in mijn organisatie gebruiken reeds IMS, moet ik nog migratie uitvoeren IMS?{#ims-migration-needed}

Deze migratie kent twee aspecten: migratie van eindgebruikers (plus productprofielen) en migratie van technische gebruikers (gebruikt in API&#39;s in uw aangepaste code).

Als al uw gebruikers (campagneexploitanten) op IMS zijn, zult u nog steeds uw Vertegenwoordiger/Klantenondersteuning van de Adobe moeten contacteren om de Migratie van de Profielen van het Product te plannen. U zult ook Technische gebruikers moeten migreren u in douanecode zou kunnen gebruikt. Meer informatie in [deze pagina](ims-migration.md).

## Nuttige koppelingen {#ims-useful-links}

* [Migratie van technische gebruikers naar Adobe Developer-console](ims-migration.md)
* [Opmerkingen bij de release van Adobe Campaign v8](../../rn/using/latest-release.md)
* [Wat is Adobe Identity Management System (IMS)](https://helpx.adobe.com/enterprise/using/identity.html){target="_blank"}
