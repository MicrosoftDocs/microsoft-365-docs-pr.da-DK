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
description: Få mere at vide om kravene og overvejelserne i forbindelse med flytningen til Microsoft 365 til virksomheder.
ms.openlocfilehash: a5f777a411f82de30c1d7dc69f07f92eadbbedce
ms.sourcegitcommit: 7dc7e9fd76adf848f941919f86ca25eecc704015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/11/2022
ms.locfileid: "65317466"
---
# <a name="plan-your-setup-of-microsoft-365-for-business"></a>Planlæg din konfiguration af Microsoft 365 til virksomheder

Denne artikel henvender sig til personer, der abonnerer på en Microsoft 365 til virksomhedsplan.
  
Før du flytter din organisation til Microsoft 365, er der krav, du skal opfylde, oplysninger, du skal have ved hånden, og beslutninger, du skal træffe.

## <a name="overview-of-microsoft-365-for-business-setup"></a>Oversigt over Microsoft 365 til virksomhedskonfiguration

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4Vjso?autoplay=false]

Tillykke med din beslutning om at flytte din virksomhed til cloudmiljøet med Microsoft 365! Uanset om du har én person i din virksomhed eller 20, hjælper lidt planlægning dig med at få mest ud af Microsoft 365 for virksomheden.

## <a name="info-to-have-on-hand-before-you-run-the-setup-wizard"></a>Oplysninger, der skal være til rådighed, før du kører installationsguiden

Når du er klar til at køre installationsguiden og flytte dit domæne til Microsoft 365, skal du have følgende oplysninger ved hånden:
  
- Liste over personer, du vil føje til Microsoft 365. Selvom du allerede har føjet dem til Microsoft 365, skal du angive deres navne her, hvis du opdaterer dine domæneoplysninger.

- Sådan giver du medarbejderne besked om deres bruger-id og adgangskode, så de kan logge på. Vil du ringe til dem med informationen? Eller sende den til deres personlige mailadresse? De har ikke adgang til deres mail, så du kan ikke bruge den.

- Hvis du har et domænenavn til din organisation (f.eks. contoso.com), **og** du planlægger at bruge Microsoft-mail, skal du vide, hvor dit domæne er registreret og have logonoplysninger.

## <a name="what-happens-when-you-run-the-microsoft-365-setup-wizard"></a>Hvad sker der, når du kører installationsguiden til Microsoft 365

Installationsguiden fører dig gennem installation af de Microsoft 365 apps på computeren, tilføjelse og bekræftelse af dit domæne, tilføjelse af brugere og tildeling af licenser til dem og oprettelse af forbindelse til domænet.

> [!NOTE]
> Hvis du har brug [for at tildele administratorroller i Microsoft 365 for virksomheder til](../add-users/assign-admin-roles.md) de brugere, du tilføjer i guiden, kan du gøre det senere på siden **Brugere**. 
  
