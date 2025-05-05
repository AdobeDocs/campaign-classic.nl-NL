---
product: campaign
title: Tomcat-versie zoeken in Adobe Campaign
description: Leer hoe u de huidige versie van de ingesloten Tomcat-webservlet kunt achterhalen die in een instantie van Adobe Campaign wordt gebruikt
feature: Monitoring
badge-v7-prem: label="Alleen op locatie/hybride" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=nl" tooltip="Alleen van toepassing op on-premise en hybride implementaties"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 76411b29-d300-4aaa-8d3b-d8ff74c3ce93
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '515'
ht-degree: 0%

---

# Tomcat-versie zoeken{#locate-tomcat-version}

Adobe Campaign gebruikt een **ingebedde Webserver genoemd Apache Tomcat** om HTTP/HTTPS- verzoeken tussen de toepassing en om het even welke externe interface (met inbegrip van de Console van de Cliënt, gevolgde verbindingen URL, SOAP vraag, en anderen) te verwerken. Er is vaak een externe webserver (meestal IIS of Apache) voor deze server voor naar buiten gerichte Adobe Campaign-instanties.

Volg hieronder de procedure om de nauwkeurige versie van Tomcat te weten te komen die in a **wordt gebruikt Campaign Classic op-gebouw instantie** om te helpen kwesties problemen oplossen.

## Tomcat gebruikt in Adobe Campaign

Tomcat wordt uitgevoerd op Java en vereist dat JDK wordt geïnstalleerd. Voor meer informatie, zie de Uitrusting van de Ontwikkeling van Java (JDK) in de [ Matrijs van de Verenigbaarheid van de Campagne ](../../rn/using/compatibility-matrix.md) sectie.

De Tomcat die in Adobe Campaign wordt gebruikt, is een aangepaste ingesloten versie die niet alle functies van de volledige algemeen beschikbare versie van Tomcat gebruikt en die mogelijk niet alle kwetsbaarheden van de volledige versie ondervindt. De Tomcat mag ook niet worden blootgesteld aan het externe internet, en Adobe Campaign-instanties die worden blootgesteld, moeten een externe webserver (IIS, Apache, enz.) vóór de Tomcat hebben om deze te beschermen.

Nieuwe of bijgewerkte versies van de ingesloten versies van Tomcat worden alleen vrijgegeven met nieuwe builds van Adobe Campaign zelf en niet als afzonderlijke patches buiten de Adobe Campaign-builds.

>[!AVAILABILITY]
>
>
>* Vanaf Campagne v7.4.1 is Tomcat 10.1 de standaardversie.
>
>* Adobe Campaign Classic maakt geen gebruik van WebSocket- en HTTP2-protocollen.
>


## Hoe te om van de versie van ingebedde Tomcat de plaats te bepalen

Voer de onderstaande stappen uit om de versie van ingesloten Tomcat in een exemplaar van Adobe Campaign te zoeken.

>[!NOTE]
>
>U moet toegang hebben tot de bestanden op de Adobe Campaign-server die u moet controleren. De hieronder beschreven procedure is slechts op **op-gebouw het ontvangen modellen** van toepassing.

1. Navigeer aan *\ tomcat-11 \ lib* subfolder binnen de de installatiemap van Adobe Campaign (bijvoorbeeld, *C:\Program [ Installation_folder]* in Vensters, of */usr/local/neolane/nl6* in Linux).

1. Kopieer het dossier *catalina.jar* aan een buiten tijdelijke omslag (bijvoorbeeld, uw Desktop) en noem de uitbreiding van .jar aan .zip anders.

1. Pak het gekopieerde bestand uit. Dit resulteert in veel submappen en bestanden.

1. Binnen de niet gezipte dossiers/de omslagen, open of lees het volgende bevatte dossier gebruikend een tekstredacteur: *org/apache/catalina/util/ServerInfo.properties*. Mogelijk moet u de extensie .txt toevoegen om het openen met een teksteditor te vergemakkelijken.

1. Als het bestand zich op een servercomputer bevindt, verwijdert u de tijdelijke bestanden die u hebt gemaakt.

Als voorbeeld, bevat het *dossier 0&rbrace; ServerInfo.properties voor Adobe Campaign de volgende informatie, die op Tomcat v11.X wijst:*

*`server.info=Apache Tomcat/11.X`*

*`server.number=A.B.X.Y`*

*`server.built=MM DD YYY HH:MM:SS`*

Zodra u de nauwkeurige versie van Tomcat kunt bepalen die in een bepaald geval wordt gebruikt, kan het u in het oplossen van problemen met betrekking tot Tomcat helpen.

>[!NOTE]
>
>De belangrijkste versie van het ingesloten Tomcat-bestand wordt alleen bijgewerkt wanneer de belangrijkste versie van Adobe Campaign wordt gewijzigd (hoewel oudere versies mogelijk niet meer officieel worden ondersteund, kan de informatie nuttig zijn omdat sommige klanten deze versies mogelijk nog steeds uitvoeren).
>

