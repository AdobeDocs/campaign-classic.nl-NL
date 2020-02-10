---
title: Antwoorden op webformulieren
seo-title: Antwoorden op webformulieren
description: Antwoorden op webformulieren
seo-description: null
page-status-flag: never-activated
uuid: 374df070-8969-4bf6-bd24-0b827d38593f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: web-forms
discoiquuid: c89926b6-488e-4c72-8f67-b6af388bade3
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Antwoorden op webformulieren{#web-forms-answers}

## Responsopslagvelden {#response-storage-fields}

Antwoorden op formulieren kunnen worden opgeslagen in een veld van de database of tijdelijk in een lokale variabele. De opslagmodus voor antwoorden wordt gekozen tijdens het maken van velden. U kunt de koppeling bewerken via de **[!UICONTROL Edit storage...]** koppeling.

Voor elk invoerveld in een formulier zijn de volgende opslagopties beschikbaar:

![](assets/s_ncs_admin_survey_select_storage.png)

* **[!UICONTROL Edit a recipient]**

   U kunt een veld van de database selecteren: de antwoorden van de gebruikers zullen op dit gebied worden opgeslagen. Voor elke gebruiker wordt alleen de laatste ingevoerde waarde opgeslagen: het wordt toegevoegd aan hun profiel: Zie Gegevens [opslaan in de database](#storing-data-in-the-database).

* **[!UICONTROL Variable]**

   Als u geen informatie in het gegevensbestand wilt opslaan, kunt u een variabele gebruiken. Lokale variabelen kunnen upstream worden gedeclareerd. Zie Gegevens [opslaan in een lokale variabele](#storing-data-in-a-local-variable).

### Gegevens opslaan in de database {#storing-data-in-the-database}

Als u de gegevens in een bestaand veld van de database wilt opslaan, klikt u op het **[!UICONTROL Edit expression]** pictogram en selecteert u deze in de lijst met beschikbare velden.

![](assets/s_ncs_admin_survey_storage_type1.png)

>[!NOTE]
>
>Het standaardreferentiedocument is het schema **nms:ontvanger** . Als u het formulier wilt weergeven of een nieuw formulier wilt kiezen, selecteert u het in de lijst en klikt u op de **[!UICONTROL Properties]** knop.

### Gegevens opslaan in een lokale variabele {#storing-data-in-a-local-variable}

U kunt lokale variabelen gebruiken zodat zelfs als gegevens niet in het gegevensbestand worden opgeslagen, het op de pagina of de andere pagina&#39;s kan worden opnieuw gebruikt, bijvoorbeeld om voorwaarden op de vertoning van een gebied te plaatsen of een bericht te personaliseren.

Dit betekent dat u de waarde van een niet-opgeslagen veld kunt gebruiken om de weergave van een groep opties op de pagina toe te staan. Op de onderstaande pagina wordt het voertuigtype niet in de database opgeslagen:

![](assets/s_ncs_admin_survey_no_storage_variable.png)

Het wordt opgeslagen in een variabele die moet worden geselecteerd wanneer de drop-down doos, of via de **[!UICONTROL Edit storage...]** verbinding wordt gecreeerd.

![](assets/s_ncs_admin_survey_no_storage_variable2.png)

Via de **[!UICONTROL Edit variables...]** koppeling kunt u bestaande variabelen weergeven en nieuwe variabelen maken. Klik op de **[!UICONTROL Add]** knop om een nieuwe variabele te maken.

![](assets/s_ncs_admin_survey_add_a_variable.png)

De toegevoegde variabele is beschikbaar in de lijst met lokale variabelen wanneer de invoervelden van de pagina worden gemaakt.

>[!NOTE]
>
>Voor elk formulier kunt u variabelen upstream maken. Selecteer het formulier en klik op de **[!UICONTROL Properties]** knop om dit te doen. Het **[!UICONTROL Variables]** tabblad bevat de lokale variabelen voor het formulier.

**Voorbeeld van lokale opslag met conditionering**

In het bovenstaande voorbeeld wordt de container met gegevens over particuliere voertuigen alleen weergegeven als de **[!UICONTROL Private]** optie is geselecteerd in de vervolgkeuzelijst, zoals aangegeven in de zichtbaarheidsvoorwaarde:

![](assets/s_ncs_admin_survey_add_a_condition.png)

Als de gebruiker een privé voertuig selecteert, biedt het formulier van het Web de volgende opties:

![](assets/s_ncs_admin_survey_no_storage_conda.png)

De container met de gegevens over bedrijfsvoertuigen wordt weergegeven als de optie &quot;Professional&quot; is geselecteerd, zoals aangegeven in de zichtbaarheidsvoorwaarde:

![](assets/s_ncs_admin_survey_view_a_condition.png)

Dit betekent dat als de gebruiker een bedrijfsvoertuig selecteert, het formulier de volgende opties biedt:

![](assets/s_ncs_admin_survey_no_storage_condb.png)

## Gezamelde gegevens gebruiken {#using-collected-information}

Voor elk formulier kunnen de gegeven antwoorden opnieuw worden gebruikt in de velden of de labels. De volgende syntaxis moet worden gebruikt:

* Voor inhoud die is opgeslagen in een veld van de database:

   ```
   <%=ctx.recipient.@field name%
   ```

* Voor inhoud die is opgeslagen in een lokale variabele:

   ```
   <%= ctx.vars.variable name %
   ```

* Voor inhoud die is opgeslagen in een HTML-tekstveld:

   ```
   <%== HTML field name %
   ```

   >[!NOTE]
   >
   >In tegenstelling tot de andere velden waarvoor `<%=` tekens worden vervangen door escape-tekens, wordt de HTML-inhoud op dezelfde manier opgeslagen met behulp van de `<%==` syntaxis.

## Webformulieren opslaan {#saving-web-forms-answers}

Als u de informatie wilt opslaan die op de pagina&#39;s van een formulier wordt verzameld, moet u een opslagvak in het diagram plaatsen.

![](assets/s_ncs_admin_survey_save_box.png)

U kunt dit vak op twee manieren gebruiken:

* Als het formulier Web wordt geopend via een koppeling die in een e-mail wordt verzonden en als de gebruiker die toegang heeft tot de toepassing zich al in de database bevindt, kunt u de **[!UICONTROL Update the preloaded record]** optie controleren. Raadpleeg [Een formulier via e-mail](../../web/using/publishing-a-web-form.md#delivering-a-form-via-email)verzenden voor meer informatie.

   In dit geval gebruikt Adobe Campaign de gecodeerde primaire sleutel van het gebruikersprofiel, een unieke id die aan elk profiel is toegewezen door Adobe Campaign. U moet de informatie vormen om via de preloaddoos vooraf te laden. Zie [De formuliergegevens](../../web/using/publishing-a-web-form.md#pre-loading-the-form-data)vooraf laden voor meer informatie.

   >[!CAUTION]
   >
   >Met deze optie worden de gebruikersgegevens genegeerd, inclusief het e-mailadres als er een veld is waarin de gegevens moeten worden ingevoerd. Het kan niet worden gebruikt om nieuwe profielen te maken en vereist het gebruik van een voorlaadvenster in het formulier.

* Als u de gegevens van ontvangers in de database wilt verrijken, bewerkt u het opslagvak en selecteert u de afstemmingssleutel. Voor intern gebruik (meestal een intranetsysteem) of voor een formulier dat wordt gebruikt om nieuwe profielen te maken, kunt u bijvoorbeeld het (de) afstemmingsveld(en) selecteren. De doos biedt alle gebieden van het gegevensbestand aan die in de diverse pagina&#39;s van de toepassing van het Web worden gebruikt:

   ![](assets/s_ncs_admin_survey_save_box_edit.png)

Standaard worden de gegevens in de database geïmporteerd door een **[!UICONTROL Update or insertion]** bewerking: als het element in de database aanwezig is, wordt het element bijgewerkt (bijvoorbeeld de geselecteerde nieuwsbrief of het ingevoerde e-mailadres). Als deze niet bestaat, wordt de informatie toegevoegd.

U kunt dit gedrag echter wijzigen. Selecteer hiertoe de basis van het element en selecteer de uit te voeren bewerking in de vervolgkeuzelijst:

![](assets/s_ncs_admin_survey_save_operation.png)

U kunt een zoekmap selecteren voor afstemming en de map waarin nieuwe profielen worden gemaakt. Als deze velden leeg zijn, worden de profielen gezocht naar en gemaakt in de standaardmap van de operator.

>[!NOTE]
>
>Mogelijke bewerkingen zijn: **[!UICONTROL Simple reconciliation]**, **[!UICONTROL Update or insertion]**, **[!UICONTROL Insertion]**, **[!UICONTROL Update]**, **[!UICONTROL Deletion]**.\
>De standaardmap van de operator is de eerste map waarvoor de operator schrijfmachtigingen heeft.\
>Zie [deze sectie](../../platform/using/access-management.md).

