---
title: Fejlfinding Microsoft 365 af forbrugsanalyse
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: a73632a1-62c8-4a13-8115-913773b30f93
description: Få mere at vide om, hvordan du foretager Microsoft 365 med skabelonappen Til brugsanalyse.
ms.openlocfilehash: afa9841b38beefcfdd091f27e7b1f328cdf52a5e
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/15/2021
ms.locfileid: "63590133"
---
# <a name="troubleshooting-microsoft-365-usage-analytics"></a>Fejlfinding Microsoft 365 af forbrugsanalyse

Udforsk følgende liste over fejlmeddelelser for at få hjælp til de mest almindelige problemer med Microsoft 365 til forbrugsanalyse.
  
    
## <a name="we-are-unable-to-process-your-request-you-have-to-first-subscribe-to-this-data-from-the-microsoft-365-admin-center"></a>Vi kan ikke behandle din anmodning. Du skal først abonnere på disse data fra Microsoft 365 Administration

 **Fejlkode:** 422 
  
 **Hvor du får vist denne meddelelse:** Klik Power BI, når du opretter forbindelse til Microsoft 365-skabelonappen til forbrugsanalyse, eller når du ringer direkte til Microsoft 365 API'er til rapportering. 
  
 **Årsag:** Før du kan oprette forbindelse til appen, skal du abonnere på dataene fra Microsoft 365 Administration. Hvis dette trin ikke udføres først, kan du ikke oprette forbindelse til skabelonappen, heller ikke selvom du angiver dit Microsoft 365-lejer-id. 
  
 **Sådan løser du fejlen:** Hvis du vil abonnere på dataene, skal \>  \> du gå til Administration Rapporterer brug af rapporter Microsoft 365 finde feltet Microsoft 365 på den primære dashboardside.<a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank"></a> Vælg knappen **Introduktion,** og i ruden Rapporter,  der åbnes, skal du derefter slå indstillingen Gør **data tilgængelige Microsoft 365 for Power BI** til og **Gem**.
  
## <a name="we-are-processing-your-data"></a>Vi er i gang med at behandle dine data

 **Hvor du får vist denne meddelelse:** I feltet **Microsoft 365 for forbrugsanalyse** på **dashboardet** For brug i Microsoft 365 Administration. 
  
 **Årsag:** Når du [vælger at se data i skabelonappen](enable-usage-analytics.md) fra Microsoft 365 Administration, begynder Microsoft 365 at generere historiske brugsdata for organisationen. Afhængigt af størrelsen på din lejer kan dette trin tage et sted mellem 2 til 48 timer. 
  
 **Sådan løser du det:** Bare vær tålmodig, men hvis meddelelsen ikke ændres til Dine **data** er klar efter 3 dage, [kontakt Microsoft 365 for Business-support](Få support](.. /get-help-support.md).
  
## <a name="we-are-unable-to-process-your-request-at-this-time-we-are-still-preparing-the-data-for-your-organization"></a>Vi kan ikke behandle din anmodning på nuværende tidspunkt. Vi er stadig i gang med at forberede data for din organisation

 **Fejlkode:** 423 
  
 **Hvor du får vist denne meddelelse:** På Power BI når du opretter forbindelse til Microsoft 365-skabelonappen til forbrugsanalyse, eller når du kalder Microsoft 365 API'er til rapportering. 
  
 **Årsag:** Når du [vælger at se data](enable-usage-analytics.md) i skabelonappen fra Administration, begynder Microsoft 365 at generere historiske brugsdata for organisationen. Afhængigt af størrelsen på din lejer kan dette trin tage et sted mellem to til 48 timer. 
  
 **Sådan løser du det:** Bare vær tålmodig, men hvis meddelelsen ikke ændres til Dine **data** er klar, selv 3 dage siden opstarten, skal [du Microsoft 365 til support til virksomheder](../../business-video/get-help-support.md).
  
