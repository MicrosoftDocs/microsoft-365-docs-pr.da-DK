---
title: Opret indikatorer for IP'er og URL-adresser/domæner
ms.reviewer: ''
description: Opret indikatorer for IP-adresser og URL-adresser/domæner, der definerer registrering, forebyggelse og udeladelse af enheder.
keywords: ip, URL-adresse, domæne, administrere, tilladt, blokeret, blokere, ren, skadelig, filhash, IP-adresse, URL-adresser, domæne
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 955f11aa44bd0defb867c25124da7c5a3769c98d
ms.sourcegitcommit: a7cd723fd62b4b0aae9c2c2df04ead3c28180084
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/02/2022
ms.locfileid: "65840107"
---
# <a name="create-indicators-for-ips-and-urlsdomains"></a>Opret indikatorer for IP'er og URL-adresser/domæner

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> [!TIP]
> Vil du opleve Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-automationexclusionlist-abovefoldlink)

Defender for Endpoint kan blokere det, som Microsoft anser for skadelige IP-adresser, via Windows Defender SmartScreen til Microsoft-browsere og via Network Protection for ikke-Microsoft-browsere eller opkald, der foretages uden for en browser.

Datasættet til trusselsintelligens er blevet administreret af Microsoft.

Ved at oprette indikatorer for IP-adresser og URL-adresser eller domæner kan du nu tillade eller blokere IP-adresser, URL-adresser eller domæner baseret på din egen trusselsintelligens. Du kan også advare brugerne med en prompt, hvis de åbner en risikable app. Prompten forhindrer dem ikke i at bruge appen, men du kan angive en brugerdefineret meddelelse og links til en firmaside, der beskriver korrekt brug af appen. Brugerne kan stadig tilsidesætte advarslen og fortsætte med at bruge appen, hvis de har brug for det.

Det kan du gøre via indstillingssiden eller computergrupper, hvis du anser visse grupper for at være mere eller mindre udsatte end andre.

> [!NOTE]
> CIDR-notation (Classless Inter-Domain Routing) for IP-adresser understøttes ikke.

## <a name="before-you-begin"></a>Før du begynder

Det er vigtigt at forstå følgende forudsætninger, før du opretter indikatorer for IPS, URL-adresser eller domæner:

- URL-adresse/IP-tilladelse og -blokering er afhængig af, at Defender for Endpoint-komponenten Network Protection aktiveres i blokeringstilstand. Du kan finde flere oplysninger om Netværksbeskyttelse og konfigurationsinstruktioner under [Aktivér netværksbeskyttelse](enable-network-protection.md).
- Antimalware-klientversionen skal være 4.18.1906.x eller nyere. 
- Understøttes på computere på Windows 10, version 1709 eller nyere, Windows 11, Windows Server 2016, Windows Server 2012 R2, Windows Server 2019, Windows Server 2022 og Android- og iOS-enheder.

    > [!NOTE]
    > Windows Server 2016 og Windows Server 2012 R2 skal onboardes ved hjælp af vejledningen i [Onboard Windows-servere](configure-server-endpoints.md#windows-server-2012-r2-and-windows-server-2016), for at denne funktion kan fungere.

- Sørg for, at **brugerdefinerede netværksindikatorer** er aktiveret i **Microsoft 365 Defender** \> **Indstillinger** \> **Avancerede funktioner**. Du kan få flere oplysninger under [Avancerede funktioner](advanced-features.md).
- Hvis du vil have hjælp til indikatorer på iOS, [skal du se Microsoft Defender for Endpoint på iOS](/microsoft-365/security/defender-endpoint/ios-configure-features#configure-custom-indicators).
- Hvis du vil have hjælp til indikatorer på Android, [skal du se Microsoft Defender for Endpoint på Android](/microsoft-365/security/defender-endpoint/android-configure#configure-custom-indicators).

> [!IMPORTANT]
> Det er kun eksterne IP-adresser, der kan føjes til indikatorlisten. Der kan ikke oprettes indikatorer for interne IP-adresser.
> I forbindelse med webbeskyttelsesscenarier anbefaler vi, at du bruger de indbyggede funktioner i Microsoft Edge. Microsoft Edge udnytter [Network Protection](network-protection.md) til at inspicere netværkstrafik og tillader blokke for TCP, HTTP og HTTPS (TLS).
> Hvis der er modstridende politikker for URL-indikator, anvendes den længere sti. URL-indikatorpolitikken `https://support.microsoft.com/office` har f.eks. forrang frem for URL-indikatorpolitikken `https://support.microsoft.com`.

> [!NOTE]
> I forbindelse med alle andre processer anvender webbeskyttelsesscenarier Netværksbeskyttelse til inspektion og håndhævelse:
>
> - IP understøttes for alle tre protokoller
> - Kun enkelte IP-adresser understøttes (ingen CIDR-blokke eller IP-områder)
> - Krypterede URL-adresser (fuld sti) kan kun blokeres i førstepartsbrowsere (Internet Explorer, Edge)
> - Krypterede URL-adresser (kun FQDN) kan blokeres uden for førstepartsbrowsere (Internet Explorer, Edge)
> - Fulde URL-stiblokke kan anvendes på domæneniveau og alle ukrypterede URL-adresser
>
> Der kan være op til to timers ventetid (normalt mindre) mellem det tidspunkt, hvor handlingen udføres, og URL-adressen og IP-adressen blokeres.

Når du bruger advarselstilstanden, kan du konfigurere følgende kontrolelementer:

**Overløbs evne**:

- Knappen Tillad i Edge
- Knappen Tillad på toast (ikke-Microsoft-browsere)
- Overløb varighedsparameteren på indikatoren
- Tilsidesæt håndhævelse på tværs af Microsoft- og ikke-Microsoft-browsere

**URL-adresse til omdirigering**:

- URL-parameter for omdirigering på indikatoren
- URL-adresse til omdirigering i Edge
- URL-adresse til omdirigering på toast (ikke-Microsoft-browsere)

Du kan finde flere oplysninger under [Styr de apps, der registreres af Microsoft Defender for Endpoint](/cloud-app-security/mde-govern).

## <a name="create-an-indicator-for-ips-urls-or-domains-from-the-settings-page"></a>Opret en indikator for IP-adresser, URL-adresser eller domæner fra indstillingssiden

1. Vælg **Indstillinger** \> **Slutpunktsindikatorer** \> (under **Regler**) i navigationsruden.

2. Vælg fanen **IP-adresser eller URL-adresser/domæner** .

3. Vælg **Tilføj element**.

4. Angiv følgende oplysninger:
   - Indikator – Angiv enhedsoplysningerne, og definer indikatorens udløb.
   - Handling – Angiv den handling, der skal udføres, og angiv en beskrivelse.
   - Scope – Definer omfanget af computergruppen.

5. Gennemse oplysningerne under fanen Oversigt, og klik derefter på **Gem**.

## <a name="related-topics"></a>Relaterede emner

- [Opret indikatorer](manage-indicators.md)
- [Opret indikatorer for filer](indicator-file.md)
- [Opret indikatorer baseret på certifikater](indicator-certificates.md)
- [Administrer indikatorer](indicator-manage.md)
