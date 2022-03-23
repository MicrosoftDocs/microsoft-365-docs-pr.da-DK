---
title: Gennemse hændelser og fejl ved hjælp af Logvisning
description: Få beskrivelser og yderligere fejlfindingstrin (hvis det er nødvendigt) for alle hændelser, der rapporteres af Microsoft Defender for Endpoint-tjenesten.
keywords: fejlfinding, logvisning, oversigt over log, fejlkode, mislykket, Microsoft Defender til slutpunktstjeneste, kan ikke starte, brydes, kan ikke starte
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.date: 05/21/2018
ms.technology: mde
ms.openlocfilehash: a09f034ac35aa3380ea834eafc149eaad9a7cb3d
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/24/2021
ms.locfileid: "63591926"
---
# <a name="review-events-and-errors-using-event-viewer"></a>Gennemse hændelser og fejl ved hjælp af Logvisning

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**
- Log over begivenheder
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-enablesiem-abovefoldlink)

Du kan gennemse begivenheds-i-fremviseren [på](https://msdn.microsoft.com/library/aa745633(v=bts.10).aspx) individuelle enheder.

Hvis enheder f.eks. ikke vises på listen **Enheder, skal** du muligvis se efter hændelses-id'er på enhederne. Du kan derefter bruge denne tabel til at fastlægge yderligere fejlfindingstrin.

**Åbn Logbog, og find hændelsesloggen for Microsoft Defender for Endpoint-tjenesten:**

1. Klik **på Start** på Windows, skriv Log **på, og** tryk på **Enter**.

2. Rul ned under Logoversigt **på loglisten**, indtil du ser **Microsoft-Windows-SENSE/Operational**. Dobbeltklik på elementet for at åbne logfilen.

   Du kan også få adgang til logfilen ved at udvide **Program- og tjenestelogfiler** \> **Microsoft** \> **Windows** \> **SENSE** og klikke på **Drift**.

   > [!NOTE]
   > SENSE er det interne navn, der bruges til at referere til den funktionalitets sensor, der bruges til at styrke Microsoft Defender til slutpunkt.

3. Hændelser, der er registreret af tjenesten, vises i logfilen. Se følgende tabel for at få en liste over hændelser, der er registreret af tjenesten.

   <br>

   ****

   |Hændelses-id|Meddelelse|Beskrivelse|Handling|
   |---|---|---|---|
   |1|Microsoft Defender for Endpoint-tjenesten startet (Version `variable`).|Sker under systemstart, lukning og under onboarding.|Meddelelse om normal drift. ingen handling påkrævet.|
   |2|Lukning af Microsoft Defender for Endpoint-tjenesten.|Sker, når enheden lukkes eller er slukket.|Meddelelse om normal drift. ingen handling påkrævet.|
   |3|Tjenesten Microsoft Defender for Endpoint kunne ikke starte. Fejlkode: `variable`.|Tjenesten blev ikke startet.|Gennemse andre meddelelser for at finde mulige årsager og fejlfindingstrin.|
   |4|Microsoft Defender for Endpoint-tjenesten kontaktede serveren på `variable`.|Variabel = URL-adressen på Defender for endpoint-behandlingsservere. <p> Denne URL-adresse stemmer overens med den, der kan ses i firewallen eller netværksaktiviteten.|Meddelelse om normal drift. ingen handling påkrævet.|
   |5|Tjenesten Microsoft Defender for Endpoint kunne ikke oprette forbindelse til serveren på `variable`.|Variabel = URL-adressen på Defender for endpoint-behandlingsservere. <p> Tjenesten kunne ikke kontakte de eksterne behandlingsservere på den pågældende URL-adresse.|Kontrollér forbindelsen til URL-adressen. Se [Konfigurere proxy og internetforbindelse](configure-proxy-internet.md).|
   |6|Microsoft Defender til slutpunktstjenesten er ikke onboardet, og der blev ikke fundet nogen onboardingparametre.|Enheden blev ikke installeret korrekt og rapporterer ikke til portalen.|Onboarding skal køres, før tjenesten startes. <p> Kontrollér, at onboardingindstillingerne og scriptene er installeret korrekt. Prøv at geninstallere konfigurationspakkerne. <p> Se [Onboard Windows 10-enheder](configure-endpoints.md).|
   |7|Microsoft Defender for Endpoint-tjenesten kunne ikke læse onboardingparametrene. Fejl: `variable`.|Variabel = detaljeret fejlbeskrivelse. Enheden blev ikke installeret korrekt og rapporterer ikke til portalen.|Kontrollér, at onboardingindstillingerne og scriptene er installeret korrekt. Prøv at geninstallere konfigurationspakkerne. <p> Se [Onboard Windows 10-enheder](configure-endpoints.md).|
   |8|Tjenesten Microsoft Defender for Endpoint kunne ikke rydde konfigurationen. Fejlkode: `variable`.|**Under onboarding:** Tjenesten kunne ikke rydde konfigurationen under onboarding. Onboardingprocessen fortsætter. <p> **Under offboarding:** Tjenesten kunne ikke rydde konfigurationen under offboarding. Offboarding-processen er afsluttet, men tjenesten fortsætter med at køre.|**Onboarding:** Ingen handling påkrævet. <p> **Offboarding:** Genstart systemet. <p> Se [Onboard Windows 10-enheder](configure-endpoints.md).|
   |9|Tjenesten Microsoft Defender for Endpoint kunne ikke ændre starttypen. Fejlkode: `variable`.|**Under onboarding:** Enheden blev ikke installeret korrekt og rapporterer ikke til portalen. <p>**Under offboarding:** Tjenestens starttype kunne ikke ændres. Offboarding-processen fortsætter. |Kontrollér, at onboardingindstillingerne og scriptene er installeret korrekt. Prøv at geninstallere konfigurationspakkerne. <p> Se [Onboard Windows 10-enheder](configure-endpoints.md).|
   |10|Microsoft Defender for Endpoint-tjenesten kunne ikke bevare onboardingoplysningerne. Fejlkode: `variable`.|Enheden blev ikke installeret korrekt og rapporterer ikke til portalen.|Kontrollér, at onboardingindstillingerne og scriptene er installeret korrekt. Prøv at geninstallere konfigurationspakkerne. <p> Se [Onboard Windows 10-enheder](configure-endpoints.md).|
   |11|Onboarding eller gen-onboarding af Defender for Endpoint-tjenesten fuldført.|Enheden er onboardet korrekt.|Meddelelse om normal drift. ingen handling påkrævet. <p> Det kan tage flere timer, før enheden vises i portalen.|
   |12|Microsoft Defender til Slutpunkt kunne ikke anvende standardkonfigurationen.|Tjenesten kunne ikke anvende standardkonfigurationen.|Denne fejl bør blive løst efter en kort tidsperiode.|
   |13|Microsoft Defender for endpoint-enheds-id beregnet: `variable`.|Normal driftsproces.|Meddelelse om normal drift. ingen handling påkrævet.|
   |15|Microsoft Defender til Slutpunkt kan ikke starte kommandokanal med URL: `variable`.|Variabel = URL-adressen på Defender for endpoint-behandlingsservere. <p> Tjenesten kunne ikke kontakte de eksterne behandlingsservere på den pågældende URL-adresse.|Kontrollér forbindelsen til URL-adressen. Se [Konfigurere proxy og internetforbindelse](configure-proxy-internet.md).|
   |17|Tjenesten Microsoft Defender for Endpoint kunne ikke ændre placeringen af forbundne brugeroplevelser og telemetritjenesten. Fejlkode: `variable`.|Der opstod en fejl med Windows-telemetritjenesten.|[Sørg for, at den diagnostiske datatjeneste](troubleshoot-onboarding.md#ensure-that-microsoft-defender-antivirus-is-not-disabled-by-a-policy) er >Sørg for, at den diagnostiske datatjeneste er aktiveret. <p> Kontrollér, at onboardingindstillingerne og scriptene er installeret korrekt. Prøv at geninstallere konfigurationspakkerne. <p> Se [Onboard Windows 10-enheder](configure-endpoints.md).|
   |18|OOBE (Windows Velkommen) er fuldført.|Tjenesten starter først, når Windows opdateringer er installeret.|Meddelelse om normal drift. ingen handling påkrævet.|
   |19|OOBE (Windows Velkommen) er endnu ikke fuldført.|Tjenesten starter først, når Windows opdateringer er installeret.|Meddelelse om normal drift. ingen handling påkrævet. <p> Hvis denne fejl fortsætter efter en genstart af systemet, skal du sikre dig, Windows alle opdateringer er installeret fuldt ud.|
   |20|Der kan ikke ventes på, at OOBE (Windows Velkommen) er fuldført. Fejlkode: `variable`.|Intern fejl.|Hvis denne fejl fortsætter efter en genstart af systemet, skal du sikre dig, Windows alle opdateringer er installeret fuldt ud.|
   |25|Microsoft Defender for Endpoint-tjenesten kunne ikke nulstille tilstandsstatus i registreringsdatabasen. Fejlkode: `variable`.|Enheden blev ikke installeret korrekt. Den rapporterer til portalen, men tjenesten vises muligvis ikke som registreret i SCCM eller registreringsdatabasen.|Kontrollér, at onboardingindstillingerne og scriptene er installeret korrekt. Prøv at geninstallere konfigurationspakkerne. <p> Se [Onboard Windows 10-enheder](configure-endpoints.md).|
   |26|Microsoft Defender for Endpoint-tjenesten kunne ikke angive onboardingstatus i registreringsdatabasen. Fejlkode: `variable`.|Enheden blev ikke installeret korrekt. <p> Den rapporterer til portalen, men tjenesten vises muligvis ikke som registreret i SCCM eller registreringsdatabasen.|Kontrollér, at onboardingindstillingerne og scriptene er installeret korrekt. Prøv at geninstallere konfigurationspakkerne. <p> Se [Onboard Windows 10-enheder](configure-endpoints.md).|
   |27|Tjenesten Microsoft Defender for Endpoint kunne ikke aktivere SENSE-bevidst tilstand i Microsoft Defender Antivirus. Onboardingprocessen mislykkedes. Fejlkode: `variable`.|Normalt vil Microsoft Defender Antivirus angive en særlig passiv tilstand, hvis et andet antimalwareprodukt i realtid kører korrekt på enheden, og enheden rapporterer til Defender til Slutpunkt.|Kontrollér, at onboardingindstillingerne og scriptene er installeret korrekt. Prøv at geninstallere konfigurationspakkerne. <p> Se [Onboard Windows 10-enheder](configure-endpoints.md). <p> Sørg for, at antimalwarebeskyttelse i realtid kører korrekt.|
   |28|Registrering af Microsoft Defender for brugeroplevelser og telemetritjeneste forbundet med slutpunkt mislykkedes. Fejlkode: `variable`.|Der opstod en fejl med Windows-telemetritjenesten.|[Sørg for, at den diagnostiske datatjeneste er aktiveret](troubleshoot-onboarding.md#ensure-that-microsoft-defender-antivirus-is-not-disabled-by-a-policy). <p> Kontrollér, at onboardingindstillingerne og scriptene er installeret korrekt. Prøv at geninstallere konfigurationspakkerne. <p> Se [Onboard Windows 10-enheder](configure-endpoints.md).|
   |29|Kunne ikke læse offboarding-parametrene. Fejltype: %1, fejlkode: %2, Beskrivelse: %3|Denne hændelse sker, når systemet ikke kan læse offboardingparametrene.|Kontrollér, at enheden har internetadgang, og kør derefter hele offboarding-processen igen. Sørg for, at offboarding-pakken ikke er udløbet.|
   |30|Tjenesten Microsoft Defender for Endpoint kunne ikke deaktivere SENSE-klar tilstand i Microsoft Defender Antivirus. Fejlkode: `variable`.|Normalt vil Microsoft Defender Antivirus angive en særlig passiv tilstand, hvis et andet antimalwareprodukt i realtid kører korrekt på enheden, og enheden rapporterer til Defender til Slutpunkt.|Kontrollér, at onboardingindstillingerne og scriptene er installeret korrekt. Prøv at geninstallere konfigurationspakkerne. <p> Se [Onboard Windows 10-enheder](configure-endpoints.md). <p> Sørg for, at antimalwarebeskyttelse i realtid kører korrekt.|
   |31|Microsoft Defender for brugeroplevelser forbundet med slutpunkt og fjern telemetritjeneste mislykkedes. Fejlkode: `variable`.|Der opstod en fejl Windows fjerntelemetritjenesten under onboarding. Offboarding-processen fortsætter.|[Kontrollér for fejl med Windows-telemetritjenesten](troubleshoot-onboarding.md#ensure-the-diagnostic-data-service-is-enabled).|
   |32|Microsoft Defender for Endpoint-tjenesten kunne ikke anmode om at stoppe sig selv efter offboarding-processen. Fejlkode: %1|Der opstod en fejl under offboarding.|Genstart enheden.|
   |33|Microsoft Defender for Endpoint-tjenesten kunne ikke bevare SENSE GUID. Fejlkode: `variable`.|En entydig identifier bruges til at repræsentere hver enhed, der rapporterer til portalen. <p> Hvis identifikatoren ikke bevares, kan den samme enhed blive vist to gange i portalen.|Kontrollér registreringsdatabasetilladelserne på enheden for at sikre, at tjenesten kan opdatere registreringsdatabasen.|
   |34|Tjenesten Microsoft Defender for Endpoint kunne ikke tilføje sig selv som en afhængighed af tjenesten Forbundne brugeroplevelser og -telemetri, hvilket medførte, at onboardingprocessen mislykkedes. Fejlkode: `variable`.|Der opstod en fejl med Windows-telemetritjenesten.|[Sørg for, at den diagnostiske datatjeneste er aktiveret](troubleshoot-onboarding.md#ensure-that-microsoft-defender-antivirus-is-not-disabled-by-a-policy). <p> Kontrollér, at onboardingindstillingerne og scriptene er installeret korrekt. Prøv at geninstallere konfigurationspakkerne. <p> Se [Onboard Windows 10-enheder](configure-endpoints.md).|
   |35|Tjenesten Microsoft Defender for Endpoint kunne ikke fjerne sig selv som en afhængighed af tjenesten Forbundne brugeroplevelser og -telemetri. Fejlkode: `variable`.|Der opstod en fejl Windows fjerntelemetritjenesten under offboarding. Offboarding-processen fortsætter.|Kontrollér for fejl med Windows diagnostiske datatjeneste.|
   |36|Registrering af Microsoft Defender for brugeroplevelser og telemetritjeneste forbundet med slutpunkt lykkedes. Fuldførelseskode: `variable`.|Registrering af Defender til slutpunkt med forbundne brugeroplevelser og telemetritjeneste fuldført.|Meddelelse om normal drift. ingen handling påkrævet.|
   |37|Microsoft Defender til slutpunkt Et modul er ved at overskride sin kvote. Modul: %1, Kvote: {%2} {%3}, Procentdel af kvoteudnyttelse: %4.|Enheden har næsten brugt den tildelte kvote for det aktuelle 24-timers vindue. Det er ved at blive begrænser.|Meddelelse om normal drift. ingen handling påkrævet.|
   |38|Netværksforbindelsen er identificeret som lav. Microsoft Defender til Slutpunkt kontakter serveren hvert %1 minut. Forbrugsafsluttet forbindelse: %2, tilgængelig via internettet: %3, gratis tilgængeligt netværk: %4.|Enheden bruger et forbrugsaf betalt netværk og kontakter serveren mindre ofte.|Meddelelse om normal drift. ingen handling påkrævet.|
   |39|Netværksforbindelsen identificeres som normalt. Microsoft Defender til Slutpunkt kontakter serveren hvert %1 minut. Forbrugsafsluttet forbindelse: %2, tilgængelig via internettet: %3, gratis tilgængeligt netværk: %4.|Enheden bruger ikke en forbrugsaf betalt forbindelse og kontakter serveren som normalt.|Meddelelse om normal drift. ingen handling påkrævet.|
   |40|Batteritilstanden er identificeret som lav. Microsoft Defender til Slutpunkt kontakter serveren hvert %1 minut. Batteritilstand: %2.|Enheden har for lav batteriniveau og kontakter serveren mindre ofte.|Meddelelse om normal drift. ingen handling påkrævet.|
   |41|Batteritilstanden identificeres som normal. Microsoft Defender til Slutpunkt kontakter serveren hvert %1 minut. Batteritilstand: %2.|Enheden har ikke for lavt batteriniveau og kontakter serveren som normalt.|Meddelelse om normal drift. ingen handling påkrævet.|
   |42|Microsoft Defender for Endpoint-komponenten kunne ikke udføre handlingen. Komponent: %1, Handling: %2, Undtagelsestype: %3, undtagelsesmeddelelse: %4|Intern fejl. Tjenesten kunne ikke startes.|Hvis fejlen fortsætter, skal du kontakte Support.|
   |43|Microsoft Defender for Endpoint-komponenten kunne ikke udføre handlingen. Komponent: %1, Handling: %2, Undtagelsestype: %3, undtagelsesfejl: %4, undtagelsesmeddelelse: %5|Intern fejl. Tjenesten kunne ikke startes.|Hvis fejlen fortsætter, skal du kontakte Support.|
   |44|Offboarding af Defender for Endpoint-tjenesten fuldført.|Tjenesten blev deaktiveret.|Meddelelse om normal drift. ingen handling påkrævet.|
   |45|Det lykkedes ikke at registrere og starte hændelsessporingssessionen [%1]. Fejlkode: %2|Der opstod en fejl ved start af tjenesten under oprettelse af etw-session. Dette forårsagede en fejl ved start af tjenesten.|Hvis fejlen fortsætter, skal du kontakte Support.|
   |46|Kunne ikke registreres og starte hændelsessporingssessionen [%1] på grund af manglende ressourcer. Fejlkode: %2. Dette er højst sandsynligt, fordi der er for mange aktive hændelsessporingssessioner. Tjenesten forsøges igen om 1 minut.|Der opstod en fejl ved start af tjenesten under oprettelse af etw-session på grund af manglende ressourcer. Tjenesten er startet og kører, men rapporterer ikke nogen sensorhændelse, før ETW-sessionen er startet.|Meddelelse om normal drift. ingen handling påkrævet. Tjenesten forsøger at starte sessionen hvert minut.|
   |47|Registrerede og startede hændelsessporingssessionen – gendannet efter tidligere mislykkede forsøg.|Denne hændelse følger den forrige begivenhed efter korrekt start af ETW-sessionen.|Meddelelse om normal drift. ingen handling påkrævet.|
   |48|Det lykkedes ikke at føje en udbyder [%1] til hændelsessporingssessionen [%2]. Fejlkode: %3. Det betyder, at hændelser fra denne udbyder ikke rapporteres.|Det lykkedes ikke at føje en udbyder til ETW-sessionen. Derfor rapporteres providerhændelser ikke.|Kontrollér fejlkoden. Hvis fejlen fortsætter, skal du kontakte Support.|
   |49|Kommandoen Ugyldig skykonfiguration modtaget og ignoreret. Version: %1, status: %2, fejlkode: %3, meddelelse: %4|Modtaget en ugyldig konfigurationsfil fra den skybaserede tjeneste, der blev ignoreret.|Hvis fejlen fortsætter, skal du kontakte Support.|
   |50|Ny skykonfiguration er anvendt korrekt. Version: %1.|En ny konfiguration fra skytjenesten er blevet anvendt.|Meddelelse om normal drift. ingen handling påkrævet.|
   |51|Ny skykonfiguration kunne ikke anvendes, version: %1. Den senest kendte gode konfiguration, version %2, er blevet anvendt.|En forkert konfigurationsfil fra skytjenesten er modtaget. Sidst kendte fredsstillende konfiguration blev anvendt.|Hvis fejlen fortsætter, skal du kontakte Support.|
   |52|Ny skykonfiguration kunne ikke anvendes, version: %1. Det lykkedes heller ikke at anvende den senest kendte konfiguration, version %2. Standardkonfigurationen er blevet anvendt.|En forkert konfigurationsfil fra skytjenesten er modtaget. Den senest kendte  gode konfiguration kunne ikke anvendes, og standardkonfigurationen blev anvendt.|Tjenesten vil forsøge at hente en ny konfigurationsfil inden for 5 minutter. Hvis du ikke kan se begivenhed #50 – kontakt Support.|
   |53|Skykonfiguration indlæst fra fast lager, version: %1.|Konfigurationen blev indlæst fra et fast lager ved start af tjenesten.|Meddelelse om normal drift. ingen handling påkrævet.|
   |55|Autologgeret Secure ETW kunne ikke oprettes. Fejlkode: %1|Der kunne ikke oprettes en sikker ETW-logger.|Genstart enheden. Hvis fejlen fortsætter, skal du kontakte Support.|
   |56|Autologgeret Secure ETW blev ikke fjernet. Fejlkode: %1|Kunne ikke fjerne den sikre ETW-session ved offboarding.|Kontakt support.|
   |57|Tage et øjebliksbillede af computeren til fejlfindingsformål.|En undersøgelsespakke, også kendt som den såkaldte informationspakke, indsamles.|Meddelelse om normal drift. ingen handling påkrævet.|
   |59|Startkommando: %1|Startende udførelse af kommandoen Svar.|Meddelelse om normal drift. ingen handling påkrævet.|
   |60|Kommandoen %1 kunne ikke køres, fejl: %2.|Kommandoen Svar kunne ikke udføres.|Hvis fejlen fortsætter, skal du kontakte Support.|
   |61|Kommandoparametre til dataindsamling er ugyldige: SasUri: %1, compressionLevel: %2.|Det lykkedes ikke at læse eller fortolke kommandoargumenterne for dataindsamling (ugyldige argumenter).|Hvis fejlen fortsætter, skal du kontakte Support.|
   |62|Forbundne brugeroplevelser og telemetritjeneste kunne ikke startes. Fejlkode: %1|Forbundne brugeroplevelser og telemetritjeneste (diagtrack) kunne ikke starte. Ikke-Microsoft Defender til slutpunkt-telemetri sendes ikke fra denne computer.|Se efter flere tip til fejlfinding i hændelsesloggen: Microsoft-Windows-UniversalTelemetryClient/Operational.|
   |63|Opdaterer starttypen for den eksterne tjeneste. Navn: %1, faktisk starttype: %2, forventet starttype: %3, udgangskode: %4|Den opdaterede starttype for den eksterne tjeneste.|Meddelelse om normal drift. ingen handling påkrævet.|
   |64|Starter stoppet ekstern tjeneste. Navn: %1, udgangskode: %2|Starte en ekstern tjeneste.|Meddelelse om normal drift. ingen handling påkrævet.|
   |65|Minifilterdriveren Microsoft Security Events Component kunne ikke indlæses. Fejlkode: %1|Kunne ikke indlæse MsSecFlt.sys filesystem-minifilter.|Genstart enheden. Hvis fejlen fortsætter, skal du kontakte Support.|
   |66|Opdatering af politik: Ventetidstilstand - %1|Politikken C&C-forbindelsesfrekvens er blevet opdateret.|Meddelelse om normal drift. ingen handling påkrævet.|
   |68|Tjenestens starttype er uventet. Tjenestenavn: %1, faktisk starttype: %2, forventet starttype: %3|Uventet starttype for eksterne tjenester.|Ret starttypen for den eksterne tjeneste.|
   |69|Tjenesten er stoppet. Tjenestenavn: %1|Den eksterne tjeneste er stoppet.|Start den eksterne tjeneste.|
   |70|Opdatering af politik: Tillad indsamling af eksempler - %1|Eksempel på en samlingspolitik blev opdateret.|Meddelelse om normal drift. ingen handling påkrævet.|
   |71|Kommandoen Kunne køres: %1|Kommandoen blev udført korrekt.|Meddelelse om normal drift. ingen handling påkrævet.|
   |72|Forsøgte at sende den første rapport over hele maskinprofilen. Resultatkode: %1|Kun til orientering.|Meddelelse om normal drift. ingen handling påkrævet.|
   |73|Sense start for platform: %1|Kun til orientering.|Meddelelse om normal drift. ingen handling påkrævet.|
   |74|Enhedskoden i registreringsdatabasen overskrider længdegrænsen. Kodenavn: %2. Længdegrænse: %1.|Enhedskoden overskrider længdegrænsen.|Brug et kortere enhedsmærke.|
   |81|Kunne ikke oprette Microsoft Defender for Endpoint ETW autologger. Fejlkode: %1|Sessionen ETW kunne ikke oprettes.|Genstart enheden. Hvis fejlen fortsætter, skal du kontakte Support.|
   |82|Kunne ikke fjerne Microsoft Defender for Endpoint ETW autologger. Fejlkode: %1|EtW-sessionen kunne ikke slettes.|Kontakt support.|
   |84|Indstil Windows Defender Antivirus køretilstand. Tving til passiv tilstand: %1, resultatkode: %2.|Indstille tilstanden Defender Running (aktiv eller passiv).|Meddelelse om normal drift. ingen handling påkrævet.|
   |85|Kunne ikke udløse eksekverbar Microsoft Defender til slutpunkt. Fejlkode: %1|Stjernemarkering af eksekverbar SenseIR mislykkedes.|Genstart enheden. Hvis fejlen fortsætter, skal du kontakte Support.|
   |86|Hvis du starter igen, stoppes en ekstern tjeneste, der skulle være oppe. Navn: %1, udgangskode: %2|Start den eksterne tjeneste igen.|Meddelelse om normal drift. ingen handling påkrævet.|
   |87|Den eksterne tjeneste kan ikke startes. Navn: %1|Den eksterne tjeneste kunne ikke startes.|Kontakt support.|
   |88|Opdaterer starttypen for den eksterne tjeneste igen. Navn: %1, faktisk starttype: %2, forventet starttype: %3, udgangskode: %4|Starttypen for den eksterne tjeneste blev opdateret.|Meddelelse om normal drift. ingen handling påkrævet.|
   |89|Starttypen for den eksterne tjeneste kan ikke opdateres. Navn: %1, faktisk starttype: %2, forventet starttype: %3|Starttypen for den eksterne tjeneste kan ikke opdateres.|Kontakt support.|
   |90|Det lykkedes ikke at konfigurere System Guard Runtime Monitor til at oprette forbindelse til skytjenesten i geo-region %1. Fejlkode: %2|System Guard Runtime Monitor sender ikke data til skytjenesten.|Kontrollér tilladelserne for registerstien: "HKLM\Software\Microsoft\Windows\CurrentVersion\Sgrm". Hvis der ikke er problemer, skal du kontakte Support.|
   |91|System Guard Runtime Monitor-geoområdeoplysninger blev ikke fjernet. Fejlkode: %1|System Guard Runtime Monitor sender ikke data til skytjenesten.|Kontrollér tilladelserne for registerstien: "HKLM\Software\Microsoft\Windows\CurrentVersion\Sgrm". Hvis der ikke er problemer, skal du kontakte Support.|
   |92|Stopper afsendelse af cyberdatakvote for sensor, fordi datakvoten overskrides. Genoptager afsendelse, når kvoteperioden er passeret. Tilstandsmaske: %1|Overgå begrænsningsgrænsen.|Meddelelse om normal drift. ingen handling påkrævet.|
   |93|Genoptager afsendelse af cyberdata for sensor. Tilstandsmaske: %1|Genoptag indsendelse af cyberdata.|Meddelelse om normal drift. ingen handling påkrævet.|
   |94|Eksekverbar Microsoft Defender til slutpunkt er startet|Den eksekverbare SenseCE er startet.|Meddelelse om normal drift. ingen handling påkrævet.|
   |95|Eksekverbar Microsoft Defender til slutpunkt er afsluttet|Den eksekverbare SenseCE er afsluttet.|Meddelelse om normal drift. ingen handling påkrævet.|
   |96|Microsoft Defender for Endpoint Init har ringet op. Resultatkode: %2|Den eksekverbare SenseCE har kaldt MCE-initialisering.|Meddelelse om normal drift. ingen handling påkrævet.|
   |97|Der er forbindelsesproblemer med skyen for DLP-scenariet|Der er problemer med netværksforbindelsen, der påvirker DLP-klassificeringsflowet.|Kontrollér netværksforbindelsen.|
   |98|Forbindelsen til skyen for DLP-scenariet er blevet genoprettet|Forbindelsen til netværket blev genoprettet, og DLP-klassificeringsflowet kan fortsætte.|Meddelelse om normal drift. ingen handling påkrævet.|
   |99|Sense er stødt på følgende fejl under kommunikation med serveren: (%1). Resultat: (%2)|Der opstod en kommunikationsfejl.|Kontrollér følgende hændelser i hændelsesloggen for at få flere oplysninger.|
   |100|Eksekverbar Microsoft Defender til slutpunkt kunne ikke starte. Fejlkode: %1|Den eksekverbare SenseCE-fejl kunne ikke starte.|Genstart enheden. Hvis fejlen fortsætter, skal du kontakte Support.|
   |102|Microsoft Defender til netværksregistrering på slutpunkt og eksekverbar svar er startet|Den eksekverbare SenseNdr er startet.|Meddelelse om normal drift. ingen handling påkrævet.|
   |103|Microsoft Defender til netværksregistrering på slutpunkt og eksekverbar svar er ophørt|Den eksekverbare SenseNdr-kant er afsluttet.|Meddelelse om normal drift. ingen handling påkrævet.|
   |

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-eventerrorcodes-belowfoldlink)

## <a name="see-also"></a>Se også
- [Onboard Windows 10 enheder](configure-endpoints.md)
- [Konfigurere indstillinger for enhedsproxy og internetforbindelse](configure-proxy-internet.md)
- [Fejlfinding af Microsoft Defender til slutpunkt](troubleshoot-onboarding.md)
- [Oversigt over klientanalyse](overview-client-analyzer.md)
- [Download og kør klientanalyse](download-client-analyzer.md)
- [Forstå HTML-analyserapporten](analyzer-report.md)