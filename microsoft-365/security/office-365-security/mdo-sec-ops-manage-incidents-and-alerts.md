---
title: Administrer hændelser og underretninger fra Defender for Office 365 i Microsoft 365 Defender
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: Admin
ms.date: ''
ms.topic: conceptual
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
ms.custom: ''
description: SecOps-personale kan lære, hvordan du bruger hændelseskøen i Microsoft 365 Defender til at administrere hændelser i Microsoft Defender for Office 365.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 8467d77bd3bdd99af0a33f7fc373e61f7e3efb51
ms.sourcegitcommit: 725a92b0b1555572b306b285a0e7a7614d34e5e5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/24/2022
ms.locfileid: "66858594"
---
# <a name="manage-incidents-and-alerts-from-microsoft-defender-for-office-365-in-microsoft-365-defender"></a>Administrer hændelser og beskeder fra Microsoft Defender for Office 365 i Microsoft 365 Defender

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Gælder for:**
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

En [hændelse](/microsoft-365/security/defender/incidents-overview) i Microsoft 365 Defender er en samling korrelerede beskeder og tilknyttede data, der definerer den komplette historie om et angreb. Defender for Office 365 [beskeder](/microsoft-365/compliance/alert-policies#default-alert-policies), [automatiseret undersøgelse og svar (AIR)](office-365-air.md#the-overall-flow-of-air) og resultatet af undersøgelserne er indbygget integreret og korreleret på siden **Hændelser** i Microsoft 365 Defender på <https://security.microsoft.com/incidents-queue>. Vi henviser til denne side som _køen Hændelser_.

Der oprettes beskeder, når ondsindet eller mistænkelig aktivitet påvirker en enhed (f.eks. mail, brugere eller postkasser). Beskeder giver værdifuld indsigt i igangværende eller fuldførte angreb. Et igangværende angreb kan dog påvirke flere enheder, hvilket resulterer i flere beskeder fra forskellige kilder. Nogle indbyggede beskeder udløser automatisk AIR-playbooks. Disse playbooks udfører en række undersøgelsestrin for at søge efter andre påvirkede enheder eller mistænkelig aktivitet.

Se denne korte video om, hvordan du administrerer Microsoft Defender for Office 365 beskeder i Microsoft 365 Defender.  
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWGrL2]

Defender for Office 365 beskeder, undersøgelser og deres data korreleres automatisk. Når en relation bestemmes, oprettes der en hændelse af systemet for at give sikkerhedsteams synlighed for hele angrebet.

Vi anbefaler på det kraftigste, at SecOps-teams administrerer hændelser og beskeder fra Defender for Office 365 i køen Hændelser på <https://security.microsoft.com/incidents-queue>. Denne fremgangsmåde har følgende fordele:

- Flere indstillinger for [administration](/microsoft-365/security/defender/manage-incidents):
  - Prioritering
  - Filtrering
  - Klassificering
  - Kodeadministration

  Du kan tage hændelser direkte fra køen eller tildele dem til nogen. Kommentarer og historik over kommentarer kan hjælpe med at spore status.

- Hvis angrebet påvirker andre arbejdsbelastninger, der er beskyttet af Microsoft Defender<sup>\*</sup>, korreleres de relaterede beskeder, undersøgelser og deres data også med den samme hændelse.

  <sup>\*</sup>Microsoft Defender for Endpoint, Microsoft Defender for Identity og Microsoft Defender for Cloud Apps.

- Kompleks korrelationslogik er ikke påkrævet, fordi logikken leveres af systemet.

- Hvis korrelationslogikken ikke fuldt ud opfylder dine behov, kan du føje beskeder til eksisterende hændelser eller oprette nye hændelser.

- Relaterede Defender for Office 365 beskeder, AIR-undersøgelser og ventende handlinger fra undersøgelser føjes automatisk til hændelser.

- Hvis AIR-undersøgelsen ikke finder nogen trussel, løses de relaterede beskeder automatisk af systemet. Hvis alle beskeder i en hændelse løses, ændres hændelsesstatussen også til **Løst**.

- Relaterede beviser og svarhandlinger samles automatisk under fanen **Beviser og svar** i hændelsen.

- Medlemmer af sikkerhedsteamet kan foretage svarhandlinger direkte fra hændelserne. De kan f.eks. slette mails i postkasser eller fjerne mistænkelige indbakkeregler fra postkasser.

- Anbefalede mailhandlinger oprettes kun, når den seneste leveringsplacering for en skadelig mail er en cloudpostkasse.

- Ventende mailhandlinger opdateres baseret på den seneste leveringsplacering. Hvis mailen allerede er blevet afhjulpet med en manuel handling, afspejles det i statussen.

- Anbefalede handlinger oprettes kun for mail- og mailklynger, der er besluttet på at være de mest kritiske trusler:
  - Malware
  - Phishing med høj genkendelsessikkerhed
  - Skadelige URL-adresser
  - Skadelige filer

