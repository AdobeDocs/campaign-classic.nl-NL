---
product: campaign
title: Architectuur van transactionele berichten
description: In deze sectie worden de Adobe Campaign Classic-structuur voor transactiemeldingen en de beschikbare kanalen voor het leveren van transactiemeldingen beschreven
feature: Transactional Messaging, Message Center, Architecture
exl-id: 0a059397-b037-405b-b9c1-94a4a072674d
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '1103'
ht-degree: 1%

---

# Architectuur van transactionele berichten {#transactional-messaging-architecture}



Transactioneel overseinen baseert zich op een specifieke architectuur, die uit verscheidene gevallen bestaat:

* A **controleinstantie**, waarop de berichtmalplaatjes worden gecreeerd.

* Één of meerdere **uitvoeringsinstanties**, die gebeurtenissen ontvangen en berichten leveren.

![](assets/messagecenter_diagram.png)

| Control-instantie | Uitvoeringsinstantie |
|--- |--- |
| Adobe Campaign-gebruikers melden zich aan bij de besturingsinstantie om: <ul><li>Transactieberichtsjablonen maken</li><li>De voorvertoning van een bericht genereren met behulp van een zaadlijst</li><li>Rapporten weergeven</li><li>De uitvoeringsinstanties controleren</li></ul> | Uitvoeringsinstanties zijn hier: <ul><li>Gebeurtenissen ontvangen</li><li>Koppel ze aan transactiemalplaatjes</li><li>Verzend een gepersonaliseerd bericht naar elke ontvanger</li></ul> |

## Instanties installeren {#installing-instances}

Er zijn verscheidene voorzorgsmaatregelen om te nemen wanneer het installeren van de Transactieberichtpakketten. Adobe raadt u aan in een testomgeving te werken voordat u in productie gaat nemen. U hebt ook een compatibele Adobe Campaign-licentie nodig. Neem voor meer informatie contact op met het accountmanager van de Adobe.

>[!IMPORTANT]
>
>De bedieningsinstantie en de uitvoeringsinstantie(s) moeten op verschillende computers zijn geïnstalleerd. Ze kunnen niet dezelfde Campagne-instantie delen.

Als u meerdere kanalen moet gebruiken, moet u gerelateerde pakketten installeren en configureren voordat u Transactieberichtpakketten installeert. Voor meer op dit, zie [ een leveringskanaal ](#adding-a-delivery-channel) toevoegen.

## Control-instantie {#control-instance}

Selecteer het **[!UICONTROL Transactional message control]** -pakket via het menu **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Import package]** om de besturingsinstantie op uw computer te installeren. Voor meer op dit, zie [ Installerend Campaign Classic standaardpakketten ](../../installation/using/installing-campaign-standard-packages.md).

![](assets/messagecenter_install_controlinstance_001.png)

