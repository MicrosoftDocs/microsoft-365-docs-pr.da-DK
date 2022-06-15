---
title: Om bord på enheder til Microsoft Defender til virksomheder
description: Se, hvordan du får enheder onboardet til Defender for Business for at beskytte dine enheder fra dag 1.
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
ms.openlocfilehash: 58b2756bead1df85e12e3276d0da475d6882b589
ms.sourcegitcommit: 66228a5506fdceb4cbf0d55b9de3f2943740134f
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/15/2022
ms.locfileid: "66088973"
---
# <a name="onboard-devices-to-microsoft-defender-for-business"></a>Om bord på enheder til Microsoft Defender til virksomheder

Med Microsoft Defender til virksomheder har du flere muligheder at vælge imellem til onboarding af din virksomheds enheder. Denne artikel fører dig gennem dine muligheder og indeholder en oversigt over, hvordan onboarding fungerer.


## <a name="what-to-do"></a>Sådan gør du

1. Vælg fanen for operativsystemet: **Windows klienter**, **macOS computere** eller **mobilenheder**.
2. Få vist dine onboardingindstillinger, og følg vejledningen på den valgte fane.
3. Fortsæt til de næste trin.

## <a name="windows-clients"></a>[**Windows klienter**](#tab/WindowsClientDevices)

## <a name="windows-clients"></a>Windows klienter

Vælg en af følgende muligheder for at onboarde Windows klientenheder til Defender for Business:

- [Lokalt script](#local-script-for-windows-clients) (til onboarding af enheder manuelt på portalen Microsoft 365 Defender)
- [Gruppepolitik](#group-policy-for-windows-clients) (hvis du allerede bruger Gruppepolitik i din organisation)
- [Microsoft Intune](#microsoft-intune-for-windows-clients) (inkluderet i [Microsoft 365 Business Premium](../../business-premium/index.md))


### <a name="local-script-for-windows-clients"></a>Lokalt script til Windows klienter

Du kan bruge et lokalt script til at onboarde Windows klientenheder. Når du kører onboardingscriptet på en enhed, oprettes der et tillidsforhold til Azure Active Directory (hvis denne tillid ikke allerede findes), tilmelder enheden Microsoft Intune (hvis den ikke allerede er tilmeldt) og onboarder derefter enheden til Defender for Business. Den lokale scriptmetode fungerer, selvom du ikke har Intune i øjeblikket. Vi anbefaler onboarding af op til 10 enheder ad gangen ved hjælp af denne metode.

> [!TIP]
> Vi anbefaler onboarding af op til 10 enheder ad gangen, når du bruger den lokale scriptmetode.

1. Gå til Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)), og log på.

2. Vælg **Indstillinger** >  **Endpoints** i navigationsruden, og vælg derefter **Onboarding** under **Enhedshåndtering**.

3. Vælg et operativsystem, f.eks **. Windows 10 og 11**, og vælg derefter **Lokalt script** i afsnittet **Installationsmetode**. 

4. Vælg **Download onboarding-pakke**. Vi anbefaler, at du gemmer onboardingpakken på et flytbart drev.

5. På en Windows enhed skal du udtrække indholdet af konfigurationspakken til en placering, f.eks. mappen Desktop. Du skal have en fil med navnet `WindowsDefenderATPLocalOnboardingScript.cmd`. 

6. Åbn kommandoprompten som administrator.

7. Skriv placeringen af scriptfilen. Hvis du f.eks. kopierede filen til mappen Desktop, skulle du skrive `%userprofile%\Desktop\WindowsDefenderATPLocalOnboardingScript.cmd`og derefter trykke på tasten Enter (eller vælge **OK**).

8. Når scriptet er kørt, skal du fortsætte med at [køre en registreringstest](#running-a-detection-test-on-a-windows-client).

### <a name="group-policy-for-windows-clients"></a>Gruppepolitik til Windows klienter

Hvis du foretrækker at bruge Gruppepolitik til at onboarde Windows klienter, skal du følge vejledningen i [Onboard Windows enheder ved hjælp af Gruppepolitik](../defender-endpoint/configure-endpoints-gp.md). I denne artikel beskrives trinnene til onboarding til Microsoft Defender for Endpoint, men trinnene til onboarding til Defender for Business er de samme.

### <a name="microsoft-intune-for-windows-clients"></a>Microsoft Intune til Windows klienter

Hvis dit abonnement omfatter Intune, kan du onboarde Windows klienter og andre enheder i Microsoft Endpoint Manager Administration ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)). Hvis du f.eks. har [Microsoft 365 Business Premium](../../business/index.yml), har du Intune som en del af dit abonnement.  

