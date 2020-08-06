---
title: パーティションの書き戻しの設定 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- write-enabled partitions [Analysis Services]
- partitions [Analysis Services], writeback
- partitions [Analysis Services], write-enabled
- writeback [Analysis Services], partitions
ms.assetid: 38bb09cc-2652-4971-8373-0cf468cdc7a6
author: minewiskan
ms.author: owend
ms.openlocfilehash: eaea005bf919545e5d63be481eb3478b286c16d5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641315"
---
# <a name="set-partition-writeback"></a><span data-ttu-id="6020f-102">パーティションの書き戻しの設定</span><span class="sxs-lookup"><span data-stu-id="6020f-102">Set Partition Writeback</span></span>
  <span data-ttu-id="6020f-103">メジャー グループを書き込み許可にすると、エンド ユーザーはキューブを参照しているときにキューブ データを変更できます。この場合、変更内容は、キューブ データやソース データではなく、書き戻しテーブルという別個のテーブルに保存されます。</span><span class="sxs-lookup"><span data-stu-id="6020f-103">If you write-enable a measure group, end users can change cube data while they browse it, where changes are saved in a separate table called a writeback table, not in the cube data or source data.</span></span> <span data-ttu-id="6020f-104">書き込み許可パーティションを参照しているエンド ユーザーは、そのパーティションの書き戻しテーブルを見れば、すべての変更の最終結果を確認できます。</span><span class="sxs-lookup"><span data-stu-id="6020f-104">End users who browse a write-enabled partition see the net effect of all changes in the writeback table for the partition.</span></span>  
  
 <span data-ttu-id="6020f-105">書き戻しデータは、参照または削除できます。</span><span class="sxs-lookup"><span data-stu-id="6020f-105">You can browse or delete writeback data.</span></span> <span data-ttu-id="6020f-106">また、書き戻しデータをパーティションに変換することもできます。</span><span class="sxs-lookup"><span data-stu-id="6020f-106">You can also convert writeback data to a partition.</span></span> <span data-ttu-id="6020f-107">書き込み許可パーティションの場合、キューブ ロールを使用して、ユーザーまたはユーザー グループに読み取り/書き込みアクセス権を許可し、パーティション内の特定のセルまたはセル グループへのアクセスを制限できます。</span><span class="sxs-lookup"><span data-stu-id="6020f-107">On a write-enabled partition, you can use cube roles to grant read/write access to users and groups of users, and to limit access to specific cells or groups of cells in the partition.</span></span>  
  
 <span data-ttu-id="6020f-108">書き戻しに関する簡単な紹介ビデオについては、「 [Excel 2010 での Analysis Services への書き戻し](https://go.microsoft.com/fwlink/p/?LinkId=394951)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6020f-108">For a short video introduction to writeback, see [Excel 2010 Writeback to Analysis Services](https://go.microsoft.com/fwlink/p/?LinkId=394951).</span></span> <span data-ttu-id="6020f-109">書き戻し機能の詳細については、ブログ投稿「 [Analysis Services を使用した書き戻しアプリケーションの構築 (ブログ)](https://go.microsoft.com/fwlink/?LinkId=394977)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6020f-109">A more detailed exploration of this feature is available through this blog post series, [Building a Writeback Application with Analysis Services (blog)](https://go.microsoft.com/fwlink/?LinkId=394977).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6020f-110">書き戻しは、SQL Server リレーショナル データベースとデータ マート、および [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 多次元モデルでのみサポートされます。</span><span class="sxs-lookup"><span data-stu-id="6020f-110">Writeback is supported for SQL Server relational databases and data marts only, and only for [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] multidimensional models.</span></span>  
  
## <a name="how-to-write-enable-a-partition"></a><span data-ttu-id="6020f-111">パーティションを書き込み許可にする方法</span><span class="sxs-lookup"><span data-stu-id="6020f-111">How to write-enable a partition</span></span>  
 <span data-ttu-id="6020f-112">パーティションのメジャー グループを書き込み許可にするには、 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] や [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]のキューブ デザイナーでパーティション自体に書き込み許可を設定します。</span><span class="sxs-lookup"><span data-stu-id="6020f-112">You can write-enable a partition's measure groups by write-enabling the partition itself in Cube Designer in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] or [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
