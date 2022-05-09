---
product: campaign
title: 'Problemen met de pijplijn oplossen '
description: 'Problemen met de pijplijn oplossen '
audience: integrations
content-type: reference
exl-id: 76645a6f-9536-49d6-b12a-fdd6113d31fa
source-git-commit: 02eebe83de49ee97e573b0c47ca1fddb2195b991
workflow-type: tm+mt
source-wordcount: '705'
ht-degree: 1%

---

# Problemen met de pijplijn oplossen {#pipeline-troubleshooting}

![](../../assets/common.svg)

**Pipelined ontbreekt met fout &quot;Geen taak beantwoordt aan het masker pipelined@&lt; instantie >&quot;**

De pijpleiding wordt niet ondersteund door uw versie van Adobe Campaign Classic.

1. Controleer of de [!DNL pipelined] -element aanwezig is in het configuratiebestand. Als dat niet het geval is, betekent dit dat dit niet wordt ondersteund.
1. Upgrade naar campagne 20.3 / [!DNL Gold Standard] 11 of hoger.

**Pipetteer mislukt met &#39;&#39; aurait dû commencer par `[` ou `{` (iRc=16384)&quot;**

De **NmsPipeline_Config** is niet ingesteld. Het is eigenlijk een JSON-parseringsfout.
De JSON-configuratie instellen in de optie **NmsPipeline_Config**. Zie &quot;verpletterende optie&quot;in deze pagina.

**Pipelined ontbreekt met &quot;het onderwerp moet een geldige organisatie of een cliënt zijn&quot;**

De configuratie van de organisatie-id is ongeldig.

1. Controleer of de organisatie-id (ImsOrgId) is ingesteld in de serverConf.xml.
1. Controleer of een lege Organisatie-id in het configuratiebestand van de instantie de standaardinstelling kan overschrijven. Als dat het geval is, verwijdert u het.
1. Controleer of de organisatie-id correct is. Raadpleeg voor meer informatie over uw organisatie-id [deze pagina](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=nl){_blank}

**Pipelined ontbreekt met &quot;ongeldige sleutel&quot;**

De parameter @authPrivateKey van het instance config-bestand is onjuist.

1. Controleer of de authPrivateKey is ingesteld.
1. Controleer of de authPrivateKey: begint met @, eindigt met = en is ongeveer 4000 tekens lang.
1. Zoek de originele sleutel en controleer of deze: in RSA formaat, 4096 beetjes lang, en begint met `-----BEGIN RSA PRIVATE KEY-----`.
   <br> Maak de sleutel zo nodig opnieuw en registreer deze op Adobe Analytics.
1. Controleer of de sleutel is gecodeerd binnen dezelfde instantie als [!DNL pipelined]. <br>Voer zo nodig de codering opnieuw uit met behulp van het voorbeeld JavaScript of de workflow.

**Pipelined ontbreekt met &quot;kan het teken tijdens authentificatie lezen niet&quot;**

De persoonlijke sleutel heeft een ongeldige indeling.

1. Voer de stappen voor sleutelversleuteling op deze pagina uit.
1. Controleer of de sleutel op dezelfde instantie is versleuteld.
1. Controleer of de authPrivateKey in het configuratiebestand overeenkomt met de gegenereerde sleutel. <br>Gebruik OpenSSL om het sleutelpaar te genereren. PuttyGen bijvoorbeeld genereert niet de juiste indeling.

**De pijplijns ontbreekt met &quot;is niet meer toegestaan toegangstoken te krijgen&quot;**

De logboeken moeten als volgt zijn:

