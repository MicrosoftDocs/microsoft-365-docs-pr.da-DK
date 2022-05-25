---
title: Brug ARC-afsendere, der er tillid til, til legitime enheder og tjenester mellem afsender og modtager
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
audience: ITPro
ms.topic: article
ms.localizationpriority: high
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.custom:
- seo-marvel-apr2020
description: Godkendt modtaget kæde (ARC) er mailgodkendelse, der forsøger at bevare godkendelsesresultater på tværs af enheder og eventuelle indirekte mailflows, der kommer mellem afsenderen og modtageren. Her kan du se, hvordan du kan gøre undtagelser for dine ARC-afsendere, der er tillid til.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 625dd27ff59fca6a0e156bd65296e407e22005a6
ms.sourcegitcommit: 612ce4d15d8a2fdbf7795393b50af477d81b6139
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/24/2022
ms.locfileid: "65663889"
---
# <a name="make-a-list-of-trusted-arc-senders-to-trust-legitimate-indirect-mailflows"></a>Opret en liste over ARC-afsendere, der er tillid til, for at have tillid til *legitime* indirekte mailflow

**Gælder for**

- Exchange Online Protection
- Microsoft Defender for Office 365 plan 1 og plan 2
- Microsoft 365 Defender

E-mail godkendelse mekanismer som [SPF](set-up-spf-in-office-365-to-help-prevent-spoofing.md), [DKIM](use-dkim-to-validate-outbound-email.md), [DMARC](use-dmarc-to-validate-email.md) bruges til at bekræfte afsendere af e-mails for *sikkerheden* af e-mail modtagere, men nogle legitime tjenester kan foretage ændringer i e-mailen mellem afsender og modtager. **I Microsoft 365 Defender hjælper ARC med at reducere leveringsfejl i SPF, DKIM og DMARC på grund af *legitime* indirekte mailflows.**

## <a name="authenticated-received-chain-arc-for-legitimate-indirect-mailflows-in-microsoft-365-defender-for-office"></a>Godkendt modtaget kæde (ARC) til *legitime* indirekte mailflow i Microsoft 365 Defender til Office

Adresselister og tjenester, der filtrerer eller videresender mails, er en velkendt og normal funktion i en organisations mailflow. Men mail videresending overtræder SPF. Tjenester kan også overtræde DKIM-e-mail-godkendelse ved at ændre mailheadere, tilføje f.eks. oplysninger om virusscanning eller fjerne vedhæftede filer. En af disse godkendelsesmetoder til mail kan medføre, at DMARC ikke kan overføres.

Planlagte mailflowindgreb fra legitime tjenester kaldes ofte *indirekte mailflow* og kan *ved et uheld* få meddelelser til at mislykke e-mail-godkendelse, når de passerer gennem (hop til) den næste enhed eller tjeneste på vej til modtageren.

**Arc-sealere, der er tillid til, gør det muligt for administratorer at føje en liste over *pålidelige* formidlere til portalen Microsoft 365 Defender.** Arc-sealere, der er tillid til, gør det muligt for Microsoft at overholde ARC-signaturer fra pålidelige mellemled, hvilket forhindrer, at disse legitime meddelelser mislykkes i godkendelseskæden.

> [!NOTE]
> ***ARC-sealers, der er tillid til, er en administratoroprettet liste over alle domæner, hvis processer resulterer i indirekte mailflow, og som har implementeret ARC-forsegling.*** Når en mail dirigeres til Office 365 igennem, og ARC rustent mellemled i Office 365 lejer, validerer Microsoft ARC-signaturen og kan på baggrund af ARC-resultaterne overholde de angivne godkendelsesoplysninger.

## <a name="when-to-use-trusted-arc-sealers"></a>Hvornår skal du bruge arc-sealere, der er tillid til?

Der kræves kun en liste over ARC-sealere, der er tillid til, hvor enheder og servere intervenerer i en organisations mailflow og:

1. Kan ændre mailheaderen eller andet mailindhold.
2. Godkendelse kan mislykkes af andre årsager (f.eks. ved at fjerne vedhæftede filer).
 
