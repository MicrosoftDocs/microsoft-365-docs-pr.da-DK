---
title: Navnehandlinger rapporteret i Aktivitetsstifinder
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
description: En liste over etiketaktiviteter, der er tilgængelige i Aktivitetsstifinder.
ms.openlocfilehash: feed9d29deb94263d242967bdef38209cda660e1
ms.sourcegitcommit: 1ef176c79a0e6dbb51834fe30807409d4e94847c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/19/2021
ms.locfileid: "63593848"
---
# <a name="labeling-activities-that-are-available-in-activity-explorer"></a>Etiketaktiviteter, der er tilgængelige i Aktivitetsstifinder

## <a name="sensitivity-label-applied"></a>Følsomhedsmærkat anvendt

Denne hændelse genereres, hver gang et ikke-navnmærket dokument navnsendes, eller der sendes en mail med et følsomhedsmærkat.

- Det registreres på tidspunktet for lagring i Office oprindelige programmer og webprogrammer.
- De registreres på det tidspunkt, hvor de forekommer i tilføjelsesprogrammet Azure Information Protection.
- Handlingerne Opgradering og nedgradering af navne kan også overvåges via *feltet Etikethændelsestype* og filter.

|Kilde  |Rapporteret i Aktivitetsoversigt | Bemærk!  |
|---------|---------|---------|
| Word, Excel, PowerPoint|Ja |
|Outlook| Ja | |
|SharePoint online, OneDrive|Ja | |
|Exchange        |Ja         | |
|Samlet Azure Information Protection-klient (AIP) og en samlet AIP-scanner |Ja |Den nye *AIP-etikethandling* knyttes til en *etiket, der anvendes* i Aktivitetsstifinder   |
|Microsoft-beskyttelse af oplysninger (MIP) SDK         |Ja|Den nye *AIP-etikethandling* knyttes til en *etiket, der anvendes* i Aktivitetsstifinder|
|RMS (Rights Management Service)         |Ikke relevant         | |
|Power BI og internettet        | Nej| Handicapvenlige i Microsoft 365 overvågningslogfiler         |
|Microsoft Defender til skyapps         |Nej|         |

## <a name="sensitivity-label-changed"></a>Følsomhedsmærkat ændret

Denne hændelse genereres, hver gang en følsomhedsmærkat opdateres i dokumentet eller mailen.

- For AIP Unified-klienten, Unified Scanner- og MIP SDK-kilderne er  handlingshandlingen AIP-opgraderingsetiket og *nedgraderingsetiket* kort til navnet *Aktivitetsstifinder ændret*

- Det registreres ved lagringspunktet i Office oprindelige programmer og webprogrammer.
- Det registreres på det tidspunkt, hvor det forekommer i Azure Information Protection Unified Client-tilføjelses- og scanner-håndhævelser
- Handlingerne Opgradering og nedgradering af navne kan også overvåges via *feltet Etikethændelsestype* og filter. *Justeringsteksten* registreres også med undtagelse af SharePoint Online og OneDrive.
- Følsomheds-mærkning udført Office oprindelige apps på Outlook indsamler den seneste handling, der blev genereret før fil gem/mail send-handlinger. Hvis f.eks. brugeren ændrer etiketten på en mail flere gange før afsendelse, registreres den sidste etiket, der blev fundet i mailen, når den sendes, i overvågningsloggen og rapporteres derefter i Aktivitetsstifinder.

|Kilde  |Rapporteret i Aktivitetsoversigt|Bemærk!  |
|---------|---------|---------|
|Word, Excel, PowerPoint         |Ja         |
|Outlook         |Ja         |
|SharePoint Online, OneDrive         |Ja         |
|Exchange         |Ja         |
|Samlet AIP-klient         |Ja         |
|AIP-samlet scanner         |Ja         |
|MIP SDK         |Ja         |
|RMS-tjeneste         |Ikke relevant         |
|Power BI og internettet         |Nej         |Handicapvenlige i Microsoft 365 overvågningslogfiler |
|Microsoft Defender til skyapps     |Nej         |         |

## <a name="sensitivity-label-removed"></a>Følsomhedsmærkat fjernet

Denne hændelse genereres, hver gang en følsomhedsmærkat fjernes fra en fil eller et dokument.

- Hændelsen registreres på tidspunktet for lagring i Office oprindelige programmer og webprogrammer.
- De registreres på det tidspunkt, hvor de forekommer i tilføjelsesprogrammet Azure Information Protection.
- Følsomhedsmærkater med Office Indbygget MIP-etiket på Outlook indsamler den seneste etikethændelse, der blev oprettet før filspare-/mail-afsendelseshandlinger.

