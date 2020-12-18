---
solution: Campaign Classic
product: campaign
title: Verbinding maken via LDAP
description: 'Leer hoe u zich bij de campagne aanmeldt met LDAP '
audience: installation
content-type: reference
topic-tags: additional-configurations
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1008'
ht-degree: 1%

---


# Verbinding maken via LDAP{#connecting-through-ldap}

## Campagne en LDAP {#configuring-campaign-and-ldap} configureren

>[!NOTE]
>
>De LDAP-configuratie is alleen mogelijk voor installaties op locatie of voor hybride installaties.

De LDAP-configuratie wordt uitgevoerd in de implementatietovenaar. De optie **[!UICONTROL LDAP integration]** moet tijdens de eerste configuratiestap worden geselecteerd. Zie [Implementatiewizard](../../installation/using/deploying-an-instance.md#deployment-wizard).

In het venster kunt u de identificatie van Adobe Campaign-gebruikers configureren via de opgegeven LDAP-directory.

![](assets/s_ncs_install_deployment_wiz_ldap_01.png)

* Geef het adres van de LDAP-server op in het veld **[!UICONTROL LDAP server]**. U kunt het poortnummer toevoegen. Standaard is de gebruikte poort 389.
* Selecteer in de vervolgkeuzelijst de verificatiemethode voor gebruikers:

   * Gecodeerd wachtwoord (**md5**)

      Standaardmodus.

   * Wachtwoord voor normale tekst + SSL (**TLS**)

      De volledige verificatieprocedure (inclusief wachtwoord) wordt gecodeerd. De veilige haven 636 moet niet op deze wijze worden gebruikt: Adobe Campaign schakelt automatisch over naar de beveiligde modus.

      Wanneer u deze verificatiemodus in Linux gebruikt, wordt het certificaat geverifieerd door een openLDAP-clientbibliotheek. Wij adviseren gebruikend een geldig SSL certificaat zodat de authentificatieprocedure wordt gecodeerd. Anders is de informatie onbewerkte tekst.

      Het certificaat wordt ook geverifieerd in Windows.

   * Windows NT LAN Manager (**NTLM**)

      Eigen Windows-verificatie. De **[!UICONTROL Unique identifier]** wordt alleen voor de domeinnaam gebruikt.

   * Gedistribueerde wachtwoordverificatie (**DPA**)

      Eigen Windows-verificatie. **[!UICONTROL Unique identifier]** wordt gebruikt voor slechts de domeinnaam (domain.com).

   * Wachtwoord voor normale tekst

      Geen versleuteling (alleen voor gebruik in testfasen).

* Selecteer de modus voor gebruikersverificatie: **[!UICONTROL Automatically compute the unique user identifier]** (zie stap [Berekening van DN-naam](#distinguished-name-calculation)) of **[!UICONTROL Search the unique user identifier in the directory]** (zie stap [Zoeken naar id&#39;s](#searching-for-identifiers)).

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
   <td> NTLM &amp; DPA<br /> </td> 
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

## Berekening van opgegeven naam {#distinguished-name-calculation}

Als u wenst om de Distinguished Name (DN) herkenningstekens gegevens te verwerken, laat de volgende stap van de plaatsingstovenaar u de berekeningswijze vormen.

![](assets/s_ncs_install_deployment_wiz_ldap_02.png)

* Geef de unieke id van de gebruiker op in de map (Distinguished Name - DN) in het veld **[!UICONTROL Distinguished Name]**.

   **[!UICONTROL (login)]** wordt vervangen door de identificatiecode van de Adobe Campaign-exploitant.

   >[!CAUTION]
   >
   >De instelling **[!UICONTROL dc]** moet in kleine letters zijn.

* Selecteer de optie **[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]** om de groep en gebruikersverenigingen in de folder LDAP en de groep en gebruikersverenigingen in Adobe Campaign te synchroniseren.

   Wanneer u deze optie selecteert, worden **[!UICONTROL Application level DN used for the search]** en **[!UICONTROL Password of the application login]** toegelaten.

   Als u deze twee velden invult, maakt Adobe Campaign verbinding met de LDAP-server met een eigen aanmelding en wachtwoord. Als deze leeg zijn, maakt Adobe Campaign anoniem verbinding met de server.

## Zoeken naar id&#39;s {#searching-for-identifiers}

Als u verkiest om naar een herkenningsteken te zoeken, laat de plaatsingstovenaar u het onderzoek vormen.

* Geef in de velden **[!UICONTROL Application level DN used for the search]** en **[!UICONTROL Password of the application login]** de id en het wachtwoord op waarmee Adobe Campaign verbinding maakt om naar de id te zoeken. Als deze leeg zijn, maakt Adobe Campaign anoniem verbinding met de server.
* Geef de velden **[!UICONTROL Base identifier]** en **[!UICONTROL Search scope]** op om te bepalen uit welke subset van de LDAP-directory de zoekopdracht moet worden gestart.

   Selecteer de gewenste modus in de vervolgkeuzelijst:

   ![](assets/s_ncs_install_deployment_wiz_ldap_03.png)

   1. **[!UICONTROL Recursive (default mode)]**.

      De LDAP-directory wordt volledig doorzocht, vanaf een bepaald niveau.

   1. **[!UICONTROL Limited to the base]**.

      Alle kenmerken worden opgenomen in de zoekopdracht.

   1. **[!UICONTROL Limited to the first sub-level of the base]**.

      De zoekopdracht wordt uitgevoerd op alle kenmerken van de map en begint op het eerste niveau van het kenmerk.

* Met het veld **[!UICONTROL Filter]** kunt u een element opgeven om het bereik van de zoekopdracht te verfijnen.

## LDAP-machtigingen {#configuring-ldap-authorizations} configureren

Dit venster wordt weergegeven wanneer u de optie **[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]** selecteert.

![](assets/s_ncs_install_deployment_wiz_ldap_04.png)

U moet verschillende parameters opgeven om de groep of groepen te vinden waartoe de gebruiker behoort en de bijbehorende rechten, te weten:

* het veld **[!UICONTROL Database identifier]**,
* het veld **[!UICONTROL Search scope]**,

   >[!NOTE]
   >
   >Als u ervoor hebt gekozen om naar DN te zoeken, kunt u **[!UICONTROL Reuse the DN search parameters]** selecteren om de geselecteerde waarden voor DN en onderzoekswerkingsgebied van het vorige scherm over te dragen.

* het veld **[!UICONTROL Rights search filter]**, gebaseerd op de aanmeldingsnaam en de volledige naam van de gebruiker;
* het veld **[!UICONTROL Attribute containing the group or authorization name]** betreffende de gebruiker,
* het veld **[!UICONTROL Association mask]** waarmee de naam van de groep in Adobe Campaign en de bijbehorende rechten kunnen worden uitgepakt. U kunt reguliere expressies gebruiken om naar de naam te zoeken.
* Selecteer **[!UICONTROL Enable the connection of users declared in the LDAP directory if the operator is not declared in Adobe Campaign]** zodat de gebruiker automatisch toegangsrechten op verbinding wordt verleend.

Klik **[!UICONTROL Save]** om het configureren van de instantie te voltooien.

## Operatoren {#managing-operators} beheren

Nadat u de configuratie hebt bevestigd, moet u bepalen welke Adobe Campaign-operatoren via de LDAP-directory worden beheerd.

Als u de LDAP-directory wilt gebruiken om een operator te verifiëren, bewerkt u het bijbehorende profiel en klikt u op de koppeling **[!UICONTROL Edit the access parameters]**. Selecteer de optie **[!UICONTROL Use LDAP for authentication]**: Het veld **[!UICONTROL Password]** wordt grijs weergegeven voor deze operator.

![](assets/s_ncs_install_operator_in_ldap.png)

## Gebruiksscenario’s {#use-cases}

Deze sectie biedt een aantal eenvoudige gebruiksgevallen om u te helpen de meest geschikte configuraties te bereiken op basis van uw behoeften.

1. Er is een gebruiker gemaakt in de LDAP-directory, maar niet in Adobe Campaign.

   Adobe Campaign kan zo worden geconfigureerd dat de gebruiker toegang krijgt tot het platform via de LDAP-verificatie. Adobe Campaign moet de geldigheid van de combinatie ID/wachtwoord in de LDAP-directory kunnen controleren, zodat de operator in Adobe Campaign direct kan worden gemaakt. Om dit te doen, controleer de **[!UICONTROL Enable the connection of users declared in the LDAP directory if the operator is not declared in Adobe Campaign]** optie. In dit geval, moet de groepssynchronisatie ook worden gevormd: de optie **[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]** moet worden geselecteerd.

1. De gebruiker is gemaakt in Adobe Campaign, maar niet in de LDAP-directory.

   Ze kunnen zich niet aanmelden bij Adobe Campaign.

1. De LDAP-directory bevat een groep die niet bestaat in Adobe Campaign.

   Deze groep wordt niet gemaakt in Adobe Campaign. U moet de groep creëren en de groepen synchroniseren om een gelijke-up via de **[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]** optie toe te laten.

1. Groepen bestaan in Adobe Campaign en de LDAP-directory wordt geactiveerd na de gebeurtenis: gebruikersgroepen in Adobe Campaign worden niet automatisch vervangen door de inhoud van LDAP-groepen. Op dezelfde manier geldt dat als een groep alleen in Adobe Campaign bestaat, er geen LDAP-gebruikers aan kunnen worden toegevoegd totdat de groep is gemaakt en gesynchroniseerd in LDAP.

   Groepen worden nooit direct gemaakt, noch door Adobe Campaign, noch door LDAP. Ze moeten afzonderlijk worden gemaakt, zowel in Adobe Campaign als in de LDAP-directory.

   De namen van groepen in de LDAP-directory moeten overeenkomen met de namen van Adobe Campaign-groepen. Hun verenigingsmasker wordt bepaald in het laatste configuratiestadium van de plaatsingstovenaar: Adobe Campaign_(.*), bijvoorbeeld.

