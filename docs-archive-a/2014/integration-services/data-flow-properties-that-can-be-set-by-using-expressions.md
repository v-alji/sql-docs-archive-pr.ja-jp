---
title: 式を使用して設定できるデータフロープロパティ |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SQL Server Integration Services packages, property expressions
- Integration Services packages, property expressions
- packages [Integration Services], properties
- SSIS packages, property expressions
- property expressions [Integration Services]
ms.assetid: cd0e171a-08be-45d6-81dc-ed94f37698b8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1763a531b1d91a60d2bb3775ae9fbe9942c6b7e5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713361"
---
# <a name="data-flow-properties-that-can-be-set-by-using-expressions"></a><span data-ttu-id="8c4e0-102">式を使って設定できるデータ フロー プロパティ</span><span class="sxs-lookup"><span data-stu-id="8c4e0-102">Data Flow Properties that Can Be Set by Using Expressions</span></span>
  <span data-ttu-id="8c4e0-103">データ フロー タスク コンテナーで使用できるプロパティ式を使用して、データ フロー オブジェクトの特定のプロパティの値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="8c4e0-103">The values of certain properties of data flow objects can be specified by using property expressions available on the Data Flow task container.</span></span>  
  
 <span data-ttu-id="8c4e0-104">プロパティ式の使用の詳細については、「 [パッケージでプロパティ式を使用する](expressions/use-property-expressions-in-packages.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8c4e0-104">For information about using property expressions, see [Use Property Expressions in Packages](expressions/use-property-expressions-in-packages.md).</span></span>  
  
 <span data-ttu-id="8c4e0-105">プロパティ式を使用して、パッケージを配置するインスタンスごとに構成をカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="8c4e0-105">You can use property expressions to customize configurations for each deployed instance of a package.</span></span> <span data-ttu-id="8c4e0-106">また、コマンド プロンプト ユーティリティ **dtexec** に **/set** オプションを付けて使用すると、プロパティ式を使用してパッケージの実行時制約を指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="8c4e0-106">You can also use property expressions to specify run-time constraints for a package by using the **/set** option with the **dtexec** command prompt utility.</span></span> <span data-ttu-id="8c4e0-107">たとえば、並べ替え変換で使用される `MaximumThreads`、または、あいまいグループ化変換およびあいまい参照変換の `MaxMemoryUsage` を制約できます。</span><span class="sxs-lookup"><span data-stu-id="8c4e0-107">For example, you can constrain the `MaximumThreads` used by the Sort transformation, or the `MaxMemoryUsage` of the Fuzzy Grouping and Fuzzy Lookup transformations.</span></span> <span data-ttu-id="8c4e0-108">制約を行わないと、これらの変換により大容量のデータがメモリ内にキャッシュされる場合があります。</span><span class="sxs-lookup"><span data-stu-id="8c4e0-108">If unconstrained, these transformations may cache large amounts of data in memory.</span></span>  
  
 <span data-ttu-id="8c4e0-109">このトピックに示すデータ フロー オブジェクトのプロパティの 1 つに対するプロパティ式を指定するには、デザイナーの **[制御フロー]** 画面でデータ フロー タスクを選択するか、コンポーネントやパスを個別に選択せずにデザイナーの **[データ フロー]** タブを選択して、データ フロー タスクの **[プロパティ]** ウィンドウを表示します。</span><span class="sxs-lookup"><span data-stu-id="8c4e0-109">To specify a property expression for one of the properties of data flow objects listed in this topic, display the **Properties** window for the Data Flow task by selecting the Data Flow task on the **Control Flow** surface of the designer, or by selecting the **Data Flow** tab of the designer without selecting any individual component or path.</span></span> <span data-ttu-id="8c4e0-110">**[式]** プロパティを選択し、省略記号 (...) をクリックして、 **[プロパティ式エディター]** ダイアログ ボックスを表示します。</span><span class="sxs-lookup"><span data-stu-id="8c4e0-110">Select the **Expressions** property and click the ellipsis (...) to display the **Property Expressions Editor** dialog box.</span></span> <span data-ttu-id="8c4e0-111">**[プロパティ]** の一覧からプロパティを選択し、 **[式]** テキスト ボックスに式を入力するか、省略記号 (...) をクリックして **[式ビルダー]** ダイアログ ボックスを表示します。</span><span class="sxs-lookup"><span data-stu-id="8c4e0-111">Drop down the **Property** list to select a property, then type an expression in the **Expression** text box, or click the ellipsis (...) to display the **Expression Builder** dialog box.</span></span>  
  
 <span data-ttu-id="8c4e0-112">**[プロパティ]** の一覧には、現在、デザイナーの **[データ フロー]** 画面に配置されているデータ フロー オブジェクトで使用できるプロパティのみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="8c4e0-112">The **Property** list displays available properties for only those data flow objects that you have already placed on the **Data Flow** surface of the designer.</span></span> <span data-ttu-id="8c4e0-113">したがって、 **[プロパティ]** の一覧では、プロパティ式をサポートするデータ フロー オブジェクトのすべてのプロパティを表示することはできません。</span><span class="sxs-lookup"><span data-stu-id="8c4e0-113">Therefore, you cannot use the **Property** list to view all the possible properties of data flow objects that support property expressions.</span></span> <span data-ttu-id="8c4e0-114">たとえば、デザイナー画面に ADO NET ソースを配置した場合 **、プロパティの一覧に**はプロパティのエントリが格納され `[ADO NET Source].[SqlCommand]` ます。</span><span class="sxs-lookup"><span data-stu-id="8c4e0-114">For example, if you have placed an ADO NET source on the designer surface, the **Property** list contains an entry for the `[ADO NET Source].[SqlCommand]` property.</span></span> <span data-ttu-id="8c4e0-115">この一覧には、データ フロー タスク自体の多数のプロパティも表示されます。</span><span class="sxs-lookup"><span data-stu-id="8c4e0-115">The list also displays many properties of the Data Flow task itself.</span></span>  
  
## <a name="properties-of-data-flow-objects-that-support-property-expressions"></a><span data-ttu-id="8c4e0-116">プロパティ式をサポートするデータ フロー オブジェクトのプロパティ</span><span class="sxs-lookup"><span data-stu-id="8c4e0-116">Properties of Data Flow Objects That Support Property Expressions</span></span>  
 <span data-ttu-id="8c4e0-117">次の一覧にあるプロパティの値は、プロパティ式を使用して指定できます。</span><span class="sxs-lookup"><span data-stu-id="8c4e0-117">The values of the properties in the following list can be specified by using property expressions.</span></span>  
  
### <a name="data-flow-sources"></a><span data-ttu-id="8c4e0-118">データ フローの変換元</span><span class="sxs-lookup"><span data-stu-id="8c4e0-118">Data Flow Sources</span></span>  
  
|<span data-ttu-id="8c4e0-119">データ フロー オブジェクト</span><span class="sxs-lookup"><span data-stu-id="8c4e0-119">Data Flow object</span></span>|<span data-ttu-id="8c4e0-120">プロパティ</span><span class="sxs-lookup"><span data-stu-id="8c4e0-120">Property</span></span>|  
|----------------------|--------------|  
|<span data-ttu-id="8c4e0-121">ADO NET ソース</span><span class="sxs-lookup"><span data-stu-id="8c4e0-121">ADO NET source</span></span>|<span data-ttu-id="8c4e0-122">TableOrViewName プロパティ</span><span class="sxs-lookup"><span data-stu-id="8c4e0-122">TableOrViewName property</span></span><br /><br /> <span data-ttu-id="8c4e0-123">SqlCommand プロパティ</span><span class="sxs-lookup"><span data-stu-id="8c4e0-123">SqlCommand property</span></span>|  
|<span data-ttu-id="8c4e0-124">XML ソース</span><span class="sxs-lookup"><span data-stu-id="8c4e0-124">XML source</span></span>|<span data-ttu-id="8c4e0-125">XMLData プロパティ</span><span class="sxs-lookup"><span data-stu-id="8c4e0-125">XMLData property</span></span><br /><br /> <span data-ttu-id="8c4e0-126">XMLSchemaDefinition プロパティ</span><span class="sxs-lookup"><span data-stu-id="8c4e0-126">XMLSchemaDefinition property</span></span>|  
  
### <a name="data-flow-transformations"></a><span data-ttu-id="8c4e0-127">データ フロー変換</span><span class="sxs-lookup"><span data-stu-id="8c4e0-127">Data Flow Transformations</span></span>  
 <span data-ttu-id="8c4e0-128">これらのカスタム プロパティの詳細については、「 [変換のカスタム プロパティ](data-flow/transformations/transformation-custom-properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8c4e0-128">For more information about these custom properties, see [Transformation Custom Properties](data-flow/transformations/transformation-custom-properties.md).</span></span>  
  
|<span data-ttu-id="8c4e0-129">データ フロー オブジェクト</span><span class="sxs-lookup"><span data-stu-id="8c4e0-129">Data Flow object</span></span>|<span data-ttu-id="8c4e0-130">プロパティ</span><span class="sxs-lookup"><span data-stu-id="8c4e0-130">Property</span></span>|  
|----------------------|--------------|  
|<span data-ttu-id="8c4e0-131">条件分割変換</span><span class="sxs-lookup"><span data-stu-id="8c4e0-131">Conditional Split transformation</span></span>|<span data-ttu-id="8c4e0-132">FriendlyExpression プロパティ</span><span class="sxs-lookup"><span data-stu-id="8c4e0-132">FriendlyExpression property</span></span>|  
|<span data-ttu-id="8c4e0-133">派生列変換</span><span class="sxs-lookup"><span data-stu-id="8c4e0-133">Derived Column transformation</span></span>|<span data-ttu-id="8c4e0-134">FriendlyExpression プロパティ</span><span class="sxs-lookup"><span data-stu-id="8c4e0-134">FriendlyExpression property</span></span>|  
|<span data-ttu-id="8c4e0-135">あいまいグループ化変換</span><span class="sxs-lookup"><span data-stu-id="8c4e0-135">Fuzzy Grouping transformation</span></span>|<span data-ttu-id="8c4e0-136">MaxMemoryUsage プロパティ</span><span class="sxs-lookup"><span data-stu-id="8c4e0-136">MaxMemoryUsage property</span></span>|  
|<span data-ttu-id="8c4e0-137">あいまい参照変換</span><span class="sxs-lookup"><span data-stu-id="8c4e0-137">Fuzzy Lookup transformation</span></span>|<span data-ttu-id="8c4e0-138">MaxMemoryUsage プロパティ</span><span class="sxs-lookup"><span data-stu-id="8c4e0-138">MaxMemoryUsage property</span></span>|  
|<span data-ttu-id="8c4e0-139">参照変換</span><span class="sxs-lookup"><span data-stu-id="8c4e0-139">Lookup transformation</span></span>|<span data-ttu-id="8c4e0-140">SqlCommand プロパティ</span><span class="sxs-lookup"><span data-stu-id="8c4e0-140">SqlCommand property</span></span><br /><br /> <span data-ttu-id="8c4e0-141">SqlCommandParam プロパティ</span><span class="sxs-lookup"><span data-stu-id="8c4e0-141">SqlCommandParam property</span></span>|  
|<span data-ttu-id="8c4e0-142">OLE DB コマンド変換</span><span class="sxs-lookup"><span data-stu-id="8c4e0-142">OLE DB Command transformation</span></span>|<span data-ttu-id="8c4e0-143">SqlCommand プロパティ</span><span class="sxs-lookup"><span data-stu-id="8c4e0-143">SqlCommand property</span></span>|  
|<span data-ttu-id="8c4e0-144">比率サンプリング変換</span><span class="sxs-lookup"><span data-stu-id="8c4e0-144">Percentage Sampling transformation</span></span>|<span data-ttu-id="8c4e0-145">SamplingValue プロパティ</span><span class="sxs-lookup"><span data-stu-id="8c4e0-145">SamplingValue property</span></span>|  
|<span data-ttu-id="8c4e0-146">ピボット変換</span><span class="sxs-lookup"><span data-stu-id="8c4e0-146">Pivot transformation</span></span>|<span data-ttu-id="8c4e0-147">PivotKeyValue プロパティ</span><span class="sxs-lookup"><span data-stu-id="8c4e0-147">PivotKeyValue property</span></span>|  
|<span data-ttu-id="8c4e0-148">行サンプリング変換</span><span class="sxs-lookup"><span data-stu-id="8c4e0-148">Row Sampling transformation</span></span>|<span data-ttu-id="8c4e0-149">SamplingValue プロパティ</span><span class="sxs-lookup"><span data-stu-id="8c4e0-149">SamplingValue property</span></span>|  
|<span data-ttu-id="8c4e0-150">並べ替え変換</span><span class="sxs-lookup"><span data-stu-id="8c4e0-150">Sort transformation</span></span>|<span data-ttu-id="8c4e0-151">MaximumThreads プロパティ</span><span class="sxs-lookup"><span data-stu-id="8c4e0-151">MaximumThreads property</span></span>|  
|<span data-ttu-id="8c4e0-152">ピボット解除変換</span><span class="sxs-lookup"><span data-stu-id="8c4e0-152">Unpivot transformation</span></span>|<span data-ttu-id="8c4e0-153">PivotKeyValue プロパティ</span><span class="sxs-lookup"><span data-stu-id="8c4e0-153">PivotKeyValue property</span></span>|  
  
### <a name="data-flow-destinations"></a><span data-ttu-id="8c4e0-154">データ フローの変換先</span><span class="sxs-lookup"><span data-stu-id="8c4e0-154">Data Flow Destinations</span></span>  
  
|<span data-ttu-id="8c4e0-155">データ フロー オブジェクト</span><span class="sxs-lookup"><span data-stu-id="8c4e0-155">Data Flow object</span></span>|<span data-ttu-id="8c4e0-156">プロパティ</span><span class="sxs-lookup"><span data-stu-id="8c4e0-156">Property</span></span>|  
|----------------------|--------------|  
|<span data-ttu-id="8c4e0-157">ADO NET 変換先</span><span class="sxs-lookup"><span data-stu-id="8c4e0-157">ADO NET Destination</span></span>|<span data-ttu-id="8c4e0-158">TableOrViewName プロパティ</span><span class="sxs-lookup"><span data-stu-id="8c4e0-158">TableOrViewName property</span></span><br /><br /> <span data-ttu-id="8c4e0-159">BatchSize プロパティ</span><span class="sxs-lookup"><span data-stu-id="8c4e0-159">BatchSize property</span></span><br /><br /> <span data-ttu-id="8c4e0-160">CommandTimeOut プロパティ</span><span class="sxs-lookup"><span data-stu-id="8c4e0-160">CommandTimeout property</span></span>|  
|<span data-ttu-id="8c4e0-161">フラット ファイル変換先</span><span class="sxs-lookup"><span data-stu-id="8c4e0-161">Flat File destination</span></span>|<span data-ttu-id="8c4e0-162">Header プロパティ</span><span class="sxs-lookup"><span data-stu-id="8c4e0-162">Header property</span></span>|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="8c4e0-163">Compact 変換先</span><span class="sxs-lookup"><span data-stu-id="8c4e0-163">Compact destination</span></span>|<span data-ttu-id="8c4e0-164">TableName プロパティ</span><span class="sxs-lookup"><span data-stu-id="8c4e0-164">TableName property</span></span>|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="8c4e0-165">変換先</span><span class="sxs-lookup"><span data-stu-id="8c4e0-165">destination</span></span>|<span data-ttu-id="8c4e0-166">BulkInsertTableName プロパティ</span><span class="sxs-lookup"><span data-stu-id="8c4e0-166">BulkInsertTableName property</span></span><br /><br /> <span data-ttu-id="8c4e0-167">BulkInsertFirstRow プロパティ</span><span class="sxs-lookup"><span data-stu-id="8c4e0-167">BulkInsertFirstRow property</span></span><br /><br /> <span data-ttu-id="8c4e0-168">BulkInsertLastRow プロパティ</span><span class="sxs-lookup"><span data-stu-id="8c4e0-168">BulkInsertLastRow property</span></span><br /><br /> <span data-ttu-id="8c4e0-169">BulkInsertOrder プロパティ</span><span class="sxs-lookup"><span data-stu-id="8c4e0-169">BulkInsertOrder property</span></span><br /><br /> <span data-ttu-id="8c4e0-170">Timeout プロパティ</span><span class="sxs-lookup"><span data-stu-id="8c4e0-170">Timeout property</span></span>|  
  
## <a name="related-tasks"></a><span data-ttu-id="8c4e0-171">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="8c4e0-171">Related Tasks</span></span>  
  
-   [<span data-ttu-id="8c4e0-172">プロパティ式を追加または変更する</span><span class="sxs-lookup"><span data-stu-id="8c4e0-172">Add or Change a Property Expression</span></span>](expressions/add-or-change-a-property-expression.md)  
  
## <a name="related-content"></a><span data-ttu-id="8c4e0-173">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="8c4e0-173">Related Content</span></span>  
 <span data-ttu-id="8c4e0-174">pragmaticworks.com の技術記事「 [SSIS 式チート シート](https://pragmaticworks.com/Resources/Cheat-Sheets/SSIS-Expression-Cheat-Sheet)」</span><span class="sxs-lookup"><span data-stu-id="8c4e0-174">Technical article, [SSIS Expression Cheat Sheet](https://pragmaticworks.com/Resources/Cheat-Sheets/SSIS-Expression-Cheat-Sheet), on pragmaticworks.com</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c4e0-175">参照</span><span class="sxs-lookup"><span data-stu-id="8c4e0-175">See Also</span></span>  
 <span data-ttu-id="8c4e0-176">[パッケージでプロパティ式を使用する](expressions/use-property-expressions-in-packages.md) </span><span class="sxs-lookup"><span data-stu-id="8c4e0-176">[Use Property Expressions in Packages](expressions/use-property-expressions-in-packages.md) </span></span>  
 <span data-ttu-id="8c4e0-177">[共通プロパティ](../../2014/integration-services/common-properties.md) </span><span class="sxs-lookup"><span data-stu-id="8c4e0-177">[Common Properties](../../2014/integration-services/common-properties.md) </span></span>  
 <span data-ttu-id="8c4e0-178">[変換のカスタムプロパティ](data-flow/transformations/transformation-custom-properties.md) </span><span class="sxs-lookup"><span data-stu-id="8c4e0-178">[Transformation Custom Properties](data-flow/transformations/transformation-custom-properties.md) </span></span>  
 [<span data-ttu-id="8c4e0-179">パスのプロパティ</span><span class="sxs-lookup"><span data-stu-id="8c4e0-179">Path Properties</span></span>](../../2014/integration-services/path-properties.md)  
  
  
