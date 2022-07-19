---
title: Installér og konfigurer tilføjelsesprogrammet til rapportmeddelelsen
description: Trinnene til installation og konfiguration af Microsofts tilføjelsesprogram(er) til phishrapportering, der er målrettet sikkerhedsadministratorer
search.product: ''
search.appverid: ''
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTBen
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-guidance-templates
ms.topic: how-to
ms.technology: mdo
ms.openlocfilehash: 36e3fe25444f57de4cd43d67cab5a99f546a0f13
ms.sourcegitcommit: a209c9f86a7b4340a426c4cfed2d36a388c71124
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/15/2022
ms.locfileid: "66859010"
---
# <a name="deploy-and-configure-the-report-message-add-in-to-users"></a>Udrul og konfigurer tilføjelsesprogrammet til rapportmeddelelsen til brugere.

Tilføjelsesprogrammet Rapportmeddelelse og rapport phishing til Outlook gør det nemt at rapportere phishing til Microsoft og microsofts associerede virksomheder til analyse sammen med nem gennemgang for administratorer på [indsendelsesportalen](https://security.microsoft.com/reportsubmission?viewid=user). 

Afhængigt af om du har licens til Defender for Office 365, får du også yderligere funktionalitet, f.eks. besked om & automatiseret undersøgelse og svar (AIR), hvilket vil fjerne byrden fra dine sikkerhedsmedarbejdere. Denne vejledning fører dig gennem konfigurationen af udrulningen af tilføjelsesprogrammet som anbefalet af Microsoft Defender for Office 365 team.

## <a name="choose-between-which-add-in-to-deploy"></a>Vælg mellem, hvilket tilføjelsesprogram der skal installeres

- Tilføjelsesprogrammet Rapport phishing giver mulighed for kun at rapportere phishing-meddelelser
- Tilføjelsesprogrammet Rapportmeddelelse giver mulighed for at rapportere uønsket post og ikke uønsket post (falsk positiv) og phishing-meddelelser


## <a name="what-youll-need"></a>Det skal du bruge

-   Exchange Online Protection (nogle funktioner kræver Defender for Office 365 Plan 2)
-   Tilstrækkelige tilladelser (global administrator til installation af tilføjelsesprogrammer, sikkerhedsadministrator til tilpasning)
- 5-10 minutter for at udføre trinnene nedenfor

## <a name="deploy-the-add-in-for-users"></a>Udrul tilføjelsesprogrammet til brugere

1.  **Log på** Microsoft 365 Administration.  https://admin.microsoft.com.
1.  Tryk på **Vis alle** i venstre navigationsrude, udvid derefter **Indstillinger** , og vælg **Integrerede apps**.
1.  Tryk på **Hent apps** på den side, der indlæses.
1.  På den side, der vises, skal du i søgefeltet øverst til højre angive **Rapportmeddelelse** eller **Rapport phishing** og derefter vælge **Søg**.
1.  Tryk på **Hent den nu** i den valgte app i søgeresultaterne (udgiveren er **Microsoft Corporation**).
1.  På det pop op-vindue, der vises, skal du vælge, hvem tilføjelsesprogrammet skal installeres på. Hvis du tester, vil du måske bruge en bestemt gruppe, ellers skal du konfigurere den for **hele organisationen** – når du har foretaget et valg, skal du trykke på **Næste**.
1.  Gennemse tilladelser, oplysninger og egenskaber, og tryk derefter på **Næste**.
1.  Tryk på **Udfør udrulning** (det kan tage 12-24 timer, før tilføjelsesprogrammet vises automatisk i Outlook-klienter).

## <a name="configure-the-add-in-for-users"></a>Konfigurer tilføjelsesprogrammet for brugere
1.  **Log på** Microsoft Security-portalen på https://security.microsoft.com.
2.  Vælg Politikker & regler under **Mail & samarbejde** i venstre navigationsrude.
3.  Vælg **Trusselspolitikker**.
4.  Vælg **Brugerrapporterede meddelelsesindstillinger** under overskriften **Andre** .
5.  Kontrollér, at **knappen Microsoft Outlook-rapportmeddelelse** er **slået til.**
6.  Under **Send de rapporterede meddelelser for at** vælge **Microsoft** (anbefales).
7.  Sørg for **, at Lad brugerne vælge, om de vil rapportere** , ikke er markeret, og **rapportér altid meddelelsen** er valgt.
8.  Tryk på **Gem**.

## <a name="optional-steps--configure-notifications"></a>Valgfrie trin – konfigurer meddelelser

1.  På konfigurationssiden fra de tidligere trin under **brugerrapporteringsoplevelsen** skal du konfigurere pop op-titel og brødtekst før og efter rapportering, hvis det er nødvendigt. Slutbrugerne får vist pop op-vinduet før rapportering, hvis **Spørg mig, før rapportering** også er aktiveret.
2.  Hvis du ønsker, at meddelelser skal komme fra en intern organisationspostkasse, skal du vælge **Angiv Office 365 mailadresse, der skal bruges som afsender**, og søge efter en gyldig postkasse i din organisation, hvorfra meddelelserne skal sendes.
3.  Tryk på **Tilpas meddelelser** for at konfigurere den tekst, der sendes til rapportbrugere, efter at administratoren har gennemset en rapporteret meddelelse ved hjælp af Markér & Giv besked, konfigurer indstillingerne **Phishing**, **Uønsket** & **ingen trusler** fundet.
4.  Under fanen **Sidefod** skal du vælge den globale sidefod, der skal sendes til meddelelser, sammen med organisationens logo, hvis det er relevant.


### <a name="further-reading"></a>Yderligere læsning
Få mere at vide om brugerrapporterede meddelelsesindstillinger [Brugerrapporterede meddelelsesindstillinger – Office 365 | Microsoft Docs](../user-submission.md)

Aktivér tilføjelsesprogrammet Tilføjelsesprogram til rapportmeddelelse eller rapport phishing [Aktivér tilføjelsesprogrammet Rapportmeddelelse eller Rapport phishing – Office 365 | Microsoft Docs](../enable-the-report-message-add-in.md)
