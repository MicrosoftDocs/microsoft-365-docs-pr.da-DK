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
description: Få mere at vide Microsoft 365 hvordan eDiscovery-værktøjer håndterer krypterede dokumenter, der er vedhæftet mails og gemt i SharePoint Online og OneDrive for Business.
ms.openlocfilehash: aa6d6a72353378f98b9e567500233b4c26f6221c
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/12/2022
ms.locfileid: "63594363"
---
# <a name="decryption-in-microsoft-365-ediscovery-tools"></a>Dekryptering i Microsoft 365 eDiscovery-værktøjer

Kryptering er en vigtig del af din strategi for filbeskyttelse og informationsbeskyttelse. Organisationer af alle typer bruger krypteringsteknologi til at beskytte følsomt indhold i organisationen og sikre, at kun de rette personer har adgang til indholdet.

For at udføre almindelige eDiscovery-opgaver på krypteret indhold blev eDiscovery-ledere bedt om at dekryptere mailindhold, da det blev eksporteret fra indholdssøgninger, centrale eDiscovery-sager og Advanced eDiscovery-sager. Indhold, der er krypteret med Microsofts krypteringsteknologier, kunne ikke gennemses, før efter det blev eksporteret.

For at gøre det nemmere at administrere krypteret indhold i eDiscovery-arbejdsprocessen indeholder Microsoft 365 eDiscovery-værktøjer nu dekryptering af krypterede filer, der er vedhæftet mails og sendt i Exchange Online.<sup> 1</sup> Desuden bliver krypterede dokumenter, der er SharePoint Online og OneDrive for Business, dekrypteret Advanced eDiscovery.

Før denne nye funktion er det kun indholdet af en mail, der er beskyttet af rettighedsstyring (og ikke vedhæftede filer), der blev dekrypteret. Krypterede dokumenter i SharePoint og OneDrive kunne ikke dekrypteres under eDiscovery-arbejdsprocessen. Nu er filer, der er krypteret med en Microsoft-krypteringsteknologi, placeret på en SharePoint- eller OneDrive-konto søgbare og dekrypteret, når søgeresultaterne er forberedt til forhåndsvisning, føjet til et korrektursæt i Advanced eDiscovery og eksporteret. Desuden kan der søges i krypterede SharePoint og OneDrive, der er vedhæftet en mail. Denne dekrypteringsfunktion gør det muligt for eDiscovery-ledere at få vist indholdet af krypterede vedhæftede filer og webstedsdokumenter, når søgeresultaterne vises, og gennemgå dem, når de er blevet føjet til et korrektursæt i Advanced eDiscovery.

## <a name="supported-encryption-technologies"></a>Understøttede krypteringsteknologier

Microsoft eDiscovery-værktøjer understøtter elementer, der er krypteret med Microsoft-krypteringsteknologier. Disse teknologier er Azure Rights Management og Microsoft Information Protection (specifikt følsomhedsmærkater). Du kan finde flere oplysninger om Microsofts krypteringsteknologier under [Kryptering](encryption.md). Indhold, der er krypteret med krypteringsteknologier fra tredjepart, understøttes ikke. Eksempelvis understøttes eksempelvisning eller eksport af indhold, der er krypteret med ikke-Microsoft-teknologier, ikke.

> [!NOTE]
> Dekryptering af mails, der sendes med [en Office 365-meddelelseskryptering (OME) brugerdefineret brandingskabelon](add-your-organization-brand-to-encrypted-messages.md), understøttes ikke af Microsoft eDiscovery-værktøjer. Når du bruger en OME-brugerdefineret brandingskabelon, leveres mails til OME-portalen i stedet for modtagerens postkasse. Derfor kan du ikke bruge eDiscovery-værktøjer til at søge efter OME-krypterede meddelelser, fordi disse meddelelser aldrig modtages i modtagerens postkasse.

## <a name="ediscovery-activities-that-support-encrypted-items"></a>eDiscovery-aktiviteter, der understøtter krypterede elementer

