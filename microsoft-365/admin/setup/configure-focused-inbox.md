---
title: Konfigurer Fokuseret indbakke for alle i organisationen
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
- admindeeplinkMAC
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 613a845c-4b71-41de-b331-acdcf5b6625d
description: Hvis du er ansvarlig for konfiguration af mailindstillinger for alle i en virksomhed, forklarer denne artikel, hvordan du konfigurerer Fokuseret indbakke for brugere.
ms.openlocfilehash: b2c315b6fb4a4c80f245bcf4731b93996753586a
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63590814"
---
# <a name="configure-focused-inbox-for-everyone-in-your-organization"></a>Konfigurer Fokuseret indbakke for alle i organisationen

Hvis du er ansvarlig for at konfigurere, hvordan mail fungerer for ALLE i en virksomhed, så er denne artikel lige noget for dig! Den forklarer, hvordan du tilpasser den eller slår den fra for din virksomhed og [besvarer ofte stillede spørgsmål](#faq-for-focused-inbox).

Hvis du vil deaktivere Fokuseret indbakke for dig selv, skal du se [Slå Fokuseret indbakke fra](https://support.microsoft.com/office/f714d94d-9e63-4217-9ccb-6cb2986aa1b2).  

Hvis du vil være sikker på, at brugerne modtager forretningsspecifikke mails, f.eks. fra HR- eller lønafdelingen, kan du konfigurere Fokuseret indbakke, så disse meddelelser når til Fokuseret visning. Du kan også styre, om brugerne i organisationen kan se Fokuseret indbakke i deres postkasse.
  
## <a name="turn-focused-inbox-on-or-off-in-your-organization"></a>Slå Fokuseret indbakke til eller fra i din organisation

Du kan bruge PowerShell til at slå Fokuseret indbakke til eller fra for alle i organisationen. Vil du gøre dette i Microsoft 365 Administration? Giv vores tekniske team besked. **[Stem her!](https://go.microsoft.com/fwlink/?linkid=862489)**
  
**Sådan deaktiverer du Fokuseret indbakke:**
  
Følgende PowerShell-eksempel slår Fokuseret indbakke **Fra** i din organisation. Funktionen blokeres dog ikke for dine brugeres tilgængelighed. Hvis de vil, kan de stadig genaktivere Fokuseret indbakke på hver af deres klienter. 
  
1. [Forbind til Exchange Online bruge Remote PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Du skal have tildelt tilladelser, før du kan udføre proceduren eller procedurerne. Se hvilke tilladelser, du skal bruge, i posten "Transportregler" under Meddelelsespolitik [og overholdelsestilladelser](/exchange/messaging-policy-and-compliance-permissions-exchange-2013-help).

3. Kør **cmdlet'en Get-OrganizationConfig** . 

    ```powershell
    Get-OrganizationConfig
    ```

4. Se efter **FocusedInboxOn for** at få vist den aktuelle indstilling: 

    ![Svar fra PowerShell om tilstanden for Fokuseret indbakke.](../../media/419d8caa-89b9-45c5-91d9-8c023297456e.png)
  
5. Kør følgende cmdlet for at slå Fokuseret indbakke fra.

    ```powershell
    Set-OrganizationConfig -FocusedInboxOn $false
    ```

6. Kør **cmdlet'en Get-OrganizationConfig** igen, og du vil se, at FocusedInboxOn er indstillet til $false, hvilket betyder, at den er blevet deaktiveret. 

**Sådan aktiverer du Fokuseret indbakke:**
  
- I trin 5 ovenfor skal du køre følgende cmdlet for at aktivere Fokuseret indbakke.

  ```powershell
  Set-OrganizationConfig -FocusedInboxOn $true
  ```
    
## <a name="what-do-users-see-after-i-turn-on-focused-inbox"></a>Hvad får brugerne vist, efter jeg har aktiveret Fokuseret indbakke?

Brugerne vil først få vist Fokuseret visning, når de lukker og genstarter Outlook. Når de genstarter Outlook, får de vist et tip i Outlook-brugergrænsefladen, der giver dem mulighed for at bruge den nye Fokuseret indbakke.
  
![Et billede af hvordan Fokuseret indbakke ser ud, når en bruger først åbner Outlook på internettet.](../../media/f6ef79e7-0f4c-4a23-b6f0-7c15d927b5f0.png)
  
Hvis du skifter fra Clutter til Fokuseret indbakke, kan de vælge at aktivere ("Prøv det") eller afvise funktionen. Hvis brugeren har flere (understøttede) klienter, kan de aktivere/deaktivere Fokuseret indbakke enkeltvis på hver enkelt. Tippet ser sådan ud:
  
![Et billede af hvordan Fokuseret indbakke ser ud, når den rulles ud til dine brugere, Outlook åbnes igen.](../../media/c034f969-d650-4333-88f1-dd10ade0a94c.png)
  
Når en bruger begynder at bruge Fokuseret indbakke, deaktiveres Clutter automatisk. Mappen Clutter konverteres til en standardmappe, der giver brugeren mulighed for at omdøbe eller slette den.
  
## <a name="turn-focused-inbox-on-or-off-for-specific-users"></a>Slå Fokuseret indbakke til eller fra for bestemte brugere

I dette eksempel deaktiveres **Fokuseret indbakke Fra** for Tim Matthews i organisationen Contoso. Han har dog ikke adgang til funktionen. Hvis han ønsker det, kan han stadig genaktivere Fokuseret indbakke på ny for hver af hans klienter. 
  
1. [Forbind til Exchange Online bruge Remote PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Du skal have tildelt tilladelser, før du kan udføre proceduren eller procedurerne. Hvis du vil se, hvilke tilladelser du skal bruge, skal du se posten "Transportregler" under emnet Meddelelsespolitik og overholdelsestilladelser.

3. Kør **Cmdlet'en Get-FocusedInbox** , f.eks.: 

    ```powershell
    Get-FocusedInbox -Identity <tim@contoso.com>
    ```

4. Se efter FocusedInboxOn for at få vist den aktuelle indstilling:

    ![Svar fra PowerShell om tilstanden for Fokuseret indbakke.](../../media/419d8caa-89b9-45c5-91d9-8c023297456e.png)
  
5. Kør følgende cmdlet for at deaktivere Fokuseret indbakke:

    ```powershell
    Set-FocusedInbox -Identity <tim@contoso.com> -FocusedInboxOn $false
    ```

    ELLER kør følgende cmdlet for at aktivere den:

    ```powershell
    Set-FocusedInbox -Identity <tim@contoso.com> -FocusedInboxOn $true
    ```

## <a name="use-the-ui-to-create-a-transport-rule-to-direct-email-messages-to-the-focused-view-for-all-your-users"></a>Brug brugergrænsefladen til at oprette en transportregel til at dirigere mails til Fokuseret visning for alle dine brugere

1. Gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange Administration</a>.

2. Gå til **Regler for mailflow**\>. Vælg ![EAC-ikonet Tilføj.](../../media/795e5bdd-48bb-433f-8e07-3c7a19f8eca2.gif) og derefter vælge **Opret en ny regel...**. 

3. Når du er færdig med at oprette den nye regel, skal du **vælge Gem** for at starte reglen.

    Følgende billede viser et eksempel, hvor alle meddelelser fra "Lønafdeling" skal leveres til Fokuseret indbakke.

    ![focusedinbox løn.](../../media/focusedinbox-transport-rule.PNG)

    > [!NOTE]
    > Teksten i meddelelsens overskriftsværdi i dette eksempel er **X-MS-Exchange-Organization-BypassFocusedInbox**.
  
## <a name="use-powershell-to-create-a-transport-rule-to-direct-email-messages-to-the-focused-view-for-all-your-users"></a>Brug PowerShell til at oprette en transportregel til at dirigere mails til Fokuseret visning for alle dine brugere

1. [Forbind til Exchange Online bruge Remote PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Du skal have tildelt tilladelser, før du kan udføre proceduren eller procedurerne. Se hvilke tilladelser, du skal bruge, i posten "Transportregler" under Meddelelsespolitik [og overholdelsestilladelser](/exchange/messaging-policy-and-compliance-permissions-exchange-2013-help).

3. Kør følgende kommando for at tillade, at alle meddelelser fra "Lønafdeling" f.eks. bliver leveret til Fokuseret indbakke.

    ```powershell
    New-TransportRule -Name <name_of_the_rule> -From "Payroll Department" -SetHeaderName "X-MS-Exchange-Organization-BypassFocusedInbox" -SetHeaderValue "true"
    ```

> [!IMPORTANT]
> I dette eksempel er der både store og små bogstaver i både "X-MS-Exchange-Organization-BypassFocusedInbox" og "true".
> Desuden vil Fokuseret indbakke efterkomme X-overskriften, der tilsidesætter Clutter, så hvis du bruger denne indstilling i Clutter, bruges den i Fokuseret indbakke. Du kan finde detaljerede oplysninger om syntaks og parameter [i New-TransportRule](/powershell/module/exchange/new-transportrule).

### <a name="how-do-you-know-this-worked"></a>Hvordan ved du, at det virkede?

Du kan kontrollere brevhoveder i mails for at se, om mails lander i indbakken på grund af Fokuseret indbakkes transportregel for bypass. Vælg en mail fra en postkasse i organisationen, der har transportreglen for Fokuseret indbakke anvendt. Se på brevhovederne på meddelelsen, og du bør kunne se **overskriften X-MS-Exchange-Organization-BypassFocusedInbox: true**. Det betyder, at bypass'en fungerer. Se artiklen Få [vist oplysninger om internetoverskriften for at få oplysninger](https://go.microsoft.com/fwlink/p/?LinkId=822530) om, hvordan du finder oplysningerne om brevhovedet.

### <a name="what-will-the-user-see"></a>Hvad vil brugeren se?

Hvis der er en transportregel på plads, vises en meddelelse om tilsidesættelsen. Outlook på internettet deaktiverer "Flyt altid til Andre" og viser et værktøjstip. Outlook klienter på skrivebordet giver mulighed for at vælge "Flyt altid til Andre", og der åbnes en dialogboks.

## <a name="turn-onoff-clutter"></a>Slå Clutter til/fra

Vi har modtaget rapporter om, at Clutter pludselig ikke længere virker for nogle brugere. Hvis dette sker, kan du aktivere det igen for bestemte brugere. Se [Konfigurer Clutter i din organisation](../email/configure-clutter.md).

## <a name="faq-for-focused-inbox"></a>Ofte stillede spørgsmål om Fokuseret indbakke

Her finder du svar på ofte stillede spørgsmål om Fokuseret indbakke.

### <a name="can-i-control-how-i-roll-out-focused-inbox-in-my-organization"></a>Kan jeg styre, hvordan jeg udruller Fokuseret indbakke i min organisation?

Ja. Du kan slå Fokuseret indbakke til eller fra for hele organisationen, eller du kan slå den til eller fra for bestemte brugere. Se ovenfor.
  
### <a name="is-the-focused-inbox-feature-only-available-for-office-2016-clients"></a>Er funktionen Fokuseret indbakke KUN tilgængelig for Office 2016-klienter?

Ja, kun brugere med Office 2016 påvirkes. Funktionen bliver ikke tilbageporteret til Outlook 2013 eller tidligere.
  
### <a name="how-long-does-it-take-for-focused-inbox-changes-to-take-place-in-outlook"></a>Hvor lang tid tager det for ændringer i Fokuseret indbakke at finde sted i Outlook?

Når du aktiverer eller deaktiverer Fokuseret indbakke, træder indstillingerne i kraft, når brugerne lukker og genstarter Outlook.
  
### <a name="what-happens-to-clutter-once-i-turn-on-focused-inbox"></a>Hvad sker der med Clutter, når jeg slår Fokuseret indbakke til?

Når du har skiftet, får du ikke længere mails, der i mindre grad kan handles på, i mappen Clutter. I stedet opdeles mail mellem fanerne Fokuseret og Andre i din indbakke. Den samme algoritme, der flyttede elementer til mappen Clutter, bruges nu til Fokuseret indbakke, hvilket betyder, at alle mails, der blev konfigureret til at flytte til Clutter, nu flyttes til Andre. Alle meddelelser, der allerede findes i mappen Clutter, forbliver der, indtil du beslutter dig for at slette eller flytte dem.
  
Se dette indlæg fra [Tony Redmond](https://www.petri.com/author/tony-redmond), Microsoft MVP: Sådan erstatter [Fokuseret indbakke Clutter i Office 365](https://www.petri.com/focused-inbox-office-365).
  
### <a name="can-i-keep-users-on-clutter-what-is-microsofts-recommendation-when-it-comes-to-using-clutter-vs-focused-inbox"></a>Kan jeg fortsat have brugere på Clutter? Hvad er Microsofts anbefaling med hensyn til brugen af Clutter vs Fokuseret indbakke?

Ja, du kan beholde brugere på Clutter og deaktivere Fokuseret indbakke, men Clutter vil med tiden blive udskiftet helt med Fokuseret indbakke, så Microsoft anbefaler at flytte til Fokuseret indbakke nu. Hvis du vil have mere at vide om, hvornår du bruger Clutter Exchange Online, skal du se dette blogindlæg: Opdatering om Fokuseret [indbakke og vores planer for Clutter](https://techcommunity.microsoft.com/t5/Outlook-Blog/Update-on-Focused-Inbox-and-our-plans-for-Clutter/ba-p/136448).
  
### <a name="should-i-disable-clutter-for-my-end-users-if-we-are-going-to-move-everyone-to-focused-inbox"></a>Skal jeg deaktivere Clutter for mine slutbrugere, hvis alle skal flyttes til Fokuseret indbakke?

Nej. Det er muligt at deaktivere Clutter eksplicit for en postkasse ved at køre Set-Clutter cmdlet'en. Men hvis du gør dette, får postkasseejeren vist meddelelser, der tidligere er blevet omdirigeret til mappen Clutter, i indbakken, og de er nødt til at behandle disse meddelelser, indtil klienten er blevet opgraderet til en version, der understøtter Fokuseret indbakke. Det er derfor bedst ikke at deaktivere Clutter, før de opgraderede klienter er tilgængelige.
  
### <a name="why-are-there-two-different-cmdlets-for-managing-focused-inbox"></a>Hvorfor er der to forskellige cmdlet'er til administration af Fokuseret indbakke?

Der er to tilstande knyttet til Fokuseret indbakke.
  
- **Organisationsniveau**: Tilstand for Fokuseret indbakke og et tilknyttet tidsstempel for seneste opdatering.

- **Postkasseniveau**: Tilstand for Fokuseret indbakke og et tilknyttet tidsstempel for seneste opdatering 

### <a name="how-does-outlook-decide-to-show-the-focused-inbox-experience-with-these-two-states"></a>Hvordan beslutter Outlook at vise Fokuseret indbakke-oplevelsen med disse to tilstande?

Outlook beslutter at vise oplevelsen ved at vælge, hvilken cmdlet der har det seneste tidsstempel. Som standard er begge tidsstempler "null", og i dette tilfælde er funktionen aktiveret.
  
### <a name="why-does-the-get-focusedinbox-cmdlet-return-true-when-ive-turned-focused-inbox-off-in-my-organization"></a>Hvorfor returnerer Get-FocusedInbox "sand", når jeg har slået Fokuseret indbakke fra i min organisation?

Der er to cmdlet'er til at styre Fokuseret indbakke. Når du kører Get-FocusedInbox for en postkasse, returnerer den funktionens tilstand på postkasseniveau. Oplevelsen i Outlook baseret på, hvilken cmdlet-tilstand der senest blev ændret.
  
### <a name="can-i-run-a-script-to-see-who-has-turned-on-focused-inbox"></a>Kan jeg køre et script for at se, hvem der har aktiveret Fokuseret indbakke?

Nej, og det er tilstr brug. Aktivering af Fokuseret indbakke er en indstilling på klientsiden, så alt, hvad cmdlet'en kan gøre, er at fortælle dig, om brugerens postkasse er berettiget til klientoplevelsen. Det er muligt at aktivere funktionen samtidigt i nogle klienter og deaktivere den i andre, f.eks. aktiveret i Outlook-appen og Outlook Mobile, men deaktiveret i Outlook på internettet.

## <a name="related-content"></a>Relateret indhold

[Konfigurer Clutter i din organisation](../email/configure-clutter.md) (artikel)\
[Konfigurer indstillinger for delt postkasse](../email/configure-a-shared-mailbox.md) (artikel)\
[Opret signaturer og ansvarsfraskrivelser](create-signatures-and-disclaimers.md) (video)
