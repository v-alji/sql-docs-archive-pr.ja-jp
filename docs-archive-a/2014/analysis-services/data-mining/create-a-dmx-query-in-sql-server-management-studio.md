---
title: SQL Server Management Studio | で DMX クエリを作成します。Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- templates [Analysis Services], queries
- SQL Server Management Studio [Analysis Services], DMX queries
- predictions [Analysis Services], DMX prediction queries
- predictions [DMX]
- prediction queries [DMX]
- queries [DMX], prediction queries
- mining models [Analysis Services], DMX
ms.assetid: 568ce40a-1f53-47eb-8c79-14347cdfde83
author: minewiskan
ms.author: owend
ms.openlocfilehash: d20fc7a618f4977058203d8f35d235b543609dd9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642420"
---
# <a name="create-a-dmx-query-in-sql-server-management-studio"></a><span data-ttu-id="57b9a-102">SQL Server Management Studio で DMX クエリを作成する</span><span class="sxs-lookup"><span data-stu-id="57b9a-102">Create a DMX Query in SQL Server Management Studio</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="57b9a-103">には、マイニング モデルおよびマイニング構造に対する、予測クエリ、コンテンツ クエリ、およびデータ定義クエリを作成できる一連の機能が用意されています。</span><span class="sxs-lookup"><span data-stu-id="57b9a-103">provides a set of features to help you create prediction queries, content queries, and data definition queries against mining models and mining structures.</span></span>  
  
-   <span data-ttu-id="57b9a-104">グラフィカルな予測クエリ ビルダーは、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] と [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]の両方で使用でき、予測クエリを記述し、データ セットをモデルにマッピングするプロセスを簡略化します。</span><span class="sxs-lookup"><span data-stu-id="57b9a-104">The graphical Prediction Query Builder is available in both [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] and [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], to simplify the process of writing prediction queries and mapping data sets to a model.</span></span>  
  
-   <span data-ttu-id="57b9a-105">テンプレート エクスプローラーに用意されているクエリ テンプレートを使用すると、さまざまな種類の予測クエリなど、さまざまな種類の DMX クエリの作成をすぐに開始できます。</span><span class="sxs-lookup"><span data-stu-id="57b9a-105">The query templates provided in the Template Explorer jump-start the creation of many kinds of DMX queries, including many types of prediction queries.</span></span> <span data-ttu-id="57b9a-106">テンプレートには、コンテンツ クエリ用、入れ子になったデータ セットを使用したクエリ用、マイニング構造からケースを返すクエリ用だけでなく、データ定義クエリ用もあります。</span><span class="sxs-lookup"><span data-stu-id="57b9a-106">Templates are provided for content queries, queries used nested data sets, queries that return cases from the mining structure, and even data definition queries.</span></span>  
  
-   <span data-ttu-id="57b9a-107">MDX および DMX のクエリ ペインのメタデータ エクスプローラーには、DMX 関数の一覧のほかに、使用できるモデルと構造の一覧が表示されます。それらをクエリ ビルダーにドラッグ アンド ドロップできます。</span><span class="sxs-lookup"><span data-stu-id="57b9a-107">The Metadata Explorer in the MDX and DMX query panes provides a list of available models and structures that you can drag and drop into the query builder, as well as a list of DMX functions.</span></span> <span data-ttu-id="57b9a-108">この機能を使用すると、正しいオブジェクト名を入力することなく簡単に指定できます。</span><span class="sxs-lookup"><span data-stu-id="57b9a-108">This feature makes it easy to get object names right, without typing.</span></span>  
  
 <span data-ttu-id="57b9a-109">ここでは、メタデータ エクスプローラーと DMX クエリ エディターを使用して、DMX クエリを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="57b9a-109">This topic describes how to build a DMX query by using the Metadata Explorer and the DMX query editor.</span></span>  
  
