---
title: Office TLS-certifikatændringer
description: Sådan forbereder du kommende ændringer af Office TLS-certifikater.
author: pshelton-skype
ms.author: pshelton
manager: toddbeckett
ms.topic: article
audience: Developer
ms.date: 3/7/2022
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.openlocfilehash: d5390c97c097bdbf52e496336e3a239d975a88aa
ms.sourcegitcommit: 2aa5c026cc06ed39a9c1c2bcabd1f563bf5a1859
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/09/2022
ms.locfileid: "66696222"
---
# <a name="office-tls-certificate-changes"></a>Ændringer i Office TLS-certifikatet

Microsoft 365 opdaterer tjenester, der giver mulighed for beskeder, møder, telefoni, stemme og video, for at bruge TLS-certifikater fra et andet sæt rodcertifikatcentre. Denne ændring foretages, fordi det aktuelle rodnøglecenter udløber i maj 2025.

Berørte produkter omfatter:
- Microsoft Teams
- Skype
- Skype for Business Online
- Microsoft Dynamics 365
- Gruppér
- Kaizala
- Azure Communication Services

Berørte slutpunkter omfatter (men er ikke begrænset til):
- *.teams.microsoft.com
- *.skype.com
- *.skypeforbusiness.com
- *.groupme.com
- *.communication.azure.com
- *.operatorconnect.microsoft.com

Derudover foretager Teams og Skype for Business Online-slutpunkter i nationale cloudforekomster af Microsoft 365 i US Government den samme ændring, hvilket påvirker slutpunkter som f.eks.:
- *.gcc.teams.microsoft.com
- *.dod.teams.microsoft.us
- *.gov.teams.microsoft.us
- *.online.dod.skypeforbusiness.us
- *.online.gov.skypeforbusiness.us
- *.um-dod.office365.us
- *.um.office365.us

Denne ændring påvirker ikke certifikater, domæner eller tjenester, der bruges i de nationale cloudforekomster af Microsoft 365 i Kina eller Tyskland.

Alle certifikatoplysninger i denne artikel blev tidligere leveret i [Microsoft 365-krypteringskæder](./encryption-office-365-certificate-chains.md) senest i oktober 2020.

## <a name="when-will-this-change-happen"></a>Hvornår sker denne ændring?

Tjenesterne begyndte overgangen til de nye rodnøglecentre i januar 2022 og fortsætter til oktober 2022.

## <a name="what-is-changing"></a>Hvad ændrer sig?

I dag kædes de fleste af de TLS-certifikater, der bruges af Microsoft 365-tjenester, sammen med følgende rodnøglecenter:

