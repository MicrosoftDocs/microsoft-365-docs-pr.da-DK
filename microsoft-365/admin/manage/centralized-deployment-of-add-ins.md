---
title: Afgør, om Centraliseret udrulning af tilføjelses ins fungerer for din organisation
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: b4527d49-4073-4b43-8274-31b7a3166f92
description: Fastsæt, om din lejer og brugere opfylder kravene, så du kan bruge Centraliseret udrulning til Office-tilføjelsesprogrammet.
ms.openlocfilehash: 856e48db79627e0e736c05fe0062680017e24418
ms.sourcegitcommit: bcbcbd4ddc72ad2fed629619d23fac5827d072bf
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/29/2022
ms.locfileid: "64506961"
---
# <a name="determine-if-centralized-deployment-of-add-ins-works-for-your-organization"></a>Afgør, om Centraliseret udrulning af tilføjelses ins fungerer for din organisation

Centraliseret udrulning er den mest funktionsrige måde, hvorpå de fleste kunder kan installere Office tilføjelsesprogrammet til brugere og grupper i organisationen. Hvis du er administrator, kan du bruge denne vejledning til at afgøre, om din organisation og brugere opfylder kravene, så du kan bruge Centraliseret udrulning.

Centraliseret udrulning giver følgende fordele:

- En administrator kan installere og tildele et tilføjelsesprogrammet direkte til en bruger, til flere brugere via en gruppe eller til alle i organisationen (se afsnittet Administratorkrav for at få flere oplysninger).
- Når det Office program startes, downloades tilføjelsesprogrammet automatisk. Hvis tilføjelsesprogrammet understøtter tilføjelsesprogramkommandoer, vises tilføjelsesprogrammet automatisk på båndet i det Office program.
- Tilføjelsesprogrammet vises ikke længere for brugere, hvis administratoren deaktiverer eller sletter tilføjelsesprogrammet, eller hvis brugeren fjernes fra Azure Active Directory eller fra en gruppe, som tilføjelsesprogrammet er tildelt til.

Centraliseret udrulning understøtter tre Windows-, Mac- og online-Office apps. Centraliseret udrulning understøtter også iOS og Android (Outlook kun for mobile tilføjelser).

Det kan tage op til 24 timer, før et tilføjelsesprogrammet vises for klienten for alle brugere.

## <a name="before-you-begin"></a>Før du begynder

