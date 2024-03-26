---
product: campaign
title: Seedadressen
description: Seedadressen
role: Data Engineer, Developer
badge-v7: label="v7" type="Informative" tooltip="Is van toepassing op Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
feature: Seed Address
exl-id: a16103bf-0498-4f59-ad96-8bfdeea26577
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 6%

---

# Seedadressen{#seed-addresses}



Als de ontvankelijke lijst een douanetabel is, worden de extra configuraties vereist. De **[!UICONTROL nms:seedMember]** schema moet worden uitgebreid. Er wordt een extra tabblad toegevoegd aan de podadressen voor het definiëren van de juiste velden, zoals hieronder wordt getoond:

![](assets/s_ncs_user_seedlist_new_tab.png)

Voor meer bij het gebruiken van zaadadressen, verwijs [deze sectie](../../delivery/using/about-seed-addresses.md).

## Implementatie {#implementation}

De **nms:zaadMember** schema&#39;s en de gekoppelde vorm die uit-van-de-doos komen moeten voor klantenconfiguratie worden uitgebreid, om alle noodzakelijke gebieden van verwijzingen te voorzien. De schemadefinitie bevat commentaren detailleert zijn configuratiewijze.

Definitie van het uitgebreide schema van de lijst van ontvangers:

```
<srcSchema label="Person" name="person" namespace="cus">
  <element autopk="true" label="Person" name="person">
      <attribute label="LastName" name="lastname" type="string"/>
      <attribute label="FirstName" name="firstname" type="string"/>
    <element label="Address" name="address">
      <attribute label="Email" name="addrEnv" type="string"/>
    </element>
    <attribute label="Code Offer" name="codeOffer" type="string"/>
  </element>
</srcSchema>
```

Voer de volgende stappen uit:

1. Een extensie maken van de **nms:zaadMember** schema. Raadpleeg [deze sectie](../../configuration/using/extending-a-schema.md) voor meer informatie.
1. Voeg in deze nieuwe extensie een nieuw element toe aan de basis van **[!UICONTROL seedMember]** met de volgende parameters:

   ```
   name="custom_customNamespace_customSchema"
   ```

   Dit element moet de velden bevatten die vereist zijn om de campagnes te exporteren. Deze velden moeten dezelfde naam hebben als de corresponderende velden in het externe schema. Als het schema bijvoorbeeld **[!UICONTROL cus:person]** de **[!UICONTROL nms:seedMember]** schema moet als volgt worden uitgebreid:

   ```
     <srcSchema extendedSchema="nms:seedMember" label="Seed addresses" labelSingular="Seed address" name="seedMember" namespace="cus">
     <element name="common">
       <element name="custom_cus_person">
         <attribute name="lastname" template="cus:person:person/@lastname"/>
         <attribute name="firstname" template="cus:person:person/@firstname"/>
         <attribute name="email" sqlname="myEmailField" template="cus:person:person/address/@addrEnv" xml="false"/>
       </element>
     </element>
     <element name="seedMember">
      <element aggregate="cus:seedMember:common"/>
     </element>
   </srcSchema>
   ```

   >[!NOTE]
   >
   >De verlenging van de **nms:zaadMember** schema moet voldoen aan de structuur van een campagne en een levering in Adobe Campaign.

   >[!IMPORTANT]
   >
   >
   >    
   >    
   >    * Tijdens de extensie moet u een **SQL-naam (@sqlname)** voor het veld E-mail. De SQL-naam moet afwijken van de &#39;sEmail&#39;-naam die is gereserveerd voor het ontvangende schema.
   >    * U moet de databasestructuur bijwerken met het gemaakte schema wanneer u het uitbreidt **nms:zaadMember**.
   >    * In de **nms:zaadMember** extensie, moet het veld dat het e-mailadres bevat **name=&quot;email&quot;** als een kenmerk. De SQL-naam moet anders zijn dan &#39;sEmail&#39;, dat al wordt gebruikt voor het ontvangende schema. Dit kenmerk moet onmiddellijk onder het **`<element name="custom_cus_person" />`** element.
   >    
   >

1. Wijzig de **[!UICONTROL seedMember]** formulier dienovereenkomstig een nieuw tabblad &quot;Interne ontvanger&quot; definiëren in het dialoogvenster **[!UICONTROL Seed addresses]** venster. Raadpleeg [deze pagina](../../configuration/using/form-structure.md) voor meer informatie.

   ```
   <container colcount="2" label="Internal recipient" name="internal"
                xpath="custom_cus_person">
       <input colspan="2" editable="true" nolabel="true" type="treeEdit">
         <container label="Recipient (cus:person)">
           <input xpath="@last name"/>
           <input xpath="@first name"/>
           <input xpath="@email"/>
         </container>
       </input>
     </container>
   ```

Als niet alle attributen van het zaadadres zijn ingegaan, vervangt Adobe Campaign automatisch de profielen: zij zullen automatisch tijdens verpersoonlijking gebruikend gegevens van een bestaand profiel worden ingegaan.
