---
title: Forudsætninger for Microsoft-administreret skrivebord
description: Licenser, Azure-konti, godkendelsesindstillinger og Microsoft 365, der skal konfigureres, før du tilmelder dig Microsoft Managed Desktop
keywords: Microsoft-administreret skrivebord, Microsoft 365, tjeneste, dokumentation
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
audience: Admin
ms.openlocfilehash: 495aa7e505bdcec8b5848499ac688847afa129bc
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/12/2022
ms.locfileid: "63587254"
---
# <a name="prerequisites-for-microsoft-managed-desktop"></a>Forudsætninger for Microsoft-administreret skrivebord

<!--This topic is the target for a "Learn more" link in the Admin Portal (aka.ms/prereq-azure). DO NOT DELETE.-->
<!--from Prerequisites -->

I denne artikel beskrives de krav til infrastruktur, du skal opfylde for at sikre succes med Microsoft Managed Desktop.

| Område | Oplysninger om forudsætninger |
| ----- | ----- |
| Licensering | Microsoft Managed Desktop kræver en Microsoft 365 E3 der er tildelt Microsoft Defender til slutpunkt (eller tilsvarende) til dine brugere. <ul><li>Hvis du vil have mere at vide om de specifikke serviceplaner, skal [du se Mere om licenser](#more-about-licenses).</li><li> Du kan finde flere oplysninger om tilgængelige licenser [under Microsoft 365 licenser](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans).</li></ul>
| Forbindelse | Alle Microsoft-administrerede skrivebordsenheder kræver forbindelse til mange Microsoft-tjenesteslutpunkter fra virksomhedens netværk.<br><br> Du kan finde en komplet liste over nødvendige IP'er og URL-adresser under [Netværkskonfiguration](../get-ready/network.md).
| Azure Active Directory | Azure Active Directory (Azure AD) skal enten være kilde til autoritet for alle brugerkonti, eller brugerkonti skal synkroniseres fra det lokale Active Directory med den nyeste understøttede version af Azure AD Forbind. <ul><li>Du kan finde flere oplysninger [i Azure AD Forbind](/azure/active-directory/hybrid/whatis-azure-ad-connect).</li><li> Du kan finde flere oplysninger om understøttede Azure AD Forbind-versioner i [Azure AD Forbind:Versionsudgivelseshistorik](/azure/active-directory/hybrid/reference-connect-version-history).</li></ul>
| Godkendelse | Hvis Azure AD ikke er kilden til primær godkendelse for brugerkonti, skal du konfigurere en af følgende godkendelsesmetoder i Azure AD Forbind:<ul><li> Synkronisering af adgangskodehash.</li> <li> Pass-through-godkendelse.</li><li>En ekstern identitetsudbyder (herunder Windows Server ADFS og ikke-Microsoft IDP'er), der er konfigureret til at opfylde krav til Azure AD-integration. Du kan finde flere oplysninger i [retningslinjerne](https://www.microsoft.com/download/details.aspx?id=56843).</li></ul> <br> Ved indstilling af godkendelsesindstillinger med Azure AD Forbind anbefales også tilbageførsel af adgangskode. Du kan finde flere oplysninger under [Tilbageførsel af adgangskode](/azure/active-directory/authentication/howto-sspr-writeback). <br><br> Hvis en ekstern identitetsudbyder implementeres, skal du validere løsningen:<ul><li>Opfylder kravene til Azure AD-integration.</li><li>Understøtter betinget adgang til Azure AD, som gør det muligt at konfigurere overholdelsespolitikken for microsoft-administrerede enheder på skrivebordet.</li><li>Aktiverer tilmelding til enhed, brug af Microsoft 365 tjenester eller funktioner, der kræves som en del af Microsofts administrerede skrivebord.</li></ul> <br>Du kan finde flere oplysninger om godkendelsesindstillinger med Azure AD under [Indstillinger for Forbind af Azure AD](/azure/active-directory/connect/active-directory-aadconnect-user-signin).
| Microsoft 365 | OneDrive for Business være aktiveret for brugere af Microsoft-administrerede computere.<br><br>Selvom det ikke er påkrævet at tilmelde dig Microsoft Managed Desktop, anbefaler vi kraftigt, at følgende tjenester overføres til skyen:<ul><li>Mail: Overfør til skybaserede postkasser, Exchange online, eller konfigurer med Exchange Online Hybrid med Exchange 2013 eller nyere i det lokale miljø.</li><li>Filer og mapper: Overfør til OneDrive for Business eller SharePoint Online.</li><li>Online samarbejdsværktøjer: Overfør til Teams.</ul> |
| Enhedshåndtering | Microsoft-administrerede skrivebordsenheder kræver administration ved hjælp Microsoft Intune. Intune skal angives som nøglecenteret for administration af mobilenheder.<br><br> Du kan finde flere oplysninger [under Microsoft Intune](https://www.microsoft.com/cloud-platform/microsoft-intune).
| Sikkerhedskopiering og gendannelse af data | Microsoft Managed Desktop kræver, at filer synkroniseres til OneDrive for Business for beskyttelse. Filer, der ikke er synkroniseret OneDrive for Business ikke garanteres af Microsoft Managed Desktop. Filerne kan gå tabt under børser på enheder eller under supportopkald, der kræver nulstilling af enhed.<br><br>Selvom det ikke er påkrævet, anbefaler Microsoft Managed Desktop på det kraftigste overførsel fra tilknyttede netværksdrev til den relevante skybaserede løsning. Få mere at vide under [Forbered tilknyttede drev til Microsoft Managed Desktop](mapped-drives.md)

Når du er klar til at komme i gang med Microsoft Managed Desktop, skal du kontakte Din Microsoft Account Manager.

## <a name="more-about-licenses"></a>Mere om licenser

Microsoft Managed Desktop kræver visse licensindstillinger for at kunne fungere. Se [Microsoft Managed Desktop-teknologier](../intro/technologies.md) for at få oplysninger om, hvordan disse licenser bruges.

> [!TIP]
> Hvis du vil tildele disse licensmuligheder til bestemte brugere, anbefaler vi, at du udnytter den [gruppebaserede licensfunktion](/azure/active-directory/fundamentals/active-directory-licensing-whatis-azure-portal) i Azure Active Directory.

- Azure Active Directory Premium P1
- Microsoft Intune
- Windows 10 Enterprise  
- Microsoft Defender til Slutpunkt
- Microsoft 365 Apps for enterprise
- Microsoft Teams
- [SharePoint Online Plan 2](https://www.microsoft.com/microsoft-365/sharepoint/compare-sharepoint-plans)
- [Exchange Online plan 2](https://www.microsoft.com/microsoft-365/exchange/compare-microsoft-exchange-online-plans)

> [!TIP]
> Microsoft Account Manager hjælper dig med at gennemgå dine aktuelle licenser, serviceplaner og finde den mest effektive vej til, at du kan få de ekstra licenser eller serviceplaner, du skal bruge, og samtidig undgå duplikering.

## <a name="steps-to-get-ready-for-microsoft-managed-desktop"></a>Trin til at blive klar til Microsoft Managed Desktop

1. Gennemgå forudsætningerne (denne artikel).
1. Kør værktøjer [til vurdering af parathed](readiness-assessment-tool.md).
1. Køb [Firmaportal](../get-started/company-portal.md).
1. Gennemgå [forudsætningerne for gæstekonti](guest-accounts.md).
1. Kontrollér [netværkskonfigurationen](network.md).
1. [Forberede certifikater og netværksprofiler](certs-wifi-lan.md).
1. [Forberede brugeradgang til data](authentication.md).
1. [Forbered apps](apps.md).
1. [Forbered tilknyttede drev](mapped-drives.md).
1. [Forberede udskrivningsressourcer](printing.md).
1. Navne [på adresseenhed](address-device-names.md).
