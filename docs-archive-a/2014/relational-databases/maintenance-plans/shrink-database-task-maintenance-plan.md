---
title: '[データベースの圧縮タスク] (メンテナンス プラン) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.maint.shrink.f1
- Shrink Database Task
- Shrink Database(s) Task
helpviewer_keywords:
- Shrink Database Task dialog box
ms.assetid: a9874cac-cded-4145-9c38-8aafd267dbee
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: b8ee6060a4ee6ca3272434cf3d9115638a675e62
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715245"
---
# <a name="shrink-database-task-maintenance-plan"></a><span data-ttu-id="1e086-102">[データベースの圧縮タスク]\(メンテナンス プラン)</span><span class="sxs-lookup"><span data-stu-id="1e086-102">Shrink Database Task (Maintenance Plan)</span></span>
  <span data-ttu-id="1e086-103">**[データベースの圧縮タスク]** ダイアログを使用すると、選択されているデータベースのサイズを小さくするタスクを作成できます。</span><span class="sxs-lookup"><span data-stu-id="1e086-103">Use the **Shrink Database Task** dialog to create a task that attempts to reduce the size of the selected databases.</span></span> <span data-ttu-id="1e086-104">次に示すオプションを使用して、データベースを圧縮する際に残す未使用領域の割合をパーセント比率で指定します (指定値を大きくするほど、データベースは少ししか圧縮されなくなります)。</span><span class="sxs-lookup"><span data-stu-id="1e086-104">Use the options below to determine the amount of unused space to remain in the database after the database is shrunk (the larger the percentage, the less the database can shrink).</span></span> <span data-ttu-id="1e086-105">残される未使用領域の大きさは、データベースに格納されているデータの量に対する比率で決められます。</span><span class="sxs-lookup"><span data-stu-id="1e086-105">The value is based on the percentage of the actual data in the database.</span></span> <span data-ttu-id="1e086-106">たとえば、60 MB のデータと 40 MB の空き領域を含む 100 MB のデータベースに対して 50% の値を指定した場合、そのデータベースは、60 MB のデータと (60 MB の 50% に当たる) 30 MB の空き領域から成る 90 MB のデータベースに圧縮されます。</span><span class="sxs-lookup"><span data-stu-id="1e086-106">For example, a 100-MB database containing 60 MB of data and 40 MB of free space, with a free space percentage of 50 percent, would result in 60 MB of data and 30 MB of free space (because 50 percent of 60 MB is 30 MB).</span></span> <span data-ttu-id="1e086-107">削除されるのは、指定の割合を超える分の未使用領域だけです。</span><span class="sxs-lookup"><span data-stu-id="1e086-107">Only excess space in the database is eliminated.</span></span> <span data-ttu-id="1e086-108">有効値は、0 ～ 100 です。</span><span class="sxs-lookup"><span data-stu-id="1e086-108">Valid values are from 0 through 100.</span></span>  
  
 <span data-ttu-id="1e086-109">ファイルの末尾にあるデータのページを、ファイルの先頭に近い占有されていない領域に移動することにより、データ ファイルが圧縮され、領域が回復されます。</span><span class="sxs-lookup"><span data-stu-id="1e086-109">Shrinking data files recovers space by moving pages of data from the end of the file to unoccupied space closer to the front of the file.</span></span> <span data-ttu-id="1e086-110">ファイル末尾に十分な空き領域が作成された場合は、ファイル末尾のデータ ページの割り当てを解除して、ファイル システムに戻すことができます。</span><span class="sxs-lookup"><span data-stu-id="1e086-110">When enough free space is created at the end of the file, data pages at end of the file can deallocated and returned to the file system.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="1e086-111">ファイルを圧縮するために移動されたデータは、ファイル内のあらゆる使用可能な場所に分散される場合があります。</span><span class="sxs-lookup"><span data-stu-id="1e086-111">Data that is moved to shrink a file can be scattered to any available location in the file.</span></span> <span data-ttu-id="1e086-112">これにより、インデックスの断片化が発生し、広範なインデックスを検索するクエリのパフォーマンスが低下する場合があります。</span><span class="sxs-lookup"><span data-stu-id="1e086-112">This causes index fragmentation and can slow the performance of queries that search a range of the index.</span></span> <span data-ttu-id="1e086-113">断片化を解消するには、圧縮後にファイルのインデックスを再構築することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="1e086-113">To eliminate the fragmentation, consider rebuilding the indexes on the file after shrinking.</span></span>  
  
 <span data-ttu-id="1e086-114">このタスクでは、DBCC SHRINKDATABASE ステートメントが実行されます。</span><span class="sxs-lookup"><span data-stu-id="1e086-114">This task executes the DBCC SHRINKDATABASE statement.</span></span>  
  
