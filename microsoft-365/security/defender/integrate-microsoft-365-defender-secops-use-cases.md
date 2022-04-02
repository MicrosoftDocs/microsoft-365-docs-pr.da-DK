---
title: Trin 5. Udvikle og teste use cases
description: Grundlæggende om udvikling og test af use cases ved integrering Microsoft 365 Defender dine sikkerhedshandlinger.
keywords: hændelser, beskeder, undersøge, korrelation, angreb, enheder, brugere, identiteter, identitet, postkasse, mail, 365, microsoft, m365, hændelsesrespons, cyberangreb, secops, sikkerhedshandlinger, soc
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-m365dsecops
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: 6621ca47356f87edd47a905e4edeb592d9b556ff
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/28/2022
ms.locfileid: "64499083"
---
# <a name="step-5-develop-and-test-use-cases"></a>Trin 5. Udvikle og teste use cases

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Gælder for:**
- Microsoft 365 Defender

De anbefalede metoder til at installere Microsoft 365 Defender i Security Operations Center (SOC) afhænger af SOC-teamets aktuelle sæt af værktøjer, processer og færdigheder. Vedligeholdelse af cyberangreb på tværs af platforme kan være udfordrende på grund af den enorme mængde data, der kommer fra dusin, hvis ikke hundredvis af sikkerhedskilder. 

Sikkerhedsværktøjer er indbyrdes forbundne. Hvis du slår én funktion til i en sikkerhedsteknologi eller ændrer en proces, kan det medføre, at en anden funktion brydes. Af denne grund anbefaler Microsoft, at dit SOC-team formaliserer en metode til at definere og prioritere use cases. Use cases hjælper med at definere krav og testprocesser for SOC-handlinger på tværs af forskellige teams. Der oprettes en metode til registrering af målepunkter for at afgøre, om de rigtige roller og blandinger af opgaver er justeret med det rigtige team med de rette færdigheder. 

## <a name="develop-and-formalize-use-case-process"></a>Udvikle og formalisere case-processen

SOC bør definere en standard og proces på højt niveau for udvikling af brugstilfælde, som vil blive regulerede af SOC-oversigtsteamet. SOC-oversigtsteamet bør arbejde med din virksomhed, it, juridiske afdeling, HR og andre grupper for at prioritere use cases for SOC,som med tiden vil gøre deres vej til SOC-teamets kørselsbøger og playbooks. Prioriteten af use cases er baseret på målsætninger som f.eks. overholdelse af regler og standarder eller beskyttelse af personlige oplysninger.

SOC-oversigtsaktiviteter relateret til udvikling af use case omfatter: 

- Krav
- Behov for personale eller uddannelse
- Softwarelicenser
- Leverandørkontrakter
- Administrer plan
- Vedligeholdelse af registreringsdatabasen for use case
- Vedligeholde/opdatere skabeloner

For at lette processerne for oprettelse af runbook og playbook skal du oprette et beslutningstræ for use case. I figuren nedenfor vises et eksempel.

:::image type="content" source="../../media/integrate-microsoft-365-defender-secops/use-case-decision-process.png" alt-text="Processen for beslutningstagning i use-case" lightbox="../../media/integrate-microsoft-365-defender-secops/use-case-decision-process.png":::

Når en use case-standard på højt niveau er blevet defineret og godkendt, er næste trin at oprette og teste en faktisk use case. I de følgende afsnit bruges scenarier med scanning af antiphishing og trussel og sikkerhedsrisiko som eksempler.

## <a name="use-case-example-1-new-phishing-variant"></a>Use case example 1: Ny phishingvariant

Det første trin til at oprette en use case er at oprette en disposition for arbejdsprocessen ved hjælp af et story board. Her er et eksempel på et story board på højt niveau for en ny meddelelse om phishing-udnyttelse til et Threat Intelligence-team.
 
