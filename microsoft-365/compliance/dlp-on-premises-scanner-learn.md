---
title: Få mere at vide om scanner til forebyggelse af datatab i det lokale miljø
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: conceptual
f1_keywords:
- ms.o365.cc.DLPLandingPage
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
search.appverid:
- MET150
description: Scanneren til forebyggelse af datatab udvider overvågningen af filaktiviteter og beskyttende handlinger for disse filer til filshares i det lokale miljø og SharePoint-mapper og dokumentbiblioteker. Filer scannes og beskyttes af AIP-scanner (Azure Information Protection)
ms.openlocfilehash: 8edf472fe65380b708a833864ccceedadb240191
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66629811"
---
# <a name="learn-about-the-data-loss-prevention-on-premises-scanner"></a>Få mere at vide om forebyggelse af datatab i det lokale miljø

Forebyggelse af datatab i det lokale miljø er en del af DLP-pakken (Microsoft Purview Forebyggelse af datatab), som du kan bruge til at finde og beskytte følsomme elementer på tværs af Microsoft 365-tjenester. Du kan finde flere oplysninger om alle Microsofts DLP-tilbud under [Få mere at vide om forebyggelse af datatab](dlp-learn-about-dlp.md).

**DLP-scanneren** i det lokale miljø gennemsøger inaktive data i det lokale miljø i filshares og SharePoint-dokumentbiblioteker og -mapper for følsomme elementer, der, hvis de blev lækket, ville udgøre en risiko for din organisation eller udgøre en risiko for overtrædelse af politikken for overholdelse af angivne standarder. Dette giver dig den synlighed og kontrol, du har brug for, for at sikre, at følsomme elementer bruges og beskyttes korrekt, og for at forhindre risikable funktionsmåder, der kan kompromittere dem. DLP-scanneren i det lokale miljø registrerer følsomme oplysninger ved hjælp af [indbyggede](sensitive-information-type-entity-definitions.md) eller [brugerdefinerede typer følsomme oplysninger](create-a-custom-sensitive-information-type.md) , [følsomhedsmærkater](sensitivity-labels.md) eller filegenskaber. Oplysningerne om, hvad brugerne foretager sig med følsomme elementer, gøres synlige i [Aktivitetsoversigt,](data-classification-activity-explorer.md) og du kan gennemtvinge beskyttende handlinger på disse elementer via [DLP-politikker](create-test-tune-dlp-policy.md).

## <a name="the-dlp-on-premises-scanner-relies-on-azure-information-protection-scanner"></a>DLP-scanneren i det lokale miljø er afhængig af Azure Information Protection-scanneren

DLP-scanneren i det lokale miljø er afhængig af en komplet implementering af Azure Information Protection-scanneren (AIP) til at overvåge, navngive og beskytte følsomme elementer. Hvis du ikke er bekendt med AIP-scanneren, anbefaler vi på det kraftigste, at du bliver fortrolig med den. Se disse artikler:

- [Hvad er Azure Information Protection](/azure/information-protection/what-is-information-protection)
- [Hvad er Azure Information Protection Unified Labeling Scanner](/azure/information-protection/deploy-aip-scanner)
- [Krav til installation og installation af Azure Information Protection Unified Labeling Scanner](/azure/information-protection/deploy-aip-scanner-prereqs)
- [Selvstudium: Installation af Azure Information Protection (AIP) Unified Labeling Scanner](/azure/information-protection/tutorial-install-scanner)
- [Konfiguration og installation af Azure Information Protection Unified Labeling Scanner](/azure/information-protection/deploy-aip-scanner-configure-install)
- [Azure Information Protection unified labeling client – Versionsudgivelseshistorik og supportpolitik](/azure/information-protection/rms-client/unifiedlabelingclient-version-release-history)

## <a name="dlp-on-premises-scanner-actions"></a>DLP-scannerhandlinger i det lokale miljø

DLP-scanner i det lokale miljø registrerer filer ved hjælp af en af disse fire metoder:

- følsomme oplysningstyper
- følsomhedsmærkater
- filtypenavn
- brugerdefinerede dokumentegenskaber kun for Office-filer 

Når en registreret fil udgør en potentiel risiko, hvis den er lækket, eller der er en overtrædelse af politikken for overholdelse af angivne standarder, kan DLP-scanneren i det lokale miljø foretage en af disse fire handlinger.

