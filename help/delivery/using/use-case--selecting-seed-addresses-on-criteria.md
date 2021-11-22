---
product: campaign
title: '"Gebruiksscenario: seed-adressen selecteren op criteria"'
description: '"Gebruiksscenario: seed-adressen selecteren op criteria"'
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
exl-id: 091648b8-bf2d-4595-8be3-287f1ac48edd
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '838'
ht-degree: 3%

---

# Gebruiksscenario: seed-adressen selecteren op criteria{#use-case-selecting-seed-addresses-on-criteria}

![](../../assets/common.svg)

In het kader van een levering of een campagne **[!UICONTROL Edit the dynamic condition...]** met de koppeling kunt u zaadadressen kiezen op basis van specifieke selectiecriteria.

In dit geval, de plaats **Mijn onlinebibliotheek** wil haar nieuwsbrieven personaliseren volgens de literaire smaak van haar klanten .

In samenwerking met de aankoopafdeling heeft de gebruiker die verantwoordelijk is voor de levering een nieuwsbrief gemaakt voor abonnees die politieromans hebben gekocht.

Om het definitieve resultaat van hun samenwerking met hen te delen, besluit de leveringsmanager om zijn collega&#39;s van de aankoopafdeling aan de levering als zaadadressen toe te voegen. Met een dynamische voorwaarde kunt u tijd besparen bij het configureren en bijwerken van adressen.

Als u de dynamische voorwaarde wilt gebruiken, moet u beschikken over:

* een levering klaar om te worden verzonden,
* zaadadressen die een gemeenschappelijke waarde hebben. Deze waarde kan een veld zijn dat al bestaat in Adobe Campaign. In dit voorbeeld hebben de zaadadressen dezelfde waarde als &quot;Aanschaffen&quot; in het veld &quot;Afdeling&quot;, die standaard niet in de toepassing aanwezig is.

## Stap 1 - Een levering maken {#step-1---creating-a-delivery}

De stappen voor het maken van een levering worden beschreven in het dialoogvenster [Een e-maillevering maken](creating-an-email-delivery.md) sectie.

In dit voorbeeld heeft de leveringsmanager de nieuwsbrief gemaakt en de ontvangers geselecteerd.

![](assets/dlv_seeds_usecase_01.png)

## Stap 2 - Een gemeenschappelijke waarde maken {#step-2---creating-a-common-value}

Als u een gemeenschappelijke waarde wilt maken, zoals in ons voorbeeld (afdeling Aanschaffen), moet u eerst het dialoogvenster **gegevensschema** van uw zaadadressen en geef het bijbehorende inputformulier uit.

### Het gegevensschema uitbreiden {#extending-the-data-schema}

Raadpleeg voor meer informatie over schema-extensies de [Configuratiegids](../../configuration/using/data-schemas.md).

1. In de **[!UICONTROL Administration > Configuration > Data schemas]** knoop, klik **[!UICONTROL New]** pictogram.
1. In de **[!UICONTROL Creation of a data schema]** venster, selecteert u de **[!UICONTROL Extension of a schema]** en klik op **[!UICONTROL Next]**.

   ![](assets/dlv_seeds_usecase_09.png)

1. Selecteer **[!UICONTROL Seed addresses]** bronschema, voer **doc** als de **[!UICONTROL Namespace]** en klik op **[!UICONTROL Ok]**.

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

   Kopieer vervolgens de volgende regels en plak deze onder de **[!UICONTROL Seed to insert in the export files]** element.

   ```
       <element aggregate="doc:seedMember:common">
     </element>
   ```

   ![](assets/dlv_seeds_usecase_29.png)

   In dit geval geeft u op dat een nieuwe opsomming met de naam **[!UICONTROL Department]** is gecreeerd in de lijst van het zaadadres, en het is gebaseerd op de norm **[!UICONTROL @company]** opsommingssjabloon (gelabeld onder de naam **Bedrijf** in het zaadadresformulier).

1. Klik op **[!UICONTROL Save]**.
1. In de **[!UICONTROL Tools > Advanced]** selecteert u de **[!UICONTROL Update database structure]** optie.

   ![](assets/dlv_seeds_usecase_12.png)

1. Klik op de knop **[!UICONTROL Next]** om het venster Tabellen bewerken te openen: de veranderingen die in het schema van de zaadadresgegevens worden uitgevoerd vereisen een structuurupdate.

   ![](assets/dlv_seeds_usecase_13.png)

1. Volg de wizard totdat u naar de pagina komt om de update uit te voeren. Klik op de knop **[!UICONTROL Start]**.

   ![](assets/dlv_seeds_usecase_14.png)

   Nadat de update is voltooid, kunt u de wizard sluiten.

