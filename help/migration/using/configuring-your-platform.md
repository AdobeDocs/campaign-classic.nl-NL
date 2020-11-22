---
solution: Campaign Classic
product: campaign
title: Uw platform configureren
description: Uw platform configureren
audience: migration
content-type: reference
topic-tags: migration-procedure
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '940'
ht-degree: 1%

---


# Uw platform configureren{#configuring-your-platform}

Bepaalde belangrijke wijzigingen in Adobe Campaign v7 vereisen een configuratie om ervoor te zorgen dat deze effectief werkt. Deze parameters kunnen nodig zijn voor of na het migreren. De betrokken veranderingen en hun configuratiewijze worden voorgesteld in deze sectie.

Tijdens migratie, wordt de **lijst NmsRecipient** herbouwd van de schemadefinitie. Eventuele wijzigingen die buiten Adobe Campaign in de SQL-structuur van deze tabel zijn aangebracht, gaan verloren.

Voorbeeldelementen om te controleren:

* Als u een kolom (of een index) in de **lijst NmsRecipient** hebt toegevoegd maar u hebt niet het in het schema gedetailleerd, zal dit niet worden bewaard.
* Het **tabelruimteattribuut** neemt standaard zijn waarden terug, met andere woorden die in de plaatsingstovenaar worden bepaald.
* Als u een verwijzingsmening aan de lijst NmsRecipient hebt toegevoegd, moet u het schrappen alvorens zich te migreren.

