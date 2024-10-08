---
product: campaign
title: Inkomende sms-workflowactiviteit voor mid-sourcing-infrastructuur
description: Inkomende sms-workflowactiviteit voor mid-sourcing-infrastructuur
feature: Technote, SMS
exl-id: 756039b2-5f57-4dc5-8166-a421206b886b
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 5%

---

# Inkomende sms-workflowactiviteit voor mid-sourcing-infrastructuur {#inbound-sms-wf}

## Beperkingen {#limitations}

* Dit gebruiksgeval is alleen van toepassing op de marketinginstantie waar u inSMS-gegevens verzamelt van de instantie(s) van de tussenbron.
* Implementeer dit gebruiksgeval niet op de instantie Midden-sourcing.
* Slechts één aangepaste workflow per externe account voor midsourcing.

## Implementatie {#implementation}

1. Voeg een extensie toe aan het schema `nms:inSMS` op uw marketingexemplaar. De extensie voegt een nieuw kenmerk toe aan het `nms:inSMS` -schema en houdt de primaire sleutel van de inSMS-record die afkomstig is van de instantie Midden-sourcing bij.

   ```xml
   <element img="nms:miniatures/mini-sms.png" label="Incoming SMS"
          labelSingular="Incoming SMS" name="inSMS">
   <dbindex name="midInSMSId" unique="false">
     <keyfield xpath="@extAccount-id"/>
     <keyfield xpath="@midInSMSId"/>
   </dbindex>
   
   <attribute label="External Mid SMS ID" name="midInSMSId" type="long"/>
   </element>
   ```

1. Om de wijzigingen toe te passen die aan de schema&#39;s worden aangebracht, lanceer de medewerker van de gegevensbestandupdate. Deze medewerker is toegankelijk via **Hulpmiddelen** > **Geavanceerd** > **de gegevensbestandstructuur van de Update**. Het controleert of de fysieke structuur van het gegevensbestand zijn logische beschrijving aanpast en de SQL updatescripts uitvoert. [Meer informatie](../../configuration/using/updating-the-database-structure.md)

1. Het einde en steun uw werkschema dat de **Binnenkomende activiteit van SMS** bevat.

   Maak een back-up van de overeenkomende aanwijzer van de optie met de volgende notatie `SMS_MO_INDEX_{internal name of the workflow}_{name of the insms workflow activity}_{internal name of the external account to access the mid}` .

[Meer informatie over back-ups](../../production/using/backup.md)

1. (**OPTIONEEL**) als u reeds een activiteit van de Planner gebruikt, open het werkschema en hervorm het als volgt:

   1. Herhaal de huidige montages van het **Programma** lusje van uw **Binnenkomende activiteit van SMS** in uw externe **planner** activiteit.

   1. Maak het huidige plaatsen in het **Programma** lusje van **Binnenkomende activiteit van SMS** onbruikbaar.

      ![](assets/inbound_sms_1.png)