Følgende tabel identificerer de understøttede opgaver, der kan udføres i Microsoft 365 eDiscovery-værktøjer på krypterede filer, der er vedhæftet mails og krypterede dokumenter i SharePoint og OneDrive. Disse understøttede opgaver kan udføres på krypterede filer, der opfylder kriterierne for en søgning. En værdi af `N/A` angiver, at funktionaliteten ikke er tilgængelig i det tilsvarende eDiscovery-værktøj.

|eDiscovery-opgave  |Indholdssøgning  |Core eDiscovery  |Advanced eDiscovery  |
|:---------|:---------|:---------|:---------|
|Søge efter indhold i krypterede filer på websteder og vedhæftede filer <sup>i mails1</sup>     |Nej      |Nej      |Ja      |
|Forhåndsvisning af krypterede filer, der er vedhæftet en mail     |Ja      |Ja     |Ja       |
|Få vist krypterede dokumenter i SharePoint og OneDrive|Nej      |Nej    |Ja       |
|Gennemse krypterede filer i et gennemsynssæt    |I/T      |I/T        | Ja        |
|Eksportere krypterede filer, der er vedhæftet en mail    |Ja       |Ja  |Ja    |
|Eksportere krypterede dokumenter i SharePoint og OneDrive    |Nej       |Nej  |Ja    |
|||||

