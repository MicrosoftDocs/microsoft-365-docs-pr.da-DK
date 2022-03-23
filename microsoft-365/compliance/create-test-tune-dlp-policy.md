---
title: Opret, test og finjuster en DLP-politik
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: article
f1_keywords:
- ms.o365.cc.NewPolicyFromTemplate
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MET150
ms.custom:
- seo-marvel-mar2020
ms.assetid: 59414438-99f5-488b-975c-5023f2254369
description: I denne artikel lærer du, hvordan du opretter, tester og finjusterer en DLP-politik efter virksomhedens behov.
ms.openlocfilehash: cc31d067eaf2684c17a09d7b2731a5cc3500af76
ms.sourcegitcommit: 99067d5eb1fa7b094e7cdb1f7be65acaaa235a54
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/29/2022
ms.locfileid: "63587273"
---
# <a name="create-test-and-tune-a-dlp-policy"></a>Opret, test og finjuster en DLP-politik

Forebyggelse af datatab (DLP) hjælper dig med at forhindre utilsigtet eller utilsigtet deling af følsomme oplysninger.

DLP undersøger mails og filer for følsomme oplysninger, f.eks. et kreditkortnummer. Ved hjælp af DLP kan du registrere følsomme oplysninger og gøre noget som f.eks.:

- Logfør hændelsen med overvågningsformål
- Vise en advarsel til den slutbruger, der sender mailen eller deler filen
- Bloker aktivt mail- eller fildeling fra at finde sted

## <a name="permissions"></a>Tilladelser

Medlemmer af dit overholdelsesteam, der opretter DLP-politikker, skal have tilladelse til Overholdelsescenter. Som standard har din lejeradministrator adgang til at give dem, der er dem, der overholder regler og standarder, adgang. Følg disse trin:
  
1. Opret en gruppe i Microsoft 365 og tilføj compliance officers til den.
    
2. Opret en rollegruppe på siden **Tilladelser i** Security &amp; Compliance Center. 

3. Når du opretter rollegruppen, skal du bruge **sektionen Vælg** roller for at føje følgende rolle til rollegruppen: **DLP-overholdelsesstyring**.
    
4. Brug sektionen **Vælg medlemmer** for at tilføje den Microsoft 365 gruppe, du har oprettet før, til rollegruppen.

Brug rollen **View-Only DLP Compliance Management** til at oprette en rollegruppe med visningsrettigheder til DLP-politikker og DLP-rapporter.

Få mere at vide under [Giv brugere adgang til Office 365 Overholdelsescenter](../security/office-365-security/grant-access-to-the-security-and-compliance-center.md).
  
Disse tilladelser er nødvendige for at oprette og anvende en DLP-politik for ikke at gennemtvinge politikker.

### <a name="roles-and-role-groups-in-preview"></a>Roller og rollegrupper i forhåndsvisning

Eksempelvisningen har roller og rollegrupper, som du kan teste for at finjustere dine adgangskontrolelementer.

Her er en liste over de Microsoft Information Protection (MIP)-roller, der er i forhåndsvisning. Du kan få mere at vide om [dem under Roller i & Security & Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center)

- Administratoren for informationsbeskyttelse
- Information Protection-analytiker
- Information Protection Investigator
- Information Protection Reader

