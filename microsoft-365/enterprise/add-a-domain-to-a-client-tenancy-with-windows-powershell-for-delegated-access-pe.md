---
title: Føj et domæne til en klients leje med Windows PowerShell for DAP-partnere
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- Ent_O365
- M365-subscription-management
f1.keywords:
- NOCSH
ms.custom:
- seo-marvel-apr2020
- admindeeplinkMAC
ms.assetid: f49b4d24-9aa0-48a6-95dd-6bae9cf53d2c
description: 'Oversigt: Brug PowerShell til Microsoft 365 til at føje et alternativt domænenavn til en eksisterende kundelejer.'
ms.openlocfilehash: 1a121407ebe242747a693084289e972e56e1cbee
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63591398"
---
# <a name="add-a-domain-to-a-client-tenancy-with-windows-powershell-for-delegated-access-permission-dap-partners"></a>Føj et domæne til en klients leje med Windows PowerShell for DAP-partnere (Delegated Access Permission)

*Denne artikel gælder for både Microsoft 365 Enterprise og Office 365 Enterprise.*

Du kan oprette og knytte nye domæner til din kundes leje med PowerShell for at Microsoft 365 hurtigere end at bruge Microsoft 365 Administration.

Delegerede adgangstilladelsespartnere (DAP) er Syndication- og Skyløsningsudbydere (CSP-partnere). De er ofte netværks- eller telekommunikationsudbydere til andre virksomheder. They bundle Microsoft 365 subscriptions into their service offerings to their customers. Når de sælger et Microsoft 365-abonnement, tildeles de automatisk Administrer på vegne af (AOBO)-tilladelser til kundens tilladelser, så de kan administrere og rapportere om kundens tilladelser.
## <a name="what-do-you-need-to-know-before-you-begin"></a>Hvad har du brug for at vide, før du begynder?

Fremgangsmåderne i dette emne kræver, at du opretter forbindelse [Forbind til Microsoft 365 med PowerShell](connect-to-microsoft-365-powershell.md).

Du skal også have legitimationsoplysninger som partnerlejeradministrator.

Du skal også bruge følgende oplysninger:

- Du skal bruge det fulde domænenavn, som din kunde ønsker.

- Du skal bruge kundens **TenantId**.

- FQDN'et skal være registreret hos en DNS-registrator (Internet Domain name service), f.eks. GoDaddy. Du kan finde flere oplysninger om, hvordan du offentligt kan registrere et domænenavn, [under Sådan køber du et domænenavn](../admin/get-help-with-domains/buy-a-domain-name.md).

- Du skal vide, hvordan du føjer en TXT-post til den registrerede DNS-zone for din DNS-registrator. Du kan finde flere oplysninger om, hvordan du tilføjer en TXT-post, [under Tilføj DNS-poster for at forbinde dit domæne](../admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md). Hvis disse procedurer ikke fungerer for dig, skal du finde fremgangsmåderne for din DNS-registrator.

## <a name="create-domains"></a>Opret domæner

 Dine kunder vil sandsynligvis bede dig om at oprette flere domæner, der skal knyttes \<domain>til deres leje, fordi de ikke ønsker, at standarddomænet .onmicrosoft.com skal være det primære domæne, der repræsenterer deres firmaidentiteter over for verden. Denne fremgangsmåde viser dig, hvordan du opretter et nyt domæne, der er knyttet til kundens leje.

> [!NOTE]
> For at udføre nogle af disse handlinger skal den partneradministratorkonto, du logger på med, være indstillet til Fuld **administration** for indstillingen Tildel administrativ adgang til firmaer, du yder **support** til, som findes i detaljerne for administratorkontoen <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">i Microsoft 365 Administration</a>. Du kan finde flere oplysninger om administration af [partneradministratorroller i Partnere: Tilbyde delegeret administration](https://go.microsoft.com/fwlink/p/?LinkId=532435).

### <a name="create-the-domain-in-azure-active-directory"></a>Opret domænet i Azure Active Directory

Denne kommando opretter domænet Azure Active Directory domænet, men knytter det ikke til det offentligt registrerede domæne. Det kommer, når du bekræfter, at du ejer det offentligt registrerede domæne til Microsoft Microsoft 365 til virksomheder.

```powershell
New-MsolDomain -TenantId <customer TenantId> -Name <FQDN of new domain>
```

> [!NOTE]
> PowerShell Core understøtter ikke Microsoft Azure Active Directory til Windows PowerShell og cmdlet'er med **Msol** i deres navn. Hvis du vil fortsætte med at bruge disse cmdlet'er, skal du køre dem fra Windows PowerShell.

### <a name="get-the-data-for-the-dns-txt-verification-record"></a>Hent dataene til DNS TXT-bekræftelsesposten

 Microsoft 365 genererer de specifikke data, som du skal placere i DNS TXT-bekræftelsesposten. Kør denne kommando for at hente dataene.

```powershell
Get-MsolDomainVerificationDNS -TenantId <customer TenantId> -DomainName <FQDN of new domain> -Mode DnsTxtRecord
```

Dette giver dig output som:

 `Label: domainname.com`

 `Text: MS=ms########`

 `Ttl: 3600`

> [!NOTE]
> Du skal bruge denne tekst for at oprette TXT-posten i den offentligt registrerede DNS-zone. Sørg for at kopiere og gemme den.

### <a name="add-a-txt-record-to-the-publically-registered-dns-zone"></a>Føj en TXT-post til den offentligt registrerede DNS-zone

Før Microsoft 365 accepterer trafik, der dirigeres til det offentligt registrerede domænenavn, skal du bevise, at du ejer og har administratortilladelser til domænet. Du bekræfter, at du ejer domænet, ved at oprette en TXT-post i domænet. En TXT-post gør ikke noget i dit domæne, og den kan slettes, når dit ejerskab af domænet er etableret. Hvis du vil oprette TXT-posterne, skal du følge fremgangsmåden under [Tilføj DNS-poster for at forbinde dit domæne](../admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md). Hvis disse procedurer ikke fungerer for dig, skal du finde fremgangsmåderne for din DNS-registrator.

Bekræft den vellykkede oprettelse af TXT-posten via nslookup. Følg denne syntaks.

```console
nslookup -type=TXT <FQDN of registered domain>
```

Dette giver dig output som:

 `Non-authoritative answer:`

 `FQDN of the registered domain`

 `text=MS=ms########`

### <a name="validate-domain-ownership-in-microsoft-365"></a>Valider ejerskab af domæne i Microsoft 365

I dette sidste trin validerer du, om Microsoft 365 ejer det offentligt registrerede domæne. Når dette trin er Microsoft 365 du begynde at acceptere trafik, der dirigeres til det nye domænenavn. Kør denne kommando for at fuldføre domæneoprettelses- og registreringsprocessen.

```powershell
Confirm-MsolDomain -TenantId <customer TenantId> -DomainName <FQDN of new domain>
```

Denne kommando returnerer ikke noget output, så du kan bekræfte, at det lykkedes, ved at køre denne kommando.

```powershell
Get-MsolDomain -TenantId <customer TenantId> -DomainName <FQDN of new domain>
```

Dette returnerer noget i denne

```console
Name                   Status      Authentication
--------------------   ---------   --------------
FQDN of new domain     Verified    Managed
```

## <a name="see-also"></a>Se også

[Hjælp til partnere](https://go.microsoft.com/fwlink/p/?LinkID=533477)
