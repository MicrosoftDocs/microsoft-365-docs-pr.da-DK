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
description: I denne artikel lærer du, hvordan du opretter, tester og finjusterer en DLP-politik i henhold til dine organisatoriske behov.
ms.openlocfilehash: 605288d5ee2839cc2f3ec225e551f0ba3e65bfcc
ms.sourcegitcommit: 6a981ca15bac84adbbed67341c89235029aad476
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/27/2022
ms.locfileid: "65753986"
---
# <a name="create-test-and-tune-a-dlp-policy"></a>Opret, test og finjuster en DLP-politik

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Microsoft Purview Forebyggelse af datatab (DLP) hjælper dig med at forhindre utilsigtet eller utilsigtet deling af følsomme oplysninger.

DLP undersøger mails og filer for følsomme oplysninger, f.eks. et kreditkortnummer. Ved hjælp af DLP kan du registrere følsomme oplysninger og udføre handlinger som:

- Logfør hændelsen med henblik på overvågning
- Vis en advarsel til den slutbruger, der sender mailen eller deler filen
- Bloker aktivt mail- eller fildelingen fra at foregå

## <a name="permissions"></a>Tilladelser

Medlemmer af dit overholdelsesteam, der skal oprette DLP-politikker, skal have tilladelser til Overholdelsescenter. Som standard kan din lejeradministrator få adgang til at give overholdelsesansvarlige og andre personer adgang. Følg disse trin:
  
1. Opret en gruppe i Microsoft 365, og føj overholdelsesansvarlige til den.
    
2. Opret en rollegruppe på siden **Tilladelser** i Microsoft Purview-compliance-portal. 

3. Når du opretter rollegruppen, skal du bruge afsnittet **Vælg roller** til at føje følgende rolle til rollegruppen: **DLP Compliance Management**.
    
4. Brug afsnittet **Vælg medlemmer** til at føje den Microsoft 365 gruppe, du oprettede før, til rollegruppen.

Brug rollen **Vis kun DLP-overholdelsesstyring** til at oprette en rollegruppe med skrivebeskyttede rettigheder til DLP-politikker og DLP-rapporter.

Du kan få flere oplysninger under [Giv brugere adgang til Office 365 Compliance Center](../security/office-365-security/grant-access-to-the-security-and-compliance-center.md).
  
Disse tilladelser kræves for at oprette og anvende en DLP-politik for ikke at gennemtvinge politikker.

### <a name="roles-and-role-groups-in-preview"></a>Roller og rollegrupper som prøveversion

Der er roller og rollegrupper som prøveversion, som du kan teste for at finjustere dine adgangskontrolelementer.

Her er en liste over relevante roller, der findes som prøveversion. Hvis du vil vide mere om dem, skal du se [Roller i Security & Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center)

- Information Protection Administration
- Information Protection analytiker
- Information Protection investigator
- Information Protection-læser

