---
title: Om bord på en enhed fra Microsoft Defender til virksomheder
description: Få mere at vide om, hvordan du fjerner eller fjerner en enhed fra Microsoft Defender til virksomheder.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: 00b9b8b9a4ac1cfad07741de84bd99db5403ef1a
ms.sourcegitcommit: f30616b90b382409f53a056b7a6c8be078e6866f
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/03/2022
ms.locfileid: "65174453"
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

2. Højreklik på Microsoft Defender til virksomheder, og vælg derefter **Flyt til papirkurv**. <br/>--- eller --- <br/> Brug følgende kommando: `sudo '/Library/Application Support/Microsoft/Defender/uninstall/uninstall'`.

> [!IMPORTANT]
> Hvis du om bord på en enhed holder op med at sende data til Defender for Business. Data, der modtages før offboarding, opbevares dog i op til seks (6) måneder.

## <a name="next-steps"></a>Næste trin

- [Brug dashboardet Administration af sårbarheder i & Threat & i Microsoft Defender til virksomheder](mdb-view-tvm-dashboard.md)
- [Få vist eller rediger politikker i Microsoft Defender til virksomheder](mdb-view-edit-create-policies.md)
- [Administrer enheder i Microsoft Defender til virksomheder](mdb-manage-devices.md)