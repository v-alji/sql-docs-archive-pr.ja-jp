---
title: MultiPoint | Microsoft Docs
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- MultiPoint geometry subtype [SQL Server]
ms.assetid: 2aaab211-3aba-4dbd-90b7-095d997b1f62
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: b741071b7986aceea4e49d4fde8293ef2c96fc2b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644925"
---
# <a name="multipoint"></a><span data-ttu-id="d816c-102">MultiPoint</span><span class="sxs-lookup"><span data-stu-id="d816c-102">MultiPoint</span></span>
  <span data-ttu-id="d816c-103">`MultiPoint` は、0 個以上のポイントのコレクションです。</span><span class="sxs-lookup"><span data-stu-id="d816c-103">A `MultiPoint` is a collection of zero or more points.</span></span> <span data-ttu-id="d816c-104">`MultiPoint` インスタンスの境界は空になります。</span><span class="sxs-lookup"><span data-stu-id="d816c-104">The boundary of a `MultiPoint` instance is empty.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="d816c-105">例</span><span class="sxs-lookup"><span data-stu-id="d816c-105">Examples</span></span>  
 <span data-ttu-id="d816c-106">次の例では、SRID が 23 で、ポイントが 2 つある (1 つは座標 (2,3) のポイントで、もう 1 つは座標 (7,8) で Z が 9.5 のポイント) `geometry MultiPoint` インスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="d816c-106">The following example creates a `geometry MultiPoint` instance with SRID 23 and two points: one point with the coordinates (2, 3), one point with the coordinates (7, 8), and a Z value of 9.5.</span></span>  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('MULTIPOINT((2 3), (7 8 9.5))', 23);  
```  
  
 <span data-ttu-id="d816c-107">この `MultiPoint` インスタンスは、次のように `STMPointFromText()` を使用して表現することもできます。</span><span class="sxs-lookup"><span data-stu-id="d816c-107">This `MultiPoint` instance can also be expressed using `STMPointFromText()` as shown below.</span></span>  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STMPointFromText('MULTIPOINT((2 3), (7 8 9.5))', 23);  
```  
  
 <span data-ttu-id="d816c-108">次のコード例では、 `STGeometryN()` メソッドを使用して、コレクション内の最初のポイントの説明を取得します。</span><span class="sxs-lookup"><span data-stu-id="d816c-108">The following example uses the method `STGeometryN()` to retrieve a description of the first point in the collection.</span></span>  
  
```  
SELECT @g.STGeometryN(1).STAsText();  
```  
  
## <a name="see-also"></a><span data-ttu-id="d816c-109">参照</span><span class="sxs-lookup"><span data-stu-id="d816c-109">See Also</span></span>  
 <span data-ttu-id="d816c-110">[視点](point.md) </span><span class="sxs-lookup"><span data-stu-id="d816c-110">[Point](point.md) </span></span>  
 [<span data-ttu-id="d816c-111">空間データ &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="d816c-111">Spatial Data &#40;SQL Server&#41;</span></span>](spatial-data-sql-server.md)  
  
  
