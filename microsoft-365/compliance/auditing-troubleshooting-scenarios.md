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
description: Få mere at vide om, hvordan du bruger søgeværktøjet Microsoft 365 overvågningslog til at foretage fejlfinding af almindelige supportproblemer for mailkonti.
ms.openlocfilehash: add354058a9e6e3d114c97a2932ff0302a27e272
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/19/2022
ms.locfileid: "64946545"
---
# <a name="search-the-audit-log-to-investigate-common-support-issues"></a>Søg i overvågningsloggen for at undersøge almindelige supportproblemer

I denne artikel beskrives det, hvordan du bruger søgeværktøjet til overvågningslog til at hjælpe dig med at undersøge almindelige supportproblemer. Dette omfatter brug af overvågningsloggen til at:

- Find IP-adressen på den computer, der bruges til at få adgang til en kompromitteret konto
- Find ud af, hvem der konfigurerer videresendelse af mail for en postkasse
- Find ud af, om en bruger har slettet mailelementer i sin postkasse
- Find ud af, om en bruger har oprettet en indbakkeregel
- Undersøg, hvorfor en bruger uden for organisationen lykkedes med at logge på
- Søg efter postkasseaktiviteter, der udføres af brugere med ikke-E5-licenser
- Søg efter postkasseaktiviteter, der udføres af stedfortræderbrugere

## <a name="using-the-audit-log-search-tool"></a>Brug af søgeværktøjet til overvågningslog

Hvert af de fejlfindingsscenarier, der er beskrevet i denne artikel, er baseret på brug af søgeværktøjet til overvågningslog på Microsoft Purview-overholdelsesportalen. I dette afsnit vises de tilladelser, der kræves for at søge i overvågningsloggen, og det beskrives, hvordan du får adgang til og kører søgninger i overvågningsloggen. I hvert scenarieafsnit forklares det, hvordan du konfigurerer en søgeforespørgsel i overvågningsloggen, og hvad du skal søge efter i de detaljerede oplysninger i de overvågningsposter, der opfylder søgekriterierne.

### <a name="permissions-required-to-use-the-audit-log-search-tool"></a>Tilladelser, der kræves for at bruge søgeværktøjet til overvågningslog

Du skal være tildelt rollen View-Only overvågningslogge eller overvågningslogge i Exchange Online for at kunne søge i overvågningsloggen. Disse roller tildeles som standard til rollegrupperne Administration af overholdelse og Organisationsadministration på siden **Tilladelser** i <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange Administration</a>. Globale administratorer i Office 365 og Microsoft 365 tilføjes automatisk som medlemmer af rollegruppen Organisationsadministration i Exchange Online. Du kan få flere oplysninger under [Administrer rollegrupper i Exchange Online](/Exchange/permissions-exo/role-groups).

### <a name="running-audit-log-searches"></a>Kører søgninger i overvågningslog

