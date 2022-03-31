---
title: Installér ransomware-beskyttelse for din Microsoft 365 lejer
author: dansimp
f1.keywords:
- NOCSH
ms.author: dansimp
manager: dansimp
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
- ransomware
- m365solution-ransomware
- m365solution-overview
ms.custom: seo-marvel-jun2020
keywords: ransomware, ransomware drevet af mennesker, ransomware drevet af mennesker, HumOR, extortionsangreb, ransomware-angreb, kryptering, cryptovirologi, nultillids
description: Gennemgå beskyttelsen af dine Microsoft 365 mod ransomware-angreb.
ms.openlocfilehash: c356a0e3fac83c77a7e1eb1eda6e169405f43863
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63600979"
---
# <a name="deploy-ransomware-protection-for-your-microsoft-365-tenant"></a>Installér ransomware-beskyttelse for din Microsoft 365 lejer

Ransomware er en type extortion-angreb, der ødelægger eller krypterer filer og mapper, hvilket forhindrer adgang til vigtige data. Malware spredes typisk som en virus, der inficerer enheder og kun kræver afhjælpning af malware. Menneskelig ransomware er resultatet af et aktivt angreb fra cyberkriminelle, der infiltrerer en organisations lokale eller skybaserede it-infrastruktur, hæver deres rettigheder og implementere ransomware til vigtige data.

Når angrebene er udført, kræver en hacker penge fra sig selv i bytte for de slettede filer, dekrypteringsnøgler til krypterede filer eller løftet om ikke at frigive følsomme data til det mørke internet eller det offentlige internet. Human-drevet ransomware kan også bruges til at lukke kritiske maskiner eller processer, f.eks dem, der er nødvendige for den industribaserede produktion, sætte normale forretningshandlinger til standsning, indtil der betales, og skaden er rettet, eller organisationen afhjælper selve skaden.

En menneskeligt drevet ransomware-angreb kan være en slags problemer for virksomheder i alle størrelser og er svær at rydde op, hvilket kræver fuldstændig adversær eviction for at beskytte mod fremtidige angreb. I modsætning til almindelig ransomware kan human-drevet ransomware fortsat true virksomheder med at udføre handlinger efter den indledende anmodning om ransomware.

>[!Note]
>En ransomware-angreb på en Microsoft 365-lejer forudsætter, at hackeren har gyldige legitimationsoplysninger til en brugerkonto til en lejer og har adgang til alle de filer og ressourcer, der er tilladte for brugerkontoen. En hacker uden gyldige legitimationsoplysninger til brugerkontoen skal dekryptere de data, der er blevet krypteret med standardkryptering og Microsoft 365 kryptering. Få mere at vide under Oversigt [over kryptering og nøgleadministration](/compliance/assurance/assurance-encryption). 
>