Der findes flere metoder til tilmelding af enheder i Intune. Vi anbefaler, at du starter med en af følgende metoder:

- [Aktivér Windows automatisk tilmelding](/mem/intune/enrollment/windows-enroll) til virksomhedsejede eller virksomhedsadministrerede enheder
- [Bed brugerne om at tilmelde deres egne Windows 10/11-enheder på Intune](/mem/intune/user-help/enroll-windows-10-device)

#### <a name="to-enable-automatic-enrollment-for-windows-devices"></a>Sådan aktiverer du automatisk tilmelding til Windows enheder

Når du konfigurerer automatisk tilmelding, føjer brugerne deres arbejdskonto til enheden. I baggrunden registrerer og tilmelder enheden Azure Active Directory (Azure AD) og er tilmeldt Intune.

1. Gå til Azure Portal ([https://portal.azure.com/](https://portal.azure.com/)), og log på. 

2. Vælg **Azure Active Directory** >  **Mobilitet (MDM og MAM)** > **Microsoft Intune**.

3. Konfigurer **MDM-brugeromfanget** og **MAM-brugeromfanget**.

   :::image type="content" source="media/mem-mam-scope-azure-ad.png" alt-text="Skærmbillede af angivelse af MDM-brugeromfang og MAM-brugeromfang i Intune.":::

   - I forbindelse med MDM-brugerområde anbefaler vi, at du vælger **Alle**, så alle brugere automatisk kan tilmelde deres Windows enheder.
   - I afsnittet MAM-brugerområde anbefaler vi, at du bruger følgende standardværdier for URL-adresserne:

       - **MDM Vilkår for anvendelse AF URL-adresse**
       - **URL-adresse til MDM-registrering**
       - **URL-adresse til MDM-overholdelse**

4. Vælg **Gem**.

5. Når en enhed er blevet tilmeldt Intune, kan du føje den til en enhedsgruppe. [Få mere at vide om enhedsgrupper i Microsoft Defender til virksomheder](mdb-create-edit-device-groups.md).


> [!TIP]
> Hvis du vil vide mere om automatisk tilmelding, skal du se [Aktivér Windows automatisk tilmelding](/mem/intune/enrollment/windows-enroll).

#### <a name="to-have-users-enroll-their-own-windows-devices"></a>Sådan får du brugerne til at tilmelde deres egne Windows enheder

1. Se følgende video for at se, hvordan tilmelding fungerer: <br/><br/>

   > [!VIDEO https://www.youtube.com/embed/TKQxEckBHiE?rel=0]  

2. Del denne artikel med brugere i din organisation: [Tilmeld Windows 10/11-enheder i Intune](/mem/intune/user-help/enroll-windows-10-device).

3. Når en enhed er blevet tilmeldt Intune, kan du føje den til en enhedsgruppe. [Få mere at vide om enhedsgrupper i Microsoft Defender til virksomheder](mdb-create-edit-device-groups.md).

### <a name="running-a-detection-test-on-a-windows-client"></a>Kørsel af en registreringstest på en Windows klient

Når du har onboardet Windows enheder til Defender for Business, kan du køre en registreringstest på en Windows enhed for at sikre, at alt fungerer korrekt.

1. Opret en mappe på den Windows enhed: `C:\test-MDATP-test`.

2. Åbn kommandoprompten som administrator.

3. Kør følgende PowerShell-kommando i vinduet Kommandoprompt:

   ```powershell
   powershell.exe -NoExit -ExecutionPolicy Bypass -WindowStyle Hidden $ErrorActionPreference = 'silentlycontinue';(New-Object System.Net.WebClient).DownloadFile('http://127.0.0.1/1.exe', 'C:\\test-MDATP-test\\invoice.exe');Start-Process 'C:\\test-MDATP-test\\invoice.exe'
   ```

Når kommandoen er kørt, lukkes kommandopromptvinduet automatisk. Hvis det lykkes, markeres registreringstesten som fuldført, og der vises en ny besked på portalen Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) for den nyligt onboardede enhed om ca. 10 minutter.

## <a name="view-a-list-of-onboarded-devices"></a>Få vist en liste over onboardede enheder

Hvis du vil have vist listen over enheder, der er onboardet til Defender for Business, skal du vælge **Enhedslager** i Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)) i navigationsruden under **Slutpunkter**.