I dette afsnit beskrives de grundlæggende funktioner til oprettelse og kørsel af søgninger i overvågningslog. Brug disse instruktioner som udgangspunkt for hvert fejlfindingsscenarie i denne artikel. Du kan finde mere detaljerede trinvise instruktioner i [Søg i overvågningsloggen](search-the-audit-log-in-security-and-compliance.md#step-1-run-an-audit-log-search).

1. Gå til , <https://compliance.microsoft.com/auditlogsearch> og log på med din arbejds- eller skolekonto.
  
    Siden **Overvågning** vises.
  
    ![Konfigurer kriterier, og vælg derefter Søg for at køre søgningen.](../media/AuditLogSearchPage1.png)
  
2. Du kan konfigurere følgende søgekriterier. Hvert fejlfindingsscenarie i denne artikel anbefaler specifik vejledning til konfiguration af disse felter.
  
   a. **Startdato** og **slutdato:** Vælg et dato- og klokkeslætsinterval for at få vist de hændelser, der opstod inden for den pågældende periode. De seneste syv dage er valgt som standard. Dato og klokkeslæt vises i UTC-format (Coordinated Universal Time). Det maksimale datointerval, du kan angive, er 90 dage.

   b. **Aktiviteter:** Vælg rullelisten for at få vist de aktiviteter, du kan søge efter. Når du har kørt søgningen, er det kun overvågningsposterne for de valgte aktiviteter, der vises. Hvis du vælger **Vis resultater for alle aktiviteter** , vises der resultater for alle aktiviteter, der opfylder de andre søgekriterier. Du skal også lade feltet være tomt i nogle af fejlfindingsscenarierne.
  
    c. **Brugere:** Klik i dette felt, og vælg derefter en eller flere brugere, der skal vises søgeresultater for. Overvågningsposter for den valgte aktivitet, der er udført af de brugere, du vælger i dette felt, vises på listen over resultater. Lad dette felt være tomt for at returnere poster for alle brugere (og tjenestekonti) i din organisation.
  
    d. **Fil, mappe eller websted:** Skriv et eller hele navnet på en fil eller mappe for at søge efter aktivitet, der er relateret til filen med den mappe, der indeholder det angivne nøgleord. Du kan også angive en URL-adresse til en fil eller mappe. Hvis du bruger en URL-adresse, skal du sørge for at skrive hele URL-stien, eller hvis du kun skriver en del af URL-adressen, skal du ikke inkludere specialtegn eller mellemrum. Lad dette felt være tomt for at returnere poster for alle filer og mapper i din organisation. Dette felt er tomt i alle fejlfindingsscenarier i denne artikel.
  
3. Vælg **Søg** for at køre søgningen ved hjælp af dine søgekriterier.
  
    Søgeresultaterne indlæses, og efter et øjeblik vises de på en side i søgeværktøjet til overvågningslog. Hvert af afsnittene i denne artikel indeholder vejledning om ting, du skal kigge efter i forbindelse med det specifikke fejlfindingsscenarie.

    Du kan finde flere oplysninger om visning og eksport af søgeresultater i overvågningsloggen i:

    - [Vis søgeresultater](search-the-audit-log-in-security-and-compliance.md#step-2-view-the-search-results)
  
    - [Eksportér søgeresultater](search-the-audit-log-in-security-and-compliance.md#step-3-export-the-search-results-to-a-file)

## <a name="find-the-ip-address-of-the-computer-used-to-access-a-compromised-account"></a>Find IP-adressen på den computer, der bruges til at få adgang til en kompromitteret konto

Den IP-adresse, der svarer til en aktivitet udført af en hvilken som helst bruger, er inkluderet i de fleste overvågningsposter. Oplysninger om den klient, der bruges, er også inkluderet i overvågningsposten.

Sådan konfigurerer du en søgeforespørgsel i overvågningsloggen for dette scenarie:

**Aktiviteter:** Hvis det er relevant for din sag, skal du vælge en bestemt aktivitet, du vil søge efter. I forbindelse med fejlfinding af kompromitterede konti kan du overveje at vælge den bruger, der **er logget på postkasseaktiviteten** under **Exchange postkasseaktiviteter**. Dette returnerer overvågningsposter, der viser den IP-adresse, der blev brugt, da du logger på postkassen. Ellers skal du lade feltet være tomt for at returnere overvågningsposter for alle aktiviteter. 

> [!TIP]
> Hvis du lader feltet være tomt, **returneres UserLoggedIn-aktiviteter**, som er en Azure Active Directory aktivitet, der angiver, at en person har logget på en brugerkonto. Brug filtrering i søgeresultaterne til at få vist **UserLoggedIn-overvågningsposterne** .

**Startdato** og **slutdato:** Vælg et datointerval, der skal gælde for din undersøgelse.

**Brugere:** Hvis du undersøger en kompromitteret konto, skal du vælge den bruger, hvis konto blev kompromitteret. Dette returnerer overvågningsposter for aktiviteter, der udføres af den pågældende brugerkonto.

**Fil, mappe eller websted:** Lad dette felt være tomt.

Når du har kørt søgningen, vises IP-adressen for hver aktivitet i kolonnen **IP-adresse** i søgeresultaterne. Vælg posten i søgeresultaterne for at få vist mere detaljerede oplysninger på pop op-siden.

## <a name="determine-who-set-up-email-forwarding-for-a-mailbox"></a>Find ud af, hvem der konfigurerer videresendelse af mail for en postkasse

Når videresendelse af mail er konfigureret for en postkasse, videresendes mails, der sendes til postkassen, til en anden postkasse. Meddelelser kan videresendes til brugere i eller uden for din organisation. Når videresendelse af mail er konfigureret på en postkasse, er den underliggende Exchange Online cmdlet, der bruges, **Set-Mailbox**.

Sådan konfigurerer du en søgeforespørgsel i overvågningsloggen for dette scenarie:

**Aktiviteter:** Lad feltet være tomt, så søgningen returnerer overvågningsposter for alle aktiviteter. Dette er nødvendigt for at returnere alle overvågningsposter, der er relateret til **Set-Mailbox-cmdlet'en** .

**Startdato** og **slutdato:** Vælg et datointerval, der skal gælde for din undersøgelse.

**Brugere:** Medmindre du undersøger et problem med videresendelse af mail for en bestemt bruger, skal du lade dette felt være tomt. Dette hjælper dig med at identificere, om videresendelse af mail blev konfigureret for nogen bruger.

**Fil, mappe eller websted:** Lad dette felt være tomt.

Når du har kørt søgningen, skal du vælge **Filtrer resultater** på siden med søgeresultater. I feltet under **Kolonneoverskrift for aktivitet** skal du skrive **Set-Mailbox** , så det kun er overvågningsposter, der er relateret til **Set-Mailbox-cmdlet'en** , der vises.

![Filtrering af resultaterne af en søgning i overvågningsloggen.](../media/emailforwarding1.png)

På dette tidspunkt skal du se på detaljerne for hver overvågningspost for at afgøre, om aktiviteten er relateret til videresendelse af mail. Vælg overvågningsposten for at få vist pop op-siden **Detaljer** , og vælg derefter **Flere oplysninger**. På følgende skærmbillede og beskrivelser fremhæves de oplysninger, der angiver, at videresendelse af mail blev angivet i postkassen.

![Detaljerede oplysninger fra overvågningsposten.](../media/emailforwarding2.png)

a. I feltet **ObjectId** vises aliasset for den postkasse, som videresendelse af mail blev angivet for. Denne postkasse vises også i kolonnen **Element** på siden med søgeresultater.

b. I feltet **Parametre** angiver værdien *ForwardingSmtpAddress* , at videresendelse af mail blev angivet i postkassen. I dette eksempel videresendes mail til mailadressen mike@contoso.com, som er uden for den alpinehouse.onmicrosoft.com organisation.

c. Værdien *True* for parameteren *DeliverToMailboxAndForward* angiver, at der leveres en kopi af meddelelsen til sarad@alpinehouse.onmicrosoft.com *og* videresendes til den mailadresse, der er angivet i parameteren *ForwardingSmtpAddress* , som i dette eksempel er mike@contoso.com. Hvis værdien for parameteren *DeliverToMailboxAndForward* er angivet til *Falsk*, videresendes mail kun til den adresse, der er angivet i parameteren *ForwardingSmtpAddress* . Den leveres ikke til den postkasse, der er angivet i feltet **ObjectId** .

d. Feltet **UserId** angiver den bruger, der angiver videresendelse af mail for den postkasse, der er angivet i feltet **ObjectId** . Denne bruger vises også i kolonnen **Bruger** på siden med søgeresultater. I dette tilfælde ser det ud til, at ejeren af postkassen har angivet videresendelse af mail på sin postkasse.

Hvis du finder ud af, at videresendelse af mail ikke skal angives i postkassen, kan du fjerne den ved at køre følgende kommando i Exchange Online PowerShell:

```powershell
Set-Mailbox <mailbox alias> -ForwardingSmtpAddress $null 
```

Du kan få flere oplysninger om de parametre, der er relateret til videresendelse af mail, i artiklen [Angiv postkasse](/powershell/module/exchange/set-mailbox) .

## <a name="determine-if-a-user-deleted-email-items"></a>Find ud af, om en bruger har slettet mailelementer

Fra og med januar 2019 aktiverer Microsoft som standard logføring af overvågning af postkasser for alle Office 365 og Microsoft-organisationer. Det betyder, at visse handlinger, der udføres af postkasseejere, logføres automatisk, og de tilsvarende overvågningsposter for postkassen er tilgængelige, når du søger efter dem i postkassens overvågningslog. Før overvågning af postkassen blev slået til som standard, skulle du aktivere den manuelt for hver brugerpostkasse i din organisation. 

De postkassehandlinger, der logføres som standard, omfatter handlingerne SoftDelete og HardDelete, der udføres af postkasseejere. Det betyder, at du kan bruge følgende trin til at søge i overvågningsloggen efter hændelser, der er relateret til slettede mailelementer. Du kan få flere oplysninger om overvågning af postkasser som standard under [Administrer overvågning af postkasser](enable-mailbox-auditing.md).

Sådan konfigurerer du en søgeforespørgsel i overvågningsloggen for dette scenarie:

**Aktiviteter:** Under **Exchange postkasseaktiviteter** skal du vælge en eller begge af følgende aktiviteter:

- **Slettede meddelelser fra mappen Slettet post:** Denne aktivitet svarer til overvågningshandlingen **for SoftDelete-postkassen** . Denne aktivitet logføres også, når en bruger sletter et element permanent ved at markere det og trykke på **Skift+Slet**. Når et element er slettet permanent, kan brugeren gendanne det, indtil opbevaringsperioden for slettede elementer udløber.

- **Fjernede meddelelser fra postkasse:** Denne aktivitet svarer til overvågningshandlingen **for HardDelete-postkassen** . Dette logføres, når en bruger fjerner et element fra mappen Gendanbare elementer. Administratorer kan bruge værktøjet indholdssøgning i Security and Compliance Center til at søge efter og gendanne fjernede elementer, indtil opbevaringsperioden for slettede elementer udløber eller er længere, hvis brugerens postkasse er i venteposition.

**Startdato** og **slutdato:** Vælg et datointerval, der skal gælde for din undersøgelse.

**Brugere:** Hvis du vælger en bruger i dette felt, returnerer søgeværktøjet til overvågningsloggen overvågningsposter for mailelementer, der er blevet slettet (SoftDeleted eller HardDeleted) af den bruger, du angiver. Nogle gange er den bruger, der sletter en mail, muligvis ikke ejeren af postkassen.

**Fil, mappe eller websted:** Lad dette felt være tomt.

Når du har kørt søgningen, kan du filtrere søgeresultaterne for at få vist overvågningsposterne for elementer, der er slettet med blød adgang, eller for elementer, der er slettet hårdt. Vælg overvågningsposten for at få vist pop op-siden **Detaljer** , og vælg derefter **Flere oplysninger**. Yderligere oplysninger om det slettede element, f.eks. emnelinjen og placeringen af elementet, da det blev slettet, vises i feltet **Berørte elementer** . På følgende skærmbilleder vises et eksempel på feltet **AffectedItems** fra et blød slettet element og et hårdt slettet element.

**Eksempel på feltet AffectedItems for element med blød sletning**

![Overvågningspost for element, der er slettet med blød sletning.](../media/softdeleteditem.png)

**Eksempel på feltet AffectedItems for hårdt slettet element**

![Overvågningspost for hårdt slettet mailelement.](../media/harddeleteditem.png)

### <a name="recover-deleted-email-items"></a>Gendan slettede mailelementer

Brugerne kan gendanne elementer, der er slettet med blød adgang, hvis opbevaringsperioden for slettede elementer ikke er udløbet. I Exchange Online er standardopbevaringsperioden for slettede elementer 14 dage, men administratorer kan øge denne indstilling til højst 30 dage. Peg brugerne på artiklen [Gendan slettede elementer eller mail i Outlook på internettet](https://support.office.com/article/Recover-deleted-items-or-email-in-Outlook-Web-App-C3D8FC15-EEEF-4F1C-81DF-E27964B7EDD4) for at få instruktioner i gendannelse af slettede elementer.

Som tidligere forklaret kan administratorer muligvis gendanne slettede elementer, hvis opbevaringsperioden for slettede elementer ikke er udløbet, eller hvis postkassen er i venteposition, i hvilket tilfælde elementer bevares, indtil varigheden af ventepositionen udløber. Når du kører en indholdssøgning, returneres elementer i mappen Gendanbare elementer i søgeresultaterne, hvis de stemmer overens med søgeforespørgslen. Du kan finde flere oplysninger om kørsel af indholdssøgninger [under Indholdssøgning i Office 365](content-search.md).

> [!TIP]
> Hvis du vil søge efter slettede mailelementer, skal du søge efter hele eller en del af emnelinjen, der vises i feltet **Berørte elementer** i overvågningsposten.

## <a name="determine-if-a-user-created-an-inbox-rule"></a>Find ud af, om en bruger har oprettet en indbakkeregel

Når brugerne opretter en indbakkeregel for deres Exchange Online postkasse, gemmes der en tilsvarende overvågningspost i overvågningsloggen. Du kan få flere oplysninger om indbakkeregler under:

- [Brug indbakkeregler i Outlook på internettet](https://support.office.com/article/use-inbox-rules-in-outlook-on-the-web-8400435c-f14e-4272-9004-1548bb1848f2)
- [Administrer mails i Outlook ved hjælp af regler](https://support.office.com/article/Manage-email-messages-by-using-rules-C24F5DEA-9465-4DF4-AD17-A50704D66C59)

Sådan konfigurerer du en søgeforespørgsel i overvågningsloggen for dette scenarie:

**Aktiviteter:** Under **Exchange postkasseaktiviteter** skal du vælge en eller begge af følgende aktiviteter:

- **New-InboxRule Opret en ny indbakkeregel fra Outlook Web App**. Denne aktivitet returnerer overvågningsposter, når der oprettes indbakkeregler ved hjælp af Outlook webapp eller Exchange Online PowerShell.

- **Opdaterede indbakkeregler fra Outlook klient**. Denne aktivitet returnerer overvågningsposter, når indbakkeregler oprettes, ændres eller fjernes ved hjælp af Outlook desktopklient.

**Startdato** og **slutdato:** Vælg et datointerval, der skal gælde for din undersøgelse.

**Brugere:** Medmindre du undersøger en bestemt bruger, skal du lade dette felt være tomt. Dette hjælper dig med at identificere nye indbakkeregler, der er konfigureret af alle brugere.

**Fil, mappe eller websted:** Lad dette felt være tomt.

Når du har kørt søgningen, vises alle overvågningsposter for denne aktivitet i søgeresultaterne. Vælg en overvågningspost for at få vist pop op-siden **Detaljer** , og vælg derefter **Flere oplysninger**. Oplysninger om indstillingerne for indbakkereglen vises i feltet **Parametre** . På følgende skærmbillede og beskrivelser fremhæves oplysningerne om indbakkeregler.

![Overvågningspost for ny indbakkeregel.](../media/NewInboxRuleRecord.png)

a. I feltet **ObjectId** vises det fulde navn på indbakkereglen. Dette navn indeholder aliasset for brugerens postkasse (f.eks. SaraD) og navnet på indbakkereglen (f.eks. "Flyt meddelelser fra administratoren").

b. I feltet **Parametre** vises betingelsen for indbakkereglen. I dette eksempel er betingelsen angivet af parameteren *From* . Den værdi, der er defineret for parameteren *From* , angiver, at indbakkereglen fungerer på mails, der er sendt af admin@alpinehouse.onmicrosoft.com. Du kan finde en komplet liste over de parametre, der kan bruges til at definere betingelser for indbakkeregler, i artiklen [Ny IndbakkeRegel](/powershell/module/exchange/new-inboxrule) .

c. Parameteren *MoveToFolder* angiver handlingen for indbakkereglen. I dette eksempel flyttes meddelelser, der er modtaget fra admin@alpinehouse.onmicrosoft.com, til mappen med navnet *AdminSearch*. Se også artiklen [Ny IndbakkeRegel](/powershell/module/exchange/new-inboxrule) for at få en komplet liste over parametre, der kan bruges til at definere handlingen for en indbakkeregel.

d. Feltet **UserId** angiver den bruger, der oprettede den indbakkeregel, der er angivet i feltet **ObjectId** . Denne bruger vises også i kolonnen **Bruger** på siden med søgeresultater.

## <a name="investigate-why-there-was-a-successful-login-by-a-user-outside-your-organization"></a>Undersøg, hvorfor en bruger uden for organisationen lykkedes med at logge på

Når du gennemser overvågningsposter i overvågningsloggen, kan du se poster, der angiver, at en ekstern bruger er blevet godkendt af Azure Active Directory og er logget på din organisation. En administrator i contoso.onmicrosoft.com kan f.eks. se en overvågningspost, der viser, at en bruger fra en anden organisation (f.eks. fabrikam.onmicrosoft.com) er logget på contoso.onmicrosoft.com. På samme måde kan du muligvis se overvågningsposter, der angiver, at brugere med en Microsoft-konto (MSA), f.eks. en Outlook.com eller Live.com, er logget på din organisation. I disse situationer er den overvågede aktivitet **bruger logget på**. 

Denne funktionsmåde er tilsigtet. Azure Active Directory (Azure AD), katalogtjenesten, tillader noget, der kaldes *pass-through-godkendelse*, når en ekstern bruger forsøger at få adgang til et SharePoint websted eller en OneDrive placering i din organisation. Når den eksterne bruger forsøger at gøre dette, bliver vedkommende bedt om at angive sine legitimationsoplysninger. Azure AD bruger legitimationsoplysningerne til at godkende brugeren, hvilket betyder, at det kun er Azure AD, der bekræfter, at brugeren er den, de siger, de er. Indikationen af det vellykkede logon i overvågningsposten er resultatet af, at Azure AD godkender brugeren. Det vellykkede logon betyder ikke, at brugeren kunne få adgang til ressourcer eller udføre andre handlinger i din organisation. Det angiver kun, at brugeren blev godkendt af Azure AD. Hvis en pass-through-bruger skal have adgang til SharePoint eller OneDrive ressourcer, skal en bruger i organisationen udtrykkeligt dele en ressource med den eksterne bruger ved at sende vedkommende en invitation til deling eller et anonymt delingslink. 

> [!NOTE]
> Azure AD tillader kun pass-through-godkendelse for *førstepartsprogrammer*, f.eks. SharePoint Online og OneDrive for Business. Det er ikke tilladt for andre tredjepartsprogrammer.

Her er et eksempel på og beskrivelser af relevante egenskaber i en overvågningspost for en bruger, der er **logget på** hændelse, som er et resultat af pass-through-godkendelse. Vælg overvågningsposten for at få vist pop op-siden **Detaljer** , og vælg derefter **Flere oplysninger**.

![Eksempel på overvågningspost for vellykket pass-through-godkendelse.](../media/PassThroughAuth1.png)

   a. Dette felt angiver, at den bruger, der forsøgte at få adgang til en ressource i din organisation, ikke blev fundet i din organisations Azure AD.

   b. I dette felt vises UPN'et for den eksterne bruger, der forsøgte at få adgang til en ressource i organisationen. Dette bruger-id identificeres også i egenskaberne **User** og **UserId** i overvågningsposten.

   c. Egenskaben **ApplicationId** identificerer det program, der udløste logonanmodningen. Værdien 00000003-0000-0ff1-ce00-000000000000, der vises i egenskaben ApplicationId i denne overvågningspost, angiver SharePoint Online. OneDrive for Business har også det samme ApplicationId.

   d. Dette angiver, at pass-through-godkendelsen lykkedes. Med andre ord blev brugeren godkendt af Azure AD. 

   e. **Værdien af RecordType** **på 15** angiver, at den overvågede aktivitet (UserLoggedIn) er en STS-logonhændelse (Secure Token Service) i Azure AD.

Du kan få flere oplysninger om de andre egenskaber, der vises i en UserLoggedIn-overvågningspost, i azure AD-relaterede skemaoplysninger i [API-skemaet til administration af Office 365](/office/office-365-management-api/office-365-management-activity-api-schema#azure-active-directory-base-schema).

Her er to eksempler på scenarier, der kan resultere i en vellykket bruger, der er **logget på** overvågningsaktivitet på grund af pass-through-godkendelse: 

  - En bruger med en Microsoft-konto (f.eks. SaraD@outlook.com) har forsøgt at få adgang til et dokument på en OneDrive for Business konto i fourthcoffee.onmicrosoft.com, og der er ikke en tilsvarende gæstebrugerkonto til SaraD@outlook.com i fourthcoffee.onmicrosoft.com.

  - En bruger med en arbejds- eller skolekonto i en organisation (f.eks. pilarp@fabrikam.onmicrosoft.com) har forsøgt at få adgang til et SharePoint websted i contoso.onmicrosoft.com, og der er ikke en tilsvarende gæstebrugerkonto til pilarp@fabrikam.com i contoso.onmicrosoft.com.

### <a name="tips-for-investigating-successful-logins-resulting-from-pass-through-authentication"></a>Tips til undersøgelse af vellykkede logon som følge af pass-through-godkendelse

- Søg i overvågningsloggen efter aktiviteter, der er udført af den eksterne bruger, som er identificeret i den **bruger, der er logget på** overvågningsposten. Skriv UPN'et for den eksterne bruger i feltet **Brugere** , og brug et datointerval, hvis det er relevant for dit scenarie. Du kan f.eks. oprette en søgning ved hjælp af følgende søgekriterier:

   ![Søg efter alle aktiviteter, der udføres af den eksterne bruger.](../media/PassThroughAuth2.png)

    Ud over den bruger, der er **logget på** aktiviteter, kan andre overvågningsposter blive returneret, f.eks. dem, der angiver, at en bruger i organisationen delte ressourcer med den eksterne bruger, og om den eksterne bruger har åbnet, ændret eller downloadet et dokument, der er delt med dem.

- Søg efter SharePoint delingsaktiviteter, der angiver, at en fil er delt med den eksterne bruger, der er identificeret af en bruger, der **er logget på** overvågningsposten. Du kan få flere oplysninger under [Brug overvågning af deling i overvågningsloggen](use-sharing-auditing.md).

- Eksportér søgeresultaterne i overvågningsloggen, der indeholder poster, der er relevante for din undersøgelse, så du kan bruge Excel til at søge efter andre aktiviteter, der er relateret til den eksterne bruger. Du kan finde flere oplysninger under  [Eksportér, konfigurer og få vist overvågningslogposter](export-view-audit-log-records.md).

## <a name="search-for-mailbox-activities-performed-by-users-with-non-e5-licenses"></a>Søg efter postkasseaktiviteter, der udføres af brugere med ikke-E5-licenser

Selvom [overvågning af postkasser som standard](enable-mailbox-auditing.md) er slået til for din organisation, vil du måske bemærke, at overvågningshændelser for nogle brugere ikke findes i søgninger i overvågningsloggen ved hjælp af overholdelsescenteret, cmdlet'en **Search-UnifiedAuditLog** eller API'en til Office 365-administrationsaktivitet. Årsagen til dette er, at postkassens overvågningshændelser kun returneres for brugere med E5-licenser, når du en af de tidligere metoder til at søge i den samlede overvågningslog.

Hvis du vil hente overvågningslogposter for postkasser for ikke-E5-brugere, kan du udføre en af følgende løsninger:

- Aktivér overvågning af postkasser manuelt på individuelle postkasser (kør kommandoen `Set-Mailbox -Identity <MailboxIdentity> -AuditEnabled $true` i Exchange Online PowerShell). Når du har gjort dette, skal du søge efter overvågningsaktiviteter for postkasser ved hjælp af Overholdelsescenter, cmdlet'en **Search-UnifiedAuditLog** eller API'en til Office 365 administrationsaktiviteter.
  
  > [!NOTE]
  > Hvis overvågning af postkassen allerede ser ud til at være aktiveret i postkassen, men dine søgninger ikke returnerer nogen resultater, skal du ændre værdien af parameteren _AuditEnabled_ til `$false` og derefter tilbage til `$true`.
  
- Brug følgende cmdlet'er i Exchange Online PowerShell:

  - [Search-MailboxAuditLog](/powershell/module/exchange/search-mailboxauditlog) for at søge i postkassens overvågningslog for bestemte brugere.

  - [New-MailboxAuditLogSearch](/powershell/module/exchange/new-mailboxauditlogsearch) til at søge i postkassens overvågningslog for bestemte brugere og få resultaterne sendt via mail til angivne modtagere.

## <a name="search-for-mailbox-activities-performed-in-a-specific-mailbox-including-shared-mailboxes"></a>Søg efter postkasseaktiviteter, der udføres i en bestemt postkasse (herunder delte postkasser)

Når du bruger rullelisten **Brugere** i søgeværktøjet til overvågningslog i overholdelsescenter eller kommandoen **Search-UnifiedAuditLog -UserIds** i Exchange Online PowerShell, kan du søge efter aktiviteter, der er udført af en bestemt bruger. I forbindelse med overvågningsaktiviteter for postkasser søger denne type søgning efter aktiviteter, der er udført af den angivne bruger. Det garanterer ikke, at alle aktiviteter, der udføres i den samme postkasse, returneres i søgeresultaterne. En søgning i en overvågningslog returnerer f.eks. ikke overvågningsposter for aktiviteter, der er udført af en stedfortræderbruger, fordi søgning efter postkasseaktiviteter, der udføres af en bestemt bruger, ikke returnerer aktiviteter, der er udført af en stedfortræderbruger, som har fået tildelt tilladelser til at få adgang til en anden brugers postkasse. En stedfortræderbruger er en person, der har fået tildelt tilladelsen SendAs, SendOnBehalf eller FullAccess-postkassen til en anden brugers postkasse.

Hvis du bruger rullelisten **Bruger** i søgeværktøjet til overvågningslog eller **Search-UnifiedAuditLog -UserIds, returneres** der heller ikke resultater for aktiviteter, der udføres i en delt postkasse.

Hvis du vil søge efter de aktiviteter, der udføres i en bestemt postkasse, eller hvis du vil søge efter aktiviteter, der udføres i en delt postkasse, skal du bruge følgende syntaks, når du kører cmdlet'en **Search-UnifiedAuditLog** :

```powershell
Search-UnifiedAuditLog  -StartDate <date> -EndDate <date> -FreeText (Get-Mailbox <mailbox identity).ExchangeGuid
```

Følgende kommando returnerer f.eks. overvågningsposter for aktiviteter, der udføres i den delte postkasse Contoso Compliance Team mellem august 2020 og oktober 2020:

```powershell
Search-UnifiedAuditLog  -StartDate 08/01/2020 -EndDate 10/31/2020 -FreeText (Get-Mailbox complianceteam@contoso.onmicrosoft.com).ExchangeGuid
```

Du kan også bruge **cmdlet'en Search-MailboxAuditLog** til at søge efter overvågningsposter for aktivitet, der er udført i en bestemt postkasse. Dette omfatter søgning efter aktiviteter, der udføres i en delt postkasse.

I følgende eksempel returneres overvågningslogposter for postkasser for aktiviteter, der udføres i den delte postkasse Contoso Compliance Team:

```powershell
Search-MailboxAuditLog -Identity complianceteam@contoso.onmicrosoft.com -StartDate 08/01/2020 -EndDate 10/31/2020 -ShowDetails
```

I følgende eksempel returneres overvågningslogposter for postkassen for aktiviteter, der udføres i den angivne postkasse af stedfortræderbrugere:

```powershell
Search-MailboxAuditLog -Identity <mailbox identity> -StartDate <date> -EndDate <date> -LogonTypes Delegate -ShowDetails
```

Du kan også bruge cmdlet'en **New-MailboxAuditLogSearch** til at søge i overvågningsloggen efter en bestemt postkasse og sende resultaterne via mail til de angivne modtagere.