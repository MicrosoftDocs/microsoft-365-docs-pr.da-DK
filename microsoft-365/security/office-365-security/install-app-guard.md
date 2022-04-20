---
title: Application Guard til Office for administratorer
keywords: application guard, beskyttelse, isolation, isoleret objektbeholder, hardwareisolation
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
description: Få den nyeste hardwarebaserede isolation. Undgå aktuelle og nye angreb, f.eks. udnyttelser eller skadelige links, fra at forstyrre medarbejdernes produktivitet og virksomhedens sikkerhed.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 98d23a814ac2af8d9dedc4f163923e67c9ca7dc2
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/20/2022
ms.locfileid: "64973239"
---
# <a name="application-guard-for-office-for-admins"></a>Application Guard til Office for administratorer

**Gælder for:** Word, Excel og PowerPoint til Microsoft 365, Windows 10 Enterprise, Windows 11 Enterprise

Microsoft Defender Application Guard til Office (Application Guard for Office) hjælper med at forhindre, at filer, der ikke er tillid til, får adgang til ressourcer, der er tillid til, og holder din virksomhed sikker mod nye og nye angreb. I denne artikel gennemgås det, hvordan administratorer konfigurerer enheder til en prøveversion af Application Guard til Office. Den indeholder oplysninger om systemkrav og installationstrin for at aktivere Application Guard for Office på en enhed.

## <a name="prerequisites"></a>Forudsætninger

### <a name="minimum-hardware-requirements"></a>Minimumkrav til hardware

* **CPU**: 64-bit, 4 kerner (fysisk eller virtuel), virtualiseringsudvidelser (Intel VT-x ELLER AMD-V), Core i5 tilsvarende eller højere anbefales
* **Fysisk hukommelse**: 8 GB RAM
* **Harddisk**: 10 GB ledig plads på systemdrevet (SSD anbefales)

### <a name="minimum-software-requirements"></a>Minimumkrav til software

