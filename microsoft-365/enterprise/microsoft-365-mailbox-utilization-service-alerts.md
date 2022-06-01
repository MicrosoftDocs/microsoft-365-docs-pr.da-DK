---
title: Tjenestebeskeder for postkasseudnyttelse
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: ''
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- admindeeplinkMAC
- admindeeplinkEXCHANGE
f1.keywords:
- NOCSH
description: Brug tjenestevarsler for postkasseudnyttelse til at overvåge postkasser i venteposition, der når kvoten for postkassen.
ms.openlocfilehash: 22583cbc6c6495d07caa3f920eeacb6bcd1d7536
ms.sourcegitcommit: aff1732dfa21e9283b173d8e5ca5bcbeeaaa26d8
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/01/2022
ms.locfileid: "65810544"
---
# <a name="service-advisories-for-mailbox-utilization-in-exchange-online-monitoring"></a>Tjenestemeddelelser om udnyttelse af postkasser i Exchange Online overvågning

Vi har udgivet en ny Exchange Online servicemeddelelser, der informerer dig om postkasser, der er i venteposition, og som risikerer at nå eller overskride deres kvote. Disse tjenestemeddelelser giver synlighed over antallet af postkasser i din organisation, der kan kræve administratorinput.

Disse tjenestemeddelelser vises i Microsoft 365 Administration. Hvis du vil have vist disse tjenestemeddelelser, skal <a href="https://go.microsoft.com/fwlink/p/?linkid=842900" target="_blank">**du**</a> >  gå til **Tilstand** >  Tjenestetilstand **Exchange Online** og derefter klikke på fanen **Aktive problemer**. Her er et eksempel på en meddelelse om udnyttelse af postkasser.

:::image type="content" alt-text="Tjenestebesked om postkasseudnyttelse." source="../media/MailboxUtilizationServiceAlert.png" lightbox="../media/MailboxUtilizationServiceAlert.png":::

Hvis du vil have vist en liste over postkasser, der nærmer sig deres lagerkvote (kaldet *rapporten over postkasseforbrug*), skal du klikke på det fremhævede link på følgende skærmbillede. Dette link vises i tjenestemeddelelsen.

:::image type="content" alt-text="Link til rapport over postkasseforbrug." source="../media/LinkToMailboxUsageReport.png" lightbox="../media/LinkToMailboxUsageReport.png":::

Alternativt kan den direkte URL-adresse til rapporten over postkassens brug være <https://admin.microsoft.com/Adminportal/Home?source=applauncher#/reportsUsage/MailboxUsage>.

## <a name="what-do-these-service-advisories-indicate"></a>Hvad indikerer disse servicemeddelelser?

Tjenestevarsler for udnyttelse af postkasser informerer administratorer om postkasser i venteposition, der nærmer sig kvoten for postkasselageret. Den type ventepositioner, der kan placeres i postkasser, omfatter litigation-ventepositioner, eDiscovery-ventepositioner og Microsoft 365 opbevaringspolitikker (der er konfigureret til at bevare data). Når en postkasse er i venteposition, kan brugere (eller automatiserede processer) ikke permanent fjerne data fra deres postkasse. Administratorer skal i stedet konfigurere MRM-opbevaringspolitikker i Exchange Online (indbygget i organisationens politikker for overholdelse af angivne standarder i forbindelse med dataopbevaring) for at flytte data fra en brugers primære postkasse til deres arkivpostkasse. Hvis en postkasse i venteposition ikke når en kritisk tilstand eller en advarselstilstand, skal administratorer [aktivere arkivpostkasser](../compliance/enable-archive-mailboxes.md) og [aktivere automatisk udvidelse af arkivering](../compliance/enable-autoexpanding-archiving.md) og derefter sikre, at opbevaringsperioden for den arkivpolitik, der er tildelt postkassen (der flytter mail fra den primære postkasse til arkivpostkassen), er kort nok. Hvis der ikke gøres noget for at løse de kvotaproblemer, der identificeres af meddelelsen om anvendelse af postkassen, kan brugerne muligvis ikke sende eller modtage mails eller mødeinviteringer.

En tjenestemeddelelse til udnyttelse af postkasser indeholder tabeller over antallet af postkasser, der nærmer sig deres kvote. I følgende afsnit beskrives oplysningerne i disse tabeller, og de handlinger, som administratorer kan udføre for at sikre, at disse postkasser ikke overskrider deres kvote.

> [!NOTE]
> Tjenestemeddelelser indeholder beskrivelser af kvotaegenskaberne for postkassen, der vises i kolonnerne i tabellerne, der er beskrevet i følgende afsnit.

### <a name="mailboxes-on-hold-without-an-archive"></a>Postkasser i venteposition uden et arkiv

