---
solution: Campaign Classic
product: campaign
title: De integratie configureren
description: De integratie configureren
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '582'
ht-degree: 1%

---


# Problemen met pipelines oplossen {#pipeline-troubleshooting}

**Pipelined ontbreekt met fout &quot;Geen taak beantwoordt aan het masker pipelined@&lt; instantie >&quot;**

De pijpleiding wordt niet ondersteund door uw versie van Adobe Campaign Classic.

1. Controleer of het [!DNL pipelined] element aanwezig is in het configuratiebestand. Als dat niet het geval is, betekent dit dat dit niet wordt ondersteund.
1. Upgrade naar versie 6.11 build 8705 of hoger.

**Pipelined failed with &#39;&#39; aurait dû commencer par `[` ou `{` (iRc=16384)&quot;**

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
   <br> Maak de sleutel zo nodig opnieuw en registreer deze op Adobe Analytics.
1. Controleer of de sleutel is gecodeerd binnen dezelfde instantie als [!DNL pipelined]. <br>Voer zo nodig de codering opnieuw uit met behulp van het voorbeeld JavaScript of de workflow.

**Pipelined ontbreekt met &quot;kan het teken tijdens authentificatie lezen niet&quot;**

De persoonlijke sleutel heeft een ongeldige indeling.

1. Voer de stappen voor sleutelversleuteling op deze pagina uit.
1. Controleer of de sleutel op dezelfde instantie is versleuteld.
1. Controleer of de authPrivateKey in het configuratiebestand overeenkomt met de gegenereerde sleutel. <br>Gebruik OpenSSL om het sleutelpaar te genereren. PuttyGen bijvoorbeeld genereert niet de juiste indeling.

**Er worden geen triggers opgehaald**

Wanneer het [!DNL pipelined] proces wordt uitgevoerd en er geen triggers worden opgehaald:

1. Zorg ervoor dat de trigger actief is in Analytics en gebeurtenissen genereert.
1. Zorg ervoor dat het [!DNL pipelined] proces wordt uitgevoerd.
1. Zoek naar fouten in het [!DNL pipelined] logboek.
1. Zoek naar fouten in de [!DNL pipelined] statuspagina. trigger-discarted, trigger-failure moet nul zijn.
1. Controleer of de triggernaam in de **[!UICONTROL NmsPipeline_Config]** optie is geconfigureerd. Als er twijfel bestaat, gebruikt u de jokertekenoptie.
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

1. Controleer of het [!DNL pipelined] proces actief is geweest.
1. Zoek naar fouten in pipelined.log die nieuwe pogingen kunnen veroorzaken. Corrigeer de fouten, indien van toepassing.
1. Controleer de [!DNL pipelined] statuspagina voor de rijgrootte. Als de wachtrij groot is, verbetert u de prestaties van de JS.
1. Aangezien een vertraging met volume lijkt te stijgen, vorm de trekkers op Analytics gebruikend minder berichten.
Bijlagen
