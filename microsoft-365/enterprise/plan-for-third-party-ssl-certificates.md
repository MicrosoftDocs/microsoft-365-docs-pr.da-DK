---
title: Planlæg SSL-certifikater fra tredjepart til Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
audience: ITPro
ms.date: 05/15/2019
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- M365-subscription-management
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: b48cdf63-07e0-4cda-8c12-4871590f59ce
description: 'Oversigt: Beskriver de SSL-certifikater, der kræves til Exchange i det lokale miljø og hybrid, SSO ved hjælp af AD FS, Exchange Online-tjenester og Exchange webtjenester.'
ms.openlocfilehash: 0cd7cce2cd5f0aba8baecab7048d86d629d30427
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65100297"
---
# <a name="plan-for-third-party-ssl-certificates-for-microsoft-365"></a>Planlæg SSL-certifikater fra tredjepart til Microsoft 365

*Denne artikel gælder både for Microsoft 365 Enterprise og Office 365 Enterprise.*

Hvis du vil kryptere kommunikationen mellem dine klienter og det Microsoft 365 miljø, skal der installeres SSL-certifikater (Secure Socket Layer) fra tredjepart på infrastrukturserverne.

Denne artikel er en del af [netværksplanlægning og justering af ydeevnen for Microsoft 365](./network-planning-and-performance.md).
   
Der kræves certifikater til følgende Microsoft 365 komponenter:
  
- Exchange i det lokale miljø
    
- Enkeltlogon (SSO) (for både AD FS-servere (Active Directory Federation Services) og AD FS-sammenslutningsserverproxyer)
    
- Exchange Online tjenester, f.eks. Autodiscover, Outlook Anywhere og Exchange Web Services
    
- Exchange hybridserver
    
## <a name="certificates-for-exchange-on-premises"></a>Certifikater til Exchange i det lokale miljø

Du kan få en oversigt over, hvordan du bruger digitale certifikater til at gøre kommunikationen mellem Exchange organisation i det lokale miljø og Exchange Online sikker, i TechNet-artiklen [Om certifikatkrav](/previous-versions/exchange-server/exchange-141/gg476123(v=exchg.141)).
  
## <a name="certificates-for-single-sign-on"></a>Certifikater til enkeltlogon

Hvis du vil give brugerne en forenklet single sign-on-oplevelse, der omfatter robust sikkerhed, kræves de certifikater, der vises i følgende tabel, på enten samlingsserverne eller proxyerne for sammenslutningsserveren. I nedenstående tabel fokuseres der på Active Directory Federation Services (AD FS), og vi har også flere oplysninger om [brug af identitetsudbydere fra tredjepart](/azure/active-directory/hybrid/how-to-connect-fed-compatibility).
  
