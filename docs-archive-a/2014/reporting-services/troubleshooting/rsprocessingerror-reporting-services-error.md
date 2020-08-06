---
title: rsProcessingError - Reporting Services エラー | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- rsProcessingError
ms.assetid: 414ee58a-8251-4367-9a8e-10c068d17280
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ca98c5532db080ab1e146e2aaa81e24fcb25579b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643171"
---
# <a name="rsprocessingerror---reporting-services-error"></a><span data-ttu-id="d64be-102">rsProcessingError - Reporting Services エラー</span><span class="sxs-lookup"><span data-stu-id="d64be-102">rsProcessingError - Reporting Services Error</span></span>
    
## <a name="details"></a><span data-ttu-id="d64be-103">詳細</span><span class="sxs-lookup"><span data-stu-id="d64be-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d64be-104">製品名</span><span class="sxs-lookup"><span data-stu-id="d64be-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="d64be-105">イベント ID</span><span class="sxs-lookup"><span data-stu-id="d64be-105">Event ID</span></span>|<span data-ttu-id="d64be-106">rsProcessingError</span><span class="sxs-lookup"><span data-stu-id="d64be-106">rsProcessingError</span></span>|  
|<span data-ttu-id="d64be-107">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="d64be-107">Event Source</span></span>|<span data-ttu-id="d64be-108">Microsoft.ReportingServices.Diagnostics.Utilities.ErrorStrings.resources</span><span class="sxs-lookup"><span data-stu-id="d64be-108">Microsoft.ReportingServices.Diagnostics.Utilities.ErrorStrings.resources</span></span>|  
|<span data-ttu-id="d64be-109">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="d64be-109">Component</span></span>|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|  
|<span data-ttu-id="d64be-110">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="d64be-110">Message Text</span></span>|<span data-ttu-id="d64be-111">レポートの処理中にエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="d64be-111">Errors have occurred in report processing.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="d64be-112">説明</span><span class="sxs-lookup"><span data-stu-id="d64be-112">Explanation</span></span>  
 <span data-ttu-id="d64be-113">レポートのサブスクリプションをパブリッシュ、処理、ローカルでプレビュー、レポート サーバーから表示、または作成しているときに、1 つ以上のエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="d64be-113">One or more errors were encountered while publishing, processing, previewing locally, viewing from the report server, or creating a subscription for a report.</span></span> <span data-ttu-id="d64be-114">このエラー メッセージは、少なくとも 1 つのエラーが検出されたことを示しています。</span><span class="sxs-lookup"><span data-stu-id="d64be-114">This error message indicates at least one error was detected.</span></span>  
  
### <a name="possible-causes"></a><span data-ttu-id="d64be-115">考えられる原因</span><span class="sxs-lookup"><span data-stu-id="d64be-115">Possible Causes</span></span>  
 <span data-ttu-id="d64be-116">次の原因が考えられます。</span><span class="sxs-lookup"><span data-stu-id="d64be-116">Possible causes include:</span></span>  
  
-   <span data-ttu-id="d64be-117">レポート サーバーで処理エラーが発生した。</span><span class="sxs-lookup"><span data-stu-id="d64be-117">A processing error occurred on the report server.</span></span>  
  
-   <span data-ttu-id="d64be-118">レポートをプレビューするときに、ローカルでのレポート処理の際、処理エラーが発生した。</span><span class="sxs-lookup"><span data-stu-id="d64be-118">A processing error occurred during local report processing when previewing a report.</span></span>  
  
-   <span data-ttu-id="d64be-119">グループ式が、不適切なデータ型に評価された。</span><span class="sxs-lookup"><span data-stu-id="d64be-119">A group expression evaluated to an incorrect data type.</span></span>  
  
-   <span data-ttu-id="d64be-120">比較できないデータ型として評価される 2 つの式をフィルター定義で指定した。</span><span class="sxs-lookup"><span data-stu-id="d64be-120">A filter definition specified two expressions that evaluated to data types that could not be compared.</span></span>  
  