* **Windows**: Windows 10 Enterprise udgave, Client Build version 2004 (20H1) build 19041 eller nyere. Alle versioner af Windows 11 understøttes.
* **Office**: Office Current Channel og Monthly Enterprise Channel, Build version 2011 16.0.13530.10000 eller nyere. Office Semi-Annual Enterprise Channel, Build version 2108 eller nyere. Både 32-bit og 64-bit versioner af Office understøttes.
* **Opdateringspakke**: Windows 10 kumulative månedlige sikkerhedsopdatering [KB4571756](https://support.microsoft.com/help/4571756/windows-10-update-KB4571756)

Du kan finde detaljerede systemkrav i [Systemkrav til Microsoft Defender Application Guard](/windows/security/threat-protection/microsoft-defender-application-guard/reqs-md-app-guard). Se også computerproducentens vejledninger i, hvordan du aktiverer virtualiseringsteknologi.
Hvis du vil vide mere om Office opdatere kanaler, skal du se [Oversigt over opdateringskanaler til Microsoft 365](/deployoffice/overview-update-channels).

### <a name="licensing-requirements"></a>Licenskrav

* Microsoft 365 E5 eller Microsoft 365 E5 Sikkerhed

> [!NOTE]
> Microsoft 365 Apps for enterprise med delt computeraktivering eller enhedsbaserede licenser har ikke adgang til Application Guard for Office.

## <a name="deploy-application-guard-for-office"></a>Installer Application Guard for Office

### <a name="enable-application-guard-for-office"></a>Aktivér Application Guard for Office

1. Download og installér **Windows 10 kumulative månedlige sikkerhedsopdateringer KB4571756**.

2. Vælg **Microsoft Defender Application Guard** under Windows Funktioner, og vælg **OK**. Hvis du aktiverer funktionen Application Guard, bliver systemet genstartet. Du kan vælge at genstarte nu eller efter trin 3.

   :::image type="content" source="../../media/ag03-deploy.png" alt-text="Dialogboksen Windows funktioner, der viser AG" lightbox="../../media/ag03-deploy.png":::

   Funktionen kan også aktiveres ved at køre følgende PowerShell-kommando som administrator:

   ```powershell
   Enable-WindowsOptionalFeature -online -FeatureName Windows-Defender-ApplicationGuard
   ```

3. Søg efter **Microsoft Defender Application Guard i administreret tilstand**, en gruppepolitik i **ComputerkonfigurationAdministrative\\ skabeloner\\ Windows Komponenter\\ Microsoft Defender Application Guard**. Aktivér denne politik ved at angive værdien under Indstillinger som **2** eller **3**, og vælg derefter **OK** eller **Anvend**.

   :::image type="content" source="../../media/ag04-deploy.png" alt-text="Muligheden for at aktivere ag i administreret tilstand" lightbox="../../media/ag04-deploy.png":::

   Du kan i stedet angive den tilsvarende politik for udbydere af delte tjenester:

   > OMA-URI: **./Device/Vendor/MSFT/WindowsDefenderApplicationGuard/Indstillinger/AllowWindowsDefenderApplicationGuard** <br> Datatype: **Heltal** <br> Værdi: **2**

4. Genstart systemet.

### <a name="set-diagnostics--feedback-to-send-full-data"></a>Angiv Diagnosticering & feedback for at sende komplette data

> [!NOTE]
> Dette er ikke påkrævet, men konfiguration af valgfri diagnosticeringsdata hjælper med at diagnosticere rapporterede problemer.

Dette trin sikrer, at de data, der er nødvendige for at identificere og løse problemer, når Microsoft. Følg disse trin for at aktivere diagnosticering på din Windows enhed:

1. Åbn **Indstillinger** fra menuen Start.

   :::image type="content" source="../../media/ag05-diagnostic.png" alt-text="Menuen Start" lightbox="../../media/ag05-diagnostic.png":::

2. Vælg **Beskyttelse af personlige oplysninger** **på Windows Indstillinger**.

   :::image type="content" source="../../media/ag06-diagnostic.png" alt-text="Menuen Windows Indstillinger" lightbox="../../media/ag06-diagnostic.png":::

3. Under Beskyttelse af personlige oplysninger skal du vælge **Diagnosticering & feedback** og vælge **Valgfri diagnosticeringsdata**.

   :::image type="content" source="../../media/ag07a-diagnostic.png" alt-text="Menuen Diagnosticering og feedback" lightbox="../../media/ag07a-diagnostic.png":::

Du kan finde flere oplysninger om konfiguration af Windows diagnosticeringsindstillinger under [Konfiguration af Windows diagnosticeringsdata i din organisation](/windows/privacy/configure-windows-diagnostic-data-in-your-organization#enterprise-management).

### <a name="confirm-that-application-guard-for-office-is-enabled-and-working"></a>Bekræft, at Application Guard for Office er aktiveret og fungerer

Før du bekræfter, at Application Guard for Office er aktiveret, skal du starte Word, Excel eller PowerPoint på en enhed, hvor politikkerne er blevet installeret. Kontrollér, at Office er aktiveret. Du skal muligvis bruge din arbejdsidentitet for at aktivere Office produkt først.

Hvis du vil bekræfte, at Application Guard for Office er aktiveret, skal du starte Word, Excel eller PowerPoint og derefter åbne et dokument, der ikke er tillid til. Du kan f.eks. åbne et dokument, der er downloadet fra internettet, eller en vedhæftet fil i en mail fra en person uden for din organisation.

Når du åbner en fil, der ikke er tillid til, første gang, får du muligvis vist et Office velkomstbillede som i følgende eksempel. Den kan blive vist i et stykke tid, mens Application Guard for Office aktiveres, og filen åbnes. Efterfølgende åbninger af filer, der ikke er tillid til, bør være hurtigere.

:::image type="content" source="../../media/ag08-confirm.png" alt-text="Den Office-app velkomstside" lightbox="../../media/ag08-confirm.png":::

Ved åbning bør filen vise et par visuelle indikatorer, som filen blev åbnet i Application Guard for Office:

* En billedforklaring på båndet

  :::image type="content" source="../../media/ag09-confirm.png" alt-text="Doc-filen, der viser en lille App Guard-note" lightbox="../../media/ag09-confirm.png":::

* Programikonet med et skjold på proceslinjen

  ![Ikon på proceslinjen.](../../media/ag12-limitations.png)

## <a name="configure-application-guard-for-office"></a>Konfigurer Application Guard til Office

Office understøtter følgende politikker, så du kan konfigurere funktionerne i Application Guard for Office. Disse politikker kan konfigureres via gruppepolitikker eller via [tjenesten Office cloudpolitik](/DeployOffice/overview-office-cloud-policy-service).

> [!NOTE]
> Konfiguration af disse politikker kan deaktivere nogle funktioner for filer, der er åbnet i Application Guard for Office.

|Politik|Beskrivelse|
|---|---|
|Brug ikke Application Guard til Office|Aktivering af denne politik tvinger Word, Excel og PowerPoint til at bruge isolationsobjektbeholderen Beskyttet visning i stedet for Application Guard til Office. Denne politik kan bruges til midlertidigt at deaktivere Application Guard for Office, når der er problemer med at lade den være aktiveret for Microsoft Edge.|
|Konfigurer Application Guard til forudoprettelse af Office objektbeholder|Denne politik bestemmer, om Application Guard for Office objektbeholder til isolering af filer, der ikke er tillid til, er oprettet på forhånd for at forbedre ydeevnen på kørselstidspunktet. Hvis du aktiverer denne indstilling, kan du angive det antal dage, der skal fortsætte med at oprette en objektbeholder på forhånd, eller lade Office indbyggede heuristiske præ-oprette objektbeholderen.
|Tillad ikke kopiering/indsættelse for Office dokumenter, der er åbnet i Application Guard til Office|Aktivering af denne politik forhindrer en bruger i at kopiere og indsætte indhold fra et dokument, der er åbnet i Application Guard for Office til et dokument, der er åbnet uden for den.|
|Deaktiver hardwareacceleration i Application Guard for Office|Denne politik styrer, om Application Guard til Office bruger hardwareacceleration til at gengive grafik. Hvis du aktiverer denne indstilling, bruger Application Guard til Office softwarebaseret (CPU)-gengivelse og indlæser ikke nogen grafikdrivere fra tredjepart eller interagerer med tilsluttet grafikhardware.
|Deaktiver beskyttelse af ikke-understøttede filtyper i Application Guard for Office|Denne politik styrer, om Application Guard for Office blokerer for åbning af ikke-understøttede filtyper, eller om omdirigering til beskyttet visning aktiveres.
|Slå kamera- og mikrofonadgang fra for dokumenter, der er åbnet i Application Guard til Office|Aktivering af denne politik fjerner Office adgang til kameraet og mikrofonen i Application Guard til Office.|
|Begræns udskrivning fra dokumenter, der er åbnet i Application Guard til Office|Aktivering af denne politik begrænser de printere, som en bruger kan udskrive til, fra en fil, der er åbnet i Application Guard for Office. Du kan f.eks. bruge denne politik til at begrænse brugerne til kun at udskrive til PDF.|
|Undgå, at brugere fjerner Application Guard til Office beskyttelse af filer|Hvis du aktiverer denne politik, fjernes indstillingen (i Office programoplevelse) for at deaktivere Application Guard for Office beskyttelse eller for at åbne en fil uden for Application Guard for Office. <p> **Bemærk:** Brugerne kan stadig tilsidesætte denne politik ved manuelt at fjerne egenskaben Mark-of-the-web fra filen eller ved at flytte et dokument til en placering, der er tillid til.|

> [!NOTE]
> Følgende politikker kræver, at brugeren logger af og logger på igen for at Windows træder i kraft:
>
> * Deaktiver kopiering/indsættelse for dokumenter, der er åbnet i Application Guard for Office
> * Begræns udskrivning af dokumenter, der er åbnet i Application Guard til Office
> * Slå kamera- og mikrofonadgang til dokumenter, der er åbnet i Application Guard, fra for Office

## <a name="submit-feedback"></a>Send feedback

### <a name="submit-feedback-via-feedback-hub"></a>Indsend feedback via Feedback Hub

Hvis du støder på problemer, når du starter Application Guard for Office, opfordres du til at indsende din feedback via Feedback Hub:

1. Åbn **appen Feedback Hub,** og log på.

2. Hvis du får vist en fejldialogboks, mens du starter Application Guard, skal du vælge **Rapportér til Microsoft** i fejldialogboksen for at starte en ny indsendelse af feedback. Ellers skal du navigere til <https://aka.ms/mdagoffice-fb> for at vælge den korrekte kategori for Application Guard og derefter vælge **+&nbsp;Tilføj ny feedback** øverst til højre.

3. Angiv en oversigt i feltet **Opsummer din feedback** , hvis den ikke allerede er udfyldt for dig.

4. Angiv en detaljeret beskrivelse af det problem, du oplevede, og hvilke trin du har udført i feltet **Forklar mere detaljeret** , og vælg derefter **Næste**.

5. Vælg boblen ud for **Problem**. Sørg for, at den valgte kategori er **Sikkerhed og Beskyttelse af personlige oplysninger \> Microsoft Defender Application Guard – Office**, og vælg derefter **Næste**.

6. Vælg **Ny feedback** og derefter **Næste**.

7. Indsaml sporinger om problemet:

   1. Udvid feltet **Genopret mit problem** .

   2. Hvis det problem, du oplever, opstår, mens Application Guard kører, skal du åbne en Application Guard-forekomst. Åbning af en forekomst gør det muligt at indsamle yderligere sporinger fra Application Guard-objektbeholderen.

   3. Vælg **Start optagelse**, og vent på, at feltet stopper med at rotere, og sig *Stop optagelse*.

   4. Genskab problemet med Application Guard fuldt ud. Gengivelse kan omfatte forsøg på at starte en Application Guard-forekomst og vente, indtil det mislykkes, eller genskabe et problem i en kørende Application Guard-forekomst.

   5. Vælg feltet **Stop optagelse** .

   6. Hold alle kørende Application Guard-instanser åbne, selv i et par minutter efter indsendelsen, så der også kan indsamles objektbeholderdiagnosticering.

8. Vedhæft relevante skærmbilleder eller filer, der er relateret til problemet.

9. Vælg **Send**.

### <a name="submit-feedback-via-office-customer-voice"></a>Indsend feedback via Office Customer Voice

Du kan også sende feedback fra Office hvis problemet opstår, når Office dokumenter åbnes i Application Guard. Se [Office Insider Handbook](https://insider.office.com/handbook) for at få feedback.

## <a name="integration-with-microsoft-defender-for-endpoint-and-microsoft-defender-for-office-365"></a>Integration med Microsoft Defender for Endpoint og Microsoft Defender for Office 365

Application Guard for Office er integreret med Microsoft Defender for Endpoint til at levere overvågning og advarsler om ondsindet aktivitet, der sker i det isolerede miljø.

[Pengeskab dokumenter i Microsoft E365 E5](/microsoft-365/security/office-365-security/safe-docs) er en funktion, der bruger Microsoft Defender for Endpoint til at scanne dokumenter, der er åbnet i Application Guard, for Office. For at få et ekstra beskyttelseslag kan brugerne ikke forlade Application Guard til Office, før resultaterne af scanningen er blevet fastlagt.

Microsoft Defender for Endpoint er en sikkerhedsplatform, der er udviklet til at hjælpe virksomhedsnetværk med at forhindre, registrere, undersøge og reagere på avancerede trusler. Du kan finde flere oplysninger om denne platform [under Microsoft Defender for Endpoint](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp). Hvis du vil vide mere om onboarding af enheder til denne platform, skal du se [Onboard enheder til Microsoft Defender for Endpoint-tjenesten](/windows/security/threat-protection/microsoft-defender-atp/onboard-configure).

Du kan også konfigurere Microsoft Defender for Office 365 til at arbejde med Defender for Endpoint. Du kan finde flere oplysninger under [Integrer Defender for Office 365 med Microsoft Defender for Endpoint](integrate-office-365-ti-with-mde.md).

## <a name="limitations-and-considerations"></a>Begrænsninger og overvejelser

* Application Guard for Office er en beskyttet tilstand, der isolerer dokumenter, der ikke er tillid til, så de ikke kan få adgang til virksomhedens ressourcer, et intranet, brugerens identitet og vilkårlige filer på computeren. Hvis en bruger forsøger at få adgang til en funktion, der er afhængig af en sådan adgang, f.eks. at indsætte et billede fra en lokal fil på disken, mislykkes adgangen, og der oprettes en prompt, der ligner følgende eksempel. Hvis du vil aktivere et dokument, der ikke er tillid til, for at få adgang til ressourcer, der er tillid til, skal brugerne fjerne Application Guard-beskyttelse fra dokumentet.

  :::image type="content" source="../../media/ag09-confirm.png" alt-text="Dialogboksen, der angiver sikkerhedsmeddelelsen og funktionsstatussen" lightbox="../../media/ag09-confirm.png":::

  > [!NOTE]
  > Råder brugerne til kun at fjerne beskyttelsen, hvis de har tillid til filen og dens kilde, eller hvor den kom fra.

* Når et dokument, der ikke er tillid til, gemmes på et sted, der er tillid til, nedarves tillid fra placeringen af dokumentet. En organisations cloudlager identificeres typisk som et sted, der er tillid til.

* Aktivt indhold i dokumenter, f.eks. makroer og ActiveX kontrolelementer, er deaktiveret i Application Guard for Office. Brugerne skal fjerne Application Guard-beskyttelse for at aktivere aktivt indhold.

* Filer, der ikke er tillid til, fra netværksshares eller filer, der deles fra OneDrive, OneDrive for Business eller SharePoint Online fra en anden organisation, åbnes som skrivebeskyttet i Application Guard. Brugerne kan gemme en lokal kopi af disse filer for at fortsætte med at arbejde i objektbeholderen eller fjerne beskyttelsen for at arbejde direkte med den oprindelige fil.

* Filer, der er beskyttet af IRM (Information Rights Management), blokeres som standard. Hvis brugerne vil åbne disse filer i beskyttet visning, skal en administrator konfigurere politikindstillinger for ikke-understøttede filtyper for organisationen.

* Tilpasninger af Office programmer i Application Guard til Office bevares ikke, når en bruger logger af og logger på igen, eller når enheden genstartes.

* Kun tilgængelighedsværktøjer, der bruger UIA-strukturen, kan give en tilgængelig oplevelse for filer, der er åbnet i Application Guard for Office.

* Der kræves netværksforbindelse til den første start af Application Guard efter installationen. Der kræves forbindelse, for at Application Guard kan validere licensen.

* I afsnittet med oplysninger i dokumentet kan egenskaben *Senest ændret af* vise **WDAGUtilityAccount** som brugeren. WDAGUtilityAccount er den anonyme bruger, der er konfigureret i Application Guard. Desktopbrugerens identitet deles ikke i Application Guard-objektbeholderen.

## <a name="performance-optimizations-for-application-guard-for-office"></a>Optimering af ydeevnen for Application Guard til Office

Dette afsnit indeholder en oversigt over de optimeringer af ydeevnen, der bruges i Application Guard til Office. Disse oplysninger kan hjælpe administratorer med at diagnosticere rapporter fra brugere, der er relateret til ydeevnen af Office eller det overordnede system, når Application Guard er aktiveret.

Application Guard bruger en virtualiseret objektbeholder til at isolere dokumenter, der ikke er tillid til, væk fra systemet. Processen med at oprette en objektbeholder og konfigurere Application Guard-objektbeholderen til at åbne Office dokumenter har en belastning på ydeevnen, der kan påvirke brugeroplevelsen negativt, når brugerne åbner et dokument, der ikke er tillid til.

For at give brugerne den forventede filåbningsoplevelse bruger Application Guard logik til at oprette en objektbeholder på forhånd, når følgende heuristik er opfyldt på et system: En bruger har åbnet en fil i enten Beskyttet visning eller Application Guard inden for de seneste 28 dage.

Når denne heuristik er opfyldt, opretter Office en Application Guard-objektbeholder for brugeren, når brugeren logger på Windows. Mens denne handling på forhånd er i gang, kan systemet opleve langsom ydeevne, men effekten vil blive løst, så snart handlingen er fuldført.

> [!NOTE]
> De tip, der er nødvendige, for at heuristiken kan oprette objektbeholderen på forhånd, genereres af Office programmer, når en bruger bruger bruger dem. Hvis en bruger installerer Office på et nyt system, hvor Application Guard er aktiveret, opretter Office ikke objektbeholderen på forhånd, før efter første gang en bruger åbner et dokument, der ikke er tillid til, på systemet. Brugeren vil bemærke, at det tager længere tid at åbne denne første fil i Application Guard.

## <a name="known-issues"></a>Kendte problemer

* Hvis du vælger weblinks (`http` eller `https`), åbnes browseren ikke.
* Standardindstillingen for beskyttelsespolitikken kopiér og sæt ind er kun at give udklipsholder adgang til tekst.
* Standardindstillingen for beskyttelsespolitikken for ikke-understøttede filtyper er at blokere åbning af ikke-understøttede filtyper, der ikke er tillid til, og som er krypteret, eller hvor IRM (Information Rights Management) er angivet. Dette omfatter filer, der krypteres ved hjælp af følsomhedsmærkater fra Microsoft Purview Information Protection.
* CSV- og HTML-filer understøttes ikke i øjeblikket.
* Application Guard til Office fungerer i øjeblikket ikke sammen med NTFS-komprimerede diskenheder. Hvis du får vist fejlmeddelelsen "ERROR_VIRTUAL_DISK_LIMITATION", skal du prøve at dekomprimere diskenheden.
* Opdateringer til .NET kan medføre, at filer ikke åbnes i Application Guard. Som en løsning kan brugerne genstarte deres enhed, når de støder på denne fejl. Få mere at vide om problemet ved [at modtage en fejlmeddelelse, når du forsøger at åbne Windows Defender Application Guard eller Windows Sandkasse](https://support.microsoft.com/help/4575917/receiving-an-error-message-when-attempting-to-open-windows-defender-ap).
* Se [Ofte stillede spørgsmål – Microsoft Defender Application Guard for at få flere oplysninger.](/windows/security/threat-protection/microsoft-defender-application-guard/faq-md-app-guard)
