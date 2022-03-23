---
title: Sådan bruger du tilmelding via selvbetjening i din organisation
f1.keywords:
- NOCSH
author: cmcatee-MSFT
ms.author: cmcatee
manager: scotv
ms.reviewer: seemg, pablom
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- commerce_signup
- AdminSurgePortfolio
- okr_SMB
search.appverid: MET150
description: Få mere Microsoft 365 om selvbetjeningsbaserede tilmeldingsprogrammer og tilgængelige selvbetjeningsprogrammer som f.eks. Microsoft Power Apps, Microsoft Power Automate og Dynamics 365 til økonomi.
ms.date: 03/17/2021
ms.openlocfilehash: 67f0955a4485ea0f668b143f485b34cf2935404b
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63588297"
---
# <a name="using-self-service-sign-up-in-your-organization"></a>Sådan bruger du tilmelding via selvbetjening i din organisation

Tilmelding via selvbetjening gør det nemmere for brugerne i organisationen at tilmelde sig onlinetjenester fra Microsoft. Vi kalder tilmeldingsprocessen for "tilmelding via selvbetjening", fordi brugerne kan tilmelde sig for at bruge tjenester, der er betalt med abonnementet, eller bruge gratis tjenester uden at bede dig om at handle på deres vegne.

## <a name="how-self-service-sign-up-works"></a>Sådan fungerer tilmelding ved selvbetjening

I følgende eksempel beskrives det, hvordan selvbetjening fungerer for en skole. Den samme proces fungerer for alle organisationer, der har aktiveret selvbetjeningsprogrammer i deres lejer.

