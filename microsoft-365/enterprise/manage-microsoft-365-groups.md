---
title: Administrere Microsoft 365 grupper
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: Få mere at vide om, hvordan du administrerer Microsoft 365 grupper.
ms.openlocfilehash: 0e7cef7d1b55f695af9a33f22393172f6eee6485
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65100495"
---
# <a name="manage-microsoft-365-groups"></a>Administrere Microsoft 365 grupper

*Denne artikel gælder både for Microsoft 365 Enterprise og Office 365 Enterprise.*

Du kan administrere Microsoft 365 grupper på flere forskellige måder, afhængigt af din konfiguration. Du kan administrere brugerkonti i [Microsoft 365 Administration](/admin), PowerShell, i Active Directory-domæneservices (AD DS) eller i [Azure Active Directory (Azure AD) Administration](/azure/active-directory/fundamentals/active-directory-groups-create-azure-portal). 

## <a name="plan-for-where-and-how-you-will-manage-your-groups"></a>Planlæg, hvor og hvordan du vil administrere dine grupper

Hvor og hvordan du kan administrere dine brugerkonti, afhænger af den identitetsmodel, du vil bruge til dine Microsoft 365. De to overordnede modeller er cloudbaserede og hybride.
  
### <a name="cloud-only"></a>Kun i skyen

Du opretter og administrerer grupper med:

- [Microsoft 365 Administration](/admin)
- [PowerShell](maintain-group-membership-with-microsoft-365-powershell.md)
- [Azure AD Administration](/azure/active-directory/fundamentals/active-directory-groups-create-azure-portal)
    
### <a name="hybrid"></a>Hybrid

AD DS-grupper synkroniseres med Microsoft 365 fra AD DS, så du skal bruge AD DS-værktøjer i det lokale miljø til at administrere disse grupper.

Du kan også oprette og administrere Azure AD-grupper, der er adskilt fra AD DS-grupper, men som kan indeholde brugere og grupper fra AD DS. I dette tilfælde kan du bruge:

- [Microsoft 365 Administration](/admin)
- [PowerShell](maintain-group-membership-with-microsoft-365-powershell.md)
- [Azure AD Administration](/azure/active-directory/fundamentals/active-directory-groups-create-azure-portal)

## <a name="allow-users-to-create-and-manage-their-own-groups"></a>Tillad brugere at oprette og administrere deres egne grupper

Azure AD tillader grupper, der kan administreres af gruppeejere i stedet for it-administratorer. Denne funktion, der kaldes *selvbetjent gruppeadministration*, gør det muligt for gruppeejere, der ikke har fået tildelt en administrativ rolle, at oprette og administrere sikkerhedsgrupper. 

Brugerne kan anmode om medlemskab af en sikkerhedsgruppe, og denne anmodning sendes til gruppens ejer i stedet for en it-administrator. Dette gør det muligt at delegere den daglige kontrol over gruppemedlemskabet til team-, projekt- eller virksomhedsejere, der forstår den forretningsmæssige brug af gruppen og kan administrere dens medlemskab.

>[!Note]
>Selvbetjent gruppeadministration er kun tilgængelig for Azure AD-sikkerhed og Microsoft 365 grupper. Den er ikke tilgængelig for mailaktiverede grupper, distributionslister eller grupper, der er synkroniseret fra AD DS.
>

Du kan finde flere oplysninger i [vejledningen til at konfigurere en Azure AD-gruppe til selvbetjeningsadministration](/azure/active-directory/active-directory-accessmanagement-self-service-group-management).

## <a name="set-up-dynamic-group-membership"></a>Konfigurer dynamisk gruppemedlemskab

Azure AD understøtter konfiguration af en række regler, der automatisk tilføjer eller fjerner brugerkonti som medlemmer af en Azure AD-gruppe. Dette kaldes *dynamisk gruppemedlemskab*. Reglerne er baseret på brugerkontoattributter, f.eks. Afdeling eller Land.

Sådan anvendes reglerne:

- Hvis en ny brugerkonto stemmer overens med alle reglerne for gruppen, bliver den medlem.
- Hvis en brugerkonto ikke er medlem af gruppen, men dens attributter ændres, så den stemmer overens med alle reglerne for gruppen, bliver den medlem af gruppen.
- Hvis en brugerkonto ikke stemmer overens med alle reglerne for gruppen, føjes den ikke til gruppen.
- Hvis en brugerkonto er medlem af gruppen, men dens attributter ændres, så den ikke længere stemmer overens med alle reglerne for gruppen, fjernes den som medlem af gruppen.

Hvis du vil bruge dynamisk medlemskab, skal du først bestemme de grupper, der har et fælles sæt brugerkontoattributter. Alle medlemmer af salgsafdelingen skal f.eks. være i sales Azure AD-gruppen baseret på attributten Afdeling for brugerkontoen, der er angivet til "Salg".

Se [instruktionerne for at oprette og konfigurere reglerne for en dynamisk Azure AD-gruppe](/azure/active-directory/active-directory-groups-dynamic-membership-azure-portal).

## <a name="set-up-automatic-licensing"></a>Konfigurer automatisk licensering

Du kan konfigurere sikkerhedsgrupper i Azure AD for automatisk at tildele licenser fra et sæt abonnementer til alle medlemmer af gruppen. Dette kaldes *gruppebaserede licenser*. Hvis en brugerkonto føjes til eller fjernes fra gruppen, tildeles eller ikke-tildeles licenserne til gruppens abonnementer automatisk fra brugerkontoen.

For Microsoft 365 Enterprise skal du konfigurere Azure AD-sikkerhedsgrupper for at tildele den relevante Microsoft 365 Enterprise licens.

Sørg for, at du har tilstrækkelige licenser til alle gruppemedlemmerne. Hvis du løber tør for licenser, tildeles nye brugere ikke licenser, før licenser bliver tilgængelige.

>[!Note]
>Du bør ikke konfigurere gruppebaserede licenser for grupper, der indeholder B2B-konti (Azure Business to Business).
>

Du kan få flere oplysninger under [Grundlæggende om gruppebaserede licenser i Azure AD](/azure/active-directory/active-directory-licensing-whatis-azure-portal).

Se [vejledningen til konfiguration af gruppebaserede licenser for en Azure-sikkerhedsgruppe](/azure/active-directory/active-directory-licensing-group-assignment-azure-portal).