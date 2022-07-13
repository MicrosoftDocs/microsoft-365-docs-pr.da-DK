---
title: Dekryptering i eDiscovery
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.custom:
- seo-marvel-apr2020
description: Få mere at vide om, hvordan Microsoft 365 eDiscovery-værktøjer håndterer krypterede dokumenter, der er knyttet til mailmeddelelser og gemt i SharePoint Online og OneDrive for Business.
ms.openlocfilehash: 5e94c7b09745d017d5fa91d39a58c9d5351e911a
ms.sourcegitcommit: fa90763559239c4c46c5e848939126763879d8e4
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/13/2022
ms.locfileid: "66770849"
---
# <a name="decryption-in-microsoft-365-ediscovery-tools"></a>Dekryptering i Microsoft 365 eDiscovery-værktøjer

Kryptering er en vigtig del af din strategi til beskyttelse af filer og beskyttelse af oplysninger. Organisationer af alle typer bruger krypteringsteknologi til at beskytte følsomt indhold i deres organisation og sikre, at kun de rette personer har adgang til dette indhold.

For at udføre almindelige eDiscovery-opgaver på krypteret indhold skulle eDiscovery-ledere dekryptere mailindhold, efterhånden som det blev eksporteret fra indholdssøgninger, Microsoft Purview eDiscovery (Standard)-sager og Microsoft Purview eDiscovery (Premium)-sager. Indhold, der er krypteret med Microsoft-krypteringsteknologier, var først tilgængeligt til gennemsyn, efter at det blev eksporteret.

For at gøre det nemmere at administrere krypteret indhold i eDiscovery-arbejdsprocessen inkorporerer Microsoft 365 eDiscovery-værktøjer nu dekryptering af krypterede filer, der er knyttet til mails og sendt i Exchange Online.<sup> 1</sup> Derudover dekrypteres krypterede dokumenter, der er gemt i SharePoint Online og OneDrive for Business i eDiscovery (Premium)<sup>2</sup>.

Før denne nye funktion blev kun indholdet af en mail, der er beskyttet af Rights Management (og ikke vedhæftede filer), dekrypteret. Krypterede dokumenter i SharePoint og OneDrive kunne ikke dekrypteres under eDiscovery-arbejdsprocessen. Nu er filer, der er krypteret med en Microsoft-krypteringsteknologi, placeret på en SharePoint- eller OneDrive-konto, der kan søges i og dekrypteres, når søgeresultaterne forberedes til eksempelvisning, føjes til et gennemsynssæt i eDiscovery (Premium) og eksporteres. Derudover kan der søges i krypterede dokumenter i SharePoint og OneDrive, der er knyttet til en mail (som en kopi). Denne dekrypteringsfunktion gør det muligt for eDiscovery-ledere at få vist indholdet af krypterede vedhæftede filer i mails og webstedsdokumenter, når de får vist søgeresultater, og gennemse dem, når de er føjet til et korrektursæt i eDiscovery (Premium).

## <a name="supported-encryption-technologies"></a>Understøttede krypteringsteknologier

For Exchange understøtter Microsoft eDiscovery-værktøjer elementer, der er krypteret med Microsoft-krypteringsteknologier. Disse teknologier er Azure Rights Management (Azure RMS)<sup>3</sup> og Microsoft Purview Information Protection (især følsomhedsmærkater). Du kan få flere oplysninger om Microsoft-krypteringsteknologier under [Kryptering](encryption.md). Indhold, der er krypteret af S/MIME- eller tredjepartskrypteringsteknologier, understøttes ikke. Eksempelvisning eller eksport af indhold, der er krypteret med ikke-Microsoft-teknologier, understøttes f.eks. ikke.

> [!NOTE]
> Dekryptering af mails, der sendes med en [Microsoft Purview-meddelelseskryptering brugerdefineret brandingskabelon](add-your-organization-brand-to-encrypted-messages.md), understøttes ikke af Microsoft eDiscovery-værktøjer. Når du bruger en brugerdefineret OME-brandingskabelon, leveres mailmeddelelser til OME-portalen i stedet for modtagerens postkasse. Derfor kan du ikke bruge eDiscovery-værktøjer til at søge efter krypterede meddelelser, fordi disse meddelelser aldrig modtages af modtagerens postkasse.

