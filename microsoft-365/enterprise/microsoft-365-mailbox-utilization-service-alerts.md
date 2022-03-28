---
title: Beskeder om postkasseudnyttelse
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
description: Brug beskeder om postkasseudnyttelse til at overvåge postkasser i venteposition, der når deres postkassekvote.
ms.openlocfilehash: 311be4159d45b19ce1123baa840eebdf844840ec
ms.sourcegitcommit: b1066b2a798568afdea9c09401d52fa38fe93546
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/13/2021
ms.locfileid: "63596879"
---
# <a name="service-alerts-for-mailbox-utilization-in-exchange-online-monitoring"></a>Tjenestebeskeder om anvendelsen af postkasse i Exchange Online overvågning

Vi har udgivet en ny Exchange Online, der informerer dig om postkasser, der er i venteposition, og som risikerer at nå eller overskride deres kvote. Disse tjenesteadvarsler giver overblik over antallet af postkasser i organisationen, der kan kræve handling fra administratorer.

Disse serviceadvarsler vises i Microsoft 365 Administration. For at få vist disse serviceadvarsler skal du **gå til HealthService** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=842900" target="_blank">**health**</a> >  **Exchange Online** og derefter klikke på **fanen Aktive** problemer. Her er et eksempel på en besked om anvendelsen af en postkassetjeneste.

:::image type="content" alt-text="Besked om brug af postkassetjeneste." source="../media/MailboxUtilizationServiceAlert.png" lightbox="../media/MailboxUtilizationServiceAlert.png":::

For at få vist en liste over postkasser, der nærmer sig deres lagerkvote (kaldet postkassebrugsrapport *), skal* du klikke på det fremhævede link på følgende skærmbillede. Dette link vises i tjenestebeskeden.

:::image type="content" alt-text="Link til rapport over postkassebrug." source="../media/LinkToMailboxUsageReport.png" lightbox="../media/LinkToMailboxUsageReport.png":::

Alternativt er den direkte URL-adresse til rapporten om postkassebrug <https://admin.microsoft.com/Adminportal/Home?source=applauncher#/reportsUsage/MailboxUsage>.

## <a name="what-do-these-service-alerts-indicate"></a>Hvad angiver disse serviceadvarsler?

Tjenesten advarer om anvendelsen af postkasser og informerer administratorer om postkasser i venteposition, der nærmer sig lagerkvoten for postkassen. Den type venteposition, der kan placeres i postkasser, omfatter retslig tilbageholdelse, eDiscovery-venteposition og Microsoft 365 opbevaringspolitikker (der er konfigureret til at bevare data). Når en postkasse er i venteposition, kan brugere (eller automatiserede processer) ikke fjerne data fra deres postkasse permanent. I stedet skal administratorer konfigurere MRM-opbevaringspolitikker i Exchange Online (i overensstemmelse med organisationens politikker for overholdelse af regler og standarder relateret til dataopbevaring) for at flytte data fra en brugers primære postkasse til arkivpostkassen. Hvis ikke, og en postkasse i en venteposition når en kritisk tilstand eller en advarselstilstand, [](../compliance/enable-archive-mailboxes.md) skal administratorer aktivere arkivpostkasser og aktivere automatisk udvidende [arkivering](../compliance/enable-autoexpanding-archiving.md) og derefter sørge for, at opbevaringsperioden for den arkivpolitik, der er tildelt postkassen (der flytter mails fra den primære postkasse til arkivpostkassen) er kort nok. Hvis der ikke gøres noget for at løse de kvoteproblemer, der identificeres af beskederne om anvendelsen af postkassetjenesten, kan brugerne muligvis ikke sende eller modtage mails eller mødeindkaldelser.

En tjenestebesked om anvendelsen af postkasse indeholder tabeller om antallet af postkasser, der nærmer sig deres kvote. I de følgende afsnit beskrives oplysningerne i disse tabeller, og de handlinger administratorer kan benytte for at sikre, at postkasserne ikke overskrider deres kvote.

> [!NOTE]
> Tjenestebeskeder indeholder beskrivelser af egenskaberne for postkassekvoter, der vises i kolonnerne i de tabeller, der er beskrevet i de følgende afsnit.

### <a name="mailboxes-on-hold-without-an-archive"></a>Postkasser i venteposition uden et arkiv

I følgende tabel vises antallet af postkasser i venteposition, der nærmer sig deres kvote, men ikke har aktiveret en arkivpostkasse. Hver kolonne i tabellen identificerer den specifikke kvote og antallet af postkasser, der nærmer sig den pågældende kvote.

