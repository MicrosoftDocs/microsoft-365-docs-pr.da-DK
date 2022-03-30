---
title: Installer Microsoft 365 lighthouse-grundlinjer
f1.keywords: CSH
ms.author: sharik
author: SKjerland
manager: scotv
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
description: For administrerede tjenesteudbydere, der bruger Microsoft 365 Lighthouse, kan du få mere at vide om, hvordan du Microsoft 365 grundlinjer med fyrtårne.
ms.openlocfilehash: 0e19843ee6cfebaf9b37e10929884d0671608451
ms.sourcegitcommit: 8423f47fce3905a48db9daefe69c21c841da43a0
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/15/2022
ms.locfileid: "63599478"
---
# <a name="deploy-microsoft-365-lighthouse-baselines"></a>Installer Microsoft 365 lighthouse-grundlinjer

Microsoft 365 Lighthouse giver dig mulighed for at installere almindelige konfigurationer for administrerede lejere for at sikre brugere, enheder og data i kundelejere. Der er syv [standardkonfigurationer for grundlinjer,](m365-lighthouse-deploy-standard-tenant-configurations-overview.md) der er standard med Fyrtårn. Med funktionen Lighthouse-installationsplan kan du få vist, teste og implementere sikkerhedskonfigurationer på tværs af alle dine lejere. En udrulningsplan er kun tilgængelig for aktive lejere. Når en lejer er onboardet, kan du sammenligne dine kunders aktuelle konfiguration med standardkonfigurationen for grundlinjer og udføre de relevante handlinger.

## <a name="before-you-begin"></a>Før du begynder

Sørg for, at du og dine kundelejere opfylder de krav, der er angivet [i Krav til Microsoft 365 Lighthouse](m365-lighthouse-requirements.md).

## <a name="view-a-deployment-plan"></a>Få vist en installationsplan

1. I venstre navigationsside skal du vælge **Lejere**.

2. Vælg den lejer, du vil have vist, på lejerlisten.

3. Vælg fanen **Installationsplan** .

    Fanen Installationsplan indeholder en søgbar og eksporterelig liste over hvert installationstrin, der er inkluderet i lejerens installationsplan, som indeholder følgende oplysninger for hvert installationstrin:

    | Kolonne            | Beskrivelse |
    |-----------------|-------------------------------------------------------------------------------------|
    | Installationstrin | Beskrivelse af installationstrin.                                                     |
    | Status          | Status for installationstrinnet.                                                  |
    | Oprindelig plan        | Den oprindelige plan, som installationstrinnet er afledt af.                             |
    | Kategori        | Uanset om installationstrinnet er knyttet til administration af enheder, identitet eller data. |
    | Senest opdateret    | Den dato, hvor installationstrinnet sidst blev opdateret.                             |

4. Vælg et installationstrin, du vil gennemse, på listen.

    Siden Installationstrin indeholder følgende oplysninger:

    | Kolonne            | Beskrivelse |
    |-------------------|-----------------------------------------------------------------------------------------------|
    | Oversigt        | En oversigt over udrulningstrinnets formål.                                         |
    | Oprindelig plan       | Den oprindelige plan, som installationstrinnet er afledt af.                             |
    | Kategori       | Uanset om installationstrinnet er knyttet til administration af enheder, identitet eller data. |
    | Påkrævet varenummer   | SKU'er, der kræves for at fuldføre udrulningstrinnet.                                      |
    | Brugerpåvirkning    | Virkningen af at udrulle trinnet til lejerens brugere.                             |
    | For dine brugere | Links til ressourcer, som lejerens brugere kan finde nyttige.                             |
    | Næste trin     | Links og vejledning omkring eventuelle næste trin.                                |

    Installationstrin består af en eller flere processer, der skal udføres for at opfylde kravene til installationstrinnet. Siden Installationstrin indeholder procestabellen, der viser hver proces, der er inkluderet i installationstrinnet, og indeholder følgende oplysninger:

    | Kolonne            | Beskrivelse |
    |-------------------|-------------------------------------------------------------|
    | Procesnavn      | Navnet på processen, som, når den er markeret, åbner den relevante procesfane.          |
    | Status            | Den registrerede status for disse indstillingskonfigurationer, der er inkluderet i installationsprocessen.           |
    | Administrationsportal | Portalen, hvor de konfigurationsindstillinger, der er knyttet til processen, administreres. |

