---
title: Information protection for the Contoso Corporation
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
description: Forstå, hvordan Contoso bruger funktionerne til beskyttelse af oplysninger i Microsoft 365 for virksomheder til at sikre deres digitale aktiver i cloudmiljøet.
ms.openlocfilehash: 70d5a0a6fba7204177771256d9a508c76a010d6d
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/19/2022
ms.locfileid: "64931577"
---
# <a name="information-protection-for-the-contoso-corporation"></a>Information protection for the Contoso Corporation

Contoso mener det alvorligt med deres informationssikkerhed. Lækage eller ødelæggelse af intellektuel ejendom, der beskriver deres produktdesign og beskyttede produktionsteknikker, vil stille dem ringere i konkurrencen.

Før Contoso flyttede deres følsomme digitale aktiver til cloudmiljøet, sørgede han for, at deres krav til klassificering og beskyttelse i det lokale miljø blev understøttet af cloudbaserede tjenester fra Microsoft 365 for enterprise.

## <a name="contoso-data-security-classification"></a>Contoso-datasikkerhedsklassificering

Contoso udførte en analyse af deres data og bestemte følgende klassificeringsniveauer.

| Niveau 1: Oprindelig plan | Niveau 2: Følsom | Niveau 3: Stærkt reguleret |
|:-------|:-----|:-----|
| Data er krypteret og kun tilgængelige for godkendte brugere.<BR> <BR> Leveres til alle data, der er gemt i det lokale miljø og i cloudbaseret lager og arbejdsbelastninger. Data krypteres, mens de er placeret i tjenesten og under overførsel mellem tjenesten og klientenhederne. <BR><BR>Eksempler på niveau 1-data er normal forretningskommunikation (e-mail) og filer til administrative, salg og supportmedarbejdere. | Niveau 1 plus stærk godkendelse og beskyttelse af datatab.<BR> <BR> Stærk godkendelse omfatter Azure AD Multi-Factor Authentication (MFA) med SMS-validering. Microsoft Purview Forebyggelse af datatab sikrer, at følsomme eller kritiske oplysninger ikke bevæger sig uden for Microsoft-cloudmiljøet.<BR><BR>Eksempler på niveau 2-data er økonomiske og juridiske oplysninger samt forsknings- og udviklingsdata for nye produkter. | Niveau 2 plus de højeste niveauer af kryptering, godkendelse og overvågning.<BR><BR>Det højeste krypteringsniveau for inaktive data og i cloudmiljøet, der overholder regionale regler, kombineret med MFA med chipkort og detaljeret overvågning og advarsler.<BR> <BR>Eksempler på niveau 3-data er personlige oplysninger om kunder og partnere, produktkonstruktionsspecifikationer og teknikker til fremstilling af ejendomsret.  |
||||

## <a name="contoso-information-policies"></a>Contoso-informationspolitikker
I følgende tabel vises Contoso-informationspolitikkerne.


| Værdi | Access | Datalagring | Beskyttelse af oplysninger |
|:-------|:-----|:-----|:-----|
| Lav forretningsværdi (niveau 1: oprindelig plan) | Tillad adgang til alle.  | 6 måneder | Brug kryptering. |
| Mellem forretningsværdi (niveau 2: Følsom) | Giv adgang til Contoso-medarbejdere, underleverandører og partnere. <BR><BR> Brug MFA, TLS (Transport Layer Security) og MAM (Mobile Application Management). | 2 år  | Brug hashværdier til dataintegritet.  |
| Høj forretningsværdi (niveau 3: Stærkt reguleret) | Giv adgang til direktører og kundeemner inden for teknik og produktion. <BR> <BR> RMS (Rights Management System) med administrerede netværksenheder.  | 7 år  | Brug digitale signaturer til ikke-afvisning.  |
|||||

## <a name="the-contoso-path-to-information-protection-with-microsoft-365-for-enterprise"></a>Contoso-stien til information protection med Microsoft 365 for enterprise

Contoso fulgte disse trin for at forberede Microsoft 365 til virksomheder til deres krav til information-beskyttelse:

1. Identificer, hvilke oplysninger der skal beskyttes

   Contoso foretog en omfattende gennemgang af deres eksisterende digitale aktiver, der er placeret i det lokale miljø SharePoint websteder og filshares og klassificerede hvert aktiv.

2. Fastlæg politikker for adgang, opbevaring og beskyttelse af oplysninger for dataniveauer

   På baggrund af dataniveauerne fastsatte Contoso detaljerede politikkrav, som blev brugt til at beskytte eksisterende digitale aktiver, efterhånden som de blev flyttet til cloudmiljøet.

3. Opret følsomhedsmærkater og deres indstillinger for de forskellige informationsniveauer

   Contoso oprettede følsomhedsmærkater for deres dataniveauer med deres højt regulerede mærkat, der omfatter kryptering, tilladelser og vandmærker.

