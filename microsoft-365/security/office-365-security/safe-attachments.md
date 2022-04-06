---
title: Pengeskab vedhæftede filer
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
description: Administratorer kan få mere at vide Pengeskab funktionen Vedhæftede filer i Microsoft Defender Office 365.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 01721d36967413a7f939d3618340e5630c3d6007
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/20/2022
ms.locfileid: "63683795"
---
# <a name="safe-attachments-in-microsoft-defender-for-office-365"></a>Pengeskab vedhæftede filer i Microsoft Defender til Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Microsoft Defender til Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Pengeskab Vedhæftede filer i [Microsoft Defender til Office 365](defender-for-office-365.md) giver et ekstra lag af beskyttelse til vedhæftede filer i mails, der allerede er scannet af beskyttelse mod [malware i Exchange Online Protection (EOP)](anti-malware-protection.md). Specifikt bruger Pengeskab et virtuelt miljø til at kontrollere vedhæftede filer i mails, før de leveres til modtagere (en proces kaldet _detonation_).

Pengeskab beskyttelse af vedhæftede filer i mails styres af politikkerne Pengeskab vedhæftede filer. Selvom der ikke er nogen standardpolitik Pengeskab Vedhæftede filer, giver den **indbyggede** beskyttelse foruddefinerede sikkerhedspolitik Pengeskab Beskyttelse af vedhæftede filer til alle modtagere (brugere, der ikke er defineret i brugerdefinerede Pengeskab Politikker for vedhæftede filer). Du kan finde flere oplysninger [i Forudindstillede sikkerhedspolitikker i EOP og Microsoft Defender Office 365](preset-security-policies.md). Du kan også oprette Pengeskab politikker for vedhæftede filer, der gælder for bestemte brugere, grupper eller domæner. Du kan finde en [vejledning under Konfigurere Pengeskab Politikker for vedhæftede filer i Microsoft Defender Office 365](set-up-safe-attachments-policies.md).

I følgende tabel beskrives scenarier for Pengeskab Vedhæftede filer i Microsoft 365- og Office 365-organisationer, der omfatter Microsoft Defender til Office 365 (med andre ord er manglende licenser aldrig et problem i eksemplerne).

|Scenarie|Resultat|
|---|---|
|Pats Microsoft 365 E5 har ikke konfigureret Pengeskab vedhæftede filer.|Pat er beskyttet af Pengeskab på grund af den **indbyggede** beskyttelse foruddefinerede sikkerhedspolitik, der gælder for alle modtagere, der ellers ikke er defineret i Pengeskab Vedhæftede filer politikker.|
|Lees organisation har en Pengeskab Politik for vedhæftede filer, der kun gælder for finansmedarbejdere. Lee er medlem af salgsafdelingen.|Lee og resten af salgsafdelingen er beskyttet af Pengeskab Vedhæftede filer på grund af den **indbyggede** beskyttelse foruddefinerede sikkerhedspolitik, der gælder for alle modtagere, der ellers ikke er defineret i Pengeskab Politikker for vedhæftede filer.|
|I går oprettede en administrator i Jean's organisation en Pengeskab politik for vedhæftede filer, der gælder for alle medarbejdere. Tidligere i dag modtog Jane en mail, der indeholdt en vedhæftet fil.|Jean er beskyttet af Pengeskab vedhæftede filer på grund af denne brugerdefinerede Pengeskab politik for vedhæftede filer. <p> Det tager som regel ca. 30 minutter, før en ny politik træder i kraft.|
|Chris's organisation har længe arbejdet Pengeskab politikker for vedhæftede filer for alle i organisationen. Chris modtager en mail med en vedhæftet fil og videresender derefter meddelelsen til eksterne modtagere.|Chis er beskyttet af Pengeskab vedhæftede filer. <p> Hvis de eksterne modtagere i en Microsoft 365, så er de videresendte meddelelser også beskyttet af Pengeskab vedhæftede filer.|

