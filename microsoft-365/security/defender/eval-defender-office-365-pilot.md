---
title: Pilot Microsoft Defender for Office 365, brug evalueringen i dit produktionsmiljø
description: Trin til at teste din evaluering med grupper af aktive og eksisterende brugere for på korrekt vis at teste funktionerne i Microsoft Defender for Office 365.
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
- zerotrust-solution
ms.custom: admindeeplinkEXCHANGE
ms.topic: how-to
ms.technology: m365d
ms.openlocfilehash: fb246805ebf38cddfda6fe308d19e1dd1419531b
ms.sourcegitcommit: 61b22df76e0f81e5ef11c587b129287886151c79
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/12/2022
ms.locfileid: "66748797"
---
# <a name="pilot-microsoft-defender-for-office-365"></a>Pilot Microsoft Defender for Office 365

**Gælder for:**
- Microsoft 365 Defender

Denne artikel er [trin 3 af 3](eval-defender-office-365-overview.md) i processen med at konfigurere evalueringsmiljøet for Microsoft Defender for Office 365. Du kan få flere oplysninger om denne proces i [oversigtsartiklen](eval-defender-office-365-overview.md).

Brug følgende trin til at konfigurere pilotprojektet til Microsoft Defender for Office 365.

:::image type="content" source="../../media/defender/m365-defender-office-pilot.png" alt-text="Trinnene til oprettelse af pilotprojektet på Microsoft Defender for Office 365-portalen" lightbox="../../media/defender/m365-defender-office-pilot.png":::

