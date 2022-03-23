---
title: Oversigt over lejere til Microsoft 365
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- m365initiative-coredeploy
ms.custom: it-pro
description: Roadmap til at konfigurere dine lejere til Microsoft 365.
ms.openlocfilehash: 180f7f998819986d05febe6ae19877da290d20a5
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/04/2022
ms.locfileid: "63591396"
---
# <a name="tenant-roadmap-for-microsoft-365"></a>Oversigt over lejere til Microsoft 365

Din Microsoft 365 lejer er det sæt af tjenester, der er tildelt din organisation. Typisk er denne lejer knyttet til et eller flere af dine offentlige DNS-domænenavne og fungerer som en central og isoleret beholder for forskellige abonnementer og licenser i dem, som du tildeler til brugerkonti. Få mere at vide [under Abonnementer, licenser, konti og lejere for Microsofts skybaserede tilbud](subscriptions-licenses-accounts-and-tenants-for-microsoft-cloud-offerings.md).

Når du opretter en Microsoft 365 lejer, tildeler du den til en bestemt geografisk placering. Du kan også have en lejer med flere geografiske placeringer og flytte din lejer fra én placering til en anden.

For at gøre din lejer klar til brugere, grupper, licenser og skyapps er det vigtigt omhyggeligt at planlægge og udføre din lejerkonfiguration.

## <a name="set-up-your-microsoft-365-tenant"></a>Konfigurer din Microsoft 365 lejer

Når du har sikret dig, at dit netværk er optimeret til adgang til Microsoft 365 for både lokale medarbejdere og eksterne medarbejdere, er de næste store opgaver at planlægge og derefter konfigurere din Microsoft 365-lejer for DNS-domænenavne, almindelige tjenester og for den pågældende identitetsinfrastruktur, der understøtter sikker brugeradgang.

### <a name="plan"></a>Plan

Sådan planlægger du implementering af din lejer:

- [Forstå abonnementer, licenser og Azure Active Directory (Azure AD)-lejere](subscriptions-licenses-accounts-and-tenants-for-microsoft-cloud-offerings.md)
- [Forstå, hvordan du bruger tredjeparts SSL-certifikater](plan-for-third-party-ssl-certificates.md)
- [Forstå de måder, hvorpå Microsoft 365 lejer er integreret med Azure AD-tjenester](integrated-apps-and-azure-ads.md)
- [Plan for understøttelse af klientapp](microsoft-365-client-support-certificate-based-authentication.md)
- [Find ud af, hvordan du bruger hybrid moderne godkendelse](hybrid-modern-auth-overview.md)
- [Planlæg Office 2007- Office 2010-opgraderinger](plan-upgrade-previous-versions-office.md)
- [Forstå lejerisolation](/compliance/assurance/microsoft-365-isolation-controls)

### <a name="deploy"></a>Installér

Sådan installerer du din lejer: 

- Tilføj [DNS-domænerne](../admin/setup/add-domain.md) for din organisation.
- Brug [installationshjælpelinjerne i Microsoft 365 Administration](setup-guides-for-microsoft-365.md).
- Udbyg din [identitetsinfrastruktur](deploy-identity-solution-overview.md).

### <a name="move-a-tenants-geographic-locations"></a>Flyt en lejers geografiske placeringer

Microsoft fortsætter med at åbne nye datacenter geografiske placeringer (geos) for Microsoft 365 tjenester. Disse nye datacentre tilføjer kapacitet og beregner ressourcer for at understøtte kundebehov og vækst i brugen. Desuden tilbyder det nye datacenter geos in-geo-dataopbevaring for kernekundedata.

Få mere at vide under [Flytning af kernedata til Microsoft 365 datacenter geos](moving-data-to-new-datacenter-geos.md).


## <a name="deploy-microsoft-365-multi-geo"></a>Installér Microsoft 365 Multi-Geo

Med Microsoft 365 Multi-Geo kan din organisation udvide sin tilstedeværelse Microsoft 365 til flere geografiske områder og/eller lande i din eksisterende lejer.

Du kan finde flere oplysninger [Microsoft 365 Multi-Geo](microsoft-365-multi-geo.md).

## <a name="manage-multiple-microsoft-365-tenants"></a>Administrere flere Microsoft 365 lejere 

Selvom det er ideelt at have en enkelt lejer til din tilpasning, kan du være en af mange organisationer, der har flere lejere. Mulige årsager kan være fusioner og overtagelser, du ønsker administrativ isolation, eller du har en decentraliseret it.

Hvis du har flere Microsoft 365 lejere, kan du læse disse artikler for at få flere oplysninger om:

- [Samarbejde mellem lejere](microsoft-365-inter-tenant-collaboration.md)
- [Overførsel af postkasse på tværs af lejere](cross-tenant-mailbox-migration.md)
- [Lejer-til-lejer-migrering](microsoft-365-tenant-to-tenant-migrations.md)

## <a name="next-step"></a>Næste trin

Start din lejerplanlægning [med Abonnementer, licenser, konti og lejere](subscriptions-licenses-accounts-and-tenants-for-microsoft-cloud-offerings.md).