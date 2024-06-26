---
product: campaign
title: Tag voor webspatiëring definiëren
description: Tag voor webspatiëring definiëren
feature: Application Settings
role: Data Engineer, Developer
exl-id: 0b5575be-57e7-4eee-9c0a-e9ef4b0931bf
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 1%

---

# Tag voor webtracking: definitie{#web-tracking-tag-definition}



Een tag voor webtracering is een URL die is samengesteld met de juiste parameters en die via een HTTP-query naar de omleidingsserver wordt verzonden.

## Formaat van de te verzenden gegevens {#format-of-the-data-to-be-sent}

De indeling van een URL voor webtracering is als volgt: **https://`<name_of_redirection_server>`:`<port>`/r/`<random_number>`?`<parameters>`**

>[!NOTE]
>
>Met het willekeurige nummer dat aan de URL wordt toegevoegd, worden problemen voorkomen die worden veroorzaakt doordat browsers webpagina&#39;s in cache plaatsen.

De volgende tabel bevat een lijst met speciale parameters die door de omleidingsserver worden ondersteund.

<table>
                     <thead>
                        <tr>
                           <th>Naam</th>
                           <th>Type</th>
                           <th>Beschrijving</th> 
                        </tr> 
                     </thead>
                     <tbody>
                        <tr>
                           <td>
                              <p>ID</p> 
                           </td>
                           <td>
                              <p>Sessiecookie</p> 
                           </td>
                           <td>
                              <p>Identificatiecode van levering en ontvanger.</p> 
                           </td> 
                        </tr>
                        <tr>
                           <td>
                              <p>uuid230</p> 
                           </td>
                           <td>
                              <p>Permanent cookie</p> 
                           </td>
                           <td>
                              <p>Ontvanger-id (nuttig als het sessiecookie ontbreekt).</p> 
                           </td> 
                        </tr>
                        <tr>
                           <td>
                              <p>gelabeld</p> 
                           </td>
                           <td>
                              <p>URL-parameter</p> 
                           </td>
                           <td>
                              <p>Id van bijgehouden webpagina: dit is de enige verplichte parameter.</p> 
                           </td> 
                        </tr>
                        <tr>
                           <td>
                              <p>jobid</p> 
                           </td>
                           <td>
                              <p>URL-parameter</p> 
                           </td>
                           <td>
                              <p>Leverings-id die moet worden gebruikt als er geen sessiecookie is. Deze waarde moet worden uitgedrukt in hexadecimale waarden.
                              </p> 
                           </td> 
                        </tr>
                        <tr>
                           <td>
                              <p>rcpid</p> 
                           </td>
                           <td>
                              <p>URL-parameter</p> 
                           </td>
                           <td>
                              <p>Parameter gebruikt om de internetgebruiker te identificeren. De indeling van deze parameter is "name=value", waarbij de naam een veld is van het ontvangende schema. Deze parameter heeft voorrang op het herkenningsteken in het zittingskoekje.
                              </p> 
                           </td> 
                        </tr> 
                     </tbody>  
                  </table>

**Enkele URL&#39;s voor webtracking**

* Bezoek naar een homepage met id&#39;s

  **https://myserver.adobe.com/r/9862?tagid=home**

* Gegevens over bedrijfsvolumes verzamelen

  **https://myserver.adobe.com/r/4567?tagid=command&amp;amount=100&amp;article=2l**

* Veld opgeven om ontvanger te zoeken

  **https://myserver.adobe.com/r/2353?tagid=home&amp;rcpid=saccount%3D10**

  Een ontvanger van wie het rekeningnummer 10 is, wordt naar de homepage verzonden.

* Een standaardlevering gebruiken

  **https://myserver.adobe.com/r/2456?tagid=home&amp;jobid=e6**

  Een ontvanger wordt verzonden naar de homepage. Deze informatie zal in de levering met herkenningsteken 230 (e6 in gegevensbestand 16) worden opgeslagen tenzij een zittingskoekje die een leveringsherkenningsteken bevat met deze vraag wordt verzonden.

>[!NOTE]
>
>Alle waarden die via URL-parameters naar de omleidingsserver worden verzonden, moeten URL-gecodeerd zijn. In de gegeven voorbeelden worden de tekens &#39;=&#39; en &#39;|&#39; gecodeerd als respectievelijk &#39;%3D&#39; en &#39;%7C&#39;.

## Methoden voor gegevensoverdracht {#data-transmission-methods}

De volgende methoden zijn mogelijk:

* De URL invoegen in het dialoogvenster **&quot;src&quot;** kenmerk van een HTML **`<img>`** -tag wordt opgenomen in de webpagina die u wilt bijhouden.
* Directe aanroep naar de omleidingsserver wanneer de webpagina die u wilt bijhouden, wordt gegenereerd.
