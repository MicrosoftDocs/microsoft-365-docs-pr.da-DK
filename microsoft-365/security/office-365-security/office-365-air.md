---
title: Automatiseret undersøgelse og svar i Microsoft Defender for Office 365
keywords: AIR, autoIR, Microsoft Defender for Endpoint, automatiseret, undersøgelse, svar, afhjælpning, trusler, avanceret, trussel, beskyttelse
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
description: Kom i gang med automatiseret undersøgelse og svarfunktioner Microsoft Defender for Office 365.
ms.custom:
- air
- seo-marvel-mar2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: e9cd2388d3551ccc0c180d20a92ec0c513472797
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64473667"
---
# <a name="automated-investigation-and-response-air-in-microsoft-defender-for-office-365"></a>Automatiseret undersøgelse og svar (AIR) i Microsoft Defender for Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

[Microsoft Defender for Office 365 indeholder](defender-for-office-365.md) effektive funktioner til automatisk undersøgelse og svar (AIR), som kan spare tid og besvær for dit sikkerhedsteam. Når der udløses beskeder, er det op til dit sikkerhedsteam at gennemse, prioritere og reagere på disse beskeder. Det kan være overvældende at holde styr på mængden af indgående beskeder. Det kan være en hjælp at automatisere nogle af disse opgaver.

AIR gør det muligt for dit sikkerhedsteam at fungere mere effektivt. AIR-funktioner omfatter automatiserede undersøgelsesprocesser som reaktion på velkendte trusler, der findes i dag. Relevante afhjælpningshandlinger afventer godkendelse, så dit sikkerhedsteam kan reagere effektivt på registrerede trusler. Med AIR kan dit sikkerhedsteam fokusere på opgaver med højere prioritet, uden at de vigtige beskeder, der udløses, går tabt.

I denne artikel beskrives følgende:

