---
title: Blokering og opbevaring af funktionsmåder
description: Få mere at vide om funktionsblokering og funktionalitet til opbevaring på Microsoft Defender for Endpoint
keywords: Microsoft Defender for Endpoint, Slutpunktsregistrering og -svar i bloktilstand, blokering af passiv tilstand
ms.pagetype: security
author: denisebmsft
ms.author: deniseb
manager: dansimp
ms.reviewer: shwetaj
audience: ITPro
ms.topic: article
ms.prod: m365-security
ms.localizationpriority: medium
ms.custom:
- next-gen
- edr
- admindeeplinkDEFENDER
ms.collection: m365-security-compliance
ms.technology: mde
ms.openlocfilehash: f6544a14891a98523d202c19634d0e70a3e839e2
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/14/2022
ms.locfileid: "65416788"
---
# <a name="behavioral-blocking-and-containment"></a>Blokering og opbevaring af funktionsmåder

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- Microsoft Defender Antivirus

**Platforme**
- Windows

> Vil du gerne opleve Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

## <a name="overview"></a>Oversigt

Dagens trusselslandskab er overrendt af [filløs malware](/windows/security/threat-protection/intelligence/fileless-threats) , og som lever af landet, meget polymorfe trusler, der muterer hurtigere end traditionelle løsninger kan holde trit med, og menneskedrevne angreb, der tilpasser sig det, modstandere finder på kompromitterede enheder. Traditionelle sikkerhedsløsninger er ikke tilstrækkelige til at stoppe sådanne angreb; Du skal bruge funktioner, der understøttes af kunstig intelligens (AI) og ml (device learning), f.eks. funktionsblokering og indeslutning, i [Defender for Endpoint](/windows/security).

Funktionalitet til adfærdsblokering og indkapsling kan hjælpe med at identificere og stoppe trusler baseret på deres adfærd og procestræer, selv når truslen er begyndt at blive udført. Næste generations beskyttelse, Slutpunktsregistrering og -svar og Defender for Endpoint-komponenter og -funktioner arbejder sammen i funktionsblokerings- og indeslutningsfunktioner.

:::image type="content" source="images/mdatp-next-gen-EDR-behavblockcontain.png" alt-text="Funktionsmådeblokering og -opbevaring på Microsoft Defender ATP-portalen" lightbox="images/mdatp-next-gen-EDR-behavblockcontain.png":::

Funktionalitet til funktionsblokering og indeslutning fungerer sammen med flere komponenter og funktioner i Defender for Endpoint for at stoppe angreb med det samme og forhindre, at angreb skrider frem.

- [Næste generations beskyttelse](microsoft-defender-antivirus-in-windows-10.md) (som omfatter Microsoft Defender Antivirus) kan registrere trusler ved at analysere adfærd og stoppe trusler, der er begyndt at køre.

- [Slutpunktsregistrering og -svar](overview-endpoint-detection-response.md) (Slutpunktsregistrering og -svar) modtager sikkerhedssignaler på tværs af dit netværk, dine enheder og kernefunktionsmåden. Når der registreres trusler, oprettes der beskeder. Flere beskeder af samme type samles i hændelser, hvilket gør det nemmere for dit team af sikkerhedshandlinger at undersøge og svare.

- [Defender for Endpoint](overview-endpoint-detection-response.md) har en bred vifte af optik på tværs af identiteter, mail, data og apps foruden netværket, slutpunktet og kernefunktionsmådesignaler, der modtages via Slutpunktsregistrering og -svar. En komponent i [Microsoft 365 Defender](../defender/microsoft-365-defender.md), Defender for Endpoint-processer og korrelerer disse signaler, udløser registreringsbeskeder og opretter forbindelse til relaterede beskeder i hændelser.

Med disse funktioner kan flere trusler forhindres eller blokeres, selvom de begynder at køre. Når mistænkelig adfærd registreres, er truslen indeholdt, der oprettes beskeder, og trusler stoppes i deres spor.

På følgende billede vises et eksempel på en besked, der blev udløst af funktionsmådens blokerings- og indeslutningsfunktioner:

:::image type="content" source="images/blocked-behav-alert.png" alt-text="Siden Beskeder med en besked via funktionsblokering og -opbevaring" lightbox="images/blocked-behav-alert.png":::

