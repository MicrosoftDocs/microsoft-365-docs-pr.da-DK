---
title: Oversigt over Microsoft 365 for virksomhedssikkerhed for Contoso Corporation
author: kelleyvice-msft
f1.keywords:
- NOCSH
ms.author: kvice
manager: scotv
ms.date: 10/02/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
ms.custom: ''
description: Sådan bruger Contoso sikkerhedsfunktionerne i Microsoft 365 for enterprise.
ms.openlocfilehash: 7ffde6eec3e5f294311926fa013d9e089ad67e0f
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65091319"
---
# <a name="summary-of-microsoft-365-for-enterprise-security-for-the-contoso-corporation"></a>Oversigt over Microsoft 365 for virksomhedssikkerhed for Contoso Corporation

Contoso IT-sikkerhedsafdelingen foretog en grundig sikkerhedsgennemgang for at få godkendelse til at udrulle Microsoft 365 til virksomheder. De identificerede følgende sikkerhedskrav til cloudmiljøet:

- Brug de stærkeste godkendelsesmetoder til medarbejderadgang til cloudressourcer.
- Sørg for, at pc'er og mobilenheder opretter forbindelse til og får adgang til programmer på sikre måder.
- Beskyt pc'er og mail mod malware.
- Tilladelser til cloudbaserede digitale aktiver definerer, hvem der kan få adgang til, hvad og hvad de kan gøre, og de er designet til at give færrest mulige rettigheder
- Følsomme og stærkt regulerede digitale aktiver mærkes, krypteres og gemmes på sikre placeringer.
- Stærkt regulerede digitale aktiver er beskyttet med yderligere kryptering og tilladelser.
- It-sikkerhedspersonalet kan overvåge den aktuelle sikkerhedsholdning fra centrale dashboards og få besked om sikkerhedshændelser med henblik på hurtig reaktion og afhjælpning.

## <a name="the-contoso-path-to-microsoft-365-security-readiness"></a>Contoso-stien til Microsoft 365 sikkerhedsparathed

Contoso fulgte disse trin for at forberede deres sikkerhed på deres udrulning af Microsoft 365 til virksomheder:

1. Begræns administratorkonti for cloudmiljøet

   Contoso foretog en omfattende gennemgang af sine eksisterende ad DS-administratorkonti (Active Directory-domæneservices) og konfigurerede en række dedikerede cloudadministratorkonti og -grupper.

2. Klassificer data i tre sikkerhedsniveauer

   Contoso foretog en omhyggelig gennemgang og bestemte de tre niveauer, som blev brugt til at identificere Microsoft 365 for virksomhedsfunktioner for at beskytte de mest værdifulde data.

3. Fastlæg politikker for adgang, opbevaring og beskyttelse af oplysninger for dataniveauer

   På baggrund af dataniveauerne fastsatte Contoso detaljerede krav for at kvalificere fremtidige it-arbejdsbelastninger, der flyttes til cloudmiljøet.

For at følge bedste praksis for sikkerhed og Microsoft 365 i forbindelse med installationskrav til virksomheder har Contoso-sikkerhedsadministratorer og it-afdelingen installeret mange sikkerhedsfunktioner og -egenskaber, som beskrevet i følgende afsnit.

## <a name="identity-and-access-management"></a>Identitets- og adgangsstyring 

- Dedikerede globale administratorkonti med MFA og PIM

  I stedet for at tildele den globale administratorrolle til almindelige brugerkonti oprettede Contoso tre dedikerede globale administratorkonti med stærke adgangskoder. Kontiene er beskyttet af Azure AD Multi-Factor Authentication (MFA) og Azure Active Directory (Azure AD) Privileged Identity Management (PIM). *PIM er kun tilgængelig med Microsoft 365 E5.*

  Når du logger på med en **Azure AD DC-administrator** eller **en global administratorkonto** , udføres det kun for bestemte administrative opgaver. Adgangskoderne kendes kun af udpegede medarbejdere og kan kun bruges inden for en tidsperiode, der er konfigureret i Azure AD PIM.

  Contoso-sikkerhedsadministratorer tildelte mindre administratorroller til konti, der er relevante for it-arbejderens jobfunktion.

  Du kan få flere oplysninger under [Om Microsoft 365 administratorroller](/office365/admin/add-users/about-admin-roles).

- MFA for alle brugerkonti

  MFA føjer et ekstra beskyttelseslag til logonprocessen. Det kræver, at brugerne bekræfter et telefonopkald, en sms eller en appmeddelelse på deres smartphone, når de har indtastet deres adgangskode korrekt. Med MFA er Azure AD-brugerkonti beskyttet mod uautoriseret logon, selvom en adgangskode til en konto kompromitteres.

   - Contoso kræver MFA på alle **Azure AD DC-administratorer** eller **globale administratorkonti** for at beskytte mod kompromitteret Microsoft 365-abonnement.
   - For at beskytte mod phishing-angreb, hvor en hacker kompromitterer legitimationsoplysningerne for en person, der er tillid til, i organisationen og sender skadelige mails, aktiverede Contoso MFA på alle brugerkonti, herunder ledere og direktører.

- Sikrere adgang til enheder og programmer med politikker for betinget adgang

  Contoso bruger [politikker for betinget adgang](../security/office-365-security/microsoft-365-policies-configurations.md) for identitet, enheder, Exchange Online og SharePoint. Politikker for betinget adgang til identitet omfatter krav om adgangskodeændringer for brugere med høj risiko og blokering af klienter fra at bruge apps, der ikke understøtter moderne godkendelse. Enhedspolitikker omfatter definitionen af godkendte apps og krav om kompatible pc'er og mobilenheder. Exchange Online politikker for betinget adgang omfatter blokering af ActiveSync-klienter og konfiguration af Office 365 meddelelsekryptering. SharePoint politikker for betinget adgang omfatter yderligere beskyttelse af følsomme og stærkt regulerede websteder.

