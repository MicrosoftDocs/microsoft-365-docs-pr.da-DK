---
title: Fejlfind og løs problemer og fejlmeddelelser i Microsoft 365 Lighthouse
f1.keywords: NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: article
ms.prod: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- M365-Lighthouse
search.appverid: MET150
description: For administrerede tjenesteudbydere, der bruger Microsoft 365 Lighthouse, kan du få hjælp til fejlfinding og løsning af fejlmeddelelser og problemer.
ms.openlocfilehash: e39eea66222852d8f331aa6bc68b386bea3da763
ms.sourcegitcommit: a216617d6ff27fe7d3089a047fbeaac5d72fd25c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/16/2022
ms.locfileid: "63705435"
---
# <a name="troubleshoot-and-resolve-problems-and-error-messages-in-microsoft-365-lighthouse"></a>Fejlfind og løs problemer og fejlmeddelelser i Microsoft 365 Lighthouse

I denne artikel beskrives fejlmeddelelser og problemer, du kan støde på, når du bruger Microsoft 365 Lighthouse, og den indeholder fejlfindingstrin, du kan udføre for at løse dem.

## <a name="partner-onboarding"></a>Partner onboarding

### <a name="message-when-trying-to-access-lighthouse-microsoft-365-lighthouse-doesnt-support-indirect-providers-at-this-time-you-must-be-an-indirect-reseller-or-direct-bill-partner-to-use-this-service"></a>Meddelelse, når du forsøger at få adgang til Lighthouse: "Microsoft 365 Lighthouse understøtter ikke indirekte udbydere på nuværende tidspunkt, du skal være indirekte forhandler eller direkte fakturapartner for at bruge denne tjeneste"

**Årsag:** Du har forsøgt at få adgang til Lighthouse som indirekte fakturapartner. På nuværende tidspunkt understøtter Lighthouse kun indirekte forhandlere og direkte fakturerede partnere.

**Løsning:** Du kan finde en komplet liste over kvalifikationer og krav [under Krav til Microsoft 365 Lighthouse](m365-lighthouse-requirements.md). Hvis du ikke er en indirekte udbyder, og du mener, at du har modtaget denne meddelelse ved en fejl, skal du kontakte Support. Få mere at vide under [Få hjælp og support til Microsoft 365 Lighthouse](m365-lighthouse-get-help-and-support.md).

### <a name="message-when-trying-to-access-lighthouse-you-must-be-an-indirect-reseller-or-direct-bill-partner-to-use-this-service"></a>Meddelelse, når du forsøger at få adgang til Lighthouse: "Du skal være indirekte forhandler eller direkte fakturapartner for at bruge denne tjeneste"

**Årsag:** Du har forsøgt at få adgang til Lighthouse og er ikke Microsoft-partner. Du skal være tilmeldt programmet Cloud Solution Provider (CSP) som en indirekte forhandler eller direkte faktureret partner for at bruge Lighthouse.

**Løsning:** Du kan finde en komplet liste over kvalifikationer og krav [under Krav til Microsoft 365 Lighthouse](m365-lighthouse-requirements.md). Hvis du er kvalificeret til at få adgang til Lighthouse, og du mener, at du har modtaget denne meddelelse ved en fejl, skal du kontakte Support. Få mere at vide under [Få hjælp og support til Microsoft 365 Lighthouse](m365-lighthouse-get-help-and-support.md).

### <a name="message-when-signing-in-to-lighthouse-accept-the-partner-amendment"></a>Meddelelse, når du logger på Lighthouse: "Acceptér partnerændringen"

**Årsag:** Du har forsøgt at få adgang til Lighthouse, før en global administrator i partnerlejeren har underskrevet partnerændringen.

**Løsning:** En global administrator skal logge på Lighthouse og acceptere partnerændringen, før du kan få adgang til og arbejde i Fyrtårn. Hvis fejlen fortsætter, efter en global administrator har underskrevet ændringen, skal du kontakte Support. Få mere at vide under [Få hjælp og support til Microsoft 365 Lighthouse](m365-lighthouse-get-help-and-support.md).

## <a name="customer-tenant-onboarding"></a>Onboarding af kundelejer  

### <a name="customer-tenants-show-a-status-other-than-active-in-the-tenant-list"></a>Kundelejere viser en anden status end "Aktiv" på lejerlisten  

**Årsag:** Dine kundelejere opfylder ikke følgende kriterier:

  - Skal have delegerede (DAP) eller detaljerede delegerede administratorrettigheder (GDAP) konfigureret for den administrerede tjenesteudbyder (MSP)
  - Skal have mindst én Microsoft 365 Business Premium eller Microsoft 365 E3 licens
  - Ikke må have mere end 1000 brugere med licens 

**Løsning:** I følgende tabel beskrives de forskellige lejerstatusser, der kræver handling, og forklarer, hvordan du løser dem.<br><br>

