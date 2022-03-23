---
title: Planlæg din konfiguration af Microsoft 365 til virksomheder
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_O365_Setup
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- okr_smb
search.appverid:
- MET150
- MOE150
ms.assetid: eb926624-018b-4486-bf11-5fba6ee4d645
description: Få mere at vide om krav og overvejelser i forbindelse med at skifte Microsoft 365 til virksomheder.
ms.openlocfilehash: 1012e854d514212ae3c5c970347255936ea94f1a
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63588081"
---
# <a name="plan-your-setup-of-microsoft-365-for-business"></a>Planlæg din konfiguration af Microsoft 365 til virksomheder

Denne artikel er til personer, der abonnerer på en Microsoft 365 for Business-plan.
  
Før du flytter din organisation Microsoft 365, er der krav, du skal opfylde, oplysninger, du skal have ved hånden, og beslutninger, du skal træffe.

## <a name="overview-of-microsoft-365-business-premium-setup"></a>Oversigt over Microsoft 365 Business Premium konfiguration

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4jZwg?autoplay=false]

Tillykke med din beslutning om at flytte din virksomhed til skyen med Microsoft 365! Uanset om du har én person i din virksomhed eller 20, kan du planlægge lidt for at få mest muligt ud Microsoft 365 Business Premium.

## <a name="info-to-have-on-hand-before-you-run-the-setup-wizard"></a>Oplysninger, du skal have ved hånden, før du kører konfigurationsguiden

Når du er klar til at køre konfigurationsguiden og flytte dit domæne til Microsoft 365, er her de oplysninger, du skal have ved hånden:
  
- Liste over personer, du vil føje til Microsoft 365. Selvom du allerede har føjet dem til Microsoft 365, skal du angive deres navne her, hvis du opdaterer dine domæneoplysninger.

- Hvordan du vil give dine medarbejdere besked om deres bruger-id og adgangskode, så de kan logge på. Vil du ringe til dem med oplysningerne? Eller sende den til deres personlige mailadresse? De har ikke adgang til deres mail, så du kan ikke bruge den.

- Hvis du har et domænenavn til organisationen (f.eks. contoso.com), og du planlægger  at bruge Microsoft-mail, skal du vide, hvor dit domæne er registreret og have logonoplysninger.

## <a name="what-happens-when-you-run-the-microsoft-365-setup-wizard"></a>Hvad sker der, når du kører Microsoft 365 konfigurationsguiden?

Konfigurationsguiden hjælper dig med at installere Microsoft 365-apps på computeren, tilføje og bekræfte dit domæne, tilføje brugere og tildele licenser til dem og forbinde dit domæne.

> [!NOTE]
> Hvis du har brug [for at tildele administratorroller i Microsoft 365 til virksomheder](../add-users/assign-admin-roles.md) til de brugere, du tilføjer i guiden, kan du gøre det senere på **siden** Brugere. 
  