Hvis du ikke fuldfører installationsguiden, kan du når som helst fuldføre konfigurationsopgaver fra [AdministrationSæt](https://go.microsoft.com/fwlink/p/?linkid=2024339) > . Herfra kan du overføre mail og kontakter fra en anden mailtjeneste, ændre domænet for din administratorkonto, administrere dine faktureringsoplysninger, tilføje eller fjerne brugere, nulstille adgangskoder og udføre andre forretningsfunktioner. Du kan få flere oplysninger om forskellene mellem installationsguiden og siden **Installation** under [Forskelle mellem installationsguiden Microsoft 365 og siden Installation](o365-setup-wizard-and-setup-page.md).

Hvis du sidder fast på et tidspunkt, så ring til os. [Vi er her for at hjælpe!](../../business-video/get-help-support.md).
  
## <a name="when-not-to-use-the-setup-wizard-active-directory-synchronization-and-hybrid-environments"></a>Når du ikke skal bruge installationsguiden: Active Directory-synkronisering og hybridmiljøer

Der er et par scenarier, der omfatter enten overførsel af data eller brugere fra lokale miljøer eller konfiguration af et hybridsystem, der omfatter katalogsynkronisering. Hvis du er i en af kategorierne, skal du følge vejledningen i disse artikler:
  
- Hvis du vil konfigurere katalogsynkronisering med din Active Directory i det lokale miljø, skal du se [Konfigurer katalogsynkronisering for Microsoft 365](../../enterprise/set-up-directory-synchronization.md) og forstå de forskellige identitetsmodeller i Microsoft 365 ved at læse [Installér din identitetsinfrastruktur for Microsoft 365](../../enterprise/deploy-identity-solution-overview.md).

- Hvis du vil konfigurere en Exchange hybrid, kan du finde det fulde sæt instruktioner, der fører dig gennem alle de forskellige måder at konfigurere en hybridudveksling (herunder konfiguration af DNS-poster) her: [Exchange Server Installationsassistent](/exchange/exchange-deployment-assistant)

- Hvis du vil konfigurere en SharePoint hybrid, især hybride søge- og webstedsfunktioner, skal [du se Hybridsøgning i SharePoint](/SharePoint/hybrid/hybrid-search-in-sharepoint).

## <a name="move-to-microsoft-365-all-at-once-or-in-stages"></a>Flyt til Microsoft 365 alle på én gang eller i faser

- **Vil du flytte din organisation for at Microsoft 365 på én gang?** Hvis det er tilfældet, skal du planlægge at flytte dit domæne til Microsoft 365 med det samme. Start med at køre guiden Microsoft 365 installation. Du bliver bedt om at konfigurere dit domæne.

- **Vil du gradvist flytte til Microsoft 365?** Hvis du vil flytte til Microsoft 365 i faser, skal du springe over at køre installationsguiden til Microsoft 365 og overveje at anvende Microsoft 365 funktioner i følgende rækkefølge:

    1. [Føj dine medarbejdere til Microsoft 365](../add-users/add-users.md), så de kan downloade og installere Office apps.

    2. [Download og installér de Office apps](https://support.microsoft.com/office/4414eaaf-0478-48be-9c42-23adc4716658) for at bruge Word, Excel og PowerPoint på din computer og dine enheder.

    3. [Konfigurer Microsoft Teams](#plan-for-teams), der skal bruges til dine møder.

    4. [Flyt dit indhold til Microsoft 365 cloudlager](set-up-file-storage-and-sharing.md) (OneDrive eller SharePoint teamwebsteder).

    5. Når du er klar, skal du i [Administration](https://go.microsoft.com/fwlink/p/?linkid=2024339) vælge **Konfiguration** i venstre navigationsrude og bruge siden **Konfiguration** til at [flytte dit domæne og din mail](add-domain.md).

## <a name="check-that-your-devices-meet-system-requirements"></a>Kontrollér, at dine enheder opfylder systemkravene

Hver person i din organisation kan installere Office 2016-programpakken (Word, Excel, PowerPoint osv.) på op til fem pc'er og Mac-computere. Se kravene til operativsystemet og computeren for at installere [Office 2016-pakker](https://go.microsoft.com/fwlink/?LinkId=534827) til virksomheder.
  
Mobilapps kan installeres på iOS-, Android- og Windows-enheder. Du kan finde oplysninger om understøttelse af mobilenheder og browsere i [Systemkrav til Office](https://go.microsoft.com/fwlink/?LinkId=534827).
  
## <a name="plan-for-email"></a>Planlæg mail

Hvis du planlægger at flytte fra en eksisterende mailtjeneste til Microsoft 365, tager det normalt to dage at skifte.
  
### <a name="plan-for-email-downtime"></a>Planlæg nedetid for mail
  
Hvis du vil bruge Microsoft 365 til din mail:
  
- Hvis du vil flytte din virksomheds mailadresse (f.eks *. rob\@ contoso.com*) fra en anden mailtjeneste til Microsoft 365, skal du sende din mail til din nye Microsoft 365 postkasse. Det gør du ved at vælge **Overfør dine brugeres data** på siden **Konfiguration** , hvor vi guider dig gennem de opdateringer, du skal foretage hos din domænevært, trin for trin.

- Når du har opdateret din domænevært, træder ændringerne typisk i kraft om blot en time eller to. Men vær opmærksom på, at det nogle gange kan tage op til 72 timer, før ændringerne opdateres på tværs af internettet.

- Da du muligvis har nedetid for mails, anbefaler vi, at du planlægger at skifte til Microsoft-mail i løbet af en aften eller weekend, når du modtager færre mails.

### <a name="plan-to-move-your-existing-email-contacts-and-calendar"></a>Planlæg at flytte din eksisterende mail, dine kontakter og din kalender
  
Hvis du vil bruge Microsoft 365 til din mailkonto, kan du tage dine eksisterende mails, kontakter og kalender med dig. Siden **Konfiguration** hjælper dig med at flytte dine eksisterende mails og kontakter i de fleste scenarier. Vi har også trinvise vejledninger til at flytte en eller mange postkasser.
  
|**Hvor mange postkasser?**|**Anbefaling**|
|:-----|:-----|
|Kun nogle få  <br/> |Hvis du ikke vil bruge siden **Installation** til at overføre postkasserne, kan du lade postkasseejere overføre deres egne mails og kontakter. Se [Overfør mail og kontakter til Microsoft 365 til virksomheder](migrate-email-and-contacts-admin.md).  <br/> |
|Flere  <br/> |Hvis du migrerer fra Gmail, skal du se [Overfør G Suite-postkasser til Microsoft 365](/Exchange/mailbox-migration/migrating-imap-mailboxes/migrate-g-suite-mailboxes).  <br/> Hvis du migrerer fra en anden mailudbyder, herunder Exchange, skal du se [Måder at overføre flere mailkonti til Microsoft 365](/Exchange/mailbox-migration/mailbox-migration).  <br/> |

## <a name="plan-for-file-storage-and-migration"></a>Planlæg fillagring og overførsel

Microsoft 365 leverer cloudlager til enkeltpersoner, små organisationer og virksomheder. Du kan finde vejledning til, hvad du skal gemme hvor, [under Hvor du kan gemme dokumenter i Microsoft 365](https://support.microsoft.com/office/d18d21a0-1f9f-4f6c-ac45-d52afa0a4a2e).
  
- **Du kan flytte hundredvis af filer** til [OneDrive](https://support.microsoft.com/office/45114744-6D42-45CD-8975-F9617819BDEB) eller til et [SharePoint teamwebsted](https://support.microsoft.com/office/da549fb1-1fcb-4167-87d0-4693e93cb7a0#__toc384119242). Du kan uploade 100 filer ad gangen. Undgå at overføre filer, der er større end 2 GB, hvilket som standard er den maksimale filstørrelse.
  
- **Hvis du vil flytte flere tusinde filer** til Microsoft 365 lager, skal du gennemse [SharePoint Online-grænser](/office365/servicedescriptions/sharepoint-online-service-description/sharepoint-online-limits). Vi anbefaler, at du bruger et overførselsværktøj eller overvejer at hyre en [partner](https://go.microsoft.com/fwlink/?linkid=391089) til at hjælpe dig med migreringen. Du kan få oplysninger om, hvordan du overfører et stort antal filer, [i brugervejledningen SharePoint Online og OneDrive migrering](/sharepointmigration/upload-on-premises-content-to-sharepoint-online-using-powershell-cmdlets).
  
## <a name="plan-for-teams"></a>Planlæg for Teams

Du kan bruge Microsoft Teams til at foretage opkald til andre personer i din organisation, som er på dit abonnement. Hvis din organisation f.eks. har 10 personer, kan du ringe til og chatte med hinanden ved hjælp af Teams uden nogen særlig konfiguration. Du kan få flere oplysninger under [Kom i gang med Microsoft Teams](/MicrosoftTeams/get-started-with-teams-quick-start).

For større organisationer, eller hvis du starter fra Skype for Business, det lokale miljø eller hybridinstallationer, skal du se [Sådan udrulles Microsoft Teams](/MicrosoftTeams/how-to-roll-out-teams).
  
## <a name="plan-for-integration-with-active-directory-or-other-software"></a>Planlæg integration med Active Directory eller anden software

- **Vil du integrere med din Active Directory i det lokale miljø?** Du kan integrere dine Active Directory i det lokale miljø med Microsoft 365 ved hjælp af Azure Active Directory Forbind. Du kan finde en vejledning under [Konfigurer katalogsynkronisering for Microsoft 365](../../enterprise/set-up-directory-synchronization.md).
  
- **Vil du integrere Microsoft 365 med software, der er lavet af andre virksomheder?** Hvis du har brug for at integrere Microsoft 365 med anden software i din organisation, anbefaler vi, at du overvejer at [hyre en partner](https://go.microsoft.com/fwlink/?linkid=391089), der kan hjælpe dig med udrulningen.
  
## <a name="do-you-want-someone-to-help-you-set-up-microsoft-365"></a>Vil du have nogen til at hjælpe dig med at konfigurere Microsoft 365?

- **Hvis du har færre end 50 medarbejdere:**

  - **Bed om hjælp, så ringer vi til dig**. Når du har købt Microsoft 365, kan du få adgang til Administration (du behøver ikke at køre installationsprogrammet for at få adgang til det). Vælg **Har du brug for hjælp** nederst i Administration? Beskriv dit problem, så ringer vi til dig. 
  - **Ring [til Microsoft 365 for Business Support](../../business-video/get-help-support.md) med dine spørgsmål**. Vi er her for at hjælpe! 
  - **Overvej at hyre en [Microsoft-partner](https://go.microsoft.com/fwlink/?linkid=391089)**. Hvis du mangler tid eller har avancerede krav (f.eks. flytning af tusindvis af filer til Microsoft 365 cloudlager eller integration med anden software), kan en erfaren partner være en stor hjælp. 

- **Hvis du har mere end 50 medarbejdere**, er [FastTrack Onboarding Center](https://go.microsoft.com/fwlink/?LinkId=517115) tilgængeligt til at hjælpe dig med din udrulning.

## <a name="see-also"></a>Se også

[Bedste praksis for sikring af Microsoft 365 til forretningsplaner](../security-and-compliance/secure-your-business-data.md)