| Status | Beskrivelse | Løsning |
|--|--|--|
| Inaktiv | Lejeren blev udlejet på anmodning af MSP'en og administreres ikke længere i Fyrtårn. | Du skal genaktivere lejeren. På siden **Lejere** skal du vælge de tre prik (flere handlinger) ud for den lejer, du vil genaktivere, og derefter vælge **Aktivér lejer**. Det kan tage 24-48 timer, før indledende kundedata vises i Lighthouse. |
| Ikke berettiget – DAP eller GDAP er ikke konfigureret | Du har ikke DAP- eller GDAP-administratorrettigheder konfigureret med lejeren, hvilket kræves af Lighthouse. | Konfigurer DAP- eller GDAP-administratorrettigheder i Microsoft Partnercenter. |
| Ikke berettiget – Påkrævet licens mangler | Lejeren mangler en påkrævet licens. De skal bruge mindst én Microsoft 365 Business Premium eller Microsoft 365 E3 licens. | Sørg for, at lejeren har tildelt mindst Microsoft 365 Business Premium en Microsoft 365 E3 licens. |
| Ikke berettiget – Antal brugere er overskredet | Lejeren har mere end de maksimalt 1000 brugere med licens, som Lighthouse tillader. | Bekræft, at lejeren ikke har mere end 1000 brugere med licens. |
| Ikke berettiget – Geo-kontrol mislykkedes | Du og din kunde bor ikke i det samme geografiske område, som kræves af Lighthouse. | Kontrollér, at kunden er placeret i dit geografiske område. Hvis ikke, kan du ikke administrere lejeren i Lighthouse. |
| I gang | Fyrtårn har fundet lejeren, men er stadig i gang med at onboarde dem. | Tillad, at Fyrtårn 48 timer gennemfører onboarding af lejeren. |

Hvis du har bekræftet, at din kundelejer opfylder onboardingkriterierne, og de stadig ikke vises som **Aktive** i Lighthouse, skal du kontakte Support. Få mere at vide under [Få hjælp og support til Microsoft 365 Lighthouse](m365-lighthouse-get-help-and-support.md).

## <a name="access-and-permissions"></a>Adgang og tilladelser

### <a name="message-when-trying-to-access-lighthouse-not-authorized-or-insufficient-privileges-or-access-restriction-insufficient-or-lack-of-permissions-is-causing-access-restriction"></a>Meddelelse, når du forsøger at få adgang til Lighthouse: "Ikke godkendt" eller "Utilstrækkelige rettigheder" eller "Adgangsbegrænsning: Utilstrækkelige eller manglende tilladelser forårsager adgangsbegrænsning" 

**Årsag:** Du hører ikke til den korrekte sikkerhedsgruppe i Azure AD, eller du har ikke fået tildelt den korrekte rolle i Partnercenter for at få adgang til Fyrtårn.

**Løsning:** Sørg for, at en administrator fra din partnerlejer med de relevante tilladelser har tildelt dig den korrekte GDAP-sikkerhedsgruppe i Azure AD og tildelt dig den korrekte rolle i Partnercenter. Husk også, at nogle handlinger i Lighthouse kræver, at du er global administrator. Hvis du vil vide mere om GDAP-rollerne, og hvad hver rolle kan gøre, [skal du se Konfigurer Microsoft 365 Lighthouse Portal Security](m365-lighthouse-configure-portal-security.md). Du kan finde en detaljeret beskrivelse af alle indbyggede roller og tilladelser for GDAP i de [indbyggede roller i Azure AD](/azure/active-directory/roles/permissions-reference).

For kunder med DAP-relationer skal partneradministratoren tildele dig rollen som administrator eller Helpdesk-agent i Partnercenter. Hvis du vil have en detaljeret beskrivelse af alle partnercenterroller og -tilladelser, skal [du se Tildel roller og tilladelser til brugere](/partner-center/permissions-overview).

### <a name="i-dont-see-complete-data-in-certain-areas-of-lighthouse-or-i-cant-perform-certain-tasks-or-i-cant-access-certain-tenants"></a>Jeg kan ikke se fuldstændige data i bestemte områder af Lighthouse, eller jeg kan ikke udføre bestemte opgaver, eller jeg kan ikke få adgang til bestemte lejere

**Årsag:** Du har begrænset GDAP-adgang baseret på de roller, der er tildelt den Azure AD-sikkerhedsgruppe, du er i.

**Løsning:** Sørg for, at en administrator fra din partnerlejer med de rette tilladelser har tildelt dig den korrekte GDAP-sikkerhedsgruppe i Azure AD. Husk også, at nogle handlinger i Lighthouse kræver, at du er global administrator. Hvis du vil vide mere om GDAP-rollerne, og hvad hver rolle kan gøre, [skal du se Konfigurer Microsoft 365 Lighthouse Portal Security](m365-lighthouse-configure-portal-security.md). Du kan finde en detaljeret beskrivelse af alle indbyggede roller og tilladelser for GDAP i de [indbyggede roller i Azure AD](/azure/active-directory/roles/permissions-reference).

