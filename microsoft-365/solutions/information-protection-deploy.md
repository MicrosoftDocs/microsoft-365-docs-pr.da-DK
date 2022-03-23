---
title: Installér beskyttelse af oplysninger for regler om beskyttelse af data med Microsoft 365
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
description: Konfigurer beskyttelse af oplysninger i Microsoft 365 for bestemmelser om beskyttelse af data som GDPR og California Consumer Privacy Act (CCPA), herunder Microsoft Teams, SharePoint og mail.
ms.openlocfilehash: 92314529cf6ca3ec318b181eb367bab81b9b81a0
ms.sourcegitcommit: ab5368888876d8796da7640553fc8426d040f470
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/04/2021
ms.locfileid: "63588651"
---
# <a name="deploy-information-protection-for-data-privacy-regulations-with-microsoft-365"></a>Installér beskyttelse af oplysninger for regler om beskyttelse af data med Microsoft 365

Din organisation kan være underlagt regionale bestemmelser om beskyttelse af data, der kræver, at du beskytter, administrerer og giver rettigheder og kontrol over personlige oplysninger, der er gemt i din it-infrastruktur, herunder både lokalt og i skyen. Det bedste eksempel på en forordning om beskyttelse af personlige oplysninger er EU's generelle forordning om databeskyttelse (GDPR). Manglende overholdelse af regler om beskyttelse af data kan give betydelige fines.

Eksempler på datatyper i Microsoft 365 omfatter chatsessioner i Microsoft Teams, mails i Exchange og filer i SharePoint og OneDrive. Denne løsning giver vejledning i, hvordan du vurderer risici og tager de nødvendige skridt til at beskytte personlige data Microsoft 365. Dette omfatter identificering af personlige oplysninger, så du kan beskytte, styre og reagere på hændelser i forbindelse med beskyttelse af personlige oplysninger for data.

![Hvad er beskyttelse af oplysninger i forbindelse med bestemmelser om beskyttelse af personlige oplysninger.](../media/information-protection-deploy/information-protection-data-privacy-regulations-overview.png#lightbox)

Der findes også yderligere oplysninger om brug af Microsoft 365, enhed og kontrolelementer til trusselsbeskyttelse til dine behov for beskyttelse af personlige oplysninger.

Se denne video for at få et overblik over installationsprocessen.
<br>
<br>
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4NHCQ]

Disse Microsoft 365 funktioner hjælper dig med at opfylde kriterierne for beskyttelse af oplysninger.

| Funktionalitet eller funktion | Beskrivelse | Licensering |
|:-------|:-----|:-------|
| Overholdelsesstyring | Administrer aktiviteter til overholdelse af lovgivning, få et overordnet resultat af din aktuelle overholdelseskonfiguration, og find anbefalinger til forbedringer. Dette er et arbejdsprocesbaseret værktøj til risikovurdering i Microsoft 365 Overholdelsescenter. | Microsoft 365 E3 og E5 |
| Microsoft Defender til Office 365 | Beskyt dine Microsoft 365 apps og data – f.eks. mails, Office dokumenter og samarbejdsværktøjer – mod angreb. | Microsoft 365 E3 og E5 |
| Følsomhedsmærkater | Klassificer og beskyt din organisations data uden at begrænse brugernes produktivitet og deres mulighed for at samarbejde. Placer navne med forskellige niveauer af beskyttelse på mail, filer eller websteder. | Microsoft 365 E3 og E5 |
| DLP (Data Loss Protection) | Registrer, advar og bloker risikabelt, utilsigtet eller upassende deling af data, der indeholder personlige oplysninger, både internt og eksternt. | Microsoft 365 E3 og E5 |
| Dataopbevaringsmærkater og -politikker | Implementer kontrolelementer til informationsstyring. Disse kan omfatte fastlæggelse af, hvor lang tid data (f.eks. personlige data relateret til kunder) skal overholde organisationens politikker eller databestemmelser. | Microsoft 365 E3 og E5 |
| Mailkryptering | Beskyt personlige data ved at sende og modtage krypterede mails mellem personer i og uden for organisationen. | Microsoft 365 E3 og E5 |
||||

## <a name="organization-of-the-guidance-in-this-solution"></a>Organisering af vejledningen i denne løsning

For at hjælpe dig med at forstå Microsoft 365, der kan hjælpe dig med at overholde en eller flere regler, der er relateret til beskyttelse af personlige oplysninger, er denne vejledning organiseret i sektioner.

