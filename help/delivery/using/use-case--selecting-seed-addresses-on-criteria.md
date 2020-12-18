---
solution: Campaign Classic
product: campaign
title: '"Gebruiksscenario: seed-adressen selecteren op criteria"'
description: '"Gebruiksscenario: seed-adressen selecteren op criteria"'
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '838'
ht-degree: 3%

---


# Gebruiksscenario: seed-adressen selecteren op criteria{#use-case-selecting-seed-addresses-on-criteria}

In het kader van een levering of een campagne, **[!UICONTROL Edit the dynamic condition...]** laat de verbinding u zaadadressen kiezen die op specifieke selectiecriteria worden gebaseerd.

In dit geval zou de site **Mijn onlinebibliotheek** de nieuwsbrieven willen personaliseren volgens de literaire smaak van de klant.

In samenwerking met de aankoopafdeling heeft de gebruiker die verantwoordelijk is voor de levering een nieuwsbrief gemaakt voor abonnees die politieromans hebben gekocht.

Om het definitieve resultaat van hun samenwerking met hen te delen, besluit de leveringsmanager om zijn collega&#39;s van de aankoopafdeling aan de levering als zaadadressen toe te voegen. Met een dynamische voorwaarde kunt u tijd besparen bij het configureren en bijwerken van adressen.

Als u de dynamische voorwaarde wilt gebruiken, moet u beschikken over:

* een levering klaar om te worden verzonden,
* zaadadressen die een gemeenschappelijke waarde hebben. Deze waarde kan een veld zijn dat al bestaat in Adobe Campaign. In dit voorbeeld hebben de zaadadressen dezelfde waarde als &quot;Aanschaffen&quot; in het veld &quot;Afdeling&quot;, die standaard niet in de toepassing aanwezig is.

## Stap 1 - het Creëren van een levering {#step-1---creating-a-delivery}

De stappen voor het maken van een levering worden beschreven in de sectie [Een e-maillevering maken](../../delivery/using/creating-an-email-delivery.md).

In dit voorbeeld heeft de leveringsmanager de nieuwsbrief gemaakt en de ontvangers geselecteerd.

![](assets/dlv_seeds_usecase_01.png)

## Stap 2 - het Creëren van een gemeenschappelijke waarde {#step-2---creating-a-common-value}

Als u een gemeenschappelijke waarde wilt maken zoals in ons voorbeeld (afdeling Aanschaffen), moet u eerst het **gegevensschema** van uw zaadadressen uitbreiden en het bijbehorende invoerformulier bewerken.

### Het gegevensschema {#extending-the-data-schema} uitbreiden

Voor meer details op schemauitbreidingen, verwijs naar [de gids van de Configuratie](../../configuration/using/data-schemas.md).

1. Klik in het knooppunt **[!UICONTROL Administration > Configuration > Data schemas]** op het pictogram **[!UICONTROL New]**.
1. Selecteer in het venster **[!UICONTROL Creation of a data schema]** de optie **[!UICONTROL Extension of a schema]** en klik op **[!UICONTROL Next]**.

   ![](assets/dlv_seeds_usecase_09.png)

1. Selecteer **[!UICONTROL Seed addresses]** bronschema, ga **doc** als **[!UICONTROL Namespace]** in en klik **[!UICONTROL Ok]**.

   ![](assets/dlv_seeds_usecase_10.png)

1. Klik op **[!UICONTROL Save]**.
1. Kopieer in het schemabewerkingsvenster de onderstaande regels en plak deze in het gebied dat in de schermafbeelding wordt aangegeven.

   ```
     <element name="common">
       <element label="Recipient" name="custom_nms_recipient">
         <attribute label="Department" length="80" name="workField" template="nms:recipient:recipient/@company"
                    type="string" userEnum="workField"/>
       </element>
     </element>
   ```

   ![](assets/dlv_seeds_usecase_20.png)

   Kopieer vervolgens de volgende regels en plak deze onder het element **[!UICONTROL Seed to insert in the export files]**.

   ```
       <element aggregate="doc:seedMember:common">
     </element>
   ```

   ![](assets/dlv_seeds_usecase_29.png)

   In dit geval, specificeert u dat een nieuwe opsomming genoemd **[!UICONTROL Department]** in de lijst van het zaadadres is gecreeerd, en het is gebaseerd op het standaard **[!UICONTROL @company]** opsommingsmalplaatje (geëtiketteerd onder de naam **Bedrijf** in de vorm van het zaadadres).

1. Klik op **[!UICONTROL Save]**.
1. Selecteer in het menu **[!UICONTROL Tools > Advanced]** de optie **[!UICONTROL Update database structure]**.

   ![](assets/dlv_seeds_usecase_12.png)

1. Wanneer de updatetovenaar wordt getoond, klik **[!UICONTROL Next]** knoop om tot het Edit venster van lijsten toegang te hebben: de veranderingen die in het schema van de zaadadresgegevens worden uitgevoerd vereisen een structuurupdate.

   ![](assets/dlv_seeds_usecase_13.png)

1. Volg de wizard totdat u naar de pagina komt om de update uit te voeren. Klik op de knop **[!UICONTROL Start]**.

   ![](assets/dlv_seeds_usecase_14.png)

   Nadat de update is voltooid, kunt u de wizard sluiten.

