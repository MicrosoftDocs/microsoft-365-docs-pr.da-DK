---
title: Aktivér styret mappeadgang
keywords: Styret mappeadgang, windows 10, windows 11, windows defender, ransomware, beskyt, filer, mapper, aktivér, aktivér, brug
description: Få mere at vide om, hvordan du beskytter dine vigtige filer ved at aktivere styret mappeadgang
ms.prod: m365-security
ms.topic: article
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
audience: ITPro
author: dansimp
ms.author: dansimp
ms.reviewer: oogunrinde, sugamar
manager: dansimp
ms.technology: mde
ms.collection: m365-security-compliance
ms.date: ''
ms.openlocfilehash: b62ff851cbee58cf3b29a2b4dde6fb1b6107dd85
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64472809"
---
# <a name="enable-controlled-folder-access"></a>Aktivér styret mappeadgang

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

[Kontrolleret mappeadgang](controlled-folders.md) hjælper dig med at beskytte værdifulde data mod skadelige apps og trusler, f.eks ransomware. Styret mappeadgang følger med Windows 10, Windows 11 og Windows Server 2019. Kontrolleret mappeadgang følger også med som en del af den moderne[, samlede løsning til Windows Server 2012R2 og 2016](/microsoft-365/security/defender-endpoint/configure-server-endpoints#new-functionality-in-the-modern-unified-solution-for-windows-server-2012-r2-and-2016-preview).

Du kan aktivere styret mappeadgang ved hjælp af en af disse metoder:

- [Windows Sikkerhed app *](#windows-security-app)
- [Microsoft Endpoint Manager](#endpoint-manager)
- [Mobildata Enhedshåndtering (MDM)](#mobile-device-management-mdm)
- [Microsoft Endpoint Configuration Manager](#microsoft-endpoint-configuration-manager)
- [Gruppepolitik](#group-policy)
- [PowerShell](#powershell)

[I overvågningstilstand](evaluate-controlled-folder-access.md) kan du teste, hvordan funktionen fungerer (og gennemse hændelser), uden at det påvirker den normale brug af enheden.

Gruppepolitik, der deaktiverer fletning af lokale administratorlisten, tilsidesætter indstillinger for kontrolleret mappeadgang. De tilsidesætter også beskyttede mapper og tilladte apps, der er angivet af den lokale administrator via styret mappeadgang. Disse politikker omfatter:

- Microsoft Defender Antivirus Konfigurer **den lokale administrators flettefunktionsmåde for lister**
- System Center Endpoint Protection **Tillad brugere at tilføje udeladelse og tilsidesættelser**

Du kan finde flere oplysninger om deaktivering af lokal listefletning [under Forebyd eller tillad brugere lokalt at redigere politikindstillinger for Microsoft Defender AV](/windows/security/threat-protection/microsoft-defender-antivirus/configure-local-policy-overrides-microsoft-defender-antivirus).

## <a name="windows-security-app"></a>Windows Sikkerhed app

1. Åbn Windows Sikkerhed-appen ved at vælge skjoldet på proceslinjen. Du kan også søge efter oplysninger i **menuen start Windows Sikkerhed**.

2. Vælg **flisen & virusbeskyttelse** (eller skjoldikonet på den venstre menulinje), og vælg derefter **Ransomware-beskyttelse**.

3. Sæt parameteren **kontrolleret mappeadgang** til **Til**.

> [!NOTE]
> *Denne metode er ikke tilgængelig på Windows Server 2012R2 eller 2016.
> 
> Hvis styret mappeadgang er konfigureret med Gruppepolitik,PowerShell- eller MDM-CSP'er, ændres tilstanden i Windows Sikkerhed-appen efter genstart af enheden.
> Hvis funktionen er indstillet **til overvågningstilstand** med nogen af disse værktøjer, viser appen Windows Sikkerhed **tilstanden Fra.**
> Hvis du beskytter brugerprofildata, anbefaler vi, at brugerprofilen skal være på Windows-installationsdrevet.

## <a name="endpoint-manager"></a>Endpoint Manager

1. Log [på Endpoint Manager og](https://endpoint.microsoft.com) åbn **Slutpunktssikkerhed**.

2. Gå til **politik for reduktion af** **angrebsoverfladen**\>.

3. Vælg **Platform**, vælg **Windows 10 og nyere**, og vælg profilen **Regler for reduktion af angrebsoverfladen** \> **Opret**.

4. Navngive politikken og tilføje en beskrivelse. Vælg **Næste**.

5. Rul ned til bunden, vælg **rullemenuen Aktivér** mappebeskyttelse, og vælg **Aktivér**.

6. Vælg **Liste over yderligere mapper, der skal være beskyttet,** og tilføj de mapper, der skal være beskyttet.

7. Vælg **Liste over apps, der har adgang til beskyttede mapper, og** tilføj de apps, der har adgang til beskyttede mapper.

8. Vælg **Ekskluder filer og stier** fra reduktionsregler for angrebsoverfladen, og tilføj de filer og stier, der skal udelukkes fra reglerne for reduktion af angrebsoverfladen.

9. Vælg profilen **Opgaver**, tildel til **Alle brugere & Alle enheder**, og vælg **Gem**.

10. Vælg **Næste for** at gemme hver åben blade og derefter **Opret**.

    > [!NOTE]
    > Jokertegn understøttes for programmer, men ikke for mapper. Undermapper er ikke beskyttede. Tilladte apps fortsætter med at udløse hændelser, indtil de genstartes.

## <a name="mobile-device-management-mdm"></a>Mobildata Enhedshåndtering (MDM)

Brug [konfigurationen ./Vendor/MSFT/Policy/Config/ControlledFolderAccessProtectedFolders](/windows/client-management/mdm/policy-csp-defender) serviceudbyder (CSP) til at tillade, at apps foretager ændringer i beskyttede mapper.

## <a name="microsoft-endpoint-configuration-manager"></a>Microsoft Endpoint Configuration Manager

1. I Microsoft Endpoint Configuration Manager skal du gå **til Assets and Compliance Endpoint Protection** \>  \> **Windows Defender Exploit Guard**.

2. Vælg **Home** \> **Create Exploit Guard-politik**.

3. Angiv et navn og en beskrivelse, vælg **Kontrolleret mappeadgang**, og vælg **Næste**.

4. Vælg, om du vil blokere eller overvåge ændringer, tillade andre apps eller tilføje andre mapper, og vælg **Næste**.

   > [!NOTE]
   > Jokertegn understøttes for programmer, men ikke for mapper. Undermapper er ikke beskyttede. Tilladte apps fortsætter med at udløse hændelser, indtil de genstartes.

5. Gennemse indstillingerne, og vælg **Næste for** at oprette politikken.

6. Luk, når politikken er **oprettet**.

## <a name="group-policy"></a>Gruppepolitik

1. På Gruppepolitik administrationsenhed skal du åbne [Gruppepolitik Administrationskonsol](https://technet.microsoft.com/library/cc731212.aspx), højreklikke på det Gruppepolitik objekt, du vil konfigurere, og vælge **Rediger**.

2. I **administrationseditoren Gruppepolitik** skal du gå **til Computerkonfiguration** og vælge **Administrative skabeloner**.

3. Udvid træet til **at Windows komponenter > Microsoft Defender Antivirus > Windows Defender Exploit Guard > kontrolleret mappeadgang**.

4. Dobbeltklik på indstillingen Konfigurer **styret mappeadgang,** og angiv indstillingen til **Aktiveret**. I sektionen Indstillinger skal du angive en af følgende indstillinger:
   - **Aktivér** – Ondsindede og mistænkelige apps kan ikke foretage ændringer i filer i beskyttede mapper. Der vises en meddelelse i Windows hændelsesloggen.
   - **Deaktiver (standard)** – Funktionen Kontrolleret mappeadgang virker ikke. Alle apps kan foretage ændringer i filer i beskyttede mapper.
   - **Overvågningstilstand** – Ændringer er tilladt, hvis en skadelig eller mistænkelig app forsøger at foretage en ændring i en fil i en beskyttet mappe. Men den vil blive registreret i logbogen Windows, hvor du kan vurdere påvirkningen af din organisation.
   - **Bloker kun diskændringer** – Forsøg fra upålidelige apps på at skrive til diskudførte enheder logføres Windows hændelsesloggen. Disse logfiler kan findes i Logfiler **for** \> programmer og tjenester, som Microsoft \> Windows \> Windows Defender-drifts-id \> \> 1123.
   - **Kun overvåge diskændringer** – Det er kun forsøg på at skrive til beskyttet disk, der skal **registreres i hændelsesloggen** \> i Windows (under Programmer **og** \> tjenestelogfiler **Microsoft** \> Windows **Windows Defender** \> **drifts-id** \> **1124**). Forsøg på at ændre eller slette filer i beskyttede mapper optages ikke.

    :::image type="content" source="../../media/cfa-gp-enable.png" alt-text="Indstillingen Gruppepolitik aktiveret og Overvågningstilstand valgt" lightbox="../../media/cfa-gp-enable.png":::

> [!IMPORTANT]
> For at aktivere styret mappeadgang fuldt ud skal du angive indstillingen Gruppepolitik aktiveret og vælge  Bloker i  rullemenuen med indstillinger.

## <a name="powershell"></a>PowerShell

1. Skriv **powershell** i menuen Start, **højreklik på Windows PowerShell** og vælg **Kør som administrator**.

2. Angiv følgende cmdlet:

    ```PowerShell
    Set-MpPreference -EnableControlledFolderAccess Enabled
    ```

Du kan aktivere funktionen i overvågningstilstand ved at angive i stedet `AuditMode` for `Enabled`.

Bruges `Disabled` til at deaktivere funktionen.

## <a name="see-also"></a>Se også

- [Beskyt vigtige mapper med styret mappeadgang](controlled-folders.md)
- [Tilpas styret mappeadgang](customize-controlled-folders.md)
- [Evaluer Microsoft Defender for Endpoint](evaluate-mde.md)
