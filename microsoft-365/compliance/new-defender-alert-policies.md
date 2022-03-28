---
title: Nye beskedpolitikker i Microsoft Defender til Office 365
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
description: Vi udgiver nye politikker for påmindelser for Microsoft Defender for Office 365. Vi udgår også to eksisterende politikker for påmindelser, der er blevet erstattet af de nye.
ms.openlocfilehash: 895a1fa51b9db5991bdb5235fd467bbac581d02e
ms.sourcegitcommit: 1ef176c79a0e6dbb51834fe30807409d4e94847c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/19/2021
ms.locfileid: "63597896"
---
# <a name="new-alert-policies-in-microsoft-defender-for-office-365"></a>Nye beskedpolitikker i Microsoft Defender til Office 365

Microsoft Defender for Office 365 introducerer nye og forbedrede advarselspolitikker i forbindelse med registreringer efter levering. Dette omfatter forbedringer af de automatiserede & Response (AIR), der er knyttet til dem. Desuden ændrer vi klassifikationen af alvorsgrad for seks standardbeskedpolitikker for bedre at justere de beskeder, der genereres af disse politikker, efter deres indvirkning på din organisation.

## <a name="post-delivery-detections"></a>Registreringer efter levering

Vi introducerer fire nye standardbeskedpolitikker, der er relateret til registreringer efter levering, efter Microsoft Defender til Office 365 automatisk tømning uden time (ZAP) fjerner meddelelser fra en indbakke. Disse fire nye politikker for påmindelser erstatter to eksisterende standardpolitikker for påmindelser, der dækker ZAP-scenarier og giver organisationer forbedrede oplysninger om den underliggende registrering og relaterede indikatorer. Disse beskeder (og AIR-playbooks, der udløser disse beskeder), registrerer nøjagtigt truslerne i mails og enheder, herunder hvis URL-adressen peger på en skadelig fil, eller hvis filen indeholder en skadelig URL-adresse.

