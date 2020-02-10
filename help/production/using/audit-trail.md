---
title: Audittrail
seo-title: Audittrail
description: Audittrail
seo-description: null
page-status-flag: never-activated
uuid: b96b93b6-e002-4c67-b9ce-b66cdcd395d7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: production-procedures
discoiquuid: aa147a8c-9d93-45c8-bb4a-db714739f4c0
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: e1937c1ddcbde092a22f4fe8c50d3d72b02cfeed

---


# Audittrail{#audit-trail}

In de Campagne van Adobe, **[!UICONTROL Audit trail]** geeft u toegang tot de volledige geschiedenis van veranderingen die binnen uw instantie worden aangebracht.

**[!UICONTROL Audit trail]** legt in real-time een uitgebreide lijst met acties en gebeurtenissen vast die in uw Adobe Campagne-instantie plaatsvinden. Het omvat een zelfbediende manier om tot een geschiedenis van gegevens toegang te hebben helpen vragen zoals beantwoorden: wat er met uw workflows is gebeurd en wie deze voor het laatst heeft bijgewerkt of wat uw gebruikers in dat geval hebben gedaan.

>[!NOTE]
>
>Adobe Campaign controleert geen wijzigingen die zijn aangebracht in gebruikersrechten, sjablonen, personalisatie of campagnes.\
>Het spoor van de controle kan slechts door beheerders van de instantie worden beheerd.

Audittrail bestaat uit drie onderdelen:

* **Schema audittrail**: Controleer de activiteiten en de laatste wijzigingen die u in uw schema&#39;s hebt aangebracht.

   Raadpleeg deze [pagina](../../configuration/using/data-schemas.md)voor meer informatie over schema&#39;s.

* **Workflowaudittrail**: Controleer activiteiten en laatste wijzigingen die zijn aangebracht aan workflows, en daarnaast de status van uw workflows, zoals:

   * Start
   * Pauzeren
   * Stoppen
   * Opnieuw starten
   * Opschonen wat overeenkomt met de handeling Historie leegmaken
   * Simuleer wat aan de actieBegin op simulatiemodus evenaart
   * Wakeup die gelijk is aan de handeling Voer taken uit die in behandeling zijn.
   * Onvoorwaardelijke stop
   Raadpleeg deze [pagina](../../workflow/using/about-workflows.md)voor meer informatie over workflows.

   Raadpleeg de [desbetreffende sectie](../../workflow/using/monitoring-workflow-execution.md)voor meer informatie over het controleren van workflows.

* **Optie audittrail**: Controleer de activiteiten en de laatste wijzigingen die u hebt aangebracht in uw opties.

   Raadpleeg deze [pagina](../../installation/using/configuring-campaign-options.md)voor meer informatie over opties.

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

Daartoe:

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

1. Klik **[!UICONTROL Save]** .

