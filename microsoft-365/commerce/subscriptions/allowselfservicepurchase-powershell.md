---
title: Brug AllowSelfServicePurchase til MSCommerce PowerShell-modulet
f1.keywords:
- NOCSH
author: cmcatee-MSFT
ms.author: cmcatee
manager: scotv
ms.reviewer: mijeffer, pablom
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: ''
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- commerce_ssp
- AdminSurgePortfolio
search.appverid:
- MET150
description: Få mere at vide om, hvordan du bruger PowerShell-cmdlet'en AllowSelfServicePurchase til at slå køb via selvbetjening til eller fra.
ROBOTS: NOINDEX, NOFOLLOW
ms.date: 4/7/2022
ms.openlocfilehash: d9be7179ed26a35b2e04af8386f161de935b1ae1
ms.sourcegitcommit: 9fdb5c5b9eaf0c8a8d62b579a5fb5a5dc2d29fa9
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/11/2022
ms.locfileid: "66714700"
---
# <a name="use-allowselfservicepurchase-for-the-mscommerce-powershell-module"></a>Brug AllowSelfServicePurchase til MSCommerce PowerShell-modulet

**MSCommerce PowerShell-modulet** er nu tilgængeligt i [PowerShell-galleriet](https://aka.ms/allowselfservicepurchase-powershell-gallery). Modulet indeholder en **PolicyID-parameterværdi** for **AllowSelfServicePurchase** , der giver dig mulighed for at styre, om brugere i din organisation kan foretage køb via selvbetjening.

Du kan bruge **MSCommerce PowerShell-modulet** til at:

- Få vist standardtilstanden for parameterværdien **AllowSelfServicePurchase** – uanset om den er aktiveret eller deaktiveret
- Få vist en liste over relevante produkter, og om køb via selvbetjening er aktiveret eller deaktiveret
- Få vist eller rediger den aktuelle indstilling for et bestemt produkt for enten at aktivere eller deaktivere det

## <a name="requirements"></a>Krav

Hvis du vil bruge **MSCommerce PowerShell-modulet** , skal du bruge:

- En Windows 10 enhed
- PowerShell 5 eller nyere. PowerShell 6.x/7.x understøttes i øjeblikket ikke i dette modul.
- Administratortilladelse til enheden
- Global eller fakturerings-Administration rolle for din lejer

## <a name="install-the-mscommerce-powershell-module"></a>Installér MSCommerce PowerShell-modulet

Du installerer **MSCommerce** PowerShell-modulet én gang på din Windows 10 enhed og importerer det derefter til hver PowerShell-session, du starter. Download **MSCommerce** PowerShell-modulet fra [PowerShell-galleriet](https://aka.ms/allowselfservicepurchase-powershell-gallery).

Hvis du vil installere **MSCommerce PowerShell-modulet** med **PowerShellHent**, skal du køre følgende kommando:

```powershell
Install-Module -Name MSCommerce
```

## <a name="import-mscommerce-into-the-powershell-session"></a>Importér MSCommerce til PowerShell-sessionen

Når du har installeret modulet på din Windows 10 enhed, importerer du det derefter til hver PowerShell-session, du starter. Kør følgende kommando for at importere den i en PowerShell-session:

```powershell
Import-Module -Name MSCommerce
```

## <a name="connect-to-mscommerce-with-your-credentials"></a>Opret forbindelse til MSCommerce med dine legitimationsoplysninger

Hvis du vil oprette forbindelse til PowerShell-modulet med dine legitimationsoplysninger, skal du køre følgende kommando.

```powershell
Connect-MSCommerce
```

Denne kommando forbinder den aktuelle PowerShell-session med en Azure Active Directory-lejer. Kommandoen beder dig om et brugernavn og en adgangskode for den lejer, du vil oprette forbindelse til. Hvis multifaktorgodkendelse er aktiveret for dine legitimationsoplysninger, kan du bruge den interaktive indstilling til at logge på.

## <a name="view-details-for-allowselfservicepurchase"></a>Få vist oplysninger om AllowSelfServicePurchase

Kør følgende kommando for at få vist en beskrivelse af parameterværdien **AllowSelfServicePurchase** og standardstatussen baseret på din organisation:

```powershell
Get-MSCommercePolicy -PolicyId AllowSelfServicePurchase
```

## <a name="view-a-list-of-self-service-purchase-products-and-their-status"></a>Få vist en liste over produkter til køb via selvbetjening og deres status

Kør følgende kommando for at få vist en liste over alle tilgængelige produkter til køb via selvbetjening og status for hver enkelt:

```powershell
Get-MSCommerceProductPolicies -PolicyId AllowSelfServicePurchase
```

I følgende tabel vises de tilgængelige produkter og deres **ProductId**.

| Produkt | Instruktion |
|-----------------------------|--------------|
| Power Apps pr. bruger* | CFQ7TTC0LH2H |
| Power Automate pr. bruger | CFQ7TTC0KP0N |
| Power Automate RPA | CFQ7TTC0KXG6  |
| Power BI Premium (separat) | CFQ7TTC0KXG7  |
| Power BI Pro | CFQ7TTC0L3PB |
| Project Plan 1* | CFQ7TTC0HDB1 |
| Project Plan 3* | CFQ7TTC0HDB0 |
| Visio Plan 1* | CFQ7TTC0HD33 |
| Visio Plan 2* | CFQ7TTC0HD32 |
| Windows 365 Enterprise | CFQ7TTC0HHS9 |
| Windows 365 Business | CFQ7TTC0J203 |
| Windows 365 Business med Windows Hybrid-fordel | CFQ7TTC0HX99 |
| Microsoft 365 F3 | CFQ7TTC0LH05 |
| Dynamics 365 Marketing | CFQ7TTC0LH3N |
| Dynamics 365 Marketing Attach | CFQ7TTC0LHWP | 
| Yderligere program til Dynamics 365 Marketing | CFQ7TTC0LHVK |
| Dynamics 365 Marketing – ekstra ikke-prod.program | CFQ7TTC0LHWM |

*Disse id'er er blevet ændret. Hvis du tidligere har blokeret produkter ved hjælp af de gamle id'er, blokeres de automatisk ved hjælp af de nye id'er. Der kræves ikke yderligere arbejde.

## <a name="view-or-set-the-status-for-allowselfservicepurchase"></a>Få vist eller angiv status for AllowSelfServicePurchase

Når du har vist listen over produkter, der kan købes via selvbetjening, kan du få vist eller ændre indstillingen for et bestemt produkt.

Kør følgende kommando for at hente politikindstillingen for et bestemt produkt:

```powershell
Get-MSCommerceProductPolicy -PolicyId AllowSelfServicePurchase -ProductId CFQ7TTC0KP0N
```

Kør følgende kommando for at aktivere politikindstillingen for et bestemt produkt:

```powershell
Update-MSCommerceProductPolicy -PolicyId AllowSelfServicePurchase -ProductId CFQ7TTC0KP0N -Enabled $True
```

Hvis du vil deaktivere politikindstillingen for et bestemt produkt, skal du køre følgende kommando:

```powershell
Update-MSCommerceProductPolicy -PolicyId AllowSelfServicePurchase -ProductId CFQ7TTC0KP0N -Enabled $False
```

## <a name="example-script-to-disable-allowselfservicepurchase"></a>Eksempelscript til deaktivering af AllowSelfServicePurchase

I følgende eksempel gennemgår vi, hvordan du importerer **MSCommerce-modulet** , logger på med din konto, henter **ProductId** for Power Automate pr. bruger og derefter deaktiverer **AllowSelfServicePurchase** for det pågældende produkt.

```powershell
Import-Module -Name MSCommerce
Connect-MSCommerce #sign-in with your global or billing administrator account when prompted
$product = Get-MSCommerceProductPolicies -PolicyId AllowSelfServicePurchase | where {$_.ProductName -match 'Power Automate per user'}
Update-MSCommerceProductPolicy -PolicyId AllowSelfServicePurchase -ProductId $product.ProductID -Enabled $false
```

Hvis der er flere værdier for produktet, kan du køre kommandoen enkeltvist for hver værdi som vist i følgende eksempel:

```powershell
Update-MSCommerceProductPolicy -PolicyId AllowSelfServicePurchase -ProductId $product[0].ProductID -Enabled $false
Update-MSCommerceProductPolicy -PolicyId AllowSelfServicePurchase -ProductId $product[1].ProductID -Enabled $false
```


## <a name="troubleshooting"></a>Fejlfinding

### <a name="problem"></a>Problem

Du får vist følgende fejlmeddelelse:

> HandleError: Politikken med PolicyId 'AllowSelfServicePurchase', ErrorMessage – Den underliggende forbindelse blev lukket: Der opstod en uventet fejl under en afsendelse.

Dette kan skyldes en ældre version af Transport Layer Security (TLS). Hvis du vil oprette forbindelse til denne tjeneste, skal du bruge TLS 1.2 eller nyere

### <a name="solution"></a>Løsning

Opgrader til TLS 1.2. Følgende syntaks opdaterer ServicePointManager-sikkerhedsprotokollen til TLS1.2:

```powershell
 [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.SecurityProtocolType]::Tls12
```

Du kan få mere at vide under [Sådan aktiverer du TLS 1.2](/mem/configmgr/core/plan-design/security/enable-tls-1-2).

<!--
## Uninstall the MSCommerce module

Before you uninstall the MSCommerce module, close your current PowerShell session, then open a new session with admin rights.

To remove the **MSCommerce** PowerShell module from your computer, run the following command:

```powershell
Uninstall-Module -Name MSCommerce
```-->

## <a name="related-content"></a>Relateret indhold

[Administrer køb via selvbetjening (Administration)](manage-self-service-purchases-admins.md) (artikel)

[Ofte stillede spørgsmål om køb via selvbetjening](self-service-purchase-faq.yml) (artikel)
