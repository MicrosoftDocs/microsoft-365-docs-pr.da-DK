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
description: Brug Intune og Autopilot til at tilmelde enheder til administration for at sikre, at de apps, der kører på dem, overholder angivne standarder og for at forhindre, at virksomhedens data lækker.
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- m365solution-managedevices
- m365solution-scenario
ms.custom: ''
keywords: ''
ms.openlocfilehash: 177c21b46357ca890994751b9f4d7597a57c6b64
ms.sourcegitcommit: a06bb81fbd727a790a8fe6a3746b8a3cf62a6b24
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/05/2022
ms.locfileid: "64651273"
---
# <a name="step-2-enroll-devices-to-intune"></a>Trin 2. Tilmeld enheder til Intune

Der er flere måder at sikre slutpunktet på, et begreb, der ofte bruges til at henvise til det kombinerede objekt, herunder enheder, apps og brugeridentitet. Sikkerhedspolitikker skal håndhæves konsekvent og pålideligt ikke kun på appsene, men selve enheden. Det er en god start at tilmelde enheden for at Intune og registrere sig hos en cloudidentitetsudbyder, f.eks. Azure Active Directory.

Uanset om en enhed er en BYOD-enhed, der ejes personligt, eller en virksomhedsejet og fuldt administreret enhed, er det godt at have indblik i de slutpunkter, der har adgang til organisationens ressourcer, for at sikre, at du kun tillader sunde og kompatible enheder. Dette omfatter tilstanden og troværdigheden af mobil- og skrivebordsapps, der kører på slutpunkter. Du vil gerne sikre, at disse apps er sunde og kompatible, og at de forhindrer, at virksomhedsdata lækker til forbrugerapps eller -tjenester via ondsindede hensigter eller ved et uheld.

Processen til tilmelding af enheden etablerer en relation mellem brugeren, enheden og den Microsoft Intune tjeneste. Brug af Microsoft Intune som en separat tjeneste giver dig mulighed for at bruge en enkelt webbaseret administrationskonsol til at administrere Windows pc'er, macOS og de mest populære mobilenhedsplatforme.

Denne artikel anbefaler metoder til tilmelding af enheder til Intune. Du kan finde flere oplysninger om disse metoder, og hvordan du installerer hver enkelt, i [Installationsvejledning: Tilmeld enheder i Microsoft Intune](/mem/intune/fundamentals/deployment-guide-enrollment).

