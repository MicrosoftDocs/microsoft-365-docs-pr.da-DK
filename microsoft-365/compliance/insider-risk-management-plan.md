---
title: Plan for styring af insider-risiko
description: Få mere at vide om, hvordan du planlægger at bruge politikker for styring af insiderrisiko i din organisation.
keywords: Microsoft 365, Microsoft Purview, insiderrisiko, risikostyring, overholdelse
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
ms.openlocfilehash: 043ee6cac3a7aa7408d949b4455fd90f7f6a66d0
ms.sourcegitcommit: aff1732dfa21e9283b173d8e5ca5bcbeeaaa26d8
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/01/2022
ms.locfileid: "65810916"
---
# <a name="plan-for-insider-risk-management"></a>Plan for styring af insider-risiko

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Før du går i gang med [insiderrisikostyring](insider-risk-management.md) i din organisation, er der vigtige planlægningsaktiviteter og overvejelser, der bør gennemgås af dine it- og overholdelsesadministrationsteams. En grundig forståelse af og planlægning af udrulning på følgende områder hjælper med at sikre, at din implementering og brug af insiderrisikostyringsfunktionerne går problemfrit og er i overensstemmelse med bedste praksis for løsningen. 

Du kan finde flere oplysninger og en oversigt over planlægningsprocessen for at håndtere risikable aktiviteter i din organisation under [Start af et program til styring af insiderrisiko](https://download.microsoft.com/download/b/2/0/b208282a-2482-4986-ba07-15a9b9286df0/pwc-starting-an-insider-risk-management-program-with-pwc-and-microsoft.pdf).

Se videoen nedenfor for at få mere at vide om, hvordan arbejdsprocessen for styring af insiderrisiko kan hjælpe din organisation med at forhindre, registrere og indeholde risici, samtidig med at du prioriterer organisationens værdier, kultur og brugeroplevelse:
<br>
<br>

>[!VIDEO https://www.microsoft.com/videoplayer/embed/RE4OUXB]

Se [Microsoft Mechanics-videoen](https://www.youtube.com/watch?v=Ynkfu8OF0wQ) om, hvordan styring af insiderrisiko og overholdelse af kommunikation fungerer sammen for at minimere datarisici fra brugere i din organisation.

## <a name="work-with-stakeholders-in-your-organization"></a>Arbejd med interessenter i din organisation

Identificer de relevante interessenter i din organisation for at samarbejde om at udføre handlinger i forbindelse med insiderrisikostyringsbeskeder og -sager. Nogle af de anbefalede interessenter, der skal overvejes, herunder i den indledende planlægning og [arbejdsprocessen for insiderrisikostyring](insider-risk-management.md#workflow) fra ende til anden, er personer fra følgende områder i organisationen:

- Informationsteknologi
- Overholdelse af regler og standarder
- Beskyttelse af personlige oplysninger
- Sikkerhed
- Personaleafdelingen
- Juridiske

## <a name="determine-any-regional-compliance-requirements"></a>Fastlæg eventuelle regionale krav til overholdelse af angivne standarder

Forskellige geografiske og organisatoriske områder kan have krav til overholdelse af angivne standarder og beskyttelse af personlige oplysninger, der er forskellige fra andre områder i organisationen. Arbejd sammen med interessenterne på disse områder for at sikre, at de forstår kontrolelementer for overholdelse af angivne standarder og beskyttelse af personlige oplysninger i styring af insiderrisiko, og hvordan de skal bruges på tværs af forskellige områder i din organisation. I nogle scenarier kan krav til overholdelse af angivne standarder og beskyttelse af personlige oplysninger kræve politikker, der angiver eller begrænser nogle interessenter fra undersøgelser og sager, der er baseret på sagen for en bruger eller lovmæssige eller politiske krav til området.

Hvis du har krav om, at bestemte interessenter skal involveres i sagsundersøgelser, der involverer brugere i visse områder, roller eller afdelinger, kan det være en god idé at implementere separate (også selvom de er identiske) [politikker for styring af insiderrisiko](insider-risk-management-policies.md) , der er målrettet til de forskellige områder og befolkningsgrupper. Denne konfiguration gør det nemmere for de rette interessenter at triagere og administrere sager, der er relevante for deres roller og områder. Derudover kan du overveje at oprette processer og politikker for områder, hvor efterforskere og korrekturlæsere taler det samme sprog som brugerne for at hjælpe med at strømline eskaleringsprocessen for insiderrisikostyringsbeskeder og -sager.

## <a name="plan-for-the-review-and-investigation-workflow"></a>Planlæg arbejdsprocessen for gennemsyn og undersøgelse

Afhængigt af hvordan du vil administrere politikker og beskeder for styring af insiderrisiko, skal du tildele brugere til bestemte rollegrupper for at administrere forskellige sæt insiderrisikostyringsfunktioner. Du har mulighed for at tildele brugere med forskellige overholdelsesansvar til bestemte rollegrupper for at administrere forskellige områder af insiderrisikostyringsfunktioner. Du kan også vælge at tildele alle brugerkonti for udpegede administratorer, analytikere, efterforskere og seere til rollegruppen Insider Risk Management. Brug en enkelt rollegruppe eller flere rollegrupper, så de passer bedst til dine krav til administration af overholdelse.

Du skal vælge mellem disse indstillinger for rollegrupper og løsningshandlinger, når du arbejder med styring af insiderrisiko:

|**Handlinger**|**Styring af insiderrisiko**|**Styring af insiderrisiko Administration**|**Analytikere af styring af insider-risiko**|**Undersøgere af styring af insider-risiko**|**Auditører for styring af insiderrisiko**|
|:----------|:--------------------------|:--------------------------------|:-----------------------------------|:----------------------------------------|:-----------------------------------|
| Konfigurer politikker og indstillinger | Ja | Ja | Nej | Nej | Nej |
| Få adgang til indsigt i analyse | Ja | Ja | Ja | Nej | Nej |
| Få adgang & undersøge beskeder | Ja | Nej | Ja | Ja | Nej |
| Adgang & undersøge sager | Ja | Nej | Ja | Ja | Nej |
| Få adgang & få vist Indholdsoversigt | Ja | Nej | Nej | Ja | Nej |
| Konfigurer meddelelsesskabeloner | Ja | Nej | Ja | Ja | Nej |
| Vis & eksport af overvågningslogge | Ja | Nej | Nej | Nej | Ja |

>[!IMPORTANT]
>Sørg for, at du altid har mindst én bruger i *Insider Risk Management* eller *Insider Risk Management Administration* rollegrupper (afhængigt af den indstilling, du vælger), så konfigurationen af styring af insiderrisiko ikke kommer ind i et scenarie med "nul administrator", hvis bestemte brugere forlader organisationen.

Medlemmer af følgende roller kan tildele brugere til insiderrisikostyringsrollegrupper og have de samme løsningstilladelser som i rollegruppen *Insider Risk Management Administration*:

- Azure Active Directory *global administrator*
- Azure Active Directory *overholdelsesadministrator*
- Microsoft Purview-compliance-portal *organisationsstyring*
- Microsoft Purview-compliance-portal *overholdelsesadministrator*

## <a name="understand-requirements-and-dependencies"></a>Forstå krav og afhængigheder

Afhængigt af hvordan du planlægger at implementere politikker for styring af insiderrisiko, skal du have de korrekte Microsoft 365 licensabonnementer og forstå og planlægge nogle løsningsforudsætninger.

**Licenser:** Insiderrisikostyring er tilgængelig som en del af et stort udvalg af Microsoft 365 licensabonnementer. Du kan finde flere oplysninger i artiklen [Introduktion til styring af insiderrisiko](insider-risk-management-configure.md#subscriptions-and-licensing) .

> [!IMPORTANT]
> Styring af insiderrisiko er i øjeblikket tilgængelig i lejere, der hostes i geografiske områder og lande, der understøttes af Azure-tjenesteafhængigheder. Hvis du vil bekræfte, at styring af insiderrisiko understøttes for din organisation, skal du se [Tilgængelighed af Azure-afhængighed efter land/område](/troubleshoot/azure/general/dependency-availability-by-country).

Hvis du ikke har en eksisterende Microsoft 365 Enterprise E5-plan og vil prøve styring af insiderrisiko, kan du [føje Microsoft 365](/office365/admin/try-or-buy-microsoft-365) til dit eksisterende abonnement eller [tilmelde dig en prøveversion](https://www.microsoft.com/microsoft-365/enterprise) af Microsoft 365 Enterprise E5.

**Krav til politikskabelon:** Afhængigt af den politikskabelon, du vælger, er der krav, som du skal forstå og planlægge for, før du konfigurerer insiderrisikostyring i din organisation:

- Når du bruger skabelonen **Datatyveri ved at forlade brugere**, skal du konfigurere en Microsoft 365 HR-connector til periodisk at importere oplysninger om fratræden og slutdato for brugere i din organisation. Se artiklen [Importér data med HR-connectoren](import-hr-data.md) for at få en trinvis vejledning til, hvordan du konfigurerer Microsoft 365 HR-connectoren for din organisation.
- Når du bruger skabeloner til **datalækage**, skal du konfigurere mindst én DLP-politik (Microsoft Purview Forebyggelse af datatab) for at definere følsomme oplysninger i din organisation og for at modtage insiderrisikobeskeder for DLP-politikbeskeder med høj alvorsgrad. Se artiklen [Opret, test og juster en DLP-politik](create-test-tune-dlp-policy.md) for at få en trinvis vejledning til, hvordan du konfigurerer DLP-politikker for din organisation.
- Når du bruger skabeloner til **overtrædelse af sikkerhedspolitik**, skal du aktivere Microsoft Defender for Endpoint til integration af styring af insiderrisiko i Defender Security Center for at importere beskeder om sikkerhedsovertrædelse. Du kan finde en trinvis vejledning til, hvordan du aktiverer Defender for Endpoint-integration med styring af insiderrisiko, [under Konfigurer avancerede funktioner i Microsoft Defender for Endpoint](/windows/security/threat-protection/microsoft-defender-atp/advanced-features).
- Når du bruger **utilfredse brugerskabeloner**, skal du konfigurere en Microsoft 365 HR-connector for jævnligt at importere oplysninger om ydeevne eller sænkningsstatus for brugere i din organisation. Se artiklen [Importér data med HR-connectoren](import-hr-data.md) for at få en trinvis vejledning til, hvordan du konfigurerer Microsoft 365 HR-connectoren for din organisation.

## <a name="test-with-a-small-group-of-users-in-a-production-environment"></a>Test med en lille gruppe brugere i et produktionsmiljø

Før du aktiverer løsningen bredt i dit produktionsmiljø, kan du overveje at teste politikkerne med et lille sæt produktionsbrugere, mens du udfører den nødvendige overholdelse af angivne standarder, beskyttelse af personlige oplysninger og juridiske korrekturer i din organisation. Evaluering af styring af insiderrisiko i et testmiljø kræver, at du genererer simulerede brugerhandlinger og andre signaler for at oprette beskeder om triage og sager til behandling. Denne fremgangsmåde er ikke praktisk for de fleste organisationer, så det foretrækkes at teste insiderrisikostyring med en lille gruppe brugere i et produktionsmiljø.

Bevar anonymiseringsfunktionen i politikindstillinger, der er aktiveret til anonymisering af visningsnavne for brugere i konsollen til styring af insiderrisiko under denne test for at bevare beskyttelsen af personlige oplysninger i værktøjet. Denne indstilling hjælper med at beskytte beskyttelsen af personlige oplysninger for brugere, der har politikforekomster, og kan hjælpe med at fremme objektivitet i dataundersøgelser og analysegennemgange for insiderrisikobeskeder.

Hvis du ikke kan se nogen beskeder umiddelbart efter konfigurationen af en politik for styring af insiderrisiko, kan det betyde, at grænsen for minimumrisikoen endnu ikke er opfyldt. En god måde at kontrollere, om politikken udløses og fungerer som forventet, er ved at se, om brugeren er omfattet af politikken på siden **Brugere** .

## <a name="resources-for-stakeholders"></a>Ressourcer til interessenter

Del dokumentation til styring af insiderrisiko med de interessenter i din organisation, der er inkluderet i din arbejdsproces for administration og afhjælpning:

- [Opret og administrer politikker for insider-risiko](insider-risk-management-policies.md)
- [Undersøg aktiviteter i insider-risiko](insider-risk-management-activities.md)
- [Udfør handlinger på sager i insider-risiko](insider-risk-management-cases.md)
- [Gennemse sagsdata med indholdsoversigten for insiderrisiko](insider-risk-management-content-explorer.md)
- [Opret skabeloner til meddelelser om insider-risiko](insider-risk-management-notices.md)

## <a name="ready-to-get-started"></a>Er du klar til at komme i gang?

Er du klar til at konfigurere styring af insiderrisiko for din organisation? Gennemse følgende artikler:

- [Kom i gang med indstillinger for styring af insiderrisiko](insider-risk-management-settings.md) for at konfigurere globale politikindstillinger.
- [Kom i gang med styring af insiderrisiko](insider-risk-management-configure.md) for at konfigurere forudsætninger, oprette politikker og begynde at modtage beskeder.
