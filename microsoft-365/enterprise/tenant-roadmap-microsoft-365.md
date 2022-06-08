---
title: Oversigt over lejere til Microsoft 365
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: scotv
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- m365initiative-coredeploy
ms.custom: it-pro
description: Køreplanen for konfiguration af dine lejere til Microsoft 365.
ms.openlocfilehash: 5eed55d45e4b34962b08d236f8659cfd2cf209c1
ms.sourcegitcommit: 61bdfa84f2d6ce0b61ba5df39dcde58df6b3b59d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/08/2022
ms.locfileid: "65940398"
---
# <a name="tenant-roadmap-for-microsoft-365"></a>Oversigt over lejere til Microsoft 365

Din Microsoft 365-lejer er det sæt tjenester, der er tildelt din organisation. Denne lejer er typisk knyttet til et eller flere af dine offentlige DNS-domænenavne og fungerer som en central og isoleret objektbeholder for forskellige abonnementer og de licenser i dem, som du tildeler til brugerkonti. Du kan få flere oplysninger under [Abonnementer, licenser, konti og lejere til Microsofts cloudtilbud](subscriptions-licenses-accounts-and-tenants-for-microsoft-cloud-offerings.md).

Når du opretter en Microsoft 365-lejer, tildeler du den til en bestemt geografisk placering. Du kan også have en lejer med flere geografiske placeringer og flytte din lejer fra én placering til en anden.

Hvis du vil gøre din lejer klar til bruger, grupper, licenser og cloudapps, er det vigtigt at planlægge og udføre din lejerkonfiguration omhyggeligt.

## <a name="set-up-your-microsoft-365-tenant"></a>Konfigurer din Microsoft 365-lejer

Når du har sikret dig, at dit netværk er optimeret til at få adgang til Microsoft 365 for både medarbejdere i det lokale miljø og fjernarbejdere, planlægger og konfigurerer dine næste store opgaver din Microsoft 365-lejer til DNS-domænenavne, almindelige tjenester og for den identitetsinfrastruktur, der understøtter sikker brugerlogon.

### <a name="plan"></a>Plan

Sådan planlægger du implementering af din lejer:

- [Forstå abonnementer, licenser og Azure Ad-lejere (Azure Active Directory)](subscriptions-licenses-accounts-and-tenants-for-microsoft-cloud-offerings.md)
- [Forstå, hvordan du bruger SSL-certifikater fra tredjepart](plan-for-third-party-ssl-certificates.md)
- [Forstå, hvordan en Microsoft 365-lejer er integreret i Azure AD-tjenester](integrated-apps-and-azure-ads.md)
- [Planlæg support til klientapps](microsoft-365-client-support-certificate-based-authentication.md)
- [Bestem, hvordan du bruger hybrid moderne godkendelse](hybrid-modern-auth-overview.md)
- [Planlæg office 2007- og Office 2010-opgraderinger](plan-upgrade-previous-versions-office.md)
- [Forstå lejerisolation](/microsoft-365-isolation-in-microsoft-365?view=o365-worldwide&preserve-view=true)

### <a name="deploy"></a>Rul ud

Sådan udruller du din lejer: 

- Tilføj [DNS-domænerne](../admin/setup/add-domain.md) for din organisation.
- Brug [installationsvejledningerne i Microsoft 365 Administration](setup-guides-for-microsoft-365.md).
- Udbyg din [identitetsinfrastruktur](deploy-identity-solution-overview.md).

### <a name="move-a-tenants-geographic-locations"></a>Flyt en lejers geografiske placeringer

Microsoft fortsætter med at åbne nye geografiske datacenterplaceringer (geos) til Microsoft 365-tjenester. Disse nye datacenter-geos tilføjer kapacitet og beregningsressourcer for at understøtte kundeefterspørgsel og forbrugsvækst. Derudover tilbyder det nye datacenter geos in-geo-dataopbevaring for kernekundedata.

Du kan få flere oplysninger under [Flytning af kernedata til nye Geos for Microsoft 365-datacentre](moving-data-to-new-datacenter-geos.md).


## <a name="deploy-microsoft-365-multi-geo"></a>Udrul Microsoft 365 Multi-Geo

Med Microsoft 365 Multi-Geo kan din organisation udvide sin Microsoft 365-tilstedeværelse til flere geografiske områder og/eller lande i din eksisterende lejer.

Du kan få flere oplysninger i [Microsoft 365 Multi-Geo](microsoft-365-multi-geo.md).

## <a name="manage-multiple-microsoft-365-tenants"></a>Administrer flere Microsoft 365-lejere 

Selvom det er ideelt at have en enkelt lejer til din oganisering, kan du være en af mange organisationer, der har flere lejere. Årsagerne kan omfatte fusioner og opkøb, du vil have administrativ isolation, eller du har en decentraliseret it-virksomhed.

Hvis du har flere Microsoft 365-lejere, skal du se disse artikler for at få flere oplysninger om:

- [Samarbejde mellem lejere](microsoft-365-inter-tenant-collaboration.md)
- [Migrering af postkasse på tværs af lejere](cross-tenant-mailbox-migration.md)
- [Lejer til lejer-migreringer](microsoft-365-tenant-to-tenant-migrations.md)

## <a name="next-step"></a>Næste trin

Start din lejerplanlægning med [abonnementer, licenser, konti og lejere](subscriptions-licenses-accounts-and-tenants-for-microsoft-cloud-offerings.md).