1. Studerende og fakultetsmedarbejdere har skolemailadresser, der angiver, at de er knyttet til din institution. Mailadressen, som jakob@uw.edu, kan f.eks. angive en studerende på University of Washington.
2. Studerende og [fakultetsmedarbejdere går](https://go.microsoft.com/fwlink/p/?LinkId=536628) til vores websted og bruger deres mailadresse til at tilmelde sig de tjenester, som din organisation tilbyder, f.Microsoft 365 Apps for enterprise. De kan også tilmelde sig andre gratis tjenester, som vi tilbyder.
3. Vi validerer deres mailadresse, og så kan de begynde at bruge Microsoft 365, Power BI eller andre tjenester med det samme.
4. Som virksomhedsadministrator kan du se, hvem der har tilmeldt sig et abonnement, ved at vælge abonnementet på siden  Licensering i Microsoft 365 Administration. På den måde kan du se, hvornår der er nye eller ukendt licenser til tjenester i din lejer. Hvis du vil styre, om brugerne kan tilmelde sig selvbetjeningsabonnementer, skal du bruge cmdlet'en [Set-MsolCompanySettings](/powershell/module/msonline/set-msolcompanysettings) PowerShell med **parameteren AllowAdHocSubscriptions** . Du kan finde flere oplysninger [under Hvordan styrer jeg selvbetjeningsindstillinger?](/azure/active-directory/users-groups-roles/directory-self-service-signup#how-do-i-control-self-service-settings)

## <a name="available-self-service-programs"></a>Tilgængelige selvbetjeningsprogrammer

Følgende er de aktuelt tilgængelige selvbetjeningsprogrammer. Denne liste opdateres, efterhånden som nye programmer tilføjes.

| Program <br/> | Beskrivelse <br/> | Yderligere oplysninger <br/> | Websted til tilmelding via selvbetjening <br/> |
|:-----|:-----|:-----|:-----|
|Office 365 A1**** <br/> |Enhver studerende eller lærer kan bruge en skolemailadresse til at tilmelde sig gratis Office 365 og få Office-apps til internettet, 1 TB OneDrive lagerplads i skyen og SharePoint Online til klasse-, team- og projektwebsteder.  <br/> |[Office 365 Education tekniske ofte stillede spørgsmål](/microsoft-365/education/deploy/office-365-education-self-sign-up) <br/> |[Office 365 Education](https://go.microsoft.com/fwlink/p/?linkid=140841) <br/> |
|**Office 365 A1 Plus** <br/> |Berettigede studerende og lærere kan tilmelde sig Office 365 A1 Plus, som omfatter alt det, der nævnes ovenfor, Microsoft 365 Apps for enterprise. Microsoft 365 Apps for enterprise er produktivitetssoftware, herunder Word, PowerPoint, Excel, Outlook, OneNote, Publisher, Access og Skype for Business , som er installeret på din stationære eller bærbare computer.  <br/> |[Office 365 Education tekniske ofte stillede spørgsmål](/microsoft-365/education/deploy/office-365-education-self-sign-up) <br/> |[Office 365 Education](https://go.microsoft.com/fwlink/p/?linkid=140841) <br/> |
|**Power BI** <br/> |Power BI gør det muligt for brugerne at visualisere data, dele opdagelser og samarbejde på intuitive, nye måder. <br/> Hvis din organisation allerede abonnerer, får du muligvis desuden vist licenser til "Power BI Pro prøveversion af den individuelle bruger", som giver brugerne begrænset, gratis adgang til avancerede funktioner.  <br/> |[Power BI i din organisation](./power-bi-in-your-organization.md) <br/> |[Microsoft Power BI](https://go.microsoft.com/fwlink/p/?LinkId=536629) <br/> |
|**RMS (Rights Management Services)** <br/> |RMS for enkeltpersoner er et gratis selvbetjeningsabonnement for brugere i en organisation, der har fået sendt følsomme filer, der er blevet beskyttet af Azure Rights Management (Azure RMS), men deres it-afdeling har ikke implementeret Azure Rights Management (Azure RMS) eller Active Directory Rights Management-tjenester (AD RMS).  <br/> |[RMS for enkeltpersoner og Azure Rights Management](/azure/information-protection/rms-for-individuals) <br/> |[Microsoft Rights Management-portalen](https://portal.azure.com/) , så du kan kontrollere, om du kan åbne et givet rettighedsbeskyttet dokument.  <br/> |
|**Microsoft Power Apps** <br/> |I Power Apps kan du administrere organisationsdata ved at køre en app, du har oprettet, eller som en anden har oprettet og delt med dig. Apps kører på mobilenheder som f.eks. telefoner, eller du kan køre dem i en browser ved at åbne Dynamics 365. Du kan oprette et uendeligt udvalg af apps – alt sammen uden at lære et programmeringssprog som f.eks. C#.  <br/> |[Selvbetjenings-tilmelding til Power Apps](/powerapps/maker/signup-for-powerapps) <br/> |[Microsoft Power Apps](https://go.microsoft.com/fwlink/p/?linkid=841462) <br/> |
|**Dynamics 365 til finans** <br/> |Få en komplet virksomheds- og økonomisk administrationsløsning til små og mellemstore virksomheder. Dynamics 365 til finans gør det nemmere at bestille, sælge, invoicing og rapportere – fra og med den første dag.  <br/> |[Microsoft Dynamics 365 til finans](https://go.microsoft.com/fwlink/p/?linkid=841466) <br/> |[Microsoft Dynamics 365 til finans](https://go.microsoft.com/fwlink/p/?linkid=841466) <br/> |
|**Microsoft Dynamics 365 til drift** <br/> |Forøg hastigheden på at gøre forretninger. De komplette ERP-værktøjer i Dynamics 365 for Operations giver global skalerbarhed og digital intelligens, der kan hjælpe dig med at vokse i dit tempo.  <br/> |[Microsoft Dynamics 365 til drift](https://go.microsoft.com/fwlink/p/?linkid=841467) <br/> |[Microsoft Dynamics 365 til drift](https://go.microsoft.com/fwlink/p/?linkid=841467) <br/> |
|**Microsoft AppSource** <br/> |Microsoft AppSource er en destination for software-as-a-service-virksomhedsapps, der er bygget på Microsofts skyplatform. AppSource indeholder hundredvis af apps, tilføjelsesprogrammer og indholdspakker, der udvider funktionaliteten af Microsoft-produkter som Azure, Dynamics 365, Office 365 og Power BI.  <br/> |[Microsoft AppSource](https://go.microsoft.com/fwlink/p/?linkid=841474) <br/> |[Microsoft AppSource](https://go.microsoft.com/fwlink/p/?linkid=841474) <br/> |
|**Microsoft Partner Incentives** <br/> |Microsoft Partner Network indeholder tre typer medlemskaber. Hver type indeholder et sæt fordele, der kan hjælpe din virksomhed med at vokse. Når du når dine mål, skal du deltage i programmet på det niveau, der passer til dine unikke behov for at få adgang til flere fordele og udvikle din relation til os og andre partnere i netværket.  <br/> |[Microsoft Partner Incentives](https://go.microsoft.com/fwlink/p/?linkid=841469) <br/> |[Microsoft Partner Incentives](https://go.microsoft.com/fwlink/p/?linkid=841469) <br/> |
|**Microsoft Business Center** <br/> |Microsoft Business Center er portalen for kunder, der har foretaget køb via MPSA (Microsoft Products and Services Agreement). <br/> |[Hurtig start: Tilmelde dig Microsoft Business Center](https://go.microsoft.com/fwlink/p/?linkid=841479) <br/> |[Microsoft Business Center](https://go.microsoft.com/fwlink/p/?linkid=841470) <br/> |
|**Microsoft Volume License Service Center** <br/> |Microsoft Volume License Service Center viser licenser, der er købt under Enterprise, Select, Education (Campus eller Skole), Open Value, Open License og ISV Royalty-aftaler.  <br/> |[VLSC-kurser og -ressourcer](https://www.microsoft.com/en-us/Licensing/existing-customer/vlsc-training-and-resources.aspx) <br/> |[Volume License Service Center](https://www.microsoft.com/Licensing/servicecenter/default.aspx) <br/> |
|**Minecraft Education Edition** <br/> |Ved at Minecraft en platform til læring kan undervisere udvikle sig og inspirere hver enkelt studerende til at opnå mere og fremtændre en passion for læring. Deltag i et community af undervisere, der lærer at bruge dem Minecraft at låse op for elevernes potentiale.  <br/> |[Minecraft Education Edition](https://go.microsoft.com/fwlink/p/?linkid=841480) <br/> |[Minecraft Education Edition](https://go.microsoft.com/fwlink/p/?linkid=841471) <br/> |
|**Microsoft Stream** <br/> |Upload og del videoer på tværs af organisationen for at forbedre kommunikation, deltagelse og læring.  <br/> |[Tilmeld dig &amp; Dag 0-oplevelse](https://go.microsoft.com/fwlink/p/?linkid=841472) <br/> |[Microsoft Stream](https://go.microsoft.com/fwlink/p/?linkid=841473) <br/> |
|**Power Automate** <br/> |Power Automate er et produkt, der kan hjælpe dig med at konfigurere automatiserede arbejdsprocesser mellem dine foretrukne apps og tjenester til at synkronisere filer, få meddelelser, indsamle data og meget mere.  <br/> |[Tilmeld dig, og log på for at Power Automate](/power-automate/sign-up-sign-in) <br/> |[Power Automate](https://go.microsoft.com/fwlink/p/?linkid=841465) <br/> |
|**Power Virtual Agents** <br/> |Power Virtual Agents gør det nemt for teams at oprette effektive bots ved hjælp af en guidet grafisk grænseflade uden brug af data, der er tilsigtet, eller udviklere. Power Virtual Agents adresserer mange af de største problemer med botopbygning i branchen i dag. Det fjerner mellemrummet mellem eksperter inden for emne og udviklingsteams, der opbygger botter, og den lange ventetid mellem teams, der genkender et problem og opdaterer robotten for at løse det.  <br/> |[Oplysninger om licenser og adgang](/power-virtual-agents/requirements-licensing) <br/> |[Tilmeld dig for at Power Virtual Agents](https://aka.ms/TryPVA) <br/> |
|**Azure AD B2B** <br/> |Azure Active Directory (Azure AD) til virksomhed (B2B)-samarbejde giver dig mulighed for at invitere eksterne brugere (eller "gæstebrugere") til at bruge dine betalte Azure AD-tjenester. Nogle funktioner er gratis, men for alle betalte Azure AD-funktioner kan du invitere op til fem gæstebrugere for hver licens til Azure AD-version, som du ejer for en medarbejder eller en ikke-gæstebruger i din lejer. <br/> |[Selvbetjening til tilmelding til Azure AD B2B-samarbejde](/azure/active-directory/b2b/self-service-portal) <br/> |[Azure Active Directory vejledning til B2B-samarbejdslicens](/azure/active-directory/b2b/licensing-guidance) <br/> |
