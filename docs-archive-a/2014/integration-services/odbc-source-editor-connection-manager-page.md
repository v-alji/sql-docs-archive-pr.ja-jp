---
title: '[ODBC ソースエディター] ([接続マネージャー] ページ)Microsoft Docs'
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.designer.odbcsource.connection.f1
ms.assetid: e2c8dc83-6394-4d6c-9232-97e94be72431
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c8b54ce4a1c1b3fea0afb51f1cbf7447971ccab4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718566"
---
# <a name="odbc-source-editor-connection-manager-page"></a><span data-ttu-id="cd775-102">[ODBC ソース エディター] ([接続マネージャー] ページ)</span><span class="sxs-lookup"><span data-stu-id="cd775-102">ODBC Source Editor (Connection Manager Page)</span></span>
  <span data-ttu-id="cd775-103">**[ODBC 入力元エディター]** ダイアログ ボックスの **[接続マネージャー]** ページを使用すると、入力元の ODBC 接続マネージャーを選択できます。</span><span class="sxs-lookup"><span data-stu-id="cd775-103">Use the **Connection Manager** page of the **ODBC Source Editor** dialog box to select the ODBC connection manager for the source.</span></span> <span data-ttu-id="cd775-104">さらにこのページを使用して、データベースのテーブルやビューを選択できます。</span><span class="sxs-lookup"><span data-stu-id="cd775-104">This page also lets you select a table or view from the database.</span></span>  
  
 <span data-ttu-id="cd775-105">ODBC 入力元の詳細については、「 [ODBC Source](data-flow/odbc-source.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cd775-105">For more information about the ODBC source, see [ODBC Source](data-flow/odbc-source.md).</span></span>  
  
## <a name="task-list"></a><span data-ttu-id="cd775-106">タスク一覧</span><span class="sxs-lookup"><span data-stu-id="cd775-106">Task List</span></span>  
 <span data-ttu-id="cd775-107">**[ODBC 入力元エディター] の [接続マネージャー] ページを開くには**</span><span class="sxs-lookup"><span data-stu-id="cd775-107">**To open the ODBC Source Editor Connection Manager Page**</span></span>  
  
-   <span data-ttu-id="cd775-108">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]で、ODBC 入力元を含む [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] パッケージを開きます。</span><span class="sxs-lookup"><span data-stu-id="cd775-108">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], open the [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] package that has the ODBC source.</span></span>  
  
-   <span data-ttu-id="cd775-109">**[データ フロー]** タブで、ODBC 入力元をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="cd775-109">On the **Data Flow** tab, double-click the ODBC source.</span></span>  
  
## <a name="options"></a><span data-ttu-id="cd775-110">オプション</span><span class="sxs-lookup"><span data-stu-id="cd775-110">Options</span></span>  
  
### <a name="connection-manager"></a><span data-ttu-id="cd775-111">[ODBC 入力元エディター]</span><span class="sxs-lookup"><span data-stu-id="cd775-111">Connection manager</span></span>  
 <span data-ttu-id="cd775-112">既存の ODBC 接続マネージャーを一覧から選択するか、[**新規**作成] をクリックして新しい接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="cd775-112">Select an existing ODBC connection manager from the list, or click **New** to create a new connection.</span></span> <span data-ttu-id="cd775-113">ODBC でサポートされているデータベースへの接続を選択または入力できます。</span><span class="sxs-lookup"><span data-stu-id="cd775-113">The connection can be to any ODBC-supported database.</span></span>  
  
