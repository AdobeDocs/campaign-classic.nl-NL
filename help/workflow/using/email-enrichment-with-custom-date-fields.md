---
product: campaign
title: E-mailverrijking met aangepaste datumvelden
description: Leer hoe u e-mailberichten verrijkt met aangepaste datumvelden
feature: Workflows
exl-id: 85e0ec2a-b7cb-4d0b-a281-9ad72594403a
source-git-commit: b94c4bfd478b4a8fbcefe6341608dd6a14bb31d3
workflow-type: tm+mt
source-wordcount: '538'
ht-degree: 3%

---

# E-mailverrijking met aangepaste datumvelden{#email-enrichment-with-custom-date-fields}

![](../../assets/common.svg)

In dit voorbeeld willen we een e-mail met aangepaste gegevensvelden verzenden aan ontvangers die deze maand hun verjaardagen vieren. Het e-mailbericht bevat een coupon die een week voor en na hun verjaardagen geldig is.

We moeten ontvangers van een lijst aanspreken die hun verjaardagen deze maand vieren met een **[!UICONTROL Split]** activiteit. Gebruik vervolgens de **[!UICONTROL Enrichment]** activiteit, zal het gebied van douanegegevens als geldigheidsdata in e-mail voor de speciale aanbieding van de klant dienst doen.

![](assets/uc_enrichment.png)

U kunt dit voorbeeld maken door de volgende stappen toe te passen:

1. In de **[!UICONTROL Targeting and workflows]** tabblad van uw campagne, sleept u een **[!UICONTROL Read list]** activiteit om uw lijst van ontvangers te richten.
1. De lijst die moet worden verwerkt, kan expliciet worden opgegeven, door een script worden berekend of dynamisch worden gelokaliseerd, afhankelijk van de geselecteerde opties en de hier gedefinieerde parameters.

   ![](assets/uc_enrichment_1.png)

1. Voeg een **[!UICONTROL Split]** activiteit om ontvangers die deze maand hun verjaardagen vieren te onderscheiden van andere ontvangers.
1. Als u de lijst wilt splitsen, gaat u naar **[!UICONTROL Filtering of selected records]** categorie, selecteert u **[!UICONTROL Add a filtering condition on the inbound population]**. Klik vervolgens op **[!UICONTROL Edit]**.

   ![](assets/uc_enrichment_2.png)

1. Selecteren **[!UICONTROL Filtering conditions]** Klik vervolgens op de knop **[!UICONTROL Edit expression]** om de maand van de verjaardag van de ontvanger te filteren.

   ![](assets/uc_enrichment_3.png)

1. Klikken **[!UICONTROL Advanced Selection]** dan **[!UICONTROL Edit the formula using an expression]** en voeg de volgende expressie toe: Maand (@geboorteDate).
1. In de **[!UICONTROL Operator]** kolom, selecteert u de **[!UICONTROL equal to]**.
1. Filter de voorwaarde verder door de **[!UICONTROL Value]** maand van de huidige datum: Month(GetDate()).

   Hierdoor worden ontvangers gevraagd van wie de geboortemaand overeenkomt met de huidige maand.

   ![](assets/uc_enrichment_4.png)

1. Klik op **[!UICONTROL Finish]**. Dan, in **[!UICONTROL General]** tabblad van uw **[!UICONTROL Split]** activiteit, klik **[!UICONTROL Generate complement]** in de **[!UICONTROL Results]** categorie.

   Met de **[!UICONTROL Complement]** resulteert, kunt u een leveringsactiviteit toevoegen of een lijst bijwerken. Hier hebben we zojuist een **[!UICONTROL End]** activiteit.

   ![](assets/uc_enrichment_6.png)

U moet nu uw **[!UICONTROL Enrichment]** activiteit:

1. Een **[!UICONTROL Enrichment]** activiteit na de subset om aangepaste datumvelden toe te voegen.

   ![](assets/uc_enrichment_7.png)

