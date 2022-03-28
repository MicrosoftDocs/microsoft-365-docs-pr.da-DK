---
title: Trin 2. Tilmeld enheder til administration med Intune
ms.author: bcarter
author: brendacarter
f1.keywords:
- enroll devices into management
- enroll devices with Intune
- Intune mobile device platforms
manager: dougeby
audience: ITPro
description: Brug Intune og Autopilot til at tilmelde enheder til administration for at sikre, at de apps, der kører på dem, er kompatible og for at forhindre virksomhedens datalækager.
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- m365solution-managedevices
- m365solution-scenario
ms.custom: ''
keywords: ''
ms.openlocfilehash: 5810513cd3aa4fccd8ce0100f22c708c53527c42
ms.sourcegitcommit: bae72428d229827cba4c807d9cd362417afbcccb
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/02/2022
ms.locfileid: "63596957"
---
# <a name="step-2-enroll-devices-into-management-with-intune"></a>Trin 2. Tilmeld enheder til administration med Intune

Der er flere måder at sikre slutpunktet på, et udtryk, der ofte bruges til at referere til den kombinerede enhed, herunder enheder, apps og brugeridentitet. Sikkerhedspolitikker skal håndhæves konsekvent og pålideligt ikke kun på appsene, men også på selve enheden. Tilmelding af enheden til administration og registrering med en skyidentitetsudbyder, f.eks. Azure Active Directory, er en god start.

Uanset om en enhed er en personligt ejet BYOD-enhed eller en virksomhedsejede og fuldt administrerede enhed, er det godt at have indsigt i slutpunkterne, der tilgår organisationens ressourcer for at sikre, at du kun tillader sunde og kompatible enheder. Dette omfatter pålideligheden og pålideligheden af mobil- og skrivebordsapps, der kører på slutpunkter. Du skal sikre dig, at disse apps er sunde og kompatible, og at de forhindrer, at virksomhedens data ulækager til apps eller tjenester til forbrugere via ondsindede eller utilsigtede metoder.

Tilmeldingsprocessen for enheder etablerer en relation mellem brugeren, enheden og Microsoft Intune tjeneste. Hvis Microsoft Intune som enkeltstående tjeneste, kan du bruge en enkelt webbaseret administrationskonsol til at administrere Windows pc'er, macOS og de mest populære mobilenhedsplatforme.

Denne artikel anbefaler metoder til registrering af enheder i administration ved hjælp af Intune. Du kan finde flere oplysninger om disse metoder, og hvordan du installerer hver enkelt af dem, under Installationsvejledning[: Tilmeld enheder Microsoft Intune](/mem/intune/fundamentals/deployment-guide-enrollment).

