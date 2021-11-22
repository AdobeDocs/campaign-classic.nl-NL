---
product: campaign
title: E-mailparameters configureren in Adobe Campaign Classic
description: Meer informatie over opties en instellingen die specifiek zijn voor e-maillevering.
audience: delivery
content-type: reference
topic-tags: sending-emails
exl-id: 1bb36e71-9f1a-4553-b266-eca3f48688e2
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '905'
ht-degree: 8%

---

# E-mailparameters {#email-parameters}

![](../../assets/common.svg)

In deze sectie worden de opties en parameters beschreven die specifiek zijn voor e-maillevering.

## BCC e-mailen {#email-bcc}

Met Adobe Campaign kunt u e-mailberichten op een extern systeem opslaan via BCC door eenvoudig een BCC-e-mailadres toe te voegen aan uw berichtdoel.

Zodra de optie geactiveerd is, wordt een exacte kopie van alle verzonden berichten bewaard voor deze levering.

Raadpleeg voor meer informatie over de BCC-configuratie en aanbevolen procedures voor e-mail de volgende bronnen: [deze sectie](../../installation/using/email-archiving.md).

>[!NOTE]
>
>E-mail BCC is een optionele mogelijkheid. Controleer uw licentieovereenkomst en neem contact op met uw accountmanager om deze te activeren.

Bij het maken van een nieuwe bezorgings- of leveringssjabloon is E-mail BCC niet standaard ingeschakeld. U moet het manueel op het niveau van de e-maillevering of leveringsmalplaatje toelaten.

>[!NOTE]
>
>Als u BCC via e-mail gebruikt met Enhanced MTA, wordt deze optie automatisch ingeschakeld voor alle leveringen.

Voer de onderstaande stappen uit om e-mailblokcode in te schakelen voor een sjabloon voor e-maillevering:

1. Ga naar **[!UICONTROL Campaign Management]** > **[!UICONTROL Deliveries]** of **[!UICONTROL Resources]** > **[!UICONTROL Templates]** > **[!UICONTROL Delivery templates]**.
1. Selecteer de levering van uw keuze of dupliceer de uit-van-de-doos **E-maillevering** selecteert u vervolgens de gedupliceerde sjabloon.
1. Klik op de knop **Eigenschappen** knop.
1. Selecteer het tabblad **[!UICONTROL Delivery]**. 
1. Controleer de **BCC e-mailen** optie. Een kopie van alle verzonden berichten voor elke levering op basis van deze sjabloon wordt verzonden naar het e-mailadres BCC dat is geconfigureerd.

   ![](assets/s_ncs_user_wizard_archiving.png)

>[!NOTE]
>
>Als de e-mails die naar het BCC-adres worden verzonden worden geopend en als hierop wordt geklikt, wordt hiermee rekening gehouden in het dialoogvenster **[!UICONTROL Total opens]** en **[!UICONTROL Clicks]** van de send analyse, die sommige misberekeningen zou kunnen veroorzaken.

## Berichtindelingen selecteren {#selecting-message-formats}

U kunt de indeling van verzonden e-mailberichten wijzigen. Hiervoor bewerkt u de leveringseigenschappen en klikt u op de knop **[!UICONTROL Delivery]** tab.

![](assets/s_ncs_user_wizard_email_param.png)

Selecteer de indeling van de e-mail in de onderste sectie van het venster:

* **[!UICONTROL Use recipient preferences]** (standaardmodus)

   De berichtindeling wordt gedefinieerd op basis van de gegevens die zijn opgeslagen in het ontvangende profiel en wordt standaard opgeslagen in het dialoogvenster **[!UICONTROL email format]** veld (@emailFormat). Als een ontvanger berichten in een bepaalde indeling wenst te ontvangen, wordt deze indeling gebruikt. Als het veld niet is ingevuld, wordt een meerdelig alternatief bericht verzonden (zie hieronder).

* **[!UICONTROL Let recipient mail client choose the most appropriate format]**

   Het bericht bevat beide indelingen: tekst en HTML. Het formaat dat op ontvangst wordt getoond hangt van de configuratie van de postsoftware van de ontvanger (multipart-alternatief) af.

   >[!IMPORTANT]
   >
   >Deze optie omvat beide versies van het document. Het heeft daarom invloed op de leveringstarieven, omdat de berichtgrootte groter is.

* **[!UICONTROL Send all messages in text format]**

   Het bericht wordt verzonden in tekstformaat. De indeling HTML wordt niet verzonden, maar wordt alleen voor de spiegelpagina gebruikt wanneer de ontvanger op het bericht klikt.

