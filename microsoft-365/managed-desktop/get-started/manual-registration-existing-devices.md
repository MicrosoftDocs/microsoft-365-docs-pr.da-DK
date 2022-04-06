---
title: Manuel registrering af eksisterende enheder
description: Registrer eksisterende enheder, så de kan administreres af Microsoft Managed Desktop
ms.service: m365-md
author: tiaraquan
f1.keywords:
- NOCSH
ms.author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
manager: dougeby
ms.topic: article
audience: Admin
ms.openlocfilehash: 1d100cc3336dcb465e54f4b81d13d50ecd4bfe1e
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63703817"
---
# <a name="manual-registration-for-existing-devices"></a>Manuel registrering af eksisterende enheder

>[!NOTE]
>I denne artikel beskrives trinnene, du kan bruge til at genbruge enheder, du allerede har, og registrere dem i Microsoft Managed Desktop. Hvis du arbejder med helt nye enheder, skal du i stedet følge trinnene i [Registrer nye enheder i Microsoft Managed Desktop](manual-registration.md) . <br> <br> Processen for partnere er dokumenteret i Trin [for partnere til registrering af enheder](partner-registration.md).

Microsoft-administreret skrivebord kan fungere med helt nye enheder, eller du kan genbruge enheder, som du måske allerede har. Hvis du genbruger enheder, skal du animere dem igen. Du kan registrere enheder med Microsoft Managed Desktop i Microsoft Endpoint Manager portal.

## <a name="prepare-to-register-existing-devices"></a>Forbered dig på at registrere eksisterende enheder

**Sådan registreres eksisterende enheder:**

