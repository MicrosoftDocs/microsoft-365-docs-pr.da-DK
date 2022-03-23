---
title: Brug en QR-kode til at logge på Outlook mobilapps
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
description: Lær at bruge en QR-kode til at godkende og downloade Outlook mobile.
ms.openlocfilehash: 736628fb97cf2a6f4f6c6d175384a30c41bf642d
ms.sourcegitcommit: 7f0c5b55e2966c0c1ce6a153a4e6a7ec035bd818
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/22/2021
ms.locfileid: "63592577"
---
# <a name="use-a-qr-code-to-sign-in-to-the-outlook-mobile-apps"></a>Brug en QR-kode til at logge på Outlook mobilapps

Som administrator Microsoft 365 du give dine brugere mulighed for at logge på Outlook til Android- eller iOS-appen på deres mobilenheder uden at skulle angive deres brugernavn og adgangskode. Ved at scanne en QR-kode kan brugerne godkende sikkert og logge på Outlook mobile.

I Outlook på internettet eller andre Outlook programmer vil brugerne muligvis se meddelelser om, at de kan bruge Outlook på deres mobilenhed. Disse meddelelser kan administreres af administratoren ved hjælp Exchange PowerShell. Hvis brugerne vælger at sende sig selv en sms-besked for at downloade appen på deres mobilenhed, vises der en QR-kode på deres computer. De vil kunne scanne QR-koden for at logge på Outlook deres telefon eller tablet. Denne QR-kode er et kort, løst token, der kun kan indløses én gang.

Meddelelsen genereres kun, hvis følgende betingelser er opfyldt:

1. QR-kodeoplevelsen er aktiveret for lejeren (denne oplevelse er aktiveret som standard).

2. Brugeren bruger ikke allerede en Outlook til iOS og Android.

3. Brugeren har en tom tilstand i læseruden (vælger ikke muligheden for at åbne den første mail automatisk).

4. Brugeren afviste ikke meddelelsen.

> [!NOTE]
> I nogle tilfælde skal brugerne godkende igen på deres computer for at generere QR-koden.

## <a name="use-exchange-powershell"></a>Brug Exchange PowerShell

Denne funktion er som standard markeret. Følg nedenstående trin for at deaktivere denne funktion.

1. [Forbind til Exchange PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).
2. Ved hjælp af PowerShell kan du deaktivere meddelelser, der informerer dine brugere om Outlook-mobilapps. Dette forhindrer også, at logonflowet til QR-koden vises.

```powershell
Set-OrganizationConfig -MobileAppEducationEnabled <Boolean>
```

> [!NOTE]
> Når du bruger Exchange PowerShell-kommandoen, kan det tage op til otte timer, før ændringerne er overført.

## <a name="related-content"></a>Relateret indhold

[Konfigurer Standard eller Målrettede udgivelsesindstillinger](release-options-in-office-365.md) (artikel)\
[Set-OrganizationConfig](/powershell/module/exchange/set-organizationconfig) (artikel)
