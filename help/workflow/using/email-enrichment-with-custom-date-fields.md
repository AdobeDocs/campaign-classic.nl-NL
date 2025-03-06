---
product: campaign
title: E-mailverrijking met aangepaste datumvelden
description: Leer hoe u e-mailberichten verrijkt met aangepaste datumvelden
feature: Workflows
hide: true
hidefromtoc: true
exl-id: 85e0ec2a-b7cb-4d0b-a281-9ad72594403a
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '538'
ht-degree: 3%

---

# E-mailverrijking met aangepaste datumvelden{#email-enrichment-with-custom-date-fields}



In dit voorbeeld willen we een e-mail met aangepaste gegevensvelden verzenden aan ontvangers die deze maand hun verjaardagen vieren. Het e-mailbericht bevat een coupon die een week voor en na hun verjaardagen geldig is.

We moeten ontvangers van een lijst die hun verjaardagen deze maand vieren, aanspreken met een **[!UICONTROL Split]** -activiteit. Vervolgens gebruikt u de activiteit **[!UICONTROL Enrichment]** en fungeert het veld met aangepaste gegevens als geldigheidsdatums in de e-mail voor de speciale aanbieding van de klant.

![](assets/uc_enrichment.png)

U kunt dit voorbeeld maken door de volgende stappen toe te passen:

1. Sleep op het tabblad **[!UICONTROL Targeting and workflows]** van uw campagne een **[!UICONTROL Read list]** -activiteit naar de lijst met ontvangers.
1. De lijst die moet worden verwerkt, kan expliciet worden opgegeven, door een script worden berekend of dynamisch worden gelokaliseerd, afhankelijk van de geselecteerde opties en de hier gedefinieerde parameters.

   ![](assets/uc_enrichment_1.png)

1. Voeg een **[!UICONTROL Split]** -activiteit toe om ontvangers die deze maand hun verjaardagen vieren, te onderscheiden van andere ontvangers.
1. Als u de lijst wilt splitsen, selecteert u in de categorie **[!UICONTROL Filtering of selected records]** de optie **[!UICONTROL Add a filtering condition on the inbound population]** . Klik vervolgens op **[!UICONTROL Edit]** .

   ![](assets/uc_enrichment_2.png)

1. Selecteer **[!UICONTROL Filtering conditions]** en klik vervolgens op de knop **[!UICONTROL Edit expression]** om de maand van de verjaardag van de ontvanger te filteren.

   ![](assets/uc_enrichment_3.png)

1. Klik op **[!UICONTROL Advanced Selection]** dan **[!UICONTROL Edit the formula using an expression]** en voeg de volgende expressie toe: Month(@geboortedatum).
1. Selecteer in de kolom **[!UICONTROL Operator]** de **[!UICONTROL equal to]** .
1. Filter de voorwaarde verder door de **[!UICONTROL Value]** maand van de huidige datum toe te voegen: Month(GetDate()).

   Hierdoor worden ontvangers gevraagd van wie de geboortemaand overeenkomt met de huidige maand.

   ![](assets/uc_enrichment_4.png)

1. Klik op **[!UICONTROL Finish]**. Klik vervolgens op het tabblad **[!UICONTROL General]** van de **[!UICONTROL Split]** -activiteit op de **[!UICONTROL Generate complement]** in de **[!UICONTROL Results]** -categorie.

   Met het **[!UICONTROL Complement]** resultaat kunt u een leveringsactiviteit toevoegen of een lijst bijwerken. Hier hebben we zojuist een **[!UICONTROL End]** activiteit toegevoegd.

   ![](assets/uc_enrichment_6.png)

U moet nu uw **[!UICONTROL Enrichment]** activiteit vormen:

1. Voeg een **[!UICONTROL Enrichment]** activiteit na uw subset toe om uw gebieden van de douanedatum toe te voegen.

   ![](assets/uc_enrichment_7.png)

1. Open uw **[!UICONTROL Enrichment]** activiteit. Klik in de categorie **[!UICONTROL Complementary information]** op **[!UICONTROL Add data]** .

   ![](assets/uc_enrichment_8.png)

1. Selecteer **[!UICONTROL Data linked to the filtering dimension]** dan **[!UICONTROL Data of the filtering dimension]** .
1. Klik op de knop **[!UICONTROL Add]**.

   ![](assets/uc_enrichment_9.png)

1. Voeg een **[!UICONTROL Label]** toe. Klik vervolgens in de kolom **[!UICONTROL Expression]** op **[!UICONTROL Edit expression]** .

   ![](assets/uc_enrichment_10.png)

1. Eerst, moeten wij de week vóór de geboortedatum als **begindatum van de Geldigheid** met het volgende richten **[!UICONTROL Expression]**: `SubDays([target/@birthDate], 7)`.

   ![](assets/uc_enrichment_11.png)

1. Dan, om het gebied van de douanedatum **eind datum van de Geldigheid** tot stand te brengen die de week na de geboortedatum zal richten, moet u **[!UICONTROL Expression]** toevoegen: `AddDays([target/@birthDate], 7)`.

   U kunt een label aan uw expressie toevoegen.

   ![](assets/uc_enrichment_12.png)

1. Klik op **[!UICONTROL Ok]**. Uw verrijking is nu klaar.

Na de **[!UICONTROL Enrichment]** -activiteit kunt u een levering toevoegen. In dit geval hebben we een e-maillevering toegevoegd om ontvangers een speciaal voorstel met geldigheidsdata te sturen naar klanten die deze maand hun verjaardagen vieren.

1. Sleep een **[!UICONTROL Email delivery]** -activiteit na de **[!UICONTROL Enrichment]** -activiteit.

   ![](assets/uc_enrichment_15.png)

1. Dubbelklik op uw **[!UICONTROL Email delivery]** -activiteit om de levering aan te passen.
1. Voeg een **[!UICONTROL Label]** toe aan uw levering en klik op **[!UICONTROL Continue]** .
1. Klik op **[!UICONTROL Save]** om uw e-maillevering te maken.
1. Controleer op het tabblad **[!UICONTROL Approval]** van de e-maillevering **[!UICONTROL Properties]** of de **[!UICONTROL Confirm delivery before sending option]** is ingeschakeld.

   Start vervolgens de workflow om de uitgaande overgang te verrijken met de doelgegevens.

   ![](assets/uc_enrichment_18.png)

U kunt nu uw e-maillevering ontwerpen met de aangepaste datumvelden die in de **[!UICONTROL Enrichment]** -activiteit zijn gemaakt.

1. Dubbelklik op de **[!UICONTROL Email delivery]** -activiteit.
1. Voeg uw doelextensies toe aan uw e-mail. Het zou binnen de volgende uitdrukking moeten zijn om het formaat van uw geldigheidsdata te vormen:

   ```
   <%=
           formatDate(targetData.alias of your expression,"%2D.%2M")  %>
   ```

1. Klik op ![](assets/uc_enrichment_16.png) . Selecteer **[!UICONTROL Target extension]** en de eerder gemaakte aangepaste geldigheidsdatums met de **[!UICONTROL Enrichment]** -activiteit om uw extensie toe te voegen aan de formatDate-expressie.

   ![](assets/uc_enrichment_19.png)

1. Configureer uw e-mailinhoud naar wens.

   ![](assets/uc_enrichment_17.png)

1. Geef een voorbeeld van uw e-mail weer om te controleren of uw aangepaste datumvelden correct zijn geconfigureerd

   ![](assets/uc_enrichment_20.png)

Uw e-mail is nu klaar. Je kunt je proefdrukken verzenden en je levering bevestigen om je geboortee-mails te verzenden.
