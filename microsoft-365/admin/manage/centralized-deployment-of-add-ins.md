---
title: Find ud af, om central installation af tilføjelsesprogrammer fungerer for din organisation
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
description: Find ud af, om din lejer og dine brugere opfylder kravene, så du kan bruge Central installation til at udrulle Office tilføjelsesprogrammer.
ms.openlocfilehash: 4d135e76034880e1419e296f2c201536be98b4bc
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65093762"
---
# <a name="determine-if-centralized-deployment-of-add-ins-works-for-your-organization"></a>Find ud af, om central installation af tilføjelsesprogrammer fungerer for din organisation

Centraliseret udrulning er den anbefalede og mest funktionsrige måde for de fleste kunder at udrulle Office tilføjelsesprogrammer til brugere og grupper i din organisation. Hvis du er administrator, kan du bruge denne vejledning til at afgøre, om din organisation og brugerne opfylder kravene, så du kan bruge Centraliseret installation.

Centraliseret installation giver følgende fordele:

- En administrator kan udrulle og tildele et tilføjelsesprogram direkte til en bruger, til flere brugere via en gruppe eller til alle i organisationen (se afsnittet Administratorkrav for at få flere oplysninger).
- Når det relevante Office program starter, downloades tilføjelsesprogrammet automatisk. Hvis tilføjelsesprogrammet understøtter kommandoer i tilføjelsesprogrammet, vises tilføjelsesprogrammet automatisk på båndet i det Office program.
- Tilføjelsesprogrammer vises ikke længere for brugere, hvis administratoren slår tilføjelsesprogrammet fra eller sletter det, eller hvis brugeren er fjernet fra Azure Active Directory eller fra en gruppe, som tilføjelsesprogrammet er tildelt.

Central installation understøtter tre skrivebordsplatforme Windows, Mac- og Online-Office-apps. Centraliseret installation understøtter også iOS og Android (kun Outlook mobile tilføjelsesprogrammer).

Det kan tage op til 24 timer, før et tilføjelsesprogram vises for klienten for alle brugere.

## <a name="before-you-begin"></a>Før du begynder

