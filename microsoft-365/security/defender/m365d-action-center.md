---
title: Gå til Handlingscenter for at få vist og godkende dine automatiserede undersøgelses- og afhjælpningsopgaver
description: Brug handlingscenter til at få vist oplysninger om automatiseret undersøgelse og godkende afventende handlinger
keywords: Handlingscenter, trusselsbeskyttelse, undersøgelse, besked, afventende, automatiseret, registrering
search.appverid: met150
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
- m365initiative-m365-defender
ms.topic: how-to
ms.custom:
- autoir
- admindeeplinkDEFENDER
ms.reviewer: evaldm, isco
ms.openlocfilehash: b64cbc55a975ee02bd1bd5d41d30330e8729d4be
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63606454"
---
# <a name="the-action-center"></a>Handlingscenter

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Gælder for:**
- Microsoft 365 Defender

Handlingscenter giver en "enkelt rude af glas" til hændelses- og beskedopgaver som f.eks.:

- Godkende afventende afhjælpningshandlinger.
- Få vist en overvågningslog over allerede godkendte afhjælpningshandlinger.
- Gennemgå de fuldførte afhjælpningshandlinger.

Da handlingscenteret giver en omfattende oversigt over Microsoft 365 Defender på arbejdet, kan dit sikkerhedsteam fungere mere effektivt og effektivt.

## <a name="the-unified-action-center"></a>Det samlede handlingscenter

