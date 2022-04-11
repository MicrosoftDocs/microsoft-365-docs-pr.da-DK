---
title: Nye beskedpolitikker i Microsoft Defender for Office 365
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: reference
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
search.appverid:
- MET150
- MOE150
ms.custom:
- seo-marvel-apr2020
- admindeeplinkDEFENDER
ROBOTS: noindex,nofollow
description: Vi frigiver nye beskedpolitikker for Microsoft Defender for Office 365. Vi udfaser også to eksisterende beskedpolitikker, der er blevet erstattet af de nye.
ms.openlocfilehash: afdc547fc658b40c2eee7a92ef2043326e159b32
ms.sourcegitcommit: 9ba00298cfa9ae293e4a57650965fdb3e8ffe07b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/11/2022
ms.locfileid: "64759473"
---
# <a name="new-alert-policies-in-microsoft-defender-for-office-365"></a>Nye beskedpolitikker i Microsoft Defender for Office 365

Microsoft Defender for Office 365 introducerer nye og forbedrede advarselspolitikker i forbindelse med registreringer efter levering. Dette omfatter forbedringer af de air-playbooks (Automated Investigation & Response), der er knyttet til dem. Derudover ændrer vi klassificeringen af alvorsgrad for seks standardbeskedpolitikker for bedre at justere de beskeder, der genereres af disse politikker, med deres indvirkning på din organisation.

## <a name="post-delivery-detections"></a>Registreringer efter levering

Vi introducerer fire nye standardpolitikker for beskeder, der er relateret til registreringer efter levering, efter at den Microsoft Defender for Office 365 ZAP (Automatisk fjernelse på nul timer) fjerner meddelelser fra en indbakke. Disse fire nye beskedpolitikker erstatter to eksisterende standardpolitikker for beskeder, der dækker ZAP-scenarier, og giver organisationer forbedrede oplysninger om den underliggende registrering og relaterede indikatorer. Disse beskeder (og air-playbooks, der udløses fra disse beskeder) vil præcist fange truslerne fra mails og enheder, herunder hvis URL-adressen peger på en skadelig fil, eller hvis filen indeholder en ondsindet URL-adresse.

