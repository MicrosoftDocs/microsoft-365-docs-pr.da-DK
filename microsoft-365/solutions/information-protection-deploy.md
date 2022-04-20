---
title: Udrul beskyttelse af oplysninger i forbindelse med bestemmelser om beskyttelse af personlige oplysninger med Microsoft 365
ms.author: bcarter
author: brendacarter
f1.keywords:
- NOCSH
manager: laurawi
ms.date: 06/22/2020
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
- m365solution-infoprotection
- m365solution-overview
ms.custom: admindeeplinkCOMPLIANCE
description: Konfigurer beskyttelse af oplysninger i Microsoft 365 for bestemmelser om beskyttelse af personlige oplysninger, f.eks. GDPR og CCPA (California Consumer Privacy Act), herunder Microsoft Teams, SharePoint og mail.
ms.openlocfilehash: ece8483773d3e2f5cdafe90bd93e11c52e2ba838
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/19/2022
ms.locfileid: "64939010"
---
# <a name="deploy-information-protection-for-data-privacy-regulations-with-microsoft-365"></a>Udrul beskyttelse af oplysninger i forbindelse med bestemmelser om beskyttelse af personlige oplysninger med Microsoft 365

Din organisation kan være underlagt regionale regler for beskyttelse af personlige oplysninger, der kræver, at du beskytter, administrerer og giver rettigheder og kontrol over personlige oplysninger, der er gemt i it-infrastrukturen, herunder både i det lokale miljø og i cloudmiljøet. Det bedste eksempel på en forordning om beskyttelse af personlige oplysninger er EU's generelle forordning om databeskyttelse (GDPR). Hvis du ikke overholder reglerne for beskyttelse af personlige oplysninger, kan det medføre betydelige bøder.

Eksempler på datatyperne i Microsoft 365 omfatter chatsessioner i Microsoft Teams, mails i Exchange og filer i SharePoint og OneDrive. Denne løsning indeholder en vejledning i, hvordan du vurderer risici og træffer passende foranstaltninger for at beskytte personlige data i Microsoft 365. Dette omfatter identificering af personlige oplysninger, så du kan beskytte, styre og reagere på hændelser om beskyttelse af personlige oplysninger.

![Hvad er beskyttelse af oplysninger i forbindelse med bestemmelser om beskyttelse af personlige oplysninger.](../media/information-protection-deploy/information-protection-data-privacy-regulations-overview.png#lightbox)

Der gives også yderligere oplysninger om brugen af Microsoft 365 identitets-, enheds- og trusselsbeskyttelseskontroller til dine behov for beskyttelse af personlige oplysninger.

Se denne video for at få en oversigt over udrulningsprocessen.
<br>
<br>
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4NHCQ]

Disse Microsoft 365 funktioner hjælper dig med at opfylde kriterierne for beskyttelse af oplysninger.

| Funktionalitet eller funktion | Beskrivelse | Licensering |
|:-------|:-----|:-------|
| Overholdelsesstyring | Administrer aktiviteter for lovmæssig overholdelse af angivne standarder, få en samlet score for din aktuelle konfiguration af overholdelse af angivne standarder, og find anbefalinger til forbedringer. Dette er et arbejdsprocesbaseret risikovurderingsværktøj på Microsoft Purview-overholdelsesportalen. | Microsoft 365 E3 og E5 |
| Microsoft Defender for Office 365 | Beskyt dine Microsoft 365 apps og data – f.eks. mails, Office dokumenter og samarbejdsværktøjer – mod angreb. | Microsoft 365 E3 og E5 |
| Følsomhedsmærkater | Klassificer og beskyt din organisations data uden at hindre brugernes produktivitet og deres mulighed for at samarbejde. Placer mærkater med forskellige beskyttelsesniveauer på mail, filer eller websteder. | Microsoft 365 E3 og E5 |
| DLP (Data Loss Protection) | Registrer, advar og bloker risikable, utilsigtede eller upassende deling af data, der indeholder personlige oplysninger, både internt og eksternt. | Microsoft 365 E3 og E5 |
| Dataopbevaringsmærkater og -politikker | Implementer kontrolelementer til styring af oplysninger. Disse kan omfatte bestemmelse af, hvor længe data (f.eks. personlige data, der er relateret til kunder), for at overholde organisationens politikker eller dataregler. | Microsoft 365 E3 og E5 |
| Mailkryptering | Beskyt personlige data ved at sende og modtage krypterede mails mellem personer i og uden for din organisation. | Microsoft 365 E3 og E5 |
||||

## <a name="organization-of-the-guidance-in-this-solution"></a>Organisering af vejledningen i denne løsning

