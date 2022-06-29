---
title: Gå til Løsningscenter for at få vist og godkende dine automatiserede undersøgelses- og afhjælpningsopgaver
description: Brug Løsningscenter til at få vist oplysninger om automatiseret undersøgelse og godkende ventende handlinger
keywords: Handlingscenter, trusselsbeskyttelse, undersøgelse, besked, ventende, automatiseret, registrering
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
ms.openlocfilehash: 631849997fffc0e4f90a9aa9d1850646b764a52a
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/29/2022
ms.locfileid: "66493481"
---
# <a name="the-action-center"></a>Løsningscenter

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Gælder for:**
- Microsoft 365 Defender

Løsningscenter giver en "enkelt rude af glas" til hændelses- og beskedopgaver, f.eks.:

- Godkendelse af ventende afhjælpningshandlinger.
- Visning af en overvågningslog over allerede godkendte afhjælpningshandlinger.
- Gennemse fuldførte afhjælpningshandlinger.

Da Løsningscenter giver en omfattende visning af Microsoft 365 Defender på arbejdet, kan sikkerhedsteamet arbejde mere effektivt og effektivt.

## <a name="the-unified-action-center"></a>Det samlede løsningscenter

Unified Action Center ([https://security.microsoft.com/action-center](https://security.microsoft.com/action-center)) viser ventende og fuldførte afhjælpningshandlinger for dine enheder, mail & samarbejdsindhold og identiteter på én placering.

:::image type="content" source="../../media/m3d-action-center-unified.png" alt-text="Det samlede handlingscenter på Microsoft 365 Defender-portalen." lightbox="../../media/m3d-action-center-unified.png":::

Eksempel: 

- Hvis du tidligere har brugt Office 365 Security & Compliance Center ([https://protection.office.com](https://protection.office.com)), kan du prøve unified Action Center på <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portalen</a>.
- Hvis du brugte Løsningscenter i Microsoft Defender Security Center ([https://securitycenter.windows.com/action-center](https://securitycenter.windows.com/action-center)), kan du prøve Unified Action Center på <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portalen</a>.
- Hvis du allerede bruger <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender-portalen</a>, kan du se flere forbedringer i Løsningscenter ([https://security.microsoft.com/action-center](https://security.microsoft.com/action-center)).

I Unified Action Center samles afhjælpningshandlinger på tværs af Defender for Endpoint og Defender for Office 365. Den definerer et fælles sprog for alle afhjælpningshandlinger og giver en samlet undersøgelsesoplevelse. Sikkerhedsteamet har en "enkelt rude af glas" til at få vist og administrere afhjælpningshandlinger.  

Du kan bruge Unified Action Center, hvis du har de nødvendige tilladelser og et eller flere af følgende abonnementer:

- [Defender for Endpoint](../defender-endpoint/microsoft-defender-endpoint.md)
- [Defender for Office 365](/microsoft-365/security/office-365-security/defender-for-office-365)
- [Microsoft 365 Defender](microsoft-365-defender.md)

> [!TIP]
> Du kan få mere at vide under [Krav](./prerequisites.md).

## <a name="using-the-action-center"></a>Brug af Løsningscenter

1. Gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portal,</a> og log på. 
2. Vælg **Løsningscenter** i navigationsruden. 

Når du besøger Løsningscenter, får du vist to faner: **Ventende handlinger** og **Historik**. I følgende tabel opsummeres det, du får vist under hver fane:

|Tab  |Beskrivelse  |
|---------|---------|
|**Ventende**     | Viser en liste over handlinger, der kræver opmærksomhed. Du kan godkende eller afvise handlinger én ad gangen eller vælge flere handlinger, hvis de har samme type handling (f.eks. Karantænefil). <p>**TIP**: Sørg for at gennemse og godkende (eller afvise) ventende handlinger så hurtigt som muligt, så dine automatiserede undersøgelser kan fuldføres rettidigt.       |
|**Historie**     | Fungerer som en overvågningslog for handlinger, der blev udført, f.eks.: <br/>- Afhjælpningsforanstaltninger, der blev truffet som følge af automatiserede undersøgelser <br/>– Afhjælpningshandlinger, der blev udført på mistænkelige eller skadelige mails, filer eller URL-adresser<br/>– Afhjælpningshandlinger, der blev godkendt af dit team for sikkerhedshandlinger <br/>– Kommandoer, der blev kørt, og afhjælpningshandlinger, der blev anvendt under Live Response-sessioner<br/>- Afhjælpningshandlinger, der blev udført af antivirusbeskyttelsen <p>Giver dig mulighed for at fortryde visse handlinger (se [Fortryd fuldførte handlinger](m365d-autoir-actions.md#undo-completed-actions)).        |

Du kan tilpasse, sortere, filtrere og eksportere data i Løsningscenter.

:::image type="content" source="../../media/m3d-action-center-columnsfilters.png" alt-text="Funktionerne til sortering, filtrering og tilpasning af Løsningscenter" lightbox="../../media/m3d-action-center-columnsfilters.png":::

- Vælg en kolonneoverskrift for at sortere elementer i stigende eller faldende rækkefølge.
- Brug tidsperiodefilteret til at få vist data for den seneste dag, uge, 30 dage eller 6 måneder.
- Vælg de kolonner, du vil have vist.
- Angiv, hvor mange elementer der skal medtages på hver side med data.
- Brug filtre til kun at få vist de elementer, du vil have vist.
- Vælg **Eksportér** for at eksportere resultater til en .csv fil.

## <a name="actions-tracked-in-the-action-center"></a>Handlinger, der spores i Løsningscenter

Alle handlinger, uanset om de afventer godkendelse eller allerede er udført, spores i Løsningscenter. Tilgængelige handlinger omfatter følgende:

- Hent undersøgelsespakke 
- Isoler enhed (denne handling kan fortrydes) 
- offboard-maskine 
- Frigiv kørsel af kode 
- Frigiv fra karantæne 
- Anmodningseksempel 
- Begræns udførelse af kode (denne handling kan fortrydes) 
- Kør antivirusscanning 
- Stop og sæt karantæne 
- Indeholder enheder fra netværket

Ud over afhjælpningshandlinger, der udføres automatisk som følge af [automatiserede undersøgelser](m365d-autoir.md), sporer Løsningscentret også de handlinger, dit sikkerhedsteam har foretaget for at håndtere registrerede trusler, og handlinger, der blev taget som følge af trusselsbeskyttelsesfunktioner i Microsoft 365 Defender. Du kan få flere oplysninger om automatiske og manuelle afhjælpningshandlinger under [Afhjælpningshandlinger](m365d-remediation-actions.md).

## <a name="viewing-action-source-details"></a>Få vist oplysninger om handlingskilde

(**NY!**) Det forbedrede Løsningscenter indeholder nu en kolonne med **en handlingskilde** , der fortæller dig, hvor hver handling kom fra. I følgende tabel beskrives de mulige **værdier for handlingskilden** :

| Værdi for handlingskilde | Beskrivelse |
|:-----|:---|
| **Manuel enhedshandling** | En manuel handling, der udføres på en enhed. Eksempler omfatter [enhedsisolation](../defender-endpoint/respond-machine-alerts.md#isolate-devices-from-the-network) eller [fil karantæne](../defender-endpoint/respond-file-alerts.md#stop-and-quarantine-files). |
| **Manuel mailhandling** | En manuel handling, der udføres på mail. Et eksempel omfatter blød sletning af mails eller [afhjælpning af en mail](../office-365-security/remediate-malicious-email-delivered-office-365.md). |
| **Automatisk enhedshandling** | En automatiseret handling, der udføres på et objekt, f.eks. en fil eller proces. Eksempler på automatiserede handlinger omfatter afsendelse af en fil for at sætte en fil i karantæne, stoppe en proces og fjerne en registreringsdatabasenøgle. (Se [Afhjælpningshandlinger i Microsoft Defender for Endpoint](../defender-endpoint/manage-auto-investigation.md#remediation-actions)). |
| **Automatisk mailhandling** | En automatisk handling, der udføres på mailindhold, f.eks. en mail, en vedhæftet fil eller URL-adresse. Eksempler på automatiserede handlinger omfatter blød sletning af mails, blokering af URL-adresser og deaktivering af ekstern videresendelse af mail. (Se [Afhjælpningshandlinger i Microsoft Defender for Office 365](../office-365-security/air-remediation-actions.md)). |
| **Avanceret jagthandling** | Handlinger, der udføres på enheder eller mail med [avanceret jagt](./advanced-hunting-overview.md). |
| **Explorer-handling** | Handlinger, der udføres på mailindhold med [Stifinder](../office-365-security/threat-explorer.md). |
| **Manuel live-svarhandling** | Handlinger, der udføres på en enhed med [live-svar](../defender-endpoint/live-response.md). Eksempler omfatter sletning af en fil, standsning af en proces og fjernelse af en planlagt opgave. |
| **Live response-handling** | Handlinger, der udføres på en enhed med [Microsoft Defender for Endpoint API'er](../defender-endpoint/management-apis.md#microsoft-defender-for-endpoint-apis). Eksempler på handlinger omfatter isolering af en enhed, kørsel af en antivirusscanning og hentning af oplysninger om en fil. |

## <a name="required-permissions-for-action-center-tasks"></a>Påkrævede tilladelser til opgaver i Løsningscenter

Hvis du vil udføre opgaver, f.eks. godkendelse eller afvisning af ventende handlinger i Løsningscenter, skal du have tildelt tilladelser som angivet i følgende tabel:

|Afhjælpningshandling |Påkrævede roller og tilladelser |
|--|----|
|Microsoft Defender for Endpoint afhjælpning (enheder) |**Sikkerhedsadministratorrolle** tildelt i enten Azure Active Directory (Azure AD) ([https://portal.azure.com](https://portal.azure.com)) eller Microsoft 365 Administration ([https://admin.microsoft.com](https://admin.microsoft.com))<br/>--- eller ---<br/>**Rolle for aktive afhjælpningshandlinger**, der er tildelt i Microsoft Defender for Endpoint <br/> <br/> Du kan få mere at vide i følgende ressourcer: <br/>- [Azure AD indbyggede roller](/azure/active-directory/roles/permissions-reference)<br/>- [Opret og administrer roller for rollebaseret adgangskontrol (Microsoft Defender for Endpoint)](../defender-endpoint/user-roles.md)  |
|Microsoft Defender for Office 365 afhjælpning (Office-indhold og -mail)  |**Sikkerhedsadministratorrolle**, der er tildelt i enten Azure AD ([https://portal.azure.com](https://portal.azure.com)) eller Microsoft 365 Administration ([https://admin.microsoft.com](https://admin.microsoft.com))<br/>--- og --- <br/>**Rollen Søg og Fjern** , der er tildelt i Security & Compliance Center ([https://protection.office.com](https://protection.office.com)) <br/><br/>**VIGTIGT!** Hvis du kun har tildelt rollen **Sikkerhedsadministrator** i Office 365 Security & Compliance Center ([https://protection.office.com](https://protection.office.com)), kan du ikke få adgang til Løsningscenter eller Microsoft 365 Defender funktioner. Du skal have tildelt rollen **Sikkerhedsadministrator** i Azure AD eller Microsoft 365 Administration. <br/><br/>Du kan få mere at vide i følgende ressourcer: <br/>- [Azure AD indbyggede roller](/azure/active-directory/roles/permissions-reference)<br/>- [Tilladelser i Security & Compliance Center](/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center) |

> [!TIP]
> Brugere, der har fået tildelt rollen **Global administrator** i Azure AD kan godkende eller afvise alle ventende handlinger i Løsningscenter. Som bedste praksis bør din organisation dog begrænse antallet af personer, der har fået tildelt rollen **Global administrator** . Vi anbefaler, at du bruger rollerne **Sikkerhedsadministrator**, **Aktiv afhjælpning** og **Søg og Fjern** , der er angivet i den foregående tabel for tilladelser til Løsningscenter.

## <a name="next-step"></a>Næste trin 

- [Få vist og administrer afhjælpningshandlinger](m365d-autoir-actions.md)
