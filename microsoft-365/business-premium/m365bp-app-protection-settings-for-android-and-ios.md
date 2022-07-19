---
title: Angiv indstillinger for appbeskyttelse for Android- eller iOS-enheder
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: Admin
ms.topic: how-to
ms.service: o365-administration
ms.localizationpriority: high
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
description: Få mere at vide om, hvordan du opretter, redigerer eller sletter en politik for administration af apps og beskytter arbejdsfiler på Android- eller iOS-enheder.
ms.openlocfilehash: 60bc5b3b69eacf9573dd806734cb47355266d3a5
ms.sourcegitcommit: e9692a40dfe1f8c2047699ae3301c114a01b0d3a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/01/2022
ms.locfileid: "66858909"
---
# <a name="set-app-protection-settings-for-android-or-ios-devices"></a>Angiv indstillinger for appbeskyttelse for Android- eller iOS-enheder

Se [Microsoft 365 small business-hjælp](https://go.microsoft.com/fwlink/?linkid=2197659) på YouTube.

Denne artikel gælder for Microsoft 365 Business Premium.

## <a name="watch-secure-office-apps-on-ios"></a>Se: Secure Office-apps på iOS

Se denne og andre videoer på vores [YouTube-kanal](https://go.microsoft.com/fwlink/?linkid=2197828).

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE1FLvZ?autoplay=false]

Du kan konfigurere en politik for brugeradgang, der kræver, at mobilbrugere angiver en pinkode eller et fingeraftryk for at logge på, og du kan også kryptere arbejdsfiler, der er gemt på deres enheder.

1. Log på <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 Administration</a>.

2. Under **Politikker** skal du vælge **Tilføj politik**.

3. Angiv et navn under **Politiknavn** i ruden **Tilføj politik**, og vælg den ønskede politiktype under **Politiktype**.

4. Slå **Beskyt arbejdsfiler til, når enheder mistes eller bliver stjålet**, og sørg derefter for, at følgende tre indstillinger er slået til:
 
    - **Tving brugerne til at gemme alle arbejdsfiler i OneDrive for Business**
  
    - **Kryptér arbejdsfiler**

5. Slå **Administrer, hvordan brugere får adgang til Office-filer på mobilenheder** , og sørg for, at indstillingerne er slået til eller angivet for hvert element.

6. Under **Filer i disse apps vil blive beskyttet** skal du vælge de Office-apps, du vil beskytte på mobilenheder.

7. Under **Hvem får disse indstillinger?** er alle brugere valgt som standard, men du kan vælge **Skift** for at vælge de sikkerhedsgrupper, du har oprettet.

8. Vælg **Tilføj** for at afslutte oprettelsen af politikken.

9. På siden **Tilføj politik** skal du vælge **Luk**.

10. På startsiden for Administration skal du bekræfte, at din nye politik blev tilføjet, ved at vælge **Politikker** og gennemse politikken på siden **Politikker** .

## <a name="create-an-app-management-policy"></a>Opret en politik for administration af apps

1. Gå til Administration på <a href="https://go.microsoft.com/fwlink/p/?linkid=837890" target="_blank">https://admin.microsoft.com</a>.

2. Vælg **Tilføj enhedspolitikker** \>  \> i venstre **navigationsrude**.
  
3. Angiv et entydigt navn til denne politik i ruden **Tilføj politik** .

4. Under **Politiktype** skal du vælge **Programadministration til Android** eller **Programadministration til iOS**, afhængigt af hvilket sæt politikker du vil oprette.

5. Udvid **Beskyt arbejdsfiler, når enheder mistes eller stjåles** , og **Administrer, hvordan brugere får adgang til Office-filer på mobilenheder**. Konfigurer indstillingerne, som du vil. **Administrer, hvordan brugere får adgang til Office-filer på mobilenheder** er **som standard slået fra** , men vi anbefaler, at du slår den **til** og accepterer standardværdierne. Du kan få flere oplysninger under [Tilgængelige indstillinger](#available-settings).

    Du kan altid bruge linket **Gendan standardindstillinger** til at vende tilbage til standardindstillingen.

:::image type="content" source="Media/m365bp-add-policy.png" alt-text="Opret en politik med programstyring.":::
  
6. Beslut derefter **, hvem der får disse indstillinger?** Hvis du ikke vil bruge standardsikkerhedsgruppen **Alle brugere** , skal du vælge **Skift** og vælge de sikkerhedsgrupper, der får disse indstillinger \> **Vælg**.

7. Til sidst skal du vælge **Udført** for at gemme politikken og tildele den til enheder.

## <a name="edit-an-app-management-policy"></a>Rediger en politik for appadministration

1. Vælg **Rediger politik** på kortet **Politikker**.

2. Vælg den politik, du vil ændre, i ruden **Rediger politik** .

3. Vælg **Rediger** ud for hver indstilling for at ændre værdierne i politikken. Når du ændrer en værdi, gemmes den automatisk i politikken.

4. Når du er færdig, skal du lukke ruden **Rediger politik** .

## <a name="delete-an-app-management-policy"></a>Slet en politik for appadministration

1. Vælg en politik på siden **Politikker** , og vælg derefter **Slet**.

2. I ruden **Slet politik** skal du vælge **Bekræft** for at slette den eller de politikker, du har valgt. 

## <a name="available-settings"></a>Tilgængelige indstillinger

Følgende tabeller indeholder detaljerede oplysninger om de indstillinger, der er tilgængelige for at beskytte arbejdsfiler på enheder, og de indstillinger, der styrer, hvordan brugerne får adgang til Office-filer fra deres mobilenheder.
  
 Du kan få flere oplysninger under [Hvordan kan beskyttelsesfunktioner i Microsoft 365 Business Premium knyttes til Intune indstillinger](m365bp-map-protection-features-to-intune-settings.md). 
  
### <a name="settings-that-protect-work-files"></a>Indstillinger, der beskytter arbejdsfiler

Følgende indstillinger er tilgængelige til beskyttelse af arbejdsfiler, hvis en brugers enhed mistes eller bliver stjålet:


|Indstilling  |Beskrivelse  |
|:-----|:-----|
|Slet arbejdsfiler fra en inaktiv enhed efter dette antal dage  |Hvis en enhed ikke bruges i det antal dage, du angiver her, slettes alle arbejdsfiler, der er gemt på enheden, automatisk.  |
|Tving brugerne til at gemme alle arbejdsfiler i OneDrive for Business  |Hvis denne indstilling er **Slået** til, er den eneste tilgængelige lagringsplacering for arbejdsfiler OneDrive for Business.  |
|Kryptér arbejdsfiler  |Bevar denne indstilling **Til** , så arbejdsfiler beskyttes af kryptering. Selvom enheden mistes eller bliver stjålet, kan ingen læse dine virksomhedsdata.  |

### <a name="settings-that-control-how-users-access-office-files-on-mobile-devices"></a>Indstillinger, der styrer, hvordan brugerne får adgang til Office-filer på mobilenheder

Følgende indstillinger er tilgængelige til at administrere, hvordan brugere får adgang til Office-arbejdsfiler:

|Indstilling  |Beskrivelse  |
|:-----|:-----|
|Kræv en pinkode eller et fingeraftryk for at få adgang til Office-apps  |Hvis denne indstilling er **Til** , skal brugerne angive en anden form for godkendelse ud over deres brugernavn og adgangskode, før de kan bruge Office-apps på deres mobilenheder.|
|Nulstil pinkode, når logon mislykkes så mange gange  |For at forhindre en uautoriseret bruger i tilfældigt at gætte en pinkode, nulstilles pinkoden efter antallet af forkerte poster, som du angiver.  |
|Kræv, at brugerne logger på igen, når Office-apps har været inaktive i  |Denne indstilling bestemmer, hvor længe en bruger må være inaktiv, før vedkommende bliver bedt om at logge på igen.  |
|Afvis adgang til arbejdsfiler på jailbroken- eller rooted-enheder  |Smarte brugere kan have en enhed, der er jailbroken eller rooted. Det betyder, at brugeren kan ændre operativsystemet, hvilket kan gøre enheden mere udsat for malware. Disse enheder blokeres, når denne indstilling er **slået til**.  |
|Tillad ikke, at brugerne kopierer indhold fra Office-apps til personlige apps  |Vi tillader dette som standard, men hvis indstillingen er **Slået** til, kan brugeren kopiere oplysninger i en arbejdsfil til en personlig fil. Hvis indstillingen er **Slået fra**, kan brugeren ikke kopiere oplysninger fra en arbejdskonto til en personlig app eller personlig konto.  |

## <a name="see-also"></a>Se også

[Bedste praksis for sikring af Microsoft 365 til virksomheder-planer](../admin/security-and-compliance/secure-your-business-data.md)