---
title: Synkroniser domænebrugere Microsoft 365
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_TOC
ms.custom:
- Adm_O365
- Core_O365Admin_Migration
- MiniMaven
- MSB365
- OKR_SMB_M365
- seo-marvel-mar
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
description: Synkroniser domænekontrollerede brugere med Microsoft 365 til virksomheder.
ms.openlocfilehash: 6a00b76113a750f306ef6545f1b38fcf9f9b2202
ms.sourcegitcommit: adea59259a5900cad5de29ddf46d1ca9e9e1c82f
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/04/2022
ms.locfileid: "64634531"
---
# <a name="synchronize-domain-users-to-microsoft-365"></a>Synkroniser domænebrugere Microsoft 365

## <a name="1-prepare-for-directory-synchronization"></a>1. Forbered katalogsynkronisering 

Før du synkroniserer dine brugere og computere fra det lokale Active Directory-domæne, skal du [gennemgå Forbered katalogsynkronisering på Microsoft 365](../../enterprise/prepare-for-directory-synchronization.md). Det gælder især:

   - Sørg for, at der ikke findes nogen dubletter i dit katalog til følgende attributter: **mail**, **proxyAddresses** og **userPrincipalName**. Disse værdier skal være entydige, og dubletter skal fjernes.
   
   - Vi anbefaler, at du konfigurerer **userPrincipalName-attributten** (UPN) for hver lokal brugerkonto, så den svarer til den primære mailadresse, der svarer til den licenserede Microsoft 365 bruger. Eksempel: *mary.shelley@contoso.com* i stedet *for mary@contoso.local*
   
   - Hvis Active Directory-domænet slutter med et suffiks, der ikke kan rous, f.eks. *.local* eller *.lan*, skal du i stedet for et suffiks, som f.eks. kan køres via internettet, f.eks. *.com* eller *.org*, justere UPN-suffikset [for](../../enterprise/prepare-a-non-routable-domain-for-directory-synchronization.md) de lokale brugerkonti først som beskrevet i Forberede et domæne, der ikke kan rous, til katalogsynkronisering. 

Kør **IdFix i** trin fire (4) nedenfor, vil også sikre, at din Active Directory i det lokale miljø er klar til katalogsynkronisering.

## <a name="2-install-and-configure-azure-ad-connect"></a>2. Installer og konfigurer Azure AD-Forbind

Hvis du vil synkronisere brugere, grupper og kontakter fra det lokale Active Directory Azure Active Directory, skal Azure Active Directory Forbind installere og konfigurere katalogsynkronisering. 

 1. I Administration [skal du](https://go.microsoft.com/fwlink/p/?linkid=2024339) vælge **Konfiguration i** venstre navigationslinje.

 2. Under **Logon og sikkerhed skal du vælge** Tilføj **eller synkroniser brugere til din Microsoft-konto**.

 3. På siden **Tilføj eller synkroniser brugere til din Microsoft-konto** skal du vælge **Introduktion**.

 4. I det første trin skal du køre IdFix-værktøjet til klargøring til katalogsynkronisering.

 5. Følg trinnene i guiden for at downloade Azure AD Forbind og brug den til at synkronisere dine domænekontrollerede brugere Microsoft 365.


Se [Konfigurer katalogsynkronisering for Microsoft 365 for](../../enterprise/set-up-directory-synchronization.md) at få mere at vide.

Når du konfigurerer indstillingerne for Azure AD Forbind, anbefaler vi, at du aktiverer synkronisering af **adgangskoder, nem** enkelt logon og funktionen til tilbageførsel af  adgangskode, som også understøttes i Microsoft 365 til virksomheder. 

> [!NOTE]
> Der er nogle yderligere trin til tilbageførsel af adgangskode ud over afkrydsningsfeltet i Azure AD Forbind. Du kan finde flere oplysninger [under Sådan konfigureres tilbageførsel af adgangskode](/azure/active-directory/authentication/howto-sspr-writeback). 

Hvis du også vil administrere domænebaserede Windows 10-enheder, skal du se Aktivér domæne sammenføjede [Windows 10-enheder](../../business-premium/m365bp-manage-windows-devices.md), så de administreres af Microsoft 365 Business Premium til at konfigurere en Azure AD-hybridforbindelse.
