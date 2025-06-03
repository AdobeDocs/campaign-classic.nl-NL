---
product: campaign
title: Aan de slag met campagneoperatoren
description: Meer informatie over het maken en beheren van campagnegebruikers
badge: label="v7" type="Informative" tooltip="Alleen van toepassing op Campaign Classic v7"
feature: Access Management, Permissions
role: User, Admin
level: Beginner
exl-id: 580282ce-ee30-422a-8724-9c328637cc39
source-git-commit: 42cec0e9bede94a2995a5ad442822512bda14f2b
workflow-type: tm+mt
source-wordcount: '1259'
ht-degree: 2%

---

# Operatoren maken en beheren {#operators}

>[!CAUTION]
>
>* Beginnend Campaign Classic v7.3.1, zouden alle exploitanten [ Adobe Identity Management Systeem (IMS) ](https://helpx.adobe.com/nl/enterprise/using/identity.html){target="_blank"} moeten gebruiken om met Campagne te verbinden.
>  &#x200B;>Als onderdeel van de inspanningen om het beveiligings- en verificatieproces te versterken, raadt Adobe Campaign ten zeerste aan om alle bestaande verificatiemodus voor operatoren te migreren van de native verificatie van aanmelding/wachtwoord naar Adobe Identity Management System (IMS). Leer hoe te om uw exploitanten in [ te migreren deze pagina ](../../technotes/using/migrate-users-to-ims.md).
> 
>* Na deze migratie is de volgende sectie niet meer van toepassing.  Leer hoe te opstellingstoestemmingen met Adobe IMS in [ Campagne v8 documentatie ](https://experienceleague.adobe.com/docs/campaign/campaign-v8/admin/permissions/gs-permissions.html?lang=nl-NL){target="_blank"}.


## Aan de slag met campagneoperatoren {#about-operators}

>[!NOTE]
>
>Deze procedures zijn alleen van toepassing op operatoren die verbinding maken met een campagne met native verificatie. Voor de authentificatie van Adobe IMS, verwijs naar [ deze documentatie ](https://helpx.adobe.com/nl/enterprise/using/manage-users-individually.html#_blank).

Een operator is een Adobe Campaign-gebruiker die gemachtigd is om zich aan te melden en handelingen uit te voeren.

Operatoren worden standaard opgeslagen in het knooppunt **[!UICONTROL Administration > Access management > Operators]** .

![](assets/s_ncs_user_list_operators.png)

Operatoren kunnen handmatig worden gemaakt of toegewezen aan een bestaande LDAP-directory.

De volledige procedure om een exploitant tot stand te brengen wordt beschreven in [ deze pagina ](#creating-an-operator).

Voor meer op de integratie van Adobe Campaign en LDAP, verwijs naar [ deze pagina ](../../installation/using/connecting-through-ldap.md).

>[!IMPORTANT]
>
>Operatoren moeten zijn gekoppeld aan een beveiligingszone om zich aan te melden bij een instantie. Voor meer op veiligheidsstreken in Adobe Campaign, verwijs naar [ deze pagina ](../../installation/using/security-zones.md).

Gebruikers kunnen ook rechtstreeks verbinding maken met Adobe Campaign via hun Adobe ID. Raadpleeg [deze pagina](../../integrations/using/about-adobe-id.md) voor meer informatie.

## Een operator maken {#creating-an-operator}

Voer de volgende stappen uit om een nieuwe operator te maken en machtigingen te verlenen:

1. Klik op de knop **[!UICONTROL New]** boven de lijst met operatoren en voer de details van de nieuwe operator in.

   ![](assets/s_ncs_user_operator_new.png)

1. Geef de **[!UICONTROL Identification parameters]** van de gebruiker op: de aanmeldingsnaam, het wachtwoord en de naam. De aanmeldingsnaam en het wachtwoord worden door de operator gebruikt om u aan te melden bij Adobe Campaign. Zodra de gebruiker is aangemeld, kunnen deze zijn of haar wachtwoord wijzigen via het menu **[!UICONTROL Tools > Change password]** . Het e-mailadres van de exploitant is essentieel omdat het de exploitant in staat stelt meldingen te ontvangen, bijvoorbeeld bij de verwerking van goedkeuringen.

   In deze sectie kunt u ook een operator koppelen aan een organisatie-entiteit. Voor meer op dit, verwijs naar [ deze pagina ](../../distributed/using/about-distributed-marketing.md).

1. Selecteer in de sectie **[!UICONTROL Operator access rights]** de machtigingen die aan de operator zijn verleend.

   Als u rechten wilt toewijzen aan de operator, klikt u op de knop **[!UICONTROL Add]** boven de lijst met rechten en selecteert u een groep operatoren in de lijst met beschikbare groepen:

   ![](assets/s_ncs_user_permissions_operators.png)

   U kunt één of meerdere genoemde rechten ook selecteren (verwijs naar [ Genoemde rechten ](#named-rights)). Klik hiertoe op de pijl rechts van het veld **[!UICONTROL Folder]** en selecteer **[!UICONTROL Named rights]** :

   ![](assets/s_ncs_user_rights_operators.png)

   Selecteer groepen en/of benoemde rechten die u wilt toewijzen en klik op **[!UICONTROL OK]** om te valideren.

1. Klik op **[!UICONTROL Ok]** om de operator te maken: het profiel wordt toegevoegd aan de lijst met bestaande operatoren.

   ![](assets/operator_profile_new.png)

>[!NOTE]
>
>U kunt de operatoren naar wens ordenen door nieuwe operatormappen te maken. Klik hiertoe met de rechtermuisknop op de operatormap en selecteer **[!UICONTROL Add an 'Operators' folder]** .

Nadat het profiel van de operator is gemaakt, kunt u de gegevens ervan toevoegen of bijwerken. Klik hiertoe op de tab **[!UICONTROL Edit]** .

![](assets/operator_edit_profile.png)

>[!NOTE]
>
>In het veld **[!UICONTROL Session timeout]** kunt u de vertraging vóór de FDA-sessietime-out aanpassen. Voor meer op dit, verwijs naar [ Ongeveer Verdeelde Toegang van Gegevens ](../../installation/using/about-fda.md).

## De tijdzone van de operator definiëren {#time-zone-of-the-operator}

Op het tabblad **[!UICONTROL General]** kunt u de tijdzone van de operator selecteren. Operatoren werken standaard in de tijdzone van de server. Het is echter mogelijk een andere tijdzone te selecteren met de vervolgkeuzelijst.

De configuratie van tijdstreken wordt beschreven in [ deze pagina ](../../installation/using/time-zone-management.md).

>[!NOTE]
>
>Voor samenwerkingsverbanden binnen verschillende tijdzones moeten datums in UTC worden opgeslagen. Datums worden in de juiste tijdzone in de volgende context omgezet: wanneer een datum wordt weergegeven in de tijdzone van de gebruiker, wanneer bestanden worden geïmporteerd en geëxporteerd, wanneer een e-maillevering gepland is, wanneer activiteiten in een workflow zijn gepland (planner, wait, tijdbeperking, enz.)
>
>Restricties en aanbevelingen in verband met deze contexten worden weergegeven in verwante secties van de documentatie van Adobe Campaign.

Daarnaast kunt u in de vervolgkeuzelijst **[!UICONTROL Regional settings]** de notatie selecteren voor het weergeven van datums en getallen.

## Machtigingen toevoegen {#access-rights-options}

Gebruik het tabblad **[!UICONTROL Access rights]** om de groepen en benoemde rechten bij te werken die aan de operator zijn gekoppeld.

![](assets/operator_profile_security_options.png)

Met de koppeling **[!UICONTROL Edit the access parameters...]** hebt u toegang tot de volgende opties:

* Met de optie **[!UICONTROL Disable account]** kunt u het account van de operator uitschakelen: deze gebruiker heeft geen toegang meer tot Adobe Campaign.

  >[!NOTE]
  >
  >Zelfs als hun account is uitgeschakeld, kan de operator nog steeds waarschuwingen of meldingen ontvangen vanuit Campagne. Adobe raadt u aan het e-mailadres uit hun profiel te verwijderen om te stoppen met het verzenden van campagnemeldingen naar deze operator.

* De **[!UICONTROL Forbid access from the rich client]** optie laat u het gebruik van Adobe Campaign tot [ toegang van het Web ](../../platform/using/adobe-campaign-workspace.md#console-and-web-access) of door APIs beperken: de toegang tot de de cliëntconsole van Adobe Campaign is niet meer beschikbaar.
* Het is mogelijk om een veiligheidszone aan de exploitant te verbinden. Raadpleeg [deze pagina](../../installation/using/security-zones.md) voor meer informatie.
* U kunt een vertrouwd IP masker ook bepalen gebruikend de aangewezen verbinding.

  De operator kan verbinding maken met Adobe Campaign zonder het wachtwoord in te voeren als het IP-adres in deze lijst staat.

  U kunt ook een set IP-adressen opgeven die zonder wachtwoord verbinding mogen maken, zoals in het volgende voorbeeld:

  ![](assets/operator_trustip.png)

  >[!NOTE]
  >
  >Om toegang tot uw platform veilig te houden, moet deze optie met zorg worden gebruikt.

* Met de optie **[!UICONTROL Restrict to information found in sub-folders of:]** kunt u de rechten beperken die aan de operator van een map worden toegewezen. Alleen de submappen van het knooppunt dat in deze optie is opgegeven, zijn zichtbaar voor de gebruiker:

  ![](assets/s_ncs_user_restrictions_operators.png)

  >[!IMPORTANT]
  >
  >Dit is een zeer strenge beperking en het moet met voorzichtigheid worden gebruikt. Een exploitant die met dit type van rechten het programma wordt geopend kan slechts de inhoud van de gespecificeerde omslag zien, en heeft geen toegang tot een andere knoop van de boom via de ontdekkingsreiziger. Afhankelijk van de functies waartoe deze operator toegang heeft (bijvoorbeeld workflows), kan de gebruiker echter gegevens weergeven die gewoonlijk zijn opgeslagen in knooppunten die niet toegankelijk zijn.

### Instellingen controleren {#check-settings}

Op het tabblad **[!UICONTROL Audit]** kunt u informatie weergeven die betrekking heeft op de operator. De verschillende tabbladen worden automatisch toegevoegd op basis van de instellingen die zijn gedefinieerd in het interventiegebied van de operator.

U hebt toegang tot:

* De lijst met rechten voor mappen die aan de operator zijn gekoppeld.

  ![](assets/operator_folder_permissions.png)

  >[!NOTE]
  >
  >Voor meer op dit, verwijs naar [ het toegangsbeheer van de Omslag ](#folder-access-management).

* Het erkenningslogboek van de exploitant.

  ![](assets/operator_profile_validations.png)

* De lijst met discussieforums waarop ze zich hebben geabonneerd.
* Gebeurtenissen in hun kalender.
* De lijst met taken die aan hen zijn toegewezen.

## Standaardoperatoren {#default-operators}

Adobe Campaign gebruikt technische operatoren met profielen die standaard zijn geconfigureerd: beheerder (&#39;admin&#39;), facturering (&#39;facturering&#39;), monitoring, webtoepassingsagent (&#39;webapp&#39;), enz. Sommige hiervan zijn afhankelijk van de toepassingen en opties die op het platform zijn geïnstalleerd: &#39;centrale&#39; en &#39;lokale&#39; operatoren zijn bijvoorbeeld alleen zichtbaar als de optie Distributed Marketing is geïnstalleerd.

>[!IMPORTANT]
>
>Deze technische operatoren worden standaard op de hoogte gesteld wanneer het platform informatieberichten retourneert. We raden u ten zeerste aan een contactbericht voor hen te verzenden.
>
>Om ervoor te zorgen dat webtoepassingen correct werken, raden we u ook aan geen specifieke regionale instellingen voor de operator &#39;webapp&#39; te definiëren.

De technische operator &#39;webapp&#39; heeft standaard het benoemde BEHEERRECHT, wat tot beveiligingsrisico&#39;s kan leiden. We raden u aan dit recht te verwijderen om dit probleem op te lossen. Dit doet u als volgt:

1. Klik in het knooppunt **[!UICONTROL Administration > Access management > Named rights]** op **[!UICONTROL New]** om een rechts-item te maken en dit WEBAPP te noemen.

   ![](assets/s_ncs_default_operators_webapp_right.png)

   De genoemde rechten worden gedetailleerd in de [ Benoemde rechten ](#named-rights) sectie.

1. Selecteer in het knooppunt **[!UICONTROL Administration > Access management > Operators]** de webapplicatieagent (&#39;webapp&#39;).

   Selecteer de tab **[!UICONTROL Edit]** , vervolgens de tab **[!UICONTROL Access rights]** en verwijder de benoemde ADMINISTRATIE rechts uit de lijst.

   ![](assets/s_ncs_default_operators_webapp_admin_right.png)

   Klik op **[!UICONTROL Add]** en selecteer het WEBAPP-recht dat u net hebt gemaakt. Sla vervolgens uw wijzigingen op.

   ![](assets/s_ncs_default_operators_webapp_webapp_right.png)

1. Wijs de operator &#39;webapp&#39; toegangsrechten toe voor het lezen en schrijven van gegevens voor de mappen die betrekking hebben op deze operator, in de eerste plaats de mappen &#39;Ontvanger&#39;.

   ![](assets/s_ncs_default_operators_webapp_folder_access.png)

   Het wijzigen van rechten op boomomslagen is gedetailleerd in de [ sectie van het de toegangsbeheer van de Omslag ](#folder-access-management).

>[!NOTE]
>
>Voor meer informatie over de richtlijnen van de Veiligheid, verwijs naar [ checklist van de Configuratie van de Veiligheid van Adobe Campaign ](https://helpx.adobe.com/nl/campaign/kb/acc-security.html).