---
title: '[Excel 変換先エディター] ([接続マネージャー] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.exceldestadapter.connection.f1
helpviewer_keywords:
- Excel Destination Editor
ms.assetid: fc13f725-963c-488e-91e2-20627133e842
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1556bf713c49aac31f1cc1cd624336f10dbf832f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641774"
---
# <a name="excel-destination-editor-connection-manager-page"></a><span data-ttu-id="59274-102">[Excel 変換先エディター] ([接続マネージャー] ページ)</span><span class="sxs-lookup"><span data-stu-id="59274-102">Excel Destination Editor (Connection Manager Page)</span></span>
  <span data-ttu-id="59274-103">**[Excel 変換先エディター]** ダイアログ ボックスの **[接続マネージャー]** ページを使用すると、データ ソース情報を指定したり、結果をプレビューしたりできます。</span><span class="sxs-lookup"><span data-stu-id="59274-103">Use the **Connection Manager** page of the **Excel Destination Editor** dialog box to specify data source information, and to preview the results.</span></span> <span data-ttu-id="59274-104">Excel 変換先では、 [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] ブックのワークシートまたは名前付き範囲にデータが読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="59274-104">The Excel destination loads data into a worksheet or a named range in a [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] workbook.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="59274-105">Excel 変換 `CommandTimeout` 先のプロパティは、 **Excel 変換先エディター**では使用できませんが、**詳細エディター**を使用して設定できます。</span><span class="sxs-lookup"><span data-stu-id="59274-105">The `CommandTimeout` property of the Excel destination is not available in the **Excel Destination Editor**, but can be set by using the **Advanced Editor**.</span></span> <span data-ttu-id="59274-106">また、特定の高速読み込みオプションは、**詳細エディター**でのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="59274-106">In addition, certain Fast Load options are available only in the **Advanced Editor**.</span></span> <span data-ttu-id="59274-107">これらのプロパティの詳細については、「 [Excel Custom Properties](data-flow/excel-custom-properties.md)」の「Excel 変換先」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="59274-107">For more information on these properties, see the Excel Destination section of [Excel Custom Properties](data-flow/excel-custom-properties.md).</span></span>  
  
 <span data-ttu-id="59274-108">Excel 変換先の詳細については、「 [Excel Destination](data-flow/excel-destination.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="59274-108">To learn more about the Excel destination, see [Excel Destination](data-flow/excel-destination.md).</span></span>  
  
## <a name="static-options"></a><span data-ttu-id="59274-109">静的オプション</span><span class="sxs-lookup"><span data-stu-id="59274-109">Static Options</span></span>  
 <span data-ttu-id="59274-110">**Excel 接続マネージャー**</span><span class="sxs-lookup"><span data-stu-id="59274-110">**Excel connection manager**</span></span>  
 <span data-ttu-id="59274-111">既存の Excel 接続マネージャーを一覧から選択するか、 **[新規作成]** をクリックして新しい接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="59274-111">Select an existing Excel connection manager from the list, or create a new connection by clicking **New**.</span></span>  
  
 <span data-ttu-id="59274-112">**[新規作成]**</span><span class="sxs-lookup"><span data-stu-id="59274-112">**New**</span></span>  
 <span data-ttu-id="59274-113">**[Excel 接続マネージャー]** ダイアログ ボックスを使用して、新しい接続マネージャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="59274-113">Create a new connection manager by using the **Excel Connection Manager** dialog box.</span></span>  
  
 <span data-ttu-id="59274-114">**[データ アクセス モード]**</span><span class="sxs-lookup"><span data-stu-id="59274-114">**Data access mode**</span></span>  
 <span data-ttu-id="59274-115">ソースからデータを選択する方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="59274-115">Specify the method for selecting data from the source.</span></span>  
  
|<span data-ttu-id="59274-116">オプション</span><span class="sxs-lookup"><span data-stu-id="59274-116">Option</span></span>|<span data-ttu-id="59274-117">説明</span><span class="sxs-lookup"><span data-stu-id="59274-117">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="59274-118">[テーブルまたはビュー]</span><span class="sxs-lookup"><span data-stu-id="59274-118">Table or view</span></span>|<span data-ttu-id="59274-119">Excel データ ソースのワークシートまたは名前付き範囲にデータを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="59274-119">Loads data into a worksheet or named range in the Excel data source.</span></span>|  
|<span data-ttu-id="59274-120">[テーブル名またはビュー名の変数]</span><span class="sxs-lookup"><span data-stu-id="59274-120">Table name or view name variable</span></span>|<span data-ttu-id="59274-121">ワークシートまたは範囲の名前を変数に指定します。</span><span class="sxs-lookup"><span data-stu-id="59274-121">Specify the worksheet or range name in a variable.</span></span><br /><br /> <span data-ttu-id="59274-122">**関連情報**: [パッケージで変数を使用する](../../2014/integration-services/use-variables-in-packages.md)</span><span class="sxs-lookup"><span data-stu-id="59274-122">**Related information**: [Use Variables in Packages](../../2014/integration-services/use-variables-in-packages.md)</span></span>|  
|<span data-ttu-id="59274-123">[SQL コマンド]</span><span class="sxs-lookup"><span data-stu-id="59274-123">SQL command</span></span>|<span data-ttu-id="59274-124">SQL クエリを使用して、Excel 変換先にデータを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="59274-124">Load data into the Excel destination by using an SQL query.</span></span>|  
  
 <span data-ttu-id="59274-125">**[Excel シートの名前]**</span><span class="sxs-lookup"><span data-stu-id="59274-125">**Name of the Excel sheet**</span></span>  
 <span data-ttu-id="59274-126">ドロップダウン リストから Excel 変換先を選択します。</span><span class="sxs-lookup"><span data-stu-id="59274-126">Select the excel destination from the drop-down list.</span></span> <span data-ttu-id="59274-127">一覧が空の場合は **[新規]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="59274-127">If the list is empty, click **New**.</span></span>  
  
 <span data-ttu-id="59274-128">**[新規作成]**</span><span class="sxs-lookup"><span data-stu-id="59274-128">**New**</span></span>  
 <span data-ttu-id="59274-129">**[新規]** をクリックすると、 **[テーブルの作成]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="59274-129">Click **New** to launch the **Create Table** dialog box.</span></span> <span data-ttu-id="59274-130">**[OK]** をクリックすると、 **Excel 接続マネージャー** の参照先の Excel ファイルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="59274-130">When you click **OK**, the dialog box creates the excel file that the **Excel Connection Manager** points to.</span></span>  
  
 <span data-ttu-id="59274-131">**[既存のデータを表示]**</span><span class="sxs-lookup"><span data-stu-id="59274-131">**View Existing Data**</span></span>  
 <span data-ttu-id="59274-132">**[クエリ結果のプレビュー]** ダイアログ ボックスを使用して、結果をプレビューします。</span><span class="sxs-lookup"><span data-stu-id="59274-132">Preview results by using the **Preview Query Results** dialog box.</span></span> <span data-ttu-id="59274-133">プレビューでは、最大で 200 行を表示できます。</span><span class="sxs-lookup"><span data-stu-id="59274-133">Preview can display up to 200 rows.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="59274-134"> 選択した **Excel 接続マネージャー** が存在しない Excel ファイルを参照している場合、このボタンをクリックするとエラー メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="59274-134">If the **Excel connection manager** you selected points to an excel file that does not exist, you will see an error message when you click this button.</span></span>  
  
## <a name="data-access-mode-dynamic-options"></a><span data-ttu-id="59274-135">データ アクセス モードの動的オプション</span><span class="sxs-lookup"><span data-stu-id="59274-135">Data Access Mode Dynamic Options</span></span>  
  
### <a name="data-access-mode--table-or-view"></a><span data-ttu-id="59274-136">[データ アクセス モード] = [テーブルまたはビュー]</span><span class="sxs-lookup"><span data-stu-id="59274-136">Data access mode = Table or view</span></span>  
 <span data-ttu-id="59274-137">**[Excel シートの名前]**</span><span class="sxs-lookup"><span data-stu-id="59274-137">**Name of the Excel sheet**</span></span>  
 <span data-ttu-id="59274-138">データ ソースで使用できるワークシートまたは名前付き範囲の名前を一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="59274-138">Select the name of the worksheet or named range from a list of those available in the data source.</span></span>  
  
### <a name="data-access-mode--table-name-or-view-name-variable"></a><span data-ttu-id="59274-139">[データ アクセス モード] = [テーブル名またはビュー名の変数]</span><span class="sxs-lookup"><span data-stu-id="59274-139">Data access mode = Table name or view name variable</span></span>  
 <span data-ttu-id="59274-140">**[変数名]**</span><span class="sxs-lookup"><span data-stu-id="59274-140">**Variable name**</span></span>  
 <span data-ttu-id="59274-141">ワークシートまたは名前付き範囲の名前が含まれている変数を選択します。</span><span class="sxs-lookup"><span data-stu-id="59274-141">Select the variable that contains the name of the worksheet or named range.</span></span>  
  
### <a name="data-access-mode--sql-command"></a><span data-ttu-id="59274-142">[データ アクセス モード] = [SQL コマンド]</span><span class="sxs-lookup"><span data-stu-id="59274-142">Data access mode = SQL command</span></span>  
 <span data-ttu-id="59274-143">**[SQL コマンド テキスト]**</span><span class="sxs-lookup"><span data-stu-id="59274-143">**SQL command text**</span></span>  
 <span data-ttu-id="59274-144">SQL クエリのテキストを入力し、 **[クエリの作成]** をクリックしてクエリを作成します。または、 **[参照]** をクリックし、クエリ テキストが含まれているファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="59274-144">Enter the text of an SQL query, build the query by clicking **Build Query**, or locate the file that contains the query text by clicking **Browse**.</span></span>  
  
 <span data-ttu-id="59274-145">**[クエリの作成]**</span><span class="sxs-lookup"><span data-stu-id="59274-145">**Build Query**</span></span>  
 <span data-ttu-id="59274-146">SQL クエリを視覚的に作成するには、 **[クエリ ビルダー]** ダイアログ ボックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="59274-146">Use the **Query Builder** dialog box to construct the SQL query visually.</span></span>  
  
 <span data-ttu-id="59274-147">**[参照]**</span><span class="sxs-lookup"><span data-stu-id="59274-147">**Browse**</span></span>  
 <span data-ttu-id="59274-148">**[開く]** ダイアログ ボックスを使用して、SQL クエリのテキストが含まれているファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="59274-148">Use the **Open** dialog box to locate the file that contains the text of the SQL query.</span></span>  
  
 <span data-ttu-id="59274-149">**[クエリの解析]**</span><span class="sxs-lookup"><span data-stu-id="59274-149">**Parse Query**</span></span>  
 <span data-ttu-id="59274-150">クエリ テキストの構文を検査します。</span><span class="sxs-lookup"><span data-stu-id="59274-150">Verify the syntax of the query text.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59274-151">参照</span><span class="sxs-lookup"><span data-stu-id="59274-151">See Also</span></span>  
 <span data-ttu-id="59274-152">[Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="59274-152">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="59274-153">[Excel 変換先エディターの [マッピング] ページ&#41;&#40;](../../2014/integration-services/excel-destination-editor-mappings-page.md) </span><span class="sxs-lookup"><span data-stu-id="59274-153">[Excel Destination Editor &#40;Mappings Page&#41;](../../2014/integration-services/excel-destination-editor-mappings-page.md) </span></span>  
 <span data-ttu-id="59274-154">[Excel 変換先エディター &#40;エラー出力ページ&#41;](../../2014/integration-services/excel-destination-editor-error-output-page.md) </span><span class="sxs-lookup"><span data-stu-id="59274-154">[Excel Destination Editor &#40;Error Output Page&#41;](../../2014/integration-services/excel-destination-editor-error-output-page.md) </span></span>  
 [<span data-ttu-id="59274-155">Foreach ループ コンテナーを使用して Excel のファイルおよびテーブルをループ処理する</span><span class="sxs-lookup"><span data-stu-id="59274-155">Loop through Excel Files and Tables by Using a Foreach Loop Container</span></span>](control-flow/foreach-loop-container.md)  
  
  
