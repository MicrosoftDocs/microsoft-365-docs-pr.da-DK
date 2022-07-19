---
title: Prøv at evaluere Defender for Office 365
description: Få mere at vide om, hvordan du evaluerer og prøver funktionerne i Microsoft Defender for Office 365, uden at det påvirker dit eksisterende mailflow.
keywords: ''
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: article
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
ms.custom: ''
ms.technology: mdo
ms.prod: m365-security
ROBOTS: ''
ms.openlocfilehash: ad8c15ef0b5dc56d2df8455341f8bf5e4e6efd94
ms.sourcegitcommit: c6f1486617b39565bfd8f662ee6ad65a9cefd3e3
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/29/2022
ms.locfileid: "66858870"
---
# <a name="try-microsoft-defender-for-office-365"></a>Prøv Microsoft Defender for Office 365

Den samlede **prøveversionsportal** på Microsoft 365 Defender-portalen indeholder et enkelt indgangspunkt for de tidligere separate prøveversions- og evalueringsoplevelser for Microsoft Defender for Office 365. Hensigten er at give dig mulighed for at prøve funktionerne i Defender for Office 365 Plan 2 i 90 dage, før du fuldt ud forpligter dig til det. Men der er forskelle i evalueringsoplevelsen baseret på din Microsoft 365-organisations karakter:

- Du har allerede Microsoft 365-postkasser, men du bruger i øjeblikket en tredjepartstjeneste eller -enhed til mailbeskyttelse. Mails fra internettet flyder via beskyttelsestjeneste, før de leveres til din Microsoft 365-organisation. Microsoft 365-beskyttelse er så lav som muligt (den er aldrig helt slukket, for eksempel gennemtvinges malwarebeskyttelse altid).

  ![Mail flyder fra internettet via beskyttelsestjeneste fra tredjepart eller enhed, før de leveres til Microsoft 365.](../../media/mdo-migration-before.png)

  I disse miljøer kan du kun prøve Defender for Office 365 i *overvågningstilstand*. Du behøver ikke at ændre dit mailflow (MX-poster) for at prøve Defender for Office 365.

- Du har allerede en Microsoft 365-organisation. Mail fra internetflows direkte fra Microsoft 365, men dit aktuelle abonnement har kun [Exchange Online Protection (EOP)](exchange-online-protection-overview.md) eller [Defender for Office 365 Plan 1](overview.md#microsoft-defender-for-office-365-plan-1-vs-plan-2-cheat-sheet).

  ![Mail flyder fra internettet til Microsoft 365 med beskyttelse mod EOP og/eller Defender for Office 365 Plan 1.](../../media/mdo-trial-mail-flow.png)

  I disse miljøer kan du prøve Defender for Office 365 i *overvågningstilstand* eller i *blokeringstilstand*.

Du er inviteret til at starte din prøveversion på forskellige Defender for Office 365 funktionsplaceringer på portalen Microsoft 365 Defender på <https://security.microsoft.com>. Den centraliserede placering, hvor du starter din prøveversion, er på siden **Prøveversioner** på <https://security.microsoft.com/atpEvaluation>.

Se denne korte video for at få mere at vide om, hvordan du kan få mere fra hånden på kortere tid med Microsoft Defender for Office 365.
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWMmIe]

I resten af denne artikel forklares forskellen mellem blokeringstilstand for overvågningstilstand, hvordan du konfigurerer evalueringer og andre oplysninger.

Hvis du vil have en medfølgende vejledning til, hvordan du bruger din prøveversion, skal du se [Prøvelegebog: Microsoft Defender for Office 365](trial-playbook-defender-for-office-365.md).

## <a name="overview-of-defender-for-office-365"></a>Oversigt over Defender for Office 365

Defender for Office 365 hjælper organisationer med at sikre deres virksomhed ved at tilbyde en omfattende tavle af egenskaber. Du kan få flere oplysninger under [Microsoft Defender for Office 365](defender-for-office-365.md).