## <a name="next-steps"></a>Næste trin

- Hvis du har andre enheder at onboarde, skal du vælge den fane, der svarer til operativsystemet på enhederne [(Windows klienter, Windows Server, macOS eller mobilenheder](#what-to-do)) og følge vejledningen under den pågældende fane.
- Hvis du er færdig med at onboarde enheder, skal du gå til [Trin 5: Konfigurer dine sikkerhedsindstillinger og politikker i Microsoft Defender til virksomheder](mdb-configure-security-settings.md)
- Se [Kom i gang med at bruge Microsoft Defender til virksomheder](mdb-get-started.md).

## <a name="macos"></a>[**macOS**](#tab/macOSdevices)

## <a name="macos-computers"></a>macOS computere

> [!NOTE]
> - Vi anbefaler, at du bruger et [lokalt script til at onboarde macOS enheder](#local-script-for-macos). Selvom du kan [konfigurere tilmelding for macOS enheder i Intune](/mem/intune/enrollment/macos-enroll), er det lokale script den nemmeste metode til onboarding macOS enheder til Defender for Business. 

Vælg en af følgende muligheder for at onboarde macOS enheder:

- [Lokalt script til macOS](#local-script-for-macos) (*anbefales*)
- [Intune til macOS](#microsoft-intune-for-macos)

### <a name="local-script-for-macos"></a>Lokalt script til macOS

Når du kører det lokale script på en macOS enhed, oprettes der et tillidsforhold til Azure Active Directory (hvis denne tillid ikke allerede findes), tilmeldes enheden i Microsoft Intune (hvis den ikke allerede er tilmeldt) og onboarder derefter enheden til Defender for Business. Den lokale scriptmetode fungerer, selvom du ikke har Intune i øjeblikket. Vi anbefaler onboarding af op til 10 enheder ad gangen ved hjælp af denne metode.

1. Gå til Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)), og log på.

2. Vælg **Indstillinger** >  **Endpoints** i navigationsruden, og vælg derefter **Onboarding** under **Enhedshåndtering**.

3. Vælg **macOS**, og vælg derefter **Lokalt script** i afsnittet **Installationsmetode**. 

4. Vælg **Download onboarding-pakke**, og gem den på et flytbart drev. Vælg også **Download installationspakken**, og gem den på din flytbare enhed.

5. På en macOS enhed skal du gemme installationspakken som `wdav.pkg` en lokal mappe.

6. Gem onboardingpakken som `WindowsDefenderATPOnboardingPackage.zip` i den samme mappe, som du brugte til installationspakken.

7. Brug Finder til at navigere til `wdav.pkg` dig, der er gemt, og åbn den derefter.

8. Vælg **Fortsæt**, acceptér licensvilkårene, og angiv derefter din adgangskode, når du bliver bedt om det.

9. Du bliver bedt om at tillade, at en driver fra Microsoft installeres (enten "System Extension Blocked" eller "Installation er i venteposition" eller begge dele. Driveren skal have tilladelse til at blive installeret. Hvis du vil tillade installationen, skal du vælge **Åbn sikkerhedsindstillinger** eller **Åbn systemindstillinger** > **Sikkerhed & Beskyttelse af personlige oplysninger** og derefter vælge **Tillad**.

10. Brug følgende Python-kommando i Bash til at køre onboardingpakken: `/usr/bin/python MicrosoftDefenderATPOnboardingMacOs.sh`

11. Når en enhed er blevet tilmeldt Intune, kan du føje den til en enhedsgruppe. [Få mere at vide om enhedsgrupper i Microsoft Defender til virksomheder](mdb-create-edit-device-groups.md).

### <a name="microsoft-intune-for-macos"></a>Microsoft Intune til macOS

Hvis dit abonnement omfatter Microsoft Intune, kan du onboarde macOS enheder i Microsoft Endpoint Manager Administration ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)). Hvis du f.eks. har [Microsoft 365 Business Premium](../../business/index.yml), har du Intune som en del af dit abonnement.  

Der findes flere metoder til tilmelding af enheder i Intune. Vi anbefaler, at du starter med en af følgende metoder:

- [Vælg en indstilling for virksomhedsejede macOS enheder](#options-for-company-owned-macos-devices)
- [Bed brugerne om at tilmelde deres egne macOS enheder i Intune](#ask-users-to-enroll-their-own-macos-devices-in-intune)

#### <a name="options-for-company-owned-macos-devices"></a>Indstillinger for virksomhedsejede macOS enheder

Vælg en af indstillingerne i følgende tabel for at tilmelde virksomhedsadministrerede macOS enheder i Intune:

| Mulighed  | Beskrivelse  |
|---------|---------|
| Apple Automated Device Enrollment |  Brug denne metode til at automatisere tilmeldingsoplevelsen på enheder, der er købt via Apple Business Manager eller Apple School Manager. Automatiseret tilmelding af enheder udruller tilmeldingsprofilen via internettet, så du ikke behøver at have fysisk adgang til enheder. <br/><br/>Se [Tilmeld automatisk macOS enheder med Apple Business Manager eller Apple School Manager](/mem/intune/enrollment/device-enrollment-program-enroll-macos). |
| Administrator af enhedsregistrering (DEM)  |  Brug denne metode til udrulninger i stor skala, og når der er flere personer i din organisation, som kan hjælpe med konfiguration af tilmelding. En person med administratorrettigheder til enhedsregistrering kan tilmelde op til 1.000 enheder med en enkelt Azure Active Directory konto. Denne metode bruger Firmaportal-appen eller Microsoft Intune-appen til at tilmelde enheder. Du kan ikke bruge en demografikonto til at tilmelde enheder via automatiseret enhedsregistrering.<br/><br/> Se [Tilmeld enheder i Intune ved hjælp af en administratorkonto til enhedsregistrering](/mem/intune/enrollment/device-enrollment-manager-enroll).  |
| Direkte tilmelding  | Direkte tilmelding tilmelder enheder uden brugertilhør, så denne metode er bedst til enheder, der ikke er knyttet til en enkelt bruger. Denne metode kræver, at du har fysisk adgang til de Macs, du tilmelder dig. <br/><br/>Se [Brug direkte tilmelding til macOS enheder](/mem/intune/enrollment/device-enrollment-direct-enroll-macos).      |

#### <a name="ask-users-to-enroll-their-own-macos-devices-in-intune"></a>Bed brugerne om at tilmelde deres egne macOS enheder i Intune

Hvis din virksomhed foretrækker at få personer til at tilmelde deres egne enheder i Intune, skal du bede brugerne om at følge disse trin:

1. Gå til webstedet Firmaportal ([https://portal.manage.microsoft.com/](https://portal.manage.microsoft.com/)), og log på.

2. Følg vejledningen på Firmaportal websted for at tilføje deres enhed.

3. Installér Firmaportal-appen på [https://aka.ms/EnrollMyMac](https://aka.ms/EnrollMyMac), og følg vejledningen i appen.

### <a name="confirm-that-a-macos-device-is-onboarded"></a>Bekræft, at en macOS enhed er onboardet

1. Hvis du vil bekræfte, at enheden er knyttet til dit firma, skal du bruge følgende Python-kommando i Bash: `mdatp health --field org_id`.

2. Hvis du bruger macOS 10.15 (Catalina) eller nyere, skal du give Defender for Business-samtykke for at beskytte din enhed. Gå til **Systemindstillinger** > **Sikkerhed & Beskyttelse af personlige oplysninger** >  > **Fuld diskadgang**. Vælg låseikonet for at foretage ændringer (nederst i dialogboksen), og vælg derefter **Microsoft Defender til virksomheder** (eller **Defender for Endpoint**, hvis det er det, du ser).

3. Hvis du vil bekræfte, at enheden er onboardet, skal du bruge følgende kommando i Bash: `mdatp health --field real_time_protection_enabled`

4. Når en enhed er blevet tilmeldt Intune, kan du føje den til en enhedsgruppe. [Få mere at vide om enhedsgrupper i Microsoft Defender til virksomheder](mdb-create-edit-device-groups.md).

## <a name="view-a-list-of-onboarded-devices"></a>Få vist en liste over onboardede enheder

Hvis du vil have vist listen over enheder, der er onboardet til Defender for Business, skal du vælge **Enhedslager** i Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)) i navigationsruden under **Slutpunkter**.

## <a name="next-steps"></a>Næste trin

- Hvis du har andre enheder at onboarde, skal du vælge den fane, der svarer til operativsystemet på enhederne ([Windows klienter, Windows Server, macOS eller mobilenheder](#what-to-do)) og følge vejledningen under den pågældende fane.
- Hvis du er færdig med at onboarde enheder, skal du gå til [Trin 5: Konfigurer dine sikkerhedsindstillinger og politikker i Microsoft Defender til virksomheder](mdb-configure-security-settings.md)
- Se [Kom i gang med at bruge Microsoft Defender til virksomheder](mdb-get-started.md).

## <a name="mobile-devices"></a>[**mobilenheder**](#tab/mobiles)

## <a name="mobile-devices"></a>Mobilenheder

Du skal bruge Microsoft Intune til at onboarde mobilenheder, f.eks. Android- og iOS-/iPadOS-enheder. Hvis du har [Microsoft 365 Business Premium](../../business/index.yml), har du Intune. 

Se følgende ressourcer for at få hjælp til at tilmelde disse enheder til Intune:

- [Tilmeld Android-enheder](/mem/intune/enrollment/android-enroll)
- [Tilmeld iOS- eller iPadOS-enheder](/mem/intune/enrollment/ios-enroll)

Når en enhed er blevet tilmeldt Intune, kan du føje den til en enhedsgruppe. [Få mere at vide om enhedsgrupper i Microsoft Defender til virksomheder](mdb-create-edit-device-groups.md).

## <a name="next-steps"></a>Næste trin

- Hvis du har andre enheder at onboarde, skal du vælge den fane, der svarer til operativsystemet på enhederne ([Windows klienter, Windows Server, macOS eller mobilenheder](#what-to-do)) og følge vejledningen under den pågældende fane.
- Hvis du er færdig med at onboarde enheder, skal du gå til [Trin 5: Konfigurer dine sikkerhedsindstillinger og politikker i Microsoft Defender til virksomheder](mdb-configure-security-settings.md)
- Se [Kom i gang med at bruge Microsoft Defender til virksomheder](mdb-get-started.md).
