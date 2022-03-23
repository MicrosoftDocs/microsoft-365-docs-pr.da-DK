---
title: Brug evalueringen i dit produktionsmiljø Office 365 at prøve Microsoft Defender til Office 365 forbindelse
description: Trin til at afprøve din evaluering med grupper af aktive og eksisterende brugere for at teste funktionerne i Microsoft Defender for Office 365.
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
ms.date: 05/25/2021
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
- m365solution-evalutatemtp
ms.topic: how-to
ms.technology: m365d
ms.openlocfilehash: 456f5dae90f2a559e82599271f23bd5f3452ac12
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/24/2022
ms.locfileid: "63593345"
---
# <a name="pilot-microsoft-defender-for-office-365"></a>Prøve microsoft Defender til Office 365

**Gælder for:**
- Microsoft 365 Defender

Denne artikel er [trin 3 af 3](eval-defender-office-365-overview.md) i oprettelsen af evalueringsmiljøet for Microsoft Defender Office 365. Du kan finde flere oplysninger om denne proces i [oversigtsartikel](eval-defender-office-365-overview.md).

Brug følgende trin til at konfigurere pilotprojektet for Microsoft Defender til Office 365.

![Trin til oprettelse af pilotprojektet for Microsoft Defender til Office 365.](../../media/defender/m365-defender-office-pilot.png)

