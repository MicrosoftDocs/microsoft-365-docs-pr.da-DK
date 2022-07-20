---
title: Hvordan knyttes beskyttelsesfunktioner i Microsoft 365 Business Premium til Intune indstillinger
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: high
ms.date: 07/19/2022
ms.collection: ''
ms.custom:
- MiniMaven
search.appverid:
- BCS160
- MET150
description: Få mere at vide om, hvordan beskyttelsesfunktioner i Microsoft 365 Business Premium kort for at Intune indstillinger. Abonnementet giver dig en licens til at ændre Intune indstillinger.
ms.openlocfilehash: b3a428e43bc42eb0d23cacc584afc370ab27dc10
ms.sourcegitcommit: c1eaea74c8ffce2f9f477c9469342e88e4a70c14
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/20/2022
ms.locfileid: "66893161"
---
# <a name="how-do-protection-features-in-microsoft-365-business-premium-map-to-intune-settings"></a>Hvordan knyttes beskyttelsesfunktioner i Microsoft 365 Business Premium til Intune indstillinger

## <a name="android-and-ios-application-protection-settings"></a>Indstillinger for beskyttelse af Android- og iOS-programmer

Følgende tabel indeholder oplysninger om, hvordan politikindstillingerne for Android- og iOS-programmet knyttes til Intune indstillinger.
  
Hvis du vil finde indstillingen for Intune, skal du logge på med dine legitimationsoplysninger som Microsoft 365 Business Premium administrator og gå til **Administration centre** og derefter **Intune**.
  
 > [!IMPORTANT]
 > 
 > Et Microsoft 365 Business Premium abonnement giver dig en licens til at ændre alle indstillingerne for Intune. Se [Introduktion til Intune for at komme i gang.](/intune/introduction-intune)
  
Vælg det ønskede &mdash; politiknavn, f.eks. Programpolitik til Android &mdash; , og vælg derefter **Politikindstillinger**.
  
Under **Beskyt arbejdsfiler, når enheder mistes eller bliver stjålet**
  
|**Politikindstilling for Android- eller iOS-program**|**Intune indstillinger**|
|:-----|:-----|
|Slet arbejdsfiler fra en inaktiv enhed efter  |Offlineinterval (dage), før appdata slettes  |
|Tving brugere til at gemme arbejdsfiler i OneDrive for Business  <br/> Bemærk, at kun OneDrive for Business er tilladt  |Vælg, hvilke lagertjenester firmadata kan gemmes i  |
   
Under **Administrer, hvordan brugeren får adgang til Office-filer på mobilenheder**
  
|**Politikindstilling for Android- eller iOS-program**|**Intune indstillinger**|
|:-----|:-----|
|Slet arbejdsfiler fra en inaktiv enhed efter  |Offlineinterval (dage), før appdata slettes  |
|Tving brugere til at gemme arbejdsfiler i OneDrive for Business  <br/> Bemærk, at kun OneDrive for Business er tilladt  |Vælg, hvilke lagertjenester firmadata kan gemmes i  |
|Kryptér arbejdsfiler  |Kryptér appdata  |
|Under **Administrer, hvordan brugeren får adgang til Office-filer på mobilenheder** ||
|Kræv en pinkode eller et fingeraftryk for at få adgang til Office-apps  | Kræv pinkode for at få adgang  <br/>  Dette angiver også:  <br/> **Tillad simpel pinkode** til **Ja** <br/> **Fastgør længde** til 4  <br/> **Tillad fingeraftryk i stedet for pinkode** til **Ja** <br/> **Deaktiver pinkode for app, når enhedspinkode administreres** til **Nej** |
|Nulstil pinkode, når logon mislykkes så mange gange (dette deaktiveres, hvis pinkode ikke er påkrævet)  |Antal forsøg før nulstilling af pinkode  |
|Kræv, at brugerne logger på igen, når Office-apps har været inaktive (dette er deaktiveret, hvis pinkode ikke er påkrævet)  | Kontrollér adgangskravene igen efter (minutter)  <br/>  Dette angiver også:  <br/> **Timeout** er angivet til minutter  <br/>  Det er det samme antal minutter, som du angiver i Microsoft 365 Business.  <br/> **Offlineperiode** er som standard angivet til 720 minutter  |
|Afvis adgang til arbejdsfiler på jailbroken- eller rooted-enheder  |Bloker administrerede apps fra at køre på jailbroken- eller rootede enheder  |
|Tillad brugere at kopiere indhold fra Office-apps til personlige apps  | Begræns klip, kopiér og indsæt med andre apps  <br/>  Hvis indstillingen Microsoft 365 Business Premium er angivet til **Til**, angives disse tre indstillinger også til **Alle apps** i Intune:  <br/> **Tillad, at appen overfører data til andre apps** <br/> **Tillad, at appen modtager data fra andre apps** <br/> **Begræns klip, kopiér og indsæt med andre apps** <br/>  Hvis indstillingen Microsoft 365 Business er **slået til,** er alle indstillingerne for Intune angivet til:  <br/> **Tillad, at appen overfører data til andre apps** er angivet til **Politikadministrerede apps** <br/> **Tillad, at appen modtager data fra andre apps** er angivet til **Alle apps** <br/> **Begræns klip, kopiér og sæt ind med andre apps** er angivet til **Politikadministrerede apps med Indsætning** |
   
