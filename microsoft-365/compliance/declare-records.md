---
title: Erklære poster ved hjælp af opbevaringsnavne
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
description: Erklære poster ved hjælp af opbevaringsetiketter.
ms.openlocfilehash: 93e51698109819f4743dd4b5b45f5a5177739a2a
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63591385"
---
# <a name="declare-records-by-using-retention-labels"></a>Erklære poster ved hjælp af opbevaringsnavne

>*[Microsoft 365 licenseringsvejledning til sikkerhed og & overholdelse af regler og standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Hvis du vil erklære dokumenter og mails [som poster](records-management.md#records), skal du [bruge opbevaringsetiketter](retention.md#retention-labels) , der markerer indholdet som **en post** eller en **lovgivningsmæssig post**.

Hvis du ikke er sikker på, om du vil bruge en post eller en lovgivningspost, kan du se Sammenlign begrænsninger [for, hvilke handlinger der er tilladte eller blokerede](records-management.md#compare-restrictions-for-what-actions-are-allowed-or-blocked). Hvis du skal bruge lovgivningsposter, skal du først køre en PowerShell-kommando, som beskrevet i næste afsnit.

Derefter kan du enten publicere disse etiketter i en opbevaringsetiketpolitik, så brugere og administratorer kan anvende dem på indhold eller på etiketter, der markerer elementer som poster (men ikke lovgivningsmæssige poster), ved automatisk at anvende disse etiketter på indhold, du vil erklære en post.

## <a name="how-to-display-the-option-to-mark-content-as-a-regulatory-record"></a>Sådan får du vist muligheden for at markere indhold som en lovgivningspost

> [!NOTE]
> Følgende procedure er en handling, der kan overvåges, logføring Aktiveret lovgivningspostindstilling [](search-the-audit-log-in-security-and-compliance.md#retention-policy-and-retention-label-activities) **for** opbevaringsnavne i sektionen Opbevaringspolitik og opbevaringsetiketaktiviteter i overvågningsloggen.

Som standard vises indstillingen for opbevaringsetiket til at markere indhold som en lovgivningspost ikke i guiden til opbevaringsetiket. For at få vist denne indstilling skal du først køre en PowerShell-kommando:

1. [Forbind til Office 365 Security & Compliance Center PowerShell](/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell).

2. Kør følgende cmdlet:

    ```powershell
    Set-RegulatoryComplianceUI -Enabled $true
    ````

    Der er ingen prompt om at bekræfte, og indstillingen træder i kraft med det samme.

Hvis du skifter mening om at få vist denne indstilling i guiden til opbevaringsnavn, kan du skjule den igen ved at køre den samme cmdlet med **den falske** værdi: `Set-RegulatoryComplianceUI -Enabled $false`

## <a name="configuring-retention-labels-to-declare-records"></a>Konfiguration af opbevaringsnavne til erklæring af poster

Når du opretter et opbevaringsnavn **fra løsningen** Datastyring i Microsoft 365 Overholdelsescenter, har du mulighed for at markere elementer som en post. Hvis du kørte PowerShell-kommandoen fra det forrige afsnit, kan du alternativt markere elementer som en lovoptegnelse.

Eksempel:

![Konfigurer en opbevaringsetiket for at markere indhold som en post eller lovgivning.](../media/recordversioning6.png)

Med denne opbevaringsetiket kan du nu anvende den på SharePoint eller OneDrive dokumenter og Exchange efter behov.

Du kan få den fulde vejledning:

- [Opret opbevaringsnavne, og anvend dem i apps](create-apply-retention-labels.md)

- [Anvend automatisk en opbevaringsetiket på indhold](apply-retention-labels-automatically.md) (understøttes ikke for lovgivningsposter)

## <a name="tenant-setting-for-editing-record-properties"></a>Lejerindstilling til redigering af postegenskaber

Hvis du vil bruge opbevaringsnavne til at erklære elementer som poster (i stedet for lovgivningsposter) i SharePoint og OneDrive, skal du overveje, om du vil ændre standardindstillingen for lejeren, der giver brugerne mulighed for at redigere [](record-versioning.md) egenskaberne for en låst post, når filer er større end 0 byte.

Hvis du vil ændre denne standard, skal du gå til [Microsoft 365 Overholdelsescenter](https://compliance.microsoft.com/) >  PoststyringIndstillinger for administrationRetention-navneStilgræns >  >  >  redigering af postegenskaber og derefter deaktivere indstillingen Tillad brugere at redigere postegenskaber **.**

## <a name="applying-the-configured-retention-label-to-content"></a>Anvendelse af den konfigurerede opbevaringsetiket på indhold

Når opbevaringsnavne, der markerer elementer som en post eller lovgivningsmæssig post, gøres tilgængelige for brugerne, så de kan anvende dem i apps:

- For Exchange kan alle brugere med skriveadgang til postkassen anvende disse etiketter.
- For SharePoint og OneDrive kan alle brugere i standardgruppen Medlemmer (tilladelsesniveauet Bidrage) anvende disse etiketter.

Eksempel på et dokument, der er markeret som post, ved hjælp af en opbevaringsetiket:

![Detaljeruden for dokument, der er mærket som en post.](../media/recordversioning7.png)

## <a name="searching-the-audit-log-for-labeled-items-that-were-declared-records"></a>Søgning i overvågningsloggen efter navneelementer, der blev erklæret poster

Handlingerne for at angive elementer som poster logføres i overvågningsloggen.

For SharePoint elementer:
- Fra **Fil- og sideaktiviteter skal** du vælge **Ændret opbevaringsmærkat for en fil**. Denne overvågningshændelse er for opbevaringsnavne, der markerer elementer som poster, lovmæssige poster, eller som er standardopbevaringsnavne.

For Exchange elementer:
- Fra **Exchange postkasseaktiviteter** skal du **vælge Mærket meddelelse som en post**. Denne overvågningshændelse er for opbevaringsnavne, der markerer elementer som poster eller lovgivningsposter.

Du kan finde flere oplysninger om søgning efter disse hændelser [i Søg i overvågningsloggen i Security & Compliance Center](search-the-audit-log-in-security-and-compliance.md#file-and-page-activities).

## <a name="next-steps"></a>Næste trin

Forstå, hvordan du kan bruge [postversionering til at opdatere poster, der er gemt i SharePoint eller OneDrive](record-versioning.md).