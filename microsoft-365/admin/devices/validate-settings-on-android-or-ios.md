---
title: Valider indstillinger for appbeskyttelse på Android- eller iOS-enheder
f1.keywords:
- NOCSH
ms.author: sharik
author: skjerland
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- M365-identity-device-management
- Adm_TOC
ms.custom:
- Adm_O365
- Core_O365Admin_Migration
- MSB365
- OKR_SMB_M365
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
ms.assetid: f3433b6b-02f7-447f-9d62-306bf03638b0
description: Få mere at vide om, hvordan du validerer indstillingerne for Microsoft 365 Business Premium appbeskyttelse på dine Android- eller iOS-enheder.
ms.openlocfilehash: 7e1355f71e9757e1055999e1951b4f093b0d21a0
ms.sourcegitcommit: 7dc7e9fd76adf848f941919f86ca25eecc704015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/11/2022
ms.locfileid: "65317910"
---
# <a name="validate-app-protection-settings-on-android-or-ios-devices"></a>Valider indstillinger for appbeskyttelse på Android- eller iOS-enheder

> [!NOTE]
> Microsoft Defender til virksomheder udrulles til Microsoft 365 Business Premium kunder fra den 1. marts 2022. Dette tilbud indeholder yderligere sikkerhedsfunktioner til enheder. [Få mere at vide om Defender for Business](../../security/defender-business/mdb-overview.md)

Følg vejledningen i følgende afsnit for at validere indstillinger for appbeskyttelse på Android- eller iOS-enheder.
  
## <a name="android"></a>Android
  
### <a name="check-that-the-app-protection-settings-are-working-on-user-devices"></a>Kontrollér, at indstillingerne for appbeskyttelse fungerer på brugerenheder

Når du [har angivet indstillinger for appbeskyttelse for Android- eller iOS-enheder for](../../business-premium/m365bp-app-protection-settings-for-android-and-ios.md) at beskytte appsene, kan du følge disse trin for at validere, at de indstillinger, du vælger, fungerer. 
  
Først skal du sørge for, at politikken gælder for den app, hvor du vil validere den.
  