|Kilde  |Rapporteret i Aktivitetsoversigt | Bemærk!  |
|---------|---------|---------|
|Word, Excel, PowerPoint         |Ja         |
|Outlook         |Ja         ||
|SharePoint Online, OneDrive         |Ja         |
|Exchange         |Ja         |
|Samlet AIP-klient         |Ja         |Handlingen *Fjern etiket i* AIP er knyttet til den handling, *der fjernede navnet* i Aktivitetsstifinder|
|AIP-samlet scanner         |Ja         |Handlingen *Fjern etiket i* AIP er knyttet til den handling, *der fjernede navnet* i Aktivitetsstifinder |
|MIP SDK         |Ja         |Handlingen *Fjern etiket i* AIP er knyttet til den handling, *der fjernede navnet* i Aktivitetsstifinder |
|RMS-tjeneste         |Ikke relevant         |
|Power BI og internettet         |Nej         |Handicapvenlige i Microsoft 365 overvågningslogfiler |
|Microsoft Defender til skyapps     |Nej         |         |

## <a name="sensitivity-label-file-read"></a>Følsomheds-etiketfil læst

Denne hændelse genereres, hver gang en følsomhed, der er mærket eller et beskyttet dokument, åbnes.

|Kilde  |Rapporteret i Aktivitetsoversigt | Bemærk!  |
|---------|---------|---------|
|Word, Excel, PowerPoint         |Ja         |
|Outlook         |Nej         |
|SharePoint Online, OneDrive         |Nej         |
|Exchange         |Nej         |
|Samlet AIP-klient         |Ja         |*AIP-adgangshandlingen* er knyttet til *læsehandlingen for* filen i Aktivitetsstifinder|
|AIP-samlet scanner         |Ja         |*AIP-adgangshandlingen* er knyttet til *læsehandlingen for* filen i Aktivitetsstifinder|
|MIP SDK         |Ja         |*AIP-adgangshandlingen* er knyttet til *læsehandlingen for* filen i Aktivitetsstifinder|
|RMS-tjeneste         |Ja         |*Adgangshandlingen* er knyttet til handlingen *Læsning af fil* i Aktivitetsstifinder |
|Power BI og internettet         |Nej         |Handicapvenlige i Microsoft 365 overvågningslogfiler |
|Microsoft Defender til skyapps     |Nej         |         |

## <a name="files-discovered"></a>Fundne filer

Denne hændelse genereres, hver gang der bliver fundet filer, når AIP-scanneren bruges til at scanne følsomme data på forskellige steder og finder filer.

|Kilde  |Rapporteret i Aktivitetsoversigt | Bemærk!  |
|---------|---------|---------|
|Word, Excel, PowerPoint         |Ikke relevant         |
|Outlook         |Ikke relevant         |
|SharePoint Online, OneDrive         |Ikke relevant         |
|Exchange         |Ikke relevant         |
|Samlet AIP-klient         |Ikke relevant       |
|AIP-samlet scanner         |Ja         |Handlingen *AIP-opdag* er knyttet til de filer *, der blev fundet* i Aktivitetsstifinder|
|MIP SDK         |Ja         |Handlingen *AIP-opdag* er knyttet til den fil *, der blev fundet* i Aktivitetsstifinder|
|RMS-tjeneste         |Ikke relevant         |
|Power BI og internettet         |Ikke relevant         |
|Microsoft Defender til skyapps     |Ikke relevant         |         |

## <a name="sensitivity-label-file-renamed"></a>Følsomheds-etiketfil omdøbt

Denne hændelse genereres, hver gang et dokument med et følsomhedsmærkat omdøbes.

|Kilde  | Rapporteret i Aktivitetsoversigt | Bemærk!  |
|---------|---------|---------|
|Word, Excel, PowerPoint         |Ja         |
|Outlook         |Ikke relevant         |
|SharePoint Online, OneDrive         |Nej        |
|Exchange         |Ikke relevant         |
|Samlet AIP-klient         |Nej         |
|AIP-samlet scanner         |Nej         |
|MIP SDK         |Nej         |
|RMS-tjeneste         |Nej      |
|Power BI og internettet         |Nej         |
|Microsoft Defender til skyapps     |Nej         |         |

## <a name="file-removed"></a>Fil fjernet

Denne hændelse genereres, hver gang AIP-scanneren registrerer, at en tidligere scannet fil er blevet fjernet.

|Kilde  |Rapporteret i Aktivitetsoversigt | Bemærk!  |
|---------|---------|---------|
|Word, Excel, PowerPoint         |Ikke relevant         |
|Outlook         |Ikke relevant         |
|SharePoint Online, OneDrive         |Ikke relevant           |
|Exchange         |Ikke relevant         |
|Samlet AIP-klient         |Ikke relevant            |
|AIP-samlet scanner         |Ja         |
|MIP SDK         |Ikke relevant            |
|RMS-tjeneste         |Ikke relevant         |
|Power BI og internettet         |Ikke relevant  |
|Microsoft Defender til skyapps     |Ikke relevant        |         |

### <a name="protection-applied"></a>Beskyttelse anvendt

Denne hændelse genereres beskyttelse første gang føjes manuelt til et element, der ikke har en etiket.