## <a name="deploy-a-deployment-step"></a>Installér et installationstrin

1. I venstre navigationsside skal du vælge **Lejere**.

2. Vælg den lejer, du vil have vist, på lejerlisten.

3. Vælg fanen **Installationsplan** .

4. Vælg det installationstrin, du vil installere, på listen Installationstrin.

5. Vælg **Gennemse, og installér**.

6. Vælg **Installér i** ruden Bekræft **konfigurationer**.

## <a name="test-a-deployment-step"></a>Test et installationstrin

For installationstrin, der er installeret via Betingede adgangspolitikker, kan du sammenligne konfigurationsindstillingerne i installationstrinnet med indstillinger i eventuelle eksisterende politikker uden at udrulle indstillingerne for lejeren.

1. I venstre navigationsside skal du vælge **Lejere**.

2. Vælg den lejer, du vil have vist, på lejerlisten.

3. Vælg fanen **Installationsplan** .

4. Vælg det installationstrin, du vil installere, på listen Installationstrin.

5. Vælg **Gennemse, og installér**.

6. I **ruden Bekræft konfigurationer** skal du **vælge Test disse indstillinger uden en installation**.

7. Vælg **Test**.

Ruden Bekræft konfigurationer lukker og viser sammenligning af politikker. Hver politik inden for den eksisterende lejer vises i tabellen Registrerede indstillinger.

Tabellen Registrerede indstillinger viser hver eksisterende politik og opsummerer antallet af indstillinger og i parenteser antallet af brugere, der har en af følgende statusser:

| Status         | Beskrivelse
|-------------|------------------------------------------------------------|
| Indstillinger, der er lige store       | Samlet antal konfigurationsindstillinger i installationsplanen med en tilsvarende værdi i lejeren.      |
| Manglende indstillinger     | Samlet antal konfigurationsindstillinger i udrulningsplanen, der mangler en værdi i lejeren.      |
| Modstridende indstillinger | Samlet antal konfigurationsindstillinger i udrulningsplanen, der har en modstridende værdi i lejeren. |

Registrerede indstillinger kan også vises i en modulær tabel, der indeholder konfigurationsindstillinger for hver politik på indstillingsniveau og brugerniveau, og som kan sorteres efter hver af følgende indstillingers status:

| Status         | Beskrivelse
|-------------|------------------------------------------------------------|
| Samlet antal indstillinger       | Samlet antal konfigurationsindstillinger, der er inkluderet i installationsprocessen.                        |
| Indstillinger, der er lige store       | Samlet antal konfigurationsindstillinger i installationsplanen med en tilsvarende værdi i lejeren.      |
| Manglende indstillinger     | Samlet antal konfigurationsindstillinger i udrulningsplanen, der mangler en værdi i lejeren.      |
| Modstridende indstillinger | Samlet antal konfigurationsindstillinger i udrulningsplanen, der har en modstridende værdi i lejeren. |
| Ekstra indstillinger       | Samlet antal konfigurationsindstillinger med en værdi i lejeren, men ingen værdi i installationsplanen.     |

Når denne sammenligning foretages, opdaterer Lighthouse automatisk statussen Registreret, Installationsstatus og Installationstrin.

Hvis der ikke er nogen eksisterende politikker at sammenligne, skal du vælge Gennemse og installere for at genåbne ruden Bekræft konfigurationer og vælge Installér.

Hvis der er eksisterende politikker, som du skal sammenligne, kan du enten:

- Rediger konfigurationsindstillingerne for installationsplanen, og afkryds dem igen i forhold til de eksisterende  politikker, vælg Gennemse og installér for at genåbne ruden Bekræft konfigurationer, juster de ønskede konfigurationsindstillinger, markér afkrydsningsfeltet igen, og vælg **Test** nederst i ruden.

