---
title: Forberedelse til TLS 1.2 i Office 365 og Office 365 GCC
description: Sådan forberedes du til at bruge TLS 1.2 til alle klientserver- og browserserverkombinationer i Office 365 og Office 365 GCC, når understøttelse af TLS 1.0 og 1.1 er deaktiveret.
author: kccross
manager: laurawi
ms.localizationpriority: medium
search.appverid:
- MET150
audience: ITPro
ms.service: O365-seccomp
ms.topic: article
ms.author: shmehta
ms.reviewer: krowley
appliesto:
- Office 365 Business
ms.openlocfilehash: d2562e52c307fcf251b0b3030219aca68dc96a0a
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/09/2021
ms.locfileid: "63588246"
---
# <a name="preparing-for-tls-12-in-office-365-and-office-365-gcc"></a>Forberedelse til TLS 1.2 i Office 365 og Office 365 GCC

## <a name="summary"></a>Oversigt

For at levere den bedste kryptering i klassen til vores kunder, planlægger Microsoft at fraråde TLS-versionerne (Transport Layer Security) 1.0 og 1.1 i Office 365 og Office 365 GCC. Vi forstår, at sikkerheden for dine data er vigtig, og vi er forpligtet til gennemsigtighed om ændringer, der kan påvirke din brug af TLS-tjenesten.

