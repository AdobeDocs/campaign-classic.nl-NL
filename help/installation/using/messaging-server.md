---
product: campaign
title: Berichtenserver
description: Berichtenserver
feature: Installation, Instance Settings
badge-v7-prem: label="Alleen op locatie/hybride" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=nl" tooltip="Alleen van toepassing op on-premise en hybride implementaties"
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: d9ffa58d-81e3-4291-8502-3cb7c326b666
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 3%

---

# Berichtenserver{#messaging-server}



Adobe Campaign verwerkt uitgaande e-mail zelf, maar een traditionele e-mailserver is vereist voor het ontvangen van inkomende berichten die zijn gekoppeld aan geretourneerde e-mail (van mailingdaemons). De brievenbussen die op deze server worden gevormd zullen automatisch door de toepassing worden verwerkt.

Alle servers die voor POP3 toegang worden gevormd kunnen worden gebruikt om terugkeerpost te ontvangen als zij SMTP &quot;bericht-identiteitskaart&quot;kopballen wanneer het opnemen van de post bewaren. Bijvoorbeeld, zijn de implementaties die Qmail gebruiken, SendMail en de Uitwisseling van Microsoft momenteel in productie. In sommige installaties van Lotus Notes/domino is echter een probleem met het onderhoud van de koppen voor &quot;message-id&quot; aan het licht gekomen.

>[!CAUTION]
>
>Deze postserver kan zware lasten moeten behandelen: In aanvankelijke fasen, kunnen de typische lijsten tot 10% stuittarieven veroorzaken (als u 100.000 berichten verzendt, verwacht om 10.000 grenzen te ontvangen).
>
>Daarom adviseren wij tegen het gebruiken van uw server van het bedrijfsoverseinen voor deze taak aangezien het sterk kan worden beïnvloed.
>
>Het is raadzaam om een specifiek subdomein van uw DNS en een specifieke server voor stuiterende post te vormen.
