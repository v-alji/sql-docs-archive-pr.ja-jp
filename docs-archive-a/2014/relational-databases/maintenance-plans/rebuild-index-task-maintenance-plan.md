---
title: '[インデックスの再構築タスク] (メンテナンス プラン) | Microsoft Docs'
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.maint.reindex.f1
- reindex
helpviewer_keywords:
- Rebuild Index Task dialog box
ms.assetid: 33e2940b-139f-4563-b0cb-5683f08bd879
author: rothja
ms.author: jroth
ms.openlocfilehash: bc9d7c85a72c34cee1ef7af8cb4b4f25f918a3fd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639481"
---
# <a name="rebuild-index-task-maintenance-plan"></a><span data-ttu-id="73020-102">[インデックスの再構築タスク] (メンテナンス プラン)</span><span class="sxs-lookup"><span data-stu-id="73020-102">Rebuild Index Task (Maintenance Plan)</span></span>
  <span data-ttu-id="73020-103">**[インデックスの再構築タスク]** ダイアログ ボックスを使用すると、データベースのテーブルに新しい FILL FACTOR でインデックスを再作成できます。</span><span class="sxs-lookup"><span data-stu-id="73020-103">Use the **Rebuild Index Task** dialog to re-create the indexes on the tables in the database with a new fill factor.</span></span> <span data-ttu-id="73020-104">FILL FACTOR は、後で拡張できるように、インデックスの各ページの空き領域の量を決定します。</span><span class="sxs-lookup"><span data-stu-id="73020-104">The fill factor determines the amount of empty space on each page in the index, to accommodate future expansion.</span></span> <span data-ttu-id="73020-105">FILL FACTOR が適用されるのはインデックスの作成時だけであるため、テーブルにデータが追加されるにつれて、各ページの空き容量は徐々に減少します。</span><span class="sxs-lookup"><span data-stu-id="73020-105">As data is added to the table, the free space fills because the fill factor is not maintained.</span></span> <span data-ttu-id="73020-106">データ ページおよびインデックス ページを再編成すると、再び空き領域を確保できます。</span><span class="sxs-lookup"><span data-stu-id="73020-106">Reorganizing data and index pages can re-establish the free space.</span></span>  
  
 <span data-ttu-id="73020-107">**[インデックスの再構築タスク]** では、ALTER INDEX ステートメントが使用されます。</span><span class="sxs-lookup"><span data-stu-id="73020-107">The **Rebuild Index Task** uses the ALTER INDEX statement.</span></span>  
  
## <a name="options"></a><span data-ttu-id="73020-108">Options</span><span class="sxs-lookup"><span data-stu-id="73020-108">Options</span></span>  
 <span data-ttu-id="73020-109">**接続**</span><span class="sxs-lookup"><span data-stu-id="73020-109">**Connection**</span></span>  
 <span data-ttu-id="73020-110">このタスクを実行するときに使用するサーバー接続を選択します。</span><span class="sxs-lookup"><span data-stu-id="73020-110">Select the server connection to use when performing this task.</span></span>  
  
 <span data-ttu-id="73020-111">**[新規作成]**</span><span class="sxs-lookup"><span data-stu-id="73020-111">**New**</span></span>  
 <span data-ttu-id="73020-112">このタスクを実行するときに使用する新しいサーバー接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="73020-112">Create a new server connection to use when performing this task.</span></span> <span data-ttu-id="73020-113">**[新しい接続]** ダイアログ ボックスについては、後で説明します。</span><span class="sxs-lookup"><span data-stu-id="73020-113">The **New Connection** dialog box is described below.</span></span>  
  
 <span data-ttu-id="73020-114">**データベース**</span><span class="sxs-lookup"><span data-stu-id="73020-114">**Databases**</span></span>  
 <span data-ttu-id="73020-115">このタスクで操作するデータベースを指定します。</span><span class="sxs-lookup"><span data-stu-id="73020-115">Specify the databases affected by this task.</span></span>  
  
