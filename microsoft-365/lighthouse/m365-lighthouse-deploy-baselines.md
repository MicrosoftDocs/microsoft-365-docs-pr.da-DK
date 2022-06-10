---
title: Udrul Microsoft 365 grundlinjer for fyrtårne
f1.keywords: CSH
ms.author: sharik
author: SKjerland
manager: scotv
ms-reviewer: shcallaw, kywirpel
audience: Admin
ms.topic: article
ms.prod: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- M365-Lighthouse
search.appverid: MET150
description: For MSP'er (Managed Service Providers) ved hjælp af Microsoft 365 Lighthouse kan du få mere at vide om, hvordan du udruller Microsoft 365 grundlinjer for fyrtårne.
ms.openlocfilehash: 17eda86e80b928fb8b4f56b0e5c719574e4741f5
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/10/2022
ms.locfileid: "66012588"
---
# <a name="deploy-microsoft-365-lighthouse-baselines"></a>Udrul Microsoft 365 grundlinjer for fyrtårne

Microsoft 365 Lighthouse giver dig mulighed for at udrulle standardkonfigurationer med administrerede lejere for at sikre brugere, enheder og data i kundelejere. Der er syv [standardkonfigurationer for grundlinjer](m365-lighthouse-deploy-standard-tenant-configurations-overview.md) , der følger med Lighthouse. Ved hjælp af funktionen Lighthouse-udrulningsplan kan du få vist, teste og udrulle sikkerhedskonfigurationer på tværs af alle dine lejere. En udrulningsplan er kun tilgængelig for aktive lejere. Når en lejer er onboardet, kan du sammenligne dine kunders aktuelle konfiguration med den oprindelige standardkonfiguration og foretage de relevante handlinger.

## <a name="before-you-begin"></a>Før du begynder

Sørg for, at du og dine kundelejere opfylder de krav, der er angivet i [Krav til Microsoft 365 Fyrtårn](m365-lighthouse-requirements.md).

## <a name="view-a-deployment-plan"></a>Få vist en udrulningsplan

1. Vælg **Lejere** i navigationsruden til venstre i Lighthouse.

2. Vælg den lejer, du vil have vist, på lejerlisten.

3. Vælg fanen **Udrulningsplan** .

    Fanen Udrulningsplan indeholder en liste, der kan søges i, og som kan eksporteres, over hvert udrulningstrin, der er inkluderet i lejerens installationsplan, og som indeholder følgende oplysninger for hvert installationstrin:

    | Kolonne            | Beskrivelse |
    |-----------------|-------------------------------------------------------------------------------------|
    | Installationstrin | Beskrivelse af installationstrin.                                                     |
    | Status          | Status for installationstrinnet.                                                  |
    | Oprindelige        | Den oprindelige plan, som udrulningstrinnet er afledt fra.                             |
    | Kategori        | Angiver, om installationstrinnet er knyttet til administration af enheder, identitet eller data. |
    | Senest opdateret    | Den dato, hvor udrulningstrinnet sidst blev opdateret.                             |

4. Vælg et installationstrin, du vil gennemse, på listen.

    Siden Installationstrin indeholder følgende oplysninger:

    | Kolonne            | Beskrivelse |
    |-------------------|-----------------------------------------------------------------------------------------------|
    | Oversigt        | En oversigt over formålet med udrulningstrinnet.                                         |
    | Oprindelige       | Den oprindelige plan, som udrulningstrinnet er afledt fra.                             |
    | Kategori       | Angiver, om installationstrinnet er knyttet til administration af enheder, identitet eller data. |
    | Påkrævet SKU   | DE SKU'er, der kræves for at fuldføre udrulningstrinnet.                                      |
    | Brugerpåvirkning    | Effekten af at udrulle trinnet til lejerens brugere.                             |
    | Til dine brugere | Links til ressourcer, som lejerens brugere kan finde nyttige.                             |
    | Næste trin     | Links og vejledning til alle relevante næste trin.                                |

    Udrulningstrinnene omfatter en eller flere processer, der skal fuldføres. Siden Installationstrin indeholder en tabel, der viser hver proces, der er inkluderet i installationstrinnet, og som indeholder følgende oplysninger:

    | Kolonne            | Beskrivelse |
    |-------------------|-------------------------------------------------------------|
    | Procesnavn      | Navnet på processen, som åbner den relevante procesfane, når den vælges.          |
    | Status            | Registreret status for disse indstillingskonfigurationer, der er inkluderet i installationsprocessen.           |
    | Administrationsportal | Den portal, hvor de konfigurationsindstillinger, der er knyttet til processen, administreres. |

