---
title: Beskyt vigtige mapper mod ransomware i at kryptere dine filer med kontrolleret mappeadgang
description: Filer i standardmapper kan beskyttes mod at blive ændret via skadelige apps. Undgå ransomware i at kryptere dine filer.
keywords: styret mappeadgang, windows 10, windows defender, ransomware, beskyt, filer, mapper
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
audience: ITPro
ms.reviewer: oogunrinde, sugamar
manager: dansimp
ms.custom: asr
ms.technology: mde
ms.topic: how-to
ms.collection: m365-security-compliance
ms.date: ''
ms.openlocfilehash: ea3e45a5469c9769f55f9ce90f799c54556de814
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63591773"
---
# <a name="protect-important-folders-with-controlled-folder-access"></a>Beskyt vigtige mapper med styret mappeadgang

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**

- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

## <a name="what-is-controlled-folder-access"></a>Hvad er styret mappeadgang?

Kontrolleret mappeadgang beskytter dine værdifulde data mod skadelige apps og trusler, f.eks ransomware. Kontrolleret mappeadgang beskytter dine data ved at kontrollere apps mod en liste over kendte apps, der er tillid til. Understøttes på Windows Server 2019-, Windows Server 2022-, Windows 10- og Windows 11-klienter, kontrolleret mappeadgang kan slås til ved hjælp af Windows Sikkerhed-appen, Microsoft Endpoint Configuration Manager eller Intune (for administrerede enheder).

> [!NOTE]
> Der er ikke tillid til scripting-programmer, og du kan ikke give dem adgang til beskyttede mapper. PowerShell har f.eks. ikke tillid til styret mappeadgang, heller ikke selvom du tillader det med [certifikat- og filindikatorer](/microsoft-365/security/defender-endpoint/indicator-certificates).

Kontrolleret mappeadgang fungerer bedst med [Microsoft Defender til](microsoft-defender-endpoint.md) slutpunkt, hvilket giver dig detaljeret rapportering om kontrollerede mappeadgangshændelser og -blokke som en del af de sædvanlige scenarier for [beskedundersøgelse](investigate-alerts.md).

> [!TIP]
> Kontrollerede mappeadgangsblokke genererer ikke beskeder i [køen Vigtige beskeder](alerts-queue.md). Du kan dog få vist oplysninger om kontrollerede mappeadgangsblokke i visningen af enhedens [tidslinje, mens](investigate-machines.md) du bruger avanceret [jagt eller med](advanced-hunting-overview.md) [brugerdefinerede registreringsregler](custom-detection-rules.md).

## <a name="how-does-controlled-folder-access-work"></a>Hvordan fungerer kontrolleret mappeadgang?

Styret mappeadgang fungerer kun ved at give pålidelige apps adgang til beskyttede mapper. Beskyttede mapper angives, når der konfigureres kontrolleret mappeadgang. Normalt medtages ofte anvendte mapper, f.eks. mapper, der bruges til dokumenter, billeder, overførsler osv., på listen over kontrollerede mapper.

Styret mappeadgang fungerer sammen med en liste over pålidelige apps. Apps, der er medtaget på listen over softwarearbejde, der er tillid til, som forventet. Apps, der ikke er medtaget på listen, er forhindret i at foretage ændringer i filer i beskyttede mapper.

Apps føjes til listen baseret på deres tilsnelse og omdømme. Apps, der bruges meget i hele organisationen, og som aldrig har vist adfærd, der anses for skadelig, betragtes som pålidelige. Disse apps føjes automatisk til listen.

Apps kan også tilføjes manuelt til listen, der er tillid til, ved hjælp Konfigurationsstyring eller Intune. Der kan udføres yderligere handlinger fra Microsoft 365 Defender portal.

## <a name="why-controlled-folder-access-is-important"></a>Derfor er kontrolleret mappeadgang vigtigt

