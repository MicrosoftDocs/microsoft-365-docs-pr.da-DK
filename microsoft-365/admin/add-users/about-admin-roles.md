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
description: Få mere at vide om administratorroller, f.eks. tjenesteadministratorrollen, som knyttes til bestemte forretningsfunktioner og giver tilladelser til at udføre bestemte opgaver i Administration.
ms.openlocfilehash: cd40eb3421abf21205aac909fa2cb1796d7f0aa2
ms.sourcegitcommit: e9692a40dfe1f8c2047699ae3301c114a01b0d3a
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 07/01/2022
ms.locfileid: "66601966"
---
# <a name="about-admin-roles-in-the-microsoft-365-admin-center"></a>Om administratorroller i Microsoft 365 Administration

Se [Microsoft 365 small business-hjælp](https://go.microsoft.com/fwlink/?linkid=2197659) på YouTube.

Microsoft 365- eller Office 365-abonnementet fås med et sæt administratorroller, som du kan tildele til brugere i organisationen ved hjælp af <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 Administration</a>. De enkelte administratorroller relaterer til almindelige forretningsfunktioner og giver personer tilladelse til at udføre bestemte opgaver i Administrationerne.

Med <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 Administration</a> kan du administrere Azure AD-roller og Microsoft Intune-roller. Disse roller er dog et undersæt af de roller, der er tilgængelige i Azure AD-portalen og Intune Administration.

> [!TIP]
> Hvis du har brug for hjælp til trinnene i dette emne, kan du overveje at [arbejde med en Microsoft Small Business-specialist](https://go.microsoft.com/fwlink/?linkid=2186871). Med Business Assist har du og dine medarbejdere adgang til specialister i små virksomheder døgnet rundt, efterhånden som du får din virksomhed til at vokse, lige fra onboarding til hverdagsbrug.

## <a name="watch-what-is-an-admin"></a>Se: Hvad er en administrator?

Se denne og andre videoer på vores [YouTube-kanal](https://go.microsoft.com/fwlink/?linkid=2198028).

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE1SRc0]

1. Vælg Appstarteren, mens du er logget på Microsoft 365. Hvis du kan se administratorknappen, er du administrator.
1. Vælg **Administrator** for at gå til Microsoft 365 Administration.
1. I venstre navigationsrude skal du vælge **Brugere** > <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">**Aktive brugere**</a>.
1. Vælg den person, du vil gøre til administrator. Brugerens oplysninger vises i højre dialogboks.

## <a name="before-you-begin"></a>Før du begynder

Leder du efter den komplette liste over detaljerede beskrivelser af Azure AD-roller, som du kan administrere i <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 Administration</a>? Se nærmere på administratorrolletilladelser i Azure Active Directory. [Indbyggede Azure AD-roller](/azure/active-directory/roles/permissions-reference).

Leder du efter den komplette liste over detaljerede beskrivelser af Intune-roller, som du kan administrere i <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 Administration</a>?  Se nærmere på [rollebaseret adgangskontrol med Microsoft Intune](/mem/intune/fundamentals/role-based-access-control).

Du kan få mere at vide om tildeling af roller i <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 Administration</a> under [Tildel administratorroller](assign-admin-roles.md).

## <a name="security-guidelines-for-assigning-roles"></a>Sikkerhedsretningslinjer for tildeling af roller

Da administratorer har adgang til følsomme data og filer, anbefaler vi, at du følger disse retningslinjer for at holde din organisations data mere sikre.

| Anbefaling                  | Hvorfor er dette vigtigt?                 |
| :------------------- | :------------------- |
| Du bør have 2 til 4 globale administratorer  | Da det kun er en anden global administrator, der kan nulstille en global administrators adgangskode, anbefaler vi, at du har mindst 2 globale administratorer i din organisation i tilfælde af kontospærring. Men den globale administrator har næsten ubegrænset adgang til din organisations indstillinger og de fleste af dataene, så vi anbefaler også, at du ikke har mere end 4 globale administratorer, fordi det kan udgøre en sikkerhedsrisiko. |
| Tildel rollen *mindst tilladende*    | Tildeling af den *mindst tilladende* rolle betyder, at administratorer kun får den adgang, de skal bruge for at få arbejdet udført. Hvis du f.eks. vil have nogen til at nulstille medarbejderadgangskoder, bør du ikke tildele den ubegrænsede globale administratorrolle, du bør tildele en begrænset administratorrolle, f.eks. adgangskodeadministrator eller helpdeskadministrator.  Dette hjælper med at beskytte dine data.                 |
| Kræv multifaktorgodkendelse for administratorer                  |    Det er faktisk en god ide at kræve multifaktorgodkendelse for alle dine brugere, men administratorer bør være påkrævet at skulle bruge multifaktorgodkendelse til at logge på. Multifaktorgodkendelse får brugerne til at angive en anden identifikationsmetode for at bekræfte, at de er den, de udgiver sig for. Administratorer kan få adgang til meget kunde- og medarbejderdata, og hvis du kræver multifaktorgodkendelse, selvom administratorens adgangskode bliver kompromitteret, er adgangskoden ubrugelig uden den anden form for identifikation.  <br><br>Når du slår multifaktorgodkendelse til, skal brugeren angive en alternativ mailadresse og et alternativt telefonnummer til genoprettelse af kontoen, næste gang brugeren logger på.  <br> [Konfigurer multifaktorgodkendelse](../security-and-compliance/set-up-multi-factor-authentication.md)          |

Hvis du får en meddelelse i Administration, der fortæller dig, at du ikke har tilladelse til at redigere en indstilling eller side, skyldes det, at du er tildelt en rolle, der ikke har denne tilladelse.

## <a name="commonly-used-microsoft-365-admin-center-roles"></a>Ofte anvendte Microsoft 365 Administration roller

I Microsoft 365 Administration kan du gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2097861" target="_blank">**Rolletildelinger**</a>og vælg derefter en hvilken som helst rolle for at åbne dens oplysningsrude. Vælg fanen **Tilladelser** for at få vist en detaljeret liste over, hvad administratorer, der er tildelt rollen, har tilladelser til at gøre. Vælg fanen **Tildelte** eller **Tildelte administratorer** for at føje brugere til roller.

Du skal sandsynligvis kun tildele følgende roller i din organisation. Som standard viser vi først roller, som de fleste organisationer bruger. Hvis du ikke kan finde en rolle, skal du gå til bunden af listen og vælge **Vis alle efter kategori**. (Du kan finde detaljerede oplysninger, herunder de cmdlet'er, der er knyttet til en rolle, i [Indbyggede Azure AD-roller](/azure/active-directory/roles/permissions-reference).)

|Administratorrolle     |Hvem skal have tildelt denne rolle?  |
|---------|---------|
|Faktureringsadministrator     |   Tildel rollen Faktureringsadministrator til brugere, der foretager køb, administrerer abonnementer og serviceanmodninger og overvåger tjenestetilstanden. <br><br> Faktureringsadministratorer kan også:<br> – Administrere alle aspekter af fakturering <br> – Oprette og administrere supportanmodninger på Azure-portalen <br>  |
|Exchange-administrator     |   Tildel Exchange-administratorrollen til brugere, der har brug for at få vist og administrere din brugers postkasser, Microsoft 365 grupper og Exchange Online. <br><br> Exchange-administratorer kan også:<br> – Gendanne slettede elementer i en brugers postkasse  <br> – Konfigurere "Send som"- og "Send på vegne af"-stedfortrædere <br>  |
|Global administrator     |   Tildel rollen Global administrator til brugere, der har brug for global adgang til de fleste administrationsfunktioner og data på tværs af Microsofts onlinetjenester. <br><br> Det kan udgøre en sikkerhedsrisiko at give for mange brugere global adgang, og vi anbefaler, at du har mellem 2 og 4 globale administratorer. <br><br> Det er udelukkende globale administratorer, der kan:<br> – Nulstille alle brugeres adgangskoder <br> – Tilføje og administrere domæner <br> – Fjerne blokeringen af en anden global administrator <br> <br> **Bemærk!**   Den person, der tilmeldte sig Microsoft onlinetjenester, bliver automatisk global administrator. |
|Global læser    |   Tildel rollen global læser til brugere, der har brug for at få vist administratorfunktioner og -indstillinger i Administration, som den globale administrator kan få vist. Den globale læseradministrator kan ikke redigere nogen indstillinger.   |
|Gruppeadministrator     |   Tildel rollen Gruppeadministrator til brugere, der skal administrere alle gruppeindstillinger på tværs af administrationer, herunder Microsoft 365 Administration og Azure Active Directory-portalen. <br><br> Gruppeadministratorer kan:<br> – Oprette, redigere, slette og gendanne Microsoft 365-grupper <br> – Oprette og opdatere politikker for oprettelse, udløb og navngivning af grupper <br> – Oprette, redigere, slette og gendanne Azure Active Directory-sikkerhedsgrupper| 
|Helpdesk-administrator     |   Tildel rollen Helpdesk-administrator til brugere, der har brug for at kunne udføre følgende:<br> – Nulstille adgangskoder <br> – Gennemtvinge, at brugerne logger af <br> – Administrere tjenesteanmodninger <br> – Overvåge tjenestetilstand <br> <br> **Bemærk!** Helpdesk-administratoren kan kun hjælpe brugere, der ikke er administratorer, og brugere, der har fået tildelt disse roller: Mappelæser, Gæsteinviterer, Helpdesk-administrator, Meddelelsescenter-læser og Rapportlæser.      |
|Licensadministrator    |   Tildel rollen Licensadministrator til brugere, der skal tildele og fjerne licenser fra brugere, og redigere deres brugsplacering. <br/><br/> Licensadministratorer kan også: <br> – Foretage genbehandling af licens tildelinger for gruppebaseret licensering <br> – Tildele produktlicenser til grupper for gruppebaseret licensering  |
|Administrator af Office-apps    |   Tildel rollen som Administrator af Office-apps til brugere, der har brug for at kunne udføre følgende: <br> – Bruge Office-skypolitiktjenesten til at oprette og administrere skybaserede politikker til Office <br> – Oprette og administrere serviceanmodninger <br> – Administrere indholdet af Nyheder, som brugerne får vist i deres Office-apps   <br> – Overvåge tjenestetilstand  |
|Adgangskodeadministrator  |   Tildel rollen Adgangskodeadministrator til en bruger, der skal kunne nulstille adgangskoder for ikke-administratorer og adgangskodeadministratorer.   |
|Meddelelsescenter-læser |   Tildel rollen som Meddelelsescenter-læser til brugere, der har brug for at kunne udføre følgende: <br> – Overvåge meddelelser i meddelelsescenteret <br> – Få ugentlige mailoversigter over indlæg og opdateringer i meddelelsescenteret <br> – Dele indlæg i meddelelsescenter <br> – Have skrivebeskyttet adgang til Azure AD-tjenester, f.eks. brugere og grupper|
|Administrator af Power Platform |   Tildel rollen som Administrator af Power Platform til brugere, der har brug for at kunne udføre følgende: <br> – Administrer alle administratorfunktioner til Power Apps, Power Automate og Microsoft Purview-forebyggelse af datatab <br> – Oprette og administrere serviceanmodninger <br> – Overvåge tjenestetilstand  |
|Rapportlæser |   Tildel rollen som Rapportlæser til brugere, der har brug for at kunne udføre følgende: <br> – Få vist brugsdata og aktivitetsrapporter i Microsoft 365 Administration <br> – Få adgang til indholdspakken til ibrugtagning af Power BI <br> – Få adgang til logonrapporter og -aktivitet i Azure AD <br> – Få vist data, der returneres af Microsoft Graph-rapporterings API|
|Administrator af tjenestesupport   |   Tildel rollen Administrator af tjenestesupport som en ekstra rolle til administratorer eller brugere, der har brug for at kunne udføre følgende ud over deres sædvanlige administratorrolle: <br> – Åbne og administrere serviceanmodninger <br> – Få vist og dele indlæg i meddelelsescenter <br> – Overvåge tjenestetilstand   |
|SharePoint-administrator    |   Tildel rollen SharePoint-administrator til brugere, der skal have adgang til og administrere SharePoint Online Administration. <br><br>SharePoint-administratorer kan også: <br> – Oprette og slette websteder <br> – Administrere grupper af websteder og globale SharePoint-indstillinger   |
|Administrator af Teams    |   Tildel rollen Administrator af Teams til brugere, der har brug for at få adgang til og administrere Teams Administration. <br><br>Administrator af Teams kan også: <br> – Administrere møder <br> – Administrere mødebroer <br> – Administrere alle indstillinger for hele organisationen, herunder sammenslutning, teams-opgradering og teams-klientindstillinger   |
|Brugeradministrator     |    Tildel rollen Brugeradministrator til brugere, der har brug for at kunne udføre følgende: <br> – Tilføje brugere og grupper <br> – Tildele licenser <br> – Administrere de fleste brugeres egenskaber <br> – Oprette og administrere brugervisninger <br> – Opdatere politikker for udløb af adgangskode <br> – Administrere tjenesteanmodninger <br> – Overvåge tjenestetilstand <br><br>  Brugeradministratoren kan også udføre følgende handlinger for brugere, der ikke er administratorer, og for brugere, der er tildelt følgende roller: Mappelæser, Gæsteinviterer, Helpdesk-administrator, Meddelelsescenter-læser og Rapportlæser: <br> – Administrere brugernavne<br> – Slette og gendanne brugere<br> – Nulstille adgangskoder <br> – Gennemtvinge, at brugerne logger af <br> – Opdatere (FIDO) enhedsnøgler   |

## <a name="delegated-administration-for-microsoft-partners"></a>Stedfortræderadministration til Microsoft-partnere

Hvis du arbejder med en Microsoft-partner, kan du tildele vedkommende administratorroller. Så kan vedkommende tildele brugere i din virksomhed eller sin egen virksomhed administratorroller. Det kan du eksempelvis gøre brug af, hvis de konfigurerer og administrerer din online-organisation for dig.
  
En partner kan tildele disse roller: 
  
- Rettigheder som **Administrator-agent**, der svarer til en global administrator, med undtagelse af administration af multifaktorgodkendelse via Partnercenter.

- Rettigheder som **Helpdesk-agent**, der svarer til en helpdesk-administrator.

Før partneren kan tildele disse roller til brugere, skal du føje partneren til din konto, som delegeret administrator. Denne proces startes af en autoriseret partner. Partneren sender dig en mail for at spørge dig, om du vil give vedkommende tilladelse til at fungere som delegeret administrator. Du kan finde en vejledning under [Godkend eller fjern partnerrelationer](../misc/add-partner.md).
  
## <a name="related-content"></a>Relateret indhold

[Tildel administratorroller](assign-admin-roles.md) (artikel)\
[Azure AD-roller i Microsoft 365 Administration](azure-ad-roles-in-the-mac.md) (artikel)\
[Aktivitetsrapporter i Microsoft 365 Administration](../activity-reports/activity-reports.md) (artikel)\
[Exchange Online-administratorrolle](about-exchange-online-admin-role.md) (artikel)
