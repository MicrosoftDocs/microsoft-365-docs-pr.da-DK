---
title: Konfigurer og valider Microsoft Defender Antivirus netværksforbindelser
description: Konfigurer og test din forbindelse til tjenesten Microsoft Defender Antivirus cloudbeskyttelse.
keywords: antivirus, Microsoft Defender Antivirus, antimalware, sikkerhed, defender, cloud, aggressivitet, beskyttelsesniveau
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.topic: article
ms.custom: nextgen
ms.date: 06/28/2022
ms.reviewer: mkaminska; pahuijbr
manager: dansimp
ms.collection: M365-security-compliance
ms.openlocfilehash: e06b2a37f45ccf0febc35e31d33ece55c03e3303
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/29/2022
ms.locfileid: "66492054"
---
# <a name="configure-and-validate-microsoft-defender-antivirus-network-connections"></a>Konfigurer og valider Microsoft Defender Antivirus netværksforbindelser

**Gælder for:**

- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Microsoft Defender Antivirus

**Platforme**
- Windows

For at sikre at Microsoft Defender Antivirus cloud-leveret beskyttelse fungerer korrekt, skal dit sikkerhedsteam konfigurere dit netværk for at tillade forbindelser mellem dine slutpunkter og visse Microsoft-servere. Denne artikel indeholder en liste over forbindelser, der skal være tilladt ved brug af firewallreglerne. Den indeholder også instruktioner til validering af forbindelsen. Hvis du konfigurerer din beskyttelse korrekt, sikrer du, at du får den bedste værdi fra dine skybaserede beskyttelsestjenester.

> [!IMPORTANT]
> Denne artikel indeholder oplysninger om konfiguration af netværksforbindelser kun til Microsoft Defender Antivirus. Hvis du bruger Microsoft Defender for Endpoint (hvilket omfatter Microsoft Defender Antivirus), skal du se [Konfigurer indstillinger for enhedsproxy og internetforbindelse for Defender for Endpoint](configure-proxy-internet.md).


> [!NOTE]
> Demowebstedet Defender for Endpoint på demo.wd.microsoft.com frarådes og fjernes fremover.

## <a name="allow-connections-to-the-microsoft-defender-antivirus-cloud-service"></a>Tillad forbindelser til cloudtjenesten Microsoft Defender Antivirus

Cloudtjenesten Microsoft Defender Antivirus sikrer hurtig og stærk beskyttelse af dine slutpunkter. Det er valgfrit at aktivere den skybaserede beskyttelsestjeneste. Cloudtjenesten Microsoft Defender Antivirus anbefales, da den giver vigtig beskyttelse mod malware på dine slutpunkter og netværk. Du kan finde flere oplysninger under [Aktivér skybaseret beskyttelse](enable-cloud-protection-microsoft-defender-antivirus.md) for at aktivere tjenesten med Intune, Microsoft Endpoint Configuration Manager, Gruppepolitik, PowerShell-cmdlet'er eller individuelle klienter i appen Windows Sikkerhed.

Når du har aktiveret tjenesten, skal du konfigurere netværket eller firewallen for at tillade forbindelser mellem netværket og dine slutpunkter. Da din beskyttelse er en cloudtjeneste, skal computere have adgang til internettet og kontakte Microsofts cloudtjenester. Udelad ikke URL-adressen `*.blob.core.windows.net` fra nogen form for netværksinspektion.

> [!NOTE]
> Cloudtjenesten Microsoft Defender Antivirus leverer opdateret beskyttelse til dit netværk og dine slutpunkter. Cloudtjenesten bør ikke betragtes som kun beskyttelse af dine filer, der er gemt i cloudmiljøet. Cloudtjenesten bruger i stedet distribuerede ressourcer og maskinel indlæring til at levere beskyttelse til dine slutpunkter hurtigere end de traditionelle Sikkerhedsintelligensopdateringer.

## <a name="services-and-urls"></a>Tjenester og URL-adresser

Tabellen i dette afsnit indeholder en liste over tjenester og deres tilknyttede webstedsadresser (URL-adresser).

Sørg for, at der ikke er nogen regler for firewall- eller netværksfiltrering, der nægter adgang til disse URL-adresser. Ellers skal du oprette en tilladelsesregel specifikt for disse URL-adresser (undtagen URL-adressen `*.blob.core.windows.net`). URL-adresserne i følgende tabel bruger port 443 til kommunikation.

<br/><br/>

