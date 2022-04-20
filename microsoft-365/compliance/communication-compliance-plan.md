---
title: Plan for kommunikationsoverholdelse
description: Få mere at vide om planlægning af brug af overholdelse af angivne standarder for kommunikation i din organisation.
keywords: Microsoft 365, Microsoft Purview, overholdelse af angivne standarder, kommunikation
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: Admin
ms.topic: article
f1_keywords:
- ms.o365.cc.SupervisoryReview
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MET150
- MOE150
ms.openlocfilehash: bda0874ef829495b162beae09fde1c4efcb03c85
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/20/2022
ms.locfileid: "64971555"
---
# <a name="plan-for-communication-compliance"></a>Plan for kommunikationsoverholdelse

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Før du går i gang med [overholdelse af angivne standarder for kommunikation](communication-compliance.md) i din organisation, er der vigtige planlægningsaktiviteter og overvejelser, der bør gennemgås af dine it- og overholdelsesadministrationsteams. En grundig forståelse og planlægning af udrulningen på følgende områder hjælper med at sikre, at implementering og brug af funktioner til kommunikation med overholdelse af angivne standarder går problemfrit og er i overensstemmelse med bedste praksis for løsningen.

> [!IMPORTANT]
> Kommunikationsoverholdelse er i øjeblikket tilgængelig i lejere, der hostes i geografiske områder og lande, der understøttes af Azure-tjenesteafhængigheder. Hvis du vil kontrollere, at overholdelse af angivne standarder for kommunikation understøttes for din organisation, skal du se [Tilgængelighed af Azure-afhængighed efter land/område](/troubleshoot/azure/general/dependency-availability-by-country).

## <a name="transitioning-from-supervision-in-office-365"></a>Overgang fra overvågning i Office 365

For organisationer, der bruger overvågningspolitikker i Office 365, skal du straks planlægge at overgå til politikker for overholdelse af kommunikation i Microsoft Purview og have brug for at forstå disse vigtige punkter:

- Tilsynsløsningen i Office 365 er blevet fuldt erstattet af løsningen til kommunikationsoverholdelse i Microsoft Purview. Vi anbefaler, at du opretter nye politikker i overholdelse af angivne standarder for kommunikation, der har de samme indstillinger som eksisterende overvågningspolitikker, for at bruge de nye undersøgelses- og afhjælpningsforbedringer.
- Meddelelser, der er gemt under overvågning i Office 365 politikforekomster, kan ikke flyttes eller deles i kommunikation med overholdelse af angivne standarder.
- For organisationer med begge løsninger, der bruges side om side under overgangsprocessen, skal politikker, der bruges i hver løsning, have entydige politiknavne. Grupper og brugerdefinerede nøgleordsordbøger kan deles mellem løsninger i en overgangsperiode.

