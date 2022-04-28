---
title: Oversigt over enhedshåndtering for Microsoft 365
keywords: Microsoft 365, Microsoft 365 til virksomheder, Microsoft 365 dokumentation, administration af mobilenheder, Intune
author: kelleyvice-msft
ms.author: kvice
manager: scotv
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
description: Køreplanen for konfiguration af enhedshåndtering for Microsoft 365.
ms.openlocfilehash: eeed1a69fc1724f3feb75f4bc096cad3a3c25cf0
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65095306"
---
# <a name="device-management-roadmap-for-microsoft-365"></a>Oversigt over enhedshåndtering for Microsoft 365

Microsoft 365 til virksomheder indeholder funktioner, der kan hjælpe med at administrere enheder og deres apps i din organisation. Administration af mobilenheder hjælper dig med at beskytte og beskytte organisationens ressourcer.

Der er to muligheder for enhedshåndtering:

- [Microsoft Intune](#microsoft-intune)
- [Basic Mobility og Security](#basic-mobility-and-security)

## <a name="microsoft-intune"></a>Microsoft Intune

Du kan bruge Microsoft Intune til at administrere adgang til din organisation ved hjælp af administration af mobilenheder eller administration af mobilapps. Administration af mobilenheder er, når brugerne "tilmelder" deres enheder i Intune. Når en enhed er tilmeldt, er det en administreret enhed. derfor kan den modtage organisationens politikker, regler og indstillinger. Du kan f.eks. installere bestemte apps, oprette en adgangskodepolitik, installere en VPN-forbindelse og meget mere.

Brugere med deres egne personlige enheder vil muligvis ikke tilmelde deres enheder eller administreres af Intune og organisationens politikker. Men du skal stadig beskytte organisationens ressourcer og data. I dette scenarie kan du beskytte dine apps ved hjælp af administration af mobilapps. Du kan f.eks. bruge en politik for administration af mobilapps, der kræver, at en bruger angiver en pinkode, når der åbnes SharePoint Online på enheden.

Du bestemmer også, hvordan du skal administrere personlige enheder og enheder, der ejes af organisationen. Det kan være en god idé at behandle enheder forskelligt, afhængigt af deres anvendelse.

## <a name="basic-mobility-and-security"></a>Basic Mobility og Security

Dette er indbygget i Microsoft 365 og hjælper dig med at sikre og administrere dine brugeres mobilenheder, f.eks. iPhones, iPads, Androids og Windows telefoner. Du kan oprette og administrere politikker for enhedssikkerhed, fjerne sletning af en enhed og få vist detaljerede enhedsrapporter.

## <a name="choose-between-the-two-options"></a>Vælg mellem de to indstillinger

For at hjælpe dig med bedre at vurdere, hvilken mulighed for enhedshåndtering der er bedst for dig, skal du se [Vælg mellem grundlæggende mobilitetssikkerhed og Intune](/office365/securitycompliance/choose-between-mdm-and-intune).

Baseret på din vurdering kan du komme i gang med at administrere dine enheder med:

- [Intune](/microsoft-365/solutions/manage-devices-with-intune-overview)
- [Basic Mobility og Security](https://support.microsoft.com/office/set-up-basic-mobility-and-security-dd892318-bc44-4eb1-af00-9db5430be3cd)
 
## <a name="identity-and-device-access-recommendations"></a>Anbefalinger til identitets- og enhedsadgang

Microsoft giver en række anbefalinger til [identitets- og enhedsadgang](../security/office-365-security/microsoft-365-policies-configurations.md) for at sikre en sikker og produktiv arbejdsstyrke. Hvis du vil have adgang til enheden, skal du bruge anbefalingerne og indstillingerne i disse artikler:

- [Forudsætninger](../security/office-365-security/identity-access-prerequisites.md)
- [Fælles politikker for identitets- og enhedsadgang](../security/office-365-security/identity-access-policies.md)

## <a name="how-contoso-did-device-management-for-microsoft-365"></a>Sådan klarede Contoso enhedshåndtering for Microsoft 365

Du kan få mere at vide om, hvordan en fiktiv, men repræsentativ multinational virksomhed udrullede infrastrukturen til administration af mobilenheder med Microsoft 365 cloudtjenester, under [Administration af mobilenheder for Contoso](contoso-mdm.md).