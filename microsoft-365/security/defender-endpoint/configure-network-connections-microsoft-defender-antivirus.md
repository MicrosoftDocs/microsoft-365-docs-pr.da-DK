---
title: Konfigurere og validere Microsoft Defender Antivirus netværksforbindelser
description: Konfigurer og test din forbindelse til Microsoft Defender Antivirus skybeskyttelsestjeneste.
keywords: antivirus, Microsoft Defender Antivirus, antimalware, sikkerhed, defender, sky, aggressiveness, beskyttelsesniveau
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
ms.date: 02/03/2022
ms.reviewer: mkaminska; pahuijbr
manager: dansimp
ms.collection: M365-security-compliance
ms.openlocfilehash: f29cf5f77acd52a4ff3ccc8384f3c64861e48b64
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/14/2022
ms.locfileid: "63592371"
---
# <a name="configure-and-validate-microsoft-defender-antivirus-network-connections"></a>Konfigurere og validere Microsoft Defender Antivirus netværksforbindelser

**Gælder for:**

- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

For at Microsoft Defender Antivirus beskyttelse, der leveres i skyen, fungerer korrekt, skal dit sikkerhedsteam konfigurere dit netværk for at tillade forbindelser mellem dine slutpunkter og bestemte Microsoft-servere. I denne artikel vises forbindelser, der skal være tilladt for at bruge firewall-reglerne. Den indeholder også en vejledning til validering af din forbindelse. Hvis du konfigurerer beskyttelsen korrekt, sikrer du dig den bedste værdi fra dine skybaserede beskyttelsestjenester.

> [!IMPORTANT]
> Denne artikel indeholder kun oplysninger om konfiguration af netværksforbindelser for Microsoft Defender Antivirus. Hvis du bruger Microsoft Defender til slutpunkt (som omfatter Microsoft Defender Antivirus), skal du se Konfigurer enhedsproxy og [indstillinger for internetforbindelse for Defender til slutpunkt](configure-proxy-internet.md).


> [!NOTE]
> Defender for Endpoint-demowebstedet demo.wd.microsoft.com forældet og fjernes fremover.

## <a name="allow-connections-to-the-microsoft-defender-antivirus-cloud-service"></a>Tillad forbindelser til Microsoft Defender Antivirus-skytjenesten

Den Microsoft Defender Antivirus skytjeneste giver hurtig og stærk beskyttelse til dine slutpunkter. Det er valgfrit at aktivere den skybaserede tjeneste til beskyttelse. Microsoft Defender Antivirus skytjeneste anbefales, fordi den giver vigtig beskyttelse mod malware på dine slutpunkter og dit netværk. Du kan få mere at [](enable-cloud-protection-microsoft-defender-antivirus.md) vide under Aktivér beskyttelse, der leveres i skyen, for at aktivere tjenesten med Intune-, Microsoft Endpoint Configuration Manager-, Gruppepolitik-, PowerShell-cmdlet'er eller individuelle klienter i Windows Sikkerhed-appen.

Når du har aktiveret tjenesten, skal du konfigurere dit netværk eller din firewall til at tillade forbindelser mellem netværk og dine slutpunkter. Da din beskyttelse er en skybaseret tjeneste, skal computere have adgang til internettet og nå Microsofts skytjenester. Du må ikke udelade URL-adressen `*.blob.core.windows.net` fra nogen form for netværksinspektion.

> [!NOTE]
> Den Microsoft Defender Antivirus skytjeneste leverer opdateret beskyttelse til dit netværk og dine slutpunkter. Skytjenesten bør ikke betragtes som kun beskyttelse af dine filer, der er gemt i skyen; I stedet bruger skytjenesten distribuerede ressourcer og maskinlæring til at levere beskyttelse til dine slutpunkter hurtigere end de traditionelle sikkerhedsintelligensopdateringer.

## <a name="services-and-urls"></a>Tjenester og URL-adresser

Tabellen i dette afsnit viser tjenester og deres tilknyttede webadresser (URL-adresser).