##  <a name="dmx-query-templates"></a><a name="BKMK_Templates"></a><span data-ttu-id="57b9a-110">DMX クエリテンプレート</span><span class="sxs-lookup"><span data-stu-id="57b9a-110">DMX Query Templates</span></span>  
 <span data-ttu-id="57b9a-111">基本的な DMX クエリを作成するためのテンプレートは、テンプレート エクスプローラーから利用できます。</span><span class="sxs-lookup"><span data-stu-id="57b9a-111">Templates for creating basic DMX queries are available in Template Explorer.</span></span> <span data-ttu-id="57b9a-112">**DMX** フォルダーには、データ マイニング テンプレートが含まれています。テンプレートは、次のカテゴリに分類されます。</span><span class="sxs-lookup"><span data-stu-id="57b9a-112">The **DMX** folder contains data mining templates, which are divided into these categories:</span></span>  
  
-   <span data-ttu-id="57b9a-113">**モデルコンテンツ**</span><span class="sxs-lookup"><span data-stu-id="57b9a-113">**Model Content**</span></span>  
  
-   <span data-ttu-id="57b9a-114">**モデル管理**</span><span class="sxs-lookup"><span data-stu-id="57b9a-114">**Model Management**</span></span>  
  
-   <span data-ttu-id="57b9a-115">**予測クエリ**</span><span class="sxs-lookup"><span data-stu-id="57b9a-115">**Prediction Queries**</span></span>  
  
-   <span data-ttu-id="57b9a-116">**構造コンテンツ**</span><span class="sxs-lookup"><span data-stu-id="57b9a-116">**Structure Content**</span></span>  
  
 <span data-ttu-id="57b9a-117">頻繁に実行するクエリまたはコマンドのカスタム テンプレートを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="57b9a-117">You can also create custom templates, for queries or commands that you run frequently.</span></span>  
  