![Trin til at implementere beskyttelse af oplysninger i forbindelse med bestemmelser om beskyttelse af data.](../media/information-protection-deploy/information-protection-data-privacy-regulations-steps.png)

Hver af disse sektioner svarer til en separat artikel i denne løsning.

> [!NOTE]
> Hvis du allerede kender dine forpligtelser til beskyttelse af data og udfører i forhold til en eksisterende plan, kan det være en ide at fokusere på vejledningen Forebyd, Beskyt, Behold og Undersøg.

> [!IMPORTANT]
> Hvis du følger denne vejledning, vil du ikke nødvendigvis overholde nogen bestemmelser om beskyttelse af personlige oplysninger for data, især i betragtning af antallet af nødvendige trin, der er uden for funktionernes kontekst. Du er ansvarlig for at sikre din overholdelse og for at rådføre dig med dine juridiske teams og overholdelsesteams eller for at få vejledning og rådgivning fra tredjeparter, som er specialiserede i overholdelse af regler og standarder.

## <a name="plan-assess-data-privacy-risks-and-identify-sensitive-items"></a>Plan: Vurder risici i forbindelse med beskyttelse af data og identificer følsomme elementer

Vurdering af regler for beskyttelse af personlige oplysninger og risici, som din organisation er underlagt, er det vigtigste første skridt, før du går i gang med at implementere forbedringer, herunder konfiguration af funktioner i Microsoft 365. Dette arbejde kan omfatte en generel vurdering af parathed eller identifikation af bestemte typer af følsomme oplysninger, der er underlagt lovmæssige kontroller, som organisationen skal overholde.

Få mere at vide under [Vurder risici i forbindelse med beskyttelse af data og identificer følsomme elementer](information-protection-deploy-assess.md).

## <a name="track-run-risk-assessments-and-check-your-compliance-score"></a>Spor: Kør risikovurderinger, og kontrollér din vurdering af overholdelse af regler og standarder

Overholdelsesstyring, som findes i <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft 365 Overholdelsescenter</a>, giver dig en indbygget mulighed for at registrere og administrere overordnede forbedringshandlinger samt dem, der er relateret til flere regler om beskyttelse af personlige oplysninger, der gælder for dig.

Du kan bruge indbyggede bedømmelsesskabeloner, der er specifikke for hver lovgivning, hvor du kan spore handlingspunkter for hver valgte bedømmelsesskabelon samt få vist bestemte lovgivningsmæssige kontrolelementer og relatere dem til bestemte handlinger.

Få mere at vide under [Brug Overholdelsesstyring til at administrere forbedringshandlinger](information-protection-deploy-compliance.md).

## <a name="prevent-protect-personal-data"></a>Undgå: Beskyt personlige data

Microsoft 365 indeholder funktioner til identitet, enhed og trusselsbeskyttelse, som du kan bruge til at overholde lovgivning om overholdelse af lovgivning om beskyttelse af personlige oplysninger.

Få mere at vide under [Brug af identitet, enhed og trusselsbeskyttelse til databeskyttelse.](information-protection-deploy-identity-device-threat.md)

I denne artikel beskrives kort, hvad disse bestemmelser om beskyttelse af personlige oplysninger generelt kræver på disse områder, og den indeholder en liste over relaterede Microsoft 365-løsninger med links til flere oplysninger, der kan hjælpe dig med at tage hånd om eventuelle implementeringskrav.

## <a name="protect-information-subject-to-data-privacy-regulation"></a>Beskytte oplysninger i henhold til persondataforordningen

Bestemmelser om beskyttelse af datas personlige oplysninger dikterer en række kontrolelementer til beskyttelse af personlige oplysninger, der kan anvendes i dit miljø, herunder mere end 40 kontrolelementer til beskyttelse af oplysninger på tværs af kun de fire bestemmelser om beskyttelse af personlige oplysninger i vores eksempelsæt af GDPR, California Consumer Protection Act (CCPA), HIPAA-HITECH (United States Health Care Privacy Act) og LGPD (Brazil Data Protection Act).

Du kan få mere at vide [under Beskyt oplysninger, der er underlagt lovgivningen om beskyttelse af data i din organisation](information-protection-deploy-protect-information.md).

