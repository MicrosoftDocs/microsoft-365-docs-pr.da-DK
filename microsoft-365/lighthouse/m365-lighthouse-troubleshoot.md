---
title: Foretag fejlfinding af fejlmeddelelser og problemer i Microsoft 365 Fyrtårn
f1.keywords: NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: troubleshooting
ms.prod: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- M365-Lighthouse
search.appverid: MET150
description: For MSP'er (Managed Service Providers) ved hjælp af Microsoft 365 Lighthouse kan du få hjælp til fejlfinding af fejlmeddelelser og problemer.
ms.openlocfilehash: 3ee2190732fdd7c9022edaa172bd45909807225c
ms.sourcegitcommit: 7e0094ddff54bcbe5d691dba58d4c4fb86f8b1a9
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/04/2022
ms.locfileid: "65188872"
---
# <a name="troubleshoot-error-messages-and-problems-in-microsoft-365-lighthouse"></a>Foretag fejlfinding af fejlmeddelelser og problemer i Microsoft 365 Fyrtårn

I denne artikel beskrives fejlmeddelelser og problemer, der kan opstå, når du bruger Microsoft 365 Lighthouse, og den indeholder fejlfindingstrin, du kan udføre for at løse dem.

## <a name="partner-onboarding"></a>Partner onboarding

### <a name="message-when-trying-to-access-lighthouse-microsoft-365-lighthouse-doesnt-support-indirect-providers-at-this-time-you-must-be-an-indirect-reseller-or-direct-bill-partner-to-use-this-service"></a>Meddelelse, når du forsøger at få adgang til Lighthouse: "Microsoft 365 Lighthouse understøtter ikke indirekte udbydere på nuværende tidspunkt, skal du være en indirekte forhandler eller direkte fakturapartner for at bruge denne tjeneste"

**Forårsage:** Du forsøgte at få adgang til Lighthouse som en indirekte fakturapartner. Lighthouse understøtter i øjeblikket kun indirekte forhandlere og partnere med direkte fakturering.

**Opløsning:** Du kan se en komplet liste over kvalifikationer og krav under [Krav til Microsoft 365 Lighthouse](m365-lighthouse-requirements.md). Hvis du ikke er indirekte udbyder og mener, at du har modtaget denne meddelelse ved en fejl, skal du kontakte Support. Du kan finde flere oplysninger under [Få hjælp og support til Microsoft 365 Lighthouse](m365-lighthouse-get-help-and-support.md).

### <a name="message-when-trying-to-access-lighthouse-you-must-be-an-indirect-reseller-or-direct-bill-partner-to-use-this-service"></a>Meddelelse, når du forsøger at få adgang til Lighthouse: "Du skal være indirekte forhandler eller direct-bill-partner for at bruge denne tjeneste"

**Forårsage:** Du forsøgte at få adgang til Lighthouse og er ikke Microsoft-partner. Du skal være tilmeldt programmet Cloud Solution Provider (CSP) som indirekte forhandler eller direct-bill-partner for at bruge Lighthouse.

**Opløsning:** Du kan se en komplet liste over kvalifikationer og krav under [Krav til Microsoft 365 Lighthouse](m365-lighthouse-requirements.md). Hvis du kvalificerer dig til at få adgang til Lighthouse og mener, at du har modtaget denne meddelelse ved en fejl, skal du kontakte Support. Du kan finde flere oplysninger under [Få hjælp og support til Microsoft 365 Lighthouse](m365-lighthouse-get-help-and-support.md).

### <a name="message-when-signing-in-to-lighthouse-accept-the-partner-amendment"></a>Meddelelse, når du logger på Lighthouse: "Acceptér partnerændringen"

**Forårsage:** Du forsøgte at få adgang til Lighthouse, før en global administrator i partnerlejer har signeret partnerændringen.

