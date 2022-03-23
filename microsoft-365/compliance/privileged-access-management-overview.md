---
title: Få mere at vide om administration af adgang med rettigheder
description: Denne artikel indeholder en oversigt over administration af adgangspriviviligementer i Microsoft 365 herunder svar på ofte stillede spørgsmål.
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: overview
f1.keywords:
- NOCSH
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- m365-security-compliance
- m365solution-insiderrisk
- m365initiative-compliance
ms.custom:
- Ent_Solutions
- seo-marvel-apr2020
ms.openlocfilehash: 4fb4b548d71cf3e1da11e3c861a16929ac7073d8
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63587925"
---
# <a name="learn-about-privileged-access-management"></a>Få mere at vide om administration af adgang med rettigheder

Med administration af adgang med rettigheder kan du opnå detaljeret adgangskontrol over administratoropgaver med Office 365. Det kan hjælpe med at beskytte din organisation mod brud på brugen af eksisterende privilegerede administratorkonti med stående adgang til følsomme data eller adgang til vigtige konfigurationsindstillinger. Administration af adgang med rettigheder kræver, at brugerne anmoder om rettidig adgang til at udføre administratorbaserede og privilegerede opgaver gennem en meget begrænset og tidsbundet godkendelsesarbejdsproces. Denne konfiguration giver brugerne lige så god adgang til at udføre den aktuelle opgave uden at risikere eksponering af følsomme data eller kritiske konfigurationsindstillinger. Aktivering af adgangsstyring med rettigheder i Microsoft 365 giver din organisation mulighed for at fungere med nulstående rettigheder og giver et lag af forsvar mod stående administrative adgangsrisici.

