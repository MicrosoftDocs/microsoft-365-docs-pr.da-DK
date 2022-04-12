---
title: Tilpas styret mappeadgang
description: Tilføj andre mapper, der skal beskyttes af kontrolleret mappeadgang, eller tillad apps, der fejlagtigt blokerer ændringer af vigtige filer.
keywords: Kontrolleret mappeadgang, Windows 10, Windows 11, Windows Defender, ransomware, beskytte, filer, mapper, tilpasse, tilføje mappe, tilføje app, tillade, tilføje eksekverbar
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
audience: ITPro
author: denisebmsft
ms.author: deniseb
ms.reviewer: oogunrinde, dbodorin, vladiso, nixanm, anvascon
manager: dansimp
ms.technology: mde
ms.topic: how-to
ms.collection: M365-security-compliance
ms.date: ''
ms.openlocfilehash: 5b941cf40a220f2d9298a4918d334349f784dd13
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/12/2022
ms.locfileid: "64789882"
---
# <a name="customize-controlled-folder-access"></a>Tilpas styret mappeadgang

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- Microsoft Defender Antivirus

**Platforme**
- Windows

> [!TIP]
> Vil du gerne opleve Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

Kontrolleret mappeadgang hjælper dig med at beskytte værdifulde data mod skadelige apps og trusler, f.eks. ransomware. Kontrolleret mappeadgang understøttes på Windows Server 2019, Windows Server 2022, Windows 10 og Windows 11 klienter. I denne artikel beskrives det, hvordan du tilpasser egenskaber for kontrolleret mappeadgang, og den indeholder følgende afsnit:

