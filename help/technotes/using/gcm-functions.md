---
product: campaign
title: Nieuwe op GCM gebaseerde functies
description: Nieuwe op GCM gebaseerde functies
feature: Technote
exl-id: 154dee7a-a1e9-40a2-bfa5-3641382d0574
source-git-commit: b6d64f66d287dba79be5eddec48ee852c2c7740c
workflow-type: tm+mt
source-wordcount: '578'
ht-degree: 0%

---

# Op GCM gebaseerde functies {#new-functions}

Om veiligheid te verbeteren, hebben wij het gebruik van het (Geavanceerde Norm van de Encryptie van AES) algoritme met CBC (het Ketelen van het Blok van de Cliënt) wijze voor cryptografische verrichtingen verouderd. Er zijn nieuwe coderingsfuncties geïntroduceerd. Deze functies gebruiken AES met de Wijze van Galois/van de Teller (AES-GCM), die een veiliger alternatief verstrekken. Deze functies zijn beschikbaar in JavaScript, JSP, SOAP APIs, en de schema&#39;s van XML, toestaand klanten aan overgang van CBC aan GCM voor encryptie en decryptie.

Deze documentatie maakt een lijst van de onlangs geïntroduceerde functies AES-GCM en op CBC-Gebaseerde die worden verouderd.

Nieuwe functies:

* [EncryptString API-functie](#encryptString-api-xtk)
* [API-functie EncryptStringWithServerPassword](#EncryptStringWithServerPassword-api-xtk)
* [encryptString javascript, functie](#encryptString-javascript)

Oudere functies die kunnen worden gebruikt voor GCM:

* [Javascript-functie DecryptString](#decryptString-javascript)
* [Javascript-functie DecryptPassword](#decryptPassword-javascript)

[Verouderde functies](#depracated-functions)

## API-functies

### EncryptString {#encryptString-api-xtk}

Codeert de tekenreeks met de instantietoets met het AES-algoritme met de GCM-modus.

```
            String 
            encrypted = EncryptString (
            String       
            decrypted
            

      )
         
```

**Parameters**: Versleutelde tekst

**de waarde(n) van de Terugkeer**: Gecodeerd

**Schema**: xtk:zitting

**Statisch**: Ja

## EncryptStringWithServerPassword {#EncryptStringWithServerPassword-api-xtk}

Codeert de tekenreeks van het teken met de serversleutel met behulp van het AES-algoritme met de GCM-modus.


```
            String 
            encrypted = EncryptStringWithServerPassword (
            String       
            decrypted
            

      )
         
```

**Parameters**: Ontsleuteld

**de waarde(n) van de Terugkeer**: Gecodeerd

**Schema**: xtk:zitting

**Statisch**: Ja

## JavaScript-functies

### encryptString() {#encryptString-javascript}

Codeert een tekenreeks met tekens met de sleutel van de instantie of een andere sleutel.

```
            encryptString (str [, key
      ] [, useSalt ])
         
```

**Parameters**:

* str: De tekenreeks die moet worden gecodeerd.
* key: De AES encryptiesleutel wordt gecodeerd in basis 64: 256 beetjes als de zeer belangrijke lengte 32 is; 192 beetjes als de zeer belangrijke lengte 24 is; 128 beetjes als de zeer belangrijke lengte 16 is of als geen sleutel wordt gespecificeerd.
* useSalt: gebruik een salt van de gegevens om te coderen. Waar standaard.

**waarde van de Terugkeer**: Keert het gecodeerde karakterkoord terug.

**Opmerkingen**

Versleuteling vindt plaats volgens de volgende methode:

* De unicode-tekenreeks wordt omgezet in een UTF-8-tekenreeks.
* Aan het einde wordt een vinkje toegevoegd in de hoofdtekst.
* Deze tekenreeks wordt gecodeerd met het AES-algoritme in de modus Galois/Counter (GCM) met salt met een initialisatievector van 12 bytes en een tag van 16 bytes. Als geen sleutel als parameter wordt verstrekt, wordt de instantiesleutel gebruikt.
* Versleutelde tekst bevat de tag en de initialisatievector.
* Het gecodeerde blok wordt vervolgens omgezet in basis 64.

Decryptie wordt uitgevoerd gebruikend de decryptString functie.

**Eigenschappen**

Beschikbaar in:

* Inhoudsbeheer
* Afleveringseigenschappen
* Afleveringsbericht
* Typologieregel
* Importeren
* JSSP
* SOAP-methode
* WebApp
* Workflow

### decryptString() {#decryptString-javascript}

Decrypteert een koord van karakters met de sleutel van de instantie of een andere sleutel. Deze oudere functie kan met GCM worden gebruikt. Het is afgekeurd voor decodering van scripttekst die is versleuteld met de modus AES-CBC.

```
            decryptString (str [, key
      ] [, useSalt ])
         
```

**Parameters**:

* str: De tekenreeks die moet worden gedecodeerd.
* key: De AES encryptiesleutel wordt gecodeerd in basis 64: 256 beetjes als de zeer belangrijke lengte 32 is; 192 beetjes als de zeer belangrijke lengte 24 is; 128 beetjes als de zeer belangrijke lengte 16 is of als geen sleutel wordt gespecificeerd.
* useSalt: gebruik een salt van de gegevens om te decoderen. Waar standaard.

**waarde van de Terugkeer**: Keert het gedecrypteerde karakterkoord terug.

**Waarschuwing**: De wachtwoorden die in het gegevensbestand (opties/externe rekeningen) worden opgeslagen kunnen niet meer door het gebruik van deze methode worden gedecrypteerd. Voor dat, gebruik [ decryptPassword ](#decryptPassword-javascript).

### decryptPassword() {#decryptPassword-javascript}

Decrypts a password stored in an external account. Deze oudere functie kan met GCM worden gebruikt. Het is afgekeurd voor decodering van scripttekst die is versleuteld met de modus AES-CBC.

```
            decryptPassword (str)
         
```

**Parameters**:

* str: De tekenreeks die moet worden gedecodeerd.

**waarde van de Terugkeer**: Keert het onbewerkte-tekstwachtwoord terug.

**Opmerkingen**

Deze functie kan niet worden aangeroepen in workflows, webtoepassingen, rapporten of leveringen. Het kan in JSSP of SOAP vraagimplementaties worden geroepen. Voorbeeld:

```
        function nms_extAccount_LogonToRemoteInstance(remoteInstanceUrl, login, encryptedPassword) {
        var cnx = null, sessionService = null;
        try
            {
                var cnx = new HttpSoapConnection(remoteInstanceUrl + '/nl/jsp/soaprouter.jsp', 'utf-8', 0);
                sessionService = new SoapService(cnx, 'xtk:session');
                sessionService.addMethod("Logon", "xtk:session#Logon",
                    ["token", "string", "login", "string", "password", "string", "parameters", "NLElement"],
                    ["sessionToken", "string", "sessionInfo", "NLElement", "securityToken", "string"]);
                return sessionService.Logon("", login, decryptPassword(encryptedPassword), <parameters/>);
            }
        catch( e ) {
        logError(e);
        }
        finally {
        if( sessionService ) sessionService.dispose();
        if( cnx ) cnx.dispose();
        }
        })
      
```

## Verouderde functies {#depracated-functions}

De volgende functies zijn volledig afgekeurd:

* cryptString
* Coderen
* EncryptServerPassword
