---
title: Konfigurere Azure Rights Management til den tidligere version af meddelelseskryptering
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 10/30/2018
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: 2cba47b3-f09e-4911-9207-ac056fcb9db7
description: Den tidligere version af Office 365-meddelelseskryptering afhænger af Microsoft Azure Rights Management (tidligere kendt som Windows Azure Active Directory Rights Management).
ms.openlocfilehash: c94497069d929dd3819e3ced915c8e778e983c10
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63588940"
---
# <a name="set-up-azure-rights-management-for-the-previous-version-of-message-encryption"></a>Konfigurere Azure Rights Management til den tidligere version af meddelelseskryptering

I dette emne beskrives de trin, du skal følge for at aktivere og derefter konfigurere RMS (Azure Rights Management), som er en del af Azure Information Protection, til brug med den tidligere version af Office 365-meddelelseskryptering (OME).

## <a name="this-article-only-applies-to-the-previous-version-of-ome"></a>Denne artikel gælder kun for den tidligere version af OME

Hvis du endnu ikke har flyttet organisationen til de nye OME-funktioner, men du allerede har installeret OME, gælder oplysningerne i denne artikel for din organisation. Microsoft anbefaler, at du planlægger at flytte til de nye OME-funktioner, så snart det er fornuftigt for din organisation. Du kan finde en [vejledning under Konfigurere Office 365-meddelelseskryptering funktioner](set-up-new-message-encryption-capabilities.md). Hvis du vil vide mere om, hvordan de nye funktioner virker først, skal du se [Office 365-meddelelseskryptering](ome.md). Resten af denne artikel henviser til OME-funktionsmåde før frigivelsen af de nye OME-funktioner.

## <a name="prerequisites-for-using-the-previous-version-of-office-365-message-encryption"></a>Forudsætninger for brug af den tidligere version af Office 365-meddelelseskryptering
<a name="warmprereqs"> </a>

Office 365-meddelelseskryptering (OME), herunder IRM, afhænger af Azure Rights Management (Azure RMS). Azure RMS er den teknologi til beskyttelse, der bruges af Azure Information Protection. Hvis du vil bruge OME, skal din organisation Exchange Online et Exchange Online Protection-abonnement, der omfatter et Azure Rights Management-abonnement.
  
- Hvis du ikke er sikker på, hvad dit abonnement omfatter, skal du se Exchange Online tjenestebeskrivelserne for Meddelelsespolitik[, Gendannelse og overholdelse af regler og standarder](/office365/servicedescriptions/exchange-online-service-description/message-policy-and-compliance).

- Hvis du har Azure Rights Management, men det ikke er konfigureret til Exchange Online eller Exchange Online Protection, forklares det i denne artikel, hvordan du aktiverer Azure Rights Management, og derefter beskrives den bedste måde at konfigurere OME til at fungere med Azure Rights Management.

- Hvis du allerede har konfigureret OME til at fungere sammen med Azure Rights Management til Exchange Online eller Exchange Online Protection, kan du, afhængigt af hvordan du konfigurerer det, være klar til at begynde at bruge OME og de nye funktioner med det samme. Denne artikel forklarer, hvordan du finder ud af, om du har konfigureret OME korrekt, hvad du skal gøre, hvis du skal ændre din konfiguration, og hvad der sker, hvis du vælger ikke at ændre din konfiguration. For at kunne bruge de nye funktioner skal du f.eks. bruge Azure RMS med OME. Du kan ikke bruge de nye funktioner med en lokal Active Directory RMS.

## <a name="activate-azure-rights-management-for--the-previous-version-of-ome-in-office-365"></a>Aktivér Azure Rights Management for den tidligere version af OME Office 365

Du skal aktivere Azure Rights Management, så brugerne i organisationen kan anvende beskyttelse af oplysninger på meddelelser, de sender, og åbne meddelelser og filer, der er blevet beskyttet af Azure Rights Management-tjenesten. Du kan finde en vejledning [under Aktivering af Azure Rights Management](/azure/information-protection/activate-service). Når du har fuldført aktiveringen, skal du vende tilbage hertil og fortsætte med opgaverne i denne artikel.
  
## <a name="set-up-the-previous-version-of-ome-to-use-azure-rms-by-importing-trusted-publishing-domains-tpds"></a>Konfigurer den tidligere version af OME til at bruge Azure RMS ved at importere pålidelige publiceringsdomæner (TPD'er)

En TPD er en XML-fil, der indeholder oplysninger om organisationens indstillinger for rettighedsstyring. TPD'en indeholder f.eks. oplysninger om serverlicensorcertifikatet (SLC), der bruges til signering og kryptering af certifikater og licenser, URL-adresser, der bruges til licenser og publicering osv. Du importerer TPD'en til organisationen ved hjælp af Windows PowerShell.
  
> [!IMPORTANT]
> Tidligere kunne du vælge at importere TPD'er fra Active Directory Rights Management Service (AD RMS) til din organisation. Dette forhindrer dig dog i at bruge de nye OME-funktioner og anbefales ikke. Hvis din organisation aktuelt er konfigureret på denne måde, anbefaler Microsoft, at du opretter en plan for overførsel fra dit lokale Active Directory RMS til skybaseret Azure Information Protection. Få mere at vide under [Overførsel fra AD RMS til Azure Information Protection](/information-protection/plan-design/migrate-from-ad-rms-to-azure-rms). Du vil ikke kunne bruge de nye OME-funktioner, før du har fuldført overførslen til Azure Information Protection.
  
 **Sådan importeres TPD'er fra Azure RMS**
  
