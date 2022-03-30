---
title: Hvordan knyttes beskyttelsesfunktioner Microsoft 365 Business Premium indstillinger i Intune
f1.keywords:
- NOCSH
ms.author: sharik
author: skjerland
manager: scotv
ms.date: 02/27/2022
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Adm_O365
- M365-subscription-management
- M365-identity-device-management
- Adm_TOC
ms.custom:
- Adm_O365
- Core_O365Admin_Migration
- MiniMaven
- MSB365
- OKR_SMB_M365
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
ms.assetid: aad21b1a-c775-469a-b89c-c5d1d59d27db
description: Få mere at vide om, hvordan beskyttelsesfunktioner Microsoft 365 Business Premium er kort over til Indstillinger i Intune. Abonnementet giver dig licens til at ændre indstillinger i Intune.
ms.openlocfilehash: 33dfb7b53e048f258c1974ced046deaad41f5ce2
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63598468"
---
# <a name="how-do-protection-features-in-microsoft-365-business-premium-map-to-intune-settings"></a>Hvordan knyttes beskyttelsesfunktioner Microsoft 365 Business Premium indstillinger i Intune

> [!NOTE]
> Microsoft Defender for Business udrulles til Microsoft 365 Business Premium fra 1. marts 2022. Dette tilbud indeholder yderligere sikkerhedsfunktioner til enheder. [Få mere at vide om Defender for Business](../../security/defender-business/mdb-overview.md).

## <a name="android-and-ios-application-protection-settings"></a>Beskyttelsesindstillinger for Android- og iOS-programmer

Følgende tabel viser, hvordan politikindstillinger for Android- og iOS-programmer knyttes til indstillinger i Intune.
  
Du kan finde Intune-indstillingen ved at logge på med Microsoft 365 Business Premium administratorlegitimationsoplysninger og gå til Administration og derefter **intune**.
  
 > [!IMPORTANT]
 > 
 > Et Microsoft 365 Business Premium-abonnement giver dig licens til at ændre alle Intune-indstillingerne. Se [Introduktion til Intune for at komme i gang.](/intune/introduction-intune)
  
Vælg det ønskede Politiknavn, f.eks &mdash; . Programpolitik for Android &mdash; , og vælg derefter **Politikindstillinger**.
  
Under **Beskyt arbejdsfiler, når enheder er gået tabt eller blevet stjålet**
  
|**Politikindstilling for Android- eller iOS-program**|**Intune-indstilling(er)**|
|:-----|:-----|
|Slet arbejdsfiler fra en inaktiv enhed efter  <br/> |Offlineinterval (dage), før appdataene slettes  <br/> |
|Tving brugerne til at gemme arbejdsfiler på OneDrive for Business  <br/> Bemærk, at kun OneDrive for Business er tilladt  <br/> |Vælg, hvilke lagertjenester virksomhedens data kan gemmes i  <br/> |
|||
   
Under **Administrer, hvordan brugeradgang Office filer på mobilenheder**
  
|**Politikindstilling for Android- eller iOS-program**|**Intune-indstilling(er)**|
|:-----|:-----|
|Slet arbejdsfiler fra en inaktiv enhed efter  <br/> |Offlineinterval (dage), før appdataene slettes  <br/> |
|Tving brugerne til at gemme arbejdsfiler på OneDrive for Business  <br/> Bemærk, at kun OneDrive for Business er tilladt  <br/> |Vælg, hvilke lagertjenester virksomhedens data kan gemmes i  <br/> |
|Kryptér arbejdsfiler  <br/> |Kryptér appdata  <br/> |
|Under **Administrer, hvordan brugeradgang Office filer på mobilenheder** <br/> ||
|Kræv en pinkode eller et fingeraftryk for at få adgang Office apps  <br/> | Kræv pinkode for at få adgang  <br/>  Dette indstiller også:  <br/> **Tillad enkel pinkode** til **Ja** <br/> **Pinkodelængde** til 4  <br/> **Tillad fingeraftryk i stedet for pinkode** til **Ja** <br/> **Deaktiver apppinkode, når enhedens pinkode administreres** til **Nej** <br/> |
|Nulstil pinkode, når logon mislykkes dette mange gange (er deaktiveret, hvis pinkode ikke er påkrævet)  <br/> |Antal forsøg før nulstilling af pinkode  <br/> |
|Kræv, at brugerne logger på igen, Office apps har været inaktive i (deaktiveres, hvis pinkode ikke er påkrævet)  <br/> | Kontrollere adgangskravene igen efter (minutter)  <br/>  Dette indstiller også:  <br/> **Timeout** er indstillet til minutter  <br/>  Dette er det samme antal minutter, du angiver i Microsoft 365 Business.  <br/> **Offlineperiode er** indstillet til 720 minutter som standard  <br/> |
|Afvisning af adgang til arbejdsfiler på jailbroken eller rootede enheder  <br/> |Bloker administrerede apps fra at køre på jailbroken eller rootede enheder  <br/> |
|Tillad brugere at kopiere indhold fra Office apps til personlige apps  <br/> | Begræns klip, kopiér og indsæt med andre apps  <br/>  Hvis indstillingen Microsoft 365 Business Premium til **Til, så** er disse tre indstillinger også indstillet til **Alle apps** i Intune:  <br/> **Tillad app at overføre data til andre apps** <br/> **Tillad app at modtage data fra andre apps** <br/> **Begræns klip, kopiér og indsæt med andre apps** <br/>  Hvis indstillingen Microsoft 365 Business er angivet **til Til**, så er alle Intune-indstillingerne angivet til:  <br/> **Tillad app at overføre data til andre apps er** indstillet til **Politik-administrerede apps** <br/> **Tillad, at appen kan modtage data fra andre apps** er indstillet til **Alle apps** <br/> **Begræns klip, kopiér og sæt ind med andre apps** er indstillet **til Politik-administrerede apps med Indsætning** <br/> |
|||
   