## <a name="the-tenant-id-you-provided-is-not-in-the-correct-format"></a>Det angivne lejer-id er ikke i det korrekte format

 **Fejlkode:** 400 
  
 **Hvor du får vist denne meddelelse:** På Power BI når du opretter forbindelse til Microsoft 365-skabelonappen til forbrugsanalyse, eller når du kalder Microsoft 365 API'er til rapportering. 
  
 **Årsag:** Lejer-id'et er et guid og skal være i formatet xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx. Hvis du angiver en anden streng i inputfeltet for lejeren, får du denne fejl. 
  
 **Sådan løser du fejlen:** Gå til Administration Rapporterer **anvendelse** \> \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">,</a> og find Microsoft 365 for Forbrugsanalyse på den primære dashboardside. Lejer-id'et er angivet i feltet. Du kan kopiere den herfra og indsætte den i dialogboksen for at oprette forbindelse til skabelonappen. 
  
## <a name="the-tenant-id-you-provided-is-not-recognized-by-our-system"></a>Det angivne lejer-id genkendes ikke af vores system

 **Fejlkode:** 404 
  
 **Hvor du får vist denne meddelelse:** Klik Power BI, når du opretter forbindelse til Microsoft 365-skabelonappen til forbrugsanalyse, eller når du ringer direkte til Microsoft 365 API'er til rapportering. 
  
 **Årsag:** Det angivne lejer-id er ikke gyldigt eller findes ikke. 
  
 **Sådan løser du fejlen:** Gå til Administration Rapporterer **anvendelse** \> \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">,</a> og find Microsoft 365 for Forbrugsanalyse på den primære dashboardside. Lejer-id'et er angivet i feltet. Du kan kopiere den herfra og indsætte den i dialogboksen for at oprette forbindelse til skabelonappen. 
  
## <a name="please-re-enter-your-credentials-to-sign-in-to-power-bi-again"></a>Angiv dine legitimationsoplysninger igen for at logge på Power BI igen

Fejlkode: 302
  
 **Hvor du får vist denne meddelelse:** Klik Power BI, når du opretter forbindelse til Microsoft 365-skabelonappen til forbrugsanalyse, eller når du ringer direkte til Microsoft 365 API'er til rapportering. 
  
 **Årsag:** Godkendelseskoden mislykkedes og kan kræve, at du skal angive dine legitimationsoplysninger igen. 
  
 **Sådan løser du fejlen:** Log af Power BI, og log derefter på igen. 
  
## <a name="you-do-not-have-the-right-authorization-to-access-to-this-data-to-be-able-to-gain-access-to-the-data-from-this-service-you-need-to-be-either-a-global-admin-or-any-one-of-the-product-admins"></a>Du har ikke den rette tilladelse til at få adgang til disse data. Hvis du vil have adgang til dataene fra denne tjeneste, skal du enten være global administrator eller en af produktadministratorerne

 **Fejlkode:** 403 
  
 **Hvor du får vist denne meddelelse:** Klik Power BI, når du opretter forbindelse til Microsoft 365-skabelonappen til forbrugsanalyse, eller når du ringer direkte til Microsoft 365 API'er til rapportering. 
  
 **Årsag:** Godkendelseskoden mislykkedes, fordi den bruger, der forsøgte at oprette forbindelse til skabelonappen, ikke har det rette tilladelsesniveau til at få adgang til disse data. 
  
 **Sådan løser du fejlen:** Angiv legitimationsoplysninger for en bruger, der enten er **global** administrator, **Exchange-administrator**, **Skype for Business-administrator**, **SharePoint-administrator**, **global** læser eller rapportlæser for at oprette forbindelse  til skabelonappen. Se [Om administratorroller for](../add-users/about-admin-roles.md) at få flere oplysninger. 
  
## <a name="refresh-failed"></a>Opdatering mislykkedes

 **Hvor du får vist denne meddelelse:** Mail fra Power BI eller mislykket status i opdateringsoversigten. 
  
 **Årsag:** Nogle gange nulstilles legitimationsoplysningerne for den bruger, der har oprettet forbindelse til skabelonappen, og de opdateres ikke i forbindelsesindstillingerne i skabelonappen, hvilket medfører, at brugeren får vist fejlmeddelelser om, at opdateringen mislykkedes. 
  
 **Sådan løser du fejlen:** I Power BI skal du finde det datasæt, der svarer Microsoft 365 skabelonappen til Microsoft 365, vælge planlæg opdatering og  angive dine administratorlegitimationsoplysninger. 
  
Hvis det ikke virker, skal du rydde cachen og oprette skabelonappen igen.
  
  
