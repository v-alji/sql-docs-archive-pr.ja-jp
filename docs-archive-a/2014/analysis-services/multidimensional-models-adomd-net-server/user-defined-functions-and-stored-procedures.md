---
title: ユーザー定義関数とストアドプロシージャ |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- stored procedures [ADOMD.NET]
- ADOMD.NET, user defined functions
- user defined functions [ADOMD.NET]
- ADOMD.NET, UDFs
- ADOMD.NET, stored procedures
ms.assetid: 07e8aa47-37d4-4bbc-8bff-49e422d12897
author: minewiskan
ms.author: owend
ms.openlocfilehash: a49aa41d158bf2c9fd1ebb1a711d6ff35c0df98b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711122"
---
# <a name="user-defined-functions-and-stored-procedures"></a><span data-ttu-id="4dfdc-102">ユーザー定義関数およびストアド プロシージャ</span><span class="sxs-lookup"><span data-stu-id="4dfdc-102">User Defined Functions and Stored Procedures</span></span>
  <span data-ttu-id="4dfdc-103">ADOMD.NET server オブジェクトを使用すると、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] サーバーからメタデータとデータを操作するためのユーザー定義関数 (UDF) またはストアドプロシージャを作成できます。</span><span class="sxs-lookup"><span data-stu-id="4dfdc-103">With ADOMD.NET server objects, you can create user defined function (UDF) or stored procedures for [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] that interact with metadata and data from the server.</span></span> <span data-ttu-id="4dfdc-104">これらのインプロセス メソッドは、ネットワーク通信に関連する待機時間を伴わず、追加機能を提供する多次元式 (MDX) ステートメントまたはデータ マイニング拡張機能 (DMX) ステートメントを通して呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="4dfdc-104">These in-process methods are called through Multidimensional Expressions (MDX) or Data Mining Extensions (DMX) statements to provide added functionality without the latencies associated with network communications.</span></span>  
  
## <a name="udf-examples"></a><span data-ttu-id="4dfdc-105">UDF の例</span><span class="sxs-lookup"><span data-stu-id="4dfdc-105">UDF Examples</span></span>  
 <span data-ttu-id="4dfdc-106">UDF は、MDX ステートメントまたは DMX ステートメントのコンテキスト内で呼び出すことができます。また、任意の数のパラメーターを取り、任意の型のデータを返します。</span><span class="sxs-lookup"><span data-stu-id="4dfdc-106">A UDF is a method that can be called in the context of an MDX or DMX statement, can take any number of parameters, and can return any type of data.</span></span>  
  
 <span data-ttu-id="4dfdc-107">MDX を使用して作成された UDF は、DMX の UDF と似ています。</span><span class="sxs-lookup"><span data-stu-id="4dfdc-107">A UDF created using MDX is similar to one created for DMX.</span></span> <span data-ttu-id="4dfdc-108">主な違いは、Microsoft.analysisservices.sharepoint.integration.dll などの[microsoft.analysisservices.sharepoint.integration.dll](/previous-versions/sql/sql-server-2014/ms143353(v=sql.120))オブジェクトの特定のプロパティ ( [Microsoft.AnalysisServices.AdomdServer.Context.CurrentCube\*](/previous-versions/sql/sql-server-2014/ms137081(v=sql.120))など) は、1つのスクリプト言語またはもう一方のスクリプト言語でしか使用できないという点です。これは、microsoft.analysisservices.sharepoint.integration.dll プロパティや[CurrentMiningModel \*](/previous-versions/sql/sql-server-2014/ms137178(v=sql.120))プロパティなどです。</span><span class="sxs-lookup"><span data-stu-id="4dfdc-108">The main difference is that certain properties of the [Microsoft.AnalysisServices.AdomdServer.Context](/previous-versions/sql/sql-server-2014/ms143353(v=sql.120)) object, such as the [Microsoft.AnalysisServices.AdomdServer.Context.CurrentCube\*](/previous-versions/sql/sql-server-2014/ms137081(v=sql.120)) and [Microsoft.AnalysisServices.AdomdServer.Context.CurrentMiningModel\*](/previous-versions/sql/sql-server-2014/ms137178(v=sql.120)) properties, are available only for one scripting language or the other.</span></span>  
  
 <span data-ttu-id="4dfdc-109">次の例では、UDF を使用して、ノードの記述を取得し、組をフィルターし、組に対してフィルターを適用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="4dfdc-109">The following examples show how to use a UDF to return a node description, filter tuples, and apply a filter to a tuple.</span></span>  
  
### <a name="returning-a-node-description"></a><span data-ttu-id="4dfdc-110">ノードの記述を取得する</span><span class="sxs-lookup"><span data-stu-id="4dfdc-110">Returning a Node Description</span></span>  
 <span data-ttu-id="4dfdc-111">次の例では、指定されたノードのノード記述を返す UDF を作成します。</span><span class="sxs-lookup"><span data-stu-id="4dfdc-111">The following example creates a UDF that returns the node description for a specified node.</span></span> <span data-ttu-id="4dfdc-112">UDF は、UDF が実行されている現在のコンテキストを使用し、DMX FROM 句を使用して現在のマイニング モデルからノードを取得します。</span><span class="sxs-lookup"><span data-stu-id="4dfdc-112">The UDF uses the current context in which it is being run, and uses a DMX FROM clause to retrieve the node from the current mining model.</span></span>  
  
