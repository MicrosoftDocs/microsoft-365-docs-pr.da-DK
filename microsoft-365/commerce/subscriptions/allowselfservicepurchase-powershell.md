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
description: Få mere at vide om, hvordan du bruger AllowSelfServicePurchase PowerShell-cmdlet'en til at slå selvbetjeningskøb til eller fra.
ROBOTS: NOINDEX, NOFOLLOW
ms.date: 12/15/2021
ms.openlocfilehash: a3800f82386fafe509d9bdabb25cd91422cf058d
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63587953"
---
# <a name="use-allowselfservicepurchase-for-the-mscommerce-powershell-module"></a>Brug AllowSelfServicePurchase til MSCommerce PowerShell-modulet

**Modulet MSCommerce** PowerShell er nu tilgængeligt i [PowerShell-galleriet](https://aka.ms/allowselfservicepurchase-powershell-gallery). Modulet indeholder en **PolicyID-parameterværdi** for **AllowSelfServicePurchase** , der giver dig mulighed for at kontrollere, om brugerne i organisationen kan foretage selvbetjeningskøb.

Du kan bruge **MSCommerce** PowerShell-modulet til at:

- Få vist standardtilstanden for **parameterværdien AllowSelfServicePurchase** – uanset om den er aktiveret eller deaktiveret
- Få vist en liste over relevante produkter, og om selvbetjeningskøb er aktiveret eller deaktiveret
- Få vist eller rediger den aktuelle indstilling for et bestemt produkt for enten at aktivere eller deaktivere det

## <a name="requirements"></a>Krav

Hvis du vil bruge **modulet MSCommerce** PowerShell, skal du bruge:

- En Windows 10 enhed
- PowerShell 5 eller nedenfor. PowerShell 6.x/7.x understøttes i øjeblikket ikke med dette modul.
- Administratortilladelse for enheden
- Rollen global administrator eller faktureringsadministrator for din lejer

## <a name="install-the-mscommerce-powershell-module"></a>Installér modulet MSCommerce PowerShell

Du skal installere **MSCommerce** PowerShell-modulet på din Windows 10 én gang og derefter importere det til hver PowerShell-session, du starter. Download **MSCommerce** PowerShell-modulet fra [PowerShell-galleriet](https://aka.ms/allowselfservicepurchase-powershell-gallery).

For at installere **MSCommerce** PowerShell-modulet med **PowerShellGet** skal du køre følgende kommando:

```powershell
Install-Module -Name MSCommerce
```

## <a name="import-mscommerce-into-the-powershell-session"></a>Importér MSCommerce til PowerShell-sessionen

Når du har installeret modulet på din Windows 10, skal du derefter importere det til hver PowerShell-session, du starter. Hvis du vil importere den til en PowerShell-session, skal du køre følgende kommando:

```powershell
Import-Module -Name MSCommerce
```

## <a name="connect-to-mscommerce-with-your-credentials"></a>Forbind til MSCommerce med dine legitimationsoplysninger

Kør følgende kommando for at oprette forbindelse til PowerShell-modulet med dine legitimationsoplysninger.

```powershell
Connect-MSCommerce
```

Denne kommando forbinder den aktuelle PowerShell-session til en Azure Active Directory lejer. Kommandoen beder dig om et brugernavn og en adgangskode til den lejer, du vil oprette forbindelse til. Hvis multifaktorgodkendelse er aktiveret for dine legitimationsoplysninger, bruger du den interaktive mulighed for at logge på.

## <a name="view-details-for-allowselfservicepurchase"></a>Vis detaljer for AllowSelfServicePurchase

Kør følgende kommando for at få vist en beskrivelse af parameterværdien **AllowSelfServicePurchase** og standardstatus baseret på organisationen:

```powershell
Get-MSCommercePolicy -PolicyId AllowSelfServicePurchase
```

## <a name="view-a-list-of-self-service-purchase-products-and-their-status"></a>Få vist en liste over selvbetjeningskøbsprodukter og deres status

Hvis du vil have vist en liste over alle tilgængelige produkter til selvbetjeningskøb og status for hver enkelt, skal du køre følgende kommando:

```powershell
Get-MSCommerceProductPolicies -PolicyId AllowSelfServicePurchase
```

I følgende tabel vises de tilgængelige produkter og deres **Produkt-id**.

| Produkt | ProductId |
|-----------------------------|--------------|
| Power Apps pr. bruger | CFQ7TTC0KP0P |
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
| Windows 365 Business med Windows hybridfordel | CFQ7TTC0HX99 |

*Disse iD'er er blevet ændret. Hvis du tidligere har blokeret produkter ved hjælp af de gamle ID'er, blokeres de automatisk ved hjælp af de nye ID'er. Der kræves ikke yderligere arbejde.

## <a name="view-or-set-the-status-for-allowselfservicepurchase"></a>Få vist eller angive status for AllowSelfServicePurchase

Når du har vist listen over produkter, der kan købes via selvbetjening, kan du få vist eller ændre indstillingen for et bestemt produkt.

Kør følgende kommando for at få politikindstillingen for et bestemt produkt:

```powershell
Get-MSCommerceProductPolicy -PolicyId AllowSelfServicePurchase -ProductId CFQ7TTC0KP0N
```

Kør følgende kommando for at aktivere politikindstillingen for et bestemt produkt:

```powershell
Update-MSCommerceProductPolicy -PolicyId AllowSelfServicePurchase -ProductId CFQ7TTC0KP0N -Enabled $True
```

Kør følgende kommando for at deaktivere politikindstillingen for et bestemt produkt:

```powershell
Update-MSCommerceProductPolicy -PolicyId AllowSelfServicePurchase -ProductId CFQ7TTC0KP0N -Enabled $False
```

## <a name="example-script-to-disable-allowselfservicepurchase"></a>Eksempelscript til deaktivering af AllowSelfServicePurchase

I følgende eksempel kan du se, hvordan du importerer **modulet MSCommerce**, logger på med din konto, henter **ProductId'et** til Power Automate og derefter **deaktiverer AllowSelfServicePurchase** for det pågældende produkt.

```powershell
Import-Module -Name MSCommerce
Connect-MSCommerce #sign-in with your global or billing administrator account when prompted
$product = Get-MSCommerceProductPolicies -PolicyId AllowSelfServicePurchase | where {$_.ProductName -match 'Power Automate'}
Update-MSCommerceProductPolicy -PolicyId AllowSelfServicePurchase -ProductId $product.ProductID -Enabled $false
```

Hvis der er flere værdier for produktet, kan du køre kommandoen enkeltvis for hver værdi, som vist i følgende eksempel:

```powershell
Update-MSCommerceProductPolicy -PolicyId AllowSelfServicePurchase -ProductId $product[0].ProductID -Enabled $false
Update-MSCommerceProductPolicy -PolicyId AllowSelfServicePurchase -ProductId $product[1].ProductID -Enabled $false
```


## <a name="troubleshooting"></a>Fejlfinding

### <a name="problem"></a>Problem

Du får vist følgende fejlmeddelelse:

> HåndtagFejl: Politikken kunne ikke hentes med PolicyId 'AllowSelfServicePurchase', ErrorMessage – Den underliggende forbindelse blev lukket: Der opstod en uventet fejl ved en afsendelse.

Dette kan skyldes en ældre version af TLS (Transport Layer Security). For at oprette forbindelse til denne tjeneste skal du bruge TLS 1.2 eller derover

### <a name="solution"></a>Løsning

Opgrader til TLS 1.2. Følgende syntaks opdaterer Sikkerhedsprotokol ServicePointManager til TLS1.2:

```powershell
 [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.SecurityProtocolType]::Tls12
```

Du kan få mere at vide [under Sådan aktiveres TLS 1.2](/mem/configmgr/core/plan-design/security/enable-tls-1-2).

<!--
## Uninstall the MSCommerce module

Before you uninstall the MSCommerce module, close your current PowerShell session, then open a new session with admin rights.

To remove the **MSCommerce** PowerShell module from your computer, run the following command:

```powershell
Uninstall-Module -Name MSCommerce
```-->

## <a name="related-content"></a>Relateret indhold

[Administrer selvbetjeningskøb (administrator)](manage-self-service-purchases-admins.md) (artikel)

[Ofte stillede spørgsmål om selvbetjeningskøb](self-service-purchase-faq.yml) (artikel)
