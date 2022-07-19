---
product: campaign
title: Een verjaardags-e-mail verzenden
description: Leer hoe u een e-mailbericht over een verjaardag verzendt met een workflow
feature: Workflows
exl-id: 38006cca-e945-4b9d-8e2d-ed537b8541d9
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: tm+mt
source-wordcount: '879'
ht-degree: 2%

---

# Een verjaardags-e-mail verzenden{#sending-a-birthday-email}

![](../../assets/v7-only.svg)

## Inleiding {#introduction}

In dit geval wordt beschreven hoe u een terugkerende e-mail naar een lijst met ontvangers op de dag van hun geboortedatum wilt sturen.

Voor het instellen van dit gebruiksgeval hebben we de volgende workflow voor doelversie gemaakt:

![](assets/birthday-workflow_usecase_1.png)

Met deze (dagelijkse) workflow worden alle ontvangers geselecteerd die op de huidige datum jarig zijn.

![](assets/do-not-localize/how-to-video.png) Deze manier van werken kan ook worden gevonden in de vorm van een video. Raadpleeg voor meer informatie de [Een workflow maken](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/automating-with-workflows/creating-a-workflow.html) video.

Om dit te doen, creeer een campagne en klik **[!UICONTROL Targeting and workflows]** tab. Raadpleeg voor meer informatie de [Het hoofddoel opbouwen in een workflow](../../campaign/using/marketing-campaign-deliveries.md#building-the-main-target-in-a-workflow) sectie.

Voer vervolgens de volgende stappen uit:

## Het plannen van het verzenden {#configuring-the-scheduler}

1. Voeg eerst een **Planner** om het verzenden van de levering elke dag te activeren. In het onderstaande voorbeeld wordt de levering elke dag om 18.00 uur gemaakt.

   ![](assets/recur_delivery2.png)


## Ontvangers identificeren van wie de verjaardag het is {#identifying-recipients-whose-birthday-it-is}

Nadat u de **[!UICONTROL Scheduler]** activiteit zodat de werkstroom elke dag begint, identificeer alle ontvangers waarvan geboortedatum de huidige datum evenaart.

Hiervoor voert u de volgende stappen uit:

1. Sleep een **[!UICONTROL Query]** in de werkstroom en dubbelklik erop.
1. Klik op de knop **Query bewerken** koppelen en selecteren **[!UICONTROL Filtering conditions]**.

   ![](assets/s_ncs_user_create_exp_exple00.png)

1. Klik op de eerste cel van het dialoogvenster **[!UICONTROL Expression]** kolom en klik op **[!UICONTROL Edit expression]** om de expressie-editor te openen.

   ![](assets/s_ncs_user_create_exp_exple.png)

1. Klikken **[!UICONTROL Advanced selection]** om de filtermodus te selecteren.

   ![](assets/s_ncs_user_create_exp_exple_a.png)

1. Selecteren **[!UICONTROL Edit the formula using an expression]** en klik op **[!UICONTROL Next]** om de expressie-editor weer te geven.
1. Dubbelklik in de lijst met functies op **[!UICONTROL Day]**, die toegankelijk is via de **[!UICONTROL Date]** knooppunt. Deze functie retourneert het getal dat de dag vertegenwoordigt die overeenkomt met de datum die als parameter is doorgegeven.

   ![](assets/s_ncs_user_create_exp_exple01.png)

1. Dubbelklik in de lijst met beschikbare velden **[!UICONTROL Birth date]**. In het bovenste gedeelte van de editor wordt dan de volgende formule weergegeven:

   ```
   Day(@birthDate)
   ```

   Klik op **[!UICONTROL Finish]** om te bevestigen.

1. In de vraagredacteur, in de eerste cel van **[!UICONTROL Operator]** kolom, selecteren **[!UICONTROL equal to]**.

   ![](assets/s_ncs_user_create_exp_exple02.png)

1. Klik vervolgens op de eerste cel van de tweede kolom (**[!UICONTROL Value]**) en klik op **[!UICONTROL Edit expression]** om de expressie-editor te openen.
1. Dubbelklik in de lijst met functies op **[!UICONTROL Day]**, die toegankelijk is via de **[!UICONTROL Date]** knooppunt.
1. Dubbelklik op de knop **[!UICONTROL GetDate]** om de huidige datum op te halen.

   ![](assets/s_ncs_user_create_exp_exple04.png)

   In het bovenste gedeelte van de editor wordt de volgende formule weergegeven:

   ```
   Day(GetDate())
   ```

   Klik op **[!UICONTROL Finish]** om te bevestigen.

1. Herhaal deze procedure om de geboortemaand van de huidige maand op te halen. Om dit te doen, klik **[!UICONTROL Add]** en herhaal stap 3 tot en met 10, vervangen **[!UICONTROL Day]** with **[!UICONTROL Month]**.

   De volledige vraag is als volgt:

   ![](assets/s_ncs_user_create_exp_exple03.png)

Het resultaat van de opdracht koppelen **[!UICONTROL Query]** activiteit aan een **[!UICONTROL Email delivery]** activiteit om een e-mail naar de lijst van al uw ontvangers op hun verjaardag te verzenden.

## Met inbegrip van ontvangers geboren op 29 februari (facultatief) {#including-recipients-born-on-february-29th--optional-}

Als u alle ontvangers wilt opnemen die op 29 februari zijn geboren, toont deze gebruikszaak hoe u een terugkerende e-mail naar een lijst met ontvangers voor hun verjaardag wilt sturen - of het nu een schrikkeljaar is of niet.

De belangrijkste implementatiestappen voor dit gebruiksgeval zijn:

* Ontvangers selecteren
* Kiezen of het een schrikkeljaar is
* Ontvangers selecteren die op 29 februari zijn geboren

Voor het instellen van dit gebruiksgeval hebben we de volgende workflow voor doelversie gemaakt:



Indien het lopende jaar **is geen schrikkeljaar** en de workflow wordt uitgevoerd op 1 maart, dus moeten we alle ontvangers selecteren die gisteren (29 februari) jarig zouden zijn en ze toevoegen aan de lijst met ontvangers. In alle andere gevallen is geen aanvullende actie vereist.

### Stap 1: De ontvangers selecteren {#step-1--selecting-the-recipients}

Nadat u de **[!UICONTROL Scheduler]** activiteit zodat de werkstroom elke dag begint, identificeer alle ontvangers de waarvan verjaardag de huidige dag is.

>[!NOTE]
>
>Als het huidige jaar een schrikkeljaar is, worden alle ontvangers die op 29 februari geboren zijn automatisch opgenomen.

![](assets/birthday-workflow_usecase_2.png)

Ontvangers selecteren waarvan de verjaardag overeenkomt met de huidige datum wordt weergegeven in het dialoogvenster [Ontvangers identificeren van wie de verjaardag het is](#identifying-recipients-whose-birthday-it-is) sectie.

### Stap 2: Selecteer of het een schrikkeljaar is {#step-2--select-whether-or-not-it-is-a-leap-year}

De **[!UICONTROL Test]** Met deze activiteit kunt u controleren of het een schrikkeljaar is en of de huidige datum 1 maart is.

Als de test wordt geverifieerd (het jaar is geen schrikkeljaar - er is geen 29 februari - en de huidige datum is inderdaad 1 maart), **[!UICONTROL True]** de overgang is ingeschakeld en de op 29 februari geboren ontvangers worden toegevoegd aan de levering van 1 maart. Anders wordt **[!UICONTROL False]** de overgang wordt toegelaten en slechts zullen de ontvangers die op de huidige datum worden geboren de levering ontvangen.

Kopieer en plak de onderstaande code in de **[!UICONTROL Initialization script]** van de **[!UICONTROL Advanced]** tab.

```
function isLeapYear(iYear)
{
    if(iYear/4 == Math.floor(iYear/4))
    {
        if(iYear/100 != Math.floor(iYear/100))
        {
            // Divisible by 4 only -> Leap Year
            return 1;
        }
        else
        {
            if(iYear/400 == Math.floor(iYear/400))
            {
                // Divisible by 4, 100 and 400 -> Leap year
                return 1;
            }
        }
    }
    // all others: no leap year
    return 0;
}

// Return today's date and time
var currentTime = new Date()
// returns the month (from 0 to 11)
var month = currentTime.getMonth() + 1
// returns the day of the month (from 1 to 31)
var day = currentTime.getDate()
// returns the year (four digits)
var year = currentTime.getFullYear()

// is current year a leap year?
vars.currentIsALeapYear = isLeapYear(year);

// is current date the first of march?
if(month == 3 && day == 1) {
  // today is 1st of march
vars.firstOfMarch = 1;
}
```

![](assets/birthday-workflow_usecase_3.png)

Voeg de volgende voorwaarde in toe **[!UICONTROL Conditional forks]** sectie:

```
vars.currentIsALeapYear == 0 && vars.firstOfMarch == 1
```

![](assets/birthday-workflow_usecase_4.png)

### Stap 3: Selecteer de ontvangers die op 29 februari zijn geboren {#step-3--select-any-recipients-born-on-february-29th}

Een **[!UICONTROL Fork]** activiteit en verbind één van de uitgaande overgangen aan een **[!UICONTROL Query]** activiteit.

Selecteer in deze query alle ontvangers waarvan de geboortedatum 29 februari is.

![](assets/birthday-workflow_usecase_5.png)

De resultaten combineren met een **[!UICONTROL Union]** activiteit.

De resultaten van de twee koppelingen **[!UICONTROL Test]** vertakkingen van activiteiten aan een **[!UICONTROL Email delivery]** activiteit om een e-mail naar de lijst van al uw ontvangers op hun verjaardag te verzenden, zelfs aan hen die op 29 februari tijdens een niet-schrikkeljaar geboren worden.

## Een terugkerende levering maken {#creating-a-recurring-delivery-in-a-targeting-workflow}

Voeg een **Terugkerende levering** activiteit op basis van de e-mailsjabloon voor verjaardag die u wilt verzenden.

>[!CAUTION]
>
>Om de workflows uit te voeren, moeten de technische workflows met betrekking tot het campagnepakket worden gestart. Raadpleeg voor meer informatie de [Lijst van technische werkstromen](about-technical-workflows.md) sectie.
>
>Als de goedkeuringsstappen voor de campagne zijn ingeschakeld, worden de leveringen pas verzonden nadat deze stappen zijn bevestigd. Raadpleeg voor meer informatie de [Ervoor te keuren processen kiezen](../../campaign/using/marketing-campaign-approval.md#choosing-the-processes-to-be-approved) sectie.

![](assets/birthday-workflow_usecase_1.png)
