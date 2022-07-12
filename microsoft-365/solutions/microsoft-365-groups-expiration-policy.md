---
title: Udløbspolitik for Microsoft 365-gruppe
ms.reviewer: arvaradh
f1.keywords: NOCSH
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- m365solution-collabgovernance
search.appverid:
- MET150
recommendations: false
description: Få mere at vide om udløbspolitikker for Microsoft 365-grupper.
ms.openlocfilehash: 41a179dc714063a66ba34aeb676321badfc5f947
ms.sourcegitcommit: 8101c12df67cfd9c15507b0133c23ce4cca1c6ba
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/12/2022
ms.locfileid: "66720451"
---
# <a name="microsoft-365-group-expiration-policy"></a>Udløbspolitik for Microsoft 365-gruppe

Med stigningen i brugen af Microsoft 365-grupper og Microsoft Teams har administratorer og brugere brug for en måde at rydde op i ubenyttede grupper og teams på. En udløbspolitik for Microsoft 365-grupper kan hjælpe med at fjerne inaktive grupper fra systemet og gøre tingene renere.

Når en gruppe udløber, slettes alle dens tilknyttede tjenester (postkassen, Planner, SharePoint-webstedet, teamet osv.) også.

Når en gruppe udløber, er den "blød slettet", hvilket betyder, at den stadig kan gendannes i op til 30 dage.

Administratorer kan angive en udløbsperiode, og alle inaktive grupper, der når slutningen af den pågældende periode, og som ikke fornys, slettes. (Dette omfatter arkiverede teams). Udløbsperioden begynder, når gruppen oprettes, eller den dato, hvor den senest blev fornyet. Gruppeejere får automatisk tilsendt en mail før udløbet, der giver dem mulighed for at forny gruppen med et andet udløbsinterval. Teams-brugere får vist vedvarende meddelelser i Teams.

Grupper, der aktivt bruges, fornys automatisk. En af følgende handlinger vil automatisk forny en gruppe:
- SharePoint – Få vist, rediger, download, flyt, del eller upload filer. (Visning af en SharePoint-side tæller ikke som en handling til automatisk fornyelse).
- Outlook – Deltag i eller rediger gruppe, læs eller skriv gruppemeddelelse fra gruppen, og synes godt om en meddelelse (Outlook på internettet).
- Teams – Besøg en teams-kanal.
- Yammer – få vist et indlæg i et Yammer-community eller en interaktiv mail i Outlook.
- Formularer – få vist, opret eller rediger formularer, eller send et svar til en formular. 

> [!IMPORTANT]
> Når du ændrer udløbspolitikken, genberegner tjenesten udløbsdatoen for hver gruppe. Den starter altid med at tælle fra den dato, hvor gruppen blev oprettet, og anvender derefter den nye udløbspolitik.

Det er vigtigt at vide, at udløb er slået fra som standard. Administratorer skal aktivere den for deres organisation, hvis de vil bruge den.

> [!NOTE]
> Konfiguration og brug af udløbspolitikken for Microsoft 365-grupper kræver, at du har, men ikke nødvendigvis tildele Azure AD Premium-licenser til medlemmerne af alle grupper, som udløbspolitikken anvendes på. [Du kan finde flere oplysninger under Introduktion til Azure Active Directory Premium](/azure/active-directory/active-directory-get-started-premium).

## <a name="who-can-configure-and-use-the-microsoft-365-groups-expiration-policy"></a>Hvem kan konfigurere og bruge udløbspolitikken for Microsoft 365-grupper?

|Rolle|Hvad de kan gøre|
|---------|---------|
|Office 365 global administrator (i Azure, firmaadministratoren), brugeradministrator|Opret, læs, opdater eller slet indstillingerne for udløbspolitik for Microsoft 365-grupper.|
|Bruger|Forny eller [gendan](/azure/active-directory/users-groups-roles/groups-restore-deleted) en Microsoft 365-gruppe, som de ejer|

## <a name="how-to-set-the-expiration-policy"></a>Sådan angiver du udløbspolitikken