-   <span data-ttu-id="d64be-121">Fields コレクションに存在しないフィールドを式で参照した。</span><span class="sxs-lookup"><span data-stu-id="d64be-121">An expression referenced a non-existing field in the Fields collection.</span></span>  
  
-   <span data-ttu-id="d64be-122">無効または競合するスコープを使用した集計関数呼び出しが式に含まれていた。</span><span class="sxs-lookup"><span data-stu-id="d64be-122">An expression included an aggregate function call with an invalid or conflicting scope.</span></span>  
  
-   <span data-ttu-id="d64be-123">レポート パラメーター コレクションに存在しないパラメーターを式で参照した。</span><span class="sxs-lookup"><span data-stu-id="d64be-123">An expression referenced a non-existing parameter in the Report Parameters collection.</span></span>  
  
-   <span data-ttu-id="d64be-124">正しく展開されていないカスタム アセンブリまたは [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] アセンブリを読み込めなかった。</span><span class="sxs-lookup"><span data-stu-id="d64be-124">A custom assembly or a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] assembly that was incorrectly deployed failed to load.</span></span>  
  
-   <span data-ttu-id="d64be-125">Null 許容プロパティがに設定されているパラメーターは、 `False` パラメーターに null 値を検出しました。</span><span class="sxs-lookup"><span data-stu-id="d64be-125">A parameter that has the Nullable property set to `False` has detected a null value in the parameter.</span></span>  
  
-   <span data-ttu-id="d64be-126">データ領域の Hidden プロパティの式に次のエラーが含まれています。オブジェクト参照がオブジェクト インスタンスに設定されていません。</span><span class="sxs-lookup"><span data-stu-id="d64be-126">An expression for the Hidden property of a data region contains an error: Object reference not set to an instance of an object.</span></span>  
  
-   <span data-ttu-id="d64be-127">無効な関数呼び出しまたは構文エラーが式に含まれていた。</span><span class="sxs-lookup"><span data-stu-id="d64be-127">An expression included an invalid function call or syntax error.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="d64be-128">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="d64be-128">User Action</span></span>  
  
### <a name="finding-more-information"></a><span data-ttu-id="d64be-129">詳細情報</span><span class="sxs-lookup"><span data-stu-id="d64be-129">Finding More Information</span></span>  
 <span data-ttu-id="d64be-130">必要に応じて以下の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="d64be-130">Do one or more of the following actions:</span></span>  
  
-   <span data-ttu-id="d64be-131">レポート サーバーからレポートを表示している場合、またはサブスクリプションとしてレポートを表示している場合は、エラー メッセージを通読します。</span><span class="sxs-lookup"><span data-stu-id="d64be-131">If you are viewing the report from the report server or if you are viewing the report as a subscription, look at the entire text of the error message.</span></span> <span data-ttu-id="d64be-132">詳細テキストに追加情報が記載されています。</span><span class="sxs-lookup"><span data-stu-id="d64be-132">Additional information is provided in the expanded text.</span></span>  
  
-   <span data-ttu-id="d64be-133">レポート デザイナーでレポートを作成していて、レポートのプレビューまたはパブリッシュ中にこのエラーが表示された場合は、[エラー一覧] ウィンドウに追加情報が記載されています。</span><span class="sxs-lookup"><span data-stu-id="d64be-133">If you are authoring a report in Report Designer and see this error when you preview or publish the report, additional information is provided in the Error List window.</span></span>  
  
-   <span data-ttu-id="d64be-134">レポート デザイナー プレビューでレポートを作成している場合は、エラー メッセージ全体に目を通します。</span><span class="sxs-lookup"><span data-stu-id="d64be-134">If you are authoring a report in Report Designer Preview, look at the entire text of the error message.</span></span> <span data-ttu-id="d64be-135">詳細テキストに追加情報が記載されています。</span><span class="sxs-lookup"><span data-stu-id="d64be-135">Additional information is provided in the expanded text.</span></span>  
  
