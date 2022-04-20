---
title: Kundelåsekasseanmodninger
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
search.appverid:
- BCS160
- MET150
- MOE150
ms.custom: admindeeplinkMAC
description: Få mere at vide om kunde lockbox-anmodninger, der giver dig mulighed for at styre, hvordan en Microsoft-supporttekniker kan få adgang til dine data, når du støder på et problem.
ms.openlocfilehash: cf9a2a6d682ca87e97986389f640a536775ca014
ms.sourcegitcommit: e911dd506ea066795e418daf7b84c1e11381a21c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/19/2022
ms.locfileid: "64953820"
---
# <a name="microsoft-purview-customer-lockbox"></a>Microsoft Purview Customer Lockbox

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Denne artikel indeholder en installations- og konfigurationsvejledning til Customer Lockbox. Customer Lockbox understøtter anmodninger om at få adgang til data i Exchange Online, SharePoint Online, OneDrive for Business og Teams. Hvis du vil anbefale support til andre tjenester, skal du sende en anmodning på [feedbackportalen](https://feedbackportal.microsoft.com).

Hvis du vil se indstillingerne for licensering af dine brugere, så de kan drage fordel af Microsoft Purview-tilbud, skal du se [Microsoft 365 licensvejledning for at få hjælp til sikkerhed & overholdelse af angivne standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

Kundelåsekasse sikrer, at Microsoft ikke kan få adgang til dit indhold for at udføre servicehandlinger uden din eksplicitte godkendelse. Customer Lockbox fører dig ind i den arbejdsproces for godkendelse, som Microsoft bruger til at sikre, at kun godkendte anmodninger giver adgang til dit indhold. Du kan få mere at vide om Microsofts arbejdsproces under [Privilegeret adgangsstyring](privileged-access-management-solution-overview.md).

Nogle gange hjælper Microsoft-teknikere med at foretage fejlfinding og løse problemer, der opstår i forbindelse med tjenesten. Normalt løser teknikere problemer ved hjælp af omfattende telemetri- og fejlfindingsværktøjer, som Microsoft har til sine tjenester. Nogle tilfælde kræver dog, at en Microsoft-tekniker har adgang til dit indhold for at finde rodårsagen og løse problemet. Customer Lockbox kræver, at teknikeren anmoder om adgang fra dig som et sidste trin i godkendelsesarbejdsprocessen. Det giver dig mulighed for at godkende eller afvise anmodningen for din organisation og give direkte adgangskontrol til dit indhold.

## <a name="customer-lockbox-overview-video"></a>Video med oversigt over kundelåsekasse

> [!VIDEO https://www.microsoft.com/videoplayer/embed/8fecf10b-1f03-4849-8b67-76d3d2a43f26?autoplay=false]

## <a name="customer-lockbox-workflow"></a>Arbejdsproces for kundelåsekasse

I disse trin beskrives den typiske arbejdsproces, når en Microsoft-tekniker starter en kundelåsekasseanmodning:

1. En person i en organisation oplever et problem med deres Microsoft 365 postkasse.

2. Når brugeren har lokaliseret problemet, men ikke kan løse det, åbner vedkommende en supportanmodning hos Microsoft Support.

3. En Microsoft-supporttekniker gennemgår serviceanmodningen og bestemmer et behov for at få adgang til organisationens lejer for at reparere problemet.

4. Microsofts supporttekniker logger på kundelåsekasseanmodningsværktøjet og foretager en anmodning om adgang til data, der indeholder organisationens lejernavn, serviceanmodningsnummer og den anslåede tid, teknikeren har brug for at få adgang til dataene.

5. Når en Microsoft Support manager godkender anmodningen, sender Customer Lockbox den udpegede godkender i organisationen en mail om den ventende anmodning om adgang fra Microsoft.

    ![Eksempel på en kundes lockbox-mailmeddelelse.](../media/CustomerLockbox1.png)

   Alle, der har fået tildelt administratorrollen [Kundelåskasseadgang](/office365/admin/add-users/about-admin-roles) i Microsoft 365 Administration, kan godkende kundelåsningsanmodninger.

6. Godkenderen logger på Microsoft 365 Administration og godkender anmodningen. Dette trin udløser oprettelsen af en overvågningspost, der er tilgængelig, ved at søge i overvågningsloggen. Du kan få flere oplysninger under [Overvågning af kundelåsekasseanmodninger](#auditing-customer-lockbox-requests).

   Hvis kunden afviser anmodningen eller ikke godkender anmodningen inden for 12 timer, udløber anmodningen, og Der gives ingen adgang til Microsoft-teknikeren.

   > [!IMPORTANT]
   > Microsoft inkluderer ingen links i kundelåskassemailmeddelelser, der kræver, at du logger på Office 365.

7. Når godkenderen fra organisationen har godkendt anmodningen, modtager Microsoft-teknikere godkendelsesmeddelelsen, logger på lejeren og løser kundens problem. Microsoft-teknikere har den ønskede varighed til at løse problemet, hvorefter adgangen tilbagekaldes automatisk.

> [!NOTE]
> Alle handlinger, der udføres af en Microsoft-tekniker, logføres i overvågningsloggen. Du kan søge efter og gennemse disse overvågningsposter.

## <a name="turn-customer-lockbox-requests-on-or-off"></a>Slå kundelåsekasseanmodninger til eller fra

Du kan slå Customer Lockbox-kontrolelementer til i Microsoft 365 Administration. Når du slår Customer Lockbox til, skal Microsoft indhente din organisations godkendelse, før du får adgang til noget af din lejers indhold.

1. Ved hjælp af en arbejds- eller skolekonto, der enten har rollen global administrator eller **rollen Kundelåskasseadgangsgodkender** tildelt, skal du gå til [https://admin.microsoft.com](https://admin.microsoft.com) og logge på.

2. Vælg **Indstillinger** >  **Ellerg Indstillinger** >  **Sikkerhed & Beskyttelse af personlige oplysninger**.

3. Vælg **Sikkerhed & Beskyttelse af personlige oplysninger**, og vælg derefter **Kundelåseboks** i venstre kolonne. Markér afkrydsningsfeltet **Kræv godkendelse af alle anmodninger om dataadgang** , og gem ændringerne for at aktivere funktionen.

    ![Kræv godkendelse af Customer Lockbox](../media/CustomerLockbox4-new.png)

## <a name="approve-or-deny-a-customer-lockbox-request"></a>Godkend eller afvis en kundelåsekasseanmodning

1. Ved hjælp af en arbejds- eller skolekonto, der enten har rollen global administrator eller **rollen Kundelåskasseadgangsgodkender** tildelt, skal du gå til [https://admin.microsoft.com](https://admin.microsoft.com) og logge på.

2. Vælg **Support > kundelåsekasseanmodninger**.

    ![Klik på Support, og klik derefter på Kundelåsekasseanmodninger.](../media/CustomerLockbox5.png)

    Der vises en liste over kundelåsekasseanmodninger.

    ![Liste over kundelåsekasseanmodninger.](../media/CustomerLockbox6.png)

3. Vælg en kundelåsekasseanmodning, og vælg derefter **Godkend** eller **Afvis**.

    ![Godkend kundelåsekasseanmodninger.](../media/CustomerLockbox7.png)

    Der vises en bekræftelsesmeddelelse om godkendelse af kundelåsekasseanmodningen.

    ![Afvis kundelåsekasseanmodninger.](../media/CustomerLockbox8.png)

> [!NOTE]
> Brug cmdlet'en Set-AccessToCustomerDataRequest til at godkende, afvise eller annullere Microsoft Purview Customer Lockbox-anmodninger, der styrer microsoft-supportteknikeres adgang til dine data. Du kan få flere oplysninger under [Set-AccessToCustomerDataRequest](/powershell/module/exchange/set-accesstocustomerdatarequest).

## <a name="auditing-customer-lockbox-requests"></a>Overvågning af kundelåsekasseanmodninger

Overvågningsposter, der svarer til kundelåsekasseanmodninger, logføres i Microsoft 365 overvågningslog. Du kan få adgang til disse logge ved hjælp af [søgeværktøjet til overvågningslogfiler](search-the-audit-log-in-security-and-compliance.md) på Microsoft Purview-overholdelsesportalen. Handlinger, der er relateret til at acceptere eller afvise en kundelåsekasseanmodning, og handlinger, der udføres af Microsoft-teknikere (når adgangsanmodninger godkendes), logføres også i overvågningsloggen. Du kan søge efter og gennemse disse overvågningsposter.

### <a name="search-the-audit-log-for-activity-related-to-customer-lockbox-requests"></a>Søg i overvågningsloggen efter aktivitet, der er relateret til kundelåsekasseanmodninger

Før du kan bruge overvågningsloggen til at spore anmodninger om Customer Lockbox, er der nogle trin, du skal udføre for at konfigurere overvågningslogføring, herunder tildeling af tilladelser til at søge i overvågningsloggen. Du kan få flere oplysninger under [Konfigurer Microsoft Purview Audit (Standard)](set-up-basic-audit.md). Når du har fuldført konfigurationen, skal du bruge disse trin til at oprette en søgeforespørgsel i overvågningsloggen for at returnere overvågningsposter, der er relateret til Customer Lockbox:

1. Gå til <https://compliance.microsoft.com>.
  
2. Log på med en konto, der har fået tildelt de nødvendige tilladelser til at søge i overvågningsloggen.

3. I venstre rude i Overholdelsescenter skal du vælge **Overvågning**.

    Fanen **Søg** på siden **Overvågning** vises.

    ![Søgeside for overvågningslog.](../media/auditlogsearch1.png)
  
4. Konfigurer følgende søgekriterier:

   1. **Startdato** og **Slutdato**. Vælg et dato- og klokkeslætsinterval for at få vist de hændelser, der opstod inden for den pågældende periode.  

   2. **Aktiviteter**. Lad feltet være tomt, så søgningen returnerer overvågningsposter for alle aktiviteter. Dette er nødvendigt for at returnere eventuelle overvågningsposter, der er relateret til kundelåsekasseanmodninger og tilsvarende aktivitet udført af Microsoft-teknikere.

   3. **Brugere**. Lad dette felt være tomt.

   4. **Fil, mappe eller websted**. Lad dette felt være tomt.

5. Klik på **Søg** for at køre søgningen ved hjælp af dine søgekriterier.

    Søgeresultaterne vises efter et øjeblik. Der føjes flere søgeresultater til siden, indtil søgningen er fuldført.

6. Klik på overskriften i kolonnen **Aktivitet** for at sortere resultaterne alfabetisk baseret på værdierne i kolonnen **Aktivitet** .

7. Rul ned, og søg efter overvågningsposter med en aktivitet i **Set-AccessToCustomerDataRequest**. Poster med denne aktivitet er relateret til en godkender i din organisation, der godkender eller afviser en kundelåsekasseanmodning.

8. Du kan også klikke på overskriften i kolonnen **User** for at sortere resultaterne alfabetisk ved hjælp af værdierne i kolonnen **User** . Søg efter værdien af **Microsoft Operator**, som angiver aktiviteter, der udføres af en Microsoft-tekniker som svar på en godkendt kundelåsekasseanmodning. Kolonnen **Aktivitet** viser den handling, der er udført af teknikeren.

      ![Filtrer efter "Microsoft Operator" for at få vist overvågningsposter](../media/CustomerLockbox10.png)

9. Klik på en overvågningspost på listen over resultater for at få den vist.

### <a name="export-the-audit-log-search-results"></a>Eksportér søgeresultaterne i overvågningsloggen

Du kan også eksportere søgeresultaterne i overvågningsloggen til en CSV-fil og derefter åbne filen i Excel for at bruge filtrerings- og sorteringsfunktionerne for at gøre det nemmere at finde og få vist overvågningsposter, der er relateret til en kundelåskasseadgangsanmodning.

Hvis du vil eksportere overvågningsposter, skal du bruge de forrige trin til at søge i overvågningsloggen. Når søgningen er fuldført, skal du vælge **Eksportér > Download alle resultater** øverst på siden med søgeresultater. Når eksporten er fuldført, kan du downloade CSV-filen til din lokale computer. Du kan finde mere detaljerede instruktioner under [Eksportér, konfigurer og få vist overvågningslogposter](export-view-audit-log-records.md).

Når du har downloadet filen, kan du åbne den i Excel og derefter filtrere kolonnen **Handlinger** for at få vist overvågningsposter for aktiviteter af typen **Set-AccessToCustomerDataRequest**. Du kan også filtrere på kolonnen **UserIds** (ved hjælp af værdien **Microsoft Operator**) for at få vist overvågningsposter for aktiviteter, der udføres af Microsoft-teknikere.

> [!NOTE]
> Når du får vist overvågningsposter i CSV-filen, findes der flere oplysninger i kolonnen **AuditData** . Oplysningerne i denne kolonne findes i et JSON-objekt, som indeholder flere egenskaber, der er konfigureret som *property:value-par* adskilt af kommaer. Du kan bruge transformationsfunktionen JSON i Power Query-editor i Excel til at opdele hver egenskab i JSON-objektet i kolonnen **AuditData** i flere kolonner, så hver egenskab har sin egen kolonne. Det gør det lettere at fortolke disse oplysninger. Du kan finde flere instruktioner under [Formatér den eksporterede overvågningslog ved hjælp af Power Query-editor](export-view-audit-log-records.md#step-2-format-the-exported-audit-log-using-the-power-query-editor).

### <a name="use-powershell-to-search-and-export-audit-records"></a>Brug PowerShell til at søge efter og eksportere overvågningsposter

Et alternativ til at bruge værktøjet til overvågningssøgning på Microsoft Purview-overholdelsesportalen er at køre cmdlet'en [Search-UnifiedAuditLog](/powershell/module/exchange/search-unifiedauditlog) i Exchange Online PowerShell. En fordel ved at bruge PowerShell er, at du specifikt kan søge efter **Set-AccessToCustomerDataRequest-aktiviteter** eller aktiviteter, der udføres af Microsoft-teknikere, som er relateret til en kundelåskasseanmodning.

Når du [har oprettet forbindelse til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell), skal du køre en af følgende kommandoer. Erstat pladsholderne med et bestemt datointerval.

Søg efter `Set-AccessToCustomerDataRequest` aktiviteter

```powershell
Search-UnifiedAuditLog -StartDate xx/xx/xxxx -EndDate xx/xx/xxxx -Operations Set-AccessToCustomerDataRequest
```

Søg efter aktiviteter, der udføres af Microsoft-teknikere

```powershell
Search-UnifiedAuditLog -StartDate xx/xx/xxxx -EndDate xx/xx/xxxx -UserIds "Microsoft Operator"
```

Du kan finde flere oplysninger og eksempler under [Brug PowerShell til at søge efter og eksportere overvågningslogposter](export-view-audit-log-records.md#use-powershell-to-search-and-export-audit-log-records).

Vi har også angivet et PowerShell-script, som du kan bruge til at søge i overvågningsloggen og eksportere resultaterne til en CSV-fil. Du kan finde flere oplysninger under [Brug et PowerShell-script til at søge i overvågningsloggen](audit-log-search-script.md).

### <a name="audit-record-for-a-customer-lockbox-request"></a>Overvågningspost for en kundelåsekasseanmodning

Når en person i organisationen godkender eller afviser en Customer Lockbox-anmodning, logføres overvågningsposten i overvågningsloggen med følgende oplysninger.

| Overvågningspostegenskab| Beskrivelse|
|:---------- |:----------|
| Dato       | Den dato og det klokkeslæt, hvor kundelåskasseanmodningen blev godkendt eller afvist.
| IP-adresse | IP-adressen på den computer, som godkenderen brugte til at godkende eller afvise en anmodning. |
| Bruger       | Tjenestekontoen BOXServiceAccount@\[customerforest.prod.outlook.com\].            |
| Aktivitet   | Set-AccessToCustomerDataRequest; dette er den overvågningsaktivitet, der logføres, når du godkender eller afviser en kundelåsekasseanmodning.                                |
| Element       | GUID for kundelåsekasseanmodningen                             |

På følgende skærmbillede kan du se et eksempel på en overvågningspost, der svarer til en godkendt kundelåsekasseanmodning. Hvis en kundes Lockbox-anmodning blev nægtet, ville værdien af `ApprovalDecision` parameteren være `Deny`.

![Overvågningspost for en godkendt kundelåsekasseanmodning.](../media/CustomerLockbox9.png)

### <a name="audit-record-for-an-action-performed-by-a-microsoft-engineer"></a>Overvågningspost for en handling, der udføres af en Microsoft-tekniker

De handlinger, der udføres af en Microsoft-tekniker, efter at en kundes Lockbox-anmodning er godkendt (og som kan resultere i adgang til kundeindhold), logføres i overvågningsloggen. Disse poster indeholder følgende oplysninger.

| Overvågningspostegenskab| Beskrivelse|
|:---------- |:----------|
| Dato       | Dato og klokkeslæt for udførelse af handlingen. Det tidspunkt, hvor denne handling blev udført, er inden for 4 timer efter, at kundelåsekasseanmodningen blev godkendt.              |
| IP-adresse | IP-adressen på den computer, Som Microsoft-tekniker brugte. |
| Bruger       | Microsoft Operator; denne værdi angiver, at posten er relateret til en kundelåsekasseanmodning.                                  |
| Aktivitet   | Navnet på den aktivitet, der udføres af Microsoft-teknikeren.|
| Element       | \<empty\>                                             |

## <a name="frequently-asked-questions"></a>Ofte stillede spørgsmål

### <a name="which-microsoft-365-services-does-customer-lockbox-apply-to"></a>Hvilke Microsoft 365 tjenester gælder Customer Lockbox for?

Customer Lockbox understøttes i øjeblikket i Exchange Online, SharePoint Online, OneDrive for Business og Teams.

### <a name="is-customer-lockbox-available-to-all-customers"></a>Er Customer Lockbox tilgængelig for alle kunder?

Kundelåseboksen er inkluderet i abonnementerne på Microsoft 365 eller Office 365 E5 og kan føjes til andre planer med et abonnement på Information Protection og overholdelse eller et tilføjelsesprogram til avanceret overholdelse. Se [Planer og priser](https://products.office.com/business/office-365-enterprise-e5-business-software) for at få flere oplysninger.

### <a name="what-is-customer-content"></a>Hvad er kundeindhold?

Kundeindhold er de data, der oprettes af brugere af Microsoft 365 tjenester og programmer. Eksempler på kundeindhold omfatter:

- Brødtekst eller vedhæftede filer i mails

- SharePoint webstedsindhold

- Oplysninger i brødteksten i en SharePoint fil

- brødtekst i Skype for Business præsentationsfil

- Chatsamtaler eller talesamtaler

- Tekst, der er angivet i Teams chats og Teams kanaler, f.eks. 1:1 chats, gruppechats, delte kanaler, private kanaler og mødechat

- Andre data, der er indsat i Teams chattråde, f.eks. kodestykker, billeder, lyd- og videomeddelelser og links

- App- og bot-data i Teams chats og Teams kanaler

- Teams aktivitetsopdatering

- Teams mødeoptagelser og transskriptioner

- Voicemail

- Filer, der er sendt til Teams chats og Teams kanaler

- Kundegenererede blob- eller strukturerede lagerdata (f.eks. SQL objektbeholdere)

- Kundeejede sikkerhedsoplysninger (f.eks. certifikater, krypteringsnøgler og adgangskoder)

- Udledelser og alle efterfølgende konklusioner, hvis kundeindholdet forbliver

Du kan få flere oplysninger om kundeindhold i Office 365 i [Office 365 Center for sikkerhed og rettighedsadministration](https://products.office.com/business/office-365-trust-center-privacy/).

### <a name="who-is-notified-when-there-is-a-request-to-access-my-content"></a>Who får besked, når der er en anmodning om at få adgang til mit indhold?

Globale administratorer og alle, der har fået tildelt administratorrollen Kundelåskasseadgangsadministrator, får besked. Det er også de samme brugere, der kan godkende kundelåsekasseanmodninger.

### <a name="who-can-approve-or-reject-these-requests-in-my-organization"></a>Who kan godkende eller afvise disse anmodninger i min organisation?

Globale administratorer og alle, der har fået tildelt administratorrollen Kundelåskasseadgang, kan godkende kundelåsningsanmodninger. Kunder styrer disse rolletildelinger i deres organisationer.

### <a name="how-do-i-opt-in-to-customer-lockbox"></a>Hvordan gør jeg tilmelde dig Customer Lockbox?

En global administrator kan aktivere og konfigurere Customer Lockbox i Microsoft 365 Administration.

### <a name="if-i-approve-a-customer-lockbox-request-what-can-the-engineer-do-and-how-will-i-know-what-the-microsoft-engineer-did"></a>Hvis jeg godkender en Customer Lockbox-anmodning, hvad kan tekniker så gøre, og hvordan ved jeg, hvad Microsoft-teknikeren har gjort?

Når du har godkendt en kundelåsekasseanmodning, har Microsoft-teknikeren tildelt disse nødvendige rettigheder til at få adgang til kundeindhold ved hjælp af forhåndsgodkendte cmdlet'er. Handlinger, der udføres af Microsoft-teknikere som svar på kundelåsekasseanmodninger, logføres og er tilgængelige i overvågningsloggen i Security & Compliance Center.

### <a name="how-do-i-know-that-microsoft-follows-the-approval-process"></a>Hvordan gør jeg vide, at Microsoft følger godkendelsesprocessen?

Du kan krydsreferere til meddelelser om godkendelse via mail, der er sendt til administratorer og godkendere i din organisation, med historikken for kundelåskasseanmodninger i [Microsoft 365 Administration](https://go.microsoft.com/fwlink/p/?linkid=2024339).

Kundelåsekasse er inkluderet i den seneste [SOC 1 SSAE 16-overvågningsrapport](https://servicetrust.microsoft.com/ViewPage/MSComplianceGuide?command=Download&downloadType=Document&downloadId=91592749-e86a-43ac-801e-121382614681&docTab=4ce99610-c9c0-11e7-8c2c-f908a777fa4d_SOC%20%2F%20SSAE%2016%20Reports). Du kan finde de nyeste rapporter på [Microsoft Service Trust Portal](https://servicetrust.microsoft.com/ViewPage/MSComplianceGuide?command=Download&downloadType=Document&downloadId=91592749-e86a-43ac-801e-121382614681&docTab=4ce99610-c9c0-11e7-8c2c-f908a777fa4d_SOC%20%2F%20SSAE%2016%20Reports) for at få flere oplysninger.

### <a name="can-microsoft-modify-the-list-of-approvers-for-my-tenant-if-not-how-is-it-prevented"></a>Kan Microsoft ændre listen over godkendere for min lejer? Hvis ikke, hvordan forhindres det så?

Det er kun en global administrator i din organisation, der kan angive, hvem der kan godkende kundelåsekasseanmodninger. Det betyder, at det kun er medlemmerne af Global administrator-gruppen i Azure Active Directory, der kan angive, hvem der kan godkende anmodningen. Medlemskab af den Global administrator gruppe i Azure Active Directory administreres kun af din organisation.

### <a name="what-if-i-need-more-information-about-a-content-access-request-to-approve-it"></a>Hvad gør jeg, hvis jeg har brug for flere oplysninger om en anmodning om adgang til indhold for at godkende den?

Hver kundelåsekasseanmodning indeholder et Microsoft 365 serviceanmodningsnummer. Du kan kontakte Microsoft Support og henvise til dette tjenestenummer for at få flere oplysninger om anmodningen.

### <a name="when-a-customer-lockbox-request-is-approved-how-long-are-the-permissions-valid"></a>Hvor længe er tilladelserne gyldige, når en kundes Lockbox-anmodning godkendes?

I øjeblikket er den maksimale periode for de adgangstilladelser, der er tildelt Microsoft-tekniker, 4 timer. Microsoft-teknikeren kan også anmode om en kortere periode.

### <a name="how-can-i-get-a-history-of-all-customer-lockbox-requests"></a>Hvordan får jeg en oversigt over alle kundelåsekasseanmodninger?

Alle kundelåsekasseanmodninger vises i [Microsoft 365 Administration](https://go.microsoft.com/fwlink/p/?linkid=2024339).

### <a name="how-do-i-correlate-the-content-access-requests-with-the-related-audit-logs"></a>Hvordan gør jeg korrelere anmodninger om adgang til indhold med de relaterede overvågningslogge?

Aktivitetsopdateringen for Overholdelsescenter indeholder logaktiviteter for Kundelåseboks. Kunder kan krydsreferencer til kundelåskasselogaktiviteterne fra aktivitetsopdateringen i forhold til den mailanmodning, de modtager.

### <a name="what-happens-when-a-customer-doesnt-respond-to-a-customer-lockbox-request"></a>Hvad sker der, når en kunde ikke besvarer en kundes Lockbox-anmodning?

Kunde lockbox-anmodninger har en standardvarighed på 12 timer. Hvis du ikke besvarer en anmodning inden for 12 timer, udløber anmodningen.

### <a name="what-does-microsoft-do-when-a-customer-rejects-a-customer-lockbox-request"></a>Hvad gør Microsoft, når en kunde afviser en Kunde lockbox-anmodning?

Hvis en kunde afviser en kundelåsekasseanmodning, sker der ingen adgang til kundeindhold. Hvis en bruger i din organisation fortsat oplever et tjenesteproblem, der kræver, at Microsoft får adgang til kundeindhold for at løse problemet, kan tjenesteproblemet fortsætte, og Microsoft informerer brugeren om dette.

### <a name="how-do-i-set-up-alerts-whenever-a-request-has-been-approved"></a>Hvordan gør jeg konfigurere beskeder, når en anmodning er blevet godkendt?

Der er ingen indbygget mulighed for at give administratorer besked. Administratorer kan dog konfigurere beskeder ved hjælp af [Microsoft Defender for Cloud Apps](/cloud-app-security/getting-started-with-cloud-app-security#to-create-policies).

### <a name="does-customer-lockbox-protect-against-data-requests-from-law-enforcement-agencies-or-other-third-parties"></a>Beskytter Customer Lockbox mod dataanmodninger fra retshåndhævende myndigheder eller andre tredjeparter?

Nej. Microsoft tager tredjepartsanmodninger om kundedata alvorligt. Som cloudtjenesteudbyder går Microsoft altid ind for beskyttelse af kundedata. I tilfælde af at vi får en stævning, forsøger Microsoft altid at omdirigere tredjeparten til kunden for at få oplysningerne. (Læs Brad Smiths blog: [Beskyttelse af kundedata mod offentlige snooping](https://blogs.microsoft.com/blog/2013/12/04/protecting-customer-data-from-government-snooping/)). Vi udgiver jævnligt [detaljerede oplysninger](https://www.microsoft.com/corporate-responsibility/lerr) om de anmodninger om retshåndhævelse, som Microsoft modtager.

Se [Microsoft Center for sikkerhed og rettighedsadministration](https://www.microsoft.com/trustcenter/default.aspx) vedrørende dataanmodninger fra tredjepart og afsnittet "Offentliggørelse af kundedata" under [Vilkår for onlinetjenester for at](https://www.microsoft.com/Licensing/product-licensing/products.aspx) få flere oplysninger.

### <a name="how-does-microsoft-ensure-that-a-member-of-its-staff-doesnt-have-standing-access-to-customer-content-in-office-365-applications"></a>Hvordan sikrer Microsoft, at en medarbejder ikke har stående adgang til kundeindhold i Office 365 programmer?

Microsoft implementerer omfattende forebyggende foranstaltninger via adgangskontrolsystemer og detektivforanstaltninger for at identificere og løse forsøg på at omgå disse adgangskontrolsystemer. Microsoft 365 opererer med principperne om færrest mulige rettigheder og just-in-time-adgang. Derfor har ingen Microsoft-medarbejdere tilladelse til at få adgang til kundeindhold løbende. Hvis der gives tilladelse, er det af begrænset varighed.

Microsoft 365 bruger et adgangskontrolsystem kaldet *Lockbox* til at behandle anmodninger om tilladelser, der giver mulighed for at udføre driftsmæssige og administrative funktioner i tjenesten. En operator skal anmode om adgang til kundeindhold ved hjælp af Lockbox, som derefter kræver, at en anden person foretager sig noget på anmodningen (f.eks. godkender den), før der gives adgang. Den anden person kan ikke være anmoderen og skal være udpeget til at godkende adgang til kundeindhold. Det er kun, hvis anmodningen er godkendt, at operatøren får midlertidig adgang til kundeindhold. Når udvidede rettigheder udløber, tilbagekalder Lockbox adgangen.

Se vilkårene for [onlinetjenester](https://www.microsoft.com/licensing/product-licensing/products) for at få flere oplysninger om Microsofts generelle sikkerhedspraksisser.

### <a name="under-what-circumstances-do-microsoft-engineers-need-access-to-my-content"></a>Under hvilke omstændigheder har Microsoft-teknikere brug for adgang til mit indhold?

Det mest almindelige scenarie, hvor Microsoft-teknikere har brug for at få adgang til kundeindhold, er, når kunden foretager en supportanmodning, der kræver adgang til fejlfinding. Et grundlæggende princip i Microsoft 365 er, at tjenesten fungerer uden Microsofts adgang til kundeindhold. Næsten alle tjenestehandlinger, der udføres af Microsoft, er fuldt automatiserede, og menneskelig involvering styres i høj grad og abstrakteres væk fra kundeindhold. Målet for Microsoft 365 er at få adgang til kundeindhold for at understøtte tjenesten, før kunden godkender en specifik anmodning om Microsoft-adgang.

### <a name="i-already-thought-my-data-was-secure-with-the-microsoft-cloud-so-why-do-i-need-customer-lockbox"></a>Jeg troede allerede, at mine data var sikre med Microsoft-cloudmiljøet, så hvorfor har jeg brug for Customer Lockbox?

Customer Lockbox giver et ekstra lag af kontrol ved at give kunderne mulighed for at give eksplicit adgangstilladelse til tjenestehandlinger. Ved at demonstrere, at der er procedurer for eksplicit godkendelse af dataadgang, hjælper Customer Lockbox også kunderne med at opfylde visse overholdelsesforpligtelser, f.eks. HIPAA og FEDRAMP.
