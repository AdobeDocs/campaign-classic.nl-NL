---
product: campaign
title: Doelpopulatie definiëren
description: Leer hoe u de doelpopulatie definieert
feature: Audiences, Proofs
role: User
exl-id: d0ed7be7-3147-4cb8-9ce7-ea51602e9048
source-git-commit: 41296a0acaee93d31874bf58287e51085c6c1261
workflow-type: tm+mt
source-wordcount: '1593'
ht-degree: 2%

---

# Doelpopulatie definiëren {#defining-the-target-population}

Voor elke levering kunt u verschillende typen doelpopulaties definiëren:

* **Belangrijkste publiek**: profielen die berichten zullen ontvangen. [Meer informatie](steps-defining-the-target-population.md#selecting-the-main-target)
* **Bewijs**: ontvangers van proefdrukberichten, betrokken bij de bevestigingscyclus. [Meer informatie](steps-defining-the-target-population.md#defining-a-specific-proof-target)
* **zaadadressen**: ontvangers die uit het leveringsdoel zijn maar de levering (in de context van een marketing campagne slechts) zullen ontvangen. [Meer informatie](about-seed-addresses.md)
* **de groepen van de Controle**: bevolking die niet de levering zal ontvangen, die aan spoorgedrag en campagneeffect (in de context van een marketing campagne slechts) wordt gebruikt. [Meer informatie](../../campaign/using/marketing-campaign-target.md#defining-a-control-group).

## Selecteer de belangrijkste ontvangers van de levering {#selecting-the-main-target}

In de meeste gevallen wordt het hoofddoel opgehaald uit de Adobe Campaign-database (standaardmodus). Ontvangers kunnen echter ook in een extern bestand worden opgeslagen. Lees meer in [deze sectie](steps-defining-the-target-population.md#selecting-external-recipients).

Volg onderstaande stappen om de ontvangers van een levering te selecteren:

1. Selecteer **[!UICONTROL To]** in de leveringseditor.
1. Als de ontvangers in het gegevensbestand worden opgeslagen, kies de eerste optie.

   ![](assets/s_ncs_user_wizard_email02a.png)

1. Selecteer de doeltoewijzing in de vervolgkeuzelijst **[!UICONTROL Target mapping]** . Adobe Campaign standaarddoelafbeelding is **[!UICONTROL Recipients]**, gebaseerd op **nms:ontvangend** schema.

   Andere doeltoewijzingen zijn beschikbaar, en sommige kunnen met uw specifieke configuratie verwant zijn. Voor meer op doelafbeeldingen, verwijs naar [ Uitgezochte een doelafbeelding ](selecting-a-target-mapping.md).

1. Klik op de knop **[!UICONTROL Add]** om beperkingsfilters te definiëren.

   Vervolgens kunt u het type filter selecteren dat u wilt toepassen:

   ![](assets/s_ncs_user_wizard_email02b.png)

   U kunt ontvangers selecteren aan de hand van de doeltypen die in de database zijn gedefinieerd. Als u een doeltype wilt gebruiken, selecteert u het en klikt u op **[!UICONTROL Next]** . Voor elk doel kunt u de betrokken ontvangers weergeven door op het tabblad **[!UICONTROL Preview]** te klikken. Voor bepaalde typen doelen kunt u met de knop **[!UICONTROL Refine target]** verschillende doelcriteria combineren.

   De volgende doeltypen worden standaard aangeboden:

   * **[!UICONTROL Filtering conditions]** : met deze optie kunt u een query definiëren en het resultaat weergeven. De methode om vragen te bepalen wordt voorgesteld in [ deze sectie ](../../platform/using/creating-filters.md#creating-an-advanced-filter).
   * **[!UICONTROL Subscribers of an information service]** : met deze optie kunt u een nieuwsbrief selecteren waarop de ontvangers moeten worden geabonneerd om de levering die wordt gemaakt als doel te hebben.

     ![](assets/s_ncs_user_wizard_email02c.png)

   * **[!UICONTROL Recipients of a delivery]** : met deze optie kunt u de ontvangers van een bestaande levering definiëren als een doelcriterium. U moet dan de levering in de lijst selecteren:

     ![](assets/s_ncs_user_wizard_email02d.png)

   * **[!UICONTROL Delivery recipients belonging to a folder]** : met deze optie kunt u een leveringsmap selecteren en de ontvangers van de leveringen in die map als doel instellen.

     ![](assets/s_ncs_user_wizard_email02e.png)

     U kunt het gedrag van ontvangers filteren door een keuze te maken in de vervolgkeuzelijst:

     ![](assets/s_ncs_user_wizard_email02f.png)

     >[!NOTE]
     >
     >Met de optie **[!UICONTROL Include sub-folders]** kunt u ook de leveringen uitvoeren die zich bevinden in mappen in de boomstructuur onder het geselecteerde knooppunt.

   * **[!UICONTROL Recipients included in a folder]** : met deze optie kunt u de profielen in een specifieke map van de boomstructuur als doel instellen.
   * **[!UICONTROL A recipient]** : met deze optie kunt u een specifieke ontvanger selecteren uit de profielen in de database.
   * **[!UICONTROL A list of recipients]** : met deze optie kunt u een lijst met ontvangers als doel instellen. De lijsten worden voorgesteld in [ deze sectie ](../../platform/using/creating-and-managing-lists.md).
   * **[!UICONTROL User filters]** : met deze optie hebt u toegang tot de vooraf geconfigureerde filters om deze te gebruiken als filtercriteria voor profielen in de database. Vooraf gevormde filters worden voorgesteld in [ deze sectie ](../../platform/using/creating-filters.md#saving-a-filter).
   * Met de optie **[!UICONTROL Exclude recipients corresponding to this segment]** kunt u zich richten op ontvangers die niet aan de gedefinieerde doelcriteria voldoen. Als u deze optie wilt gebruiken, selecteert u het desbetreffende vak en past u vervolgens de focus toe, zoals eerder is gedefinieerd, om de resulterende profielen uit te sluiten.

     ![](assets/s_ncs_user_wizard_email02g.png)

1. Voer in het veld **[!UICONTROL Label]** een naam in voor dit doel. Standaard is het label het label van het eerste doelcriterium. Voor een combinatie is het beter om een expliciete naam te gebruiken.
1. Klik op **[!UICONTROL Finish]** om het geconfigureerde doel te valideren.

   De gedefinieerde doelcriteria worden samengevat in het centrale gedeelte van het hoofdtabblad voor doelconfiguratie. Klik op een criterium om de inhoud ervan weer te geven (configuratie en voorvertoning). Als u een criterium wilt verwijderen, klikt u op het kruisje dat zich na het label bevindt.

   ![](assets/s_ncs_user_wizard_email02h.png)

### Externe ontvangers selecteren {#selecting-external-recipients}

U kunt een levering starten bij ontvangers die niet in de database zijn opgeslagen, maar wel in een extern bestand. We sturen hier bijvoorbeeld een levering naar ontvangers die zijn geïmporteerd uit een tekstbestand.

Dit doet u als volgt:

1. Klik op de koppeling **[!UICONTROL To]** om de ontvangers van de levering te selecteren.
1. Selecteer de optie **[!UICONTROL Defined in an external file]** .

   ![](assets/s_ncs_user_wizard_external_recipients.png)

1. Ontvangers worden standaard in de database geïmporteerd. U moet **[!UICONTROL Target mapping]** selecteren. Voor meer op doelafbeeldingen, verwijs naar [ Uitgezochte een doelafbeelding ](selecting-a-target-mapping.md)

   U kunt ook **[!UICONTROL Do not import the recipients into the database]** kiezen.

1. Klik tijdens het importeren van de ontvangers op de koppeling **[!UICONTROL File format definition...]** om het externe bestand te selecteren en te configureren.

   Voor meer informatie bij de invoer van gegevens, verwijs naar [ deze sectie ](../../platform/using/executing-import-jobs.md#step-2---source-file-selection).

1. Klik op **[!UICONTROL Finish]** en configureer de levering als standaardlevering.

>[!CAUTION]
>
>Wanneer het bepalen van de inhoud van het bericht voor e-maillevering, omvat niet de verbinding aan de spiegelpagina; het kan niet op deze leveringswijze worden geproduceerd.

### Uitsluitingsinstellingen definiëren {#define-exclusion-settings}

Adresfouten en kwaliteitsbeoordelingen worden geleverd door de serviceprovider (IAP). Deze informatie wordt automatisch bijgewerkt in het ontvangende profiel na leveringsacties en met dossiers die door dienstverleners zijn teruggekeerd. Deze kan alleen-lezen in het profiel worden weergegeven.

U kunt adressen uitsluiten die een bepaald aantal opeenvolgende fouten hebben bereikt, of waarvan de kwaliteitsclassificatie onder een drempel is die in dit venster wordt gespecificeerd. U kunt ook kiezen of u niet-gekwalificeerde adressen waarvoor geen gegevens zijn geretourneerd, wilt autoriseren.

>[!NOTE]
>
>Als twee ontvangers dezelfde voornaam, achternaam, postcode en plaats in een directe postbestelling hebben, zal een dubbele fout voorkomen en zal het duplicaat niet in aanmerking worden genomen.

Het tabblad **[!UICONTROL Exclusions]** wordt gebruikt om het aantal berichten te beperken.

>[!NOTE]
>
>Standaardparameters worden aanbevolen, maar u kunt de instellingen naar wens aanpassen. Deze opties mogen echter alleen door een deskundige gebruiker worden gewijzigd om elk misbruik en elke fout te voorkomen.

Klik op de koppeling **[!UICONTROL Edit...]** om de standaardconfiguratie te wijzigen.

![](assets/s_ncs_user_wizard_email02i.png)

De volgende opties zijn beschikbaar:

* **[!UICONTROL Exclude duplicate addresses during delivery]**. Deze optie is standaard actief: hiermee kunt u dubbele e-mailadressen tijdens de levering verwijderen. De toegepaste strategie kan variëren afhankelijk van hoe Adobe Campaign wordt gebruikt en het type gegevens in het gegevensbestand.

  De standaardwaarde van de optie kan voor elke leveringsmalplaatje worden gevormd.

  Bijvoorbeeld:

   * Levering van een nieuwsbrief of elektronische documentlevering. In sommige gevallen wordt geen uitsluiting van duplicaten toegepast als de gegevens geen native duplicaten hebben. Een paar dat zich abonneert op hetzelfde e-mailadres, kan verwachten twee specifieke persoonlijke e-mailberichten te ontvangen: een die op naam aan elk individu is gericht. In dit geval kan deze optie niet zijn geselecteerd.
   * Aflevering van een marketingcampagne: dubbele uitsluiting is van essentieel belang om te voorkomen dat te veel berichten naar dezelfde ontvanger worden gestuurd. In dat geval kunt u deze optie selecteren.

     Als u deze optie uitschakelt, hebt u toegang tot een extra optie: **[!UICONTROL Keep duplicate records (same identifier)]** . Hiermee kunt u meerdere leveringen toestaan aan ontvangers die aan verschillende doelcriteria voldoen.

     ![](assets/s_ncs_user_wizard_email02j.png)

* **[!UICONTROL Exclude recipients who no longer want to be contacted]** , d.w.z. ontvangers wier e-mailadressen in de lijst van gewezen personen staan (&#39;Weigeren&#39;). Deze optie moet geselecteerd blijven om de beroepsethiek van e-marketing en de wetgeving inzake e-handel te eerbiedigen.
* **[!UICONTROL Exclude quarantined recipients]**. Met deze optie kunt u profielen met een adres dat niet reageert, uitsluiten van het doel. We raden u ten zeerste aan deze optie geselecteerd te houden.

  >[!NOTE]
  >
  >Voor verdere informatie over quarantainebeheer, verwijs naar [ begrijp quarantainebeheer ](understanding-quarantine-management.md).

* **[!UICONTROL Limit delivery]** aan een bepaald aantal berichten. Met deze optie kunt u het maximum aantal berichten invoeren dat moet worden verzonden. Als de inhoud van het doel het aangegeven aantal berichten overschrijdt, wordt een willekeurige selectie toegepast op het doel.

### De omvang van de doelpopulatie verminderen {#reducing-the-size-of-the-target-population}

U kunt de grootte van de doelpopulatie verminderen. Hiervoor geeft u het aantal ontvangers op dat u wilt exporteren in het veld **[!UICONTROL Requested quantity]** .

![](assets/s_ncs_user_edit_del_exe_tab.png)

## Ontvangers van proefdrukberichten selecteren {#selecting-the-proof-target}

De proef is een speciaal bericht dat u een levering laat testen alvorens het naar het belangrijkste doel te verzenden. Ontvangers van het bewijs zijn verantwoordelijk voor het goedkeuren van zowel de vorm als de inhoud van het bericht.

![](assets/do-not-localize/how-to-video.png) [Ontdek deze functie in video](#seeds-and-proofs-video)


Voer de onderstaande stappen uit om het doel van de proefdrukken te selecteren:

1. Klik op de koppeling **[!UICONTROL To]**.
1. Klik op de tab **[!UICONTROL Target of the proofs]** .
1. Klik op het veld **[!UICONTROL Targeting mode]** om de methode te kiezen die u wilt toepassen: **[!UICONTROL Definition of a specific proof target]** , **[!UICONTROL Substitution of the address]** , **[!UICONTROL Seed addresses]** of **[!UICONTROL Specific target and seed addresses]** .

>[!NOTE]
>
>Gewoonlijk kan het doel voor de proefdruk worden toegevoegd aan het hoofddoel. Selecteer hiertoe de gewenste optie in de onderste sectie van het tabblad **[!UICONTROL Main target]** .

## Een specifiek proefdrukdoel definiëren {#defining-a-specific-proof-target}

Als u het proefdrukdoel selecteert, kunt u met de optie **[!UICONTROL Definition of a specific proof target]** de proefdrukontvangers selecteren in de profielen in de database.

Selecteer deze optie om ontvangers te kiezen met de knop **[!UICONTROL Add]** , zoals bij het definiëren van het hoofddoel. Zie [ selecteren het belangrijkste doel ](steps-defining-the-target-population.md#selecting-the-main-target).

![](assets/s_ncs_user_wizard_email01_143.png)

Voor meer bij bewijs dat verzendt, verwijs naar [ deze sectie ](steps-validating-the-delivery.md#sending-a-proof).

### Adres vervangen in proefdruk gebruiken {#using-address-substitution-in-proof}

In plaats van speciale ontvangers in de database te selecteren, kunt u de optie **[!UICONTROL Substitution of the address]** gebruiken.

Met deze optie kunt u de profielen van de ontvangers van de levering gebruiken en hun e-mailadressen vervangen door een of meer andere adressen waarop de proefdruk wordt uitgevoerd.

Als deze optie is geselecteerd, worden de proefdrukadressen ingevuld in een speciale editor waarmee u de vervanging(en) kunt configureren.

![](assets/s_ncs_user_wizard_email_bat_substitute.png)

De configuratie wordt uitgevoerd als volgt:

1. Klik op het pictogram **[!UICONTROL Add]** om een vervanging te definiëren.
1. Voer het gewenste adres in dat u wilt gebruiken of selecteer het adres in de lijst.
1. Selecteer het profiel dat u in de proefdruk wilt gebruiken: sla de **[!UICONTROL Random]** -waarde in de **[!UICONTROL Profile to use]** -kolom op om de gegevens van een willekeurig profiel van het doel in de proefdruk te gebruiken.

   ![](assets/s_ncs_user_wizard_email_bat_substitute_choose.png)

1. Klik op het pictogram **[!UICONTROL Detail]** om een profiel van het hoofddoel te selecteren, zoals in het volgende voorbeeld:

   ![](assets/s_ncs_user_wizard_email_bat_substitute_select.png)

   U kunt zo veel vervangende adressen definiëren als nodig is.

## zaadadressen gebruiken als proefdruk {#using-seed-addresses-as-proof}

U kunt **[!UICONTROL Seed addresses]** gebruiken als doel voor proefdrukken: met deze optie kunt u een lijst met bestaande beginadressen gebruiken of importeren.

![](assets/s_ncs_user_wizard_email_bat_control_address.png)

>[!NOTE]
>
>De zaadadressen worden voorgesteld in [ Ongeveer zaadadressen ](about-seed-addresses.md).

Met de optie **[!UICONTROL Specific target and Seed addresses]** kunt u de definitie van een specifiek proefdrukdoel combineren met het gebruik van beginadressen. De gerelateerde configuraties worden vervolgens in twee aparte subtabbladen gedefinieerd.

Zie ook:

* [Proofingdoel selecteren](#selecting-the-proof-target)
* [Seedadressen](about-seed-addresses.md)
* [Gebruiksscenario: seedadressen selecteren op criteria](use-case-selecting-seed-addresses-on-criteria.md)

## Video over zelfstudie {#seeds-and-proofs-video}

In deze video leert u hoe u zaden en proefdrukken aan een bestaande e-mail kunt toevoegen en hoe u deze kunt verzenden.

>[!VIDEO](https://video.tv.adobe.com/v/25606?quality=12)

De extra Campaign Classic hoe te video&#39;s zijn beschikbaar [ hier ](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=nl).