1. [Hent hardware-hash'en for hver enhed.](#obtain-the-hardware-hash)
2. [Flet hash-dataene](#merge-hash-data).
3. [Registrer enhederne i Microsoft Managed Desktop](#register-devices-by-using-the-admin-portal).
4. [Kontrollér, at billedet er korrekt.](#check-the-image)
5. [Lever enheden](#deliver-the-device).

### <a name="obtain-the-hardware-hash"></a>Hent hardwarehash'en

Microsoft Managed Desktop identificerer hver enhed entydigt ved at referere til dens hardwarehash. Du har fire muligheder for at hente disse oplysninger fra enheder, du allerede bruger.

**Sådan får du hardwarehash'en:**

- Spørg din OEM-leverandør om AutoPilot-registreringsfilen, som vil indeholde hardwarehashes.
- Indsaml oplysninger [Microsoft Endpoint Configuration Manager](#microsoft-endpoint-configuration-manager).
- Kør et Windows PowerShell script enten ved hjælp [af Active Directory](#active-directory-powershell-script-method) eller manuelt på [](#manual-powershell-script-method) hver enhed, og indsaml resultaterne i en fil.
- Start hver enhed, men fuldfør ikke konfigurationen Windows, og [indsaml hashes på et flytbart flashdrev](#flash-drive-method).

#### <a name="microsoft-endpoint-configuration-manager"></a>Microsoft Endpoint Configuration Manager

Du kan bruge Microsoft Endpoint Configuration Manager til at indsamle hardwarehashes fra eksisterende enheder, som du vil registrere med Microsoft Managed Desktop. Hvis du har opfyldt alle disse forudsætninger, er du klar til at indsamle oplysningerne.

> [!IMPORTANT]
> Alle enheder, du vil have disse oplysninger til, skal køre Windows 10 version 1703 eller nyere.

**Sådan indsamler du oplysninger om hardwarehash:**

1. I Konfigurationsstyring skal du vælge **Overvågning**.
2. I arbejdsområdet Overvågning **skal du udvide** noden Rapportering, **udvide** Rapporter og vælge **noden Hardware – Generel** .
3. Kør rapporten, **Windows oplysninger om AutoPilot-enheden**, og få vist resultaterne.
4. I rapportvisningen skal du vælge ikonet **Eksportér** og vælge **csv-indstillingen (kommasepareret** ).
5. Når du har gemt filen, skal du filtrere resultaterne til de enheder, du planlægger at registrere med Microsoft Managed Desktop. Overfør derefter dataene til Microsoft Managed Desktop.
    - Åbn Microsoft Endpoint Manager, og gå til **menuen** Enheder.
    - I sektionen Microsoft Managed Desktop skal du vælge **Enheder**.
    - Vælg **+ Registrer enheder**, som åbner et fly-in for at registrere nye enheder.

Få mere at vide under [Registrer enheder ved hjælp af administrationsportalen](#register-devices-by-using-the-admin-portal) nedenfor.

#### <a name="active-directory-powershell-script-method"></a>Active Directory PowerShell-scriptmetode

I et Active Directory-miljø kan `Get-WindowsAutoPilotInfo` du bruge PowerShell-cmdlet'en til at indsamle oplysninger fra enheder eksternt i Active Directory-grupper ved hjælp af WinRM. Du kan også bruge `Get-AD Computer` cmdlet'en og få filtrerede resultater for et bestemt navn på hardwaremodellen, der er inkluderet i kataloget. Bekræft disse forudsætninger, før du fortsætter, og fortsæt derefter.

**Sådan bruges scriptmetoden Active Directory PowerShell:**

1. Sørg for, at WinRM er aktiveret.
1. De enheder, du vil registrere, er aktive på netværket. Det vil sige, at de ikke afbrydes eller slås fra.
1. Sørg for, at du har en parameter for domænelegitimationsoplysninger, der har tilladelse til at udføre eksternt på enhederne.
1. Sørg for, Windows Firewall tillader adgang til WMI. Det gør du ved at følge disse trin:

    - Åbn Windows Defender **Firewall**, og vælg **Tillad en app eller funktion at bruge Windows Defender Firewall**.
    - Find **Windows WMI (Management Instrumentation)** på listen, aktivér for **både Privat og Offentlig**, og vælg derefter **OK**.
1. Åbn en PowerShell-meddelelse med administrative rettigheder.
1. Kør *et af* disse scripts:

    ```powershell
    Install-script -name Get-WindowsAutoPilotInfo 
    #example one – leverage Get-ADComputer to enumerate devices 
    Get-ADComputer -filter * | powershell -ExecutionPolicy Unrestricted Get-WindowsAutoPilotInfo.ps1 -credential Domainname\<accountname>
    ```

    ```powershell
    #example two – target specific devices: 
    Set-ExecutionPolicy powershell -ExecutionPolicy Unrestricted Get-WindowsAutoPilotInfo.ps1 -credential Domainname\<accountname> -Name Machine1,Machine2,Machine3
    ```

1. Få adgang til alle mapper, hvor der kan være poster for enhederne. Fjern poster for hver enhed fra *alle* mapper, herunder Windows Server Active Directory-domæneservices og Azure Active Directory. Det kan tage et par timer at behandle processen fuldstændigt.
1. Adgangsstyringstjenester, hvor der kan være poster for enhederne. Fjern poster for hver enhed fra *alle* administrationstjenester, herunder Microsoft Endpoint Configuration Manager, Microsoft Intune og Windows Autopilot. Det kan tage et par timer at behandle processen fuldstændigt.

Nu kan du fortsætte med at [registrere enheder](#register-devices-by-using-the-admin-portal).

#### <a name="manual-powershell-script-method"></a>Manuel PowerShell-scriptmetode

**Sådan bruges den manuelle Powershell-scriptmetode:**

1. Åbn en PowerShell-meddelelse med administrative rettigheder.
2. Kør `Install-Script -Name Get-WindowsAutoPilotInfo`.
3. Kør `powershell -ExecutionPolicy Unrestricted Get-WindowsAutoPilotInfo -OutputFile <path>\hardwarehash.csv`.
4. [Flet hash-dataene.](#merge-hash-data)

#### <a name="flash-drive-method"></a>Flashdrevmetode

**Sådan bruger du flashdrevmetoden:**

1. Indsæt et USB-drev på en anden enhed end den, du er ved at registrere.
2. Åbn en PowerShell-meddelelse med administrative rettigheder.
3. Kør `Save-Script -Name Get-WindowsAutoPilotInfo -Path <pathToUsb>`.
4. Slå den enhed, du registrerer, til, *men start ikke konfigurationsoplevelsen*. Hvis du ved et uheld kommer til at starte konfigurationen, er du nødt til at nulstille eller animere enheden.
5. Indsæt USB-drevet, og tryk derefter på Shift + F10.
6. Åbn en PowerShell-prompt med administrative rettigheder, og kør derefter `cd <pathToUsb>`.
7. Kør `Set-ExecutionPolicy -ExecutionPolicy Unrestricted`.
8. Kør `.\Get-WindowsAutoPilotInfo -OutputFile <path>\hardwarehash.csv`.
9. Fjern USB-drevet, og luk enheden ved at køre `shutdown -s -t 0`.
10. [Flet hash-dataene.](#merge-hash-data)

> [!IMPORTANT]
> Tænd ikke for den enhed, du tilmelder dig igen, før du har fuldført tilmeldingen til den.

### <a name="merge-hash-data"></a>Flet hash-data

Hvis du har indsamlet hardwarehashdataene med de manuelle PowerShell- eller flashdrevsmetoder, skal du kombinere dataene i de to CSV-filer til en enkelt fil for at fuldføre registreringen. Her er et eksempel på et PowerShell-script, der gør det nemt:

```powershell
Import-CSV -Path (Get-ChildItem -Filter *.csv) | ConvertTo-Csv -NoTypeInformation | % {$_.Replace('"', '')} | Out-File .\aggregatedDevices.csv
```

Når hash-dataene er flettet ind i én CSV-fil, kan du nu fortsætte med [at registrere enhederne](#register-devices-by-using-the-admin-portal).

## <a name="register-devices-by-using-the-admin-portal"></a>Registrere enheder ved hjælp af administrationsportalen

I [Microsoft Endpoint Manager](https://endpoint.microsoft.com/) du vælge **Enheder** i venstre navigationsrude. I sektionen Microsoft Managed Desktop skal du vælge **Enheder**. I arbejdsområdet Microsoft-administrerede stationære enheder skal **du vælge + Registrer** enheder, som åbner et pop op-vindue for at registrere nye enheder.

<!-- Update with new picture [![Fly-in after selecting Register devices, listing devices with columns for assigned users, serial number, status, last-seen date, and age.](../../media/new-registration-ui.png)](../../media/new-registration-ui.png) -->

<!--Registering any existing devices with Managed Desktop will completely re-image them; make sure you've backed up any important data prior to starting the registration process.-->

**Sådan registrerer du enheder ved hjælp af administrationsportalen:**

1. Angiv **en sti til** den CSV-fil, du oprettede tidligere, under Filoverførsel.
2. Vælg [en enhedsprofil](../service-description/profiles.md) i rullemenuen.
3. Vælg **Registrer enheder**. Systemet føjer enhederne til din liste over enheder på **enhedens blade**. Enhederne er markeret som Registrering **afventer**. Registrering tager typisk mindre end 10 minutter, og når det lykkes, vises enheden som **Klar til bruger**. **Klar til bruger betyder** , at den er klar og venter på, at en bruger begynder at bruge den.

> [!NOTE]
> Hvis du manuelt ændrer Azure Active Directory(AAD)-gruppemedlemskab til en enhed, tildeles den automatisk gruppen til dens enhedsprofil og fjernes fra eventuelle grupper, der er i konflikt med hinanden.

Du kan overvåge status for enhedsregistrering på hovedsiden. Mulige rapporterede tilstande omfatter:

| Stat | Beskrivelse |
| ----- | ----- |
| Afventer registrering | Registreringen er ikke fuldført endnu. Kontrollér igen senere. |
| Registrering mislykkedes | Registreringen kunne ikke fuldføres. Du kan finde flere oplysninger under [Fejlfinding af enhedsregistrering](#troubleshooting-device-registration). |
| Klar til brug | Registreringen lykkedes. Enheden er nu klar til at blive leveret til brugeren. Microsoft Managed Desktop vejleder dem gennem første opsætning, så du behøver ikke at gøre yderligere forberedelser. |
| Aktiv | Enheden er blevet leveret til brugeren, og brugeren er registreret hos din lejer. Denne tilstand angiver også, at de regelmæssigt bruger enheden. |
| Inaktiv | Enheden er blevet leveret til brugeren, og brugeren er registreret hos din lejer. Men brugeren har ikke brugt enheden for nylig (inden for de seneste syv dage). |

### <a name="troubleshooting-device-registration"></a>Fejlfinding af enhedsregistrering

| Fejlmeddelelse | Detaljer |
| ----- | ----- |
| Enheden blev ikke fundet | Vi kunne ikke registrere denne enhed, fordi vi ikke kunne finde et match for den angivne producent, model eller serienummer. Bekræft disse værdier med din enhedsleverandør. |
| Hardwarehash er ugyldig | Den hardware-hash, du anede til denne enhed, var ikke formateret korrekt. Dobbelttjek hardwarehash'en, og send den igen. |
| Enheden er allerede registreret | Denne enhed er allerede registreret for organisationen. Der kræves ingen yderligere handling. |
| Enhed, der er påstået af en anden organisation | Denne enhed er allerede blevet påstået af en anden organisation. Kontakt enhedsleverandøren. |
| Uventet fejl | Din anmodning kunne ikke behandles automatisk. Kontakt support, og angiv anmodnings-id'et: `<requestId>` |

## <a name="check-the-image"></a>Kontrollér billedet

Hvis din enhed er taget fra en Microsoft Managed Desktop-partnerleverandør, skal billedet være korrekt.

Du er også velkommen til at anvende billedet selv, hvis du foretrækker det. For at komme i gang skal du kontakte den Microsoft-repræsentant, du arbejder med, og de giver dig en placering og trin til at anvende billedet.

## <a name="deliver-the-device"></a>Levyd enheden

> [!IMPORTANT]
> Før du udleverer enheden til brugeren, skal du kontrollere, at du har fået og anvendt [de relevante licenser](../get-ready/prerequisites.md) for den pågældende bruger.

Hvis alle licenserne er anvendt, kan du [gøre dine brugere klar til at bruge enhederne](get-started-devices.md). Derefter kan brugeren starte enheden og fortsætte Windows konfigurationen.
