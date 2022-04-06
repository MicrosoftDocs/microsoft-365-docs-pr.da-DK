---
title: Foretag fejlfinding af problemer, og find svar på ofte stillede spørgsmål om Microsoft Defender for Endpoint på iOS
description: Fejlfinding og ofte stillede spørgsmål – Microsoft Defender for Endpoint på iOS
keywords: microsoft, defender, Microsoft Defender for Endpoint, ios, fejlfinding, ofte stillede spørgsmål, hvordan du
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
ms.openlocfilehash: bc8cda3fb61ec9338b95eed58f5f0a70e1deb3e1
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64469355"
---
# <a name="troubleshoot-issues-and-find-answers-to-faqs-on-microsoft-defender-for-endpoint-on-ios"></a>Fejlfinding af problemer, og find svar på ofte stillede spørgsmål Microsoft Defender for Endpoint i iOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Dette emne indeholder fejlfindingsoplysninger, der kan hjælpe dig med at løse de problemer, der kan opstå, når du Microsoft Defender for Endpoint på iOS.



> [!NOTE]
> Defender til Slutpunkt på iOS ville bruge et VPN for at levere webbeskyttelsesfunktionen. Dette er ikke et almindeligt VPN og er et lokalt/selvløkkende VPN, der ikke tager trafik uden for enheden.

## <a name="apps-dont-work-when-vpn-is-turned-on"></a>Apps virker ikke, når VPN er slået til
Der er nogle apps, der stopper med at fungere, når et aktivt VPN registreres. Du kan deaktivere VPN i den tid, du bruger disse apps. 

Defender til Slutpunkt på iOS omfatter og aktiverer som standard funktionen til webbeskyttelse. [Webbeskyttelse hjælper](web-protection-overview.md) dig med at beskytte enheder mod webtrusler og beskytte brugere mod phishingangreb. Defender til Slutpunkt på iOS bruger et VPN for at give denne beskyttelse. Bemærk, at dette er et lokalt VPN, og i modsætning til traditionelt VPN sendes netværkstrafik ikke uden for enheden.

Mens den er aktiveret som standard, kan der være nogle tilfælde, hvor du er nødt til at deaktivere VPN. For eksempel vil du køre nogle apps, der ikke fungerer, når et VPN er konfigureret. I sådanne tilfælde kan du vælge at deaktivere VPN direkte fra Defender for Endpoint-appen eller ved at bruge følgende trin:

1. På din iOS-enhed skal du åbne **Indstillinger**, klikke eller trykke **på Generelt** og derefter **VPN**.
1. Klik eller tryk på knappen "i" for at Microsoft Defender for Endpoint.
1. Slå VPN **fra Forbind On Demand for** at deaktivere VPN.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/ios-vpn-config.png" alt-text="Indstillingen Forbind on-demand" lightbox="images/ios-vpn-config.png":::

> [!NOTE]
> Webbeskyttelse er ikke tilgængelig, når VPN er deaktiveret. Hvis du vil genaktivere Webbeskyttelse, skal Microsoft Defender for Endpoint appen på enheden og Aktivere Webbeskyttelse.

## <a name="coexistence-with-multiple-vpn-profiles"></a>Sameksistens med flere VPN-profiler

Apple iOS understøtter ikke flere VPN **for hele enheden** for at være aktive samtidigt. Selvom flere VPN-profiler kan findes på enheden, kan kun ét VPN være aktivt ad gangen. Hvis du skal bruge et andet VPN på enheden, kan du deaktivere Defender for Endpoint VPN, mens du bruger det andet VPN.

## <a name="battery-consumption"></a>Batteriforbrug

