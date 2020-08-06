---
title: クエリビルダー (レポートウィザード) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.dataview.vdtquerydesigner.f1
- sql12.rtp.rptwizard.querybuilder.f1
helpviewer_keywords:
- Query Builder [Reporting Services]
ms.assetid: 1b0904ea-28c1-448e-b56c-c0fdfbc8b222
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 34369bc72fadae75afbc93eb03c0e40509dd27a4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631626"
---
# <a name="query-builder-report-wizard"></a><span data-ttu-id="c4024-102">クエリ ビルダー (レポート ウィザード)</span><span class="sxs-lookup"><span data-stu-id="c4024-102">Query Builder (Report Wizard)</span></span>
  <span data-ttu-id="c4024-103">クエリ ビルダーを使用すると、レポートで使用する結果セットを取得するためのクエリを指定できます。</span><span class="sxs-lookup"><span data-stu-id="c4024-103">Use the Query Builder to specify a query that retrieves a result set to use in a report.</span></span> <span data-ttu-id="c4024-104">2 種類のクエリ ビルダーを選択できます。</span><span class="sxs-lookup"><span data-stu-id="c4024-104">You can choose between two query builders:</span></span>  
  
-   <span data-ttu-id="c4024-105">テキスト ベースのクエリ ビルダー (既定) は、クエリを指定して結果を表示するための単純なワークスペースを備えています。</span><span class="sxs-lookup"><span data-stu-id="c4024-105">The text-based query builder (default) provides a simple workspace for specifying a query and viewing the results.</span></span> <span data-ttu-id="c4024-106">複数の [!INCLUDE[tsql](../includes/tsql-md.md)] ステートメント、カスタム データ処理拡張機能のクエリまたはコマンド構文、および式としてのクエリを指定できます。</span><span class="sxs-lookup"><span data-stu-id="c4024-106">You can specify multiple [!INCLUDE[tsql](../includes/tsql-md.md)] statements, query or command syntax for custom data processing extensions, and queries that are specified as expressions.</span></span> <span data-ttu-id="c4024-107">汎用クエリ ビルダーはクエリを前処理せず、どんな種類のクエリ構文にも対応するので、レポート デザイナーの既定のクエリ ビルダー ツールとして設定されています。</span><span class="sxs-lookup"><span data-stu-id="c4024-107">Because the generic query builder does not preprocess the query and can accommodate any kind of query syntax, it is the default query builder tool for Report Designer.</span></span>  
  
-   <span data-ttu-id="c4024-108">グラフィカル クエリ ビルダーでは、より視覚的な操作が可能です。</span><span class="sxs-lookup"><span data-stu-id="c4024-108">The graphical query builder provides a richer visual experience.</span></span> <span data-ttu-id="c4024-109">これは、 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] と [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]の他の部分で使用されます。</span><span class="sxs-lookup"><span data-stu-id="c4024-109">It is used in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] and in other parts of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="c4024-110">式を作成しない場合や、複数の要素で構成される SQL ステートメントを作成しない場合に、グラフィカル クエリ ビルダーを使用できます。</span><span class="sxs-lookup"><span data-stu-id="c4024-110">You can use the graphical query builder if you are not creating expressions or multi-part SQL statements.</span></span>  
  
     <span data-ttu-id="c4024-111">グラフィカル クエリ ビルダーに切り替えるには、ウィンドウの左上隅にある **[テキストとして編集]** ボタンを切り替えます。</span><span class="sxs-lookup"><span data-stu-id="c4024-111">To switch to the graphical query builder, toggle the **Edit As Text** button in the top left corner of the window.</span></span>  
  
 <span data-ttu-id="c4024-112">別のレポートからクエリをインポートすることもできます。</span><span class="sxs-lookup"><span data-stu-id="c4024-112">You can also import a query from another report.</span></span>  
  
