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
description: Konfigurer beskyttelse af mobilapps med appbeskyttelsespolitikker (APP) for at forhindre, at bestemte virksomhedsdata kopieres og indsættes i andre apps.
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- m365solution-managedevices
- m365solution-scenario
ms.custom: ''
keywords: ''
ms.openlocfilehash: 4535e4a05ac8408e57c767999de66c39a4bf0274
ms.sourcegitcommit: 23166424125b80b2d615643f394a3c023cba641d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/14/2022
ms.locfileid: "63596954"
---
# <a name="step-1-implement-app-protection-policies"></a>Trin 1. Implementer politikker for appbeskyttelse

Intune App Protection-politikker (APP), nogle gange kaldet administration af mobilapps (MAM), beskytter virksomhedens data, også selvom selve enheden ikke administreres. Dette giver dig mulighed for at aktivere bring-your-own (BYO) og personlige enheder på arbejdet, hvor brugere kan være blevet "tilmeldt" deres enhed i administration. Politikker for appbeskyttelse sikrer, at virksomhedens data i de apps, du angiver, ikke kan kopieres og indsættes i andre apps på enheden.

![Trin til oprettelse af politikker for appbeskyttelse](../media/devices/intune-app-steps.png#lightbox)

I denne illustration:
- Med APP opretter Intune en væg mellem virksomhedens data og personlige data. Politikkerne for appbeskyttelse definerer, hvilke apps der har tilladelse til at få adgang til dine data.
- Hvis en bruger logger på med sine legitimationsoplysninger til organisationen, anvender Intune en politik i applaget for at forhindre kopiering og indsættelse af virksomhedens data i personlige apps og for at kræve pinkodeadgang til disse data.
- Når du har oprettet en politik for appbeskyttelse, skal du gennemtvinge databeskyttelse med en politik for betinget adgang. 

Denne konfiguration øger markant din sikkerhedsstilling uden at påvirke brugeroplevelsen.  Medarbejdere kan bruge apps som Office og Microsoft Teams, som de kender og holder af, mens din organisation på samme tid kan beskytte de data, der er indeholdt i apps og enheder.

Hvis du har brugerdefinerede Line of Business-programmer, der skal beskyttes, kan du i øjeblikket bruge ombrydningsværktøjet til apps til at aktivere APP med disse programmer. Eller du kan integrere ved hjælp af Intune App SDK. Når appen har politikker for appbeskyttelse anvendt, kan den administreres af Intune og genkendes af Intune som en administreret app. Du kan finde flere oplysninger om beskyttelse af dine Line of Business-programmer ved hjælp af Intune i Forbered apps til administration af [mobilprogrammer Microsoft Intune](/mem/intune/developer/apps-prepare-mobile-application-management).

## <a name="configuring-mobile-app-protection"></a>Konfiguration af beskyttelse af mobilapp

Denne vejledning er tæt koordineret med de anbefalede politikker for [Nul tillid til identitet og enhedsadgang](../security/office-365-security/microsoft-365-policies-configurations.md). Når du har oprettet beskyttelsespolitikkerne for mobilapps i Intune, skal du arbejde sammen med dit identitetsteam om at konfigurere politikken for betinget adgang i Azure AD, der gennemtvinger beskyttelse af mobilapps. 

I denne illustration fremhæves de to politikker (også beskrevet i tabellen under illustrationen).

[![Politikker for nultillidshed og enhedsadgang](../media/devices/identity-device-starting-point.png#lightbox)](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/devices/identity-device-starting-point.png)

For at konfigurere disse politikker skal du bruge den anbefalede vejledning og de indstillinger, der er angivet i [Null Trust-identitet og politikker for enhedsadgang](../security/office-365-security/microsoft-365-policies-configurations.md). Tabellen nedenfor linker direkte til instruktionerne til konfiguration af disse politikker i Intune og Azure AD.


|Trin  |Politikker  |Flere oplysninger  |Licensering  |
|---------|---------|---------|---------|
|1   |  [Anvend politikker for programbeskyttelse (APP) databeskyttelse](../security/office-365-security/identity-access-policies.md#apply-app-data-protection-policies)       | One Intune-politik for appbeskyttelse pr. platform (Windows, iOS/iPadOS, Android).        | Microsoft 365 E3 eller E5        |
|2     | [Kræv godkendte apps og appbeskyttelse ](../security/office-365-security/identity-access-policies.md#require-approved-apps-and-app-protection)       |  Gennemtvinger beskyttelse af mobilapps til telefoner og tablets ved hjælp af iOS, iPadOS eller Android.   |  Microsoft 365 E3 eller E5       |
| | | | |

## <a name="next-steps"></a>Næste trin

Gå til [Trin 2. Tilmeld enheder til administration med Intune](manage-devices-with-intune-enroll.md). 