I følgende tabel vises de nye politikker for påmindelsesbeskeder og de eksisterende beskedpolitikker, der fjernes. Se afsnittet [Hvordan dette påvirker din organisation](#how-this-will-affect-your-organization) for at få mere at vide om udrulningen.

| Ny eller eksisterende beskedpolitik | Navn på politik for besked | Id for beskedpolitik|
|:-----------------------------|:----------------|:--------------|
| Ny| **Mails, der indeholder skadelig URL-adresse fjernet efter levering**   | 8e6ba277-ef39-404e-aaf1-294f6d9a2b88 |
| Ny| **Mails, der indeholder skadelig fil fjernet efter levering**  | 4b1820ec-39dc-45f3-abf6-5ee80df51fd2 |
| Ny| **Mails fra en kampagne er blevet leveret og fjernet senere** | c8522cbb-9368-4e25-4ee9-08d8d899dfab |
| Ny|**Mails fjernet efter levering**                | b8f6b088-5487-4c70-037c-08d8d71a43fe |
| Eksisterende (fjernes)| **Mails, der indeholder phish-webadresser, der er fjernet efter levering**| EA8169FA-0678-4751-8854-AEBEA7ADECEB |
| Eksisterende (fjernes)| **Mails, der indeholder malware, der er fjernet efter levering**| 0179B3F7-3FDA-40C3-8F24-278563978DBB |
||||

## <a name="alert-severity-enhancements"></a>Vigtige forbedringer af alvorsgrad

I følgende tabel identificeres de standardbeskedpolitikker, hvis klassifikationer ændres. Vi ændrer klassificeringen af alvorsgraden for disse politikker, så de passer bedre til den potentielle risiko og indvirkning på organisationen og for at hjælpe dine sikkerhedsteams med at prioritere de beskeder, der genereres af disse politikker.

| Besked| Id for beskedpolitik| Gammel alvorsgrad| Ny alvorsgrad  |
|:----------|:---------------|:------------|:--------------|
| **Mistænkelig videresendelse af mail**| BFD48F06-0865-41A6-85FF-ADB746423EBF | Mellem| Høj|
| **Mail rapporteret af bruger som malware eller phish** | B26A5770-0C38-434A-9380-3A3C2C27BBB3 | Information | Lav|
| **Usædvanlig stigning i mail rapporteret som phish** | A00D8C62-9320-4EEA-A7E5-966B9AC09558 | Høj| Mellem |
| **Administratorafsendelsesresultat fuldført** | AE9B83DD-6039-4EA9-B675-6B0AC3BF4A41 | Lav| Information |
| **Oprettelse af regel for videresendelse/omdirigering** | D59A8FD4-1272-41EE-9408-86F7BCF72479 | Lav| Information |
| **eDiscovery-søgning startet eller eksporteret** | 6FDC5710-3998-47F0-AFBB-57CEFD7378A | Meduim | Information |
|||||

## <a name="when-will-these-changes-happen"></a>Hvornår sker disse ændringer?

I følgende tabel kan du se, hvornår de nye beskedpolitikker begynder at udløse beskeder efter levering. Tabellen identificerer også, hvornår de to eksisterende påmindelsespolitikker fjernes.

| Beskedpolitik| Dato |
|:------------|:-----|
| **Mails, der indeholder skadelig URL-adresse fjernet efter levering** (ny) | Beskeder begynder at udløses d. 11. april 2021|
| **Mails, der indeholder skadelig fil, der er fjernet efter levering** (ny) | Beskeder begynder at udløses d. 11. april 2021 |
| **Mails fra en kampagne er blevet leveret og senere fjernet** (ny) | Beskeder begynder at udløses den 28. maj 2021|
| **Ondsindede mails blev leveret og fjernet senere** (nye) | Beskeder begynder at udløses den 28. maj 2021|
| **Mails, der indeholder phish URL-adresser, der er fjernet** efter levering (eksisterende, fjernes)| Beskedpolitikken blev fjernet i juni 2021. Se [afsnittet Hvad du skal gøre for at forberede disse](#what-you-need-to-do-to-prepare-for-these-changes) ændringer.|
| **Mails, der indeholder malware, som er fjernet** efter levering (eksisterende, fjernes) | Beskedpolitikken blev fjernet i juni 2021. Se [afsnittet Hvad du skal gøre for at forberede disse](#what-you-need-to-do-to-prepare-for-these-changes) ændringer. |
|||

Alvorsgradsændringerne for beskeder udrulles til alle organisationer inden den 14. maj 2021.

## <a name="how-this-will-affect-your-organization"></a>Sådan vil det påvirke din organisation

De nye beskeder udløses og udløser AIR-undersøgelser i din organisation på de datoer, der er anført ovenfor. Hvis du vil reducere effekten på sikkerhedsorganisationer, der har aktiveret de to beskeder, der skal fjernes, får du vist beskeder, der er udløst af de eksisterende politikker  for påmindelsesbeskeder og de beskeder, der udløses af de nye beskedpolitikker mellem den 5. april 2021 og den 28. maj 2021. Dette er for at give sikkerhedsteams tid til at håndtere de nødvendige ændringer. For at hjælpe sikkerhedsteams med den øgede beskedmængde i denne korte periode vil både de eksisterende beskeder og de nye beskeder blive korreleret til den samme AIR-undersøgelse og korreleret til en samme hændelse. Mere specifikt omfatter dette følgende funktionsmåde for beskeder, AIR-undersøgelser og hændelser:

- **Beskeder**: Tilsendende kan du se følgende par af beskeder på tværs af eksisterende og nye beskeder:

  - **Mails, der indeholder phish-webadresser, der er fjernet efter levering** AND **Email messages containing malicious URL removed after delivery**

  - **Mails, der indeholder malware, der er fjernet efter levering** AND **Email messages containing malicious file removed after delivery**

  ![Giv par besked om nye og eksisterende beskeder.](../media/DefenderAlerts.png)

   Du kan finde flere oplysninger om administration af disse beskedpar i [afsnittet Hvad du skal gøre for at forberede dig på disse](#what-you-need-to-do-to-prepare-for-these-changes) ændringer.

- **AIR-undersøgelser**: Beskederne korreleres til en enkelt AIR-undersøgelse med en af de beskeder, der klassificeres som "udløsere", og den anden som "gentaget".

  ![Giv besked til par i AIR-undersøgelser.](../media/AIRAlerts.png)

- **Hændelser**: Begge beskeder korrelerer til den samme hændelse

  ![Giv besked til par i Hændelser.](../media/IncidentsAlerts.png)

## <a name="what-you-need-to-do-to-prepare-for-these-changes"></a>Hvad du skal gøre for at forberede disse ændringer

Hvordan din organisation anvender disse beskeder, afgør, hvad du skal gøre for at forberede dig. Hvis du har driftsiseret beskederne og bruger eller anvender dem enten via en API, en besked via mailbesked eller i <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft 365 Overholdelsescenter</a>- eller <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender-portalen</a>, skal du ændre dine arbejdsprocesser.

**Hvis du ikke har driftsiseret disse beskeder, kan du gøre et af følgende:**

- Deaktiver følgende politikker for påmindelser (som fjernes) for at reducere mængden af beskeder i organisationen:

  - **Mails, der indeholder phish-webadresser, der er fjernet efter levering**

  - **Mails, der indeholder malware, der er fjernet efter levering**

- Gør ingenting. Vi deaktiverer de eksisterende beskedpolitikker den 28. maj 2021.

**Hvis du har driftsklargjort disse beskeder:**

- Begynd at bruge de nye beskeder som en del af dine arbejdsprocesser i forbindelse med fjernelse af den eksisterende beskedpolitik den 28. maj 2021. Hvis du har en brugerdefineret logik i dit billetsystem, en sikkerhedspostkasse, hvor du modtager beskeder via mail eller en SIEM-løsning, der afhænger af beskednavnet eller korrelationspolitik-id'et (CorrelationId), skal du ændre logikken, så den tager højde for ændringen.

  > [!NOTE]
  > Oplysningerne i beskeder, undersøgelser og hændelser er ikke ændret. Faktisk er disse oplysninger blevet forbedret med yderligere detaljer om de trusler, der er knyttet til dem.

- Når du har foretaget ændringerne, kan du deaktivere de eksisterende påmindelsespolitikker for at reducere mængden af beskeder i organisationen:

  - **Mails, der indeholder phish-webadresser, der er fjernet efter levering**

  - **Mails, der indeholder malware, der er fjernet efter levering**

  Alternativt kan du lade disse politikker være aktiveret, indtil vi sletter dem den 28. maj 2021.
