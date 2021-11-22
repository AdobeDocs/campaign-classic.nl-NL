---
product: campaign
title: Uw platform configureren
description: Uw platform configureren
audience: migration
content-type: reference
topic-tags: migration-procedure
exl-id: ad71dead-c0ca-42d5-baa8-0f340979231a
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '940'
ht-degree: 1%

---

# Uw platform configureren{#configuring-your-platform}

![](../../assets/v7-only.svg)

Bepaalde belangrijke wijzigingen in Adobe Campaign v7 vereisen een configuratie om ervoor te zorgen dat deze effectief werkt. Deze parameters kunnen nodig zijn voor of na het migreren. De betrokken veranderingen en hun configuratiewijze worden voorgesteld in deze sectie.

Tijdens de migratie **NmsRecipient** tabel wordt opnieuw samengesteld op basis van de schemadefinitie. Eventuele wijzigingen die buiten Adobe Campaign in de SQL-structuur van deze tabel zijn aangebracht, gaan verloren.

Voorbeeldelementen om te controleren:

* Als u een kolom (of een index) hebt toegevoegd aan de **NmsRecipient** tabel maar u hebt deze niet in het schema gedetailleerd, deze wordt niet opgeslagen.
* De **tabelruimte** Het attribuut neemt zijn waarden door gebrek terug, met andere woorden die die in de plaatsingstovenaar worden bepaald.
* Als u een verwijzingsmening aan de lijst NmsRecipient hebt toegevoegd, moet u het schrappen alvorens zich te migreren.

