---
title: Brug dataforbindelser til at importere og arkivere tredjepartsdata i Microsoft 365
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
description: Få mere at vide om, hvordan du importerer og arkiverer tredjepartsdata fra sociale medieplatforme, chatplatforme og samarbejdsplatforme til Microsoft 365 postkasser.
ms.openlocfilehash: 06833acd3ea29e30d8789fbb05e0a081309c7f2b
ms.sourcegitcommit: dbce0b6e74ae2efec42fe2b3b82c8e8cabe0ddbe
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/15/2022
ms.locfileid: "63587698"
---
# <a name="learn-about-connectors-for-third-party-data"></a>Få mere at vide om forbindelser til tredjepartsdata

Microsoft 365 giver administratorer mulighed for at bruge dataforbindelser til at importere og arkivere data fra sociale medieplatforme, chatplatforme og samarbejdsplatforme fra tredjeparter til postkasser i Microsoft 365-organisation. En af de primære fordele ved at bruge dataforbindelser til at importere og arkivere tredjepartsdata i Microsoft 365 er, at du kan anvende forskellige Microsoft 365-overholdelsesløsninger på dataene, efter de er blevet importeret. Dette hjælper dig med at sikre, at din organisations data, der ikke er Microsoft-data, overholder de bestemmelser og standarder, der påvirker din organisation.

Se denne interaktive vejledning, der viser, hvordan du opretter dataforbindelser til import og arkivering af data fra tredjeparter samt eksempler på at anvende overholdelsesløsninger på data, efter de er importeret til Microsoft 365.

