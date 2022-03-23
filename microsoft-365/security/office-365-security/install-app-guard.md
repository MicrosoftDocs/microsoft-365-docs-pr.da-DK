---
title: Application Guard til Office til administratorer
keywords: application guard, protection, isolation, isoleret beholder, hardwareisolation
f1.keywords:
- NOCSH
ms.author: maccruz
author: schmurky
manager: dansimp
audience: ITPro
ms.topic: article
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.collection: M365-security-compliance
description: Få den nyeste hardwarebaserede isolation. Undgå aktuelle og nye angreb som udnyttelse eller ondsindede links i at forstyrre medarbejdernes produktivitet og virksomhedens sikkerhed.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: d1dfe0bf7082d05fa534a34cb0dd55d9227fca1a
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/14/2022
ms.locfileid: "63591027"
---
# <a name="application-guard-for-office-for-admins"></a>Application Guard til Office til administratorer

**Gælder for:** Word, Excel og PowerPoint til Microsoft 365, Windows 10 Enterprise, Windows 11 Enterprise

Microsoft Defender Application Guard for Office (Application Guard til Office) hjælper med at forhindre upålidelige filer i at få adgang til pålidelige ressourcer, så din virksomhed er beskyttet mod nye og kommende angreb. Denne artikel gennemgår administratorers konfiguration af enheder for at få en forhåndsvisning af Application Guard Office. Den indeholder oplysninger om systemkrav og installationstrin til at aktivere Application Guard til Office på en enhed.

## <a name="prerequisites"></a>Forudsætninger

### <a name="minimum-hardware-requirements"></a>Minimumskrav til hardware

* **CPU**: 64-bit, 4 kerner (fysisk eller virtuelle), virtualiseringsudvidelser (Intel VT-x ELLER AMD-V), Core i5-ækvivalent eller højere anbefalet
* **Fysisk hukommelse**: 8 GB RAM
* **Harddisk**: 10 GB ledig plads på systemdrevet (SSD anbefales)

### <a name="minimum-software-requirements"></a>Minimumskrav til software

