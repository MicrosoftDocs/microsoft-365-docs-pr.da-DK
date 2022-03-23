---
title: Send krypteret mail
f1.keywords:
- NOCSH
ms.author: sharik
author: skjerland
manager: scotv
ms.date: 9/20/2018
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Adm_O365
- M365-subscription-management
- M365-Campaigns
- m365solution-smb
ms.custom:
- Adm_O365
- Core_O365Admin_Migration
- MiniMaven
- MSB365
- admindeeplinkEXCHANGE
search.appverid:
- BCS160
- MET150
ms.assetid: 496e690b-b75d-4ff5-bf34-cc32905d0364
description: Få mere at vide om, hvordan du sender krypterede mails ved hjælp Outlook.
ms.openlocfilehash: 15f5b87fb238d4a872f13c11f1e88892f628a255
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/12/2022
ms.locfileid: "63594744"
---
# <a name="encrypt-or-label-your-sensitive-email"></a>Kryptér eller mærkater dine følsomme mails

Dine data og kampagneoplysninger er vigtige og ofte fortrolige. Beskyt disse følsomme oplysninger ved hjælp af kryptering og følsomhedsmærkater, så du og dine mailmodtagere behandler oplysningerne med den følsomhed, det kræver.

## <a name="best-practices"></a>Anbefalede fremgangsmåder

Før du sender mails med fortrolige eller følsomme oplysninger, bør du overveje at slå:

- **Kryptering:** Du kan kryptere dine mails for at beskytte oplysningerne i mailen. Når du krypterer en mail, konverteres den fra almindelig læsbar tekst til ulæselig cyphertekst. Kun den modtager, der har den private nøgle, der svarer til den offentlige nøgle, der bruges til at kryptere meddelelsen, kan dekryptere meddelelsen til læsning. Alle modtagere uden den tilsvarende private nøgle kan dog se uoverensstemmende tekst. Din administrator kan definere regler for automatisk at kryptere meddelelser, der opfylder bestemte kriterier. Din administrator kan f.eks. oprette en regel, der krypterer alle meddelelser, der sendes uden for organisationen, eller alle meddelelser, der nævner bestemte ord eller udtryk. Krypteringsregler anvendes automatisk.
- **Følsomhedsmærkater:** Din kampagne kan også konfigurere følsomhedsmærkater, som du kan anvende på dine filer og mails, så de overholder din kampagnes politikker for beskyttelse af oplysninger. Når du angiver en etiket, bevares navnet sammen med din mail, også selvom den sendes – f.eks. ved at blive vist som brevhoved i meddelelsen.

![Diagram over en mail med uddelingskopier til etiketter og kryptering.](../media/m365-campaign-email-encrypt.png)

## <a name="set-it-up"></a>Konfigurer det

Hvis du vil kryptere en meddelelse, der ikke opfylder en foruddefineret regel, eller din administrator ikke har konfigureret nogen regler, kan du anvende en række forskellige krypteringsregler, før du sender meddelelsen. Hvis du vil sende en krypteret meddelelse fra Outlook 2013 eller 2016 eller Outlook 2016 til Mac, skal du vælge Indstillinger **>** Tilladelser og derefter vælge den ønskede beskyttelsesindstilling. Du kan også sende en krypteret meddelelse ved at vælge **knappen** Beskyt i Outlook på internettet. Du kan finde flere oplysninger [i Sende, få vist og svare på krypterede meddelelser i Outlook til pc](https://support.microsoft.com/en-us/office/send-view-and-reply-to-encrypted-messages-in-outlook-for-pc-eaa43495-9bbb-4fca-922a-df90dee51980).

## <a name="admin-settings"></a>Administratorindstillinger

Du kan få alt at vide om konfiguration af mailkryptering [ved mailkryptering Microsoft 365](../compliance/email-encryption.md).

### <a name="automatically-encrypt-email-messages"></a>Krypter mails automatisk

Administratorer kan oprette regler for mailflow for automatisk at beskytte mails, der sendes og modtages fra din kampagne. Konfigurer regler for at kryptere eventuelle udgående mails, og fjern krypteringen fra krypterede meddelelser, der kommer fra din organisation eller fra svar på krypterede meddelelser, der sendes fra organisationen.

Du opretter regler for mailflow for at kryptere mails med de nye Office 365-meddelelseskryptering (OME)-funktioner. Definer regler for mailflow for at udløse meddelelseskryptering med de nye OME-funktioner <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">ved hjælp Exchange Administration (EAC)</a>. 

1. Log på i en webbrowser ved hjælp af en arbejds- eller skolekonto, der har fået globale administratorrettigheder.
2. Vælg feltet Administrator.
3. I Administration skal du vælge **> Exchange**.

Du kan finde flere oplysninger i [Definere regler for mailflow for at kryptere mails](../compliance/define-mail-flow-rules-to-encrypt-email.md).

### <a name="brand-your-encryption-messages"></a>Brande dine krypteringsmeddelelser

Du kan også anvende din kampagnebranding til at tilpasse udseendet og teksten i mails. Få mere at vide [under Føj organisationens brand til dine krypterede meddelelser](../compliance/email-encryption.md).