**Opløsning:** En global administrator skal logge på Lighthouse og acceptere partnerændringen, før du kan få adgang til og arbejde i Lighthouse. Hvis fejlen fortsætter, når en global administrator har signeret ændringen, skal du kontakte Support. Du kan finde flere oplysninger under [Få hjælp og support til Microsoft 365 Lighthouse](m365-lighthouse-get-help-and-support.md).

## <a name="customer-tenant-onboarding"></a>Onboarding af kundelejer  

### <a name="customer-tenants-show-a-status-other-than-active-in-the-tenant-list"></a>Kundelejere viser en anden status end "Aktiv" på lejerlisten  

**Forårsage:** Dine kundelejere opfylder ikke følgende kriterier:

- Der skal være konfigureret uddelegeret adgang for MSP'en (Managed Service Provider) for at kunne administrere kundelejer*
- Der skal være mindst én Microsoft 365 Business Premium, Microsoft 365 E3, Windows 365 Business eller Microsoft Defender til virksomheder licens
- Der må ikke være mere end 1000 licenserede brugere 

**Opløsning:** I følgende tabel beskrives de forskellige lejerstatusser, der kræver handling, og det forklares, hvordan du løser dem.

*Der kræves delegerede administratorrettigheder (DAP) for at onboarde kunder til Lighthouse. Vi anbefaler også, at du opretter GDAP (Granular Delegated Admin Privileges) sammen med dine kunder for at muliggøre mere sikker delegeret adgang. Mens DAP og GDAP eksisterer, har GDAP forrang for kunder, hvor begge modeller er på plads. Snart vil kunder med kun GDAP (og ingen DAP) kunne onboarde til Lighthouse.

| Status | Beskrivelse | Opløsning |
|--|--|--|
| Inaktive | Lejeren blev offboardet på anmodning af MSP'en og administreres ikke længere i Lighthouse. | Du skal genaktivere lejeren. På siden **Lejere** skal du vælge de tre prikker (flere handlinger) ud for den lejer, du vil genaktivere, og derefter vælge **Aktivér lejer**. Det kan tage 24-48 timer, før de første kundedata vises i Lighthouse. |
| Ikke berettiget – DAP eller GDAP er ikke konfigureret | Du har ikke rettigheder som DAP- eller GDAP-administrator konfigureret med lejeren, hvilket er påkrævet af Lighthouse. | Konfigurer DAP- eller GDAP-administratorrettigheder i Microsoft Partnercenter. |
| Ikke berettiget – Påkrævet licens mangler | Lejeren mangler en påkrævet licens. De skal bruge mindst én Microsoft 365 Business Premium, Microsoft 365 E3 eller Microsoft Defender til virksomheder licens. | Sørg for, at lejeren har tildelt mindst én Microsoft 365 Business Premium, Microsoft 365 E3, Windows 365 Business eller Microsoft Defender til virksomheder licens. |
| Ikke kvalificeret - Antallet af brugere er overskredet | Lejeren har mere end maksimalt 1000 licenserede brugere tilladt af Lighthouse. | Kontrollér, at lejeren ikke har mere end 1000 licenserede brugere. |
| Ikke berettiget - Geo-kontrol mislykkedes | Du og din kunde bor ikke i det samme geografiske område, hvilket er påkrævet af Lighthouse. | Kontrollér, at kunden er placeret i dit geografiske område. Hvis ikke, kan du ikke administrere lejeren i Lighthouse. |
| I gang | Lighthouse opdagede lejeren, men er stadig i gang med at onboarde dem. | Tillad, at Lighthouse 48 timer fuldfører onboarding af lejeren. |

Hvis du har bekræftet, at din kundelejer opfylder onboardingkriterierne, og de stadig ikke vises som **Aktive** i Lighthouse, skal du kontakte Support. Du kan finde flere oplysninger under [Få hjælp og support til Microsoft 365 Lighthouse](m365-lighthouse-get-help-and-support.md).

