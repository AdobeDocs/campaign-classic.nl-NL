---
product: campaign
title: Aan de slag met machtigingen
description: Leer hoe u toegang kunt verlenen tot campagnecapaciteiten
badge: label="v7" type="Informative" tooltip="Alleen van toepassing op Campaign Classic v7"
feature: Access Management, Permissions
exl-id: 9b616715-33cd-43ba-8548-8d96a179408e
source-git-commit: e1a085384fb27ec165c487c112fbc70fe9738d9e
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 4%

---

# Aan de slag met machtigingen{#access-management}


>[!CAUTION]
>
>Vanaf Campaign Classic v7.3.1 moeten alle operatoren [Adobe Identity Management System (IMS)](https://helpx.adobe.com/enterprise/using/identity.html){target="_blank"} om verbinding te maken met Campagne.
>
>Als onderdeel van de inspanningen om het beveiligings- en verificatieproces te versterken, raadt Adobe Campaign ten zeerste aan om alle bestaande verificatiemodus voor operatoren te migreren van de native verificatie van aanmelding/wachtwoord naar Adobe Identity Management System (IMS). Leer hoe u uw operatoren kunt migreren in [deze pagina](../../technotes/using/migrate-users-to-ims.md).
> 
>Na deze migratie is de volgende sectie niet meer van toepassing.  Meer informatie over het instellen van machtigingen met Adobe IMS in [Campagne v8-documentatie](https://experienceleague.adobe.com/docs/campaign/campaign-v8/admin/permissions/gs-permissions.html){target="_blank"}.


Met Adobe Campaign kunt u de rechten definiëren en beheren die aan de verschillende operatoren zijn toegewezen. Dit zijn een reeks rechten en beperkingen die autoriseren of weigeren:

* Toegang tot bepaalde functies (via genoemde rechten);
* Toegang tot bepaalde registers,
* Opstellen, wijzigen en/of verwijderen van registers (acties, contacten, campagnes, groepen, enz.).

De machtigingen gelden voor operatorprofielen of groepen operatoren.

Zij worden aangevuld met veiligheidsparameters die gekoppeld zijn aan de verbindingsmodus van de exploitant met Adobe Campaign. Voor meer informatie over beveiligingszones in [deze pagina](../../installation/using/security-zones.md).

Er zijn twee soorten toestemmingen u aan een gebruiker kunt verlenen:

* U kunt groepen operatoren definiëren waaraan u rechten toewijst en de operatoren vervolgens koppelen aan een of meer groepen. Op deze manier kunt u rechten opnieuw gebruiken en de consistentie van operatorprofielen verhogen. Het vergemakkelijkt ook het beheer en het onderhoud van profielen. Het creëren en beheren van groepen worden voorgesteld in [deze sectie](access-management-groups.md).

* U kunt benoemde rechten rechtstreeks toewijzen aan gebruikers, in sommige gevallen om de rechten die via groepen zijn toegewezen, te overladen. Deze rechten worden weergegeven in [deze pagina](access-management-named-rights.md).

>[!NOTE]
>
>Voordat u begint met het definiëren van machtigingen, raadt de Adobe u aan de [Controlelijst voor beveiligingsconfiguratie](https://helpx.adobe.com/nl/campaign/kb/acc-security.html).

Leer hoe te om toegang en opstellingstoestemmingen in deze secties te verlenen:

* [Operatoren maken](access-management-operators.md)

* [Groepen definiëren](access-management-groups.md)

* [Benoemde rechten toevoegen](access-management-named-rights.md)

* [Toegang tot de map Campagne beheren](access-management-folders.md)

* [Matrix toegangsrechten](access-management-named-rights.md#access-rights-matrix)


Zie ook:

* [Machtigingen voor workflows beheren](../../workflow/using/managing-rights.md)
* [Rechten voor gedistribueerde marketing beheren](../../distributed/using/about-distributed-marketing.md#operators-and-entities)
* [Rechten voor de interactiemodule beheren](../../interaction/using/operator-profiles.md)
* [Toegang tot schema&#39;s filteren](../../configuration/using/filtering-schemas.md)
* [Weergave PI beperken](../../configuration/using/restricting-pii-view.md)
