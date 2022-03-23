---
title: Oversigt over Microsoft 365 for virksomhedssikkerhed for Contoso Corporation
author: kelleyvice-msft
f1.keywords:
- NOCSH
ms.author: kvice
manager: laurawi
ms.date: 10/02/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
ms.custom: ''
description: Sådan bruger Contoso sikkerhedsfunktionerne i Microsoft 365 til virksomheder.
ms.openlocfilehash: 15fd559b6dade63d56647c8f5f3437a57d27a56b
ms.sourcegitcommit: 1ef176c79a0e6dbb51834fe30807409d4e94847c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/19/2021
ms.locfileid: "63588679"
---
# <a name="summary-of-microsoft-365-for-enterprise-security-for-the-contoso-corporation"></a>Oversigt over Microsoft 365 for virksomhedssikkerhed for Contoso Corporation

Contoso IT-sikkerhedsafdelingen udførte en grundig sikkerhedsvurdering for at få godkendelse til at installere Microsoft 365 til virksomheder. De identificerede følgende sikkerhedskrav til skyen:

- Brug de stærkeste metoder til godkendelse for medarbejderadgang til skyressourcer.
- Sørg for, at pc'er og mobilenheder opretter forbindelse til og får adgang til programmer på sikre måder.
- Beskyt pc'er og mails mod malware.
- Tilladelser for skybaserede digitale aktiver definerer, hvem der har adgang til hvad, og hvad de kan gøre, og er udviklet til adgang med mindst rettigheder
- Følsomme og meget regulerede digitale aktiver mærkes, krypteres og gemmes på sikre steder.
- Meget regulerede digitale aktiver er beskyttet med yderligere kryptering og tilladelser.
- It-sikkerhedsmedarbejdere kan overvåge den aktuelle sikkerhed fra centrale dashboards og få besked om sikkerhedshændelser, så de hurtigt kan reagere og afhjælpe den.

## <a name="the-contoso-path-to-microsoft-365-security-readiness"></a>Contoso-stien til Microsoft 365 for sikkerhed

Contoso har fulgt disse trin for at forberede deres sikkerhed i forbindelse med udrulning Microsoft 365 til virksomheder:

1. Begræns administratorkonti til skyen

   Contoso har grundigt gennemset sine eksisterende Active Directory-domæneservices (AD DS)-administratorkonti og konfigureret en række dedikerede skyadministratorkonti og -grupper.

2. Klassificer data i tre sikkerhedsniveauer

   Contoso gennemstede de tre niveauer og bestemte dem, der blev brugt til at identificere de Microsoft 365 for virksomhedsfunktioner for at beskytte de mest værdifulde data.

3. Fastsæt politikker for adgang, opbevaring og beskyttelse af oplysninger for dataniveauer

   Baseret på dataniveauer bestemte Contoso detaljerede krav for at kvalificere fremtidige it-arbejdsbelastninger, der flyttes til skyen.

For at følge de bedste fremgangsmåder og Microsoft 365 til krav til virksomhedsinstallation har Contoso-sikkerhedsadministratorer og it-afdelingen installeret mange sikkerhedsfunktioner og -egenskaber, som beskrevet i de følgende afsnit.

## <a name="identity-and-access-management"></a>Administration af identitet og adgang 

- Dedikerede globale administratorkonti med MFA og PIM

  I stedet for at tildele den globale administratorrolle til almindelige brugerkonti oprettede Contoso tre dedikerede globale administratorkonti med stærke adgangskoder. Kontiene er beskyttet af Azure AD Multi-Factor Authentication (MFA), og Azure Active Directory (Azure AD) Privileged Identity Management (PIM). *PIM er kun tilgængelig med Microsoft 365 E5.*

  Når du logger på med **en Azure AD DC-administrator** eller **en global administratorkonto** , udføres det kun for bestemte administrative opgaver. Adgangskoderne kendes kun af angivne medarbejdere og kan kun bruges inden for en tidsperiode, der er konfigureret i Azure AD PIM.

  Contoso-sikkerhedsadministratorer tildelte mindre administratorroller til konti, der er relevante for den pågældende it-medarbejders jobfunktion.

  Få mere at vide under [Om Microsoft 365 administratorroller](/office365/admin/add-users/about-admin-roles).

- MFA for alle brugerkonti

  MFA føjer et ekstra lag beskyttelse til logonprocessen. Det kræver, at brugerne skal bekræfte et telefonopkald, en sms-besked eller en appmeddelelse på deres smartphone efter korrekt indtastning af deres adgangskode. Med MFA er Azure AD-brugerkonti beskyttet mod uautoriserede logonoplysninger, også selvom en adgangskode til en konto er kompromitteret.

   - For at beskytte dig mod kompromis med Microsoft 365-abonnementet kræver Contoso MFA på alle **Azure AD DC-administratorer** eller **globale administratorkonti**.
   - For at beskytte dig mod phishingangreb, hvor en hacker kompromitterer legitimationsoplysningerne for en person i organisationen, der er tillid til, og sender ondsindede mails, aktiverede Contoso MFA på alle brugerkonti, herunder ledere og ledere.

