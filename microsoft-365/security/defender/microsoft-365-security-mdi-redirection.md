---
title: Omdirigering af konti fra Microsoft Defender for Identity til Microsoft 365 Defender
description: Sådan omdirigerer du konti og sessioner fra Defender for Identity til Microsoft 365 Defender.
keywords: Microsoft 365 Defender, Introduktion til Microsoft 365 Defender, omdirigering af Sikkerhedscenter
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
ms.custom: admindeeplinkDEFENDER
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: b5c122f01d37d066e0f20bf817ca45ad5c57480b
ms.sourcegitcommit: 5fe7f2954a89406245416fc1a218cf4bf19abb85
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/03/2022
ms.locfileid: "66858658"
---
# <a name="redirecting-accounts-from-microsoft-defender-for-identity-to-microsoft-365-defender"></a>Omdirigering af konti fra Microsoft Defender for Identity til Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Gælder for:**

- Microsoft 365 Defender
- Defender for Identity

I denne vejledning forklares det, hvordan du dirigerer konti til Microsoft 365 Defender ved at aktivere automatisk omdirigering fra den tidligere Microsoft Defender for Identity portal (portal.atp.azure.com) for at <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a>.

## <a name="what-to-expect"></a>Hvad kan du forvente?

Når automatisk omdirigering er aktiveret, dirigeres konti, der tilgår den tidligere Microsoft Defender for Identity portal på portal.atp.azure.com, automatisk til Microsoft 365 Defender-portalen på <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">security.microsoft.com</a>.

## <a name="when-does-this-take-effect"></a>Hvornår træder dette i kraft?

Når denne opdatering er aktiveret, kan den træde i kraft næsten med det samme for nogle konti. Men omdirigeringen kan tage længere tid at overføre til alle konti i din organisation. Konti i aktive sessioner, mens denne indstilling anvendes, bliver ikke sendt fra deres session og distribueres kun til Microsoft 365 Defender, når den aktuelle session er afsluttet og logger på igen.  

### <a name="set-up-portal-redirection"></a>Konfigurer portalomdirigering

Sådan starter du distribution af konti til Microsoft 365 Defender:

1. Kontrollér, at du er global administrator, eller at du har sikkerhedsadministratortilladelser i Azure Active Directory.

1. Log på <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a>.

1. Gå til **Indstillinger** > **Identiteter** > **Generel** > **portalomdirigering** , eller [klik her](https://security.microsoft.com/preferences2/portal_redirection).

    :::image type="content" source="../../media/portal-redirection.png" alt-text="Portalomdirigering."lightbox="../../media/portal-redirection.png":::

1. Slå indstillingen For automatisk omdirigering til **Til**.

>[!IMPORTANT]
>Aktivering af denne indstilling afslutter ikke aktive brugersessioner. Konti, der er i en aktiv session, mens denne indstilling anvendes, sendes kun til Microsoft 365 Defender, når de har afsluttet deres aktuelle session og logget på igen.

>[!NOTE]
>Du skal være global administrator eller have sikkerhedsadministratortilladelser i Azure Active Directory for at aktivere eller deaktivere denne indstilling.  

## <a name="can-i-go-back-to-using-the-former-portal"></a>Kan jeg gå tilbage til den tidligere portal?

Hvis noget ikke fungerer for dig, eller hvis der er noget, du ikke kan fuldføre gennem Microsoft 365 Defender, vil vi gerne høre om det. Hvis du har oplevet problemer med omdirigering, opfordrer vi dig til at fortælle os det ved hjælp af formularen Send feedback.

Sådan vender du tilbage til den tidligere Microsoft Defender for Identity portal:

1. Log på <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> som global administrator eller bruge og -konto med sikkerhedsadministratortilladelser i Azure Active Directory.

2. Gå til **Indstillinger** > **Identiteter** > **Generel** > **portalomdirigering** , eller [åbn siden her](https://security.microsoft.com/preferences2/portal_redirection).  

3. Slå indstillingen Automatisk omdirigering til **Fra**.

Denne indstilling kan aktiveres igen når som helst.

Når konti er deaktiveret, distribueres de ikke længere til security.microsoft.com.

## <a name="related-information"></a>Relaterede oplysninger

- [Oversigt over Microsoft 365 Defender-portalen](microsoft-365-defender.md)
- [Om Microsoft 365 Defender](https://www.microsoft.com/microsoft-365/security/microsoft-365-defender)
- [Microsofts sikkerhedsportaler og administrationscentre](portals.md)
