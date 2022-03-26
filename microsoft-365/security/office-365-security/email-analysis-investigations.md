---
title: Mailanalyse i undersøgelser af Microsoft Defender til Office 365
f1.keywords:
- NOCSH
author: dansimp
ms.author: dansimp
manager: dansimp
audience: ITPro
ms.topic: article
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
keywords: automatiseret hændelsesrespons, undersøgelse, afhjælpning, trusselsbeskyttelse
description: Se, hvordan mailanalyse i undersøgelser fungerer i Microsoft Defender for Office 365.
ms.custom:
- air
- seo-marvel-mar2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 5c4d1be31742d21f6e7919a8db4a3d2aff75f66e
ms.sourcegitcommit: 9c8eca862a2f0fdca7a66c641e382e37fcaefa10
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/24/2022
ms.locfileid: "63775384"
---
# <a name="email-analysis-in-investigations-for-microsoft-defender-for-office-365"></a>Mailanalyse i undersøgelser af Microsoft Defender til Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Microsoft Defender til Office 365 plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Under den automatiserede undersøgelse af beskeder analyserer Microsoft Defender for Office 365 den oprindelige mail for trusler og identificerer andre mails, der er relateret til den oprindelige mail og potentielt en del af et angreb. Denne analyse er vigtig, fordi mailangreb sjældent består af en enkelt mail.

Den automatiske undersøgelses mailanalyse identificerer mailklynger ved hjælp af attributter fra den oprindelige mail til forespørgsel på mails, der sendes og modtages af din organisation. Dette svarer til, at en sikkerhedsanalytiker vil lede efter de relaterede mails i Explorer eller Avanceret jagt. Der bruges flere forespørgsler til at identificere matchende mails, fordi hackere typisk omformer mailparametrene for at undgå sikkerhedsregistrering. Klyngeanalysen udfører disse kontroller for at afgøre, hvordan mails, der er involveret i undersøgelsen, håndteres:

- Mailanalysen opretter forespørgsler (klynger) af mails ved hjælp af attributter fra den oprindelige mail – afsenderværdier (IP-adresse, afsendelse af domæne) og indhold (emne, klynge-id) for at finde mails, der er relaterede.
- Hvis analyse af den oprindelige mails URL-adresser og filer identificerer, at nogle er skadelige (dvs. malware eller phish), vil den også oprette forespørgsler eller klynger af mails, der indeholder den ondsindede URL-adresse eller fil.
- Analyse af mailklynge tæller de trusler, der er knyttet til de tilsvarende mails i klyngen, for at afgøre, om mails er skadelige, mistænkelige eller ikke har nogen klare trusler. Hvis klyngen af mails, der matcher forespørgslen, har en tilstrækkelig mængde spam, normal phish, phish- eller malwaretrusler, så får mailklyngen den pågældende trusselstype anvendt på den.
- Analyse af mailklynge kontrollerer også den nyeste leveringssted for de oprindelige mails og mails i mailklyngerne for at hjælpe med at identificere, om mails potentielt stadig skal fjernes eller allerede er blevet løst eller forhindret. Denne analyse er vigtig, fordi hackere omformer skadeligt indhold samt sikkerhedspolitikker og beskyttelse kan variere fra postkasse til postkasse. Denne funktion fører til situationer, hvor skadeligt indhold stadig kan være i postkasser, selvom en eller flere skadelige mails er blevet registreret og fjernet ved automatisk tømning i nul timer (ZAP).
- Mailklynger, der betragtes som skadelige på grund af malware, phish med høj tillid, skadelige filer eller skadelige URL-adresser, får en afventende handling til blød sletning af mails, når der stadig er i den skybaserede postkasse (indbakke eller mappe med uønsket post). Hvis skadelige mails eller mailklynger kun er "Ikke i postkasse" (blokeret, sat i karantæne, mislykket, blød slettet osv.) eller "Lokalt/Eksternt" uden nogen i den skybaserede postkasse, vil der ikke blive konfigureret nogen afventende handling for at fjerne dem.
- Hvis en af mailklyngerne vurderes at være skadelig, vil den trussel, der er identificeret af klyngen, blive anvendt tilbage til de oprindelige mails, der var involveret i undersøgelsen. Denne funktionsmåde svarer til en sikkerhedsanalytiker, der bruger mail med at lede efter resultater for at afgøre, om en oprindelig mail er baseret på tilsvarende mails. Dette resultat sikrer, at uanset om en oprindelig mails URL-adresser, filer eller kildemailindikatorer registreres eller ej, kan systemet identificere skadelige mails, der potentielt undgår registrering via tilpasning, omformning, angreb eller andre hackerteknikker.
- Under undersøgelsen af brugerforliget oprettes der yderligere mailklynger for at identificere potentielle mailproblemer, som postkassen har skabt. Denne proces omfatter en ren mailklynge (gode mails fra brugere, potentielle dataudfyldning og potentielle kommando-/kontrolmails), mistænkelige mailklynger (mails, der indeholder spam eller normal phish) og skadelige mailklynger (mails, der indeholder malware eller phish). Disse mailklynger leverer sikkerheds operationsanalytikerdata for at afgøre, hvilke andre problemer der kan være nødt til at blive løst fra et kompromis, og synligheden af hvilke mails, der kan have udløst de oprindelige beskeder (f.eks. phish/spam, der udløste brugernes begrænsninger for afsendelse).

