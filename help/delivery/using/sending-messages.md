---
solution: Campaign Classic
product: campaign
title: Een e-mail verzenden met Adobe Campaign Classic
description: Meer informatie over parameters voor e-maillevering
audience: delivery
content-type: reference
topic-tags: sending-emails
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '739'
ht-degree: 8%

---


# Een e-mail verzenden{#sending-an-email}

Klik om uw e-mail goed te keuren en deze te verzenden naar de ontvangers van de levering die wordt gemaakt. **[!UICONTROL Send]**.

Het gedetailleerde proces voor het valideren en verzenden van een levering wordt in de volgende secties weergegeven:

* [De levering valideren](../../delivery/using/steps-validating-the-delivery.md)
* [De levering verzenden](../../delivery/using/steps-sending-the-delivery.md)

In de onderstaande secties worden de parameters beschreven die specifiek zijn voor het verzenden van e-mails.

## BCC e-mailen {#archiving-emails}

Met Adobe Campaign kunt u e-mailberichten op een extern systeem opslaan via BCC door eenvoudig een BCC-e-mailadres toe te voegen aan uw berichtdoel. Zodra de optie geactiveerd is, wordt een exacte kopie van alle verzonden berichten bewaard voor deze levering.

Raadpleeg [deze sectie](../../installation/using/email-archiving.md)voor meer informatie over de BCC-configuratie en best practices voor e-mail.

>[!NOTE]
>
>E-mail BCC is een optionele mogelijkheid. Controleer uw licentieovereenkomst en neem contact op met uw accountmanager om deze te activeren.

Bij het maken van een nieuwe bezorgings- of leveringssjabloon is E-mail BCC niet standaard ingeschakeld. U moet het manueel op het niveau van de e-maillevering of leveringsmalplaatje toelaten.

Voer de onderstaande stappen uit om e-mailblokcode in te schakelen voor een sjabloon voor e-maillevering:

1. Ga naar **[!UICONTROL Campaign Management]** > **[!UICONTROL Deliveries]** of **[!UICONTROL Resources]** > **[!UICONTROL Templates]** > **[!UICONTROL Delivery templates]**.
1. Selecteer de levering van uw keuze of dupliceer de uit-van-de-doos sjabloon voor **e-maillevering** en selecteer vervolgens de gedupliceerde sjabloon.
1. Click the **Properties** button.
1. Selecteer het tabblad **[!UICONTROL Delivery]**. 
1. Schakel de optie **BCC** e-mailen in. Een kopie van alle verzonden berichten voor elke levering op basis van deze sjabloon wordt verzonden naar het e-mailadres BCC dat is geconfigureerd.

   ![](assets/s_ncs_user_wizard_archiving.png)

   >[!NOTE]
   >
   >Als de e-mails die naar het BCC-adres worden verzonden worden geopend en doorgeklikt, wordt hiermee rekening gehouden in de analyse **[!UICONTROL Total opens]** en **[!UICONTROL Clicks]** de verzendanalyse, wat tot onjuiste berekeningen kan leiden.

## De spiegelpagina genereren {#generating-the-mirror-page}

De spiegelpagina is een HTML-pagina die online toegankelijk is via een webbrowser. De inhoud is identiek aan de e-mail.

Standaard wordt de spiegelpagina gegenereerd als de koppeling wordt ingevoegd in de inhoud van de e-mail. Voor meer op verpersoonlijkingsblokkeringen toevoeging, verwijs naar de blokken [van de](../../delivery/using/personalization-blocks.md)Personalisatie.

In de leveringseigenschappen, laat het **[!UICONTROL Mode]** gebied van het **[!UICONTROL Validity]** lusje u de generatiemodus voor deze pagina wijzigen.

![](assets/s_ncs_user_wizard_miror_page_mode.png)

>[!CAUTION]
>
>Er moet een HTML-inhoud zijn gedefinieerd voordat de spiegelpagina kan worden gemaakt.

Naast de standaardmodus zijn ook de volgende opties beschikbaar:

* **[!UICONTROL Force the generation of the mirror page]** : zelfs als geen verbinding aan de spiegelpagina in de levering wordt opgenomen, zal de spiegelpagina worden gecreeerd.
* **[!UICONTROL Do not generate the mirror page]** : er wordt geen spiegelpagina gegenereerd, zelfs niet als de koppeling aanwezig is in de levering.
* **[!UICONTROL Generates a mirror page accessible using only the message identifier]** : deze optie laat u tot de inhoud van de spiegelpagina, met verpersoonlijkingsinformatie, in het venster van het leveringslogboek toegang hebben. Als u dit wilt doen, klikt u na afloop van de levering op het **[!UICONTROL Delivery]** tabblad en selecteert u de regel van de ontvanger waarvan u de spiegelpagina wilt weergeven. Klik op de **[!UICONTROL Display the mirror page for this message...]** koppeling.

   ![](assets/s_ncs_user_wizard_miror_page_link.png)

## Bounce-e-mails beheren {#managing-bounce-emails}

Het **[!UICONTROL SMTP]** lusje van de leveringsparameters laat u het beheer van stuitende berichten vormen.

![](assets/s_ncs_user_email_del_properties_smtp_tab.png)

Standaard worden teruggestuurde e-mailberichten ontvangen in het standaardfoutvak van het platform, maar u kunt een specifiek foutadres voor een levering definiëren.

U kunt ook een specifiek adres vanuit dit scherm definiëren om de redenen voor stuiterende berichten te onderzoeken wanneer deze niet automatisch door de toepassing kunnen worden gekwalificeerd. Voor elk van deze velden kunt u met het pictogram &#39;Aangepaste velden toevoegen&#39; personalisatieparameters toevoegen.

## Tekencodering {#character-encoding}

Op het **[!UICONTROL SMTP]** tabblad van de leveringsparameters kunt u in de **[!UICONTROL Character encoding]** sectie een specifieke codering instellen.

De standaardcodering is UTF-8. Als sommige e-mailproviders van uw ontvangers de standaardcodering UTF-8 niet ondersteunen, kunt u een specifieke codering instellen om de speciale tekens correct weer te geven aan de ontvangers van uw e-mail.

U wilt bijvoorbeeld een e-mail verzenden met Japanse tekens. Om ervoor te zorgen dat alle tekens correct worden weergegeven aan ontvangers in Japan, kunt u een codering gebruiken die de Japanse tekens ondersteunt in plaats van de standaard UTF-8.

Hiervoor selecteert u de **[!UICONTROL Force the encoding used for messages]** optie in de **[!UICONTROL Character encoding]** sectie en kiest u een codering in de vervolgkeuzelijst die wordt weergegeven.

![](assets/s_ncs_user_email_del_properties_smtp_tab_encoding.png)

## SMTP-koppen toevoegen {#adding-smtp-headers}

Het is mogelijk om kopballen SMTP aan uw leveringen toe te voegen. Hiervoor gebruikt u de desbetreffende sectie van het **[!UICONTROL SMTP]** tabblad in de levering.

The script entered in this window must reference one header per line in the following form: **name:value**.

Waarden worden indien nodig automatisch gecodeerd.

>[!CAUTION]
>
>Het toevoegen van een script voor het opnemen van extra SMTP-kopteksten is gereserveerd voor gevorderde gebruikers.
>
>De syntaxis van dit script moet voldoen aan de vereisten van dit type content: geen ongebruikte ruimte, geen lege regel, enz.
