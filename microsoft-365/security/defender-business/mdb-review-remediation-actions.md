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
ms.openlocfilehash: 63bbeb218693174402264bb59a6c014e63e14bef
ms.sourcegitcommit: fa90763559239c4c46c5e848939126763879d8e4
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/13/2022
ms.locfileid: "66770971"
---
# <a name="review-remediation-actions-in-the-action-center"></a>Gennemse afhjælpningshandlinger i Løsningscenter

I takt med at der registreres trusler, spiller afhjælpningshandlinger ind. Afhængigt af den specifikke trussel, og hvordan dine sikkerhedsindstillinger er konfigureret, kan afhjælpningshandlinger udføres automatisk eller kun efter godkendelse. Eksempler på afhjælpningshandlinger omfatter: 
- Send en fil til karantæne
- Stop en proces i at køre
- Fjern en planlagt opgave

Alle afhjælpningshandlinger spores i Løsningscenter.

:::image type="content" source="../../media/defender-business/mdb-actioncenter.png" alt-text="Skærmbillede af Løsningscenter":::

**I denne artikel beskrives**:

- [Sådan bruger du Løsningscenter](#how-to-use-the-action-center)
- [Afhjælpningshandlinger](#remediation-actions)


## <a name="how-to-use-the-action-center"></a>Sådan bruger du Løsningscenter

1. Gå til Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)), og log på.

2. Vælg **Løsningscenter** i navigationsruden.

3. Vælg fanen **Ventende** for at få vist og godkende (eller afvise) ventende handlinger. Handlinger kan opstå som følge af beskyttelse mod antivirus/antimalware, automatiserede undersøgelser, manuelle svaraktiviteter eller live-svarsessioner.

4. Vælg fanen **Oversigt** for at få vist en liste over fuldførte handlinger.

## <a name="remediation-actions"></a>Afhjælpningshandlinger

Defender for Business indeholder flere afhjælpningshandlinger. Disse handlinger omfatter manuelle svarhandlinger, handlinger efter automatiseret undersøgelse og liveresponshandlinger.

I følgende tabel vises de afhjælpningshandlinger, der er tilgængelige.

| Kilde  | Handlinger  |
|---------|---------|
| [Automatiserede undersøgelser](../defender-endpoint/automated-investigations.md)      |<ul><li>Sæt en fil i karantæne</li><li>Fjern en registreringsdatabasenøgle</li><li>Dræb en proces</li><li>Stop en tjeneste</li><li>Deaktiver en driver</li><li>Fjern en planlagt opgave </li></ul> |
| [Handlinger for manuelt svar](../defender-endpoint/respond-machine-alerts.md)   |<ul><li>Kør antivirusscanning</li><li>Isoler en enhed</li><li>Stop og sæt karantæne</li><li>Tilføj en indikator for at blokere eller tillade en fil</li></ul> |
| [Live-svar](../defender-endpoint/live-response.md)   |<ul><li>Indsaml tekniske data</li><li>Analysér en fil</li><li>Kør et script</li><li>Send en mistænkelig enhed til Microsoft til analyse</li><li>Afhjælpning af en fil </li><li>Proaktiv jagt på trusler</li></ul>|

## <a name="next-steps"></a>Næste trin

- [Reager på og afhjælp trusler i Defender for Business](mdb-respond-mitigate-threats.md)
- [Administrer enheder i Defender for Business](mdb-manage-devices.md)
