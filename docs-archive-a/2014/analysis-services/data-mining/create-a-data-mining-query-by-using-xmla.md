---
title: XMLA | を使用してデータマイニングクエリを作成するMicrosoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- content queries [DMX]
ms.assetid: 8f6b6008-006c-4792-9bd1-64c30dc3fd41
author: minewiskan
ms.author: owend
ms.openlocfilehash: d0e85b17db0781671fab0874706f12fdac95b30b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644712"
---
# <a name="create-a-data-mining-query-by-using-xmla"></a><span data-ttu-id="d1be3-102">XMLA を使用したデータ マイニング クエリの作成</span><span class="sxs-lookup"><span data-stu-id="d1be3-102">Create a Data Mining Query by Using XMLA</span></span>
  <span data-ttu-id="d1be3-103">AMO、DMX、または XML/A を使用すると、データ マイニング オブジェクトに対するさまざまなクエリを作成できます。</span><span class="sxs-lookup"><span data-stu-id="d1be3-103">You can create a variety of queries against data mining objects by using AMO, DMX, or XML/A.</span></span>  
  
 <span data-ttu-id="d1be3-104">Analysis Services サーバーとすべてのクライアントの間の通信には、XML が使用されます。</span><span class="sxs-lookup"><span data-stu-id="d1be3-104">XML is used for communication between the Analysis Services server and all clients.</span></span> <span data-ttu-id="d1be3-105">したがって、一般には DMX を使用してコンテンツ クエリを作成する方がはるかに簡単ですが、SOAP プロトコルをサポートするクライアントを使用するか、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で XML/A クエリを作成することにより、XML/A で DISCOVER および COMMAND ステートメントを使用してクエリを作成できます。</span><span class="sxs-lookup"><span data-stu-id="d1be3-105">Therefore, although it is generally much easier to create content queries by using DMX, you can write queries by using the DISCOVER and COMMAND statements in XML/A, either by using a client that supports the SOAP protocol, or by creating an XML/A query in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="d1be3-106">このトピックでは、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] で利用できる XML/A テンプレートを使用して、現在のサーバーに格納されているマイニング モデルに対するモデル コンテンツ クエリを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d1be3-106">This topic explains how to use the XML/A templates that are available in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to create a model content query against a mining model stored on the current server.</span></span>  
  
## <a name="querying-data-mining-schema-rowsets-by-using-xmla"></a><span data-ttu-id="d1be3-107">XML/A を使用したデータ マイニング スキーマ行セットのクエリ</span><span class="sxs-lookup"><span data-stu-id="d1be3-107">Querying Data Mining Schema Rowsets by Using XML/A</span></span>  
  
#### <a name="to-open-an-xmla-template"></a><span data-ttu-id="d1be3-108">XML/A テンプレートを開くには</span><span class="sxs-lookup"><span data-stu-id="d1be3-108">To open an XML/A template</span></span>  
  
