---
title: Føj et domæne til en klientleje med Windows PowerShell til DAP-partnere
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
ms.openlocfilehash: c4dcdb34f9065009ccaa77d23222601506b537b5
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65099032"
---
# <a name="add-a-domain-to-a-client-tenancy-with-windows-powershell-for-delegated-access-permission-dap-partners"></a>Føj et domæne til en klientleje med Windows PowerShell for DAP-partnere (Delegated Access Permission)

*Denne artikel gælder både for Microsoft 365 Enterprise og Office 365 Enterprise.*

Du kan oprette og knytte nye domæner til din kundes lejer i PowerShell, så Microsoft 365 hurtigere end at bruge Microsoft 365 Administration.

DAP-partnere (Delegated Access Permission) er syndikerings- og CSP-partnere (Cloud Solution Providers). De er ofte netværks- eller telekommunikationsudbydere til andre virksomheder. De bundter Microsoft 365 abonnementer i deres servicetilbud til deres kunder. Når de sælger et Microsoft 365 abonnement, tildeles de automatisk tilladelserne Administrer på vegne af (AOBO) til kundens lejere, så de kan administrere og rapportere om kundens lejere.
## <a name="what-do-you-need-to-know-before-you-begin"></a>Hvad har du brug for at vide, før du begynder?

Procedurerne i dette emne kræver, at du opretter forbindelse til [Forbind for at Microsoft 365 med PowerShell](connect-to-microsoft-365-powershell.md).

Du skal også bruge legitimationsoplysningerne for din partnerlejeradministrator.

Du skal også bruge følgende oplysninger:

- Du skal bruge det fuldt kvalificerede domænenavn (FQDN), som din kunde ønsker.

- Du skal bruge kundens **TenantId**.

- FQDN skal være registreret hos en DNS-registrator (Internet domain name service), f.eks. GoDaddy. Du kan få flere oplysninger om, hvordan du registrerer et domænenavn offentligt, under [Sådan køber du et domænenavn](../admin/get-help-with-domains/buy-a-domain-name.md).

- Du skal vide, hvordan du føjer en TXT-post til den registrerede DNS-zone for din DNS-registrator. Du kan få flere oplysninger om, hvordan du tilføjer en [TXT-post, under Tilføj DNS-poster for at oprette forbindelse til dit domæne](../admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md). Hvis disse procedurer ikke fungerer for dig, skal du finde procedurerne for din DNS-registrator.

## <a name="create-domains"></a>Opret domæner

 Dine kunder vil sandsynligvis bede dig om at oprette yderligere domæner, der skal knyttes til deres lejer, fordi de ikke ønsker, at standarddomænet \<domain>.onmicrosoft.com skal være det primære domæne, der repræsenterer deres virksomhedsidentiteter i verden. Denne procedure fører dig gennem oprettelse af et nyt domæne, der er knyttet til din kundes lejemål.

> [!NOTE]
> Hvis du vil udføre nogle af disse handlinger, skal den partneradministratorkonto, du logger på med, være angivet til **Fuld administration** for indstillingen **Tildel administrativ adgang til de firmaer, du understøtter**, som findes i oplysningerne om administratorkontoen i <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 Administration</a>. Du kan få flere oplysninger om administration af partneradministratorroller under [Partnere: Tilbyd delegeret administration](https://go.microsoft.com/fwlink/p/?LinkId=532435).

### <a name="create-the-domain-in-azure-active-directory"></a>Opret domænet i Azure Active Directory

Denne kommando opretter domænet i Azure Active Directory, men knytter det ikke til det offentligt registrerede domæne. Det kommer, når du beviser, at du ejer det offentligt registrerede domæne til Microsoft Microsoft 365 for virksomheder.

```powershell
New-MsolDomain -TenantId <customer TenantId> -Name <FQDN of new domain>
```

> [!NOTE]
> PowerShell Core understøtter ikke Microsoft Azure Active Directory modulet til Windows PowerShell moduler og cmdlet'er med **Msol** i deres navn. Hvis du vil fortsætte med at bruge disse cmdlet'er, skal du køre dem fra Windows PowerShell.

### <a name="get-the-data-for-the-dns-txt-verification-record"></a>Hent dataene til bekræftelsesposten for DNS TXT

 Microsoft 365 genererer de specifikke data, du skal placere i DNS TXT-bekræftelsesposten. Kør denne kommando for at hente dataene.

```powershell
Get-MsolDomainVerificationDNS -TenantId <customer TenantId> -DomainName <FQDN of new domain> -Mode DnsTxtRecord
```

Dette giver dig output som:

 `Label: domainname.com`

 `Text: MS=ms########`

 `Ttl: 3600`

> [!NOTE]
> Du skal bruge denne tekst til at oprette TXT-posten i den offentligt registrerede DNS-zone. Sørg for at kopiere og gemme den.

### <a name="add-a-txt-record-to-the-publically-registered-dns-zone"></a>Føj en TXT-post til den offentligt registrerede DNS-zone

Før Microsoft 365 begynder at acceptere trafik, der er rettet mod det offentligt registrerede domænenavn, skal du bevise, at du ejer og har administratortilladelser til domænet. Du kan bevise, at du ejer domænet ved at oprette en TXT-post i domænet. En TXT-post gør ikke noget i dit domæne, og den kan slettes, når dit ejerskab af domænet er etableret. Hvis du vil oprette TXT-posterne, skal du følge procedurerne på [Tilføj DNS-poster for at oprette forbindelse til dit domæne](../admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md). Hvis disse procedurer ikke fungerer for dig , skal du finde procedurerne for din DNS-registrator.

Bekræft, at TXT-posten blev oprettet via nslookup. Følg denne syntaks.

```console
nslookup -type=TXT <FQDN of registered domain>
```

Dette giver dig output som:

 `Non-authoritative answer:`

 `FQDN of the registered domain`

 `text=MS=ms########`

### <a name="validate-domain-ownership-in-microsoft-365"></a>Valider ejerskabet af domænet i Microsoft 365

I dette sidste trin validerer du, at Microsoft 365, at du ejer det offentligt registrerede domæne. Efter dette trin begynder Microsoft 365 at acceptere trafik, der dirigeres til det nye domænenavn. Kør denne kommando for at fuldføre domæneoprettelses- og registreringsprocessen.

```powershell
Confirm-MsolDomain -TenantId <customer TenantId> -DomainName <FQDN of new domain>
```

Denne kommando returnerer ikke noget output, så kør denne kommando for at bekræfte, at det virkede.

```powershell
Get-MsolDomain -TenantId <customer TenantId> -DomainName <FQDN of new domain>
```

Dette returnerer noget i stil med dette

```console
Name                   Status      Authentication
--------------------   ---------   --------------
FQDN of new domain     Verified    Managed
```

## <a name="see-also"></a>Se også

[Hjælp til partnere](https://go.microsoft.com/fwlink/p/?LinkID=533477)
