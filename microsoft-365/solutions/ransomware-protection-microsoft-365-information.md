---
title: Trin 5. Beskyt oplysninger
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
ms.custom: seo-marvel-jun2020
keywords: ransomware, ransomware drevet af mennesker, ransomware drevet af mennesker, HumOR, extortionsangreb, ransomware-angreb, kryptering, cryptovirologi, nultillids
description: Brug kontrolleret mappeadgang, MIP, DLP og Microsoft Defender til skyapps til at beskytte Microsoft 365 følsomme data.
ms.openlocfilehash: 0011a3c9fc0d24815818b67906b8f404a191563e
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63598494"
---
# <a name="step-5-protect-information"></a>Trin 5. Beskyt oplysninger

Da ransomware-hackere også vil kigge på dine lokale data, der er placeret i filer, databaser og andre typer servere, er en af de bedste måder at beskytte disse data på at overføre dem til din Microsoft 365-lejer. Når den er der, kan den være beskyttet af indbyggede afhjælpnings- og genoprettelsesfunktioner som f.eks. [versionsoprettelse, papirkurv og filgendannelse](ransomware-protection-microsoft-365.md#ransomware-mitigation-and-recovery-capabilities-provided-with-microsoft-365).

Sådan yder du yderligere beskyttelse af følsomme oplysninger i din Microsoft 365 lejer:

- Find dine følsomme oplysninger.
- Implementer restriktive tilladelser, og fjern bred adgang (du kan f.eks. forhindre for mange brugere med skrive-, redigerings- og sletningsfunktioner).
- Beskyt dine følsomme oplysninger.

>[!Note]
>Du kan finde detaljerede installationsvejledninger til beskyttelse af oplysninger Microsoft 365 en lejer i [Deploy Information Protection for data privacy regulations](information-protection-deploy.md). Selvom den er beregnet til bestemmelser om beskyttelse af personlige oplysninger, gælder meget af vejledningen også for ransomware-beskyttelse.
>

## <a name="locate-your-sensitive-information"></a>Find dine følsomme oplysninger

Den første opgave er [at identificere typerne og placeringen af](/microsoft-365/compliance/information-protection#know-your-data) følsomme oplysninger i din lejer, hvilket kan omfatte følgende typer:

- Følsom
- Ejendomsret eller intellektuel ejendom
- Regulerede, sådanne regionale bestemmelser, der giver beskyttelse af personlige identifikationsoplysninger (PII)
- IT-genoprettelsesplaner

For hver type af følsomme oplysninger skal du bestemme følgende:

- Brug af oplysningerne til din organisation
- Et relativt mål for dens pengeværdi, hvis den blev opbevaret for noterne (f.eks. høj, mellem, lav)
- Dens aktuelle placering, f.eks. en OneDrive eller SharePoint eller samarbejdsplacering som f.eks. et Microsoft Teams team
- De aktuelle tilladelser, som består af:

   - De brugerkonti, der har adgang

   - De handlinger, der er tilladt for hver konto, der har adgang 

## <a name="implement-strict-permissions-for-locations-with-sensitive-information"></a>Implementere restriktive tilladelser for placeringer med følsomme oplysninger

Hvis du implementerer restriktive tilladelser i din Microsoft 365-lejer, anvendes princippet om mindste rettigheder til placeringer og kommunikationssteder, som i Microsoft 365 typisk er OneDrive-mapper, SharePoint websteder og mapper og teams. 

Det er nemmere at oprette fillagringsplaceringer eller teams med bred adgang (f.eks. standard for alle i organisationen), for følsomme oplysninger er de brugerkonti, der er tilladt, og de handlinger, der er tilladt, begrænset til det minimum, der kræves for at opfylde samarbejds- og forretningskrav.

Når en ransomware-hacker har infiltreret din lejer, forsøger de at eskalere deres rettigheder ved at forringe legitimationsoplysningerne for brugerkonti med bredere omfang af tilladelser på tværs af din lejer, f.eks. administratorrollekonti eller brugerkonti, der har adgang til følsomme oplysninger. 

Baseret på denne typiske hackeradfærd er der to niveauer af besvær for hackeren:

- **Lav:** En hacker kan bruge en konto med lav tilladelse og opdage dine følsomme oplysninger på grund af bred adgang i hele din lejer.
- **Højere:** En hacker kan ikke bruge en konto med lav tilladelse og opdage dine følsomme oplysninger på grund af strenge tilladelser. De skal eskalere deres tilladelser ved at fastslå og derefter forringe legitimationsoplysningerne for en konto, der har adgang til en placering med følsomme oplysninger, men derefter kan de muligvis kun udføre et begrænset antal handlinger.

Ved følsomme oplysninger skal du gøre problemniveauet så højt som muligt.

Du kan sikre dig strenge tilladelser i din lejer med disse trin:

1. Når du vil [finde dine følsomme oplysninger](#locate-your-sensitive-information), skal du gennemse tilladelserne for placeringerne af følsomme oplysninger. 
2. Implementer restriktive tilladelser for følsomme oplysninger under mødesamarbejde og forretningsmæssige krav, og informer de brugere, der er påvirket.
3. Udfør administration af ændringer for dine brugere, så fremtidige placeringer af følsomme oplysninger oprettes og vedligeholdes med strenge tilladelser.
4. Overvåg og overvåg placeringerne for følsomme oplysninger for at sikre, at der ikke gives generelle tilladelser.

Se [Konfigurer sikker fildeling og samarbejde med andre Microsoft Teams](setup-secure-collaboration-with-teams.md) for at få detaljeret vejledning. Et eksempel på et kommunikations- og samarbejdssted med strenge tilladelser til følsomme oplysninger er et [team med sikkerhedsisolation](/microsoft-365/solutions/secure-teams-security-isolation).

## <a name="protect-your-sensitive-information"></a>Beskyt dine følsomme oplysninger

Sådan beskytter du dine følsomme oplysninger i tilfælde af, at en ransomware hacker får adgang til dem:

- Brug [styret mappeadgang](/windows/security/threat-protection/microsoft-defender-atp/controlled-folders) til at gøre det sværere for uautoriserede programmer at redigere dataene i kontrollerede mapper.

- Brug [Microsoft Information Protection og](/microsoft-365/compliance/information-protection) følsomhedsmærkater, og anvend dem på følsomme oplysninger. Følsomhedsmærkater kan konfigureres til yderligere kryptering og tilladelser med definerede brugerkonti og tilladte handlinger. En fil med denne type følsomhedsmærkat, der er eksfiltreret fra din lejer, kan kun bruges til en brugerkonto, der er defineret i mærkaten.

- Brug Microsoft 365 forebyggelse af datatab [(DLP)](/microsoft-365/compliance/dlp-learn-about-dlp) til at registrere, advare og blokere risikabelt, utilsigtet eller upassende deling af data, der indeholder personlige eller fortrolige oplysninger, baseret på følsomhedsmærkater, både internt og eksternt.

- Brug [Microsoft Defender til skyapps](/cloud-app-security/what-is-cloud-app-security) til at blokere overførsler af følsomme oplysninger, f.eks filer. Du kan også bruge politikker til registrering af problemer [med Defender til](/cloud-app-security/anomaly-detection-policy#ransomware-activity) skyapps til at registrere en høj hastighed af filuploads eller filsletningsaktiviteter.

## <a name="impact-on-users-and-change-management"></a>Indvirkning på brugere og administration af ændringer

Administrative ændringer af generelle tilladelser kan føre til, at brugere nægtes adgang eller ikke kan udføre visse handlinger.

For at beskytte følsomme oplysninger i din Microsoft 365 lejer kan du også træne dine brugere til at:

- Opret kommunikations- og samarbejdssteder med strenge tilladelser (minimumsættet af brugerkonti til adgang og minimum tilladte handlinger for hver konto). 
- Anvend de korrekte følsomhedsmærkater på følsomme oplysninger.
- Brug styret mappeadgang.

## <a name="resulting-configuration"></a>Resulterende konfiguration

Her er beskyttelse mod ransomware for din lejer for trin 1-5.

![Beskyttelse mod ransomware for din Microsoft 365 lejer efter trin 5](../media/ransomware-protection-microsoft-365/ransomware-protection-microsoft-365-architecture-step5.png)

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
