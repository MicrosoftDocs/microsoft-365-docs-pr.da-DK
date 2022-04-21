---
title: Brug dataconnectors til at importere og arkivere tredjepartsdata i Microsoft 365
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: overview
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- m365initiative-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: 0ce338d5-3666-4a18-86ab-c6910ff408cc
ms.custom:
- seo-marvel-apr2020
description: Få mere at vide om, hvordan du importerer og arkiverer tredjepartsdata fra sociale medieplatforme, chatplatforme og dokumentationsplatforme til Microsoft 365 postkasser.
ms.openlocfilehash: 820c4e2fb92720940a8b4f207d43aea649ef16e7
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/20/2022
ms.locfileid: "64997246"
---
# <a name="learn-about-connectors-for-third-party-data"></a>Få mere at vide om forbindelser til tredjepartsdata

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Microsoft 365 gør det muligt for administratorer at bruge dataconnectors til at importere og arkivere ikke-Microsoft-data fra sociale medieplatforme, chatplatforme og platforme til dokumentsamarbejde til postkasser i din Microsoft 365 organisation. En af de primære fordele ved at bruge dataconnectors til at importere og arkivere tredjepartsdata i Microsoft 365 er, at du kan anvende forskellige Microsoft Purview-løsninger på dataene, når de er blevet importeret. Dette hjælper dig med at sikre, at organisationens ikke-Microsoft-data overholder de regler og standarder, der påvirker din organisation.

Se denne interaktive vejledning, der viser, hvordan du opretter dataconnectors til import og arkivering af tredjepartsdata og eksempler på anvendelse af løsninger til overholdelse af angivne standarder på data, når de er importeret til Microsoft 365.

