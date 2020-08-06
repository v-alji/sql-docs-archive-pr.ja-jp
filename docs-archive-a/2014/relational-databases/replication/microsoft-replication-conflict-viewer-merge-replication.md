---
title: '[Microsoft レプリケーション競合表示モジュール] (マージ レプリケーション) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.replconflictviewer.cvmerge.f1
ms.assetid: bfef5e21-ac04-4bc5-a55e-595421e34923
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1354a35e06f58b56f9678267338917a272ff8b19
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631826"
---
# <a name="microsoft-replication-conflict-viewer-merge-replication"></a><span data-ttu-id="5043f-102">[Microsoft レプリケーション競合表示モジュール] (マージ レプリケーション)</span><span class="sxs-lookup"><span data-stu-id="5043f-102">Microsoft Replication Conflict Viewer (Merge Replication)</span></span>
  <span data-ttu-id="5043f-103">レプリケーション競合表示モジュールを使用すると、レプリケーション同期中に発生した競合を表示できます。</span><span class="sxs-lookup"><span data-stu-id="5043f-103">The Replication Conflict Viewer allows you to view any conflicts that have occurred during replication synchronization.</span></span> <span data-ttu-id="5043f-104">競合が発生するのは、同一のデータの変更が、2 つの異なるサーバー、たとえば、パブリッシャーとサブスクライバー、または 2 つの異なるサブスクライバーで行われたときです。</span><span class="sxs-lookup"><span data-stu-id="5043f-104">Conflicts occur when the same data is modified at two separate servers, for example, at a Publisher and Subscriber, or at two different Subscribers.</span></span> <span data-ttu-id="5043f-105">競合は、レプリケーションがアーティクルの作成時に選択された競合回避モジュールを使用することで自動的に解決されます。</span><span class="sxs-lookup"><span data-stu-id="5043f-105">Replication automatically resolves conflicts using the conflict resolver you selected when the article was created.</span></span> <span data-ttu-id="5043f-106">ただし、レプリケーション競合表示モジュールを使用すると、必要な場合に、競合を回避するための別の解決方法を選択することができます。</span><span class="sxs-lookup"><span data-stu-id="5043f-106">However, the Replication Conflict Viewer allows you to choose a different resolution for the conflict when necessary.</span></span> <span data-ttu-id="5043f-107">発生する可能性がある競合は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="5043f-107">The following conflicts can occur:</span></span>  
  
-   <span data-ttu-id="5043f-108">更新競合。</span><span class="sxs-lookup"><span data-stu-id="5043f-108">Update conflicts.</span></span> <span data-ttu-id="5043f-109">更新競合は、同一のデータが 2 つの異なる場所で変更された場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="5043f-109">Update conflicts occur when the same data is changed at two locations.</span></span> <span data-ttu-id="5043f-110">一方の変更が競合の優先データとなり、他方は非優先データとなります。</span><span class="sxs-lookup"><span data-stu-id="5043f-110">One change wins, and the other one loses.</span></span> <span data-ttu-id="5043f-111">既存のデータ (競合の優先データ) を保持する、競合したデータ (競合の非優先データ) で既存のデータを上書きする、または優先データと非優先データをマージして既存のデータを更新するオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="5043f-111">You have the option to keep the existing data (the data that won), overwrite the existing data with the data that conflicted with it (the losing data), or merge the winning and losing data and update the existing data.</span></span>  
  
-   <span data-ttu-id="5043f-112">挿入競合。</span><span class="sxs-lookup"><span data-stu-id="5043f-112">Insert conflicts.</span></span> <span data-ttu-id="5043f-113">挿入競合は、他の場所での変更とマージされた場合に、データの一貫性のルールに違反する場所に行が挿入されたときに発生します。</span><span class="sxs-lookup"><span data-stu-id="5043f-113">Insert conflicts occur when a row is inserted at one location that violates some data consistency rule when merged with changes at other locations.</span></span> <span data-ttu-id="5043f-114">既存のデータ (競合の優先データ) を保持する、競合したデータ (競合の非優先データ) で既存のデータを上書きする、または優先データと非優先データをマージして既存のデータを更新するオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="5043f-114">You have the option to keep the existing data (the data that won), overwrite the existing data with the data that conflicted with it (the losing data), or merge the winning and losing data and update the existing data.</span></span>  
  
