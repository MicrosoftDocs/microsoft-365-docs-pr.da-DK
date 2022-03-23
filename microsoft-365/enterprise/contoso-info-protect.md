---
title: Beskyttelse af oplysninger for Contoso Corporation
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
description: Få mere at vide om, hvordan Contoso bruger funktionerne til beskyttelse af oplysninger i Microsoft 365 til virksomheder til at sikre deres digitale aktiver i skyen.
ms.openlocfilehash: 1dff2cadd5afa66b3b469a2debedddbb347db0e5
ms.sourcegitcommit: 07405a81513d1c63071a128b9d5070d3a3bfe1cd
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/19/2021
ms.locfileid: "63588683"
---
# <a name="information-protection-for-the-contoso-corporation"></a>Beskyttelse af oplysninger for Contoso Corporation

Contoso er seriøs i sin informationssikkerhed. Lækage eller udvikling af intellektuel ejendom, der beskriver deres produktdesign og beskyttede produktionsteknikker, vil medføre konkurrencemæssige ulemper.

Før du flyttede deres følsomme digitale aktiver til skyen, sørgede Contoso for, at deres lokale krav til klassificering og beskyttelse af oplysninger var understøttet af skybaserede tjenester af Microsoft 365 til virksomheder.

## <a name="contoso-data-security-classification"></a>Datasikkerhedsklassificering for Contoso

Contoso udførte en analyse af deres data og bestemte følgende klassificeringsniveauer.

| Niveau 1: Oprindelig plan | Niveau 2: Følsom | Niveau 3: Meget regulerede |
|:-------|:-----|:-----|
| Data krypteres og er kun tilgængelige for godkendte brugere.<BR> <BR> Leveres for alle data, der er gemt lokalt og i skybaseret lager og arbejdsbelastninger. Data krypteres, mens de befinder sig i tjenesten og under overførsel mellem tjenesten og klientenhederne. <BR><BR>Eksempler på niveau 1-data er normal forretningskommunikation (mail) og filer for administrative medarbejdere, salgsmedarbejdere og supportmedarbejdere. | Niveau 1 plus stærk godkendelse og beskyttelse mod datatab.<BR> <BR> Stærk godkendelse omfatter Azure AD Multi-Factor Authentication (MFA) med sms-validering. Forebyggelse af datatab sikrer, at følsomme eller kritiske oplysninger ikke finder sted uden for Microsofts sky.<BR><BR>Eksempler på niveau 2-data er finansielle og juridiske oplysninger samt oplysninger om forskning og udvikling for nye produkter. | Niveau 2 plus det højeste niveau af kryptering, godkendelse og overvågning.<BR><BR>De højeste niveauer af kryptering af data på hvile og i skyen, der overholder regionale bestemmelser kombineret med MFA med chipkort og detaljeret overvågning og advarsel.<BR> <BR>Eksempler på niveau 3-data er personlige oplysninger fra kunder og partnere, produktteknikspecifikationer og beskyttede produktionsteknikker.  |
||||

## <a name="contoso-information-policies"></a>Contoso-oplysningspolitikker
I følgende tabel vises Contoso-oplysningspolitikkerne.


| Værdi | Access | Dataopbevaring | Beskyttelse af oplysninger |
|:-------|:-----|:-----|:-----|
| Lav forretningsværdi (niveau 1: Oprindelig plan) | Tillad adgang til alle.  | 6 måneder | Brug kryptering. |
| Mellemstor forretningsværdi (niveau 2: Følsom) | Tillad adgang til Contoso-medarbejdere, underleverandører og partnere. <BR><BR> Brug MFA, Transport Layer Security (TLS) og administration af mobilapps (MAM). | 2 år  | Brug hash-værdier til dataintegritet.  |
| Høj forretningsværdi (niveau 3: Højt regulerede) | Tillad adgang til ledere og kundeemner inden for teknik og produktion. <BR> <BR> Kun med administrerede netværksenheder (Rights Management System) med RMS.  | 7 år  | Brug digitale signaturer til ikke-afvisning.  |
|||||

## <a name="the-contoso-path-to-information-protection-with-microsoft-365-for-enterprise"></a>Contoso-stien til beskyttelse af oplysninger med Microsoft 365 til virksomheder

Contoso har fulgt disse trin for at forberede Microsoft 365 til virksomheder til deres krav til beskyttelse af oplysninger:

1. Identificer, hvilke oplysninger der skal beskyttes

   Contoso gennemvurdering af deres eksisterende digitale aktiver, der er placeret lokalt, SharePoint websteds- og filshares og klassificerede hvert aktiv.

2. Fastsæt politikker for adgang, opbevaring og beskyttelse af oplysninger for dataniveauer

   Baseret på dataniveauerne bestemte Contoso detaljerede politikkrav, som blev brugt til at beskytte eksisterende digitale aktiver, da de blev flyttet til skyen.

3. Opret følsomhedsmærkater og deres indstillinger for de forskellige niveauer af oplysninger

   Contoso oprettede følsomhedsmærkater for deres dataniveauer med deres meget regulerede etikette, der omfatter kryptering, tilladelser og vandmærker.