> [!VIDEO https://mslearn.cloudguides.com/guides/Archive%20data%20from%20non-Microsoft%20sources%20in%20Microsoft%20365]

## <a name="third-party-data-connectors"></a>Dataconnectors fra tredjepart

Microsoft Purview-overholdelsesportalen indeholder oprindelige dataconnectors fra Microsoft til import af data fra forskellige datakilder, f.eks. LinkedIn, Instant Bloomberg og Twitter samt dataconnectorer, der understøtter Insider-løsningen til styring af risici. Ud over disse dataconnectors arbejder Microsoft sammen med følgende partnere om at levere mange flere dataconnectors i tredje del på overholdelsesportalen. Din organisation arbejder sammen med disse partnere om at konfigurere deres arkiveringstjeneste, før du opretter en tilsvarende dataconnector på overholdelsesportalen.

- [Veritas](#veritas-data-connectors)

- [Telemeddelelse](#telemessage-data-connectors)

- [17a-4 LLC](#17a-4-data-connectors)

- [CellTrust](#celltrust-data-connectors)

De tredjepartsdata, der er angivet i de næste afsnit (undtagen HR-data og fysiske badging-data, der bruges til Microsoft 365 Insider Risk Management-løsningen), importeres i brugerpostkasser. De Microsoft Purview-løsninger, der understøtter tredjepartsdata, anvendes på den brugerpostkasse, hvor dataene er gemt.

### <a name="microsoft-data-connectors"></a>Microsoft-dataforbindelser

I følgende tabel vises de oprindelige dataconnectors fra tredjepart, der er tilgængelige på overholdelsesportalen. Tabellen opsummerer også de løsninger til overholdelse af angivne standarder, som du kan anvende, når du har importeret og arkiveret tredjepartsdata i Microsoft 365. Se afsnittet [Oversigt over løsninger til overholdelse af angivne standarder, der understøtter data fra tredjepart for at](#overview-of-compliance-solutions-that-support-third-party-data) få en mere detaljeret beskrivelse af hver overholdelsesløsning, og hvordan den understøtter tredjepartsdata.

Klik på linket i datakolonnen **fra tredjepart** for at gå til den trinvise vejledning til oprettelse af en connector for den pågældende datatype.

|Tredjepartsdata  |Procesførelse i venteposition|eDiscovery  |Opbevaringsindstillinger  |Datastyring  |Kommunikationsoverholdelse  |Styring af insider-risiko  |
|:---------|:---------|:---------|:---------|:---------|:---------|:---------|
|[Meddelelse fra Bloomberg](archive-bloomberg-message-data.md)     |![Markeret.](../media/checkmark.png)|![Markeret.](../media/checkmark.png)|![Markeret.](../media/checkmark.png)|![Markeret.](../media/checkmark.png)|![Markeret.](../media/checkmark.png)||
|[Episke EHR-sundhedssektoren](import-epic-data.md) ||||||![Markeret](../media/checkmark.png)|
|[Facebook](archive-facebook-data-with-sample-connector.md)     |![Markeret.](../media/checkmark.png)|![Markeret.](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|||
|[Generisk EHR-sundhedspleje](import-healthcare-data.md) ||||||![Markeret](../media/checkmark.png)|
|[HR (Hr)](import-hr-data.md) ||||||![Markeret](../media/checkmark.png)|
|[ICE Chat](archive-icechat-data.md)     |![Markeret.](../media/checkmark.png)|![Markeret.](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)||
|[Øjeblikkelig Bloomberg](archive-instant-bloomberg-data.md)|![Markeret.](../media/checkmark.png)|![Markeret.](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)||
|[LinkedIn](archive-linkedin-data.md)   |![Markeret.](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|||
|[Fysisk badging](import-physical-badging-data.md) ||||||![Markeret](../media/checkmark.png)|
|[Slack eDiscovery](archive-slack-data-microsoft.md)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)||
|[Twitter](archive-twitter-data-with-sample-connector.md)     |![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|||
||||||||

### <a name="veritas-data-connectors"></a>Veritas-dataforbindelser

I tabellen i dette afsnit vises de dataconnectors fra tredjepart, der er tilgængelige i partnerskab med Veritas. Tabellen opsummerer også de løsninger til overholdelse af angivne standarder, som du kan anvende på tredjepartsdata, når du har importeret og arkiveret dem i Microsoft 365. Se afsnittet [Oversigt over løsninger til overholdelse af angivne standarder, der understøtter data fra tredjepart for at](#overview-of-compliance-solutions-that-support-third-party-data) få en mere detaljeret beskrivelse af hver overholdelsesløsning, og hvordan den understøtter tredjepartsdata.

Før du kan arkivere tredjepartsdata i Microsoft 365, skal du arbejde med Veritas for at konfigurere deres arkiveringstjeneste (kaldet *Merge1*) for din organisation. Du kan finde flere oplysninger ved at klikke på linket i kolonnen **Data fra tredjepart** for at gå til den trinvise vejledning til oprettelse af en connector til den pågældende datatype.

|Tredjepartsdata  |Procesførelse i venteposition|eDiscovery  |Opbevaringsindstillinger  |Datastyring  |Kommunikationsoverholdelse  |Styring af insider-risiko  |
|:---------|:---------|:---------|:---------|:---------|:---------|:---------|
|[CellTrust](archive-celltrust-data.md)|![Markeret.](../media/checkmark.png)|![Markeret.](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)||
|[Cisco Japper på MS SQL](archive-ciscojabberonmssql-data.md)|![Markeret.](../media/checkmark.png)|![Markeret.](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)||
|[Cisco Japper på Oracle](archive-ciscojabberonoracle-data.md)|![Markeret.](../media/checkmark.png)|![Markeret.](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)||
|[Cisco Japper på PostgreSQL](archive-ciscojabberonpostgresql-data.md)|![Markeret.](../media/checkmark.png)|![Markeret.](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)||
|[EML](archive-eml-data.md)|![Markeret.](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|||
|[FX-forbindelse](archive-fxconnect-data.md)|![Markeret.](../media/checkmark.png)|![Markeret.](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)||
|[Jive](archive-jive-data.md)|![Markeret.](../media/checkmark.png)|![Markeret.](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)||
|[MS SQL Database](archive-mssqldatabaseimporter-data.md)|![Markeret.](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|||
|[Pivot](archive-pivot-data.md)|![Markeret.](../media/checkmark.png)|![Markeret.](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)||
|[Redtail-tale](archive-redtailspeak-data.md)|![Markeret.](../media/checkmark.png)|![Markeret.](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)||
|[Reuters håndtering](archive-reutersdealing-data.md)|![Markeret.](../media/checkmark.png)|![Markeret.](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)||
|[Reuters Eikon](archive-reuterseikon-data.md)|![Markeret.](../media/checkmark.png)|![Markeret.](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)||
|[Reuters FX](archive-reutersfx-data.md)|![Markeret.](../media/checkmark.png)|![Markeret.](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)||
|[RingCentral](archive-ringcentral-data.md)|![Markeret.](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)||
|[Salesforce-snak](archive-salesforcechatter-data.md)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|||
|[ServiceNow](archive-servicenow-data.md)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|||
|[Skype for Business](archive-skypeforbusiness-data.md)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)||
|[Slack eDiscovery](archive-slack-data.md)|![Markeret.](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)||
|[Symphony](archive-symphony-data.md)|![Markeret.](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)||
|[Afgrænset tekst](archive-text-delimited-data.md)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|||
|[Twitter](archive-veritas-twitter-data.md)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|||
|[Webex Teams](archive-webexteams-data.md)|![Markeret.](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)||
|[Websider](archive-webpagecapture-data.md)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|||
|[Workplace fra Facebook](archive-workplacefromfacebook-data.md)|![Markeret.](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)||
|[XIP](archive-xip-data.md)|![Markeret.](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)||
|[XSLT/XML](archive-xslt-xml-data.md)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|||
|[Yieldbroker](archive-yieldbroker-data.md)|![Markeret.](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)||
|[YouTube](archive-youtube-data.md)|![Markeret.](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|||
|[Zoom-møde.](archive-zoommeetings-data.md)     |![Markeret.](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)||
||||||||

### <a name="telemessage-data-connectors"></a>TeleMessage-dataforbindelser

I tabellen i dette afsnit vises de dataconnectors fra tredjepart, der er tilgængelige i partnerskab med TeleMessage. Tabellen opsummerer også de løsninger til overholdelse af angivne standarder, som du kan anvende på tredjepartsdata, når du har importeret og arkiveret dem i Microsoft 365. Se afsnittet [Oversigt over løsninger til overholdelse af angivne standarder, der understøtter data fra tredjepart for at](#overview-of-compliance-solutions-that-support-third-party-data) få en mere detaljeret beskrivelse af hver overholdelsesløsning, og hvordan den understøtter tredjepartsdata.

Før du kan arkivere tredjepartsdata i Microsoft 365, skal du arbejde med TeleMessage for at konfigurere deres arkiveringstjeneste for din organisation. Du kan finde flere oplysninger ved at klikke på linket i kolonnen **Data fra tredjepart** for at gå til den trinvise vejledning til oprettelse af en connector til den pågældende datatype.

TeleMessage-dataconnectors er også tilgængelige i GCC-miljøer i Microsoft 365 US Government-cloudmiljøet. Du kan få flere oplysninger [i afsnittet Dataconnectors i US Government-cloudmiljøet](#data-connectors-in-the-us-government-cloud) i denne artikel.

|Tredjepartsdata  |Procesførelse i venteposition|eDiscovery  |Opbevaringsindstillinger  |Datastyring  |Kommunikationsoverholdelse  |Styring af insider-risiko  |
|:---------|:---------|:---------|:---------|:---------|:---------|:---------|
|[Android](archive-android-archiver-data.md)     |![Markeret.](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)||
|[AT&T-netværk](archive-att-network-archiver-data.md)     |![Markeret.](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)||
|[Klokkenetværk](archive-bell-network-data.md)     |![Markeret.](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)||
|[Virksomhed - nummer](archive-enterprise-number-data.md)     |![Markeret.](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)||
|[O2-netværk](archive-o2-network-data.md)     |![Markeret.](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)||
|[Rogers Network](archive-rogers-network-archiver-data.md)|![Markeret.](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)||
|[Signal](archive-signal-archiver-data.md)|![Markeret.](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)||
|[Telegram](archive-telegram-archiver-data.md)|![Markeret.](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)||
|[TELUS-netværk](archive-telus-network-data.md)    |![Markeret.](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)||
|[Verizon Network](archive-verizon-network-data.md)     |![Markeret.](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)||
|[WeChat](archive-wechat-data.md)|![Markeret.](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)||
|[Whatsapp](archive-whatsapp-data.md)     |![Markeret.](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)||
||||||||

### <a name="17a-4-data-connectors"></a>17a-4 dataforbindelser

Tabellen i dette afsnit viser de dataconnectors fra tredjepart, der er tilgængelige i partnerskab med 17a-4 LLC. Tabellen opsummerer også de løsninger til overholdelse af angivne standarder, som du kan anvende på tredjepartsdata, når du har importeret og arkiveret dem i Microsoft 365. Se afsnittet [Oversigt over løsninger til overholdelse af angivne standarder, der understøtter data fra tredjepart for at](#overview-of-compliance-solutions-that-support-third-party-data) få en mere detaljeret beskrivelse af hver overholdelsesløsning, og hvordan den understøtter tredjepartsdata.

Før du kan arkivere tredjepartsdata i Microsoft 365, skal du arbejde med 17a-4 LLC for at konfigurere deres arkiveringstjeneste (kaldet *DataParser*) for din organisation. Du kan finde flere oplysninger ved at klikke på linket i kolonnen **Data fra tredjepart** for at gå til den trinvise vejledning til oprettelse af en connector til den pågældende datatype.

17a-4-dataconnectors er også tilgængelige i GCC-miljøer i Microsoft 365 US Government-cloudmiljøet. Du kan få flere oplysninger [i afsnittet Dataconnectors i US Government-cloudmiljøet](#data-connectors-in-the-us-government-cloud) i denne artikel.

|Tredjepartsdata  |Procesførelse i venteposition|eDiscovery  |Opbevaringsindstillinger  |Datastyring  |Kommunikationsoverholdelse  |Styring af insider-risiko  |
|:---------|:---------|:---------|:---------|:---------|:---------|:---------|
|[Blackberry](archive-17a-4-blackberry-data.md)     |![Markeret.](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)||
|[Bloomberg](archive-17a-4-bloomberg-data.md)     |![Markeret.](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)||
|[Cisco Jabber](archive-17a-4-cisco-jabber-data.md)   |![Markeret.](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)||
|[Cisco Webex](archive-17a-4-webex-teams-data.md)   |![Markeret.](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)||
|[FactSet](archive-17a-4-factset-data.md)    |![Markeret.](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)||
|[Fuze](archive-17a-4-fuze-data.md)    |![Markeret.](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)||
|[FX-forbindelse](archive-17a-4-fxconnect-data.md)    |![Markeret.](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)||
|[ICE Chat](archive-17a-4-ice-im-data.md)    |![Markeret.](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)||
|[InvestEdge](archive-17a-4-investedge-data.md)    |![Markeret.](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)||
|[LivePerson Conversational Cloud](archive-17a-4-liveperson-data.md)    |![Markeret.](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)||
|[Quip](archive-17a-4-quip-data.md)    |![Markeret.](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)||
|[Refinitiv Eikon Messenger](archive-17a-4-refinitiv-messenger-data.md)    |![Markeret.](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)||
|[ServiceNow](archive-17a-4-servicenow-data.md)    |![Markeret.](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)||
[Skype for Business-server](archive-17a-4-skype-for-business-server-data.md)    |![Markeret.](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)||
|[Slæk](archive-17a-4-slack-data.md)    |![Markeret.](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)||
|[SQL](archive-17a-4-sql-database-data.md)    |![Markeret.](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)||
|[Symphony](archive-17a-4-symphony-data.md)    |![Markeret.](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)||
|[Zoom](archive-17a-4-zoom-data.md)    |![Markeret.](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)||
||||||||

### <a name="celltrust-data-connectors"></a>CellTrust-dataconnectors

I tabellen i dette afsnit vises den dataconnector fra tredjepart, der er tilgængelig i partnerskab med CellTrust. Tabellen opsummerer også de løsninger til overholdelse af angivne standarder, som du kan anvende på tredjepartsdata, når du har importeret og arkiveret dem i Microsoft 365. Se afsnittet [Oversigt over løsninger til overholdelse af angivne standarder, der understøtter data fra tredjepart for at](#overview-of-compliance-solutions-that-support-third-party-data) få en mere detaljeret beskrivelse af hver overholdelsesløsning, og hvordan den understøtter tredjepartsdata.

Før du kan arkivere tredjepartsdata i Microsoft 365, skal du arbejde med CellTrust for at konfigurere deres arkiveringstjeneste (kaldet *CellTrust SL2*) for din organisation. Du kan finde flere oplysninger ved at klikke på linket i datakolonnen **fra tredjepart** for at gå til den trinvise vejledning til oprettelse af en CellTrust SL2-connector.

|Tredjepartsdata  |Procesførelse i venteposition|eDiscovery  |Opbevaringsindstillinger  |Datastyring  |Kommunikationsoverholdelse  |Styring af insider-risiko  |
|:---------|:---------|:---------|:---------|:---------|:---------|:---------|
|[CellTrust SL2](archive-data-from-celltrustsl2.md)     |![Markeret.](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)||
||||||||

CellTrust SL2-dataconnectoren er også tilgængelig i GCC-miljøer i Microsoft 365 US Government-cloudmiljøet. Du kan få flere oplysninger [i afsnittet Dataconnectors i US Government-cloudmiljøet](#data-connectors-in-the-us-government-cloud) i denne artikel.

## <a name="overview-of-compliance-solutions-that-support-third-party-data"></a>Oversigt over løsninger til overholdelse af angivne standarder, der understøtter tredjepartsdata

I de følgende afsnit beskrives nogle af de ting, som Microsoft Purview-løsninger kan hjælpe dig med at administrere de tredjepartsdata, der er angivet i den forrige tabel.

### <a name="litigation-hold"></a>Procesførelse i venteposition

Du placerer en [litigation-venteposition](create-a-litigation-hold.md) på en brugerpostkasse for at bevare tredjepartsdata. Når du opretter en venteposition, kan du angive en varighed af venteposition (også kaldet en *tidsbaseret venteposition*), så slettede og ændrede tredjepartsdata bevares i en bestemt periode og derefter slettes permanent fra postkassen. Eller du kan bare bevare indhold på ubestemt tid (kaldet en *uendelig venteposition*), eller indtil bevarelse af procesførelse er fjernet.

### <a name="ediscovery"></a>eDiscovery

De tre primære eDiscovery-værktøjer i Microsoft 365 er Indholdssøgning, Microsoft Purview eDiscovery (Standard) og Microsoft Purview eDiscovery (Premium).

- **[Indholdssøgning](content-search.md).** Du kan bruge værktøjet til indholdssøgning til at søge i postkasser efter tredjepartsdata, som du har importeret. Du kan bruge søgeforespørgsler og -betingelser til at indsnævre søgeresultaterne og eksportere søgeresultaterne.

- **[eDiscovery (Standard)](get-started-core-ediscovery.md).** Dette værktøj bygger på den grundlæggende søge- og eksportfunktionalitet ved at gøre det muligt for dig at oprette sager, der giver dig mulighed for at styre, hvem der kan få adgang til sagsdata, sætte brugerpostkasser eller postkasseindhold i venteposition, der stemmer overens med søgekriterierne. Det betyder, at du kan placere en eDiscovery-venteposition på de tredjepartsdata, der blev importeret til brugerpostkasser.

- **[eDiscovery (Premium)](overview-ediscovery-20.md).** Dette effektive værktøj udvider sagsfunktionaliteten i eDiscovery (Standard) ved at lade dig føje vogtere til en sag, placere tilsynsførendes data i venteposition og derefter indlæse en tilsynsførendes tredjepartsdata i en gennemgang for at få yderligere analyser, f.eks. temaer og registrering af dubletter. Når du har indlæst tredjepartsdata i et korrektursæt, kan du forespørge på og filtrere dem til et smalt resultatsæt.

   Både eDiscovery (Standard) og eDiscovery (Premium) giver dig mulighed for at administrere tredjepartsdata, der kan være relevante for organisationens juridiske eller interne undersøgelser.

### <a name="retention-settings"></a>Opbevaringsindstillinger

Du kan anvende en [opbevaringspolitik](retention.md) på brugerpostkasser for at bevare og derefter slette tredjepartsdata (og andet postkasseindhold), når opbevaringsperioden er udløbet. Du kan også bruge opbevaringspolitikker til at slette tredjepartsdata af en bestemt alder eller [bruge opbevaringsmærkater til at udløse en gennemgang af fordeling](disposition.md) , når opbevaringsperioden for tredjepartsdata udløber.

### <a name="records-management"></a>Datastyring

Funktionen [datastyring](records-management.md) i Microsoft 365 giver dig mulighed for at deklarere tredjepartsdata som en post. Dette kan gøres manuelt af brugere, der anvender en opbevaringsmærkat, der markerer tredjepartsdata i deres postkasse som post. Eller du kan anvende opbevaringsmærkater automatisk ved at identificere følsomme oplysninger, nøgleord eller indholdstyper i tredjepartsdata.

### <a name="communication-compliance"></a>Kommunikationsoverholdelse

Du kan bruge [Kommunikation med overholdelse af angivne standarder](communication-compliance.md) til at undersøge tredjepartsdata for at sikre, at de overholder organisationens datastandarder. Du kan gøre dette ved at registrere, registrere og udføre afhjælpningshandlinger for upassende meddelelser i din organisation. Du kan f.eks. overvåge de tredjepartsdata, som du importerer for stødende sprog, følsomme oplysninger og lovmæssig overholdelse af angivne standarder.

### <a name="insider-risk-management"></a>Styring af insider-risiko

Signaler fra tredjepartsdata, f.eks. selektive HR-data, kan bruges af [Insider-risikostyringsløsningen](insider-risk-management.md) til at minimere interne risici ved at lade dig registrere, undersøge og reagere på risikable aktiviteter i din organisation. Data, der importeres af HR-dataconnectoren, bruges f.eks. som risikoindikatorer til at hjælpe med at registrere datatyveri fra medarbejdere, der afgår.

## <a name="using-ediscovery-tools-to-search-for-third-party-data"></a>Brug af eDiscovery-værktøjer til at søge efter tredjepartsdata

Når du har brugt dataconnectors til at importere og arkivere tredjepartsdata i brugerpostkasser, kan du bruge Microsoft 365 eDiscovery-værktøjer til at søge efter data fra tredjepart. Du kan også eDiscovery-værktøjer til at oprette forespørgselsbaserede ventepositioner, der er knyttet til sager med eDiscovery (Standard) og eDiscovery (Premium), for at bevare tredjepartsdata. Du kan finde flere oplysninger om eDiscovery-værktøjer [under eDiscovery-løsninger i Microsoft 365](ediscovery.md).

Hvis du vil søge efter (eller placere en venteposition) for alle typer tredjepartsdata, som du har importeret til brugerpostkasser ved hjælp af en dataconnector, kan du bruge følgende søgeforespørgsel. Sørg for at indsnævre søgningen til brugerpostkasser.

```powershell
kind:externaldata
```

Du kan bruge denne forespørgsel i feltet Nøgleord til en **indholdssøgning** , en søgning, der er knyttet til en eDiscovery-sag (Standard) eller en samling i eDiscovery (Premium).

![Forespørgsel, der skal søge efter data fra tredjepart.](..\media\SearchThirdPartyData1.png)

Du kan også bruge parret `kind:externaldata` property:value til at begrænse omfanget af søgninger til tredjepartsdata. Hvis du f.eks. vil søge efter elementer, der er importeret fra en hvilken som helst datakilde fra tredjepart, som indeholder ordet *contoso* i egenskaben **Subject** for det importerede element, skal du bruge følgende forespørgsel i feltet **Nøgleord** :

```powershell
subject:contoso AND kind:externaldata
```

Du kan også bruge betingelsen **Meddelelsestype** til at konfigurere den samme forespørgsel.

![Brug betingelsen Meddelelsestype til at indsnævre søgninger til tredjepartsdata.](..\media\SearchThirdPartyData2.png)

Hvis du vil søge efter en bestemt type arkiverede tredjepartsdata, skal du bruge egenskaben **itemclass** mailbox i en søgeforespørgsel. Brug følgende egenskab:værdiformat:

```powershell
itemclass:ipm.externaldata.<third-party data type>
```

Alle elementer, der importeres af en dataconnector fra tredjepart, indeholder egenskaben **itemclass** med en værdi, der svarer til datatypen fra tredjepart. Hvis du f.eks. vil søge efter Facebook-data, der indeholder ordet *contoso*, skal du bruge følgende forespørgsel i egenskaben **Subject** for det importerede element:

```powershell
subject:contoso AND itemclass:ipm.externaldata.facebook*
```

Her er nogle eksempler på **itemclass-værdier** for forskellige typer tredjepartsdata.

| **Datatype fra tredjepart** | **Værdi for egenskaben itemclass**   |
|---------------------------|-------------------------------------|
| Meddelelse fra Bloomberg         | ipm.externaldata.bloombergmessage* |
| CellTrust                 | ipm.externaldata.celltrust*        |
| Pivot                     | ipm.externaldata.pivot*            |
| WhatsApp-akivering         | ipm.externaldata.whatsapparchiver* |
|||

Der skelnes ikke mellem store og små bogstaver i værdierne for egenskaben *itemclass* . Generelt skal du bruge navnet på datatypen fra tredjepart (uden mellemrum) efterfulgt af et jokertegn ( * ).

Du kan finde flere oplysninger om oprettelse af eDiscovery-søgeforespørgsler under [Nøgleordsforespørgsler og søgebetingelser for eDiscovery](keyword-queries-and-search-conditions.md).

## <a name="data-connectors-in-the-us-government-cloud"></a>Dataconnectors i US Government-cloudmiljøet

Nogle dataconnectors er tilgængelige i US Government-cloudmiljøet. De følgende afsnit angiver de specifikke offentlige miljøer, der understøtter dataconnectors fra tredjepart. Du kan få flere oplysninger om US Government-cloudmiljøer [i Microsoft 365 US Government](/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/microsoft-365-government-how-to-buy).

### <a name="veritas-data-connectors-in-the-us-government-cloud-preview"></a>Veritas-dataconnectors i US Government-cloudmiljøet (prøveversion)

|Dataconnector  |GCC  |GCC High  |Dod  |
|:---------|:---------|:---------|:---------|
|CellTrust| Ja | Nej | Nej |
|Cisco Japper på MS SQL| Ja | Nej | Nej |
|Cisco Japper på Oracle| Ja | Nej | Nej |
|Cisco Japper på PostgreSQL| Ja | Nej | Nej |
|EML| Ja | Nej | Nej |
|FX-forbindelse| Ja | Nej | Nej |
|Jive| Ja | Nej | Nej |
|MS SQL Database| Ja | Nej | Nej |
|Pivot| Ja | Nej | Nej |
|Redtail-tale| Ja | Nej | Nej |
|Reuters håndtering| Ja | Nej | Nej |
|Reuters Eikon| Ja | Nej | Nej |
|Reuters FX| Ja | Nej | Nej |
|RingCentral| Ja | Nej | Nej |
|Salesforce-snak| Ja | Nej | Nej |
|ServiceNow| Ja | Nej | Nej |
|Skype for Business| Ja | Nej | Nej |
|Slack eDiscovery| Ja | Nej | Nej |
|Symphony| Ja | Nej | Nej |
|Afgrænset tekst| Ja | Nej | Nej |
|Twitter| Ja | Nej | Nej |
|Webex Teams| Ja | Nej | Nej |
|Websider| Ja | Nej | Nej |
|Workplace fra Facebook| Ja | Nej | Nej |
|XIP| Ja | Nej | Nej |
|XSLT/XML| Ja | Nej | Nej |
|Yieldbroker| Ja | Nej | Nej |
|YouTube| Nej | Nej | Nej |
|Zoom-møde.| Ja | Nej | Nej |
|||||

### <a name="telemessage-data-connectors-in-the-us-government-cloud"></a>TeleMessage-dataconnectors i US Government-cloudmiljøet

|Dataconnector  |GCC  |GCC High  |Dod  |
|:---------|:---------|:---------|:---------|
|Android-arkivering | Ja | Nej | Nej |
|AT&T SMS/MMS-netværksarkivering | Ja | Nej | Nej |
|Bell SMS/MMS-netværksarkivering | Ja | Nej | Nej |
|Arkivér virksomhedsnummer | Ja | Nej | Nej |
|O2 SMS og Voice Network Archiver | Ja         | Nej | Nej |
|Rogers Netværksarkivering | Ja         | Nej | Nej |
|Signal-arkivering | Ja | Nej | Nej |
|Telegram-arkivering | Ja | Nej | Nej |
|TELUS SMS Network Archiver | Ja | Nej | Nej |
|Verizon SMS/MMS-netværksarkivering | Ja | Nej | Nej |
|WeChat-arkivering | Ja | Nej | Nej |
|WhatsApp-akivering | Ja | Nej | Nej |
|||||

### <a name="17a-4-data-connectors-in-the-us-government-cloud"></a>17a-4-dataconnectors i US Government-cloudmiljøet

|Dataconnector  |GCC  |GCC High  |Dod  |
|:---------|:---------|:---------|:---------|
|BlackBerry DataParser | Ja | Nej | Nej |
|Bloomberg DataParser  | Ja | Nej | Nej |
|Cisco Japper DataParser  | Ja | Nej | Nej |
|Cisco Webex DataParser  | Ja | Nej | Nej |
|FactSet DataParser  | Ja | Nej | Nej |
|Fuze DataParser  | Ja | Nej | Nej |
|FX Connect DataParser  | Ja | Nej | Nej |
|ICE DataParser  | Ja | Nej | Nej |
|InvestEdge DataParser  | Ja | Nej | Nej |
|LivePerson DataParser for samtaler i skyen  | Ja | Nej | Nej |
|Quip DataParser  | Ja | Nej | Nej |
|Refinitiv Eikon Messenger DataParser  | Ja | Nej | Nej |
|ServiceNow DataParser  | Ja | Nej | Nej |
|Skype for Business Server DataParser | Ja | Nej | Nej |
|Slack DataParser | Ja | Nej | Nej |
|SQL DataParser  | Ja | Nej | Nej |
|Symphony DataParser | Ja | Nej | Nej |
|Zoom DataParser | Ja | Nej | Nej |
|||||

### <a name="celltrust-data-connectors-in-the-us-government-cloud"></a>CellTrust-dataconnectors i US Government-cloudmiljøet

|Dataconnector  |GCC  |GCC High  |Dod  |
|:---------|:---------|:---------|:---------|
|CellTrust SL2 | Ja | Nej | Nej |
|||||

## <a name="working-with-a-microsoft-partner-to-archive-third-party-data"></a>Arbejde med en Microsoft-partner for at arkivere data fra tredjepart

En anden mulighed for at importere og arkivere tredjepartsdata er, at din organisation arbejder sammen med en Microsoft-partner. Hvis en datatype fra tredjepart ikke understøttes af de dataconnectors, der er tilgængelige i Microsofts overholdelsescenter, kan du arbejde sammen med en partner, der kan levere en brugerdefineret connector, der konfigureres til at udtrække elementer fra datakilden fra tredjepart med jævne mellemrum og derefter oprette forbindelse til Microsoft-cloudmiljøet af en tredjeparts-API og importere disse elementer til Microsoft 365. Partnerconnectoren konverterer også indholdet af et element fra datakilden fra tredjepart til en mail og importerer det derefter til en postkasse i Microsoft 365.

Du kan se en liste over partnere, som du kan arbejde med, og den trinvise proces for denne metode under [Arbejd med en partner for at arkivere tredjepartsdata i Microsoft 365](work-with-partner-to-archive-third-party-data.md).
