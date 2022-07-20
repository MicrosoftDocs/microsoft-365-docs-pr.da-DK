---
title: Send krypteret mail
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: high
ms.date: 07/19/2022
ms.collection:
- M365-Campaigns
- m365solution-smb
ms.custom:
- MiniMaven
search.appverid:
- BCS160
- MET150
description: Få mere at vide om, hvordan du sender krypteret mail ved hjælp af Outlook.
ms.openlocfilehash: 5e0698db0a17e24df358fc873b0a419b13c17dad
ms.sourcegitcommit: c1eaea74c8ffce2f9f477c9469342e88e4a70c14
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/20/2022
ms.locfileid: "66893117"
---
# <a name="encrypt-or-label-your-sensitive-email-in-microsoft-365"></a>Kryptér eller mærkér din følsomme mail i Microsoft 365

Dine data og oplysninger er vigtige og ofte fortrolige. Målet her er at hjælpe med at beskytte disse følsomme oplysninger ved at sikre, at alle bruger følsomhedsmærkater, så mailmodtagere behandler oplysningerne med den største følsomhed.

## <a name="best-practices"></a>Anbefalede fremgangsmåder

Før enkeltpersoner sender mails med fortrolige eller følsomme oplysninger, bør de overveje at aktivere:

- **Kryptering:** Du kan kryptere din mail for at beskytte beskyttelsen af personlige oplysninger i mailen. Når du krypterer en mail, konverteres den fra læsbar almindelig tekst til krypteret cyphertekst. Det er kun den modtager, der har den private nøgle, som svarer til den offentlige nøgle, der bruges til at kryptere meddelelsen, der kan dechifrere meddelelsen til læsning. Alle modtagere uden den tilsvarende private nøgle kan dog se tekst, der ikke kan læses. Din administrator kan definere regler for automatisk kryptering af meddelelser, der opfylder bestemte kriterier. Din administrator kan f.eks. oprette en regel, der krypterer alle meddelelser, der sendes uden for din organisation, eller alle meddelelser, der nævner bestemte ord eller udtryk. Alle krypteringsregler anvendes automatisk.

- **Følsomhedsmærkater:** Hvis din organisation kræver det, kan du konfigurere følsomhedsmærkater, som du anvender på dine filer og mails, for at holde dem kompatible med organisationens politikker for beskyttelse af oplysninger. Når du angiver en etiket, bevares etiketten sammen med din mail, også selvom den f.eks. sendes &mdash; , ved at blive vist som en overskrift i meddelelsen.

![Diagram over en mail med billedforklatter til mærkater og kryptering.](../media/m365-campaign-email-encrypt.png)

## <a name="set-it-up"></a>Konfigurer det

Hvis du vil kryptere en meddelelse, der ikke opfylder en foruddefineret regel, eller hvis din administrator ikke har konfigureret nogen regler, kan du anvende en række forskellige krypteringsregler, før du sender meddelelsen. Hvis du vil sende en krypteret meddelelse fra Outlook 2013 eller 2016 eller Outlook 2016 til Mac, skal du vælge **Indstillinger > Tilladelser** og derefter vælge den beskyttelse, du har brug for. Du kan også sende en krypteret meddelelse ved at vælge knappen **Beskyt** i Outlook på internettet. Du kan få flere oplysninger under [Send, få vist og besvar krypterede meddelelser i Outlook til pc](https://support.microsoft.com/en-us/office/send-view-and-reply-to-encrypted-messages-in-outlook-for-pc-eaa43495-9bbb-4fca-922a-df90dee51980).

## <a name="admin-settings"></a>indstillinger for Administration

Du kan få mere at vide om konfiguration af mailkryptering ved [mailkryptering i Microsoft 365](../compliance/email-encryption.md).

### <a name="automatically-encrypt-email-messages"></a>Kryptér automatisk mails

Administratorer kan oprette regler for mailflow for automatisk at beskytte mails, der sendes og modtages fra en kampagne eller virksomhed. Konfigurer regler for at kryptere eventuelle udgående mails, og fjern kryptering fra krypterede meddelelser, der kommer fra din organisation, eller fra svar på krypterede meddelelser, der er sendt fra din organisation.

Du opretter regler for mailflow for at kryptere mails med Microsoft Purview-meddelelseskryptering. Definer regler for mailflow for udløsning af meddelelseskryptering ved hjælp af <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange Administration (EAC).</a>

1. Log på ved hjælp af en arbejds- eller skolekonto, der er tildelt globale administratortilladelser, i en webbrowser.
2. Vælg feltet Administration.
3. Vælg **Administration centre > Exchange** i Administration centrum.

Du kan finde flere oplysninger under [Definer regler for mailflow for at kryptere mails](../compliance/define-mail-flow-rules-to-encrypt-email.md).

### <a name="brand-your-encryption-messages"></a>Brand dine krypteringsmeddelelser

Du kan også anvende branding til at tilpasse udseendet og teksten i mailmeddelelserne. Du kan få flere oplysninger under [Føj organisationens brand til dine krypterede meddelelser](../compliance/email-encryption.md).

## <a name="next-mission"></a>Næste mission

Hvis du har fået så langt, har du gennemført en anden mission, så tillykke! Der er ikke tid til at hvile på vores succeser, så lad os komme i gang med at konfigurere et sikkert miljø, hvor teamet kan [samarbejde sikkert](m365bp-collaborate-share-securely.md).