---
title: Aktivér styret mappeadgang
keywords: Kontrolleret mappeadgang, Windows 10, Windows 11, Windows Defender, ransomware, beskytte, filer, mapper, aktivere, tænde, bruge
description: Få mere at vide om, hvordan du beskytter dine vigtige filer ved at aktivere adgang til styrede mapper
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
ms.openlocfilehash: 4854ca235790cc8400f3f5a962e4bff203f86f98
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/12/2022
ms.locfileid: "64788122"
---
# <a name="enable-controlled-folder-access"></a>Aktivér styret mappeadgang

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- Microsoft Defender Antivirus

**Platforme**
- Windows

> Vil du gerne opleve Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

[Kontrolleret mappeadgang](controlled-folders.md) hjælper dig med at beskytte værdifulde data mod skadelige apps og trusler, f.eks. ransomware. Kontrolleret mappeadgang er inkluderet i Windows 10, Windows 11 og Windows Server 2019. Kontrolleret mappeadgang er også inkluderet som en del af den [moderne, samlede løsning til Windows Server 2012R2 og 2016](/microsoft-365/security/defender-endpoint/configure-server-endpoints#new-functionality-in-the-modern-unified-solution-for-windows-server-2012-r2-and-2016-preview).

Du kan aktivere adgang til styrede mapper ved hjælp af en af disse metoder:

- [Windows Sikkerhed app *](#windows-security-app)
- [Microsoft Endpoint Manager](#endpoint-manager)
- [Mobil Enhedshåndtering (MDM)](#mobile-device-management-mdm)
- [Microsoft Endpoint Configuration Manager](#microsoft-endpoint-configuration-manager)
- [Gruppepolitik](#group-policy)
- [PowerShell](#powershell)

[Overvågningstilstand](evaluate-controlled-folder-access.md) giver dig mulighed for at teste, hvordan funktionen fungerer (og gennemse hændelser) uden at påvirke den normale brug af enheden.

Gruppepolitik indstillinger, der deaktiverer fletning af lokale administratorlister, tilsidesætter kontrollerede mappeadgangsindstillinger. De tilsidesætter også beskyttede mapper og tilladte apps, der er angivet af den lokale administrator, via kontrolleret mappeadgang. Disse politikker omfatter:

- Microsoft Defender Antivirus **Konfigurer funktionsmåden for lokal administratorfletning for lister**
- System Center Endpoint Protection **Tillad brugere at tilføje udeladelser og tilsidesættelser**

Du kan få flere oplysninger om deaktivering af fletning af lokale lister under [Forbyd eller tillad brugere at redigere Microsoft Defender AV-politikindstillinger lokalt](/windows/security/threat-protection/microsoft-defender-antivirus/configure-local-policy-overrides-microsoft-defender-antivirus).

## <a name="windows-security-app"></a>Windows Sikkerhed app

1. Åbn appen Windows Sikkerhed ved at vælge skjoldikonet på proceslinjen. Du kan også søge i menuen Start efter **Windows Sikkerhed**.

2. Vælg feltet **Virus & threat protection** (eller skjoldikonet på menulinjen til venstre), og vælg derefter **Ransomware-beskyttelse**.

3. Angiv parameteren for **adgang til Kontrolleret mappe** til **Til**.

> [!NOTE]
> *Denne metode er ikke tilgængelig på Windows Server 2012R2 eller 2016.
> 
> Hvis kontrolleret mappeadgang er konfigureret med Gruppepolitik, PowerShell eller MDM-CSP'er, ændres tilstanden i appen Windows Sikkerhed efter genstart af enheden.
> Hvis funktionen er angivet til **Overvågningstilstand** med et af disse værktøjer, viser appen Windows Sikkerhed tilstanden som **Fra**.
> Hvis du beskytter brugerprofildata, anbefaler vi, at brugerprofilen er på standard-Windows installationsdrevet.

## <a name="endpoint-manager"></a>Endpoint Manager

1. Log på [Endpoint Manager](https://endpoint.microsoft.com), og åbn **Endpoint Security**.

2. Gå til **Politik** for **reduktion af** \> angrebsoverflade.

3. Vælg **Platform**, vælg **Windows 10 og nyere**, og vælg profilen **Regler for** \> reduktion af angrebsoverfladen **Opret**.

4. Navngiv politikken, og tilføj en beskrivelse. Vælg **Næste**.

5. Rul ned til bunden, vælg rullelisten **Aktivér mappebeskyttelse** , og vælg **Aktivér**.

6. Vælg **Liste over yderligere mapper, der skal beskyttes,** og tilføj de mapper, der skal beskyttes.

7. Vælg **Liste over apps, der har adgang til beskyttede mapper** , og tilføj de apps, der har adgang til beskyttede mapper.

8. Vælg **Udelad filer og stier fra regler for reduktion af angrebsoverfladen** , og tilføj de filer og stier, der skal udelukkes fra regler for reduktion af angrebsoverfladen.

9. Vælg **profiltildelingerne**, tildel alle **brugere & Alle enheder**, og vælg **Gem**.

10. Vælg **Næste** for at gemme hvert åbne blad og derefter **Opret**.

    > [!NOTE]
    > Jokertegn understøttes for programmer, men ikke for mapper. Undermapper er ikke beskyttet. Tilladte apps vil fortsætte med at udløse hændelser, indtil de genstartes.

## <a name="mobile-device-management-mdm"></a>Mobil Enhedshåndtering (MDM)

Brug [./Vendor/MSFT/Policy/Config/ControlledFolderAccessProtectedFolders](/windows/client-management/mdm/policy-csp-defender) CSP (Configuration Service Provider) til at tillade, at apps foretager ændringer i beskyttede mapper.

## <a name="microsoft-endpoint-configuration-manager"></a>Microsoft Endpoint Configuration Manager

1. I Microsoft Endpoint Configuration Manager skal du gå til **Assets and Compliance** \> **Endpoint Protection** \> **Windows Defender Exploit Guard**.

2. Vælg **Start** \> **Opret Exploit Guard-politik**.

3. Angiv et navn og en beskrivelse, vælg **Kontrolleret mappeadgang**, og vælg **Næste**.

4. Vælg, om du vil blokere eller overvåge ændringer, tillade andre apps eller tilføje andre mapper, og vælg **Næste**.

   > [!NOTE]
   > Jokertegn understøttes for programmer, men ikke for mapper. Undermapper er ikke beskyttet. Tilladte apps vil fortsætte med at udløse hændelser, indtil de genstartes.

5. Gennemse indstillingerne, og vælg **Næste** for at oprette politikken.

6. Luk **, når** politikken er oprettet.

## <a name="group-policy"></a>Gruppepolitik

1. Åbn [administrationskonsollen for Gruppepolitik](https://technet.microsoft.com/library/cc731212.aspx) på din Gruppepolitik-administrationsenhed, højreklik på det Gruppepolitik objekt, du vil konfigurere, og vælg **Rediger**.

2. I **editoren til Gruppepolitik administration** skal du gå til **Computerkonfiguration** og vælge **Administrative skabeloner**.

3. Udvid træet for at **Windows komponenter > Microsoft Defender Antivirus > Windows Defender Exploit Guard > kontrolleret mappeadgang**.

4. Dobbeltklik på indstillingen **Konfigurer kontrolleret mappeadgang** , og angiv indstillingen til **Aktiveret**. I afsnittet indstillinger skal du angive en af følgende indstillinger:
   - **Enable** – Ondsindede og mistænkelige apps kan ikke foretage ændringer af filer i beskyttede mapper. Der vises en meddelelse i hændelsesloggen for Windows.
   - **Disable (Standard)** – Funktionen Kontrolleret mappeadgang fungerer ikke. Alle apps kan foretage ændringer af filer i beskyttede mapper.
   - **Overvågningstilstand** – Ændringer tillades, hvis en skadelig eller mistænkelig app forsøger at foretage en ændring af en fil i en beskyttet mappe. Den registreres dog i Windows hændelseslog, hvor du kan vurdere indvirkningen på din organisation.
   - **Bloker kun diskændring** – Forsøg fra apps, der ikke er tillid til, på at skrive til disksektorer logføres i Windows hændelseslog. Du kan finde disse logge i **Logfiler for** \> programmer og tjenester Microsoft \> Windows \> Windows Defender \> Handlings-id \> 1123.
   - **Kun ændring af overvågningsdisk** – Kun forsøg på at skrive til beskyttede disksektorer registreres i Windows hændelseslog (under **Logfiler over** \> programmer og tjenester **Microsoft** \> **Windows** \> **Windows Defender** \> **handlings-id** \> **1124**). Forsøg på at redigere eller slette filer i beskyttede mapper registreres ikke.

    :::image type="content" source="../../media/cfa-gp-enable.png" alt-text="Gruppepolitikindstillingen Aktiveret og Overvågningstilstand valgt" lightbox="../../media/cfa-gp-enable.png":::

> [!IMPORTANT]
> Hvis du vil aktivere kontrolleret mappeadgang fuldt ud, skal du angive indstillingen Gruppepolitik til **Aktiveret** og vælge **Bloker** i rullemenuen med indstillinger.

## <a name="powershell"></a>PowerShell

1. Skriv **powershell** i menuen Start, højreklik **Windows PowerShell**, og vælg **Kør som administrator**.

2. Angiv følgende cmdlet:

    ```PowerShell
    Set-MpPreference -EnableControlledFolderAccess Enabled
    ```

Du kan aktivere funktionen i overvågningstilstand ved at angive `AuditMode` i stedet for `Enabled`.

Bruges `Disabled` til at deaktivere funktionen.

## <a name="see-also"></a>Se også

- [Beskyt vigtige mapper med kontrolleret mappeadgang](controlled-folders.md)
- [Tilpas styret mappeadgang](customize-controlled-folders.md)
- [Evaluer Microsoft Defender for Endpoint](evaluate-mde.md)
