---
title: キューブスキーマを表示する |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 82fc715c-e08e-447d-8fc8-9c9005f145f0
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2e7d324db1e0c41588694031d3c121fdb47233f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740518"
---
# <a name="view-the-cube-schema"></a><span data-ttu-id="8abe8-102">キューブ スキーマの表示</span><span class="sxs-lookup"><span data-stu-id="8abe8-102">View the Cube Schema</span></span>
  <span data-ttu-id="8abe8-103">**キューブ デザイナー** の **[キューブ構造]** タブにある **[データ ソース ビュー]** ペインには、キューブ スキーマが表示されます。</span><span class="sxs-lookup"><span data-stu-id="8abe8-103">The **Data Source View** pane of the **Cube Structure** tab in **Cube Designer** displays the cube schema.</span></span> <span data-ttu-id="8abe8-104">スキーマとは、キューブのメジャーおよびディメンションの派生元であるテーブルのセットです。</span><span class="sxs-lookup"><span data-stu-id="8abe8-104">The schema is the set of tables from which the measures and dimensions for a cube are derived.</span></span> <span data-ttu-id="8abe8-105">どのキューブ スキーマも、キューブ内のメジャーとディメンションの基になっている 1 つ以上のファクト テーブルと 1 つ以上のディメンション テーブルで構成されます。</span><span class="sxs-lookup"><span data-stu-id="8abe8-105">Every cube schema consists of one or more fact tables and one or more dimension tables on which the measures and dimensions in the cube are based.</span></span>  
  
 <span data-ttu-id="8abe8-106">**[キューブ構造]** タブの **[データ ソース ビュー]** ペインには、キューブの基になっているデータ ソース ビューのダイアグラムが表示されます。</span><span class="sxs-lookup"><span data-stu-id="8abe8-106">The **Data Source View** pane of the **Cube Structure** tab displays a diagram of the data source view on which the cube is based.</span></span> <span data-ttu-id="8abe8-107">このダイアグラムは、データ ソース ビューのメイン ダイアグラムのサブセットです。</span><span class="sxs-lookup"><span data-stu-id="8abe8-107">This diagram is a subset of the main diagram of the data source view.</span></span> <span data-ttu-id="8abe8-108">**[データ ソース ビュー]** ペインのテーブルの表示と非表示を切り替えたり、既存のダイアグラムを表示したりできます。</span><span class="sxs-lookup"><span data-stu-id="8abe8-108">You can hide and show tables in the **Data Source View** pane and view any existing diagrams.</span></span> <span data-ttu-id="8abe8-109">ただし、基になるスキーマに変更 (新しいリレーションシップまたは名前付きクエリの追加など) を加えることはできません。</span><span class="sxs-lookup"><span data-stu-id="8abe8-109">However, you cannot make changes (such as adding new relationships or named queries) to the underlying schema.</span></span> <span data-ttu-id="8abe8-110">スキーマに変更を加えるには、データ ソース ビュー デザイナーを使用します。</span><span class="sxs-lookup"><span data-stu-id="8abe8-110">To make changes to the schema, use Data Source View Designer.</span></span>  
  
 <span data-ttu-id="8abe8-111">キューブを作成すると、 **[キューブ構造]** タブの **[データ ソース ビュー]** ペインに最初に表示されるダイアグラムは、プロジェクトまたはデータベースのデータ ソース ビューの **[すべてのテーブルを表示]** ダイアグラムと同じになります。</span><span class="sxs-lookup"><span data-stu-id="8abe8-111">When you create a cube, the diagram displayed in the **Data Source View** pane of the **Cube Structure** tab is initially the same as the **Show All Tables** diagram in the data source view for the project or database.</span></span> <span data-ttu-id="8abe8-112">このダイアグラムをデータ ソース ビューの既存のダイアグラムで置換して、 **[データ ソース ビュー]** ペインで調整を加えることができます。</span><span class="sxs-lookup"><span data-stu-id="8abe8-112">You can replace this diagram with any existing diagram in the data source view and make adjustments in the **Data Source View** pane.</span></span>  
  
 <span data-ttu-id="8abe8-113">**キューブ デザイナー**でダイアグラムを編集する場合、タブまたはタブ内の選択したオブジェクトに対して実行できるコマンドは、 **[データ ソース ビュー]** メニューから選択できます。</span><span class="sxs-lookup"><span data-stu-id="8abe8-113">While you work with the diagram in **Cube Designer**, commands that act on the tab or on any selected object in the tab are available on the **Data Source View** menu.</span></span> <span data-ttu-id="8abe8-114">また、ダイアグラムまたはダイアグラム内の任意のオブジェクトの背景を右クリックして、ダイアグラムまたは選択したオブジェクトに対してコマンドを実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="8abe8-114">You can also right-click the background of the diagram or any object in the diagram to use commands that act on the diagram or selected object.</span></span> <span data-ttu-id="8abe8-115">次のようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="8abe8-115">You can:</span></span>  
  
