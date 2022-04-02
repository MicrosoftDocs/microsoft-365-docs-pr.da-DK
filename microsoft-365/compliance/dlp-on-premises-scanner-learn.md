---
title: Få mere Microsoft 365 om lokal scanner til forebyggelse af datatab
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
description: Microsoft 365 forebyggelse af datatab i det lokale miljø udvider overvågning af filaktiviteter og beskyttende handlinger for disse filer til lokale filshares og SharePoint-mapper og dokumentbiblioteker. Filer scannes og beskyttes af Azure Information Protection (AIP)-scanneren
ms.openlocfilehash: c696d4c4e8504d07ce69554c6ff52f264b8ba491
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63602994"
---
# <a name="learn-about-the-microsoft-365-data-loss-prevention-on-premises-scanner"></a>Få mere at vide Microsoft 365 lokal scanner til forebyggelse af datatab

Microsofts lokale scanner til forebyggelse af datatab er en del af Microsoft 365 DLP-pakken (forebyggelse af datatab), som du kan bruge til at opdage og beskytte følsomme elementer på tværs af Microsoft 365-tjenester. Du kan finde flere oplysninger om alle Microsofts DLP-tilbud i [Få mere at vide om forebyggelse af datatab](dlp-learn-about-dlp.md).

Den **lokale DLP-scanner** gennemsøger lokale data i filshares og SharePoint-dokumentbiblioteker og mapper for følsomme elementer, der, hvis de er sivet ud, udgør en risiko for din organisation eller udgør en risiko for overtrædelse af overholdelsespolitikken. Dette giver dig den synlighed og kontrol, du skal bruge for at sikre, at følsomme elementer bruges og beskyttes korrekt, og for at forhindre risikabel adfærd, der kan kompromittere dem. Den lokale DLP-scanner registrerer følsomme oplysninger ved hjælp af [indbyggede](sensitive-information-type-entity-definitions.md) eller brugerdefinerede typer [](create-a-custom-sensitive-information-type.md) af følsomme oplysninger, [følsomhedsmærkater](sensitivity-labels.md) eller filegenskaber. Oplysningerne om, hvad brugerne foretager sig med følsomme elementer, gøres synlige i [](data-classification-activity-explorer.md) Aktivitetsstifinder, og du kan gennemtvinge beskyttende handlinger for disse elementer via [DLP-politikker](create-test-tune-dlp-policy.md).

## <a name="the-dlp-on-premises-scanner-relies-on-azure-information-protection-scanner"></a>Den lokale DLP-scanner afhænger af Azure Information Protection-scanneren

Den lokale DLP-scanner er afhængig af en fuld implementering af Azure Information Protection -scanneren (AIP) til at overvåge, mærke og beskytte følsomme elementer. Hvis du ikke kender AIP-scanneren, anbefaler vi, at du gør dig bekendt med den. Se følgende artikler:

- [Hvad er Azure Information Protection?](/azure/information-protection/what-is-information-protection)
- [Hvad er Den samlede Azure Information Protection-etiketscanner](/azure/information-protection/deploy-aip-scanner)
- [Krav til installation og installation af en samlet Azure Information Protection-scanner til mærkning](/azure/information-protection/deploy-aip-scanner-prereqs)
- [Selvstudium: Installation af en samlet Azure Information Protection -scanner (AIP)](/azure/information-protection/tutorial-install-scanner)
- [Konfiguration og installation af den samlede Azure Information Protection-etiketscanner](/azure/information-protection/deploy-aip-scanner-configure-install)
- [Azure Information Protection samlet etiketklient – versionsudgivelsesoversigt og supportpolitik](/azure/information-protection/rms-client/unifiedlabelingclient-version-release-history)

## <a name="dlp-on-premises-scanner-actions"></a>Lokale DLP-scannerhandlinger

DLP-scanner i det lokale miljø registrerer filer med en af disse fire metoder:

- typer af følsomme oplysninger
- følsomhedsmærkater
- filtypenavn
- Brugerdefinerede dokumentegenskaber Office filer 

Når en registreret fil udgør en potentiel risiko ved lækage eller en overtrædelse af overholdelsespolitikken, kan den lokale DLP-scanner udføre en af disse fire handlinger.