- [Beskyt yderligere mapper](#protect-additional-folders)
- [Tilføj apps, der skal have adgang til beskyttede mapper](#allow-specific-apps-to-make-changes-to-controlled-folders)
- [Tillad, at signerede eksekverbare filer får adgang til beskyttede mapper](#allow-signed-executable-files-to-access-protected-folders)
- [Tilpas meddelelsen](#customize-the-notification)

> [!IMPORTANT]
> Adgang til kontrollerede mapper overvåger apps for aktiviteter, der registreres som skadelige. Nogle gange blokeres legitime apps fra at foretage ændringer af dine filer. Hvis kontrolleret mappeadgang påvirker din organisations produktivitet, kan du overveje at køre denne funktion i [overvågningstilstand](audit-windows-defender.md) for fuldt ud at vurdere virkningen.

## <a name="protect-additional-folders"></a>Beskyt yderligere mapper

Kontrolleret mappeadgang gælder for mange systemmapper og standardplaceringer, herunder mapper som **dokumenter**, **billeder** og **film**. Du kan tilføje andre mapper, der skal beskyttes, men du kan ikke fjerne standardmapperne på standardlisten.

Tilføjelse af andre mapper til kontrolleret mappeadgang kan være nyttigt i tilfælde, hvor du ikke gemmer filer i standard-Windows biblioteker, eller du har ændret standardplaceringen af dine biblioteker.

Du kan også angive netværksshares og tilknyttede drev. Miljøvariabler og jokertegn understøttes. Du kan få oplysninger om, hvordan du bruger jokertegn, [under Brug jokertegn i filnavnet og mappestien eller på listen over filtypenavne](configure-extension-file-exclusions-microsoft-defender-antivirus.md).

Du kan bruge tjenesteudbyderen Windows Sikkerhed app, Gruppepolitik, PowerShell-cmdlet'er eller tjenesteudbydere til konfiguration af mobilenheder til at tilføje og fjerne beskyttede mapper.

### <a name="use-the-windows-security-app-to-protect-additional-folders"></a>Brug appen Windows Sikkerhed til at beskytte yderligere mapper

1. Åbn appen Windows Sikkerhed ved at vælge skjoldikonet på proceslinjen eller ved at søge efter *sikkerhed* i menuen Start.

2. Vælg **Virus & trusselsbeskyttelse**, og rul derefter ned til afsnittet **Om ransomware-beskyttelse** .

3. Vælg **Administrer ransomware-beskyttelse** for at åbne ruden **Ransomware-beskyttelse** .

4. Under afsnittet **Adgang til kontrolleret mappe** skal du vælge **Beskyttede mapper**.

5. Vælg **Ja** i **prompten Bruger Access Control**. Ruden **Beskyttede mapper** vises.

6. Vælg **Tilføj en beskyttet mappe** , og følg prompterne for at tilføje mapper.

### <a name="use-group-policy-to-protect-additional-folders"></a>Brug Gruppepolitik til at beskytte yderligere mapper

1. Åbn [administrationskonsollen for Gruppepolitik på administrationscomputeren til Gruppepolitik](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)?preserve=true). 

2. Højreklik på det Gruppepolitik objekt, du vil konfigurere, og vælg derefter **Rediger**.

3. I **editoren til administration af Gruppepolitik** skal du gå til **Computerkonfigurationspolitikker** \>  \> **Administrative skabeloner**.

4. Udvid træet for at **Windows komponenter** \> **Microsoft Defender Antivirus** \> Windows Defender **adgang til mappen Exploit** **Guard** \> Controlled. <br/>**BEMÆRK**! På ældre versioner af Windows kan du muligvis se **Windows Defender Antivirus** i stedet for **Microsoft Defender Antivirus**.

5. Dobbeltklik på **Konfigurerede beskyttede mapper**, og angiv derefter indstillingen til **Aktiveret**. Vælg **Vis**, og angiv de mapper, du vil beskytte.

6. Udrul dit Gruppepolitik-objekt, som du normalt gør.

### <a name="use-powershell-to-protect-additional-folders"></a>Brug PowerShell til at beskytte yderligere mapper

1. Skriv **PowerShell** i menuen Start, højreklik **Windows PowerShell**, og vælg **Kør som administrator**

2. Skriv følgende PowerShell-cmdlet, der erstatter `<the folder to be protected>` med mappens sti (f.eks. `"c:\apps\"`):

    ```PowerShell
    Add-MpPreference -ControlledFolderAccessProtectedFolders "<the folder to be protected>"
    ```
3. Gentag trin 2 for hver mappe, du vil beskytte. Mapper, der er beskyttet, er synlige i appen Windows Sikkerhed.

   :::image type="content" source="images/cfa-allow-folder-ps.png" alt-text="PowerShell-vinduet med den viste cmdlet" lightbox="images/cfa-allow-folder-ps.png":::

> [!IMPORTANT]
> Bruges `Add-MpPreference` til at tilføje eller føje apps til listen og ikke `Set-MpPreference`til . Hvis du bruger cmdlet'en `Set-MpPreference` , overskrives den eksisterende liste.

### <a name="use-mdm-csps-to-protect-additional-folders"></a>Brug MDM CSP'er til at beskytte yderligere mapper

Brug [./Vendor/MSFT/Policy/Config/Defender/GuardedFoldersList](/windows/client-management/mdm/policy-csp-defender#defender-guardedfolderslist) CSP (Configuration Service Provider) til at tillade, at apps foretager ændringer af beskyttede mapper.

## <a name="allow-specific-apps-to-make-changes-to-controlled-folders"></a>Tillad, at bestemte apps foretager ændringer i styrede mapper

Du kan angive, om visse apps altid betragtes som sikre, og give skriveadgang til filer i beskyttede mapper. Det kan være nyttigt at tillade apps, hvis en bestemt app, du kender og har tillid til, blokeres af adgangsfunktionen til den styrede mappe.

> [!IMPORTANT]
> Som standard føjer Windows apps, der betragtes som brugervenlige, til listen over tilladte. Sådanne apps, der tilføjes automatisk, registreres ikke på den liste, der vises i appen Windows Sikkerhed eller ved hjælp af de tilknyttede PowerShell-cmdlet'er. Du skal ikke tilføje de fleste apps. Tilføj kun apps, hvis de blokeres, og du kan bekræfte deres troværdighed.

Når du tilføjer en app, skal du angive appens placering. Det er kun appen på denne placering, der har adgang til de beskyttede mapper. Hvis appen (med samme navn) er på en anden placering, føjes den ikke til listen over tilladte og kan blokeres af kontrolleret mappeadgang.

Et tilladt program eller en tilladt tjeneste har kun skriveadgang til en kontrolleret mappe, når den starter. En opdateringstjeneste vil f.eks. fortsætte med at udløse hændelser, når den er tilladt, indtil den stoppes og genstartes.

### <a name="use-the-windows-defender-security-app-to-allow-specific-apps"></a>Brug appen Windows Defender Security til at tillade bestemte apps

1. Åbn appen Windows Sikkerhed ved at søge i menuen Start efter **Sikkerhed**.

2. Vælg feltet **Virus & threat protection** (eller skjoldikonet på menulinjen til venstre), og vælg derefter **Administrer ransomware-beskyttelse**.

3. Under afsnittet **Adgang til kontrolleret mappe** skal du vælge **Tillad en app via adgang til kontrollerede mapper**

4. Vælg **Tilføj en tilladt app** , og følg prompterne for at tilføje apps.

   :::image type="content" source="images/cfa-allow-app.png" alt-text="Knappen Tilføj en tilladt app" lightbox="images/cfa-allow-app.png":::

### <a name="use-group-policy-to-allow-specific-apps"></a>Brug Gruppepolitik til at tillade bestemte apps

1. Åbn [administrationskonsollen for Gruppepolitik](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)?preserve=true) på din Gruppepolitik-administrationsenhed, højreklik på det Gruppepolitik objekt, du vil konfigurere, og vælg **Rediger**.

2. I **editoren til Gruppepolitik administration** skal du gå til **Computerkonfiguration** og vælge **Administrative skabeloner**.

3. Udvid træet for at **Windows komponenter** \> **Microsoft Defender Antivirus** \> Windows Defender **adgang til mappen Exploit** **Guard** \> Controlled.

4. Dobbeltklik på indstillingen **Konfigurer tilladte programmer** , og angiv indstillingen til **Aktiveret**. Vælg **Vis** , og angiv hver app.

### <a name="use-powershell-to-allow-specific-apps"></a>Brug PowerShell til at tillade bestemte apps

1. Skriv **PowerShell** i menuen Start, højreklik **Windows PowerShell**, og vælg **Kør som administrator**
2. Angiv følgende cmdlet:

    ```PowerShell
    Add-MpPreference -ControlledFolderAccessAllowedApplications "<the app that should be allowed, including the path>"
    ```

    Hvis du f.eks. vil tilføje den eksekverbare *test.exe* , der er placeret i mappen *C:\apps*, vil cmdlet'en være som følger:

    ```PowerShell
    Add-MpPreference -ControlledFolderAccessAllowedApplications "c:\apps\test.exe"
    ```

   Fortsæt med at bruge `Add-MpPreference -ControlledFolderAccessAllowedApplications` til at føje flere apps til listen. Apps, der tilføjes ved hjælp af denne cmdlet, vises i appen Windows Sikkerhed.

   :::image type="content" source="images/cfa-allow-app-ps.png" alt-text="PowerShell-cmdlet'en, der tillader et program" lightbox="images/cfa-allow-app-ps.png":::

> [!IMPORTANT]
> Bruges `Add-MpPreference` til at tilføje eller føje apps til listen. Hvis du bruger cmdlet'en `Set-MpPreference` , overskrives den eksisterende liste.

### <a name="use-mdm-csps-to-allow-specific-apps"></a>Brug MDM CSP'er til at tillade bestemte apps

Brug [./Vendor/MSFT/Policy/Config/Defender/GuardedFoldersAllowedApplications](/windows/client-management/mdm/policy-csp-defender#defender-guardedfoldersallowedapplications) CSP (Configuration Service Provider) til at tillade apps at foretage ændringer af beskyttede mapper.

## <a name="allow-signed-executable-files-to-access-protected-folders"></a>Tillad, at signerede eksekverbare filer får adgang til beskyttede mapper

Microsoft Defender for Endpoint indikatorer for certifikater og filer kan give signerede eksekverbare filer adgang til beskyttede mapper. Du kan finde oplysninger om implementering under [Opret indikatorer baseret på certifikater](indicator-certificates.md).

> [!Note]
> Dette gælder ikke for scriptingprogrammer, herunder Powershell

## <a name="customize-the-notification"></a>Tilpas meddelelsen

Du kan få flere oplysninger om tilpasning af meddelelsen, når en regel udløses, og blokerer en app eller fil i [Konfigurer beskedmeddelelser i Microsoft Defender for Endpoint](configure-email-notifications.md).

## <a name="see-also"></a>Se også

- [Beskyt vigtige mapper med kontrolleret mappeadgang](controlled-folders.md)
- [Aktivér styret mappeadgang](enable-controlled-folders.md)
- [Evaluer regler for reduktion af angrebsoverfladen](evaluate-attack-surface-reduction.md)