|Kilde  |Rapporteret i Aktivitetsoversigt | Bemærk!  |
|---------|---------|---------|
|Word, Excel, PowerPoint         |Nej         |
|Outlook         |Nej         |
|SharePoint Online, OneDrive         |Ikke relevant           |
|Exchange         |Nej       |
|Samlet AIP-klient         |Ja            |
|AIP-samlet scanner         |Ikke relevant         |
|MIP SDK         |Ja            |
|RMS-tjeneste         |Ikke relevant         |
|Power BI og internettet         |Ikke relevant            |
|Microsoft Defender til skyapps     |Ikke relevant        |         |

## <a name="protection-changed"></a>Beskyttelse er ændret

Denne hændelse genereres, hver gang beskyttelsen på et dokument uden navn ændres manuelt.

|Kilde  |Rapporteret i Aktivitetsoversigt |
|---------|---------|
|Word, Excel, PowerPoint         |Nej         |
|Outlook         |Nej         |
|SharePoint Online, OneDrive         |Ikke relevant           |
|Exchange         |Nej       |
|Samlet AIP-klient         |Ja            |
|AIP-samlet scanner         |Ikke relevant         |
|MIP SDK         |Ja            |
|RMS-tjeneste         |Ikke relevant         |
|Power BI og internettet         |Ikke relevant            |
|Microsoft Defender til skyapps     |Ikke relevant        |

## <a name="protection-removed"></a>Beskyttelse er fjernet

Denne hændelse genereres, hver gang beskyttelsen på et dokument uden navn ændres manuelt.

|Kilde  |Rapporteret i Aktivitetsoversigt |
|---------|---------|
|Word, Excel, PowerPoint         |Nej         |
|Outlook         |Nej         |
|SharePoint Online, OneDrive         |Ikke relevant           |
|Exchange         |Nej       |
|Samlet AIP-klient         |Ja            |
|AIP-samlet scanner         |Ikke relevant         |
|MIP SDK         |Ja            |
|RMS-tjeneste         |Ikke relevant         |
|Power BI og internettet         |Ikke relevant            |
|Microsoft Defender til skyapps     |Ikke relevant        |

## <a name="dlp-policy-matched"></a>DLP-politik matchet

Denne hændelse genereres, hver gang en DLP-politik matches på et dokument eller en mail.

|Kilde  |Rapporteret i Aktivitetsoversigt |
|---------|---------|
|Exchange         |Ja       |
|SharePoint Online|Ja          |
|OneDrive |Ja|
|Teams |Ja   |
|Windows 10 enheder         |Ja |
|MAC         |Nej     |
|Lokalt miljø         |Nej|
|Microsoft Defender til skyapps     |Nej        |

Hændelserne for Windows 10 (Slutpunkt DLP) er:

- Filen er slettet
- Fil oprettet
- Fil, der er kopieret til Udklipsholder
- Filen er ændret
- Filen er læst
- Fil udskrevet
- Omdøbt fil
- Fil, der er kopieret til netværksdeling
- Fil åbnet ved ikke-tilladt app

## <a name="retention-label-applied"></a>Opbevaringsmærkat anvendt

Denne hændelse genereres, hver gang et dokument uden navn navnmærkes, eller der sendes en mail med et opbevaringsetiket.

- Det registreres på tidspunktet for lagring for et dokument og på tidspunktet for afsendelse af en mail.

|Kilde  |Rapporteret i Aktivitetsoversigt |
|---------|---------|
|Exchange         |Nej       |
|SharePoint Online|Ja          |
|OneDrive |Ja|

## <a name="retention-label-changed"></a>Opbevaringsnavn ændret

Denne hændelse genereres, hver gang et navn opdateres i et dokument eller en mail.

- Det registreres på tidspunktet for lagring for et dokument og på tidspunktet for afsendelse af en mail.

|Kilde  |Rapporteret i Aktivitetsoversigt |
|---------|---------|
|Exchange         |Nej       |
|SharePoint Online|Ja          |
|OneDrive |Ja|

## <a name="retention-label-removed"></a>Opbevaringsmærkat fjernet

Denne hændelse genereres, hver gang et navn fjernes fra en fil eller et dokument.

- Det registreres på tidspunktet for lagring for et dokument og på tidspunktet for afsendelse af en mail.

|Kilde  |Rapporteret i Aktivitetsoversigt |
|---------|---------|
|Exchange         |Nej       |
|SharePoint Online|Ja          |
|OneDrive |Ja|

## <a name="known-issues"></a>Kendte problemer
  
- Når det anbefalede værktøjstip til etiketter vises for en slutbruger, registreres det ikke. Men hvis brugeren vælger at anvende den anbefalede etiket, vises etiketten under *Feltet Hvor anvendt* som *anbefalet*.

- Justeringstekst er i øjeblikket ikke tilgængelig på følsomhedsmærkatens nedgradering SharePoint og OneDrive.

- Følsomme oplysningstyper er i øjeblikket ikke tilgængelige for automatisk mærkning af aktiviteter fra Word, Excel, PowerPoint og Outlook samt SharePoint Online og OneDrive.
