---
title: Konfigurer Microsoft 365 Business Premium
description: Se, hvordan du konfigurerer Microsoft 365 Business Premium
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 03/01/2022
ms.service: o365-administration
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: 5b6f187f93e8a135bfb67c78509553d2963b011b
ms.sourcegitcommit: b67385243fb56ad20f2a6f1c40be46f5691c1c2a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/17/2022
ms.locfileid: "63705635"
---
# <a name="set-up-microsoft-365-business-premium"></a>Konfigurer Microsoft 365 Business Premium

Du har flere muligheder for at konfigurere og konfigurere Microsoft 365 Business Premium. Du kan:

- [Brug en guidet konfigurationsoplevelse til grundlæggende konfiguration og konfiguration](#guided-process-for-basic-setup)
- [Arbejde med en partner, f.eks. Microsoft Cloud Solution Provider (CSP)](#work-with-a-microsoft-partner)
- [Arbejde manuelt gennem konfigurationsprocessen](#manual-setup-and-configuration)


Brug denne artikel som vejledning.

## <a name="guided-process-for-basic-setup"></a>Guidet proces til grundlæggende konfiguration

Microsoft 365 Business Premium omfatter en guidet proces til grundlæggende konfiguration. Opgaver omfatter oprettelse af forbindelse til et brugerdefineret domæne, tilføjelse af brugere, tildeling af licenser, installation af Outlook på mobilenheder, gennemgang af indstillinger for databeskyttelse og anvendelse af en politik for beskyttelse af mobilapps. 

Se følgende video for at se, hvordan den guidede konfiguration fungerer: <br/><br/>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE471FJ?autoplay=false]

Når du er færdig med konfigurationen, er der yderligere trin, du skal udføre for at sikre, at dine sikkerheds- og overholdelsesfunktioner er korrekt konfigureret og anvendt. Disse trin omfatter:

- [Sikring Windows enheder](m365bp-secure-windows-devices.md)
- [Installation af Microsoft 365 apps](../admin/setup/install-applications.md)
- [Konfiguration og konfiguration af dine nye funktioner i Defender for Business](../security/defender-business/mdb-setup-configuration.md)

[Få mere at vide om forskellene mellem den guidede konfigurationsproces og siden Konfiguration](../admin/setup/o365-setup-wizard-and-setup-page.md).

> [!TIP]
> Se det følgende afsnit for at få mere at vide om konfiguration og konfiguration Microsoft 365 Business Premium.


## <a name="work-with-a-microsoft-partner"></a>Arbejd sammen med en Microsoft-partner

Microsoft har en liste over løsningsudbydere, der er autoriseret til at sælge tilbud, herunder Microsoft 365 Business Premium. 

Hvis du vil finde en løsningsudbyder i dit område, skal du gøre følgende:

1. Gå til siden **Microsoft Solution Providers** ([https://www.microsoft.com/solution-providers](https://www.microsoft.com/solution-providers)).
 
2. I søgefeltet skal du udfylde din placering og virksomhedens størrelse. 

3. I feltet **Søg efter produkter, tjenester, færdigheder, brancher** skal du lægge `Microsoft 365`, og derefter vælge **Gå**.

4. Gennemse listen over resultater. Vælg en udbyder for at få mere at vide om deres ekspertise og de tjenester, de leverer.

Se også [Find din partner eller forhandler](../admin/manage/find-your-partner-or-reseller.md).

## <a name="manual-setup-and-configuration"></a>Manuel konfiguration og konfiguration

Hvis du foretrækker at fuldføre konfigurationen og konfigurationen manuelt, skal du bruge følgende tabel som vejledning:

| Fase  | Opgave  | Ressourcer til at få mere at vide  |
|---------|---------|---------|
| **Planlægning**     | Planlæg din konfigurationsproces  | [Planlæg din konfiguration af Microsoft 365 til virksomheder](../admin/setup/plan-your-setup.md)   |
|  | Gennemse kravene | [Microsoft 365 Business Premium krav](https://www.microsoft.com/microsoft-365/business/microsoft-365-business-premium?activetab=pivot:overviewtab) |
| **Grundlæggende konfiguration**     | Brug et brugerdefineret domæne som `rob@contoso.com` med Microsoft 365 | [Føj et domæne til Microsoft 365](../admin/setup/add-domain.md) |
|      | Tilføj brugere, og tildel licenser i Microsoft 365      | [Tilføje brugere og tildele licenser på samme tid](../admin/add-users/add-users.md)        |
|  | Tildel administratorroller til brugere, der skal udføre visse funktioner, f.eks.: <br/>- Administration af funktioner<br/>- Administration af brugerkonti<br/>- Administration af enheder<br/>- Få vist eller administrere organisationens oplysninger om sikkerhed og overholdelse af regler og standarder | [Få mere at vide om administratorroller](../admin/add-users/about-admin-roles.md) <br/><br/> [Tildel administratorroller](../admin/add-users/assign-admin-roles.md)  |
|  | Installere Microsoft 365 Apps (f.eks. Word, Excel, PowerPoint og meget mere) | [Installér Office-programmer](../admin/setup/install-applications.md) |
| **Sikring af din organisation** | Se de 10 øverste dage for at sikre dit Microsoft 365 abonnement |  [De 10 mest populære måder at sikre Microsoft 365 planer til virksomheder på](../admin/security-and-compliance/secure-your-business-data.md) |
|  | Kræve, at alle bruger en ekstra bekræftelsesmetode, når de logger på Microsoft 365 | [Konfigurer multifaktorgodkendelse](../admin/security-and-compliance/set-up-multi-factor-authentication.md) | 
| **Beskyttelse af mail og indhold** |  Konfigurer avanceret beskyttelse mod phishing for at beskytte dig mod ondsindede efterligningsbaserede phishing-angreb og andre phishing-angreb | [Beskyt dine mails mod phishingangreb](../admin/security-and-compliance/secure-your-business-data.md) |
|   | Konfigurer vedhæftede Pengeskab for at beskytte din organisation mod skadelige vedhæftede filer i mails | [Beskyt dig mod skadelige vedhæftede filer og filer med Pengeskab vedhæftede filer](../admin/security-and-compliance/secure-your-business-data.md) |
|  | Konfigurere Pengeskab links til beskyttelse mod skadelige websteder (URL-adresser) i mails og Office dokumenter | [Konfigurere Pengeskab links](../admin/security-and-compliance/secure-your-business-data.md) |
|  | Konfigurere politik til forebyggelse af datatab for at beskytte følsomme oplysninger mod at blive delt | [Konfigurer overholdelsesfunktioner](../admin/security-and-compliance/set-up-compliance.md) |
| **Administration og beskyttelse af enheder** | Beskyt din organisations Windows enheder | [Gør Windows enheder sikre](m365bp-secure-windows-devices.md) <br/><br/>[Angive eller redigere indstillinger for programbeskyttelse til Windows 10 enheder](../admin/devices/protection-settings-for-windows-10-devices.md) |
|   | Gør Microsoft 365-apps sikre på mobilenheder | [Angiv indstillinger for appbeskyttelse til Android- eller iOS-enheder](../admin/devices/app-protection-settings-for-android-and-ios.md) |
|  | Konfigurer Microsoft Defender for Business (når det er tilgængeligt for din lejer) | [Oversigt over Microsoft Defender for Business](../security/defender-business/mdb-overview.md)<br/><br/>[Brug guiden til at konfigurere Defender for Business](../security/defender-business/mdb-use-wizard.md) |
| **Fillagring og overførsel af indhold** | Konfigurer fillagring, og hvordan deling fungerer for din organisation | [Konfigurer lagring og deling af filer i Microsoft 365](../admin/setup/set-up-file-storage-and-sharing.md) |
| | Importér eller overfør mail og kontakter | [Overfør mails og kontakter til Microsoft 365](../admin/setup/migrate-email-and-contacts-admin.md) |
|  | Flyt de firmafiler, som alle skal have adgang til SharePoint (SharePoint erstatter typisk brugen af et filshare eller netværksdrev) | [Flyt filer til SharePoint](../admin/setup/files-to-sharepoint.md) |
|  | Flyt dine eksisterende arbejdsfiler, f.eks. personlige arbejdsfiler eller følsomme forretningsfiler, til OneDrive | [Flyt filer til OneDrive](../admin/setup/files-to-onedrive.md) |
| **Kursusadministratorer og dit sikkerhedsteam** | Få mere at vide om, hvordan du bruger Administration | [Oversigt over Microsoft 365 Administration](../admin/admin-overview/admin-center-overview.md) |
|  | Brug det gratis videobibliotek til Microsoft 365 administratorer | [Videobibliotek for administratorkurser](../admin/admin-video-library.yml)  |
|  | Få mere at vide om, hvordan du bruger Microsoft 365 Defender portal ([https://security.microsoft.com](https://security.microsoft.com)) | [Kom i gang med at bruge Microsoft 365 Defender portalen](../security/defender-business/mdb-get-started.md) |

> [!TIP]
> Har du brug for hjælp? Overvej at [få Business Assist til Microsoft 365](https://support.microsoft.com/en-us/office/business-assist-for-microsoft-365-37deb8fe-61cc-4cf9-9ad1-1c8d93475070)

## <a name="see-also"></a>Se også

- [Oversigt over Microsoft Defender for Business](../security/defender-business/mdb-overview.md) (nu inkluderet i Microsoft 365 Business Premium!)

- [Virksomhedsabonnementer og faktureringsdokumentation](../commerce/index.yml)

- [Oversigt over Microsoft 365 Lighthouse](../lighthouse/m365-lighthouse-overview.md) (til Microsoft-csp'er)

- [De 10 mest populære måder at sikre Microsoft 365 planer til virksomheder på](../admin/security-and-compliance/secure-your-business-data.md)
