---
title: Microsoft Defender for Endpoint flytbare Storage Access Control til enhedsstyring, flytbare lagermedier
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
ms.openlocfilehash: 03efd5f8681824b5625611e0c8c871bfc7fd03a6
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/06/2022
ms.locfileid: "64665134"
---
# <a name="microsoft-defender-for-endpoint-device-control-removable-storage-access-control"></a>flytbare Storage Access Control Microsoft Defender for Endpoint enhedsstyring

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> [!NOTE]
> Administration af Gruppepolitik og Intune OMA-URI/Custom Policy management af dette produkt er nu offentlig tilgængelig (4.18.2106): Se [Tech Community-bloggen: Beskyt dit flytbare lager og din printer med Microsoft Defender for Endpoint](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/protect-your-removable-storage-and-printers-with-microsoft/ba-p/2324806).

Microsoft Defender for Endpoint Flytbare Storage Access Control enhedshåndtering gør det muligt for dig at udføre følgende opgave:

- overvågning, tilladelse til eller forebyggelse af læse-, skrive- eller udførelsesadgang til flytbart lagermedier med eller uden udeladelse

|Privilegium|Tilladelse|
|---|---|
|Access|Læs, Skriv, Udfør|
|Handlingstilstand|Overvåg, Tillad, Forbyd|
|Understøttelse af CSP|Ja|
|Understøttelse af gruppepolitikobjekt|Ja|
|Brugerbaseret support|Ja|
|Computerbaseret support|Ja|

