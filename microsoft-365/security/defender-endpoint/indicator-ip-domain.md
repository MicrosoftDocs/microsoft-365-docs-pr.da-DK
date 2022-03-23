---
title: Opret indikatorer for IP'er og URL-adresser/domæner
ms.reviewer: ''
description: Opret indikatorer for IP'er og URL-adresser/domæner, der definerer registrering, forebyggelse og udelukkelse af enheder.
keywords: ip, url, domæne, administrer, tilladt, blokeret, bloker, ren, skadelig, filhash, IP-adresse, URL-adresser, domæne
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
ms.openlocfilehash: 8865bf2138947238980b533b8b47ee9663fd5448
ms.sourcegitcommit: dd6514ae173f1c821d4ec25298145df6cb232e2e
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/19/2022
ms.locfileid: "63591900"
---
# <a name="create-indicators-for-ips-and-urlsdomains"></a>Opret indikatorer for IP'er og URL-adresser/domæner

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> [!TIP]
> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-automationexclusionlist-abovefoldlink)

Defender til slutpunkt kan blokere, hvad Microsoft anser som skadelige IP'er/URL-adresser, via Windows Defender SmartScreen til Microsoft-browsere og via Netværksbeskyttelse til browsere, der ikke er Microsoft, eller opkald, der foretages uden for en browser.

Datasættet trusselsintelligens for dette er blevet administreret af Microsoft.

Ved at oprette indikatorer for IP'er og URL-adresser eller domæner kan du nu tillade eller blokere IP'er, URL-adresser eller domæner baseret på din egen trusselsintelligens. Du kan også advare brugere med en meddelelse, hvis de åbner en risikabel app. Prompten kan ikke forhindre dem i at bruge appen, men du kan angive en brugerdefineret meddelelse og links til en virksomhedsside, der beskriver den relevante brug af appen. Brugere kan stadig springe advarslen over og fortsætte med at bruge appen, hvis de har brug for det.

Du kan gøre dette via indstillingssiden eller efter maskingrupper, hvis du mener, at visse grupper er mere eller mindre udsat end andre.

> [!NOTE]
> CIDR-notation (Classless Inter-Domain Routing) for IP-adresser understøttes ikke.

## <a name="before-you-begin"></a>Før du begynder

Det er vigtigt at forstå følgende forudsætninger, før du opretter indikatorer for IPS, URL-adresser eller domæner:

- Tilladelse og blokering af URL-adresse/IP afhænger af, at Defender for Endpoint-komponenten Network Protection er aktiveret i blokeringstilstand. Du kan finde flere oplysninger om netværksbeskyttelse og konfigurationsinstruktioner [i Aktivér netværksbeskyttelse](enable-network-protection.md).
- Versionen af Antimalware-klienten skal være 4.18.1906.x eller nyere. 
- Understøttes på computere på Windows 10, version 1709 eller nyere, Windows 11, Windows Server 2016, Windows Server 2012 R2, Windows Server 2019 og Windows Server 2022.

    > [!NOTE]
    > Windows Server 2016 og Windows Server 2012 R2 skal være onboardet ved hjælp af instruktionerne i [Onboard Windows-servere](configure-server-endpoints.md#windows-server-2012-r2-and-windows-server-2016), for at denne funktion kan fungere.

- Sørg for **, at Brugerdefinerede netværksindikatorer** er **aktiveret i Microsoft 365 Defender** \> **Indstillinger** \> **avancerede funktioner**. Du kan finde flere oplysninger under [Avancerede funktioner](advanced-features.md).
- Du kan finde oplysninger om understøttelse af indikatorer på iOS [under Konfigurer brugerdefinerede indikatorer](/microsoft-365/security/defender-endpoint/ios-configure-features#configure-custom-indicators).

> [!IMPORTANT]
> Kun eksterne IP-adresser kan føjes til indikatorlisten. Der kan ikke oprettes indikatorer for interne IP'er.
> Til webbeskyttelsesscenarier anbefaler vi, at du bruger de indbyggede funktioner i Microsoft Edge. Microsoft Edge bruger [Netværksbeskyttelse til](network-protection.md) at undersøge netværkstrafik og tillader blokke til TCP, HTTP og HTTPS (TLS).
> Hvis der er politikker for indikator for modstridende URL-adresser, anvendes den længere sti. URL-indikatorpolitikken tilsidesætter `https://support.microsoft.com/office` f.eks. URL-indikatorpolitikken `https://support.microsoft.com`.

> [!NOTE]
> For alle andre processer udnytter webbeskyttelsesscenarier netværksbeskyttelse til inspektion og håndhævelse:
>
> - IP understøttes for alle tre protokoller
> - Kun enkelte IP-adresser understøttes (ingen CIDR-blokke eller IP-områder)
> - Krypterede URL-adresser (fuld sti) kan kun blokeres i tredjepartsbrowsere (Internet Explorer, Edge)
> - Krypterede URL-adresser (kun FQDN) kan blokeres uden for tredjepartsbrowsere (Internet Explorer, Edge)
> - Fulde URL-stiblokke kan anvendes på domæneniveau og alle ikke-krypterede URL-adresser
>
> Der kan være op til 2 timers ventetid (som regel mindre) mellem det tidspunkt, hvor handlingen udføres, og URL-adressen og IP-adressen blokeres.

Når du bruger advarselstilstanden, kan du konfigurere følgende kontrolelementer:

**Bypass-funktion**:

- Knappen Tillad i Edge
- Knappen Tillad på toast (ikke-Microsoft-browsere)
- Tilgår varighedsparameteren på indikatoren
- Tilsidesætte håndhævelse på tværs af Microsoft- og ikke-Microsoft-browsere

**Omdiriger URL-adresse**:

- Omdiriger URL-parameter på indikatoren
- Omdiriger URL-adresse i Edge
- Omdiriger URL-adresse på toast (ikke-Microsoft-browsere)

Få mere at vide under [Styre apps, der findes af Microsoft Defender til slutpunkt](/cloud-app-security/mde-govern).

## <a name="create-an-indicator-for-ips-urls-or-domains-from-the-settings-page"></a>Opret en indikator for IP'er, URL-adresser eller domæner på siden med indstillinger

1. I **navigationsruden** skal du **vælge Indstillinger** \> **Slutpunktsindikatorer** \> (under **Regler**).

2. Vælg **fanen IP-adresser eller URL-adresser/** domæner.

3. Vælg **Tilføj element**.

4. Angiv følgende oplysninger:
   - Indikator – Angiv enhedsdetaljerne, og definer udløb af indikatoren.
   - Handling – Angiv den handling, der skal gøres, og angiv en beskrivelse.
   - Omfang – Definer computergruppens omfang.

5. Gennemgå oplysningerne under fanen Oversigt, og klik derefter på **Gem**.

## <a name="related-topics"></a>Relaterede emner

- [Opret indikatorer](manage-indicators.md)
- [Opret indikatorer for filer](indicator-file.md)
- [Opret indikatorer baseret på certifikater](indicator-certificates.md)
- [Administrer indikatorer](indicator-manage.md)
