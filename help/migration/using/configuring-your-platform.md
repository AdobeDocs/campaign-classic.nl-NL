---
title: Uw platform configureren
seo-title: Uw platform configureren
description: Uw platform configureren
seo-description: null
page-status-flag: never-activated
uuid: e6255e4b-c9c8-4ac9-9ee3-aaa4dc9e5ecf
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: migration-procedure
discoiquuid: 4d2e765b-750b-457f-ad55-8bd6faaa86af
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 40391fbea53757decb48fd937f5e74e8ba6fb207

---


# Uw platform configureren{#configuring-your-platform}

Bepaalde belangrijke wijzigingen in Adobe Campaign v7 vereisen een configuratie om ervoor te zorgen dat deze effectief werkt. Deze parameters kunnen nodig zijn voor of na het migreren. De betrokken veranderingen en hun configuratiewijze worden voorgesteld in deze sectie.

Tijdens migratie, wordt de **lijst NmsRecipient** herbouwd van de schemadefinitie. Eventuele wijzigingen die buiten de Adobe-campagne in de SQL-structuur van deze tabel zijn aangebracht, gaan verloren.

Voorbeeldelementen om te controleren:

* Als u een kolom (of een index) in de **lijst NmsRecipient** hebt toegevoegd maar u hebt niet het in het schema gedetailleerd, zal dit niet worden bewaard.
* Het **tabelruimteattribuut** neemt standaard zijn waarden terug, met andere woorden die in de plaatsingstovenaar worden bepaald.
* Als u een verwijzingsmening aan de lijst NmsRecipient hebt toegevoegd, moet u het schrappen alvorens zich te migreren.

Deze waarschuwing geldt ook voor Oracle-gebruikers: als u de optie **usetimestamptz:1** tijdens een postupgrade hebt toegevoegd (zie [Tijdzones](../../migration/using/general-configurations.md#time-zones)), worden alle tabellen met ten minste één **datum+tijd** -veld opnieuw samengesteld.

## Voor de migratie {#before-the-migration}

Bij het migreren naar Adobe Campaign v7 moeten de volgende elementen zijn geconfigureerd. Deze elementen moeten worden behandeld alvorens met de **postupgrade** te beginnen.

* Tijdzones

   Tijdens een migratie vanaf een v5.11-platform moet u opgeven welke tijdzone u tijdens de postupgrade wilt gebruiken.

   Raadpleeg de sectie [Tijdzones](../../migration/using/general-configurations.md#time-zones) als u de modus Meerdere tijdzones wilt gebruiken.

   Als u Oracle als een database gebruikt, moet u controleren of de Oracle-tijdzonebestanden correct zijn gesynchroniseerd tussen de toepassingsserver en de databaseserver. Raadpleeg de sectie [Oracle](../../migration/using/general-configurations.md#oracle) voor meer informatie.

* Beveiligingszones

   Om veiligheidsredenen is het Adobe Campagne-platform niet meer standaard toegankelijk: u moet de veiligheidsstreken vormen, die het verzamelen van de gebruikersIP adressen vóór de migratie vereist.

   Raadpleeg de sectie [Beveiliging](../../migration/using/general-configurations.md#security) voor meer informatie.

* Syntaxis

   Bepaalde syntaxis in JavaScript wordt mogelijk geaccepteerd in versies 5.11 en 6.02 en wordt niet meer geaccepteerd in versie 7, omdat er een nieuwe interpreter wordt gebruikt. Raadpleeg de sectie [JavaScript](../../migration/using/general-configurations.md#javascript) voor meer informatie.

   Op dezelfde manier wordt een nieuwe syntaxis geïntroduceerd in Adobe Campagne v7 om de op SQLData gebaseerde syntaxis te vervangen. Als u code-elementen met deze syntaxis gebruikt, moet u deze aanpassen. Raadpleeg de sectie [SQLData](../../migration/using/general-configurations.md#sqldata) voor meer informatie.

* Wachtwoorden

   U moet de **wachtwoorden Admin** en **Internal** configureren. Raadpleeg voor meer informatie de sectie [Gebruikerswachtwoorden](../../migration/using/before-starting-migration.md#user-passwords) .

* Boomstructuur

   Als u migreert vanaf een v5.11-platform, moet u de structuurmappen opnieuw ordenen volgens de Adobe Campagne v6-normen. Raadpleeg de structuursectie [Adobe Campagne v7 voor meer informatie](../../migration/using/specific-configurations-in-v5-11.md#campaign-vseven-tree-structure) .

* Interactie

   Als u **Interactie** gebruikt, moet u alle 6.02 schemaverwijzingen schrappen die niet meer in v7 bestaan. Raadpleeg de sectie [Interactie](../../migration/using/general-configurations.md#interaction) voor meer informatie.

## Na de migratie {#after-the-migration}

Na het runnen van **postupgrade**, moeten de volgende elementen in aanmerking worden genomen en de overeenkomstige configuraties uitgevoerd.

* Pagina&#39;s spiegelen

   Het aanpassingsblok van de pagina Mirror is gewijzigd met v6.x. Deze nieuwe versie verbetert de beveiliging bij het openen van deze pagina&#39;s.

   Als u het v5-verpersoonlijkingsblok in uw berichten hebt gebruikt, mislukt de weergave van de spiegelpagina. Adobe raadt u ten zeerste aan het nieuwe aanpassingsblok te gebruiken wanneer u een spiegel in uw berichten invoegt.

   Nochtans, als tijdelijke oplossing (en aangezien de spiegelpagina&#39;s nog leven), kunt u aan het oude verpersoonlijkingsblok terugkeren om dit probleem te vermijden door de optie te veranderen **[!UICONTROL XtkAcceptOldPasswords]** en het te plaatsen aan **[!UICONTROL 1]**. Dit heeft geen invloed op het gebruik van het nieuwe personalisatieblok v6.x.

* Syntaxis

   Als er fouten optreden die te maken hebben met de syntaxis, moet u tijdens de postupgrade de optie **allowSQLInjection** tijdelijk activeren in het bestand **serverConf.xml** , omdat u dan tijd hebt om de code te herschrijven. Nadat de code is aangepast, moet u de beveiliging opnieuw activeren. Raadpleeg de sectie [SQLData](../../migration/using/general-configurations.md#sqldata) voor meer informatie hierover.

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

   In de Rode Hoed, kunt u fouten ontmoeten wanneer het uitgeven van bepaalde schema&#39;s. Raadpleeg voor meer informatie de sectie [Red-Hat](../../migration/using/general-configurations.md#red-hat) .

* Workflows

   Als u migreert vanaf een v5.11-platform, moet u de runtimemap voor workflows beheren. Raadpleeg de sectie [Workflows](../../migration/using/specific-configurations-in-v5-11.md#workflows) voor meer informatie.

* Tekstspatiëring

   Als u migreert vanaf een v5.11-platform, moet u de modus Tekstspatiëring configureren. Raadpleeg de sectie [Tekstspatiëring](../../migration/using/specific-configurations-in-v5-11.md#tracking) voor meer informatie.

* Homepage

   Als u migreert vanaf een v6.02-platform, kunt u aanvullende parameters definiëren om uw oude startpagina vanaf v6.02 te houden. Raadpleeg voor meer informatie de [gebruiksvriendelijkheid: Homepage en navigatiegedeelte](../../migration/using/specific-configurations-in-v6-02.md#user-friendliness--home-page-and-navigation) .

* Interactie

   Als u **Interactie** gebruikt, moet u om het even welke parameters na de migratie aanpassen. Raadpleeg de sectie [Interactie](../../migration/using/general-configurations.md#interaction) voor meer informatie.

