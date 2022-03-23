---
title: Forbered certifikater og netværksprofiler til Microsoft Managed Desktop
description: Certifikatkrav og Wi-Fi-forbindelse
keywords: Microsoft-administreret skrivebord, Microsoft 365, tjeneste, dokumentation
ms.service: m365-md
author: tiaraquan
f1.keywords:
- NOCSH
ms.author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
manager: dougeby
ms.topic: article
audience: Admin
ms.openlocfilehash: ccdd9f390c794590eed6cbe11d169430f92bdf55
ms.sourcegitcommit: cafca45069819a44c7cf8c67f6c1e105de1b3393
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/10/2022
ms.locfileid: "63587471"
---
# <a name="prepare-certificates-and-network-profiles-for-microsoft-managed-desktop"></a>Forbered certifikater og netværksprofiler til Microsoft Managed Desktop  

Certifikatbaseret godkendelse er et almindeligt krav for kunder, der bruger Microsoft Managed Desktop. Du skal muligvis bruge certifikater for at:

- Access Wi-Fi eller LAN
- Forbind til VPN-løsninger
- Få adgang til interne ressourcer i organisationen

Da Microsoft-administrerede desktopenheder er forbundet til Azure Active Directory (Azure AD) og administreres af Microsoft Intune, skal du installere sådanne certifikater ved hjælp af:

- Simple Certificate Enrollment Protocol (SCEP) eller
- PKCS-certifikatinfrastruktur (Public Key Cryptography Standard), der er integreret med Intune.

## <a name="certificate-requirements"></a>Certifikatkrav

Rodcertifikater er nødvendige for at installere certifikater via en SCEP- eller PKCS-infrastruktur. Andre programmer og tjenester i organisationen kræver muligvis, at rodcertifikater installeres på dine Microsoft-administrerede computerenheder.

Før du installerer SCEP- eller PKCS-certifikater til Microsoft Managed Desktop, skal du indsamle krav til hver tjeneste, der kræver et bruger- eller enhedscertifikat i organisationen. For at gøre denne aktivitet nemmere kan du bruge en af følgende planlægningsskabeloner:  

- [Skabelonen PKCS-certifikat](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/managed-desktop/get-ready/downloads/PKCS-certificate-template.xlsx)
- [SCEP-certifikatskabelon](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/managed-desktop/get-ready/downloads/SCEP-certificate-template.xlsx)

## <a name="wi-fi-connectivity-requirements"></a>Wi-Fi forbindelseskrav

Hvis du vil tillade, at en enhed automatisk får den påkrævede Wi-Fi-konfiguration for dit virksomhedsnetværk, skal du muligvis bruge Wi-Fi konfigurationsprofil.

Du kan konfigurere Microsoft Managed Desktop til at installere disse profiler på dine enheder. Hvis din netværkssikkerhed kræver, at enheder er en del af det lokale domæne, kan det være nødvendigt at evaluere din Wi-Fi-netværksinfrastruktur for at sikre, at den er kompatibel med Microsoft-administrerede stationære computere. Microsoft-administrerede desktopenheder er kun forbundet med Azure AD.

Før du installerer Wi-Fi konfiguration på Microsoft Managed Desktop-enheder, skal du indsamle organisationens krav for hvert Wi-Fi-netværk. Du kan gøre denne aktivitet nemmere ved at bruge denne [WiFi-profilskabelon](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/managed-desktop/get-ready/downloads/WiFi-profile-template.xlsx).

## <a name="wired-connectivity-requirements-and-8021x-authentication"></a>Krav til kablet forbindelse og 802.1x-godkendelse

Hvis du bruger 802.1x-godkendelse til at sikre adgang fra enheder til dit lokalnetværk (LAN), skal du skubbe de nødvendige konfigurationsoplysninger til dine Microsoft Managed Desktop-enheder.

Microsoft-administrerede skrivebordsenheder, der kører Windows 10, version 1809 eller nyere, understøtter installation af en 802.1x-konfiguration via CSP (WiredNetwork configuration serviceudbyder). Du kan få mere at vide [under WiredNetwork CSP-dokumentation](/windows/client-management/mdm/wirednetwork-csp) .

Før du installerer en konfigurationsprofil for et kablet netværk på Microsoft Managed Desktop-enheder, skal du indsamle organisationens krav til virksomhedens netværk via kabel.

**Sådan indsamles krav til virksomhedens netværk via kabel:**

1. Log på en enhed, hvor din eksisterende 802.1x-profil er konfigureret og har forbindelse til LAN-netværket.  
2. Åbn en kommandoprompt med administrative legitimationsoplysninger.
3. Find navnet på LAN-grænsefladen ved at køre `netsh interface show interface`.
4. Eksportér LAN-profil XML ved at køre `netsh lan export profile folder=.  Interface=”interface_name”`.
5. Hvis du skal teste din eksporterede profil på en Microsoft-administreret skrivebordsenhed, skal du køre `netsh lan add profile filename="PATH_AND_FILENAME.xml" interface="INTERFACE_NAME"`.