Central installation af tilføjelsesprogrammer kræver, at brugerne bruger Microsoft 365 Business-licenser (Business Basic, Business Standard, Business Premium), Office 365 Enterprise licenser (E1/E3/E5/F3) eller Microsoft 365 Enterprise licenser (E3/E5/F3) (og er logget på Office ved hjælp af deres organisations-id), Office 365 Education licenser (A1/A3/A5) eller Microsoft 365 Education licenser (A3/A5) og har Exchange Online og aktive Exchange Online postkasser. Abonnementsmappen skal enten være i organisationsnetværket for at Azure Active Directory.
Du kan få vist specifikke krav til Office og Exchange nedenfor, eller du kan bruge [Centraliseret udrulningskompatibilitetskontrol](#centralized-deployment-compatibility-checker).

Centraliseret installation understøtter ikke følgende:

- Tilføjelsesprogrammer, der er målrettet Office MSI-version (undtagen Outlook 2016)
- En katalogtjeneste i det lokale miljø
- Udrulning af tilføjelsesprogram i en Exchange postkasse i det lokale miljø
- Installation af tilføjelsesprogram til SharePoint
- Teams apps
- Installation af COM (Component Object Model) eller Visual Studio Tools for Office -tilføjelsesprogrammer (VSTO).
- Udrulninger af Microsoft 365, der ikke indeholder Exchange Online, f.eks. SKU'er: Microsoft 365 Apps for Business og Microsoft 365 Apps for Enterprise.

### <a name="office-requirements"></a>krav til Office

- I forbindelse med Word-, Excel- og PowerPoint-tilføjelsesprogrammer skal brugerne bruge et af følgende:
  - På en Windows enhed, version 1704 eller nyere af Microsoft 365 Business-licenser (Business Basic, Business Standard, Business Premium), Office 365 Enterprise licenser (E1/E3/E5/F3) eller Microsoft 365 Enterprise licenser (E3/E5/F3).
  - På en Mac, version 15.34 eller nyere.

- Brugerne skal bruge en af følgende fremgangsmåder til Outlook:
  - Version 1701 eller nyere af Microsoft 365 Business-licenser (Business Basic, Business Standard, Business Premium), Office 365 Enterprise licenser (E1/E3/E5/F3) eller Microsoft 365 Enterprise licenser (E3/E5/F3).
  - Version 1808 eller nyere af Office Professional Plus 2019 eller Office Standard 2019.
  - Version 16.0.4494.1000 eller nyere af Office Professional Plus 2016 (MSI) eller Office Standard 2016 (MSI)\*
  - Version 15.0.4937.1000 eller nyere af Office Professional Plus 2013 (MSI) eller Office Standard 2013 (MSI)\*
  - Version 16.0.9318.1000 eller nyere af Office 2016 til Mac
- Version 2.75.0 eller nyere af Outlook mobil til iOS
- Version 2.2.145 eller nyere af Outlook mobil til Android

    *MSI-versioner af Outlook viser tilføjelsesprogrammer, der er installeret af administratorer, på det relevante Outlook bånd og ikke i afsnittet "Mine tilføjelsesprogrammer".

### <a name="exchange-online-requirements"></a>krav til Exchange Online

Microsoft Exchange gemmer tilføjelsesprogrammets manifester i din organisations lejer. Den administrator, der installerer tilføjelsesprogrammer, og de brugere, der modtager disse tilføjelsesprogrammer, skal være på en version af Exchange Online, der understøtter OAuth-godkendelse.

Kontakt organisationens Exchange administrator for at finde ud af, hvilken konfiguration der er i brug. OAuth-forbindelse pr. bruger kan bekræftes ved hjælp af PowerShell-cmdlet'en [Test-OAuthConnectivity](/powershell/module/exchange/test-oauthconnectivity) .

### <a name="admin-requirements"></a>Administratorkrav

Hvis du vil installere et tilføjelsesprogram via central installation, skal du enten være global administrator eller Exchange administrator i organisationen.

> [!NOTE]
> En Exchange administrator kan installere et tilføjelsesprogram, hvis rollen **Programadministrator** tilføjes, eller hvis egenskaben **App Registrations** er angivet til true i Azure Active Directory Administration som vist på følgende billede:
>
> ![Billede](https://user-images.githubusercontent.com/89943918/144516704-8874a10d-b540-41f3-ae9d-c07a8d7e143f.png)

### <a name="centralized-deployment-compatibility-checker"></a>Centraliseret kontrol af udrulningskompatibilitet

Ved hjælp af Centraliseret udrulningskompatibilitetskontrol kan du kontrollere, om brugerne i din lejer er konfigureret til at bruge Centraliseret installation til Word, Excel og PowerPoint. Kompatibilitetskontrol er ikke påkrævet for Outlook support. Download [kompatibilitetskontrollen](https://aka.ms/officeaddindeploymentorgcompatibilitychecker).

#### <a name="run-the-compatibility-checker"></a>Kør kompatibilitetskontrol

1. Start et vindue med administratorrettigheder PowerShell.exe.

2. Kør følgende kommando:

   ```powershell
   Import-Module O365CompatibilityChecker
   ```

3. Kør kommandoen **Invoke-CompatibilityCheck** :

   ```powershell
   Invoke-CompatibilityCheck
   ```

   Denne kommando beder dig om _TenantDomain_ (f.eks. _TailspinToysIncorporated.onmicrosoft.com_) og _TenantAdmin-legitimationsoplysninger_ (brug dine globale administratorlegitimationsoplysninger) og anmoder derefter om samtykke.

   > [!NOTE]
   > Afhængigt af antallet af brugere i din lejer kan kontrollen fuldføres på få minutter eller timer.

Når værktøjet er færdigt, opretter det en outputfil i kommasepareret (.csv)-format. Filen gemmes som standard **i den aktuelle arbejdsmappe** . Outputfilen indeholder følgende oplysninger:

- Brugernavn
- Bruger-id (brugerens mailadresse)
- Centraliseret installation klar – hvis de resterende elementer er sande
- Office plan – Planen for Office, de er licenseret til
- Office aktiveret – Hvis de har aktiveret Office
- Understøttet postkasse – Hvis de er i en OAuth-aktiveret postkasse

> [!NOTE]
> Multifactor-godkendelse understøttes ikke, når powershell-modulet til central installation bruges. Modulet fungerer kun sammen med basisgodkendelse.

## <a name="user-and-group-assignments"></a>Bruger- og gruppetildelinger

Funktionen Centraliseret installation understøtter i øjeblikket de fleste grupper, der understøttes af Azure Active Directory, herunder Microsoft 365 grupper, distributionslister og sikkerhedsgrupper.

> [!NOTE]
> Ikke-mailaktiverede sikkerhedsgrupper understøttes ikke i øjeblikket.

Central installation understøtter tildelinger til individuelle brugere, grupper og alle i lejeren. Central installation understøtter brugere i grupper på øverste niveau eller grupper uden overordnede grupper, men ikke brugere i indlejrede grupper eller grupper, der har overordnede grupper.

Se følgende eksempel, hvor Sandra, Sheila og gruppen Salgsafdeling er tildelt til et tilføjelsesprogram. Da salgsafdelingen for vestkysten er en indlejret gruppe, er Bert og Fred ikke tildelt et tilføjelsesprogram.

![MicrosoftTeams-billede](../../media/683094bb-1160-4cce-810d-26ef7264c592.png)

### <a name="find-out-if-a-group-contains-nested-groups"></a>Find ud af, om en gruppe indeholder indlejrede grupper

Den nemmeste måde at registrere, om en gruppe indeholder indlejrede grupper, er ved at få vist gruppens visitkort i Outlook. Hvis du angiver gruppenavnet i feltet **Til** i en mail og derefter vælger gruppenavnet, når det fortolkes, vises det, hvis det indeholder brugere eller indlejrede grupper. I eksemplet nedenfor vises ingen brugere og kun to undergrupper under fanen **Medlemmer** på visitkortet Outlook for testgruppen.

![Fanen Medlemmer på Outlook visitkort.](../../media/d9db88c4-d752-426c-a480-b11a5b3adcd6.png)

Du kan udføre den modsatte forespørgsel ved at løse problemet for gruppen for at se, om den er medlem af en gruppe. I eksemplet nedenfor kan du se under fanen **Medlemskab** på Outlook visitkort, at Undergruppe 1 er medlem af testgruppen.

![Fanen Medlemskab på Outlook visitkort.](../../media/a9f9b6ab-9c19-4822-9e3d-414ca068c42f.png)

Du kan også bruge API'en Azure Active Directory Graph til at køre forespørgsler for at finde listen over grupper i en gruppe. Du kan få flere oplysninger under [Handlinger på grupper| Graph API-reference](/previous-versions/azure/ad/graph/api/groups-operations).

### <a name="contacting-microsoft-for-support"></a>Kontakt Microsoft for at få support

Hvis du eller dine brugere oplever problemer med at indlæse tilføjelsesprogrammet, mens du bruger Office apps til internettet (Word, Excel osv.), som blev installeret centralt, skal du muligvis kontakte Microsoft Support ([få mere at vide](../../business-video/get-help-support.md). Angiv følgende oplysninger om dit Microsoft 365 miljø i supportanmodningen.

|Platform|Fejlfindingsoplysninger|
|---|---|
|Office|Charles/Fiddler-logge <br/> Lejer-id ([få mere at vide](/onedrive/find-your-office-365-tenant-id)) <br/> CorrelationID. Få vist kilden til en af Office-siderne, og søg efter værdien Korrelations-id, og send den til support:  <br/>`<input name=" **wdCorrelationId**" type="hidden" value=" **{BC17079E-505F-3000-C177-26A8E27EB623}**">` <br/> `<input name="user_id" type="hidden" value="1003bffd96933623"></form>`|
|Avancerede klienter (Windows, Mac)|Charles/Fiddler-logge <br/> Opret numre på klientappen (helst som et skærmbillede fra **fil/konto**)|

## <a name="related-content"></a>Relateret indhold

[Installér tilføjelsesprogrammer i Administration](../manage/manage-deployment-of-add-ins.md) (artikel)\
[Administrer tilføjelsesprogrammer i Administration](manage-addins-in-the-admin-center.md) (artikel)\
[Ofte stillede spørgsmål om central installation](../manage/centralized-deployment-faq.yml) (artikel)\
[Opgrader dine Microsoft 365 for erhvervsbrugere til den nyeste Office klient](../setup/upgrade-users-to-latest-office-client.md) (artikel)