For SharePoint dekrypteres indhold, der er mærket med SharePoint Online-tjenesten. Elementer, der er mærket eller krypteret i klienten, før de overføres til SharePoint, ældre RMS-skabeloner eller -indstillinger for dokumentbiblioteker og S/MIME eller andre standarder understøttes ikke<sup>2</sup>.

## <a name="ediscovery-activities-that-support-encrypted-items"></a>eDiscovery-aktiviteter, der understøtter krypterede elementer

I følgende tabel identificeres de understøttede opgaver, der kan udføres i eDiscovery-værktøjer i Microsoft 365 på krypterede filer, der er knyttet til mailmeddelelser og krypterede dokumenter i SharePoint og OneDrive. Disse understøttede opgaver kan udføres på krypterede filer, der opfylder kriterierne i en søgning. Værdien angiver `N/A` , at funktionaliteten ikke er tilgængelig i det tilsvarende eDiscovery-værktøj.

|eDiscovery-opgave  |Indholdssøgning  |eDiscovery (Standard)  |eDiscovery (Premium)  |
|:---------|:---------|:---------|:---------|
|Søg efter indhold i krypterede filer på websteder og vedhæftede filer i mails<sup>1</sup>     |Nej      |Nej      |Ja      |
|Vis krypterede filer, der er knyttet til mail     |Ja      |Ja     |Ja       |
|Vis krypterede dokumenter i SharePoint og OneDrive|Nej      |Nej    |Ja       |
|Gennemse krypterede filer i et korrektursæt    |NIELSEN      |NIELSEN        | Ja        |
|Eksportér krypterede filer, der er knyttet til mail    |Ja       |Ja  |Ja    |
|Eksportér krypterede dokumenter i SharePoint og OneDrive    |Nej       |Nej  |Ja    |
|||||

## <a name="decryption-limitations-with-sensitivity-labels-in-sharepoint-and-onedrive"></a>Dekrypteringsbegrænsninger med følsomhedsmærkater i SharePoint og OneDrive

eDiscovery understøtter ikke krypterede filer i SharePoint og OneDrive, når en følsomhedsmærkat, der anvendte krypteringen, er konfigureret med en af følgende indstillinger:

- Brugerne kan tildele tilladelser, når de anvender mærkaten manuelt på et dokument. Dette kaldes nogle gange *brugerdefinerede tilladelser*.

- Brugeradgang til dokumentet har en udløbsindstilling, der er angivet til en anden værdi end **Aldrig**.

