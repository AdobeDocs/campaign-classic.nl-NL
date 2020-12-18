---
solution: Campaign Classic
product: campaign
title: Een verjaardags-e-mail verzenden
description: Leer hoe u een e-mailbericht over een verjaardag verzendt met een workflow
audience: workflow
content-type: reference
topic-tags: use-cases
translation-type: tm+mt
source-git-commit: 20dcdd91d71158bc373db68c3f61f6808b240bd2
workflow-type: tm+mt
source-wordcount: '882'
ht-degree: 1%

---


# Een verjaardags-e-mail verzenden{#sending-a-birthday-email}

## Inleiding {#introduction}

In dit geval wordt beschreven hoe u een terugkerende e-mail naar een lijst met ontvangers op de dag van hun geboortedatum wilt sturen.

Voor het instellen van dit gebruiksgeval hebben we de volgende workflow voor doelversie gemaakt:

![](assets/birthday-workflow_usecase_1.png)

Met deze (dagelijkse) workflow worden alle ontvangers geselecteerd die op de huidige datum jarig zijn.

![](assets/do-not-localize/how-to-video.png) Deze manier van werken kan ook worden gevonden in de vorm van een video. Raadpleeg voor meer informatie de [Video over het maken van een workflow](https://docs.adobe.com/content/help/en/campaign-classic-learn/tutorials/automating-with-workflows/creating-a-workflow.html).

Hiertoe maakt u een campagne en klikt u op het tabblad **[!UICONTROL Targeting and workflows]**. Raadpleeg voor meer informatie de sectie [Het hoofddoel maken in een workflow](../../campaign/using/marketing-campaign-deliveries.md#building-the-main-target-in-a-workflow).

Voer vervolgens de volgende stappen uit:

## Het verzenden {#configuring-the-scheduler} plannen

1. Voeg eerst een **Planner** toe om het verzenden van de levering elke dag te activeren. In het onderstaande voorbeeld wordt de levering elke dag om 18.00 uur gemaakt.

   ![](assets/recur_delivery2.png)


## Ontvangers identificeren waarvan de verjaardag {#identifying-recipients-whose-birthday-it-is} is

Na het vormen van **[!UICONTROL Scheduler]** activiteit zodat het werkschema elke dag begint, identificeer alle ontvangers de waarvan geboortedatum de huidige datum evenaart.

Hiervoor voert u de volgende stappen uit:

1. Sleep een **[!UICONTROL Query]**-activiteit naar de werkstroom en dubbelklik erop.
1. Klik op de koppeling **Query** bewerken en selecteer **[!UICONTROL Filtering conditions]**.

   ![](assets/s_ncs_user_create_exp_exple00.png)

1. Klik op de eerste cel van de kolom **[!UICONTROL Expression]** en klik **[!UICONTROL Edit expression]** om de expressieeditor te openen.

   ![](assets/s_ncs_user_create_exp_exple.png)

1. Klik **[!UICONTROL Advanced selection]** om de het filtreren wijze te selecteren.

   ![](assets/s_ncs_user_create_exp_exple_a.png)

1. Selecteer **[!UICONTROL Edit the formula using an expression]** en klik **[!UICONTROL Next]** om de uitdrukkingsredacteur te tonen.
1. Dubbelklik in de lijst met functies op **[!UICONTROL Day]**, die toegankelijk is via het knooppunt **[!UICONTROL Date]**. Deze functie retourneert het getal dat de dag vertegenwoordigt die overeenkomt met de datum die als parameter is doorgegeven.

   ![](assets/s_ncs_user_create_exp_exple01.png)

1. Dubbelklik in de lijst met beschikbare velden op **[!UICONTROL Birth date]**. In het bovenste gedeelte van de editor wordt dan de volgende formule weergegeven:

   ```
   Day(@birthDate)
   ```

   Klik **[!UICONTROL Finish]** om te bevestigen.

1. In de vraagredacteur, in de eerste cel van de **[!UICONTROL Operator]** kolom, uitgezochte **[!UICONTROL equal to]**.

   ![](assets/s_ncs_user_create_exp_exple02.png)

1. Klik vervolgens op de eerste cel van de tweede kolom (**[!UICONTROL Value]**) en klik op **[!UICONTROL Edit expression]** om de expressie-editor te openen.
1. Dubbelklik in de lijst met functies op **[!UICONTROL Day]**, die toegankelijk is via het knooppunt **[!UICONTROL Date]**.
1. Dubbelklik op de functie **[!UICONTROL GetDate]** om de huidige datum op te halen.

   ![](assets/s_ncs_user_create_exp_exple04.png)

   In het bovenste gedeelte van de editor wordt de volgende formule weergegeven:

   ```
   Day(GetDate())
   ```

   Klik **[!UICONTROL Finish]** om te bevestigen.

1. Herhaal deze procedure om de geboortemaand van de huidige maand op te halen. Klik hiertoe op de knop **[!UICONTROL Add]** en herhaal stap 3 tot en met 10, waarbij **[!UICONTROL Day]** wordt vervangen door **[!UICONTROL Month]**.

   De volledige vraag is als volgt:

   ![](assets/s_ncs_user_create_exp_exple03.png)

Koppel het resultaat van de **[!UICONTROL Query]** activiteit aan **[!UICONTROL Email delivery]** activiteit om een e-mail naar de lijst van al uw ontvangers op hun verjaardag te verzenden.

## Met inbegrip van ontvangers geboren op 29 februari (facultatief) {#including-recipients-born-on-february-29th--optional-}

Als u alle ontvangers wilt opnemen die op 29 februari zijn geboren, toont deze gebruikszaak hoe u een terugkerende e-mail naar een lijst met ontvangers voor hun verjaardag wilt sturen - of het nu een schrikkeljaar is of niet.

De belangrijkste implementatiestappen voor dit gebruiksgeval zijn:

* Ontvangers selecteren
* Kiezen of het een schrikkeljaar is
* Ontvangers selecteren die op 29 februari zijn geboren

Voor het instellen van dit gebruiksgeval hebben we de volgende workflow voor doelversie gemaakt:



Als het huidige jaar **geen schrikkeljaar is** en de werkstroom op 1 Maart wordt in werking gesteld, moeten wij alle ontvangers selecteren die hun verjaardag gisteren (29 februari) zouden hebben gehad en hen toevoegen aan de lijst van ontvangers. In alle andere gevallen is geen aanvullende actie vereist.

### Stap 1: Ontvangers selecteren {#step-1--selecting-the-recipients}

Na het vormen van **[!UICONTROL Scheduler]** activiteit zodat het werkschema elke dag begint, identificeer alle ontvangers de waarvan verjaardag de huidige dag is.

>[!NOTE]
>
>Als het huidige jaar een schrikkeljaar is, worden alle ontvangers die op 29 februari geboren zijn automatisch opgenomen.

![](assets/birthday-workflow_usecase_2.png)

Ontvangers selecteren waarvan de verjaardag overeenkomt met de huidige datum, wordt weergegeven in de sectie [Ontvangers identificeren waarvan de verjaardag ](#identifying-recipients-whose-birthday-it-is) is.

### Stap 2: Selecteer of het een schrikkeljaar is {#step-2--select-whether-or-not-it-is-a-leap-year}

Met de activiteit **[!UICONTROL Test]** kunt u controleren of het een schrikkeljaar is en of de huidige datum 1 maart is.

Als de test wordt geverifieerd (het jaar is geen schrikkeljaar - er is geen 29 februari - en de huidige datum is inderdaad 1 maart), wordt de overgang **[!UICONTROL True]** ingeschakeld en worden de ontvangers die op 29 februari geboren worden toegevoegd aan de eerste levering van 1 maart. Anders, wordt de **[!UICONTROL False]** overgang toegelaten en slechts zullen de ontvangers die op de huidige datum worden geboren de levering ontvangen.

Kopieer en plak de onderstaande code in de sectie **[!UICONTROL Initialization script]** van het tabblad **[!UICONTROL Advanced]**.

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

Voeg de volgende voorwaarde in **[!UICONTROL Conditional forks]** sectie toe:

```
vars.currentIsALeapYear == 0 && vars.firstOfMarch == 1
```

![](assets/birthday-workflow_usecase_4.png)

### Stap 3: Selecteer ontvangers die op 29 februari {#step-3--select-any-recipients-born-on-february-29th} zijn geboren

Maak een **[!UICONTROL Fork]**-activiteit en koppel een van de uitgaande overgangen aan een **[!UICONTROL Query]**-activiteit.

Selecteer in deze query alle ontvangers waarvan de geboortedatum 29 februari is.

![](assets/birthday-workflow_usecase_5.png)

Combineer de resultaten met een **[!UICONTROL Union]** activiteit.

Koppel de resultaten van de twee **[!UICONTROL Test]** activiteitsvertakkingen aan een **[!UICONTROL Email delivery]** activiteit om een e-mail naar de lijst van al uw ontvangers op hun verjaardag te verzenden, zelfs aan die op 29 februari tijdens een niet-schrikkeljaar geboren.

## Een terugkerende levering {#creating-a-recurring-delivery-in-a-targeting-workflow} maken

Voeg een **Terugkerende levering** activiteit toe die op het malplaatje wordt gebaseerd van verjaardags e-mail dat u wilt verzenden.

>[!CAUTION]
>
>Om de workflows uit te voeren, moeten de technische workflows met betrekking tot het campagneproces worden gestart. Raadpleeg voor meer informatie de sectie [Lijst met workflows voor campagneprocessen](../../workflow/using/campaign.md).
>
>Als de goedkeuringsstappen voor de campagne zijn ingeschakeld, worden de leveringen pas verzonden nadat deze stappen zijn bevestigd. Raadpleeg voor meer informatie de sectie [De processen kiezen die moeten worden goedgekeurd](../../campaign/using/marketing-campaign-approval.md#choosing-the-processes-to-be-approved).

![](assets/birthday-workflow_usecase_1.png)
