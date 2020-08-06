---
title: キューブの書き戻しの使用 (MDX) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- writeback [Analysis Services], cubes
- cubes [Analysis Services], modifying
- modifying cubes
- UPDATE CUBE statement
- cubes [Analysis Services], writeback
ms.assetid: ae2385fc-7fa0-4f8e-98d7-dcb0a5f0eeea
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3ac43e9206619117c1fc090a594ca32ccbeeeb31
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639698"
---
# <a name="using-cube-writebacks-mdx"></a><span data-ttu-id="a05ab-102">キューブの書き戻しの使用 (MDX)</span><span class="sxs-lookup"><span data-stu-id="a05ab-102">Using Cube Writebacks (MDX)</span></span>
  <span data-ttu-id="a05ab-103">キューブを更新するには、 [UPDATE CUBE](/sql/mdx/mdx-data-manipulation-update-cube) ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="a05ab-103">You update a cube by using the [UPDATE CUBE](/sql/mdx/mdx-data-manipulation-update-cube) statement.</span></span> <span data-ttu-id="a05ab-104">このステートメントを使用すると、特定の値で組を更新できます。</span><span class="sxs-lookup"><span data-stu-id="a05ab-104">This statement lets you update a tuple with a specific value.</span></span> <span data-ttu-id="a05ab-105">UPDATE CUBE ステートメントを使って効果的にキューブを更新するには、ステートメントの構文、発生し得るエラー条件、および更新操作がキューブに与える影響を理解しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="a05ab-105">To effectively use the UPDATE CUBE statement to update a cube, you have to understand the syntax for the statement, the error conditions that can occur, and the affect that updates can have on a cube.</span></span>  
  
## <a name="update-cube-statement-syntax"></a><span data-ttu-id="a05ab-106">UPDATE CUBE ステートメントの構文</span><span class="sxs-lookup"><span data-stu-id="a05ab-106">UPDATE CUBE Statement Syntax</span></span>  
 <span data-ttu-id="a05ab-107">UPDATE CUBE ステートメントの構文は、以下のとおりです。</span><span class="sxs-lookup"><span data-stu-id="a05ab-107">The following syntax describes the UPDATE CUBE statement:</span></span>  
  
```  
UPDATE [CUBE] <Cube_Name> SET <tuple>.VALUE = <value> [,<tuple>.VALUE = <value>...]  
 [ USE_EQUAL_ALLOCATION | USE_EQUAL_INCREMENT |  
  USE_WEIGHTED_ALLOCATION [BY <weight value_expression>] |  
  USE_WEIGHTED_INCREMENT [BY <weight value_expression>] ]   
```  
  
 <span data-ttu-id="a05ab-108">組の座標の完全なセットが指定されていない場合、未指定の座標には階層の既定のメンバーが使用されます。</span><span class="sxs-lookup"><span data-stu-id="a05ab-108">If a full set of coordinates is not specified for the tuple, the unspecified coordinates will use the default member of the hierarchy.</span></span> <span data-ttu-id="a05ab-109">指定される組では、 [Sum](/sql/mdx/sum-mdx) 関数を使って集計されるセルを参照する必要があり、計算されるメンバーをいずれかのセルの座標として使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="a05ab-109">The tuple identified must reference a cell that is aggregated with the [Sum](/sql/mdx/sum-mdx) function, and must not use a calculated member as one of the cell's coordinates.</span></span>  
  
 <span data-ttu-id="a05ab-110">UPDATE CUBE ステートメントは、アトミック セルに対する個々のセルの一連の書き戻し操作を生成するサブルーチンのようなものと考えることができます。</span><span class="sxs-lookup"><span data-stu-id="a05ab-110">You can think of the UPDATE CUBE statement as a subroutine that generates a series of individual writeback operations to atomic cells.</span></span> <span data-ttu-id="a05ab-111">その後、これらすべての個々の書き戻し操作は、指定された合計にロール アップします。</span><span class="sxs-lookup"><span data-stu-id="a05ab-111">All these individual writeback operations then roll up into the specified sum.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a05ab-112">更新されるセルが重ならない場合は、`Update Isolation Level` 接続文字列プロパティを使用して、UPDATE CUBE のパフォーマンスを向上させることができます。</span><span class="sxs-lookup"><span data-stu-id="a05ab-112">When updated cells do not overlap, the `Update Isolation Level` connection string property can be used to enhance performance for UPDATE CUBE.</span></span> <span data-ttu-id="a05ab-113">詳細については、「<xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.ConnectionString%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a05ab-113">For more information, see <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.ConnectionString%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a05ab-114">例</span><span class="sxs-lookup"><span data-stu-id="a05ab-114">Example</span></span>  
 <span data-ttu-id="a05ab-115">Adventure Works キューブの Sales Targets メジャー グループを使って UPDATE CUBE をテストできます。</span><span class="sxs-lookup"><span data-stu-id="a05ab-115">You can test UPDATE CUBE using the Sales Targets measure group in the Adventure Works cube.</span></span> <span data-ttu-id="a05ab-116">このメジャー グループは、UPDATE CUBE の要件である SUM によって集計されたメジャーで構成されます。</span><span class="sxs-lookup"><span data-stu-id="a05ab-116">This measure group consists of measures aggregated by SUM, which is a requirement for UPDATE CUBE.</span></span>  
  