## <a name="options"></a><span data-ttu-id="1e086-115">Options</span><span class="sxs-lookup"><span data-stu-id="1e086-115">Options</span></span>  
 <span data-ttu-id="1e086-116">**接続**</span><span class="sxs-lookup"><span data-stu-id="1e086-116">**Connection**</span></span>  
 <span data-ttu-id="1e086-117">このタスクを実行するときに使用するサーバー接続を選択します。</span><span class="sxs-lookup"><span data-stu-id="1e086-117">Select the server connection to use when performing this task.</span></span>  
  
 <span data-ttu-id="1e086-118">**[新規作成]**</span><span class="sxs-lookup"><span data-stu-id="1e086-118">**New**</span></span>  
 <span data-ttu-id="1e086-119">このタスクを実行するときに使用する新しいサーバー接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="1e086-119">Create a new server connection to use when performing this task.</span></span> <span data-ttu-id="1e086-120">**[新しい接続]** ダイアログ ボックスについては、後で説明します。</span><span class="sxs-lookup"><span data-stu-id="1e086-120">The **New Connection** dialog box is described below.</span></span>  
  
 <span data-ttu-id="1e086-121">**データベース**</span><span class="sxs-lookup"><span data-stu-id="1e086-121">**Databases**</span></span>  
 <span data-ttu-id="1e086-122">このタスクで操作するデータベースを指定します。</span><span class="sxs-lookup"><span data-stu-id="1e086-122">Specify the databases affected by this task.</span></span>  
  
