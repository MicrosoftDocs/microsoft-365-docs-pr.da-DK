---
title: Mærkningshandlinger, der er rapporteret i aktivitetsviser
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
search.appverid:
- MOE150
- MET150
description: En liste over navngivne aktiviteter, der er tilgængelige i Aktivitetsoversigt.
ms.openlocfilehash: 27a6bb3f0fe4293d5904c7e1661ef1e422fbac5b
ms.sourcegitcommit: 24827a509b3e78959ce67679646e572a0c996282
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/21/2022
ms.locfileid: "66917864"
---
# <a name="labeling-activities-that-are-available-in-activity-explorer"></a>Navngiver aktiviteter, der er tilgængelige i Aktivitetsoversigt

## <a name="sensitivity-label-applied"></a>Følsomhedsmærkat anvendt

Denne hændelse genereres, hver gang et ikke-navngivet dokument mærkes, eller der sendes en mail med en følsomhedsmærkat.

- Den registreres på tidspunktet for lagring i oprindelige Office-programmer og webprogrammer.
- Den registreres på tidspunktet for forekomsten af Azure Information Protection (AIP) unified labeling-klienten.
- Handlinger for opgradering og nedgradering af mærkater kan også overvåges via feltet og filteret *for hændelsestypen Mærkat* .

|Kilde  |Rapporteret i Aktivitetsoversigt | Bemærk  |
|---------|---------|---------|
| Word, Excel, PowerPoint|Ja |
|Outlook| Ja | |
|SharePoint online, OneDrive|Ja | |
|Exchange        |Ja         | |
|Azure Information Protection (AIP) unified client og AIP Unified Scanner |Ja |Den *nye AIP-etikethandling* er knyttet til *den mærkat, der anvendes* i Aktivitetsoversigt   |
|Microsoft Information Protection SDK (MIP)         |Ja|Den *nye AIP-etikethandling* er knyttet til *den mærkat, der anvendes* i Aktivitetsoversigt|
|RMS (Rights Management Service)         |Ikke relevant         | |
|Power BI Desktop og web        | Nej| Tilgængelig i Microsoft 365-overvågningslogge         |
|Microsoft Defender for Cloud Apps         |Nej|         |

## <a name="sensitivity-label-changed"></a>Følsomhedsmærkaten er ændret

Denne hændelse genereres, hver gang en følsomhedsmærkat opdateres i dokumentet eller mailen.

- For AIP Unified Client-, AIP Unified Scanner- og MIP SDK-kilderne er handlingstilknytningerne for *AIP-opgraderingsbeskrivelsen* og *-nedgraderingsmærkaten* *ændret til mærkaten* Aktivitetsoversigt

- Den registreres ved lagring i oprindelige Office-programmer og webprogrammer.
- Den registreres på tidspunktet for forekomsten af AIP Unified Labeling Client- og Scanner Enforcements
- Handlinger for opgradering og nedgradering af mærkater kan også overvåges via feltet og filteret *for hændelsestypen Mærkat* . *Justeringsteksten* registreres også med undtagelse af SharePoint Online og OneDrive.
- Følsomhedsmærkater, der udføres i oprindelige Office-apps i Outlook, indsamler den seneste handling, der blev genereret, før handlingerne for fillagring/mailsending. Hvis brugeren f.eks. ændrer mærkat på en mail flere gange, før der sendes, registreres den sidste mærkat, der blev fundet i mailen, da den blev sendt, i overvågningsloggen og rapporteres derefter i Aktivitetsoversigt.

|Kilde  |Rapporteret i Aktivitetsoversigt|Bemærk  |
|---------|---------|---------|
|Word, Excel, PowerPoint         |Ja         |
|Outlook         |Ja         |
|SharePoint Online, OneDrive         |Ja         |
|Exchange         |Ja         |
|AIP Unified Client         |Ja         |
|AIP unified scanner         |Ja         |
|MIP SDK         |Ja         |
|RMS-tjeneste         |Ikke relevant         |
|Power BI Desktop og Web         |Nej         |Tilgængelig i Microsoft 365-overvågningslogge |
|Microsoft Defender for Cloud Apps     |Nej         |         |

## <a name="sensitivity-label-removed"></a>Følsomhedsmærkat er fjernet

Denne hændelse genereres, hver gang en følsomhedsmærkat fjernes fra en fil eller et dokument.

- Denne hændelse registreres på tidspunktet for lagring i oprindelige Office-programmer og webprogrammer.
- Den registreres på tidspunktet for forekomsten af Azure Information Protection (AIP) unified labeling-klienten.
- Følsomhedsmærkater med indbyggede Office-mærkater i Outlook indsamler den sidste navngivningshændelse, der blev genereret før handlinger til fillagring/mailsending.