> [!NOTE]
> <sup>1 Krypterede</sup> filer, der er placeret på en lokal computer, og vedhæftede skyfiler, der er kopieret til en mail, bliver ikke dekrypteret og indekseret til eDiscovery. Du kan finde flere oplysninger og en løsning på disse scenarier i afsnittet [Dekrypteringsbegrænsninger med vedhæftede](#decryption-limitations-with-email-attachments) filer i mails i denne artikel.

## <a name="decryption-limitations-with-sensitivity-labels-in-sharepoint-and-onedrive"></a>Dekrypteringsbegrænsninger med følsomhedsetiketter i SharePoint og OneDrive

eDiscovery understøtter ikke krypterede filer i SharePoint og OneDrive når en følsomhedsmærkat, der anvendte krypteringen, er konfigureret med en af følgende indstillinger:

- Brugere kan tildele tilladelser, når de manuelt anvender etiketten på et dokument. Dette kaldes sommetider for *brugerdefinerede tilladelser*.

- Brugeradgang til dokumentet har en indstilling for udløb, der er angivet til en anden værdi end **Aldrig**.

Du kan finde flere oplysninger om disse indstillinger i afsnittet "Konfigurer krypteringsindstillinger" i Begræns adgang til indhold ved at bruge [følsomhedsmærkater til at anvende kryptering](encryption-sensitivity-labels.md#configure-encryption-settings).

Dokumenter, der er krypteret med de tidligere indstillinger, kan stadig returneres af en eDiscovery-søgning. Dette kan ske, når en dokumentegenskab (f.eks. titel, forfatter eller ændringsdato) svarer til søgekriterierne. Selvom disse dokumenter kan være inkluderet i søgeresultater, kan de ikke vises eller gennemses. Disse dokumenter forbliver også krypterede, når de eksporteres i Advanced eDiscovery.

> [!IMPORTANT]
> Dekryptering understøttes ikke for filer, der er krypteret lokalt og derefter uploadet til SharePoint eller OneDrive. Lokale filer, der er krypteret af AIP-klienten (Azure Information Protection) og derefter overført til Microsoft 365, understøttes f.eks. ikke. Kun filer, der er krypteret i SharePoint eller OneDrive, understøttes til dekryptering.

## <a name="decryption-limitations-with-email-attachments"></a>Dekrypteringsbegrænsninger med vedhæftede filer i mails

Følgende scenarier beskriver begrænsninger i dekryptering af filer, der er vedhæftet mails. Disse scenariebeskrivelser omfatter også løsninger, der kan afhjælpe disse begrænsninger.

- Hvis en fil, der er placeret på en lokal computer (og ikke er gemt på et SharePoint-websted eller en OneDrive-konto), er vedhæftet en mail, og en følsomhedsmærkat, der anvender kryptering, anvendes på mailen, kan den vedhæftede fil ikke dekrypteres af eDiscovery. Det betyder, at hvis du kører en søgeforespørgsel med nøgleord i modtagerens postkasse, så returneres den krypterede vedhæftede fil ikke af en søgeordssøgningsforespørgsel.

  Løsningen på denne begrænsning er at søge i afsenderens postkasse efter den samme vedhæftede fil. Det skyldes, at den kryptering, der anvendes af følsomhedsmærkatet, anvendes under transport af mailen. Det betyder, at den vedhæftede fil krypteres, når mailen sendes. Resultatet er forekomsten af den vedhæftede fil i afsenderens postkasse er ikke-krypteret, selvom den samme fil i modtagerens postkasse er krypteret.

- På samme måde kan vedhæftede filer i skyen (filer, der er gemt på et SharePoint-websted eller en OneDrive-konto), der kopieres til en mail (ved hjælp af indstillingen Vedhæft som kopi i Outlook), ikke dekrypteres af eDiscovery. Dette skyldes også, at den kryptering, der anvendes af en følsomhedsmærkat, anvendes, når mailen sendes. At søge i afsenderens postkasse efter den ikke-krypterede forekomst af den vedhæftede kopi fra skyen er også løsningen på denne begrænsning.

I begge disse scenarier kan mails med krypterede vedhæftede filer returneres af en eDiscovery-søgning, hvis en mailegenskab (f.eks. sendt dato, afsender, modtager eller emne) svarer til søgeforespørgslen.

## <a name="requirements-for-decryption-in-ediscovery"></a>Krav til dekryptering i eDiscovery

Du skal have tildelt rollen RMS Dekrypter for at få vist, gennemse og eksportere filer, der er krypteret med Microsoft-krypteringsteknologier. Du skal også have tildelt denne rolle for at gennemse og forespørge på krypterede filer, der er føjet til et gennemsynssæt Advanced eDiscovery.

Denne rolle **tildeles** som standard til rollegruppen eDiscovery Manager på siden Tilladelser i Microsoft 365 Overholdelsescenter. Du kan finde flere oplysninger om rollen RMS Dekrypter [under Tildele eDiscovery-tilladelser](assign-ediscovery-permissions.md#rms-decrypt).

### <a name="decrypting-rms-protected-email-messages-and-encrypted-file-attachments-using-content-search-or-core-ediscovery"></a>Dekryptering af RMS-beskyttede mails og krypterede vedhæftede filer ved hjælp af indholdssøgning eller Core eDiscovery

Alle rettighedsbeskyttede mails (RMS-beskyttede), der medtages i resultaterne af en indholdssøgning, bliver dekrypteret, når du eksporterer dem. Desuden bliver alle filer, der er krypteret med en [Microsoft-krypteringsteknologi](encryption.md) og vedhæftes en mail, som er inkluderet i søgeresultaterne, dekrypteret, når den eksporteres. Denne dekrypteringsfunktion er aktiveret som standard for medlemmer af rollegruppen eDiscovery Manager. Dette skyldes, at administrationsrollen RMS Dekrypter tildeles denne rollegruppe som standard. Husk følgende, når du eksporterer krypterede mails og vedhæftede filer:
  
- Som tidligere nævnt skal du eksportere søgeresultaterne som individuelle meddelelser for at dekryptere RMS-beskyttede meddelelser, når du eksporterer dem. Hvis du eksporterer søgeresultater til en PST-fil, forbliver RMS-beskyttede meddelelser krypteret.

- Meddelelser, der er dekrypteret, identificeres i **ResultsLog-rapporten** . Denne rapport indeholder en kolonne med navnet **Afkod status**, og en værdi af **Afkodet** identificerer de meddelelser, der blev dekrypteret.

- Ud over at dekryptere vedhæftede filer, når du eksporterer søgeresultater, kan du også se en forhåndsvisning af den dekrypterede fil, når du får vist søgeresultaterne. Du kan kun se den rettighedsbeskyttede mail, når du har eksporteret den.

- Hvis du vil forhindre nogen i at dekryptere RMS-beskytte meddelelser og krypterede vedhæftede filer, skal du oprette en brugerdefineret rollegruppe (ved at kopiere den indbyggede rollegruppe eDiscovery Manager) og derefter fjerne administrationsrollen RMS Dekrypter fra den brugerdefinerede rollegruppe. Tilføj derefter den person, du ikke vil dekryptere meddelelser fra, som medlem af den brugerdefinerede rollegruppe.