| Certifikattype | Beskrivelse | Det har du brug for at vide, før du udruller |
|:-----|:-----|:-----|
|**SSL-certifikat (også kaldet et certifikat til servergodkendelse)** <br/> |Dette er et standard-SSL-certifikat, der bruges til at gøre kommunikation mellem server-, klient- og sammenslutningsserverproxycomputere sikker.  <br/> |AD FS kræver et SSL-certifikat. AD FS bruger som standard det SSL-certifikat, der er konfigureret til standardwebstedet i Internet Information Services (IIS).  <br/> Emnenavnet på dette SSL-certifikat bruges til at bestemme FS-navnet (Federation Service) for hver forekomst af AD FS, du installerer. Overvej at vælge et emnenavn til et nyt nøglecenter (CA)-udstedte certifikater, der bedst repræsenterer navnet på det firma eller den organisation, der skal Microsoft 365. Dette navn skal være internet-routable.  <br/>**Forsigtighed:** AD FS kræver, at dette SSL-certifikat ikke har et emnenavn uden punktum (kort navn).          <br/> **Henstilling:** Da klienter i AD FS skal have tillid til dette certifikat, anbefaler vi, at du bruger et SSL-certifikat, der er udstedt af et offentligt nøglecenter (tredjepart) eller af et nøglecenter, der er underordnet en rod, der er offentligt tillid til. f.eks. VeriSign eller Thawte.  <br/> |
|**Certifikat til tokensignering** <br/> |Dette er et standard-X.509-certifikat, der bruges til sikker signering af alle tokens, som problemer med sammenslutningsserveren, og som Microsoft 365 accepterer og validerer.  <br/> |Certifikatet til tokensignering skal indeholde en privat nøgle, der kædes til en rod, der er tillid til, i FS. AD FS opretter som standard et selvsigneret certifikat. Afhængigt af organisationens behov kan du dog ændre dette certifikat til et certifikat, der er udstedt af et nøglecenter, ved hjælp af snap-in'en AD FS-administration.  <br/>**Forsigtighed:** Certifikatet til tokensignering er afgørende for stabiliteten i FS. Hvis certifikatet ændres, skal Microsoft 365 have besked om ændringen. Hvis der ikke vises en meddelelse, kan brugerne ikke logge på deres Microsoft 365 servicetilbud.<br/>**Henstilling:** Vi anbefaler, at du bruger det selvsignerede tokensigneringscertifikat, der genereres af AD FS. Det administrerer som standard dette certifikat for dig. Når dette certifikat f.eks. er ved at udløbe, genererer AD FS et nyt selvsigneret certifikat.  <br/> |
   
Sammenslutningsserverproxyer kræver det certifikat, der er beskrevet i følgende tabel.
  
| Certifikattype | Beskrivelse | Det har du brug for at vide, før du udruller |
|:-----|:-----|:-----|
|SSL-certifikat  <br/> |Dette er et STANDARD SSL-certifikat, der bruges til at sikre kommunikation mellem en sammenslutningsserver, en sammenslutningsserverproxy og internetklientcomputere.  <br/> |Dette SSL-certifikat skal bindes til standardwebstedet i IIS, før du kan køre guiden Konfiguration af AD FS Federation Server-proxy.  <br/> Certifikatet skal have samme emnenavn som det SSL-certifikat, der blev konfigureret på organisationsserveren på virksomhedens netværk.  <br/> **Henstilling:** Vi anbefaler, at du bruger det samme servergodkendelsescertifikat, som er konfigureret på den samlingsserver, som denne sammenslutningsserverproxy opretter forbindelse til.  <br/> |
   
## <a name="certificates-for-autodiscover-outlook-anywhere-and-active-directory-synchronization"></a>Certifikater til automatisk søgning, Outlook hvor som helst og Synkronisering af Active Directory

Dine eksterne Exchange 2013, Exchange 2010, Exchange 2007 og Exchange 2003 CASs (Client Access Servers) kræver et SSL-certifikat fra tredjepart for at sikre forbindelser til Autodiscover, Outlook Anywhere og Active Directory-synkroniseringstjenester. Du har muligvis allerede dette certifikat installeret i dit lokale miljø.
  
## <a name="certificate-for-an-exchange-hybrid-server"></a>Certifikat til en Exchange Hybrid Server

Din eksterne Exchange hybridserver eller -servere kræver et SSL-certifikat fra tredjepart for at sikre forbindelsen til Exchange Online-tjenesten. Du skal hente dette certifikat fra din SSL-tredjepartsudbyder.
  
## <a name="microsoft-365-certificate-chains"></a>Microsoft 365 certifikatkæder

I denne artikel beskrives de certifikater, du muligvis skal installere på infrastrukturen. Du kan få flere oplysninger om de certifikater, der er installeret på vores Microsoft 365-servere, [under Microsoft 365 Certifikatkæder](https://support.office.com/article/0c03e6b3-e73f-4316-9e2b-bf4091ae96bb).
  
## <a name="see-also"></a>Se også

[oversigt over Microsoft 365 Enterprise](microsoft-365-overview.md)