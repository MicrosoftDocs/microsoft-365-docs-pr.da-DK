---
title: Slå netværksbeskyttelse til
description: Aktivér netværksbeskyttelse med Gruppepolitik, PowerShell eller administration af mobilenheder, og Konfigurationsstyring.
keywords: Netværksbeskyttelse, udnyttelse, skadeligt websted, ip, domæne, domæner, aktivér, aktivér
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
ms.openlocfilehash: b21b2f2a69ab9a85f1f5003104969364ae9c6e78
ms.sourcegitcommit: cdb90f28e59f36966f8751fa8ba352d233317fc1
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/09/2022
ms.locfileid: "63599310"
---
# <a name="turn-on-network-protection"></a>Slå netværksbeskyttelse til

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> [!TIP]
> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

[Netværksbeskyttelse hjælper](network-protection.md) med at forhindre medarbejdere i at bruge et hvilket som helst program til at få adgang til skadelige domæner, der kan hoste forsøg på phishing, udnyttelse og andet skadeligt indhold på internettet. Du kan [overvåge netværksbeskyttelse i et](evaluate-network-protection.md) testmiljø for at se, hvilke apps der blev blokeret, før du aktiverer det.

[Få mere at vide om konfigurationsindstillinger for netværksfiltrering.](/mem/intune/protect/endpoint-protection-windows-10#network-filtering)

## <a name="check-if-network-protection-is-enabled"></a>Kontrollér, om netværksbeskyttelse er aktiveret

Kontrollér, om netværksbeskyttelse er aktiveret på en lokal enhed ved hjælp af registreringseditoren.

1. Vælg knappen **Start** på proceslinjen, og skriv **regedit for at** åbne Registreringseditor.

2. Vælg **HKEY_LOCAL_MACHINE** i sidemenuen.

3. Naviger gennem de indlejrede menuer til **SOFTWARE-politikker** \>  \> **Microsoft** \> **Windows Defender** \> **Windows Defender Exploit** **Guard-netværksbeskyttelse**\>.

Hvis nøglen mangler, skal du gå til **SOFTWARE** \> **Microsoft** \> **Windows Defender** \> **Windows Defender Exploit Guard** \> **Network Protection**.

4. Vælg **EnableNetworkProtection for** at få vist den aktuelle tilstand for netværksbeskyttelse på enheden:

   - 0 eller **Fra**
   - 1 eller **Til**
   - 2 eller **overvågningstilstand**

    :::image type="content" alt-text="Registreringsdatabasenøgle til netværksbeskyttelse." source="../../media/95341270-b738b280-08d3-11eb-84a0-16abb140c9fd.png" lightbox="../../media/95341270-b738b280-08d3-11eb-84a0-16abb140c9fd.png":::
    
    
## <a name="enable-network-protection"></a>Aktivér netværksbeskyttelse

Aktivér netværksbeskyttelse ved hjælp af en af disse metoder:

- [PowerShell](#powershell)
- [Administration af mobilenheder (MDM)](#mobile-device-management-mdm)
- [Microsoft Endpoint Manager](#microsoft-endpoint-manager)
- [Gruppepolitik](#group-policy)
- [Microsoft Endpoint Configuration Manager](#microsoft-endpoint-configuration-manager)

### <a name="powershell"></a>PowerShell

1. Skriv **powershell** i menuen Start, **højreklik på Windows PowerShell** og vælg **Kør som administrator**.

2. Angiv følgende cmdlet:

    ```PowerShell
    Set-MpPreference -EnableNetworkProtection Enabled
    ```

3. Valgfrit: Aktivér funktionen i overvågningstilstand ved hjælp af følgende cmdlet:

    ```PowerShell
    Set-MpPreference -EnableNetworkProtection AuditMode
    ```

    Brug `Disabled` i stedet `AuditMode` for `Enabled` eller til at deaktivere funktionen.

### <a name="mobile-device-management-mdm"></a>Administration af mobilenheder (MDM)

Brug [konfigurationskonfigurationen ./Vendor/MSFT/Policy/Config/Defender/EnableNetworkProtection](/windows/client-management/mdm/policy-csp-defender) serviceudbyder (CSP) til at aktivere eller deaktivere netværksbeskyttelse eller aktivere overvågningstilstand.

[Opdater Microsoft Defender-antimalwareplatformen til den nyeste version](https://support.microsoft.com/topic/update-for-microsoft-defender-antimalware-platform-92e21611-8cf1-8e0e-56d6-561a07d144cc) , før du aktiverer eller deaktiverer netværksbeskyttelse eller aktiverer overvågningstilstand.


### <a name="microsoft-endpoint-manager"></a>Microsoft Endpoint Manager

1. Log på Microsoft Endpoint Manager Administration (https://endpoint.microsoft.com).

2. Gå til **EnhederKonfigurationsprofilerOpret** >  >  **profil**.

3. I pop **op-menuen Opret** en profil skal **du vælge Platform** og **vælge Profiltype** som **skabeloner**.

4. Vælg **Slutpunktsbeskyttelse** fra **listen over skabeloner** under Skabelonnavn, og vælg derefter **Opret**.

4. Gå til **Endpoint** **protectionBasics** > , angiv et navn til din profil, og vælg derefter **Næste**.

5. I sektionen **Konfigurationsindstillinger** skal du gå **til Microsoft Defender Exploit Guard** >  **Network-filtreringNetwork** >  **protectionEnable** >  eller **Audit**. Vælg **Næste**.

6. Vælg de relevante **omfangsmærker**, **tildelinger** og **regler for anvendelse, som** kræves af din organisation. Administratorer kan angive flere krav.

7. Gennemse alle oplysningerne, og vælg derefter **Opret**.

### <a name="group-policy"></a>Gruppepolitik

Brug følgende fremgangsmåde for at aktivere netværksbeskyttelse på computere, der er medlem af et domæne eller på en enkeltstående computer.

1. Gå til Start på en enkeltstående computer **, og** skriv og vælg **Rediger gruppepolitik**.

    *– eller –*

    På en domæne forbundet Gruppepolitik-administrationscomputer skal du åbne [Gruppepolitik Management Console](https://technet.microsoft.com/library/cc731212.aspx), højreklikke på det Gruppepolitik-objekt, du vil konfigurere, og vælge **Rediger**.

2. I **administrationseditoren Gruppepolitik** skal du gå til **Computerkonfiguration** og vælge **Administrative skabeloner**.

3. Udvid træet for **at Windows komponenter** \> **Microsoft Defender Antivirus** \> **Windows Defender Exploit** **Guard-netværksbeskyttelse**\>.

   > [!NOTE]
   > I ældre versioner af Windows kan der i stien til gruppepolitikken være "Windows Defender Antivirus" i stedet for "Microsoft Defender Antivirus".

4. Dobbeltklik på indstillingen Undgå **, at brugere og apps får adgang til skadelige websteder** , og angiv indstillingen til **Aktiveret**. I sektionen Indstillinger skal du angive en af følgende indstillinger:
    - **Bloker** – Brugere kan ikke få adgang til skadelige IP-adresser og domæner.
    - **Deaktiver (standard)** – Funktionen netværksbeskyttelse virker ikke. Brugere vil ikke blive blokeret fra at få adgang til skadelige domæner.
    - **Overvågningstilstand** – Hvis en bruger besøger en ondsindet IP-adresse eller et domæne, registreres en hændelse i Windows hændelsesloggen. Brugeren vil dog ikke blive blokeret fra at besøge adressen.

   > [!IMPORTANT]
   > For at aktivere netværksbeskyttelse fuldt ud skal Gruppepolitik indstillingen til Aktiveret og også vælge  Bloker i rullemenuen med indstillinger.

Bekræft, at netværksbeskyttelse er aktiveret på en lokal computer ved hjælp af registreringseditoren:

1. Vælg **Start, og** skriv **regedit for** at åbne **Registreringseditor**.

2. Naviger **tilHKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender\Windows Defender Exploit Guard\Network Protection\EnableNetworkProtection**

3. Vælg **EnableNetworkProtection** , og bekræft værdien:
   - 0 =Fra
   - 1 =Til
   - 2=Overvågning

### <a name="microsoft-endpoint-configuration-manager"></a>Microsoft Endpoint Configuration Manager

1. Åbn Konfigurationsstyring konsol.

2. Gå til **Aktiver og overholdelse** >  **Endpoint Protection** >  **Windows Defender Exploit Guard**. 

3. Vælg **Opret Exploit Guard-politik** på båndet for at oprette en ny politik.
   - Hvis du vil redigere en eksisterende politik, skal du vælge **politikken** og derefter vælge Egenskaber enten på båndet eller i genvejsmenuen. Rediger indstillingen **Konfigurer netværksbeskyttelse** på **fanen Netværksbeskyttelse** .  

4. Angiv et **navn** til den nye politik på siden Generelt, og bekræft, at **indstillingen Netværksbeskyttelse** er aktiveret. 

5. På siden **Netværksbeskyttelse** skal du vælge en af følgende indstillinger for **indstillingen Konfigurer netværksbeskyttelse** :
   - **Bloker**
   - **Overvågning**
   - **Deaktiveret**
   
6. Udfør resten af trinnene, og gem politikken. 

7. Vælg Installér på båndet **for** at installere politikken i en samling.


> [!IMPORTANT]
> Når du har implementeret en Exploit Guard-politik Konfigurationsstyring, fjernes Exploit Guard-indstillingerne ikke fra klienterne, hvis du fjerner installationen. `Delete not supported` er registreret i Konfigurationsstyring ExploitGuardHandler.log, hvis du fjerner klientens Exploit Guard-installation. <!--CMADO8538577-->
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

- [Netværksbeskyttelse og TCP trevejs-handshake](network-protection.md#network-protection-and-the-tcp-three-way-handshake)

- [Evaluer netværksbeskyttelse](evaluate-network-protection.md)

- [Fejlfinding af netværksbeskyttelse](troubleshoot-np.md)