>[!NOTE]
>
>Voor meer informatie over het definiëren van de e-mailinhoud raadpleegt u [deze sectie](defining-the-email-content.md).

## De spiegelpagina genereren {#generating-mirror-page}

De spiegelpagina is een HTML-pagina die online toegankelijk is via een webbrowser. De inhoud is identiek aan de e-mail.

Standaard wordt de spiegelpagina gegenereerd als de koppeling wordt ingevoegd in de inhoud van de e-mail. Voor meer op verpersoonlijkingsblokkeringen, verwijs naar [Aanpassingsblokken](personalization-blocks.md).

In de leveringseigenschappen **[!UICONTROL Mode]** van het **[!UICONTROL Validity]** kunt u de generatiemodus voor deze pagina wijzigen.

![](assets/s_ncs_user_wizard_miror_page_mode.png)

>[!IMPORTANT]
>
>Een inhoud van HTML moet voor de levering voor de spiegelpagina worden bepaald om te creëren.

Naast de standaardmodus zijn ook de volgende opties beschikbaar:

* **[!UICONTROL Force the generation of the mirror page]**: zelfs als geen verbinding aan de spiegelpagina in de levering wordt opgenomen, zal de spiegelpagina worden gecreeerd.
* **[!UICONTROL Do not generate the mirror page]**: er wordt geen spiegelpagina gegenereerd, zelfs niet als de koppeling aanwezig is in de levering.
* **[!UICONTROL Generates a mirror page accessible using only the message identifier]**: deze optie laat u tot de inhoud van de spiegelpagina, met verpersoonlijkingsinformatie, in het venster van het leveringslogboek toegang hebben. Als u dit wilt doen, klikt u na afloop van de levering op de knop **[!UICONTROL Delivery]** en selecteert u de regel van de ontvanger waarvan u de spiegelpagina wilt weergeven. Klik op de koppeling **[!UICONTROL Display the mirror page for this message...]**.

   ![](assets/s_ncs_user_wizard_miror_page_link.png)

## Tekencodering {#character-encoding}

In de **[!UICONTROL SMTP]** tabblad van de leveringsparameters, **[!UICONTROL Character encoding]** kunt u een specifieke codering instellen.

De standaardcodering is UTF-8. Als sommige e-mailproviders van uw ontvangers de standaardcodering UTF-8 niet ondersteunen, kunt u een specifieke codering instellen om de speciale tekens correct weer te geven aan de ontvangers van uw e-mail.

U wilt bijvoorbeeld een e-mail verzenden met Japanse tekens. Om ervoor te zorgen dat alle tekens correct worden weergegeven aan ontvangers in Japan, kunt u een codering gebruiken die de Japanse tekens ondersteunt in plaats van de standaard UTF-8.

Selecteer hiervoor de optie **[!UICONTROL Force the encoding used for messages]** in de **[!UICONTROL Character encoding]** en kiest u een codering in de vervolgkeuzelijst die wordt weergegeven.

![](assets/s_ncs_user_email_del_properties_smtp_tab_encoding.png)

## Bounce-e-mails beheren {#managing-bounce-emails}

De **[!UICONTROL SMTP]** tabblad van de leveringsparameters kunt u het beheer van stuiterende berichten configureren.

Standaard worden teruggestuurde e-mailberichten ontvangen in het standaardfoutvak van het platform, maar u kunt een specifiek foutadres voor een levering definiëren.

U kunt ook een specifiek adres vanuit dit scherm definiëren om de redenen voor stuiterende berichten te onderzoeken wanneer deze niet automatisch door de toepassing kunnen worden gekwalificeerd. Voor elk van deze velden wordt **Aangepaste velden toevoegen** kunt u personalisatieparameters toevoegen.

![](assets/s_ncs_user_email_del_properties_smtp_tab.png)

Zie voor meer informatie over stuiterend mailbeheer [deze sectie](understanding-delivery-failures.md#bounce-mail-management).

## SMTP-koppen toevoegen {#adding-smtp-headers}

Het is mogelijk om kopballen SMTP aan uw leveringen toe te voegen. Hiervoor gebruikt u de desbetreffende sectie van de **[!UICONTROL SMTP]** in de levering.

Het script dat in dit venster wordt ingevoerd, moet in het volgende formulier verwijzen naar één koptekst per regel: **name:value**.

Waarden worden indien nodig automatisch gecodeerd.

>[!IMPORTANT]
>
>Het toevoegen van een script voor het opnemen van extra SMTP-kopteksten is gereserveerd voor gevorderde gebruikers.
>
>De syntaxis van dit script moet voldoen aan de vereisten van dit type content: geen ongebruikte ruimte, geen lege regel, enz.
