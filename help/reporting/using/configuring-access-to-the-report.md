---
title: Toegang tot het rapport configureren
seo-title: Toegang tot het rapport configureren
description: Toegang tot het rapport configureren
seo-description: null
page-status-flag: never-activated
uuid: d32d9805-f84f-457f-b37b-a8278642336a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: creating-new-reports
discoiquuid: dd50ca25-8fa2-48fa-84cc-a63e476701a0
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Toegang tot het rapport configureren{#configuring-access-to-the-report}

## Weergavecontext rapporteren {#report-display-context}

Bepaal de vertoningscontext van het rapport in het platform van de Campagne van Adobe gebruikend het **[!UICONTROL Display]** lusje. De toegang tot een rapport hangt van zijn selectietype, vertoningsvoorwaarden en toegangsvergunningen af.

### Type selectie {#selection-type}

De toegang tot het rapport kan worden beperkt tot een specifieke context of ruimte bieden, bijvoorbeeld een levering, een ontvanger, een selectie van ontvangers, enz. Deze toegang wordt gevormd in de **[!UICONTROL Selection type]** sectie van het **[!UICONTROL Display]** lusje.

![](assets/s_ncs_advuser_report_visibility_4.png)

* **[!UICONTROL Single selection]** : het verslag is alleen toegankelijk wanneer een specifieke entiteit is geselecteerd .
* **[!UICONTROL Multiple selection]** : het rapport is toegankelijk wanneer meerdere entiteiten zijn geselecteerd.
* **[!UICONTROL Global]** : het rapport is toegankelijk via de lijst van beschikbare rapporten in het universum van Rapporten.

### Weergavevolgorde {#display-sequence}

In het **[!UICONTROL Sequence]** veld kunt u een numerieke waarde invoeren die de weergavevolgorde van het rapport in de lijst aangeeft.

Standaard worden rapporten weergegeven op relevantie: Met de waarde die u in dit veld opgeeft, kunt u rapporten sorteren van de meest (hoogste waarde) naar de minst (laagste waarde) relevante.

U kunt de schaal selecteren die u wilt gebruiken op basis van uw behoeften: 1 tot en met 10, 0 tot en met 100, -10 tot en met 10, enz.

### Weergavevoorwaarden {#display-conditions}

U kunt de vertoning van het rapport via een vraag ook bepalen.

![](assets/s_ncs_advuser_report_visibility_5.png)

In het volgende voorbeeld wordt het rapport weergegeven als het hoofdcampagnekanaal e-mail is.

![](assets/s_ncs_advuser_report_visibility_6.png)

Dit betekent dat als het hoofdkanaal van de campagne direct mail is, het rapport niet beschikbaar zal zijn in de campagnerapporten.

### Toegangsvergunning {#access-authorization}

Het rapport kan met andere exploitanten worden gedeeld.

Selecteer de **[!UICONTROL Report shared with other operators]** optie om het rapport toegankelijk te maken. Als deze optie niet wordt geselecteerd, slechts kan de exploitant die het rapport creeerde tot het rapport toegang hebben.

Het rapport kan ook worden gedeeld met specifieke operatoren of groepen operatoren die via het venster voor machtigingen zijn toegevoegd.

![](assets/s_ncs_advuser_report_visibility_8.png)

### Filteropties definiëren {#defining-the-filtering-options}

Het **[!UICONTROL Reports]** universum geeft alle beschikbare rapporten weer in het platform en waarvoor de verbonden operator een toegangsrecht heeft.

Standaard worden ze gesorteerd op relevantie, maar u kunt andere typen filters toepassen: alfabetisch, naar leeftijd, enz.

U kunt de weergave ook filteren op basis van de rapportcategorie:

![](assets/report_ovv_select_type.png)

Om de categorie van een rapport te bepalen, selecteer het via het **[!UICONTROL Display]** lusje, zoals hieronder getoond:

![](assets/report_select_category.png)

Je kunt hier een nieuwe rubriek invoeren en deze toevoegen aan de lijst met beschikbare rubrieken. De overeenkomstige opsomming wordt automatisch bijgewerkt.

## Een koppeling naar een rapport maken {#creating-a-link-to-a-report-}

Het is mogelijk om een rapport toegankelijk te maken via een specifiek knooppunt van de boom, zoals een lijst, een ontvanger, een levering, enz. Hiertoe maakt u gewoon een koppeling naar het betreffende rapport en geeft u de entiteit op waar u het wilt aanbieden.

Als voorbeeld zullen wij een verbinding aan een rapport creëren om het via een lijst van ontvangers toegankelijk te maken.

1. Klik **[!UICONTROL New]** en selecteer **[!UICONTROL Create a link to an existing report]** in de tovenaar van de rapportverwezenlijking.

   ![](assets/s_ncs_advuser_report_wizard_link_01.png)

1. Selecteer het rapport waarnaar u een koppeling wilt maken in de vervolgkeuzelijst. In dit voorbeeld gaan we het rapport **Onderverdeling per land** selecteren.

   ![](assets/s_ncs_advuser_report_wizard_link_02.png)

1. Voer een label in en selecteer het schema. In dit voorbeeld, gaan wij de ontvankelijke lijstlijst selecteren.

   ![](assets/s_ncs_advuser_report_wizard_link_03.png)

   Dit betekent dat het rapport toegankelijk zal zijn via een lijst van ontvangers en dat de statistieken betrekking zullen hebben op de ontvangers in de geselecteerde lijst.

1. Uw rapport opslaan en weergeven.
1. Voer de koppelingssleutel in. In dit geval is dit de buitenlandse sleutel van de koppeling &#39;Mappen&#39;.

   ![](assets/s_ncs_advuser_report_wizard_link_04.png)

1. Publiceer uw rapport.
1. Ga naar een van uw lijsten met ontvangers en klik op de **[!UICONTROL Reports]** koppeling: het rapport dat u zojuist hebt gemaakt, is toegankelijk.

   ![](assets/s_ncs_advuser_report_wizard_link_05.png)

## Voorbeeld van het rapport {#preview-of-the-report}

Alvorens uw rapport te publiceren, zorg ervoor het correct op het **[!UICONTROL Preview]** lusje wordt getoond.

![](assets/s_ncs_advuser_report_preview_01.png)

Als u de voorvertoning van het rapport wilt weergeven, selecteert u de optie **[!UICONTROL Global]** of de **[!UICONTROL Selection]** optie.

Deze twee opties worden geselecteerd gebaseerd op de vertoningsmontages van het rapport. Als de weergave-instelling **[!UICONTROL Global]** is, moet u de **[!UICONTROL Global]** voorvertoningsoptie selecteren. Als de weergave-instellingen worden gebruikt **[!UICONTROL Single selection]** of **[!UICONTROL Multiple selection]** moet de **[!UICONTROL Selection]** voorvertoningsoptie zijn geselecteerd.

Voor meer op dit, verwijs naar de vertoningscontext [van het](#report-display-context)Rapport.

Met specifieke instellingen kunt u fouten beheren. De instelling **_uuid** vindt u in de URL van het rapport. U kunt de instellingen **&amp;_preview** of **&amp;_debug** eraan toevoegen.

Meer informatie over deze instellingen vindt u in het gedeelte Eigenschappen **van webformulieren** definiëren van het hoofdstuk [Webformulieren](../../web/using/about-web-forms.md) .

## Het rapport publiceren {#publishing-the-report}

Publiceren van het rapport is verplicht om deze te delen met andere operatoren en weer te geven in de lijst met beschikbare rapporten (zie ook de weergavecontext [](#report-display-context)Rapport). Deze operatie moet telkens opnieuw worden uitgevoerd wanneer het verslag wordt gewijzigd.

1. Open de publicatiewizard door op **[!UICONTROL Publish]** de werkbalk te klikken.

   ![](assets/s_ncs_advuser_report_publish_01.png)

1. Klik **[!UICONTROL Start]** om te publiceren.

   ![](assets/s_ncs_advuser_report_publish_02.png)

1. Klik op het **[!UICONTROL Enlarge]** pictogram om het rapport in een webbrowser te openen.

