---
product: campaign
title: Filterregels
description: Leer hoe u filterregels kunt gebruiken in Adobe Campaign
role: User, Data Engineer
feature: Typology Rules, Campaigns
hide: true
hidefromtoc: true
exl-id: a4d12445-5680-4704-9c67-e43e0ea6631b
source-git-commit: 4f809011a8b4cb3803c4e8151e358e5fd73634e4
workflow-type: tm+mt
source-wordcount: '510'
ht-degree: 2%

---

# Filterregels{#filtering-rules}

Met filterregels kunt u de berichten definiëren die u wilt uitsluiten op basis van criteria die in een query zijn gedefinieerd. Deze regels zijn gekoppeld aan een doelgerichte dimensie.

Het filtreren van regels kan met andere soorten regels (controle, druk, enz.) in typologieën worden verbonden, of in een specifieke **het Filtreren** typologie worden gegroepeerd. Voor meer op dit, verwijs naar [&#x200B; Creërend en gebruikend een het filtreren typologie &#x200B;](#creating-and-using-a-filtering-typology).

## Een filterregel maken {#creating-a-filtering-rule}

Bijvoorbeeld, kunt u uw nieuwsbrief abonnees filtreren om mededelingen te verhinderen worden verzonden naar ontvangers die onderage zijn.

Pas de volgende stappen toe om dit filter te definiëren:

1. Maak een **[!UICONTROL Filtering]** typologieregel die op alle communicatiekanalen van toepassing is.

   ![](assets/campaign_opt_create_filter_01.png)

1. Verander het gebrek richtend afmeting en selecteer de abonnementen (**nms:abonnement**).

   ![](assets/campaign_opt_create_filter_02.png)

1. Maak het filter met de koppeling **[!UICONTROL Edit the query from the targeting dimension...]** .

   ![](assets/campaign_opt_create_filter_03.png)

1. Koppel deze regel aan een campagnetypologie en sla deze op.

   ![](assets/campaign_opt_create_filter_04.png)

Wanneer deze regel in een levering wordt gebruikt, worden minderjarige abonnees automatisch uitgesloten. Een specifiek bericht geeft regeltoepassing aan:

![](assets/campaign_opt_create_filter_05.png)

## Voorwaarde een filterregel {#conditioning-a-filtering-rule}

U kunt het toepassingsgebied van de het filtreren regel beperken die op de verbonden levering of leveringsoverzicht wordt gebaseerd.

Hiervoor gaat u naar het tabblad **[!UICONTROL General]** van de typologieregel, selecteert u het type beperking dat u wilt toepassen en maakt u het filter, zoals hieronder wordt weergegeven:

![](assets/campaign_opt_create_filter_06.png)

In dit geval wordt de regel, zelfs als deze aan alle leveringen is gekoppeld, alleen toegepast op leveringen die aan de criteria van het gedefinieerde filter voldoen.

>[!NOTE]
>
>Typologieën en filterregels kunnen worden gebruikt in een workflow, in de **[!UICONTROL Delivery outline]** -activiteit. Raadpleeg [deze sectie](../../workflow/using/delivery-outline.md) voor meer informatie.

## Filtertypologie maken en gebruiken {#creating-and-using-a-filtering-typology}

U kunt **[!UICONTROL Filtering]** -typologieën maken: deze bevatten alleen filterregels.

![](assets/campaign_opt_create_typo_filtering.png)

Deze specifieke typologieën kunnen worden gekoppeld aan een levering wanneer het doel is geselecteerd: klik in de leveringsassistent op de koppeling **[!UICONTROL To]** en klik vervolgens op het tabblad **[!UICONTROL Exclusions]** .

![](assets/campaign_opt_apply_typo_filtering.png)

Selecteer vervolgens de filtertypologie die op de levering moet worden toegepast. Klik hiertoe op de knop **[!UICONTROL Add]** en selecteer de typologieën die u wilt toepassen.

U kunt filterregels ook rechtstreeks via dit tabblad koppelen, zonder ze te groeperen in een typologie. Gebruik hiervoor de onderste sectie van het venster.

![](assets/campaign_opt_select_typo_filtering.png)

>[!NOTE]
>
>Alleen typologieën en filterregels zijn beschikbaar in het selectievenster.
>
>Deze configuraties kunnen in het leveringsmalplaatje worden bepaald dat automatisch op alle nieuwe die leveringen worden toegepast worden gecreeerd gebruikend het malplaatje.
>

## Uitsluitingsregels voor standaardlevering {#default-deliverability-exclusion-rules}

Er zijn standaard twee filterregels beschikbaar: **[!UICONTROL Exclude addresses]** ( **[!UICONTROL addressExclusions]** ) en **[!UICONTROL Exclude domains]** ( **[!UICONTROL domainExclusions]** ). Tijdens de e-mailanalyse, vergelijken deze regels de ontvankelijke e-mailadressen met de verboden adressen of domeinnamen in een gecodeerde globale suppressielijst die in de leveringsinstantie wordt beheerd. Als er een gelijke is, wordt het bericht niet verzonden naar die ontvanger.

Hiermee voorkomt u dat de lijst van gewezen personen wordt toegevoegd vanwege kwaadwillige activiteiten, met name het gebruik van een Spamtrap. Als bijvoorbeeld een spamtrap wordt gebruikt om zich te abonneren via een van uw webformulieren, wordt automatisch een bevestigingsbericht verzonden naar die spamtrap. Hierdoor wordt uw adres automatisch toegevoegd aan de lijst van gewezen personen.

>[!NOTE]
>
>De adressen en domeinnamen in de globale suppressielijst worden verborgen. Alleen het aantal uitgesloten ontvangers wordt vermeld in de logboeken van de leveringsanalyse.
