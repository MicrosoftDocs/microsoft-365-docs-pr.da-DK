---
title: Oversigt over Grundlæggende mobilitet og sikkerhed til Microsoft 365
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- MET150
description: Brug Grundlæggende mobilitet og sikkerhed til at angive sikkerhedspolitikker og adgangsregler for enheder.
ms.openlocfilehash: 4fb1b8ca467d86259f2608af5140510a2a88b23a
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63591047"
---
# <a name="overview-of-basic-mobility-and-security-for-microsoft-365"></a>Oversigt over Grundlæggende mobilitet og sikkerhed til Microsoft 365

Du kan administrere og sikre mobilenheder, når de er forbundet til din Microsoft 365 organisation ved hjælp af Grundlæggende mobilitet og sikkerhed. Mobilenheder som smartphones og tablets, der bruges til at få adgang til arbejdsmail, kalender, kontakter og dokumenter, spiller en stor rolle i at sikre, at medarbejderne får arbejdet gjort når som helst og hvor som helst. Det er derfor meget vigtigt, at du beskytter organisationens oplysninger, når folk bruger enheder. Du kan bruge Grundlæggende mobilitet og sikkerhed til at angive sikkerhedspolitikker og adgangsregler for enheder samt til at slette mobilenheder, hvis de mistes eller bliver stjålet.

:::image type="content" source="../../media/basic-mobility-security/bms-3-setup.png" alt-text="Grundlæggende konfiguration af mobilitet og sikkerhed.":::

## <a name="what-types-of-devices-can-you-manage"></a>Hvilke typer enheder kan du administrere?

Du kan bruge Grundlæggende mobilitet og sikkerhed til at administrere mange typer af mobilenheder som Windows Phone, Android, iPhone og iPad. For at administrere mobilenheder, der bruges af personer i organisationen, skal hver person have en relevant Microsoft 365-licens, og personens enhed skal være tilmeldt Grundlæggende mobilitet og sikkerhed.

Hvis du vil se, hvilke standardmobilitet og sikkerhed der understøtter hver type enhed, skal du  [seCapabilities of Basic Mobility and Security](capabilities.md).

## <a name="setup-steps-for-basic-mobility-and-security"></a>Konfigurationstrin til Grundlæggende mobilitet og sikkerhed

En Microsoft 365 global administrator skal gennemføre følgende trin for at aktivere og konfigurere Grundlæggende mobilitet og sikkerhed. Hvis du vil have en detaljeret vejledning, skal du [følge vejledningen i Konfigurer Grundlæggende mobilitet og sikkerhed](set-up.md). 

Her er en oversigt over trinnene:

**Trin 1:** Aktivér Grundlæggende mobilitet og sikkerhed ved at følge trinnene  [iSet up Basic Mobility and Security](set-up.md).

**Trin 2:** Konfigurer Grundlæggende mobilitet og sikkerhed ved f.eks. at oprette et APNs-certifikat til at administrere iOS-enheder og tilføje en DNS-post (Domain Name System) for dit domæne for at understøtte Windows telefoner.

**Trin 3:** Opret enhedspolitikker, og anvend dem på grupper af brugere. Når du gør dette, får dine brugere en registreringsmeddelelse på deres enhed, og når de har fuldført tilmeldingen, er deres enheder begrænset af de politikker, du har konfigureret for dem. Du kan få mere at vide [under Tilmeld din mobilenhed ved hjælp af Grundlæggende mobilitet og sikkerhed](enroll-your-mobile-device.md). 

:::image type="content" source="../../media/basic-mobility-security/bms-4-policy.png" alt-text="Grundlæggende indstillinger for sikkerheds- og mobilitetspolitik.":::

## <a name="device-management-tasks"></a>Administration af enheder

Når du har konfigureret Grundlæggende mobilitet og sikkerhed, og dine brugere har tilmeldt sig deres enheder, kan du administrere enhederne, blokere adgangen eller slette en enhed, hvis det er nødvendigt. Du kan få mere at vide om nogle almindelige administrationsopgaver for enheder, herunder hvor du skal udføre opgaverne, under Administrer enheder, der er tilmeldt Administration af [mobilenheder for Microsoft 365](manage-enrolled-devices.md).

## <a name="other-ways-to-manage-devices-and-apps"></a>Andre måder at administrere enheder og apps på

Hvis du kun har brug for administration af mobilapps (MAM), måske til personer, der opdaterer arbejdsprojekter på deres egne enheder, indeholder Intune en anden mulighed end registrering og administration af enheder. Med et Intune-abonnement kan du konfigurere MAM-politikker ved hjælp af Azure-portalen, også selvom personers enheder ikke er tilmeldt Intune. Få mere at vide under  [Oversigt over beskyttelsespolitikker til app](/mem/intune/apps/app-protection-policy).

## <a name="related-content"></a>Relateret indhold

[Konfigurer Grundlæggende mobilitet og sikkerhed](set-up.md) (artikel)\
[Tilmeld din mobilenhed ved hjælp af Grundlæggende mobilitet og sikkerhed](enroll-your-mobile-device.md) (artikel)\
[Administrer enheder, der er tilmeldt Administration af mobilenheder for Microsoft 365](manage-enrolled-devices.md) (artikel)\
[Få oplysninger om enheder, der administreres af Basic Mobility and Security](get-details-about-managed-devices.md) (artikel)