I følgende tabel vises antallet af postkasser i venteposition, der nærmer sig deres kvote, men som ikke har en arkivpostkasse aktiveret. Hver kolonne i tabellen identificerer den specifikke kvote og antallet af postkasser i nærheden af denne kvote.

| # Postkasser ProhibitSendReceiveQuota (advarsel)| # Postkasser ProhibitSendReceiveQuota (kritisk)** |# Postkasser RecoverableItemsQuota (advarsel)|# Postkasser RecoverableItemsQuota (kritisk)** |
|:--------------|:--------------|:------------------|:--------------- |
| 2             | 2             | 1                 | 0               |
||||

Den handling, administratorer kan udføre for disse postkasser, er at aktivere arkivpostkassen og sikre, at der anvendes en MRM-arkivpolitik (som er en MRM-opbevaringspolitik i Exchange Online, der flytter elementer til arkivpostkassen) på postkassen, så elementerne flyttes til arkivpostkassen. Du kan få flere oplysninger under [Konfigurer en politik for arkiv og sletning for postkasser](../compliance/set-up-an-archive-and-deletion-policy-for-mailboxes.md).

Når du har aktiveret en arkivpostkasse, anbefaler vi, at du overvejer at øge kvoten for mappen Gendanbare elementer. Dette forhindrer, at kvoten for mappen Elementer, der kan gendannes, overskrides for postkasser, der er sat i venteposition. Du kan finde flere oplysninger under [Forøg kvoten for genoprettelige elementer for postkasser i venteposition](../compliance/increase-the-recoverable-quota-for-mailboxes-on-hold.md).

### <a name="mailboxes-on-hold-with-an-archive"></a>Postkasser i venteposition med et arkiv

I følgende tabel vises antallet af postkasser i venteposition, der nærmer sig deres kvote, og hvor en arkivpostkasse er aktiveret.

|# Postkasser ProhibitSendReceiveQuota (advarsel) |# Postkasser ForbydSendReceiveQuota (kritisk) |# Postkasser RecoverableItemsQuota (advarsel) |# Postkasser RecoverableItemsQuota (kritisk)** |
|:--------------|:--------------|:------------------|:--------------- |
| 1             | 1             | 6                 | 0               |
||||

Den handling, administratorer kan udføre for disse postkasser, er at øge kvoten for mappen Gendanbare elementer. Du kan finde flere oplysninger under [Forøg kvoten for genoprettelige elementer for postkasser i venteposition](../compliance/increase-the-recoverable-quota-for-mailboxes-on-hold.md).

Administratorer skal også sørge for, at en MRM-arkivpolitik, der flytter elementer til arkivpostkassen, også anvendes på postkasserne, og at opbevaringsperioden for arkivpolitikken er kort nok, så elementer ikke bevares for længe i den primære postkasse, før de flyttes til arkivet.

> [!NOTE]
> MRM-arkivpolitikker flytter også elementer fra mappen Gendanbare elementer i den primære postkasse til mappen Gendanbare elementer i den tilsvarende arkivpostkasse. Denne funktion hjælper med at forhindre, at postkassen overskrider kvoten for kvoten Gendanbare elementer.

### <a name="mrm-retention-policies-in-your-organization"></a>MRM-opbevaringspolitikker i din organisation

Tjenestevarsler til udnyttelse af postkasser kan også indeholde en tabel med oplysninger om MRM-opbevaringspolitikkerne i din organisation, og om de postkasser, der er en opbevaringspolitik, har en arkivpostkasse eller ej. Du kan få flere oplysninger om opbevaringspolitikker under [Opbevaringskoder og opbevaringspolitikker i Exchange Online](/exchange/security-and-compliance/messaging-records-management/retention-tags-and-policies).

| RetentionPolicyGuid | Postkassetype | HasMoveDumpsterToArchiveTag | HasMovePrimaryToArchiveTag | HasPersonalArchiveTag |  Postkasser |
|:--------------|:--------------|:---------------|:---------------|:---------------|:--------------- |
| 6c041498-1611-5011-a058-1156ce60890c | PrimaryWithArchive | Sandt | Falsk | Sandt | 398 |
| 6c041498-1611-5011-a058-1156ce60890c | Primære | Sandt | Falsk | Sandt | 10 |
| 749ceecc-d49d-4000-a9d5-594dbaea1e56 | PrimaryWithArchive | Falsk | Sandt | Falsk | 7 |
| 269f6a85-1234-4648-8cde-59bbc7bc67d0 | PrimaryWithArchive | Sandt | Sandt | Sandt | 1 |
| 13fb778d-e1cb-4c44-5768-ad4282906c1f | PrimaryWithArchive | Sandt | Sandt  | Falsk | 1 |
|||||||

