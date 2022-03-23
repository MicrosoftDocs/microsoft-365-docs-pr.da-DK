---
title: Microsoft 365 udløbspolitik for gruppen
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
description: Få mere at Microsoft 365 om udløbspolitikker for grupper.
ms.openlocfilehash: 1c0ac1aa7e38fddb85bb9b434c46665cacd1ca69
ms.sourcegitcommit: c2b5ce3150ae998e18a51bad23277cedad1f06c6
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/17/2021
ms.locfileid: "63591339"
---
# <a name="microsoft-365-group-expiration-policy"></a>Microsoft 365 udløbspolitik for gruppen

Med den øgede brug af Microsoft 365 grupper og Microsoft Teams har administratorer og brugere brug for en metode til at rydde op i ubrugte grupper og teams. En Microsoft 365 gruppers udløbspolitik kan hjælpe med at fjerne inaktive grupper fra systemet og gøre tingene renere.

Når en gruppe udløber, slettes alle dens tilknyttede tjenester (postkassen, Planner, SharePoint, team osv.) også.

Når en gruppe udløber, bliver den "blød-slettet", hvilket betyder, at den stadig kan gendannes i op til 30 dage.

Administratorer kan angive en udløbsperiode, og enhver inaktiv gruppe, der når slutningen af den pågældende periode, og som ikke fornys, slettes. (Dette omfatter arkiverede teams). Udløbsperioden starter, når gruppen oprettes, eller på den dato, hvor den sidst blev fornyet. Gruppeejere vil automatisk få tilsendt en mail før udløb, der giver dem mulighed for at forny gruppen til et andet udløbsinterval. Teams brugere får vist faste meddelelser i Teams.

Grupper, der er aktivt i brug, fornyes automatisk. En af følgende handlinger vil automatisk blive fornyt en gruppe:
- SharePoint - få vist, redigere, downloade, flytte, dele eller uploade filer. Visning af en SharePoint side tæller ikke som en handling for automatisk fornyelse.
- Outlook – Deltag i gruppe, læs eller skriv gruppemeddelelse fra gruppen, og synes godt om en meddelelse (Outlook på internettet).
- Teams – besøger en teamskanal.

Bemærk, at den Yammer aktivitet, der udløser en automatisk gruppefornyelse, er overførsel af et dokument til SharePoint inden for communityet.

> [!IMPORTANT]
> Når du ændrer udløbspolitikken, genberegner tjenesten udløbsdatoen for hver gruppe. Den starter altid optællingen fra den dato, hvor gruppen blev oprettet, og anvender derefter den nye udløbspolitik.

Det er vigtigt at vide, at udløb er slået fra som standard. Administratorer skal aktivere det for deres organisation, hvis de vil bruge det.

> [!NOTE]
> Konfiguration og brug af politikken for udløb for Microsoft 365-grupper kræver, at du har, men ikke nødvendigvis tildeler Azure AD Premium-licenser til medlemmer af alle grupper, som politikken for udløb er anvendt på. Få mere at vide under [Introduktion til Azure Active Directory Premium](/azure/active-directory/active-directory-get-started-premium).

## <a name="who-can-configure-and-use-the-microsoft-365-groups-expiration-policy"></a>Who konfigurere og bruge udløbspolitikken for Microsoft 365 gruppe?

|Rolle|Hvad de kan gøre|
|---------|---------|
|Office 365 global administrator (i Azure, virksomhedsadministratoren), brugeradministrator|Opret, læs, opdater eller slet de Microsoft 365 indstillinger for udløbspolitik for grupper.|
|Bruger|Forny eller [gendan](/azure/active-directory/users-groups-roles/groups-restore-deleted) Microsoft 365 gruppe, de ejer|

## <a name="how-to-set-the-expiration-policy"></a>Sådan angives udløbspolitikken

