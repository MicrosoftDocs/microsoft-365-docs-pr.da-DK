---
title: Identitet for Contoso Corporation
author: kelleyvice-msft
f1.keywords:
- NOCSH
ms.author: kvice
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- M365-identity-device-management
- Strat_O365_Enterprise
ms.custom: ''
description: Sådan udnytter Contoso Identitet som en tjeneste (IDaaS) og leverer skybaseret godkendelse til medarbejderne og organisationsnetværksgodkendelse for partnere og kunder.
ms.openlocfilehash: 1e1fb2a74c3c3b491ddfda2b0b88e4ad11926a5a
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/04/2022
ms.locfileid: "63587253"
---
# <a name="identity-for-the-contoso-corporation"></a>Identitet for Contoso Corporation

Microsoft leverer Identity as a Service (IDaaS) på tværs af sine skybaserede tilbud via Azure Active Directory (Azure AD). For at Microsoft 365 til virksomheder skulle Contoso IDaaS-løsningen bruge deres lokale identitetsudbyder og medtage federated authentication med deres eksisterende pålidelige tredjeparts identitetsudbydere.

## <a name="the-contoso-active-directory-domain-services-forest"></a>Contoso Active Directory-domæneservices skoven

Contoso anvender en enkelt Active Directory-domæneservices (AD DS)-skov til contosocom\. med syv underdomæner, én for hvert område i verden. Hovedkontoret, de regionale hubkontorer og satellitkontorer indeholder domænecontrollere til lokal godkendelse og autorisation.

Her er Contoso-skoven med regionale domæner for de forskellige dele af verden, der indeholder regionale hubs.

:::image type="content" alt-text="Contosos skov og domæner over hele verden." source="../media/contoso-identity/contoso-identity-fig1.png" lightbox="../media/contoso-identity/contoso-identity-fig1.png":::
 
Contoso har besluttet at bruge konti og grupper i contosocom-skoven\. til godkendelse og godkendelse til sine Microsoft 365 arbejdsbelastninger og tjenester.

## <a name="the-contoso-federated-authentication-infrastructure"></a>Contoso-organisationsnetværksgodkendelsesinfrastrukturen

Contoso tillader:

- Kunder kan bruge deres Microsoft-, Facebook- eller Google Mail-konti til at logge på virksomhedens offentlige websted.
- Leverandører og partnere kan bruge deres LinkedIn-, Salesforce- eller Google Mail-konti til at logge på virksomhedens partner ekstranet.

Her er Contoso DMZ, der indeholder et offentligt websted, et partner extranet og et sæt af AD FS-servere (Active Directory Federation Services). DMZ har forbindelse til internettet, der indeholder kunder, partnere og internettjenester.

![Contoso-understøttelse til federated authentication for kunder og partnere.](../media/contoso-identity/contoso-identity-fig2.png)
 
AD FS-servere i DMZ letter godkendelse af kundelegitimationsoplysninger af deres identitetsudbydere for at få adgang til det offentlige websted og partnerens legitimationsoplysninger for at få adgang til partner ekstranet.

Contoso har besluttet at beholde denne infrastruktur og dedikere den til kunde- og partnergodkendelse. Contoso-identitetsarkitekter undersøger konverteringen af denne infrastruktur til Azure AD [B2B-](/azure/active-directory/b2b/hybrid-organizations) og [B2C-løsninger](/azure/active-directory-b2c/solution-articles) .

## <a name="hybrid-identity-with-password-hash-synchronization-for-cloud-based-authentication"></a>Hybrididentitet med synkronisering af adgangskodehash til skybaseret godkendelse

Contoso ønskede at bruge sit lokale miljø AD DS til godkendelse for at Microsoft 365 i skyen. Det har besluttet at bruge synkronisering af adgangskodehash (PHS).

PHS synkroniserer området for AD DS i det lokale miljø med Azure AD-lejeren i deres abonnement på Microsoft 365 til store virksomheder, kopiering af bruger- og gruppekonti og en tidligere version af adgangskoder til brugerkonti.

For at udføre katalogsynkronisering har Contoso installeret Værktøjet Azure AD Forbind på en server i sit Paris-datacenter.

Her er den server, der kører Azure AD Forbind, der forespørger Contoso AD DS-skoven om ændringer og derefter synkroniserer disse ændringer med Azure AD-lejeren.

![Contoso PHS-katalogsynkroniseringsinfrastrukturen.](../media/contoso-identity/contoso-identity-fig4.png)
 
## <a name="conditional-access-policies-for-zero-trust-identity-and-device-access"></a>Betingede access-politikker for nultillidsidentitet og enhedsadgang

Contoso oprettede et sæt politikker for Betinget adgang til Azure AD og [Intune for](../security/office-365-security/identity-access-policies.md) tre beskyttelsesniveauer:

- *Beskyttelse ved* udgangspunkt gælder for alle brugerkonti.
- *Virksomhedsbeskyttelse* gælder for seniorledelsen og ledelsen.
- *Specialiserede sikkerhedsbeskyttelsesprogrammer* gælder for bestemte brugere i finans-, juridiske- og forskningsafdelinger, der har adgang til stærkt regulerede data.

Her er det resulterende sæt af politikker for Contoso-identitet og betinget adgang til enhed.

:::image type="content" alt-text="Politikkerne for Contosos identitet og betingede adgang på enhed." source="../media/contoso-identity/contoso-identity-fig5.png" lightbox="../media/contoso-identity/contoso-identity-fig5.png":::
 
## <a name="next-step"></a>Næste trin

Få mere at vide om, hvordan Contoso bruger sin Microsoft Endpoint Configuration Manager til at [installere og holde Windows 10 Enterprise på](contoso-win10.md) tværs af organisationen.

## <a name="see-also"></a>Se også

[Installér identitet for Microsoft 365](deploy-identity-solution-overview.md)

[Microsoft 365 for Enterprise-oversigt](microsoft-365-overview.md)

[Test labvejledninger](m365-enterprise-test-lab-guides.md)