## <a name="windows-10-app-protection-settings"></a>indstillinger for beskyttelse af Windows 10 apps

Følgende tabel indeholder oplysninger om, hvordan indstillingerne for Windows 10 programpolitik knyttes til Intune indstillinger.
  
Hvis du vil finde indstillingen for Intune, skal du logge på med dine Microsoft 365 Business Premium administratorlegitimationsoplysninger og gå til [Azure Portal](https://portal.azure.com). Vælg **Flere tjenester**, og skriv Intune i **Filteret**. Vælg **Intune apppolitik for appbeskyttelse**\>.
  
 > [!IMPORTANT]
 > Et Microsoft 365 Business Premium abonnement giver dig en licens til kun at ændre de Intune indstillinger, der er knyttet til de indstillinger, der er tilgængelige i Microsoft 365 Business Premium. 
  
Hvis du vil udforske de tilgængelige indstillinger, skal du vælge det ønskede politiknavn og derefter vælge **Generelt, Tildelinger**, **Tilladte apps**, **Undtaget apps**, **Påkrævede indstillinger** eller **Avancerede indstillinger** i venstre navigationsrude. 
  
|**politikindstilling for Windows 10 program**|**Intune indstillinger**|
|:-----|:-----|
|Kryptér arbejdsfiler  |**Avancerede indstillinger** \> **Databeskyttelse**: **Tilbagekald krypteringsnøgler ved framelding** og **tilbagekald adgang til beskyttede dataenheder, der tilmelder sig MDM** , er begge angivet til **Til**.  |
|Undgå, at brugerne kopierer virksomhedsdata til personlige filer.  |**Påkrævede indstillinger** \> **Windows Information Protection-tilstand**. **Slået** til i Microsoft 365 Business Premium kort til: **Skjul tilsidesættelser**, **Fra** i Microsoft 365 Business Premium kort til: **Fra**.  |
|Adgangskontrol til Office-dokumenter  | Hvis dette er angivet til **Til** i Microsoft 365 Business Premium,  <br/> **Avancerede indstillinger** \> **Access**, **Brug Windows Hello til virksomheder som en metode til at logge på Windows** er angivet til **Til** med følgende yderligere indstillinger:  <br/> **Angiv det mindste antal tegn, der kræves for pinkoden,** er angivet til **4**.  <br/> **Konfigurer brugen af store bogstaver i den Windows Hello til virksomheder pinkode** er angivet til **Tillad ikke brug af store bogstaver til pinkode**.  <br/> **Konfigurer brugen af små bogstaver i den Windows Hello til virksomheder pinkode** er angivet til **Tillad ikke brug af små bogstaver til pinkode**.  <br/> **Konfigurer brugen af specialtegn i den Windows Hello til virksomheder pinkode** er angivet til **Tillad ikke brug af specialtegn i pinkode**.  <br/> **Angiv den tidsperiode (i dage), som en pinkode kan bruges, før systemet kræver, at brugeren skal ændre** den, indstilles til **0**.  <br/> **Angiv antallet af tidligere PIN'er, der kan knyttes til en brugerkonto, som ikke kan genbruges,** er angivet til **0**.  <br/> **Antallet af godkendelsesfejl, der er tilladt, før enheden slettes** , er angivet til samme som i Microsoft 365 Business (5 som standard).  <br/> **Den maksimale mængde tid (i minutter), der er tilladt, efter at enheden er inaktiv, og som medfører, at enheden bliver pinkode eller adgangskodelåst** , er angivet til samme som i Microsoft 365 Business.  |
|Aktivér gendannelse af beskyttede data  |**Avancerede indstillinger** \> **Databeskyttelse**: **Vis ikonet for databeskyttelse i virksomheden**, og **Brug Azure RMS til WIP** er **slået til.**  |
|Beskyt yderligere placeringer i virksomhedens cloudmiljøer  |**Avancerede indstillinger** \> **Beskyttede domæner** og **cloudressourcer** viser domæner og SharePoint-websteder.  |
|Filer, der bruges af disse apps, er beskyttet  |Listen over beskyttede apps er angivet i **Tilladte apps**.  |
   
## <a name="windows-10-device-protection-settings"></a>Windows 10 indstillinger for enhedsbeskyttelse

Følgende tabel indeholder oplysninger om, hvordan indstillingerne for Windows 10 enhedskonfiguration knyttes til Intune indstillinger.
  
Hvis du vil finde indstillingen for Intune, skal du logge på med dine Microsoft 365 Business Premium administratorlegitimationsoplysninger og gå til [Azure Portal](https://portal.azure.com) og derefter vælge **Flere tjenester** og skrive Intune i **filteret**, vælge **Intune** \> **Enhedskonfiguration** \> **Profiler**. Vælg derefter **Enhedspolitik for Windows 10** \> **Egenskaber** \> **.**
  
|**politikindstilling for Windows 10 enhed**|**Intune indstillinger**|
|:-----|:-----|
|Hjælp med at beskytte pc'er mod virus og andre trusler ved hjælp af Microsoft Defender Antivirus  |Tillad overvågning i realtid = SLÅET TIL  <br/> Tillad cloudbeskyttelse = SLÅET TIL  <br/> Bed brugerne om indsendelse af eksempler = Send automatisk sikre eksempler (send automatisk standardeksempler, der ikke er pii)  |
|Hjælp med at beskytte pc'er mod webbaserede trusler i Microsoft Edge  |**SmartScreen** i **Edge Browser-indstillingerne** er angivet til **Påkrævet**.  |
|Slå enhedsskærmen fra, når den er inaktiv i (minutter)  |Maksimalt antal minutter med inaktivitet, indtil skærmlåse (minutter)  |
|Tillad brugere at downloade apps fra Microsoft Store  |Brugerdefineret URI-politik  |
|Tillad brugere at få adgang til Cortana  |**Generelle** \> **Cortana er indstillet** til **at blokere** i Intune, når den er **slået fra** i Microsoft 365 Business Premium.  |
|Tillad brugere at modtage Tip og reklamer til Windows fra Microsoft  |**Windows Spotlys**, alt sammen blokeret, hvis dette er slået **fra** i Microsoft 365 Business Premium.  |
|Hold Windows 10 enheder opdateret automatisk  | Denne indstilling er i **Microsoft Intune** \> **tjenesteopdateringer – Windows 10 Opdateringsringe**, vælg **Opdateringspolitik for Windows 10 enheder** og derefter **Egenskaber** \> **Indstillinger**.  <br/>  Når indstillingen Microsoft 365 Business Premium er **slået til,** angives alle følgende indstillinger:  <br/> **Tjenesteforgreningen** er indstillet til **CB** (CBB, når denne er slået fra i Microsoft 365 Business Premium).  <br/> **Microsoft-produktopdateringer** er angivet til **Tillad**.  <br/> **Windows-drivere** er angivet til **Tillad**.  <br/> **Funktionsmåden for automatisk opdatering** er indstillet til **Automatisk installation på vedligeholdelsestidspunktet** med:  <br/> **Efter timer er start** indstillet til **6 AM**.  <br/> **Slut på aktive timer** er indstillet til **10 PM**.  <br/> **Udskydelsesperioden for kvalitetsopdateringen (dage)** er angivet til **0**.  <br/> **Udsættelsesperioden for funktionsopdateringen (dage)** er angivet til **0**.  <br/> **Downloadtilstanden for leveringsoptimering** er angivet til **HTTP blandet med peering bag samme NAT**.  |

## <a name="see-also"></a>Se også

[Bedste praksis for sikring af Microsoft 365 til virksomheder-planer](../admin/security-and-compliance/secure-your-business-data.md)