Som nævnt ovenfor er udløb slået fra som standard. En administrator skal aktivere udløbspolitikken og angive egenskaberne for, at den træder i kraft. Du aktiverer den ved at gå til **udløb** af **Azure Active Directory-grupper** >  > . Her kan du angive standardgruppens levetid og angive, hvor lang tid i forvejen du vil have, at den første og anden udløbsbesked skal gå til gruppeejeren.

Gruppens levetid er angivet i dage og kan indstilles til 180, 365 eller til en brugerdefineret værdi, som du angiver. Den brugerdefinerede værdi skal være på mindst 30 dage.

Hvis gruppen ikke har en ejer, sendes udløbsmailene til den angivne administrator.

Du kan angive politikken for alle dine grupper, kun udvalgte grupper (op til 500) eller slå den helt fra ved at vælge **Ingen**. Bemærk, at du i øjeblikket ikke kan have forskellige politikker for forskellige grupper.

![Skærmbillede af udløbsindstillinger for grupper i Azure Active Directory.](../media/azure-groups-expiration-settings.png)

## <a name="how-expiry-works-with-the-retention-policy"></a>Sådan fungerer udløb sammen med opbevaringspolitikken

Hvis du har konfigureret en opbevaringspolitik for grupper i Microsoft Purview-compliance-portal, fungerer udløbspolitikken uden problemer sammen med opbevaringspolitikken. Når en gruppe udløber, bevares gruppens postkassesamtaler og -filer på gruppewebstedet i opbevaringsobjektbeholderen i det specifikke antal dage, der er defineret i opbevaringspolitikken. Brugerne får dog ikke vist gruppen eller dens indhold efter udløb.

## <a name="how-and-when-a-group-owner-learns-if-their-groups-are-going-to-expire"></a>Hvordan og hvornår en gruppeejer får at vide, om deres grupper udløber

Hvis gruppen blev oprettet via Planner, SharePoint eller en anden app, sendes udløbsmeddelelserne altid via mail.
Hvis gruppen blev oprettet via Teams, modtager gruppeejeren en mail og en meddelelse, der skal fornys via aktivitetsafsnittet. Det anbefales ikke, at du aktiverer udløb for en gruppe, hvis din gruppeejer ikke har en gyldig mailadresse.

30 dage, før gruppen udløber, modtager gruppeejerne (eller de mailadresser, du har angivet for grupper, der ikke har en ejer) en mail, så de nemt kan forny gruppen. Hvis de ikke fornyer den, modtager de en anden fornyelsesmail 15 dage før udløbet. Hvis de stadig ikke har fornyet den, modtager de en mail mere dagen før udløbet.

Hvis ingen af ejerne eller administratorerne af en eller anden grund fornyer gruppen, før den udløber, kan administratoren stadig gendanne gruppen i op til 30 dage efter udløb. Du kan finde flere oplysninger under: [Gendan en slettet Microsoft 365-gruppe](https://support.office.com/article/restore-a-deleted-office-365-group-b7c66b59-657a-4e1a-8aa0-8163b1f4eb54).

## <a name="archiving-group-contents"></a>Arkivering af gruppeindhold

Hvis du har en gruppe, som du ikke længere har planer om at bruge, men du vil bevare dens indhold, skal du se [Arkivgrupper, teams og Yammer](end-life-cycle-groups-teams-sites-yammer.md) for at få oplysninger om, hvordan du eksporterer oplysninger fra de forskellige gruppetjenester.

## <a name="related-topics"></a>Relaterede emner

[Anbefalinger til planlægning af styring af samarbejde](collaboration-governance-overview.md#collaboration-governance-planning-recommendations)

[Opret din plan for styring af samarbejde](collaboration-governance-first.md)

[Oversigt over opbevaringspolitikker](https://support.office.com/article/5e377752-700d-4870-9b6d-12bfc12d2423)

[Tildel en ny ejer til en mistet gruppe](https://support.office.com/article/86bb3db6-8857-45d1-95c8-f6d540e45732)

[Konfigurer udløb af Microsoft 365-grupper](/azure/active-directory/active-directory-groups-lifecycle-azure-portal)
