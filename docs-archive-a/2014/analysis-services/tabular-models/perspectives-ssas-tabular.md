---
title: パースペクティブ (SSAS テーブル) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 1f78c3a1-ce2c-4e7f-a277-71a657692bea
author: minewiskan
ms.author: owend
ms.openlocfilehash: e11f8be980b99c4e9bd824f281db31e9c3f7d9bf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712474"
---
# <a name="perspectives-ssas-tabular"></a><span data-ttu-id="dad71-102">パースペクティブ (SSAS テーブル)</span><span class="sxs-lookup"><span data-stu-id="dad71-102">Perspectives (SSAS Tabular)</span></span>
  <span data-ttu-id="dad71-103">テーブル モデルでパースペクティブを使用すると、ビジネス固有またはアプリケーション固有のビューポイントをモデルに対して的を絞って作成するための、表示可能なサブセットを定義できます。</span><span class="sxs-lookup"><span data-stu-id="dad71-103">Perspectives, in tabular models, define viewable subsets of a model that provide focused, business-specific, or application-specific viewpoints of the model.</span></span>  
  
 <span data-ttu-id="dad71-104">このトピックのセクション:</span><span class="sxs-lookup"><span data-stu-id="dad71-104">Sections in this topic:</span></span>  
  
-   [<span data-ttu-id="dad71-105">メリット</span><span class="sxs-lookup"><span data-stu-id="dad71-105">Benefits</span></span>](#bkmk_understanding)  
  
-   [<span data-ttu-id="dad71-106">パースペクティブのテスト</span><span class="sxs-lookup"><span data-stu-id="dad71-106">Testing Perspectives</span></span>](#bkmk_testpersp)  
  
-   [<span data-ttu-id="dad71-107">関連タスク</span><span class="sxs-lookup"><span data-stu-id="dad71-107">Related Tasks</span></span>](#bkmk_related_tasks)  
  
##  <a name="benefits"></a><a name="bkmk_understanding"></a> <span data-ttu-id="dad71-108">利点</span><span class="sxs-lookup"><span data-stu-id="dad71-108">Benefits</span></span>  
 <span data-ttu-id="dad71-109">テーブル モデルは非常に複雑であるために、扱いが困難なことがあります。</span><span class="sxs-lookup"><span data-stu-id="dad71-109">Tabular models can be very complex for users to explore.</span></span> <span data-ttu-id="dad71-110">テーブル モデルは、1 つだけで多くのテーブル、メジャー、ディメンションを持つ完全なデータ ウェアハウスの内容を表すことができます。</span><span class="sxs-lookup"><span data-stu-id="dad71-110">A single model can represent the contents of a complete data warehouse with many tables, measures, and dimensions.</span></span> <span data-ttu-id="dad71-111">しかしこのような複雑さは、ビジネス インテリジェンス要件やレポート要件を満たすために、モデルのごく一部分しか操作する必要のないユーザーにとっては大きな負担になります。</span><span class="sxs-lookup"><span data-stu-id="dad71-111">Such complexity can be daunting to users who may only need to interact with a small part of the model in order to satisfy their business intelligence and reporting requirements.</span></span>  
  
 <span data-ttu-id="dad71-112">パースペクティブでは、テーブル、列、およびメジャー (KPI を含む) がフィールド オブジェクトとして定義されます。</span><span class="sxs-lookup"><span data-stu-id="dad71-112">In a perspective, tables, columns, and measures (including KPIs) are defined as field objects.</span></span> <span data-ttu-id="dad71-113">パースペクティブごとに複数の表示可能なフィールドを選択できます。</span><span class="sxs-lookup"><span data-stu-id="dad71-113">You can select the viewable fields for each perspective.</span></span> <span data-ttu-id="dad71-114">たとえば、1 つのモデルに商品、売上、財務、従業員、および地域のデータが含まれている場合があります。</span><span class="sxs-lookup"><span data-stu-id="dad71-114">For example, a single model may contain product, sales, financial, employee, and geographic data.</span></span> <span data-ttu-id="dad71-115">販売部門では商品、売上、プロモーション、地域のデータは必要ですが、従業員や財務のデータはおそらく必要ありません。</span><span class="sxs-lookup"><span data-stu-id="dad71-115">While a sales department requires product, sales, promotions, and geography data, they likely do not require employee and financial data.</span></span> <span data-ttu-id="dad71-116">同様に、人事部門では販売プロモーションや地域のデータは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="dad71-116">Similarly, a human resources department does not require data about sales promotions and geography.</span></span>  
  
 <span data-ttu-id="dad71-117">パースペクティブが定義されたモデルに (データ ソースとして) 接続する際、ユーザーは使用するパースペクティブを選択できます。</span><span class="sxs-lookup"><span data-stu-id="dad71-117">When a user connects to a model (as a data source) with defined perspectives, the user can select the perspective they want to use.</span></span> <span data-ttu-id="dad71-118">たとえば、Excel のモデル データ ソースに接続する際、人事部門のユーザーはデータ接続ウィザードの [テーブルとビューの選択] ページにある人事パースペクティブを選択できます。</span><span class="sxs-lookup"><span data-stu-id="dad71-118">For example, when connecting to a model data source in Excel, users in Human Resources can select the Human Resources perspective on the Select Tables and Views page of the Data Connection Wizard.</span></span> <span data-ttu-id="dad71-119">ピボットテーブルのフィールド一覧には、人事パースペクティブに定義されたフィールド (テーブル、列、およびメジャー) のみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="dad71-119">Only fields (tables, columns, and measures) defined for the Human Resources perspective will be visible in the PivotTable Field List.</span></span>  
  
 <span data-ttu-id="dad71-120">パースペクティブは、セキュリティ メカニズムとして使用するためのものではなく、ユーザーの使用体験をより良いものにするためのツールとして使用するものです。</span><span class="sxs-lookup"><span data-stu-id="dad71-120">Perspectives are not meant to be used as a security mechanism, but as a tool for providing a better user experience.</span></span> <span data-ttu-id="dad71-121">特定のパースペクティブのセキュリティはすべて、基になるモデルから継承されます。</span><span class="sxs-lookup"><span data-stu-id="dad71-121">All security for a particular perspective is inherited from the underlying model.</span></span> <span data-ttu-id="dad71-122">パースペクティブでは、ユーザーがアクセス権を持っていないモデル オブジェクトにアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="dad71-122">Perspectives cannot provide access to model objects to which a user does not already have access.</span></span> <span data-ttu-id="dad71-123">パースペクティブでモデルのオブジェクトへのアクセスが提供されるようにするには、そのモデル データベースのセキュリティを解決しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="dad71-123">Security for the model database must be resolved before access to objects in the model can be provided through a perspective.</span></span> <span data-ttu-id="dad71-124">セキュリティ ロールを使用して、モデルのメタデータとデータをセキュリティ保護することができます。</span><span class="sxs-lookup"><span data-stu-id="dad71-124">Security roles can be used to secure model metadata and data.</span></span> <span data-ttu-id="dad71-125">詳しくは、「 [ロール &#40;SSAS テーブル&#41;](roles-ssas-tabular.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="dad71-125">For more information, see [Roles &#40;SSAS Tabular&#41;](roles-ssas-tabular.md).</span></span>  
  
##  <a name="testing-perspectives"></a><a name="bkmk_testpersp"></a><span data-ttu-id="dad71-126">パースペクティブのテスト</span><span class="sxs-lookup"><span data-stu-id="dad71-126">Testing Perspectives</span></span>  
 <span data-ttu-id="dad71-127">モデルの作成時に、モデル デザイナーの Excel で分析機能を使用して、定義したパースペクティブの有効性をテストできます。</span><span class="sxs-lookup"><span data-stu-id="dad71-127">When authoring a model, you can use the Analyze in Excel feature in the model designer to test the efficacy of the perspectives you have defined.</span></span> <span data-ttu-id="dad71-128">モデル デザイナーで **[モデル]** メニューの **[Excel で分析]** をクリックすると、Excel が開く前に **[資格情報とパースペクティブの選択]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="dad71-128">From the **Model** menu in the model designer, when you click **Analyze in Excel**, before Excel opens, the **Choose Credentials and Perspective** dialog box appears.</span></span> <span data-ttu-id="dad71-129">このダイアログ ボックスでは、データ ソースとしてモデル ワークスペース データベースに接続し、データを表示するために使用する、現在のユーザー名、別のユーザー、ロール、およびパースペクティブを指定できます。</span><span class="sxs-lookup"><span data-stu-id="dad71-129">In this dialog, you can specify the current username, a different user, a role, and a perspective with which you will use to connect to the model workspace database as a data source and view data.</span></span>  
  
##  <a name="related-tasks"></a><a name="bkmk_related_tasks"></a> <span data-ttu-id="dad71-130">関連タスク</span><span class="sxs-lookup"><span data-stu-id="dad71-130">Related Tasks</span></span>  
  
|<span data-ttu-id="dad71-131">トピック</span><span class="sxs-lookup"><span data-stu-id="dad71-131">Topic</span></span>|<span data-ttu-id="dad71-132">説明</span><span class="sxs-lookup"><span data-stu-id="dad71-132">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="dad71-133">パースペクティブの作成と管理 (SSAS テーブル)</span><span class="sxs-lookup"><span data-stu-id="dad71-133">Create and Manage Perspectives &#40;SSAS Tabular&#41;</span></span>](perspectives-ssas-tabular.md)|<span data-ttu-id="dad71-134">モデル デザイナーで [パースペクティブ] ダイアログ ボックスを使用して、パースペクティブを作成し管理する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="dad71-134">Describes how to create and manage perspectives using the Perspectives dialog box in the model designer.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dad71-135">参照</span><span class="sxs-lookup"><span data-stu-id="dad71-135">See Also</span></span>  
 <span data-ttu-id="dad71-136">[SSAS 表形式のロール &#40;&#41;](roles-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="dad71-136">[Roles &#40;SSAS Tabular&#41;](roles-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="dad71-137">階層 &#40;SSAS テーブル&#41;</span><span class="sxs-lookup"><span data-stu-id="dad71-137">Hierarchies &#40;SSAS Tabular&#41;</span></span>](hierarchies-ssas-tabular.md)  
  
  
