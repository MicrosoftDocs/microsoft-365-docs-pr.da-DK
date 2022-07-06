---
title: AAD-klassificering og følsomhedsmærkater for Microsoft 365-grupper
ms.reviewer: vijagan
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
f1.keywords: NOCSH
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
description: I denne artikel beskrives klassisk Azure Active Directory-klassificering og følsomhedsmærkater.
ms.openlocfilehash: 260b71d703f2534e5e2ddcf4ef45fe28a914eeab
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66623777"
---
# <a name="azure-active-directory-classification-and-sensitivity-labels-for-microsoft-365-groups"></a>Azure Active Directory-klassificering og følsomhedsmærkater for Microsoft 365-grupper

I denne artikel beskrives klassisk Azure Active Directory-klassificering og følsomhedsmærkater.

Følsomhedsmærkater understøttes af [disse tjenester](./sensitivity-labels-teams-groups-sites.md).

Du kan finde komplette oplysninger om følsomhedsmærkater under [Få mere at vide om følsomhedsmærkater](sensitivity-labels.md).

Hvis du vil vide mere om følsomhedsmærkater og deres funktionsmåde for websteder og Microsoft 365-grupper, skal du se [Brug følsomhedsmærkater til at beskytte indhold i Microsoft Teams, Microsoft 365-grupper og SharePoint-websteder](sensitivity-labels-teams-groups-sites.md).

Se følgende scenarier for at få de bedste fremgangsmåder ved overførsel fra klassisk AAD-klassificering til følsomhedsmærkater.

## <a name="scenario-1-tenant-never-used-classic-aad-classifications-or-sensitivity-labels-for-documents-and-emails"></a>Scenarie 1: Lejer har aldrig brugt klassiske AAD-klassificeringer eller følsomhedsmærkater til dokumenter og mails