- Windows Hello til virksomheder

  Contoso udrullede [Windows Hello til virksomheder](/windows/security/identity-protection/hello-for-business/hello-identity-verification) for til sidst at fjerne behovet for adgangskoder via stærk tofaktorgodkendelse på pc'er og mobilenheder, der kører Windows 10 Enterprise.

- Windows Defender Credential Guard

  Contoso aktiverede [Windows Defender Credential Guard](/windows/security/identity-protection/credential-guard/credential-guard) via AD DS-gruppepolitik for at blokere målrettede angreb og malware, der kører i operativsystemet med administrative rettigheder.

## <a name="threat-protection"></a>Trusselsbeskyttelse

- Beskyttelse mod malware med Windows Defender Antivirus

  Contoso bruger [Windows Defender Antivirus](/windows/security/threat-protection/windows-defender-antivirus/windows-defender-antivirus-in-windows-10) til beskyttelse mod skadelig software og administration af antimalware på pc'er og enheder, der kører Windows 10 Enterprise.

- Logføring af sikker mailflow og postkasseovervågning med Microsoft Defender for Office 365 

  Contoso bruger Exchange Online Protection og [Defender for Office 365](/office365/securitycompliance/office-365-atp) til at beskytte mod ukendt malware, virus og skadelige URL-adresser, der sendes via mails.

  Contoso har også aktiveret logføring af overvågning af postkasser for at identificere, hvem der logger på brugerpostkasser, sender meddelelser og udfører andre aktiviteter, der udføres af postkasseejeren, en delegeret bruger eller en administrator.

- Overvågning og forebyggelse af angreb med Office 365 trusselsundersøgelse og -reaktion

  Contoso bruger [Office 365 trusselsundersøgelse og -svar](/office365/securitycompliance/office-365-ti) til at beskytte brugerne ved at gøre det nemt at identificere og håndtere angreb og forhindre fremtidige angreb.

- Beskyttelse mod avancerede angreb med Advanced Threat Analytics

  Contoso bruger [ATA (Advanced Threat Analytics)](/advanced-threat-analytics/what-is-ata) til at beskytte sig selv mod avancerede målrettede angreb.  ATA analyserer, lærer og identificerer automatisk normal og unormal enhedsfunktionsmåde (bruger, enheder og ressourcer).

## <a name="information-protection"></a>Beskyttelse af oplysninger

- Beskyt følsomme og stærkt regulerede digitale aktiver med Azure Information Protection-mærkater

  Contoso bestemte tre niveauer af databeskyttelse og udrullede [Microsoft 365 følsomhedsmærkater](../compliance/sensitivity-labels.md), som brugerne anvender på digitale aktiver. Contoso bruger følsomhedsundermærkler til stærkt regulerede data for sine forretningshemmeligheder og andre immaterielle rettigheder. Denne proces krypterer indhold og begrænser adgangen til bestemte brugerkonti og -grupper.

- Undgå intranetdatalækager med forebyggelse af datatab

  Contoso har konfigureret [Microsoft Purview-politikker til forebyggelse af datatab](../compliance/dlp-learn-about-dlp.md) for Exchange Online, SharePoint og OneDrive for Business for at forhindre, at brugerne utilsigtet eller bevidst deler følsomme data.

- Undgå, at enhedens datalækager Windows Information Protection

  Contoso bruger [Windows Information Protection (WIP)](/windows/security/information-protection/windows-information-protection/protect-enterprise-data-using-wip) til at beskytte mod datalækage via internetbaserede apps og tjenester og virksomhedsapps og data på virksomhedsejede enheder og personlige enheder, som medarbejderne bringer på arbejde.

- Cloudovervågning med Microsoft Defender for Cloud Apps

  Contoso bruger [Microsoft Defender for Cloud Apps](/cloud-app-security/what-is-cloud-app-security) til at kortlægge deres cloudmiljø, overvåge dets brug og registrere sikkerhedshændelser og hændelser. *Microsoft Defender for Cloud Apps er kun tilgængelig med Microsoft 365 E5.*

- Enhedshåndtering med Microsoft Intune

  Contoso bruger [Microsoft Intune](/intune/introduction-intune) til at tilmelde, administrere og konfigurere adgang til mobilenheder og de apps, der kører på dem. Enhedsbaserede politikker for betinget adgang kræver også godkendte apps og kompatible pc'er og mobilenheder.

## <a name="security-management"></a>Sikkerhedsadministration

- Central sikkerhedsdashboard til it med Microsoft Defender for Cloud

  Contoso bruger [Microsoft Defender for Cloud](https://azure.microsoft.com/services/security-center/) til at præsentere en samlet visning af sikkerhed og trusselsbeskyttelse, til at administrere sikkerhedspolitikker på tværs af sine arbejdsbelastninger og til at reagere på cyberangreb.

- Dashboard til central sikkerhed for brugere med Windows Defender Security Center

  Contoso udrullede [Windows Sikkerhed-appen](/windows/security/threat-protection/windows-defender-security-center/windows-defender-security-center) på sine pc'er og enheder, der kører Windows 10 Enterprise, så brugerne hurtigt kan se deres sikkerhedsholdning og udføre handlinger.