* **Windows**: Windows 10 Enterprise version, klient build version 2004 (20H1) build 19041 eller nyere. Alle versioner af Windows 11 understøttes. 
* **Office**: Office Aktuel kanal og Månedlig virksomhedskanal, Build version 2011 16.0.13530.10000 eller nyere. Office Semi-Annual virksomhedskanal, Build version 2108 eller nyere. Både 32-bit og 64-bit versioner af Office understøttes.
* **Opdateringspakke**: Windows 10 månedlig sikkerhedsopdatering [KB4571756](https://support.microsoft.com/help/4571756/windows-10-update-KB4571756)

Du kan finde detaljerede systemkrav under [Systemkrav til Microsoft Defender Application Guard](/windows/security/threat-protection/microsoft-defender-application-guard/reqs-md-app-guard). Se også computerproducentens vejledninger til aktivering af virtualiseringsteknologi.
Hvis du vil vide mere Office om opdateringskanaler, [skal du se Oversigt over opdateringskanaler Microsoft 365](/deployoffice/overview-update-channels).

### <a name="licensing-requirements"></a>Licenskrav

* Microsoft 365 E5 eller Microsoft 365 E5 Sikkerhed

> [!NOTE]
> Microsoft 365 Apps for enterprise med den enhedsbaserede licens, har ikke adgang til Application Guard til Office.

## <a name="deploy-application-guard-for-office"></a>Installér Application Guard til Office

### <a name="enable-application-guard-for-office"></a>Aktivér Application Guard til Office

1. Download og **installér Windows 10 månedlige sikkerhedsopdateringer KB4571756**.

2. Vælg **Microsoft Defender Application Guard** under Windows funktioner, og vælg **OK**. Hvis du aktiverer Application Guard-funktionen, bliver du bedt om at genstarte systemet. Du kan vælge at genstarte nu eller efter trin 3.

   ![Windows Funktioner, der viser AG.](../../media/ag03-deploy.png)

   Funktionen kan også aktiveres ved at køre følgende PowerShell-kommando som administrator:

   ```powershell
   Enable-WindowsOptionalFeature -online -FeatureName Windows-Defender-ApplicationGuard
   ```

3. Søg efter **Microsoft Defender Application Guard i administreret tilstand**, en gruppepolitik i **ComputerkonfigurationAdministrative\\ skabeloner\\ Windows Komponenter\\ Microsoft Defender Application Guard**. Slå denne politik til ved at angive værdien under Indstillinger **som 2** eller **3**, og vælg derefter **OK** eller **Anvend**.

   ![Slå AG til i administreret tilstand.](../../media/ag04-deploy.png)

   I stedet kan du angive den tilsvarende CSP-politik:

   > OMA-URI: **./Device/Vendor/MSFT/WindowsDefenderApplicationGuard/Indstillinger/AllowWindowsDefenderApplicationGuard** <br> Datatype: **Heltal** <br> Værdi: **2**

4. Genstart systemet.

### <a name="set-diagnostics--feedback-to-send-full-data"></a>Angiv & til at sende komplette data

> [!NOTE]
> Dette er dog ikke påkrævet, men konfiguration af valgfrie diagnosticeringsdata kan hjælpe med at diagnosticere rapporterede problemer.

Dette trin sikrer, at de data, der er nødvendige for at identificere og løse problemer, når frem til Microsoft. Følg disse trin for at aktivere diagnosticering på din Windows enhed:

1. Åbn **Indstillinger** fra menuen Start.

   ![menuen Start.](../../media/ag05-diagnostic.png)

2. På siden **Windows Indstillinger** du vælge Beskyttelse af **personlige oplysninger**.

   ![Windows Indstillinger menu.](../../media/ag06-diagnostic.png)

3. Under Beskyttelse af personlige oplysninger **skal du & feedback og** vælge **Valgfrie diagnostiske data**.

   ![Menuen Diagnosticering og feedback.](../../media/ag07a-diagnostic.png)

Du kan finde flere oplysninger Windows konfiguration af diagnosticeringsindstillinger i [Konfiguration Windows diagnostiske data i organisationen](/windows/privacy/configure-windows-diagnostic-data-in-your-organization#enterprise-management).

### <a name="confirm-that-application-guard-for-office-is-enabled-and-working"></a>Bekræft, at Application Guard til Office er aktiveret og virker

Før du bekræfter, at Application Guard til Office er aktiveret, skal du starte Word, Excel eller PowerPoint på en enhed, hvor politikkerne er blevet installeret. Kontrollér, Office er aktiveret. Det kan være nødvendigt at bruge din arbejdsidentitet til at aktivere Office produktet først.

For at bekræfte at Application Guard til Office er aktiveret, skal du starte Word, Excel eller PowerPoint og derefter åbne et dokument, der ikke er tillid til. Du kan f.eks. åbne et dokument, der er hentet fra internettet, eller en vedhæftet fil i en mail fra en person uden for organisationen.

Når du åbner en fil, der ikke er tillid til, vises der Office velkomstbillede som i følgende eksempel. Den kan vises i et stykke tid, mens Application Guard Office er ved at blive aktiveret, og filen åbnes. Efterfølgende åbning af upålidelige filer bør være hurtigere.

![Office-app velkomstbillede.](../../media/ag08-confirm.png)

Når filen er åbnet, bør den vise et par visuelle indikatorer for, at filen blev åbnet inde i Application Guard Office:

* Enforklaring på båndet

  ![Dokumentfil, der viser en lille App Guard-note.](../../media/ag09-confirm.png)

* Programikonet med et skjold på proceslinjen

  ![Ikon på proceslinjen.](../../media/ag12-limitations.png)

## <a name="configure-application-guard-for-office"></a>Konfigurer Application Guard til Office

Office understøtter følgende politikker, så du kan konfigurere funktionaliteterne i Application Guard til Office. Disse politikker kan konfigureres via gruppepolitikker eller via Office [skypolitiktjeneste](/DeployOffice/overview-office-cloud-policy-service).


> [!NOTE]
> Konfiguration af disse politikker kan deaktivere visse funktioner for filer, der åbnes i Application Guard til Office.

|Politik|Beskrivelse|
|---|---|
|Brug ikke Application Guard til Office|Aktivering af denne politik tvinger Word, Excel og PowerPoint til at bruge isolationsbeholderen beskyttet visning i stedet for Application Guard til Office. Denne politik kan bruges til midlertidigt at deaktivere Application Guard til Office når der er problemer med at lade den være aktiveret til Microsoft Edge.|
|Konfigurer Application Guard til Office for oprettelse af objektbeholder|Denne politik bestemmer, om Application Guard til Office objektbeholder til at isolere upålidelige filer på forhånd er oprettet for at forbedre kørselsydeevnen. Hvis du aktiverer denne indstilling, kan du angive, hvor mange dage du vil fortsætte med at oprette en objektbeholder, Office den indbyggede heuristiske oprettelse af beholderen.
|Tillad ikke kopiér/sæt ind for Office dokumenter, der er åbnet i Application Guard til Office|Aktivering af denne politik forhindrer en bruger i at kopiere og indsætte indhold fra et dokument, der er åbnet i Application Guard, for Office til et dokument, der er åbnet uden for det.|
|Deaktiver hardwareacceleration i Application Guard til Office|Denne politik styrer, om Application Guard til Office bruger hardwareacceleration til at gengive grafik. Hvis du aktiverer denne indstilling, bruger Application Guard til Office softwarebaseret (CPU) gengivelse og indlæser ikke nogen tredjeparts grafikdrivere eller interagerer med noget forbundet grafikhardware.
|Deaktiver ikke-understøttet beskyttelse af filtyper i Application Guard til Office|Denne politik styrer, om Application Guard til Office blokerer ikke-understøttede filtyper i at blive åbnet, eller om det vil aktivere omdirigeringen til Beskyttet visning.
|Slå kamera- og mikrofonadgang fra for dokumenter, der er åbnet i Application Guard, Office|Aktivering af denne politik fjerner Office adgang til kameraet og mikrofonen i Application Guard til Office.|
|Begræns udskrivning fra dokumenter, der er åbnet i Application Guard, Office|Hvis du aktiverer denne politik, begrænses de printere, som en bruger kan udskrive til, fra en fil, der åbnes i Application Guard, Office. Du kan f.eks. bruge denne politik til at begrænse brugere til kun at udskrive til PDF.|
|Forebyg, at brugere fjerner Application Guard Office beskyttelse af filer|Aktivering af denne politik fjerner indstillingen (i Office-programoplevelsen) for at deaktivere Application Guard for Office-beskyttelse eller for at åbne en fil uden for Application Guard Office. <p> **Bemærk!** Brugere kan stadig tilsidesætte denne politik ved manuelt at fjerne egenskaben Mark-of-the-web fra filen eller ved at flytte et dokument til en placering, der er tillid til.|
|

> [!NOTE]
> Følgende politikker kræver, at brugeren logger af og logger på igen for at Windows træder i kraft:
>
> * Deaktiver kopiér/sæt ind for dokumenter, der er åbnet i Application Guard Office
> * Begræns udskrivning for dokumenter, der er åbnet i Application Guard til Office
> * Slå kamera- og mikrofonadgang til dokumenter, der er åbnet i Application Guard, Office

## <a name="submit-feedback"></a>Send feedback

### <a name="submit-feedback-via-feedback-hub"></a>Send feedback via Feedback Hub

Hvis du støder på problemer, når du starter Application Guard Office, opfordres du til at sende din feedback via Feedback Hub:

1. Åbn **Feedback Hub-appen,** og log på.

2. Hvis du får en fejldialogboks, når du starter Application Guard, skal du **vælge Rapportér til Microsoft** i fejldialogboksen for at starte en ny feedbackindsendelse. Ellers skal du gå <https://aka.ms/mdagoffice-fb> til den korrekte kategori for Application Guard og derefter vælge **+&nbsp;Tilføj ny feedback øverst** til højre.

3. Angiv en oversigt i feltet **Opsummer din feedback** , hvis det ikke allerede er udfyldt for dig.

4. Angiv en detaljeret beskrivelse af det problem, du har oplevet, og hvilke trin du har taget, i feltet Forklar **mere detaljeret,** og vælg derefter **Næste**.

5. Vælg boblen ud for **Problem**. Kontrollér, at den valgte kategori **er Sikkerhed og beskyttelse af \> personlige oplysninger Microsoft Defender Application Guard – Office**, og vælg derefter **Næste**.

6. Vælg **Ny feedback** og derefter **Næste**.

7. Indsaml sporinger om problemet:

   1. Udvid **feltet Genskab** mit problem.

   2. Hvis det problem, du oplever, opstår, mens Application Guard kører, skal du åbne en Application Guard-forekomst. Hvis du åbner en forekomst, kan du indsamle yderligere sporinger fra Application Guard-beholderen.

   3. Vælg **Start optagelse**, og vent på, at feltet stopper med at dreje, og sig *Stop optagelsen*.

   4. Genskab problemet fuldt ud med Application Guard. Reproduktion kan omfatte forsøg på at starte en Application Guard-forekomst og vente, indtil den mislykkes, eller kopiering af et problem i en kørende Application Guard-forekomst.

   5. Vælg feltet **Stop** optagelse.

   6. Hold alle kørende Application Guard-forekomster åbne, selv i nogle minutter efter indsendelse, så containerdiagnosticering også kan indsamles.

8. Vedhæft relevante skærmbilleder eller filer, der er relateret til problemet.

9. Vælg **Send**.

### <a name="submit-feedback-via-office-customer-voice"></a>Send feedback via Office Customer Voice

Du kan også sende feedback fra Office, hvis problemet opstår, Office dokumenter åbnes i Application Guard. Refer to the [Office Insider Handbook](https://insider.office.com/handbook) for submitting feedback.

## <a name="integration-with-microsoft-defender-for-endpoint-and-microsoft-defender-for-office-365"></a>Integration med Microsoft Defender for Endpoint og Microsoft Defender Office 365

Application Guard til Office er integreret med Microsoft Defender for Endpoint, så der kan overvåges og advares om ondsindet aktivitet, der sker i det isolerede miljø.

[Pengeskab Dokumenter i Microsoft E365 E5](/microsoft-365/security/office-365-security/safe-docs) er en funktion, der bruger Microsoft Defender til slutpunkt til at scanne dokumenter, der er åbnet i Application Guard for Office. For et ekstra lag af beskyttelse kan brugere ikke forlade Application Guard Office indtil resultaterne af scanningen er blevet fastlagt.

Microsoft Defender til Slutpunkt er en sikkerhedsplatform, der er udviklet til at hjælpe virksomhedsnetværk med at forhindre, registrere, undersøge og reagere på avancerede trusler. Du kan finde flere oplysninger om denne platform [under Microsoft Defender til slutpunkt](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp). Hvis du vil have mere at vide om onboardingenheder på denne platform, skal du [se Onboard-enheder til Microsoft Defender for Endpoint-tjenesten](/windows/security/threat-protection/microsoft-defender-atp/onboard-configure).

Du kan også konfigurere Microsoft Defender, så Office 365 kan arbejde sammen med Defender til slutpunktet. Du kan finde flere oplysninger [i Integrer Defender Office 365 med Microsoft Defender til slutpunkt](integrate-office-365-ti-with-mde.md).

## <a name="limitations-and-considerations"></a>Begrænsninger og overvejelser

* Application Guard til Office er en beskyttet tilstand, der isolerer dokumenter, der ikke er tillid til, så de ikke kan få adgang til virksomhedens ressourcer, et intranet, brugerens identitet og tilfældige filer på computeren. Det betyder, at hvis en bruger forsøger at få adgang til en funktion, der er afhængig af en sådan adgang, f.eks. indsættelse af et billede fra en lokal fil på disken, mislykkes adgangen, og der vises en prompt, der ligner eksemplet nedenfor. For at aktivere et dokument, der ikke er tillid til, for at få adgang til ressourcer, der er tillid til, skal brugerne fjerne Application Guard-beskyttelsen fra dokumentet. 

  ![Dialogboks, der siger, at Denne funktion ikke er tilgængelig for at hjælpe dig med at beskytte dig.](../../media/ag10-limitations.png)

  > [!NOTE]
  > Anbefaler brugerne, at de kun fjerner beskyttelsen, hvis de har tillid til filen og dens kilde, eller hvor den stammer fra.

* Når et dokument, der ikke er tillid til, er gemt på en placering, der er tillid til, nedarves tillid til placeringen af dokumentet. En organisations skylager identificeres typisk som en pålidelig placering.
  
* Aktivt indhold i dokumenter som makroer og ActiveX er deaktiveret i Application Guard til Office. Brugere skal fjerne Application Guard-beskyttelse for at aktivere aktivt indhold.

* Upålidelige filer fra netværksshares eller filer, der er delt fra OneDrive, OneDrive for Business eller SharePoint Online fra en anden organisation, der er åben som skrivebeskyttet i Application Guard. Brugere kan gemme en lokal kopi af sådanne filer for at fortsætte arbejdet i beholderen eller fjerne beskyttelsen for at arbejde direkte med den oprindelige fil.

* Filer, der er beskyttet af IRM (Information Rights Management), er som standard blokeret. Hvis brugerne vil åbne disse filer i beskyttet visning, skal en administrator konfigurere politikindstillinger for ikke-understøttede filtyper for organisationen.

* Eventuelle tilpasninger af Office i Application Guard til Office bevares ikke, når en bruger logger ud og logger på igen, eller når enheden genstartes.

* Kun tilgængelighedsværktøjer, der bruger UIA-rammen, kan give en handicapvenlig oplevelse for filer, der er åbnet i Application Guard til Office.

* Netværksforbindelsen er påkrævet for den første start af Application Guard efter installationen. Der kræves forbindelse, for at Application Guard kan validere licensen.

* I dokumentets oplysningssektion kan egenskaben *Sidst ændret af* vise **WDAGUtilityAccount** som brugeren. WDAGUtilityAccount er den anonyme bruger, der er konfigureret i Application Guard. Desktopbrugerens identitet deles ikke i Application Guard-beholderen.

## <a name="performance-optimizations-for-application-guard-for-office"></a>Optimering af ydeevnen for Application Guard til Office

Dette afsnit indeholder en oversigt over de optimeringer af ydeevnen, der bruges i Application Guard til Office. Disse oplysninger kan hjælpe administratorer med at diagnosticere rapporter fra brugere i forbindelse med ydeevnen af Office eller det overordnede system, når Application Guard er aktiveret.

Application Guard bruger en virtualiseret beholder til at isolere upålidelige dokumenter væk fra systemet. Processen med at oprette en beholder og konfigurere Application Guard-beholderen til at åbne Office-dokumenter har en ydeevne, der kan påvirke brugeroplevelsen negativt, når brugere åbner et dokument, der ikke er tillid til.

For at give brugerne den forventede filåbningsoplevelse bruger Application Guard logik til at oprette en beholder på forhånd, når følgende heuristisk er opfyldt på et system: En bruger har åbnet en fil i enten Beskyttet visning eller Application Guard inden for de seneste 28 dage.

Når denne heuristiske værdi er nået, Office du oprette en Application Guard-beholder for brugeren, når de er logget på Windows. Mens denne handling før oprettelse er i gang, kan systemet opleve langsom ydeevne, men effekten vil blive løst, så snart handlingen er fuldført.

> [!NOTE]
> De tip, der er nødvendige for den heuristiske måde at oprette beholderen på, genereres af Office som en bruger bruger bruger dem. Hvis en bruger installerer Office på et nyt system, hvor Application Guard er aktiveret, vil Office først oprette beholderen efter første gang, en bruger åbner et dokument, der ikke er tillid til, på systemet. Brugeren vil se, at det tager længere tid at åbne denne første fil i Application Guard.

## <a name="known-issues"></a>Kendte problemer

* Hvis du vælger weblinks`http` ( `https`eller ) åbnes browseren ikke.
* Standardindstillingen for beskyttelsespolitik for kopiering og indsættelse er at aktivere adgang til kun tekst i Udklipsholder.
* Standardindstillingen for en politik for ikke-understøttede filtyper er at blokere for åbning af upålidelige ikke-understøttede filtyper, der er krypteret eller har IRM -sæt (Information Rights Management). Dette omfatter filer, der Microsoft Information Protection følsomhedsmærkater ved hjælp af kryptering (fortroligt eller meget fortroligt).
* CSV- og HTML-filer understøttes ikke på nuværende tidspunkt.
* Application Guard til Office fungerer i øjeblikket ikke med NTFS-komprimerede volumener. Hvis du får vist fejlmeddelelsen "ERROR_VIRTUAL_DISK_LIMITATION", skal du prøve at fjerne dekomprimering af lydstyrken.
* Opdateringer til .NET kan medføre, at filer ikke åbnes i Application Guard. Som en midlertidig løsning kan brugerne genstarte enheden, når fejlen opstår. Få mere at vide om problemet ved modtagelse af en fejlmeddelelse, når du forsøger at [åbne Windows Defender Application Guard eller Windows sandkasse](https://support.microsoft.com/help/4575917/receiving-an-error-message-when-attempting-to-open-windows-defender-ap).
* Se Ofte [stillede spørgsmål - Microsoft Defender Application Guard for at få flere oplysninger.](/windows/security/threat-protection/microsoft-defender-application-guard/faq-md-app-guard) 
