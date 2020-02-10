---
title: Filterregels
seo-title: Filterregels
description: Filterregels
seo-description: null
page-status-flag: never-activated
uuid: 24238a99-1f0f-4d04-9807-557ec2a5ba16
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: campaign-optimization
discoiquuid: 0d50826e-2211-4c3b-8413-ca1453bba6c4
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 209ac4d81d2d27c264ee6b288bcb7fcb1900ffc5

---


# Filterregels{#filtering-rules}

Met filterregels kunt u de berichten definiëren die u wilt uitsluiten op basis van criteria die in een query zijn gedefinieerd. Deze regels zijn gekoppeld aan een doelgerichte dimensie.

Filterregels kunnen worden gekoppeld aan andere soorten regels (controle, druk, enz.) in typologieën, of gegroepeerd in een specifieke **Filtrerende** typologie. Raadpleeg [Filtertypologie](#creating-and-using-a-filtering-typology)voor meer informatie hierover.

## Filterregels maken {#creating-a-filtering-rule}

Bijvoorbeeld, kunt u uw nieuwsbrief abonnees filtreren om mededelingen te verhinderen worden verzonden naar ontvangers die onderage zijn.

Pas de volgende stappen toe om dit filter te definiëren:

1. Maak een **[!UICONTROL Filtering]** typologieregel die op alle communicatiekanalen van toepassing is.

   ![](assets/campaign_opt_create_filter_01.png)

1. Wijzig de standaarddoeldimensie en selecteer de abonnementen (**nms:abonnement**).

   ![](assets/campaign_opt_create_filter_02.png)

1. Maak het filter met de **[!UICONTROL Edit the query from the targeting dimension...]** koppeling.

   ![](assets/campaign_opt_create_filter_03.png)

1. Koppel deze regel aan een campagnetypologie en sla deze op.

   ![](assets/campaign_opt_create_filter_04.png)

Wanneer deze regel in een levering wordt gebruikt, worden minderjarige abonnees automatisch uitgesloten. Een specifiek bericht geeft regeltoepassing aan:

![](assets/campaign_opt_create_filter_05.png)

## Een filterregel conditioneren {#conditioning-a-filtering-rule}

U kunt het toepassingsgebied van de het filtreren regel beperken die op de verbonden levering of leveringsoverzicht wordt gebaseerd.

Hiervoor gaat u naar het **[!UICONTROL General]** tabblad van de typologieregel, selecteert u het type beperking dat u wilt toepassen en maakt u het filter, zoals hieronder wordt weergegeven:

![](assets/campaign_opt_create_filter_06.png)

In dit geval wordt de regel, zelfs als deze aan alle leveringen is gekoppeld, alleen toegepast op leveringen die aan de criteria van het gedefinieerde filter voldoen.

>[!NOTE]
>
>Typologieën en filterregels kunnen in een werkschema, in de **[!UICONTROL Delivery outline]** activiteit worden gebruikt. Zie [deze sectie](../../workflow/using/delivery-outline.md)voor meer informatie.

## Filtertypologie maken en gebruiken {#creating-and-using-a-filtering-typology}

U kunt **[!UICONTROL Filtering]** typologieën maken: zij bevatten alleen filterregels .

![](assets/campaign_opt_create_typo_filtering.png)

Deze specifieke typologieën kunnen aan een levering worden verbonden wanneer het doel wordt geselecteerd: in de leveringstovenaar, klik de **[!UICONTROL To]** verbinding, dan klik de **[!UICONTROL Exclusions]** tabel.

![](assets/campaign_opt_apply_typo_filtering.png)

Selecteer vervolgens de filtertypologie die op de levering moet worden toegepast. Klik hiertoe op de **[!UICONTROL Add]** knop en selecteer de typologieën die u wilt toepassen.

U kunt filterregels ook rechtstreeks via dit tabblad koppelen, zonder ze te groeperen in een typologie. Gebruik hiervoor de onderste sectie van het venster.

![](assets/campaign_opt_select_typo_filtering.png)

>[!NOTE]
>
>* Alleen typologieën en filterregels zijn beschikbaar in het selectievenster.
>* Deze configuraties kunnen in het leveringsmalplaatje worden bepaald dat automatisch op alle nieuwe die leveringen worden toegepast worden gecreeerd gebruikend het malplaatje.
>



## Uitsluitingsregels voor standaardlevering {#default-deliverability-exclusion-rules}

Twee het filtreren regels zijn beschikbaar door gebrek: **[!UICONTROL Exclude addresses]** ( **[!UICONTROL addressExclusions]** ) en **[!UICONTROL Exclude domains]** ( **[!UICONTROL domainExclusions]** ) . Tijdens de e-mailanalyse, vergelijken deze regels de ontvankelijke e-mailadressen met de verboden adressen of domeinnamen in een gecodeerde globale suppressielijst die in de leveringsinstantie wordt beheerd. Als er een gelijke is, wordt het bericht niet verzonden naar die ontvanger.

Dit om te voorkomen dat ze op de zwarte lijst worden gezet vanwege kwaadwillige activiteiten, met name het gebruik van een Spamtrap. Als bijvoorbeeld een spamtrap wordt gebruikt om zich te abonneren via een van uw webformulieren, wordt automatisch een bevestigingsbericht verzonden naar die spamtrap. Hierdoor wordt uw adres automatisch op de zwarte lijst gezet.

>[!NOTE]
>
>De adressen en domeinnamen in de globale suppressielijst worden verborgen. Alleen het aantal uitgesloten ontvangers wordt vermeld in de logboeken van de leveringsanalyse.

