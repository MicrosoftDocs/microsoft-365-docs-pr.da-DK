---
title: Omdirigere konti fra Microsoft Defender for Endpoint til Microsoft 365 Defender
description: Sådan omdirigerer du konti og sessioner fra Defender for Endpoint for at Microsoft 365 Defender.
keywords: Microsoft 365 Defender, Introduktion til Microsoft 365 Defender, omdirigering af sikkerhedscenter
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
ms.custom: admindeeplinkDEFENDER
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: 64a9926253ea699fa6cc62d1ec2d80d07f25fd29
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/24/2022
ms.locfileid: "63592892"
---
# <a name="redirecting-accounts-from-microsoft-defender-for-endpoint-to-microsoft-365-defender"></a>Omdirigere konti fra Microsoft Defender for Endpoint til Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Gælder for:**
- Microsoft 365 Defender
- Defender til Slutpunkt

I overensstemmelse med Microsofts tilgang på tværs af domæner til trusselsbeskyttelse med SIEM og udvidet registrering og svar (XDR) har vi omdøbt Microsoft Defender Advanced Threat Protection som Microsoft Defender til slutpunkt og samlet det i en enkelt integreret portal: Microsoft 365 Defender.

Denne vejledning forklarer, hvordan du distribuerer konti til Microsoft 365 Defender ved at aktivere automatisk omdirigering fra den tidligere Microsoft Defender for Endpoint-portal (securitycenter.windows.com eller securitycenter.microsoft.com) <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">til Microsoft 365 Defender</a>.

> [!NOTE]
> Microsoft Defender til slutpunkt i Microsoft 365 Defender understøtter tildeling af adgang [](/windows/security/threat-protection/microsoft-defender-atp/grant-mssp-access) til administrerede sikkerhedstjenesteudbydere på samme måde som adgang [i Microsoft Defender Security Center](./mssp-access.md).

## <a name="what-to-expect"></a>Hvad du kan forvente

Når automatisk omdirigering er aktiveret, omdirigeres konti, der åbner den tidligere Microsoft Defender for Endpoint-portal på securitycenter.windows.com eller securitycenter.microsoft.com, automatisk til Microsoft 365 Defender-portalen <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank"><security.microsoft.com></a>.

Få mere at vide om, hvad der er ændret: [Microsoft Defender til slutpunkt Microsoft 365 Defender](microsoft-365-security-center-mde.md).

Dette omfatter omdirigering af direkte adgang til den tidligere portal via browser, herunder links, der peger mod den tidligere securitycenter.windows.com-portal – f.eks. links i mailmeddelelser og links, der returneres af SIEM API-opkald.  

 Eksterne links fra mailmeddelelser eller SIEM-API'er indeholder i øjeblikket links til begge portaler. Når omdirigering er aktiveret, peger begge links på det Microsoft 365 Defender indtil det gamle link er blevet fjernet. Vi opfordrer dig til at indføre det nye link, der peger på Microsoft 365 Defender.

Se tabellen nedenfor for at få mere at vide om links og routing.
## <a name="siem-api-routing"></a>ROUTING AF SIEM API

| Egenskab | Destination, når omdirigering er slået FRA | Destination, når omdirigering er til |
|---------|---------|---------|
| LinkToWDATP | Siden Besked i securitycenter.windows.com | Siden Besked i security.microsoft.com |
| IncidentLinkToWDATP | Hændelsesside i securitycenter.windows.com | Hændelsesside i security.microsoft.com |
| LinkToMTP | Siden Besked i security.microsoft.com | Siden Besked i security.microsoft.com |
| IncidentLinkToMTP | Hændelsesside i security.microsoft.com | Hændelsesside i security.microsoft.com |

## <a name="email-alert-notifications"></a>Beskeder via mail