-   <span data-ttu-id="5043f-115">削除競合。</span><span class="sxs-lookup"><span data-stu-id="5043f-115">Delete conflicts.</span></span> <span data-ttu-id="5043f-116">この競合は、同一行が、ある箇所で削除され、別の箇所で変更された場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="5043f-116">This conflict occurs when the same row is deleted at one location and changed at the other.</span></span>  
  
 <span data-ttu-id="5043f-117">競合は同期中に解決され、競合の非優先行のデータは競合テーブルに書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="5043f-117">When conflicts are resolved during synchronization, the data from the losing row is written to a conflict table.</span></span> <span data-ttu-id="5043f-118">この競合に対して、最初の解決策を受け入れるか別の解決策を選択すると、記録された競合行は競合テーブルから削除されます。</span><span class="sxs-lookup"><span data-stu-id="5043f-118">Whether you accept the original resolution or choose a different resolution for the conflict, the logged conflict row is deleted from the conflict table.</span></span> <span data-ttu-id="5043f-119">定期的に競合を見直して、競合テーブルのサイズを小さくするようにしてください。</span><span class="sxs-lookup"><span data-stu-id="5043f-119">You should periodically review conflicts to help reduce the size of the conflict tracking tables.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5043f-120">論理レコードに関連する競合は、競合表示モジュールに表示されません。</span><span class="sxs-lookup"><span data-stu-id="5043f-120">Conflicts that involve logical records are not displayed in Conflict Viewer.</span></span> <span data-ttu-id="5043f-121">これらの競合に関する情報を表示するには、レプリケーション ストアド プロシージャを使用します。</span><span class="sxs-lookup"><span data-stu-id="5043f-121">To view information about these conflicts, use replication stored procedures.</span></span> <span data-ttu-id="5043f-122">詳細については、「[マージ パブリケーションの競合情報の表示 (レプリケーション Transact-SQL プログラミング)](view-conflict-information-for-merge-publications.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5043f-122">For more information, see [View Conflict Information for Merge Publications &#40;Replication Transact-SQL Programming&#41;](view-conflict-information-for-merge-publications.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="5043f-123">Options</span><span class="sxs-lookup"><span data-stu-id="5043f-123">Options</span></span>  
 <span data-ttu-id="5043f-124">レプリケーション競合表示モジュールは 2 つのセクションに分かれています。</span><span class="sxs-lookup"><span data-stu-id="5043f-124">The Replication Conflict Viewer is divided into two sections.</span></span> <span data-ttu-id="5043f-125">ダイアログ ボックスの上側のセクションには、選択されたテーブルの競合の一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="5043f-125">The upper section of the dialog box shows the conflict list for the selected table.</span></span> <span data-ttu-id="5043f-126">競合の一覧の項目をクリックすると、競合の詳細がダイアログ ボックスの下側のセクションに表示されます。</span><span class="sxs-lookup"><span data-stu-id="5043f-126">When you click an item in the conflict list, the details of the conflict are displayed in the lower section of the dialog box.</span></span>  
  
 <span data-ttu-id="5043f-127">競合の発生理由を示す情報 (パブリッシャーとサブスクライバーの両方で同じ行が更新された場合など) はダイアログ ボックスの下部に表示されます。</span><span class="sxs-lookup"><span data-stu-id="5043f-127">Information describing why the conflict occurred (for example, the same row was updated at both the Publisher and the Subscriber) is displayed in the lower section of the dialog box.</span></span> <span data-ttu-id="5043f-128">下側のセクションの競合データは、2 つの対応する列 (**[競合で優先されたデータ]** と **[競合で優先されなかったデータ]**) に表示されます。</span><span class="sxs-lookup"><span data-stu-id="5043f-128">The conflict data in the lower section is displayed in two corresponding columns (**Conflict Winner** and **Conflict Loser**).</span></span> <span data-ttu-id="5043f-129">更新されたデータと削除されたデータの間で競合が発生した場合、競合で削除された側にデータが表示されない場合があります。</span><span class="sxs-lookup"><span data-stu-id="5043f-129">If the conflict is between updated and deleted data, there may be no data to show for the deleted side of the conflict.</span></span> <span data-ttu-id="5043f-130">この場合、レプリケーション競合表示モジュールでは、その行がある箇所では削除され別の箇所では更新されたことを示すメッセージが列の 1 つに表示されます。</span><span class="sxs-lookup"><span data-stu-id="5043f-130">In this case, the Replication Conflict Viewer displays a message in one of the columns, indicating that the row was deleted at one location and updated at another.</span></span> <span data-ttu-id="5043f-131">また、提案された解決策についても示されます。</span><span class="sxs-lookup"><span data-stu-id="5043f-131">It also indicates the suggested resolution.</span></span>  
  
 <span data-ttu-id="5043f-132">レプリケーション競合表示モジュールで編集できないデータ (たとえば、 **rowguid** データ) は、読み取り専用としてボックス内に淡色表示されます。</span><span class="sxs-lookup"><span data-stu-id="5043f-132">Data that cannot be edited in the Replication Conflict Viewer (for example, **rowguid** data) is displayed read-only with the box shaded.</span></span>  
  
 <span data-ttu-id="5043f-133">**[データベース]**</span><span class="sxs-lookup"><span data-stu-id="5043f-133">**Database**</span></span>  
 <span data-ttu-id="5043f-134">競合があるパブリケーションを含むデータベースを選択します。</span><span class="sxs-lookup"><span data-stu-id="5043f-134">Choose a database that includes publications with conflicts.</span></span>  
  
 <span data-ttu-id="5043f-135">**Publication**</span><span class="sxs-lookup"><span data-stu-id="5043f-135">**Publication**</span></span>  
 <span data-ttu-id="5043f-136">競合があるテーブルを含むパブリケーションを選択します。</span><span class="sxs-lookup"><span data-stu-id="5043f-136">Choose a publication that includes tables with conflicts.</span></span>  
  
 <span data-ttu-id="5043f-137">**テーブル**</span><span class="sxs-lookup"><span data-stu-id="5043f-137">**Table**</span></span>  
 <span data-ttu-id="5043f-138">競合を含むテーブルを選択します。</span><span class="sxs-lookup"><span data-stu-id="5043f-138">Choose a table that includes conflicts.</span></span>  
  
 <span data-ttu-id="5043f-139">**[フィルターの定義]**</span><span class="sxs-lookup"><span data-stu-id="5043f-139">**Define Filter**</span></span>  
 <span data-ttu-id="5043f-140">**[フィルターの定義]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="5043f-140">Click to open the **Define Filters** dialog box.</span></span>  
  
 <span data-ttu-id="5043f-141">**[フィルターの適用または削除]**</span><span class="sxs-lookup"><span data-stu-id="5043f-141">**Apply or Remove Filter**</span></span>  
 <span data-ttu-id="5043f-142">**[フィルターの定義]** ダイアログ ボックスで定義されたフィルターを適用または削除します。</span><span class="sxs-lookup"><span data-stu-id="5043f-142">Click to apply or remove a filter that has been defined in the **Define Filters** dialog box.</span></span>  
  
 <span data-ttu-id="5043f-143">**[すべて選択]**</span><span class="sxs-lookup"><span data-stu-id="5043f-143">**Select All**</span></span>  
 <span data-ttu-id="5043f-144">グリッドに一覧表示されたすべての競合を選択します。</span><span class="sxs-lookup"><span data-stu-id="5043f-144">Click to select all conflicts listed in the grid.</span></span>  
  
 <span data-ttu-id="5043f-145">**[なし] を選択**</span><span class="sxs-lookup"><span data-stu-id="5043f-145">**Select None**</span></span>  
 <span data-ttu-id="5043f-146">グリッドに一覧表示されたすべての競合の選択を解除します。</span><span class="sxs-lookup"><span data-stu-id="5043f-146">Click to deselect all conflicts listed in the grid.</span></span>  
  
 <span data-ttu-id="5043f-147">**削除**</span><span class="sxs-lookup"><span data-stu-id="5043f-147">**Remove**</span></span>  
 <span data-ttu-id="5043f-148">選択された競合をビューアーから削除し、関連するメタデータをレプリケーション システム テーブルから削除します。</span><span class="sxs-lookup"><span data-stu-id="5043f-148">Click to remove selected conflicts from the viewer and their associated metadata from the replication system tables.</span></span> <span data-ttu-id="5043f-149">それぞれの選択された競合に対して [優先するデータの送信] ボタンをクリックする (データへの変更を行わない) 場合と同じです。</span><span class="sxs-lookup"><span data-stu-id="5043f-149">Equivalent to clicking the Submit Winner button (without making any changes to the data) for each selected conflict.</span></span>  
  
 <span data-ttu-id="5043f-150">**[すべての列を表示]**</span><span class="sxs-lookup"><span data-stu-id="5043f-150">**Show all columns**</span></span>  
 <span data-ttu-id="5043f-151">テーブルのすべての列を表示します。</span><span class="sxs-lookup"><span data-stu-id="5043f-151">Select to show all columns of the table.</span></span>  
  
 <span data-ttu-id="5043f-152">**[最初の 5 列および競合データが含まれている列を表示]**</span><span class="sxs-lookup"><span data-stu-id="5043f-152">**Show first five columns and other columns with conflicting data**</span></span>  
 <span data-ttu-id="5043f-153">最初の 5 列および競合データが含まれている列を表示します。</span><span class="sxs-lookup"><span data-stu-id="5043f-153">Select to display the first five columns and any columns that have conflicts.</span></span> <span data-ttu-id="5043f-154">これは、テーブルに多数の列があり、競合を解決するのに最も関連する列のみを表示する場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="5043f-154">This is helpful when the table has a large number of columns, but you want to see only the columns most relevant to resolving the conflict.</span></span> <span data-ttu-id="5043f-155">主キーや名前フィールドなど、行を識別するフィールドはテーブルの最初の列にある場合が多いため、このビューでは最初の 5 列が必ず表示されます。</span><span class="sxs-lookup"><span data-stu-id="5043f-155">The first five columns are always included in this view, as fields that identify a row, such as the primary key or name fields, are often among the first columns of the table.</span></span>  
  
 <span data-ttu-id="5043f-156">**列情報の表示**(**...**)</span><span class="sxs-lookup"><span data-stu-id="5043f-156">**Display Column Information** (**...**)</span></span>  
 <span data-ttu-id="5043f-157">列の情報である **[テーブル名]**、 **[列名]**、 **[データ型]**、および **[列の値]** を表示します。</span><span class="sxs-lookup"><span data-stu-id="5043f-157">Click to view column information: **Table Name**, **Column Name**, **Data Type**, and **Column Value**.</span></span> <span data-ttu-id="5043f-158">**[列の値]** は、値が読み取り専用と表示されている場合を除いて編集可能です。</span><span class="sxs-lookup"><span data-stu-id="5043f-158">**Column Value** is editable unless the value is displayed as read-only.</span></span>  
  
 <span data-ttu-id="5043f-159">**[優先されたデータの送信]**</span><span class="sxs-lookup"><span data-stu-id="5043f-159">**Submit Winner**</span></span>  
 <span data-ttu-id="5043f-160">競合回避モジュールによって優先データと見なされた行をそのまま使用します。</span><span class="sxs-lookup"><span data-stu-id="5043f-160">Click to keep the row the conflict resolver determined to be the winner.</span></span> <span data-ttu-id="5043f-161">読み取り専用と表示されていない列の値は、このボタンをクリックする前に変更することができます。</span><span class="sxs-lookup"><span data-stu-id="5043f-161">The value of any column that is not displayed as read-only can be changed prior to clicking this button.</span></span>  
  
 <span data-ttu-id="5043f-162">**[優先されなかったデータの送信]**</span><span class="sxs-lookup"><span data-stu-id="5043f-162">**Submit Loser**</span></span>  
 <span data-ttu-id="5043f-163">競合回避モジュールによって非優先データと見なされた行を受け入れます。</span><span class="sxs-lookup"><span data-stu-id="5043f-163">Click to accept the row the conflict resolver determined to be the loser.</span></span> <span data-ttu-id="5043f-164">読み取り専用と表示されていない列の値は、このボタンをクリックする前に変更することができます。</span><span class="sxs-lookup"><span data-stu-id="5043f-164">The value of any column that is not displayed as read-only can be changed prior to clicking this button.</span></span>  
  
 <span data-ttu-id="5043f-165">**[競合の詳細をログに記録]**</span><span class="sxs-lookup"><span data-stu-id="5043f-165">**Log the details of the conflict**</span></span>  
 <span data-ttu-id="5043f-166">このボックスをオンにすると、競合の詳細がファイルに記録されます。</span><span class="sxs-lookup"><span data-stu-id="5043f-166">Check this box to log the details of the conflict to a file.</span></span> <span data-ttu-id="5043f-167">ファイルの場所を指定するには、 **[表示]** メニューをポイントし、 **[オプション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5043f-167">To specify a location for the file, point to the **View** menu and click **Options**.</span></span> <span data-ttu-id="5043f-168">値を入力するか、参照ボタン (**[...]**) をクリックして適切なファイルに移動します。</span><span class="sxs-lookup"><span data-stu-id="5043f-168">Enter a value, or click the browse (**...**) and navigate to the appropriate file.</span></span> <span data-ttu-id="5043f-169">**[OK]** をクリックして、 **[オプション]** ダイアログ ボックスを終了します。</span><span class="sxs-lookup"><span data-stu-id="5043f-169">Click **OK** to exit the **Options** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5043f-170">参照</span><span class="sxs-lookup"><span data-stu-id="5043f-170">See Also</span></span>  
 <span data-ttu-id="5043f-171">[マージパブリケーションのデータの競合を表示および解決する &#40;SQL Server Management Studio&#41;](view-and-resolve-data-conflicts-for-merge-publications.md) </span><span class="sxs-lookup"><span data-stu-id="5043f-171">[View and Resolve Data Conflicts for Merge Publications &#40;SQL Server Management Studio&#41;](view-and-resolve-data-conflicts-for-merge-publications.md) </span></span>  
 [<span data-ttu-id="5043f-172">マージ レプリケーションの競合検出および解決の詳細</span><span class="sxs-lookup"><span data-stu-id="5043f-172">Advanced Merge Replication Conflict Detection and Resolution</span></span>](merge/advanced-merge-replication-conflict-detection-and-resolution.md)  
  
  
