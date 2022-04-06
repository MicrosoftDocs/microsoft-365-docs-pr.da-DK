---
title: Tilpas styret mappeadgang
description: Tilføj andre mapper, der skal være beskyttet af styret mappeadgang, eller tillad apps, der fejlagtigt blokerer ændringer af vigtige filer.
keywords: Styret mappeadgang, windows 10, windows 11, windows defender, ransomware, beskyt, filer, mapper, tilpas, tilføj mappe, tilføj app, tillad, tilføj eksekverbar
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
ms.openlocfilehash: 04e7617825a3e14eac541b296cbed9f4dd95e206
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64469311"
---
# <a name="customize-controlled-folder-access"></a>Tilpas styret mappeadgang

**Gælder for:**
- [Microsoft Defender for Endpoint plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> [!TIP]
> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

Kontrolleret mappeadgang hjælper dig med at beskytte værdifulde data mod skadelige apps og trusler, f.eks ransomware. Kontrolleret mappeadgang understøttes Windows Server 2019, Windows Server 2022, Windows 10 og Windows 11 klienter. I denne artikel beskrives det, hvordan du kan tilpasse funktioner for styret mappeadgang, og du kan læse følgende afsnit:

- [Beskyt flere mapper](#protect-additional-folders)
- [Tilføje apps, der skal have adgang til beskyttede mapper](#allow-specific-apps-to-make-changes-to-controlled-folders)
- [Tillad signerede eksekverbare filer at få adgang til beskyttede mapper](#allow-signed-executable-files-to-access-protected-folders)
- [Tilpasse meddelelsen](#customize-the-notification)

> [!IMPORTANT]
> Kontrolleret mappeadgang overvåger apps til aktiviteter, der er registreret som skadelige. Nogle gange blokeres legitime apps fra at foretage ændringer i dine filer. Hvis kontrolleret mappeadgang påvirker din organisations produktivitet, kan du overveje at køre denne funktion i [overvågningstilstand](audit-windows-defender.md) for at vurdere påvirkningen fuldt ud.

## <a name="protect-additional-folders"></a>Beskyt flere mapper

Styret mappeadgang gælder for mange systemmapper og standardplaceringer, herunder mapper som **Dokumenter****, Billeder** og **Film**. Du kan tilføje andre mapper, der skal være beskyttede, men du kan ikke fjerne standardmapperne på standardlisten.

Det kan være nyttigt at føje andre mapper til kontrolleret mappeadgang, når du ikke gemmer filer i standardbibliotekerne i Windows, eller hvis du har ændret standardplaceringen for dine biblioteker.

Du kan også angive netværksshares og tilknyttede drev. Miljøvariabler og jokertegn understøttes. Du kan finde oplysninger om brug af jokertegn i [Brug jokertegn i filnavnet og mappestien eller udeladelseslister for filtypenavnet](configure-extension-file-exclusions-microsoft-defender-antivirus.md).

Du kan bruge Windows Sikkerhed-appen, Gruppepolitik, PowerShell-cmdlet'er eller konfigurationstjenesteudbydere til administration af mobilenheder til at tilføje og fjerne beskyttede mapper.

### <a name="use-the-windows-security-app-to-protect-additional-folders"></a>Brug appen Windows Sikkerhed til at beskytte flere mapper

1. Åbn appen Windows Sikkerhed ved at vælge skjoldikonet på proceslinjen eller ved at *søge efter sikkerhed* i menuen Start.

2. Vælg **Virusbeskyttelse & trusselsbeskyttelse**, og rul derefter ned til **afsnittet Beskyttelse mod ransomware** .

3. Vælg **Administrer ransomware-beskyttelse** for at åbne **ruden beskyttelse mod ransomware** .

4. Under sektionen **Kontrolleret mappeadgang** skal du **vælge Beskyttede mapper**.

5. Vælg **Ja** i **Access Control** brugeroplysninger. **Ruden Beskyttede mapper** vises.

6. Vælg **Tilføj en beskyttet mappe,** og følg instruktionerne for at tilføje mapper.

### <a name="use-group-policy-to-protect-additional-folders"></a>Brug Gruppepolitik til at beskytte flere mapper

1. På Gruppepolitik administrationscomputer skal du åbne [Gruppepolitik administrationskonsollen](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)?preserve=true). 

2. Højreklik på det Gruppepolitik objekt, du vil konfigurere, og vælg derefter **Rediger**.

3. I din **Gruppepolitik Administration skal** du gå til **Administrative skabeloner for politikker for** \>  \> **computerkonfiguration**.

4. Udvid træet for **at Windows adgang til** \> **Microsoft Defender Antivirus** \> **Windows Defender Exploit** **Guard-kontrolleret**\> mappeadgang. <br/>**BEMÆRK**! I ældre versioner af Windows vises den muligvis **som Windows Defender Antivirus** i stedet for **Microsoft Defender Antivirus**.

5. Dobbeltklik på **Konfigurerede beskyttede mapper, og** angiv derefter indstillingen til **Aktiveret**. Vælg **Vis**, og angiv hver mappe, du vil beskytte.

6. Installér dit Gruppepolitik-objekt, som du normalt gør det.

### <a name="use-powershell-to-protect-additional-folders"></a>Brug PowerShell til at beskytte flere mapper

1. Skriv **PowerShell** i menuen Start, **højreklik på Windows PowerShell** og vælg **Kør som administrator**

2. Skriv følgende PowerShell-cmdlet, der erstatter `<the folder to be protected>` med mappens sti (f.eks `"c:\apps\"`.):

    ```PowerShell
    Add-MpPreference -ControlledFolderAccessProtectedFolders "<the folder to be protected>"
    ```
3. Gentag trin 2 for hver mappe, du vil beskytte. Mapper, der er beskyttet, er synlige i Windows Sikkerhed appen.

   :::image type="content" source="images/cfa-allow-folder-ps.png" alt-text="PowerShell-vinduet med cmdlet vist" lightbox="images/cfa-allow-folder-ps.png":::

> [!IMPORTANT]
> Bruges `Add-MpPreference` til at tilføje eller føje apps til listen og ikke `Set-MpPreference`. Hvis du `Set-MpPreference` bruger cmdlet'en, overskrives den eksisterende liste.

### <a name="use-mdm-csps-to-protect-additional-folders"></a>Bruge MDM-CSP'er til at beskytte flere mapper

Brug [konfigurationskonfigurationen ./Vendor/MSFT/Policy/Config/Defender/GuardedFoldersList](/windows/client-management/mdm/policy-csp-defender#defender-guardedfolderslist) serviceudbyder (CSP) til at tillade, at apps foretager ændringer i beskyttede mapper.

## <a name="allow-specific-apps-to-make-changes-to-controlled-folders"></a>Tillad, at bestemte apps foretager ændringer i kontrollerede mapper

Du kan angive, om visse apps altid betragtes som sikre, og give skriveadgang til filer i beskyttede mapper. Det kan være nyttigt at tillade apps, hvis en bestemt app, som du kender og har tillid til, blokeres af funktionen styret mappeadgang.

> [!IMPORTANT]
> Som standard føjer Windows apps, der betragtes som brugervenlige, til listen over tilladte. Sådanne apps, der tilføjes automatisk, optages ikke på den liste, der vises i Windows Sikkerhed-appen eller ved hjælp af de tilknyttede PowerShell-cmdlet'er. Det er ikke nødvendigt at tilføje de fleste apps. Tilføj kun apps, hvis de blokeres, og du kan bekræfte deres pålidelighed.

Når du tilføjer en app, skal du angive appens placering. Det er kun appen på den pågældende placering, der har tilladelse til at få adgang til de beskyttede mapper. Hvis appen (med samme navn) er på en anden placering, føjes den ikke til tilladelseslisten, og den blokeres muligvis af styret mappeadgang.

Et tilladt program eller en tilladt tjeneste har kun skriveadgang til en kontrolleret mappe, når den starter. Eksempelvis fortsætter en opdateringstjeneste med at udløse hændelser, efter den er tilladt, indtil den stoppes og genstartes.

### <a name="use-the-windows-defender-security-app-to-allow-specific-apps"></a>Brug appen Windows Defender til at tillade bestemte apps

1. Åbn appen Windows Sikkerhed ved at søge efter Sikkerhed i menuen **Start**.

2. Vælg **flisen & virusbeskyttelse** (eller skjoldikonet på venstre menulinje), og vælg derefter **Administrer beskyttelse mod ransomware**.

3. Under sektionen **Kontrolleret mappeadgang** skal du vælge **Tillad en app via styret mappeadgang**

4. Vælg **Tilføj en tilladt app,** og følg instruktionerne for at tilføje apps.

   :::image type="content" source="images/cfa-allow-app.png" alt-text="Knappen Tilføj en tilladt app" lightbox="images/cfa-allow-app.png":::

### <a name="use-group-policy-to-allow-specific-apps"></a>Brug Gruppepolitik til at tillade bestemte apps

1. På Gruppepolitik administrationsenhed skal du åbne [Gruppepolitik Administrationskonsol](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)?preserve=true), højreklikke på det Gruppepolitik objekt, du vil konfigurere, og vælge **Rediger**.

2. I **administrationseditoren Gruppepolitik** skal du gå **til Computerkonfiguration** og vælge **Administrative skabeloner**.

3. Udvid træet for **at Windows adgang til** \> **Microsoft Defender Antivirus** \> **Windows Defender Exploit** **Guard-kontrolleret**\> mappeadgang.

4. Dobbeltklik på indstillingen Konfigurer **tilladte programmer** , og angiv indstillingen til **Aktiveret**. Vælg **Vis,** og angiv hver app.

### <a name="use-powershell-to-allow-specific-apps"></a>Brug PowerShell til at tillade bestemte apps

1. Skriv **PowerShell** i menuen Start, **højreklik på Windows PowerShell** og vælg **Kør som administrator**
2. Angiv følgende cmdlet:

    ```PowerShell
    Add-MpPreference -ControlledFolderAccessAllowedApplications "<the app that should be allowed, including the path>"
    ```

    Hvis du f.eks. vil tilføje *den eksekverbaretest.exe* i *mappen C:\apps*, skal cmdlet'en være som følger:

    ```PowerShell
    Add-MpPreference -ControlledFolderAccessAllowedApplications "c:\apps\test.exe"
    ```

   Fortsæt med at `Add-MpPreference -ControlledFolderAccessAllowedApplications` bruge til at føje flere apps til listen. Apps, der tilføjes ved hjælp af denne cmdlet, vises i Windows Sikkerhed appen.

   :::image type="content" source="images/cfa-allow-app-ps.png" alt-text="PowerShell-cmdlet'en til at tillade et program" lightbox="images/cfa-allow-app-ps.png":::

> [!IMPORTANT]
> Bruges `Add-MpPreference` til at tilføje eller føje apps til listen. Hvis du `Set-MpPreference` bruger cmdlet'en, overskrives den eksisterende liste.

### <a name="use-mdm-csps-to-allow-specific-apps"></a>Brug MDM-CSP'er til at tillade bestemte apps

Brug [konfigurationen ./Vendor/MSFT/Policy/Config/Defender/GuardedFoldersAllowedApplications](/windows/client-management/mdm/policy-csp-defender#defender-guardedfoldersallowedapplications) serviceudbyder (CSP) til at tillade, at apps foretager ændringer i beskyttede mapper.

## <a name="allow-signed-executable-files-to-access-protected-folders"></a>Tillad signerede eksekverbare filer at få adgang til beskyttede mapper

Microsoft Defender for Endpoint certifikat- og filindikatorer kan tillade signerede eksekverbare filer at få adgang til beskyttede mapper. Du kan få mere at vide [om implementeringen under Opret indikatorer, der er baseret på certifikater](indicator-certificates.md).

> [!Note]
> Dette gælder ikke for scripting-søgemaskiner, herunder Powershell

## <a name="customize-the-notification"></a>Tilpasse meddelelsen

Du kan finde flere oplysninger om tilpasning af meddelelsen, når en regel udløses og blokerer en app eller fil, under Konfigurer beskeder [om beskeder Microsoft Defender for Endpoint](configure-email-notifications.md).

## <a name="see-also"></a>Se også

- [Beskyt vigtige mapper med styret mappeadgang](controlled-folders.md)
- [Aktivér styret mappeadgang](enable-controlled-folders.md)
- [Evaluer regler for reduktion af angrebsoverfladen](evaluate-attack-surface-reduction.md)
