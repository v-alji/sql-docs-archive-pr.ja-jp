---
title: '[ADO NET 変換元エディター] ([接続マネージャー] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.adonetsource.connection.f1
ms.assetid: 7de3f438-bdd6-49b5-937a-47369e754943
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 19dd9c256f15bc9022f7267cb38b6f91bd4d8a5c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736684"
---
# <a name="ado-net-source-editor-connection-manager-page"></a><span data-ttu-id="7ccf3-102">[ADO NET 変換元エディター] ([接続マネージャー] ページ)</span><span class="sxs-lookup"><span data-stu-id="7ccf3-102">ADO NET Source Editor (Connection Manager Page)</span></span>
  <span data-ttu-id="7ccf3-103">**[ADO NET 変換元エディター]** ダイアログ ボックスの **[接続マネージャー]** ページを使用すると、変換元の [!INCLUDE[vstecado](../includes/vstecado-md.md)] 接続マネージャーを選択できます。</span><span class="sxs-lookup"><span data-stu-id="7ccf3-103">Use the **Connection Manager** page of the **ADO NET Source Editor** dialog box to select the [!INCLUDE[vstecado](../includes/vstecado-md.md)] connection manager for the source.</span></span> <span data-ttu-id="7ccf3-104">さらにこのページを使用して、データベースのテーブルやビューを選択できます。</span><span class="sxs-lookup"><span data-stu-id="7ccf3-104">This page also lets you select a table or view from the database.</span></span>  
  
 <span data-ttu-id="7ccf3-105">ADO NET 変換元の詳細については、「 [ADO NET Source](data-flow/ado-net-source.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7ccf3-105">To learn more about the ADO NET source, see [ADO NET Source](data-flow/ado-net-source.md).</span></span>  
  
 <span data-ttu-id="7ccf3-106">**[接続マネージャー] ページを開くには**</span><span class="sxs-lookup"><span data-stu-id="7ccf3-106">**To open the Connection Manager page**</span></span>  
  
1.  <span data-ttu-id="7ccf3-107">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で、ADO NET 変換元を含む [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] パッケージを開きます。</span><span class="sxs-lookup"><span data-stu-id="7ccf3-107">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package that has the ADO NET source.</span></span>  
  
2.  <span data-ttu-id="7ccf3-108">**[データ フロー]** タブで、ADO NET 変換元をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="7ccf3-108">On the **Data Flow** tab, double-click the ADO NET source.</span></span>  
  
3.  <span data-ttu-id="7ccf3-109">**[ADO NET 変換元エディター]** で、 **[接続マネージャー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7ccf3-109">In the **ADO NET Source Editor**, click **Connection Manager**.</span></span>  
  
## <a name="static-options"></a><span data-ttu-id="7ccf3-110">静的オプション</span><span class="sxs-lookup"><span data-stu-id="7ccf3-110">Static Options</span></span>  
 <span data-ttu-id="7ccf3-111">**ADO.NET 接続マネージャー**</span><span class="sxs-lookup"><span data-stu-id="7ccf3-111">**ADO.NET connection manager**</span></span>  
 <span data-ttu-id="7ccf3-112">既存の接続マネージャーを一覧から選択するか、 **[新規作成]** をクリックして新しい接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="7ccf3-112">Select an existing connection manager from the list, or create a new connection by clicking **New**.</span></span>  
  
 <span data-ttu-id="7ccf3-113">**[新規作成]**</span><span class="sxs-lookup"><span data-stu-id="7ccf3-113">**New**</span></span>  
 <span data-ttu-id="7ccf3-114">**[ADO.NET の接続マネージャーの構成]** ダイアログ ボックスを使用して、新しい接続マネージャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="7ccf3-114">Create a new connection manager by using the **Configure ADO.NET Connection Manager** dialog box.</span></span>  
  
 <span data-ttu-id="7ccf3-115">**[データ アクセス モード]**</span><span class="sxs-lookup"><span data-stu-id="7ccf3-115">**Data access mode**</span></span>  
 <span data-ttu-id="7ccf3-116">ソースからデータを選択する方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="7ccf3-116">Specify the method for selecting data from the source.</span></span>  
  
|<span data-ttu-id="7ccf3-117">オプション</span><span class="sxs-lookup"><span data-stu-id="7ccf3-117">Option</span></span>|<span data-ttu-id="7ccf3-118">説明</span><span class="sxs-lookup"><span data-stu-id="7ccf3-118">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="7ccf3-119">[テーブルまたはビュー]</span><span class="sxs-lookup"><span data-stu-id="7ccf3-119">Table or view</span></span>|<span data-ttu-id="7ccf3-120">[!INCLUDE[vstecado](../includes/vstecado-md.md)] データ ソースのテーブルまたはビューからデータを取得します。</span><span class="sxs-lookup"><span data-stu-id="7ccf3-120">Retrieve data from a table or view in the [!INCLUDE[vstecado](../includes/vstecado-md.md)] data source.</span></span>|  
|<span data-ttu-id="7ccf3-121">[SQL コマンド]</span><span class="sxs-lookup"><span data-stu-id="7ccf3-121">SQL command</span></span>|<span data-ttu-id="7ccf3-122">SQL クエリを使用して、 [!INCLUDE[vstecado](../includes/vstecado-md.md)] データ ソースからデータを取得します。</span><span class="sxs-lookup"><span data-stu-id="7ccf3-122">Retrieve data from the [!INCLUDE[vstecado](../includes/vstecado-md.md)] data source by using a SQL query.</span></span>|  
  
 <span data-ttu-id="7ccf3-123">**プレビュー**</span><span class="sxs-lookup"><span data-stu-id="7ccf3-123">**Preview**</span></span>  
 <span data-ttu-id="7ccf3-124">**[データ ビュー]** ダイアログ ボックスを使用して、結果をプレビューします。</span><span class="sxs-lookup"><span data-stu-id="7ccf3-124">Preview results by using the **Data View** dialog box.</span></span> <span data-ttu-id="7ccf3-125">**プレビュー** では、最大で 200 行を表示できます。</span><span class="sxs-lookup"><span data-stu-id="7ccf3-125">**Preview** can display up to 200 rows.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7ccf3-126">データをプレビューするときに、CLR ユーザー定義型を含む列にはデータが表示されません。</span><span class="sxs-lookup"><span data-stu-id="7ccf3-126">When you preview data, columns with a CLR user-defined type do not contain data.</span></span> <span data-ttu-id="7ccf3-127">その代わりに、\<value too big to display> または System.Byte[] が値として表示されます。</span><span class="sxs-lookup"><span data-stu-id="7ccf3-127">Instead the values \<value too big to display> or System.Byte[] display.</span></span> <span data-ttu-id="7ccf3-128">前者は、 [!INCLUDE[vstecado](../includes/vstecado-md.md)] プロバイダーを使用してデータ ソースにアクセスする場合に表示されます。後者は、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Native Client プロバイダーを使用している場合に表示されます。</span><span class="sxs-lookup"><span data-stu-id="7ccf3-128">The former displays when the data source is accessed by using the [!INCLUDE[vstecado](../includes/vstecado-md.md)] provider, the latter when using the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Native Client provider.</span></span>  
  
## <a name="data-access-mode-dynamic-options"></a><span data-ttu-id="7ccf3-129">データ アクセス モードの動的オプション</span><span class="sxs-lookup"><span data-stu-id="7ccf3-129">Data Access Mode Dynamic Options</span></span>  
  
### <a name="data-access-mode--table-or-view"></a><span data-ttu-id="7ccf3-130">[データ アクセス モード] = [テーブルまたはビュー]</span><span class="sxs-lookup"><span data-stu-id="7ccf3-130">Data access mode = Table or view</span></span>  
 <span data-ttu-id="7ccf3-131">**[テーブル名またはビュー名]**</span><span class="sxs-lookup"><span data-stu-id="7ccf3-131">**Name of the table or the view**</span></span>  
 <span data-ttu-id="7ccf3-132">データ ソースで使用できるテーブルまたはビューの一覧から、テーブルまたはビューの名前を選択します。</span><span class="sxs-lookup"><span data-stu-id="7ccf3-132">Select the name of the table or view from a list of those available in the data source.</span></span>  
  
### <a name="data-access-mode--sql-command"></a><span data-ttu-id="7ccf3-133">[データ アクセス モード] = [SQL コマンド]</span><span class="sxs-lookup"><span data-stu-id="7ccf3-133">Data access mode = SQL command</span></span>  
 <span data-ttu-id="7ccf3-134">**[SQL コマンド テキスト]**</span><span class="sxs-lookup"><span data-stu-id="7ccf3-134">**SQL command text**</span></span>  
 <span data-ttu-id="7ccf3-135">SQL クエリのテキストを入力し、 **[クエリの作成]** をクリックしてクエリを作成するか、 **[参照]** をクリックしてクエリ テキストを含むファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="7ccf3-135">Enter the text of a SQL query, build the query by clicking **Build Query**, or locate the file that contains the query text by clicking **Browse**.</span></span>  
  
 <span data-ttu-id="7ccf3-136">**[クエリの作成]**</span><span class="sxs-lookup"><span data-stu-id="7ccf3-136">**Build query**</span></span>  
 <span data-ttu-id="7ccf3-137">SQL クエリを視覚的に作成するには、 **[クエリ ビルダー]** ダイアログ ボックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="7ccf3-137">Use the **Query Builder** dialog box to construct the SQL query visually.</span></span>  
  
 <span data-ttu-id="7ccf3-138">**[参照]**</span><span class="sxs-lookup"><span data-stu-id="7ccf3-138">**Browse**</span></span>  
 <span data-ttu-id="7ccf3-139">**[開く]** ダイアログ ボックスを使用して、SQL クエリのテキストが含まれているファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="7ccf3-139">Use the **Open** dialog box to locate the file that contains the text of the SQL query.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ccf3-140">参照</span><span class="sxs-lookup"><span data-stu-id="7ccf3-140">See Also</span></span>  
 <span data-ttu-id="7ccf3-141">[[ADO NET 変換元エディター] &#40;[列] ページ&#41;](../../2014/integration-services/ado-net-source-editor-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="7ccf3-141">[ADO NET Source Editor &#40;Columns Page&#41;](../../2014/integration-services/ado-net-source-editor-columns-page.md) </span></span>  
 <span data-ttu-id="7ccf3-142">[ADO NET 変換元エディター &#40;エラー出力ページ&#41;](../../2014/integration-services/ado-net-source-editor-error-output-page.md) </span><span class="sxs-lookup"><span data-stu-id="7ccf3-142">[ADO NET Source Editor &#40;Error Output Page&#41;](../../2014/integration-services/ado-net-source-editor-error-output-page.md) </span></span>  
 [<span data-ttu-id="7ccf3-143">ADO.NET 接続マネージャー</span><span class="sxs-lookup"><span data-stu-id="7ccf3-143">ADO.NET Connection Manager</span></span>](connection-manager/ado-net-connection-manager.md)  
  
  