Denne vejledning er organiseret i afsnit for at hjælpe dig med at forstå de Microsoft 365 værktøjer, der er tilgængelige for at hjælpe dig med at overholde en eller flere bestemmelser relateret til beskyttelse af personlige oplysninger.

![Trin til implementering af databeskyttelse i forbindelse med bestemmelser om beskyttelse af personlige oplysninger.](../media/information-protection-deploy/information-protection-data-privacy-regulations-steps.png)

Hvert af disse afsnit svarer til en separat artikel i denne løsning.

> [!NOTE]
> Hvis du allerede har kendskab til dine forpligtelser til beskyttelse af personlige oplysninger og udfører i forhold til en eksisterende plan, kan du fokusere på vejledningen Forbyd, Beskyt, Bevar og Undersøg.

> [!IMPORTANT]
> Hvis du følger denne vejledning, vil du ikke nødvendigvis overholde nogen forordning om beskyttelse af personlige oplysninger, især i betragtning af det antal trin, der kræves, og som ligger uden for funktionernes kontekst. Du er ansvarlig for at sikre din overholdelse af angivne standarder og kontakte dine juridiske teams og overholdelsesteams eller for at søge vejledning og rådgivning fra tredjeparter, der er specialiserede i overholdelse af angivne standarder.

## <a name="plan-assess-data-privacy-risks-and-identify-sensitive-items"></a>Plan: Vurder risici for beskyttelse af personlige oplysninger, og identificer følsomme elementer

Vurdering af regler for beskyttelse af personlige oplysninger og risici, som din organisation er underlagt, er et vigtigt første skridt at tage, før du begynder at implementere forbedringer, herunder konfiguration af funktioner i Microsoft 365. Dette arbejde kan omfatte en overordnet parathedsvurdering eller identifikation af bestemte følsomme informationstyper, der er underlagt lovmæssige kontroller, som din organisation skal overholde.

Du kan finde flere oplysninger under [Vurder risici for beskyttelse af personlige oplysninger og identificer følsomme elementer](information-protection-deploy-assess.md).

## <a name="track-run-risk-assessments-and-check-your-compliance-score"></a>Spor: Kør risikovurderinger, og kontrollér din overholdelsesscore

Overholdelsesstyring, der er tilgængelig på <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft Purview-overholdelsesportalen</a>, giver dig en indbygget mulighed for at spore og administrere forbedringshandlinger generelt samt dem, der er relateret til flere bestemmelser om beskyttelse af personlige oplysninger, som gælder for dig.

Du kan bruge indbyggede vurderingsskabeloner, der er specifikke for hver regulering, hvor du kan spore handlingselementer for hver valgt vurderingsskabelon samt få vist specifikke lovmæssige kontroller og relatere dem til bestemte handlinger.

Du kan få flere oplysninger under [Brug Overholdelsesstyring til at administrere forbedringshandlinger](information-protection-deploy-compliance.md).

## <a name="prevent-protect-personal-data"></a>Forebyg: Beskyt personlige data

Microsoft 365 leverer identitets-, enheds- og trusselsbeskyttelsesfunktioner, som du kan bruge til at overholde lovmæssige krav til beskyttelse af personlige oplysninger.

Du kan få flere oplysninger under [Brug identitets-, enheds- og trusselsbeskyttelse til forordning om beskyttelse af personlige oplysninger](information-protection-deploy-identity-device-threat.md).

I denne artikel beskrives kort, hvad reglerne for beskyttelse af personlige oplysninger generelt kræver på disse områder, og den indeholder en liste over relaterede Microsoft 365 løsninger med links til flere oplysninger, der kan hjælpe dig med at håndtere eventuelle implementeringskrav.

## <a name="protect-information-subject-to-data-privacy-regulation"></a>Beskyt oplysninger, der er underlagt lovgivningen om beskyttelse af personlige oplysninger

Bestemmelser om beskyttelse af personlige oplysninger kræver en række kontrolelementer til beskyttelse af personlige oplysninger, som kan anvendes i dit miljø, herunder mere end 40 kontrolelementer til beskyttelse af oplysninger på tværs af blot de fire bestemmelser om beskyttelse af personlige oplysninger i vores eksempelsæt gdpr, CCPA (California Consumer Protection Act), HIPAA-HITECH (USA lov om beskyttelse af personlige oplysninger) og LGPD (Brazil Data Protection Act).

Du kan få flere oplysninger under [Beskyt oplysninger, der er underlagt regler om beskyttelse af personlige oplysninger i din organisation](information-protection-deploy-protect-information.md).

