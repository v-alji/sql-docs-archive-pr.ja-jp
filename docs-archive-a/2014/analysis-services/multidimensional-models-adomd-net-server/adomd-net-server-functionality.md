---
title: ADOMD.NET サーバーの機能 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- functionality [ADOMD.NET]
- ADOMD.NET, functionality
ms.assetid: b74c6957-3f64-4e09-aa09-d06ee93f82fa
author: minewiskan
ms.author: owend
ms.openlocfilehash: f00215c6bcc0104c920be29e0837288a469b252e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712598"
---
# <a name="adomdnet-server-functionality"></a><span data-ttu-id="d3d43-102">ADOMD.NET のサーバー機能</span><span class="sxs-lookup"><span data-stu-id="d3d43-102">ADOMD.NET Server Functionality</span></span>
  <span data-ttu-id="d3d43-103">すべての ADOMD.NET サーバー オブジェクトは、サーバー上のデータやメタデータへの読み取り専用アクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="d3d43-103">All ADOMD.NET server objects provide read-only access to the data and metadata on the server.</span></span> <span data-ttu-id="d3d43-104">データやメタデータを取得するには、ADOMD.NET サーバー オブジェクト モデルを使用します。スキーマ行セットはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="d3d43-104">To retrieve data and metadata, you use the ADOMD.NET server object model as the server object model does not support schema rowsets.</span></span>  
  
 <span data-ttu-id="d3d43-105">ADOMD.NET server オブジェクトを使用すると、のユーザー定義関数 (UDF) またはストアドプロシージャを作成でき [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="d3d43-105">With ADOMD.NET server objects, you can create a user defined function (UDF) or a stored procedure for [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="d3d43-106">これらのインプロセス メソッドは、多次元式 (MDX)、データ マイニング拡張機能 (DMX)、SQL などの言語で作成されたクエリ ステートメントを通じて呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="d3d43-106">These in-process methods are called through query statements created in languages such as Multidimensional Expressions (MDX), Data Mining Extensions (DMX), or SQL.</span></span> <span data-ttu-id="d3d43-107">また、これらのインプロセス メソッドを使用すると、ネットワーク通信に関連する待機時間なしに追加の機能を利用できます。</span><span class="sxs-lookup"><span data-stu-id="d3d43-107">These in-process methods also provide added functionality without the latencies associated with network communications.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d3d43-108">[Microsoft.analysisservices.sharepoint.integration.dll](/previous-versions/sql/sql-server-2014/ms143286(v=sql.120))オブジェクトは、DMX のみをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="d3d43-108">The [Microsoft.AnalysisServices.AdomdServer.AdomdCommand](/previous-versions/sql/sql-server-2014/ms143286(v=sql.120)) object only supports DMX.</span></span>  
  
## <a name="what-is-a-udf"></a><span data-ttu-id="d3d43-109">UDF とは</span><span class="sxs-lookup"><span data-stu-id="d3d43-109">What is a UDF?</span></span>  
 <span data-ttu-id="d3d43-110">*UDF*は、次の特性を持つメソッドです。</span><span class="sxs-lookup"><span data-stu-id="d3d43-110">A *UDF* is a method that has the following characteristics:</span></span>  
  
-   <span data-ttu-id="d3d43-111">クエリのコンテキストで呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="d3d43-111">You can call the UDF in the context of a query.</span></span>  
  
-   <span data-ttu-id="d3d43-112">任意の数のパラメーターを受け取ることができます。</span><span class="sxs-lookup"><span data-stu-id="d3d43-112">The UDF can take any number of parameters.</span></span>  
  
-   <span data-ttu-id="d3d43-113">さまざまな種類のデータを返すことができます。</span><span class="sxs-lookup"><span data-stu-id="d3d43-113">The UDF can return various types of data.</span></span>  
  
 <span data-ttu-id="d3d43-114">次の例では、架空の UDF である `FinalSalesNumber` を使用しています。</span><span class="sxs-lookup"><span data-stu-id="d3d43-114">The following example uses the fictional UDF, `FinalSalesNumber`:</span></span>  
  
```  
SELECT SalesPerson.Name ON ROWS,  
       FinalSalesNumber() ON COLUMNS  
FROM SalesModel  
```  
  
## <a name="what-is-a-stored-procedure"></a><span data-ttu-id="d3d43-115">ストアド プロシージャとは</span><span class="sxs-lookup"><span data-stu-id="d3d43-115">What is a Stored Procedure?</span></span>  
 <span data-ttu-id="d3d43-116">*ストアドプロシージャ*は、次の特性を持つメソッドです。</span><span class="sxs-lookup"><span data-stu-id="d3d43-116">A *stored procedure* is a method that has the following characteristics:</span></span>  
  
-   <span data-ttu-id="d3d43-117">MDX [call](/sql/mdx/mdx-data-manipulation-call)ステートメントを使用して、独自のストアドプロシージャを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="d3d43-117">You call a stored procedure on its own with the MDX [CALL](/sql/mdx/mdx-data-manipulation-call) statement.</span></span>  
  
-   <span data-ttu-id="d3d43-118">ストアドプロシージャは、任意の数のパラメーターを受け取ることができます。</span><span class="sxs-lookup"><span data-stu-id="d3d43-118">A stored procedure can take any number of parameters.</span></span>  
  
-   <span data-ttu-id="d3d43-119">データセット、`IDataReader`、または空の結果を返すことができます。</span><span class="sxs-lookup"><span data-stu-id="d3d43-119">A stored procedure can return a dataset, an `IDataReader`, or an empty result.</span></span>  
  
 <span data-ttu-id="d3d43-120">次の例では、架空のストアド プロシージャである `FinalSalesNumbers` を使用しています。</span><span class="sxs-lookup"><span data-stu-id="d3d43-120">The following example uses the fictional stored procedure, `FinalSalesNumbers`:</span></span>  
  
```  
CALL FinalSalesNumbers()  
```  
  
## <a name="see-also"></a><span data-ttu-id="d3d43-121">参照</span><span class="sxs-lookup"><span data-stu-id="d3d43-121">See Also</span></span>  
 [<span data-ttu-id="d3d43-122">ADOMD.NET サーバー プログラミング</span><span class="sxs-lookup"><span data-stu-id="d3d43-122">ADOMD.NET Server Programming</span></span>](https://docs.microsoft.com/bi-reference/adomd/multidimensional-models-adomd-net-server/adomd-net-server-programming)  
  
  
