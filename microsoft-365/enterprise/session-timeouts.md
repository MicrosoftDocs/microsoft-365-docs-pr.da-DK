---
title: Sessionstimeouts for Microsoft 365
ms.author: tracyp
author: MSFTTracyP
manager: scotv
ms.date: 6/29/2018
audience: Admin
ms.topic: reference
ms.service: o365-administration
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- BCS160
ms.assetid: 37a5c116-5b07-4f70-8333-5b86fd2c3c40
ms.collection:
- M365-security-compliance
description: Få mere at vide om, hvordan sessionstimeouts bruges til at afbalancere sikkerhed og nem adgang i Microsoft 365-klientapps.
ms.openlocfilehash: f5b7c87cabfd6f80061c2795568cd53955caa10f
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63590318"
---
# <a name="session-timeouts-for-microsoft-365"></a>Sessionstimeouts for Microsoft 365

Sessionens levetid er en vigtig del af godkendelse til Microsoft 365 og er en vigtig komponent i justering af sikkerhed og det antal gange, brugerne bliver bedt om at angive deres legitimationsoplysninger.

## <a name="session-times-for-microsoft-365-services"></a>Sessionstider for Microsoft 365 tjenester

Når brugerne godkendes i en af de Microsoft 365 webapps eller mobilapps, oprettes der en session. Under sessionens varighed behøver brugerne ikke at godkende igen. Sessioner kan udløbe, når brugere er inaktive, når de lukker browseren eller fanen, eller når deres godkendelsestoken udløber af andre årsager, f.eks. når adgangskoden er blevet nulstillet. Tjenesten Microsoft 365 forskellige sessionstimeouts, så de svarer til den typiske brug af hver tjeneste.

I følgende tabel vises sessionens levetid for Microsoft 365 tjenester:

| Microsoft 365 tjeneste | Timeout for session |
|:-----|:-----|
|Microsoft 365 Administration  <br/> |Du bliver bedt om at angive legitimationsoplysninger til Administration hver 8. time.  <br/> |
|SharePoint Online  <br/> |5 dages inaktivitet, så længe brugerne vælger **Forvar mig logget på**. Hvis brugeren får adgang SharePoint Online igen, efter der er gået 24 timer eller mere siden forrige logon, nulstilles timeoutværdien til 5 dage.  <br/> |
|Outlook Web App  <br/> |6 timer.  <br/> Du kan ændre denne værdi ved hjælp  _af ActivityBasedAuthenticationTimeoutInterval-parameteren_ i [Set-OrganizationConfig-cmdlet'en](/powershell/module/exchange/set-organizationconfig) .  <br/> |
|Azure Active Directory  <br/> (Bruges af Office og Microsoft 365 i Windows klienter med moderne godkendelse aktiveret)  <br/> | Moderne godkendelse bruger adgangstokens og opdateringstokens til at give brugeradgang til ressourcer, Microsoft 365 bruger Azure Active Directory. Et adgangstoken er en JSON-webtoken, der er gyldig i én time og leveres efter en vellykket godkendelse. Der leveres også en opdateringstoken med længere levetid. Når adgangstokens udløber, Office en gyldig opdateringstoken til at opnå en ny adgangstoken. Denne udveksling lykkes, hvis brugerens oprindelige godkendelse stadig er gyldig.  <br/>  Opdateringstokens er gyldige i 90 dage, og med fortløbende brug kan de være gyldige, indtil de tilbagekaldes.  <br/>  Opdateringstokens kan blive ugyldige ved flere hændelser, f.eks.:  <br/>  Brugerens adgangskode er ændret, siden opdateringstokenet blev udstedt.  <br/>  En administrator kan anvende politikker for betinget adgang, der begrænser adgangen til ressourcen, som brugeren forsøger at få adgang til.  <br/> |
|SharePoint og OneDrive til Android, iOS og Windows 10  <br/> |Standardlevetid for adgangstoken er 1 time. Den maksimale tid, som opdateringstokenet kan være inaktivt, er som standard 90 dage.  <br/> [Få mere at vide om tokens, og hvordan du konfigurerer tokenlevetid](/azure/active-directory/active-directory-configurable-token-lifetimes) <br/> Hvis du vil tilbagekalde opdateringstokenet, kan du nulstille brugerens Microsoft 365 adgangskode  <br/> |
|Yammer med Microsoft 365 Sign-In  <br/> |Browserens levetid. Hvis brugere lukker browseren og får adgang Yammer en ny browser, vil Yammer godkende dem igen med Microsoft 365. Hvis brugerne bruger tredjepartsbrowsere, der cachelagrer cookies, skal de muligvis ikke godkende igen, når de åbner browseren igen.  <br/> > [!NOTE]> Dette gælder kun for netværk, der bruger Microsoft 365 Sign-In til Yammer.           |