1. Verbinding verbreken en vervolgens opnieuw verbinding maken met Adobe Campaign. De veranderingen in het schema van de zaadadresgegevens worden aangebracht die zijn nu effectief. Om hen van het zaadadresscherm zichtbaar te zijn, moet u bijbehorende **[!UICONTROL Input form]** bijwerken. Raadpleeg de sectie [Invoerformulier bijwerken](#updating-the-input-form).

#### Het gegevensschema uitbreiden vanuit een gekoppelde tabel {#extending-the-data-schema-from-a-linked-table}

Het gegevensschema van de zaadadressen kan waarden van een lijst gebruiken verbonden aan het ontvankelijke gegevensschema - Ontvanger (nms).

Bijvoorbeeld, zou de gebruiker **[!UICONTROL Internet Extension]** in **[!UICONTROL Country]** lijst willen integreren die met het ontvanesschema verbonden is.

![](assets/dlv_seeds_usecase_06.png)

Daarom moeten zij het schema van de zaadadressen zoals die in de sectie worden gedetailleerd uitbreiden. De coderegels die in **stap 4** moeten worden geïntegreerd, zijn echter als volgt:

```
<element name="country">
      <attribute label="Internet Extension" length="2" name="iana" type="string"/>
      <attribute label="Country ISO" length="2" name="countryIsoA2" type="string"/>
    </element>
```

![](assets/dlv_seeds_usecase_11.png)

Zij geven aan:

* dat de gebruiker een nieuw element wil tot stand brengen genoemd **[!UICONTROL Internet Extension]**,
* dat dit element uit de **[!UICONTROL Country]** lijst komt.

>[!CAUTION]
>
>In de verbonden lijstnaam, moet u **xpath-dst** van genoemde verbonden lijst specificeren.
>
>Dit vindt u in het element **[!UICONTROL Country]** in de tabel met ontvangers.

![](assets/dlv_seeds_usecase_07.png)

De gebruiker kan dan uit **stap 5** van de sectie volgen, en **[!UICONTROL Input form]** van de zaadadressen bijwerken.

Raadpleeg de sectie [Invoerformulier bijwerken](#updating-the-input-form).

#### Invoerformulier {#updating-the-input-form} bijwerken

1. In **[!UICONTROL Administration > Configuration > Input forms]** knoop, vind de zaadadressen inputvorm.

   ![](assets/dlv_seeds_usecase_19.png)

1. Bewerk het formulier en voeg de volgende regel in de container **[!UICONTROL Recipient]** in.

   ```
   <input xpath="@workField"/>
   ```

   ![](assets/dlv_seeds_usecase_21.png)

1. Sla uw wijzigingen op.
1. Open een zaadadres. Het veld **[!UICONTROL Department]** wordt weergegeven in de tabel **[!UICONTROL Recipient]**.

   ![](assets/dlv_seeds_usecase_22.png)

1. Bewerk de zaadadressen die u voor de levering wilt gebruiken en typ **Aanschaf** als waarde in het veld **[!UICONTROL Department]**.

## Stap 3 - De voorwaarde {#step-3---defining-the-condition} bepalen

U kunt nu de dynamische voorwaarde van de zaadadressen voor de levering specificeren. Dit doet u als volgt:

1. Open een levering.

   ![](assets/dlv_seeds_usecase_01.png)

1. Klik op de koppeling **[!UICONTROL To]** en vervolgens op de tab **[!UICONTROL Seed addresses]** om de koppeling **[!UICONTROL Edit the dynamic condition...]** te openen.

   ![](assets/dlv_seeds_usecase_02.png)

1. Selecteer de uitdrukking die u de zaadadressen laat kiezen u wilt. Hier selecteert de gebruiker de expressie **[!UICONTROL Department (@workField)]**.

   ![](assets/dlv_seeds_usecase_03.png)

1. Selecteer de gewenste waarde. In dit voorbeeld selecteert de gebruiker de **Inkoopafdeling** in de vervolgkeuzelijst met waarden.

   ![](assets/dlv_seeds_usecase_17.png)

   >[!NOTE]
   >
   >De eerder gemaakte schema-extensie is afkomstig uit het schema **receiving**. De waarden die op het scherm hierboven worden getoond komen van een opsomming van het **ontvanger** schema.

1. Klik op **[!UICONTROL Ok]**.

   De query wordt weergegeven in het venster **[!UICONTROL Select target]**.

   ![](assets/dlv_seeds_usecase_04.png)

1. Klik **[!UICONTROL Ok]** om de vraag goed te keuren.
1. Analyseer uw levering dan klik op **[!UICONTROL Delivery]** lusje om tot de leveringslogboeken toegang te hebben.

   De zaadadressen van de aankoopafdeling worden getoond als hangende levering, enkel zoals die van de ontvangers of andere zaadadressen.

   ![](assets/dlv_seeds_usecase_05.png)

1. Klik op de knop **[!UICONTROL Send]** om de levering te starten.

   De leden van de aankoopafdeling maken deel uit van uw zaadadressen die de levering in hun e-mailpostvak zullen ontvangen.

   ![](assets/dlv_seeds_usecase_18.png)
