---
title: パーティションの管理ウィザードの F1 ヘルプ | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.managepartition.getstart.f1
- sql12.swb.managepartition.selectoutput.f1
- sql12.swb.managepartition.partitionaction.f1
- sql12.swb.managepartition.switchout.f1
- sql12.swb.managepartition.summary.f1
- sql12.swb.managepartition.createjob.f1
- sql12.swb.managepartition.stagingtable.f1
- sql12.swb.managepartition.progress.f1
- sql12.swb.managepartition.switchin.f1
- sql12.swb.managepartition.selectswitchtables.f1
helpviewer_keywords:
- wizards [SQL Server Management Studio] See Manage Partition Wizard
ms.assetid: e2478d26-dea4-428d-98c5-aad2d2a30da8
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 09b3e774168e9a48a0a387c3474b29f96081d875
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713105"
---
# <a name="manage-partition-wizard-f1-help"></a><span data-ttu-id="c9982-102">パーティションの管理ウィザードの F1 ヘルプ</span><span class="sxs-lookup"><span data-stu-id="c9982-102">Manage Partition Wizard F1 Help</span></span>
  <span data-ttu-id="c9982-103">**パーティションの管理ウィザード** を使用すると、パーティションの切り替えやスライディング ウィンドウ シナリオの実装によって、既存のパーティション テーブルを管理および変更することができます。</span><span class="sxs-lookup"><span data-stu-id="c9982-103">Use the **Manage Partition Wizard** to manage and modify existing partitioned tables through partition switching or the implementation of a sliding window scenario.</span></span> <span data-ttu-id="c9982-104">このウィザードによって、パーティションの管理が容易になり、テーブル内外へのデータの通常の移行が簡単になります。</span><span class="sxs-lookup"><span data-stu-id="c9982-104">This wizard can ease the management of your partitions and simplify the regular migration of data in and out of your tables.</span></span>  
  
### <a name="to-start-the-manage-partition-wizard"></a><span data-ttu-id="c9982-105">パーティションの管理ウィザードを起動するには</span><span class="sxs-lookup"><span data-stu-id="c9982-105">To start the Manage Partition Wizard</span></span>  
  
