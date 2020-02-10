---
title: Verbinding maken via LDAP
seo-title: Verbinding maken via LDAP
description: Verbinding maken via LDAP
seo-description: null
page-status-flag: never-activated
uuid: 13a426bc-7c34-49e5-ac8e-26d830845f28
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: additional-configurations
discoiquuid: 1563db7c-ccb6-46b3-9299-67ec0aedaca0
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 209ac4d81d2d27c264ee6b288bcb7fcb1900ffc5

---


# Verbinding maken via LDAP{#connecting-through-ldap}

## Campagne en LDAP configureren {#configuring-campaign-and-ldap}

>[!NOTE]
>
>De LDAP-configuratie is alleen mogelijk voor installaties op locatie of voor hybride installaties.

De LDAP-configuratie wordt uitgevoerd in de implementatietovenaar. De **[!UICONTROL LDAP integration]** optie moet tijdens de eerste configuratiestatus worden geselecteerd. Raadpleeg de wizard [Implementatie](../../installation/using/deploying-an-instance.md#deployment-wizard).

In het venster kunt u de identificatie van gebruikers van Adobe Campagne configureren via de opgegeven LDAP-directory.

![](assets/s_ncs_install_deployment_wiz_ldap_01.png)

* Geef het adres van de LDAP-server op in het **[!UICONTROL LDAP server]** veld. U kunt het poortnummer toevoegen. Standaard is de gebruikte poort 389.
* Selecteer in de vervolgkeuzelijst de verificatiemethode voor gebruikers:

   * Gecodeerd wachtwoord (**md5**)

      Standaardmodus.

   * Wachtwoord voor normale tekst + SSL (**TLS**)

      De volledige verificatieprocedure (inclusief wachtwoord) wordt gecodeerd. De veilige haven 636 moet niet op deze wijze worden gebruikt: Adobe Campagne schakelt automatisch over naar de beveiligde modus.

      Wanneer u deze verificatiemodus in Linux gebruikt, wordt het certificaat geverifieerd door een openLDAP-clientbibliotheek. Wij adviseren gebruikend een geldig SSL certificaat zodat de authentificatieprocedure wordt gecodeerd. Anders is de informatie onbewerkte tekst.

      Het certificaat wordt ook geverifieerd in Windows.

   * Windows NT LAN Manager (**NTLM**)

      Eigen Windows-verificatie. De naam **[!UICONTROL Unique identifier]** wordt alleen voor de domeinnaam gebruikt.

   * Distributed Password Authentication (**DPA**)

      Eigen Windows-verificatie. De naam **[!UICONTROL Unique identifier]** wordt alleen gebruikt voor de domeinnaam (domain.com).

   * Wachtwoord voor normale tekst

      Geen versleuteling (alleen voor gebruik in testfasen).

* Selecteer de modus voor gebruikersverificatie: **[!UICONTROL Automatically compute the unique user identifier]** (zie stap [Distinguished Name calculation](#distinguished-name-calculation)) of **[!UICONTROL Search the unique user identifier in the directory]** (zie stap [Zoeken naar id&#39;s](#searching-for-identifiers)).

## Compatibiliteit {#compatibility}

Welke systemen compatibel zijn, is afhankelijk van het geselecteerde verificatiemechanisme. Hieronder volgt een compatibiliteitsmatrix van besturingssystemen en LDAP-servers.

<table> 
 <thead> 
  <tr> 
   <th> </th> 
   <th> OpenLDAP<br /> </th> 
   <th> Active Directory<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> md5<br /> </td> 
   <td> Windows, Linux<br /> </td> 
   <td> Linux<br /> </td> 
  </tr> 
  <tr> 
   <td> TLS<br /> </td> 
   <td> Linux<br /> </td> 
   <td> Windows, Linux<br /> </td> 
  </tr> 
  <tr> 
   <td> NTLM en DPA<br /> </td> 
   <td> </td> 
   <td> Windows<br /> </td> 
  </tr> 
  <tr> 
   <td> normale tekst<br /> </td> 
   <td> Windows, Linux<br /> </td> 
   <td> Windows, Linux<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Berekening van Distinguished Name {#distinguished-name-calculation}

Als u wenst om de Distinguished Name (DN) herkenningstekens gegevens te verwerken, laat de volgende stap van de plaatsingstovenaar u de berekeningswijze vormen.

![](assets/s_ncs_install_deployment_wiz_ldap_02.png)

* Geef de unieke id van de gebruiker in de map (Distinguished Name - DN) op in het **[!UICONTROL Distinguished Name]** veld.

   **[!UICONTROL (login)]** wordt vervangen door de id van de Adobe Campaign-operator.

   >[!CAUTION]
   >
   >De **[!UICONTROL dc]** instelling moet in kleine letters zijn.

* Selecteer de optie **[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]** om de groep- en gebruikerskoppelingen in de LDAP-directory en de groep- en gebruikerskoppelingen in Adobe Campagne te synchroniseren.

   Als u deze optie selecteert, worden de opties **[!UICONTROL Application level DN used for the search]** en **[!UICONTROL Password of the application login]** ingeschakeld.

   Als u deze twee velden invult, maakt Adobe Campaign verbinding met de LDAP-server met een eigen aanmelding en wachtwoord. Als deze leeg zijn, maakt Adobe Campaign anoniem verbinding met de server.

## Zoeken naar id&#39;s {#searching-for-identifiers}

Als u verkiest om naar een herkenningsteken te zoeken, laat de plaatsingstovenaar u het onderzoek vormen.

* Geef in de velden **[!UICONTROL Application level DN used for the search]** en **[!UICONTROL Password of the application login]** velden de id en het wachtwoord op waarmee Adobe Campaign verbinding maakt om de id te zoeken. Als deze leeg zijn, maakt Adobe Campaign anoniem verbinding met de server.
* Geef de velden **[!UICONTROL Base identifier]** en **[!UICONTROL Search scope]** velden op om te bepalen uit welke subset van de LDAP-directory de zoekopdracht moet beginnen.

   Selecteer de gewenste modus in de vervolgkeuzelijst:

   ![](assets/s_ncs_install_deployment_wiz_ldap_03.png)

   1. **[!UICONTROL Recursive (default mode)]**.

      De LDAP-directory wordt volledig doorzocht, vanaf een bepaald niveau.

   1. **[!UICONTROL Limited to the base]**.

      Alle kenmerken worden opgenomen in de zoekopdracht.

   1. **[!UICONTROL Limited to the first sub-level of the base]**.

      De zoekopdracht wordt uitgevoerd op alle kenmerken van de map en begint op het eerste niveau van het kenmerk.

* In het **[!UICONTROL Filter]** veld kunt u een element opgeven om het bereik van de zoekopdracht te verfijnen.

## LDAP-machtigingen configureren {#configuring-ldap-authorizations}

Dit venster wordt weergegeven wanneer u de **[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]** optie selecteert.

![](assets/s_ncs_install_deployment_wiz_ldap_04.png)

U moet verschillende parameters opgeven om de groep of groepen te vinden waartoe de gebruiker behoort en de bijbehorende rechten, te weten:

* het **[!UICONTROL Database identifier]** veld,
* het **[!UICONTROL Search scope]** veld,

   >[!NOTE]
   >
   >Als u naar de DN hebt gezocht, kunt u selecteren **[!UICONTROL Reuse the DN search parameters]** om de geselecteerde waarden voor DN en onderzoekswerkingsgebied van het vorige scherm over te nemen.

* het **[!UICONTROL Rights search filter]** veld, gebaseerd op de aanmelding en de volledige naam van de gebruiker;
* het **[!UICONTROL Attribute containing the group or authorization name]** veld betreffende de gebruiker,
* het **[!UICONTROL Association mask]** veld waarin de groepsnaam kan worden opgehaald in Adobe Campaign en de bijbehorende rechten. U kunt reguliere expressies gebruiken om naar de naam te zoeken.
* Selecteer deze optie **[!UICONTROL Enable the connection of users declared in the LDAP directory if the operator is not declared in Adobe Campaign]** zodat de gebruiker automatisch toegangsrechten krijgt bij verbinding.

Klik **[!UICONTROL Save]** om het configureren van de instantie te voltooien.

## Operatoren beheren {#managing-operators}

Nadat u de configuratie hebt bevestigd, moet u definiëren welke Adobe Campagneoperatoren worden beheerd via de LDAP-directory.

Als u de LDAP-directory wilt gebruiken om een operator te verifiëren, bewerkt u het bijbehorende profiel en klikt u op de **[!UICONTROL Edit the access parameters]** koppeling. Selecteer de **[!UICONTROL Use LDAP for authentication]** optie: Het **[!UICONTROL Password]** veld wordt grijs weergegeven voor deze operator.

![](assets/s_ncs_install_operator_in_ldap.png)

## Gebruik hoofdletters {#use-cases}

Deze sectie biedt een aantal eenvoudige gebruiksgevallen om u te helpen de meest geschikte configuraties te bereiken op basis van uw behoeften.

1. Er is een gebruiker gemaakt in de LDAP-directory, maar niet in Adobe Campaign.

   Adobe-campagne kan zo worden geconfigureerd dat de gebruiker het platform opent via de LDAP-verificatie. Adobe Campagne moet de geldigheid van de combinatie identiteitskaart/wachtwoord in de folder kunnen controleren LDAP, zodat de exploitant in de Campagne van Adobe kan worden gecreeerd. Schakel de **[!UICONTROL Enable the connection of users declared in the LDAP directory if the operator is not declared in Adobe Campaign]** optie in om dit te doen. In dit geval, moet de groepssynchronisatie ook worden gevormd: de **[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]** optie moet worden geselecteerd .

1. De gebruiker is gemaakt in Adobe Campaign, maar niet in de LDAP-directory.

   Ze kunnen zich niet aanmelden bij Adobe Campaign.

1. De LDAP-directory bevat een groep die niet bestaat in Adobe Campagne.

   Deze groep wordt niet gemaakt in Adobe Campaign. U moet de groep maken en de groepen synchroniseren om een match-up via de **[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]** optie in te schakelen.

1. De groepen bestaan in de Campagne van Adobe en de folder LDAP wordt geactiveerd na de gebeurtenis: gebruikersgroepen in Adobe Campaign worden niet automatisch vervangen door de inhoud van LDAP-groepen. Op dezelfde manier geldt dat als er alleen een groep bestaat in Adobe Campaign, er geen LDAP-gebruikers aan kunnen worden toegevoegd totdat de groep is gemaakt en gesynchroniseerd in LDAP.

   Groepen worden nooit direct gemaakt, noch via Adobe Campaign, noch via LDAP. Ze moeten afzonderlijk worden gemaakt, zowel in Adobe Campaign als in de LDAP-directory.

   De namen van groepen in de LDAP-directory moeten overeenkomen met de namen van groepen in de Adobe-campagne. Hun verenigingsmasker wordt bepaald in het laatste configuratiestadium van de plaatsingstovenaar: Adobe Campagne_(.*), bijvoorbeeld.

