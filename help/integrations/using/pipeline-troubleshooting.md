---
title: Integratie configureren
seo-title: Integratie configureren
description: Integratie configureren
seo-description: null
page-status-flag: never-activated
uuid: e2db7bdb-8630-497c-aacf-242734cc0a72
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
discoiquuid: 1c20795d-748c-4f5d-b526-579b36666e8f
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0112d5bd052ad66169225073276d1da4f3c245d8
workflow-type: tm+mt
source-wordcount: '642'
ht-degree: 0%

---


# Problemen met pijpleidingen oplossen {#pipeline-troubleshooting}

**Pipelined ontbreekt met fout &quot;Geen taak beantwoordt aan het masker pipelined@&quot;**

Uw versie van Adobe Campaign Classic biedt geen ondersteuning voor de pijpleiding.

1. Controleer of het [!DNL pipelined] element aanwezig is in het configuratiebestand. Als dat niet het geval is, betekent dit dat dit niet wordt ondersteund.
1. Upgrade naar versie 6.11 build 8705 of hoger.

**Pipelined failed with &#39;&#39; aurait dmeeste commencer par &#39;[&#39; ou &#39;{&#39; (iRc=16384)&quot;**

De optie **NmsPipeline_Config** is niet ingesteld. Het is eigenlijk een JSON-parseringsfout.
Stel de JSON-configuratie in de optie **NmsPipeline_Config** in. Zie &quot;verpletterende optie&quot;in deze pagina.

**Pipelined ontbreekt met &quot;het onderwerp moet een geldige organisatie of een cliënt zijn&quot;**

De configuratie IMSOrgid is ongeldig.

1. Controleer of de IMSOrgId is ingesteld in de serverConf.xml.
1. Zoek een lege IMSOrgId in het instantie config dossier dat het gebrek kan met voeten treden. Als dat het geval is, verwijdert u het.
1. Controleer of de IMSOrgId overeenkomt met die van de klant in de Experience Cloud.

**Pipelined ontbreekt met &quot;ongeldige sleutel&quot;**

De parameter @authPrivateKey van het instance config-bestand is onjuist.

1. Controleer of de authPrivateKey is ingesteld.
1. Controleer of de authPrivateKey: begint met @, eindigt met = en is ongeveer 4000 tekens lang.
1. Zoek de originele sleutel en controleer of deze: in formaat RSA, 4096 beetjes lang, en begint met —BEGIN RSA PRIVATE KEY—.
   <br> Maak de sleutel zo nodig opnieuw en registreer deze op Adobe Analytics. Zie deze [sectie](../../integrations/using/configuring-pipeline.md#oauth-client-creation).
1. Controleer of de sleutel is gecodeerd binnen dezelfde instantie als [!DNL pipelined]. <br>Voer zo nodig de codering opnieuw uit met behulp van het voorbeeld JavaScript of de workflow.

**Pipelined ontbreekt met &quot;kan het teken tijdens authentificatie lezen niet&quot;**

De persoonlijke sleutel heeft een ongeldige indeling.

1. Voer de stappen voor sleutelversleuteling op deze pagina uit.
1. Controleer of de sleutel op dezelfde instantie is versleuteld.
1. Controleer of de authPrivateKey in het configuratiebestand overeenkomt met de gegenereerde sleutel. <br>Gebruik OpenSSL om het sleutelpaar te genereren. PuttyGen bijvoorbeeld genereert niet de juiste indeling.

**Er worden geen triggers opgehaald**

Wanneer het [!DNL pipelined] proces wordt uitgevoerd en er geen triggers worden opgehaald:

1. Controleer of de trigger actief is in Analytics en of deze gebeurtenissen genereert.
1. Zorg ervoor dat het [!DNL pipelined] proces wordt uitgevoerd.
1. Zoek naar fouten in het [!DNL pipelined] logboek.
1. Zoek naar fouten in de [!DNL pipelined] statuspagina. trigger-discarted, trigger-failure moet nul zijn.
1. Controleer of de triggernaam in de **[!UICONTROL NmsPipeline_Config]** optie is geconfigureerd. Als er twijfel bestaat, gebruikt u de jokertekenoptie.
1. Controleer of Analytics een actieve trigger heeft en of deze gebeurtenissen genereert. Er kan een vertraging van een paar uur optreden nadat de configuratie in Analytics is gemaakt voordat deze actief is.

**Gebeurtenissen zijn niet gekoppeld aan een klant**

Wanneer bepaalde gebeurtenissen niet aan een klant zijn gekoppeld:

1. Controleer of de afstemmingsworkflow actief is, indien van toepassing.
1. Controleer of de gebeurtenis een klant-id bevat.
1. Maak een vraag op de klantenlijst gebruikend klantenidentiteitskaart
1. Controleer de frequentie waarmee de klant importeert. Nieuwe klanten worden met een workflow geïmporteerd naar Adobe Campaign.

**Latentie bij gebeurtenisverwerking**

Wanneer de Analytics-tijdstempel veel ouder is dan de aanmaakdatum van de gebeurtenis in Campagne.

Over het algemeen kan het 15 tot 90 minuten duren voordat een marketingcampagne wordt gestart. Dit varieert afhankelijk van de implementatie van gegevensinzameling, lading op de pijpleiding, douaneconfiguratie van de bepaalde trekker, en het werkschema in Adobe Campaign.

1. Controleer of het [!DNL pipelined] proces actief is geweest.
1. Zoek naar fouten in pipelined.log die nieuwe pogingen kunnen veroorzaken. Corrigeer de fouten, indien van toepassing.
1. Controleer de [!DNL pipelined] statuspagina voor de rijgrootte. Als de wachtrij groot is, verbetert u de prestaties van de JS.
1. Aangezien een vertraging met volume lijkt te toenemen, configureert u de triggers op Analytics met behulp van minder berichten.
Bijlagen

**JavaScript voor sleutelversleuteling gebruiken**

Voer een JavaScript uit om de persoonlijke sleutel te versleutelen. Het wordt vereist voor de pijpleidingsconfiguratie.

Hier is een codevoorbeeld dat u kunt gebruiken om de cryptString functie in werking te stellen:

```
/*
USAGE:
  nlserver javascript -instance:<instancename> -file -arg:"<private_key.pem file>" -file encryptKey.js
*/
 
function usage()
{
  return "USAGE:\n" +
    '  nlserver javascript -instance:<instancename> -file -arg:"<private_key.pem file>" -file encryptKey.js\n'
}
 
var fn = application.arg;
if( fn == "" )
  logError("Missing key file file\n" + usage());
 
//open the pem file
plaintext = loadFile(fn)
 
if( !plaintext.match(/^-----BEGIN RSA PRIVATE KEY-----/) )
  logError("File should be an rsa private key")
 
logInfo("Encrypted key:\n" + cryptString(plaintext, <xtkSecretKey>))
```

Voer op de server de JavaScript-code uit:

```
nlserver javascript -instance:<instancename> -file -arg:"<private_key.pem file>" -file encryptKey.js
```

Kopieer en plak de gecodeerde sleutel van de output aan de console.