-   <span data-ttu-id="c9982-106">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、データベースを選択し、パーティションを作成するテーブルを右クリックして **[ストレージ]** をポイントし、 **[パーティションの管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c9982-106">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], select the database, right-click the table on which you want to create partitions, point to **Storage**, and then click **Manage Partition**.</span></span>  
  
     <span data-ttu-id="c9982-107">`Note`[**パーティションの管理**] が使用できない場合は、パーティションを含まないテーブルを選択している可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c9982-107">`Note` If **Manage Partition** is unavailable, you may have selected a table that does not contain partitions.</span></span> <span data-ttu-id="c9982-108">**[ストレージ]** サブメニューの **[パーティションの作成]** をクリックし、 **パーティションの作成ウィザード** を使用してテーブルにパーティションを作成してください。</span><span class="sxs-lookup"><span data-stu-id="c9982-108">Click **Create Partition** on the **Storage** submenu and use the **Create Partition Wizard** to create partitions in your table.</span></span>  
  
 <span data-ttu-id="c9982-109">パーティション インデックスについての一般情報については、「 [パーティション テーブルとパーティション インデックス](partitioned-tables-and-indexes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c9982-109">For general information about partitions and indexes, see [Partitioned Tables and Indexes](partitioned-tables-and-indexes.md).</span></span>  
  
 <span data-ttu-id="c9982-110">ここでは、 **パーティションの管理ウィザード**を使用してパーティションを管理、変更、および実装する場合に必要な情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="c9982-110">This section provides the information that is required to manage, modify, and implement partitions using the **Manage Partition Wizard**.</span></span>  
  
##  <a name="in-this-section"></a><a name="Top"></a> <span data-ttu-id="c9982-111">トピックの内容</span><span class="sxs-lookup"><span data-stu-id="c9982-111">In This Section</span></span>  
 <span data-ttu-id="c9982-112">以下のセクションでは、 **パーティションの管理ウィザード**の各ページのヘルプについて紹介します。</span><span class="sxs-lookup"><span data-stu-id="c9982-112">The following sections provide help on the pages of the **Manage Partition Wizard**.</span></span>  
  
 <span data-ttu-id="c9982-113">[パーティションの管理ウィザード ([パーティション操作の選択] ページ)](#SelectPartitionAction)</span><span class="sxs-lookup"><span data-stu-id="c9982-113">[Manage Partition Wizard (Select Partition Action Page)](#SelectPartitionAction)</span></span>  
  
 <span data-ttu-id="c9982-114">[パーティションの管理ウィザード ([切り替え先] ページ)](#SwitchIn)</span><span class="sxs-lookup"><span data-stu-id="c9982-114">[Manage Partition Wizard (Switch In Page)](#SwitchIn)</span></span>  
  
 <span data-ttu-id="c9982-115">[パーティションの管理ウィザード ([切り替え元] ページ)](#SwitchOut)</span><span class="sxs-lookup"><span data-stu-id="c9982-115">[Manage Partition Wizard (Switch Out Page)](#SwitchOut)</span></span>  
  
 <span data-ttu-id="c9982-116">[パーティションの管理ウィザード ([ステージング テーブル オプションの選択] ページ)](#StagingTableOptions)</span><span class="sxs-lookup"><span data-stu-id="c9982-116">[Manage Partition Wizard (Select Staging Table Options Page)](#StagingTableOptions)</span></span>  
  
 <span data-ttu-id="c9982-117">[パーティションの管理ウィザード ([出力オプションの選択] ページ)](#OutputOption)</span><span class="sxs-lookup"><span data-stu-id="c9982-117">[Manage Partition Wizard (Select Output Option Page)](#OutputOption)</span></span>  
  
 <span data-ttu-id="c9982-118">[パーティションの管理ウィザード ([新しいジョブ スケジュール] ページ)](#NewJob)</span><span class="sxs-lookup"><span data-stu-id="c9982-118">[Manage Partition Wizard (New Job Schedule Page)](#NewJob)</span></span>  
  
 <span data-ttu-id="c9982-119">[パーティションの管理ウィザード ([概要] ページ)](#Summary)</span><span class="sxs-lookup"><span data-stu-id="c9982-119">[Manage Partition Wizard (Summary Page)](#Summary)</span></span>  
  
 <span data-ttu-id="c9982-120">[パーティションの管理ウィザード ([進行状況] ページ)](#Progress)</span><span class="sxs-lookup"><span data-stu-id="c9982-120">[Manage Partition Wizard (Progress Page)](#Progress)</span></span>  
  
##  <a name="select-partition-action-page"></a><a name="SelectPartitionAction"></a> <span data-ttu-id="c9982-121">[パーティション操作の選択] ページ</span><span class="sxs-lookup"><span data-stu-id="c9982-121">Select Partition Action Page</span></span>  
 <span data-ttu-id="c9982-122">**[パーティション操作の選択]** ページを使用すると、パーティションに対して実行する操作を選択できます。</span><span class="sxs-lookup"><span data-stu-id="c9982-122">Use the **Select Partition Action** page to choose the action you want to perform on your partition.</span></span>  
  
### <a name="create-a-staging-table"></a><span data-ttu-id="c9982-123">ステージング テーブルの作成</span><span class="sxs-lookup"><span data-stu-id="c9982-123">Create a Staging Table</span></span>  
 <span data-ttu-id="c9982-124">定期的にデータの入れ替えを行っているパーティション テーブルが存在する場合、パーティションの切り替えは一般的なパーティション分割タスクです。たとえば、現在の四半期データを格納するパーティション テーブルがある場合は、各四半期末に新しいデータを追加し、古いデータをアーカイブする必要があります。</span><span class="sxs-lookup"><span data-stu-id="c9982-124">Partition switching is a common partitioning task if you have a partitioned table that you migrate data into and out of on a regular basis; for example, you have a partitioned table that stores current quarterly data, and you must move in new data and archive older data at the end of each quarter.</span></span>  
  
 <span data-ttu-id="c9982-125">ウィザードは、同一のパーティション分割列、テーブル/列構造、およびインデックスを持つステージング テーブルをデザインし、基になるパーティションがあるファイル グループに新しいテーブルを格納します。</span><span class="sxs-lookup"><span data-stu-id="c9982-125">The wizard designs the staging table with the same partitioning column, table and column structure, and indexes, and stores the new table in the filegroup where your source partition is located.</span></span>  
  
 <span data-ttu-id="c9982-126">パーティション データの切り替え先または切り替え元になるステージング テーブルを作成するには、 **[パーティション切り替え用のステージング テーブルを作成する]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="c9982-126">To create a staging table to switch in or switch out partition data, select **Create a staging table for partition switching**.</span></span>  
  
### <a name="sliding-window-scenario"></a><span data-ttu-id="c9982-127">スライディング ウィンドウ シナリオ</span><span class="sxs-lookup"><span data-stu-id="c9982-127">Sliding Window Scenario</span></span>  
 <span data-ttu-id="c9982-128">スライディング ウィンドウ シナリオでパーティションを管理するには、 **[スライディング ウィンドウ シナリオでパーティション分割されたデータを管理する]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="c9982-128">To manage your partitions in a sliding-window scenario, select **Manage partitioned data in a sliding window scenario**.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="c9982-129">UI 要素の一覧</span><span class="sxs-lookup"><span data-stu-id="c9982-129">UI element list</span></span>  
 <span data-ttu-id="c9982-130">**[パーティション切り替え用のステージング テーブルを作成する]**</span><span class="sxs-lookup"><span data-stu-id="c9982-130">**Create a staging table for partition switching**</span></span>  
 <span data-ttu-id="c9982-131">既存のパーティション テーブルのデータの切り替え先または切り替え元になるステージング テーブルを作成します。</span><span class="sxs-lookup"><span data-stu-id="c9982-131">Creates a staging table for the data you are switching in or switching out of the existing partitioned table.</span></span>  
  
 <span data-ttu-id="c9982-132">**[切り替え元パーティション]**</span><span class="sxs-lookup"><span data-stu-id="c9982-132">**Switch out partition**</span></span>  
 <span data-ttu-id="c9982-133">テーブルからパーティションを削除するときのオプションを提供します。</span><span class="sxs-lookup"><span data-stu-id="c9982-133">Provides options when removing a partition from the table.</span></span>  
  
 <span data-ttu-id="c9982-134">**[切り替え先パーティション]**</span><span class="sxs-lookup"><span data-stu-id="c9982-134">**Switch in partition**</span></span>  
 <span data-ttu-id="c9982-135">テーブルにパーティションを追加するときのオプションを提供します。</span><span class="sxs-lookup"><span data-stu-id="c9982-135">Provides options when adding a partition to the table.</span></span>  
  
 <span data-ttu-id="c9982-136">**[スライディング ウィンドウ シナリオでパーティション分割されたデータを管理する]**</span><span class="sxs-lookup"><span data-stu-id="c9982-136">**Manage partitioned data in a sliding window scenario**</span></span>  
 <span data-ttu-id="c9982-137">データの切り替えに使用できる空のパーティションを既存のテーブルに追加します。</span><span class="sxs-lookup"><span data-stu-id="c9982-137">Appends an empty partition to the existing table that can be used for switching in data.</span></span> <span data-ttu-id="c9982-138">ウィザードでは、現在、最後のパーティションへの切り替えと最初のパーティションからの切り替えがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="c9982-138">The wizard currently supports switching into the last partition and switching out the first partition.</span></span>  
  
 <span data-ttu-id="c9982-139">![[トップに戻る] リンクで使用される矢印アイコン](../../2014-toc/media/uparrow16x16.gif "[トップに戻る] リンクで使用される矢印アイコン") [このセクションの内容](#Top)</span><span class="sxs-lookup"><span data-stu-id="c9982-139">![Arrow icon used with Back to Top link](../../2014-toc/media/uparrow16x16.gif "Arrow icon used with Back to Top link") [In This Section](#Top)</span></span>  
  
##  <a name="select-partition-switching-in-options-page"></a><a name="SwitchIn"></a> <span data-ttu-id="c9982-140">[パーティションの切り替え先オプションの選択] ページ</span><span class="sxs-lookup"><span data-stu-id="c9982-140">Select Partition Switching-In Options Page</span></span>  
 <span data-ttu-id="c9982-141">**[パーティションの切り替え先オプションの選択]** ページを使用すると、パーティション テーブルに切り替えるステージング テーブルを選択できます。</span><span class="sxs-lookup"><span data-stu-id="c9982-141">Use the **Select Partition Switching-In options** page to select the staging table you are switching into the partitioned table.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="c9982-142">UI 要素の一覧</span><span class="sxs-lookup"><span data-stu-id="c9982-142">UI element list</span></span>  
 <span data-ttu-id="c9982-143">**[すべてのパーティションを表示]**</span><span class="sxs-lookup"><span data-stu-id="c9982-143">**Show All Partitions**</span></span>  
 <span data-ttu-id="c9982-144">現在パーティション テーブル内にあるパーティションを含む、すべてのパーティションを表示します。</span><span class="sxs-lookup"><span data-stu-id="c9982-144">Select to show all partitions, including the partitions currently in the partitioned table.</span></span>  
  
 <span data-ttu-id="c9982-145">**[パーティション グリッド]**</span><span class="sxs-lookup"><span data-stu-id="c9982-145">**Partition grid**</span></span>  
 <span data-ttu-id="c9982-146">選択したパーティションのパーティション名、 **[左側の境界]** 、 **[右側の境界]** 、 **[ファイル グループ]** 、および **[行数]** を表示します。</span><span class="sxs-lookup"><span data-stu-id="c9982-146">Displays the partition name, **Left boundary**, **Right boundary**, **Filegroup**, and **Row count** of the partitions you selected.</span></span>  
  
 <span data-ttu-id="c9982-147">**[切り替え先テーブル]**</span><span class="sxs-lookup"><span data-stu-id="c9982-147">**Switch in table**</span></span>  
 <span data-ttu-id="c9982-148">パーティション テーブルに追加するパーティションを含んでいるステージング テーブルを選択します。</span><span class="sxs-lookup"><span data-stu-id="c9982-148">Select the staging table that contains the partition that you want to add to your partitioned table.</span></span> <span data-ttu-id="c9982-149">**パーティションの管理ウィザード**でパーティションを切り替える前に、このステージング テーブルを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c9982-149">You must create this staging table before you switch-in partitions with the **Manage PartitionsWizard**.</span></span>  
  
 <span data-ttu-id="c9982-150">![[トップに戻る] リンクで使用される矢印アイコン](../../2014-toc/media/uparrow16x16.gif "[トップに戻る] リンクで使用される矢印アイコン") [このセクションの内容](#Top)</span><span class="sxs-lookup"><span data-stu-id="c9982-150">![Arrow icon used with Back to Top link](../../2014-toc/media/uparrow16x16.gif "Arrow icon used with Back to Top link") [In This Section](#Top)</span></span>  
  
##  <a name="select-partition-switching-out-options-page"></a><a name="SwitchOut"></a> <span data-ttu-id="c9982-151">[パーティションの切り替え元オプションの選択] ページ</span><span class="sxs-lookup"><span data-stu-id="c9982-151">Select Partition Switching-Out Options Page</span></span>  
 <span data-ttu-id="c9982-152">**[パーティションの切り替え元オプションの選択]** ページを使用すると、切り替え元のパーティション テーブルのパーティション分割されたデータを保持するパーティションとステージング テーブルを選択できます。</span><span class="sxs-lookup"><span data-stu-id="c9982-152">Use the **Select Partition Switching-Out options** page to select the partition and the staging table to hold the partitioned data that you are switching out of the partitioned table.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="c9982-153">UI 要素の一覧</span><span class="sxs-lookup"><span data-stu-id="c9982-153">UI element list</span></span>  
 <span data-ttu-id="c9982-154">**[パーティション グリッド]**</span><span class="sxs-lookup"><span data-stu-id="c9982-154">**Partition grid**</span></span>  
 <span data-ttu-id="c9982-155">選択したパーティションのパーティション名、 **[左側の境界]** 、 **[右側の境界]** 、 **[ファイル グループ]** 、および **[行数]** を表示します。</span><span class="sxs-lookup"><span data-stu-id="c9982-155">Displays the partition name, **Left boundary**, **Right boundary**, **Filegroup**, and **Row count** of the partitions you selected.</span></span>  
  
 <span data-ttu-id="c9982-156">**[切り替え元テーブル]**</span><span class="sxs-lookup"><span data-stu-id="c9982-156">**Switch out table**</span></span>  
 <span data-ttu-id="c9982-157">データの切り替え元となる新しいテーブルまたは既存のテーブルを選択します。</span><span class="sxs-lookup"><span data-stu-id="c9982-157">Choose a new table or an existing table to switch-out your data to.</span></span>  
  
 <span data-ttu-id="c9982-158">**[新規作成]**</span><span class="sxs-lookup"><span data-stu-id="c9982-158">**New**</span></span>  
 <span data-ttu-id="c9982-159">現在の切り替え元テーブルを切り替えるパーティションに使用するステージング テーブルの、新しい名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="c9982-159">Enter a new name for the staging table you want to use for the partition to switch out of the current source table.</span></span>  
  
 <span data-ttu-id="c9982-160">**Existing**</span><span class="sxs-lookup"><span data-stu-id="c9982-160">**Existing**</span></span>  
 <span data-ttu-id="c9982-161">現在の切り替え元テーブルを切り替えるパーティションに使用する、既存のステージング テーブルを選択します。</span><span class="sxs-lookup"><span data-stu-id="c9982-161">Select an existing staging table you want to use for the partition you want to switch out of the current source table.</span></span> <span data-ttu-id="c9982-162">既存のテーブルにデータが含まれている場合は、切り替え元データで上書きされます。</span><span class="sxs-lookup"><span data-stu-id="c9982-162">If the existing table contains data, this data will be overwritten with the data you are switching out.</span></span>  
  
 <span data-ttu-id="c9982-163">![[トップに戻る] リンクで使用される矢印アイコン](../../2014-toc/media/uparrow16x16.gif "[トップに戻る] リンクで使用される矢印アイコン") [このセクションの内容](#Top)</span><span class="sxs-lookup"><span data-stu-id="c9982-163">![Arrow icon used with Back to Top link](../../2014-toc/media/uparrow16x16.gif "Arrow icon used with Back to Top link") [In This Section](#Top)</span></span>  
  
##  <a name="select-the-staging-table-options-page"></a><a name="StagingTableOptions"></a> <span data-ttu-id="c9982-164">[ステージング テーブル オプションの選択] ページ</span><span class="sxs-lookup"><span data-stu-id="c9982-164">Select the Staging Table Options Page</span></span>  
 <span data-ttu-id="c9982-165">**[ステージング テーブル オプションの選択]** ページを使用すると、パーティション分割されたデータの切り替えに使用するステージング テーブルを作成できます。</span><span class="sxs-lookup"><span data-stu-id="c9982-165">Use the **Select the Staging Table Options** page to create the staging table you want to use for switching your partitioned data.</span></span>  
  
 <span data-ttu-id="c9982-166">ステージング テーブルは、元のテーブルがある、選択したパーティションと同じファイル グループに存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c9982-166">Staging tables must reside in the same filegroup of the selected partition where the source table is located.</span></span> <span data-ttu-id="c9982-167">ステージング テーブルは、切り替え元テーブルと切り替え先テーブルの両方の設計をミラー化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c9982-167">The staging table must mirror the design of both the source table and the destination table.</span></span>  
  
 <span data-ttu-id="c9982-168">また、基になるパーティションと同じインデックスを、ステージング テーブルに作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="c9982-168">You can also create the same indexes in the staging table that exist in the source partition.</span></span> <span data-ttu-id="c9982-169">ステージング テーブルには、基になるパーティションの要素に基づく制約が自動的に格納されます。</span><span class="sxs-lookup"><span data-stu-id="c9982-169">The staging table automatically contains a constraint based on the elements of the source partition.</span></span> <span data-ttu-id="c9982-170">この制約は、通常、基になるパーティションの境界値から生成されます。</span><span class="sxs-lookup"><span data-stu-id="c9982-170">This constraint is typically generated from the boundary value of the source partition.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="c9982-171">UI 要素の一覧</span><span class="sxs-lookup"><span data-stu-id="c9982-171">UI element list</span></span>  
 <span data-ttu-id="c9982-172">**[ステージング テーブル名]**</span><span class="sxs-lookup"><span data-stu-id="c9982-172">**Staging table name**</span></span>  
 <span data-ttu-id="c9982-173">ステージング テーブルの名前を作成するか、エディット ボックスに表示された既定の名前を受け入れます。</span><span class="sxs-lookup"><span data-stu-id="c9982-173">Create a name for the staging table or accept the default name displayed in the edit box.</span></span>  
  
 <span data-ttu-id="c9982-174">**[パーティションの切り替え]**</span><span class="sxs-lookup"><span data-stu-id="c9982-174">**Switch partition**</span></span>  
 <span data-ttu-id="c9982-175">現在のテーブルを切り替える、基になるパーティションを選択します。</span><span class="sxs-lookup"><span data-stu-id="c9982-175">Select the source partition that you want to switch out of the current table.</span></span>  
  
 <span data-ttu-id="c9982-176">**[新しい境界値]**</span><span class="sxs-lookup"><span data-stu-id="c9982-176">**New boundary value**</span></span>  
 <span data-ttu-id="c9982-177">ステージング テーブルのパーティション用の境界値を選択または入力します。</span><span class="sxs-lookup"><span data-stu-id="c9982-177">Select or enter the boundary value you want for the partition in the staging table.</span></span>  
  
 <span data-ttu-id="c9982-178">**[ファイル グループ]**</span><span class="sxs-lookup"><span data-stu-id="c9982-178">**Filegroup**</span></span>  
 <span data-ttu-id="c9982-179">新しいテーブルのファイル グループを選択します。</span><span class="sxs-lookup"><span data-stu-id="c9982-179">Select a filegroup for the new table.</span></span>  
  
 <span data-ttu-id="c9982-180">![[トップに戻る] リンクで使用される矢印アイコン](../../2014-toc/media/uparrow16x16.gif "[トップに戻る] リンクで使用される矢印アイコン") [このセクションの内容](#Top)</span><span class="sxs-lookup"><span data-stu-id="c9982-180">![Arrow icon used with Back to Top link](../../2014-toc/media/uparrow16x16.gif "Arrow icon used with Back to Top link") [In This Section](#Top)</span></span>  
  
##  <a name="select-output-option-page"></a><a name="OutputOption"></a> <span data-ttu-id="c9982-181">[出力オプションの選択] ページ</span><span class="sxs-lookup"><span data-stu-id="c9982-181">Select Output Option Page</span></span>  
 <span data-ttu-id="c9982-182">**[出力オプションの選択]** ページで、パーティションに対する変更を完了する方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="c9982-182">Use the **Select Output Option** page to specify how you want to complete the modifications to your partitions.</span></span>  
  
### <a name="create-script"></a><span data-ttu-id="c9982-183">[スクリプトの作成]</span><span class="sxs-lookup"><span data-stu-id="c9982-183">Create Script</span></span>  
 <span data-ttu-id="c9982-184">ウィザードの完了時に、テーブルのパーティションを変更するためのスクリプトがクエリ エディターで作成されます。</span><span class="sxs-lookup"><span data-stu-id="c9982-184">When the wizard finishes, it creates a script in Query Editor to modify partitions in the table.</span></span> <span data-ttu-id="c9982-185">スクリプトを確認し、手動で実行する場合は、 **[スクリプトの作成]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="c9982-185">Select **Create Script** if you want to review the script, and then execute the script manually.</span></span>  
  
 <span data-ttu-id="c9982-186">**[スクリプトをファイルに保存]**</span><span class="sxs-lookup"><span data-stu-id="c9982-186">**Script to file**</span></span>  
 <span data-ttu-id="c9982-187">スクリプトを .sql ファイルに生成します。</span><span class="sxs-lookup"><span data-stu-id="c9982-187">Generate the script to a .sql file.</span></span> <span data-ttu-id="c9982-188">**Unicode** または **ANSI テキスト**を指定します。</span><span class="sxs-lookup"><span data-stu-id="c9982-188">Specify either **Unicode** or **ANSI text**.</span></span> <span data-ttu-id="c9982-189">ファイルの名前と場所を指定するには、 **[参照]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c9982-189">To specify a name and location for the file, click **Browse**.</span></span>  
  
 <span data-ttu-id="c9982-190">**[スクリプトをクリップボードに保存]**</span><span class="sxs-lookup"><span data-stu-id="c9982-190">**Script to Clipboard**</span></span>  
 <span data-ttu-id="c9982-191">スクリプトをクリップボードに保存します。</span><span class="sxs-lookup"><span data-stu-id="c9982-191">Save the script to the Clipboard.</span></span>  
  
 <span data-ttu-id="c9982-192">**[スクリプトを新しいクエリ ウィンドウに保存]**</span><span class="sxs-lookup"><span data-stu-id="c9982-192">**Script to New Query Window**</span></span>  
 <span data-ttu-id="c9982-193">スクリプトをクエリ エディター ウィンドウに生成します。</span><span class="sxs-lookup"><span data-stu-id="c9982-193">Generate the script to a Query Editor window.</span></span> <span data-ttu-id="c9982-194">エディター ウィンドウが開いていない場合、スクリプトのターゲットとして新しいエディター ウィンドウが開きます。</span><span class="sxs-lookup"><span data-stu-id="c9982-194">If no editor window is open, a new editor window opens as the target for the script.</span></span>  
  
### <a name="run-immediately"></a><span data-ttu-id="c9982-195">[すぐに実行する]</span><span class="sxs-lookup"><span data-stu-id="c9982-195">Run Immediately</span></span>  
 <span data-ttu-id="c9982-196">**Run immediately**</span><span class="sxs-lookup"><span data-stu-id="c9982-196">**Run immediately**</span></span>  
 <span data-ttu-id="c9982-197">ウィザードで **[次へ]** または **[完了]** をクリックしたときにパーティションの変更が完了するようにします。</span><span class="sxs-lookup"><span data-stu-id="c9982-197">Have the wizard finish modifications to the partitions when you click **Next** or **Finish**.</span></span>  
  
### <a name="schedule"></a><span data-ttu-id="c9982-198">スケジュール</span><span class="sxs-lookup"><span data-stu-id="c9982-198">Schedule</span></span>  
 <span data-ttu-id="c9982-199">スケジュールした日時にテーブル パーティションを変更する場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="c9982-199">Select to modify the table partitions at a scheduled date and time.</span></span>  
  
 <span data-ttu-id="c9982-200">**[スケジュールの変更]**</span><span class="sxs-lookup"><span data-stu-id="c9982-200">**Change schedule**</span></span>  
 <span data-ttu-id="c9982-201">**[新しいジョブ スケジュール]** ダイアログ ボックスを開きます。このダイアログ ボックスでは、スケジュールされたジョブのプロパティを選択、変更、または表示できます。</span><span class="sxs-lookup"><span data-stu-id="c9982-201">Opens the **New Job Schedule** dialog box, where you can select, change, or view the properties of the scheduled job.</span></span>  
  
 <span data-ttu-id="c9982-202">![[トップに戻る] リンクで使用される矢印アイコン](../../2014-toc/media/uparrow16x16.gif "[トップに戻る] リンクで使用される矢印アイコン") [このセクションの内容](#Top)</span><span class="sxs-lookup"><span data-stu-id="c9982-202">![Arrow icon used with Back to Top link](../../2014-toc/media/uparrow16x16.gif "Arrow icon used with Back to Top link") [In This Section](#Top)</span></span>  
  
##  <a name="new-job-schedule-page"></a><a name="NewJob"></a> <span data-ttu-id="c9982-203">[新しいジョブ スケジュール] ページ</span><span class="sxs-lookup"><span data-stu-id="c9982-203">New Job Schedule Page</span></span>  
 <span data-ttu-id="c9982-204">**[新しいジョブ スケジュール]** ページを使用すると、スケジュールのプロパティを表示したり、変更したりできます。</span><span class="sxs-lookup"><span data-stu-id="c9982-204">Use the **New Job Schedule** page to view and change the properties of the schedule.</span></span>  
  
### <a name="options"></a><span data-ttu-id="c9982-205">Options</span><span class="sxs-lookup"><span data-stu-id="c9982-205">Options</span></span>  
 <span data-ttu-id="c9982-206">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ジョブに必要なスケジュールの種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="c9982-206">Select the type of schedule you want for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job.</span></span>  
  
 <span data-ttu-id="c9982-207">**名前**</span><span class="sxs-lookup"><span data-stu-id="c9982-207">**Name**</span></span>  
 <span data-ttu-id="c9982-208">スケジュールの新しい名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="c9982-208">Type a new name for the schedule.</span></span>  
  
 <span data-ttu-id="c9982-209">**[スケジュール済みのジョブ]**</span><span class="sxs-lookup"><span data-stu-id="c9982-209">**Jobs in schedule**</span></span>  
 <span data-ttu-id="c9982-210">スケジュールを使用する既存のジョブを表示します。</span><span class="sxs-lookup"><span data-stu-id="c9982-210">View the existing jobs that use the schedule.</span></span>  
  
 <span data-ttu-id="c9982-211">**[スケジュールの種類]**</span><span class="sxs-lookup"><span data-stu-id="c9982-211">**Schedule type**</span></span>  
 <span data-ttu-id="c9982-212">スケジュールの種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="c9982-212">Select the type of schedule.</span></span>  
  
 <span data-ttu-id="c9982-213">**有効**</span><span class="sxs-lookup"><span data-stu-id="c9982-213">**Enabled**</span></span>  
 <span data-ttu-id="c9982-214">スケジュールを有効または無効にします。</span><span class="sxs-lookup"><span data-stu-id="c9982-214">Enable or disable the schedule.</span></span>  
  
### <a name="recurring-schedule-types-options"></a><span data-ttu-id="c9982-215">定期スケジュールのオプション</span><span class="sxs-lookup"><span data-stu-id="c9982-215">Recurring Schedule Types Options</span></span>  
 <span data-ttu-id="c9982-216">スケジュールされているジョブの頻度を選択します。</span><span class="sxs-lookup"><span data-stu-id="c9982-216">Select the frequency of the scheduled job.</span></span>  
  
 <span data-ttu-id="c9982-217">**[実行]**</span><span class="sxs-lookup"><span data-stu-id="c9982-217">**Occurs**</span></span>  
 <span data-ttu-id="c9982-218">スケジュールが定期的に実行される間隔を選択します。</span><span class="sxs-lookup"><span data-stu-id="c9982-218">Select the interval at which the schedule recurs.</span></span>  
  
 <span data-ttu-id="c9982-219">**[間隔]**</span><span class="sxs-lookup"><span data-stu-id="c9982-219">**Recurs every**</span></span>  
 <span data-ttu-id="c9982-220">スケジュールを実行する間隔を日数または週数で選択します。</span><span class="sxs-lookup"><span data-stu-id="c9982-220">Select the number of days or weeks between recurrences of the schedule.</span></span> <span data-ttu-id="c9982-221">このオプションは、月単位のスケジュールでは使用できません。</span><span class="sxs-lookup"><span data-stu-id="c9982-221">This option is not available for monthly schedules.</span></span>  
  
 <span data-ttu-id="c9982-222">**月曜日**</span><span class="sxs-lookup"><span data-stu-id="c9982-222">**Monday**</span></span>  
 <span data-ttu-id="c9982-223">月曜日にジョブを実行するように設定します。</span><span class="sxs-lookup"><span data-stu-id="c9982-223">Set the job to occur on a Monday.</span></span> <span data-ttu-id="c9982-224">週単位のスケジュールでのみ選択できます。</span><span class="sxs-lookup"><span data-stu-id="c9982-224">Only available for weekly schedules.</span></span>  
  
 <span data-ttu-id="c9982-225">**火曜日**</span><span class="sxs-lookup"><span data-stu-id="c9982-225">**Tuesday**</span></span>  
 <span data-ttu-id="c9982-226">火曜日にジョブを実行するように設定します。</span><span class="sxs-lookup"><span data-stu-id="c9982-226">Set the job to occur on a Tuesday.</span></span> <span data-ttu-id="c9982-227">週単位のスケジュールでのみ選択できます。</span><span class="sxs-lookup"><span data-stu-id="c9982-227">Only available for weekly schedules.</span></span>  
  
 <span data-ttu-id="c9982-228">**水曜日**</span><span class="sxs-lookup"><span data-stu-id="c9982-228">**Wednesday**</span></span>  
 <span data-ttu-id="c9982-229">水曜日にジョブを実行するように設定します。</span><span class="sxs-lookup"><span data-stu-id="c9982-229">Set the job to occur on a Wednesday.</span></span> <span data-ttu-id="c9982-230">週単位のスケジュールでのみ選択できます。</span><span class="sxs-lookup"><span data-stu-id="c9982-230">Only available for weekly schedules.</span></span>  
  
 <span data-ttu-id="c9982-231">**木曜日**</span><span class="sxs-lookup"><span data-stu-id="c9982-231">**Thursday**</span></span>  
 <span data-ttu-id="c9982-232">木曜日にジョブを実行するように設定します。</span><span class="sxs-lookup"><span data-stu-id="c9982-232">Set the job to occur on a Thursday.</span></span> <span data-ttu-id="c9982-233">週単位のスケジュールでのみ選択できます。</span><span class="sxs-lookup"><span data-stu-id="c9982-233">Only available for weekly schedules.</span></span>  
  
 <span data-ttu-id="c9982-234">**金曜日**</span><span class="sxs-lookup"><span data-stu-id="c9982-234">**Friday**</span></span>  
 <span data-ttu-id="c9982-235">金曜日にジョブを実行するように設定します。</span><span class="sxs-lookup"><span data-stu-id="c9982-235">Set the job to occur on a Friday.</span></span> <span data-ttu-id="c9982-236">週単位のスケジュールでのみ選択できます。</span><span class="sxs-lookup"><span data-stu-id="c9982-236">Only available for weekly schedules.</span></span>  
  
 <span data-ttu-id="c9982-237">**土曜日**</span><span class="sxs-lookup"><span data-stu-id="c9982-237">**Saturday**</span></span>  
 <span data-ttu-id="c9982-238">土曜日にジョブを実行するように設定します。</span><span class="sxs-lookup"><span data-stu-id="c9982-238">Set the job to occur on a Saturday.</span></span> <span data-ttu-id="c9982-239">週単位のスケジュールでのみ選択できます。</span><span class="sxs-lookup"><span data-stu-id="c9982-239">Only available for weekly schedules.</span></span>  
  
 <span data-ttu-id="c9982-240">**日曜日**</span><span class="sxs-lookup"><span data-stu-id="c9982-240">**Sunday**</span></span>  
 <span data-ttu-id="c9982-241">日曜日にジョブを実行するように設定します。</span><span class="sxs-lookup"><span data-stu-id="c9982-241">Set the job to occur on a Sunday.</span></span> <span data-ttu-id="c9982-242">週単位のスケジュールでのみ選択できます。</span><span class="sxs-lookup"><span data-stu-id="c9982-242">Only available for weekly schedules.</span></span>  
  
 <span data-ttu-id="c9982-243">**日**</span><span class="sxs-lookup"><span data-stu-id="c9982-243">**Day**</span></span>  
 <span data-ttu-id="c9982-244">スケジュールが発生する日を選択します。</span><span class="sxs-lookup"><span data-stu-id="c9982-244">Select the day of the month the schedule occurs.</span></span> <span data-ttu-id="c9982-245">月単位のスケジュールでのみ選択できます。</span><span class="sxs-lookup"><span data-stu-id="c9982-245">Only available for monthly schedules.</span></span>  
  
 <span data-ttu-id="c9982-246">**[間隔]**</span><span class="sxs-lookup"><span data-stu-id="c9982-246">**of every**</span></span>  
 <span data-ttu-id="c9982-247">スケジュールを実行する間隔を月数で選択します。</span><span class="sxs-lookup"><span data-stu-id="c9982-247">Select the number of months between occurrences of the schedule.</span></span> <span data-ttu-id="c9982-248">月単位のスケジュールでのみ選択できます。</span><span class="sxs-lookup"><span data-stu-id="c9982-248">Only available for monthly schedules.</span></span>  
  
 <span data-ttu-id="c9982-249">**[曜日]**</span><span class="sxs-lookup"><span data-stu-id="c9982-249">**The**</span></span>  
 <span data-ttu-id="c9982-250">月の特定の週における特定の曜日をスケジュールに指定します。</span><span class="sxs-lookup"><span data-stu-id="c9982-250">Specify a schedule for a specific day of the week on a specific week within the month.</span></span> <span data-ttu-id="c9982-251">月単位のスケジュールでのみ選択できます。</span><span class="sxs-lookup"><span data-stu-id="c9982-251">Only available for monthly schedules.</span></span>  
  
 <span data-ttu-id="c9982-252">**[1 回]**</span><span class="sxs-lookup"><span data-stu-id="c9982-252">**Occurs once at**</span></span>  
 <span data-ttu-id="c9982-253">毎日実行するジョブの開始時刻を設定します。</span><span class="sxs-lookup"><span data-stu-id="c9982-253">Set the time for a job to occur daily.</span></span>  
  
 <span data-ttu-id="c9982-254">**[間隔]**</span><span class="sxs-lookup"><span data-stu-id="c9982-254">**Occurs every**</span></span>  
 <span data-ttu-id="c9982-255">ジョブの実行間隔を時間と分の単位で設定します。</span><span class="sxs-lookup"><span data-stu-id="c9982-255">Set the number of hours or minutes between occurrences.</span></span>  
  
 <span data-ttu-id="c9982-256">**開始日**</span><span class="sxs-lookup"><span data-stu-id="c9982-256">**Start date**</span></span>  
 <span data-ttu-id="c9982-257">設定したスケジュールの適用開始日を指定します。</span><span class="sxs-lookup"><span data-stu-id="c9982-257">Set the date when this schedule will become effective.</span></span>  
  
 <span data-ttu-id="c9982-258">**終了日**</span><span class="sxs-lookup"><span data-stu-id="c9982-258">**End date**</span></span>  
 <span data-ttu-id="c9982-259">設定したスケジュールを適用する期間の最終日を指定します。</span><span class="sxs-lookup"><span data-stu-id="c9982-259">Set the date when the schedule will no longer be effective.</span></span>  
  
 <span data-ttu-id="c9982-260">**[終了日なし]**</span><span class="sxs-lookup"><span data-stu-id="c9982-260">**No end date**</span></span>  
 <span data-ttu-id="c9982-261">スケジュールを無期限に適用するように指定します。</span><span class="sxs-lookup"><span data-stu-id="c9982-261">Specify that the schedule will remain effective indefinitely.</span></span>  
  
### <a name="one-time-schedule-types-options"></a><span data-ttu-id="c9982-262">指定日時スケジュールのオプション</span><span class="sxs-lookup"><span data-stu-id="c9982-262">One Time Schedule Types Options</span></span>  
 <span data-ttu-id="c9982-263">ジョブを一度だけ実行するようにスケジュールする場合は、将来の日付と時刻を選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c9982-263">If you schedule a job to run once, you must select a date and time in the future.</span></span>  
  
 <span data-ttu-id="c9982-264">**Date**</span><span class="sxs-lookup"><span data-stu-id="c9982-264">**Date**</span></span>  
 <span data-ttu-id="c9982-265">ジョブを実行する日付を選択します。</span><span class="sxs-lookup"><span data-stu-id="c9982-265">Select the date for the job to run.</span></span>  
  
 <span data-ttu-id="c9982-266">**Time**</span><span class="sxs-lookup"><span data-stu-id="c9982-266">**Time**</span></span>  
 <span data-ttu-id="c9982-267">ジョブを実行する時刻を選択します。</span><span class="sxs-lookup"><span data-stu-id="c9982-267">Select the time for the job to run.</span></span>  
  
 <span data-ttu-id="c9982-268">![[トップに戻る] リンクで使用される矢印アイコン](../../2014-toc/media/uparrow16x16.gif "[トップに戻る] リンクで使用される矢印アイコン") [このセクションの内容](#Top)</span><span class="sxs-lookup"><span data-stu-id="c9982-268">![Arrow icon used with Back to Top link](../../2014-toc/media/uparrow16x16.gif "Arrow icon used with Back to Top link") [In This Section](#Top)</span></span>  
  
##  <a name="summary-page"></a><a name="Summary"></a> <span data-ttu-id="c9982-269">[概要] ページ</span><span class="sxs-lookup"><span data-stu-id="c9982-269">Summary Page</span></span>  
 <span data-ttu-id="c9982-270">**[概要]** ページを使用すると、前の各ページで選択したオプションを確認できます。</span><span class="sxs-lookup"><span data-stu-id="c9982-270">Use the **Summary** page to review the options that you have selected on the previous pages.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="c9982-271">UI 要素の一覧</span><span class="sxs-lookup"><span data-stu-id="c9982-271">UI element list</span></span>  
 <span data-ttu-id="c9982-272">**[選択内容の確認]**</span><span class="sxs-lookup"><span data-stu-id="c9982-272">**Review your selections**</span></span>  
 <span data-ttu-id="c9982-273">ウィザードの各ページで行った選択の内容が表示されます。</span><span class="sxs-lookup"><span data-stu-id="c9982-273">Displays the selections you have made for each page of the wizard.</span></span> <span data-ttu-id="c9982-274">ノードをクリックして展開すると、以前に選択したオプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c9982-274">Click a node to expand and view your previously selected options.</span></span>  
  
 <span data-ttu-id="c9982-275">![[トップに戻る] リンクで使用される矢印アイコン](../../2014-toc/media/uparrow16x16.gif "[トップに戻る] リンクで使用される矢印アイコン") [このセクションの内容](#Top)</span><span class="sxs-lookup"><span data-stu-id="c9982-275">![Arrow icon used with Back to Top link](../../2014-toc/media/uparrow16x16.gif "Arrow icon used with Back to Top link") [In This Section](#Top)</span></span>  
  
##  <a name="progress-page"></a><a name="Progress"></a> <span data-ttu-id="c9982-276">[進行状況] ページ</span><span class="sxs-lookup"><span data-stu-id="c9982-276">Progress Page</span></span>  
 <span data-ttu-id="c9982-277">**[進行状況]** ページを使用すると、 **パーティションの管理ウィザード**のアクションに関する状態情報を監視できます。</span><span class="sxs-lookup"><span data-stu-id="c9982-277">Use the **Progress** page to monitor status information about the actions of the **Manage Partition Wizard**.</span></span> <span data-ttu-id="c9982-278">ウィザードで選択したオプションに応じて、 **[進行状況]** ページに 1 つまたは複数のアクションが含まれる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c9982-278">Depending on the options that you selected in the wizard, the **Progress** page might contain one or more actions.</span></span> <span data-ttu-id="c9982-279">上部のボックスには、ウィザードの全体的な状態と受信した状態メッセージ、エラー メッセージ、および警告メッセージの数が表示されます。</span><span class="sxs-lookup"><span data-stu-id="c9982-279">The top box displays the overall status of the wizard and the number of status, error, and warning messages that the wizard has received.</span></span>  
  
### <a name="options"></a><span data-ttu-id="c9982-280">Options</span><span class="sxs-lookup"><span data-stu-id="c9982-280">Options</span></span>  
 <span data-ttu-id="c9982-281">**詳細**</span><span class="sxs-lookup"><span data-stu-id="c9982-281">**Details**</span></span>  
 <span data-ttu-id="c9982-282">アクション、状態、およびウィザードで実行したアクションから返されたメッセージが提供されます。</span><span class="sxs-lookup"><span data-stu-id="c9982-282">Provides the action, status, and any messages that are returned from action taken by the wizard.</span></span>  
  
 <span data-ttu-id="c9982-283">**操作**</span><span class="sxs-lookup"><span data-stu-id="c9982-283">**Action**</span></span>  
 <span data-ttu-id="c9982-284">各アクションの種類と名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="c9982-284">Specifies the type and name of each action.</span></span>  
  
 <span data-ttu-id="c9982-285">**状態**</span><span class="sxs-lookup"><span data-stu-id="c9982-285">**Status**</span></span>  
 <span data-ttu-id="c9982-286">全体としてウィザードのアクションが **[成功]** または **[失敗]** のいずれの値を返したかを示します。</span><span class="sxs-lookup"><span data-stu-id="c9982-286">Indicates whether the wizard action as a whole returned the value of **Success** or **Failure**.</span></span>  
  
 <span data-ttu-id="c9982-287">**メッセージ**</span><span class="sxs-lookup"><span data-stu-id="c9982-287">**Message**</span></span>  
 <span data-ttu-id="c9982-288">プロセスから返されたすべてのエラー メッセージまたは警告メッセージを提供します。</span><span class="sxs-lookup"><span data-stu-id="c9982-288">Provides any error or warning messages that are returned from the process.</span></span>  
  
 <span data-ttu-id="c9982-289">**Stop**</span><span class="sxs-lookup"><span data-stu-id="c9982-289">**Stop**</span></span>  
 <span data-ttu-id="c9982-290">ウィザードのアクションを停止します。</span><span class="sxs-lookup"><span data-stu-id="c9982-290">Stop the action of the wizard.</span></span>  
  
 <span data-ttu-id="c9982-291">**Report**</span><span class="sxs-lookup"><span data-stu-id="c9982-291">**Report**</span></span>  
 <span data-ttu-id="c9982-292">**パーティションの管理ウィザード**の結果を含むレポートを作成します。</span><span class="sxs-lookup"><span data-stu-id="c9982-292">Create a report that contains the results of the **Manage Partition Wizard**.</span></span> <span data-ttu-id="c9982-293">オプションは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="c9982-293">The options are:</span></span>  
  
-   <span data-ttu-id="c9982-294">**[レポートの表示]**</span><span class="sxs-lookup"><span data-stu-id="c9982-294">**View Report**</span></span>  
  
-   <span data-ttu-id="c9982-295">**[レポートをファイルに保存]**</span><span class="sxs-lookup"><span data-stu-id="c9982-295">**Save Report to File**</span></span>  
  
-   <span data-ttu-id="c9982-296">**[レポートをクリップボードにコピー]**</span><span class="sxs-lookup"><span data-stu-id="c9982-296">**Copy Report to Clipboard**</span></span>  
  
-   <span data-ttu-id="c9982-297">**[レポートを電子メールとして送信]**</span><span class="sxs-lookup"><span data-stu-id="c9982-297">**Send Report as Email**</span></span>  
  
 <span data-ttu-id="c9982-298">**[レポートの表示]**</span><span class="sxs-lookup"><span data-stu-id="c9982-298">**View Report**</span></span>  
 <span data-ttu-id="c9982-299">**[レポートの表示]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="c9982-299">Open the **View Report** dialog box.</span></span> <span data-ttu-id="c9982-300">このダイアログ ボックスでは、 **パーティションの管理ウィザード**の進行状況のテキスト レポートが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c9982-300">This dialog box contains a text report of the progress of the **Manage Partition Wizard**.</span></span>  
  
 <span data-ttu-id="c9982-301">**[閉じる]**</span><span class="sxs-lookup"><span data-stu-id="c9982-301">**Close**</span></span>  
 <span data-ttu-id="c9982-302">ウィザードを閉じます。</span><span class="sxs-lookup"><span data-stu-id="c9982-302">Close the wizard.</span></span>  
  
 <span data-ttu-id="c9982-303">![[トップに戻る] リンクで使用される矢印アイコン](../../2014-toc/media/uparrow16x16.gif "[トップに戻る] リンクで使用される矢印アイコン") [このセクションの内容](#Top)</span><span class="sxs-lookup"><span data-stu-id="c9982-303">![Arrow icon used with Back to Top link](../../2014-toc/media/uparrow16x16.gif "Arrow icon used with Back to Top link") [In This Section](#Top)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9982-304">参照</span><span class="sxs-lookup"><span data-stu-id="c9982-304">See Also</span></span>  
 [<span data-ttu-id="c9982-305">パーティション テーブルとパーティション インデックス</span><span class="sxs-lookup"><span data-stu-id="c9982-305">Partitioned Tables and Indexes</span></span>](partitioned-tables-and-indexes.md)  
  
  
