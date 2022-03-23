---
title: Lokalisere brugeroplevelsen
description: Sådan lokaliserer du enheder for brugere
keywords: Microsoft-administreret skrivebord, Microsoft 365, tjeneste, dokumentation
ms.service: m365-md
author: tiaraquan
f1.keywords:
- NOCSH
ms.author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
manager: dougeby
ms.topic: article
audience: Admin
ms.openlocfilehash: c429a072d6ceb2d5d1472533649e30d1fc1a0078
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/17/2022
ms.locfileid: "63592351"
---
# <a name="localize-the-user-experience"></a>Lokalisere brugeroplevelsen

Brugere af Microsoft-administrerede skrivebordsenheder kan vælge sproget efter eget valg enten under installationen ("out of box-oplevelsen") eller bagefter.

## <a name="during-setup-the-out-of-box-experience"></a>Under installationen ("out of box-oplevelsen")

Under installationen kan brugerne vælge det sprog, de ønsker. Dette valg påvirker disse attributter:

| Attribut | Beskrivelse |
| ------ | ------ |
| Windows 10 over sprogfunktioner | <ul><li>Visningssprog</li><li>Tastatursprog</li><li>Sprogrelaterede funktioner on-demand</li><ul> |
| Microsoft 365 Apps til enterprise-sprogfunktioner | <ul><li>Visningssprog</li><li>Korrektur- og redigeringsværktøjer</li></ul> |

> [!NOTE]
> Brugere kan kun få sprogrelaterede funktioner on-demand ved at vælge sproget under konfigurationen.

## <a name="after-completing-setup"></a>Når installationen er fuldført

Brugerne kan når som helst vælge det sprog, de Windows 10, og Microsoft 365 Apps til Enterprise når som helst, når konfigurationen er fuldført. Mere specifikt:

| Funktion | Beskrivelse |
| ------ | ------ |
| Windows 10 over sprogfunktioner | <ul><li>Visningssprog</li><li>Tastatursprog</li><ul> |
| Microsoft 365 Apps til enterprise-sprogfunktioner | <ul><li>Visningssprog</li><li>Korrektur- og redigeringsværktøjer</li></ul> |

## <a name="install-more-languages"></a>Installere flere sprog

> [!NOTE]
> Fra den 16. marts 2022 udfaser vi den gruppe med moderne Office-Language_Packs, der gør det muligt for dine brugere at tilføje sprog Microsoft Office. Overgangen til den nye metode (se nedenfor) vil blive gennemført i april 2022. Hvis du har problemer i denne overgangsperiode, er du velkommen til at kontakte [support](../working-with-managed-desktop/admin-support.md).

Som standard kræver Microsoft Office, at brugerne er administrator. Microsoft Managed Desktop implementerer en Office-politik for at gøre det muligt for standardbrugere at installere tilbehørssprogpakker direkte fra deres Office-apps. Du kan finde flere oplysninger [under Tillad brugere, der ikke er administratorer, at installere flere sprog](/deployoffice/overview-deploying-languages-microsoft-365-apps#allow-users-who-arent-admins-to-install-additional-languages).

## <a name="supported-languages"></a>Understøttede sprog

For nye enheder skal producenten levere enhedsbilleder, der indeholder de sprog, du kræver. Hvis producentens billede indeholder sprog, der ikke findes på listen over understøttede sprog, understøttes enheden stadig af tjenesten.

Hvis du bruger eksisterende enheder, skal du muligvis arbejde sammen med din Microsoft-kontorepræsentant for at få relevante billeder. Du kan finde flere oplysninger i [Enhedsbilleder](../service-description/device-images.md).

Det [universelle billede](../service-description/device-images.md#universal-image), der leveres af Microsoft Managed Desktop, omfatter disse sprog og Windows 10:

- Arabisk
- Bulgarian
- Chinese Simplified
- Chinese Traditional
- Croatian
- Czech
- Danish  
- Dutch  
- Engelsk (USA, GB, AU, CA, IN)
- Estonian
- Finnish
- Fransk (Frankrig, Canada)
- German
- Greek
- Hebrew
- Hungarian
- Indonesian
- Italian
- Japanese
- Korean
- Latvian
- Lithuanian
- Norsk (bokmål)
- Polish
- Portugisisk (Brasilien)
- Portugisisk (Portugal)
- Romanian
- Russian
- Serbisk (latinsk alfabet)
- Slovak
- Slovenian
- Spansk (Spanien, Mexico)
- Swedish
- Thai
- Turkish
- Ukrainian
- Vietnamese

> [!NOTE]
> Microsoft 365 Apps til Enterprise understøtter muligvis en lidt anden liste.

Hvis dine brugere skal bruge et andet sprog end dem, der er angivet her, kan du [arkivere en supportanmodning](../working-with-managed-desktop/admin-support.md) ved hjælp af [administrationsportalen](access-admin-portal.md).

## <a name="languages-for-support-and-operations"></a>Sprog til support og handlinger

### <a name="admin-support-and-operations"></a>Administratorsupport og -handlinger

Microsoft Managed Desktop understøtter kun administratorer på engelsk. Denne understøttelse omfatter administrationsportalen og al kommunikation med Microsoft-administrerede computerhandlinger. Du skal antage, at alle administratorrelaterede interaktioner og grænseflader er på engelsk, medmindre andet er angivet.
