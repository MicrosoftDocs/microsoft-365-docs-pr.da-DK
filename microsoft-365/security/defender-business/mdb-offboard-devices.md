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
ms.openlocfilehash: bd6ea78daa1a19d84efc23c34bdb58704484c0d1
ms.sourcegitcommit: fa90763559239c4c46c5e848939126763879d8e4
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/13/2022
ms.locfileid: "66772414"
---
# <a name="offboard-a-device-from-microsoft-defender-for-business"></a>Om bord på en enhed fra Microsoft Defender til virksomheder

Hvis du vil være ombord på en enhed, skal du bruge en af følgende procedurer:

- [Uden for en Windows-enhed](#offboard-a-windows-device)
- [På en Mac](#offboard-a-mac)

## <a name="offboard-a-windows-device"></a>Uden for en Windows-enhed

1. Gå til Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)), og log på.

2. Vælg **Indstillinger** i navigationsruden, og vælg derefter **Slutpunkter**.

3. Under **Enhedshåndtering** skal du vælge **Offboarding**.

4. Vælg et operativsystem, f.eks **. Windows 10 og 11**, og vælg derefter **Lokalt script** under **Offboard en enhed** i afsnittet **Installationsmetode**. 

5. Gennemse oplysningerne på bekræftelsesskærmen, og vælg derefter **Download** for at fortsætte.

6. Vælg **Download offboarding-pakke**. Vi anbefaler, at du gemmer offboarding-pakken på et flytbart drev.

7. Kør scriptet på hver enhed, du vil offboarde.

## <a name="offboard-a-mac"></a>På en Mac

1. Gå til **Søgeprogrammer** > . 

2. Højreklik på **Microsoft Defender til virksomheder**, og vælg derefter **Flyt til papirkurven**. <br/>--- eller --- <br/> Brug følgende kommando: `sudo '/Library/Application Support/Microsoft/Defender/uninstall/uninstall'`.

> [!IMPORTANT]
> Hvis du om bord på en enhed holder op med at sende data til Defender for Business. Data, der modtages før offboarding, opbevares dog i op til seks (6) måneder.

## <a name="next-steps"></a>Næste trin

- [Brug dashboardet Administration af sårbarheder i & Threat & i Microsoft Defender til virksomheder](mdb-view-tvm-dashboard.md)
- [Få vist eller rediger politikker i Microsoft Defender til virksomheder](mdb-view-edit-create-policies.md)
- [Administrer enheder i Microsoft Defender til virksomheder](mdb-manage-devices.md)