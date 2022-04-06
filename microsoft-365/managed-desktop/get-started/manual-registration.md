---
title: Manuel registrering
description: Registrer enheder, der skal administreres af Microsoft Managed Desktop
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
ms.openlocfilehash: aaa1446cbb1ffdc20b023f568a7fd41d6cf01848
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63704955"
---
# <a name="manual-registration"></a>Manuel registrering

Microsoft-administreret skrivebord kan fungere med helt nye enheder, eller du kan genbruge enheder, som du måske allerede har. Hvis du genbruger enheder, skal du animere dem igen. Du kan registrere enheder med Microsoft Managed Desktop i Microsoft Endpoint Manager portal.

> [!NOTE]
> Arbejder du sammen med en partner om at hente enheder? Hvis det er ja, behøver du ikke at bekymre dig om at få hardwarehashes; det tager de sig af for dig. Sørg for, at din partner etablerer en relation til dig i [Partnercenter](https://partner.microsoft.com/dashboard). Din partner kan få mere at vide [under Hjælp til Partnercenter](/partner-center/request-a-relationship-with-a-customer). <br><br>Når denne relation er etableret, vil din partner blot registrere enheder på dine vegne – der kræves ikke yderligere handling fra dig. Hvis du vil se oplysningerne, eller din partner har spørgsmål, skal du se [Partnerregistrering](partner-registration.md). Når enhederne er registreret, kan du fortsætte [med at kontrollere](#check-the-image) billedet [og levere enhederne](#deliver-the-device) til dine brugere.

## <a name="prepare-to-register-brand-new-devices"></a>Forbered dig på at registrere helt nye enheder

Når du har de nye enheder ved hånden, skal du følge disse trin:

1. [Hent hardware-hash'en for hver enhed.](#obtain-the-hardware-hash)
2. [Flet hash-dataene](#merge-hash-data).
3. [Registrer enhederne i Microsoft Managed Desktop](#register-devices-by-using-the-admin-portal).
4. [Kontrollér, at billedet er korrekt.](#check-the-image)
5. [Lever enheden](#deliver-the-device).

### <a name="obtain-the-hardware-hash"></a>Hent hardwarehash'en

Microsoft Managed Desktop identificerer hver enhed entydigt ved at referere til dens hardwarehash. Du har tre muligheder for at hente disse oplysninger.

**Sådan får du hardwarehash'en:**

- Spørg din OEM-leverandør om AutoPilot-registreringsfilen, som vil indeholde hardwarehashes.
- Kør et [Windows PowerShell på](#powershell-script-method) hver enhed, og indsaml resultaterne i en fil.
- Start hver enhed, men fuldfør ikke konfigurationen Windows, og [indsaml hashes på et flytbart flashdrev](#flash-drive-method).

#### <a name="powershell-script-method"></a>PowerShell-scriptmetode

Du kan [ brugeGet-WindowsAutoPilotInfo.ps1](https://www.powershellgallery.com/packages/Get-WindowsAutoPilotInfo) PowerShell-scriptet på webstedet for PowerShell-galleriet. Du kan finde flere oplysninger om enhedsidentifikation og hardwarehash [under Føj enheder til Windows Autopilot](/mem/autopilot/add-devices#device-identification).

**Sådan bruges Powershell-scriptmetoden:**

1. Åbn en PowerShell-meddelelse med administrative rettigheder.
2. Kør `Install-Script -Name Get-WindowsAutoPilotInfo`.
3. Kør `powershell -ExecutionPolicy Unrestricted Get-WindowsAutoPilotInfo -OutputFile <path>\hardwarehash.csv`.
4. Kør `powershell -ExecutionPolicy restricted` for at forhindre efterfølgende ikke-tilstløbende scripts.

#### <a name="flash-drive-method"></a>Flashdrevmetode

**Sådan bruger du flashdrevmetoden:**

1. Indsæt et USB-drev på en anden enhed end den, du er ved at registrere.
2. Åbn en PowerShell-meddelelse med administrative rettigheder.
3. Kør `Save-Script -Name Get-WindowsAutoPilotInfo -Path <pathToUsb>`
4. Slå den enhed, du registrerer, til, *men start ikke konfigurationsoplevelsen*. Hvis du ved et uheld kommer til at starte konfigurationen, er du nødt til at nulstille eller animere enheden.
5. Indsæt USB-drevet, og tryk derefter på Shift + F10.
6. Åbn en PowerShell-prompt med administrative rettigheder, og kør derefter `cd <pathToUsb>`.
7. Kør `Set-ExecutionPolicy -ExecutionPolicy Unrestricted`
8. Kør `.\Get-WindowsAutoPilotInfo -OutputFile <path>\hardwarehash.csv`
9. Fjern USB-drevet, og luk enheden ved at køre `shutdown -s -t 0`

> [!IMPORTANT]
> Tænd ikke for den enhed, du tilmelder dig igen, før du har fuldført tilmeldingen til den.

### <a name="merge-hash-data"></a>Flet hash-data

Du skal have dataene i CSV-filerne kombineret i en enkelt fil for at fuldføre registreringen. Her er et eksempel på et PowerShell-script, der gør det nemt:

`Import-CSV -Path (Get-ChildItem -Filter *.csv) | ConvertTo-Csv -NoTypeInformation | % {$_.Replace('"', '')} | Out-File .\aggregatedDevices.csv`

> [!NOTE]
> Ekstra kolonner understøttes ikke. Tilbud understøttes ikke. Det er kun tekstfiler i ANSI-format, der kan bruges (ikke Unicode). Der er store og små bogstaver i sidehoveder. Når du redigerer filen Excel filen og gemmer den som en CSV-fil, genereres der ikke en brugbar fil på grund af disse krav. Sørg for at bevare eventuelle foranstillede nuller i enhedens serienumre.

### <a name="register-devices-by-using-the-admin-portal"></a>Registrere enheder ved hjælp af administrationsportalen

I [Microsoft Endpoint Manager](https://endpoint.microsoft.com/) du vælge **Enheder** i venstre navigationsrude. I sektionen Microsoft Managed Desktop skal du vælge **Enheder**. I arbejdsområdet Microsoft-administrerede stationære enheder skal **du vælge + Registrer** enheder, som åbner et pop op-vindue for at registrere nye enheder.

<!-- [![Fly-in after selecting Register devices, listing devices with columns for assigned users, serial number, status, last-seen date, and age.](../../media/new-registration-ui.png)](../../media/new-registration-ui.png) -->

<!--Registering any existing devices with Managed Desktop will completely re-image them; make sure you've backed up any important data prior to starting the registration process.-->

**Sådan registrerer du enheder ved hjælp af administrationsportalen:**

1. Angiv **en sti til** den CSV-fil, du oprettede tidligere, under Filoverførsel.
2. Vælg [en enhedsprofil](../service-description/profiles.md) i rullemenuen.
3. Vælg **Registrer enheder**. Systemet føjer enhederne til din liste over enheder på enheder **, der er** markeret som **Registrering afventer**. Registrering tager typisk under 10 minutter, og når det lykkes, vises enheden som Klar til  bruger, hvilket betyder, at den er klar og venter på, at en bruger begynder at bruge den.

> [!NOTE]
> Hvis du manuelt ændrer Azure Active Directory(AAD)-gruppemedlemskab til en enhed, tildeles den automatisk gruppen til dens enhedsprofil og fjernes fra eventuelle grupper, der er i konflikt med hinanden.

Du kan overvåge status for enhedsregistrering på hovedsiden. Mulige rapporterede tilstande omfatter:

| Stat | Beskrivelse |
| -----|-----|
| Afventer registrering | Registreringen er ikke fuldført endnu. Kontrollér igen senere. |
| Registrering mislykkedes | Registreringen kunne ikke fuldføres. Du kan finde flere oplysninger under [Fejlfinding af enhedsregistrering](#troubleshooting-device-registration). |
| Klar til brug | Registreringen lykkedes. Enheden er nu klar til at blive leveret til brugeren. Microsoft Managed Desktop vejleder dem gennem første opsætning, så du behøver ikke at gøre yderligere forberedelser. |
| Aktiv | Enheden er blevet leveret til brugeren, og brugeren er registreret hos din lejer. Denne tilstand angiver også, at de regelmæssigt bruger enheden. |
| Inaktiv | Enheden er blevet leveret til brugeren, og brugeren er registreret hos din lejer. De har dog ikke brugt enheden for nylig (inden for de seneste syv dage).  |

#### <a name="troubleshooting-device-registration"></a>Fejlfinding af enhedsregistrering

| Fejlmeddelelse | Detaljer |
|-----| ----- |
| Enheden blev ikke fundet | Vi kunne ikke registrere denne enhed, fordi vi ikke kunne finde et match for den angivne producent, model eller serienummer. Bekræft disse værdier med din enhedsleverandør. |
| Hardwarehash er ugyldig | Den hardware-hash, du anede til denne enhed, var ikke formateret korrekt. Dobbelttjek hardwarehash'en, og send den igen. |
| Enheden er allerede registreret | Denne enhed er allerede registreret for organisationen. Der kræves ingen yderligere handling. |
| Enhed, der er påstået af en anden organisation | Denne enhed er allerede blevet påstået af en anden organisation. Kontakt enhedsleverandøren. |
| Uventet fejl | Din anmodning kunne ikke behandles automatisk. Kontakt support, og angiv anmodnings-id'et: `<requestId>` |

### <a name="check-the-image"></a>Kontrollér billedet

Hvis din enhed er taget fra en Microsoft Managed Desktop-partnerleverandør, skal billedet være korrekt.

Du er også velkommen til at anvende billedet selv, hvis du foretrækker det. For at komme i gang skal du kontakte den Microsoft-repræsentant, du arbejder sammen med. Repræsentanten vil give dig placeringen og trinene til at anvende billedet.

### <a name="autopilot-group-tag"></a>Autopilot-gruppemærke

Når du bruger administrationsportalen til at registrere enheder, tildeler vi automatisk Autopilot-gruppemærket, der er knyttet til den enhedsprofil, der er angivet i Registrer enheder ved [hjælp af Partnercenter](partner-registration.md).
Tjenesten overvåger dagligt alle Microsoft-administrerede stationære computere og tildeler gruppemærket til nogen, der ikke allerede har den.

### <a name="deliver-the-device"></a>Levyd enheden

> [!IMPORTANT]
> Før du udleverer enheden til brugeren, skal du kontrollere, at du har fået og anvendt [de relevante licenser](../get-ready/prerequisites.md) for den pågældende bruger.

Hvis alle licenserne er anvendt, kan du [gøre dine brugere klar til at bruge enheder](get-started-devices.md). Derefter kan brugeren starte enheden og fortsætte Windows konfigurationen.
