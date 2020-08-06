---
title: ドリルスルーを使用したソースデータの取得 (MDX) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- DRILLTHROUGH statement
- retrieving data
- queries [MDX], DRILLTHROUGH statement
- data retrieval [MDX]
ms.assetid: fe0ab170-25a9-45a8-a377-f71a67f77018
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5601a3ddfa7075ed53330e12c260af88648db990
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641319"
---
# <a name="using-drillthrough-to-retrieve-source-data-mdx"></a><span data-ttu-id="8e402-102">DRILLTHROUGH を使用したソース データの取得 (MDX)</span><span class="sxs-lookup"><span data-stu-id="8e402-102">Using DRILLTHROUGH to Retrieve Source Data (MDX)</span></span>
  <span data-ttu-id="8e402-103">多次元式 (MDX) では、キューブ セルのソース データから行セットを取得するために [DRILLTHROUGH](/sql/mdx/mdx-data-manipulation-drillthrough)ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="8e402-103">Multidimensional Expressions (MDX) uses the [DRILLTHROUGH](/sql/mdx/mdx-data-manipulation-drillthrough)statement to retrieve a rowset from the source data for a cube cell.</span></span>  
  
 <span data-ttu-id="8e402-104">キューブに対して `DRILLTHROUGH` ステートメントを実行するには、そのキューブに対するドリルスルー アクションを定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8e402-104">In order to run a `DRILLTHROUGH` statement on a cube, a drillthrough action must be defined for that cube.</span></span> <span data-ttu-id="8e402-105">ドリルスルー アクションを定義するには、 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]のキューブ デザイナーの **[アクション]** ペインで、ツール バーの **[新しいドリルスルー アクション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8e402-105">To define a drillthrough action, in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], in Cube Designer, on the **Actions** pane, on the toolbar, click **New Drillthrough Action**.</span></span> <span data-ttu-id="8e402-106">新しいドリルスルー アクションでは、アクションの名前、対象、条件を指定し、`DRILLTHROUGH` ステートメントによって返される列を指定します。</span><span class="sxs-lookup"><span data-stu-id="8e402-106">In the new drillthrough action, specify the action name, target, condition, and the columns that are returned by a `DRILLTHROUGH` statement.</span></span>  
  
## <a name="drillthrough-statement-syntax"></a><span data-ttu-id="8e402-107">DRILLTHROUGH ステートメントの構文</span><span class="sxs-lookup"><span data-stu-id="8e402-107">DRILLTHROUGH Statement Syntax</span></span>  
 <span data-ttu-id="8e402-108">`DRILLTHROUGH` ステートメントの構文は、以下のとおりです。</span><span class="sxs-lookup"><span data-stu-id="8e402-108">The `DRILLTHROUGH` statement uses the following syntax:</span></span>  
  
```  
<drillthrough> ::= DRILLTHROUGH [<Max_Rows>] [<First_Rowset>] <MDX select> [<Return_Columns>]  
   < Max_Rows> ::= MAXROWS <positive number>  
   <First_Rowset> ::= FIRSTROWSET <positive number>  
   <Return_Columns> ::= RETURN <member or attribute> [, <member or attribute>]  
```  
  
 <span data-ttu-id="8e402-109">`SELECT` 句は、取得対象のソース データが入っているキューブ セルを識別します。</span><span class="sxs-lookup"><span data-stu-id="8e402-109">The `SELECT` clause identifies the cube cell that contains the source data to be retrieved.</span></span> <span data-ttu-id="8e402-110">この `SELECT` 句は MDX の通常の `SELECT` ステートメントとほぼ同じですが、`SELECT` 句の場合、それぞれの軸上で 1 つのメンバーだけを指定できます。</span><span class="sxs-lookup"><span data-stu-id="8e402-110">This `SELECT` clause is the same to an ordinary MDX `SELECT` statement, except that in the `SELECT` clause only one member can be specified on each axis.</span></span> <span data-ttu-id="8e402-111">1 つの軸で複数のメンバーが指定されている場合、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="8e402-111">If more than one member is specified on an axis, an error occurs.</span></span>  
  
 <span data-ttu-id="8e402-112">構文 `<Max_Rows>` は、返されるそれぞれの行セットにおける行の最大数を指定します。</span><span class="sxs-lookup"><span data-stu-id="8e402-112">The `<Max_Rows>` syntax specifies the maximum number of the rows in each returned rowset.</span></span> <span data-ttu-id="8e402-113">データ ソースとの接続に使われる OLE DB プロバイダーが `DBPROP_MAXROWS` をサポートしない場合、`<Max_Rows>` の設定は無視されます。</span><span class="sxs-lookup"><span data-stu-id="8e402-113">If the OLE DB provider that is used to connect to the data source does not support `DBPROP_MAXROWS`, the `<Max_Rows>` setting is ignored.</span></span>  
  
 <span data-ttu-id="8e402-114">構文 `<First_Rowset>` は、どのパーティションの行セットが最初に返されるかを識別します。</span><span class="sxs-lookup"><span data-stu-id="8e402-114">The `<First_Rowset>` syntax identifies the partition whose rowset is returned first.</span></span>  
  
 <span data-ttu-id="8e402-115">構文 `<Return_Columns>` は、基になるデータベースのどの列が返されるかを識別します。</span><span class="sxs-lookup"><span data-stu-id="8e402-115">The `<Return_Columns>` syntax identifies the underlying database columns to be returned.</span></span>  
  
## <a name="drillthrough-statement-example"></a><span data-ttu-id="8e402-116">DRILLTHROUGH ステートメントの例</span><span class="sxs-lookup"><span data-stu-id="8e402-116">DRILLTHROUGH Statement Example</span></span>  
 <span data-ttu-id="8e402-117">以下の例は、`DRILLTHROUGH` ステートメントの使用方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="8e402-117">The following example demonstrates the use of the `DRILLTHROUGH` statement.</span></span> <span data-ttu-id="8e402-118">この例の DRILLTHROUGH ステートメントは、Stores ディメンション (スライサー軸) 上の Store、Product、Time ディメンションのリーフを照会して、部門メジャー グループ、部門 ID、従業員の名前を返します。</span><span class="sxs-lookup"><span data-stu-id="8e402-118">In this example, the DRILLTHROUGH statement queries the leaves of the Store, Product, and Time dimensions along the Stores dimension (the slicer axis), and then returns the department measure group, department ID, and employee's first name.</span></span>  
  
```  
DRILLTHROUGH  
Select {Leaves(Store), Leaves(Product), Leaves(Time),*} on 0  
From Stores  
RETURN [Department MeasureGroup].[Department Id], [Employee].[First Name]  
```  
  
## <a name="see-also"></a><span data-ttu-id="8e402-119">参照</span><span class="sxs-lookup"><span data-stu-id="8e402-119">See Also</span></span>  
 [<span data-ttu-id="8e402-120">データの操作 (MDX)</span><span class="sxs-lookup"><span data-stu-id="8e402-120">Manipulating Data &#40;MDX&#41;</span></span>](mdx-data-manipulation-manipulating-data.md)  
  
  
