---
title: Appkontrolelement
description: Sådan bruges appkontrol og -tillid til programmer
keywords: Microsoft-administreret skrivebord, Microsoft 365, tjeneste, dokumentation
ms.service: m365-md
author: tiaraquan
ms.author: tiaraquan
manager: dougeby
audience: ITpro
ms.topic: article
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.openlocfilehash: 108c4d3d64f503d2221aed9df9724faee85b2998
ms.sourcegitcommit: 559df2c86a7822463ce0597140537bab260c746a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/15/2022
ms.locfileid: "63588664"
---
# <a name="app-control"></a>Appkontrolelement

Appkontrol er en valgfri sikkerhedspraksis i Microsoft Managed Desktop, der begrænser udførelse af kode på klientenheder.

Denne kontrol reducerer risikoen for malware eller skadelige scripts. Kontrolelementet kræver, at kun koder, der er signeret af en kundegodkendt liste over udgivere, kan køre. Denne kontrol giver mange sikkerhedsfordele, men det er primært en fordel at beskytte data og identitet mod klientbaserede udnyttelser.

Microsoft Managed Desktop forenkler administrationen af politikker for appkontrol ved at oprette en grundlæggende politik, der aktiverer de grundlæggende produktivitetsscenarier. Du kan udvide tillid til andre underskrivere, der er specifikke for apps og scripts i dit miljø.

Enhver sikkerhedsteknologi kræver en balance mellem brugeroplevelse, sikkerhed og omkostninger. Appkontrol reducerer risikoen for skadelig software i dit miljø, men det har konsekvenser for brugeren og yderligere handlinger for din it-administrator.

| Yderligere sikkerhed og ansvarsområder | Beskrivelse |
| ------ | ------ |
| Ekstra sikkerhed | Apps eller scripts, der ikke er tillid til af politikken for appkontrol, er blokeret fra at køre på enheder. |
| Dine yderligere ansvarsområder | <ul><li>Du er ansvarlig for at teste dine apps for at identificere, om de blev blokeret af programkontrolpolitikken.</li><li>Hvis en app er (eller ville blive) blokeret, er du ansvarlig for at identificere de nødvendige oplysninger om underskriveren. Du skal anmode om en ændring via administrationsportalen.</li></ul>
| Microsoft Managed Desktop-ansvarsområder | <ul><li>Microsoft Managed Desktop vedligeholder basispolitikken, der aktiverer kerneprodukter fra Microsoft, Microsoft 365 Apps, Windows, Teams, OneDrive osv.</li><li>Microsoft Managed Desktop indsætter dine pålidelige underskrivere og installerer den opdaterede politik på dine enheder.</li></ul>

## <a name="managing-trust-in-applications"></a>Administrere tillid til programmer

Microsoft Managed Desktop bruger en grundlæggende politik, der har tillid til de vigtigste komponenter i Microsoft-teknologier. Du kan derefter *tilføje tillid* til dine egne programmer og scripts ved at informere Microsoft Managed Desktop om, hvilke apps og scripts du allerede har tillid til.

### <a name="base-policy"></a>Grundpolitik

Microsoft Managed Desktop opretter og vedligeholder en standardpolitik i samarbejde med Microsoft-eksperter inden for cybersikkerhed. Denne standardpolitik:

- Aktiverer de fleste apps, der er Microsoft Intune.
- Blokerer skadelige aktiviteter som kompilering af kode eller udførelse af filer, der ikke er tillid til.

Grundpolitikken har følgende tilgang til begrænsning af softwareudførelse:

- Filer, der køres af administratorer, har tilladelse til at køre.
- Filer på placeringer, der *ikke er* i bruger-skrivbare mapper, får tilladelse til at køre.
- Filer er signeret af en [underskriver, der er tillid til](#signer-requests).
- De fleste filer, der er signeret af Microsoft, kører, men nogle er blokeret for at forhindre handlinger med høj risiko såsom kompilering af kode.

Hvis en bruger, bortset fra en administrator, kunne have føjet en app eller et script til en enhed (dvs. den er i en brugers skrivbare mappe), tillader vi ikke, at den køres. Vi tillader udførelse, hvis appen eller scriptet allerede er blevet tilladt af en administrator.

Vores politik stopper udførelsen af apps i følgende scenarier:

- Hvis en bruger er blevet narret til at forsøge at installere malware.
- Hvis en sikkerhedsrisiko i en app, som brugeren kører, forsøger at installere malware.
- Hvis en bruger bevidst forsøger at køre en uautoriseret app eller et uautoriseret script.

### <a name="signer-requests"></a>Underskriversanmodninger

Du oplyser os om, hvilke apps der leveres af de softwareudgivere, du har tillid til, ved at *arkivere en underskriveranmodning*. Når vi gør det, gør vi følgende:

- Føj disse oplysninger om tillid til kontrolelementpolitikken for det oprindelige program.
- Tillad, at software, der er signeret med den pågældende udgivers certifikat, kan køre på dine enheder.

## <a name="audit-and-enforced-policies"></a>Overvågning og gennemtvungne politikker

Microsoft-administreret skrivebord anvender Microsoft Intune til at give appkontrol:

### <a name="audit-policy"></a>Overvågningspolitik

Denne politik opretter logfiler for at registrere, om en app eller et script blokeres af politikken Gennemtvungen.

Overvågningspolitikker gennemtvinger ikke regler for appkontrol. De er beregnet til testformål for at identificere, om et program kræver en udgiverfritagelse. Der logges advarsler (8003- eller 8006-hændelser) i Logbog i stedet for at blokere udførelse eller installation af angivne apps eller script.

### <a name="enforced-policy"></a>Gennemtvunget politik

Denne politik blokerer kørsel af upålidelige apps og scripts og opretter logfiler, når en app eller et script blokeres. Gennemtvungne politikker forhindrer almindelige brugere i at udføre apps eller scripts, der er gemt i bruger skrivbare mapper.

Enheder i gruppen Test har anvendt en overvågningspolitik for at validere, om nogen programmer kan medføre problemer. Alle andre grupper (Først, Hurtig og Bred) bruger en gennemtvungen politik. Brugere i disse grupper kan ikke køre upålidelige apps eller scripts.