Deze waarschuwing heeft ook betrekking op gebruikers van Oracles: als u de **usetimestamptz:1** optie tijdens een postupgrade (zie [Tijdzones](../../migration/using/general-configurations.md#time-zones)), alle tabellen die ten minste één **date+time** het veld wordt opnieuw opgebouwd.

## Voor de migratie {#before-the-migration}

Bij het migreren naar Adobe Campaign v7 moeten de volgende elementen worden geconfigureerd. Deze elementen moeten worden aangepakt voordat met de **postupgrade**.

* Tijdzones

   Tijdens een migratie vanaf een v5.11-platform moet u opgeven welke tijdzone u tijdens de postupgrade wilt gebruiken.

   Als u de modus &quot;multi timezone&quot; wilt gebruiken, raadpleegt u de [Tijdzones](../../migration/using/general-configurations.md#time-zones) sectie.

   Als u Oracle als gegevensbestand gebruikt, controleer dat de dossiers van de Oracle timezone behoorlijk tussen de toepassingsserver en de gegevensbestandserver zijn gesynchroniseerd. Raadpleeg voor meer informatie de [Oracle](../../migration/using/general-configurations.md#oracle) sectie.

* Beveiligingszones

   Om veiligheidsredenen is het Adobe Campaign-platform niet meer standaard toegankelijk: u moet de veiligheidsstreken vormen, die het verzamelen van de gebruikersIP adressen vóór de migratie vereist.

   Raadpleeg voor meer informatie de [Beveiliging](../../migration/using/general-configurations.md#security) sectie.

* Syntaxis

   Bepaalde syntaxis in JavaScript wordt mogelijk geaccepteerd in versies 5.11 en 6.02 en wordt niet meer geaccepteerd in versie 7, omdat er een nieuwe interpreter wordt gebruikt. Raadpleeg voor meer informatie de [JavaScript](../../migration/using/general-configurations.md#javascript) sectie.

   Op dezelfde manier wordt in Adobe Campaign v7 een nieuwe syntaxis geïntroduceerd die de op SQLData gebaseerde syntaxis vervangt. Als u code-elementen met deze syntaxis gebruikt, moet u deze aanpassen. Raadpleeg voor meer informatie de [SQLData](../../migration/using/general-configurations.md#sqldata) sectie.

* Wachtwoorden

   U moet de **Beheer** en **Intern** wachtwoorden. Raadpleeg voor meer informatie de [Gebruikerswachtwoorden](../../migration/using/before-starting-migration.md#user-passwords) sectie.

* Boomstructuur

   Als u migreert vanaf een v5.11-platform, moet u de structuurmappen opnieuw ordenen volgens de Adobe Campaign v6-normen. Raadpleeg voor meer informatie de [Adobe Campaign v7-boomstructuur](../../migration/using/specific-configurations-in-v5-11.md#campaign-vseven-tree-structure) sectie.

* Interaction

   Als u **Interactie**, moet u alle 6.02 schemaverwijzingen schrappen die niet meer in v7 bestaan. Raadpleeg voor meer informatie de [Interactie](../../migration/using/general-configurations.md#interaction) sectie.

## Na de migratie {#after-the-migration}

Na uitvoering **postupgrade**, moeten de volgende elementen in aanmerking worden genomen en moeten de overeenkomstige configuraties worden uitgevoerd.

* Pagina&#39;s spiegelen

   Het aanpassingsblok van de pagina Mirror is gewijzigd met v6.x. Deze nieuwe versie verbetert de beveiliging bij het openen van deze pagina&#39;s.

   Als u het v5-verpersoonlijkingsblok in uw berichten hebt gebruikt, mislukt de weergave van de spiegelpagina. Adobe adviseert hoogst om het nieuwe verpersoonlijkingsblok te gebruiken wanneer het opnemen van spiegelpagina in uw berichten.

   Nochtans als tijdelijke oplossing (en aangezien de spiegelpagina&#39;s nog leven), kunt u aan het oude verpersoonlijkingsblok terugkeren om dit probleem te vermijden door de optie te veranderen **[!UICONTROL XtkAcceptOldPasswords]** en stel deze in op **[!UICONTROL 1]**. Dit heeft geen invloed op het gebruik van het nieuwe personalisatieblok v6.x.

* Syntaxis

   Als er fouten optreden met betrekking tot de syntaxis, moet u de functie **allowSQLInjection** in de **serverConf.xml** bestand, omdat u dan tijd hebt om de code te herschrijven. Nadat de code is aangepast, moet u de beveiliging opnieuw activeren. Raadpleeg voor meer informatie de [SQLData](../../migration/using/general-configurations.md#sqldata) sectie.

* Conflicten

   De migratie wordt uitgevoerd via een postupgrade en conflicten kunnen optreden in rapporten, formulieren of webtoepassingen. Deze conflicten kunnen vanaf de console worden opgelost.

   Zie de [Conflicten](../../migration/using/general-configurations.md#conflicts) sectie.

* Tomcat

   Als u de installatiemap hebt aangepast, moet u controleren of deze na de migratie correct is bijgewerkt. Raadpleeg voor meer informatie de [Tomcat](../../migration/using/general-configurations.md#tomcat) sectie.

* Rapporten

   Alle out-of-box-rapporten gebruiken momenteel de v6.x-renderingengine. Als u JavaScript-code hebt toegevoegd aan de rapporten, kunnen bepaalde elementen worden gewijzigd.

   Raadpleeg de [Rapporten](../../migration/using/general-configurations.md#reports) sectie.

* Webtoepassingen

   Na postupgrade, als u om het even welke problemen hebt die met uw geïdentificeerde toepassingen van het Web verbinden, moet u activeren **allowUserPassword** en **sessionTokenOnly** opties in het dialoogvenster **serverConf.xml** bestand. Vergeet niet deze twee opties vervolgens te deactiveren. Raadpleeg voor meer informatie de [Geïdentificeerde webtoepassingen](../../migration/using/general-configurations.md#identified-web-applications) sectie.

   Afhankelijk van het type van de toepassingen van het Web en hun configuratie, moet u extra manipulaties uitvoeren om ervoor te zorgen zij correct werken.

   Zie de [Webtoepassingen](../../migration/using/general-configurations.md#web-applications) sectie.

   Bij migratie vanaf een v5.11-platform moeten aanvullende configuraties worden uitgevoerd: voor meer informatie raadpleegt u de [Webtoepassingen](../../migration/using/specific-configurations-in-v5-11.md#web-applications) sectie.

* Beveiligingszones.

   Voordat u de server start, moet u de beveiligingszones configureren. Raadpleeg voor meer informatie [deze sectie](../../installation/using/security-zones.md) en de [Beveiliging](../../migration/using/general-configurations.md#security) sectie.

* Schemas

   In de Rode Hoed, kunt u fouten ontmoeten wanneer het uitgeven van bepaalde schema&#39;s. Raadpleeg voor meer informatie de [Rood-Hoed](../../migration/using/general-configurations.md#red-hat) sectie.

* Workflows

   Als u migreert vanaf een v5.11-platform, moet u de runtimemap voor workflows beheren. Raadpleeg voor meer informatie de [Workflows](../../migration/using/specific-configurations-in-v5-11.md#workflows) sectie.

* Tracking

   Als u migreert vanaf een v5.11-platform, moet u de modus Tekstspatiëring configureren. Raadpleeg voor meer informatie de [Tekstspatiëring](../../migration/using/specific-configurations-in-v5-11.md#tracking) sectie.

* Startpagina

   Als u migreert vanaf een v6.02-platform, kunt u aanvullende parameters definiëren om uw oude startpagina vanaf v6.02 te houden. Raadpleeg voor meer informatie de [Gebruikersvriendelijkheid: Homepage en navigatie](../../migration/using/specific-configurations-in-v6-02.md#user-friendliness--home-page-and-navigation) sectie.

* Interactie

   Als u **Interactie**, moet u parameters aanpassen na de migratie. Raadpleeg voor meer informatie de [Interactie](../../migration/using/general-configurations.md#interaction) sectie.