| Almindeligt navn på nøglecenteret | Aftryk (SHA1) |
|--|--|
| [Baltimore CyberTrust-rod](https://cacerts.digicert.com/BaltimoreCyberTrustRoot.crt) | d4de20d05e66fc53fe1a50882c78db2852cae474 |

med en af følgende mellemliggende nøglecentre:

| Almindeligt navn på nøglecenteret | Aftryk (SHA1) |
|--|--|
| [Microsoft RSA TLS CA 01](https://www.microsoft.com/pki/mscorp/Microsoft%20RSA%20TLS%20CA%2001.crt) | 703d7a8f0ebf55aaa59f98eaf4a206004eb2516a |
| [Microsoft RSA TLS CA 02](https://www.microsoft.com/pki/mscorp/Microsoft%20RSA%20TLS%20CA%2002.crt) | b0c2d2d13cdd56cdaa6ab6e2c04440be4a429c75 |

Nye TLS-certifikater, der bruges af Microsoft 365-tjenester, kædes nu sammen med en af følgende rodnøglecentre:

| Almindeligt navn på nøglecenteret | Aftryk (SHA1) |
|--|--|
| [DigiCert Global Root G2](https://cacerts.digicert.com/DigiCertGlobalRootG2.crt) | df3c24f9bfd666761b268073fe06d1cc8d4f82a4 |
| [Microsoft RSA Root Certificate Authority 2017](https://www.microsoft.com/pkiops/certs/Microsoft%20RSA%20Root%20Certificate%20Authority%202017.crt) | 73a5e64a3bff8316ff0edccc618a906e4eae4d74 | 
| [Microsoft ECC Root Certificate Authority 2017](https://www.microsoft.com/pkiops/certs/Microsoft%20ECC%20Root%20Certificate%20Authority%202017.crt) | 999a64c37ff47d9fab95f14769891460eec4c3c5 |

med en af følgende mellemliggende nøglecentre:

| Almindeligt navn på nøglecenteret | Aftryk (SHA1) |
|--|--|
| [Microsoft Azure TLS udstedende CA 01](https://www.microsoft.com/pkiops/certs/Microsoft%20Azure%20TLS%20Issuing%20CA%2001%20-%20xsign.crt) | 2f2877c5d778c31e0f29c7e371df5471bd673173 |
| [Microsoft Azure TLS udstedende CA 02](https://www.microsoft.com/pkiops/certs/Microsoft%20Azure%20TLS%20Issuing%20CA%2002%20-%20xsign.crt) | e7eea674ca718e3befd90858e09f8372ad0ae2aa |
| [Microsoft Azure TLS udstedende CA 05](https://www.microsoft.com/pkiops/certs/Microsoft%20Azure%20TLS%20Issuing%20CA%2005%20-%20xsign.crt) | 6c3af02e7f269aa73afd0eff2a88a4a1f04ed1e5 |
| [Microsoft Azure TLS udstedende CA 06](https://www.microsoft.com/pkiops/certs/Microsoft%20Azure%20TLS%20Issuing%20CA%2006%20-%20xsign.crt) | 30e01761ab97e59a06b41ef20af6f2de7ef4f7b0 |

Dette er f.eks. et gyldigt certifikat med en af de nye certifikatkæder:

![Teams TLS-certifikatkæde](../media/teams-tls-certificate-chain.png)

## <a name="will-this-change-affect-me"></a>Vil denne ændring påvirke mig?

Der er stor tillid til rodnøglecenteret "DigiCert Global Root G2" fra operativsystemer, herunder Windows, macOS, Android og iOS og browsere som f.eks. Microsoft Edge, Chrome, Safari og Firefox. Vi forventer, at **de fleste Microsoft 365-kunder ikke påvirkes**. 

Dit **program kan dog blive påvirket, hvis det eksplicit angiver en liste over acceptable nøglecentre**. Denne fremgangsmåde kaldes "fastgørelse af certifikat". Kunder, der ikke har de nye rodnøglecentre på deres liste over acceptable nøglecentre, modtager certifikatvalideringsfejl, som kan påvirke tilgængeligheden eller funktionen af dit program.

Her er nogle måder at registrere, om dit program kan blive påvirket:

- Søg i kildekoden efter aftryk, almindeligt navn eller andre egenskaber for en af de mellemliggende nøglecentre, der findes [her](https://www.microsoft.com/pki/mscorp/cps/default.htm). Hvis der er et match, påvirkes dit program. Du kan løse dette problem ved at opdatere kildekoden for at tilføje egenskaberne for de nye nøglecentre. Som bedste praksis skal du sikre, at nøglecentre kan tilføjes eller redigeres med kort varsel. I nogle tilfælde kræver brancheregler, at CA-certifikater erstattes inden for syv dage, så programmer, der implementerer fastgørelse af certifikater, skal reagere hurtigt på disse ændringer.

- .NET viser `System.Net.ServicePointManager.ServerCertificateValidationCallback` tilbagekaldsfunktionerne `System.Net.HttpWebRequest.ServerCertificateValidationCallback` og , som gør det muligt for udviklere at bruge brugerdefineret logik til at afgøre, om certifikater er gyldige i stedet for at være afhængige af Windows-standardcertifikatlageret. En udvikler kan tilføje logik, der søger efter et bestemt almindeligt navn eller aftryk eller kun tillader et bestemt rodnøglecenter, f.eks. "Baltimore CyberTrust Root". Hvis dit program bruger disse tilbagekaldsfunktioner, skal du sørge for, at det accepterer både de gamle og nye rod- og mellemliggende nøglecentre.

- Oprindelige programmer bruger `WINHTTP_CALLBACK_STATUS_SENDING_REQUEST`muligvis , som gør det muligt for oprindelige programmer at implementere brugerdefineret certifikatvalideringslogik. Brugen af denne meddelelse er sjælden og kræver en betydelig mængde brugerdefineret kode at implementere. På samme måde som ovenstående skal du sikre, at dit program accepterer både de gamle og nye rodnøglecentre og mellemliggende nøglecentre. 

- Hvis du bruger et program, der kan integreres med Microsoft Teams, Skype, Skype for Business Online eller Microsoft Dynamics-API'er, og du er usikker på, om der bruges certifikatfastgørelse, skal du kontakte programleverandøren.

- Forskellige operativsystemer og sprogkørsler, der kommunikerer med Azure-tjenester, kan kræve andre trin for at bygge og validere de nye certifikatkæder korrekt:
   - **Linux**: Mange distributioner kræver, at du føjer nøglecentre til `/etc/ssl/certs`. Du kan finde specifikke instruktioner i dokumentationen til distributionen.
   - **Java**: Sørg for, at Java-nøglelageret indeholder de nøglecentre, der er angivet ovenfor.
   - **Windows, der kører i afbrudte miljøer**: Systemer, der kører i frakoblede miljøer, skal have de nye rodnøglecentre føjet til deres `Trusted Root Certification Authorities` lager, og de nye mellemliggende nøglecentre skal føjes til deres `Intermediate Certification Authorities` lager.
   - **Android**: Se dokumentationen til din enhed og version af Android.
   - **IoT- eller integrerede enheder**: Integrerede enheder, f.eks. tv-sættopbokse, leveres ofte med et begrænset sæt rodnøglecentercertifikater og har ingen nem måde at opdatere certifikatlageret på. Hvis du skriver kode til eller administrerer installationer af brugerdefinerede integrerede enheder eller IoT-enheder, skal du sørge for, at enhederne har tillid til de nye rodnøglecentre. Du skal muligvis kontakte enhedsproducenten.

- Hvis du har et miljø, hvor firewallregler kun tillader udgående opkald til bestemte slutpunkter, skal du tillade følgende URL-adresser til certifikattilbagekaldelsesliste (CRL) eller OCSP (Online Certificate Status Protocol):
   - `http://crl3.digicert.com`
   - `http://crl4.digicert.com`
   - `http://ocsp.digicert.com`
   - `http://crl.microsoft.com`
   - `http://oneocsp.microsoft.com`
   - `http://ocsp.msocsp.com`
   - `http://www.microsoft.com/pkiops`

- Hvis du påvirkes af denne ændring, kan du få vist fejlmeddelelser, der afhænger af den type miljø, du kører i, og det scenarie, du er påvirket af. Kontrollér Windows Application-hændelseslogge, CAPI2-hændelseslogge og brugerdefinerede programlogge for meddelelser, der ligner:
   ```output
   An operation failed because the following certificate has validation errors:
   
   Subject Name: CN=teams.microsoft.com
   Issuer Name: CN=Microsoft Azure TLS Issuing CA 01, O=Microsoft Corporation, C=US
   
   Errors:
   
   The root of the certificate chain is not a trusted root authority.
   ```

## <a name="when-can-i-retire-the-old-ca-information"></a>Hvornår kan jeg trække de gamle ca-oplysninger tilbage?

Det aktuelle rodnøglecenter, det mellemliggende nøglecenter og bladcertifikaterne tilbagekaldes ikke. De eksisterende fælles nøglecenternavne og/eller aftryk vil være påkrævet indtil mindst oktober 2023 baseret på eksisterende certifikaters levetid.

## <a name="known-issues"></a>Kendte problemer

I meget sjældne tilfælde kan virksomhedsbrugere få vist certifikatvalideringsfejl, hvor rodnøglecenteret "DigiCert Global Root G2" vises som tilbagekaldt. Dette skyldes en kendt Windows-fejl under begge følgende betingelser:

- Rodnøglecenteret findes i [CurrentUser\Root-certifikatlageret](/windows/win32/seccrypto/system-store-locations#cert_system_store_current_user) og mangler `NotBeforeFileTime` egenskaberne og `NotBeforeEKU`
- Rodnøglecenteret findes i [certifikatlageret LocalMachine\AuthRoot,](/windows/win32/seccrypto/system-store-locations#cert_system_store_local_machine) men har både egenskaberne `NotBeforeFileTime` og `NotBeforeEKU`
- Rodnøglecenteret er IKKE i [LocalMachine\Root Certificate Store](/windows/win32/seccrypto/system-store-locations#cert_system_store_local_machine)

Alle bladcertifikater, der er udstedt fra dette rodnøglecenter efter , `NotBeforeFileTime` vises tilbagekaldt. 

Administratorer kan identificere og foretage fejlfinding af problemet ved at undersøge CAPI2-logfilen for denne fejl:

```text
Log Name:      Microsoft-Windows-CAPI2/Operational
Source:        Microsoft-Windows-CAPI2
Date:          6/23/2022 8:36:39 AM
Event ID:      11
Task Category: Build Chain
Level:         Error
[...]
        <ChainElement>
          <Certificate fileRef="DF3C24F9BFD666761B268073FE06D1CC8D4F82A4.cer" subjectName="DigiCert Global Root G2" />
          [...]
          <TrustStatus>
            <ErrorStatus value="4000024" CERT_TRUST_IS_REVOKED="true" CERT_TRUST_IS_UNTRUSTED_ROOT="true" CERT_TRUST_IS_EXPLICIT_DISTRUST="true" />
            <InfoStatus value="10C" CERT_TRUST_HAS_NAME_MATCH_ISSUER="true" CERT_TRUST_IS_SELF_SIGNED="true" CERT_TRUST_HAS_PREFERRED_ISSUER="true" />
          </TrustStatus>
          [...]
          <RevocationInfo freshnessTime="PT0S">
            <RevocationResult value="80092010">The certificate is revoked.</RevocationResult>
          </RevocationInfo>
        </ChainElement>
      </CertificateChain>
      <EventAuxInfo ProcessName="Teams.exe" />
      <Result value="80092010">The certificate is revoked.</Result>
```
Bemærk tilstedeværelsen af elementet `CERT_TRUST_IS_EXPLICIT_DISTRUST="true"` . 

Du kan bekræfte, at der findes to kopier af rodnøglecenteret med forskellige `NotBeforeFileTime` egenskaber, ved at køre følgende `certutil` kommandoer og sammenligne outputtet:

```
certutil -store -v authroot DF3C24F9BFD666761B268073FE06D1CC8D4F82A4
certutil -user -store -v root DF3C24F9BFD666761B268073FE06D1CC8D4F82A4
```

En bruger kan løse problemet ved at slette kopien af rodnøglecenteret i certifikatlageret `CurrentUser\Root` ved at gøre følgende:
```
certutil -user -delstore root DF3C24F9BFD666761B268073FE06D1CC8D4F82A4
```
Eller 
```
reg delete HKCU\SOFTWARE\Microsoft\SystemCertificates\Root\Certificates\DF3C24F9BFD666761B268073FE06D1CC8D4F82A4 /f
```
Den første tilgang opretter en Windows-dialogboks, som en bruger skal klikke sig igennem, mens den anden fremgangsmåde ikke gør det. 