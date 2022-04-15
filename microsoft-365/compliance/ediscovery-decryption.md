---
title: Dekryptering i eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
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
description: Få mere at vide om, hvordan Microsoft 365 eDiscovery-værktøjer håndterer krypterede dokumenter, der er knyttet til mails og gemt i SharePoint Online og OneDrive for Business.
ms.openlocfilehash: ae4e1fe274015da27514ef5149cd05c09928890b
ms.sourcegitcommit: e3bc6563037bd2cce2abf108b3d1bcc2ccf538f6
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/15/2022
ms.locfileid: "64861923"
---
# <a name="decryption-in-microsoft-365-ediscovery-tools"></a>Dekryptering i Microsoft 365 eDiscovery-værktøjer

Kryptering er en vigtig del af din strategi til beskyttelse af filer og beskyttelse af oplysninger. Organisationer af alle typer bruger krypteringsteknologi til at beskytte følsomt indhold i deres organisation og sikre, at kun de rette personer har adgang til dette indhold.

For at udføre almindelige eDiscovery-opgaver på krypteret indhold skulle eDiscovery-ledere dekryptere mailindhold, efterhånden som det blev eksporteret fra indholdssøgninger, centrale eDiscovery-sager og Advanced eDiscovery sager. Indhold, der er krypteret med Microsoft-krypteringsteknologier, var først tilgængeligt til gennemsyn, efter at det blev eksporteret.

For at gøre det nemmere at administrere krypteret indhold i eDiscovery-arbejdsprocessen omfatter Microsoft 365 eDiscovery-værktøjer nu dekryptering af krypterede filer, der er knyttet til mails og sendt i Exchange Online.<sup> 1</sup> Desuden dekrypteres krypterede dokumenter, der er gemt i SharePoint Online, og OneDrive for Business i Advanced eDiscovery.

Før denne nye funktion blev kun indholdet af en mail, der er beskyttet af Rights Management (og ikke vedhæftede filer), dekrypteret. Krypterede dokumenter i SharePoint og OneDrive kunne ikke dekrypteres under eDiscovery-arbejdsprocessen. Nu er filer, der krypteres med en Microsoft-krypteringsteknologi, placeret på en SharePoint- eller OneDrive-konto, der kan søges i og dekrypteres, når søgeresultaterne forberedes til eksempelvisning, føjes til et korrektursæt i Advanced eDiscovery og eksporteres. Derudover kan der søges i krypterede dokumenter i SharePoint og OneDrive, der er knyttet til en mail. Denne dekrypteringsfunktion gør det muligt for eDiscovery-ledere at få vist indholdet af krypterede vedhæftede filer i mails og webstedsdokumenter, når de får vist søgeresultater, og gennemse dem, når de er føjet til et korrektursæt i Advanced eDiscovery.

## <a name="supported-encryption-technologies"></a>Understøttede krypteringsteknologier

Microsoft eDiscovery-værktøjer understøtter elementer, der er krypteret med Microsoft-krypteringsteknologier. Disse teknologier er Azure Rights Management og Microsoft informācijas aizsardzība (specifikt følsomhedsmærkater). Du kan få flere oplysninger om Microsoft-krypteringsteknologier under [Kryptering](encryption.md). Indhold, der er krypteret af krypteringsteknologier fra tredjepart, understøttes ikke. Eksempelvisning eller eksport af indhold, der er krypteret med ikke-Microsoft-teknologier, understøttes f.eks. ikke.

> [!NOTE]
> Dekryptering af mails, der sendes med en [brugerdefineret OME-skabelon (Office 365 Message Encryption),](add-your-organization-brand-to-encrypted-messages.md) understøttes ikke af Microsoft eDiscovery-værktøjer. Når du bruger en brugerdefineret OME-brandingskabelon, leveres mailmeddelelser til OME-portalen i stedet for modtagerens postkasse. Derfor kan du ikke bruge eDiscovery-værktøjer til at søge efter OME-krypterede meddelelser, fordi disse meddelelser aldrig modtages af modtagerens postkasse.

## <a name="ediscovery-activities-that-support-encrypted-items"></a>eDiscovery-aktiviteter, der understøtter krypterede elementer