De gedetailleerde stappen om de controleinstantie te vormen worden voorgesteld in [ deze sectie ](../../message-center/using/configuring-instances.md#control-instance).

### Verschillende besturingsinstanties ondersteunen {#supporting-several-control-instances}

>[!IMPORTANT]
>
>Het delen van een uitvoeringscluster met verschillende besturingsinstanties wordt alleen ondersteund voor omgevingen op locatie.

Het is mogelijk om een uitvoeringscluster onder verscheidene controleinstanties te delen. Bijvoorbeeld, als u verscheidene gespecialiseerde opslag beheert, kunt u één controleinstantie per merk vormen en hen verbinden allen aan de zelfde uitvoeringscluster.

![](assets/messagecenter_diagram_2.png)

>[!NOTE]
>
>Voor meer op de noodzakelijke configuratie, verwijs naar [ Gebruik verscheidene controleinstanties ](../../message-center/using/configuring-instances.md#using-several-control-instances).

## Uitvoeringsinstantie {#execution-instance}

Als u een uitvoeringsinstantie op uw computer wilt installeren, selecteert u het pakket **[!UICONTROL Transactional message execution]** via het menu **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Import package]** . Voor meer op dit, zie [ Installerend Campaign Classic standaardpakketten ](../../installation/using/installing-campaign-standard-packages.md).

![](assets/messagecenter_install_executioninstance_001.png)

De gedetailleerde stappen om een uitvoeringsinstantie te vormen worden voorgesteld in [ deze sectie ](../../message-center/using/configuring-instances.md#execution-instance).

## Beschikbare leveringskanalen

Het e-mailkanaal is standaard beschikbaar. Als u uw transactieberichten op meerdere kanalen wilt verzenden, kunt u andere kanalen toevoegen (mobiel kanaal, Mobile App-kanaal, enz.).

>[!IMPORTANT]
>
>Een leveringskanaal toevoegen (mobiel kanaal, Mobile App-kanaal, enz.) moet worden uitgevoerd voordat het Transactiebericht-pakket wordt geïnstalleerd.

### Een leveringskanaal toevoegen {#adding-a-delivery-channel}

De Adobe adviseert u **altijd het pakket van het leveringskanaal alvorens het Transactionele berichtpakket** te installeren toevoegt.

Nochtans, als u een transactie overseinenproject op het e-mailkanaal bent begonnen, dan besluit tijdens het project om een nieuw kanaal toe te voegen, kunt u de hieronder stappen volgen.

>[!NOTE]
>
>Deze procedure is alleen van toepassing op klanten die een Windows NLServer gebruiken die op dezelfde computer is geïnstalleerd als waarop zij werken.

1. Installeer het kanaal u, bijvoorbeeld het **Mobiele kanaal** nodig hebt, gebruikend de medewerker van de pakketinvoer (**[!UICONTROL Tools > Advanced > Import package... > Adobe Campaign Package]**).
1. Voer een dossierinvoer (**[!UICONTROL Tools > Advanced > Import package... > File]**) uit, en selecteer het **datakitnms &#x200B;**`[Your language]`**pakketmanagementCenter.xml** dossier.
1. Bewaar in de **[!UICONTROL XML content of the data to import]** alleen de leveringssjabloon die overeenkomt met het toegevoegde kanaal. Bijvoorbeeld, als u het **Mobiele kanaal** hebt toegevoegd, houd slechts het **entiteiten** element dat aan **[!UICONTROL Mobile transactional message]** beantwoordt (smsTriggerMessage). Als u het **Mobiele Kanaal van de App** hebt toegevoegd, houd slechts het **transactiebericht van iOS** (iosTriggerMessage) en het **de transactionele bericht van Android** (androidTriggerMessage).

   ![](assets/messagecenter_install_channel.png)

<!--## Transactional messages and inbound Interaction {#transactional-messages-and-inbound-interaction}

When combined with the Inbound Interaction module, transactional messaging enables you to insert a marketing offer dedicated to the recipient into the message.

>[!NOTE]
>
>The Interaction module is detailed in [Interaction](../../interaction/using/interaction-and-offer-management.md).

To use transactional messaging with Interaction, you need to apply the following configurations:

* Install the **Interaction** package onto the control instance and configure your offer catalog.

  >[!IMPORTANT]
  >
  >Do not replicate the offers onto the execution instances.

* The event must include an identifier linked to the recipients, for personalizing offers. The **@externalId** attribute must contain the value of this identifier. **Interaction** is configured by default to identify the recipient of the primary key:

  ```
  <rtEvent type="order_confirmation" email="john.doe@adobe.com" externalId="1242"> 
  ```

  You can configure **Interaction** so that identification takes place in the field of your choice, for example on the email address:

  ```
  <rtEvent type="order_confirmation" email="john.doe@adobe.com" externalId="john.doe@yahoo.com"> 
  ```

Create your delivery templates the way you would for an email campaign:

* Add the offer to your transactional message template.
* Check the preview, send a proof and publish the template.

You also have to enable the unitary mode on your offer spaces. For more on this, refer to [this section](../../interaction/using/creating-offer-spaces.md).-->

### Transactionele pushmeldingen {#transactional-messaging-and-push-notifications}

In combinatie met de Mobile App Channel-module kunt u met een transactiebericht transactieberichten verzenden via meldingen op mobiele apparaten.

>[!NOTE]
>
>Het mobiele kanaal van de App is gedetailleerd in [ deze sectie ](../../delivery/using/about-mobile-app-channel.md).

Als u transactiemodules voor berichten wilt gebruiken met Mobile App Channel, moet u de volgende configuraties toepassen:

1. Installeer het **Mobiele pakket van het Kanaal van de App** op de controle en uitvoeringsinstanties.
1. Repliceer de **het typeAdobe Campaign dienst van 0&rbrace; Mobiele toepassing &lbrace;evenals de mobiele toepassingen die het op de uitvoeringsinstanties bevat.**

De gebeurtenis moet de volgende elementen bevatten:

* Mobiele apparatenidentiteitskaart (**registrationId** voor Android en **deviceToken** voor iOS). Deze ID vertegenwoordigt het &quot;adres&quot;dat het bericht zal worden verzonden naar.
* De verbinding aan de mobiele toepassing of de integratiesleutel (**uuid**) die u verbindingsinformatie specifiek voor de toepassing laat terugkrijgen.
* Het kanaal waarnaar het bericht zal worden verzonden (**wishedChannel**): 41 voor iOS en 42 voor Android
* Alle gegevens die nuttig zijn voor personalisatie

Hier volgt een voorbeeld van een gebeurtenis die deze informatie bevat:

```
<SOAP-ENV:Envelope xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/">
   <SOAP-ENV:Body>
     <urn:PushEvent>
         <urn:sessiontoken>mc/</urn:sessiontoken>
         <urn:domEvent>

              <rtEvent wishedChannel="41" type="DELIVERY" registrationToken="2cefnefzef758398493srefzefkzq483974">
                <mobileApp _operation="none" uuid="com.adobe.NeoMiles"/>
                <ctx>
                    <deliveryTime>1:30 PM</deliveryTime>
                    <url>http://www.adobe.com</url>
                </ctx>
              </rtEvent>

         </urn:domEvent>
     </urn:PushEvent>           
   </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

>[!NOTE]
>
>Het maken van berichtsjablonen blijft hetzelfde.

### Transactieberichten en LIJN {#transactional-messaging-and-line}

In combinatie met het lijnkanaal kunt u met transactiemeldingen realtime berichten verzenden naar de LINE-app die is geïnstalleerd in mobiele apparaten voor consumenten. Hiermee wordt het welkomstbericht verzonden wanneer een lijngebruiker de pagina van het merk toevoegt.

Om transactionele berichtmodule met LIJN te gebruiken, zijn de volgende elementen nodig voor de configuratie op uw **marketing** instantie en uw **uitvoerings** instantie:

* Installeer het **[!UICONTROL LINE Connect]** -pakket op beide instanties.
* Installeer het pakket **[!UICONTROL Transactional message control]** op de marketinginstantie en het pakket **[!UICONTROL Transactional message execution]** op de uitvoeringsinstantie.
* Creeer de externe rekening van de LIJN **&#x200B;**&#x200B;en **dienst** op beide instanties met het identieke noemen voor hen om worden gesynchroniseerd. Voor meer informatie over hoe te om tot een externe rekening en de dienst van de LIJN te leiden, verwijs naar [ deze sectie ](../../delivery/using/line-channel.md#setting-up-line-channel).

Vervolgens moet u in **[!UICONTROL Explorer]** , in **[!UICONTROL Platform]** > **[!UICONTROL External account]** , verschillende externe accounts configureren voor beide instanties:

1. Creeer een **[!UICONTROL External database]** externe rekening in uw **uitvoerings** instantie met de volgende configuratie:

   ![](assets/line_config_mc.png)

   * **[!UICONTROL Label]** en **[!UICONTROL Internal name]** : geef uw externe account de naam die u nodig hebt.
   * **[!UICONTROL Type]** : select **[!UICONTROL External database]** .
   * **[!UICONTROL Enabled]** moet zijn ingeschakeld.

   Van de categorie **[!UICONTROL Connection]** :

   * **[!UICONTROL Type]** : selecteer uw databaseserver, bijvoorbeeld PostgresSQL.
   * **[!UICONTROL Server]** : voer de URL van de databaseserver in.
   * **[!UICONTROL Account]** : voer uw databaseaccount in.

     >[!NOTE]
     >
     >De databasegebruiker moet leesrechten hebben voor de volgende tabellen voor FDA-verbinding: XtkOption, NmsVisitor, NmsVisitorSub, NmsService, NmsBroadLogRtEvent, NmsBroadLogBatchEvent, NmsTrackingLogRtEvent, NmsTrackingLogBatchEvent, NmsRms tEvent, NmsBatchEvent, NmsBroadLogMsg, NmsTrackingUrl, NmsDelivery, NmsWebTrackingLogXtkFolder.

   * **[!UICONTROL Password]** : voer het wachtwoord voor uw databaseaccount in.
   * **[!UICONTROL Database]** : voer de databasenaam van de uitvoeringsinstantie in.
   * **[!UICONTROL Target of an HTTP relay to remote database's account]** moet zijn ingeschakeld.

1. Creeer een **[!UICONTROL External Database]** rekening in uw **marketing** instantie met de volgende configuratie.

   ![](assets/line_config_mc_1.png)

   * **[!UICONTROL Label]** en **[!UICONTROL Internal name]** : geef uw externe account de naam die u nodig hebt.
   * **[!UICONTROL Type]** : select **[!UICONTROL External database]** .
   * Ingeschakelde doos moet worden gecontroleerd.

   Van de categorie **[!UICONTROL Connection]** :

   * **[!UICONTROL Type]** : select **[!UICONTROL HTTP relay to remote Database]** .
   * **[!UICONTROL Server]** : voer de server-URL van de uitvoeringsinstantie van uw campagne in.
   * **[!UICONTROL Account]** : voer het account in dat wordt gebruikt om toegang te krijgen tot uw uitvoeringsinstantie.
   * **[!UICONTROL Password]** : voer het wachtwoord in voor de account die wordt gebruikt om toegang te krijgen tot uw uitvoeringsinstantie.
   * **[!UICONTROL Data Source]** : voer de volgende syntaxis **`nms:extAccount:ID`** van uw externe databaseaccount in de uitvoeringsinstantie in.

1. Creeer een **[!UICONTROL Execution instance]** externe rekening in uw **marketing** instantie gebruikend de volgende configuratie om het werkschema van de gegevenssynchronisatie tot stand te brengen:

   ![](assets/line_config_mc_2.png)

   * **[!UICONTROL Label]** en **[!UICONTROL Internal name]** : geef uw externe account de naam die u nodig hebt.
   * **[!UICONTROL Type]** : select **[!UICONTROL Execution instance]** .
   * Ingeschakelde doos moet worden gecontroleerd.

   Van de categorie **[!UICONTROL Connection]** :

   * **[!UICONTROL URL]** : voer de URL van de uitvoeringsinstantie in.
   * **[!UICONTROL Account]** : voer uw account in die u gebruikt om toegang te krijgen tot uw uitvoeringsinstantie.
   * **[!UICONTROL Password]** : voer het wachtwoord in voor de account die wordt gebruikt om toegang te krijgen tot uw uitvoeringsinstantie.

   Van de categorie **[!UICONTROL Account connection method]** :

   * **[!UICONTROL Method]** : select **[!UICONTROL Federated Data Access (FDA)]** .
   * **[!UICONTROL FDA account]** : selecteer uw FDA-account in de vervolgkeuzelijst.
   * Klik op de knop **[!UICONTROL Create the archiving workflow]**.
   * Klik op de knop **[!UICONTROL Create data synchronization workflow]** om de workflow voor het synchroniseren van lijngegevens te maken.

1. U kunt [ nu beginnen creërend transactionele berichten ](../../message-center/using/creating-the-message-template.md).