```  
public string GetNodeDescription(string nodeUniqueName)  
{  
   return Context.CurrentMiningModel.GetNodeFromUniqueName(nodeUniqueName).Description;  
}  
```  
  
 <span data-ttu-id="4dfdc-113">前の例の UDF を配置すると、次の DMX 式で呼び出せるようになります。この式は、最も可能性が高い予測ノードを取得します。</span><span class="sxs-lookup"><span data-stu-id="4dfdc-113">Once deployed, the previous UDF example can be called by the following DMX expression, which retrieves the most-likely prediction node.</span></span> <span data-ttu-id="4dfdc-114">ノード記述には、予測ノードを構成する条件についての情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="4dfdc-114">The description contains information that describes the conditions that make up the prediction node.</span></span>  
  
```  
select Cluster(), SampleAssembly.GetNodeDescription( PredictNodeId(Cluster()) ) FROM [Customer Clusters]  
```  
  
### <a name="returning-tuples"></a><span data-ttu-id="4dfdc-115">組を返す</span><span class="sxs-lookup"><span data-stu-id="4dfdc-115">Returning Tuples</span></span>  
 <span data-ttu-id="4dfdc-116">次の例は、セットおよび返される回数を受け取り、そのセットからランダムに組を取得し、最後のサブセットを返します。</span><span class="sxs-lookup"><span data-stu-id="4dfdc-116">The following example takes a set and a return count, and randomly retrieves tuples from the set, returning a final subset:</span></span>  
  
```  
public Set RandomSample(Set set, int returnCount)  
{  
   //Return the original set if there are fewer tuples  
   //in the set than the number requested.  
   if (set.Tuples.Count <= returnCount)  
      return set;  
  
   System.Random r = new System.Random();  
   SetBuilder returnSet = new SetBuilder();  
  
   //Retrieve random tuples until the return set is filled.  
   int i = set.Tuples.Count;  
   foreach (Tuple t in set.Tuples)  
   {  
      if (r.Next(i) < returnCount)  
      {  
         returnCount--;  
         returnSet.Add(t);  
      }  
      i--;  
      //Stop the loop if we have enough tuples.  
      if (returnCount == 0)  
         break;  
   }  
   return returnSet.ToSet();  
}  
```  
  
 <span data-ttu-id="4dfdc-117">前の例は、次の MDX 式で呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="4dfdc-117">The previous example is called in the following MDX example.</span></span> <span data-ttu-id="4dfdc-118">この MDX の例では、 **Adventure works**データベースから5つのランダムな状態または都道府県が取得されます。</span><span class="sxs-lookup"><span data-stu-id="4dfdc-118">In this MDX example, five random states or provinces are retrieved from the **Adventure Works** database.</span></span>  
  
```  
SELECT SampleAssembly.RandomSample([Geography].[State-Province].Members, 5) on ROWS,   
[Date].[Calendar].[Calendar Year] on COLUMNS  
FROM [Adventure Works]  
WHERE [Measures].[Reseller Freight Cost]  
```  
  
### <a name="applying-a-filter-to-a-tuple"></a><span data-ttu-id="4dfdc-119">組に対してフィルターを適用する</span><span class="sxs-lookup"><span data-stu-id="4dfdc-119">Applying a Filter to a Tuple</span></span>  
 <span data-ttu-id="4dfdc-120">次の例では、UDF は、セットを受け取り、Expression オブジェクトを使用してそのセット内の各組に対してフィルターを適用するように定義されます。</span><span class="sxs-lookup"><span data-stu-id="4dfdc-120">In the following example, a UDF is defined that takes a set, and applies a filter to each tuple in the set, using the Expression object.</span></span> <span data-ttu-id="4dfdc-121">フィルターの条件に合う組は、返されるセットに追加されます。</span><span class="sxs-lookup"><span data-stu-id="4dfdc-121">Any tuples that conform to the filter will be added to a set that is returned.</span></span>  
  
 [!code-csharp[Adomd.NetServer#FilterSet](../../snippets/csharp/SQL14/adomd.net/adomd.netserver/cs/class1.cs#filterset)]  
  
 <span data-ttu-id="4dfdc-122">前の例は、次の MDX 例で呼び出されます。この MDX 例は、セットにフィルターを適用し、名前が "A" で始まる都市だけに絞り込みます。</span><span class="sxs-lookup"><span data-stu-id="4dfdc-122">The previous example is called in the following MDX example, which filters the set to cities with names beginning with 'A'.</span></span>  
  
```  
Select Measures.Members on Rows,  
SampleAssembly.FilterSet([Customer].[Customer Geography].[City], "[Customer].[Customer Geography].[City].CurrentMember.Name < 'B'") on Columns  
From [Adventure Works]  
```  
  
## <a name="stored-procedure-example"></a><span data-ttu-id="4dfdc-123">ストアド プロシージャの例</span><span class="sxs-lookup"><span data-stu-id="4dfdc-123">Stored Procedure Example</span></span>  
 <span data-ttu-id="4dfdc-124">次の例では、MDX ベースのストアド プロシージャが AMO を使用して、必要に応じて Internet Sales のパーティションを作成します。</span><span class="sxs-lookup"><span data-stu-id="4dfdc-124">In the following example, an MDX-based stored procedure uses AMO to create partitions, if needed, for Internet Sales.</span></span>  
  
 [!code-csharp[Adomd.NetServer#CreateInternetSalesMeasureGroupPartitions](../../snippets/csharp/SQL14/adomd.net/adomd.netserver/cs/class1.cs#createinternetsalesmeasuregrouppartitions)]  
  
  