-   <span data-ttu-id="6020f-113">キューブ デザイナーの [パーティション] タブで、パーティションを右クリックし、 **[書き戻しの設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6020f-113">In Cube Designer, in the Partitions tab, right-click a partition and choose **Writeback Settings**.</span></span>  
  
-   <span data-ttu-id="6020f-114">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]で、データベース | キューブ | メジャー グループを展開し、 **[書き戻し]** を右クリックして、 **[書き戻しの有効化]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6020f-114">In [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], expand the database | cube | measure group, and then right-click **Writeback** and choose **Enable Writeback**.</span></span>  
  
 <span data-ttu-id="6020f-115">書き戻しは、SUM 集計を使用するメジャーに対してのみサポートされます。</span><span class="sxs-lookup"><span data-stu-id="6020f-115">Writeback is only supported for measures that use the SUM aggregation.</span></span> <span data-ttu-id="6020f-116">AdventureWorks サンプル データベースでは、Sales Targets メジャー グループを使用して、書き戻しの動作をテストできます。</span><span class="sxs-lookup"><span data-stu-id="6020f-116">In the AdventureWorks sample database, you can use the Sales Targets measure group to test writeback behaviors.</span></span>  
  
 <span data-ttu-id="6020f-117">パーティションを書き込み許可する場合は、書き戻しテーブルを保存するためのテーブル名とデータ ソースを指定します。</span><span class="sxs-lookup"><span data-stu-id="6020f-117">When you write-enable a partition, you specify a table name and a data source for storing the write-back table.</span></span> <span data-ttu-id="6020f-118">その後のメジャー グループの変更は、このテーブルに記録されます。</span><span class="sxs-lookup"><span data-stu-id="6020f-118">Any subsequent changes to the measure group are recorded in this table.</span></span>  
  
## <a name="browse-writeback-data-in-a-partition"></a><span data-ttu-id="6020f-119">パーティションの書き戻しデータの参照</span><span class="sxs-lookup"><span data-stu-id="6020f-119">Browse writeback data in a partition</span></span>  
 <span data-ttu-id="6020f-120">**[データの参照]** ダイアログ ボックスでは、キューブの書き戻しテーブルの内容を参照できます。このダイアログ ボックスにアクセスするには、キューブ デザイナーの **[パーティション]** タブで、書き込み許可パーティションを右クリックします。</span><span class="sxs-lookup"><span data-stu-id="6020f-120">You can browse the contents of a cube's writeback table in the **Browse Data** dialog box, which you can access by right-clicking a write-enabled partition on the **Partitions** tab in Cube Designer.</span></span>  
  
## <a name="delete-writeback-data-or-disable-writeback"></a><span data-ttu-id="6020f-121">書き戻しデータの削除と書き戻しの無効化</span><span class="sxs-lookup"><span data-stu-id="6020f-121">Delete writeback data or disable writeback</span></span>  
 <span data-ttu-id="6020f-122">書き戻しデータを削除すると、ライトバック キャッシュが消去されます。つまり、データが削除されるとすぐに、追加の書き戻し作業が白紙の状態から実行されます。</span><span class="sxs-lookup"><span data-stu-id="6020f-122">Deleting writeback data clears the writeback cache; as soon as that data is deleted, additional writeback work is performed on a clean slate.</span></span> <span data-ttu-id="6020f-123">キューブ パーティションの書き戻しを無効にすると、そのパーティションの書き戻しがオフになります。</span><span class="sxs-lookup"><span data-stu-id="6020f-123">Disabling writeback for a cube partition simply turns off writeback for that partition.</span></span>  
  