## <a name="query-builder-options"></a><span data-ttu-id="c4024-113">クエリ ビルダーのオプション</span><span class="sxs-lookup"><span data-stu-id="c4024-113">Query Builder Options</span></span>  
 <span data-ttu-id="c4024-114">**[テキストとして編集]**</span><span class="sxs-lookup"><span data-stu-id="c4024-114">**Edit As Text**</span></span>  
 <span data-ttu-id="c4024-115">テキスト ベースのクエリ デザイナーとグラフィカル クエリ デザイナーを切り替えます (両方のデザイナーが使用できる場合)。</span><span class="sxs-lookup"><span data-stu-id="c4024-115">Toggles between the text-based and graphical query designers, if both will work for the query.</span></span>  
  
 <span data-ttu-id="c4024-116">**[インポート]**</span><span class="sxs-lookup"><span data-stu-id="c4024-116">**Import**</span></span>  
 <span data-ttu-id="c4024-117">**[クエリのインポート]** ダイアログ ボックスを開き、利用可能なレポートの .rdl ファイルおよび .sql ファイルを表示します。</span><span class="sxs-lookup"><span data-stu-id="c4024-117">Opens the **Import Query** dialog box and displays .rdl and .sql files for any available report.</span></span> <span data-ttu-id="c4024-118">インポートされたクエリはそのまま使用することもできますが、クエリ ビルダーで修正することもできます。</span><span class="sxs-lookup"><span data-stu-id="c4024-118">You can use the imported query as it is, or you can modify it in the query builder.</span></span>  
  
 <span data-ttu-id="c4024-119">**[!] (実行)**</span><span class="sxs-lookup"><span data-stu-id="c4024-119">**! (Run)**</span></span>  
 <span data-ttu-id="c4024-120">クエリを実行し、クエリが有効であれば結果セットを返します。</span><span class="sxs-lookup"><span data-stu-id="c4024-120">Runs the query and returns a result set if the query is valid.</span></span> <span data-ttu-id="c4024-121">クエリが式の場合、そのクエリは実行できません。</span><span class="sxs-lookup"><span data-stu-id="c4024-121">Note that you cannot execute the query if it is an expression.</span></span> <span data-ttu-id="c4024-122">式に基づくクエリかどうかを確認するには、レポートをプレビューする必要があります。</span><span class="sxs-lookup"><span data-stu-id="c4024-122">To verify an expression-based query, you must preview the report.</span></span>  
  
 <span data-ttu-id="c4024-123">**コマンドの種類**</span><span class="sxs-lookup"><span data-stu-id="c4024-123">**Command type**</span></span>  
 <span data-ttu-id="c4024-124">テキスト、ストアド プロシージャ、またはテーブルを直接指定します。</span><span class="sxs-lookup"><span data-stu-id="c4024-124">Specifies text, stored procedure, or table direct.</span></span> <span data-ttu-id="c4024-125">使用できるコマンドの種類は、指定したデータ処理拡張機能によって異なります。</span><span class="sxs-lookup"><span data-stu-id="c4024-125">Availability of a command type depends on the data processing extension you specified.</span></span>  
  
 <span data-ttu-id="c4024-126">**クエリペイン**</span><span class="sxs-lookup"><span data-stu-id="c4024-126">**Query pane**</span></span>  
 <span data-ttu-id="c4024-127">クエリを入力します。</span><span class="sxs-lookup"><span data-stu-id="c4024-127">Type the query.</span></span>  
  
 <span data-ttu-id="c4024-128">**結果ペイン**</span><span class="sxs-lookup"><span data-stu-id="c4024-128">**Result pane**</span></span>  
 <span data-ttu-id="c4024-129">クエリから返された結果セットが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c4024-129">Shows the result set returned from the query.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4024-130">参照</span><span class="sxs-lookup"><span data-stu-id="c4024-130">See Also</span></span>  
 <span data-ttu-id="c4024-131">[レポート埋め込みデータセットと共有データセット &#40;レポートビルダーと SSRS&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c4024-131">[Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="c4024-132">レポート ウィザードのヘルプ</span><span class="sxs-lookup"><span data-stu-id="c4024-132">Report Wizard Help</span></span>](../../2014/reporting-services/report-wizard-help.md)  
  
  
