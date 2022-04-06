---
title: Phishingtendenser og -teknikker
ms.reviewer: ''
description: Få mere at vide om, hvordan du spotter phishingteknikker
keywords: sikkerhed, malware, phishing, oplysninger, svindel, social engineering, bait, tilsnende, beskyttelse, tendenser, målrettet angreb, phishing phishing, whaling
ms.prod: m365-security
ms.mktglfcycl: secure
ms.sitesec: library
ms.localizationpriority: medium
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
search.appverid: met150
ms.technology: m365d
ms.openlocfilehash: fbd86a25b6f1224748225263103e13ca07f93166
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/20/2022
ms.locfileid: "63706185"
---
# <a name="phishing-trends-and-techniques"></a>Phishingtendenser og -teknikker

Phishing-angreb er svindel, der ofte bruger social engineering til at lokke med indhold. Kommunikation med et legitimt udseende, som regel mails, der linker til et phishingwebsted, er en af de mest almindelige metoder til phishing-angreb. Phishing-webstedet efterligner typisk logonsider, der kræver, at brugerne skal indtaste legitimationsoplysninger og kontooplysninger. Phishingwebstedet registrerer derefter de følsomme oplysninger, så snart brugeren giver dem, og giver hackere adgang til oplysningerne.

Nedenfor er nogle af de mest almindelige phishingteknikker, hackere kan anvende til at forsøge at stjæle oplysninger eller få adgang til dine enheder.

## <a name="invoice-phishing"></a>Fakturaphishing

I dette svindelnummer forsøger hackeren at snyde dig med en mail om, at du har en udestående faktura fra en kendt leverandør eller virksomhed. De indeholder derefter et link, som du kan bruge til at få adgang til og betale din faktura. Når du åbner webstedet, vil hackeren stjæle dine personlige oplysninger og midler.

## <a name="paymentdelivery-scam"></a>Svindel med betaling/levering

Du bliver bedt om at angive et kreditkort eller andre personlige oplysninger, så dine betalingsoplysninger kan opdateres med en almindeligt kendt leverandør eller leverandør. Der anmodes om en opdatering, så du kan tage imod levering af dine bestilte varer. Generelt kan du være bekendt med virksomheden og sandsynligvis have gjort forretninger med dem tidligere. Du er dog ikke klar over nogen elementer, du for nylig har købt hos dem.

## <a name="tax-themed-phishing-scams"></a>Skattet phishingsvindel

Et almindeligt forsøg på phishing i IRS modtager et vigtigt mailbrev, der angiver, at du skylder penge til IRS. Mailen truer ofte juridiske handlinger, hvis du ikke får rettidig adgang til webstedet og betaler din moms. Når du åbner webstedet, kan hackerne stjæle dit personlige kreditkort eller dine bankoplysninger og tømme dine konti.

## <a name="downloads"></a>Downloads

En hacker sender en svigagtig mail, der anmoder dig om at åbne eller downloade en vedhæftet fil, f.eks. en PDF-fil. Den vedhæftede fil indeholder ofte en meddelelse, der beder dig om at logge på et andet websted, f.eks. mail eller websteder til fildeling, for at åbne dokumentet. Når du åbner disse phishingwebsteder ved hjælp af dine logonoplysninger, har hackeren nu adgang til dine oplysninger og kan få yderligere personlige oplysninger om dig.

## <a name="phishing-emails-that-deliver-other-threats"></a>Phishingmails, der leverer andre trusler

Phishingmails er ofte effektive, så hackere bruger dem nogle gange til at distribuere [ransomware](/security/compass/human-operated-ransomware) via links eller vedhæftede filer i mails. Når den køres, krypterer ransomware filer og viser en notat, som beder dig om at betale en sum penge for at få adgang til dine filer.

Vi har også set phishing-mails, der har links til [svindelwebsteder for teknisk support](support-scams.md) . Disse websteder bruger forskellige besværlige taktikker til at narre dig til at ringe til og betale for unødvendige "tekniske supporttjenester", som angiveligt løser problemer med enheder, platforme eller software.

## <a name="spear-phishing"></a>Phishing

Phishing med phishing er et målrettet phishingangreb, der involverer meget tilpasset indhold. Hackere vil typisk genoptage deres arbejde ved at undersøge sociale medier og andre informationskilder om deres tilsigtede mål.

Phishing kan være en mulighed for at narre dig til at logge på falske websteder og dele legitimationsoplysninger. Jeg kan også lokke dig til at åbne dokumenter ved at klikke på links, der automatisk installerer malware. Når denne malware er på plads, kan hackere fjernstyre den inficeret computer.

Den malware, der spredes, fungerer som indgangspunkt for et mere avanceret angreb, også kaldet en avanceret vedvarende trussel (APT). APT'er er designet til at etablere kontrol og stjæle data over længere perioder. Hackere kan forsøge at installere flere skjulte hackingværktøjer, flytte til andre computere senere, gå på kompromis med eller oprette privilegerede konti og jævnligt eksfiltrere oplysninger fra kompromitterede netværk.

## <a name="whaling"></a>Whaling

Whaling er en form for phishing, der dirigeres til ledere på højt niveau eller i ledende virksomheder i specifikke virksomheder for at få adgang til deres legitimationsoplysninger og/eller bankoplysninger. Indholdet af mailen kan skrives som en juridisk stævning, en kundeklage eller et andet ledelsesproblem. Denne type angreb kan også føre til et APT-angreb i en organisation.

## <a name="business-email-compromise"></a>Kompromis med virksomhedsmail

Business email compromise (BEC) er et avanceret svindelnummer, der er målrettet virksomheder, der ofte arbejder med fremmede leverandører eller gør pengeoverførsel. En af de mest almindelige systemer, der bruges af BEC-hackere, er at få adgang til en virksomheds netværk via et phishingangreb, som du ønsker at undgå. Hackeren opretter et domæne, der ligner det firma, de målretter, eller spoofs deres mail for at snyde brugere til at frigive personlige kontooplysninger ved pengeoverførsler.

## <a name="more-information-about-phishing-attacks"></a>Flere oplysninger om phishing-angreb

Du kan finde oplysninger om de nyeste phishing-angreb, -teknikker og -tendenser ved at læse disse poster på [Microsoft Security-bloggen](https://www.microsoft.com/security/blog/product/windows/):

- [Phishere slipper simple, men effektive social engineering-teknikker ved hjælp af vedhæftede PDF-filer](https://cloudblogs.microsoft.com/microsoftsecure/2017/01/26/phishers-unleash-simple-but-effective-social-engineering-techniques-using-pdf-attachments/?source=mmpc)
- [Tax themed phishing and malware attacks prolifeliferate during the tax filing season](https://cloudblogs.microsoft.com/microsoftsecure/2017/03/20/tax-themed-phishing-and-malware-attacks-proliferate-during-the-tax-filing-season/?source=mmpc)
- [Phishing som mails fører til svindel med teknisk support](https://cloudblogs.microsoft.com/microsoftsecure/2017/08/07/links-in-phishing-like-emails-lead-to-tech-support-scam/?source=mmpc)
