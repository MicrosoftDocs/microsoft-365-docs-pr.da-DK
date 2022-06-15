---
title: Gennemse afhjælpningshandlinger i Microsoft Defender til virksomheder
description: Få vist afhjælpninger, der blev udført på registrerede trusler med Defender for Business. Du kan få vist handlinger i Løsningscenter på Microsoft 365 Defender-portalen.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: how-to
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: 5c73b840b127770c4581dda4d03b3c95066df515
ms.sourcegitcommit: 66228a5506fdceb4cbf0d55b9de3f2943740134f
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/15/2022
ms.locfileid: "66089522"
---
# <a name="review-remediation-actions-in-the-action-center"></a>Gennemse afhjælpningshandlinger i Løsningscenter

I takt med at der registreres trusler, spiller afhjælpningshandlinger ind. Afhængigt af den specifikke trussel, og hvordan dine sikkerhedsindstillinger er konfigureret, kan afhjælpningshandlinger udføres automatisk eller kun efter godkendelse. Eksempler på afhjælpningshandlinger omfatter afsendelse af en fil til karantæne, stop af en proces i at køre og fjernelse af en planlagt opgave. Alle afhjælpningshandlinger spores i Løsningscenter.

:::image type="content" source="../../media/defender-business/mdb-actioncenter.png" alt-text="Skærmbillede af Løsningscenter":::

**I denne artikel beskrives**:

- [Sådan bruger du Løsningscenter](#how-to-use-the-action-center)
- [Afhjælpningshandlinger](#remediation-actions)


## <a name="how-to-use-the-action-center"></a>Sådan bruger du Løsningscenter

1. Gå til Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)), og log på.

2. Vælg **Løsningscenter** i navigationsruden.

3. Vælg fanen **Ventende** for at få vist og godkende (eller afvise) ventende handlinger. Sådanne handlinger kan opstå som følge af beskyttelse mod antivirus/antimalware, automatiserede undersøgelser, manuelle svaraktiviteter eller live-svarsessioner.

4. Vælg fanen **Oversigt** for at få vist en liste over fuldførte handlinger. 

## <a name="remediation-actions"></a>Afhjælpningshandlinger

Microsoft Defender til virksomheder omfatter flere afhjælpningshandlinger. Disse handlinger omfatter manuelle svarhandlinger, handlinger efter automatiseret undersøgelse og liveresponshandlinger.

I følgende tabel vises de afhjælpningshandlinger, der er tilgængelige:

| Kilde  | Handlinger  |
|---------|---------|
| [Automatiserede undersøgelser](../defender-endpoint/automated-investigations.md)      | - Sæt en fil i karantæne <br/>- Fjern en registreringsdatabasenøgle <br/>- Dræb en proces <br/>- Stop en tjeneste <br/>- Deaktiver en driver <br/>- Fjern en planlagt opgave        |
| [Handlinger for manuelt svar](../defender-endpoint/respond-machine-alerts.md)   | - Kør antivirusscanning <br/>- Isoler enhed <br/>- Stop og sæt karantæne <br/>– Tilføj en indikator for at blokere eller tillade en fil       |
| [Live-svar](../defender-endpoint/live-response.md)   | - Indsaml tekniske data <br/>- Analysér en fil <br/>- Kør et script <br/>- Send en mistænkelig enhed til Microsoft til analyse <br/>- Afhjælpning af en fil <br/>- Proaktiv jagt efter trusler         |

## <a name="next-steps"></a>Næste trin

- [Reagere på og afhjælpe trusler i Microsoft Defender til virksomheder](mdb-respond-mitigate-threats.md)
- [Administrer enheder i Microsoft Defender til virksomheder](mdb-manage-devices.md)