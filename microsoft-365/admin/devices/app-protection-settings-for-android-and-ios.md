---
title: Angiv indstillinger for appbeskyttelse til Android- eller iOS-enheder
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
ms.assetid: 6f2b80b4-81c3-4714-a7bc-ae69313e8a33
description: Få mere at vide om, hvordan du opretter, redigerer eller sletter en politik for appadministration og beskytter arbejdsfiler på Android- eller iOS-enheder.
ms.openlocfilehash: 6849b24f691f7b567cc55dce2dda21f2a7e93f22
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63594596"
---
# <a name="set-app-protection-settings-for-android-or-ios-devices"></a>Angiv indstillinger for appbeskyttelse til Android- eller iOS-enheder

Denne artikel gælder for Microsoft 365 Business Premium.

> [!NOTE]
> Microsoft Defender for Business udrulles til Microsoft 365 Business Premium fra 1. marts 2022. Dette tilbud indeholder yderligere sikkerhedsfunktioner til enheder. [Få mere at vide om Defender for Business](../../security/defender-business/mdb-overview.md).

## <a name="watch-secure-office-apps-on-ios"></a>Se: Gør Office-apps sikre på iOS

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE1FLvZ?autoplay=false]

Du kan konfigurere en brugeradgangspolitik, der kræver, at mobilbrugere indtaster en pinkode eller et fingeraftryk for at logge på samt krypterer arbejdsfiler, der er gemt på deres enheder.

1. Log på <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 Administration</a>.
1. Vælg **Tilføj** politik **under Politikker**.
1. Skriv et **navn** under Politiknavn i **ruden Tilføj politik**, og vælg den ønskede politiktype under **Politiktype**.
1. Slå Administrer **, hvordan brugere får adgang Office filer på mobilenheder**, og kontrollér derefter, at følgende tre indstillinger er slået til:
    - **Kræv en pinkode eller et fingeraftryk for at få adgang Office apps**
    - **Beskyt arbejdsfiler, når enheder er gået tabt eller bliver stjålet**
    - **Kryptér arbejdsfiler**

1. Under **Filer i disse apps vil være beskyttet skal** du vælge den Office apps, du vil beskytte på mobilenheder.
1. Under **Who får disse indstillinger?** vælges alle brugere som standard, men du kan vælge Rediger for at vælge en af  de sikkerhedsgrupper, du har oprettet.
1. Vælg Tilføj for at afslutte oprettelsen af **politikken**.
1. På siden **Tilføj politik** skal du vælge **Luk**.
1. På startsiden for Administration skal du bekræfte, at din nye politik blev tilføjet ved at  vælge Politikker og gennemse politikken på **siden** Politikker.

## <a name="create-an-app-management-policy"></a>Opret en politik for appadministration

1. Gå til Administration på <a href="https://go.microsoft.com/fwlink/p/?linkid=837890" target="_blank">https://admin.microsoft.com</a>. 
    
2. I venstre navigationslinje skal du **vælge Tilføj** \> **enheder-politikker**\>.
  
3. Angiv et **entydigt** navn for denne politik i ruden Tilføj politik. 
    
4. Under **Politiktype** skal du **vælge Programadministration til Android** eller Programadministration **til iOS**, afhængigt af hvilket sæt politikker du vil oprette. 
    
