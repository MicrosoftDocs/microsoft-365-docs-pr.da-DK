---
title: Konfigurer IRM til at bruge en lokal AD RMS-server
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
description: Få mere at vide om, hvordan du konfigurerer IRM (Information Rights Management) i Exchange Online til at bruge en AD RMS-server (Active Directory Rights Management Service).
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 5bd4a104d4cceedbdb82c1ff2baac0b547b74fbe
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66637499"
---
# <a name="configure-irm-to-use-an-on-premises-ad-rms-server"></a>Konfigurer IRM til at bruge en lokal AD RMS-server

Til brug med udrulninger i det lokale miljø bruger IRM (Information Rights Management) i Exchange Online AD RMS (Active Directory Rights Management Services), som er en teknologi til beskyttelse af oplysninger i Windows Server 2008 og nyere. IRM-beskyttelse anvendes på mail ved at anvende en SKABELON for AD RMS-rettigheder på en mail. Rettigheder vedhæftes selve meddelelsen, så beskyttelsen sker online og offline og i og uden for organisationens firewall.

I dette emne kan du se, hvordan du konfigurerer IRM til at bruge en AD RMS-server. Du kan få oplysninger om brug af Microsoft Purview-meddelelseskryptering med Azure Active Directory og Azure Rights Management i [Ofte stillede spørgsmål om meddelelseskryptering](./ome-faq.yml).

Du kan få mere at vide om IRM i Exchange Online [under Information Rights Management i Exchange Online](information-rights-management-in-exchange-online.md).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Hvad har du brug for at vide, før du begynder?

- Anslået tid til at fuldføre denne opgave: 30 minutter

- Du skal have tildelt tilladelser, før du kan udføre denne procedure eller disse procedurer. Hvis du vil se, hvilke tilladelser du har brug for, skal du se emnet "Information Rights Management" under emnet [Meddelelsespolitik og tilladelser til overholdelse af angivne standarder](/Exchange/permissions/feature-permissions/policy-and-compliance-permissions) .

- AD RMS-serveren skal køre Windows Server 2008 eller nyere. Du kan finde oplysninger om, hvordan du installerer AD RMS, under [Installation af en AD RMS-klynge](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc726041(v=ws.11)).