-   <span data-ttu-id="8abe8-116">ダイアグラム形式とツリー形式の切り替え</span><span class="sxs-lookup"><span data-stu-id="8abe8-116">Switch between diagram and tree formats.</span></span>  
  
-   <span data-ttu-id="8abe8-117">テーブルの整列、検索、表示、および非表示</span><span class="sxs-lookup"><span data-stu-id="8abe8-117">Arrange, find, show, and hide tables.</span></span>  
  
-   <span data-ttu-id="8abe8-118">表示名の表示</span><span class="sxs-lookup"><span data-stu-id="8abe8-118">Show friendly names.</span></span>  
  
-   <span data-ttu-id="8abe8-119">レイアウトの切り替え</span><span class="sxs-lookup"><span data-stu-id="8abe8-119">Switch layouts.</span></span>  
  
-   <span data-ttu-id="8abe8-120">倍率の変更</span><span class="sxs-lookup"><span data-stu-id="8abe8-120">Change the magnification.</span></span>  
  
-   <span data-ttu-id="8abe8-121">プロパティの表示</span><span class="sxs-lookup"><span data-stu-id="8abe8-121">View properties.</span></span>  
  
 <span data-ttu-id="8abe8-122">さらに、次の表に示す操作を実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="8abe8-122">Additionally, you can perform the actions listed in the following table:</span></span>  
  
|<span data-ttu-id="8abe8-123">ターゲット</span><span class="sxs-lookup"><span data-stu-id="8abe8-123">To</span></span>|<span data-ttu-id="8abe8-124">方法</span><span class="sxs-lookup"><span data-stu-id="8abe8-124">Do this</span></span>|  
|--------|-------------|  
|<span data-ttu-id="8abe8-125">キューブのデータ ソース ビューのダイアグラムを使用する</span><span class="sxs-lookup"><span data-stu-id="8abe8-125">Use a diagram from the data source view of the cube</span></span>|<span data-ttu-id="8abe8-126">**[データ ソース ビュー]** メニューの **[ダイアグラムのコピー元]** をポイントして、使用するデータ ソース ビュー ダイアグラムをクリックします。</span><span class="sxs-lookup"><span data-stu-id="8abe8-126">On the **Data Source View** menu, point to **Copy Diagram from**, and then click the data source view diagram you want to use.</span></span><br /><br /> <span data-ttu-id="8abe8-127">または</span><span class="sxs-lookup"><span data-stu-id="8abe8-127">- or -</span></span><br /><br /> <span data-ttu-id="8abe8-128">**[データ ソース ビュー]** ペインの背景を右クリックして、 **[ダイアグラムのコピー元]** をポイントし、使用するデータ ソース ビューのダイアグラムをクリックします。</span><span class="sxs-lookup"><span data-stu-id="8abe8-128">Right-click the background of the **Data Source View** pane, point to **Copy Diagram from**, and then click the diagram in the data source view that you want.</span></span> <span data-ttu-id="8abe8-129">この方法では、ダイアグラムの独立したコピーが作成されるため、 **[キューブ ビルダー]** タブで加えた変更は元のダイアグラムには反映されません。</span><span class="sxs-lookup"><span data-stu-id="8abe8-129">This method creates an independent copy of the diagram, so any changes you make on the **Cube Builder** tab do not appear in the original diagram.</span></span>|  
|<span data-ttu-id="8abe8-130">キューブで使用されているテーブルのみを表示する</span><span class="sxs-lookup"><span data-stu-id="8abe8-130">Show only the tables that are used in the cube</span></span>|<span data-ttu-id="8abe8-131">**[データ ソース ビュー]** メニューの **[使用されたテーブルのみを表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8abe8-131">On the **Data Source View** menu, click **Show Only Used Tables**.</span></span><br /><br /> <span data-ttu-id="8abe8-132">または</span><span class="sxs-lookup"><span data-stu-id="8abe8-132">- or -</span></span><br /><br /> <span data-ttu-id="8abe8-133">**[データ ソース ビュー]** ペインの背景を右クリックして、 **[使用されたテーブルのみを表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8abe8-133">Right-click the background of the **Data Source View** pane, and then click **Show Only Used Tables**.</span></span>|  
|<span data-ttu-id="8abe8-134">データ ソース ビューのスキーマを編集する</span><span class="sxs-lookup"><span data-stu-id="8abe8-134">Edit the data source view schema</span></span>|<span data-ttu-id="8abe8-135">**[データ ソース ビュー]** メニューで、 **[データ ソース ビューの編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8abe8-135">On the **Data Source View** menu, click **Edit Data Source View**.</span></span><br /><br /> <span data-ttu-id="8abe8-136">または</span><span class="sxs-lookup"><span data-stu-id="8abe8-136">- or -</span></span><br /><br /> <span data-ttu-id="8abe8-137">**[データ ソース ビュー]** ペインの背景を右クリックして、 **[データ ソース ビューの編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8abe8-137">Right-click the background of the **Data Source View** pane, and then click **Edit Data Source View**.</span></span>|  
  
  
