---
title: 空間データに対するニアレスト ネイバーのクエリ | Microsoft Docs
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: 7af4ad5d-484e-45b4-aa16-83c33b358bb6
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 644b3e5cfdaeff7457639bc2da77260b64011735
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644918"
---
# <a name="query-spatial-data-for-nearest-neighbor"></a><span data-ttu-id="c517f-102">空間データに対するニアレスト ネイバーのクエリ</span><span class="sxs-lookup"><span data-stu-id="c517f-102">Query Spatial Data for Nearest Neighbor</span></span>
  <span data-ttu-id="c517f-103">空間データで使用される一般的なクエリの 1 つに、ニアレスト ネイバー クエリがあります。</span><span class="sxs-lookup"><span data-stu-id="c517f-103">A common query used with spatial data is the Nearest Neighbor query.</span></span> <span data-ttu-id="c517f-104">ニアレスト ネイバー クエリは、特定の空間オブジェクトに最も近い空間オブジェクトを検索するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="c517f-104">Nearest Neighbor queries are used to find the closest spatial objects to a specific spatial object.</span></span> <span data-ttu-id="c517f-105">たとえば、Web サイトのストア ロケーターは、多くの場合、顧客の場所に最も近い店舗の場所を検索する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c517f-105">For example a store locater for a Web site often must find the closest store locations to a customer location.</span></span>  
  
 <span data-ttu-id="c517f-106">ニアレスト ネイバー クエリは、さまざまな有効なクエリ形式で記述できますが、空間インデックスを使用するニアレスト ネイバー クエリでは、次の構文を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c517f-106">A Nearest Neighbor query can be written in a variety of valid query formats, but for the Nearest Neighbor query to use a spatial index the following syntax must be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c517f-107">構文</span><span class="sxs-lookup"><span data-stu-id="c517f-107">Syntax</span></span>  
  
```vb  
SELECT TOP ( number )  
        [ WITH TIES ]  
        [ * | expression ]   
        [, ...]  
    FROM spatial_table_reference, ...   
        [ WITH   
            (   
                [ INDEX ( index_ref ) ]   
                [ , SPATIAL_WINDOW_MAX_CELLS = <value>]   
                [ ,... ]   
            )   
        ]  
    WHERE   
        column_ref.STDistance ( @spatial_ object )   
            {   
                [ IS NOT NULL ] | [ < const ] | [ > const ]   
                | [ <= const ] | [ >= const ] | [ <> const ] ]   
            }  
            [ AND { other_predicate } ]   
    }  
    ORDER BY column_ref.STDistance ( @spatial_ object ) [ ,...n ]  
[ ; ]  
  
```  
  
## <a name="nearest-neighbor-query-and-spatial-indexes"></a><span data-ttu-id="c517f-108">ニアレスト ネイバー クエリと空間インデックス</span><span class="sxs-lookup"><span data-stu-id="c517f-108">Nearest Neighbor Query and Spatial Indexes</span></span>  
 <span data-ttu-id="c517f-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、`TOP` および `ORDER BY` 句は、空間データ列にニアレスト ネイバー クエリを実行するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="c517f-109">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], `TOP` and `ORDER BY` clauses are used to perform a Nearest Neighbor query on spatial data columns.</span></span> <span data-ttu-id="c517f-110">`ORDER BY` 句には、空間列データ型の `STDistance()` メソッドの呼び出しが含まれます。</span><span class="sxs-lookup"><span data-stu-id="c517f-110">The `ORDER BY` clause contains a call to the `STDistance()` method for the spatial column data type.</span></span> <span data-ttu-id="c517f-111">`TOP` 句は、クエリで返されるオブジェクトの数を示します。</span><span class="sxs-lookup"><span data-stu-id="c517f-111">The `TOP` clause indicates the number of objects to return for the query.</span></span>  
  
 <span data-ttu-id="c517f-112">ニアレスト ネイバー クエリで空間インデックスを使用するには、次の要件を満たす必要があります。</span><span class="sxs-lookup"><span data-stu-id="c517f-112">The following requirements must be met for a Nearest Neighbor query to use a spatial index:</span></span>  
  
1.  <span data-ttu-id="c517f-113">空間インデックスが空間列の 1 つにあり、`STDistance()` メソッドが `WHERE` および `ORDER BY` 句でその列を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c517f-113">A spatial index must be present on one of the spatial columns and the `STDistance()` method must use that column in the `WHERE` and `ORDER BY` clauses.</span></span>  
  
2.  <span data-ttu-id="c517f-114">`TOP`句は `PERCENT` ステートメントを含むことはできません。</span><span class="sxs-lookup"><span data-stu-id="c517f-114">The `TOP` clause cannot contain a `PERCENT` statement.</span></span>  
  
3.  <span data-ttu-id="c517f-115">`WHERE` 句は `STDistance()` メソッドを含む必要があります。</span><span class="sxs-lookup"><span data-stu-id="c517f-115">The `WHERE` clause must contain a `STDistance()` method.</span></span>  
  
