---
title: PII-weergave beperken
seo-title: PII-weergave beperken
description: PII-weergave beperken
seo-description: null
page-status-flag: never-activated
uuid: 4dddc7f5-dac3-47b3-b3cb-92b47eb595fa
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: editing-schemas
discoiquuid: 550439c1-978c-414e-be5b-a9e1a202c4cd
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# PII-weergave beperken{#restricting-pii-view}

## Overzicht {#overview}

Sommige klanten hebben marketinggebruikers nodig om toegang te krijgen tot gegevensrecords, maar willen niet dat ze PII (Personeel Identified Information), zoals voornaam, achternaam of e-mailadres, kunnen zien. Adobe Campaign stelt een manier voor om privacy te beschermen en te voorkomen dat gegevens worden misbruikt door reguliere campagnebedrijven.

## Implementatie {#implementation}

Een nieuw attribuut dat op om het even welk element of attribuut kan worden toegepast is toegevoegd aan de schema&#39;s, vult het bestaande attribuut aan **[!UICONTROL visibleIf]** . Dit kenmerk is: **[!UICONTROL accessibleIf]** . Als een XTK-expressie wordt opgenomen die gerelateerd is aan de huidige gebruikerscontext, kan deze bijvoorbeeld hefboomwerking **[!UICONTROL HasNamedRight]** of **[!UICONTROL $(login)]** .

U kunt een voorbeeld van een ontvankelijke schemauitbreiding vinden die dit gebruik hieronder toont:

```
<srcSchema desc="Recipient table (profiles" entitySchema="xtk:srcSchema" extendedSchema="nms:recipient"
           img="nms:recipient.png" label="Recipients" labelSingular="Recipient"
           name="recipient" namespace="sec" xtkschema="xtk:srcSchema">
  <element desc="Recipient table (profiles" img="nms:recipient.png" label="Recipients"
           labelSingular="Recipient" name="recipient">
    <attribute name="firstName" accessibleIf="$(login)=='admin'"/>
    <attribute name="lastName" visibleIf="$(login)=='admin'"/>
    <attribute name="email" accessibleIf="$(login)=='admin'"/>
  </element>
</srcSchema>
```

De belangrijkste eigenschappen zijn:

* **[!UICONTROL visibleIf]** : verbergt de gebieden van de meta-gegevens, zodat kunnen zij niet binnen een schemamening, kolomselectie, of een uitdrukkingsbouwer worden betreden. Maar dit verbergt geen gegevens, als de veldnaam handmatig wordt ingevoerd in een expressie, wordt de waarde weergegeven.
* **[!UICONTROL accessibleIf]** : Hiermee verbergt u de gegevens (en vervangt u deze door lege waarden) uit de resulterende query. Als visibleIf leeg is, krijgt het dezelfde expressie als **[!UICONTROL accessibleIf]** .

Hier volgen de gevolgen van het gebruik van dit kenmerk in Campagne:

* De gegevens zullen niet worden getoond gebruikend generische vraagredacteur in de console,
* Gegevens zijn niet zichtbaar in overzichtslijsten en recordlijst (console).
* Gegevens worden alleen-lezen in gedetailleerde weergave.
* Gegevens kunnen alleen worden gebruikt in filters (u kunt waarden toch raden met behulp van bepaalde dichotomiestrategieën).
* Om het even welke uitdrukking die gebruikend een beperkt gebied wordt gebouwd wordt beperkt tot: lower(@email) wordt even toegankelijk als @email.
* In een werkstroom kunt u de beperkte kolom aan de doelpopulatie toevoegen als een extra kolom van de overgang, maar deze is nog steeds niet toegankelijk voor Adobe-campagnegebruikers.
* Wanneer de doelpopulatie in een groep (lijst) wordt opgeslagen, zijn de kenmerken van de opgeslagen velden gelijk aan de gegevensbron.
* Gegevens zijn standaard niet toegankelijk voor JS-code.

## Aanbevelingen {#recommendations}

In elke levering worden e-mailadressen gekopieerd naar de **[!UICONTROL broadLog]** en de **[!UICONTROL forecastLog]** tabellen: bijgevolg moeten deze velden ook worden beschermd .

Hieronder ziet u een voorbeeld van de extensie van een logtabel voor het implementeren van deze extensie:

```
<srcSchema entitySchema="xtk:srcSchema" extendedSchema="nms:broadLogRcp" img="nms:broadLog.png"
           label="Recipient delivery logs" labelSingular="Recipient delivery log"
           name="broadLogRcp" namespace="sec" xtkschema="xtk:srcSchema">
  <element img="nms:broadLog.png" label="Recipient delivery logs" labelSingular="Recipient delivery log"
           name="broadLogRcp">
    <attribute accessibleIf="$(login)=='admin'" name="address"/>
  </element>
</srcSchema>
<srcSchema desc="Delivery messages being prepared." entitySchema="xtk:srcSchema"
           extendedSchema="nms:tmpBroadcast" img="" label="Messages being prepared"
           labelSingular="Message" name="tmpBroadcast" namespace="sec" xtkschema="xtk:srcSchema">
  <element desc="Delivery messages being prepared." label="Messages being prepared"
           labelSingular="Message" name="tmpBroadcast">
    <attribute accessibleIf="$(login)=='admin'" name="address"/>
  </element>
</srcSchema>
<srcSchema entitySchema="xtk:srcSchema" extendedSchema="nms:excludeLogRcp" img="nms:excludeLog.png"
           label="Recipient exclusion logs" labelSingular="Recipient exclusion log"
           name="excludeLogRcp" namespace="sec" xtkschema="xtk:srcSchema">
  <element img="nms:excludeLog.png" label="Recipient exclusion logs" labelSingular="Recipient exclusion log"
           name="excludeLogRcp">
    <attribute accessibleIf="$(login)=='admin'" name="address"/>
  </element>
</srcSchema>
```

>[!NOTE]
>
>Deze beperking geldt voor niet-technische gebruikers: een technische gebruiker , met de bijbehorende machtigingen , zal gegevens kunnen ophalen . Deze methode is dus niet 100% veilig.

