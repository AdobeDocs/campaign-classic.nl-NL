---
solution: Campaign Classic
product: campaign
title: E-mailverrijking met aangepaste datumvelden
description: Leer hoe u e-mailberichten verrijkt met aangepaste datumvelden
audience: workflow
content-type: reference
topic-tags: use-cases
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '538'
ht-degree: 3%

---


# E-mailverrijking met aangepaste datumvelden{#email-enrichment-with-custom-date-fields}

In dit voorbeeld willen we een e-mail met aangepaste gegevensvelden verzenden aan ontvangers die deze maand hun verjaardagen vieren. Het e-mailbericht bevat een coupon die een week voor en na hun verjaardagen geldig is.

Wij moeten ontvangers van een lijst richten die hun verjaardagen deze maand met een **[!UICONTROL Split]** activiteit vieren. Vervolgens gebruikt u de activiteit **[!UICONTROL Enrichment]** om het veld met aangepaste gegevens als geldigheidsdatums op te nemen in de e-mail voor de speciale aanbieding van de klant.

![](assets/uc_enrichment.png)

U kunt dit voorbeeld maken door de volgende stappen toe te passen:

1. Op **[!UICONTROL Targeting and workflows]** lusje van uw campagne, belemmering en laat vallen **[!UICONTROL Read list]** activiteit om uw lijst van ontvangers te richten.
1. De lijst die moet worden verwerkt, kan expliciet worden opgegeven, door een script worden berekend of dynamisch worden gelokaliseerd, afhankelijk van de geselecteerde opties en de hier gedefinieerde parameters.

   ![](assets/uc_enrichment_1.png)

1. Voeg een **[!UICONTROL Split]** activiteit toe om ontvangers te onderscheiden die hun verjaardagen deze maand van andere ontvangers zullen vieren.
1. Als u de lijst wilt splitsen, selecteert u **[!UICONTROL Add a filtering condition on the inbound population]** in de categorie **[!UICONTROL Filtering of selected records]**. Klik vervolgens op **[!UICONTROL Edit]**.

   ![](assets/uc_enrichment_2.png)

1. Selecteer **[!UICONTROL Filtering conditions]** dan klik **[!UICONTROL Edit expression]** knoop om de maand van de verjaardag van de ontvanger te filtreren.

   ![](assets/uc_enrichment_3.png)

1. Klik **[!UICONTROL Advanced Selection]** dan **[!UICONTROL Edit the formula using an expression]** en voeg de volgende uitdrukking toe: Maand (@geboorteDate).
1. Selecteer **[!UICONTROL equal to]** in de kolom **[!UICONTROL Operator]**.
1. Filter de voorwaarde verder door de **[!UICONTROL Value]** maand van de huidige datum toe te voegen: Month(GetDate()).

   Hierdoor worden ontvangers gevraagd van wie de geboortemaand overeenkomt met de huidige maand.

   ![](assets/uc_enrichment_4.png)

1. Klik op **[!UICONTROL Finish]**. Klik vervolgens op het tabblad **[!UICONTROL General]** van uw **[!UICONTROL Split]**-activiteit op **[!UICONTROL Generate complement]** in de categorie **[!UICONTROL Results]**.

   Met het **[!UICONTROL Complement]** resultaat, kunt u een leveringsactiviteit toevoegen of een lijst bijwerken. Hier hebben we zojuist een **[!UICONTROL End]**-activiteit toegevoegd.

   ![](assets/uc_enrichment_6.png)

U moet nu uw **[!UICONTROL Enrichment]** activiteit vormen:

1. Voeg een **[!UICONTROL Enrichment]** activiteit na uw subset toe om uw gebieden van de douanedatum toe te voegen.

   ![](assets/uc_enrichment_7.png)

1. Open uw **[!UICONTROL Enrichment]** activiteit. Klik in de categorie **[!UICONTROL Complementary information]** op **[!UICONTROL Add data]**.

   ![](assets/uc_enrichment_8.png)

1. Selecteer **[!UICONTROL Data linked to the filtering dimension]** dan **[!UICONTROL Data of the filtering dimension]**.
1. Klik op de knop **[!UICONTROL Add]**.

   ![](assets/uc_enrichment_9.png)

1. Voeg een **[!UICONTROL Label]** toe. Klik vervolgens in de kolom **[!UICONTROL Expression]** op **[!UICONTROL Edit expression]**.

   ![](assets/uc_enrichment_10.png)

1. Eerst, moeten wij de week vóór de geboortedatum als **Geldigheidsbegindatum** met het volgende richten **[!UICONTROL Expression]**: `SubDays([target/@birthDate], 7)`.

   ![](assets/uc_enrichment_11.png)

1. Als u vervolgens het aangepaste datumveld **Einddatum geldigheid** wilt maken dat de week na de geboortedatum als doel instelt, moet u **[!UICONTROL Expression]** toevoegen: `AddDays([target/@birthDate], 7)`.

   U kunt een label aan uw expressie toevoegen.

   ![](assets/uc_enrichment_12.png)

1. Klik op **[!UICONTROL Ok]**. Uw verrijking is nu klaar.

Na uw **[!UICONTROL Enrichment]** activiteit, kunt u een levering toevoegen. In dit geval hebben we een e-maillevering toegevoegd om ontvangers een speciaal voorstel met geldigheidsdata te sturen naar klanten die deze maand hun verjaardagen vieren.

1. Sleep een **[!UICONTROL Email delivery]** activiteit na uw **[!UICONTROL Enrichment]** activiteit.

   ![](assets/uc_enrichment_15.png)

1. Dubbelklik op uw **[!UICONTROL Email delivery]** activiteit om uw levering aan te passen.
1. Voeg een **[!UICONTROL Label]** aan uw levering toe en klik **[!UICONTROL Continue]**.
1. Klik **[!UICONTROL Save]** om uw e-maillevering tot stand te brengen.
1. Schakel op het tabblad **[!UICONTROL Approval]** van de e-maillevering **[!UICONTROL Properties]** in dat **[!UICONTROL Confirm delivery before sending option]** is ingeschakeld.

   Start vervolgens de workflow om de uitgaande overgang te verrijken met de doelgegevens.

   ![](assets/uc_enrichment_18.png)

U kunt nu uw e-maillevering ontwerpen met de aangepaste datumvelden die in de activiteit **[!UICONTROL Enrichment]** zijn gemaakt.

1. Dubbelklik op uw **[!UICONTROL Email delivery]**-activiteit.
1. Voeg uw doelextensies toe aan uw e-mail. Het zou binnen de volgende uitdrukking moeten zijn om het formaat van uw geldigheidsdata te vormen:

   ```
   <%=
           formatDate(targetData.alias of your expression,"%2D.%2M")  %>
   ```

1. Klik op ![](assets/uc_enrichment_16.png) . Selecteer **[!UICONTROL Target extension]** dan de eerder gemaakte aangepaste geldigheidsdata met de **[!UICONTROL Enrichment]** activiteit om uw uitbreiding aan de formatDate uitdrukking toe te voegen.

   ![](assets/uc_enrichment_19.png)

1. Configureer uw e-mailinhoud naar wens.

   ![](assets/uc_enrichment_17.png)

1. Geef een voorbeeld van uw e-mail weer om te controleren of uw aangepaste datumvelden correct zijn geconfigureerd

   ![](assets/uc_enrichment_20.png)

Uw e-mail is nu klaar. Je kunt je proefdrukken verzenden en je levering bevestigen om je geboortee-mails te verzenden.
