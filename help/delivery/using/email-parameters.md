---
product: campaign
title: E-mailparameters
description: Meer informatie over opties en instellingen die specifiek zijn voor e-maillevering
feature: Email
role: User, Developer, Data Engineer
hide: true
hidefromtoc: true
exl-id: 1bb36e71-9f1a-4553-b266-eca3f48688e2
source-git-commit: b353b562bd2f0b0bd2dfde22c6477ab66d499483
workflow-type: tm+mt
source-wordcount: '903'
ht-degree: 7%

---

# E-mailparameters {#email-parameters}

In deze sectie worden de opties en parameters beschreven die specifiek zijn voor e-maillevering.

## BCC e-mailen {#email-bcc}

Met Adobe Campaign kunt u e-mailberichten op een extern systeem opslaan via BCC door eenvoudig een BCC-e-mailadres toe te voegen aan uw berichtdoel.

Zodra de optie geactiveerd is, wordt een exacte kopie van alle verzonden berichten bewaard voor deze levering.

Voor meer informatie over de configuratie en beste praktijken van BCC E-mail, verwijs naar [ deze sectie ](../../installation/using/email-archiving.md).

>[!NOTE]
>
>E-mail BCC is een optionele mogelijkheid. Controleer uw licentieovereenkomst en neem contact op met uw accountmanager om deze te activeren.

Bij het maken van een nieuwe bezorgings- of leveringssjabloon is E-mail BCC niet standaard ingeschakeld. U moet het manueel op het niveau van de e-maillevering of leveringsmalplaatje toelaten.

>[!NOTE]
>
>Als u E-mail BCC met [ Verbeterde MTA ](sending-with-enhanced-mta.md) gebruikt, wordt deze optie automatisch toegelaten voor alle leveringen.

Voer de onderstaande stappen uit om e-mailblokcode in te schakelen voor een sjabloon voor e-maillevering:

1. Ga naar **[!UICONTROL Campaign Management]** > **[!UICONTROL Deliveries]** of **[!UICONTROL Resources]** > **[!UICONTROL Templates]** > **[!UICONTROL Delivery templates]** .
1. Selecteer de levering van uw keus of dupliceer uit-van-de-doos **E-mail bezorging** malplaatje, dan selecteer het gedupliceerde malplaatje.
1. Klik de **knoop van Eigenschappen**.
1. Selecteer het tabblad **[!UICONTROL Delivery]**. 
1. Controleer de **E-mailBCC** optie. Een kopie van alle verzonden berichten voor elke levering op basis van deze sjabloon wordt verzonden naar het e-mailadres BCC dat is geconfigureerd.

   ![](assets/s_ncs_user_wizard_archiving.png)

>[!NOTE]
>
>Als de e-mails die naar het BCC-adres worden verzonden, worden geopend en doorgeklikt, wordt hiermee rekening gehouden in de **[!UICONTROL Total opens]** - en **[!UICONTROL Clicks]** -analyse, wat tot onjuiste berekeningen kan leiden.

## Berichtindelingen selecteren {#selecting-message-formats}

U kunt de indeling van verzonden e-mailberichten wijzigen. Hiervoor bewerkt u de leveringseigenschappen en klikt u op het tabblad **[!UICONTROL Delivery]** .

![](assets/s_ncs_user_wizard_email_param.png)

Selecteer de indeling van de e-mail in de onderste sectie van het venster:

* **[!UICONTROL Use recipient preferences]** (standaardmodus)

  De berichtindeling wordt gedefinieerd op basis van de gegevens die zijn opgeslagen in het ontvangende profiel en wordt standaard opgeslagen in het veld **[!UICONTROL email format]** (@emailFormat). Als een ontvanger berichten in een bepaalde indeling wenst te ontvangen, wordt deze indeling gebruikt. Als het veld niet is ingevuld, wordt een meerdelig alternatief bericht verzonden (zie hieronder).

* **[!UICONTROL Let recipient mail client choose the most appropriate format]**

  Het bericht bevat beide indelingen: tekst en HTML. Het formaat dat op ontvangst wordt getoond hangt van de configuratie van de de postsoftware van de ontvanger (multipart-alternatief) af.

  >[!IMPORTANT]
  >
  >Deze optie omvat beide versies van het document. Het heeft daarom invloed op de leveringstarieven, omdat de berichtgrootte groter is.

* **[!UICONTROL Send all messages in text format]**

  Het bericht wordt verzonden in tekstformaat. De HTML-indeling wordt niet verzonden, maar wordt alleen voor de spiegel gebruikt wanneer de ontvanger op het bericht klikt.

>[!NOTE]
>
>Voor meer bij het bepalen van de e-mailinhoud, zie [ deze sectie ](defining-the-email-content.md).

