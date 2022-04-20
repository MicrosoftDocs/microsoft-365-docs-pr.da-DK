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
keywords: ransomware, menneskelig drevet ransomware, menneskelig drevet ransomware, HumOR, extortion attack, ransomware angreb, kryptering, kryptovirologi, nul tillid
description: Brug kontrolleret mappeadgang, Microsoft Purview Information Protection, DLP og Microsoft Defender for Cloud Apps til at beskytte dine Microsoft 365 følsomme data.
ms.openlocfilehash: e32c214688adb60fa39fc3c392512f46ec94aecf
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/19/2022
ms.locfileid: "64945125"
---
# <a name="step-5-protect-information"></a>Trin 5. Beskyt oplysninger

Da ransomware-hackere også vil se på dine data i det lokale miljø, der er placeret på fil, database og andre typer servere, er en af de bedste måder at beskytte disse data på at overføre dem til din Microsoft 365 lejer. Når den er der, kan den beskyttes af indbyggede afhjælpnings- og genoprettelsesfunktioner, f.eks [. versionering, papirkurv og gendannelse af filer](ransomware-protection-microsoft-365.md#ransomware-mitigation-and-recovery-capabilities-provided-with-microsoft-365).

Sådan yder du yderligere beskyttelse af følsomme oplysninger i din Microsoft 365 lejer:

- Find dine følsomme oplysninger.
- Implementer strenge tilladelser, og fjern bred adgang (undgå f.eks., at for mange brugere har skrive-, redigerings- og slettefunktioner).
- Beskyt dine følsomme oplysninger.

>[!Note]
>Du kan finde en detaljeret udrulningsvejledning til beskyttelse af oplysninger i en Microsoft 365 lejer under [Udrul regler for beskyttelse af personlige oplysninger](information-protection-deploy.md). Selvom det er beregnet til regler for beskyttelse af personlige oplysninger, gælder meget af vejledningen også for ransomware-beskyttelse.
>

## <a name="locate-your-sensitive-information"></a>Find dine følsomme oplysninger

Den første opgave er at [identificere typerne og placeringen](/microsoft-365/compliance/information-protection#know-your-data) af følsomme oplysninger i din lejer, som kan omfatte følgende typer:

- Følsomme
- Ejendomsret eller intellektuel ejendom
- Regulerede, sådanne regionale regler, der angiver beskyttelse af personlige identificerende oplysninger (PII)
- Planer for it-genoprettelse

For hver type følsomme oplysninger skal du bestemme følgende:

- Brugen af oplysningerne til din organisation
- En relativ måling af dens pengeværdi, hvis den blev holdt som løsesum (f.eks. høj, mellem, lav)
- Dens aktuelle placering, f.eks. en OneDrive eller SharePoint mappe eller et samarbejdssted, f.eks. et Microsoft Teams team
- De aktuelle tilladelser, der består af:

   - De brugerkonti, der har adgang

   - De handlinger, der er tilladt for hver konto, der har adgang 

## <a name="implement-strict-permissions-for-locations-with-sensitive-information"></a>Implementer strenge tilladelser for placeringer med følsomme oplysninger

Implementering af strenge tilladelser i din Microsoft 365 lejer bruger princippet om færrest mulige rettigheder for placeringer og kommunikationssteder, som i Microsoft 365 typisk er OneDrive mapper, SharePoint websteder og mapper samt teams. 

Selvom det er nemmere at oprette fillagringsplaceringer eller teams med bred adgang (f.eks. standarden for alle i din organisation), skal de tilladte brugerkonti og de tilladte handlinger være begrænset til det minimum, der kræves for at opfylde kravene til samarbejde og forretning.

Når en ransomware-hacker har infiltreret din lejer, forsøger de at eskalere deres rettigheder ved at kompromittere legitimationsoplysningerne for brugerkonti med bredere omfang af tilladelser på tværs af din lejer, f.eks. administratorrollekonti eller brugerkonti, der har adgang til følsomme oplysninger. 

Baseret på denne typiske adfærd for hackere er der to niveauer af vanskeligheder for angriberen:

- **Lav:** En hacker kan bruge en konto med lav tilladelse og finde dine følsomme oplysninger på grund af bred adgang i hele din lejer.
- **Højere:** En hacker kan ikke bruge en konto med lav tilladelse og finde dine følsomme oplysninger på grund af strenge tilladelser. De skal eskalere deres tilladelser ved at bestemme og derefter kompromittere legitimationsoplysningerne for en konto, der har adgang til en placering med følsomme oplysninger, men som derefter kun kan udføre et begrænset sæt handlinger.

Hvis du vil have følsomme oplysninger, skal du gøre det så svært som muligt.

Du kan sikre strenge tilladelser i din lejer ved hjælp af disse trin:

1. Gennemse tilladelserne til placering af følsomme oplysninger, så du kan [finde dine følsomme oplysninger](#locate-your-sensitive-information). 
2. Implementer strenge tilladelser til de følsomme oplysninger, mens du opfylder samarbejds- og forretningskrav, og informér de brugere, der berøres.
3. Udfør ændringsstyring for dine brugere, så fremtidige placeringer for følsomme oplysninger oprettes og vedligeholdes med strenge tilladelser.
4. Overvåg og overvåg placeringerne for følsomme oplysninger for at sikre, at der ikke gives brede tilladelser.

Se [Konfigurer sikker fildeling og samarbejde med Microsoft Teams](setup-secure-collaboration-with-teams.md) for at få en detaljeret vejledning. Et eksempel på et kommunikations- og samarbejdssted med strenge tilladelser til følsomme oplysninger er et [team med sikkerhedsisolering](/microsoft-365/solutions/secure-teams-security-isolation).

## <a name="protect-your-sensitive-information"></a>Beskyt dine følsomme oplysninger

For at beskytte dine følsomme oplysninger, hvis en ransomware-hacker får adgang til dem:

- Brug [kontrolleret mappeadgang](/windows/security/threat-protection/microsoft-defender-atp/controlled-folders) for at gøre det vanskeligere for uautoriserede programmer at ændre dataene i kontrollerede mapper.

- Brug [Microsoft Purview Information Protection](/microsoft-365/compliance/information-protection) og følsomhedsmærkater, og anvend dem på følsomme oplysninger. Følsomhedsmærkater kan konfigureres til yderligere kryptering og tilladelser med definerede brugerkonti og tilladte handlinger. En fil, der er mærket med denne type følsomhedsmærkat, som eksfiltreres fra din lejer, kan kun bruges til en brugerkonto, der er defineret i mærkaten.

- Brug Microsoft Purview [DLP (Forebyggelse af datatab)](/microsoft-365/compliance/dlp-learn-about-dlp) til at registrere, advare og blokere risikable, utilsigtede eller upassende deling af data, der indeholder personlige eller fortrolige oplysninger baseret på følsomhedsmærkater, både internt og eksternt.

- Brug [Microsoft Defender for Cloud Apps](/cloud-app-security/what-is-cloud-app-security) til at blokere downloads af følsomme oplysninger, f.eks. filer. Du kan også bruge [politikker for registrering af uregelmæssigheder i Defender for Cloud Apps](/cloud-app-security/anomaly-detection-policy#ransomware-activity) til at registrere et højt antal aktiviteter for filuploads eller filsletning.

## <a name="impact-on-users-and-change-management"></a>Indvirkning på brugere og ændringsstyring

Administrative ændringer af brede tilladelser kan medføre, at brugere nægtes adgang, eller at nogle handlinger ikke kan udføres.

For at beskytte følsomme oplysninger i din Microsoft 365 lejer skal du desuden oplære dine brugere til at:

- Opret kommunikations- og samarbejdssteder med strenge tilladelser (minimumsættet af brugerkonti til adgang og de mindst tilladte handlinger for hver konto). 
- Anvend de korrekte følsomhedsmærkater på følsomme oplysninger.
- Brug kontrolleret mappeadgang.

## <a name="resulting-configuration"></a>Resulterende konfiguration

Her er ransomware-beskyttelse for din lejer til trin 1-5.

![Ransomware-beskyttelse til din Microsoft 365 lejer efter Trin 5](../media/ransomware-protection-microsoft-365/ransomware-protection-microsoft-365-architecture-step5.png)

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
