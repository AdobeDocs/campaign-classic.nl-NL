---
product: campaign
title: SMS-kanaal voor campagne instellen
description: Leer hoe te om het kanaal van SMS in Campagne te vormen
audience: delivery
content-type: reference
topic-tags: sending-messages-on-mobiles
exl-id: a2783a5e-6d38-41a1-b5c6-24ab489116f8
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '1677'
ht-degree: 34%

---

# Sms-kanaal configureren {#setting-up-sms-channel}

Als u naar een mobiele telefoon wilt verzenden, hebt u het volgende nodig:

1. Een externe account die een connector en type bericht opgeeft.

   Merk op dat de erfenisschakelaars nu verouderd zijn. Verouderde mogelijkheden zijn nog steeds beschikbaar, maar deze worden niet verder verbeterd en worden niet ondersteund. Meer informatie [op deze pagina](../../rn/using/deprecated-features.md).

1. Een leveringssjabloon waarin naar deze externe account wordt verwezen.

## Een SMPP-externe account maken {#creating-an-smpp-external-account}

Als u SMS naar een mobiele telefoon wilt verzenden, moet u eerst uw SMPP-externe account maken.
Voor meer informatie over het protocol en de montages van SMS, verwijs naar deze [pagina](../../delivery/using/sms-protocol.md).

Volg de onderstaande stappen om dit te doen:

1. Klik in het knooppunt **[!UICONTROL Platform]** > **[!UICONTROL External accounts]** van de structuur op het pictogram **[!UICONTROL New]**.
1. Definieer het accounttype als **Routering**, het kanaal als **Mobiel (SMS)**, en de leveringswijze als **Bulk levering**.

   ![](assets/extended_smpp_create_account.png)

1. Schakel het selectievakje **[!UICONTROL Enabled]** in.
1. Selecteer op het tabblad **[!UICONTROL Mobile]** **[!UICONTROL Extended generic SMPP]** in de vervolgkeuzelijst **[!UICONTROL Connector]**.

   ![](assets/extended_smpp_connector.png)

   >[!CAUTION]
   >
   > Vanaf versie 20.2 zijn verouderde connectors vervangen en niet ondersteund. Wij adviseren gebruikend de **[!UICONTROL Extended generic SMPP]** schakelaar. Voor meer informatie over hoe te om aan de geadviseerde schakelaar te migreren, verwijs naar deze [pagina](../../delivery/using/unsupported-connector-migration.md).

1. Met de optie **[!UICONTROL Enable verbose SMPP traces in the log file]** kunt u al het SMPP-verkeer in logbestanden dumpen. Deze optie moet zijn ingeschakeld om problemen met de connector op te lossen en om vergelijkingen te maken met het verkeer dat door de provider wordt waargenomen.

1. Neem contact op met uw SMS-serviceprovider die u zal uitleggen hoe u de verschillende externe accountvelden op het tabblad **[!UICONTROL Connection settings]** kunt invullen.

   Neem vervolgens contact op met uw provider, afhankelijk van de gekozen provider, die u de waarde geeft die u in het veld **[!UICONTROL SMSC implementation name]** wilt invoeren.

   U kunt het aantal verbindingen aan de leverancier per MTA kind bepalen. De standaardwaarde is 1.