Microsoft [TLS 1.0-implementeringen har](https://support.microsoft.com/help/3117336/schannel-implementation-of-tls-1-0-in-windows-security-status-update-n) ingen kendte sikkerhedsrisici. Men på grund af mulighederne for fremtidige protokolnedgraderingsangreb og andre TLS-sårbarheder ophører vi med at understøtte TLS 1.0 og 1.1 i Microsoft Office 365 og Office 365 GCC.

For information about how to remove TLS 1.0 and 1.1 dependencies, see the following white paper: [Solving the TLS 1.0 problem](https://www.microsoft.com/download/details.aspx?id=55266).

Når du har opgraderet til TLS 1.2, skal du sørge for, at de krypterede pakker, du bruger, understøttes af Azure Front Door. Microsoft 365 og Azure Front Door har små forskelle i understøttelse af cipher-pakken. Du kan få mere [at vide under Hvad understøttes de aktuelle krypteringspakker af Azure Front Door?](/azure/frontdoor/front-door-faq#what-are-the-current-cipher-suites-supported-by-azure-front-door-).

## <a name="more-information"></a>Flere oplysninger

Vi er allerede begyndt at udråde TLS 1.0 og 1.1 pr. januar 2020. Klienter, enheder eller tjenester, der har forbindelse til Office 365 via TLS 1.0 eller 1.1 i vores DoD- eller GCC High-forekomster, understøttes ikke. For vores kommercielle kunder til Office 365 begynder udrådningen af TLS 1.0 og 1.1 d. 15. oktober 2020, og udrulningen fortsætter i løbet af de følgende uger og måneder.

Vi anbefaler, at alle kombinationer af klientserver og browserserver bruger TLS 1.2 (eller en nyere version) for at bevare forbindelsen til Office 365-tjenester. Du skal muligvis opdatere visse kombinationer af klientserver og browserserver.

  > [!NOTE]
  > For SMTP-indgående mailflow accepterer vi kun TLS 1.2-forbindelse efter udrådningen af TLS 1.0 og 1.1. Vi fortsætter dog med at acceptere SMTP-forbindelse, som er ikke-krypteret uden nogen TLS. Selvom vi ikke anbefaler mailoverførsel uden kryptering. 

Du skal opdatere programmer, der kalder Microsoft 365 API'er over TLS 1.0 eller TLS 1.1 for at bruge TLS 1.2. .NET 4.5 bruger som standard TLS 1.1. Hvis du vil opdatere din .NET-konfiguration, skal du se Sådan aktiveres [TLS 1.2 (Transport Layer Security) på klienter](/mem/configmgr/core/plan-design/security/enable-tls-1-2-client).

Det er kendt, at følgende klienter ikke kan bruge TLS 1.2. Opdater disse klienter for at sikre uafbrudt adgang til tjenesten.

- Android 4.3 og tidligere versioner
- Firefox version 5.0 og tidligere versioner
- Internet Explorer 8-10 på Windows 7 og tidligere versioner
- Internet Explorer 10 på Windows Phone 8
- Safari 6.0.4/OS X10.8.4 og tidligere versioner

### <a name="tls-12-for-microsoft-teams-rooms-and-surface-hub"></a>TLS 1.2 til Microsoft Teams-rum og Surface Hub

Microsoft Teams-rum (tidligere kendt som Skype Room System V2 SRS V2) har understøttet TLS 1.2 siden december 2018. Vi anbefaler, at rumenheder Microsoft Teams-rum version 4.0.64.0 eller nyere installeret. Du kan finde flere oplysninger i [Produktbemærkninger](/microsoftteams/room-systems/srs2-release-note). Ændringerne er bagud- og fremadkompatible.

Surface Hub TLS 1.2-understøttelse i maj 2019.

Understøttelse af TLS 1.2 Microsoft Teams-rum-Surface Hub-produkter kræver også følgende ændringer af serversiden:

- Skype for Business onlineserverændringer blev foretaget live i april 2019. Nu understøtter Skype for Business Online tilslutning Microsoft Teams-rum og Surface Hub-enheder ved hjælp af TLS 1.2.
- Skype for Business Server kunder skal installere en akkumuleret opdatering (CU) for at bruge TLS 1.2 til Teams-rum-systemer og Surface Hub.

  - I Skype for Business Server 2015 er CU9 allerede frigivet i maj 2019.
  - I Skype for Business Server 2019 var CU1 tidligere planlagt til april 2019, men er forsinket til juni 2019.

  > [!NOTE]
  > Skype for Business lokale kunder bør ikke deaktivere TLS 1.0/1.1, før de installerer bestemte CUs til Skype for Business Server.

Hvis du bruger en lokal infrastruktur til hybridscenarier eller Active Directory Federation Services, skal du sørge for, at infrastrukturen understøtter både indgående og udgående forbindelser, der bruger TLS 1.2.

## <a name="references"></a>Referencer

Følgende ressourcer indeholder en vejledning til at sikre, at dine kunder bruger TLS 1.2 eller en nyere version og til at deaktivere TLS 1.0 og 1.1.

- For Windows 7 klienter, der opretter forbindelse til Office 365, skal du sørge for, at TLS 1.2 er den sikre standardprotokol i Winhttp Windows. Du kan finde flere oplysninger [i KB 3140245 – Opdater for at aktivere TLS 1.1 og TLS 1.2](https://support.microsoft.com/help/3140245/update-to-enable-tls-1-1-and-tls-1-2-as-a-default-secure-protocols-in) som en sikker standardprotokoller i WinHTTP Windows.
- [TLS-krypteringspakker, der understøttes af Office 365](/microsoft-365/compliance/technical-reference-details-about-encryption#tls-cipher-suites-supported-by-office-365)
- Hvis du vil begynde at adressere svag brug af TLS ved at fjerne afhængigheder af TLS 1.0 og 1.1, skal du se [understøttelse af TLS 1.2 hos Microsoft](https://cloudblogs.microsoft.com/microsoftsecure/2017/06/20/tls-1-2-support-at-microsoft/).
- [Den nye IIS-funktionalitet](https://cloudblogs.microsoft.com/microsoftsecure/2017/09/07/new-iis-functionality-to-help-identify-weak-tls-usage/) gør det nemmere at finde klienter på [Windows Server 2012 R2](https://support.microsoft.com/help/4025335/windows-8-1-windows-server-2012-r2-update-kb4025335) og [Windows Server 2016](https://support.microsoft.com/help/4025334/windows-10-update-kb4025334), der opretter forbindelse til tjenesten ved hjælp af svage sikkerhedsprotokoller.
- Få mere at vide om, [hvordan du løser problemet TLS 1.0](https://www.microsoft.com/download/details.aspx?id=55266).
- Du kan finde generelle oplysninger om vores tilgang til sikkerhed i [Office 365 Center for sikkerhed og sikkerhed](https://www.microsoft.com/trustcenter/cloudservices/office365).
- Du kan finde oplysninger om den TLS-version, der bruges af SMTP-klienter, ved at se indsigt og rapport fra [SMTP-klienter i Security & Compliance Center](../security/office-365-security/mfi-smtp-auth-clients-report.md).
- [Forberedelse til udrådning af TLS 1.0/1.1 – Office 365 Skype for Business](https://techcommunity.microsoft.com/t5/Skype-for-Business-Blog/Preparing-for-TLS-1-0-1-1-Deprecation-O365-Skype-for-Business/ba-p/222247)
- [Exchange Server TLS-vejledning, del 1: Blive klar til TLS 1.2](https://techcommunity.microsoft.com/t5/exchange-team-blog/exchange-server-tls-guidance-part-1-getting-ready-for-tls-1-2/ba-p/607649)
- [Exchange Server TLS-vejledning Del 2: Aktivering af TLS 1.2 og identificering af klienter, der ikke bruger det](https://techcommunity.microsoft.com/t5/exchange-team-blog/exchange-server-tls-guidance-part-2-enabling-tls-1-2-and/ba-p/607761)
- [Exchange Server TLS-vejledning Del 3: De slår TLS 1.0/1.1 fra](https://techcommunity.microsoft.com/t5/exchange-team-blog/exchange-server-tls-guidance-part-3-turning-off-tls-1-0-1-1/ba-p/607898)
- [Aktivér understøttelse af TLS 1.1 og TLS 1.2 Office Online Server](/officeonlineserver/enable-tls-1-1-and-tls-1-2-support-in-office-online-server)
- [Aktivér understøttelse af TLS og SSL SharePoint 2013](/sharepoint/security-for-sharepoint-server/enable-tls-and-ssl-support-in-sharepoint-2013)
- [Aktivér understøttelse af TLS 1.1 og TLS 1.2 SharePoint Server 2016](/sharepoint/security-for-sharepoint-server/enable-tls-1-1-and-tls-1-2-support-in-sharepoint-server-2016)
- [Aktivér understøttelse af TLS 1.1 og TLS 1.2 SharePoint Server 2019](/sharepoint/security-for-sharepoint-server/enable-tls-1-1-and-tls-1-2-support-in-sharepoint-server-2019)