- Rediger de eksisterende politikker inden for den gældende administrationsportal for at afstemme forskellene enten ved at:
  - Anvend manglende indstillinger
  - Redigering af indstillinger, der er i konflikt med hinanden
  - Sletning af eksisterende politikker

For hver installationsproces, der kan automatiseres via Lighthouse, er der både en installationsstatus og en registreret status.

- Den registrerede status angiver, i hvilket omfang indstillingerne i denne proces er implementeret i øjeblikket.
- Installationsstatussen er status for den seneste installation for lejeren.

Installationstrin kan installeres uanset eksisterende politikker, men betragtes ikke som fuldført, før der ikke er nogen modstridende indstillinger. Hvis disse modstridende indstillinger ikke løses, kan det påvirke brugeroplevelsen. 

Udrulning af installationstrinnet i tilfælde, hvor der er samme indstillinger i lejeren fra en eksisterende politik, medfører duplikering af de eksisterende indstillinger i lejeren, men påvirker ikke brugeroplevelsen. 

Ekstra indstillinger er medfølgende for din opmærksomhed, men kræver ikke, at du skal handle.

Du kan finde flere oplysninger om administration af politikkonflikter under [Dokumentation til betinget adgang til Azure AD](/azure/active-directory/conditional-access/).

## <a name="update-deployment-step-status"></a>Status for opdatering af installationstrin

1. I venstre navigationsside skal du vælge **Lejere**.

2. Vælg den lejer, du vil have vist, på lejerlisten.

3. Vælg fanen **Installationsplan** .

4. Vælg det installationstrin, du vil opdatere, på installationstrinlisten.

5. Vælg **en handlingsstatus** på rullelisten Til-adresse.

    | Handlingsstatus                        | Beskrivelse      |
    |---------------------------------------|----------------------------------------|
    | Til-adresse                        | Standardtilstanden for alle installationstrin, der IKKE inkluderer flere installationsprocesser.      |
    | Planlagt                           | Installationstrinnet har været planlagt, men er endnu ikke fuldført.                                      |
    | Accepteret risiko                     | Brugeren har accepteret den risiko, der ellers ville være blevet omvendt, ved at anvende installationstrinnet. |
    | Risiko løst via tredjepart | Risikoen er løst ved implementeringen af et program eller en software fra tredjepart.             |
    | Løst via alternativ måde  | Risikoen er løst via alternative metoder, f.eks. implementeringen af et internt værktøj.    |
    | Manuel konfiguration anvendt      | Den konfiguration, der er angivet i installationsplanen, er blevet anvendt manuelt.                         |

## <a name="share-deployment-step"></a>Del installationstrin

1. I venstre navigationsside skal du vælge **Lejere**.

2. Vælg den lejer, du vil have vist, på lejerlisten.

3. Vælg fanen **Installationsplan** .

4. Vælg det installationstrin, du vil dele, på listen Installationstrin.

5. Vælg **en** af følgende indstillinger på rullelisten Del.

    | Indstilling  | Beskrivelse |
    |-----------|-------------------------------------------------------------------------|
    | Kopiér  | Kopierer et link til installationstrinnet til udklipsholderen.                                     |
    | Mail | Åbner din nye mail på din lokale computer og indsætter et link til installationstrinnet. |

    Linket gør det muligt for alle med tilladelser i organisationen at få vist lejerens installationsplan.


## <a name="related-content"></a>Relateret indhold

[Oversigt over brug af oprindelige planer til installation af standardlejerkonfigurationer](m365-lighthouse-deploy-standard-tenant-configurations-overview.md) (artikel)\
[Microsoft 365 for lejere sideoversigt](m365-lighthouse-tenants-page-overview.md) (artikel)\
[Microsoft 365 ofte stillede spørgsmål om Fyrtårn](m365-lighthouse-faq.yml) (artikel)\
[Konfigurere Microsoft 365 Lighthouse-portalens sikkerhed](m365-lighthouse-configure-portal-security.md) (artikel) 