1.  <span data-ttu-id="a05ab-117">Adventure Works データベースの Sales Targets メジャー グループに対して書き戻しを有効にします。</span><span class="sxs-lookup"><span data-stu-id="a05ab-117">Enable writeback for the Sales Targets measure group in the Adventure Works database.</span></span> <span data-ttu-id="a05ab-118">Management Studio で、メジャー グループを右クリックし、 **[書き戻しオプション]** をポイントして、 **[書き戻しの有効化]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a05ab-118">In Management Studio, right-click a measure group, point to **Write Back Options**, choose **Enable Writeback**.</span></span>  
  
     <span data-ttu-id="a05ab-119">Writeback フォルダーに新しい書き戻しテーブルが示されます。</span><span class="sxs-lookup"><span data-stu-id="a05ab-119">You should see a new writeback table in the Writeback folder.</span></span> <span data-ttu-id="a05ab-120">テーブル名は WriteTable_Fact Sales Quota です。</span><span class="sxs-lookup"><span data-stu-id="a05ab-120">The table name is WriteTable_Fact Sales Quota.</span></span>  
  
2.  <span data-ttu-id="a05ab-121">MDX クエリ ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="a05ab-121">Open an MDX query window.</span></span> <span data-ttu-id="a05ab-122">元の値を表示するために次の SELECT ステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="a05ab-122">Run the following select statement to view the original value:</span></span>  
  
    ```  
    SELECT [Measures].[Sales Amount Quota] on 0 ,  
    [Employee].[Employee Department].[Title].&[Sales Representative].children on 1  
    FROM [Adventure Works]  
  
    ```  
  
     <span data-ttu-id="a05ab-123">各代表者の販売ノルマを表示する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a05ab-123">You should see sales amount quotas for each representative.</span></span>  
  
3.  <span data-ttu-id="a05ab-124">新しい値を書き戻すために Update Cube ステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="a05ab-124">Run the update cube statement to write back a new value.</span></span> <span data-ttu-id="a05ab-125">この例では、販売量ノルマを 0 に設定しています。</span><span class="sxs-lookup"><span data-stu-id="a05ab-125">In this example, we are setting the sales amount quota to 0.</span></span> <span data-ttu-id="a05ab-126">新しい値は 0 であるため、割り当て方法は指定しません。</span><span class="sxs-lookup"><span data-stu-id="a05ab-126">Because the new value is 0, do not specify an allocation method.</span></span>  
  
    ```  
    UPDATE CUBE [Adventure Works]   
    SET ([Measures].[Sales Amount Quota], [Employee].[Employee Department].[Department].&[Sales]) = 0  
  
    ```  
  