Centraliseret udrulning af tilføjelsesprogrammet kræver, at brugerne bruger Microsoft 365 Business-licenser (Business Basic, Business Standard, Business Premium), Office 365 Enterprise-licenser (E1/E3/E5/F3) eller Microsoft 365 Enterprise-licenser (E3/E5/F3) (og er logget på Office bruger deres organisations-id), Office 365 Education licenser (A1/A3/A5) eller Microsoft 365 Education-licenser (A3/A5) og har Exchange Online og aktive Exchange Online postkasser. Din abonnementsmappe skal enten være i eller i organisationsnetværk for at Azure Active Directory.
Du kan se specifikke krav til Office og Exchange nedenfor, eller du kan bruge [kompatibilitetskontrollen til Centraliseret udrulning](#centralized-deployment-compatibility-checker).

Centraliseret udrulning understøtter ikke følgende:

- Tilføjelser, der er rettet mod Office MSI-version (undtagen Outlook 2016)
- En lokal katalogtjeneste
- Installation af tilføjelsesprogrammet til Exchange lokale postkasse
- Installation af tilføjelsesprogrammet til SharePoint
- Teams apps
- Installation af Component Object Model (COM) eller Visual Studio Tools Office til tilføjelsesprogrammet VSTO (Component Object Model).
- Installationer af Microsoft 365, der ikke Exchange Online, f.eks. SKU'er: Microsoft 365 Apps til virksomheder og Microsoft 365 Apps til virksomheder.

### <a name="office-requirements"></a>Office krav

- For Word Excel og PowerPoint-tilføjelsesprogrammet skal dine brugere benytte en af følgende fremgangsmåder:
  - På en Windows-enhed version 1704 eller nyere af Microsoft 365 Business-licenser (Business Basic, Business Standard, Business Premium), Office 365 Enterprise-licenser (E1/E3/E5/F3) eller Microsoft 365 Enterprise-licenser (E3/E5/F3).
  - På en Mac, version 15.34 eller nyere.

- For Outlook skal dine brugere bruge en af følgende:
  - Version 1701 eller nyere af Microsoft 365 Business-licenser (Business Basic, Business Standard, Business Premium), Office 365 Enterprise-licenser (E1/E3/E5/F3) eller Microsoft 365 Enterprise licenser (E3/E5/F3).
  - Version 1808 eller nyere af Office Professional Plus 2019 eller Office Standard 2019.
  - Version 16.0.4494.1000 eller nyere af Office Professional Plus 2016 (MSI) eller Office Standard 2016 (MSI)\*
  - Version 15.0.4937.1000 eller nyere af Office Professional Plus 2013 (MSI) eller Office Standard 2013 (MSI)\*
  - Version 16.0.9318.1000 eller nyere af Office 2016 til Mac
- Version 2.75.0 eller nyere af Outlook mobil til iOS
- Version 2.2.145 eller nyere af Outlook mobile til Android

    *MSI-versioner af Outlook viser tilføjelsesprogrammet administratorinstalleret på det relevante Outlook-bånd og ikke i sektionen "Mine tilføjelsesprogrammet".

### <a name="exchange-online-requirements"></a>Exchange Online krav

Microsoft Exchange gemmer manifester for tilføjelsesprogrammet i din organisations lejer. Administratoren, der udruller tilføjelsesprogrammet, og de brugere, der modtager disse tilføjelses ins, skal bruge en version af Exchange Online der understøtter OAuth-godkendelse.

Kontakt din organisations administrator Exchange at finde ud af, hvilken konfiguration der er i brug. OAuth-forbindelse pr. bruger kan bekræftes ved hjælp af [Cmdlet'en Test-OAuthConnectivity](/powershell/module/exchange/test-oauthconnectivity) PowerShell.

### <a name="admin-requirements"></a>Administratorkrav

For at kunne installere et tilføjelsesprogrammet via Centraliseret udrulning skal du enten være global administrator eller Exchange administrator i organisationen.

> [!NOTE]
> En Exchange administrator kan installere et tilføjelsesprogram, hvis programadministratorrollen er tilføjet, eller hvis egenskaben **Appregistreringer** er angivet til sand i Azure Active Directory Administration som vist på følgende billede:
>
> ![billede](https://user-images.githubusercontent.com/89943918/144516704-8874a10d-b540-41f3-ae9d-c07a8d7e143f.png)

### <a name="centralized-deployment-compatibility-checker"></a>Kompatibilitetskontrol for Centraliseret udrulning

Ved hjælp af kompatibilitetskontrollen til Centraliseret udrulning kan du kontrollere, om brugerne i din lejer er konfigureret til at bruge Centraliseret udrulning af Word, Excel og PowerPoint. Kompatibilitetskontrol er ikke påkrævet for at Outlook support. Download [kompatibilitetskontrollen](https://aka.ms/officeaddindeploymentorgcompatibilitychecker).

#### <a name="run-the-compatibility-checker"></a>Kør kompatibilitetskontrollen

1. Start et hævet PowerShell.exe vindue.

2. Kør følgende kommando:

   ```powershell
   Import-Module O365CompatibilityChecker
   ```

3. Kør kommandoen **Invoke-CompatibilityCheck** :

   ```powershell
   Invoke-CompatibilityCheck
   ```

   Denne kommando beder dig om _TenantDomain_ (f.eks _. TailspinToysIncorporated.onmicrosoft.com_) og _TenantAdmin-legitimationsoplysninger_ (brug dine globale administratoroplysninger), og anmoder derefter om samtykke.

   > [!NOTE]
   > Afhængigt af antallet af brugere i din lejer kan kontrol fuldføres i minutter eller timer.

Når værktøjet er færdigt med at køre, frembringes en outputfil i kommasepareret format (.csv) format. Filen gemmes som standard **i den aktuelle arbejdsmappe** . Outputfilen indeholder følgende oplysninger:

- Brugernavn
- Bruger-id (brugerens mailadresse)
- Centraliseret udrulning klar – hvis de resterende elementer er sande
- Office plan – Planen for de Office, de har licens til
- Office aktiveret – Hvis de har aktiveret Office
- Understøttet postkasse – hvis de er på en OAuth-aktiveret postkasse

> [!NOTE]
> Multifaktorgodkendelse understøttes ikke, når du bruger PowerShell-modulet til centralinstallation. Modulet virker kun med grundlæggende godkendelse.

## <a name="user-and-group-assignments"></a>Bruger- og gruppetildelinger

Funktionen Centraliseret udrulning understøtter i øjeblikket størstedelen af grupper, der understøttes Azure Active Directory, herunder Microsoft 365 grupper, distributionslister og sikkerhedsgrupper.

> [!NOTE]
> Ikke-mailaktiverede sikkerhedsgrupper understøttes ikke i øjeblikket.

Centraliseret udrulning understøtter tildelinger til individuelle brugere, grupper og alle i lejeren. Centraliseret udrulning understøtter brugere i grupper på øverste niveau eller grupper uden overordnede grupper, men ikke brugere i indlejrede grupper eller grupper, der har overordnede grupper.

I følgende eksempel er Sandra, Sheila og gruppen Salgsafdeling tildelt et tilføjelsesprogrammet. West Coast Sales Department er en indlejret gruppe, og derfor er Bert og Fred ikke tildelt et tilføjelsesprogrammet.

![MicrosoftTeams-image](../../media/683094bb-1160-4cce-810d-26ef7264c592.png)

### <a name="find-out-if-a-group-contains-nested-groups"></a>Find ud af, om en gruppe indeholder indlejrede grupper

Den nemmeste måde at registrere, om en gruppe indeholder indlejrede grupper, er at få vist gruppens visitkort i Outlook. Hvis du angiver gruppenavnet i feltet Til  i en mail og derefter vælger gruppenavnet, når det findes, får du vist, om den indeholder brugere eller indlejrede grupper. I eksemplet nedenfor viser fanen **Medlemmer** på Outlook for testgruppen ingen brugere og kun to undergrupper.

![Fanen Medlemmer på Outlook visitkort.](../../media/d9db88c4-d752-426c-a480-b11a5b3adcd6.png)

Du kan udføre den modsatte forespørgsel ved at finde gruppen for at se, om den er medlem af en gruppe. I eksemplet nedenfor kan du under fanen Medlemskab på visitkortet Outlook se, at Undergruppe 1 er medlem af testgruppen.

![Fanen Medlemskab på Outlook visitkort.](../../media/a9f9b6ab-9c19-4822-9e3d-414ca068c42f.png)

Alternativt kan du bruge API'en Azure Active Directory Graph til at køre forespørgsler for at finde listen over grupper inden for en gruppe. Du kan finde flere oplysninger [under Handlinger for grupper| Graph API-reference](/previous-versions/azure/ad/graph/api/groups-operations).

### <a name="contacting-microsoft-for-support"></a>Kontakt Microsoft for at få support

Hvis du eller dine brugere oplever problemer med at indlæse tilføjelsesprogrammet under brug af Office-apps til internettet (Word, Excel osv.), som er blevet installeret centralt, skal du muligvis kontakte Microsoft [Support (se](../../business-video/get-help-support.md) hvordan. Angiv følgende oplysninger om dit Microsoft 365 i supportanmodningen.

|Platform|Fejlfindingsoplysninger|
|---|---|
|Office|Charles/Fiddler-logge <br/> Lejer-id ([se hvordan](/onedrive/find-your-office-365-tenant-id)) <br/> Korrelations-id. Få vist kilden til en af Office-siderne, og se efter værdien for Korrelations-id, og send den til support:  <br/>`<input name=" **wdCorrelationId**" type="hidden" value=" **{BC17079E-505F-3000-C177-26A8E27EB623}**">` <br/> `<input name="user_id" type="hidden" value="1003bffd96933623"></form>`|
|Avancerede klienter (Windows, Mac)|Charles/Fiddler-logge <br/> Buildnumre af klientappen (helst som et skærmbillede fra **fil/konto**)|

## <a name="related-content"></a>Relateret indhold

[Installér tilføjelser i Administration (artikel](../manage/manage-deployment-of-add-ins.md) )\
[Administrer tilføjelser i Administration (artikel](manage-addins-in-the-admin-center.md) )\
[Ofte stillede spørgsmål om Centraliseret](../manage/centralized-deployment-faq.yml) udrulning (artikel)\
[Opgrader Microsoft 365 til virksomhedsbrugere til den nyeste Office klient](../setup/upgrade-users-to-latest-office-client.md) (artikel)