Denne artikel omhandler de primære kontrolskemaer, der kan bruges til at imødekomme behov for beskyttelse af oplysninger i forbindelse med beskyttelse af data i organisationen.

## <a name="retain-govern-information-subject-to-data-privacy-regulation"></a>Behold: Regulerer oplysninger, der er underlagt persondataforordningen

Bestemmelser om beskyttelse af personlige oplysninger for data kræver styring af personlige oplysninger, der kan anvendes i dit miljø, herunder mere end 24 kontrolelementer på tværs af de fire bestemmelser om beskyttelse af personlige oplysninger i vores eksempelsæt af GDPR, CCPA, HIPAA-HITECH og LGPD.

Få mere at vide under [Regulerer oplysninger, der er underlagt lovgivningen om beskyttelse af personlige oplysninger i din organisation](information-protection-deploy-govern.md).

&mdash;Selvom reglerne om beskyttelse af datas personlige oplysninger kan være uklare angående styring af oplysninger såsom effektiv opbevaring, sletning og arkiveringDette&mdash; artikel indeholder de primære kontrolskemaer, som du kan bruge til at håndtere behov for styring af oplysninger i forbindelse med beskyttelse af personlige oplysninger i organisationen.

## <a name="investigate-monitor-investigate-and-respond-to-data-privacy-incidents"></a>Undersøg: Overvåge, undersøge og reagere på hændelser i forbindelse med beskyttelse af data

Der findes Microsoft 365, der kan hjælpe dig med at overvåge, undersøge og reagere på hændelser i forbindelse med beskyttelse af personlige oplysninger for data i organisationen, når du driftsiserer relaterede funktioner.

Det kan være vigtigt at have processer, procedurer og anden dokumentation til brug af disse funktioner for at demonstrere overholdelse af lovbestemmelser.

Du kan få mere at vide [under Overvåge og reagere på hændelser i forbindelse med beskyttelse af data i organisationen](information-protection-deploy-monitor-respond.md).

## <a name="training-for-administrators"></a>Kurser til administratorer

Disse kursusmoduler fra Microsoft Learn kan hjælpe dig med at få mere at vide om, hvordan funktioner, der er vigtige for beskyttelse af oplysninger.


#### <a name="information-protection"></a>Beskyttelse af oplysninger

|Kursus:|Beskyt virksomhedsoplysninger med Microsoft 365|
|:---|:---|
|![Teams for uddannelse i beskyttelse af oplysninger.](../media/protect-enterprise-information-microsoft-365.svg)|At beskytte og sikre din organisations oplysninger er mere udfordrende end nogensinde før. I læringsstien Beskyt virksomhedsoplysninger med Microsoft 365 beskrives det, hvordan du beskytter dine følsomme oplysninger mod utilsigtet overdeling eller misbrug, hvordan du finder og klassificerer data, hvordan du beskytter dem med følsomhedsmærkater, og hvordan du både overvåger og analyserer dine følsomme oplysninger for at beskytte dig mod tab. Denne læringssti kan hjælpe dig med at forberede dig til Microsoft 365 certificeret: Security Administrator Associate og Microsoft 365 Certified: Enterprise Administration Expert-certificeringer.<br><br>1 timer - Learning Sti - 5 moduler|

> [!div class="nextstepaction"]
> [Start >](/learn/modules/m365-security-info-overview/introduction/)

#### <a name="identity-and-access"></a>Identitet og adgang

|Kursus:|Beskyt identitet og adgang med Azure Active Directory|
|:---|:---|
|![Ikonet Identitets- og adgangskursus.](../media/protect-identity-and-access-with-microsoft-365.svg)|Identitets- og Access-læringsstien dækker de nyeste identitets- og adgangsteknologier, værktøjer til godkendelse med henblik på godkendelse og vejledning til identitetsbeskyttelse inden for organisationen. Microsofts adgangs- og identitetsteknologier giver dig mulighed for at sikre din organisations identitet, uanset om den er lokal eller i skyen, og give dine brugere mulighed for at arbejde sikkert fra et hvilket som helst sted. Denne læringssti kan hjælpe dig med at forberede dig til Microsoft 365 certificeret: Security Administrator Associate og Microsoft 365 Certified: Enterprise Administration Expert-certificeringer.<br><br>2 timer 52 min - Learning Sti - 6 moduler|

> [!div class="nextstepaction"]
> [Start >](/learn/modules/m365-identity-overview/introduction/)