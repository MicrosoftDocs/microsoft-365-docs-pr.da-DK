---
title: Administrer aktivt indhold i Office dokumenter for it-administratorer
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
description: Administratorer kan få mere at vide om, hvordan de opretter politikker til blokering af aktivt indhold i Office dokumenter
ms.openlocfilehash: 7a24c56bdd388f2dc9a8f408b52b2de1c6805a0a
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65100935"
---
# <a name="manage-active-content-in-office-documents"></a>Administrer aktivt indhold i Office dokumenter

> [!NOTE]
> De funktioner, der er beskrevet i denne artikel, er i prøveversion, er ikke tilgængelige for alle og kan ændres.

Office dokumenter kan opdateres, opdateres eller udføres automatisk, når de indeholder _aktivt indhold_. Eksempler på aktivt indhold er makroer, ActiveX kontrolelementer og Office tilføjelsesprogrammer. Aktivt indhold kan give brugerne effektive og nyttige funktioner, men personer med ondsindede hensigter kan også bruge aktivt indhold til at levere malware.

Administratorer kan oprette organisationspolitikker (gruppepolitikker eller cloudpolitikker), der begrænser brugen af aktivt indhold til bestemte brugersæt eller udelukkende deaktiverer aktivt indhold. Brugerne kan konfigurere deres egne indstillinger for sikkerhed og beskyttelse af personlige oplysninger i Office Center for sikkerhed og rettighedsadministration i deres Office apps i Center **for sikkerhed og rettighedsadministration for filindstillinger** \>  \>.

Tidligere når brugere identificerede dokumenter som dokumenter, der er tillid til, ville deres valg tillade, at aktivt indhold kunne køre, selvom en administrator konfigurerede politikker til at blokere aktivt indhold i Office dokumenter. Nu har politikker, der er angivet af administratorer, forrang frem for brugeridentifikation af dokumenter, der er tillid til. Denne ændring i funktionsmåden kan medføre problemer for brugerne.

Den opdaterede logik for Center for sikkerhed og rettighedsadministration er beskrevet i følgende diagram:

:::image type="content" source="../media/office-trust-center-flow.png" alt-text="Et rutediagram, der beskriver logikken for Center for sikkerhed og rettighedsadministration på Microsoft 365 Defender-portalen" lightbox="../media/office-trust-center-flow.png":::

1. En bruger åbner et Office dokument, der indeholder aktivt indhold.

2. Hvis dokumentet kommer fra et sted, der er tillid til, åbnes dokumentet med det aktive indhold aktiveret. Hvis dokumentet ikke kommer fra et sted, der er tillid til, fortsætter evalueringen.

3. Det er her, den opdaterede funktionsmåde træder i kraft:
   - Tidligere ville den næste evaluerede indstilling have været, hvis brugeren havde identificeret dette dokument som et dokument, der er tillid til. Hvis de gjorde det, åbnes dokumentet med det aktive indhold aktiveret.
   - Om brugeren har identificeret dokumentet som et dokument, der er tillid til, tages nu ikke i betragtning her (nu på trin 8).

     Den grundlæggende ændring i funktionsmåden er beskrevet på følgende måde: Cloudpolitikker (trin 4), gruppepolitikker (trin 6) og lokale indstillinger (trin 7) kontrolleres _, før_ brugerangivelsen for et dokument, der er tillid til, tages i betragtning. Hvis et af disse trin blokerer adgangen til det aktive indhold, **og** ingen af trinnene tillader bruger tilsidesættelser, er brugeridentifikation af dokumentet som et dokument, der er tillid til, irrelevant.

4. Cloudpolitikker kontrolleres for at se, om denne type aktivt indhold er tilladt eller blokeret. Hvis det aktive indhold ikke er blokeret, fortsætter evalueringen til trin 6.

   Hvis det aktive indhold er blokeret af en politik, er oplevelsen beskrevet i trin 5.

