---
title: Administrere aktivt indhold i Office for IT-administratorer
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: Admin
ms.topic: tutorial
ms.localizationpriority: medium
ms.prod: m365-security
ms.collection:
- M365-security-compliance
search.appverid:
- MET150
ROBOTS: NOINDEX,NOFOLOW
description: Administratorer kan få mere at vide om, hvordan du opretter politikker for at blokere aktivt indhold Office dokumenter
ms.openlocfilehash: 33d53ab14fec1b6cd16b8de95befe8bc8a898e16
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64468915"
---
# <a name="manage-active-content-in-office-documents"></a>Administrere aktivt indhold i Office dokumenter

> [!NOTE]
> De funktioner, der er beskrevet i denne artikel, findes i Forhåndsvisning, er ikke tilgængelige for alle og kan ændres uden forbehold.

Office dokumenter kan automatisk opdateres, opdateres eller udføres, når de indeholder _aktivt indhold_. Eksempler på aktivt indhold er makroer, ActiveX kontrolelementer og Office-tilføjelsesprogrammet. Aktivt indhold kan levere effektive og nyttige funktioner til brugere, men hackere kan også bruge aktivt indhold til at levere malware.

Administratorer kan oprette organisationspolitikker (gruppepolitikker eller skypolitikker), der begrænser brugen af aktivt indhold til bestemte sæt af brugere eller til helt at deaktivere aktivt indhold. Brugerne kan konfigurere deres egne indstillinger for sikkerhed og beskyttelse af personlige oplysninger Office Sikkerhedscenter i deres Office apps  i **Sikkerhedscenter** \> \> **til filindstillinger**.

Tidligere, når brugerne identificerede dokumenter som dokumenter, der er tillid til, ville deres valg tillade kørsel af aktivt indhold, også selvom en administrator konfigurerede politikker til at blokere aktivt indhold Office dokumenter. Politikker, der er angivet af administratorer, tilsidesætter nu brugeridentifikationen af dokumenter, der er tillid til. Denne ændring kan medføre problemer for brugerne.

Den opdaterede sikkerhedscenterlogik er beskrevet i følgende diagram:

:::image type="content" source="../media/office-trust-center-flow.png" alt-text="Et rutediagram, der beskriver Sikkerhedscenterlogik i Microsoft 365 Defender portal" lightbox="../media/office-trust-center-flow.png":::

1. En bruger åbner et Office, der indeholder aktivt indhold.

2. Hvis dokumentet kommer fra en placering, der er tillid til, åbnes dokumentet med det aktive indhold aktiveret. Hvis dokumentet ikke kommer fra en placering, der er tillid til, fortsætter evalueringen.

3. Det er her, den opdaterede funktionsmåde træder i kraft:
   - Tidligere ville den næste evaluerede indstilling have været, hvis brugeren havde identificeret dette dokument som et dokument, der er tillid til. Hvis det var gjort, blev dokumentet åbnet med det aktive indhold aktiveret.
   - Om brugeren har identificeret dokumentet som et dokument, der er tillid til, behandles nu ikke her (nu på trin 8).

     Den grundlæggende ændring i funktionsmåden er beskrevet på følgende måde: Skypolitikker (trin 4), gruppepolitikker (trin 6) og lokale indstillinger (trin 7) kontrolleres,  før brugerangivelsen af et dokument, der er tillid til, overhovedet tages i betragtning. Hvis nogen af disse trin blokerer adgangen til det aktive indhold, og ingen af trinnene tillader brugertilsidesættelse, er brugeridentifikation af dokumentet som et dokument, der er tillid til, irrelevant.

4. Skypolitikker kontrolleres for at se, om denne type aktivt indhold er tilladt eller blokeret. Hvis det aktive indhold ikke blokeres, fortsætter evalueringen til trin 6.

   Hvis det aktive indhold blokeres af politik, er oplevelsen beskrevet i trin 5.