```
2021-05-31T08:42:18.124Z        66462   66501   1       error   log     Listener: JWT Token is empty. (iRc=16384)
2021-05-31T08:42:18.210Z        66462   66501   1       error   log     Unknown authentication mode: 'Bearer realm="Adobe Analytics"'. (iRc=-55)
2021-05-31T08:42:18.210Z        66462   66501   1       error   log     BAS-010007 Function not implemented (iRc=-55)
2021-05-31T08:42:48.582Z        66462   66501   1       warning log     Connection seems to have been lost. Attempting to reconnect.
2021-05-31T08:43:09.156Z        66462   66501   1       error   log     INT-150012 The HTTP query returned a 'Forbidden' type error (403) (iRc=-53)
2021-05-31T08:43:09.160Z        66462   66501   1       error   log     Error while authenticating: '{"error":"This client: df73c224e5-triggers-test is no longer allowed to get access token."}' (iRc=16384)
```

Dit foutbericht geeft aan dat de verificatie is geconfigureerd met de Omniture base OAuth. Zie de [Adobe I/O configureren voor Adobe Experience Cloud Triggers](../../integrations/using/configuring-adobe-io.md) documentatie om uw authentificatie te bevorderen.

**Er worden geen triggers opgehaald**

Wanneer de [!DNL pipelined] proces wordt uitgevoerd en er worden geen triggers opgehaald:

1. Zorg ervoor dat de trigger actief is in Analytics en gebeurtenissen genereert.
1. Zorg ervoor dat de [!DNL pipelined] -proces wordt uitgevoerd.
1. Zoek naar fouten in [!DNL pipelined] log.
1. Zoek naar fouten in [!DNL pipelined] statuspagina. trigger-discarted, trigger-failure moet nul zijn.
1. Controleer of de triggernaam is geconfigureerd in het dialoogvenster **[!UICONTROL NmsPipeline_Config]** optie. Als er twijfel bestaat, gebruikt u de jokertekenoptie.
1. Controleer of Analytics een actieve trigger heeft en gebeurtenissen genereert. Er kan een vertraging van een paar uur optreden nadat de configuratie is gemaakt in Analytics voordat deze actief is.

**Gebeurtenissen zijn niet gekoppeld aan een klant**

Wanneer bepaalde gebeurtenissen niet aan een klant zijn gekoppeld:

1. Controleer of de afstemmingsworkflow actief is, indien van toepassing.
1. Controleer of de gebeurtenis een klant-id bevat.
1. Maak een vraag op de klantenlijst gebruikend klantenidentiteitskaart
1. Controleer de frequentie waarmee de klant importeert. Nieuwe klanten worden met een workflow geïmporteerd naar Adobe Campaign.

**Latentie bij gebeurtenisverwerking**

Wanneer de tijdstempel van Analytics veel ouder is dan de aanmaakdatum van de gebeurtenis in Campagne.

Over het algemeen kan het 15 tot 90 minuten duren voordat een marketingcampagne wordt gestart. Dit varieert afhankelijk van de implementatie van gegevensinzameling, lading op de pijpleiding, douaneconfiguratie van de bepaalde trekker, en het werkschema in Adobe Campaign.

1. Controleer of de [!DNL pipelined] -proces is uitgevoerd.
1. Zoek naar fouten in pipelined.log die nieuwe pogingen kunnen veroorzaken. Corrigeer de fouten, indien van toepassing.
1. Controleer de [!DNL pipelined] statuspagina voor de grootte van de wachtrij. Als de wachtrij groot is, verbetert u de prestaties van de JS.
1. Aangezien een vertraging met volume lijkt te stijgen, vorm de trekkers op Analytics gebruikend minder berichten.

**Werkgebiedinstanties upgraden van verouderde verificatie naar Adobe IO-verificatie**

Het wijzigen van de integratieverificatie in de werkgebiedinstantie heeft geen invloed op de configuratie van de productieinstantie. U kunt ervoor kiezen om uw werkgebiedinstantie te upgraden en vervolgens de verificatie bij te werken naar Adobe-IO en de triggers voor uw werkgebiedinstantie te testen.

Uw productie-instantie zal de oudere verificatie blijven gebruiken en deze wijziging heeft geen invloed op deze instantie.
