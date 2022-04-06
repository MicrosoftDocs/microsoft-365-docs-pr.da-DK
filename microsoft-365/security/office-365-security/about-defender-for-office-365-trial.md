---
title: Om microsoft Defender for Office 365 prøveversion
f1.keywords: ''
ms.author: chrisda
author: chrisda
manager: dansimp
audience: Admin
ms.topic: overview
ms.prod: m365-security
ms.technology: mdo
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: ''
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.custom:
- seo-marvel-apr2020
ROBOTS: NOINDEX, NOFOLLOW
description: Administratorer kan få mere at vide om prøveversionen af Microsoft Defender til Office 365
ms.openlocfilehash: 40ad151dfa4ee26bf1e6177dda170cc2998c7c7e
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/20/2022
ms.locfileid: "63683861"
---
# <a name="about-the-microsoft-defender-for-office-365-trial"></a>Om microsoft Defender for Office 365 prøveversion

> [!IMPORTANT]
> Kom hurtigt i gang med vores [brugervenlige prøvespilbog til Microsoft Defender til Office 365](trial-playbook-defender-for-office-365.md). Denne playbook hjælper dig med at få mest muligt ud af din gratis prøveversion ved at vise dig, hvordan du beskytter din organisation med Microsoft Defender for Office 365.

Microsoft Defender for Office 365 beskytter din organisation mod skadelige trusler, der kan udgøres af mails, links (URL-adresser) og samarbejdsværktøjer. Defender til Office 365 omfatter:

- **Politikker for trusselsbeskyttelse**: Definer politikker for trusselsbeskyttelse for at angive det passende beskyttelsesniveau for organisationen.
- **Rapporter**: Få vist rapporter i realtid for at overvåge Defender Office 365 ydeevnen i organisationen.
- **Funktioner til trusselsundersøgelse og svar**: Brug førende værktøjer til at undersøge, forstå, simulere og forhindre trusler.
- **Automatiserede undersøgelses- og svarmuligheder**: Spar tid og besvær med at undersøge og mindske trusler.

En Microsoft Defender for Office 365-prøveversion er en nem måde at afprøve funktionerne i Defender til Office 365 Plan 2 gratis efter blot nogle få klik. Disse funktioner på højt niveau er beskrevet i følgende tabel:

|Funktion|Beskrivelse|
|---|---|
|[Eksklusive indstillinger i antiphishing-politikker](set-up-anti-phishing-policies.md#exclusive-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)|Få beskyttelse af bruger efterligning, beskyttelse af domæne efterligning, postkasseintelligens og avancerede tærskelværdier for phishing.|
|[Pengeskab vedhæftede filer](safe-attachments.md)|Undersøg vedhæftede filer i mails og andre filer i et kontrolleret detonationsmiljø for at opfange ny og undgår malware.|
|[Sikre links](safe-links.md)|Udfør kontroltid for klik for at sikre, at URL-adresser, der eventuelt har bestået den indledende inspektion, ikke er blevet overdimensioneret.|
|[Threat Trackers](threat-trackers.md)<sup>\*</sup>|Brug informative widgets og visninger til at identificere cybersikkerhedsproblemer, der kan påvirke din organisation.|
|[Threat Explorer](threat-explorer.md)<sup>\*</sup>|På jagt efter næsten realtidsoplysninger om trusler i din Office 365 mail.|
|[Automatiseret undersøgelse og svar (AIR)](office-365-air.md)<sup>\*</sup>|Find og afhjulpet trusselsobjekter automatisk, når der udløses beskeder.|
|[Kursus i angrebssimulering](attack-simulation-training.md)<sup>\*</sup>|Oplære dine brugere til at identificere phishing-angreb og reagere korrekt.|
|[Kampagnevisninger](campaigns.md)<sup>\*</sup>|Undersøg og svar på omfattende ondsindede mailaktiviteter.|
|[Rapporter, der bruger Defender Office 365 funktioner](view-reports-for-mdo.md)|Få vist rapporter, herunder status for trusselsbeskyttelse, URL-trusselsbeskyttelse, mailventetid og meget mere.|
|[Prioritetskontobeskyttelse](/microsoft-365/admin/setup/priority-accounts)<sup>\*</sup>|Brugere, som du identificerer som Prioritet-konti, mærkes i beskeder, rapporter og undersøgelser, så de skiller sig ud. Du kan også bruge mærket Prioritet i filtre.|

<sup>\*</sup>Denne funktion er eksklusiv for Defender Office 365 Plan 2.

## <a name="set-up-a-defender-for-office-365-trial"></a>Konfigurer en Defender for Office 365 prøveversion

En prøveversion giver organisationer mulighed for nemt at konfigurere Defender til Office 365 funktioner. Under konfigurationen anvendes politikker, der er eksklusive til Defender for Office 365 (specifikt [Pengeskab](safe-attachments.md) Vedhæftede filer til mails, [Pengeskab Links](safe-links.md) til mails og Microsoft Teams og beskyttelse mod [phishing](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)) ved hjælp af standardskabelonen [til](preset-security-policies.md) forudindstillede sikkerhedspolitikker.

Som standard er disse politikker begrænset til alle brugere i organisationen, men under eller efter konfigurationen af prøveversionen kan du ændre politiktildelingen til bestemte brugere.

> [!NOTE]
> Dine eksisterende antispampolitikker er sandsynligvis konfigureret med handlingen Flyt meddelelsen til mappen Uønsket **mail for at** få en konfidenskonfidens af spamkonst indhold i antispam-politikker. Skabelonen Standard til forudindstillede sikkerhedspolitikker bruger handlingen Karantæne-meddelelse **for at** sikre spam, og foruddefinerede sikkerhedspolitikker anvendes altid før brugerdefinerede antispampolitikker eller standardpolitikken for uønsket post. Du kan finde flere oplysninger om standardindstillinger, standardindstillinger og strenge indstillinger under Anbefalede indstillinger [for EOP og Microsoft Defender Office 365 sikkerhed](recommended-settings-for-eop-and-office365.md).

Andre arbejdsbelastninger er også tilgængelige med henblik på beskyttelse (f.eks. Pengeskab Vedhæftede filer [til SharePoint, OneDrive og Microsoft Teams](mdo-for-spo-odb-and-teams.md) [og Pengeskab Links til understøttede Office 365 apps](safe-links.md#safe-links-settings-for-office-365-apps).

Under konfigurationen af prøveversionen er svarfunktionalitet, der er eksklusiv for Defender til Office 365 Plan 2 (f.eks. [er AIR](office-365-air.md) og [Threat Explorer](threat-explorer.md) også konfigureret for hele organisationen. Ingen angivelse af politik er påkrævet.

## <a name="licensing"></a>Licensering

Som en del af konfigurationen af prøveversionen anvendes Defender for Office 365-licenser automatisk til organisationen. Licenserne er gratis i de første 90 dage.

Licenskortet for prøveversionen viser følgende oplysninger:

![Licenskortet i Microsoft Defender for Office 365 prøveversionen.](../../media/mdo-trial-licensing-card.png)

- **Sektionen Brugstype** :
  - **Prøveversion**: Antallet af Defender-prøveversioner til Office 365, der er tilgængelige for dig at bruge.

    > [!NOTE]
    > På andre placeringer får du muligvis vist værdien 300 for antallet af tilgængelige prøvelicenser. Denne værdi er forkert (medmindre din organisation har nøjagtigt 300 brugere). Antallet af prøvelicenser, der er tilgængelige for dig, svarer til størrelsen af organisationen, ikke den vilkårlige værdi 300.

  - **Betalt**: Antallet af betalte Defender-licenser Office 365 (hvis der er nogen).

- **Sektionen** Brug: Hvor mange af dine brugere, der er dækket af Defender Office 365 politikker.
  - **Kun & registreringssvar**: Det samlede antal brugere, der er inkluderet i følgende scenarier:
    - Under prøveperioden har du begrænset politikkerne til bestemte brugere.
    - Du har brugerdefinerede politikforanstaltninger, der er tilpassede til bestemte brugere.
  - **Fuld beskyttelse**: Det samlede antal brugere, der er beskyttet af Defender til Office 365 Plan 2-funktioner (AIR, Threat Explorer, kursus i angrebssimulering osv.).

## <a name="permissions"></a>Tilladelser

Hvis du vil starte eller afslutte prøveabonnementet, skal du være medlem af **rollerne Global administrator** eller Sikkerhedsadministrator i Azure Active Directory. Du kan få mere at vide [under Om administratorroller](../../admin/add-users/about-admin-roles.md).

## <a name="additional-information"></a>Flere oplysninger:

Når du starter prøveversionen, kan det tage op til 2 timer, før ændringerne og opdateringerne er tilgængelige. Og administratorer skal logge af og logge på igen for at se ændringerne.

## <a name="availability"></a>Tilgængelighed

Defender for Office 365-prøveversionen udrulles gradvist til eksisterende kunder, der opfylder bestemte kriterier, og som ikke har eksisterende Defender til Office 365 Plan 2-licenser (inkluderet i deres abonnement eller som et tilføjelsesprogrammet).

## <a name="terms-and-conditions"></a>Vilkår og betingelser

Du kan finde flere oplysninger [under Vilkår for Office 365 for microsoft-& prøveversioner](defender-for-office-365-trial-terms-and-conditions.md).

## <a name="frequently-asked-questions"></a>Ofte stillede spørgsmål

### <a name="q-how-do-i-extend-the-trial"></a>Sp: Hvordan forlænger jeg prøveabonnementet?

A: Se [Forlæng dit prøveabonnement](/microsoft-365/commerce/try-or-buy-microsoft-365#extend-your-trial).

### <a name="q-what-happens-to-my-data-after-the-trial-expires"></a>Sp: Hvad sker der med mine data, når prøveperioden udløber?

A: Når prøveperioden udløber, har du adgang til dine prøvedata (data fra funktioner i Defender for Office 365, som du ikke har haft tidligere) i 30 dage. Efter denne periode på 30 dage slettes alle politikker og data, der er knyttet til Defender Office 365-prøveabonnementet.

### <a name="q-how-many-times-can-i-use-the-defender-for-office-365-trial-in-my-organization"></a>Sp: Hvor mange gange kan jeg bruge Defender til Office 365 prøveversion i min organisation?

A: Maksimalt 2 gange. Hvis dit første prøveabonnement udløber, skal du vente mindst 30 dage efter udløbsdatoen, før du kan tilmelde dig Defender for Office 365 prøveversionen igen. Efter dit andet prøveabonnement kan du ikke tilmelde dig et andet prøveabonnement.

## <a name="learn-more-about-defender-for-office-365"></a>Få mere at vide om Defender Office 365

Defender for Office 365 hjælper organisationer med at sikre deres virksomhed ved at tilbyde en lang række funktioner.

Du kan også få mere at vide om Defender Office 365 i denne [interaktive vejledning](https://aka.ms/MS365D.InteractiveGuide).

![Konceptdiagram for Microsoft Defender Office 365 grundlæggende diagram.](../../media/microsoft-defender-for-office-365.png)

### <a name="prevention"></a>Forebyggelse

En robust filtreringsstak forhindrer en lang række mængdebaserede og målrettede angreb, herunder forlig med virksomhedsmail, phishing med legitimationsoplysninger, ransomware og avanceret malware.

- [Antiphishing-politikker: Eksklusive indstillinger i Defender til Office 365](set-up-anti-phishing-policies.md#exclusive-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)
- [Pengeskab vedhæftede filer](safe-attachments.md)
- [Sikre links](safe-links.md)

### <a name="detection"></a>Registrering

Brancheførende AI registrerer skadeligt og mistænkeligt indhold og korrelerer angrebsmønstre for at identificere kampagner, der er udviklet til at undgå beskyttelse.

- [Kampagnevisninger i Microsoft Defender for Office 365](campaigns.md)

### <a name="investigation-and-hunting"></a>Undersøgelse og jagt

Effektive oplevelser hjælper med at identificere, prioritere og undersøge trusler med avancerede muligheder for at spore angreb på tværs Office 365.

- [Registreringer af Trusselsstifinder og i realtid](threat-explorer.md)
- [Rapporter i realtid i Defender for Office 365](view-reports-for-mdo.md)
- [Threat Trackers – nye og be noterede](threat-trackers.md)
- Integration med [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

### <a name="response-and-remediation"></a>Svar og afhjælpning

Omfattende muligheder for hændelsesrespons og automatisering øger dit sikkerhedsteams effektivitet.

- [Automatiseret undersøgelse og svar (AIR) i Microsoft Defender for Office 365](office-365-air.md)

### <a name="awareness-and-training"></a>Opmærksomhed og kurser

Omfattende simulerings- og undervisningsfunktioner samt integrerede oplevelser i klientprogrammer skaber brugerindsigt.

- [Kom i gang med at bruge simuleringskursus til angreb](attack-simulation-training-get-started.md)

### <a name="security-posture"></a>Sikkerhedsstilling

Anbefalede skabeloner og konfigurationsindsigt hjælper kunderne med at få og forblive sikre.

- [Forudindstillede sikkerhedspolitikker i EOP og Microsoft Defender Office 365](preset-security-policies.md)
- [Konfigurationsanalyse til beskyttelsespolitikker i EOP og Microsoft Defender til Office 365](configuration-analyzer-for-security-policies.md).

## <a name="give-feedback"></a>Giv feedback

Din feedback hjælper os med at blive bedre til at beskytte dit miljø mod avancerede angreb. Del din oplevelse og dine indtryk af produktegenskaber og prøveresultater.