4. Flytte data fra lokale SharePoint og filshares til deres nye SharePoint websteder

    De filer, der blev overført til den nye SharePoint fra de standardopbevaringsnavne, der blev tildelt webstedet.

5. Oplære medarbejderne, hvordan de bruger følsomhedsmærkater til nye dokumenter, hvordan de interagerer med Contoso IT, når de opretter nye SharePoint-websteder, og til altid at gemme digitale aktiver på SharePoint websteder

    Ændring af vaner for informationlagring for en dårlig medarbejder betragtes ofte som den sværeste del af overgangen til informationsbeskyttelse i skyen. Contoso IT og administration er nødvendig for at få medarbejdere til altid at navnmærke og gemme deres digitale aktiver i skyen, ikke at bruge lokale filshares og ikke bruge skylagertjenester fra tredjeparter eller USB-drev.

## <a name="conditional-access-policies-for-information-protection"></a>Politikker for betinget adgang til beskyttelse af oplysninger

Som en del af deres implementering af Exchange Online og SharePoint konfigurerede Contoso følgende sæt af politikker for Betinget adgang og anvendte dem til de relevante grupper:

- [Administreret og ikke-administreret programadgang på enheders politikker](../security/office-365-security/identity-access-policies.md)
- [Exchange Online adgangspolitikker](../security/office-365-security/secure-email-recommended-policies.md)
- [SharePoint adgangspolitikker](../security/office-365-security/sharepoint-file-access-policies.md)

Her er et resultatsæt af Contoso-politikker til beskyttelse af oplysninger.

:::image type="content" alt-text="Politikker for enhed, Exchange Online og SharePoint betinget adgang." source="../media/contoso-info-protect/contoso-info-protect-fig1.png" lightbox="../media/contoso-info-protect/contoso-info-protect-fig1.png":::

>[!Note]
>Contoso konfigurerede også yderligere Betingede adgangspolitikker for identitet og logon. Se [Identitet for Contoso Corporation](contoso-identity.md#conditional-access-policies-for-zero-trust-identity-and-device-access).
>

Disse politikker sikrer, at:

- Apps, der er tilladte, og de handlinger, de kan udføre med organisationens data, defineres af politikker for appbeskyttelse.
- Pc'er og mobilenheder skal være kompatible.
- Exchange Online bruger Office 365 (OME) til Exchange Online.
- SharePoint anvender app-tvungne begrænsninger.
- SharePoint bruger adgangskontrolpolitikker til browseradgang og til at blokere adgangen for enheder, der ikke er administrerede.

## <a name="mapping-microsoft-365-for-enterprise-features-to-contoso-data-levels"></a>Tilknytning Microsoft 365 virksomhedsfunktioner til Contoso-dataniveauer

I følgende tabel knyttes Contoso-dataniveauer til funktioner til beskyttelse af oplysninger Microsoft 365 til virksomheder.

| Niveau | Microsoft 365 skytjenester | Windows 10 og Microsoft 365 Apps for enterprise | Sikkerhed og overholdelse af regler og standarder |
|:-------|:-----|:-----|:-----|
| Niveau 1: Oprindelig plan  | SharePoint og Exchange Online politikker for betinget adgang <BR> Tilladelser på SharePoint websteder | Følsomhedsmærkater <BR> BitLocker <BR> Windows beskyttelse af oplysninger | Politikker for betinget adgang for enheder og politikker for administration af mobilapps |
| Niveau 2: Følsom | Niveau 1 plus: <BR> <BR> Følsomhedsmærkater <BR> Microsoft 365 opbevaringsetiketter på SharePoint websteder <BR> Forebyggelse af datatab for SharePoint og Exchange Online <BR> Isolerede SharePoint websteder  | Niveau 1 plus: <BR> <BR> Følsomhedsmærkater på digitale aktiver  | Niveau 1 |
| Niveau 3: Meget regulerede | Niveau 2 plus: <BR><BR> Medbring din egen nøglekryptering (BYOK) og beskyttelse af handelshemmelige oplysninger <BR> Azure Key Vault til line of business-programmer, der interagerer med Microsoft 365 tjenester | Niveau 2 | Niveau 1 |
|||||

Her er den resulterende Contoso-konfiguration til informationsbeskyttelse.

:::image type="content" alt-text="Contosos resulterende konfiguration af informationsbeskyttelse." source="../media/contoso-info-protect/contoso-info-protect-fig2.png":::

## <a name="next-step"></a>Næste trin

Få mere at vide om, hvordan Contoso bruger sikkerhedsfunktionerne på tværs [af Microsoft 365](contoso-security-summary.md) til virksomheder til identitets- og adgangsstyring, trusselsbeskyttelse, beskyttelse af oplysninger og sikkerhedsadministration.

## <a name="see-also"></a>Se også

[Sikkerhedsoversigt](../security/office-365-security/security-roadmap.md)

[Microsoft 365 for Enterprise-oversigt](microsoft-365-overview.md)

[Test labvejledninger](m365-enterprise-test-lab-guides.md)