---
title: Nyheder i Microsoft Defender til Office 365
description: Få mere at vide om de nye funktioner og den nye funktionalitet i den nyeste version af Microsoft Defender Office 365.
keywords: nyheder i Microsoft Defender til Office 365, ga, generelt tilgængelige, tilgængelige, nye
search.appverid: met150
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: tracyp
author: msfttracyp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.topic: conceptual
ms.date: 12/03/2021
ms.custom: seo-marvel-apr2020
ms.reviewer: vippand
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 5ae288b2d7dbaec9f66a501f7177741a5df48d0c
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63597861"
---
# <a name="whats-new-in-microsoft-defender-for-office-365"></a>Nyheder i Microsoft Defender til Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for:**

- [Microsoft Defender til Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Denne artikel viser en liste over nye funktioner i den nyeste version af Microsoft Defender Office 365. Funktioner, der i øjeblikket er i forhåndsvisning, er angivet med **(forhåndsvisning)**.

Få mere at vide ved at [se denne video](https://www.youtube.com/watch?v=Tdz6KfruDGo&list=PL3ZTgFEc7LystRja2GnDeUFqk44k7-KXf&index=3).

> [!TIP]
> Har du ikke Microsoft Defender til Office 365 endnu? [Kontakt salg for at starte en prøveversion](https://info.microsoft.com/ww-landing-M365SMB-web-contact.html).

Du kan finde flere oplysninger om nyheder i forbindelse med andre Microsoft Defender-sikkerhedsprodukter her:

- [Nyheder i Microsoft 365 Defender](../defender/whats-new.md)
- [Nyheder i Microsoft Defender til slutpunkt](../defender-endpoint/whats-new-in-microsoft-defender-endpoint.md)
- [Nyheder i Microsoft Defender for Identity](/defender-for-identity/whats-new)
- [Nyheder i Microsoft Cloud App Security](/cloud-app-security/release-notes)

## <a name="march-2022"></a>Marts 2022

- [Strømlinet indsendelsesoplevelse i Microsoft Defender til Office 365](https://techcommunity.microsoft.com/t5/microsoft-defender-for-office/streamlining-the-submissions-experience-in-microsoft-defender/ba-p/3152080): Introduktion til den nye samlede og strømlinede indsendelsesproces for at gøre din oplevelse enklere.


## <a name="january-2022"></a>Januar 2022

- [Opdaterede oplevelser med jagt og undersøgelse til Microsoft Defender til Office 365](https://techcommunity.microsoft.com/t5/microsoft-defender-for-office/updated-hunting-and-investigation-experiences-for-microsoft/ba-p/3002015): Introduktion til panelet til mailoversigt for oplevelser i Defender til Office 365 samt oplevelsesopdateringer til Threat Explorer og registreringer i realtid.


## <a name="october-2021"></a>Oktober 2021

- [Avanceret forbedring af DKIM-levering](configure-advanced-delivery.md): Tilføjet understøttelse af DKIM-domænepost som en del af konfiguration af phishing-simulering fra tredjepart.
- [Sikker som standard](secure-by-default.md): Udvidet sikker som standard for Exchange regler for mailflow (også kaldet transportregler).

## <a name="september-2021"></a>September 2021

- [Forbedret rapporteringsoplevelse i Defender til Office 365](https://techcommunity.microsoft.com/t5/microsoft-defender-for-office/improving-the-reporting-experience-in-microsoft-defender-for/ba-p/2760898)
- [Karantænepolitikker](quarantine-policies.md): Administratorer kan konfigurere detaljeret kontrol for modtageradgang til meddelelser, der er sat i karantæne, og tilpasse beskeder om spam til slutbrugeren.
  - [Video om administratoroplevelse](https://youtu.be/vnar4HowfpY)
  - [Video af slutbrugeroplevelsen](https://youtu.be/s-vozLO43rI)
  - Andre nye funktioner, der er på vej til karantæne, er beskrevet i dette blogindlæg: [Forenkle karantæneoplevelsen](https://techcommunity.microsoft.com/t5/microsoft-defender-for-office/simplifying-the-quarantine-experience/ba-p/2676388).
- Portalomdirigering er som standard startet, hvilket omdirigerer brugere fra & overholdelse Microsoft 365 Defender <https://security.microsoft.com>. Du kan finde flere oplysninger under: [Omdirigere konti fra Office 365 Security and Compliance Center til Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-security-mdo-redirection)

## <a name="august-2021"></a>August 2021

- [Administratorgennemsyn for rapporterede](admin-review-reported-message.md) meddelelser: Administratorer kan nu sende skabelonmeddelelser tilbage til slutbrugere, efter de har gennemset rapporterede meddelelser. Skabelonerne kan tilpasses til din organisation og baseres også på din administrators konklusion.
- [Tilføj tilladelse](manage-tenant-allows.md) i lejerens tilladelses-/blokeringsliste: Du kan nu føje tilladte poster til lejerens tilladelses-/blokeringsliste, hvis den blokerede meddelelse blev sendt som en del af administratorindsendelsesprocessen. Afhængigt af blokkens art føjes den sendte URL-adresse, fil og/eller senderen til lejerens tilladelses-/blokeringsliste. I de fleste tilfælde tilføjes tilladelse til at give systemet noget tid og tillade det naturligt, hvis det garanteres. I nogle tilfælde administrerer Microsoft tilladen for dig.

## <a name="july-2021"></a>Juli 2021

- [Forbedringer af mailanalyse i automatiserede undersøgelser](email-analysis-investigations.md)
- [Avanceret](configure-advanced-delivery.md) levering: Introduktion til en ny funktion til konfiguration af levering af phishing-simuleringer fra tredjeparter til brugere og ufiltrerede meddelelser til postkasser til sikkerhedsfunktioner.
- [Pengeskab links til Microsoft Teams](safe-links.md#safe-links-settings-for-microsoft-teams)
- Nye politikker for påmindelser om følgende scenarier: kompromitterede postkasser, phishingformularer, skadelige mails leveret på grund af tilsidesættelser og afrunding af ZAP
  - Mistænkelig videresendelse af mail
  - Bruger begrænset fra delingsformularer og indsamling af svar
  - Formular blokeret på grund af potentielt forsøg på phishing
  - Formular markeret med flag og bekræftet som phishing
  - [Nye beskedpolitikker for ZAP](../../compliance/new-defender-alert-policies.md)
- Microsoft Defender til Office 365-beskeder er nu integreret i Microsoft 365 Defender – [Microsoft 365 Defender samlet advarselskø og samlet advarselskø](../defender/investigate-alerts.md)
- [Brugermærker](user-tags.md) er nu integreret i Microsoft Defender til Office 365-påmindelsesoplevelser, herunder: køen med beskeder og detaljer i Office 365 Security & Compliance og angivelse af brugerdefinerede politikker for påmindelser til brugermærker for at oprette målrettede beskedpolitikker.
  - Mærker er også tilgængelige i køen til samlede beskeder i Microsoft 365 Defender portal (Microsoft Defender for Office 365 Plan 2)

## <a name="june-2021"></a>Juni 2021

- Indstillingen Ny sikkerhedstip inden for antiphishing-politikker. Denne sikkerhedstip vises, når modtagerne først modtager en mail fra en afsender eller ikke ofte modtager mails fra en afsender. Du kan finde flere oplysninger om denne indstilling, og hvordan du konfigurerer den, i følgende artikler:
  - [Første kontakt sikkerhedstip](set-up-anti-phishing-policies.md#first-contact-safety-tip)
  - [Konfigurer antiphishing-politikker i EOP](configure-anti-phishing-policies-eop.md)
  - [Konfigurer antiphishing-politikker i Microsoft Defender til Office 365](configure-mdo-anti-phishing-policies.md)

## <a name="aprilmay-2021"></a>April/maj 2021

- [Siden Mailenhed](mdo-email-entity-page.md): En samlet 360-graders visning af en mail med forbedrede oplysninger om trusler, godkendelse og registreringer, detonationsdetaljer og en helt ny oplevelse af maileksempel.
- [Office 365-administrations-API](/office/office-365-management-api/office-365-management-activity-api-schema#email-message-events): Opdateringer til EmailEvents (RecordType 28) for at tilføje leveringshandling, oprindelige og seneste leveringsplaceringer samt opdaterede registreringsoplysninger.
- [Threat Analytics for Defender til Office 365](/microsoft-365/security/defender/threat-analytics): Få vist aktive trusselseksperter, populære teknikker og angrebsoverflader sammen med omfattende rapportering fra Microsoft-agenter omkring igangværende kampagner.

## <a name="februarymarch-2021"></a>Februar/marts 2021

- Integration af besked-id (søgning ved hjælp af alert-id Alert-Explorer navigation) i [jagtoplevelser](threat-explorer.md)
- Øge grænsen for eksport af poster fra 9990 til 200.000 i [jagtoplevelser](threat-explorer.md)
- Udvidelse af stifinderen (og registreringer i realtid) af dataopbevaring og søgegrænse for prøvelejere fra 7 (tidligere grænse) til 30 dage i [jagtoplevelser](threat-explorer.md)
- Nye pivots ved navn **Impersonated domain** and **Impersonated** user within the Explorer (and Real-time detections) to search for impersonation attacks against protected users or domains. Du kan få mere at vide under [detaljer](threat-explorer.md#view-phishing-emails-sent-to-impersonated-users-and-domains). (Microsoft Defender til Office 365 Plan 1 eller Plan 2)


## <a name="microsoft-defender-for-office-365-plan-1-and-plan-2"></a>Microsoft Defender til Office 365 Plan 1 og Plan 2

Vidste du, at Microsoft Defender for Office 365 er tilgængelig i to planer? [Få mere at vide om, hvad hver plan indeholder](defender-for-office-365.md#microsoft-defender-for-office-365-plan-1-and-plan-2).

## <a name="see-also"></a>Se også

[Microsoft 365 oversigt](https://www.microsoft.com/microsoft-365/roadmap)

[Beskrivelse af Microsoft Defender Office 365-tjenesten](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description)
