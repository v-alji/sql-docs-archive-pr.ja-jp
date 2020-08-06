---
title: テーブルモデルパーティションの作成および管理 (SSAS テーブル) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: dab72cf0-95bc-4b63-95dc-505b5cd881c1
author: minewiskan
ms.author: owend
ms.openlocfilehash: 58c408c712d6ac4b6bd590bd0f8c895dc1a88700
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643488"
---
# <a name="create-and-manage-tabular-model-partitions-ssas-tabular"></a><span data-ttu-id="f237e-102">テーブル モデル パーティションの作成および管理 (SSAS テーブル)</span><span class="sxs-lookup"><span data-stu-id="f237e-102">Create and Manage Tabular Model Partitions (SSAS Tabular)</span></span>
  <span data-ttu-id="f237e-103">パーティションは、テーブルを論理的な部分に分割します。</span><span class="sxs-lookup"><span data-stu-id="f237e-103">Partitions divide a table into logical parts.</span></span> <span data-ttu-id="f237e-104">各パーティションは、他のパーティションとは個別に処理 (更新) できます。</span><span class="sxs-lookup"><span data-stu-id="f237e-104">Each partition can then be processed (Refreshed) independent of other partitions.</span></span> <span data-ttu-id="f237e-105">モデル作成時にあるモデルのために定義されたパーティションが、配置済みモデルで複製されます。</span><span class="sxs-lookup"><span data-stu-id="f237e-105">Partitions defined for a model during model authoring are duplicated in a deployed model.</span></span> <span data-ttu-id="f237e-106">いったん配置されると、 **の** [パーティション] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ダイアログ ボックスまたはスクリプトを使用して、それらのパーティションを管理できます。</span><span class="sxs-lookup"><span data-stu-id="f237e-106">Once deployed, you can manage those partitions by using the **Partitions** dialog box in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or by using a script.</span></span> <span data-ttu-id="f237e-107">このトピックで説明するタスクで、配置済みモデル用のパーティションを作成、管理する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="f237e-107">Tasks provided in this topic describe how to create and manage partitions for a deployed model.</span></span>  
  
 <span data-ttu-id="f237e-108">このトピックでは、次のタスクについて説明します。</span><span class="sxs-lookup"><span data-stu-id="f237e-108">This topic includes the following tasks:</span></span>  
  