## <a name="deploy-certificate-infrastructure"></a>Installér certifikatinfrastruktur  

Hvis du allerede har en eksisterende SCEP- eller PKCS-infrastruktur med Intune, og denne tilgang opfylder dine krav, kan du også bruge den til Microsoft Managed Desktop.

Hvis der ikke allerede findes en SCEP- eller PKCS-infrastruktur, skal du forberede en. Få mere at vide under [Konfigurer en certifikatprofil for dine enheder i Microsoft Intune](/intune/certificates-configure).

## <a name="deploy-a-lan-profile"></a>Installere en LAN-profil

Når din LAN-profil er blevet eksporteret, kan du forberede politikken for Microsoft Managed Desktop.

**Sådan forberedes politikken til Microsoft-administreret skrivebord:**

1. Opret en brugerdefineret profil i Microsoft Intune for LAN-profilen ved hjælp af følgende indstillinger (se Brug af brugerdefinerede indstillinger [for Windows 10 i Intune](/intune/custom-settings-windows-10)). I **Brugerdefineret OMA-URI Indstillinger** **du vælge** Tilføj og derefter angive følgende værdier:
    - Navn: Moderne Workplace-Windows 10 LAN-profil
    - Beskrivelse: Angiv en beskrivelse, der giver et overblik over indstillingen og andre vigtige detaljer.
    - OMA-URI (store og små bogstaver): Enter `./Device/Vendor/MSFT/WiredNetwork/LanXML`
    - Datatype: Vælg **Streng (XML-fil)**.
    - Brugerdefineret XML: Upload den eksporterede XML-fil.
2. Tildel den brugerdefinerede profil til **enheder med den moderne arbejdsplads – testgruppe** .
3. Afprøver en hvilken som helst test, du har brug for, med en enhed, der er i gruppen Testinstallation. Hvis det lykkes, kan du tildele den brugerdefinerede profil til følgende grupper:
    - Moderne enheder på arbejdspladsen – først
    - Moderne enheder på arbejdspladsen – Hurtig
    - Moderne enheder på arbejdspladsen – bred

## <a name="deploy-certificates-and-wi-fivpn-profile"></a>Installere certifikater og Wi-Fi/VPN-profil

**Sådan installeres certifikater og profiler:**

1. Opret en profil for hvert af rod- og mellemliggende certifikater (se [Opret pålidelige certifikatprofiler](/intune/protect/certificates-configure#step-3-create-trusted-certificate-profiles). Hver af disse profiler skal have en beskrivelse, der indeholder en udløbsdato i DD/MM/AAA-format. **Certifikatprofiler skal have en udløbsdato.**
2. Opret en profil for hvert SCEP- eller PKCS-certifikat (se Opret en [SCEP-certifikatprofil](/intune/protect/certificates-scep-configure#create-a-scep-certificate-profile) eller [Opret en pcKCS-certifikatprofil](/intune/protect/certficates-pfx-configure#create-a-pkcs-certificate-profile)). Hver af disse profiler skal have en beskrivelse, der indeholder en udløbsdato i DD/MM/AAA-format. **Certifikatprofiler skal have en udløbsdato.**
3. Opret en profil for hvert firma-WiFi-netværk ([se Wi-Fi-indstillinger for Windows 10 og nyere enheder](/intune/wi-fi-settings-windows)).
4. Opret en profil for hver virksomheds VPN (se [Windows 10 og Windows Holographic enhedsindstillinger for at tilføje VPN-forbindelser ved hjælp af Intune](/intune/vpn-settings-windows-10)).
5. Tildel profilerne til **enheder med den moderne arbejdsplads – testgruppe** .
6. Afprøver en hvilken som helst test, du har brug for, med en enhed, der er i gruppen Testinstallation. Hvis det lykkes, kan du tildele den brugerdefinerede profil til følgende grupper:
    - Moderne enheder på arbejdspladsen – først
    - Moderne enheder på arbejdspladsen – Hurtig
    - Moderne enheder på arbejdspladsen – bred

## <a name="steps-to-get-ready-for-microsoft-managed-desktop"></a>Trin til at blive klar til Microsoft Managed Desktop

1. Gennemgå [forudsætninger for Microsoft Managed Desktop](prerequisites.md).
1. Kør værktøjer [til vurdering af parathed](readiness-assessment-tool.md).
1. Køb [Firmaportal](../get-started/company-portal.md).
1. Gennemgå [forudsætningerne for gæstekonti](guest-accounts.md).
1. Kontrollér [netværkskonfigurationen](network.md).
1. Forberede certifikater og netværksprofiler (denne artikel).
1. [Forberede brugeradgang til data](authentication.md).
1. [Forbered apps](apps.md).
1. [Forbered tilknyttede drev](mapped-drives.md).
1. [Forberede udskrivningsressourcer](printing.md).
1. Navne [på adresseenhed](address-device-names.md).
