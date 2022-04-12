---
title: Slå netværksbeskyttelse til
description: Aktivér netværksbeskyttelse med Gruppepolitik, PowerShell eller mobile Enhedshåndtering og Configuration Manager.
keywords: Netværksbeskyttelse, udnyttelser, skadeligt websted, ip, domæne, domæner, aktivere, slå til
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
ms.topic: conceptual
author: denisebmsft
ms.author: deniseb
ms.reviewer: mkaminska
manager: dansimp
ms.technology: mde
ms.collection: m365-security-compliance
ms.date: ''
ms.openlocfilehash: d37723e45c5c4049e913422b2500b74d36c701eb
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/12/2022
ms.locfileid: "64789706"
---
# <a name="turn-on-network-protection"></a>Slå netværksbeskyttelse til

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- Microsoft Defender Antivirus

**Platforme**
- Windows

> [!TIP]
> Vil du gerne opleve Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

[Netværksbeskyttelse](network-protection.md) hjælper med at forhindre medarbejdere i at bruge alle programmer til at få adgang til farlige domæner, der kan hoste phishing-svindel, udnyttelser og andet skadeligt indhold på internettet. Du kan [overvåge netværksbeskyttelse](evaluate-network-protection.md) i et testmiljø for at få vist, hvilke apps der blokeres, før du aktiverer den.

