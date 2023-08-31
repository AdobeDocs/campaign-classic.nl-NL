---
product: campaign
title: SMS-kanaal voor campagne configureren
description: Leer hoe te om het kanaal van SMS in Campagne te vormen
badge-v7: label="v7" type="Informative" tooltip="Is van toepassing op Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
feature: SMS
role: User, Developer, Admin
exl-id: a2783a5e-6d38-41a1-b5c6-24ab489116f8
source-git-commit: d2f5f2a662c022e258fb3cc56c8502c4f4cb2849
workflow-type: tm+mt
source-wordcount: '1734'
ht-degree: 34%

---

# Sms-kanaal configureren {#setting-up-sms-channel}

Als u naar een mobiele telefoon wilt verzenden, hebt u het volgende nodig:

1. Een externe account die een connector en type bericht opgeeft.

   Merk op dat de erfenisschakelaars nu verouderd zijn. Afgeschafte mogelijkheden zijn nog steeds beschikbaar, maar ze zullen niet verder worden verbeterd of ondersteund. Meer informatie vindt u [op deze pagina](../../rn/using/deprecated-features.md).

1. Een leveringssjabloon waarin naar deze externe account wordt verwezen.

>[!NOTE]
>
> Voor SMS-leveringen moet de typologie een specifieke SMS-affiniteit gebruiken die in **één** specifieke toepassingsservercontainer. [Meer informatie](../../installation/using/configure-delivery-settings.md#managing-outbound-smtp-traffic-with-affinities)

## Een SMPP-externe account maken {#creating-an-smpp-external-account}

>[!IMPORTANT]
>
>Het gebruik van hetzelfde account en wachtwoord voor meerdere externe SMS-accounts kan leiden tot conflicten en overlapping tussen de accounts. Zie de [De pagina voor probleemoplossing via SMS](troubleshooting-sms.md#external-account-conflict).

Als u SMS naar een mobiele telefoon wilt verzenden, moet u eerst uw SMPP-externe account maken.
Voor meer informatie over het protocol en de montages van SMS, verwijs naar dit [page](sms-protocol.md).

Volg de onderstaande stappen om dit te doen:

1. In de **[!UICONTROL Platform]** > **[!UICONTROL External accounts]** knoop van de boom, klik **[!UICONTROL New]** pictogram.
1. Het accounttype definiëren als **Routering**, het kanaal als **Mobiel (SMS)** en de leveringsmodus als **Bulklevering**.

   ![](assets/extended_smpp_create_account.png)

1. Controleer de **[!UICONTROL Enabled]** doos.
1. In de **[!UICONTROL Mobile]** tab, selecteert u **[!UICONTROL Extended generic SMPP]** van de **[!UICONTROL Connector]** vervolgkeuzelijst.

   ![](assets/extended_smpp_connector.png)

   >[!CAUTION]
   >
   > Vanaf versie 20.2 zijn verouderde connectors vervangen en niet ondersteund. We raden u aan de **[!UICONTROL Extended generic SMPP]** -aansluiting. Voor meer informatie over hoe te om aan de geadviseerde schakelaar te migreren, verwijs naar dit [page](unsupported-connector-migration.md).

1. De **[!UICONTROL Enable verbose SMPP traces in the log file]** optie staat u toe om al verkeer SMPP in logboekdossiers te dumpen. Deze optie moet zijn ingeschakeld om problemen met de connector op te lossen en om vergelijkingen te maken met het verkeer dat door de provider wordt waargenomen.

1. Neem contact op met uw SMS-serviceprovider die u zal uitleggen hoe u de verschillende velden voor externe accounts kunt invullen via de **[!UICONTROL Connection settings]** tab.

   Neem vervolgens contact op met uw provider, afhankelijk van de gekozen provider, die u de waarde geeft die u in de **[!UICONTROL SMSC implementation name]** veld.

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

1. In de **[!UICONTROL Throughput and delays]** kunt u de maximale doorvoer van uitgaande berichten (&quot;MT&quot;, Mobiel beëindigd) in MT per seconde opgeven. Als u ‘0’ invoert in het overeenkomstige veld, is de doorvoer onbeperkt.

   De waarden van alle velden die corresponderen met een tijdsduur, moeten in seconden worden ingevuld.

1. In de **[!UICONTROL Mapping of encodings]** kunt u coderingen definiëren.

   Raadpleeg [deze sectie](#about-text-encodings) voor meer informatie.

1. In de **[!UICONTROL SMSC specificities]** de **[!UICONTROL Send full phone number]** is standaard uitgeschakeld. Laat het niet toe als u het protocol wilt respecteren SMPP en slechts cijfers naar de server van de leverancier van SMS (SMSC) overbrengen.

   Aangezien bepaalde providers het gebruik van het voorvoegsel &#39;+&#39; vereisen, wordt u echter geadviseerd contact op te nemen met uw provider en wordt u aangeraden deze optie indien nodig in te schakelen.

   De **[!UICONTROL Enable TLS over SMPP]** checkbox staat u toe om verkeer te coderen SMPP. Raadpleeg [deze pagina](sms-protocol.md) voor meer informatie.

1. Als u een **[!UICONTROL Extended generic SMPP]** , kunt u automatische antwoorden instellen.

   Raadpleeg [deze sectie](#automatic-reply) voor meer informatie.

## Vertaling van SMS-tekens {#about-character-transliteration}

Tekentransliteratie kan worden ingesteld in een externe rekening voor levering via SMPP voor mobiele apparaten, onder de **[!UICONTROL Mobile]** tab.

Transliteratie houdt in dat een teken van een sms door een ander teken wordt vervangen wanneer dat teken niet in aanmerking wordt genomen door de gsm-standaard.

* Indien transliteratie **[!UICONTROL authorized]**, wordt elk teken dat niet in aanmerking wordt genomen, vervangen door een GSM-teken wanneer het bericht wordt verzonden. De letter ‘ë’ wordt bijvoorbeeld vervangen door ‘e’. Het bericht is daarom enigszins gewijzigd, maar de tekenlimiet blijft hetzelfde.
* Wanneer transliteratie **[!UICONTROL not authorized]**, wordt elk bericht dat tekens bevat waarmee geen rekening wordt gehouden, verzonden in binaire notatie (Unicode): alle tekens worden daarom verzonden zoals ze zijn. De sms-berichten met Unicode zijn echter beperkt tot 70 tekens (of 67 tekens per sms voor berichten die in meerdere delen worden verzonden). Als het maximum aantal tekens wordt overschreden, worden verschillende berichten verzonden, wat extra kosten kan veroorzaken.

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
   <td> ¡ </td> 
   <td> P </td> 
   <td> ¿ </td> 
   <td> p </td> 
  </tr> 
  <tr> 
   <td> £ </td> 
   <td> _ </td> 
   <td> ! </td> 
   <td> 1 </td> 
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
   <td> # </td> 
   <td> 3 </td> 
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
   <td> &lt; </td> 
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

Wanneer u een nieuwe externe account voor levering via SMPP mobile configureert, kunt u de **[!UICONTROL Mapping of encodings]** in de **[!UICONTROL Mobile]** tab: the **[!UICONTROL data_coding]** in het veld kan Adobe Campaign meedelen welke codering wordt gebruikt voor het SMSC.

>[!NOTE]
>
>De toewijzing tussen de waarde **data_coding** en de werkelijk gebruikte codering wordt gestandaardiseerd. Niettemin hebben bepaalde SMSC hun eigen specifieke kaart: in dit geval uw **Adobe Campaign** de beheerder moet deze afbeelding verklaren. Neem contact op met uw provider om meer informatie te krijgen.

U kunt declareren **data_codings** en forceer zo nodig de codering: hiervoor geeft u één codering in de tabel op.

* Wanneer geen afbeelding van coderingen wordt bepaald, neemt de schakelaar een generisch gedrag over:

   * Er wordt geprobeerd gsm-codering te gebruiken waaraan de waarde **data_coding = 0** wordt toegewezen.
   * Als gsm-codering mislukt, wordt **UCS2** -codering gebruikt waaraan de waarde **data_coding = 8** wordt toegewezen.

* Wanneer u de coderingen definieert die u wilt gebruiken en de gekoppelde coderingen **[!UICONTROL data_coding]** veldwaarden, probeert Adobe Campaign de eerste codering in de lijst te gebruiken, daarna het volgende als de eerste codering onmogelijk blijkt.

>[!IMPORTANT]
>
>De volgorde van de declaratie is belangrijk. U wordt aangeraden de lijst in oplopende volgorde **van kosten** te plaatsen om voorrang te geven aan de coderingen, zodat u in elk sms-bericht zoveel mogelijk tekens kunt plaatsen.
>
>Declareer alleen de coderingen die u wilt gebruiken. Als sommige coderingen die door het SMSC worden verstrekt niet met uw doel van gebruik zouden moeten beantwoorden, verklaar hen niet in de lijst.

## Automatische reactie {#automatic-reply}

Wanneer vestiging een uitgebreide generische schakelaar SMPP, kunt u automatische antwoorden vormen.

Wanneer een abonnee op een SMS-bericht reageert dat via Adobe Campaign naar hem is verzonden en zijn bericht een trefwoord bevat zoals &quot;STOP&quot;, kunt u berichten configureren die automatisch naar hem worden teruggestuurd in het dialoogvenster **[!UICONTROL Automatic reply sent to the MO]** sectie.

>[!NOTE]
>
>De trefwoorden zijn niet hoofdlettergevoelig.

Voor elk sleutelwoord, specificeer een korte code, die een aantal is dat gewoonlijk wordt gebruikt om leveringen te verzenden en als afzendernaam zal dienen, dan ga het bericht in dat naar de abonnee zal worden verzonden.

U kunt ook een actie koppelen aan uw automatische reactie: **[!UICONTROL Send to quarantine]** of **[!UICONTROL Remove from quarantine]**. Bijvoorbeeld, als een ontvanger het sleutelwoord &quot;STOP&quot;verzendt, zullen zij automatisch een unsubscription bevestiging ontvangen en naar quarantaine verzonden.

![](assets/extended_smpp_reply.png)

Als u de koppeling **[!UICONTROL Remove from quarantine]** actie aan een automatische reactie, worden de ontvangers die het overeenkomstige sleutelwoord verzenden automatisch verwijderd uit quarantaine.

Ontvangers worden vermeld in het dialoogvenster **[!UICONTROL Non deliverables and addresses]** tabel beschikbaar via **[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Non deliverables Management]** -menu.

* Als u hetzelfde antwoord wilt verzenden, ongeacht de korte code, laat u de **[!UICONTROL Short code]** kolom leeg.
* Als u hetzelfde antwoord wilt verzenden, ongeacht het trefwoord, laat u het **[!UICONTROL Keyword]** kolom leeg.
* Als u een actie wilt uitvoeren zonder een antwoord te verzenden, laat u de **[!UICONTROL Response]** kolom leeg. Zo kunt u bijvoorbeeld een gebruiker die met een ander bericht dan &quot;STOP&quot; reageert, uit quarantaine verwijderen.

Als u veelvoudige externe rekeningen gebruikend de Uitgebreide generische schakelaar SMPP met de zelfde leveranciersrekening hebt, kan de volgende kwestie gebeuren: wanneer het verzenden van een antwoord naar een korte code, kan het op om het even welk van uw externe rekeningsverbindingen worden ontvangen. Het automatische antwoord dat wordt verzonden, kan dan ook niet het verwachte bericht zijn.
U kunt dit voorkomen door een van de volgende oplossingen toe te passen, afhankelijk van de provider die u gebruikt:

* Maak één leverancieraccount voor elke externe account.
* Gebruik de **[!UICONTROL System type]** veld van de **[!UICONTROL Mobile]** > **[!UICONTROL Connection settings]** om elke korte code van elkaar te onderscheiden. Vraag uw provider om een andere waarde voor elke account.

  ![](assets/extended_smpp_system-type.png)

De stappen voor het opzetten van een externe account met behulp van de Extended Generic SMPP-connector worden beschreven in de [Een SMPP-externe account maken](#creating-an-smpp-external-account) sectie.

## De leveringssjabloon wijzigen {#changing-the-delivery-template}

Adobe Campaign biedt u een sjabloon voor levering aan mobiele apparaten. Deze sjabloon is beschikbaar in het dialoogvenster **[!UICONTROL Resources > Templates > Delivery templates]** knooppunt. Raadpleeg voor meer informatie de [Over sjablonen](about-templates.md) sectie.

Om via het kanaal van SMS te leveren, moet u een malplaatje tot stand brengen waarin de kanaalschakelaar van verwijzingen wordt voorzien.

Om het inheemse leveringsmalplaatje te houden, adviseren wij dat u het dupliceert en dan het vormt.

In het onderstaande voorbeeld maken we een sjabloon voor het verzenden van berichten via de SMPP-account die eerder is ingeschakeld. Dit doet u als volgt:

1. Ga naar de **[!UICONTROL Delivery templates]** knooppunt.
1. Klik met de rechtermuisknop op de knop **[!UICONTROL Send to mobiles]** en selecteer **[!UICONTROL Duplicate]**.

   ![](assets/s_user_mobile_template_change_01.png)

1. Het label van de sjabloon wijzigen, bijvoorbeeld **Verzonden naar mobiele apparaten (SMPP)**.

   ![](assets/s_user_mobile_template_change_02.png)

1. Klik op **[!UICONTROL Properties]**.
1. In de **[!UICONTROL General]** selecteert u een routeringsmodus die overeenkomt met de externe account die u in de vorige stappen hebt gemaakt.

   ![](assets/s_user_mobile_template_change_03.png)

1. Klikken **[!UICONTROL Save]** om de sjabloon te maken.

   ![](assets/s_user_mobile_template_list.png)

Je hebt nu een externe account en een leveringstemplate waarmee je via SMS kunt leveren.
