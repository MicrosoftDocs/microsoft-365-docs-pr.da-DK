---
title: Onboard-enheder til Microsoft Defender til virksomheder
description: Få mere at vide om indstillinger for onboarding af enheder Microsoft Defender til virksomheder
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 04/01/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: 78a8eaa5a9472a32c9615dfb7c7f5b08afe548ff
ms.sourcegitcommit: adea59259a5900cad5de29ddf46d1ca9e9e1c82f
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/04/2022
ms.locfileid: "64634729"
---
# <a name="onboard-devices-to-microsoft-defender-for-business"></a>Onboard-enheder til Microsoft Defender til virksomheder

> [!IMPORTANT]
> Microsoft Defender til virksomheder udrulles til [Microsoft 365 Business Premium](../../business-premium/index.md) fra 1. marts 2022. Defender for Business som et enkeltstående abonnement er i preview, og den udrulles gradvist til kunder og [it-partnere](https://aka.ms/mdb-preview) , der tilmelder sig her for at anmode om det. [Forhåndsvisning indeholder et indledende sæt scenarier](mdb-tutorials.md#try-these-preview-scenarios), og vi tilføjer funktioner regelmæssigt.
> 
> Nogle oplysninger i denne artikel relaterer til foreløbige produkter/tjenester, der kan være væsentligt ændret, før de frigives kommercielt. Microsoft giver ingen garantier, udtrykkelige eller underforståede, for de oplysninger, du har angivet her. 

Med Microsoft Defender til virksomheder har du adskillige muligheder at vælge mellem til onboarding af virksomhedens enheder. Denne artikel gennemgår dine muligheder og indeholder en oversigt over, hvordan onboarding fungerer.

>
> **Har du et minut?**
> Tag vores <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">korte undersøgelse om Microsoft Defender til virksomheder</a>. Vi vil meget gerne høre fra dig!
>

## <a name="what-to-do"></a>Hvad kan du gøre?

1. [Se dine muligheder for onboardingenheder](#device-onboarding-methods), og vælg en metode. 

   - [Brug automatisk onboarding til Windows enheder, der allerede er tilmeldt Microsoft Endpoint Manager](#automatic-onboarding-for-windows-devices-enrolled-in-microsoft-endpoint-manager)
   - [Brug et lokalt script til at Windows eller macOS-enheder](#local-script-in-defender-for-business)
   - [Brug Microsoft Endpoint Manager til at onboarde Windows, macOS eller mobilenheder](#microsoft-endpoint-manager)

2. [Kør en registreringstest](#run-a-detection-test) på nyligt onboardede Windows enheder.

3. [Se dine næste trin](#next-steps). 

Denne artikel indeholder også oplysninger om [offboarding af en enhed](#offboarding-a-device).

## <a name="device-onboarding-methods"></a>Onboardingmetoder for enheder

Defender for Business giver dig flere forskellige metoder til onboardingenheder, uanset om du allerede bruger Microsoft Endpoint Manager, eller du blot ønsker en forenklet onboardingoplevelse. De mest almindeligt anvendte metoder til at onboarde enheder til Defender for Business omfatter:

- **Automatisk onboarding** til Windows enheder, der allerede er tilmeldt Microsoft Endpoint Manager. Automatisk onboarding konfigurerer en forbindelse mellem Defender for Business og Microsoft Endpoint Manager og derefter onboards Windows til Defender for Business. Før du kan bruge denne indstilling, skal dine enheder allerede være tilmeldt Endpoint Manager. Du kan få mere at vide [under Automatisk onboarding](#automatic-onboarding-for-windows-devices-enrolled-in-microsoft-endpoint-manager).

- **Lokalt script** til at onboarde Windows og macOS-enheder til Defender for Business manuelt. Du kan onboarde op til 10 enheder ad gangen ved hjælp af det lokale script. Du kan få mere at vide [under Lokalt script i Defender for Business](#local-script-in-defender-for-business).

- **Microsoft Intune** eller **Microsoft Endpoint Manager** til Windows, macOS og mobilenheder. Du kan tilmelde enheder i Endpoint Manager og derefter onboarde dine enheder til Defender for Business. [Microsoft 365 Business Premium kunder](../../business-premium/index.md) allerede har [Microsoft Intune](/mem/intune/fundamentals/what-is-intune), og både Microsoft Intune og [Enhedshåndtering er](/mem/intune/enrollment/device-enrollment) nu en del af Endpoint Manager. Hvis du vil bruge denne metode, skal [du se Microsoft Endpoint Manager](#microsoft-endpoint-manager).

> [!IMPORTANT]
> Hvis noget går galt, og din onboardingproces mislykkes, skal [du Microsoft Defender til virksomheder fejlfinding](mdb-troubleshooting.yml).

## <a name="automatic-onboarding-for-windows-devices-enrolled-in-microsoft-endpoint-manager"></a>Automatisk onboarding til Windows enheder, der er tilmeldt Microsoft Endpoint Manager

Indstillingen automatisk onboarding gælder kun for Windows enheder. Automatisk onboarding er tilgængelig, hvis følgende betingelser er opfyldt:

- Din virksomhed brugte allerede Microsoft Endpoint Manager, Microsoft Intune eller mobile Enhedshåndtering (MDM) i Microsoft Intune, før du fik Defender for Business

- Du har allerede Windows enheder, der er tilmeldt Endpoint Manager

Hvis Windows-enheder allerede er tilmeldt Endpoint Manager, registrerer Defender for Business disse enheder, mens du er i gang med at konfigurere Defender for Business. Du bliver spurgt, om du vil bruge automatisk onboarding til alle eller nogle af dine Windows enheder. Du kan onboarde Windows-enheder på én gang, eller du kan vælge specifikke enheder, du vil starte med, og derefter tilføje flere enheder senere.

> [!TIP]
> Vi anbefaler, at du vælger indstillingen "Alle enheder tilmeldt". På den måde Windows enheder automatisk onboardet til Defender for Business, Endpoint Manager senere er tilmeldt. Hvis du har administreret sikkerhedspolitikker og -indstillinger i Endpoint Manager, anbefaler vi desuden, at du skifter til Microsoft 365 Defender-portalen for at administrere dine enheder, politikker og indstillinger. Du kan få mere at vide [under Vælg, hvor du vil administrere sikkerhedspolitikker og -enheder](mdb-configure-security-settings.md#choose-where-to-manage-security-policies-and-devices).

Du kan få mere at vide om automatisk onboarding i trin 2 [i Brug guiden til at konfigurere Microsoft Defender til virksomheder](mdb-use-wizard.md).

## <a name="local-script-in-defender-for-business"></a>Lokalt script i Defender for Business

Du kan bruge et lokalt script til at onboarde Windows- og Mac-enheder. Når du kører onboardingscriptet på en enhed, opretter det en tillid til Azure Active Directory (hvis denne tillid ikke allerede findes), tilmelder enheden i Microsoft Endpoint Manager (hvis den ikke allerede er tilmeldt) og onboarder derefter enheden til Defender for Business. Denne metode er nyttig til onboardingenheder i Defender for Business. Du kan onboarde op til 10 enheder ad gangen.

1. Gå til Microsoft 365 Defender -portalen ([https://security.microsoft.com](https://security.microsoft.com)), og log på.

2. I navigationsruden skal du **vælge Indstillinger** >  **Endpoints**, og derefter skal du under **Enhedshåndtering** vælge **Onboarding**.

3. Vælg et operativsystem, f.eks **. Windows 10 og 11** eller **macOS**, og vælg derefter **Lokalt script i sektionen Installationsmetode**. 

4. Vælg **Download onboarding pakke**. Vi anbefaler, at du gemmer onboardingpakken på et flytbart drev. Hvis du har valgt **macOS**, skal du også **vælge Download installationspakke** og gemme den på din flytbare enhed.

5. Følg vejledningen i følgende tabel:

   | Operativsystem | Procedure |
   |---|---|
   | Windows | 1. På en Windows enhed skal du udtrække indholdet af konfigurationspakken til en placering, f.eks. mappen Skrivebord. Du bør have en fil med navnet `WindowsDefenderATPLocalOnboardingScript.cmd`. <br/><br/>2. Åbn Kommandoprompt som administrator.<br/><br/>3. Skriv placeringen af scriptfilen. Hvis du f.eks. har kopieret filen til mappen Skrivebord, skal du skrive: `%userprofile%\Desktop\WindowsDefenderATPLocalOnboardingScript.cmd`og derefter trykke på Enter (eller vælge **OK**).<br/><br/>4. Når scriptet kører, skal du gå videre til [Kør en registreringstest](#run-a-detection-test). |
   | macOS | 1. På en Mac-computer skal du gemme installationspakken som `wdav.pkg` en lokal mappe. <br/><br/>2. Gem onboardingpakken som i `WindowsDefenderATPOnboardingPackage.zip` den samme mappe, du brugte til installationspakken. <br/><br/>3. Brug Finder til at navigere til `wdav.pkg` det, du har gemt, og åbn det derefter.<br/><br/>4. Vælg **Fortsæt**, enig med licensvilkårene, og angiv din adgangskode, når du bliver bedt om det.<br/><br/>5. Du bliver bedt om at tillade installation af en driver fra Microsoft (enten "Systemudvidelse blokeret" eller "Installation er sat i venteposition" eller begge dele. Driveren skal være installeret. For at tillade installationen skal du **vælge Åbn sikkerhedsindstillinger** eller **Åbn systemindstillingerSikkerhedsindstillinger** > **& beskyttelse** af personlige oplysninger, og vælg derefter **Tillad**.<br/><br/>6. Brug følgende Python-kommando i Bash til at køre onboardingpakken: `/usr/bin/python MicrosoftDefenderATPOnboardingMacOs.py`. <br/><br/>7. For at bekræfte at enheden er knyttet til dit firma, skal du bruge følgende Python-kommando i Bash: `mdatp health --field org_id`.<br/><br/>8. Hvis du bruger macOS 10.15 (Catalina) eller nyere, skal du give Defender for Business tilladelse til at beskytte din enhed. Gå til **SystemindstillingerSikkerhedsindstillinger** >  **&** **PrivacyPrivacyFull** >  >  **Disk Access**.  Vælg låseikonet for at foretage ændringer (nederst i dialogboksen), og vælg derefter Microsoft Defender til virksomheder (eller Defender til slutpunkt, hvis det er, hvad du ser). <br/><br/>9. Hvis du vil bekræfte, at enheden er onboardet, skal du bruge følgende kommando i Bash: `mdatp health --field real_time_protection_enabled`.    |

## <a name="microsoft-endpoint-manager"></a>Microsoft Endpoint Manager

Hvis du allerede brugte Endpoint Manager (som omfatter Microsoft Intune og Mobile Enhedshåndtering), kan du, før du fik Defender for Business, fortsætte med at bruge Endpoint Manager til at onboarde din virksomheds enheder. Med Endpoint Manager kan du onboarde computere, tablets og telefoner, herunder iOS- og Android-enheder.

Se [Tilmelding til enhed Microsoft Intune](/mem/intune/enrollment/device-enrollment).

## <a name="run-a-detection-test"></a>Kør en registreringstest

Når du har onboardet Windows-enheder til Defender for Business, kan du køre en registreringstest på en Windows-enhed for at sikre, at alt fungerer korrekt.

1. På Windows skal du oprette en mappe: `C:\test-MDATP-test`.

2. Åbn Kommandoprompt som administrator.

3. I vinduet Kommandoprompt skal du køre følgende PowerShell-kommando:

   ```powershell
   powershell.exe -NoExit -ExecutionPolicy Bypass -WindowStyle Hidden $ErrorActionPreference = 'silentlycontinue';(New-Object System.Net.WebClient).DownloadFile('http://127.0.0.1/1.exe', 'C:\\test-MDATP-test\\invoice.exe');Start-Process 'C:\\test-MDATP-test\\invoice.exe'
   ```

Når kommandoen er kørt, lukkes vinduet Kommandoprompt automatisk. Hvis det lykkes, markeres registreringstesten som fuldført, og der vises en ny besked i Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)) for den nyligt onboardede enhed på ca. 10 minutter.

## <a name="gradual-device-onboarding"></a>Gradvis onboarding af enhed

Du kan onboarde din virksomheds enheder i faser. *Vi kalder denne gradvise onboarding af enheder*. 

1. Identificer et sæt af enheder, der skal onboarde.

2. Gå til Microsoft 365 Defender -portalen ([https://security.microsoft.com](https://security.microsoft.com)), og log på.

3. I navigationsruden skal du **vælge Indstillinger** >  **Endpoints**, og derefter skal du under **Enhedshåndtering** vælge **Onboarding**.

4. Vælg et operativsystem (f.eks. **Windows 10 og 11),** og vælg derefter en onboardingmetode (f.eks. **Lokalt script**). Følg vejledningen for den metode, du har valgt.

5. Gentag denne proces for hvert sæt af enheder, du vil onboarde. 

> [!TIP]
> Du behøver ikke at bruge den samme onboardingpakke, hver gang du onboarder enheder. Du kan f.eks. bruge et lokalt script til at onboarde visse enheder, og senere kan du vælge en anden metode til at onboarde flere enheder.

## <a name="offboarding-a-device"></a>Offboarding af en enhed

Hvis du vil deaktivere en enhed, skal du benytte en af følgende fremgangsmåder:

| Operativsystem | Procedure |
|---|---|
| Windows | 1. Gå til Microsoft 365 Defender -portalen ([https://security.microsoft.com](https://security.microsoft.com)), og log på.<br/><br/>2. I navigationsruden skal **du vælge Indstillinger** og derefter **vælge Slutpunkter**.<br/><br/>3. Under **Enhedshåndtering skal** du vælge **Offboarding**.<br/><br/>4. Vælg et operativsystem, f.eks. **Windows 10 og 11**, og vælg derefter Lokalt script i sektionen Installationsmetode under  **Fraboard en enhed**. <br/><br/>5. Gennemgå oplysningerne på bekræftelsesskærmbilledet, og vælg derefter **Download for at** fortsætte.<br/><br/>6. Vælg **Download offboarding-pakke**. Vi anbefaler, at du gemmer offboarding-pakken på et flytbart drev.<br/><br/>7. Kør scriptet på hver enhed, du vil offboarde.| 
| macOS | 1. Gå **til** **FinderApplications** > . <br/><br/>2. Højreklik på Microsoft Defender til virksomheder, og vælg derefter Flyt **til Papirkurv**. <br/><br/>--- eller --- <br/><br/> Brug følgende kommando: `sudo '/Library/Application Support/Microsoft/Defender/uninstall/uninstall'`.|

> [!IMPORTANT]
> Offboarding af en enhed får enhederne til at holde op med at sende data til Defender for Business. Men data, der modtages før offboarding, bevares i op til seks (6) måneder.

## <a name="next-steps"></a>Næste trin

Fortsæt til:

- [Trin 5: Konfigurer dine sikkerhedsindstillinger og politikker i Microsoft Defender til virksomheder](mdb-configure-security-settings.md)

- [Kom i gang med at Microsoft Defender til virksomheder](mdb-get-started.md) 
