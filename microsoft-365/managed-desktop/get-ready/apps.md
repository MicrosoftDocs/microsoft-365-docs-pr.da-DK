---
title: Apps i Microsoft-administreret skrivebord
description: Beskriver, hvordan apps håndteres, herunder hvordan du pakker, installerer og understøtter dem.
keywords: Microsoft-administreret skrivebord, Microsoft 365, tjeneste, dokumentation
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
audience: Admin
ms.openlocfilehash: ce43080c284c4c15be5a8799f70a43de611ff9ba
ms.sourcegitcommit: cafca45069819a44c7cf8c67f6c1e105de1b3393
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/10/2022
ms.locfileid: "63588676"
---
# <a name="apps-in-microsoft-managed-desktop"></a>Apps i Microsoft-administreret skrivebord

<!--This topic is the target for 2 "Learn more" links in the Admin Portal (aka.ms/app-overview;app-package); also target for link from Online resources (aka.ms/app-overviewmmd-app-prep) do not delete.-->

<!--Applications: supported/onboard/deployment -->

## <a name="apps-generally"></a>Apps generelt

Microsoft inkluderer visse vigtige apps sammen med den Microsoft 365 E3 eller E5-licens, der er nødvendig for at deltage i Microsoft Managed Desktop. Men selvom vi leverer disse apps, har du stadig visse ansvarsområder og handlinger, der skal fuldføres.

Du kan også installere flere ikke-Microsoft-apps til dine brugere via selvbetjening via Firmaportal eller en påkrævet baggrundsinstallation ved hjælp af Microsoft Intune's installationspipeline.

## <a name="apps-provided-by-microsoft"></a>Apps leveret af Microsoft

Inkluderet med din Microsoft Managed Desktop-licens er 64-bit versioner af appsene i Microsoft 365 Apps for Enterprise Standard Suite (Word, Excel, PowerPoint, Outlook, Publisher, Access, Teams og OneNote).)

Klik og kør-versioner af Microsoft Project og Visio *ikke* som standard, men du kan anmode om, at de bliver tilføjet. Du kan finde flere oplysninger om disse apps under [Installér Microsoft Project eller Microsoft Visio på Microsoft-administrerede skrivebordsenheder](../get-started/project-visio.md).

### <a name="what-microsoft-does-to-support-the-apps-we-provide"></a>Hvad Microsoft gør for at understøtte de apps, vi leverer

Microsoft yder fuld service til udrulning, opdatering og support til de inkluderede Microsoft 365 Apps for enterprise apps. Klik og kør-versioner af Microsoft Project og Visio *ikke som* standard. Microsoft Managed Desktop indeholder dog installationsgrupper, som giver din it-administrator mulighed for at administrere licenser og installere disse programmer korrekt for organisationen. Microsoft vil understøtte brugere af disse programmer via supportkanalerne til Microsoft Managed Desktop.

### <a name="what-you-need-to-do-to-support-the-apps-we-provide"></a>Hvad du skal gøre for at understøtte de apps, vi leverer

Der er stadig visse ting, du skal gøre med disse apps:

| Opgave | Beskrivelse |
| ------ | ------ |
| Tildel licenser | Du er ansvarlig for at få og tildele de relevante licenser til brugere i Microsoft 365 Apps for enterprise. |
| Føj brugere til sikkerhedsgrupper | Hvis du bruger en Microsoft Project eller Visio, skal din it-administrator føje disse brugere til de relevante installationsgrupper. It-administratorer er også ansvarlige for at frigøre licenser fra disse brugere, hvis de forlader virksomheden. |
| Installere Microsoft 365-tilføjelsesprogrammet | Hvis du har brug for nogen tilføjelsesprogrammer til en af Microsoft 365 Apps for enterprise-appsene, kan du installere dem centralt som enhver Windows 32-app.

## <a name="apps-you-provide"></a>Apps, du angiver

Du har sikkert også andre apps, du skal bruge til dine forretningsaktiviteter. Disse apps kan kun installeres på Microsofts administrerede skrivebordsenheder ved hjælp Microsoft Intune din installationspipeline. Hvis du vil have mere at vide om programinstallation, skal du følge trinnene i [Installér apps på Microsoft-administrerede computerenheder](../get-started/deploy-apps.md).

### <a name="preparing-your-own-apps-for-inclusion-in-microsoft-managed-desktop"></a>Forberedelse af dine egne apps til inklusion i Microsoft Managed Desktop

Gennemse dine apps, tjek:

- Ingen af disse apps er forbudt eller har begrænset funktionsmåde, som beskrevet i [Microsoft Managed Desktop-appkrav](../service-description/mmd-app-requirements.md).
- Apps skal være klar til administration af Microsoft Intune. Du kan finde flere oplysninger [Windows 10 installation af apps ved Microsoft Intune og](/intune/apps-windows-10-app-deploy) [Føj apps Microsoft Intune](/intune/apps-add).
- Andre krav til forudemballering, f.eks. levering af licensnøgler, aftale med licensvilkår og forudindstilling af serverforbindelser.

## <a name="steps-to-get-ready-for-microsoft-managed-desktop"></a>Trin til at blive klar til Microsoft Managed Desktop

1. Gennemgå [forudsætninger for Microsoft Managed Desktop](prerequisites.md).
1. Kør værktøjer [til vurdering af parathed](readiness-assessment-tool.md).
1. Køb [Firmaportal](../get-started/company-portal.md).
1. Gennemgå [forudsætningerne for gæstekonti](guest-accounts.md).
1. Kontrollér [netværkskonfigurationen](network.md).
1. [Forberede certifikater og netværksprofiler](certs-wifi-lan.md).
1. [Forberede brugeradgang til data](authentication.md).
1. Forbered apps (denne artikel).
1. [Forbered tilknyttede drev](mapped-drives.md).
1. [Forberede udskrivningsressourcer](printing.md).
1. Navne [på adresseenhed](address-device-names.md).
