---
title: Gennemse afhjælpningshandlinger i Microsoft Defender til virksomheder
description: Vis afhjælpninger, der er taget automatisk, eller som afventer godkendelse i Løsningscenter
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: how-to
ms.date: 04/12/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: 15a64491f6e97137d1e919aa126d4bf134c47999
ms.sourcegitcommit: e3bc6563037bd2cce2abf108b3d1bcc2ccf538f6
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/15/2022
ms.locfileid: "64862208"
---
# <a name="review-remediation-actions-in-the-action-center"></a>Gennemse afhjælpningshandlinger i Løsningscenter

> [!NOTE]
> Microsoft Defender til virksomheder er nu inkluderet i [Microsoft 365 Business Premium](../../business-premium/index.md). 

I takt med at der registreres trusler, spiller afhjælpningshandlinger ind. Afhængigt af den specifikke trussel, og hvordan dine sikkerhedsindstillinger er konfigureret, kan afhjælpningshandlinger udføres automatisk eller kun efter godkendelse. Eksempler på afhjælpningshandlinger omfatter afsendelse af en fil til karantæne, stop af en proces i at køre og fjernelse af en planlagt opgave. Alle afhjælpningshandlinger spores i Løsningscenter.

:::image type="content" source="../../media/defender-business/mdb-actioncenter.png" alt-text="Skærmbillede af Løsningscenter":::

**I denne artikel beskrives**:

- [Sådan bruger du Løsningscenter](#how-to-use-the-action-center)
- [Afhjælpningshandlinger](#remediation-actions)

>
> **Har du et øjeblik?**
> Tag vores <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">korte undersøgelse om sikkerhed</a>. Vi vil meget gerne høre fra dig!
>

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