- Den [overordnede strøm af AIR](#the-overall-flow-of-air);
- [Sådan får du AIR](#how-to-get-air); og
- De [nødvendige tilladelser til](#required-permissions-to-use-air-capabilities) at konfigurere eller bruge AIR-funktioner.
- Ændringer, der snart kommer til din Microsoft 365 Defender-portal

Denne artikel indeholder også næste [trin og](#next-steps) ressourcer til at få mere at vide.

## <a name="the-overall-flow-of-air"></a>Den overordnede strøm af AIR

Der udløses en besked, og en sikkerhedsspilbog starter en automatisk undersøgelse, som resulterer i resultater og anbefalede handlinger. Her er den overordnede strøm af AIR, trin for trin:

1. En automatisk undersøgelse igangsættes på en af følgende måder:
   - Enten [udløses en advarsel af noget](#which-alert-policies-trigger-automated-investigations) mistænkeligt i en mail (f.eks. en meddelelse, vedhæftet fil, URL-adresse eller kompromitteret brugerkonto). Der oprettes en hændelse, og en automatisk undersøgelse begynder; eller
   - En sikkerhedsanalytiker starter [en automatisk undersøgelse, mens](automated-investigation-response-office.md#example-a-security-administrator-triggers-an-investigation-from-threat-explorer) du bruger [Stifinder](threat-explorer.md).
2. Mens en automatisk undersøgelse kører, indsamler den data om den pågældende mail og enheder, der er relateret til den pågældende mail. Sådanne enheder kan omfatte filer, URL-adresser og modtagere. Undersøgelsens omfang kan øges, efterhånden som der udløses nye og relaterede beskeder.
3. Under og efter en automatiseret undersøgelse [er det muligt at få](air-view-investigation-results.md) vist detaljer og resultater. Resultaterne omfatter [anbefalede handlinger](air-remediation-actions.md) , der kan tages for at reagere på og afhjælpe eventuelle trusler, der blev fundet.
4. Dit sikkerhedsteam gennemser [undersøgelsesresultaterne og anbefalingerne](air-view-investigation-results.md) [og godkender eller afviser afhjælpningshandlinger](air-review-approve-pending-completed-actions.md).
5. Efterhånden som ventende afhjælpningshandlinger godkendes (eller afvises), fuldføres den automatiske undersøgelse.

I Microsoft Defender for Office 365 bliver der ikke foretaget nogen afhjælpningshandlinger automatisk. Afhjælpningshandlingerne skal kun løses, når organisationens sikkerhedsteam har godkendt det. AIR-funktioner sparer tid for sikkerhedsteamet ved at identificere afhjælpningshandlinger og angive de oplysninger, der er nødvendige for at træffe en velovervejet beslutning.

Under og efter hver automatiseret undersøgelse kan dit sikkerhedsteam:

- [Få vist oplysninger om en besked i forbindelse med en undersøgelse](air-view-investigation-results.md#view-details-about-an-alert-related-to-an-investigation)
- [Få vist resultaterne af en undersøgelse](air-view-investigation-results.md#view-details-of-an-investigation)
- [Gennemse og godkend handlinger som et resultat af en undersøgelse](air-review-approve-pending-completed-actions.md)

> [!TIP]
> Du kan få en mere detaljeret oversigt under [Sådan fungerer AIR](automated-investigation-response-office.md).

## <a name="how-to-get-air"></a>Sådan får du AIR

AIR-funktioner er inkluderet [Microsoft Defender for Office 365](defender-for-office-365.md#microsoft-defender-for-office-365-plan-1-and-plan-2), forudsat at dine politikker og beskeder er konfigureret. Har du brug for hjælp? Følg vejledningen i [Beskyt mod trusler for](protect-against-threats.md) at konfigurere følgende beskyttelsesindstillinger:

- [Overvågningslogføring](../../compliance/turn-audit-log-search-on-or-off.md) (skal være slået til)
- [Beskyttelse mod malware](protect-against-threats.md#part-1---anti-malware-protection-in-eop)
- [Beskyttelse mod phishing](../office-365-security/protect-against-threats.md#part-2---anti-phishing-protection-in-eop-and-defender-for-office-365)
- [Beskyttelse mod uønsket post](protect-against-threats.md#part-3---anti-spam-protection-in-eop)
- [Pengeskab links og Pengeskab vedhæftede filer](protect-against-threats.md#part-4---protection-from-malicious-urls-and-files-safe-links-and-safe-attachments-in-defender-for-office-365)

Desuden skal du sørge for [at gennemse organisationens advarselspolitikker](../../compliance/alert-policies.md), især [standardpolitikkerne i kategorien Trusselsadministration](../../compliance/alert-policies.md#default-alert-policies).

## <a name="which-alert-policies-trigger-automated-investigations"></a>Hvilke beskedpolitikker udløser automatiserede undersøgelser?

Microsoft 365 indeholder mange indbyggede politikker for påmindelser, som hjælper med at identificere Exchange misbrug af administratortilladelser, malwareaktivitet, potentielle eksterne og interne trusler samt risiko for informationsstyring. Flere af [standardbeskedpolitikker kan](../../compliance/alert-policies.md#default-alert-policies) udløse automatiserede undersøgelser. I følgende tabel beskrives de beskeder, der udløser automatiserede undersøgelser, deres alvorsgrad i Microsoft 365 Defender, og hvordan de genereres:

|Besked|Alvorsgrad|Sådan genereres beskeden|
|---|---|---|
|Der blev fundet et potentielt ondsindet klik på webadressen|**Høj**|Denne besked genereres, når et af følgende sker: <ul><li>En bruger, der [er Pengeskab links](safe-links.md) i organisationen, klikker på et skadeligt link</li><li>Ændringer af konklusion for URL-adresser identificeres af Microsoft Defender for Office 365</li><li>Brugere tilsidesætter Pengeskab Links-advarselssider (baseret på [organisationens politik Pengeskab Links](set-up-safe-links-policies.md).</li></ul> <p> Du kan finde flere oplysninger om hændelser, der udløser denne besked, [under Konfigurer Pengeskab links-politikker](set-up-safe-links-policies.md).|
|En mail rapporteres af en bruger som malware eller phish|**Information**|Denne besked genereres, når brugere i organisationen rapporterer meddelelser som phishingmail ved hjælp af tilføjelsesprogrammet [Rapportmeddelelse](enable-the-report-message-add-in.md) eller [tilføjelsesprogrammet Rapportphishing](enable-the-report-phish-add-in.md).|
|Mails, der indeholder malware, fjernes efter levering|**Information**|Denne besked genereres, når alle mails, der indeholder malware, leveres til postkasser i organisationen. Hvis denne hændelse forekommer, fjerner Microsoft de inficeret meddelelser fra Exchange Online postkasser ved hjælp [af automatisk tømning (ZAP) uden brug af nul-time](zero-hour-auto-purge.md).|
|Mails, der indeholder phish URL-adresser, fjernes efter levering|**Information**|Denne besked genereres, når alle meddelelser, der indeholder phish, leveres til postkasser i organisationen. Hvis denne hændelse sker, fjerner Microsoft de inficeret meddelelser fra Exchange Online postkasser ved hjælp af [ZAP](zero-hour-auto-purge.md).|
|Mistænkelige e-mail-afsendelsesmønstre registreres|**Mellem**|Denne besked genereres, når en person i organisationen har sendt mistænkelige mails og er i risiko for at blive begrænset fra at sende mails. Beskeden er en tidlig advarsel for adfærd, der kan betyde, at kontoen er kompromitteret, men ikke alvorlig nok til at begrænse brugeren. <p> Selvom det er sjældent, kan en besked, der genereres af denne politik, være en anomali. Det er dog en god ide at [kontrollere, om brugerkontoen er kompromitteret](responding-to-a-compromised-email-account.md).|
|En bruger er begrænset i at kunne sende mails|**Høj**|Denne besked genereres, når en person i organisationen er begrænset i at kunne sende udgående mail. Denne påmindelse giver typisk resultater, når [en mailkonto er kompromitteret](responding-to-a-compromised-email-account.md). <p> Du kan finde flere oplysninger om begrænsede brugere [i Fjern blokerede brugere fra portalen Begrænsede brugere Microsoft 365](removing-user-from-restricted-users-portal-after-spam.md).|

> [!TIP]
> Du kan få mere at vide om beskedpolitikker eller redigere standardindstillingerne under [Beskedpolitikker i Microsoft 365 Overholdelsescenter](../../compliance/alert-policies.md).

## <a name="required-permissions-to-use-air-capabilities"></a>Påkrævede tilladelser til at bruge AIR-funktioner

Tilladelser tildeles gennem bestemte roller, f.eks. dem, der er beskrevet i følgende tabel:

|Opgave|Rolle(er) påkrævet|
|---|---|
|Konfigurer AIR-funktioner|En af følgende roller: <ul><li>Global Administrator</li><li>Sikkerhedsadministrator</li></ul> <p> Disse roller kan tildeles [i Azure Active Directory](/azure/active-directory/roles/permissions-reference) eller i [Microsoft 365 Defender portalen](permissions-microsoft-365-security-center.md).|
|Start en automatiseret undersøgelse <p> --- eller --- <p> Godkend eller afvis anbefalede handlinger|En af følgende roller, der er [tildelt Azure Active Directory](/azure/active-directory/roles/permissions-reference) eller på [Microsoft 365 Defender portalen](permissions-microsoft-365-security-center.md): <ul><li>Global Administrator</li><li>Sikkerhedsadministrator</li><li>Sikkerhedsoperator</li><li>Sikkerhedslæser <br> --- og --- </li><li>Søg og tøm (denne rolle tildeles kun i [Microsoft 365 Defender portalen](permissions-microsoft-365-security-center.md). Det kan være nødvendigt at oprette en **ny rollegruppe &** mailsamarbejde og føje rollen Søg og tøm til den nye rollegruppe.</li></ul>|

## <a name="required-licenses"></a>Påkrævede licenser

[Microsoft Defender for Office 365 plan 2-licenser](defender-for-office-365.md#microsoft-defender-for-office-365-plan-1-and-plan-2) skal tildeles til:

- Sikkerhedsadministratorer (herunder globale administratorer)
- Organisationens sikkerhedsteam (herunder sikkerhedslæsere og personer med rollen **Søg og Tøm** )
- Slutbrugere

## <a name="changes-are-coming-soon-in-your-microsoft-365-defender-portal"></a>Der kommer snart ændringer i din Microsoft 365 Defender-portal

Hvis du allerede bruger AIR-funktioner i Microsoft Defender for Office 365, vil du nu se nogle ændringer i den forbedrede [Microsoft 365 Defender portal](../defender/microsoft-365-defender.md#the-microsoft-365-defender-portal).

:::image type="content" source="../../media/m3d-action-center-unified.png" alt-text="Samlet handlingscenter" lightbox="../../media/m3d-action-center-unified.png":::

Den nye og forbedrede Microsoft 365 Defender samler <https://security.microsoft.com> AIR-funktioner i [Microsoft Defender for Office 365](defender-for-office-365.md) og [Microsoft Defender for Endpoint](../defender-endpoint/automated-investigations.md). Med disse opdateringer og forbedringer kan dit sikkerhedsteam få vist oplysninger om automatiserede undersøgelser og afhjælpningshandlinger på tværs af din mail, dit samarbejdsindhold, dine brugerkonti og enheder, alt sammen på ét sted.

> [!TIP]
> Den nye Microsoft 365 Defender portal erstatter følgende administrationscentre:
>
> - Security & Compliance Center (<https://protection.office.com>)
> - Microsoft 365 Defender (<https://security.microsoft.com>)
>
> Ud over at URL-adressen er ændret, er der et nyt udseende, som er designet til at give dit sikkerhedsteam en mere strømlinet oplevelse med synlighed til flere trusselsregistreringer på ét sted.

### <a name="what-to-expect"></a>Hvad du kan forvente

I følgende tabel vises ændringer og forbedringer af AIR i Microsoft Defender for Office 365.

|Element|Hvad ændres?|
|---|---|
|**Undersøgelsesside**|Den opdaterede **side Undersøgelser er** mere i overensstemmelse med det, du ser [i Microsoft Defender for Endpoint](/windows/security/threat-protection/microsoft-defender-atp/automated-investigations). Du får vist nogle generelle format- og typografiændringer, der er justeret efter den nye, samlede **undersøgelsesvisning** . Undersøgelsesgrafen har f.eks. et mere ensartet format.|
|**Fanen** Brugere|Fanen **Brugere** er nu **fanen Postkasser** . Oplysninger om brugere er angivet på **fanen** Postkasse.|
|**Fanen** Mail|Fanen **Mail** er blevet fjernet. gå til **fanen Enheder for** at få vist en liste over mail- og mailklyngeelementer.|
|**Fanen Enheder**|Fanen **Enheder har** en fane i tabulatortypografi, der omfatter en oversigtsvisning, og muligheden for at filtrere efter enhedstype. Fanen **Enheder indeholder** nu indstillingen **Gå på jagt** ud over indstillingen **Åbn i Stifinder** . Du kan nu bruge enten [Stifinder](threat-explorer.md) [eller avanceret jagt](../defender-endpoint/advanced-hunting-overview.md) på at finde enheder og trusler og filtrere efter resultater.|
|**Fanen** Handlinger|Den opdaterede **fane Handlinger** indeholder nu fanen **Afventende handlinger** og fanen **Handlingsoversigt** . Handlinger kan godkendes (eller afvises) i en siderude, der åbnes, når du vælger en afventende handling.|
|**Fanen** Beviser|En ny **fane med** Beviser viser de vigtigste resultater i forbindelse med handlinger. Handlinger, der er relateret til hvert enkelt beviser, kan godkendes (eller afvises) i en siderude, der åbnes, når du vælger en afventende handling.|
|**Handlingscenter**|Det opdaterede **handlingscenter** (<https://security.microsoft.com/action-center>) samler afventende og fuldførte handlinger på tværs af mail, enheder og identiteter. Du kan få mere at vide i Handlingscenter. Hvis du vil have mere at vide, [skal du se Handlingscenter](../defender/m365d-action-center.md).|
|**Siden Hændelser**|Siden **Hændelser korrelerer** nu flere undersøgelser i fællesskab for at give en bedre konsolideret visning af undersøgelser. ([Få mere at vide om hændelser](../defender/incidents-overview.md)).|

## <a name="next-steps"></a>Næste trin

- [Se detaljer og resultater af en automatisk undersøgelse](air-view-investigation-results.md#view-details-of-an-investigation)
- [Gennemse og godkende afventende handlinger](air-remediation-actions.md)
