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
ms.openlocfilehash: c7fd01b95d461332baaf4eac90aee4715da3e55e
ms.sourcegitcommit: e911dd506ea066795e418daf7b84c1e11381a21c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/19/2022
ms.locfileid: "64953024"
---
# <a name="test-base-faq"></a>Ofte stillede spørgsmål om testbase

**Spørgsmål: Hvordan sender vi vores pakker til testbaseteamet?**

**A:** Indsend dine pakker direkte til Test Base-miljøet ved hjælp af vores selvbetjeningsportal.

Hvis du vil sende din programpakke, skal du gå til [Azure Portal](https://www.aka.ms/testbaseportal "Startside for testbase") og uploade en zip-komprimeret mappe, der indeholder programmets binære filer, afhængigheder og testscripts via det selvbetjente dashboard til Test Base-portalen.

Se onboardingbrugervejledningen for at få flere oplysninger eller kontakt vores team på <testbasepreview@microsoft.com> for at få hjælp og flere oplysninger.

**Spørgsmål: Hvad er OOB-test (Out-of-box)?**

**A:** OOB-test (Out-of-box) standardiseres, standardtestkørsler, hvor programpakker installeres, startes og lukkes tredive (30) gange og derefter fjernes.

De pakker, der er oprettet til Test Base, har følgende testscripts: installér, start, luk og eventuelt fjernelsesscriptet.

Oob-testene (Out-of-box) giver dig standardiseret telemetri på dit program, som du kan sammenligne på tværs af Windows builds.

**Spørgsmål: Kan vi indsende test uden for de indbyggede test (installere, starte, lukke, fjerne testscripts)?**

**A:** Ja, kunderne kan også uploade programpakker til **funktionelle test** via det selvbetjente portaldashboard.
**Funktionelle test** er test, der gør det muligt for kunder at udføre deres scripts for at køre brugerdefineret funktionalitet på deres program.

## <a name="testing"></a>Test

**Spørgsmål: Understøtter du funktionelle test?**

**A:** Ja, testbasen understøtter funktionelle test. Funktionelle test er test, der gør det muligt for vores kunder at udføre deres scripts for at køre brugerdefineret funktionalitet på deres program.

Hvis du vil sende din programpakke til funktionel test, skal du uploade den ZIP-mappe, der indeholder programmets binære filer, afhængigheder og testscripts, via vores selvbetjente portaldashboard.

Se onboardingbrugervejledningen for at få flere oplysninger eller kontakt vores team på <testbasepreview@microsoft.com> for at få hjælp og flere oplysninger.

**Spørgsmål: Hvordan håndterer Test Base vores testdata?**

**A:** Testbasen indsamler og administrerer dine testdata sikkert i Azure-miljøet.

**Spørgsmål: Kan testbasen understøtte vores automatiserede test?**

**A:** Ja, testbasen understøtter automatiserede test, men vi understøtter ikke manuelle test på nuværende tidspunkt på grund af tjenestefunktioner.

**Spørgsmål: Hvilke sprog og strukturer i automatiserede test understøtter du?**

**A:** Vi understøtter alle sprog og strukturer. Vi aktiverer alle scripts via PowerShell.

Du skal også angive (uploade) de afhængige binære filer i den påkrævede struktur.

**Spørgsmål: Hvor hurtigt giver testbasen testresultater?**

**A:** For hver test, vi kører i forhold til foreløbige builds, leverer vi resultater inden for 48 timer på dit [Azure Portal-dashboard](https://www.aka.ms/testbaseportal "Startside for testbase") .

**Spørgsmål: Kan du genstarte efter installationen?**

**A:** Ja, vores proces understøtter genstart efter installation. Sørg for at vælge denne indstilling på rullelisten "Valgfrie indstillinger", når du angiver dine **opgaver** på onboardingportalen.

I forbindelse med OOB-test (Out-of-box) kan du angive, om der kræves en genstart til _installationsscriptet._

![Genstart billede.](Media/reboot.png)

I forbindelse med funktionelle test kan du angive, om en genstart er påkrævet for hvert script, der tilføjes.

![Sådan vælger du funktionelle test.](Media/functionalreboot.png)

**Spørgsmål: Hvilke Windows versioner understøtter du?**

**A:** Vi understøtter i øjeblikket Windows 10 klienter, Windows Server 2016, Windows Server 2016 Core-version, Windows Server 2019 og Windows Server 2019 Core-versionen.

**Spørgsmål: Hvad er forskellen mellem test af sikkerhedsopdatering og funktionsopdatering?**

**A:** I forbindelse med test af sikkerhedsopdateringer tester vi i forhold til de **<ins>månedlige foreløbige sikkerhedsopdateringer</ins>** på Windows, som fokuserer på at holde vores brugere altid sikre og beskyttede. I forbindelse med test af funktionsopdateringen tester vi mod de **<ins>toårige foreløbige funktionsopdateringer</ins>**, der introducerer nye funktioner og funktioner på Windows.

## <a name="debugging-options"></a>Indstillinger for fejlfinding

**Spørgsmål: Får vi adgang til Virtual Machines (VM'er) i tilfælde af fejl? Hvad deler Test Base?**

**A:** Det er kun Microsoft, der har adgang til VM'erne, for at tjenesten er kompatibel, og de foreløbige opdateringer er sikre. Kunder kan dog få vist testresultater og andre testmålepunkter på deres portaldashboard, herunder nedbruds- og stopsignaler, målepunkter for pålidelighed, hukommelse og CPU-forbrug osv. Vi genererer og leverer også logge over testkørsler på dashboardet til download og yderligere analyse.

Vi kan også levere hukommelsesdumps til fejlfinding efter behov.

**Spørgsmål: Hvad er de næste trin til at løse disse problemer, hvis der er problemer under testen?**

**A:** Testbaseteamet udfører en indledende triageproces for at bestemme den egentlige årsag til fejlen, og afhængigt af vores resultater dirigerer vi til kunden eller interne teams i Microsoft med henblik på fejlfinding.

Vi arbejder altid tæt sammen med vores kunder om fælles afhjælpning for at løse eventuelle problemer.

**Spørgsmål: Er Microsoft i besiddelse af udgivelsen af sikkerhedsrettelsen, indtil problemet er løst? Hvilke alternative løsninger er tilgængelige?**

**A:** Formålet med testbasen er at sikre, at vores fælles slutbrugere ikke oplever problemer. Vi vil arbejde hårdt sammen med softwareleverandører for at løse eventuelle problemer før udgivelsen, men i tilfælde af at rettelsen ikke er mulig, har vi andre løsninger som f.eks. shims og blokke.

## <a name="miscellaneous"></a>Diverse

**Spørgsmål: Hvordan fungerer tjenesten med en server i det lokale miljø?**

**A:** Vi understøtter i øjeblikket ikke lokale servere. Men hvis serveren eksponerer HTTP-slutpunktet, kan vi oprette forbindelse til det via internettet.

**Spørgsmål: Who er vært for VM'erne?**

**A:** Microsoft klargør vm'en til denne tjeneste og tager belastningen ved at gøre det fra kunden.

**Spørgsmål: Understøtter denne tjeneste web-, mobil- eller skrivebordsprogrammer?**

**A:** I øjeblikket fokuserer vi på skrivebordsprogrammer, men vi har planer om at onboarde webprogrammer i fremtiden, men vi understøtter ikke mobilapps på nuværende tidspunkt.

**Spørgsmål: Hvad er forskellen mellem Test Base og SUVP?**

**A:** Den største forskel mellem Test Base og SUVP er, at vores partnere onboarder deres programmer i Test Base Azure-miljøet til valideringskørsler mod foreløbige opdateringer i stedet for selv at udføre testene.

Ud over test af foreløbige sikkerhedsopdateringer understøtter vi test af foreløbige funktionsopdateringer på vores platform. Vi har mange andre typer opdateringer og OS-test på vores roadmap.

**Spørgsmål: Er der en omkostning forbundet med tjenesten?**

**A:** Fra og med den 1. marts 2022 får du 100 gratis timer (til en værdi af $800), der udløber om 6 måneder under dit abonnement til dine valideringsbehov. Når de gratis timer forbruges (eller udløber, før de bruges), måles du automatisk til 8 USD pr. time i forhold til dit forbrug.

**Spørgsmål: Hvordan kan jeg give feedback om testbasen?**

**A:** Hvis du vil dele din feedback om testbasen, skal du vælge ikonet **Feedback** nederst til venstre på portalen. Medtag et skærmbillede med din indsendelse for at hjælpe Microsoft med bedre at forstå din feedback.

Du kan også indsende produktforslag og opvote andre ideer på <testbasepreview@microsoft.com>.
