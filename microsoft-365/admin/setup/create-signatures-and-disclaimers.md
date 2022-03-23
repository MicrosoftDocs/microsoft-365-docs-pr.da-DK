---
title: Opret signaturer og ansvarsfraskrivelser for hele organisationen
f1.keywords:
- NOCSH
ms.author: twerner
author: twernermsft
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- TRN_M365B
- OKR_SMB_Videos
- seo-marvel-may2020
- AdminSurgePortfolio
- okr_smb
- AdminTemplateSet
- adminvideo
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 2d75860f-c527-4352-a7f6-73eba54c0c72
description: Administrer mailsignaturer, herunder ansvarsfraskrivelser eller hemmeligholdelseserklæringer for alle mails, der kommer ind i eller forlader organisationen.
ms.openlocfilehash: d2e8b93825b98724bfd2698d95b93289dee30e00
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/15/2021
ms.locfileid: "63588569"
---
# <a name="create-organization-wide-signatures-and-disclaimers"></a>Opret signaturer og ansvarsfraskrivelser for hele organisationen

 Du kan administrere mailsignaturer ved at føje en mailsignatur, ansvarsfraskrivelse eller hemmeligholdelseserklæringer til de mails, der kommer ind i eller forlader organisationen. Du kan konfigurere den til at gælde for alle indgående og udgående meddelelser, som vist nedenfor. Eller du kan anvende den på bestemte meddelelser, såsom dem, der indeholder bestemte ord eller tekstmønstre.

## <a name="watch-create-a-company-wide-email-signature"></a>Se: Opret en signatur for hele virksomheden
  
> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE1IEWf] 

1. Vælg <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 Administration</a> i **Exchange**.
1. Vælg **Mailflow**.
1. Vælg **Tilføj +**, og vælg derefter **Anvend ansvarsfraskrivelser**.
1. På siden **Ny regel** skal du udføre trinnene. 

Hvis du synes, denne video var nyttig, kan du [se den komplette kursusserie til små virksomheder og dem, der er nye Microsoft 365](../../business-video/index.yml).

## <a name="create-a-signature-that-applies-to-all-messages"></a>Oprette en signatur, der gælder for alle meddelelser

> [!TIP]
> Signaturer for hele organisationen kaldes "ansvarsfraskrivelser", uanset hvad de indeholder. De kan f.eks. bare være en signatur eller også inkludere din adresse, din juridiske ansvarsfraskrivelse eller andre oplysninger, du ønsker.
    
::: moniker range="o365-worldwide"

Gå til Administration på <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a>.

::: moniker-end

::: moniker range="o365-21vianet"

Gå til Administration på <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">https://portal.partner.microsoftonline.cn/adminportal</a>.

::: moniker-end

1. Vælg appstarteren ![Ikonet for appstarteren](../../media/7502f4ec-3c9a-435d-a7b4-b9cda85189a7.png), og vælg derefter **Administrator**.
   
    Kan du ikke finde den app, du leder efter? Fra appstarteren skal du vælge Alle **apps for** at få vist en alfabetisk liste over de apps, der er tilgængelige for dig. Derfra kan du søge efter en bestemt app. 
    
2. Vælg **Administration**, og vælg derefter **Exchange**.
    
3. Under Mailflow skal du vælge **Regler**.
    
4. Vælg ikonet **+** (Tilføj), og vælg Anvend **ansvarsfraskrivelser**.
    
5. Navngive reglen.
    
6. Under **Anvend denne regel** skal du **vælge [Anvend på alle meddelelser]**.
    
    > [!TIP]
    > [Få mere](/Exchange/policy-and-compliance/mail-flow-rules/signatures#Scoping) at vide om at anvende betingelser, hvis du ikke vil have, at ansvarsfraskrivelsen anvendes på alle meddelelser. (Denne angivelse af artikel er til Exchange Server, men den gælder også for Microsoft 365).) 
  
7. Under Gør følgende skal du lade **Tilføj ansvarsfraskrivelsen være** markeret. 
    
8.  Vælg **Skriv tekst,** og skriv din ansvarsfraskrivelse. 
    
    > [!TIP]
    > [Få mere at vide](/Exchange/policy-and-compliance/mail-flow-rules/signatures#FormatDisclaimer) om at formatere ansvarsfraskrivelser. (Denne formateringsartikel er til Exchange Server, men den gælder også for Microsoft 365.) 

9. Vælg **Vælg en,** og vælg **Ombryd** som reserveindstilling. Derefter **OK**. Det betyder, at hvis ansvarsfraskrivelsen ikke kan tilføjes på grund af kryptering eller en anden mailindstilling, ombrydes den i en konvolut.
    
10. Lad **Overhold reglen med alvorsniveau være** markeret. Vælg derefter **Lav**, **Mellem eller** Høj, **der** skal bruges i meddelelsesloggen. 
    
11. Vælg **Gennemtving** for at slå ansvarsfraskrivelsen til med det samme, medmindre du vil teste den først. 
    
12. Vælg **Flere indstillinger for** at medtage yderligere betingelser eller undtagelser. 
    
13. Vælg **Gem,** når du er færdig. 
    
## <a name="limitations-of-organization-wide-signatures"></a>Begrænsninger for signaturer for hele organisationen

Du kan ikke gøre følgende, når du administrerer mailsignaturer i Microsoft 365:
  
- Indsæt signaturen direkte under det seneste mailsvar eller -videresendelsen
    
- Vise mailsignaturer på serversiden i brugernes sendt post-mapper
    
- Integrer billeder i mailsignaturer
    
- Spring linjer over, som indeholder variabler, der ikke kunne opdateres (f.eks. fordi værdien ikke blev angivet for en bruger)
    
For at få disse og andre funktioner til at administrere mailsignaturer skal du bruge et tredjepartsværktøj. Søg efter mailsignatursoftware **på internettet**. En række af disse udbydere er Microsoft Gold-partnere, og deres software leverer disse egenskaber. 
  
## <a name="more-resources"></a>Flere ressourcer

Du kan finde oplysninger om brug af PowerShell under [Ansvarsfraskrivelser, signaturer, sidefødder](/exchange/security-and-compliance/mail-flow-rules/disclaimers-signatures-footers-or-headers) eller sidehoveder for hele organisationen Exchange Online.

## <a name="related-content"></a>Relateret indhold

[Overfør mail og kontakter til Microsoft 365](migrate-email-and-contacts-admin.md) (video)\
[Brugermailindstillinger](../email/office-365-user-email-settings.md) (artikel)\
[Oversigt over Microsoft 365 Administration](Oversigt over Microsoft 365 Administration](.. /admin-overview/admin-center-overview.md) (video)

