---
title: Om bord på en enhed fra Microsoft Defender til virksomheder
description: Få mere at vide om, hvordan du fjerner en enhed fra Microsoft Defender til virksomheder
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 04/14/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: f702cb51e87777f0ac0e18e7caa794977df9c3dd
ms.sourcegitcommit: e3bc6563037bd2cce2abf108b3d1bcc2ccf538f6
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/15/2022
ms.locfileid: "64862917"
---
# <a name="offboard-a-device-from-microsoft-defender-for-business"></a>Om bord på en enhed fra Microsoft Defender til virksomheder

Hvis du vil være ombord på en enhed, skal du bruge en af følgende procedurer:

- [På en Windows enhed](#offboard-a-windows-device)
- [Ombord på en macOS-computer](#offboard-a-macos-computer)

## <a name="offboard-a-windows-device"></a>På en Windows enhed

1. Gå til Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)), og log på.

2. Vælg **Indstillinger** i navigationsruden, og vælg derefter **Slutpunkter**.

3. Under **Enhedshåndtering** skal du vælge **Offboarding**.

4. Vælg et operativsystem, f.eks **. Windows 10 og 11**, og vælg derefter **Lokalt script** under **Offboard en enhed** i afsnittet **Installationsmetode**. 

5. Gennemse oplysningerne på bekræftelsesskærmen, og vælg derefter **Download** for at fortsætte.

6. Vælg **Download offboarding-pakke**. Vi anbefaler, at du gemmer offboarding-pakken på et flytbart drev.

7. Kør scriptet på hver enhed, du vil offboarde.

## <a name="offboard-a-macos-computer"></a>Ombord på en macOS-computer

1. Gå til **FinderApplications** > . 

2. Højreklik på Microsoft Defender til virksomheder, og vælg derefter **Flyt til papirkurv**. <br/><br/>--- eller --- <br/><br/> Brug følgende kommando: `sudo '/Library/Application Support/Microsoft/Defender/uninstall/uninstall'`.

> [!IMPORTANT]
> Hvis du om bord på en enhed holder op med at sende data til Defender for Business. Data, der modtages før offboarding, opbevares dog i op til seks (6) måneder.

## <a name="next-steps"></a>Næste trin