- [Trin 1: Opret pilotgrupper](#step-1-create-pilot-groups)
- [Trin 2: Konfigurer beskyttelse](#step-2-configure-protection)
- [Trin 3: Prøv funktioner – Bliv fortrolig med simulering, overvågning og målepunkter](#step-3-try-out-capabilities-and-get-familiar-with-simulation-monitoring-and-metrics)

Når du evaluerer Microsoft Defender for Office 365, kan du vælge at styre bestemte brugere, før du aktiverer og gennemtvinger politikker for hele organisationen. Oprettelse af distributionsgrupper kan hjælpe med at administrere udrulningsprocesserne. Du kan f.eks. oprette grupper som *f.eks. Defender for Office 365 brugere – Standardbeskyttelse*, *Defender for Office 365 brugere – Strict Protection*, *Defender for Office 365 Users – Custom Protection* eller *Defender for Office 365  Brugere – undtagelser*.

Det er muligvis ikke tydeligt, hvorfor "Standard" og "Strict" er de begreber, der bruges til disse grupper, men det bliver tydeligt, når du udforsker mere om Defender for Office 365 sikkerhedsindstillinger. Navngivningsgrupperne "brugerdefinerede" og "undtagelser" taler for sig selv, og selvom de fleste af dine brugere bør falde ind under *standardgrupper* og *strenge*, vil brugerdefinerede grupper og undtagelsesgrupper indsamle værdifulde data for dig vedrørende administration af risici.

## <a name="step-1-create-pilot-groups"></a>Trin 1: Opret pilotgrupper

Distributionsgrupper kan oprettes og defineres direkte i Exchange Online eller synkroniseres fra Active Directory i det lokale miljø.

1. Log på Exchange Administration Center (EAC) ved hjælp af en konto, der har fået tildelt rollen Modtageradministrator eller er blevet uddelegeret tilladelser til gruppeadministration.
2. Udvid *Modtagere* i navigationsmenuen, og vælg *Grupper*.

   :::image type="content" source="../../media/mdo-eval/1_mdo-eval-pilot.png" alt-text=" Det menupunkt i menuen Grupper, der skal klikkes på" lightbox="../../media/mdo-eval/1_mdo-eval-pilot.png":::

3. Vælg "Tilføj en gruppe" på dashboardet Grupper.

   :::image type="content" source="../../media/mdo-eval/2_mdo-eval-pilot-add-group.png" alt-text="Indstillingen Tilføj en gruppe, der skal klikkes på" lightbox="../../media/mdo-eval/2_mdo-eval-pilot-add-group.png":::

4. Vælg *Distribution* som gruppetype, og klik på Næste.

   :::image type="content" source="../../media/mdo-eval/3-mdo-eval-pilot-group-type.png" alt-text=" Afsnittet Vælg en gruppetype" lightbox="../../media/mdo-eval/3-mdo-eval-pilot-group-type.png":::

5. Giv gruppen et navn og en beskrivelse, og klik derefter på Næste.

   :::image type="content" source="../../media/mdo-eval/4_mdo-eval-pilot-set-up-basics.png" alt-text="Afsnittet Konfigurer de grundlæggende funktioner" lightbox="../../media/mdo-eval/4_mdo-eval-pilot-set-up-basics.png":::

## <a name="step-2-configure-protection"></a>Trin 2: Konfigurer beskyttelse

Nogle funktioner i Defender for Office 365 er konfigureret og aktiveret som standard, men sikkerhedshandlinger kan øge beskyttelsesniveauet fra standarden.

Nogle funktioner er *endnu ikke* konfigureret. Du har tre muligheder for at konfigurere beskyttelse:

- **Tildel forudindstillede sikkerhedspolitikker automatisk** – [Forudindstillede sikkerhedspolitikker](../office-365-security/preset-security-policies.md) leveres som en metode til hurtigt at tildele et ensartet beskyttelsesniveau på tværs af alle funktionerne. Du kan vælge mellem **_standard_*_ eller _*_strict_**. En god tilgang er at starte med forudindstillede sikkerhedspolitikker og derefter finjustere politikkerne, efterhånden som du får mere at vide om funktionerne og dit eget unikke trusselsmiljø. Fordelen her er, at du beskytter grupper af brugere så hurtigt som muligt med muligheden for at tilpasse beskyttelsen bagefter. (Denne metode anbefales).
- **Konfigurer grundlæggende beskyttelse manuelt** – Hvis du selv foretrækker at konfigurere miljøet, kan du hurtigt opnå en *grundlæggende beskyttelse ved* at følge vejledningen i [Beskyt mod trusler](../office-365-security/protect-against-threats.md). Med denne fremgangsmåde får du mere at vide om de indstillinger, der kan konfigureres. Og du kan finjustere politikkerne senere.
- **Konfigurer *brugerdefinerede* beskyttelsespolitikker** – Du kan også oprette og tildele brugerdefinerede beskyttelsespolitikker som en del af din evaluering. Før du begynder at tilpasse politikker, er det vigtigt at forstå den prioritet, som disse beskyttelsespolitikker anvendes og gennemtvinges i. Sikkerhedsindstillinger skal oprette nogle politikker, selvom den forudindstillede er anvendt, for at definere sikkerhedspolitikker for Sikre links og Sikre vedhæftede filer.
> [!IMPORTANT]
> **Hvis du har brug for at konfigurere brugerdefinerede beskyttelsespolitikker**, skal du undersøge de værdier, der udgør **Standard**- og Strict-sikkerhedsdefinitionerne, her: *[Anbefalede indstillinger for EOP og Microsoft Defender for Office 365 sikkerhed](../office-365-security/recommended-settings-for-eop-and-office365.md)*. Standardværdier vises også, som før der udføres nogen konfiguration. Bevar et regneark, hvor dit brugerdefinerede build afviger.

### <a name="assign-preset-security-policies"></a>Tildel forudindstillede sikkerhedspolitikker

Det anbefales, at du starter med de *anbefalede grundlæggende politikker* , når du evaluerer MDO og derefter tilpasser dem efter behov i løbet af din evalueringsperiode.

Du kan aktivere anbefalede EOP- og Defender for Office 365 beskyttelsespolitikker hurtigt og tildele dem til specifikke pilotbrugere eller definerede grupper som en del af din evaluering. Forudindstillede politikker tilbyder  en grundlæggende standardbeskyttelsesskabelon eller en mere aggressiv **Strict-beskyttelsesskabelon**, som kan tildeles uafhængigt af hinanden eller kombineres.

Her er artiklen [Forudindstillede sikkerhedspolitikker i EOP og Microsoft Defender for Office 365](../office-365-security/preset-security-policies.md), der beskriver trinnene.

1. Log på din Microsoft 365-lejer. Brug en konto med adgang til Microsoft 365 Defender portalen, der er føjet til rollen Organisationsadministration i Office 365 eller rollen Sikkerhedsadministrator i Microsoft 365.
2. I navigationsmenuen skal du vælge *Polices & Rules* under Email & Collaboration.

   :::image type="content" source="../../media/mdo-eval/5_mdo-eval-pilot-policies.png" alt-text=" Menupunktet Politikker & regler, der skal klikkes på" lightbox="../../media/mdo-eval/5_mdo-eval-pilot-policies.png":::

3. Klik på *Trusselspolitikker* på dashboardet Politik & regler.

   :::image type="content" source="../../media/mdo-eval/6-mdo-eval-pilot-threat-policies.png" alt-text=" Menupunktet Trusselspolitikker, der skal klikkes på" lightbox="../../media/mdo-eval/6-mdo-eval-pilot-threat-policies.png":::

4. På Microsoft 365 Defender-portalen skal du udvide Threat Management i navigationsmenuen og derefter vælge Politik i undermenuen.
5. Klik på *Forudindstillede sikkerhedspolitikker* på dashboardet Politik.

   :::image type="content" source="../../media/mdo-eval/7-mdo-eval-pilot-template-policies.png" alt-text="Typerne af trusselspolitikker" lightbox="../../media/mdo-eval/7-mdo-eval-pilot-template-policies.png":::

6. Klik på *Rediger* for at konfigurere og tildele standardpolitikken og/eller Strict-politikken.

   :::image type="content" source="../../media/mdo-eval/8-mdo-eval-pilot-preset.png" alt-text="De forskellige indstillinger, der anvendes på forskellige politikker på siden Forudindstillede sikkerhedspolitikker" lightbox="../../media/mdo-eval/8-mdo-eval-pilot-preset.png":::

7. Tilføj betingelser for at anvende grundlæggende ***EOP** _-beskyttelse for bestemte pilotbrugere eller grupper af brugere efter behov, og vælg _Next* for at fortsætte.

   Der kan f.eks. anvendes en Defender for Office 365 betingelse for pilotevalueringer, hvis modtagerne er *medlemmer* af en defineret *Defender for Office 365 Standard Protection-gruppe* og derefter administreres ved at føje konti til eller fjerne kontoen fra gruppen.

   :::image type="content" source="../../media/mdo-eval/9-mdo-eval-pilot-eop-protections.png" alt-text="De politikker, der betragtes som EOP-beskyttelse" lightbox="../../media/mdo-eval/9-mdo-eval-pilot-eop-protections.png":::

8. Tilføj betingelser for at anvende grundlæggende ***MDO_-** beskyttelse for bestemte pilotbrugere eller grupper af brugere efter behov. Klik på _Next* for at fortsætte.

   Der kan f.eks. anvendes en Defender for Office 365 betingelse for pilotevalueringer, hvis modtagerne er *medlemmer* af en defineret *Defender for Office 365 standardbeskyttelsesgruppe* og derefter administreres ved at tilføje/fjerne konti via gruppen.

   :::image type="content" source="../../media/mdo-eval/10-mdo-eval-pilot-mdo-protections.png" alt-text="De politikker, der betragtes som defensive med hensyn til beskyttelse af Office 365" lightbox="../../media/mdo-eval/10-mdo-eval-pilot-mdo-protections.png":::

9. Gennemse og bekræft dine ændringer i forbindelse med tildeling af forudindstillede sikkerhedspolitikker.
10. Forudindstillede beskyttelsespolitikker kan administreres (omkonfigureres, anvendes igen, deaktiveres osv.) ved at vende tilbage til Microsoft 365 Defender portalen > politikker & regler > Threat Policies > og klikke på feltet *Forudindstillede sikkerhedspolitikker*.

### <a name="configure-custom-protection-policies"></a>Konfigurer brugerdefinerede beskyttelsespolitikker

De *foruddefinerede standard*- eller  Strict-politikskabeloner Defender for Office 365 giver dine pilotbrugere den anbefalede grundlæggende beskyttelse. Du kan dog også oprette og tildele brugerdefinerede beskyttelsespolitikker som en del af din evaluering.

Det er *vigtigt* at være opmærksom på, hvilken prioritet disse beskyttelsespolitikker har, når de anvendes og håndhæves, som det [forklares i order and precedence of email protection (Rækkefølge og prioritet for mailbeskyttelse). Office 365](../office-365-security/how-policies-and-protections-are-combined.md).

Nedenstående tabel indeholder referencer og mere vejledning til konfiguration og tildeling af brugerdefinerede beskyttelsespolitikker:

<br>

****

|Politik|Beskrivelse|Reference|
|:---:|---|---|
|Forbindelsesfiltrering|Identificer gode eller forkerte kildemailservere ved hjælp af deres IP-adresser.|[Konfigurer standardfilterpolitikken for forbindelse i EOP](../office-365-security/configure-the-connection-filter-policy.md)|
|Antimalware|Beskyt brugerne mod malware via mail, herunder hvilke handlinger der skal udføres, og hvem der skal underrettes, hvis der registreres malware.|[Konfigurer politikker for antimalware i EOP](../office-365-security/configure-anti-malware-policies.md)|
|Anti-spoofing|Beskyt brugerne mod spoofing-forsøg ved hjælp af spoof intelligence- og spoof intelligence-indsigter.|[Konfigurer spoof intelligence i Defender for Office 365](../office-365-security/learn-about-spoof-intelligence.md)|
|Anti-Spam|Beskyt brugerne mod mailspam, herunder hvilke handlinger der skal udføres, hvis der registreres spam.|[Konfigurer politikker mod spam i Defender for Office 365](../office-365-security/configure-your-spam-filter-policies.md)|
|Anti-phishing|Beskyt brugerne mod phishing-angreb, og konfigurer sikkerhedstip til mistænkelige meddelelser|[Konfigurer politikker for antiphishing i Defender for Office 365](../office-365-security/configure-mdo-anti-phishing-policies.md)|
|Sikre vedhæftede filer|Beskyt brugerne mod skadeligt indhold i vedhæftede filer i mails og filer i SharePoint, OneDrive og Teams.|[Konfigurer politikker for sikre vedhæftede filer i Defender for Office 365](../office-365-security/set-up-safe-attachments-policies.md)|
|Sikre links|Beskyt brugerne mod at åbne og dele skadelige links i mails eller Office Desktop-apps.|[Konfigurer politikker for sikre links i Defender for Office 365](../office-365-security/set-up-safe-links-policies.md)|
|

## <a name="step-3-try-out-capabilities-and-get-familiar-with-simulation-monitoring-and-metrics"></a>Trin 3: Prøv funktionerne, og bliv fortrolig med simulering, overvågning og målepunkter

Nu, hvor din pilot er konfigureret og konfigureret, er det nyttigt at blive fortrolig med rapporterings-, overvågnings- og angrebssimuleringsværktøjer, der er unikke for Microsoft Defender til Microsoft 365.

<br>

****

|Kapacitet|Beskrivelse|Flere oplysninger|
|---|---|---|
|Trusselsoversigt|Threat Explorer er et effektivt værktøj i næsten realtid, der hjælper sikkerhedsteams med at undersøge og reagere på trusler og viser oplysninger om mistanke om malware og phish i mails og filer i Office 365 samt andre sikkerhedstrusler og risici for din organisation.|[Visninger i Trusselsoversigt og registreringer i realtid](../office-365-security/threat-explorer-views.md)|
|Angrebssimulator|Du kan bruge oplæring i angrebssimulering på Microsoft 365 Defender portalen til at køre realistiske angrebsscenarier i din organisation, som hjælper dig med at identificere og finde sårbare brugere, før et reelt angreb påvirker dit miljø.|[Kom i gang med at bruge kursus i angrebssimulering](../office-365-security/attack-simulation-training-get-started.md)|
|Dashboard for rapporter|Klik på Rapporter i navigationsruden til venstre, og udvid overskriften Mail & samarbejde. Mail & samarbejdsrapporter handler om at spotte sikkerhedstendenser, hvoraf nogle giver dig mulighed for at handle (via knapper som f.eks. 'Gå til indsendelser'), og andre, der viser tendenser, f.eks. Statusoversigt over mailflow, Top malware, Spoof-registreringer, Kompromitterede brugere, Mailventetid, Sikre links og Rapporter over sikre vedhæftede filer. Disse målepunkter genereres automatisk.|[Vis rapporter](../office-365-security/view-email-security-reports.md)|
|

## <a name="next-steps"></a>Næste trin

[Evaluer Microsoft Defender for Endpoint](eval-defender-endpoint-overview.md)

Vend tilbage til oversigten for [Evaluate Microsoft Defender for Office 365](eval-defender-office-365-overview.md)

Vend tilbage til oversigten for [Evaluate og pilot Microsoft 365 Defender](eval-overview.md)
