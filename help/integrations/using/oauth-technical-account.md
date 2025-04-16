---
product: campaign
title: Een technische Adobe-account voor API's maken en configureren
description: Meer informatie over het maken van uw Adobe API-account
role: User, Admin
level: Intermediate, Experienced
exl-id: 5d830ea0-a0a3-4b35-8dc4-e955380431fb
source-git-commit: 84e6b2fad97f0ca5d6621cff4648e0be0bef7521
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 2%

---

# Uw technische account voor Adobe maken {#create-service-account}

Server-aan-server authentificatiegeloofsbrieven staan de server van uw toepassing toe om toegangstokens te produceren en API vraag namens uw toepassing zelf te maken. [Meer informatie](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/)

## Bestaande integratie migreren {#migrate-jwt}

De service Account (JWT)-referentie wordt door Adobe afgekeurd. Campagne-integratie met Adobe-oplossingen en -toepassingen moet nu afhankelijk zijn van OAuth Server-to-Server-referenties.

Als u binnenkomende of uitgaande integratie met Campagne vóór Juni 2024 hebt uitgevoerd, moet u uw milieu van de Campagne aan v7.4.1 bevorderen en uw Technische Rekening migreren aan Auth zoals gedetailleerd [ in deze documentatie ](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration){target="_blank"}. De bestaande geloofsbrieven van de Rekening van de Dienst (JWT) zullen tot **30 juni, 2025** blijven werken.

Zodra de migratie wordt gedaan, moet u uw nieuwe geloofsbrieven aan Campagne zoals die in [ wordt verklaard deze sectie ](#add-credentials) associëren.

## Nieuwe technische OAuth-account maken voor nieuwe integratie {#oauth-service}

Ga als volgt te werk om uw technische OAuth-account voor nieuwe integraties te maken:

1. De console van Adobe Developer van de toegang en login als **Beheerder van het Systeem** van uw Organisatie.

   Voor meer informatie over rollen Admin, verwijs naar deze [ pagina ](https://helpx.adobe.com/enterprise/using/admin-roles.html).

1. Klik op **[!UICONTROL Create a new project]**.

   ![](assets/api-account-1.png)

1. Klik op **[!UICONTROL Add to Project]** en selecteer **[!UICONTROL API]** .

   ![](assets/api-account-2.png)

1. Selecteer het product dat u wilt integreren met Campagne en klik op **[!UICONTROL Next]** .

1. Kies **[!UICONTROL OAuth Server-to-Server]** als verificatietype en klik op **[!UICONTROL Next]** .

   ![](assets/api-account-3.png)

1. Selecteer de koppeling **[!UICONTROL Product profile]** naar uw project.

   U kunt desgewenst een nieuwe sjabloon maken. [Meer informatie](https://helpx.adobe.com/enterprise/using/manage-product-profiles.html)

1. Klik vervolgens op **[!UICONTROL Save Configured API]** .

   ![](assets/api-account-4.png)

1. Selecteer in uw project onder Referentie de optie [!DNL OAuth Server-to-Server] en kopieer de volgende gegevens:

   * **[!UICONTROL Client ID]**
   * **[!UICONTROL Client secret]**
   * **[!UICONTROL Technical account ID]**
   * **[!UICONTROL Organization ID]**

## OAuth projectgeloofsbrieven in Campaign toevoegen {#add-credentials}

Als de bovenstaande stappen zijn uitgevoerd, voegt u uw OAuth-projectgegevens in Adobe Campaign toe.

>[!NOTE]
>
>Als gehoste of beheerde klant van de Diensten van de Wolk, is deze stappen niet nodig: Adobe heeft reeds uw OAuth projectgeloofsbrieven aan uw milieu toegevoegd.
>

Als klant op locatie of hybride klant voert u de volgende stappen uit:

1. Meld u via SSH aan bij elke container waarin de Adobe Campaign-instantie is geïnstalleerd.

1. Voeg uw OAuth projectgeloofsbrieven in Adobe Campaign toe door het volgende bevel als `neolane` gebruiker in werking te stellen. Hiermee worden de **[!UICONTROL Technical Account]** -referenties ingevoegd in het configuratiebestand van de instantie.

   ```
   nlserver config -instance:<instance_name> -setimsoauth:ims-org-id/client-id/technical-account-id/client-secret
   ```

   >[!NOTE]
   >
   > Gebruik `setimsauth` of `setimsjwtauth` in plaats van `setimsoauth` voor versies ouder dan 7.4.1.


