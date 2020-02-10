---
title: Leeslijst
seo-title: Leeslijst
description: Leeslijst
seo-description: null
page-status-flag: never-activated
uuid: 34e28675-f28b-407f-8d60-41a5383af0db
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: 96a7aea4-4799-4ac7-8dff-666b075a1c43
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Leeslijst{#read-list}

Gegevens die in een werkstroom worden verwerkt, kunnen afkomstig zijn van lijsten waarin de gegevens vooraf zijn voorbereid of gestructureerd (na een eerdere segmentatie of bestandsupload).

Met de **[!UICONTROL Read list]** activiteit kunt u de gegevens kopiëren uit een lijst in de werktabel van de workflow, zoals gegevens uit een query. Het is dan toegankelijk door het werkschema.

De lijst die moet worden verwerkt, kan expliciet worden opgegeven, door een script worden berekend of dynamisch worden gelokaliseerd, afhankelijk van de geselecteerde opties en de parameters die in een **[!UICONTROL Read list]** activiteit zijn gedefinieerd.

![](assets/list_edit_select_option_01.png)

Als de lijst niet uitdrukkelijk wordt gespecificeerd, moet u een lijst verstrekken die als malplaatje moet worden gebruikt om zijn structuur te weten te komen.

![](assets/s_advuser_list_template_select.png)

Zodra de lijstselectie is gevormd, kunt u een filter toevoegen gebruikend de **[!UICONTROL Edit query]** optie om één deel van de bevolking voor het volgende werkschema te houden.

![](assets/wf_readlist_1.png)

>[!CAUTION]
>
>Als u een filter wilt maken in een leeslijstactiviteit, moet de relevante lijst een &quot;bestandstype&quot;zijn.

De lijsten kunnen rechtstreeks in de Campagne van Adobe via de verbinding van de homepage worden gecreeerd. **[!UICONTROL Profiles and Targets > Lists]** Ze kunnen ook in een workflow worden gemaakt met behulp van de **[!UICONTROL List update]** activiteit.

**Voorbeeld: Een lijst met verzendadressen uitsluiten**

In het volgende voorbeeld kunt u een lijst met e-mailadressen gebruiken om gegevens uit te sluiten van het doel voor e-maillevering.

![](assets/s_advuser_list_read_sample_1.png)

De profielen in de map **Nieuwe contactpersonen** moeten worden geactiveerd door een leveringsactie. De e-mailadressen die van het doel moeten worden uitgesloten, worden opgeslagen in een externe lijst. In ons voorbeeld is alleen de informatie over e-mailadressen vereist voor uitsluiting.

1. Met de selectievraag voor de map **Nieuwe contactpersonen** kunt u de e-mailadressen van de geselecteerde profielen laden om uitlijning met de gegevens in de lijst in te schakelen.

   ![](assets/s_advuser_list_read_sample_0.png)

1. Hier wordt de lijst opgeslagen in de map **Lijsten** en wordt het label ervan berekend.

   ![](assets/s_advuser_list_read_sample_2.png)

1. Als u de e-mailadressen van de externe lijst wilt uitsluiten van het hoofddoel, moet u de uitsluitingsactiviteit configureren en opgeven dat de map **Nieuwe contactpersonen** de gegevens bevat die moeten worden bewaard. De gezamenlijke gegevens tussen deze set en andere binnenkomende sets uit de uitsluitingsactiviteit worden uit het doel verwijderd.

   ![](assets/s_advuser_list_read_sample_3.png)

   De uitsluitingsregels worden geconfigureerd in de centrale sectie van het bewerkingsgereedschap. Klik op de **[!UICONTROL Add]** knop om het type uitsluiting te definiëren dat u wilt toepassen.

   U kunt verschillende uitsluitingen definiëren afhankelijk van het aantal inkomende overgangen van de activiteit.

1. Selecteer in het **[!UICONTROL Exclusion set]** veld de **[!UICONTROL Read list]** activiteit: de gegevens in deze activiteit moeten van de hoofdreeks worden uitgesloten .

   In ons voorbeeld hebben we een uitzondering op joins: de gegevens in de lijst worden in overeenstemming gebracht met de gegevens van de hoofdset via het veld met het e-mailadres . Om de verbinding te vormen, selecteer **[!UICONTROL Joins]** op het **[!UICONTROL Change dimension]** gebied.

   ![](assets/s_advuser_list_read_sample_4.png)

1. Selecteer vervolgens het veld dat overeenkomt met het e-mailadres in de twee sets (bron en doel). De kolommen zullen dan worden verbonden en de ontvangers waarvan e-mailadres in de lijst van ingevoerde adressen is zullen van het doel worden uitgesloten.

