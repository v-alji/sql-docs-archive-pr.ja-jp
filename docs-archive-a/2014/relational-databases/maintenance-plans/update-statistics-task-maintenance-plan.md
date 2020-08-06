---
title: '[統計の更新タスク] (メンテナンス プラン) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.maint.statistics.f1
helpviewer_keywords:
- Updates Statistics Task dialog box
ms.assetid: 22902fd0-eb39-4f18-af94-3fcb69d2a3a4
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 486ef2da96785ed200900f497435117ef6437cb5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645597"
---
# <a name="update-statistics-task-maintenance-plan"></a><span data-ttu-id="3cc5b-102">[統計の更新タスク] (メンテナンス プラン)</span><span class="sxs-lookup"><span data-stu-id="3cc5b-102">Update Statistics Task (Maintenance Plan)</span></span>
  <span data-ttu-id="3cc5b-103">**[統計の更新タスク]** ダイアログ ボックスを使用して、テーブルおよびインデックスのデータに関する [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 情報を更新します。</span><span class="sxs-lookup"><span data-stu-id="3cc5b-103">Use the **Update Statistics Task** dialog to update [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] information about the data in the tables and indexes.</span></span> <span data-ttu-id="3cc5b-104">このタスクでは、データベース内のユーザー テーブルに定義されている各インデックスの分布統計のサンプル データを取り直します。</span><span class="sxs-lookup"><span data-stu-id="3cc5b-104">This task resamples the distribution statistics of each index created on user tables in the database.</span></span> <span data-ttu-id="3cc5b-105">分布統計は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを処理する際のテーブル内の移動の最適化に使用されます。</span><span class="sxs-lookup"><span data-stu-id="3cc5b-105">The distribution statistics are used by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to optimize navigation through tables during the processing of [!INCLUDE[tsql](../../includes/tsql-md.md)] statements.</span></span> <span data-ttu-id="3cc5b-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は、分布統計を自動的に作成するために、各インデックスに対応するテーブルのデータを定期的にサンプリングしています。</span><span class="sxs-lookup"><span data-stu-id="3cc5b-106">To build the distribution statistics automatically, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] periodically samples the data in the corresponding table for each index.</span></span> <span data-ttu-id="3cc5b-107">サンプリングするサイズは、テーブルに含まれる行数とデータ更新の頻度に基づいて決められます。</span><span class="sxs-lookup"><span data-stu-id="3cc5b-107">This size of the sample is based on the number of rows in the table and the frequency of data modification.</span></span> <span data-ttu-id="3cc5b-108">このオプションを使用すると、サンプリングされるテーブル データの比率を指定して、サンプリングを追加実行することができます。</span><span class="sxs-lookup"><span data-stu-id="3cc5b-108">Use this option to perform an additional sampling using the specified percentage of data in the tables.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="3cc5b-109">は、この情報を使用してより適切なクエリ プランを作成します。</span><span class="sxs-lookup"><span data-stu-id="3cc5b-109">uses this information to create better query plans.</span></span>  
  
 <span data-ttu-id="3cc5b-110">このタスクでは、UPDATE STATISTICS ステートメントが実行されます。</span><span class="sxs-lookup"><span data-stu-id="3cc5b-110">This task executes the UPDATE STATISTICS statement.</span></span>  
  
## <a name="options"></a><span data-ttu-id="3cc5b-111">Options</span><span class="sxs-lookup"><span data-stu-id="3cc5b-111">Options</span></span>  
 <span data-ttu-id="3cc5b-112">**接続**</span><span class="sxs-lookup"><span data-stu-id="3cc5b-112">**Connection**</span></span>  
 <span data-ttu-id="3cc5b-113">このタスクを実行するときに使用するサーバー接続を選択します。</span><span class="sxs-lookup"><span data-stu-id="3cc5b-113">Select the server connection to use when performing this task.</span></span>  
  
 <span data-ttu-id="3cc5b-114">**[新規作成]**</span><span class="sxs-lookup"><span data-stu-id="3cc5b-114">**New**</span></span>  
 <span data-ttu-id="3cc5b-115">このタスクを実行するときに使用する新しいサーバー接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="3cc5b-115">Create a new server connection to use when performing this task.</span></span> <span data-ttu-id="3cc5b-116">**[新しい接続]** ダイアログ ボックスについては、後で説明します。</span><span class="sxs-lookup"><span data-stu-id="3cc5b-116">The **New Connection** dialog box is described below.</span></span>  
  
 <span data-ttu-id="3cc5b-117">**データベース**</span><span class="sxs-lookup"><span data-stu-id="3cc5b-117">**Databases**</span></span>  
 <span data-ttu-id="3cc5b-118">このタスクで操作するデータベースを指定します。</span><span class="sxs-lookup"><span data-stu-id="3cc5b-118">Specify the databases affected by this task.</span></span>  
  
-   <span data-ttu-id="3cc5b-119">**[すべてのデータベース]**</span><span class="sxs-lookup"><span data-stu-id="3cc5b-119">**All databases**</span></span>  
  
     <span data-ttu-id="3cc5b-120">すべての [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベース (tempdb を除く) を対象として、メンテナンス タスクを実行するメンテナンス プランを生成します。</span><span class="sxs-lookup"><span data-stu-id="3cc5b-120">Generate a maintenance plan that runs maintenance tasks against all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases, except tempdb.</span></span>  
  
-   <span data-ttu-id="3cc5b-121">**[すべてのシステム データベース]**</span><span class="sxs-lookup"><span data-stu-id="3cc5b-121">**All system databases**</span></span>  
  
     <span data-ttu-id="3cc5b-122">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のシステム データベース (tempdb を除く) を対象として、メンテナンス タスクを実行するメンテナンス プランを生成します。</span><span class="sxs-lookup"><span data-stu-id="3cc5b-122">Generate a maintenance plan that runs maintenance tasks against each of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system databases except tempdb.</span></span> <span data-ttu-id="3cc5b-123">ユーザーが作成したデータベースではメンテナンス タスクは実行されません。</span><span class="sxs-lookup"><span data-stu-id="3cc5b-123">No maintenance tasks are run against user-created databases.</span></span>  
  
-   <span data-ttu-id="3cc5b-124">**[すべてのユーザー データベース]**</span><span class="sxs-lookup"><span data-stu-id="3cc5b-124">**All user databases**</span></span>  
  
     <span data-ttu-id="3cc5b-125">ユーザーが作成したすべてのデータベースを対象として、メンテナンス タスクを実行するメンテナンス プランを生成します。</span><span class="sxs-lookup"><span data-stu-id="3cc5b-125">Generate a maintenance plan that runs maintenance tasks against all user-created databases.</span></span> <span data-ttu-id="3cc5b-126">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のシステム データベースではメンテナンス タスクは実行されません。</span><span class="sxs-lookup"><span data-stu-id="3cc5b-126">No maintenance tasks are run against the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system databases.</span></span>  
  
-   <span data-ttu-id="3cc5b-127">**[これらのデータベース]**</span><span class="sxs-lookup"><span data-stu-id="3cc5b-127">**These specific databases**</span></span>  
  
     <span data-ttu-id="3cc5b-128">選択されたデータベースだけを対象として、メンテナンス タスクを実行するメンテナンス プランを生成します。</span><span class="sxs-lookup"><span data-stu-id="3cc5b-128">Generate a maintenance plan that runs maintenance tasks against only those databases that are selected.</span></span> <span data-ttu-id="3cc5b-129">このオプションをオンにする場合は、少なくとも 1 つのデータベースが一覧内で選択されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="3cc5b-129">At least one database in the list must be selected if this option is chosen.</span></span>  
  
 <span data-ttu-id="3cc5b-130">**メモ** メンテナンス プランは、互換性レベルが 80 以上に設定されているデータベースに対してのみ実行されます。</span><span class="sxs-lookup"><span data-stu-id="3cc5b-130">**Note** Maintenance plans only run against databases set to compatibility level 80 or higher.</span></span> <span data-ttu-id="3cc5b-131">互換性レベルが 70 以下に設定されているデータベースは表示されません。</span><span class="sxs-lookup"><span data-stu-id="3cc5b-131">Databases set to compatibility level 70 or lower are not displayed.</span></span>  
  
 <span data-ttu-id="3cc5b-132">**Object**</span><span class="sxs-lookup"><span data-stu-id="3cc5b-132">**Object**</span></span>  
 <span data-ttu-id="3cc5b-133">**[選択]** グリッドでテーブル、ビュー、または両方を表示するように制限します。</span><span class="sxs-lookup"><span data-stu-id="3cc5b-133">Limit the **Selection** grid to display tables, views, or both.</span></span>  
  
 <span data-ttu-id="3cc5b-134">**選択内容**</span><span class="sxs-lookup"><span data-stu-id="3cc5b-134">**Selection**</span></span>  
 <span data-ttu-id="3cc5b-135">このタスクの対象とするテーブルまたはインデックスを指定します。</span><span class="sxs-lookup"><span data-stu-id="3cc5b-135">Specify the tables or indexes affected by this task.</span></span> <span data-ttu-id="3cc5b-136">[オブジェクト] ボックスで **[テーブルとビュー]** が選択されている場合は、このオプションは利用できません。</span><span class="sxs-lookup"><span data-stu-id="3cc5b-136">Not available when **Tables and Views** is selected in the Object box.</span></span>  
  
 <span data-ttu-id="3cc5b-137">**[すべての既存の統計]**</span><span class="sxs-lookup"><span data-stu-id="3cc5b-137">**All existing statistics**</span></span>  
 <span data-ttu-id="3cc5b-138">列とインデックスの統計を両方とも更新します。</span><span class="sxs-lookup"><span data-stu-id="3cc5b-138">Update statistics for both columns and indexes.</span></span>  
  
 <span data-ttu-id="3cc5b-139">**[列統計のみ]**</span><span class="sxs-lookup"><span data-stu-id="3cc5b-139">**Column statistics only**</span></span>  
 <span data-ttu-id="3cc5b-140">列統計のみを更新します。</span><span class="sxs-lookup"><span data-stu-id="3cc5b-140">Only update column statistics.</span></span>  
  
 <span data-ttu-id="3cc5b-141">**[インデックス統計のみ]**</span><span class="sxs-lookup"><span data-stu-id="3cc5b-141">**Index statistics only**</span></span>  
 <span data-ttu-id="3cc5b-142">インデックス統計のみを更新します。</span><span class="sxs-lookup"><span data-stu-id="3cc5b-142">Only update index statistics.</span></span>  
  
 <span data-ttu-id="3cc5b-143">**[スキャンの種類]**</span><span class="sxs-lookup"><span data-stu-id="3cc5b-143">**Scan type**</span></span>  
 <span data-ttu-id="3cc5b-144">更新された統計情報を収集するスキャンの種類です。</span><span class="sxs-lookup"><span data-stu-id="3cc5b-144">Type of scan used to gather updated statistics.</span></span>  
  
 <span data-ttu-id="3cc5b-145">**[フル スキャン]**</span><span class="sxs-lookup"><span data-stu-id="3cc5b-145">**Full scan**</span></span>  
 <span data-ttu-id="3cc5b-146">統計を収集する際、テーブルまたはビューのすべての行を読み取ります。</span><span class="sxs-lookup"><span data-stu-id="3cc5b-146">Read all rows in the table or view to gather the statistics.</span></span>  
  
 <span data-ttu-id="3cc5b-147">**[サンプル対象]**</span><span class="sxs-lookup"><span data-stu-id="3cc5b-147">**Sample by**</span></span>  
 <span data-ttu-id="3cc5b-148">大きなテーブルやビューの統計を収集するときにサンプリングする、テーブルまたはインデックス付きビューの割合や行数を指定します。</span><span class="sxs-lookup"><span data-stu-id="3cc5b-148">Specify the percentage of the table or indexed view, or the number of rows to sample when collecting statistics for larger tables or views.</span></span>  
  
 <span data-ttu-id="3cc5b-149">**[T-SQL の表示]**</span><span class="sxs-lookup"><span data-stu-id="3cc5b-149">**View T-SQL**</span></span>  
 <span data-ttu-id="3cc5b-150">選択したオプションに基づき、このタスクでサーバーに対して実行される [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを表示します。</span><span class="sxs-lookup"><span data-stu-id="3cc5b-150">View the [!INCLUDE[tsql](../../includes/tsql-md.md)] statements performed against the server for this task, based on the selected options.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3cc5b-151">影響を受けるオブジェクトが大量にある場合は、表示にかなりの時間を要する場合があります。</span><span class="sxs-lookup"><span data-stu-id="3cc5b-151">When the number of objects affected is large, this display can take a considerable amount of time.</span></span>  
  
## <a name="new-connection-dialog-box"></a><span data-ttu-id="3cc5b-152">[新しい接続] ダイアログ ボックス</span><span class="sxs-lookup"><span data-stu-id="3cc5b-152">New Connection Dialog Box</span></span>  
 <span data-ttu-id="3cc5b-153">**接続名**</span><span class="sxs-lookup"><span data-stu-id="3cc5b-153">**Connection name**</span></span>  
 <span data-ttu-id="3cc5b-154">新しい接続の名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="3cc5b-154">Enter a name for the new connection.</span></span>  
  
 <span data-ttu-id="3cc5b-155">**[サーバー名の選択または入力]**</span><span class="sxs-lookup"><span data-stu-id="3cc5b-155">**Select or enter a server name**</span></span>  
 <span data-ttu-id="3cc5b-156">このタスクを実行するときに接続するサーバーを選択します。</span><span class="sxs-lookup"><span data-stu-id="3cc5b-156">Select a server to connect to when performing this task.</span></span>  
  
 <span data-ttu-id="3cc5b-157">**[更新]**</span><span class="sxs-lookup"><span data-stu-id="3cc5b-157">**Refresh**</span></span>  
 <span data-ttu-id="3cc5b-158">使用できるサーバーの一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="3cc5b-158">Refresh the list of available servers.</span></span>  
  
 <span data-ttu-id="3cc5b-159">**[サーバーにログオンするための情報の入力]**</span><span class="sxs-lookup"><span data-stu-id="3cc5b-159">**Enter information to log on to the server**</span></span>  
 <span data-ttu-id="3cc5b-160">サーバーの認証情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="3cc5b-160">Specify how to authenticate against the server.</span></span>  
  
 <span data-ttu-id="3cc5b-161">**[Windows NT の統合セキュリティを使用する]**</span><span class="sxs-lookup"><span data-stu-id="3cc5b-161">**Use Windows integrated security**</span></span>  
 <span data-ttu-id="3cc5b-162">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 認証を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="3cc5b-162">Connect to an instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] with [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Authentication.</span></span>  
  
 <span data-ttu-id="3cc5b-163">**[特定のユーザー名とパスワードを使用する]**</span><span class="sxs-lookup"><span data-stu-id="3cc5b-163">**Use a specific user name and password**</span></span>  
 <span data-ttu-id="3cc5b-164">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="3cc5b-164">Connect to an instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="3cc5b-165">このオプションは利用できません。</span><span class="sxs-lookup"><span data-stu-id="3cc5b-165">This option is not available.</span></span>  
  
 <span data-ttu-id="3cc5b-166">**ユーザー名**</span><span class="sxs-lookup"><span data-stu-id="3cc5b-166">**User name**</span></span>  
 <span data-ttu-id="3cc5b-167">認証に使用する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインを指定します。</span><span class="sxs-lookup"><span data-stu-id="3cc5b-167">Provide a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login to use when authenticating.</span></span> <span data-ttu-id="3cc5b-168">このオプションは利用できません。</span><span class="sxs-lookup"><span data-stu-id="3cc5b-168">This option is not available.</span></span>  
  
 <span data-ttu-id="3cc5b-169">**パスワード**</span><span class="sxs-lookup"><span data-stu-id="3cc5b-169">**Password**</span></span>  
 <span data-ttu-id="3cc5b-170">認証に使用するパスワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="3cc5b-170">Provide a password to use when authenticating.</span></span> <span data-ttu-id="3cc5b-171">このオプションは利用できません。</span><span class="sxs-lookup"><span data-stu-id="3cc5b-171">This option is not available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cc5b-172">参照</span><span class="sxs-lookup"><span data-stu-id="3cc5b-172">See Also</span></span>  
 [<span data-ttu-id="3cc5b-173">UPDATE STATISTICS &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="3cc5b-173">UPDATE STATISTICS &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/update-statistics-transact-sql)  
  
  
