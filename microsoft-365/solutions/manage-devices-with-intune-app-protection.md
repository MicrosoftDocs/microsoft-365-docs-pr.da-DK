---
title: Trin 1. Implementer politikker for appbeskyttelse
ms.author: bcarter
author: brendacarter
f1.keywords:
- Intune App Protection policies
- APP
- mobile application management
- MAM
- set up mobile ap protection
manager: dougeby
audience: ITPro
ms.topic: article
description: Konfigurer beskyttelse af mobilapps med appbeskyttelsespolitikker (APP) for at forhindre, at angivne virksomhedsdata kopieres og indsættes i andre apps.
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- m365solution-managedevices
- m365solution-scenario
- zerotrust-solution
ms.custom: ''
keywords: ''
ms.openlocfilehash: 829d650b6d815a84203e43e7256442bfee6bac0d
ms.sourcegitcommit: 61b22df76e0f81e5ef11c587b129287886151c79
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/12/2022
ms.locfileid: "66749281"
---
# <a name="step-1-implement-app-protection-policies"></a>Trin 1. Implementer politikker for appbeskyttelse

Intune App Protection-politikker (APP), også kaldet MAM (Mobile Application Management), beskytter virksomhedens data, selvom selve enheden ikke administreres. Dette giver dig mulighed for at aktivere BYO (bring-your-own) og personlige enheder på arbejdet, hvor brugerne kan være tilbageholdende med at "tilmelde" deres enhed til administration. Politikker for appbeskyttelse sikrer, at firmadata i de apps, du angiver, ikke kan kopieres og indsættes i andre apps på enheden.

![Trin til oprettelse af beskyttelsespolitikker for apps](../media/devices/intune-app-steps.png#lightbox)

I denne illustration:
- Med APP opretter Intune en mur mellem dine organisationsdata og personlige data. Politikkerne for appbeskyttelse definerer, hvilke apps der har tilladelse til at få adgang til dine data.
- Hvis en bruger logger på med sine organisationslegitimationsoplysninger, anvender Intune en politik på applaget for at forhindre kopiering og indsættelse af dine organisationsdata i personlige apps og for at kræve adgang til pinkode til disse data.
- Når du har oprettet en appbeskyttelsespolitik, gennemtvinger du databeskyttelse med en politik for betinget adgang. 

Denne konfiguration øger din sikkerhedsholdning markant med næsten ingen indvirkning på brugeroplevelsen.  Medarbejdere kan bruge apps som Office og Microsoft Teams, som de kender og elsker, samtidig med at din organisation kan beskytte dataene i apps og enheder.

Hvis du har brugerdefinerede Line of Business-programmer, der kræver beskyttelse, kan du i øjeblikket bruge appombrydningsværktøjet til at aktivere APP med disse programmer. Du kan også integrere ved hjælp af Intune App SDK. Når der er anvendt politikker for appbeskyttelse på din app, kan den administreres af Intune og genkendes af Intune som en administreret app. Du kan få flere oplysninger om beskyttelse af dine Line of Business-programmer ved hjælp af Intune under [Forbered apps til administration af mobilapps med Microsoft Intune](/mem/intune/developer/apps-prepare-mobile-application-management).

## <a name="configuring-mobile-app-protection"></a>Konfiguration af beskyttelse af mobilapps

Denne vejledning er tæt koordineret med de anbefalede [Nul tillid politikker for identitet og enhedsadgang](../security/office-365-security/microsoft-365-policies-configurations.md). Når du har oprettet politikkerne for mobil Appbeskyttelse i Intune, skal du arbejde sammen med dit identitetsteam for at konfigurere politikken for betinget adgang i Azure AD, der gennemtvinger beskyttelse af mobilapps. 

Denne illustration fremhæver de to politikker (også beskrevet i tabellen nedenfor illustrationen).

[![Nul tillid politikker for identitet og enhedsadgang](../media/devices/identity-device-starting-point.png#lightbox)](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/devices/identity-device-starting-point.png)

Hvis du vil konfigurere disse politikker, skal du bruge den anbefalede vejledning og de indstillinger, der er foreskrevet i [Nul tillid politikker for identitets- og enhedsadgang](../security/office-365-security/microsoft-365-policies-configurations.md). I nedenstående tabel linker du direkte til instruktionerne til konfiguration af disse politikker i Intune og Azure AD.


|Trin  |Politikker  |Flere oplysninger  |Licensering  |
|---------|---------|---------|---------|
|1   |  [Anvend app-databeskyttelse (Application Protection Policies)](../security/office-365-security/identity-access-policies.md#apply-app-data-protection-policies)       | Én Intune appbeskyttelsespolitik pr. platform (Windows, iOS/iPadOS, Android).        | Microsoft 365 E3 eller E5        |
|2     | [Kræv godkendt app- og appbeskyttelse ](../security/office-365-security/identity-access-policies.md#require-approved-apps-and-app-protection)       |  Gennemtvinger beskyttelse af mobilapps til telefoner og tablets ved hjælp af iOS, iPadOS eller Android.   |  Microsoft 365 E3 eller E5       |
| | | | |

## <a name="next-steps"></a>Næste trin

Gå til [trin 2. Tilmeld enheder til Intune](manage-devices-with-intune-enroll.md). 