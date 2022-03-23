---
title: Konfigurere IRM til at bruge en lokal AD RMS-server
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 12/13/2017
audience: End User
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: 3ecde857-4b7c-451d-b4aa-9eeffc8a8c61
ms.collection:
- M365-security-compliance
description: Få mere at vide om, hvordan du konfigurerer IRM (Information Rights Management) Exchange Online at bruge en AD RMS-server (Active Directory Rights Management Service).
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: f87992fc9be676b9485d6ec7a7b7ff1f3a4d39d9
ms.sourcegitcommit: 99067d5eb1fa7b094e7cdb1f7be65acaaa235a54
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/29/2022
ms.locfileid: "63588915"
---
# <a name="configure-irm-to-use-an-on-premises-ad-rms-server"></a>Konfigurere IRM til at bruge en lokal AD RMS-server

Til brug med lokale installationer bruger IRM (Information Rights Management) i Exchange Online Active Directory Rights Management-tjenester (AD RMS), en teknologi til informationsbeskyttelse i Windows Server 2008 og nyere. IRM-beskyttelse anvendes på mail ved at anvende en AD RMS-rettighedspolitikskabelon på en mail. Rettigheder knyttes til selve meddelelsen, så beskyttelsen sker online og offline og inden for og uden for organisationens firewall.

I dette emne kan du se, hvordan du konfigurerer IRM til at bruge en AD RMS-server. Du kan finde oplysninger om brug af de nye Office 365-meddelelseskryptering med Azure Active Directory og Azure Rights Management i de [ofte Office 365-meddelelseskryptering ofte stillede spørgsmål](./ome-faq.yml).

Du kan få mere at vide om IRM Exchange Online i [IRM (Information Rights Management) Exchange Online](information-rights-management-in-exchange-online.md).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Hvad har du brug for at vide, før du begynder?

- Anslået tidspunkt for at fuldføre denne opgave: 30 minutter

- Du skal have tildelt tilladelser, før du kan udføre proceduren eller procedurerne. Hvis du vil se, hvilke tilladelser du skal bruge, skal du se posten "IDE (Information Rights Management) under emnet Meddelelsespolitik [og overholdelsestilladelser](/Exchange/permissions/feature-permissions/policy-and-compliance-permissions) .

- AD RMS-serveren skal køre Windows Server 2008 eller nyere. Hvis du vil have mere at vide om, hvordan du installerer AD RMS, [skal du se Installation af en AD RMS-klynge](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc726041(v=ws.11)).