Her er en liste over relevante rollegrupper, der findes som prøveversion. Du kan få mere at vide under [Rollegrupper i Security & Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#role-groups-in-the-security--compliance-center)

- Information Protection
- Information Protection administratorer
- Information Protection analytikere
- Information Protection efterforskere
- Information Protection læsere

## <a name="how-sensitive-information-is-detected-by-dlp"></a>Sådan registreres følsomme oplysninger af DLP

DLP finder følsomme oplysninger ved at matche mønstre med regulære udtryk (RegEx) sammen med andre indikatorer, f.eks. nærhed af visse nøgleord til de matchende mønstre. Et VISA-kreditkortnummer har f.eks. 16 cifre. Men disse cifre kan skrives på forskellige måder, f.eks. 1111-1111-1111-1111, 1111 1111 1111 1111 eller 1111111111111111.

En hvilken som helst 16-cifret streng er ikke nødvendigvis et kreditkortnummer, det kan være et billetnummer fra et helpdesk-system eller et serienummer for et stykke hardware. For at se forskellen mellem et kreditkortnummer og en harmløs 16-cifret streng udføres der en beregning (kontrolsum) for at bekræfte, at tallene stemmer overens med et kendt mønster fra de forskellige kreditkortmærker.

Hvis DLP finder nøgleord som f.eks. "VISA" eller "AMEX", nær datoværdier, der kan være udløbsdatoen for kreditkortet, bruger DLP også disse data som en hjælp til at afgøre, om strengen er et kreditkortnummer eller ej.

DLP er med andre ord smart nok til at genkende forskellen mellem disse to tekststrenge i en mail:

- "Kan du bestille mig en ny bærbar. Brug mit VISA nummer 1111-1111-1111-1111, udløbsdato 11/22, og send mig den anslåede leveringsdato, når du har det."
- "Min laptop serienummer er 2222-2222-2222-2222, og det blev købt på 11/2010. Af den måde, er mit visum godkendt endnu?"

Se [Objektdefinitioner for følsomme oplysninger,](sensitive-information-type-entity-definitions.md) der forklarer, hvordan hver oplysningstype registreres.

## <a name="where-to-start-with-data-loss-prevention"></a>Her skal du starte med forebyggelse af datatab

Når risikoen for datalækage ikke er helt indlysende, er det svært at se, præcis hvor du skal starte med at implementere DLP. Heldigvis kan DLP-politikker køres i "testtilstand", så du kan måle deres effektivitet og nøjagtighed, før du slår dem til.

DLP-politikker for Exchange Online kan administreres via Exchange Administration. Men du kan konfigurere DLP-politikker for alle arbejdsbelastninger via Microsoft Purview-compliance-portal, så det er det, jeg skal bruge til demonstrationer i denne artikel. I Microsoft Purview-compliance-portal finder du DLP-politikkerne under **Politik til** **forebyggelse af** >  datatab. Vælg **Opret en politik** for at starte.

Microsoft 365 indeholder en række [DLP-politikskabeloner](what-the-dlp-policy-templates-include.md), som du kan bruge til at oprette politikker. Lad os sige, at du er en australsk virksomhed. Du kan filtrere skabelonerne i Australien og vælge Økonomi, Medicinsk og Sundhed og Beskyttelse af personlige oplysninger.

![Mulighed for at vælge land eller område.](../media/DLP-create-test-tune-choose-country.png)

Til denne demonstration vælger jeg personidentificerbare oplysninger (Australian Personligt identificerbare oplysninger), som indeholder oplysningstyperne for TFN (Australian Tax File Number) og driverens licensnummer.

![Mulighed for at vælge en politikskabelon.](../media/DLP-create-test-tune-choose-policy-template.png)

Navngiv din nye DLP-politik. Standardnavnet svarer til DLP-politikskabelonen, men du bør vælge dit eget mere beskrivende navn, da der kan oprettes flere politikker ud fra den samme skabelon.

![Mulighed for at navngive politikken.](../media/DLP-create-test-tune-name-policy.png)

Vælg de placeringer, som politikken skal gælde for. DLP-politikker kan gælde for Exchange Online, SharePoint Online og OneDrive for Business. Jeg vil lade denne politik være konfigureret til at gælde for alle placeringer.

![Mulighed for at vælge alle placeringer.](../media/DLP-create-test-tune-choose-locations.png)

Ved det første **Indstillinger** trin for Politik skal du blot acceptere standardindstillingerne for nu. Du kan tilpasse DLP-politikker, men standardværdierne er et fint sted at starte.

![Indstillinger for tilpasning af den type indhold, der skal beskyttes.](../media/DLP-create-test-tune-default-customization-settings.png)

Når du har klikket på Næste,** får du vist en side med flere **indstillinger for politik Indstillinger**. For en politik, som du kun tester, kan du begynde at foretage nogle justeringer her.

- Jeg har slået politiktips fra for nu, hvilket er et rimeligt skridt at tage, hvis du bare tester ting og ikke ønsker at vise noget til brugerne endnu. Politiktip viser advarsler til brugerne om, at de er ved at overtræde en DLP-politik. En Outlook bruger får f.eks. vist en advarsel om, at den fil, brugeren har vedhæftet, indeholder kreditkortnumre og medfører, at vedkommendes mail afvises. Målet med politiktips er at stoppe funktionsmåden, der ikke overholder angivne standarder, før det sker.
- Jeg har også reduceret antallet af forekomster fra 10 til 1, så denne politik registrerer enhver deling af australske PII-data og ikke kun massedeling af dataene.
- Jeg har også føjet en anden modtager til mailen med hændelsesrapporten.

![Yderligere politikindstillinger.](../media/DLP-create-test-tune-more-policy-settings.png)

Til sidst har jeg konfigureret denne politik til at køre i testtilstand i starten. Bemærk, at der også er en mulighed her for at deaktivere politiktips i testtilstand. Dette giver dig fleksibiliteten til at aktivere politiktips i politikken, men derefter beslutte, om du vil vise eller undertrykke dem under din test.

![Mulighed for at teste politikken først.](../media/DLP-create-test-tune-test-mode.png)

Klik på **Opret** på den endelige gennemgangsskærm for at afslutte oprettelsen af politikken.

## <a name="test-a-dlp-policy"></a>Test en DLP-politik

Du kan sidde og vente på, at politikken udløses af normal brugeraktivitet, eller du kan prøve at udløse den selv. Tidligere linkde jeg til [objektdefinitioner for følsomme oplysninger](sensitive-information-type-entity-definitions.md), som giver dig oplysninger om, hvordan du udløser DLP-matches.

Som et eksempel vil den DLP-politik, jeg har oprettet for denne artikel, registrere australske skattefilnumre (TFN). Ifølge dokumentationen er kampen baseret på følgende kriterier.

![Dokumentation om Australiens skattefilnummer.](../media/DLP-create-test-tune-Australia-Tax-File-Number-doc.png)
 
For at demonstrere TFN-registrering på en ret stump måde vil en mail med ordene "Skattefilnummer" og en nicifret streng i nærheden sejle igennem uden problemer. Årsagen til, at den ikke udløser DLP-politikken, er, at den nicifrede streng skal bestå kontrolsummen, der angiver, at det er et gyldigt TFN og ikke kun en harmløs streng af tal.

![Det australske skattefilnummer, der ikke består kontrolsummen.](../media/DLP-create-test-tune-email-test1.png)

Til sammenligning udløser en mail med ordene "Skattefilnummer" og et gyldigt TFN, der består kontrolsummen, politikken. For posten her, TFN jeg bruger blev taget fra et websted, der genererer gyldige, men ikke ægte, TFN'er. Sådanne websteder er nyttige, fordi en af de mest almindelige fejl, når du tester en DLP-politik, bruger et falsk tal, der ikke er gyldigt, og som ikke består kontrolsummen (og derfor ikke udløser politikken).

![Det australske skattefilnummer, der passerer kontrolsummen.](../media/DLP-create-test-tune-email-test2.png)

Mailen med hændelsesrapporten indeholder den type følsomme oplysninger, der blev registreret, hvor mange instanser der blev registreret, og registreringens konfidensniveau.

![Hændelsesrapport, der viser det registrerede skattefilnummer.](../media/DLP-create-test-tune-email-incident-report.png)

Hvis du lader din DLP-politik være i testtilstand og analyserer mails om hændelsesrapporten, kan du begynde at få en fornemmelse af nøjagtigheden af DLP-politikken, og hvor effektiv den vil være, når den håndhæves. Ud over hændelsesrapporterne kan du [bruge DLP-rapporterne](view-the-dlp-reports.md) til at se en samlet visning af politikforekomster på tværs af din lejer.

## <a name="tune-a-dlp-policy"></a>Juster en DLP-politik

Når du analyserer dine politikhits, kan det være en god idé at foretage nogle justeringer af den måde, politikkerne fungerer på. Som et simpelt eksempel kan du fastslå, at et TFN i en e-mail ikke er et problem (jeg tror, det stadig er, men lad os gå med det af hensyn til demonstration), men to eller flere tilfælde er et problem. Flere forekomster kan være et risikabelt scenarie, f.eks. en medarbejder, der sender en CSV-eksport fra HR-databasen til en ekstern part, f.eks. en ekstern regnskabstjeneste. Bestemt noget, du foretrækker at opdage og blokere.

I Overholdelsescenter kan du redigere en eksisterende politik for at justere funktionsmåden.

![Mulighed for at redigere politik.](../media/DLP-create-test-tune-edit-policy.png)
 
Du kan justere placeringsindstillingerne, så politikken kun anvendes på bestemte arbejdsbelastninger eller på bestemte websteder og konti.

![Indstillinger for at vælge bestemte placeringer.](../media/DLP-create-test-tune-edit-locations.png)

Du kan også justere politikindstillingerne og redigere reglerne, så de passer bedre til dine behov.

![Mulighed for at redigere regel.](../media/DLP-create-test-tune-edit-rule.png)

Når du redigerer en regel i en DLP-politik, kan du ændre:

- Betingelserne, herunder typen og antallet af forekomster af følsomme data, der udløser reglen.
- De handlinger, der udføres, f.eks. begrænsning af adgang til indholdet.
- Brugermeddelelser, som er politiktip, der vises for brugeren i deres mailklient eller webbrowser.
- Bruger tilsidesætter bestemmer, om brugerne kan vælge at fortsætte med deres mail- eller fildeling alligevel.
- Hændelsesrapporter for at give administratorer besked.

![Indstillinger for redigering af dele af en regel.](../media/DLP-create-test-tune-editing-options.png)

Til denne demonstration har jeg føjet brugermeddelelser til politikken (vær forsigtig med at gøre dette uden tilstrækkelig oplæring i brugeroplysning) og tilladt brugerne at tilsidesætte politikken med en forretningsberettigelse eller ved at markere den som falsk positiv. Du kan også tilpasse teksten til mail- og politiktip, hvis du vil medtage yderligere oplysninger om organisationens politikker, eller bede brugerne om at kontakte support, hvis de har spørgsmål.

![Indstillinger for brugermeddelelser og tilsidesættelser.](../media/DLP-create-test-tune-user-notifications.png)

Politikken indeholder to regler for håndtering af høj og lav lydstyrke, så sørg for at redigere begge med de ønskede handlinger. Dette er en mulighed for at behandle sager forskelligt afhængigt af deres egenskaber. Du kan f.eks. tillade tilsidesættelser i forbindelse med overtrædelser af begrænset volumen, men ikke tillade tilsidesættelser for overtrædelser af stor mængde.

![Én regel for høj volumen og én regel for lav volumen.](../media/DLP-create-test-tune-two-rules.png)

Hvis du rent faktisk vil blokere eller begrænse adgangen til indhold, der er i strid med en politik, skal du konfigurere en handling for reglen for at gøre det.

![Mulighed for at begrænse adgangen til indhold.](../media/DLP-create-test-tune-restrict-access-action.png)

Når jeg har gemt disse ændringer af politikindstillingerne, skal jeg også vende tilbage til hovedindstillingssiden for politikken og aktivere muligheden for at få vist politiktip til brugere, mens politikken er i testtilstand. Dette er en effektiv måde at introducere DLP-politikker til dine slutbrugere på og udføre oplæring i brugeroplysning uden at risikere for mange falske positiver, der påvirker deres produktivitet.

![Mulighed for at få vist politiktip i testtilstand.](../media/DLP-create-test-tune-show-policy-tips.png)

På serversiden (eller cloudsiden, hvis du foretrækker det), træder ændringen muligvis ikke i kraft med det samme på grund af forskellige behandlingsintervaller. Hvis du foretager en DLP-politikændring, der viser nye politiktips til en bruger, kan brugeren muligvis ikke se ændringerne træde i kraft med det samme i deres Outlook klient, som kontrollerer, om der er ændringer i politikken hver 24. time. Hvis du vil sætte fart på testen, kan du bruge denne rettelse i registreringsdatabasen til at [rydde tidsstemplet for seneste download fra nøglen PolicyNudges](https://support.microsoft.com/en-au/help/2823261/changes-to-a-data-loss-prevention-policy-don-t-take-effect-in-outlook?__hstc=18650278.46377037dc0a82baa8a30f0ef07a7b2f.1538687978676.1538693509953.1540315763430.3&__hssc=18650278.1.1540315763430&__hsfp=3446956451). Outlook henter de nyeste politikoplysninger, næste gang du genstarter dem, og begynder at oprette en mail.

Hvis du har aktiveret politiktips, begynder brugeren at se tipene i Outlook og kan rapportere falske positiver til dig, når de opstår.

![Politiktip med mulighed for at rapportere falsk positiv.](../media/DLP-create-test-tune-policy-tip-in-outlook.png)

## <a name="investigate-false-positives"></a>Undersøg falske positiver

DLP-politikskabeloner er ikke perfekte lige fra kassen. Det er sandsynligt, at du finder nogle falske positiver i dit miljø, og derfor er det så vigtigt at lette din vej til en DLP-udrulning og tage dig tid til at teste og justere dine politikker korrekt.

Her er et eksempel på et falsk positivt. Denne mail er uskadelig. Brugeren giver sit mobiltelefonnummer til en person, og herunder deres e-mail-signatur.

![Mail, der viser falske positive oplysninger.](../media/DLP-create-test-tune-false-positive-email.png)
 
Men brugeren får vist et politiktip, der advarer dem om, at mailen indeholder følsomme oplysninger, specifikt et australsk kørekortsnummer.

![Mulighed for at rapportere falsk positiv i politiktip.](../media/DLP-create-test-tune-policy-tip-closeup.png)

Brugeren kan rapportere falsk positiv, og administratoren kan undersøge, hvorfor den er opstået. I mailen med hændelsesrapporten markeres mailen som falsk positiv.

![Hændelsesrapport, der viser falsk positiv.](../media/DLP-create-test-tune-false-positive-incident-report.png)

Denne driver licens sag er et godt eksempel til at grave ind. Denne falske positive er opstået, fordi typen "Australian Driver's License" udløses af en hvilken som helst 9-cifret streng (selv en streng, der er en del af en 10-cifret streng) inden for 300 tegn tæt på nøgleordene "Sydney nsw" (der skelnes ikke mellem store og små bogstaver). Så det udløses af telefonnummeret og mailsignaturen, kun fordi brugeren tilfældigvis er i Sydney.


Én mulighed er at fjerne oplysningstypen for den australske driverlicens fra politikken. Den er derinde, fordi den er en del af DLP-politikskabelonen, men vi er ikke tvunget til at bruge den. Hvis du kun er interesseret i skattefilnumre og ikke kørekort, kan du bare fjerne det. Du kan f.eks. fjerne den fra reglen for lav volumen i politikken, men lade den være i reglen om høj volumen, så der stadig registreres lister over flere driverlicenser.
 
En anden mulighed er at øge antallet af forekomster, så der kun registreres en lav mængde driverlicenser, når der er flere forekomster.

![Mulighed for at redigere antallet af forekomster.](../media/DLP-create-test-tune-edit-instance-count.png)

Ud over at ændre antallet af forekomster kan du også justere matchnøjagtigheden (eller konfidensniveauet). Hvis din følsomme oplysningstype har flere mønstre, kan du justere matchnøjagtigheden i din regel, så reglen kun matcher bestemte mønstre. For at hjælpe med at reducere falske positiver kan du f.eks. angive matchnøjagtigheden for din regel, så den kun matcher mønsteret med det højeste konfidensniveau. Du kan få flere oplysninger om tillidsniveauer under [Sådan bruger du tillidsniveauet til at justere dine regler](data-loss-prevention-policies.md#match-accuracy).

Endelig, hvis du vil have endnu en smule mere avanceret, kan du tilpasse enhver type følsomme oplysninger – du kan f.eks. fjerne "Sydney NSW" fra listen over nøgleord for [den australske drivers licensnummer](sensitive-information-type-entity-definitions.md#australia-drivers-license-number) for at fjerne det falske positive, der udløses ovenfor. Hvis du vil vide mere om, hvordan du gør dette ved hjælp af XML og PowerShell, skal du se [Tilpasning af en indbygget type følsomme oplysninger](customize-a-built-in-sensitive-information-type.md).

## <a name="turn-on-a-dlp-policy"></a>Slå en DLP-politik til

Når du er glad for, at din DLP-politik nøjagtigt og effektivt registrerer følsomme informationstyper, og at dine slutbrugere er klar til at håndtere de politikker, der er på plads, kan du aktivere politikken.

![Mulighed for at aktivere politik.](../media/DLP-create-test-tune-turn-on-policy.png)
 
Hvis du venter på at se, hvornår politikken træder i kraft, [skal du Forbind til Security & Compliance Center PowerShell](/powershell/exchange/connect-to-scc-powershell) og køre [cmdlet'en Get-DlpCompliancePolicy](/powershell/module/exchange/get-dlpcompliancepolicy) for at se DistributionStatus.

 ```powershell
 Get-DlpCompliancePolicy "Testing -Australia PII" -DistributionDetail | Select distributionstatus
 ```
Når du har aktiveret DLP-politikken, bør du køre nogle af dine egne endelige test for at sikre, at de forventede politikhandlinger forekommer. Hvis du forsøger at teste ting som kreditkortdata, er der websteder online med oplysninger om, hvordan du genererer eksempelkreditkort eller andre personlige oplysninger, der vil bestå kontrolsummen og udløse dine politikker.

Politikker, der tillader brugertilsidesættelser, præsenterer denne indstilling for brugeren som en del af politiktip.

![Politiktip, der tillader brugertilsidesættelse.](../media/DLP-create-test-tune-override-option.png)

Politikker, der begrænser indhold, viser advarslen til brugeren som en del af politiktip og forhindrer dem i at sende mailen.

![Politiktip om, at indholdet er begrænset.](../media/DLP-create-test-tune-restrict-warning.png)

## <a name="summary"></a>Oversigt

Politikker til forebyggelse af datatab er nyttige for organisationer af alle typer. Test af nogle DLP-politikker er en øvelse med lav risiko på grund af den kontrol, du har over ting som politiktips, tilsidesættelser af slutbrugere og hændelsesrapporter. Du kan stille og roligt teste nogle DLP-politikker for at se, hvilken type overtrædelser der allerede forekommer i din organisation, og derefter udforme politikker med lave falske positive satser, uddanne dine brugere i, hvad der er tilladt og ikke tilladt, og derefter udrulle dine DLP-politikker til organisationen.