Du kan finde flere oplysninger om beskyttelse mod ransomware på tværs af Microsoft-produkter i [disse yderligere ransomware-ressourcer](#additional-ransomware-resources).

## <a name="security-in-the-cloud-is-a-partnership"></a>Sikkerhed i skyen er et partnerskab

Sikkerheden for dine Microsoft-skytjenester er et partnerskab mellem dig og Microsoft:

- Microsofts skytjenester er bygget på et grundlag af tillid og sikkerhed. Microsoft giver dig sikkerhedskontrolelementer og funktioner, der kan hjælpe dig med at beskytte dine data og programmer.
- Du ejer dine data og identiteter og har ansvaret for at beskytte dem, sikkerheden for dine lokale ressourcer og sikkerheden for de skykomponenter, du styrer.

Ved at kombinere disse egenskaber og ansvarsområder kan vi yde den bedste beskyttelse mod ransomware-angreb.

## <a name="ransomware-mitigation-and-recovery-capabilities-provided-with-microsoft-365"></a>Afhjælpning af ransomware og genoprettelse, som leveres med Microsoft 365

En ransomware hacker, der har infiltreret en Microsoft 365 lejer, kan holde din organisation privat ved at:

- Sletning af filer eller mail
- Kryptering af filer på plads
- Kopiere filer uden for din lejer (dataudfyldning)

Onlinetjenester Microsoft 365 mange indbyggede funktioner og kontrolelementer for at beskytte kundedata mod ransomware-angreb. De følgende afsnit indeholder en oversigt. Du kan finde flere oplysninger om, hvordan Microsoft beskytter kundedata, [malware og ransomware beskyttelse Microsoft 365](/compliance/assurance/assurance-malware-and-ransomware-protection).

>[!Note]
>En ransomware-angreb på en Microsoft 365-lejer forudsætter, at hackeren har gyldige legitimationsoplysninger til en brugerkonto til en lejer og har adgang til alle de filer og ressourcer, der er tilladte for brugerkontoen. En hacker uden gyldige legitimationsoplysninger til brugerkontoen skal dekryptere de data, der er blevet krypteret med standardkryptering og Microsoft 365 kryptering. Få mere at vide under Oversigt [over kryptering og nøgleadministration](/compliance/assurance/assurance-encryption). 
>

### <a name="deleting-files-or-email"></a>Sletning af filer eller mail

Filer i SharePoint og OneDrive for Business er beskyttet af:

- Versionsversioner 

   Microsoft 365 beholder mindst 500 versioner af en fil som standard og kan konfigureres til at bevare flere. 

   For at minimere belastningen af dine sikkerheds- og helpdeskmedarbejdere skal du oplære dine brugere i, hvordan [de gendanner tidligere versioner af filer](https://support.microsoft.com/office/restore-a-previous-version-of-an-item-or-file-in-sharepoint-f66dbda0-81f4-4d1e-b08c-793265c58934).

- Papirkurv

   Hvis ransomware opretter en ny krypteret kopi af filen og sletter den gamle fil, har kunder 93 dage til at gendanne den fra papirkurven. Efter 93 dage er der et 14-dages vindue, hvor Microsoft stadig kan gendanne dataene. 
  
   For at minimere belastningen af dine sikkerheds- og helpdeskmedarbejdere skal du oplære dine brugere i [, hvordan de gendanner filer fra papirkurven](https://support.microsoft.com/office/restore-deleted-items-from-the-site-collection-recycle-bin-5fa924ee-16d7-487b-9a0a-021b9062d14b).

- [Filgendannelse](https://support.microsoft.com/office/restore-your-onedrive-fa231298-759d-41cf-bcd0-25ac53eb8a15)

   En komplet løsning til selvbetjeningsgendannelse til SharePoint og OneDrive, der giver administratorer og slutbrugere mulighed for at gendanne filer fra et hvilket som helst tidspunkt inden for de seneste 30 dage.

   For at minimere belastningen af dine sikkerhedsmedarbejdere og it-helpdeskmedarbejdere skal du oplære dine brugere i [Filgendannelse](https://support.microsoft.com/office/restore-your-onedrive-fa231298-759d-41cf-bcd0-25ac53eb8a15).


I OneDrive og SharePoint filer kan Microsoft vende tilbage til et tidligere tidspunkt i op til 14 dage, hvis du bliver ramt af et masseangreb.

Mail er beskyttet af:

- [Gendannelse af enkelt element](/exchange/recipients-in-exchange-online/manage-user-mailboxes/enable-or-disable-single-item-recovery) og opbevaring af postkasse, hvor du kan gendanne elementer i en postkasse ved utilsigtet eller ondsindet sletning. Du kan som standard tilbagestryge mails, der er blevet slettet inden for 14 dage, og som kan konfigureres op til 30 dage.

- [Opbevaringspolitikker](/exchange/security-and-compliance/messaging-records-management/retention-tags-and-policies) giver dig mulighed for at bevare uforanderlige kopier af mails i den konfigurerede opbevaringsperiode.

### <a name="encrypting-files-in-place"></a>Kryptering af filer på plads

Som tidligere beskrevet er filer i SharePoint og OneDrive for Business beskyttet mod skadelig kryptering med:

- Versionsversioner
- Papirkurv
- Preservation Hold-bibliotek

Du kan finde flere oplysninger [under Håndtering af data beskadigelse i Microsoft 365](/compliance/assurance/assurance-dealing-with-data-corruption).

### <a name="copying-files-outside-your-tenant"></a>Kopiere filer uden for din lejer 

Du kan forhindre en hacker i at kopiere filer uden for din lejer med:

- [Politikker til forebyggelse af datatab (DLP)](/microsoft-365/compliance/dlp-learn-about-dlp)

    Registrer, advar og bloker risikabelt, utilsigtet eller upassende deling af data, der indeholder:

    - Personlige oplysninger som personlige identifikationsoplysninger (PII) for overholdelse af regionale bestemmelser om beskyttelse af personlige oplysninger.

    - Fortrolige organisationsoplysninger baseret på følsomhedsmærkater.

- [Microsoft Defender til skyapps](/cloud-app-security/what-is-cloud-app-security)

    Bloker overførsler af følsomme oplysninger, f.eks filer. 

    Du kan også bruge sessionspolitikker for [Defender for Cloud Apps Conditional Access App Control](/cloud-app-security/tutorial-dlp#how-to-discover-and-protect-sensitive-information-in-your-organization) til at overvåge strømmen af oplysninger mellem en bruger og et program i realtid.

## <a name="whats-in-this-solution"></a>Hvad er der i denne løsning

Denne løsning hjælper dig gennem udrulningen af funktioner til beskyttelse og afhjælpning af Microsoft 365, konfigurationer og igangværende handlinger for at minimere en ransomware hackers mulighed for at bruge vigtige data i din Microsoft 365-lejer og holde din organisation til hjælp.

![Trinnene til beskyttelse mod ransomware med Microsoft 365](../media/ransomware-protection-microsoft-365/ransomware-protection-microsoft-365-step-grid.png)

Trinnene i denne løsning er:

1. [Konfigurere grundlinjer for sikkerhed](ransomware-protection-microsoft-365-security-baselines.md)
2. [Udrul registrering af angreb og svar](ransomware-protection-microsoft-365-attack-detection-response.md)
3. [Beskyt identiteter](ransomware-protection-microsoft-365-identities.md)
4. [Beskyt enheder](ransomware-protection-microsoft-365-devices.md)
5. [Beskyt oplysninger](ransomware-protection-microsoft-365-information.md)

Her er de fem trin i den løsning, der er installeret for Microsoft 365 lejer.

![Beskyttelse mod ransomware for en Microsoft 365 lejer](../media/ransomware-protection-microsoft-365/ransomware-protection-microsoft-365-architecture.png)

Denne løsning anvender principperne for [Nul tillid](/security/zero-trust/): 

- **Bekræft udtrykkeligt:** Godkend og godkend altid baseret på alle tilgængelige datapunkter.
- **Brug adgang med mindst rettigheder:** Begræns brugeradgang med Just-In-Time og Just-Enough-Access (JIT/JEA), risikobaserede adaptive politikker og databeskyttelse.
- **Antag misligholdelse:** Minimer mængden af radius og segmentadgang. Bekræft kryptering fra ende til anden, og brug analyse til at få synlighed, køre trusselsregistrering og forbedre forsvar.

I modsætning til traditionel intranetadgang, som har tillid til alt bag en organisations firewall, behandler Zero Trust hvert logon og adgang, som om det stammer fra et netværk, der er til at få adgang til, uanset om det er bag organisationens firewall eller på internettet. Nultillid kræver beskyttelse af netværket, infrastrukturen, identiteter, slutpunkter, apps og data.

## <a name="microsoft-365-capabilities-and-features"></a>Microsoft 365 funktioner

For at beskytte din Microsoft 365 lejer mod ransomware-angreb skal du bruge disse Microsoft 365 funktioner til disse trin i løsningen.

### <a name="1-security-baseline"></a>1. Grundlinje over sikkerhed

| Funktionalitet eller funktion | Beskrivelse | Hjælper... | Licensering |
|:-------|:-----|:-------|:-------|
| Microsoft Secure Score |  Måler en Microsoft 365 lejers sikkerhed. | Vurder din sikkerhedskonfiguration, og foreslår forbedringer. | Microsoft 365 E3 eller Microsoft 365 E5 |
| Regler for reduktion af angrebsoverflade | Reducerer din organisations sikkerhedsrisiko for cyberangreb ved hjælp af en række konfigurationsindstillinger. | Bloker mistænkelig aktivitet og sårbar indhold. | Microsoft 365 E3 eller Microsoft 365 E5 |
| Exchange mailindstillinger |  Gør det muligt for tjenester, der reducerer din organisations sikkerhedsrisiko ved mailbaserede angreb. | Undgå indledende adgang til din lejer via phishing og andre mailbaserede angreb.  | Microsoft 365 E3 eller Microsoft 365 E5 |
| Microsoft Windows, Microsoft Edge og Microsoft 365 Apps til virksomhedsindstillinger | Indeholder branchestandardsikkerhedskonfigurationer, der er bredt kendt og gennemtestede. | Forebyd angreb Windows, Edge og Microsoft 365 Apps for Enterprise. | Microsoft 365 E3 eller Microsoft 365 E5 |
|

### <a name="2-detection-and-response"></a>2. Registrering og svar

| Funktionalitet eller funktion | Beskrivelse | Hjælper med at registrere og reagere på... | Licensering |
|:-------|:-----|:-------|:-------|
| Microsoft 365 Defender | Kombinerer signaler og signalmuligheder til en enkelt løsning. <br><br> Gør det muligt for sikkerhedsmedarbejdere at samle trusselssignaler og fastslå det fulde omfang og den fulde virkning af en trussel. <br><br> Automatiserer handlinger til at forhindre eller stoppe angreb og selv samme postkasser, slutpunkter og brugeridentiteter. | Hændelser, som er de kombinerede beskeder og data, der udgør et angreb. | Microsoft 365 E5 eller Microsoft 365 E3 med Microsoft 365 E5 Sikkerhed tilføjelsesprogrammet |
| Microsoft Defender for Identity |  Identificerer, registrerer og undersøger avancerede trusler, kompromitterede identiteter og skadelige Insider-handlinger, der er rettet mod din organisation via en skybaseret sikkerhedsgrænseflade, bruger dine lokale Active Directory-domæneservices (AD DS)-signaler. | Legitimationsoplysninger er blevet kompromitteret AD DS konti. | Microsoft 365 E5 eller Microsoft 365 E3 med Microsoft 365 E5 Sikkerhed tilføjelsesprogrammet |
| Microsoft Defender til Office 365 | Beskytter din organisation mod skadelige trusler fra mails, links (URL-adresser) og samarbejdsværktøjer. <br><br> Beskytter mod malware, phishing, spoofing og andre typer angreb. | Phishing-angreb. | Microsoft 365 E5 eller Microsoft 365 E3 med Microsoft 365 E5 Sikkerhed tilføjelsesprogrammet |
| Microsoft Defender til Slutpunkt | Aktiverer registrering og svar på avancerede trusler på tværs af slutpunkter (enheder). | Malwareinstallation og kompromis af enhed. | Microsoft 365 E5 eller Microsoft 365 E3 med Microsoft 365 E5 Sikkerhed tilføjelsesprogrammet |
| Azure Active Directory (Azure AD) Identity Protection | Dette automatiserer registrering og afhjælpning af identitetsbaserede risici og undersøgelse af disse risici. | Legitimationsforligning for Azure AD-konti og rettighedseskalering. | Microsoft 365 E5 eller Microsoft 365 E3 med Microsoft 365 E5 Sikkerhed tilføjelsesprogrammet |
| Defender til skyapps | En sikkerhedsmægler til skyadgang til opdagelse, undersøgelse og styring på tværs af alle dine Microsoft- og tredjepartsskytjenester. | Lateral bevægelse og dataudfyldning. | Microsoft 365 E5 eller Microsoft 365 E3 med Microsoft 365 E5 Sikkerhed tilføjelsesprogrammet |
|

### <a name="3-identities"></a>3. Identities

| Funktionalitet eller funktion | Beskrivelse | Hjælper med at forhindre... | Licensering |
|:-------|:-----|:-------|:-------|
|Azure AD Password Protection | Bloker adgangskoder fra en fælles liste og brugerdefinerede poster. | Bestemmelse af adgangskoder til skyen eller i det lokale miljø. |Microsoft 365 E3 eller Microsoft 365 E5|
|MFA gennemtvunget med Betinget adgang | Kræv MFA baseret på egenskaberne for brugerkonti med politikker for betinget adgang. | Legitimationsoplysninger er blevet kompromitteret og adgang. | Microsoft 365 E3 eller Microsoft 365 E5|
|MFA gennemtvunget med risikobaseret betinget adgang | Kræv MFA baseret på risikoen for bruger logins med Azure AD Identity Protection. |Legitimationsoplysninger er blevet kompromitteret og adgang. | Microsoft 365 E5 eller Microsoft 365 E3 med Microsoft 365 E5 Sikkerhed tilføjelsesprogrammet|
|

### <a name="4-devices"></a>4. Enheder

Til enheds- og appadministration:

| Funktionalitet eller funktion | Beskrivelse | Hjælper med at forhindre... | Licensering |
|:-------|:-----|:-------|:-------|
| Microsoft Intune | Administrer enheder og de programmer, der kører på dem.  | Kompromis og adgang til enhed eller app. | Microsoft 365 E3 eller E5 |
|  |  |  |  |

Til Windows 11 eller 10 enheder:

| Funktionalitet eller funktion | Beskrivelse | Hjælper... | Licensering |
|:-------|:-----|:-------|:-------|
| Microsoft Defender Firewall | Indeholder en værtsbaseret firewall.  | Undgå angreb fra indgående, uopfordret netværkstrafik. | Microsoft 365 E3 eller Microsoft 365 E5 |
| Microsoft Defender Antivirus | Indeholder antimalwarebeskyttelse af enheder (slutpunkter) ved hjælp af maskinlæring, analyse af big-data, dybdegående forskning i trusselsbeskyttelse og Microsofts skyinfrastruktur. | Forebyd installation og kørsel af malware. | Microsoft 365 E3 eller Microsoft 365 E5 |
| Microsoft Defender SmartScreen | Beskytter mod phishing- eller malwarewebsteder og -programmer og download af potentielt skadelige filer. | Bloker eller advar, når du kontrollerer websteder, overførsler, apps og filer. | Microsoft 365 E3 eller Microsoft 365 E5 |
| Microsoft Defender til Slutpunkt | Hjælper med at forhindre, registrere, undersøge og reagere på avancerede trusler på tværs af enheder (slutpunkter). | Beskyt dig mod tæmmelse af netværket. | Microsoft 365 E5 eller Microsoft 365 E3 med Microsoft 365 E5 Sikkerhed tilføjelsesprogrammet |
|  |  |  |  |

### <a name="5-information"></a>5. Oplysninger

| Funktionalitet eller funktion | Beskrivelse | Hjælper... | Licensering |
|:-------|:-----|:-------|:-------|
| Styret mappeadgang | Beskytter dine data ved at kontrollere apps mod en liste over kendte, pålidelige apps. | Undgå, at filer ændres eller krypteres via ransomware. | Microsoft 365 E3 eller Microsoft 365 E5 |
| Microsoft Information Protection | Aktiverer følsomhedsmærkater, der kan anvendes på oplysninger, der ikke kan ses | Forhindre brug af oplysninger, der eksfiltreres. | Microsoft 365 E3 eller Microsoft 365 E5 |
| Forebyggelse af datatab (DLP) | Beskytter følsomme data og reducerer risikoen ved at forhindre brugere i at dele dem upassende. | Undgå udfyldning af data. | Microsoft 365 E3 eller Microsoft 365 E5 |
| Defender til skyapps | En sikkerhedsmægler til skyadgang til opdagelse, undersøgelse og styring. | Registrere lateral bevægelse og forhindre dataudfyldning. | Microsoft 365 E5 eller Microsoft 365 E3 med Microsoft 365 E5 Sikkerhed tilføjelsesprogrammet |
|

## <a name="impact-on-users-and-change-management"></a>Indvirkning på brugere og administration af ændringer

Implementering af yderligere sikkerhedsfunktioner og implementeringskrav og sikkerhedspolitikker for din Microsoft 365 lejer kan påvirke dine brugere. 

Du kan f.eks. indføre en ny sikkerhedspolitik, der kræver, at brugerne opretter nye teams til specifikke formål med en liste over brugerkonti som medlemmer i stedet for nemmere at oprette et team for alle brugere i organisationen. Dette kan hjælpe med at forhindre en ransomware-hacker i at udforske teams, der ikke er tilgængelige for hackerens kompromitterede brugerkonto og målrette ressourcer for det pågældende team i de efterfølgende angreb.

Denne basisløsning kan identificere, hvornår nye konfigurationer eller anbefalede sikkerhedspolitikker kan påvirke dine brugere, så du kan udføre den nødvendige administration af ændringer.

## <a name="next-steps"></a>Næste trin

Brug disse trin til at installere omfattende beskyttelse af din Microsoft 365 lejer:

1. [Konfigurere grundlinjer for sikkerhed](ransomware-protection-microsoft-365-security-baselines.md)
2. [Udrul registrering af angreb og svar](ransomware-protection-microsoft-365-attack-detection-response.md)
3. [Beskyt identiteter](ransomware-protection-microsoft-365-identities.md)
4. [Beskyt enheder](ransomware-protection-microsoft-365-devices.md)
5. [Beskyt oplysninger](ransomware-protection-microsoft-365-information.md)

[![Trin 1 til beskyttelse mod ransomware med Microsoft 365](../media/ransomware-protection-microsoft-365/ransomware-protection-microsoft-365-step1.png)](ransomware-protection-microsoft-365-security-baselines.md)

## <a name="additional-ransomware-resources"></a>Yderligere ransomware-ressourcer

Vigtige oplysninger fra Microsoft:

- [Den voksende trussel om ransomware](https://blogs.microsoft.com/on-the-issues/2021/07/20/the-growing-threat-of-ransomware/), Microsoft On the Issues blog post on July 20, 2021
- [Human ransomware](/security/compass/human-operated-ransomware)
- [Beskyt hurtigt mod ransomware og afpressning](/security/compass/protect-against-ransomware)
- [2021 Microsoft Digital Defense Report](https://www.microsoft.com/security/business/microsoft-digital-defense-report) (se side 10-19)
- [Ransomware: En pervasiv og løbende rapport over](https://security.microsoft.com/threatanalytics3/05658b6c-dc62-496d-ad3c-c6a795a33c27/overview) trusler mod trusler i Microsoft 365 Defender-portalen
- Microsofts registrerings- og svarteam (ACE) [ransomware-tilgang og bedste fremgangsmåder](/security/compass/incident-response-playbook-dart-ransomware-approach) og [casestudie](/security/compass/dart-ransomware-case-study)

Microsoft 365:

- [Maksimere ransomware-fleksibilitet med Azure og Microsoft 365](https://azure.microsoft.com/resources/maximize-ransomware-resiliency-with-azure-and-microsoft-365/)
- [Gendan efter en ransomware-angreb](/microsoft-365/security/office-365-security/recover-from-ransomware)
- [Beskyttelse mod malware og ransomware](/compliance/assurance/assurance-malware-and-ransomware-protection)
- [Beskyt din Windows 10-pc mod ransomware](https://support.microsoft.com//windows/protect-your-pc-from-ransomware-08ed68a7-939f-726c-7e84-a72ba92c01c3)
- [Håndtering af ransomware i SharePoint Online](/sharepoint/troubleshoot/security/handling-ransomware-in-sharepoint-online)
- [Rapporter om trusselsanalyse for ransomware](https://security.microsoft.com/threatanalytics3?page_size=30&filters=tags%3DRansomware&ordering=-lastUpdatedOn&fields=displayName,alertsCount,impactedEntities,reportType,createdOn,lastUpdatedOn,tags,flag) i Microsoft 365 Defender-portalen

Microsoft 365 Defender:

- [Find ransomware med avanceret jagt](/microsoft-365/security/defender/advanced-hunting-find-ransomware)

Microsoft Azure:

- [Azure-forsvar til ransomware-angreb](https://azure.microsoft.com/resources/azure-defenses-for-ransomware-attack/)
- [Maksimere ransomware-fleksibilitet med Azure og Microsoft 365](https://azure.microsoft.com/resources/maximize-ransomware-resiliency-with-azure-and-microsoft-365/)
- [Plan for sikkerhedskopiering og gendannelse for at beskytte dig mod ransomware](/security/compass/backup-plan-to-protect-against-ransomware)
- [Hjælp med at beskytte mod ransomware Microsoft Azure sikkerhedskopiering](https://www.youtube.com/watch?v=VhLOr2_1MCg) (26-minutters video)
- [Genoprettelse af identitet efter identitet, der er identiteter, er blevet genoprettet](/azure/security/fundamentals/recover-from-identity-compromise)
- [Avanceret registrering af multistage-angreb i Microsoft Sentinel](/azure/sentinel/fusion#ransomware)
- [Registrering af fusion til ransomware i Microsoft Sentinel](https://techcommunity.microsoft.com/t5/azure-sentinel/what-s-new-fusion-detection-for-ransomware/ba-p/2621373)

Microsoft Defender til skyapps:

-  [Opret anomaliregistreringspolitikker i Defender til skyapps](/cloud-app-security/anomaly-detection-policy)

Blogindlæg for Microsoft-sikkerhedsteamet:

- [3 trin til at forebygge og genoprette fra ransomware (september 2021)](https://www.microsoft.com/security/blog/2021/09/07/3-steps-to-prevent-and-recover-from-ransomware/)
- [En vejledning i at bekæmpe human ransomware: Del 1 (september 2021)](https://www.microsoft.com/security/blog/2021/09/20/a-guide-to-combatting-human-operated-ransomware-part-1/)

  Vigtige trin til, hvordan Microsofts registrerings- og svarteam (AFS) udfører undersøgelser af ransomware-hændelser.

- [En vejledning til at bekæmpe human ransomware: Del 2 (september 2021)](https://www.microsoft.com/security/blog/2021/09/27/a-guide-to-combatting-human-operated-ransomware-part-2/)

  Anbefalinger og bedste fremgangsmåder.

- [Bliv robust ved at forstå risici i cybersikkerhed: Del 4 – navigering i aktuelle trusler (maj 2021)](https://www.microsoft.com/security/blog/2021/05/26/becoming-resilient-by-understanding-cybersecurity-risks-part-4-navigating-current-threats/)

  Se **afsnittet ransomware** .

- [Ransomware-angreb drevet af mennesker: En undgåelig nedbrud (marts 2020)](https://www.microsoft.com/security/blog/2020/03/05/human-operated-ransomware-attacks-a-preventable-disaster/)

  Omfatter angrebskædeanalyser af faktiske angreb.

- [Ransomware-svar – for at betale eller ej at betale? (December 2019)](https://www.microsoft.com/security/blog/2019/12/16/ransomware-response-to-pay-or-not-to-pay/)
- [Norsk Bing reagerer på ransomware-angreb med gennemsigtighed (december 2019)](https://www.microsoft.com/security/blog/2019/12/17/norsk-hydro-ransomware-attack-transparency/)