|Tjeneste og beskrivelse|URL|
|---|---|
|Microsoft Defender Antivirus cloud-leveret beskyttelsestjeneste kaldes Microsoft Active Protection Service (MAPS).<p> Microsoft Defender Antivirus bruger MAPS-tjenesten til at yde skybaseret beskyttelse.|`*.wdcp.microsoft.com` <p> `*.wdcpalt.microsoft.com` <p> `*.wd.microsoft.com`|
|Microsoft Update Service (MU) og Windows Update Service (WU) <p>Disse tjenester tillader sikkerhedsintelligens og produktopdateringer.|`*.update.microsoft.com` <p> `*.delivery.mp.microsoft.com`<p> `*.windowsupdate.com` <p> Du kan finde flere oplysninger under [Forbindelsesslutpunkter for Windows Update](/windows/privacy/manage-windows-1709-endpoints#windows-update)|
|ADL (Security Intelligence Updates Alternate Download Location)<p>Dette er en alternativ placering til Microsoft Defender Antivirus Security intelligence-opdateringer, hvis den installerede Sikkerhedsintelligens er forældet (syv eller flere dage bagud).|`*.download.microsoft.com` <p> `*.download.windowsupdate.com`<p>  `go.microsoft.com`<p> `https://www.microsoft.com/security/encyclopedia/adlpackages.aspx` <p> `https://definitionupdates.microsoft.com/download/DefinitionUpdates/` <p> `https://fe3cr.delivery.mp.microsoft.com/ClientWebService/client.asmx`|
|Lager til indsendelse af malware <p>Dette er en placering til overførsel af filer, der er sendt til Microsoft via indsendelsesformularen eller automatisk eksempelafsendelse.|`ussus1eastprod.blob.core.windows.net` <p> `ussus2eastprod.blob.core.windows.net` <p> `ussus3eastprod.blob.core.windows.net` <p> `ussus4eastprod.blob.core.windows.net` <p> `wsus1eastprod.blob.core.windows.net` <p> `wsus2eastprod.blob.core.windows.net` <p> `ussus1westprod.blob.core.windows.net` <p> `ussus2westprod.blob.core.windows.net` <p> `ussus3westprod.blob.core.windows.net` <p> `ussus4westprod.blob.core.windows.net` <p> `wsus1westprod.blob.core.windows.net` <p> `wsus2westprod.blob.core.windows.net` <p> `usseu1northprod.blob.core.windows.net` <p> `wseu1northprod.blob.core.windows.net` <p> `usseu1westprod.blob.core.windows.net` <p> `wseu1westprod.blob.core.windows.net` <p> `ussuk1southprod.blob.core.windows.net` <p> `wsuk1southprod.blob.core.windows.net` <p> `ussuk1westprod.blob.core.windows.net` <p> `wsuk1westprod.blob.core.windows.net`|
|Liste over tilbagekaldte certifikater (CRL) <p> Windows bruger denne liste, mens du opretter SSL-forbindelsen til MAPS til opdatering af liste over tilbagekaldte certifikater.|`http://www.microsoft.com/pkiops/crl/` <p> `http://www.microsoft.com/pkiops/certs` <p> `http://crl.microsoft.com/pki/crl/products` <p> `http://www.microsoft.com/pki/certs`|
|Symbollager <p>Microsoft Defender Antivirus bruger Symbol Store til at gendanne visse kritiske filer under afhjælpningsflows.|`https://msdl.microsoft.com/download/symbols`|
|Universel GDPR-klient <p> Windows bruger denne klient til at sende klientdiagnosticeringsdata. <p> Microsoft Defender Antivirus bruger den generelle forordning om databeskyttelse til produktkvalitet og overvågning.|Opdateringen bruger SSL (TCP Port 443) til at downloade manifester og overføre diagnosticeringsdata til Microsoft, der bruger følgende DNS-slutpunkter: <p> `vortex-win.data.microsoft.com` <p> `settings-win.data.microsoft.com`|


## <a name="validate-connections-between-your-network-and-the-cloud"></a>Valider forbindelser mellem dit netværk og cloudmiljøet

Når du har tilladt de angivne URL-adresser, skal du teste, om du har forbindelse til cloudtjenesten Microsoft Defender Antivirus. Test, at URL-adresserne rapporterer korrekt og modtager oplysninger for at sikre, at du er fuldt beskyttet.

### <a name="use-the-cmdline-tool-to-validate-cloud-delivered-protection"></a>Brug cmdlineværktøjet til at validere skybaseret beskyttelse

Brug følgende argument sammen med kommandolinjeværktøjet Microsoft Defender Antivirus (`mpcmdrun.exe`) til at bekræfte, at dit netværk kan kommunikere med cloudtjenesten Microsoft Defender Antivirus:

```console
"%ProgramFiles%\Windows Defender\MpCmdRun.exe" -ValidateMapsConnection
```

> [!NOTE]
> Åbn kommandoprompten som administrator. Højreklik på elementet i menuen **Start** , klik på **Kør som administrator** , og klik på **Ja** i tilladelsesprompten. Denne kommando fungerer kun på Windows 10, version 1703 eller nyere eller Windows 11.

Du kan få flere oplysninger under [Administrer Microsoft Defender Antivirus med kommandolinjeværktøjet mpcmdrun.exe](command-line-arguments-microsoft-defender-antivirus.md).

### <a name="attempt-to-download-a-fake-malware-file-from-microsoft"></a>Forsøg på at downloade en falsk malwarefil fra Microsoft

Du kan downloade en eksempelfil, som Microsoft Defender Antivirus registrerer og blokerer, hvis du har korrekt forbindelse til cloudmiljøet. Besøg [https://aka.ms/ioavtest1](https://aka.ms/ioavtest1) for at downloade filen.

> [!NOTE]
> Den downloadede fil er ikke ligefrem malware. Det er en falsk fil, der er designet til at teste, om du har korrekt forbindelse til cloudmiljøet.

Hvis du har forbindelse korrekt, får du vist en advarsel fra Microsoft Defender Antivirus.

Hvis du bruger Microsoft Edge, får du også vist en meddelelse:

:::image type="content" source="../../media/wdav-bafs-edge.png" alt-text="Meddelelsen om, at malware blev fundet i Edge" lightbox="../../media/wdav-bafs-edge.png":::

Der forekommer en lignende meddelelse, hvis du bruger Internet Explorer:

:::image type="content" source="../../media/wdav-bafs-ie.png" alt-text="Microsoft Defender AV-meddelelsen om, at malware blev fundet" lightbox="../../media/wdav-bafs-ie.png":::

#### <a name="view-the-fake-malware-detection-in-your-windows-security-app"></a>Få vist registrering af falsk malware i din Windows Sikkerhed-app

1. Vælg ikonet Skjold på proceslinjen, og åbn appen **Windows Sikkerhed**. Du kan også søge i **Start** efter *sikkerhed*.

2. Vælg **Virus & trusselsbeskyttelse**, og vælg derefter **Beskyttelseshistorik**.

3. Under afsnittet **Karantænetrusler** skal du vælge **Se hele historikken** for at se den registrerede falske malware.

   > [!NOTE]
   > Versioner af Windows 10 før version 1703 har en anden brugergrænseflade. Se [Microsoft Defender Antivirus i Windows Sikkerhed-appen](microsoft-defender-security-center-antivirus.md).

   Windows-hændelsesloggen viser også [Windows Defender klienthændelses-id 1116](troubleshoot-microsoft-defender-antivirus.md).

    > [!TIP]
    > Hvis du leder efter antivirusrelaterede oplysninger til andre platforme, skal du se:
    > - [Angiv indstillinger for Microsoft Defender for Endpoint på macOS-](mac-preferences.md)
    > - [Microsoft Defender for Endpoint på Mac](microsoft-defender-endpoint-mac.md)
    > - [Politikindstillinger for macOS Antivirus for Microsoft Defender Antivirus for Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
    > - [Angiv indstillinger for Microsoft Defender for Endpoint på Linux](linux-preferences.md)
    > - [Microsoft Defender for Endpoint på Linux](microsoft-defender-endpoint-linux.md)
    > - [Konfigurer Defender for Endpoint på Android-funktioner](android-configure.md)
    > - [Konfigurer Microsoft Defender for Endpoint på iOS-funktioner](ios-configure-features.md)


## <a name="see-also"></a>Se også

- [Konfigurer indstillingerne for enhedsproxy og internetforbindelse for Microsoft Defender for Endpoint](configure-proxy-internet.md)
- [Brug Gruppepolitik indstillinger til at konfigurere og administrere Microsoft Defender Antivirus](use-group-policy-microsoft-defender-antivirus.md)
- [Vigtige ændringer af Slutpunktet for Microsoft Active Protection Services](https://techcommunity.microsoft.com/t5/Configuration-Manager-Archive/Important-changes-to-Microsoft-Active-Protection-Service-MAPS/ba-p/274006) 