## <a name="windows-10-app-protection-settings"></a>Windows 10 indstillinger for appbeskyttelse

Følgende tabel viser, hvordan politikindstillingerne Windows 10 programoversigten i forhold til indstillinger i Intune.
  
Du kan finde Intune-indstillingen ved at logge på med Microsoft 365 Business Premium legitimationsoplysninger og gå til [Azure-portalen](https://portal.azure.com). Vælg **Flere tjenester**, og skriv Intune i **Filter**. Vælg **Intune App Protection** \> **App-politik**.
  
 > [!IMPORTANT]
 >
 >Et Microsoft 365 Business Premium-abonnement giver dig kun licens til at ændre Intune-indstillingerne, der er kort til de indstillinger, der er tilgængelige Microsoft 365 Business Premium. 
  
Hvis du vil udforske de tilgængelige indstillinger, skal du vælge det ønskede politiknavn og derefter vælge Generelt, Tildelinger, Tilladte apps, Fritagne  **apps****, Påkrævede** indstillinger eller Avancerede indstillinger fra venstre **navigationsrude**.  
  
|**Windows 10 programpolitikindstilling**|**Intune-indstilling(er)**|
|:-----|:-----|
|Kryptér arbejdsfiler  <br/> |**Avancerede indstillinger** \> **Databeskyttelse**: **Tilbagekald krypteringsnøgler** , når registrering og Tilbagekald adgang til beskyttede **dataenhedsregistreringer til MDM** begge er indstillet til **Til**.  <br/> |
|Forebyd, at brugere kopierer virksomhedsdata til personlige filer.  <br/> |**Påkrævede indstillinger** \> **Windows i tilstanden Beskyttelse af oplysninger**. **Til** i Microsoft 365 Business Premium til: **Skjul tilsidesættelser**, **Fra** Microsoft 365 Business Premium til: **Fra**.  <br/> |
|Office adgangskontrol for dokumenter  <br/> | Hvis denne er indstillet **til Til** i Microsoft 365 Business Premium, skal du derefter  <br/> **Avancerede indstillinger** \> **Access**, **Brug Windows Hello for Business som en metode til at logge på Windows** er indstillet til **Til** med følgende yderligere indstillinger:  <br/> **Angiv det mindste antal tegn, der kræves til pinkoden er** indstillet til **4**.  <br/> **Konfigurer brugen af store bogstaver i pinkoden til Windows Hello for Business** er indstillet til Tillad ikke brugen af **store bogstaver i pinkode**.  <br/> **Konfigurer brugen af små bogstaver i pinkoden til Windows Hello for Business** er indstillet til Tillad ikke brug af små bogstaver **i pinkode**.  <br/> **Konfigurer brugen af specialtegn i pinkoden til Windows Hello for Business** er indstillet til Tillad ikke **brugen af specialtegn i pinkode**.  <br/> **Angiv den periode (i dage),** en pinkode kan bruges, før systemet kræver, at brugeren ændrer, er indstillet til **0**.  <br/> **Angiv antallet af tidligere pinkoder, der** kan knyttes til en brugerkonto, som ikke kan genbruges, er angivet til **0**.  <br/> **Antal mislykkede godkendelsesfejl, der er tilladt**, før enheden slettes, er indstillet til det samme som i Microsoft 365 Business (5 som standard).  <br/> **Maksimalt tidsrum (i minutter),** der tillades, efter enheden er inaktiv, som medfører, at enheden bliver pinkode- eller adgangskodelåst, er indstillet til det samme som i Microsoft 365 Business.  <br/> |
|Aktivér gendannelse af beskyttede data  <br/> |**Avancerede indstillinger** \> **Databeskyttelse**: Vis **ikonet for beskyttelse af virksomhedsdata,** og **Brug Azure RMS til WIP** er indstillet til **Til**.  <br/> |
|Beskyt yderligere skybaserede virksomhedsplaceringer  <br/> |**Avancerede indstillinger** \> **Beskyttede domæner og** **skyressourcer** viser domæner og SharePoint websteder.  <br/> |
|Filer, der bruges af disse apps, er beskyttet  <br/> |Listen over beskyttede apps er angivet i **Tilladte apps**.  <br/> |
|||
   
## <a name="windows-10-device-protection-settings"></a>Windows 10 indstillinger for enhedsbeskyttelse

Følgende tabel viser, hvordan konfigurationsindstillingerne Windows 10 af enheder er knyttet til indstillinger i Intune.
  
For at finde Intune-indstillingen skal du logge på med dine Microsoft 365 Business Premium-administratorlegitimationsoplysninger og gå til [Azure-portalen](https://portal.azure.com), derefter vælge Flere **tjenester og skrive** Intune i **Filter**, vælge **Intune** \> **Enhedskonfigurationsprofiler** \> **.** Vælg derefter **Enhedspolitik for Windows 10** \> **Egenskaber** \> **Indstillinger**.
  
|**Windows 10 for enhedspolitik**|**Intune-indstilling(er)**|
|:-----|:-----|
|Beskyt pc'er mod virus og andre trusler ved hjælp af Windows Defender Antivirus  <br/> |Tillad overvågning i realtid = TIL  <br/> Tillad skybeskyttelse = TIL  <br/> Bed brugere om indsendelse af eksempler = Send Pengeskab eksempler automatisk (send som standard ikke automatisk til brug af pinkoder)  <br/> |
|Beskyt pc'er mod webbaserede trusler i Microsoft Edge  <br/> |**SmartScreen i** **Edge-browserindstillinger er** indstillet til **Påkrævet**.  <br/> |
|Slå enhedsskærmen fra, når den har været inaktiv i (minutter)  <br/> |Maksimale minutters inaktivitet indtil skærmen låses (minutter)  <br/> |
|Tillad brugere at downloade apps fra Microsoft Store  <br/> |Brugerdefineret URI-politik  <br/> |
|Give brugere adgang til Cortana  <br/> |**Generelt** \> **Cortana er** indstillet til **bloker** i Intune, når slået **fra** i Microsoft 365 Business Premium.  <br/> |
|Tillad brugere at modtage Windows tip og reklamer fra Microsoft  <br/> |**Windows spotlight,** blokeres alle, hvis denne er slået **fra** i Microsoft 365 Business Premium.  <br/> |
|Hold Windows 10-enheder opdateret automatisk  <br/> | Denne indstilling er i **Microsoft Intune** \> **tjenesteopdateringer – Windows 10 Opdateringsringene**, vælg Opdater politik **for Windows 10-enheder** og **derefter Egenskaber** \> **Indstillinger**.  <br/>  Når indstillingen Microsoft 365 Business Premium er indstillet **til Til**, angives alle følgende indstillinger:  <br/> **Tjenestegren** er indstillet **til CB** (CBB, når dette er slået fra i Microsoft 365 Business Premium).  <br/> **Microsoft-produktopdateringer** er indstillet til **Tillad**.  <br/> **Windows er indstillet** til **Tillad**.  <br/> **Funktionsmåden for automatisk** opdatering er indstillet **til Installer automatisk på vedligeholdelsestid** med:  <br/> **Start efter arbejdstid** er indstillet til **06:00**.  <br/> **Aktive timer slutter** kl. **10**.  <br/> **Kvalitetsopdaterings udskydelsesperiode (dage)** er indstillet til **0**.  <br/> **Funktionsopdaterings udskydelsesperiode (dage)** er indstillet til **0**.  <br/> **Leveringsoptimerings downloadtilstand** er indstillet **til HTTP blandet med peering bag samme NAT**.  <br/> |
|||

## <a name="see-also"></a>Se også

[De 10 mest populære måder at sikre Microsoft 365 planer til virksomheder på](../security-and-compliance/secure-your-business-data.md)