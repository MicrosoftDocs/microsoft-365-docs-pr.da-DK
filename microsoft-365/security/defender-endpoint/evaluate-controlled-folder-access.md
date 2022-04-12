---
title: Evaluer styret mappeadgang
description: Se, hvordan kontrolleret mappeadgang kan hjælpe med at beskytte filer mod at blive ændret af skadelige apps.
keywords: Udnyt beskyttelse, Windows 10, Windows 11, Windows Defender, ransomware, beskyt, evaluer, test, demo, prøv
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
ms.openlocfilehash: 4ccb91f0a8c181697eb525dd8f5576e6f6cdc0d1
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/12/2022
ms.locfileid: "64789816"
---
# <a name="evaluate-controlled-folder-access"></a>Evaluer styret mappeadgang

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- Microsoft Defender Antivirus

**Platforme**
- Windows

> Vil du opleve Microsoft Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-enablesiem-abovefoldlink)


[Kontrolleret mappeadgang](controlled-folders.md) er en funktion, der hjælper med at beskytte dine dokumenter og filer mod at blive ændret af mistænkelige eller skadelige apps. Kontrolleret mappeadgang understøttes på Windows Server 2019, Windows Server 2022, Windows 10 og Windows 11 klienter.

Det er især nyttigt i at hjælpe med at beskytte mod [ransomware](https://www.microsoft.com/wdsi/threats/ransomware) , der forsøger at kryptere dine filer og holde dem som gidsler.

Denne artikel hjælper dig med at evaluere kontrolleret mappeadgang. Den forklarer, hvordan du aktiverer overvågningstilstand, så du kan teste funktionen direkte i din organisation.

> [!TIP]
> Du kan også besøge webstedet for Microsoft Defender for Endpoint demoscenarie på [demo.wd.microsoft.com](https://demo.wd.microsoft.com?ocid=cx-wddocs-testground) for at bekræfte, at funktionen fungerer, og se, hvordan den fungerer.

> [!NOTE]
> Demowebstedet Defender for Endpoint på demo.wd.microsoft.com frarådes og fjernes fremover.

## <a name="use-audit-mode-to-measure-impact"></a>Brug overvågningstilstand til at måle indvirkning

Aktivér adgang til den styrede mappe i overvågningstilstand for at se en post over, hvad der *ville* være sket, hvis den var fuldt aktiveret. Test, hvordan funktionen fungerer i din organisation, for at sikre, at den ikke påvirker dine line of business-apps. Du kan også få en idé om, hvor mange mistænkelige filændringsforsøg der generelt opstår over en bestemt periode.

Hvis du vil aktivere overvågningstilstand, skal du bruge følgende PowerShell-cmdlet:

```PowerShell
Set-MpPreference -EnableControlledFolderAccess AuditMode
```

> [!TIP]
> Hvis du vil overvåge, hvordan kontrolleret mappeadgang fungerer i din organisation, skal du bruge et administrationsværktøj til at installere denne indstilling på enheder på dine netværk.
Du kan også bruge Gruppepolitik, Intune, administration af mobilenheder (MDM) eller Microsoft Endpoint Manager til at konfigurere og installere indstillingen, som beskrevet i [emnet adgang til hovedmapper](controlled-folders.md).

## <a name="review-controlled-folder-access-events-in-windows-event-viewer"></a>Gennemse hændelser for kontrolleret mappeadgang i Windows Logbog

Følgende hændelser for adgang til styrede mapper vises i Windows Logbog under Mappen Microsoft/Windows/Windows Defender/Operations.

Hændelses-id | Beskrivelse
-|-
 5007 | Hændelse, når indstillingerne ændres
 1124 | Overvåget hændelse for mappeadgang, der kontrolleres
 1123 | Hændelse for adgang til blokeret kontrolleret mappe

> [!TIP]
> Du kan konfigurere et [abonnement på videresendelse af Windows hændelse](/windows/win32/wec/setting-up-a-source-initiated-subscription) for at indsamle loggene centralt. 

## <a name="customize-protected-folders-and-apps"></a>Tilpas beskyttede mapper og apps

Under din evaluering kan du føje til listen over beskyttede mapper eller tillade, at visse apps redigerer filer.

Se [Beskyt vigtige mapper med kontrolleret mappeadgang](controlled-folders.md) for at konfigurere funktionen med administrationsværktøjer, herunder udbydere af Gruppepolitik, PowerShell og MDM-konfigurationstjenester.

## <a name="see-also"></a>Se også

* [Beskyt vigtige mapper med kontrolleret mappeadgang](controlled-folders.md)
* [Evaluer Microsoft Defender for Endpoint](evaluate-mde.md)
* [Brug overvågningstilstand](audit-windows-defender.md)
