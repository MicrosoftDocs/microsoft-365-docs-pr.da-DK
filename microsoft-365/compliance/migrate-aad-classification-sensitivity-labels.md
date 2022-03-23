---
title: Azure Active Directory klassificerings- og følsomhedsetiketter for Microsoft 365 grupper
ms.reviewer: vijagan
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
f1.keywords: NOCSH
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
description: I denne artikel beskrives klassiske Azure Active Directory klassificerings- og følsomhedsmærkater.
ms.openlocfilehash: 0a8c12d3d133000a880c58366a9f2b13ed8cbf49
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63589465"
---
# <a name="azure-active-directory-classification-and-sensitivity-labels-for-microsoft-365-groups"></a>Azure Active Directory klassificerings- og følsomhedsetiketter for Microsoft 365 grupper

I denne artikel beskrives klassiske Azure Active Directory klassificerings- og følsomhedsmærkater.

Følsomhedsmærkater understøttes [af disse tjenester](./sensitivity-labels-teams-groups-sites.md).

Du kan finde alle oplysninger om følsomhedsmærkater [under Få mere at vide om følsomhedsmærkater](sensitivity-labels.md).

Du kan få mere at vide om følsomhedsmærkater og deres funktionsmåde for websteder og Microsoft 365-grupper under Brug følsomhedsmærkater til at beskytte indhold [i Microsoft Teams, Microsoft 365 grupper og SharePoint websteder](sensitivity-labels-teams-groups-sites.md).

Se følgende scenarier for bedste fremgangsmåder ved overførsel fra klassisk AAD klassificering til følsomhedsmærkaterne.

## <a name="scenario-1-tenant-never-used-classic-aad-classifications-or-sensitivity-labels-for-documents-and-emails"></a>Scenarie 1: Lejer har aldrig brugt klassisk AAD klassificeringer eller følsomhedsetiketter til dokumenter og mails