- Mere sikker enheds- og programadgang med politikker for betinget adgang

  Contoso bruger [Betingede adgangspolitikker](../security/office-365-security/microsoft-365-policies-configurations.md) til identitet, enheder, Exchange Online og SharePoint. Politikker for betinget adgang til identitet omfatter krav om ændringer af adgangskode for brugere med høj risiko og blokering af klienter fra at bruge apps, der ikke understøtter moderne godkendelse. Enhedspolitikker omfatter definitionen af godkendte apps og kræver kompatible pc'er og mobilenheder. Exchange Online politikker for betinget adgang omfatter blokering af ActiveSync-klienter og konfiguration Office 365 kryptering af meddelelser. SharePoint Betingede adgangspolitikker omfatter yderligere beskyttelse af følsomme og meget regulerede websteder.

- Windows Hello for Business

  Contoso installeret [Windows Hello for Business](/windows/security/identity-protection/hello-for-business/hello-identity-verification) for på et tidspunkt at fjerne behovet for adgangskoder via stærk tofaktorgodkendelse på pc'er og mobilenheder, der kører Windows 10 Enterprise.

- Windows Defender Credential Guard

  For at blokere målrettede angreb og malware i operativsystemet med administratorrettigheder aktiverede Contoso [Windows Defender Credential Guard](/windows/security/identity-protection/credential-guard/credential-guard) AD DS gruppepolitik.

## <a name="threat-protection"></a>Trusselsbeskyttelse

- Beskyttelse mod malware med Windows Defender Antivirus

  Contoso [bruger Windows Defender Antivirus til](/windows/security/threat-protection/windows-defender-antivirus/windows-defender-antivirus-in-windows-10) malwarebeskyttelse og antimalwarestyring for pc'er og enheder, der Windows 10 Enterprise.

- Sikker logføring af mailflow og postkassekontrol med Microsoft Defender Office 365 

  Contoso bruger Exchange Online Protection [og Defender til Office 365](/office365/securitycompliance/office-365-atp) at beskytte mod ukendt malware, virus og skadelige URL-adresser, der overføres via mails.

  Contoso har også aktiveret logføring af postkassekontrol for at identificere, hvem der logger på brugerpostkasser, sender meddelelser og laver andre aktiviteter, der udføres af ejeren af postkassen, en delegeret bruger eller en administrator.

- Overvågning og forebyggelse af angreb med Office 365 trusselsundersøgelse og -svar

  Contoso bruger [Office 365 trusselsundersøgelse](/office365/securitycompliance/office-365-ti) og svar til at beskytte brugerne ved at gøre det nemt at identificere og tage hånd om angreb og for at forhindre fremtidige angreb.

- Beskyttelse mod avancerede angreb med Advanced Threat Analytics

  Contoso bruger [Advanced Threat Analytics (ATA) til at beskytte](/advanced-threat-analytics/what-is-ata) sig selv mod avancerede målrettede angreb.  ATA analyserer, lærer og identificerer automatisk normal og unormal adfærd (bruger, enheder og ressourcer).

## <a name="information-protection"></a>Beskyttelse af oplysninger

- Beskyt følsomme og meget regulerede digitale aktiver med Azure Information Protection-etiketter

  Contoso bestemte tre niveauer af databeskyttelse og implementerede Microsoft 365 [følsomhedsmærkater](../compliance/sensitivity-labels.md), som brugerne anvender på digitale aktiver. For sine forretningshemmeligheder og andre immaterielle ejendomsrettigheder anvender Contoso følsomhedsundergrupper til meget regulerede data. Denne proces krypterer indhold og begrænser adgangen til bestemte brugerkonti og grupper.

- Undgå lækager fra intranetdata med forebyggelse af datatab

  Contoso-konfigurerede [politikker](../compliance/dlp-learn-about-dlp.md) til forebyggelse af datatab for Exchange Online, SharePoint og OneDrive for Business for at forhindre brugere i utilsigtet eller tilsigtet deling af følsomme data.

- Undgå, at enhedens datalækager Windows Information Protection

  Contoso bruger [Windows Information Protection (WIP)](/windows/security/information-protection/windows-information-protection/protect-enterprise-data-using-wip) til at beskytte mod datalækage gennem internetbaserede apps og tjenester og virksomhedsapps og data på virksomhedsejede enheder og personlige enheder, som medarbejdere tager med i arbejdet.

- Skyovervågning med Microsoft Defender til skyapps

  Contoso bruger [Microsoft Defender til skyapps](/cloud-app-security/what-is-cloud-app-security) til at kortlægge deres skymiljø, overvåge brugen af det og registrere sikkerhedshændelser og hændelser. *Microsoft Defender til skyapps er kun tilgængelig med Microsoft 365 E5.*

- Enhedshåndtering med Microsoft Intune

  Contoso bruger [Microsoft Intune](/intune/introduction-intune) til at tilmelde, administrere og konfigurere adgang til mobilenheder og de apps, der kører på dem. Enhedsbaserede politikker for Betinget adgang kræver også godkendte apps og kompatible pc'er og mobilenheder.

## <a name="security-management"></a>Sikkerhedsadministration

- Dashboard til central sikkerhed for it med Microsoft Defender for Cloud

  Contoso bruger [Microsoft Defender for Cloud](https://azure.microsoft.com/services/security-center/) til at præsentere en samlet visning af sikkerhed og trusselsbeskyttelse, administrere sikkerhedspolitikker på tværs af arbejdsbelastningen og reagere på cyberangreb.

- Central security dashboard for brugere med Windows Defender Security Center

  Contoso har installeret [Windows Sikkerhed-appen](/windows/security/threat-protection/windows-defender-security-center/windows-defender-security-center) på dens pc'er og enheder, der kører Windows 10 Enterprise, så brugerne hurtigt kan se deres sikkerhedsstilling og handle på den.
