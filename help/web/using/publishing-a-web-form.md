---
product: campaign
title: Een webformulier publiceren
description: Een webformulier publiceren
badge-v8: label="Ook van toepassing op v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
feature: Web Forms
exl-id: 1c66b8e8-7590-4767-9b2f-a9a509df4508
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '1284'
ht-degree: 0%

---

# Een webformulier publiceren{#publishing-a-web-form}



## De formuliergegevens vooraf laden {#pre-loading-the-form-data}

Als u de profielen wilt bijwerken die in het gegevensbestand via een vorm van het Web worden opgeslagen, kunt u een preloading doos gebruiken. In het vak Voorladen kunt u aangeven hoe de record moet worden gevonden die in de database moet worden bijgewerkt.

De volgende identificatiemethoden zijn mogelijk:

* **[!UICONTROL Adobe Campaign Encryption]**

  Deze coderingsmethode gebruikt de gecodeerde Adobe Campaign-id (ID). Deze methode is alleen van toepassing op een Adobe Campaign-object en de gecodeerde id mag alleen worden gegenereerd door het Adobe Campaign-platform.

  Wanneer u deze methode gebruikt, moet u de URL van het formulier aanpassen om het e-mailadres te verzenden door de parameter **`<%=escapeUrl(recipient.cryptedId) %>`** toe te voegen. Voor meer op dit, verwijs naar [ Leverend een vorm via e-mail ](#delivering-a-form-via-email).

* **[!UICONTROL DES encryption]**

  ![](assets/s_ncs_admin_survey_preload_methods_001.png)

  Deze encryptiemethode gebruikt een herkenningsteken (identiteitskaart) die extern wordt verstrekt, verbonden met een sleutel die door Adobe Campaign en de externe leverancier wordt gedeeld. In het veld **[!UICONTROL Des key]** kunt u deze coderingssleutel invoeren.

* **[!UICONTROL List of fields]**

  Met deze optie kunt u kiezen uit de velden in de huidige context van het formulier, de velden die worden gebruikt om het bijbehorende profiel in de database te zoeken.

  ![](assets/s_ncs_admin_survey_preload_methods_002.png)

  De gebieden kunnen aan de vormeigenschappen via het **[!UICONTROL Parameters]** lusje worden toegevoegd (verwijs naar [ Toevoegende parameters ](defining-web-forms-properties.md#adding-parameters)). Ze worden in de formulier-URL of invoerzones geplaatst.

  >[!CAUTION]
  >
  >De gegevens in de geselecteerde velden worden niet versleuteld. Deze mag niet in een versleuteld formulier worden aangeboden, omdat Adobe Campaign deze niet kan decoderen als de optie **[!UICONTROL Field list]** is geselecteerd.

  In het volgende voorbeeld wordt het vooraf laden van profielen gebaseerd op het e-mailadres.

  De URL kan het niet-gecodeerde e-mailadres bevatten. In dat geval hebben gebruikers rechtstreeks toegang tot de pagina&#39;s die hen aangaan.

  ![](assets/s_ncs_admin_survey_preload_methods_003.png)

  Als dat niet het geval is, worden ze om hun wachtwoord gevraagd.

  ![](assets/s_ncs_admin_survey_preload_methods_004.png)

  >[!CAUTION]
  >
  >Als verscheidene gebieden in de lijst worden gespecificeerd, moeten de gegevens van **ALLE GEBIEDEN** de gegevens aanpassen die in het gegevensbestand worden opgeslagen opdat het profiel wordt bijgewerkt. Anders wordt een nieuw profiel gemaakt.
  > 
  >Deze functie is vooral nuttig voor de toepassingen van het Web maar niet geadviseerd voor openbare vormen. De geselecteerde toegangsbeheeroptie moet &quot;toegangsbeheer&quot;toelaten zijn.

U moet de optie **[!UICONTROL Skip preloading if no ID]** selecteren als u geen profielen wilt bijwerken. In dat geval wordt elk ingevoerde profiel na goedkeuring van het formulier toegevoegd aan de database. Deze optie wordt bijvoorbeeld gebruikt wanneer het formulier op een website wordt geplaatst.

Met de optie **[!UICONTROL Auto-load data referenced in the form]** kunt u automatisch de gegevens laden die overeenkomen met de invoer- en samenvoegvelden in het formulier. De gegevens waarnaar wordt verwezen in **[!UICONTROL Script]** - en **[!UICONTROL Test]** -activiteiten hebben echter geen betrekking. Als deze optie niet is geselecteerd, moet u de velden definiëren met de optie **[!UICONTROL Load additional data]** .

Met de optie **[!UICONTROL Load additional data]** kunt u informatie toevoegen die niet wordt gebruikt op de pagina&#39;s van het formulier, maar die wel vooraf wordt geladen.

U kunt bijvoorbeeld het geslacht van de ontvanger vooraf laden en deze automatisch via een testvak naar de juiste pagina sturen.

![](assets/s_ncs_admin_survey_preload_ex.png)

## Levering en bijhouden van webformulieren beheren {#managing-web-forms-delivery-and-tracking}

Nadat het formulier is gemaakt, geconfigureerd en gepubliceerd, kunt u het verzenden en de reacties van gebruikers volgen.

### Levenscyclus van een formulier {#life-cycle-of-a-form}

Er zijn drie fasen in de levenscyclus van een formulier:

1. **wordt uitgegeven**

   Dit is de eerste ontwerpfase. Wanneer een nieuw formulier wordt gemaakt, bevindt het zich in de bewerkingsfase. Toegang tot het formulier alleen voor testdoeleinden vereist dat de parameter **[!UICONTROL __uuid]** in de URL wordt gebruikt. Deze URL is toegankelijk op het subtabblad **[!UICONTROL Preview]** . Zie {de parameters van 0} Vorm URL [&#128279;](defining-web-forms-properties.md#form-url-parameters).

   >[!CAUTION]
   >
   >Zolang het formulier wordt bewerkt, is de toegangs-URL een speciale URL.

1. **Hangende publicatie**

   In sommige gevallen (zoals wanneer [ een vorm door een pakket ](#import-web-packages) invoert), kan een Webvorm de **[!UICONTROL Pending publication]** status hebben tot het levend is.

   >[!NOTE]
   >
   >Voor technische Webtoepassingen (beschikbaar door **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Web applications]** menu), is een vorm met de **[!UICONTROL Pending publication]** status automatisch [ gepubliceerd ](#publishing-a-form) en krijgt de **[!UICONTROL Online]** status.

1. **Online**

   Nadat de ontwerpfase is voltooid, kan het formulier worden afgeleverd.

   Wanneer een vorm **[!UICONTROL Being edited]** of **[!UICONTROL Pending publication]** status heeft, moet het [ worden gepubliceerd ](#publishing-a-form) om online en toegankelijk door Webvorm URL in browser te zijn.

   Nadat het formulier is gepubliceerd, blijft het actief tot het vervalt.

   Het formulier is **[!UICONTROL Live]** totdat het vervalt.

   >[!CAUTION]
   >
   >De URL van het formulier mag de parameter **[!UICONTROL __uuid]** niet bevatten om te worden verzonden.

1. **Gesloten**

   Nadat het formulier is gesloten, is de leveringsfase voorbij en is het formulier niet meer beschikbaar: het is niet meer toegankelijk voor gebruikers.

   De vervaldatum kan worden gedefinieerd in het venster met formuliereigenschappen. Voor meer op dit, verwijs naar [ Making een vorm online ](#making-a-form-available-online) beschikbaar.

De publicatiestatus van een formulier wordt weergegeven in de lijst met formulieren.

![](assets/s_ncs_admin_survey_status.png)

### Een formulier publiceren {#publishing-a-form}

Als u de status van een formulier wilt wijzigen, moet u het publiceren. Klik hiertoe op de knop **[!UICONTROL Publication]** boven de lijst met webformulieren en selecteer de status in de vervolgkeuzelijst.

![](assets/webapp_publish_webform.png)

### Een formulier online beschikbaar maken {#making-a-form-available-online}

Om door gebruikers te kunnen worden geraadpleegd, moet het formulier in productie zijn en worden gestart, d.w.z. binnen de geldigheidsperiode. De geldigheidsdatums worden ingevoerd via de koppeling **[!UICONTROL Properties]** van het formulier.

* Gebruik de velden in de sectie **[!UICONTROL Project]** om begin- en einddatums voor het formulier in te voeren.

  ![](assets/webapp_availability_date.png)

* Klik op de koppeling **[!UICONTROL Personalize the message displayed if the form is closed...]** om het foutbericht te definiëren dat moet worden weergegeven als de gebruiker toegang probeert te krijgen tot het formulier terwijl het niet geldig is.

  Zie [ Toegankelijkheid van de vorm ](defining-web-forms-properties.md#accessibility-of-the-form).

### Een formulier via e-mail verzenden {#delivering-a-form-via-email}

Wanneer u een uitnodiging via e-mail verzendt, kunt u de optie **[!UICONTROL Adobe Campaign Encryption]** gebruiken voor het afstemmen van gegevens. Om dit te doen, ga naar de leveringsmedewerker en pas de verbinding aan de vorm aan door de volgende parameter toe te voegen:

```
<a href="https://server/webApp/APP264?&id=<%=escapeUrl(recipient.cryptedId) %>">
```

In dit geval moet de compatibiliteitssleutel voor gegevensopslag de gecodeerde id van de ontvanger zijn. Voor meer op dit, verwijs naar [ pre-ladend de vormgegevens ](#pre-loading-the-form-data).

In dit geval moet u de optie **[!UICONTROL Update the preloaded record]** in het recordvak inschakelen. Voor meer op dit, verwijs naar [ het Opslaan van de vormen van het Web antwoorden ](web-forms-answers.md#saving-web-forms-answers).

![](assets/s_ncs_admin_survey_save_box_option.png)

### Antwoorden in logboek {#log-responses}

Het volgen van de reactie kan in een specifiek lusje worden geactiveerd om het effect van uw vorm van het Web te controleren. Klik hiertoe op de koppeling **[!UICONTROL Advanced parameters...]** in het venster met formuliereigenschappen en selecteer de optie **[!UICONTROL Log responses]** .

![](assets/s_ncs_admin_survey_trace.png)

Op het tabblad **[!UICONTROL Responses]** kunt u de identiteit van de geënquêteerden weergeven.

![](assets/s_ncs_admin_survey_trace_tab.png)

Selecteer een ontvanger en klik op de knop **[!UICONTROL Detail...]** om de antwoorden weer te geven.

![](assets/s_ncs_admin_survey_trace_edit.png)

U kunt de antwoordlogboeken verwerken die in vragen worden verstrekt, bijvoorbeeld om slechts niet-geënquêteerden te richten wanneer het verzenden van herinneringen, of specifieke mededelingen aan slechts geënquêteerden aan te bieden.

### Webformulierpakketten importeren {#import-web-packages}

Bij het exporteren en importeren van een pakket met een webformulier van een exemplaar naar een ander exemplaar (bijvoorbeeld van werkgebied naar productie), kan de status van het webformulier op het nieuwe exemplaar afhankelijk van verschillende omstandigheden variëren. De verschillende gevallen worden hieronder vermeld.

Leer meer op de verschillende statussen van een Webvorm in [ deze sectie ](#life-cycle-of-a-form).

>[!NOTE]
>
>Wanneer u een webformulier exporteert via een pakket, is de formulierstatus zichtbaar in de inhoud van het resulterende pakket.

* Als de status van het webformulier **[!UICONTROL Pending publication]** of **[!UICONTROL Online]** was bij het exporteren uit de eerste instantie:

   * Het webformulier krijgt de status **[!UICONTROL Pending publication]** wanneer het wordt geïmporteerd in het nieuwe exemplaar.

   * Als het webformulier al bestaat op het nieuwe exemplaar, wordt het vervangen door de nieuwe versie van het formulier en krijgt het de status **[!UICONTROL Pending publication]** , zelfs als de oude versie van het formulier **[!UICONTROL Online]** was.

   * Of de vorm al dan niet bestond, moet de vorm [ worden gepubliceerd ](#publishing-a-form) om **[!UICONTROL Online]** op de nieuwe instantie te worden en toegankelijk door Webvorm URL in browser.

* Als de status van het webformulier tijdens het exporteren **[!UICONTROL Being edited]** was:

   * Als het webformulier nieuw is op het exemplaar waar het pakket wordt geïmporteerd, krijgt het webformulier de status **[!UICONTROL Being edited]** .

   * Als het webformulier al bestaat op het nieuwe exemplaar, is dit een wijziging op een bestaand formulier. Als de oude versie van de vorm **[!UICONTROL Online]** was, blijft de oude versie online tot de nieuwe versie van de vorm [&#128279;](#publishing-a-form) opnieuw op de nieuwe instantie wordt gepubliceerd.

  >[!NOTE]
  >
  >U kunt de meest recente versie van uw webformulier controleren via het tabblad **[!UICONTROL Preview]** .

<!--For RN:
* Now, when a web form has the **Pending publication** status, it must be published before it becomes **Online** and accessible through the web form URL in a web browser. [Read more](../../web/using/publishing-a-web-form.md#life-cycle-of-a-form)
-->
