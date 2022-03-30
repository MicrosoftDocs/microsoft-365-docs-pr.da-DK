---
title: Blokering og inddæmmelse af funktionsmåder
description: Få mere at vide om funktionalitet til blokering af funktionsmåder og inddæmmelse i Microsoft Defender til slutpunkt
keywords: Microsoft Defender til slutpunkt, blokering Slutpunktsregistrering og -svar bloktilstand, blokering af passiv tilstand
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
ms.openlocfilehash: bab766fd69b9227f10ba897040faff79e65b1722
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63599292"
---
# <a name="behavioral-blocking-and-containment"></a>Blokering og inddæmmelse af funktionsmåder

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

## <a name="overview"></a>Oversigt

Nutidens trusselsbillede er løbet over af filløs [malware](/windows/security/threat-protection/intelligence/fileless-threats) , og malware befinder sig uden for landet, stærkt polymorphic-trusler, der muterer hurtigere end traditionelle løsninger kan følge med, og menneskedrevne angreb, der tilpasser sig til, hvad modgangsarer finder på kompromitterede enheder. Traditionelle sikkerhedsløsninger er ikke tilstrækkelige til at stoppe sådanne angreb. du har brug for kunstig intelligens (AI) og enhedslæring (ML) understøttede funktioner, f.eks. blokering af adfærd og inddæmmelse, som er inkluderet [i Defender til slutpunkt](/windows/security).

Funktionsmådeblokering og -spærring kan hjælpe med at identificere og stoppe trusler baseret på deres funktionsmåde og procestræer, selv når truslerne er begyndt at blive udført. Næste generations beskyttelse, Slutpunktsregistrering og -svar og Defender til slutpunktskomponenter og -funktioner arbejder sammen i funktioner til blokering af funktionsmåder og inddæmmelse.

:::image type="content" source="images/mdatp-next-gen-EDR-behavblockcontain.png" alt-text="Blokering og inddæmmelse af funktionsmåder.":::

Funktionsmådeblokering og -blokering fungerer sammen med flere komponenter og funktioner i Defender til Slutpunkt for at stoppe angreb med det samme og forhindre, at angrebene skrider frem.

- [Næste generations beskyttelse](microsoft-defender-antivirus-in-windows-10.md) (som omfatter Microsoft Defender Antivirus) kan registrere trusler ved at analysere funktionsmåder og stoppe trusler, der er begyndt at køre.

- [Slutpunktsregistrering og -svar](overview-endpoint-detection-response.md) (Slutpunktsregistrering og -svar) modtager sikkerhedslys på tværs af dit netværk, dine enheder og kernefunktionsmåden. I forbindelse med at der registreres trusler, oprettes der beskeder. Flere beskeder af samme type samles i hændelser, hvilket gør det nemmere for dit sikkerhedsteam at undersøge og reagere.

- [Defender til slutpunkt](overview-endpoint-detection-response.md) har en bred vifte af optik på tværs af identiteter, mail, data og apps, ud over de netværks-, slutpunkts- og kernefunktionsmådelys, der modtages via Slutpunktsregistrering og -svar. En komponent [af Microsoft 365 Defender](../defender/microsoft-365-defender.md), Defender til slutpunkt behandler og korrelerer disse signaler, hæver registreringsbeskeder og forbinder relaterede beskeder i hændelser.

Med disse funktioner kan flere trusler forhindres eller blokeres, selvom de begynder at køre. Når der registreres mistænkelig adfærd, er truslerne indeholdt, beskeder oprettes, og trusler stoppes i deres spor.

Følgende billede viser et eksempel på en besked, der blev udløst af funktioner til blokering af funktionsmåder og inddæmmelse:

:::image type="content" alt-text="Eksempel på en advarsel via blokering og inddæmmelse af funktionsmåder." source="images/blocked-behav-alert.png" lightbox="images/blocked-behav-alert.png":::

## <a name="components-of-behavioral-blocking-and-containment"></a>Komponenter til blokering og inddæmmelse af funktionsmåder

- **Regler for reduktion af angrebsoverfladen [på klientsiden](attack-surface-reduction.md)** Foruddefinerede almindelige angrebsadfærd forhindres i at blive udført i henhold til dine regler for reduktion af angrebsoverfladen. Når sådanne funktionsmåder forsøger at udføre, kan de ses <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">i Microsoft 365 Defender</a> som informationsbeskeder. Regler for reduktion af angrebsoverfladen er ikke aktiveret som standard. skal du konfigurere dine politikker [i Microsoft 365 Defender portal](/microsoft-365/security/defender/microsoft-365-defender).

- **[Blokering af klientfunktionsmåde](client-behavioral-blocking.md)** Trusler på slutpunkter registreres via maskinel indlæring og blokeres og afhjælpes derefter automatisk. Blokering af klientfunktionsmåden er aktiveret som standard.

- **[Blokering af feedbackløkker](feedback-loop-blocking.md)** (også kaldet hurtig beskyttelse) Trusselsregistreringer observeres via behavioral intelligens. Trusler stoppes og forhindres i at køre på andre slutpunkter. Blokering af feedbackløkker er aktiveret som standard.

- **[Slutpunktsregistrering og -svar (Slutpunktsregistrering og -svar)](edr-in-block-mode.md)** i bloktilstand Skadelige artefakter eller funktionsmåder, der observeres via beskyttelse efter brud, blokeres og indeholdes. Slutpunktsregistrering og -svar bloktilstand fungerer, selvom Microsoft Defender Antivirus ikke er den primære antivirusløsning. (Slutpunktsregistrering og -svar bloktilstand er ikke aktiveret som standard. Du slår det til Microsoft 365 Defender.)