Du kan få en hurtig oversigt over den integrerede kundelåskasse og arbejdsprocessen for adgangsstyring ved at se denne video [om kunde lockbox og administration af privilegeret adgang](https://go.microsoft.com/fwlink/?linkid=2066800).

## <a name="layers-of-protection"></a>Beskyttelseslag

Privileged access management complements other data and access feature protections within Microsoft 365 security architecture. Herunder adgangsstyring med rettigheder som en del af en integreret og lagdelt tilgang til sikkerhed giver en sikkerhedsmodel, der maksimerer beskyttelsen af følsomme oplysninger og Microsoft 365 indstillingerne for konfiguration. Som vist i diagrammet bygger adgangsstyring på grundlag af den beskyttelse, der leveres med oprindelig kryptering af Microsoft 365-data og den rollebaserede sikkerhedsmodel for adgangskontrol for Microsoft 365-tjenester. Når de bruges [sammen med Azure AD Privileged Identity Management](/azure/active-directory/active-directory-privileged-identity-management-configure), giver disse to funktioner adgangskontrol med just-in-time adgang på forskellige områder.

![Lagdelt beskyttelse i Microsoft 365.](../media/pam-layered-protection.png)

Adgangsstyring med rettigheder defineres og begrænses  på opgaveniveau, mens Azure AD Privileged Identity Management anvender beskyttelse på rolleniveau med  mulighed for at udføre flere opgaver. Azure AD Privileged Identity Management primært giver mulighed for at administrere adgang for AD-roller og rollegrupper, mens administration af adgang med rettigheder i Microsoft 365 kun gælder på opgaveniveau.

- Aktivering af adgangsstyring med privilegeret adgang, mens du allerede bruger **Azure AD Privileged Identity Management:** Hvis du tilføjer adgangsstyring med rettigheder, får du endnu et detaljeret lag af beskyttelses- og overvågningsegenskaber med adgangspriviligitet til Microsoft 365 data.

- **Aktivering af Azure AD Privileged Identity Management**, mens du allerede bruger styring af adgang med rettigheder i Office 365: Når du føjer Azure AD Privileged Identity Management til administration af adgang med rettigheder, kan du udvide den privilegerede adgang til data uden for Microsoft 365  der primært er defineret af brugerroller eller identitet.  

## <a name="privileged-access-management-architecture-and-process-flow"></a>Arkitektur og procesflow med adgangsstyring med rettigheder

Hver af følgende proces flyder opridser arkitekturen for privilegeret adgang, og hvordan den interagerer med Microsoft 365-understrat, overvågning og Exchange Management-runspace.

### <a name="step-1-configure-a-privileged-access-policy"></a>Trin 1: Konfigurere en politik for adgang med rettigheder

Når du konfigurerer en politik for privilegeret adgang med [Microsoft 365 Administration](https://admin.microsoft.com) eller Exchange Management PowerShell, definerer du politikken og processer for adgang med privilegeret adgang samt politikattributterne i Microsoft 365-undergruppen. Aktiviteterne logføres i Security &amp; Compliance Center. Politikken er nu aktiveret og klar til at håndtere indgående anmodninger om godkendelser.

![Trin 1: Oprettelse af politikker.](../media/pam-step1-policy-creation.jpg)

### <a name="step-2-access-request"></a>Trin 2: Anmodning om adgang

I programmet [Microsoft 365 Administration](https://admin.microsoft.com) med Exchange Management PowerShell kan brugere anmode om adgang til opgaver med administratoradgang eller særlige rettigheder. Den privilegerede adgangsfunktion sender anmodningen til Microsoft 365-undernøglen til behandling i forhold til den konfigurerede adgangspolitik for rettigheder og registrerer Aktivitet i logfilerne for Security &amp; Compliance Center.

![Trin 2: Anmodning om adgang.](../media/pam-step2-access-request.jpg)

### <a name="step-3-access-approval"></a>Trin 3: Adgangsgodkendelse

Der genereres en anmodning om godkendelse, og den ventende anmodning sendes via mail til godkendere. Hvis den godkendes, behandles anmodningen om privilegeret adgang som en godkendelse, og opgaven er klar til at blive fuldført. Hvis det afvises, blokeres opgaven, og anmoderen får ikke adgang. Anmoderen underrettes om anmodningens godkendelse eller afvisning via mail.

![Trin 3: Få adgang til godkendelse.](../media/pam-step3-access-approval.jpg)

### <a name="step-4-access-processing"></a>Trin 4: Behandling af adgang

For en godkendt anmodning behandles opgaven af Exchange Management-runspace. Godkendelsen kontrolleres i forhold til politikken for privilegeret adgang og behandles af Microsoft 365 understrat. Alle aktiviteter for opgaven logføres i Security &amp; Compliance Center.

![Trin 4: Tilgå behandling.](../media/pam-step4-access-processing.jpg)

## <a name="frequently-asked-questions"></a>Ofte stillede spørgsmål

### <a name="what-skus-can-use-privileged-access-in-office-365"></a>Hvilke SKU'er kan benytte privilegeret adgang i Office 365?

Kunder kan få adgang til et bredt udvalg af Microsoft 365 og Office 365-abonnementer og -tilføjelser. Se [Introduktion til administration af adgangsrettigheder for at](privileged-access-management-configuration.md) få flere oplysninger.

### <a name="when-will-privileged-access-support-office-365-workloads-beyond-exchange"></a>Hvornår understøtter den privilegerede adgang Office 365 arbejdsbelastninger ud Exchange?

Privileged access management will be available in other Office 365 workloads soon. Besøg Oversigt [Microsoft 365 for at](https://www.microsoft.com/microsoft-365/roadmap) få mere at vide.

### <a name="my-organization-needs-more-than-30-privileged-access-policies-will-this-limit-be-increased"></a>Min organisation har brug for mere end 30 politikker for privilegeret adgang. Øges denne grænse?

Ja, at hæve den aktuelle grænse på 30 politikker for privilegeret adgang pr. organisation er på funktionsoversigten.

### <a name="do-i-need-to-be-a-global-admin-to-manage-privileged-access-in-office-365"></a>Skal jeg være global administrator for at administrere privilegeret adgang i Office 365?

Nej, du skal bruge den Exchange rollestyringsrolle, der er tildelt til konti, der administrerer privilegeret adgang Office 365. Hvis du ikke vil konfigurere rollestyringsrollen som en enkeltstående kontotilladelse, omfatter rollen Global administrator som standard denne rolle og kan administrere privilegeret adgang. Brugere, der er inkluderet i en godkenders gruppe, behøver ikke at være globale administratorer eller have rollestyringsrollen tildelt til at gennemse og godkende anmodninger med PowerShell.

### <a name="how-is-privileged-access-management-related-to-customer-lockbox"></a>Hvordan er adgangsstyring for privilegeret adgang relateret til kunde lockbox?

[Kunde lockbox giver](/office365/admin/manage/customer-lockbox-requests) mulighed for et adgangsniveau for organisationer, når Microsoft får adgang til data. Med adgangsstyring med rettigheder kan du i en organisation få detaljeret adgang til alle Microsoft 365 opgaver med rettigheder.

## <a name="ready-to-get-started"></a>Er du klar til at gå i gang?

Start [konfiguration af din organisation for at få adgangsstyring med rettigheder](privileged-access-management-configuration.md).

## <a name="learn-more"></a>Lær mere

[Interaktiv vejledning: Overvåge og kontrollere administratoropgaver med adgangsstyring](https://content.cloudguides.com/guides/Privileged%20Access%20Management)
