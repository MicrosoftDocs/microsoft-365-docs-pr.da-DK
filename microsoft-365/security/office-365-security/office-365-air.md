---
title: Automatiseret undersøgelse og svar i Microsoft Defender for Office 365
keywords: AIR, autoIR, Microsoft Defender for Endpoint, automatiseret, undersøgelse, reaktion, afhjælpning, trusler, avanceret, trussel, beskyttelse
f1.keywords:
- NOCSH
author: dansimp
ms.author: dansimp
manager: dansimp
audience: ITPro
ms.topic: article
ms.date: 01/29/2021
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Kom i gang med at bruge automatiserede undersøgelses- og svarfunktioner i Microsoft Defender for Office 365.
ms.custom:
- air
- seo-marvel-mar2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 0fda154f8eb52ddab024a7f5bb02f980c9a05894
ms.sourcegitcommit: 44ece87e3e0c0c851dfc1e77211ac3e5e4a5b973
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/05/2022
ms.locfileid: "66617146"
---
# <a name="automated-investigation-and-response-air-in-microsoft-defender-for-office-365"></a>Automatiseret undersøgelse og reaktion (AIR) i Microsoft Defender for Office 365

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Gælder for**
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

[Microsoft Defender for Office 365](defender-for-office-365.md) indeholder effektive funktioner til automatiseret undersøgelse og svar (AIR), der kan spare dit team for sikkerhedshandlinger tid og kræfter. Når beskeder udløses, er det op til dit team af sikkerhedshandlinger at gennemse, prioritere og svare på disse beskeder. Det kan være overvældende at holde styr på mængden af indgående beskeder. Det kan hjælpe at automatisere nogle af disse opgaver.

AIR gør det muligt for dit sikkerhedsteam at arbejde mere effektivt og effektivt. AIR-funktioner omfatter automatiserede undersøgelsesprocesser som svar på velkendte trusler, der findes i dag. Passende afhjælpningshandlinger venter på godkendelse, hvilket gør det muligt for dit team af sikkerhedshandlinger at reagere effektivt på registrerede trusler. Med AIR kan dit team af sikkerhedshandlinger fokusere på opgaver med højere prioritet uden at miste vigtige beskeder, der udløses, af syne.

I denne artikel beskrives:

