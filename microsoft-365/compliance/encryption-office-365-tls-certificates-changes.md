---
title: Office ændringer af TLS-certifikat
description: Sådan forberedes du til kommende ændringer Office TLS-certifikater.
author: pshelton-skype
ms.author: pshelton
manager: toddbeckett
ms.topic: article
audience: Developer
ms.date: 3/7/2022
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.openlocfilehash: 075fb8f4c27401a4622f4ce639c897f2e98bb3e9
ms.sourcegitcommit: 2697938d2d4fec523b501c5e7b0b8ec8f34e59b0
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/12/2022
ms.locfileid: "63593064"
---
# <a name="office-tls-certificate-changes"></a>Office ændringer af TLS-certifikat

Microsoft 365 er at opdatere tjenester, der bruger sms-beskeder, møder, telefoni, tale og video til at bruge TLS-certifikater fra et andet sæt rodnøglecertifikater. Denne ændring foretages, fordi det aktuelle rodnøglecenter udløber i maj 2025.

Påvirkede produkter omfatter:
- Microsoft Teams
- Skype
- Skype for Business Online
- Microsoft Dynamics 365
- GroupMe
- Kaizala
- Azure Communication Services

Påvirkede slutpunkter omfatter (men er ikke begrænset til):
- *.teams.microsoft.com
- *.skype.com
- *.skypeforbusiness.com
- *.groupme.com
- *.communication.azure.com
- *.operatorconnect.microsoft.com

Desuden vil Teams og Skype for Business Online-slutpunkter i den amerikanske regerings nationale skybaserede forekomster af Microsoft 365 foretage den samme ændring og påvirke slutpunkter som f.eks.:
- *.gcc.teams.microsoft.com
- *.dod.teams.microsoft.us
- *.gov.teams.microsoft.us
- *.online.dod.skypeforbusiness.us
- *.online.gov.skypeforbusiness.us
- *.um-dod.office365.us
- *.um.office365.us

Denne ændring påvirker ikke certifikater, domæner eller tjenester, der bruges i de nationale skybaserede skybaserede skyforekomster i Kina eller Microsoft 365.

Alle certifikatoplysninger i denne artikel blev tidligere leveret i [Microsoft 365 krypteringskæder](./encryption-office-365-certificate-chains.md) senest oktober 2020.

## <a name="when-will-this-change-happen"></a>Hvornår sker denne ændring?

Tjenester begyndte overgangen til de nye rod-CA'er i januar 2022 og vil fortsætte til og med oktober 2022.

## <a name="what-is-changing"></a>Hvad ændres?

I dag kæder de fleste af de TLS-certifikater, Microsoft 365, sammen med følgende rodnøglecenter:

| Nøglecenternavn | Thumbprint (SHA1) |
|--|--|
| [Baltimore CyberTrust Root](https://cacerts.digicert.com/BaltimoreCyberTrustRoot.crt) | d4de20d05e66fc53fe1a50882c78db2852cae474 |

med en af følgende Mellemliggende CAs:

| Nøglecenternavn | Thumbprint (SHA1) |
|--|--|
| [Microsoft RSA TLS CA 01](https://www.microsoft.com/pki/mscorp/Microsoft%20RSA%20TLS%20CA%2001.crt) | 703d7a8f0ebf55aaa59f98eaf4a206004eb2516a |
| [Microsoft RSA TLS CA 02](https://www.microsoft.com/pki/mscorp/Microsoft%20RSA%20TLS%20CA%2002.crt) | b0c2d2d13cdd56cdaa6ab6e2c04440be4a429c75 |

Nye TLS-certifikater, der bruges Microsoft 365 tjenester, vil nu kæde op til et af følgende rod-CAs:

| Nøglecenternavn | Thumbprint (SHA1) |
|--|--|
| [DigiCert Global Root G2](https://cacerts.digicert.com/DigiCertGlobalRootG2.crt) | df3c24f9bfd666761b268073fe06d1cc8d4f82a4 |
| [Microsoft RSA Root Certificate Authority 2017](https://www.microsoft.com/pkiops/certs/Microsoft%20RSA%20Root%20Certificate%20Authority%202017.crt) | 73a5e64a3bff8316ff0edccc618a906e4eae4d74 | 
| [Microsoft ECC Root Certificate Authority 2017](https://www.microsoft.com/pkiops/certs/Microsoft%20ECC%20Root%20Certificate%20Authority%202017.crt) | 999a64c37ff47d9fab95f14769891460eec4c3c5 |

med en af følgende Mellemliggende CAs:

| Nøglecenternavn | Thumbprint (SHA1) |
|--|--|
| [Microsoft Azure TLS-udstedelse ca. 01](https://www.microsoft.com/pkiops/certs/Microsoft%20Azure%20TLS%20Issuing%20CA%2001%20-%20xsign.crt) | 2f2877c5d778c31e0f29c7e371df5471bd673173 |
| [Microsoft Azure TLS-udstedelse ca. 02](https://www.microsoft.com/pkiops/certs/Microsoft%20Azure%20TLS%20Issuing%20CA%2002%20-%20xsign.crt) | e7eea674ca718e3befd90858e09f8372ad0ae2aa |
| [Microsoft Azure TLS-udstedelse af CA 05](https://www.microsoft.com/pkiops/certs/Microsoft%20Azure%20TLS%20Issuing%20CA%2005%20-%20xsign.crt) | 6c3af02e7f269aa73afd0eff2a88a4a1f04ed1e5 |
| [Microsoft Azure TLS-udstedelse ca. 06](https://www.microsoft.com/pkiops/certs/Microsoft%20Azure%20TLS%20Issuing%20CA%2006%20-%20xsign.crt) | 30e01761ab97e59a06b41ef20af6f2de7ef4f7b0 |

Som et eksempel er dette et gyldigt certifikat med en af de nye certifikatkæder:

![Teams TLS-certifikatkæde](../media/teams-tls-certificate-chain.png)

## <a name="will-this-change-affect-me"></a>Vil denne ændring påvirke mig?

Rodnøglecenter "DigiCert Global Root G2" har stor tillid til operativsystemer, herunder Windows, macOS, Android og iOS samt browsere som Microsoft Edge, Chrome, Safari og Firefox. Vi forventer, **at Microsoft 365 kunder ikke påvirkes**. 

Dit program **kan dog blive påvirket, hvis det udtrykkeligt angiver en liste over acceptable CAs**. Denne fremgangsmåde kaldes "certifikatpinning". Kunder, der ikke har de nye rod-CAs på deres liste over acceptable CAs, modtager certifikatvalideringsfejl, der kan påvirke dit programs tilgængelighed eller funktion.

Her er nogle metoder til at registrere, om dit program kan blive påvirket:

- Søg i din kildekode efter thumbprint, Common Name eller andre egenskaber for en hvilken som helst af de mellemliggende CAs, der findes [her](https://www.microsoft.com/pki/mscorp/cps/default.htm). Hvis der findes et match, så påvirkes dit program. For at løse dette problem skal du opdatere kildekoden for at tilføje egenskaberne for de nye CAs. Som bedste fremgangsmåde skal du sørge for, at CAs kan tilføjes eller redigeres med kort varsel. Branchebestemmelser kræver, at nøglecentercertifikater erstattes inden for syv dage under visse omstændigheder, så programmer, der implementerer certifikatpinning, hurtigt skal reagere på disse ændringer.

- .NET viser funktionerne `System.Net.ServicePointManager.ServerCertificateValidationCallback` `System.Net.HttpWebRequest.ServerCertificateValidationCallback` og tilbagekaldsfunktionerne, som giver udviklere mulighed for at bruge brugerdefineret logik til at afgøre, om certifikater er gyldige, i stedet for at være afhængige af standardcertifikatlageret Windows certifikater. En udvikler kan tilføje logik, der kontrollerer, om et bestemt Common Name eller thumbprint eller kun tillader et bestemt rodnøglecenter, f.eks. "Baltimore CyberTrust Root". Hvis dit program bruger disse callback-funktioner, skal du sørge for, at det accepterer både den gamle og den nye rod- og mellemliggende CAs.

- Oprindelige programmer bruger muligvis , hvilket tillader `WINHTTP_CALLBACK_STATUS_SENDING_REQUEST`, at oprindelige programmer implementerer brugerdefineret certifikatvalideringslogik. Brugen af denne meddelelse er sjælden og kræver en betydelig mængde brugerdefineret kode for at implementere. Som det er beskrevet ovenfor, skal du sikre dig, at dit program accepterer både den gamle og nye rod- og mellemliggende CAs. 

- Hvis du bruger et program, der er integreret med Microsoft Teams, Skype, Skype for Business Online eller Microsoft Dynamics-API'er, og du er i tvivl, om den bruger certifikatpinning, skal du kontakte programleverandøren.

- Forskellige operativsystemer og sprogkørsel, der kommunikerer med Azure-tjenester, kan kræve andre trin for at opbygge og validere de nye certifikatkæder korrekt:
   - **Linux**: Mange distributioner kræver, at du føjer CAs til `/etc/ssl/certs`. Se fordelingens dokumentation for at få specifikke instruktioner.
   - **Java**: Sørg for, at Java-nøglelageret indeholder de CAs, der er angivet ovenfor.
   - **Windows kører** i afbrudte miljøer: Systemer, der kører i afbrudte miljøer, skal have de nye rod-CAs `Trusted Root Certification Authorities` føjet til deres lager og de nye Midlertidige CAs `Intermediate Certification Authorities` føjet til deres lager.
   - **Android**: Kontrollér dokumentationen til din enhed og version af Android.
   - **IoT eller integrerede** enheder: Integrerede enheder som f.eks. tv-sættets topfelter leveres ofte med et begrænset sæt rodnøglecentercertifikater og har ingen nem måde at opdatere certifikatlageret på. Hvis du skriver kode til eller administrerer installationer af brugerdefinerede integrerede eller IoT-enheder, skal du sikre dig, at enhederne har tillid til de nye rod-CAs. Det kan være nødvendigt at kontakte enhedsproducenten.

- Hvis du har et miljø, hvor firewallregler kun tillader udgående opkald til bestemte slutpunkter, skal du tillade følgende URL-adresser for Liste over tilbagekaldte certifikater eller OCSP-adresser (Online Certificate Status Protocol):
   - `http://crl3.digicert.com`
   - `http://crl4.digicert.com`
   - `http://ocsp.digicert.com`
   - `http://crl.microsoft.com`
   - `http://oneocsp.microsoft.com`
   - `http://ocsp.msocsp.com`
   - `http://www.microsoft.com/pkiops`

- Hvis du er påvirket af denne ændring, får du muligvis vist fejlmeddelelser, der afhænger af den type miljø, du kører i, og scenarie, som du er påvirket af. Kontrollér Windows programhændelseslogfiler, CAPI2-hændelseslogfiler og brugerdefinerede programlogfiler for meddelelser, der ser sådan ud:
   ```output
   An operation failed because the following certificate has validation errors:
   
   Subject Name: CN=teams.microsoft.com
   Issuer Name: CN=Microsoft Azure TLS Issuing CA 01, O=Microsoft Corporation, C=US
   
   Errors:
   
   The root of the certificate chain is not a trusted root authority.
   ```

## <a name="when-can-i-retire-the-old-ca-information"></a>Hvornår kan jeg lade de gamle nøglecenteroplysninger udgå?

Det aktuelle Rodnøglecenter, Mellemliggende nøglecenter og bladcertifikater tilbagekaldes ikke. De eksisterende ca Common Names og/eller thumbprints vil være nødvendige til mindst oktober 2023 baseret på levetiden for eksisterende certifikater.
