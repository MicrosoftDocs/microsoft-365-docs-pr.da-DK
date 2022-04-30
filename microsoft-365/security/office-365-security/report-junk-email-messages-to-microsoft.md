---
title: Rapportér spam, ikke-spam og phishing-meddelelser til Microsoft
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
description: Administratorer kan få mere at vide om de forskellige måder at rapportere gode og dårlige meddelelser og filer til Microsoft til analyse.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: d2ddd9c0d96355af1ccdbb40cdd5c7542d9852c1
ms.sourcegitcommit: 58ec09f1fd66af9717dc2743585d06d358ec7360
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/30/2022
ms.locfileid: "65144667"
---
# <a name="report-messages-and-files-to-microsoft"></a>Rapportér meddelelser og filer til Microsoft

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

I Microsoft 365 organisationer med postkasser i Exchange Online eller enkeltstående Exchange Online Protection organisationer (EOP) uden Exchange Online postkasser har både brugere og administratorer flere forskellige metoder til rapportering af mails og filer til Microsoft.

|Metode|Beskrivelse|
|---|---|
|[Brug portalen Indsendelser til at sende mistanke om spam, phish, URL-adresser og filer til Microsoft](admin-submission.md)|Den anbefalede rapporteringsmetode for administratorer i organisationer med Exchange Online postkasser (ikke tilgængelig i enkeltstående EOP).|
|[Aktivér rapportmeddelelsen eller tilføjelsesprogrammer til rapport phishing](enable-the-report-message-add-in.md)|Fungerer sammen med Outlook og Outlook på internettet (tidligere kaldet Outlook Web App). <br/><br/> Afhængigt af dit abonnement er meddelelser, som brugere har rapporteret med tilføjelsesprogrammer, tilgængelige på [portalen Administratorindsendelser](admin-submission.md), [Automatiserede undersøgelses- og svarresultater (AIR),](air-view-investigation-results.md) [rapporten over brugerrapporterede meddelelser](view-email-security-reports.md#user-reported-messages-report) og [Stifinder](threat-explorer-views.md#email--submissions). <br/><br/> Du kan konfigurere rapporterede meddelelser til at blive kopieret eller omdirigeret til en postkasse, som du angiver. Du kan få flere oplysninger under [Politikker for brugerindsendelser](user-submission.md).
|[Rapportér falske positiver og falske negativer i Outlook](report-false-positives-and-false-negatives.md)|Send falske positiver (god mail, der er blokeret eller sendt til mappen med uønsket post) og falske negativer (uønsket mail eller phish, der blev leveret til indbakken) for at Exchange Online Protection (EOP) ved hjælp af funktionen Rapportmeddelelse.|
|[Brug regler for mailflow til at se, hvad brugerne rapporterer til Microsoft](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-see-what-users-are-reporting-to-microsoft)|Få mere at vide om, hvordan du opretter en regel for mailflow (også kaldet en transportregel), der giver dig besked, når brugerne rapporterer meddelelser til Microsoft til analyse.|
|[Send malware og ikke-malware til Microsoft til analyse](submitting-malware-and-non-malware-to-microsoft-for-analysis.md)|Brug det Microsoft Sikkerhedsviden websted til at sende vedhæftede filer og andre filer.|

> [!NOTE]
> Når du rapporterer en mailenhed til Microsoft, opretter vi en kopi af alt, der er knyttet til mailen, for at inkludere den i vores løbende algoritmegennemgange. Denne kopi indeholder mailindholdet, mailheaderne og relaterede data om maildistributionen. Vedhæftede filer i meddelelsen er også inkluderet.
>
> Microsoft behandler din feedback som din organisations tilladelse til at analysere alle de tidligere beskrevne oplysninger og arbejde på at finjustere algoritmerne for meddelelseshygiejne. Vi holder din besked i vores sikre overvågede datacentre i USA, indtil vi sletter din indsendelse senest 30 dage efter, at du har leveret den til os. Personale hos Microsoft kan læse din indsendte meddelelse og vedhæftede filer, hvilket normalt ikke er tilladt for mail i Office 365. Din mail behandles dog stadig som fortroligt mellem dig og Microsoft, og vi sender din indsendelse til en anden part for at læse mailen eller dens vedhæftede filer til denne korrekturproces.
