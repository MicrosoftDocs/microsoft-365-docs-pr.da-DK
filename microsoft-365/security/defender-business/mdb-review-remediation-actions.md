---
title: Gennemse afhjælpningshandlinger i Microsoft Defender for Business
description: Få vist afhjælpninger, der er taget automatisk, eller som afventer godkendelse i Handlingscenter
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: how-to
ms.date: 03/10/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: b5bb61d4a0b8f3cb0732633463fbf2c96ec258e9
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/17/2022
ms.locfileid: "63598575"
---
# <a name="review-remediation-actions-in-the-action-center"></a>Gennemse afhjælpningshandlinger i Handlingscenter

> [!IMPORTANT]
> Microsoft Defender for Business udrulles til [Microsoft 365 Business Premium](../../business-premium/index.md) kunder fra d. 1. marts 2022. Defender for Business som et enkeltstående abonnement er i preview, og den udrulles gradvist til kunder og [it-partnere](https://aka.ms/mdb-preview) , der tilmelder sig her for at anmode om det. [Forhåndsvisning indeholder et indledende sæt scenarier](mdb-tutorials.md#try-these-preview-scenarios), og vi tilføjer funktioner regelmæssigt.
> 
> Nogle oplysninger i denne artikel relaterer til foreløbige produkter/tjenester, der kan være væsentligt ændret, før de frigives kommercielt. Microsoft giver ingen garantier, udtrykkelige eller underforståede, for de oplysninger, du har angivet her. 

Efterhånden som trusler registreres, bliver afhjælpningshandlingerne afspillet. Afhængigt af den bestemte trussel, og hvordan dine sikkerhedsindstillinger er konfigureret, kan afhjælpningshandlinger blive taget automatisk eller kun efter godkendelse. Eksempler på afhjælpningshandlinger er at sende en fil til karantæne, stoppe en proces i at køre og fjerne en planlagt opgave. Alle afhjælpningshandlinger registreres i Handlingscenter.

:::image type="content" source="../../media/defender-business/mdb-actioncenter.png" alt-text="Skærmbillede af handlingscenter":::

**I denne artikel beskrives følgende**:

- [Sådan bruger du handlingscenter](#how-to-use-the-action-center)

- [Afhjælpningshandlinger](#remediation-actions)

>
> **Har du et minut?**
> Tag vores korte <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">undersøgelse om Microsoft Defender for Business</a>. Vi vil meget gerne høre fra dig!
>

## <a name="how-to-use-the-action-center"></a>Sådan bruger du handlingscenter

1. Gå til Microsoft 365 Defender -portalen ([https://security.microsoft.com](https://security.microsoft.com)), og log på.

2. Vælg Handlingscenter i **navigationsruden**.

3. Vælg fanen **Afventer** for at få vist og godkende (eller afvise) alle ventende handlinger. Sådanne handlinger kan opstå som følge af beskyttelse mod antivirus/antimalware, automatiserede undersøgelser, manuelle svaraktiviteter eller live svarsessioner.

4. Vælg fanen **Oversigt** for at få vist en liste over fuldførte handlinger. 

## <a name="remediation-actions"></a>Afhjælpningshandlinger

Microsoft Defender for Business omfatter adskillige afhjælpningshandlinger. Disse handlinger omfatter manuelle svarhandlinger, handlinger efter automatiseret undersøgelse og live svarhandlinger.

I følgende tabel vises afhjælpningshandlinger, der er tilgængelige:

| Kilde  | Handlinger  |
|---------|---------|
| [Automatiserede undersøgelser](../defender-endpoint/automated-investigations.md)      | - Sætte en fil i karantæne <br/>- Fjerne en registreringsdatabasenøgle <br/>- Kill a process <br/>- Stop en tjeneste <br/>- Deaktiver en driver <br/>- Fjerne en planlagt opgave        |
| [Manuelle svarhandlinger](../defender-endpoint/respond-machine-alerts.md)   | - Kør antivirus-scanning <br/>- Isoler enhed <br/>- Stop og karantæne <br/>- Tilføj en indikator for at blokere eller tillade en fil       |
| [Livesvar](../defender-endpoint/live-response.md)   | - Indsamle data, der skal indsamles <br/>- Analysér en fil <br/>- Kør et script <br/>- Sende en mistænkelig enhed til Microsoft til analyse <br/>- Afhjælpe en fil <br/>- Proaktivt lede efter trusler         |

## <a name="next-steps"></a>Næste trin

- [Re besvare og afhjælpe trusler i Microsoft Defender for Business](mdb-respond-mitigate-threats.md)

- [Administrer enheder i Microsoft Defender for Business](mdb-manage-devices.md)