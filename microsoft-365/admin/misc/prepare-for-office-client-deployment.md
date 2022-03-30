---
title: Forbered Office klientinstallation med Microsoft 365 til virksomheder
f1.keywords:
- CSH
ms.author: efrene
author: efrene
manager: scotv
ms.date: 02/25/2022
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection: M365-subscription-management
ms.custom:
- Core_O365Admin_Migration
- MiniMaven
- MSB365
- OKR_SMB_M365
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
ROBOTS: NO INDEX, NO FOLLOW
ms.assetid: ed34fff3-2881-4ed4-9906-1ba6bb8dd804
description: Få mere at vide om, hvordan du automatisk installerer 32-bit Office-apps på Windows 10 og holder dem opdateret.
ms.openlocfilehash: aa14aa9407f7115e31f01a8e20ea1324a23452ec
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63598470"
---
# <a name="prepare-for-office-client-deployment-by-microsoft-365-for-business"></a>Forbered Office klientinstallation med Microsoft 365 til virksomheder

Denne artikel gælder for Microsoft 365 Business Premium.

> [!NOTE]
> Microsoft Defender for Business udrulles til Microsoft 365 Business Premium fra 1. marts 2022. Dette tilbud indeholder yderligere sikkerhedsfunktioner til enheder. [Få mere at vide om Defender for Business](../../security/defender-business/mdb-overview.md).

## <a name="prepare-to-automatically-install-office-apps-to-client-computers"></a>Forberede automatisk installation af Office på klientcomputere

Du kan bruge Microsoft 365 Business Premium til automatisk at installere 32-bit Office-apps på Windows 10-computere og holde dem opdateret med opdateringer.
  
Automatisk installation fungerer bedst, hvis slutbrugerens computer er tændt Windows 10 Business og:
  
- ikke har eksisterende Office-skrivebordsprogrammer (Word, Excel, PowerPoint, Outlook, OneNote, Publisher, Access og OneDrive).
    
    eller
    
- Har en eksisterende version af Klik og kør-Office installeret.
    
For at finde ud af om du har Klik og kør-versionen af Office, skal du i enhver Office-app gå  \> til Filkonto **(****Office Konto** i Outlook). Hvis du ser **Office Opdateringer** som vist i følgende figur, blev installationen udført ved hjælp af Klik og kør. 
  
![Skærmbillede af Office opdateringer i Office-app Account.](../../media/e3439380-fa43-4ed6-ae5d-64851c297df5.png)
  
 **Who fordel ved at have denne funktion**
  
Den slutbruger, hvis pc:
  
- **Har** en Windows 10 Business, en aktiv Microsoft 365 til virksomheder-licens, -Windows 10 Creators Update og er forbundet Azure Active Directory. 
    
- **ikke har** 64-bit Office (eksempel: Word, Excel, PowerPoint). Hvis der kræves 64-bit Office-apps, er denne funktion ikke god nok, fordi den ikke understøtter udløsning af en Klik og kør-version af Office til 64-bit 2016 fra administrationskonsollen til Microsoft 365 til virksomheder. 
    
- **Ikke har nogen** enkeltstående 2016 Windows installationsprogram (MSI) (f.eks. Visio eller Project). Microsoft 365 til virksomhedsopgradering Office til Klik og kør-versionen af Office 2016, og det fungerer ikke sammen med Office 2016 MSI-enkeltstående apps. 
    
Følgende tabel viser, hvilken handling slutbrugere/administratorer muligvis skal tage, afhængigt af deres starttilstand, for at få en vellykket 32-bit Klik og kør-version af Office-installation fra administrationskonsollen til Microsoft 365 til virksomheder.<br/>


|Start Office installationsstatus|Handling, der skal Microsoft 365 installationen af Office for Business|Sluttilstand|
|:-----|:-----|:-----|
|Ingen Office installeret  <br/> |Ingen  <br/> |Office 32-bit 2016 installeres ved hjælp af Klik og kør  <br/> |
|Eksisterende Klik og kør 32-bit-version af Office (2016 eller tidligere) og ingen enkeltstående apps  <br/> |Ingen  <br/> |Opgraderet til den nyeste Klik og kør-version af 32-bit Office 2016 efter behov **\*** <br/> |
|Eksisterende Klik og kør 32-bit-version af Office og Klik og kør 32-bit eller 64-bit enkeltstående Office-apps (f.eks. Visio, Project)  <br/> |Ingen  <br/> |Enkeltstående apps påvirkes ikke. Pakken opgraderes til Klik og kør 32-bit-versionen Office 2016  <br/> |
|Eksisterende Klik og kør 32-bit-version af Office og eventuelle 32-bit eller 64-bit (undtagen 2016) MSI-enkeltstående Office apps  <br/> |Ingen  <br/> |Enkeltstående apps påvirkes ikke. Pakken opgraderes til Klik og kør 32-bit-versionen Office 2016  <br/> |
|En eksisterende Klik og kør 64-bit-version af Office  <br/> |Fjern 64-bit Office apps, hvis det er OK at erstatte dem med 32-bit Office apps  <br/> |Hvis Office 64-bit apps fjernes, installeres Klik og kør 32-bit-versionen Office 2016  <br/> |
|En eksisterende MSI-installation af Office 2016 med eller uden enkeltstående apps  <br/> |Fjern MSI Office 2016.  <br/> |Klik og kør 32-bit-versionen af Office 2016 er installeret. Ingen ændring af enkeltstående apps  <br/> |
|Eksisterende MSI-installation af Office 2013 (eller tidligere) og/eller enkeltstående Office apps  <br/> |Ingen  <br/> |Klik og kør 32-bit-versionen af Office 2016 med den eksisterende MSI Office-installation (og enkeltstående apps) side om side  <br/> |
||||
   
 **(\*) Bemærk!** Opgraderer ikke til Klik og kør 32-bit-versionen af Office 2016 på grund af en kendt fejl. En rettelse er i gang. 
  