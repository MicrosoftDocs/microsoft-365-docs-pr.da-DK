---
title: Windows 10 placeringstjeneste
description: Beskrivelse af, hvordan du Windows placeringstjenester slået til for dine enheder
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
ms.openlocfilehash: b12f0d188c8347762443cc80e24cfdd7c6280acc
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/04/2022
ms.locfileid: "63592779"
---
# <a name="windows-10-location-service"></a>Windows 10 placeringstjeneste

Enheder i Microsoft Managed Desktop registreres ved hjælp af Windows Autopilot. Med denne proces kan vi administrere dem med Azure Active Directory og Microsoft Intune.

Tjenesten Windows 10-placering er som standard deaktiveret, når en enhed aktiveres for første gang, medmindre denne funktion er aktiveret i indstillingerne for beskyttelse af personlige oplysninger under "standardoplevelsen". Disse indstillinger er skjult under Autopilot-registrering i Microsoft Managed Desktop. Du kan finde flere oplysninger om, hvordan AutoPilot er konfigureret, under Første kørsel med [Autopilot og Statussiden For tilmelding](esp-first-run.md).

Derfor kan Microsoft-administrerede skrivebordsenheder ikke hente deres placering på enheden og begrænser funktionaliteten af flere Windows, f.eks. tidszoner. Du kan finde flere oplysninger Windows 10 placeringstjenesten i [Windows 10-placeringstjenesten og beskyttelse af personlige oplysninger](https://support.microsoft.com/windows/windows-10-location-service-and-privacy-3a8eee0a-5b0b-dc07-eede-2a5ca1c49088).

Du behøver ikke at bruge placeringstjenesten for at kunne deltage i Microsoft Managed Desktop. Brugeroplevelsen begrænses. Enheder vil f.eks. ikke automatisk kunne bestemme den tidszone, de er i, når dine brugere arbejder i en anden tidszone.

## <a name="enable-the-location-service"></a>Aktivér placeringstjenesten

Du kan enten:

- Tilmeld dig for at bruge placeringstjenesten, når du tilmelder enheder til Microsoft Managed Desktop-tjenesten, eller
- Du kan slå tjenesten til eller fra efter tilmelding.

### <a name="opt-in-during-enrollment"></a>Tilmeld dig under tilmelding

Du kan få tjenesten Microsoft Managed Desktop til at aktivere placeringstjenesten. Under tilmeldingssekvensen bliver du bedt om at vælge, om du vil tillade, Windows 10 placeringstjenesten er aktiveret på enheder.

### <a name="control-the-location-service-after-enrollment"></a>Styr placeringstjenesten efter tilmeldingen

Du kan når som helst have placeringstjenesten slået til (eller fra) ved at sende en [supportanmodning](../working-with-managed-desktop/admin-support.md) via [administratorportalen](access-admin-portal.md).

## <a name="how-microsoft-managed-desktop-configures-the-windows-10-location-service"></a>Sådan konfigurerer Microsoft Managed Desktop Windows 10 placeringstjenesten

Hvis du vælger at bruge placeringstjenesten, bruger vi de nødvendige minimumindstillinger uden at påvirke brugernes personlige oplysninger. Du kan finde flere oplysninger Windows 10 [placeringstjenesten og beskyttelse af personlige oplysninger](https://support.microsoft.com/windows/windows-10-location-service-and-privacy-3a8eee0a-5b0b-dc07-eede-2a5ca1c49088).

Microsoft Managed Desktop aktiverer indstillingen **placering for beskyttelse** af **personlige oplysninger Windows indstillingerne for** **Tillad adgang til placering på denne enhed**. Brugergrænsefladen ser sådan ud:

 :::image type="content" source="../../media/MMD-location-services-UI.png" alt-text="Indstillinger for placering Windows indstillingerne.":::

> [!NOTE]
> Hvis du vælger at bruge placeringstjenesten, gælder dette kun for Windows selve operativsystemet. Apps har ikke tilladelse til at bruge placeringstjenester. Hver bruger kan vælge, om de vil give apps adgang til deres placering.
