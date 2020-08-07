---
title: '[ODBC 変換先エディター] ([接続マネージャー] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.designer.odbcdest.connection.f1
ms.assetid: f6d9c6c2-e4c4-468b-9e0d-af7b9609614d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6e4fc1073bb187c0864d2991459a358a7f81d066
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718584"
---
# <a name="odbc-destination-editor-connection-manager-page"></a><span data-ttu-id="1dee3-102">[ODBC 変換先エディター]\([接続マネージャー] ページ)</span><span class="sxs-lookup"><span data-stu-id="1dee3-102">ODBC Destination Editor (Connection Manager Page)</span></span>
  <span data-ttu-id="1dee3-103">**[ODBC 入力先エディター]** ダイアログ ボックスの **[接続マネージャー]** ページを使用すると、入力先の ODBC 接続マネージャーを選択できます。</span><span class="sxs-lookup"><span data-stu-id="1dee3-103">Use the **Connection Manager** page of the **ODBC Destination Editor** dialog box to select the ODBC connection manager for the destination.</span></span> <span data-ttu-id="1dee3-104">さらにこのページを使用して、データベースのテーブルやビューを選択できます。</span><span class="sxs-lookup"><span data-stu-id="1dee3-104">This page also lets you select a table or view from the database</span></span>  
  
 <span data-ttu-id="1dee3-105">ODBC 入力先の詳細については、「 [ODBC Destination](data-flow/odbc-destination.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1dee3-105">For more information about the ODBC destination, see [ODBC Destination](data-flow/odbc-destination.md).</span></span>  
  
 <span data-ttu-id="1dee3-106">**[ODBC 入力先エディター] の [接続マネージャー] ページを開くには**</span><span class="sxs-lookup"><span data-stu-id="1dee3-106">**To open the ODBC Destination Editor Connection Manager Page**</span></span>  
  
## <a name="task-list"></a><span data-ttu-id="1dee3-107">タスク一覧</span><span class="sxs-lookup"><span data-stu-id="1dee3-107">Task List</span></span>  
  
-   <span data-ttu-id="1dee3-108">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]で、ODBC 入力先を含む [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] パッケージを開きます。</span><span class="sxs-lookup"><span data-stu-id="1dee3-108">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], open the [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] package that has the ODBC destination.</span></span>  
  
-   <span data-ttu-id="1dee3-109">**[データ フロー]** タブで、ODBC 入力先をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="1dee3-109">On the **Data Flow** tab, double-click the ODBC destination.</span></span>  
  
