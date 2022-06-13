---
title: Trin 5. Udvikl og test use cases
description: Det grundlæggende ved udvikling og test af use cases, når du integrerer Microsoft 365 Defender i dine sikkerhedshandlinger.
keywords: hændelser, beskeder, undersøge, korrelation, angreb, enheder, brugere, identitet, identitet, postkasse, mail, 365, microsoft, m365, svar på hændelser, cyberangreb, secops, sikkerhedshandlinger, soc
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
ms.openlocfilehash: a039239545a5442592fe1a07f840cf75bebb0eca
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/10/2022
ms.locfileid: "66012940"
---
# <a name="step-5-develop-and-test-use-cases"></a>Trin 5. Udvikl og test use cases

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Gælder for:**
- Microsoft 365 Defender

De anbefalede metoder til udrulning af Microsoft 365 Defender i dit SOC (Security Operations Center) afhænger af SOC-teamets aktuelle sæt værktøjer, processer og færdigheder. Det kan være en udfordring at opretholde cyberhygiejne på tværs af platforme på grund af den enorme mængde data, der kommer fra snesevis, hvis ikke hundredvis af sikkerhedskilder.

Sikkerhedsværktøjer er indbyrdes forbundne. Hvis du aktiverer en funktion i en sikkerhedsteknologi eller ændrer en proces, kan det også ødelægge en anden funktion. Derfor anbefaler Microsoft, at dit SOC-team formaliserer en metode til definition og prioritering af use cases. Use cases hjælper med at definere krav og testprocesser for SOC-handlinger på tværs af forskellige teams. Den opretter en metode til registrering af målepunkter for at bestemme, om de rigtige roller og en blanding af opgaver er justeret i forhold til det rigtige team med de rette færdigheder.

## <a name="develop-and-formalize-use-case-process"></a>Udvikl og formaliser processen for use case

SOC bør definere en standard og en proces på højt niveau for udvikling af use cases, som skal reguleres af SOC-tilsynsteamet. SOC Tilsynsteamet bør arbejde med din virksomhed, it, juridiske, HR og andre grupper for at prioritere use cases for SOC, der i sidste ende vil gøre deres vej ind i SOC-teamets runbooks og playbooks. Prioriteten af use cases er baseret på målsætninger, f.eks. overholdelse af angivne standarder eller beskyttelse af personlige oplysninger.

SOC Tilsynsaktiviteter i forbindelse med udvikling af use case omfatter:

- Krav
- Personale- eller uddannelsesbehov
- Softwarelicenser
- Leverandørkontr.
- Administration af plan
- Vedligeholdelse af use case-registreringsdatabasen
- Vedligeholdelse/opdatering af skabeloner

For at facilitere processerne for oprettelse af runbook og playbook skal du oprette et beslutningstræ for use case. Dette tal viser et eksempel.

:::image type="content" source="../../media/integrate-microsoft-365-defender-secops/use-case-decision-process.png" alt-text="Beslutningsprocessen for use case" lightbox="../../media/integrate-microsoft-365-defender-secops/use-case-decision-process.png":::

Når der er defineret og godkendt en standard for use case på højt niveau, er det næste trin at oprette og teste en faktisk use case. I følgende afsnit bruges scenarier til anti-phishing og trussels- og sårbarhedsscanning som eksempler.

## <a name="use-case-example-1-new-phishing-variant"></a>Eksempel på brugseksempel 1: Ny phishing-variant

Det første trin i oprettelsen af en use case er at skitsere arbejdsprocessen ved hjælp af et historieforum. Her er et eksempel på et historieforum på højt niveau for en ny meddelelse om phishing-udnyttelse til et Threat Intelligence-team.

:::image type="content" source="../../media/integrate-microsoft-365-defender-secops/example-use-case-workflow-storyboard-phishing.png" alt-text="Arbejdsprocessen for en use case til en anti-phishing-kampagne" lightbox="../../media/integrate-microsoft-365-defender-secops/example-use-case-workflow-storyboard-phishing.png":::

### <a name="invoke-the-use-case-workflow-for-example-1"></a>Aktivér arbejdsprocessen for use case, f.eks. 1

Når tekstenhedstavlen er blevet godkendt, er det næste trin at aktivere arbejdsprocessen for use case. Her er et eksempel på en proces til anti-phishing-kampagne.

:::image type="content" source="../../media/integrate-microsoft-365-defender-secops/example-detailed-use-case-workflow-phishing.png" alt-text="En detaljeret arbejdsproces til brug af en anti-phishing-kampagne" lightbox="../../media/integrate-microsoft-365-defender-secops/example-detailed-use-case-workflow-phishing.png":::

## <a name="use-case-example-2-threat-and-vulnerability-scanning"></a>Eksempel 2 i brugseksempel: Scanning af trusler og sårbarheder

Et andet scenarie, hvor der kan bruges en use case, er til scanning af trusler og sårbarheder. I dette eksempel kræver SOC, at trusler og sårbarheder afhjælpes mod aktiver via godkendte processer, der omfatter scanning af aktiver.