1. Werk **Binnenkomend SMS** douanescript bij.

   Vervang het onderstaande blok. Dit script kan variëren als u deze code eerder hebt aangepast.

   ```Javascript
   var lastSynchKey = getOption('SMS_MO_INDEX_WKF1105_inSmsUS_smsmidus');
   
   var smsId = application.getNewIds(1);
   
   xtk.session.Write(<inSMS xtkschema="nms:inSMS" _operation="insert"
       id={smsId}
       origin={smsMessage.origin}
       message={smsMessage.message}
       providerId={smsMessage.messageId}/>);
   
   return 2;
   ```

   Met het volgende nieuwe douanescript om inSMS gegevens bij te werken die op een samengestelde sleutel worden gebaseerd, die de primaire sleutel van het middelsourcingsverslag en externe rekening identiteitskaart van het Verkoop SMS combineren die verplettert.

   Volg de onderstaande voorwaarden:

   * Voer de werkelijke waarde in voor `<EXTERNAL_ACCOUNT_ID>` , bijvoorbeeld `var iExtAccountId=72733155` .
   * Zorg ervoor dat u de volgende elementen in het aangepaste script opneemt:
      * `_operation="insertOrUpdate"`
      * `_key="@midInSMSId,@extAccount-id"`
      * `midInSMSId={smsMessage.id}`
      * `inSms.@["extAccount-id"] = iExtAccountId;{}`

   ```Javascript
   // please enter real external account ID to replace <EXTERNAL ACCOUNT ID>
   var iExtAccountId=<EXTERNAL_ACCOUNT_ID>;
   
   var inSms = <inSMS xtkschema="nms:inSMS" _operation="insertOrUpdate"
   
               _key="@midInSMSId,@extAccount-id"
               midInSMSId={smsMessage.id}
               message={smsMessage.message}
               origin={smsMessage.origin}
               providerId={smsMessage.providerId}
               alias={smsMessage.alias}
               messageDate = {smsMessage.messageDate}
               receivalDate = {smsMessage.receivalDate}
               deliveryDate = {smsMessage.deliveryDate}
               largeAccount = {smsMessage.largeAccount}
               countryCode = {smsMessage.countryCode}
               operatorCode = {smsMessage.operatorCode}
               linkedSmsId={smsMessage.linkedSmsId}
               separator = {smsMessage.separator}/>
   
   inSms.@["extAccount-id"] = iExtAccountId;
   
   xtk.session.Write(inSms);
   
   return 2;
   ```

1. Werk het Binnenkomende Geavanceerde SMS initialisatiescript met het volgende manuscript bij.

   Het script stelt de aanwijzer van de primaire sleutel opnieuw in op 24 uur eerder. De workflow probeert alle InSMS-gegevens van de instantie Midden-sourcing binnen de voorafgaande 24 uur opnieuw te verwerken en eventuele ontbrekende gegevens aan de instantie Marketing toe te voegen.

   ```Javascript
   // please enter real external account ID to replace <EXTERNAL_ACCOUNT_ID>
   // please enter real pointer option name to replace '<POINTER_OPTION_NAME>'
   // OPTION NAME format: SMS_MO_INDEX_{internal name of the workflow}_inSms_{internal name of the external account to access the mid}
   
   var queryDef = xtk.queryDef.create(
       <queryDef operation="getIfExists" schema="nms:inSMS" lineCount="1">
       <select>
           <node expr="@midInSMSId" alias="@midInSMSId"/>
       </select>
       <where>
           <condition expr="@midInSMSId != 0"/>
           <condition expr={"@created > SubHours(GetDate(), 24)"}/>
           <condition expr={"[@extAccount-id]=<EXTERNAL_ACCOUNT_ID>"}/>
       </where>
       <orderBy>
           <node expr="@midInSMSId"/>
       </orderBy>
       </queryDef>);
   
   var res = parseInt(queryDef.ExecuteQuery().@midInSMSId.toString());
   
   if( !isNaN(res) )
   setOption('<POINTER_OPTION_NAME>', res);
   ```

   >[!WARNING]
   >
   > * Als verscheidene SMS die rekeningen verpletteren met de zelfde Midden-sourcing instantie worden verbonden, slechts wordt één enkel werkschema per Midden-sourcing instantie toegelaten.
   > * U kunt elke externe account-id gebruiken. De rol van de buitenlandse sleutel is het handhaven van de integriteit van de gegevensverzoening in scenario&#39;s die verschillende Midden-sourcingservers impliceren waar identiteitskaart van Midden-sourcing SMS over andere Midden-sourcinginstanties identiek zou kunnen zijn.
   > * Als er meerdere InSMS-workflows per instantie van de tussenbron zijn, kan gegevensduplicatie optreden omdat de SMS-id van de tussenbron constant blijft terwijl de externe account-id&#39;s variëren.

1. Sla de workflow op en start deze opnieuw.