Hvis du ikke fuldfører konfigurationsguiden, kan du når som helst fuldføre konfigurationsopgaver [fra](https://go.microsoft.com/fwlink/p/?linkid=2024339) >  **AdministrationKonfiguration**. Herfra kan du overføre mail og kontakter fra en anden mailtjeneste, ændre domænet for din administratorkonto, administrere dine faktureringsoplysninger, tilføje eller fjerne brugere, nulstille adgangskoder og udføre andre virksomhedsfunktioner. Du kan finde flere oplysninger om forskellene mellem konfigurationsguiden  og siden Konfiguration under [Forskelle Microsoft 365 konfigurationsguiden og siden Konfiguration](o365-setup-wizard-and-setup-page.md).

Hvis du på et tidspunkt sidder fast, kan du ringe til os. [Vi er her for at hjælpe!](../../business-video/get-help-support.md)
  
## <a name="when-not-to-use-the-setup-wizard-active-directory-synchronization-and-hybrid-environments"></a>Hvornår skal du ikke bruge konfigurationsguiden: Active Directory-synkronisering og hybridmiljøer

Der er et par scenarier, der omfatter enten overførsel af data eller brugere fra lokale miljøer eller konfiguration af et hybridsystem, der omfatter katalogsynkronisering. Hvis du er i en af kategorierne, skal du følge vejledningen i følgende artikler:
  
- Hvis du vil konfigurere katalogsynkronisering med dit lokale Active Directory, skal du se Konfigurer katalogsynkronisering [til Microsoft 365 og for](../../enterprise/set-up-directory-synchronization.md) at forstå de forskellige identitetsmodeller i Microsoft 365 skal du læse Installér din identitetsinfrastruktur [til Microsoft 365](../../enterprise/deploy-identity-solution-overview.md).

- Hvis du vil konfigurere en Exchange-hybrid, kan du finde det fulde sæt af instruktioner, der hjælper dig gennem alle de forskellige måder at konfigurere en hybrid exchange (herunder konfiguration af DNS-poster), her: [Exchange Server Deployment Assistant](/exchange/exchange-deployment-assistant)

- Hvis du vil konfigurere SharePoint hybrid, især hybridsøgning og webstedsfunktioner, skal du [se Hybridsøgning i SharePoint](/SharePoint/hybrid/hybrid-search-in-sharepoint).

## <a name="move-to-microsoft-365-all-at-once-or-in-stages"></a>Flyt til Microsoft 365 på én gang eller i faser

- **Vil du flytte din organisation til Microsoft 365 på én gang?** Hvis det er ja, skal du planlægge at flytte dit domæne Microsoft 365 med det samme. Start med at køre Microsoft 365 konfigurationsguiden. Den beder dig om at konfigurere dit domæne.

- **Vil du flytte til Microsoft 365 gradvist?** Hvis du vil flytte til Microsoft 365 trin, skal du springe over at køre guiden Microsoft 365 konfiguration og overveje at Microsoft 365 funktioner i følgende rækkefølge:

    1. [Føj dine medarbejdere til en Microsoft 365](../add-users/add-users.md), så de kan downloade og installere Office apps.

    2. [Download og installér Office apps](https://support.microsoft.com/office/4414eaaf-0478-48be-9c42-23adc4716658) for at bruge Word, Excel og PowerPoint på din computer og dine enheder.

    3. [Konfigurer Microsoft Teams til](#plan-for-teams) at bruge til dine møder.

    4. [Flyt dit indhold til Microsoft 365 skylager](set-up-file-storage-and-sharing.md) (OneDrive eller SharePoint-teamwebsteder).

    5. Når du er klar, skal du i [](https://go.microsoft.com/fwlink/p/?linkid=2024339)Administration vælge Konfiguration i  venstre navigationsrude og bruge siden Konfiguration til [at flytte dit domæne og din mail](add-domain.md).

## <a name="check-that-your-devices-meet-system-requirements"></a>Kontrollér, at dine enheder opfylder systemkravene

Hver person i din organisation kan installere Office 2016-pakken af apps (Word, Excel, PowerPoint osv.) på op til fem pc'er og Mac-computere. Se operativsystemet og computerkravene til installation af [Office 2016-pakker til](https://go.microsoft.com/fwlink/?LinkId=534827) virksomheder.
  
Mobilapps kan installeres på iOS-, Android- og Windows enheder. Du kan finde oplysninger om mobilenheds- og browsersupport [i Systemkrav til Office](https://go.microsoft.com/fwlink/?LinkId=534827).
  
## <a name="plan-for-email"></a>Planlæg mail

Hvis du planlægger at flytte fra en eksisterende mailtjeneste til Microsoft 365, tager det normalt to dage at skifte.
  
### <a name="plan-for-email-downtime"></a>Planlægning af mail-nedetid
  
Hvis du vil bruge en Microsoft 365 til din mail:
  
- Hvis du vil flytte din virksomheds mailadresse (f.eks *. rob\@ contoso.com*) fra en anden mailtjeneste til Microsoft 365, skal du dirigere din mail, så den leveres til din nye Microsoft 365-postkasse. Det gør du ved at vælge Overfør dine brugeres **data** på  siden Konfiguration, hvor vi trinvist fører dig gennem de opdateringer, du skal foretage på din domænevært.

- Når du har opdateret din domænevært, træder ændringerne typisk i kraft efter blot en time eller to. Men vær opmærksom på, at det nogle gange kan tage op til 72 timer, før ændringerne opdateres på tværs af internettet.

- Da du muligvis har nedetid for mails, anbefaler vi, at du planlægger at skifte til Microsoft-mail om aftenen eller i weekenden, hvor du modtager færre mails.

### <a name="plan-to-move-your-existing-email-contacts-and-calendar"></a>Planlæg at flytte dine eksisterende mails, kontakter og kalender
  
Hvis du vil bruge en Microsoft 365 din mailkonto, kan du tage dine eksisterende mails, kontakter og kalender med dig. Siden **Konfiguration** hjælper dig med at flytte dine eksisterende mails og kontakter for de fleste scenarier. Vi har også trinvise vejledninger til at flytte en eller mange postkasser.
  
|**Hvor mange postkasser?**|**Anbefaling**|
|:-----|:-----|
|Kun nogle få  <br/> |Hvis du ikke vil bruge siden Konfiguration til at  overføre postkasser, kan du lade postkasseejere overføre deres egne mails og kontakter. Se [Overfør mail og kontakter Microsoft 365 til virksomheder](migrate-email-and-contacts-admin.md).  <br/> |
|Flere  <br/> |Hvis du overfører fra Gmail, skal du se [Overføre G Suite-postkasser for at Microsoft 365](/Exchange/mailbox-migration/migrating-imap-mailboxes/migrate-g-suite-mailboxes).  <br/> Hvis du overfører fra en anden mailudbyder, herunder Exchange, skal du se Sådan kan du [overføre flere mailkonti til Microsoft 365](/Exchange/mailbox-migration/mailbox-migration).  <br/> |

## <a name="plan-for-file-storage-and-migration"></a>Planlæg fillagring og -overførsel

Microsoft 365 indeholder skylagring for enkeltpersoner, små organisationer og virksomheder. Du kan finde en vejledning til, hvad du skal gemme hvor[, under Hvor du kan gemme dokumenter Microsoft 365](https://support.microsoft.com/office/d18d21a0-1f9f-4f6c-ac45-d52afa0a4a2e).
  
- **Du kan flytte hundredvis af filer** til [OneDrive](https://support.microsoft.com/office/45114744-6D42-45CD-8975-F9617819BDEB) eller til et [SharePoint-teamwebsted](https://support.microsoft.com/office/da549fb1-1fcb-4167-87d0-4693e93cb7a0#__toc384119242). Du kan overføre 100 filer ad gangen. Undgå at overføre filer, der er større end 2 GB, hvilket som standard er den maksimale filstørrelse.
  
- **Hvis du vil flytte flere tusinde filer til Microsoft 365**, skal du gennemse [SharePoint Onlinegrænser](/office365/servicedescriptions/sharepoint-online-service-description/sharepoint-online-limits). Vi anbefaler, at du bruger et overflytningsværktøj eller overvejer at hyre [en partner](https://go.microsoft.com/fwlink/?linkid=391089) til at hjælpe dig med overførslen. Du kan finde oplysninger om, hvordan du overfører et stort antal filer, [SharePoint Online og OneDrive Brugervejledning til overførsel](/sharepointmigration/upload-on-premises-content-to-sharepoint-online-using-powershell-cmdlets).
  
## <a name="plan-for-teams"></a>Planlæg Teams

Du kan bruge Microsoft Teams til at foretage opkald til andre personer i organisationen, som er på dit abonnement. Hvis din organisation f.eks. har 10 personer, kan I ringe og chat med hinanden Teams uden nogen særlig konfiguration. Få mere at vide under [Introduktion til Microsoft Teams](/MicrosoftTeams/get-started-with-teams-quick-start).

For større organisationer, eller hvis du starter fra Skype for Business, lokale eller hybride installationer, skal du se Sådan udrulles [Microsoft Teams](/MicrosoftTeams/how-to-roll-out-teams).
  
## <a name="plan-for-integration-with-active-directory-or-other-software"></a>Planlæg integration med Active Directory eller anden software

- **Vil du integrere med dit lokale Active Directory?** Du kan integrere dit lokale Active Directory med Microsoft 365 ved hjælp af Azure Active Directory Forbind. Du kan finde en vejledning [under Konfigurer katalogsynkronisering for Microsoft 365](../../enterprise/set-up-directory-synchronization.md).
  
- **Vil du integrere Microsoft 365 software, der er lavet af andre virksomheder?** Hvis du har brug for at integrere Microsoft 365 anden software i din organisation, anbefaler vi, at du overvejer at hyre en [partner](https://go.microsoft.com/fwlink/?linkid=391089) til at hjælpe dig med installationen.
  
## <a name="do-you-want-someone-to-help-you-set-up-microsoft-365"></a>Skal nogen hjælpe dig med at konfigurere Microsoft 365?

- **Hvis du har færre end 50 medarbejdere:**

  - **Hvis du har brug for hjælp, ringer vi til dig**. Når du har Microsoft 365, kan du få adgang til Administration (du behøver ikke at køre konfigurationen for at få adgang til den). Nederst i Administration skal du vælge Har du **brug for hjælp?** Beskriv problemet, så ringer vi til dig. 
  - **Ring [Microsoft 365 for Business Support](../../business-video/get-help-support.md) med dine spørgsmål**. Vi er her for at hjælpe! 
  - **Overvej at hyre en [Microsoft-partner](https://go.microsoft.com/fwlink/?linkid=391089)**. Hvis du kun har lidt tid eller har avancerede krav, f.eks. flytning af tusindvis af filer til Microsoft 365 skylagring eller integration med anden software, kan en erfaren partner være en stor hjælp. 

- **Hvis du har mere end 50 medarbejdere**, kan [FastTrack Onboarding Center](https://go.microsoft.com/fwlink/?LinkId=517115) hjælpe dig med installationen.

## <a name="see-also"></a>Se også

[De 10 mest populære måder at sikre Microsoft 365 planer til virksomheder på](../security-and-compliance/secure-your-business-data.md)
