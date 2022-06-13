---
title: Foretag fejlfinding af problemer, og find svar på ofte stillede spørgsmål, der er relateret til Microsoft Defender for Endpoint på iOS
description: Fejlfinding og ofte stillede spørgsmål – Microsoft Defender for Endpoint på iOS
keywords: microsoft, defender, Microsoft Defender for Endpoint, ios, troubleshoot, faq, how to
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: ae6e65d99a82bdf4a9c0adbb740c6e5b969f4b68
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/10/2022
ms.locfileid: "66016322"
---
# <a name="troubleshoot-issues-and-find-answers-to-faqs-on-microsoft-defender-for-endpoint-on-ios"></a>Foretag fejlfinding af problemer, og find svar på ofte stillede spørgsmål om Microsoft Defender for Endpoint på iOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Dette emne indeholder fejlfindingsoplysninger, der kan hjælpe dig med at løse problemer, der kan opstå, når du bruger Microsoft Defender for Endpoint på iOS.

> [!NOTE]
> Defender for Endpoint på iOS ville bruge en VPN-forbindelse til at levere webbeskyttelsesfunktionen. Dette er ikke en almindelig VPN- og er en lokal/selv-løkke-VPN, der ikke tager trafik uden for enheden.

## <a name="apps-dont-work-when-vpn-is-turned-on"></a>Apps fungerer ikke, når VPN er slået til
Der er nogle apps, der holder op med at fungere, når der registreres en aktiv VPN. Du kan deaktivere VPN i den tid, du bruger sådanne apps.

Som standard inkluderer og aktiverer Defender for Endpoint på iOS webbeskyttelsesfunktionen. [Webbeskyttelse](web-protection-overview.md) hjælper med at beskytte enheder mod webtrusler og beskytte brugerne mod phishingangreb. Defender for Endpoint på iOS bruger en VPN for at give denne beskyttelse. Bemærk, at dette er en lokal VPN, og i modsætning til traditionel VPN sendes netværkstrafik ikke uden for enheden.

Selvom indstillingen er aktiveret som standard, kan der være nogle tilfælde, der kræver, at du deaktiverer VPN. Du vil f.eks. køre nogle apps, der ikke fungerer, når en VPN er konfigureret. I sådanne tilfælde kan du vælge at deaktivere VPN direkte fra appen Defender for Endpoint eller ved hjælp af følgende trin:

1. Åbn appen **Indstillinger** på din iOS-enhed, klik eller tryk på **Generelt** og derefter **VPN**.
1. Klik eller tryk på knappen "i" for Microsoft Defender for Endpoint.
1. Slå **Forbind On Demand** fra for at deaktivere VPN.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/ios-vpn-config.png" alt-text="Indstillingen Forbind efter behov" lightbox="images/ios-vpn-config.png":::

> [!NOTE]
> Webbeskyttelse vil ikke være tilgængelig, når VPN er deaktiveret. Hvis du vil aktivere Webbeskyttelse igen, skal du åbne appen Microsoft Defender for Endpoint på enheden og aktivere webbeskyttelse.

## <a name="coexistence-with-multiple-vpn-profiles"></a>Samliv med flere VPN-profiler

Apple iOS understøtter ikke, at flere VPN'er for **hele enheden** er aktive samtidig. Selvom der kan være flere VPN-profiler på enheden, kan kun én VPN-forbindelse være aktiv ad gangen. Hvis du har brug for at bruge en anden VPN på enheden, kan du deaktivere Defender for Endpoint VPN, mens du bruger den anden VPN.

## <a name="battery-consumption"></a>Batteriforbrug

