---
title: Sammenlign politikindstillinger for enhedens overholdelse af regler og standarder i Microsoft 365 Lighthouse
f1.keywords: NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
ms-reviewer: ragovind
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
description: For MSP'er (Managed Service Providers) ved hjælp af Microsoft 365 Lighthouse kan du få mere at vide om, hvordan du sammenligner politikindstillinger for enhedens overholdelse af regler og standarder.
ms.openlocfilehash: 0a0c5127a86832637a16449e06c3df70299b49a3
ms.sourcegitcommit: 5e5c2c1f7c321b5eb1c5b932c03bdd510005de13
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/15/2022
ms.locfileid: "66822895"
---
# <a name="compare-device-compliance-policy-settings-in-microsoft-365-lighthouse"></a>Sammenlign politikindstillinger for enhedens overholdelse af regler og standarder i Microsoft 365 Lighthouse

Med Microsoft 365 Lighthouse kan du få vist politikker for overholdelse af angivne standarder på tværs af dine lejere i en enkelt visning. Du kan fremme sikkerhed og standardisering på tværs af dine lejere ved at sammenligne politikker. Du kan filtrere visninger for at se indstillinger, der er konfigureret (i forhold til indstillinger, der ikke er konfigureret), indstillinger, der er forskellige i deres konfigurationer, eller indstillinger, der stemmer overens. Du kan også søge efter specifikke indstillinger for at se, hvordan de kan sammenlignes på tværs af politikker.

## <a name="before-you-begin"></a>Før du begynder

Sørg for, at enheder har en Microsoft Intune licens og er tilmeldt Microsoft Endpoint Manager (MEM).

## <a name="compare-policy-settings"></a>Sammenlign politikindstillinger

1. Vælg **Enheder****Enhedsoverholdelse** >  i navigationsruden til venstre i Lighthouse.

2. Vælg fanen **Politikker** .

3. Vælg et operativsystem eller en platform på rullelisten **Filtre** .

   > [!NOTE]
   > Du kan kun sammenligne politikker med det samme operativsystem eller den samme platform.

4. Vælg op til tre politikker, som du vil sammenligne, på den filtrerede liste.

5. Vælg **Sammenlign**.

Du kan filtrere resultaterne for at se **indstillinger, der er forskellige**, **indstillinger, der stemmer overens**, eller **Konfigurerede indstillinger**.

## <a name="configure-a-policy-setting"></a>Konfigurer en politikindstilling

1. Vælg **Enheder****Enhedsoverholdelse** >  i navigationsruden til venstre i Lighthouse.

2. Vælg fanen **Politikker** .

3. Vælg et politiknavn på listen.

4. I ruden Politikoplysninger skal du vælge **Få vist denne politik i Microsoft Endpoint Manager**.

5. Rediger politikindstillingerne efter behov i MEM.

## <a name="next-steps"></a>Næste trin

Når du foretager politikjusteringer, skal du sørge for at vurdere dine ændringer i forhold til dine aktuelle indstillinger for grundlinjer. Du kan få flere oplysninger under [Oversigt over brug af grundlinjer til installation af standardlejerkonfigurationer](m365-lighthouse-deploy-standard-tenant-configurations-overview.md).

## <a name="related-content"></a>Relateret indhold

[Hvad er tilmelding af enheder i Intune?](/mem/intune/enrollment/device-enrollment) (artikel)  
[Brug politikker for overholdelse af regler og standarder til at angive regler for enheder, du administrerer med Intune](/mem/intune/protect/device-compliance-get-started) (artikel)  
[Oversigt over brug af Microsoft 365 Lighthouse Baselines til installation af standardlejerkonfigurationer](m365-lighthouse-deploy-standard-tenant-configurations-overview.md) (artikel)
