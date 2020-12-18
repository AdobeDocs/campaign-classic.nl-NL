---
solution: Campaign Classic
product: campaign
title: Seed-adressen
description: Seed-adressen
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '323'
ht-degree: 1%

---


# Seed-adressen{#seed-addresses}

Als de ontvankelijke lijst een douanetabel is, worden de extra configuraties vereist. Het schema **[!UICONTROL nms:seedMember]** moet worden uitgebreid. Er wordt een extra tabblad toegevoegd aan de podadressen voor het definiëren van de juiste velden, zoals hieronder wordt getoond:

![](assets/s_ncs_user_seedlist_new_tab.png)

Voor meer bij het gebruiken van zaadadressen, verwijs [deze sectie](../../delivery/using/about-seed-addresses.md).

## Implementatie {#implementation}

Het schema **nms:seedMember** en de gekoppelde vorm die uit-van-de-doos komen zijn bedoeld om voor klantenconfiguratie worden uitgebreid, om naar alle noodzakelijke gebieden te verwijzen. De schemadefinitie bevat commentaren detailleert zijn configuratiewijze.

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

1. Maak een extensie van het schema **nms:seedMember**. Voor meer op dit, verwijs naar [Uitbreidend een schema](../../configuration/using/extending-a-schema.md).
1. In deze nieuwe uitbreiding, voeg een nieuw element bij de wortel van **[!UICONTROL seedMember]** met de volgende parameters toe:

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
   >De uitbreiding van het schema **nms:seedMember** moet voldoen aan de structuren van een campagne en een levering in Adobe Campaign.

   >[!IMPORTANT]
   >
   >
   >    
   >    
   >    * Tijdens de extensie moet u een **SQL-naam (@sqlname)** opgeven voor het veld E-mail. De SQL-naam moet afwijken van de &#39;sEmail&#39;-naam die is gereserveerd voor het ontvangende schema.
   >    * U moet de databasestructuur bijwerken met het gemaakte schema wanneer u **nms:seedMember** uitbreidt.
   >    * In de extensie **nms:zaadlid** moet het veld met het e-mailadres **name=&quot;email&quot;** hebben als kenmerk. De SQL-naam moet anders zijn dan &#39;sEmail&#39;, dat al wordt gebruikt voor het ontvangende schema. Dit kenmerk moet onmiddellijk worden gedeclareerd onder het element **`<element name="custom_cus_person" />`**.


1. Wijzig het formulier **[!UICONTROL seedMember]** dienovereenkomstig om een nieuw tabblad &quot;Interne ontvanger&quot; in het venster **[!UICONTROL Seed addresses]** te definiëren. Raadpleeg [Formulierstructuur](../../configuration/using/form-structure.md) voor meer informatie.

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

Als niet alle attributen van het zaadadres zijn ingegaan, vervangt Adobe Campaign automatisch de profielen: deze gegevens worden automatisch ingevoerd tijdens de personalisatie met behulp van gegevens uit een bestaand profiel.
