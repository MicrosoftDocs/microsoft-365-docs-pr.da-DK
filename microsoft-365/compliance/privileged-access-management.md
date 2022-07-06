---
title: Få mere at vide om Privileged Access Management
description: Denne artikel indeholder en oversigt over administration af privilegeret adgang i Microsoft Purview, herunder svar på ofte stillede spørgsmål.
keywords: Microsoft 365, Microsoft Purview, overholdelse af angivne standarder, privilegeret adgangsstyring
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
ms.openlocfilehash: 6bf13adb96ae5d4d4030ebe44f10dab22602196e
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66622541"
---
# <a name="learn-about-privileged-access-management"></a>Få mere at vide om Privileged Access Management

Privilegeret adgangsstyring i Microsoft Purview giver detaljeret adgangskontrol over privilegerede administratoropgaver i Office 365. Det kan hjælpe med at beskytte din organisation mod brud, der bruger eksisterende privilegerede administratorkonti med stående adgang til følsomme data eller adgang til vigtige konfigurationsindstillinger. Administration af privilegeret adgang kræver, at brugerne anmoder om just-in-time-adgang til at udføre udvidede og privilegerede opgaver via en arbejdsproces med meget begrænset og tidsgrænset godkendelse. Denne konfiguration giver brugerne lige adgang nok til at udføre opgaven ved hånden uden at risikere eksponering af følsomme data eller kritiske konfigurationsindstillinger. Aktivering af privilegeret adgangsstyring gør det muligt for din organisation at arbejde med nul stående rettigheder og levere et forsvarslag mod sårbarheder i forhold til stående administrativ adgang.

