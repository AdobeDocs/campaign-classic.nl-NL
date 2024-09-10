---
product: campaign
title: Verbinding maken via LDAP
description: Leer hoe u zich bij de campagne aanmeldt met LDAP
feature: Installation, Instance Settings
badge-v7-prem: label="Alleen op locatie/hybride" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=nl" tooltip="Alleen van toepassing op on-premise en hybride implementaties"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 0533cd50-3aa4-4160-9152-e916e149e77f
source-git-commit: 0fba6a2ad4ffa864e2f726f241aa9d7cd39072a6
workflow-type: tm+mt
source-wordcount: '1045'
ht-degree: 0%

---

# Verbinding maken via LDAP {#connecting-through-ldap}

## Campagne en LDAP configureren {#configuring-campaign-and-ldap}

>[!NOTE]
>
>* De LDAP-configuratie is alleen mogelijk voor installaties op locatie of voor hybride installaties.
>
>* Zorg ervoor dat uw systeem en uw open versies met Campagne in de [ matrijs van de Verenigbaarheid ](../../rn/using/compatibility-matrix.md) compatibel zijn. Verouderde versies kunnen invloed hebben op uw LDAP-verificatie.
>

De LDAP-configuratie wordt uitgevoerd in de implementatietovenaar. De optie **[!UICONTROL LDAP integration]** moet tijdens de eerste configuratiestatus worden geselecteerd. Verwijs naar [ plaatsingstovenaar ](../../installation/using/deploying-an-instance.md#deployment-assistant).

In het venster kunt u de identificatie van Adobe Campaign-gebruikers configureren via de opgegeven LDAP-directory.

![](assets/s_ncs_install_deployment_wiz_ldap_01.png)

* Geef het adres van de LDAP-server op in het veld **[!UICONTROL LDAP server]** . U kunt het poortnummer toevoegen. Standaard wordt 389 gebruikt.
* Selecteer in de vervolgkeuzelijst de verificatiemethode voor gebruikers:

   * Gecodeerd wachtwoord (**md5**) - Standaardwijze.

   * Ononderbroken tekstwachtwoord + SSL (**TLS**) - de volledige authentificatieprocedure (inbegrepen wachtwoord) wordt gecodeerd. Beveiligde poort 636 mag niet worden gebruikt in deze modus: Adobe Campaign schakelt automatisch over naar de beveiligde modus.

     Wanneer u deze verificatiemodus in Linux gebruikt, wordt het certificaat geverifieerd door een openLDAP-clientbibliotheek. Wij adviseren gebruikend een geldig SSL certificaat zodat de authentificatieprocedure wordt gecodeerd. Anders wordt de informatie in onbewerkte tekst weergegeven.

     Het certificaat wordt ook geverifieerd in Windows.

   * De LAN Manager van NT van vensters (**NTLM**) - de Eigen authentificatie van Vensters. **[!UICONTROL Unique identifier]** wordt alleen voor de domeinnaam gebruikt.

   * De verdeelde Authentificatie van het Wachtwoord (**DPA**) - de merkgebonden authentificatie van Vensters. **[!UICONTROL Unique identifier]** wordt alleen gebruikt voor de domeinnaam (domain.com).

   * Wachtwoord voor normale tekst - Geen versleuteling (alleen voor gebruik in testfasen).

* Selecteer de wijze van de gebruikersauthentificatie: **[!UICONTROL Automatically compute the unique user identifier]** (zie stap [ Distinguished Name berekening ](#distinguished-name-calculation)) of **[!UICONTROL Search the unique user identifier in the directory]** (zie stap [ die naar herkenningstekens ](#searching-for-identifiers) zoekt).

## Compatibiliteit {#compatibility}

Welke systemen compatibel zijn, is afhankelijk van het geselecteerde verificatiemechanisme. Hieronder volgt een compatibiliteitsmatrix van besturingssystemen en LDAP-servers.

<table> 
 <thead> 
  <tr> 
   <th> </th> 
   <th> OpenLDAP <br /> </th> 
   <th> Actieve map <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> md5<br /> </td> 
   <td> Windows, Linux <br /> </td> 
   <td> Linux<br /> </td> 
  </tr> 
  <tr> 
   <td> TLS<br /> </td> 
   <td> Linux<br /> </td> 
   <td> Windows, Linux <br /> </td> 
  </tr> 
  <tr> 
   <td> NTLM &amp; DPA <br /> </td> 
   <td> </td> 
   <td> Windows<br /> </td> 
  </tr> 
  <tr> 
   <td> onbewerkte tekst <br /> </td> 
   <td> Windows, Linux <br /> </td> 
   <td> Windows, Linux <br /> </td> 
  </tr> 
 </tbody> 
</table>

## Berekening van Distinguished Name {#distinguished-name-calculation}

Als u wenst om de Distinguished Name (DN) herkenningstekens gegevens te verwerken, laat de volgende stap van de plaatsingstovenaar u de berekeningswijze vormen.

![](assets/s_ncs_install_deployment_wiz_ldap_02.png)

* Geef de unieke id van de gebruiker op in de map (Distinguished Name - DN) in het veld **[!UICONTROL Distinguished Name]** .

  **[!UICONTROL (login)]** wordt vervangen door de id van de Adobe Campaign-operator.

  >[!CAUTION]
  >
  >De instelling **[!UICONTROL dc]** moet in kleine letters worden weergegeven.

* Selecteer de optie **[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]** om de groep- en gebruikerskoppelingen in de LDAP-directory en de groep- en gebruikerskoppelingen in Adobe Campaign te synchroniseren.

  Wanneer u deze optie selecteert, worden de opties **[!UICONTROL Application level DN used for the search]** en **[!UICONTROL Password of the application login]** ingeschakeld.

  Als u deze twee velden invult, maakt Adobe Campaign verbinding met de LDAP-server met een eigen aanmelding en wachtwoord. Als deze leeg zijn, maakt Adobe Campaign anoniem verbinding met de server.

## Zoeken naar id&#39;s {#searching-for-identifiers}

Als u verkiest om naar een herkenningsteken te zoeken, laat de plaatsingstovenaar u het onderzoek vormen.

* Geef in de velden **[!UICONTROL Application level DN used for the search]** en **[!UICONTROL Password of the application login]** de id en het wachtwoord op waarmee Adobe Campaign verbinding maakt om de id te zoeken. Als deze leeg zijn, maakt Adobe Campaign anoniem verbinding met de server.
* Geef de velden **[!UICONTROL Base identifier]** en **[!UICONTROL Search scope]** op om te bepalen van welke subset van de LDAP-directory de zoekopdracht moet starten.

  Selecteer de gewenste modus in de vervolgkeuzelijst:

  ![](assets/s_ncs_install_deployment_wiz_ldap_03.png)

   1. **[!UICONTROL Recursive (default mode)]**.

      De LDAP-directory wordt volledig doorzocht, vanaf een bepaald niveau.

   1. **[!UICONTROL Limited to the base]**.

      Alle kenmerken worden opgenomen in de zoekopdracht.

   1. **[!UICONTROL Limited to the first sub-level of the base]**.

      De zoekopdracht wordt uitgevoerd op alle kenmerken van de map en begint op het eerste niveau van het kenmerk.

* In het veld **[!UICONTROL Filter]** kunt u een element opgeven om het bereik van de zoekopdracht te verfijnen.

## LDAP-machtigingen configureren {#configuring-ldap-authorizations}

Dit venster wordt weergegeven wanneer u de optie **[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]** selecteert.

![](assets/s_ncs_install_deployment_wiz_ldap_04.png)

U moet verschillende parameters opgeven om de groep of groepen te vinden waartoe de gebruiker behoort en de bijbehorende rechten, te weten:

* het veld **[!UICONTROL Database identifier]** ,
* het veld **[!UICONTROL Search scope]** ,

  >[!NOTE]
  >
  >Als u ervoor hebt gekozen om naar DN te zoeken, kunt u **[!UICONTROL Reuse the DN search parameters]** selecteren om de geselecteerde waarden voor de DN en het zoekbereik van het vorige scherm over te nemen.

* het veld **[!UICONTROL Rights search filter]**, op basis van de aanmeldingsnaam en de DN-naam van de gebruiker,
* het veld **[!UICONTROL Attribute containing the group or authorization name]** betreffende de gebruiker,
* het veld **[!UICONTROL Association mask]** waarin de naam van de groep kan worden opgehaald in Adobe Campaign en de bijbehorende rechten. U kunt reguliere expressies gebruiken om naar de naam te zoeken.
* Selecteer **[!UICONTROL Enable the connection of users declared in the LDAP directory if the operator is not declared in Adobe Campaign]** zodat de gebruiker automatisch toegangsrechten krijgt bij verbinding.

Klik op **[!UICONTROL Save]** om het configureren van de instantie te voltooien.

## Operatoren beheren {#managing-operators}

Nadat u de configuratie hebt bevestigd, moet u bepalen welke Adobe Campaign-operatoren via de LDAP-directory worden beheerd.

Als u de LDAP-directory wilt gebruiken om een operator te verifiëren, bewerkt u het bijbehorende profiel en klikt u op de koppeling **[!UICONTROL Edit the access parameters]** . Selecteer de optie **[!UICONTROL Use LDAP for authentication]** : het veld **[!UICONTROL Password]** wordt grijs weergegeven voor deze operator.

![](assets/s_ncs_install_operator_in_ldap.png)

## Gebruiksscenario’s {#use-cases}

Deze sectie biedt een aantal eenvoudige gebruiksgevallen om u te helpen de meest geschikte configuraties te bereiken op basis van uw behoeften.

1. Er is een gebruiker gemaakt in de LDAP-directory, maar niet in Adobe Campaign.

   Adobe Campaign kan zo worden geconfigureerd dat de gebruiker toegang krijgt tot het platform via de LDAP-verificatie. Adobe Campaign moet de geldigheid van de combinatie id/wachtwoord in de LDAP-directory kunnen controleren, zodat de operator in Adobe Campaign direct kan worden gemaakt. Schakel de optie **[!UICONTROL Enable the connection of users declared in the LDAP directory if the operator is not declared in Adobe Campaign]** in om dit te doen. In dit geval moet ook groepssynchronisatie worden geconfigureerd: de optie **[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]** moet worden geselecteerd.

1. De gebruiker is gemaakt in Adobe Campaign, maar niet in de LDAP-directory.

   Ze kunnen zich niet aanmelden bij Adobe Campaign.

1. De LDAP-directory bevat een groep die niet bestaat in Adobe Campaign.

   Deze groep wordt niet gemaakt in Adobe Campaign. U moet de groep maken en de groepen synchroniseren om een overeenkomst mogelijk te maken via de optie **[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]** .

1. Groepen bestaan in Adobe Campaign en de LDAP-directory wordt geactiveerd na de gebeurtenis: gebruikersgroepen in Adobe Campaign worden niet automatisch vervangen door de inhoud van LDAP-groepen. Op dezelfde manier geldt dat als een groep alleen in Adobe Campaign bestaat, er geen LDAP-gebruikers aan kunnen worden toegevoegd totdat de groep is gemaakt en gesynchroniseerd in LDAP.

   Groepen worden nooit direct gemaakt, noch door Adobe Campaign, noch door LDAP. Ze moeten afzonderlijk worden gemaakt, zowel in Adobe Campaign als in de LDAP-directory.

   De namen van groepen in de LDAP-directory moeten overeenkomen met de namen van Adobe Campaign-groepen. Hun verenigingsmasker wordt bepaald in het laatste configuratiestadium van de plaatsingstovenaar: Adobe Campaign_ (.&#42; ), bijvoorbeeld.
