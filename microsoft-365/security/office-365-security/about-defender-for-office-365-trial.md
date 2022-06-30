---
title: Om prøveversionen af Microsoft Defender for Office 365
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
description: Administratorer kan få mere at vide om prøveversionen af Microsoft Defender for Office 365
ms.openlocfilehash: 086ea200b6f8519c487622d02ba2d2fc8347f68a
ms.sourcegitcommit: bc35c7826e3403f259725ac72cca5bafd36aa56a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/30/2022
ms.locfileid: "66554197"
---
# <a name="about-the-microsoft-defender-for-office-365-trial"></a>Om prøveversionen af Microsoft Defender for Office 365

> [!IMPORTANT]
> Kom hurtigt i gang med vores brugervenlige [prøve playbook til Microsoft Defender for Office 365](trial-playbook-defender-for-office-365.md). Denne playbook hjælper dig med at få mest ud af din gratis prøveversion ved at vise dig, hvordan du beskytter din organisation med Microsoft Defender for Office 365.

Microsoft Defender for Office 365 beskytter din organisation mod skadelige trusler, der stilles af mails, links (URL-adresser) og samarbejdsværktøjer. Defender for Office 365 omfatter:

- **Politikker til trusselsbeskyttelse**: Definer politikker for trusselsbeskyttelse for at angive det relevante beskyttelsesniveau for din organisation.
- **Rapporter**: Få vist rapporter i realtid for at overvåge Defender for Office 365 ydeevne i din organisation.
- **Trusselsundersøgelses- og svarfunktioner**: Brug avancerede værktøjer til at undersøge, forstå, simulere og forhindre trusler.
- **Automatiserede undersøgelses- og svarfunktioner**: Spar tid og kræfter på at undersøge og afhjælpe trusler.

En Microsoft Defender for Office 365 prøveversion er en nem måde at prøve funktionerne i Defender for Office 365 Plan 2 gratis med kun nogle få klik. Disse funktioner på højt niveau er beskrevet i følgende tabel:

|Funktion|Beskrivelse|
|---|---|
|[Eksklusive indstillinger i politikker til bekæmpelse af phishing](set-up-anti-phishing-policies.md#exclusive-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)|Få beskyttelse mod brugerrepræsentation, beskyttelse mod repræsentation af domæner, postkasseintelligens og avancerede tærskler for phishing.|
|[Sikre vedhæftede filer](safe-attachments.md)|Undersøg vedhæftede filer i mails og andre filer i et kontrolleret detonationsmiljø for at fange ny og undvigende malware.|
|[Sikre links](safe-links.md)|Udfør tidskontroller af klik for at sikre, at URL-adresser, der kan være gået igennem den indledende inspektion, ikke er blevet våben.|
|[Trusselssporing](threat-trackers.md)<sup>\*</sup>|Brug informative widgets og visninger til at identificere cybersikkerhedsproblemer, der kan påvirke din organisation.|
|[Threat Explorer](threat-explorer.md)<sup>\*</sup>|Gå på jagt med oplysninger næsten i realtid om trusler i din Office 365 mail.|
|[Automatiseret undersøgelse og svar (AIR)](office-365-air.md)<sup>\*</sup>|Find og afhjælp automatisk trusselsobjekter, når beskeder udløses.|
|[Træning i simulering af angreb](attack-simulation-training.md)<sup>\*</sup>|Oplær dine brugere til at identificere phishing-angreb og reagere korrekt.|
|[Kampagnevisninger](campaigns.md)<sup>\*</sup>|Undersøg og besvar omfattende ondsindet mailaktivitet.|
|[Rapporter, der bruger Defender for Office 365 funktioner](view-reports-for-mdo.md)|Få vist rapporter, herunder status for trusselsbeskyttelse, URL-trusselsbeskyttelse, mailventetid med mere.|
|[Prioritet til kontobeskyttelse](/microsoft-365/admin/setup/priority-accounts)<sup>\*</sup>|Brugere, som du identificerer som prioritetskonti, mærkes i beskeder, rapporter og undersøgelser, så de skiller sig ud. Du kan også bruge mærket Prioritet i filtre.|

<sup>\*</sup>Denne funktion er eksklusiv for Defender for Office 365 Plan 2.

## <a name="set-up-a-defender-for-office-365-trial"></a>Konfigurer en Defender for Office 365 prøveversion

En prøveversion gør det nemt for organisationer at konfigurere funktionerne til Defender for Office 365. Under installationen anvendes politikker, der udelukkende gælder for Defender for Office 365 (specifikt [sikre vedhæftede filer for mails](safe-attachments.md), [Sikre links til mails og Microsoft Teams](safe-links.md) og [repræsentationsbeskyttelse i politikker til bekæmpelse af phishing](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)) ved hjælp af standardskabelonen for [forudindstillede sikkerhedspolitikker](preset-security-policies.md).

Disse politikker er som standard begrænset til alle brugere i organisationen, men under eller efter konfigurationen af prøveversionen kan du ændre politiktildelingen til bestemte brugere.

> [!NOTE]
> Dine eksisterende politikker til bekæmpelse af spam er sandsynligvis konfigureret med handlingen **Flyt meddelelse til mappen Uønsket mail** for at få en dom med høj tillid til spam i politikker til bekæmpelse af spam. Standardskabelonen til forudindstillede sikkerhedspolitikker bruger handlingen **Karantænemeddelelse** for spam med høj sikkerhed, og forudindstillede sikkerhedspolitikker anvendes altid før brugerdefinerede politikker til bekæmpelse af spam eller standardpolitikken for spam. Du kan få flere oplysninger om standard-, Standard- og Strict-indstillinger under [Anbefalede indstillinger for EOP og Microsoft Defender for Office 365 sikkerhed](recommended-settings-for-eop-and-office365.md).

Andre arbejdsbelastninger er også tilgængelige til beskyttelse (f.eks. [sikre vedhæftede filer til SharePoint, OneDrive og Microsoft Teams](mdo-for-spo-odb-and-teams.md) og [sikre links til understøttede Office 365 apps](safe-links.md#safe-links-settings-for-office-365-apps).

Under konfigurationen af prøveversionen er svarfunktionalitet, der udelukkende gælder for Defender for Office 365 Plan 2 (f.eks. [AIR](office-365-air.md) og [Threat Explorer](threat-explorer.md), også konfigureret for hele organisationen. Der kræves ingen politikudformning.

## <a name="licensing"></a>Licensering

Som en del af konfigurationen af prøveversionen anvendes de Defender for Office 365 licenser automatisk på organisationen. Licenserne er gratis de første 90 dage.

Licenskortet til prøveversionen viser følgende oplysninger:

:::image type="content" source="../../media/mdo-trial-licensing-card.png" alt-text="Kortet Licensering i prøveversionen af Microsoft Defender for Office 365" lightbox="../../media/mdo-trial-licensing-card.png":::

- **Anvendelsestypesektion** :
  - **Prøveversion**: Antallet af prøveversioner Defender for Office 365 licenser, der er tilgængelige for dig at bruge.

    > [!NOTE]
    > På andre placeringer kan du muligvis se værdien 300 for dit antal tilgængelige prøvelicenser. Denne værdi er forkert (medmindre din organisation tilfældigvis har nøjagtigt 300 brugere). Antallet af prøvelicenser, der er tilgængelige for dig, svarer til størrelsen på din organisation og ikke den vilkårlige værdi 300.

  - **Betalt**: Antallet af betalte Defender for Office 365 licenser (hvis der er nogen).

- **Anvendelsesafsnit**: Hvor mange af dine brugere, der er omfattet af Defender for Office 365 politikker.
  - **Registrering & kun svar**: Det samlede antal brugere, der er inkluderet i følgende scenarier:
    - I løbet af prøveversionen har du begrænset politikkerne til bestemte brugere.
    - Du har brugerdefinerede politifolk, der er beregnet til bestemte brugere.
  - **Fuld beskyttelse**: Det samlede antal brugere, der er beskyttet af Defender for Office 365 Plan 2-funktioner (AIR, Threat Explorer, træning i simulering af angreb osv.).

Du kan finde prisoplysninger [under Microsoft Defender for Office 365](https://www.microsoft.com/security/business/siem-and-xdr/microsoft-defender-office-365).

## <a name="permissions"></a>Tilladelser

Hvis du vil starte eller afslutte prøveversionen, skal du være medlem af rollerne **Global administrator** eller **Sikkerhedsadministrator** i Azure Active Directory. Du kan finde flere oplysninger under [Om administratorroller](../../admin/add-users/about-admin-roles.md).

## <a name="additional-information"></a>Flere oplysninger:

Når du har startet prøveversionen, kan det tage op til 2 timer, før ændringerne og opdateringerne er tilgængelige. Og administratorer skal logge af og logge på igen for at se ændringerne.

## <a name="availability"></a>Tilgængelighed

Den Defender for Office 365 prøveversion udrulles gradvist til eksisterende kunder, der opfylder bestemte kriterier, og som ikke har eksisterende Defender for Office 365 Plan 2-licenser (inkluderet i deres abonnement eller som et tilføjelsesprogram).

## <a name="terms-and-conditions"></a>Vilkår og betingelser

Du kan få flere oplysninger [under vilkår & betingelser for Microsoft Defender for Office 365 prøveversion](defender-for-office-365-trial-terms-and-conditions.md).

## <a name="frequently-asked-questions"></a>Ofte stillede spørgsmål

### <a name="q-how-do-i-extend-the-trial"></a>Spørgsmål: Hvordan gør jeg forlænge prøveversionen?

Svar: Se [Forlæng din prøveversion](/microsoft-365/commerce/try-or-buy-microsoft-365#extend-your-trial).

### <a name="q-what-happens-to-my-data-after-the-trial-expires"></a>Spørgsmål: Hvad sker der med mine data, når prøveversionen udløber?

Svar: Når din prøveversion udløber, har du adgang til dine prøvedata (data fra funktioner i Defender for Office 365, som du ikke tidligere har haft) i 30 dage. Efter denne 30-dages periode slettes alle politikker og data, der er knyttet til den Defender for Office 365 prøveversion.

### <a name="q-how-many-times-can-i-use-the-defender-for-office-365-trial-in-my-organization"></a>Spørgsmål: Hvor mange gange kan jeg bruge prøveversionen af Defender for Office 365 i min organisation?

Sv.: Maksimalt 2 gange. Hvis din første prøveversion udløber, skal du vente mindst 30 dage efter udløbsdatoen, før du kan tilmelde dig Defender for Office 365 prøveversion igen. Efter din anden prøveversion kan du ikke tilmelde dig en anden prøveversion.

## <a name="learn-more-about-defender-for-office-365"></a>Få mere at vide om Defender for Office 365

Defender for Office 365 hjælper organisationer med at sikre deres virksomhed ved at tilbyde en omfattende tavle af egenskaber.

Du kan også få mere at vide om Defender for Office 365 i denne [interaktive vejledning](https://aka.ms/MS365D.InteractiveGuide).

:::image type="content" source="../../media/microsoft-defender-for-office-365.png" alt-text="Det Microsoft Defender for Office 365 konceptuelle diagram" lightbox="../../media/microsoft-defender-for-office-365.png":::

### <a name="prevention"></a>Forebyggelse

En robust filtreringsstak forhindrer en lang række volumenbaserede og målrettede angreb, herunder kompromitteret virksomhedsmail, phishing af legitimationsoplysninger, ransomware og avanceret malware.

- [Anti-phishing-politikker: Eksklusive indstillinger i Defender for Office 365](set-up-anti-phishing-policies.md#exclusive-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)
- [Sikre vedhæftede filer](safe-attachments.md)
- [Sikre links](safe-links.md)

### <a name="detection"></a>Påvisning

Brancheførende AI registrerer skadeligt og mistænkeligt indhold og korrelerer angrebsmønstre for at identificere kampagner, der er designet til at undgå beskyttelse.

- [Kampagnevisninger i Microsoft Defender for Office 365](campaigns.md)

### <a name="investigation-and-hunting"></a>Undersøgelse og jagt

Effektive oplevelser hjælper med at identificere, prioritere og undersøge trusler med avancerede jagtegenskaber til sporing af angreb på tværs af Office 365.

- [Trusselsoversigt og registreringer i realtid](threat-explorer.md)
- [Rapporter i realtid i Defender for Office 365](view-reports-for-mdo.md)
- [Threat Trackers – ny og bemærkelsesværdig](threat-trackers.md)
- Integration med [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

### <a name="response-and-remediation"></a>Svar og afhjælpning

Omfattende funktioner til svar på hændelser og automatisering forstærker dit sikkerhedsteams effektivitet og effektivitet.

- [Automatiseret undersøgelse og reaktion (AIR) i Microsoft Defender for Office 365](office-365-air.md)

### <a name="awareness-and-training"></a>Opmærksomhed og uddannelse

Omfattende simulerings- og oplæringsfunktioner sammen med integrerede oplevelser i klientprogrammer skaber brugerbevidsthed.

- [Kom i gang med at bruge kursus i angrebssimulering](attack-simulation-training-get-started.md)

### <a name="security-posture"></a>Sikkerhedsholdning

Anbefalede skabeloner og konfigurationsindsigt hjælper kunderne med at få og forblive sikre.

- [Forudindstillede sikkerhedspolitikker i EOP og Microsoft Defender for Office 365](preset-security-policies.md)
- [Konfigurationsanalyse til beskyttelsespolitikker i EOP og Microsoft Defender for Office 365](configuration-analyzer-for-security-policies.md).

## <a name="give-feedback"></a>Giv feedback

Din feedback hjælper os med at blive bedre til at beskytte dit miljø mod avancerede angreb. Del din oplevelse og dine visninger af produktegenskaber og prøveversionsresultater.
