---
solution: Campaign Classic
product: campaign
title: Een webformulier publiceren
description: Een webformulier publiceren
audience: web
content-type: reference
topic-tags: web-forms
translation-type: tm+mt
source-git-commit: 21219f4a85a0caec4531acda33ab8bba5c7605d6
workflow-type: tm+mt
source-wordcount: '995'
ht-degree: 2%

---


# Een webformulier publiceren{#publishing-a-web-form}

## De formuliergegevens {#pre-loading-the-form-data} vooraf laden

Als u de profielen wilt bijwerken die in het gegevensbestand via een vorm van het Web worden opgeslagen, kunt u een preloading doos gebruiken. In het vak Voorladen kunt u aangeven hoe de record moet worden gevonden die in de database moet worden bijgewerkt.

De volgende identificatiemethoden zijn mogelijk:

* **[!UICONTROL Adobe Campaign Encryption]**

   Deze coderingsmethode gebruikt de gecodeerde Adobe Campaign-id (ID). Deze methode is alleen van toepassing op een Adobe Campaign-object en de gecodeerde id mag alleen worden gegenereerd door het Adobe Campaign-platform.

   Wanneer u deze methode gebruikt, moet u de URL van het formulier aanpassen om het e-mailadres te bereiken door de parameter **`<%=escapeUrl(recipient.cryptedId) %>`** toe te voegen. Raadpleeg [Formulieren verzenden via e-mail](#delivering-a-form-via-email) voor meer informatie.

* **[!UICONTROL DES encryption]**

   ![](assets/s_ncs_admin_survey_preload_methods_001.png)

   Deze encryptiemethode gebruikt een herkenningsteken (identiteitskaart) die extern wordt verstrekt, verbonden met een sleutel die door Adobe Campaign en de externe leverancier wordt gedeeld. In het veld **[!UICONTROL Des key]** kunt u deze coderingssleutel invoeren.

* **[!UICONTROL List of fields]**

   Met deze optie kunt u kiezen uit de velden in de huidige context van het formulier, de velden die worden gebruikt om het bijbehorende profiel in de database te zoeken.

   ![](assets/s_ncs_admin_survey_preload_methods_002.png)

   U kunt velden toevoegen aan de formuliereigenschappen via het tabblad **[!UICONTROL Parameters]** (zie [Parameters toevoegen](../../web/using/defining-web-forms-properties.md#adding-parameters)). Ze worden in de formulier-URL of invoerzones geplaatst.

   >[!CAUTION]
   >
   >De gegevens in de geselecteerde velden worden niet versleuteld. Deze mag niet in een versleutelde vorm worden aangeboden, omdat Adobe Campaign deze niet kan decoderen als de optie **[!UICONTROL Field list]** is geselecteerd.

   In het volgende voorbeeld wordt het vooraf laden van profielen gebaseerd op het e-mailadres.

   De URL kan het niet-gecodeerde e-mailadres bevatten. In dat geval hebben gebruikers rechtstreeks toegang tot de pagina&#39;s die hen aangaan.

   ![](assets/s_ncs_admin_survey_preload_methods_003.png)

   Als dat niet het geval is, worden ze om hun wachtwoord gevraagd.

   ![](assets/s_ncs_admin_survey_preload_methods_004.png)

   >[!CAUTION]
   >
   >Als de lijst meerdere velden bevat, moeten de gegevens van **ALLE VELDEN** overeenkomen met de gegevens die in de database zijn opgeslagen om het profiel te kunnen bijwerken. Anders wordt een nieuw profiel gemaakt.
   > 
   >Deze functie is vooral nuttig voor de toepassingen van het Web maar niet geadviseerd voor openbare vormen. De geselecteerde toegangsbeheeroptie moet &quot;toegangsbeheer&quot;toelaten zijn.

De optie **[!UICONTROL Skip preloading if no ID]** moet zijn geselecteerd als u geen profielen wilt bijwerken. In dat geval wordt elk ingevoerde profiel na goedkeuring van het formulier toegevoegd aan de database. Deze optie wordt bijvoorbeeld gebruikt wanneer het formulier op een website wordt geplaatst.

Met de optie **[!UICONTROL Auto-load data referenced in the form]** kunt u automatisch de gegevens laden die overeenkomen met de invoer- en samenvoegvelden in het formulier. Gegevens waarnaar wordt verwezen in **[!UICONTROL Script]**- en **[!UICONTROL Test]**-activiteiten, hebben echter geen betrekking. Als deze optie niet wordt geselecteerd, moet u de gebieden bepalen gebruikend de **[!UICONTROL Load additional data]** optie.

Met de optie **[!UICONTROL Load additional data]** kunt u informatie toevoegen die niet wordt gebruikt op de pagina&#39;s van het formulier, maar die wel vooraf wordt geladen.

U kunt bijvoorbeeld het geslacht van de ontvanger vooraf laden en hem of haar automatisch via een testvak naar de juiste pagina sturen.

![](assets/s_ncs_admin_survey_preload_ex.png)

## Levering en bijhouden van webformulieren beheren {#managing-web-forms-delivery-and-tracking}

Nadat het formulier is gemaakt, geconfigureerd en gepubliceerd, kunt u het verzenden en de reacties van gebruikers volgen.

### Levenscyclus van een formulier {#life-cycle-of-a-form}

Er zijn drie fasen in de levenscyclus van een formulier:

1. **Formulier wordt bewerkt**

   Dit is de eerste ontwerpfase. Wanneer een nieuw formulier wordt gemaakt, bevindt het zich in de bewerkingsfase. Toegang tot het formulier alleen voor testdoeleinden vereist dat de parameter **[!UICONTROL __uuid]** in de URL wordt gebruikt. Deze URL is toegankelijk op het subtabblad **[!UICONTROL Preview]**. Zie [Formulier-URL-parameters](../../web/using/defining-web-forms-properties.md#form-url-parameters).

   >[!CAUTION]
   >
   >Zolang het formulier wordt bewerkt, is de toegangs-URL een speciale URL.

1. **Formulier online**

   Nadat de ontwerpfase is voltooid, kan het formulier worden afgeleverd. Ten eerste moet het worden gepubliceerd. Raadpleeg [Een formulier publiceren](#publishing-a-form) voor meer informatie.

   Het formulier wordt **[!UICONTROL Live]** totdat het vervalt.

   >[!CAUTION]
   >
   >De URL van de enquête mag niet de parameter **[!UICONTROL __uuid]** bevatten.

1. **Formulier niet beschikbaar**

   Nadat het formulier is gesloten, is de leveringsfase voorbij en is het formulier niet meer beschikbaar: het is niet meer toegankelijk voor gebruikers.

   De vervaldatum kan worden gedefinieerd in het venster met formuliereigenschappen. Raadpleeg [Een formulier online beschikbaar maken](#making-a-form-available-online) voor meer informatie

De publicatiestatus van een formulier wordt weergegeven in de lijst met formulieren.

![](assets/s_ncs_admin_survey_status.png)

### Een formulier {#publishing-a-form} publiceren

Als u de status van een formulier wilt wijzigen, moet u het publiceren. Klik hiertoe op de knop **[!UICONTROL Publication]** boven de lijst met webformulieren en selecteer de status in de vervolgkeuzelijst.

![](assets/webapp_publish_webform.png)

### Een formulier online beschikbaar maken {#making-a-form-available-online}

Om door gebruikers te kunnen worden geraadpleegd, moet het formulier in productie zijn en worden gestart, d.w.z. binnen de geldigheidsperiode. De geldigheidsdata worden ingevoerd via de koppeling **[!UICONTROL Properties]** van het formulier.

* Gebruik de velden in de sectie **[!UICONTROL Project]** om begin- en einddatums voor het formulier in te voeren.

   ![](assets/webapp_availability_date.png)

* Klik op de koppeling **[!UICONTROL Personalize the message displayed if the form is closed...]** om het foutbericht te definiëren dat moet worden weergegeven als de gebruiker toegang probeert te krijgen tot het formulier terwijl het niet geldig is.

   Zie [Toegankelijkheid van het formulier](../../web/using/defining-web-forms-properties.md#accessibility-of-the-form).

### Een formulier verzenden via e-mail {#delivering-a-form-via-email}

Wanneer u een uitnodiging via e-mail verzendt, kunt u de optie **[!UICONTROL Adobe Campaign Encryption]** gebruiken voor het afstemmen van gegevens. Hiervoor gaat u naar de wizard voor levering en past u de koppeling naar het formulier aan door de volgende parameter toe te voegen:

```
<a href="https://server/webApp/APP264?&id=<%=escapeUrl(recipient.cryptedId) %>">
```

In dit geval moet de compatibiliteitssleutel voor gegevensopslag de gecodeerde id van de ontvanger zijn. Zie [De formuliergegevens vooraf laden](#pre-loading-the-form-data) voor meer informatie.

In dit geval moet u de optie **[!UICONTROL Update the preloaded record]** in het recordvak controleren. Voor meer op dit, verwijs naar [Het Opslaan van Web vormt antwoorden](../../web/using/web-forms-answers.md#saving-web-forms-answers).

![](assets/s_ncs_admin_survey_save_box_option.png)

### Logreacties {#log-responses}

Het volgen van de reactie kan in een specifiek lusje worden geactiveerd om het effect van uw vorm van het Web te controleren. Klik hiertoe op de koppeling **[!UICONTROL Advanced parameters...]** in het venster met formuliereigenschappen en selecteer de optie **[!UICONTROL Log responses]**.

![](assets/s_ncs_admin_survey_trace.png)

Op het tabblad **[!UICONTROL Responses]** kunt u de identiteit van de geënquêteerden weergeven.

![](assets/s_ncs_admin_survey_trace_tab.png)

Selecteer een ontvanger en klik op de knop **[!UICONTROL Detail...]** om de gegeven reacties weer te geven.

![](assets/s_ncs_admin_survey_trace_edit.png)

U kunt de antwoordlogboeken verwerken die in vragen worden verstrekt, bijvoorbeeld om slechts niet-geënquêteerden te richten wanneer het verzenden van herinneringen, of specifieke mededelingen aan slechts geënquêteerden aan te bieden.

>[!NOTE]
>
>Voor een volledig volgen van de verstrekte reacties, voer de reacties uit en bekijk of creeer specifieke rapporten, gebruik de facultatieve **Enquête** module. Raadpleeg [deze sectie](../../web/using/about-surveys.md) voor meer informatie.

