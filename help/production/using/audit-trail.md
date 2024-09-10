---
product: campaign
title: Audit trail
description: Leer hoe u uw exemplaar kunt controleren met het Campagne Audit Trail
feature: Audit Trail, Monitoring, Workflows
exl-id: 8508d879-fb38-4b1f-9f55-0341bb8d0c67
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '464'
ht-degree: 2%

---

# Audit trail{#audit-trail}



In Adobe Campaign biedt de **[!UICONTROL Audit trail]** u toegang tot de volledige geschiedenis van wijzigingen die in uw instantie zijn aangebracht.

**[!UICONTROL Audit trail]** legt in real-time een uitgebreide lijst met acties en gebeurtenissen vast die in uw Adobe Campaign-instantie plaatsvinden. Het omvat een zelf-servermanier om tot een geschiedenis van gegevens toegang te hebben helpen vragen zoals beantwoorden: wat met uw werkschema&#39;s gebeurde, en wie hen het laatst bijwerkte of wat uw gebruikers in de instantie deden.

>[!NOTE]
>
>Adobe Campaign controleert geen wijzigingen die zijn aangebracht in gebruikersrechten, sjablonen, personalisatie of campagnes.\
>Het spoor van de controle kan slechts door beheerders van de instantie worden beheerd.

Audittrail bestaat uit drie onderdelen:

* **de auditspoor van het Schema**: Controleer de activiteiten en de laatste wijzigingen die aan uw schema&#39;s worden gedaan.

  Voor meer informatie over schema&#39;s, verwijs naar deze [ pagina ](../../configuration/using/data-schemas.md).

* **het auditspoor van het Werkschema**: De activiteiten van de controle en laatste wijzigingen die aan werkschema&#39;s worden gedaan, en daarnaast, de staat van uw werkschema&#39;s zoals:

   * Starten
   * Pauzeren
   * Stoppen
   * Opnieuw starten
   * Opschonen wat overeenkomt met de handeling Historie leegmaken
   * Simuleer wat aan de actieBegin op simulatiemodus evenaart
   * Wakeup die gelijk is aan de handeling Voer taken uit die in behandeling zijn.
   * Onvoorwaardelijk stoppen

  Voor meer informatie over werkschema&#39;s, verwijs naar deze [ pagina ](../../workflow/using/about-workflows.md).

  Voor meer op hoe te om werkschema&#39;s te controleren, verwijs naar de [ specifieke sectie ](../../workflow/using/monitoring-workflow-execution.md).

* **de controlespoor van de Optie**: Controleer de activiteiten en de laatste wijzigingen die aan uw opties worden gedaan.

  Voor meer informatie over opties, verwijs naar deze [ pagina ](../../installation/using/configuring-campaign-options.md).

## Audittrail openen {#accessing-audit-trail}

Ga als volgt te werk om de instantie **[!UICONTROL Audit trail]** te openen:

1. Open het menu **[!UICONTROL Explorer]** van uw instantie.
1. Selecteer **[!UICONTROL Audit]** onder het menu **[!UICONTROL Administration]** .

   ![](assets/audit_trail_1.png)

1. Het venster **[!UICONTROL Audit trail]** wordt geopend met de lijst met entiteiten. Adobe Campaign controleert het maken, bewerken en verwijderen van acties voor workflows, opties en schema&#39;s.

   Selecteer een van de entiteiten voor meer informatie over de laatste wijzigingen.

   ![](assets/audit_trail_2.png)

1. In het venster **[!UICONTROL Audit entity]** vindt u gedetailleerdere informatie over de gekozen entiteit, zoals:

   * **[!UICONTROL Type]** : workflow, opties of schema&#39;s.
   * **[!UICONTROL Entity]** : interne naam van uw activiteiten.
   * **[!UICONTROL Modified by]** : gebruikersnaam van de laatste persoon die deze entiteit als laatste heeft gewijzigd.
   * **[!UICONTROL Action]** : De laatste actie die op deze entiteit is uitgevoerd, is gemaakt, bewerkt of verwijderd.
   * **[!UICONTROL Modification date]** : Datum van de laatste actie die op deze entiteit is uitgevoerd.

   Het codeblok geeft u meer informatie over wat precies in uw entiteit is gewijzigd.

   ![](assets/audit_trail_3.png)

>[!NOTE]
>
>De retentieperiode is standaard ingesteld op 180 dagen voor **[!UICONTROL Audit logs]** . Meer leren op hoe te om de behoudperiode te veranderen, verwijs naar deze [ pagina ](../../production/using/database-cleanup-workflow.md#deployment-assistant).

## Audittrail in-/uitschakelen {#enable-disable-audit-trail}

Het audittrail kan gemakkelijk voor een specifieke activiteit worden geactiveerd of worden gedeactiveerd als, bijvoorbeeld, u wat ruimte op het gegevensbestand wilt bewaren.

Dit doet u als volgt:

1. Open het menu **[!UICONTROL Explorer]** van uw instantie.
1. Selecteer **[!UICONTROL Platform]** then **[!UICONTROL Options]** onder het menu **[!UICONTROL Administration]** .

   ![](assets/audit_trail_4.png)

1. Selecteer een van de volgende opties, afhankelijk van de entiteit die u wilt activeren/deactiveren:

   * Voor workflow: **[!UICONTROL XtkAudit_Workflows]**
   * Voor schema&#39;s: **[!UICONTROL XtkAudit_DataSchema]**
   * Voor opties: **[!UICONTROL XtkAudit_Option]**
   * Voor elke entiteit: **[!UICONTROL XtkAudit_Enable_All]**

   ![](assets/audit_trail_5.png)

1. Wijzig **[!UICONTROL Value]** in 1 als u de entiteit wilt inschakelen of in 0 als u deze wilt uitschakelen.

   ![](assets/audit_trail_6.png)

1. Klik op **[!UICONTROL Save]** .
