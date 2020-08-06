---
title: '[参照変換エディター] ([接続] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.lookuptransformation.referencetable.f1
helpviewer_keywords:
- Lookup Transformation Editor
ms.assetid: e90d6b69-5a26-43c5-8433-5c3c9588e08c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 381378ac1aca85c6bca825033bc439ebc39fb063
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641066"
---
# <a name="lookup-transformation-editor-connection-page"></a><span data-ttu-id="2ae3b-102">[参照変換エディター] ([接続] ページ)</span><span class="sxs-lookup"><span data-stu-id="2ae3b-102">Lookup Transformation Editor (Connection Page)</span></span>
  <span data-ttu-id="2ae3b-103">**[参照変換エディター]** ダイアログ ボックスの **[接続]** ページを使用して、接続マネージャーを選択します。</span><span class="sxs-lookup"><span data-stu-id="2ae3b-103">Use the **Connection** page of the **Lookup Transformation Editor** dialog box to select a connection manager.</span></span> <span data-ttu-id="2ae3b-104">OLE DB 接続マネージャーを選択する場合は、参照データセットを生成するためのクエリ、テーブル、またはビューも選択します。</span><span class="sxs-lookup"><span data-stu-id="2ae3b-104">If you select an OLE DB connection manager, you also select a query, table, or view to generate the reference dataset.</span></span>  
  
 <span data-ttu-id="2ae3b-105">参照変換の詳細については、「 [Lookup Transformation](data-flow/transformations/lookup-transformation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2ae3b-105">To learn more about the Lookup transformation, see [Lookup Transformation](data-flow/transformations/lookup-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="2ae3b-106">Options</span><span class="sxs-lookup"><span data-stu-id="2ae3b-106">Options</span></span>  
 <span data-ttu-id="2ae3b-107">**[参照変換エディター]** ダイアログ ボックスの [全般] ページで **[フル キャッシュ]** および **[キャッシュ接続マネージャー]** を選択すると、次のオプションを使用できます。</span><span class="sxs-lookup"><span data-stu-id="2ae3b-107">The following options are available when you select **Full cache** and **Cache connection manager** on the General page of the **Lookup Transformation Editor** dialog box.</span></span>  
  
 <span data-ttu-id="2ae3b-108">**キャッシュ接続マネージャー**</span><span class="sxs-lookup"><span data-stu-id="2ae3b-108">**Cache connection manager**</span></span>  
 <span data-ttu-id="2ae3b-109">既存のキャッシュ接続マネージャーを一覧から選択するか、 **[新規作成]** をクリックして新しい接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="2ae3b-109">Select an existing Cache connection manager from the list, or create a new connection by clicking **New**.</span></span>  
  
 <span data-ttu-id="2ae3b-110">**[新規作成]**</span><span class="sxs-lookup"><span data-stu-id="2ae3b-110">**New**</span></span>  
 <span data-ttu-id="2ae3b-111">[**キャッシュ接続マネージャーエディター** ] ダイアログボックスを使用して、新しい接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="2ae3b-111">Create a new connection by using the **Cache Connection Manager Editor** dialog box.</span></span>  
  
 <span data-ttu-id="2ae3b-112">**[参照変換エディター]** ダイアログ ボックスの [全般] ページで **[フル キャッシュ]**、 **[部分キャッシュ]**、 **[キャッシュなし]**、および **[OLE DB 接続マネージャー]** を選択すると、次のオプションを使用できます。</span><span class="sxs-lookup"><span data-stu-id="2ae3b-112">The following options are available when you select **Full cache**, **Partial cache**, or **No cache**, and **OLE DB connection manager**, on the General page of the **Lookup Transformation Editor** dialog box.</span></span>  
  
 <span data-ttu-id="2ae3b-113">**[キャッシュなし]**</span><span class="sxs-lookup"><span data-stu-id="2ae3b-113">**OLE DB connection manager**</span></span>  
 <span data-ttu-id="2ae3b-114">一覧から既存の OLE DB 接続マネージャーを選択するか、 **[新規作成]** をクリックして新しい接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="2ae3b-114">Select an existing OLE DB connection manager from the list, or create a new connection by clicking **New**.</span></span>  
  
 <span data-ttu-id="2ae3b-115">**[新規作成]**</span><span class="sxs-lookup"><span data-stu-id="2ae3b-115">**New**</span></span>  
 <span data-ttu-id="2ae3b-116">**[OLE DB 接続マネージャーの構成]** ダイアログ ボックスを使用して、新しい接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="2ae3b-116">Create a new connection by using the **Configure OLE DB Connection Manager** dialog box.</span></span>  
  
 <span data-ttu-id="2ae3b-117">**[テーブルまたはビューを使用する]**</span><span class="sxs-lookup"><span data-stu-id="2ae3b-117">**Use a table or view**</span></span>  
 <span data-ttu-id="2ae3b-118">既存のテーブルまたはビューを一覧から選択するか、[**新規**作成] をクリックして新しいテーブルを作成します。</span><span class="sxs-lookup"><span data-stu-id="2ae3b-118">Select an existing table or view from the list, or create a new table by clicking **New**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2ae3b-119">**[参照変換エディター]** の **[詳細設定]** ページで SQL ステートメントを指定する場合、ここで選択したテーブル名はその SQL ステートメントでオーバーライドおよび置換されます。</span><span class="sxs-lookup"><span data-stu-id="2ae3b-119">If you specify a SQL statement on the **Advanced** page of the **Lookup Transformation Editor**, that SQL statement overrides and replaces the table name selected here.</span></span> <span data-ttu-id="2ae3b-120">詳細については、「 [[参照変換エディター] &#40;[詳細設定] ページ&#41;](../../2014/integration-services/lookup-transformation-editor-advanced-page.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2ae3b-120">For more information, see [Lookup Transformation Editor &#40;Advanced Page&#41;](../../2014/integration-services/lookup-transformation-editor-advanced-page.md).</span></span>  
  
 <span data-ttu-id="2ae3b-121">**[新規作成]**</span><span class="sxs-lookup"><span data-stu-id="2ae3b-121">**New**</span></span>  
 <span data-ttu-id="2ae3b-122">**[テーブルの作成]** ダイアログ ボックスを使用して新しいテーブルを作成します。</span><span class="sxs-lookup"><span data-stu-id="2ae3b-122">Create a new table by using the **Create Table** dialog box.</span></span>  
  
 <span data-ttu-id="2ae3b-123">**[SQL クエリの結果を使用する]**</span><span class="sxs-lookup"><span data-stu-id="2ae3b-123">**Use results of an SQL query**</span></span>  
 <span data-ttu-id="2ae3b-124">既存のクエリの参照、新しいクエリの構築、クエリ構文のチェック、およびクエリ結果のプレビューを行うには、このオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="2ae3b-124">Choose this option to browse to a preexisting query, build a new query, check query syntax, and preview query results.</span></span>  
  
 <span data-ttu-id="2ae3b-125">**[クエリの作成]**</span><span class="sxs-lookup"><span data-stu-id="2ae3b-125">**Build query**</span></span>  
 <span data-ttu-id="2ae3b-126">**[クエリ ビルダー]** を使用して、実行する Transact-SQL ステートメントを作成します。これは、データを参照することによってクエリを作成するグラフィカルなツールです。</span><span class="sxs-lookup"><span data-stu-id="2ae3b-126">Create the Transact-SQL statement to run by using **Query Builder**, a graphical tool that is used to create queries by browsing through data.</span></span>  
  
 <span data-ttu-id="2ae3b-127">**[参照]**</span><span class="sxs-lookup"><span data-stu-id="2ae3b-127">**Browse**</span></span>  
 <span data-ttu-id="2ae3b-128">ファイルとして保存されている既存のクエリを参照します。</span><span class="sxs-lookup"><span data-stu-id="2ae3b-128">Use this option to browse to a preexisting query saved as a file.</span></span>  
  
 <span data-ttu-id="2ae3b-129">**[クエリの解析]**</span><span class="sxs-lookup"><span data-stu-id="2ae3b-129">**Parse Query**</span></span>  
 <span data-ttu-id="2ae3b-130">クエリ構文をチェックします。</span><span class="sxs-lookup"><span data-stu-id="2ae3b-130">Check the syntax of the query.</span></span>  
  
 <span data-ttu-id="2ae3b-131">**プレビュー**</span><span class="sxs-lookup"><span data-stu-id="2ae3b-131">**Preview**</span></span>  
 <span data-ttu-id="2ae3b-132">**[クエリ結果のプレビュー]** ダイアログ ボックスを使用して、結果をプレビューします。</span><span class="sxs-lookup"><span data-stu-id="2ae3b-132">Preview results by using the **Preview Query Results** dialog box.</span></span> <span data-ttu-id="2ae3b-133">結果は 200 行まで表示されます。</span><span class="sxs-lookup"><span data-stu-id="2ae3b-133">This option displays up to 200 rows.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="2ae3b-134">外部リソース</span><span class="sxs-lookup"><span data-stu-id="2ae3b-134">External Resources</span></span>  
 <span data-ttu-id="2ae3b-135">blogs.msdn.com のブログ「 [キャッシュ モードの参照](https://go.microsoft.com/fwlink/?LinkId=219518) 」</span><span class="sxs-lookup"><span data-stu-id="2ae3b-135">Blog entry, [Lookup cache modes](https://go.microsoft.com/fwlink/?LinkId=219518) on blogs.msdn.com</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ae3b-136">参照</span><span class="sxs-lookup"><span data-stu-id="2ae3b-136">See Also</span></span>  
 <span data-ttu-id="2ae3b-137">[[参照変換エディター] &#40;[全般] ページ&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="2ae3b-137">[Lookup Transformation Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="2ae3b-138">[[参照変換エディター] &#40;[列] ページ&#41;](../../2014/integration-services/lookup-transformation-editor-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="2ae3b-138">[Lookup Transformation Editor &#40;Columns Page&#41;](../../2014/integration-services/lookup-transformation-editor-columns-page.md) </span></span>  
 <span data-ttu-id="2ae3b-139">[[参照変換エディター] &#40;[詳細設定] ページ&#41;](../../2014/integration-services/lookup-transformation-editor-advanced-page.md) </span><span class="sxs-lookup"><span data-stu-id="2ae3b-139">[Lookup Transformation Editor &#40;Advanced Page&#41;](../../2014/integration-services/lookup-transformation-editor-advanced-page.md) </span></span>  
 <span data-ttu-id="2ae3b-140">[[参照変換エディター] &#40;エラー出力ページ&#41;](../../2014/integration-services/lookup-transformation-editor-error-output-page.md) </span><span class="sxs-lookup"><span data-stu-id="2ae3b-140">[Lookup Transformation Editor &#40;Error Output Page&#41;](../../2014/integration-services/lookup-transformation-editor-error-output-page.md) </span></span>  
 [<span data-ttu-id="2ae3b-141">あいまい参照変換</span><span class="sxs-lookup"><span data-stu-id="2ae3b-141">Fuzzy Lookup Transformation</span></span>](data-flow/transformations/fuzzy-lookup-transformation.md)  
  
  
