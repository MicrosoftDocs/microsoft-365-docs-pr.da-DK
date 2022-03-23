---
title: Plan for overholdelse af kommunikationsreglerne
description: Få mere at vide om planlægning af brug af kommunikationsoverholdelse i din organisation.
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
ms.openlocfilehash: 77579a97016d37dd9bfc12f88db62200fbca0ccc
ms.sourcegitcommit: 559df2c86a7822463ce0597140537bab260c746a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/15/2022
ms.locfileid: "63590260"
---
# <a name="plan-for-communication-compliance"></a>Plan for overholdelse af kommunikationsreglerne

Før du går [i gang med](communication-compliance.md) at overholde kommunikationsreglerne i din organisation, er der vigtige planlægningsaktiviteter og overvejelser, som bør gennemgås af dine informationsteknologi- og overholdelsesstyringsteams. Grundig forståelse og planlægning af installation på følgende områder hjælper med at sikre, at din implementering og brug af funktioner til overholdelse af kommunikation går problemfrit og er justeret med de bedste fremgangsmåder for løsningen.

> [!IMPORTANT]
> Kommunikationsoverholdelse er i øjeblikket tilgængelig i lejere, der er hostet i geografiske områder og lande, der understøttes af Azure-tjenesteafhængigheder. Hvis du vil kontrollere, at kommunikationsoverholdelse understøttes for din organisation, skal du [se Tilgængelighed af Azure-afhængighed efter land/område](/troubleshoot/azure/general/dependency-availability-by-country).

## <a name="transitioning-from-supervision-in-office-365"></a>Overgang fra overvågning i Office 365

For organisationer, der bruger overvågningspolitikker i Office 365, bør du straks planlægge overgangen til politikker for overholdelse af kommunikation i Microsoft 365 og have brug for at forstå disse vigtige punkter:

- Overvågningsløsningen i Office 365 er helt erstattet af løsningen til overholdelse af kommunikation på Microsoft 365. Vi anbefaler, at du opretter nye politikker for overholdelse af kommunikation med de samme indstillinger som eksisterende overvågningspolitikker for at bruge den nye undersøgelse og afhjælpningsforbedringer.
- Meddelelser, der er gemt under overvågning Office 365 at politikoverensstemmelser ikke kan flyttes eller deles i overholdelse af kommunikationsreglerne Microsoft 365.
- For organisationer med begge løsninger, der bruges side om side under overgangsprocessen, skal de politikker, der bruges i hver løsning, have entydige politiknavne. Grupper og brugerordbøger til nøgleord kan deles mellem løsninger i løbet af en overgangsperiode.

