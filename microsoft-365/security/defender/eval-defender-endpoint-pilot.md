---
title: Pilot Microsoft Defender for Endpoint
description: Få mere at vide om, hvordan du kører et pilotprojekt for Microsoft Defender for Endpoint(MDE), herunder bekræftelse af pilotgruppen og afprøver funktioner.
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: v-jweston
author: jweston-1
ms.date: 07/09/2021
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
- m365solution-evalutatemtp
- zerotrust-solution
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: c12d1bca36884a7b43580b0685f38df99e51ba1d
ms.sourcegitcommit: 61b22df76e0f81e5ef11c587b129287886151c79
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/12/2022
ms.locfileid: "66750401"
---
# <a name="pilot-microsoft-defender-for-endpoint"></a>Pilot Microsoft Defender for Endpoint

Denne artikel hjælper dig i gang med at køre et pilotprojekt for Microsoft Defender for Endpoint. 

Brug følgende trin til at konfigurere pilotprojektet til Microsoft Defender for Endpoint. 

:::image type="content" source="../../media/defender/m365-defender-endpoint-pilot-steps.png" alt-text="Trinnene til tilføjelse af Microsoft Defender for Identity til Microsoft Defender-evalueringsmiljøet" lightbox="../../media/defender/m365-defender-endpoint-pilot-steps.png":::

- Trin 1. Bekræft pilotgruppe
- Trin 2. Prøv funktioner

Når du styrer Microsoft Defender for Endpoint, kan du vælge at onboarde nogle få enheder til tjenesten, før du onboarder hele organisationen.  

Du kan derefter afprøve funktioner, der er tilgængelige, f.eks. kørsel af angrebssimuleringer og se, hvordan Defender for Endpoint viser skadelige aktiviteter og giver dig mulighed for at udføre et effektivt svar. 

## <a name="step-1-verify-pilot-group"></a>Trin 1. Bekræft pilotgruppe
Når du har fuldført de onboardingtrin, der er beskrevet i afsnittet [Aktivér evaluering](eval-defender-endpoint-enable-eval.md) , kan du se enhederne på listen Over enheder ca. efter en time. 

Når du ser dine onboardede enheder, kan du fortsætte med at afprøve funktioner. 

## <a name="step-2-try-out-capabilities"></a>Trin 2. Prøv funktioner
Nu, hvor du er færdig med at onboarde nogle enheder og bekræftet, at de rapporterer til tjenesten, kan du blive fortrolig med produktet ved at afprøve de effektive funktioner, der er tilgængelige lige fra starten.

Under pilotprojektet kan du nemt komme i gang med at afprøve nogle af funktionerne for at se produktet i aktion uden at gennemgå komplekse konfigurationstrin.

Lad os starte med at tjekke dashboards ud.

### <a name="view-the-device-inventory"></a>Få vist enhedslageret
Enhedsoversigten er stedet, hvor du kan se en liste over slutpunkter, netværksenheder og IoT-enheder på dit netværk. Den giver dig ikke blot en visning af enhederne i dit netværk, den giver også detaljerede oplysninger om dem, f.eks. domæne, risikoniveau, OS-platform og andre oplysninger, så du nemt kan identificere de enheder, der er mest udsatte.

### <a name="view-the-threat-and-vulnerability-management-dashboard"></a>Få vist dashboardet trussels- og sårbarhedsstyring 
Trussels- og sårbarhedsstyring hjælper dig med at fokusere på de svagheder, der udgør den mest presserende og højeste risiko for organisationen. Fra dashboardet kan du få en overordnet visning af organisationens eksponeringsscore, Microsoft Secure Score for Devices, distribution af enhedseksponering, topsikkerhedsanbefalinger, top sårbar software, topafhjælpningsaktiviteter og topeksponerede enhedsdata. 

### <a name="run-a-simulation"></a>Kør en simulering
Microsoft Defender for Endpoint leveres med ["Gør det selv"-angrebsscenarier](https://securitycenter.windows.com/tutorials), som du kan køre på dine pilotenheder.  Hvert dokument indeholder krav til operativsystem og program samt detaljerede instruktioner, der er specifikke for et angrebsscenarie. Disse scripts er sikre, dokumenterede og nemme at bruge. Disse scenarier afspejler funktionerne i Defender for Endpoint og fører dig gennem undersøgelsesoplevelsen.

Hvis du vil køre en af de angivne simuleringer, skal du bruge mindst [én onboardet enhed](../defender-endpoint/onboard-configure.md).

1. I **Hjælp-simuleringer** >  & selvstudier skal du vælge, hvilke af de tilgængelige **angrebsscenarier** du vil simulere:

   - **Scenarie 1: Dokumentet falder bagdør** – simulerer levering af et dokument med socialt manipulerede lokker. Dokumentet starter en særligt udformet bagdør, der giver angribere kontrol.

   - **Scenarie 2: PowerShell-script i et filløst angreb** – simulerer et filuafhængigt angreb, der er baseret på PowerShell, og viser reduktion af angrebsoverfladen og registrering af enhedslæring for skadelig hukommelsesaktivitet.

   - **Scenarie 3: Automatiseret svar på hændelser** – udløser automatiseret undersøgelse, som automatisk søger efter og afhjælper brudartefakter for at skalere din kapacitet til svar på hændelser.

2. Download og læs det tilsvarende gennemgangsdokument, der følger med det valgte scenarie.

3. Download simuleringsfilen, eller kopiér simuleringsscriptet ved at gå til **Hjælp-simuleringer** >  & selvstudier. Du kan vælge at downloade filen eller scriptet på testenheden, men det er ikke obligatorisk.

4. Kør simuleringsfilen eller scriptet på testenheden som beskrevet i gennemgangsdokumentet.

> [!NOTE]
> Simuleringsfiler eller scripts efterligner angrebsaktivitet, men er faktisk godartede og vil ikke skade eller kompromittere testenheden.

## <a name="next-steps"></a>Næste trin
[Evaluer Microsoft Defender for Cloud Apps](eval-defender-mcas-overview.md)

Vend tilbage til oversigten for [Evaluate Microsoft Defender for Endpoint](eval-defender-endpoint-overview.md)

Vend tilbage til oversigten for [Evaluate og pilot Microsoft 365 Defender](eval-overview.md)
