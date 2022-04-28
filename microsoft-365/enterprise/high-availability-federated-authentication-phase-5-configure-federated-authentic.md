---
title: Godkendelse i organisationsnetværket med høj tilgængelighed Fase 5 Konfigurer organisationsnetværksgodkendelse for Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: 'Oversigt: Konfigurer Azure AD-Forbind for din organisationsnetværksgodkendelse med høj tilgængelighed for Microsoft 365 i Microsoft Azure.'
ms.openlocfilehash: 9eff7f815ff5f7508da1f0e1230079a1b1802fed
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65091253"
---
# <a name="high-availability-federated-authentication-phase-5-configure-federated-authentication-for-microsoft-365"></a>Godkendelse i organisationsnetværket med høj tilgængelighed Fase 5: Konfigurer godkendelse i organisationsnetværket for Microsoft 365

I denne sidste fase af udrulningen af samlet godkendelse med høj tilgængelighed for Microsoft 365 i Azure-infrastrukturtjenester henter og installerer du et certifikat, der er udstedt af et offentligt nøglecenter, bekræfter konfigurationen og derefter installerer og kører Azure AD-Forbind på katalogsynkroniseringsserveren. Azure AD-Forbind konfigurerer dit Microsoft 365-abonnement og dine Active Directory Federation Services (AD FS) og webprogramproxyservere til godkendelse i organisationsnetværket.
  
Se [Udrul organisationsnetværksgodkendelse med høj tilgængelighed for Microsoft 365 i Azure](deploy-high-availability-federated-authentication-for-microsoft-365-in-azure.md) for alle faserne.
  
## <a name="get-a-public-certificate-and-copy-it-to-the-directory-synchronization-server"></a>Hent et offentligt certifikat, og kopiér det til katalogsynkroniseringsserveren

Hent et digitalt certifikat fra et offentligt nøglecenter med følgende egenskaber:
  
- Et X.509-certifikat, der er egnet til oprettelse af SSL-forbindelser.
    
- Den udvidede egenskab Subject Alternative Name (SAN) er angivet til FQDN (f.eks. fs.contoso.com).
    
- Certifikatet skal have den private nøgle og gemmes i PFX-format.
    
Organisationens computere og enheder skal desuden have tillid til det offentlige nøglecenter, der udsteder det digitale certifikat. Dette tillidsforhold etableres ved at have et rodcertifikat fra det offentlige nøglecenter installeret i det rodnøglecenter, der er tillid til, på dine computere og enheder. Computere, der kører Microsoft Windows har typisk et sæt af disse typer certifikater installeret fra almindeligt anvendte nøglecentre. Hvis rodcertifikatet fra dit offentlige nøglecenter ikke allerede er installeret, skal du installere det på computere og enheder i din organisation.
  
