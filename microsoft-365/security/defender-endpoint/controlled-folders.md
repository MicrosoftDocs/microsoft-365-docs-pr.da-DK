---
title: Beskyt vigtige mapper mod ransomware fra at kryptere dine filer med kontrolleret mappeadgang
description: Filer i standardmapper kan beskyttes mod at blive ændret af skadelige apps. Forhindre ransomware i at kryptere dine filer.
keywords: kontrolleret mappeadgang, Windows 10, Windows Defender, ransomware, beskytte, filer, mapper
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
ms.openlocfilehash: 02017a614544cfb10eb43d375212fc7e37124ad3
ms.sourcegitcommit: a7cd723fd62b4b0aae9c2c2df04ead3c28180084
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/02/2022
ms.locfileid: "65840381"
---
# <a name="protect-important-folders-with-controlled-folder-access"></a>Beskyt vigtige mapper med kontrolleret mappeadgang

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**

- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- Microsoft Defender Antivirus

**Gælder for**
- Windows


> Vil du opleve Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

## <a name="what-is-controlled-folder-access"></a>Hvad er kontrolleret mappeadgang?

Kontrolleret mappeadgang hjælper med at beskytte dine værdifulde data mod skadelige apps og trusler, f.eks. ransomware. Kontrolleret mappeadgang beskytter dine data ved at kontrollere apps mod en liste over kendte apps, der er tillid til. Understøttes på Windows Server 2019, Windows Server 2022, Windows 10 og Windows 11 klienter, kan kontrolleret mappeadgang slås til ved hjælp af appen Windows Sikkerhed, Microsoft Endpoint Configuration Manager eller Intune (til administrerede enheder).

> [!NOTE]
> Der er ikke tillid til scriptprogrammer, og du kan ikke give dem adgang til beskyttede mapper. Der er f.eks. ikke tillid til PowerShell af kontrolleret mappeadgang, selvom du tillader det med [certifikat- og filindikatorer](/microsoft-365/security/defender-endpoint/indicator-certificates).

Kontrolleret mappeadgang fungerer bedst sammen med [Microsoft Defender for Endpoint](microsoft-defender-endpoint.md), hvilket giver dig detaljeret rapportering om hændelser og blokke for kontrolleret mappeadgang som en del af de sædvanlige [scenarier til undersøgelse af beskeder](investigate-alerts.md).

> [!TIP]
> Adgangsblokke for styrede mapper genererer ikke beskeder i [køen Beskeder](alerts-queue.md). Du kan dog få vist oplysninger om adgangsblokke for styrede mapper i [enhedens tidslinjevisning](investigate-machines.md), mens du bruger [avanceret jagt](advanced-hunting-overview.md) eller med [brugerdefinerede regler for registrering](custom-detection-rules.md).

## <a name="how-does-controlled-folder-access-work"></a>Hvordan fungerer kontrolleret mappeadgang?

Kontrolleret mappeadgang fungerer ved kun at give apps, der er tillid til, adgang til beskyttede mapper. Beskyttede mapper angives, når der konfigureres adgang til styrede mapper. Ofte anvendte mapper, f.eks. mapper, der bruges til dokumenter, billeder, downloads osv., er inkluderet på listen over kontrollerede mapper.

Kontrolleret mappeadgang fungerer sammen med en liste over apps, der er tillid til. Apps, der er inkluderet på listen over software, der er tillid til, fungerer som forventet. Apps, der ikke er inkluderet på listen, forhindres i at foretage ændringer af filer i beskyttede mapper.

Apps føjes til listen baseret på deres udbredelse og omdømme. Apps, der er meget udbredt i hele organisationen, og som aldrig har vist nogen adfærd, der anses for skadelig, anses for at være pålidelige. Disse apps føjes automatisk til listen.

Apps kan også føjes manuelt til listen, der er tillid til, ved hjælp af Configuration Manager eller Intune. Der kan udføres yderligere handlinger fra Microsoft 365 Defender portalen.

## <a name="why-controlled-folder-access-is-important"></a>Hvorfor kontrolleret mappeadgang er vigtig

