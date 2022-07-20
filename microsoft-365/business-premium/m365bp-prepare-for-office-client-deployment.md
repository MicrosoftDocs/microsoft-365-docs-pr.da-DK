---
title: Forbered office-klientinstallation med Microsoft 365 Business Premium
f1.keywords:
- CSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: high
ms.date: 07/19/2022
ms.custom:
- MiniMaven
search.appverid:
- BCS160
- MET150
ROBOTS: NO INDEX, NO FOLLOW
description: Få mere at vide om, hvordan du automatisk installerer 32-bit Office-apps på Windows-computere og holder dem opdateret i Microsoft 365 Business Premium.
ms.openlocfilehash: a8bdede91b0b7e5114f38ac8f555d43913ff22dd
ms.sourcegitcommit: c1eaea74c8ffce2f9f477c9469342e88e4a70c14
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/20/2022
ms.locfileid: "66893895"
---
# <a name="prepare-to-automatically-install-office-apps-to-client-computers"></a>Forbered automatisk installation af Office-apps på klientcomputere

Brug Microsoft 365 Business Premium til automatisk at installere 32-bit Office-apps på Windows-computere og holde dem opdateret med opdateringer.
  
Automatisk installation fungerer bedst, hvis computeren: 

- er på Windows for Business.
  
- har ikke eksisterende Office-skrivebordsapps (Word, Excel, PowerPoint, Outlook, OneNote, Publisher, Access og OneDrive) ELLER har en eksisterende version af Klik og kør Office installeret.

Hvis du vil finde ud af, om du har Klik og kør-versionen af Office, skal du gå til **Filkonto** \> (**Office-konto** i Outlook) i en Office-app. Hvis du kan se **Office Opdateringer** som vist i følgende figur, blev installationen udført ved hjælp af Klik og kør.
  
![Skærmbillede af Office-opdateringer i Office-appkonto.](./../media/e3439380-fa43-4ed6-ae5d-64851c297df5.png)
  
## <a name="requirements-for-using-this-feature"></a>Krav til brug af denne funktion
  
Fungerer sammen med:
  
- En bruger, der har en Windows Business-brugerlicens, en aktiv Microsoft 365 for Business-licens, Windows 10 Creators Update og er tilsluttet Azure Active Directory.

Fungerer ikke sammen med: 

- 64-bit Office-apps (f.eks. Word, Excel, PowerPoint). Hvis der kræves 64-bit Office-apps, passer denne funktion ikke, fordi der ikke er nogen understøttelse af, at der udløses en 64-bit 2016 Klik og kør-version af Office fra Administrationskonsollen til Microsoft 365 til virksomheder.

- Alle separate 2016 Windows Installer-apps (MSI) (f.eks. Visio eller Project). Microsoft 365 til virksomheder opgraderer Office til Klik og kør-versionen af Office 2016, og det fungerer ikke sammen med office 2016 MSI-separate programmer.

I følgende tabel kan du se, hvilken handling slutbrugerne eller administratorerne kan få brug for, afhængigt af deres starttilstand, for at få en vellykket Klik og kør-version af Office-installationen fra Administrationskonsollen til Microsoft 365 til virksomheder.<br/>


|Starter office-installationsstatus|Handling, der skal udføres, før Office-installationen af Microsoft 365 til virksomheder|Sluttilstand|
|:-----|:-----|:-----|
|Der er ikke installeret en Office-pakke  |Ingen  |Office 2016 32-bit installeres ved hjælp af Klik og kør  |
|Eksisterende Klik og kør 32-bit version af Office (2016 eller tidligere) og ingen separate apps  |Ingen  |Opgraderet til den nyeste 32-bit Klik og kør-version af Office 2016 efter behov **\*** |
|Eksisterende Klik og kør 32-bit version af Office og Klik og kør 32-bit eller 64-bit separate Office-apps (f.eks. Visio, Project)  |Ingen  |Separate apps påvirkes ikke. Pakken er opgraderet til Klik og kør 32-bit versionen af Office 2016  |
|Eksisterende Klik og kør 32-bit version af Office og eventuelle 32-bit eller 64-bit (undtagen 2016) MSI-separate Office-apps  |Ingen  |Separate apps påvirkes ikke. Pakken er opgraderet til Klik og kør 32-bit versionen af Office 2016  |
|Enhver eksisterende Klik og kør 64-bit version af Office  |Fjern 64-bit Office-appsene, hvis det er OK at erstatte dem med 32-bit Office-apps  |Hvis Office 64-bit-apps fjernes, installeres Klik og kør 32-bit versionen af Office 2016  |
|En eksisterende MSI-installation af Office 2016 med eller uden separate apps  |Fjern MSI Office 2016.  |Klik og kør 32-bit versionen af Office 2016 er installeret. Ingen ændring af separate apps  |
|Eksisterende MSI-installation af Office 2013 (eller tidligere) og/eller separate Office-apps  |Ingen  |Klik og kør 32-bit version af Office 2016 med den eksisterende MSI Office-installation (og separate apps) findes side om side  |

 **(\*) Bemærk!** Opgraderer ikke til Klik og kør 32-bit versionen af Office 2016 på grund af en kendt fejl. Der er en rettelse i gang. 

## <a name="next-objective"></a>Næste mål

[Opret indstillinger for appbeskyttelse](m365bp-protection-settings-for-windows-10-devices.md)
  