1. Open uw **[!UICONTROL Enrichment]** activiteit. In de **[!UICONTROL Complementary information]** categorie, klikt u op **[!UICONTROL Add data]**.

   ![](assets/uc_enrichment_8.png)

1. Selecteren **[!UICONTROL Data linked to the filtering dimension]** dan **[!UICONTROL Data of the filtering dimension]**.
1. Klik op de knop **[!UICONTROL Add]**.

   ![](assets/uc_enrichment_9.png)

1. Voeg een **[!UICONTROL Label]**. Dan, in **[!UICONTROL Expression]** kolom, klikt u op **[!UICONTROL Edit expression]**.

   ![](assets/uc_enrichment_10.png)

1. Ten eerste moeten we ons richten op de week vóór de geboortedatum als **Begindatum geldigheid** met de volgende **[!UICONTROL Expression]**: `SubDays([target/@birthDate], 7)`.

   ![](assets/uc_enrichment_11.png)

1. Vervolgens maakt u het aangepaste datumveld **Einddatum geldigheid** die de week na de geboortedatum als doel zullen hebben, moet u de **[!UICONTROL Expression]**: `AddDays([target/@birthDate], 7)`.

   U kunt een label aan uw expressie toevoegen.

   ![](assets/uc_enrichment_12.png)

1. Klik op **[!UICONTROL Ok]**. Uw verrijking is nu klaar.

Na uw **[!UICONTROL Enrichment]** activiteit, kunt u een levering toevoegen. In dit geval hebben we een e-maillevering toegevoegd om ontvangers een speciaal voorstel met geldigheidsdata te sturen naar klanten die deze maand hun verjaardagen vieren.

1. Sleep een **[!UICONTROL Email delivery]** activiteit na uw **[!UICONTROL Enrichment]** activiteit.

   ![](assets/uc_enrichment_15.png)

1. Dubbelklik op de knop **[!UICONTROL Email delivery]** activiteiten om uw levering aan te passen.
1. Voeg een **[!UICONTROL Label]** aan uw levering en klik op **[!UICONTROL Continue]**.
1. Klikken **[!UICONTROL Save]** om uw e-maillevering te maken.
1. Inchecken in het dialoogvenster **[!UICONTROL Approval]** tabblad van de e-maillevering **[!UICONTROL Properties]** de **[!UICONTROL Confirm delivery before sending option]** is ingeschakeld.

   Start vervolgens de workflow om de uitgaande overgang te verrijken met de doelgegevens.

   ![](assets/uc_enrichment_18.png)

U kunt nu uw e-maillevering ontwerpen met de aangepaste datumvelden die zijn gemaakt in het dialoogvenster **[!UICONTROL Enrichment]** activiteit.

1. Dubbelklik op de knop **[!UICONTROL Email delivery]** activiteit.
1. Voeg uw doelextensies toe aan uw e-mail. Het zou binnen de volgende uitdrukking moeten zijn om het formaat van uw geldigheidsdata te vormen:

   ```
   <%=
           formatDate(targetData.alias of your expression,"%2D.%2M")  %>
   ```

1. Klik op ![](assets/uc_enrichment_16.png) . Selecteren **[!UICONTROL Target extension]** de eerder gemaakte aangepaste geldigheidsdatums met de **[!UICONTROL Enrichment]** activiteit om uw uitbreiding aan de formatDate uitdrukking toe te voegen.

   ![](assets/uc_enrichment_19.png)

1. Configureer uw e-mailinhoud naar wens.

   ![](assets/uc_enrichment_17.png)

1. Geef een voorbeeld van uw e-mail weer om te controleren of uw aangepaste datumvelden correct zijn geconfigureerd

   ![](assets/uc_enrichment_20.png)

Uw e-mail is nu klaar. Je kunt je proefdrukken verzenden en je levering bevestigen om je geboortee-mails te verzenden.
