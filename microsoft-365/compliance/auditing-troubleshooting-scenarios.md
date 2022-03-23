---
title: Søg i overvågningsloggen for at foretage fejlfinding af almindelige scenarier
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MET150
- MOE150
ms.custom:
- seo-marvel-apr2020
- admindeeplinkEXCHANGE
description: Få mere at vide om, hvordan du Microsoft 365 søgeværktøjet til overvågningslogfiler til at foretage fejlfinding af almindelige supportproblemer med mailkonti.
ms.openlocfilehash: 496729c7955448519d6cb1447e08b5a4b15aa655
ms.sourcegitcommit: bae72428d229827cba4c807d9cd362417afbcccb
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/02/2022
ms.locfileid: "63587699"
---
# <a name="search-the-audit-log-to-investigate-common-support-issues"></a>Søg i overvågningsloggen for at undersøge almindelige supportproblemer

I denne artikel beskrives det, hvordan du kan bruge søgeværktøjet til overvågningslogfiler til at hjælpe dig med at undersøge almindelige supportproblemer. Dette omfatter brug af overvågningsloggen til at:

- Find IP-adressen på den computer, der bruges til at få adgang til en kompromitteret konto
- Finde ud af, hvem der har konfigureret videresendelse af mail for en postkasse
- Afgør, om en bruger har slettet mailelementer i sin postkasse
- Finde ud af, om en bruger har oprettet en indbakkeregel
- Undersøg, hvorfor en bruger uden for organisationen har udført et vellykket logon
- Søg efter postkasseaktiviteter, der udføres af brugere med licenser, der ikke er E5
- Søge efter postkasseaktiviteter, der udføres af stedfortrædere

## <a name="using-the-audit-log-search-tool"></a>Brug af søgeværktøjet til overvågningslogfiler

Alle de fejlfindingsscenarier, der er beskrevet i denne artikel, er baseret på brug af søgeværktøjet til overvågningslogfiler i Microsoft 365 Overholdelsescenter. I dette afsnit beskrives de tilladelser, der kræves for at søge i overvågningsloggen, og trinnene til at få adgang til og køre overvågningsloggens søgninger. Hvert scenarieafsnit beskriver, hvordan du konfigurerer en søgeforespørgsel til overvågningsloggen, og hvad du skal lede efter i de detaljerede oplysninger i overvågningsposterne, der opfylder søgekriterierne.

### <a name="permissions-required-to-use-the-audit-log-search-tool"></a>Tilladelser, der kræves for at bruge overvågningsloggens søgeværktøj

Du skal have tildelt rollen View-Only overvågningslogfiler eller Overvågningslogfiler i en Exchange Online at søge i overvågningsloggen. Disse roller **tildeles** som standard rollegrupperne Styring af overholdelse og Organisationsadministration på siden Tilladelser <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">i Exchange Administration</a>. Globale administratorer i Office 365 og Microsoft 365 tilføjes automatisk som medlemmer af rollegruppen Organisationsadministration i Exchange Online. Du kan finde flere oplysninger [i Administrere rollegrupper i Exchange Online](/Exchange/permissions-exo/role-groups).

### <a name="running-audit-log-searches"></a>Køre søgninger i overvågningsloggen