![Trin til administration af enheder](../media/devices/intune-mdm-steps-1.png#lightbox)

## <a name="windows-enrollment"></a>Windows tilmelding
Der er flere muligheder for at tilmelde Windows 10 og Windows 11 enheder. De mest almindelige metoder omfatter disse to:

- Azure Active Directory (Azure AD) Deltag – tilmelder sig enheden med Azure Active Directory og gør det muligt for brugerne at logge på Windows med deres Azure AD-legitimationsoplysninger. Hvis Automatisk registrering er aktiveret, tilmeldes enheden automatisk Intune. Fordelen ved automatisk registrering er en trinvis proces for brugeren. Ellers skal de kun tilmeldes separat via MDM og angive deres legitimationsoplysninger igen. Brugerne tilmelder sig på denne måde enten under Windows OOBE eller fra Indstillinger. Enheden er markeret som en virksomhedsejet enhed i Intune.
- Autopilot – automatiserer Azure AD-tilmelding og tilmelder nye enheder, der ejes af virksomheden, til Intune. Denne metode forenkler køreoplevelsen og fjerner behovet for at anvende brugerdefinerede billeder fra operativsystemet på enhederne. Når administratorer bruger Intune til at administrere Autopilot-enheder, kan de administrere politikker, profiler, apps og meget mere, når de er tilmeldt. Der findes fire typer Autopilot-udrulning: Self-Deploying-tilstand (for kiosker, digital signage eller en delt enhed), brugerbaseret tilstand (for traditionelle brugere), Windows Autopilot til klargjort installation giver partnere eller it-medarbejdere mulighed for at klargøre en pc, der kører Windows 10 eller Windows  11 så det er fuldt konfigureret og forretningsklart, og Autopilot til eksisterende enheder gør det nemt at installere den nyeste version af Windows til dine eksisterende enheder.

Du kan finde flere indstillinger, herunder registrering af BYOD-Windows-enheder, under [Tilmeld Windows enheder Microsoft Intune](/mem/intune/fundamentals/deployment-guide-enrollment-windows).

## <a name="ios-and-ipados-enrollment"></a>Tilmelding til iOS og iPadOS

For brugerejede enheder (BYOD) kan du lade brugerne tilmelde deres personlige enheder til Intune-administration ved hjælp af en af følgende metoder.
- Tilmelding til enheder er noget af det, du måske synes om som en typisk BYOD-registrering. Det giver administratorer en lang række administrationsindstillinger.
- Brugerregistrering er en mere strømlinet registreringsproces, der giver administratorer et undersæt af indstillinger for administration af enheder. Denne funktion er i øjeblikket en prøveversion.

Til organisationer, der køber enheder til deres brugere, understøtter Intune følgende iOS/iPadOS-registreringsmetoder for virksomhedsejede enheder:
- Apples automatiserede tilmelding af enheder (ADE)
- Apple School Manager
- Tilmeldingsassistent til Apple Konfigureringsassistent
- Direkte registrering i Apple Configurator

Få mere at vide under [Tilmeld iOS- og iPadOS-enheder i Microsoft Intune](/mem/intune/fundamentals/deployment-guide-enrollment-ios-ipados).

## <a name="android-enrollment"></a>Tilmelding til Android 

Der er flere muligheder for Android-tilmelding afhængigt af typen af enhed, den type tilmelding, du gerne vil understøtte, samt ting som den Android-version, du bruger eller endda producenten (især Samsung). De fleste organisationer bruger Android-arbejdsprofiler til deres slutbrugere, især i BYOD-scenarier. 

Med en Android-arbejdsprofil er slutbrugerens oplysninger adskilt tydeligt med databeholdere samt separate apps til arbejdsbrug og personlig brug. Dette er en ideel måde for brugerne at tilmelde deres enhed på og samtidig bevare beskyttelsen af deres egne data og sikkerheden for virksomhedens data. 

Men hvis din organisation leverer Android-enheder, kan du vælge at bruge det, der kaldes en fuldt administreret (User Affinity) eller dedikeret (ingen User Affinity)-enhed.

Hvis du vil have mere at vide om Android-tilmelding, [skal du se Tilmeld Android-enheder Microsoft Intune](/mem/intune/fundamentals/deployment-guide-enrollment-android).

## <a name="macos-enrollment"></a>macOS-registrering

Tilmelding til macOS kan være et svært emne for mange it-organisationer. Medmindre størstedelen af brugerne er Mac-brugere, end du muligvis ikke administrerer disse typer enheder i stor udstrækning. Hvis du har et lille antal macOS-brugere, anbefaler vi Intune Only Enrollment. Hvis du har et stort antal macOS-brugere, anbefaler vi Intune + Jamf-registrering.  
- Intune Only-tilmelding – Dette er til grundlæggende administration af macOS-enheder. Det kræver en manuel proces ligesom de fleste andre brugerbaserede registreringsindstillinger. Men hvis du har et lille antal Mac-enheder, kan det være nemmere end at konfigurere en hel automatiseret infrastruktur kun for disse få brugere. Kun med Intune-tilmelding har du mulighed for at installere ting som f.eks. certifikater, adgangskodekonfigurationer og programmer. Du kan også konfigurere politikker for overholdelse af regler og standarder samt adgang via betinget adgang samt muligheden for at gennemtvinge kryptering og sletning af enhed. 
- Intune og Jamf-tilmelding – For dem, der er på udkig efter den dybeste support til Mac-administration med Sylf + Intune til Betinget adgang, har vi en god løsning, der kombinerer de omfattende Mac-administrationsfunktioner fra Jamf med Intune-overholdelse for at aktivere Betinget adgang. I dette scenarie administrerer du stadig enheden fuldt ud med Sylf, mens du kan tage disse signaler fra Sylf for at øge sikkerheden.

Du kan få mere at vide om macOS-tilmelding [under Tilmeld macOS-enheder Microsoft Intune](/mem/intune/fundamentals/deployment-guide-enrollment-macos).

## <a name="next-steps"></a>Næste trin

Gå til Trin [3. Konfigurer politikker for overholdelse af regler og standarder for enheder med Intune](manage-devices-with-intune-compliance-policies.md).

