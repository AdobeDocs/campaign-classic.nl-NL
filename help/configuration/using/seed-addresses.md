---
product: campaign
title: Seedadressen
description: Seedadressen
role: Data Engineer, Developer
badge-v8: label="Ook van toepassing op v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
feature: Seed Address
level: Intermediate, Experienced
exl-id: a16103bf-0498-4f59-ad96-8bfdeea26577
source-git-commit: 2bfcec5eaa1145cfb88adfa9c8b2f72ee3cd9469
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 6%

---

# Seedadressen{#seed-addresses}



Als de ontvankelijke lijst een douanetabel is, worden de extra configuraties vereist. Het schema **[!UICONTROL nms:seedMember]** moet worden uitgebreid. Er wordt een extra tabblad toegevoegd aan de podadressen voor het definiëren van de juiste velden, zoals hieronder wordt getoond:

![](assets/s_ncs_user_seedlist_new_tab.png)

Voor meer bij het gebruiken van zaadadressen, verwijs [ deze sectie ](../../delivery/using/about-seed-addresses.md).

## Implementatie {#implementation}

**nms:seedMember** schema en de verbonden vorm die uit-van-de-doos komen moeten voor klantenconfiguratie worden uitgebreid, om alle noodzakelijke gebieden van verwijzingen te voorzien. De schemadefinitie bevat commentaren detailleert zijn configuratiewijze.

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

1. Creeer een uitbreiding van het **nms:seedMember** schema. Raadpleeg [deze sectie](../../configuration/using/extending-a-schema.md) voor meer informatie.
1. Voeg in deze nieuwe extensie een nieuw element toe aan de basis van **[!UICONTROL seedMember]** met de volgende parameters:

   ```
   name="custom_customNamespace_customSchema"
   ```

   Dit element moet de velden bevatten die vereist zijn om de campagnes te exporteren. Deze velden moeten dezelfde naam hebben als de corresponderende velden in het externe schema. Als het schema bijvoorbeeld **[!UICONTROL cus:person]** is, moet het schema **[!UICONTROL nms:seedMember]** als volgt worden uitgebreid:

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
   >De uitbreiding van **nms:seedMember** schema moet aan de structuren van een campagne en een levering in Adobe Campaign voldoen.

   >[!IMPORTANT]
   >
   >
   >    
   >    
   >    * Tijdens de uitbreiding, moet u een **SQL naam (@sqlname)** voor het &quot;e-mailgebied&quot;specificeren. De SQL-naam moet afwijken van de &#39;sEmail&#39;-naam die is gereserveerd voor het ontvangende schema.
   >    * U moet de gegevensbestandstructuur met het gecreeerde schema bijwerken wanneer het uitbreiden van **nms:seedMember**.
   >    * In **nms:seedMember** uitbreiding, moet het gebied dat het e-mailadres bevat **name= &quot;email&quot;** als attribuut hebben. De SQL-naam moet anders zijn dan &#39;sEmail&#39;, dat al wordt gebruikt voor het ontvangende schema. Dit kenmerk moet onmiddellijk worden gedeclareerd onder het element **`<element name="custom_cus_person" />`** .
   >    
   >

1. Wijzig het **[!UICONTROL seedMember]** -formulier dienovereenkomstig om een nieuw tabblad &quot;Interne ontvanger&quot; in het **[!UICONTROL Seed addresses]** -venster te definiëren. Raadpleeg [deze pagina](../../configuration/using/form-structure.md) voor meer informatie.

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
