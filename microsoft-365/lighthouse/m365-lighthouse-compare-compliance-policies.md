---
title: Sammenlign indstillinger for politikker for overholdelse af enhed
f1.keywords: NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: article
ms.prod: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- M365-Lighthouse
search.appverid: MET150
description: For administrerede tjenesteudbydere ved hjælp af Microsoft 365 Lighthouse kan du se, hvordan du sammenligner politikindstillinger for enhedsoverholdelse.
ms.openlocfilehash: 30645ef4d59fcdee0d994ae709ff9bb45fc21b09
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63594130"
---
# <a name="compare-device-compliance-policy-settings"></a>Sammenlign indstillinger for politikker for overholdelse af enhed

Microsoft 365 Lighthouse giver dig mulighed for at få vist overholdelsespolitikker på tværs af dine lejere i en enkelt visning. Du kan fremme sikkerhed og standardisering på tværs af dine lejere ved at sammenligne politikker. Du kan filtrere visninger for at få vist indstillinger, der er blevet konfigureret (kontra de indstillinger, der ikke blev konfigureret), indstillinger, der er forskellige i deres konfigurationer, eller indstillinger, der matcher. Du kan også søge efter bestemte indstillinger for at se, hvordan de kan sammenlignes på tværs af politikker.

## <a name="before-you-begin"></a>Før du begynder

Kontrollér, at enheder har Microsoft Intune licens og er tilmeldt Microsoft Endpoint Manager (MEM).

## <a name="compare-policy-settings"></a>Sammenlign politikindstillinger

1. I venstre navigationsrude i Fyrtårn skal du vælge **Enheder**.

2. Vælg **fanen** Politikker.

3. Vælg **et** operativsystem eller en platform på rullelisten Filtre.

   > [!NOTE]
   > Du kan kun sammenligne politikker med det samme operativsystem eller den samme platform.

4. Vælg op til tre politikker, du vil sammenligne, på den filtrerede liste.

5. Vælg **Sammenlign**.

Du kan filtrere resultaterne for at se **Indstillinger, der er** forskellige, **Indstillinger, der matcher**, **eller Konfigurerede indstillinger**.

## <a name="configure-a-policy-setting"></a>Konfigurere en politikindstilling

1. I venstre navigationsrude i Fyrtårn skal du vælge **Enheder**.

2. Vælg **fanen** Politikker.

3. Vælg et politiknavn på listen.

4. I ruden Politikdetaljer skal du **vælge Vis denne politik i Microsoft Endpoint Manager**.

5. Rediger politikindstillingerne efter behov i MEM.

## <a name="next-steps"></a>Næste trin

Når du foretager justeringer af politikker, skal du sørge for at vurdere dine ændringer i forhold til dine aktuelle indstillinger for oprindelige planer. Få mere at vide under Oversigt [over brug af grundlinjer til installation af standardlejerkonfigurationer](m365-lighthouse-deploy-standard-tenant-configurations-overview.md).

## <a name="related-content"></a>Relateret indhold

[Hvad er tilmelding af enheder i Intune?](/mem/intune/enrollment/device-enrollment) (artikel)  
[Brug politikker for overholdelse af regler og standarder til at angive regler for enheder, du administrerer med Intune](/mem/intune/protect/device-compliance-get-started) (artikel)  
[Oversigt over brug af oprindelige planer til installation af standardlejerkonfigurationer](m365-lighthouse-deploy-standard-tenant-configurations-overview.md) (artikel)