## <a name="deploy-a-deployment-step"></a>Installer et installationstrin

1. Vælg **Lejere** på navigationssiden til venstre.

2. Vælg den lejer, du vil have vist, på lejerlisten.

3. Vælg fanen **Udrulningsplan** .

4. På listen Installationstrin skal du vælge et installationstrin, du vil installere.

5. Vælg **Gennemse og installér**.

6. Vælg **Installér** i ruden **Bekræft konfigurationer**.

## <a name="test-a-deployment-step"></a>Test et installationstrin

I forbindelse med udrulningstrin, der installeres via politikker for betinget adgang, kan du sammenligne konfigurationsindstillingerne i installationstrinnet med indstillinger i alle eksisterende politikker uden at installere indstillingerne i lejeren.

1. Vælg **Lejere** på navigationssiden til venstre.

2. Vælg den lejer, du vil have vist, på lejerlisten.

3. Vælg fanen **Udrulningsplan** .

4. På listen Installationstrin skal du vælge et installationstrin, du vil installere.

5. Vælg **Gennemse og installér**.

6. I ruden **Bekræft konfigurationer** skal du vælge **Test disse indstillinger uden en installation**.

7. Vælg **Test**.

Ruden Bekræft konfigurationer lukkes og viser politiksammenligningen. Hver politik i den eksisterende lejer vises i tabellen Registrerede indstillinger.

Tabellen Registrerede indstillinger viser hver eksisterende politik og opsummerer antallet af indstillinger og i parentes antallet af brugere, der har en af følgende statusser:

| Status         | Beskrivelse
|-------------|------------------------------------------------------------|
| Lige indstillinger       | Det samlede antal konfigurationsindstillinger i udrulningsplanen med en tilsvarende værdi i lejeren.      |
| Manglende indstillinger     | Det samlede antal konfigurationsindstillinger i udrulningsplanen, der mangler en værdi i lejeren.      |
| Modstridende indstillinger | Det samlede antal konfigurationsindstillinger i udrulningsplanen, der har en modstridende værdi i lejeren. |

Registrerede indstillinger kan også vises i en modulopbygget tabel, der indeholder oplysninger om konfigurationsindstillinger for hver politik på indstillings- og brugerniveau og kan sorteres efter hver af følgende indstillingsstatusser:

| Status         | Beskrivelse
|-------------|------------------------------------------------------------|
| Indstillinger for total       | Det samlede antal konfigurationsindstillinger, der er inkluderet i installationsprocessen.                        |
| Lige indstillinger       | Det samlede antal konfigurationsindstillinger i udrulningsplanen med en tilsvarende værdi i lejeren.      |
| Manglende indstillinger     | Det samlede antal konfigurationsindstillinger i udrulningsplanen, der mangler en værdi i lejeren.      |
| Modstridende indstillinger | Det samlede antal konfigurationsindstillinger i udrulningsplanen, der har en modstridende værdi i lejeren. |
| Ekstra indstillinger       | Det samlede antal konfigurationsindstillinger med en værdi i lejeren, men ingen værdi i udrulningsplanen.     |

Når denne sammenligning foretages, opdaterer Lighthouse automatisk statussen Registreret status, Udrulningsstatus og Status for installationstrin.

Hvis der ikke er nogen eksisterende politikker at sammenligne, skal du vælge Gennemse og udrul for at åbne ruden Bekræft konfigurationer og vælge Installér.

Hvis der er eksisterende politikker at sammenligne med, kan du enten:

- Rediger konfigurationsindstillingerne for udrulningsplanen, og prøv dem igen i forhold til de eksisterende politikker, vælg **Gennemse og installér** for at åbne ruden Bekræft konfigurationer igen, juster de ønskede konfigurationsindstillinger, markér afkrydsningsfeltet igen, og vælg **Test** nederst i ruden.