## <a name="access-and-permissions"></a>Adgang og tilladelser

### <a name="message-when-trying-to-access-lighthouse-not-authorized-or-insufficient-privileges-or-access-restriction-insufficient-or-lack-of-permissions-is-causing-access-restriction"></a>Meddelelse, når der gøres forsøg på at få adgang til Lighthouse: "Not Authorized" or "Insufficient privileges" eller "Access Restriction: Insufficient or lack of permissions is causing access restriction" 

**Forårsage:** Du tilhører ikke den korrekte sikkerhedsgruppe i Azure AD, eller du har ikke fået tildelt den korrekte rolle i Partnercenter for at få adgang til Lighthouse.

**Opløsning:** Sørg for, at en administrator fra din partnerlejer med de relevante tilladelser har tildelt dig til den korrekte GDAP-sikkerhedsgruppe i Azure AD og tildelt dig den korrekte rolle i Partnercenter. Husk også på, at nogle handlinger i Lighthouse kræver, at du er global administrator. Du kan få mere at vide om GDAP-rollerne, og hvad hver rolle kan gøre, [under Oversigt over tilladelser i Microsoft 365 Lighthouse](m365-lighthouse-overview-of-permissions.md). Du kan finde en detaljeret beskrivelse af alle Azure AD indbyggede roller og tilladelser til GDAP [i Azure AD indbyggede roller](/azure/active-directory/roles/permissions-reference).

For kunder med DAP-relationer skal partneradministratoren tildele dig rollen Administrator eller Helpdesk-agent i Partnercenter. Du kan finde en detaljeret beskrivelse af alle Partnercenter-roller og -tilladelser under [Tildel roller og tilladelser til brugere](/partner-center/permissions-overview).

### <a name="i-dont-see-complete-data-in-certain-areas-of-lighthouse-or-i-cant-perform-certain-tasks-or-i-cant-access-certain-tenants"></a>Jeg kan ikke se komplette data i visse områder af Lighthouse, eller jeg kan ikke udføre visse opgaver, eller jeg kan ikke få adgang til visse lejere

**Forårsage:** Du har begrænset GDAP-adgang baseret på de roller, der er tildelt den Azure AD sikkerhedsgruppe, du er i.

**Opløsning:** Sørg for, at en administrator fra din partnerlejer med de relevante tilladelser har tildelt dig til den korrekte GDAP-sikkerhedsgruppe i Azure AD. Husk også på, at nogle handlinger i Lighthouse kræver, at du er global administrator. Du kan få mere at vide om GDAP-rollerne, og hvad hver rolle kan gøre, [under Oversigt over tilladelser i Microsoft 365 Lighthouse](m365-lighthouse-overview-of-permissions.md). Du kan finde en detaljeret beskrivelse af alle Azure AD indbyggede roller og tilladelser til GDAP [i Azure AD indbyggede roller](/azure/active-directory/roles/permissions-reference).

## <a name="customer-tenant-management"></a>Administration af kundelejer  

### <a name="customer-tenant-has-no-data-showing-in-lighthouse"></a>Kundelejer har ingen data, der vises i Lighthouse

**Forårsage:** Du forsøger at få vist data i Lighthouse, før onboarding af lejeren er fuldført.

**Opløsning:** Det kan tage 24-48 timer, før de første kundedata vises i Lighthouse. Hvis der er gået mere end 48 timer, siden du onboardede lejeren, og du stadig ikke kan få vist eller indlæse lejerdata, eller hvis du ikke kan få vist eller indlæse data, som du tidligere har været i stand til, skal du kontakte Support. Du kan finde flere oplysninger under [Få hjælp og support til Microsoft 365 Lighthouse](m365-lighthouse-get-help-and-support.md). Vær forberedt på at levere relevante netværkslogge og en liste over eventuelle indstillinger, der kan være blevet ændret.

