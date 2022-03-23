---
title: Microsoft Edge
description: Beskriver, hvordan Microsoft Edge installeres og opdateres
keywords: browser, Microsoft Managed Desktop, Microsoft 365, tjeneste, dokumentation
ms.service: m365-md
author: tiaraquan
ms.author: tiaraquan
manager: dougeby
audience: ITpro
ms.topic: article
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.openlocfilehash: aab02ec260f0131ab32d28834152f50b84abce21
ms.sourcegitcommit: d4797cfc15c732f1a7ef21e4f944e672a7170f9a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/08/2022
ms.locfileid: "63590080"
---
# <a name="microsoft-edge"></a>Microsoft Edge

[Microsoft Edge](https://www.microsoft.com/edge) giver førsteklasses ydeevne og værdi med:

- Mere beskyttelse af personlige oplysninger og beskyttelse mod eksterne trusler.
- Mere produktivitet Hurtig adgang Office apps, filer, websteder og indbyggede Microsoft Søg.
- Problemfri oplevelse ved at synkronisere på tværs af dine enheder med understøttelse og profiler på tværs af platforme.

> [!IMPORTANT]
> Internet Explorer 11-programmet på computeren vil udgå og vil ikke længere have support den 15. juni 2022 (du kan se en liste over, hvad der er omfattet, i De ofte stillede [spørgsmål](https://techcommunity.microsoft.com/t5/windows-it-pro-blog/internet-explorer-11-desktop-app-retirement-faq/ba-p/2366549). De samme IE11-apps og -websteder, du bruger i dag, kan Microsoft Edge i Internet Explorer-tilstand. [Få mere at vide her](https://blogs.windows.com/windowsexperience/2021/05/19/the-future-of-internet-explorer-on-windows-10-is-in-microsoft-edge/).

## <a name="updates-to-microsoft-edge"></a>Opdateringer til Microsoft Edge

Microsoft Managed Desktop installerer den [udvidede stabile kanal af](/deployedge/microsoft-edge-channels#extended-stable-channel) Microsoft Edge, som automatisk opdateres hver ottende uge. Opdateringer på den udvidede stabile kanal rulles [gradvist](/deployedge/microsoft-edge-update-progressive-rollout) ud af Microsoft Edge-produktgruppen for at sikre den bedste oplevelse for kunderne.

[Beta-kanalen](/deployedge/microsoft-edge-channels#beta-channel) installeres på enheder i gruppen Test til repræsentativ validering i organisationen. Denne kanal understøttes fuldt ud og opdateres automatisk med nye funktioner ca. hver fjerde uge.

> [!IMPORTANT]
> For at sikre Microsoft Edge opdateringerne er korrekt, skal du ikke Microsoft Edge [politikkerne for opdatering](/deployedge/microsoft-edge-update-policies).

## <a name="settings-managed-by-microsoft-managed-desktop"></a>Indstillinger administreret af Microsoft Managed Desktop

Microsoft Managed Desktop har oprettet et standardsæt af politikker for Microsoft Edge at sikre browseren. Standardbrowserindstillingerne er som følger:

### <a name="microsoft-edge-extensions"></a>Microsoft Edge filtypenavne

Grundlinjen sikkerhed for brugere Microsoft Edge Microsoft Managed Desktop-enheder angiver to politikker for at deaktivere alle Chrome-udvidelser og sikre brugere. Hvis du vil aktivere og installere udvidelser i dit miljø, skal [Indstillinger du administrerer](#settings-you-manage).

| Indstilling | Standardværdi | Beskrivelse |
| ------ | ------ | ------ |
| Installationsblokliste for udvidelse | Alle | Microsofts administrerede skrivebord indstiller denne politik for at forhindre Chrome-udvidelser i at blive installeret på administrerede slutpunkter. Der er kendte risici forbundet med Chromium, herunder beskyttelse mod datatab, beskyttelse af personlige oplysninger og andre risici, der kan kompromittere enheder. |
| Tillad lokale meddelelsesværter på brugerniveau (installeret uden administratortilladelser) | Deaktiveret | Ved at deaktivere denne politik vil Microsoft Edge kun bruge oprindelige meddelelsesværter, der er installeret på systemniveau. Native messaging hosts are a part of Chrome extensions, which allow for the browser to interact with other parts of user's endpoint, creating various security concerns. |

### <a name="secure-sockets-layer-tlsssl"></a>Secure Sockets Layer (TLS/SSL)

| Indstilling | Standardværdi | Beskrivelse
| ------ | ------ | ------ |
| Minimumversion af TLS | Minimum TLS 1.2 understøttes | Hvis du vil bruge den mindre sikre TLS 1.1, kan du arkivere en anmodning om at gøre det. |
| Tillad brugere at fortsætte fra SSL-advarselssiden | Deaktiveret | Vi anbefaler ikke, at du aktiverer denne indstilling, da den giver brugerne mulighed for at besøge websteder med TSL-fejl. |

### <a name="microsoft-defender-smartscreen"></a>Microsoft Defender SmartScreen

| Indstilling | Standardværdi | Beskrivelse
| ------ | ------ | ------ |
| Konfigurere Windows Defender SmartScreen | Aktiveret | Er som standard aktiveret for at beskytte brugerne. |
| Windows Defender SmartScreen-prompter for websteder | Aktiveret | Vi anbefaler ikke deaktivering af denne indstilling, da det ville tillade brugere at ignorere advarsler og fortsætte med potentielt skadelige websteder. |
| Undgå at ignorere Windows Defender SmartScreen-advarsler om downloads | Aktiveret | Vi anbefaler ikke at deaktivere denne indstilling, da det ville give brugerne mulighed for at ignorere advarsler og fuldføre ikke-fuldførte downloads. |

### <a name="adobe-flash"></a>Adobe Flash

| Indstilling | Standardværdi | Beskrivelse
| ------ | ------ | ------ |
| Standardindstilling for Adobe Flash | Deaktiveret | Vi anbefaler ikke at bruge Flash på grund af tilknyttede sikkerhedsrisici. <br><br> Hvis du stadig har processer, der afhænger af Flash, skal du angive politikken **[PluginsAllowedForUrls](/deployedge/microsoft-edge-policies#pluginsallowedforurls)** for at aktivere Flash for websteder, der har brug for det. Hvis du ikke kan vedligeholde en liste over websteder, der er tilladt at bruge Flash, kan du arkivere en ændringsanmodning for at ændre værdien til Klik og afspil **, hvilket** giver brugerne mulighed for at vælge, hvornår det er relevant at køre Flash. |

### <a name="password-manager"></a>Adgangskodestyring

| Indstilling | Standardværdi | Beskrivelse
| ------ | ------ | ------ |
| Aktivér lagring af adgangskoder til adgangskodestyring | Deaktiveret | Adgangskodestyring er som standard deaktiveret. Hvis du vil have denne funktion aktiveret, kan du arkivere en supportanmodning, så kan vores serviceteknikere aktivere indstillingen i dit miljø. |

### <a name="internet-explorer-mode-in-microsoft-edge"></a>Internet Explorer-tilstand i Microsoft Edge

IE-tilstand på Microsoft Edge gør det nemt at bruge alle de websteder, din organisation har brug for, i en enkelt browser. Den anvender det integrerede Chromium til websteder, der er kompatible med Chromium-gengivelsesprogrammet. Microsoft Edge bruger programmet Udryk MSHTML fra Internet Explorer 11 (IE11) til websteder, der ikke er eller er afhængige af IE-funktionalitet. [Få mere at vide](/DeployEdge/edge-ie-mode)

Microsoft Managed Desktop aktiverer Internet Explorer-tilstand for dine enheder som standard.

| Indstilling | Standardværdi | Beskrivelse
| ------ | ------ | ------ |
| Integration af Internet Explorer-tilstand | Internet Explorer tilstand | Enheder er som standard indstillet til at bruge Internet Explorer-tilstand, men du kan indstille dem til at åbne websteder i et separat Internet Explorer 11-vindue i stedet. Du kan ændre denne funktionsmåde ved at arkivere en supportanmodning. |
| Føje websteder til listen over virksomhedswebsteder i virksomhedstilstand | Se beskrivelse | For at websteder kan åbnes i Internet Explorer-tilstand, skal du medtage dem på [listen virksomhedswebsted](/DeployEdge/edge-ie-mode-sitelist). Det er dit ansvar at vedligeholde og implementere enterprise-webstedslisten. Du kan få mere at [vide under Konfigurere ved hjælp af politikken Konfigurer webstedslistepolitik for virksomhedstilstand](/DeployEdge/edge-ie-mode-policies#configure-using-the-configure-the-enterprise-mode-site-list-policy). |

### <a name="other-settings"></a>Andre indstillinger

| Indstilling | Standardværdi | Beskrivelse
| ------ | ------ | ------ |
| Aktivere webstedsisolation for hvert websted | Aktiveret | Når denne politik er aktiveret, kan brugerne ikke fravælge standardfunktionsmåden, som hvert websted kører i sin egen proces. |
| Understøttede godkendelsessystemer | NTLM, forhandl | Microsoft Managed Desktop understøtter ikke grundlæggende godkendelsessystemer eller oversigtsgodkendelsessystemer. |
| Importér automatisk en anden browsers data og indstillinger ved første kørsel | Importér automatisk alle understøttede datatyper og indstillinger fra standardbrowseren. | Når denne politik er anvendt, springer Første kørsel-oplevelsen importsektionen over, hvilket minimerer brugerinteraktion. Browserdata fra ældre versioner af Microsoft Edge overføres altid automatisk ved første kørsel, uanset denne indstilling. |

## <a name="settings-you-manage"></a>Indstillinger du administrerer

Du kan installere alle Microsoft Edge, der ikke er beskrevet tidligere, ved hjælp af profilen for administrative skabeloner Microsoft Intune. Du kan finde flere [oplysninger i Microsoft Edge konfigurere politikindstillinger med Microsoft Intune](/deployedge/configure-edge-with-intune). Hvis du vil evaluere en politik, der i øjeblikket ikke findes i de administrative Microsoft Edge i Intune, kan du bruge brugerdefinerede indstillinger til Windows 10 enheder i Intune.

| Indstilling | Beskrivelse
| ------ | ------ |
| Aktivér bestemte Chrome-udvidelser | Administrationsskabelonen giver mulighed for at installere bestemte Chrome-udvidelser med Microsoft Intune. Du kan finde den i **Computerkonfiguration > Microsoft Edge >-> Tillade, at bestemte udvidelser installeres**. |
| Installer udvidelser automatisk | Du kan også bruge den administrative skabelon til at angive Microsoft Edge at installere udvidelser uden at give brugeren besked. Du kan finde den i **Computerkonfiguration > Microsoft Edge > Udvidelser > at kontrollere, hvilke udvidelser der installeres automatisk**. |
| Microsoft Edge opdateringspolitikker | For at sikre Microsoft Edge opdateringerne er korrekt, skal du ikke Microsoft Edge [politikkerne for opdatering](/deployedge/microsoft-edge-update-policies). |
| Andre almindelige virksomhedspolitikker | Microsoft Edge tilbyder mange andre politikker. Følgende er nogle af de mest almindelige: <ul> <li> [Konfigurere websteder på listen over virksomhedswebsteder og IE-tilstand](/deployedge/edge-ie-mode-sitelist)</li><li> [Konfigurere indstillinger for start, startside og ny fane](/deployedge/microsoft-edge-policies#startup-home-page-and-new-tab-page)</li> <li> [Konfigurer indstillinger for Surf-spil](/deployedge/microsoft-edge-policies#allowsurfgame)</li> <li> [Konfigurere indstillinger for proxyserver](/deployedge/microsoft-edge-policies#proxy-server)</li></ul>
