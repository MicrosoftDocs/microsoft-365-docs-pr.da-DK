---
title: Pilot af Microsoft Defender til slutpunkt
description: Få mere at vide om, hvordan du kører et pilotprojekt for Microsoft Defender for Endpoint(MDE), herunder bekræftelse af pilotgruppen og prøvefunktioner.
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
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 4fff094b06dfa265f9fc44c568216582083ce1d9
ms.sourcegitcommit: d32654bdfaf08de45715dd362a7d42199bdc1ee7
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/23/2022
ms.locfileid: "63755463"
---
# <a name="pilot-microsoft-defender-for-endpoint"></a>Pilot af Microsoft Defender til slutpunkt

Denne artikel guider dig i gang med at køre et pilotprojekt for Microsoft Defender til slutpunkt. 

Brug følgende trin til at konfigurere pilotprojektet for Microsoft Defender til slutpunkt. 

:::image type="content" source="../../media/defender/m365-defender-endpoint-pilot-steps.png" alt-text="Trinnene til at føje Microsoft Defender for Identity til Microsoft Defender-evalueringsmiljøet" lightbox="../../media/defender/m365-defender-endpoint-pilot-steps.png":::

- Trin 1. Bekræft pilotgruppe
- Trin 2. Prøv funktioner

Når du kører et pilotprojekt med Microsoft Defender til Slutpunkt, kan du vælge at onboarde et par enheder til tjenesten, før du tager telefonen.  

Du kan derefter prøve de tilgængelige funktioner, f.eks. at køre angrebssimulering, og se, hvordan Defender til Slutpunkt viser ondsindede aktiviteter og gør det muligt at udføre et effektivt svar. 

## <a name="step-1-verify-pilot-group"></a>Trin 1. Bekræft pilotgruppe
Når du har fuldført onboardingtrinnene beskrevet [](eval-defender-endpoint-enable-eval.md) i afsnittet Aktivér evaluering, bør du kunne se enhederne på listen Lager over enheder ca. efter en time. 

Når du ser dine onboardede enheder, kan du derefter fortsætte med at prøve funktionerne. 

## <a name="step-2-try-out-capabilities"></a>Trin 2. Prøv funktioner
Nu hvor du har færdiggjort onboarding af visse enheder og bekræftet, at de rapporterer til tjenesten, kan du lære produktet at kende ved at prøve de effektive funktioner, der er tilgængelige direkte fra start.

Under pilotprojektet kan du nemt komme i gang med at afprøve nogle af funktionerne for at se produktet i aktion uden at skulle igennem komplekse konfigurationstrin.

Lad os starte med at tjekke dashboards ud.

### <a name="view-the-device-inventory"></a>Få vist enhedens lager
Lagerlisten over enheder er det sted, hvor du får vist listen over slutpunkter, netværksenheder og IoT-enheder i dit netværk. Den giver dig ikke blot en oversigt over enhederne i dit netværk, men den giver også detaljerede oplysninger om dem, f.eks. domæne, risikoniveau, styresystemplatform og andre oplysninger, der gør det nemt at identificere de enheder, der er størst risiko for.

### <a name="view-the-threat-and-vulnerability-management-dashboard"></a>Få vist dashboardet Fortrudt håndtering af sikkerhedsrisici Dashboard 
Trussels- håndtering af sikkerhedsrisici hjælper dig med at fokusere på de mennesker, der udgør den mest presserende og den største risiko for organisationen. På dashboardet kan du få en oversigt over organisationens eksponeringsscore, Microsoft Secure Score for enheder, fordeling af enheds eksponering, de vigtigste sikkerhedsanbefalinger, mest sårbar software, vigtigste afhjælpningsaktiviteter og de mest eksponerede enhedsdata. 

### <a name="run-a-simulation"></a>Kør en simulering
Microsoft Defender til Slutpunkt leveres med [angrebsscenarier med "Gør det selv",](https://securitycenter.windows.com/tutorials) som du kan køre på dine pilotenheder.  Hvert dokument indeholder krav til operativsystem og program samt detaljerede instruktioner, der er specifikke for et angrebsscenarie. Disse scripts er sikre, dokumenterede og nemme at bruge. Disse scenarier afspejler Defender for Endpoint-egenskaber og hjælper dig gennem din undersøgelsesoplevelse.

Hvis du vil køre en af de angivne simuleringer, skal du bruge mindst [én onboardingenhed](../defender-endpoint/onboard-configure.md).

1. I **HjælpSimulationer** >  & du vælge, hvilke af de tilgængelige angrebsscenarier du gerne vil simulere:

   - **Scenarie 1: Dokument går ned i backdoor** – simulerer leveringen af et manipuleret dokument. Dokumentet starter en særligt udformet bagdoor, der giver hackere kontrol.

   - **Scenarie 2: PowerShell-script** i filløse angreb – simulerer et filløst angreb, der afhænger af PowerShell, showcasing attack surface reduction and device learning detection of malicious memory activity.

   - **Scenarie 3:** Automatiseret hændelsesrespons – udløser automatisk undersøgelse, som automatisk registrerer og afhjælper brudsakter for at skalere din kapacitet for hændelsesrespons.

2. Download og læs det tilhørende gennemgangsdokument, der leveres sammen med det valgte scenarie.

3. Download simuleringsfilen, eller kopiér simuleringsscriptet ved at navigere **til HelpSimulationer** >  & selvstudier. Du kan vælge at downloade filen eller scriptet på testenheden, men det er ikke obligatorisk.

4. Kør simuleringsfilen eller scriptet på testenheden som anvist i gennemgangsdokumentet.

> [!NOTE]
> Simuleringsfiler eller scripts efterligner angrebsaktivitet, men er faktisk bengalske og vil ikke skade eller kompromittere testenheden.

## <a name="next-steps"></a>Næste trin
[Evaluer Microsoft Defender til skyapps](eval-defender-mcas-overview.md)

Gå tilbage til oversigten for [Evaluer Microsoft Defender til slutpunkt](eval-defender-endpoint-overview.md)

Gå tilbage til oversigten for [Evaluer og Microsoft 365 Defender](eval-overview.md)
