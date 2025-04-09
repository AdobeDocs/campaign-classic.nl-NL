---
product: campaign
title: Uw Adobe-account voor API's maken en configureren
description: Meer informatie over het maken van uw Adobe API-account
role: User, Admin
level: Intermediate, Experienced
exl-id: 5d830ea0-a0a3-4b35-8dc4-e955380431fb
source-git-commit: 2bfcec5eaa1145cfb88adfa9c8b2f72ee3cd9469
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 2%

---

# Uw technische account voor Adobe maken {#create-service-account}

Met server-to-server-verificatiereferenties kan de server van uw toepassing toegangstokens genereren en API-aanroepen uitvoeren namens uw toepassing zelf. [Meer informatie](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/)

## Bestaande integraties migreren {#migrate-jwt}

De referentie van het serviceaccount (JWT) wordt afgeschaft door Adobe. Campagne-integraties met Adobe-oplossingen en -apps moeten nu afhankelijk zijn van OAuth Server-to-Server-referenties.

Als u vóór juni 2024 inslag- of uitgaande integraties met Campaign heeft geïmplementeerd, moet u uw Campaign-omgeving upgraden naar v7.4.1 en uw technische account migreren naar oAuth zoals beschreven [in deze documentatie](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration){target="_blank"}. De bestaande inloggegevens voor een serviceaccount (JWT) blijven werken tot **27 januari 2025**.

Zodra de migratie is voltooid, moet u uw nieuwe referentie koppelen aan Campaign, zoals wordt uitgelegd in [deze sectie](#add-credentials).

## Maak een nieuw OAuth technisch account voor nieuwe integraties {#oauth-service}

Ga als volgt te werk om uw OAuth technische account voor nieuwe integraties te maken:

1. Ga naar de Adobe-ontwikkelaarsconsole en meld u aan als **systeembeheerder** van uw organisatie.

   Raadpleeg deze [pagina](https://helpx.adobe.com/enterprise/using/admin-roles.html) voor meer informatie over beheerdersrollen.

1. Klik op **[!UICONTROL Create a new project]**.

   ![](assets/api-account-1.png)

1. Klik **[!UICONTROL Add to Project]** en selecteer **[!UICONTROL API]**.

   ![](assets/api-account-2.png)

1. Selecteer het product dat u wilt integreren met Campaign en klik op **[!UICONTROL Next]**.

1. Kies **[!UICONTROL OAuth Server-to-Server]** als verificatietype en klik op **[!UICONTROL Next]**.

   ![](assets/api-account-3.png)

1. Selecteer de **[!UICONTROL Product profile]** link naar uw project.

   U kunt indien nodig een nieuwe maken. [Meer informatie](https://helpx.adobe.com/enterprise/using/manage-product-profiles.html)

1. Klik vervolgens op **[!UICONTROL Save Configured API]**.

   ![](assets/api-account-4.png)

1. Selecteer [!DNL OAuth Server-to-Server] en kopieer in uw project onder Referenties de volgende gegevens:

   * **[!UICONTROL Client ID]**
   * **[!UICONTROL Client secret]**
   * **[!UICONTROL Technical account ID]**
   * **[!UICONTROL Organization ID]**

## OAuth-projectreferenties toevoegen in Campaign {#add-credentials}

Zodra de bovenstaande stappen zijn uitgevoerd, voegt u uw OAuth-projectreferenties toe in Adobe Campaign.

>[!NOTE]
>
>Als klant van een gehoste of beheerde Cloud Services is deze stap niet nodig: Adobe heeft uw OAuth-projectreferenties al aan uw omgeving toegevoegd.
>

Volg als on-premise of hybride klant de volgende stappen:

1. Meld u via SSH aan bij elke container waarop de Adobe Campaign-instantie is geïnstalleerd.

1. Voeg uw OAuth-projectreferenties toe in Adobe Campaign door de volgende opdracht als gebruiker uit te `neolane` voeren. Hiermee worden de **[!UICONTROL Technical Account]** referenties in het configuratiebestand van de instantie ingevoegd.

   ```
   nlserver config -instance:<instance_name> -setimsoauth:ims-org-id/client-id/technical-account-id/client-secret
   ```

   >[!NOTE]
   >
   > Gebruik voor versies ouder dan 7.4.1 `setimsauth` of `setimsjwtauth` in plaats van `setimsoauth`.