5. **Udvid Beskyt arbejdsfiler, når enheder er gået tabt eller bliver stjålet** **og Administrer, hvordan Office adgang til filer på mobilenheder**. Konfigurer indstillingerne efter dine ønsker. **Administrer, hvordan brugere Office filer på mobilenheder** er slået Fra  som standard, men vi anbefaler, at du slår den **Til** og accepterer standardværdierne. Du kan finde flere oplysninger [under Tilgængelige indstillinger](#available-settings). 
    
    Du kan altid bruge linket **Nulstil standardindstillingerne** for at vende tilbage til standardindstillingen. 
    
    ![Skærmbillede af Opret en politik med Programadministration for Android markeret.](../../media/eabbe06d-ac0a-4f3a-8630-68c808b1e662.png)
  
6. Beslut **derefter Who får disse indstillinger?** Hvis du ikke vil bruge standardsikkerhedsgruppen Alle  brugere, skal du vælge **Rediger og vælge** de sikkerhedsgrupper, der får disse indstillinger \> **Vælg**.
    
7. Til sidst skal **du** vælge Udført for at gemme politikken og tildele den til enheder. 
    
## <a name="edit-an-app-management-policy"></a>Rediger en politik for appadministration

1. Vælg **Rediger politik** på **kortet Politikker**.
    
2. I **ruden Rediger** politik skal du vælge den politik, du vil ændre 
    
3. Vælg **Rediger** ud for hver indstilling for at ændre værdierne i politikken. Når du ændrer en værdi, gemmes den automatisk i politikken.
    
4. Når du er færdig, skal du lukke **ruden Rediger** politik. 
    
## <a name="delete-an-app-management-policy"></a>Slet en politik for appadministration

1. Vælg en **politik** på siden Politikker, og vælg derefter **Slet**.
    
2. I **ruden Slet politik** skal du vælge **Bekræft for** at slette den eller de politikker, du har valgt. 
    
## <a name="available-settings"></a>Tilgængelige indstillinger

Følgende tabeller giver detaljerede oplysninger om de indstillinger, der er tilgængelige til at beskytte arbejdsfiler på enheder, og de indstillinger, der styrer, hvordan brugere får adgang Office filer fra deres mobilenheder.
  
 Du kan finde flere oplysninger [under Hvordan er beskyttelsesfunktionerne i Microsoft 365 Business Premium til indstillinger i Intune](map-protection-features-to-intune-settings.md). 
  
### <a name="settings-that-protect-work-files"></a>Indstillinger, der beskytter arbejdsfiler

Følgende indstillinger er tilgængelige til beskyttelse af arbejdsfiler, hvis en brugers enhed mistes eller bliver stjålet:


|Indstilling  <br/> |Beskrivelse  <br/> |
|:-----|:-----|
|Slet arbejdsfiler fra en inaktiv enhed efter dette antal dage  <br/> |Hvis en enhed ikke bruges i det antal dage, du angiver her, slettes alle arbejdsfiler, der er gemt på enheden, automatisk.  <br/> |
|Tving brugerne til at gemme alle arbejdsfiler på OneDrive for Business  <br/> |Hvis denne indstilling er **til**, er den eneste tilgængelige lagringsplacering for arbejdsfiler OneDrive for Business.  <br/> |
|Kryptér arbejdsfiler  <br/> |Sørg for, at **denne** indstilling er indstillet til Til, så arbejdsfiler er beskyttet med kryptering. Selvom enheden mistes eller bliver stjålet, er der ingen, der kan læse virksomhedens data.  <br/> |
   
### <a name="settings-that-control-how-users-access-office-files-on-mobile-devices"></a>Indstillinger, der styrer, hvordan brugere får Office adgang til filer på mobilenheder

Følgende indstillinger er tilgængelige til at administrere, hvordan brugere får adgang Office arbejdsfiler:


|Indstilling  <br/> |Beskrivelse  <br/> |
|:-----|:-----|
|Kræv en pinkode eller et fingeraftryk for at få adgang Office apps  <br/> |Hvis denne indstilling er **aktiveret**, skal brugerne angive en anden form for godkendelse ud over deres brugernavn og adgangskode, før de kan bruge Office-apps på deres mobilenheder.<br/> |
|Nulstil pinkode, når logon mislykkes dette mange gange  <br/> |For at forhindre uautoriserede brugere i tilfældigt at gætte en pinkode nulstilles pinkoden efter det antal forkerte indtastninger, du angiver.  <br/> |
|Kræv, at brugerne logger på igen, Office apps har været inaktive i  <br/> |Denne indstilling bestemmer, hvor længe en bruger kan være inaktiv, før brugeren bliver bedt om at logge på igen.  <br/> |
|Afvisning af adgang til arbejdsfiler på jailbroken eller rootede enheder  <br/> |Intelligente brugere har muligvis en enhed, der er jailbroken eller rooted. Det betyder, at brugeren kan redigere i operativsystemet, hvilket kan betyde, at enheden bliver mere underlagt malware. Disse enheder blokeres, når denne indstilling er **indstillet til Til**.  <br/> |
|Tillad ikke, at brugere kopierer indhold fra Office apps til personlige apps  <br/> |Vi tillader dette som standard, men hvis indstillingen er **til, kan** brugeren kopiere oplysninger i en arbejdsfil til en personlig fil. Hvis indstillingen er **slået Fra**, kan brugeren ikke kopiere oplysninger fra en arbejdskonto til en personlig app eller personlig konto.  <br/> |

## <a name="see-also"></a>Se også

[De 10 mest populære måder at sikre Microsoft 365 planer til virksomheder på](../security-and-compliance/secure-your-business-data.md)