I følgende tabel identificeres de understøttede opgaver, der kan udføres i Microsoft 365 eDiscovery-værktøjer på krypterede filer, der er knyttet til mailmeddelelser og krypterede dokumenter i SharePoint og OneDrive. Disse understøttede opgaver kan udføres på krypterede filer, der opfylder kriterierne i en søgning. Værdien angiver `N/A` , at funktionaliteten ikke er tilgængelig i det tilsvarende eDiscovery-værktøj.

|eDiscovery-opgave  |Indholdssøgning  |Grundlæggende eDiscovery  |Avanceret eDiscovery  |
|:---------|:---------|:---------|:---------|
|Søg efter indhold i krypterede filer på websteder og vedhæftede filer <sup>i mails1</sup>     |Nej      |Nej      |Ja      |
|Vis krypterede filer, der er knyttet til mail     |Ja      |Ja     |Ja       |
|Vis krypterede dokumenter i SharePoint og OneDrive|Nej      |Nej    |Ja       |
|Gennemse krypterede filer i et korrektursæt    |NIELSEN      |NIELSEN        | Ja        |
|Eksportér krypterede filer, der er knyttet til mail    |Ja       |Ja  |Ja    |
|Eksportér krypterede dokumenter i SharePoint og OneDrive    |Nej       |Nej  |Ja    |
|||||