5. Åbningen af dokumentet er blokeret med en meddelelse på tillidslinjen. Det næste, der sker, styres af indstillingerne for tilsidesættelse af brugeren i politikken: a. **Tilsidesættelse af brugeren er ikke tilladt**: Brugeren kan ikke åbne dokumentet, og evalueringen stopper.
   b. **Tilsidesættelse af brugeren er tilladt**: Brugeren kan klikke på linket på tillidspanelet for at åbne dokumentet med det aktive indhold aktiveret.

6. Gruppepolitikker kontrolleres for at se, om denne type aktivt indhold er tilladt eller blokeret. Hvis det aktive indhold ikke er blokeret, fortsætter evalueringen til trin 7.

   Hvis det aktive indhold er blokeret af en politik, er oplevelsen beskrevet i trin 5.

7. Lokale indstillinger kontrolleres for at se, om denne type aktivt indhold er tilladt eller blokeret. Hvis det aktive indhold blokeres, blokeres åbningen af dokumentet med en meddelelse på tillidslinjen. Hvis det aktive indhold ikke er blokeret, fortsætter evalueringen.

8. Hvis brugeren tidligere har identificeret dokumentet som et dokument, der er tillid til, åbnes dokumentet med det aktive indhold aktiveret. Hvis ikke, blokeres åbningen af dokumentet.

## <a name="what-is-a-trusted-document"></a>Hvad er et dokument, der er tillid til?

Dokumenter, der er tillid til, er Office dokumenter, der åbnes uden sikkerhedsprompts for makroer, ActiveX kontrolelementer og andre typer aktivt indhold i dokumentet. Beskyttet visning eller Application Guard bruges ikke til at åbne dokumentet. Når brugerne åbner et dokument, der er tillid til, og alt aktivt indhold er aktiveret. Selvom dokumentet indeholder nyt aktivt indhold eller opdateringer til eksisterende aktivt indhold, modtager brugerne ikke sikkerhedsprompter, næste gang de åbner dokumentet.

På grund af denne funktionsmåde skal brugerne kun have tillid til dokumenter, hvis de har tillid til dokumentkilden.

Hvis en administrator blokerer aktivt indhold ved hjælp af en politik, eller hvis brugerne angiver en indstilling for Center for sikkerhed og rettighedsadministration, der blokerer aktivt indhold, forbliver det aktive indhold blokeret.

Du kan finde flere oplysninger i følgende artikler:

- [Dokumenter, der er tillid til](https://support.microsoft.com/topic/trusted-documents-cf872bd8-47ec-4c02-baa5-1fdba1a11b53)
- [Tilføje, fjerne eller ændre et sted, der er tillid til](https://support.microsoft.com/topic/add-remove-or-change-a-trusted-location-7ee1cdc2-483e-4cbb-bcb3-4e7c67147fb4)
- [Aktive indholdstyper i dine filer](https://support.microsoft.com/topic/active-content-types-in-your-files-b7ff2e8a-4055-47d4-8c7d-541e19f62bea)

## <a name="configure-trusted-document-settings-in-office-policies"></a>Konfigurer dokumentindstillinger, der er tillid til, i Office politikker

Administratorer har mange måder at konfigurere Office på i en organisation. Eksempel:

- **Office tjeneste for cloudpolitik**: Konfigurer en brugerbaseret politik, der gælder for en bruger på alle enheder, der har adgang til filer i Office apps, med deres Azure AD-konto. Se trinnene til [oprettelse af en Office cloudpolitikkonfiguration](/DeployOffice/overview-office-cloud-policy-service) i [tjenesten Office Cloud Policy Service](https://config.office.com/officeSettings/officePolicies).
- **Office politikker i Intune**: Brug kataloget Intune Indstillinger eller administrative skabeloner til at installere HKCU-politikker på Windows 10 pc'er: I [MEM Administration](https://endpoint.microsoft.com/#blade/Microsoft_Intune_DeviceSettings/DevicesMenu/configurationProfiles) under **Enhedskonfigurationsprofiler**\>.
  - ***Administrative skabeloner***: Se instruktionerne til at bruge Windows 10 skabeloner til at konfigurere [administrative skabeloner](/mem/intune/configuration/administrative-templates-windows).
  - ***Indstillinger katalog (prøveversion)***: Se instruktionerne til brug af [kataloget Indstillinger (prøveversion).](/mem/intune/configuration/settings-catalog)
- **Gruppepolitik**: Brug dit lokale Active Directory til at installere gruppepolitikobjekter på brugere og computere. Hvis du vil oprette et gruppepolitikobjekt for denne indstilling, skal du downloade de nyeste [administrative skabelonfiler (ADMX/ADML) og Office tilpasningsværktøj til Microsoft 365 Apps for enterprise, Office 2019 og Office 2016](https://www.microsoft.com/download/details.aspx?id=49030).

## <a name="known-issues"></a>Kendte problemer

- Når politikken **VBA-makromeddelelser** (Access, PowerPoint, Visio, Word) eller **makromeddelelser** (Excel) er angivet til værdien **Deaktiver alle undtagen digitalt signerede makroer**, vises den forventede tillidslinje ikke, og **Sikkerhedsoplysninger** i backstage viser ikke oplysninger om blokerede makroer, selvom indstillingen fungerer som forventet. Det Office team arbejder på at løse problemet.

## <a name="admin-options-for-restricting-active-content"></a>Administratorindstillinger til begrænsning af aktivt indhold

Der er stor forskel på tillidsniveauet i internt oprettet indhold i forhold til indhold, som brugerne downloader fra internettet. Overvej at tillade aktivt indhold i interne dokumenter og globalt undlade at tillade aktivt indhold i dokumenter fra internettet.

Hvis dine brugere ikke har brug for bestemte typer aktivt indhold, er din mest sikre mulighed at bruge politikker til at deaktivere brugeradgang til det aktive indhold og tillade undtagelser efter behov.

Følgende politikker er tilgængelige:

- **Deaktiver placeringer, der er tillid til**: Undtagelser for tilgængelige grupper.
- **Deaktiver dokumenter, der er tillid til**: Undtagelser for tilgængelige grupper.
- **Deaktiver alt aktivt indhold**: Undtagelser for enkeltpersoner.

Tabellerne i følgende afsnit beskriver de indstillinger, der styrer aktivt indhold. Hvis disse politikker anvendes på brugere, gennemtvinges de på dokumenter, der er tillid til, og den tidligere slutbrugeroplevelse er muligvis ikke den samme. Tabellerne indeholder også den anbefalede indstilling for grundlæggende sikkerhedsindstillinger og identificerer andre indstillinger, hvor brugerprompten, der skal tilsidesættes, er tilgængelig (så brugeren kan aktivere det aktive indhold).

### <a name="hkey_current_user-settings"></a>indstillinger for HKEY_CURRENT_USER

<p>

****
|Kategori|App|Politiknavn|Oprindelig plan for sikkerhed<br>indstilling (anbefales)|Indstilling med brugerprompt<br>og tilsidesætte tilgængelige?|
|---|---|---|---|---|
|ActiveX|Office|initialisering af ActiveX-kontrolelement|**6**|**Ja** for følgende værdier: <ul><li>**3**</li><li>**4**</li><li>**5**</li><li>**6**</li></ul>|
|ActiveX|Office|Tillad aktive X One Off-formularer|**Indlæs kun Outlook kontrolelementer**|Nej|
|ActiveX|Office|Kontrollér ActiveX objekter|Ikke en indstilling for sikkerhedsgrundlinje.|Nej|
|ActiveX|Office|Deaktiver alle ActiveX|Ikke en indstilling for sikkerhedsgrundlinje.|**Ja** for følgende værdier: <ul><li>**Deaktiveret**</li><li>**Ikke konfigureret**</li></ul>|
|ActiveX|Office|Indlæs kontrolelementer i Formularer3|**1**|**Ja** for følgende værdier: <ul><li>**2**</li><li>**3**</li></ul>|
|Tilføjelsesprogrammer & udvidelse|Excel <p> PowerPoint <p> Project <p> Publisher <p> Visio <p> Word|Deaktiver meddelelse om tillidslinje for ikke-signerede programtilføjelsesprogramler, og bloker dem|**Aktiveret**|**Ja** for værdien **Disabled**.|
|Tilføjelsesprogrammer & udvidelse|Excel <p> PowerPoint <p> Project <p> Publisher <p> Visio <p> Word|Kræv, at programtilføjelsesprogramler er signeret af Publisher|**Aktiveret**|Nej|
|Tilføjelsesprogrammer & udvidelse|Excel|Vis ikke advarselsbeskeden Genudgiv automatisk|**Deaktiveret**|Nej|
|Tilføjelsesprogrammer & udvidelse|Excel|INDSTILLINGER for funktionen WEBSERVICE|**Deaktiver alle med meddelelse**|**Ja** for følgende værdier: <ul><li>**Deaktiver alle med meddelelse**</li><li>**Deaktiveret**</li><li>**Ikke konfigureret**</li></ul>|
|Tilføjelsesprogrammer & udvidelse|Office|Deaktiver den Office klient fra at forespørge SharePoint-serveren om publicerede links|**Deaktiveret**|Nej|
|Tilføjelsesprogrammer & udvidelse|Office|Deaktiver brugergrænseflade, der udvides fra dokumenter og skabeloner|Tillad ikke i Word = Sand <p> Tillad ikke i Project = Falsk <p> Tillad ikke i Excel = Sand <p> Tillad ikke i Visio = Falsk <p> Tillad ikke i PowerPoint = Sand <p> Tillad ikke i Access = Sand <p> Tillad ikke i Outlook = Sand <p> Tillad ikke i Publisher = Sand <p> Tillad ikke i InfoPath = Sand|Nej|
|Tilføjelsesprogrammer & udvidelse|Outlook|Konfigurer Outlook objektmodelprompt ved adgang til et adressekartotek|**Afvis automatisk**|**Ja** for følgende værdier: <ul><li>**Spørg bruger**</li><li>**Spørg bruger baseret på computersikkerhed**</li><li>**Deaktiveret**</li><li>**Ikke konfigureret**</li></ul>|
|Tilføjelsesprogrammer & udvidelse|Outlook|Prompten Konfigurer Outlook objektmodel Ved adgang til egenskaben Formula for et UserProperty-objekt|**Afvis automatisk**|**Ja** for følgende værdier: <ul><li>**Spørg bruger**</li><li>**Spørg bruger baseret på computersikkerhed**</li><li>**Deaktiveret**</li><li>**Ikke konfigureret**</li></ul>|
|Tilføjelsesprogrammer & udvidelse|Outlook|Konfigurer Outlook objektmodelprompt ved udførelse af Gem som|**Afvis automatisk**|**Ja** for følgende værdier: <ul><li>**Spørg bruger**</li><li>**Spørg bruger baseret på computersikkerhed**</li><li>**Deaktiveret**</li><li>**Ikke konfigureret**</li></ul>|
|Tilføjelsesprogrammer & udvidelse|Outlook|Konfigurer Outlook objektmodelprompt ved læsning af adresseoplysninger|**Afvis automatisk**|**Ja** for følgende værdier: <ul><li>**Spørg bruger**</li><li>**Spørg bruger baseret på computersikkerhed**</li><li>**Deaktiveret**</li><li>**Ikke konfigureret**</li></ul>|
|Tilføjelsesprogrammer & udvidelse|Outlook|Konfigurer Outlook objektmodelprompt, når der svares på møde- og opgaveanmodninger|**Afvis automatisk**|**Ja** for følgende værdier: <ul><li>**Spørg bruger**</li><li>**Spørg bruger baseret på computersikkerhed**</li><li>**Deaktiveret**</li><li>**Ikke konfigureret**</li></ul>|
|Tilføjelsesprogrammer & udvidelse|Outlook|Konfigurer Outlook objektmodelprompt, når der sendes mail|**Afvis automatisk**|**Ja** for følgende værdier: <ul><li>**Spørg bruger**</li><li>**Spørg bruger baseret på computersikkerhed**</li><li>**Deaktiveret**</li><li>**Ikke konfigureret**</li></ul>|
|Tilføjelsesprogrammer & udvidelse|Outlook|Angiv Outlook handlingsprompt for brugerdefinerede handlinger i objektmodellen|**Afvis automatisk**|**Ja** for følgende værdier: <ul><li>**Spørg bruger**</li><li>**Spørg bruger baseret på computersikkerhed**</li><li>**Deaktiveret**</li><li>**Ikke konfigureret**</li></ul>|
|Tilføjelsesprogrammer & udvidelse|PowerPoint|Kør programmer|**deaktiver (kør ikke nogen programmer)**|**Ja** for værdien **Aktivér (spørg brugeren, før der køres)**|
|Tilføjelsesprogrammer & udvidelse|Word <p> Excel|Deaktiver smart dokuments brug af manifester|**Aktiveret**|Nej|
|DDE|Excel|Tillad ikke, at DDE-serveren (Dynamic Data Exchange) startes i Excel|**Aktiveret**|**Ja** for værdien **Ikke konfigureret**.|
|DDE|Excel|Tillad ikke DDE-serveropslag (Dynamic Data Exchange) i Excel|**Aktiveret**|**Ja** for følgende værdier: <ul><li>**Deaktiveret**</li><li>**Ikke konfigureret**</li></ul>|
|DDE|Word|Dynamiske data Exchange|**Deaktiveret**|Nej|
|Jscript & VBScript|Outlook|Tillad scripts i engangsformularer Outlook formularer|**Deaktiveret**|Nej|
|Jscript & VBScript|Outlook|Tillad ikke, at Outlook objektmodelscripts kører for offentlige mapper|**Aktiveret**|Nej|
|Jscript & VBScript|Outlook|Tillad ikke, at Outlook objektmodelscripts kører for delte mapper|**Aktiveret**|Nej|
|Makroer|Excel|Makromeddelelser|**Deaktiver alle undtagen digitalt signerede makroer**|**Ja** for følgende værdier: <ul><li>**Deaktiveret**</li><li>**Ikke konfigureret**</li></ul>|
|Makroer|Access <p> PowerPoint <p> Project <p> Publisher <p> Visio <p> Word|INDSTILLINGER for VBA-makromeddelelse|**Deaktiver alle undtagen digitalt signerede makroer** <p> Og <p> **Kræv, at makroer signeres af en udgiver, der er tillid til**|**Ja** for følgende værdier: <ul><li>**Deaktiveret**</li><li>**Ikke konfigureret**</li></ul>|
|Makroer|Access <p> Excel <p> PowerPoint <p> Visio <p> Word|Bloker makroer fra at køre i Office filer fra internettet|**Aktiveret**|**Ja** for følgende værdier: <ul><li>**Deaktiveret**</li><li>**Ikke konfigureret**</li></ul>|
|Makroer|Excel|Scan krypterede makroer i Excel Åbne XML-projektmapper|**Scan krypterede makroer (standard)**|Nej|
|Makroer|Office|Tillad, at VBA indlæser typelib-referencer efter sti fra intranetplaceringer, der ikke er tillid til|**Deaktiveret**|Nej|
|Makroer|Office|Automatiseringssikkerhed|**Brug sikkerhedsniveauet for programmakroer**|Nej|
|Makroer|Office|Deaktiver andre sikkerhedskontroller i VBA-biblioteksreferencer, der kan referere til usikre placeringer på den lokale computer|**Deaktiveret**|Nej|
|Makroer|Office|Scanningsområde for makrokørsel|**Aktivér for alle dokumenter**|Nej|
|Makroer|Office|Hav kun tillid til VBA-makroer, der bruger V3-signaturer|Ikke en indstilling for sikkerhedsgrundlinje.|Nej|
|Makroer|Outlook|Outlook sikkerhedstilstand|**Brug Gruppepolitik Outlook Security**|Påkrævet for at aktivere alle indstillinger for Outlook gruppepolitikobjekt. <p> Nævnt som en afhængighed (denne politik blokerer ikke aktivt indhold selv).|
|Makroer|Outlook|Sikkerhedsindstilling for makroer|**Advar for signeret, deaktiver usigneret**|**Ja** for følgende værdier: <ul><li>**Advar altid**</li><li>**Advar for signeret, deaktiver usigneret**</li><li>**Deaktiveret**</li><li>**Ikke konfigureret**</li></ul>|
|Makroer|PowerPoint|Scan krypterede makroer i PowerPoint Åbn XML-præsentationer|**Scan krypterede makroer (standard)**|Nej|
|Makroer|Publisher|Publisher Automation-sikkerhedsniveau|**Efter brugergrænseflade (bedt om)**|Nej|
|Makroer|Word|Scan krypterede makroer i Åbne XML-dokumenter i Word|**Scan krypterede makroer (standard)**|Nej|
|

### <a name="hkey_local_machine-settings"></a>indstillinger for HKEY_LOCAL_MACHINE

<p>

****
|Kategori|App|Politiknavn|Oprindelig plan for sikkerhed<br>indstilling (anbefales)|Indstilling med brugerprompt<br>og tilsidesætte tilgængelige?|
|---|---|---|---|---|
|ActiveX|Office|Begræns ActiveX installation|excel.exe = Sand <p> exprwd.exe = Sand <p> groove.exe = Sand <p> msaccess.exe = Sand <p> mse7.exe = Sand <p> mspub.exe = Sand <p> onent.exe = Sand <p> outlook.exe = Sand <p> powerpnt.exe = Sand <p> pptview.exe = Sand <p> spDesign.exe = Sand <p> visio.exe = Sand <p> winproj.exe = Sand <p> winword.exe = Sand|Nej|
|Tilføjelsesprogrammer & udvidelse|Office|Administration af tilføjelsesprogram|excel.exe = Sand <p> exprwd.exe = Sand <p> groove.exe = Sand <p> msaccess.exe = Sand <p> mse7.exe = Sand <p> mspub.exe = Sand <p> onent.exe = Sand <p> outlook.exe = Sand <p> powerpnt.exe = Sand <p> pptview.exe = Sand <p> spDesign.exe = Sand <p> visio.exe = Sand <p> winproj.exe = Sand <p> winword.exe = Sand|Nej|
|Tilføjelsesprogrammer & udvidelse|Office|Bloker flashaktivering i Office dokumenter|Se Microsoft Security Guide ADMX/ADML-filer for at få en liste over COM-killbits for at blokere al aktivering af Flash på Microsoft 365 apps. ADMX-/ADML-filerne til enterprise Security Baselines er tilgængelige i [Security Compliance Toolkit](https://www.microsoft.com/download/details.aspx?id=55319).|Nej|
|Jscript & VBScript|Office|Begræns udførelse af ældre JScript for Office|**Aktiveret**: <p> Adgang: 69632 <p> Excel: 69632 <p> OneNote: 69632 <p> Outlook: 69632 <p> PowerPoint: 69632 <p> Project: 69632 <p> Publisher: 69632 <p> Visio: 69632 <p> Ord: 69632|Nej|
|Jscript & VBScript|Office|Sikkerhedsbegrænsninger for scriptede vinduer|excel.exe = Sand <p> exprwd.exe = Sand <p> groove.exe = Sand <p> msaccess.exe = Sand <p> mse7.exe = Sand <p> mspub.exe = Sand <p> onent.exe = Sand <p> outlook.exe = Sand <p> powerpnt.exe = Sand <p> pptview.exe = Sand <p> spDesign.exe = Sand <p> visio.exe = Sand <p> winproj.exe = Sand <p> winword.exe = Sand|Nej|
|
