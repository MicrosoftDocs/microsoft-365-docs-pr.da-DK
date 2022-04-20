---
title: Erklær data ved hjælp af opbevaringsmærkater
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
description: Deklarer poster ved hjælp af opbevaringsmærkater.
ms.openlocfilehash: 23dd6c61d9da787eecd2e1fa825fe338d961d1d1
ms.sourcegitcommit: 1d972f15a45204e89e268c5ff257021aced5e775
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/18/2022
ms.locfileid: "64911449"
---
# <a name="declare-records-by-using-retention-labels"></a>Erklær data ved hjælp af opbevaringsmærkater

>*[Microsoft 365 licensvejledning til sikkerhed & overholdelse af angivne standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Hvis du vil deklarere dokumenter og mails som [poster](records-management.md#records), skal du bruge [opbevaringsmærkater](retention.md#retention-labels) , der markerer indholdet som en **post** eller en **lovmæssig post**.

Hvis du ikke er sikker på, om du vil bruge en post eller en lovmæssig post, skal du se [Sammenlign begrænsninger for, hvilke handlinger der er tilladt eller blokeret](records-management.md#compare-restrictions-for-what-actions-are-allowed-or-blocked). Hvis du har brug for at bruge lovmæssige poster, skal du først køre en PowerShell-kommando, som beskrevet i næste afsnit.

Du kan derefter enten publicere disse mærkater i en politik for opbevaringsmærkater, så brugere og administratorer kan anvende dem på indhold eller for etiketter, der markerer elementer som poster (men ikke lovmæssige poster), automatisk anvende disse mærkater på indhold, som du vil deklarere en post.

## <a name="how-to-display-the-option-to-mark-content-as-a-regulatory-record"></a>Sådan får du vist muligheden for at markere indhold som en lovmæssig post

> [!NOTE]
> Følgende procedure er en handling, der kan overvåges, og logføring **af indstillingen Aktiveret lovgivningsmæssig post for opbevaringsmærkater** i afsnittet [Opbevaringspolitik og aktiviteter med opbevaringsmærkater](search-the-audit-log-in-security-and-compliance.md#retention-policy-and-retention-label-activities) i overvågningsloggen.

Indstillingen for opbevaringsmærkat til markering af indhold som en lovmæssig post vises som standard ikke i guiden til opbevaringsmærkater. Hvis du vil have vist denne indstilling, skal du først køre en PowerShell-kommando:

1. [Forbind til PowerShell Office 365 Security & Compliance Center](/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell).

2. Kør følgende cmdlet:

    ```powershell
    Set-RegulatoryComplianceUI -Enabled $true
    ````

    Der er ingen prompt om at bekræfte, og indstillingen træder i kraft med det samme.

Hvis du skifter mening om at få vist denne indstilling i guiden til opbevaringsmærkat, kan du skjule den igen ved at køre den samme cmdlet med værdien **falsk** : `Set-RegulatoryComplianceUI -Enabled $false`

## <a name="configuring-retention-labels-to-declare-records"></a>Konfiguration af opbevaringsmærkater for at deklarere poster

Når du opretter en opbevaringsmærkat fra løsningen **Datastyring** i Microsoft 365 Overholdelsescenter, kan du vælge indstillingen **Markér elementer som en post**. Som en ekstra mulighed, der i øjeblikket udrulles som prøveversion, kan du låse posten op som standard for SharePoint og OneDrive.

Den ekstra indstilling **Lås denne post op som standard** giver brugerne mulighed for effektivt at deklarere poster, fordi de låser posten, når de er færdige med at redigere indholdet. Du kan få flere oplysninger om dette understøttede scenarie under [Brug postversionsstyring til at opdatere poster, der er gemt i SharePoint eller OneDrive](record-versioning.md).

Hvis du kørte PowerShell-kommandoen fra det forrige afsnit, kan du alternativt markere elementer som en lovmæssig post.

Eksempel:

![Konfigurer en opbevaringsmærkat for at markere indhold som en post eller lovgivningsmæssig.](../media/declare-records.png)

Ved hjælp af denne opbevaringsmærkat kan du nu anvende den på SharePoint eller OneDrive dokumenter og Exchange mails efter behov.

Hvis du vil have en komplet vejledning:

- [Publicer opbevaringsmærkater, og anvend dem i apps](create-apply-retention-labels.md)

- [Anvend automatisk en opbevaringsmærkat på indhold](apply-retention-labels-automatically.md) (understøttes ikke for lovmæssige poster)

## <a name="tenant-setting-for-editing-record-properties"></a>Lejerindstilling for redigering af postegenskaber

Hvis du vil bruge opbevaringsmærkater til at deklarere elementer som poster (i stedet for lovmæssige poster) i SharePoint og OneDrive skal du overveje, om du skal ændre standardindstillingen for lejeren, der giver brugerne mulighed for at redigere egenskaberne for en [låst post](record-versioning.md), når filer er større end 0 byte.

Hvis du vil ændre denne standard, skal du gå til indstillingerne [for administration af Microsoft 365 Overholdelsescenter](https://compliance.microsoft.com/) >  **PostadministrationAdministrationsnavneTillad** >  >  >  **redigering af postegenskaber** og derefter deaktivere indstillingen **Tillad brugere at redigere postegenskaber**.

## <a name="applying-the-configured-retention-label-to-content"></a>Anvendelse af den konfigurerede opbevaringsmærkat på indhold

Når opbevaringsmærkater, der markerer elementer som en post eller lovgivningsmæssig post, gøres tilgængelige for brugere, så de kan anvende dem i apps:

- For Exchange kan alle brugere med skriveadgang til postkassen anvende disse mærkater.
- For SharePoint og OneDrive kan alle brugere i standardgruppen Medlemmer (tilladelsesniveauet Bidrag) anvende disse mærkater.

Eksempel på et dokument, der er markeret som en post ved hjælp af en opbevaringsmærkat:

![Detaljerude for dokument, der er mærket som en post.](../media/recordversioning7.png)

## <a name="searching-the-audit-log-for-labeled-items-that-were-declared-records"></a>Søger i overvågningsloggen efter navngivne elementer, der er defineret som poster

Handlingerne for at navngive for at deklarere elementer som poster logføres i overvågningsloggen.

For SharePoint elementer:
- Fra **Fil- og sideaktiviteter** skal du vælge **Ændret opbevaringsmærkat for en fil**. Denne overvågningshændelse er for opbevaringsmærkater, der markerer elementer som poster, lovmæssige poster, eller som er standardopbevaringsmærkater.

For Exchange elementer:
- Fra **Exchange postkasseaktiviteter** skal du vælge **Markeret meddelelse som en post**. Denne overvågningshændelse er for opbevaringsmærkater, der markerer elementer som poster eller lovmæssige poster.

Du kan finde flere oplysninger om søgning efter disse hændelser i [Søg i overvågningsloggen i Security & Compliance Center](search-the-audit-log-in-security-and-compliance.md#file-and-page-activities).

## <a name="next-steps"></a>Næste trin

Forstå, hvordan du kan bruge [postversionsstyring til at opdatere poster, der er gemt i SharePoint eller OneDrive](record-versioning.md).