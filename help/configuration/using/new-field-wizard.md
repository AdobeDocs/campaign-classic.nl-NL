---
product: campaign
title: Nieuwe assistent voor velden
description: Nieuwe assistent voor velden
feature: Schema Extension
role: Developer
exl-id: 2350a531-7a26-4f26-90fe-8dac0cc26605
source-git-commit: 9f5205ced6b8d81639d4d0cb6a76905a753cddac
workflow-type: tm+mt
source-wordcount: '199'
ht-degree: 4%

---

# Nieuwe assistent voor velden{#new-field-wizard}


Met een assistent die toegankelijk is via **[!UICONTROL Tools > Advanced > Add new fields]** kunt u een of meer velden toevoegen aan een tabel in de database.

Valideren van de medewerker werkt het extensieschema van de uit te breiden lijst bij en lanceert het SQL manuscript om de fysieke structuur van het gegevensbestand te wijzigen.

Deze assistent heeft het voordeel om snel een gebied toe te voegen zonder de structuur van een gegevensschema te moeten kennen.

Het belangrijkste nadeel is de beperking van de gegevens en de eigenschappen die moeten worden uitgebreid.

De hulpschermen bevatten de volgende stappen:

1. Op de eerste pagina kunt u de naam invoeren van het schema dat moet worden uitgebreid en de naamruimte van het extensieschema waarin de wijzigingen worden opgeslagen:

   ![](assets/d_ncs_integration_schema_addfield.png)

1. Op de volgende pagina kunt u de eigenschappen invoeren van het veld dat moet worden toegevoegd.

   ![](assets/d_ncs_integration_schema_addfield2.png)

1. Klik op de knop **[!UICONTROL Finish]** om de wijzigingen te bevestigen.

Een uitbreidingsdossier, genoemd &quot;cus :recipient&quot;in ons voorbeeld, wordt automatisch gecreeerd en het overeenkomstige SQL manuscript wordt uitgevoerd:

```
<srcSchema extendedSchema="nms:recipient" label="Recipients" name="recipient"  namespace="cus">  
  <element name="recipient">    
    <attribute belongsTo="cus:recipient" dataPolicy="email" label="Email" length="80" name="email1" sqlname="sEmail1" type="string" user="true"/>  
  </element>
</srcSchema>
```

>[!NOTE]
>
>Door gebrek, worden de toegevoegde gebieden verklaard met het bezit **gebruiker** (met de waarde &quot;waar&quot;). Hiermee kunt u het veld in de invoervorm van het uitgebreide schema weergeven en bewerken met behulp van een &quot;treeEdit&quot;-type besturingselement (zie Invoerformulier).
