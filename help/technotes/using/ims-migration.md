---
title: Migratie van technische gebruikers naar Adobe Developer-console
description: Leer hoe u technische operatoren van campagnes kunt migreren naar een technische account op de Adobe Developer-console
feature: Technote
role: Admin
exl-id: 1a409daf-57be-43c9-a3d9-b8ab54c88068
source-git-commit: af811b2df325efcaee38a967252b6952e67680d1
workflow-type: tm+mt
source-wordcount: '1775'
ht-degree: 0%

---

# Migratie van technische operatoren van campagnes naar Adobe Developer Console {#migrate-tech-users-to-ims}

In het kader van de inspanningen om het beveiligings- en verificatieproces te versterken, te beginnen met Campaign Classic v7.3.5, wordt het verificatieproces naar Campaign Classic verbeterd. De technische exploitanten moeten nu de [Adobe Identity Management System (IMS)](https://helpx.adobe.com/enterprise/using/identity.html){target="_blank"} om verbinding te maken met Campagne. Meer informatie over het verificatieproces van de nieuwe server naar de server vindt u in [Adobe Developer Console-documentatie](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/){target="_blank"}. **Adobe raadt aan deze migratie uit te voeren in v7 om probleemloos te kunnen migreren naar Campaign v8.**

Een technische operator is een Campagnegebruikersprofiel dat expliciet is gemaakt voor API-integratie. In dit artikel worden de stappen beschreven die nodig zijn om een technische operator via de Adobe Developer-console naar een technische account te migreren.

## Heb je invloed op?{#ims-impacts}

Als u API vraag van een systeem buiten Campagne in of uw instantie van de Marketing van de Campagne of de instantie van het Centrum van het Bericht in real time maakt, adviseert de Adobe u hoogst om de technische exploitant(en) aan technische rekening(en) door de Console van Adobe Developer te migreren zoals hieronder gedetailleerd.

Deze wijziging is van toepassing vanaf Campaign Classic v7.3.5 (en de nieuwste [Met IMS compatibele versies voor migratie](ac-ims.md#ims-versions)) en is **verplicht** naar Adobe Campaign v8 verplaatsen.

## Migratieproces {#ims-migration-procedure}

Voer de onderstaande stappen uit om een of meer technische accounts te maken in de Adobe Developer Console en gebruik vervolgens deze nieuwe accounts om de verificatiemethoden te kunnen wijzigen voor al uw externe systemen die API-aanroepen uitvoeren in Adobe Campaign.

Een overzicht van de stappen is:

* Een project maken in de Adobe Developer-console
* Wijs de aangewezen API&#39;s aan het nieuwe project toe
* De benodigde profielen van campagneproducten aan het project toekennen
* Werk uw API&#39;s bij om de nieuwe gegevens van de technische account te gebruiken
* Verwijder de verouderde technische operatoren uit uw Campagne-instantie


### Voorwaarden voor migratie{#ims-migration-prerequisites}

<!--To be able to create the technical accounts which replace the technical operators, the prerequisite that the proper Campaign Product Profiles exist within the Admin Console for all Campaign instances need to be validated. You can learn more about Product Profiles within the Adobe Console in [Adobe Developer Console documentation](https://developer.adobe.com/developer-console/docs/guides/projects/){target="_blank"}.-->

* Campagne-gehost en Managed Services-klanten

  Voor API-aanroepen naar de Message Center-instantie(s) moet het productprofiel (hieronder vermeld) worden gemaakt tijdens de upgrade naar Campagne v7.4.1 (of een ander profiel) [Compatibele versie van IMS-migratie](ac-ims.md#ims-versions)), of tijdens levering van de instantie. Neem contact op met uw Overgangsmanager of Klantenondersteuning als u het productprofiel niet ziet voordat u de IMS-migratie start. Dit productprofiel heeft de volgende naam:

  `campaign - <your campaign marketing instance> - messagecenter`

  Als u reeds op IMS gebaseerde authentificatie voor gebruikerstoegang tot Campagne gebruikt, dan zouden de productprofielen nodig voor de API vraag reeds binnen de Admin Console moeten bestaan. Als u een groep van de douaneexploitant binnen Campagne voor de API vraag aan de instantie van de Marketing gebruikt, moet u dat productprofiel binnen de Admin Console tot stand brengen.

  In andere gevallen moet u contact opnemen met de Adobe Overgangsmanager (voor Managed Services-gebruikers) of de klantenservice Adoben (voor andere gehoste gebruikers), zodat technische teams van Adoben uw bestaande groepen van beheerders en benoemde rechten op de productprofielen in de Admin Console kunnen migreren.

* Campagne-on-premise en Hybride klanten

  Voor API-aanroepen naar de Message Center-instantie(s) moet u een productprofiel maken met de naam:

  `campaign - <your campaign instance> - messagecenter`

  Als u reeds op IMS gebaseerde authentificatie voor gebruikerstoegang tot Campagne gebruikt, dan zouden de productprofielen nodig voor de API vraag reeds binnen de Admin Console moeten bestaan. Als u een groep van de douaneexploitant binnen Campagne voor de API vraag aan de instantie van de Marketing gebruikt, moet u dat productprofiel binnen de Admin Console tot stand brengen.

  Meer informatie over productprofielen vindt u in de Adobe Console in [Adobe Developer Console-documentatie](https://developer.adobe.com/developer-console/docs/guides/projects/){target="_blank"}


### Stap 1 - Maak uw Campagne-project in de Adobe Developer-console {#ims-migration-step-1}

Integraties worden gemaakt als onderdeel van een **Project** in Adobe Developer Console. Meer informatie over projecten in [Adobe Developer Console-documentatie](https://developer.adobe.com/developer-console/docs/guides/projects/){target="_blank"}.

U kunt elk project gebruiken dat u eerder hebt gemaakt of u kunt een nieuw project maken. De stappen voor het maken van een project worden beschreven in het dialoogvenster [Adobe Developer Console-documentatie](https://developer.adobe.com/developer-console/docs/guides/getting-started/){target="_blank"}. U vindt hieronder de belangrijkste stappen

<!--
For this migration, you must add below APIs in your project: **I/O Management API** and **Adobe Campaign**.

![](assets/do-not-localize/ims-products-and-services.png)-->

Als u een nieuw project wilt maken, klikt u op **Nieuw project maken** in het hoofdscherm van de Adobe Developer-console.

![](assets/New-Project.png)

U kunt de **Project bewerken** om de naam van dit project te wijzigen.


### Stap 2 - voeg APIs aan uw project toe {#ims-migration-step-2}

Voeg vanuit het nieuwe projectscherm de API&#39;s toe die nodig zijn om dit project als een technische account te kunnen gebruiken voor uw API-aanroepen naar Adobe Campaign.

Ga als volgt te werk om API&#39;s aan uw project toe te voegen:

1. Klikken op **API toevoegen** om APIs te selecteren om aan uw project toe te voegen.
   ![](assets/do-not-translate/ims-updates-01.png)
1. Selecteer de Adobe Campaign API en voeg deze toe aan uw project door het selectievakje rechtsboven in de Adobe Campaign-kaart in te schakelen. Dit selectievakje wordt weergegeven wanneer u de muis boven de kaart houdt
   ![](assets/do-not-translate/ims-updates-02.png)
1. Klikken **Volgende** onder aan het scherm.

### Stap 3 - selecteer het authentificatietype  {#ims-migration-step-3}

In de **API configureren** het vereiste verificatietype. **OAuth Server-to-Server** Verificatie is vereist voor dit project. Zorg ervoor dat deze is geselecteerd en klik op **Volgende** onder aan het scherm.

![](assets/do-not-translate/ims-updates-03.png)

<!--
Once your project is created in the Adobe Developer Console, add an API that uses Server-to-Server authentication. Learn how to set up the OAuth Server-to-Server credential in [Adobe Developer Console documentation](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation/){target="_blank"}.

When the API has been successfully connected, you can access the newly generated credentials including Client ID and Client Secret, as well as generate an access token.-->

### Stap 4 - Selecteer de productprofielen {#ims-migration-step-4}

Zoals beschreven in de sectie Voorwaarden moet u de juiste productprofielen toewijzen die door het project worden gebruikt. In deze stap moet u het productprofiel of de profielen selecteren die moeten worden gebruikt door de technische account die wordt gemaakt.

Als deze technische rekening wordt gebruikt om API vraag aan de instantie van het Centrum van het Bericht te maken, zorg ervoor om het het productprofiel van de Adobe te selecteren, beëindigend met berichtcentrum, voor de Instantie van de Marketing verbonden aan het Centrum van het Bericht.

Voor API-aanroepen naar de marketinginstantie(s) selecteert u het productprofiel dat overeenkomt met de instantie en de exploitantgroep, bijvoorbeeld `campaign - <your campaign marketing instance> - Admin`.

Klik op **geconfigureerde API opslaan** onder aan het scherm.

<!--
You can now add your Campaign product profile to the project, as detailed below:

1. Open the Adobe Campaign API.
1. Click the **Edit product profiles** button

    ![](assets/do-not-localize/ims-edit-api.png)

1. Assign all the relevant Product Profiles to the API, for example 'messagecenter', and save your changes.
1. Browse to the **Credential details** tab of your project, and copy the **Technical Account Email** value.-->

### Stap 5 - voeg toe I/O Beheer API aan uw project {#ims-migration-step-5}


Van het projectscherm, klik **[!UICONTROL + Add to Project]** en kiest u **[!UICONTROL API]** linksboven in het scherm om de API voor I/O-beheer aan dit project toe te voegen.

![](assets/do-not-translate/ims-updates-04.png)

In de **Een API toevoegen** scherm, omlaag schuiven om de **API voor I/O-beheer** kaart. Selecteer het door checkbox te klikken die verschijnt wanneer u over de kaart beweegt. Klik vervolgens op **Volgende** onder aan het scherm.

![](assets/do-not-translate/ims-updates-05.png)


In de **API configureren** -scherm, bestaat de OAuth Server-to-Server-verificatie al. Klikken **geconfigureerde API opslaan** onder aan het scherm.


![](assets/do-not-translate/ims-updates-06.png)

Dit neemt u terug naar het scherm van het Project binnen het I/O Beheer API van het pas gecreëerde project. Klik op de projectnaam in de broodkruimels bij de bovenkant van het scherm om terug naar de belangrijkste pagina van de Details van het Project te nemen.


### Stap 6 - verifieer de projectopstelling {#ims-migration-step-6}

Controleer uw project om ervoor te zorgen dat het er net als hieronder uitziet **API voor I/O-beheer** en **ADOBE CAMPAIGN API** zichtbaar in de sectie Producten en de Diensten en **OAuth Server-to-Server** in de sectie Referenties.

![](assets/do-not-translate/ims-updates-07.png)


### Stap 7 - Valideer uw configuratie {#ims-migration-step-7}

Voer de stappen in het dialoogvenster [Handleiding voor Adobe Developer Console-referenties](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation/#generate-access-tokens){target="_blank"} voor het produceren van een toegangstoken en kopieer het verstrekte bevel van de Steekproef cURL. U kunt een soapaanroep maken met deze gegevens om te testen of u de Adobe Campaign-instantie(s) correct kunt verifiëren en er verbinding mee kunt maken. We raden u aan deze validatie uit te voeren voordat u alle wijzigingen aanbrengt in de integratie van de externe API.

### Stap 8 - De integratie van de externe API bijwerken {#ims-migration-step-8}

U moet nu alle API-integraties bijwerken en aanroepen naar Adobe Campaign uitvoeren om het zojuist gemaakte technische account te kunnen gebruiken.

Raadpleeg de onderstaande codevoorbeelden voor meer informatie over de integratiestappen van de API.

Wanneer u Adobe Identity Management System (IMS)-verificatie gebruikt om een WSDL-bestand te genereren, moet u de Autorisatie toevoegen: Drager &lt;ims_technical_token_token> in de postbode :

```
curl --location --request POST 'https://<instance_url>/nl/jsp/schemawsdl.jsp?schema=nms:rtEvent' \--header 'Authorization: Bearer <Technical account access token>'
```

>[!BEGINTABS]

>[!TAB SOAP]

```
curl --location --request POST 'https://<instance_name>.campaign.adobe.com/nl/jsp/soaprouter.jsp' \
--header 'Content-Type: text/xml; charset=utf-8' \
--header 'SOAPAction: xtk:queryDef#ExecuteQuery' \
--header 'Authorization: Bearer eyJhw' \
--data-raw '<?xml version="1.0" encoding="utf-8"?>
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
  <soap:Body>
    <ExecuteQuery xmlns="urn:xtk:queryDef">
            <sessiontoken></sessiontoken>
            <entity>
                <queryDef schema="nms:recipient" operation="select">
                    <!-- fields to retrieve -->
                    <select>
                        <node expr="@lastName"/>
                        <node expr="@email"/>
                        <node expr="@firstName"/>
                    </select>
                    <!-- condition on email -->
                    <!-- <where><condition expr="@email= '\''joh@com.com'\''"/>
                </where> -->
                </queryDef>
            </entity>
        </ExecuteQuery>
  </soap:Body>
</soap:Envelope>
'
```

>[!TAB  SampleCode Java]

```javascript
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.io.IOException;
import com.google.gson.Gson;
import com.google.gson.JsonObject;
 
import com.google.gson.JsonSyntaxException;
import org.apache.hc.client5.http.classic.methods.HttpPost;
import org.apache.hc.client5.http.impl.classic.CloseableHttpClient;
import org.apache.hc.client5.http.impl.classic.CloseableHttpResponse;
import org.apache.hc.client5.http.impl.classic.HttpClients;
import org.apache.hc.core5.http.HttpEntity;
import org.apache.hc.core5.http.io.entity.StringEntity;
 
 
public class TAAccessToken {
    public static void main(String[] args) throws IOException {
        String accessToken = null;
        CloseableHttpClient httpClient = HttpClients.createDefault();
        try {
            HttpPost httpPost = new HttpPost("https://ims-na1.adobelogin.com/ims/token/v3");
 
            // Request headers
            httpPost.addHeader("Content-Type", "application/x-www-form-urlencoded");
 
            String clientId = "<client_id>";
            String clientSecret = "<client_secret>";
            String scopes = "<scopes>";
 
            // Define the request body
            String requestBody = "client_id="+clientId+"&client_secret="+clientSecret+"&grant_type=client_credentials&scope="+scopes+"";
            StringEntity requestEntity = new StringEntity(requestBody);
            httpPost.setEntity(requestEntity);
 
            // Execute the request
            CloseableHttpResponse response = httpClient.execute(httpPost);
            try {
                // Get the response entity
                HttpEntity entity = response.getEntity();
                int responseCode = response.getCode();
 
                // Print the response
                if (entity != null) {
                    BufferedReader bufferedReader = new BufferedReader(new InputStreamReader(entity.getContent()));
                    String lineImsToken;
                    StringBuilder responseImsToken = new StringBuilder();
                    while ((lineImsToken = bufferedReader.readLine()) != null) {
                        responseImsToken.append(lineImsToken);
                    }
 
                    String jsonString = responseImsToken.toString();
 
                    try {
                        Gson gson = new Gson();
                        JsonObject jsonObject = gson.fromJson(jsonString, JsonObject.class);
 
                        // Get the value of a specific key
                        accessToken = jsonObject.get("access_token").getAsString();
                    }
                    catch (JsonSyntaxException | NullPointerException e) {
                        System.err.println("Error parsing JSON: " + e.getMessage());
                        e.printStackTrace();
                    }
                    System.out.println("Response Code: " + responseCode);
                    System.out.println("Response Body: " + accessToken);
                }
            } catch (IOException e) {
                e.printStackTrace();
            } finally {
                response.close();
            }
        } finally {
            httpClient.close();
        }
 
        CloseableHttpClient httpClientSoap = HttpClients.createDefault();
        try {
            HttpPost httpPostSoap = new HttpPost("https://<instance_name>.campaign.adobe.com/nl/jsp/soaprouter.jsp");
 
            // Request headers
            httpPostSoap.addHeader("Content-Type", "text/xml; charset=utf-8");
            httpPostSoap.addHeader("SOAPAction", "xtk:queryDef#ExecuteQuery");
            httpPostSoap.addHeader("Authorization", "Bearer "+accessToken);
 
            // Request body
            String xmlData = "<?xml version=\"1.0\" encoding=\"utf-8\"?>\n" +
                    "<soap:Envelope xmlns:soap=\"http://schemas.xmlsoap.org/soap/envelope/\">\n" +
                    "  <soap:Body>\n" +
                    "    <ExecuteQuery xmlns=\"urn:xtk:queryDef\">\n" +
                    "            <sessiontoken></sessiontoken>\n" +
                    "            <entity>\n" +
                    "                <queryDef schema=\"nms:recipient\" operation=\"select\">\n" +
                    "                    <!-- fields to retrieve -->\n" +
                    "                    <select>\n" +
                    "                        <node expr=\"@lastName\"/>\n" +
                    "                        <node expr=\"@email\"/>\n" +
                    "                        <node expr=\"@firstName\"/>\n" +
                    "                    </select>\n" +
                    "                    <!-- condition on email -->\n" +
                    "                    <!-- <where><condition expr=\"@email= '\''joh@com.com'\''\"/>\n" +
                    "                </where> -->\n" +
                    "                </queryDef>\n" +
                    "            </entity>\n" +
                    "        </ExecuteQuery>\n" +
                    "  </soap:Body>\n" +
                    "</soap:Envelope>";
            StringEntity requestEntity = new StringEntity(xmlData);
            httpPostSoap.setEntity(requestEntity);
 
            // Execute the request
            CloseableHttpResponse response = httpClientSoap.execute(httpPostSoap);
            try {
                // Get the response entity
                HttpEntity entity = response.getEntity();
 
                // Print the response
                if (entity != null) {
                    BufferedReader bufferedReader = new BufferedReader(new InputStreamReader(entity.getContent()));
                    String line;
                    while ((line = bufferedReader.readLine()) != null) {
                        System.out.println(line);
                    }
                }
            } catch (IOException e) {
                e.printStackTrace();
            } finally {
                response.close();
            }
        } finally {
            httpClientSoap.close();
        }
 
    }
}
```

>[!TAB SampleCodePython]

```python
import requests
 
oauth_url = 'https://ims-na1.adobelogin.com/ims/token/v3'
data = {
    'grant_type': 'client_credentials',
    'scope': '<scopes>',
    'client_id': '<client_id>',
    'client_secret': '<client_secret>'
}
 
headers = {
    'Content-Type': 'application/x-www-form-urlencoded',
    'Accept': 'application/json'
}
response = requests.post(oauth_url, data=data, headers=headers)
response = response.json()
access_token = response['access_token']
 
 
url = 'https://<instance_name>.campaign.adobe.com/nl/jsp/soaprouter.jsp'
headers = {
    'Content-Type': 'text/xml; charset=utf-8',
    'SOAPAction': 'xtk:queryDef#ExecuteQuery',
    'Authorization': 'Bearer '+access_token
}
xml_data = '''<?xml version="1.0" encoding="utf-8"?>
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
  <soap:Body>
    <ExecuteQuery xmlns="urn:xtk:queryDef">
            <sessiontoken></sessiontoken>
            <entity>
                <queryDef schema="nms:recipient" operation="select">
                    <!-- fields to retrieve -->
                    <select>
                        <node expr="@lastName"/>
                        <node expr="@email"/>
                        <node expr="@firstName"/>
                    </select>
                    <!-- condition on email -->
                    <!-- <where><condition expr="@email= '\''joh@com.com'\''"/>
                </where> -->
                </queryDef>
            </entity>
        </ExecuteQuery>
  </soap:Body>
</soap:Envelope>
'''
response = requests.post(url, headers=headers, data=xml_data)
```

>[!ENDTABS]

Raadpleeg voor meer informatie [Adobe Developer Console-verificatiedocumentatie](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/){target="_blank"}.

Hieronder zijn steekproef SOAP vraag die vóór en na migratievraag naar de derdesystemen toont.

Zodra het migratieproces wordt bereikt en bevestigd, worden de Vraag van Soap als volgt bijgewerkt:

* Vóór de migratie: er was geen ondersteuning voor het token voor toegang tot de technische account.

  ```sql
  POST /nl/jsp/soaprouter.jsp HTTP/1.1
  Host: localhost:8080
  Content-Type: application/soap+xml;
  SOAPAction: "nms:rtEvent#PushEvent"
  charset=utf-8
  
  <?xml version="1.0" encoding="utf-8"?>  <soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:nms:rtEvent">
  <soapenv:Header/>
  <soapenv:Body>
      <urn:PushEvent>
          <urn:sessiontoken>SESSION_TOKEN</urn:sessiontoken>
          <urn:domEvent>
              <!--You may enter ANY elements at this point-->
              <rtEvent type="type" email="name@domain.com"/>
          </urn:domEvent>
      </urn:PushEvent>
  </soapenv:Body>
  </soapenv:Envelope>
  ```

* Na de migratie: er is ondersteuning voor het token voor toegang tot de technische account. Van het toegangstoken wordt verwacht dat het wordt geleverd in `Authorization` koptekst als token voor Drager. Het gebruik van sessietoken moet hier worden genegeerd, zoals in het onderstaande voorbeeld met soapoproepen wordt getoond.

  ```sql
  POST /nl/jsp/soaprouter.jsp HTTP/1.1
  Host: localhost:8080
  Content-Type: application/soap+xml;
  SOAPAction: "nms:rtEvent#PushEvent"
  charset=utf-8
  Authorization: Bearer <IMS_Technical_Token_Token>
  
  <?xml version="1.0" encoding="utf-8"?>  <soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:nms:rtEvent">
  <soapenv:Header/>
  <soapenv:Body>
      <urn:PushEvent>
          <urn:sessiontoken></urn:sessiontoken>
          <urn:domEvent>
              <!--You may enter ANY elements at this point-->
              <rtEvent type="type" email="name@domain.com"/>
          </urn:domEvent>
      </urn:PushEvent>
  </soapenv:Body>
  </soapenv:Envelope>
  ```



### Stap 9 - (facultatief) Werk de technische rekeningsexploitant binnen de Console van de Cliënt van de Campagne bij {#ims-migration-step-9}

Deze stap is optioneel en alleen beschikbaar binnen de marketinginstantie(s), niet binnen een Message Center-instantie. Indien specifieke mapmachtigingen of benoemde rechten zijn gedefinieerd voor de technische exploitant, niet via de toegewezen groep(en) bedieners. U moet de nieuwe gebruiker van de Technische Rekening in de Admin Console nu bijwerken om de omslagtoestemmingen of de genoemde vereiste rechten te verlenen.

De gebruiker van de Technische Rekening zal NIET in Adobe Campaign bestaan tot minstens één API vraag aan de Instantie van de Campagne wordt gemaakt, waarbij IMS de gebruiker binnen Campagne zal creëren. Als u de technische gebruikers niet kunt vinden in Campagne, moet u ervoor zorgen dat u een API-aanroep zoals beschreven hebt kunnen verzenden [in stap 7](#ims-migration-step-7).

1. Als u de wijzigingen die nodig zijn voor de nieuwe gebruiker van de technische account wilt toepassen, zoekt u deze via e-mailadres in de Campagne Client Console. Dit e-mailadres is gemaakt tijdens de bovenstaande stappen voor het maken en verifiëren van projecten.

   U kunt dit e-mailadres vinden door op het **OAuth Server-to-Server** in de **Credentials** van het project.

   ![](assets/do-not-translate/ims-updates-07.png)

   In de **Credentials details** tabblad, omlaag schuiven om de **E-mail technische account** en klik op de knop **Kopiëren** knop.

   ![](assets/do-not-translate/ims-updates-08.png)

1. U moet nu de nieuwe technische operator bijwerken in Adobe Campaign Client Console. U moet de bestaande technische omslagtoestemmingen van de exploitant op de nieuwe technische exploitant toepassen.

   Ga als volgt te werk om deze operator bij te werken:

   1. Blader vanuit de Campagne Client Console-verkenner naar de **Beheer > Toegangsbeheer > Operatoren**.
   1. Toegang krijgen tot de bestaande technische operator die wordt gebruikt voor API&#39;s.
   1. Blader naar de machtigingen voor de map en controleer de rechten.
   1. Pas de zelfde toestemmingen op de pas gecreëerde technische exploitant toe. De e-mail van deze operator is de **E-mail technische account** eerder gekopieerde waarde.
   1. Sla uw wijzigingen op.


>[!CAUTION]
>
>De nieuwe technische exploitant moet minstens één API vraag hebben gemaakt om aan de Console van de Cliënt van de Campagne te worden toegevoegd.
>

### Stap 10 - Verwijder de oude technische operator uit Adobe Campaign {#ims-migration-step-10}

Nadat u alle systemen van derden hebt gemigreerd om de nieuwe technische account met IMS-verificatie te gebruiken, kunt u de oude technische operator verwijderen uit de Campagne Client Console.

U doet dit door u aan te melden bij de Console van de Cliënt van de Campagne, navigerend aan **Beheer > Toegangsbeheer > Operatoren** en de oude technische gebruikers zoeken en verwijderen.


>[!MORELIKETHIS]
>
>* [Migratie van eindgebruikers naar IMS](migrate-users-to-ims.md)
>* [Campagne-interface bijwerken na IMS-migratie](impact-ims-migration.md)
>* [Opmerkingen bij de nieuwste release van Adobe Campaign Classic v7](../../rn/using/latest-release.md)
>* [Wat is Adobe Identity Management System (IMS)](https://helpx.adobe.com/enterprise/using/identity.html){target="_blank"}