I denne artikel beskrives de primære kontrolordninger, der kan bruges til at håndtere behov for beskyttelse af oplysninger i forbindelse med beskyttelse af personlige oplysninger i din organisation.

## <a name="retain-govern-information-subject-to-data-privacy-regulation"></a>Bevar: Styr de oplysninger, der er underlagt lovgivningen om beskyttelse af personlige oplysninger

Bestemmelser om beskyttelse af personlige oplysninger kræver kontrolelementer til styring af personlige oplysninger, der kan anvendes i dit miljø, herunder mere end 24 kontrolelementer på tværs af de fire bestemmelser om beskyttelse af personlige oplysninger i vores eksempelsæt GDPR, CCPA, HIPAA-HITECH og LGPD.

Du kan få flere oplysninger under [Styr oplysninger, der er underlagt lovgivningen om beskyttelse af personlige oplysninger i din organisation](information-protection-deploy-govern.md).

Selvom reglerne for beskyttelse af personlige oplysninger kan være vage med hensyn til styring af&mdash; oplysninger, f.eks. målrettet opbevaring, sletning og arkivering&mdash;, fastlægger denne artikel de primære kontrolordninger, som du kan bruge til at håndtere behov for styring af oplysninger i forbindelse med beskyttelse af personlige oplysninger i din organisation.

## <a name="investigate-monitor-investigate-and-respond-to-data-privacy-incidents"></a>Undersøg: Overvåg, undersøg og reager på hændelser om beskyttelse af personlige oplysninger

Der er Microsoft 365 funktioner, der kan hjælpe dig med at overvåge, undersøge og reagere på hændelser om beskyttelse af personlige oplysninger i din organisation, efterhånden som du udfører relaterede funktioner.

Det kan være vigtigt at have processer, procedurer og anden dokumentation til brug af disse funktioner for at vise overholdelse af angivne standarder i de regulerende organer.

Du kan få flere oplysninger under [Overvåg og besvar hændelser om beskyttelse af personlige oplysninger i din organisation](information-protection-deploy-monitor-respond.md).

## <a name="training-for-administrators"></a>Oplæring af administratorer

Disse træningsmoduler fra Microsoft Learn kan hjælpe dig med at få mere at vide om, hvordan funktioner, der er vigtige for beskyttelse af oplysninger.


#### <a name="information-protection"></a>Beskyttelse af oplysninger

|Uddannelse:|Beskyt virksomhedsoplysninger med Microsoft 365|
|:---|:---|
|![Teams træningsikon for infobeskyttelse.](../media/protect-enterprise-information-microsoft-365.svg)|Det er mere udfordrende end nogensinde før at beskytte og beskytte din organisations oplysninger. Læringsforløbet Beskyt virksomhedsoplysninger med Microsoft 365 beskriver, hvordan du beskytter dine følsomme oplysninger mod utilsigtet overdeling eller misbrug, hvordan du finder og klassificerer data, hvordan du beskytter dem med følsomhedsmærkater, og hvordan du både overvåger og analyserer dine følsomme oplysninger for at beskytte mod tab. Dette læringsforløb kan hjælpe dig med at forberede dig på Microsoft 365 Certificeret: Sikkerhedsadministratormedarbejder og Microsoft 365 certificeret: Certificeringer fra virksomhedsadministrationseksperter..<br><br>1 t. – Learning sti – 5 moduler|

> [!div class="nextstepaction"]
> [Start >](/learn/modules/m365-security-info-overview/introduction/)

#### <a name="identity-and-access"></a>Identitet og adgang

|Uddannelse:|Beskyt identitet og adgang med Azure Active Directory|
|:---|:---|
|![Ikon for oplæring af identitet og adgang.](../media/protect-identity-and-access-with-microsoft-365.svg)|Læringsforløbet Identitet og adgang dækker de nyeste identitets- og adgangsteknologier, værktøjer til styrkelse af godkendelse og vejledning om identitetsbeskyttelse i din organisation. Microsofts adgangs- og identitetsteknologier gør det muligt for dig at sikre din organisations identitet, uanset om det er i det lokale miljø eller i cloudmiljøet, og gøre det muligt for dine brugere at arbejde sikkert fra enhver placering. Dette læringsforløb kan hjælpe dig med at forberede dig på Microsoft 365 Certificeret: Sikkerhedsadministratormedarbejder og Microsoft 365 Certificeret: Certificeringer fra virksomhedsadministrationseksperter.<br><br>2 t. 52 min. - Learning sti - 6 moduler|

> [!div class="nextstepaction"]
> [Start >](/learn/modules/m365-identity-overview/introduction/)