## <a name="convert-writeback-data-to-a-partition"></a><span data-ttu-id="6020f-124">書き戻しデータからパーティションへの変換</span><span class="sxs-lookup"><span data-stu-id="6020f-124">Convert writeback data to a partition</span></span>  
 <span data-ttu-id="6020f-125">パーティションの書き戻しテーブルに含まれるデータは、パーティションに変換できます。</span><span class="sxs-lookup"><span data-stu-id="6020f-125">You can convert the data in a partition's writeback table to a partition.</span></span> <span data-ttu-id="6020f-126">この手順により、書き戻しテーブルは新しいパーティションのファクト テーブルになります。</span><span class="sxs-lookup"><span data-stu-id="6020f-126">This procedure causes the writeback table to become the new partition's fact table.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="6020f-127">パーティションの使い方が不適切な場合、キューブ データが不正確になることがあります。</span><span class="sxs-lookup"><span data-stu-id="6020f-127">Incorrect use of partitions can result in inaccurate cube data.</span></span> <span data-ttu-id="6020f-128">詳細については、「 [ローカル パーティションの作成と管理 (Analysis Services)](create-and-manage-a-local-partition-analysis-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6020f-128">For more information, see [Create and Manage a Local Partition &#40;Analysis Services&#41;](create-and-manage-a-local-partition-analysis-services.md).</span></span>  
  
 <span data-ttu-id="6020f-129">書き戻しデータ テーブルをパーティションに変換すると、パーティションの書き込みも無効になります。</span><span class="sxs-lookup"><span data-stu-id="6020f-129">Converting the writeback data table to a partition also write-disables the partition.</span></span> <span data-ttu-id="6020f-130">パーティションのセルの無制限読み取り/書き込みポリシーと読み取り/書き込み (Read/Write) 権限はすべて無効になり、エンド ユーザーは表示されるキューブ データを変更できなくなります。</span><span class="sxs-lookup"><span data-stu-id="6020f-130">All unrestricted read/write policies and read/write permissions for the partition's cells are disabled, and end users will not be able to change displayed cube data.</span></span> <span data-ttu-id="6020f-131">無制限読み取り/書き込みポリシーまたは読み取り/書き込み権限が無効であるエンド ユーザーでもキューブを参照できます。読み取り (Read) 権限と条件付き読み取り (Read-Contingent) 権限は影響を受けません。</span><span class="sxs-lookup"><span data-stu-id="6020f-131">(End users with disabled unrestricted read/write policies or disabled read/write permissions will still be able to browse the cube.) Read and read-contingent permissions are not affected.</span></span>  
  
 <span data-ttu-id="6020f-132">書き戻しデータをパーティションに変換するには、 **[パーティションに変換]** ダイアログ ボックスを使用します。このダイアログ ボックスにアクセスするには、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で書き込み可能なパーティションの書き戻しテーブルを右クリックします。</span><span class="sxs-lookup"><span data-stu-id="6020f-132">To convert writeback data to a partition, use the **Convert to Partition** dialog box, which is accessed by right-clicking the writeback table for a write-enabled partition in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="6020f-133">ここで、パーティションの名前と、パーティションの集計のデザインを作成後に行うか同時に行うかを指定します。</span><span class="sxs-lookup"><span data-stu-id="6020f-133">You specify a name for the partition and whether to design the aggregation for the partition later or at the same time that you create it.</span></span> <span data-ttu-id="6020f-134">パーティションの選択と同時に集計を作成するには、既存のパーティションから集計のデザインをコピーするように選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6020f-134">To create the aggregation at the same time you choose the partition, you must choose to copy the aggregation design from an existing partition.</span></span> <span data-ttu-id="6020f-135">これは、必ずというわけではありませんが、通常は現在の書き戻しパーティションです。</span><span class="sxs-lookup"><span data-stu-id="6020f-135">This is normally, but not necessarily, the current writeback partition.</span></span> <span data-ttu-id="6020f-136">また、パーティションの作成と同時に処理するように選択することもできます。</span><span class="sxs-lookup"><span data-stu-id="6020f-136">You can also choose to process the partition at the same time that you create it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6020f-137">参照</span><span class="sxs-lookup"><span data-stu-id="6020f-137">See Also</span></span>  
 <span data-ttu-id="6020f-138">[書き込み許可パーティション](../multidimensional-models-olap-logical-cube-objects/partitions-write-enabled-partitions.md) </span><span class="sxs-lookup"><span data-stu-id="6020f-138">[Write-Enabled Partitions](../multidimensional-models-olap-logical-cube-objects/partitions-write-enabled-partitions.md) </span></span>  
 <span data-ttu-id="6020f-139">[Excel 2010 のセルレベルで OLAP キューブへの書き戻しを有効にする](https://go.microsoft.com/fwlink/p/?LinkId=394952) </span><span class="sxs-lookup"><span data-stu-id="6020f-139">[Enabling Write-back to an OLAP Cube at Cell Level in Excel 2010](https://go.microsoft.com/fwlink/p/?LinkId=394952) </span></span>  
 [<span data-ttu-id="6020f-140">Analysis Services の書き戻しを使用したデータ入力の有効化と保護</span><span class="sxs-lookup"><span data-stu-id="6020f-140">Enabling and Securing Data Entry with Analysis Services Writeback</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=394953)  
  
  