Mailklyngeanalyse via ligheds- og ondsindede enhedsforespørgsler sikrer, at mailproblemerne identificeres og ryddes helt op, også selvom der kun identificeres én mail fra et angreb. Du kan bruge links fra sidepanelvisningerne med mailklyngens detaljer til at åbne forespørgslerne i Stifinder eller Avanceret jagt til at udføre en dybere analyse og ændre forespørgslerne, hvis det er nødvendigt. Denne funktion aktiverer manuel forbedring og afhjælpning, hvis du synes, at mailklyngens forespørgsler er for smalle eller for brede (herunder ikke-relaterede mails).

Her er yderligere forbedringer af mailanalyse i undersøgelser.

## <a name="air-investigation-ignores-advanced-delivery-items-secops-mailbox-and-phishedu-messages"></a>AIR-undersøgelse ignorerer avancerede leveringsvarer (SecOps-postkasse og PhishEDU-meddelelser)

Under mailklyngeanalysen ignorerer alle klyngeforespørgsler sikkerhedspostkasser, der er konfigureret som sikkerhedsbaserede postkasser i politikken for avanceret levering. På samme måde ignorerer mailklyngeforespørgsler phish-simulering (uddannelse), der er konfigureret i politikken for avanceret levering. Hverken SecOps- eller PhishEdu-udeladelsesværdierne vises i forespørgslen for at gøre klyngeattributterne enklere og nemmere at læse. Denne udelukkelse sikrer, at trusselsintelligens og driftsmæssige postkasser (SecOps-postkasser) og phish-simuleringerne (PhishEdu) ignoreres under trusselsanalyse og ikke fjernes under afhjælpningen.

>[!Note]
>Når du åbner en mailklynge for at få den vist i Stifinder fra detaljerne i mailklyngen, anvendes postkassefiltrene PhishEdu og SecOps i Stifinder, men vises ikke. Hvis du ændrer Stifinders filtre, datoer eller opdaterer forespørgslen på siden, fjernes udelukkelserne for filteret PhishEdu/SecOps, og mails, der opfylder disse, vises igen. Hvis du opdaterer siden Stifinder ved hjælp af browseropdateringsfunktionen, genindlæses de oprindelige forespørgselsfiltre igen, herunder filtrene PhishEdu/SecOps – men fjerner alle efterfølgende ændringer, du har foretaget.
>

## <a name="air-updates-pending-email-action-status"></a>AIR-opdateringer afventer mailhandlingsstatus

Undersøgelsesmailanalysen beregner mailtrusler og -placeringer på tidspunktet for undersøgelsen for at skabe undersøgelses beviser og handlinger. Disse data kan blive forældede og forældede, når handlinger uden for undersøgelsen påvirker de mails, der er involveret i undersøgelsen. Eksempelvis kan manuel jagt og afhjælpning af sikkerhedshandlinger rydde op i mails, som er inkluderet i en undersøgelse. Ligeledes kan sletningshandlinger, der er godkendt ved parallelle undersøgelser eller automatiske annulleringer uden time (ZAP), have fjernet mails. Desuden kan forsinkede registreringer af trusler efter levering af mail ændre antallet af trusler i undersøgelsens mailforespørgsler/grupper.

For at sikre, at undersøgelseshandlinger er opdaterede, vil en undersøgelse med ventende handlinger med jævne mellemrum køre mailanalyseforespørgsler for at opdatere mailplaceringer og trusler.

- Når data i mailklyngen ændres, opdateres truslerne og antallet af seneste leveringssted.
- Hvis mails eller mailklynge med afventende handlinger ikke længere findes i postkassen, annulleres den afventende handling, og den ondsindede mail/klynge betragtes som løst.
- Når alle undersøgelsens trusler er blevet løst eller annulleret som nævnt ovenfor, vil undersøgelsen overgå til en afhjulpet tilstand, og den oprindelige besked vil blive løst.

## <a name="the-display-of-incident-evidence-for-email-and-email-clusters"></a>Visning af hændelse beviser for mail- og mailklynger

Mailbaserede beviser i **fanen Beviser og Svar** for en hændelse viser nu følgende oplysninger.

:::image type="content" source="../../media/email-analysis-investigations/email-analysis-evidence-example.png" alt-text="Eksempel på mailanalyseoplysninger i Beviser og Svar." lightbox="../../media/email-analysis-investigations/email-analysis-evidence-example.png":::

Fra de nummereredeforklaringer i figuren:

1. Ud over Handlingscenter kan du udføre **afhjælpningshandlinger**.
2. Du kan rette op på mailklynger med en **ondsindet** konklusion ( **men ikke mistænkelig**).
3. Phishing opdeles i høj tillid til og normal phish for mailspam.

   For en ondsindet konklusion er trusselskategorierne malware, phish med høj tillid, skadelig URL-adresse og skadelig fil.

   For en mistænkelig mistanke er trusselskategorierne spam og normal phish.

4. Optællingen af mails er baseret på den seneste leveringsplacering og omfatter tællere for mails i postkasser, ikke i postkasser og i lokale miljø.
5. Omfatter dato og klokkeslæt for forespørgslen, som muligvis bliver opdateret for de seneste data.

For mails eller mailklynger  i fanen Enheder for en hændelse betyder **Forhindret, at** der ikke var nogen skadelige mails i postkassen for dette element (mail eller klynge). Her er et eksempel.

:::image type="content" source="../../media/email-analysis-investigations/email-analysis-evidence-example-prevented.png" alt-text="Eksempel på en forhindret mail." lightbox="../../media/email-analysis-investigations/email-analysis-evidence-example-prevented.png":::

I dette eksempel er mailen skadelig, men ikke i en postkasse.

## <a name="next-steps"></a>Næste trin

- [Få vist afventende eller fuldførte afhjælpningshandlinger](air-review-approve-pending-completed-actions.md)