Forvent mere inden for blokering og inddæmmelse af funktionsmåder, da Microsoft fortsat forbedrer funktionerne og egenskaberne for trusselsbeskyttelse. Hvis du vil se, hvad der er planlagt og rullet ud nu, skal [du Microsoft 365 oversigten](https://www.microsoft.com/microsoft-365/roadmap).

## <a name="examples-of-behavioral-blocking-and-containment-in-action"></a>Eksempler på funktionsmådeblokering og -inddæmmelse i aktion

Funktionsmåder for blokering og inddæmmelse har blokeret hackerteknikker som f.eks. følgende:

- Legitimationsoplysninger fra LSASS
- Indsnit på tværs af processer
- Proces, der tommes
- Tilsidesætte af kontrol af brugerkonti
- Ændring af antivirus (f.eks. deaktivering af det eller tilføjelse af malware som udelukkelse)
- Kontakter Kommando og styring (C&C) for at downloade nyttedata
- Kronemining
- Ændring af startpost
- Pass-the-hash-angreb
- Installation af rodcertifikat
- Udnyttelsesforsøg til forskellige sårbarheder

Nedenfor finder du to eksempler på funktionsmådeblokering og -inddæmmelse i aktion.

### <a name="example-1-credential-theft-attack-against-100-organizations"></a>Eksempel 1: Tyveri af legitimationsoplysninger-angreb mod 100 organisationer

Som beskrevet i I et hurtigt forsøg på [elusive trusler: AI-baseret adfærdsbaseret](https://www.microsoft.com/security/blog/2019/10/08/in-hot-pursuit-of-elusive-threats-ai-driven-behavior-based-blocking-stops-attacks-in-their-tracks) blokering stopper angreb i deres spor, et tyveri af legitimationsoplysninger mod 100 organisationer over hele verden blev stoppet af funktionsmåderne for blokering og inddæmmelse. Mails med phishing, der indeholdt et uønsket dokument, blev sendt til den målrettede organisation. Hvis en modtager åbnede den vedhæftede fil, kunne et relateret fjerndokument udføre kode på brugerens enhed og indlæse Lokibot-malware, som stjålet legitimationsoplysninger, eksfiltrerede stjålet data og ventede på yderligere instruktioner fra en kommando- og kontrolserver.

Adfærdsbaserede modeller for enhedslæring i Defender til Endpoint blev afbrudt og stoppet hackerens teknikker på to punkter i angrebskæden:

- Det første beskyttelseslag registrerede udnyttelsesfunktionsmåden. Klassificeringer af enhedslæring i skyen identificerede trussel korrekt som og instruerede straks klientenheden i at blokere angrebene.
- Det andet beskyttelseslag, som hjalp med at stoppe tilfælde, hvor angrebet kom forbi det første lag, registrerede proces udbedring, stoppede denne proces og fjernede de tilsvarende filer (f.eks. Lokibot).

Mens angrebene blev registreret og stoppet, blev beskeder, f.eks. en "startadgangsbesked", udløst og vist [i Microsoft 365 Defender portal](/microsoft-365/security/defender/microsoft-365-defender).

:::image type="content" source="images/behavblockcontain-initialaccessalert.png" alt-text="Besked om startadgang i Microsoft 365 Defender portalen.":::

Dette eksempel viser, hvordan behavior-baserede enhedslæringsmodeller i skyen tilføjer nye lag af beskyttelse mod angreb, selv efter de er begyndt at køre.

### <a name="example-2-ntlm-relay---juicy-potato-malware-variant"></a>Eksempel 2: NTLM relay - Juicy Potato malware variant

Som beskrevet i det seneste blogindlæg registrerede Behavioral blokering og - [blokererment: Transformering af optics](https://www.microsoft.com/security/blog/2020/03/09/behavioral-blocking-and-containment-transforming-optics-into-protection) til beskyttelse, i januar 2020 registrerede Defender for Endpoint en aktivitet for rettighedseskalering på en enhed i en organisation. Der blev udløst en besked med navnet "Mulig eskalering af rettigheder ved hjælp af NTLM relay".

:::image type="content" alt-text="NTLM-besked om malware med juicy-kartomel." source="images/NTLMalertjuicypotato.png" lightbox="images/NTLMalertjuicypotato.png":::

Truslerne viste sig at være malware. det var en ny, ikke set før-variant af et kendt hackingværktøj ved navn Juicy Potato, som bruges af hackere til at få rettighedseskalering på en enhed.

Minutter efter beskeden blev udløst, blev filen analyseret og bekræftet som skadelig. Processen blev stoppet og blokeret, som vist på følgende billede:

:::image type="content" alt-text="Artefakt blokeret." source="images/Artifactblockedjuicypotato.png" lightbox="images/Artifactblockedjuicypotato.png":::

Et par minutter efter at artefaktet blev blokeret, blev flere forekomster af den samme fil blokeret på den samme enhed, hvilket forhindrede flere hackere eller anden malware i at blive udrullet på enheden.

Dette eksempel viser, at med funktionalitet til blokering og inddæmmelse af funktionsmåder bliver trusler registreret, indeholdt og blokeret automatisk.

## <a name="next-steps"></a>Næste trin

- [Få mere at vide om Defender til Slutpunkt](overview-endpoint-detection-response.md)

- [Konfigurer dine regler for reduktion af angrebsoverfladen](attack-surface-reduction.md)

- [Aktivér Slutpunktsregistrering og -svar i bloktilstand](edr-in-block-mode.md)

- [Se den seneste globale trusselsaktivitet](https://www.microsoft.com/wdsi/threats)

- [Få et overblik over Microsoft 365 Defender](../defender/microsoft-365-defender.md)