-   <span data-ttu-id="73020-116">**[すべてのデータベース]**</span><span class="sxs-lookup"><span data-stu-id="73020-116">**All databases**</span></span>  
  
     <span data-ttu-id="73020-117">すべての [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベース (tempdb を除く) を対象として、メンテナンス タスクを実行するメンテナンス プランを生成します。</span><span class="sxs-lookup"><span data-stu-id="73020-117">Generate a maintenance plan that runs maintenance tasks against all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases except tempdb.</span></span>  
  
-   <span data-ttu-id="73020-118">**[すべてのシステム データベース]**</span><span class="sxs-lookup"><span data-stu-id="73020-118">**All system databases**</span></span>  
  
     <span data-ttu-id="73020-119">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のシステム データベース (tempdb を除く) を対象として、メンテナンス タスクを実行するメンテナンス プランを生成します。</span><span class="sxs-lookup"><span data-stu-id="73020-119">Generate a maintenance plan that runs maintenance tasks against each of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system databases except tempdb.</span></span> <span data-ttu-id="73020-120">ユーザーが作成したデータベースではメンテナンス タスクは実行されません。</span><span class="sxs-lookup"><span data-stu-id="73020-120">No maintenance tasks are run against user-created databases.</span></span>  
  
-   <span data-ttu-id="73020-121">**[すべてのユーザー データベース]**</span><span class="sxs-lookup"><span data-stu-id="73020-121">**All user databases**</span></span>  
  
     <span data-ttu-id="73020-122">ユーザーが作成したすべてのデータベースを対象として、メンテナンス タスクを実行するメンテナンス プランを生成します。</span><span class="sxs-lookup"><span data-stu-id="73020-122">Generate a maintenance plan that runs maintenance tasks against all user-created databases.</span></span> <span data-ttu-id="73020-123">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のシステム データベースではメンテナンス タスクは実行されません。</span><span class="sxs-lookup"><span data-stu-id="73020-123">No maintenance tasks are run against the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system databases.</span></span>  
  
-   <span data-ttu-id="73020-124">**[これらのデータベース]**</span><span class="sxs-lookup"><span data-stu-id="73020-124">**These specific databases**</span></span>  
  
     <span data-ttu-id="73020-125">選択されたデータベースだけを対象として、メンテナンス タスクを実行するメンテナンス プランを生成します。</span><span class="sxs-lookup"><span data-stu-id="73020-125">Generate a maintenance plan that runs maintenance tasks against only those databases that are selected.</span></span> <span data-ttu-id="73020-126">このオプションをオンにする場合は、少なくとも 1 つのデータベースが一覧内で選択されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="73020-126">At least one database in the list must be selected if this option is chosen.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="73020-127">メンテナンス プランは、互換性レベルが 80 以上に設定されているデータベースに対してのみ実行されます。</span><span class="sxs-lookup"><span data-stu-id="73020-127">Maintenance plans only run against databases set to compatibility level 80 or higher.</span></span> <span data-ttu-id="73020-128">互換性レベルが 70 以下に設定されているデータベースは表示されません。</span><span class="sxs-lookup"><span data-stu-id="73020-128">Databases set to compatibility level 70 or lower are not displayed.</span></span>  
  
 <span data-ttu-id="73020-129">**Object**</span><span class="sxs-lookup"><span data-stu-id="73020-129">**Object**</span></span>  
 <span data-ttu-id="73020-130">**[選択]** グリッドでテーブル、ビュー、または両方を表示するように制限します。</span><span class="sxs-lookup"><span data-stu-id="73020-130">Limit the **Selection** grid to display tables, views, or both.</span></span>  
  
 <span data-ttu-id="73020-131">**選択内容**</span><span class="sxs-lookup"><span data-stu-id="73020-131">**Selection**</span></span>  
 <span data-ttu-id="73020-132">このタスクの対象とするテーブルまたはインデックスを指定します。</span><span class="sxs-lookup"><span data-stu-id="73020-132">Specify the tables or indexes affected by this task.</span></span> <span data-ttu-id="73020-133">[オブジェクト] ボックスで **[テーブルとビュー]** が選択されている場合は、このオプションは利用できません。</span><span class="sxs-lookup"><span data-stu-id="73020-133">Not available when **Tables and Views** is selected in the Object box.</span></span>  
  
 <span data-ttu-id="73020-134">**[既定の空き領域を使用してページを再構成する]**</span><span class="sxs-lookup"><span data-stu-id="73020-134">**Reorganize pages with the default amount of free space**</span></span>  
 <span data-ttu-id="73020-135">データベース内のテーブルに定義されているインデックスを削除し、インデックスの作成時に指定された FILL FACTOR を使用して、新しいインデックスを再作成します。</span><span class="sxs-lookup"><span data-stu-id="73020-135">Drop the indexes on the tables in the database and re-create them with the fill factor that was specified when the indexes were created.</span></span>  
  
 <span data-ttu-id="73020-136">**ページごとの空き領域の割合をに変更する**</span><span class="sxs-lookup"><span data-stu-id="73020-136">**Change free space per page percentage to**</span></span>  
 <span data-ttu-id="73020-137">データベース内のテーブルに定義されているインデックスを削除し、指定した割合の空き領域が各インデックス ページに確保されるように自動的に計算される FILL FACTOR の値を使用してインデックスを再作成します。</span><span class="sxs-lookup"><span data-stu-id="73020-137">Drop the indexes on the tables in the database and re-create them with a new, automatically calculated fill factor, thereby reserving the specified amount of free space on the index pages.</span></span> <span data-ttu-id="73020-138">指定するパーセント値を大きくすると、インデックス ページに確保される空き領域が増えて、より多くのデータをインデックスに追加できるようになります。</span><span class="sxs-lookup"><span data-stu-id="73020-138">The higher the percentage, the more free space is reserved on the index pages, and the larger the index grows.</span></span> <span data-ttu-id="73020-139">有効値は、0 ～ 100 です。</span><span class="sxs-lookup"><span data-stu-id="73020-139">Valid values are from 0 through 100.</span></span>  
  
 <span data-ttu-id="73020-140">**[tempdb の結果を並べ替える]**</span><span class="sxs-lookup"><span data-stu-id="73020-140">**Sort results in tempdb**</span></span>  
 <span data-ttu-id="73020-141">オプションを使用して、 `SORT_IN_TEMPDB` インデックスの作成中に生成された中間の並べ替え結果を一時的に格納する場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="73020-141">Use the `SORT_IN_TEMPDB`option, which determines where the intermediate sort results, generated during index creation, are temporarily stored.</span></span> <span data-ttu-id="73020-142">並べ替え操作が必要ない場合、または並べ替えをメモリ上で実行できる場合、 `SORT_IN_TEMPDB`オプションは無視されます。</span><span class="sxs-lookup"><span data-stu-id="73020-142">If a sort operation is not required, or if the sort can be performed in memory, the `SORT_IN_TEMPDB`option is ignored.</span></span>  
  
 <span data-ttu-id="73020-143">**[インデックスの再作成中にオンラインのインデックスを保持する]**</span><span class="sxs-lookup"><span data-stu-id="73020-143">**Keep index online while reindexing**</span></span>  
 <span data-ttu-id="73020-144">`ONLINE` オプションを使用すると、インデックス操作の実行中に、ユーザーは基になるテーブルまたはクラスター化インデックス データ、および任意の関連付けられた非クラスター化インデックスにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="73020-144">Use the `ONLINE` option which allows users to access the underlying table or clustered index data and any associated nonclustered indexes during index operations.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="73020-145">オンラインでのインデックス操作は、[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のすべてのエディションで使用できるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="73020-145">Online index operations are not available in every edition of [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="73020-146">の各エディションでサポートされる機能の一覧につい [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ては、「 [SQL Server 2014 の各エディションがサポートする機能](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="73020-146">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
 <span data-ttu-id="73020-147">**[T-SQL の表示]**</span><span class="sxs-lookup"><span data-stu-id="73020-147">**View T-SQL**</span></span>  
 <span data-ttu-id="73020-148">選択したオプションに基づき、このタスクでサーバーに対して実行される [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを表示します。</span><span class="sxs-lookup"><span data-stu-id="73020-148">View the [!INCLUDE[tsql](../../includes/tsql-md.md)] statements performed against the server for this task, based on the selected options.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="73020-149">影響を受けるオブジェクトが大量にある場合は、表示にかなりの時間を要する場合があります。</span><span class="sxs-lookup"><span data-stu-id="73020-149">When the number of objects affected is large, this display can take a considerable amount of time.</span></span>  
  
## <a name="new-connection-dialog-box"></a><span data-ttu-id="73020-150">[新しい接続] ダイアログ ボックス</span><span class="sxs-lookup"><span data-stu-id="73020-150">New Connection Dialog Box</span></span>  
 <span data-ttu-id="73020-151">**接続名**</span><span class="sxs-lookup"><span data-stu-id="73020-151">**Connection name**</span></span>  
 <span data-ttu-id="73020-152">新しい接続の名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="73020-152">Enter a name for the new connection.</span></span>  
  
 <span data-ttu-id="73020-153">**[サーバー名の選択または入力]**</span><span class="sxs-lookup"><span data-stu-id="73020-153">**Select or enter a server name**</span></span>  
 <span data-ttu-id="73020-154">このタスクを実行するときに接続するサーバーを選択します。</span><span class="sxs-lookup"><span data-stu-id="73020-154">Select a server to connect to when performing this task.</span></span>  
  
 <span data-ttu-id="73020-155">**[更新]**</span><span class="sxs-lookup"><span data-stu-id="73020-155">**Refresh**</span></span>  
 <span data-ttu-id="73020-156">使用できるサーバーの一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="73020-156">Refresh the list of available servers.</span></span>  
  
 <span data-ttu-id="73020-157">**[サーバーにログオンするための情報の入力]**</span><span class="sxs-lookup"><span data-stu-id="73020-157">**Enter information to log on to the server**</span></span>  
 <span data-ttu-id="73020-158">サーバーの認証情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="73020-158">Specify how to authenticate against the server.</span></span>  
  
 <span data-ttu-id="73020-159">**[Windows NT の統合セキュリティを使用する]**</span><span class="sxs-lookup"><span data-stu-id="73020-159">**Use Windows integrated security**</span></span>  
 <span data-ttu-id="73020-160">Windows 認証を使用して [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="73020-160">Connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] with Windows Authentication.</span></span>  
  
 <span data-ttu-id="73020-161">**[特定のユーザー名とパスワードを使用する]**</span><span class="sxs-lookup"><span data-stu-id="73020-161">**Use a specific user name and password**</span></span>  
 <span data-ttu-id="73020-162">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 認証を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="73020-162">Connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="73020-163">このオプションは利用できません。</span><span class="sxs-lookup"><span data-stu-id="73020-163">This option is not available.</span></span>  
  
 <span data-ttu-id="73020-164">**ユーザー名**</span><span class="sxs-lookup"><span data-stu-id="73020-164">**User name**</span></span>  
 <span data-ttu-id="73020-165">認証に使用する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインを指定します。</span><span class="sxs-lookup"><span data-stu-id="73020-165">Provide a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login to use when authenticating.</span></span> <span data-ttu-id="73020-166">このオプションは利用できません。</span><span class="sxs-lookup"><span data-stu-id="73020-166">This option is not available.</span></span>  
  
 <span data-ttu-id="73020-167">**パスワード**</span><span class="sxs-lookup"><span data-stu-id="73020-167">**Password**</span></span>  
 <span data-ttu-id="73020-168">認証に使用するパスワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="73020-168">Provide a password to use when authenticating.</span></span> <span data-ttu-id="73020-169">このオプションは利用できません。</span><span class="sxs-lookup"><span data-stu-id="73020-169">This option is not available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73020-170">参照</span><span class="sxs-lookup"><span data-stu-id="73020-170">See Also</span></span>  
 <span data-ttu-id="73020-171">[ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="73020-171">[ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql) </span></span>  
 <span data-ttu-id="73020-172">[DBCC DBREINDEX &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-dbreindex-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="73020-172">[DBCC DBREINDEX &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-dbreindex-transact-sql) </span></span>  
 <span data-ttu-id="73020-173">[CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="73020-173">[CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql) </span></span>  
 <span data-ttu-id="73020-174">[インデックスの SORT_IN_TEMPDB オプション](../indexes/indexes.md) </span><span class="sxs-lookup"><span data-stu-id="73020-174">[SORT_IN_TEMPDB Option For Indexes](../indexes/indexes.md) </span></span>  
 <span data-ttu-id="73020-175">[オンライン インデックス操作のガイドライン](../indexes/guidelines-for-online-index-operations.md) </span><span class="sxs-lookup"><span data-stu-id="73020-175">[Guidelines for Online Index Operations](../indexes/guidelines-for-online-index-operations.md) </span></span>  
 <span data-ttu-id="73020-176">[オンライン インデックス操作の動作原理](../indexes/how-online-index-operations-work.md) </span><span class="sxs-lookup"><span data-stu-id="73020-176">[How Online Index Operations Work](../indexes/how-online-index-operations-work.md) </span></span>  
 [<span data-ttu-id="73020-177">オンラインでのインデックス操作の実行</span><span class="sxs-lookup"><span data-stu-id="73020-177">Perform Index Operations Online</span></span>](../indexes/perform-index-operations-online.md)  
  
  
