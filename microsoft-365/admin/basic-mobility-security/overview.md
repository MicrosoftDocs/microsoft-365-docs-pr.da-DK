---
title: Oversigt over grundlæggende mobilitet og sikkerhed for Microsoft 365
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
description: Administrer og sikker mobilenheder, der er forbundet til din Microsoft 365 organisation, ved at konfigurere og bruge Grundlæggende mobilitet og sikkerhed.
ms.openlocfilehash: 168fd1f0ef08cf1a9bd5d7c90c53781016b232e6
ms.sourcegitcommit: db1e48af88995193f15bbd5962f5101a6088074b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/23/2022
ms.locfileid: "65636124"
---
# <a name="overview-of-basic-mobility-and-security-for-microsoft-365"></a>Oversigt over grundlæggende mobilitet og sikkerhed for Microsoft 365

Du kan administrere og sikre mobilenheder, når de har forbindelse til din Microsoft 365 organisation, ved hjælp af Grundlæggende mobilitet og sikkerhed. Mobilenheder som smartphones og tablets, der bruges til at få adgang til arbejdsmail, kalender, kontakter og dokumenter, spiller en vigtig rolle for at sikre, at medarbejderne får arbejdet fra hånden når som helst og hvor som helst. Det er derfor vigtigt, at du hjælper med at beskytte din organisations oplysninger, når folk bruger enheder. Du kan bruge Basic Mobility and Security til at angive politikker for enhedssikkerhed og adgangsregler og til at slette mobilenheder, hvis de mistes eller bliver stjålet.

:::image type="content" source="../../media/basic-mobility-security/bms-3-setup.png" alt-text="Grundlæggende konfiguration af mobilitet og sikkerhed.":::

## <a name="what-types-of-devices-can-you-manage"></a>Hvilke typer enheder kan du administrere?

Du kan bruge Basic Mobility og Security til at administrere mange typer mobilenheder, f.eks. Windows Phone, Android, iPhone og iPad. Hvis du vil administrere mobilenheder, der bruges af personer i din organisation, skal hver person have en relevant Microsoft 365 licens, og deres enhed skal være tilmeldt Basic Mobility and Security.

Hvis du vil se, hvad Basic Mobility og Security understøtter for hver type enhed, skal du se [Egenskaber for grundlæggende mobilitet og sikkerhed](capabilities.md).

## <a name="setup-steps-for-basic-mobility-and-security"></a>Trin til konfiguration af Basic Mobility og Security

En Microsoft 365 global administrator skal udføre følgende trin for at aktivere og konfigurere Grundlæggende mobilitet og sikkerhed. Du kan finde detaljerede trin ved at følge vejledningen i [Konfigurer grundlæggende mobilitet og sikkerhed](set-up.md). 

Her er en oversigt over trinnene:

**Trin 1:** Aktivér Grundlæggende mobilitet og sikkerhed ved at følge trinnene i [Konfigurer grundlæggende mobilitet og sikkerhed](set-up.md).

**Trin 2:** Konfigurer Basic Mobility og Security ved f.eks. at oprette et APN-certifikat for at administrere iOS-enheder og tilføje en DNS-post (Domain Name System) for dit domæne for at understøtte Windows telefoner.

**Trin 3:** Opret enhedspolitikker, og anvend dem på grupper af brugere. Når du gør dette, får brugerne en tilmeldingsmeddelelse på deres enhed, og når de har fuldført tilmeldingen, begrænses deres enheder af de politikker, du har konfigureret for dem. Du kan finde flere oplysninger under [Tilmeld din mobilenhed ved hjælp af Basic Mobility og Security](enroll-your-mobile-device.md). 

:::image type="content" source="../../media/basic-mobility-security/bms-4-policy.png" alt-text="Grundlæggende indstillinger for sikkerheds- og mobilitetspolitik.":::

## <a name="device-management-tasks"></a>Opgaver i forbindelse med enhedshåndtering

Når du har konfigureret Basic Mobility og Security, og dine brugere har tilmeldt deres enheder, kan du administrere enhederne, blokere adgang eller slette en enhed, hvis det er nødvendigt. Hvis du vil vide mere om nogle almindelige opgaver for enhedshåndtering, herunder hvor du skal udføre opgaverne, skal du se Administrer enheder, der er [tilmeldt mobile Enhedshåndtering for Microsoft 365](manage-enrolled-devices.md).

## <a name="other-ways-to-manage-devices-and-apps"></a>Andre måder at administrere enheder og apps på

Hvis du kun har brug for administration af mobilapps (MAM), måske for personer, der opdaterer arbejdsprojekter på deres egne enheder, Intune giver en anden mulighed ud over at tilmelde og administrere enheder. Et Intune abonnement giver dig mulighed for at konfigurere MAM-politikker ved hjælp af Azure Portal, selvom andres enheder ikke er tilmeldt Intune. Du kan finde flere oplysninger [under oversigt over Appbeskyttelse politikker](/mem/intune/apps/app-protection-policy).

## <a name="related-content"></a>Relateret indhold

[Konfigurer Basic Mobility and Security](set-up.md) (artikel)\
[Tilmeld din mobilenhed ved hjælp af Basic Mobility and Security](enroll-your-mobile-device.md) (artikel)\
[Administrer enheder, der er tilmeldt mobile Enhedshåndtering for Microsoft 365](manage-enrolled-devices.md) (artikel)\
[Få oplysninger om enheder, der administreres af Basic Mobility and Security](get-details-about-managed-devices.md) (artikel)