4.  <span data-ttu-id="a05ab-127">SELECT ステートメントを再実行します。</span><span class="sxs-lookup"><span data-stu-id="a05ab-127">Re-run the SELECT statement.</span></span> <span data-ttu-id="a05ab-128">これで、ノルマに 0 が表示されます。</span><span class="sxs-lookup"><span data-stu-id="a05ab-128">You should now see zero for the quotas.</span></span>  
  
 <span data-ttu-id="a05ab-129">書き戻し値は、現在のセッションに制限されます。</span><span class="sxs-lookup"><span data-stu-id="a05ab-129">The writeback value is constrained to the current session.</span></span> <span data-ttu-id="a05ab-130">ユーザーおよびセッション間で値を永続化するために、書き戻しテーブルを処理します。</span><span class="sxs-lookup"><span data-stu-id="a05ab-130">To persist the value across users and sessions, process the writeback table.</span></span> <span data-ttu-id="a05ab-131">Management Studio で、[WriteTable_Fact Sales Quota] を右クリックし、 **[処理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a05ab-131">In Management Studio, right-click WriteTable_Fact Sales Quota and choose **Process**.</span></span>  
  
 <span data-ttu-id="a05ab-132">割り当て方法を指定するには、新しい値が 0 より大きいことが必要です。</span><span class="sxs-lookup"><span data-stu-id="a05ab-132">To specify an allocation method, the new value must be greater than zero.</span></span> <span data-ttu-id="a05ab-133">この例では、Sales Amount Quota の新しい値は 200 万であり、この割り当て方法ではこの金額がすべての販売員に配分されます。</span><span class="sxs-lookup"><span data-stu-id="a05ab-133">In this example, the new value for Sales Amount Quota is two million and the allocation method distributes the amount across all sales representatives.</span></span>  
  
```  
UPDATE CUBE [Adventure Works]   
SET ([Measures].[Sales Amount Quota], [Employee].[Employee Department].[Department].&[Sales]) = 2000000   
USE_EQUAL_ALLOCATION  
```  
  
## <a name="error-conditions"></a><span data-ttu-id="a05ab-134">エラー条件</span><span class="sxs-lookup"><span data-stu-id="a05ab-134">Error Conditions</span></span>  
 <span data-ttu-id="a05ab-135">次の表は、書き戻しが失敗する原因と、エラーの結果を示しています。</span><span class="sxs-lookup"><span data-stu-id="a05ab-135">The following table describes both what can cause writebacks to fail and the result of those errors.</span></span>  
  
|<span data-ttu-id="a05ab-136">エラー条件</span><span class="sxs-lookup"><span data-stu-id="a05ab-136">Error Condition</span></span>|<span data-ttu-id="a05ab-137">結果</span><span class="sxs-lookup"><span data-stu-id="a05ab-137">Result</span></span>|  
|---------------------|------------|  
|<span data-ttu-id="a05ab-138">同じディメンションにあるが、互いに対して存在しないメンバーが更新に含まれる場合。</span><span class="sxs-lookup"><span data-stu-id="a05ab-138">Update includes members from the same dimension that do not exist with one another.</span></span>|<span data-ttu-id="a05ab-139">更新は失敗します。</span><span class="sxs-lookup"><span data-stu-id="a05ab-139">Update will fail.</span></span> <span data-ttu-id="a05ab-140">参照されるセルはキューブ空間に格納されません。</span><span class="sxs-lookup"><span data-stu-id="a05ab-140">The cube space will not contain the referenced cell.</span></span>|  
|<span data-ttu-id="a05ab-141">符号なしの型のメジャーに由来するメジャーが更新に含まれる場合。</span><span class="sxs-lookup"><span data-stu-id="a05ab-141">Update includes a measure sourced to a measure of an unsigned type.</span></span>|<span data-ttu-id="a05ab-142">更新は失敗します。</span><span class="sxs-lookup"><span data-stu-id="a05ab-142">Update will fail.</span></span> <span data-ttu-id="a05ab-143">増分変更を行うには、メジャーが負の値をとることができなければなりません。</span><span class="sxs-lookup"><span data-stu-id="a05ab-143">Increments require that the measure be able to take a negative value.</span></span>|  
|<span data-ttu-id="a05ab-144">合計以外の集計が行われるメジャーが更新に含まれる場合。</span><span class="sxs-lookup"><span data-stu-id="a05ab-144">Update includes a measure that aggregates other than sum.</span></span>|<span data-ttu-id="a05ab-145">エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="a05ab-145">An error is raised.</span></span>|  
|<span data-ttu-id="a05ab-146">サブキューブに対する更新が試行された場合。</span><span class="sxs-lookup"><span data-stu-id="a05ab-146">Update was tried on a subcube.</span></span>|<span data-ttu-id="a05ab-147">エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="a05ab-147">An error is raised.</span></span>|  
  
## <a name="affect-of-cube-changes"></a><span data-ttu-id="a05ab-148">キューブの変更の影響</span><span class="sxs-lookup"><span data-stu-id="a05ab-148">Affect of Cube Changes</span></span>  
 <span data-ttu-id="a05ab-149">次のような変更は、書き戻しに影響を与えません。</span><span class="sxs-lookup"><span data-stu-id="a05ab-149">The following changes will not have an effect on a writeback:</span></span>  
  
-   <span data-ttu-id="a05ab-150">キューブ、キューブのメジャー グループ、またはキューブのディメンションの処理。</span><span class="sxs-lookup"><span data-stu-id="a05ab-150">Processing of a cube, the cube's measure groups, or the cube's dimensions.</span></span>  
  
-   <span data-ttu-id="a05ab-151">いずれかのディメンションへの属性の追加。</span><span class="sxs-lookup"><span data-stu-id="a05ab-151">Adding attributes to any dimension.</span></span>  
  
-   <span data-ttu-id="a05ab-152">新しいディメンションの追加。</span><span class="sxs-lookup"><span data-stu-id="a05ab-152">Adding a new dimension.</span></span>  
  
-   <span data-ttu-id="a05ab-153">書き戻しを含まないディメンションの削除。</span><span class="sxs-lookup"><span data-stu-id="a05ab-153">Deleting a dimension that does not include the writeback.</span></span>  
  
-   <span data-ttu-id="a05ab-154">階層の追加、変更、または削除。</span><span class="sxs-lookup"><span data-stu-id="a05ab-154">Adding, modifying, or removing a hierarchy.</span></span>  
  
-   <span data-ttu-id="a05ab-155">新しいメジャーの追加。</span><span class="sxs-lookup"><span data-stu-id="a05ab-155">Adding a new measure.</span></span>  
  
 <span data-ttu-id="a05ab-156">次のような変更は、書き戻しデータを削除しない限り行うことはできません。</span><span class="sxs-lookup"><span data-stu-id="a05ab-156">The following changes cannot be made without removing the writeback data:</span></span>  
  
-   <span data-ttu-id="a05ab-157">書き戻しに含まれる属性や、その属性階層の削除。</span><span class="sxs-lookup"><span data-stu-id="a05ab-157">Deleting an attribute, or its attribute hierarchy, if the attribute is included in the writeback.</span></span> <span data-ttu-id="a05ab-158">これには、属性または属性階層を明示的に削除することや、属性の親ディメンションを削除することが含まれます。</span><span class="sxs-lookup"><span data-stu-id="a05ab-158">This includes explicitly removing the attribute, or its attribute hierarchy, or removing the attribute's parent dimension.</span></span>  
  
-   <span data-ttu-id="a05ab-159">書き戻しに含まれるメジャーの削除。</span><span class="sxs-lookup"><span data-stu-id="a05ab-159">Deleting a measure included in the writeback.</span></span>  
  
-   <span data-ttu-id="a05ab-160">書き戻しに含まれるディメンションに、`(All)` レベルを使用せずに属性を追加すること。</span><span class="sxs-lookup"><span data-stu-id="a05ab-160">Adding an attribute without an `(All)` level to a dimension included in the writeback.</span></span>  
  
-   <span data-ttu-id="a05ab-161">書き戻しに含まれるディメンションの粒度の変更。</span><span class="sxs-lookup"><span data-stu-id="a05ab-161">Changing the dimension granularity for a dimension included in the writeback.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a05ab-162">参照</span><span class="sxs-lookup"><span data-stu-id="a05ab-162">See Also</span></span>  
 [<span data-ttu-id="a05ab-163">データの変更 &#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="a05ab-163">Modifying Data &#40;MDX&#41;</span></span>](mdx-data-modification-modifying-data.md)  
  
  
