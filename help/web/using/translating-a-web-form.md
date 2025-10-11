---
product: campaign
title: Een webformulier vertalen
description: Een webformulier vertalen
badge-v8: label="Ook van toepassing op v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
feature: Web Forms
exl-id: 72959141-ca18-4512-80c7-239efd31f711
source-git-commit: 8817b485fd5b6d6aeb9d71c1106f16fbb6bc3c5b
workflow-type: tm+mt
source-wordcount: '1549'
ht-degree: 0%

---

# Een webformulier vertalen{#translating-a-web-form}



Het is mogelijk om een toepassing van het Web in verscheidene talen te lokaliseren.

U kunt vertalingen direct in de console van Adobe Campaign uitvoeren (verwijs naar [&#x200B; het Leiden vertalingen in de redacteur &#x200B;](#managing-translations-in-the-editor)), of koorden uitvoeren en invoeren om vertaling (verwijs naar [&#x200B; het Buiten*stellen vertaling &#x200B;](#externalizing-translation)) te externaliseren.

De lijst van vertaaltalen beschikbaar door gebrek is gedetailleerd in [&#x200B; Veranderende de taal van de vormenvertoning &#x200B;](#changing-forms-display-language).

De toepassing van het Web wordt ontworpen in een het uitgeven taal: dit is de verwijzingstaal die wordt gebruikt om etiketten en andere te vertalen inhoud in te gaan.

De standaardtaal is de taal waarin de toepassing van het Web zal worden getoond als geen taal het plaatsen aan zijn toegang URL wordt toegevoegd.

>[!NOTE]
>
>Door gebrek, zijn de het uitgeven taal en de standaardtaal het zelfde als de consoletaal.

## Talen kiezen {#choosing-languages}

Als u een of meer vertaaltalen wilt definiëren, klikt u op de knop **[!UICONTROL Properties]** van de webtoepassing en vervolgens op de tab **[!UICONTROL Localization]** . Klik op de knop **[!UICONTROL Add]** om een nieuwe vertaaltaal voor de webtoepassing te definiëren.

>[!NOTE]
>
>In dit venster kunt u ook de standaardtaal en de bewerkingstaal wijzigen.

![](assets/s_ncs_admin_survey_add_lang.png)

Wanneer u vertaaltalen toevoegt voor een webtoepassing (of wanneer de standaardtaal en de bewerkingstaal verschillend zijn), wordt een subtabblad **[!UICONTROL Translation]** toegevoegd aan het tabblad **[!UICONTROL Edit]** voor het beheren van vertalingen.

Adobe Campaign beschikt over een instrument voor het vertalen en beheren van meertalige vertalingen. In deze editor kunt u de tekenreeksen bekijken die u wilt vertalen of goedkeuren, vertalingen rechtstreeks in de interface invoeren of tekenreeksen importeren/exporteren om vertalingen te externaliseren.

## Vertalingen beheren in de editor {#managing-translations-in-the-editor}

### Tekenreeksen verzamelen {#collecting-strings}

Op het tabblad **[!UICONTROL Translations]** kunt u vertalingen invoeren voor de tekenreeksen die de webtoepassing vormen.

De eerste keer dat u dit tabblad opent, bevat dit tabblad geen gegevens. Klik op de koppeling **[!UICONTROL Collect the strings to translate]** om de tekenreeksen in de webtoepassing bij te werken.

Adobe Campaign verzamelt labels van velden en tekenreeksen die zijn gedefinieerd op de tabbladen **[!UICONTROL Texts]** van alle statische elementen: HTML-blokken, JavaScript, enzovoort. De statische elementen worden gedetailleerd in [&#x200B; Statische elementen in een Webvorm &#x200B;](static-elements-in-a-web-form.md).

![](assets/s_ncs_admin_survey_trad_tab.png)

>[!CAUTION]
>
>Dit proces kan enkele minuten duren, afhankelijk van het volume gegevens dat moet worden verwerkt.
> 
>Als een waarschuwing lijkt te zeggen dat sommige vertalingen in het systeemwoordenboek ontbreken, verwijs naar [&#x200B; Vertaal de systeemkoorden &#x200B;](#translating-the-system-strings).

Elke keer dat een tekenreeks wordt vertaald, wordt de vertaling ervan toegevoegd aan het vertaalwoordenboek.

Wanneer tijdens het verzamelingsproces wordt vastgesteld dat er al een vertaling bestaat, wordt deze vertaling weergegeven in de kolom **[!UICONTROL Text]** van de tekenreeks. De status van de tekenreeks wordt gewijzigd in **[!UICONTROL Translated]** .

Voor tekenreeksen die nog niet zijn omgezet, is het veld **[!UICONTROL Text]** leeg en is de status **[!UICONTROL To translate]** .

### Tekenreeksen filteren {#filtering-strings}

Door gebrek, wordt elke vertaaltaal van de toepassing van het Web getoond. Er zijn twee standaardfilters: taal en status. Klik op de knop **[!UICONTROL Filters]** en klik vervolgens op **[!UICONTROL By language or status]** om de overeenkomende vervolgkeuzelijsten weer te geven. U kunt ook een geavanceerd filter maken. Voor meer informatie over filters, verwijs naar de [&#x200B; Campagne v8 (console) documentatie &#x200B;](https://experienceleague.adobe.com/nl/docs/campaign/campaign-v8/audience/create-filters){target=_blank}.

![](assets/s_ncs_admin_survey_trad_tab_en.png)

Ga naar de vervolgkeuzelijst **[!UICONTROL Language]** om de vertaaltaal te selecteren.

Als u alleen onvertaalde tekenreeksen wilt weergeven, selecteert u **[!UICONTROL To translate]** in de vervolgkeuzelijst **[!UICONTROL Status]** . U kunt ook alleen vertaalde of goedgekeurde tekenreeksen weergeven.

### Tekenreeksen omzetten {#translating-strings}

1. Als u een woord wilt vertalen, dubbelklikt u op de desbetreffende regel in de lijst met tekenreeksen.

   ![](assets/s_ncs_admin_survey_trad_tab_add_term.png)

   De brontekenreeks wordt weergegeven in de bovenste sectie van het venster.

1. Voer de vertaling in de onderste sectie in. Schakel de optie **[!UICONTROL Translation approved]** in om deze goed te keuren.

   >[!NOTE]
   >
   >Goedkeuring van vertaling is optioneel en blokkeert het proces niet.

   Niet-goedgekeurde vertalingen worden weergegeven als **[!UICONTROL Translated]** . Goedgekeurde vertalingen worden weergegeven als **[!UICONTROL Approved]** .

## Externe vertaling {#externalizing-translation}

Het is mogelijk tekenreeksen te exporteren en te importeren om deze te vertalen met een ander gereedschap dan Adobe Campaign.

>[!CAUTION]
>
>Nadat u de tekenreeksen hebt geëxporteerd, hoeft u geen vertalingen meer uit te voeren met het geïntegreerde gereedschap. Dit zou tot een conflict leiden wanneer u de vertalingen opnieuw invoert en deze zullen verloren gaan.

### Bestanden exporteren {#exporting-files}

1. Selecteer de webtoepassing(en) waarvan u de tekenreeksen wilt exporteren, klik met de rechtermuisknop en selecteer vervolgens **[!UICONTROL Actions > Export strings for translation...]**

   ![](assets/s_ncs_admin_survey_trad_export.png)

1. Selecteer een **[!UICONTROL Export strategy]** :

   * **[!UICONTROL One file per language]** : bij het exporteren wordt één bestand per vertaaltaal gegenereerd. Elk dossier zal voor alle geselecteerde toepassingen van het Web gemeenschappelijk zijn.
   * **[!UICONTROL One file per Web application]** : bij het exporteren wordt één bestand per geselecteerde webtoepassing gegenereerd. Elk bestand bevat alle vertaaltalen.

     >[!NOTE]
     >
     >Dit type export is niet beschikbaar voor XLIFF-export.

   * **[!UICONTROL One file per language and per Web application]** : tijdens het exporteren worden meerdere bestanden gegenereerd. Elk dossier zal één vertaaltaal per toepassing van het Web bevatten.
   * **[!UICONTROL One file for all]** : tijdens het exporteren wordt één meertalig bestand voor alle webtoepassingen gegenereerd. Het zal alle vertaaltalen voor alle geselecteerde toepassingen van het Web bevatten.

     >[!NOTE]
     >
     >Dit type export is niet beschikbaar voor XLIFF-export.

1. Kies vervolgens de locatie **[!UICONTROL Target folder]** waar de bestanden worden opgenomen.
1. Selecteer de bestandsindeling **[!UICONTROL CSV]** of **[!UICONTROL XLIFF]** en klik op **[!UICONTROL Start]** .

![](assets/s_ncs_admin_survey_trad_export_start.png)

>[!NOTE]
>
>De namen van exportbestanden worden automatisch gegenereerd. Als u dezelfde exportbewerking meerdere malen uitvoert, vervangt u bestaande bestanden door de nieuwe bestanden. Als u de vorige bestanden wilt behouden, wijzigt u **[!UICONTROL Target folder]** en klikt u nogmaals op **[!UICONTROL Start]** om het exporteren uit te voeren.

Wanneer u dossiers in **formaat CSV** uitvoert, is elke taal verbonden met een status en goedkeuringsstatus. **goedkeuren?Met de kolom** kunt u een vertaling goedkeuren. Deze kolom kan de waarden **ja** of **Nr** bevatten. Zoals voor de geïntegreerde redacteur (verwijs naar [&#x200B; het Leiden vertalingen in de redacteur &#x200B;](#managing-translations-in-the-editor)), is het goedkeuren van vertalingen facultatief en blokkeert niet het proces.

### Bestanden importeren {#importing-files}

Nadat de externe vertaling is voltooid, kunt u de vertaalde bestanden importeren.

1. Ga naar de lijst met webtoepassingen, klik met de rechtermuisknop en selecteer vervolgens **[!UICONTROL Actions > Import translated strings...]**

   >[!NOTE]
   >
   >Het is niet nodig om de webtoepassingen te selecteren waarop de vertaling betrekking heeft. Plaats overal de curseur op de lijst van de toepassingen van het Web.

   ![](assets/s_ncs_admin_survey_trad_import.png)

1. Selecteer het bestand dat u wilt importeren en klik op **[!UICONTROL Upload]** .

   ![](assets/s_ncs_admin_survey_trad_import_start.png)

>[!NOTE]
>
>Externe vertalingen hebben altijd voorrang op interne vertalingen. In geval van conflicten wordt de interne vertaling overschreven door de externe vertaling.

## Weergavetaal van formulieren wijzigen {#changing-forms-display-language}

Webformulieren worden weergegeven in de standaardtaal die is opgegeven op het tabblad **[!UICONTROL Localization]** van de eigenschappen van de webtoepassing. Om talen te veranderen, moet u de volgende karakters aan het eind van URL (waar **xx** het symbool van de taal is) toevoegen:

```
?lang=xx
```

als de taal de eerste of enige parameter van de URL is. Bijvoorbeeld: **https://myserver/webApp/APP34**

```
&lang=xx
```

als er andere parameters zijn vóór de taal in de URL. Bijvoorbeeld: **https://myserver/webApp/APP34?status=1&lang=en**

De vertalingstalen en woordenboeken die standaard beschikbaar zijn, worden hieronder weergegeven.

**Standaard systeemwoordenboek**: sommige talen omvatten een standaardwoordenboek dat de vertaling van de systeemkoorden bevat. Voor meer op dit, verwijs naar [&#x200B; Vertaal de systeemkoorden &#x200B;](#translating-the-system-strings).

**het beheer van de Kalender**: de pagina&#39;s van een toepassing van het Web kunnen een kalender omvatten om data in te gaan. Deze kalender is standaard beschikbaar in verschillende talen (vertaling van dagen, datumnotatie).

<table> 
 <tbody> 
  <tr> 
   <td> <strong> Taal (symbolen) </strong><br /> </td> 
   <td> <strong> Standaard systeemwoordenboek </strong><br /> </td> 
   <td> <strong> het beheer van de Kalender </strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Duits (de) <br /> </td> 
   <td> yes<br /> </td> 
   <td> yes<br /> </td> 
  </tr> 
  <tr> 
   <td> Engels (en) <br /> </td> 
   <td> yes<br /> </td> 
   <td> yes<br /> </td> 
  </tr> 
  <tr> 
   <td> Engels (Verenigde Staten) (en_US) <br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Engels (Verenigd Koninkrijk) (en_GB) <br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Arabisch (ar) <br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Chinees (zh) <br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Koreaans (ko) <br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Deens (da) <br /> </td> 
   <td> yes<br /> </td> 
   <td> yes<br /> </td> 
  </tr> 
  <tr> 
   <td> Spaans (es) <br /> </td> 
   <td> yes<br /> </td> 
   <td> yes<br /> </td> 
  </tr> 
  <tr> 
   <td> Ests (et) <br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Fins (fi) <br /> </td> 
   <td> </td> 
   <td> yes<br /> </td> 
  </tr> 
  <tr> 
   <td> Frans (fr) <br /> </td> 
   <td> yes<br /> </td> 
   <td> yes<br /> </td> 
  </tr> 
  <tr> 
   <td> Frans (Belgium) (fr_BE) <br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Frans (Frankrijk) (fr_FR) <br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Grieks (el) <br /> </td> 
   <td> </td> 
   <td> yes<br /> </td> 
  </tr> 
  <tr> 
   <td> Hebreeuws (hij) <br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Hongaars (hu) <br /> </td> 
   <td> </td> 
   <td> yes<br /> </td> 
  </tr> 
  <tr> 
   <td> Indonesisch (id) <br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Iers (ga) <br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Italiaans (it) <br /> </td> 
   <td> yes<br /> </td> 
   <td> yes<br /> </td> 
  </tr> 
  <tr> 
   <td> Italiaans (Italië) (it_IT) <br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Italiaans (Zwitsers) (it_CH) <br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Japans (ja) <br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Lets (lv) <br /> </td> 
   <td> </td> 
   <td> yes<br /> </td> 
  </tr> 
  <tr> 
   <td> Litouws (lt) <br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Maltees (mt) <br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Nederlands (nl) <br /> </td> 
   <td> </td> 
   <td> yes<br /> </td> 
  </tr> 
  <tr> 
   <td> Nederlands (België) (nl_BE) <br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Nederlands (Nederland) (nl_NL) <br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Noors (Noorwegen) (no_NO) <br /> </td> 
   <td> </td> 
   <td> yes<br /> </td> 
  </tr> 
  <tr> 
   <td> Pools (pl) <br /> </td> 
   <td> </td> 
   <td> yes<br /> </td> 
  </tr> 
  <tr> 
   <td> Portugees (pt) <br /> </td> 
   <td> </td> 
   <td> yes<br /> </td> 
  </tr> 
  <tr> 
   <td> Portugees (Brazilië) (pt_BR) <br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Portugees (Portugal) (pt_PT) <br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Russisch (ru) <br /> </td> 
   <td> </td> 
   <td> yes<br /> </td> 
  </tr> 
  <tr> 
   <td> Sloveens (sl) <br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Slowaaks (sk) <br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Zweeds (sv) <br /> </td> 
   <td> yes<br /> </td> 
   <td> yes<br /> </td> 
  </tr> 
  <tr> 
   <td> Zweeds (Finland) (sv_FI) <br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Zweeds (Zweden) (sv_SE) <br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Tsjechisch (cs) <br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Thai (th) <br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Vietnamees (vi) <br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Walen (wa) <br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Om andere talen toe te voegen dan die door gebrek worden aangeboden, verwijs naar [&#x200B; Toevoegend een vertaaltaal &#x200B;](#adding-a-translation-language)

## Voorbeeld: een webtoepassing weergeven in verschillende talen {#example--displaying-a-web-application-in-several-languages}

Het volgende webformulier is beschikbaar in vier talen: Engels, Frans, Duits en Spaans. De tekenreeksen zijn allemaal omgezet via het tabblad **[!UICONTROL Translation]** van het webformulier. Omdat de standaardtaal Engels is, gebruikt u bij het publiceren van de enquête de standaard-URL om deze in het Engels weer te geven.

![](assets/s_ncs_admin_survey_trad_sample_fr.png)

Voeg **toe?lang=fr** aan het eind van URL om het in het Frans te tonen:

>[!NOTE]
>
>De lijst van symbolen voor elke taal wordt gedetailleerd in [&#x200B; Veranderende de taal van de vormenvertoning &#x200B;](#changing-forms-display-language).

![](assets/s_ncs_admin_survey_trad_sample_en.png)

U kunt **toevoegen?lang=es** of **?lang=de** om het in Spaans of Duits te tonen.

>[!NOTE]
>
>Als andere parameters al voor deze toepassing van Web worden gebruikt, voeg **&amp;lang=** toe.\
>Bijvoorbeeld: **https://myserver/webApp/APP34?status=1&lang=en**

## Geavanceerde vertaalconfiguratie {#advanced-translation-configuration}

>[!CAUTION]
>
>Deze sectie is alleen bedoeld voor ervaren gebruikers.

### De systeemtekenreeksen omzetten {#translating-the-system-strings}

De koorden van het systeem zijn uit-van-de-doos karakterkoorden die door alle toepassingen van het Web worden gebruikt. Bijvoorbeeld: **[!UICONTROL Next]** , **[!UICONTROL Previous]** , **[!UICONTROL Approve]** knoppen, **[!UICONTROL Loading]** berichten, enzovoort. Standaard bevatten sommige talen een woordenboek met vertalingen voor deze tekenreeksen. De lijst van talen wordt gedetailleerd in [&#x200B; Veranderende de taal van de vormenvertoning &#x200B;](#changing-forms-display-language).

Als u uw toepassing van het Web in een taal vertaalt waarvoor het systeemwoordenboek niet wordt vertaald, zal een waarschuwingsbericht schijnen om u te laten weten dat sommige vertalingen ontbreken.

![](assets/s_ncs_admin_survey_trad_error.png)

Voer de volgende stappen uit om een taal toe te voegen:

1. Ga naar de Adobe Campaign-structuur en klik op **[!UICONTROL Administration > Configuration > Global dictionary > System dictionary]** .
1. Selecteer in de bovenste sectie van het venster de systeemtekenreeks die u wilt vertalen en klik vervolgens op **[!UICONTROL Add]** in de onderste sectie.

   ![](assets/s_ncs_admin_survey_trad_system_translation.png)

1. Selecteer de vertaaltaal en voer een vertaling voor de tekenreeks in. U kunt de vertaling goedkeuren door de optie **[!UICONTROL Translation approved]** te controleren.

   ![](assets/s_ncs_admin_survey_trad_system_translation2.png)

   >[!NOTE]
   >
   >Goedkeuring van vertaling is optioneel en blokkeert het proces niet.

>[!CAUTION]
>
>Verwijder niet de uit-van-de-doos systeemkoorden.

### Een vertaaltaal toevoegen {#adding-a-translation-language}

Om de toepassingen van het Web in talen buiten standaarddegenen (verwijs naar [&#x200B; Veranderende de taal van de vormenvertoning &#x200B;](#changing-forms-display-language)) te vertalen, zult u een nieuwe vertaaltaal moeten toevoegen.

1. Klik op het knooppunt **[!UICONTROL Administration > Platform > Enumerations]** van de Adobe Campaign-structuur en selecteer **[!UICONTROL Languages available for translation]** in de lijst. De lijst met beschikbare vertalingen wordt weergegeven in de onderste sectie van het venster.

   ![](assets/s_ncs_admin_survey_trad_new_itemized_list_1.png)

1. Klik op de knop **[!UICONTROL Add]** en voer vervolgens de markeringen **[!UICONTROL Internal name]** , **[!UICONTROL Label]** en de id van de afbeelding (markering) in. Neem contact op met de beheerder als u een nieuwe afbeelding wilt toevoegen.

   ![](assets/s_ncs_admin_survey_trad_new_itemized_list_2.png)