- Rediger de eksisterende politikker i den relevante administrationsportal for at afstemme forskellene ved at:
  - Anvender manglende indstillinger
  - Redigering af modstridende indstillinger
  - Sletter eksisterende politikker

For hver udrulningsproces, der kan automatiseres via Lighthouse, er der både en udrulningsstatus og en registreret status.

- Den registrerede status angiver, i hvilket omfang indstillingerne i denne proces er installeret i øjeblikket.
- Installationsstatussen er status for den seneste udrulning til lejeren.

Installationstrinnene kan installeres, uanset hvilke eksisterende politikker der findes, men anses ikke for at være fuldført, før der ikke er nogen modstridende indstillinger. Hvis disse modstridende indstillinger ikke løses, kan det påvirke brugeroplevelsen. 

Udrulningen af udrulningstrinnet i de tilfælde, hvor der findes lige indstillinger i lejeren fra en eksisterende politik, resulterer i duplikering af de eksisterende indstillinger i lejeren, men påvirker ikke brugeroplevelsen. 

Der er angivet ekstra indstillinger for din opmærksomhed, men kræver ikke, at du gør noget.

Du kan få flere oplysninger om administration af politikkonflikter [i Azure AD dokumentation til betinget adgang](/azure/active-directory/conditional-access/).

## <a name="update-deployment-step-status"></a>Status for opdateringstrin til installation

1. Vælg **Lejere** på navigationssiden til venstre.

2. Vælg den lejer, du vil have vist, på lejerlisten.

3. Vælg fanen **Udrulningsplan** .

4. Vælg et installationstrin, du vil opdatere, på listen over installationstrin.

5. Vælg en handlingsstatus på rullelisten **Til adresse** .

    | Handlingsstatus                        | Beskrivelse      |
    |---------------------------------------|----------------------------------------|
    | Til-adresse                        | Standardtilstanden for alle installationstrin, der ikke omfatter flere processer for udrulningstrin.      |
    | Planlagt                           | Udrulningstrinnet er planlagt, men er endnu ikke fuldført.                                      |
    | Risiko accepteret                     | Brugeren har accepteret den risiko, der ellers ville være blevet afværget ved at anvende installationstrinnet. |
    | Risiko løst via tredjepart | Risikoen er løst ved implementering af et tredjepartsprogram eller en software.             |
    | Løst via alternative midler  | Risikoen er blevet løst på andre måder, f.eks. ved at implementere et internt værktøj.    |
    | Manuel konfiguration er anvendt      | Den konfiguration, der er foreskrevet i udrulningsplanen, er blevet anvendt manuelt.                         |

## <a name="share-deployment-step"></a>Del udrulningstrin

1. Vælg **Lejere** på navigationssiden til venstre.

2. Vælg den lejer, du vil have vist, på lejerlisten.

3. Vælg fanen **Udrulningsplan** .

4. Vælg et installationstrin, du vil dele, på listen Installationstrin.

5. Vælg en af følgende indstillinger på rullelisten **Del** .

    | Mulighed  | Beskrivelse |
    |-----------|-------------------------------------------------------------------------|
    | Kopiere  | Kopierer et link til installationstrinnet til Udklipsholder.                                     |
    | E-mail | Åbner den nye mail på din lokale computer og indsætter et link til udrulningstrinnet. |

    Linket gør det muligt for alle med tilladelser i din organisation at få vist lejerens udrulningsplan.


## <a name="related-content"></a>Relateret indhold

[Oversigt over brug af Microsoft 365 baselines for fyrtårne til installation af standardlejerkonfigurationer](m365-lighthouse-deploy-standard-tenant-configurations-overview.md) (artikel)\
[Oversigt over siden Windows 365 (cloud-pc'er) i Microsoft 365 Lighthouse](m365-lighthouse-tenants-page-overview.md) (artikel)\
[Microsoft 365 Ofte stillede spørgsmål om Fyrtårn](m365-lighthouse-faq.yml) (artikel)\
[Konfigurer sikkerhed Microsoft 365 Lighthouse-portal](m365-lighthouse-configure-portal-security.md) (artikel) 