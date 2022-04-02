---
title: Kunde lockboxanmodninger
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
description: Få mere at vide om kunde lockboxanmodninger, der giver dig mulighed for at styre, hvordan en Microsoft-supporttekniker kan få adgang til dine data, når du støder på et problem.
ms.openlocfilehash: dd62eac46630d92fa5171969d48baec151c92b33
ms.sourcegitcommit: db2ed146b46ade9ea62eed9cb8efff5fea7a35e6
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/26/2022
ms.locfileid: "64481402"
---
# <a name="customer-lockbox-in-office-365"></a>Kunde lockbox i Office 365

Denne artikel indeholder installations- og konfigurationsvejledning til kunde lockbox. Kunde lockbox understøtter anmodninger om at få adgang til data Exchange Online, SharePoint Online, OneDrive for Business og Teams. Hvis du vil anbefale support til andre tjenester, skal du sende en anmodning på [Feedback Portal](https://feedbackportal.microsoft.com).

Hvis du vil se mulighederne for at licensere dine brugere til at drage fordel af Microsoft 365-overholdelsestilbud, skal du se [Microsoft 365-licensvejledning til sikkerhed & overholdelse af regler og standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

Kunde-lockbox sikrer, at Microsoft ikke kan få adgang til dit indhold for at udføre servicehandlinger uden din udtrykkelige godkendelse. Kunde lockbox fører dig ind i den godkendelsesproces, som Microsoft bruger til at sikre, at kun autoriserede anmodninger tillader adgang til dit indhold. Du kan få mere at vide om Microsofts arbejdsproces under [Administration af adgang med rettigheder i Microsoft 365](privileged-access-management-solution-overview.md).

Nogle gange hjælper Microsoft-teknikere med at foretage fejlfinding og løse problemer, der opstår med tjenesten. Som regel løser teknikere problemer med omfattende telemetri- og fejlfindingsværktøjer, som Microsoft har for sine tjenester. Nogle tilfælde kræver dog, at en Microsoft-tekniker får adgang til dit indhold for at fastlægge den egentlige årsag og løse problemet. Kunde lockbox kræver, at teknikeren anmoder om adgang fra dig som det sidste trin i arbejdsprocessen til godkendelse. Dette giver dig mulighed for at godkende eller afvise anmodningen for din organisation og give direkte adgang til dit indhold.

## <a name="customer-lockbox-overview-video"></a>Video med oversigt over kundelåseboks

> [!VIDEO https://www.microsoft.com/videoplayer/embed/8fecf10b-1f03-4849-8b67-76d3d2a43f26?autoplay=false]

## <a name="customer-lockbox-workflow"></a>Arbejdsprocesser for kunde lockbox

Disse trin beskriver den typiske arbejdsproces, når en Microsoft-tekniker starter en kunde lockboxanmodning:

1. En person i en organisation oplever et problem med deres Microsoft 365 postkasse.

2. Når brugeren foretager fejlfinding af problemet, men ikke kan løse det, åbner de en supportanmodning hos Microsoft Support.

3. En Microsoft-supporttekniker gennemser serviceanmodningen og afgør, om der er behov for at få adgang til organisationens lejer for at reparere problemet.

4. Microsoft-supportteknikeren logger på værktøjet til kunde lockboxanmodningen og anmoder om dataadgang, som omfatter organisationens lejernavn, serviceanmodningsnummer og den anslåede tid, teknikeren skal bruge adgang til dataene.

5. Når en Microsoft Supportadministrator godkender anmodningen, sender kundelåsfeltet den udpegede godkender i organisationen en mail om den ventende adgangsanmodning fra Microsoft.

    ![Eksempel på en kunde-Lockbox-mailmeddelelse.](../media/CustomerLockbox1.png)

   Alle, der er tildelt [administratorrollen kundelåskasseadgang](/office365/admin/add-users/about-admin-roles) i Microsoft 365 Administration kan godkende kunde lockboxanmodninger.

6. Godkenderen logger på Microsoft 365 Administration og godkender anmodningen. Dette trin udløser oprettelse af en tilgængelig overvågningspost ved at søge i overvågningsloggen. Få mere at vide under [Overvågning af kunde lockboxanmodninger](#auditing-customer-lockbox-requests).

   Hvis kunden afviser anmodningen eller ikke godkender anmodningen inden for 12 timer, udløber anmodningen, og Microsoft-teknikeren får ingen adgang.

   > [!IMPORTANT]
   > Microsoft inkluderer ikke nogen links i kunde lockbox-mailmeddelelser, der kræver, at du logger på Office 365.

7. Når godkenderen fra organisationen godkender anmodningen, modtager Microsoft-teknikeren godkendelsesmeddelelsen, logger på lejeren og løser kundens problem. Microsoft-teknikere har den anmodede varighed til at løse problemet, hvorefter adgangen automatisk tilbagekaldes.

> [!NOTE]
> Alle handlinger, der udføres af en Microsoft-tekniker, logføres i overvågningsloggen. Du kan søge efter og gennemse disse overvågningsposter.

## <a name="turn-customer-lockbox-requests-on-or-off"></a>Slå kunde lockboxanmodninger til eller fra

Du kan aktivere kontrolelementer for kunde-lockbox i Microsoft 365 Administration. Når du slår kunde-lockbox til, skal Microsoft have din organisations godkendelse, før der tilgås noget af din lejers indhold.

1. Ved hjælp af en arbejds- eller skolekonto, som enten har den  globale administrator eller den rolle, som godkender af adgang til kundelåsefeltet er tildelt, [https://admin.microsoft.com](https://admin.microsoft.com) skal du gå til og logge på.

2. Vælg **Indstillinger** >  **Org Indstillinger** >  **Security & Beskyttelse af personlige oplysninger**.

3. Vælg **Sikkerhed & beskyttelse af** personlige oplysninger, og **vælg derefter Kundelåskasse** i den venstre kolonne. Markér **afkrydsningsfeltet Kræv godkendelse af alle anmodninger om** dataadgang, og gem ændringerne for at aktivere funktionen.

    ![Kræv godkendelse til kunde lockbox](../media/CustomerLockbox4-new.png)

## <a name="approve-or-deny-a-customer-lockbox-request"></a>Godkend eller afvisning af en kunde-lockboxanmodning

1. Ved hjælp af en arbejds- eller skolekonto, som enten har den  globale administrator eller den rolle, som godkender af adgang til kundelåsefeltet er tildelt, [https://admin.microsoft.com](https://admin.microsoft.com) skal du gå til og logge på.

2. Vælg **Support > kunde lockboxanmodninger**.

    ![Klik på Support, og klik derefter på Kunde lockboxanmodninger.](../media/CustomerLockbox5.png)

    Der vises en liste over kunde lockboxanmodninger.

    ![Liste over kunde lockboxanmodninger.](../media/CustomerLockbox6.png)

3. Vælg en kunde lockboxanmodning, og vælg derefter **Approve** eller **Deny**.

    ![Godkend kunde lockboxanmodninger.](../media/CustomerLockbox7.png)

    Der vises en bekræftelsesmeddelelse om godkendelse af kunde lockboxanmodningen.

    ![Afvisning af kunde-lockboxanmodninger.](../media/CustomerLockbox8.png)

> [!NOTE]
> Brug Set-AccessToCustomerDataRequest til at godkende, afvise eller annullere Microsoft 365 kunde-lockboxanmodninger, der styrer Microsoft-supportteknikeres adgang til dine data. Få mere at vide under [Set-AccessToCustomerDataRequest](/powershell/module/exchange/set-accesstocustomerdatarequest).

## <a name="auditing-customer-lockbox-requests"></a>Overvågning af kunde lockboxanmodninger

Overvågningsposter, der svarer til kunde lockboxanmodninger, logføres Microsoft 365 overvågningsloggen. Du kan få adgang til disse logfiler ved hjælp [af søgeværktøjet til](search-the-audit-log-in-security-and-compliance.md) overvågningslogfiler i Microsoft 365 Overholdelsescenter. Handlinger vedrørende accept eller afvisning af en kunde lockboxanmodning og handlinger, der udføres af Microsoft-teknikere (når adgangsanmodninger godkendes), logføres også i overvågningsloggen. Du kan søge efter og gennemse disse overvågningsposter.

### <a name="search-the-audit-log-for-activity-related-to-customer-lockbox-requests"></a>Søg i overvågningsloggen efter aktivitet, der er relateret til kunde lockboxanmodninger

Før du kan bruge overvågningsloggen til at spore anmodninger om kundelåsfelt, er der nogle ting, du skal gøre for at konfigurere overvågningslogføring, herunder tildele tilladelser til at søge i overvågningsloggen. Du kan finde flere oplysninger [under Konfigurere grundlæggende overvågning i Microsoft 365](set-up-basic-audit.md). Når du har fuldført konfigurationen, skal du følge disse trin for at oprette en søgning i overvågningsloggen for at returnere overvågningsposter, der er relateret til kundelåsfeltet:

1. Gå til <https://compliance.microsoft.com>.
  
2. Log på med en konto, der har fået tildelt de relevante tilladelser til at søge i overvågningsloggen.

3. I venstre rude i Overholdelsescenter skal du vælge **Overvågning**.

    **Fanen Søg** på **siden** Overvågning vises.

    ![Siden Søgning i overvågningslogfil.](../media/auditlogsearch1.png)
  
4. Konfigurer følgende søgekriterier:

   1. **Startdato** **og Slutdato**. Vælg en dato og et tidsinterval for at få vist de hændelser, der er opstået inden for den pågældende periode.  

   2. **Aktiviteter**. Lad dette felt være tomt, så søgningen returnerer overvågningsposter for alle aktiviteter. Dette er nødvendigt for at returnere eventuelle overvågningsposter, der er relateret til kunde lockboxanmodninger og tilsvarende aktivitet udført af Microsoft-teknikere.

   3. **Brugere**. Lad dette felt være tomt.

   4. **Fil, mappe eller websted**. Lad dette felt være tomt.

5. Klik **på Søg** for at køre søgningen ved hjælp af dine søgekriterier.

    Søgeresultaterne vises efter et øjeblik. Der tilføjes flere søgeresultater på siden, indtil søgningen er fuldført.

6. Klik på overskriften i **kolonnen Aktivitet** for at sortere resultaterne alfabetisk baseret på værdierne i **kolonnen** Aktivitet.

7. Rul ned, og se efter overvågningsposter med en aktivitet **for Set-AccessToCustomerDataRequest**. Poster med denne aktivitet er relateret til en godkender i organisationen, der godkender eller afviser en kunde lockboxanmodning.

8. Alternativt kan du klikke på overskriften i **kolonnen Bruger** for at sortere resultaterne alfabetisk ved hjælp af værdierne i **kolonnen** Bruger. Se efter værdien af **Microsoft-operatoren**, som angiver aktiviteter, der er udført af en Microsoft-tekniker som svar på en godkendt kunde lockboxanmodning. Kolonnen **Aktivitet** viser den handling, der udføres af teknikeren.

      ![Filtrer efter "Microsoft-operator" for at få vist overvågningsposter](../media/CustomerLockbox10.png)

9. Klik på en overvågningspost på listen over resultater for at få den vist.

### <a name="export-the-audit-log-search-results"></a>Eksportér søgeresultaterne fra overvågningsloggen

Du kan også eksportere søgeresultaterne fra overvågningsloggen til en CSV-fil og derefter åbne filen i Excel for at bruge filtrerings- og sorteringsfunktionerne til at gøre det nemmere at finde og få vist overvågningsposter, der er relateret til en kunde lockboxanmodning.

Hvis du vil eksportere overvågningsposter, skal du bruge de foregående trin til at søge i overvågningsloggen. Når søgningen er fuldført, skal **du vælge > Hent** alle resultater øverst på siden med søgeresultater. Når eksporten er fuldført, kan du hente CSV-filen til din lokale computer. Du kan finde en mere detaljeret vejledning [under Eksportere, konfigurere og få vist overvågningslogposter](export-view-audit-log-records.md).

Når du har hentet filen, kan du åbne den i Excel og derefter filtrere på kolonnen Handlinger for at  få vist overvågningsposter for **Set-AccessToCustomerDataRequest-aktiviteter**. Du kan også filtrere på kolonnen **UserIds** (med værdien **Microsoft Operator**) for at få vist overvågningsposter for aktiviteter, der er udført af Microsoft-teknikere.

> [!NOTE]
> Når du får vist overvågningsposter i CSV-filen, er yderligere oplysninger indeholdt i **kolonnen AuditData** . Oplysningerne i denne kolonne er indeholdt i et JSON-objekt, som indeholder flere egenskaber, der er konfigureret som *egenskab:* værdipar adskilt af kommaer. Du kan bruge JSON-transformeringsfunktionen i Power Query-editor i Excel til at opdele hver egenskab i JSON-objektet i kolonnen **AuditData** i flere kolonner, så hver egenskab har sin egen kolonne. Det gør det nemmere at fortolke disse oplysninger. Du kan finde flere oplysninger [i Formatere den eksporterede overvågningslog ved hjælp af Power Query-editor](export-view-audit-log-records.md#step-2-format-the-exported-audit-log-using-the-power-query-editor).

### <a name="use-powershell-to-search-and-export-audit-records"></a>Brug PowerShell til at søge efter og eksportere overvågningsposter

Et alternativ til at bruge overvågningssøgeværktøjet i Microsoft 365 Overholdelsescenter er at køre [Search-UnifiedAuditLog-cmdlet'en](/powershell/module/exchange/search-unifiedauditlog) Exchange Online PowerShell. En fordel ved at bruge PowerShell er, at du specifikt kan søge efter **Set-AccessToCustomerDataRequest-aktiviteter** eller aktiviteter, der udføres af Microsoft-teknikere relateret til en kunde-Lockbox-anmodning.

Når du [har forbindelse til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell), skal du køre en af følgende kommandoer. Erstat pladsholderne med et bestemt datointerval.

Søg efter `Set-AccessToCustomerDataRequest` aktiviteter

```powershell
Search-UnifiedAuditLog -StartDate xx/xx/xxxx -EndDate xx/xx/xxxx -Operations Set-AccessToCustomerDataRequest
```

Søg efter aktiviteter udført af Microsoft-teknikere

```powershell
Search-UnifiedAuditLog -StartDate xx/xx/xxxx -EndDate xx/xx/xxxx -UserIds "Microsoft Operator"
```

Du kan finde flere oplysninger og eksempler under [Brug PowerShell til at søge efter og eksportere overvågningslogposter](export-view-audit-log-records.md#use-powershell-to-search-and-export-audit-log-records).

Vi har også leveret et PowerShell-script, som du kan bruge til at søge i overvågningsloggen og eksportere resultaterne til en CSV-fil. Få mere at vide under [Brug et PowerShell-script til at søge i overvågningsloggen](audit-log-search-script.md).

### <a name="audit-record-for-a-customer-lockbox-request"></a>Overvågningspost for en kunde lockboxanmodning

Når en person i organisationen godkender eller afviser en kunde lockboxanmodning, logføres overvågningsposten i overvågningsloggen med følgende oplysninger.

| Egenskaben Overvågningspost| Beskrivelse|
|:---------- |:----------|
| Dato       | Dato og klokkeslæt for, hvornår kunde lockboxanmodningen blev godkendt eller afvist.
| IP-adresse | IP-adressen på den computer, som godkenderen brugte til at godkende eller afvise en anmodning. |
| Bruger       | Tjenestekontoen BOXServiceAccount@\[customerforest.prod.outlook.com\].            |
| Aktivitet   | Set-AccessToCustomerDataRequest; dette er den overvågningsaktiviteter, der logføres, når du godkender eller afviser en kunde lockboxanmodning.                                |
| Element       | Guid for kunde-lockboxanmodningen                             |

Følgende skærmbillede viser et eksempel på en overvågningspost, der svarer til en godkendt kunde lockboxanmodning. Hvis en kunde lockboxanmodning blev afvist, så ville værdien af `ApprovalDecision` parameteren være `Deny`.

![Overvågningspost for en godkendt kunde lockboxanmodning.](../media/CustomerLockbox9.png)

### <a name="audit-record-for-an-action-performed-by-a-microsoft-engineer"></a>Overvågningspost for en handling, der udføres af en Microsoft-tekniker

De handlinger, der udføres af en Microsoft-tekniker, efter at en kunde lockboxanmodning er godkendt (og som kan resultere i adgang til kundeindhold), logføres i overvågningsloggen. Disse poster indeholder følgende oplysninger.

| Egenskaben Overvågningspost| Beskrivelse|
|:---------- |:----------|
| Dato       | Dato klokkeslæt for, hvornår handlingen blev udført. Det tidspunkt, hvor denne handling blev udført, vil være inden for 4 timer fra det tidspunkt, hvor kunde lockboxanmodningen blev godkendt.              |
| IP-adresse | IP-adressen på den computer, som Microsoft-tekniker har brugt. |
| Bruger       | Microsoft Operator; denne værdi angiver, at posten er relateret til en kunde lockboxanmodning.                                  |
| Aktivitet   | Navnet på den aktivitet, der er udført af Microsoft-teknikeren.|
| Element       | \<empty\>                                             |

## <a name="frequently-asked-questions"></a>Ofte stillede spørgsmål

### <a name="which-microsoft-365-services-does-customer-lockbox-apply-to"></a>Hvilke Microsoft 365 tjenester gælder Kunde lockbox for?

Kunde lockbox understøttes i øjeblikket i Exchange Online, SharePoint Online, OneDrive for Business og Teams.

### <a name="is-customer-lockbox-available-to-all-customers"></a>Er kundelåsfeltet tilgængeligt for alle kunder?

Kunde-Lockbox er inkluderet i Microsoft 365- eller Office 365 E5-abonnementerne og kan føjes til andre planer med et abonnement på Information Protection og Compliance eller et abonnement på avanceret overholdelse. Se [Planer og priser for at](https://products.office.com/business/office-365-enterprise-e5-business-software) få flere oplysninger.

### <a name="what-is-customer-content"></a>Hvad er kundeindhold?

Kundeindhold er de data, der oprettes af brugere Microsoft 365 tjenester og programmer. Eksempler på kundeindhold omfatter:

- Brødtekst i mails eller vedhæftede filer i mails

- SharePoint webstedsindhold

- Oplysninger i brødteksten i en SharePoint fil

- Skype for Business brødteksten i præsentationsfilen

- Chat eller talesamtaler

- Tekst indtastet i Teams og Teams-kanaler, f.eks. 1:1 chats, gruppechats, delte kanaler, private kanaler og mødechat

- Andre data, der er Teams i chattråde, f.eks. kodestykker, billeder, lyd- og videomeddelelser og links

- App- og botdata i Teams chats og Teams kanaler

- Teams aktivitetsfeed

- Teams og afskrifter af møder

- Telefonsvarer

- Filer, der er sendt Teams chatsamtaler og Teams kanaler

- Kundegenererede blob- eller strukturerede lagerdata (f.eks. SQL Containers)

- Sikkerhedsoplysninger, som ejes af kunder (f.eks. certifikater, krypteringsnøgler og adgangskoder)

- Afslutninger og alle efterfølgende afslutninger, hvis kundeindhold forbliver

Du kan finde flere oplysninger om Office 365 i [Office 365 Sikkerhedscenter](https://products.office.com/business/office-365-trust-center-privacy/).

### <a name="who-is-notified-when-there-is-a-request-to-access-my-content"></a>Who får besked, når der er en anmodning om at få adgang til mit indhold?

Globale administratorer og alle, der er tildelt administratorrollen for adgang til kundelåsfeltet, underrettes. Dette er også de samme brugere, der kan godkende i forbindelse med kunde lockboxanmodninger.

### <a name="who-can-approve-or-reject-these-requests-in-my-organization"></a>Who kan godkende eller afvise disse anmodninger i min organisation?

Globale administratorer og alle, der er tildelt rollen som administrator for adgang til kundelåsfeltet, kan godkende kunde lockboxanmodninger. Kunder styrer disse rolletildelinger i deres organisationer.

### <a name="how-do-i-opt-in-to-customer-lockbox"></a>Hvordan gør jeg du tilmelde dig kunde-lockbox?

En global administrator kan aktivere og konfigurere kunde lockbox i Microsoft 365 Administration.

### <a name="if-i-approve-a-customer-lockbox-request-what-can-the-engineer-do-and-how-will-i-know-what-the-microsoft-engineer-did"></a>Hvis jeg godkender en kunde-lockboxanmodning, hvad kan teknikeren gøre, og hvordan kan jeg så vide, hvad Microsoft-teknikeren gjorde?

Når du godkender en kunde lockboxanmodning, gav Microsoft-teknikeren disse nødvendige rettigheder til at få adgang til kundeindhold ved hjælp af forhåndsgodkendte cmdlet'er. Handlinger, der er foretaget af Microsoft-teknikere som svar på kunde lockboxanmodninger, logføres og er tilgængelige i overvågningsloggen i Security & Compliance Center.

### <a name="how-do-i-know-that-microsoft-follows-the-approval-process"></a>Hvordan gør jeg vide, at Microsoft følger godkendelsesprocessen?

Du kan krydsreference de meddelelser om godkendelse af mails, der sendes til administratorer og godkendere i organisationen, med historikken for kunde lockboxanmodning [i Microsoft 365 Administration](https://go.microsoft.com/fwlink/p/?linkid=2024339).

Kunde lockbox er inkluderet i den nyeste [SOC 1 SSAE 16-overvågningsrapport](https://servicetrust.microsoft.com/ViewPage/MSComplianceGuide?command=Download&downloadType=Document&downloadId=91592749-e86a-43ac-801e-121382614681&docTab=4ce99610-c9c0-11e7-8c2c-f908a777fa4d_SOC%20%2F%20SSAE%2016%20Reports). Du kan finde flere oplysninger i de seneste rapporter i [Microsoft Service Trust Portal](https://servicetrust.microsoft.com/ViewPage/MSComplianceGuide?command=Download&downloadType=Document&downloadId=91592749-e86a-43ac-801e-121382614681&docTab=4ce99610-c9c0-11e7-8c2c-f908a777fa4d_SOC%20%2F%20SSAE%2016%20Reports).

### <a name="can-microsoft-modify-the-list-of-approvers-for-my-tenant-if-not-how-is-it-prevented"></a>Kan Microsoft ændre listen over godkendere for min lejer? Hvis ikke, hvordan er det så forhindret?

Kun en global administrator i organisationen kan angive, hvem der kan godkende kunde lockboxanmodninger. Det betyder, at kun medlemmerne af Global administrator i Azure Active Directory kan angive, hvem der kan godkende anmodning. Medlemskab af Global administrator gruppe i Azure Active Directory administreres kun af din organisation.

### <a name="what-if-i-need-more-information-about-a-content-access-request-to-approve-it"></a>Hvad gør jeg, hvis jeg har brug for flere oplysninger om en anmodning om adgang til indhold for at godkende den?

Hver kunde lockboxanmodning indeholder et Microsoft 365 serviceanmodningsnummer. Du kan kontakte Microsoft Support og henvise til dette servicenummer for at få flere oplysninger om anmodningen.

### <a name="when-a-customer-lockbox-request-is-approved-how-long-are-the-permissions-valid"></a>Hvor lang tid er tilladelserne gyldige, når en kunde lockboxanmodning godkendes?

I øjeblikket er den maksimale periode for de adgangstilladelser, der tildeles Microsoft-teknikeren, 4 timer. Microsoft-teknikeren kan også anmode om en kortere periode.

### <a name="how-can-i-get-a-history-of-all-customer-lockbox-requests"></a>Hvordan får jeg en oversigt over alle kunde lockboxanmodninger?

Alle kunde lockboxanmodninger vises i [Microsoft 365 Administration](https://go.microsoft.com/fwlink/p/?linkid=2024339).

### <a name="how-do-i-correlate-the-content-access-requests-with-the-related-audit-logs"></a>Hvordan gør jeg du korrelere anmodninger om adgang til indhold med de relaterede overvågningslogge?

Aktivitetsfeed for Overholdelsescenter indeholder logaktiviteter for kunde-lockbox. Kunder kan krydsreference til aktiviteter i kunde lockboxloggen fra aktivitetsfeedet i forhold til den mailanmodning, de modtager.

### <a name="what-happens-when-a-customer-doesnt-respond-to-a-customer-lockbox-request"></a>Hvad sker der, når en kunde ikke svarer på en kunde lockboxanmodning?

Kunde lockboxanmodninger har en standardvarighed på 12 timer. Hvis du ikke besvarer en anmodning inden for 12 timer, udløber anmodningen.

### <a name="what-does-microsoft-do-when-a-customer-rejects-a-customer-lockbox-request"></a>Hvad gør Microsoft, når en kunde afviser en kunde lockboxanmodning?

Hvis en kunde afviser en kunde lockboxanmodning, sker der ingen adgang til kundens indhold. Hvis en bruger i organisationen fortsat oplever et serviceproblem, der kræver, at Microsoft skal have adgang til kundeindhold for at løse problemet, kan tjenesteproblemet bevares, og Microsoft informerer brugeren om dette.

### <a name="how-do-i-set-up-alerts-whenever-a-request-has-been-approved"></a>Hvordan gør jeg du konfigurerer beskeder, når en anmodning er blevet godkendt?

Der er ingen indbygget indstilling til at give administratorer besked. Administratorer kan dog konfigurere beskeder ved hjælp af [Microsoft Defender for Cloud Apps](/cloud-app-security/getting-started-with-cloud-app-security#to-create-policies).

### <a name="does-customer-lockbox-protect-against-data-requests-from-law-enforcement-agencies-or-other-third-parties"></a>Beskytter kunde lockbox mod dataanmodninger fra håndhævende myndigheder eller andre tredjeparter?

Nej. Microsoft tager anmodninger fra tredjeparter om kundedata alvorligt. Som cloud-serviceudbyder anbefaler Microsoft altid, at kundedata beskyttes. I tilfælde af at vi får en stævning, forsøger Microsoft altid at omdirigere tredjeparten til kunden for at hente oplysningerne. (Læs Brad Smiths blog: [Beskyttelse af kundedata fra offentlige myndigheder](https://blogs.microsoft.com/blog/2013/12/04/protecting-customer-data-from-government-snooping/)). Vi udgiver jævnligt [detaljerede oplysninger om](https://www.microsoft.com/corporate-responsibility/lerr) de anmodninger om håndhævelse af lovgivningen, som Microsoft modtager.

Se [Microsoft Center for sikkerhed og beskyttelse](https://www.microsoft.com/trustcenter/default.aspx) vedrørende anmodninger om data fra tredjeparter og afsnittet "Videregivelse af kundedata" i [vilkårene for onlinetjenester](https://www.microsoft.com/Licensing/product-licensing/products.aspx) for at få flere oplysninger.

### <a name="how-does-microsoft-ensure-that-a-member-of-its-staff-doesnt-have-standing-access-to-customer-content-in-office-365-applications"></a>Hvordan sikrer Microsoft, at en medarbejder ikke har stående adgang til kundeindhold i Office 365 programmer?

Microsoft implementerer omfattende sikkerhedsforanstaltninger gennem adgangskontrolsystemer og programmer til at identificere og håndtere forsøg på at omgå disse adgangskontrolsystemer. Microsoft 365 fungerer med principperne for mindst rettigheder og just-in-time adgang. Derfor er der ingen Microsoft-medarbejdere, der har tilladelse til løbende at få adgang til kundeindhold. Hvis der gives tilladelse, gælder det i en begrænset periode.

Microsoft 365 bruger et adgangskontrolsystem kaldet *Lockbox* til at behandle anmodninger om tilladelser, der giver mulighed for at udføre driftsmæssige og administrative funktioner i tjenesten. En operator skal anmode om adgang til kundeindhold ved hjælp af Lockbox, hvilket derefter kræver, at en anden person skal handle på anmodningen (f.eks. godkende den), før der gives adgang. Den anden person kan ikke være anmoder og skal udpeges til at godkende adgang til kundens indhold. Kun hvis anmodningen godkendes, får operatoren midlertidig adgang til kundens indhold. Når udvidelsesperioden udløber, tilbagekalder Lockbox adgangen.

Se vilkårene for [onlinetjenester for at](https://www.microsoft.com/licensing/product-licensing/products) få mere at vide om Microsofts generelle sikkerhedspraksisser.

### <a name="under-what-circumstances-do-microsoft-engineers-need-access-to-my-content"></a>Under hvilke omstændigheder skal Microsoft-teknikere have adgang til mit indhold?

Det mest almindelige scenarie, hvor Microsoft-teknikere skal have adgang til kundeindhold, er, når kunden anmoder om support, der kræver adgang til fejlfinding. Et grundlæggende princip for Microsoft 365 er, at tjenesten fungerer uden Microsofts adgang til kundeindhold. Næsten alle tjenestehandlinger, der udføres af Microsoft, er fuldt automatiseret, og menneskelig deltagelse er stærkt kontrolleret og abstrakt væk fra kundeindhold. Målet med at Microsoft 365 er at få adgang til kundeindhold for at understøtte tjenesten, er ikke nødvendigt, før kunden godkender en bestemt anmodning om Microsoft-adgang.

### <a name="i-already-thought-my-data-was-secure-with-the-microsoft-cloud-so-why-do-i-need-customer-lockbox"></a>Jeg troede allerede, at mine data var sikre med Microsoft-skyen, så hvorfor skal jeg bruge kunde lockbox?

Kunde lockbox giver et ekstra lag af kontrol ved at give kunderne mulighed for at give eksplicit adgangsgodkendelse for tjenestehandlinger. Ved at vise, at der er indført procedurer for eksplicitte dataadgangstilladelser, hjælper kunde lockbox også kunderne med at opfylde visse overholdelsesforpligtelser som HIPAA og FEDRAMP.
