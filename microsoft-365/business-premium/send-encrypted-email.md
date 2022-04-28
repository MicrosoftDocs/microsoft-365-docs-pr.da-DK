---
title: Send krypteret mail
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
ms.date: 03/08/2022
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: high
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
description: Få mere at vide om, hvordan du sender krypteret mail ved hjælp af Outlook.
ms.openlocfilehash: 02dc3b7720f6aa46ffaf3cf4a04511c725798a24
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65095160"
---
# <a name="encrypt-or-label-sensitive-email"></a>Kryptér eller mærkatfølsom mail

Dine data og oplysninger er vigtige og ofte fortrolige. Målet her er at hjælpe med at beskytte disse følsomme oplysninger ved at sikre, at alle bruger følsomhedsmærkater, så mailmodtagere behandler oplysningerne med den største følsomhed.

## <a name="best-practices"></a>Anbefalede fremgangsmåder

Før enkeltpersoner sender mails med fortrolige eller følsomme oplysninger, bør de overveje at aktivere:

- **Kryptering:** Du kan kryptere din mail for at beskytte beskyttelsen af personlige oplysninger i mailen. Når du krypterer en mail, konverteres den fra læsbar almindelig tekst til krypteret cyphertekst. Det er kun den modtager, der har den private nøgle, som svarer til den offentlige nøgle, der bruges til at kryptere meddelelsen, der kan dechifrere meddelelsen til læsning. Alle modtagere uden den tilsvarende private nøgle kan dog se tekst, der ikke kan læses. Din administrator kan definere regler for automatisk kryptering af meddelelser, der opfylder bestemte kriterier. Din administrator kan f.eks. oprette en regel, der krypterer alle meddelelser, der sendes uden for din organisation, eller alle meddelelser, der nævner bestemte ord eller udtryk. Alle krypteringsregler anvendes automatisk.

- **Følsomhedsmærkater:** Hvis din organisation kræver det, kan du konfigurere følsomhedsmærkater, som du anvender på dine filer og mails, for at holde dem kompatible med organisationens politikker for beskyttelse af oplysninger. Når du angiver en etiket, bevares etiketten sammen med din mail, også selvom den f.eks. sendes &mdash; , ved at blive vist som en overskrift i meddelelsen.

![Diagram over en mail med billedforklatter til mærkater og kryptering.](../media/m365-campaign-email-encrypt.png)

## <a name="set-it-up"></a>Konfigurer det

Hvis du vil kryptere en meddelelse, der ikke opfylder en foruddefineret regel, eller hvis din administrator ikke har konfigureret nogen regler, kan du anvende en række forskellige krypteringsregler, før du sender meddelelsen. Hvis du vil sende en krypteret meddelelse fra Outlook 2013 eller 2016 eller Outlook 2016 til Mac, skal du vælge **Indstillinger > tilladelser** og derefter vælge den beskyttelse, du har brug for. Du kan også sende en krypteret meddelelse ved at vælge knappen **Beskyt** i Outlook på internettet. Du kan få flere oplysninger under [Send, få vist og besvar krypterede meddelelser i Outlook til pc](https://support.microsoft.com/en-us/office/send-view-and-reply-to-encrypted-messages-in-outlook-for-pc-eaa43495-9bbb-4fca-922a-df90dee51980).

## <a name="admin-settings"></a>Administratorindstillinger

Du kan få mere at vide om konfiguration af mailkryptering på [Mailkryptering i Microsoft 365](../compliance/email-encryption.md).

### <a name="automatically-encrypt-email-messages"></a>Kryptér automatisk mails

Administratorer kan oprette regler for mailflow for automatisk at beskytte mails, der sendes og modtages fra en kampagne eller virksomhed. Konfigurer regler for at kryptere eventuelle udgående mails, og fjern kryptering fra krypterede meddelelser, der kommer fra din organisation, eller fra svar på krypterede meddelelser, der er sendt fra din organisation.

Du opretter regler for mailflow for at kryptere mails med Microsoft Purview Message Encryption. Definer regler for mailflow for udløsning af meddelelseskryptering ved hjælp af <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange Administration (EAC).</a>

1. Log på ved hjælp af en arbejds- eller skolekonto, der er tildelt globale administratortilladelser, i en webbrowser.
2. Vælg feltet Administrator.
3. Vælg **Administrationscentre > Exchange** i Administration.

Du kan finde flere oplysninger under [Definer regler for mailflow for at kryptere mails](../compliance/define-mail-flow-rules-to-encrypt-email.md).

### <a name="brand-your-encryption-messages"></a>Brand dine krypteringsmeddelelser

Du kan også anvende branding til at tilpasse udseendet og teksten i mailmeddelelserne. Du kan få flere oplysninger under [Føj organisationens brand til dine krypterede meddelelser](../compliance/email-encryption.md).

Hvis du har fået så langt, har du gennemført en anden mission, så tillykke! Der er ikke tid til at hvile på vores succeser, så lad os komme i gang med at konfigurere et sikkert miljø, hvor teamet kan [samarbejde sikkert](m365bp-collaborate-share-securely.md). 

