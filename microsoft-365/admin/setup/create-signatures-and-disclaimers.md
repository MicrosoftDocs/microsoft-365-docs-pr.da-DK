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
description: Administrer mailsignaturer, herunder juridiske ansvarsfraskrivelser eller afsløringserklæringer for alle mails, der kommer til eller forlader din organisation.
ms.openlocfilehash: 47e6a862441b5c2725a48cae20669541b8a69f87
ms.sourcegitcommit: e9692a40dfe1f8c2047699ae3301c114a01b0d3a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/01/2022
ms.locfileid: "66602806"
---
# <a name="create-organization-wide-signatures-and-disclaimers"></a>Opret signaturer og ansvarsfraskrivelser for hele organisationen

Se [Hjælp til små virksomheder i Microsoft 365](https://go.microsoft.com/fwlink/?linkid=2197659) på YouTube.

 Du kan administrere mailsignaturer ved at føje en mailsignatur, juridisk ansvarsfraskrivelse eller afsløringserklæring til de mails, der kommer ind i eller forlader din organisation. Du kan konfigurere den til at gælde for alle indgående og udgående meddelelser som vist nedenfor. Eller du kan anvende den på bestemte meddelelser, f.eks. dem, der indeholder bestemte ord eller tekstmønstre.

## <a name="watch-create-a-company-wide-email-signature"></a>Se: Opret en mailsignatur for hele virksomheden
  
Se denne video og andre på vores [YouTube-kanal](https://go.microsoft.com/fwlink/?linkid=2198031).

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE1IEWf] 

1. Vælg **Exchange** i <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 Administration</a>.
1. Vælg **Mailflow**.
1. Vælg **Tilføj +**, og vælg derefter **Anvend ansvarsfraskrivelser**.
1. På siden **Ny regel** skal du fuldføre trinnene. 

Hvis du har fundet denne video nyttig, kan du se den [komplette træningsserie for små virksomheder og nye i Microsoft 365](../../business-video/index.yml).

## <a name="create-a-signature-that-applies-to-all-messages"></a>Opret en signatur, der gælder for alle meddelelser

> [!TIP]
> Signaturer, der gælder for hele organisationen, kaldes "ansvarsfraskrivelser", uanset hvad de omfatter. De kan f.eks. blot være en signatur eller også indeholde din adresse, juridisk ansvarsfraskrivelse eller andre oplysninger, du ønsker.
    
::: moniker range="o365-worldwide"

Gå til Administration på <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a>.

::: moniker-end

::: moniker range="o365-21vianet"

Gå til Administration på <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">https://portal.partner.microsoftonline.cn/adminportal</a>.

::: moniker-end

1. Vælg appstarteren ![Ikonet for appstarteren,](../../media/7502f4ec-3c9a-435d-a7b4-b9cda85189a7.png) og vælg derefter **Administration**.
   
    Kan du ikke finde den app, du leder efter? Vælg **Alle apps** i appstarteren for at få vist en alfabetisk liste over de apps, der er tilgængelige for dig. Herfra kan du søge efter en bestemt app. 
    
2. Vælg **Administration centre**, og vælg derefter **Exchange**.
    
3. Under Mailflow skal du vælge **Regler**.
    
4. Vælg ikonet **+** (Tilføj), og vælg **Anvend ansvarsfraskrivelser**.
    
5. Giv reglen et navn.
    
6. Under **Anvend denne regel** skal du vælge **[Anvend på alle meddelelser]**.
    
    > [!TIP]
    > [Få mere at vide](/Exchange/policy-and-compliance/mail-flow-rules/signatures#Scoping) om anvendelse af betingelser, hvis du ikke ønsker, at ansvarsfraskrivelsen anvendes på alle meddelelser. (Denne artikel om Exchange Server er beregnet til Exchange Server, men den gælder også for Microsoft 365). 
  
7. Under Gør følgende skal du lade **Tilføj ansvarsfraskrivelsen** være valgt. 
    
8.  Vælg **Angiv tekst** , og skriv ansvarsfraskrivelsen. 
    
    > [!TIP]
    > [Få mere at vide](/Exchange/policy-and-compliance/mail-flow-rules/signatures#FormatDisclaimer) om formatering af ansvarsfraskrivelser. Denne formateringsartikel er til Exchange Server, men den gælder også for Microsoft 365. 

9. **Vælg Vælg en,** og vælg **Ombryd** som reserveindstilling. Så **OK**. Det betyder, at hvis ansvarsfraskrivelsen ikke kan tilføjes på grund af kryptering eller en anden mailindstilling, ombrydes den i en meddelelseskonvolut.
    
10. Lad **Overvåg denne regel med alvorsgradsniveau** være valgt. Vælg derefter **Lav**, **Mellem** eller **Høj** , der skal bruges i meddelelsesloggen. 
    
11. Vælg **Gennemtving** for at aktivere ansvarsfraskrivelsen med det samme, medmindre du vil teste den først. 
    
12. Vælg **Flere indstillinger** for at inkludere yderligere betingelser eller undtagelser. 
    
13. Vælg **Gem** , når du er færdig. 
    
## <a name="limitations-of-organization-wide-signatures"></a>Begrænsninger for organisationsdækkende signaturer

Du kan ikke gøre følgende, når du administrerer mailsignaturer i Microsoft 365:
  
- Indsæt signaturen direkte under det seneste svar eller videresendelse via mail
    
- Vis mailsignaturer på serversiden i brugernes Mapper sendt post
    
- Integrer billeder i mailsignaturer
    
- Spring linjer over, der indeholder variabler, der ikke kunne opdateres (f.eks. fordi værdien ikke blev angivet for en bruger)
    
Hvis du vil have disse og andre funktioner til at administrere mailsignaturer, skal du bruge et tredjepartsværktøj. Udfør en internetsøgning efter **mailsignatursoftware**. En række af disse udbydere er Microsoft Gold-partnere, og deres software leverer disse funktioner. 
  
## <a name="more-resources"></a>Flere ressourcer

Du kan få oplysninger om brug af PowerShell under [Ansvarsfraskrivelser, signaturer, sidefødder eller sidehoveder i Exchange Online for hele organisationen](/exchange/security-and-compliance/mail-flow-rules/disclaimers-signatures-footers-or-headers).

## <a name="related-content"></a>Relateret indhold

[Overfør mail og kontakter til Microsoft 365](migrate-email-and-contacts-admin.md) (video)\
[Indstillinger for brugermail](../email/office-365-user-email-settings.md) (artikel)\
[Oversigt over Microsoft 365 Administration](Oversigt over Microsoft 365 Administration](.. /admin-overview/admin-center-overview.md) (video)

