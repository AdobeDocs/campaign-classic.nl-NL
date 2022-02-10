---
product: campaign
title: Audit trail
description: Leer hoe u uw exemplaar kunt controleren met het Campagne Audit Trail
feature: Audit Trail, Monitoring
exl-id: 8508d879-fb38-4b1f-9f55-0341bb8d0c67
source-git-commit: c54102b2ec32fbea89ce41dd3c9fedb98e612996
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 3%

---

# Audittrail{#audit-trail}

![](../../assets/v7-only.svg)

In Adobe Campaign **[!UICONTROL Audit trail]** geeft u toegang tot de volledige geschiedenis van veranderingen die binnen uw instantie worden aangebracht.

**[!UICONTROL Audit trail]** legt in real-time een uitgebreide lijst vast met acties en gebeurtenissen die plaatsvinden in uw Adobe Campaign-instantie. Het omvat een zelfbediende manier om tot een geschiedenis van gegevens toegang te hebben helpen vragen zoals beantwoorden: wat er met uw workflows is gebeurd en wie deze voor het laatst heeft bijgewerkt of wat uw gebruikers in dat geval hebben gedaan.

>[!NOTE]
>
>Adobe Campaign controleert geen wijzigingen die zijn aangebracht in gebruikersrechten, sjablonen, personalisatie of campagnes.\
>Het spoor van de controle kan slechts door beheerders van de instantie worden beheerd.

Audittrail bestaat uit drie onderdelen:

* **Schema audit trail**: Controleer de activiteiten en de laatste wijzigingen die u in uw schema&#39;s hebt aangebracht.

   Voor meer informatie over schema&#39;s, verwijs naar dit [page](../../configuration/using/data-schemas.md).

* **Workflowaudittrail**: Controleer activiteiten en laatste wijzigingen die zijn aangebracht aan workflows, en daarnaast de status van uw workflows, zoals:

   * Starten
   * Pauzeren
   * Stoppen
   * Opnieuw starten
   * Opschonen die gelijk is aan de handeling Historie leegmaken
   * Simuleer wat aan de actieBegin op simulatiemodus evenaart
   * Wakeup die gelijk is aan de handeling Voer taken uit die in behandeling zijn.
   * Onvoorwaardelijk stoppen

   Raadpleeg deze voor meer informatie over workflows [page](../../workflow/using/about-workflows.md).

   Raadpleeg voor meer informatie over het controleren van workflows de [speciale sectie](../../workflow/using/monitoring-workflow-execution.md).

* **Optie audittrail**: Controleer de activiteiten en de laatste wijzigingen die u hebt aangebracht in uw opties.

   Raadpleeg deze voor meer informatie over opties [page](../../installation/using/configuring-campaign-options.md).

## Audittrail openen {#accessing-audit-trail}

Toegang krijgen tot de **[!UICONTROL Audit trail]** :

1. Toegang krijgen tot **[!UICONTROL Explorer]** van uw instantie.
1. Onder de **[!UICONTROL Administration]** menu, selecteert u **[!UICONTROL Audit]** .

   ![](assets/audit_trail_1.png)

1. De **[!UICONTROL Audit trail]** wordt geopend met de lijst van uw entiteiten. Adobe Campaign controleert het maken, bewerken en verwijderen van acties voor workflows, opties en schema&#39;s.

   Selecteer een van de entiteiten voor meer informatie over de laatste wijzigingen.

   ![](assets/audit_trail_2.png)

1. De **[!UICONTROL Audit entity]** het venster geeft u meer gedetailleerde informatie over de gekozen entiteit zoals:

   * **[!UICONTROL Type]** : Workflow, opties of schema&#39;s.
   * **[!UICONTROL Entity]** : Interne naam van uw activiteiten.
   * **[!UICONTROL Modified by]** : Gebruikersnaam van de laatste persoon die deze entiteit als laatste heeft gewijzigd.
   * **[!UICONTROL Action]** : De laatste actie die op deze entiteit is uitgevoerd, is gemaakt, bewerkt of verwijderd.
   * **[!UICONTROL Modification date]** : Datum van de laatste actie die op deze entiteit is uitgevoerd.

   Het codeblok geeft u meer informatie over wat precies in uw entiteit is gewijzigd.

   ![](assets/audit_trail_3.png)

>[!NOTE]
>
>De bewaarperiode is standaard ingesteld op 180 dagen voor **[!UICONTROL Audit logs]** . Raadpleeg de volgende secties voor meer informatie over het wijzigen van de retentieperiode [page](../../production/using/database-cleanup-workflow.md#deployment-wizard).

## Audittrail in-/uitschakelen {#enable-disable-audit-trail}

Het audittrail kan gemakkelijk voor een specifieke activiteit worden geactiveerd of worden gedeactiveerd als, bijvoorbeeld, u wat ruimte op het gegevensbestand wilt bewaren.

Dit doet u als volgt:

1. Toegang krijgen tot **[!UICONTROL Explorer]** van uw instantie.
1. Onder de **[!UICONTROL Administration]** menu, selecteert u **[!UICONTROL Platform]** dan **[!UICONTROL Options]** .

   ![](assets/audit_trail_4.png)

1. Selecteer een van de volgende opties, afhankelijk van de entiteit die u wilt activeren/deactiveren:

   * Voor workflow: **[!UICONTROL XtkAudit_Workflows]**
   * Voor schema&#39;s: **[!UICONTROL XtkAudit_DataSchema]**
   * Voor opties: **[!UICONTROL XtkAudit_Option]**
   * Voor elke entiteit: **[!UICONTROL XtkAudit_Enable_All]**

   ![](assets/audit_trail_5.png)

1. Wijzig de **[!UICONTROL Value]** tot 1 als u de entiteit wilt toelaten of aan 0 als u het wilt onbruikbaar maken.

   ![](assets/audit_trail_6.png)

1. Klik op **[!UICONTROL Save]** .
