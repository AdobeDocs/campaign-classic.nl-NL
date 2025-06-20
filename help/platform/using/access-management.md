---
product: campaign
title: Aan de slag met machtigingen
description: Leer hoe u toegang kunt verlenen tot campagnecapaciteiten
badge: label="v7" type="Informative" tooltip="Alleen van toepassing op Campaign Classic v7"
feature: Access Management, Permissions
exl-id: 9b616715-33cd-43ba-8548-8d96a179408e
source-git-commit: b27b85b126e002c0ea8b5d71da1ed60e1e817980
workflow-type: tm+mt
source-wordcount: '202'
ht-degree: 8%

---

# Aan de slag met machtigingen{#access-management}


>[!CAUTION]
>
>Beginnend Campaign Classic v7.3.1, zouden alle exploitanten [ Adobe Identity Management Systeem (IMS) ](https://helpx.adobe.com/nl/enterprise/using/identity.html){target="_blank"} moeten gebruiken om met Campagne te verbinden.
>
>Als onderdeel van de inspanningen om het beveiligings- en verificatieproces te versterken, raadt Adobe Campaign ten zeerste aan om alle bestaande verificatiemodus voor operatoren te migreren van de native verificatie van aanmelding/wachtwoord naar Adobe Identity Management System (IMS). Leer hoe te om uw exploitanten in [ te migreren deze pagina ](../../technotes/using/migrate-users-to-ims.md).
> 
>Na deze migratie is de volgende sectie niet meer van toepassing.  Leer hoe te opstellingstoestemmingen met Adobe IMS in [ Campagne v8 documentatie ](https://experienceleague.adobe.com/docs/campaign/campaign-v8/admin/permissions/gs-permissions.html?lang=nl-NL){target="_blank"}.


Met Adobe Campaign kunt u de rechten definiëren en beheren die aan de verschillende operatoren zijn toegewezen. Dit zijn een reeks rechten en beperkingen die autoriseren of weigeren:

* Toegang tot bepaalde functies (via genoemde rechten);
* Toegang tot bepaalde registers,
* Opstellen, wijzigen en/of verwijderen van registers (acties, contacten, campagnes, groepen, enz.).

>[!BEGINTABS]

>[!TAB  documentatie van Toestemmingen ]

Meer over toestemmingen in Adobe Campaign leren, gelieve te verwijzen naar de [ documentatie van de Campagne v8 ](https://experienceleague.adobe.com/nl/docs/campaign/campaign-v8/admin/permissions/gs-permissions?lang=en#_blank){target=_blank}.

[![afbeelding](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/nl/docs/campaign/campaign-v8/admin/permissions/gs-permissions?lang=en#_blank){target=_blank}

>[!TAB  beheert omslagtoegang ]

Meer over de toegang van Omslagen leren en hoe te om hen te beheren, gelieve te verwijzen naar de [ documentatie van de Campagne v8 ](https://experienceleague.adobe.com/nl/docs/campaign/campaign-v8/admin/permissions/folder-permissions?lang=en#_blank){target=_blank}.

[![afbeelding](../../assets/do-not-localize/learn-more-button.svg)] ([![image](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/nl/docs/campaign/campaign-v8/admin/permissions/gs-permissions?lang=en#_blank){target=_blank}){target=_blank}

>[!ENDTABS]

<!--
The permissions apply to operator profiles or operator groups.

They are completed by safety parameters linked to the operator's connection mode to Adobe Campaign. For more about security zones in [this page](../../installation/using/security-zones.md).

There are two types of permissions you can grant to a user:

* You can define groups of operators to which you attribute rights, then associate the operators with one or more groups. This enables you to reuse rights and make operator profiles more consistent. It also facilitates the management and maintenance of profiles. Group creation and management are presented in [this section](access-management-groups.md).

* You can attribute named rights directly to users, in some cases to overload the rights allocated via groups. These rights are presented in [this page](access-management-named-rights.md).

>[!NOTE]
>
> * Before starting defining permissions, Adobe recommends you to read the [Security configuration checklist](https://helpx.adobe.com/nl/campaign/kb/acc-security.html).
> * To learn more about permissions, please refer to the detailed explanation on the [Campaign v8 documentation](https://experienceleague.adobe.com/nl/docs/campaign/campaign-v8/admin/permissions/gs-permissions){target=_blank}.

Learn how to grant access and set up permissions in these sections:

* [Create operators](access-management-operators.md)

* [Define groups](access-management-groups.md)

* [Add Named rights](access-management-named-rights.md)

* [Manage Campaign folder access](access-management-folders.md)

* [Access rights matrix](access-management-named-rights.md#access-rights-matrix)


See also:

* [Manage permissions for workflows](../../workflow/using/managing-rights.md)
* [Manage permissions for distributed marketing](../../distributed/using/about-distributed-marketing.md#operators-and-entities)
* [Manage permissions for the interaction module](../../interaction/using/operator-profiles.md)
* [Filter access to schemas](../../configuration/using/filtering-schemas.md)
* [Restricting PI view](../../configuration/using/restricting-pii-view.md)
-->