|Kilde  |Rapporteret i Aktivitetsoversigt | Bemærk  |
|---------|---------|---------|
|Word, Excel, PowerPoint         |Ja         |
|Outlook         |Ja         ||
|SharePoint Online, OneDrive         |Ja         |
|Exchange         |Ja         |
|AIP Unified Client         |Ja         |Handlingen *Fjern mærkat* i AIP er knyttet til den handling, der er *fjernet af mærkaten* i Aktivitetsoversigt|
|AIP unified scanner         |Ja         |Handlingen *Fjern mærkat* i AIP er knyttet til den handling, der er *fjernet af mærkaten* i Aktivitetsoversigt |
|MIP SDK         |Ja         |Handlingen *Fjern mærkat* i AIP er knyttet til den handling, der er *fjernet af mærkaten* i Aktivitetsoversigt |
|RMS-tjeneste         |Ikke relevant         |
|Power BI Desktop og Web         |Nej         |Tilgængelig i Microsoft 365-overvågningslogge |
|Microsoft Defender for Cloud Apps     |Nej         |         |

## <a name="sensitivity-label-file-read"></a>Fil med følsomhedsmærkat læst

Denne hændelse genereres, hver gang et følsomhedsmærkat eller beskyttet dokument åbnes.

|Kilde  |Rapporteret i Aktivitetsoversigt | Bemærk  |
|---------|---------|---------|
|Word, Excel, PowerPoint         |Ja         |
|Outlook         |Nej         |
|SharePoint Online, OneDrive         |Nej         |
|Exchange         |Nej         |
|AIP Unified Client         |Ja         |*AIP-adgangshandlingen* er knyttet til handlingen *Læs fil* i Aktivitetsoversigt|
|AIP unified scanner         |Ja         |*AIP-adgangshandlingen* er knyttet til handlingen *Læs fil* i Aktivitetsoversigt|
|MIP SDK         |Ja         |*AIP-adgangshandlingen* er knyttet til handlingen *Læs fil* i Aktivitetsoversigt|
|RMS-tjeneste         |Ja         |*Adgangshandlingen* er knyttet til *handlingen Læs fil* i Aktivitetsoversigt |
|Power BI Desktop og Web         |Nej         |Tilgængelig i Microsoft 365-overvågningslogge |
|Microsoft Defender for Cloud Apps     |Nej         |         |

## <a name="files-discovered"></a>Registrerede filer

Denne hændelse genereres, hver gang filer registreres, når AIP-scanneren bruges til at scanne følsomme data på forskellige placeringer og finder filer.

|Kilde  |Rapporteret i Aktivitetsoversigt | Bemærk  |
|---------|---------|---------|
|Word, Excel, PowerPoint         |Ikke relevant         |
|Outlook         |Ikke relevant         |
|SharePoint Online, OneDrive         |Ikke relevant         |
|Exchange         |Ikke relevant         |
|AIP Unified Client         |Ikke relevant       |
|AIP unified scanner         |Ja         |*AIP-registreringshandlingen* er knyttet til den *registrerede filhandling i Aktivitetsoversigt*|
|MIP SDK         |Ja         |*AIP-registreringshandlingen* er knyttet til den *registrerede fil-handling i Aktivitetsoversigt*|
|RMS-tjeneste         |Ikke relevant         |
|Power BI Desktop og Web         |Ikke relevant         |
|Microsoft Defender for Cloud Apps     |Ikke relevant         |         |

## <a name="sensitivity-label-file-renamed"></a>Filen med følsomhedsmærkaten er omdøbt

Denne hændelse genereres, hver gang et dokument med en følsomhedsmærkat omdøbes.

|Kilde  | Rapporteret i Aktivitetsoversigt | Bemærk  |
|---------|---------|---------|
|Word, Excel, PowerPoint         |Ja         |
|Outlook         |Ikke relevant         |
|SharePoint Online, OneDrive         |Nej        |
|Exchange         |Ikke relevant         |
|AIP Unified Client         |Nej         |
|AIP unified scanner         |Nej         |
|MIP SDK         |Nej         |
|RMS-tjeneste         |Nej      |
|Power BI Desktop og Web         |Nej         |
|Microsoft Defender for Cloud Apps     |Nej         |         |

## <a name="file-removed"></a>Filen er fjernet

Denne hændelse genereres, hver gang AIP-scanneren registrerer, at en tidligere scannet fil er blevet fjernet.

|Kilde  |Rapporteret i Aktivitetsoversigt | Bemærk  |
|---------|---------|---------|
|Word, Excel, PowerPoint         |Ikke relevant         |
|Outlook         |Ikke relevant         |
|SharePoint Online, OneDrive         |Ikke relevant           |
|Exchange         |Ikke relevant         |
|AIP Unified Client         |Ikke relevant            |
|AIP unified scanner         |Ja         |
|MIP SDK         |Ikke relevant            |
|RMS-tjeneste         |Ikke relevant         |
|Power BI Desktop og Web         |Ikke relevant  |
|Microsoft Defender for Cloud Apps     |Ikke relevant        |         |

### <a name="protection-applied"></a>Beskyttelse anvendt

Denne hændelse genereres, første gang beskyttelsen føjes manuelt til et element, der ikke har en mærkat.