Kontrolleret mappeadgang er især nyttigt i forbindelse med at beskytte dine dokumenter og oplysninger mod [ransomware](https://www.microsoft.com/wdsi/threats/ransomware). I en ransomware-angreb, kan dine filer krypteres og opbevares af dine venner. Når du har kontrolleret mappeadgang på plads, vises der en meddelelse på den computer, hvor en app har forsøgt at foretage ændringer i en fil i en beskyttet mappe. Du kan [tilpasse meddelelsen med](attack-surface-reduction-rules-deployment-implement.md#customize-attack-surface-reduction-rules) dine firmaoplysninger og kontaktoplysninger. Du kan også aktivere reglerne enkeltvis for at tilpasse, hvilke teknikker funktionen overvåger.

De [beskyttede mapper inkluderer](#review-controlled-folder-access-events-in-windows-event-viewer) almindelige systemmapper (herunder boot udklynde), og [du kan tilføje flere mapper](customize-controlled-folders.md#protect-additional-folders). Du kan også [tillade, at apps](customize-controlled-folders.md#allow-specific-apps-to-make-changes-to-controlled-folders) giver dem adgang til de beskyttede mapper.

Du kan bruge [overvågningstilstand til at](audit-windows-defender.md) evaluere, hvordan kontrolleret mappeadgang vil påvirke organisationen, hvis den blev aktiveret. Du kan også besøge webstedet Windows Defender Test-webstedet [demo.wd.microsoft.com for at](https://demo.wd.microsoft.com?ocid=cx-wddocs-testground) bekræfte, at funktionen virker, og se, hvordan den fungerer.

> [!NOTE]
> Defender for Endpoint-demowebstedet demo.wd.microsoft.com forældet og fjernes fremover.

Kontrolleret mappeadgang understøttes i følgende versioner af Windows:

- [Windows 10, version 1709](/windows/whats-new/whats-new-windows-10-version-1709) og nyere
- Windows 11
- [Windows Server 2019](/windows-server/get-started-19/whats-new-19)
- Windows Server 2022

## <a name="windows-system-folders-are-protected-by-default"></a>Windows systemmapper er som standard beskyttet

Windows systemmapper er som standard beskyttet sammen med flere andre mapper:

De beskyttede mapper inkluderer almindelige systemmapper (herunder boot-udslag), og du kan tilføje flere mapper. Du kan også tillade, at apps giver dem adgang til de beskyttede mapper.  De Windows systemmapper, der er beskyttet som standard, er:

- `c:\Users\<username>\Documents`
- `c:\Users\Public\Documents`
- `c:\Users\<username>\Pictures`
- `c:\Users\Public\Pictures`
- `c:\Users\Public\Videos`
- `c:\Users\<username>\Videos`
- `c:\Users\<username>\Music`
- `c:\Users\Public\Music`
- `c:\Users\<username>\Favorites`

Standardmapper vises i brugerens profil under **Denne pc**.
   > [!div class="mx-imgBorder"]
   > ![Beskyttede Windows standardsystemmapper](images/defaultfolders.png)

> [!NOTE]
> Du kan konfigurere flere mapper som beskyttede, men du kan ikke fjerne Windows mapper, der er beskyttet som standard.

## <a name="requirements-for-controlled-folder-access"></a>Krav til styret mappeadgang

Kontrolleret mappeadgang [kræver Microsoft Defender Antivirus beskyttelse i realtid](configure-real-time-protection-microsoft-defender-antivirus.md).

## <a name="review-controlled-folder-access-events-in-the-microsoft-365-defender-portal"></a>Gennemse styret mappeadgangshændelser i Microsoft 365 Defender-portalen

Defender til Slutpunkt leverer detaljeret rapportering om hændelser og blokke som en del af [dens](investigate-alerts.md) scenarier for undersøgelse af beskeder på Microsoft 365 Defender-portalen. Se [Microsoft Defender til slutpunkt i Microsoft 365 Defender](../defender/microsoft-365-security-center-mde.md).

Du kan forespørge Microsoft Defender efter slutpunktsdata ved hjælp af [Avanceret jagt](advanced-hunting-overview.md). Hvis du bruger [overvågningstilstand,](audit-windows-defender.md) kan du bruge avanceret [](advanced-hunting-overview.md) på jagt efter at se, hvordan kontrollerede indstillinger for mappeadgang vil påvirke dit miljø, hvis de blev aktiveret.

Eksempelforespørgsel:

```PowerShell
DeviceEvents
| where ActionType in ('ControlledFolderAccessViolationAudited','ControlledFolderAccessViolationBlocked')
```

## <a name="review-controlled-folder-access-events-in-windows-event-viewer"></a>Gennemse kontrollerede mappeadgangshændelser Windows Logvisning

Du kan gennemse hændelsesloggen Windows for at få vist hændelser, der oprettes, når du styret mappeadgangsblokke (eller revisioner) en app:

1. Download [evalueringspakken](https://aka.ms/mp7z2w) , og udtræk *filencfa-events.xml* en lettilgængelig placering på enheden.
2. Skriv **Log på menuen Start** for at åbne Windows Log på.
3. I venstre panel under Handlinger **skal du** vælge **Importér brugerdefineret visning...**.
4. Gå til det sted, hvor du *cfa-events.xml,* og vælg den. Alternativt kan du [kopiere XML direkte](event-views.md).
5. Vælg **OK**.

Følgende tabel viser hændelser, der er relateret til styret mappeadgang:

<br/><br/>

|Hændelses-id|Beskrivelse|
|---|---|
|5007|Hændelse, når indstillingerne ændres|
|1124|Overvåget styret mappeadgangshændelse|
|1123|Hændelse med blokeret styret mappeadgang|

## <a name="view-or-change-the-list-of-protected-folders"></a>Få vist eller rediger listen over beskyttede mapper

Du kan bruge Windows Sikkerhed til at få vist listen over mapper, der er beskyttet af styret mappeadgang.

1. På din Windows 10 eller Windows 11-enhed skal du Windows Sikkerhed appen.
2. Vælg **Virus- & trusselsbeskyttelse**.
3. Under **Ransomware-beskyttelse** skal du **vælge Administrer beskyttelse mod ransomware**.
4. Hvis kontrolleret mappeadgang er slået fra, skal du aktivere den. Vælg **beskyttede mapper**.
5. Udfør et af følgende trin:
   - Hvis du vil tilføje en mappe, skal **du vælge + Tilføj en beskyttet mappe**.
   - Hvis du vil fjerne en mappe, skal du markere den og derefter vælge **Fjern**.

> [!NOTE]
> [Windows systemmapper](#windows-system-folders-are-protected-by-default) er som standard beskyttet, og du kan ikke fjerne dem fra listen.