Kontrolleret mappeadgang er især nyttig til at hjælpe med at beskytte dine dokumenter og oplysninger mod [ransomware](https://www.microsoft.com/wdsi/threats/ransomware). I et ransomware-angreb kan dine filer krypteres og holdes som gidsler. Med kontrolleret mappeadgang på plads vises en meddelelse på den computer, hvor en app forsøgte at foretage ændringer af en fil i en beskyttet mappe. Du kan [tilpasse meddelelsen](attack-surface-reduction-rules-deployment-implement.md#customize-attack-surface-reduction-rules) med dine firmaoplysninger og kontaktoplysninger. Du kan også aktivere reglerne individuelt for at tilpasse, hvilke teknikker funktionen overvåger.

De [beskyttede mapper](#review-controlled-folder-access-events-in-windows-event-viewer) omfatter almindelige systemmapper (herunder startsektorer), og du kan [tilføje flere mapper](customize-controlled-folders.md#protect-additional-folders). Du kan også [give apps tilladelse](customize-controlled-folders.md#allow-specific-apps-to-make-changes-to-controlled-folders) til at give dem adgang til de beskyttede mapper.

Du kan bruge [overvågningstilstand](audit-windows-defender.md) til at evaluere, hvordan kontrolleret mappeadgang ville påvirke din organisation, hvis den blev aktiveret. Du kan også besøge webstedet Windows Defender Test ground på [demo.wd.microsoft.com](https://demo.wd.microsoft.com?ocid=cx-wddocs-testground) for at bekræfte, at funktionen fungerer og se, hvordan den fungerer.

> [!NOTE]
> Demowebstedet Defender for Endpoint på demo.wd.microsoft.com frarådes og fjernes fremover.

Kontrolleret mappeadgang understøttes i følgende versioner af Windows:

- [Windows 10, version 1709](/windows/whats-new/whats-new-windows-10-version-1709) og nyere
- Windows 11
- Windows 2012 R2
- Windows 2016
- [Windows Server 2019](/windows-server/get-started-19/whats-new-19)
- Windows Server 2022

## <a name="windows-system-folders-are-protected-by-default"></a>Windows systemmapper er som standard beskyttet

Windows systemmapper er som standard beskyttet sammen med flere andre mapper:

De beskyttede mapper omfatter almindelige systemmapper (herunder startsektorer), og du kan tilføje flere mapper. Du kan også give apps tilladelse til at give dem adgang til de beskyttede mapper.  De Windows systemmapper, der er beskyttet som standard, er:

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
> Du kan konfigurere flere mapper som beskyttede, men du kan ikke fjerne de Windows systemmapper, der er beskyttet som standard.

## <a name="requirements-for-controlled-folder-access"></a>Krav til adgang til styrede mapper

Kontrolleret mappeadgang kræver aktivering [Microsoft Defender Antivirus beskyttelse i realtid](configure-real-time-protection-microsoft-defender-antivirus.md).

## <a name="review-controlled-folder-access-events-in-the-microsoft-365-defender-portal"></a>Gennemse hændelser for kontrolleret mappeadgang på Microsoft 365 Defender-portalen

Defender for Endpoint giver detaljeret rapportering om hændelser og blokke som en del af [scenarierne til undersøgelse af vigtige beskeder](investigate-alerts.md) på Microsoft 365 Defender-portalen. Se [Microsoft Defender for Endpoint i Microsoft 365 Defender](../defender/microsoft-365-security-center-mde.md).

Du kan forespørge Microsoft Defender for Endpoint data ved hjælp af [Avanceret jagt](advanced-hunting-overview.md). Hvis du bruger [overvågningstilstand](audit-windows-defender.md), kan du bruge [avanceret jagt](advanced-hunting-overview.md) til at se, hvordan indstillinger for adgang til styrede mapper vil påvirke dit miljø, hvis de er aktiveret.

Eksempelforespørgsel:

```PowerShell
DeviceEvents
| where ActionType in ('ControlledFolderAccessViolationAudited','ControlledFolderAccessViolationBlocked')
```

## <a name="review-controlled-folder-access-events-in-windows-event-viewer"></a>Gennemse hændelser for kontrolleret mappeadgang i Windows Logbog

Du kan gennemse Windows hændelsesloggen for at se hændelser, der oprettes, når adgangsblokke (eller overvågninger) for styrede mapper i en app:

1. Download [evalueringspakken](https://aka.ms/mp7z2w) , og udtræk filen *cfa-events.xml* til en placering, der er let tilgængelig på enheden.
2. Skriv **Logbog** i menuen Start for at åbne Windows Logbog.
3. Under **Handlinger** i venstre panel skal du vælge **Importér brugerdefineret visning...**.
4. Naviger til det ønskede *cfa-events.xml* , og vælg det. Du kan også [kopiere XML-koden direkte](event-views.md).
5. Vælg **OK**.

I følgende tabel vises hændelser, der er relateret til kontrolleret mappeadgang:

<br/><br/>

|Hændelses-id|Beskrivelse|
|---|---|
|5007|Hændelse, når indstillingerne ændres|
|1124|Overvåget hændelse for mappeadgang, der kontrolleres|
|1123|Hændelse for adgang til blokeret kontrolleret mappe|

## <a name="view-or-change-the-list-of-protected-folders"></a>Få vist eller rediger listen over beskyttede mapper

Du kan bruge appen Windows Sikkerhed til at få vist listen over mapper, der er beskyttet af kontrolleret mappeadgang.

1. Åbn appen Windows Sikkerhed på din Windows 10- eller Windows 11-enhed.
2. Vælg **Virus- og trusselsbeskyttelse**.
3. Under **Ransomware-beskyttelse** skal du vælge **Administrer ransomware-beskyttelse**.
4. Hvis kontrolleret mappeadgang er slået fra, skal du aktivere den. Vælg **beskyttede mapper**.
5. Udfør et af følgende trin:
   - Hvis du vil tilføje en mappe, skal du vælge **+ Tilføj en beskyttet mappe**.
   - Hvis du vil fjerne en mappe, skal du markere den og derefter vælge **Fjern**.

> [!NOTE]
> [Windows systemmapper](#windows-system-folders-are-protected-by-default) er som standard beskyttet, og du kan ikke fjerne dem fra listen.
