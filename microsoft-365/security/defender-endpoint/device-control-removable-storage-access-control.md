---
title: Microsoft Defender for Endpoint Access Control flytbart lagermedie til enhedsstyring
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
ms.date: 06/24/2022
ms.openlocfilehash: d9ff97aa50a03c1a75f073328a250a9acc3faf54
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/29/2022
ms.locfileid: "66490747"
---
# <a name="microsoft-defender-for-endpoint-device-control-removable-storage-access-control"></a>Access Control flytbare lagermedier Microsoft Defender for Endpoint enhedsstyring

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> [!NOTE]
> Administration af Gruppepolitik og Intune OMA-URI/Custom Policy management af dette produkt er nu offentlig tilgængelig (4.18.2106): Se [Tech Community-bloggen: Beskyt dit flytbare lager og din printer med Microsoft Defender for Endpoint](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/protect-your-removable-storage-and-printers-with-microsoft/ba-p/2324806).

## <a name="device-control-removable-storage-access-control-overview"></a>Oversigt over flytbare lagermedier til enhedsstyring Access Control

Microsoft Defender for Endpoint device control Flytbare lagermedier Access Control funktion giver dig mulighed for at overvåge, tillade eller forhindre adgang til læsning, skrivning eller udførelse af flytbare lagermedier med eller uden udeladelse.

|Privilegium|Tilladelse|
|---|---|
|Access|Læs, Skriv, Udfør|
|Handlingstilstand|Overvåg, Tillad, Forbyd|
|Understøttelse af CSP|Ja|
|Understøttelse af gruppepolitikobjekt|Ja|
|Brugerbaseret support|Ja|
|Computerbaseret support|Ja|

Microsoft Defender for Endpoint funktionen Flytbare lagermedier til enhedshåndtering Access Control giver dig følgende funktioner:

|Kapacitet|Beskrivelse|Udrul via Intune|Udrul via Gruppepolitik|
|---|---|---|---|
|Oprettelse af flytbar mediegruppe|Giver dig mulighed for at oprette en flytbar mediegruppe, der kan genbruges|Trin 4 og 6 i afsnittet [Udrulning af Flytbare lagermedier Access Control ved hjælp af Intune OMA-URI](#deploying-removable-storage-access-control-by-using-intune-oma-uri)| Trin 4 og 6 i afsnittet [Udrulning af Flytbare lagermedier Access Control ved hjælp af Gruppepolitik](#deploying-removable-storage-access-control-by-using-group-policy)|
|Oprettelse af politik|Giver dig mulighed for at oprette en politik, der gennemtvinger hver flytbare mediegruppe|Trin 5 og 7 i afsnittet [Udrulning af Flytbare lagermedier Access Control ved hjælp af Intune OMA-URI](#deploying-removable-storage-access-control-by-using-intune-oma-uri)| Trin 5 og 7 i afsnittet [Udrulning af Flytbare lagermedier Access Control ved hjælp af Gruppepolitik](#deploying-removable-storage-access-control-by-using-group-policy)|
|Standard gennemtvingelse|Giver dig mulighed for at angive standardadgang (Afvis eller Tillad) til flytbare medier, hvis der ikke er nogen politik|Trin 2 i afsnittet [Udrulning af Flytbare lagermedier Access Control ved hjælp af Intune OMA-URI](#deploying-removable-storage-access-control-by-using-intune-oma-uri) | Trin 2 i afsnittet [Udrulning af Flytbare lagermedier Access Control ved hjælp af Gruppepolitik](#deploying-removable-storage-access-control-by-using-group-policy)|
|Aktivér eller deaktiver flytbare lagermedier Access Control|Hvis du angiver Deaktiver, deaktiveres Politikken for Flytbare lagermedier Access Control på denne computer| Trin 1 i afsnittet [Installation af Flytbare lagermedier Access Control ved hjælp af Intune OMA-URI](#deploying-removable-storage-access-control-by-using-intune-oma-uri)| Trin 1 i afsnittet [Udrulning af Flytbare lagermedier Access Control ved hjælp af Gruppepolitik](#deploying-removable-storage-access-control-by-using-group-policy)|
|Hent filoplysninger|Giver dig mulighed for at oprette en politik til hentning af filoplysninger, når der sker skriveadgang|  | Trin 10 i afsnittet [Udrulning af Flytbare lagermedier Access Control ved hjælp af Gruppepolitik](#deploying-removable-storage-access-control-by-using-group-policy) |

### <a name="prepare-your-endpoints"></a>Forbered dine slutpunkter

Installer Flytbare lagermedier Access Control på Windows 10 og Windows 11 enheder, der har antimalwareklientversion **4.18.2103.3 eller nyere**.

- **4.18.2104 eller nyere**: Tilføj `SerialNumberId`understøttelse af filstibaseret gruppepolitikobjekt af typen , `VID_PID`og `ComputerSid`

- **4.18.2105 eller nyere**: Tilføj understøttelse af jokertegn for `HardwareId/DeviceId/InstancePathId/FriendlyNameId/SerialNumberId`, kombinationen af specifik bruger på en bestemt maskine, SSD, der kan fjernes (en SanDisk Extreme SSD)/UAS-understøttelse (USB Attached SCSI)

- **4.18.2107 eller nyere**: Tilføj understøttelse af Windows Portable Device (WPD) (til mobilenheder, f.eks. tablets); føj `AccountName` til [avanceret jagt](device-control-removable-storage-access-control.md#view-device-control-removable-storage-access-control-data-in-microsoft-defender-for-endpoint)

- **4.18.2205 eller nyere**: Udvid standardgennemtvingenheden til **Printer**. Hvis du angiver den til **Afvis**, blokeres printeren også, så hvis du kun vil administrere lagerplads, skal du sørge for at oprette en brugerdefineret politik for at tillade Printer.

:::image type="content" source="images/powershell.png" alt-text="PowerShell-grænsefladen" lightbox="images/powershell.png":::

> [!NOTE]
> Ingen af Windows Sikkerhed komponenter skal være aktive, da du kan køre Flytbare lagermedier Access Control uafhængigt af Windows Sikkerhed status.

## <a name="device-control-removable-storage-access-control-policies"></a>Politikker for flytbart lager Access Control for enhedsstyring

Du kan bruge følgende egenskaber til at oprette en flytbar lagergruppe:

> [!NOTE]
> Kommentarer, der bruger XML-kommentarnotation `<!-- COMMENT -->` , kan bruges i XML-filerne Regel og Gruppe, men de skal være inden for den første XML-kode og ikke den første linje i XML-filen.

### <a name="removable-storage-group"></a>Flytbar lagergruppe

|Egenskabsnavn|Beskrivelse|Muligheder|
|---|---|---|
|**Gruppe-id**|GUID, et entydigt id, repræsenterer gruppen og bruges i politikken.||
|**DescriptorIdList**|Angiv de enhedsegenskaber, du vil bruge til at dække i gruppen. Du kan finde flere oplysninger om hver enhedsegenskab under [Egenskaber for enhed](device-control-removable-storage-protection.md) . Der skelnes mellem store og små bogstaver i alle egenskaber. |**PrimaryId**: `RemovableMediaDevices`, `CdRomDevices`, `WpdDevices`<p>**BusId**: F.eks. USB, SCSI<p>**Deviceid**<p>**HardwareId**<p>**InstancePathId**: InstancePathId er en streng, der entydigt identificerer enheden i systemet, `USBSTOR\DISK&VEN_GENERIC&PROD_FLASH_DISK&REV_8.07\8735B611&0`f.eks. . Tallet i slutningen (f.eks. &0) repræsenterer det tilgængelige slot og kan ændres fra enhed til enhed. Du opnår det bedste resultat ved at bruge et jokertegn i slutningen. Det kunne f.eks. være `USBSTOR\DISK&VEN_GENERIC&PROD_FLASH_DISK&REV_8.07\8735B611*`.<p>**FriendlyNameId**<p>**SerialNumberId**<p>**VID**<p>**PID**<p>**VID_PID**<p>`0751_55E0`: matcher dette nøjagtige VID/PID-par<p>`_55E0`: Match et hvilket som helst medie med PID=55E0 <p>`0751_`: matcher et hvilket som helst medie med VID=0751|
|**MatchType**|Når der bruges flere enhedsegenskaber i `DescriptorIDList`, definerer MatchType relationen.|**MatchAll**: Alle attributter under relationen `DescriptorIdList` vil være **And** . Hvis administratoren f.eks. placerer `DeviceID` og `InstancePathID`for hver tilsluttet USB, kontrollerer systemet, om USB'en opfylder begge værdier. <p> **MatchAny**: Attributterne under DescriptorIdList vil være **relationen Or** . Hvis administratoren f.eks. sætter `DeviceID` og `InstancePathID`for hver tilsluttet USB, gennemtvinger systemet håndhævelsen, så længe USB'en har enten en identisk **DeviceID** - eller **InstanceID-værdi** .|

### <a name="access-control-policy"></a>politik for Access Control
Du kan bruge følgende egenskaber til at oprette politikken for adgangskontrol:

| Egenskabsnavn | Beskrivelse | Muligheder |
|---|---|---|
| **Politikregel-id** | GUID, et entydigt id, repræsenterer politikken og bruges i rapportering og fejlfinding. | |
| **IncludedIdList** | De grupper, som politikken skal anvendes på. Hvis der tilføjes flere grupper, anvendes politikken på alle medier i alle disse grupper.|Gruppe-id/GUID skal bruges i denne forekomst. <p> I følgende eksempel vises brugen af GroupID: <p> `<IncludedIdList> <GroupId> {EAA4CCE5-F6C9-4760-8BAD-FDCC76A2ACA1}</GroupId> </IncludedIdList>` |
| **ExcludedIDList** | De grupper, som politikken ikke anvendes på. | Gruppe-id/GUID skal bruges i denne forekomst. |
| **Adresse-id** | Én Politikregel kan have flere poster. Hver post med et entydigt GUID fortæller Enhedshåndtering én begrænsning.| |
| **Type** | Definerer handlingen for de flytbare lagergrupper på IncludedIDList. <p>Håndhævelse: Tillad eller Afvis <p>Overvågning: AuditAllowed eller AuditDenied<p> | Tillad<p>Benægte <p>AuditAllowed: Definerer meddelelse og hændelse, når adgang er tilladt <p>AuditDenied: Definerer meddelelse og hændelse, når adgang nægtes. skal arbejde sammen med **Afvis** post.<p> Når der er konflikttyper for de samme medier, anvender systemet den første i politikken. Et eksempel på en konflikttype er **Tillad** og **Afvis**. |
| **Sid** | Sid for lokal bruger eller sid-gruppe for brugeren eller SID'et for AD-objektet definerer, om denne politik skal anvendes på en bestemt bruger eller brugergruppe. én post kan maksimalt have ét Sid, og en post uden sid betyder anvendelse af politikken over maskinen. |  |
| **ComputerSid** | Sid- eller computer-SID-gruppen eller SID'et for AD-objektet definerer, om denne politik skal anvendes på en bestemt computer- eller computergruppe. én post kan maksimalt have ét ComputerSid, og en post uden ComputerSid betyder, at politikken skal anvendes på computeren. Hvis du vil anvende en Entry på en bestemt bruger og en bestemt maskine, skal du føje både Sid og ComputerSid til den samme post. |  |
| **Muligheder** | Definerer, om der skal vises en meddelelse eller ej |**Når Tillad type er valgt**: <p>0: intet<p>4: Deaktiver **AuditAllowed** og **AuditDenied** for denne post. Selvom **Allow** sker, og indstillingen AuditAllowed er konfigureret, sender systemet ikke hændelsen. <p>8: Hent filoplysninger, og få en kopi af filen som dokumentation for skriveadgang. <p>16: Hent filoplysninger for skriveadgang. <p>**Når Afvis type er valgt**: <p>0: intet<p>4: Deaktiver **AuditDenied** for denne post. Selvom **Block** sker, og AuditDenied er konfigureret, vises der ikke en meddelelse i systemet. <p>**Når Type **AuditAllowed** er valgt**: <p>0: intet <p>1: intet <p>2: Send begivenhed<p> **Når Type **AuditDenied** er valgt**: <p>0: intet <p>1: vis meddelelse <p>2: Send begivenhed<p>3: Vis meddelelse og send begivenhed |
|AccessMask|Definerer adgangen. | **Adgang på diskniveau**: <p>1: Læs <p>2: Skriv <p>4: Udfør <p>**Adgang på filsystemniveau**: <p>8: Filsystemet Læs <p>16: Skriv til filsystemet <p>32: Filsystemet Udfør <p><p>Du kan have flere adgange ved at udføre en binær OR-handling. AccessMask for Læs og Skriv og Udfør vil f.eks. være 7. AccessMask for Læs og Skriv er 3.|

## <a name="device-control-removable-storage-access-control-scenarios"></a>Scenarier med flytbare Access Control af enhedskontrolelementer

For at hjælpe dig med at blive fortrolig med Microsoft Defender for Endpoint Flytbare lagermedier Access Control har vi sammensat nogle almindelige scenarier, som du kan følge.

### <a name="scenario-1-prevent-write-and-execute-access-to-all-but-allow-specific-approved-usbs"></a>Scenarie 1: Undgå skrive- og udførelsesadgang til alle undtagen tillad specifikke godkendte USB'er

1. Opret grupper

    1. Gruppe 1: Ethvert flytbart lager og cd/dvd. Et eksempel på et flytbart lagermedie og en cd/dvd er: Gruppér **9b28fae8-72f7-4267-a1a5-685f747a7146** i eksempelfilen [Any Flytbart lagermedie og cd-dvd Group.xml](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) fil.

    2. Gruppe 2: Godkendte USB'er baseret på enhedsegenskaber. Et eksempel på denne use case er: Instance ID – Group **65fa649a-a111-4912-9294-fb6337a25038** i eksemplet [Godkendte USB'er Group.xml](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) fil.

    > [!TIP]
    > Erstat `&` med `&amp;` i værdien.

2. Opret politik

    1. Politik 1: Bloker Skrive- og Udfør-adgang, men tillad godkendte USB'er. Et eksempel på denne use case er: PolicyRule **c544a991-5786-4402-949e-a032cb790d0e** i [eksempelscenariet 1 Block Write and Execute Access, men tillad godkendt USBs.xml](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) fil.

    2. Politik 2: Overvåg adgangen Skriv og Udfør til tilladte USB'er. Et eksempel på denne use case er: PolicyRule **36ae1037-a639-4cff-946b-b36c53089a4c** i [eksempelscenariet 1 overvågningsskrivnings- og udførelsesadgang til godkendt USBs.xml](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) fil.

### <a name="scenario-2-audit-write-and-execute-access-to-all-but-block-specific-unapproved-usbs"></a>Scenarie 2: Overvåg skrive- og udførelsesadgang til alle, men bloker specifikke ikke-godkendte USB'er

1. Opret grupper

    1. Gruppe 1: Ethvert flytbart lager og cd/dvd. Et eksempel på denne brugscase er: Gruppe **9b28fae8-72f7-4267-a1a5-685f747a7146** i eksemplet [på Any Removable Storage- og CD-DVD-Group.xml-filen](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) .

    2. Gruppe 2: UsB'er, der ikke er godkendt, baseret på enhedsegenskaber, f.eks. Leverandør-id/Produkt-id, Brugervenligt navn - Gruppe **65fa649a-a111-4912-9294-fb6337a25038** i eksemplet [På ikke-godkendte USB'er Group.xml](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) fil.

    > [!TIP]
    > Erstat `&` med `&amp;` i værdien.

2. Opret politik

    1. Politik 1: Bloker adgangen Skriv og Udfør til alle, men bloker specifikke ikke-godkendte USB'er. Et eksempel på denne use case er: PolicyRule **23b8e437-66ac-4b32-b3d7-24044637fc98** i [scenariet Scenario 2 Audit Write and Execute adgang til alle, men bloker specifikke ikke-godkendte USBs.xml](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) fil.

    2. Politik 2: Overvåg adgangen Skriv og Udfør til andre. Et eksempel på denne use case er: PolicyRule **b58ab853-9a6f-405c-a194-740e69422b48** i [eksempelscenariet 2 Overvågningsskrivning og Udfør-adgang til others.xml](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) fil.

## <a name="deploying-and-managing-removable-storage-access-control-by-using-intune-oma-uri"></a>Udrulning og administration af Flytbare lagermedier Access Control ved hjælp af Intune OMA-URI

Funktionen Flytbare lagermedier Access Control giver dig mulighed for at anvende politik ved hjælp af OMA-URI på enten bruger eller enhed eller begge dele.

### <a name="licensing-requirements"></a>Licenskrav

Før du kommer i gang med Flytbare lagermedier Access Control, skal du bekræfte dit [Microsoft 365-abonnement](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=2). Hvis du vil have adgang til og bruge Access Control til Flytbare lagermedier, skal du have Microsoft 365 E3 eller Microsoft 365 E5.

### <a name="permission"></a>Tilladelse

I forbindelse med politikinstallation i Intune skal kontoen have tilladelser til at oprette, redigere, opdatere eller slette enhedskonfigurationsprofiler. Du kan oprette brugerdefinerede roller eller bruge en af de indbyggede roller med disse tilladelser.

- Rolle som politik- og profiladministrator
- Brugerdefineret rolle med tilladelserne Opret/Rediger/Opdater/Læs/Slet/Vis rapporter slået til for profiler til enhedskonfiguration
- Global administrator

### <a name="deploying-removable-storage-access-control-by-using-intune-oma-uri"></a>Udrulning af Flytbare lagermedier Access Control ved hjælp af Intune OMA-URI

Gå til Microsoft Endpoint Manager Administration (<https://endpoint.microsoft.com/>) **> Enheder > Opret profil > Platform: Windows 10 og nyere, Profiltype: Skabeloner > Brugerdefineret**

1. Aktivér eller deaktiver enhedskontrol på følgende måde:

   - Klik på **Tilføj** under **Konfigurationsindstillinger for brugerdefineret >**.
   - I ruden **Tilføj række** skal du angive:
     - **Navngiv** som **Aktivér enhedskontrol**
     - **OMA-URI** som `./Vendor/MSFT/Defender/Configuration/DeviceControlEnabled`
     - **Datatype** som **heltal**
     - **Værdi** som **1**

       `Disable: 0`
       `Enable: 1`

     - Klik på **Gem**.

   :::image type="content" source="images/enable-rsac.png" alt-text="Skærmbillede af aktivering af politikken for Flytbare lagermedier Access Control" lightbox="images/enable-rsac.png":::

2. Angiv standard gennemtvingelse:

   Du kan angive standardadgangen (Afvis eller Tillad) for alle funktioner i Enhedshåndtering (`RemovableMediaDevices`, `CdRomDevices`, `WpdDevices`, `PrinterDevices`).

   Du har f.eks. enten politikken **Afvis** eller **Tillad** for `RemovableMediaDevices`, men du har ikke en politik for `CdRomDevices` eller `WpdDevices`. Du kan angive **Standardafvis** via denne politik, hvorefter adgangen `CdRomDevices` Læs/Skriv/Udfør til eller `WpdDevices` blokeres. Hvis du kun vil administrere lagerplads, skal du sørge for at oprette en **tillad** politik for printeren. Ellers anvendes denne standard gennemtvingelse også på printere.

   - I ruden **Tilføj række** skal du angive:
     - **Navn** som **standardafvis**
     - **OMA-URI** som `./Vendor/MSFT/Defender/Configuration/DefaultEnforcement`
     - **Datatype** som **heltal**
     - **Værdi** som **1** eller **2**

       `DefaultEnforcementAllow = 1`
       `DefaultEnforcementDeny = 2`

     - Klik på **Gem**.

   :::image type="content" source="images/default-deny.png" alt-text="Skærmbillede af angivelse af Standard gennemtvingelse som Afvis" lightbox="images/default-deny.png":::

3. Afvis som standard for overvågning:

   Du kan oprette en overvågningspolitik for Standardafvis på følgende måde:

   - I ruden **Tilføj række** skal du angive:
     - **Navn** som **standardafvising for overvågning**
     - **OMA-URI** som `./Vendor/MSFT/Defender/Configuration/DeviceControl/PolicyRules/%7bf3520ea7-fd1b-4237-8ebc-96911db44f8e%7d/RuleData`

       :::image type="content" source="images/audit-default-deny-1.png" alt-text="Skærmbillede af oprettelse af politik for standardafvising for overvågning" lightbox="images/audit-default-deny-1.png":::

     - **Datatype** som **streng (XML-fil)**
     - **Brugerdefineret XML** som **standardfil Deny.xml** .

       Sti til XML-fil: <https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/Intune%20OMA-URI/Audit%20Default%20Deny.xml>

       Brug følgende XML-data til at oprette overvågningspolitikken for Standardafvising:

       :::image type="content" source="images/audit-default-deny-xml-file-1.png" alt-text="Skærmbillede af xml-filen til standardafvising som standard":::

4. ReadOnly – Gruppe:

   Du kan oprette en flytbar lagergruppe med Skrivebeskyttet adgang på følgende måde:

   - I ruden **Tilføj række** skal du angive:
     - **Navngiv** som **en hvilken som helst flytbar lagergruppe**
     - **OMA-URI** som `./Vendor/MSFT/Defender/Configuration/DeviceControl/PolicyGroups/%7b9b28fae8-72f7-4267-a1a5-685f747a7146%7d/GroupData`

       :::image type="content" source="images/any-removable-storage-group.png" alt-text="Skærmbillede af oprettelse af en flytbar lagergruppe" lightbox="images/any-removable-storage-group.png":::

     - **Datatype** som **streng (XML-fil)**
       - **Brugerdefineret XML** som **et vilkårligt flytbart lagermedier og en cd-dvd og en WPD-Group.xml** fil

         Sti til XML-fil: <https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/Intune%20OMA-URI/Any%20Removable%20Storage%20and%20CD-DVD%20and%20WPD%20Group.xml>

         Brug følgende XML-data til at oprette 'Any Flytbare Storage- og CD-DVD- og WPD-grupper' med ReadOnly-adgang:

         :::image type="content" source="images/read-only-group-xml-file.png" alt-text="Skærmbillede af skrivebeskyttet xml-gruppefil":::

5. ReadOnly – Politik:

   Du kan oprette en ReadOnly-politik og anvende den på den flytbare ReadOnly-lagergruppe for at tillade læseaktivitet på følgende måde:

   - I ruden **Tilføj række** skal du angive:
     - **Navngiv** som **Tillad læseaktivitet**
     - **OMA-URI** som `./Vendor/MSFT/Defender/Configuration/DeviceControl/PolicyRules/%7bf7e75634-7eec-4e67-bec5-5e7750cb9e02%7d/RuleData`

       :::image type="content" source="images/allow-read-activity.png" alt-text="Skærmbillede af politikken Tillad læseaktivitet" lightbox= "images/allow-read-activity.png":::

     - **Datatype** som **streng (XML-fil)**
     - **Brugerdefineret XML** som **Tillad Read.xml-fil**

       Sti til XML-fil: <https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/Intune%20OMA-URI/Allow%20Read.xml>

       Brug følgende XML-data til at oprette En ReadOnly-politik og anvende den flytbare ReadOnly-lagergruppe:

       :::image type="content" source="images/read-only-policy-xml-file.png" alt-text="Skærmbillede af xml-fil med skrivebeskyttet politik":::

6. Opret en gruppe for tilladte medier: Du kan oprette den tilladte mediegruppe på følgende måde:
   - I ruden **Tilføj række** skal du angive:
     - **Navngiv** som **godkendt USB-gruppe**
     - **OMA-URI** som `./Vendor/MSFT/Defender/Configuration/DeviceControl/PolicyGroups/%7b65fa649a-a111-4912-9294-fb6337a25038%7d/GroupData`

       :::image type="content" source="images/create-group-allowed-medias.png" alt-text="Skærmbillede af oprettelse af gruppen Godkendte USB'er" lightbox="images/create-group-allowed-medias.png":::

     - **Datatype** som **streng (XML-fil)**
     - **Brugerdefineret XML** som **godkendt Group.xml-fil**

       Sti til XML-fil: <https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/Intune%20OMA-URI/Approved%20USBs%20Group.xml>

       Brug følgende XML-data til at oprette en tilladt mediegruppe:

       :::image type="content" source="images/create-group-allowed-medias-xml-file.png" alt-text="Skærmbillede af oprettelse af gruppe for tilladt XML-mediefil":::

7. Opret en politik for at tillade den godkendte USB-gruppe: Du kan oprette en politik for at tillade den godkendte USB-gruppe på følgende måde:
   - I ruden **Tilføj række** skal du angive:
     - **Navngiv** som **Tillad adgang og Overvåg filoplysninger**
     - **OMA-URI** som `./Vendor/MSFT/Defender/Configuration/DeviceControl/PolicyRules/%7bb2061588-029e-427d-8404-6dfec096a571%7d/RuleData`

       :::image type="content" source="images/allow-access-audit-file-information-1.png" alt-text="Skærmbillede af Tillad adgangs- og overvågningsfiloplysninger" lightbox= "images/allow-access-audit-file-information-1.png":::

     - **Datatype** som **streng (XML-fil)**
     - **Brugerdefineret XML** som **Tillad fuld adgang og overvågning file.xml**  fil

       Sti til XML-fil: <https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/Intune%20OMA-URI/Allow%20full%20access%20and%20audit%20file.xml>

       Brug følgende XML-data til at oprette en politik, der tillader den godkendte USB-gruppe:

       :::image type="content" source="images/create-policy-allow-approved-usb-group-xml-intune.png" alt-text="Skærmbillede af oprettelse af en politik, der tillader den godkendte USB-gruppe-XML-fil":::

       Hvad betyder "47" i politikken? Det er 9 + 2 + 36 = 47:

       - Læseadgang: 1 + 8 = 9.
       - Skriveadgang: diskniveau 2.
       - Udfør: 4 + 32 = 36.

## <a name="deploying-and-managing-policy-by-using-intune-user-interface"></a>Udrulning og administration af politik ved hjælp af Intune brugergrænseflade

Denne funktion er tilgængelig i Microsoft Endpoint Manager Administration (<https://endpoint.microsoft.com/>). Gå til **Endpoint Security** > **Attack Surface Reduction** > **Create Policy**. Vælg **Platform: Windows 10 og nyere** med **Profil: Enhedskontrol**.

## <a name="deploying-and-managing-removable-storage-access-control-by-using-group-policy"></a>Udrulning og administration af Flytbare lagermedier Access Control ved hjælp af Gruppepolitik

Funktionen Flytbare lagermedier Access Control giver dig mulighed for at anvende en politik ved hjælp af Gruppepolitik til enten bruger eller enhed eller begge dele.

### <a name="licensing"></a>Licensering

Før du kommer i gang med Flytbare lagermedier Access Control, skal du bekræfte dit [Microsoft 365-abonnement](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=2). Hvis du vil have adgang til og bruge Access Control til Flytbare lagermedier, skal du have Microsoft 365 E3 eller Microsoft 365 E5.

### <a name="deploying-removable-storage-access-control-by-using-group-policy"></a>Udrulning af Flytbare lagermedier Access Control ved hjælp af Gruppepolitik

1. Aktivér eller deaktiver flytbare lagermedier Access Control:

   Du kan aktivere enhedskontrol på følgende måde:

   - Gå til **Computerkonfiguration > Administrative skabeloner > Windows-komponenter > Microsoft Defender Antivirus > Funktioner > Enhedskontrol**
   - I vinduet **Enhedskontrol** skal du vælge **Aktiveret**.

   :::image type="content" source="images/enable-rsac-gp.png" alt-text="Skærmbillede af aktivering af RSAC ved hjælp af Gruppepolitik " lightbox="images/enable-rsac-gp.png":::

2. Angiv standard gennemtvingelse:

   Du kan angive standardadgang (Afvis eller Tillad) for alle enhedskontrolfunktioner (Flytbare medier, CdRomDevices, WpdDevices, PrinterDevices).

   Du har f.eks. enten politikken Afvis eller Tillad for RemovableMediaDevices, men du har ikke nogen politik for CdRomDevices eller WpdDevices. Du angiver Standardafvis via denne politik, og derefter blokeres adgangen Læs/Skriv/Udfør til CdRomDevices eller WpdDevices. Hvis du kun vil administrere lagerpladsen, skal du sørge for at oprette Tillad politik for printer. Ellers anvendes denne standard gennemtvingelse også på printeren.

   - Gå til **Computerkonfiguration > Administrative skabeloner > Windows-komponenter > Microsoft Defender Antivirus > Funktioner > Enhedskontrol > Vælg standard gennemtvingelse af enhedskontrol**

   - I vinduet **Vælg standard gennemtvingelse af enhedskontrol** skal du vælge **Standardafvis:**

   :::image type="content" source="images/set-default-enforcement-deny-gp.png" alt-text="Skærmbillede af angivelse af Standard gennemtvingelse = Afvis ved hjælp af Gruppepolitik" lightbox="images/set-default-enforcement-deny-gp.png":::

3. Afvis som standard for overvågning:

   Brug følgende XML-data til at oprette overvågningspolitik for Standardafvising:

   :::image type="content" source="images/audit-default-deny-gp.png" alt-text="Skærmbillede af standardafvis xml-data for overvågning":::

4. ReadOnly – Gruppe:

   Brug følgende XML-data til at oprette en flytbar lagergruppe med Skrivebeskyttet adgang:

   :::image type="content" source="images/read-only-group-gp.png" alt-text="Skærmbillede af XML-data for skrivebeskyttet flytbar lagergruppe":::

5. ReadOnly – Politik:

   Brug følgende XML-data til at oprette en ReadOnly-politik og anvende den flytbare ReadOnly-lagergruppe for at tillade læseaktivitet:

    :::image type="content" source="images/read-only-policy-gp.png" alt-text="Skærmbillede af XML-data for skrivebeskyttet politik" lightbox="images/read-only-policy-gp.png":::

6. Opret gruppe for tilladte medier:

   Brug følgende XML-data til at oprette en tilladt mediegruppe for flytbart lager:

   :::image type="content" source="images/create-group-allowed-medias-gp.png" alt-text="Skærmbillede af XML-data til oprettelse af gruppe for tilladte medier" lightbox="images/create-group-allowed-medias-gp.png":::

7. Opret politik for at tillade den godkendte USB-gruppe:

   Brug følgende XML-data til at oprette en politik, der tillader godkendt USB-gruppe:

   :::image type="content" source="images/create-policy-allow-approved-usb-group-xml.png" alt-text="Skærmbillede af XML-data til oprettelse af en politik, der tillader den godkendte USB-gruppe ved hjælp af Gruppepolitik" lightbox="images/create-policy-allow-approved-usb-group-xml.png":::

   Hvad betyder "47" i politikken? Det er 9 + 2 + 36 = 47:

   - Læseadgang: 1+8 = 9.
   - Skriveadgang: diskniveau 2.
   - Udfør: 4 + 32 = 36.

8. Kombiner grupper i én XML-fil:

   Du kan kombinere politikgrupper for enhedskontrol i én XML-fil på følgende måde:

   - Gå til **Computerkonfiguration** \> **Administrative skabeloner** \> **Windows-komponenter** \> **Microsoft Defender Antivirus** \> **Enhedskontrol** \> **Definer politikgrupper for enhedskontrol**.

    :::image type="content" source="images/define-device-control-policy-grps-gp.png" alt-text="Skærmbillede af Definer politikgrupper for enhedskontrol" lightbox="images/define-device-control-policy-grps-gp.png":::

   - I vinduet **Definer politikgrupper for enhedskontrol** skal du angive den filsti, der indeholder XML-gruppernes data.

     Sti til XML-fil: <https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/Group%20Policy/Demo_Groups.xml>

     Følgende er XML-skemaet for politikgrupper for enhedskontrol:

     :::image type="content" source="images/combine-grps-xml-file-gp.png" alt-text="Skærmbillede af kombiner grupper i én XML-fil":::

9. Kombiner politikker i én XML-fil:

   Du kan kombinere politikregler for enhedskontrol i én XML-fil på følgende måde:

   - Gå til **Computerkonfiguration > Administrative skabeloner > Windows-komponenter > Microsoft Defender Antivirus > Device Control > Definer politikregler for enhedskontrol**

     :::image type="content" source="images/define-device-cntrl-policy-rules-gp.png" alt-text="Skærmbillede af definer politikregler for enhedskontrol" lightbox="images/define-device-cntrl-policy-rules-gp.png":::

   - I vinduet **Definer politikregler for enhedskontrol** skal du vælge **Aktiveret** og angive den filsti, der indeholder XML-regeldataene.

     Sti til XML-fil: <https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/Group%20Policy/Demo_Policies.xml>

     Følgende er XML-skemaet for politikregler for enhedskontrol:

    :::image type="content" source="images/combine-policies-xml-gp.png" alt-text="Skærmbillede af kombination af politikker i én XML-fil":::

10. Angiv placeringen af en kopi af filen (beviser):

    Hvis du vil have en kopi af filen (beviser), når skriveadgangen finder sted, skal du angive den placering, hvor systemet kan gemme kopien.

    - Gå til **Computerkonfiguration > Administrative skabeloner > Windows-komponenter > Microsoft Defender Antivirus > Device Control > Define Device Control evidence data remote location**.

    - I vinduet **Definer beviser for enhedskontroldata skal** du vælge **Aktiveret** og angive stien til den lokale mappe eller netværkssharemappe.

      :::image type="content" source="images/evidence-data-remote-location-gp.png" alt-text="Skærmbillede af fjernplacering af enhedskontroldata" lightbox="images/evidence-data-remote-location-gp.png":::

## <a name="view-device-control-removable-storage-access-control-data-in-microsoft-defender-for-endpoint"></a>Få vist data om flytbare lagermedier til enhedsstyring Access Control data i Microsoft Defender for Endpoint

På [Microsoft 365 Defender-portalen](https://security.microsoft.com/advanced-hunting) vises hændelser, der udløses af Access Control til Flytbare lagermedier for enhedskontrol. Hvis du vil have adgang til sikkerheden i Microsoft 365, skal du have følgende abonnement:

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

:::image type="content" source="images/block-removable-storage.png" alt-text="Skærmen, der viser blokeringen af det flytbare lager.":::

## <a name="frequently-asked-questions"></a>Ofte stillede spørgsmål

### <a name="how-to-generate-guid-for-group-idpolicyrule-identry-id"></a>Hvordan genererer du GUID for gruppe-id/PolicyRule-id/post-id?

Du kan generere GUID via online åben kildekode eller via PowerShell – [Sådan genererer du GUID via PowerShell](/powershell/module/microsoft.powershell.utility/new-guid)

![Billede](https://user-images.githubusercontent.com/81826151/159046476-26ea0a21-8087-4f01-b8ae-5aa73b392d8f.png)

### <a name="what-are-the-removable-storage-media-and-policy-limitations"></a>Hvad er begrænsningerne for flytbare lagermedier og politikker?

Enten fra Microsoft Endpoint Manager Administration (Intune) eller via Microsoft Graph API udføres backendopkaldet via OMA-URI (GET to read eller PATCH to update), og begrænsningen er derfor den samme som enhver brugerdefineret OMA-URI-konfigurationsprofil i Microsoft, som officielt er 350.000 tegn for XML-filer.

Hvis du f.eks. har brug for to blokke med poster pr. bruger-SID til "Tillad"/"Overvågning tilladt" bestemte brugere og to blokke af poster i slutningen til "Afvis" alle, kan du administrere 2.276 brugere.

### <a name="why-does-the-policy-not-work"></a>Hvorfor fungerer politikken ikke?

1. Den mest almindelige årsag er, at der ikke er nogen påkrævet [antimalwareklientversion](/microsoft-365/security/defender-endpoint/device-control-removable-storage-access-control#prepare-your-endpoints).

2. En anden årsag kan være, at XML-filen ikke er formateret korrekt, f.eks. at den korrekte markdown-formatering ikke bruges til tegnet "&" i XML-filen, eller at teksteditoren tilføjer et byterækkefølgetegn (BOM) 0xEF 0xBB 0xBF i starten af filerne, hvilket medfører, at XML-fortolkning ikke fungerer. En enkel løsning er at downloade [eksempelfilen](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) (vælge **Rå** og derefter **Gem som**) og derefter opdatere.

3. Hvis du installerer og administrerer politikken ved hjælp af Gruppepolitik, skal du sørge for at kombinere alle PolicyRule i én XML-fil i en overordnet node, der kaldes PolicyRules, og alle grupper i én XML-fil i en overordnet node kaldet Grupper. Hvis du administrerer via Intune, skal du beholde én PolicyRule én XML-fil, samme ting, én gruppér én XML-fil.

Hvis det stadig ikke virker, kan du kontakte os og dele support-cab ved at køre cmd med administratoren: "%programfiles%\Windows Defender\MpCmdRun.exe" -GetFiles

### <a name="there-is-no-configuration-ux-for-define-device-control-policy-groups-and-define-device-control-policy-rules-on-my-group-policy"></a>Der er ingen konfigurations-UX for 'Definer politikgrupper for enhedskontrol' og 'Definer politikregler for enhedskontrol' på mit Gruppepolitik

Vi backporterer ikke Gruppepolitik konfigurations-UX, men du kan stadig hente de relaterede adml- og admx-filer ved at klikke på 'Raw' og 'Gem som' i [filerne WindowsDefender.adml](https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/WindowsDefender.adml) og [WindowsDefender.admx](https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/WindowsDefender.admx).

### <a name="how-can-i-know-whether-the-latest-policy-has-been-deployed-to-the-target-machine"></a>Hvordan kan jeg vide, om den nyeste politik er blevet installeret på destinationscomputeren?

Du kan køre "Get-MpComputerStatus" på PowerShell som administrator. Følgende værdi viser, om den seneste politik er anvendt på destinationscomputeren.

:::image type="icon" source="images/148609885-bea388a9-c07d-47ef-b848-999d794d24b8.png" border="false":::

### <a name="how-can-i-know-which-machine-is-using-out-of-date-antimalware-client-version-in-the-organization"></a>Hvordan ved jeg, hvilken computer der bruger forældet antimalwareklientversion i organisationen?

Du kan bruge følgende forespørgsel til at hente en antimalwareklientversion på Microsoft 365-sikkerhedsportalen:

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
