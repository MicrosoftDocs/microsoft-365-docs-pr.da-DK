---
title: Identitet for Contoso Corporation
author: kelleyvice-msft
f1.keywords:
- NOCSH
ms.author: kvice
manager: scotv
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- M365-identity-device-management
- Strat_O365_Enterprise
ms.custom: ''
description: Sådan udnytter Contoso Identitet som en tjeneste (IDaaS) og leverer cloudbaseret godkendelse til sine medarbejdere og samlet godkendelse til sine partnere og kunder.
ms.openlocfilehash: fc53ae761f26776c4bd632704505d2eafe8daa88
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65094432"
---
# <a name="identity-for-the-contoso-corporation"></a>Identitet for Contoso Corporation

Microsoft leverer IDaaS (Identity as a Service) på tværs af sine cloudtilbud via Azure Active Directory (Azure AD). For at kunne anvende Microsoft 365 til virksomheder skulle Contoso IDaaS-løsningen bruge deres identitetsudbyder i det lokale miljø og inkludere sammenkædet godkendelse med deres eksisterende identitetsudbydere, der er tillid til.

## <a name="the-contoso-active-directory-domain-services-forest"></a>Contoso Active Directory-domæneservices skov

Contoso bruger en enkelt Active Directory-domæneservices skov (AD DS) til contosocom\. med syv underdomæner, ét for hver region i verden. Hovedkvarteret, regionale hubkontorer og satellitkontorer indeholder domænecontrollere til lokal godkendelse og autorisation.

Her er Contoso-skoven med regionale domæner for de forskellige dele af verden, der indeholder regionale hubs.

:::image type="content" alt-text="Contosos skov og domæner over hele verden." source="../media/contoso-identity/contoso-identity-fig1.png" lightbox="../media/contoso-identity/contoso-identity-fig1.png":::
 
Contoso besluttede at bruge konti og grupper i contosocom-området\. til godkendelse og godkendelse til sine Microsoft 365 arbejdsbelastninger og -tjenester.

## <a name="the-contoso-federated-authentication-infrastructure"></a>Godkendelsesinfrastrukturen i Contoso-organisationsnetværket

Contoso tillader:

- Kunder til at bruge deres Microsoft-, Facebook- eller Google Mail-konti til at logge på virksomhedens offentlige hjemmeside.
- Leverandører og partnere til at bruge deres LinkedIn-, Salesforce- eller Google Mail-konti til at logge på virksomhedens partner-ekstranet.

Her er Contoso DMZ, der indeholder et offentligt websted, et partner-ekstranet og et sæt Active Directory Federation Services (AD FS) servere. DMZ har forbindelse til det internet, der indeholder kunder, partnere og internettjenester.

![Contoso-understøttelse af godkendelse i organisationsnetværk for kunder og partnere.](../media/contoso-identity/contoso-identity-fig2.png)
 
AD FS-servere i DMZ faciliterer godkendelse af kundelegitimationsoplysninger af deres identitetsudbydere for at få adgang til det offentlige websted og partnerlegitimationsoplysninger for at få adgang til partnerens ekstranet.

Contoso besluttede at beholde denne infrastruktur og dedikere den til kunde- og partnergodkendelse. Contoso-identitetsarkitekter undersøger konverteringen af denne infrastruktur til Azure AD [B2B](/azure/active-directory/b2b/hybrid-organizations) - og [B2C-løsninger](/azure/active-directory-b2c/solution-articles) .

## <a name="hybrid-identity-with-password-hash-synchronization-for-cloud-based-authentication"></a>Hybrididentitet med synkronisering af adgangskodehash til skybaseret godkendelse

Contoso ønskede at bruge AD DS-området i det lokale miljø til godkendelse til at Microsoft 365 cloudressourcer. Det besluttede at bruge synkronisering af adgangskodehash (PHS).

PHS synkroniserer AD DS-området i det lokale miljø med Azure AD-lejeren for deres Microsoft 365 til virksomhedsabonnement, kopierer bruger- og gruppekonti og en hashkodet version af adgangskoder til brugerkonti.

Contoso udrullede Azure AD Forbind-værktøjet på en server i sit Paris-datacenter for at udføre katalogsynkronisering.

Her er den server, der kører Azure AD Forbind forespørge Contoso AD DS-området om ændringer og derefter synkronisere disse ændringer med Azure AD-lejeren.

![Infrastrukturen til synkronisering af Contoso PHS-kataloger.](../media/contoso-identity/contoso-identity-fig4.png)
 
## <a name="conditional-access-policies-for-zero-trust-identity-and-device-access"></a>Politikker for betinget adgang for Nul tillid identitet og enhedsadgang

Contoso oprettede et sæt Azure AD- og Intune [politikker for betinget adgang](../security/office-365-security/identity-access-policies.md) for tre beskyttelsesniveauer:

- *Startpunktbeskyttelse* gælder for alle brugerkonti.
- *Beskyttelse af virksomheder* gælder for ledende ledere og ledelsespersonale.
- *Specialiseret sikkerhedsbeskyttelse* gælder for bestemte brugere inden for økonomi-, juridiske og forskningsafdelinger, der har adgang til stærkt regulerede data.

Her er det resulterende sæt Contoso-identitets- og enhedspolitikker for betinget adgang.

:::image type="content" alt-text="Contosos politikker for betinget adgang til identitet og enhed." source="../media/contoso-identity/contoso-identity-fig5.png" lightbox="../media/contoso-identity/contoso-identity-fig5.png":::
 
## <a name="next-step"></a>Næste trin

Få mere at vide om, hvordan Contoso bruger sin Microsoft Endpoint Configuration Manager infrastruktur til at [udrulle og bevare aktuelle Windows 10 Enterprise](contoso-win10.md) på tværs af organisationen.

## <a name="see-also"></a>Se også

[Udrul identitet for Microsoft 365](deploy-identity-solution-overview.md)

[Microsoft 365 til virksomhedsoversigt](microsoft-365-overview.md)

[Vejledninger til testlaboratorier](m365-enterprise-test-lab-guides.md)