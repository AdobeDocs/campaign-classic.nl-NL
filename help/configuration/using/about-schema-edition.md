---
product: campaign
title: De schema-editor
description: Aan de slag met schema-editie
audience: configuration
content-type: reference
topic-tags: editing-schemas
exl-id: 9e10b24e-c4de-4e76-bbed-0d05f62120b7
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '1004'
ht-degree: 7%

---

# De schema-editor{#about-schema-edition}

Adobe Campaign past gegevensschema&#39;s toe op:

* Definiëren hoe dataobjecten in de applicatie worden gekoppeld aan onderliggende databasetabellen.
* Definiëren van koppelingen tussen de verschillende dataobjecten in de Campaign-applicatie.
* Definiëren en beschrijven van de afzonderlijke velden die in elk object zijn opgenomen.

Raadpleeg [deze sectie](https://helpx.adobe.com/nl/campaign/kb/acc-datamodel.html) voor een beter begrip van geïntegreerde tabellen en hun interactie voor campagnes.

## Schema&#39;s uitbreiden of maken {#extending-or-creating-schemas}

Als u een veld, index of ander element wilt toevoegen aan een van de schema&#39;s met kerngegevens in Campagne, zoals de ontvangende tabel (nms:ontvanger), moet u dat schema uitbreiden. Voor meer op dit, verwijs naar [Uitbreidend een schema](../../configuration/using/extending-a-schema.md) sectie.

Als u een geheel nieuw type gegevens wilt toevoegen dat niet in Adobe Campaign buiten het vak bestaat (bijvoorbeeld een contracttabel), kunt u rechtstreeks een aangepast schema maken. Raadpleeg voor meer informatie de sectie [Gegevensschema&#39;s](../../configuration/using/data-schemas.md).

![](assets/schemaextension_getting_started_1.png)

Nadat u een schema hebt uitgebreid of gemaakt waarin u wilt werken, kunt u het beste de XML-inhoudselementen definiëren in dezelfde volgorde als hieronder.

## Opsommingen {#enumerations}

Opsommingen worden eerst gedefinieerd, vóór het hoofdelement van het schema. Hiermee kunt u waarden in een lijst weergeven om de keuzes te beperken die de gebruiker voor een bepaald veld heeft.

Voorbeeld:

```
<enumeration basetype="byte" name="exTransactionTypeEnum" default="store">
<value label="Website" name="web" value="0"/>
<value label="Call Center" name="phone" value="1"/>
<value label="In Store" name="store" value="2"/>
</enumeration>
```

Wanneer u velden definieert, kunt u deze opsomming als volgt gebruiken:

```
<attribute desc="Type of Transaction" label="Transaction Type" name="transactionType" 
type="string" enum="exTransactionTypeEnum"/>
```

>[!NOTE]
>
>U kunt door de gebruiker beheerde opsommingen ook gebruiken (gewoonlijk onder **[!UICONTROL Administration]** > **[!UICONTROL Platform]**) om de waarden voor een bepaald veld op te geven. Dit zijn in feite globale opsommingen, en een betere keus als uw opsomming buiten het specifieke schema kan worden gebruikt u binnen werkt.

Als u meer informatie wilt over opsommingen, raadpleegt u de secties [Opsommingen](../../configuration/using/schema-structure.md#enumerations) en [`<enumeration>` element](../../configuration/using/schema/enumeration.md).

## Index {#index}

Indexen zijn de eerste elementen die in het hoofdelement van het schema worden gedeclareerd.

Ze kunnen uniek zijn of niet en verwijzen naar een of meer velden.

Voorbeelden:

```
<dbindex name="email" unique="true">
  <keyfield xpath="@email"/>
</dbindex>
```

```
<dbindex name="lastNameAndZip">
  <keyfield xpath="@lastName"/>
  <keyfield xpath="location/@zipCode"/>
</dbindex>
```

Het **xpath** attribuut richt aan het gebied in uw schema dat u wenst om te indexeren.

>[!IMPORTANT]
>
>Het is belangrijk om te herinneren dat de SQL de prestatiewinst van de vraaglees die door indexen wordt verstrekt ook met een prestatieshit bij het schrijven van verslagen komt. De indexen moeten daarom met voorzichtigheid worden gebruikt.

Raadpleeg de sectie [Geïndexeerde velden](../../configuration/using/database-mapping.md#indexed-fields) voor meer informatie over indexen.

## Toetsen {#keys}

Elke lijst moet minstens één sleutel hebben, en vaak wordt het automatisch gevestigd in het belangrijkste element van het schema door **@autopk=true** attributen te gebruiken die aan &quot;waar&quot;worden geplaatst.

De primaire sleutel kan ook worden bepaald gebruikend het **internal** attribuut.

Voorbeeld:

```
<key name="householdId" internal="true">
  <keyfield xpath="@householdId"/>
</key>
```

In dit voorbeeld, in plaats van het laten **@automatische attribuut** een standaard primaire sleutel tot stand brengen genoemd &quot;id&quot;wij specificeren onze eigen &quot;huishoudenId&quot;primaire sleutel.

>[!IMPORTANT]
>
>Wanneer het creëren van een nieuw schema of tijdens een schemauitbreiding, moet u de zelfde primaire zeer belangrijke opeenvolgingswaarde (@pkSequence) voor het volledige schema houden.

Raadpleeg de sectie [Beheer van sleutels](../../configuration/using/database-mapping.md#management-of-keys) voor meer informatie over toetsen.

## Attributen (velden) {#attributes--fields-}

Met kenmerken kunt u de velden definiëren waaruit het gegevensobject bestaat. U kunt de **[!UICONTROL Insert]** knoop in de toolbar van de schemageditie gebruiken om lege attributenmalplaatjes in uw XML te laten vallen waar uw curseur is. Raadpleeg voor meer informatie de sectie [Gegevensschema&#39;s](../../configuration/using/data-schemas.md).

![](assets/schemaextension_getting_started_2.png)

De volledige lijst van attributen is beschikbaar in [`<attribute>` element](../../configuration/using/schema/attribute.md) sectie. Hier volgen enkele van de meer gebruikte kenmerken:

* **@advanced**
* **@dataPolicy**
* **@default**
* **@desc**
* **@enum**
* **@expr**
* **@label**
* **@length**
* **@name**
* **@notNull**
* **@required**
* **@ref**
* **@xml**
* **@type**

   Als u een tabel wilt weergeven met de toewijzingen voor de gegevenstypen die door Adobe Campaign zijn gegenereerd voor de verschillende databasebeheersystemen, raadpleegt u de sectie [Typen Adobe Campaign/DBMS-gegevens toewijzen](../../configuration/using/schema-structure.md#mapping-the-types-of-adobe-campaign-dbms-data).

Raadpleeg de sectie [Kenmerkbeschrijving](../../configuration/using/schema/attribute.md) voor meer informatie over elk kenmerk.

### Voorbeelden {#examples}

Voorbeeld van het definiëren van een standaardwaarde:

```
<attribute name="transactionDate" label="Transaction Date" type="datetime" default="GetDate()"/>
```

Voorbeeld van het gebruik van een gemeenschappelijk kenmerk als een sjabloon voor een veld dat ook als verplicht is gemarkeerd:

```
<attribute name="mobile" label="Mobile" template="nms:common:phone" required="true" />
```

Voorbeeld van een berekend veld dat is verborgen met het kenmerk **@advanced**:

```
<attribute name="domain" label="Email domain" desc="Domain of recipient email address" expr="GetEmailDomain([@email])" advanced="true" />
```

Voorbeeld van een XML-veld dat ook is opgeslagen in een SQL-veld en dat het kenmerk **@dataPolicy** heeft.

```
<attribute name="secondaryEmail" label="Secondary email address" length="100" xml="true" sql="true" dataPolicy="email" />
```

>[!IMPORTANT]
>
>Hoewel de meeste kenmerken volgens een 1-1-cardinaliteit aan een fysiek veld van de database zijn gekoppeld, is dit niet het geval voor de XML-velden of de berekende velden.\
>Een XML-veld wordt opgeslagen in een memoveld (&quot;mData&quot;) van de tabel.\
>Een gegevens verwerkt gebied nochtans wordt gecreeerd dynamisch telkens als een vraag wordt begonnen, bestaat het daarom slechts in de toepassingslaag.

## Koppelingen {#links}

De verbindingen zijn enkele laatste elementen in het belangrijkste element van uw schema. Ze definiëren hoe alle verschillende schema&#39;s in uw instantie op elkaar betrekking hebben.

De verbindingen worden verklaard in het schema dat **buitenlandse sleutel** van de lijst bevat waaraan het wordt verbonden.

Er zijn drie soorten kardinaliteit: 1-1, 1-N, en N-N. Het is het type 1-N dat door gebrek wordt gebruikt.

### Voorbeelden {#examples-1}

Een voorbeeld van een verbinding 1-N tussen de ontvankelijke lijst (out-of-the-box schema) en een lijst van douanetransacties:

```
<element label="Recipient" name="lnkRecipient" revLink="lnkTransactions" target="nms:recipient" type="link"/>
```

Een voorbeeld van een 1-1 verbinding tussen een douaneschema &quot;Auto&quot;(in &quot;cus&quot;namespace) en de ontvankelijke lijst:

```
<element label="Car" name="lnkCar" revCardinality="single" revLink="recipient" target="cus:car" type="link"/>
```

Voorbeeld van een externe verbinding tussen de ontvankelijke lijst en een lijst van adressen die op het e-mailadres en niet een primaire sleutel wordt gebaseerd:

```
<element name="emailInfo" label="Email Info" revLink="recipient" target="nms:address" type="link" externalJoin="true">
  <join xpath-dst="@address" xpath-src="@email"/>
</element>
```

Hier komt &#39;xpath-dst&#39; overeen met de primaire sleutel in het doelschema en &#39;xpath-src&#39; komt overeen met de externe sleutel in het bronschema.

## Audit trail {#audit-trail}

Eén handig element dat u onder aan het schema wilt opnemen, is een element tracking (audittrail).

In het onderstaande voorbeeld kunt u velden opnemen die betrekking hebben op de aanmaakdatum, de gebruiker die de gegevens heeft gemaakt, de datum en de auteur van de laatste wijziging voor alle gegevens in de tabel:

```
<element aggregate="xtk:common:auditTrail" name="auditTrail"/>
```

## De databasestructuur bijwerken {#updating-the-database-structure}

Nadat de wijzigingen zijn voltooid en opgeslagen, moeten alle wijzigingen die van invloed kunnen zijn op de SQL-structuur worden toegepast op de database. Hiervoor gebruikt u de wizard Database bijwerken.

![](assets/schemaextension_getting_started_3.png)

Raadpleeg de sectie [De databasestructuur bijwerken](../../configuration/using/updating-the-database-structure.md) voor meer informatie.

>[!NOTE]
>
>Wanneer de wijzigingen niet de gegevensbestandstructuur beïnvloeden, moet u enkel schema&#39;s regenereren. Selecteer hiertoe de schema&#39;s die u wilt bijwerken, klik met de rechtermuisknop en kies **[!UICONTROL Actions > Regenerate selected schemas...]**. Raadpleeg voor meer informatie de sectie [Regenererende schema&#39;s](../../configuration/using/regenerating-schemas.md).
