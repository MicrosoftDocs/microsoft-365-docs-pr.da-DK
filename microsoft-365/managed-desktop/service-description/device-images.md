---
title: Enhedsbilleder
description: Billedkrav ved bestilling af nye enheder eller genbrug af eksisterende enheder
keywords: Microsoft Managed Desktop, Microsoft 365, tjeneste, dokumentation
ms.service: m365-md
author: tiaraquan
f1.keywords:
- NOCSH
ms.author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
manager: dougeby
ms.topic: article
audience: Admin
ms.openlocfilehash: 294531305321901dfa704462471d1573b9cb4b88
ms.sourcegitcommit: adea59259a5900cad5de29ddf46d1ca9e9e1c82f
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/04/2022
ms.locfileid: "64635103"
---
# <a name="device-images"></a>Enhedsbilleder

Uanset om du [bestiller nye](#new-devices) enheder eller [genbruger](#existing-devices) eksisterende, har du flere muligheder for at sikre, at billedet på enheden opfylder vores [enhedskrav](device-requirements.md#check-hardware-requirements).

## <a name="new-devices"></a>Nye enheder

Når du bestiller en ny enhed fra en godkendt [producent, skal](device-requirements.md#minimum-requirements) du følge disse trin for at sikre, at de sender enheder med den rette Microsoft Managed Desktop og softwarekonfiguration.

Hver gang du planlægger at tilmelde en bestemt enhedsmodel i tjenesten for første gang, skal du teste et eksempel for at sikre, at den leverer den brugeroplevelse, du forventer. Du kan finde flere oplysninger under [Valider nye enheder](/microsoft-365/managed-desktop/get-started/validate-device).

### <a name="windows-10-pro"></a>Windows 10 Pro
Hvis du bestiller enheder med din Windows 10, skal du arbejde direkte sammen med din OEM-sælger. Pr. 1. november 2022 kan OEMs kun sælge Windows 10 Pro under Windows 11 Pro med Windows 10 Pro nedgraderingslicens. Du kan finde flere oplysninger [Windows 10 supportdatoer](/lifecycle/products/windows-10-enterprise-and-education?msclkid=4a74c7b9b04111eca478c6fdafbc51a5) for tilbagetrækningsdatoerne for Windows 10 versioner.

Kunder, der er interesseret i at Windows 11, kan du finde flere oplysninger om den anbefalede proces [her](/microsoft-365/managed-desktop/intro/win11-overview). 

### <a name="dell"></a>Dell

Arbejd direkte sammen med Dell-sælger.

Repræsentanten vil sikre, at det billede, der er Microsoft Managed Desktop, anvendes på enheder i din rækkefølge. Hvis du vil have mere at vide om Dell-enheder, billedet og bestillingsprocessen, skal du kontakte MMD_at_dell@dell.com.

### <a name="hp"></a>HP

Når du bestiller nye enheder fra HP, skal du sørge for at bruge den specifikke SKU, der er angivet i afsnittet Yderligere krav for hver model, der findes på siden Køb [Windows Pro-forretningsenheder](https://www.microsoft.com/windows/business/devices#view-all-filter). Filtrer visningen for at få vist Microsoft Managed Desktop enheder.

Hvis du bestiller en enhed fra HP, der er godkendt som en [undtagelse, men](customizing.md) ikke aktuelt er angivet på siden Enhedsliste, skal du anmode om, at SKU'en bruges til modellen. Vi arbejder sammen med HP for at give dig disse oplysninger ved hjælp af din anmodning om undtagelser. Du kan også kontakte HP direkte for spørgsmål om enheder og instruktioner til bestilling af enheder ved hjælp af disse adresser:

- Usa: mmd-americas@hp.com
- Europa/Mellemøsten/Afrika: mmd-emea@hp.com
- Asien/Japan: mmd-apj@hp.com
- Global: mmd@hp.com

### <a name="lenovo"></a>Lenovo

Når du bestiller enheder fra Lenovo, skal du angive et bestemt delnummer i ordren. Kontakt din Lenovo-sælger eller Lenovo Channel-partner, og bed dem om at oprette en "*særlig tilbudsmodel*" med et system, der opfylder vores [enhedskrav](device-requirements.md#minimum-requirements).

Hvis du vil medtage et forudinstalleret billede, der er kompatibelt med Microsoft Managed Desktop, skal du bede sælger om at henvise til "*system building block part number SBB0Q94938 - MMD Enablement*." Arbejd sammen med din Lenovo-sælger eller Lenovo Channel Partner om anbefalede tjenester, support og billedtjenester.

### <a name="microsoft"></a>Microsoft

Alle Microsoft-enheder, der opfylder krav til enheder, indeholder et billede, der fungerer sammen Microsoft Managed Desktop. Der kræves ikke andre trin.

Hvis du vil have det nyeste billede tilgængeligt i fabriksindstillingerne på en Microsoft-enhed, skal du samarbejde med din Surface-specialist om at bruge Surface "Pegged PO"-processen.

## <a name="existing-devices"></a>Eksisterende enheder

Du kan genbruge eksisterende enheder, så længe de opfylder begge:

- [Krav til enhed](device-requirements.md#minimum-requirements)
- [Softwarekrav](device-requirements.md#installed-software)

Følg de trin, der er relevante for producenten.

Du kan genimmere enheder med et billede fra producenten eller ved at bruge Microsoft Managed Desktop "universelt billede". Du får et relevant producentbillede ved at bestille mindst [én ny](#new-devices) enhed af den model, du bruger. Derefter kan du hente billedet fra den pågældende enhed og anvende det på andre enheder af nøjagtigt den samme model.

> [!NOTE]
> Det er dig, der har ansvaret for at oprette, teste og implementere billeder. Vi anbefaler også, at du bruger de relevante billeder, der leveres af producenten, når det er muligt, i stedet for brugerdefinerede billeder. dette omfatter det "universelle billede".

### <a name="hp"></a>HP

Kommercielle HP-pc'er, der leveres sammen med HP Corporate Ready Image, indeholder en fil `.WIM` til gendannelse. Du kan bruge dette billede til at anvende fabriks gendannelsesbilledet på andre enheder af samme model.

Følgende trin fjerner alle data på enheden. Før du starter, skal du sikkerhedskopier alle data, du vil beholde.

**Sådan fjerner du data på enheden:**

1. [Opret et bootbart USB-drev](/windows-hardware/manufacture/desktop/winpe-create-usb-bootable-drive) med WinPE.
2. Kopiér disse filer fra `C:\\SOURCES` til USB-drevet:
    - FABRIKSgendannelses-WIM-fil (f.eks. `HP\_EliteBook\_840\_G7\_Notebook\_PC\_CR\_2004.wim`)
    - `DEPLOY.CMD`
    - `ReCreatePartitions.txt`
3. [Start enheden til WinPE](https://store.hp.com/us/en/tech-takes/how-to-boot-from-usb-drive-on-windows-10-pcs) USB-drev.
4. I en kommandoprompt skal du [ køreDiskpart.exe](/windows-server/administration/windows-commands/diskpart#additional-references).
5. I Diskpart skal du køre `list disk`, og derefter notere det primære disknummer (typisk Disk 0).
6. Afslut Diskpart ved at skrive `exit`.
7. I kommandoprompten skal du køre , `sys_disk` hvor er disknummeret på den primære disk, du har bestemt, `.WIM` `recovery_wim` og er filnavnet på den fil, `deploy.cmd <sys_disk> <recovery_wim>`du kopierede tidligere.
8. Fjern USB-drevet, og genstart derefter enheden.

### <a name="microsoft"></a>Microsoft

Microsoft Surface-enheder omfatter "gendannelse af metal" [billeder,](https://support.microsoft.com/en-us/surfacerecoveryimage) der er specifikke for hver model. Du kan bruge disse billeder til at genimage enheder.

Disse billeder bruger Windows Recovery Environment (WinRE). Dette er en manuel proces (ikke automatiseret). Følg trinnene i Oprette [og bruge et USB-genoprettelsesdrev til Surface](https://support.microsoft.com/surface/creating-and-using-a-usb-recovery-drive-for-surface-677852e2-ed34-45cb-40ef-398fc7d62c07).

### <a name="universal-image"></a>Universelt billede

Microsoft Managed Desktop har oprettet et billede, der Windows Pro og Microsoft 365 Apps til Enterprise, som du kan bruge med Microsoft Managed Desktop.

Det er dog bedst at bruge billeder, der passer til Microsoft Managed Desktop leveret af producenten, når det er muligt, også selvom det betyder, at en ældre version af Windows skal opdateres, når brugeren logger på. At bruge Microsoft Managed Desktop universelle billede bør være en endelig mulighed.

- Vi opdaterer billedet med de seneste Windows månedlige kvalitetsopdateringer hver 30-60 dage, og Microsoft 365 Apps til Enterprise-opdateringer mindst to gange om året.
- Billedet indeholder en genoprettelses-klargøringspakke for at sikre, Microsoft 365 Apps til Enterprise er gendannet Windows gendannelsesscenarier.
- Du kan installere billedet med USB-drev. Den indeholder en scriptbar proces til indsættelse af drivere. Denne proces er beskrevet i den dokumentation, der følger med billedet.
- Du kan ændre de inkluderede scripts og mapper med andre tilpasninger, f.eks. ved at tilføje specifikke kumulative opdateringer, filkopikode eller udføre andre kontroller.
- Der føjes drivere og kvalitetsopdateringer Windows under udrulning fra USB-drevet.

> [!NOTE]
> Det er dit ansvar at tilføje alle nødvendige drivere, udføre alle tests og sikre, at der ikke er nogen problemer med det endelige installerede billede. Vi leverer det universelle billede "som det er", men giver teknisk vejledning og besvarer spørgsmål. Kontakt MMDImage@microsoft.com.

Indsend anmodninger om det universelle billedes indhold og dokumentation ved at oprette en ændringsanmodning til [administratorportalen](../get-started/access-admin-portal.md).