1. [Forbind til Exchange Online bruge Remote PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Vælg den URL-adresse til deling af nøgler, der svarer til organisationens geografiske placering:

|**Placering**|**URL-adresse til deling af nøgler**|
|:-----|:-----|
|Nordamerika  <br/> |https://sp-rms.na.aadrm.com/TenantManagement/ServicePartner.svc  <br/> |
|EU  <br/> |https://sp-rms.eu.aadrm.com/TenantManagement/ServicePartner.svc  <br/> |
|Asien  <br/> |https://sp-rms.ap.aadrm.com/TenantManagement/ServicePartner.svc  <br/> |
|Sydamerika  <br/> |https://sp-rms.sa.aadrm.com/TenantManagement/ServicePartner.svc  <br/> |
|Office 365 for Government (Government Community Cloud)  <br/> Denne RMS-placering for deling af nøgler er reserveret til kunder, der har Office 365 til offentlige SKU'er.  <br/> |https://sp-rms.govus.aadrm.com/TenantManagement/ServicePartner.svc  <br/> |
  
3. Konfigurer placeringen af deling af nøgler ved at køre [set-IRMConfiguration-cmdlet'en](/powershell/module/exchange/set-irmconfiguration) på følgende måde: 

   ```powershell
   Set-IRMConfiguration -RMSOnlineKeySharingLocation "<RMSKeySharingURL >"
   ```
  
   Hvis du f.eks. vil konfigurere nøgledelingsplaceringen, hvis din organisation er placeret i Nordamerika:

   ```powershell
   Set-IRMConfiguration -RMSOnlineKeySharingLocation "https://sp-rms.na.aadrm.com/TenantManagement/ServicePartner.svc"
   ```

4. Kør [cmdlet'en Import-RMSTrustedPublishingDomain](/powershell/module/exchange/import-rmstrustedpublishingdomain) med parameteren -RMSOnline for at importere TPD fra Azure Rights Management: 

   ```powershell
   Import-RMSTrustedPublishingDomain -RMSOnline -Name "<TPDName> "
   ```

   Hvor  *TPDName*  er det navn, du vil bruge til TPD. F.eks. "Contoso North American TPD". 

5. For at bekræfte at du har konfigureret organisationen til at bruge tjenesten Azure Rights Management, skal du køre cmdlet'en [Test-IRMConfiguration](/powershell/module/exchange/test-irmconfiguration) med parameteren -RMSOnline på følgende måde:

   ```powershell
   Test-IRMConfiguration -RMSOnline
   ```

   Denne cmdlet kontrollerer blandt andet forbindelsen med Azure Rights Management-tjenesten, downloader TPD'et og kontrollerer dets gyldighed.

6. Kør [Set-IRMConfiguration-cmdlet'en](/powershell/module/exchange/set-irmconfiguration) på følgende måde for at deaktivere, at Azure Rights Management-skabeloner bliver tilgængelige i Outlook på internettet og Outlook: 

   ```powershell
   Set-IRMConfiguration -ClientAccessServerEnabled $false
   ```

7. Kør [Set-IRMConfiguration-cmdlet'en](/powershell/module/exchange/set-irmconfiguration) på følgende måde for at aktivere Azure Rights Management for din skybaserede mailorganisation og konfigurere den til at bruge Azure Rights Management til Office 365-meddelelseskryptering:

   ```powershell
   Set-IRMConfiguration -InternalLicensingEnabled $true
   ```

8. For at bekræfte, at du har importeret TPD og aktiveret Azure Rights Management, skal du bruge Test-IRMConfiguration-cmdlet'en til at teste Azure Rights Management-funktionalitet. Du kan få mere at vide under "Eksempel 1" [i Test-IRMConfiguration](/powershell/module/exchange/test-irmconfiguration).

## <a name="i-have-the-previous-version-of-ome-set-up-with-active-directory-rights-management-not-azure-information-protection-what-do-i-do"></a>Jeg har den tidligere version af OME konfigureret med Active Directory Rights Management , ikke Azure Information Protection, hvad gør jeg?
<a name="importTPDs"> </a>

Du kan fortsætte med at bruge dine eksisterende Office 365-meddelelseskryptering regler for mailflow med Active Directory Rights Management, men du kan ikke konfigurere eller bruge de nye OME-funktioner. I stedet skal du overføre til Azure Information Protection. Du kan finde oplysninger om overførslen, og hvad det betyder for din organisation, under [Overførsel fra AD RMS til Azure Information Protection](/information-protection/deploy-use/prepare-environment-adrms).
  
## <a name="next-steps"></a>Næste trin
<a name="importTPDs"> </a>

Når du har fuldført konfigurationen af Azure Rights Management, og du vil aktivere de nye OME-funktioner, skal du se Konfigurer nye Office 365-meddelelseskryptering-funktioner, der er bygget oven på [Azure Information Protection.](./set-up-new-message-encryption-capabilities.md)
  
Når du har konfigureret din organisation til at bruge de nye OME-funktioner, er du klar til at definere regler for mailflow for at beskytte mails med nye [OME-funktioner](define-mail-flow-rules-to-encrypt-email.md).
  
## <a name="related-topics"></a>Relaterede emner
<a name="importTPDs"> </a>

[Kryptering i Office 365](encryption.md)
  
[Tekniske referenceoplysninger om kryptering i Office 365](technical-reference-details-about-encryption.md)
  
[Hvad er Azure Rights Management?](/information-protection/understand-explore/what-is-azure-rms)