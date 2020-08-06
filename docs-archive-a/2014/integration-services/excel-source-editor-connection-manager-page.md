---
title: '[Excel ソースエディター] ([接続マネージャー] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.excelsourceadapter.connection.f1
helpviewer_keywords:
- Excel Source Editor
ms.assetid: 428e04e0-ad98-45d0-8345-12ec1b67b2eb
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3285b5c8b14016b91005af79542e3e2f9b6559b6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641758"
---
# <a name="excel-source-editor-connection-manager-page"></a><span data-ttu-id="950b7-102">[Excel ソース エディター] ([接続マネージャー] ページ)</span><span class="sxs-lookup"><span data-stu-id="950b7-102">Excel Source Editor (Connection Manager Page)</span></span>
  <span data-ttu-id="950b7-103">**[Excel ソース エディター]** ダイアログ ボックスの **[接続マネージャー]** ノードを使用すると、変換元として [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] ブックを選択して使用できます。</span><span class="sxs-lookup"><span data-stu-id="950b7-103">Use the **Connection Manager** node of the **Excel Source Editor** dialog box to select the [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] workbook for the source to use.</span></span> <span data-ttu-id="950b7-104">Excel ソースは、既存のブックのワークシートまたは名前付き範囲からデータを読み取ります。</span><span class="sxs-lookup"><span data-stu-id="950b7-104">The Excel source reads data from a worksheet or named range in an existing workbook.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="950b7-105">Excel ソース `CommandTimeout` のプロパティは、 **Excel ソースエディター**では使用できませんが、**詳細エディター**を使用して設定できます。</span><span class="sxs-lookup"><span data-stu-id="950b7-105">The `CommandTimeout` property of the Excel source is not available in the **Excel Source Editor**, but can be set by using the **Advanced Editor**.</span></span> <span data-ttu-id="950b7-106">このプロパティの詳細については、「 [Excel のカスタム プロパティ](data-flow/excel-custom-properties.md)」 の Excel ソースのセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="950b7-106">For more information on this property, see the Excel Source section of [Excel Custom Properties](data-flow/excel-custom-properties.md).</span></span>  
  
 <span data-ttu-id="950b7-107">Excel ソースの詳細については、「 [Excel Source](data-flow/excel-source.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="950b7-107">To learn more about the Excel source, see [Excel Source](data-flow/excel-source.md).</span></span>  
  
## <a name="static-options"></a><span data-ttu-id="950b7-108">静的オプション</span><span class="sxs-lookup"><span data-stu-id="950b7-108">Static Options</span></span>  
 <span data-ttu-id="950b7-109">**[キャッシュなし]**</span><span class="sxs-lookup"><span data-stu-id="950b7-109">**OLE DB connection manager**</span></span>  
 <span data-ttu-id="950b7-110">既存の Excel 接続マネージャーを一覧から選択するか、 **[新規作成]** をクリックして新しい接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="950b7-110">Select an existing Excel connection manager from the list, or create a new connection by clicking **New**.</span></span>  
  
 <span data-ttu-id="950b7-111">**[新規作成]**</span><span class="sxs-lookup"><span data-stu-id="950b7-111">**New**</span></span>  
 <span data-ttu-id="950b7-112">**[Excel 接続マネージャー]** ダイアログ ボックスを使用して、新しい接続マネージャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="950b7-112">Create a new connection manager by using the **Excel Connection Manager** dialog box.</span></span>  
  
 <span data-ttu-id="950b7-113">**[データ アクセス モード]**</span><span class="sxs-lookup"><span data-stu-id="950b7-113">**Data access mode**</span></span>  
 <span data-ttu-id="950b7-114">ソースからデータを選択する方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="950b7-114">Specify the method for selecting data from the source.</span></span>  
  
|<span data-ttu-id="950b7-115">値</span><span class="sxs-lookup"><span data-stu-id="950b7-115">Value</span></span>|<span data-ttu-id="950b7-116">説明</span><span class="sxs-lookup"><span data-stu-id="950b7-116">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="950b7-117">[テーブルまたはビュー]</span><span class="sxs-lookup"><span data-stu-id="950b7-117">Table or view</span></span>|<span data-ttu-id="950b7-118">Excel ファイルのワークシートまたは名前付き範囲からデータを取得します。</span><span class="sxs-lookup"><span data-stu-id="950b7-118">Retrieve data from a worksheet or named range in the Excel file.</span></span>|  
|<span data-ttu-id="950b7-119">[テーブル名またはビュー名の変数]</span><span class="sxs-lookup"><span data-stu-id="950b7-119">Table name or view name variable</span></span>|<span data-ttu-id="950b7-120">ワークシートまたは範囲の名前を変数に指定します。</span><span class="sxs-lookup"><span data-stu-id="950b7-120">Specify the worksheet or range name in a variable.</span></span><br /><br /> <span data-ttu-id="950b7-121">**関連情報:** [パッケージで変数を使用する](../../2014/integration-services/use-variables-in-packages.md)</span><span class="sxs-lookup"><span data-stu-id="950b7-121">**Related information:** [Use Variables in Packages](../../2014/integration-services/use-variables-in-packages.md)</span></span>|  
|<span data-ttu-id="950b7-122">[SQL コマンド]</span><span class="sxs-lookup"><span data-stu-id="950b7-122">SQL command</span></span>|<span data-ttu-id="950b7-123">SQL クエリを使用して、Excel ファイルからデータを取得します。</span><span class="sxs-lookup"><span data-stu-id="950b7-123">Retrieve data from the Excel file by using a SQL query.</span></span> <span data-ttu-id="950b7-124">クエリ構文の詳細については、「 [Excel ソース](data-flow/excel-source.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="950b7-124">For information about query syntax, see [Excel Source](data-flow/excel-source.md).</span></span>|  
|<span data-ttu-id="950b7-125">[変数からの SQL コマンド]</span><span class="sxs-lookup"><span data-stu-id="950b7-125">SQL command from variable</span></span>|<span data-ttu-id="950b7-126">SQL クエリ テキストを変数で指定します。</span><span class="sxs-lookup"><span data-stu-id="950b7-126">Specify the SQL query text in a variable.</span></span>|  
  
 <span data-ttu-id="950b7-127">**プレビュー**</span><span class="sxs-lookup"><span data-stu-id="950b7-127">**Preview**</span></span>  
 <span data-ttu-id="950b7-128">**[データ ビュー]** ダイアログ ボックスを使用して、結果をプレビューします。</span><span class="sxs-lookup"><span data-stu-id="950b7-128">Preview results by using the **Data View** dialog box.</span></span> <span data-ttu-id="950b7-129">プレビューでは、最大で 200 行を表示できます。</span><span class="sxs-lookup"><span data-stu-id="950b7-129">Preview can display up to 200 rows.</span></span>  
  
## <a name="data-access-mode-dynamic-options"></a><span data-ttu-id="950b7-130">データ アクセス モードの動的オプション</span><span class="sxs-lookup"><span data-stu-id="950b7-130">Data Access Mode Dynamic Options</span></span>  
  
### <a name="data-access-mode--table-or-view"></a><span data-ttu-id="950b7-131">[データ アクセス モード] = [テーブルまたはビュー]</span><span class="sxs-lookup"><span data-stu-id="950b7-131">Data access mode = Table or view</span></span>  
 <span data-ttu-id="950b7-132">**[Excel シートの名前]**</span><span class="sxs-lookup"><span data-stu-id="950b7-132">**Name of the Excel sheet**</span></span>  
 <span data-ttu-id="950b7-133">Excel ブックで使用できるワークシートまたは名前付き範囲の名前を一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="950b7-133">Select the name of the worksheet or named range from a list of those available in the Excel workbook.</span></span>  
  
### <a name="data-access-mode--table-name-or-view-name-variable"></a><span data-ttu-id="950b7-134">[データ アクセス モード] = [テーブル名またはビュー名の変数]</span><span class="sxs-lookup"><span data-stu-id="950b7-134">Data access mode = Table name or view name variable</span></span>  
 <span data-ttu-id="950b7-135">**[変数名]**</span><span class="sxs-lookup"><span data-stu-id="950b7-135">**Variable name**</span></span>  
 <span data-ttu-id="950b7-136">ワークシートまたは名前付き範囲の名前が含まれている変数を選択します。</span><span class="sxs-lookup"><span data-stu-id="950b7-136">Select the variable that contains the name of the worksheet or named range.</span></span>  
  
### <a name="data-access-mode--sql-command"></a><span data-ttu-id="950b7-137">[データ アクセス モード] = [SQL コマンド]</span><span class="sxs-lookup"><span data-stu-id="950b7-137">Data access mode = SQL command</span></span>  
 <span data-ttu-id="950b7-138">**[SQL コマンド テキスト]**</span><span class="sxs-lookup"><span data-stu-id="950b7-138">**SQL command text**</span></span>  
 <span data-ttu-id="950b7-139">SQL クエリのテキストを入力し、 **[クエリの作成]** をクリックしてクエリを作成します。または、 **[参照]** をクリックし、クエリ テキストが含まれているファイルを参照します。</span><span class="sxs-lookup"><span data-stu-id="950b7-139">Enter the text of a SQL query, build the query by clicking **Build Query**, or browse to the file that contains the query text by clicking **Browse**.</span></span>  
  
 <span data-ttu-id="950b7-140">**パラメーター**</span><span class="sxs-lookup"><span data-stu-id="950b7-140">**Parameters**</span></span>  
 <span data-ttu-id="950b7-141">クエリ テキスト内でパラメーターのプレースホルダーとして "?" を使用することにより、</span><span class="sxs-lookup"><span data-stu-id="950b7-141">If you have entered a parameterized query by using ?</span></span> <span data-ttu-id="950b7-142">パラメーター化クエリを入力した場合は、 **[クエリ パラメーターの設定]** ダイアログ ボックスを使用して、クエリ入力パラメーターをパッケージ変数にマップします。</span><span class="sxs-lookup"><span data-stu-id="950b7-142">as a parameter placeholder in the query text, use the **Set Query Parameters** dialog box to map query input parameters to package variables.</span></span>  
  
 <span data-ttu-id="950b7-143">**[クエリの作成]**</span><span class="sxs-lookup"><span data-stu-id="950b7-143">**Build query**</span></span>  
 <span data-ttu-id="950b7-144">SQL クエリを視覚的に作成するには、 **[クエリ ビルダー]** ダイアログ ボックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="950b7-144">Use the **Query Builder** dialog box to construct the SQL query visually.</span></span>  
  
 <span data-ttu-id="950b7-145">**[参照]**</span><span class="sxs-lookup"><span data-stu-id="950b7-145">**Browse**</span></span>  
 <span data-ttu-id="950b7-146">**[開く]** ダイアログ ボックスを使用して、SQL クエリのテキストが含まれているファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="950b7-146">Use the **Open** dialog box to locate the file that contains the text of the SQL query.</span></span>  
  
 <span data-ttu-id="950b7-147">**[クエリの解析]**</span><span class="sxs-lookup"><span data-stu-id="950b7-147">**Parse query**</span></span>  
 <span data-ttu-id="950b7-148">クエリ テキストの構文を検査します。</span><span class="sxs-lookup"><span data-stu-id="950b7-148">Verify the syntax of the query text.</span></span>  
  
### <a name="data-access-mode--sql-command-from-variable"></a><span data-ttu-id="950b7-149">データ アクセス モードが [変数からの SQL コマンド] の場合</span><span class="sxs-lookup"><span data-stu-id="950b7-149">Data access mode = SQL command from variable</span></span>  
 <span data-ttu-id="950b7-150">**[変数名]**</span><span class="sxs-lookup"><span data-stu-id="950b7-150">**Variable name**</span></span>  
 <span data-ttu-id="950b7-151">SQL クエリのテキストを含む変数を選択します。</span><span class="sxs-lookup"><span data-stu-id="950b7-151">Select the variable that contains the text of the SQL query.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="950b7-152">参照</span><span class="sxs-lookup"><span data-stu-id="950b7-152">See Also</span></span>  
 <span data-ttu-id="950b7-153">[Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="950b7-153">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="950b7-154">[Excel ソースエディター &#40;[列] ページ&#41;](../../2014/integration-services/excel-source-editor-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="950b7-154">[Excel Source Editor &#40;Columns Page&#41;](../../2014/integration-services/excel-source-editor-columns-page.md) </span></span>  
 <span data-ttu-id="950b7-155">[Excel ソースエディター &#40;エラー出力ページ&#41;](../../2014/integration-services/excel-source-editor-error-output-page.md) </span><span class="sxs-lookup"><span data-stu-id="950b7-155">[Excel Source Editor &#40;Error Output Page&#41;](../../2014/integration-services/excel-source-editor-error-output-page.md) </span></span>  
 <span data-ttu-id="950b7-156">[Excel 接続マネージャー](connection-manager/excel-connection-manager.md) </span><span class="sxs-lookup"><span data-stu-id="950b7-156">[Excel Connection Manager](connection-manager/excel-connection-manager.md) </span></span>  
 [<span data-ttu-id="950b7-157">Foreach ループ コンテナーを使用して Excel のファイルおよびテーブルをループ処理する</span><span class="sxs-lookup"><span data-stu-id="950b7-157">Loop through Excel Files and Tables by Using a Foreach Loop Container</span></span>](control-flow/foreach-loop-container.md)  
  
  