I dette afsnit beskrives de grundlæggende funktioner til oprettelse og kørsel af søgninger i overvågningslogfiler. Brug denne vejledning som et udgangspunkt for hvert fejlfindingsscenarie i denne artikel. Du kan finde en mere detaljeret trinvis vejledning under [Søge i overvågningsloggen](search-the-audit-log-in-security-and-compliance.md#step-1-run-an-audit-log-search).

1. Gå til og <https://compliance.microsoft.com/auditlogsearch> log på med din arbejds- eller skolekonto.
  
    **Siden Overvågning** vises.
  
    ![Konfigurer kriterier, og vælg derefter Søg for at køre søgningen.](../media/AuditLogSearchPage1.png)
  
2. Du kan konfigurere følgende søgekriterier. Hvert fejlfindingsscenarie i denne artikel anbefaler specifikke retningslinjer for konfiguration af disse felter.
  
   a. **Startdato og** Slutdato **: Vælg en dato** og et tidsinterval for at få vist de hændelser, der er opstået inden for den pågældende periode. De seneste syv dage er valgt som standard. Dato og klokkeslæt vises i formatet UTC (Coordinated Universal Time). Det maksimale datointerval, du kan angive, er 90 dage.

   b. **Aktiviteter:** Vælg rullelisten for at få vist de aktiviteter, du kan søge efter. Når du har kørt søgningen, vises kun overvågningsposterne for de markerede aktiviteter. Hvis du **vælger Vis resultater for alle aktiviteter, vises** resultaterne for alle aktiviteter, der opfylder de andre søgekriterier. Du skal også lade feltet være tomt i nogle af fejlfindingsscenarierne.
  
    c. **Brugere:** Klik i dette felt, og vælg derefter en eller flere brugere, der skal vises søgeresultater for. Overvågningsposter for den valgte aktivitet, der er udført af de brugere, du vælger i dette felt, vises på listen over resultater. Lad dette felt være tomt for at returnere poster for alle brugere (og tjenestekonti) i organisationen.
  
    d. **Fil, mappe eller websted:** Skriv en del af eller hele navnet på en fil eller mappe for at søge efter aktivitet relateret til den fil i mappen, der indeholder det angivne nøgleord. Du kan også angive en URL-adresse til en fil eller mappe. Hvis du bruger en URL-adresse, skal du sørge for at skrive den fulde URL-adressesti. Hvis du kun skriver en del af URL-adressen, skal du ikke medtage nogen specialtegn eller mellemrum. Lad dette felt være tomt for at returnere poster for alle filer og mapper i organisationen. Dette felt udfyldes ikke i alle fejlfindingsscenarier i denne artikel.
  
3. Vælg **Søg** for at køre søgningen ved hjælp af dine søgekriterier.
  
    Søgeresultaterne indlæses, og efter et øjeblik vises de på en side i overvågningsloggens søgeværktøj. Hvert af afsnittene i denne artikel indeholder vejledning om ting, du skal lede efter i forbindelse med det specifikke fejlfindingsscenarie.

    Du kan finde flere oplysninger om visning og eksport af søgeresultater fra overvågningsloggen i:

    - [Vis søgeresultater](search-the-audit-log-in-security-and-compliance.md#step-2-view-the-search-results)
  
    - [Eksportér søgeresultater](search-the-audit-log-in-security-and-compliance.md#step-3-export-the-search-results-to-a-file)

## <a name="find-the-ip-address-of-the-computer-used-to-access-a-compromised-account"></a>Find IP-adressen på den computer, der bruges til at få adgang til en kompromitteret konto

DEN IP-adresse, der svarer til en aktivitet, der er udført af en bruger, medtages i de fleste overvågningsposter. Oplysninger om den anvendte klient findes også i overvågningsposten.

Sådan konfigurerer du en søgeforespørgsel i overvågningsloggen for dette scenarie:

**Aktiviteter:** Hvis det er relevant for din sag, skal du vælge en bestemt aktivitet, du vil søge efter. Til fejlfinding af kompromitterede konti skal du overveje at vælge den **bruger, der er logget på postkasseaktivitet** **under Exchange postkasseaktiviteter**. Dette returnerer overvågningsposter, der viser den IP-adresse, der blev brugt, når du loggede på postkassen. Ellers skal du lade dette felt være tomt for at returnere overvågningsposter for alle aktiviteter. 

> [!TIP]
> Hvis du lader dette felt være tomt, returneres **UserLoggedIn-aktiviteter**, som er en Azure Active Directory aktivitet, der angiver, at nogen har logget på en brugerkonto. Brug filtrering i søgeresultaterne til at få vist **UserLoggedIn-overvågningsposterne** .

**Startdato og** **Slutdato: Vælg et** datointerval, der gælder for din undersøgelse.

**Brugere:** Hvis du undersøger en kompromitteret konto, skal du vælge den bruger, hvis konto er blevet kompromitteret. Dette returnerer overvågningsposter for aktiviteter, der er udført af den pågældende brugerkonto.

**Fil, mappe eller websted:** Lad dette felt være tomt.

Når du har kørt søgningen, vises IP-adressen for hver aktivitet i **kolonnen IP-adresse** i søgeresultaterne. Vælg posten i søgeresultaterne for at få vist mere detaljerede oplysninger på pop op-siden.

## <a name="determine-who-set-up-email-forwarding-for-a-mailbox"></a>Finde ud af, hvem der har konfigureret videresendelse af mail for en postkasse

Når videresendelse af mail er konfigureret for en postkasse, videresendes de mails, der sendes til postkassen, til en anden postkasse. Meddelelser kan videresendes til brugere i eller uden for organisationen. Når videresendelse af mail er konfigureret i en postkasse, Exchange Online den underliggende cmdlet, der bruges, **Set-Mailbox**.

Sådan konfigurerer du en søgeforespørgsel i overvågningsloggen for dette scenarie:

**Aktiviteter:** Lad dette felt være tomt, så søgningen returnerer overvågningsposter for alle aktiviteter. Dette er nødvendigt for at returnere eventuelle overvågningsposter, der er relateret til **Set-Mailbox-cmdlet'en** .

**Startdato og** **Slutdato: Vælg et** datointerval, der gælder for din undersøgelse.

**Brugere:** Medmindre du undersøger et problem med videresendelse af mail for en bestemt bruger, skal du lade feltet være tomt. Dette hjælper dig med at identificere, om videresendelse af mail er konfigureret for en bruger.

**Fil, mappe eller websted:** Lad dette felt være tomt.

Når du har kørt søgningen, skal du **vælge Filtrer** resultater på siden med søgeresultater. I feltet under **kolonneoverskriften** Aktivitet skal du skrive **Set-Mailbox** , så kun overvågningsposter, der er relateret til **cmdlet'en Set-Mailbox** , vises.

![Filtrering af resultaterne af en søgning i overvågningsloggen.](../media/emailforwarding1.png)

På dette tidspunkt skal du se på detaljerne for hver overvågningspost for at afgøre, om aktiviteten er relateret til videresendelse af mail. Vælg overvågningsposten for at få **vist** pop op-siden Detaljer, og vælg derefter **Flere oplysninger**. Følgende skærmbillede og beskrivelser fremhæver de oplysninger, der angiver, at videresendelse af mail var angivet på postkassen.

![Detaljerede oplysninger fra overvågningsposten.](../media/emailforwarding2.png)

a. I feltet **ObjectId** vises aliasset for den postkasse, som videresendelse af mail blev konfigureret på. Denne postkasse vises også på kolonnen **Element** på siden med søgeresultater.

b. I feltet **Parametre** angiver værdien *VideresendelseSmtpAddress* , at videresendelse af mail er angivet på postkassen. I dette eksempel videresendes mails til den mailadresse, mike@contoso.com, som er uden for alpinehouse.onmicrosoft.com organisation.

c. Værdien *True* for *parameteren DeliverToMailboxAndForward* angiver, at en kopi af meddelelsen leveres til sarad@alpinehouse.onmicrosoft.com og videresendes til den mailadresse, der er angivet af parameteren *ForwardingSmtpAddress*, som i dette eksempel er mike@contoso.com. Hvis værdien for *parameteren DeliverToMailboxAndForward* er angivet til *Falsk*, videresendes mail kun til den adresse, der er angivet af parameteren *ForwardingSmtpAddress* . Den leveres ikke til den postkasse, der er angivet i **feltet Objekt-id** .

d. Feltet **UserId** angiver den bruger, der har angivet videresendelse af mail på den postkasse, der er angivet i **feltet ObjectId** . Denne bruger vises også i **kolonnen Bruger** på siden med søgeresultater. I dette tilfælde ser det ud til, at ejeren af postkassen har konfigureret videresendelse af mail på sin postkasse.

Hvis du finder ud af, at videresendelse af mail ikke skal indstilles på postkassen, kan du fjerne den ved at køre følgende kommando i Exchange Online PowerShell:

```powershell
Set-Mailbox <mailbox alias> -ForwardingSmtpAddress $null 
```

Du kan finde flere oplysninger om parametrene for videresendelse af mail i [artiklen Set-Mailbox](/powershell/module/exchange/set-mailbox) .

## <a name="determine-if-a-user-deleted-email-items"></a>Afgør, om en bruger har slettet mailelementer

Fra januar 2019 slår Microsoft som standard logføring af postkassekontrol til for alle brugere Office 365 Microsoft-organisationer. Det betyder, at visse handlinger, der udføres af postkasseejere, logføres automatisk, og de tilsvarende postkassekontrolposter er tilgængelige, når du søger efter dem i postkassens overvågningslog. Før overvågning af postkasse var aktiveret som standard, skulle du manuelt aktivere det for hver brugerpostkasse i organisationen. 

De postkassehandlinger, der logføres som standard, omfatter postkassehandlingerne BlødSlette og HardDelete, der udføres af postkasseejere. Det betyder, at du kan bruge følgende trin til at søge i overvågningsloggen efter hændelser, der er relateret til slettede mailelementer. Du kan finde flere oplysninger om overvågning af postkasser som standard under [Administrere postkasserevision](enable-mailbox-auditing.md).

Sådan konfigurerer du en søgeforespørgsel i overvågningsloggen for dette scenarie:

**Aktiviteter:** Under **Exchange skal du** vælge en eller begge af følgende aktiviteter:

- **Slettede meddelelser fra mappen Slettet post:** Denne aktivitet svarer til **overvågningshandlingen Blødslette** i postkassen. Denne aktivitet logføres også, når en bruger sletter et element permanent ved at markere det og trykke **på Skift+Delete**. Når et element er blevet slettet permanent, kan brugeren gendanne det, indtil opbevaringsperioden for det slettede element udløber.

- **Meddelelser fjernet fra postkasse:** Denne aktivitet svarer til **postkasserevisionshandlingen HardDelete** . Dette logføres, når en bruger fjerner et element fra mappen Genoprettelige elementer. Administratorer kan bruge værktøjet Indholdssøgning i Sikkerheds- og overholdelsescenteret til at søge efter og gendanne slettede elementer, indtil opbevaringsperioden for slettede elementer udløber eller længere, hvis brugerens postkasse er i venteposition.

**Startdato og** **Slutdato: Vælg et** datointerval, der gælder for din undersøgelse.

**Brugere:** Hvis du vælger en bruger i dette felt, returnerer søgeværktøjet til overvågningsloggen overvågningsposter for mailelementer, der er blevet slettet (blødslettet eller hardslettet) af den bruger, du angiver. Nogle gange er den bruger, der sletter en mail, muligvis ikke postkasseejeren.

**Fil, mappe eller websted:** Lad dette felt være tomt.

Når du har kørt søgningen, kan du filtrere søgeresultaterne for at få vist overvågningsposterne for blød-slettede elementer eller for elementer, der er blevet hårdt slettet. Vælg overvågningsposten for at få **vist** pop op-siden Detaljer, og vælg derefter **Flere oplysninger**. Yderligere oplysninger om det slettede element, f.eks. emnelinjen og placeringen af elementet, da det blev slettet, vises i feltet **BerørteWebsteder** . Følgende skærmbilleder viser et eksempel på feltet **Påvirkede** elementer fra et blød-slettet element og et hårdt slettet element.

**Eksempel på feltet PåvirkedeWebsteder for blød-slettet element**

![Overvågningspost for blød-slettet element.](../media/softdeleteditem.png)

**Eksempel på feltet PåvirkedeWebsteder for permanent slettet element**

![Oversepost for hård slettede mailelement.](../media/harddeleteditem.png)

### <a name="recover-deleted-email-items"></a>Gendan slettede mailelementer

Brugere kan gendanne blød-slettede elementer, hvis opbevaringsperioden for slettede elementer ikke er udløbet. I Exchange Online er standardopbevaringsperioden for slettede elementer 14 dage, men administratorer kan øge denne indstilling til maksimalt 30 dage. Peg brugerne til artiklen [Gendan slettede elementer eller mails i Outlook på internettet](https://support.office.com/article/Recover-deleted-items-or-email-in-Outlook-Web-App-C3D8FC15-EEEF-4F1C-81DF-E27964B7EDD4) for at få en vejledning i at gendanne slettede elementer.

Som beskrevet tidligere kan administratorer muligvis gendanne elementer, der er blevet slettet permanent, hvis opbevaringsperioden for slettede elementer ikke er udløbet, eller hvis postkassen er i venteposition, i hvilket tilfælde elementer bevares, indtil varigheden af ventepositionen udløber. Når du kører en indholdssøgning, returneres blød-slettede og hård-slettede elementer i mappen Genoprettelige elementer i søgeresultaterne, hvis de svarer til søgeforespørgslen. Du kan finde flere oplysninger om at køre [indholdssøgninger i Indholdssøgning Office 365](content-search.md).

> [!TIP]
> Hvis du vil søge efter slettede mailelementer, skal du søge efter hele eller dele af emnelinjen, der vises i feltet **Berørtepunkter** i overvågningsposten.

## <a name="determine-if-a-user-created-an-inbox-rule"></a>Finde ud af, om en bruger har oprettet en indbakkeregel

Når brugerne opretter en indbakkeregel for deres Exchange Online postkasse, gemmes en tilsvarende overvågningspost i overvågningsloggen. Du kan finde flere oplysninger om indbakkeregler i:

- [Brug indbakkeregler i Outlook på internettet](https://support.office.com/article/use-inbox-rules-in-outlook-on-the-web-8400435c-f14e-4272-9004-1548bb1848f2)
- [Administrere mails i Outlook ved hjælp af regler](https://support.office.com/article/Manage-email-messages-by-using-rules-C24F5DEA-9465-4DF4-AD17-A50704D66C59)

Sådan konfigurerer du en søgeforespørgsel i overvågningsloggen for dette scenarie:

**Aktiviteter:** Under **Exchange skal du** vælge en eller begge af følgende aktiviteter:

- **Ny indbakkeRegel Opret ny indbakkeregel ud fra Outlook Web App**. Denne aktivitet returnerer overvågningsposter, når indbakkeregler oprettes ved hjælp Outlook webapp eller Exchange Online PowerShell.

- **Opdaterede indbakkeregler fra Outlook klient**. Denne aktivitet returnerer overvågningsposter, når indbakkeregler oprettes, ændres eller fjernes ved hjælp Outlook-klienten på computeren.

**Startdato og** **Slutdato: Vælg et** datointerval, der gælder for din undersøgelse.

**Brugere:** Medmindre du undersøger en bestemt bruger, skal du lade feltet være tomt. Dette hjælper dig med at identificere nye indbakkeregler, der er konfigureret af enhver bruger.

**Fil, mappe eller websted:** Lad dette felt være tomt.

Når du har kørt søgningen, vises alle overvågningsposter for denne aktivitet i søgeresultaterne. Vælg en overvågningspost for at få **vist pop** op-siden Detaljer, og vælg derefter **Flere oplysninger**. Oplysninger om indstillinger for indbakkeregel vises i **feltet** Parametre. Følgende skærmbillede og beskrivelser fremhæver oplysningerne om indbakkeregler.

![Overvågningspost for ny indbakkeregel.](../media/NewInboxRuleRecord.png)

a. I **feltet ObjectId** vises det fulde navn på indbakkereglen. Dette navn indeholder aliasset for brugerens postkasse (f.eks. SaraD) og navnet på indbakkereglen (f.eks. "Flyt meddelelser fra administrator").

b. I **feltet** Parametre vises betingelsen for indbakkereglen. I dette eksempel er betingelsen angivet af *parameteren* Fra. Den værdi, der er defineret for *parameteren Fra* , angiver, at indbakkereglen fungerer på mails, der sendes admin@alpinehouse.onmicrosoft.com. Du kan finde en komplet liste over de parametre, der kan bruges til at definere betingelser for indbakkeregler, i [artiklen Ny indbakkeregel](/powershell/module/exchange/new-inboxrule) .

c. *Parameteren MoveToFolder* angiver handlingen for indbakkereglen. I dette eksempel flyttes meddelelser, der admin@alpinehouse.onmicrosoft.com mails, til mappen *Administrationssøgning*. Se også artiklen [Ny indbakkeregel om en](/powershell/module/exchange/new-inboxrule) komplet liste over parametre, der kan bruges til at definere handlingen for en indbakkeregel.

d. Feltet **UserId** angiver den bruger, der oprettede indbakkereglen angivet i **feltet Objekt-id** . Denne bruger vises også i **kolonnen Bruger** på siden med søgeresultater.

## <a name="investigate-why-there-was-a-successful-login-by-a-user-outside-your-organization"></a>Undersøg, hvorfor en bruger uden for organisationen har udført et vellykket logon

Når du gennemser overvågningsposterne i overvågningsloggen, får du muligvis vist poster, der angiver, at en ekstern bruger er blevet godkendt af Azure Active Directory og logget på organisationen. Eksempelvis får en administrator i contoso.onmicrosoft.com muligvis vist en overvågningspost, der viser, at en bruger fra en anden organisation (f.eks. fabrikam.onmicrosoft.com) er logget på contoso.onmicrosoft.com. På samme måde får du muligvis vist overvågningsposter, der angiver brugere med en Microsoft-konto (MSA), f.eks. en Outlook.com eller Live.com, der er logget på organisationen. I disse situationer er den overvågede aktivitet Bruger **logget på**. 

Denne funktionsmåde er tilsdesignet. Azure Active Directory (Azure AD), katalogtjenesten, tillader noget, der kaldes *pass-through-godkendelse*, når en ekstern bruger forsøger at få adgang til et SharePoint-websted eller en OneDrive-placering i organisationen. Når den eksterne bruger forsøger at gøre dette, bliver brugeren bedt om at angive sine legitimationsoplysninger. Azure AD bruger legitimationsoplysningerne til at godkende brugeren, hvilket betyder, at det kun er Azure AD, der bekræfter, at brugeren er den, brugeren siger, at det er. Angivelsen af det vellykkede logon i overvågningsposten er resultatet af Azure AD, der godkender brugeren. Det vellykkede logon betyder ikke, at brugeren har haft adgang til ressourcer eller andre handlinger i organisationen. Den angiver kun, at brugeren er godkendt af Azure AD. Hvis en pass-through-bruger skal have adgang til SharePoint- eller OneDrive-ressourcer, skal en bruger i organisationen udtrykkeligt dele en ressource med den eksterne bruger ved at sende dem en invitation til deling eller et anonymt delingslink. 

> [!NOTE]
> Azure AD tillader kun *pass-through-godkendelse for tredjepartsprogrammer*, f.eks. SharePoint Online og OneDrive for Business. Det er ikke tilladt for andre tredjepartsprogrammer.

Her er et eksempel og beskrivelser af relevante egenskaber i en overvågningspost for en bruger,  der er logget i-hændelsen, der er resultatet af pass-through-godkendelse. Vælg overvågningsposten for at få **vist** pop op-siden Detaljer, og vælg derefter **Flere oplysninger**.

![Eksempel på overvågningspost for vellykket pass-thru-godkendelse.](../media/PassThroughAuth1.png)

   a. Dette felt angiver, at den bruger, der forsøgte at få adgang til en ressource i organisationen, ikke blev fundet i din organisations Azure AD.

   b. Dette felt viser UPN'et for den eksterne bruger, der har forsøgt at få adgang til en ressource i organisationen. Dette bruger-id identificeres også i **egenskaberne User** **og UserId** i overvågningsposten.

   c. Egenskaben **ApplicationId** identificerer det program, der udløste logonanmodningen. Værdien af 00000003-0000-0ff1-ce00-0000000000000, der vises i egenskaben ApplicationId i denne overvågningspost, angiver SharePoint Online. OneDrive for Business også har dette samme ApplicationId.

   d. Dette angiver, at pass-through-godkendelsen blev gennemført. Med andre ord blev brugeren godkendt af Azure AD. 

   e. Værdien **RecordType** på **15** angiver, at den reviderede aktivitet (UserLoggedIn) er en STS-logonhændelse (Secure Token Service) i Azure AD.

Du kan finde flere oplysninger om de andre egenskaber, der vises i en UserLoggedIn-overvågningspost, under de Azure AD-relaterede skemaoplysninger [i Office 365 Management Activity API-skema](/office/office-365-management-api/office-365-management-activity-api-schema#azure-active-directory-base-schema).

Her er to eksempelscenarier, der resulterer i, at **en vellykket bruger** er logget på overvågningsaktivitet på grund af pass-through-godkendelse: 

  - En bruger med en Microsoft-konto (f.eks. SaraD@outlook.com) har forsøgt at få adgang til et dokument i en OneDrive for Business-konto i fourthcoffee.onmicrosoft.com, og der er ikke en tilsvarende gæstebrugerkonto til SaraD@outlook.com i fourthcoffee.onmicrosoft.com.

  - En bruger med en arbejds- eller skolekonto i en organisation (f.eks. pilarp@fabrikam.onmicrosoft.com) har forsøgt at få adgang til et SharePoint-websted i contoso.onmicrosoft.com, og der er ikke en tilsvarende gæstebrugerkonto til pilarp@fabrikam.com i contoso.onmicrosoft.com.

### <a name="tips-for-investigating-successful-logins-resulting-from-pass-through-authentication"></a>Tips for at undersøge vellykkede logons som følge af pass-through-godkendelse

- Søg i overvågningsloggen efter aktiviteter, der er udført af den eksterne bruger, der er identificeret i **den bruger, der er logget i** overvågningsposten. Skriv UPN for den eksterne bruger i feltet Brugere **, og brug** et datointerval, hvis det er relevant for scenariet. Du kan f.eks. oprette en søgning ved hjælp af følgende søgekriterier:

   ![Søg efter alle aktiviteter, der udføres af den eksterne bruger.](../media/PassThroughAuth2.png)

    Ud over aktiviteter,  der er logget på af brugeren, kan der blive returneret andre overvågningsposter, f.eks. dem, der angiver, at en bruger i organisationen har delt ressourcer med den eksterne bruger, og om den eksterne bruger har fået adgang til, ændret eller hentet et dokument, der blev delt med brugeren.

- Søg efter SharePoint delingsaktiviteter, der angiver, at en fil blev delt med den eksterne bruger identificeret af en bruger, **der er logget i** overvågningspost. Få mere at vide under [Brug overvågning af deling i overvågningsloggen](use-sharing-auditing.md).

- Eksportér søgeresultaterne fra overvågningsloggen, der indeholder data, som er relevante for din undersøgelse, så du kan bruge Excel til at søge efter andre aktiviteter, der er relateret til den eksterne bruger. Få mere at vide under  [Eksportér, konfigurer og få vist overvågningslogposter](export-view-audit-log-records.md).

## <a name="search-for-mailbox-activities-performed-by-users-with-non-e5-licenses"></a>Søg efter postkasseaktiviteter, der udføres af brugere med licenser, der ikke er E5

Selv når [](enable-mailbox-auditing.md) overvågning af postkasser som standard er slået til for din organisation, bemærker du muligvis, at postkassekontrolhændelser for nogle brugere ikke findes i overvågningsloggens søgninger ved hjælp af overholdelsescenteret, **Search-UnifiedAuditLog-cmdlet'en** eller Office 365 Management Activity API. Dette skyldes, at postkassekontrolhændelser kun returneres for brugere med E5-licenser, når du en af de tidligere metoder til at søge i den samlede overvågningslog.

Hvis du vil hente poster i postkasse overvågningsloggen for brugere, der ikke er E5, kan du udføre en af følgende løsninger:

- Aktivér postkasserevision for individuelle postkasser manuelt (kør `Set-Mailbox -Identity <MailboxIdentity> -AuditEnabled $true` kommandoen i Exchange Online PowerShell). Når du har gjort dette, skal du søge efter postkassens overvågningsaktiviteter ved hjælp af overholdelsescenter, cmdlet'en **Search-UnifiedAuditLog** eller Office 365 Management Activity API.
  
  > [!NOTE]
  > Hvis overvågning af postkasser allerede ser ud til at være aktiveret på postkassen, men dine søgninger ikke returnerer nogen resultater, skal du ændre værdien af _parameteren AuditEnabled_ `$false` til og derefter tilbage til `$true`.
  
- Brug følgende cmdlet'er i Exchange Online PowerShell:

  - [Search-MailboxAuditLog til at](/powershell/module/exchange/search-mailboxauditlog) søge i postkassens overvågningslog efter bestemte brugere.

  - [New-MailboxAuditLogSearch](/powershell/module/exchange/new-mailboxauditlogsearch) for at søge i postkassens overvågningslog efter bestemte brugere og for at få sendt resultaterne via mail til bestemte modtagere.

## <a name="search-for-mailbox-activities-performed-in-a-specific-mailbox-including-shared-mailboxes"></a>Søge efter postkasseaktiviteter, der udføres i en bestemt postkasse (herunder delte postkasser)

Når du bruger rullelisten Brugere i overvågningsloggens søgeværktøj i overholdelsescenteret eller kommandoen **Search-UnifiedAuditLog -UserIds** i Exchange Online PowerShell, kan du søge efter aktiviteter, der udføres af en bestemt bruger. Ved postkassekontrolaktiviteter søger denne type søgning efter aktiviteter, der er udført af den angivne bruger. Det garanterer ikke, at alle aktiviteter, der udføres i den samme postkasse, returneres i søgeresultaterne. En søgning i overvågningsloggen returnerer f.eks. ikke overvågningsposter for aktiviteter, der er udført af en stedfortræder, fordi søgning efter postkasseaktiviteter udført af en bestemt bruger ikke returnerer aktiviteter, der er udført af en stedfortræderbruger, som har fået tildelt adgangstilladelse til en anden brugers postkasse. (En stedfortræderbruger er en person, der har fået tildelt SendAs-, SendOnBehalf- eller FullAccess-postkassetilladelse til en anden brugers postkasse).

Desuden returnerer brug af  rullelisten Bruger i søgeværktøjet til overvågningsloggen eller **Search-UnifiedAuditLog -UserIds** ikke resultater for aktiviteter, der er udført i en delt postkasse.

Hvis du vil søge efter de aktiviteter, der udføres i en bestemt postkasse, eller hvis du vil søge efter aktiviteter, der er udført i en delt postkasse, skal du bruge følgende syntaks, når du kører **cmdlet'en Search-UnifiedAuditLog** :

```powershell
Search-UnifiedAuditLog  -StartDate <date> -EndDate <date> -FreeText (Get-Mailbox <mailbox identity).ExchangeGuid
```

Følgende kommando returnerer f.eks. overvågningsposter for aktiviteter, der er udført i den delte postkasse Contoso-overholdelsesteam mellem august 2020 og oktober 2020:

```powershell
Search-UnifiedAuditLog  -StartDate 08/01/2020 -EndDate 10/31/2020 -FreeText (Get-Mailbox complianceteam@contoso.onmicrosoft.com).ExchangeGuid
```

Du kan også bruge cmdlet'en **Search-MailboxAuditLog** til at søge efter overvågningsposter for aktivitet, der er udført i en bestemt postkasse. Dette omfatter søgning efter aktiviteter, der udføres i en delt postkasse.

I følgende eksempel returneres poster i postkasse overvågningsloggen for aktiviteter, der udføres i den delte postkasse Contoso-overholdelsesteam:

```powershell
Search-MailboxAuditLog -Identity complianceteam@contoso.onmicrosoft.com -StartDate 08/01/2020 -EndDate 10/31/2020 -ShowDetails
```

I følgende eksempel returneres poster i postkasse overvågningsloggen for aktiviteter, der udføres i den angivne postkasse af stedfortræderbrugere:

```powershell
Search-MailboxAuditLog -Identity <mailbox identity> -StartDate <date> -EndDate <date> -LogonTypes Delegate -ShowDetails
```

Du kan også bruge **New-MailboxAuditLogSearch-cmdlet'en** til at søge i overvågningsloggen efter en bestemt postkasse og få sendt resultaterne via mail til de angivne modtagere.