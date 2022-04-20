---
title: Udrul ransomware-beskyttelse til din Microsoft 365 lejer
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
keywords: ransomware, menneskelig drevet ransomware, menneskelig drevet ransomware, HumOR, extortion attack, ransomware angreb, kryptering, kryptovirologi, nul tillid
description: Træd gennem beskyttelse af dine Microsoft 365 ressourcer mod ransomware-angreb.
ms.openlocfilehash: fde24132341512d76467284cb2f9c9b11b7d88cc
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/19/2022
ms.locfileid: "64943233"
---
# <a name="deploy-ransomware-protection-for-your-microsoft-365-tenant"></a>Udrul ransomware-beskyttelse til din Microsoft 365 lejer

Ransomware er en type afpresningsangreb, der ødelægger eller krypterer filer og mapper, hvilket forhindrer adgang til kritiske data. Vare ransomware spredes typisk som en virus, der inficerer enheder og kun kræver afhjælpning af malware. Menneskelig drevet ransomware er resultatet af et aktivt angreb fra cyberkriminelle, der infiltrerer en organisations it-infrastruktur i det lokale miljø eller cloudmiljøet, hæver deres rettigheder og udruller ransomware til kritiske data.

Når angrebet er fuldført, kræver en hacker penge fra ofrene til gengæld for de slettede filer, dekrypteringsnøgler til krypterede filer eller et løfte om ikke at frigive følsomme data til det mørke web eller det offentlige internet. Menneskedrevet ransomware kan også bruges til at lukke kritiske maskiner eller processer, såsom dem, der er nødvendige for industriel produktion, hvilket stopper normale forretningsaktiviteter, indtil løsesummen betales, og skaden korrigeres, eller organisationen afhjælper skaden selv.

Et menneskeligt drevet ransomware-angreb kan være katastrofalt for virksomheder i alle størrelser og er svært at rydde op, hvilket kræver fuldstændig modsatrettet fjernelse for at beskytte mod fremtidige angreb. I modsætning til vare ransomware, menneskelig-drevet ransomware kan fortsætte med at true virksomheder operationer efter den første løsesum anmodning.

>[!Note]
>Et ransomware-angreb på en Microsoft 365 lejer forudsætter, at hackeren har gyldige legitimationsoplysninger til brugerkontoen for en lejer og har adgang til alle de filer og ressourcer, der er tilladt til brugerkontoen. En hacker uden gyldige legitimationsoplysninger til brugerkontoen skal dekryptere inaktive data, der er krypteret af Microsoft 365 standard og forbedret kryptering. Du kan få flere oplysninger under [Oversigt over kryptering og administration af nøgler](/compliance/assurance/assurance-encryption). 
>

