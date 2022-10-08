---
product: campaign
title: Automatisch proces voor privacyverzoeken
description: Meer informatie over instellen van een automatisch proces voor privacyverzoeken
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: a93bac61-f615-4178-bc12-0f056e48687d
source-git-commit: 42b420d7dae7d38e9f4df442146d3b484c25e831
workflow-type: tm+mt
source-wordcount: '652'
ht-degree: 100%

---

# Automatisch proces voor privacyverzoeken {#automatic-privacy-request-api}

![](../../assets/v7-only.svg)

Adobe Campaign biedt een **API** waarmee u een automatisch proces voor verzoeken om toegang tot persoonsgegevens kunt instellen.

Het algemene privacyproces met de API is hetzelfde als [met de interface](privacy-requests-ui.md). Het enige verschil is de manier waarop het verzoek om toegang tot persoonsgegevens wordt gemaakt. In plaats van het verzoek in Adobe Campaign te maken, wordt een POST met de gegevens van het verzoek naar Campaign verzonden. Voor elk verzoek wordt een nieuwe vermelding toegevoegd in het scherm **[!UICONTROL Privacy Requests]**. De technische workflows voor privacy verwerken dan het verzoek. Dit gebeurt op dezelfde manier als voor een verzoek dat via de interface wordt toegevoegd.

Als u de API gebruikt om de privacyverzoeken in te dienen, raden wij u aan het **tweestapsproces** te activeren voor de eerste verwijderingsverzoeken. Zo kunnen de geretourneerde gegevens worden getest. Na afloop van de tests kunt u het tweestapsproces deactiveren zodat het proces voor verwijderingsverzoeken automatisch kan worden uitgevoerd.

De **[!UICONTROL CreateRequestByName]** JS-API wordt als volgt gedefinieerd.

>[!NOTE]
>
>Als u de **gdprRequest**-API gebruikte, kunt u deze nog steeds gebruiken, maar we raden u aan de nieuwe **privacyRequest**-API te gebruiken.

>[!IMPORTANT]
>
>Het opgegeven recht **[!UICONTROL Privacy Data Right]** is vereist om de API te gebruiken.

```
<method library="nms:gdpr.js" name="CreateRequestByName" static="true">
 <help>Create a new GDPR Request using namespace internal name</help>
 <parameters>
  <param name="namespaceName" type="string" desc="Namespace internal name"/>
  <param name="reconciliationValue" type="string" desc="Reconciliation value"/>
  <param name="type" type="long" desc="Reconciliation value"/>
  <param name="confirmDeletePending" type="boolean" desc="Request confirm before deleting data"/>
  <param name="regulation" type="long" desc="regulation of newly created request"/>
  <param name="id" type="long" inout="out" desc="ID of newly created request"/>
 </parameters>
</method>
```

>[!NOTE]
>
>Het veld &#39;regulation&#39; is alleen beschikbaar als u Campaign Classic 20.2 (build 9178+) gebruikt.
>
>Als u naar 20.2 migreert en de API voorheen al gebruikte, moet u het veld ‘regulation’ toevoegen, zoals hierboven is aangegeven. Als u een oudere build gebruikt, kunt u de API zonder het veld ‘regulation’ blijven gebruiken.

## De API extern aanroepen {#invoking-api-externally}