Her er en liste over MIP-rollegrupper, der er i forhåndsvisning. Du kan få mere at [vide under Rollegrupper i & Security & Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#role-groups-in-the-security--compliance-center)

- Beskyttelse af oplysninger
- Administratorer for informationsbeskyttelse
- Information Protection-analytikere
- Beskyttelse af oplysninger
- Læsere til informationsbeskyttelse

## <a name="how-sensitive-information-is-detected-by-dlp"></a>Sådan registreres følsomme oplysninger af DLP

DLP finder følsomme oplysninger ved brug af regulære udtryk (RegEx) matchning i kombination med andre indikatorer, f.eks. hvor tæt visse nøgleord ligger på de matchende mønstre. Et VISA-kreditkortnummer har f.eks. 16 cifre. Men disse cifre kan skrives på forskellige måder, f.eks. 1111-1111-1111-1111, 1111 1111 1111 1111 eller 1111111111111111.

En hvilken som helst 16-cifret streng er ikke nødvendigvis et kreditkortnummer, det kan være et billetnummer fra et helpdesksystem eller et serienummer på en hardware. For at skelne mellem et kreditkortnummer og en uskadelig 16-cifret streng udføres der en beregning (kontrolsum) for at bekræfte, at tallene svarer til et kendt mønster fra de forskellige kreditkortmærker.

Hvis DLP finder nøgleord som "VISA" eller "AMEX", nær datoværdier, der kan være udløbsdatoen for kreditkortet, bruger DLP også disse data til at afgøre, om strengen er et kreditkortnummer eller ej.

Med andre ord er DLP smart nok til at genkende forskellen mellem disse to tekststrenge i en mail:

- "Kan du bestille en ny bærbar computer til mig. Brug mit VISA-nummer 1111-1111-1111-1111, udløber 22-11-22, og send mig den anslåede leveringsdato, når du har den."
- "Serienummeret for min bærbare computer er 2222-2222-2222-2222, og det blev købt den 2010-11-2010. Af den måde, er mit rejsevisum godkendt endnu?"

Se [Enhedsdefinitioner af typen Følsomme oplysninger](sensitive-information-type-entity-definitions.md) , der forklarer, hvordan hver oplysningstype registreres.

## <a name="where-to-start-with-data-loss-prevention"></a>Hvor starter jeg med forebyggelse af datatab?

Når risikoen for lækage af data ikke er helt indlysende, er det svært at finde ud af, hvor præcis du skal starte med implementering af DLP. Heldigvis kan DLP-politikker køres i "testtilstand", så du kan måle deres effektivitet og nøjagtighed, før du aktiverer dem.

DLP-politikker for Exchange Online administreres via Exchange Administration. Men du kan konfigurere DLP-politikker for alle arbejdsbelastninger via Security & Compliance Center, så det er, hvad jeg vil bruge til demonstrationer i denne artikel. I Security & Compliance Center kan du finde DLP-politikkerne under **Politik til forebyggelse af datatab** > . Vælg **Opret en politik for** at starte.

Microsoft 365 indeholder en række [DLP-politikskabeloner, du](what-the-dlp-policy-templates-include.md) kan bruge til at oprette politikker. Lad os sige, at du er en australsk virksomhed. Du kan filtrere skabelonerne i Australien og vælge Finansiel, Medicinsk og Sundhed og Beskyttelse af personlige oplysninger.

![Mulighed for at vælge land eller område.](../media/DLP-create-test-tune-choose-country.png)

Til denne demonstration vælger jeg Australske personidentificerbare oplysninger (PII)-data, som indeholder oplysningstyperne for det australske skattefilnummer (TFN) og kørekortnummeret.

![Mulighed for at vælge en politikskabelon.](../media/DLP-create-test-tune-choose-policy-template.png)

Giv din nye DLP-politik et navn. Standardnavnet matcher skabelonen DLP-politik, men du skal vælge dit eget mere beskrivende navn, da der kan oprettes flere politikker fra den samme skabelon.

![Mulighed for at navngive din politik.](../media/DLP-create-test-tune-name-policy.png)

Vælg de placeringer, som politikken skal gælde for. DLP-politikker kan gælde for Exchange Online, SharePoint Online og OneDrive for Business. Jeg vil lade denne politik være konfigureret til at gælde for alle placeringer.

![Mulighed for at vælge alle placeringer.](../media/DLP-create-test-tune-choose-locations.png)

I det første **politiktrin Indstillinger** du blot acceptere standardindstillingerne for nu. Du kan tilpasse DLP-politikker, men standarderne er et fint sted at starte.

![Indstillinger til tilpasning af den type indhold, der skal beskyttes.](../media/DLP-create-test-tune-default-customization-settings.png)

Når du har klikket på Næste**, får du vist en mere **Indstillinger med flere** tilpasningsmuligheder. Hvis du skal bruge en politik, som du kun tester, kan du begynde at foretage nogle justeringer her.

- Jeg har slået politiktip fra for nu, hvilket er et fornuftigt trin at tage, hvis du blot tester ting og ikke vil vise noget til brugerne endnu. Politiktip viser advarsler til brugere om, at de er ved at overtræde en DLP-politik. Eksempelvis får en Outlook vist en advarsel om, at den fil, brugeren har vedhæftet, indeholder kreditkortnumre og medfører, at brugerens mail afvises. Formålet med politiktip er at stoppe den ikke-kompatible funktionsmåde, før den sker.
- Jeg har også reduceret antallet af forekomster fra 10 til 1, så denne politik vil registrere enhver deling af australske PII-data, ikke kun massedeling af data.
- Jeg har også føjet en anden modtager til mailen med hændelsesrapporten.

![Yderligere politikindstillinger.](../media/DLP-create-test-tune-more-policy-settings.png)

Endelig har jeg konfigureret denne politik til i første omgang at køre i testtilstand. Bemærk, at der også er en mulighed her for at deaktivere politiktip, mens du er i testtilstand. Dette giver dig fleksibiliteten til at have politiktip aktiveret i politikken, men beslutter derefter, om du vil vise eller undertrykke dem under din test.

![Mulighed for at teste politikken først.](../media/DLP-create-test-tune-test-mode.png)

Klik på Opret på det sidste skærmbillede for **gennemsyn for** at afslutte oprettelsen af politikken.

## <a name="test-a-dlp-policy"></a>Test en DLP-politik

Du kan vente og vente på, at politikken udløses af normal brugeraktivitet, eller du kan prøve at udløse den selv. Tidligere sammenkædede jeg med [enhedsdefinitioner af typen](sensitive-information-type-entity-definitions.md) Følsomme oplysninger, som giver dig oplysninger om, hvordan du udløser DLP-matches.

Som et eksempel vil DLP-politikken, jeg har oprettet til denne artikel, registrere australske skattefilnumre (TFN). Ifølge dokumentationen er matchet baseret på følgende kriterier.

![Dokumentation om Australiens skattefilnummer.](../media/DLP-create-test-tune-Australia-Tax-File-Number-doc.png)
 
For at demonstrere TFN-registrering på en ret god måde, vil en mail med ordene "Momsfilnummer" og en nicifret streng i nærheden blive sejlet igennem uden problemer. Årsagen til, at den ikke udløser DLP-politikken, er, at den nicifrede streng skal bestå den kontrolsum, der angiver, at det er en gyldig TFN og ikke kun en uskadelig streng af tal.

![Australiens skattefilnummer, der ikke består checksum.](../media/DLP-create-test-tune-email-test1.png)

Til sammenligning vil en mail med ordene "Skattefilnummer" og et gyldigt TFN, der består kontrolsummet, udløse politikken. For posten her er den TFN, jeg bruger, blevet taget fra et websted, der genererer gyldige, men ikke ægte, TFN'er. Sådanne websteder er nyttige, fordi en af de mest almindelige fejl, når du tester en DLP-politik, bruger et falsk tal, der ikke er gyldigt og ikke består kontrolsummet (og udløser derfor ikke politikken).

![Australiens skattefilnummer, der består kontrolsummet.](../media/DLP-create-test-tune-email-test2.png)

Hændelsesrapportens mail indeholder typen af følsomme oplysninger, der blev registreret, hvor mange forekomster der blev registreret, og registreringsniveauet.

![Hændelsesrapport, der viser det registrerede momsfilnummer.](../media/DLP-create-test-tune-email-incident-report.png)

Hvis du lader din DLP-politik stå i testtilstand og analyserer mails om hændelsesrapport, kan du begynde at få en fornemmelse for nøjagtigheden af DLP-politikken, og hvor effektiv den vil være, når den håndhæves. Ud over hændelsesrapporter kan du bruge [DLP-rapporterne](view-the-dlp-reports.md) til at få vist en samlet visning af politik match på tværs af din lejer.

## <a name="tune-a-dlp-policy"></a>Finjustere en DLP-politik

Når du analyserer dine politikhits, kan det være en ide at foretage nogle justeringer af, hvordan politikkerne fungerer. Som et enkelt eksempel kan du afgøre, at en TFN i en mail ikke er et problem (jeg tror, at det stadig er, men lad os fortsætte med det for at få demonstrationen), men to eller flere forekomster er et problem. Flere forekomster kan være et risikabelt scenarie, f.eks. at en medarbejder sender en CSV-eksport via mail fra HR-databasen til en ekstern part, f.eks. en ekstern regnskabstjeneste. Bestemt noget, du foretrækker at registrere og blokere.

I Overholdelsescenter kan du redigere en eksisterende politik for at justere funktionsmåden.

![Mulighed for at redigere politik.](../media/DLP-create-test-tune-edit-policy.png)
 
Du kan justere placeringsindstillingerne, så politikken kun anvendes på bestemte arbejdsbelastninger eller på bestemte websteder og konti.

![Indstillinger til at vælge bestemte placeringer.](../media/DLP-create-test-tune-edit-locations.png)

Du kan også justere politikindstillingerne og redigere reglerne, så de passer bedre til dine behov.

![Mulighed for at redigere regel.](../media/DLP-create-test-tune-edit-rule.png)

Når du redigerer en regel i en DLP-politik, kan du ændre:

- Betingelserne, herunder typen og antallet af forekomster af følsomme data, der udløser reglen.
- De handlinger, der er foretaget, f.eks begrænse adgang til indholdet.
- Brugermeddelelser, som er politiktip, der vises til brugeren i sin mailklient eller webbrowser.
- Brugertilsidesættelser bestemmer, om brugerne kan vælge at fortsætte med deres mail eller fildeling alligevel.
- Hændelsesrapporter for at underrette administratorer.

![Indstillinger til redigering af dele af en regel.](../media/DLP-create-test-tune-editing-options.png)

I denne demonstration har jeg føjet brugermeddelelser til politikken (vær forsigtig med at gøre dette uden tilstrækkelig undervisning i brugerindsigt) og tilladt brugerne at tilsidesætte politikken med en forretningsberettigelse eller ved at markere den som en falsk positiv. Du kan også tilpasse teksten med tip til mail og politik, hvis du vil medtage yderligere oplysninger om organisationens politikker, eller du kan bede brugerne om at kontakte support, hvis de har spørgsmål.

![Indstillinger for brugerbeskeder og tilsidesættelser.](../media/DLP-create-test-tune-user-notifications.png)

Politikken indeholder to regler for håndtering af høj lydstyrke og lav lydstyrke, så sørg for at redigere begge med de ønskede handlinger. Dette er en mulighed for at behandle sager forskelligt afhængigt af deres karakteristika. Du kan f.eks. tillade tilsidesættelser ved lav volumen, men ikke tillade tilsidesættelser ved brud på store mængder.

![En regel for høj lydstyrke og én regel for lav lydstyrke.](../media/DLP-create-test-tune-two-rules.png)

Hvis du faktisk vil blokere eller begrænse adgangen til indhold, der overtræder politikken, skal du konfigurere en handling på reglen for at gøre det.

![Mulighed for at begrænse adgangen til indhold.](../media/DLP-create-test-tune-restrict-access-action.png)

Når jeg har gemt disse ændringer i politikindstillingerne, skal jeg også vende tilbage til siden med hovedindstillinger for politikken og aktivere muligheden for at vise politiktip til brugere, mens politikken er i testtilstand. Dette er en effektiv metode til at introducere DLP-politikker til dine slutbrugere og kursus i brugerindsigt uden at risikere for mange falske positive, der påvirker deres produktivitet.

![Mulighed for at vise politiktip i testtilstand.](../media/DLP-create-test-tune-show-policy-tips.png)

På serversiden (eller skysiden, hvis du foretrækker det), træder ændringen muligvis ikke i kraft med det samme på grund af forskellige behandlingsintervaller. Hvis du foretager en DLP-politikændring, der viser nye politiktip til en bruger, kan brugeren muligvis ikke se ændringerne i kraft straks i deres Outlook-klient, som kontrollerer, om politikken ændres en gang i døgnet. Hvis du vil sætte fart på test, kan du bruge denne rettelse i registreringsdatabasen til at fjerne det seneste tidsstempel fra [PolicyNudges-tasten](https://support.microsoft.com/en-au/help/2823261/changes-to-a-data-loss-prevention-policy-don-t-take-effect-in-outlook?__hstc=18650278.46377037dc0a82baa8a30f0ef07a7b2f.1538687978676.1538693509953.1540315763430.3&__hssc=18650278.1.1540315763430&__hsfp=3446956451). Outlook downloader de nyeste politikoplysninger, næste gang du genstarter den og begynder at skrive en mail.

Hvis du har aktiveret politiktip, begynder brugeren at se tip i en Outlook og kan rapportere falske positive til dig, når de forekommer.

![Politiktip med mulighed for at rapportere falsk positiv.](../media/DLP-create-test-tune-policy-tip-in-outlook.png)

## <a name="investigate-false-positives"></a>Undersøg falske positive

DLP-politikskabeloner er ikke perfekte direkte ud af feltet. Det er sandsynligt, at du vil finde nogle falske positive, der forekommer i dit miljø, hvilket er grunden til, at det er så vigtigt at gøre det nemmere for dig at finde en DLP-installation og bruge tid på at teste og finjustere dine politikker.

Her er et eksempel på en falsk positiv. Denne mail er helt uskadelig. Brugeren leverer mobiltelefonnummeret til en person, herunder dennes mailsignatur.

![Mail, der viser falske positive oplysninger.](../media/DLP-create-test-tune-false-positive-email.png)
 
Men brugeren får vist et politiktip, der advarer dem om, at mailen indeholder følsomme oplysninger, specifikt en australsk kørekortnummer.

![Mulighed for at rapportere falsk positiv i politiktip.](../media/DLP-create-test-tune-policy-tip-closeup.png)

Brugeren kan rapportere den falske positive, og administratoren kan undersøge, hvorfor det er sket. I hændelsesrapportens mail markeres mailen som en falsk positiv.

![Hændelsesrapport, der viser falsk positiv.](../media/DLP-create-test-tune-false-positive-incident-report.png)

Dette kørekort er et godt eksempel at se på. Årsagen til, at denne falske positive er opstået, er, at typen "Australsk kørekort" udløses af en 9-cifret streng (selv en, der er en del af en 10-cifret streng), inden for 300 tegn afstand til nøgleordene "Sydney nsw" (der er ikke store og små bogstaver). Så den udløses af telefonnummeret og mailsignaturen, kun fordi brugeren befinder sig i Sydney.


En mulighed er at fjerne den australske kørekortoplysningerstype fra politikken. Det er her, fordi det er en del af skabelonen DLP-politik, men vi er ikke nødt til at bruge den. Hvis du kun er interesseret i momsfilnumre og ikke kørekort, kan du bare fjerne dem. Du kan f.eks. fjerne den fra reglen om lav volumen i politikken, men lade den være i reglen om stor volumen, så lister over flere kørelicenser stadig registreres.
 
En anden mulighed er at øge antallet af forekomster, så en lav mængde af kørekort kun registreres, når der er flere forekomster.

![Mulighed for at redigere antallet af forekomster.](../media/DLP-create-test-tune-edit-instance-count.png)

Ud over at ændre antallet af forekomster kan du også justere matchnøjagtigheden (eller tillidsniveauet). Hvis din type af følsomme oplysninger har flere mønstre, kan du justere matchnøjagtigheden i reglen, så reglen kun matcher bestemte mønstre. Hvis du f.eks. vil reducere falske positive, kan du angive reglens nøjagtighed, så den kun matcher mønsteret med det højeste tillidsniveau. Du kan finde flere oplysninger om tillidsniveauer under [Sådan bruges tillidsniveau til at finjustere dine regler](data-loss-prevention-policies.md#match-accuracy).

Hvis du vil være endnu mere avanceret, kan du tilpasse en hvilken som helst type af følsomme oplysninger – du kan f.eks. fjerne "Sydney NSW" fra listen over [nøgleord til](sensitive-information-type-entity-definitions.md#australia-drivers-license-number) Australiens kørekortnummer for at fjerne den falske positive, der er udløst ovenfor. Hvis du vil lære, hvordan du gør dette ved hjælp af XML og PowerShell, skal du se tilpasse [en indbygget følsom oplysningstype](customize-a-built-in-sensitive-information-type.md).

## <a name="turn-on-a-dlp-policy"></a>Slå en DLP-politik til

Når du er tilfreds med, at din DLP-politik registrerer følsomme oplysningstyper præcist og effektivt, og at dine slutbrugere er klar til at tage sig af de politikker, der er på plads, kan du aktivere politikken.

![Indstilling til at aktivere politik.](../media/DLP-create-test-tune-turn-on-policy.png)
 
Hvis du venter på at se, hvornår politikken træder i kraft, [skal du Forbind til Security & Compliance Center PowerShell](/powershell/exchange/connect-to-scc-powershell) og køre [cmdlet'en Get-DlpCompliancePolicy](/powershell/module/exchange/get-dlpcompliancepolicy) for at få vist DistributionStatus.

 ```powershell
 Get-DlpCompliancePolicy "Testing -Australia PII" -DistributionDetail | Select distributionstatus
 ```
Når du har slår DLP-politikken til, skal du køre nogle endelige test selv for at sikre, at de forventede politikhandlinger udføres. Hvis du forsøger at teste ting som kreditkortdata, er der websteder online med oplysninger om, hvordan du opretter et eksempel på et kreditkort eller andre personlige oplysninger, der passerer kontrolsum og udløser dine politikker.

Politikker, der tillader brugertilsidesættelser, viser denne indstilling for brugeren som en del af politiktip.

![Politiktip, der tillader brugertilsidesættelse.](../media/DLP-create-test-tune-override-option.png)

Politikker, der begrænser indhold, viser advarslen for brugeren som en del af politiktiplen og forhindrer brugeren i at sende mailen.

![Politiktip om, at indhold er begrænset.](../media/DLP-create-test-tune-restrict-warning.png)

## <a name="summary"></a>Oversigt

Politikker til forebyggelse af datatab er nyttige for organisationer af alle typer. Test af nogle DLP-politikker er en øvelse med lav risiko, da du har kontrol over ting som politiktip, slutbrugerens tilsidesættelser og hændelsesrapporter. Du kan stille og roligt teste nogle DLP-politikker for at se, hvilke typer overtrædelser der allerede forekommer i organisationen, og derefter udforme politikker med lave falske positive satser, informere brugerne om, hvad der er tilladt og ikke tilladt, og derefter udrulle dine DLP-politikker til organisationen.