![Trin til administration af enheder](../media/devices/intune-mdm-steps-1.png#lightbox)

## <a name="windows-enrollment"></a>Windows tilmelding
Der er flere muligheder for at tilmelde Windows 10 og Windows 11 enheder. De mest almindelige metoder omfatter disse to:

- Azure Active Directory (Azure AD) Joinforbind – slutter enheden til Azure Active Directory og giver brugerne mulighed for at logge på Windows med deres Azure AD-legitimationsoplysninger. Hvis Automatisk tilmelding er aktiveret, bliver enheden automatisk tilmeldt Intune. Fordelen ved automatisk tilmelding er en proces med et enkelt trin for brugeren. Ellers skal de kun tilmelde sig separat via MDM-tilmelding og angive deres legitimationsoplysninger igen. Brugerne tilmelder sig på denne måde enten under den indledende Windows OOBE eller fra Indstillinger. Enheden er markeret som en virksomhedsejet enhed i Intune.
- Autopilot – automatiserer Azure AD Join og tilmelder nye virksomhedsejede enheder i Intune. Denne metode forenkler den køreklare oplevelse og fjerner behovet for at anvende brugerdefinerede operativsystemafbildninger på enhederne. Når administratorer bruger Intune til at administrere Autopilot-enheder, kan de administrere politikker, profiler, apps og meget mere, når de er tilmeldt. Der er fire typer udrulning af Autopilot: Self-Deploying-tilstand (for kiosker, digital skiltning eller en delt enhed), brugerdreven tilstand (for traditionelle brugere), Windows Autopilot til forudklargjort udrulning gør det muligt for partnere eller it-medarbejdere at klargøre en pc, der kører Windows 10 eller Windows 11  så den er fuldt konfigureret og klar til brug i virksomheden, og Autopilot til eksisterende enheder gør det nemt at udrulle den nyeste version af Windows på dine eksisterende enheder.

Du kan finde flere indstillinger, herunder tilmelding af BYOD-Windows enheder, [under Tilmeld Windows enheder i Microsoft Intune](/mem/intune/fundamentals/deployment-guide-enrollment-windows).

## <a name="ios-and-ipados-enrollment"></a>iOS- og iPadOS-tilmelding

For BYOD-enheder (user owned) kan du lade brugerne tilmelde deres personlige enheder til Intune administration ved hjælp af en af følgende metoder.
- Tilmelding af enheder er det, du måske synes om som typisk BYOD-tilmelding. Det giver administratorer en lang række administrationsmuligheder.
- Brugertilmelding er en mere strømlinet tilmeldingsproces, der giver administratorer et undersæt af indstillinger for enhedshåndtering. Denne funktion er i øjeblikket en prøveversion.

For organisationer, der køber enheder til deres brugere, understøtter Intune følgende iOS-/iPadOS-virksomhedsejede tilmeldingsmetoder til enheder:
- Apples automatiserede enhedsregistrering (ADE)
- Apple School Manager
- Tilmelding til Apple Configurator Setup Assistant
- Direkte tilmelding til Apple Configurator

Du kan få flere oplysninger under [Tilmeld iOS- og iPadOS-enheder i Microsoft Intune](/mem/intune/fundamentals/deployment-guide-enrollment-ios-ipados).

## <a name="android-enrollment"></a>Android-tilmelding 

Der er flere muligheder for Android-tilmelding afhængigt af enhedstypen, den type tilmelding, du vil understøtte, samt ting som den Android-version, du bruger, eller endda producenten (især Samsung). De fleste organisationer bruger Android Arbejdsprofiler til deres slutbrugere, især i BYOD-scenarier. 

Med en Android-arbejdsprofil er slutbrugerens oplysninger adskilt særskilt med dataobjektbeholdere samt separate apps til arbejde og personlig brug. Dette er en ideel måde for brugerne at tilmelde deres enhed på, samtidig med at de bevarer beskyttelsen af deres egne data og sikkerheden af virksomhedens data. 

Men hvis din organisation leverer Android-enheder, kan du vælge at bruge det, der kaldes en fuldt administreret (brugertilhør) eller dedikeret enhed (ingen brugertilhørsenhed).

Hvis du vil vide mere om Android-tilmelding, skal du se [Tilmeld Android-enheder i Microsoft Intune](/mem/intune/fundamentals/deployment-guide-enrollment-android).

## <a name="macos-enrollment"></a>macOS-tilmelding

Tilmelding til macOS kan være et vanskeligt emne for mange it-organisationer. Medmindre et flertal af dine brugere er Mac-brugere, end du muligvis ikke administrerer disse typer enheder i vid udstrækning. Hvis du har et lille antal macOS-brugere, anbefaler vi, at du Intune Kun tilmelding. Hvis du har et stort antal macOS-brugere, anbefaler vi, at du Intune + Jamf-tilmelding.  
- Intune kun tilmelding – dette er til grundlæggende administration af macOS-enheder. Det kræver en manuel proces, der ligner de fleste af de andre brugerbaserede tilmeldingsmuligheder. Men hvis du har et lille antal Mac-enheder, kan det være nemmere end at konfigurere en hel automatiseret infrastruktur kun for de få brugere. Med Intune kun tilmelding har du mulighed for at installere ting som certifikater, adgangskodekonfigurationer og programmer. Du kan også konfigurere politikker for overholdelse af regler og standarder og få betinget adgang samt muligheden for at gennemtvinge kryptering og enhedssletning. 
- Intune og Jamf-tilmelding – For dem, der leder efter den dybeste support til Mac-administration, med Jamf + Intune til betinget adgang, har vi en fantastisk løsning, der kombinerer Jamf's omfattende funktioner til administration af Mac med Intune overholdelse af angivne standarder for at aktivere betinget adgang. I dette scenarie administrerer du stadig enheden fuldt ud med Jamf, samtidig med at du kan tage disse signaler fra Jamf for at øge sikkerheden.

Du kan få mere at vide om macOS-tilmelding under [Tilmeld macOS-enheder i Microsoft Intune](/mem/intune/fundamentals/deployment-guide-enrollment-macos).

## <a name="next-steps"></a>Næste trin

Gå til trin [3. Konfigurer politikker for overholdelse af angivne standarder for enheder med Intune](manage-devices-with-intune-compliance-policies.md).