-   <span data-ttu-id="1dee3-110">**[ODBC 入力先エディター]** で、 **[接続マネージャー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1dee3-110">In the **ODBC Destination Editor**, click **Connection Manager**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="1dee3-111">オプション</span><span class="sxs-lookup"><span data-stu-id="1dee3-111">Options</span></span>  
  
### <a name="connection-manager"></a><span data-ttu-id="1dee3-112">[ODBC 入力元エディター]</span><span class="sxs-lookup"><span data-stu-id="1dee3-112">Connection manager</span></span>  
 <span data-ttu-id="1dee3-113">既存の ODBC 接続マネージャーを一覧から選択するか、[新規作成] をクリックして新しい接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="1dee3-113">Select an existing ODBC connection manager from the list, or click New to create a new connection.</span></span> <span data-ttu-id="1dee3-114">ODBC でサポートされているデータベースへの接続を選択または入力できます。</span><span class="sxs-lookup"><span data-stu-id="1dee3-114">The connection can be to any ODBC-supported database.</span></span>  
  
### <a name="new"></a><span data-ttu-id="1dee3-115">新規</span><span class="sxs-lookup"><span data-stu-id="1dee3-115">New</span></span>  
 <span data-ttu-id="1dee3-116">**[新規作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1dee3-116">Click **New**.</span></span> <span data-ttu-id="1dee3-117">新しい接続マネージャーを作成できる **[ODBC 接続マネージャーの構成エディター]** ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="1dee3-117">The **Configure ODBC Connection Manager Editor** dialog box opens where you can create a new connection manager.</span></span>  
  
### <a name="data-access-mode"></a><span data-ttu-id="1dee3-118">[データ アクセス モード]</span><span class="sxs-lookup"><span data-stu-id="1dee3-118">Data Access Mode</span></span>  
 <span data-ttu-id="1dee3-119">データを入力先に読み込む方法を選択します。</span><span class="sxs-lookup"><span data-stu-id="1dee3-119">Select the method for loading data to the destination.</span></span> <span data-ttu-id="1dee3-120">次の表に示すオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="1dee3-120">The options are shown in the following table:</span></span>  
  
|<span data-ttu-id="1dee3-121">オプション</span><span class="sxs-lookup"><span data-stu-id="1dee3-121">Option</span></span>|<span data-ttu-id="1dee3-122">説明</span><span class="sxs-lookup"><span data-stu-id="1dee3-122">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="1dee3-123">[テーブル名 - バッチ]</span><span class="sxs-lookup"><span data-stu-id="1dee3-123">Table Name - Batch</span></span>|<span data-ttu-id="1dee3-124">バッチ モードで動作する ODBC 入力先を構成するには、このオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="1dee3-124">Select this option to configure the ODBC destination to work in batch mode.</span></span> <span data-ttu-id="1dee3-125">このオプションを選択した場合は、次のオプションを指定できます。</span><span class="sxs-lookup"><span data-stu-id="1dee3-125">When you select this option the following options are available:</span></span>|  
||<span data-ttu-id="1dee3-126">**[テーブル名またはビュー名]** : 使用できるテーブルまたはビューを一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="1dee3-126">**Name of the table or the view**: Select an available table or view from the list.</span></span><br /><br /> <span data-ttu-id="1dee3-127">この一覧には、最初の 1,000 個のテーブルのみが含まれます。</span><span class="sxs-lookup"><span data-stu-id="1dee3-127">This list contains the first 1000 tables only.</span></span> <span data-ttu-id="1dee3-128">データベースに 1,000 を超えるテーブルがある場合、テーブル名の最初の文字を入力するか、名前の一部の入力にワイルドカード (\*) を使用すると、目的のテーブルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="1dee3-128">If your database contains more than 1000 tables, you can type the beginning of a table name or use the (\*) wild card to enter any part of the name to display the table or tables you want to use.</span></span><br /><br /> <span data-ttu-id="1dee3-129">**[バッチ サイズ]** : 一括読み込みのバッチのサイズを入力します。</span><span class="sxs-lookup"><span data-stu-id="1dee3-129">**Batch size**: Type the size of the batch for bulk loading.</span></span> <span data-ttu-id="1dee3-130">これは、バッチとして読み込まれる行数です。</span><span class="sxs-lookup"><span data-stu-id="1dee3-130">This is the number of rows loaded as a batch</span></span>|  
|<span data-ttu-id="1dee3-131">[テーブル名 - 行ごと]</span><span class="sxs-lookup"><span data-stu-id="1dee3-131">Table Name - Row by Row</span></span>|<span data-ttu-id="1dee3-132">一度に 1 行ずつ、入力先テーブルに各行を挿入するように ODBC 入力先を構成するには、このオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="1dee3-132">Select this option to configure the ODBC destination to insert each of the rows into the destination table one at a time.</span></span> <span data-ttu-id="1dee3-133">このオプションを選択した場合は、次のオプションを指定できます。</span><span class="sxs-lookup"><span data-stu-id="1dee3-133">When you select this option the following option is available:</span></span>|  
||<span data-ttu-id="1dee3-134">**[テーブル名またはビュー名]** : 使用できるテーブルまたはビューを一覧のデータベースから選択します。</span><span class="sxs-lookup"><span data-stu-id="1dee3-134">**Name of the table or the view**: Select an available table or view from the database from the list.</span></span><br /><br /> <span data-ttu-id="1dee3-135">この一覧には、最初の 1,000 個のテーブルのみが含まれます。</span><span class="sxs-lookup"><span data-stu-id="1dee3-135">This list contains the first 1000 tables only.</span></span> <span data-ttu-id="1dee3-136">データベースに 1,000 を超えるテーブルがある場合、テーブル名の最初の文字を入力するか、名前の一部の入力にワイルドカード (\*) を使用すると、目的のテーブルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="1dee3-136">If your database contains more than 1000 tables, you can type the beginning of a table name or use the (\*) wild card to enter any part of the name to display the table or tables you want to use.</span></span>|  
  
### <a name="preview"></a><span data-ttu-id="1dee3-137">プレビュー</span><span class="sxs-lookup"><span data-stu-id="1dee3-137">Preview</span></span>  
 <span data-ttu-id="1dee3-138">**[プレビュー]** をクリックすると、選択したテーブルのデータが最大で 200 行表示されます。</span><span class="sxs-lookup"><span data-stu-id="1dee3-138">Click **Preview** to view up to 200 rows of data for the table that you selected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1dee3-139">参照</span><span class="sxs-lookup"><span data-stu-id="1dee3-139">See Also</span></span>  
 <span data-ttu-id="1dee3-140">[ODBC 入力先のカスタムプロパティ](data-flow/odbc-destination-custom-properties.md) </span><span class="sxs-lookup"><span data-stu-id="1dee3-140">[ODBC Destination Custom Properties](data-flow/odbc-destination-custom-properties.md) </span></span>  
 <span data-ttu-id="1dee3-141">[ODBC 変換先エディター &#40;マッピングページ&#41;](../../2014/integration-services/odbc-destination-editor-mappings-page.md) </span><span class="sxs-lookup"><span data-stu-id="1dee3-141">[ODBC Destination Editor &#40;Mappings Page&#41;](../../2014/integration-services/odbc-destination-editor-mappings-page.md) </span></span>  
 <span data-ttu-id="1dee3-142">[ODBC 変換先エディター &#40;[エラー出力] ページ&#41;](../../2014/integration-services/odbc-destination-editor-error-output-page.md)</span><span class="sxs-lookup"><span data-stu-id="1dee3-142">[ODBC Destination Editor &#40;Error Output Page&#41;](../../2014/integration-services/odbc-destination-editor-error-output-page.md)</span></span>  
  
  