| # Mailboxes ProhibitSendReceiveQuota (Warning)| # Mailboxes ProhibitSendReceiveQuota (Critical)** |# Mailboxes RecoverableItemsQuota (Advarsel)|# Mailboxes RecoverableItemsQuota (Critical)** |
|:--------------|:--------------|:------------------|:--------------- |
| 2             | 2             | 1                 | 0               |
||||

Handlingen, som administratorer kan gøre for disse postkasser, er at aktivere arkivpostkassen og sikre, at en MRM-arkiveringspolitik (som er en MRM opbevaringspolitik i Exchange Online, der flytter elementer til arkivpostkassen) anvendes på postkassen, så elementer flyttes til arkivpostkassen. Få mere at vide under [Konfigurer en arkiverings- og sletningspolitik for postkasser](../compliance/set-up-an-archive-and-deletion-policy-for-mailboxes.md).

Når du har aktiveret en arkivpostkasse, anbefaler vi, at du overvejer at øge kvoten for mappen Genoprettelige elementer. Dette er med til at forhindre, at kvoten for mappen Genoprettelige elementer for postkasser, der er sat i venteposition, overskrides. Få mere at vide under [Øg kvoten for genoprettelige elementer for postkasser i venteposition](../compliance/increase-the-recoverable-quota-for-mailboxes-on-hold.md).

### <a name="mailboxes-on-hold-with-an-archive"></a>Postkasser i venteposition med et arkiv

I følgende tabel vises antallet af postkasser i venteposition, der nærmer sig deres kvote, og som har en arkivpostkasse aktiveret.

|# Mailboxes ProhibitSendReceiveQuota (Warning) |# Mailboxes ProhibitSendReceiveQuota (kritisk) |# Mailboxes RecoverableItemsQuota (Advarsel) |# Mailboxes RecoverableItemsQuota (Critical)** |
|:--------------|:--------------|:------------------|:--------------- |
| 1             | 1             | 6                 | 0               |
||||

Det, som administratorer kan gøre for disse postkasser, er at øge kvoten for mappen Genoprettelige elementer. Få mere at vide under [Øg kvoten for genoprettelige elementer for postkasser i venteposition](../compliance/increase-the-recoverable-quota-for-mailboxes-on-hold.md).

Administratorer skal også sørge for, at en MRM-arkiveringspolitik, der flytter elementer til arkivpostkassen, også anvendes på postkasserne, og at opbevaringsperioden for arkiveringspolitikken er kort nok, så elementer ikke bevares for længe i den primære postkasse, før de flyttes til arkivet.

> [!NOTE]
> MRM-arkiveringspolitikker flytter også elementer fra mappen Genoprettelige elementer i den primære postkasse til mappen Genoprettelige elementer i den tilsvarende arkivpostkasse. Denne funktion hjælper med at forhindre, at postkassen overskrider kvoten for kvoten for genoprettelige elementer.

### <a name="mrm-retention-policies-in-your-organization"></a>MRM-opbevaringspolitikker i organisationen

Service alerts for mailbox utilization may also contain a table with information about the MRM retention policies in your organization and whether the mailboxes that are a retention policy have an archive mailbox. Hvis du vil have mere at vide om opbevaringspolitikker, [skal du se Opbevaringsmærker og opbevaringspolitikker Exchange Online](/exchange/security-and-compliance/messaging-records-management/retention-tags-and-policies).

| RetentionPolicyGuid | MailboxType | HasMoveDumpsterToArchiveTag | HasMovePrimaryToArchiveTag | HasPersonalArchiveTag |  Postkasser |
|:--------------|:--------------|:---------------|:---------------|:---------------|:--------------- |
| 6c041498-1611-5011-a058-1156ce60890c | PrimaryWithArchive | Sand | Falsk | Sand | 398 |
| 6c041498-1611-5011-a058-1156ce60890c | Primær | Sand | Falsk | Sand | 10 |
| 749ceecc-d49d-4000-a9d5-594dbaea1e56 | PrimaryWithArchive | Falsk | Sand | Falsk | 7 |
| 269f6a85-1234-4648-8cde-59bbc7bc67d0 | PrimaryWithArchive | Sand | Sand | Sand | 1 |
| 13fb778d-e1cb-4c44-5768-ad4282906c1f | PrimaryWithArchive | Sand | Sand  | Falsk | 1 |
|||||||

Følgende liste beskriver hver kolonne i den forrige tabel.