På følgende liste beskrives hver kolonne i den forrige tabel.

- **RetentionPolicyGuid**: GUID'et for opbevaringspolitikken, der er tildelt postkasser i din organisation. I det forrige eksempel er der to separate rækker for den samme opbevaringspolitik. Den første række angiver antallet af postkasser med et arkiv, der er tildelt politikken. Den anden række angiver antallet af postkasser uden et arkiv, der er tildelt den samme politik.

   Hvis du vil have flere oplysninger om den opbevaringspolitik, der er angivet i denne kolonne, skal du køre følgende kommando i [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

   ```powershell
   Get-RetentionPolicy <GUID> | FL
   ```

   Værdien af egenskaben **Name** er navnet på den opbevaringspolitik, der vises på siden **Opbevaringspolitikker** i <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange Administration</a>.

- **MailboxType**: Angiver, hvilken type postkasser politikken er tildelt til. Værdier omfatter *Primary* (postkasser uden et arkiv) eller *PrimaryWithArchive* (postkasser med et arkiv). Hvis værdien i denne kolonne er *Primær*, skal du aktivere arkivet for postkasserne (kolonnen **Postkasse** angiver antallet af disse postkasser), der er tildelt politikken. Ellers fungerer en arkivpolitik eller kode for personligt arkiv ikke, fordi der ikke er et arkiv at flytte elementer til.

- **HasMoveDumpsterToArchiveTag**: Angiver, at opbevaringspolitikken indeholder en opbevaringskode, der flytter elementer i mappen Gendanbare elementer (også kaldet *dumpster*) i den primære postkasse til mappen Gendanbare elementer i arkivet. Denne type opbevaringskode angives af en administrator. Hvis opbevaringsperioden for koden for de elementer, der kan gendannes, er for lang, bør en reduktion af opbevaringsperioden forhindre, at postkasser nærmer sig kvoten for mappen Gendanbare elementer. Hvis opbevaringsperioden f.eks. er angivet til 30 dage, kan det hjælpe at reducere den til tre eller fem dage.  Du kan finde flere oplysninger under [Forøg kvoten for genoprettelige elementer for postkasser i venteposition](../compliance/increase-the-recoverable-quota-for-mailboxes-on-hold.md).

- **HasMovePrimaryToArchiveTag**: Angiver, om der er en standardopbevaringskode for "flyt til arkiv" (også kaldet en *arkivpolitik*), der er inkluderet i opbevaringspolitikken. I dette tilfælde flyttes meddelelser fra de almindelige mapper i den primære postkasse til arkivpostkassen. Denne type opbevaringskode angives af en administrator. Hvis opbevaringsperioden for dette mærke er for kort, kan brugerne have problemer med hele tiden at nå kvoten for deres primære postkasse. Hvis du reducerer opbevaringsperioden for en arkivpolitik, kan det hjælpe med at løse dette problem.

- **HasPersonalArchiveTag**: Angiver, om opbevaringspolitikken indeholder en personlig kode for "flyt til arkiv". Hvis opbevaringspolitikken indeholder en personlig kode for "flyt til arkiv", kan brugerne anvende dette mærke på mapper og meddelelser i deres postkasse for at flytte elementer til arkivet. Brugerne kan også konfigurere en indbakkeregel til at flytte meddelelser til en mappe, hvor denne kodede er anvendt på den. I begge tilfælde kan dette hjælpe med at flytte elementer til arkivet for at undgå at nå kvoten for deres primære postkasse.

- **Postkasser**: Angiver antallet af postkasser (dem med eller uden et arkiv, som er angivet i kolonnen **MailboxType** ), som opbevaringspolitikken er tildelt til.

## <a name="how-often-will-i-see-these-service-advisories"></a>Hvor ofte får jeg vist disse tjenestemeddelelser?

Hvis du ikke gør noget for at løse kvoteproblemerne, kan du forvente at se denne type servicemeddelelse hver syvende dag. Efterfølgende tjenestemeddelelser kan indeholde højere antal postkasser for andre postkasser, der nærmer sig deres kvote. Hvis du foretager en handling for at løse kvoteproblemer, sker denne tjenestemeddelelse kun, når der identificeres en anden postkasse med kvoteproblemer.

## <a name="more-information"></a>Flere oplysninger

- Du kan finde oplysninger om fejlfinding og løsning af problemer med arkivpostkasser [under Microsoft Purview fejlfinding](/office365/troubleshoot/microsoft-365-compliance-welcome).

- Hvis du vil have hjælp til at identificere de ventepositioner, der er placeret i en postkasse, skal [du se Sådan identificerer du den type venteposition, der er placeret i en postkasse](../compliance/identify-a-hold-on-an-exchange-online-mailbox.md).
