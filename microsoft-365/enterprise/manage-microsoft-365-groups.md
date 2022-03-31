---
title: Administrer Microsoft 365-grupper
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
audience: Admin
ms.topic: overview
ms.prod: office-online-server
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-mar2020
ms.collection:
- Ent_O365
- M365-subscription-management
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: 98ca5b3f-f720-4d8e-91be-fe656548a25a
description: Få mere at vide om, hvordan du administrerer Microsoft 365-grupper.
ms.openlocfilehash: 28d8bae8aaed6d02fe082824c07afe03bdc0ce5a
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63601689"
---
# <a name="manage-microsoft-365-groups"></a>Administrer Microsoft 365-grupper

*Denne artikel gælder for både Microsoft 365 Enterprise og Office 365 Enterprise.*

Du kan administrere Microsoft 365-grupper på flere forskellige måder, afhængigt af din konfiguration. Du kan administrere brugerkonti i [Microsoft 365](/admin) Administration, PowerShell, i Active Directory-domæneservices (AD DS) eller i [Azure Active Directory (Azure AD) Administration](/azure/active-directory/fundamentals/active-directory-groups-create-azure-portal). 

## <a name="plan-for-where-and-how-you-will-manage-your-groups"></a>Planlæg, hvor og hvordan du vil administrere dine grupper

Hvor og hvordan du kan administrere dine brugerkonti afhænger af den identitetsmodel, du vil bruge til din Microsoft 365. De to overordnede modeller er kun skybaserede og hybride.
  
### <a name="cloud-only"></a>Kun i skyen

Du kan oprette og administrere grupper med:

- [Microsoft 365 Administration](/admin)
- [PowerShell](maintain-group-membership-with-microsoft-365-powershell.md)
- [Azure AD Administration](/azure/active-directory/fundamentals/active-directory-groups-create-azure-portal)
    
### <a name="hybrid"></a>Hybrid

AD DS grupper synkroniseres med Microsoft 365 fra AD DS, så du skal bruge lokale AD DS til at administrere disse grupper.

Du kan også oprette og administrere Azure AD-grupper, der er adskilt fra AD DS grupper, men som kan indeholde brugere og grupper AD DS. I dette tilfælde kan du bruge:

- [Microsoft 365 Administration](/admin)
- [PowerShell](maintain-group-membership-with-microsoft-365-powershell.md)
- [Azure AD Administration](/azure/active-directory/fundamentals/active-directory-groups-create-azure-portal)

## <a name="allow-users-to-create-and-manage-their-own-groups"></a>Tillad brugere at oprette og administrere deres egne grupper

Azure AD tillader grupper, der kan administreres af gruppeejere i stedet for it-administratorer. Denne funktion *er kendt som selvbetjeningsadministration* af grupper og giver gruppeejere, der ikke er tildelt en administrativ rolle, mulighed for at oprette og administrere sikkerhedsgrupper. 

Brugere kan anmode om medlemskab af en sikkerhedsgruppe, og denne anmodning går til gruppeejeren i stedet for en it-administrator. Dette gør det muligt for den daglige kontrol af gruppemedlemskab at blive uddelegeret til team-, projekt- eller virksomhedsejere, der forstår brugen af gruppen og kan administrere medlemskabet.

>[!Note]
>Selvbetjeningsadministration af grupper er kun tilgængelig for Azure AD-sikkerhed og Microsoft 365-grupper. Den er ikke tilgængelig for mailaktiverede grupper, distributionslister eller grupper, der er blevet synkroniseret fra AD DS.
>

Du kan finde flere oplysninger i vejledningen [til konfiguration af en Azure AD-gruppe til selvbetjeningsstyring](/azure/active-directory/active-directory-accessmanagement-self-service-group-management).

## <a name="set-up-dynamic-group-membership"></a>Konfigurere dynamisk gruppemedlemskab

Azure AD understøtter konfiguration af en række regler, der automatisk tilføjer eller fjerner brugerkonti som medlemmer af en Azure AD-gruppe. Dette kaldes dynamisk *gruppemedlemskab*. Reglerne er baseret på brugerkontoattributter, f.eks. Afdeling eller Land.

Sådan anvendes reglerne:

- Hvis en ny brugerkonto opfylder alle reglerne for gruppen, bliver den medlem.
- Hvis en brugerkonto ikke er medlem af gruppen, men dens attributter ændres, så den svarer til alle reglerne for gruppen, bliver den medlem af den pågældende gruppe.
- Hvis en brugerkonto ikke opfylder alle reglerne for gruppen, føjes den ikke til gruppen.
- Hvis en brugerkonto er medlem af gruppen, men dens attributter ændres, så den ikke længere stemmer overens med alle reglerne for gruppen, fjernes den som medlem af gruppen.

Hvis du vil bruge dynamisk medlemskab, skal du først bestemme de grupper, der har et fælles sæt af brugerkontoattributter. Alle medlemmer af salgsafdelingen skal f.eks. være i gruppen Salgs Azure AD baseret på brugerkontoattributten Afdeling angivet til "Salg".

Se vejledningen [for at oprette og konfigurere reglerne for en dynamisk Azure AD-gruppe](/azure/active-directory/active-directory-groups-dynamic-membership-azure-portal).

## <a name="set-up-automatic-licensing"></a>Konfigurer automatisk licensering

Du kan konfigurere sikkerhedsgrupper i Azure AD til automatisk at tildele licenser fra et sæt abonnementer til alle gruppens medlemmer. Dette kaldes *gruppebaseret licensering*. Hvis en brugerkonto tilføjes eller fjernes fra gruppen, tildeles eller ophæves licenserne for gruppens abonnementer automatisk fra brugerkontoen.

For Microsoft 365 Enterprise skal du konfigurere Azure AD-sikkerhedsgrupper til at tildele den relevante Microsoft 365 Enterprise-licens.

Sørg for, at du har nok licenser til alle gruppemedlemmerne. Hvis du løber tør for licenser, vil nye brugere ikke få tildelt licenser, før licenser bliver tilgængelige.

>[!Note]
>Du bør ikke konfigurere gruppebaseret licensering for grupper, der indeholder B2B-konti (Azure Business to Business).
>

Få mere at vide under [Gruppebaserede grundlæggende licenser i Azure AD](/azure/active-directory/active-directory-licensing-whatis-azure-portal).

Se vejledningen [til konfiguration af gruppebaserede licenser til en Azure-sikkerhedsgruppe](/azure/active-directory/active-directory-licensing-group-assignment-azure-portal).