---
product: campaign
title: Voorwaardelijke content
description: Leer hoe u voorwaardelijke inhoud toevoegt
badge-v8: label="Ook van toepassing op v8" type="Positive" tooltip="Ook van toepassing op campagne v8"
feature: Personalization, Multilingual Messages
role: User
exl-id: 12595ee4-6a52-4e06-b80d-85fe633a5a11
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 5%

---

# Voorwaardelijke content{#conditional-content}

Door voorwaardelijke inhoudsgebieden te vormen, kunt u dynamische verpersoonlijking tot stand brengen die op het profiel van de ontvanger bijvoorbeeld wordt gebaseerd. Tekstblokken en/of afbeeldingen worden vervangen wanneer aan een bepaalde voorwaarde wordt voldaan.

![](assets/do-not-localize/how-to-video.png) [Ontdek deze functie in video](#conditionnal-content-video)


## Voorwaarden in een e-mail gebruiken {#using-conditions-in-an-email}

In het onderstaande voorbeeld leert u hoe u een boodschap kunt maken die dynamisch is gepersonaliseerd op basis van het geslacht en de belangen van de ontvanger.

* Weergave met &quot;Mr&quot; of &quot;ms&quot; volgens de waarde van het veld **[!UICONTROL Gender]** (M of F) in de gegevensbron,
* Persoonlijke vergadering van een nieuwsbrief of een promotieaanbod volgens de aangegeven of geconstateerde belangen:

   * Rente 1 — > Blok 1
   * Rente 2 — > Blok 2
   * Rente 3 — > Blok 3
   * Rente 4 — > Blok 4

Voer de volgende stappen uit om voorwaardelijke inhoud te maken op basis van de waarde van een veld:

1. Klik op het verpersoonlijkingspictogram en selecteer **[!UICONTROL Conditional content > If]** .

   ![](assets/s_ncs_user_conditional_content02.png)

   De verpersoonlijkingselementen worden opgenomen in het berichtlichaam. U moet hen nu vormen.

1. Daarna, vul de parameters van **in als** uitdrukking.

   Dit doet u als volgt:

   * Selecteer het eerste element van de uitdrukking, **`<field>`**, (door gebrek, wordt dit element benadrukt tijdens toevoeging van **als** uitdrukking) en klik het verpersoonlijkingspictogram om het met het testgebied te vervangen.

     ![](assets/s_ncs_user_conditional_content03.png)

   * Vervang **`<value>`** door de waarde van het veld waaraan aan de voorwaarde wordt voldaan. Deze waarde moet tussen aanhalingstekens staan.
   * Geef de inhoud op die moet worden ingevoegd wanneer aan de voorwaarde wordt voldaan. Dit kan tekst, een afbeelding, een formulier, een hypertekstkoppeling enzovoort zijn.

     ![](assets/s_ncs_user_conditional_content04.png)

1. Klik op het tabblad **[!UICONTROL Preview]** om de inhoud van het bericht weer te geven op basis van de ontvanger van de zending:

   * Een ontvanger selecteren waarvoor de voorwaarde waar is:

     ![](assets/s_ncs_user_conditional_content05.png)

   * Een ontvanger selecteren waarvoor de voorwaarde niet waar is:

     ![](assets/s_ncs_user_conditional_content06.png)

U kunt andere gevallen toevoegen en verschillende inhoud definiëren op basis van de waarden van een of meer velden. Gebruik **[!UICONTROL Conditional content > Else]** en **[!UICONTROL Conditional content > Else if]** om dit te doen. Deze uitdrukkingen worden gevormd op de zelfde manier zoals **als** uitdrukking.

![](assets/s_ncs_user_conditional_content07.png)

>[!CAUTION]
>
>Om de syntaxis van JavaScript te respecteren, moeten **%> &lt;%** karakters na het toevoegen van **anders** en **anders worden geschrapt als** voorwaarden.

Klik op **[!UICONTROL Preview]** en selecteer een ontvanger om de voorwaardelijke inhoud weer te geven.

![](assets/s_ncs_user_conditional_content08.png)

## Meertalige e-mail maken {#creating-multilingual-email}

In het onderstaande voorbeeld leert u hoe u een meertalige e-mail kunt maken. De inhoud wordt in de ene of de andere taal weergegeven, afhankelijk van de voorkeurstaal van de ontvanger.

1. Maak een e-mail en selecteer de doelpopulatie. In dit voorbeeld, zal de voorwaarde om één versie of andere te tonen op de **Taal** waarde van het profiel van de ontvanger worden gebaseerd. In dit voorbeeld, worden deze waarden geplaatst aan **EN**, **FR**, **ES**.
1. Klik in de inhoud van de HTML-e-mail op de tab **[!UICONTROL Source]** en plak de volgende code:

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

Deze video laat zien hoe u voorwaardelijke content aan een levering kunt toevoegen, bijvoorbeeld aan een meertalige nieuwsbrief.

>[!VIDEO](https://video.tv.adobe.com/v/24926?quality=12)

De extra Campaign Classic hoe te video&#39;s zijn beschikbaar [ hier ](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=nl).