:::image type="content" source="../../media/integrate-microsoft-365-defender-secops/example-use-case-workflow-storyboard-phishing.png" alt-text="Arbejdsprocessen for en use case for en antiphishing-kampagne" lightbox="../../media/integrate-microsoft-365-defender-secops/example-use-case-workflow-storyboard-phishing.png":::

### <a name="invoke-the-use-case-workflow-for-example-1"></a>Aktivere arbejdsprocessen for use case for eksempel 1

Når story boardet er blevet godkendt, er næste trin at fremkalde arbejdsprocessen for use case-sager. Her er et eksempel på en proces til antiphishing-kampagner. 
 
:::image type="content" source="../../media/integrate-microsoft-365-defender-secops/example-detailed-use-case-workflow-phishing.png" alt-text="En detaljeret arbejdsproces for use case for en antiphishing-kampagne" lightbox="../../media/integrate-microsoft-365-defender-secops/example-detailed-use-case-workflow-phishing.png":::

## <a name="use-case-example-2-threat-and-vulnerability-scanning"></a>Use case example 2: Scanning af trussel og sikkerhedsrisiko

Et andet scenarie, hvor der kunne benyttes en use case, er ved scanning af trusler og sikkerhedsrisiko. I dette eksempel kræver SOC, at trusler og sårbarheder afhjælpes mod aktiver via godkendte processer, der omfatter scanning af aktiver. 

Her er et eksempel på et storyboard på højt niveau til Håndtering af trusler og sikkerhedsrisici af aktiver.
 
:::image type="content" source="../../media/integrate-microsoft-365-defender-secops/example-use-case-workflow-storyboard-tvm.png" alt-text="En arbejdsproces for use-case til Håndtering af trusler og sikkerhedsrisici" lightbox="../../media/integrate-microsoft-365-defender-secops/example-use-case-workflow-storyboard-tvm.png":::

### <a name="invoke-the-use-case-workflow-for-example-2"></a>Aktivere arbejdsprocessen for use case for eksempel 2

Her er en eksempelproces til scanning af trusler og sikkerhedsrisiko.
 
:::image type="content" source="../../media/integrate-microsoft-365-defender-secops/example-detailed-use-case-workflow-tvm.png" alt-text="En detaljeret arbejdsproces for use case til Håndtering af trusler og sikkerhedsrisici" lightbox="../../media/integrate-microsoft-365-defender-secops/example-detailed-use-case-workflow-tvm.png":::
 
### <a name="analyze-the-use-case-output-and-lessons-learned"></a>Analysér output fra use case og indlærte lektioner

Når en use case er blevet godkendt og testet, skal mellemrum mellem dine sikkerhedsteams identificeres sammen med personer, processer og Microsoft 365 Defender teknologierne. Microsoft 365 Defender-teknologier bør analyseres for at afgøre, om de kan opnå de ønskede resultater. Disse kan spores via en tjekliste eller en matrix. 

I eksemplet med antiphishingscenariet kunne SOC-grupperne f.eks. have foretaget opdagelserne i denne tabel.