5. Åbning af dokumentet blokeres med en meddelelse på linjen Tillid. Hvad der herefter sker, styres af brugeren, der tilsidesætter indstillingerne i politikken: a. **Brugertilsidesættelse er** ikke tilladt: Brugeren kan ikke åbne dokumentet, og evalueringen stopper.
   b. **Brugertilsidesættelse** tilladt: Brugeren kan klikke på linket i an trustlinjen for at åbne dokumentet med det aktive indhold aktiveret.

6. Gruppepolitikker kontrolleres for at se, om denne type aktivt indhold er tilladt eller blokeret. Hvis det aktive indhold ikke blokeres, fortsætter evalueringen til trin 7.

   Hvis det aktive indhold blokeres af politik, er oplevelsen beskrevet i trin 5.

7. Lokale indstillinger kontrolleres for at se, om denne type aktivt indhold er tilladt eller blokeret. Hvis det aktive indhold blokeres, blokeres åbning af dokumentet med en meddelelse på linjen om tillid. Hvis det aktive indhold ikke blokeres, fortsætter evalueringen.

8. Hvis brugeren tidligere har identificeret dokumentet som et dokument, der er tillid til, åbnes dokumentet med det aktive indhold aktiveret. Hvis ikke, blokeres åbning af dokumentet.

## <a name="what-is-a-trusted-document"></a>Hvad er et dokument, der er tillid til?

Dokumenter, der er Office, som åbnes uden sikkerhedsprompter for makroer, ActiveX kontrolelementer og andre typer aktivt indhold i dokumentet. Beskyttet visning eller Application Guard bruges ikke til at åbne dokumentet. Når brugerne åbner et dokument, der er tillid til, og alt aktivt indhold aktiveres. Selvom dokumentet indeholder nyt aktivt indhold eller opdateringer til eksisterende aktivt indhold, modtager brugerne ikke sikkerhedsmeddelelser, næste gang de åbner dokumentet.

På grund af denne funktionsmåde skal brugerne kun have klart tillid til dokumenter, hvis de har tillid til dokumentkilden.

Hvis en administrator blokerer aktivt indhold ved hjælp af en politik, eller hvis brugerne angiver en indstilling for Center for sikkerhed og rettigheder, der blokerer aktivt indhold, forbliver det aktive indhold blokeret.

Du kan finde flere oplysninger i følgende artikler:

- [Dokumenter, der er tillid til](https://support.microsoft.com/topic/trusted-documents-cf872bd8-47ec-4c02-baa5-1fdba1a11b53)
- [Tilføje, fjerne eller ændre en placering, der er tillid til](https://support.microsoft.com/topic/add-remove-or-change-a-trusted-location-7ee1cdc2-483e-4cbb-bcb3-4e7c67147fb4)
- [Aktive indholdstyper i dine filer](https://support.microsoft.com/topic/active-content-types-in-your-files-b7ff2e8a-4055-47d4-8c7d-541e19f62bea)

## <a name="configure-trusted-document-settings-in-office-policies"></a>Konfigurere dokumentindstillinger, der er tillid til Office politikker

Administratorer har mange måder at konfigurere Office i en organisation. Eksempel:

- **Office skybaseret** politiktjeneste: Konfigurer en brugerbaseret politik, der gælder for en bruger på alle enheder, der får adgang til filer i Office-apps med deres Azure AD-konto. Se trinnene til at [oprette Office politikkonfiguration i skyen](/DeployOffice/overview-office-cloud-policy-service) i [Office skypolitiktjeneste](https://config.office.com/officeSettings/officePolicies).
- **Office** politikker i Intune: Brug kataloget Intune Indstillinger eller administrative skabeloner til at udrulle HKCU-politikker på Windows 10-pc'er: I [MEM Administration](https://endpoint.microsoft.com/#blade/Microsoft_Intune_DeviceSettings/DevicesMenu/configurationProfiles) under **Enhedskonfigurationsprofiler** \> **.**
  - ***Administrative skabeloner***: Se vejledningen i at bruge Windows 10 til at konfigurere [administrative skabeloner](/mem/intune/configuration/administrative-templates-windows).
  - ***Indstillinger (eksempel)***: Se vejledningen for at bruge [kataloget Indstillinger (forhåndsvisning)](/mem/intune/configuration/settings-catalog).
- **Gruppepolitik**: Brug dit lokale Active Directory til at udrulle gruppepolitikobjekter (GPOs) til brugere og computere. Hvis du vil oprette et gruppepolitikobjekt til denne indstilling, skal du downloade de seneste administrative skabelonfiler [(ADMX/ADML) og Office-tilpasningsværktøjet til Microsoft 365 Apps for enterprise, Office 2019 og Office 2016](https://www.microsoft.com/download/details.aspx?id=49030).

## <a name="known-issues"></a>Kendte problemer

- Når **politik-VBA-makromeddelelser** (Access, PowerPoint, Visio, Word) eller makromeddelelser **(Excel**) er indstillet til værdien Deaktiver alle undtagen **digitalt** signerede makroer, vises den forventede statuslinje ikke, og Sikkerhedsoplysninger i Backstage viser ikke  oplysninger om blokerede makroer, selvom indstillingen fungerer som forventet. Teamet Office at løse problemet.

## <a name="admin-options-for-restricting-active-content"></a>Administratorindstillinger til begrænsning af aktivt indhold

Der er en stor forskel på tillidsniveauet i internt oprettet indhold vs. indhold, som brugere downloader fra internettet. Overvej at tillade aktivt indhold i interne dokumenter og globalt ikke tillade aktivt indhold i dokumenter fra internettet.

Hvis brugerne ikke har brug for bestemte typer aktivt indhold, er den mest sikre mulighed at bruge politikker til at deaktivere brugeradgang til det aktive indhold og tillade undtagelser efter behov.

Følgende politikker er tilgængelige:

- **Deaktivere Placeringer, der er tillid til**: Undtagelser for grupper, der er tilgængelige.
- **Deaktivere Dokumenter, der er tillid til**: Undtagelser for grupper, der er tilgængelige.
- **Deaktivere alt aktivt indhold**: Undtagelser for enkeltpersoner.

Tabellerne i følgende afsnit beskriver de indstillinger, der styrer aktivt indhold. Hvis disse politikker anvendes på brugere, håndhæves de i dokumenter, der er tillid til, og den tidligere slutbrugeroplevelse vil muligvis ikke være den samme. Tabellerne indeholder også den anbefalede indstilling for sikkerheds oprindelige planer og identificerer andre indstillinger, hvor brugeren beder om at tilsidesætte er tilgængelig (hvilket gør det muligt for brugeren at aktivere det aktive indhold).

### <a name="hkey_current_user-settings"></a>HKEY_CURRENT_USER indstillinger

<p>

****
|Kategori|App|Politiknavn|Grundlinje for sikkerhed<br>indstilling (anbefales)|Indstilling med brugerprompt<br>og tilsidesætte tilgængelig?|
|---|---|---|---|---|
|ActiveX|Office|ActiveX initialisering af kontrolelement|**6**|**Ja** for følgende værdier: <ul><li>**3**</li><li>**4**</li><li>**5**</li><li>**6**</li></ul>|
|ActiveX|Office|Tillad Active X One Off-formularer|**Indlæse kun Outlook kontrolelementer**|Nej|
|ActiveX|Office|Kontrollere ActiveX objekter|Ikke en indstilling for grundlinje for sikkerhed.|Nej|
|ActiveX|Office|Deaktivere alle ActiveX|Ikke en indstilling for grundlinje for sikkerhed.|**Ja** for følgende værdier: <ul><li>**Deaktiveret**</li><li>**Ikke konfigureret**</li></ul>|
|ActiveX|Office|Indlæse kontrolelementer i Forms3|**1**|**Ja** for følgende værdier: <ul><li>**2**</li><li>**3**</li></ul>|
|Tilføjelses- & Mulighed for udvidelse|Excel <p> PowerPoint <p> Project <p> Publisher <p> Visio <p> Word|Deaktiver meddelelse i linjen, der er tillid til for usignerede tilføjelsesprogram, og bloker dem|**Aktiveret**|**Ja** for værdien **Deaktiveret**.|
|Tilføjelses- & Mulighed for udvidelse|Excel <p> PowerPoint <p> Project <p> Publisher <p> Visio <p> Word|Kræv, at tilføjelsesprogrammet er signeret af pålidelige Publisher|**Aktiveret**|Nej|
|Tilføjelses- & Mulighed for udvidelse|Excel|Vis ikke advarsel om genudgiv automatisk|**Deaktiveret**|Nej|
|Tilføjelses- & Mulighed for udvidelse|Excel|Meddelelse om funktionen WEBSERVICE Indstillinger|**Deaktiver alle med meddelelse**|**Ja** for følgende værdier: <ul><li>**Deaktiver alle med meddelelse**</li><li>**Deaktiveret**</li><li>**Ikke konfigureret**</li></ul>|
|Tilføjelses- & Mulighed for udvidelse|Office|Deaktiver Office i at forespørge på serveren SharePoint for publicerede links|**Deaktiveret**|Nej|
|Tilføjelses- & Mulighed for udvidelse|Office|Deaktiver brugergrænsefladen ud fra dokumenter og skabeloner|Ikke tillade i Word = Sand <p> Ikke tillade i Project = Falsk <p> Er du ikke til Excel = Sand <p> Ikke tillade i Visio = False <p> Er du ikke til PowerPoint = Sand <p> Ikke tillade i Access = Sand <p> Er du ikke til Outlook = Sand <p> Ikke tillade i Publisher = Sand <p> Ikke tillade i InfoPath = Sand|Nej|
|Tilføjelses- & Mulighed for udvidelse|Outlook|Konfigurere en Outlook objektmodelprompt, når du åbner et adressekartotek|**Afvisning automatisk**|**Ja** for følgende værdier: <ul><li>**Spørg brugeren**</li><li>**Promptbruger baseret på computersikkerhed**</li><li>**Deaktiveret**</li><li>**Ikke konfigureret**</li></ul>|
|Tilføjelses- & Mulighed for udvidelse|Outlook|Konfigurere Outlook om objektmodel Ved åbning af egenskaben Formel for et UserProperty-objekt|**Afvisning automatisk**|**Ja** for følgende værdier: <ul><li>**Spørg brugeren**</li><li>**Promptbruger baseret på computersikkerhed**</li><li>**Deaktiveret**</li><li>**Ikke konfigureret**</li></ul>|
|Tilføjelses- & Mulighed for udvidelse|Outlook|Konfigurere en Outlook objektmodelprompt, når du udfører Gem som|**Afvisning automatisk**|**Ja** for følgende værdier: <ul><li>**Spørg brugeren**</li><li>**Promptbruger baseret på computersikkerhed**</li><li>**Deaktiveret**</li><li>**Ikke konfigureret**</li></ul>|
|Tilføjelses- & Mulighed for udvidelse|Outlook|Konfigurere en Outlook objektmodelprompt, når du læser adresseoplysninger|**Afvisning automatisk**|**Ja** for følgende værdier: <ul><li>**Spørg brugeren**</li><li>**Promptbruger baseret på computersikkerhed**</li><li>**Deaktiveret**</li><li>**Ikke konfigureret**</li></ul>|
|Tilføjelses- & Mulighed for udvidelse|Outlook|Konfigurere en Outlook objektmodelprompt, når du besvarer møde- og opgaveanmodninger|**Afvisning automatisk**|**Ja** for følgende værdier: <ul><li>**Spørg brugeren**</li><li>**Promptbruger baseret på computersikkerhed**</li><li>**Deaktiveret**</li><li>**Ikke konfigureret**</li></ul>|
|Tilføjelses- & Mulighed for udvidelse|Outlook|Konfigurere en Outlook objektmodelprompt, når du sender mail|**Afvisning automatisk**|**Ja** for følgende værdier: <ul><li>**Spørg brugeren**</li><li>**Promptbruger baseret på computersikkerhed**</li><li>**Deaktiveret**</li><li>**Ikke konfigureret**</li></ul>|
|Tilføjelses- & Mulighed for udvidelse|Outlook|Angiv Outlook brugerdefinerede handlinger for eksekveringsanmodning|**Afvisning automatisk**|**Ja** for følgende værdier: <ul><li>**Spørg brugeren**</li><li>**Promptbruger baseret på computersikkerhed**</li><li>**Deaktiveret**</li><li>**Ikke konfigureret**</li></ul>|
|Tilføjelses- & Mulighed for udvidelse|PowerPoint|Kør programmer|**deaktiver (kør ikke nogen programmer)**|**Ja** for værdien **Aktivér (spørg brugeren, før den kører)**|
|Tilføjelses- & Mulighed for udvidelse|Word <p> Excel|Deaktivere smart document's brug af manifester|**Aktiveret**|Nej|
|DDE|Excel|Tillad ikke, at Der startes DDE-server (Dynamic Data Exchange) i Excel|**Aktiveret**|**Ja** for værdien **Ikke konfigureret**.|
|DDE|Excel|Tillad ikke opslag på Dynamic Data Exchange-serveren (DDE) Excel|**Aktiveret**|**Ja** for følgende værdier: <ul><li>**Deaktiveret**</li><li>**Ikke konfigureret**</li></ul>|
|DDE|Word|Dynamiske data Exchange|**Deaktiveret**|Nej|
|Jscript & VBScript|Outlook|Tillad scripts i enkelt Outlook formularer|**Deaktiveret**|Nej|
|Jscript & VBScript|Outlook|Tillad ikke kørsel Outlook objektmodelscripts for offentlige mapper|**Aktiveret**|Nej|
|Jscript & VBScript|Outlook|Tillad ikke kørsel Outlook objektmodelscripts for delte mapper|**Aktiveret**|Nej|
|Makroer|Excel|Makrobeskeder|**Deaktivere alle undtagen digitalt signerede makroer**|**Ja** for følgende værdier: <ul><li>**Deaktiveret**</li><li>**Ikke konfigureret**</li></ul>|
|Makroer|Access <p> PowerPoint <p> Project <p> Publisher <p> Visio <p> Word|VBA-makromeddelelse Indstillinger|**Deaktivere alle undtagen digitalt signerede makroer** <p> og <p> **Kræv, at makroer er signeret af en udgiver, der er tillid til**|**Ja** for følgende værdier: <ul><li>**Deaktiveret**</li><li>**Ikke konfigureret**</li></ul>|
|Makroer|Access <p> Excel <p> PowerPoint <p> Visio <p> Word|Bloker makroer i at køre Office filer fra internettet|**Aktiveret**|**Ja** for følgende værdier: <ul><li>**Deaktiveret**</li><li>**Ikke konfigureret**</li></ul>|
|Makroer|Excel|Scan krypterede makroer i Excel Open XML-projektmapper|**Scan krypterede makroer (standard)**|Nej|
|Makroer|Office|Tillad, at VBA indlæser referencer efter sti fra upålidelige intranetplaceringer|**Deaktiveret**|Nej|
|Makroer|Office|Automatiseringssikkerhed|**Brug programmakrosikkerhedsniveau**|Nej|
|Makroer|Office|Deaktivere andre sikkerhedskontroller for VBA-biblioteksreferencer, der kan referere til usikre placeringer på den lokale computer|**Deaktiveret**|Nej|
|Makroer|Office|Scanningsomfang for makrokørsel|**Aktivere for alle dokumenter**|Nej|
|Makroer|Office|Hav kun tillid til VBA-makroer, der bruger V3-signaturer|Ikke en indstilling for grundlinje for sikkerhed.|Nej|
|Makroer|Outlook|Outlook sikkerhedstilstand|**Brug Outlook Security Gruppepolitik**|Påkrævet for at aktivere Outlook indstillingerne for gruppepolitikobjekt. <p> Nævnt som afhængighed (denne politik blokerer ikke selve indholdet).|
|Makroer|Outlook|Sikkerhedsindstilling for makroer|**Advar for signeret, deaktiver usigneret**|**Ja** for følgende værdier: <ul><li>**Advar altid**</li><li>**Advar for signeret, deaktiver usigneret**</li><li>**Deaktiveret**</li><li>**Ikke konfigureret**</li></ul>|
|Makroer|PowerPoint|Scan krypterede makroer i PowerPoint Open XML-præsentationer|**Scan krypterede makroer (standard)**|Nej|
|Makroer|Publisher|Publisher på automatiseringsniveau|**Efter brugergrænseflade (bedt om)**|Nej|
|Makroer|Word|Scan krypterede makroer i Open XML-dokumenter i Word|**Scan krypterede makroer (standard)**|Nej|
|

### <a name="hkey_local_machine-settings"></a>HKEY_LOCAL_MACHINE indstillinger

<p>

****
|Kategori|App|Politiknavn|Grundlinje for sikkerhed<br>indstilling (anbefales)|Indstilling med brugerprompt<br>og tilsidesætte tilgængelig?|
|---|---|---|---|---|
|ActiveX|Office|Begræns ActiveX installation|excel.exe = Sand <p> exprwd.exe = Sand <p> groove.exe = Sand <p> msaccess.exe = Sand <p> mse7.exe = Sand <p> mspub.exe = Sand <p> onent.exe = Sand <p> outlook.exe = Sand <p> powerpnt.exe = Sand <p> pptview.exe = Sand <p> spDesign.exe = Sand <p> visio.exe = Sand <p> winproj.exe = Sand <p> winword.exe = Sand|Nej|
|Tilføjelses- & Mulighed for udvidelse|Office|Administration af tilføjelser|excel.exe = Sand <p> exprwd.exe = Sand <p> groove.exe = Sand <p> msaccess.exe = Sand <p> mse7.exe = Sand <p> mspub.exe = Sand <p> onent.exe = Sand <p> outlook.exe = Sand <p> powerpnt.exe = Sand <p> pptview.exe = Sand <p> spDesign.exe = Sand <p> visio.exe = Sand <p> winproj.exe = Sand <p> winword.exe = Sand|Nej|
|Tilføjelses- & Mulighed for udvidelse|Office|Bloker Flash-aktivering i Office dokumenter|Se Microsofts sikkerhedsvejledning ADMX/ADML-filer for en liste over COM killbits for at blokere al aktivering af Flash Microsoft 365 apps. ADMX-/ADML-filerne til grundlinjer for virksomhedens sikkerhed er tilgængelige i [værktøjspakken til sikkerhedsoverholdelse](https://www.microsoft.com/download/details.aspx?id=55319).|Nej|
|Jscript & VBScript|Office|Begræns ældre JScript udførelse for Office|**Aktiveret**: <p> Access: 69632 <p> Excel: 69632 <p> OneNote: 69632 <p> Outlook: 69632 <p> PowerPoint: 69632 <p> Project: 69632 <p> Publisher: 69632 <p> Visio: 69632 <p> Word: 69632|Nej|
|Jscript & VBScript|Office|Sikkerhedsbegrænsninger i scriptede vinduer|excel.exe = Sand <p> exprwd.exe = Sand <p> groove.exe = Sand <p> msaccess.exe = Sand <p> mse7.exe = Sand <p> mspub.exe = Sand <p> onent.exe = Sand <p> outlook.exe = Sand <p> powerpnt.exe = Sand <p> pptview.exe = Sand <p> spDesign.exe = Sand <p> visio.exe = Sand <p> winproj.exe = Sand <p> winword.exe = Sand|Nej|
|