1.  <span data-ttu-id="d1be3-109">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、 **[表示]** メニューの **[テンプレート エクスプローラー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d1be3-109">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], on the **View** menu, click **Template Explorer**.</span></span>  
  
2.  <span data-ttu-id="d1be3-110">キューブ アイコンをクリックして、Analysis Services テンプレートの一覧を開きます。</span><span class="sxs-lookup"><span data-stu-id="d1be3-110">Click the cube icon to open the list of Analysis Services templates.</span></span>  
  
3.  <span data-ttu-id="d1be3-111">テンプレート カテゴリの一覧で **[XMLA]**、 **[スキーマ行セット]** の順に展開し、 **[スキーマ行セットの発見]** をダブルクリックします。コード エディターにこのテンプレートが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d1be3-111">In the list of template categories, expand **XMLA**, expand **Schema Rowsets**, and double-click **Discover Schema Rowsets** to open the template in the appropriate code editor.</span></span>  
  
4.  <span data-ttu-id="d1be3-112">**[Analysis Services への接続]** ダイアログ ボックスで接続情報を指定し、 **[接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d1be3-112">In the **Connect to Analysis Services** dialog box, complete the connection information and then click **Connect**.</span></span> <span data-ttu-id="d1be3-113">新しいクエリ エディター ウィンドウが開き、 **[スキーマ行セットの発見]** テンプレートの内容が表示されます。</span><span class="sxs-lookup"><span data-stu-id="d1be3-113">A new query editor window opens, populated with the **Discover Schema Rowsets** template.</span></span>  
  
#### <a name="to-discover-column-names-from-the-mining-model-content-schema-rowset"></a><span data-ttu-id="d1be3-114">MINING MODEL CONTENT スキーマ行セットから列名を検出するには</span><span class="sxs-lookup"><span data-stu-id="d1be3-114">To discover column names from the MINING MODEL CONTENT schema rowset</span></span>  
  
1.  <span data-ttu-id="d1be3-115">**[スキーマ行セットの発見]** テンプレートを開き、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d1be3-115">With the **Discover Schema Rowsets** template open, click **Execute**.</span></span>  
  
     <span data-ttu-id="d1be3-116">**[結果]** ペインに返されるスキーマ行セットの一覧には、現在のインスタンスで入手できるすべての行セットの行セット名と行セット列が含まれます。</span><span class="sxs-lookup"><span data-stu-id="d1be3-116">A list of schema rowsets is returned in the **Results** pane that contains the rowset names and rowset columns for all rowsets available on the current instance.</span></span>  
  
2.  <span data-ttu-id="d1be3-117">**クエリ**ペインで、の後にカーソルを置き、enter **\<Restriction List>** キーを押して新しい行を追加します。</span><span class="sxs-lookup"><span data-stu-id="d1be3-117">In the **Query** pane, place the cursor after **\<Restriction List>** and press ENTER to add a new line.</span></span>  
  
3.  <span data-ttu-id="d1be3-118">空白行にカーソルを置き、「」と入力し\*\* \<SchemaName> DMSCHEMA_MINING_MODEL_CONTENT \</SchemaName> \*\*</span><span class="sxs-lookup"><span data-stu-id="d1be3-118">Place the cursor on the blank line and type **\<SchemaName>DMSCHEMA_MINING_MODEL_CONTENT\</SchemaName>**</span></span>  
  
     <span data-ttu-id="d1be3-119">制限のセクション全体は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="d1be3-119">The complete section for restrictions should appear as follows:</span></span>  
  
     `<Restrictions>`  
  
     `<RestrictionList>`  
  
     `<SchemaName>DMSCHEMA_MINING_MODEL_CONTENT</SchemaName>`  
  
     `</RestrictionList>`  
  
     `</Restrictions>`  
  
4.  <span data-ttu-id="d1be3-120">**[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d1be3-120">Click **Execute**.</span></span>  
  
     <span data-ttu-id="d1be3-121">**[結果]** ペインに、指定したスキーマ行セットの列名の一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="d1be3-121">The **Results** pane shows a list of column names for the specified schema rowset.</span></span>  
  
#### <a name="to-create-a-content-query-using-the-mining-model-content-schema-rowset"></a><span data-ttu-id="d1be3-122">MINING MODEL CONTENT スキーマ行セットを使用してコンテンツ クエリを作成するには</span><span class="sxs-lookup"><span data-stu-id="d1be3-122">To create a content query using the MINING MODEL CONTENT schema rowset</span></span>  
  
1.  <span data-ttu-id="d1be3-123">**[スキーマ行セットの発見]** テンプレートで、"要求の種類" タグの内側のテキストを置き換えて、要求の種類を変更します。</span><span class="sxs-lookup"><span data-stu-id="d1be3-123">In the **Discover Schema Rowsets** template, change the request type by replacing the text inside the request type tags.</span></span>  
  
     <span data-ttu-id="d1be3-124">次の行を置き換えます。</span><span class="sxs-lookup"><span data-stu-id="d1be3-124">Replace this line:</span></span>  
  
     `<RequestType>DISCOVER_SCHEMA_ROWSETS</RequestType>`  
  
     <span data-ttu-id="d1be3-125">次の行に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="d1be3-125">with the following line:</span></span>  
  
     <span data-ttu-id="d1be3-126">**\<RequestType>DMSCHEMA_MINING_MODEL_CONTENT\</RequestType>**</span><span class="sxs-lookup"><span data-stu-id="d1be3-126">**\<RequestType>DMSCHEMA_MINING_MODEL_CONTENT\</RequestType>**</span></span>  
  
2.  <span data-ttu-id="d1be3-127">制限リストに新しい条件を追加することで、名前でマイニング モデルを指定するように制限リストを変更します。</span><span class="sxs-lookup"><span data-stu-id="d1be3-127">Change the restriction list to specify a mining model by name, by adding a new condition to the restriction lists.</span></span>  
  
3.  <span data-ttu-id="d1be3-128">テンプレートで、 `<Restriction List>` の後ろにカーソルを置き、Enter キーを押して新しい行を追加します。</span><span class="sxs-lookup"><span data-stu-id="d1be3-128">In the template, place the cursor after `<Restriction List>` and press ENTER to add a new line.</span></span>  
  
4.  <span data-ttu-id="d1be3-129">空白行にカーソルを置き、「**<MODEL_NAME>My model name</MODEL_NAME>**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="d1be3-129">Place the cursor on the blank line and type **<MODEL_NAME>My model name</MODEL_NAME>**</span></span>  
  
     <span data-ttu-id="d1be3-130">制限のセクション全体は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="d1be3-130">The complete section for restrictions should appear as follows:</span></span>  
  
     `<Restrictions>`  
  
     `<RestrictionList>`  
  
     `<MODEL_NAME>My model name</MODEL_NAME>`  
  
     `</RestrictionList>`  
  
     `</Restrictions>`  
  
5.  <span data-ttu-id="d1be3-131">**[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d1be3-131">Click **Execute**.</span></span>  
  
     <span data-ttu-id="d1be3-132">[結果] ペインに、スキーマ定義および指定したモデルの値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="d1be3-132">The Results pane displays the schema definition, together with the values for the specified model.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1be3-133">参照</span><span class="sxs-lookup"><span data-stu-id="d1be3-133">See Also</span></span>  
 <span data-ttu-id="d1be3-134">[マイニングモデルコンテンツ &#40;Analysis Services-データマイニング&#41;](mining-model-content-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="d1be3-134">[Mining Model Content &#40;Analysis Services - Data Mining&#41;](mining-model-content-analysis-services-data-mining.md) </span></span>  
 [<span data-ttu-id="d1be3-135">データ マイニング スキーマ行セット</span><span class="sxs-lookup"><span data-stu-id="d1be3-135">Data Mining Schema Rowsets</span></span>](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/data-mining-schema-rowsets) 
  
  
