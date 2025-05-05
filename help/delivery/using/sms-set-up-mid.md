---
product: campaign
title: Campagne-sms-kanaal configureren op een mid-sourcing-infrastructuur
description: Meer informatie over het configureren van het sms-kanaal in Campaign op een mid-sourcing-infrastructuur
feature: SMS
role: User, Developer, Admin
level: Experienced
exl-id: 6987cb5e-8821-4619-b0e4-f0fad3355bfb
source-git-commit: 2bfcec5eaa1145cfb88adfa9c8b2f72ee3cd9469
workflow-type: tm+mt
source-wordcount: '981'
ht-degree: 8%

---

# SMS-kanaal configureren op een mid-sourcing infrastructuur {#setting-up-sms-channel}

Om naar een mobiele telefoon met midservers te verzenden, hebt u het volgende nodig:

1. Een exploitant van SMS die op de middelste server wordt gecreeerd voor de externe rekening van SMS die op de server van de Marketing wordt gecreeerd.

1. Een extern account op de Marketing-server, waarmee de kanaal- en leveringsmodus worden opgegeven.

1. Een extern account op de Mid-server, met details over de connector en het berichttype.

1. Een leveringssjabloon die verwijst naar het externe account om het verzendproces te stroomlijnen.

>[!NOTE]
>
> Voor sms-leveringen moet de typologie een specifieke sms-affiniteit gebruiken die is gemaakt in **één** speciale applicatieservercontainer. [Meer informatie](../../installation/using/configure-delivery-settings.md#managing-outbound-smtp-traffic-with-affinities)

## Creëer de SMS-operator op de Mid-server {#create-sms-operator}

Om het configuratieproces te beginnen, moet u een exploitant van SMS op de middelste-server specifiek voor de externe rekening tot stand brengen.

>[!IMPORTANT]
>
>Voor elke SMS-connector is een unieke SMS-operator vereist.

1. Klik in het knooppunt **[!UICONTROL Administration]** > **[!UICONTROL Access management]** > **[!UICONTROL Operators node]** van de structuur op het pictogram **[!UICONTROL New]** .

   ![](assets/sms_operator_mid_3.png)

1. Geef de gebruikersgegevens **[!UICONTROL Identification parameters]** op, inclusief hun aanmeldingsgegevens, wachtwoord en naam. De aanmelding en het wachtwoord zijn nodig om de operator op veilige wijze aan te melden bij Adobe Campaign.

   De **[!UICONTROL Name (login)]** moet later worden gebruikt om uw externe SMPP-account in de mediaserver een naam te geven.

   ![](assets/sms_operator_mid_1.png)

1. Selecteer de toestemmingen aan de exploitant in de sectie van de toegangsrechten van de Exploitant worden verleend die.

   Als u rechten wilt toewijzen aan de operator, klikt u op de knop **[!UICONTROL Add]** boven de lijst met rechten. Selecteer vervolgens een **[!UICONTROL Operator group]** of **[!UICONTROL Named rights]** in de lijst met beschikbare groepen.

   ![](assets/sms_operator_mid_2.png)

1. Klik op **[!UICONTROL Save]** om het maken van de operator te voltooien. Het profiel is nu opgenomen in de lijst met bestaande operatoren.

## Een externe SMS-account maken op de marketingserver {#create-accound-mkt}

Om een SMS te versturen naar een mobiele telefoon met Mid-servers, moet je eerst je SMS externe account aanmaken op de Marketing server.

1. Klik in het **[!UICONTROL Platform]** > **[!UICONTROL External accounts]** knooppunt van de boom op het **[!UICONTROL New]** pictogram.

   ![](assets/mid_external_account_2.png)

1. Typ uw **[!UICONTROL Label]** en **[!UICONTROL Internal name]**. Merk op dat de interne naam later moet worden gebruikt om uw SMPP externe account in de Mid-server een naam te geven.

1. Definieer het accounttype als **[!UICONTROL Routing]** , het kanaal als **[!UICONTROL Mobile (SMS)]** en de leveringsmodus als **[!UICONTROL Mid-sourcing]** .

   ![](assets/mid_external_account_1.png)

1. Geef op het tabblad **[!UICONTROL Mid-Sourcing]** de parameters voor de serververbinding voor de midsourcing op.

   Voer de gegevens van de [eerder gemaakte SMS-connector](#create-sms-operator) in de **[!UICONTROL Account]** velden en **[!UICONTROL Password]** in.

   ![](assets/mid_external_account_7.png)

1. Bevestig uw configuratie door op **[!UICONTROL Test the connection]**.

1. Klik op **[!UICONTROL Save]**.

## Maak een SMPP extern account aan op de Mid-server {#creating-smpp-mid}

>[!IMPORTANT]
>
>Het gebruik van hetzelfde account en wachtwoord voor meerdere externe sms-accounts kan leiden tot conflicten en overlapping tussen de accounts. Raadpleeg de pagina[&#128279;](troubleshooting-sms.md#external-account-conflict) voor het oplossen van problemen met sms.

Zodra u met succes uw externe rekening van SMS op de server van de Marketing hebt opgezet, is de volgende stap uw externe rekening SMPP op de middentserver te vestigen.

Voor meer informatie over het protocol en de montages van SMS, verwijs naar deze [ pagina ](sms-protocol.md).

Hiervoor voert u de volgende stappen uit:

1. Klik in het knooppunt **[!UICONTROL Platform]** > **[!UICONTROL External accounts]** van de structuur op het pictogram **[!UICONTROL New]** .

1. Typ uw **[!UICONTROL Label]** en **[!UICONTROL Internal name]** in.

   >[!WARNING]
   >
   >Wanneer u een **[!UICONTROL Internal name]** toewijst, moet u de opgegeven naamgevingsconventie volgen:
   > </br>`SMS Operator Name_Internal Name of the Marketing SMS external account`

   ![](assets/mid_external_account_6.png)

1. Bepaal het accounttype als **Verpletterend**, het kanaal als **Mobiel (SMS)**, en de leveringswijze als **bulklevering**.

   ![](assets/mid_external_account_3.png)

1. Schakel het selectievakje **[!UICONTROL Enabled]** in.

1. Selecteer op het tabblad **[!UICONTROL Mobile]** **[!UICONTROL Extended generic SMPP]** in de vervolgkeuzelijst **[!UICONTROL Connector]** .

   ![](assets/mid_external_account_4.png)

1. Met de optie **[!UICONTROL Enable verbose SMPP traces in the log file]** kunt u al het SMPP-verkeer in logbestanden dumpen. Deze optie zou slechts moeten worden toegelaten om de schakelaar problemen op te lossen en met het verkeer te vergelijken dat door de leverancier wordt gezien.

1. Neem contact op met uw SMS-serviceprovider die u uitleg geeft over het invullen van de verschillende externe accountvelden op het tabblad **[!UICONTROL Connection settings]** .

   Neem vervolgens contact op met uw provider, afhankelijk van de gekozen provider, die u de waarde zal geven om het veld in **[!UICONTROL SMSC implementation name]** te voeren.

   U kunt het aantal verbindingen aan de leverancier per MTA kind bepalen. De standaardwaarde is 1.

1. Standaard voldoet het aantal tekens in een SMS aan de GSM-standaarden.

   Sms-berichten met gsm-codering mogen maximaal 160 tekens bevatten of 153 tekens per sms voor berichten die in meerdere delen worden verzonden.

   >[!NOTE]
   >
   >Bepaalde tekens tellen als twee tekens (accolades, vierkante haken, het euroteken, enz.).
   >
   >De lijst van beschikbare karakters GSM wordt voorgesteld in [ deze sectie ](sms-set-up.md#about-character-transliteration).

   U kunt ook tekentransliteratie autoriseren door het desbetreffende vak in te schakelen.

   ![](assets/mid_external_account_5.png)

1. Op het tabblad **[!UICONTROL Throughput and delays]** kunt u de maximale doorvoer van uitgaande berichten (&quot;MT&quot;, Mobile Terminated) in MT per seconde opgeven. Als u ‘0’ invoert in het overeenkomstige veld, is de doorvoer onbeperkt.

   De waarden van alle velden die corresponderen met een tijdsduur, moeten in seconden worden ingevuld.

1. Op het tabblad **[!UICONTROL Mapping of encodings]** kunt u coderingen definiëren.

   Raadpleeg [deze sectie](sms-set-up.md#about-text-encodings) voor meer informatie.

1. Op het tabblad **[!UICONTROL SMSC specificities]** is de optie **[!UICONTROL Send full phone number]** standaard uitgeschakeld. Laat het niet toe als u het protocol wilt respecteren SMPP en slechts cijfers naar de server van de leverancier van SMS (SMSC) overbrengen.

   Aangezien bepaalde providers het gebruik van het voorvoegsel &#39;+&#39; vereisen, wordt u echter geadviseerd contact op te nemen met uw provider en wordt u aangeraden deze optie indien nodig in te schakelen.

   Met het selectievakje **[!UICONTROL Enable TLS over SMPP]** kunt u SMPP-verkeer coderen. Raadpleeg [deze pagina](sms-protocol.md) voor meer informatie.

1. Als u een **[!UICONTROL Extended generic SMPP]** connector configureert, kunt u automatische antwoorden instellen.

   Raadpleeg [deze sectie](sms-set-up.md#automatic-reply) voor meer informatie.

## Het bezorgingssjabloon wijzigen {#changing-the-delivery-template}

Adobe Campaign biedt een mobiele leveringssjabloon in het knooppunt **[!UICONTROL Resources > Templates > Delivery templates]** . Raadpleeg voor meer informatie hierover de [sectie Over sjablonen](about-templates.md) .

Om berichten door het kanaal van SMS te verzenden, moet u een malplaatje creëren dat een verwijzing naar de kanaalschakelaar omvat.

Als u de systeemeigen bezorgingssjabloon wilt behouden, raden we u aan deze te dupliceren en vervolgens te configureren.

In het onderstaande voorbeeld genereren we een sjabloon om de bezorging van berichten via het eerder aangemaakte SMPP-account te vergemakkelijken. Dit doet u als volgt:

1. Klik in de **[!UICONTROL Resources]** > **[!UICONTROL Templates]** > **[!UICONTROL Delivery templates]** knooppunt van de structuur met de rechtermuisknop op de **[!UICONTROL Send to mobiles]** sjabloon en selecteer **[!UICONTROL Duplicate]**.

   ![](assets/delivery_template_mid_1.png)

1. Wijzig het label van de sjabloon, bijvoorbeeld **Verzonden naar mobiele telefoons (SMPP).**

   ![](assets/delivery_template_mid_2.png)

1. Klik op **[!UICONTROL Properties]**.

1. Op het **[!UICONTROL General]** lusje, selecteer een verpletterende wijze die aan de externe rekening beantwoordt die u in de sectie [ creeerde een externe rekening van SMS op de Marketing server ](#create-accound-mkt).

   ![](assets/delivery_template_mid_3.png)

1. Klik op **[!UICONTROL Save]** om de sjabloon te maken.

   ![](assets/delivery_template_mid_4.png)

Je hebt nu een externe account en een leveringstemplate waarmee je via SMS kunt leveren.

## Verwante onderwerpen {#related-topics}

* [Vertaling van SMS-tekens](sms-set-up.md#about-character-transliteration)
* [Tekstcoderingen](sms-set-up.md#about-text-encodings)
* [Automatische reactie](sms-set-up.md#automatic-reply)