Pengeskab scanning af vedhæftede filer finder sted i det samme område, Microsoft 365 dine data befinder sig. Du kan finde flere oplysninger om datacentergege områder i [Hvor er dine data placeret?](https://products.office.com/where-is-your-data-located?geo=All)

> [!NOTE]
> Følgende funktioner findes i de globale indstillinger for Pengeskab politikker for vedhæftede filer i Microsoft 365 Defender portal. Men disse indstillinger er aktiveret eller deaktiveret globalt og kræver ikke ændringer af politikkerne Pengeskab vedhæftede filer:
>
> - [Pengeskab Vedhæftede filer til SharePoint, OneDrive og Microsoft Teams](mdo-for-spo-odb-and-teams.md).
> - [Sikre dokumenter i Microsoft 365 E5](safe-docs.md)

## <a name="safe-attachments-policy-settings"></a>Pengeskab indstillinger for politik for vedhæftede filer

I dette afsnit beskrives indstillingerne i Pengeskab politikker for vedhæftede filer:

- **Pengeskab Ukendt malwaresvar ved vedhæftede filer**: Denne indstilling styrer handlingen for scanning Pengeskab scanning af vedhæftede filers malware i mails. De tilgængelige indstillinger er beskrevet i følgende tabel:

  |Indstilling|Effekt|Brug følgende, når du vil:|
  |---|---|---|
  |**Fra**|Vedhæftede filer scannes ikke for malware ved hjælp af Pengeskab vedhæftede filer. Meddelelser scannes stadig for malware med [beskyttelse mod malware i EOP](anti-malware-protection.md).|Slå scanning fra for udvalgte modtagere. <p> Undgå unødvendige forsinkelser i routing af intern mail. <p> **Denne indstilling anbefales ikke til de fleste brugere. Du bør kun bruge denne indstilling til at deaktivere søgning Pengeskab scanning af vedhæftede filer for modtagere, der kun modtager meddelelser fra afsendere, der er tillid til. ZAP sætter ikke meddelelser i karantæne, Pengeskab vedhæftede filer er slået fra, og der ikke modtages et malwaresignal. Du kan få mere at [vide under Automatisk tømning uden time](zero-hour-auto-purge.md)**|
  |**Skærm**|Leverer meddelelser med vedhæftede filer og registrerer derefter, hvad der sker med registreret malware. <p> Levering af sikre meddelelser kan være forsinket på grund af Pengeskab scanning af vedhæftede filer.|Se, hvor registreret malware finder sted i din organisation.|
  |**Bloker**|Forhindrer meddelelser med registrerede malware vedhæftede filer i at blive leveret. <p> Meddelelser er sat i karantæne. Som standard er det kun administratorer (ikke brugere), der kan gennemse, frigive eller slette meddelelserne.<sup>\*</sup> <p> Blokerer automatisk fremtidige forekomster af meddelelser og vedhæftede filer. <p> Levering af sikre meddelelser kan være forsinket på grund af Pengeskab scanning af vedhæftede filer.|Beskytter din organisation mod gentagne angreb ved hjælp af de samme vedhæftede malware-filer. <p> Dette er standardværdien og den anbefalede værdi i Standard og Strenge [forudindstillede sikkerhedspolitikker](preset-security-policies.md).|
  |**Erstat**|Fjerner registrerede vedhæftede malwares. <p> Giver modtagere besked om, at vedhæftede filer er blevet fjernet. <p>  Meddelelser, der indeholder skadelige vedhæftede filer, er sat i karantæne. Som standard er det kun administratorer (ikke brugere), der kan gennemse, frigive eller slette meddelelserne.<sup>\*</sup> <p> Levering af sikre meddelelser kan være forsinket på grund af Pengeskab scanning af vedhæftede filer.|Gør modtagerne synlige for, at vedhæftede filer blev fjernet på grund af registreret malware.|
  |**Dynamisk levering**|Leverer meddelelser med det samme, men erstatter vedhæftede filer med pladsholdere, Pengeskab scanning af vedhæftede filer er fuldført. <p> Meddelelser, der indeholder skadelige vedhæftede filer, er sat i karantæne. Som standard er det kun administratorer (ikke brugere), der kan gennemse, frigive eller slette meddelelserne.<sup>\*</sup> <p> Du kan finde flere oplysninger [i afsnittet Dynamisk levering Pengeskab politikker for vedhæftede](#dynamic-delivery-in-safe-attachments-policies) filer senere i denne artikel.|Undgå forsinkelser i meddelelser, mens du beskytter modtagere mod skadelige filer.|

  <sup>\*</sup>Administratorer kan oprette og _tildele karantænepolitikker_ i Pengeskab Politikker for vedhæftede filer, der definerer, hvad brugere har tilladelse til at gøre til meddelelser, der er sat i karantæne. Du kan få mere at vide under [Karantænepolitikker](quarantine-policies.md).

- **Omdiriger** vedhæftet fil ved registrering: Aktivér omdirigering og Send den vedhæftede fil til følgende **mailadresse: For** handlinger til  **blokering, overvågning** eller erstat skal du sende meddelelser, der indeholder vedhæftede malwares, til den angivne interne eller eksterne mailadresse til analyse og undersøgelse.

  Det anbefales, at du bruger standardindstillinger og faste politikindstillinger til at aktivere omdirigering. Du kan finde flere oplysninger [under Pengeskab Indstillinger for vedhæftede filer](recommended-settings-for-eop-and-office365.md#safe-attachments-settings).

- **Anvend** ovenstående valg, hvis malwarescanning for vedhæftede filer får timeud, eller der opstår en fejl: Den handling, der er angivet af Pengeskab Vedhæftede filer ukendt **malwaresvar**, udføres på meddelelser, selvom Pengeskab Scanning af vedhæftede filer ikke kan fuldføres. Vælg altid denne indstilling, hvis du vælger **Aktivér omdirigering**. Ellers kan meddelelser gå tabt.

- **Modtagerfiltre**: Du skal angive modtagerbetingelser og undtagelser, der bestemmer, hvem politikken gælder for. Du kan bruge disse egenskaber til betingelser og undtagelser:
  - **Modtageren er**
  - **Modtagerdomænet er**
  - **Modtageren er medlem af**

  Du kan kun bruge en betingelse eller undtagelse én gang, men betingelsen eller undtagelsen kan indeholde flere værdier. Flere værdier af samme betingelse eller undtagelse bruger ELLER-logik (f.eks. _\<recipient1\>_ eller _\<recipient2\>_). Forskellige betingelser eller undtagelser bruger AND-logik (f.eks. _\<recipient1\>_ og _\<member of group 1\>_).

- **Prioritet**: Hvis du opretter flere politikker, kan du angive den rækkefølge, de anvendes i. Der er ikke to politikker, der kan have samme prioritet, og behandling af politikker stopper, når den første politik er anvendt.

  Du kan finde flere oplysninger om rangordenen, og hvordan flere politikker evalueres og anvendes, i Rækkefølge [og prioriteret mailbeskyttelse](how-policies-and-protections-are-combined.md).

### <a name="dynamic-delivery-in-safe-attachments-policies"></a>Dynamisk levering i Pengeskab politikker for vedhæftede filer

> [!NOTE]
> Dynamisk levering fungerer kun for Exchange Online postkasser.

Handlingen Dynamisk levering i Pengeskab politikker for vedhæftede filer søger at fjerne eventuelle forsinkelser i levering af mail, der kan være forårsaget Pengeskab scanning af vedhæftede filer. Brødteksten i mailen leveres til modtageren med en pladsholder for hver vedhæftet fil. Pladsholderen forbliver, indtil den vedhæftede fil findes at være sikker, og derefter kan den vedhæftede fil åbnes eller downloades.

Hvis en vedhæftet fil findes skadelig, er meddelelsen sat i karantæne.

De fleste PDF-filer Office dokumenter kan gennemses i fejlsikret tilstand, Pengeskab scanning af vedhæftede filer er i gang. Hvis en vedhæftet fil ikke er kompatibel med Dynamic Delivery Previewer, får modtagerne vist en pladsholder for den vedhæftede fil, Pengeskab scanning af vedhæftede filer er fuldført.

Hvis du bruger en mobilenhed, og PDF-filer ikke gengives i Dynamic Delivery Previewer på din mobilenhed, kan du prøve at åbne meddelelsen i Outlook på internettet (tidligere kaldet Outlook Web App) ved hjælp af din mobilbrowser.

Her er nogle overvejelser i forbindelse med Dynamisk levering og videresendte meddelelser:

- Hvis den videresendte modtager er beskyttet af en Pengeskab politik for vedhæftede filer, der bruger indstillingen Dynamisk levering, får modtageren vist pladsholderen med mulighed for at få vist kompatible filer.
- Hvis den videresendte modtager ikke er beskyttet af en Pengeskab Politik for vedhæftede filer, leveres meddelelsen og de vedhæftede filer uden nogen Pengeskab Scanning af vedhæftede filer eller pladsholdere for vedhæftede filer.

Der er scenarier, hvor Dynamisk levering ikke kan erstatte vedhæftede filer i meddelelser. Disse scenarier omfatter:

- Meddelelser i offentlige mapper.
- Meddelelser, der sendes ud af og derefter tilbage til en brugers postkasse ved hjælp af brugerdefinerede regler.
- Meddelelser, der flyttes (automatisk eller manuelt) ud af postkasser i skyen til andre placeringer, herunder arkivmapper.
- Indbakkeregler flytter meddelelsen ud af indbakken til en anden mappe.
- Slettede meddelelser.
- Brugerens søgemappe i postkassen er i fejltilstand.
- Exchange Online organisationer, hvor Exclaimer er aktiveret. Du kan finde en løsning på dette [problem under KB4014438](https://support.microsoft.com/help/4014438).
- [S/MIME)](/exchange/security-and-compliance/smime-exo/smime-exo) krypterede meddelelser.
- Du har konfigureret handlingen Dynamisk levering i en politik for vedhæftede filer i Pengeskab, men modtageren understøtter ikke dynamisk levering (f.eks. er modtageren en postkasse i en lokal Exchange organisation). Links [Pengeskab i Microsoft Defender for Office 365](set-up-safe-links-policies.md) kan imidlertid scanne vedhæftede filer Office, der indeholder URL-adresser (afhængigt af, hvordan de [globale indstillinger for Pengeskab Links er](configure-global-settings-for-safe-links.md) konfigureret).

## <a name="submitting-files-for-malware-analysis"></a>Sende filer til malwareanalyse

- Hvis du modtager en fil, du vil sende til analyse hos Microsoft, skal du se [Sende malware og ikke-malware til Microsoft til analyse](submitting-malware-and-non-malware-to-microsoft-for-analysis.md).
- Hvis du modtager en mail (med eller uden en vedhæftet fil), som du vil sende til analyse hos Microsoft, skal du se Rapportér [meddelelser og filer til Microsoft](report-junk-email-messages-to-microsoft.md).
