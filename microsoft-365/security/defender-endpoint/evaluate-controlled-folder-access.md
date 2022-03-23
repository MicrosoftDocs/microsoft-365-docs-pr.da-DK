---
title: Evaluer styret mappeadgang
description: Se, hvordan kontrolleret mappeadgang kan hjælpe med at beskytte filer mod at blive ændret af skadelige apps.
keywords: Exploit Protection, windows 10, windows 11, windows defender, ransomware, protect, evaluate, test, demo, prøv
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
audience: ITPro
ms.topic: conceptual
author: dansimp
ms.author: dansimp
ms.reviewer: oogunrinde, sugamar
manager: dansimp
ms.technology: mde
ms.collection: m365-security-compliance
ms.date: ''
ms.openlocfilehash: 85e2da73fd54bd4d24e5ab8c4d104e33b5b4d877
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63592910"
---
# <a name="evaluate-controlled-folder-access"></a>Evaluer styret mappeadgang

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-enablesiem-abovefoldlink)


[Kontrolleret mappeadgang](controlled-folders.md) er en funktion, der hjælper med at beskytte dine dokumenter og filer mod ændringer fra mistænkelige eller skadelige apps. Kontrolleret mappeadgang understøttes på Windows Server 2019, Windows Server 2022, Windows 10 og Windows 11-klienter.

Det er især nyttigt til at beskytte dig mod ransomware, der forsøger at kryptere dine filer og holde dem beskyttet mod [ransomware](https://www.microsoft.com/wdsi/threats/ransomware) .

Denne artikel hjælper dig med at evaluere kontrolleret mappeadgang. Den forklarer, hvordan du aktiverer overvågningstilstand, så du kan teste funktionen direkte i organisationen.

> [!TIP]
> Du kan også besøge webstedet for demoscenariet Microsoft Defender for Endpoint [på demo.wd.microsoft.com](https://demo.wd.microsoft.com?ocid=cx-wddocs-testground) for at bekræfte, at funktionen virker, og se, hvordan den fungerer.

> [!NOTE]
> Defender for Endpoint-demowebstedet demo.wd.microsoft.com forældet og fjernes fremover.

## <a name="use-audit-mode-to-measure-impact"></a>Brug overvågningstilstand til at måle påvirkningen

Aktivér styret mappeadgang i overvågningstilstand for at se en post med, hvad *der ville* være sket, hvis den var fuldt aktiveret. Test, hvordan funktionen fungerer i din organisation for at sikre, at den ikke påvirker dine line of business-apps. Du kan også få en ide om, hvor mange forsøg på mistænkelige filændringer, der generelt forekommer i løbet af en bestemt tidsperiode.

For at aktivere overvågningstilstand skal du bruge følgende PowerShell-cmdlet:

```PowerShell
Set-MpPreference -EnableControlledFolderAccess AuditMode
```

> [!TIP]
> Hvis du fuldt ud vil overvåge, hvordan kontrolleret mappeadgang fungerer i organisationen, skal du bruge et administrationsværktøj til at udrulle denne indstilling på enheder i dit netværk.
Du kan også bruge Gruppepolitik, Intune, administration af mobilenheder (MDM) eller Microsoft Endpoint Manager til at konfigurere og installere indstillingen, som beskrevet i det primære emne om styret [mappeadgang](controlled-folders.md).

## <a name="review-controlled-folder-access-events-in-windows-event-viewer"></a>Gennemse kontrollerede mappeadgangshændelser Windows Logvisning

Følgende hændelser med kontrolleret mappeadgang vises Windows Log over begivenheder under Microsoft/Windows/Windows Defender/Drift.

Hændelses-id | Beskrivelse
-|-
 5007 | Hændelse, når indstillingerne ændres
 1124 | Overvåget styret mappeadgangshændelse
 1123 | Hændelse med blokeret styret mappeadgang

> [!TIP]
> Du kan konfigurere et [Windows til videresendelse af](/windows/win32/wec/setting-up-a-source-initiated-subscription) begivenheder for at samle logfilerne centralt. 

## <a name="customize-protected-folders-and-apps"></a>Tilpas beskyttede mapper og apps

Under evalueringen kan det være en ide at føje til listen over beskyttede mapper eller tillade, at visse apps redigerer filer.

Se [Beskyt vigtige](controlled-folders.md) mapper med kontrolleret mappeadgang for at konfigurere funktionen med administrationsværktøjer, herunder Gruppepolitik, PowerShell og MDM-konfigurationstjenesteudbydere.

## <a name="see-also"></a>Se også

* [Beskyt vigtige mapper med styret mappeadgang](controlled-folders.md)
* [Evaluer Microsoft Defender til slutpunkt](evaluate-mde.md)
* [Brug overvågningstilstand](audit-windows-defender.md)
