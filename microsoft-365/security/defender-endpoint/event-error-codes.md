---
title: Gennemse hændelser og fejl ved hjælp af Logbog
description: Få beskrivelser og yderligere fejlfindingstrin (hvis det er nødvendigt) for alle hændelser, der rapporteres af Microsoft Defender for Endpoint-tjenesten.
keywords: fejlfinding, Logbog, logoversigt, fejlkode, mislykket, Microsoft Defender for Endpoint tjeneste, kan ikke starte, brydes, kan ikke starte
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
ms.openlocfilehash: a598361851593fc84a06e9c4a1ef94e3ed6e1fba
ms.sourcegitcommit: bc35c7826e3403f259725ac72cca5bafd36aa56a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/30/2022
ms.locfileid: "66554285"
---
# <a name="review-events-and-errors-using-event-viewer"></a>Gennemse hændelser og fejl ved hjælp af Logbog

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**
- Logbog
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-enablesiem-abovefoldlink)

Du kan gennemse hændelses-id'er i [Logbog](https://msdn.microsoft.com/library/aa745633(v=bts.10).aspx) på individuelle enheder.

Hvis enheder f.eks. ikke vises på **listen Enheder**, skal du muligvis søge efter hændelses-id'er på enhederne. Du kan derefter bruge denne tabel til at bestemme yderligere fejlfindingstrin.

**Åbn Logbog, og find hændelsesloggen for Microsoft Defender for Endpoint-tjenesten:**

1. Klik på **Start** i Windows-menuen, skriv **Logbog**, og tryk på **Enter**.

2. På loglisten under **Logoversigt** skal du rulle, indtil du ser **Microsoft-Windows-SENSE/Operational**. Dobbeltklik på elementet for at åbne logfilen.

   Du kan også få adgang til logfilen ved at udvide **Program- og tjenestelogfiler** \> **Microsoft** \> **Windows** \> **SENSE** og klikke på **Handling**.

   > [!NOTE]
   > SENSE er det interne navn, der bruges til at referere til den adfærdssensor, der driver Microsoft Defender for Endpoint.