Hier ziet u een voorbeeld van hoe u de API extern kunt aanroepen, in het bijzonder de verificatie via de API en informatie over de Privacy-API. Raadpleeg de [API-documentatie](https://experienceleague.adobe.com/developer/campaign-api/api/s-nms-privacyRequest.html?lang=nl) voor meer informatie over de Privacy-API. U kunt ook de [documentatie voor webserviceaanroepen](../../configuration/using/web-service-calls.md) raadplegen.

Allereerst moet u de verificatie uitvoeren via de API:

1. Download de **xtk:session**-WSDL via deze URL: **`<server url>`/nl/jsp/schemawsdl.jsp?schema=xtk:session**.

1. Gebruik de methode &#39;Logon&#39; en voer een gebruikersnaam en wachtwoord in als parameters voor het verzoek. U krijgt een antwoord met een sessietoken. Hier volgt een voorbeeld van het gebruik van SoapUI.

   ![](assets/do-not-localize/privacy-api.png)

1. Gebruik de geretourneerde sessietoken als verificatie voor alle verdere API-aanroepen. Deze vervalt na 24 uur.

Roep vervolgens de Privacy-API aan:

1. Download de WSDL via deze URL: **`<server url>`/nl/jsp/schemawsdl.jsp?schema=nms:privacyRequest**.

1. Gebruik **[!UICONTROL CreateRequestByName]** om een specifiek verzoek voor toegang tot persoonsgegevens te maken.

   Hier volgt een voorbeeld met de **[!UICONTROL CreateRequestByName]**. Bekijk hoe we de hierboven gegenereerde sessietoken gebruiken als verificatie. Het antwoord is de id van het gemaakte verzoek.

   ![](assets/do-not-localize/privacy-api-2.png)

   Houd rekening met het volgende als u bovenstaande stappen uitvoert:

   * U kunt een **queryDef** op het **nms:gdprRequest**-schema gebruiken om de status van het toegangsverzoek te controleren.
   * U kunt een **queryDef** op het **nms:gdprRequestData**-schema gebruiken om het resultaat van het toegangsverzoek te krijgen.
   * Om het XML-bestand van **&quot;$(serverUrl)&#39;/nms/gdpr.jssp?id=&#39;@id&quot;** te kunnen downloaden moet u zijn aangemeld en het bestand openen vanaf een IP-adres dat is toegevoegd aan de lijst met gewenste personen. U kunt dit doen door een webapplicatie te maken waarmee u toegang krijgt tot het bestand dat door de JSSP wordt gegenereerd.

## De API aanroepen vanuit een JS {#invoking-api-from-js}

Hier is een voorbeeld van hoe u de API vanuit een JS binnen Campaign Classic kunt aanroepen.

>[!NOTE]
>
>Het veld &#39;regulation&#39; is alleen beschikbaar als u Campaign Classic 20.2 (build 9178+) gebruikt.
>
>Als u naar 20.2 migreert en de API voorheen al gebruikte, moet u het veld ‘regulation’ toevoegen. Als u een oudere build gebruikt, kunt u de API zonder het veld ‘regulation’ blijven gebruiken.

* Als u **een oudere build gebruikt (met AVG-pakket)**, kunt u de API blijven gebruiken zonder het veld ‘regulation’, zoals hieronder wordt getoond:

   ```
   loadLibrary("nms:gdpr.js");
   /**************************** 
   This code calls an API to create new Privacy request on the DB.
   It requires 4 parameters below.
   Feel free to change parameter values.
   ****************************/
   // 1. Namespace internal name
   var namespaceName = "defaultNamespace1";
   // 2. Reconciliation value for privacy request
   var reconciliationValue = "example@adobe.com";
   // 3. Privacy request type
   // GDPR_REQUEST_TYPE_ACCESS = 1;
   // GDPR_REQUEST_TYPE_DELETE = 2;
   var requestType = GDPR_REQUEST_TYPE_ACCESS;
   // 4. Confirm deleting data required.
   // value : true or false
   var ConfirmDeletePending = true;
   // BEGIN
   var requestId = nms.privacyRequest.CreateRequestByName(namespaceName, reconciliationValue, requestType, ConfirmDeletePending);
   // User can use a simple queryDef with requestID as a parameter to check request status.
   ```

* Als u **migreert naar 20.2** en als u de API al gebruikte, moet u het veld ‘regulation’ toevoegen zoals hieronder wordt weergegeven:

   ```
   loadLibrary("nms:gdpr.js");
   /**************************** 
   This code calls an API to create new Privacy request on the DB.
   It requires 5 parameters below.
   Feel free to change parameter values.
   ****************************/
   // 1. Namespace internal name
   var namespaceName = "defaultNamespace1";
   // 2. Reconciliation value for privacy request
   var reconciliationValue = "example@adobe.com";
   // 3. Privacy request type
   // PRIVACY_REQUEST_TYPE_ACCESS = 1;
   // PRIVACY_REQUEST_TYPE_DELETE = 2;
   var requestType = PRIVACY_REQUEST_TYPE_ACCESS;
   // 4. Confirm deleting data required.
   // value : true or false
   var ConfirmDeletePending = true;
   // 5. Specify which regulation applies to newly created request. This is mandatory parameter.
   // GDPR = 1
   // CCPA = 2
   // PDPA = 3
   // LGPD = 4
   var regulation = 1;
   // BEGIN
   var requestId = nms.privacyRequest.CreateRequestByName(namespaceName, reconciliationValue, requestType, ConfirmDeletePending, regulation);
   // User can use a simple queryDef with requestID as a parameter to check request status.
   ```

* Als u **Campaign Classic 20.2 (build 9178+) of hoger gebruikt**, is het veld &#39;regulation&#39; optioneel, zoals hieronder wordt getoond:

   ```
   loadLibrary("nms:gdpr.js");
   /**************************** 
   This code calls an API to create new Privacy request on the DB.
   It requires 5 parameters below.
   Feel free to change parameter values 
   ****************************/
   // 1. Namespace internal name
   var namespaceName = "defaultNamespace1";
   // 2. Reconciliation value for privacy request
   var reconciliationValue = "example@adobe.com";
   // 3. Privacy request type
   // PRIVACY_REQUEST_TYPE_ACCESS = 1;
   // PRIVACY_REQUEST_TYPE_DELETE = 2;
   var requestType = PRIVACY_REQUEST_TYPE_ACCESS;
   // 4. Confirm deleting data required.
   // value : true or false
   var ConfirmDeletePending = true;
   // 5. Specify which regulation applies to newly created request. This is optional parameter.
   // GDPR = 1
   // CCPA = 2
   // PDPA = 3
   // LGPD = 4
   var regulation = 1;
   // BEGIN
   var requestId = nms.privacyRequest.CreateRequestByName(namespaceName, reconciliationValue, requestType, ConfirmDeletePending, regulation);
   // User can use a simple queryDef with requestID as a parameter to check request status.
   ```
