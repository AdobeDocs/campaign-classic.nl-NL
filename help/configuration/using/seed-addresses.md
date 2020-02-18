---
title: Zaadadressen
seo-title: Zaadadressen
description: Zaadadressen
seo-description: null
page-status-flag: never-activated
uuid: 0ebdeb73-be67-4c34-9f59-9fd4fb5241ab
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
discoiquuid: 41338d32-b95c-45ae-bee6-17b2af5bd837
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: dbff132e3bf88c408838f91e50e4b047947ee32a

---


# Zaadadressen{#seed-addresses}

Als de ontvankelijke lijst een douanetabel is, worden de extra configuraties vereist. Het **[!UICONTROL nms:seedMember]** schema moet worden uitgebreid. Er wordt een extra tabblad toegevoegd aan de podadressen voor het definiëren van de juiste velden, zoals hieronder wordt getoond:

![](assets/s_ncs_user_seedlist_new_tab.png)

Voor meer bij het gebruiken van zaadadressen, verwijs [deze sectie](../../delivery/using/about-seed-addresses.md).

## Implementatie {#implementation}

Het schema **nms:seedMember** en de gekoppelde vorm die uit-van-de-doos komen moeten voor klantenconfiguratie worden uitgebreid, om alle noodzakelijke gebieden van verwijzingen te voorzien. De schemadefinitie bevat commentaren detailleert zijn configuratiewijze.

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

1. Maak een extensie van het schema **nms:seedMember** . Raadpleeg [Een schema](../../configuration/using/extending-a-schema.md)uitbreiden voor meer informatie.
1. Voeg in deze nieuwe extensie een nieuw element toe aan de basis van **[!UICONTROL seedMember]** de volgende parameters:

   ```
   name="custom_customNamespace_customSchema"
   ```

   Dit element moet de velden bevatten die vereist zijn om de campagnes te exporteren. Deze velden moeten dezelfde naam hebben als de corresponderende velden in het externe schema. Als het schema bijvoorbeeld is **[!UICONTROL cus:person]** , moet het **[!UICONTROL nms:seedMember]** schema als volgt worden uitgebreid:

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
   >De uitbreiding van het schema **nms:seedMember** moet voldoen aan de structuren van een campagne en een levering in de Campagne van Adobe.

   >[!IMPORTANT]
   >
   >
   >    
   >    
   >    * Tijdens de extensie moet u een **SQL-naam (@sqlname)** opgeven voor het veld E-mail. De SQL-naam moet afwijken van de &#39;sEmail&#39;-naam die is gereserveerd voor het ontvangende schema.
   >    * U moet de databasestructuur bijwerken met het gemaakte schema wanneer u **nms:seedMember** uitbreidt.
   >    * In de extensie **nms:seedMember** moet het veld met het e-mailadres **name=&quot;email&quot;** hebben als kenmerk. De SQL-naam moet anders zijn dan &#39;sEmail&#39;, dat al wordt gebruikt voor het ontvangende schema. Dit kenmerk moet onmiddellijk onder het **`<element name="custom_cus_person" />`** element worden gedeclareerd.


1. Wijzig het **[!UICONTROL seedMember]** formulier dienovereenkomstig om een nieuw tabblad &quot;Interne ontvanger&quot; in het **[!UICONTROL Seed addresses]** venster te definiëren. Raadpleeg de [formulierstructuur](../../configuration/using/form-structure.md)voor meer informatie.

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

Als niet alle attributen van het zaadadres zijn ingegaan, vervangt de Campagne van Adobe automatisch de profielen: deze gegevens worden automatisch ingevoerd tijdens de personalisatie met behulp van gegevens uit een bestaand profiel.