### <a name="customer-tenant-data-isnt-updating-after-making-changes-in-the-customer-tenant"></a>Kundelejerdata opdateres ikke, når der er foretaget ændringer i kundelejer

**Forårsage:** Det kan tage op til fire timer, før ændringer, du foretager i kundelejer, synkroniseres med kundelejerdataene i Lighthouse.

**Opløsning:** Hvis der er gået mere end fire timer, og kundelejerdataene stadig ikke opdateres i Lighthouse, skal du kontakte Support. Du kan finde flere oplysninger under [Få hjælp og support til Microsoft 365 Lighthouse](m365-lighthouse-get-help-and-support.md). Vær forberedt på at angive kundelejeroplysninger.

### <a name="message-when-applying-a-baseline-to-a-customer-tenant-process-error-occurred"></a>Meddelelse, når der anvendes en oprindelig plan på en kundelejer: "Der opstod en procesfejl"  

**Forårsage:** Du fuldførte ikke konfigurationen af Microsoft Intune i kundelejer.

**Opløsning:** Kontrollér, at du har fuldført de grundlæggende konfigurationstrin for Intune i kundelejer. Hvis problemet fortsætter, efter at du har kontrolleret, at Intune konfiguration er fuldført for kundelejer, skal du kontakte Support. Du kan finde flere oplysninger under [Få hjælp og support til Microsoft 365 Lighthouse](m365-lighthouse-get-help-and-support.md).

### <a name="cant-access-partner-tenant-data-in-lighthouse"></a>Der er ikke adgang til partnerlejerdata i Lighthouse

**Årsag**: Lighthouse understøtter kun visning og administration af *kundelejere* . Det understøtter i øjeblikket ikke visning og administration af *partnerlejere* .

**Opløsning:** Fortsæt med at bruge den metode, du har brugt til at få vist og administrere din partnerlejer.

## <a name="device-and-threat-management"></a>Administration af enheder og trusler 

### <a name="i-dont-see-any-customer-tenant-data-on-the-device-compliance-and-threat-management-pages-of-lighthouse"></a>Jeg kan ikke se nogen kundelejerdata på siderne for enhedsoverholdelse og trusselsstyring i Lighthouse

**Årsag 1:** Kundelejer har ikke fuldført onboarding til Intune. Kundelejerdata vil ikke være tilgængelige på siderne om enhedsoverholdelse eller trusselsstyring i Lighthouse, før kundelejer har fuldført onboarding til Intune.

**Opløsning:** Bekræft, at den kundelejer, du forsøger at få vist data for, er blevet onboardet til Intune. Når onboarding er fuldført i Intune, kan enhedsdata vises i Lighthouse i 4 timer.

**Årsag 2:** Kundelejeren blev for nylig onboardet til Lighthouse, og data indlæses stadig i Lighthouse.

**Opløsning:** Når en kundelejer er onboardet til Lighthouse, kan de første kundedata vises i 24-48 timer.

**Årsag 3:** Kundens lejerenhed er ny, og enhedsdataene indlæses stadig i Lighthouse.

**Opløsning:** Når der tilføjes en lejerenhed, kan enhedsdataene vises i Lighthouse i 4 timer.

Hvis data stadig ikke vises på siderne for enhedsoverholdelse og trusselsstyring efter at have fulgt løsningsvejledningen, skal du kontakte Support. Du kan finde flere oplysninger under [Få hjælp og support til Microsoft 365 Lighthouse](m365-lighthouse-get-help-and-support.md).

## <a name="related-content"></a>Relateret indhold

[Kendte problemer med Microsoft 365 Lighthouse](m365-lighthouse-known-issues.md) (artikel)\
[Microsoft 365 Ofte stillede spørgsmål om Fyrtårn](m365-lighthouse-faq.yml) (artikel)\
[Få hjælp og support til Microsoft 365 Lighthouse](m365-lighthouse-get-help-and-support.md) (artikel)