- Lejer Administration aktiverer følsomhedsmærkater for grupper ved at angive lejerflaget "EnableMIPLabels" til true via AAD powershell-cmdlet.
- Lejer Administration opretter følsomhedsmærkater i [Microsoft Purview-compliance-portal](https://compliance.microsoft.com).
    - Lejeradministratoren kan vælge fil- og mailrelaterede handlinger, f.eks. kryptering og vandmærke.
    - Lejeradministratoren kan vælge Microsoft 365-grupper- og SharePoint Online-webstedsrelaterede handlinger til følsomhedsmærkater.
- Lejeren Administration publicerer politikken.
- **Kompatible arbejdsbelastninger viser følsomhedsmærkater** . Brug følsomhedsmærkater til at oprette grupper. Kompatible arbejdsbelastninger er de tjenester, der understøtter følsomhedsmærkater.
- **Ikke-kompatible arbejdsbelastninger** er de tjenester, der endnu ikke understøtter følsomhedsmærkater. Grupper kan oprettes, men de kan ikke knyttes til følsomhedsmærkaten via ikke-kompatible arbejdsbelastninger. Hvis du vil knytte sådanne grupper til følsomhedsmærkater, kan lejeradministratorer køre PowerShell-cmdlet'er.

Tabel 1. Funktionsmåde for kompatible og ikke-kompatible arbejdsbelastninger – opret, rediger eller slet grupper

|Arbejdsbyrde|Hvilken etiketliste kan brugeren se i gruppevinduet?|Opret ny gruppe |Rediger gruppe |Slet gruppe |
|:-------|:-------|:--------|:--------|:--------|   
|Kompatibel   |følsomhedsmærkater. |Der er ingen ændring i funktionsmåden. |Der er ingen ændring i funktionsmåden. |Der er ingen ændring i funktionsmåden. |
|Ikke-kompatibel |Der er ingen synlige følsomhedsmærkater. |Brugeren kan oprette en gruppe uden at vælge følsomhedsmærkat. <br><br> Bemærk, at administratoren kan køre cmdlet'er for at anvende følsomhedsmærkater i baggrunden. |**Sag 1**: Der er ikke tidligere valgt nogen følsomhedsmærkat. Brugeren kan redigere en gruppe.<br><br> **Case 2**: Følsomhedsmærkat anvendt tidligere i baggrunden ved hjælp af cmdlet. Brugeren kan redigere en gruppe med undtagelse af det tilfælde, hvor brugeren vælger en ugyldig kombination af indstillinger for beskyttelse af personlige oplysninger med hensyn til mærkaten. |Der er ingen ændring i funktionsmåden.|

> [!NOTE]
> I forbindelse med Outlook Desktop-klienten (Win 32), når administratoren har aktiveret følsomhedsmærkater på deres lejer, og brugeren er på en ældre version af Outlook Desktop-klienten (Win 32):
>
> - Brugeren får vist følsomhedsmærkater i den ældre version af Outlook Desktop-klienten.
> - Men når brugeren redigerer en gruppe og gemmer gruppen med en følsomhedsmærkat, tilsidesættes den valgte indstilling for beskyttelse af personlige oplysninger af indstillingen for beskyttelse af personlige oplysninger for den anvendte følsomhedsmærkat.
>
> Vi anbefaler, at brugerne på en gammel version af Outlook-klienten opgraderer til den nyere version.

## <a name="scenario-2-tenant-is-already-using-classic-aad-classifications"></a>Scenarie 2: Lejer bruger allerede klassiske [AAD-klassificeringer](../enterprise/manage-microsoft-365-groups-with-powershell.md)

### <a name="case-a-tenant-never-used-sensitivity-labels-for-documents-and-emails"></a>Sag A: Lejeren har aldrig brugt følsomhedsmærkater til dokumenter og mails

1. I [Microsoft Purview-compliance-portal](https://compliance.microsoft.com) anbefaler vi, at du opretter følsomhedsmærkater med samme navn som de eksisterende klassiske Azure AD-mærkater.
2. Brug PowerShell-cmdlet'en til at anvende disse følsomhedsmærkater på eksisterende Microsoft 365-grupper og SharePoint-websteder ved hjælp af navnetilknytning.
3. Administration kan vælge at slette de klassiske Azure AD navne:
    - Kompatible arbejdsbelastninger viser disse følsomhedsmærkater, og grupper oprettes sammen med dem.
    - Arbejdsbelastninger, der ikke er kompatible, fungerer, når du opretter grupper, men der er ikke knyttet nogen følsomhedsmærkat til dem.
4. Administratorer kan køre PowerShell-cmdlet'er for at anvende følsomhedsmærkater på disse grupper uden mærkater.
    - En administrator kan også vælge at beholde de klassiske Azure AD mærkater:
        - Kompatible arbejdsbelastninger viser disse følsomhedsmærkater, og grupper oprettes med dem. Kompatible arbejdsbelastninger er de tjenester, der understøtter følsomhedsmærkater.
        - Arbejdsbelastninger, der ikke er kompatible, fungerer, når du opretter grupper, og viser klassiske Azure AD mærkater. Disse klassiske Azure AD mærkater er knyttet til disse grupper, der er oprettet med ikke-kompatible arbejdsbelastninger.
5. Vi anbefaler på det kraftigste, at administratorer kører PowerShell-cmdlet'er for at anvende følsomhedsmærkater på disse grupper med klassiske Azure AD-mærkater.

Tabel 2. Funktionsmåde for kompatible og ikke-kompatible arbejdsbelastninger – opret, rediger eller slet grupper

|Arbejdsbyrde|Hvilken etiketliste kan brugeren se i gruppevinduet?|Opret ny gruppe |Rediger gruppe |Slet gruppe |
|:-------|:-------|:--------|:--------|:--------|   
|Kompatibel   |følsomhedsmærkater. |Der er ingen ændring i funktionsmåden. |Der er ingen ændring i funktionsmåden. |Der er ingen ændring i funktionsmåden. |
|Ikke-kompatibel |Gamle klassiske AAD-mærkater. |Brugeren kan oprette en gruppe med klassisk Azure AD markeret mærkat. <br><br>Bemærk, at administratoren kan køre cmdlet'er for at anvende følsomhedsmærkater i baggrunden. |**Sag 1**: Der er ikke tidligere valgt nogen følsomhedsmærkat. Brugeren kan redigere en gruppe.<br><br> **Sag 2**: Klassiske AAD-mærkater er tidligere valgt. Brugeren kan redigere en gruppe.<br><br> **Case 3**: Følsomhedsmærkat, der tidligere blev anvendt i baggrunden ved hjælp af cmdlet. Brugeren skal kunne redigere en gruppe, bortset fra ét tilfælde, hvor brugeren vælger en ugyldig kombination af indstillinger for beskyttelse af personlige oplysninger med hensyn til mærkaten. |Brugeren kan slette en gruppe. |

> [!NOTE]
> I forbindelse med Outlook Desktop-klienten (Win 32), når administratoren har aktiveret følsomhedsmærkater på deres lejer, og brugeren er på en ældre version af Outlook Desktop-klienten (Win 32):
>
> - Brugeren får vist følsomhedsmærkater i den ældre version af Outlook Desktop-klienten.
> - Men når brugeren redigerer en gruppe og gemmer gruppen med en følsomhedsmærkat, tilsidesættes den valgte indstilling for beskyttelse af personlige oplysninger af indstillingen for beskyttelse af personlige oplysninger for den anvendte følsomhedsmærkat.
>
> Vi anbefaler, at brugerne på en gammel version af Outlook-klienten opgraderer til den nyere version.

### <a name="case-b-tenant-used-sensitivity-labels-for-documents-and-emails"></a>Sag B: Lejer brugte følsomhedsmærkater til dokumenter og mails

1. Så snart administratoren aktiverer funktionen for følsomhedsmærkat på lejeren ved at angive lejerflaget 'EnableMIPLabels' til sand, vises dialogboksene til oprettelse og redigering af dokument- og mailfølsomhed i dialogboksene til oprettelse og redigering af gruppe/websted/team.
2. En administrator kan bruge de samme dokument- og mailfølsomhedsmærkater til at gennemtvinge beskyttelse af personlige oplysninger og ekstern brugeradgang på gruppen/webstedet/teamet ved at angive relaterede gruppeindstillinger:
    1. I [Microsoft Purview-compliance-portal](https://compliance.microsoft.com) skal du vælge fanen **Websteder og grupper**.
    2. Rediger et dokuments eller en mailfølsomhedsmærkat.

## <a name="sample-script"></a>Eksempelscript

Hvis du vil have et eksempelscript til at overføre grupper med klassiske AAD-mærkater til følsomhedsmærkater, skal [du se Klassisk Azure AD gruppeklassificering](./sensitivity-labels-teams-groups-sites.md#classic-azure-ad-group-classification).
