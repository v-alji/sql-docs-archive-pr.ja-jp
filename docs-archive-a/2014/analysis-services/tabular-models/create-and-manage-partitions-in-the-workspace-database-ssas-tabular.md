---
title: ワークスペースデータベースでのパーティションの作成と管理 (SSAS テーブル) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.partitionmgr.f1
ms.assetid: 0b3027d6-652b-4eb3-a197-58b25df65218
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3824dd4763e516dc5e8e34a9ec815d3969f4eb79
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634666"
---
# <a name="create-and-manage-partitions-in-the-workspace-database-ssas-tabular"></a><span data-ttu-id="25076-102">ワークスペース データベースのパーティションの作成と管理 (SSAS テーブル)</span><span class="sxs-lookup"><span data-stu-id="25076-102">Create and Manage Partitions in the Workspace Database (SSAS Tabular)</span></span>
  <span data-ttu-id="25076-103">パーティションは、テーブルを論理的な部分に分割します。</span><span class="sxs-lookup"><span data-stu-id="25076-103">Partitions divide a table into logical parts.</span></span> <span data-ttu-id="25076-104">その後、各パーティションは、個別に、または他のパーティションと並列に処理 (更新) することができます。</span><span class="sxs-lookup"><span data-stu-id="25076-104">Each partition can then be processed (Refreshed) independently or in parallel with other partitions.</span></span> <span data-ttu-id="25076-105">パーティションによって、大規模なデータベースのスケーラビリティと管理性を向上させることができます。</span><span class="sxs-lookup"><span data-stu-id="25076-105">Partitions can improve scalability and manageability of large databases.</span></span> <span data-ttu-id="25076-106">既定では、各テーブルに 1 つのパーティションがあり、すべての列がこのパーティションに含まれます。</span><span class="sxs-lookup"><span data-stu-id="25076-106">By default, each table has one partition that includes all columns.</span></span> <span data-ttu-id="25076-107">このトピックのタスクでは、の [**パーティションマネージャー** ] ダイアログボックスを使用して、モデルワークスペースデータベースでパーティションを作成および管理する方法について説明します。[!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25076-107">Tasks in this topic describe how to create and manage partitions in the model workspace database by using the **Partition Manager** dialog box in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]</span></span>  
  
 <span data-ttu-id="25076-108">別の Analysis Services インスタンスにモデルが配置された後、データベース管理者は、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を使用して (配置済みの) モデルでパーティションを作成し管理できます。</span><span class="sxs-lookup"><span data-stu-id="25076-108">After a model has been deployed to another Analysis Services instance, database administrators can create and manage partitions in the (deployed) model by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="25076-109">詳細については、「[テーブル モデル パーティションの作成および管理 (SSAS テーブル)](partitions-ssas-tabular.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="25076-109">For more information, see [Create and Manage Tabular Model Partitions &#40;SSAS Tabular&#41;](partitions-ssas-tabular.md).</span></span>  
  
 <span data-ttu-id="25076-110">このトピックでは、次のタスクについて説明します。</span><span class="sxs-lookup"><span data-stu-id="25076-110">This topic includes the following tasks:</span></span>  
  
-   [<span data-ttu-id="25076-111">新しいパーティションを作成するには</span><span class="sxs-lookup"><span data-stu-id="25076-111">To create a new partition</span></span>](#bkmk_create_new)  
  
-   [<span data-ttu-id="25076-112">パーティションをコピーするには</span><span class="sxs-lookup"><span data-stu-id="25076-112">To copy a partition</span></span>](#bkmk_copy)  
  
-   [<span data-ttu-id="25076-113">パーティションを削除するには</span><span class="sxs-lookup"><span data-stu-id="25076-113">To delete a partition</span></span>](#bkmk_delete)  
  
> [!NOTE]  
>  <span data-ttu-id="25076-114">[パーティション マネージャー] ダイアログ ボックスを使用して、モデル ワークスペース データベースのパーティションを結合することはできません。</span><span class="sxs-lookup"><span data-stu-id="25076-114">You cannot merge partitions in the model workspace database by using the Partition Manager dialog box.</span></span> <span data-ttu-id="25076-115">パーティションが結合できるのは、配置されたモデルで [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を使用した場合のみです。</span><span class="sxs-lookup"><span data-stu-id="25076-115">Partitions can be merged in a deployed model only by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="25076-116">タスク</span><span class="sxs-lookup"><span data-stu-id="25076-116">Tasks</span></span>  
 <span data-ttu-id="25076-117">パーティションの作成と管理には、 **[パーティション マネージャー]** ダイアログ ボックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="25076-117">To create and manage partitions, you will use the **Partitions Manager** dialog box.</span></span> <span data-ttu-id="25076-118">**[パーティション マネージャー]** ダイアログ ボックスを表示するには、 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]の **[テーブル]** メニューをクリックし、 **[パーティション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="25076-118">To view the **Partitions Manager** dialog box, in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], click the **Table** menu, and then click **Partitions**.</span></span>  
  
###  <a name="to-create-a-new-partition"></a><a name="bkmk_create_new"></a><span data-ttu-id="25076-119">新しいパーティションを作成するには</span><span class="sxs-lookup"><span data-stu-id="25076-119">To create a new partition</span></span>  
  
1.  <span data-ttu-id="25076-120">モデル デザイナーで、パーティションを定義するテーブルを選択します。</span><span class="sxs-lookup"><span data-stu-id="25076-120">In the model designer, select the table for which you want to define a partition.</span></span>  
  
2.  <span data-ttu-id="25076-121">**[テーブル]** メニューをクリックし、 **[パーティション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="25076-121">Click on the **Table** menu, and then click **Partitions**.</span></span>  
  
3.  <span data-ttu-id="25076-122">**[パーティション マネージャー]** の **[テーブル]** ボックスの一覧で、パーティション分割するテーブルを確認または選択し、 **[新規作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="25076-122">In **Partition Manager**, in the **Table** listbox, verify or select the table you want to partition, and then click **New**.</span></span>  
  
4.  <span data-ttu-id="25076-123">**[パーティション名]** にパーティションの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="25076-123">In **Partition Name**, type a name for the partition.</span></span> <span data-ttu-id="25076-124">既定では、既定のパーティション名に番号が付き、新しいパーティションを作成するたびにその番号が増加します。</span><span class="sxs-lookup"><span data-stu-id="25076-124">By default, the name of the default partition will be incrementally numbered for each new partition.</span></span>  
  
5.  <span data-ttu-id="25076-125">テーブル プレビュー モードを使用するか、クエリ エディター モードを使用して作成した SQL クエリを使用すると、パーティションに含める行と列を選択できます。</span><span class="sxs-lookup"><span data-stu-id="25076-125">You can select the rows and columns to be included in the partition by using Table Preview mode or by using a SQL query created using Query Editor mode.</span></span>  
  
     <span data-ttu-id="25076-126">テーブル プレビュー モード (既定) を使用するには、プレビュー ウィンドウの右上隅にある **[テーブル プレビュー]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="25076-126">To use Table Preview mode (default), click the **Table Preview** button near the upper-right corner of the preview window.</span></span> <span data-ttu-id="25076-127">列名の横のチェック ボックスをオンにして、パーティションに含める列を選択します。</span><span class="sxs-lookup"><span data-stu-id="25076-127">Select the columns you want to include in the partition by selecting the checkbox next to the column name.</span></span> <span data-ttu-id="25076-128">行をフィルター選択するには、セル値を右クリックし、 **[選択したセル値でフィルター]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="25076-128">To filter rows, right click a cell value, and click **Filter by Selected Cell Value**.</span></span>  
  
     <span data-ttu-id="25076-129">SQL ステートメントを使用するには、プレビュー ウィンドウの右上隅にある **[クエリ エディター]** ボタンをクリックしてから、クエリ ウィンドウに SQL クエリ ステートメントを入力するか貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="25076-129">To use a SQL statement, click the **Query Editor** button near the upper-right corner of the preview window, then type or paste a SQL query statement into the query window.</span></span> <span data-ttu-id="25076-130">ステートメントを検証するには、 **[検証]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="25076-130">To validate your statement, click **Validate**.</span></span> <span data-ttu-id="25076-131">クエリ デザイナーを使用するには、 **[デザイン]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="25076-131">To use the Query Designer, click **Design**.</span></span>  
  
###  <a name="to-copy-a-partition"></a><a name="bkmk_copy"></a><span data-ttu-id="25076-132">パーティションをコピーするには</span><span class="sxs-lookup"><span data-stu-id="25076-132">To copy a partition</span></span>  
  
1.  <span data-ttu-id="25076-133">**[パーティション マネージャー]** の **[テーブル]** ボックスの一覧で、コピーするパーティションが含まれているテーブルを確認または選択します。</span><span class="sxs-lookup"><span data-stu-id="25076-133">In **Partition Manager**, in the **Table** listbox, verify or select the table that contains the partition you want to copy.</span></span>  
  
2.  <span data-ttu-id="25076-134">**[パーティション]** リストでコピーするパーティションを選択し、 **[コピー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="25076-134">In the **Partitions** list, select the partition you want to copy and then click **Copy**.</span></span>  
  
3.  <span data-ttu-id="25076-135">**[パーティション名]** にパーティションの新しい名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="25076-135">In **Partition Name**, type a new name for the partition.</span></span>  
  
###  <a name="to-delete-a-partition"></a><a name="bkmk_delete"></a><span data-ttu-id="25076-136">パーティションを削除するには</span><span class="sxs-lookup"><span data-stu-id="25076-136">To delete a partition</span></span>  
  
1.  <span data-ttu-id="25076-137">**[パーティション マネージャー]** の **[テーブル]** ボックスの一覧で、削除するパーティションが含まれているテーブルを確認または選択します。</span><span class="sxs-lookup"><span data-stu-id="25076-137">In **Partition Manager**, in the **Table** listbox, verify or select the table that contains the partition you want to delete.</span></span>  
  
2.  <span data-ttu-id="25076-138">**[パーティション]** リストで削除するパーティションを選択し、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="25076-138">In the **Partitions** list, select the partition you want to delete and then click **Delete**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25076-139">参照</span><span class="sxs-lookup"><span data-stu-id="25076-139">See Also</span></span>  
 <span data-ttu-id="25076-140">[SSAS 表形式のパーティション &#40;&#41;](partitions-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="25076-140">[Partitions &#40;SSAS Tabular&#41;](partitions-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="25076-141">SSAS 表形式&#41;&#40;ワークスペースデータベースのパーティションを処理する</span><span class="sxs-lookup"><span data-stu-id="25076-141">Process Partitions in the Workspace Database &#40;SSAS Tabular&#41;</span></span>](process-partitions-in-the-workspace-database-ssas-tabular.md)  
  
  