|Kapacitet|Beskrivelse|Udrul via Intune|Udrul via Gruppepolitik|
|---|---|---|---|
|Oprettelse af flytbar mediegruppe|Giver dig mulighed for at oprette en flytbar mediegruppe, der kan genbruges|Trin 1 i afsnittet [Installation af politik via OMA-URI](#deploying-policy-via-oma-uri) | Trin 1 i afsnittet [Udrulning af politik via Gruppepolitik](#deploying-policy-via-group-policy)|
|Oprettelse af politik|Giver dig mulighed for at oprette en politik, der gennemtvinger hver flytbare mediegruppe|Trin 2 i afsnittet [Installation af politik via OMA-URI](#deploying-policy-via-oma-uri) | Trin 2 og 3 i afsnittet [Installation af politik via Gruppepolitik](#deploying-policy-via-group-policy) |
|Standard gennemtvingelse|Giver dig mulighed for at angive standardadgang (Afvis eller Tillad) til flytbare medier, hvis der ikke er nogen politik|Trin 3 i afsnittet [Installation af politik via OMA-URI](#deploying-policy-via-oma-uri) | Trin 4 i afsnittet [Installation af politik via Gruppepolitik](#deploying-policy-via-group-policy) |
|Aktivér eller deaktiver Flytbare Storage Access Control|Hvis du angiver Deaktiver, deaktiveres politikken Flytbare Storage Access Control på denne computer| Trin 4 i afsnittet [Installation af politik via OMA-URI](#deploying-policy-via-oma-uri) | Trin 5 i afsnittet [Installation af politik via Gruppepolitik](#deploying-policy-via-group-policy) |
|Hent filoplysninger|Giver dig mulighed for at oprette en politik til hentning af filoplysninger, når der sker skriveadgang| Trin 2 og 5 i afsnittet [Installation af politik via OMA-URI](#deploying-policy-via-oma-uri) | Trin 2 og 6 i afsnittet [Installation af politik via Gruppepolitik](#deploying-policy-via-group-policy) |

## <a name="prepare-your-endpoints"></a>Forbered dine slutpunkter

Installer Flytbare Storage Access Control på Windows 10 og Windows 11 enheder, der har antimalwareklientversion **4.18.2103.3 eller nyere**.

- **4.18.2104 eller nyere**: Tilføj SerialNumberId, VID_PID, understøttelse af filstibaseret gruppepolitikobjekt, ComputerSid

- **4.18.2105 eller nyere**: Tilføj understøttelse af jokertegn for HardwareId/DeviceId/InstancePathId/FriendlyNameId/SerialNumberId, kombinationen af en bestemt bruger på en bestemt computer, SSD-understøttelse, der kan fjernes (en SanDisk Extreme SSD)/USB Attached SCSI (UAS)

- **4.18.2107 eller nyere**: Tilføj understøttelse af Windows Portable Device (WPD) (til mobilenheder, f.eks. tablets), føj AccountName til [avanceret jagt](device-control-removable-storage-access-control.md#view-device-control-removable-storage-access-control-data-in-microsoft-defender-for-endpoint)

:::image type="content" source="images/powershell.png" alt-text="PowerShell-grænsefladen" lightbox="images/powershell.png":::

> [!NOTE]
> Ingen af Windows Sikkerhed komponenter skal være aktive, da du kan køre Flytbare Storage Access Control uafhængigt af Windows Sikkerhed status.

## <a name="policy-properties"></a>Politikegenskaber

Du kan bruge følgende egenskaber til at oprette en flytbar lagergruppe:

> [!NOTE]
> Kommentarer, der bruger XML-kommentarnotation `<!-- COMMENT -->` , kan bruges i XML-filerne Regel og Gruppe, men de skal være inden for den første XML-kode og ikke den første linje i XML-filen.

### <a name="removable-storage-group"></a>Flytbar Storage gruppe

|Egenskabsnavn|Beskrivelse|Muligheder|
|---|---|---|
|**Gruppe-id**|GUID, et entydigt id, repræsenterer gruppen og bruges i politikken som GroupId||
|**DescriptorIdList**|Angiv de enhedsegenskaber, du vil bruge til at dække i gruppen. Du kan finde flere oplysninger om hver enhedsegenskab under [Egenskaber for enhed](device-control-removable-storage-protection.md) . Der skelnes mellem store og små bogstaver i alle egenskaber. |**PrimaryId**: `RemovableMediaDevices`, `CdRomDevices`, `WpdDevices`<p>**BusId**: F.eks. USB, SCSI<p>**Deviceid**<p>**HardwareId**<p>**InstancePathId**: InstancePathId er en streng, der entydigt identificerer enheden i systemet, `USBSTOR\DISK&VEN_GENERIC&PROD_FLASH_DISK&REV_8.07\8735B611&0`f.eks. . Tallet i slutningen (f.eks. &0) repræsenterer det tilgængelige slot og kan ændres fra enhed til enhed. Du opnår det bedste resultat ved at bruge et jokertegn i slutningen. For eksempel `USBSTOR\DISK&VEN_GENERIC&PROD_FLASH_DISK&REV_8.07\8735B611*`.<p>**FriendlyNameId**<p>**SerialNumberId**<p>**VID**<p>**PID**<p>**VID_PID**<p>`0751_55E0`: matcher dette nøjagtige VID/PID-par<p>`_55E0`: Match et hvilket som helst medie med PID=55E0 <p>`0751_`: matcher et hvilket som helst medie med VID=0751|
|**MatchType**|Når der bruges flere enhedsegenskaber i `DescriptorIDList`, definerer MatchType relationen.|**MatchAll**: Alle attributter under relationen `DescriptorIdList` vil være **And** . Hvis administratoren f.eks. placerer `DeviceID` og `InstancePathID`for hver tilsluttet USB, kontrollerer systemet, om USB'en opfylder begge værdier. <p> **MatchAny**: Attributterne under DescriptorIdList vil være **relationen Or** . Hvis administratoren f.eks. sætter `DeviceID` og `InstancePathID`for hver tilsluttet USB, gennemtvinger systemet håndhævelsen, så længe USB'en har enten en identisk **DeviceID** - eller **InstanceID-værdi** . |

### <a name="access-control-policy"></a>politik for Access Control

| Egenskabsnavn | Beskrivelse | Muligheder |
|---|---|---|
| **Politikregel-id** | GUID, et entydigt id, repræsenterer politikken og bruges i rapportering og fejlfinding. | |
| **IncludedIdList** | De grupper, som politikken skal anvendes på. Hvis der tilføjes flere grupper, anvendes politikken på alle medier i alle disse grupper.|Gruppe-id/GUID skal bruges i denne forekomst. <p> I følgende eksempel vises brugen af GroupID: <p> `<IncludedIdList> <GroupId> {EAA4CCE5-F6C9-4760-8BAD-FDCC76A2ACA1}</GroupId> </IncludedIdList>` |
| **ExcludedIDList** | De grupper, som politikken ikke anvendes på. | Gruppe-id/GUID skal bruges i denne forekomst. |
| **Adresse-id** | Én Politikregel kan have flere poster. Hver post med et entydigt GUID fortæller Enhedshåndtering én begrænsning.| |
| **Type** | Definerer handlingen for de flytbare lagergrupper på IncludedIDList. <p>Håndhævelse: Tillad eller Afvis <p>Overvågning: AuditAllowed eller AuditDenied<p> | Tillade<p>Benægte <p>AuditAllowed: Definerer meddelelse og hændelse, når adgang er tilladt <p>AuditDenied: Definerer meddelelse og hændelse, når adgang nægtes. skal arbejde sammen med **Afvis** post.<p> Når der er konflikttyper for de samme medier, anvender systemet den første i politikken. Et eksempel på en konflikttype er **Tillad** og **Afvis**. |
| **Sid** | Sid for lokal bruger eller sid-gruppe for brugeren eller SID'et for AD-objektet definerer, om denne politik skal anvendes på en bestemt bruger eller brugergruppe. én post kan maksimalt have ét Sid, og en post uden sid betyder anvendelse af politikken over maskinen. |  |
| **ComputerSid** | Sid- eller computer-SID-gruppen eller SID'et for AD-objektet definerer, om denne politik skal anvendes på en bestemt computer- eller computergruppe. én post kan maksimalt have ét ComputerSid, og en post uden ComputerSid betyder, at politikken skal anvendes på computeren. Hvis du vil anvende en Entry på en bestemt bruger og en bestemt maskine, skal du føje både Sid og ComputerSid til den samme post. |  |
| **Muligheder** | Definerer, om der skal vises en meddelelse eller ej |**Når Tillad type er valgt**: <p>0: intet<p>4: Deaktiver **AuditAllowed** og **AuditDenied** for denne post. Selvom **Allow** sker, og indstillingen AuditAllowed er konfigureret, sender systemet ikke hændelsen. <p>8: Hent filoplysninger, og få en kopi af filen som dokumentation for skriveadgang. <p>16: Hent filoplysninger for skriveadgang. <p>**Når Afvis type er valgt**: <p>0: intet<p>4: Deaktiver **AuditDenied** for denne post. Selvom **Block** sker, og AuditDenied er konfigureret, vises der ikke en meddelelse i systemet. <p>**Når Type **AuditAllowed** er valgt**: <p>0: intet <p>1: intet <p>2: Send begivenhed<p>3: Send begivenhed <p> **Når Type **AuditDenied** er valgt**: <p>0: intet <p>1: vis meddelelse <p>2: Send begivenhed<p>3: Vis meddelelse og send begivenhed |
|AccessMask|Definerer adgangen. | **Adgang på diskniveau**: <p>1: Læs <p>2: Skriv <p>4: Udfør <p>**Adgang på filsystemniveau**: <p>8: Filsystemet Læs <p>16: Skriv til filsystemet <p>32: Filsystemet Udfør <p><p>Du kan have flere adgange ved at udføre en binær OR-handling. AccessMask for Læs og Skriv og Udfør vil f.eks. være 7. AccessMask for Læs og Skriv er 3.|

## <a name="common-removable-storage-access-control-scenarios"></a>Almindelige flytbare Storage Access Control scenarier

For at gøre dig fortrolig med Microsoft Defender for Endpoint Flytbare Storage Access Control har vi sammensat nogle almindelige scenarier, som du kan følge.

### <a name="scenario-1-prevent-write-and-execute-access-to-all-but-allow-specific-approved-usbs"></a>Scenarie 1: Undgå skrive- og udførelsesadgang til alle undtagen tillad specifikke godkendte USB'er

1. Opret grupper

    1. Gruppe 1: Ethvert flytbart lager og cd/dvd. Et eksempel på et flytbart lagermedie og en cd/dvd er: Gruppe **9b28fae8-72f7-4267-a1a5-685f747a7146** i eksemplet [på En Flytbar Storage- og CD-DVD-Group.xml-fil](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples).

    2. Gruppe 2: Godkendte USB'er baseret på enhedsegenskaber. Et eksempel på denne use case er: Instance ID – Group **65fa649a-a111-4912-9294-fb6337a25038** i eksemplet [Godkendte USB'er Group.xml](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) fil.

    > [!TIP]
    > Erstat `&` med `&amp;` i værdien.

2. Opret politik

    1. Politik 1: Bloker Skrive- og Udfør-adgang, men tillad godkendte USB'er. Et eksempel på denne use case er: PolicyRule **c544a991-5786-4402-949e-a032cb790d0e** i [eksempelscenariet 1 Block Write and Execute Access, men tillad godkendt USBs.xml](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) fil.

    2. Politik 2: Overvåg adgangen Skriv og Udfør til tilladte USB'er. Et eksempel på denne use case er: PolicyRule **36ae1037-a639-4cff-946b-b36c53089a4c** i [eksempelscenariet 1 overvågningsskrivnings- og udførelsesadgang til godkendt USBs.xml](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) fil.

### <a name="scenario-2-audit-write-and-execute-access-to-all-but-block-specific-unapproved-usbs"></a>Scenarie 2: Overvåg skrive- og udførelsesadgang til alle, men bloker specifikke ikke-godkendte USB'er

1. Opret grupper

    1. Gruppe 1: Ethvert flytbart lager og cd/dvd. Et eksempel på denne brugscase er: Gruppe **9b28fae8-72f7-4267-a1a5-685f747a7146** i eksemplet [på Filen Any Flytbare Storage og CD-DVD Group.xml](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples).

    2. Gruppe 2: Ikke-godkendte USB'er baseret på enhedsegenskaber, f.eks. Leverandør-id/Produkt-id, Brugervenligt navn – Gruppe **65fa649a-a111-4912-9294-fb6337a25038** i eksemplet [På ikke-godkendte USB'er Group.xml](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) fil.

    > [!TIP]
    > Erstat `&` med `&amp;` i værdien.

2. Opret politik

    1. Politik 1: Bloker adgangen Skriv og Udfør til alle, men bloker specifikke ikke-godkendte USB'er. Et eksempel på denne use case er: PolicyRule **23b8e437-66ac-4b32-b3d7-24044637fc98** i [scenariet Scenario 2 Audit Write and Execute adgang til alle, men bloker specifikke ikke-godkendte USBs.xml](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) fil.

    2. Politik 2: Overvåg adgangen Skriv og Udfør til andre. Et eksempel på denne use case er: PolicyRule **b58ab853-9a6f-405c-a194-740e69422b48** i [eksempelscenariet 2 Overvågningsskrivning og Udfør-adgang til others.xml](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) fil.

## <a name="deploying-and-managing-policy-via-group-policy"></a>Udrulning og administration af politik via Gruppepolitik

Funktionen Flytbare Storage Access Control giver dig mulighed for at anvende en politik via Gruppepolitik til enten bruger eller enhed eller begge dele.

### <a name="licensing"></a>Licensering

Før du kommer i gang med Flytbare Storage Access Control, skal du bekræfte dit [abonnement på Microsoft 365](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=2). Hvis du vil have adgang til og bruge Flytbare Storage Access Control, skal du have Microsoft 365 E3 eller Microsoft 365 E5.

### <a name="deploying-policy-via-group-policy"></a>Installerer politik via Gruppepolitik

1. Kombiner alle grupper i `<Groups>` `</Groups>` i én XML-fil.

    På følgende billede illustreres eksemplet med [scenarie 1: Forbyd skrive- og udførelsesadgang til alle undtagen tillad specifikke godkendte USB'er](#scenario-1-prevent-write-and-execute-access-to-all-but-allow-specific-approved-usbs).

    :::image type="content" source="images/prevent-write-access-allow-usb.png" alt-text="De konfigurationsindstillinger, der tillader bestemte godkendte USB'er på enheder" lightbox="images/prevent-write-access-allow-usb.png":::

2. Kombiner alle regler i `<PolicyRules>` `</PolicyRules>` i én XML-fil.

    Hvis du vil begrænse en bestemt bruger, skal du bruge SID-egenskaben i Posten. Hvis der ikke er noget SID i politikken Post, anvendes posten på alle logonforekomster for computeren.

    Hvis du vil overvåge filoplysninger for skriveadgang, skal du bruge den rigtige AccessMask med den rigtige indstilling (16); her er eksemplet på [Hent filoplysninger](https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/Group%20Policy/Audit%20File%20Information.xml).

    På følgende billede illustreres brugen af EGENSKABEN SID og et eksempel på [scenarie 1: Forbyd skrive- og udførelsesadgang til alle undtagen tillad specifikke godkendte USB'er](#scenario-1-prevent-write-and-execute-access-to-all-but-allow-specific-approved-usbs).

    :::image type="content" source="images/usage-sid-property.png" alt-text="Den kode, der angiver brugen af SID-egenskabsattributten" lightbox="images/usage-sid-property.png":::

3. Gem både regel- og gruppe-XML-filer i netværkssharemappen, og placer stien til netværkssharemappen i indstillingen Gruppepolitik: **Computerkonfiguration** \> **Administrative skabeloner** \> **Windows Komponenter** \> **Microsoft Defender Antivirus** \> **Enhedshåndtering**: **'Definer politikgrupper for enhedskontrol'** og **'Definer politikregler for enhedskontrol'**.

   Hvis du ikke kan finde politikkonfigurations-UX'en i Gruppepolitik, kan du downloade filerne [WindowsDefender.adml](https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/WindowsDefender.adml) og [WindowsDefender.admx](https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/WindowsDefender.admx) ved at vælge **Raw** og derefter **Gem som**.

   - Destinationscomputeren skal kunne få adgang til netværkssharet for at få politikken. Når politikken er læst, er netværksshareforbindelsen dog ikke længere påkrævet, selv efter at computeren er genstartet.

    :::image type="content" source="images/device-control.png" alt-text="Skærmen Device Control (Enhedskontrol)" lightbox="images/device-control.png":::

4. Standard gennemtvingelse: Giver dig mulighed for at angive standardadgang (Afvis eller Tillad) til flytbare medier, hvis der ikke er nogen politik. Du har f.eks. kun en politik (enten Afvis eller Tillad) for RemovableMediaDevices, men du har ikke nogen politik for CdRomDevices eller WpdDevices, og du angiver standardafvis via denne politik, læse/skrive/udføre adgang til CdRomDevices eller WpdDevices blokeres.

   - Når du har installeret denne indstilling, får du vist **Standardindstillingen Tillad** eller **Standardafvis.**
   - Overvej både Diskniveau og Filsystemniveau AccessMask, når du konfigurerer denne indstilling, hvis du f.eks. vil angive Standardafvis, men tillad specifik lagring, skal du tillade både adgang på diskniveau og filsystemniveau, og du skal angive AccessMask til 63.

    :::image type="content" source="images/148609579-a7df650b-7792-4085-b552-500b28a35885.png" alt-text="Standardkode for Tillad eller Standardafvis PowerShell":::

5. Aktivér eller deaktiver Flytbare Storage Access Control: Du kan angive denne værdi til midlertidigt at deaktivere Flytbare Storage Access Control.

    :::image type="content" source="images/148608318-5cda043d-b996-4146-9642-14fccabcb017.png" alt-text="Indstillinger for enhedskontrol":::

   - Når du installerer denne indstilling, får du vist **Aktiveret** eller **Deaktiveret**. Deaktiveret betyder, at flytbare Storage Access Control ikke kører på computeren.

    :::image type="content" source="images/148609685-4c05f002-5cbe-4aab-9245-83e730c5449e.png" alt-text="Aktiveret eller deaktiveret enhedskontrolelement i PowerShell-kode":::

6. Angiv placeringen for en kopi af filen: Hvis du vil have en kopi af filen, når skriveadgangen finder sted, skal du angive den placering, hvor systemet kan gemme kopien.

    Udrul dette sammen med den rette AccessMask og indstilling – se trin 2 ovenfor.

    :::image type="content" source="../../media/define-device-control-policy-rules.png" alt-text="Gruppepolitik – Angiv locaiton for filbeviser":::

## <a name="deploying-and-managing-policy-via-intune-oma-uri"></a>Udrulning og administration af politik via Intune OMA-URI

Funktionen Flytbare Storage Access Control giver dig mulighed for at anvende en politik via OMA-URI på enten bruger eller enhed eller begge dele.

### <a name="licensing-requirements"></a>Licenskrav

Før du kommer i gang med Flytbare Storage Access Control, skal du bekræfte dit [abonnement på Microsoft 365](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=2). Hvis du vil have adgang til og bruge Flytbare Storage Access Control, skal du have Microsoft 365 E3 eller Microsoft 365 E5.

### <a name="permission"></a>Tilladelse

I forbindelse med politikinstallation i Intune skal kontoen have tilladelser til at oprette, redigere, opdatere eller slette enhedskonfigurationsprofiler. Du kan oprette brugerdefinerede roller eller bruge en af de indbyggede roller med disse tilladelser.

- Rolle som politik- og profiladministrator

- Brugerdefineret rolle med tilladelserne Opret/Rediger/Opdater/Læs/Slet/Vis rapporter slået til for profiler til enhedskonfiguration

- Global administrator

### <a name="deploying-policy-via-oma-uri"></a>Installerer politik via OMA-URI

Microsoft Endpoint Manager Administration (<https://endpoint.microsoft.com/>) \> **Enhedskonfigurationsprofiler** \>  \> **Opret profilplatform** \> **: Windows 10 og nyere & profil: Brugerdefineret**

1. Opret en OMA-URI-regel for hver gruppe:

    - OMA-URI:

      `./Vendor/MSFT/Defender/Configuration/DeviceControl/PolicyGroups/%7b**GroupGUID**%7d/GroupData`

      Hvis der f.eks. er et **flytbart lager og en cd/dvd-gruppe** i eksemplet, skal linket være:

      `./Vendor/MSFT/Defender/Configuration/DeviceControl/PolicyGroups/%7b9b28fae8-72f7-4267-a1a5-685f747a7146%7d/GroupData`

    - Datatype: Streng (XML-fil)

      :::image type="content" source="images/xml-data-type-string.png" alt-text="Feltet Datatype på siden Tilføj række" lightbox="images/xml-data-type-string.png":::

2. For hver politik skal du også oprette en OMA-URI:

    - OMA-URI:

      `./Vendor/MSFT/Defender/Configuration/DeviceControl/PolicyRules/%7b**PolicyRuleGUID**%7d/RuleData`

      For **blokskrivnings- og udførelsesadgangen, men tillad godkendte USB-regler** i eksemplet skal linket f.eks. være:

      `./Vendor/MSFT/Defender/Configuration/DeviceControl/PolicyRules/%7bc544a991-5786-4402-949e-a032cb790d0e%7d/RuleData`

    - Datatype: Streng (XML-fil)

    Hvis du vil overvåge filoplysninger for skriveadgang, skal du bruge den rigtige AccessMask med den rigtige indstilling (16); her er eksemplet på [Hent filoplysninger](https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/Intune%20OMA-URI/Audit%20File%20Information.xml).

3. Standard gennemtvingelse: Giver dig mulighed for at angive standardadgang (Afvis eller Tillad) til flytbare medier, hvis der ikke er nogen politik. Du har f.eks. kun en politik (enten Afvis eller Tillad) for RemovableMediaDevices, men du har ikke nogen politik for CdRomDevices eller WpdDevices, og du angiver standardafvis via denne politik, læse/skrive/udføre adgang til CdRomDevices eller WpdDevices blokeres.

    - OMA-URI: `./Vendor/MSFT/Defender/Configuration/DefaultEnforcement`

    - Datatype: Indt

      `DefaultEnforcementAllow = 1`
      `DefaultEnforcementDeny = 2`

    - Når du har installeret denne indstilling, får du vist **Standardindstillingen Tillad** eller **Standardafvis**
    - Overvej både Diskniveau og Filsystemniveau AccessMask, når du konfigurerer denne indstilling, hvis du f.eks. vil angive Standardafvis, men tillad specifik lagring, skal du tillade både adgang på diskniveau og filsystemniveau, og du skal angive AccessMask til 63.

    :::image type="content" source="images/148609590-c67cfab8-8e2c-49f8-be2b-96444e9dfc2c.png" alt-text="Tillad PowerShell-kode til standard gennemtvingelse":::

4. Aktivér eller deaktiver Flytbare Storage Access Control: Du kan angive denne værdi til midlertidigt at deaktivere Flytbare Storage Access Control.

   - OMA-URI: `./Vendor/MSFT/Defender/Configuration/DeviceControlEnabled`

   - Datatype: Indt `Disable: 0`
     `Enable: 1`

   - Når du installerer denne indstilling, får du vist **Aktiveret** eller **Deaktiveret**

    **Deaktiveret** betyder, at der ikke kører en flytbar Storage Access Control politik på computeren

    :::image type="content" source="images/148609770-3e555883-f26f-45ab-9181-3fb1ff7a38ac.png" alt-text="Fjernbar Storage Access Control i PowerShell-kode":::

5. Angiv placeringen for en kopi af filen: Hvis du vil have en kopi af filen, når skriveadgangen finder sted, skal du angive den placering, hvor systemet kan gemme kopien.

    - OMA-URI: `./Vendor/MSFT/Defender/Configuration/DataDuplicationRemoteLocation;**username**;**password**`

    - Datatype: Streng

    Du skal udrulle dette sammen med den rigtige AccessMask og den rigtige indstilling – se trin 2 ovenfor.

    :::image type="content" source="../../media/device-control-oma-uri-edit-row.png" alt-text="Angiv locaiton for filbeviser":::

## <a name="deploying-and-managing-policy-by-using-intune-user-interface"></a>Udrulning og administration af politik ved hjælp af Intune brugergrænseflade

(*Kommer snart!*) Denne funktion er tilgængelig i Microsoft Endpoint Manager Administration (<https://endpoint.microsoft.com/>). Gå til **Endpoint SecurityAttack** >  **Surface** **ReductionCreate** >  Policy. Vælg **Platform: Windows 10 og nyere** med **Profil: Enhedskontrol**.

## <a name="view-device-control-removable-storage-access-control-data-in-microsoft-defender-for-endpoint"></a>Få vist flytbare Storage Access Control data for enhedsstyring i Microsoft Defender for Endpoint

På [Microsoft 365 Defender-portalen](https://security.microsoft.com/advanced-hunting) vises hændelser, der udløses af flytbare Storage Access Control for enhedskontrol. Hvis du vil have adgang til Microsoft 365 sikkerhed, skal du have følgende abonnement:

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

### <a name="what-is-the-removable-storage-media-limitation-for-the-maximum-number-of-usbs"></a>Hvad er begrænsningen for flytbare lagermedier for det maksimale antal USB'er?

Vi har valideret én USB-gruppe med 100.000 medier – op til 7 MB i størrelse. Politikken fungerer i både Intune og GPO uden problemer med ydeevnen.

### <a name="why-does-the-policy-not-work"></a>Hvorfor fungerer politikken ikke?

1. Den mest almindelige årsag er, at der ikke er nogen påkrævet [antimalwareklientversion](/microsoft-365/security/defender-endpoint/device-control-removable-storage-access-control#prepare-your-endpoints).

2. En anden årsag kan være, at XML-filen ikke er formateret korrekt, f.eks. at den korrekte markdown-formatering ikke bruges til tegnet "&" i XML-filen, eller at teksteditoren tilføjer et byterækkefølgetegn (BOM) 0xEF 0xBB 0xBF i starten af filerne, hvilket medfører, at XML-fortolkning ikke fungerer. En enkel løsning er at downloade [eksempelfilen](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) (vælge **Rå** og derefter **Gem som**) og derefter opdatere.

3. Hvis du installerer og administrerer politikken via Gruppepolitik, skal du sørge for at kombinere alle PolicyRule i én XML-fil i en overordnet node, der kaldes PolicyRules, og alle grupper i én XML-fil i en overordnet node kaldet Grupper. Hvis du administrerer via Intune, skal du beholde én PolicyRule én XML-fil, samme ting, én gruppér én XML-fil.

Hvis du stadig ikke arbejder, kan du kontakte os og dele support-cab ved at køre cmd med administratoren: "%programfiles%\Windows Defender\MpCmdRun.exe" -GetFiles

### <a name="there-is-no-configuration-ux-for-define-device-control-policy-groups-and-define-device-control-policy-rules-on-my-group-policy"></a>Der er ingen konfigurations-UX for 'Definer politikgrupper for enhedskontrol' og 'Definer politikregler for enhedskontrol' på mit Gruppepolitik

Vi backporterer ikke Gruppepolitik konfigurations-UX, men du kan stadig hente de relaterede adml- og admx-filer ved at klikke på 'Raw' og 'Gem som' i [filerne WindowsDefender.adml](https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/WindowsDefender.adml) og [WindowsDefender.admx](https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/WindowsDefender.admx).

### <a name="how-can-i-know-whether-the-latest-policy-has-been-deployed-to-the-target-machine"></a>Hvordan kan jeg vide, om den nyeste politik er blevet installeret på destinationscomputeren?

Du kan køre "Get-MpComputerStatus" på PowerShell som administrator. Følgende værdi viser, om den seneste politik er anvendt på destinationscomputeren.

:::image type="icon" source="images/148609885-bea388a9-c07d-47ef-b848-999d794d24b8.png" border="false":::

### <a name="how-can-i-know-which-machine-is-using-out-of-date-antimalware-client-version-in-the-organization"></a>Hvordan ved jeg, hvilken computer der bruger forældet antimalwareklientversion i organisationen?

Du kan bruge følgende forespørgsel til at hente en antimalwareklientversion på Microsoft 365 sikkerhedsportalen:

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