Det samlede handlingscenter ([https://security.microsoft.com/action-center](https://security.microsoft.com/action-center)) viser ventende og fuldførte afhjælpningshandlinger for dine enheder, mail & indhold til samarbejde og identiteter på ét sted.

:::image type="content" source="../../media/m3d-action-center-unified.png" alt-text="Det samlede handlingscenter i Microsoft 365 Defender portal." lightbox="../../media/m3d-action-center-unified.png":::

Eksempel: 

- Hvis du tidligere brugte Office 365 Security & Compliance Center ([https://protection.office.com](https://protection.office.com)), kan du prøve det samlede handlingscenter <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">på Microsoft 365 Defender portal</a>.
- Hvis du brugte handlingscenter i Microsoft Defender Security Center ([https://securitycenter.windows.com/action-center](https://securitycenter.windows.com/action-center)), kan du prøve det samlede handlingscenter på <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portal</a>.
- Hvis du allerede bruger <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender,</a> vil du se flere forbedringer i Handlingscenter ([https://security.microsoft.com/action-center](https://security.microsoft.com/action-center)).

Det samlede Handlingscenter samler afhjælpningshandlinger på tværs af Defender for Endpoint og Defender Office 365. Den definerer et fælles sprog for alle afhjælpningshandlinger og giver en samlet undersøgelsesoplevelse. Sikkerhedsteamet har en oplevelse med "enkelt rude af glas" til at få vist og administrere afhjælpningshandlinger.  

Du kan bruge det samlede handlingscenter, hvis du har de rette tilladelser og ét eller flere af følgende abonnementer:

- [Defender til Slutpunkt](../defender-endpoint/microsoft-defender-endpoint.md)
- [Defender til Office 365](/microsoft-365/security/office-365-security/defender-for-office-365)
- [Microsoft 365 Defender](microsoft-365-defender.md)

> [!TIP]
> Du kan få mere at vide under [Krav](./prerequisites.md).

## <a name="using-the-action-center"></a>Brug af Handlingscenter

1. Gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender,</a> og log på. 
2. Vælg Handlingscenter i **navigationsruden**. 

Når du besøger Handlingscenter, vises der to faner: **Ventende handlinger** og **Oversigt**. Følgende tabel opsummerer, hvad du ser på hver fane:

|Tabulator  |Beskrivelse  |
|---------|---------|
|**Afventer**     | Viser en liste over handlinger, der kræver opmærksomhed. Du kan godkende eller afvise handlinger én ad gangen eller vælge flere handlinger, hvis de har samme type handling (f.eks. karantænefil). <p>**Tip**: Sørg for at gennemse og godkende (eller afvise) afventende handlinger så hurtigt som muligt, så dine automatiserede undersøgelser kan fuldføres i tide.       |
|**Historik**     | Fungerer som en overvågningslog for handlinger, der er blevet foretaget, f.eks.: <br/>- Afhjælpningshandlinger, der er foretaget som et resultat af automatiserede undersøgelser <br/>- Afhjælpningshandlinger, der er foretaget på mistænkelige eller skadelige mails, filer eller URL-adresser<br/>- Afhjælpningshandlinger, der er godkendt af sikkerhedsteamet <br/>- Kommandoer, der blev kørt, og afhjælpningshandlinger, der blev anvendt under Live Response-sessioner<br/>- Afhjælpningshandlinger, der er foretaget af din antivirusbeskyttelse <p>Indeholder en metode til at fortryde bestemte handlinger (se [Fortryd fuldførte handlinger](m365d-autoir-actions.md#undo-completed-actions)).        |

Du kan tilpasse, sortere, filtrere og eksportere data i Handlingscenter.

:::image type="content" source="../../media/m3d-action-center-columnsfilters.png" alt-text="Sortering, filtrering og tilpasning af egenskaberne for handlingscenter." lightbox="../../media/m3d-action-center-columnsfilters.png":::

- Vælg en kolonneoverskrift for at sortere elementerne i stigende eller faldende rækkefølge.
- Brug tidsfilteret til at få vist data for den seneste dag, uge, 30 dage eller 6 måneder.
- Vælg de kolonner, du vil have vist.
- Angiv, hvor mange elementer der skal medtages på hver side med data.
- Brug filtre til at få vist netop de elementer, du vil have vist.
- Vælg **Eksportér** for at eksportere resultaterne til .csv fil.

## <a name="actions-tracked-in-the-action-center"></a>Handlinger, der er registreres i handlingscenter

Alle handlinger, uanset om de afventer godkendelse eller allerede er taget, registreres i Handlingscenter. Tilgængelige handlinger omfatter følgende:

- Pakke til samlet undersøgelse 
- Isoler enhed (denne handling kan fortrydes) 
- Offboard machine 
- Udgivelse af kode 
- Frigiv fra karantæne 
- Anmodningseksempel 
- Begræns udførelse af kode (denne handling kan fortrydes) 
- Kør antivirusscanning 
- Stop og karantæne 

Ud over afhjælpningshandlinger, der er foretaget automatisk som et resultat af automatiserede undersøgelser, registrerer Handlingscenter også handlinger, som dit sikkerhedsteam har taget for at løse registrerede trusler, og handlinger, der er foretaget som et resultat af funktioner til [trusselsbeskyttelse](m365d-autoir.md) i Microsoft 365 Defender. Du kan finde flere oplysninger om automatiske og manuelle afhjælpningshandlinger [i Afhjælpningshandlinger](m365d-remediation-actions.md).

## <a name="viewing-action-source-details"></a>Få vist oplysninger om handlingskilde

(**NY!**) Det forbedrede handlingscenter indeholder nu en kolonne **med handlingskilde** , der fortæller dig, hvor hver handling stammer fra. I følgende tabel beskrives mulige **handlingskildeværdier** :

| Handlingskildeværdi | Beskrivelse |
|:-----|:---|
| **Manuel enhedshandling** | En manuel handling, der er foretaget på en enhed. Eksempler kan være [enhedsisolation eller](../defender-endpoint/respond-machine-alerts.md#isolate-devices-from-the-network) [filkarantæne](../defender-endpoint/respond-file-alerts.md#stop-and-quarantine-files). |
| **Manuel mailhandling** | En manuel handling, der er foretaget på mail. Et eksempel omfatter blød sletning af mails eller [afhjælpning af en mail](../office-365-security/remediate-malicious-email-delivered-office-365.md). |
| **Automatiseret enhedshandling** | En automatisk handling, der er foretaget på en enhed, f.eks. en fil eller proces. Eksempler på automatiserede handlinger omfatter at sende en fil til karantæne, stoppe en proces og fjerne en registreringsdatabasenøgle. (Se [Afhjælpningshandlinger i Microsoft Defender til Slutpunkt](../defender-endpoint/manage-auto-investigation.md#remediation-actions)). |
| **Automatiseret mailhandling** | En automatisk handling, der er foretaget på mailindhold, f.eks. en mail, en vedhæftet fil eller URL-adresse. Eksempler på automatiserede handlinger omfatter blød sletning af mails, blokering af URL-adresser og de slå ekstern videresendelse af mails fra. (Se [Afhjælpningshandlinger i Microsoft Defender for Office 365](../office-365-security/air-remediation-actions.md).) |
| **Avanceret jagthandling** | Handlinger, der er foretaget på enheder eller mail med [avanceret jagt](./advanced-hunting-overview.md). |
| **Stifinder-handling** | Handlinger, der er foretaget på mailindhold med [Stifinder](../office-365-security/threat-explorer.md). |
| **Manuel live svarhandling** | Handlinger, der er foretaget på en enhed [med direkte svar](../defender-endpoint/live-response.md). Eksempler kan være at slette en fil, stoppe en proces og fjerne en planlagt opgave. |
| **Live response-handling** | Handlinger, der er foretaget på en enhed [med Microsoft Defender til endpoint-API'er](../defender-endpoint/management-apis.md#microsoft-defender-for-endpoint-apis). Eksempler på handlinger omfatter at isolere en enhed, køre en antivirus-scanning og få oplysninger om en fil. |

## <a name="required-permissions-for-action-center-tasks"></a>Påkrævede tilladelser for handlingscenteropgaver

Hvis du vil udføre opgaver, f.eks. godkende eller afvise afventende handlinger i Handlingscenter, skal de tilladelser, der er angivet i følgende tabel, være tildelt:

|Afhjælpningshandling |Påkrævede roller og tilladelser |
|--|----|
|Afhjælpning af Microsoft Defender til Slutpunkt (enheder) |**Sikkerhedsadministratorrolle** tildelt i Azure Active Directory (Azure AD) ([https://portal.azure.com](https://portal.azure.com)) eller Microsoft 365 Administration ([https://admin.microsoft.com](https://admin.microsoft.com))<br/>--- eller ---<br/>**Aktive afhjælpningshandlinger,** der er tildelt i Microsoft Defender til slutpunkt <br/> <br/> Du kan få mere at vide i følgende ressourcer: <br/>- [Indbyggede roller i Azure AD](/azure/active-directory/roles/permissions-reference)<br/>- [Opret og administrer roller for rollebaseret adgangskontrol (Microsoft Defender til slutpunkt)](../defender-endpoint/user-roles.md)  |
|Microsoft Defender til Office 365 afhjælpning (Office indhold og mail)  |**Sikkerhedsadministratorrolle** tildelt i enten Azure AD ([https://portal.azure.com](https://portal.azure.com)) eller Microsoft 365 Administration ([https://admin.microsoft.com](https://admin.microsoft.com))<br/>--- og --- <br/>**Den rolle, der er** tildelt i Security & Compliance Center ([https://protection.office.com](https://protection.office.com)) <br/><br/>**VIGTIGT**! Hvis du kun har  fået tildelt rollen som sikkerhedsadministrator i Office 365 Security & Compliance Center ([https://protection.office.com](https://protection.office.com)), kan du ikke få adgang til handlingscenter eller Microsoft 365 Defender funktioner. Du skal have **sikkerhedsadministratorens rolle** tildelt i Azure AD eller Microsoft 365 Administration. <br/><br/>Du kan få mere at vide i følgende ressourcer: <br/>- [Indbyggede roller i Azure AD](/azure/active-directory/roles/permissions-reference)<br/>- [Tilladelser i Sikkerheds- & Compliance Center](/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center) |

> [!TIP]
> Brugere, der har **fået tildelt rollen** Global administrator i Azure AD, kan godkende eller afvise alle afventende handlinger i Handlingscenter. Men som en bedste fremgangsmåde bør din organisation begrænse antallet af personer, der har fået **tildelt rollen som** global administrator. Vi anbefaler, at du **bruger sikkerhedsadministratoren****, aktive** afhjælpningshandlinger  og søge- og fjerneroller, der er angivet i den foregående tabel, for handlingscentertilladelser.

## <a name="next-step"></a>Næste trin 

- [Få vist og administrer afhjælpningshandlinger](m365d-autoir-actions.md)
