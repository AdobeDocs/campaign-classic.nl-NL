---
product: campaign
title: Nieuwste release
description: De nieuwste aanvullende informatie voor Campaign Classic v7
feature: Release Notes
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: 8fec4d038eddaa3c5a2aade1b619f2543453d4de
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 100%

---

# Nieuwste release{#latest-release}

Deze pagina bevat nieuwe mogelijkheden, verbeteringen en oplossingen die worden geleverd met de **nieuwste versie van Campaign Classic v7**. Elke nieuwe build heeft een status die wordt aangegeven door een kleur. Meer informatie over de build-statussen van Campaign Classic v7 vindt u op [deze pagina](rn-overview.md).

## Release 7.3.5 - build 9368 {#release-7-3-5}

[!BADGE Algemene beschikbaarheid]{type=Positive url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=nl#rn-statuses" tooltip="Algemene beschikbaarheid"}


_Woensdag 5 december 2023_


### Beveiligingsverbeteringen {#release-7-3-5-security}


* Met Campaign Classic v7.3.5 is het verificatieproces verbeterd en beveiligd. Technische operatoren moeten nu Adobe Identity Management System (IMS) gebruiken om verbinding te maken met Campaign. Ontdek in [deze technische opmerking](../../technotes/using/ims-migration.md) hoe u uw bestaande technische account(s) kunt migreren.

* Daarnaast raadt Adobe Campaign bij het versterken van het beveiligings- en verificatieproces sterk aan om de modus voor verificatie van eindgebruikers te migreren van de native verificatie van aanmelding/wachtwoord naar Identity Management System (IMS) van Adobe. Ontdek in [deze technische opmerking](../../technotes/using/migrate-users-to-ims.md) hoe u uw operators kunt migreren.

* Als een webformulier de status **Publicatie in behandeling** heeft, wordt het niet automatisch live. Om beveiligingsproblemen te voorkomen, moet het worden gepubliceerd voordat het **Online** wordt en toegankelijk is via de webformulier-URL in een webbrowser. [Meer informatie](../../web/using/publishing-a-web-form.md#life-cycle-of-a-form)

### Patches {#release-7-3-5-patches}

* Probleem verholpen bij het gebruik van gegevens uit een Google Big Query-database en het bijwerken van gegevens in een Oracle-database: alle sleutels in de tijdelijke tabel met workflows zijn ingesteld op `0`. (NEO-65091)
* Probleem verholpen waarbij de uitvoering van een workflow mislukte wanneer twee query&#39;s in een Google Big Query-database werden gecombineerd in een **Samenvoeging**-workflowactiviteit. (NEO-63705)
* Probleem verholpen waarbij de gebruiker werd gevraagd opnieuw te verifiëren wanneer in een Campaign-rapport op de knop `Back` werd geklikt. (NEO-65087)
* Probleem verholpen in de workflow Database opschonen die optrad als een levering werd verwijderd vóór de leveringsbewijzen werden afgeleverd. (NEO-48114)
* Probleem verholpen tijdens verbinden met de clientconsole: recente updates van de TLS-verificatie leidden tot een verbindingsfout. (NEO-50488)
* Probleem verholpen met de HTTP-proxyverificatie na de upgrade van de Campaign naar 7.3.1., waarbij HTTP-verzoeken in Campaign-workflows mislukten met `error 407 – proxy auth required is returned`. (NEO-49624)
* Er is een intermitterende fout opgelost bij GPG-ontsleuteling in workflowactiviteiten van **Script**. Het bijbehorende foutbericht was: `gpg: decryption failed: No secret key`. (NEO-50257)
  <!--* Workflow temporary tables now have a primary index in Teradata with a Federated Data Access (FDA) connection. (NEO-62575)-->