1. I Microsoft 365 Business Premium [Administration](https://admin.microsoft.com) skal du gå til **Politikker** \> **Rediger politik**.
    
2. Vælg **Programpolitik til Android** for de indstillinger, du oprettede under konfigurationen, eller en anden politik, du har oprettet, og bekræft, at den f.eks. gennemtvinges for Outlook. 
    
    ![Skærmbillede, der viser alle de apps, som denne politik beskytter filer til.](../../media/b3be3ddd-f683-4073-8d7a-9c639a636a2c.png)
  
### <a name="validate-require-a-pin-or-a-fingerprint-to-access-office-apps"></a>Valider Kræv en pinkode eller et fingeraftryk for at få adgang til Office apps

I ruden **Rediger politik** skal du vælge **Rediger** ud for **Office dokumentadgangskontrol**, udvide **Administrer, hvordan brugere får adgang Office filer på mobilenheder**, og sørg for, at **Kræv en pinkode eller et fingeraftryk for at få adgang til Office apps** er angivet til **Til**.
  
![Sørg for, at Kræv en pinkode eller et fingeraftryk for at få adgang til Office apps er slået til.](../../media/f37eb5b2-7e26-49fb-9bd6-d955d196bacf.png)
  
1. Åbn Outlook på brugerens Android-enhed, og log på med brugerens Microsoft 365 Business Premium legitimationsoplysninger.
    
2. Du bliver også bedt om at angive en pinkode eller bruge et fingeraftryk.
    
    ![Angiv en pinkode på din Android-enhed for at få adgang til Office apps.](../../media/9e8ecfee-8122-4a3a-8918-eece80344310.png)
  
### <a name="validate-reset-pin-after-number-of-failed-attempts"></a>Valider nulstilling af pinkode efter antal mislykkede forsøg

I ruden **Rediger politik** skal du vælge **Rediger** ud for **Office dokumentadgangskontrol**, udvide **Administrer, hvordan brugere får adgang Office filer på mobilenheder**, og sørg for, at **Nulstil pinkode efter antal mislykkede forsøg** er angivet til et tal. Dette er som standard 5. 
  
1. Åbn Outlook på brugerens Android-enhed, og log på med brugerens Microsoft 365 Business Premium legitimationsoplysninger.
    
2. Angiv en forkert pinkode så mange gange, som det er angivet i politikken. Du får vist en meddelelse om, at **grænsen for pinkodeforsøg er nået** for at nulstille pinkoden. 
    
    ![Skærmbillede, der angiver, at du skal nulstille din pinkode efter for mange forkerte pinkodeforsøg.](../../media/fca6fcb4-bb5c-477f-af5e-5dc937e8b835.png)
  
3. Tryk på **Nulstil pinkode**. Du bliver bedt om at logge på med brugerens Microsoft 365 Business Premium legitimationsoplysninger og derefter angive en ny pinkode.
    
### <a name="validate-force-users-to-save-all-work-files-to-onedrive-for-business"></a>Valider Tving brugere til at gemme alle arbejdsfiler i OneDrive for Business

I ruden **Rediger politik** skal du vælge **Rediger** ud for **Beskyttelse mod mistede eller stjålne enheder**, udvide **Beskyt arbejdsfiler, når enheder mistes eller bliver stjålet**, og sørge for, at **Tving brugere til at gemme alle arbejdsfiler til OneDrive for Business** er **slået til.**
  
![Kontrollér, at Tving brugere til at gemme alle arbejdsfiler til OneDrive for Business er slået til.](../../media/7140fa1d-966d-481c-829f-330c06abb5a5.png)
  
1. Åbn Outlook på brugerens Android-enhed, og log på med brugerens Microsoft 365 Business Premium legitimationsoplysninger, og angiv en pinkode, hvis der er anmodet om det.
    
2. Åbn en mail, der indeholder en vedhæftet fil, og tryk på pil ned-ikonet ud for den vedhæftede fils oplysninger.
    
    ![Tryk på pil ned ud for en vedhæftet fil for at prøve at gemme den.](../../media/b22573bb-91ce-455f-84fa-8feb2846b117.png)
  
    Du kan se **Kan ikke gemme på enheden** nederst på skærmen. 
    
    ![Advarselstekst, der angiver, at en fil ikke kan gemmes lokalt på en Android-fil.](../../media/52ca3f3d-7ed0-4a52-9621-4872da6ea9c5.png)
  
    > [!NOTE]
    > Lagring på OneDrive for Business er ikke aktiveret for Android på nuværende tidspunkt, så du kan kun se, at lagring lokalt er blokeret. 
  
### <a name="validate-require-user-to-sign-in-again-if-office-apps-have-been-idle-for-a-specified-time"></a>Valider Kræv, at brugeren logger på igen, hvis Office apps har været inaktive i et angivet tidsrum

I ruden **Rediger politik** skal du vælge **Rediger** ud for **Office dokumentadgangskontrol**, udvide **Administrer, hvordan brugere får adgang Office filer på mobilenheder**, og sørg for, at **Kræv, at brugerne logger på igen, når Office apps har været inaktive i** et antal minutter. Dette er som standard 30 minutter. 
  
1. Åbn Outlook på brugerens Android-enhed, og log på med brugerens Microsoft 365 Business Premium legitimationsoplysninger, og angiv en pinkode, hvis der er anmodet om det.
    
2. Du bør nu kunne se Outlook indbakke. Lad Android-enheden være inaktiv i mindst 30 minutter (eller en anden mængde tid, længere end det, du angav i politikken). Enheden vil sandsynligvis være nedtonet.
    
3. Få adgang Outlook på Android-enheden igen.
    
4. Du bliver bedt om at angive din pinkode, før du kan få adgang til Outlook igen.
    
### <a name="validate-protect-work-files-with-encryption"></a>Valider Beskyt arbejdsfiler med kryptering

I ruden **Rediger politik** skal du vælge **Rediger** ud for **Beskyttelse mod mistede eller stjålne enheder**, udvide **Beskyt arbejdsfiler, når enheder mistes eller bliver stjålet**, og sørge for, at **Beskyt arbejdsfiler med kryptering** er **slået til,** og **Tving brugere til at gemme alle arbejdsfiler til OneDrive for Business** er slået **fra**.
  
1. Åbn Outlook på brugerens Android-enhed, og log på med brugerens Microsoft 365 Business Premium legitimationsoplysninger, og angiv en pinkode, hvis der er anmodet om det.
    
2. Åbn en mail, der indeholder nogle få vedhæftede billedfiler.
    
3. Tryk på pil ned-ikonet ud for den vedhæftede fils oplysninger for at gemme den.
    
    ![Tryk på pil ned for at gemme figurfilen på Android-enheden.](../../media/08a9e21e-4022-45d5-acff-59cface651e7.png)
  
4. Du bliver muligvis bedt om at give Outlook adgang til fotos, medier og filer på din enhed. Tryk på **Tillad**.
    
5. Nederst på skærmen skal du vælge **Gem på enhed** og derefter åbne appen **Galleri** . 
    
6. Du bør kunne se et krypteret billede (eller flere, hvis du har gemt flere vedhæftede filer) på listen. Den vises muligvis på listen Billeder som et gråt kvadrat med et hvidt udråbstegn i en hvid cirkel midt i det grå kvadrat.
    
    ![En krypteret billedfil i galleriappen.](../../media/25936414-bd7e-421d-824e-6e59b877722d.png)
  
## <a name="ios"></a>Ios
  
### <a name="check-that-the-app-protection-settings-are-working-on-user-devices"></a>Kontrollér, at indstillingerne for Appbeskyttelse fungerer på brugerenheder

Når du [har angivet appkonfigurationer for iOS-enheder for](../../business-premium/m365bp-protection-settings-for-windows-10-devices.md) at beskytte apps, kan du følge disse trin for at validere, at de indstillinger, du vælger, fungerer. 
  
Først skal du sørge for, at politikken gælder for den app, hvor du vil validere den.
  
1. I Microsoft 365 Business Premium [Administration](https://admin.microsoft.com) skal du gå til **Politikker** \> **Rediger politik**.
    
2. Vælg **Programpolitik til iOS** for de indstillinger, du oprettede under konfigurationen, eller en anden politik, du har oprettet, og bekræft, at den f.eks. gennemtvinges for Outlook. 
    
    ![Skærmbillede, der viser alle de apps, som denne politik beskytter filer til.](../../media/842441b8-e7b1-4b86-9edd-d94d1f77b6f4.png)
  
### <a name="validate-require-a-pin-to-access-office-apps"></a>Valider Kræv en pinkode for at få adgang til Office apps

I ruden **Rediger politik** skal du vælge **Rediger** ud for **Office dokumentadgangskontrol**, udvide **Administrer, hvordan brugere får adgang Office filer på mobilenheder**, og sørg for, at **Kræv en pinkode eller et fingeraftryk for at få adgang til Office apps** er angivet til **Til**.
  
![Sørg for, at Kræv en pinkode eller et fingeraftryk for at få adgang til Office apps er slået til.](../../media/f37eb5b2-7e26-49fb-9bd6-d955d196bacf.png)
  
1. Åbn Outlook på brugerens iOS-enhed, og log på med brugerens Microsoft 365 Business Premium legitimationsoplysninger.
    
2. Du bliver også bedt om at angive en pinkode eller bruge et fingeraftryk.
    
    ![Angiv en pinkode på din IOS-enhed for at få adgang til Office apps.](../../media/06fc5cf3-9f19-4090-b23c-14bb59805b7a.png)
  
### <a name="validate-reset-pin-after-number-of-failed-attempts"></a>Valider nulstilling af pinkode efter antal mislykkede forsøg

I ruden **Rediger politik** skal du vælge **Rediger** ud for **Office dokumentadgangskontrol**, udvide **Administrer, hvordan brugere får adgang Office filer på mobilenheder**, og sørg for, at **Nulstil pinkode efter antal mislykkede forsøg** er angivet til et tal. Dette er som standard 5. 
  
1. Åbn Outlook på brugerens iOS-enhed, og log på med brugerens Microsoft 365 Business Premium legitimationsoplysninger.
    
2. Angiv en forkert pinkode så mange gange, som det er angivet i politikken. Du får vist en meddelelse om, at **grænsen for pinkodeforsøg er nået** for at nulstille pinkoden. 
    
    ![Skærmbillede, der viser en advarsel om nulstilling af pinkode efter for mange forkerte forsøg.](../../media/fab5c089-a4a5-4e8d-8c95-b8eed1dfa262.png)
  
3. Tryk på **OK**. Du bliver bedt om at logge på med brugerens Microsoft 365 Business Premium legitimationsoplysninger og derefter angive en ny pinkode.
    
### <a name="validate-force-users-to-save-all-work-files-to-onedrive-for-business"></a>Valider Tving brugere til at gemme alle arbejdsfiler i OneDrive for Business

I ruden **Rediger politik** skal du vælge **Rediger** ud for **Beskyttelse mod mistede eller stjålne enheder**, udvide **Beskyt arbejdsfiler, når enheder mistes eller bliver stjålet**, og sørge for, at **Tving brugere til at gemme alle arbejdsfiler til OneDrive for Business** er **slået til.**
  
![Kontrollér, at Tving brugere til at gemme alle arbejdsfiler til OneDrive for Business er slået til.](../../media/7140fa1d-966d-481c-829f-330c06abb5a5.png)
  
1. Åbn Outlook på brugerens iOS-enhed, og log på med brugerens Microsoft 365 Business Premium legitimationsoplysninger, og angiv en pinkode, hvis der er anmodet om det.
    
2. Åbn en mail, der indeholder en vedhæftet fil, åbn den vedhæftede fil, og vælg **Gem** nederst på skærmen. 
    
    ![Tryk på indstillingen Gem, når du har åbnet en vedhæftet fil for at prøve at gemme den.](../../media/b419b070-1530-4f14-86a8-8d89933a2b25.png)
  
3. Du bør kun se en indstilling for OneDrive for Business. Hvis det ikke er det, skal du trykke på **Tilføj konto** og vælge **OneDrive for Business** på skærmen **Tilføj Storage konto**. Angiv slutbrugerens Microsoft 365 Business Premium til at logge på, når du bliver bedt om det. 
    
    Tryk på **Gem**, og vælg **OneDrive for Business**.
    
### <a name="validate-require-user-to-sign-in-again-if-office-apps-have-been-idle-for-a-specified-time"></a>Valider Kræv, at brugeren logger på igen, hvis Office apps har været inaktive i et angivet tidsrum

I ruden **Rediger politik** skal du vælge **Rediger** ud for **Office dokumentadgangskontrol**, udvide **Administrer, hvordan brugere får adgang Office filer på mobilenheder**, og sørg for, at **Kræv, at brugerne logger på igen, når Office apps har været inaktive i** et antal minutter. Dette er som standard 30 minutter. 
  
1. Åbn Outlook på brugerens iOS-enhed, og log på med brugerens Microsoft 365 Business Premium legitimationsoplysninger, og angiv en pinkode, hvis der er anmodet om det.
    
2. Du bør nu kunne se Outlook indbakke. Lad iOS-enheden være uberørt i mindst 30 minutter (eller en anden mængde tid, længere end det, du angav i politikken). Enheden vil sandsynligvis være nedtonet.
    
3. Få adgang Outlook på iOS-enheden igen.
    
4. Du bliver bedt om at angive din pinkode, før du kan få adgang til Outlook igen.
    
### <a name="validate-protect-work-files-with-encryption"></a>Valider Beskyt arbejdsfiler med kryptering

I ruden **Rediger politik** skal du vælge **Rediger** ud for **Beskyttelse mod mistede eller stjålne enheder**, udvide **Beskyt arbejdsfiler, når enheder mistes eller bliver stjålet**, og sørge for, at **Beskyt arbejdsfiler med kryptering** er **slået til,** og **Tving brugere til at gemme alle arbejdsfiler til OneDrive for Business** er slået **fra**.
  
1. Åbn Outlook på brugerens iOS-enhed, og log på med brugerens Microsoft 365 Business Premium legitimationsoplysninger, og angiv en pinkode, hvis der er anmodet om det.
    
2. Åbn en mail, der indeholder nogle få vedhæftede billedfiler.
    
3. Tryk på den vedhæftede fil, og tryk derefter på indstillingen **Gem** under den. 
    
4. Åbn **Fotos** app fra startskærmen. Du bør kunne se et krypteret billede (eller flere, hvis du har gemt flere vedhæftede filer med billeder), som er gemt, men krypteret. 
    

## <a name="see-also"></a>Se også

[Bedste praksis for sikring af Microsoft 365 til forretningsplaner](../security-and-compliance/secure-your-business-data.md)