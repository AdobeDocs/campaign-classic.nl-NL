---
solution: Campaign Classic
product: campaign
title: Indicatoren berekenen
description: Indicatoren berekenen
audience: reporting
content-type: reference
topic-tags: accessing-built-in-reports
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '2972'
ht-degree: 1%

---


# Indicatoren berekenen {#indicator-calculation}

## Gebruikersactiviteiten {#user-activities-1}

<table> 
 <thead> 
  <tr> 
   <th> <strong>Label</strong> <br /> </th> 
   <th> <strong>Veldnaam</strong> <br /> </th> 
   <th> <strong>Beschrijving van de indicator</strong> <br /> </th> 
   <th> <strong>Indicatorberekeningsformule</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Geopende items<br /> </td> 
   <td> @open<br /> </td> 
   <td> De som van alle @totalClicks met een primaire URL-sleutel gelijk aan 1.<br /> </td> 
   <td> sum(IF([@url-id]=1, @totalClicks, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Klikken<br /> </td> 
   <td> @clicks<br /> </td> 
   <td> De som van alle @totalClicks met een URL-type dat gelijk is aan "Email click".<br /> </td> 
   <td> sum(Iif([url/@type]=1, @totalClicks, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Transacties<br /> </td> 
   <td> @transactions<br /> </td> 
   <td> De som van alle @totalClicks met een URL-type dat gelijk is aan "Transaction".<br /> </td> 
   <td> sum(Iif([url/@type]=5, @totalClicks, 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

Dit rapport is gebaseerd op de **[!UICONTROL Consolidated tracking]** lijst (nms:trackingStats). Deze geaggregeerde tabel wordt om prestatieredenen gebruikt bij het weergeven van rapporten, in de plaats van de tabel **[!UICONTROL Recipient tracking logs]** (nms:trackingLogRcp) en wordt niet in real-time berekend. De tabel wordt een paar minuten nadat de logbestanden voor bijhouden zijn opgehaald, gegenereerd. Als de indicatoren up-to-date zijn, zullen de resultaten het zelfde als voor de indicatoren van het **Tracking indicatoren** rapport zijn. De @totalclicks-indicator geeft het totale aantal klikken over een periode van 5 minuten aan.

## Niet-leverbare items en niet-bezorgingen {#non-deliverables-and-bounces-1}

**Uitsplitsing naar fouttype**

Dit rapport is gebaseerd op de **[!UICONTROL Delivery and tracking statistics]** lijst (nms:deliveryLogStats).

<table> 
 <thead> 
  <tr> 
   <th> <strong>Label</strong> <br /> </th> 
   <th> <strong>Veldnaam</strong> <br /> </th> 
   <th> <strong>Beschrijving van de indicator</strong> <br /> </th> 
   <th> <strong>Indicatorberekeningsformule</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Totaal aantal verwerkte berichten<br /> </td> 
   <td> @totalProcesses<br /> </td> 
   <td> Som van berichten met een status gelijk aan "Klaar", "Verzonden" of "Mislukt".<br /> </td> 
   <td> @prepare + @error + @success<br /> </td> 
  </tr> 
  <tr> 
   <td> Gebruiker onbekend<br /> </td> 
   <td> @unknownUser<br /> </td> 
   <td> Aantal van alle berichten met een status gelijk aan "Mislukt" en een reden gelijk aan "Gebruiker onbekend". <br /> </td> 
   <td> Count(@status=2 en msg/@failureReason=1)<br /> </td> 
  </tr> 
  <tr> 
   <td> Onbereikbaar <br /> </td> 
   <td> @unbereikable<br /> </td> 
   <td> Aantal van alle berichten met een status gelijk aan "Ontbroken"en een reden gelijk aan "Onbereikbaar". <br /> </td> 
   <td> Count(@status=2 en msg/@failureReason=3)<br /> </td> 
  </tr> 
  <tr> 
   <td> Afgewezen<br /> </td> 
   <td> @weiges<br /> </td> 
   <td> Aantal van alle berichten met een status gelijk aan "Mislukt" en een reden gelijk aan "Afgewezen". <br /> </td> 
   <td> Count(@status=2 en msg/@failureReason=20)<br /> </td> 
  </tr> 
  <tr> 
   <td> Ongeldig domein<br /> </td> 
   <td> @invalidDomain<br /> </td> 
   <td> Aantal van alle berichten met een status gelijk aan "Mislukt"en een reden gelijk aan "Ongeldig domein". <br /> </td> 
   <td> Count(@status=2 en msg/@failureReason=2)<br /> </td> 
  </tr> 
  <tr> 
   <td> Account uitgeschakeld<br /> </td> 
   <td> @disabled<br /> </td> 
   <td> Aantal van alle berichten met een status gelijk aan "Ontbroken"en een reden gelijk aan "Rekening gehandicapt".<br /> </td> 
   <td> Count(@status=2 en msg/@failureReason=4)<br /> </td> 
  </tr> 
  <tr> 
   <td> Inbox full<br /> </td> 
   <td> @mailBoxFull<br /> </td> 
   <td> Aantal van alle berichten met een status gelijk aan "Ontbroken"en een reden gelijk aan "Inbox volledig". <br /> </td> 
   <td> Count(@status=2 en msg/@failureReason=5)<br /> </td> 
  </tr> 
  <tr> 
   <td> Fouten<br /> </td> 
   <td> @value<br /> </td> 
   <td> Aantal mislukte berichten voor dit type van fout.<br /> </td> 
   <td> Count(@status=2 en msg/@failureReason="Waarde van het foutentype")<br /> </td> 
  </tr> 
  <tr> 
   <td> Bijdrage<br /> </td> 
   <td> -<br /> </td> 
   <td> Percentage fouten van dit type in vergelijking met het totale aantal foutberichten.<br /> </td> 
   <td> percent(@value,@totalErrors)<br /> </td> 
  </tr> 
  <tr> 
   <td> Onderverdeling<br /> </td> 
   <td> -<br /> </td> 
   <td> Percentage fouten van dit type vergeleken met het totale aantal verwerkte berichten.<br /> </td> 
   <td> percent(@value,@totalProcesses)<br /> </td> 
  </tr> 
 </tbody> 
</table>

**Uitsplitsing naar domein**

In het tweede deel van het rapport wordt de uitsplitsing van mislukte berichten per internetdomein beschreven, in tegenstelling tot het fouttype. De formule die in dit geval is gekoppeld aan de **Error**-indicator (@value) is: Count(@status=2 en @domain=&quot;Waarde van de domeinnaam&quot;), d.w.z. een telling van alle berichten met een mislukte status voor dit domein.

## Browsers {#browsers-1}

Dit rapport is gebaseerd op de **[!UICONTROL Internet Browser Statistics]** lijst (nms:userAgentsStats).

**Algemene statistieken**

<table> 
 <thead> 
  <tr> 
   <th> <strong>Label</strong> <br /> </th> 
   <th> <strong>Veldnaam</strong> <br /> </th> 
   <th> <strong>Beschrijving van de indicator</strong> <br /> </th> 
   <th> <strong>Indicatorberekeningsformule</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Bezoekers<br /> </td> 
   <td> @totalVisitors<br /> </td> 
   <td> Het totale aantal beoogde ontvangers voor deze browser die minstens één keer in een levering hebben geklikt.<br /> </td> 
   <td> Sum(@bezoekers)<br /> </td> 
  </tr> 
  <tr> 
   <td> Paginaweergaven<br /> </td> 
   <td> @totalPages<br /> </td> 
   <td> Het totale aantal klikken op leveringsverbindingen die deze browser gebruiken, voor alle leveringen.<br /> </td> 
   <td> Sum(@pagina's) <br /> </td> 
  </tr> 
  <tr> 
   <td> Gebruiksfrequentie<br /> </td> 
   <td> -<br /> </td> 
   <td> Percentage bezoekers voor deze browser in vergelijking met het totale aantal bezoekers.<br /> </td> 
   <td> percent(@totalVisitors, som(@totalVisitors)) <br /> </td> 
  </tr> 
 </tbody> 
</table>

**Statistieken per browser**

<table> 
 <thead> 
  <tr> 
   <th> <strong>Label</strong> <br /> </th> 
   <th> <strong>Veldnaam</strong> <br /> </th> 
   <th> <strong>Beschrijving van de indicator</strong> <br /> </th> 
   <th> <strong>Indicatorberekeningsformule</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Gebruiksfrequentie<br /> </td> 
   <td> @bezoekers<br /> </td> 
   <td> Percentage van het aantal bezoekers per dag dat deze browser gebruikt in vergelijking met het aantal bezoekers dat op de dag met de meeste bezoekers wordt gemeten.<br /> </td> 
   <td> percent(sum(@bezoekers),max(@bezoekersOfDay))<br /> </td> 
  </tr> 
  <tr> 
   <td> Globale snelheid<br /> </td> 
   <td> -<br /> </td> 
   <td> Percentage bezoekers voor deze versie in vergelijking met het totale aantal bezoekers dat alle browsers gebruikt.<br /> </td> 
   <td> percent(@totalVisitors, @globalVisitors)<br /> </td> 
  </tr> 
  <tr> 
   <td> Relatief gewicht<br /> </td> 
   <td> -<br /> </td> 
   <td> Percentage bezoekers voor deze versie vergeleken met het totale aantal bezoekers dat deze browser gebruikt.<br /> </td> 
   <td> percent(@totalVisitors, som(@totalVisitors)) <br /> </td> 
  </tr> 
 </tbody> 
</table>

## Delen naar sociale netwerken {#sharing-to-social-networks-1}

Dit rapport is gebaseerd op de **[!UICONTROL Delivery]** (nms:delivery), **[!UICONTROL Consolidated tracking]** (nms:trackingStats) en **[!UICONTROL Web tracking]** (nms:webTrackingLog) tabellen.

<table> 
 <thead> 
  <tr> 
   <th> <strong>Label</strong> <br /> </th> 
   <th> <strong>Veldnaam</strong> <br /> </th> 
   <th> <strong>Beschrijving van de indicator</strong> <br /> </th> 
   <th> <strong>Indicatorberekeningsformule</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Aantal te leveren berichten<br /> </td> 
   <td> @totalTarget<br /> </td> 
   <td> Het totale aantal berichten dat tijdens de leveringsanalyse wordt verwerkt.<br /> </td> 
   <td> sum([eigenschappen/@totalTarget])<br /> </td> 
  </tr> 
  <tr> 
   <td> Aantal succesvolle leveringen<br /> </td> 
   <td> @success<br /> </td> 
   <td> Aantal berichten dat is verwerkt <br /> </td> 
   <td> sum([indicatoren/@succes])<br /> </td> 
  </tr> 
  <tr> 
   <td> E-mail<br /> </td> 
   <td> @email<br /> </td> 
   <td> De som van alle @totalClicks waarvoor de categorie URL staat voor "e-mail".<br /> </td> 
   <td> Sum(iIf([url/@category]='email',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Facebook<br /> </td> 
   <td> @facebook<br /> </td> 
   <td> De som van alle @totalClicks waarvoor de categorie URL gelijk is aan "facebook".<br /> </td> 
   <td> Sum(iIf([url/@category]='facebook',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Twitter<br /> </td> 
   <td> @twitter<br /> </td> 
   <td> De som van alle @totalClicks waarvoor de categorie URL gelijk is aan "twitter".<br /> </td> 
   <td> Sum(iIf([url/@category]='twitter',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Delicious<br /> </td> 
   <td> @delicious<br /> </td> 
   <td> Som van alle @totalClicks waarvoor de categorie URL "heerlijk"evenaart.<br /> </td> 
   <td> Sum(iIf([url/@category]='delicious',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Digg<br /> </td> 
   <td> @digg<br /> </td> 
   <td> De som van alle @totalClicks waarvoor de categorie URL gelijk is aan "digg".<br /> </td> 
   <td> Sum(iIf([url/@category]='digg',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Google<br /> </td> 
   <td> @google<br /> </td> 
   <td> De som van alle @totalClicks waarvoor de categorie URL gelijk is aan "google".<br /> </td> 
   <td> Sum(iIf([url/@category]='google',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Linkedin<br /> </td> 
   <td> @linkedin<br /> </td> 
   <td> De som van alle @totalClicks waarvoor de categorie URL gelijk is aan "linkedin".<br /> </td> 
   <td> Sum(iIf([url/@category]='linkedin',@totalClicks,0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

**Aandelen**

<table> 
 <thead> 
  <tr> 
   <th> <strong>Label</strong> <br /> </th> 
   <th> <strong>Veldnaam</strong> <br /> </th> 
   <th> <strong>Beschrijving van de indicator</strong> <br /> </th> 
   <th> <strong>Indicatorberekeningsformule</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Aantal aandelen<br /> </td> 
   <td> @forward<br /> </td> 
   <td> Het totale aantal berichten dat op dit sociale netwerk wordt gedeeld.<br /> </td> 
   <td> Sum(iIf([url/@category]="Waarde van het type sociaal netwerk",@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Onderverdeling<br /> </td> 
   <td> @percent<br /> </td> 
   <td> Percentage van het aantal aandelen op dit sociale netwerk vergeleken met het totale aantal aandelen.<br /> </td> 
   <td> percent(@forward, sum(@forward))<br /> </td> 
  </tr> 
  <tr> 
   <td> Beeldfrequentie delen<br /> </td> 
   <td> @rate<br /> </td> 
   <td> Aantal aandelen op dit netwerk in vergelijking met het aantal te leveren berichten.<br /> </td> 
   <td> @forward / @totalTarget<br /> </td> 
  </tr> 
 </tbody> 
</table>

**Geopende items**

<table> 
 <thead> 
  <tr> 
   <th> <strong>Label</strong> <br /> </th> 
   <th> <strong>Veldnaam</strong> <br /> </th> 
   <th> <strong>Beschrijving van de indicator</strong> <br /> </th> 
   <th> <strong>Indicatorberekeningsformule</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Aantal geopende <br /> </td> 
   <td> @open<br /> </td> 
   <td> Het totale aantal tekstspatiëringsregels in de tabel voor webtracering.<br /> </td> 
   <td> Aantal<br /> </td> 
  </tr> 
  <tr> 
   <td> Onderverdeling<br /> </td> 
   <td> @percentOpen<br /> </td> 
   <td> Percentage van het aantal dat op dit sociale netwerk wordt geopend in vergelijking met het totale aantal dat wordt geopend.<br /> </td> 
   <td> percent(@open, sum(@open))<br /> </td> 
  </tr> 
  <tr> 
   <td> Snelheid van openen<br /> </td> 
   <td> @rateOpen<br /> </td> 
   <td> Aantal opent op dit sociale netwerk in vergelijking met het totale aantal te leveren berichten.<br /> </td> 
   <td> @open / @totalTarget<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Statistieken over het delen van activiteiten {#statistics-on-sharing-activities-1}

Dit rapport is gebaseerd op de **[!UICONTROL Delivery]** (nms:delivery), **[!UICONTROL Consolidated tracking]** (nms:trackingStats) en **[!UICONTROL Web tracking]** (nms:webTrackingLog) tabellen.

<table> 
 <thead> 
  <tr> 
   <th> <strong>Label</strong> <br /> </th> 
   <th> <strong>Veldnaam</strong> <br /> </th> 
   <th> <strong>Beschrijving van de indicator</strong> <br /> </th> 
   <th> <strong>Indicatorberekeningsformule</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Nieuwe contactpersonen<br /> </td> 
   <td> @newContacts<br /> </td> 
   <td> Aantal bezoekers dat is gekoppeld aan een ontvanger.<br /> </td> 
   <td> Formule: count(@id)<br /> Filter: @ontvanger-id!= 0<br /> </td> 
  </tr> 
  <tr> 
   <td> Geopende items<br /> </td> 
   <td> @opened<br /> </td> 
   <td> Aantal van alle @ids met een type URL gelijk aan "Open".<br /> </td> 
   <td> count (Iif([url/@type] = 2, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Aandelen<br /> </td> 
   <td> @shared<br /> </td> 
   <td> URL-categorie opgenomen in 'email', 'facebook', 'twitter', 'delicious', 'digg', 'google' , 'linkedin'<br /> Aantal alle @totalClicks met een URL-categorie die gelijk is aan 'email', 'facebook', 'twitter', 'delicious', 'digg', 'google' of 'linkedin'.1/&gt;<br /> </td> 
   <td> count (Iif([url/@category] IN (email', 'facebook' , 'twitter' , 'delicious' , 'digg' , 'google' , 'linkedin'), @totalClicks, 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Besturingssystemen {#operating-systems-1}

Dit rapport is gebaseerd op de **[!UICONTROL Internet Browser Statistics]** lijst (nms:userAgentsStats).

**Algemene statistieken**

<table> 
 <thead> 
  <tr> 
   <th> <strong>Label</strong> <br /> </th> 
   <th> <strong>Veldnaam</strong> <br /> </th> 
   <th> <strong>Beschrijving van de indicator</strong> <br /> </th> 
   <th> <strong>Indicatorberekeningsformule</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Bezoekers<br /> </td> 
   <td> @totalVisitors / @days<br /> </td> 
   <td> Het dagelijkse gemiddelde van het totale aantal ontvangers waarop het besturingssysteem zich richt en dat ten minste één keer op een levering heeft geklikt.<br /> </td> 
   <td> Sum(@bezoekers)<br /> </td> 
  </tr> 
  <tr> 
   <td> Weergegeven pagina's<br /> </td> 
   <td> @totalPages / @days<br /> </td> 
   <td> Het dagelijkse gemiddelde van het totale aantal klikken op de leveringsverbindingen per werkende systemen voor alle leveringen.<br /> </td> 
   <td> Sum(@pagina's)<br /> </td> 
  </tr> 
  <tr> 
   <td> Gebruiksfrequentie<br /> </td> 
   <td> -<br /> </td> 
   <td> Uitsplitsing van bezoekers per besturingssysteem in verhouding tot het totale aantal bezoekers.<br /> </td> 
   <td> percent(@totalVisitors, som(@totalVisitors))<br /> </td> 
  </tr> 
 </tbody> 
</table>

**Statistieken per besturingssysteem**

<table> 
 <thead> 
  <tr> 
   <th> <strong>Label</strong> <br /> </th> 
   <th> <strong>Veldnaam</strong> <br /> </th> 
   <th> <strong>Beschrijving van de indicator</strong> <br /> </th> 
   <th> <strong>Indicatorberekeningsformule</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Gebruiksfrequentie<br /> </td> 
   <td> @bezoekers<br /> </td> 
   <td> Percentage van het aantal bezoekers per dag op dit besturingssysteem in vergelijking met het aantal bezoekers dat op de dag met de meeste bezoekers wordt gemeten.<br /> </td> 
   <td> percent(sum(@bezoekers), max(@bezoekersOfDay))<br /> </td> 
  </tr> 
  <tr> 
   <td> Globale snelheid<br /> </td> 
   <td> -<br /> </td> 
   <td> Percentage bezoekers per versie vergeleken met het totale aantal bezoekers op alle besturingssystemen.<br /> </td> 
   <td> percent(@totalVisitors, @globalVisitors)<br /> </td> 
  </tr> 
  <tr> 
   <td> Relatieve snelheid<br /> </td> 
   <td> -<br /> </td> 
   <td> Percentage bezoekers per versie vergeleken met het totale aantal bezoekers dat dit besturingssysteem gebruikt.<br /> </td> 
   <td> percent(@totalVisitors, som(@totalVisitors))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Abonnementsbeheer {#subscription-tracking-1}

Dit rapport is gebaseerd op de **[!UICONTROL Services]** lijst (nms:dienst).

<table> 
 <thead> 
  <tr> 
   <th> <strong>Label</strong> <br /> </th> 
   <th> <strong>Veldnaam</strong> <br /> </th> 
   <th> <strong>Beschrijving van de indicator</strong> <br /> </th> 
   <th> <strong>Indicatorberekeningsformule</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Geregistreerd<br /> </td> 
   <td> @_subscriber<br /> </td> 
   <td> Aantal geregistreerde personen op de vorige dag.<br /> </td> 
   <td> sum(Iif(@created &lt; addDays(getDate(), (-1)), 1, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Abonnementen<br /> </td> 
   <td> @_subscription<br /> </td> 
   <td> Aantal abonnementen (@action = 1) op de vorige dag.<br /> </td> 
   <td> sum(Iif(@action = 1 en @date &gt; addDays(getDate(), (-1)), 1, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Uitschrijvingen<br /> </td> 
   <td> @_unsubscription<br /> </td> 
   <td> aantal aflossingen (actie = 0) op de vorige dag.<br /> </td> 
   <td> sum(Iif(@action = 0 en @date &gt; addDays(getDate(), (-1)), 1, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Evolutie<br /> </td> 
   <td> -<br /> </td> 
   <td> Aantal abonnementen min het aantal afboekingen. Het tarief wordt berekend in verhouding tot het totale aantal abonnees.<br /> </td> 
   <td> IF(number(@_subscription) &gt; number(@_unsubscription), '+', '')+format(@_subscription - @_unsubscription, 'number', '##0')+ Iif(@_subscriber&gt;0,' (' + format(100*percent(@_subscription - @_unsubscription, @_subscriber), 'number', '#,##0.0 0')+ '%)','')<br /> </td> 
  </tr> 
  <tr> 
   <td> Loyalty<br /> </td> 
   <td> -<br /> </td> 
   <td> Het tarief van de loyaliteit van de abonnee voor de verwante periode.<br /> </td> 
   <td> 1-percent(@_unsubscription,@_subscriber+@_subscription-@_unsubscription)<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Trackingsindicatoren {#tracking-indicators-1}

Dit rapport is gebaseerd op de **[!UICONTROL Delivery and tracking statistics]** (nms:deliveryLogStats) en **[!UICONTROL Consolidated tracking]** (nms:trackingStats) lijsten.

<table> 
 <thead> 
  <tr> 
   <th> <strong>Label</strong> <br /> </th> 
   <th> <strong>Veldnaam</strong> <br /> </th> 
   <th> <strong>Beschrijving van de indicator</strong> <br /> </th> 
   <th> <strong>Indicatorberekeningsformule</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Te leveren berichten<br /> </td> 
   <td> @toDeliver<br /> </td> 
   <td> Aantal van het aantal wideLogs na doelanalyse.<br /> </td> 
   <td> sum([eigenschappen/@toDeliver])<br /> </td> 
  </tr> 
  <tr> 
   <td> Succes<br /> </td> 
   <td> @successWithoutSeeds<br /> </td> 
   <td> Aantal berichten waarvoor het veld "zaadadres" gelijk is aan "Nee" en met een status die gelijk is aan "Door de dienstverlener in aanmerking genomen", "Verzonden" of "Ontvangen op de mobiele telefoon".<br /> </td> 
   <td> sum([indicatoren/@succes])<br /> </td> 
  </tr> 
  <tr> 
   <td> Er wordt een duidelijk onderscheid gemaakt tussen de bereikte populatie<br /> </td> 
   <td> @estimatedRecipientOpen<br /> </td> 
   <td> Extrapolatie van het aantal verschillende e-mails wordt geopend voor alle e-mails op basis van het aantal verschillende e-mails in HTML-indeling.<br /> </td> 
   <td> IF([@toDeliver] - [@text]) = 0, 0, round(toDouble(@receivingOpen) * [@toDeliver] / ([@toDeliver] - [@text]), 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Som van opent op de bevolking bereikt<br /> </td> 
   <td> @estimatedTotalRecipientOpen<br /> </td> 
   <td> Extrapolatie van het totale aantal keren dat wordt geopend voor alle e-mails op basis van het totale aantal e-mails dat wordt geopend in HTML-indeling.<br /> </td> 
   <td> IF([@toDeliver] - [@text]) = 0, 0, round(toDouble(@totalRecipientOpen) * [@toDeliver] / ([@toDeliver] - [@text]), 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Klik op de koppeling <br /> om uw abonnement op te zeggen </td> 
   <td> @optOut<br /> </td> 
   <td> Aantal alle @ids met een categorie URL gelijk aan "Opt-out".<br /> </td> 
   <td> count(Iif([url/@type]=3, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Klik op de koppeling naar de spiegelpagina<br /> </td> 
   <td> @mirrorPage<br /> </td> 
   <td> Aantal alle @ids met een categorie URL gelijk aan "pagina van de Spiegel".<br /> </td> 
   <td> count(Iif([url/@type]=6, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Schatting van voorwaarts<br /> </td> 
   <td> @forward<br /> </td> 
   <td> Verschil tussen het aantal verschillende personen en het aantal verschillende ontvangers dat ten minste één keer in de e-mail heeft geklikt.<br /> </td> 
   <td> @personClick - @receivingClick<br /> </td> 
  </tr> 
  <tr> 
   <td> Verzendt<br /> </td> 
   <td> @successWithoutSeeds<br /> </td> 
   <td> Aantal berichten waarvoor het veld "zaadadres" gelijk is aan "Nee" en met een status die gelijk is aan "door de ontvanger in aanmerking genomen", "Verzonden" of "Ontvangen op mobiel".<br /> </td> 
   <td> sum([indicatoren/@succes])<br /> </td> 
  </tr> 
  <tr> 
   <td> Klachten<br /> </td> 
   <td> @Letters<br /> </td> 
   <td> Aantal berichten met een status gelijk aan "Ontbroken"en een reden gelijk aan "adres op lijst van afgewezen personen".<br /> </td> 
   <td> Count(@status=2 en msg/@failureReason=8)<br /> </td> 
  </tr> 
  <tr> 
   <td> Geopende items<br /> </td> 
   <td> @receivingOpen<br /> </td> 
   <td> Aantal alle @wideLog-ids in alle volgende logboeken.<br /> </td> 
   <td> Countdifferent ([@wideLog-id])<br /> </td> 
  </tr> 
  <tr> 
   <td> Klikken<br /> </td> 
   <td> @receivingClick<br /> </td> 
   <td> Afzonderlijke telling van @wideLog-ids met een type URL gelijk aan "E-mail klik". <br /> </td> 
   <td> Countdifferent(Iif([url/@type]=1, @wideLog-id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Onbewerkte reactiviteit<br /> </td> 
   <td> -<br /> </td> 
   <td> Percentage van het aantal ontvangers dat ten minste één keer op een levering heeft geklikt in vergelijking met het aantal ontvangers dat een levering ten minste één keer heeft geopend.<br /> </td> 
   <td> percent (@receikClick,@receipOpen)<br /> </td> 
  </tr> 
  <tr> 
   <td> Onderscheiden klikt op de bereikte populatie<br /> </td> 
   <td> @personClick<br /> </td> 
   <td> Aantal alle @source-id's met een URL-categorie die gelijk is aan "Email click".<br /> </td> 
   <td> Countdifferent(Iif([url/@type]=1, @source-id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Gecumuleerde klikken<br /> </td> 
   <td> @totalRecipientClick<br /> </td> 
   <td> Aantal van alle @ids met een categorie URL die "E-mail klikt"evenaart.<br /> </td> 
   <td> count(Iif([url/@type]=1, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Ontvanger klikt<br /> </td> 
   <td> @receivingClick<br /> </td> 
   <td> Het aantal van de @wideLog-ids met een type URL dat "E-mail klikt"evenaart.<br /> </td> 
   <td> Countdifferent(Iif([url/@type]=1, @wideLog-id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Geschatte reactiviteit<br /> </td> 
   <td> -<br /> </td> 
   <td> Verhouding van het aantal ontvangers dat ten minste eenmaal op een levering heeft geklikt ten opzichte van de schatting van de ontvangers die de levering ten minste eenmaal hebben geopend.<br /> </td> 
   <td> percent(@receivingClick, @estimentRecipientOpen<br /> </td> 
  </tr> 
  <tr> 
   <td> Bezochte pagina's<br /> </td> 
   <td> @totalWebPage<br /> </td> 
   <td> Aantal van alle @ids met een type URL gelijk aan "Web"of "Transactie".<br /> </td> 
   <td> count(Iif([url/@type]=4 of [url/@type]=5, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Transacties<br /> </td> 
   <td> @transaction<br /> </td> 
   <td> Aantal van alle @ids met een type URL gelijk aan "Transactie".<br /> </td> 
   <td> count(Iif([url/@type]=5, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Totaal aantal<br /> </td> 
   <td> @amount<br /> </td> 
   <td> De som van webTrackingLog/@hoeveelheden met een URL-type dat gelijk is aan "Transaction". <br /> </td> 
   <td> Sum(Iif([url/@type]=5, webTrackingLog/@amount, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Gemiddeld transactiebedrag<br /> </td> 
   <td> -<br /> </td> 
   <td> Verhouding van het totale bedrag ten opzichte van het aantal transacties.<br /> </td> 
   <td> div(@amount, @transaction)<br /> </td> 
  </tr> 
  <tr> 
   <td> Items<br /> </td> 
   <td> @article<br /> </td> 
   <td> Som van webTrackingLog/@artikelen met een type URL dat "Transactie"evenaart.<br /> </td> 
   <td> Sum(Iif([url/@type]=5, webTrackingLog/@artikel, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Gemiddeld aantal items per transactie<br /> </td> 
   <td> -<br /> </td> 
   <td> Verhouding van het aantal posten ten opzichte van het aantal transacties.<br /> </td> 
   <td> div(@artikel, @transaction)<br /> </td> 
  </tr> 
  <tr> 
   <td> Gemiddeld bedrag per bericht<br /> </td> 
   <td> -<br /> </td> 
   <td> Verhouding van het totale bedrag in verhouding tot het aantal te leveren berichten.<br /> </td> 
   <td> div(@amount, @toDeliver)<br /> </td> 
  </tr> 
  <tr> 
   <td> E-mail<br /> </td> 
   <td> @email<br /> </td> 
   <td> Som van alle @totalClicks met een categorie URL die "e-mail"evenaart.<br /> </td> 
   <td> Sum(iIf([url/@category]='email',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Facebook<br /> </td> 
   <td> @facebook<br /> </td> 
   <td> Som van alle @totalClicks met een categorie URL die "facebook".<br /> evenaart </td> 
   <td> Sum(iIf([url/@category]='facebook',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Twitter<br /> </td> 
   <td> @twitter<br /> </td> 
   <td> De som van alle @totalClicks met een categorie URL die gelijk is aan "twitter".<br /> </td> 
   <td> Sum(iIf([url/@category]='twitter',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Delicious<br /> </td> 
   <td> @delicious<br /> </td> 
   <td> Som van alle @totalClicks met een categorie URL die "heerlijk"evenaart.<br /> </td> 
   <td> Sum(iIf([url/@category]='delicious',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Digg<br /> </td> 
   <td> @digg<br /> </td> 
   <td> De som van alle @totalClicks met een categorie URL die "digg".<br /> evenaart </td> 
   <td> Sum(iIf([url/@category]='digg',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Google<br /> </td> 
   <td> @google<br /> </td> 
   <td> De som van alle @totalClicks met een categorie URL die "google" evenaart.<br /> </td> 
   <td> Sum(iIf([url/@category]='google',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Linkedin<br /> </td> 
   <td> @linkedin<br /> </td> 
   <td> Som van alle @totalClicks met een categorie URL die "verbonden in"evenaart.<br /> </td> 
   <td> Sum(iIf([url/@category]='linkedin',@totalClicks,0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## URL&#39;s en klikpaden {#urls-and-click-streams-1}

Dit rapport is gebaseerd op de **[!UICONTROL Delivery]** lijst (nms:levering).

<table> 
 <thead> 
  <tr> 
   <th> <strong>Label</strong> <br /> </th> 
   <th> <strong>Veldnaam</strong> <br /> </th> 
   <th> <strong>Beschrijving van de indicator</strong> <br /> </th> 
   <th> <strong>Indicatorberekeningsformule</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Reactiviteit<br /> </td> 
   <td> @reactivity<br /> </td> 
   <td> Verhouding van het aantal beoogde ontvangers die ten minste eenmaal op een levering hebben geklikt ten opzichte van het geschatte aantal beoogde ontvangers dat een levering ten minste eenmaal heeft geopend.<br /> </td> 
   <td> percent([indicatoren/@receivingClick], [indicatoren/@estimentRecipientOpen])<br /> </td> 
  </tr> 
  <tr> 
   <td> Duidelijke klikken<br /> </td> 
   <td> @differentClicks<br /> </td> 
   <td> Verhouding van het aantal verschillende personen die ten minste één keer in een levering hebben geklikt ten opzichte van het aantal berichten dat met succes is geleverd.<br /> </td> 
   <td> percent([indicatoren/@personClick], [indicatoren/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> Gecumuleerde klikken<br /> </td> 
   <td> @totalClicks<br /> </td> 
   <td> Verhouding van het totale aantal klikken door gerichte ontvangers in vergelijking met het aantal berichten die met succes worden geleverd.<br /> </td> 
   <td> percent([indicatoren/@totalRecipientClick], [indicatoren/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> Klikken<br /> </td> 
   <td> @_click<br /> </td> 
   <td> Aantal alle @totalClicks met een primaire URL-sleutel anders dan 1<br /> </td> 
   <td> count(if([@url-id]!= 1, @totalClicks, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Klikken (%)<br /> </td> 
   <td> -<br /> </td> 
   <td> Percentage van het aantal klikken in verhouding tot het totale aantal gecumuleerde klikken.<br /> </td> 
   <td> percent(@_click, @_total)<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Leveringsoverzicht {#delivery-summary-1}

Dit rapport is gebaseerd op de **[!UICONTROL Delivery]** lijst (nms:levering).

<table> 
 <thead> 
  <tr> 
   <th> <strong>Label</strong> <br /> </th> 
   <th> <strong>Veldnaam</strong> <br /> </th> 
   <th> <strong>Beschrijving van de indicator</strong> <br /> </th> 
   <th> <strong>Indicatorberekeningsformule</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Eerste populatie<br /> </td> 
   <td> @totalTarget<br /> </td> 
   <td> Het totale aantal ontvangers waarop de levering gericht is.<br /> </td> 
   <td> sum([eigenschappen/@totalTarget])<br /> </td> 
  </tr> 
  <tr> 
   <td> Berichten die door de regel worden verworpen<br /> </td> 
   <td> @reject<br /> </td> 
   <td> Aantal adressen genegeerd tijdens de analyse in overeenstemming met typologieregels: adres niet gespecificeerd, quarantined, op lijst van afgewezen personen, enz.<br /> </td> 
   <td> sum([eigenschappen/@weiger])<br /> </td> 
  </tr> 
  <tr> 
   <td> Te leveren berichten<br /> </td> 
   <td> @toDeliver<br /> </td> 
   <td> Het totale aantal berichten dat na leveringsanalyse moet worden geleverd.<br /> </td> 
   <td> sum([eigenschappen/@toDeliver])<br /> </td> 
  </tr> 
  <tr> 
   <td> Succes<br /> </td> 
   <td> @success<br /> </td> 
   <td> Aantal berichten verwerkt met succes.<br /> </td> 
   <td> sum([indicatoren/@succes])<br /> </td> 
  </tr> 
  <tr> 
   <td> Fouten<br /> </td> 
   <td> @error<br /> </td> 
   <td> Totaal aantal fouten gecumuleerd tijdens leveringen en automatische stuiterverwerking.<br /> </td> 
   <td> sum([indicatoren/@error])<br /> </td> 
  </tr> 
  <tr> 
   <td> Nieuwe quarantines<br /> </td> 
   <td> @newQuarantine<br /> </td> 
   <td> Aantal in quarantaine geplaatste adressen na een levering ontbreekt (onbekend gebruiker, ongeldig domein).<br /> </td> 
   <td> sum([indicatoren/@newQuarantine])<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Hot clicks {#hot-clicks-1}

Dit rapport is gebaseerd op de tabellen Delivery(nms:delivery) en **[!UICONTROL Consolidated tracking]** (nms:trackingStats).

Dit rapport toont de berichtinhoud (HTML en/of tekst) met, op elke verbinding, het percentage klikt op verbindingen. De belemmeringen van de verpersoonlijking unsubscription verbindingen en de verbindingen van de spiegelpagina worden in de totale gecumuleerde kliks in aanmerking genomen maar niet getoond in het rapport.

## Statistieken {#tracking-statistics-1} bijhouden

Dit rapport is gebaseerd op de **[!UICONTROL Delivery]** lijst (nms:levering).

<table> 
 <thead> 
  <tr> 
   <th> <strong>Label</strong> <br /> </th> 
   <th> <strong>Veldnaam</strong> <br /> </th> 
   <th> <strong>Beschrijving van de indicator</strong> <br /> </th> 
   <th> <strong>Indicatorberekeningsformule</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Transacties<br /> </td> 
   <td> @transactions<br /> </td> 
   <td> Som van alle @totalClicks met een type URL dat "Transactie"evenaart.<br /> </td> 
   <td> sum(Iif([url/@type] = 5, @totalClicks, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Klikken<br /> </td> 
   <td> @clicks<br /> </td> 
   <td> De som van alle @totalClicks met een type URL dat "E-mailklik"evenaart.<br /> </td> 
   <td> sum(Iif([url/@type] = 1, @totalClicks, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Open<br /> </td> 
   <td> @open<br /> </td> 
   <td> De som van alle @totalClicks met een primaire URL-sleutel die gelijk is aan 1.<br /> </td> 
   <td> sum(Iif([@url-id] = 1, @totalClicks, 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Leveringsstatistieken {#delivery-statistics-1}

Dit rapport is gebaseerd op de **[!UICONTROL Delivery and tracking statistics]** lijst (nms:deliveryLogStats).

<table> 
 <thead> 
  <tr> 
   <th> <strong>Label</strong> <br /> </th> 
   <th> <strong>Veldnaam</strong> <br /> </th> 
   <th> <strong>Beschrijving van de indicator</strong> <br /> </th> 
   <th> <strong>Indicatorberekeningsformule</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Verwerkte e-mails<br /> </td> 
   <td> @processing<br /> </td> 
   <td> Het totale aantal berichten met een status die "Klaar", "Verzonden"of "Ontbroken"evenaart.<br /> </td> 
   <td> @prepare + @error + @success<br /> </td> 
  </tr> 
  <tr> 
   <td> Afgeleverd<br /> </td> 
   <td> @success<br /> </td> 
   <td> Aantal berichten dat is verwerkt.<br /> </td> 
   <td> indicatoren/@success<br /> </td> 
  </tr> 
  <tr> 
   <td> Harde grenzen<br /> </td> 
   <td> @hardBounce<br /> </td> 
   <td> Het totale aantal berichten met een status die "Ontbroken"en een reden evenaart die "Gebruiker onbekend".<br /> </td> 
   <td> @unknownUser<br /> </td> 
  </tr> 
  <tr> 
   <td> Zachte grenzen<br /> </td> 
   <td> @softBounce<br /> </td> 
   <td> Totaal van alle berichten met een status die "Ontbroken"en een reden evenaart die "onbereikbaar", "inbox volledig", "ongeldig domein", "gehandicapte rekening", "niet verbonden"of "verworpen"<br /> evenaart </td> 
   <td> @unbereikable + @mailBoxFull + @invalidDomain + @disabled + @notConnected + @deny<br /> </td> 
  </tr> 
  <tr> 
   <td> Geopende items<br /> </td> 
   <td> @receivingOpen<br /> </td> 
   <td> Totaal aantal @wideLog-ids in het volgende logboeken.<br /> </td> 
   <td> Countdifferent ([@wideLog-id])<br /> </td> 
  </tr> 
  <tr> 
   <td> Klikken<br /> </td> 
   <td> @personClick<br /> </td> 
   <td> Het totale aantal @source-ids waarvoor de categorie URL gelijk is aan "Email click". <br /> </td> 
   <td> Countdifferent(Iif([url/@type]=1, @source-id, 0)) <br /> </td> 
  </tr> 
  <tr> 
   <td> Uitschrijvingen<br /> </td> 
   <td> @optOut<br /> </td> 
   <td> Totaal aantal @ids waarvoor de categorie URL "Opt-out".<br /> </td> 
   <td> count(Iif([url/@type]=3, @id, 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Uitsplitsing van openen {#breakdown-of-opens-1}

Dit rapport is gebaseerd op **Deliveries** (nms:delivery) en **Tracking logs** (nms:trackingLogRcp) tabellen.

<table> 
 <thead> 
  <tr> 
   <th> <strong>Label</strong> <br /> </th> 
   <th> <strong>Veldnaam</strong> <br /> </th> 
   <th> <strong>Beschrijving van de indicator</strong> <br /> </th> 
   <th> <strong>Indicatorberekeningsformule</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Geopende items<br /> </td> 
   <td> @totalRecipientOpen<br /> </td> 
   <td> De som van alle @id met een primaire URL-sleutel gelijk aan 1 (open). <br /> </td> 
   <td> count(Iif([@url-id] = 1, @id, 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Overige indicatoren {#other-indicators}

De indicator **Verzonden** (@sent), die via **Leveringen (nms:levering) > Indicatoren** wordt betreden beantwoordt aan het totale aantal SMS dat naar de dienstverlener wordt verzonden. Deze indicator wordt alleen gebruikt voor SMS-leveringen en mag niet worden gebruikt voor andere typen leveringen (niet te verwarren met de **@success** en **@processing** indicatoren).

## Indicatorsynchronisatie {#indicator-synchronization}

Als u desynchronisatie of inconsistentie voor bepaalde indicatoren ervaart, selecteer de betrokken levering in de ontdekkingsreiziger van Adobe Campaign, klik met de rechtermuisknop aan en kies **[!UICONTROL Action>Recompute delivery and tracking indicators]**. Klik **[!UICONTROL Next]**, dan klik **[!UICONTROL Finish]**.

![](assets/s_ncs_user_recalculate_indicators.png)

## Tekstspatiëring wordt geopend {#tracking-opens-}

Als Adobe Campaign het bericht pas kan detecteren nadat het is geopend, moet de ontvanger de afbeeldingen in de e-mail downloaden. HTML en Multipart/Alternative e-mails bevatten een afbeelding van 0 pixels, waarmee u berichten kunt detecteren die zijn geopend. Aangezien berichten in tekstopmaak geen afbeeldingen bevatten, is het onmogelijk om te bepalen of ze zijn geopend of niet. Waarden die worden berekend op basis van het bericht dat wordt geopend, zijn altijd schattingen vanwege de foutmarge die is gekoppeld aan de beeldweergave.

## Doelpersonen / ontvangers {#targeted-persons---recipients}

In sommige rapporten maakt Adobe Campaign onderscheid tussen doelpersonen en doelgroepen.

De gerichte ontvangers zijn alle ontvangers aan wie de levering werd verzonden.

Het aantal personen omvat de beoogde ontvangers plus alle personen aan wie de e-mail is doorgestuurd. Telkens wanneer er een open of een klik in nieuwe browser (waar het bericht nog niet in is geopend), wordt een andere persoon toegevoegd aan de statistieken.

Als u bijvoorbeeld een e-mail (verzonden door Adobe Campaign) ontvangt op het werk en deze opent of erin klikt, wordt u geteld als een beoogde ontvanger (dus de ontvanger=1, de persoon=1). Als u deze e-mail doorstuurt naar twee vrienden, blijft het aantal beoogde ontvangers gelijk aan één, terwijl het aantal personen gelijk is aan drie. Waarde 3 valt samen met elke open/klik in een nieuwe browser.
