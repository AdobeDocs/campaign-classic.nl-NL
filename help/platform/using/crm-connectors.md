---
solution: Campaign Classic
product: campaign
title: CRM-connectoren
description: Ga aan de slag met CRM-connectors in Campagne
audience: platform
content-type: reference
topic-tags: connectors
translation-type: tm+mt
source-git-commit: 2838ced5f5d562914c0791e6a0b8f02dd61006b4
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 24%

---


# CRM-connectoren{#crm-connectors}

## Aan de slag met CRM-connectors {#about-crm-connectors}

Adobe Campaign biedt verschillende CRM-connectoren waarmee u uw Adobe Campaign-platform kunt koppelen aan systemen van derden. Deze CRM-connectoren laten u toe om contactpersonen, accounts, aankopen, enzovoort, te synchroniseren. Ze zorgen ervoor dat uw applicatie eenvoudig kan worden geïntegreerd met verschillende externe en zakelijke applicaties.

Deze connectoren maken snelle en eenvoudige data-integratie mogelijk: Adobe Campaign verstrekt een specifieke wizard voor het verzamelen en selecteren van data uit de lijsten die beschikbaar zijn in het CRM-systeem. Dit garandeert tweerichtingssynchronisatie om ervoor te zorgen dat de data altijd up-to-date zijn in alle systemen.

>[!NOTE]
>
>Deze functie is beschikbaar in Adobe Campaign via het speciale pakket **CRM-connectors**.


### Compatibele systemen {#compatible-crm-systems-and-limitations}

Ondersteunde CRM&#39;s en versies worden beschreven in Campagne [Compatibiliteitsmatrix](../../rn/using/compatibility-matrix.md).

>[!NOTE]
>
>De CRM-connectors werken alleen met een beveiligde URL (https).

### Implementatiestappen {#crm-implementation-steps}

Leer geleidelijke procedure om Campagne en de Dynamica van Microsoft [in deze sectie](../../platform/using/crm-ms-dynamics.md) te verbinden

Voer de volgende stappen uit als u CRM-connectors in Adobe Campaign wilt gebruiken:

1. Maak een nieuwe externe account via het knooppunt **[!UICONTROL Administration > Platform > External accounts]** van de Adobe Campaign-structuur.
1. Selecteer het systeem van CRM u Campagne met moet verbinden.
1. Voer instellingen in om de verbinding in te schakelen.
1. Stel de configuratietovenaar in werking om de beschikbare lijst van CRM te produceren: Met de configuratietovenaar kunt u tabellen verzamelen en het bijbehorende schema maken.

   Voorbeeld voor de configuratiewizard **Salesforce**:

   ![](assets/crm_connectors_sfdc_launch.png)

   >[!NOTE]
   >
   >Als u de installatie wilt goedkeuren, moet u zich afmelden en weer terugzetten op de Adobe Campaign-console.

1. Controleer het schema dat in Adobe Campaign in de **[!UICONTROL Administration > Configuration > Data schemas]** knoop wordt geproduceerd.

   Voorbeeld voor schema **Salesforce**:

   ![](assets/crm_connectors_sfdc_table.png)

1. Zodra het schema wordt gecreeerd, kunt u opsommingen automatisch via CRM aan Adobe Campaign synchroniseren.

   Om dit te doen, klik **[!UICONTROL Synchronizing enumerations...]** verbinding en selecteer de opsomming van Adobe Campaign die de opsomming van CRM aanpast.

   >[!NOTE]
   >
   >U kunt alle waarden van een opsomming van Adobe Campaign door die van CRM vervangen: Selecteer **[!UICONTROL Yes]** in de kolom **[!UICONTROL Replace]** om dit te doen.

   Voorbeeld voor **Salesforce** opsommingen:

   ![](assets/crm_connectors_sfdc_enum.png)

   Klik op **[!UICONTROL Next]** en **[!UICONTROL Start]** om de lijst te importeren.

1. Controleer de geïmporteerde waarden in het menu **[!UICONTROL Administration > Platform > Enumerations]**.

   ![](assets/crm_connectors_sfdc_exe.png)

   >[!NOTE]
   >
   > Meerdere selectienumeraties in Salesforce worden niet ondersteund.

1. Om gegevens tussen de gegevens van Adobe Campaign en het systeem van CRM te synchroniseren, moet u een werkschema tot stand brengen en **[!UICONTROL CRM connector]** activiteit gebruiken.

   ![](assets/crm_connectors_sfdc_wf.png)

   Meer informatie over gegevenssynchronisatie [op deze pagina](../../platform/using/crm-data-sync.md).