> [!VIDEO https://mslearn.cloudguides.com/guides/Archive%20data%20from%20non-Microsoft%20sources%20in%20Microsoft%20365]

## <a name="third-party-data-connectors"></a>Tredjepartsdataforbindelser

The Microsoft 365 Overholdelsescenter indeholder oprindelige tredjepartsdataforbindelser fra Microsoft til at importere data fra forskellige datakilder, f.eks. LinkedIn, Instant Bloomberg og Twitter, og dataforbindelser, der understøtter Insider-risikostyringsløsningen. Ud over disse dataforbindelser arbejder Microsoft sammen med følgende partnere om at levere mange flere tredjepartsdataforbindelser i Microsoft 365 Overholdelsescenter. Din organisation arbejder sammen med disse partnere om at konfigurere deres arkiveringstjeneste, før der oprettes en tilsvarende dataforbindelse Microsoft 365 Overholdelsescenter.

- [Veritas](#veritas-data-connectors)

- [TeleMessage](#telemessage-data-connectors)

- [17a-4 LLC](#17a-4-data-connectors)

- [CellTrust](#celltrust-data-connectors)

De tredjepartsdata, der er angivet i næste afsnit (med undtagelse af HR-data og fysiske badgingdata, der bruges til Microsoft 365 Insider-risikostyringsløsningen), importeres til brugerpostkasser. De Microsoft 365 løsninger til overholdelse af regler og standarder, der understøtter tredjepartsdata, anvendes på den brugerpostkasse, hvor dataene er gemt.

### <a name="microsoft-data-connectors"></a>Microsoft-dataforbindelser

I følgende tabel vises de oprindelige tredjepartsdataforbindelser, der er tilgængelige i Microsoft 365 Overholdelsescenter. Tabellen opsummerer også de løsninger til overholdelse af regler og standarder, som du kan anvende, når du importerer og arkiverer tredjepartsdata Microsoft 365. Se afsnittet [Oversigt over](#overview-of-compliance-solutions-that-support-third-party-data) overholdelsesløsninger, der understøtter tredjepartsdata for at få en mere detaljeret beskrivelse af hver overholdelsesløsning, og hvordan den understøtter tredjepartsdata.

Klik på linket i **kolonnen Tredjepartsdata** for at gå til den trinvise vejledning til oprettelse af en forbindelse for den pågældende datatype.

|Tredjepartsdata  |Retslig venteposition|eDiscovery  |Opbevaringsindstillinger  |Datastyring  |Kommunikationsoverholdelse  |Insider-risikostyring  |
|:---------|:---------|:---------|:---------|:---------|:---------|:---------|
|[Bloomberg-meddelelse](archive-bloomberg-message-data.md)     |![Markering.](../media/checkmark.png)|![Markering.](../media/checkmark.png)|![Markering.](../media/checkmark.png)|![Markering.](../media/checkmark.png)|![Markering.](../media/checkmark.png)||
|[Episk EHR-sundhedssektoren](import-epic-data.md) ||||||![Markering](../media/checkmark.png)|
|[Facebook](archive-facebook-data-with-sample-connector.md)     |![Markering.](../media/checkmark.png)|![Markering.](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|||
|[Generisk EHR-sundhedssektoren](import-healthcare-data.md) ||||||![Markering](../media/checkmark.png)|
|[HR (HUMAN Resources)](import-hr-data.md) ||||||![Markering](../media/checkmark.png)|
|[ICE Chat](archive-icechat-data.md)     |![Markering.](../media/checkmark.png)|![Markering.](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)||
|[Øjeblikkelig Bloomberg](archive-instant-bloomberg-data.md)|![Markering.](../media/checkmark.png)|![Markering.](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)||
|[LinkedIn](archive-linkedin-data.md)   |![Markering.](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|||
|[Fysisk badging](import-physical-badging-data.md) ||||||![Markering](../media/checkmark.png)|
|[Slack eDiscovery](archive-slack-data-microsoft.md)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)||
|[Twitter](archive-twitter-data-with-sample-connector.md)     |![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|||
||||||||

### <a name="veritas-data-connectors"></a>Veritas-dataforbindelser

Tabellen i dette afsnit viser de tredjepartsdataforbindelser, der er tilgængelige i partnerskab med Veritas. Tabellen indeholder også en oversigt over de løsninger til overholdelse af angivne standarder, som du kan anvende på tredjepartsdata, når du har importeret og arkiveret dem Microsoft 365. Se afsnittet [Oversigt over](#overview-of-compliance-solutions-that-support-third-party-data) overholdelsesløsninger, der understøtter tredjepartsdata for at få en mere detaljeret beskrivelse af hver overholdelsesløsning, og hvordan den understøtter tredjepartsdata.

Før du kan arkivere tredjepartsdata i Microsoft 365, skal du arbejde sammen med Veritas om at konfigurere deres arkiveringstjeneste (kaldet *Flet1*) for organisationen. Du kan få mere at vide ved at klikke på linket i kolonnen **Tredjepartsdata** for at gå til den trinvise vejledning til at oprette en forbindelse for den pågældende datatype.

|Tredjepartsdata  |Retslig venteposition|eDiscovery  |Opbevaringsindstillinger  |Datastyring  |Kommunikationsoverholdelse  |Insider-risikostyring  |
|:---------|:---------|:---------|:---------|:---------|:---------|:---------|
|[CellTrust](archive-celltrust-data.md)|![Markering.](../media/checkmark.png)|![Markering.](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)||
|[Cisco Jabber på MS SQL](archive-ciscojabberonmssql-data.md)|![Markering.](../media/checkmark.png)|![Markering.](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)||
|[Cisco Jabber på Oracle](archive-ciscojabberonoracle-data.md)|![Markering.](../media/checkmark.png)|![Markering.](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)||
|[Cisco Jabber på PostgreSQL](archive-ciscojabberonpostgresql-data.md)|![Markering.](../media/checkmark.png)|![Markering.](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)||
|[EML](archive-eml-data.md)|![Markering.](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|||
|[FX-Forbind](archive-fxconnect-data.md)|![Markering.](../media/checkmark.png)|![Markering.](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)||
|[Jive](archive-jive-data.md)|![Markering.](../media/checkmark.png)|![Markering.](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)||
|[MS SQL Database](archive-mssqldatabaseimporter-data.md)|![Markering.](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|||
|[Pivot](archive-pivot-data.md)|![Markering.](../media/checkmark.png)|![Markering.](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)||
|[Redtail Speak](archive-redtailspeak-data.md)|![Markering.](../media/checkmark.png)|![Markering.](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)||
|[Reuters Dealing](archive-reutersdealing-data.md)|![Markering.](../media/checkmark.png)|![Markering.](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)||
|[Reuters Eikon](archive-reuterseikon-data.md)|![Markering.](../media/checkmark.png)|![Markering.](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)||
|[Reuters FX](archive-reutersfx-data.md)|![Markering.](../media/checkmark.png)|![Markering.](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)||
|[RingCentral](archive-ringcentral-data.md)|![Markering.](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)||
|[Salesforce Chatter](archive-salesforcechatter-data.md)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|||
|[ServiceNow](archive-servicenow-data.md)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|||
|[Skype for Business](archive-skypeforbusiness-data.md)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)||
|[Slack eDiscovery](archive-slack-data.md)|![Markering.](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)||
|[Ikke-for-store](archive-symphony-data.md)|![Markering.](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)||
|[Tekstsepareret](archive-text-delimited-data.md)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|||
|[Twitter](archive-veritas-twitter-data.md)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|||
|[Webex-Teams](archive-webexteams-data.md)|![Markering.](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)||
|[Websider](archive-webpagecapture-data.md)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|||
|[Arbejdsplads fra Facebook](archive-workplacefromfacebook-data.md)|![Markering.](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)||
|[XIP](archive-xip-data.md)|![Markering.](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)||
|[XSLT/XML](archive-xslt-xml-data.md)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|||
|[Afkastbroker](archive-yieldbroker-data.md)|![Markering.](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)||
|[YouTube](archive-youtube-data.md)|![Markering.](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|||
|[Zoom møder](archive-zoommeetings-data.md)     |![Markering.](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)||
||||||||

### <a name="telemessage-data-connectors"></a>TeleMessage-dataforbindelser

Tabellen i dette afsnit viser de tredjepartsdataforbindelser, der er tilgængelige i partnerskab med TeleMessage. Tabellen indeholder også en oversigt over de løsninger til overholdelse af angivne standarder, som du kan anvende på tredjepartsdata, når du har importeret og arkiveret dem Microsoft 365. Se afsnittet [Oversigt over](#overview-of-compliance-solutions-that-support-third-party-data) overholdelsesløsninger, der understøtter tredjepartsdata for at få en mere detaljeret beskrivelse af hver overholdelsesløsning, og hvordan den understøtter tredjepartsdata.

Før du kan arkivere tredjepartsdata i Microsoft 365, skal du arbejde med TeleMessage for at konfigurere deres arkiveringstjeneste for din organisation. Du kan få mere at vide ved at klikke på linket i kolonnen **Tredjepartsdata** for at gå til den trinvise vejledning til at oprette en forbindelse for den pågældende datatype.

TeleMessage-dataforbindelser er også tilgængelige i GCC i den amerikanske Microsoft 365 government-sky. Du kan finde flere oplysninger i [afsnittet Dataforbindelser i den amerikanske regerings sky](#data-connectors-in-the-us-government-cloud) i denne artikel.

|Tredjepartsdata  |Retslig venteposition|eDiscovery  |Opbevaringsindstillinger  |Datastyring  |Kommunikationsoverholdelse  |Insider-risikostyring  |
|:---------|:---------|:---------|:---------|:---------|:---------|:---------|
|[Android](archive-android-archiver-data.md)     |![Markering.](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)||
|[AT&T-netværk](archive-att-network-archiver-data.md)     |![Markering.](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)||
|[Klokkenetværk](archive-bell-network-data.md)     |![Markering.](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)||
|[Virksomhedsnummer](archive-enterprise-number-data.md)     |![Markering.](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)||
|[O2-netværk](archive-o2-network-data.md)     |![Markering.](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)||
|[Rogers Network](archive-rogers-network-archiver-data.md)|![Markering.](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)||
|[Signal](archive-signal-archiver-data.md)|![Markering.](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)||
|[1.](archive-telegram-archiver-data.md)|![Markering.](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)||
|[TELUS Network](archive-telus-network-data.md)    |![Markering.](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)||
|[Verizon Network](archive-verizon-network-data.md)     |![Markering.](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)||
|[WeChat](archive-wechat-data.md)|![Markering.](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)||
|[WhatsApp](archive-whatsapp-data.md)     |![Markering.](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)||
||||||||

### <a name="17a-4-data-connectors"></a>17a-4 dataforbindelser

Tabellen i dette afsnit viser de tredjepartsdataforbindelser, der er tilgængelige i partnerskab med 17a-4 LLC. Tabellen indeholder også en oversigt over de løsninger til overholdelse af angivne standarder, som du kan anvende på tredjepartsdata, når du har importeret og arkiveret dem Microsoft 365. Se afsnittet [Oversigt over](#overview-of-compliance-solutions-that-support-third-party-data) overholdelsesløsninger, der understøtter tredjepartsdata for at få en mere detaljeret beskrivelse af hver overholdelsesløsning, og hvordan den understøtter tredjepartsdata.

Før du kan arkivere tredjepartsdata i Microsoft 365, skal du arbejde med 17a-4 LLC for at konfigurere deres arkiveringstjeneste (kaldet *DataParser*) for organisationen. Du kan få mere at vide ved at klikke på linket i kolonnen **Tredjepartsdata** for at gå til den trinvise vejledning til at oprette en forbindelse for den pågældende datatype.

17a-4-dataforbindelser er også tilgængelige i GCC i den amerikanske Microsoft 365 Government-sky. Du kan finde flere oplysninger i [afsnittet Dataforbindelser i den amerikanske regerings sky](#data-connectors-in-the-us-government-cloud) i denne artikel.

|Tredjepartsdata  |Retslig venteposition|eDiscovery  |Opbevaringsindstillinger  |Datastyring  |Kommunikationsoverholdelse  |Insider-risikostyring  |
|:---------|:---------|:---------|:---------|:---------|:---------|:---------|
|[BlackBerry](archive-17a-4-blackberry-data.md)     |![Markering.](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)||
|[Bloomberg](archive-17a-4-bloomberg-data.md)     |![Markering.](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)||
|[Cisco Jabber](archive-17a-4-cisco-jabber-data.md)   |![Markering.](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)||
|[Cisco Webex](archive-17a-4-webex-teams-data.md)   |![Markering.](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)||
|[FactSet](archive-17a-4-factset-data.md)    |![Markering.](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)||
|[Fuze](archive-17a-4-fuze-data.md)    |![Markering.](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)||
|[FX-Forbind](archive-17a-4-fxconnect-data.md)    |![Markering.](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)||
|[ICE Chat](archive-17a-4-ice-im-data.md)    |![Markering.](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)||
|[InvestEdge](archive-17a-4-investedge-data.md)    |![Markering.](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)||
|[LivePerson-samtalesky](archive-17a-4-liveperson-data.md)    |![Markering.](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)||
|[Quip](archive-17a-4-quip-data.md)    |![Markering.](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)||
|[Refinitiv Eikon Messenger](archive-17a-4-refinitiv-messenger-data.md)    |![Markering.](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)||
|[ServiceNow](archive-17a-4-servicenow-data.md)    |![Markering.](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)||
[Skype for Business Server](archive-17a-4-skype-for-business-server-data.md)    |![Markering.](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)||
|[Slæk](archive-17a-4-slack-data.md)    |![Markering.](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)||
|[SQL](archive-17a-4-sql-database-data.md)    |![Markering.](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)||
|[Ikke-for-store](archive-17a-4-symphony-data.md)    |![Markering.](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)||
|[Zoom](archive-17a-4-zoom-data.md)    |![Markering.](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)||
||||||||

### <a name="celltrust-data-connectors"></a>CellTrust-dataforbindelser

Tabellen i dette afsnit viser den tredjepartsdataforbindelse, der er tilgængelig i partnerskab med CellTrust. Tabellen indeholder også en oversigt over de løsninger til overholdelse af angivne standarder, som du kan anvende på tredjepartsdata, når du har importeret og arkiveret dem Microsoft 365. Se afsnittet [Oversigt over](#overview-of-compliance-solutions-that-support-third-party-data) overholdelsesløsninger, der understøtter tredjepartsdata for at få en mere detaljeret beskrivelse af hver overholdelsesløsning, og hvordan den understøtter tredjepartsdata.

Før du kan arkivere tredjepartsdata i Microsoft 365, skal du arbejde med CellTrust for at konfigurere deres arkiveringstjeneste (kaldet *CellTrust SL2*) for organisationen. Du kan få mere at vide ved at klikke på linket i kolonnen **Tredjepartsdata** for at gå til den trinvise vejledning til oprettelse af en CellTrust SL2-forbindelse.

|Tredjepartsdata  |Retslig venteposition|eDiscovery  |Opbevaringsindstillinger  |Datastyring  |Kommunikationsoverholdelse  |Insider-risikostyring  |
|:---------|:---------|:---------|:---------|:---------|:---------|:---------|
|[CellTrust SL2](archive-data-from-celltrustsl2.md)     |![Markering.](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)||
||||||||

CellTrust SL2-dataforbindelse er også tilgængelig i GCC i den amerikanske Microsoft 365 Government-sky. Du kan finde flere oplysninger i [afsnittet Dataforbindelser i den amerikanske regerings sky](#data-connectors-in-the-us-government-cloud) i denne artikel.

## <a name="overview-of-compliance-solutions-that-support-third-party-data"></a>Oversigt over løsninger til overholdelse af regler og standarder, der understøtter tredjepartsdata

I de følgende afsnit beskrives nogle af de ting, som Microsoft 365-overholdelsesløsninger kan hjælpe dig med at administrere de tredjepartsdata, der er angivet i den forrige tabel.

### <a name="litigation-hold"></a>Retslig venteposition

Du placerer en [retslig tilbageholdelse](create-a-litigation-hold.md) på en brugerpostkasse for at bevare tredjepartsdata. Når du opretter en venteposition, kan du angive en varighed for venteposition (også kaldet tidsbaseret *venteposition*), så slettede og ændrede tredjepartsdata bevares i en bestemt periode og derefter slettes permanent fra postkassen. Eller du kan blot bevare indhold på ubestemt tid (kaldet uendeligt *venteposition*), eller indtil retslig tilbageholdelse fjernes.

### <a name="ediscovery"></a>eDiscovery

De tre primære eDiscovery-værktøjer i Microsoft 365 er Indholdssøgning, Core eDiscovery og Advanced eDiscovery.

- **[Indholdssøgning](content-search.md).** Du kan bruge værktøjet til indholdssøgning til at søge i postkasser efter tredjepartsdata, du har importeret. Du kan bruge søgeforespørgsler og -betingelser til at indsnævre dine søgeresultater og eksportere søgeresultaterne.

- **[Core eDiscovery](get-started-core-ediscovery.md).** Dette værktøj bygger på den grundlæggende søge- og eksportfunktionalitet ved at gøre det muligt at oprette sager, der giver dig mulighed for at styre, hvem der kan få adgang til sagsdata, sætte brugerpostkasser eller postkasseindhold i venteposition, der opfylder søgekriterierne. Det betyder, at du kan placere et eDiscovery-venteposition på de tredjepartsdata, der blev importeret til brugerpostkasser.

- **[Advanced eDiscovery](overview-ediscovery-20.md).** Dette effektive værktøj udvider sagsfunktionaliteten i Core eDiscovery ved at gøre det muligt for dig at tilføje kontrolianere til en sag, sætte dine oplysninger i venteposition hos en person, der er til hjælp, og derefter indlæse en af en tredjepartsdata i en gennemgang til yderligere analyse, f.eks. temaer og registrering af dubletter. Når du har indlæst tredjepartsdata i et korrektursæt, kan du forespørge og filtrere dem til et smalt resultatsæt.

   Med både Core eDiscovery og Advanced eDiscovery kan du administrere data fra tredjeparter, der kan være relevante for din organisations juridiske eller interne undersøgelser.

### <a name="retention-settings"></a>Opbevaringsindstillinger

Du kan anvende en [opbevaringspolitik](retention.md) på brugerpostkasser for at bevare og derefter slette tredjepartsdata (og andet postkasseindhold), når en opbevaringsperiode udløber. Du kan også bruge opbevaringspolitikker til at slette tredjepartsdata for en bestemt alder eller bruge [](disposition.md) opbevaringsetiketter til at udløse en dispositionsrevision, når opbevaringsperioden for tredjepartsdata udløber.

### <a name="records-management"></a>Datastyring

Funktionen [til datastyring](records-management.md) i Microsoft 365 gør det muligt at erklære tredjepartsdata som en post. Dette kan gøres manuelt af brugere, der anvender en opbevaringsetiket, der markerer tredjepartsdata i deres postkasse som poster. Eller du kan anvende opbevaringsetiketter automatisk ved at identificere følsomme oplysninger, nøgleord eller indholdstyper i tredjepartsdata.

### <a name="communication-compliance"></a>Kommunikationsoverholdelse

Du kan bruge [kommunikationsoverholdelse](communication-compliance.md) til at undersøge tredjepartsdata for at sikre, at de er i overensstemmelse med din organisations datastandarder. Det kan du gøre ved at registrere, registrere og udføre afhjælpningshandlinger for upassende meddelelser i organisationen. Du kan f.eks. overvåge de tredjepartsdata, du importerer til stødende sprog, følsomme oplysninger og overholdelse af lovgivning.

### <a name="insider-risk-management"></a>Insider-risikostyring

Signaler fra tredjepartsdata, f.eks. selektive HR-data, kan bruges [](insider-risk-management.md) af Insider-risikostyringsløsningen for at minimere interne risici ved at lade dig registrere, undersøge og handle på risikabelt arbejde i din organisation. Eksempelvis bruges data, der importeres af HR-dataforbindelse, som risikoindikatorer til at registrere udgående medarbejderdatatyveri.

## <a name="using-ediscovery-tools-to-search-for-third-party-data"></a>Brug af eDiscovery-værktøjer til at søge efter tredjepartsdata

Når du bruger dataforbindelser til at importere og arkivere tredjepartsdata i brugerpostkasser, kan du bruge Microsoft 365 eDiscovery-værktøjer til at søge efter tredjepartsdata. Du kan også bruge eDiscovery-værktøjer til at oprette forespørgselsbaserede ventende funktioner, der er knyttet til Core eDiscovery- og Advanced eDiscovery-sager for at bevare tredjepartsdata. Du kan finde flere oplysninger om eDiscovery-værktøjer [under eDiscovery-løsninger Microsoft 365](ediscovery.md).

Hvis du vil søge efter (eller placere en venteposition) en hvilken som helst type tredjepartsdata, du har importeret til brugerpostkasser ved hjælp af en dataforbindelse, kan du bruge følgende søgeforespørgsel. Sørg for at begrænse søgningen til brugerpostkasser.

```powershell
kind:externaldata
```

Du kan bruge denne forespørgsel i feltet  Nøgleord til en indholdssøgning, en søgning, der er knyttet til en core eDiscovery-sag eller en samling i Advanced eDiscovery.

![Forespørgsel for at søge efter tredjepartsdata.](..\media\SearchThirdPartyData1.png)

Du kan også bruge parret `kind:externaldata` property:value til at begrænse omfanget af søgninger til tredjepartsdata. Hvis du f.eks. vil søge efter elementer, der er importeret fra en datakilde fra en tredjepart, som indeholder ordet  *contoso* i egenskaben Emne for det importerede element, skal du bruge følgende forespørgsel i **feltet Nøgleord:**

```powershell
subject:contoso AND kind:externaldata
```

Du kan også bruge betingelsen **Meddelelsestype** til at konfigurere den samme forespørgsel.

![Brug betingelse for meddelelses type til at indsnævre søgninger til tredjepartsdata.](..\media\SearchThirdPartyData2.png)

Hvis du vil søge efter en bestemt type arkiverede tredjepartsdata, skal du bruge  egenskaben elementklassepostkasse i en søgeforespørgsel. Brug følgende egenskab:værdiformat:

```powershell
itemclass:ipm.externaldata.<third-party data type>
```

Hvert element, der importeres af en tredjepartsdataforbindelse,  omfatter egenskaben elementklasse med en værdi, der svarer til tredjepartsdatatypen. Hvis du f.eks. vil søge efter Facebook-data, der indeholder ordet *contoso*, skal du bruge følgende forespørgsel i egenskaben Emne for det importerede element:

```powershell
subject:contoso AND itemclass:ipm.externaldata.facebook*
```

Her er nogle få eksempler på **elementklasseværdier** for forskellige typer tredjepartsdata.

| **Tredjepartsdatatype** | **Værdi for egenskaben elementklasse**   |
|---------------------------|-------------------------------------|
| Bloomberg-meddelelse         | ipm.externaldata.bloombergmessage* |
| CellTrust                 | ipm.externaldata.celltrust*        |
| Pivot                     | ipm.externaldata.pivot*            |
| WhatsApp Archiver         | ipm.externaldata.whatsapparchiver* |
|||

Værdier for egenskaben *elementklasse tager ikke* hensyn til store og små bogstaver. Generelt skal du bruge navnet på tredjepartsdatatypen (uden mellemrum) efterfulgt af et jokertegn (*).

Du kan finde flere oplysninger om oprettelse af eDiscovery-søgeforespørgsler under [Nøgleordsforespørgsler og søgebetingelser for eDiscovery](keyword-queries-and-search-conditions.md).

## <a name="data-connectors-in-the-us-government-cloud"></a>Dataforbindelser i den amerikanske regerings sky

Nogle dataforbindelser er tilgængelige i den amerikanske regerings sky. De følgende afsnit angiver de specifikke offentlige miljøer, der understøtter dataforbindelser fra tredjeparter. Du kan finde flere oplysninger om den amerikanske regerings skyer [i Microsoft 365 den amerikanske stat](/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/microsoft-365-government-how-to-buy).

### <a name="veritas-data-connectors-in-the-us-government-cloud-preview"></a>Veritas-dataforbindelser i den amerikanske Government-sky (forhåndsvisning)

|Dataforbindelse  |GCC  |GCC høj  |DoD  |
|:---------|:---------|:---------|:---------|
|CellTrust| Ja | Nej | Nej |
|Cisco Jabber på MS SQL| Ja | Nej | Nej |
|Cisco Jabber på Oracle| Ja | Nej | Nej |
|Cisco Jabber på PostgreSQL| Ja | Nej | Nej |
|EML| Ja | Nej | Nej |
|FX-Forbind| Ja | Nej | Nej |
|Jive| Ja | Nej | Nej |
|MS SQL Database| Ja | Nej | Nej |
|Pivot| Ja | Nej | Nej |
|Redtail Speak| Ja | Nej | Nej |
|Reuters Dealing| Ja | Nej | Nej |
|Reuters Eikon| Ja | Nej | Nej |
|Reuters FX| Ja | Nej | Nej |
|RingCentral| Ja | Nej | Nej |
|Salesforce Chatter| Ja | Nej | Nej |
|ServiceNow| Ja | Nej | Nej |
|Skype for Business| Ja | Nej | Nej |
|Slack eDiscovery| Ja | Nej | Nej |
|Ikke-for-store| Ja | Nej | Nej |
|Tekstsepareret| Ja | Nej | Nej |
|Twitter| Ja | Nej | Nej |
|Webex-Teams| Ja | Nej | Nej |
|Websider| Ja | Nej | Nej |
|Arbejdsplads fra Facebook| Ja | Nej | Nej |
|XIP| Ja | Nej | Nej |
|XSLT/XML| Ja | Nej | Nej |
|Afkastbroker| Ja | Nej | Nej |
|YouTube| Nej | Nej | Nej |
|Zoom møder| Ja | Nej | Nej |
|||||

### <a name="telemessage-data-connectors-in-the-us-government-cloud"></a>TeleMessage-dataforbindelser i den amerikanske regerings sky

|Dataforbindelse  |GCC  |GCC høj  |DoD  |
|:---------|:---------|:---------|:---------|
|Android-arkivering | Ja | Nej | Nej |
|AT&T SMS/MMS-netværksarkiver | Ja | Nej | Nej |
|Klokke-sms-/mms-netværksarkiver | Ja | Nej | Nej |
|Enterprise Number Archiver | Ja | Nej | Nej |
|O2-arkivering af sms og talenetværk | Ja         | Nej | Nej |
|Rogers Network Archiver | Ja         | Nej | Nej |
|Signalarkiver | Ja | Nej | Nej |
|Telegram Archiver | Ja | Nej | Nej |
|TELUS SMS Network Archiver | Ja | Nej | Nej |
|Verizon SMS/MMS Network Archiver | Ja | Nej | Nej |
|WeChat Archiver | Ja | Nej | Nej |
|WhatsApp Archiver | Ja | Nej | Nej |
|||||

### <a name="17a-4-data-connectors-in-the-us-government-cloud"></a>17a-4 dataforbindelser i den amerikanske regerings sky

|Dataforbindelse  |GCC  |GCC høj  |DoD  |
|:---------|:---------|:---------|:---------|
|BlackBerry DataParser | Ja | Nej | Nej |
|Bloomberg DataParser  | Ja | Nej | Nej |
|Cisco Jabber DataParser  | Ja | Nej | Nej |
|Cisco Webex DataParser  | Ja | Nej | Nej |
|FactSet DataParser  | Ja | Nej | Nej |
|Fuze DataParser  | Ja | Nej | Nej |
|FX Forbind DataParser  | Ja | Nej | Nej |
|ICE-dataparser  | Ja | Nej | Nej |
|InvestEdge DataParser  | Ja | Nej | Nej |
|LivePerson Conversational Cloud DataParser  | Ja | Nej | Nej |
|Quip DataParser  | Ja | Nej | Nej |
|Refinitiv Eikon Messenger DataParser  | Ja | Nej | Nej |
|ServiceNow DataParser  | Ja | Nej | Nej |
|Skype for Business Server DataParser | Ja | Nej | Nej |
|Slækdataparser | Ja | Nej | Nej |
|SQL DataParser  | Ja | Nej | Nej |
|Pattedataparser | Ja | Nej | Nej |
|ZoomDataParser | Ja | Nej | Nej |
|||||

### <a name="celltrust-data-connectors-in-the-us-government-cloud"></a>CellTrust-dataforbindelser i den amerikanske regerings sky

|Dataforbindelse  |GCC  |GCC høj  |DoD  |
|:---------|:---------|:---------|:---------|
|CellTrust SL2 | Ja | Nej | Nej |
|||||

## <a name="working-with-a-microsoft-partner-to-archive-third-party-data"></a>Arbejde sammen med en Microsoft-partner om at arkivere tredjepartsdata

En anden mulighed for at importere og arkivere tredjepartsdata er, at din organisation arbejder sammen med en Microsoft-partner. Hvis en tredjepartsdatatype ikke understøttes af de dataforbindelser, der er tilgængelige i Microsofts overholdelsescenter, kan du arbejde med en partner, der kan levere en brugerdefineret forbindelse, der konfigureres til at udtrække elementer fra tredjepartsdatakilden med jævne mellemrum og derefter oprette forbindelse til Microsoft-skyen med en tredjeparts-API og importere disse elementer til Microsoft 365. Partnerforbindelseskomponent konverterer også indholdet af et element fra tredjepartsdatakilden til en mail og importerer den derefter til en postkasse Microsoft 365.

Hvis du vil have en liste over partnere, du kan arbejde med, og den trinvise proces for denne metode, skal du se Arbejde sammen med en partner om at arkivere [tredjepartsdata i Microsoft 365](work-with-partner-to-archive-third-party-data.md).