For at give dig beskyttelse hele tiden mod webbaserede trusler skal Microsoft Defender for Endpoint til enhver tid køre i baggrunden. Dette kan medføre en mindre stigning i enhedens samlede batteriforbrug. Hvis du oplever betydelig batteriafløb, kan du [sende os feedback](ios-troubleshoot.md#send-in-app-feedback) , så undersøger vi det.

I appen Indstillinger viser iOS også kun batteribrug af apps, der er synlige for brugeren i en bestemt tidsperiode. Batteriforbruget for apps, der vises på skærmen, er kun i den pågældende tidsperiode og beregnes af iOS baseret på en lang række faktorer, herunder CPU- og netværksforbrug. Microsoft Defender for Endpoint bruger en LOKAL/løkke-VPN i baggrunden til at kontrollere webtrafik for eventuelle skadelige websteder eller forbindelser. Netværkspakker fra en hvilken som helst app gennemgår denne kontrol, og det medfører, at batteriforbruget af Microsoft Defender for Endpoint beregnes forkert. Det faktiske batteriforbrug af Microsoft Defender for Endpoint er mindre end det, der vises på siden Batteri Indstillinger på enheden.

Bemærk, at den anvendte VPN er en lokal VPN, og i modsætning til en traditionel VPN sendes netværkstrafik ikke uden for enheden.

## <a name="data-usage"></a>Dataforbrug

Microsoft Defender for Endpoint bruger en vpn til lokal/tilbagekobling til at kontrollere webtrafik for eventuelle skadelige websteder eller forbindelser. Derfor kan der tages fejl af Microsoft Defender for Endpoint dataforbrug. Vi har også observeret, at hvis enheden kun er på mobilnetværket, er det dataforbrug, der rapporteres af tjenesteudbyderen, meget tæt på det faktiske forbrug, hvorimod tallene i Indstillinger-appen kan være unøjagtige.

Vi har lignende observationer med andre VPN-tjenester.

Derudover er det afgørende for, at Microsoft Defender for Endpoint er opdateret med vores backend-tjenester for at sikre bedre beskyttelse.

## <a name="report-unsafe-site"></a>Rapportér usikkert websted

Phishingwebsteder repræsenterer pålidelige websteder for at få dine personlige eller økonomiske oplysninger. Gå til siden [Giv feedback om netværksbeskyttelse](https://www.microsoft.com/wdsi/support/report-unsafe-site) for at rapportere et websted, der kan være et phishingwebsted.

## <a name="malicious-site-detected"></a>Skadeligt websted, der er registreret

Microsoft Defender for Endpoint beskytter dig mod phishing eller andre webbaserede angreb. Hvis der registreres et skadeligt websted, blokeres forbindelsen, og der sendes en besked til organisationens Microsoft 365 Defender portal. Beskeden indeholder domænenavnet på forbindelsen, fjern-IP-adressen og enhedsoplysningerne.

Desuden vises der en meddelelse på iOS-enheden. Når du trykker på meddelelsen, åbnes følgende skærmbillede, hvor brugeren kan gennemse detaljerne.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/ios-phish-alert.png" alt-text="Webstedet blev rapporteret som usikker meddelelse" lightbox="images/ios-phish-alert.png":::

## <a name="device-not-seen-on-the-defender-for-endpoint-console-after-onboarding"></a>Enheden kan ikke ses på Defender for Endpoint-konsollen efter onboarding

Efter onboarding tager det nogle timer, før enheden vises i enhedsoversigten i sikkerhedskonsollen Defender for Endpoint. Sørg også for, at enheden er registreret korrekt med Azure Active Directory, og at enheden har forbindelse til internettet. Hvis onboarding skal lykkes, skal enheden registreres via Microsoft Authenticator eller Intune-firmaportal, og brugeren skal logge på med den samme konto, som enheden er registreret med Azure AD.

> [!NOTE]
> Nogle gange er enhedsnavnet ikke i overensstemmelse med navnet i Microsoft Endpoint Manager (Intune)-konsollen. Enhedsnavnet i Defender for Endpoint-konsollen er i formatet <username_iPhone/iPad model>. Du kan også bruge Azure AD enheds-id til at identificere enheden i Defender for Endpoint-konsollen.

## <a name="data-and-privacy"></a>Data og beskyttelse af personlige oplysninger

Du kan finde oplysninger om indsamlede data og beskyttelse af personlige oplysninger under [Oplysninger om beskyttelse af personlige oplysninger – Microsoft Defender for Endpoint på iOS](ios-privacy.md).

## <a name="connectivity-issue-on-cellular-network"></a>Forbindelsesproblem på mobilnetværk

Hvis du oplever problemer med internetforbindelsen på mobilnetværket, skal du kontrollere, om Microsoft Defender for Endpoint har aktiveret mobildata: Åbn Indstillinger app > MS Defender > sikre, at "Mobildata" er aktiveret for MS Defender.

Hvis du stadig har forbindelsesproblemer, skal du kontrollere, om aktivering/deaktivering af flytilstand hjælper med at løse problemet. Hvis problemet fortsætter, [skal du sende os logge](ios-troubleshoot.md#send-in-app-feedback).

## <a name="issues-on-supervised-devices-with-content-filter-profile-installed"></a>Problemer på overvågede enheder med indholdsfilterprofil installeret

Der er et problem på overvågede enheder, hvor Defender for Endpoint-indholdsfilter er installeret. Hvis du bemærker langsomhed eller ventetid i forbindelse med internetforbindelsen på sådanne enheder, skal du fjerne eller slette indholdsfilterprofilen fra enheden. Vi arbejder på at løse dette problem og opdaterer dette sted, når vi har en løsning. 

## <a name="issues-during-app-updates-from-the-app-store"></a>Problemer under appopdateringer fra appbutikken

Hvis du ser problemer, når appen opdateres via appbutikken (enten automatiske opdateringer eller manuelle opdateringer), skal du muligvis genstarte enheden. Hvis det ikke løser problemet, kan du deaktivere Defender VPN og udføre appopdateringen. Du kan også angive en feedback i appen for at rapportere dette problem.

## <a name="send-in-app-feedback"></a>Send feedback i appen

Hvis en bruger står over for et problem, der ikke allerede er behandlet i ovenstående afsnit, eller som ikke kan løse ved hjælp af de angivne trin, kan brugeren give feedback i appen sammen med diagnosticeringsdata. Vores team undersøger derefter loggene for at levere den rigtige løsning. Brugerne kan bruge følgende trin til at sende feedback:

- Åbn APPEN MSDefender på iOS-/iPadOS-enheden.
- Tryk på Menu (profilikon) i øverste venstre hjørne.
- Tryk på **Send feedback**.
- Vælg mellem de angivne indstillinger. Hvis du vil rapportere et problem, skal du vælge **Jeg kan ikke lide noget**.
- Angiv oplysninger om det problem, du står overfor, og markér **Send diagnosticeringsdata**. Vi anbefaler, at du inkluderer din mailadresse, så teamet kan kontakte dig for at få en løsning eller en opfølgning.
- Tryk på **Send** for at sende feedbacken.
