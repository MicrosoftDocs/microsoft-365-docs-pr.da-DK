---
title: Plan for tredjeparts SSL-certifikater til Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: 'Oversigt: Beskriver SSL-certifikater, der er nødvendige Exchange lokale og hybride tjenester, SSO-tjenester Exchange Online AD FS og Exchange Web Services.'
ms.openlocfilehash: 8c0bf69090abb87e71f2d51b73405ccf4e54d4bb
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63591577"
---
# <a name="plan-for-third-party-ssl-certificates-for-microsoft-365"></a>Plan for tredjeparts SSL-certifikater til Microsoft 365

*Denne artikel gælder for både Microsoft 365 Enterprise og Office 365 Enterprise.*

Hvis du vil kryptere kommunikationen mellem dine klienter og Microsoft 365-miljøet, skal et tredjeparts SSL-certifikat (Secure Socket Layer) være installeret på infrastrukturserverne.

Denne artikel er en del af [Netværksplanlægning og justering af ydeevnen for Microsoft 365](./network-planning-and-performance.md).
   
Der kræves certifikater til følgende Microsoft 365 komponenter:
  
- Exchange lokale miljø
    
- Single sign-on (SSO) (for både AD FS-sammenslutningsservere (Active Directory Federation Services) og AD FS-sammenslutningsserverfremvisere)
    
- Exchange Online, f.eks. Autodiscover, Outlook overalt og Exchange webtjenester
    
- Exchange-hybridserver
    
## <a name="certificates-for-exchange-on-premises"></a>Certifikater til Exchange lokale miljø

Du kan få et overblik over, hvordan du bruger digitale certifikater til at sikre kommunikationen mellem den lokale Exchange-organisation og Exchange Online i TechNet-artiklen Om [certifikatkrav](/previous-versions/exchange-server/exchange-141/gg476123(v=exchg.141)).
  
## <a name="certificates-for-single-sign-on"></a>Certifikater til enkeltlogon

For at give brugerne en forenklet enkelt logonoplevelse, der indebærer robust sikkerhed, er certifikaterne, som er vist i følgende tabel, påkrævet af enten sammenslutningsserverne eller sammenslutningsserverens proxyserver. Tabellen nedenfor fokuserer på Active Directory Federation Services (AD FS), og vi har også flere oplysninger om brug af [tredjepartsudbydere af identitet](/azure/active-directory/hybrid/how-to-connect-fed-compatibility).
  
| Certifikattype | Beskrivelse | Hvad du bør vide, før du installerer |
|:-----|:-----|:-----|
|**SSL-certifikat (også kaldet et servergodkendelsescertifikat)** <br/> |Dette er et standard-SSL-certifikat, der bruges til at sikre kommunikationen mellem sammenslutningsservere, klienter og sammenslutningsserverproxyer.  <br/> |AD FS kræver et SSL-certifikat. Som standard bruger AD FS et SSL-certifikat, der er konfigureret til standardwebstedet i Internet Information Services (IIS).  <br/> Emnenavnet på dette SSL-certifikat bruges til at bestemme navnet på sammenslutningstjenesten for hver forekomst af AD FS, du installerer. Overvej at vælge et emnenavn, der bedst repræsenterer navnet på den virksomhed eller organisation, der bedst repræsenterer det firma eller den organisation, der skal udgives Microsoft 365. Dette navn skal kunne afbildes via internettet.  <br/>**Advarsel!** AD FS kræver, at dette SSL-certifikat ikke har et emnenavn uden prik (kort navn).          <br/> **Anbefaling:** Da der skal være tillid til dette certifikat fra AD FS-klienter, anbefaler vi, at du bruger et SSL-certifikat, der er udstedt af et offentligt nøglecenter (tredjepart), eller af et nøglecenter, der er underordnet en offentlig rod; Eksempelvis VeriSign eller Thawte.  <br/> |
|**Certifikat til signering med token** <br/> |Dette er et standard X.509-certifikat, der bruges til sikker signering af alle tokens, som sammenslutningsserveren udsteder, og som Microsoft 365 accepterer og validerer.  <br/> |Certifikatet til signering med token skal indeholde en privat nøgle, der kæder til en pålidelig rod i FS. Som standard opretter AD FS et selv signeret certifikat. Men afhængigt af organisationens behov kan du ændre dette certifikat til et certifikat, der er udstedt af et nøglecenter, ved hjælp af en AD FS administrations-snap-in.  <br/>**Advarsel!** Certifikatet til signering med token er afgørende for stabiliteten af SS. Hvis certifikatet ændres, Microsoft 365 du få besked om ændringen. Hvis der ikke leveres en meddelelse, kan brugerne ikke logge på deres Microsoft 365-servicetilbud.<br/>**Anbefaling:** Vi anbefaler, at du bruger det selvsignerede certifikat til signering med token, der genereres af AD FS. Ved at gøre dette administrerer den som standard dette certifikat for dig. Når f.eks. dette certifikat er ved at udløbe, genererer AD FS et nyt selv signeret certifikat.  <br/> |
   
Sammenslutningsserverens proxyer kræver det certifikat, der er beskrevet i følgende tabel.
  
| Certifikattype | Beskrivelse | Hvad du bør vide, før du installerer |
|:-----|:-----|:-----|
|SSL-certifikat  <br/> |Dette er et standard-SSL-certifikat, der bruges til sikring af kommunikation mellem en sammenslutningsserver, en sammenslutningsserverproxy og internetklientcomputere.  <br/> |Dette SSL-certifikat skal være bundet til standardwebstedet i IIS, før du kan køre konfigurationsguiden til AD FS sammenslutningsserverproxy.  <br/> Dette certifikat skal have samme emnenavn som det SSL-certifikat, der blev konfigureret på sammenslutningsserveren i virksomhedens netværk.  <br/> **Anbefaling:** Vi anbefaler, at du bruger det samme servergodkendelsescertifikat, som er konfigureret på den sammenslutningsserver, som denne sammenslutningsserverproxy opretter forbindelse til.  <br/> |
   
## <a name="certificates-for-autodiscover-outlook-anywhere-and-active-directory-synchronization"></a>Certifikater til Autodiscover, autodiscover, Outlook hvor som helst og Active Directory-synkronisering

Dine eksternt rettede Exchange 2013-, Exchange 2010-, Exchange 2007- og Exchange 2003 Client Access-servere (CASs) kræver et SSL-certifikat fra en tredjepart for sikre forbindelser til Autodiscover, Outlook Anywhere og Active Directory-synkroniseringstjenester. Du har måske allerede dette certifikat installeret i dit lokale miljø.
  
## <a name="certificate-for-an-exchange-hybrid-server"></a>Certifikat til en Exchange hybridserver

Din eller dine Exchange en eller flere hybridservere kræver et SSL-certifikat fra en tredjepart for at sikre forbindelsen Exchange Online tjenesten. Du skal have fat i dette certifikat fra en tredjepart-SSL-udbyder.
  
## <a name="microsoft-365-certificate-chains"></a>Microsoft 365 certifikatkæder

I denne artikel beskrives de certifikater, du muligvis skal installere på din infrastruktur. Du kan finde flere oplysninger om certifikater, der er installeret Microsoft 365 vores servere, [Microsoft 365 certifikatkæder](https://support.office.com/article/0c03e6b3-e73f-4316-9e2b-bf4091ae96bb).
  
## <a name="see-also"></a>Se også

[Microsoft 365 Enterprise oversigt](microsoft-365-overview.md)