- Hvis du vil have mere at vide om, hvordan du installerer Windows PowerShell konfigurerer og opretter forbindelse til tjenesten, skal [du Forbind to Exchange Online Using Remote PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

- Du kan finde oplysninger om tastaturgenveje, der kan anvendes på procedurerne i dette emne, [under Tastaturgenveje i Exchange Administration i Exchange Online](/Exchange/accessibility/keyboard-shortcuts-in-admin-center).

> [!TIP]
> Har du problemer? Bed om hjælp i Exchange fora. Besøg [forummerne Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542) eller [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).

## <a name="how-do-you-do-this"></a>Hvordan gør du dette?
<a name="sectionSection1"> </a>

### <a name="step-1-use-the-ad-rms-console-to-export-a-trusted-publishing-domain-tpd-from-an-ad-rms-server"></a>Trin 1: Brug AD RMS-konsollen til at eksportere et pålidelig publiceringsdomæne (TPD) fra en AD RMS-server

Det første trin er at eksportere et pålidelig publiceringsdomæne (TPD) fra den lokale AD RMS-server til en XML-fil. TPD'en indeholder følgende indstillinger, der skal bruges for at bruge RMS-funktioner:

- Serverlicensorcertifikatet (SLC), der bruges til signering og kryptering af certifikater og licenser

- URL-adresserne, der bruges til licensering og publicering

- De AD RMS-rettighedspolitikskabeloner, der er oprettet med den specifikke SLC for den pågældende TPD

Når du importerer TPD'en, gemmes og beskyttes den i Exchange Online.

1. Åbn Active Directory Rights Management-tjenester, og udvid derefter AD RMS-klyngen.

2. I konsoltræet skal du udvide Hav **tillidspolitikker** og derefter klikke på **Publiceringsdomæner, der er tillid til**.

3. I resultatruden skal du vælge certifikatet for det domæne, du vil eksportere.

4. I ruden **Handlinger skal du** klikke på **Eksportér et publiceringsdomæne, der er tillid til**.

5. I feltet **Publiceringsdomænefil** skal du **klikke på Gem** som for at gemme filen på en bestemt placering på den lokale computer. Skriv et filnavn, sørg for at angive filtypenavnet `.xml` , og klik derefter på **Gem**.

6. I felterne **Adgangskode og** **Bekræft adgangskode skal** du skrive en stærk adgangskode, der skal bruges til at kryptere den pålidelige publiceringsdomænefil. Du skal angive denne adgangskode, når du importerer TPD'en til din skybaserede mailorganisation.

### <a name="step-2-use-the-exchange-management-shell-to-import-the-tpd-to-exchange-online"></a>Trin 2: Brug Exchange Management Shell til at importere TPD'et Exchange Online

Når TPD'en er eksporteret til en XML-fil, skal du importere den Exchange Online. Når en TPD importeres, importeres organisationens AD RMS-skabeloner også. Når det første TPD importeres, bliver det standard-TPD for din skybaserede organisation. Hvis du importerer en anden TPD, kan du  bruge standardskiftet til at gøre det til standard-TPD, der er tilgængeligt for brugerne.

For at importere TPD'en skal du køre følgende kommando i Windows PowerShell:

```powershell
Import-RMSTrustedPublishingDomain -FileData ([System.IO.File]::ReadAllBytes('<path to exported TPD file>')) -Name "<name of TPD>" -ExtranetLicensingUrl <URL> -IntranetLicensingUrl <URL>
```

Du kan hente værdierne for parametrene _ExtranetLicensingUrl_ og _IntranetLicensingUrl_ Active Directory Rights Management-tjenester konsollen. Vælg AD RMS-klyngen i konsoltræet. Licenswebadresserne vises i resultatruden. Disse URL-adresser bruges af mailklienter, når indhold skal dekrypteres, og når Exchange Online skal afgøre, hvilken TPD der skal bruges.

Når du kører denne kommando, bliver du bedt om en adgangskode. Angiv den adgangskode, du angav, da du eksporterede TPD'en fra DIN AD RMS-server.

Eksempelvis importerer følgende kommando TPD med navnet Eksporteret TPD ved hjælp af den XML-fil, du eksporterede fra AD RMS-serveren og gemte på computeren af administratorkontoen. Navneparameteren bruges til at angive et navn til TPD'en.

```powershell
Import-RMSTrustedPublishingDomain -FileData ([System.IO.File]::ReadAllBytes('C:\Users\Administrator\Desktop\ExportTPD.xml')) -Name "Exported TPD" -ExtranetLicensingUrl https://corp.contoso.com/_wmcs/licensing -IntranetLicensingUrl https://rmsserver/_wmcs/licensing
```

Du kan finde detaljerede oplysninger om syntaks og [parameter i Import-RMSTrustedPublishingDomain](/powershell/module/exchange/import-rmstrustedpublishingdomain).

#### <a name="how-do-you-know-that-you-successfully-imported-the-tpd"></a>Hvordan ved du, at du har importeret TPD'et?

For at bekræfte at du har importeret TPD'et, skal du køre **Get-RMSTrustedPublishingDomain** cmdlet'en for at hente TPD'er i Exchange Online organisation. Du kan få mere at vide i eksemplerne [i Get-RMSTrustedPublishingDomain](/powershell/module/exchange/get-rmstrustedpublishingdomain).

### <a name="step-3-use-the-exchange-management-shell-to-distribute-an-ad-rms-rights-policy-template"></a>Trin 3: Brug Exchange Management Shell til at distribuere en skabelon til AD RMS-rettighedspolitik

Når du har importeret TPD'et, skal du sørge for, at en AD RMS-rettighedspolitikskabelon distribueres. En distribueret skabelon er synlig for Outlook på internettet (tidligere kaldet Outlook Web App), som derefter kan anvende skabelonerne på en mail.

Kør følgende kommando for at returnere en liste over alle skabeloner, der er indeholdt i standard-TPD:

```powershell
Get-RMSTemplate -Type All | fl
```

Hvis værdien af _parameteren Type_ er `Archived`, er skabelonen ikke synlig for brugerne. Kun distribuerede skabeloner i standard-TPD er tilgængelige i Outlook på internettet.

For at distribuere en skabelon skal du køre følgende kommando:

```powershell
Set-RMSTemplate -Identity "<name of the template>" -Type Distributed
```

Følgende kommando importerer f.eks. skabelonen Firmafortrolige.

```powershell
Set-RMSTemplate -Identity "Company Confidential" -Type Distributed
```

Du kan finde detaljerede oplysninger om syntaks og [parameter i Get-RMSTemplate](/powershell/module/exchange/get-rmstemplate) [og Set-RMSTemplate](/powershell/module/exchange/set-rmstemplate).

#### <a name="the-do-not-forward-template"></a>Skabelonen Videreslær ikke

Når du importerer standard-TPD fra din lokale organisation til Exchange Online, importeres der en AD RMS-rettighedspolitikskabelon med navnet **Videresende** ikke. Denne skabelon distribueres som standard, når du importerer standard-TPD'en. Du kan ikke bruge **cmdlet'en Set-RMSTemplate** til at ændre **skabelonen Videresende** ikke.

Når **skabelonen Videressendelse** ikke anvendes på en meddelelse, er det kun de modtagere, der er adresseret i meddelelsen, der kan læse meddelelsen. Desuden kan modtagerne ikke gøre følgende:

- Videresende meddelelsen til en anden person.
- Kopiér indhold fra meddelelsen.
- Udskriv meddelelsen.

> [!IMPORTANT]
> **Skabelonen Videresend** ikke kan ikke forhindre oplysninger i en meddelelse i at blive kopieret med tredjepartsprogrammer til hentning af skærmbilleder, kameraer eller brugere, der skriver oplysningerne manuelt

Du kan oprette flere AD RMS-rettighedspolitikskabeloner på AD RMS-serveren i din lokale organisation for at opfylde dine IRM-beskyttelseskrav. Hvis du opretter flere AD RMS-rettighedspolitikskabeloner, skal du eksportere TPD'en fra den lokale AD RMS-server igen og opdatere TPD i den skybaserede mailorganisation.

#### <a name="how-do-you-know-that-you-successfully-distributed-the-ad-rms-rights-policy-template"></a>Hvordan ved du, at du har distribueret SKABELONen FOR RMS-rettigheder korrekt?

For at bekræfte, at du har distribueret og AD RMS-rettighedspolitikskabelonen, skal du køre **Get-RMSTemplate** cmdlet'en for at kontrollere skabelonens egenskaber. Du kan få mere at vide i eksemplerne [i Get-RMSTemplate](/powershell/module/exchange/get-rmstemplate).

### <a name="step-4-use-the-exchange-management-shell-to-enable-irm"></a>Trin 4: Brug Exchange Management Shell til at aktivere IRM

Når du har importeret TPD og distribueret en AD RMS-rettighedspolitikskabelon, skal du køre følgende kommando for at aktivere IRM for din skybaserede mailorganisation.

```powershell
Set-IRMConfiguration -InternalLicensingEnabled $true
```

Du kan finde detaljerede oplysninger om syntaks og parameter [i Set-IRMConfiguration](/powershell/module/exchange/set-irmconfiguration).

#### <a name="how-do-you-know-that-you-successfully-enabled-irm"></a>Hvordan ved du, at du har aktiveret IRM?

Du bekræfter, at du har aktiveret IRM, ved at køre [Cmdlet'en Get-IRMConfiguration](/powershell/module/exchange/get-irmconfiguration) for at kontrollere IRM-konfigurationen Exchange Online organisationen.

## <a name="how-do-you-know-this-task-worked"></a>Hvordan ved du, at denne opgave fungerede?
<a name="sectionSection2"> </a>

For at bekræfte, at du har importeret TPD og aktiveret IRM, skal du gøre følgende:

- Brug **Cmdlet'en Test-IRMConfiguration** til at teste IRM-funktionaliteten. Du kan få mere at vide under "Eksempel 1" [i Test-IRMConfiguration](/powershell/module/exchange/test-irmconfiguration).

- Skriv en ny meddelelse i Outlook på internettet og IRM-beskyt den ved at vælge indstillingen Angiv tilladelser  i den udvidede menu (![ikonet Flere indstillinger).](../media/ITPro-EAC-MoreOptionsIcon.gif)
