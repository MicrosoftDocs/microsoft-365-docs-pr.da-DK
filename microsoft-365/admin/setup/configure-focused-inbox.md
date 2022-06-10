---
title: Konfigurer Fokuseret indbakke for alle i din organisation
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
description: Hvis du er ansvarlig for at konfigurere mailindstillinger for alle i en virksomhed, forklares det i denne artikel, hvordan du konfigurerer Fokuseret indbakke for brugere.
ms.openlocfilehash: 9c3b17c632c2316f3c36a4f79362895d790b1c7b
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/10/2022
ms.locfileid: "66010206"
---
# <a name="configure-focused-inbox-for-everyone-in-your-organization"></a>Konfigurer Fokuseret indbakke for alle i din organisation

Hvis du er ansvarlig for at konfigurere, hvordan mail fungerer for ALLE i en virksomhed, er denne artikel noget for dig! Den forklarer, hvordan du tilpasser den eller slår den fra for din virksomhed, og den besvarer [ofte stillede spørgsmål](#faq-for-focused-inbox).

Hvis du kun vil slå Fokuseret indbakke fra for dig selv, skal du se [Slå Fokuseret indbakke fra](https://support.microsoft.com/office/f714d94d-9e63-4217-9ccb-6cb2986aa1b2).  

Hvis du vil være sikker på, at brugerne modtager virksomhedsspecifikke mails, f.eks. fra HR eller lønningslisten, kan du konfigurere Fokuseret indbakke, så disse meddelelser når visningen Fokuseret. Du kan også styre, om brugerne i din organisation kan se Fokuseret indbakke i deres postkasse.
  
## <a name="turn-focused-inbox-on-or-off-in-your-organization"></a>Slå Fokuseret indbakke til eller fra i din organisation

Du kan bruge PowerShell til at slå Fokuseret indbakke til eller fra for alle i din organisation. Vil du gøre dette i Microsoft 365 Administration? Fortæl vores teknikerteam det. **[Stem her!](https://go.microsoft.com/fwlink/?linkid=862489)**
  
**Sådan slår du Fokuseret indbakke fra:**
  
I følgende PowerShell-eksempel slås Fokuseret indbakke **fra** i din organisation. Det blokerer dog ikke for tilgængeligheden af funktionen for dine brugere. Hvis de vil, kan de stadig genaktivere Fokuseret indbakke på hver af deres klienter. 
  
1. [Forbind til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Du skal have tildelt tilladelser, før du kan udføre denne procedure eller disse procedurer. Hvis du vil se, hvilke tilladelser du har brug for, skal du se posten "Transportregler" i [Meddelelsespolitik og tilladelser til overholdelse af angivne standarder](/exchange/messaging-policy-and-compliance-permissions-exchange-2013-help).

3. Kør cmdlet'en **Get-OrganizationConfig** . 

    ```powershell
    Get-OrganizationConfig
    ```

4. Søg efter **FocusedInboxOn** for at få vist den aktuelle indstilling: 

    ![Svar fra PowerShell om tilstanden fokuseret indbakke.](../../media/419d8caa-89b9-45c5-91d9-8c023297456e.png)
  
5. Kør følgende cmdlet for at slå Fokuseret indbakke fra.

    ```powershell
    Set-OrganizationConfig -FocusedInboxOn $false
    ```

6. Kør **Cmdlet'en Get-OrganizationConfig** igen, så kan du se, at FocusedInboxOn er indstillet til $false, hvilket betyder, at den er blevet deaktiveret. 

**Sådan slår du Fokuseret indbakke til:**
  
- I trin 5 ovenfor skal du køre følgende cmdlet for at slå Fokuseret indbakke til.

  ```powershell
  Set-OrganizationConfig -FocusedInboxOn $true
  ```
    
## <a name="what-do-users-see-after-i-turn-on-focused-inbox"></a>Hvad kan brugerne se, når jeg har slået Fokuseret indbakke til?

Brugerne får først vist visningen Fokuseret, når de lukker og genstarter Outlook. Når de genstarter Outlook, får de vist et tip i den Outlook brugergrænseflade, der giver dem mulighed for at bruge den nye Fokuseret indbakke.
  
![Et billede af, hvordan Fokuseret indbakke ser ud, når en bruger åbner Outlook på internettet første gang.](../../media/f6ef79e7-0f4c-4a23-b6f0-7c15d927b5f0.png)
  
Hvis du skifter fra Clutter til Fokuseret indbakke, kan vedkommende vælge at aktivere den ("Prøv det") eller afvise funktionen. Hvis brugeren har flere (understøttede) klienter, kan de aktivere/deaktivere Fokuseret indbakke individuelt på hver enkelt. Tip ser sådan ud:
  
![Et billede af, hvordan fokuseret indbakke ser ud, når den udrulles til dine brugere, og Outlook åbnes igen.](../../media/c034f969-d650-4333-88f1-dd10ade0a94c.png)
  
Når en bruger beslutter at begynde at bruge Fokuseret indbakke, deaktiveres Clutter automatisk. Mappen Clutter konverteres til en standardmappe, der gør det muligt for brugeren at omdøbe eller slette den.
  
## <a name="turn-focused-inbox-on-or-off-for-specific-users"></a>Slå Fokuseret indbakke til eller fra for bestemte brugere

I dette eksempel slås Fokuseret indbakke **fra** for Tim Matthews i Contoso-organisationen. Det blokerer dog ikke tilgængeligheden af funktionen for ham. Hvis han vil, kan han stadig aktivere Fokuseret indbakke igen for hver af sine klienter. 
  
1. [Forbind til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Du skal have tildelt tilladelser, før du kan udføre denne procedure eller disse procedurer. Hvis du vil se, hvilke tilladelser du har brug for, skal du se posten "Transportregler" under emnet Meddelelsespolitik og tilladelser til overholdelse af angivne standarder.

3. Kør cmdlet'en **Get-FocusedInbox** , f.eks.: 

    ```powershell
    Get-FocusedInbox -Identity <tim@contoso.com>
    ```

4. Søg efter FocusedInboxOn for at få vist den aktuelle indstilling:

    ![Svar fra PowerShell om tilstanden fokuseret indbakke.](../../media/419d8caa-89b9-45c5-91d9-8c023297456e.png)
  
5. Kør følgende cmdlet for at slå Fokuseret indbakke fra:

    ```powershell
    Set-FocusedInbox -Identity <tim@contoso.com> -FocusedInboxOn $false
    ```

    ELLER kør følgende cmdlet for at aktivere den:

    ```powershell
    Set-FocusedInbox -Identity <tim@contoso.com> -FocusedInboxOn $true
    ```

## <a name="use-the-ui-to-create-a-transport-rule-to-direct-email-messages-to-the-focused-view-for-all-your-users"></a>Brug brugergrænsefladen til at oprette en transportregel for at sende mails til visningen Fokuseret for alle dine brugere

1. Gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange Administration</a>.

2. Naviger til **regler for** **mailflow**\>. Vælg ![ikonet Tilføj eAC.](../../media/795e5bdd-48bb-433f-8e07-3c7a19f8eca2.gif) og vælg derefter **Opret en ny regel...**. 

3. Når du er færdig med at oprette den nye regel, skal du vælge **Gem** for at starte reglen.

    På følgende billede vises et eksempel på, hvor alle meddelelser fra "Lønafdeling" skal leveres til fokuseret indbakke.

    ![focusedinbox løn.](../../media/focusedinbox-transport-rule.PNG)

    > [!NOTE]
    > Teksten i meddelelsens overskriftsværdi i dette eksempel er **X-MS-Exchange-Organization-BypassFocusedInbox**.
  
## <a name="use-powershell-to-create-a-transport-rule-to-direct-email-messages-to-the-focused-view-for-all-your-users"></a>Brug PowerShell til at oprette en transportregel for at sende mails til visningen Fokuseret for alle dine brugere

1. [Forbind til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Du skal have tildelt tilladelser, før du kan udføre denne procedure eller disse procedurer. Hvis du vil se, hvilke tilladelser du har brug for, skal du se posten "Transportregler" i [Meddelelsespolitik og tilladelser til overholdelse af angivne standarder](/exchange/messaging-policy-and-compliance-permissions-exchange-2013-help).

3. Kør følgende kommando for at tillade, at alle meddelelser fra f.eks. lønafdelingen leveres til fokuseret indbakke.

    ```powershell
    New-TransportRule -Name <name_of_the_rule> -From "Payroll Department" -SetHeaderName "X-MS-Exchange-Organization-BypassFocusedInbox" -SetHeaderValue "true"
    ```

> [!IMPORTANT]
> I dette eksempel skelnes der mellem store og små bogstaver i både "X-MS-Exchange-Organization-BypassFocusedInbox" og "true".
> Fokuseret indbakke vil også overholde X-headeren, der tilsidesætter Clutter, så hvis du bruger denne indstilling i Clutter, bruges den i Fokuseret indbakke. Du kan finde detaljerede oplysninger om syntaks og parametre under [New-TransportRule](/powershell/module/exchange/new-transportrule).

### <a name="how-do-you-know-this-worked"></a>Hvordan ved du, det virkede?

Du kan kontrollere brevhoveder i mails for at se, om mailmeddelelserne lander i indbakken på grund af reglen for transport af fokuseret indbakke. Vælg en mail fra en postkasse i din organisation, hvor transportreglen Fokuseret indbakke er anvendt. Kig på de overskrifter, der er stemplet på meddelelsen, og du kan se **X-MS-Exchange-Organization-BypassFocusedInbox: true** header. Det betyder, at bypass fungerer. Se artiklen [Vis oplysninger om internetheader for en mail](https://go.microsoft.com/fwlink/p/?LinkId=822530) for at få oplysninger om, hvordan du finder headeroplysningerne.

### <a name="what-will-the-user-see"></a>Hvad får brugeren vist?

Hvis der er en transportregel på plads, vises der en meddelelse for tilsidesættelsen. Outlook på internettet deaktiverer "Flyt altid til andet" og viser et værktøjstip. Outlook klienter på skrivebordet gør det muligt at vælge "Flyt altid til andet" og åbner en dialogboks.

## <a name="turn-onoff-clutter"></a>Slå Clutter til/fra

Vi har modtaget rapporter om, at Clutter pludselig holdt op med at arbejde for nogle brugere. Hvis det sker, kan du aktivere det igen for bestemte brugere. Se [Konfigurer Clutter for din organisation](../email/configure-clutter.md).

## <a name="faq-for-focused-inbox"></a>Ofte stillede spørgsmål om fokuseret indbakke

Her er svar på ofte stillede spørgsmål om fokuseret indbakke.

### <a name="can-i-control-how-i-roll-out-focused-inbox-in-my-organization"></a>Kan jeg styre, hvordan jeg udruller Fokuseret indbakke i min organisation?

Ja. Du kan slå Fokuseret indbakke til eller fra for hele organisationen, eller du kan slå den til eller fra for bestemte brugere. Se ovenfor.
  
### <a name="is-the-focused-inbox-feature-only-available-for-office-2016-clients"></a>Er funktionen Fokuseret indbakke KUN tilgængelig for Office 2016-klienter?

Ja, kun brugere med Office 2016 påvirkes. Funktionen vil ikke blive tilbageporteret til Outlook 2013 eller tidligere.
  
### <a name="how-long-does-it-take-for-focused-inbox-changes-to-take-place-in-outlook"></a>Hvor lang tid tager det, før ændringer i Fokuseret indbakke finder sted i Outlook?

Når du slår Fokuseret indbakke til eller fra, træder indstillingerne i kraft, når brugerne lukker og genstarter Outlook.
  
### <a name="what-happens-to-clutter-once-i-turn-on-focused-inbox"></a>Hvad sker der med Clutter, når jeg aktiverer Fokuseret indbakke?

Når du har skiftet, modtager du ikke længere mindre handlingsvenlige mails i mappen Clutter. Mail opdeles i stedet mellem fanerne Fokuseret og Andet i din indbakke. Den samme algoritme, der flyttede elementer til Clutter-mappen, driver nu Fokuseret indbakke, hvilket betyder, at alle mails, der er angivet til at flytte til Clutter, nu flyttes til Andet. Alle meddelelser, der allerede findes i din Clutter-mappe, forbliver der, indtil du beslutter dig for at slette eller flytte dem.
  
Tjek dette indlæg af [Tony Redmond](https://www.petri.com/author/tony-redmond), Microsoft MVP: [Hvordan fokuseret indbakke erstatter Clutter Inside Office 365](https://www.petri.com/focused-inbox-office-365).
  
### <a name="can-i-keep-users-on-clutter-what-is-microsofts-recommendation-when-it-comes-to-using-clutter-vs-focused-inbox"></a>Kan jeg holde brugerne på Clutter? Hvad anbefaler Microsoft, når det drejer sig om at bruge Clutter vs. Fokuseret indbakke?

Ja, du kan beholde brugere på Clutter og deaktivere Fokuseret indbakke, men til sidst erstattes Clutter helt med Fokuseret indbakke, så Microsoft anbefaler, at du flytter til Fokuseret indbakke nu. Du kan få mere at vide om, hvornår du bruger Clutter med Exchange Online, i dette blogindlæg: [Opdater fokuseret indbakke og vores planer for Clutter](https://techcommunity.microsoft.com/t5/Outlook-Blog/Update-on-Focused-Inbox-and-our-plans-for-Clutter/ba-p/136448).
  
### <a name="should-i-disable-clutter-for-my-end-users-if-we-are-going-to-move-everyone-to-focused-inbox"></a>Skal jeg deaktivere Clutter for mine slutbrugere, hvis vi skal flytte alle til Fokuseret indbakke?

Nej. Det er muligt at deaktivere Clutter for en postkasse eksplicit ved at køre Set-Clutter-cmdlet'en. Men hvis du gør dette, vil ejeren af postkassen se meddelelser, der tidligere er omdirigeret til clutter-mappen, blive i indbakken, og de bliver nødt til at behandle disse meddelelser, indtil deres klient opgraderes til en version, der understøtter Fokuseret indbakke. Det er derfor bedst ikke at deaktivere Clutter, før de opgraderede klienter er tilgængelige.
  
### <a name="why-are-there-two-different-cmdlets-for-managing-focused-inbox"></a>Hvorfor er der to forskellige cmdlet'er til administration af fokuseret indbakke?

Der er knyttet to tilstande til Fokuseret indbakke.
  
- **Organisationsniveau**: Fokuseret indbakketilstand og et tilknyttet tidsstempel for seneste opdatering.

- **Postkasseniveau**: Fokuseret indbakketilstand og et tilknyttet tidsstempel for seneste opdatering 

### <a name="how-does-outlook-decide-to-show-the-focused-inbox-experience-with-these-two-states"></a>Hvordan beslutter Outlook at vise oplevelsen fokuseret indbakke med disse to tilstande?

Outlook beslutter at vise oplevelsen ved at vælge, hvilken cmdlet der har det seneste tidsstempel. Begge tidsstempler er som standard "null", og i dette tilfælde er funktionen aktiveret.
  
### <a name="why-does-the-get-focusedinbox-cmdlet-return-true-when-ive-turned-focused-inbox-off-in-my-organization"></a>Hvorfor returnerer Get-FocusedInbox-cmdlet'en "sand", når jeg har slået Fokuseret indbakke fra i min organisation?

Der er to cmdlet'er til styring af fokuseret indbakke. Når du kører Get-FocusedInbox for en postkasse, returneres funktionens postkasseniveautilstand. Oplevelsen i Outlook vælges ud fra, hvilken cmdlet-tilstand der sidst blev ændret.
  
### <a name="can-i-run-a-script-to-see-who-has-turned-on-focused-inbox"></a>Kan jeg køre et script for at se, hvem der har aktiveret Fokuseret indbakke?

Nej, og det er tilsigtet. Fokuseret indbakkeaktivering er en indstilling på klientsiden, så alt cmdlet'en kan fortælle dig, om brugerens postkasse er berettiget til klientoplevelsen. Det er muligt, at den aktiveres samtidig i nogle klienter og deaktiveres i andre, f.eks. aktiveret i Outlook app og Outlook Mobile, men deaktiveret i Outlook på internettet.

## <a name="related-content"></a>Relateret indhold

[Konfigurer Clutter for din organisation](../email/configure-clutter.md) (artikel)\
[Konfigurer indstillinger for delt postkasse](../email/configure-a-shared-mailbox.md) (artikel)\
[Opret signaturer og ansvarsfraskrivelser](create-signatures-and-disclaimers.md) (video)