Sørg for, at der ikke er nogen firewall eller regler for netværksfiltrering, der afviser adgang til disse URL-adresser. Ellers skal du oprette en tilladelsesregel specifikt for disse URL-adresser (undtagen URL-adressen `*.blob.core.windows.net`). URL-adresserne i følgende tabel bruger port 443 til kommunikation.

<br/><br/>

|Tjeneste og beskrivelse|URL-adresse|
|---|---|
|Microsoft Defender Antivirus sky-leveret beskyttelsestjeneste kaldes for Microsoft Active Protection Service (MAPS).<p> Den Microsoft Defender Antivirus bruger MAPS-tjenesten til at levere beskyttelse i skyen.|`*.wdcp.microsoft.com` <p> `*.wdcpalt.microsoft.com` <p> `*.wd.microsoft.com`|
|MICROSOFT Update Service (MU) og Windows Update Service (WU) <p>Disse tjenester giver adgang til sikkerhedsintelligens og produktopdateringer.|`*.update.microsoft.com` <p> `*.delivery.mp.microsoft.com`<p> `*.windowsupdate.com` <p> Du kan finde flere oplysninger [i Forbindelsesslutpunkter for Windows Opdatering](/windows/privacy/manage-windows-1709-endpoints#windows-update)|
|Sikkerhedsintelligensopdateringer Alternativ downloadplacering (ADL)<p>Dette er en alternativ placering til Microsoft Defender Antivirus sikkerhedsintelligensopdateringer, hvis den installerede sikkerhedsintelligens er forældet (syv eller flere dage bagud).|`*.download.microsoft.com` <p> `*.download.windowsupdate.com`<p>  `go.microsoft.com`<p> `https://fe3cr.delivery.mp.microsoft.com/ClientWebService/client.asmx`|
|Lagring af malwareindsendelser <p>Dette er en overførselsplacering for filer, der er sendt til Microsoft via indsendelsesformularen eller automatisk indsendelse af eksempler.|`ussus1eastprod.blob.core.windows.net` <p> `ussus2eastprod.blob.core.windows.net` <p> `ussus3eastprod.blob.core.windows.net` <p> `ussus4eastprod.blob.core.windows.net` <p> `wsus1eastprod.blob.core.windows.net` <p> `wsus2eastprod.blob.core.windows.net` <p> `ussus1westprod.blob.core.windows.net` <p> `ussus2westprod.blob.core.windows.net` <p> `ussus3westprod.blob.core.windows.net` <p> `ussus4westprod.blob.core.windows.net` <p> `wsus1westprod.blob.core.windows.net` <p> `wsus2westprod.blob.core.windows.net` <p> `usseu1northprod.blob.core.windows.net` <p> `wseu1northprod.blob.core.windows.net` <p> `usseu1westprod.blob.core.windows.net` <p> `wseu1westprod.blob.core.windows.net` <p> `ussuk1southprod.blob.core.windows.net` <p> `wsuk1southprod.blob.core.windows.net` <p> `ussuk1westprod.blob.core.windows.net` <p> `wsuk1westprod.blob.core.windows.net`|
|Liste over tilbagekaldte certifikater <p> Windows denne liste, mens du opretter SSL-forbindelsen til KORT til opdatering af liste over tilbagekaldte certifikater.|`http://www.microsoft.com/pkiops/crl/` <p> `http://www.microsoft.com/pkiops/certs` <p> `http://crl.microsoft.com/pki/crl/products` <p> `http://www.microsoft.com/pki/certs`|
|Symbol Store <p>Microsoft Defender Antivirus bruge Symbol-Store til at gendanne visse kritiske filer under afhjælpningsflows.|`https://msdl.microsoft.com/download/symbols`|
|Universal GDPR-klient <p> Windows denne klient til at sende diagnostiske klientdata. <p> Microsoft Defender Antivirus anvender den generelle forordning om databeskyttelse til produktkvalitet og overvågningsformål.|Opdateringen bruger SSL (TCP Port 443) til at downloade manifester og uploade diagnostiske data til Microsoft, der bruger følgende DNS-slutpunkter: <p> `vortex-win.data.microsoft.com` <p> `settings-win.data.microsoft.com`|


## <a name="validate-connections-between-your-network-and-the-cloud"></a>Valider forbindelser mellem dit netværk og skyen

Når du har tilladelse til de viste URL-adresser, skal du teste, om du har forbindelse Microsoft Defender Antivirus skytjenesten. Test URL-adresserne rapporterer og modtager oplysninger korrekt for at sikre, at du er fuldt beskyttet.

### <a name="use-the-cmdline-tool-to-validate-cloud-delivered-protection"></a>Brug cmdline-værktøjet til at validere beskyttelse, der leveres i skyen

Brug følgende argument med Microsoft Defender Antivirus (`mpcmdrun.exe`) for at bekræfte, at dit netværk kan kommunikere med Microsoft Defender Antivirus skytjenesten:

```console
"%ProgramFiles%\Windows Defender\MpCmdRun.exe" -ValidateMapsConnection
```

> [!NOTE]
> Åbn Kommandoprompt som administrator. Højreklik på elementet i menuen Start, **klik** på Kør **som administrator, og** klik **på Ja** i tilladelsesprompten. Denne kommando virker kun på Windows 10, version 1703 eller nyere eller Windows 11.

Du kan få mere at [vide Microsoft Defender Antivirus Administrer mpcmdrun.exe mpcmdrun.exe kommandolinjeværktøjet](command-line-arguments-microsoft-defender-antivirus.md).

### <a name="attempt-to-download-a-fake-malware-file-from-microsoft"></a>Forsøg at downloade en falsk malwarefil fra Microsoft

Du kan downloade en eksempelfil, Microsoft Defender Antivirus registrerer og blokerer, hvis du har forbindelse til skyen. Besøg [https://aka.ms/ioavtest](https://aka.ms/ioavtest) for at downloade filen.

> [!NOTE]
> Den hentede fil er ikke præcis malware. Det er en falsk fil, der er udviklet til at teste, om du har forbindelse til skyen.

Hvis du har forbindelse korrekt, får du vist en advarsel, Microsoft Defender Antivirus besked.

Hvis du bruger Microsoft Edge, får du også vist en meddelelse:

:::image type="content" source="../../media/wdav-bafs-edge.png" alt-text="Skærmbillede af meddelelse om, at der blev fundet malware i Azure IoT Edge.":::

Der vises en lignende meddelelse, hvis du bruger Internet Explorer:

:::image type="content" source="../../media/wdav-bafs-ie.png" alt-text="Microsoft Defender AV-besked om, at der blev fundet malware.":::

#### <a name="view-the-fake-malware-detection-in-your-windows-security-app"></a>Se registrering af falske malware i din Windows Sikkerhed-app

1. På proceslinjen skal du vælge Skjold-ikonet og åbne **Windows Sikkerhed** app. Du kan også søge **i Start** for *Security*.

2. Vælg **Virusbeskyttelse& trusselsbeskyttelse**, og vælg derefter **Historik over beskyttelse**.

3. Under sektionen **Trusler i karantæne skal** du vælge **Se hele oversigten for** at se den registrerede falske malware.

   > [!NOTE]
   > Versioner af Windows 10 før version 1703 har en anden brugergrænseflade. Se [Microsoft Defender Antivirus i Windows Sikkerhed appen](microsoft-defender-security-center-antivirus.md).

   I Windows vises også et [klienthændelses-Windows Defender 1116](troubleshoot-microsoft-defender-antivirus.md).

## <a name="see-also"></a>Se også

- [Konfigurer enhedsproxy og indstillinger for internetforbindelse for Microsoft Defender til Slutpunkt](configure-proxy-internet.md)
- [Brug Gruppepolitik til at konfigurere og administrere Microsoft Defender Antivirus](use-group-policy-microsoft-defender-antivirus.md)
- [Vigtige ændringer af Microsoft Active Protection Services-slutpunkt](https://techcommunity.microsoft.com/t5/Configuration-Manager-Archive/Important-changes-to-Microsoft-Active-Protection-Service-MAPS/ba-p/274006) 