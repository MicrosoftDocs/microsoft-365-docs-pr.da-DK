---
title: Rapportér spam, ikke-spam, phishing, mistænkelige mails og filer til Microsoft
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: overview
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: c31406ea-2979-4fac-9288-f835269b9d2f
ms.collection:
- M365-security-compliance
description: Hvordan gør jeg rapportere en mistænkelig mail eller fil til Microsoft? Rapportmeddelelser, URL-adresser, vedhæftede filer i mails og filer til Analyse til Microsoft. Få mere at vide om, hvordan du rapporterer spammails og phishing-mails.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 3ccb01e63011b48fa341b7ce3198b05505940a01
ms.sourcegitcommit: c314e989202dc1c9c260fffd459d53bc1f08514e
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/12/2022
ms.locfileid: "66717774"
---
# <a name="how-do-i-report-a-suspicious-email-or-file-to-microsoft"></a>Hvordan gør jeg rapportere en mistænkelig mail eller fil til Microsoft?

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Spekulerer du på, hvad du skal gøre med mistænkelige mails eller filer? I Microsoft 365-organisationer med postkasser i Exchange Online eller enkeltstående EOP-organisationer (Exchange Online Protection) uden Exchange Online postkasser har *brugere* og *administratorer* forskellige måder at rapportere en mistænkelig mail, URL-adresse eller vedhæftet mail til Microsoft på.

Derudover har Microsoft 365-organisationer med Microsoft Defender for Endpoint administratorer også flere metoder til rapportering af filer.

Se denne video, der viser flere oplysninger om oplevelsen med samlede indsendelser.
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE50HhM]

## <a name="report-a-suspicious-email-to-microsoft"></a>Rapportér en mistænkelig mail til Microsoft

|Metode|Beskrivelse|
|---|---|
|[Brug portalen Indsendelser til at sende mistanke om spam, phish, URL-adresser og vedhæftede filer i mails til Microsoft](admin-submission.md)|Den anbefalede rapporteringsmetode for administratorer i organisationer med Exchange Online postkasser (ikke tilgængelig i enkeltstående EOP).|
|[Aktivér rapportmeddelelsen eller tilføjelsesprogrammer til rapport phishing](enable-the-report-message-add-in.md)|Fungerer sammen med Outlook og Outlook på internettet (tidligere kaldet Outlook Web App). <br/><br/> Afhængigt af dit abonnement er meddelelser, som brugere har rapporteret med tilføjelsesprogrammer, tilgængelige på [portalen Administration Indsendelser](admin-submission.md), [resultaterne af automatiseret undersøgelse og svar (AIR),](air-view-investigation-results.md) [rapporten over brugerrapporterede meddelelser](view-email-security-reports.md#user-reported-messages-report) og [Stifinder](threat-explorer-views.md#email--submissions). <br/><br/> Du kan konfigurere rapporterede meddelelser til at blive kopieret eller omdirigeret til en postkasse, som du angiver. Du kan få flere oplysninger under [Politikker for brugerindsendelser](user-submission.md).
|[Rapportér falske positiver og falske negativer i Outlook](report-false-positives-and-false-negatives.md)|Send falske positiver (god mail, der er blokeret eller sendt til mappen med uønsket post) og falske negativer (uønsket mail eller phish, der blev leveret til indbakken) for at Exchange Online Protection (EOP) ved hjælp af funktionen Rapportmeddelelse.|
|[Brug regler for mailflow til at se, hvad brugerne rapporterer til Microsoft](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-see-what-users-are-reporting-to-microsoft)|Få mere at vide om, hvordan du opretter en regel for mailflow (også kaldet en transportregel), der giver dig besked, når brugerne rapporterer meddelelser til Microsoft til analyse.|
|[Send mistænkelige filer til Microsoft til analyse](submitting-malware-and-non-malware-to-microsoft-for-analysis.md)|Brug det Microsoft Sikkerhedsviden websted til at sende vedhæftede filer og andre filer.|

> [!NOTE]
> Når du rapporterer en mailenhed til Microsoft, opretter vi en kopi af alt, der er knyttet til mailen, for at inkludere den i vores løbende algoritmegennemgange. Denne kopi indeholder mailindholdet, mailheaderne og relaterede data om maildistributionen. Vedhæftede filer i meddelelsen er også inkluderet.
>
> Microsoft behandler din feedback som din organisations tilladelse til at analysere alle de tidligere beskrevne oplysninger og arbejde på at finjustere algoritmerne for meddelelseshygiejne. Vi holder din besked i vores sikre overvågede datacentre i USA, indtil vi sletter din indsendelse senest 30 dage efter, at du har leveret den til os. Personale hos Microsoft kan læse din indsendte meddelelse og vedhæftede filer, hvilket normalt ikke er tilladt for mail i Office 365. Din mail behandles dog stadig som fortroligt mellem dig og Microsoft, og vi sender ikke din indsendelse til nogen anden part for at læse mailen eller dens vedhæftede filer til denne korrekturproces.
