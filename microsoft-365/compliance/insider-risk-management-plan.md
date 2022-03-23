---
title: Plan for insider-risikostyring
description: Få mere at vide om, hvordan du planlægger at bruge politikker for insider-risikostyring i din organisation.
keywords: Microsoft 365, insider-risiko, risikostyring, overholdelse af regler og standarder
ms.localizationpriority: medium
ms.service: O365-seccomp
ms.topic: article
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: itpro
ms.collection: m365-security-compliance
ms.custom: admindeeplinkCOMPLIANCE
ms.openlocfilehash: 3a1a2fcebdc097b1402d866a2af59d3caac633d3
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63588228"
---
# <a name="plan-for-insider-risk-management"></a>Plan for insider-risikostyring

Før du går i gang med [insider-risikostyring](insider-risk-management.md) i din organisation, er der vigtige planlægningsaktiviteter og overvejelser, som bør gennemgås af dine informationsteknologi- og overholdelsesstyringsteams. Grundig forståelse og planlægning af installation på følgende områder hjælper med at sikre, at din implementering og brug af insider risk management-funktioner går problemfrit og er justeret i forhold til de bedste fremgangsmåder for løsningen.

Se videoen nedenfor for at få mere at vide om, hvordan arbejdsprocessen for insider-risikostyring kan hjælpe din organisation med at forebygge, registrere og inddæmme risici, mens du prioriterer organisationens værdier, kultur og brugeroplevelse:
<br>
<br>