### <a name="new"></a><span data-ttu-id="cd775-114">新規</span><span class="sxs-lookup"><span data-stu-id="cd775-114">New</span></span>  
 <span data-ttu-id="cd775-115">**[新規作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cd775-115">Click **New**.</span></span> <span data-ttu-id="cd775-116">新しい ODBC 接続マネージャーを作成できる **[ODBC 接続マネージャーの構成エディター]** ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="cd775-116">The **Configure ODBC Connection Manager Editor** dialog box opens where you can create a new ODBC connection manager.</span></span>  
  
### <a name="data-access-mode"></a><span data-ttu-id="cd775-117">[データ アクセス モード]</span><span class="sxs-lookup"><span data-stu-id="cd775-117">Data Access Mode</span></span>  
 <span data-ttu-id="cd775-118">入力元のデータを選択する方法を選択します。</span><span class="sxs-lookup"><span data-stu-id="cd775-118">Select the method for selecting data from the source.</span></span> <span data-ttu-id="cd775-119">次の表に示すオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="cd775-119">The options are shown in the following table:</span></span>  
  
|<span data-ttu-id="cd775-120">オプション</span><span class="sxs-lookup"><span data-stu-id="cd775-120">Option</span></span>|<span data-ttu-id="cd775-121">説明</span><span class="sxs-lookup"><span data-stu-id="cd775-121">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="cd775-122">テーブル名</span><span class="sxs-lookup"><span data-stu-id="cd775-122">Table Name</span></span>|<span data-ttu-id="cd775-123">ODBC データ ソースのテーブルまたはビューからデータを取得します。</span><span class="sxs-lookup"><span data-stu-id="cd775-123">Retrieve data from a table or view in the ODBC data source.</span></span> <span data-ttu-id="cd775-124">このオプションを選択する場合は、以下の一覧から値を選択します。</span><span class="sxs-lookup"><span data-stu-id="cd775-124">When you select this option, select a value from the list for the following:</span></span>|  
||<span data-ttu-id="cd775-125">**[テーブル名またはビュー名]**: 使用できるテーブルまたはビューを一覧から選択するか、正規表現を入力してテーブルを特定します。</span><span class="sxs-lookup"><span data-stu-id="cd775-125">**Name of the table or the view**: Select an available table or view from the list or type a regular expression to identify the table.</span></span>|  
||<span data-ttu-id="cd775-126">この一覧には、最初の 1,000 個のテーブルのみが含まれます。</span><span class="sxs-lookup"><span data-stu-id="cd775-126">This list contains the first 1000 tables only.</span></span> <span data-ttu-id="cd775-127">データベースに 1,000 を超えるテーブルがある場合、テーブル名の最初の文字を入力するか、名前の一部の入力にワイルドカード (\*) を使用すると、目的のテーブルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="cd775-127">If your database contains more than 1000 tables, you can type the beginning of a table name or use the (\*) wild card to enter any part of the name to display the table or tables you want to use.</span></span>|  
|<span data-ttu-id="cd775-128">[SQL コマンド]</span><span class="sxs-lookup"><span data-stu-id="cd775-128">SQL command</span></span>|<span data-ttu-id="cd775-129">SQL クエリを使用して、ODBC データ ソースからデータを取得します。</span><span class="sxs-lookup"><span data-stu-id="cd775-129">Retrieve data from the ODBC data source by using an SQL query.</span></span> <span data-ttu-id="cd775-130">使用しているソース データベースの構文でクエリを記述してください。</span><span class="sxs-lookup"><span data-stu-id="cd775-130">You should write the query in the syntax of the source database you are working with.</span></span> <span data-ttu-id="cd775-131">このオプションを選択する場合は、以下のいずれかの方法でクエリを入力します。</span><span class="sxs-lookup"><span data-stu-id="cd775-131">When you select this option, enter a query in one of the following ways:</span></span>|  
||<span data-ttu-id="cd775-132">**[SQL コマンド テキスト]** フィールドに SQL クエリのテキストを入力します。</span><span class="sxs-lookup"><span data-stu-id="cd775-132">Enter the text of the SQL query in the **SQL command text** field.</span></span>|  
||<span data-ttu-id="cd775-133">**[参照]** をクリックして、テキスト ファイルから SQL クエリを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="cd775-133">Click **Browse** to load the SQL query from a text file.</span></span>|  
||<span data-ttu-id="cd775-134">**[クエリの解析]** をクリックして、クエリ テキストの構文を検証します。</span><span class="sxs-lookup"><span data-stu-id="cd775-134">Click **Parse query** to verify the syntax of the query text.</span></span>|  
  
### <a name="preview"></a><span data-ttu-id="cd775-135">プレビュー</span><span class="sxs-lookup"><span data-stu-id="cd775-135">Preview</span></span>  
 <span data-ttu-id="cd775-136">**[プレビュー]** をクリックすると、選択したテーブルまたはビューから抽出されたデータを先頭から最大で 200 行表示できます。</span><span class="sxs-lookup"><span data-stu-id="cd775-136">Click **Preview** to view up to the first 200 rows of the data extracted from the table or view you selected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd775-137">参照</span><span class="sxs-lookup"><span data-stu-id="cd775-137">See Also</span></span>  
 <span data-ttu-id="cd775-138">[ODBC 入力元のカスタムプロパティ](data-flow/odbc-source-custom-properties.md) </span><span class="sxs-lookup"><span data-stu-id="cd775-138">[ODBC Source Custom Properties](data-flow/odbc-source-custom-properties.md) </span></span>  
 <span data-ttu-id="cd775-139">[ODBC ソースエディターの [列の &#40;] ページ&#41;](../../2014/integration-services/odbc-source-editor-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="cd775-139">[ODBC Source Editor &#40;Columns Page&#41;](../../2014/integration-services/odbc-source-editor-columns-page.md) </span></span>  
 <span data-ttu-id="cd775-140">[[ODBC ソース エディター] &#40;[エラー出力] ページ&#41;](../../2014/integration-services/odbc-source-editor-error-output-page.md)</span><span class="sxs-lookup"><span data-stu-id="cd775-140">[ODBC Source Editor &#40;Error Output Page&#41;](../../2014/integration-services/odbc-source-editor-error-output-page.md)</span></span>  
  
  