Her er et eksempel på et storyboard på højt niveau for Håndtering af trusler og sikkerhedsrisici af aktiver.

:::image type="content" source="../../media/integrate-microsoft-365-defender-secops/example-use-case-workflow-storyboard-tvm.png" alt-text="En arbejdsproces for anvendelse af Håndtering af trusler og sikkerhedsrisici" lightbox="../../media/integrate-microsoft-365-defender-secops/example-use-case-workflow-storyboard-tvm.png":::

### <a name="invoke-the-use-case-workflow-for-example-2"></a>Aktivér arbejdsprocessen for use case, f.eks. 2

Her er et eksempel på en proces til scanning af trusler og sårbarheder.

:::image type="content" source="../../media/integrate-microsoft-365-defender-secops/example-detailed-use-case-workflow-tvm.png" alt-text="En detaljeret arbejdsproces for use case for Håndtering af trusler og sikkerhedsrisici" lightbox="../../media/integrate-microsoft-365-defender-secops/example-detailed-use-case-workflow-tvm.png":::

### <a name="analyze-the-use-case-output-and-lessons-learned"></a>Analysér outputtet fra use case og de erfaringer, du har lært

Når en use case er blevet godkendt og testet, skal der identificeres huller blandt dine sikkerhedsteams sammen med personer, processer og de involverede Microsoft 365 Defender teknologier. Microsoft 365 Defender teknologier bør analyseres for at afgøre, om de er i stand til at opnå de ønskede resultater. Disse kan spores via en tjekliste eller en matrix.

I eksemplet med anti-phishing-scenariet kunne SOC-teams f.eks. have gjort opdagelserne i denne tabel.

|SOC-team|Krav|Personer, der skal opfylde kravet|Behandl for at opfylde kravet|Relevant teknologi|Identificeret mellemrum|Ændringslog for use case|Undtaget (Y/N)|
|---|---|---|---|---|---|---|---|
|Threat Intelligence- og Analytics-team|Datakilder fodrer trusselsintelligensmotorerne korrekt.|Threat Intelligence-analytiker/-tekniker|Fastsatte krav til datafeeds, udløser trusselsintelligens fra godkendte kilder|Microsoft Defender for Identity, Microsoft Defender for Endpoint|Threat Intelligence-teamet brugte ikke automatiseringsscript til at linke Microsoft 365 Defender API til trussels-Intel-motorer|Føj Microsoft 365 Defender som datakilder til trusselsprogrammer <p> Opdater kørselsbog for use case|N|
|Overvågningsteam|Datakilder forsyner overvågningsdashboards korrekt|Niveau 1,2 SOC-analytiker – overvågning & beskeder|Arbejdsproces til rapportering af sikker score for Security & Compliance Center|[Beskeder i Security & Compliance Center](/microsoft-365/security/office-365-security/alerts) <p> Overvågning af sikker score|Soc-analytikere kan ikke rapportere en vellykket ny phishing-variantregistrering for at forbedre Sikker score <p> [Få vist mailsikkerhedsrapporter på Microsoft 365 Defender-portalen](/microsoft-365/security/office-365-security/view-email-security-reports)|Føj en proces til sporing af sikker scoreforbedring til arbejdsprocesser i rapportering|N|
|Teknisk team og SecOps-team|Ændringskontrolopdateringer foretages i SOC-teamets runbooks|Niveau 2 SOC-tekniker|Meddelelsesprocedure for ændring af kontrol for SOC-team runbooks|Godkendte ændringer af sikkerhedsenheder|Ændringer af Microsoft 365 Defender forbindelse til SOC-sikkerhedsteknologi kræver godkendelse|Føj Microsoft Defender for Cloud Apps, Defender for Identity, Defender for Endpoint, Security & Compliance Center til SOC-runbooks|Y|

Derudover kunne SOC-holdene have foretaget de opdagelser, der er beskrevet i nedenstående tabel, med hensyn til det Håndtering af trusler og sikkerhedsrisici scenarie, der er beskrevet ovenfor:

|SOC-team|Krav|Personer, der skal opfylde kravet|Behandl for at opfylde kravet|Relevant teknologi|Identificeret mellemrum|Ændringslog for use case|Undtaget (Y/N)|
|---|---|---|---|---|---|---|---|
|SOC-tilsyn|Alle aktiver, der er forbundet til godkendte netværk, identificeres og kategoriseres|SOC Tilsyn, BU ejere, programejere, it-aktiv ejere, osv.|Centraliseret system til administration af aktiver for at finde og vise aktivkategori og -attributter baseret på risiko.|ServiceNow eller andre aktiver. <br><br>[Microsoft 365 enhedsoversigt](/microsoft-365/security/defender-endpoint/device-discovery)|Kun 70% af aktiverne er blevet opdaget. Microsoft 365 Defender afhjælpningssporing, der kun gælder for kendte aktiver|Ældre tjenester til administration af aktivlivscyklus for at sikre, at Microsoft 365 Defender har 100 % dækning|N|
|& SecOps-Teams|Høj indvirkning og kritiske sårbarheder i aktiver afhjælpes i henhold til politikken|SecOps-teknikere, SOC-analytikere: Sårbarhed & overholdelse af angivne standarder, sikkerhedskonstruktion|Defineret proces til kategorisering af høj risiko og kritiske sikkerhedsrisici|[Dashboards til administration af trusler og sårbarheder](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)|Defender for Endpoint har identificeret høj indvirkning, enheder med høj besked uden afhjælpningsplan eller implementering af Microsofts anbefalede aktivitet|Tilføj en arbejdsproces for at give aktivejere besked, når afhjælpningsaktivitet er påkrævet inden for 30 dage pr. politik. Implementer et billetsystem for at give aktivejere besked om afhjælpningstrin.|N|
|Overvågning Teams|Trussels- og sårbarhedsstatus rapporteres via virksomhedens intranetportal|Soc-analytiker på niveau 2|Automatisk genererede rapporter fra Microsoft 365 Defender, der viser status for afhjælpning af aktiver|[Beskeder i Security & Compliance Center](/microsoft-365/security/office-365-security/alerts) <p> Overvågning af sikker score|Der kommunikeres ingen visninger eller dashboardrapporter til aktivejere vedrørende aktivernes trussels- og sårbarhedsstatus.|Opret et automatiseringsscript for at udfylde status for afhjælpning af høj risiko og alvorlig sårbarhed i forbindelse med aktiver i organisationen.|N|

I disse use cases viste testen flere huller i SOC-teamets krav, der blev fastlagt som basispunkter for de enkelte teams ansvarsområder. Brugscasens tjekliste kan være lige så omfattende som nødvendigt for at sikre, at SOC-teamet er forberedt til Microsoft 365 Defender integration med nye eller eksisterende SOC-krav. Da dette vil være en iterativ proces, vil udviklingsprocessen for use case og indholdet af use case-output naturligvis tjene til at opdatere og modne SOC's runbooks med erfaringer.

## <a name="update-production-runbooks-and-playbooks"></a>Opdater produktions runbooks og playbooks

Når use case-test er blevet afhjælpet for alle huller, kan de erfaringer og målepunkter, der indsamles i dem, inkorporeres i dit SOC-teams produktions-runbooks (operativsystemer) og playbooks (hændelsessvar og eskaleringsprocedurer).

Vedligeholdelse af SOC-teamets runbooks og playbooks kan organiseres på mange måder. Hvert SOC-team kan være ansvarlig for deres egne, eller der kan være en enkelt centraliseret version, som alle teams kan dele i et centralt lager. Administration af runbooks og strategibøger for de enkelte organisationer er baseret på størrelse, kompetencer, roller og opdeling af opgaver. Når en runbook er blevet opdateret, bør opdateringsprocessen for playbook følge.

## <a name="use-a-standard-framework-for-escalation"></a>Brug en standardstruktur til eskalering

Playbooks er de trin, SOC-holdene skal følge, når der opstår en reel begivenhed, baseret på vellykket integration og test af use case. Det er derfor altafgørende, at SOC følger en formaliseret tilgang til svar på hændelser, f.eks [. NIST Incident Response Standard](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-61r2.pdf) , der er blevet en af de førende branchestandarder for svar på hændelser.

NIST-processen for svar på fire trin indeholder fire faser:

1. Under forberedelse
2. Registrering og analyse
3. Opbevaring, udryddelse og genopretning
4. Aktivitet efter hændelse

### <a name="example-tracking-preparation-phase-activity"></a>Eksempel: Sporing af aktivitet i forberedelsesfasen

Et af de centrale fundamenter for en eskalering playbook er at sikre, at der er lidt flertydighed med hensyn til, hvad hver SOC team formodes at gøre før, under, og efter en begivenhed eller hændelse. Det er derfor god praksis at angive trinvise instruktioner.

Forberedelsesfasen kan f.eks. indeholde en if/then- eller XoR-matrix med opgaver. I tilfælde af brugseksempel på den nye phishing-variant kan en sådan matrix se sådan ud:

|Hvorfor er eskalering berettiget?|Næste trin|
|---|---|
|Advarsel i SOC-overvågning, der er klassificeret som **kritisk** udløst > **500 pr. time**|Gå til Playbook A, Sektion 2, Aktivitet 5 (med et link til playbook-sektionen)|
|eCommerce rapporterede potentielle DDoS-angreb|Aktivér Playbook B-sektion C, Aktivitet 19 (med et link til playbook-sektionen)|
|Direktør rapporterede en mistænkelig e-mail som et forsøg på phishing i spyd|Gå til Playbook 5, Sektion 2, Aktivitet 5 (med et link til playbook-sektionen)|

Når du har kørt forberedelsesfasen, skal organisationer aktivere de resterende faser som beskrevet af NIST:

- Registrering og analyse
- Opbevaring, udryddelse og genopretning
- Aktivitet efter hændelse

## <a name="next-step"></a>Næste trin

[Trin 6. Identificer SOC-vedligeholdelsesopgaver](integrate-microsoft-365-defender-secops-tasks.md)
