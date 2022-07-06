---
title: Forberedelse til TLS 1.2 i Office 365 og Office 365 GCC
description: Sådan forbereder du dig på at bruge TLS 1.2 til alle kombinationer af klient-server og browser-server i Office 365 og Office 365 GCC efter understøttelse af TLS 1.0 og 1.1 er deaktiveret.
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
ms.openlocfilehash: 9edbbb463d04447ee4babcd66b4d6e320663209a
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66639748"
---
# <a name="preparing-for-tls-12-in-office-365-and-office-365-gcc"></a>Forberedelse til TLS 1.2 i Office 365 og Office 365 GCC

## <a name="summary"></a>Oversigt

For at levere den bedste kryptering til vores kunder planlægger Microsoft at fraråde TLS version 1.0 og 1.1 i Office 365 og Office 365 GCC. Vi forstår, at sikkerheden for dine data er vigtig, og vi er forpligtet til gennemsigtighed om ændringer, der kan påvirke din brug af TLS-tjenesten.

[Microsoft TLS 1.0-implementeringen](https://support.microsoft.com/help/3117336/schannel-implementation-of-tls-1-0-in-windows-security-status-update-n) har ingen kendte sikkerhedsrisici. Men på grund af potentialet for fremtidige protokolnedgraderingsangreb og andre TLS-sårbarheder ophører vi med at understøtte TLS 1.0 og 1.1 i Microsoft Office 365 og Office 365 GCC.

Du kan finde oplysninger om, hvordan du fjerner TLS 1.0- og 1.1-afhængigheder, i følgende whitepaper: [Løsning af TLS 1.0-problemet](https://www.microsoft.com/download/details.aspx?id=55266).

Når du har opgraderet til TLS 1.2, skal du sørge for, at de krypteringspakker, du bruger, understøttes af Azure Front Door. Microsoft 365 og Azure Front Door har små forskelle i understøttelse af krypteringspakker. Du kan finde flere oplysninger under [Hvad understøttes de aktuelle krypteringspakker af Azure Front Door?](/azure/frontdoor/concept-end-to-end-tls#supported-cipher-suites).

## <a name="more-information"></a>Flere oplysninger

Vi er allerede begyndt udfasningen af TLS 1.0 og 1.1 fra og med januar 2020. Alle klienter, enheder eller tjenester, der opretter forbindelse til Office 365 via TLS 1.0 eller 1.1 i vores DoD- eller GCC High-forekomster, understøttes ikke. For vores kommercielle kunder med Office 365 begynder udfasningen af TLS 1.0 og 1.1. oktober 2020, og udrulningen fortsætter i løbet af de følgende uger og måneder.

Vi anbefaler, at alle kombinationer af klient/server og browser-server bruger TLS 1.2 (eller en nyere version) for at bevare forbindelsen til Office 365 tjenester. Du skal muligvis opdatere visse kombinationer af klient-server og browser-server.

  > [!NOTE]
  > I forbindelse med indgående SMTP-mailflow accepterer vi kun TLS 1.2-forbindelse efter udfasning af TLS 1.0 og 1.1. Vi fortsætter dog med at acceptere SMTP-forbindelsen, som ikke krypteres uden nogen TLS. Selvom vi ikke anbefaler overførsel af mail uden kryptering.

Du skal opdatere programmer, der kalder Microsoft 365 API'er via TLS 1.0 eller TLS 1.1, for at bruge TLS 1.2. .NET 4.5 er som standard TLS 1.1. Hvis du vil opdatere din .NET-konfiguration, skal du se [Sådan aktiverer du TLS 1.2 (Transport Layer Security) på klienter](/mem/configmgr/core/plan-design/security/enable-tls-1-2-client).

Følgende klienter kan ikke bruge TLS 1.2. Opdater disse klienter for at sikre uafbrudt adgang til tjenesten.

- Android 4.3 og tidligere versioner
- Firefox version 5.0 og tidligere versioner
- Internet Explorer 8-10 på Windows 7 og tidligere versioner
- Internet Explorer 10 på Windows Phone 8
- Safari 6.0.4/OS X10.8.4 og tidligere versioner

### <a name="tls-12-for-microsoft-teams-rooms-and-surface-hub"></a>TLS 1.2 til Microsoft Teams-rum og Surface Hub

Microsoft Teams-rum (tidligere kendt som Skype Room System V2 SRS V2) har understøttet TLS 1.2 siden december 2018. Vi anbefaler, at rumenheder har Microsoft Teams-rum appversion 4.0.64.0 eller nyere installeret. Du kan få flere oplysninger i [produktbemærkningerne](/microsoftteams/room-systems/srs2-release-note). Ændringerne er bagud- og fremadkompatible.

Surface Hub frigav TLS 1.2-support i maj 2019.

TLS 1.2-understøttelse af Microsoft Teams-rum- og Surface Hub-produkter kræver også følgende ændringer af serverkode:

- Skype for Business Online-serverændringer blev foretaget live i april 2019. Nu understøtter Skype for Business Online tilslutning af Microsoft Teams-rum- og Surface Hub-enheder ved hjælp af TLS 1.2.
- Skype for Business Server kunder skal installere en kumulativ opdatering (CU) for at bruge TLS 1.2 til Teams-rum Systemer og Surface Hub.

  - For Skype for Business Server 2015 er CU9 allerede udgivet i maj 2019.
  - For Skype for Business Server 2019 var CU1 tidligere planlagt til april 2019, men er udskudt til juni 2019.

  > [!NOTE]
  > Skype for Business kunder i det lokale miljø bør ikke deaktivere TLS 1.0/1.1, før de installerer bestemte CUs til Skype for Business Server.

Hvis du bruger en infrastruktur i det lokale miljø til hybride scenarier eller Active Directory Federation Services, skal du sørge for, at infrastrukturen kan understøtte både indgående og udgående forbindelser, der bruger TLS 1.2.

## <a name="references"></a>Referencer

Følgende ressourcer indeholder en vejledning til at sikre, at dine klienter bruger TLS 1.2 eller en nyere version og til at deaktivere TLS 1.0 og 1.1.

- For Windows 7-klienter, der opretter forbindelse til Office 365, skal du sørge for, at TLS 1.2 er standardsikker protokol i WinHTTP i Windows. Du kan få flere oplysninger under [KB 3140245 – Opdatering, der aktiverer TLS 1.1 og TLS 1.2 som standard sikre protokoller i WinHTTP i Windows](https://support.microsoft.com/help/3140245/update-to-enable-tls-1-1-and-tls-1-2-as-a-default-secure-protocols-in).
- [TLS-krypteringspakker, der understøttes af Office 365](/microsoft-365/compliance/technical-reference-details-about-encryption#tls-cipher-suites-supported-by-office-365)
- Hvis du vil begynde at håndtere svag TLS-brug ved at fjerne TLS 1.0- og 1.1-afhængigheder, skal [du se TLS 1.2-support hos Microsoft](https://cloudblogs.microsoft.com/microsoftsecure/2017/06/20/tls-1-2-support-at-microsoft/).
- [Ny IIS-funktionalitet](https://cloudblogs.microsoft.com/microsoftsecure/2017/09/07/new-iis-functionality-to-help-identify-weak-tls-usage/) gør det nemmere at finde klienter på [Windows Server 2012 R2](https://support.microsoft.com/help/4025335/windows-8-1-windows-server-2012-r2-update-kb4025335) og [Windows Server 2016](https://support.microsoft.com/help/4025334/windows-10-update-kb4025334) , der opretter forbindelse til tjenesten ved hjælp af svage sikkerhedsprotokoller.
- Få flere oplysninger om, hvordan du [løser TLS 1.0-problemet](https://www.microsoft.com/download/details.aspx?id=55266).
- Du kan få generelle oplysninger om vores tilgang til sikkerhed ved at gå til [Office 365 Center for sikkerhed og rettighedsadministration](https://www.microsoft.com/trustcenter/cloudservices/office365).
- Hvis du vil identificere den TLS-version, der bruges af SMTP-klienter, skal du se [indsigt og rapport for SMTP-godkendelsesklienter i Security & Compliance Center](../security/office-365-security/mfi-smtp-auth-clients-report.md).
- [Forberedelse til TLS 1.0/1.1 Udfasning – Office 365 Skype for Business](https://techcommunity.microsoft.com/t5/Skype-for-Business-Blog/Preparing-for-TLS-1-0-1-1-Deprecation-O365-Skype-for-Business/ba-p/222247)
- [Exchange Server TLS-vejledning, del 1: Klar til TLS 1.2](https://techcommunity.microsoft.com/t5/exchange-team-blog/exchange-server-tls-guidance-part-1-getting-ready-for-tls-1-2/ba-p/607649)
- [Exchange Server TLS-vejledning, del 2: Aktivering af TLS 1.2 og identificering af klienter, der ikke bruger den](https://techcommunity.microsoft.com/t5/exchange-team-blog/exchange-server-tls-guidance-part-2-enabling-tls-1-2-and/ba-p/607761)
- [Exchange Server TLS-vejledning, del 3: Deaktiver TLS 1.0/1.1](https://techcommunity.microsoft.com/t5/exchange-team-blog/exchange-server-tls-guidance-part-3-turning-off-tls-1-0-1-1/ba-p/607898)
- [Aktivér understøttelse af TLS 1.1 og TLS 1.2 i Office Online Server](/officeonlineserver/enable-tls-1-1-and-tls-1-2-support-in-office-online-server)
- [Aktivér understøttelse af TLS og SSL i SharePoint 2013](/sharepoint/security-for-sharepoint-server/enable-tls-and-ssl-support-in-sharepoint-2013)
- [Aktivér understøttelse af TLS 1.1 og TLS 1.2 i SharePoint Server 2016](/sharepoint/security-for-sharepoint-server/enable-tls-1-1-and-tls-1-2-support-in-sharepoint-server-2016)
- [Aktivér understøttelse af TLS 1.1 og TLS 1.2 i SharePoint Server 2019](/sharepoint/security-for-sharepoint-server/enable-tls-1-1-and-tls-1-2-support-in-sharepoint-server-2019)