I følgende tabel vises de nye politikker for beskeder og de eksisterende politikker for beskeder, der fjernes. Se afsnittet [Sådan påvirker det din organisation](#how-this-will-affect-your-organization) for at få oplysninger om udrulningen.

|Ny eller eksisterende beskedpolitik|Navn på beskedpolitik|Beskedpolitik-id|
|---|---|---|
|Nye|**Mails, der indeholder skadelig URL-adresse, er fjernet efter levering**|8e6ba277-ef39-404e-aaf1-294f6d9a2b88|
|Nye|**Mails, der indeholder skadelig fil, er fjernet efter levering**|4b1820ec-39dc-45f3-abf6-5ee80df51fd2|
|Nye|**Mails fra en kampagne blev leveret og senere fjernet**|c8522cbb-9368-4e25-4ee9-08d8d899dfab|
|Nye|**Mails, der er fjernet efter levering**|b8f6b088-5487-4c70-037c-08d8d71a43fe|
|Eksisterende (fjernes)|**Mails, der indeholder phish-URL-adresser, der er fjernet efter levering**|EA8169FA-0678-4751-8854-AEBEA7ADECEB|
|Eksisterende (fjernes)|**Mails, der indeholder malware, er fjernet efter levering**|0179B3F7-3FDA-40C3-8F24-278563978DBB|

## <a name="alert-severity-enhancements"></a>Forbedringer af alvorsgrad af beskeder

I følgende tabel identificeres de standardpolitikker for beskeder, hvis klassificeringer for alvorsgrad ændres. Vi ændrer klassificeringen af alvorsgrad for disse politikker for beskeder for bedre at justere med den potentielle risiko og indvirkning på din organisation og for at hjælpe dine sikkerhedsteams med at prioritere de beskeder, der genereres af disse politikker.

|Besked|Beskedpolitik-id|Gammel alvorsgrad|Ny alvorsgrad|
|---|---|---|---|
|**Mistænkelig aktivitet for videresendelse af mail**|BFD48F06-0865-41A6-85FF-ADB746423EBF|Medium|Høj|
|**Mail, der er rapporteret af brugeren som malware eller phish**|B26A5770-0C38-434A-9380-3A3C2C27BBB3|Informative|Lav|
|**Usædvanlig stigning i e-mail rapporteret som phish**|A00D8C62-9320-4EEA-A7E5-966B9AC09558|Høj|Medium|
|**Resultat af administratorindsendelse er fuldført**|AE9B83DD-6039-4EA9-B675-6B0AC3BF4A41|Lav|Informative|
|**Oprettelse af regel for videresendelse/omdirigering**|D59A8FD4-1272-41EE-9408-86F7BCF72479|Lav|Informative|
|**eDiscovery-søgning er startet eller eksporteret**|6FDC5710-3998-47F0-AFBB-57CEFD7378A|Meduim|Informative|

## <a name="when-will-these-changes-happen"></a>Hvornår sker disse ændringer?

I følgende tabel identificeres det, hvornår de nye beskedpolitikker begynder at udløse beskeder efter levering. Tabellen identificerer også, hvornår de to eksisterende beskedpolitikker fjernes.

|Beskedpolitik|Dato|
|---|---|
|**Mails, der indeholder skadelig URL-adresse, er fjernet efter levering** (ny)|Beskeder udløses den 11. april 2021|
|**Mails, der indeholder skadelig fil, er fjernet efter levering** (ny)|Beskeder udløses den 11. april 2021|
|**Mails fra en kampagne blev leveret og senere fjernet** (ny)|Beskeder udløses den 28. maj 2021|
|**Ondsindede mails blev leveret og senere fjernet** (ny)|Beskeder udløses den 28. maj 2021|
|**Mails, der indeholder phish-URL-adresser, der er fjernet efter levering** (eksisterende, fjernes)|Advarselspolitikken blev fjernet i juni 2021. Se afsnittet [Hvad du skal gøre for at forberede dig på disse ændringer](#what-you-need-to-do-to-prepare-for-these-changes) .|
|**Mails, der indeholder malware fjernet efter levering** (eksisterende, fjernes)|Advarselspolitikken blev fjernet i juni 2021. Se afsnittet [Hvad du skal gøre for at forberede dig på disse ændringer](#what-you-need-to-do-to-prepare-for-these-changes) .|

Ændringerne af alvorsgraden af beskeden udrulles til alle organisationer senest den 14. maj 2021.

## <a name="how-this-will-affect-your-organization"></a>Sådan påvirker det din organisation

De nye beskeder begynder at udløse og udløse AIR-undersøgelserne i din organisation på de datoer, der er angivet ovenfor. Hvis du vil reducere indvirkningen på sikkerhedsorganisationer, der har aktiveret de to beskeder, der skal fjernes, kan du se beskeder udløst af de eksisterende politikker for beskeder *og* de beskeder, der udløses af de nye beskedpolitikker mellem 5. april 2021 og 28. maj 2021. Dette er for at give sikkerhedsteams tid til at håndtere de påkrævede ændringer. For at hjælpe sikkerhedsteams med den øgede beskedmængde i løbet af denne korte varighed vil både de eksisterende beskeder og de nye beskeder blive korreleret i den samme AIR-undersøgelse og korrelere i en samme hændelse. Dette omfatter mere specifikt følgende funktionsmåde for beskeder, AIR-undersøgelser og hændelser:

- **Beskeder**: Tilsigtet kan du se følgende beskedpar på tværs af de eksisterende og nye beskeder:

  - **Mails, der indeholder phish-URL-adresser, der er fjernet efter levering** AND **Mails, der indeholder skadelig URL-adresse fjernet efter levering**

  - **Mails, der indeholder malware, er fjernet efter levering** AND **Mails, der indeholder skadelig fil fjernet efter levering**

  ![Beskedpar for nye og eksisterende beskeder.](../media/DefenderAlerts.png)

   Du kan få flere oplysninger om administration af disse beskedpar i afsnittet [Hvad du skal gøre for at forberede dig på disse ændringer](#what-you-need-to-do-to-prepare-for-these-changes) .

- **AIR-undersøgelser**: Beskeder vil blive korreleret i en enkelt AIR-undersøgelse med en af de indberetninger, der er klassificeret som "udløsende" og den anden som "gentaget".

  ![Alarmpar i AIR-undersøgelser.](../media/AIRAlerts.png)

- **Hændelser**: Begge beskeder vil sammenholde med den samme hændelse

  ![Beskedpar i hændelser.](../media/IncidentsAlerts.png)

## <a name="what-you-need-to-do-to-prepare-for-these-changes"></a>Det skal du gøre for at forberede dig på disse ændringer

Den måde, din organisation bruger disse beskeder på, bestemmer, hvad du skal gøre for at forberede dig. Hvis du har driftsklargjort beskederne og bruger eller bruger dem enten via en API, en besked via mail eller i <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft 365 Overholdelsescenter</a> eller <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender-portalen</a>, skal du ændre dine arbejdsprocesser.

**Hvis du ikke har operationaliseret disse beskeder, kan du gøre et af følgende:**

- Deaktiver følgende politikker for beskeder (der fjernes) for at reducere mængden af beskeder i din organisation:

  - **Mails, der indeholder phish-URL-adresser, der er fjernet efter levering**

  - **Mails, der indeholder malware, er fjernet efter levering**

- Lad være med at gøre noget. Vi deaktiverer de eksisterende beskedpolitikker den 28. maj 2021.

**Hvis du har driftsklargjort disse beskeder:**

- Begynd at bruge de nye beskeder som en del af dine arbejdsprocesser i forventning om, at den eksisterende beskedpolitik fjernes den 28. maj 2021. Hvis du har brugerdefineret logik i dit billetsystem, en sikkerhedspostkasse, hvor du modtager beskedmailmeddelelser, eller en SIEM-løsning, der afhænger af beskednavnet eller beskedpolitik-id'et (CorrelationId), skal du ændre logikken for at imødekomme ændringen.

  > [!NOTE]
  > Oplysningerne i beskeder, undersøgelser og hændelser er ikke blevet ændret. Faktisk er disse oplysninger blevet forbedret med yderligere detaljer om de trusler, der er forbundet med dem.

- Når du har foretaget ændringerne, kan du deaktivere de eksisterende politikker for beskeder for at reducere mængden af beskeder i din organisation:

  - **Mails, der indeholder phish-URL-adresser, der er fjernet efter levering**

  - **Mails, der indeholder malware, er fjernet efter levering**

  Alternativt kan du lade disse beskedpolitikker være aktiveret, indtil vi sletter dem den 28. maj 2021.
