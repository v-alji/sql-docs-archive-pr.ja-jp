---
title: Reserved ORDPATH data type | の後に指定された UDT&#39;s を削除します。Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 474e910a-6abb-4e28-acc2-055338c011d4
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 0528d19de17781d863e3a42fdef7db558fe5d190
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742802"
---
# <a name="remove-udt39s-named-after-the-reserved-ordpath-data-type"></a><span data-ttu-id="b41e4-102">Reserved ORDPATH データ型の後に指定された UDT&#39;s を削除します。</span><span class="sxs-lookup"><span data-stu-id="b41e4-102">Remove UDT&#39;s named after the reserved ORDPATH data type</span></span>
  <span data-ttu-id="b41e4-103">アップグレード アドバイザーによって、`ORDPATH` データ型に予約されている語句に基づいて名前が付けられたユーザー定義型 (UDT) が検出されました。</span><span class="sxs-lookup"><span data-stu-id="b41e4-103">Upgrade Advisor detected a user-defined type (UDT) that is named after a term reserved for the `ORDPATH` data type.</span></span>  
  
## <a name="component"></a><span data-ttu-id="b41e4-104">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="b41e4-104">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="b41e4-105">説明</span><span class="sxs-lookup"><span data-stu-id="b41e4-105">Description</span></span>  
 <span data-ttu-id="b41e4-106">組み込みデータ型に使用される語句を共通言語ランタイム (CLR) またはエイリアス UDT の名前として使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="b41e4-106">The terms used for built-in data types should not be used as names for either common language runtime (CLR) or alias UDTs.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="b41e4-107">修正措置</span><span class="sxs-lookup"><span data-stu-id="b41e4-107">Corrective Action</span></span>  
 <span data-ttu-id="b41e4-108">データ型に基づいて名前が付けられた UDT を削除し、予約されていない名前を使用して UDT を再作成します。</span><span class="sxs-lookup"><span data-stu-id="b41e4-108">Remove the UDT that is named after the data type and recreate the UDT with an unreserved name.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="b41e4-109">外部リソース</span><span class="sxs-lookup"><span data-stu-id="b41e4-109">External Resources</span></span>  
 [<span data-ttu-id="b41e4-110">ユーザー定義型の作成</span><span class="sxs-lookup"><span data-stu-id="b41e4-110">Creating a User-Defined Type</span></span>](../../relational-databases/clr-integration-database-objects-user-defined-types/creating-user-defined-types.md)  
  
  