>[!VIDEO https://www.microsoft.com/videoplayer/embed/RE4OUXB]

## <a name="work-with-stakeholders-in-your-organization"></a>Arbejd med interessenter i organisationen

Identificer de relevante interessenter i organisationen for at samarbejde om at udføre handlinger vedrørende insider-advarsler og -sager. Nogle anbefalede interessenter at overveje at inkludere i den indledende planlægning og den ende-til-ende [insider-arbejdsproces](insider-risk-management.md#workflow) for risikostyring er personer fra følgende områder i organisationen:

- Informationsteknologi
- Overholdelse af regler og standarder
- Beskyttelse af personlige oplysninger
- Sikkerhed
- HR
- Juridiske oplysninger

## <a name="determine-any-regional-compliance-requirements"></a>Fastlægge eventuelle regionale krav til overholdelse af regler og standarder

Forskellige geografiske og organisatoriske områder kan have krav til overholdelse af regler og standarder og beskyttelse af personlige oplysninger, der er forskellige fra andre områder i organisationen. Arbejd med interessenterne på disse områder for at sikre, at de forstår overholdelse og beskyttelse af personlige oplysninger i insider-risikostyring, og hvordan de skal bruges på tværs af forskellige områder i din organisation. I visse situationer kan krav til overholdelse af regler og standarder og beskyttelse af personlige oplysninger kræve politikker, der udpeger eller begrænser visse interessenter fra undersøgelser og sager baseret på en brugers situation eller lovmæssige krav eller politikkrav for området.

Hvis du har krav til, at bestemte interessenter skal deltage i caseundersøgelse, der involverer brugere i bestemte områder, roller eller afdelinger, kan det være en ide at implementere separate (selvom identiske) [insider-politikker](insider-risk-management-policies.md) for risikostyring målrettet de forskellige regioner og populationer. Denne konfiguration gør det nemmere for de rette interessenter at triage og administrere tilfælde, der er relevante for deres roller og områder. Desuden kan du overveje at oprette processer og politikker for områder, hvor korrekturlæsere og korrekturlæsere taler det samme sprog som brugerne for at hjælpe med at strømline eskaleringsprocessen for insider-risikostyringsadvarsler og -sager.

## <a name="plan-for-the-review-and-investigation-workflow"></a>Planlæg arbejdsprocessen for gennemgang og undersøgelse

Afhængigt af hvordan du vil administrere politikker og advarsler for insider-risikostyring, skal du tildele brugere til bestemte rollegrupper for at administrere forskellige sæt insider-funktioner til risikostyring. Du har mulighed for at tildele brugere med forskellige ansvarsområder i forbindelse med overholdelse til bestemte rollegrupper for at administrere forskellige områder af insider-risikostyringsfunktioner. Eller du kan vælge at tildele alle brugerkonti til udvalgte administratorer, analytikere, administratorer og seere til rollegruppen Insider Risk Management. Brug en enkelt rollegruppe eller flere rollegrupper, så de passer bedst til dine krav til overholdelsesstyring.

Du kan vælge mellem disse indstillinger for rollegrupper og løsningshandlinger, når du arbejder med Insider Risk Management:

|**Handlinger**|**Insider Risk Management**|**Insider Risk Management-administrator**|**Analytikere af styring af insider-risiko**|**Undersøgere af styring af insider-risiko**|**Insider-revisorer for risikostyring**|
|:----------|:--------------------------|:--------------------------------|:-----------------------------------|:----------------------------------------|:-----------------------------------|
| Konfigurere politikker og indstillinger | Ja | Ja | Nej | Nej | Nej |
| Få adgang til analyseindsigt | Ja | Ja | Ja | Nej | Nej |
| Access & undersøg beskeder | Ja | Nej | Ja | Ja | Nej |
| Access & undersøge sager | Ja | Nej | Ja | Ja | Nej |
| Få & adgang til at få vist Indholdsstifinder | Ja | Nej | Nej | Ja | Nej |
| Konfigurere meddelelsesskabeloner | Ja | Nej | Ja | Ja | Nej |
| Vise & for eksport af overvågningslogfiler | Ja | Nej | Nej | Nej | Ja |

>[!IMPORTANT]
>Sørg for, at du altid har mindst én bruger i rollegrupperne *Insider Risk Management* eller *Insider Risk Management-administrator* (afhængigt af den indstilling, du vælger), så din insider-risikostyringskonfiguration ikke kommer ind i et scenarie med nul administratorer, hvis bestemte brugere forlader organisationen.

Medlemmer af følgende roller kan tildele brugere rollen som Insider-rollegruppe for risikostyring og have de samme løsningstilladelser i *rollegruppen Insider Risk Management Administration* :

- Azure Active Directory *global administrator*
- Azure Active Directory *over overholdelse af regler og standarder*
- Microsoft 365 Overholdelsescenter *organisationsadministration*
- Microsoft 365 Overholdelsescenter over *overholdelse af regler og standarder*

## <a name="understand-requirements-and-dependencies"></a>Forstå krav og afhængigheder

Afhængigt af hvordan du planlægger at implementere insider-risikostyringspolitikker, skal du have de rette Microsoft 365-licensabonnementer og forstå og planlægge for nogle løsningsfor forudsætninger.

**Licensering:** Insider-risikostyring er tilgængelig som en del af et bredt udvalg Microsoft 365 af licensabonnementer. Du kan få mere at vide [i artiklen Introduktion til Insider Risk Management](insider-risk-management-configure.md#subscriptions-and-licensing) .

> [!IMPORTANT]
> Insider-risikostyring er i øjeblikket tilgængelig i lejere, der er hostet i geografiske områder, og lande, der understøttes af Azure-tjenesteafhængigheder. For at bekræfte at Insider Risk Management understøttes for din organisation, skal du [se Tilgængelighed af Azure-afhængighed efter land/område](/troubleshoot/azure/general/dependency-availability-by-country).

Hvis du ikke har en eksisterende Microsoft 365 Enterprise E5-plan og gerne vil prøve Insider-risikostyring, kan du føje [Microsoft 365](/office365/admin/try-or-buy-microsoft-365) til dit eksisterende abonnement eller tilmelde dig [en](https://www.microsoft.com/microsoft-365/enterprise) prøveversion af Microsoft 365 Enterprise E5.

**Krav til politikskabeloner:** Afhængigt af den politikskabelon, du vælger, er der krav, du skal forstå og planlægge, før du konfigurerer Insider Risk Management i din organisation:

- Når du bruger **datatyveri** ved at fortræde brugerskabelonen, skal du konfigurere en Microsoft 365 HR-forbindelse til med jævne mellemrum at importere oplysninger om brugeres dato for opsigelse og opsigelse i organisationen. Se artiklen [Importér data med HR-forbindelsen](import-hr-data.md) for at få en trinvis vejledning til konfiguration af Microsoft 365 HR-forbindelsen for organisationen.
- Når du bruger **skabeloner til datalækager** , skal du konfigurere mindst én politik til forebyggelse af datatab (DLP) for at definere følsomme oplysninger i organisationen og for at modtage Insider-risikobeskeder om DLP-politikbeskeder med høj alvorsgrad. Se artiklen [Opret, test og finjuster en DLP-politik](create-test-tune-dlp-policy.md) for at få en trinvis vejledning til at konfigurere DLP-politikker for organisationen.
- Når du **bruger skabeloner til brud på** sikkerhedspolitik, skal du aktivere Microsoft Defender for Endpoint for integration af Insider Risk Management i Defender Security Center for at kunne importere sikkerhedsbrudsbeskeder. Du kan finde en trinvis vejledning til at aktivere Defender for Endpoint-integration med insider-risikostyring under Konfigurer avancerede [funktioner i Microsoft Defender til Slutpunkt](/windows/security/threat-protection/microsoft-defender-atp/advanced-features).
- Når du **bruger forskellige brugerskabeloner**, skal du konfigurere en Microsoft 365 HR-forbindelse for med jævne mellemrum at importere oplysninger om ydeevne eller degraderingsstatus for brugere i organisationen. Se artiklen [Importér data med HR-forbindelsen](import-hr-data.md) for at få en trinvis vejledning til konfiguration af Microsoft 365 HR-forbindelsen for organisationen.

## <a name="test-with-a-small-group-of-users-in-a-production-environment"></a>Test med en lille gruppe brugere i et produktionsmiljø

Før du aktiverer løsningen bredt i produktionsmiljøet, kan du overveje at teste politikkerne med et lille sæt produktionsbrugere, mens du udfører den nødvendige overholdelse, beskyttelse af personlige oplysninger og juridiske anmeldelser i organisationen. Evaluering af insider-risikostyring i et testmiljø kræver, at du genererer simulerede brugerhandlinger og andre signaler for at oprette beskeder om triage og tilfælde til behandling. Denne fremgangsmåde er ikke praktisk for de fleste organisationer, så test insider-risikostyring med en lille gruppe brugere i et produktionsmiljø foretrækkes.

Sørg for, at funktionen til anonymisering i politikindstillinger er aktiveret til at anonymisere brugervisningsnavne i insider-administrationskonsollen under denne test for at bevare beskyttelsen af personlige oplysninger i værktøjet. Denne indstilling hjælper med at beskytte beskyttelse af personlige oplysninger for brugere, der har politik match, og kan hjælpe med at fremme objektivitet i anmeldelser af dataundersøgelse og analyse for Insider-risikobeskeder.

Hvis du ikke kan se nogen beskeder, umiddelbart efter du har konfigureret en insider-politik for risikostyring, kan det betyde, at minimumsgrænsen for risici ikke er blevet opfyldt endnu. En god måde at kontrollere, om politikken udløses og fungerer som forventet, er at se, om brugeren er omfattet af politikken på **siden** Brugere.

## <a name="resources-for-stakeholders"></a>Ressourcer til interessenter

Del insider-dokumentation om risikostyring med de interessenter i organisationen, der er inkluderet i din ledelse og afhjælpning af arbejdsprocesser:

- [Opret og administrer insider-risikopolitikker](insider-risk-management-policies.md)
- [Undersøg insider-risikoaktiviteter](insider-risk-management-activities.md)
- [Tag skridtet videre i insider-risikotilfælde](insider-risk-management-cases.md)
- [Gennemse sagsdata med Indholdsstifinder for insider-risiko](insider-risk-management-content-explorer.md)
- [Opret skabeloner til insider-risikomeddelelse](insider-risk-management-notices.md)

## <a name="ready-to-get-started"></a>Er du klar til at gå i gang?

Er du klar til at konfigurere insider-risikostyring for din organisation? Gennemgå følgende artikler:

- [Kom i gang med indstillingerne for Insider Risk Management](insider-risk-management-settings.md) for at konfigurere globale politikindstillinger.
- [Kom i gang med insider-risikostyring](insider-risk-management-configure.md) for at konfigurere forudsætninger, oprette politikker og begynde at modtage beskeder.