Du kan finde oplysninger om tilbagetrækning til overvågning Office 365 i [oversigten Microsoft 365 for at](https://www.microsoft.com/microsoft-365/roadmap) få mere at vide.

## <a name="work-with-stakeholders-in-your-organization"></a>Arbejd med interessenter i organisationen

Identificer de relevante interessenter i organisationen for at samarbejde om at udføre handlinger vedrørende beskeder om kommunikationsoverholdelse. Nogle anbefalede interessenter at overveje at medtage i den indledende planlægning og den slutpunkt-til-ende-arbejdsproces for overholdelse af regler og standarder er personer fra følgende områder i organisationen:[](communication-compliance.md#workflow)

- Informationsteknologi
- Overholdelse af regler og standarder
- Beskyttelse af personlige oplysninger
- Sikkerhed
- HR
- Juridiske oplysninger

## <a name="plan-for-the-investigation-and-remediation-workflow"></a>Planlæg undersøgelses- og afhjælpningsarbejdsprocessen

### <a name="permissions"></a>Tilladelser

Vælg dedikerede interessenter for at overvåge og gennemgå beskeder og sager med jævne mellemrum i [Microsoft 365 Overholdelsescenter](https://compliance.microsoft.com/). Sørg for, at du forstår, hvordan du vil tildele brugere og interessenter forskellige rollegrupper i organisationen til overholdelse af regler og standarder.

> [!IMPORTANT]
> Når du har konfigureret dine rollegrupper, kan det tage op til 30 minutter, før tilladelserne for rollegruppen gælder for tildelte brugere i hele organisationen.

Der bruges seks rollegrupper til at konfigurere starttilladelser til at administrere funktioner til overholdelse af regler og standarder i kommunikation. Hvis overholdelse **af** kommunikationsindstillinger skal gøres tilgængelig som en menuindstilling i Microsoft 365 Overholdelsescenter og fortsætte med disse konfigurationstrin, skal du være tildelt en af følgende roller eller rollegrupper:

- Azure Active Directory [*global administratorrolle*](/azure/active-directory/roles/permissions-reference#global-administrator)
- Azure Active Directory [*rolle som overholdelsesadministrator*](/azure/active-directory/roles/permissions-reference#compliance-administrator)
- Microsoft 365 Overholdelsescenter [*rollegruppe for*](/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center) organisationsadministration
- Microsoft 365 Overholdelsescenter af [*rollegruppen Overholdelsesadministrator*](/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center)
- *Rollegruppen Kommunikationsoverholdelse*
- *Rollegruppen Kommunikationsoverholdelsesadministrator*

Medlemmer af følgende roller har de samme løsningstilladelser, der følger med *rollegruppen* Kommunikationsoverholdelsesadministrator:

- Azure Active Directory *global administrator*
- Azure Active Directory *over overholdelse af regler og standarder*
- Microsoft 365 Overholdelsescenter *organisationsadministration*
- Microsoft 365 Overholdelsescenter over *overholdelse af regler og standarder*

> [!IMPORTANT]
> Sørg for, at du altid har mindst én bruger i  rollegrupperne  Kommunikationsoverholdelse eller Kommunikationsoverholdelse (afhængigt af den indstilling, du vælger), så din konfiguration af kommunikationsoverholdelse ikke kommer ind i et scenarie med "nul administrator", hvis bestemte brugere forlader organisationen.

Afhængigt af hvordan du ønsker at administrere politikker og beskeder om overholdelse af kommunikation, skal du tildele brugere til bestemte rollegrupper for at administrere forskellige sæt af funktioner til overholdelse af regler og standarder i kommunikation. Du har mulighed for at tildele brugere med forskellige ansvarsområder i forbindelse med overholdelse til bestemte rollegrupper for at administrere forskellige områder af funktioner til overholdelse af regler og standarder i kommunikation. Eller du kan vælge at tildele alle brugerkonti til udvalgte administratorer, analytikere, administratorer og seere til rollegruppen *Kommunikationsoverholdelse* . Brug en enkelt rollegruppe eller flere rollegrupper, så de passer bedst til dine krav til overholdelsesstyring.

Vælg mellem disse gruppeindstillinger for løsningsroller, når du konfigurerer og administrerer kommunikationsoverholdelse:

|**Rolle**|**Rolletilladelser**|
|:-----|:-----|
| **Kommunikationsoverholdelse** | Brug denne rollegruppe til at administrere overholdelse af kommunikationsreglerne for din organisation i en enkelt gruppe. Ved at tilføje alle brugerkonti for udvalgte administratorer, analytikere, seere og seere kan du konfigurere tilladelser til overholdelse af kommunikation i en enkelt gruppe. Denne rollegruppe indeholder alle kommunikationsoverholdelsestilladelsesroller. Denne konfiguration er den nemmeste måde til hurtigt at komme i gang med overholdelse af regler og standarder i kommunikation, og den passer godt til organisationer, der ikke har brug for separate tilladelser defineret til separate grupper af brugere. Brugere, der opretter politikker som kommunikationsadministrator for overholdelse af regler og standarder, skal have deres postkasse hostet Exchange Online. |
| **Administrator for overholdelse af kommunikation** | Brug denne rollegruppe til i første omgang at konfigurere kommunikationsoverholdelse og senere for at adskille administratorer af kommunikationsoverholdelse i en defineret gruppe. Brugere, der er tildelt denne rollegruppe, kan oprette, læse, opdatere og slette politikker for overholdelse af kommunikation, globale indstillinger og rollegruppetildelinger. Brugere, der er tildelt denne rollegruppe, kan ikke få vist beskeder om meddelelser. Brugere, der opretter politikker som kommunikationsadministrator for overholdelse af regler og standarder, skal have deres postkasse hostet Exchange Online. |
| **Kommunikationsoverholdelsesanalytiker** | Brug denne gruppe til at tildele tilladelser til brugere, der fungerer som analytikere for kommunikationsoverholdelse. Brugere, der er tildelt denne rollegruppe, kan få vist politikker, hvor de er tildelt som korrekturlæsere, få vist metadata for meddelelser (ikke meddelelsesindhold), eskalere til flere korrekturlæsere eller sende meddelelser til brugere. Analytikere kan ikke løse ventende beskeder. |
| **Communication Compliance Investigator** | Brug denne gruppe til at tildele tilladelser til brugere, der skal fungere som kompatibilitetsgrupper for kommunikation. Brugere, der er tildelt denne rollegruppe, kan få vist metadata og indhold for meddelelser, eskalere til flere korrekturlæsere, eskalere til Advanced eDiscovery-sag, sende meddelelser til brugere og løse beskeden. |
| **Fremviser til overholdelse af kommunikation** | Brug denne gruppe til at tildele tilladelser til brugere, der skal administrere kommunikationsrapporter. Brugere, der er tildelt denne rollegruppe, kan få adgang til alle rapporteringswidgets på startsiden til overholdelse af kommunikation og kan få vist alle rapporter om overholdelse af kommunikation. |

### <a name="supervised-users"></a>Overvågede brugere

Før du går i gang med at bruge kommunikationsoverholdelse, skal du bestemme, hvem der skal have gennemgået deres kommunikation. I politikken identificerer brugermailadresser personer eller grupper af personer, der skal overvåges. Nogle eksempler på disse grupper er Microsoft 365 grupper, Exchange-baserede distributionslister, Yammer-communities og Microsoft Teams-kanaler. Du kan også udelukke bestemte brugere eller grupper fra scanning med en bestemt udelukkelsesgruppe eller en liste over grupper. Du kan finde flere oplysninger om gruppetyper, der understøttes i politikker for overholdelse af kommunikation, [i Introduktion til overholdelse af regler og standarder i kommunikation](communication-compliance-configure.md#step-3-optional-set-up-groups-for-communication-compliance).

> [!IMPORTANT]
> Brugere, der er dækket af politikker for overholdelse af kommunikation, skal have enten en Microsoft 365 E5 Overholdelse-licens, en Office 365 Enterprise E3-licens med tilføjelsesprogrammet Avanceret overholdelse eller være inkluderet i et Office 365 Enterprise E5-abonnement. Hvis du ikke har en eksisterende Enterprise E5-plan og vil prøve overholdelse af regler og standarder i kommunikation, kan du tilmelde dig [en prøveversion Office 365 Enterprise E5](https://go.microsoft.com/fwlink/p/?LinkID=698279).

### <a name="reviewers"></a>Korrekturlæsere

Når du opretter en politik for overholdelse af kommunikationsreglerne, skal du bestemme, hvem der gennemser meddelelser fra overvågede brugere. I politikken identificerer brugermailadresser enkeltpersoner eller grupper af personer, der skal gennemgå overvåget kommunikation. Alle korrekturlæsere skal have postkasser, der er hostet på Exchange Online, skal være tildelt rollegrupperne  Kommunikationsoverholdelsesanalytiker eller Compliance For Kommunikation og skal være tildelt i den politik, de skal bruge for at undersøge det. Når korrekturlæsere føjes til en politik, modtager de automatisk en mail, der giver dem besked om tildelingen af politikken og indeholder links til oplysninger om gennemsynsprocessen.

### <a name="groups-for-supervised-users-and-reviewers"></a>Grupper til overvågede brugere og korrekturlæsere

Du kan forenkle din konfiguration ved at oprette grupper til de personer, der skal have gennemgået deres kommunikation, og grupper til de personer, der gennemser kommunikationen. Hvis du bruger grupper, skal du muligvis bruge flere. Hvis du f.eks. vil scanne kommunikation mellem to forskellige grupper af personer, eller hvis du vil angive en gruppe, der ikke overvåges. Når du tildeler en distributionsgruppe i politikken, overvåger politikken alle mails fra hver bruger i distributionsgruppen. Når du tildeler en Microsoft 365 gruppe i politikken, overvåger politikken alle mails, der sendes til den pågældende gruppe, og ikke de individuelle mails, der modtages af hvert gruppemedlem.

Tilføjelse af grupper og distributionslister til politikker for overholdelse af kommunikation er en del af de overordnede betingelser og regelsæt, så det maksimale antal grupper og distributionslister, som en politik understøtter, varierer afhængigt af antallet af betingelser, der også er føjet til politikken. Hver politik bør understøtte ca. 20 grupper eller distributionslister, afhængigt af antallet af yderligere betingelser i politikken.

Brug følgende diagram som en hjælp til at konfigurere grupper i din organisation til politikker for overholdelse af kommunikation:

| **Medlem af politik** | **Understøttede grupper** | **Ikke-understøttede grupper** |
|:-----|:-----|:-----|
|Overvågede brugere <br> Ekskluderede brugere | Distributionsgrupper <br> Microsoft 365 grupper | Dynamiske distributionsgrupper <br> Indlejrede distributionsgrupper <br> Mailaktiverede sikkerhedsgrupper <br> Microsoft 365 grupper med dynamisk medlemskab |
| Korrekturlæsere | Ingen | Distributionsgrupper <br> Dynamiske distributionsgrupper <br> Indlejrede distributionsgrupper <br> Mailaktiverede sikkerhedsgrupper |

### <a name="privacy"></a>Beskyttelse af personlige oplysninger

Beskyttelse af personlige oplysninger for brugere, der har politikoverensstemmelse, er vigtigt og kan hjælpe med at fremme objektivitet i forbindelse med vurdering og analyse af anmeldelser af kommunikationsoverholdelse. Denne indstilling gælder kun for brugernavne, der vises kommunikationsoverholdelsesløsningen. Det påvirker ikke, hvordan navne vises i andre løsninger til overholdelse af regler og standarder eller Administration.

Brugere med et match til kommunikationsoverholdelse kan vælge en af følgende indstillinger i Indstillinger for overholdelse **af kommunikation**:

- **Vis anonymiserede versioner af brugernavne**: Brugernavne er anonymiserede for at forhindre brugere  i rollegruppen i kommunikationsoverholdelsesanalytikere i at se, hvem der er knyttet til politikbeskeder. Brugere i *rollegruppen Communication Compliance Compliance* vil altid få vist brugernavne, ikke de anonymiserede versioner. Eksempelvis blev en brugers 'Grace Taylor' vist med et randomiseret pseudonym, f.eks. 'AnonIS8-988' på alle områder af kommunikationsoverholdelsesoplevelsen. Hvis du vælger denne indstilling, anonymiseres alle brugere med aktuelle og tidligere politikoverensstemmelser og gælder for alle politikker. Oplysninger om brugerprofiler i oplysningerne om overholdelse af regler og standarder i kommunikation er ikke tilgængelige, når denne indstilling vælges. Brugernavne vises dog, når du føjer nye brugere til eksisterende politikker, eller når du tildeler brugere nye politikker. Hvis du vælger at deaktivere denne indstilling, vises brugernavne for alle brugere, der har aktuelle eller tidligere politik match.
- **Vis ikke anonymiserede versioner af brugernavne: Brugernavne** vises for alle aktuelle og tidligere politikoverensstemmelser for beskeder om overholdelse af kommunikation. Brugerprofiloplysninger (navn, titel, alias og organisation eller afdeling) vises for brugeren for alle beskeder om kommunikationsoverholdelse.

## <a name="plan-for-policies"></a>Planlæg politikker

Det er hurtigt og nemt at oprette politikker for overholdelse af regler og standarder med de foruddefinerede [skabeloner til](communication-compliance-policies.md#policy-templates) upassende indhold, følsomme oplysninger og overholdelse af lovgivning. Brugerdefinerede politikker for overholdelse af regler og standarder giver fleksibilitet til at registrere og undersøge problemer, der er specifikke for din organisation og dine krav.

Når du planlægger politikker for overholdelse af kommunikation, skal du overveje følgende områder:

- Overvej at tilføje alle brugere i organisationen som en del af din politik for overholdelse af regler og standarder i kommunikation. Det er i nogle tilfælde nyttigt at identificere bestemte brugere som in-scope for individuelle politikker, men de fleste organisationer bør medtage alle brugere i politikker for overholdelse af kommunikation, som er optimeret til registrering af chikane eller trusler.
- Konfigurer procentdelen af kommunikation, så den gennemgås ved 100 %, for at sikre, at politikker fanger alle problemer, der er vigtige for din organisations kommunikation.
- Du kan scanne kommunikation fra [tredjepartskilder](communication-compliance-channels.md#third-party-sources) for data, der er importeret i postkasser i Microsoft 365 organisation. For at medtage gennemgang af kommunikation på disse platforme skal du konfigurere en forbindelse til disse tjenester, før meddelelser, som opfylder politikbetingelserne, overvåges af kommunikationspolitikken.
- Politikker kan understøtte andre sprog til overvågning end engelsk i brugerdefinerede politikker for overholdelse af regler og standarder i kommunikation. [Opbyg en brugerordbog](communication-compliance-policies.md#custom-keyword-dictionaries) med stødende ord på det sprog, du ønsker, eller opbyg din [](classifier-get-started-with.md) egen maskinlæringsmodel ved hjælp af trænbare klassificeringer i Microsoft 365.
- Alle organisationer har forskellige kommunikationsstandarder og politikbehov. Overvåg for specifikke nøgleord ved hjælp af [politikbetingelser for kommunikation](communication-compliance-policies.md#conditional-settings) eller overvåg for bestemte typer oplysninger med [brugerdefinerede typer af følsomme oplysninger](create-a-custom-sensitive-information-type.md).

## <a name="creating-a-communication-compliance-policy-walkthrough"></a>Opret en gennemgang af en politik for overholdelse af kommunikation

Vil du se en dybdegående gennemgang af, hvordan du konfigurerer en ny politik for overholdelse af kommunikation og afhjælper en besked? Se følgende 15-minutters video for at se en demonstration af, hvordan politikker for overholdelse af kommunikation kan hjælpe dig med at registrere upassende meddelelser, undersøge potentielle overtrædelser og løse problemer med overholdelse.
<br>
<br>

>[!VIDEO https://www.microsoft.com/videoplayer/embed/RWNchy]
<br>

## <a name="ready-to-get-started"></a>Er du klar til at gå i gang?

Se Konfigurer kommunikationsoverholdelse for [Microsoft 365 for](communication-compliance-configure.md) at konfigurere kommunikationsoverholdelse for din Microsoft 365-organisation, eller se casestudiet [om Contoso](communication-compliance-case-study.md), og hvordan de hurtigt konfigurerede en politik for overholdelse af kommunikation til at overvåge upassende indhold i Microsoft Teams. Exchange Online og Yammer kommunikation.
