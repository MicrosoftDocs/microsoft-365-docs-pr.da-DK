---
title: Find og løs problemer efter at have tilføjet dit domæne eller DNS-poster
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
- Adm_O365_Setup
ms.custom:
- AdminSurgePortfolio
- okr_smb
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
- GEA150
ms.assetid: 40398b0b-bdd0-4afd-ab5e-b5ae6b7990bf
description: Få mere at vide om, hvordan du finder de problemer, du løber ind i under konfigurationen af et brugerdefineret domæne, ved at sikre, at DNS-posterne er konfigureret korrekt.
ms.openlocfilehash: 7fa5a18ff0e4b7f0db8749f5659fefdd89cb3fcd
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63590774"
---
# <a name="find-and-fix-issues-after-adding-your-domain-or-dns-records"></a>Find og løs problemer efter at have tilføjet dit domæne eller DNS-poster

 **[Tjek ofte stillede spørgsmål om](../setup/domains-faq.yml)** domæner, hvis du ikke kan finde det, du leder efter. 
  
Det kan være en udfordring at få konfigureret dit domæne Microsoft 365 at arbejde sammen med andre. DNS-systemet er vigtigt at arbejde med, og DNS-konfigurationen for dit domæne påvirker vigtige forretningsaktiviteter, f.eks. mail!

> [!NOTE]
> Du kan kontrollere, om der er problemer med dit domæne, ved at kontrollere dets status. Gå til **SetupDomains** > , og få vist meddelelserne i **kolonnen Status**. Hvis du ser et problem, skal du vælge de tre prik (flere handlinger) og derefter vælge **Kontrollér tilstand**. Den rude, der åbnes, beskriver eventuelle problemer, der opstår med dit domæne.
  
## <a name="whats-going-on"></a>Hvad sker der?

- [Kan du ikke bekræfte dit domæne?](#cant-verify-your-domain)
    
- [Outlook fungerer ikke?](#outlook-isnt-working)
    
- [Alles mail er blevet flyttet til en Microsoft 365 og du ville kun have DIN mail til at skifte?](#everyones-email-got-switched-to-microsoft-365-and-you-only-wanted-your-email-to-switch)

- [Kan du ikke bekræfte status for non-profit- eller skolekonto?](#cant-confirm-non-profit-or-school-account-status)

- [Fungerer tjenesterne ikke med dit domæne?](#services-not-working-with-your-domain)
    
- [Fungerer adgangen til dit websted ikke?](#accessing-your-website-isnt-working)

## <a name="cant-verify-your-domain"></a>Kan du ikke bekræfte dit domæne?

Der er et par almindelige årsager til, at domænebekræftelsen ikke fungerer, som den skal:
  
1. **Værdien af bekræftelsesposten er ikke helt korrekt.** Dobbelttjek, at du har kopieret og indsat den nøjagtige værdi i TXT-bekræftelsesposten hos din DNS-vært. Ét almindelige problem er ikke omfatter "MS = " delen af posten. Vi har også brug for den! 
    
2. **Posten er ikke blevet gemt.** Hos nogle DNS-værter skal du gemme zonefilen (hvor DNS-posten er gemt), så den bliver opdateret på hele internettet. Sørg for, at du har gemt dine ændringer, Microsoft 365 du kan se og bekræfte posten. 
    
3. **Posten er ikke opdateret på hele internettet.** Det tager typisk et par minutter for os at få vist den nye post, men nogle gange kan det tage op til et par timer. 
    
## <a name="outlook-isnt-working"></a>Outlook fungerer ikke?

Hvis du har konfigureret din MX-post og andre DNS-poster korrekt til dit domæne, men mail ikke virker, så lad os hjælpe dig med at løse [dine Outlook problemer](/exchange/troubleshoot/outlook-connectivity/outlook-connection-issues).
  
## <a name="everyones-email-got-switched-to-microsoft-365-and-you-only-wanted-your-email-to-switch"></a>Alles mail er blevet flyttet til en Microsoft 365 og du ville kun have DIN mail til at skifte?
<a name="BKMK_EmailSwitched"> </a>

Når du føjer dit domæne til Microsoft 365, opdateres domænets MX-post typisk (af dig eller Microsoft 365), så den peger på Microsoft 365, og alle de mails, der sendes til dette domæne, vil blive sendt til Microsoft 365. Sørg for, at du har oprettet postkasser i Microsoft 365 for alle, der har mail på dit domæne, FØR du ændrer MX-posten.
  
Hvad nu, hvis du ikke vil flytte mails for alle på dit domæne til Microsoft 365? Du kan prøve køre [pilotprojekter med Microsoft 365 blot et par mailadresser i stedet](../setup/domains-faq.yml).
  
## <a name="cant-confirm-non-profit-or-school-account-status"></a>Kan du ikke bekræfte status for non-profit- eller skolekonto?
<a name="BKMK_validateAcct"> </a>

Der er et par scenarier, hvor du blot har brug for at bekræfte din organisations domæne og ikke konfigurere nogen tjenester. Hvis du f.eks. vil bevise, Microsoft 365, at din organisation er kvalificeret til et skoleabonnement.
  
Se vejledningen i Bekræfte dit Microsoft 365-domæne for at bevise [ejerskabet, status som nonprofitorganisation](../setup/domains-faq.yml) eller uddannelse eller for at aktivere Yammer for at sikre, at du har gennemført alle de påkrævede trin. Det er lidt forskelligt for hver situation. 
  
## <a name="services-not-working-with-your-domain"></a>Fungerer tjenesterne ikke med dit domæne?

Vi kan hjælpe dig med at finde problemer med domænets DNS-konfiguration. Domænefejlfinding i Microsoft 365 viser dig de poster, der er problemer med, og præcis, hvad posterne skal være indstillet til. 

> [!TIP]
> Har du din DNS konfigureret korrekt, men mail fungerer ikke i Outlook på skrivebordet? Se de forskellige scenarier for mailflow, du kan [have med Microsoft 365](/exchange/mail-flow-best-practices/mail-flow-best-practices) for at sikre, at du har konfigureret tingene korrekt for din virksomhed. Eller få mere hjælp til fejlfinding med mail her: [Løs Outlook problemer](/exchange/troubleshoot/outlook-connectivity/outlook-connection-issues). 
  
## <a name="accessing-your-website-isnt-working"></a>Fungerer adgangen til dit websted ikke?

Hvis du har løst DNS-problemer, og du stadig har problemer, kan du prøve et af følgende.
  
- Andre kan ikke få adgang til dit websted på *contoso.com*: [Finde webstedsproblemer](../setup/add-domain.md)
    
- Du kan ikke opdatere din A-post eller CNAME-post til at pege på dit websted: Opdatere [brugerdefinerede DNS-poster Microsoft 365](../setup/add-domain.md)

## <a name="related-content"></a>Relateret indhold

[Fejlfinding: Overhold data på bekræftet domæneændring](/azure/active-directory/reports-monitoring/troubleshoot-audit-data-verified-domain) (artikel)\
[Ofte stillede spørgsmål om domæner](../setup/domains-faq.yml) (artikel)