Du kan finde flere oplysninger om disse indstillinger i afsnittet "Konfigurer krypteringsindstillinger" i [Begræns adgang til indhold ved hjælp af følsomhedsmærkater for at anvende kryptering](encryption-sensitivity-labels.md#configure-encryption-settings).

Dokumenter, der er krypteret med de tidligere indstillinger, kan stadig returneres af en eDiscovery-søgning. Dette kan ske, når en dokumentegenskab (f.eks. titlen, forfatteren eller datoen for ændring) svarer til søgekriterierne. Selvom disse dokumenter kan være inkluderet i søgeresultater, kan de ikke gennemses eller gennemses. Disse dokumenter forbliver også krypterede, når de eksporteres i eDiscovery (Premium).

> [!IMPORTANT]
> Dekryptering understøttes ikke for filer, der er krypteret lokalt og derefter uploadet til SharePoint eller OneDrive. Lokale filer, der krypteres af Azure Information Protection-klienten (AIP), og som derefter uploades til Microsoft 365, understøttes f.eks. ikke. Kun filer, der er krypteret i SharePoint- eller OneDrive-tjenesten, understøttes til dekryptering.

## <a name="requirements-for-decryption-in-ediscovery"></a>Krav til dekryptering i eDiscovery

Du skal tildeles rollen RMS Dekryptering for at få vist, gennemse og eksportere filer, der er krypteret med Microsoft-krypteringsteknologier. Du skal også tildeles denne rolle for at gennemse og forespørge krypterede filer, der føjes til et korrektursæt i eDiscovery (Premium).

Denne rolle tildeles som standard rollegruppen eDiscovery Manager på siden **Tilladelser** i Microsoft Purview-compliance-portal. Du kan finde flere oplysninger om RMS-dekrypteringsrollen under [Tildel eDiscovery-tilladelser](assign-ediscovery-permissions.md#rms-decrypt).

### <a name="decrypting-rms-protected-email-messages-and-encrypted-file-attachments-using-content-search-or-ediscovery-standard"></a>Dekrypterer RMS-beskyttede mails og krypterede vedhæftede filer ved hjælp af indholdssøgning eller eDiscovery (Standard)

Alle rettighedsbeskyttede (RMS-beskyttede) mails, der er inkluderet i resultaterne af en indholdssøgning, dekrypteres, når du eksporterer dem. Derudover dekrypteres alle filer, der er krypteret med en [Microsoft-krypteringsteknologi](encryption.md) , og som er knyttet til en mail, der er inkluderet i søgeresultaterne, når de eksporteres. Denne dekrypteringsfunktion er som standard aktiveret for medlemmer af rollegruppen eDiscovery Manager. Det skyldes, at rollen RMS Decrypt management som standard er tildelt denne rollegruppe. Vær opmærksom på følgende ting, når du eksporterer krypterede mails og vedhæftede filer:
  
- Hvis du som tidligere forklaret aktiverer dekryptering af RMS-beskyttede meddelelser, når du eksporterer dem, skal du eksportere søgeresultaterne som individuelle meddelelser. Hvis du eksporterer søgeresultater til en PST-fil, eksporteres RMS-beskyttede meddelelser som individuelle mails.

- Meddelelser, der dekrypteres, identificeres i **ResultsLog-rapporten** . Denne rapport indeholder en kolonne med navnet **Decode Status**, og en værdi af **Decoded** identificerer de meddelelser, der blev dekrypteret.

- Ud over at dekryptere vedhæftede filer, når du eksporterer søgeresultater, kan du også få vist den dekrypterede fil, når du får vist søgeresultaterne. Du kan kun få vist den rettighedsbeskyttede mailmeddelelse, når du har eksporteret den.

- Hvis du har brug for at forhindre nogen i at dekryptere RMS-beskyttende meddelelser og krypterede vedhæftede filer, skal du oprette en brugerdefineret rollegruppe (ved at kopiere den indbyggede rollegruppe eDiscovery Manager) og derefter fjerne rollen RMS Dekrypter administration fra den brugerdefinerede rollegruppe. Tilføj derefter den person, du ikke vil dekryptere meddelelser som medlem af den brugerdefinerede rollegruppe.

## <a name="notes"></a>Bemærkninger

<sup>1</sup> Krypterede filer, der er placeret på en lokal computer, og vedhæftede filer i skyen, der kopieres til en mail, dekrypteres og indekseres ikke for eDiscovery. 

<sup>2</sup> Kun elementer, der er mærket i SharePoint Online-tjenesten, dekrypteres, alt andet understøttes ikke, herunder mærkning eller kryptering i klienten før upload, ældre RMS-skabeloner eller -indstillinger for dokumentbiblioteket, SMIME eller andre standarder osv. Se [Aktivér følsomhedsmærkater for Office-filer](sensitivity-labels-sharepoint-onedrive-files.md).

<sup>3</sup> RMS-nøglerne skal administreres fuldt ud i cloudtjenesten M365/O365 – hvilket betyder, at DKE, BYOK, OnPrem RMS osv. ikke understøttes. Se [Din Azure Information Protection-lejernøgle](/azure/information-protection/plan-implement-tenant-key#tenant-root-keys-generated-by-microsoft).
