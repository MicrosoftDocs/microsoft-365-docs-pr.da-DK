---
title: Gennemse afhjælpningshandlinger i Microsoft 365 Business Premium
description: Se, hvordan du får vist afhjælpninger, der er taget automatisk, eller som afventer godkendelse, i Løsningscenter.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: how-to
ms.service: o365-administration
ms.localizationpriority: high
ms.date: 07/19/2022
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: 847095a4dcfb1905cf3c95b9cbf393298b1c7c3d
ms.sourcegitcommit: c1eaea74c8ffce2f9f477c9469342e88e4a70c14
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/20/2022
ms.locfileid: "66894487"
---
# <a name="review-remediation-actions-in-microsoft-365-business-premium"></a>Gennemse afhjælpningshandlinger i Microsoft 365 Business Premium

Okay, du har opdaget et sikkerhedsbrud, men hvad gør du? Det afhænger af arten af det.

Eksempler på afhjælpningshandlinger omfatter afsendelse af en fil for at sætte en fil i karantæne, forhindre en proces i at køre eller helt fjerne en planlagt opgave. Alle afhjælpningshandlinger spores i Løsningscenter, som er placeret på [https://security.microsoft.com/action-center](https://security.microsoft.com/action-center).

:::image type="content" source="../media/defender-business/mdb-actioncenter.png" alt-text="Skærmbillede af Løsningscenter i M365.":::

**I denne artikel beskrives**:

- [Sådan bruger du Løsningscenter](#how-to-use-your-action-center).
- [Typer af afhjælpningshandlinger](#types-of-remediation-actions).


## <a name="how-to-use-your-action-center"></a>Sådan bruger du dit Løsningscenter

1. Gå til Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)), og log på.

2. Vælg **Løsningscenter** i navigationsruden.

3. Vælg fanen **Ventende** for at få vist og godkende (eller afvise) ventende handlinger. Sådanne handlinger kan opstå som følge af beskyttelse mod antivirus/antimalware, automatiserede undersøgelser, manuelle svaraktiviteter eller live-svarsessioner.

4. Vælg fanen **Oversigt** for at få vist en liste over fuldførte handlinger.

## <a name="types-of-remediation-actions"></a>Typer af afhjælpningshandlinger

Dit abonnement indeholder flere forskellige typer afhjælpningshandlinger for registrerede trusler. Disse handlinger omfatter manuelle svarhandlinger, handlinger efter automatiseret undersøgelse og liveresponshandlinger.

I følgende tabel vises de afhjælpningshandlinger, der er tilgængelige:

| Kilde  | Handlinger  |
|---------|---------|
| [Automatiserede undersøgelser](../security/defender-endpoint/automated-investigations.md)      | - Sæt en fil i karantæne <br/>- Fjern en registreringsdatabasenøgle <br/>- Dræb en proces <br/>- Stop en tjeneste <br/>- Deaktiver en driver <br/>- Fjern en planlagt opgave        |
| [Handlinger for manuelt svar](../security/defender-endpoint/respond-machine-alerts.md)   | - Kør antivirusscanning <br/>- Isoler enhed <br/>- Stop og sæt karantæne <br/>– Tilføj en indikator for at blokere eller tillade en fil       |
| [Live-svar](../security/defender-endpoint/live-response.md)   | - Indsaml tekniske data <br/>- Analysér en fil <br/>- Kør et script <br/>- Send en mistænkelig enhed til Microsoft til analyse <br/>- Afhjælpning af en fil <br/>- Proaktiv jagt efter trusler         |