4. Flyt data fra SharePoint-websteder og filshares i det lokale miljø til deres nye SharePoint websteder

    De filer, der er overført til de nye SharePoint websteder, nedarvede de standardopbevaringsmærkater, der er tildelt webstedet.

5. Oplær medarbejdere, hvordan de bruger følsomhedsmærkater til nye dokumenter, hvordan de interagerer med Contoso IT, når de opretter nye SharePoint websteder, og til altid at gemme digitale aktiver på SharePoint websteder

    Ændring af dårlige vaner med informationslager for medarbejdere anses ofte for at være den hårdeste del af overgangen til information protection for cloudmiljøet. Contoso it og administration, der er nødvendig for altid at få medarbejderne til altid at mærke og gemme deres digitale aktiver i cloudmiljøet, afholde sig fra at bruge filshares i det lokale miljø og ikke bruge cloudlagertjenester eller USB-drev fra tredjepart.

## <a name="conditional-access-policies-for-information-protection"></a>Politikker for betinget adgang til information

Som en del af udrulningen af Exchange Online og SharePoint konfigurerede Contoso følgende sæt politikker for betinget adgang og anvendte dem på de relevante grupper:

- [Administreret og ikke-administreret programadgang på enheders politikker](../security/office-365-security/identity-access-policies.md)
- [Exchange Online adgangspolitikker](../security/office-365-security/secure-email-recommended-policies.md)
- [SharePoint adgangspolitikker](../security/office-365-security/sharepoint-file-access-policies.md)

Her er det resulterende sæt Contoso-politikker til beskyttelse af oplysninger.

:::image type="content" alt-text="Politikker for enhed, Exchange Online og SharePoint betinget adgang." source="../media/contoso-info-protect/contoso-info-protect-fig1.png" lightbox="../media/contoso-info-protect/contoso-info-protect-fig1.png":::

>[!Note]
>Contoso konfigurerede også yderligere politikker for betinget adgang for identitet og logon. Se [Identitet for Contoso Corporation](contoso-identity.md#conditional-access-policies-for-zero-trust-identity-and-device-access).
>

Disse politikker sikrer, at:

- Apps, der er tilladt, og de handlinger, de kan foretage med organisationens data, er defineret af politikker for appbeskyttelse.
- Pc'er og mobilenheder skal være kompatible.
- Exchange Online bruger OME (Office 365 message encryption) til Exchange Online.
- SharePoint bruger app-gennemtvungne begrænsninger.
- SharePoint bruger politikker for adgangskontrol til browseradgang og til at blokere adgang for ikke-administrerede enheder.

## <a name="mapping-microsoft-365-for-enterprise-features-to-contoso-data-levels"></a>Tilknytning af Microsoft 365 for virksomhedsfunktioner til Contoso-dataniveauer

I følgende tabel knyttes Contoso-dataniveauer til funktioner til beskyttelse af oplysninger i Microsoft 365 for virksomheder.

| Niveau | Microsoft 365 cloudtjenester | Windows 10 og Microsoft 365 Apps for enterprise | Sikkerhed og overholdelse af angivne standarder |
|:-------|:-----|:-----|:-----|
| Niveau 1: Oprindelig plan  | politikker for betinget adgang SharePoint og Exchange Online <BR> Tilladelser til SharePoint websteder | Følsomhedsmærkater <BR> Bitlocker <BR> Windows Information Protection | Politikker for betinget adgang for enhed og politikker for administration af mobilapps |
| Niveau 2: Følsom | Niveau 1 plus: <BR> <BR> Følsomhedsmærkater <BR> Microsoft 365 opbevaringsmærkater på SharePoint websteder <BR> Forebyggelse af datatab for SharePoint og Exchange Online <BR> Isolerede SharePoint websteder  | Niveau 1 plus: <BR> <BR> Følsomhedsmærkater på digitale aktiver  | Niveau 1 |
| Niveau 3: Stærkt reguleret | Niveau 2 plus: <BR><BR> Byok-kryptering (Bring Your Own Key) og beskyttelse af fortrolige oplysninger <BR> Azure Key Vault til line of business-programmer, der interagerer med Microsoft 365-tjenester | Niveau 2 | Niveau 1 |
|||||

Her er den resulterende konfiguration af Contoso information-protection.

:::image type="content" alt-text="Contosos resulterende konfiguration af beskyttelse af oplysninger." source="../media/contoso-info-protect/contoso-info-protect-fig2.png":::

## <a name="next-step"></a>Næste trin

Få mere at vide om, hvordan Contoso bruger [sikkerhedsfunktionerne på tværs af Microsoft 365 til enterprise for](contoso-security-summary.md) identitets- og adgangsstyring, trusselsbeskyttelse, informationsbeskyttelse og sikkerhedsadministration.

## <a name="see-also"></a>Se også

[Sikkerhedsoversigt](../security/office-365-security/security-roadmap.md)

[Microsoft 365 til virksomhedsoversigt](microsoft-365-overview.md)

[Vejledninger til testlaboratorier](m365-enterprise-test-lab-guides.md)