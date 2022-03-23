---
title: Godkendelse i organisationsnetværket med høj tilgængelighed Fase 5 Konfigurer federated authentication for Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 11/25/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Ent_Solutions
ms.assetid: 0f1dbf52-5bff-44cc-a264-1b48641af98f
description: 'Oversigt: Konfigurer Azure AD Forbind til din godkendelse i organisationsnetværket med høj tilgængelighed til Microsoft 365 i Microsoft Azure.'
ms.openlocfilehash: e5a11c1b94f9a0297ccfa0a18e1963fae9898f65
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63590581"
---
# <a name="high-availability-federated-authentication-phase-5-configure-federated-authentication-for-microsoft-365"></a>Godkendelse i organisationsnetværket med høj tilgængelighed Fase 5: Konfigurer federated authentication for Microsoft 365

I denne sidste fase af udrulning af godkendelse i organisationsnetværket med høj tilgængelighed til Microsoft 365 i Azure-infrastrukturtjenester får du og installerer et certifikat, der er udstedt af et offentligt nøglecenter, bekræfter din konfiguration og installerer og kører derefter Azure AD Forbind på katalogsynkroniseringsserveren. Azure AD Forbind konfigurerer dit Microsoft 365-abonnement og dine AD FS- (Active Directory Federation Services) og webprogramproxyservere til federated authentication.
  
Se [Installér godkendelse med høj tilgængelighed i organisationsnetværket Microsoft 365 i Azure](deploy-high-availability-federated-authentication-for-microsoft-365-in-azure.md) for alle faser.
  
## <a name="get-a-public-certificate-and-copy-it-to-the-directory-synchronization-server"></a>Få et offentligt certifikat, og kopiér det til katalogsynkroniseringsserveren

Få et digitalt certifikat fra et offentligt nøglecenter med følgende egenskaber:
  
- Et X.509-certifikat, der er egnet til oprettelse af SSL-forbindelser.
    
- Den udvidede egenskab Subject Alternative Name (SAN) er indstillet til din sammenslutningstjeneste FQDN (eksempel: fs.contoso.com).
    
- Certifikatet skal have den private nøgle og være gemt i PFX-format.
    
Desuden skal din organisations computere og enheder have tillid til det offentlige nøglecenter, der udsteder det digitale certifikat. Denne tillid etableres ved at have et rodcertifikat fra det offentlige nøglecenter installeret på de pålidelige rodnøglecenters lager på dine computere og enheder. Computere, der kører Microsoft Windows har typisk et sæt af disse certifikattyper installeret fra ofte anvendte nøglecenter. Hvis rodcertifikatet fra dit offentlige nøglecenter ikke allerede er installeret, skal du installere det på organisationens computere og enheder.
  