- [Trin 1: Opret pilotgrupper](#step-1-create-pilot-groups)
- [Trin 2: Konfigurer beskyttelse](#step-2-configure-protection)
- [Trin 3: Prøv funktioner – Bliv fortrolig med simulering, overvågning og målepunkter](#step-3-try-out-capabilities--get-familiar-with-simulation-monitoring-and-metrics)

Når du evaluerer Microsoft Defender Office 365, kan du vælge at prøve pilotspecifikke brugere, før du aktiverer og gennemtvinger politikker for hele organisationen. Oprettelse af distributionsgrupper kan hjælpe med at administrere installationsprocesserne. Du kan f.eks. oprette grupper som *Defender til Office 365-brugere – Standard Protection*, *Defender til Office 365-brugere – Streng beskyttelse*, *Defender til Office 365-brugere –* brugerdefineret beskyttelse eller *Defender for Office 365-brugere – undtagelser*.

Det fremgår muligvis ikke tydeligt, hvorfor "Standard" og "Streng" er de udtryk, der bruges til dette, men det bliver klart, når du udforsker mere om Defender Office 365 sikkerhedsindstillinger. Navngivningsgrupper "brugerdefinerede" og "undtagelser" taler for sig selv, og selvom de fleste af dine brugere skal falde ind under *standard* og *strenge, vil* brugerdefinerede grupper og undtagelsesgrupper indsamle værdifulde data om risikostyring.

## <a name="step-1-create-pilot-groups"></a>Trin 1: Opret pilotgrupper

Distributionsgrupper kan oprettes og defineres direkte Exchange Online eller synkroniseres fra active directory i det lokale miljø.

1. Log på Exchange Administration (EAC) med en konto, der har fået tildelt Modtageradministrator-rolle eller fået delegeret gruppeadministrationstilladelser.
2. I navigationsmenuen skal du **udvide Modtagere** og vælge <a href="https://go.microsoft.com/fwlink/?linkid=2183233" target="_blank">**Grupper**</a>.

   :::image type="content" source="../../media/mdo-eval/1_mdo-eval-pilot.png" alt-text="Exchange Administration i navigationsmenuen (hurtig start) med en pil, der peger på Grupper. Klik på Grupper.":::

3. Vælg "Tilføj en gruppe" i dashboardet Grupper.

   :::image type="content" source="../../media/mdo-eval/2_mdo-eval-pilot-add-group.png" alt-text="Tilføj grupper i panelet Grupper.":::

4. For gruppetype skal du vælge *Distribution* og klikke på Næste.

   :::image type="content" source="../../media/mdo-eval/3-mdo-eval-pilot-group-type.png" alt-text="Vælg en distributionsgruppetype her.":::

5. Giv gruppen et navn og en beskrivelse, og klik derefter på Næste.

   :::image type="content" source="../../media/mdo-eval/4_mdo-eval-pilot-set-up-basics.png" alt-text="Navngive og beskrive gruppen.":::

## <a name="step-2-configure-protection"></a>Trin 2: Konfigurer beskyttelse

Nogle funktioner i Defender til Office 365 er konfigureret og slået til som standard, men sikkerhedshandlinger ønsker måske at hæve beskyttelsesniveauet fra standardindstillingen.

Nogle funktioner er *endnu ikke* konfigureret. Du har tre muligheder for at konfigurere beskyttelse:

- **Tildel forudindstillede sikkerhedspolitikker** automatisk [–](../office-365-security/preset-security-policies.md) Forudindstillede sikkerhedspolitikker leveres som en metode til hurtigt at tildele et ensartet beskyttelsesniveau på tværs af alle funktioner. Du kan vælge mellem **_standard_*_ eller _*_strict_**. En god tilgang er at starte med foruddefinerede sikkerhedspolitikker og derefter finjustere politikkerne, efterhånden som du får mere at vide om funktionerne og dit eget unikke trusselsmiljø. Fordelen her er, at du beskytter grupper af brugere så hurtigt som muligt med mulighed for efterfølgende at justere beskyttelsen. (Denne metode anbefales).
- **Konfigurer beskyttelse af grundlinjer** manuelt – Hvis du foretrækker selv at konfigurere miljøet, kan du hurtigt opnå  en grundlinje for beskyttelse ved at følge vejledningen i Beskyt [mod trusler](../office-365-security/protect-against-threats.md). Med denne fremgangsmåde får du mere at vide om de indstillinger, der kan konfigureres. Og du kan selvfølgelig finjustere politikkerne senere.
- **Konfigurer *brugerdefinerede* beskyttelsespolitikker** – Du kan også oprette og tildele brugerdefinerede beskyttelsespolitikker som en del af din evaluering. Før du går i gang med at tilpasse politikker, er det vigtigt at forstå den rang, hvori disse beskyttelsespolitikker anvendes og håndhæves. Sikkerhedsmæssige ops skal oprette nogle politikker, selvom forudindstillingen anvendes, specifikt for at definere sikkerhedspolitikker for Pengeskab Links og Pengeskab vedhæftede filer.

> [!IMPORTANT]
> **Hvis du har brug** for at konfigurere brugerdefinerede beskyttelsespolitikker, skal du undersøge de værdier, der udgør **Standard**- og **Strict** security-definitionerne her: Anbefalede indstillinger *[for EOP og Microsoft Defender for Office 365 sikkerhed](../office-365-security/recommended-settings-for-eop-and-office365.md)*. Standardværdierne vises også, før konfigurationen finder sted. Behold et regneark, hvor din brugerdefinerede build afviger fra.

### <a name="assign-preset-security-policies"></a>Tildel forudindstillede sikkerhedspolitikker

Det opfordres til at starte med de  anbefalede oprindelige politikker, når MDO evalueres, og derefter justere dem efter behov i løbet af evalueringsperioden.

Du kan hurtigt aktivere anbefalede EOP og Defender Office 365 beskyttelsespolitikker og tildele dem til bestemte pilotbrugere eller definerede grupper som en del af din evaluering. Forudindstillede politikker giver en **standardbeskyttelsesskabelon** eller en mere aggressive **skabelon** til streng beskyttelse, som kan tildeles uafhængigt eller kombineres.

Her er de [forudindstillede sikkerhedspolitikker i EOP og Microsoft Defender Office 365](../office-365-security/preset-security-policies.md) artikel, der beskriver trinnene.

1. Log på din Microsoft 365 lejer. Brug en konto med adgang til Microsoft 365 Defender-portalen, føjet til rollen Organisationsadministration i Office 365 eller Sikkerhedsadministrator i Microsoft 365.
2. I navigationsmenuen skal du *vælge & regler* under & samarbejde.

   :::image type="content" source="../../media/mdo-eval/5_mdo-eval-pilot-policies.png" alt-text="Klik på & regler i navigationspanelet under & Mailsamarbejde.":::

3. Klik på & på *Trusselspolitikker i dashboardet Regler for politik*.

   :::image type="content" source="../../media/mdo-eval/6-mdo-eval-pilot-threat-policies.png" alt-text="a.":::

4. I Microsoft 365 Defender skal du udvide Trusselsadministration i navigationsmenuen og derefter vælge Politik i undermenuen.
5. Klik på Forudindstillede sikkerhedspolitikker *på dashboardet Politik*.

   :::image type="content" source="../../media/mdo-eval/7-mdo-eval-pilot-template-policies.png" alt-text="Klik på feltet Forudindstillede sikkerhedspolitikker.":::

6. Klik *på* Rediger for at konfigurere og tildele standardpolitikken og/eller Streng-politikken.

   :::image type="content" source="../../media/mdo-eval/8-mdo-eval-pilot-preset.png" alt-text="Klik på Rediger i panelet Forudindstillede sikkerhedspolitikker.":::

7. Tilføj betingelser for at anvende grundlinje ***EOP** _-beskyttelse til bestemte pilotbrugere eller grupper af brugere efter behov, og vælg _Next* for at fortsætte.

   Eksempelvis kan en Defender for Office 365-betingelse for pilotevalueringer anvendes, hvis modtagerne er medlemmer af en defineret *Defender til Office 365 Standard Protection-gruppe* og derefter administreres ved blot at føje konti til eller fjerne konto fra gruppen.

   :::image type="content" source="../../media/mdo-eval/9-mdo-eval-pilot-eop-protections.png" alt-text="Tilføj de nødvendige betingelser for at anvende EOP-sikkerhedsniveauet på din pilotgruppe.":::

8. Tilføj betingelser for at anvende **grundlinje *MDO** _-beskyttelse til bestemte pilotbrugere eller grupper af brugere efter behov. Klik _Next* for at fortsætte.

   Eksempelvis kan en Defender for Office 365-betingelse for pilotevalueringer anvendes, hvis modtagerne er medlemmer af en defineret *Defender til Office 365 Standard Protection-gruppe* og derefter administreres ved blot at tilføje/fjerne konti via gruppen.

   :::image type="content" source="../../media/mdo-eval/10-mdo-eval-pilot-mdo-protections.png" alt-text="Tilføj de nødvendige betingelser for at anvende Defender Office 365 sikkerhedsniveau for din pilotgruppe.":::

9. Gennemse og bekræft dine ændringer for at tildele forudindstillede sikkerhedspolitikker.
10. Forudindstillede beskyttelsespolitikker kan administreres (konfigureres igen, anvendes igen, deaktiveres osv.) ved at gå tilbage til Microsoft 365 Defender-portalen >-politikker & regler > Trusselspolitikker > og klikke på feltet Forudindstillede sikkerhedspolitikker.

### <a name="configure-custom-protection-policies"></a>Konfigurere brugerdefinerede beskyttelsespolitikker

De foruddefinerede standard *- eller* *Strict* Defender for Office 365-politikskabeloner giver dine pilotbrugere den anbefalede beskyttelse af grundlinjer. Du kan dog også oprette og tildele brugerdefinerede beskyttelsespolitikker som en del af din evaluering.

Det er vigtigt *at* være opmærksom på den rangorden, disse beskyttelsespolitikker har, når de anvendes og håndhæves, som Rækkefølgen og rangordenen af [mailbeskyttelse – det Office 365](../office-365-security/how-policies-and-protections-are-combined.md) forklarer.

Tabellen nedenfor indeholder referencer og yderligere vejledning til konfiguration og tildeling af politikker for brugerdefineret beskyttelse:

<br>

****

|Politik|Beskrivelse|Reference|
|:---:|---|---|
|Forbindelsesfiltrering|Identificer gode eller dårlige kildemailservere ud fra deres IP-adresser.|[Konfigurere standardfilterpolitikken for forbindelse i EOP](../office-365-security/configure-the-connection-filter-policy.md)|
|Antimalware|Beskyt brugere mod mailmalware, herunder hvilke handlinger de skal udføre, og hvem de skal underrette, hvis der registreres malware.|[Konfigurer antimalwarepolitikker i EOP](../office-365-security/configure-anti-malware-policies.md)|
|Antispoofing|Beskyt brugere mod spoofing forsøg ved hjælp af efterlignet intelligens og efterlignet intelligensindsigt.|[Konfigurer efterlignet intelligens i Defender til Office 365](../office-365-security/learn-about-spoof-intelligence.md)|
|Antispam|Beskyt brugere mod mailspam, herunder hvilke handlinger der skal udføres, hvis der registreres spam.|[Konfigurer antispampolitikker i Defender for Office 365](../office-365-security/configure-your-spam-filter-policies.md)|
|Antiphishing|Beskyt brugere mod phishingangreb, og konfigurer sikkerhedstip på mistænkelige meddelelser|[Konfigurer antiphishing-politikker i Defender til Office 365](../office-365-security/configure-mdo-anti-phishing-policies.md)|
|Pengeskab vedhæftede filer|Beskyt brugere mod skadeligt indhold i vedhæftede filer og filer i SharePoint, OneDrive og Teams.|[Konfigurer politikker for sikre vedhæftede filer i Defender til Office 365](../office-365-security/set-up-safe-attachments-policies.md)|
|Sikre links|Beskyt brugere mod at åbne og dele skadelige links i mails eller Office-skrivebordsapps.|[Konfigurer politikker for sikre links i Defender til Office 365](../office-365-security/set-up-safe-links-policies.md)|
|

## <a name="step-3-try-out-capabilities--get-familiar-with-simulation-monitoring-and-metrics"></a>Trin 3: Prøv funktioner – Bliv fortrolig med simulering, overvågning og målepunkter

Nu, hvor din pilot er konfigureret og konfigureret, er det nyttigt at blive fortrolig med værktøjer til rapportering, overvågning og angrebssimulering, der er unikke for Microsoft Defender Microsoft 365.

<br>

****

|Funktion|Beskrivelse|Flere oplysninger|
|---|---|---|
|Threat Explorer|Threat Explorer er et effektivt værktøj i nærheden af realtid, som kan hjælpe sikkerhedsteams med at undersøge og reagere på trusler og vise oplysninger om mistænkelig malware og phish i mails og filer i Office 365 samt andre sikkerhedstrusler og risici for din organisation.|[Visninger i Trusselsstifinder og registreringer i realtid](../office-365-security/threat-explorer-views.md)|
|Angrebstunge|Du kan bruge kursus i angrebssimulering i Microsoft 365 Defender-portalen til at køre realistiske angrebsscenarier i din organisation, som hjælper dig med at identificere og finde følsomme brugere, før et rigtigt angreb påvirker dit miljø.|[Kom i gang med at bruge simuleringskursus til angreb](../office-365-security/attack-simulation-training-get-started.md)|
|Dashboardet Rapporter|I venstre navigationsmenu skal du klikke på Rapporter og udvide overskriften & samarbejde. Rapporterne om mailsamarbejde & handler om at opdage sikkerhedstendenser, hvoraf nogle giver dig mulighed for at handle (via knapper som 'Gå til indsendelser'), og andre, der viser tendenser, f.eks. statusoversigt for mailflow, de vigtigste malware-, efterlignede registreringer, kompromitterede brugere, mailventetid, Pengeskab Links og rapporter over vedhæftede Pengeskab-filer. Disse målepunkter genereres automatisk.|[Vis rapporter](../office-365-security/view-email-security-reports.md)|
|

## <a name="next-steps"></a>Næste trin

[Evaluer Microsoft Defender til slutpunkt](eval-defender-endpoint-overview.md)

Gå tilbage til oversigten for [Evaluer Microsoft Defender for Office 365](eval-defender-office-365-overview.md)

Gå tilbage til oversigten for [Evaluer og Microsoft 365 Defender](eval-overview.md)