|Handling |Beskrivelse  |
|---------|---------|
|**Bloker disse personer fra at få adgang til den fil, der er gemt i scanneren i det lokale miljø – alle** | Når denne handling gennemtvinges, blokerer den adgangen til alle konti undtagen ejeren af indholdet, den sidste konto, der ændrede elementet, og administratoren. Det gør den ved at fjerne alle konti fra NTFS-/SharePoint-tilladelser på filniveau undtagen filejeren, lagerejeren (angivet i indstillingen [Angiv lagerejer](/azure/information-protection/deploy-aip-scanner-configure-install#use-a-data-loss-prevention-dlp-policy-public-preview) i indholdsscanningsjobbet), sidste ændringsfunktion (kan kun identificeres i SharePoint) og administrator. Scannerkontoen tildeles også FC-rettigheder til filen.|
|**Bloker disse personer fra at få adgang til filer, der er gemt i scanneren i det lokale miljø – bloker organisationsbaseret (offentlig) adgang**    |Når denne handling gennemtvinges, fjernes SID'erne **_Alle_*_, _*_NT AUTHORITY\godkendte brugere_*_ og _*_Domænebrugere_** fra filadgangskontrollisten (ACL). Kun brugere og grupper, der eksplicit er tildelt rettigheder til filen eller den overordnede mappe, kan få adgang til filen.|
|**Angiv tilladelser til filen**|Når denne handling gennemtvinges, tvinger den filen til at nedarve tilladelserne til den overordnede mappe. Som standard gennemtvinges denne handling kun, hvis tilladelserne til den overordnede mappe er mere restriktive end de tilladelser, der allerede findes i filen. Hvis ACL'en for filen f.eks. er indstillet til kun at tillade **_bestemte brugere_*_, og den overordnede mappe er konfigureret til at tillade _*_Domænebrugere_*_-gruppen, nedarves tilladelserne til den overordnede mappe ikke af filen. Du kan tilsidesætte denne funktionsmåde ved at vælge indstillingen _* Nedarv, selvom overordnede tilladelser er mindre restriktive** .|
|**Fjern filen fra en forkert placering**|Når denne handling gennemtvinges, erstattes den oprindelige fil med en stubfil med .txt filtypenavn og placerer en kopi af den oprindelige fil i en karantænemappe. 

## <a name="whats-different-in-the-on-premises-scanner"></a>Hvad er anderledes i scanneren i det lokale miljø

Der er et par ekstra begreber, som du skal være opmærksom på, før du går i dybden med scanneren i det lokale miljø.

### <a name="aip-repositories-and-content-scan-jobs"></a>AIP-lagre og job til indholdsscanning

Du skal oprette et AIP-indholdsscanningsjob og identificere de lagre, der er vært for de filer, du vil evaluere af DLP-programmet. Sørg for at aktivere DLP-regler i det oprettede AIP-indholdsscanningsjob.

### <a name="policy-tips"></a>Tip til politik

[Politiktips](use-notifications-and-policy-tips.md) er ikke tilgængelige i scanneren i det lokale miljø.


### <a name="viewing-dlp-on-premises-scanner-events"></a>Visning af DLP-scannerhændelser i det lokale miljø

Du får vist DLP-scannerdata i det lokale miljø i [aktivitetsoversigten](data-classification-activity-explorer.md) for M365 Compliance Center. 

## <a name="next-steps"></a>Næste trin

Nu, hvor du har lært om DLP-scanner i det lokale miljø, er dine næste trin:

1. [Kom i gang med DLP-scanneren i det lokale miljø](dlp-on-premises-scanner-get-started.md)
2. [Brug DLP-scanneren i det lokale miljø](dlp-on-premises-scanner-use.md)

## <a name="see-also"></a>Se også

- [Introduktion til forebyggelse af datatab i det lokale miljø](dlp-on-premises-scanner-get-started.md)
- [Brug scanneren til forebyggelse af datatab i det lokale miljø](dlp-on-premises-scanner-use.md)
- [Få mere at vide om forebyggelse af datatab](dlp-learn-about-dlp.md)
- [Opret, test og finjuster en DLP-politik](create-test-tune-dlp-policy.md)
- [Kom i gang med Aktivitetsoversigt](data-classification-activity-explorer.md)