| SOC-team | Krav | Personer, der opfylder kravet | Proces for at opfylde krav | Relevant teknologi | Mellemrum identificeret | Use case change log | Undtaget (Y/N) |
|:-------|:-----|:-------|:-------|:-------|:-----|:-------|:-------|
| Threat Intelligence and Analytics-team | Datakilder føder trusselsintelligens-motoren korrekt. | Threat Intelligence-analytiker/-tekniker | Etablerede krav til datafeed, trusselsintelligens udløsere fra godkendte kilder | Microsoft Defender for Identity. Microsoft Defender for Endpoint | Threat Intelligence-teamet brugte ikke automationsscript til at sammenkæde Microsoft 365 Defender API med trussels-Intel-søgemaskiner | Føj Microsoft 365 Defender som datakilder til trusselsmotorer <BR> <BR> Opdatere kørselsbog for use case | N |
| Overvågningsteam | Datakilder fødningen af overvågningsdashboardsene korrekt | Niveau 1,2 SOC-analytiker– & vigtige beskeder | Arbejdsproces til rapportering af Security & Compliance Center Secure Score | [Beskeder i Security & Compliance Center](/microsoft-365/security/office-365-security/alerts)  <br><br> Sikker scoreovervågning  | Ingen mekanisme for SOC-analytikere til at rapportere en vellykket registrering af phishingvarianter for at forbedre Secure Score <br><br> [Rapportering i Security & Compliance Center](/microsoft-365/security/office-365-security/reports-and-insights-in-security-and-compliance)| Føj en proces til registrering af secure score-forbedring til rapportering af arbejdsprocesser | N | 
| Teknisk team og SecOps-team | Opdateringer til styring af ændringer foretages i SOC-teamets kørselsbøger | Niveau 2 SOC Engineer | Skift kontrolmeddelelsesprocedure for SOC-teamkørselsbøger | Godkendte ændringer af sikkerhedsenheder | Ændringer af Microsoft 365 Defender forbindelse til SOC-sikkerhedsteknologi kræver godkendelse | Føj Microsoft Defender for Cloud Apps, Defender for Identity, Defender til slutpunkt, Security & Compliance Center til SOC-runbooks | Y |
|||||||||

Desuden kan SOC-grupperne have gjort de opdagelser, der er beskrevet i tabellen nedenfor, i forhold til det Håndtering af trusler og sikkerhedsrisici, der er beskrevet ovenfor:

| SOC-team | Krav | Personer, der opfylder kravet | Proces for at opfylde krav | Relevant teknologi | Mellemrum identificeret | Use case change log | Undtaget (Y/N) |
|:-------|:-----|:-------|:-------|:-------|:-----|:-------|:-------|
| SOC-oversigt | Alle aktiver, der har forbindelse til godkendte netværk, identificeres og kategoriseres | SOC-oversigt, BU-ejere, programejere, ejere af it-aktiver osv. | Centraliseret administration af aktiver for at finde og opliste aktivkategorien og -attributter baseret på risiko. | ServiceNow eller andre aktiver. <br><br>[Microsoft 365 lagerenhed](/security/defender-endpoint/device-discovery) | Der er kun fundet 70 % af aktiverne. Microsoft 365 Defender kun effektiv afhjælpningssporing for kendte aktiver | Modne tjenester for aktivlivscyklus for at Microsoft 365 Defender en dækning på 100 % | N |
| Teknisk & SecOps Teams | Stor påvirkning og kritiske sårbarheder i aktiver afhjælpes i henhold til politikken | SecOps-teknikere, SOC-analytikere: & Compliance, Security Engineering | Defineret proces til kategorisering af høj risiko og kritiske sikkerhedsrisici | [Dashboards til administration af trusler og sikkerhedsrisiko](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt) | Defender til Slutpunkt har identificeret enheder med høj effekt og høj besked uden afhjælpningsplan eller implementering af anbefalet aktivitet fra Microsoft | Tilføj en arbejdsproces for at underrette ejere af aktiver, når afhjælpningsaktivitet er påkrævet inden for 30 dage pr. politik. Implementer et billetsystem for at underrette ejere af aktiver om afhjælpningstrin. | N |
| Overvågning Teams | Status af trussel og sikkerhedsrisiko rapporteres via virksomhedens intranetportal | Niveau 2 SOC-analytiker | Automatisk genererede rapporter fra Microsoft 365 Defender viser afhjælpning af status for aktiver | [Beskeder i Security & Compliance Center](/microsoft-365/security/office-365-security/alerts) <br><br> Sikker scoreovervågning | Der videregives ingen visninger eller dashboardrapporter til aktivejere angående aktivers trussel og sikkerhedsrisiko. | Opret et automatiseringsscript for at udfylde organisationens status for afhjælpning af høj risiko og kritisk aktivsikkerhedsrisiko. | N |
|||||||||