## <a name="customer-tenant-management"></a>Administration af kundelejer  

### <a name="customer-tenant-has-no-data-showing-in-lighthouse"></a>Kundelejeren har ingen data vist i Fyrtårn

**Årsag:** Du forsøger at få vist data i Lighthouse, før lejerens onboarding er fuldført.

**Løsning:** Det kan tage 24-48 timer, før indledende kundedata vises i Lighthouse. Hvis der er gået mere end 48 timer, siden du onboardede lejeren, og du stadig ikke kan få vist eller indlæse lejerdata, eller du ikke kan få vist eller indlæse data, som du tidligere har haft mulighed for, skal du kontakte Support. Få mere at vide under [Få hjælp og support til Microsoft 365 Lighthouse](m365-lighthouse-get-help-and-support.md). Vær klar til at levere relevante netværkslogfiler og en liste over de indstillinger, der kan være blevet ændret.

### <a name="customer-tenant-data-isnt-updating-after-making-changes-in-the-customer-tenant"></a>Kundelejerdata opdateres ikke, efter der er foretaget ændringer i kundelejeren

**Årsag:** Der kan gå op til 4 timer, før ændringer, du foretager inden for kundelejeren, synkroniseres med kundelejerdataene i Lighthouse.

**Løsning:** Hvis der er gået mere end 4 timer, og kundelejerdataene stadig ikke opdateres i Lighthouse, skal du kontakte Support. Få mere at vide under [Få hjælp og support til Microsoft 365 Lighthouse](m365-lighthouse-get-help-and-support.md). Vær klar til at give kundelejeroplysninger.

### <a name="message-when-applying-a-baseline-to-a-customer-tenant-process-error-occurred"></a>Meddelelse, når du anvender en oprindelig plan på en kundelejer: "Der opstod en procesfejl"  

**Årsag:** Du har ikke fuldført konfigurationen af Microsoft Intune i kundelejeren.

**Løsning:** Kontrollér, at du har gennemført de grundlæggende konfigurationstrin for Intune inden for kundelejeren. Hvis problemet fortsætter, efter du har kontrolleret, at Intune-konfigurationen er fuldført for kundelejeren, skal du kontakte Support. Få mere at vide under [Få hjælp og support til Microsoft 365 Lighthouse](m365-lighthouse-get-help-and-support.md).

### <a name="cant-access-partner-tenant-data-in-lighthouse"></a>Kan ikke få adgang til partnerlejerdata i Fyrtårn

**Årsag**: Lighthouse understøtter kun visning og administration *af kundelejere* . Det understøtter i øjeblikket ikke visning og administration af *partnerlejere* .

**Løsning:** Fortsæt med at bruge den metode, du har brugt til at få vist og administrere din partnerlejer.

## <a name="device-and-threat-management"></a>Administration af enheder og trusler 

### <a name="i-dont-see-any-customer-tenant-data-on-the-device-compliance-and-threat-management-pages-of-lighthouse"></a>Jeg kan ikke se nogen kundelejerdata på siderne enhedsoverholdelse og trusselsadministration i Lighthouse

**Årsag 1:** Kundelejeren har ikke færdiggjort onboarding til Intune. Kundelejerdata vil ikke være tilgængelige på siderne enhedsoverholdelse eller trusselsadministration i Lighthouse, før kundelejeren har færdiggjort onboarding til Intune.

**Løsning:** Kontrollér, at den kundelejer, du forsøger at få vist data for, har færdiggjort onboarding til Intune. Når onboarding er fuldført i Intune, skal der gå 4 timer, før enhedens data vises i Fyrtårn.

**Årsag 2:** Kundelejeren blev for nylig onboardet til Lighthouse, og data indlæses stadig i Lighthouse.

**Løsning:** Når en kundelejer er onboardet til Lighthouse, skal der gå 24-48 timer, før de indledende kundedata vises.

**Årsag 3:** Kundens lejerenhed er ny, og enhedens data indlæses stadig i Lighthouse.

**Løsning:** Når der tilføjes en lejerenhed, kan der gå 4 timer, før enhedens data vises i Fyrtårn.

Hvis data stadig ikke vises på siderne Enhedsoverholdelse og Trusselsadministration efter at have fulgt instruktionerne til løsning, skal du kontakte Support. Få mere at vide under [Få hjælp og support til Microsoft 365 Lighthouse](m365-lighthouse-get-help-and-support.md).

## <a name="related-content"></a>Relateret indhold

[Kendte problemer med Microsoft 365 Lighthouse](m365-lighthouse-known-issues.md) (artikel)\
[Microsoft 365 ofte stillede spørgsmål om Fyrtårn](m365-lighthouse-faq.yml) (artikel)\
[Få hjælp og support til Microsoft 365 Lighthouse](m365-lighthouse-get-help-and-support.md) (artikel)