1. Verbinding verbreken en vervolgens opnieuw verbinding maken met Adobe Campaign. De veranderingen in het schema van de zaadadresgegevens worden aangebracht die zijn nu effectief. Om hen van het scherm van het zaadadres zichtbaar te zijn, moet u bijbehorende bijwerken **[!UICONTROL Input form]**. Zie de [Het invoerformulier bijwerken](#updating-the-input-form) sectie.

#### Het gegevensschema uitbreiden vanuit een gekoppelde tabel {#extending-the-data-schema-from-a-linked-table}

Het gegevensschema van de zaadadressen kan waarden van een lijst gebruiken verbonden aan het ontvankelijke gegevensschema - Ontvanger (nms).

De gebruiker wil bijvoorbeeld de **[!UICONTROL Internet Extension]** gevonden in het dialoogvenster **[!UICONTROL Country]** tabel die is gekoppeld aan het schema van ontvangers.

![](assets/dlv_seeds_usecase_06.png)

Daarom moeten zij het schema van de zaadadressen zoals die in de sectie worden gedetailleerd uitbreiden. De coderegels die moeten worden geïntegreerd in **stap 4** zijn als volgt:

```
<element name="country">
      <attribute label="Internet Extension" length="2" name="iana" type="string"/>
      <attribute label="Country ISO" length="2" name="countryIsoA2" type="string"/>
    </element>
```

![](assets/dlv_seeds_usecase_11.png)

Zij geven aan:

* dat de gebruiker een nieuw element met de naam **[!UICONTROL Internet Extension]**,
* dat dit element afkomstig is van **[!UICONTROL Country]** tabel.

>[!CAUTION]
>
>In de naam van de gekoppelde tabel moet u de instelling **xpath-dst** van genoemde gekoppelde tabel.
>
>Dit vindt u in het gedeelte **[!UICONTROL Country]** -element in de tabel met ontvangers.

![](assets/dlv_seeds_usecase_07.png)

De gebruiker kan dan volgen uit **stap 5** van de sectie en werk de **[!UICONTROL Input form]** van het zaadadres.

Zie de [Het invoerformulier bijwerken](#updating-the-input-form) sectie.

#### Het invoerformulier bijwerken {#updating-the-input-form}

1. In de **[!UICONTROL Administration > Configuration > Input forms]** -knooppunt, zoekt u het invoerformulier voor zaadadressen.

   ![](assets/dlv_seeds_usecase_19.png)

1. Bewerk het formulier en voeg de volgende regel in het dialoogvenster **[!UICONTROL Recipient]** container.

   ```
   <input xpath="@workField"/>
   ```

   ![](assets/dlv_seeds_usecase_21.png)

1. Sla uw wijzigingen op.
1. Open een zaadadres. De **[!UICONTROL Department]** wordt weergegeven in het **[!UICONTROL Recipient]** tabel.

   ![](assets/dlv_seeds_usecase_22.png)

1. Bewerk de zaadadressen die u voor de levering wilt gebruiken en voer deze in **Aankoop** als de waarde in de **[!UICONTROL Department]** veld.

## Stap 3 - De voorwaarde definiëren {#step-3---defining-the-condition}

U kunt nu de dynamische voorwaarde van de zaadadressen voor de levering specificeren. Dit doet u als volgt:

1. Open een levering.

   ![](assets/dlv_seeds_usecase_01.png)

1. Klik op de knop **[!UICONTROL To]** dan de koppeling **[!UICONTROL Seed addresses]** tabblad om toegang te krijgen tot de **[!UICONTROL Edit the dynamic condition...]** koppeling.

   ![](assets/dlv_seeds_usecase_02.png)

1. Selecteer de uitdrukking die u de zaadadressen laat kiezen u wilt. Hier selecteert de gebruiker de **[!UICONTROL Department (@workField)]** expressie.

   ![](assets/dlv_seeds_usecase_03.png)

1. Selecteer de gewenste waarde. In dit voorbeeld selecteert de gebruiker de optie **Aankoop** van de vervolgkeuzelijst met waarden.

   ![](assets/dlv_seeds_usecase_17.png)

   >[!NOTE]
   >
   >De eerder gemaakte schema-extensie is afkomstig van de **ontvanger** schema. De waarden die op het bovenstaande scherm worden weergegeven, zijn afkomstig van een opsomming van de **ontvanger** schema.

1. Klik op **[!UICONTROL Ok]**.

   De query wordt weergegeven in het dialoogvenster **[!UICONTROL Select target]** venster.

   ![](assets/dlv_seeds_usecase_04.png)

1. Klikken **[!UICONTROL Ok]** om de query goed te keuren.
1. Analyseer uw levering en klik op **[!UICONTROL Delivery]** voor toegang tot de leveringslogboeken.

   De zaadadressen van de aankoopafdeling worden getoond als hangende levering, enkel zoals die van de ontvangers of andere zaadadressen.

   ![](assets/dlv_seeds_usecase_05.png)

1. Klik op de knop **[!UICONTROL Send]** om de levering te starten.

   De leden van de aankoopafdeling maken deel uit van uw zaadadressen die de levering in hun e-mailpostvak zullen ontvangen.

   ![](assets/dlv_seeds_usecase_18.png)