## De spiegelpagina genereren {#generating-mirror-page}

De spiegelpagina is een HTML-pagina die online toegankelijk is via een webbrowser. De inhoud is identiek aan de e-mail.

Standaard wordt de spiegelpagina gegenereerd als de koppeling wordt ingevoegd in de inhoud van de e-mail. Voor meer op verpersoonlijkingsbloktoevoeging, verwijs naar [ blokken van de Aanpassing ](personalization-blocks.md).

In de leveringseigenschappen, laat het **[!UICONTROL Mode]** gebied van het **[!UICONTROL Validity]** lusje u de generatiemodus voor deze pagina wijzigen.

![](assets/s_ncs_user_wizard_miror_page_mode.png)

>[!IMPORTANT]
>
>Er moet een HTML-inhoud zijn gedefinieerd voor de levering van de spiegelpagina die moet worden gemaakt.

Naast de standaardmodus zijn ook de volgende opties beschikbaar:

* **[!UICONTROL Force the generation of the mirror page]**: zelfs als er geen koppeling naar de spiegelpagina is ingevoegd in de levering, wordt de spiegelpagina gemaakt.
* **[!UICONTROL Do not generate the mirror page]**: er wordt geen spiegelpagina gegenereerd, zelfs als de koppeling aanwezig is in de levering.
* **[!UICONTROL Generates a mirror page accessible using only the message identifier]**: met deze optie hebt u toegang tot de inhoud van de spiegelpagina, met verpersoonlijkingsinformatie, in het venster van het leveringslogboek. Als u dit wilt doen, klikt u na afloop van de levering op de tab **[!UICONTROL Delivery]** en selecteert u de regel van de ontvanger waarvan u de spiegelpagina wilt weergeven. Klik op de koppeling **[!UICONTROL Display the mirror page for this message...]**.

  ![](assets/s_ncs_user_wizard_miror_page_link.png)

## Tekencodering {#character-encoding}

Op het tabblad **[!UICONTROL SMTP]** van de leveringsparameters kunt u in de sectie **[!UICONTROL Character encoding]** een specifieke codering instellen.

De standaardcodering is UTF-8. Als sommige e-mailproviders van uw ontvangers de standaardcodering UTF-8 niet ondersteunen, kunt u een specifieke codering instellen om de speciale tekens correct weer te geven aan de ontvangers van uw e-mail.

U wilt bijvoorbeeld een e-mail verzenden met Japanse tekens. Om ervoor te zorgen dat alle tekens correct worden weergegeven aan ontvangers in Japan, kunt u een codering gebruiken die de Japanse tekens ondersteunt in plaats van de standaard UTF-8.

Hiervoor selecteert u de optie **[!UICONTROL Force the encoding used for messages]** in de sectie **[!UICONTROL Character encoding]** en kiest u een codering in de vervolgkeuzelijst die wordt weergegeven.

![](assets/s_ncs_user_email_del_properties_smtp_tab_encoding.png)

## Bounce-e-mails beheren {#managing-bounce-emails}

Met het tabblad **[!UICONTROL SMTP]** van de leveringsparameters kunt u het beheer van stuiterende mails configureren.

Door gebrek, worden de teruggestuurde e-mails ontvangen in de [ standaardfoutendoos van het platform ](../../installation/using/deploying-an-instance.md#parameters-for-delivered-emails-parameters-for-delivered-emails), maar u kunt een specifiek foutenadres voor een levering bepalen.

U kunt ook een specifiek adres vanuit dit scherm definiëren om de redenen voor stuiterende berichten te onderzoeken wanneer deze niet automatisch door de toepassing kunnen worden gekwalificeerd. Voor elk van deze gebieden, **voeg gepersonaliseerde gebieden** pictogram toe laat u verpersoonlijkingsparameters toevoegen.

![](assets/s_ncs_user_email_del_properties_smtp_tab.png)

Voor meer bij stuiteren postbeheer, zie [ deze sectie ](understanding-delivery-failures.md#bounce-mail-management).

## SMTP-koppen toevoegen {#adding-smtp-headers}

Het is mogelijk om kopballen SMTP aan uw leveringen toe te voegen. Hiervoor gebruikt u de desbetreffende sectie van het tabblad **[!UICONTROL SMTP]** in de levering.

Het manuscript ingegaan in dit venster moet één kopbal per lijn in de volgende vorm van verwijzingen voorzien: **naam:waarde**.

Waarden worden indien nodig automatisch gecodeerd.

>[!IMPORTANT]
>
>Het toevoegen van een manuscript voor het opnemen van extra kopballen SMTP is gereserveerd voor gevorderde gebruikers.
>
>De syntaxis van dit script moet voldoen aan de vereisten van dit type content: geen ongebruikte ruimte, geen lege regel, enz.
