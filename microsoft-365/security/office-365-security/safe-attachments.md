---
title: Sikre vedhæftede filer
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: Admin
ms.date: ''
ms.topic: overview
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: 6e13311e-92ae-495e-a619-56d770199170
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
- seo-marvel-apr2020
description: Administratorer kan få mere at vide om funktionen Pengeskab vedhæftede filer i Microsoft Defender for Office 365.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: e50904932b95dabdad627a7a3291659c1c4d9584
ms.sourcegitcommit: 18bc521a88b7b521bccb0e69d02deac764218087
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/16/2022
ms.locfileid: "66115933"
---
# <a name="safe-attachments-in-microsoft-defender-for-office-365"></a>Pengeskab vedhæftede filer i Microsoft Defender for Office 365

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Gælder for**
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Pengeskab vedhæftede filer i [Microsoft Defender for Office 365](defender-for-office-365.md) giver et ekstra lag beskyttelse af vedhæftede filer i mails, der allerede er blevet scannet af [beskyttelse mod malware i Exchange Online Protection (EOP)](anti-malware-protection.md). Specifikt bruger Pengeskab Attachments et virtuelt miljø til at kontrollere vedhæftede filer i mails, før de leveres til modtagere (en proces, der kaldes _detonation_).

Pengeskab beskyttelse af vedhæftede filer i mails styres af Pengeskab politikker for vedhæftede filer. Selvom der ikke er nogen standardpolitik for Pengeskab Vedhæftede filer, giver den forudindstillede sikkerhedspolitik for indbygget **beskyttelse** Pengeskab beskyttelse af vedhæftede filer til alle modtagere (brugere, der ikke er defineret i brugerdefinerede Pengeskab politikker for vedhæftede filer). Du kan få flere oplysninger [under Forudindstillede sikkerhedspolitikker i EOP og Microsoft Defender for Office 365](preset-security-policies.md). Du kan også oprette politikker for vedhæftede filer Pengeskab, der gælder for bestemte brugere, grupper eller domæner. Du kan finde instruktioner under [Konfigurer politikker for vedhæftede filer Pengeskab i Microsoft Defender for Office 365](set-up-safe-attachments-policies.md).

I følgende tabel beskrives scenarier for Pengeskab Vedhæftede filer i Microsoft 365 og Office 365 organisationer, der omfatter Microsoft Defender for Office 365 (med andre ord er manglende licenser aldrig et problem i eksemplerne).

|Scenario|Resultat|
|---|---|
|Pats Microsoft 365 E5 organisation har ikke konfigureret nogen Pengeskab politikker for vedhæftede filer.|Pat er beskyttet af Pengeskab Vedhæftede filer på grund af den forudindstillede sikkerhedspolitik for indbygget **beskyttelse**, der gælder for alle modtagere, der ikke på anden måde er defineret i Pengeskab politikker for vedhæftede filer.|
|Lees organisation har en politik for vedhæftede filer Pengeskab, der kun gælder for økonomimedarbejdere. Lee er medlem af salgsafdelingen.|Lee og resten af salgsafdelingen er beskyttet af Pengeskab Vedhæftede filer på grund af den forudindstillede sikkerhedspolitik **for indbygget beskyttelse**, der gælder for alle modtagere, som ikke på anden måde er defineret i Pengeskab politikker for vedhæftede filer.|
|I går oprettede en administrator i Jeans organisation en politik for vedhæftede filer Pengeskab, der gælder for alle medarbejdere. Tidligere i dag modtog Jean en mail, der indeholdt en vedhæftet fil.|Jean er beskyttet af Pengeskab vedhæftede filer på grund af den brugerdefinerede politik Pengeskab Vedhæftede filer. <br/><br/> Det tager typisk ca. 30 minutter, før en ny politik træder i kraft.|
|Chris' organisation har mangeårige politikker for Pengeskab vedhæftede filer for alle i organisationen. Chris modtager en mail, der har en vedhæftet fil, og videresender derefter meddelelsen til eksterne modtagere.|Chis er beskyttet af Pengeskab vedhæftede filer. <br/><br/> Hvis de eksterne modtagere i en Microsoft 365 organisation, er de videresendte meddelelser også beskyttet af Pengeskab Vedhæftede filer.|