Du kan finde flere oplysninger om beskyttelse af ransomware på tværs af Microsoft-produkter under disse [yderligere ransomware-ressourcer](#additional-ransomware-resources).

## <a name="security-in-the-cloud-is-a-partnership"></a>Sikkerhed i cloudmiljøet er et partnerskab

Sikkerheden i dine Microsoft-cloudtjenester er et partnerskab mellem dig og Microsoft:

- Microsofts cloudtjenester er bygget på et fundament af tillid og sikkerhed. Microsoft giver dig sikkerhedskontroller og -funktioner, der kan hjælpe dig med at beskytte dine data og programmer.
- Du ejer dine data og identiteter og ansvaret for at beskytte dem, sikkerheden for dine ressourcer i det lokale miljø og sikkerheden for cloudkomponenter, som du styrer.

Ved at kombinere disse funktioner og ansvar, kan vi give den bedste beskyttelse mod en ransomware angreb.

## <a name="ransomware-mitigation-and-recovery-capabilities-provided-with-microsoft-365"></a>Ransomware-afhjælpnings- og genoprettelsesfunktioner, der leveres med Microsoft 365

En ransomware-hacker, der har infiltreret en Microsoft 365 lejer, kan holde din organisation som løsesum ved at:

- Sletning af filer eller mail
- Krypterer filer på plads
- Kopierer filer uden for din lejer (dataudfiltrering)

Men Microsoft 365 onlinetjenester har mange indbyggede funktioner og kontrolelementer til at beskytte kundedata mod ransomware-angreb. Følgende afsnit indeholder en oversigt. Du kan finde flere oplysninger om, hvordan Microsoft beskytter kundedata, [malware og ransomware-beskyttelse i Microsoft 365](/compliance/assurance/assurance-malware-and-ransomware-protection).

>[!Note]
>Et ransomware-angreb på en Microsoft 365 lejer forudsætter, at hackeren har gyldige legitimationsoplysninger til brugerkontoen for en lejer og har adgang til alle de filer og ressourcer, der er tilladt til brugerkontoen. En hacker uden gyldige legitimationsoplysninger til brugerkontoen skal dekryptere inaktive data, der er krypteret af Microsoft 365 standard og forbedret kryptering. Du kan få flere oplysninger under [Oversigt over kryptering og administration af nøgler](/compliance/assurance/assurance-encryption). 
>

### <a name="deleting-files-or-email"></a>Sletning af filer eller mail

Filer i SharePoint og OneDrive for Business er beskyttet af:

- Versionering 

   Microsoft 365 bevarer som standard mindst 500 versioner af en fil og kan konfigureres til at bevare flere. 

   Hvis du vil minimere byrden for dine sikkerheds- og helpdesk-medarbejdere, skal du oplære dine brugere i, hvordan [du gendanner tidligere versioner af filer](https://support.microsoft.com/office/restore-a-previous-version-of-an-item-or-file-in-sharepoint-f66dbda0-81f4-4d1e-b08c-793265c58934).

- Papirkurven

   Hvis ransomware opretter en ny krypteret kopi af filen og sletter den gamle fil, har kunderne 93 dage til at gendanne den fra papirkurven. Efter 93 dage er der et 14-dages vindue, hvor Microsoft stadig kan gendanne dataene. 
  
   Hvis du vil minimere byrden for dine sikkerheds- og helpdesk-medarbejdere, skal du oplære dine brugere i, hvordan [de gendanner filer fra papirkurven](https://support.microsoft.com/office/restore-deleted-items-from-the-site-collection-recycle-bin-5fa924ee-16d7-487b-9a0a-021b9062d14b).

- [Gendannelse af filer](https://support.microsoft.com/office/restore-your-onedrive-fa231298-759d-41cf-bcd0-25ac53eb8a15)

   En komplet selvbetjent genoprettelsesløsning til SharePoint og OneDrive, der giver administratorer og slutbrugere mulighed for at gendanne filer fra et hvilket som helst tidspunkt i løbet af de sidste 30 dage.

   Oplær dine brugere i [Gendannelse af filer](https://support.microsoft.com/office/restore-your-onedrive-fa231298-759d-41cf-bcd0-25ac53eb8a15) for at minimere byrden på din sikkerhed og it-helpdeskpersonalet.


For OneDrive og SharePoint filer kan Microsoft gå tilbage til et tidligere tidspunkt i op til 14 dage, hvis du rammes af et masseangreb.

Mail er beskyttet af:

- [Genoprettelse af et enkelt element](/exchange/recipients-in-exchange-online/manage-user-mailboxes/enable-or-disable-single-item-recovery) og opbevaring af postkasser, hvor du kan gendanne elementer i en postkasse ved utilsigtet eller ondsindet for tidlig sletning. Du kan som standard annullere mails, der er slettet inden for 14 dage, og som kan konfigureres op til 30 dage.

- [Opbevaringspolitikker](/exchange/security-and-compliance/messaging-records-management/retention-tags-and-policies) giver dig mulighed for at bevare uforanderlige kopier af mail for den konfigurerede opbevaringsperiode.

### <a name="encrypting-files-in-place"></a>Krypterer filer på plads

Som tidligere beskrevet er filer i SharePoint og OneDrive for Business beskyttet mod skadelig kryptering med:

- Versionering
- Papirkurven
- Bibliotek med bevarelsesventepositioner

Du kan finde flere oplysninger under [Håndtering af beskadigelse af data i Microsoft 365](/compliance/assurance/assurance-dealing-with-data-corruption).

### <a name="copying-files-outside-your-tenant"></a>Kopierer filer uden for din lejer 

Du kan forhindre en ransomware-hacker i at kopiere filer uden for din lejer med:

- [Microsoft Purview DLP-politikker (Forebyggelse af datatab)](/microsoft-365/compliance/dlp-learn-about-dlp)

    Registrer, advar og bloker risikable, utilsigtede eller upassende deling af data, der indeholder:

    - Personlige oplysninger, f.eks. personident identificerende oplysninger for overholdelse af regionale bestemmelser om beskyttelse af personlige oplysninger.

    - Fortrolige organisationsoplysninger baseret på følsomhedsmærkater.

- [Microsoft Defender for Cloud Apps](/cloud-app-security/what-is-cloud-app-security)

    Bloker downloads af følsomme oplysninger, f.eks. filer. 

    Du kan også bruge sessionspolitikker for [Defender for Cloud Apps-appkontrol med betinget adgang](/cloud-app-security/tutorial-dlp#how-to-discover-and-protect-sensitive-information-in-your-organization) til at overvåge informationsflowet mellem en bruger og et program i realtid.

## <a name="whats-in-this-solution"></a>Hvad er der i denne løsning

Denne løsning hjælper dig gennem udrulningen af Microsoft 365 beskyttelse og afhjælpningsfunktioner, konfigurationer og igangværende handlinger for at minimere muligheden for, at en ransomware-hacker kan bruge de kritiske data i din Microsoft 365 lejer og holde din organisation som løsepenge.

![De skridt til at beskytte mod ransomware med Microsoft 365](../media/ransomware-protection-microsoft-365/ransomware-protection-microsoft-365-step-grid.png)

Trinnene i denne løsning er:

1. [Konfigurer grundlæggende sikkerhedsoplysninger](ransomware-protection-microsoft-365-security-baselines.md)
2. [Udrul registrering af angreb og svar](ransomware-protection-microsoft-365-attack-detection-response.md)
3. [Beskyt identiteter](ransomware-protection-microsoft-365-identities.md)
4. [Beskyt enheder](ransomware-protection-microsoft-365-devices.md)
5. [Beskyt oplysninger](ransomware-protection-microsoft-365-information.md)

Her er de fem trin i løsningen, der er installeret for din Microsoft 365 lejer.

![Ransomware-beskyttelse af en Microsoft 365 lejer](../media/ransomware-protection-microsoft-365/ransomware-protection-microsoft-365-architecture.png)

Denne løsning bruger principperne for [Nul tillid](/security/zero-trust/): 

- **Bekræft eksplicit:** Godkend og godkend altid baseret på alle tilgængelige datapunkter.
- **Brug adgang med færrest rettigheder:** Begræns brugeradgang med Just-In-Time og Just-Enough-Access (JIT/JEA), risikobaserede tilpassede politikker og databeskyttelse.
- **Antag brud:** Minimer eksplosionsradius og segmentadgang. Bekræft kryptering fra slutpunkt til slutpunkt, og brug analyser til at få synlighed, skabe trusselsregistrering og forbedre forsvaret.

I modsætning til almindelig intranetadgang, der har tillid til alt bag en organisations firewall, behandler Nul tillid hvert enkelt logon og adgang, som om det stammer fra et ikke-kontrolleret netværk, uanset om det er bag organisationens firewall eller på internettet. Nul tillid kræver beskyttelse af netværket, infrastrukturen, identiteter, slutpunkter, apps og data.

## <a name="microsoft-365-capabilities-and-features"></a>Microsoft 365 funktioner og funktioner

For at beskytte din Microsoft 365 lejer mod et ransomware-angreb, skal du bruge disse Microsoft 365 funktioner til disse trin i løsningen.

### <a name="1-security-baseline"></a>1. Oprindelig sikkerhedsplan

| Funktionalitet eller funktion | Beskrivelse | Hjælper... | Licensering |
|:-------|:-----|:-------|:-------|
| Microsoft Secure Score |  Måler sikkerhedsholdning for en Microsoft 365 lejer. | Vurder din sikkerhedskonfiguration, og foreslå forbedringer. | Microsoft 365 E3 eller Microsoft 365 E5 |
| Regler for reduktion af angrebsoverflade | Reducerer din organisations sårbarhed over for cyberangreb ved hjælp af en række konfigurationsindstillinger. | Bloker mistænkelig aktivitet og sårbart indhold. | Microsoft 365 E3 eller Microsoft 365 E5 |
| Exchange mailindstillinger |  Aktiverer tjenester, der reducerer din organisations sårbarhed over for et mailbaseret angreb. | Undgå indledende adgang til din lejer via phishing og andre mailbaserede angreb.  | Microsoft 365 E3 eller Microsoft 365 E5 |
| Indstillinger for Microsoft Windows, Microsoft Edge og Microsoft 365 Apps for Enterprise | Leverer branchestandardsikkerhedskonfigurationer, der er bredt kendte og gennemtestede. | Undgå angreb via Windows, Edge og Microsoft 365 Apps for Enterprise. | Microsoft 365 E3 eller Microsoft 365 E5 |
|

### <a name="2-detection-and-response"></a>2. Registrering og svar

| Funktionalitet eller funktion | Beskrivelse | Hjælper med at registrere og reagere på... | Licensering |
|:-------|:-----|:-------|:-------|
| Microsoft 365 Defender | Kombinerer signaler og orkestrerer funktioner i en enkelt løsning. <br><br> Gør det muligt for sikkerhedseksperter at sy trusselssignaler sammen og bestemme det fulde omfang og den fulde indvirkning af en trussel. <br><br> Automatiserer handlinger for at forhindre eller stoppe angrebet og selvreparerende berørte postkasser, slutpunkter og brugeridentiteter. | Hændelser, som er de kombinerede beskeder og data, der udgør et angreb. | Microsoft 365 E5 eller Microsoft 365 E3 med tilføjelsesprogrammet Microsoft 365 E5 Sikkerhed |
| Microsoft Defender for Identity |  Identificerer, registrerer og undersøger avancerede trusler, kompromitterede identiteter og skadelige insiderhandlinger, der er rettet mod din organisation via en cloudbaseret sikkerhedsgrænseflade, bruger dine AD DS-signaler (Active Directory i det lokale miljø Domain Services). | Kompromitterede legitimationsoplysninger for AD DS-konti. | Microsoft 365 E5 eller Microsoft 365 E3 med tilføjelsesprogrammet Microsoft 365 E5 Sikkerhed |
| Microsoft Defender for Office 365 | Beskytter din organisation mod skadelige trusler fra mails, links (URL-adresser) og samarbejdsværktøjer. <br><br> Beskytter mod malware, phishing, spoofing og andre angrebstyper. | Phishingangreb. | Microsoft 365 E5 eller Microsoft 365 E3 med tilføjelsesprogrammet Microsoft 365 E5 Sikkerhed |
| Microsoft Defender for Endpoint | Aktiverer registrering og svar på avancerede trusler på tværs af slutpunkter (enheder). | Installation af skadelig software og kompromitteret enhed. | Microsoft 365 E5 eller Microsoft 365 E3 med tilføjelsesprogrammet Microsoft 365 E5 Sikkerhed |
| Identitetsbeskyttelse for Azure Active Directory (Azure AD) | Automatiserer registrering og afhjælpning af identitetsbaserede risici og undersøgelse af disse risici. | Kompromitterer legitimationsoplysninger for Azure AD-konti og rettighedseskalering. | Microsoft 365 E5 eller Microsoft 365 E3 med tilføjelsesprogrammet Microsoft 365 E5 Sikkerhed |
| Defender for Cloud Apps | En cloudadgangssikkerhedsmægler til registrering, undersøgelse og styring på tværs af alle dine cloudtjenester fra Microsoft og tredjepart. | Tværgående flytning og dataudfiltrering. | Microsoft 365 E5 eller Microsoft 365 E3 med tilføjelsesprogrammet Microsoft 365 E5 Sikkerhed |
|

### <a name="3-identities"></a>3. Identiteter

| Funktionalitet eller funktion | Beskrivelse | Hjælper med at forhindre... | Licensering |
|:-------|:-----|:-------|:-------|
|Azure AD-adgangskodebeskyttelse | Bloker adgangskoder fra en fælles liste og brugerdefinerede poster. | Bestemmelse af adgangskoden til en cloudbrugerkonto eller en brugerkonto i det lokale miljø. |Microsoft 365 E3 eller Microsoft 365 E5|
|MFA gennemtvunget med betinget adgang | Kræv MFA baseret på egenskaberne for brugerlogon med politikker for betinget adgang. | Kompromitterede legitimationsoplysninger og adgang. | Microsoft 365 E3 eller Microsoft 365 E5|
|MFA gennemtvunget med risikobaseret betinget adgang | Kræv MFA baseret på risikoen for brugerlogon med Azure AD Identity Protection. |Kompromitterede legitimationsoplysninger og adgang. | Microsoft 365 E5 eller Microsoft 365 E3 med tilføjelsesprogrammet Microsoft 365 E5 Sikkerhed|
|

### <a name="4-devices"></a>4. Enheder

Til administration af enheder og apps:

| Funktionalitet eller funktion | Beskrivelse | Hjælper med at forhindre... | Licensering |
|:-------|:-----|:-------|:-------|
| Microsoft Intune | Administrer enheder og de programmer, der kører på dem.  | Kompromitterer og giver adgang til en enhed eller app. | Microsoft 365 E3 eller E5 |
|  |  |  |  |

For Windows 11 eller 10 enheder:

| Funktionalitet eller funktion | Beskrivelse | Hjælper... | Licensering |
|:-------|:-----|:-------|:-------|
| Microsoft Defender Firewall | Leverer en værtsbaseret firewall.  | Undgå angreb fra indgående, uopfordret netværkstrafik. | Microsoft 365 E3 eller Microsoft 365 E5 |
| Microsoft Defender Antivirus | Leverer antimalwarebeskyttelse af enheder (slutpunkter) ved hjælp af maskinel indlæring, analyse af big data, dybdegående undersøgelse af trusselsresistens og Microsofts cloudinfrastruktur. | Undgå installation og kørsel af malware. | Microsoft 365 E3 eller Microsoft 365 E5 |
| Microsoft Defender SmartScreen | Beskytter mod phishing- eller malwarewebsteder og -programmer og download af potentielt skadelige filer. | Bloker eller advar, når du kontrollerer websteder, downloads, apps og filer. | Microsoft 365 E3 eller Microsoft 365 E5 |
| Microsoft Defender for Endpoint | Hjælper med at forhindre, registrere, undersøge og reagere på avancerede trusler på tværs af enheder (slutpunkter). | Beskyt mod netværksforsempning. | Microsoft 365 E5 eller Microsoft 365 E3 med tilføjelsesprogrammet Microsoft 365 E5 Sikkerhed |
|  |  |  |  |

### <a name="5-information"></a>5. Oplysninger

| Funktionalitet eller funktion | Beskrivelse | Hjælper... | Licensering |
|:-------|:-----|:-------|:-------|
| Styret mappeadgang | Beskytter dine data ved at kontrollere apps mod en liste over kendte apps, der er tillid til. | Forhindre filer i at blive ændret eller krypteret af ransomware. | Microsoft 365 E3 eller Microsoft 365 E5 |
| Microsoft Purview Information Protection | Gør det muligt at anvende følsomhedsmærkater på oplysninger, der kan løses. | Undgå brug af exfiltrated information. | Microsoft 365 E3 eller Microsoft 365 E5 |
| Forebyggelse af datatab (DLP) | Beskytter følsomme data og reducerer risikoen ved at forhindre brugerne i at dele dem upassende. | Undgå dataudfyldning. | Microsoft 365 E3 eller Microsoft 365 E5 |
| Defender for Cloud Apps | En cloudadgangssikkerhedsmægler til registrering, undersøgelse og styring. | Registrer tværgående flytning, og undgå dataudfiltrering. | Microsoft 365 E5 eller Microsoft 365 E3 med tilføjelsesprogrammet Microsoft 365 E5 Sikkerhed |
|

## <a name="impact-on-users-and-change-management"></a>Indvirkning på brugere og ændringsstyring

Udrulning af yderligere sikkerhedsfunktioner og implementering af krav og sikkerhedspolitikker for din Microsoft 365 lejer kan påvirke dine brugere. 

Du kan f.eks. pålægge en ny sikkerhedspolitik, der kræver, at brugerne opretter nye teams til bestemte brug med en liste over brugerkonti som medlemmer i stedet for nemmere at oprette et team for alle brugere i organisationen. Dette kan hjælpe med at forhindre en ransomware hacker i at udforske teams, der ikke er tilgængelige for hackerens kompromitterede brugerkonto og målrette ressourcerne i det pågældende team i det efterfølgende angreb.

Denne grundlæggende løsning identificerer, hvornår nye konfigurationer eller anbefalede sikkerhedspolitikker kan påvirke dine brugere, så du kan udføre den nødvendige ændringsstyring.

## <a name="next-steps"></a>Næste trin

Brug disse trin til at udrulle omfattende beskyttelse af din Microsoft 365 lejer:

1. [Konfigurer grundlæggende sikkerhedsoplysninger](ransomware-protection-microsoft-365-security-baselines.md)
2. [Udrul registrering af angreb og svar](ransomware-protection-microsoft-365-attack-detection-response.md)
3. [Beskyt identiteter](ransomware-protection-microsoft-365-identities.md)
4. [Beskyt enheder](ransomware-protection-microsoft-365-devices.md)
5. [Beskyt oplysninger](ransomware-protection-microsoft-365-information.md)

[![Trin 1 til beskyttelse af ransomware med Microsoft 365](../media/ransomware-protection-microsoft-365/ransomware-protection-microsoft-365-step1.png)](ransomware-protection-microsoft-365-security-baselines.md)

## <a name="additional-ransomware-resources"></a>Yderligere ransomware-ressourcer

Nøgleoplysninger fra Microsoft:

- [Den voksende trussel om ransomware](https://blogs.microsoft.com/on-the-issues/2021/07/20/the-growing-threat-of-ransomware/), Microsoft On the Issues blogindlæg den 20. juli 2021
- [Menneskedrevet ransomware](/security/compass/human-operated-ransomware)
- [Beskyt hurtigt mod ransomware og pengeafpresning](/security/compass/protect-against-ransomware)
- [2021 Microsoft Digital Defense Report](https://www.microsoft.com/security/business/microsoft-digital-defense-report) (se side 10-19)
- [Ransomware: En gennemtrængende og løbende rapport over trusselsanalyser](https://security.microsoft.com/threatanalytics3/05658b6c-dc62-496d-ad3c-c6a795a33c27/overview) på Microsoft 365 Defender-portalen
- Microsofts DART(Detection and Response Team) [ransomware-tilgang og bedste praksis](/security/compass/incident-response-playbook-dart-ransomware-approach) og [casestudie](/security/compass/dart-ransomware-case-study)

Microsoft 365:

- [Maksimer Ransomware Robusthed med Azure og Microsoft 365](https://azure.microsoft.com/resources/maximize-ransomware-resiliency-with-azure-and-microsoft-365/)
- [Gendan efter et ransomware-angreb](/microsoft-365/security/office-365-security/recover-from-ransomware)
- [Beskyttelse mod malware og ransomware](/compliance/assurance/assurance-malware-and-ransomware-protection)
- [Beskyt din Windows 10 pc mod ransomware](https://support.microsoft.com//windows/protect-your-pc-from-ransomware-08ed68a7-939f-726c-7e84-a72ba92c01c3)
- [Håndtering af ransomware i SharePoint Online](/sharepoint/troubleshoot/security/handling-ransomware-in-sharepoint-online)
- [Trusselsanalyserapporter for ransomware](https://security.microsoft.com/threatanalytics3?page_size=30&filters=tags%3DRansomware&ordering=-lastUpdatedOn&fields=displayName,alertsCount,impactedEntities,reportType,createdOn,lastUpdatedOn,tags,flag) på Microsoft 365 Defender-portalen

Microsoft 365 Defender:

- [Find ransomware med avanceret jagt](/microsoft-365/security/defender/advanced-hunting-find-ransomware)

Microsoft Azure:

- [Azure Defenses for Ransomware Attack](https://azure.microsoft.com/resources/azure-defenses-for-ransomware-attack/)
- [Maksimer Ransomware Robusthed med Azure og Microsoft 365](https://azure.microsoft.com/resources/maximize-ransomware-resiliency-with-azure-and-microsoft-365/)
- [Sikkerhedskopierings- og gendannelsesplan for beskyttelse mod ransomware](/security/compass/backup-plan-to-protect-against-ransomware)
- [Hjælp med at beskytte mod ransomware med Microsoft Azure backup](https://www.youtube.com/watch?v=VhLOr2_1MCg) (26-minutters video)
- [Gendannelse efter kompromitteret systemisk identitet](/azure/security/fundamentals/recover-from-identity-compromise)
- [Avanceret registrering af angreb i fleretages i Microsoft Sentinel](/azure/sentinel/fusion#ransomware)
- [Fusion Detection for Ransomware i Microsoft Sentinel](https://techcommunity.microsoft.com/t5/azure-sentinel/what-s-new-fusion-detection-for-ransomware/ba-p/2621373)

Microsoft Defender for Cloud Apps:

-  [Opret politikker for registrering af uregelmæssigheder i Defender for Cloud Apps](/cloud-app-security/anomaly-detection-policy)

Blogindlæg om Microsoft Security-teamet:

- [3 trin til at forhindre og komme sig efter ransomware (september 2021)](https://www.microsoft.com/security/blog/2021/09/07/3-steps-to-prevent-and-recover-from-ransomware/)
- [En guide til bekæmpelse af menneskeligt drevet ransomware: Del 1 (september 2021)](https://www.microsoft.com/security/blog/2021/09/20/a-guide-to-combatting-human-operated-ransomware-part-1/)

  Vigtige trin til, hvordan Microsofts detection and Response Team (DART) udfører ransomware-hændelsesundersøgelser.

- [En guide til bekæmpelse af menneskeligt drevet ransomware: Del 2 (september 2021)](https://www.microsoft.com/security/blog/2021/09/27/a-guide-to-combatting-human-operated-ransomware-part-2/)

  Anbefalinger og bedste praksis.

- [At blive modstandsdygtig ved at forstå cybersikkerhedsrisici: Del 4 – navigering i aktuelle trusler (maj 2021)](https://www.microsoft.com/security/blog/2021/05/26/becoming-resilient-by-understanding-cybersecurity-risks-part-4-navigating-current-threats/)

  Se afsnittet **Ransomware** .

- [Menneskedrevne ransomware-angreb: En forebyggelig katastrofe (marts 2020)](https://www.microsoft.com/security/blog/2020/03/05/human-operated-ransomware-attacks-a-preventable-disaster/)

  Indeholder analyser af angrebskæder af faktiske angreb.

- [Ransomware-svar – at betale eller ikke at betale? (december 2019)](https://www.microsoft.com/security/blog/2019/12/16/ransomware-response-to-pay-or-not-to-pay/)
- [Norsk Hydro reagerer på ransomware-angreb med gennemsigtighed (december 2019)](https://www.microsoft.com/security/blog/2019/12/17/norsk-hydro-ransomware-attack-transparency/)