Ved at tilføje en ARC-sealer, der er tillid til, validerer og har Office 365 tillid til de godkendelsesresultater, som sealer leverer til din lejer i Office 365.

**Administratorer bør *kun tilføje legitime tjenester* som ARC-sealere, der er tillid til.** Hvis du kun tilføjer tjenester, som organisationen udtrykkeligt bruger og kender, kan det hjælpe meddelelser, der først skal gennemgå en tjeneste for at kunne bestå kontrol af mailgodkendelse, og forhindre, at legitime meddelelser sendes til *uønsket mail* på grund af godkendelsesfejl.

## <a name="steps-to-add-a-trusted-arc-sealer-to-microsoft-365-defender"></a>Trin til at føje en ARC-sealer, der er tillid til, til Microsoft 365 Defender

Arc-beseglingsprogrammer, der er tillid til, på Microsoft 365 Defender portalen viser alle ARC-sealere, der er bekræftet af og føjet til din lejer.

**Sådan tilføjer du en ny ARC-sealer, der er tillid til, på administrationsportalen:**

1. Gå til siden med [indstillinger for godkendelse via mail](https://security.microsoft.com/authentication?viewid=ARC) .

2. Hvis det er første gang, du har tilføjet en ARC-sealer, der er tillid til, skal du klikke på knappen Tilføj.
3. Tilføj ARC-sealere, der er tillid til, i det viste tekstfelt.
    1. Bemærk, at du tilføjer domænerne (f.eks. fabrikam.com).
    1. Det domænenavn, du angiver her, *skal* svare til det domæne, der vises i mærket 'd' i ARC-Seal og ARC-Message-Signature-headere (i mailheaderne for meddelelsen).
    1. Du kan se disse i egenskaberne for meddelelsen i Outlook.

## <a name="steps-to-validate-your-trusted-arc-sealer"></a>Trin til at validere din ARC-sealer, du har tillid til

Hvis der er et ARC-forsegling fra en tredjepart, før meddelelsen når Microsoft 365 Defender, **skal du kontrollere overskrifterne, når mailen er modtaget, og se de seneste ARC-headere**.

I den sidste ***ARC-Authentication-Results header** _skal du kontrollere, om ARC-validering er angivet som _*pass**.

En ARC-header, der viser en 'oda' på 1, angiver, at den tidligere ARC er blevet *bekræftet*, at der er *tillid til* den tidligere ARC-forsegling, og at det tidligere *adgangsresultat* kan bruges til at tilsidesætte den aktuelle DMARC-fejl.

**En ARC-gennemløbsheader, der viser oda=1**

Se godkendelsesmetoderne for mail i slutningen af denne headerblok for at se oda-resultatet.

``
ARC-Authentication-Results: i=2; mx.microsoft.com 1; spf=pass (sender ip is
40.107.65.78) smtp.rcpttodomain=microsoft.com
smtp.mailfrom=o365e5test083.onmicrosoft.com; dmarc=bestguesspass action=none
header.from=o365e5test083.onmicrosoft.com; dkim=none (message not signed);
arc=pass (0 oda=1 ltdi=1
spf=[1,1,smtp.mailfrom=o365e5test083.onmicrosoft.com]
dkim=[1,1,header.d=o365e5test083.onmicrosoft.com]
dmarc=[1,1,header.from=o365e5test083.onmicrosoft.com])
``

Hvis du vil kontrollere, om ARC-resultatet blev brugt til at tilsidesætte en DMARC-fejl, skal du søge efter *compauth-resultat* og en *årsag til kode(130)* i headeren.

Se den sidste post i denne overskriftsblok for at finde *oplysninger* og *årsag*.

``
Authentication-Results: spf=fail (sender IP is 51.163.158.241)
smtp.mailfrom=contoso.com; dkim=fail (body hash did not verify)
header.d=contoso.com;dmarc=fail action=none
header.from=contoso.com;compauth=pass reason=130
``

## <a name="powershell-steps-to-add-or-remove-a-trusted-arc-sealer"></a>PowerShell-trin til at tilføje eller fjerne en ARC-sealer, der er tillid til

**Administratorer kan også konfigurere ARC-konfigurationer med Exchange Online Powershell.**

1. Forbind til at Exchange online powershell.
2. Forbind-ExchangeOnline.
3. Sådan tilføjer eller opdaterer du et domæne i en ARC-sealer, der er tillid til:
</br>
``
Set-ArcConfig -Identity default -ArcTrustedSealers {a list of arc signing domains split by comma}
``
</br>Eller</br>
``
Set-ArcConfig -Identity {tenant name/tenanid}\default -ArcTrustedSealers {a list of arc signing domains split by comma}
``
</br>Du skal angive identitetsparameteren *-Identity default* , når du kører *Set-ArcConfig*. De betroede sealers skal matches med værdien af mærket 'd' i *ARC-Seal-headeren*.

4. Vis de ARC-sealere, der er tillid til:
</br>
``
Get-ArcConfig
`` Eller ``
Get-ArcConfig - Organization {tenant name}
``

## <a name="trusted-arc-sealer-mailflow-graphics"></a>Arc-sealer-mailflowgrafik, der er tillid til

Disse diagrammer kontrasterer mailflowhandlinger med og uden en ARC-sealer, der er tillid til, når du bruger spf-, DKIM- og DMARC-mailgodkendelse. I begge grafikker er der legitime tjenester, der bruges af virksomheden, der skal intervenere i mailflow, som nogle gange overtræder standarder for e-mailgodkendelse ved at ændre afsendelse af IP-adresser og skrive til mailheaderen. **I det første tilfælde viser den indirekte mailflowtrafik resultatet, *før* administratorer tilføjer en ARC-sealer, der er tillid til.**

:::image type="content" source="../../media/m365d-indirect-traffic-flow-without-trusted-arc-sealer.PNG" alt-text="I denne grafik publicerer Contoso SPF, DKIM og DMARC som en del af standardmailsikkerhed. En afsender, der bruger SPF, sender mail fra contoso.com til fabrikam.com, og denne mail går gennem en tredjepartstjeneste, som Contoso har hyret, og tjenesten ændrer den afsendende IP-adresse i mailheaderen. Mailen mislykkes SPF pga. den ændrede IP-adresse og DKIM, fordi indholdet blev ændret hos en tredjepart under DNS-kontrollen på EOP. DMARC mislykkes på grund af FEJL i SPF og DKIM. Meddelelsen sendes til Uønsket, Karantæne eller Afvist.":::

Her kan du se den samme organisation **, når du har udnyttet muligheden for at oprette en ARC-sealer, der er tillid til.**

:::image type="content" source="../../media/m365d-indirect-traffic-flow-with-trusted-arc-sealer.PNG" alt-text="I den anden grafik havde Contoso-virksomheden oprettet en liste over arc-sealere, der var tillid til. Den samme bruger sender endnu en mail fra contoso.com til fabrikam.com. Den tjeneste fra tredjepart, der hyres af Contoso, ændrer afsenderens IP-adresse i mailens overskrift. Men denne gang har tjenesten implementeret ARC-forsegling, og fordi lejeradministratoren allerede har føjet domænet for tredjeparten til arc-sealere, der er tillid til, accepteres ændringen. SPF mislykkes for den nye IP-adresse. DKIM mislykkes på grund af indholdsændringen. DMARC mislykkes på grund af tidligere fejl. men ARC genkender ændringerne, udsteder et gennemløb og accepterer ændringer. Spoof modtager også et adgangskort. Meddelelsen sendes til Indbakke.":::

## <a name="next-steps-after-you-set-up-arc-for-microsoft-365-defender-for-office"></a>Næste trin: Når du har konfigureret ARC til Microsoft 365 Defender for Office

Når du har konfigureret, skal du kontrollere [ARC-headere med Analyse af brevhoved](/connectivity-analyzer/message-header-analyzer).

Gennemse [SPF](set-up-spf-in-office-365-to-help-prevent-spoofing.md), [DKIM](use-dkim-to-validate-outbound-email.md), [DMARC](use-dmarc-to-validate-email.md), konfigurationstrin.
