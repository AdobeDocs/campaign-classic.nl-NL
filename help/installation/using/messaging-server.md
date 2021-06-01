---
product: campaign
title: Berichtenserver
description: Berichtenserver
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: d9ffa58d-81e3-4291-8502-3cb7c326b666
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '162'
ht-degree: 3%

---

# Berichtenserver{#messaging-server}

Adobe Campaign verwerkt uitgaande e-mail zelf, maar een traditionele e-mailserver is vereist voor het ontvangen van inkomende berichten die zijn gekoppeld aan geretourneerde e-mail (van mailingdaemons). De brievenbussen die op deze server worden gevormd zullen automatisch door de toepassing worden verwerkt.

Alle servers die voor POP3 toegang worden gevormd kunnen worden gebruikt om terugkeerpost te ontvangen als zij SMTP &quot;bericht-identiteitskaart&quot;kopballen wanneer het opnemen van de post bewaren. Bijvoorbeeld, zijn de implementaties die Qmail, SendMail en de Uitwisseling van Microsoft gebruiken momenteel in productie. In sommige installaties van Lotus Notes/domino is echter een probleem met het onderhoud van de koppen voor &quot;message-id&quot; aan het licht gekomen.

>[!CAUTION]
>
>Deze mailserver moet mogelijk zware belastingen verwerken: In aanvankelijke fasen, kunnen de typische lijsten tot 10% stuittarieven veroorzaken (als u 100.000 berichten verzendt, verwacht om 10.000 grenzen te ontvangen).
>
>Daarom adviseren wij tegen het gebruiken van uw server van het bedrijfsoverseinen voor deze taak aangezien het sterk kan worden beïnvloed.
>
>Het is raadzaam om een specifiek subdomein van uw DNS en een specifieke server voor stuiterende post te vormen.
