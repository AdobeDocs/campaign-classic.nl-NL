---
product: campaign
title: Afmelden voor de verkoop van persoonlijke gegevens
description: Meer informatie over afmelden voor de verkoop van persoonsgegevens
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: 8e308a9f-14a4-4a25-9fd0-8d4bdbcf74ce
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '554'
ht-degree: 100%

---

# Opt-out voor de verkoop van persoonsgegevens (CCPA) {#sale-of-personal-information-ccpa}



De **California Consumer Privacy Act** (CCPA) biedt inwoners van Californië nieuwe rechten met betrekking tot hun persoonsgegevens en legt verantwoordelijkheden op het gebied van gegevensbescherming op aan bepaalde entiteiten die zaken doen in Californië.

De configuratie en het gebruik van verzoeken om toegang en verwijdering zijn hetzelfde voor de AVG en CCPA. In deze sectie wordt de opt-out voor de verkoop van persoonsgegevens beschreven, dit geldt specifiek voor de CCPA.

Naast de tools voor [toestemmingsbeheer](privacy-management.md#consent-management) die Adobe Campaign biedt, kunt u ook nagaan of een consument ervoor heeft gekozen om zich af te melden voor de verkoop van persoonsgegevens.

Contactpersonen kunnen via uw systeem besluiten dat hun persoonlijke gegevens niet aan derden mogen worden verkocht. In Adobe Campaign kunt u deze gegevens opslaan en volgen.

Dit werkt alleen als u de tabel met profielen uitbreidt en een veld **[!UICONTROL Opt-Out for CCPA]** toevoegt.

>[!IMPORTANT]
>
>Het is uw verantwoordelijkheid als gegevenscontroller om het verzoek van de betrokkene te ontvangen en de verzoekdatums voor de CCPA bij te houden. Als technologieleverancier bieden wij alleen een methode voor opt-out. Raadpleeg [Persoonsgegevens en persona&#39;s](privacy-and-recommendations.md#personal-data) voor meer informatie over uw rol als gegevenscontroller.

## Voorwaarde {#ccpa-prerequisite}

Als u deze informatie wilt gebruiken, moet u dit veld in Adobe Campaign Classic maken. Hiervoor voegt u een booleaans veld toe aan de tabel **[!UICONTROL Recipient]**. Wanneer een nieuw veld wordt gemaakt, wordt dit automatisch ondersteund door de Campaign-API.

Als u een aangepaste ontvangerstabel gebruikt, moet u deze bewerking ook uitvoeren.

Zie de [documentatie bij de Schema-editie](../../configuration/using/about-schema-edition.md) voor meer gedetailleerde informatie over het maken van een nieuw veld.

>[!IMPORTANT]
>
>Het aanpassen van schema&#39;s is een gevoelige bewerking die uitsluitend door deskundige gebruikers mag worden uitgevoerd.

1. Ga naar **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Add new fields]**, selecteer **[!UICONTROL Recipients]** als het **[!UICONTROL Document type]** en klik op **[!UICONTROL Next]**. Zie [deze sectie](../../configuration/using/new-field-wizard.md) voor meer informatie over het toevoegen van velden aan een tabel.

   ![](assets/privacy-ccpa-1.png)

1. Selecteer **[!UICONTROL SQL field]** voor het **[!UICONTROL Field type]**. Gebruik **[!UICONTROL Opt-Out for CCPA]** voor het label. Selecteer het type **[!UICONTROL 8-bit integer (boolean)]** en definieer het volgende unieke **[!UICONTROL Relative path]**: @OPTOUTCCPA. Klik op **[!UICONTROL Finish]**.

   ![](assets/privacy-ccpa-2.png)

   Hiermee wordt het schema **[!UICONTROL Recipient (cus)]** uitgebreid of gemaakt. Klik erop om te controleren of het veld correct is toegevoegd.

   ![](assets/privacy-ccpa-3.png)

1. Klik op de node **[!UICONTROL Configuration]** > **[!UICONTROL Input forms]** van de verkenner. Voeg bij **[!UICONTROL Recipient (nms)]** onder &#39;General Package&#39; een `<input>`-element toe en gebruik voor de xpath-waarde het relatieve pad dat in stap 2 is gedefinieerd. Zie [deze sectie](../../configuration/using/identifying-a-form.md) voor meer informatie over het identificeren van een formulier.

   ```
   <input  colspan="2" type="checkbox" xpath="@OPTOUTCCPA"/>
   ```

   ![](assets/privacy-ccpa-4.png)

1. Verbreek de verbinding en maak opnieuw verbinding. Voer de stappen uit die in de volgende sectie worden beschreven om te controleren of het veld beschikbaar is in de gegevens van een ontvanger.

## Gebruik {#usage}

Het is de verantwoordelijkheid van de gegevenscontroller om de waarde in het veld in te vullen en de CCPA-richtlijnen en -regels voor gegevensverkoop te volgen.

U kunt verschillende methoden gebruiken om de waarden in te vullen:

* De interface van Campaign gebruiken door de gegevens van de ontvanger te bewerken
* De API gebruiken
* Via een workflow voor het importeren van gegevens

Vervolgens moet u ervoor zorgen dat u de persoonsgegevens van profielen die zich hebben afgemeld nooit aan derden verkoopt.

1. Als u de opt-outstatus wilt wijzigen, gaat u naar **[!UICONTROL Profiles and Target]** > **[!UICONTROL Recipients]** en selecteert u een ontvanger. Op het tabblad **[!UICONTROL General]** ziet u het veld dat in de vorige sectie is geconfigureerd.

   ![](assets/privacy-ccpa-5.png)

1. Configureer de lijst met ontvangers om de opt-outkolom te tonen. Raadpleeg de [gedetailleerde documentatie](../../platform/using/adobe-campaign-workspace.md#configuring-lists) om te leren hoe u lijsten configureert.

   ![](assets/privacy-ccpa-6.png)

1. U kunt op de kolom klikken om ontvangers te sorteren op basis van de opt-outgegevens. U kunt ook een filter maken om alleen ontvangers te tonen die zich hebben afgemeld. Zie [deze sectie](../../platform/using/creating-filters.md) voor meer informatie over het maken van filters.

   ![](assets/privacy-ccpa-7.png)