[Få mere at vide om konfigurationsindstillinger for netværksfiltrering.](/mem/intune/protect/endpoint-protection-windows-10#network-filtering)

## <a name="check-if-network-protection-is-enabled"></a>Kontrollér, om netværksbeskyttelse er aktiveret

Kontrollér, om netværksbeskyttelse er blevet aktiveret på en lokal enhed ved hjælp af Registreringseditor.

1. Vælg knappen **Start** på proceslinjen, og skriv **regedit** for at åbne Registreringseditor.

2. Vælg **HKEY_LOCAL_MACHINE** i sidemenuen.

3. Naviger gennem de indlejrede menuer til **SOFTWAREpolitikker** \>  \> **Microsoft** \> **Windows Defender** \> **Windows Defender Exploit Guard** \> **Network Protection**.

Hvis nøglen mangler, skal du navigere til **SOFTWARE** \> **Microsoft** \> **Windows Defender** \> **Windows Defender Exploit Guard** \> **Network Protection**.

4. Vælg **EnableNetworkProtection** for at se den aktuelle tilstand af netværksbeskyttelse på enheden:

   - 0 eller **Fra**
   - 1 eller **Til**
   - 2 eller **overvågningstilstand**

    :::image type="content" source="../../media/95341270-b738b280-08d3-11eb-84a0-16abb140c9fd.png" alt-text="Registreringsdatabasenøglen Network Protection" lightbox="../../media/95341270-b738b280-08d3-11eb-84a0-16abb140c9fd.png":::

## <a name="enable-network-protection"></a>Aktivér netværksbeskyttelse

Aktivér netværksbeskyttelse ved hjælp af en af disse metoder:

- [PowerShell](#powershell)
- [Mobil Enhedshåndtering (MDM)](#mobile-device-management-mdm)
- [Microsoft Endpoint Manager](#microsoft-endpoint-manager)
- [Gruppepolitik](#group-policy)
- [Microsoft Endpoint Configuration Manager](#microsoft-endpoint-configuration-manager)

### <a name="powershell"></a>PowerShell

1. Skriv **powershell** i menuen Start, højreklik **Windows PowerShell**, og vælg **Kør som administrator**.

2. Angiv følgende cmdlet:

    ```PowerShell
    Set-MpPreference -EnableNetworkProtection Enabled
    ```

3. Valgfrit: Aktivér funktionen i overvågningstilstand ved hjælp af følgende cmdlet:

    ```PowerShell
    Set-MpPreference -EnableNetworkProtection AuditMode
    ```

    Brug `Disabled` i stedet for `AuditMode` eller `Enabled` til at deaktivere funktionen.

### <a name="mobile-device-management-mdm"></a>Administration af mobilenheder (MDM)

Brug [./Vendor/MSFT/Policy/Config/Defender/EnableNetworkProtection](/windows/client-management/mdm/policy-csp-defender) CSP (Configuration Service Provider) til at aktivere eller deaktivere netværksbeskyttelse eller overvågningstilstand.

[Opdater Microsoft Defender Antimalware-platformen til den nyeste version](https://support.microsoft.com/topic/update-for-microsoft-defender-antimalware-platform-92e21611-8cf1-8e0e-56d6-561a07d144cc) , før du aktiverer eller deaktiverer netværksbeskyttelse eller aktiverer overvågningstilstand.


### <a name="microsoft-endpoint-manager"></a>Microsoft Endpoint Manager

1. Log på Microsoft Endpoint Manager Administration (https://endpoint.microsoft.com).

2. Gå til **EnhederKonfigurationsprofilerOpret** >  >  **profil**.

3. I pop op-vinduet **Opret en profil** skal du vælge **Platform** og vælge **Profiltype** som **skabeloner**.

4. Vælg **Endpoint Protection** på listen over skabeloner i **skabelonnavnet**, og vælg derefter **Opret**.

4. Gå til **Endpoint** **protectionBasics** > , angiv et navn til din profil, og vælg derefter **Næste**.

5. I afsnittet **Konfigurationsindstillinger** skal du gå til **Microsoft Defender Exploit Guard** >  **NetværksfiltreringNetværksbeskyttelseEnable** >  >  eller **Audit**. Vælg **Næste**.

6. Vælg de relevante **områdekoder**, **tildelinger** og **anvendelighedsregler** , som kræves af din organisation. Administratorer kan angive flere krav.

7. Gennemse alle oplysningerne, og vælg derefter **Opret**.

### <a name="group-policy"></a>Gruppepolitik

Brug følgende procedure til at aktivere netværksbeskyttelse på domænetilsluttede computere eller på en separat computer.

1. På en separat computer skal du gå til **Start** og derefter skrive og vælge **Rediger gruppepolitik**.

    *-Eller-*

    Åbn [Gruppepolitik-administrationskonsollen](https://technet.microsoft.com/library/cc731212.aspx) på en domænetilsluttet Gruppepolitik administrationscomputer, højreklik på det Gruppepolitik objekt, du vil konfigurere, og vælg **Rediger**.

2. I **editoren til Gruppepolitik administration** skal du gå til **Computerkonfiguration** og vælge **Administrative skabeloner**.

3. Udvid træet for at **Windows komponenter** \> **Microsoft Defender Antivirus** \> **Windows Defender Exploit Guard** \> **Network Protection**.

   > [!NOTE]
   > I ældre versioner af Windows står der muligvis "Windows Defender Antivirus" i gruppepolitikken i stedet for "Microsoft Defender Antivirus".

4. Dobbeltklik på indstillingen **Forbyd brugere og apps at få adgang til farlige websteder** , og angiv indstillingen til **Aktiveret**. I afsnittet indstillinger skal du angive en af følgende indstillinger:
    - **Block** – Brugerne kan ikke få adgang til skadelige IP-adresser og domæner.
    - **Deaktiver (standard)** – Funktionen Netværksbeskyttelse fungerer ikke. Brugere blokeres ikke fra at få adgang til skadelige domæner.
    - **Overvågningstilstand** – Hvis en bruger besøger en skadelig IP-adresse eller et skadeligt domæne, registreres en hændelse i Windows hændelsesloggen. Brugeren blokeres dog ikke for at besøge adressen.

   > [!IMPORTANT]
   > Hvis du vil aktivere netværksbeskyttelse fuldt ud, skal du angive indstillingen Gruppepolitik til **Aktiveret** og også vælge **Bloker** i rullemenuen med indstillinger.

Bekræft, at netværksbeskyttelse er aktiveret på en lokal computer ved hjælp af Registreringseditor:

1. Vælg **Start** , og skriv **regedit** for at åbne **Registreringseditor**.

2. Naviger til **HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender\Windows Defender Exploit Guard\Network Protection\EnableNetworkProtection**

3. Vælg **EnableNetworkProtection,** og bekræft værdien:
   - 0=Fra
   - 1=Slået til
   - 2=Overvågning

### <a name="microsoft-endpoint-configuration-manager"></a>Microsoft Endpoint Configuration Manager

1. Åbn Configuration Manager-konsollen.

2. Gå til **Assets and Compliance** >  **Endpoint Protection** >  **Windows Defender Exploit Guard**. 

3. Vælg **Opret Exploit Guard-politik** på båndet for at oprette en ny politik.
   - Hvis du vil redigere en eksisterende politik, skal du vælge politikken og derefter vælge **Egenskaber** på båndet eller i genvejsmenuen. Rediger indstillingen **Konfigurer netværksbeskyttelse** under fanen **Netværksbeskyttelse** .  

4. Angiv et navn til den nye politik på siden **Generelt** , og kontrollér, at indstillingen **Netværksbeskyttelse** er aktiveret. 

5. På siden **Netværksbeskyttelse** skal du vælge en af følgende indstillinger for indstillingen **Konfigurer netværksbeskyttelse** :
   - **Bloker**
   - **Revision**
   - **Deaktiveret**
   
6. Fuldfør resten af trinnene, og gem politikken. 

7. På båndet skal du vælge **Installér** for at installere politikken i en samling.


> [!IMPORTANT]
> Når du har udrullet en Exploit Guard-politik fra Configuration Manager, fjernes indstillingerne for Exploit Guard ikke fra klienterne, hvis du fjerner installationen. `Delete not supported`registreres i Configuration Manager klientens ExploitGuardHandler.log, hvis du fjerner klientens Exploit Guard-installation. <!--CMADO8538577-->
> Følgende PowerShell-script kan køres under SYSTEM-kontekst for at fjerne disse indstillinger:<!--CMADO9907132-->
>
> ```powershell
> $defenderObject = Get-WmiObject -Namespace "root/cimv2/mdm/dmmap" -Class "MDM_Policy_Config01_Defender02" -Filter "InstanceID='Defender' and ParentID='./Vendor/MSFT/Policy/Config'"
> $defenderObject.AttackSurfaceReductionRules = $null
> $defenderObject.AttackSurfaceReductionOnlyExclusions = $null
> $defenderObject.EnableControlledFolderAccess = $null
> $defenderObject.ControlledFolderAccessAllowedApplications = $null
> $defenderObject.ControlledFolderAccessProtectedFolders = $null
> $defenderObject.EnableNetworkProtection = $null
> $defenderObject.Put()
>
> $exploitGuardObject = Get-WmiObject -Namespace "root/cimv2/mdm/dmmap" -Class "MDM_Policy_Config01_ExploitGuard02" -Filter "InstanceID='ExploitGuard' and ParentID='./Vendor/MSFT/Policy/Config'"
> $exploitGuardObject.ExploitProtectionSettings = $null
> $exploitGuardObject.Put()
>```  

## <a name="see-also"></a>Se også

- [Netværksbeskyttelse](network-protection.md)

- [Netværksbeskyttelse og TCP-trevejs-håndtryk](network-protection.md#network-protection-and-the-tcp-three-way-handshake)

- [Evaluer netværksbeskyttelse](evaluate-network-protection.md)

- [Foretag fejlfinding af netværksbeskyttelse](troubleshoot-np.md)
