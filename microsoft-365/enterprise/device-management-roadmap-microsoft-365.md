---
title: Roadmap til enhedshåndtering for Microsoft 365
keywords: Microsoft 365, Microsoft 365 til virksomheder, Microsoft 365, administration af mobilenheder, Intune
author: kelleyvice-msft
ms.author: kvice
manager: laurawi
ms.date: 08/10/2020
ms.topic: conceptual
f1.keywords:
- NOCSH
ms.prod: microsoft-365-enterprise
ms.service: ''
ms.technology: ''
ms.assetid: fb4182e6-5e78-45d0-9641-d791c4519441
audience: ITPro
ms.custom: microsoft-intune
description: Roadmap til at konfigurere enhedshåndtering for Microsoft 365.
ms.openlocfilehash: 0fef31697657b4694090ae7a1b63516920d8c71b
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/12/2022
ms.locfileid: "63591362"
---
# <a name="device-management-roadmap-for-microsoft-365"></a>Roadmap til enhedshåndtering for Microsoft 365

Microsoft 365 til virksomheder indeholder funktioner, der gør det muligt at administrere enheder og deres apps i din organisation. Administration af mobilenheder hjælper dig med at sikre og beskytte din organisations ressourcer.

Der er to muligheder for enhedshåndtering:

- [Microsoft Intune](#microsoft-intune)
- [Grundlæggende mobilitet og sikkerhed](#basic-mobility-and-security)

## <a name="microsoft-intune"></a>Microsoft Intune

Du kan bruge Microsoft Intune til at administrere adgang til din organisation ved hjælp af administration af mobilenheder eller administration af mobilapps. Administration af mobilenheder er, når brugerne "tilmelder" deres enheder i Intune. Når en enhed er tilmeldt, er den en administreret enhed. Kan den derfor modtage organisationens politikker, regler og indstillinger. Du kan f.eks installere bestemte apps, oprette en adgangskodepolitik, installere en VPN-forbindelse og meget mere.

Brugere med deres egne personlige enheder vil muligvis ikke registrere deres enheder eller administreres af Intune og organisationens politikker. Men du skal stadig beskytte din organisations ressourcer og data. I dette scenarie kan du beskytte dine apps ved hjælp af administration af mobilprogrammer. Du kan f.eks. bruge en politik for administration af mobilapps, der kræver, at en bruger angiver en pinkode, når der SharePoint online på enheden.

Du kan også se, hvordan du skal administrere personlige enheder og enheder, der ejes af organisationen. Det kan være en god ide at behandle enheder forskelligt, afhængigt af deres anvendelse.

## <a name="basic-mobility-and-security"></a>Grundlæggende mobilitet og sikkerhed

Det er indbygget i Microsoft 365 og hjælper dig med at sikre og administrere dine brugeres mobilenheder som iPhones, iPads, Android-Windows telefoner. Du kan oprette og administrere sikkerhedspolitikker for enheder, slette en enhed eksternt og få vist detaljerede enhedsrapporter.

## <a name="choose-between-the-two-options"></a>Vælg mellem de to indstillinger

For at hjælpe dig med bedre at vurdere, hvilken indstilling til enhedshåndtering der er bedst for dig, skal du [se Vælg mellem Basic Mobility Security og Intune](/office365/securitycompliance/choose-between-mdm-and-intune).

Baseret på din vurdering kan du komme i gang med at administrere dine enheder med:

- [Intune](/microsoft-365/solutions/manage-devices-with-intune-overview)
- [Grundlæggende mobilitet og sikkerhed](https://support.microsoft.com/office/set-up-basic-mobility-and-security-dd892318-bc44-4eb1-af00-9db5430be3cd)
 
## <a name="identity-and-device-access-recommendations"></a>Anbefalinger for identitets- og enhedsadgang

Microsoft leverer en række anbefalinger til identitets [- og enhedsadgang for](../security/office-365-security/microsoft-365-policies-configurations.md) at sikre en sikker og produktiv arbejdsstyrke. Du kan få adgang til enheden ved at følge anbefalingerne og indstillingerne i følgende artikler:

- [Forudsætninger](../security/office-365-security/identity-access-prerequisites.md)
- [Fælles identitets- og enhedsadgangspolitikker](../security/office-365-security/identity-access-policies.md)

## <a name="how-contoso-did-device-management-for-microsoft-365"></a>Sådan gjorde Contoso administration af enheder for Microsoft 365

Du kan finde oplysninger om, hvordan en fiktiv, men repræsentativ, multi national virksomhed, udrullede sin infrastruktur til administration af mobilenheder med Microsoft 365-skytjenester, under Administration af mobilenheder [for Contoso](contoso-mdm.md).