-   [<span data-ttu-id="f237e-109">新しいパーティションを作成するには</span><span class="sxs-lookup"><span data-stu-id="f237e-109">To create a new partition</span></span>](#bkmk_create_new)  
  
-   [<span data-ttu-id="f237e-110">パーティションをコピーするには</span><span class="sxs-lookup"><span data-stu-id="f237e-110">To copy a partition</span></span>](#bkmk_copy)  
  
-   [<span data-ttu-id="f237e-111">2つ以上のパーティションをマージするには</span><span class="sxs-lookup"><span data-stu-id="f237e-111">To merge two or more partitions</span></span>](#bkmk_merge)  
  
-   [<span data-ttu-id="f237e-112">パーティションを削除するには</span><span class="sxs-lookup"><span data-stu-id="f237e-112">To delete a partition</span></span>](#bkmk_delete)  
  
## <a name="tasks"></a><span data-ttu-id="f237e-113">タスク</span><span class="sxs-lookup"><span data-stu-id="f237e-113">Tasks</span></span>  
 <span data-ttu-id="f237e-114">配置済みテーブル モデル データベース用のパーティションを作成、管理するには、 **で** [パーティション] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]ダイアログ ボックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="f237e-114">To create and manage partitions for a deployed tabular model database, you will use the **Partitions** dialog box in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="f237e-115">**で** [パーティション] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]ダイアログ ボックスを表示するには、任意のテーブルを右クリックし、 **[パーティション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f237e-115">To view the **Partitions** dialog box, in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], right-click on a table, and then click **Partitions**.</span></span>  
  
###  <a name="to-create-a-new-partition"></a><a name="bkmk_create_new"></a><span data-ttu-id="f237e-116">新しいパーティションを作成するには</span><span class="sxs-lookup"><span data-stu-id="f237e-116">To create a new partition</span></span>  
  
1.  <span data-ttu-id="f237e-117">**[パーティション]** ダイアログ ボックスで **[新規]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f237e-117">In the **Partitions** dialog box, click the **New** button.</span></span>  
  
2.  <span data-ttu-id="f237e-118">**[パーティション名]** にパーティションの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="f237e-118">In **Partition Name**, type a name for the partition.</span></span> <span data-ttu-id="f237e-119">既定では、既定のパーティション名に番号が付き、新しいパーティションを作成するたびにその番号が増加します。</span><span class="sxs-lookup"><span data-stu-id="f237e-119">By default, the name of the default partition will be incrementally numbered for each new partition.</span></span>  
  
3.  <span data-ttu-id="f237e-120">**[SQL ステートメント]** で、列を定義する SQL クエリ ステートメント、およびパーティションに含める句をクエリ ウィンドウに入力するか貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="f237e-120">In **SQL Statement**, type or paste a SQL query statement that defines the columns and any clauses you want to include in the partition into the query window.</span></span>  
  
4.  <span data-ttu-id="f237e-121">このステートメントを検証するため、 **[構文の確認]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f237e-121">To validate the statement, click **Check Syntax**.</span></span>  
  
###  <a name="to-copy-a-partition"></a><a name="bkmk_copy"></a><span data-ttu-id="f237e-122">パーティションをコピーするには</span><span class="sxs-lookup"><span data-stu-id="f237e-122">To copy a partition</span></span>  
  
1.  <span data-ttu-id="f237e-123">**[パーティション]** ダイアログ ボックスの **[パーティション]** ボックスの一覧で、コピーするパーティションを選択し、 **[コピー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f237e-123">In the **Partitions** dialog box, in the **Partitions** list, select the partition you want to copy, and then click the **Copy** button.</span></span>  
  
2.  <span data-ttu-id="f237e-124">**[パーティション名]** にパーティションの新しい名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="f237e-124">In **Partition Name**, type a new name for the partition.</span></span>  
  
3.  <span data-ttu-id="f237e-125">**[SQL ステートメント]** で、SQL クエリ ステートメントを編集します。</span><span class="sxs-lookup"><span data-stu-id="f237e-125">In **SQL Statement**, edit the SQL query statement.</span></span>  
  
###  <a name="to-merge-two-or-more-partitions"></a><a name="bkmk_merge"></a> <span data-ttu-id="f237e-126">2 つ以上のパーティションをマージするには</span><span class="sxs-lookup"><span data-stu-id="f237e-126">To merge two or more partitions</span></span>  
  
-   <span data-ttu-id="f237e-127">**[パーティション]** ダイアログ ボックスの **[パーティション]** ボックスの一覧で、マージするパーティションを Ctrl キーを押しながらクリックして選択し、 **[マージ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f237e-127">In the **Partitions** dialog box, in the **Partitions** list, use Ctrl+click to select the partitions you want to merge, and then click the **Merge** button.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="f237e-128">パーティションをマージしても、パーティションのメタデータは更新されません。</span><span class="sxs-lookup"><span data-stu-id="f237e-128">Merging partitions does not update the partition metadata.</span></span> <span data-ttu-id="f237e-129">管理者は、マージ後のパーティションの SQL ステートメントを変更し、マージされたパーティション内のすべてのデータが処理操作で確実に処理されるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="f237e-129">Administrators must alter the SQL Statement for the resulting partition to make sure processing operations process all data in the merged partition.</span></span>  
  
###  <a name="to-delete-a-partition"></a><a name="bkmk_delete"></a><span data-ttu-id="f237e-130">パーティションを削除するには</span><span class="sxs-lookup"><span data-stu-id="f237e-130">To delete a partition</span></span>  
  
-   <span data-ttu-id="f237e-131">**[パーティション]** ダイアログ ボックスの **[パーティション]** ボックスの一覧で、削除するパーティションを選択し、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f237e-131">In the **Partitions** dialog box, in the **Partitions** list, select the partition you want to delete, and then click the **Delete** button.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f237e-132">参照</span><span class="sxs-lookup"><span data-stu-id="f237e-132">See Also</span></span>  
 <span data-ttu-id="f237e-133">[SSAS 表形式&#41;&#40;テーブルモデルパーティション](partitions-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="f237e-133">[Tabular Model Partitions &#40;SSAS Tabular&#41;](partitions-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="f237e-134">テーブル モデル パーティションの処理 (SSAS テーブル)</span><span class="sxs-lookup"><span data-stu-id="f237e-134">Process Tabular Model Partitions &#40;SSAS Tabular&#41;</span></span>](process-tabular-model-partitions-ssas-tabular.md)  
  
  