4.  <span data-ttu-id="c517f-116">`WHERE` 句に複数の述語がある場合、`STDistance()` メソッドを含む述語は、`AND` 結合で他の述語と接続する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c517f-116">If there are multiple predicates in the `WHERE` clause then the predicate containing `STDistance()` method must be connected by an `AND` conjunction to the other predicates.</span></span> <span data-ttu-id="c517f-117">`STDistance()` メソッドは、`WHERE` 句のオプションの一部にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="c517f-117">The `STDistance()` method cannot be in an optional part of the `WHERE` clause.</span></span>  
  
5.  <span data-ttu-id="c517f-118">`ORDER BY` 句の最初の式では `STDistance()` メソッドを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c517f-118">The first expression in the `ORDER BY` clause must use the `STDistance()` method.</span></span>  
  
6.  <span data-ttu-id="c517f-119">`ORDER BY` 句の最初の `STDistance()` 式の並べ替え順序は、`ASC` である必要があります。</span><span class="sxs-lookup"><span data-stu-id="c517f-119">Sort order for the first `STDistance()` expression in the `ORDER BY` clause must be `ASC`.</span></span>  
  
7.  <span data-ttu-id="c517f-120">`STDistance` が `NULL` を返すすべての行は、フィルターで除外する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c517f-120">All the rows for which `STDistance` returns `NULL` must be filtered out.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="c517f-121">`geography` または `geometry` データ型を引数として取るメソッドは、SRID がその型と同一でない場合、`NULL` を返します。</span><span class="sxs-lookup"><span data-stu-id="c517f-121">Methods that take `geography` or `geometry` data types as arguments will return `NULL` if the SRIDs are not the same for the types.</span></span>  
  
 <span data-ttu-id="c517f-122">ニアレスト ネイバー クエリで使用されるインデックスでは、新しい空間インデックス テセレーションを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="c517f-122">It is recommended that the new spatial index tessellations be used for indexes used in Nearest Neighbor queries.</span></span> <span data-ttu-id="c517f-123">空間インデックス テセレーションの詳細については、「 [空間データ &#40;SQL Server&#41;](spatial-data-sql-server.md)である必要があります。</span><span class="sxs-lookup"><span data-stu-id="c517f-123">For more information on spatial index tessellations, see [Spatial Data &#40;SQL Server&#41;](spatial-data-sql-server.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c517f-124">例</span><span class="sxs-lookup"><span data-stu-id="c517f-124">Example</span></span>  
 <span data-ttu-id="c517f-125">次のコード例は、空間インデックスを使用できるニアレスト ネイバー クエリを示します。</span><span class="sxs-lookup"><span data-stu-id="c517f-125">The following code example shows a Nearest Neighbor query that can use a spatial index.</span></span> <span data-ttu-id="c517f-126">次の例では、 `Person.Address` データベースにある `AdventureWorks2012` テーブルを使用しています。</span><span class="sxs-lookup"><span data-stu-id="c517f-126">The example uses the `Person.Address` table in `AdventureWorks2012` database.</span></span>  
  
```  
USE AdventureWorks2012  
GO  
DECLARE @g geography = 'POINT(-121.626 47.8315)';  
SELECT TOP(7) SpatialLocation.ToString(), City FROM Person.Address  
WHERE SpatialLocation.STDistance(@g) IS NOT NULL  
ORDER BY SpatialLocation.STDistance(@g);  
  
```  
  
 <span data-ttu-id="c517f-127">列 SpatialLocation にインデックスを作成して、ニアレスト ネイバー クエリが空間インデックスを使用する方法を確認します。</span><span class="sxs-lookup"><span data-stu-id="c517f-127">Create a spatial index on the column SpatialLocation to see how a Nearest Neighbor query uses a spatial index.</span></span> <span data-ttu-id="c517f-128">空間インデックスの作成の詳細については、「 [Create, Modify, and Drop Spatial Indexes](create-modify-and-drop-spatial-indexes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c517f-128">For more information on creating spatial indexes, see [Create, Modify, and Drop Spatial Indexes](create-modify-and-drop-spatial-indexes.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c517f-129">例</span><span class="sxs-lookup"><span data-stu-id="c517f-129">Example</span></span>  
 <span data-ttu-id="c517f-130">次のコード例は、空間インデックスを使用できないニアレスト ネイバー クエリを示します。</span><span class="sxs-lookup"><span data-stu-id="c517f-130">The following code example shows a Nearest Neighbor query that cannot use a spatial index.</span></span>  
  
```  
USE AdventureWorks2012  
GO  
DECLARE @g geography = 'POINT(-121.626 47.8315)';  
SELECT TOP(7) SpatialLocation.ToString(), City FROM Person.Address  
ORDER BY SpatialLocation.STDistance(@g);  
  
```  
  
 <span data-ttu-id="c517f-131">このクエリは、構文で指定した形式の `STDistance()` を使用する `WHERE` 句がないため、空間インデックスを使用できません。</span><span class="sxs-lookup"><span data-stu-id="c517f-131">The query lacks a `WHERE` clause that uses `STDistance()` in a form specified in the syntax section so the query cannot use a spatial index.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c517f-132">参照</span><span class="sxs-lookup"><span data-stu-id="c517f-132">See Also</span></span>  
 [<span data-ttu-id="c517f-133">空間データ &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="c517f-133">Spatial Data &#40;SQL Server&#41;</span></span>](spatial-data-sql-server.md)  
  
  