- [Luftstrømmens samlede strøm](#the-overall-flow-of-air);
- [Sådan får du LUFT](#how-to-get-air); Og
- De [nødvendige tilladelser](#required-permissions-to-use-air-capabilities) til at konfigurere eller bruge AIR-funktioner.
- Ændringer, der snart kommer til Microsoft 365 Defender-portalen

Denne artikel indeholder også [næste trin](#next-steps) og ressourcer til at få mere at vide.

## <a name="the-overall-flow-of-air"></a>Den samlede luftstrøm

En besked udløses, og en sikkerhedslegebog starter en automatisk undersøgelse, som resulterer i resultater og anbefalede handlinger. Her er den overordnede flow for AIR, trin for trin:

1. En automatiseret undersøgelse startes på en af følgende måder:
   - En [besked udløses](#which-alert-policies-trigger-automated-investigations) enten af noget mistænkeligt i en mail (f.eks. en meddelelse, vedhæftet fil, URL-adresse eller kompromitteret brugerkonto). Der oprettes en hændelse, og en automatisk undersøgelse starter. Eller
   - En sikkerhedsanalytiker [starter en automatisk undersøgelse](automated-investigation-response-office.md#example-a-security-administrator-triggers-an-investigation-from-threat-explorer) , mens der bruges [Stifinder](threat-explorer.md).
2. Mens en automatiseret undersøgelse kører, indsamler den data om den pågældende mail og enheder, der er relateret til den pågældende mail. Sådanne enheder kan omfatte filer, URL-adresser og modtagere. Undersøgelsens omfang kan øges, når nye og relaterede beskeder udløses.
3. Under og efter en automatiseret undersøgelse er [detaljer og resultater](air-view-investigation-results.md) tilgængelige for at få vist. Resultaterne omfatter [anbefalede handlinger](air-remediation-actions.md) , der kan udføres for at reagere på og afhjælpe eventuelle trusler, der blev fundet.
4. Teamet for sikkerhedshandlinger gennemgår [undersøgelsesresultaterne og -anbefalingerne](air-view-investigation-results.md) og [godkender eller afviser afhjælpningshandlinger](air-review-approve-pending-completed-actions.md).
5. Da ventende afhjælpningshandlinger godkendes (eller afvises), fuldføres den automatiserede undersøgelse.

I Microsoft Defender for Office 365 udføres der ingen afhjælpningshandlinger automatisk. Afhjælpningshandlinger udføres kun efter godkendelse af organisationens sikkerhedsteam. AIR-funktioner sparer tid for dit team for sikkerhedshandlinger ved at identificere afhjælpningshandlinger og angive de oplysninger, der er nødvendige for at træffe en informeret beslutning.

Under og efter hver automatiseret undersøgelse kan dit team for sikkerhedshandlinger:

- [Få vist oplysninger om en besked, der er relateret til en undersøgelse](air-view-investigation-results.md#view-details-about-an-alert-related-to-an-investigation)
- [Vis resultaterne af en undersøgelse](air-view-investigation-results.md#view-details-of-an-investigation)
- [Gennemse og godkend handlinger som et resultat af en undersøgelse](air-review-approve-pending-completed-actions.md)

> [!TIP]
> Du kan få en mere detaljeret oversigt under [Sådan fungerer AIR](automated-investigation-response-office.md).

## <a name="how-to-get-air"></a>Sådan får du LUFT

AIR-funktioner er inkluderet i [Microsoft Defender for Office 365](defender-for-office-365.md#microsoft-defender-for-office-365-plan-1-and-plan-2), forudsat at dine politikker og beskeder er konfigureret. Har du brug for hjælp? Følg vejledningen i [Beskyt mod trusler](protect-against-threats.md) for at konfigurere følgende beskyttelsesindstillinger:

- [Overvågningslogføring](../../compliance/turn-audit-log-search-on-or-off.md) (skal aktiveres)
- [Beskyttelse mod malware](protect-against-threats.md#part-1---anti-malware-protection-in-eop)
- [Beskyttelse mod phishing](../office-365-security/protect-against-threats.md#part-2---anti-phishing-protection-in-eop-and-defender-for-office-365)
- [Beskyttelse mod spam](protect-against-threats.md#part-3---anti-spam-protection-in-eop)
- [Sikre links og vedhæftede filer, der er tillid til](protect-against-threats.md#part-4---protection-from-malicious-urls-and-files-safe-links-and-safe-attachments-in-defender-for-office-365)

Derudover skal du sørge for at [gennemse organisationens politikker for beskeder](../../compliance/alert-policies.md), især [standardpolitikkerne i kategorien Trusselsadministration](../../compliance/alert-policies.md#default-alert-policies).

## <a name="which-alert-policies-trigger-automated-investigations"></a>Hvilke beskedpolitikker udløser automatiserede undersøgelser?

Microsoft 365 indeholder mange indbyggede beskedpolitikker, der hjælper med at identificere misbrug af Exchange-administratortilladelser, malwareaktivitet, potentielle eksterne og interne trusler og risici for styring af oplysninger. Flere af [standardpolitikkerne for beskeder](../../compliance/alert-policies.md#default-alert-policies) kan udløse automatiserede undersøgelser. I følgende tabel beskrives de beskeder, der udløser automatiserede undersøgelser, deres alvorsgrad på Microsoft 365 Defender portalen, og hvordan de genereres:

|Besked|Sværhedsgraden|Sådan genereres beskeden|
|---|---|---|
|Der blev registreret et potentielt skadeligt klik på URL-adressen|**Høj**|Denne besked genereres, når en af følgende opstår: <ul><li>En bruger, der er beskyttet af [sikre links](safe-links.md) i din organisation, klikker på et skadeligt link</li><li>Ændringer af dom for URL-adresser identificeres af Microsoft Defender for Office 365</li><li>Brugere tilsidesætter advarselssider for Sikre links (baseret på organisationens [politik for sikre links](set-up-safe-links-policies.md).</li></ul> <p> Du kan få flere oplysninger om hændelser, der udløser denne besked, under [Konfigurer politikker for sikre links](set-up-safe-links-policies.md).|
|En mail rapporteres af en bruger som malware eller phish|**Informative**|Denne besked genereres, når brugere i organisationen rapporterer meddelelser som phishing-mail ved hjælp af [tilføjelsesprogrammet Rapportmeddelelse](enable-the-report-message-add-in.md) eller [tilføjelsesprogrammet Rapport phishing](enable-the-report-phish-add-in.md).|
|Mails, der indeholder malware, fjernes efter levering|**Informative**|Denne besked genereres, når alle mails, der indeholder malware, leveres til postkasser i din organisation. Hvis denne hændelse indtræffer, fjerner Microsoft de inficerede meddelelser fra Exchange Online postkasser ved hjælp af [automatisk tømning på nul timer (ZAP).](zero-hour-auto-purge.md)|
|Mails, der indeholder phish-URL-adresser, fjernes efter levering|**Informative**|Denne besked genereres, når alle meddelelser, der indeholder phish, leveres til postkasser i din organisation. Hvis denne hændelse opstår, fjerner Microsoft de inficerede meddelelser fra Exchange Online postkasser ved hjælp af [ZAP](zero-hour-auto-purge.md).|
|Der registreres mistænkelige mønstre for afsendelse af mail|**Medium**|Denne besked genereres, når en person i din organisation har sendt mistænkelig mail og er i fare for at blive begrænset fra at sende mail. Beskeden er en tidlig advarsel om funktionsmåde, der kan indikere, at kontoen er kompromitteret, men ikke alvorlig nok til at begrænse brugeren. <p> Selvom det er sjældent, kan en besked, der genereres af denne politik, være en uregelmæssighed. Det er dog en god idé at [kontrollere, om brugerkontoen er kompromitteret](responding-to-a-compromised-email-account.md).|
|En bruger er begrænset til at sende mail|**Høj**|Denne besked genereres, når en person i din organisation er begrænset til at sende udgående mails. Denne besked opstår typisk, når en [mailkonto kompromitteres](responding-to-a-compromised-email-account.md). <p> Du kan få flere oplysninger om begrænsede brugere i [Fjern blokerede brugere fra portalen Brugere med begrænset adgang i Microsoft 365](removing-user-from-restricted-users-portal-after-spam.md).|

> [!TIP]
> Hvis du vil vide mere om politikker for beskeder eller redigere standardindstillingerne, skal du se [Beskedpolitikker i Microsoft Purview-compliance-portal](../../compliance/alert-policies.md).

## <a name="required-permissions-to-use-air-capabilities"></a>Påkrævede tilladelser til at bruge AIR-funktioner

Tilladelser tildeles via visse roller, f.eks. dem, der er beskrevet i følgende tabel:

|Opgave|Rolle(er) påkrævet|
|---|---|
|Konfigurer AIR-funktioner|En af følgende roller: <ul><li>Global administrator</li><li>Sikkerhedsadministrator</li></ul> <p> Disse roller kan tildeles i [Azure Active Directory](/azure/active-directory/roles/permissions-reference) eller på [Microsoft 365 Defender-portalen](permissions-microsoft-365-security-center.md).|
|Start en automatiseret undersøgelse <p> --- eller --- <p> Godkend eller afvis anbefalede handlinger|En af følgende roller, der er tildelt i [Azure Active Directory](/azure/active-directory/roles/permissions-reference) eller på [Microsoft 365 Defender-portalen](permissions-microsoft-365-security-center.md): <ul><li>Global administrator</li><li>Sikkerhedsadministrator</li><li>Sikkerhedsoperator</li><li>Sikkerhedslæser <br> --- og --- </li><li>Søg og fjern (denne rolle tildeles kun på [Microsoft 365 Defender-portalen](permissions-microsoft-365-security-center.md). Du skal muligvis oprette en ny **mail & rollegruppe for samarbejde** der og føje rollen Søg og Fjern til den nye rollegruppe.</li></ul>|

## <a name="required-licenses"></a>Påkrævede licenser

[Microsoft Defender for Office 365 Plan 2-licenser](defender-for-office-365.md#microsoft-defender-for-office-365-plan-1-and-plan-2) skal tildeles til:

- Sikkerhedsadministratorer (herunder globale administratorer)
- Organisationens team for sikkerhedshandlinger (herunder sikkerhedslæsere og dem med rollen **Søg og Fjern** )
- Slutbrugere

## <a name="changes-are-coming-soon-in-your-microsoft-365-defender-portal"></a>Ændringer kommer snart på Microsoft 365 Defender-portalen

Hvis du allerede bruger AIR-funktioner i Microsoft Defender for Office 365, kan du se nogle ændringer i den [forbedrede Microsoft 365 Defender portal](../defender/microsoft-365-defender-portal.md).

:::image type="content" source="../../media/m3d-action-center-unified.png" alt-text="Unified Action Center" lightbox="../../media/m3d-action-center-unified.png":::

Den nye og forbedrede Microsoft 365 Defender portal <https://security.microsoft.com> samler AIR-funktioner i [Microsoft Defender for Office 365](defender-for-office-365.md) og i [Microsoft Defender for Endpoint](../defender-endpoint/automated-investigations.md). Med disse opdateringer og forbedringer kan dit team for sikkerhedshandlinger få vist oplysninger om automatiserede undersøgelser og afhjælpningshandlinger på tværs af din mail, samarbejdsindhold, brugerkonti og enheder på ét sted.

> [!TIP]
> Den nye Microsoft 365 Defender-portal erstatter følgende administrationscentre:
>
> - Security & Compliance Center (<https://protection.office.com>)
> - Microsoft 365 Defender (<https://security.microsoft.com>)
>
> Ud over at URL-adressen ændres, er der et nyt udseende og en ny funktionalitet, der er designet til at give dit sikkerhedsteam en mere strømlinet oplevelse med synlighed til flere trusselsregistreringer på ét sted.

### <a name="what-to-expect"></a>Hvad kan du forvente?

I følgende tabel vises de ændringer og forbedringer, der kommer til AIR i Microsoft Defender for Office 365.

|Element|Hvad ændres?|
|---|---|
|**Siden Undersøgelser**|Den opdaterede side **Undersøgelser** er mere konsistent med det, du ser i [Microsoft Defender for Endpoint](/windows/security/threat-protection/microsoft-defender-atp/automated-investigations). Du får vist nogle generelle formaterings- og formateringsændringer, der er i overensstemmelse med den nye samlede **undersøgelsesvisning** . Undersøgelsesgrafen har f.eks. et mere ensartet format.|
|Fanen **Brugere**|Fanen **Brugere** er nu fanen **Postkasser** . Oplysninger om brugere vises under fanen **Postkasse** .|
|Fanen **Mail**|Fanen **Mail** er blevet fjernet. gå til fanen **Enheder** for at få vist en liste over mail- og mailklyngeelementer.|
|Fanen **Enheder**|Fanen **Enheder** har en fane i faneformat, der indeholder en visning af alle oversigter og muligheden for at filtrere efter objekttype. Fanen **Enheder** indeholder nu indstillingen **Gå på jagt** ud over indstillingen **Åbn i Stifinder** . Du kan nu bruge enten [Stifinder](threat-explorer.md) eller [avanceret jagt](../defender-endpoint/advanced-hunting-overview.md) til at finde enheder og trusler og filtrere på resultater.|
|Fanen **Handlinger**|Fanen Opdaterede **handlinger** indeholder nu fanen **Ventende handlinger** og fanen **Handlingers historik** . Handlinger kan godkendes (eller afvises) i en siderude, der åbnes, når du vælger en ventende handling.|
|Fanen **Beviser**|På en ny fane **med beviser** kan du se de vigtigste objektresultater, der er relateret til handlinger. Handlinger, der er relateret til hver enkelt dokumentation, kan godkendes (eller afvises) i en siderude, der åbnes, når du vælger en ventende handling.|
|**Handlingscenter**|Det opdaterede **Løsningscenter** (<https://security.microsoft.com/action-center>) samler ventende og fuldførte handlinger på tværs af mail, enheder og identiteter. Du kan få mere at vide i Løsningscenter. Du kan få mere at vide [under Løsningscenter](../defender/m365d-action-center.md).|
|**Hændelsesside**|Siden **Hændelser** korrelerer nu flere undersøgelser sammen for at give et bedre samlet overblik over undersøgelserne. ([Få mere at vide om hændelser](../defender/incidents-overview.md)).|

## <a name="next-steps"></a>Næste trin

- [Se detaljer og resultater af en automatiseret undersøgelse](air-view-investigation-results.md#view-details-of-an-investigation)
- [Gennemse og godkend ventende handlinger](air-remediation-actions.md)
