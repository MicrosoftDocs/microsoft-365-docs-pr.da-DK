---
title: Gennemse afhjælpningshandlinger i Microsoft 365 Business Premium
description: Se, hvordan du kan få vist afhjælpninger, der er blevet taget automatisk, eller som afventer godkendelse i Handlingscenter
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: how-to
ms.date: 02/24/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: 160cef2ec7691fbc9debad809b20461a0d3efe23
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/17/2022
ms.locfileid: "63705535"
---
# <a name="review-remediation-actions-in-microsoft-365-business-premium"></a>Gennemse afhjælpningshandlinger i Microsoft 365 Business Premium

Efterhånden som trusler registreres, bliver afhjælpningshandlingerne afspillet. Afhængigt af den bestemte trussel, og hvordan dine sikkerhedsindstillinger er konfigureret, kan afhjælpningshandlinger blive taget automatisk eller kun efter godkendelse. Eksempler på afhjælpningshandlinger er at sende en fil til karantæne, stoppe en proces i at køre og fjerne en planlagt opgave. Alle afhjælpningshandlinger registreres i Handlingscenter, som findes på [https://security.microsoft.com/action-center](https://security.microsoft.com/action-center).

:::image type="content" source="../media/defender-business/mdb-actioncenter.png" alt-text="Skærmbillede af Handlingscenter i M365.":::

**I denne artikel beskrives følgende**:

- [Sådan bruger du handlingscenter](#how-to-use-your-action-center)

- [Typer af afhjælpningshandlinger](#types-of-remediation-actions)


## <a name="how-to-use-your-action-center"></a>Sådan bruger du dit handlingscenter

1. Gå til Microsoft 365 Defender -portalen ([https://security.microsoft.com](https://security.microsoft.com)), og log på.

2. Vælg Handlingscenter i **navigationsruden**.

3. Vælg fanen **Afventer** for at få vist og godkende (eller afvise) alle ventende handlinger. Sådanne handlinger kan opstå som følge af beskyttelse mod antivirus/antimalware, automatiserede undersøgelser, manuelle svaraktiviteter eller live svarsessioner.

4. Vælg fanen **Oversigt** for at få vist en liste over fuldførte handlinger. 

## <a name="types-of-remediation-actions"></a>Typer af afhjælpningshandlinger

Dit abonnement omfatter flere forskellige typer afhjælpningshandlinger for registrerede trusler. Disse handlinger omfatter manuelle svarhandlinger, handlinger efter automatiseret undersøgelse og live svarhandlinger.

I følgende tabel vises afhjælpningshandlinger, der er tilgængelige:

| Kilde  | Handlinger  |
|---------|---------|
| [Automatiserede undersøgelser](../security/defender-endpoint/automated-investigations.md)      | - Sætte en fil i karantæne <br/>- Fjerne en registreringsdatabasenøgle <br/>- Kill a process <br/>- Stop en tjeneste <br/>- Deaktiver en driver <br/>- Fjerne en planlagt opgave        |
| [Manuelle svarhandlinger](../security/defender-endpoint/respond-machine-alerts.md)   | - Kør antivirus-scanning <br/>- Isoler enhed <br/>- Stop og karantæne <br/>- Tilføj en indikator for at blokere eller tillade en fil       |
| [Livesvar](../security/defender-endpoint/live-response.md)   | - Indsamle data, der skal indsamles <br/>- Analysér en fil <br/>- Kør et script <br/>- Sende en mistænkelig enhed til Microsoft til analyse <br/>- Afhjælpe en fil <br/>- Proaktivt lede efter trusler         |
