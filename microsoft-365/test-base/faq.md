---
title: Ofte stillede spørgsmål om testbase
description: Gennemse ofte stillede spørgsmål
search.appverid: MET150
author: Tinacyt
ms.author: tinachen
manager: rshastri
audience: Software-Vendor
ms.topic: troubleshooting
ms.date: 07/06/2021
ms.service: virtual-desktop
ms.localizationpriority: medium
ms.collection: TestBase-M365
ms.custom: ''
ms.reviewer: mapatel
f1.keywords: NOCSH
ms.openlocfilehash: e21774ada245a3b9d5c131998b7c60b4a4778210
ms.sourcegitcommit: a9266e4e7470e8c1e8afd31fef8d266f7849d781
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/09/2022
ms.locfileid: "63595998"
---
# <a name="test-base-faq"></a>Ofte stillede spørgsmål om testbase

**Sp: Hvordan sender vi vores pakker til Test Base-teamet?**

**A:** Send dine pakker direkte til Test Base-miljøet ved hjælp af vores selvbetjeningsportal.

Hvis du vil sende din programpakke, skal du gå til [Azure](https://www.aka.ms/testbaseportal "Testbase startside") Portal og uploade en zip-komprimeret mappe, der indeholder dit programs binære binære, afhængigheder og testscripts via dashboardet for selvbetjeningsportalen for Test Base. 

Se brugervejledningen til onboarding for at få flere oplysninger, eller kontakt vores team for at <testbasepreview@microsoft.com> få hjælp og flere oplysninger.

**Sp: Hvad er OOB-test (out of box) ?**

**A:** Out of box-test (OOB) er standardiserede, standardtest kører, hvor programpakker installeres, startes og lukkes tredive (30) gange og derefter fjernes. 

De pakker, der er oprettet til Test Base, har følgende testscripts: installér, start, luk og eventuelt fjernelsesscriptet. 

OOB-test (Out of box) giver dig standardiseret telemetri på dit program, så du kan sammenligne på tværs Windows builds.

**Sp: Kan vi indsende tests uden for out of box-tests (installér, start, luk, fjern testscripts)?**

**A:** Ja, kunder kan også uploade programpakker til **funktionstests** via dashboardet i selvbetjeningsportalen.
**Funktionstest** er test, der giver kunderne mulighed for at udføre deres scripts for at køre brugerdefinerede funktioner i deres program.


## <a name="testing"></a>Test

**Sp: Understøtter I funktionstest?**

**A:** Ja, Testbase understøtter funktionstest. Funktionstest er test, der giver vores kunder mulighed for at udføre deres scripts for at køre brugerdefinerede funktioner på deres program. 

Hvis du vil sende programpakken til funktionelle test, skal du uploade den ZIP-komprimerede mappe, der indeholder dit programs binære binære, afhængigheder og testscripts via vores selvbetjeningsportaldashboard. 

Se brugervejledningen til onboarding for at få flere oplysninger, eller kontakt vores team for at <testbasepreview@microsoft.com> få hjælp og flere oplysninger.

**Sp: Hvordan håndterer TestBase vores testdata?**

**A:** Testbase indsamler og administrerer sikkert dine testdata på Azure-miljøet. 

**Sp: Kan TestBase understøtte vores automatiserede test?**

**A:** Ja, Testbase understøtter automatiserede test, men vi understøtter ikke manuelle test på nuværende tidspunkt på grund af tjenestefunktioner.

**Sp: Hvilke sprog og rammer for automatiserede test understøtter du?**

**A:** Vi understøtter alle sprog og rammer. Vi aktiverer alle scripts via PowerShell. 

Du skal også angive (uploade) de afhængige binære i den påkrævede struktur.

**Sp: Hvor hurtigt giver Test Base testresultater?**

**A:** For hver test, vi kører i forhold til de foreløbige builds, leverer vi resultater inden for 48 timer på dashboardet i [Azure Portal](https://www.aka.ms/testbaseportal "Testbase startside") .

**Sp: Kan du genstarte efter installationen?**

**A:** Ja, vores proces understøtter genstart efter installationen. Sørg for at vælge denne indstilling på rullelisten "Valgfri indstillinger", når du angiver **dine opgaver** på onboardingportalen.

Ved OOB-test (Out of box) kan du angive, om en genstart er nødvendig for _scriptet Installér._

![Billede af Genstart.](Media/reboot.png)

Når det gælder funktionelle test, kan du angive, om der kræves en genstart for hvert script, der tilføjes.

![Sådan vælges funktionstests.](Media/functionalreboot.png)

**Sp: hvilke Windows versioner understøtter du?**

**A:** Vi understøtter i øjeblikket Windows 10-klienter, Windows Server 2016, Windows Server 2016 Core-version, Windows Server 2019 og Windows Server 2019 Core-version.

**Sp: Hvad er forskellen mellem sikkerhedsopdateringstests og funktionsopdateringstests?**

**A:** I forbindelse med sikkerhedsopdateringstests tester **<ins></ins>** vi i forhold til de månedlige foreløbige sikkerhedsopdateringer på Windows, som fokuserer på at holde vores brugere altid sikre og beskyttede. I forbindelse med funktionsopdateringstestene tester **<ins></ins>** vi dig i forhold til de toårlige foreløbige funktionsopdateringer, som introducerer nye funktioner og Windows.

## <a name="debugging-options"></a>Fejlfindingsindstillinger

**Sp: Får vi adgang til virtuelle computere i tilfælde af fejl? Hvad deler Test Base?**

**A:** For at tjenesten skal være kompatibel, og de foreløbige opdateringer skal være sikre, er det kun Microsoft, der har adgang til VM'erne. Men kunder kan få vist testresultater og andre testmålepunkter på deres portaldashboard, herunder crash and hang-signaler, målepunkter for pålidelighed, hukommelse og CPU-udnyttelse osv. Vi genererer og leverer også logfiler over test, der køres på dashboardet til download og yderligere analyse. 

Vi kan også levere hukommelsesdumps til fejlfinding af nedbrud efter behov.

**Sp: Hvis der bliver fundet problemer under testen, hvad er de næste trin til at løse disse problemer?**

**A:** Testbaseteamet udfører en indledende triageproces for at bestemme den egentlige årsag til fejlen, og afhængigt af vores resultater dirigerer vi derefter til kunden eller de interne teams i Microsoft til fejlfinding. 

Vi arbejder altid tæt sammen med vores kunder i fælles afhjælpning for at løse eventuelle problemer. 

**Sp: Holder Microsoft frigivelsen af sikkerhedsopdateringen i venteposition, indtil problemet er løst? Hvilke alternative opløsninger er tilgængelige?**

**A:** Formålet med Test Base er at sikre, at vores fælles slutbrugere ikke står over for problemer. Vi arbejder hårdt sammen med softwareleverandører om at løse eventuelle problemer før udgivelsen, men i tilfælde af at rettelsen ikke er mulig, har vi andre løsninger, f.eks. f.eks. glimser og blokke.

## <a name="miscellaneous"></a>Diverse bestemmelser

**Sp: Hvordan fungerer tjenesten med en server i det offentlige sted?**

**A:** Vi yder i øjeblikket ikke support på serverne i det aktuelle tidspunkt. Men hvis serveren bruger HTTP-slutpunkt, kan vi oprette forbindelse til det via internettet.

**Sp: Who VM'erne?**

**A:** Microsoft klar gør VM'en til denne tjeneste og tager kundens indlæsning af den.

**Sp: Understøtter denne tjeneste web-, mobil- eller skrivebordsprogrammer?**

**A:** I øjeblikket er vores fokus på skrivebordsprogrammer, men vi har planer om at onboarde webprogrammer i fremtiden, men vi understøtter ikke mobilprogrammer på nuværende tidspunkt.

**Sp: Hvad er forskellen mellem Test Base og AFRUKP?**

**A:** Den største forskel mellem Test Base og ONBOARDP er, at vores partnere onboarder deres programmer til Test Base Azure-miljøet til validering i forhold til foreløbige opdateringer i stedet for at udføre selve testene. 

Ud over foreløbige sikkerhedsopdateringer understøtter vi tests af foreløbige funktionsopdateringer på vores platform. Vi har mange andre typer opdateringer og os-test i vores oversigt.

**Sp: Er der en omkostning knyttet til tjenesten?**

**A:** Pr. 1. marts 2022 får du 100 gratis timer (værdien 800 USD), der udløber om 6 måneder under dit abonnement for at opfylde dine valideringsbehov. Når de gratis timer bliver forbrugt (eller udløbet før brug), bliver du automatisk forbrugt til 8 USD pr. time i forhold til dit forbrug.   

**Sp: Hvordan kan jeg give feedback om Test Base?**

**A:** Hvis du vil dele din feedback om TestBase, **skal du** vælge Feedback-ikonet nederst til venstre på portalen. Medtag et skærmbillede sammen med din indsendelse for at hjælpe Microsoft med bedre at forstå din feedback. 

Du kan også indsende produktforslag ogvote andre ideer på <testbasepreview@microsoft.com>.
