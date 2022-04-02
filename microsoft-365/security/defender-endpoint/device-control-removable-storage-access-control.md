---
title: Microsoft Defender for Endpoint flytbare eller flytbare lagringsmedier Storage Access Control enhedsstyring
description: En gennemgang af Microsoft Defender for Endpoint
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.custom: admindeeplinkDEFENDER
ms.topic: conceptual
ms.technology: mde
ms.date: 03/18/2022
ms.openlocfilehash: 3b3e01fd0d205182f7d028e2170cc00ebb6f780e
ms.sourcegitcommit: a4729532278de62f80f2160825d446f6ecd36995
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/31/2022
ms.locfileid: "64568066"
---
# <a name="microsoft-defender-for-endpoint-device-control-removable-storage-access-control"></a>Microsoft Defender for Endpoint Flytbare enhedsstyrings-Storage Access Control

**Gælder for:**
- [Microsoft Defender for Endpoint plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> [!NOTE]
> Administration Gruppepolitik og Intune OMA-URI/Brugerdefineret politikstyring for dette produkt er nu generelt tilgængelig (4.18.2106): Se [Tech Community-blog: Beskyt](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/protect-your-removable-storage-and-printers-with-microsoft/ba-p/2324806) dit flytbare lager og din printer med Microsoft Defender for Endpoint.


Microsoft Defender for Endpoint Flytbare Enhedshåndteringsenhed Storage Access Control gør det muligt at udføre følgende opgave:

- overvågning, tillade eller forhindre læse-, skrive- eller eksekveringsadgang til flytbart lager med eller uden udelukkelse

|Rettighed|Tilladelse|
|---|---|
|Access|Læse, skrive, udføre|
|Handlingstilstand|Overvågning, Tillad, Forebyd|
|CSP-support|Ja|
|Understøttelse af gruppepolitikobjekt|Ja|
|Brugerbaseret support|Ja|
|Computerbaseret support|Ja|

|Funktion|Beskrivelse|Installér via Intune|Installér via Gruppepolitik|
|---|---|---|---|
|Oprettelse af flytbare mediegrupper|Giver dig mulighed for at oprette flytbare mediegrupper|Trin 1 i sektionen [Installationspolitik via OMA-URI](#deploying-policy-via-oma-uri) | Trin 1 i afsnittet [Installationspolitik via Gruppepolitik](#deploying-policy-via-group-policy)|
|Oprettelse af politik|Giver dig mulighed for at oprette en politik for at håndhæve hver flytbare mediegruppe|Trin 2 i afsnittet [Installationspolitik via OMA-URI](#deploying-policy-via-oma-uri) | Trin 2 og 3 i sektionen [Installationspolitik via Gruppepolitik](#deploying-policy-via-group-policy) |
|Standardhåndhævelse|Giver dig mulighed for at angive standardadgang (Afvisning eller Tillad) til flytbare medier, hvis der ikke er nogen politik|Trin 3 i afsnittet [Installationspolitik via OMA-URI](#deploying-policy-via-oma-uri) | Trin 4 i afsnittet [Installationspolitik via Gruppepolitik](#deploying-policy-via-group-policy) |
|Aktivér eller deaktiver Flytbare Storage Access Control|Hvis du indstiller Deaktiver, deaktiverer den politikken flytbare Storage Access Control på denne computer| Trin 4 i afsnittet [Installationspolitik via OMA-URI](#deploying-policy-via-oma-uri) | Trin 5 i afsnittet [Installationspolitik via Gruppepolitik](#deploying-policy-via-group-policy) |
|Hente filoplysninger|Gør det muligt at oprette en politik for hentning af filoplysninger, når der sker skriveadgang| Trin 2 og 5 i sektionen [Implementeringspolitik via OMA-URI](#deploying-policy-via-oma-uri) | Trin 2 og 6 i sektionen [Installationspolitik via Gruppepolitik](#deploying-policy-via-group-policy) |

## <a name="prepare-your-endpoints"></a>Forbered dine slutpunkter

Installér Flytbare Storage Access Control på Windows 10 og Windows 11-enheder, der har antimalwareklientversion **4.18.2103.3 eller nyere**.

- **4.18.2104** eller nyere: Tilføj SerialNumberId, VID_PID, filpath-baseret understøttelse af gruppepolitikobjekt, ComputerSid

- **4.18.2105** eller nyere: Tilføj understøttelse af jokertegn for HardwareId/DeviceId/InstancePathId/FriendlyNameId/SerialNumberId, kombinationen af en bestemt bruger på en bestemt computer, understøttelse af SSD (en SanDisk Extreme SSD)/USB-tilsluttet SCSI (UAS)

- **4.18.2107** eller nyere: Tilføj Windows WPD-understøttelse (til mobilenheder, f.eks. tablets); Tilføj AccountName til avanceret [jagt](device-control-removable-storage-access-control.md#view-device-control-removable-storage-access-control-data-in-microsoft-defender-for-endpoint)

:::image type="content" source="images/powershell.png" alt-text="Brugergrænsefladen i PowerShell" lightbox="images/powershell.png":::

> [!NOTE]
> Ingen af Windows Sikkerhed komponenter skal være aktive, da du kan køre Flytbare Storage Access Control af Windows Sikkerhed status.

## <a name="policy-properties"></a>Egenskaber for politik

Du kan bruge følgende egenskaber til at oprette en flytbar lagergruppe:

> [!NOTE]
> Kommentarer, der bruger XML-kommentar notation `<!-- COMMENT -->` , kan bruges i regel- og gruppe XML-filer, men de skal være i den første XML-kode, ikke den første linje i XML-filen.

### <a name="removable-storage-group"></a>Flytbar Storage gruppe

|Egenskabsnavn|Beskrivelse|Indstillinger|
|---|---|---|
|**Gruppe-id**|GUID, et entydigt id, repræsenterer gruppen og bruges i politikken som Gruppe-id||
|**DescriptorIdList**|Vis en liste over de enhedsegenskaber, du vil bruge til at dække i gruppen. For hver enhedsegenskab skal du [se Enhedsegenskaber](device-control-removable-storage-protection.md) for at få flere oplysninger. Der er store og små bogstaver i alle egenskaber. |**PrimaryId**: `RemovableMediaDevices`, , `CdRomDevices``WpdDevices`<p>**BusId**: F.eks. USB, SCSI<p>**DeviceId**<p>**HardwareId**<p>**InstancePathId**: InstancePathId er en streng, der entydigt identificerer enheden i systemet, f.eks `USBSTOR\DISK&VEN_GENERIC&PROD_FLASH_DISK&REV_8.07\8735B611&0`. . Tallet i slutningen (f.eks. &0) repræsenterer det tilgængelige slot og kan skifte fra enhed til enhed. Du opnår de bedste resultater ved at bruge et jokertegn i slutningen. F.eks. `USBSTOR\DISK&VEN_GENERIC&PROD_FLASH_DISK&REV_8.07\8735B611*`.<p>**FriendlyNameId**<p>**SerialNumberId**<p>**VID**<p>**PID**<p>**VID_PID**<p>`0751_55E0`: matcher dette nøjagtige VID/PID-par<p>`_55E0`: match et medie med PID=55E0 <p>`0751_`: match et hvilket som helst medie med VID=0751|
|**MatchType**|Når der bruges flere enhedsegenskaber i , definerer `DescriptorIDList`MatchType relationen.|**MatchAll**: Alle attributter under `DescriptorIdList` skal være And-relationen. Hvis f.eks. administrator `InstancePathID` `DeviceID` placerer og – for hvert forbundet USB-drev – kontrollerer systemet, om USB-drevet opfylder begge værdier. <p> **MatchAny**: Attributterne under DescriptorIdList er **Or-relationen** ; Hvis f.eks. administrator `DeviceID` `InstancePathID`placerer og , for hver forbundet USB, vil systemet udføre håndhævelsen, så længe USB-drevet har enten en identisk Værdi for **DeviceID** eller **InstanceID** . |

### <a name="access-control-policy"></a>Access Control politik

| Egenskabsnavn | Beskrivelse | Indstillinger |
|---|---|---|
| **PolicyRule-id** | GUID, et entydigt id, repræsenterer politikken og bruges til rapportering og fejlfinding. | |
| **IncludedIdList** | Den eller de grupper, som politikken anvendes på. Hvis der tilføjes flere grupper, anvendes politikken på alle medier i alle disse grupper.|Gruppe-id/GUID skal bruges i denne forekomst. <p> I følgende eksempel vises brugen af GroupID: <p> `<IncludedIdList> <GroupId> {EAA4CCE5-F6C9-4760-8BAD-FDCC76A2ACA1}</GroupId> </IncludedIdList>` |
| **ExcludedIDList** | Den eller de grupper, som politikken ikke anvendes på. | Gruppe-id/GUID skal bruges i denne forekomst. |
| **Indtastnings-id** | Én Politikregel kan have flere poster. hver post med et entydigt GUID fortæller Enhedskontrol én begrænsning.| |
| **Type** | Definerer handlingen for de flytbare lagringsgrupper i IncludedIDList. <p>Håndhævelse: Tillad eller afvisning <p>Overvågning: AuditAllowed eller AuditDenied<p> | Tillad<p>Afvisning <p>AuditAllowed: Definerer meddelelse og hændelse, når adgang er tilladt <p>AuditDenied: Definerer meddelelse og hændelse, når adgang nægtet; skal arbejde sammen med **posten Afvisning** .<p> Når der er konflikttyper for det samme medie, anvender systemet den første i politikken. Et eksempel på en konflikttype er **Tillad** **og Afvis**. |
| **Sid** | Den lokale bruger Sid eller bruger Sid-gruppen eller SID i AD-objektet definerer, om denne politik skal anvendes på en bestemt bruger eller brugergruppe. én post kan maksimalt have ét Sid, og en post uden sid betyder at anvende politikken over computeren. |  |
| **ComputerSid** | Den lokale computers Sid- eller computer-Sid-gruppe eller SID for AD-objektet definerer, om denne politik skal anvendes på en bestemt computer eller computergruppe. En post kan maksimalt have én ComputerSid, og en post uden nogen ComputerSid betyder at anvende politikken over computeren. Hvis du vil anvende en post på en bestemt bruger og en bestemt computer, skal du tilføje både Sid og ComputerSid i samme Post. |  |
| **Indstillinger** | Definerer, om meddelelser skal vises eller ej |**Når Type Tillad er markeret**: <p>0: intet<p>4: **Deaktiver AuditAllowed** og **AuditDenied** for denne post. Selvom **Tillad sker** , og indstillingen Tilladt Overvågning er konfigureret, sender systemet ikke hændelse. <p>8: registrerer filoplysninger og har en kopi af filen som bevis for skriveadgang. <p>16: hente filoplysninger for skriveadgang. <p>**Når Type Afvisning er markeret**: <p>0: intet<p>4: **Deaktiver AuditDenied** for denne post. Selvom **Bloker** sker, og AuditDenied er konfigureret, vises der ikke en meddelelse i systemet. <p>**Når Type **AuditAllowed** er valgt**: <p>0: intet <p>1: intet <p>2: Send begivenhed<p>3: Send begivenhed <p> **Når Type **AuditDenied** er valgt**: <p>0: intet <p>1: vis meddelelse <p>2: Send begivenhed<p>3: Vis meddelelse og send hændelse |
|AccessMask|Definerer adgangen. | **Adgang på diskniveau**: <p>1: Læs <p>2: Skriv <p>4: Udfør <p>**Adgang på filsystemniveau**: <p>8: Læsning af filsystem <p>16: File system Write <p>32: Filsystem Udfør <p><p>Du kan have flere adgang ved at udføre en binær ELLER-handling, f.eks. bliver AccessMask for Læs og Skriv og Udfør 7; AccessMasken for læs og skriv bliver 3.|

## <a name="common-removable-storage-access-control-scenarios"></a>Almindelige flytbare Storage Access Control scenarier

For at gøre dig bekendt med Microsoft Defender for Endpoint Flytbare Storage Access Control har vi samlet nogle almindelige scenarier, som du kan følge.

### <a name="scenario-1-prevent-write-and-execute-access-to-all-but-allow-specific-approved-usbs"></a>Scenarie 1: Undgå skrive- og kørselsadgang til alle, men tillade bestemte godkendte usbs

1. Opret grupper

    1. Gruppe 1: Flytbart lager og cd/dvd. Et eksempel på et flytbart lager og en cd/dvd er: Gruppe **9b28fae8-72f7-4267-a1a5-685f747a7146** i eksemplet Alle flytbare Storage- og [cd-dvd-Group.xml-filer](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples).

    2. Gruppe 2: Godkendte USBs baseret på enhedsegenskaber. Et eksempel på denne use case er: **Forekomst-id - Gruppe 65fa649a-a111-4912-9294-fb6337a25038** i eksemplet [Godkendte USBs Group.xml-fil](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) .

    > [!TIP]
    > Erstat `&` med `&amp;` i værdien.

2. Opret politik

    1. Politik 1: Bloker skrive- og eksekver adgang, men tillad godkendte USBs. Et eksempel på dette use case er: PolicyRule **c544a991-5786-4402-949e-a032cb790d0e** i eksempelscenarie 1 Bloker skriv og Eksekver Access, men tillad godkendt [USBs.xml-fil](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) .

    2. Politik 2: Overvågningss write and Execute access to allowed USBs. Et eksempel på denne use case er: PolicyRule **36ae1037-a639-4cff-946b-b36c53089a4c** i eksempelscenarie 1 Overvågningsskrivning og Udfør adgang til godkendt [USBs.xml-fil](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) .

### <a name="scenario-2-audit-write-and-execute-access-to-all-but-block-specific-unapproved-usbs"></a>Scenarie 2: Overvåge skrive- og udføre adgang for alle, men blokere bestemte ikke-godkendte USB'er

1. Opret grupper

    1. Gruppe 1: Flytbart lager og cd/dvd. Et eksempel på dette use case er: Gruppe **9b28fae8-72f7-4267-a1a5-685f747a7146** i eksemplet Alle flytbare Storage- og [cd-dvd-Group.xml-filer](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples).

    2. Gruppe 2: Ikke-godkendte USB'er baseret på enhedsegenskaber, f.eks. leverandør-id/produkt-id, brugervenligt navn – Gruppe **65fa649a-a111-4912-9294-fb6337a25038** i eksemplet Ikke-godkendte [USBs Group.xml-fil](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) .

    > [!TIP]
    > Erstat `&` med `&amp;` i værdien.

2. Opret politik

    1. Politik 1: Bloker skrive- og eksekver adgang til alle, men bloker bestemte ikke-godkendte USB'er. Et eksempel på denne use case er: PolicyRule **23b8e437-66ac-4b32-b3d7-24044637fc98** i eksempelscenarie 2 Overvågningsskrivning og Udfør adgang til alle, men blokere bestemte [ikke-USBs.xml-filer](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) .

    2. Politik 2: Overvåge skrive- og udføre adgang for andre. Et eksempel på denne use case er: PolicyRule **b58ab853-9a6f-405c-a194-740e69422b48** i eksempelscenarie 2 Overvågningsskrivning og Udfør adgang [til others.xml-fil](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) .

## <a name="deploying-and-managing-policy-via-group-policy"></a>Implementering og administration af politik via Gruppepolitik

Funktionen Flytbare Storage Access Control gør det muligt at anvende politikken via Gruppepolitik på enten bruger eller enhed eller begge dele.

### <a name="licensing"></a>Licensering

Før du går i gang med Flytbare Storage Access Control, skal du bekræfte dit [Microsoft 365 abonnement](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=2). For at få adgang til og bruge Flytbare Storage Access Control, skal du have Microsoft 365 E3 eller Microsoft 365 E5.

### <a name="deploying-policy-via-group-policy"></a>Implementeringspolitik via Gruppepolitik

1. Kombiner alle grupper i `<Groups>` `</Groups>` én XML-fil.

    Følgende billede illustrerer eksemplet med Scenarie 1: Undgå skrive- og [kørselsadgang til alle, men tillade bestemte godkendte usbs](#scenario-1-prevent-write-and-execute-access-to-all-but-allow-specific-approved-usbs).

    :::image type="content" source="images/prevent-write-access-allow-usb.png" alt-text="De konfigurationsindstillinger, der tillader bestemte godkendte USB'er på enheder" lightbox="images/prevent-write-access-allow-usb.png":::

2. Kombiner alle regler i `<PolicyRules>` `</PolicyRules>` én XML-fil.

    Hvis du vil begrænse en bestemt bruger, skal du bruge SID-egenskaben i Posten. Hvis der ikke er noget SID i politikken Indtastning, anvendes posten på alle logonforekomster for computeren.
    
    Hvis du vil overvåge filoplysninger for skriveadgang, skal du bruge den højre AccessMask med den rigtige indstilling (16); her er eksemplet med [Registrer filoplysninger](https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/Group%20Policy/Audit%20File%20Information.xml).

    Følgende billede illustrerer brugen af SID-egenskab og et eksempel på Scenarie 1: Undgå skrive- og kørselsadgang til alle, men tillade bestemte [godkendte usbs](#scenario-1-prevent-write-and-execute-access-to-all-but-allow-specific-approved-usbs).

    :::image type="content" source="images/usage-sid-property.png" alt-text="Den kode, der angiver brugen af ATTRIBUTten SID-egenskab" lightbox="images/usage-sid-property.png":::

3. Gem både regel- og gruppe XML-filer på netværkssharemappen, og sæt stien til netværkssharemappen ind i Gruppepolitik-indstillingen: **Administrative** \>  \> skabeloner til computerkonfiguration **Windows Komponenter** \> **Microsoft Defender Antivirus** \> **Enhedsstyring**: **'Definer politikgrupper for enhedsstyring'** **og 'Definer politikregler for enhedsstyring'**.

   Hvis du ikke kan finde politikkonfigurationen for brugeroplevelse i Gruppepolitik, kan du hente filerne [WindowsDefender.adml](https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/WindowsDefender.adml) og [WindowsDefender.admx](https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/WindowsDefender.admx) ved at vælge **Raw** og derefter **Gem som**.

   - Destinationscomputeren skal kunne få adgang til netværkssharen for at have politikken. Men når politikken er læst, er netværksshareforbindelsen ikke længere påkrævet, selv efter computeren er genstartet.

    :::image type="content" source="images/device-control.png" alt-text="Skærmbilledet Enhedshåndtering" lightbox="images/device-control.png":::

4. Standard håndhævelse: Giver dig mulighed for at angive standardadgang (Afvisning eller Tillad) til flytbare medier, hvis der ikke er nogen politik. Hvis du f.eks. kun har en politik (enten Deny eller Allow) for FlytbareMediaDevices, men du ikke har nogen politik for CdRomDevices eller WpdDevices, og du angiver standard afvisningen via denne politik, blokeres adgangen til Read/Write/Execute til CdRomDevices eller WpdDevices.

   - Når du har udrullet denne indstilling, får du **vist Tillad** som **standard eller Standard afvisning**.
   - Overvej både Diskniveau og Filsystemniveau AccessMask, når du konfigurerer denne indstilling, hvis du f.eks. vil Standardafvisning, men tillade bestemt lagerplads, skal du tillade adgang på både diskniveau og filsystemniveau, du skal angive AccessMask til 63.

    :::image type="content" source="images/148609579-a7df650b-7792-4085-b552-500b28a35885.png" alt-text="Standardkode for Tillad eller Standard afvisning af PowerShell":::

5. Aktivér eller deaktiver Flytbare Storage Access Control: Du kan indstille denne værdi til midlertidigt at deaktivere Flytbare Storage Access Control.

    :::image type="content" source="images/148608318-5cda043d-b996-4146-9642-14fccabcb017.png" alt-text="Indstillinger for Enhedsstyring":::

   - Når du installerer denne indstilling, får du vist **Aktiveret** eller **Deaktiveret**. Deaktiveret betyder, at denne computer ikke har flytbare Storage Access Control politik kørende.

    :::image type="content" source="images/148609685-4c05f002-5cbe-4aab-9245-83e730c5449e.png" alt-text="Aktiveret eller deaktiveret enhedsstyring i PowerShell-kode":::

6. Angiv placering for en kopi af filen: Hvis du vil have en kopi af filen, når der sker skriveadgang, skal du angive den placering, hvor systemet kan gemme kopien.
    
    Installer dette sammen med den rette AccessMask og Indstilling – se trin 2 ovenfor.

    :::image type="content" source="../../media/define-device-control-policy-rules.png" alt-text="Gruppepolitik – Angiv locaiton for fil beviser":::

## <a name="deploying-and-managing-policy-via-intune-oma-uri"></a>Implementering og administration af politik via Intune OMA-URI

Funktionen Flytbare Storage Access Control gør det muligt at anvende politik via OMA-URI på enten bruger eller enhed eller begge dele.

### <a name="licensing-requirements"></a>Licenskrav

Før du går i gang med Flytbare Storage Access Control, skal du bekræfte dit [Microsoft 365 abonnement](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=2). For at få adgang til og bruge Flytbare Storage Access Control, skal du have Microsoft 365 E3 eller Microsoft 365 E5.

### <a name="permission"></a>Tilladelse

I forbindelse med udrulning af Intune skal kontoen have tilladelse til at oprette, redigere, opdatere eller slette enhedskonfigurationsprofiler. Du kan oprette brugerdefinerede roller eller bruge en af de indbyggede roller med disse tilladelser.

- Politik og profilstyringsrolle

- Brugerdefineret rolle med tilladelsen Opret/Rediger/Opdater/Læs/Slet/Vis rapporter aktiveret for Enhedskonfigurationsprofiler

- Global administrator

### <a name="deploying-policy-via-oma-uri"></a>Implementeringspolitik via OMA-URI

Microsoft Endpoint Manager Administration (<https://endpoint.microsoft.com/>) **EnhederKonfigurationsprofiler** \>  \> \> Opret **profilplatform** \> **: Windows 10 senere & Profil: Brugerdefineret**

1. Opret en OMA-URI-regel for hver gruppe:

    - OMA-URI:

      `./Vendor/MSFT/Defender/Configuration/DeviceControl/PolicyGroups/%7b**GroupGUID**%7d/GroupData`

      For flytbare **lagrings- og cd-/dvd-grupper** i stikprøven skal linket f.eks. være:

      `./Vendor/MSFT/Defender/Configuration/DeviceControl/PolicyGroups/%7b9b28fae8-72f7-4267-a1a5-685f747a7146%7d/GroupData`

    - Datatype: Streng (XML-fil)

      :::image type="content" source="images/xml-data-type-string.png" alt-text="Feltet Datatype på siden Tilføj række" lightbox="images/xml-data-type-string.png":::

2. For hver politik skal du også oprette en OMA-URI:

    - OMA-URI:

      `./Vendor/MSFT/Defender/Configuration/DeviceControl/PolicyRules/%7b**PolicyRuleGUID**%7d/RuleData`

      For eksempel skal linket for **reglen Bloker skriv og eksekvering af Access, men tillade godkendte USBs-reglen** i eksemplet være:

      `./Vendor/MSFT/Defender/Configuration/DeviceControl/PolicyRules/%7bc544a991-5786-4402-949e-a032cb790d0e%7d/RuleData`

    - Datatype: Streng (XML-fil)
       
    Hvis du vil overvåge filoplysninger for skriveadgang, skal du bruge den højre AccessMask med den rigtige indstilling (16); her er eksemplet med [Registrer filoplysninger](https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/Intune%20OMA-URI/Audit%20File%20Information.xml).

3. Standard håndhævelse: Giver dig mulighed for at angive standardadgang (Afvisning eller Tillad) til flytbare medier, hvis der ikke er nogen politik. Hvis du f.eks. kun har en politik (enten Deny eller Allow) for FlytbareMediaDevices, men du ikke har nogen politik for CdRomDevices eller WpdDevices, og du angiver standard afvisningen via denne politik, blokeres adgangen til Read/Write/Execute til CdRomDevices eller WpdDevices.

    - OMA-URI: `./Vendor/MSFT/Defender/Configuration/DefaultEnforcement`

    - Datatype: Helt ind

      `DefaultEnforcementAllow = 1`
      `DefaultEnforcementDeny = 2`

    - Når du installerer denne indstilling, får du **vist Tillad som** standard **eller Standard afvisning**
    - Overvej både Diskniveau og Filsystemniveau AccessMask, når du konfigurerer denne indstilling, hvis du f.eks. vil Standardafvisning, men tillade bestemt lagerplads, skal du tillade adgang på både diskniveau og filsystemniveau, du skal angive AccessMask til 63.

    :::image type="content" source="images/148609590-c67cfab8-8e2c-49f8-be2b-96444e9dfc2c.png" alt-text="Standardhåndhævelsesreglerne for PowerShell-kode":::

4. Aktivér eller deaktiver Flytbare Storage Access Control: Du kan indstille denne værdi til midlertidigt at deaktivere Flytbare Storage Access Control.

   - OMA-URI: `./Vendor/MSFT/Defender/Configuration/DeviceControlEnabled`

   - Datatype: Helt ind `Disable: 0`
     `Enable: 1`

   - Når du installerer denne indstilling, får du vist **Aktiveret** eller **Deaktiveret**

    **Deaktiveret** betyder, at denne computer ikke har flytbare Storage Access Control der kører en politik

    :::image type="content" source="images/148609770-3e555883-f26f-45ab-9181-3fb1ff7a38ac.png" alt-text="Fjernbar Storage Access Control i PowerShell-kode":::

5. Angiv placeringen for en kopi af filen: Hvis du vil have en kopi af filen, når der sker skriveadgang, skal du angive den placering, hvor systemet kan gemme kopien.
    
    - OMA-URI: `./Vendor/MSFT/Defender/Configuration/DataDuplicationRemoteLocation;**username**;**password**`

    - Datatype: Streng
    
    Du skal installere dette sammen med den højre AccessMask og den rigtige Indstilling – se trin 2 ovenfor.

    :::image type="content" source="../../media/device-control-oma-uri-edit-row.png" alt-text="Angiv locaiton for fil beviser":::
    
## <a name="deploying-and-managing-policy-by-using-intune-user-interface"></a>Implementering og administration af politik ved hjælp Intune brugergrænsefladen

(*Kommer snart!*) Denne funktion er tilgængelig i Microsoft Endpoint Manager Administration (<https://endpoint.microsoft.com/>). Gå til **Endpoint** **SecurityAttack** >  Surface **ReductionCreate** >  Policy. Vælg **Platform: Windows 10 og senere med** **Profil: Enhedshåndtering**.

## <a name="view-device-control-removable-storage-access-control-data-in-microsoft-defender-for-endpoint"></a>Vis flytbare enhedsstyringsdata Storage Access Control i Microsoft Defender for Endpoint

Portalen [Microsoft 365 Defender viser](https://security.microsoft.com/advanced-hunting) hændelser, der er udløst af det flytbare enhedselement Storage Access Control. For at få Microsoft 365 adgang til sikkerhed skal du have følgende abonnement:

- Microsoft 365 til E5-rapportering

```kusto
//RemovableStoragePolicyTriggered: event triggered by Disk level enforcement
DeviceEvents
| where ActionType == "RemovableStoragePolicyTriggered"
| extend parsed=parse_json(AdditionalFields)
| extend RemovableStorageAccess = tostring(parsed.RemovableStorageAccess)
| extend RemovableStoragePolicyVerdict = tostring(parsed.RemovableStoragePolicyVerdict)
| extend MediaBusType = tostring(parsed.BusType)
| extend MediaClassGuid = tostring(parsed.ClassGuid)
| extend MediaClassName = tostring(parsed.ClassName)
| extend MediaDeviceId = tostring(parsed.DeviceId)
| extend MediaInstanceId = tostring(parsed.DeviceInstanceId)
| extend MediaName = tostring(parsed.MediaName)
| extend RemovableStoragePolicy = tostring(parsed.RemovableStoragePolicy)
| extend MediaProductId = tostring(parsed.ProductId)
| extend MediaVendorId = tostring(parsed.VendorId)
| extend MediaSerialNumber = tostring(parsed.SerialNumber)
|project Timestamp, DeviceId, DeviceName, InitiatingProcessAccountName, ActionType, RemovableStorageAccess, RemovableStoragePolicyVerdict, MediaBusType, MediaClassGuid, MediaClassName, MediaDeviceId, MediaInstanceId, MediaName, RemovableStoragePolicy, MediaProductId, MediaVendorId, MediaSerialNumber
| order by Timestamp desc
```

```kusto
//information of file written to removable storage 
DeviceEvents
| where ActionType contains "RemovableStorageFileEvent"
| extend parsed=parse_json(AdditionalFields)
| extend Policy = tostring(parsed.Policy) 
| extend PolicyRuleId = tostring(parsed.PolicyRuleId) 
| extend MediaClassName = tostring(parsed.ClassName)
| extend MediaInstanceId = tostring(parsed.InstanceId)
| extend MediaName = tostring(parsed.MediaName)
| extend MediaProductId = tostring(parsed.ProductId) 
| extend MediaVendorId = tostring(parsed.VendorId) 
| extend MediaSerialNumber = tostring(parsed.SerialNumber) 
| extend FileInformationOperation = tostring(parsed.DuplicatedOperation)
| extend FileEvidenceLocation = tostring(parsed.TargetFileLocation) 
| project Timestamp, DeviceId, DeviceName, InitiatingProcessAccountName, ActionType, Policy, PolicyRuleId, FileInformationOperation, MediaClassName, MediaInstanceId, MediaName, MediaProductId, MediaVendorId, MediaSerialNumber, FileName, FolderPath, FileSize, FileEvidenceLocation, AdditionalFields
| order by Timestamp desc
```
    
:::image type="content" source="images/block-removable-storage.png" alt-text="Skærmen viser blokeringen af det flytbare lager.":::


## <a name="frequently-asked-questions"></a>Ofte stillede spørgsmål


### <a name="how-to-generate-guid-for-group-idpolicyrule-identry-id"></a>Sådan genereres GUID for Gruppe-id/PolitikRegel-id/Post-id?

Du kan generere GUID via online-åben kildekode eller via PowerShell – [Sådan genererer du GUID via PowerShell](/powershell/module/microsoft.powershell.utility/new-guid?msclkid=c1398a25a6d911ec9c888875fa1f24f5&view=powershell-7.2)
    
![billede](https://user-images.githubusercontent.com/81826151/159046476-26ea0a21-8087-4f01-b8ae-5aa73b392d8f.png)
    
### <a name="what-is-the-removable-storage-media-limitation-for-the-maximum-number-of-usbs"></a>Hvad er begrænsningen på flytbare lagringsmedier for det maksimale antal USB'er?

Vi har valideret én USB-gruppe med 100.000 medier – op til 7 MB. Politikken fungerer både i Intune og gruppepolitikobjekt uden problemer med ydeevnen.

### <a name="why-does-the-policy-not-work"></a>Hvorfor virker politikken ikke?

1. Den mest almindelige årsag er, at der ikke er nogen [påkrævet antimalwareklientversion](/microsoft-365/security/defender-endpoint/device-control-removable-storage-access-control#prepare-your-endpoints).

2. En anden årsag kan være, at XML-filen ikke er formateret korrekt, f.eks. hvis den ikke bruger den korrekte markdown-formatering for tegnet "&" i XML-filen, eller teksteditoren kan tilføje et byterækkefølgemærke (HTML) 0xEF 0xBB 0xBF i starten af filerne, hvilket får XML-parsing til ikke at fungere. En enkel løsning er at downloade [eksempelfilen](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) (vælg **Rå** og derefter **Gem som**) og derefter opdatere.

3. Hvis du installerer og administrerer politikken via Gruppepolitik, skal du sørge for at kombinere alle PolicyRule i én XML-fil i en overordnet node kaldet PolicyRules og alle grupper i én XML-fil i en overordnet node ved navn Grupper. Hvis du administrerer gennem Intune, skal du beholde én PolicyRule one XML-fil, samme ting, én Gruppe en XML-fil.
    
Hvis det stadig ikke virker, kan du kontakte os og dele support cab ved at køre cmd med administrator: "%programfiles%\Windows Defender\MpCmdRun.exe" -GetFiles

### <a name="there-is-no-configuration-ux-for-define-device-control-policy-groups-and-define-device-control-policy-rules-on-my-group-policy"></a>Der er ingen konfigurations-UX for "Definer politikgrupper for enhedsstyring" og "Definer politikregler for enhedsstyring" på min Gruppepolitik

Vi kan ikke backporte Gruppepolitik-konfigurationen af UX, men du kan stadig få de relaterede adml- og admx-filer ved at klikke på 'Raw' og 'Gem som' i [WindowsDefender.adml](https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/WindowsDefender.adml)- og [WindowsDefender.admx-filerne](https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/WindowsDefender.admx).

### <a name="how-can-i-know-whether-the-latest-policy-has-been-deployed-to-the-target-machine"></a>Hvordan ved jeg, om den seneste politik er blevet installeret på destinationscomputeren?

Du kan køre "Get-MpComputerStatus" på PowerShell som administrator. Følgende værdi viser, om den seneste politik er blevet anvendt på destinationscomputeren.

:::image type="icon" source="images/148609885-bea388a9-c07d-47ef-b848-999d794d24b8.png" border="false":::

### <a name="how-can-i-know-which-machine-is-using-out-of-date-antimalware-client-version-in-the-organization"></a>Hvordan ved jeg, hvilken computer der bruger forældet antimalwareklientversion i organisationen?

Du kan bruge følgende forespørgsel til at få antimalwareklientversion på Microsoft 365-sikkerhedsportalen:

```kusto
//check the antimalware client version
DeviceFileEvents
|where FileName == "MsMpEng.exe"
|where FolderPath contains @"C:\ProgramData\Microsoft\Windows Defender\Platform\"
|extend PlatformVersion=tostring(split(FolderPath, "\\", 5))
//|project DeviceName, PlatformVersion // check which machine is using legacy platformVersion
|summarize dcount(DeviceName) by PlatformVersion // check how many machines are using which platformVersion
|order by PlatformVersion desc
```