## <a name="xmla-query-templates"></a><span data-ttu-id="57b9a-118">XMLA クエリ テンプレート</span><span class="sxs-lookup"><span data-stu-id="57b9a-118">XMLA Query Templates</span></span>  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="57b9a-119">には、XMLA クエリのテンプレートも用意されています。</span><span class="sxs-lookup"><span data-stu-id="57b9a-119">also provides templates for XMLA queries.</span></span>  
  
 <span data-ttu-id="57b9a-120">XMLA と DMX を使用して実行できるクエリの種類は一部重複しています。</span><span class="sxs-lookup"><span data-stu-id="57b9a-120">There is some overlap between the types of queries that you can perform by using XMLA and DMX.</span></span> <span data-ttu-id="57b9a-121">たとえば、モデル コンテンツ クエリは DMX またはデータ マイニング スキーマ行セットを使用して作成できますが、スキーマ行セットには DMX コンテンツ クエリでは公開されない情報が含まれている場合があります。</span><span class="sxs-lookup"><span data-stu-id="57b9a-121">For example, you can create some model content queries by using either DMX or the data mining schema rowsets, but the schema rowsets sometimes contain information that is not exposed in DMX content queries.</span></span>  
  
 <span data-ttu-id="57b9a-122">また、DMX と XMLA での操作の処理方法には、いくつかの重要な違いがあります。</span><span class="sxs-lookup"><span data-stu-id="57b9a-122">There are also some key differences in the way that operations are handled in DMX and in XMLA.</span></span> <span data-ttu-id="57b9a-123">たとえば、XMLA を使用して、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベース全体のバックアップなどの管理操作を実行できますが、DMX には [EXPORT (DMX)](/sql/dmx/export-dmx) という簡単なコマンドが用意されています。1 つのマイニング モデルをバックアップする場合は、このコマンドの方が適しています。</span><span class="sxs-lookup"><span data-stu-id="57b9a-123">For example, you can use XMLA to perform administrative operations such as backup of an entire [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database, but if you want to back up a single mining model, DMX provides a simple command, [EXPORT &#40;DMX&#41;](/sql/dmx/export-dmx), that is better suited to that purpose.</span></span>  
  
##  <a name="build-and-run-a-dmx-query"></a><a name="BKMK_Building_Queries"></a><span data-ttu-id="57b9a-124">DMX クエリの作成と実行</span><span class="sxs-lookup"><span data-stu-id="57b9a-124">Build and Run a DMX Query</span></span>  
  
#### <a name="open-a-new-dmx-query-window"></a><span data-ttu-id="57b9a-125">新しい DMX クエリ ウィンドウを開く</span><span class="sxs-lookup"><span data-stu-id="57b9a-125">Open a new DMX Query window</span></span>  
  
1.  <span data-ttu-id="57b9a-126">**で** [新しいクエリ] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]をクリックし、 **[新しい分析サーバー DMX クエリ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="57b9a-126">Click **New Query** in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], and then select **New Analysis Server DMX Query**.</span></span>  
  
2.  <span data-ttu-id="57b9a-127">**[サーバーへの接続]** ダイアログ ボックスが表示されたら、操作するマイニング モデルが含まれている [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインスタンスを選択します。</span><span class="sxs-lookup"><span data-stu-id="57b9a-127">When the **Connect to Server** dialog box appears, select the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] that contains the mining models you want to work with.</span></span>  
  
#### <a name="open-template-explorer"></a><span data-ttu-id="57b9a-128">テンプレート エクスプローラーを開く</span><span class="sxs-lookup"><span data-stu-id="57b9a-128">Open Template Explorer</span></span>  
  
1.  <span data-ttu-id="57b9a-129">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、 **[表示]** メニューの **[テンプレート エクスプローラー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="57b9a-129">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], on the **View** menu, select **Template Explorer**.</span></span>  
  
2.  <span data-ttu-id="57b9a-130">**[分析サーバー]** をクリックして、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]に適用するテンプレートのツリー ビューを表示します。</span><span class="sxs-lookup"><span data-stu-id="57b9a-130">Click **Analysis Server** to see a tree view of the templates that apply to [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
#### <a name="apply-a-template-to-build-a-query"></a><span data-ttu-id="57b9a-131">テンプレートを適用したクエリの作成</span><span class="sxs-lookup"><span data-stu-id="57b9a-131">Apply a template to build a query</span></span>  
  
-   <span data-ttu-id="57b9a-132">適切なクエリの種類を右クリックし、 **[開く]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="57b9a-132">Right-click the appropriate query type and select **Open**.</span></span>  
  
-   <span data-ttu-id="57b9a-133">または、テンプレートをクエリ エディターにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="57b9a-133">Or, drag the template into the query editor.</span></span>  
  
-   <span data-ttu-id="57b9a-134">また、 **[クエリ]** メニューの **[パラメーター値の指定]** オプションを使用して、クエリのパラメーターを入力することもできます。</span><span class="sxs-lookup"><span data-stu-id="57b9a-134">You can also fill in the parameters for the query by using the option, **Specify Values for Parameters**, from the **Query** menu.</span></span>  
  
 <span data-ttu-id="57b9a-135">テンプレートから特定の種類のクエリを作成する方法の例については、次の各トピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="57b9a-135">For examples of how to create specific types of queries from templates, see the following topics:</span></span>  
  
 [<span data-ttu-id="57b9a-136">テンプレートからの単一予測クエリの作成</span><span class="sxs-lookup"><span data-stu-id="57b9a-136">Create a Singleton Prediction Query from a Template</span></span>](create-a-singleton-prediction-query-from-a-template.md)  
  
 [<span data-ttu-id="57b9a-137">マイニング モデルのコンテンツ クエリの作成</span><span class="sxs-lookup"><span data-stu-id="57b9a-137">Create a Content Query on a Mining Model</span></span>](create-a-content-query-on-a-mining-model.md)  
  
## <a name="see-also"></a><span data-ttu-id="57b9a-138">参照</span><span class="sxs-lookup"><span data-stu-id="57b9a-138">See Also</span></span>  
 <span data-ttu-id="57b9a-139">[データマイニングクエリインターフェイス](data-mining-query-tools.md) </span><span class="sxs-lookup"><span data-stu-id="57b9a-139">[Data Mining Query Interfaces](data-mining-query-tools.md) </span></span>  
 [<span data-ttu-id="57b9a-140">データ マイニング拡張機能 &#40;DMX&#41; リファレンス</span><span class="sxs-lookup"><span data-stu-id="57b9a-140">Data Mining Extensions &#40;DMX&#41; Reference</span></span>](/sql/dmx/data-mining-extensions-dmx-reference)  
  
  
