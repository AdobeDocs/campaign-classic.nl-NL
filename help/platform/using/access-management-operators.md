---
product: campaign
title: Aan de slag met campagneoperatoren
description: Meer informatie over het maken en beheren van campagnegebruikers
badge: label="v7" type="Informatief" tooltip="Alleen van toepassing op Campaign Classic v7"
feature: Access Management, Permissions
role: User, Admin
level: Beginner
exl-id: 580282ce-ee30-422a-8724-9c328637cc39
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '1160'
ht-degree: 2%

---

# Operatoren maken en beheren {#operators}



## Aan de slag met campagneoperatoren  {#about-operators}

Een operator is een Adobe Campaign-gebruiker die gemachtigd is om zich aan te melden en handelingen uit te voeren.

Operatoren worden standaard opgeslagen in de **[!UICONTROL Administration > Access management > Operators]** knooppunt.

![](assets/s_ncs_user_list_operators.png)

Operatoren kunnen handmatig worden gemaakt of toegewezen aan een bestaande LDAP-directory.

De volledige procedure voor het maken van een operator wordt beschreven in [deze pagina](#creating-an-operator).

Raadpleeg voor meer informatie over Adobe Campaign- en LDAP-integratie [deze pagina](../../installation/using/connecting-through-ldap.md).

>[!IMPORTANT]
>
>Operatoren moeten zijn gekoppeld aan een beveiligingszone om zich aan te melden bij een instantie. Voor meer informatie over beveiligingszones in Adobe Campaign raadpleegt u [deze pagina](../../installation/using/security-zones.md).

Gebruikers kunnen ook rechtstreeks verbinding maken met Adobe Campaign via hun Adobe ID. Raadpleeg [deze pagina](../../integrations/using/about-adobe-id.md) voor meer informatie.

## Een operator maken {#creating-an-operator}

Voer de volgende stappen uit om een nieuwe operator te maken en machtigingen te verlenen:

1. Klik op de knop **[!UICONTROL New]** boven de lijst met operatoren en voer de details van de nieuwe operator in.

   ![](assets/s_ncs_user_operator_new.png)

1. Geef de **[!UICONTROL Identification parameters]** van de gebruiker: zijn aanmelding, wachtwoord en naam. De aanmeldingsnaam en het wachtwoord worden door de operator gebruikt om u aan te melden bij Adobe Campaign. Nadat de gebruiker is aangemeld, kan hij of zij hun wachtwoord wijzigen via het dialoogvenster **[!UICONTROL Tools > Change password]** -menu. Het e-mailadres van de exploitant is essentieel omdat het de exploitant in staat stelt meldingen te ontvangen, bijvoorbeeld bij de verwerking van goedkeuringen.

   In deze sectie kunt u ook een operator koppelen aan een organisatie-entiteit. Raadpleeg voor meer informatie de [deze pagina](../../distributed/using/about-distributed-marketing.md).

1. Selecteer de machtigingen die aan de operator zijn verleend in het dialoogvenster **[!UICONTROL Operator access rights]** sectie.

   Als u rechten aan de operator wilt toewijzen, klikt u op de knop **[!UICONTROL Add]** boven de lijst met rechten en selecteer vervolgens een groep operatoren in de lijst met beschikbare groepen:

   ![](assets/s_ncs_user_permissions_operators.png)

   U kunt ook een of meer benoemde rechten selecteren (zie [Benoemde rechten](#named-rights)). Klik hiertoe op de pijl rechts van de knop **[!UICONTROL Folder]** en selecteer **[!UICONTROL Named rights]**:

   ![](assets/s_ncs_user_rights_operators.png)

   Selecteer groepen en/of benoemde rechten die u wilt toewijzen en klik op **[!UICONTROL OK]** om te valideren.

1. Klikken **[!UICONTROL Ok]** om de operator te maken: het profiel wordt toegevoegd aan de lijst met bestaande operatoren.

   ![](assets/operator_profile_new.png)

>[!NOTE]
>
>U kunt de operatoren naar wens ordenen door nieuwe operatormappen te maken. Klik hiertoe met de rechtermuisknop op de operatormap en selecteer **[!UICONTROL Add an 'Operators' folder]**.

Nadat het profiel van de operator is gemaakt, kunt u de gegevens ervan toevoegen of bijwerken. Om dit te doen, klik **[!UICONTROL Edit]** tab.

![](assets/operator_edit_profile.png)

>[!NOTE]
>
>De **[!UICONTROL Session timeout]** kunt u de vertraging vóór de FDA sessieonderbreking aanpassen. Raadpleeg voor meer informatie hierover [Over Federale gegevenstoegang](../../installation/using/about-fda.md).

## De tijdzone van de operator definiëren {#time-zone-of-the-operator}

In de **[!UICONTROL General]** kunt u de tijdzone van de operator selecteren. Operatoren werken standaard in de tijdzone van de server. Het is echter mogelijk een andere tijdzone te selecteren met de vervolgkeuzelijst.

De configuratie van tijdzones wordt beschreven in [deze pagina](../../installation/using/time-zone-management.md).

>[!NOTE]
>
>Voor samenwerkingsverbanden binnen verschillende tijdzones moeten datums in UTC worden opgeslagen. Datums worden in de juiste tijdzone geconverteerd in de volgende context: wanneer een datum in de gebruikerstijdzone wordt getoond, wanneer de dossiers worden ingevoerd en uitgevoerd, wanneer een e-maillevering gepland is, wanneer de activiteiten in een werkschema (planner, wacht, tijdbeperking, enz.) worden gepland
>
>Restricties en aanbevelingen in verband met deze contexten worden weergegeven in verwante secties van de documentatie van Adobe Campaign.

Bovendien **[!UICONTROL Regional settings]** in de vervolgkeuzelijst kunt u de notatie selecteren voor het weergeven van datums en getallen.

## Machtigingen toevoegen {#access-rights-options}

Gebruik de **[!UICONTROL Access rights]** om de groepen en benoemde rechten die aan de operator zijn gekoppeld, bij te werken.

![](assets/operator_profile_security_options.png)

De **[!UICONTROL Edit the access parameters...]** Via de koppeling hebt u toegang tot de volgende opties:

* De **[!UICONTROL Disable account]** Met deze optie kunt u de account van de operator uitschakelen: deze gebruiker heeft geen toegang meer tot Adobe Campaign.

   >[!NOTE]
   >
   >Zelfs als hun account is uitgeschakeld, kan de operator nog steeds waarschuwingen of meldingen ontvangen vanuit Campagne. Adobe raadt u aan het e-mailadres uit hun profiel te verwijderen om te stoppen met het verzenden van campagnemeldingen naar deze operator.

* De **[!UICONTROL Forbid access from the rich client]** kunt u het gebruik van Adobe Campaign beperken tot [Webtoegang](../../platform/using/adobe-campaign-workspace.md#console-and-web-access) of via API&#39;s: toegang tot de Adobe Campaign-clientconsole is niet meer beschikbaar.
* Het is mogelijk om een veiligheidszone aan de exploitant te verbinden. Raadpleeg [deze pagina](../../installation/using/security-zones.md) voor meer informatie.
* U kunt een vertrouwd IP masker ook bepalen gebruikend de aangewezen verbinding.

   De operator kan verbinding maken met Adobe Campaign zonder het wachtwoord in te voeren als het IP-adres in deze lijst staat.

   U kunt ook een set IP-adressen opgeven die zonder wachtwoord verbinding mogen maken, zoals in het volgende voorbeeld:

   ![](assets/operator_trustip.png)

   >[!NOTE]
   >
   >Om toegang tot uw platform veilig te houden, moet deze optie met zorg worden gebruikt.

* De **[!UICONTROL Restrict to information found in sub-folders of:]** Hiermee kunt u de rechten beperken die aan de operator van een map worden toegewezen. Alleen de submappen van het knooppunt dat in deze optie is opgegeven, zijn zichtbaar voor de gebruiker:

   ![](assets/s_ncs_user_restrictions_operators.png)

   >[!IMPORTANT]
   >
   >Dit is een zeer strenge beperking en het moet met voorzichtigheid worden gebruikt. Een exploitant die met dit type van rechten het programma wordt geopend kan slechts de inhoud van de gespecificeerde omslag zien, en heeft geen toegang tot een andere knoop van de boom via de ontdekkingsreiziger. Afhankelijk van de functies waartoe deze operator toegang heeft (bijvoorbeeld: (workflows), kan de gebruiker gegevens weergeven die doorgaans zijn opgeslagen in knooppunten die niet toegankelijk zijn.

### Instellingen controleren {#check-settings}

De **[!UICONTROL Audit]** kunt u informatie met betrekking tot de operator weergeven. De verschillende tabbladen worden automatisch toegevoegd op basis van de instellingen die zijn gedefinieerd in het interventiegebied van de operator.

U hebt toegang tot:

* De lijst met rechten voor mappen die aan de operator zijn gekoppeld.

   ![](assets/operator_folder_permissions.png)

   >[!NOTE]
   >
   >Raadpleeg voor meer informatie hierover [Toegangsbeheer voor mappen](#folder-access-management).

* Het erkenningslogboek van de exploitant.

   ![](assets/operator_profile_validations.png)

* De lijst met discussieforums waarop ze zich hebben geabonneerd.
* Gebeurtenissen in hun kalender.
* De lijst met taken die aan hen zijn toegewezen.

## Standaardoperatoren {#default-operators}

Adobe Campaign gebruikt technische operatoren met profielen die standaard zijn geconfigureerd: Beheerder (&#39;admin&#39;), Facturering (&#39;facturering&#39;), Controle, Web application agent (&#39;webapp&#39;), enz. Sommige hiervan zijn afhankelijk van de toepassingen en opties die op het platform zijn geïnstalleerd: De &quot;centrale&quot;en &quot;lokale&quot;exploitanten, bijvoorbeeld, zijn slechts zichtbaar als de Verdeelde optie van de Marketing wordt geïnstalleerd.

>[!IMPORTANT]
>
>Deze technische operatoren worden standaard op de hoogte gesteld wanneer het platform informatieberichten retourneert. We raden u ten zeerste aan een contactbericht voor hen te verzenden.
>
>Om ervoor te zorgen dat webtoepassingen correct werken, raden we u ook aan geen specifieke regionale instellingen voor de operator &#39;webapp&#39; te definiëren.

De technische operator &#39;webapp&#39; heeft standaard het benoemde BEHEERRECHT, wat tot beveiligingsrisico&#39;s kan leiden. We raden u aan dit recht te verwijderen om dit probleem op te lossen. Dit doet u als volgt:

1. Van de **[!UICONTROL Administration > Access management > Named rights]** knooppunt, klikken **[!UICONTROL New]** om een recht te creëren en het WEBAPP te noemen.

   ![](assets/s_ncs_default_operators_webapp_right.png)

   Benoemde rechten worden nader beschreven in het dialoogvenster [Benoemde rechten](#named-rights) sectie.

1. Van de **[!UICONTROL Administration > Access management > Operators]** -knooppunt, selecteert u de webapplicatieagent (&#39;webapp&#39;).

   Selecteer **[!UICONTROL Edit]** en vervolgens de **[!UICONTROL Access rights]** en verwijder de rechts genoemde BEHEER uit de lijst.

   ![](assets/s_ncs_default_operators_webapp_admin_right.png)

   Klikken **[!UICONTROL Add]** en selecteer het WEBAPP-recht dat u net hebt gemaakt, en sla uw wijzigingen op.

   ![](assets/s_ncs_default_operators_webapp_webapp_right.png)

1. Wijs de operator &#39;webapp&#39; toegangsrechten toe voor het lezen en schrijven van gegevens voor de mappen die betrekking hebben op deze operator, in de eerste plaats de mappen &#39;Ontvanger&#39;.

   ![](assets/s_ncs_default_operators_webapp_folder_access.png)

   De rechten voor het wijzigen van boommappen worden beschreven in het gedeelte [Toegangsbeheer voor mappen](#folder-access-management) sectie.

>[!NOTE]
>
>Voor meer informatie over de richtlijnen van de Veiligheid, verwijs naar [Controlelijst voor Adobe Campaign-beveiligingsconfiguratie](https://helpx.adobe.com/nl/campaign/kb/acc-security.html).