3. Hændelser, der er registreret af tjenesten, vises i logfilen. Se følgende tabel for at få vist en liste over hændelser, der er registreret af tjenesten.

   <br>

   ****

   |Hændelses-id|Meddelelse|Beskrivelse|Handling|
   |---|---|---|---|
   |1|Microsoft Defender for Endpoint tjeneste er startet (version `variable`).|Opstår under systemstart, lukning og onboarding.|Normal driftsmeddelelse; der kræves ingen handling.|
   |2|Microsoft Defender for Endpoint lukning af tjenesten.|Opstår, når enheden lukkes ned eller offboardes.|Normal driftsmeddelelse; der kræves ingen handling.|
   |3|Microsoft Defender for Endpoint tjenesten kunne ikke startes. Fejlkode: `variable`.|Tjenesten startede ikke.|Gennemse andre meddelelser for at finde mulige årsags- og fejlfindingstrin.|
   |4|Microsoft Defender for Endpoint tjeneste kontaktede serveren på `variable`.|Variabel = URL-adresse til Defender for Endpoint-behandlingsservere. <p> Denne URL-adresse svarer til den, der vises i firewall- eller netværksaktiviteten.|Normal driftsmeddelelse; der kræves ingen handling.|
   |5|Microsoft Defender for Endpoint-tjenesten kunne ikke oprette forbindelse til serveren på `variable`.|Variabel = URL-adresse til Defender for Endpoint-behandlingsservere. <p> Tjenesten kunne ikke kontakte de eksterne behandlingsservere på den pågældende URL-adresse.|Kontrollér forbindelsen til URL-adressen. Se [Konfigurer proxy og internetforbindelse](configure-proxy-internet.md).|
   |6|Microsoft Defender for Endpoint-tjenesten er ikke onboardet, og der blev ikke fundet nogen onboardingparametre.|Enheden blev ikke onboardet korrekt og rapporterer ikke til portalen.|Onboarding skal køres, før tjenesten startes. <p> Kontrollér, at onboardingindstillingerne og scripts er installeret korrekt. Prøv at geninstallere konfigurationspakkerne. <p> Se [Onboard Windows 10-enheder](configure-endpoints.md).|
   |7|Microsoft Defender for Endpoint-tjenesten kunne ikke læse onboardingparametrene. Fejl! `variable`.|Variabel = detaljeret fejlbeskrivelse. Enheden blev ikke onboardet korrekt og rapporterer ikke til portalen.|Kontrollér, at onboardingindstillingerne og scripts er installeret korrekt. Prøv at geninstallere konfigurationspakkerne. <p> Se [Onboard Windows 10-enheder](configure-endpoints.md).|
   |8|Microsoft Defender for Endpoint tjeneste kunne ikke rense konfigurationen. Fejlkode: `variable`.|**Under onboarding:** Tjenesten kunne ikke rense konfigurationen under onboarding. Onboardingprocessen fortsætter. <p> **Under offboarding:** Tjenesten kunne ikke rense konfigurationen under offboarding. Offboardingprocessen blev afsluttet, men tjenesten fortsætter med at køre.|**Onboarding:** Der kræves ingen handling. <p> **Offboarding:** Genstart systemet. <p> Se [Onboard Windows 10-enheder](configure-endpoints.md).|
   |9|Microsoft Defender for Endpoint tjeneste kunne ikke ændre starttypen. Fejlkode: `variable`.|**Under onboarding:** Enheden blev ikke onboardet korrekt og rapporterer ikke til portalen. <p>**Under offboarding:** Tjenestens starttype kunne ikke ændres. Offboarding-processen fortsætter. |Kontrollér, at onboardingindstillingerne og scripts er installeret korrekt. Prøv at geninstallere konfigurationspakkerne. <p> Se [Onboard Windows 10-enheder](configure-endpoints.md).|
   |10|Microsoft Defender for Endpoint-tjenesten kunne ikke bevare onboardingoplysningerne. Fejlkode: `variable`.|Enheden blev ikke onboardet korrekt og rapporterer ikke til portalen.|Kontrollér, at onboardingindstillingerne og scripts er installeret korrekt. Prøv at geninstallere konfigurationspakkerne. <p> Se [Onboard Windows 10-enheder](configure-endpoints.md).|
   |11|Onboarding eller gen onboarding af Defender for Endpoint-tjenesten er fuldført.|Enheden er onboardet korrekt.|Normal driftsmeddelelse; der kræves ingen handling. <p> Det kan tage flere timer, før enheden vises på portalen.|
   |12|Microsoft Defender for Endpoint kunne ikke anvende standardkonfigurationen.|Tjenesten kunne ikke anvende standardkonfigurationen.|Denne fejl bør blive løst efter en kort periode.|
   |13|Microsoft Defender for Endpoint enheds-id beregnet: `variable`.|Normal driftsproces.|Normal driftsmeddelelse; der kræves ingen handling.|
   |15|Microsoft Defender for Endpoint kan ikke starte kommandokanalen med URL-adressen: `variable`.|Variabel = URL-adresse til Defender for Endpoint-behandlingsservere. <p> Tjenesten kunne ikke kontakte de eksterne behandlingsservere på den pågældende URL-adresse.|Kontrollér forbindelsen til URL-adressen. Se [Konfigurer proxy og internetforbindelse](configure-proxy-internet.md).|
   |17|Microsoft Defender for Endpoint tjeneste kunne ikke ændre placeringen af tjenesten Tilsluttet brugeroplevelse og telemetri. Fejlkode: `variable`.|Der opstod en fejl med Windows-telemetritjenesten.|[Sørg for, at diagnosticeringsdatatjenesten er aktiveret](troubleshoot-onboarding.md#ensure-that-microsoft-defender-antivirus-is-not-disabled-by-a-policy)">Kontrollér, at diagnosticeringsdatatjenesten er aktiveret. <p> Kontrollér, at onboardingindstillingerne og scripts er installeret korrekt. Prøv at geninstallere konfigurationspakkerne. <p> Se [Onboard Windows 10-enheder](configure-endpoints.md).|
   |18|OOBE (Velkommen til Windows) er fuldført.|Tjenesten starter først, når installationen af Windows-opdateringer er fuldført.|Normal driftsmeddelelse; der kræves ingen handling.|
   |19|OOBE (Velkommen til Windows) er endnu ikke fuldført.|Tjenesten starter først, når installationen af Windows-opdateringer er fuldført.|Normal driftsmeddelelse; der kræves ingen handling. <p> Hvis denne fejl fortsætter, efter at systemet er genstartet, skal du kontrollere, at alle Windows-opdateringer er installeret fuldt ud.|
   |20|Kan ikke vente på, at OOBE (Velkommen til Windows) fuldføres. Fejlkode: `variable`.|Intern fejl.|Hvis denne fejl fortsætter, efter at systemet er genstartet, skal du kontrollere, at alle Windows-opdateringer er installeret fuldt ud.|
   |25|Microsoft Defender for Endpoint tjeneste kunne ikke nulstille tilstandsstatus i registreringsdatabasen. Fejlkode: `variable`.|Enheden blev ikke onboardet korrekt. Den rapporterer til portalen, men tjenesten vises muligvis ikke som registreret i SCCM eller i registreringsdatabasen.|Kontrollér, at onboardingindstillingerne og scripts er installeret korrekt. Prøv at geninstallere konfigurationspakkerne. <p> Se [Onboard Windows 10-enheder](configure-endpoints.md).|
   |26|Microsoft Defender for Endpoint tjeneste kunne ikke angive onboardingstatus i registreringsdatabasen. Fejlkode: `variable`.|Enheden blev ikke onboardet korrekt. <p> Den rapporterer til portalen, men tjenesten vises muligvis ikke som registreret i SCCM eller i registreringsdatabasen.|Kontrollér, at onboardingindstillingerne og scripts er installeret korrekt. Prøv at geninstallere konfigurationspakkerne. <p> Se [Onboard Windows 10-enheder](configure-endpoints.md).|
   |27|Microsoft Defender for Endpoint tjeneste kunne ikke aktivere SENSE-klar tilstand i Microsoft Defender Antivirus. Onboardingprocessen mislykkedes. Fejlkode: `variable`.|Normalt vil Microsoft Defender Antivirus angive en særlig passiv tilstand, hvis et andet antimalwareprodukt i realtid kører korrekt på enheden, og enheden rapporterer til Defender for Endpoint.|Kontrollér, at onboardingindstillingerne og scripts er installeret korrekt. Prøv at geninstallere konfigurationspakkerne. <p> Se [Onboard Windows 10-enheder](configure-endpoints.md). <p> Sørg for, at beskyttelse modmalware kører korrekt i realtid.|
   |28|Microsoft Defender for Endpoint tilsluttede brugeroplevelser og telemetritjenesteregistrering mislykkedes. Fejlkode: `variable`.|Der opstod en fejl med Windows-telemetritjenesten.|[Kontrollér, at diagnosticeringsdatatjenesten er aktiveret](troubleshoot-onboarding.md#ensure-that-microsoft-defender-antivirus-is-not-disabled-by-a-policy). <p> Kontrollér, at onboardingindstillingerne og scripts er installeret korrekt. Prøv at geninstallere konfigurationspakkerne. <p> Se [Onboard Windows 10-enheder](configure-endpoints.md).|
   |29|Offboarding-parametrene kunne ikke læses. Fejltype: %1, fejlkode: %2, beskrivelse: %3|Denne hændelse opstår, når systemet ikke kan læse offboarding-parametrene.|Sørg for, at enheden har internetadgang, og kør derefter hele offboarding-processen igen. Sørg for, at offboarding-pakken ikke er udløbet.|
   |30|Microsoft Defender for Endpoint tjeneste kunne ikke deaktivere SENSE-klar tilstand i Microsoft Defender Antivirus. Fejlkode: `variable`.|Normalt vil Microsoft Defender Antivirus angive en særlig passiv tilstand, hvis et andet antimalwareprodukt i realtid kører korrekt på enheden, og enheden rapporterer til Defender for Endpoint.|Kontrollér, at onboardingindstillingerne og scripts er installeret korrekt. Prøv at geninstallere konfigurationspakkerne. <p> Se [Onboard Windows 10-enheder](configure-endpoints.md). <p> Sørg for, at beskyttelse modmalware kører korrekt i realtid.|
   |31|Microsoft Defender for Endpoint tilsluttede brugeroplevelser og telemetritjeneste kunne ikke registreres. Fejlkode: `variable`.|Der opstod en fejl med Windows-telemetritjenesten under onboarding. Offboarding-processen fortsætter.|[Kontrollér, om der er fejl med Windows-telemetritjenesten](troubleshoot-onboarding.md#ensure-the-diagnostic-data-service-is-enabled).|
   |32|Microsoft Defender for Endpoint tjeneste kunne ikke anmode om at stoppe sig selv efter offboarding-processen. Fejlkode: %1|Der opstod en fejl under offboarding.|Genstart enheden.|
   |33|Microsoft Defender for Endpoint tjeneste kunne ikke bevare SENSE GUID. Fejlkode: `variable`.|Der bruges et entydigt id til at repræsentere hver enhed, der rapporterer til portalen. <p> Hvis identifikatoren ikke bevares, vises den samme enhed muligvis to gange på portalen.|Kontrollér tilladelserne i registreringsdatabasen på enheden for at sikre, at tjenesten kan opdatere registreringsdatabasen.|
   |34|Microsoft Defender for Endpoint tjeneste kunne ikke tilføje sig selv som en afhængighed af tjenesten Tilsluttet brugeroplevelse og telemetri, hvilket medfører, at onboardingprocessen mislykkes. Fejlkode: `variable`.|Der opstod en fejl med Windows-telemetritjenesten.|[Kontrollér, at diagnosticeringsdatatjenesten er aktiveret](troubleshoot-onboarding.md#ensure-that-microsoft-defender-antivirus-is-not-disabled-by-a-policy). <p> Kontrollér, at onboardingindstillingerne og scripts er installeret korrekt. Prøv at geninstallere konfigurationspakkerne. <p> Se [Onboard Windows 10-enheder](configure-endpoints.md).|
   |35|Microsoft Defender for Endpoint-tjenesten kunne ikke fjerne sig selv som en afhængighed af tjenesten Tilsluttet brugeroplevelse og telemetri. Fejlkode: `variable`.|Der opstod en fejl med Windows-telemetritjenesten under offboarding. Offboarding-processen fortsætter.|Kontrollér, om der er fejl med Diagnostiske Windows-datatjeneste.|
   |36|Microsoft Defender for Endpoint tilsluttede brugeroplevelser og telemetritjenesteregistrering lykkedes. Afslutningskode: `variable`.|Registrering af Defender for Endpoint med tjenesten Tilsluttet brugeroplevelse og telemetri blev fuldført.|Normal driftsmeddelelse; der kræves ingen handling.|
   |37|Microsoft Defender for Endpoint Et modul er ved at overskride dets kvote. Modul: %1, kvote: {%2} {%3}, Procentdel af kvoteudnyttelse: %4.|Enheden har næsten brugt sin tildelte kvote for det aktuelle 24-timers vindue. Det er ved at blive begrænset.|Normal driftsmeddelelse; der kræves ingen handling.|
   |38|Netværksforbindelsen er identificeret som lav. Microsoft Defender for Endpoint kontakter serveren hvert %1. minut. Forbrugsbaseret forbindelse: %2, internet tilgængelig: %3, gratis netværk tilgængeligt: %4.|Enheden bruger et forbrugsbaseret/betalt netværk og kontakter mindre hyppigt serveren.|Normal driftsmeddelelse; der kræves ingen handling.|
   |39|Netværksforbindelsen identificeres som normal. Microsoft Defender for Endpoint kontakter serveren hvert %1. minut. Forbrugsbaseret forbindelse: %2, internet tilgængelig: %3, gratis netværk tilgængeligt: %4.|Enheden bruger ikke en betalingsforbindelse efter forbrug og kontakter serveren som normalt.|Normal driftsmeddelelse; der kræves ingen handling.|
   |40|Batteritilstanden er identificeret som lav. Microsoft Defender for Endpoint kontakter serveren hvert %1. minut. Batteritilstand: %2.|Enheden har lavt batteriniveau og kontakter serveren sjældnere.|Normal driftsmeddelelse; der kræves ingen handling.|
   |41|Batteritilstanden identificeres som normal. Microsoft Defender for Endpoint kontakter serveren hvert %1. minut. Batteritilstand: %2.|Enheden har ikke et lavt batteriniveau og kontakter serveren som normalt.|Normal driftsmeddelelse; der kræves ingen handling.|
   |42|Microsoft Defender for Endpoint komponent kunne ikke udføre handlingen. Komponent: %1, handling: %2, undtagelsestype: %3, undtagelsesmeddelelse: %4|Intern fejl. Tjenesten kunne ikke startes.|Hvis denne fejl fortsætter, skal du kontakte support.|
   |43|Microsoft Defender for Endpoint komponent kunne ikke udføre handlingen. Komponent: %1, handling: %2, undtagelsestype: %3, undtagelsesfejl: %4, undtagelsesmeddelelse: %5|Intern fejl. Tjenesten kunne ikke startes.|Hvis denne fejl fortsætter, skal du kontakte support.|
   |44|Offboarding af Defender for Endpoint-tjenesten er fuldført.|Tjenesten var offboarded.|Normal driftsmeddelelse; der kræves ingen handling.|
   |45|Registreringen og start af hændelsessporingssessionen [%1] blev ikke udført. Fejlkode: %2|Der opstod en fejl under start af tjenesten under oprettelse af ETW-sessionen. Dette forårsagede en startfejl for tjenesten.|Hvis denne fejl fortsætter, skal du kontakte support.|
   |46|Registreringen og start af hændelsessporingssessionen [%1] mislykkedes på grund af manglende ressourcer. Fejlkode: %2. Dette skyldes sandsynligvis, at der er for mange aktive hændelsessporingssessioner. Tjenesten prøver igen om 1 minut.|Der opstod en fejl under start af tjenesten under oprettelse af ETW-sessionen på grund af manglende ressourcer. Tjenesten startede og kører, men rapporterer ikke nogen sensorhændelse, før ETW-sessionen er startet.|Normal driftsmeddelelse; der kræves ingen handling. Tjenesten forsøger at starte sessionen hvert minut.|
   |47|Hændelsessporingssessionen blev registreret og startet – gendannet efter tidligere mislykkede forsøg.|Denne hændelse følger den forrige hændelse efter vellykket start af ETW-sessionen.|Normal driftsmeddelelse; der kræves ingen handling.|
   |48|Det lykkedes ikke at føje en provider [%1] til hændelsessporingssessionen [%2]. Fejlkode: %3. Det betyder, at hændelser fra denne udbyder ikke rapporteres.|Det lykkedes ikke at føje en provider til ETW-sessionen. Derfor rapporteres providerhændelserne ikke.|Kontrollér fejlkoden. Hvis fejlen fortsætter, skal du kontakte Support.|
   |49|Ugyldig skykonfigurationskommando blev modtaget og ignoreret. Version: %1, status: %2, fejlkode: %3, meddelelse: %4|Der blev modtaget en ugyldig konfigurationsfil fra cloudtjenesten, der blev ignoreret.|Hvis denne fejl fortsætter, skal du kontakte support.|
   |50|Den nye cloudkonfiguration blev anvendt. Version: %1.|Der blev anvendt en ny konfiguration fra cloudtjenesten.|Normal driftsmeddelelse; der kræves ingen handling.|
   |51|Den nye cloudkonfiguration kunne ikke anvendes, version: %1. Den sidst kendte fungerende konfiguration, version %2, blev anvendt.|Der blev modtaget en ugyldig konfigurationsfil fra cloudtjenesten. Den sidst kendte fungerende konfiguration blev anvendt.|Hvis denne fejl fortsætter, skal du kontakte support.|
   |52|Den nye cloudkonfiguration kunne ikke anvendes, version: %1. Det lykkedes heller ikke at anvende den sidst kendte fungerende konfiguration, version %2. Standardkonfigurationen blev anvendt.|Der blev modtaget en ugyldig konfigurationsfil fra cloudtjenesten. Den sidst kendte fungerende konfiguration kunne ikke anvendes - og standardkonfigurationen blev anvendt.|Tjenesten forsøger at downloade en ny konfigurationsfil inden for 5 minutter. Hvis du ikke kan se begivenheden #50, skal du kontakte Support.|
   |53|Cloudkonfiguration indlæst fra vedvarende lager, version: %1.|Konfigurationen blev indlæst fra det vedvarende lager ved start af tjenesten.|Normal driftsmeddelelse; der kræves ingen handling.|
   |54| Den globale tilstand (pr. mønster) blev ændret. Tilstand: %1, mønster: %2 | Hvis tilstand = 0: Regel for rapportering af cyberdata har nået sin definerede capping-kvote og sender ikke flere data, før kvoten for capping udløber. Hvis tilstand = 1: Den kvota, der afpper, udløb, og reglen fortsætter med at sende data. | Normal driftsmeddelelse; der kræves ingen handling. |
   |55|Autologgeren secure ETW kunne ikke oprettes. Fejlkode: %1|Det lykkedes ikke at oprette den sikre ETW-logføring.|Genstart enheden. Hvis denne fejl fortsætter, skal du kontakte support.|
   |56|Autologgeren secure ETW kunne ikke fjernes. Fejlkode: %1|Den sikre ETW-session kunne ikke fjernes på offboarding.|Kontakt support.|
   |57|Hentning af et snapshot af computeren til fejlfindingsformål.|Der indsamles en undersøgelsespakke, som også kaldes en kriminalteknisk pakke.|Normal driftsmeddelelse; der kræves ingen handling.|
   |59|Starter kommando: %1|Starter udførelsen af svarkommandoen.|Normal driftsmeddelelse; der kræves ingen handling.|
   |60|Kommandoen %1 kunne ikke køres. Fejl! %2.|Svarkommandoen kunne ikke udføres.|Hvis denne fejl fortsætter, skal du kontakte support.|
   |61|Kommandoparametre for dataindsamling er ugyldige: SasUri: %1, compressionLevel: %2.|Kommandoargumenterne for dataindsamlingen kunne ikke læses eller fortolkes (ugyldige argumenter).|Hvis denne fejl fortsætter, skal du kontakte support.|
   |62|Den tilsluttede brugeroplevelses- og telemetritjeneste kunne ikke startes. Fejlkode: %1|Tjenesten Tilsluttet brugeroplevelse og telemetri (diagtrack) kunne ikke starte. Telemetri, der ikke er Microsoft Defender for Endpoint, sendes ikke fra denne computer.|Se efter flere tip til fejlfinding i hændelsesloggen: Microsoft-Windows-UniversalTelemetryClient/Operational.|
   |63|Opdaterer starttypen for den eksterne tjeneste. Navn: %1, faktisk starttype: %2, forventet starttype: %3, afslutningskode: %4|Opdaterede starttypen for den eksterne tjeneste.|Normal driftsmeddelelse; der kræves ingen handling.|
   |64|Start stoppede ekstern tjeneste. Navn: %1, afslutningskode: %2|Starter en ekstern tjeneste.|Normal driftsmeddelelse; der kræves ingen handling.|
   |65|Minifilterdriveren til Microsoft-sikkerhedshændelser blev ikke indlæst. Fejlkode: %1|Det lykkedes ikke at indlæse MsSecFlt.sys filsystemets minifilter.|Genstart enheden. Hvis denne fejl fortsætter, skal du kontakte support.|
   |66|Politikopdatering: Ventetidstilstand - %1|Politikken for C-&C-forbindelseshyppighed blev opdateret.|Normal driftsmeddelelse; der kræves ingen handling.|
   |68|Tjenestens starttype er uventet. Tjenestenavn: %1, faktisk starttype: %2, forventet starttype: %3|Uventet starttype for ekstern tjeneste.|Ret starttypen for den eksterne tjeneste.|
   |69|Tjenesten er stoppet. Tjenestenavn: %1|Den eksterne tjeneste er stoppet.|Start den eksterne tjeneste.|
   |70|Politikopdatering: Tillad eksempelsamling - %1|Politikken for indsamling af eksempler blev opdateret.|Normal driftsmeddelelse; der kræves ingen handling.|
   |71|Kommandoen %1 blev kørt|Kommandoen blev udført.|Normal driftsmeddelelse; der kræves ingen handling.|
   |72|Forsøgte at sende den første fulde computerprofilrapport. Resultatkode: %1|Kun til orientering.|Normal driftsmeddelelse; der kræves ingen handling.|
   |73|Assistent starter for platformen: %1|Kun til orientering.|Normal driftsmeddelelse; der kræves ingen handling.|
   |74|Enhedskoden i registreringsdatabasen overskrider længdegrænsen. Kodenavn: %2. Længdegrænse: %1.|Enhedskoden overskrider længdegrænsen.|Brug et kortere enhedsmærke.|
   |81|Det lykkedes ikke at oprette Microsoft Defender for Endpoint ETW-autologger. Fejlkode: %1|ETW-sessionen kunne ikke oprettes.|Genstart enheden. Hvis denne fejl fortsætter, skal du kontakte support.|
   |82|Det lykkedes ikke at fjerne Microsoft Defender for Endpoint etw-autologger. Fejlkode: %1|ETW-sessionen kunne ikke slettes.|Kontakt support.|
   |84|Angiv Windows Defender Antivirus kørende tilstand. Gennemtving passiv tilstand: %1, resultatkode: %2.|Angiv kørselstilstand for defender (aktiv eller passiv).|Normal driftsmeddelelse; der kræves ingen handling.|
   |85|Det lykkedes ikke at udløse Microsoft Defender for Endpoint eksekverbar fil. Fejlkode: %1|Den eksekverbare AssistentIR-stjerne mislykkedes.|Genstart enheden. Hvis denne fejl fortsætter, skal du kontakte support.|
   |86|Start igen stoppede den eksterne tjeneste, der skulle være oppe. Navn: %1, afslutningskode: %2|Starter den eksterne tjeneste igen.|Normal driftsmeddelelse; der kræves ingen handling.|
   |87|Den eksterne tjeneste kan ikke startes. Navn: %1|Den eksterne tjeneste kunne ikke startes.|Kontakt support.|
   |88|Opdaterer starttypen for den eksterne tjeneste igen. Navn: %1, faktisk starttype: %2, forventet starttype: %3, afslutningskode: %4|Opdaterede starttypen for den eksterne tjeneste.|Normal driftsmeddelelse; der kræves ingen handling.|
   |89|Starttypen for den eksterne tjeneste kan ikke opdateres. Navn: %1, faktisk starttype: %2, forventet starttype: %3|Starttypen for den eksterne tjeneste kan ikke opdateres.|Kontakt support.|
   |90|System Guard Runtime Monitor kunne ikke konfigureres til at oprette forbindelse til cloudtjenesten i geoområdet %1. Fejlkode: %2|System Guard Runtime Monitor sender ikke attestationsdata til cloudtjenesten.|Kontrollér tilladelserne til registreringsstien: "HKLM\Software\Microsoft\Windows\CurrentVersion\Sgrm". Hvis der ikke er nogen problemer, der opdages, skal du kontakte Support.|
   |91|Det lykkedes ikke at fjerne oplysninger om geo-område for System Guard Runtime Monitor. Fejlkode: %1|System Guard Runtime Monitor sender ikke attestationsdata til cloudtjenesten.|Kontrollér tilladelserne til registreringsstien: "HKLM\Software\Microsoft\Windows\CurrentVersion\Sgrm". Hvis der ikke er nogen problemer, der opdages, skal du kontakte Support.|
   |92|Stopper afsendelsen af sensor-cyberdatakvoten, fordi datakvoten er overskredet. Sender igen, når kvoteperioden passerer. Tilstandsmaske: %1|Overskride grænsen for begrænsning.|Normal driftsmeddelelse; der kræves ingen handling.|
   |93|Genoptager afsendelse af sensor cyberdata. Tilstandsmaske: %1|Genoptag indsendelse af cyberdata.|Normal driftsmeddelelse; der kræves ingen handling.|
   |94|Microsoft Defender for Endpoint eksekverbare fil er startet|Den eksekverbare SenseCE-fil er startet.|Normal driftsmeddelelse; der kræves ingen handling.|
   |95|Microsoft Defender for Endpoint eksekverbare fil er afsluttet|Den eksekverbare SenseCE-fil er afsluttet.|Normal driftsmeddelelse; der kræves ingen handling.|
   |96|Microsoft Defender for Endpoint Init har kaldt. Resultatkode: %2|Den eksekverbare SenseCE-fil har kaldt MCE-initialisering.|Normal driftsmeddelelse; der kræves ingen handling.|
   |97|Der er forbindelsesproblemer med cloudmiljøet i DLP-scenariet|Der er problemer med netværksforbindelsen, der påvirker DLP-klassificeringsflowet.|Kontrollér netværksforbindelsen.|
   |98|Forbindelsen til cloudmiljøet for DLP-scenariet er blevet gendannet|Forbindelsen til netværket blev gendannet, og DLP-klassificeringsflowet kan fortsætte.|Normal driftsmeddelelse; der kræves ingen handling.|
   |99|Sense stødte på følgende fejl under kommunikation med serveren: (%1). Resultat: (%2)|Der opstod en kommunikationsfejl.|Se følgende hændelser i hændelsesloggen for at få flere oplysninger.|
   |100|Microsoft Defender for Endpoint eksekverbare fil kunne ikke startes. Fejlkode: %1|Den eksekverbare SenseCE-fil kunne ikke startes.|Genstart enheden. Hvis denne fejl fortsætter, skal du kontakte support.|
   |102|Microsoft Defender for Endpoint eksekverbare netværksregistrerings- og svar-fil er startet|Den eksekverbare SenseNdr-fil er startet.|Normal driftsmeddelelse; der kræves ingen handling.|
   |103|Microsoft Defender for Endpoint Netværksregistrering og Svar eksekverbar er afsluttet|Den eksekverbare SenseNdr-fil er afsluttet.|Normal driftsmeddelelse; der kræves ingen handling.|
   |

> Vil du opleve Microsoft Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-eventerrorcodes-belowfoldlink)

## <a name="see-also"></a>Se også
- [Onboarde Windows 10 enheder](configure-endpoints.md)
- [Konfigurer indstillingerne for enhedsproxy og internetforbindelse](configure-proxy-internet.md)
- [Foretag fejlfinding af Microsoft Defender for Endpoint](troubleshoot-onboarding.md)
- [Oversigt over klientanalyse](overview-client-analyzer.md)
- [Download og kør klientanalysen](download-client-analyzer.md)
- [Forstå HTML-analyserapporten](analyzer-report.md)