Du kan også få mere at vide om Defender for Office 365 i denne [interaktive vejledning](https://aka.ms/MS365D.InteractiveGuide).

![Microsoft Defender for Office 365 konceptuelt diagram.](../../media/microsoft-defender-for-office-365.png)

## <a name="policies-in-blocking-mode-or-audit-mode"></a>Politikker i blokeringstilstand eller overvågningstilstand

Når du evaluerer Defender for Office 365, findes de politikker, der styrer beskyttelsesfunktionerne i Microsoft 365:

- **Exchange Online Protection (EOP):** Der oprettes ingen nye eller særlige politikker. Eksisterende EOP-politikker kan reagere på meddelelser (f.eks. sende meddelelser til mappen Uønsket mail eller sætte dem i karantæne):

  - [Politikker for antimalware](anti-malware-protection.md)
  - [Indgående beskyttelse mod spam](anti-spam-protection.md)
  - [Beskyttelse mod spoofing i politikker til bekæmpelse af phishing](set-up-anti-phishing-policies.md#spoof-settings)

  Standardpolitikkerne for disse funktioner er altid slået til, gælder for alle modtagere og anvendes altid sidst (efter brugerdefinerede politikker).

- **Defender for Office 365**: Der oprettes politikker, der kun gælder for Defender for Office 365, til evaluering af Defender for Office 365:

  - [Repræsentationsbeskyttelse i politikker til bekæmpelse af phishing](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)
  - [Sikre vedhæftede filer i mails](safe-attachments.md)
  - [Sikre links til mails og Microsoft Teams](safe-links.md)

  Men karakteren af disse politikker er anderledes i blokeringstilstand og overvågningstilstand:

  - **Overvågningstilstand**: Der oprettes almindelige politikker, men politikkerne er kun konfigureret til at *registrere* trusler. Defender for Office 365 registrerer skadelige meddelelser til rapportering, men meddelelserne reageres ikke på (f.eks. er registrerede meddelelser ikke sat i karantæne).

  - **Blokeringstilstand**: Politikker oprettes ved hjælp af standardskabelonen for [forudindstillede sikkerhedspolitikker](preset-security-policies.md). Defender for Office 365 *registrerer og reagerer* *på* skadelige meddelelser (f.eks. er registrerede meddelelser sat i karantæne).

  Standardvalget og det anbefalede valg er at tilpasse disse Defender for Office 365 politikker til alle brugere i organisationen. Men under eller efter konfigurationen kan du ændre politiktildelingen til bestemte brugere, grupper eller maildomæner.

**Noter**:

- Sikre links detonerer URL-adresser i mailflow. Hvis du vil forhindre, at bestemte URL-adresser udløses, skal du bruge listen over tilladte/blokerede lejere. Du kan få flere oplysninger [under Administrer listen over tilladte/blokerede lejere](tenant-allow-block-list.md).
- Sikre links ombryder ikke URL-links i meddelelsestekster.
- Indstillingerne for evalueringspolitikken er beskrevet i afsnittet [Indstillinger for evalueringspolitik](#evaluation-policy-settings) senere i denne artikel.

## <a name="set-up-an-evaluation-in-audit-mode"></a>Konfigurer en evaluering i overvågningstilstand

1. Klik på **Start evaluering**.

2. I dialogboksen **Slå beskyttelse til** skal du vælge **Nej, Jeg vil kun rapportere** og derefter klikke på **Fortsæt**.

3. Konfigurer følgende indstillinger **i dialogboksen Vælg de brugere, du vil medtage** :

   - **Alle brugere**: Dette er standardindstillingen og den anbefalede indstilling.
   - **Vælg brugere**: Hvis du vælger denne indstilling, skal du vælge de interne modtagere, som evalueringen gælder for:
     - **Brugere**: De angivne postkasser, mailbrugere eller mailkontakter.
     - **Grupper**:
       - Medlemmer af de angivne distributionsgrupper eller mailaktiverede sikkerhedsgrupper.
       - Den angivne Microsoft 365-grupper.
       - **Domæner**: Alle modtagere i de angivne [accepterede domæner](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) i din organisation.

     Klik i det relevante felt, begynd at skrive en værdi, og vælg den ønskede værdi fra resultaterne. Gentag denne proces så mange gange, det er nødvendigt. Hvis du vil fjerne en eksisterende værdi, skal du klikke på Fjern ![Fjern ikon.](../../media/m365-cc-sc-remove-selection-icon.png) ud for værdien.

     For brugere eller grupper kan du bruge de fleste identifikatorer (navn, vist navn, alias, mailadresse, kontonavn osv.), men det tilsvarende viste navn vises i resultaterne. For brugere skal du angive en stjerne (\*) alene for at se alle tilgængelige værdier.

   > [!NOTE]
   > Du kan ændre disse valg, når du er færdig med at konfigurere evalueringen.

   Klik på **Fortsæt**, når du er færdig.

4. I dialogboksen **Hjælp os med at forstå dit mailflow** skal du konfigurere følgende indstillinger:

   - **Del data med Microsoft**: Denne indstilling er valgt som standard, men du kan fjerne markeringen i afkrydsningsfeltet, hvis du vil.

   - En af følgende indstillinger vælges automatisk på baggrund af vores registrering af MX-posten for dit domæne:

     - **Jeg bruger en tredjepartsudbyder og/eller en tjenesteudbyder i det lokale miljø: MX-posten** for dine domænepunkter et andet sted end Microsoft 365. Dette valg kræver følgende yderligere indstillinger, når du har klikket på **Næste**:

       1. Konfigurer følgende indstillinger i dialogboksen **Indstillinger for tredjepart eller det lokale** miljø:

          - **Vælg en tredjepartsudbyder**: Vælg en af følgende værdier:
            - **Barracuda**
            - **IronPort**
            - **Mimecast**
            - **Korrekturpunkt**
            - **Sophos**
            - **Symantec**
            - **Trend Micro**
            - **Andet**

          - **Den connector, som denne evaluering skal anvendes på**: Vælg den connector, der bruges til mailflow, i Microsoft 365.

            [Forbedret filtrering for forbindelser](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors) (også kendt som *oversigt over spring* over) konfigureres automatisk på den connector, du angiver.

            Når en tjeneste eller enhed fra tredjepart er placeret foran Microsoft 365, identificerer udvidet filtrering for connectors kilden til internetmeddelelser korrekt og forbedrer i høj grad nøjagtigheden af Microsoft-filtreringsstakken (især [spoof intelligence](anti-spoofing-protection.md) samt funktioner efter sikkerhedsbrud i [Threat Explorer](threat-explorer.md) og [automatiseret undersøgelse & svar (AIR)](automated-investigation-response-office.md)).

          - **Angiv hver gateway-IP-adresse, dine meddelelser passerer:** Denne indstilling er kun tilgængelig, hvis du har valgt **Andet** for **Vælg en tredjepartsudbyder**. Angiv en kommasepareret liste over de IP-adresser, der bruges af beskyttelsestjeneste fra tredjepart eller enhed til at sende mail til Microsoft 365.

          Klik på **Næste**, når du er færdig.

       2. I dialogboksen **Regler for Exchange-mailflow** skal du beslutte, om du har brug for en Exchange Online regel for mailflow (også kendt som en transportregel), der springer spamfiltrering over for indgående meddelelser fra beskyttelsestjeneste eller enhed fra tredjepart.

          Det er sandsynligt, at du allerede har en SCL=-1-regel for mailflow i Exchange Online, der gør det muligt for alle indgående mails fra beskyttelsestjenesten at omgå (de fleste) Microsoft 365-filtrering. Mange beskyttelsestjenester opfordrer til dette niveau for mailflowregel for mailflow for de Microsoft 365-kunder, der bruger deres tjenester.

          Som forklaret i det forrige trin konfigureres udvidet filtrering for forbindelser automatisk på den connector, du angiver som kilde til mail fra beskyttelsestjeneste.

          Hvis du aktiverer forbedret filtrering for forbindelser uden en SCL=-1-regel for indgående mails fra beskyttelsestjenesten, vil det forbedre registreringsfunktionerne i EOP-beskyttelsesfunktionerne, f.eks. [spoof intelligence](anti-spoofing-protection.md), og det kan påvirke leveringen af disse nyligt registrerede meddelelser (f.eks. flytte til mappen Uønsket mail eller sætte dem i karantæne). Denne virkning er begrænset til EOP-politikker; som tidligere forklaret, oprettes Defender for Office 365 politikker i overvågningstilstand.

          Hvis du vil oprette en regel for SCL=-1-mailflowet eller gennemse dine eksisterende regler, skal du klikke på knappen **Gå til Exchange Administration** på siden. Du kan få flere oplysninger under [Brug regler for mailflow til at angive niveauet for spamsikkerhed i meddelelser i Exchange Online](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-set-scl).

          Klik på **Udfør**, når du er færdig.

     - **Jeg bruger kun Microsoft Exchange Online**: MX-posterne for dit domæne peger på Microsoft 365. Der er ikke mere at konfigurere, så klik på **Udfør**.

5. Der vises en statusdialogboks, når evalueringen konfigureres. Når opsætningen er fuldført, skal du klikke på **Udført**.

## <a name="set-up-an-evaluation-in-blocking-mode"></a>Konfigurer en evaluering i blokeringstilstand

1. Klik på **Start evaluering**.

2. I dialogboksen **Slå beskyttelse** til skal du vælge **Ja, beskytte min organisation ved at blokere trusler** og derefter klikke på **Fortsæt**.

3. Konfigurer følgende indstillinger **i dialogboksen Vælg de brugere, du vil medtage** :

   - **Alle brugere**: Dette er standardindstillingen og den anbefalede indstilling.
   - **Vælg brugere**: Hvis du vælger denne indstilling, skal du vælge de interne modtagere, som evalueringen gælder for:
     - **Brugere**: De angivne postkasser, mailbrugere eller mailkontakter.
     - **Grupper**:
       - Medlemmer af de angivne distributionsgrupper eller mailaktiverede sikkerhedsgrupper.
       - Den angivne Microsoft 365-grupper.
     - **Domæner**: Alle modtagere i de angivne [accepterede domæner](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) i din organisation.

     Klik i det relevante felt, begynd at skrive en værdi, og vælg den ønskede værdi fra resultaterne. Gentag denne proces så mange gange, det er nødvendigt. Hvis du vil fjerne en eksisterende værdi, skal du klikke på Fjern ![Fjern ikon.](../../media/m365-cc-sc-remove-selection-icon.png) ud for værdien.

     For brugere eller grupper kan du bruge de fleste identifikatorer (navn, vist navn, alias, mailadresse, kontonavn osv.), men det tilsvarende viste navn vises i resultaterne. For brugere skal du angive en stjerne (\*) alene for at se alle tilgængelige værdier.

   > [!NOTE]
   > Du kan ændre disse valg, når du er færdig med at konfigurere evalueringen.

   Klik på **Fortsæt**, når du er færdig.

4. Der vises en statusdialogboks, når evalueringen konfigureres. Når installationen er fuldført, skal du klikke på **Udført**.

## <a name="reporting-in-audit-mode"></a>Rapportering i overvågningstilstand

- [Statusrapporten Trusselsbeskyttelse](view-email-security-reports.md#threat-protection-status-report) viser registreringer efter Defender for Office 365 i følgende visninger:
  - [Få vist data efter mailmalware \> og diagramopdeling efter registreringsteknologi](view-email-security-reports.md#view-data-by-email--malware-and-chart-breakdown-by-detection-technology)
  - [Få vist data efter mail-phish \> og diagramopdeling efter registreringsteknologi](view-email-security-reports.md#view-data-by-email--phish-and-chart-breakdown-by-detection-technology)

- I [Threat Explorer](threat-explorer.md) viser meddelelser, der blev registreret af Defender for Office 365-evalueringen, følgende banner i detaljerne for posten:

  ![Meddelelsesbanner i meddelelsesoplysninger om, at Defender for Office 365-evalueringen registrerede en skadelig mail.](../../media/evalv2-detection-banner.png)

<!--- This stuff is likely not applicable for V2 reporting --->

Den **Microsoft Defender for Office 365 evalueringsside** på <https://security.microsoft.com/atpEvaluation> konsoliderer rapporteringen for politikkerne i evalueringen:

- Repræsentationsbeskyttelse i politikker til bekæmpelse af phishing
- Sikre links
- Sikre vedhæftede filer

Diagrammerne viser som standard data for de seneste 30 dage, men du kan filtrere datointervallet ved at klikke på ![kalenderikonet.](../../media/m365-cc-sc-add-internal-icon.png) **30 dage** og vælge mellem følgende yderligere værdier, der er mindre end 30 dage:

- 24 timer
- 7 dage
- 14 dage
- Brugerdefineret datointerval

Du kan klikke på ![ikonet Download.](../../media/m365-cc-sc-download-icon.png) **Download** for at downloade diagramdataene til en .csv fil.

## <a name="required-permissions"></a>Påkrævede tilladelser

Tilladelser, der kræves i **Azure AD** for at konfigurere en evaluering af Defender for Microsoft 365, er beskrevet på følgende liste:

- **Opret, rediger eller slet en evaluering**: Sikkerhedsadministrator eller Global administrator.
- **Få vist evalueringspolitikker og -rapporter**: Sikkerhedsadministrator eller Sikkerhedslæser.

Du kan få flere oplysninger om Azure AD tilladelser på Microsoft 365 Defender-portalen [under Azure AD roller på Microsoft 365 Defender-portalen](permissions-microsoft-365-security-center.md#azure-ad-roles-in-the-microsoft-365-defender-portal)

## <a name="evaluation-policy-settings"></a>Indstillinger for evalueringspolitik

Indstillingerne i Defender for Office 365, der er oprettet specifikt til evalueringen, er beskrevet i følgende tabeller:

**Politikindstillinger for evaluering af anti-phishing**:

|Indstilling|Værdi|
|---|---|
|AdminDisplayName|Evalueringspolitik|
|AuthenticationFailAction|Flyt til Jmf|
|Aktiveret|Sandt|
|EnableFirstContactSafetyTips|Falsk|
|EnableMailboxIntelligence|Sandt|
|EnableMailboxIntelligenceProtection|Sandt|
|EnableOrganizationDomainsProtection|Falsk|
|EnableSimilarDomainsSafetyTips|Falsk|
|EnableSimilarUsersSafetyTips|Falsk|
|EnableSpoofIntelligence|Sandt|
|EnableSuspiciousSafetyTip|Falsk|
|EnableTargetedDomainsProtection|Falsk|
|EnableTargetedUserProtection|Falsk|
|EnableUnauthenticatedSender|Sandt|
|EnableUnusualCharactersSafetyTips|Falsk|
|EnableViaTag|Sandt|
|Guid|GUID-værdi|
|ImpersonationProtectionState|Manuel|
|IsDefault|Falsk|
|MailboxIntelligenceProtectionAction|Ingen handling|
|MailboxIntelligenceProtectionActionRecipients|{}|
|MailboxIntelligenceQuarantineTag|DefaultFullAccessPolicy|
|Navn|Evalueringspolitik|
|PhishThresholdLevel|1|
|Anbefalet politiktype|Evaluering|
|SpoofQuarantineTag|DefaultFullAccessPolicy|
|Målmodtagere afdomainAction-modtagere|{}|
|TargetedDomainProtectionAction|Ingen handling|
|TargetedDomainQuarantineTag|DefaultFullAccessPolicy|
|Målrettede brugere|{}|
|TargetedUserProtectionAction|Ingen handling|
|TargetedUserQuarantineTag|DefaultFullAccessPolicy|
|||
|AntiPhishPolicyLevelDataList|Tom|
|AntiSpoofEnforcementType|Høj|
|AuthenticationSafetyTipText|Tom|
|AuthenticationSoftPassSafetyTipText|Tom|
|EnableAuthenticationSafetyTip|Falsk|
|EnableAuthenticationSoftPassSafetyTip|Falsk|
|PolicyTag|Tom|
|SimilarUsersSafetyTipsCustomText|Tom|
|TreatSoftPassAsAuthenticated|Sandt|
|UnusualCharactersSafetyTipsCustomText|Tom|
|||
|ExcludedDomains|{}|
|ExcludedSenders|{}|
|TargetedDomainsToProtect|{}|
|TargetedUsersToProtect|{}|

**Politikindstillinger for evaluering af vedhæftede filer, der er tillid til**:

|Indstilling|Værdi|
|---|---|
|Handling|Tillad|
|ActionOnError|Sandt|
|AdminDisplayName|Evalueringspolitik|
|ConfidenceLevelThreshold|80|
|Aktiverer|Sandt|
|EnableOrganizationBranding|Falsk|
|Guid|GUID-værdi|
|IsBuiltInProtection|Falsk|
|IsDefault|Falsk|
|Navn|Evalueringspolitik|
|Handlingstilstand|Forsinkelse|
|QuarantineTag|AdminOnlyAccessPolicy|
|Anbefalet politiktype|Evaluering|
|Omdirigere|Falsk|
|RedirectAddress|{}|
|ScanTimeout|30|

**Politikindstillinger for evaluering af sikre links**:

|Indstilling|Værdi|
|---|---|
|AdminDisplayName|Evalueringspolitik|
|AllowClickThrough|Falsk|
|CustomNotificationText|Tom|
|DeliverMessageAfterScan|Sandt|
|DisableUrlRewrite|Sandt|
|DoNotRewriteUrls|{}|
|EnableForInternalSenders|Falsk|
|EnableOrganizationBranding|Falsk|
|EnableSafeLinksForTeams|Sandt|
|Guid|GUID-værdi|
|IsBuiltInProtection|Falsk|
|IsDefault|Falsk|
|IsEnabled|Sandt|
|LocalizedNotificationTextList|{}|
|Navn|"EvaluationPolicy"|
|Anbefalet politiktype|Evaluering|
|ScanUrls|Sandt|
|TrackClicks|Sandt|
|||
|DoNotAllowClickThrough|Tom|
|DoNotTrackUserClicks|Falsk|
|EnableSafeLinksForEmail|Sandt|
|EnableSafeLinksForOffice|Sandt|
|ExcludedUrls|{}|
|WhiteListedUrls|Tom|
