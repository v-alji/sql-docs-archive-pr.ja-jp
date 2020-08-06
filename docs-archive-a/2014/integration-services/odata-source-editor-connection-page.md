---
title: '[OData ソースエディター] ([接続] ページ)Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- Sql12.dts.designer.odatasource.connection.f1
ms.assetid: 20bcd347-4547-4fad-b182-9571030101df
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6ecd0d060ea2197ae7174325b654645fefa23505
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642164"
---
# <a name="odata-source-editor-connection-page"></a><span data-ttu-id="be5a9-102">[OData ソース エディター] ([接続] ページ)</span><span class="sxs-lookup"><span data-stu-id="be5a9-102">OData Source Editor (Connection Page)</span></span>
  <span data-ttu-id="be5a9-103">**[ODBC ソース エディター]** ダイアログ ボックスの **[接続]** ページを使用すると、OData ソースに対応する ODBC 接続マネージャーを選択できます。</span><span class="sxs-lookup"><span data-stu-id="be5a9-103">Use the **Connection** page of the **OData Source Editor** dialog box to select the OData connection manager for the OData source.</span></span> <span data-ttu-id="be5a9-104">また、このページで、コレクションまたはリソースのパスと、どのデータを OData ソースから取得する必要があるかを示すクエリ オプションを指定することができます。</span><span class="sxs-lookup"><span data-stu-id="be5a9-104">This page also lets you specify a collection or a resource path and any query options to indicate what data needs to be retrieved from the OData source.</span></span> <span data-ttu-id="be5a9-105">OData ソースの詳細については、「 [OData ソース](data-flow/odata-source.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="be5a9-105">To learn more about the OData source, see [OData Source](data-flow/odata-source.md).</span></span>  
  
## <a name="static-options"></a><span data-ttu-id="be5a9-106">静的オプション</span><span class="sxs-lookup"><span data-stu-id="be5a9-106">Static Options</span></span>  
 <span data-ttu-id="be5a9-107">**OData 接続マネージャー**</span><span class="sxs-lookup"><span data-stu-id="be5a9-107">**OData connection manager**</span></span>  
 <span data-ttu-id="be5a9-108">既存の接続マネージャーを一覧から選択するか、 **[新規作成]** をクリックして新しい接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="be5a9-108">Select an existing connection manager from the list, or create a new connection by clicking **New**.</span></span>  
  
 <span data-ttu-id="be5a9-109">**[新規作成]**</span><span class="sxs-lookup"><span data-stu-id="be5a9-109">**New**</span></span>  
 <span data-ttu-id="be5a9-110">新しい接続マネージャーを作成するには、 **[OData 接続マネージャー エディター]** ダイアログ ボックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="be5a9-110">Create a new connection manager by using the **OData Connection Manager Editor** dialog box.</span></span>  
  
 <span data-ttu-id="be5a9-111">**コレクションまたはリソースのパスを使用します。**</span><span class="sxs-lookup"><span data-stu-id="be5a9-111">**Use collection or resource path**</span></span>  
 <span data-ttu-id="be5a9-112">ソースからデータを選択する方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="be5a9-112">Specify the method for selecting data from the source.</span></span>  
  
|<span data-ttu-id="be5a9-113">オプション</span><span class="sxs-lookup"><span data-stu-id="be5a9-113">Option</span></span>|<span data-ttu-id="be5a9-114">説明</span><span class="sxs-lookup"><span data-stu-id="be5a9-114">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="be5a9-115">コレクション</span><span class="sxs-lookup"><span data-stu-id="be5a9-115">Collection</span></span>|<span data-ttu-id="be5a9-116">コレクション名を使用して、Odata ソースからデータを取得します。</span><span class="sxs-lookup"><span data-stu-id="be5a9-116">Retrieve data from the OData source by using a collection name.</span></span>|  
|<span data-ttu-id="be5a9-117">リソースのパス</span><span class="sxs-lookup"><span data-stu-id="be5a9-117">Resource Path</span></span>|<span data-ttu-id="be5a9-118">リソースのパスを使用して、Odata ソースからデータを取得します。</span><span class="sxs-lookup"><span data-stu-id="be5a9-118">Retrieve data from the OData source by using a resource path.</span></span>|  
  
 <span data-ttu-id="be5a9-119">**クエリオプション**</span><span class="sxs-lookup"><span data-stu-id="be5a9-119">**Query options**</span></span>  
 <span data-ttu-id="be5a9-120">クエリのオプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="be5a9-120">Specify options for the query.</span></span>  <span data-ttu-id="be5a9-121">例: $top=5</span><span class="sxs-lookup"><span data-stu-id="be5a9-121">For example: $top=5</span></span>  
  
 <span data-ttu-id="be5a9-122">**フィード URL**</span><span class="sxs-lookup"><span data-stu-id="be5a9-122">**Feed url**</span></span>  
 <span data-ttu-id="be5a9-123">このダイアログ ボックスで選択したオプションに基づいて、読み取り専用のフィード URL を表示します。</span><span class="sxs-lookup"><span data-stu-id="be5a9-123">Displays the read-only Feed URL based on options you selected on this dialog box.</span></span>  
  
 <span data-ttu-id="be5a9-124">**プレビュー**</span><span class="sxs-lookup"><span data-stu-id="be5a9-124">**Preview**</span></span>  
 <span data-ttu-id="be5a9-125">**[プレビュー]** ダイアログ ボックスを使用して、結果をプレビューします。</span><span class="sxs-lookup"><span data-stu-id="be5a9-125">Preview results by using the **Preview** dialog box.</span></span> <span data-ttu-id="be5a9-126">**プレビュー** では、最大で 20 行を表示できます。</span><span class="sxs-lookup"><span data-stu-id="be5a9-126">**Preview** can display up to 20 rows.</span></span>  
  
## <a name="dynamic-options"></a><span data-ttu-id="be5a9-127">動的オプション</span><span class="sxs-lookup"><span data-stu-id="be5a9-127">Dynamic Options</span></span>  
  
### <a name="use-collection-or-resource-path--collection"></a><span data-ttu-id="be5a9-128">コレクション、またはリソースのパス = Collection を使用します。</span><span class="sxs-lookup"><span data-stu-id="be5a9-128">Use collection or resource path = Collection</span></span>  
 <span data-ttu-id="be5a9-129">**コレクション**</span><span class="sxs-lookup"><span data-stu-id="be5a9-129">**Collection**</span></span>  
 <span data-ttu-id="be5a9-130">ドロップダウン リストからコレクションを選択します。</span><span class="sxs-lookup"><span data-stu-id="be5a9-130">Select a collection from the drop-down list.</span></span>  
  
### <a name="use-collection-or-resource-path--resource-path"></a><span data-ttu-id="be5a9-131">コレクションまたはリソースのパス = Resource Path を使用します。</span><span class="sxs-lookup"><span data-stu-id="be5a9-131">Use collection or resource path = Resource Path</span></span>  
 <span data-ttu-id="be5a9-132">**リソースパス**</span><span class="sxs-lookup"><span data-stu-id="be5a9-132">**Resource path**</span></span>  
 <span data-ttu-id="be5a9-133">リソースのパスを入力します。</span><span class="sxs-lookup"><span data-stu-id="be5a9-133">Type a resource path.</span></span> <span data-ttu-id="be5a9-134">例: Employees</span><span class="sxs-lookup"><span data-stu-id="be5a9-134">For example: Employees</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be5a9-135">参照</span><span class="sxs-lookup"><span data-stu-id="be5a9-135">See Also</span></span>  
 <span data-ttu-id="be5a9-136">[OData ソースエディター &#40;列のページ&#41;](../../2014/integration-services/odata-source-editor-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="be5a9-136">[OData Source Editor &#40;Columns Page&#41;](../../2014/integration-services/odata-source-editor-columns-page.md) </span></span>  
 <span data-ttu-id="be5a9-137">[OData ソースエディター &#40;エラー出力ページ&#41;](../../2014/integration-services/odata-source-editor-error-output-page.md) </span><span class="sxs-lookup"><span data-stu-id="be5a9-137">[OData Source Editor &#40;Error Output Page&#41;](../../2014/integration-services/odata-source-editor-error-output-page.md) </span></span>  
 [<span data-ttu-id="be5a9-138">OData 接続マネージャー</span><span class="sxs-lookup"><span data-stu-id="be5a9-138">OData Connection Manager</span></span>](connection-manager/odata-connection-manager.md)  
  
  