Du kan finde flere oplysninger om certifikatkrav til federated authentication under [Forudsætninger for installation og konfiguration af sammenslutning](/azure/active-directory/connect/active-directory-aadconnect-prerequisites#prerequisites-for-federation-installation-and-configuration).
  
Når du modtager certifikatet, skal du kopiere det til en mappe på C:-drevet på katalogsynkroniseringsserveren. Navngive filen SSL.pfx og gemme den i mappen C:\\Certs på katalogsynkroniseringsserveren.
  
## <a name="verify-your-configuration"></a>Bekræfte din konfiguration

Du bør nu være klar til at konfigurere Azure AD Forbind godkendelse i organisationsnetværket til Microsoft 365. Her er en tjekliste for at sikre, at du er:
  
- Din organisations offentlige domæne føjes til dit Microsoft 365 abonnement.
    
- Organisationens brugerkonti Microsoft 365 konfigureres til organisationens offentlige domænenavn og kan logge på.
    
- Du har fastlagt en sammenslutningstjeneste FQDN baseret på dit offentlige domænenavn.
    
- En offentlig DNS En post for din sammenslutningstjeneste FQDN peger på den offentlige IP-adresse på den internetrettede Azure-belastningsbalance for webprogramproxyservere.
    
- En privat DNS A-post for din sammenslutningstjeneste FQDN peger på den private IP-adresse for den interne Azure-belastningsbalance for AD FS-serverne.
    
- Et offentligt nøglecenter- og et digitalt certifikat, der er egnet til SSL-forbindelser med SAN-sættet til din sammenslutningstjeneste FQDN, er en PFX-fil, der er gemt på din katalogsynkroniseringsserver.
    
- Rodcertifikatet for det offentlige nøglecenter er installeret i lageret for rodnøglecenter, der er tillid til på dine computere og enheder.
    
Her er et eksempel for Contoso-organisationen:
  
**Et eksempel på konfiguration af en godkendelsesinfrastruktur med høj tilgængelighed i organisationsnetværket i Azure**

![Et eksempel på konfiguration af den høje tilgængelighed Microsoft 365 organisationsnetværksgodkendelsesinfrastruktur i Azure.](../media/ac1a6a0d-0156-4407-9336-6e4cd6db8633.png)
  
## <a name="run-azure-ad-connect-to-configure-federated-authentication"></a>Kør Azure AD Forbind for at konfigurere organisationsnetværksgodkendelse

Azure AD Forbind konfigurerer AD FS-serverne, webprogrammets proxyservere og Microsoft 365 til federated authentication med disse trin:
  
1. Opret en fjernskrivebordsforbindelse til din katalogsynkroniseringsserver med en domænekonto, der har lokale administratorrettigheder.
    
2. Åbn Internet Explorer på skrivebordet på katalogsynkroniseringsserveren, og gå til [https://aka.ms/aadconnect](https://aka.ms/aadconnect).
    
3. På siden **Microsoft Azure Active Directory Forbind** skal du klikke **på Download** og derefter klikke på **Kør**.
    
4. På siden **Velkommen til Azure AD Forbind skal du** klikke på **Jeg accepterer** og derefter klikke på **Fortsæt.**
    
5. Klik **på Tilpas Indstillinger** siden **Hurtig tilpasning**.
    
6. Klik på **Installér på** siden Installér **påkrævede komponenter**.
    
7. På siden **Bruger-logon skal** du klikke på **Sammenslutning med AD FS** og derefter klikke på **Næste**.
    
8. På siden **Forbind til Azure AD** skal du skrive navn og adgangskode for en **Azure AD DC-administrator** eller **global** administratorkonto for dit Microsoft 365-abonnement og derefter klikke på **Næste**.
    
9. På siden **Forbind** skal du sørge for, at dit lokale Active Directory-domæneservices(AD DS)-område er markeret i **Skov, skrive** navnet og adgangskoden til en domæneadministratorkonto, klikke på Tilføj **mappe og derefter** klikke på **Næste**.
    
10. På siden **Konfiguration af Azure AD-logon skal** du klikke på **Næste**.
    
11. Klik på **Næste på siden Domæne- og OU-filtrering**.
    
12. Klik på **Næste på siden Entydigt identificerende** dine **brugere**.
    
13. Klik på **Næste på siden Filtrer** brugere og **enheder**.
    
14. Klik på **Næste på** siden **Valgfrie funktioner**.
    
15. På siden **AD FS-farm skal** du klikke på **Konfigurer en ny AD FS-farm**.
    
16. Klik **på** Gennemse, og angiv placeringen og navnet på SSL-certifikatet fra det offentlige nøglecenter.
    
17. Når du bliver bedt om det, skal du skrive adgangskoden til certifikatet og derefter klikke på **OK**.
    
18. Kontrollér, at **Emnenavn og** **sammenslutningstjenestenavn er** angivet til din sammenslutningstjenesteSQDN, og klik derefter på **Næste**.
    
19. På siden **AD FS-servere** skal du skrive navnet på din første AD FS-server (kolonnen Tabel M - element 4 - navn på virtuel maskine) og derefter klikke på **Tilføj**.
    
20. Skriv navnet på den anden AD FS-server (Tabel M – element 5 – kolonnen navn på virtuel maskine), klik **på Tilføj,** og klik derefter på **Næste**.
    
21. På siden **Web Application Proxy-servere** skal du skrive navnet på proxyserveren for dit første webprogram (kolonnen Tabel M - element 6 - navn på virtuel maskine) og derefter klikke på **Tilføj**.
    
22. Skriv navnet på den anden proxyserver til webprogrammet (Tabel M - element 7 - kolonnen navn på virtuel maskine), klik **på Tilføj,** og klik derefter på **Næste**.
    
23. Skriv **brugernavnet og adgangskoden til en** domæneadministratorkonto på siden Legitimationsoplysninger for domæneadministrator, og klik derefter på **Næste**.
    
24. På siden **AD FS-tjenestekonto** skal du skrive brugernavnet og adgangskoden til en virksomhedsadministratorkonto og derefter klikke på **Næste**.
    
25. På siden **Azure AD Domain** i **Domain skal** du vælge organisationens DNS-domænenavn og derefter klikke på **Næste**.
    
26. Klik på **Installer på siden** Klar til **konfiguration**.
    
27. Klik på **Bekræft på** siden Installation **fuldført**. Du bør få vist to meddelelser, der angiver, at både intranet- og internetkonfigurationen blev bekræftet.
    
  - Intranetmeddelelsen skal vise den private IP-adresse for din interne Azure-belastningsbalance for dine AD FS-servere.
    
  - Internetmeddelelsen bør vise den offentlige IP-adresse for din Azure Internet-rettede belastningsbalance for dine proxyservere for webprogram.
    
28. Klik på **Afslut** på siden Installation **fuldført**.
    
Her er den endelige konfiguration med pladsholdernavnene for serverne.
  
**Fase 5: Den endelige konfiguration af en godkendelsesinfrastruktur i organisationsnetværket med høj tilgængelighed i Azure**

![Den endelige konfiguration af den høje tilgængelighed Microsoft 365 organisationsnetværksgodkendelsesinfrastruktur i Azure.](../media/c5da470a-f2aa-489a-a050-df09b4d641df.png)
  
Din store tilgængelighedsgodkendelsesinfrastruktur til organisationsnetværket til Microsoft 365 i Azure er fuldført.
  
## <a name="see-also"></a>Se også

[Installér godkendelse med høj tilgængelighed i organisationsnetværket Microsoft 365 i Azure](deploy-high-availability-federated-authentication-for-microsoft-365-in-azure.md)
  
[Identitet i organisationsnetværk for dit Microsoft 365 udviklings-/testmiljø](federated-identity-for-your-microsoft-365-dev-test-environment.md)
  
[Microsoft 365 og arkitekturcenter](../solutions/index.yml)

[Identitet i organisationsnetværk for Microsoft 365](https://support.office.com/article/Understanding-Office-365-identity-and-Azure-Active-Directory-06a189e7-5ec6-4af2-94bf-a22ea225a7a9#bk_federated)