> [!NOTE]
> Hændelser repræsenterer ikke kun statiske hændelser. De repræsenterer også angrebshistorier, der sker over tid. Efterhånden som angrebet skrider frem, føjes nye Defender for Office 365 beskeder, AIR-undersøgelser og deres data løbende til den eksisterende hændelse.

Administrer hændelser på siden **Hændelser** på portalen Microsoft 365 Defender på <https://security.microsoft.com/incidents-queue>:

![Siden Hændelser på Microsoft 365 Defender-portalen.](../../media/mdo-sec-ops-incidents.png)

![Pop op-vinduet Detaljer på siden Hændelser på portalen Microsoft 365 Defender.](../../media/mdo-sec-ops-incident-details.png)

![Pop op-vinduet Filtrer på siden Hændelser på portalen Microsoft 365 Defender.](../../media/mdo-sec-ops-incident-filters.png)

![Fanen Oversigt over oplysninger om hændelser på portalen Microsoft 365 Defender.](../../media/mdo-sec-ops-incident-summary-tab.png)

![Fanen Med beviser og beskeder i hændelsesoplysningerne på Microsoft 365 Defender-portalen.](../../media/mdo-sec-ops-incident-evidence-and-response-tab.png)

Administrer hændelser på siden **Hændelser** i Microsoft Sentinel på <https://portal.azure.com/#blade/HubsExtension/BrowseResource/resourceType/microsoft.securityinsightsarg%2Fsentinel>:

![Siden Hændelser i Microsoft Sentinel.](../../media/mdo-sec-ops-microsoft-sentinel-incidents.png)

![Siden Med oplysninger om hændelser i Microsoft Sentinel.](../../media/mdo-sec-ops-microsoft-sentinel-incident-details.png)

## <a name="response-actions-to-take"></a>Svarhandlinger, der skal udføres

Sikkerhedsteams kan foretage en lang række svarhandlinger på mail ved hjælp af Defender for Office 365 værktøjer:

- Du kan slette meddelelser, men du kan også foretage følgende handlinger på mail:
  - Flyt til Indbakke
  - Flyt til uønsket mail
  - Flyt til Slettede elementer
  - Blød sletning
  - Slet hårdt.

  Du kan foretage disse handlinger fra følgende placeringer:

  - Fanen **Beviser og svar** fra oplysningerne om hændelsen på siden **Hændelser** ** på <https://security.microsoft.com/incidents-queue> (anbefales).
  - **Threat Explorer** på <https://security.microsoft.com/threatexplorer>.
  - Det samlede **handlingscenter** på  <https://security.microsoft.com/action-center/pending>.

- Du kan starte en AIR-playbook manuelt på en hvilken som helst mail ved hjælp af handlingen **Udløs undersøgelse** i Threat Explorer.

- Du kan rapportere falske positive eller falske negative registreringer direkte til Microsoft ved hjælp af [Threat Explorer](threat-explorer.md) eller [administratorindsendelser](admin-submission.md).

- Du kan blokere uopdagede skadelige filer, URL-adresser eller afsendere ved hjælp af [listen over tilladte/blokerede](tenant-allow-block-list.md) lejere.

Defender for Office 365 handlinger integreres problemfrit i jagtoplevelser, og handlingshistorikken er synlig under fanen **Historie** i det samlede **handlingscenter** på <https://security.microsoft.com/action-center/history>.

Den mest effektive måde at gribe ind på er ved at bruge den indbyggede integration med Incidents i Microsoft 365 Defender. Du kan blot godkende de handlinger, der blev anbefalet af AIR, i Defender for Office 365 under fanen [Beviser og svar](/microsoft-365/security/defender/investigate-incidents#evidence-and-response) i en hændelse i Microsoft 365 Defender. Denne metode til tacking-handling anbefales af følgende årsager:

- Du undersøger hele angrebshistorien.
- Du kan drage fordel af den indbyggede korrelation med andre arbejdsbelastninger: Microsoft Defender for Endpoint, Microsoft Defender for Identity og Microsoft Defender for Cloud Apps.
- Du foretager handlinger på mail fra et enkelt sted.

Du foretager handlinger på mail baseret på resultatet af en manuel undersøgelse eller jagtaktivitet. [Threat Explorer](threat-explorer.md) gør det muligt for medlemmer af sikkerhedsteamet at reagere på alle mails, der stadig findes i cloudpostkasser. De kan udføre handlinger på meddelelser i organisationen, der blev sendt mellem brugere i din organisation. Threat Explorer-data er tilgængelige for de sidste 30 dage.

Se denne korte video for at få mere at vide om, hvordan Microsoft 365 Defender kombinerer beskeder fra forskellige registreringskilder, f.eks. Defender for Office 365, i hændelser. 
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWGpcs]
