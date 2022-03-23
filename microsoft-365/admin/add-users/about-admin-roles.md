---
title: Om administratorroller i Microsoft 365 Administration
f1.keywords:
- CSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: overview
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- okr_smb
- AdminTemplateSet
- admindeeplinkMAC
- adminvideo
- business_assist
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: da585eea-f576-4f55-a1e0-87090b6aaa9d
description: Administratorroller, som f.eks. tjenestens administrator, knyttes til virksomhedsfunktioner og giver tilladelse til at udføre bestemte opgaver i Administration.
ms.openlocfilehash: 5bea496ca24f3aef97a780d48c74b84aaa46176b
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/12/2022
ms.locfileid: "63587447"
---
# <a name="about-admin-roles"></a>Om administratorroller

Microsoft 365-Office 365-abonnement leveres med et sæt administratorroller, som du kan tildele til brugere i organisationen ved hjælp <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">af Microsoft 365 Administration</a>. Hver administratorrolle tilknyttes almindelige forretningsfunktioner og giver personer i organisationen tilladelse til at udføre bestemte opgaver i Administration.

Med <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 Administration</a> kan du administrere Azure AD-roller og Microsoft Intune roller. Disse roller er dog et undersæt af de roller, der er tilgængelige i Azure AD-portalen og Intune Administration.

> [!TIP]
> Hvis du har brug for hjælp til trinnene i dette emne, kan du overveje at [arbejde med en Microsoft Small Business-specialspecialist](https://go.microsoft.com/fwlink/?linkid=2186871). Med Business Assist får du og dine medarbejdere døgnet rundt adgang til små virksomhedsspecialister, efterhånden som du vokser din virksomhed, fra onboarding til daglig brug.

## <a name="watch-what-is-an-admin"></a>Se: Hvad er en administrator?

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE1SRc0]

1. Mens du er logget Microsoft 365, skal du vælge appstarteren. Hvis du kan se knappen Administrator, er du administrator.
1. Vælg **Administrator** for at gå til Microsoft 365 Administration.
1. I venstre navigationsrude skal du vælge <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">**BrugereAktivér**</a> >  brugere.
1. Vælg den person, du vil gøre til administrator. Brugerens oplysninger vises i den højre dialogboks.

## <a name="before-you-begin"></a>Før du begynder

Leder du efter den komplette liste over detaljerede beskrivelser af Azure AD-rollen, som du kan administrere <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">i Microsoft 365 Administration</a>? Se Administratorrolletilladelser i Azure Active Directory. [Indbyggede roller i Azure AD](/azure/active-directory/roles/permissions-reference).

Leder du efter en komplet liste over detaljerede Intune-rollebeskrivelser, du kan administrere <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">i Microsoft 365 Administration</a>?  Se [Rollebaseret adgangskontrol (RBAC) med Microsoft Intune](/mem/intune/fundamentals/role-based-access-control).

Du kan finde flere oplysninger om at tildele roller <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">i Microsoft 365 Administration</a> i [Tildel administratorroller](assign-admin-roles.md).

## <a name="security-guidelines-for-assigning-roles"></a>Sikkerhedsretningslinjer for tildeling af roller

Da administratorer har adgang til følsomme data og filer, anbefaler vi, at du følger disse retningslinjer for at holde din organisations data mere sikre.

| Anbefaling                  | Hvorfor er dette vigtigt?                 |
| :------------------- | :------------------- |
| Have 2 til 4 globale administratorer  | Da kun en anden global administrator kan nulstille en global administrators adgangskode, anbefaler vi, at du har mindst to globale administratorer i organisationen i tilfælde af kontospærring. Men den globale administrator har næsten ubegrænset adgang til din organisations indstillinger og de fleste data, så vi anbefaler også, at du ikke har mere end 4 globale administratorer, da det er en sikkerhedstrussel. |
| Tildel *den mindst givende* rolle    | At tildele den *mindst givtige rolle* betyder, at administratorer kun skal have adgang til at få arbejdet gjort. Hvis du f.eks. vil have nogen til at nulstille adgangskoder for medarbejdere, som du ikke skal tildele ubegrænset global administratorrolle, skal du tildele en begrænset administratorrolle, f.eks. adgangskodeadministrator eller helpdesk-administrator.  Dette er med til at beskytte dine data.                 |
| Kræv multifaktorgodkendelse for administratorer                  |    Det er faktisk en god ide at kræve MFA for alle dine brugere, men administratorer skal helt sikkert bruge MFA til at logge på. MFA gør det muligt for brugerne at angive en anden identifikationsmetode for at bekræfte, at det er dem, de mener, de er. Administratorer kan have adgang til mange kunde- og medarbejderdata, og hvis du kræver MFA, selvom administratorens adgangskode bliver kompromitteret, er adgangskoden ubrugelig uden den anden form for identifikation.  <br><br>Når du slår MFA til, næste gang brugeren logger på, skal brugeren angive en alternativ mailadresse og et alternativt telefonnummer til kontogendannelse.  <br> [Konfigurer multifaktorgodkendelse](../security-and-compliance/set-up-multi-factor-authentication.md)          |

