---
title: Campagnebeheerders migreren naar Adobe Identity Management System (IMS)
description: Leer hoe u campagneoperatoren kunt migreren naar Adobe Identity Management System (IMS)
exl-id: f01948c7-b523-492d-a4e8-67f4adde5fc5
source-git-commit: 02ecc0e6bb3bd361f512baeefc9e0f2271063387
workflow-type: tm+mt
source-wordcount: '1217'
ht-degree: 1%

---

# Campagnebeheerders migreren naar Adobe Identity Management System (IMS) {#migrate-users-to-ims}

Als onderdeel van de inspanningen om het beveiligings- en verificatieproces te versterken, raadt Adobe Campaign u ten zeerste aan de modus voor verificatie van eindgebruikers te migreren van de native aanmelding/wachtwoord-verificatie naar Adobe Identity Management System (IMS). Alle exploitanten zouden [&#x200B; het Systeem van Adobe Identity Management (IMS) &#x200B;](https://helpx.adobe.com/nl/enterprise/using/identity.html){target="_blank"} moeten uitvoeren om met Campagne te verbinden.

Leer meer over deze migratie in [&#x200B; deze pagina &#x200B;](ac-ims.md).

## Wat is er veranderd? {#move-to-ims-changes}

Met Campaign Classic kunnen alle gewone gebruikers al verbinding maken met de Adobe Campaign-clientconsole via hun Adobe ID, via Adobe Identity Management System (IMS). De gebruikers-/wachtwoordverbindingen zijn echter nog steeds beschikbaar. Dit is niet langer toegestaan in Campaign v8.

Daarnaast roept de Adobe Campaign-clienttoepassing als onderdeel van de inspanningen om het beveiligings- en verificatieproces te versterken nu de campagne-API&#39;s rechtstreeks aan met het token van de technische IMS-account. De migratie voor technische exploitanten is gedetailleerd in een specifiek artikel, beschikbaar in [&#x200B; deze pagina &#x200B;](ims-migration.md).

Deze verandering is reeds van toepassing in Campaign Classic v7, en zal **verplicht** zijn om zich naar Campagne v8 te bewegen.

Adobe ondersteunt u bij deze migratie. In het onderstaande artikel vindt u gedetailleerde context- en stapsgewijze richtlijnen.

## Heb je invloed op?{#migrate-ims-impacts}

Deze procedure is van toepassing op alle campagnegebruikers die nog geen verbinding maken met Campagne met hun Adobe ID.

Als de exploitanten in uw organisatie met de cliëntconsole van de Campagne gebruikend hun login/wachtwoord verbinden (alias. (native verificatie), heeft dit invloed op u en moet u deze operator(s) migreren naar Adobe IMS, zoals hieronder beschreven.

De migratie aan [&#x200B; Identity Management Systeem van Adobe (IMS) &#x200B;](https://helpx.adobe.com/nl/enterprise/using/identity.html){target="_blank"} is een veiligheidsvereiste om uw milieu&#39;s veilig en gestandaardiseerd te maken, aangezien de meeste andere oplossingen en apps van Adobe Experience Cloud reeds op IMS zijn.

Deze verandering is van toepassing beginnend Campaign Classic v7.4.1 (en recentste [&#x200B; IMS migratie compatibele versies &#x200B;](ac-ims.md#ims-versions)) en is **verplicht** om zich naar Adobe Campaign v8 te bewegen.

>[!IMPORTANT]
>
>**de toegangseffect van het Comité van de Controle**
>
>Wanneer u uw gebruikers naar IMS migreert, moet u er rekening mee houden dat elk productprofiel in de Adobe Admin Console dat het woord &quot;admin&quot; in de naam bevat (zoals &quot;Beheerders&quot;, &quot;admin&quot;, &quot;admins&quot;, &quot;approval admin&quot; enz.) automatisch toegang verleent tot het Configuratiescherm. Het Controlebord is een zelfbedienend hulpmiddel dat het aanbrengen van significante veranderingen in de instanties van de Campagne toestaat.
>
>Controleer zorgvuldig de naamgevingsconventies van het productprofiel om ervoor te zorgen dat alleen geautoriseerde gebruikers toegang hebben tot het Configuratiescherm. Leer meer over het beheren van de toestemmingen van het Controlebord in de [&#x200B; documentatie van het Controlebord &#x200B;](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html?lang=nl-NL){target="_blank"}.


## Hoe migreren naar gehoste en Managed Services-omgevingen? {#ims-migration-procedure}

### Vereisten {#ims-migration-prerequisites}

Voordat u het migratieproces start, moet u contact opnemen met uw Adobe Transition Manager (voor Managed Services-klanten) of met de Adobe Customer Care (voor andere gehoste klanten), zodat Adobe Technical Teams uw bestaande Operator groups en Named Rights kunnen migreren naar Adobe Identity Management System (IMS).

### Belangrijkste stappen {#ims-migration-steps}

De belangrijkste stappen voor deze migratie worden hieronder weergegeven:

1. Adobe verbetert uw milieu&#39;s aan Campagne v7.4.1 (of een [&#x200B; IMS migratie compatibele versie &#x200B;](ac-ims.md#ims-versions)).
1. Na de upgrade kunt u nog steeds nieuwe gebruikers maken met beide methoden, als native gebruiker of met IMS.
1. Uw interne beheerder van de Campagne moet unieke e-mails toevoegen aan alle native gebruikers op de Campagne-clientconsole en uw Adobe-vertegenwoordiger/klantenservice bevestigen zodra dit is gebeurd.  Deze stap wordt gedetailleerd in [&#x200B; deze sectie &#x200B;](#ims-migration-id).
1. Werk samen met uw Adobe-vertegenwoordiger/klantenservice om een datum te beveiligen waarop Adobe de automatische migratie voor uw niet-technische gebruikers (operators) en productprofielen kan uitvoeren. Deze stap vereist een uurvenster zonder onderbreking aan om het even welk van uw diensten.
1. Uw interne beheerder van de Campagne bevestigt deze veranderingen, en verstrekt aftekening. Na deze migratie moet u geen andere operator meer maken die wordt geverifieerd met zijn aanmeldingsnaam en wachtwoord.

U kunt uw technische exploitant(s) aan Adobe Developer Console ook migreren zoals die in [&#x200B; wordt gedetailleerd dit technische &#x200B;](ims-migration.md).

Zodra deze migratie is voltooid, bevestigt u dit aan uw Adobe Transition Manager (voor Managed Services-gebruikers) of aan de klantenservice van Adobe (voor gehoste klanten). Adobe markeert de migratie vervolgens als voltooid. Uw omgeving wordt dan beveiligd en gestandaardiseerd.


## Hoe kan ik hybride en on-premise omgevingen migreren? {#ims-migration-procedure-on-prem}

De belangrijkste stappen voor deze migratie worden hieronder weergegeven:

1. Bevorder uw milieu&#39;s aan Campagne v7.4.1 (of een [&#x200B; migratie IMS compatibele versie &#x200B;](#ims-versions)).
1. Na de upgrade kunt u nog steeds nieuwe gebruikers maken met beide methoden, als native gebruiker of met IMS.
1. Uw interne Beheerder van de Campagne moet Adobe IMS zoals gedetailleerd in [&#x200B; vormen deze sectie &#x200B;](../../integrations/using/configuring-ims.md).
1. Voeg vervolgens unieke e-mailberichten toe aan alle native gebruikers op de Campagne-clientconsole. Deze stap wordt gedetailleerd in [&#x200B; deze sectie &#x200B;](#ims-migration-id).
1. Creeer gebruikers en productprofielen in Adobe Admin Console zoals die in [&#x200B; worden gedetailleerd de documentatie van de Campagne v8 &#x200B;](https://experienceleague.adobe.com/docs/campaign/campaign-v8/admin/permissions/manage-permissions.html){target="_blank"}.
1. Laat **verbinden met Adobe ID** optie voor alle exploitanten toe.
1. Voer Adobe IMS voor uw verbinding zoals die in [&#x200B; wordt gedetailleerd deze pagina &#x200B;](../../integrations/using/implementing-ims.md) uit.

U kunt uw technische exploitant(s) aan Adobe Developer Console ook migreren zoals die in [&#x200B; wordt gedetailleerd dit technische &#x200B;](ims-migration.md).


## Veelgestelde vragen {#ims-migration-faq}

### Hoe kunt u na de migratie gebruikers maken? {#ims-migration-native}

Adobe adviseert om slechts gebruikers tot stand te brengen IMS na bevordering aan Campaign Classic v7.4.1 (of een [&#x200B; IMS migratie compatibele versie &#x200B;](#ims-versions)).
Beginnende Campagne v7.4.1, kunt u inheemse operatorverwezenlijking verhinderen door uw instantieconfiguratie zoals die in [&#x200B; wordt gedetailleerd deze pagina &#x200B;](impact-ims-migration.md) bij te werken.

Als beheerder van de Campagne, kunt u toestemmingen aan de gebruikers van uw organisatie via Adobe Admin Console en de Console van de Cliënt van de Campagne verlenen. Gebruikers melden zich aan bij Adobe Campaign met hun Adobe ID. Leer hoe te opstellingstoestemmingen met IMS in [&#x200B; Campagne v8 documentatie &#x200B;](https://experienceleague.adobe.com/docs/campaign/campaign-v8/admin/permissions/gs-permissions.html){target="_blank"}.

### E-mails toevoegen voor huidige native gebruikers? {#ims-migration-id}

Als Campagnebeheerder moet u e-mailadressen toevoegen aan alle native gebruikers vanaf de clientconsole. Volg onderstaande stappen om dit te doen:

1. Verbind met de cliëntconsole en doorblader aan **Beleid > het Beheer van de Toegang > Exploitanten**.
1. Selecteer de operator die u wilt bijwerken in de lijst met operatoren.
1. Ga e-mail van de exploitant in de **sectie van de Contactpunten** van de exploitantvorm in.
1. Sla uw wijzigingen op.

<!--You can also import a CSV file to update all your operator profiles with their email.-->


### Hoe u zich via IMS aanmeldt bij Campaign? {#ims-migration-log}

Leer hoe te met Campagne met uw Adobe ID in [&#x200B; te verbinden deze sectie &#x200B;](../../integrations/using/implementing-ims.md).

### Zal er tijdens deze migratie een onderbreking plaatsvinden? {#ims-migration-downtime}

Voor klanten met gehoste en Managed Services is voor het voltooien van de migratie (migreren van gebruikers en productprofielen) een periode van één uur zonder downtime vereist voor Adobe (workflows, enz.).

Tijdens dit tijdsbestek moeten alle Campagnegebruikers zich afmelden en zich opnieuw aanmelden bij hun Adobe ID zodra de migratie naar IMS is voltooid.

Adobe raadt alle gebruikers sterk aan zich af te melden tijdens het migratievenster.

### De gebruikers in mijn organisatie gebruiken reeds IMS, moet ik nog migratie uitvoeren IMS?{#ims-migration-needed}

Deze migratie kent twee aspecten: migratie van eindgebruikers (plus productprofielen) en migratie van technische gebruikers (gebruikt in API&#39;s in uw aangepaste code).

Als al uw gebruikers (campagneoperatoren) op IMS zijn, moet u nog steeds contact opnemen met uw Adobe-vertegenwoordiger/Klantenondersteuning om de migratie van productprofielen te plannen. U zult ook Technische gebruikers moeten migreren u in douanecode zou kunnen gebruikt. Meer informatie vindt u [op deze pagina](ims-migration.md).

### Hoe te om het de authentificatietype van uw Operatoren te bekijken?

Leer hoe te om het authentificatietype van uw Exploitanten in Campagne te bekijken:

1. Van de **Ontdekkingsreiziger**, toegang **Beleid** `>` **Toegangsbeheer** `>` **Operatoren**.

1. Klik de kopbalrij met de rechtermuisknop aan en selecteer **vormen lijst** menu.

   ![](assets/ims_2.png)

1. Voeg **Gehandicapte Rekening** en **Type van Authentificatie** als **kolommen van de Output** toe.

   ![](assets/ims_1.png)

U kunt de lijst van uw **Operatoren** en hun **Type van Authentificatie** nu zien.

![](assets/ims_3.png)


>[!MORELIKETHIS]
>
>* [&#x200B; Migratie van technische gebruikers aan de console van Adobe Developer &#x200B;](ims-migration.md)
>* [&#x200B; de versienota&#39;s van Adobe Campaign Classic v7 &#x200B;](../../rn/using/latest-release.md)
>* [&#x200B; wat is het Systeem van Adobe Identity Management (IMS) &#x200B;](https://helpx.adobe.com/nl/enterprise/using/identity.html){target="_blank"}
