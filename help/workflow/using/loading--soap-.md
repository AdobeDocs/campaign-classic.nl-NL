---
solution: Campaign Classic
product: campaign
title: Laden (SOAP)
description: Laden (SOAP)
audience: workflow
content-type: reference
topic-tags: action-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 4%

---


# Laden (SOAP){#loading-soap}

>[!CAUTION]
>
>De activiteit van de **Lading (ZEEP)** is slechts beschikbaar als u de **FDA (Federated Data Access)** module geïnstalleerd hebt. Controleer hiervoor uw licentieovereenkomst.

De **activiteit van de Lading (ZEEP)** wordt gebruikt naast de activiteit van het laden van **gegevens (RDBMS)** wanneer het niet mogelijk is om gegevens direct via FDA in een externe gegevensbestand te verzamelen.

De bewerking is als volgt:

1. Selecteer tussen het gebruiken van een voorbeeld van XML of een WSDL.

   Het volgende voorbeeld komt uit een technisch werkschema van de module van het Centrum van het Bericht.

   ![](assets/load_soap_002.png)

1. Selecteer een voorbeeldbestand voor een XML-voorbeeld. Het bestand wordt geanalyseerd om een voorbeeld van een resultaat te maken.

   Voer voor een WSDL de overeenkomende toegangs-URL in en genereren vervolgens de skeletcode. De dienst en de geselecteerde vraag worden automatisch bijgewerkt en getoond.

   ![](assets/soap_load_003.png)

1. Selecteer deze optie **[!UICONTROL Click here to view and edit analysis results]** om elke opgegeven kolom op te geven.

   ![](assets/soap_load_001.png)

   Selecteer **[!UICONTROL Re-analyze the example]**.

   U kunt de indeling van kolomgegevens ook aanpassen via de **[!UICONTROL Advanced parameters]** koppeling. Raadpleeg deze [sectie](../../platform/using/importing-data.md#import-wizard)voor meer informatie over het opmaken van geïmporteerde gegevens.

1. U kunt het lijnaantal als herkenningsteken gebruiken en/of specificeren dat de vraag van de ZEEP verscheidene elementen terugkeert.
1. Voer de volgende tabscripts in op basis van hun functie:

   * **[!UICONTROL Initialization]**: stelt een verbinding van de ZEEP in.
   * **[!UICONTROL Iteration]**: voert de vraag aan de dienst van de ZEEP uit. De return voor deze functie moet een XML-object zijn dat compatibel is met de beschrijving van het voorbeeld of de WSDL.

      De code van dit tabblad wordt aangeroepen in een lus door Adobe Campaign totdat een null XML-object wordt geretourneerd.

   * **[!UICONTROL Finalization]**: sluit verbinding en/of bevrijdt andere middelen die tijdens verwerking worden gecreeerd.

