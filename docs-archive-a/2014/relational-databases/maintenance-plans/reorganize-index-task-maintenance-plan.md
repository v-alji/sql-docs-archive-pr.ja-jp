---
title: '[インデックスの再構成タスク] (メンテナンス プラン) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.maint.defrag.f1
helpviewer_keywords:
- Reorganize Index Task dialog box
ms.assetid: e9cbebbd-f36f-4176-9832-382a46ac946c
author: rothja
ms.author: jroth
ms.openlocfilehash: 0bbb154045b781f8a92dfce9c9d2f6ee2d819c17
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639479"
---
# <a name="reorganize-index-task-maintenance-plan"></a><span data-ttu-id="c6b68-102">[インデックスの再構成タスク] (メンテナンス プラン)</span><span class="sxs-lookup"><span data-stu-id="c6b68-102">Reorganize Index Task (Maintenance Plan)</span></span>
  <span data-ttu-id="c6b68-103">**[インデックスの再構成タスク]** ダイアログを使用すると、インデックス ページを効率的な検索順になるように移動できます。</span><span class="sxs-lookup"><span data-stu-id="c6b68-103">Use the **ReorganizeIndex Task** dialog to move index pages into a more efficient search order.</span></span> <span data-ttu-id="c6b68-104">このタスクでは、 `ALTER INDEX REORGANIZE` データベースに [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="c6b68-104">This task uses the `ALTER INDEX REORGANIZE` statement with [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] databases.</span></span>  
  
## <a name="options"></a><span data-ttu-id="c6b68-105">オプション</span><span class="sxs-lookup"><span data-stu-id="c6b68-105">Options</span></span>  
 <span data-ttu-id="c6b68-106">**Connection**</span><span class="sxs-lookup"><span data-stu-id="c6b68-106">**Connection**</span></span>  
 <span data-ttu-id="c6b68-107">このタスクを実行するときに使用するサーバー接続を選択します。</span><span class="sxs-lookup"><span data-stu-id="c6b68-107">Select the server connection to use when performing this task.</span></span>  
  
 <span data-ttu-id="c6b68-108">**[新規作成]**</span><span class="sxs-lookup"><span data-stu-id="c6b68-108">**New**</span></span>  
 <span data-ttu-id="c6b68-109">このタスクを実行するときに使用する新しいサーバー接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="c6b68-109">Create a new server connection to use when performing this task.</span></span> <span data-ttu-id="c6b68-110">**[新しい接続]** ダイアログ ボックスについては、後で説明します。</span><span class="sxs-lookup"><span data-stu-id="c6b68-110">The **New Connection** dialog box is described below.</span></span>  
  
 <span data-ttu-id="c6b68-111">**データベース**</span><span class="sxs-lookup"><span data-stu-id="c6b68-111">**Databases**</span></span>  
 <span data-ttu-id="c6b68-112">このタスクで操作するデータベースを指定します。</span><span class="sxs-lookup"><span data-stu-id="c6b68-112">Specify the databases affected by this task.</span></span>  
  
-   <span data-ttu-id="c6b68-113">**[すべてのデータベース]**</span><span class="sxs-lookup"><span data-stu-id="c6b68-113">**All databases**</span></span>  
  
     <span data-ttu-id="c6b68-114">すべての [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベース (tempdb を除く) を対象として、メンテナンス タスクを実行するメンテナンス プランを生成します。</span><span class="sxs-lookup"><span data-stu-id="c6b68-114">Generate a maintenance plan that runs maintenance tasks against all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases except tempdb.</span></span>  
  
-   <span data-ttu-id="c6b68-115">**[すべてのシステム データベース]**</span><span class="sxs-lookup"><span data-stu-id="c6b68-115">**All system databases**</span></span>  
  
     <span data-ttu-id="c6b68-116">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のシステム データベース ( **tempdb**を除く) を対象として、メンテナンス タスクを実行するメンテナンス プランを生成します。</span><span class="sxs-lookup"><span data-stu-id="c6b68-116">Generate a maintenance plan that runs maintenance tasks against each of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system databases except **tempdb**.</span></span> <span data-ttu-id="c6b68-117">ユーザーが作成したデータベースではメンテナンス タスクは実行されません。</span><span class="sxs-lookup"><span data-stu-id="c6b68-117">No maintenance tasks are run against user-created databases.</span></span>  
  
-   <span data-ttu-id="c6b68-118">**[すべてのユーザー データベース]**</span><span class="sxs-lookup"><span data-stu-id="c6b68-118">**All user databases**</span></span>  
  
     <span data-ttu-id="c6b68-119">ユーザーが作成したすべてのデータベースを対象として、メンテナンス タスクを実行するメンテナンス プランを生成します。</span><span class="sxs-lookup"><span data-stu-id="c6b68-119">Generate a maintenance plan that runs maintenance tasks against all user-created databases.</span></span> <span data-ttu-id="c6b68-120">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のシステム データベースではメンテナンス タスクは実行されません。</span><span class="sxs-lookup"><span data-stu-id="c6b68-120">No maintenance tasks are run against the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system databases.</span></span>  
  
-   <span data-ttu-id="c6b68-121">**[これらのデータベース]**</span><span class="sxs-lookup"><span data-stu-id="c6b68-121">**These specific databases**</span></span>  
  
     <span data-ttu-id="c6b68-122">選択されたデータベースだけを対象として、メンテナンス タスクを実行するメンテナンス プランを生成します。</span><span class="sxs-lookup"><span data-stu-id="c6b68-122">Generate a maintenance plan that runs maintenance tasks against only those databases that are selected.</span></span> <span data-ttu-id="c6b68-123">このオプションをオンにする場合は、少なくとも 1 つのデータベースが一覧内で選択されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="c6b68-123">At least one database in the list must be selected if this option is chosen.</span></span>  
  
 <span data-ttu-id="c6b68-124">**Object**</span><span class="sxs-lookup"><span data-stu-id="c6b68-124">**Object**</span></span>  
 <span data-ttu-id="c6b68-125">**[選択]** グリッドでテーブル、ビュー、または両方を表示するように制限します。</span><span class="sxs-lookup"><span data-stu-id="c6b68-125">Limit the **Selection** grid to display tables, views, or both.</span></span>  
  
 <span data-ttu-id="c6b68-126">**選択内容**</span><span class="sxs-lookup"><span data-stu-id="c6b68-126">**Selection**</span></span>  
 <span data-ttu-id="c6b68-127">このタスクの対象とするテーブルまたはインデックスを指定します。</span><span class="sxs-lookup"><span data-stu-id="c6b68-127">Specify the tables or indexes affected by this task.</span></span> <span data-ttu-id="c6b68-128">**[オブジェクト]** ボックスで **[テーブルとビュー]** が選択されている場合は、このオプションを使用できません。</span><span class="sxs-lookup"><span data-stu-id="c6b68-128">Not available when **Tables and Views** is selected in the **Object** box.</span></span>  
  
 <span data-ttu-id="c6b68-129">**[ラージ オブジェクトを圧縮する]**</span><span class="sxs-lookup"><span data-stu-id="c6b68-129">**Compact large objects**</span></span>  
 <span data-ttu-id="c6b68-130">可能であれば、テーブルとビューに対する領域の割り当てを解除します。</span><span class="sxs-lookup"><span data-stu-id="c6b68-130">Deallocate space for tables and views when possible.</span></span> <span data-ttu-id="c6b68-131">このオプションでは `ALTER INDEX LOB_COMPACTION = ON`を使用します。</span><span class="sxs-lookup"><span data-stu-id="c6b68-131">This option uses `ALTER INDEX LOB_COMPACTION = ON`.</span></span>  
  
 <span data-ttu-id="c6b68-132">**[T-SQL の表示]**</span><span class="sxs-lookup"><span data-stu-id="c6b68-132">**View T-SQL**</span></span>  
 <span data-ttu-id="c6b68-133">選択したオプションに基づき、このタスクでサーバーに対して実行される [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを表示します。</span><span class="sxs-lookup"><span data-stu-id="c6b68-133">View the [!INCLUDE[tsql](../../includes/tsql-md.md)] statements performed against the server for this task, based on the selected options.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c6b68-134">影響を受けるオブジェクトが大量にある場合は、表示にかなりの時間を要する場合があります。</span><span class="sxs-lookup"><span data-stu-id="c6b68-134">When the number of objects affected is large, this display can take a considerable amount of time.</span></span>  
  
## <a name="new-connection-dialog-box"></a><span data-ttu-id="c6b68-135">[新しい接続] ダイアログ ボックス</span><span class="sxs-lookup"><span data-stu-id="c6b68-135">New Connection Dialog Box</span></span>  
 <span data-ttu-id="c6b68-136">**[接続名]**</span><span class="sxs-lookup"><span data-stu-id="c6b68-136">**Connection name**</span></span>  
 <span data-ttu-id="c6b68-137">新しい接続の名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="c6b68-137">Enter a name for the new connection.</span></span>  
  
 <span data-ttu-id="c6b68-138">**[サーバー名の選択または入力]**</span><span class="sxs-lookup"><span data-stu-id="c6b68-138">**Select or enter a server name**</span></span>  
 <span data-ttu-id="c6b68-139">このタスクを実行するときに接続するサーバーを選択します。</span><span class="sxs-lookup"><span data-stu-id="c6b68-139">Select a server to connect to when performing this task.</span></span>  
  
 <span data-ttu-id="c6b68-140">**[更新]**</span><span class="sxs-lookup"><span data-stu-id="c6b68-140">**Refresh**</span></span>  
 <span data-ttu-id="c6b68-141">使用できるサーバーの一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="c6b68-141">Refresh the list of available servers.</span></span>  
  
 <span data-ttu-id="c6b68-142">**[サーバーにログオンするための情報の入力]**</span><span class="sxs-lookup"><span data-stu-id="c6b68-142">**Enter information to log on to the server**</span></span>  
 <span data-ttu-id="c6b68-143">サーバーの認証情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="c6b68-143">Specify how to authenticate against the server.</span></span>  
  
 <span data-ttu-id="c6b68-144">**[Windows NT の統合セキュリティを使用する]**</span><span class="sxs-lookup"><span data-stu-id="c6b68-144">**Use Windows integrated security**</span></span>  
 <span data-ttu-id="c6b68-145">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Windows 認証を使用して [!INCLUDE[ssDE](../../includes/ssde-md.md)] [!INCLUDE[msCoName](../../includes/msconame-md.md)] のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="c6b68-145">Connect to an instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] with [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Authentication.</span></span>  
  
 <span data-ttu-id="c6b68-146">**[特定のユーザー名とパスワードを使用する]**</span><span class="sxs-lookup"><span data-stu-id="c6b68-146">**Use a specific user name and password**</span></span>  
 <span data-ttu-id="c6b68-147">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用して [!INCLUDE[ssDE](../../includes/ssde-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="c6b68-147">Connect to an instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="c6b68-148">このオプションは利用できません。</span><span class="sxs-lookup"><span data-stu-id="c6b68-148">This option is not available.</span></span>  
  
 <span data-ttu-id="c6b68-149">**ユーザー名**</span><span class="sxs-lookup"><span data-stu-id="c6b68-149">**User name**</span></span>  
 <span data-ttu-id="c6b68-150">認証に使用する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインを指定します。</span><span class="sxs-lookup"><span data-stu-id="c6b68-150">Provide a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login to use when authenticating.</span></span> <span data-ttu-id="c6b68-151">このオプションは利用できません。</span><span class="sxs-lookup"><span data-stu-id="c6b68-151">This option is not available.</span></span>  
  
 <span data-ttu-id="c6b68-152">**パスワード**</span><span class="sxs-lookup"><span data-stu-id="c6b68-152">**Password**</span></span>  
 <span data-ttu-id="c6b68-153">認証に使用するパスワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="c6b68-153">Provide a password to use when authenticating.</span></span> <span data-ttu-id="c6b68-154">このオプションは利用できません。</span><span class="sxs-lookup"><span data-stu-id="c6b68-154">This option is not available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6b68-155">参照</span><span class="sxs-lookup"><span data-stu-id="c6b68-155">See Also</span></span>  
 <span data-ttu-id="c6b68-156">[ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c6b68-156">[ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql) </span></span>  
 [<span data-ttu-id="c6b68-157">DBCC INDEXDEFRAG &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="c6b68-157">DBCC INDEXDEFRAG &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/database-console-commands/dbcc-indexdefrag-transact-sql)  
  
  