Du kan finde flere oplysninger i [Microsoft 365 Roadmap](https://www.microsoft.com/microsoft-365/roadmap) for at få oplysninger om overvågning i Office 365.

## <a name="work-with-stakeholders-in-your-organization"></a>Arbejd med interessenter i din organisation

Identificer de relevante interessenter i din organisation for at samarbejde om at udføre handlinger i forbindelse med beskeder om kommunikation med overholdelse af angivne standarder. Nogle af de anbefalede interessenter, der bør overvejes, herunder i den indledende planlægning og [arbejdsprocessen for overholdelse af angivne standarder for kommunikation](communication-compliance.md#workflow) fra ende til anden, er personer fra følgende områder i organisationen:

- Informationsteknologi
- Overholdelse af regler og standarder
- Beskyttelse af personlige oplysninger
- Sikkerhed
- Personaleafdelingen
- Juridiske

## <a name="plan-for-the-investigation-and-remediation-workflow"></a>Plan for undersøgelses- og afhjælpningsarbejdsprocessen

### <a name="permissions"></a>Tilladelser

Vælg dedikerede interessenter for at overvåge og gennemse beskeder og sager med jævne mellemrum på [Microsoft Purview-overholdelsesportalen](https://compliance.microsoft.com/). Sørg for, at du forstår, hvordan du tildeler brugere og interessenter til forskellige rollegrupper for kommunikation med overholdelse af angivne standarder i din organisation.

> [!IMPORTANT]
> Når du har konfigureret dine rollegrupper, kan det tage op til 30 minutter, før rollegruppens tilladelser gælder for tildelte brugere på tværs af organisationen.

Der er seks rollegrupper, der bruges til at konfigurere de første tilladelser til at administrere funktioner til kommunikation med overholdelse af angivne standarder. Hvis du vil gøre **Overholdelse af kommunikation** tilgængelig som en menuindstilling på Microsoft Purview-overholdelsesportalen og fortsætte med disse konfigurationstrin, skal du være tildelt en af følgende roller eller rollegrupper:

- Azure Active Directory [*rolle som global administrator*](/azure/active-directory/roles/permissions-reference#global-administrator)
- rollen Azure Active Directory [*overholdelsesadministrator*](/azure/active-directory/roles/permissions-reference#compliance-administrator)
- Rollegruppe for Microsoft Purview-overholdelsesportal [*til organisationsadministration*](/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center)
- Rollegruppe for Microsoft [*Purview-overholdelsesportalen Overholdelsesadministrator*](/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center)
- *Rollegruppe for kommunikation med overholdelse af angivne standarder*
- Rollegruppe *for administrator af kommunikationsoverholdelse*

Medlemmer af følgende roller har de samme løsningstilladelser, der er inkluderet i rollegruppen *Administration af kommunikationsoverholdelse* :

- Azure Active Directory *global administrator*
- Azure Active Directory *overholdelsesadministrator*
- Microsoft Purview Compliance Portal *Organisationsadministration*
- Microsoft Purview Compliance Portal *Compliance Administrator*

> [!IMPORTANT]
> Sørg for, at du altid har mindst én bruger i rollegrupperne *Kommunikationsoverholdelse* eller *Administrator af kommunikationsoverholdelse* (afhængigt af den indstilling, du vælger), så konfigurationen af kommunikationsoverholdelse ikke kommer ind i et scenarie med "nul administrator", hvis bestemte brugere forlader din organisation.

Afhængigt af hvordan du vil administrere politikker og beskeder om overholdelse af kommunikation, skal du tildele brugere til bestemte rollegrupper for at administrere forskellige sæt funktioner til kommunikation med overholdelse af angivne standarder. Du har mulighed for at tildele brugere med forskellige overholdelsesansvar til bestemte rollegrupper for at administrere forskellige områder af funktioner til kommunikation med overholdelse af angivne standarder. Du kan også vælge at tildele alle brugerkonti for udpegede administratorer, analytikere, efterforskere og seere til rollegruppen *Kommunikationsoverholdelse* . Brug en enkelt rollegruppe eller flere rollegrupper, så de passer bedst til dine krav til administration af overholdelse.

Vælg mellem disse indstillinger for løsningsrollegruppen, når du konfigurerer og administrerer kommunikation med overholdelse af angivne standarder:

|**Rolle**|**Rolletilladelser**|
|:-----|:-----|
| **Kommunikation med overholdelse af angivne standarder** | Brug denne rollegruppe til at administrere overholdelse af kommunikation for din organisation i en enkelt gruppe. Ved at tilføje alle brugerkonti for udpegede administratorer, analytikere, efterforskere og seere kan du konfigurere tilladelser til kommunikation med overholdelse af angivne standarder i en enkelt gruppe. Denne rollegruppe indeholder alle tilladelser til kommunikation med overholdelse af angivne standarder. Denne konfiguration er den nemmeste måde hurtigt at komme i gang med overholdelse af angivne standarder for kommunikation på, og den er velegnet til organisationer, der ikke har brug for separate tilladelser, der er defineret for separate grupper af brugere. Brugere, der opretter politikker som administrator af kommunikationsoverholdelse, skal have deres postkasse hostet på Exchange Online. |
| **Administrator af kommunikation med overholdelse af angivne standarder** | Brug denne rollegruppe til først at konfigurere overholdelse af kommunikation og senere til at adskille administratorer af kommunikation med overholdelse af angivne standarder i en defineret gruppe. Brugere, der er tildelt denne rollegruppe, kan oprette, læse, opdatere og slette politikker for kommunikation med overholdelse af angivne standarder, globale indstillinger og tildelinger af rollegrupper. Brugere, der er tildelt denne rollegruppe, kan ikke få vist meddelelsesbeskeder. Brugere, der opretter politikker som administrator af kommunikationsoverholdelse, skal have deres postkasse hostet på Exchange Online. |
| **Kommunikationsoverholdelsesanalytiker** | Brug denne gruppe til at tildele tilladelser til brugere, der fungerer som analytikere af kommunikation med overholdelse af angivne standarder. Brugere, der er tildelt til denne rollegruppe, kan få vist politikker, hvor de er tildelt som korrekturlæsere, få vist meddelelsesmetadata (ikke meddelelsesindhold), eskalere til yderligere korrekturlæsere eller sende meddelelser til brugere. Analytikere kan ikke løse ventende beskeder. |
| **Efterforsker af kommunikation med overholdelse af angivne standarder** | Brug denne gruppe til at tildele tilladelser til brugere, der fungerer som undersøgere af kommunikation med overholdelse af angivne standarder. Brugere, der er tildelt denne rollegruppe, kan få vist metadata og indhold, eskalere til yderligere korrekturlæsere, eskalere til en eDiscovery-sag (Premium), sende meddelelser til brugere og løse beskeden. |
| **Meddelelsesoverholdelsesfremviser** | Brug denne gruppe til at tildele tilladelser til brugere, der skal administrere kommunikationsrapporter. Brugere, der er tildelt denne rollegruppe, kan få adgang til alle rapporteringswidgets på startsiden for kommunikation med overholdelse af angivne standarder og kan få vist alle rapporter om kommunikation med overholdelse af angivne standarder. |

### <a name="supervised-users"></a>Overvågede brugere

Før du begynder at bruge overholdelse af kommunikation, skal du afgøre, hvem der har brug for, at deres kommunikation gennemses. I politikken identificerer brugermailadresser enkeltpersoner eller grupper af personer, der skal overvåges. Eksempler på disse grupper er Microsoft 365-grupper, Exchange-baserede distributionslister, Yammer communities og Microsoft Teams kanaler. Du kan også udelukke bestemte brugere eller grupper fra scanning med en bestemt udeladelsesgruppe eller en liste over grupper. Du kan få flere oplysninger om de gruppertyper, der understøttes i politikker for kommunikation med overholdelse af [angivne standarder, under Kom i gang med overholdelse af angivne standarder for kommunikation](communication-compliance-configure.md#step-3-optional-set-up-groups-for-communication-compliance).

> [!IMPORTANT]
> Brugere, der er omfattet af politikker for overholdelse af angivne standarder for kommunikation, skal enten have en Microsoft 365 E5 Overholdelse licens, en Office 365 Enterprise E3-licens med tilføjelsesprogrammet Avanceret overholdelse eller være inkluderet i et Office 365 Enterprise E5-abonnement. Hvis du ikke har en eksisterende Enterprise E5-plan og vil prøve overholdelse af angivne standarder for kommunikation, kan du [tilmelde dig en prøveversion af Office 365 Enterprise E5](https://go.microsoft.com/fwlink/p/?LinkID=698279).

### <a name="reviewers"></a>Korrekturlæsere

Når du opretter en politik for overholdelse af angivne standarder for kommunikation, skal du bestemme, hvem der gennemser meddelelserne fra de overvågede brugere. I politikken identificerer brugermailadresser enkeltpersoner eller grupper af personer, der skal gennemse overvåget kommunikation. Alle korrekturlæsere skal have postkasser, der hostes på Exchange Online, skal tildeles til enten *rollegrupperne Analytiker af kommunikationoverholdelse* eller *Undersøger af kommunikationoverholdelse* og skal tildeles i den politik, de skal undersøge. Når validatorer føjes til en politik, modtager de automatisk en mail, der giver dem besked om tildelingen til politikken og indeholder links til oplysninger om korrekturprocessen.

### <a name="groups-for-supervised-users-and-reviewers"></a>Grupper til overvågede brugere og korrekturlæsere

Hvis du vil forenkle konfigurationen, skal du oprette grupper til personer, der har brug for, at deres kommunikation gennemses, og grupper til personer, der gennemser denne kommunikation. Hvis du bruger grupper, har du muligvis brug for flere. Hvis du f.eks. vil scanne kommunikation mellem to forskellige grupper af personer, eller hvis du vil angive en gruppe, der ikke overvåges. Når du tildeler en distributionsgruppe i politikken, overvåger politikken alle mails fra hver bruger i distributionsgruppen. Når du tildeler en Microsoft 365 gruppe i politikken, overvåger politikken alle mails, der sendes til den pågældende gruppe, og ikke de enkelte mails, der modtages af hvert gruppemedlem.

Tilføjelse af grupper og distributionslister til politikker for overholdelse af kommunikation er en del af de overordnede betingelser og regler, der er angivet, så det maksimale antal grupper og distributionslister, som en politik understøtter, varierer afhængigt af det antal betingelser, der også føjes til politikken. Hver politik skal understøtte ca. 20 grupper eller distributionslister, afhængigt af antallet af yderligere betingelser, der findes i politikken.

Brug følgende diagram til at hjælpe dig med at konfigurere grupper i din organisation til politikker for kommunikation med overholdelse af angivne standarder:

| **Politikmedlem** | **Understøttede grupper** | **Ikke-understøttede grupper** |
|:-----|:-----|:-----|
|Overvågede brugere <br> Udeladte brugere | Distributionsgrupper <br> Microsoft 365-grupper | Dynamiske distributionsgrupper <br> Indlejrede distributionsgrupper <br> Mailaktiverede sikkerhedsgrupper <br> Microsoft 365 grupper med dynamisk medlemskab |
| Korrekturlæsere | Ingen | Distributionsgrupper <br> Dynamiske distributionsgrupper <br> Indlejrede distributionsgrupper <br> Mailaktiverede sikkerhedsgrupper |

### <a name="privacy"></a>Beskyttelse af personlige oplysninger

Det er vigtigt at beskytte beskyttelsen af personlige oplysninger for brugere, der har politikforekomster, og det kan hjælpe med at fremme objektivitet i dataundersøgelser og analysegennemgange for beskeder om kommunikation med overholdelse af angivne standarder. Denne indstilling gælder kun for de brugernavne, der vises i kommunikationsoverholdelsesløsningen. Det påvirker ikke, hvordan navne vises i andre løsninger til overholdelse af angivne standarder eller i Administration.

For brugere med overholdelse af angivne standarder for kommunikation kan du vælge en af følgende indstillinger under **Indstillinger for kommunikation med overholdelse af angivne standarder**:

- **Vis anonymiserede versioner af brugernavne**: Brugernavne anonymiseres for at forhindre brugere i rollegruppen *Kommunikationsoverholdelsesanalytiker i* at se, hvem der er knyttet til politikbeskeder. Brugere i rollegruppen *Communication Compliance Investigator* kan altid se brugernavne og ikke de anonymiserede versioner. En bruger "Grace Taylor" vises f.eks. med et randomiseret pseudonym, f.eks. "AnonIS8-988" på alle områder af oplevelsen med kommunikation med overholdelse af angivne standarder. Hvis du vælger denne indstilling, anonymiseres alle brugere med aktuelle og tidligere politikforekomster og gælder for alle politikker. Brugerprofiloplysninger i beskedoplysningerne om kommunikation med overholdelse af angivne standarder vil ikke være tilgængelige, når denne indstilling vælges. Brugernavne vises dog, når du føjer nye brugere til eksisterende politikker, eller når du tildeler brugere til nye politikker. Hvis du vælger at deaktivere denne indstilling, vises brugernavne for alle brugere, der har aktuelle eller tidligere politikforekomster.
- **Vis ikke anonymiserede versioner af brugernavne**: Brugernavne vises for alle aktuelle og tidligere politikforekomster for beskeder om kommunikation med overholdelse af angivne standarder. Brugerprofiloplysninger (navn, titel, alias og organisation eller afdeling) vises for brugeren for alle beskeder om kommunikation med overholdelse af angivne standarder.

## <a name="plan-for-policies"></a>Planlæg politikker

Det er hurtigt og nemt at oprette politikker for overholdelse af angivne standarder for kommunikation med de [foruddefinerede skabeloner](communication-compliance-policies.md#policy-templates) til upassende indhold, følsomme oplysninger og lovmæssig overholdelse af angivne standarder. Brugerdefinerede politikker for overholdelse af kommunikation giver fleksibiliteten til at registrere og undersøge problemer, der er specifikke for din organisation og dine krav.

Når du planlægger politikker for kommunikation med overholdelse af angivne standarder, skal du overveje følgende områder:

- Overvej at tilføje alle brugere i din organisation som in-scope for dine politikker for kommunikation med overholdelse af angivne standarder. Det er nyttigt i nogle tilfælde at identificere bestemte brugere som omfattet af individuelle politikker, men de fleste organisationer bør inkludere alle brugere i politikker for overholdelse af kommunikation, der er optimeret til chikane eller registrering af diskrimination.
- Konfigurer den procentdel af kommunikationen, der skal gennemses, til 100 % for at sikre, at politikker indhenter alle problemer, der giver anledning til bekymring i forbindelse med kommunikation for din organisation.
- Du kan scanne kommunikation fra [tredjepartskilder](communication-compliance-channels.md#third-party-sources) for data, der er importeret til postkasser i din Microsoft 365 organisation. Hvis du vil inkludere gennemgang af kommunikation på disse platforme, skal du konfigurere en connector til disse tjenester, før meddelelser, der opfylder politikbetingelser, overvåges af kommunikationspolitikken.
- Politikker kan understøtte overvågning af andre sprog end engelsk i brugerdefinerede politikker for overholdelse af kommunikation. Byg en [brugerordbog med nøgleord](communication-compliance-policies.md#custom-keyword-dictionaries) med stødende ord på det sprog, du vælger, eller byg din egen model til maskinel indlæring ved hjælp af [klassificeringsmaskiner, der kan oplæres](classifier-get-started-with.md) i Microsoft 365.
- Alle organisationer har forskellige kommunikationsstandarder og politikbehov. Overvåg for bestemte nøgleord ved hjælp af [betingelser for kommunikation med](communication-compliance-policies.md#conditional-settings) overholdelse af regler og standarder, eller overvåg for bestemte typer oplysninger med [brugerdefinerede følsomme oplysningstyper](create-a-custom-sensitive-information-type.md).

## <a name="creating-a-communication-compliance-policy-walkthrough"></a>Gennemgang af oprettelse af en politik for overholdelse af angivne standarder for kommunikation

Vil du se en detaljeret gennemgang af, hvordan du konfigurerer en ny politik for overholdelse af angivne standarder for kommunikation og afhjælper en besked? Se følgende 15-minutters video for at se en demonstration af, hvordan politikker for kommunikation med overholdelse af angivne standarder kan hjælpe dig med at registrere upassende meddelelser, undersøge potentielle overtrædelser og afhjælpe problemer med overholdelse af angivne standarder.
<br>
<br>

>[!VIDEO https://www.microsoft.com/videoplayer/embed/RWNchy]
<br>

## <a name="ready-to-get-started"></a>Er du klar til at komme i gang?

Hvis du vil konfigurere overholdelse af angivne standarder for kommunikation for din Microsoft 365 organisation, skal du se [Konfigurer overholdelse af angivne standarder for kommunikation](communication-compliance-configure.md) eller se [casestudiet for Contoso](communication-compliance-case-study.md), og hvordan de hurtigt konfigurerede en politik for overholdelse af angivne standarder for kommunikation for at overvåge upassende indhold i Microsoft Teams, Exchange Online og Yammer  Kommunikation.