## <a name="components-of-behavioral-blocking-and-containment"></a>Komponenter til funktionsblokering og indeslutning

- **Regler for [reduktion af angreb på](attack-surface-reduction.md) klienten** Foruddefinerede almindelige angrebsadfærd forhindres i at blive udført i henhold til reglerne for reduktion af angrebsoverfladen. Når sådanne funktionsmåder forsøger at blive udført, kan de ses i <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> som informationsbeskeder. Regler for reduktion af angrebsoverfladen er ikke aktiveret som standard. du konfigurerer dine politikker på [Microsoft 365 Defender-portalen](/microsoft-365/security/defender/microsoft-365-defender).

- **[Blokering af klientens funktionsmåde](client-behavioral-blocking.md)** Trusler på slutpunkter registreres via maskinel indlæring og blokeres og afhjælpes derefter automatisk. (Blokering af klientens funktionsmåde er aktiveret som standard).

- **[Blokering af feedbackløkke](feedback-loop-blocking.md)** (også kaldet hurtig beskyttelse) Trusselsregistreringer observeres via adfærdsintelligens. Trusler stoppes og forhindres i at køre på andre slutpunkter. (Blokering af feedbackløkke er aktiveret som standard).

- **[Registrering af slutpunkter og svar (Slutpunktsregistrering og -svar) i blokeringstilstand](edr-in-block-mode.md)** Ondsindede artefakter eller funktionsmåder, der observeres via beskyttelse efter brud, blokeres og er indeholdt. Slutpunktsregistrering og -svar i bloktilstand fungerer, selvom Microsoft Defender Antivirus ikke er den primære antivirusløsning. (Slutpunktsregistrering og -svar i bloktilstand ikke er aktiveret som standard, aktiveres den ved Microsoft 365 Defender.

Forvent, at der kommer mere inden for adfærdsblokering og -opbevaring, efterhånden som Microsoft fortsætter med at forbedre funktioner og funktioner til trusselsbeskyttelse. Hvis du vil se, hvad der er planlagt og udrullet nu, skal du besøge [køreplanen for Microsoft 365](https://www.microsoft.com/microsoft-365/roadmap).

## <a name="examples-of-behavioral-blocking-and-containment-in-action"></a>Eksempler på funktionsblokering og -indeslutning i aktion

Funktionalitet til funktionsblokering og indeslutning har blokeret hackerteknikker som f.eks.følgende:

- Dumping af legitimationsoplysninger fra LSASS
- Tværgående procesinjektion
- Behandl udhuling
- Tilsidesættelse af brugerkontokontrol
- Manipulation med antivirus (f.eks. deaktivering af det eller tilføjelse af malware som udelukkelse)
- Kontakter kommando og kontrol (C&C) for at downloade nyttedata
- Møntmining
- Ændring af startpost
- Pass-the-hash angreb
- Installation af rodcertifikat
- Udnyttelsesforsøg for forskellige sikkerhedsrisici

Nedenfor er to eksempler på adfærdsblokering og indeslutning i praksis.

### <a name="example-1-credential-theft-attack-against-100-organizations"></a>Eksempel 1: Angreb på 100 organisationer for tyveri af legitimationsoplysninger

Som beskrevet i [Under jagten på flygtige trusler: AI-drevet adfærdsbaseret blokering stopper angreb på deres spor](https://www.microsoft.com/security/blog/2019/10/08/in-hot-pursuit-of-elusive-threats-ai-driven-behavior-based-blocking-stops-attacks-in-their-tracks), blev et legitimationstyveriangreb mod 100 organisationer over hele verden stoppet af adfærdsmæssige blokerings- og indeslutningsfunktioner. Spear-phishing-mails, der indeholdt et lokkedokument, blev sendt til de målrettede organisationer. Hvis en modtager åbnede den vedhæftede fil, kunne et relateret fjerndokument udføre kode på brugerens enhed og indlæse Lokibot-malware, som stjal legitimationsoplysninger, eksfiltrerede stjålne data og ventede på yderligere instruktioner fra en kommando- og kontrolserver.

Adfærdsbaserede modeller til enhedslæring i Defender for Endpoint fanget og stoppet hackerens teknikker på to punkter i angrebskæden:

- Det første beskyttelseslag registrerede funktionsmåden for udnyttelse. Device-learning-klassificeringerne i clouden identificerede korrekt truslen som og bad straks klientenheden om at blokere angrebet.
- Det andet beskyttelseslag, som hjalp med at stoppe tilfælde, hvor angrebet kom forbi det første lag, registrerede procesudhulning, stoppede denne proces og fjernede de tilsvarende filer (såsom Lokibot).

Mens angrebet blev registreret og stoppet, blev beskeder, f.eks. en "indledende adgangsbesked", udløst og vist på [portalen Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender).

:::image type="content" source="images/behavblockcontain-initialaccessalert.png" alt-text="Indledende adgangsbesked på Microsoft 365 Defender-portalen" lightbox="images/behavblockcontain-initialaccessalert.png":::

Dette eksempel viser, hvordan adfærdsbaserede modeller til enhedslæring i cloudmiljøet tilføjer nye lag af beskyttelse mod angreb, selv efter at de er begyndt at køre.

### <a name="example-2-ntlm-relay---juicy-potato-malware-variant"></a>Eksempel 2: NTLM-relæ – Variant af saftig kartoffelmalware

Som beskrevet i det seneste blogindlæg [Adfærdsblokering og -opbevaring: Transformation af optik til beskyttelse](https://www.microsoft.com/security/blog/2020/03/09/behavioral-blocking-and-containment-transforming-optics-into-protection) registrerede Defender for Endpoint i januar 2020 en rettighedseskaleringsaktivitet på en enhed i en organisation. En besked med navnet "Mulig rettighedseskalering ved hjælp af NTLM-relæ" blev udløst.

:::image type="content" source="images/NTLMalertjuicypotato.png" alt-text="En NTLM-besked om saftig kartoffelmalware" lightbox="images/NTLMalertjuicypotato.png":::

Truslen viste sig at være malware; det var en ny ikke-set før-variant af et berygtet hackingværktøj kaldet Juicy Potato, som bruges af angribere til at få rettighedseskalering på en enhed.

Minutter efter beskeden blev udløst, blev filen analyseret og bekræftet til at være skadelig. Processen blev stoppet og blokeret, som vist på følgende billede:

:::image type="content" source="images/Artifactblockedjuicypotato.png" alt-text="Artefakt er blokeret"  lightbox="images/Artifactblockedjuicypotato.png":::

Få minutter efter at artefaktet blev blokeret, blev flere forekomster af den samme fil blokeret på den samme enhed, hvilket forhindrede flere hackere eller anden malware i at installere på enheden.

Dette eksempel viser, at med funktionalitet til funktionsblokering og funktionalitet til opbevaring registreres, indesluttet og blokeres trusler automatisk.

> [!TIP]
> Hvis du leder efter antivirusrelaterede oplysninger til andre platforme, kan du se:
> - [Angiv indstillinger for Microsoft Defender for Endpoint på macOS-](mac-preferences.md)
> - [Microsoft Defender for Endpoint på Mac](microsoft-defender-endpoint-mac.md)
> - [Politikindstillinger for macOS Antivirus for Microsoft Defender Antivirus for Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Angiv indstillinger for Microsoft Defender for Endpoint på Linux](linux-preferences.md)
> - [Microsoft Defender for Endpoint på Linux](microsoft-defender-endpoint-linux.md)
> - [Konfigurer Defender for Endpoint på Android-funktioner](android-configure.md)
> - [Konfigurer Microsoft Defender for Endpoint på iOS-funktioner](ios-configure-features.md)

## <a name="next-steps"></a>Næste trin

- [Få mere at vide om Defender for Endpoint](overview-endpoint-detection-response.md)

- [Konfigurer reglerne for reduktion af angrebsoverfladen](attack-surface-reduction.md)

- [Aktivér Slutpunktsregistrering og -svar i bloktilstand](edr-in-block-mode.md)

- [Se seneste globale trusselsaktivitet](https://www.microsoft.com/wdsi/threats)

- [Få et overblik over Microsoft 365 Defender](../defender/microsoft-365-defender.md)