I disse eksempler viser testene, at der er flere huller i SOC-teamets krav, der blev fastlagt som grundlinjer for hvert teams ansvarsområder. Tjeklisten for use case kan være så omfattende som nødvendigt for at sikre, at SOC-teamet er forberedt til Microsoft 365 Defender integration med nye eller eksisterende SOC-krav. Da dette vil være en iterativ proces, vil processen til udvikling af use case og indholdet af use case-output naturligt fungere med at opdatere og modne SOC's kørselsbøger med indlærte lektioner.

## <a name="update-production-runbooks-and-playbooks"></a>Opdater produktions-runbooks og -playbooks

Når casetests af use case er blevet løst for alle huller, kan de indlærte lektioner og målepunkter, der indsamles i dem, indarbejdes i dit SOC-teams produktions runbooks (operativsystemer) og playbooks (hændelsessvar og eskaleringsprocedurer). 

Vedligeholdelse af SOC-teamets kørselsbøger og playbooks kan organiseres på mange forskellige måder. Hvert SOC-team kan være ansvarlig for sit eget, eller der kan være en enkelt centraliseret version, som alle teams kan dele i et centralt lager. Administration af kørsels- og opgavebøger for den enkelte organisation er baseret på størrelse, færdigheder, roller og opdeling af pligter. Når en kørselsbog er blevet opdateret, bør opdateringsprocessen for lærebogen følge. 

## <a name="use-a-standard-framework-for-escalation"></a>Brug en standardstruktur til eskalering

Playbooks er de trin, SOC-teams skal følge, når en reel begivenhed indtræffer, baseret på en vellykket integration og test af use case. Det er derfor af afgørende betydning, at SOC følger en formaliseret tilgang til hændelsesrespons, f.eks [. NIST-standarden](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-61r2.pdf) for hændelsesrespons, der er blevet en af de førende branchestandarder for hændelsesrespons.

Svarprocessen for NIST-hændelser i fire trin omfatter fire faser:

1.  Forberedelse
2.  Registrering og analyse
3.  Inddæmmelse, ar og genoprettelse
4.  Aktivitet efter hændelse

### <a name="example-tracking-preparation-phase-activity"></a>Eksempel: Sporing af forberedelsesfaseaktivitet

En af de grundlæggende grundsten i en eskaleringsspilbog er at sikre, at der er mindre tvetydighed omkring, hvad hvert SOC-team skal gøre før, under og efter en begivenhed eller hændelse. Derfor er det god praksis at opliste trinvise instruktioner. 

Forberedelsesfasen kan f.eks. omfatte en hvis-derefter- eller XoR-matrix af opgaver. I forbindelse med det nye eksempel på brug af phishingvarianter kunne en sådan matrix se således ud:

| Hvorfor garanteres eskalering? | Næste trin |
|:-------|:-----|
| Besked i SOC-overvågning klassificeret **som** kritisk udløst > **500/time** | Gå til Lærebog A, sektion 2, aktivitet 5 (med et link til sektionen om lærebogen) |
| eCommerce rapporterede potentielle DDoS-angreb | Invoke Playbook B-Section C, Activity 19 (with a link to the playbook section) |
| Ledelsen har rapporteret en mistænkelig mail som forsøg på phishing | Gå til Lærebog 5, sektion 2, aktivitet 5 (med et link til sektionen om lærebogen) |
|||

Når fasen Forberedelse er udført, skal organisationer fremkalde de resterende faser som beskrevet af NIST:

- Registrering og analyse
- Inddæmmelse, ar og genoprettelse
- Aktivitet efter hændelse 

## <a name="next-step"></a>Næste trin

[Trin 6. Identificer SOC-vedligeholdelsesopgaver](integrate-microsoft-365-defender-secops-tasks.md)
