---
title: 予約された GEOMETRY データ型と GEOGRAPHY データ型の後に名前が付けられた Udt を削除します。Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- geometry data type [SQL Server], UDTs
- geography data type [SQL Server], UDTs
ms.assetid: a167ce3a-50b4-4e77-a884-adb23b586c72
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 4977d45d53e1114edc8e04ad504963bae0b9eb9d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742801"
---
# <a name="remove-udts-named-after-the-reserved-geometry-and-geography-data-types"></a><span data-ttu-id="5cfbc-102">予約されている GEOMETRY データ型および GEOGRAPHY データ型に基づいて名前が付けられた UDT の削除</span><span class="sxs-lookup"><span data-stu-id="5cfbc-102">Remove UDTs named after the reserved GEOMETRY and GEOGRAPHY data types</span></span>
  <span data-ttu-id="5cfbc-103">アップグレード アドバイザーによって、`geometry` データ型または `geography` データ型に予約されている語句に基づいて名前が付けられたユーザー定義型 (UDT) が検出されました。</span><span class="sxs-lookup"><span data-stu-id="5cfbc-103">Upgrade Advisor detected a user-defined type (UDT) that is named after a term reserved for either the `geometry` or the `geography` data types.</span></span> <span data-ttu-id="5cfbc-104">`geometry` データ型および `geography` データ型は、空間データ機能の一部です。</span><span class="sxs-lookup"><span data-stu-id="5cfbc-104">The `geometry` and `geography` data types are part of the spatial data feature.</span></span>  
  
## <a name="component"></a><span data-ttu-id="5cfbc-105">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="5cfbc-105">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="5cfbc-106">説明</span><span class="sxs-lookup"><span data-stu-id="5cfbc-106">Description</span></span>  
 <span data-ttu-id="5cfbc-107">空間データ型に使用される語句を共通言語ランタイム (CLR) またはエイリアス UDT の名前として使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="5cfbc-107">The terms used for spatial data types should not be used as names for either common language runtime (CLR) or alias UDTs.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="5cfbc-108">修正措置</span><span class="sxs-lookup"><span data-stu-id="5cfbc-108">Corrective Action</span></span>  
 <span data-ttu-id="5cfbc-109">データ型に基づいて名前が付けられた UDT を削除し、予約されていない名前を使用して UDT を再作成します。</span><span class="sxs-lookup"><span data-stu-id="5cfbc-109">Remove the UDT that is named after the data type and recreate the UDT with an unreserved name.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="5cfbc-110">外部リソース</span><span class="sxs-lookup"><span data-stu-id="5cfbc-110">External Resources</span></span>  
 [<span data-ttu-id="5cfbc-111">ユーザー定義型の作成</span><span class="sxs-lookup"><span data-stu-id="5cfbc-111">Creating a User-Defined Type</span></span>](../../relational-databases/clr-integration-database-objects-user-defined-types/creating-user-defined-types.md)  
  
 [<span data-ttu-id="5cfbc-112">空間データ型の概要</span><span class="sxs-lookup"><span data-stu-id="5cfbc-112">Spatial Data Types Overview</span></span>](../../relational-databases/spatial/spatial-data-types-overview.md)  
  
  
