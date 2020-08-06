---
title: 予約された日付と時刻のデータ型の後に指定された UDT&#39;s を削除します |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- time data type [SQL Server], UDTs
- date data type [SQL Server], UDTs
ms.assetid: 48f109af-b1d1-4f03-a7e3-8a0b05ed94e8
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 827f060b309a7a620fd448554b074f45d78d3cb0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643107"
---
# <a name="remove-udt39s-named-after-the-reserved-date-and-time-data-types"></a><span data-ttu-id="fc294-102">予約された日付と時刻のデータ型の後に指定された UDT&#39;s を削除します</span><span class="sxs-lookup"><span data-stu-id="fc294-102">Remove UDT&#39;s named after the reserved DATE and TIME data types</span></span>
  <span data-ttu-id="fc294-103">アップグレード アドバイザーによって、`date` データ型または `time` データ型に予約されている語句に基づいて名前が付けられたユーザー定義型 (UDT) が検出されました。</span><span class="sxs-lookup"><span data-stu-id="fc294-103">Upgrade Advisor detected a user-defined type (UDT) that is named after a term reserved for either the `date` or the `time` data types.</span></span>  
  
## <a name="component"></a><span data-ttu-id="fc294-104">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="fc294-104">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="fc294-105">説明</span><span class="sxs-lookup"><span data-stu-id="fc294-105">Description</span></span>  
 <span data-ttu-id="fc294-106">データ型に使用される語句を共通言語ランタイム (CLR) またはエイリアス UDT の名前として使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="fc294-106">The terms used for data types should not be used as names for either common language runtime (CLR) or alias UDTs.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="fc294-107">修正措置</span><span class="sxs-lookup"><span data-stu-id="fc294-107">Corrective Action</span></span>  
 <span data-ttu-id="fc294-108">データ型に基づいて名前が付けられた UDT を削除し、予約されていない名前を使用して UDT を再作成します。</span><span class="sxs-lookup"><span data-stu-id="fc294-108">Remove the UDT that is named after the data type and recreate the UDT with an unreserved name.</span></span>  
  
  
