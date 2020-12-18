---
solution: Campaign Classic
product: campaign
title: Voorwaardelijke content
description: Voorwaardelijke content
audience: delivery
content-type: reference
topic-tags: personalizing-deliveries
translation-type: tm+mt
source-git-commit: 20dcdd91d71158bc373db68c3f61f6808b240bd2
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 4%

---


# Voorwaardelijke content{#conditional-content}

Door voorwaardelijke inhoudsgebieden te vormen, kunt u dynamische verpersoonlijking tot stand brengen die op het profiel van de ontvanger bijvoorbeeld wordt gebaseerd. Tekstblokken en/of afbeeldingen worden vervangen wanneer aan een bepaalde voorwaarde wordt voldaan.

![](assets/do-not-localize/how-to-video.png) [Ontdek deze functie in video](#conditionnal-content-video)


## Voorwaarden gebruiken in een e-mail {#using-conditions-in-an-email}

In het onderstaande voorbeeld leert u hoe u een boodschap kunt maken die dynamisch is gepersonaliseerd op basis van het geslacht en de belangen van de ontvanger.

* Weergave met &quot;Mr&quot; of &quot;Mej.&quot; volgens de waarde van het veld **[!UICONTROL Gender]** (M of F) in de gegevensbron,
* Persoonlijke vergadering van een nieuwsbrief of een promotieaanbod volgens de aangegeven of geconstateerde belangen:

   * Rente 1 — > Blok 1
   * Rente 2 — > Blok 2
   * Rente 3 — > Blok 3
   * Rente 4 — > Blok 4

Voer de volgende stappen uit om voorwaardelijke inhoud te maken op basis van de waarde van een veld:

1. Klik op het verpersoonlijkingspictogram en selecteer **[!UICONTROL Conditional content > If]**.

   ![](assets/s_ncs_user_conditional_content02.png)

   De verpersoonlijkingselementen worden opgenomen in het berichtlichaam. U moet hen nu vormen.

1. Vul vervolgens de parameters van de expressie **if** in.

   Dit doet u als volgt:

   * Selecteer het eerste element van de expressie **`<field>`** (dit element wordt standaard gemarkeerd tijdens het invoegen van de expressie **if**) en klik op het verpersoonlijkingspictogram om het te vervangen door het testveld.

      ![](assets/s_ncs_user_conditional_content03.png)

   * Vervang **`<value>`** door de waarde van het veld waaraan aan de voorwaarde wordt voldaan. Deze waarde moet tussen aanhalingstekens staan.
   * Geef de inhoud op die moet worden ingevoegd wanneer aan de voorwaarde wordt voldaan. Dit kan tekst, een afbeelding, een formulier, een hypertekstkoppeling enzovoort zijn.

      ![](assets/s_ncs_user_conditional_content04.png)

1. Klik op het tabblad **[!UICONTROL Preview]** om de inhoud van het bericht weer te geven op basis van de ontvanger van de levering:

   * Een ontvanger selecteren waarvoor de voorwaarde waar is:

      ![](assets/s_ncs_user_conditional_content05.png)

   * Een ontvanger selecteren waarvoor de voorwaarde niet waar is:

      ![](assets/s_ncs_user_conditional_content06.png)

U kunt andere gevallen toevoegen en verschillende inhoud definiëren op basis van de waarden van een of meer velden. Hiervoor gebruikt u **[!UICONTROL Conditional content > Else]** en **[!UICONTROL Conditional content > Else if]**. Deze expressies worden op dezelfde manier geconfigureerd als de expressie **if**.

![](assets/s_ncs_user_conditional_content07.png)

>[!CAUTION]
>
>Als u de JavaScript-syntaxis wilt respecteren, moeten de &lt;%**tekens worden verwijderd nadat u** Anders **en** Anders if **voorwaarden hebt toegevoegd.**

Klik op **[!UICONTROL Preview]** en selecteer een ontvanger om de voorwaardelijke inhoud weer te geven.

![](assets/s_ncs_user_conditional_content08.png)

## Meertalige e-mail {#creating-multilingual-email} maken

In het onderstaande voorbeeld leert u hoe u een meertalige e-mail kunt maken. De inhoud wordt in de ene of de andere taal weergegeven, afhankelijk van de voorkeurstaal van de ontvanger.

1. Maak een e-mail en selecteer de doelpopulatie. In dit voorbeeld wordt de voorwaarde voor het weergeven van de ene versie of de andere gebaseerd op de waarde **Language** van het profiel van de ontvanger. In dit voorbeeld worden deze waarden ingesteld op **EN**, **FR**, **ES**.
1. Klik in de HTML-inhoud van de e-mail op het tabblad **[!UICONTROL Source]** en plak de volgende code:

   ```
   <% if (language == "EN" ) { %>
   <DIV id=en-version>Hello <%= recipient.firstName %>,</DIV>
   <DIV>Discover your new offers!</DIV>
   <DIV><a href="https://www.adobe.com/products/en">www.adobe.com/products/en</A></FONT></DIV><%
    } %>
   <% if (language == "FR" ) { %>
   <DIV id=fr-version>Bonjour <%= recipient.firstName %>,</DIV>
   <DIV>Découvrez nos nouvelles offres !</DIV>
   <DIV><a href="https://www.adobe.com/products/fr">www.adobe.com/products/fr</A></DIV><%
    } %>
    <% if (language == "ES" ) { %>
   <DIV id=es-version><FONT face=Arial>
   <DIV>Olà <%= recipient.firstName %>,</DIV>
   <DIV>Descubra nuestros nuevas ofertas !</DIV>
   <DIV><a href="https://www.adobe.com/products/es">www.adobe.com/products/es</A></DIV>
   <% } %>
   ```

1. Test e-mailinhoud op het tabblad **[!UICONTROL Preview]** door ontvangers met verschillende voorkeurstalen te selecteren.

   >[!NOTE]
   >
   >Aangezien er geen alternatieve versie is gedefinieerd in de e-mailinhoud, moet u de doelpopulatie filteren voordat u de e-mail verzendt.

## Video over zelfstudie {#conditionnal-content-video}

Leer hoe u voorwaardelijke inhoud aan een levering kunt toevoegen op het voorbeeld van een meertalige nieuwsbrief.

>[!VIDEO](https://video.tv.adobe.com/v/24926?quality=12)

Er zijn [hier](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=nl) extra Campaign Classic hoe kan ik-video&#39;s beschikbaar.