-   <span data-ttu-id="d64be-136">レポート サーバーでレポートを表示していて、さらにレポート サーバーをローカル管理者として実行している場合は、ページを右クリックして **[ソースの表示]** をクリックすると、呼び出し履歴を表示できます。</span><span class="sxs-lookup"><span data-stu-id="d64be-136">If you are viewing a report on the report server, and if you are running as local administrator on the report server, you can view the call stack if you right-click the page and select **View Source**.</span></span> <span data-ttu-id="d64be-137">呼び出し履歴には追加情報が記載されています。</span><span class="sxs-lookup"><span data-stu-id="d64be-137">Additional information is provided in the call stack.</span></span>  
  
-   <span data-ttu-id="d64be-138">レポート サーバーでローカル管理者として処理を実行している場合は、ログ ファイル内で `ReportProcessingException`を検索します。</span><span class="sxs-lookup"><span data-stu-id="d64be-138">If you are running as local administrator on the report server, search the log file for `ReportProcessingException`.</span></span> <span data-ttu-id="d64be-139">ログ エントリには詳細情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="d64be-139">Log entries contain more information.</span></span> <span data-ttu-id="d64be-140">レポートサーバーのログファイルは、通常、次の場所にあります。 \<*drive*>MSSQLSERVER\Reporting Services\LogFiles\ ReportServerService__*datetimestamp*.log.</span><span class="sxs-lookup"><span data-stu-id="d64be-140">The report server log file is typically located at \<*drive*>:\Program Files\Microsoft SQL Server\MSRS12.MSSQLSERVER\Reporting Services\LogFiles\ReportServerService__*datetimestamp*.log.</span></span> <span data-ttu-id="d64be-141">詳細については、「 [Reporting Services のログ ファイルとソース](../report-server/reporting-services-log-files-and-sources.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d64be-141">For more information, see [Reporting Services Log Files and Sources](../report-server/reporting-services-log-files-and-sources.md).</span></span>  
  
### <a name="failed-to-load-expression-host-assembly"></a><span data-ttu-id="d64be-142">式のホスト アセンブリの読み込みに失敗した</span><span class="sxs-lookup"><span data-stu-id="d64be-142">Failed to Load Expression Host Assembly</span></span>  
 <span data-ttu-id="d64be-143">カスタム アセンブリには、厳密な名前の署名と、属性 AllowPartiallyTrustedCallers の設定が必要です。</span><span class="sxs-lookup"><span data-stu-id="d64be-143">Custom assemblies must have strong name signing and the attribute AllowPartiallyTrustedCallers set.</span></span> <span data-ttu-id="d64be-144">詳細については、「 [レポートでのカスタム アセンブリの使用](../custom-assemblies/using-custom-assemblies-with-reports.md) 」と「 [セキュリティ ポリシーの概要](../extensions/secure-development/understanding-security-policies.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d64be-144">For more information, see [Using Custom Assemblies with Reports](../custom-assemblies/using-custom-assemblies-with-reports.md) and [Understanding Security Policies](../extensions/secure-development/understanding-security-policies.md).</span></span>  
  
### <a name="a-built-in-global-name-does-not-exist"></a><span data-ttu-id="d64be-145">組み込みのグローバル名が存在しない</span><span class="sxs-lookup"><span data-stu-id="d64be-145">A Built-in Global Name Does Not Exist</span></span>  
 <span data-ttu-id="d64be-146">式内のスペルを確認します。</span><span class="sxs-lookup"><span data-stu-id="d64be-146">Check the spelling in expressions.</span></span> <span data-ttu-id="d64be-147">組み込みのグローバル、パラメーター、およびフィールド名では、大文字と小文字が区別されます。</span><span class="sxs-lookup"><span data-stu-id="d64be-147">Built-in globals, parameters, and field names are case-sensitive.</span></span> <span data-ttu-id="d64be-148">エラーが発生した式で、レポートに名前が実際に存在し、そのスペルが正しいことを確認します。</span><span class="sxs-lookup"><span data-stu-id="d64be-148">In the expression causing the error, check that the name actually exists in the report and that it is spelled correctly.</span></span> <span data-ttu-id="d64be-149">詳細については、「[式で使用される組み込みコレクション &#40;レポート ビルダーおよび SSRS&#41;](../report-design/built-in-collections-in-expressions-report-builder.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d64be-149">For more information, see [Built-in Collections in Expressions &#40;Report Builder and SSRS&#41;](../report-design/built-in-collections-in-expressions-report-builder.md).</span></span>  
  
### <a name="parameter-properties-and-null"></a><span data-ttu-id="d64be-150">パラメーターのプロパティと NULL</span><span class="sxs-lookup"><span data-stu-id="d64be-150">Parameter Properties and Null</span></span>  
 <span data-ttu-id="d64be-151">複数値パラメーターには NULL を設定できません。</span><span class="sxs-lookup"><span data-stu-id="d64be-151">A multivalue parameter cannot be Null.</span></span> <span data-ttu-id="d64be-152">詳細については、「 [レポート パラメーター (レポート ビルダーおよびレポート デザイナー)](../report-design/report-parameters-report-builder-and-report-designer.md)にあります。</span><span class="sxs-lookup"><span data-stu-id="d64be-152">For more information, see [Report Parameters &#40;Report Builder and Report Designer&#41;](../report-design/report-parameters-report-builder-and-report-designer.md).</span></span>  
  
### <a name="main-report-with-subreport-could-not-be-processed"></a><span data-ttu-id="d64be-153">サブレポートを含むメイン レポートを処理できなかった</span><span class="sxs-lookup"><span data-stu-id="d64be-153">Main Report with Subreport Could Not Be Processed</span></span>  
 <span data-ttu-id="d64be-154">サブレポートを含むレポートは、同一バージョンの [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] レポート プロセッサで処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d64be-154">A report with subreports must be processed by the same version of the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report processor.</span></span> <span data-ttu-id="d64be-155">レポートを最新バージョンのレポート定義スキーマにアップグレードする場合、メイン レポートとサブレポートは同時に更新されることもされないこともあります。</span><span class="sxs-lookup"><span data-stu-id="d64be-155">When upgrading reports to the current version of the report definition schema, the main report and the subreports may or may not be updated at the same time.</span></span> <span data-ttu-id="d64be-156">レポートとそのサブレポートの間でバージョンが一致しないと、"サブレポートを処理できませんでした" というメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d64be-156">If the version is not compatible between a report and its subreports, the following message is displayed: "Subreport could not be processed."</span></span>  
  
 <span data-ttu-id="d64be-157">すべてのレポートを同一バージョンのレポート プロセッサで処理できるように、メイン レポートまたはサブレポートのいずれかを変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d64be-157">You must change either the main report or the subreports so that all the reports can be processed by the same version of the report processor.</span></span> <span data-ttu-id="d64be-158">レポートをアップグレードできない場合の原因については、「 [レポートのアップグレード](../install-windows/upgrade-reports.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d64be-158">For information about why a report fails to upgrade, see [Upgrade Reports](../install-windows/upgrade-reports.md).</span></span>  
  
### <a name="verify-function-calls-are-visual-basic-and-not-sql"></a><span data-ttu-id="d64be-159">関数呼び出しが SQL ではなく Visual Basic であることを確認する</span><span class="sxs-lookup"><span data-stu-id="d64be-159">Verify Function Calls are Visual Basic and Not SQL</span></span>  
 <span data-ttu-id="d64be-160">リレーショナル データベースのクエリ テキストでは SQL 関数を使用できます。</span><span class="sxs-lookup"><span data-stu-id="d64be-160">You can use SQL functions in query text on a relational database.</span></span> <span data-ttu-id="d64be-161">[!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 関数はクエリ テキストで使用できません。</span><span class="sxs-lookup"><span data-stu-id="d64be-161">You cannot use [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] functions in query text.</span></span>  
  
 <span data-ttu-id="d64be-162">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]では、 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 関数、System.Math 関数、System.String 関数、完全に修飾された [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 関数、またはカスタム コードやカスタム アセンブリで指定したカスタム関数を式内で使用できます。</span><span class="sxs-lookup"><span data-stu-id="d64be-162">In [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], expressions can use [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] functions, System.Math or System.String functions, fully qualified [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] functions, or custom functions that you provide in custom code or a custom assembly.</span></span> <span data-ttu-id="d64be-163">式で SQL 関数は使用できません。</span><span class="sxs-lookup"><span data-stu-id="d64be-163">You cannot use SQL functions in an expression.</span></span>  
  
 <span data-ttu-id="d64be-164">クエリ内および式内の関数呼び出しが有効であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="d64be-164">Verify that the function calls made in the query and in the expressions are valid.</span></span>  
  
### <a name="cannot-compare-data-types-for-a-filter"></a><span data-ttu-id="d64be-165">フィルターのデータ型を比較できない</span><span class="sxs-lookup"><span data-stu-id="d64be-165">Cannot Compare Data Types for a Filter</span></span>  
 <span data-ttu-id="d64be-166">フィルターの演算式では、フィルターの対象を定義するフィルター式とフィルター値は、比較できるように同じデータ型にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d64be-166">In a filter equation, the filter expression that defines what to filter on and the filter value must be the same data type in order to be compared.</span></span> <span data-ttu-id="d64be-167">次のいずれかのエラーが表示された場合は、データ型が一致するようにフィールド式またはフィルター値を変更します。</span><span class="sxs-lookup"><span data-stu-id="d64be-167">If you see one of the following errors, modify the field expression or the filter value so that the data types match:</span></span>  
  
-   <span data-ttu-id="d64be-168">のの処理を *\<report item type>* *\<report item name>* 実行できません。</span><span class="sxs-lookup"><span data-stu-id="d64be-168">The processing of *\<report item type>* for the *\<report item name>* cannot be performed.</span></span> <span data-ttu-id="d64be-169">型と型のデータを比較することはできません *\<type>* *\<type>* 。</span><span class="sxs-lookup"><span data-stu-id="d64be-169">Cannot compare data of types *\<type>* and *\<type>*.</span></span> <span data-ttu-id="d64be-170">によって返されたデータ型を確認してください *\<report item name>* 。</span><span class="sxs-lookup"><span data-stu-id="d64be-170">Please check the data type returned by the *\<report item name>*.</span></span>  
  
-   <span data-ttu-id="d64be-171">を評価できませんでした *\<property name>* 。</span><span class="sxs-lookup"><span data-stu-id="d64be-171">Failed to evaluate the *\<property name>*.</span></span>  
  
-   <span data-ttu-id="d64be-172">を評価できませんでした *\<property name>* 。</span><span class="sxs-lookup"><span data-stu-id="d64be-172">Failed to evaluate the *\<property name>*.</span></span> <span data-ttu-id="d64be-173">エラーが発生したデータセットフィールドを参照 *\<error string>* しています:。</span><span class="sxs-lookup"><span data-stu-id="d64be-173">It references a dataset field which has an error: *\<error string>*.</span></span>  
  
 <span data-ttu-id="d64be-174">詳細については、「 [データのフィルター、グループ化、および並べ替え (レポート ビルダーおよび SSRS)](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d64be-174">For more information, see [Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md).</span></span>  
  
### <a name="invalid-or-conflicting-scope-specification-in-an-aggregate-function-call"></a><span data-ttu-id="d64be-175">集計関数呼び出しでの無効または競合するスコープの指定</span><span class="sxs-lookup"><span data-stu-id="d64be-175">Invalid or Conflicting Scope Specification in an Aggregate Function Call</span></span>  
 <span data-ttu-id="d64be-176">Tablix セルの式に集計関数呼び出しを含める場合、レポート プロセッサでは、セルが属している最も内側のグループのスコープでその式を評価します。</span><span class="sxs-lookup"><span data-stu-id="d64be-176">When you include aggregate function calls to an expression in a Tablix cell, the report processor evaluates the expression in the scope of the innermost groups to which the cell belongs.</span></span>  
  
 <span data-ttu-id="d64be-177">特定のスコープの名前を集計関数に渡すこともできます。</span><span class="sxs-lookup"><span data-stu-id="d64be-177">You can also pass the name of a specific scope to an aggregate function.</span></span> <span data-ttu-id="d64be-178">スコープでは、データセットの名前、データ領域、またはデータ階層のより上位のスコープの名前を参照できます。</span><span class="sxs-lookup"><span data-stu-id="d64be-178">Scope can refer to the name of a dataset, a data region, or the name of a scope higher on the data hierarchy.</span></span> <span data-ttu-id="d64be-179">これは、次のメッセージに当てはまります。</span><span class="sxs-lookup"><span data-stu-id="d64be-179">This applies to the following messages:</span></span>  
  
-   <span data-ttu-id="d64be-180">*\<report item type>*' *\<report item name>* ' に無効なスコープ "" が含まれてい *\<scope name>* ます。</span><span class="sxs-lookup"><span data-stu-id="d64be-180">The *\<report item type>* '*\<report item name>*' has an invalid scope "*\<scope name>*".</span></span> <span data-ttu-id="d64be-181">スコープは現在のスコープであるか、または現在のスコープ内に含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="d64be-181">The scope must be the current scope, or contained within the current scope.</span></span>  
  
-   <span data-ttu-id="d64be-182">*\<property name>*' ' の式には、 *\<report item type>* *\<report item name>* 集計関数に対して無効なスコープパラメーターが含まれています。</span><span class="sxs-lookup"><span data-stu-id="d64be-182">The *\<property name>* expression for the *\<report item type>* '*\<report item name>*' has a scope parameter that is not valid for an aggregate function.</span></span> <span data-ttu-id="d64be-183">スコープのパラメーターは、含まれるグループの名前、含まれるデータ領域の名前、またはデータセットの名前のいずれかと同じ文字列の定数に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d64be-183">The scope parameter must be set to a string constant that is equal to either the name of a containing group, the name of a containing data region, or the name of a dataset.</span></span>  
  
 <span data-ttu-id="d64be-184">累計を計算する集計関数 (`Previous`、`RunningValue`、または `RowNumber`) の場合、行グループ名または列グループ名をスコープのパラメーターに指定できますが、両方を指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="d64be-184">For aggregate functions that calculate running totals (`Previous`, `RunningValue`, or `RowNumber`), you can specify a scope parameter that is either a row group name or a column group name, but not both.</span></span> <span data-ttu-id="d64be-185">これは、次のエラー メッセージに当てはまります。</span><span class="sxs-lookup"><span data-stu-id="d64be-185">This applies to the following error message:</span></span>  
  
-   <span data-ttu-id="d64be-186">`Previous``RunningValue`または `RowNumber` ' ' のデータセルで使用される集計関数は *\<report item type>* *\<report item name>* 、の列と行の両方でグループ化スコープを参照し *\<report item type>* ます。</span><span class="sxs-lookup"><span data-stu-id="d64be-186">`Previous`, `RunningValue` or `RowNumber` aggregate functions used in the data cells of the *\<report item type>* '*\<report item name>*' refer to grouping scopes in both the columns and rows of the *\<report item type>*.</span></span> <span data-ttu-id="d64be-187">内のすべてのおよび集計関数のスコープパラメーターは、 `Previous` `RunningValue` `RowNumber` *\<report item type>* 行グループまたはデータ列のグループを参照できますが、両方を参照することはできません。</span><span class="sxs-lookup"><span data-stu-id="d64be-187">The scope parameters of all `Previous`, `RunningValue` and `RowNumber` aggregate functions within a *\<report item type>* can refer to row groupings or data column groupings, but not both.</span></span>  
  
 <span data-ttu-id="d64be-188">詳細については、「[合計、集計、および組み込みコレクションの式のスコープについて (レポート ビルダー 3.0 および SSRS)](../report-design/expression-scope-for-totals-aggregates-and-built-in-collections.md)」および「[式での組み込みコレクションの使用 (レポート ビルダー 3.0 および SSRS)](../report-design/built-in-collections-in-expressions-report-builder.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d64be-188">For more information, see [Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;](../report-design/expression-scope-for-totals-aggregates-and-built-in-collections.md) and [Built-in Collections in Expressions &#40;Report Builder and SSRS&#41;](../report-design/built-in-collections-in-expressions-report-builder.md).</span></span>  
  
### <a name="default-dataset-scope-for-a-top-level-text-box"></a><span data-ttu-id="d64be-189">最上位レベル テキスト ボックスの既定のデータセット スコープ</span><span class="sxs-lookup"><span data-stu-id="d64be-189">Default Dataset Scope for a Top Level Text Box</span></span>  
 <span data-ttu-id="d64be-190">レポートに複数のデータセットがある場合、レポート デザイン画面に追加したテキスト ボックスの既定のスコープは使用できません。</span><span class="sxs-lookup"><span data-stu-id="d64be-190">Do not use a default scope for a text box added to the report design surface when the report has more than one dataset.</span></span> <span data-ttu-id="d64be-191">スコープとしてデータセットの名前を含む式と、集計関数を使用してください。</span><span class="sxs-lookup"><span data-stu-id="d64be-191">Use an expression that includes the name of the dataset as the scope, and an aggregate function.</span></span> <span data-ttu-id="d64be-192">たとえば、「 `=First(Fields!FieldName.Value, "DataSet2")` 」のように入力します。</span><span class="sxs-lookup"><span data-stu-id="d64be-192">For example, `=First(Fields!FieldName.Value, "DataSet2")`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d64be-193">参照</span><span class="sxs-lookup"><span data-stu-id="d64be-193">See Also</span></span>  
 <span data-ttu-id="d64be-194">[式 &#40;レポート ビルダーおよび SSRS&#41;](../report-design/expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="d64be-194">[Expressions &#40;Report Builder and SSRS&#41;](../report-design/expressions-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="d64be-195">[集計関数リファレンス &#40;レポート ビルダーおよび SSRS&#41;](../report-design/report-builder-functions-aggregate-functions-reference.md) </span><span class="sxs-lookup"><span data-stu-id="d64be-195">[Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](../report-design/report-builder-functions-aggregate-functions-reference.md) </span></span>  
 <span data-ttu-id="d64be-196">[式の例 (レポート ビルダーおよび SSRS)](../report-design/expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="d64be-196">[Expression Examples &#40;Report Builder and SSRS&#41;](../report-design/expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="d64be-197">[レポート &#40;レポートビルダーおよび SSRS&#41;にデータを追加する](../report-data/report-datasets-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="d64be-197">[Add Data to a Report &#40;Report Builder and SSRS&#41;](../report-data/report-datasets-ssrs.md) </span></span>  
 <span data-ttu-id="d64be-198">[一般的に使用されるフィルター &#40;レポート ビルダーおよび SSRS&#41;](../report-design/commonly-used-filters-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="d64be-198">[Commonly Used Filters &#40;Report Builder and SSRS&#41;](../report-design/commonly-used-filters-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="d64be-199">[データセット フィールド コレクション &#40;レポート ビルダーおよび SSRS&#41;](../report-data/dataset-fields-collection-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="d64be-199">[Dataset Fields Collection &#40;Report Builder and SSRS&#41;](../report-data/dataset-fields-collection-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="d64be-200">[レポート デザイナーでカスタム コードやアセンブリを式から参照する (SSRS)](../report-design/custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="d64be-200">[Custom Code and Assembly References in Expressions in Report Designer &#40;SSRS&#41;](../report-design/custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md) </span></span>  
 [<span data-ttu-id="d64be-201">Parameters コレクションの参照 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="d64be-201">Parameters Collection References &#40;Report Builder and SSRS&#41;</span></span>](../report-design/built-in-collections-parameters-collection-references-report-builder.md)  
  
  