- **RetentionPolicyGuid**: GUID for den opbevaringspolitik, der er tildelt postkasser i organisationen. I det forrige eksempel er der to separate rækker for den samme opbevaringspolitik. Den første række angiver antallet af postkasser med et arkiv, der er tildelt politikken. Den anden række angiver antallet af postkasser uden et arkiv, der er tildelt samme politik.

   For at få flere oplysninger om opbevaringspolitikken, der er angivet i denne kolonne, skal du køre følgende [kommando i Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

   ```powershell
   Get-RetentionPolicy <GUID> | FL
   ```

   Værdien af egenskaben **Navn** er navnet på den opbevaringspolitik, der vises på siden Opbevaringspolitikker <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">i Exchange Administration</a>.

- **MailboxType**: Angiver, hvilken type postkasser politikken er tildelt til. Værdier *omfatter Primær (* postkasser uden et arkiv) eller *PrimaryWithArchive* (postkasser med et arkiv). Hvis værdien i denne kolonne er *Primær, skal* du aktivere arkivet for postkasserne (kolonnen Postkasse angiver antallet  af disse postkasser), der er tildelt politikken. Ellers vil en arkiveringspolitik eller et personligt arkivmærke ikke fungere, fordi der ikke er et arkiv at flytte elementer til.

- **HasMoveDumpsterToArchiveTag**: Angiver, at opbevaringspolitikken indeholder et opbevaringsmærke, der flytter elementer i mappen Genoprettelige elementer (også kaldet *dumpster*) i den primære postkasse til mappen Genoprettelige elementer i arkivet. Denne type opbevaringsmærke er angivet af en administrator. Hvis opbevaringsperioden for mærket med genoprettelige elementer er for lang, bør en reduktion af opbevaringsperioden være med til at forhindre, at postkasser nærmer sig kvoten for mappen genoprettelige elementer. Hvis f.eks. opbevaringsperioden er indstillet til 30 dage, kan det være en hjælp at reducere den til tre eller fem dage.  Få mere at vide under [Øg kvoten for genoprettelige elementer for postkasser i venteposition](../compliance/increase-the-recoverable-quota-for-mailboxes-on-hold.md).

- **HasMovePrimaryToArchiveTag**: Angiver, om opbevaringspolitikken som standard indeholder opbevaringsmærket "Flyt til arkiv". I dette tilfælde flyttes meddelelser fra de almindelige mapper i den primære postkasse til arkivpostkassen. Denne type opbevaringsmærke er angivet af en administrator. Hvis opbevaringsperioden for dette mærke er for kort, kan brugere have problemer med kontinuerligt at nå kvoten for deres primære postkasse. Du kan muligvis løse dette problem ved at reducere opbevaringsperioden for en arkiveringspolitik.

- **HasPersonalArchiveTag**: Angiver, om opbevaringspolitikken indeholder et personligt mærke "Flyt til arkiv". Hvis opbevaringspolitikken indeholder et personligt mærke af mærket "Flyt til arkiv", kan brugerne anvende dette mærke på mapper og meddelelser i deres postkasse for at flytte elementer til arkivet. Brugere kan også konfigurere en indbakkeregel til at flytte meddelelser til en mappe med denne kodet anvendt på den. I begge tilfælde kan dette hjælpe med at flytte elementer til arkivet for at undgå at nå kvoten for deres primære postkasse.

- **Postkasser**: Angiver antallet af postkasser (dem med eller uden et arkiv, som er angivet i kolonnen **MailboxType** ), som opbevaringspolitikken tildeles til.

## <a name="how-often-will-i-see-these-service-alerts"></a>Hvor ofte får jeg vist disse servicebeskeder?

Hvis du ikke løser kvoteproblemerne, kan du forvente at få vist denne type tjenestebesked hver fjerde dag. Efterfølgende serviceadvarsler kan indeholde højere postkasseantal for andre postkasser, der nærmer sig deres kvote. Hvis du løser kvoteproblemerne, vises denne tjenestebesked kun, når der identificeres en anden postkasse med kvoteproblemer.

## <a name="more-information"></a>Flere oplysninger

- Du kan finde oplysninger om fejlfinding og løsning af problemer med arkivpostkassen [i Microsoft 365 fejlfinding i forbindelse med overholdelse af regler og standarder](/office365/troubleshoot/microsoft-365-compliance-welcome).

- Du kan finde en vejledning til at identificere de ventepositioner, der er sat i en postkasse, under Sådan identificerer du [typen af venteposition i en postkasse](../compliance/identify-a-hold-on-an-exchange-online-mailbox.md).