> [!NOTE]
> <sup>1</sup> Krypterede filer, der er placeret på en lokal computer, og vedhæftede filer i skyen, der kopieres til en mail, dekrypteres og indekseres ikke for eDiscovery. Du kan få flere oplysninger og en løsning til disse scenarier i afsnittet [Dekrypteringsbegrænsninger med vedhæftede filer i mails](#decryption-limitations-with-email-attachments) i denne artikel.

## <a name="decryption-limitations-with-sensitivity-labels-in-sharepoint-and-onedrive"></a>Dekrypteringsbegrænsninger med følsomhedsmærkater i SharePoint og OneDrive

eDiscovery understøtter ikke krypterede filer i SharePoint og OneDrive, når en følsomhedsmærkat, der anvendte krypteringen, er konfigureret med en af følgende indstillinger:

- Brugerne kan tildele tilladelser, når de anvender mærkaten manuelt på et dokument. Dette kaldes nogle gange *brugerdefinerede tilladelser*.

- Brugeradgang til dokumentet har en udløbsindstilling, der er angivet til en anden værdi end **Aldrig**.

Du kan finde flere oplysninger om disse indstillinger i afsnittet "Konfigurer krypteringsindstillinger" i [Begræns adgang til indhold ved hjælp af følsomhedsmærkater for at anvende kryptering](encryption-sensitivity-labels.md#configure-encryption-settings).

Dokumenter, der er krypteret med de tidligere indstillinger, kan stadig returneres af en eDiscovery-søgning. Dette kan ske, når en dokumentegenskab (f.eks. titlen, forfatteren eller datoen for ændring) svarer til søgekriterierne. Selvom disse dokumenter kan være inkluderet i søgeresultater, kan de ikke gennemses eller gennemses. Disse dokumenter forbliver også krypterede, når de eksporteres i Advanced eDiscovery.

> [!IMPORTANT]
> Dekryptering understøttes ikke for filer, der er krypteret lokalt og derefter uploadet til SharePoint eller OneDrive. Lokale filer, der krypteres af Azure Information Protection-klienten (AIP), og som derefter uploades til Microsoft 365, understøttes f.eks. ikke. Kun filer, der er krypteret i tjenesten SharePoint eller OneDrive, understøttes til dekryptering.

## <a name="decryption-limitations-with-email-attachments"></a>Dekrypteringsbegrænsninger med vedhæftede filer i mails

I følgende scenarier beskrives begrænsningerne i dekryptering af filer, der er knyttet til mails. Disse scenariebeskrivelser omfatter også løsninger til at afhjælpe disse begrænsninger.

- Hvis en fil, der er placeret på en lokal computer (og ikke er gemt på et SharePoint websted eller OneDrive konto), er knyttet til en mail, og der anvendes en følsomhedsmærkat, der anvender kryptering på mailen, kan den vedhæftede fil ikke dekrypteres af eDiscovery. Det betyder, at hvis du kører en søgeforespørgsel med nøgleord i modtagerens postkasse, returneres den krypterede vedhæftede fil ikke af en søgeforespørgsel med nøgleord.

  Løsningen på denne begrænsning er at søge i afsenderens postkasse efter den samme vedhæftede fil. Det skyldes, at krypteringen, der anvendes af følsomhedsmærkaten, anvendes under transport af mailen. Det betyder, at den vedhæftede fil krypteres, når mailen sendes. Resultatet er, at den vedhæftede fil i afsenderens postkasse ikke krypteres, selvom den samme fil i modtagerens postkasse er krypteret.

- På samme måde kan vedhæftede filer i skyen (filer, der er gemt på et SharePoint websted eller OneDrive konto), som kopieres til en mail (ved hjælp af indstillingen **Vedhæft som kopi** i Outlook) ikke dekrypteres af eDiscovery. Det skyldes også, at den kryptering, der anvendes af en følsomhedsmærkat, anvendes, når mailen sendes. Du kan også løse problemet ved at søge i afsenderens postkasse efter den ukrypterede forekomst af kopien af den vedhæftede fil i skyen.

I begge disse scenarier kan mails med krypterede vedhæftede filer returneres af en eDiscovery-søgning, hvis en mailegenskab (f.eks. afsendelsesdato, afsender, modtager eller emne) stemmer overens med søgeforespørgslen.

## <a name="requirements-for-decryption-in-ediscovery"></a>Krav til dekryptering i eDiscovery

Du skal tildeles rollen RMS Dekryptering for at få vist, gennemse og eksportere filer, der er krypteret med Microsoft-krypteringsteknologier. Du skal også have tildelt denne rolle for at gennemse og forespørge krypterede filer, der føjes til et korrektursæt i Advanced eDiscovery.

Denne rolle tildeles som standard rollegruppen eDiscovery Manager på siden **Tilladelser** i Qendra e pajtimit e Microsoft 365. Du kan finde flere oplysninger om RMS-dekrypteringsrollen under [Tildel eDiscovery-tilladelser](assign-ediscovery-permissions.md#rms-decrypt).

### <a name="decrypting-rms-protected-email-messages-and-encrypted-file-attachments-using-content-search-or-core-ediscovery"></a>Dekrypterer RMS-beskyttede mails og krypterede vedhæftede filer ved hjælp af indholdssøgning eller kerne-eDiscovery

Alle rettighedsbeskyttede (RMS-beskyttede) mails, der er inkluderet i resultaterne af en indholdssøgning, dekrypteres, når du eksporterer dem. Derudover dekrypteres alle filer, der er krypteret med en [Microsoft-krypteringsteknologi](encryption.md) , og som er knyttet til en mail, der er inkluderet i søgeresultaterne, når de eksporteres. Denne dekrypteringsfunktion er som standard aktiveret for medlemmer af rollegruppen eDiscovery Manager. Det skyldes, at rollen RMS Decrypt management som standard er tildelt denne rollegruppe. Vær opmærksom på følgende ting, når du eksporterer krypterede mails og vedhæftede filer:
  
- Hvis du som tidligere forklaret aktiverer dekryptering af RMS-beskyttede meddelelser, når du eksporterer dem, skal du eksportere søgeresultaterne som individuelle meddelelser. Hvis du eksporterer søgeresultater til en PST-fil, eksporteres RMS-beskyttede meddelelser som individuelle mails.

- Meddelelser, der dekrypteres, identificeres i **ResultsLog-rapporten** . Denne rapport indeholder en kolonne med navnet **Decode Status**, og en værdi af **Decoded** identificerer de meddelelser, der blev dekrypteret.

- Ud over at dekryptere vedhæftede filer, når du eksporterer søgeresultater, kan du også få vist den dekrypterede fil, når du får vist søgeresultaterne. Du kan kun få vist den rettighedsbeskyttede mailmeddelelse, når du har eksporteret den.

- Hvis du har brug for at forhindre nogen i at dekryptere RMS-beskyttende meddelelser og krypterede vedhæftede filer, skal du oprette en brugerdefineret rollegruppe (ved at kopiere den indbyggede rollegruppe eDiscovery Manager) og derefter fjerne rollen RMS Dekrypter administration fra den brugerdefinerede rollegruppe. Tilføj derefter den person, du ikke vil dekryptere meddelelser som medlem af den brugerdefinerede rollegruppe.