|Kilde  |Rapporteret i Aktivitetsoversigt | Bemærk  |
|---------|---------|---------|
|Word, Excel, PowerPoint         |Nej         |
|Outlook         |Nej         |
|SharePoint Online, OneDrive         |Ikke relevant           |
|Exchange         |Nej       |
|AIP Unified Client         |Ja            |
|AIP unified scanner         |Ikke relevant         |
|MIP SDK         |Ja            |
|RMS-tjeneste         |Ikke relevant         |
|Power BI Desktop og Web         |Ikke relevant            |
|Microsoft Defender for Cloud Apps     |Ikke relevant        |         |

## <a name="protection-changed"></a>Beskyttelsen er ændret

Denne hændelse genereres, hver gang beskyttelsen af et ikke-navngivet dokument ændres manuelt.

|Kilde  |Rapporteret i Aktivitetsoversigt |
|---------|---------|
|Word, Excel, PowerPoint         |Nej         |
|Outlook         |Nej         |
|SharePoint Online, OneDrive         |Ikke relevant           |
|Exchange         |Nej       |
|AIP Unified Client         |Ja            |
|AIP unified scanner         |Ikke relevant         |
|MIP SDK         |Ja            |
|RMS-tjeneste         |Ikke relevant         |
|Power BI Desktop og Web         |Ikke relevant            |
|Microsoft Defender for Cloud Apps     |Ikke relevant        |

## <a name="protection-removed"></a>Beskyttelse fjernet

Denne hændelse genereres, hver gang beskyttelsen af et ikke-navngivet dokument ændres manuelt.

|Kilde  |Rapporteret i Aktivitetsoversigt |
|---------|---------|
|Word, Excel, PowerPoint         |Nej         |
|Outlook         |Nej         |
|SharePoint Online, OneDrive         |Ikke relevant           |
|Exchange         |Nej       |
|AIP Unified Client         |Ja            |
|AIP unified scanner         |Ikke relevant         |
|MIP SDK         |Ja            |
|RMS-tjeneste         |Ikke relevant         |
|Power BI Desktop og Web         |Ikke relevant            |
|Microsoft Defender for Cloud Apps     |Ikke relevant        |

## <a name="dlp-policy-matched"></a>DLP-politik matcher

Denne hændelse genereres, hver gang en DLP-politik matches i et dokument eller en mail.

|Kilde  |Rapporteret i Aktivitetsoversigt |
|---------|---------|
|Exchange         |Ja       |
|SharePoint Online|Ja          |
|OneDrive |Ja|
|Teams |Ja   |
|Windows 10 enheder         |Ja |
|MAC         |Nej     |
|I det lokale miljø         |Nej|
|Microsoft Defender for Cloud Apps     |Nej        |

Hændelserne for Windows 10 Enheder (Slutpunkt DLP) er:

- Filen er slettet
- Filen er oprettet
- Fil, der er kopieret til Udklipsholder
- Filen er ændret
- Fillæsning
- Udskrevet fil
- Filen er omdøbt
- Filen er kopieret til netværkssharet
- Fil, der er åbnet af en ikke-tilladt app

## <a name="retention-label-applied"></a>Opbevaringsmærkat anvendt

Denne hændelse genereres, hver gang et ikke-navngivet dokument mærkes, eller der sendes en mail med en opbevaringsmærkat.

- Den registreres på lagringstidspunktet for et dokument og på tidspunktet for afsendelse af en mail.

|Kilde  |Rapporteret i Aktivitetsoversigt |
|---------|---------|
|Exchange         |Nej       |
|SharePoint Online|Ja          |
|OneDrive |Ja|

## <a name="retention-label-changed"></a>Opbevaringsmærkat er ændret

Denne hændelse genereres, hver gang en etiket opdateres i et dokument eller en mail.

- Den registreres på lagringstidspunktet for et dokument og på tidspunktet for afsendelse af en mail.

|Kilde  |Rapporteret i Aktivitetsoversigt |
|---------|---------|
|Exchange         |Nej       |
|SharePoint Online|Ja          |
|OneDrive |Ja|

## <a name="retention-label-removed"></a>Opbevaringsmærkat er fjernet

Denne hændelse genereres, hver gang en etiket fjernes fra en fil eller et dokument.

- Den registreres på lagringstidspunktet for et dokument og på tidspunktet for afsendelse af en mail.

|Kilde  |Rapporteret i Aktivitetsoversigt |
|---------|---------|
|Exchange         |Nej       |
|SharePoint Online|Ja          |
|OneDrive |Ja|

## <a name="known-issues"></a>Kendte problemer
  
- Når det anbefalede etiketværktøjstip vises for en slutbruger, registreres det ikke. Men hvis brugeren vælger at anvende den anbefalede mærkat, vises etiketten under feltet *Sådan anvendes* som *anbefalet*.

- Justeringstekst er i øjeblikket ikke tilgængelig for nedgradering af følsomhedsmærkat fra SharePoint og OneDrive.

- Følsomme oplysningstyper er i øjeblikket ikke tilgængelige til automatisk angivelse af oplysninger fra Word, Excel, PowerPoint og Outlook samt SharePoint Online og OneDrive.
