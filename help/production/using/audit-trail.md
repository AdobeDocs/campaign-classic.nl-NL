---
solution: Campaign Classic
product: campaign
title: Audittrail
description: Audittrail
audience: production
content-type: reference
topic-tags: production-procedures
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 3%

---


# Audittrail{#audit-trail}

In Adobe Campaign **[!UICONTROL Audit trail]** krijgt u toegang tot de volledige geschiedenis van wijzigingen die in uw exemplaar zijn aangebracht.

**[!UICONTROL Audit trail]** legt in real-time een uitgebreide lijst vast met acties en gebeurtenissen die plaatsvinden in uw Adobe Campaign-instantie. Het omvat een zelfbediende manier om tot een geschiedenis van gegevens toegang te hebben helpen vragen zoals beantwoorden: wat er met uw workflows is gebeurd en wie deze voor het laatst heeft bijgewerkt of wat uw gebruikers in dat geval hebben gedaan.

>[!NOTE]
>
>Adobe Campaign controleert geen wijzigingen die zijn aangebracht in gebruikersrechten, sjablonen, personalisatie of campagnes.\
>Het spoor van de controle kan slechts door beheerders van de instantie worden beheerd.

Audittrail bestaat uit drie onderdelen:

* **Schema audittrail**: Controleer de activiteiten en de laatste wijzigingen die u in uw schema&#39;s hebt aangebracht.

   For more information on schemas, refer to this [page](../../configuration/using/data-schemas.md).

* **Workflowaudittrail**: Controleer activiteiten en laatste wijzigingen die zijn aangebracht aan workflows, en daarnaast de status van uw workflows, zoals:

   * Starten
   * Pauzeren
   * Stoppen
   * Opnieuw starten
   * Opschonen die gelijk is aan de handeling Historie leegmaken
   * Simuleer wat aan de actieBegin op simulatiemodus evenaart
   * Wakeup die gelijk is aan de handeling Voer taken uit die in behandeling zijn.
   * Onvoorwaardelijk stoppen

   For more information on workflows, refer to this [page](../../workflow/using/about-workflows.md).

   Raadpleeg de [desbetreffende sectie](../../workflow/using/monitoring-workflow-execution.md)voor meer informatie over het controleren van workflows.

* **Optie audittrail**: Controleer de activiteiten en de laatste wijzigingen die u hebt aangebracht in uw opties.

   For more information on options, refer to this [page](../../installation/using/configuring-campaign-options.md).

## Audittrail openen {#accessing-audit-trail}

Toegang krijgen tot de **[!UICONTROL Audit trail]** volgende informatie van uw instantie:

1. Open het **[!UICONTROL Explorer]** menu van uw instantie.
1. Selecteer onder het **[!UICONTROL Administration]** menu **[!UICONTROL Audit]** .

   ![](assets/audit_trail_1.png)

1. Het **[!UICONTROL Audit trail]** venster wordt geopend met de lijst met entiteiten. Adobe Campaign controleert het maken, bewerken en verwijderen van acties voor workflows, opties en schema&#39;s.

   Selecteer een van de entiteiten voor meer informatie over de laatste wijzigingen.

   ![](assets/audit_trail_2.png)

1. Het **[!UICONTROL Audit entity]** venster geeft u meer gedetailleerde informatie over de gekozen entiteit, zoals:

   * **[!UICONTROL Type]** : Workflow, opties of schema&#39;s.
   * **[!UICONTROL Entity]** : Interne naam van uw activiteiten.
   * **[!UICONTROL Modified by]** : Gebruikersnaam van de laatste persoon die deze entiteit als laatste heeft gewijzigd.
   * **[!UICONTROL Action]** : De laatste actie die op deze entiteit is uitgevoerd, is gemaakt, bewerkt of verwijderd.
   * **[!UICONTROL Modification date]** : Datum van de laatste actie die op deze entiteit is uitgevoerd.

   Het codeblok geeft u meer informatie over wat precies in uw entiteit is gewijzigd.

   ![](assets/audit_trail_3.png)

>[!NOTE]
>
>De bewaartermijn wordt standaard ingesteld op 180 dagen voor **[!UICONTROL Audit logs]** . Raadpleeg deze [pagina](../../production/using/database-cleanup-workflow.md#deployment-wizard)voor meer informatie over het wijzigen van de retentieperiode.

## Audittrail in-/uitschakelen {#enable-disable-audit-trail}

Het audittrail kan gemakkelijk voor een specifieke activiteit worden geactiveerd of worden gedeactiveerd als, bijvoorbeeld, u wat ruimte op het gegevensbestand wilt bewaren.

Dit doet u als volgt:

1. Open het **[!UICONTROL Explorer]** menu van uw instantie.
1. Selecteer **[!UICONTROL Administration]** vervolgens onder het **[!UICONTROL Platform]** menu **[!UICONTROL Options]** .

   ![](assets/audit_trail_4.png)

1. Selecteer een van de volgende opties, afhankelijk van de entiteit die u wilt activeren/deactiveren:

   * Voor workflow: **[!UICONTROL XtkAudit_Workflows]**
   * Voor schema&#39;s: **[!UICONTROL XtkAudit_DataSchema]**
   * Voor opties: **[!UICONTROL XtkAudit_Option]**
   * Voor elke entiteit: **[!UICONTROL XtkAudit_Enable_All]**

   ![](assets/audit_trail_5.png)

1. Wijzig de waarde **[!UICONTROL Value]** in 1 als u de entiteit wilt inschakelen of in 0 als u deze wilt uitschakelen.

   ![](assets/audit_trail_6.png)

1. Klik op **[!UICONTROL Save]** .