Du kan få flere oplysninger om certifikatkrav til godkendelse i organisationsnetværket under [Forudsætninger for installation og konfiguration af organisationsnetværk](/azure/active-directory/connect/active-directory-aadconnect-prerequisites#prerequisites-for-federation-installation-and-configuration).
  
Når du modtager certifikatet, skal du kopiere det til en mappe på C:-drevet på katalogsynkroniseringsserveren. Navngiv f.eks. filen SSL.pfx, og gem den i mappen C:\\Certs på katalogsynkroniseringsserveren.
  
## <a name="verify-your-configuration"></a>Kontrollér konfigurationen

Du bør nu være klar til at konfigurere Azure AD-Forbind og organisationsnetværksgodkendelse for Microsoft 365. Her er en tjekliste for at sikre, at du er:
  
- Organisationens offentlige domæne føjes til dit abonnement på Microsoft 365.
    
- Organisationens Microsoft 365 brugerkonti er konfigureret til organisationens offentlige domænenavn og kan logge på.
    
- Du har bestemt, at FQDN for en sammenslutningstjeneste er baseret på dit offentlige domænenavn.
    
- En offentlig DNS En post for din FQDN-samlingstjeneste peger på den offentlige IP-adresse for azure-belastningsjustering via internettet for webprogramproxyserverne.
    
- En privat DNS En post for din FQDN-samlingstjeneste peger på den private IP-adresse for den interne Azure-belastningsjustering for AD FS-serverne.
    
- Et digitalt certifikat, der udgives af et offentligt nøglecenter, som egner sig til SSL-forbindelser med SAN-sættet til din FQDN-samlingstjeneste, er en PFX-fil, der er gemt på katalogsynkroniseringsserveren.
    
- Rodcertifikatet for det offentlige nøglecenter installeres i lageret med rodnøglecentre, der er tillid til, på dine computere og enheder.
    
Her er et eksempel på Contoso-organisationen:
  
**Et eksempel på konfiguration af en organisationsnetværksgodkendelsesinfrastruktur med høj tilgængelighed i Azure**

![Et eksempel på konfiguration af høj tilgængelighed Microsoft 365 organisationsnetværket godkendelsesinfrastruktur i Azure.](../media/ac1a6a0d-0156-4407-9336-6e4cd6db8633.png)
  
## <a name="run-azure-ad-connect-to-configure-federated-authentication"></a>Kør Azure AD Forbind for at konfigurere godkendelse i organisationsnetværket

Værktøjet Azure AD Forbind konfigurerer AD FS-servere, webprogramproxyservere og Microsoft 365 til godkendelse i organisationsnetværk med disse trin:
  
1. Opret en fjernskrivebordsforbindelse til katalogsynkroniseringsserveren med en domænekonto, der har lokale administratorrettigheder.
    
2. Åbn Internet Explorer på skrivebordet på katalogsynkroniseringsserveren, og gå til [https://aka.ms/aadconnect](https://aka.ms/aadconnect).
    
3. Klik på **Download** på siden **Microsoft Azure Active Directory Forbind**, og klik derefter på **Kør**.
    
4. Klik på **Jeg accepterer** **på siden Velkommen til Azure AD Forbind**, og klik derefter på **Fortsæt.**
    
5. Klik på **Tilpas** på siden **Express Indstillinger**.
    
6. Klik på **Installér** på siden **Installér påkrævede komponenter**.
    
7. Klik på **Sammenslutning med AD FS** på siden **Brugerlogon**, og klik derefter på **Næste**.
    
8. På siden **Forbind til Azure AD** skal du skrive navnet og adgangskoden for en **Azure AD DC-administrator** eller **global administratorkonto** for dit Microsoft 365 abonnement og derefter klikke på **Næste**.
    
9. På siden **Forbind mapperne** skal du sikre dig, at du har valgt dit AD DS-område (Active Directory i det lokale miljø Domain Services) i **Område**, skrive navnet og adgangskoden på en domæneadministratorkonto, klikke på **Tilføj mappe** og derefter klikke på **Næste**.
    
10. Klik på **Næste** på siden med **konfiguration af Azure AD-logon**.
    
11. Klik på **Næste** på siden **Domæne- og organisationsfiltrering**.
    
12. Klik på **Næste** på siden **Entydigt identificere dine brugere**.
    
13. Klik på **Næste** på siden **Filtrer brugere og enheder**.
    
14. Klik på **Næste** på siden **Valgfrie funktioner**.
    
15. Klik på **Konfigurer en ny AD FS-farm** på siden **AD FS-farm**.
    
16. Klik på **Gennemse** , og angiv placeringen og navnet på SSL-certifikatet fra det offentlige nøglecenter.
    
17. Når du bliver bedt om det, skal du skrive adgangskoden til certifikatet og derefter klikke på **OK**.
    
18. Kontrollér, at **Emnenavn** og **Navn på organisationstjeneste** er angivet til FQDN for organisationstjenesten, og klik derefter på **Næste**.
    
19. På siden **AD FS-servere** skal du skrive navnet på din første AD FS-server (kolonnen Tabel M - Element 4 - Navn på virtuel maskine) og derefter klikke på **Tilføj**.
    
20. Skriv navnet på den anden AD FS-server (Tabel M - Element 5 - Navn på virtuel maskine), klik på **Tilføj**, og klik derefter på **Næste**.
    
21. Skriv navnet på den første webprogramproxyserver (Tabel M - Element 6 - Navn på virtuel maskine) på siden **Web Programproxy-servere**, og klik derefter på **Tilføj**.
    
22. Skriv navnet på den anden webprogramproxyserver (Tabel M - Element 7 - Navn på virtuel maskine), klik på **Tilføj**, og klik derefter på **Næste**.
    
23. På siden **Legitimationsoplysninger for domæneadministrator** skal du skrive brugernavnet og adgangskoden for en domæneadministratorkonto og derefter klikke på **Næste**.
    
24. På siden **AD FS-tjenestekonto** skal du skrive brugernavnet og adgangskoden for en virksomhedsadministratorkonto og derefter klikke på **Næste**.
    
25. Vælg din organisations DNS-domænenavn i **Domæne** på siden **Azure AD Domain**, og klik derefter på **Næste**.
    
26. Klik på **Installér** på siden **Klar til at konfigurere**.
    
27. Klik på **Bekræft** på siden **Installation fuldført**. Du bør kunne se to meddelelser, der angiver, at både intranet- og internetkonfigurationen blev bekræftet.
    
  - Intranetmeddelelsen skal vise den private IP-adresse for din interne Azure-belastningsjustering for dine AD FS-servere.
    
  - Internetmeddelelsen skal vise den offentlige IP-adresse for belastningsjusteringen på Azure Internet for proxyserverne for webprogrammet.
    
28. Klik på **Afslut** på siden **Installation fuldført**.
    
Her er den endelige konfiguration med pladsholdernavne for serverne.
  
**Fase 5: Den endelige konfiguration af en samlet godkendelsesinfrastruktur med høj tilgængelighed i Azure**

![Den endelige konfiguration af den høje tilgængelighed Microsoft 365 godkendelsesinfrastruktur i organisationsnetværket i Azure.](../media/c5da470a-f2aa-489a-a050-df09b4d641df.png)
  
Din organisationsnetværksgodkendelsesinfrastruktur med høj tilgængelighed for Microsoft 365 i Azure er fuldført.
  
## <a name="see-also"></a>Se også

[Udrul organisationsnetværksgodkendelse med høj tilgængelighed for Microsoft 365 i Azure](deploy-high-availability-federated-authentication-for-microsoft-365-in-azure.md)
  
[Organisationsnetværksidentitet for dit Microsoft 365 udviklings-/testmiljø](federated-identity-for-your-microsoft-365-dev-test-environment.md)
  
[Microsoft 365-løsnings- og arkitekturcenter](../solutions/index.yml)

[Organisationsnetværksidentitet for Microsoft 365](https://support.office.com/article/Understanding-Office-365-identity-and-Azure-Active-Directory-06a189e7-5ec6-4af2-94bf-a22ea225a7a9#bk_federated)
