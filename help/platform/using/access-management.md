---
title: Toegangsbeheer
seo-title: Toegangsbeheer
description: Toegangsbeheer
seo-description: null
page-status-flag: never-activated
uuid: 3f0cfa8f-1511-4445-9acb-b5be46e78295
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: administration-basics
discoiquuid: c0eb06fd-192c-4ee4-9a38-c9bedbe6aea0
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 92f4047628eca0fc1d71aded0329720c094463bd

---


# Toegangsbeheer{#access-management}

## Machtigingen {#about-permissions}

Met Adobe Campaign kunt u de rechten definiëren en beheren die aan de verschillende operatoren zijn toegewezen. Dit zijn een reeks rechten en beperkingen die autoriseren of weigeren:

* Toegang tot bepaalde functies (via genoemde rechten);
* Toegang tot bepaalde registers,
* Opstellen, wijzigen en/of verwijderen van registers (acties, contacten, campagnes, groepen, enz.).

De machtigingen zijn van toepassing op operatorprofielen of groepen operatoren.

De instructies worden uitgevoerd met veiligheidsparameters die zijn gekoppeld aan de verbindingsmodus van de operator met Adobe Campaign. For more on this, refer to [this page](../../installation/using/configuring-campaign-server.md#defining-security-zones).

Er zijn twee soorten toestemmingen u aan een gebruiker kunt verlenen:

* U kunt groepen operatoren definiëren waaraan u rechten toewijst en de operatoren vervolgens koppelen aan een of meer groepen. Op deze manier kunt u rechten opnieuw gebruiken en de consistentie van operatorprofielen verhogen. Het vergemakkelijkt ook het beheer en het onderhoud van profielen. De creatie en het beheer van de groep worden voorgesteld in de groepen [van de](#operator-groups)Exploitant.
* U kunt benoemde rechten rechtstreeks toewijzen aan gebruikers, in sommige gevallen om de rechten die via groepen zijn toegewezen, te overladen. Deze rechten worden weergegeven in [Benoemde rechten](#named-rights).

>[!NOTE]
>
>Voordat u begint met het definiëren van machtigingen, raadt Adobe u aan de checklist voor [beveiligingsconfiguraties](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/security.html)te lezen.

## Operatoren {#operators}

### Operatoren {#about-operators}

Een exploitant is een gebruiker van de Campagne van Adobe die toestemmingen heeft om zich aan te melden en acties uit te voeren.

Operatoren worden standaard opgeslagen in het **[!UICONTROL Administration > Access management > Operators]** knooppunt.

![](assets/s_ncs_user_list_operators.png)

Operatoren kunnen handmatig worden gemaakt of toegewezen aan een bestaande LDAP-directory.

De volledige procedure voor het maken van een operator wordt in [deze pagina](#creating-an-operator)beschreven.

Raadpleeg [deze pagina](../../installation/using/connecting-through-ldap.md)voor meer informatie over de integratie met Adobe Campagne en LDAP.

>[!CAUTION]
>
>Operatoren moeten zijn gekoppeld aan een beveiligingszone om zich aan te melden bij een instantie. Raadpleeg [deze pagina](../../installation/using/configuring-campaign-server.md#defining-security-zones)voor meer informatie over beveiligingszones in Adobe Campaign.

Gebruikers kunnen ook rechtstreeks verbinding maken met Adobe-campagne met hun Adobe-id. Raadpleeg deze [pagina](../../integrations/using/about-adobe-id.md)voor meer informatie.

### Een operator maken {#creating-an-operator}

Voer de volgende stappen uit om een nieuwe operator te maken en machtigingen te verlenen:

1. Klik op de **[!UICONTROL New]** knop boven de lijst met operatoren en voer de details van de nieuwe operator in.

   ![](assets/s_ncs_user_operator_new.png)

1. Geef de naam **[!UICONTROL Identification parameters]** van de gebruiker op: zijn aanmelding, wachtwoord en naam. De operator gebruikt de aanmelding en het wachtwoord om u aan te melden bij Adobe Campaign. Zodra de gebruiker het programma wordt geopend, kunnen zij hun wachtwoord via het **[!UICONTROL Tools > Change password]** menu veranderen. Het e-mailadres van de exploitant is essentieel omdat het de exploitant in staat stelt meldingen te ontvangen, bijvoorbeeld bij de verwerking van goedkeuringen.

   In deze sectie kunt u ook een operator koppelen aan een organisatie-entiteit. Raadpleeg de [pagina](../../campaign/using/about-distributed-marketing.md)voor meer informatie hierover.

1. Selecteer in de **[!UICONTROL Operator access rights]** sectie de machtigingen die aan de operator zijn verleend.

   Als u rechten aan de operator wilt toewijzen, klikt u op de **[!UICONTROL Add]** knop boven de lijst met rechten en selecteert u een groep operatoren in de lijst met beschikbare groepen:

   ![](assets/s_ncs_user_permissions_operators.png)

   U kunt ook een of meer benoemde rechten selecteren (zie [Benoemde rechten](#named-rights)). Klik hiertoe op de pijl rechts van het **[!UICONTROL Folder]** veld en selecteer **[!UICONTROL Named rights]**:

   ![](assets/s_ncs_user_rights_operators.png)

   Selecteer groepen en/of benoemde rechten die u wilt toewijzen en klik **[!UICONTROL OK]** om te valideren.

1. Klik **[!UICONTROL Ok]** om de operator te maken: het profiel wordt toegevoegd aan de lijst met bestaande operatoren.

   ![](assets/operator_profile_new.png)

>[!NOTE]
>
>U kunt de operatoren naar wens ordenen door nieuwe operatormappen te maken. Klik hiertoe met de rechtermuisknop op de operatormap en selecteer **[!UICONTROL Add an 'Operators' folder]**.

Nadat het profiel van de operator is gemaakt, kunt u de gegevens ervan toevoegen of bijwerken. Klik hiertoe op het **[!UICONTROL Edit]** tabblad.

![](assets/operator_edit_profile.png)

>[!NOTE]
>
>In het **[!UICONTROL Session timeout]** veld kunt u de vertraging vóór de FDA-sessietime-out aanpassen. Raadpleeg voor meer informatie [over Federated Data Access](../../platform/using/about-fda.md).

### Tijdzone van de operator {#time-zone-of-the-operator}

Op het **[!UICONTROL General]** tabblad kunt u de tijdzone van de operator selecteren. Operatoren werken standaard in de tijdzone van de server. Het is echter mogelijk een andere tijdzone te selecteren met de vervolgkeuzelijst.

De configuratie van tijdzones wordt beschreven in [deze pagina](../../installation/using/time-zone-management.md).

>[!NOTE]
>
>Voor samenwerkingsverbanden binnen verschillende tijdzones moeten datums in UTC worden opgeslagen. Datums worden in de juiste tijdzone geconverteerd in de volgende context: wanneer een datum in de gebruikerstijdzone wordt getoond, wanneer de dossiers worden ingevoerd en uitgevoerd, wanneer een e-maillevering gepland is, wanneer de activiteiten in een werkschema (planner, wacht, tijdbeperking, enz.) worden gepland
>
>Restricties en aanbevelingen met betrekking tot deze contexten worden weergegeven in verwante secties van de documentatie van Adobe Campagne.

Daarnaast kunt u in de **[!UICONTROL Regional settings]** vervolgkeuzelijst de notatie selecteren voor het weergeven van datums en getallen.

### Opties voor toegangsrechten {#access-rights-options}

Gebruik het **[!UICONTROL Access rights]** tabblad om de groepen en benoemde rechten bij te werken die aan de operator zijn gekoppeld.

![](assets/operator_profile_security_options.png)

Met de **[!UICONTROL Edit the access parameters...]** koppeling hebt u toegang tot de volgende opties:

* Met de **[!UICONTROL Disable account]** optie kunt u de account van de operator uitschakelen: hij heeft geen toegang meer tot Adobe Campaign.
* Met de **[!UICONTROL Forbid access from the rich client]** optie kunt u het gebruik van Adobe Campaign beperken tot [webtoegang](../../platform/using/adobe-campaign-workspace.md#console-and-web-access) of via API&#39;s: toegang tot de Adobe Campaign-clientconsole is niet meer beschikbaar.
* Het is mogelijk om een veiligheidszone aan de exploitant te verbinden. For more on this, refer to [this page](../../installation/using/configuring-campaign-server.md#defining-security-zones).
* U kunt een vertrouwd IP masker ook bepalen gebruikend de aangewezen verbinding.

   De operator kan verbinding maken met Adobe Campaign zonder een wachtwoord in te voeren als het IP-adres in deze lijst staat.

   U kunt ook een set IP-adressen opgeven die zonder wachtwoord verbinding mogen maken, zoals in het volgende voorbeeld:

   ![](assets/operator_trustip.png)

   >[!NOTE]
   >
   >Om toegang tot uw platform veilig te houden, moet deze optie met zorg worden gebruikt.

* Met de **[!UICONTROL Restrict to information found in sub-folders of:]** optie kunt u de rechten beperken die aan de operator van een map worden toegewezen. Alleen de submappen van het knooppunt dat in deze optie is opgegeven, zijn zichtbaar voor de gebruiker:

   ![](assets/s_ncs_user_restrictions_operators.png)

   >[!CAUTION]
   >
   >Dit is een zeer strenge beperking en het moet met voorzichtigheid worden gebruikt. Een exploitant die met dit type van rechten het programma wordt geopend kan slechts de inhoud van de gespecificeerde omslag zien, en heeft geen toegang tot een andere knoop van de boom via de ontdekkingsreiziger. Afhankelijk van de functies waartoe hij toegang heeft (bijvoorbeeld: werkstromen), kan hij gegevens tonen die gewoonlijk in knopen worden opgeslagen die hij niet kan zien.

### Mappen, goedkeuring en taken van een exploitant {#folders--approval-and-tasks-of-an-operator}

Op het **[!UICONTROL Audit]** tabblad kunt u informatie weergeven die betrekking heeft op de operator. De verschillende tabbladen worden automatisch toegevoegd op basis van de instellingen die zijn gedefinieerd in het interventiegebied van de operator.

U hebt toegang tot:

* De lijst met rechten voor mappen die aan de operator zijn gekoppeld.

   ![](assets/operator_folder_permissions.png)

   >[!NOTE]
   >
   >Raadpleeg voor meer informatie [het toegangsbeheer](#folder-access-management)van mappen.

* Het erkenningslogboek van de exploitant.

   ![](assets/operator_profile_validations.png)

* De lijst met discussieforums waarop ze zich hebben geabonneerd.
* Gebeurtenissen in hun kalender.
* De lijst met taken die aan hen zijn toegewezen.

### Standaardoperatoren {#default-operators}

Adobe Campaign gebruikt technische operatoren met profielen die standaard zijn geconfigureerd: Beheerder (&#39;admin&#39;), Facturering (&#39;facturering&#39;), Controle, Web application agent (&#39;webapp&#39;), enz. Sommige hiervan zijn afhankelijk van de toepassingen en opties die op het platform zijn geïnstalleerd: De &quot;centrale&quot;en &quot;lokale&quot;exploitanten, bijvoorbeeld, zijn slechts zichtbaar als de Verdeelde optie van de Marketing wordt geïnstalleerd.

>[!CAUTION]
>
>Deze technische operatoren worden standaard op de hoogte gesteld wanneer het platform informatieberichten retourneert. We raden u ten zeerste aan een contactbericht voor hen te verzenden.
>
>Om ervoor te zorgen dat webtoepassingen correct werken, raden we u ook aan geen specifieke regionale instellingen voor de operator &#39;webapp&#39; te definiëren.

De technische operator &#39;webapp&#39; heeft standaard het benoemde BEHEERRECHT, wat tot beveiligingsrisico&#39;s kan leiden. We raden u aan dit recht te verwijderen om dit probleem op te lossen. Dit doet u als volgt:

1. Klik in het **[!UICONTROL Administration > Access management > Named rights]** knooppunt **[!UICONTROL New]** om een rechts-item te maken en geef het de naam WEBAPP.

   ![](assets/s_ncs_default_operators_webapp_right.png)

   Benoemde rechten worden beschreven in de sectie [Benoemde rechten](#named-rights) .

1. Selecteer in het **[!UICONTROL Administration > Access management > Operators]** knooppunt de webapplicatieagent (&#39;webapp&#39;).

   Selecteer het **[!UICONTROL Edit]** tabblad, klik vervolgens op het **[!UICONTROL Access rights]** tabblad en verwijder de rechts genoemde BEHEERSING uit de lijst.

   ![](assets/s_ncs_default_operators_webapp_admin_right.png)

   Klik **[!UICONTROL Add]** en selecteer het recht WEBAPP dat u net hebt gecreeerd, dan sparen uw veranderingen.

   ![](assets/s_ncs_default_operators_webapp_webapp_right.png)

1. Wijs de operator &#39;webapp&#39; toegangsrechten toe voor het lezen en schrijven van gegevens voor de mappen die betrekking hebben op deze operator, in de eerste plaats de mappen &#39;Ontvanger&#39;.

   ![](assets/s_ncs_default_operators_webapp_folder_access.png)

   Het wijzigen van rechten voor boommappen wordt beschreven in de sectie [Maptoegangsbeheer](#folder-access-management) .

>[!NOTE]
>
>Raadpleeg de configuratiecontrolelijst [](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/security.html)voor Adobe Campagne Security voor meer informatie over beveiligingsrichtlijnen.

## Exploitantgroepen {#operator-groups}

Operatorgroepen worden gemaakt via het **[!UICONTROL Administration > Access management > Operator groups]** knooppunt in de structuur.

### Een nieuwe operatorgroep maken {#creating-a-new-operator-group}

Voer de volgende stappen uit om een nieuwe operatorgroep te maken:

1. Klik op de **[!UICONTROL New]** knop rechts van de lijst met groepen of klik met de rechtermuisknop op de lijst en kies **[!UICONTROL New]**.
1. Typ in het onderste venster van de sectie op het **[!UICONTROL General]** tabblad de naam en een beschrijving voor deze groep in de desbetreffende velden.

   ![](assets/s_ncs_user_create_operator_gp.png)

1. Klik op het **[!UICONTROL Content]** tabblad om machtigingen voor deze groep te definiëren.
1. Klik op de **[!UICONTROL Add]** knop om een toegewezen recht of een operator te selecteren die u aan de groep wilt koppelen.
1. Klik op de vervolgkeuzelijst of op de map rechts van het **[!UICONTROL Folder]** veld om de toegewezen rechten of operatoren te zoeken die u aan deze groep wilt koppelen.
1. Selecteer de rechten of operatoren die u wilt toevoegen en klik **[!UICONTROL OK]** om te valideren.

   ![](assets/s_ncs_user_create_operator_gp03.png)

   Herhaal deze bewerking om andere rechten of operatoren toe te voegen.

1. Klik op de **[!UICONTROL Save]** knop om de groep aan de lijst toe te voegen.

### Standaardgroepen {#default-groups}

De standaardgroepen met operatoren zijn:

1. Leveringsoperatoren

   De exploitanten in deze groep zijn verantwoordelijk voor het beheer van de leveringen: zij verlenen toegang tot de belangrijkste middelen die voor het creëren van en het voorbereiden van levering worden vereist (campagneretypologieën, leveringsafbeeldingen, standaardmalplaatjes, verpersoonlijkingsblokken, enz.).

   Deze groep bevat de volgende benoemde rechten:

   * LEVERINGEN VOORBEREIDEN: het recht om de leveringsanalyse te maken, te bewerken en te starten;
   * AFLEVERINGEN STARTEN: het recht om eerder geanalyseerde leveringen goed te keuren.

1. Campagne-managers

   De exploitanten in deze groep kunnen marketingcampagnes beheren: hiermee hebt u toegang tot de objecten die aan campagnes zijn gekoppeld (plannen, programma&#39;s, workflows, budgetten, enz.).

   Deze groep bevat de volgende benoemde rechten:

   * MAPPEN INVOEGEN: het recht om mappen in te voegen in de Adobe Campaign-structuur (op voorwaarde dat u bewerkingsrechten hebt voor de betrokken vertakkingen),
   * WORKFLOW: recht om werkstromen te gebruiken.
   >[!NOTE]
   >
   >Met deze groep kunnen operatoren geen leveringen starten.

1. Inhoudsauteurs

   De operatoren in deze groep hebben toegang tot de mappen Inhoud binnen het kader van **Inhoudsbeheer** (optionele Adobe Campagne-module). Deze groep verleent geen aanvullende rechten.

1. Toegang tot rapporten

   Deze groep is gereserveerd voor externe operatoren, voor toegang tot de leveringsrapporten via een webtoegang.

1. Workflow-uitvoering

   Met deze groep kunt u operatoren het recht geven om workflows te beheren die geen verband houden met campagnes.

1. Workflowsupervisors

   De operatoren in deze groep ontvangen een e-mailkennisgeving in geval van waarschuwingen over workflows voor campagnes.

1. Lokaal/centraal beheer

   In deze groepen kunt u **Distributed Marketing** gebruiken (optionele Adobe Campagne-module).

## Benoemde rechten {#named-rights}

Standaard stelt Adobe Campaign een aantal benoemde rechten voor waarmee u de machtigingen kunt definiëren die aan operatoren en groepen operatoren zijn toegewezen. Deze rechten kunnen worden bewerkt vanaf het **[!UICONTROL Administration > Access management > Named rights]** knooppunt van de boomstructuur.

![](assets/s_ncs_admin_named_rights.png)

Deze rechten zijn als volgt:

* **[!UICONTROL ADMINISTRATION]**: Operatoren met het **[!UICONTROL ADMINISTRATION]** recht hebben volledige toegang tot de instantie. Beheerders kunnen elk object, zoals workflow, levering, scripts, enzovoort, uitvoeren, maken, bewerken of verwijderen.

* **[!UICONTROL APPROVAL ADMINISTRATION]**: U kunt meerdere goedkeuringsstappen instellen in workflows en leveringen om ervoor te zorgen dat de huidige status is goedgekeurd door een toegewezen operator of groep. Gebruikers met de **[!UICONTROL APPROVAL ADMINISTRATION]** rechterstatus kunnen goedkeuringsstappen instellen en ook een exploitant of groep van bedieners toewijzen die deze stappen moeten goedkeuren.

* **[!UICONTROL CENTRAL]**: Recht op centraal beheer (Distributed Marketing).

* **[!UICONTROL DELETE FOLDER]**: Rechts om mappen te verwijderen. Met dit recht kunnen gebruikers mappen verwijderen uit de verkennerweergave.

* **[!UICONTROL EDIT FOLDERS]**: Recht om omslageigenschappen zoals interne naam, etiket, bijbehorende beeld, subomslagorde te veranderen, etc.

* **[!UICONTROL EXPORT]**: Gebruikers kunnen gegevens uit hun Adobe Campagne-instanties exporteren naar een bestand op een server of lokale computer met behulp van de **[!UICONTROL EXPORT]** workflowactiviteit.

* **[!UICONTROL FILES ACCESS]**: Recht om toegang voor dossiers te lezen en te schrijven via een manuscript dat in de **[!UICONTROL JavaScript]** werkschemaactiviteit kan worden geschreven om dossiers op een server te lezen/te schrijven.

* **[!UICONTROL IMPORT]**: Recht op het importeren van generieke gegevens. **[!UICONTROL IMPORT]** kunt u gegevens in een andere tabel importeren, terwijl u **[!UICONTROL RECIPIENT IMPORT]** rechts alleen in de ontvangende tabel kunt importeren.

* **[!UICONTROL INSERT FOLDERS]**: Recht om omslagen op te nemen. Gebruikers met de **[!UICONTROL INSERT FOLDERS]** rechtermuisknop kunnen nieuwe mappen maken in de mappenstructuur in de weergave Verkenner.

* **[!UICONTROL LOCAL]**: Recht op lokaal beheer (Distributed Marketing).

* **[!UICONTROL MERGE]**: Rechts om de geselecteerde records samen te voegen tot één record. Als ontvangers bestaan als duplicaten, staat het **[!UICONTROL MERGE]** recht gebruiker toe om de duplicaten te selecteren en hen samen te voegen in een primaire ontvanger.

* **[!UICONTROL PREPARE DELIVERIES]**: Recht om een levering te maken, te bewerken en op te slaan. Gebruikers met het **[!UICONTROL PREPARE DELIVERIES]** recht kunnen ook het analyseproces voor de levering starten.

* **[!UICONTROL PRIVACY DATA RIGHT]**: Recht om privacygegevens te verzamelen en te schrappen. Raadpleeg deze [pagina](https://helpx.adobe.com/campaign/kb/acc-privacy.html)voor meer informatie.

* **[!UICONTROL PROGRAM EXECUTION]**: Recht om bevelen in diverse programmeertalen uit te voeren.

* **[!UICONTROL RECIPIENT IMPORT]**: Recht om ontvangers in te voeren. Gebruikers met **[!UICONTROL RECIPIENT IMPORT]** rechts kunnen een lokaal bestand importeren in de tabel met ontvangers.

* **[!UICONTROL SQL SCRIPT EXECUTION]** Recht om het even welk SQL bevel direct op het gegevensbestand uit te voeren.

* **[!UICONTROL START DELIVERIES]**: Recht om eerder geanalyseerde leveringen goed te keuren. Na de afleveringsanalyse wordt de levering onderbroken in verschillende goedkeuringsstappen en moet deze worden goedgekeurd om te worden hervat. Gebruikers met **[!UICONTROL START DELIVERIES]** recht mogen leveringen goedkeuren.

* **[!UICONTROL USE SQL DATA MANAGEMENT ACTIVITY]**: Recht om uw eigen SQL manuscripten te schrijven gebruikend de SQL activiteit van het Beheer van Gegevens, om het werklijsten tot stand te brengen en te bevolken (zie [deze sectie](../../workflow/using/sql-data-management.md)).

* **[!UICONTROL WORKFLOW]**: Recht om werkstromen uit te voeren. Zonder dit recht kunnen gebruikers geen workflows starten, stoppen of opnieuw starten.

* **[!UICONTROL WEBAPP]**: Recht om Webtoepassingen te gebruiken.

>[!NOTE]
>
>Deze lijst kan verschillen, afhankelijk van de invoegtoepassingen die op het platform zijn geïnstalleerd.

## Matrix toegangsrechten {#access-rights-matrix}

Met standaardgroepen en benoemde rechten hebben operatoren toegang tot bepaalde mappen in de navigatiehiërarchie en kunnen ze lees-, schrijf- en verwijdermachtigingen verlenen.

Adobe Campagne Access Rights Matrix is [hier](/help/platform/using/assets/accessrights.pdf)beschikbaar.

## Toegangsbeheer voor mappen {#folder-access-management}

Elke map van de structuur bevat toegangsrechten voor lezen, schrijven en verwijderen. Om toegang te krijgen tot een bestand, moet een operator of groep operatoren ten minste lees-toegang hebben.

### Machtigingen bewerken in een map {#edit-permissions-on-a-folder}

Voer de volgende stappen uit als u machtigingen voor een specifieke map in de structuur wilt bewerken:

1. Klik met de rechtermuisknop op de map en selecteer **[!UICONTROL Properties...]**.

   ![](assets/s_ncs_user_folder_properties.png)

1. Klik op het **[!UICONTROL Security]** tabblad om machtigingen voor deze map weer te geven.

   ![](assets/s_ncs_user_folder_properties_security.png)

### Machtigingen wijzigen {#modify-permissions}

Als u machtigingen wilt wijzigen, kunt u:

* **Een groep of operator** vervangen. Klik hiertoe op een van de groepen (of operatoren) met rechten voor de map en selecteer een nieuwe groep (of een nieuwe operator) in de vervolgkeuzelijst:

   ![](assets/s_ncs_user_folder_properties_security02.png)

* **Een groep of operator** autoriseren. Klik hiertoe op de **[!UICONTROL Add]** knop en selecteer de groep of operator waaraan u machtigingen voor deze map wilt toewijzen.
* **Verbod een groep of een operator**. Om dit te doen, klik **[!UICONTROL Delete]** en selecteer de groep of de exploitant waarvan u vergunning voor deze omslag wilt verwijderen.
* **Selecteer de rechten die aan een groep of een operator** zijn toegewezen. Klik hiertoe op de betrokken groep of operator, selecteer vervolgens de toegangsrechten die u wilt verlenen en hef de selectie van de andere rechten op.

   ![](assets/s_ncs_user_folder_properties_security03.png)

### Machtigingen voor doorgeven {#propagate-permissions}

U kunt machtigingen en toegangsrechten doorgeven. Selecteer hiertoe de **[!UICONTROL Propagate]** optie in de mapeigenschappen.

De in dit venster gedefinieerde autorisaties worden vervolgens toegepast op alle submappen van het huidige knooppunt. Vervolgens kunt u deze machtigingen voor elke submap te veel laden.

>[!NOTE]
>
>Als u deze optie voor een map wist, wordt deze niet automatisch gewist voor de submappen. U moet dit expliciet wissen voor elk van de submappen.

### Toegang verlenen aan alle marktdeelnemers {#grant-access-to-all-operators}

Als de **[!UICONTROL Security]** optie op het **[!UICONTROL System folder]** tabblad is geselecteerd, hebben alle operatoren toegang tot deze gegevens, ongeacht hun rechten. Als deze optie wordt ontruimd, moet u de exploitant (of hun groep) aan de lijst van toestemmingen uitdrukkelijk toevoegen om hen toegang te hebben.

![](assets/s_ncs_user_folder_properties_security03b.png)

## Mappen en weergaven {#folders-and-views}

### Mappen en weergaven {#about-folders-and-views}

Mappen zijn knooppunten in de Adobe Campaign-structuur. Deze knooppunten worden gemaakt door met de rechtermuisknop op de structuur te klikken via het **[!UICONTROL Add new folder]** menu. Standaard kunt u in het eerste menu de map toevoegen die overeenkomt met de huidige context.

![](assets/s_ncs_user_add_folder_in_tree.png)

U kunt machtigingen voor deze mappen verlenen, net als voor alle andere mappen in de structuur. Zie Toegangsbeheer voor [mappen](#folder-access-management).

Daarnaast kunt u weergaven maken om de toegang tot gegevens te beperken en de inhoud van de structuur aan uw wensen aan te passen. U kunt vervolgens rechten toewijzen aan de weergaven.

Een weergave is een map waarin records worden weergegeven die fysiek zijn opgeslagen in een of meer andere mappen van hetzelfde type. Als u bijvoorbeeld een map Campagne maakt die een weergave is, worden standaard alle campagnes in de database weergegeven, ongeacht de oorsprong ervan. Deze gegevens kunnen vervolgens worden gefilterd.

Wanneer u een map naar een weergave converteert, worden alle gegevens die overeenkomen met het maptype dat in de database aanwezig is, weergegeven in de weergave, ongeacht de map waarin deze is opgeslagen. Vervolgens kunt u het filter filteren om de lijst met weergegeven gegevens te beperken.

>[!CAUTION]
>
>De weergaven bevatten gegevens en bieden toegang tot deze gegevens, maar de gegevens worden niet fysiek opgeslagen in de weergavemap. De exploitant moet de aangewezen rechten voor de gewenste actie in de omslagen van de gegevensbron (lees minstens toegang) hebben.
>
>Als u toegang tot een weergave wilt geven zonder toegang tot de bronmap, geeft u geen leestoegang op het bovenliggende knooppunt van de bronmap.

### Mappen toevoegen en weergaven maken {#adding-folders-and-creating-views}

In het onderstaande voorbeeld maken we nieuwe mappen waarin specifieke gegevens worden weergegeven:

1. Maak een nieuwe **[!UICONTROL Deliveries]** typemap en noem deze map **Deliveries France**.
1. Klik met de rechtermuisknop op deze map en selecteer **[!UICONTROL Properties...]**.

   ![](assets/s_ncs_user_add_folder_exple.png)

1. Selecteer op het **[!UICONTROL Restriction]** tabblad **[!UICONTROL This folder is a view]**. Alle leveringen in het gegevensbestand zullen dan worden getoond.

   ![](assets/s_ncs_user_add_folder_exple01.png)

1. Bepaal de criteria van de leveringsfilter van de vraagredacteur in het middelste gedeelte van het venster: de campagnes die overeenkomen met het gedefinieerde filter worden dan weergegeven.

   >[!NOTE]
   >
   >De vraagredacteur wordt voorgesteld in [deze sectie](../../platform/using/about-queries-in-campaign.md).

   Met de volgende filtervoorwaarden:

![](assets/s_ncs_user_add_folder_exple00.png)

De volgende leveringen worden weergegeven in de weergave:

![](assets/s_ncs_user_add_folder_exple02.png)