|Handling |Beskrivelse  |
|---------|---------|
|**Bloker disse personer fra at få adgang til filer, der er gemt i en lokal scanner – Alle** | Når dette gennemtvinges, blokerer denne handling adgangen til alle konti undtagen ejeren af indholdet, den sidste konto, der ændrede elementet og administratoren. Det gør programmet ved at fjerne alle konti fra NTFS/SharePoint-tilladelser på filniveau undtagen filejeren, lagerejeren (angivet i indstillingen Angiv lagerejer [](/azure/information-protection/deploy-aip-scanner-configure-install#use-a-data-loss-prevention-dlp-policy-public-preview) i indholdsscanningsjob), den sidste ændring (kan kun identificeres i SharePoint) og administrator. Scannerkontoen tildeles også FC-rettigheder til filen.|
|**Bloker disse personer fra at få adgang til filer, der er gemt i en lokal scanner – bloker adgang for hele organisationen (offentlig)**    |Når gennemtvinges, fjerner denne handling ALLE ***_, _*_NT AUTHORITY\godkendte_ brugere *_ og _*_Domain Users-SID'er_** fra filadgangskontrollisten (ACL). Kun brugere og grupper, der udtrykkeligt har fået rettigheder til filen eller den overordnede mappe, vil kunne få adgang til filen.|
|**Angive tilladelser på filen**|Når filen gennemtvinges, tvinger den filen til at nedarve tilladelserne for dens overordnede mappe. Som standard gennemtvinges denne handling kun, hvis tilladelserne på den overordnede mappe er mere restriktive end de tilladelser, der allerede findes på filen. Hvis F.eks. ACL på filen er indstillet til kun at tillade bestemte brugere_, og den overordnede mappe er konfigureret til at tillade ***_*_Domain Users_ _group, nedarves tilladelserne for den overordnede mappe ikke af *filen. Du kan tilsidesætte denne funktionsmåde ved at vælge indstillingen _* Nedarvning, selvom overordnede tilladelser er mindre restriktive**.|
|**Fjern filen fra forkert placering**|Når gennemtvinges, erstatter denne handling den oprindelige fil med en stub-fil med .txt-filtypenavn og placerer en kopi af den oprindelige fil i en karantænemappe. 

## <a name="whats-different-in-the-on-premises-scanner"></a>Hvad er anderledes i den lokale scanner

Der er et par ekstra begreber, du skal være opmærksom på, før du graver dig ind i den lokale scanner.

### <a name="aip-repositories-and-content-scan-jobs"></a>AIP-lagre og indholdsscanningsjob

Du skal oprette en AIP-indholdsscanningsjob og identificere de lagre, der hoster de filer, der skal evalueres af DLP-programmer. Sørg for, at du aktiverer DLP-regler i det oprettede AIP-indholdsscanningsjob.

### <a name="policy-tips"></a>Politiktip

[Politiktip](use-notifications-and-policy-tips.md) er ikke tilgængelige i en lokal scanner.


### <a name="viewing-dlp-on-premises-scanner-events"></a>Visning af lokale DLP-scannerhændelser

Du får vist lokale DLP-scannerdata i aktivitetsstifinderen M365 [Compliance Center](data-classification-activity-explorer.md). 

## <a name="next-steps"></a>Næste trin

Nu hvor du har lært om den lokale DLP-scanner, er de næste trin:

1. [Introduktion til den lokale DLP-scanner](dlp-on-premises-scanner-get-started.md)
2. [Brug den lokale DLP-scanner](dlp-on-premises-scanner-use.md)

## <a name="see-also"></a>Se også

- [Introduktion til den lokale Microsoft-scanner til forebyggelse af datatab](dlp-on-premises-scanner-get-started.md)
- [Brug en lokal Microsoft-scanner til forebyggelse af datatab](dlp-on-premises-scanner-use.md)
- [Få mere at vide om forebyggelse af datatab](dlp-learn-about-dlp.md)
- [Opret, test og finjuster en DLP-politik](create-test-tune-dlp-policy.md)
- [Introduktion til Aktivitetsstifinder](data-classification-activity-explorer.md)