- Du kan finde oplysninger om, hvordan du installerer og konfigurerer Windows PowerShell og opretter forbindelse til tjenesten, under [Opret forbindelse til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

- Du kan finde oplysninger om tastaturgenveje, der kan gælde for procedurerne i dette emne, under [Tastaturgenveje til Exchange Administration i Exchange Online](/Exchange/accessibility/keyboard-shortcuts-in-admin-center).

> [!TIP]
> Har du problemer? Bed om hjælp i Exchange-forummerne. Besøg forummerne på [Exchange Server,Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=60612) eller[](https://go.microsoft.com/fwlink/p/?linkId=267542) [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).

## <a name="how-do-you-do-this"></a>Hvordan gør du det?
<a name="sectionSection1"> </a>

### <a name="step-1-use-the-ad-rms-console-to-export-a-trusted-publishing-domain-tpd-from-an-ad-rms-server"></a>Trin 1: Brug AD RMS-konsollen til at eksportere et TPD (publiceringsdomæne), der er tillid til, fra en AD RMS-server

Det første trin er at eksportere et TPD (Publishing Domain), der er tillid til, fra AD RMS-serveren i det lokale miljø til en XML-fil. TPD indeholder følgende indstillinger, der er nødvendige for at bruge RMS-funktioner:

- Det SLC-certifikat (Server Licensor Certificate), der bruges til signering og kryptering af certifikater og licenser

- De URL-adresser, der bruges til licensering og publicering

- AD RMS-rettighedspolitikskabeloner, der blev oprettet med den specifikke SLC for den pågældende TPD

Når du importerer TPD, gemmes og beskyttes den i Exchange Online.

1. Åbn Active Directory Rights Management Services-konsollen, og udvid derefter AD RMS-klyngen.

2. Udvid **Tillidspolitikker** i konsoltræet, og klik derefter på **Publiceringsdomæner, der er tillid til**.

3. Vælg certifikatet for det domæne, du vil eksportere, i resultatruden.

4. Klik på **Eksportér udgivelsesdomæne, der er tillid til**, i ruden **Handlinger**.

5. Klik på **Gem som** i feltet **Publicer domænefil** for at gemme filen på en bestemt placering på den lokale computer. Skriv et filnavn, og sørg for at angive filtypenavnet `.xml` , og klik derefter på **Gem**.

6. I felterne **Adgangskode** og **Bekræft adgangskode** skal du skrive en stærk adgangskode, der skal bruges til at kryptere den publiceringsdomænefil, der er tillid til. Du skal angive denne adgangskode, når du importerer TPD til din skybaserede mailorganisation.

### <a name="step-2-use-the-exchange-management-shell-to-import-the-tpd-to-exchange-online"></a>Trin 2: Brug Exchange Management Shell til at importere TPD til Exchange Online

Når TPD er eksporteret til en XML-fil, skal du importere den for at Exchange Online. Når en TPD importeres, importeres din organisations AD RMS-skabeloner også. Når den første TPD importeres, bliver den standard-TPD for din cloudbaserede organisation. Hvis du importerer en anden TPD, kan du bruge parameteren **Default** til at gøre den til standard-TPD, der er tilgængelig for brugerne.

Hvis du vil importere TPD, skal du køre følgende kommando i Exchange Online PowerShell:

```powershell
Import-RMSTrustedPublishingDomain -FileData ([System.IO.File]::ReadAllBytes('<path to exported TPD file>')) -Name "<name of TPD>" -ExtranetLicensingUrl <URL> -IntranetLicensingUrl <URL>
```

Du kan hente værdierne for parametrene _ExtranetLicensingUrl_ og _IntranetLicensingUrl_ i Active Directory Rights Management Services-konsollen. Vælg AD RMS-klyngen i konsoltræet. URL-adresserne til licenser vises i resultatruden. Disse URL-adresser bruges af mailklienter, når indhold skal dekrypteres, og når Exchange Online skal afgøre, hvilken TPD der skal bruges.

Når du kører denne kommando, bliver du bedt om at angive en adgangskode. Angiv den adgangskode, du angav, da du eksporterede TPD fra AD RMS-serveren.

Følgende kommando importerer f.eks. TPD med navnet Eksporteret TPD ved hjælp af den XML-fil, du eksporterede fra AD RMS-serveren og gemte på skrivebordet for administratorkontoen. Parameteren Name bruges til at angive et navn til TPD.

```powershell
Import-RMSTrustedPublishingDomain -FileData ([System.IO.File]::ReadAllBytes('C:\Users\Administrator\Desktop\ExportTPD.xml')) -Name "Exported TPD" -ExtranetLicensingUrl https://corp.contoso.com/_wmcs/licensing -IntranetLicensingUrl https://rmsserver/_wmcs/licensing
```

Du kan finde detaljerede oplysninger om syntaks og parametre under [Import-RMSTrustedPublishingDomain](/powershell/module/exchange/import-rmstrustedpublishingdomain).

#### <a name="how-do-you-know-that-you-successfully-imported-the-tpd"></a>Hvordan ved du, at du har importeret TPD?

Kør **cmdlet'en Get-RMSTrustedPublishingDomain** for at hente TPD'er i din Exchange Online organisation for at kontrollere, at du har importeret TPD'en. Du kan finde flere oplysninger i eksemplerne i [Get-RMSTrustedPublishingDomain](/powershell/module/exchange/get-rmstrustedpublishingdomain).

### <a name="step-3-use-the-exchange-management-shell-to-distribute-an-ad-rms-rights-policy-template"></a>Trin 3: Brug Exchange Management Shell til at distribuere en SKABELON for AD RMS-rettigheder

Når du har importeret TPD'et, skal du sikre dig, at der distribueres en SKABELON for AD RMS-rettigheder. En distribueret skabelon er synlig for Outlook på internettet brugere (tidligere kaldet Outlook Web App), som derefter kan anvende skabelonerne på en mail.

Kør følgende kommando for at returnere en liste over alle skabeloner i standard-TPD:

```powershell
Get-RMSTemplate -Type All | fl
```

Hvis værdien af parameteren _Type_ er `Archived`, er skabelonen ikke synlig for brugerne. Det er kun distribuerede skabeloner i standard-TPD, der er tilgængelige i Outlook på internettet.

Hvis du vil distribuere en skabelon, skal du køre følgende kommando:

```powershell
Set-RMSTemplate -Identity "<name of the template>" -Type Distributed
```

Følgende kommando importerer f.eks. skabelonen Firmafortrolige.

```powershell
Set-RMSTemplate -Identity "Company Confidential" -Type Distributed
```

Du kan finde detaljerede oplysninger om syntaks og parametre under [Get-RMSTemplate](/powershell/module/exchange/get-rmstemplate) og [Set-RMSTemplate](/powershell/module/exchange/set-rmstemplate).

#### <a name="the-do-not-forward-template"></a>Skabelonen Videresend ikke

Når du importerer standard-TPD fra din lokale organisation til Exchange Online, importeres der én AD RMS-politikskabelon med navnet **Videresend ikke**. Denne skabelon distribueres som standard, når du importerer standard-TPD. Du kan ikke bruge **Set-RMSTemplate-cmdlet'en** til at ændre skabelonen **Videresend ikke** .

Når skabelonen **Videresend ikke** anvendes på en meddelelse, er det kun de modtagere, der er adresseret i meddelelsen, der kan læse meddelelsen. Desuden kan modtagere ikke gøre følgende:

- Videresend meddelelsen til en anden person.
- Kopiér indhold fra meddelelsen.
- Udskriv meddelelsen.

> [!IMPORTANT]
> Skabelonen **Videresend** ikke kan ikke forhindre, at oplysninger i en meddelelse kopieres med tredjepartsprogrammer, -kameraer eller -brugere, der transskriberer oplysningerne manuelt

Du kan oprette yderligere AD RMS-rettighedspolitikskabeloner på AD RMS-serveren i din lokale organisation for at opfylde dine IRM-beskyttelseskrav. Hvis du opretter yderligere AD RMS-rettighedspolitikskabeloner, skal du eksportere TPD fra AD RMS-serveren i det lokale miljø igen og opdatere TPD'en i den cloudbaserede mailorganisation.

#### <a name="how-do-you-know-that-you-successfully-distributed-the-ad-rms-rights-policy-template"></a>Hvordan ved du, at du har distribueret politikskabelonen FOR AD RMS-rettigheder?

Kør **cmdlet'en Get-RMSTemplate** for at kontrollere skabelonens egenskaber for at bekræfte, at du har distribueret og AD RMS-rettigheder. Du kan finde flere oplysninger i eksemplerne i [Get-RMSTemplate](/powershell/module/exchange/get-rmstemplate).

### <a name="step-4-use-the-exchange-management-shell-to-enable-irm"></a>Trin 4: Brug Exchange Management Shell til at aktivere IRM

Når du har importeret TPD og distribueret en SKABELON for AD RMS-rettigheder, skal du køre følgende kommando for at aktivere IRM for din skybaserede mailorganisation.

```powershell
Set-IRMConfiguration -InternalLicensingEnabled $true
```

Du kan finde detaljerede oplysninger om syntaks og parametre under [Set-IRMConfiguration](/powershell/module/exchange/set-irmconfiguration).

#### <a name="how-do-you-know-that-you-successfully-enabled-irm"></a>Hvordan ved du, at du har aktiveret IRM?

Hvis du vil kontrollere, at du har aktiveret IRM, skal du køre [Cmdlet'en Get-IRMConfiguration](/powershell/module/exchange/get-irmconfiguration) for at kontrollere IRM-konfigurationen i den Exchange Online organisation.

## <a name="how-do-you-know-this-task-worked"></a>Hvordan ved du, at denne opgave virkede?
<a name="sectionSection2"> </a>

Benyt følgende fremgangsmåde for at bekræfte, at du har importeret TPD og aktiveret IRM:

- Brug **cmdlet'en Test-IRMConfiguration** til at teste IRM-funktionalitet. Du kan finde flere oplysninger under "Eksempel 1" i [Test-IRMConfiguration](/powershell/module/exchange/test-irmconfiguration).

- Opret en ny meddelelse i Outlook på internettet og IRM-beskyt den ved at vælge Indstillingen **Angiv tilladelser** i den udvidede menu (![ikonet Flere indstillinger).](../media/ITPro-EAC-MoreOptionsIcon.gif)
