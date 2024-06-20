---
product: campaign
title: Uw technische account voor Adoben maken en configureren voor API's
description: Meer informatie over het maken van uw Adobe API-account
role: User, Admin
level: Beginner
source-git-commit: efd09fd71069878a5096bfa3592e6ebbaa9dd4e4
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 1%

---

# Een technische account voor Adobe maken {#create-service-account}

Server-aan-server authentificatiegeloofsbrieven staan de server van uw toepassing toe om toegangstokens te produceren en API vraag namens uw toepassing zelf te maken. [Meer informatie](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/)

## Bestaande integratie migreren {#migrate-jwt}

De referentie van de Rekening van de Dienst (JWT) wordt afgekeurd door Adobe. De integratie van de campagne met de oplossingen en apps van de Adobe moet nu op server-aan-server referentie van OAuth vertrouwen.

Als u binnenkomende of uitgaande integratie met Campagne vóór Juni 2024 hebt uitgevoerd, moet u uw milieu van de Campagne aan v7.4.1 bevorderen en uw Technische Rekening migreren aan Auth zoals gedetailleerd [in deze documentatie](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration){target="_blank"}. JWT-referenties (Existing Service Account) blijven werken tot **27 januari 2025**.

Als de migratie is voltooid, moet u uw nieuwe referentie aan Campagne koppelen, zoals wordt uitgelegd in [deze sectie](#add-credentials).

## Nieuwe technische OAuth-account maken voor nieuwe integratie {#oauth-service}

Ga als volgt te werk om uw technische OAuth-account voor nieuwe integraties te maken:

1. Adobe Developer-console openen en aanmelden als **Systeembeheerder** van uw organisatie.

   Raadpleeg deze voor meer informatie over beheerdersrollen [page](https://helpx.adobe.com/enterprise/using/admin-roles.html).

1. Klik op **[!UICONTROL Create a new project]**.

   ![](assets/api-account-1.png)

1. Klikken **[!UICONTROL Add to Project]** en selecteert u **[!UICONTROL API]**.

   ![](assets/api-account-2.png)

1. Selecteer het product dat u wilt integreren met de campagne en klik op **[!UICONTROL Next]**.

1. Kies **[!UICONTROL OAuth Server-to-Server]** als verificatietype en klik op **[!UICONTROL Next]**.

   ![](assets/api-account-3.png)

1. Selecteer de **[!UICONTROL Product profile]** een koppeling naar uw project maken.

   U kunt desgewenst een nieuwe sjabloon maken. [Meer informatie](https://helpx.adobe.com/enterprise/using/manage-product-profiles.html)

1. Klik vervolgens op **[!UICONTROL Save Configured API]**.

   ![](assets/api-account-4.png)

1. Van uw project, onder Referentie selecteert u [!DNL OAuth Server-to-Server] en kopieert u de volgende gegevens:

   * **[!UICONTROL Client ID]**
   * **[!UICONTROL Client secret]**
   * **[!UICONTROL Technical account ID]**
   * **[!UICONTROL Organization ID]**

## OAuth-projectgegevens toevoegen in Adobe Campaign {#add-credentials}

Voer de onderstaande stappen uit om uw OAuth-projectgegevens in Adobe Campaign toe te voegen:

1. Meld u via SSH aan bij elke container waarin de Adobe Campaign-instantie is geïnstalleerd.

1. Voeg uw OAuth projectgeloofsbrieven in Adobe Campaign toe door het volgende bevel als in werking te stellen `neolane` gebruiker. Hiermee voegt u de **[!UICONTROL Technical Account]** referenties in het configuratiebestand van de instantie.

   ```
   nlserver config -instance:<instance_name> -setimsoauth:ims-org-id/client-id/technical-account-id/client-secret
   ```
