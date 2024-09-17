---
product: campaign
title: Uw technische account voor Adoben maken en configureren voor API's
description: Meer informatie over het maken van uw Adobe API-account
role: User, Admin
level: Beginner
exl-id: 5d830ea0-a0a3-4b35-8dc4-e955380431fb
source-git-commit: 2ce7a91aaddb0df412fc0002ff1463d48b2b7c3c
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 3%

---

# Uw technische account voor Adobe maken {#create-service-account}

Server-aan-server authentificatiegeloofsbrieven staan de server van uw toepassing toe om toegangstokens te produceren en API vraag namens uw toepassing zelf te maken. [Meer informatie](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/)

## Bestaande integratie migreren {#migrate-jwt}

De referentie van de Rekening van de Dienst (JWT) wordt afgekeurd door Adobe. De integratie van de campagne met de oplossingen en apps van de Adobe moet nu op server-aan-server referentie van OAuth vertrouwen.

Als u binnenkomende of uitgaande integratie met Campagne vóór Juni 2024 hebt uitgevoerd, moet u uw milieu van de Campagne aan v7.4.1 bevorderen en uw Technische Rekening migreren aan Auth zoals gedetailleerd [ in deze documentatie ](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration) {target="_blank"}. De bestaande geloofsbrieven van de Rekening van de Dienst (JWT) zullen blijven werken tot **27 Januari, 2025**.

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
>Als ontvangen of Beheerde klant van Cloud Servicen, is deze stappen niet nodig: de Adobe heeft reeds uw OAuth projectgeloofsbrieven aan uw milieu toegevoegd.
>

Als klant op locatie of hybride klant voert u de volgende stappen uit:

1. Meld u via SSH aan bij elke container waarin de Adobe Campaign-instantie is geïnstalleerd.

1. Voeg uw OAuth projectgeloofsbrieven in Adobe Campaign toe door het volgende bevel als `neolane` gebruiker in werking te stellen. Hiermee worden de **[!UICONTROL Technical Account]** -referenties ingevoegd in het configuratiebestand van de instantie.

   ```
   nlserver config -instance:<instance_name> -setimsoauth:ims-org-id/client-id/technical-account-id/client-secret
   ```