Pengeskab Scanning af vedhæftede filer finder sted i det samme område, hvor dine Microsoft 365 data er placeret. Du kan finde flere oplysninger om datacentergeografi under [Hvor er dine data placeret?](https://products.office.com/where-is-your-data-located?geo=All)

> [!NOTE]
> Følgende funktioner er placeret i de globale indstillinger for Pengeskab politikker for vedhæftede filer på Microsoft 365 Defender-portalen. Men disse indstillinger er aktiveret eller deaktiveret globalt og kræver ikke Pengeskab politikker for vedhæftede filer:
>
> - [Pengeskab Vedhæftede filer til SharePoint, OneDrive og Microsoft Teams](mdo-for-spo-odb-and-teams.md).
> - [Sikre dokumenter i Microsoft 365 E5](safe-docs.md)

## <a name="safe-attachments-policy-settings"></a>politikindstillinger for Pengeskab vedhæftede filer

I dette afsnit beskrives indstillingerne i Pengeskab politikker for vedhæftede filer:

- **Pengeskab Ukendt malwaresvar for vedhæftede filer**: Denne indstilling styrer handlingen for Pengeskab scanning af malware i vedhæftede filer i mails. De tilgængelige indstillinger er beskrevet i følgende tabel:

  |Mulighed|Effekt|Bruges, når du vil:|
  |---|---|---|
  |**Ud**|Vedhæftede filer scannes ikke for malware af Pengeskab Vedhæftede filer. Meddelelser scannes stadig for malware af [beskyttelse mod skadelig software i EOP](anti-malware-protection.md).|Slå scanning fra for valgte modtagere. <br/><br/> Undgå unødvendige forsinkelser i distributionen af interne mails. <br/><br/> **Denne indstilling anbefales ikke til de fleste brugere. Du bør kun bruge denne indstilling til at slå scanning af Pengeskab vedhæftede filer fra for modtagere, der kun modtager meddelelser fra afsendere, der er tillid til. ZAP sætter ikke meddelelser i karantæne, hvis Pengeskab Vedhæftede filer er slået fra, og der ikke modtages et malwaresignal. Du kan finde flere oplysninger under [Automatisk tøm på nul timer](zero-hour-auto-purge.md)**|
  |**Skærm**|Leverer meddelelser med vedhæftede filer og sporer derefter, hvad der sker med registreret malware. <br/><br/> Levering af sikre meddelelser kan blive forsinket på grund af scanning af Pengeskab vedhæftede filer.|Se, hvor registreret malware findes i din organisation.|
  |**Bloker**|Forhindrer, at meddelelser med registrerede vedhæftede filer med skadelig software leveres. <br/><br/> Meddelelser er sat i karantæne. Som standard er det kun administratorer (ikke brugere), der kan gennemse, udgive eller slette meddelelserne.<sup>\*</sup> <br/><br/> Blokerer automatisk fremtidige forekomster af meddelelserne og de vedhæftede filer. <br/><br/> Levering af sikre meddelelser kan blive forsinket på grund af scanning af Pengeskab vedhæftede filer.|Beskytter din organisation mod gentagne angreb ved hjælp af de samme vedhæftede malwarefiler. <br/><br/> Dette er standardværdien og den anbefalede værdi i standard- og [strenge forudindstillede sikkerhedspolitikker](preset-security-policies.md).|
  |**Erstatte**|Fjerner registrerede vedhæftede filer efter malware. <br/><br/> Giver modtagere besked om, at vedhæftede filer er blevet fjernet. <br/><br/>  Meddelelser, der indeholder skadelige vedhæftede filer, er sat i karantæne. Som standard er det kun administratorer (ikke brugere), der kan gennemse, udgive eller slette meddelelserne.<sup>\*</sup> <br/><br/> Levering af sikre meddelelser kan blive forsinket på grund af scanning af Pengeskab vedhæftede filer.|Gør modtagerne mere synlige for, at vedhæftede filer blev fjernet på grund af registreret malware.|
  |**Dynamisk levering**|Leverer meddelelser med det samme, men erstatter vedhæftede filer med pladsholdere, indtil scanningen af vedhæftede filer Pengeskab er fuldført. <br/><br/> Meddelelser, der indeholder skadelige vedhæftede filer, er sat i karantæne. Som standard er det kun administratorer (ikke brugere), der kan gennemse, udgive eller slette meddelelserne.<sup>\*</sup> <br/><br/> Du kan finde flere oplysninger [i afsnittet Dynamisk levering i Pengeskab politikker for vedhæftede filer](#dynamic-delivery-in-safe-attachments-policies) senere i denne artikel.|Undgå meddelelsesforsinkelser, samtidig med at modtagerne beskyttes mod skadelige filer.|

  <sup>\*</sup>Administratorer kan oprette og tildele _karantænepolitikker_ i Pengeskab politikker for vedhæftede filer, der definerer, hvad brugerne har tilladelse til at gøre for karantænemeddelelser. Du kan få flere oplysninger under [Karantænepolitikker](quarantine-policies.md).

- **Omdiriger vedhæftet fil ved registrering: Aktivér omdirigering** , og **send den vedhæftede fil til følgende mailadresse**: Ved handlinger af typen **Bloker**, **Overvåg** eller **Erstat** skal du sende meddelelser, der indeholder vedhæftede malware-filer, til den angivne interne eller eksterne mailadresse til analyse og undersøgelse.

  Anbefalingen for Standard- og Strict-politikindstillinger er at aktivere omdirigering. Du kan få flere oplysninger under [Pengeskab indstillinger for vedhæftede filer](recommended-settings-for-eop-and-office365.md#safe-attachments-settings).

- **Anvend ovenstående valg, hvis der opstår timeout for malwarescanning efter vedhæftede filer, eller der opstår fejl**: Den handling, der er angivet af **Pengeskab Vedhæftede filer ukendt malwaresvar**, udføres på meddelelser, selvom Pengeskab scanning af vedhæftede filer ikke kan fuldføres. Vælg altid denne indstilling, hvis du vælger **Aktivér omdirigering**. Ellers kan meddelelser gå tabt.

- **Modtagerfiltre**: Du skal angive de betingelser og undtagelser for modtageren, der bestemmer, hvem politikken gælder for. Du kan bruge disse egenskaber til betingelser og undtagelser:
  - **Modtageren er**
  - **Modtagerdomænet er**
  - **Modtageren er medlem af**

  Du kan kun bruge en betingelse eller undtagelse én gang, men betingelsen eller undtagelsen kan indeholde flere værdier. Flere værdier med samme betingelse eller undtagelse bruger OR-logik (f.eks. _\<recipient1\>_ eller _\<recipient2\>_). Forskellige betingelser eller undtagelser bruger AND-logik (f.eks. _\<recipient1\>_ og _\<member of group 1\>_).

  > [!IMPORTANT]
  > Flere forskellige betingelser eller undtagelser er ikke additive; de er inkluderende. Politikken anvendes _kun_ på de modtagere, der stemmer overens med _alle_ de angivne modtagerfiltre. Du kan f.eks. konfigurere en modtagerfilterbetingelse i politikken med følgende værdier:
  >
  > - Modtageren er: romain@contoso.com
  > - Modtageren er medlem af: Direktører
  >
  > Politikken anvendes _kun_ på romain@contoso.com, hvis han også er medlem af koncernerne Direktører. Hvis han ikke er medlem af gruppen, anvendes politikken ikke på ham.
  >
  > Hvis du på samme måde bruger det samme modtagerfilter som en undtagelse til politikken, anvendes politikken ikke _kun_ på romain@contoso.com, hvis han også er medlem af grupperne Direktører. Hvis han ikke er medlem af gruppen, gælder politikken stadig for ham.

- **Prioritet**: Hvis du opretter flere politikker, kan du angive den rækkefølge, de anvendes i. Der kan ikke være to politikker, der har samme prioritet, og behandlingen af politikker stopper, når den første politik er anvendt.

  Du kan finde flere oplysninger om prioritetsrækkefølgen, og hvordan flere politikker evalueres og anvendes, under [Beskyttelse af mailrækkefølge og prioritet](how-policies-and-protections-are-combined.md).

### <a name="dynamic-delivery-in-safe-attachments-policies"></a>Dynamisk levering i politikker for vedhæftede filer Pengeskab

> [!NOTE]
> Dynamic Delivery fungerer kun for Exchange Online postkasser.

Handlingen Dynamisk levering i Pengeskab politikker for vedhæftede filer søger at fjerne eventuelle forsinkelser i levering af mails, der kan skyldes scanning af vedhæftede filer Pengeskab. Brødteksten i mailen leveres til modtageren med en pladsholder for hver vedhæftet fil. Pladsholderen forbliver, indtil det konstateres, at den vedhæftede fil er sikker, og derefter bliver den vedhæftede fil tilgængelig til at åbne eller downloade.

Hvis en vedhæftet fil er skadelig, er meddelelsen sat i karantæne.

De fleste PDF-filer og Office dokumenter kan vises i fejlsikret tilstand, mens scanning af vedhæftede filer Pengeskab er i gang. Hvis en vedhæftet fil ikke er kompatibel med fremviseren til dynamisk levering, får modtagerne vist en pladsholder for den vedhæftede fil, indtil scanningen af Pengeskab vedhæftede filer er fuldført.

Hvis du bruger en mobilenhed, og PDF-filer ikke gengives i Dynamic Delivery-fremviseren på din mobilenhed, kan du prøve at åbne meddelelsen i Outlook på internettet (tidligere kaldet Outlook Web App) ved hjælp af din mobilbrowser.

Her er nogle overvejelser i forbindelse med Dynamisk levering og videresendte meddelelser:

- Hvis den videresendte modtager er beskyttet af en Pengeskab politik for vedhæftede filer, der bruger indstillingen Dynamisk levering, får modtageren vist pladsholderen med mulighed for at få vist kompatible filer.
- Hvis den videresendte modtager ikke er beskyttet af en Pengeskab politik for vedhæftede filer, leveres meddelelsen og de vedhæftede filer uden Pengeskab scanning af vedhæftede filer eller pladsholdere for vedhæftede filer.

Der er scenarier, hvor Dynamic Delivery ikke kan erstatte vedhæftede filer i meddelelser. Disse scenarier omfatter:

- Meddelelser i offentlige mapper.
- Meddelelser, der distribueres ud af og derefter tilbage til en brugers postkasse ved hjælp af brugerdefinerede regler.
- Meddelelser, der flyttes (automatisk eller manuelt) fra cloudpostkasser til andre placeringer, herunder arkivmapper.
- Indbakkeregler flytter meddelelsen fra indbakken til en anden mappe.
- Slettede meddelelser.
- Brugerens postkassesøgemappe er i fejltilstand.
- Exchange Online organisationer, hvor Udråbstegn er aktiveret. Du kan løse dette problem under [KB4014438](https://support.microsoft.com/help/4014438).
- [S/MIME)](/exchange/security-and-compliance/smime-exo/smime-exo) krypterede meddelelser.
- Du har konfigureret handlingen Dynamisk levering i en politik for vedhæftede filer Pengeskab, men modtageren understøtter ikke Dynamisk levering (modtageren er f.eks. en postkasse i en lokal Exchange organisation). Men [Pengeskab Links i Microsoft Defender for Office 365](set-up-safe-links-policies.md) kan scanne Office vedhæftede filer, der indeholder URL-adresser (afhængigt af hvordan de [globale indstillinger for Pengeskab links](configure-global-settings-for-safe-links.md) er konfigureret).

## <a name="submitting-files-for-malware-analysis"></a>Indsendelse af filer til malwareanalyse

- Hvis du modtager en fil, som du vil sende til Microsoft til analyse, skal du se [Send malware og ikke-malware til Microsoft til analyse](submitting-malware-and-non-malware-to-microsoft-for-analysis.md).
- Hvis du modtager en mail (med eller uden en vedhæftet fil), som du vil sende til Microsoft til analyse, skal du se [Rapportér meddelelser og filer til Microsoft](report-junk-email-messages-to-microsoft.md).