| Egenskab | Destination, når omdirigering er SLÅET FRA** | Destination, når omdirigering er til |
|---------|---------|---------|
| Siden Besked | Siden Besked i securitycenter.windows.com | Siden Besked i security.microsoft.com |
| Hændelsesside |Hændelsesside i securitycenter.windows.com | Hændelsesside i security.microsoft.com |
| Siden besked i Defender for Cloud-portalen | Siden Besked i security.microsoft.com | Siden Besked i security.microsoft.com |
| Hændelsesside i Defender til skyportalen | Hændelsesside i security.microsoft.com | Hændelsesside i security.microsoft.com |

## <a name="when-does-this-take-effect"></a>Hvornår træder dette i kraft?

Når denne opdatering er aktiveret, træder den i kraft næsten med det samme for nogle konti. Men omdirigeringen kan tage længere tid at overført til alle konti i organisationen. Konti i aktive sessioner, mens denne indstilling anvendes, vil ikke blive tilføjet fra deres session og dirigeres kun til Microsoft 365 Defender, når deres aktuelle session er afsluttet og logger på igen.  

### <a name="set-up-portal-redirection"></a>Konfigurer portalomdirigering

Sådan startes routing af konti Microsoft 365 Defender:

1. Sørg for, at du er global administrator eller har sikkerhedsadministratortilladelser i Azure Active Directory.

2. Log på <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a>.

3. Gå til **Indstillinger** >  **EndpointsGeneralPortal** >  >  **redirection,** eller [klik her](https://security.microsoft.com/preferences2/portal_redirection).  

4. Slå indstillingen Automatisk omdirigering **Til.**

5. Klik **på Aktivér** for at anvende automatisk omdirigering Microsoft 365 Defender.

>[!IMPORTANT]
>Aktivering af denne indstilling afslutter ikke aktive brugersessioner. Konti, der er i en aktiv session, mens denne indstilling anvendes, vil kun blive omdirigeret til en Microsoft 365 Defender når de har afsluttet deres aktuelle session og logget på igen.

>[!NOTE]
>Du skal være global administrator eller have tilladelser som sikkerhedsadministrator i Azure Active Directory at aktivere eller deaktivere denne indstilling.  

## <a name="can-i-go-back-to-using-the-former-portal"></a>Kan jeg gå tilbage til at bruge den tidligere portal?

Hvis noget ikke fungerer for dig, eller hvis der er noget, du ikke kan fuldføre via Microsoft 365 Defender, vil vi gerne høre om det. Hvis du har haft problemer med omdirigering, opfordrer vi dig til at give os besked ved hjælp af indsendelsesformularen Giv feedback.

Sådan gendannes den tidligere Microsoft Defender for Endpoint-portal:

1. Log <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">på Microsoft 365 Defender som</a> global administrator eller ved hjælp af og konto med sikkerhedsadministratortilladelser i Azure Active Directory.

2. Naviger **til Indstillinger** >  **EndpointsGeneralPortal-omdirigering** >  > [, eller åbn siden her](https://security.microsoft.com/preferences2/portal_redirection).  

3. Slå indstillingen Automatisk omdirigering til **Fra**.

4. Klik på **Deaktiver** & del feedback, når du bliver bedt om det.

Denne indstilling kan aktiveres igen når som helst. 

Når det er deaktiveret, dirigeres konti ikke længere til security.microsoft.com, og du vil igen have adgang til den tidligere portal - securitycenter.windows.com eller securitycenter.microsoft.com. 

## <a name="related-information"></a>Relaterede oplysninger
- [Microsoft 365 Defender oversigt](microsoft-365-defender.md)
- [Microsoft Defender til slutpunkt i Microsoft 365 Defender](microsoft-365-security-center-mde.md)
- [Microsoft leverer samlet SIEM og XDR til at modernisere sikkerhedshandlinger](https://www.microsoft.com/security/blog/?p=91813) 
- [XDR versus SIEM infografik](https://afrait.com/blog/xdr-versus-siem/) 
- [`The New Defender`](https://afrait.com/blog/the-new-defender/) 
- [Om Microsoft 365 Defender](https://www.microsoft.com/microsoft-365/security/microsoft-365-defender) 
- [Microsoft-sikkerhedsportaler og -administrationscentre](portals.md)