Deze waarschuwing heeft ook betrekking op Oracle-gebruikers: als u de optie **usetimestamptz:1** tijdens een postupgrade hebt toegevoegd (zie [Tijdzones](../../migration/using/general-configurations.md#time-zones)), worden alle tabellen met ten minste één **datum+tijd** -veld opnieuw samengesteld.

## Voor de migratie {#before-the-migration}

Bij het migreren naar Adobe Campaign v7 moeten de volgende elementen worden geconfigureerd. Deze elementen moeten worden behandeld alvorens met de **postupgrade** te beginnen.

* Tijdzones

   Tijdens een migratie vanaf een v5.11-platform moet u opgeven welke tijdzone u tijdens de postupgrade wilt gebruiken.

   Raadpleeg de sectie [Tijdzones](../../migration/using/general-configurations.md#time-zones) als u de modus Meerdere tijdzones wilt gebruiken.

   Als u Oracle als database gebruikt, moet u controleren of de Oracle-tijdzonebestanden correct zijn gesynchroniseerd tussen de toepassingsserver en de databaseserver. For more on this, refer to the [Oracle](../../migration/using/general-configurations.md#oracle) section.

* Beveiligingszones

   Om veiligheidsredenen is het Adobe Campaign-platform niet meer standaard toegankelijk: u moet de veiligheidsstreken vormen, die het verzamelen van de gebruikersIP adressen vóór de migratie vereist.

   For more information, refer to the [Security](../../migration/using/general-configurations.md#security) section.

* Syntaxis

   Bepaalde syntaxis in JavaScript wordt mogelijk geaccepteerd in versies 5.11 en 6.02 en wordt niet meer geaccepteerd in versie 7, omdat er een nieuwe interpreter wordt gebruikt. For more information, refer to the [JavaScript](../../migration/using/general-configurations.md#javascript) section.

   Op dezelfde manier wordt in Adobe Campaign v7 een nieuwe syntaxis geïntroduceerd die de op SQLData gebaseerde syntaxis vervangt. Als u code-elementen met deze syntaxis gebruikt, moet u deze aanpassen. For more information, refer to the [SQLData](../../migration/using/general-configurations.md#sqldata) section.

* Wachtwoorden

   U moet de **wachtwoorden Admin** en **Internal** configureren. For more information, refer to the [User passwords](../../migration/using/before-starting-migration.md#user-passwords) section.

* Boomstructuur

   Als u migreert vanaf een v5.11-platform, moet u de structuurmappen opnieuw ordenen volgens de Adobe Campaign v6-normen. Raadpleeg de sectie Structuur [van de](../../migration/using/specific-configurations-in-v5-11.md#campaign-vseven-tree-structure) Adobe Campaign v7-structuur voor meer informatie.

* Interaction

   Als u **Interactie** gebruikt, moet u alle 6.02 schemaverwijzingen schrappen die niet meer in v7 bestaan. For more information, refer to the [Interaction](../../migration/using/general-configurations.md#interaction) section.

## Na de migratie {#after-the-migration}

Na het runnen van **postupgrade**, moeten de volgende elementen in aanmerking worden genomen en de overeenkomstige configuraties uitgevoerd.

* Pagina&#39;s spiegelen

   Het aanpassingsblok van de pagina Mirror is gewijzigd met v6.x. Deze nieuwe versie verbetert de beveiliging bij het openen van deze pagina&#39;s.

   Als u het v5-verpersoonlijkingsblok in uw berichten hebt gebruikt, mislukt de weergave van de spiegelpagina. Adobe adviseert hoogst om het nieuwe verpersoonlijkingsblok te gebruiken wanneer het opnemen van spiegelpagina in uw berichten.

   Nochtans, als tijdelijke oplossing (en aangezien de spiegelpagina&#39;s nog leven), kunt u aan het oude verpersoonlijkingsblok terugkeren om dit probleem te vermijden door de optie te veranderen **[!UICONTROL XtkAcceptOldPasswords]** en het te plaatsen aan **[!UICONTROL 1]**. Dit heeft geen invloed op het gebruik van het nieuwe personalisatieblok v6.x.

* Syntaxis

   Als er fouten optreden die te maken hebben met de syntaxis, moet u tijdens de postupgrade de optie **allowSQLInjection** tijdelijk activeren in het bestand **serverConf.xml** , omdat u dan tijd hebt om de code te herschrijven. Nadat de code is aangepast, moet u de beveiliging opnieuw activeren. For more on this, refer to the [SQLData](../../migration/using/general-configurations.md#sqldata) section.

* Conflicten

   De migratie wordt uitgevoerd via een postupgrade en conflicten kunnen optreden in rapporten, formulieren of webtoepassingen. Deze conflicten kunnen vanaf de console worden opgelost.

   Zie de sectie [Conflicten](../../migration/using/general-configurations.md#conflicts) .

* Tomcat

   Als u de installatiemap hebt aangepast, moet u controleren of deze na de migratie correct is bijgewerkt. Raadpleeg de sectie [Tomcat](../../migration/using/general-configurations.md#tomcat) voor meer informatie.

* Rapporten

   Alle out-of-box-rapporten gebruiken momenteel de v6.x-renderingengine. Als u JavaScript-code hebt toegevoegd aan de rapporten, kunnen bepaalde elementen worden gewijzigd.

   Raadpleeg de sectie [Rapporten](../../migration/using/general-configurations.md#reports) .

* Webtoepassingen

   Na postupgrade, als u om het even welke problemen hebt die met uw geïdentificeerde toepassingen van het Web verbinden, moet u **allowUserPassword** en **sessionTokenOnly** opties in het **serverConf.xml** dossier activeren. Vergeet niet deze twee opties vervolgens te deactiveren. Raadpleeg de sectie [Identified web applications](../../migration/using/general-configurations.md#identified-web-applications) voor meer informatie.

   Afhankelijk van het type van de toepassingen van het Web en hun configuratie, moet u extra manipulaties uitvoeren om ervoor te zorgen zij correct werken.

   Zie de de toepassingssectie van het [Web](../../migration/using/general-configurations.md#web-applications) .

   Bij migratie vanaf een v5.11-platform moeten aanvullende configuraties worden uitgevoerd: voor meer informatie, verwijs naar de de toepassingssectie van het [Web](../../migration/using/specific-configurations-in-v5-11.md#web-applications) .

* Beveiligingszones.

   Voordat u de server start, moet u de beveiligingszones configureren. Raadpleeg [deze sectie](../../installation/using/configuring-campaign-server.md#defining-security-zones) en de sectie [Beveiliging](../../migration/using/general-configurations.md#security) voor meer informatie.

* Schemas

   In de Rode Hoed, kunt u fouten ontmoeten wanneer het uitgeven van bepaalde schema&#39;s. For more on this, refer to the [Red-Hat](../../migration/using/general-configurations.md#red-hat) section.

* Workflows

   Als u migreert vanaf een v5.11-platform, moet u de runtimemap voor workflows beheren. For more on this, refer to the [Workflows](../../migration/using/specific-configurations-in-v5-11.md#workflows) section.

* Tracking

   Als u migreert vanaf een v5.11-platform, moet u de modus Tekstspatiëring configureren. For more on this, refer to the [Tracking](../../migration/using/specific-configurations-in-v5-11.md#tracking) section.

* Startpagina

   Als u migreert vanaf een v6.02-platform, kunt u aanvullende parameters definiëren om uw oude startpagina vanaf v6.02 te houden. Raadpleeg voor meer informatie de [gebruiksvriendelijkheid: Homepage en navigatiegedeelte](../../migration/using/specific-configurations-in-v6-02.md#user-friendliness--home-page-and-navigation) .

* Interaction

   Als u **Interactie** gebruikt, moet u om het even welke parameters na de migratie aanpassen. For more on this, refer to the [Interaction](../../migration/using/general-configurations.md#interaction) section.