Som nævnt ovenfor er udløbsdatoen som standard slået fra. En administrator skal aktivere udløbspolitikken og angive egenskaberne for, at den skal træder i kraft. For at aktivere den skal du **gå Azure Active Directory** >  **GroupsExpiration** > . Her kan du angive standardgruppens levetid og angive, hvor langt på forhånd du vil have, at den første og anden udløbsmeddelelser skal sendes til gruppeejeren.

Gruppens levetid er angivet i dage og kan indstilles til 180, 365 eller til en brugerdefineret værdi, som du angiver. Den brugerdefinerede værdi skal være mindst 30 dage.

Hvis gruppen ikke har en ejer, går udløbsmailsene til den angivne administrator.

Du kan angive politikken for alle dine grupper, kun udvalgte grupper (op til 500), eller du kan deaktivere den helt ved at vælge **Ingen**. Bemærk, at du i øjeblikket ikke kan have forskellige politikker for forskellige grupper.

![Skærmbillede af indstillinger for udløb af grupper i Azure Active Directory.](../media/azure-groups-expiration-settings.png)

## <a name="how-expiry-works-with-the-retention-policy"></a>Sådan fungerer udløb med opbevaringspolitikken

Hvis du har konfigureret en opbevaringspolitik for grupper i Security and Compliance Center, fungerer udløbspolitikken problemfrit med opbevaringspolitik. Når en gruppe udløber, bevares gruppens postkassesamtaler og filer på gruppewebstedet i opbevaringsbeholderen i det specifikke antal dage, der er defineret i opbevaringspolitikken. Brugerne vil dog ikke kunne se gruppen eller dens indhold efter udløb.

## <a name="how-and-when-a-group-owner-learns-if-their-groups-are-going-to-expire"></a>Hvordan og hvornår en gruppeejer lærer, om deres grupper udløber

Gruppeejere får kun besked via mail. Hvis gruppen blev oprettet via Planner, SharePoint eller en anden app, vil udløbsmeddelelserne altid komme via mail. Hvis gruppen blev oprettet via Teams, modtager gruppeejeren en besked om at forny via aktivitetssektionen. Det anbefales ikke, at du aktiverer udløb for en gruppe, hvis gruppeejeren ikke har en gyldig mailadresse.

30 dage før gruppen udløber, vil gruppeejerne (eller de mailadresser, du har angivet for grupper, der ikke har en ejer) modtage en mail, der giver dem mulighed for nemt at forny gruppen. Hvis de ikke fornyer den, modtager de endnu en mail med fornyelse 15 dage før udløb. Hvis de stadig ikke har fornyet den, modtager de endnu en mailbesked dagen før udløb.

Hvis ingen af ejerne eller administratorerne af en eller anden grund fornyer gruppen, før den udløber, kan administratoren stadig gendanne gruppen i op til 30 dage efter udløb. Du kan få mere [at vide under: Gendan en Microsoft 365 gruppe](https://support.office.com/article/restore-a-deleted-office-365-group-b7c66b59-657a-4e1a-8aa0-8163b1f4eb54).

## <a name="archiving-group-contents"></a>Arkivering af gruppeindhold

Hvis du har en gruppe, du ikke længere vil bruge, men du vil bevare dens indhold, skal du se Arkivér grupper[, teams og Yammer](end-life-cycle-groups-teams-sites-yammer.md) for at få oplysninger om, hvordan du eksporterer oplysninger fra de forskellige gruppetjenester.

## <a name="related-topics"></a>Relaterede emner

[Anbefalinger til planlægning af styring af samarbejde](collaboration-governance-overview.md#collaboration-governance-planning-recommendations)

[Opret din plan for styring af samarbejde](collaboration-governance-first.md)

[Oversigt over opbevaringspolitikker](https://support.office.com/article/5e377752-700d-4870-9b6d-12bfc12d2423)

[Tildel en ny ejer til en uafhængig gruppe](https://support.office.com/article/86bb3db6-8857-45d1-95c8-f6d540e45732)

[Konfigurere Microsoft 365 gruppeudløb](/azure/active-directory/active-directory-groups-lifecycle-azure-portal)
