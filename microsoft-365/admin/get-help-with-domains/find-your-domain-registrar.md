---
title: Find din domæneregistrator
f1.keywords:
- CSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_O365_Setup
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
- GEA150
ms.assetid: b5b633ba-1e56-4a98-8ff5-2acaac63a5c8
description: Lær at finde din domæneregistrator og DNS-udbyder ved hjælp af InterNIC-søgning.
ms.openlocfilehash: c7802067bc3d8397d9f7b7ddf0f6cda4dd57c38b
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63588107"
---
# <a name="find-your-domain-registrar"></a>Find din domæneregistrator

 **[Tjek ofte stillede spørgsmål om](../setup/domains-faq.yml)** domæner, hvis du ikke kan finde det, du leder efter.

## <a name="domain-registrar"></a>Domæneregistrator

### <a name="find-your-domain-name-registrar"></a>Find din domæneregistrator

> [!NOTE]
> Kun domæner, der slutter *med .COM*, *.NET* og *.EDU* , fungerer med dette værktøj.

1. Skriv dit [domæne i feltet](https://go.microsoft.com/fwlink/p/?LinkId=402770) **Whois Search** på søgesiden InterNIC. For eksempel  *contoso.com.*

2. Vælg indstillingen **Domæne** , og vælg derefter **Send**.

3. Find posten **Registrar** på siden **Whois Search Results**. Her kan du se, hvordan den organisation, der leverer registratortjeneste for dit domæne, vises.

## <a name="dns-hosting-provider"></a>DNS-udbyder

### <a name="find-your-dns-hosting-provider"></a>Find din DNS-udbyder

> [!NOTE]
> Kun domæner, der slutter *med .COM*, *.NET* og *.EDU* , fungerer med dette værktøj.

1. Skriv dit [domæne i feltet](https://go.microsoft.com/fwlink/p/?LinkId=402770) **Whois Search** på søgesiden InterNIC. For eksempel contoso.com.

2. Vælg indstillingen **Domæne** , og vælg derefter **Send**.

3. Find **den første Navneserver-post på siden Whois Search Results**.

4. Kopiér de navneserveroplysninger (NS), der vises efter kolonet (:), og indsæt dem derefter i feltet  Søg øverst på siden. Vælg **Nameserver**, og vælg derefter **Submit**.

5. Find posten **Registrar** på siden **Whois Search Results**. Her kan du se, hvilken DNS-udbyder der ejer navneserveren for dit domæne.

---