Du kan få et hurtigt overblik over den integrerede arbejdsproces Customer Lockbox og privilegeret adgangsstyring i denne [video om kundelåskasse og privilegeret adgangsstyring](https://go.microsoft.com/fwlink/?linkid=2066800).

## <a name="layers-of-protection"></a>Beskyttelseslag

Privilegeret adgangsstyring supplerer andre beskyttelser af data og adgangsfunktioner i Microsoft 365-sikkerhedsarkitekturen. Hvis du inkluderer privilegeret adgangsstyring som en del af en integreret og lagdelt tilgang til sikkerhed, får du en sikkerhedsmodel, der maksimerer beskyttelsen af følsomme oplysninger og Konfigurationsindstillinger for Microsoft 365. Som vist i diagrammet bygger privilegeret adgangsstyring på den beskyttelse, der leveres med oprindelig kryptering af Microsoft 365-data og den rollebaserede sikkerhedsmodel for adgangskontrol i Microsoft 365-tjenester. Når disse to funktioner bruges sammen med [Azure AD Privileged Identity Management](/azure/active-directory/active-directory-privileged-identity-management-configure), giver de adgangskontrol med just-in-time-adgang i forskellige områder.

![Lagdelt beskyttelse i Microsoft 365.](../media/pam-layered-protection.png)

Privilegeret adgangsstyring er defineret og begrænset på **opgaveniveau**, mens Azure AD Privileged Identity Management anvender beskyttelse på **rolleniveau** med mulighed for at udføre flere opgaver. Azure AD Privileged Identity Management tillader primært administration af adgange for AD-roller og rollegrupper, mens Privilegeret adgangsstyring i Microsoft Purview kun gælder på opgaveniveau.

- **Aktivering af privilegeret adgangsstyring, mens der allerede bruges Azure AD Privileged Identity Management:** Hvis du tilføjer privilegeret adgangsstyring, får du endnu et detaljeret lag af beskyttelse og overvågningsfunktioner, så du kan få privilegeret adgang til Microsoft 365-data.

- **Aktivering af Azure AD Privileged Identity Management, mens der allerede bruges privilegeret adgangsstyring i Microsoft Purview:** Tilføjelse af Azure AD Privileged Identity Management  til Privilegeret adgangsstyring i Microsoft Purview kan udvide privilegeret adgang til data uden for Microsoft 365, der primært er defineret af brugerroller eller identitet.  

## <a name="privileged-access-management-architecture-and-process-flow"></a>Arkitektur og procesflow til privilegeret adgangsstyring

Hvert af følgende procesflow beskriver arkitekturen af privilegeret adgang, og hvordan den interagerer med Microsoft 365-underlaget, overvågning og Exchange Management-runspace.

### <a name="step-1-configure-a-privileged-access-policy"></a>Trin 1: Konfigurer en politik for privilegeret adgang

Når du konfigurerer en politik for privilegeret adgang med [Microsoft 365 Administration](https://admin.microsoft.com) eller PowerShell til Exchange-administration, definerer du politikken og processerne for privilegeret adgangsfunktion og politikattributterne i Microsoft 365-underlaget. Aktiviteterne logføres i Security &amp; Compliance Center. Politikken er nu aktiveret og klar til at håndtere indgående anmodninger om godkendelser.

![Trin 1: Oprettelse af politik.](../media/pam-step1-policy-creation.jpg)

### <a name="step-2-access-request"></a>Trin 2: Anmodning om adgang

I [Microsoft 365 Administration](https://admin.microsoft.com) eller med PowerShell til Exchange-administration kan brugerne anmode om adgang til udvidede eller privilegerede opgaver. Funktionen med privilegeret adgang sender anmodningen til Microsoft 365-underlaget til behandling i forhold til den konfigurerede politik for adgang til rettigheder og registrerer aktiviteten i loggene for Security &amp; Compliance Center.

![Trin 2: Anmodning om adgang.](../media/pam-step2-access-request.jpg)

### <a name="step-3-access-approval"></a>Trin 3: Adgangsgodkendelse

Der genereres en godkendelsesanmodning, og meddelelsen om ventende anmodning sendes til godkendere via mail. Hvis den godkendes, behandles anmodningen om privilegeret adgang som en godkendelse, og opgaven er klar til at blive fuldført. Hvis den afvises, blokeres opgaven, og anmoderen får ikke adgang. Anmoderen får besked om anmodningens godkendelse eller afvisning via mail.

![Trin 3: Adgangsgodkendelse.](../media/pam-step3-access-approval.jpg)

### <a name="step-4-access-processing"></a>Trin 4: Adgangsbehandling

For en godkendt anmodning behandles opgaven af Exchange Management-runspace. Godkendelsen kontrolleres i forhold til politikken for privilegeret adgang og behandles af Microsoft 365-underlaget. Al aktivitet for opgaven logføres i Security &amp; Compliance Center.

![Trin 4: Adgangsbehandling.](../media/pam-step4-access-processing.jpg)

## <a name="frequently-asked-questions"></a>Ofte stillede spørgsmål

### <a name="what-skus-can-use-privileged-access-in-office-365"></a>Hvilke SKU'er kan bruge privilegeret adgang i Office 365?

Privilegeret adgangsstyring er tilgængelig for kunder for et bredt udvalg af Microsoft 365- og Office 365-abonnementer og -tilføjelsesprogrammer. Se [Kom i gang med privilegeret adgangsstyring](privileged-access-management-configuration.md) for at få flere oplysninger.

### <a name="when-will-privileged-access-support-office-365-workloads-beyond-exchange"></a>Hvornår understøttes privilegeret adgang Office 365 arbejdsbelastninger ud over Exchange?

Privilegeret adgangsstyring vil snart være tilgængelig i andre Office 365 arbejdsbelastninger. Besøg [Microsoft 365 Roadmap](https://www.microsoft.com/microsoft-365/roadmap) for at få flere oplysninger.

### <a name="my-organization-needs-more-than-30-privileged-access-policies-will-this-limit-be-increased"></a>Min organisation har brug for mere end 30 privilegerede adgangspolitikker. Øges denne grænse?

Ja, en forhøjelse af den aktuelle grænse på 30 privilegerede adgangspolitikker pr. organisation er på funktionsoversigten.

### <a name="do-i-need-to-be-a-global-admin-to-manage-privileged-access-in-office-365"></a>Skal jeg være global Administration for at administrere privilegeret adgang i Office 365?

Nej, du skal have rollen Exchange-rolleadministration tildelt konti, der administrerer privilegeret adgang i Office 365. Hvis du ikke vil konfigurere rollen rolleadministration som en separat kontotilladelse, indeholder rollen Global administrator som standard denne rolle og kan administrere privilegeret adgang. Brugere, der er inkluderet i en godkenders gruppe, behøver ikke at være en global Administration eller have rollen Rolleadministration tildelt til at gennemse og godkende anmodninger med PowerShell.

### <a name="how-is-privileged-access-management-related-to-customer-lockbox"></a>Hvordan er privilegeret adgangsstyring relateret til Customer Lockbox?

[Customer Lockbox](/office365/admin/manage/customer-lockbox-requests) tillader et adgangskontrolniveau for organisationer, når Microsoft tilgår data. Privilegeret adgangsstyring giver detaljeret adgangskontrol i en organisation for alle privilegerede Microsoft 365-opgaver.

## <a name="ready-to-get-started"></a>Er du klar til at komme i gang?

Begynd [at konfigurere din organisation til privilegeret adgangsstyring](privileged-access-management-configuration.md).

## <a name="learn-more"></a>Lær mere

[Interaktiv vejledning: Overvåg og styr administratoropgaver med privilegeret adgangsstyring](https://content.cloudguides.com/guides/Privileged%20Access%20Management)
