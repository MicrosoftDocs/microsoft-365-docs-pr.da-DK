---
title: Microsoft Defender for Identity VPN-integration i Microsoft 365 Defender
description: Lær at indsamle regnskabsoplysninger ved at integrere et VPN til Microsoft Defender for Identity i Microsoft 365 Defender
ms.date: 06/07/2021
ms.topic: how-to
author: dcurwin
ms.author: dacurwin
ms.service: microsoft-defender-for-identity
ms.custom: admindeeplinkDEFENDER
manager: raynew
ms.collection: M365-security-compliance
ms.openlocfilehash: a5c45ecda43b32e37f7309b9a2de33810d60bd15
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64469157"
---
# <a name="defender-for-identity-vpn-integration-in-microsoft-365-defender"></a>Defender til VPN-integration af identitet i Microsoft 365 Defender

**Gælder for:**

- Microsoft 365 Defender
- Defender for Identity

Denne artikel forklarer, hvordan du integrerer et [VPN Microsoft Defender for Identity](/defender-for-identity) i [Microsoft 365 Defender](/microsoft-365/security/defender/overview-security-center).

>[!IMPORTANT]
>Som en del af dine <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> har nogle indstillinger og detaljer ændret sig fra deres placering i Defender for Identity-portalen. Læs oplysningerne nedenfor for at finde ud af, hvor du kan finde både de velkendte og nye funktioner.

[!INCLUDE [Product long](includes/product-long.md)] kan indsamle regnskabsoplysninger fra VPN-løsninger. Når konfigureret, indeholder brugerens profilside oplysninger fra VPN-forbindelser, f.eks. IP-adresser og placeringer, hvor forbindelserne stammer fra. Dette supplerer undersøgelsesprocessen ved at give yderligere oplysninger om brugeraktivitet samt en ny registrering for unormale VPN-forbindelser. Opkaldet for at løse en ekstern IP-adresse til en placering er anonymt. Der sendes ingen personligt id i dette opkald.

[!INCLUDE [Product short](includes/product-short.md)] integreres med din VPN-løsning ved at lytte til RADIUS-revisionshændelser, der videresendes til sensorerne [!INCLUDE [Product short](includes/product-short.md)] . Denne mekanisme er baseret på standard RADIUS Accounting ([RFC 2866](https://tools.ietf.org/html/rfc2866)), og følgende VPN-leverandører understøttes:

- Microsoft
- F5
- Kontrolpunkt
- Cisco ASA

## <a name="prerequisites"></a>Forudsætninger

Hvis du vil aktivere VPN-integration, skal du sørge for at angive følgende parametre:

- Åbn port UDP 1813 på dine sensorer [!INCLUDE [Product short](includes/product-short.md)] og/eller [!INCLUDE [Product short](includes/product-short.md)] enkeltstående sensorer.

> [!NOTE]
>
> - Ved at aktivere **Radius Accounting** aktiverer [!INCLUDE [Product short](includes/product-short.md)] sensoren en forudinstalleret Windows firewallpolitik **[!INCLUDE [Product long](includes/product-long.md)] kaldet Sensor** for at tillade indgående RADIUS Accounting på port UDP 1813.
> - VPN-integration understøttes ikke i miljøer, der opfylder føderale FIPS-standarder (Information Processing Standards)

Eksemplet nedenfor bruger Microsoft Routing og RRAS (Remote Access Server) til at beskrive VPN-konfigurationsprocessen.

Hvis du bruger en tredjeparts VPN-løsning, skal du se i dokumentationen for at få instruktioner om, hvordan du aktiverer RADIUS Accounting.

## <a name="configure-radius-accounting-on-the-vpn-system"></a>Konfigurere RADIUS Accounting på VPN-systemet

Udfør følgende trin på RRAS-serveren.

1. Åbn konsollen **Routing og Fjernadgang** .
1. Højreklik på servernavnet, og vælg **Egenskaber**.
1. På fanen **Sikkerhed** under **Regnskabsudbyder skal du** vælge **RADIUS Accounting** og vælge **Konfigurer**.

   :::image type="content" source="../../media/defender-identity/radius-setup.png" alt-text="Radius-konfigurationen" lightbox="../../media/defender-identity/radius-setup.png":::

1. I vinduet **Tilføj RADIUS-server** skal du skrive **Servernavnet på** den nærmeste [!INCLUDE [Product short](includes/product-short.md)] sensor (som har netværksforbindelse). Ved høj tilgængelighed kan du tilføje yderligere sensorer [!INCLUDE [Product short](includes/product-short.md)] som RADIUS-servere. **Kontrollér,** at standardværdien på 1813 er konfigureret under Port. Vælg **Rediger** , og skriv en ny delt hemmelig streng med alfanumeriske tegn. Vær opmærksom på den nye, hemmelige streng, som du skal udfylde senere under [!INCLUDE [Product short](includes/product-short.md)] konfigurationen. Markér **afkrydsningsfeltet Send RADIUS-konto til og Bogføring fra,** og **vælg OK** i alle åbne dialogbokse.

   :::image type="content" source="../../media/defender-identity/vpn-set-accounting.png" alt-text="VPN-konfigurationen" lightbox="../../media/defender-identity/vpn-set-accounting.png":::

## <a name="configure-vpn-in-defender-for-identity"></a>Konfigurer VPN i Defender for Identity

[!INCLUDE [Product short](includes/product-short.md)] indsamler VPN-data, der hjælper med at profilere de placeringer, hvorfra computere opretter forbindelse til netværket, og for at kunne registrere mistænkelige VPN-forbindelser.

Sådan konfigurerer du VPN-data [!INCLUDE [Product short](includes/product-short.md)] i Microsoft 365 Defender:

1. I <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> skal du gå **til Indstillinger** og derefter **Identities**.

   :::image type="content" source="../../media/defender-identity/settings-identities.png" alt-text="Indstillingen Identiteter under menuelementet Indstillinger" lightbox="../../media/defender-identity/settings-identities.png":::

1. Vælg **VPN**.
1. Vælg **Aktivér radiusregnskab**, og skriv **Den Delte hemmelighed,** du konfigurerede tidligere på din RRAS VPN-server. Vælg derefter **Gem**.

   :::image type="content" source="../../media/defender-identity/vpn-integration.png" alt-text="VPN-integration" lightbox="../../media/defender-identity/vpn-integration.png":::

Når dette er aktiveret, lytter alle Defender til identitetssensorer på port 1813 til RADIUS-revisionshændelser, og din VPN-konfiguration er fuldført.

Når Sensoren Defender for Identity modtager VPN-hændelserne og sender dem til den skybaserede Defender for Identity-tjeneste til behandling, angiver enhedsprofilen særskilte adgangsplaceringer og aktiviteter i profilen for at angive placeringer.

## <a name="see-also"></a>Se også

- [Undersøg beskeder i Microsoft 365 Defender](../defender/investigate-alerts.md)