- Lejeradministrator aktiverer følsomhedsmærkater for grupper ved at indstille lejerflaget "EnableMIPLabels" til sand via AAD PowerShell-cmdlet.
- Lejeradministrator opretter følsomhedsmærkaterne i [Microsoft 365 Overholdelsescenter](https://compliance.microsoft.com).
    - Lejeradministrator kan vælge fil- og mailrelaterede handlinger som kryptering og vandmærker.
    - Lejeradministrator kan vælge Microsoft 365 grupper og SharePoint Online-webstedsrelaterede handlinger til følsomhedsmærkaterne.
- Lejeradministrator udgiver politikken.
- **Kompatible arbejdsbelastninger viser følsomhedsmærkater** . Brug følsomhedsmærkaterne til at oprette grupper. Kompatible arbejdsbelastninger er de tjenester, der understøtter følsomhedsmærkater.
- **Ikke-kompatible arbejdsbelastninger** er de tjenester, der endnu ikke understøtter følsomhedsmærkater. Grupper kan dog oprettes, men de kan ikke knyttes til følsomhedsmærkatet gennem ikke-kompatible arbejdsbelastninger. Lejeradministratorer kan køre PowerShell-cmdlet'er for at knytte disse grupper til følsomhedsmærkater.

Tabel 1. Funktionsmåde for kompatible og ikke-kompatible arbejdsbelastninger – opret, rediger eller slet grupper

|Arbejdsbelastning|Hvilken etiketliste kan brugeren se i gruppevinduet?|Opret ny gruppe |Rediger gruppe |Slet gruppe |
|:-------|:-------|:--------|:--------|:--------|   
|Kompatibel   |følsomhedsmærkater. |Ingen ændring i funktionsmåden. |Ingen ændring i funktionsmåden. |Ingen ændring i funktionsmåden. |
|Ikke-kompatibel |Der er ingen synlige følsomhedsmærkater. |Brugeren kan oprette en gruppe uden at vælge følsomhedsmærkat. <br><br> Bemærk, at administratoren kan køre cmdlet'er for at anvende følsomhedsmærkater i baggrunden. |**Case 1**: Ingen følsomhedsmærkat tidligere valgt. Brugeren kan redigere en gruppe.<br><br> **Case 2**: følsomhedsmærkat anvendt tidligere i baggrunden ved hjælp af cmdlet. Brugeren kan redigere en gruppe korrekt, undtagen i tilfælde hvor brugeren vælger en ugyldig kombination af indstilling for beskyttelse af personlige oplysninger med hensyn til etiketten. |Ingen ændring i funktionsmåden.|

> [!NOTE]
> For Outlook-klienten til stationær pc (Win 32) aktiverer administratoren følsomhedsmærkaterne på deres lejer, og brugeren har en ældre version af Outlook-skrivebordsklienten (Win 32):
>
> - Brugeren ser følsomhedsmærkaterne vises på den ældre version Outlook desktopklienten.
> - Men når brugeren redigerer en gruppe og gemmer gruppen med et følsomhedsmærkat, tilsidesættes den valgte indstilling for beskyttelse af personlige oplysninger via indstillingen for beskyttelse af personlige oplysninger på den anvendte følsomhedsmærkat.
>
> Vi anbefaler, at dine brugere på en gammel version Outlook klient opgraderer til den nyere version.

## <a name="scenario-2-tenant-is-already-using-classic-aad-classifications"></a>Scenarie 2: Lejer anvender allerede klassiske AAD [klassificeringer](../enterprise/manage-microsoft-365-groups-with-powershell.md)

### <a name="case-a-tenant-never-used-sensitivity-labels-for-documents-and-emails"></a>Case A: Lejer brugte aldrig følsomhedsmærkater til dokumenter og mails

1. I den [Microsoft 365 Overholdelsescenter](https://compliance.microsoft.com), anbefaler vi, at du opretter følsomhedsmærkater med samme navn som de eksisterende klassiske Azure AD-etiketter.
2. Brug PowerShell-cmdlet'en til at anvende disse følsomhedsmærkater på eksisterende Microsoft 365 grupper og SharePoint ved hjælp af navnetilknytning.
3. Administratoren kan vælge at slette de klassiske Azure AD-etiketter:
    - Kompatible arbejdsbelastninger viser disse følsomhedsmærkater og grupper, der oprettes med dem.
    - Ikke-kompatible arbejdsbelastninger fungerer ved oprettelse af grupper, men der knyttes ingen følsomhedsmærkat til dem.
4. Administratorer kan køre PowerShell-cmdlet'er for at anvende følsomhedsmærkater på disse grupper uden mærkater.
    - Alternativt kan en administrator vælge at beholde de klassiske Azure AD-etiketter:
        - Kompatible arbejdsbelastninger viser disse følsomhedsmærkater, og grupper oprettes med dem. Kompatible arbejdsbelastninger er de tjenester, der understøtter følsomhedsmærkater.
        - Ikke-kompatible arbejdsbelastninger fungerer, når du opretter grupper, og vis klassiske Azure AD-etiketter. Disse klassiske Azure AD-etiketter er knyttet til disse grupper, der er oprettet med ikke-kompatible arbejdsbelastninger.
5. Vi anbefaler på det kraftigste, at administratorer kører PowerShell-cmdlet'er for at anvende følsomhedsmærkater på disse grupper med klassiske Azure AD-etiketter.

Tabel 2. Funktionsmåde for kompatible og ikke-kompatible arbejdsbelastninger – opret, rediger eller slet grupper

|Arbejdsbelastning|Hvilken etiketliste kan brugeren se i gruppevinduet?|Opret ny gruppe |Rediger gruppe |Slet gruppe |
|:-------|:-------|:--------|:--------|:--------|   
|Kompatibel   |følsomhedsmærkater. |Ingen ændring i funktionsmåden. |Ingen ændring i funktionsmåden. |Ingen ændring i funktionsmåden. |
|Ikke-kompatibel |Gamle klassiske AAD navne. |Brugeren kan oprette en gruppe med den klassiske Azure AD-etiket markeret. <br><br>Bemærk, at administratoren kan køre cmdlet'er for at anvende følsomhedsmærkater i baggrunden. |**Case 1**: Ingen følsomhedsmærkat tidligere valgt. Brugeren kan redigere en gruppe.<br><br> **Case 2**: Klassisk AAD tidligere valgt. Brugeren kan redigere en gruppe.<br><br> **Case 3**: følsomhedsmærkat, der tidligere er anvendt i baggrunden ved hjælp af cmdlet. Brugeren skal kunne redigere en gruppe, bortset fra et tilfælde, hvor brugeren vælger en ugyldig kombination af indstilling for beskyttelse af personlige oplysninger med hensyn til etiketten. |Brugeren kan slette en gruppe. |

> [!NOTE]
> For Outlook-klienten til stationær pc (Win 32) aktiverer administratoren følsomhedsmærkaterne på deres lejer, og brugeren har en ældre version af Outlook-skrivebordsklienten (Win 32):
>
> - Brugeren ser følsomhedsmærkaterne vises på den ældre version Outlook desktopklienten.
> - Men når brugeren redigerer en gruppe og gemmer gruppen med et følsomhedsmærkat, tilsidesættes den valgte indstilling for beskyttelse af personlige oplysninger via indstillingen for beskyttelse af personlige oplysninger på den anvendte følsomhedsmærkat.
>
> Vi anbefaler, at dine brugere på en gammel version Outlook klient opgraderer til den nyere version.

### <a name="case-b-tenant-used-sensitivity-labels-for-documents-and-emails"></a>Case B: Lejer brugte følsomhedsmærkater til dokumenter og mails

1. Så snart administratoren aktiverer følsomhedsetiketfunktionen på lejeren ved at indstille lejerflaget "EnableMIPLabels" til sand, vises mærkaterne for dokument- og mailfølsomhed i gruppe/websted/team for oprettelse og redigering.
2. En administrator kan bruge de samme mærkater for dokument- og mailfølsomhed til at gennemtvinge beskyttelse af personlige oplysninger og ekstern brugeradgang på gruppen/webstedet/teamet ved at angive relaterede gruppeindstillinger:
    1. I [Microsoft 365 Overholdelsescenter du](https://compliance.microsoft.com) vælge **fanen Websteder og** grupper.
    2. Rediger et dokument eller en mails følsomhedsmærkat.

## <a name="sample-script"></a>Eksempel på script

Hvis du vil have et eksempel på et script til at overføre grupper med klassiske AAD til følsomhedsmærkater, skal du [se Klassisk Azure AD-gruppeklassifikation](./sensitivity-labels-teams-groups-sites.md#classic-azure-ad-group-classification).