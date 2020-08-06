---
title: Microsoft レプリケーション競合表示モジュール (トランザクション レプリケーション) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.replconflictviewer.cvqueued.f1
ms.assetid: eec59d8e-cadb-4623-a31f-9f42ec09c97f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8cc3f2ea3d1d2b29fba9c9d9121e23bf4bcd88bd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87630938"
---
# <a name="microsoft-replication-conflict-viewer-transactional-replication"></a><span data-ttu-id="8c9d6-102">Microsoft レプリケーション競合表示モジュール (トランザクション レプリケーション)</span><span class="sxs-lookup"><span data-stu-id="8c9d6-102">Microsoft Replication Conflict Viewer (Transactional Replication)</span></span>
  <span data-ttu-id="8c9d6-103">レプリケーション競合表示モジュールを使用すると、ピア ツー ピア トランザクション レプリケーション、およびキュー更新サブスクリプションを使用するトランザクション レプリケーションの同期中に発生した競合を表示できます。</span><span class="sxs-lookup"><span data-stu-id="8c9d6-103">The Replication Conflict Viewer enables you to view conflicts that have occurred during synchronization for peer-to-peer transactional replication and transactional replication with queued updating subscriptions.</span></span> <span data-ttu-id="8c9d6-104">詳細については、「[トランザクション パブリケーションのデータの競合の表示 &#40;SQL Server Management Studio&#41;](view-data-conflicts-for-transactional-publications-sql-server-management-studio.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8c9d6-104">For more information, see [View Data Conflicts for Transactional Publications &#40;SQL Server Management Studio&#41;](view-data-conflicts-for-transactional-publications-sql-server-management-studio.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8c9d6-105">レプリケーション競合表示モジュールでは、マージ レプリケーションおよびトランザクション レプリケーションで発生した競合が表示されます。</span><span class="sxs-lookup"><span data-stu-id="8c9d6-105">The Replication Conflict Viewer displays conflicts that occur in merge replication and in transactional replication.</span></span> <span data-ttu-id="8c9d6-106">トランザクション レプリケーションの場合は、レプリケーション競合表示モジュールを使用して競合データを表示することはできますが、競合に対して別の解決策を選択することはできません。</span><span class="sxs-lookup"><span data-stu-id="8c9d6-106">For transactional replication, you can use Replication Conflict Viewer to view conflict data, but you cannot choose a different resolution for the conflict.</span></span>  
  
## <a name="options"></a><span data-ttu-id="8c9d6-107">Options</span><span class="sxs-lookup"><span data-stu-id="8c9d6-107">Options</span></span>  
 <span data-ttu-id="8c9d6-108">レプリケーション競合表示モジュールは 2 つのセクションに分かれています。</span><span class="sxs-lookup"><span data-stu-id="8c9d6-108">The Replication Conflict Viewer is divided into two sections.</span></span> <span data-ttu-id="8c9d6-109">ダイアログ ボックスの上側のセクションには、選択されたテーブルの競合の一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="8c9d6-109">The upper section of the dialog box shows the conflict list for the selected table.</span></span> <span data-ttu-id="8c9d6-110">競合の一覧の項目をクリックすると、競合の詳細がダイアログ ボックスの下側のセクションに表示されます。</span><span class="sxs-lookup"><span data-stu-id="8c9d6-110">When you click an item in the conflict list, the details of the conflict are displayed in the lower section of the dialog box.</span></span>  
  
 <span data-ttu-id="8c9d6-111">下側のセクションの競合データは、2 つの対応する列 (**[競合で優先されたデータ]** と **[競合で優先されなかったデータ]**) に表示されます。</span><span class="sxs-lookup"><span data-stu-id="8c9d6-111">The conflict data in the lower section is displayed in two corresponding columns (**Conflict Winner** and **Conflict Loser**).</span></span> <span data-ttu-id="8c9d6-112">更新されたデータと削除されたデータの間で競合が発生した場合、競合で削除された側にデータが表示されない場合があります。</span><span class="sxs-lookup"><span data-stu-id="8c9d6-112">If the conflict is between updated and deleted data, there may be no data to show for the deleted side of the conflict.</span></span> <span data-ttu-id="8c9d6-113">この場合、レプリケーション競合表示モジュールでは、その行が 1 か所では削除され別の箇所では更新されたことを示すメッセージが列の 1 つに表示されます。</span><span class="sxs-lookup"><span data-stu-id="8c9d6-113">In this case, the Replication Conflict Viewer displays a message in one of the columns, indicating the row was deleted at one location and updated at another.</span></span> <span data-ttu-id="8c9d6-114">また、提案された解決策についても示されます。</span><span class="sxs-lookup"><span data-stu-id="8c9d6-114">It also indicates the suggested resolution.</span></span>  
  
 <span data-ttu-id="8c9d6-115">**[データベース]**</span><span class="sxs-lookup"><span data-stu-id="8c9d6-115">**Database**</span></span>  
 <span data-ttu-id="8c9d6-116">競合があるパブリケーションを含むデータベースを選択します。</span><span class="sxs-lookup"><span data-stu-id="8c9d6-116">Choose a database that includes publications with conflicts.</span></span>  
  
 <span data-ttu-id="8c9d6-117">**Publication**</span><span class="sxs-lookup"><span data-stu-id="8c9d6-117">**Publication**</span></span>  
 <span data-ttu-id="8c9d6-118">競合があるテーブルを含むパブリケーションを選択します。</span><span class="sxs-lookup"><span data-stu-id="8c9d6-118">Choose a publication that includes tables with conflicts.</span></span>  
  
 <span data-ttu-id="8c9d6-119">**テーブル**</span><span class="sxs-lookup"><span data-stu-id="8c9d6-119">**Table**</span></span>  
 <span data-ttu-id="8c9d6-120">競合を含むテーブルを選択します。</span><span class="sxs-lookup"><span data-stu-id="8c9d6-120">Choose a table that includes conflicts.</span></span>  
  
 <span data-ttu-id="8c9d6-121">**[フィルターの定義]**</span><span class="sxs-lookup"><span data-stu-id="8c9d6-121">**Define Filter**</span></span>  
 <span data-ttu-id="8c9d6-122">**[フィルターの定義]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="8c9d6-122">Click to open the **Define Filters** dialog box.</span></span>  
  
 <span data-ttu-id="8c9d6-123">**[フィルターの適用または削除]**</span><span class="sxs-lookup"><span data-stu-id="8c9d6-123">**Apply or Remove Filter**</span></span>  
 <span data-ttu-id="8c9d6-124">**[フィルターの定義]** ダイアログ ボックスで定義されたフィルターを適用または削除します。</span><span class="sxs-lookup"><span data-stu-id="8c9d6-124">Click to apply or remove a filter that has been defined in the **Define Filters** dialog box.</span></span>  
  
 <span data-ttu-id="8c9d6-125">**[すべて選択]**</span><span class="sxs-lookup"><span data-stu-id="8c9d6-125">**Select All**</span></span>  
 <span data-ttu-id="8c9d6-126">グリッドに一覧表示されたすべての競合を選択します。</span><span class="sxs-lookup"><span data-stu-id="8c9d6-126">Click to select all conflicts listed in the grid.</span></span>  
  
 <span data-ttu-id="8c9d6-127">**[なし] を選択**</span><span class="sxs-lookup"><span data-stu-id="8c9d6-127">**Select None**</span></span>  
 <span data-ttu-id="8c9d6-128">グリッドに一覧表示されたすべての競合の選択を解除します。</span><span class="sxs-lookup"><span data-stu-id="8c9d6-128">Click to deselect all conflicts listed in the grid.</span></span>  
  
 <span data-ttu-id="8c9d6-129">**削除**</span><span class="sxs-lookup"><span data-stu-id="8c9d6-129">**Remove**</span></span>  
 <span data-ttu-id="8c9d6-130">選択された競合をビューアーから削除し、関連するメタデータをレプリケーション システム テーブルから削除します。</span><span class="sxs-lookup"><span data-stu-id="8c9d6-130">Click to remove selected conflicts from the viewer and their associated metadata from the replication system tables.</span></span>  
  
 <span data-ttu-id="8c9d6-131">**[すべての列を表示]**</span><span class="sxs-lookup"><span data-stu-id="8c9d6-131">**Show all columns**</span></span>  
 <span data-ttu-id="8c9d6-132">テーブルのすべての列を表示します。</span><span class="sxs-lookup"><span data-stu-id="8c9d6-132">Select to show all columns of the table.</span></span>  
  
 <span data-ttu-id="8c9d6-133">**[最初の 5 列および競合データが含まれている列を表示]**</span><span class="sxs-lookup"><span data-stu-id="8c9d6-133">**Show first five columns and other columns with conflicting data**</span></span>  
 <span data-ttu-id="8c9d6-134">最初の 5 列および競合データが含まれている列を表示します。</span><span class="sxs-lookup"><span data-stu-id="8c9d6-134">Select to display the first five columns and any columns that have conflicts.</span></span> <span data-ttu-id="8c9d6-135">これは、テーブルに多数の列があり、競合を解決するのに最も関連する列のみを表示する場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="8c9d6-135">This is helpful when the table has a large number of columns, but you want to see only the columns most relevant to resolving the conflict.</span></span> <span data-ttu-id="8c9d6-136">主キーや名前フィールドなど、行を識別するフィールドはテーブルの最初の列にある場合が多いため、このビューでは最初の 5 列が必ず表示されます。</span><span class="sxs-lookup"><span data-stu-id="8c9d6-136">The first five columns are always included in this view, as fields that identify a row, such as the primary key or name fields, are often among the first columns of the table.</span></span>  
  
 <span data-ttu-id="8c9d6-137">**列情報の表示**(**...**)</span><span class="sxs-lookup"><span data-stu-id="8c9d6-137">**Display Column Information** (**...**)</span></span>  
 <span data-ttu-id="8c9d6-138">列の情報である **[テーブル名]**、 **[列名]**、 **[データ型]**、および **[列の値]** を表示します。</span><span class="sxs-lookup"><span data-stu-id="8c9d6-138">Click to view column information: **Table Name**, **Column Name**, **Data Type**, and **Column Value**.</span></span>  
  
 <span data-ttu-id="8c9d6-139">**[競合の詳細をログに記録]**</span><span class="sxs-lookup"><span data-stu-id="8c9d6-139">**Log the details of the conflict**</span></span>  
 <span data-ttu-id="8c9d6-140">このボックスをオンにすると、競合の詳細がファイルに記録されます。</span><span class="sxs-lookup"><span data-stu-id="8c9d6-140">Check this box to log the details of the conflict to a file.</span></span> <span data-ttu-id="8c9d6-141">ファイルの場所を指定するには、 **[表示]** メニューをポイントし、 **[オプション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8c9d6-141">To specify a location for the file, point to the **View** menu and click **Options**.</span></span> <span data-ttu-id="8c9d6-142">値を入力するか、参照ボタン (**[...]**) をクリックして適切なファイルに移動します。</span><span class="sxs-lookup"><span data-stu-id="8c9d6-142">Enter a value, or click the browse (**...**) and navigate to the appropriate file.</span></span> <span data-ttu-id="8c9d6-143">**[OK]** をクリックして、 **[オプション]** ダイアログ ボックスを終了します。</span><span class="sxs-lookup"><span data-stu-id="8c9d6-143">Click **OK** to exit the **Options** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c9d6-144">参照</span><span class="sxs-lookup"><span data-stu-id="8c9d6-144">See Also</span></span>  
 <span data-ttu-id="8c9d6-145">[ピアツーピアレプリケーションでの競合の検出](transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md) </span><span class="sxs-lookup"><span data-stu-id="8c9d6-145">[Conflict Detection in Peer-to-Peer Replication](transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md) </span></span>  
 [<span data-ttu-id="8c9d6-146">トランザクション パブリケーションのデータの競合の表示 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="8c9d6-146">View Data Conflicts for Transactional Publications &#40;SQL Server Management Studio&#41;</span></span>](view-data-conflicts-for-transactional-publications-sql-server-management-studio.md)  
  
  