For at kunne yde dig hele tiden beskyttelse mod webbaserede trusler skal Microsoft Defender for Endpoint køre i baggrunden hele tiden. Dette kan medføre en mindre stigning i det samlede batteriforbrug på din enhed. Hvis du oplever betydelige batteriafladninger, skal du [sende os feedback](ios-troubleshoot.md#send-in-app-feedback) , så vil vi undersøge det.

Desuden viser iOS Indstillinger-appen kun batteriforbrug af apps, der kan ses af brugeren i en bestemt periode. Batteriforbruget i apps, der vises på skærmen, er kun i denne periode og beregnes af iOS baseret på en lang række faktorer, herunder CPU og netværksforbrug. Microsoft Defender for Endpoint bruger et lokalt/tilbage-VPN i baggrunden til at kontrollere webtrafik for ondsindede websteder eller forbindelser. Netværkspakker fra en hvilken som helst app gennemgår denne kontrol, og det medfører, at batteriforbruget for Microsoft Defender for Endpoint beregnes forkert. Det faktiske batteriforbrug for Microsoft Defender for Endpoint er mindre end det, der vises på siden Indstillinger på enheden.

Bemærk, at det anvendte VPN er et lokalt VPN, og i modsætning til et traditionelt VPN sendes netværkstrafik ikke uden for enheden.

## <a name="data-usage"></a>Dataforbrug

Microsoft Defender for Endpoint bruger et lokalt/loopback-VPN til at kontrollere webtrafik for ondsindede websteder eller forbindelser. På grund af denne grund Microsoft Defender for Endpoint der ikke taget forkert højde for dataforbruget. Vi har også bemærket, at hvis enheden kun er på mobilnetværket, er det dataforbrug, der rapporteres af serviceudbyder, meget tæt på det faktiske forbrug, hvorimod Apple i Indstillinger-appen viser ca. 1,5x til 2x af de faktiske forbrugte data.

Vi har også lignende observationer med andre VPN-tjenester og har rapporteret dette til Apple.

Det er desuden vigtigt, at Microsoft Defender for Endpoint opdateret med vores backendtjenester for at yde bedre beskyttelse.

## <a name="report-unsafe-site"></a>Rapportér usikkert websted

Phishingwebsteder udgives som pålidelige websteder for at få dine personlige eller økonomiske oplysninger. Besøg siden [Giv feedback om netværksbeskyttelse for at](https://www.microsoft.com/wdsi/support/report-unsafe-site) rapportere et websted, der kunne være et phishingwebsted.

## <a name="malicious-site-detected"></a>Ondsindet websted registreret

Microsoft Defender for Endpoint beskytter dig mod phishing eller andre webbaserede angreb. Hvis der registreres et skadeligt websted, blokeres forbindelsen, og der sendes en besked til Microsoft 365 Defender portal. Beskeden indeholder forbindelsens domænenavn, IP-ekstern adresse og oplysninger om enheden.

Desuden vises der en meddelelse på iOS-enheden. Når du trykker på meddelelsen, åbnes følgende skærmbillede, hvor brugeren kan gennemse oplysningerne.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/ios-phish-alert.png" alt-text="Webstedet rapporteres som usikker meddelelse" lightbox="images/ios-phish-alert.png":::

## <a name="device-not-seen-on-the-defender-for-endpoint-console-after-onboarding"></a>Enheden kan ikke ses på Defender for Endpoint-konsollen efter onboarding.

Efter onboarding tager det et par timer, før enheden vises på lageret for enheden i sikkerhedskonsollen Defender til Endpoint. Sørg også for, at enheden er registreret korrekt med Azure Active Directory og enheden har forbindelse til internettet. For at få en vellykket onboarding skal enheden være registreret via Microsoft Authenticator eller Intune-firmaportal, og brugeren skal logge på med den samme konto, som enheden er registreret med Azure AD med.

> [!NOTE]
> Nogle gange stemmer enhedsnavnet ikke overens med det i Microsoft Endpoint Manager (Intune). Enhedsnavnet i Defender til slutpunktskonsollen er af formatet <username_iPhone/iPad model>. Du kan også bruge Azure AD-enheds-id til at identificere enheden i Defender for Endpoint-konsollen.

## <a name="data-and-privacy"></a>Data og beskyttelse af personlige oplysninger

Hvis du vil have mere at vide om data, der indsamles og [beskyttes, skal du se Oplysninger om beskyttelse Microsoft Defender for Endpoint på iOS](ios-privacy.md).

## <a name="connectivity-issue-on-cellular-network"></a>Forbindelsesproblemer på mobilnetværk

Hvis du oplever problemer med forbindelsen til internettet på mobilnetværket, skal du kontrollere, om Microsoft Defender for Endpoint har aktiveret mobildata: Åbn Indstillinger-appen > MS Defender > sørg for, at "Mobildata" er aktiveret for MS Defender.

Hvis du stadig har forbindelsesproblemer, kan du kontrollere, om flytilstanden til/fra hjælper med at løse problemet. Hvis problemet fortsætter, kan [du sende os logfiler](ios-troubleshoot.md#send-in-app-feedback).

## <a name="issues-on-supervised-devices-with-content-filter-profile-installed"></a>Problemer med overvågede enheder med profilen til indholdsfiltre installeret

Der er et problem på enheder, der overvåges med Defender for Endpoint-indholdsfilter installeret. Hvis du bemærker langsomhed eller ventetid i forbindelse med internetforbindelse på sådanne enheder, skal du fjerne eller slette indholdsfilterprofilen fra enheden. Vi arbejder på at løse problemet og opdaterer dette sted, når vi har en løsning. 

## <a name="issues-during-app-updates-from-the-app-store"></a>Problemer under appopdateringer fra appbutikken

Hvis du ser problemer, når appen opdateres via App Store (enten automatiske opdateringer eller manuelle opdateringer), skal du muligvis genstarte enheden. Hvis det ikke løser problemet, kan du deaktivere Defender VPN og udføre appopdateringen. Du kan også give feedback i appen for at rapportere dette problem.

## <a name="send-in-app-feedback"></a>Send feedback i appen

Hvis en bruger oplever et problem, som ikke allerede er adresseret i ovenstående afsnit eller ikke kan løse ved hjælp af de angivne trin, kan brugeren give feedback i appen sammen med diagnostiske data. Vores team vil derefter undersøge logfilerne for at finde den rette løsning. Brugerne kan bruge følgende trin til at sende feedback:

  - Åbn MSDefender-appen på iOS-/iPadOS-enheden.
  - Tryk på Menu (profilikon) i øverste venstre hjørne.
  - Tryk **på Send feedback**.
  - Vælg mellem de angivne indstillinger. Hvis du vil rapportere et problem, skal **du vælge Der er noget, jeg ikke kan lide**.
  - Angiv oplysninger om det problem, du oplever, og markér **Send diagnostiske data**. Vi anbefaler, at du medtager din mailadresse, så teamet kan kontakte dig for en løsning eller en opfølgning.
  - Tryk **på Send** for at sende feedbacken.