1. Standaard voldoet het aantal tekens in een SMS aan de GSM-standaarden.

   Sms-berichten met gsm-codering mogen maximaal 160 tekens bevatten of 153 tekens per sms voor berichten die in meerdere delen worden verzonden.

   >[!NOTE]
   >
   >Bepaalde tekens tellen als twee tekens: accolades, vierkante haakjes, het euroteken, enzovoort. 
   >
   >De lijst met beschikbare GSM-tekens wordt hieronder weergegeven.

   Desgewenst kunt u tekentransliteratie autoriseren door het betreffende vakje in te schakelen.

   ![](assets/extended_smpp_transliteration.png)

   Raadpleeg [deze sectie](#about-character-transliteration) voor meer informatie.

1. Op het tabblad **[!UICONTROL Throughput and delays]** kunt u de maximale doorvoer van uitgaande berichten (&quot;MT&quot;, Mobiel beëindigd) in MT per seconde opgeven. Als u ‘0’ invoert in het overeenkomstige veld, is de doorvoer onbeperkt.

   De waarden van alle velden die corresponderen met een tijdsduur, moeten in seconden worden ingevuld.

1. Op het tabblad **[!UICONTROL Mapping of encodings]** kunt u coderingen definiëren.

   Raadpleeg [deze sectie](#about-text-encodings) voor meer informatie.

1. Op het tabblad **[!UICONTROL SMSC specificities]** is de optie **[!UICONTROL Send full phone number]** standaard uitgeschakeld. Laat het niet toe als u het protocol wilt respecteren SMPP en slechts cijfers naar de server van de leverancier van SMS (SMSC) overbrengen.

   Aangezien bepaalde providers het gebruik van het voorvoegsel &#39;+&#39; vereisen, wordt u echter geadviseerd contact op te nemen met uw provider en wordt u aangeraden deze optie indien nodig in te schakelen.

   Met het selectievakje **[!UICONTROL Enable TLS over SMPP]** kunt u SMPP-verkeer coderen. Raadpleeg [deze pagina](../../delivery/using/sms-protocol.md) voor meer informatie.

1. Als u een **[!UICONTROL Extended generic SMPP]** schakelaar vormt, kunt u opstelling automatische antwoorden.

   Raadpleeg [deze sectie](#automatic-reply) voor meer informatie.

## Vertaling van SMS-tekens {#about-character-transliteration}

Tekentransliteratie kan worden ingesteld in een externe account voor levering via SMPP voor mobiele apparaten, onder het tabblad **[!UICONTROL Mobile]**.

Transliteratie houdt in dat een teken van een sms door een ander teken wordt vervangen wanneer dat teken niet in aanmerking wordt genomen door de gsm-standaard.

* Als de transliteratie **[!UICONTROL authorized]** is, wordt elk karakter dat niet in aanmerking wordt genomen vervangen door een GSM karakter wanneer het bericht wordt verzonden. De letter ‘ë’ wordt bijvoorbeeld vervangen door ‘e’. Het bericht is daarom enigszins gewijzigd, maar de tekenlimiet blijft hetzelfde.
* Wanneer transliteratie **[!UICONTROL not authorized]** is, wordt elk bericht dat karakters bevat die niet in rekening worden gebracht verzonden in binair formaat (Unicode): alle tekens worden daarom naar behoren verzonden. De sms-berichten met Unicode zijn echter beperkt tot 70 tekens (of 67 tekens per sms voor berichten die in meerdere delen worden verzonden). Als het maximum aantal tekens wordt overschreden, worden verschillende berichten verzonden, wat extra kosten kan veroorzaken.

>[!IMPORTANT]
>
>Als u personalisatievelden invoegt in de content van uw sms-bericht, worden mogelijk tekens ingevoegd die niet in aanmerking worden genomen door de gsm-codering.

Standaard is transliteratie van tekens uitgeschakeld. Als u alle tekens in uw sms-berichten wilt behouden zoals ze zijn, bijvoorbeeld om geen eigennamen te wijzigen, wordt u aangeraden deze optie niet in te schakelen.

Als uw sms-berichten echter veel tekens bevatten die Unicode-berichten genereren, kunt u deze optie inschakelen om de kosten voor het verzenden van uw berichten te beperken.

In de volgende tabel worden de tekens weergegeven waarmee de GSM-standaard rekening houdt. Alle tekens die in de hoofdtekst van het bericht worden ingevoegd, met uitzondering van de onderstaande tekens, converteren het volledige bericht naar de binaire indeling (Unicode) en beperken het tot 70 tekens.

**Standaardtekens**

<table> 
 <tbody> 
  <tr> 
   <td> @ </td> 
   <td> <img height="21px" src="assets/delta.png" /> </td> 
   <td> SP </td> 
   <td> 0 </td> 
   <td> TP </td> 
   <td> P </td> 
   <td> voor </td> 
   <td> p </td> 
  </tr> 
  <tr> 
   <td> £ </td> 
   <td> _ </td> 
   <td> ! </td> 
   <td> 3 </td> 
   <td> A </td> 
   <td> Q </td> 
   <td> a </td> 
   <td> q </td> 
  </tr> 
  <tr> 
   <td> $ </td> 
   <td> <img height="21px" src="assets/phi.png" /> </td> 
   <td> ’ </td> 
   <td> 2 </td> 
   <td> B </td> 
   <td> R </td> 
   <td> b </td> 
   <td> r </td> 
  </tr> 
  <tr> 
   <td> ¥ </td> 
   <td> <img height="21px" src="assets/gamma.png" /> </td> 
   <td> Aantal </td> 
   <td> 1 </td> 
   <td> C </td> 
   <td> S </td> 
   <td> c </td> 
   <td> s </td> 
  </tr> 
  <tr> 
   <td> è </td> 
   <td> <img height="21px" src="assets/delta.png" /> </td> 
   <td> ¤ </td> 
   <td> 4 </td> 
   <td> D </td> 
   <td> T </td> 
   <td> d </td> 
   <td> t </td> 
  </tr> 
  <tr> 
   <td> é </td> 
   <td> <img height="21px" src="assets/omega.png" /> </td> 
   <td> % </td> 
   <td> 5 </td> 
   <td> E </td> 
   <td> U </td> 
   <td> e </td> 
   <td> u </td> 
  </tr> 
  <tr> 
   <td> ù </td> 
   <td> <img height="21px" src="assets/pi.png" /> </td> 
   <td> &amp; </td> 
   <td> 6 </td> 
   <td> F </td> 
   <td> V </td> 
   <td> f </td> 
   <td> v </td> 
  </tr> 
  <tr> 
   <td> ì </td> 
   <td> <img height="21px" src="assets/psi.png" /> </td> 
   <td> ' </td> 
   <td> 7 </td> 
   <td> G </td> 
   <td> W </td> 
   <td> g </td> 
   <td> w </td> 
  </tr> 
  <tr> 
   <td> ò </td> 
   <td> <img height="21px" src="assets/sigma.png" /> </td> 
   <td> ( </td> 
   <td> 8 </td> 
   <td> H </td> 
   <td> X </td> 
   <td> h </td> 
   <td> x </td> 
  </tr> 
  <tr> 
   <td> Ç </td> 
   <td> <img height="21px" src="assets/theta.png" /> </td> 
   <td> ) </td> 
   <td> 9 </td> 
   <td> I </td> 
   <td> Y </td> 
   <td> i </td> 
   <td> y </td> 
  </tr> 
  <tr> 
   <td> LF </td> 
   <td> <img height="21px" src="assets/xi.png" /> </td> 
   <td> * </td> 
   <td> : </td> 
   <td> J </td> 
   <td> Z </td> 
   <td> j </td> 
   <td> z </td> 
  </tr> 
  <tr> 
   <td> Ø </td> 
   <td> ESC </td> 
   <td> + </td> 
   <td> ; </td> 
   <td> K </td> 
   <td> Ä </td> 
   <td> k </td> 
   <td> ä </td> 
  </tr> 
  <tr> 
   <td> ø </td> 
   <td> Æ </td> 
   <td> , </td> 
   <td> &lt;&gt; </td> 
   <td> L </td> 
   <td> Ö </td> 
   <td> l </td> 
   <td> ö </td> 
  </tr> 
  <tr> 
   <td> CR </td> 
   <td> æ </td> 
   <td> - </td> 
   <td> = </td> 
   <td> M </td> 
   <td> Ñ </td> 
   <td> m </td> 
   <td> ñ </td> 
  </tr> 
  <tr> 
   <td> Å </td> 
   <td> ß </td> 
   <td> . </td> 
   <td> &gt; </td> 
   <td> N </td> 
   <td> Ü </td> 
   <td> n </td> 
   <td> ü </td> 
  </tr> 
  <tr> 
   <td> å </td> 
   <td> É </td> 
   <td> / </td> 
   <td> ? </td> 
   <td> O </td> 
   <td> § </td> 
   <td> o </td> 
   <td> à </td> 
  </tr> 
 </tbody> 
</table>

SP: Spatie

ESC: Escape

LF: Nieuwe regel

CR: Enter-teken

**Geavanceerde tekens (twee keer geteld)**

^ { } `[ ~ ]` | €

## Tekstcoderingen {#about-text-encodings}

Wanneer u een sms-bericht verzendt, kan Adobe Campaign een of meer tekstcoderingen gebruiken. Elke codering heeft een eigen specifieke tekenset en bepaalt het aantal tekens dat in een sms-bericht past.

Wanneer u een nieuwe externe account voor levering via SMPP mobile configureert, kunt u **[!UICONTROL Mapping of encodings]** definiëren op het tabblad **[!UICONTROL Mobile]**: Met het veld **[!UICONTROL data_coding]** kan Adobe Campaign meedelen welke codering wordt gebruikt voor het SMSC.

>[!NOTE]
>
>De toewijzing tussen de waarde **data_coding** en de werkelijk gebruikte codering wordt gestandaardiseerd. Bepaalde SMSC&#39;s hebben echter hun eigen specifieke kaart: in dit geval moet uw **Adobe Campaign**-beheerder deze toewijzing declareren. Neem contact op met uw provider om meer informatie te krijgen.

U kunt **data_codings** verklaren en zonodig het coderen dwingen: Hiervoor geeft u één codering in de tabel op.

* Wanneer geen afbeelding van coderingen wordt bepaald, neemt de schakelaar een generisch gedrag over:

   * Er wordt geprobeerd gsm-codering te gebruiken waaraan de waarde **data_coding = 0** wordt toegewezen.
   * Als gsm-codering mislukt, wordt **UCS2** -codering gebruikt waaraan de waarde **data_coding = 8** wordt toegewezen.

* Wanneer u de coderingen definieert die u wilt gebruiken en de gekoppelde **[!UICONTROL data_coding]**-veldwaarden, probeert Adobe Campaign de eerste codering in de lijst te gebruiken, gevolgd door de volgende codering als de eerste codering onmogelijk blijkt.

>[!IMPORTANT]
>
>De volgorde van de declaratie is belangrijk. U wordt aangeraden de lijst in oplopende volgorde **van kosten** te plaatsen om voorrang te geven aan de coderingen, zodat u in elk sms-bericht zoveel mogelijk tekens kunt plaatsen.
>
>Declareer alleen de coderingen die u wilt gebruiken. Als sommige coderingen die door het SMSC worden verstrekt niet met uw doel van gebruik zouden moeten beantwoorden, verklaar hen niet in de lijst.

## Automatisch antwoord {#automatic-reply}

Wanneer vestiging een uitgebreide generische schakelaar SMPP, kunt u automatische antwoorden vormen.

Wanneer een abonnee op een SMS-bericht reageert dat via Adobe Campaign naar hem is verzonden en zijn bericht een trefwoord zoals &quot;STOP&quot; bevat, kunt u berichten configureren die automatisch naar hem worden teruggestuurd in de sectie **[!UICONTROL Automatic reply sent to the MO]**.

>[!NOTE]
>
>De trefwoorden zijn niet hoofdlettergevoelig.

Voor elk sleutelwoord, specificeer een korte code, die een aantal is dat gewoonlijk wordt gebruikt om leveringen te verzenden en als afzendernaam zal dienen, dan ga het bericht in dat naar de abonnee zal worden verzonden.

U kunt ook een actie koppelen aan uw automatische reactie: **[!UICONTROL Send to quarantine]** of **[!UICONTROL Remove from quarantine]**. Bijvoorbeeld, als een ontvanger het sleutelwoord &quot;STOP&quot;verzendt, zullen zij automatisch een unsubscription bevestiging ontvangen en naar quarantaine verzonden.

![](assets/extended_smpp_reply.png)

Als u de **[!UICONTROL Remove from quarantine]** actie aan een automatische reactie verbindt, worden de ontvangers die het overeenkomstige sleutelwoord verzenden automatisch verwijderd uit quarantaine.

Ontvangers worden vermeld in de tabel **[!UICONTROL Non deliverables and addresses]** die beschikbaar is via het menu **[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Non deliverables Management]**.

* Als u hetzelfde antwoord wilt verzenden, ongeacht de korte code, laat u de kolom **[!UICONTROL Short code]** leeg.
* Als u hetzelfde antwoord wilt verzenden, ongeacht het trefwoord, laat u de kolom **[!UICONTROL Keyword]** leeg.
* Als u een actie wilt uitvoeren zonder een reactie te verzenden, laat u de kolom **[!UICONTROL Response]** leeg. Zo kunt u bijvoorbeeld een gebruiker die met een ander bericht dan &quot;STOP&quot; reageert, uit quarantaine verwijderen.

Als u veelvoudige externe rekeningen gebruikend de Uitgebreide generische schakelaar SMPP met de zelfde leveranciersrekening hebt, kan de volgende kwestie gebeuren: wanneer u een antwoord op een korte code verzendt, kan dit antwoord op een van uw externe accountverbindingen worden ontvangen. Het automatische antwoord dat wordt verzonden, kan dan ook niet het verwachte bericht zijn.
U kunt dit voorkomen door een van de volgende oplossingen toe te passen, afhankelijk van de provider die u gebruikt:

* Maak één leverancieraccount voor elke externe account.
* Gebruik het veld **[!UICONTROL System type]** op het tabblad **[!UICONTROL Mobile]** > **[!UICONTROL Connection settings]** om elke korte code te onderscheiden. Vraag uw provider om een andere waarde voor elke account.

   ![](assets/extended_smpp_system-type.png)

De stappen voor het instellen van een externe account met behulp van de uitgebreide algemene SMPP-connector worden beschreven in de sectie [Een externe SMPP-account maken](#creating-an-smpp-external-account).

## De leveringssjabloon wijzigen {#changing-the-delivery-template}

Adobe Campaign biedt u een sjabloon voor levering aan mobiele apparaten. Deze sjabloon is beschikbaar in het knooppunt **[!UICONTROL Resources > Templates > Delivery templates]**. Raadpleeg voor meer informatie de sectie [Informatie over sjablonen](../../delivery/using/about-templates.md).

Om via het kanaal van SMS te leveren, moet u een malplaatje tot stand brengen waarin de kanaalschakelaar van verwijzingen wordt voorzien.

Om het inheemse leveringsmalplaatje te houden, adviseren wij dat u het dupliceert en dan het vormt.

In het onderstaande voorbeeld maken we een sjabloon voor het verzenden van berichten via de SMPP-account die eerder is ingeschakeld. Dit doet u als volgt:

1. Ga naar de **[!UICONTROL Delivery templates]** knoop.
1. Klik met de rechtermuisknop op de sjabloon **[!UICONTROL Send to mobiles]** en selecteer **[!UICONTROL Duplicate]**.

   ![](assets/s_user_mobile_template_change_01.png)

1. Wijzig het label van de sjabloon, bijvoorbeeld **Verzonden naar mobiele apparaten (SMPP)**.

   ![](assets/s_user_mobile_template_change_02.png)

1. Klik op **[!UICONTROL Properties]**.
1. Op **[!UICONTROL General]** lusje, selecteer een verpletterende wijze die aan de externe rekening beantwoordt die u in de vorige stappen creeerde.

   ![](assets/s_user_mobile_template_change_03.png)

1. Klik op **[!UICONTROL Save]** om de sjabloon te maken.

   ![](assets/s_user_mobile_template_list.png)

Je hebt nu een externe account en een leveringstemplate waarmee je via SMS kunt leveren.