-   <span data-ttu-id="1e086-123">**[すべてのデータベース]**</span><span class="sxs-lookup"><span data-stu-id="1e086-123">**All databases**</span></span>  
  
     <span data-ttu-id="1e086-124">すべての [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベース (tempdb を除く) を対象として、メンテナンス タスクを実行するメンテナンス プランを生成します。</span><span class="sxs-lookup"><span data-stu-id="1e086-124">Generate a maintenance plan that runs maintenance tasks against all [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases except tempdb.</span></span>  
  
-   <span data-ttu-id="1e086-125">**[すべてのシステム データベース]**</span><span class="sxs-lookup"><span data-stu-id="1e086-125">**All system databases**</span></span>  
  
     <span data-ttu-id="1e086-126">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のシステム データベース (tempdb を除く) を対象として、メンテナンス タスクを実行するメンテナンス プランを生成します。</span><span class="sxs-lookup"><span data-stu-id="1e086-126">Generate a maintenance plan that runs maintenance tasks against each of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system databases except tempdb.</span></span> <span data-ttu-id="1e086-127">ユーザーが作成したデータベースではメンテナンス タスクは実行されません。</span><span class="sxs-lookup"><span data-stu-id="1e086-127">No maintenance tasks are run against user-created databases.</span></span>  
  
-   <span data-ttu-id="1e086-128">**[すべてのユーザー データベース]**</span><span class="sxs-lookup"><span data-stu-id="1e086-128">**All user databases**</span></span>  
  
     <span data-ttu-id="1e086-129">ユーザーが作成したすべてのデータベースを対象として、メンテナンス タスクを実行するメンテナンス プランを生成します。</span><span class="sxs-lookup"><span data-stu-id="1e086-129">Generate a maintenance plan that runs maintenance tasks against all user-created databases.</span></span> <span data-ttu-id="1e086-130">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のシステム データベースではメンテナンス タスクは実行されません。</span><span class="sxs-lookup"><span data-stu-id="1e086-130">No maintenance tasks are run against the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system databases.</span></span>  
  
-   <span data-ttu-id="1e086-131">**[これらのデータベース]**</span><span class="sxs-lookup"><span data-stu-id="1e086-131">**These databases**</span></span>  
  
     <span data-ttu-id="1e086-132">選択されたデータベースだけを対象として、メンテナンス タスクを実行するメンテナンス プランを生成します。</span><span class="sxs-lookup"><span data-stu-id="1e086-132">Generate a maintenance plan that runs maintenance tasks against only those databases that are selected.</span></span> <span data-ttu-id="1e086-133">このオプションをオンにする場合は、少なくとも 1 つのデータベースが一覧内で選択されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="1e086-133">At least one database in the list must be selected if this option is chosen.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="1e086-134">メンテナンス プランは、互換性レベルが 80 以上に設定されているデータベースに対してのみ実行されます。</span><span class="sxs-lookup"><span data-stu-id="1e086-134">Maintenance plans only run against databases set to compatibility level 80 or higher.</span></span> <span data-ttu-id="1e086-135">互換性レベルが 70 以下に設定されているデータベースは表示されません。</span><span class="sxs-lookup"><span data-stu-id="1e086-135">Databases set to compatibility level 70 or lower are not displayed.</span></span>  
  
 <span data-ttu-id="1e086-136">**[次のサイズに到達したらデータベースを圧縮]**</span><span class="sxs-lookup"><span data-stu-id="1e086-136">**Shrink database when it grows beyond**</span></span>  
 <span data-ttu-id="1e086-137">このタスクが実行されるときのサイズをメガバイト単位で指定します。</span><span class="sxs-lookup"><span data-stu-id="1e086-137">Specify the size in megabytes that causes the task to execute.</span></span>  
  
 <span data-ttu-id="1e086-138">**[圧縮後に残す空き領域]**</span><span class="sxs-lookup"><span data-stu-id="1e086-138">**Amount of free space to remain after shrink**</span></span>  
 <span data-ttu-id="1e086-139">データベース ファイルの空き領域がこのサイズに達したら圧縮を停止します。</span><span class="sxs-lookup"><span data-stu-id="1e086-139">Stop shrinking when free space in database files reaches this size.</span></span>  
  
 <span data-ttu-id="1e086-140">**[T-SQL の表示]**</span><span class="sxs-lookup"><span data-stu-id="1e086-140">**View T-SQL**</span></span>  
 <span data-ttu-id="1e086-141">選択したオプションに基づき、このタスクでサーバーに対して実行される [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを表示します。</span><span class="sxs-lookup"><span data-stu-id="1e086-141">View the [!INCLUDE[tsql](../../includes/tsql-md.md)] statements performed against the server for this task, based on the selected options.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1e086-142">影響を受けるオブジェクトが大量にある場合は、表示にかなりの時間を要する場合があります。</span><span class="sxs-lookup"><span data-stu-id="1e086-142">When the number of objects affected is large, this display can take a considerable amount of time.</span></span>  
  
## <a name="new-connection-dialog-box"></a><span data-ttu-id="1e086-143">[新しい接続] ダイアログ ボックス</span><span class="sxs-lookup"><span data-stu-id="1e086-143">New Connection Dialog Box</span></span>  
 <span data-ttu-id="1e086-144">**接続名**</span><span class="sxs-lookup"><span data-stu-id="1e086-144">**Connection name**</span></span>  
 <span data-ttu-id="1e086-145">新しい接続の名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="1e086-145">Enter a name for the new connection.</span></span>  
  
 <span data-ttu-id="1e086-146">**[サーバー名の選択または入力]**</span><span class="sxs-lookup"><span data-stu-id="1e086-146">**Select or enter a server name**</span></span>  
 <span data-ttu-id="1e086-147">このタスクを実行するときに接続するサーバーを選択します。</span><span class="sxs-lookup"><span data-stu-id="1e086-147">Select a server to connect to when performing this task.</span></span>  
  
 <span data-ttu-id="1e086-148">**[更新]**</span><span class="sxs-lookup"><span data-stu-id="1e086-148">**Refresh**</span></span>  
 <span data-ttu-id="1e086-149">使用できるサーバーの一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="1e086-149">Refresh the list of available servers.</span></span>  
  
 <span data-ttu-id="1e086-150">**[サーバーにログオンするための情報の入力]**</span><span class="sxs-lookup"><span data-stu-id="1e086-150">**Enter information to log on to the server**</span></span>  
 <span data-ttu-id="1e086-151">サーバーの認証情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="1e086-151">Specify how to authenticate against the server.</span></span>  
  
 <span data-ttu-id="1e086-152">**[Windows NT の統合セキュリティを使用する]**</span><span class="sxs-lookup"><span data-stu-id="1e086-152">**Use Windows NT Integrated security**</span></span>  
 <span data-ttu-id="1e086-153">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 認証を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="1e086-153">Connect to an instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] with [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Authentication.</span></span>  
  
 <span data-ttu-id="1e086-154">**[特定のユーザー名とパスワードを使用する]**</span><span class="sxs-lookup"><span data-stu-id="1e086-154">**Use a specific user name and password**</span></span>  
 <span data-ttu-id="1e086-155">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="1e086-155">Connect to an instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="1e086-156">このオプションは利用できません。</span><span class="sxs-lookup"><span data-stu-id="1e086-156">This option is not available.</span></span>  
  
 <span data-ttu-id="1e086-157">**ユーザー名**</span><span class="sxs-lookup"><span data-stu-id="1e086-157">**User name**</span></span>  
 <span data-ttu-id="1e086-158">認証に使用する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインを指定します。</span><span class="sxs-lookup"><span data-stu-id="1e086-158">Provide a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login to use when authenticating.</span></span> <span data-ttu-id="1e086-159">このオプションは利用できません。</span><span class="sxs-lookup"><span data-stu-id="1e086-159">This option is not available.</span></span>  
  
 <span data-ttu-id="1e086-160">**パスワード**</span><span class="sxs-lookup"><span data-stu-id="1e086-160">**Password**</span></span>  
 <span data-ttu-id="1e086-161">認証に使用するパスワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="1e086-161">Provide a password to use when authenticating.</span></span> <span data-ttu-id="1e086-162">このオプションは利用できません。</span><span class="sxs-lookup"><span data-stu-id="1e086-162">This option is not available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e086-163">参照</span><span class="sxs-lookup"><span data-stu-id="1e086-163">See Also</span></span>  
 [<span data-ttu-id="1e086-164">DBCC SHRINKDATABASE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="1e086-164">DBCC SHRINKDATABASE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/database-console-commands/dbcc-shrinkdatabase-transact-sql)  
  
  