Hvis du får en meddelelse i Administration om, at du ikke har tilladelse til at redigere en indstilling eller side, skyldes det, at du er tildelt en rolle, der ikke har denne tilladelse.

## <a name="commonly-used-microsoft-365-admin-center-roles"></a>Ofte anvendte Microsoft 365 Administration roller

I Microsoft 365 Administration du gå til Rolletildelinger <a href="https://go.microsoft.com/fwlink/p/?linkid=2097861" target="_blank">**og derefter**</a> vælge en hvilken som helst rolle for at åbne detaljeruden. Vælg fanen **Tilladelser for** at få vist den detaljerede liste over, hvad administratorer, der er tildelt den pågældende rolle, har tilladelse til at gøre. Vælg fanen **Tildelte** eller **Tildelte administratorer for** at føje brugere til roller.

Du skal sandsynligvis kun tildele følgende roller i organisationen. Som standard viser vi først roller, som de fleste organisationer bruger. Hvis du ikke kan finde en rolle, skal du gå til bunden af listen og vælge **Vis alle efter kategori**. (Du kan finde detaljerede oplysninger, herunder de cmdlet'er, der er knyttet til en rolle, [under Indbyggede roller i Azure AD](/azure/active-directory/roles/permissions-reference)).)

|Administratorrolle     |Who have tildelt denne rolle?  |
|---------|---------|
|Faktureringsadministrator     |   Tildel rollen som faktureringsadministrator til brugere, der foretager køb, administrerer abonnementer og serviceanmodninger og overvåger tjenestestilstanden. <br><br> Faktureringsadministratorer kan også:<br> - Administrer alle aspekter af fakturering <br> - Oprette og administrere supportbilletter i Azure-portalen <br>  |
|Exchange administrator     |   Tildel Exchange administratorrolle til brugere, der skal have vist og administrere dine brugeres mailpostkasser, Microsoft 365 grupper og Exchange Online. <br><br> Exchange administratorer kan også:<br> - Gendan slettede elementer i en brugers postkasse <br> - Konfigurere stedfortrædere for "Send som" og "Send på vegne af" <br>  |
|Global administrator     |   Tildel rollen Som global administrator til brugere, der har brug for global adgang til de fleste administrationsfunktioner og data på tværs af Microsoft-onlinetjenester. <br><br> At give for mange brugere global adgang er en sikkerhedsrisiko, og vi anbefaler, at du har mellem 2 og 4 globale administratorer. <br><br> Kun globale administratorer kan:<br> - Nulstil adgangskoder for alle brugere <br> - Tilføje og administrere domæner <br> - Fjerne blokeringen af en anden global administrator <br> <br> **Bemærk!**   Den person, der tilmeldte sig Microsoft-onlinetjenester, bliver automatisk global administrator. |
|Global læser    |   Tildel den globale læserrolle til brugere, der skal have vist administratorfunktioner og -indstillinger i Administration, som den globale administrator kan få vist. Den globale læseradministrator kan ikke redigere nogen indstillinger.   |
|Gruppeadministrator     |   Tildel gruppeadministratorrollen til brugere, der skal administrere alle gruppeindstillinger på tværs af administrationscentre, herunder Microsoft 365 Administration og Azure Active Directory portal. <br><br> Gruppeadministratorer kan:<br> - Oprette, redigere, slette og gendanne Microsoft 365 grupper <br> - Opret og opdater politikker for oprettelse af grupper, udløb og navngivning <br> - Opret, rediger, slet og gendan Azure Active Directory sikkerhedsgrupper| 
|Helpdesk-administrator     |   Tildel administratorrollen Helpdesk til brugere, der skal gøre følgende:<br> - Nulstil adgangskoder <br> - Tving brugerne til at logge af <br> - Administrer serviceanmodninger <br> - Overvåg tjeneste sundhed <br> <br> **Bemærk**! Helpdesk-administratoren kan kun hjælpe brugere, der ikke er administratorer, og brugere, der er tildelt disse roller: Mappelæser, Gæste inviterer, Helpdesk-administrator, meddelelsescenterlæser og rapportlæser.      |
|Licensadministrator    |   Tildel licensadministratorrollen til brugere, der skal tildele og fjerne licenser fra brugere, og redigere deres brugsplacering. <br/><br/> Licensadministratorer kan også: <br> - Genbehandler licenstildelinger til gruppebaserede licenser <br> - Tildel produktlicenser til grupper for gruppebaserede licenser  |
|Office appadministrator    |   Tildel administratorrollen Office apps til brugere, der skal gøre følgende: <br> - Brug Office til at oprette og administrere skybaserede politikker for Office <br> - Oprette og administrere serviceanmodninger <br> - Administrere indholdet Nyheder, som brugerne kan se i deres Office apps   <br> - Overvåg tjeneste sundhed  |
|Adgangskodeadministrator  |   Tildel administratorrollen Adgangskode til en bruger, der skal nulstille adgangskoder for ikke-administratorer og adgangskodeadministratorer.   |
|Meddelelsescenterlæser |   Tildel læserrollen i Meddelelsescenter til brugere, der skal gøre følgende: <br> - Overvåge meddelelser i meddelelsescenteret <br> - Få en ugentlig mailopdatering af indlæg og opdateringer i meddelelsescenteret <br> - Dele indlæg i meddelelsescenteret <br> - Have skrivebeskyttet adgang til Azure AD-tjenester, f.eks. brugere og grupper|
|Power Platform-administrator |   Tildel administratorrollen Power-platform til brugere, der skal gøre følgende: <br> - Administrere alle administratorfunktioner til Power Apps, Power Automate og forebyggelse af datatab <br> - Oprette og administrere serviceanmodninger <br> - Overvåg tjeneste sundhed  |
|Rapportlæser |   Tildel rollen Rapportlæser til brugere, der skal gøre følgende: <br> - Få vist brugsdata og aktivitetsrapporter i Microsoft 365 Administration <br> - Få adgang til Power BI adoption-indholdspakke <br> - Få adgang til logonrapporter og -aktivitet i Azure AD <br> - Vis data, der returneres af Microsoft Graph API til rapportering|
|Tjenestesupportadministrator   |   Tildel tjenestesupportadministratorrollen som en ekstra rolle til administratorer eller brugere, der skal gøre følgende ud over deres sædvanlige administratorrolle: <br> - Åbne og administrere serviceanmodninger <br> - Få vist og dele indlæg i meddelelsescenteret <br> - Overvåg tjeneste sundhed   |
|SharePoint administrator    |   Tildel SharePoint administratorrolle til brugere, der skal have adgang til og administrere SharePoint Online Administration. <br><br>SharePoint administratorer kan også: <br> - Oprette og slette websteder <br> - Administrere grupper af websteder og globale SharePoint indstillinger   |
|Teams administrator    |   Tildel Teams administratorrolle til brugere, der skal have adgang til og Teams Administration. <br><br>Teams administrator kan også: <br> - Administrer møder <br> - Administrer mødebroer <br> - Administrer alle indstillinger for hele organisationen, herunder indstillinger for sammenslutning, teamopgradering og teams-klientindstillinger   |
|Brugeradministrator     |    Tildel brugeradministratorrollen til brugere, der skal gøre følgende for alle brugere: <br> - Tilføj brugere og grupper <br> - Tildel licenser <br> - Administrere de fleste brugeregenskaber <br> - Oprette og administrere brugervisninger <br> - Opdater udløbspolitikker for adgangskoder <br> - Administrer serviceanmodninger <br> - Overvåg tjeneste sundhed <br><br>  Brugeradministratoren kan også udføre følgende handlinger for brugere, der ikke er administratorer, og for brugere, der er tildelt følgende roller: Mappelæser, Gæsteinvitator, Helpdesk-administrator, meddelelsescenterlæser, rapportlæser: <br> - Administrer brugernavne<br> - Slette og gendanne brugere<br> - Nulstil adgangskoder <br> - Tving brugerne til at logge af <br> - Opdateringsenhedstaster (FIDO)   |

## <a name="delegated-administration-for-microsoft-partners"></a>Delegeret administration for Microsoft-partnere

Hvis du arbejder med en Microsoft-partner, kan du tildele vedkommende administratorroller. De kan så tildele brugere i din virksomhed eller deres virksomhed administratorroller. Du kan f.eks. have dem til at gøre dette, hvis de konfigurerer og administrerer din onlineorganisation for dig.
  
En partner kan tildele disse roller:
  
- **Administratoragent** Rettigheder, der svarer til en global administrator, med undtagelse af administration af multifaktorgodkendelse via Partnercenter.

- **Helpdesk-agent** Rettigheder, der svarer til en helpdesk-administrator.

Før partneren kan tildele disse roller til brugere, skal du tilføje partneren som delegeret administrator til din konto. Denne proces igangsættes af en autoriseret partner. Partneren sender dig en mail for at spørge, om du vil give vedkommende tilladelse til at fungere som delegeret administrator. Du kan finde en vejledning [under Godkend eller fjern partnerrelationer](../misc/add-partner.md).
  
## <a name="related-content"></a>Relateret indhold

[Tildel administratorroller](assign-admin-roles.md) (artikel)\
[Azure AD-roller i Microsoft 365 Administration](azure-ad-roles-in-the-mac.md) (artikel)\
[Aktivitetsrapporter i Microsoft 365 Administration](../activity-reports/activity-reports.md) (artikel)\
[Exchange Online administratorrolle](about-exchange-online-admin-role.md) (artikel)
