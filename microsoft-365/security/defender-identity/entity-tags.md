---
title: Microsoft Defender for Identity-enhedsmærker i Microsoft 365 Defender
description: Få mere at vide om, hvordan du anvender Microsoft Defender til identitetsenhedsmærker i Microsoft 365 Defender
ms.date: 06/08/2021
ms.topic: how-to
author: dcurwin
ms.author: dacurwin
ms.service: microsoft-defender-for-identity
ms.custom: admindeeplinkDEFENDER
manager: raynew
ms.openlocfilehash: e53c14405d3d190715b49e58061aee8ba771180a
ms.sourcegitcommit: 542e6b5d12a8d400c3b9be44d849676845609c5f
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/15/2021
ms.locfileid: "63606646"
---
# <a name="defender-for-identity-entity-tags-in-microsoft-365-defender"></a>Defender for Identity-enhedsmærker i Microsoft 365 Defender

**Gælder for:**

- Microsoft 365 Defender
- Defender for Identity

I denne artikel forklares det, [hvordan du anvender Microsoft Defender for Identity-enhedsmærker](/defender-for-identity) [i Microsoft 365 Defender](/microsoft-365/security/defender/overview-security-center).

>[!IMPORTANT]
>Som en del af dine Microsoft 365 Defender har nogle indstillinger og detaljer ændret sig fra deres placering i Defender for Identity-portalen. Læs oplysningerne nedenfor for at finde ud af, hvor du kan finde både de velkendte og nye funktioner.

## <a name="entity-tags"></a>Enhedsmærker

I Microsoft 365 Defender kan du angive tre typer Defender for Identity-enhedsmærker: Følsomme **mærker**, **Honeytoken-mærker** **Exchange servermærker**.

Hvis du vil angive disse mærker <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">, Microsoft 365 Defender</a> du gå **til Indstillinger** og derefter **Identities**.

![Gå til Indstillinger og derefter Identities.](../../media/defender-identity/settings-identities.png)

Mærkeindstillingerne vises under **Enhedsmærker**.

![Typer af mærkeindstillinger.](../../media/defender-identity/tag-settings.png)

Følg vejledningen nedenfor for at angive hver type mærke.

## <a name="sensitive--tags"></a>Følsomme mærker

Mærket **Følsom bruges** til at identificere aktiver med høj værdi. Den laterale bevægelsessti afhænger også af en enheds følsomhedsstatus. Nogle enheder betragtes automatisk som følsomme af Defender for Identity. Du kan finde en liste over disse aktiver [under Følsomme enheder](/defender-for-identity/manage-sensitive-honeytoken-accounts#sensitive-entities).

Du kan også manuelt markere brugere, enheder eller grupper som følsomme.

1. Vælg **Følsom**. Du får derefter vist de eksisterende **følsomme brugere****, enheder** og **grupper**.

    ![Følsomme enheder.](../../media/defender-identity/sensitive-entities.png)

1. Under hver kategori skal du **vælge Tag...** for at mærke den pågældende type enhed. Under Grupper skal **du f.eks**. **vælge Tag grupper.** En rude åbnes med de grupper, du kan vælge at mærke. Hvis du vil søge efter en gruppe, skal du skrive dens navn i søgefeltet.

    ![Tilføj grupper.](../../media/defender-identity/add-groups.png)

1. Vælg din gruppe, og klik på **Tilføj markering.**

    ![Tilføj markering.](../../media/defender-identity/add-selection.png)

## <a name="honeytoken-tags"></a>Honeytoken-mærker

Honeytoken-enheder bruges som fanger af ondsindede aktører. Enhver godkendelse, der er knyttet til disse honeytoken-enheder, udløser en besked.

Du kan mærke brugere eller enheder med **mærket Honeytoken** på samme måde, som du mærker følsomme konti.

1. Vælg **Honeytoken**. Du får derefter vist de eksisterende **honeytoken-brugere** og **-enheder**.

    ![Honeytoken-enheder.](../../media/defender-identity/honeytoken-entities.png)

1. Under hver kategori skal du **vælge Tag...** for at mærke den pågældende type enhed. Eksempelvis skal du under **Brugere** vælge **Tag brugere.** En rude åbnes med de grupper, du kan vælge at mærke. Hvis du vil søge efter en gruppe, skal du skrive dens navn i søgefeltet.

    ![Tilføj brugere.](../../media/defender-identity/add-users.png)

1. Vælg din bruger, og klik på **Tilføj markering.**

    ![Tilføj valgt bruger.](../../media/defender-identity/add-selected-user.png)

## <a name="exchange-server-tags"></a>Exchange servermærker

Defender for Identity opfatter Exchange-servere som aktiver med høj værdi og mærker dem automatisk som **Følsomme**. Du kan også manuelt mærke enheder som Exchange servere.

1. Vælg **Exchange server**. Du får derefter vist de eksisterende enheder med navnet Exchange **servermærket**.

    ![Exchange-servere.](../../media/defender-identity/exchange-servers.png)

1. Hvis du vil mærke en enhed som Exchange server, skal du vælge **Tag enheder**.  En rude åbnes med de enheder, du kan vælge at mærke. Hvis du vil søge efter en enhed, skal du skrive dens navn i søgefeltet.

    ![Tilføj enheder.](../../media/defender-identity/add-devices.png)

1. Vælg din enhed, og klik **på Tilføj markering.**

    ![Vælg enhed.](../../media/defender-identity/select-device.png)

## <a name="see-also"></a>Se også

- [Administrer sikkerhedsadvarsler for Defender for Identity](manage-security-alerts.md)
