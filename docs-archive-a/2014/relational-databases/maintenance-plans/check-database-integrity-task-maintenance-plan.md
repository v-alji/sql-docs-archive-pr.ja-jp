---
title: データベースの整合性確認タスク (メンテナンス プラン) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.maint.maintplanproperties.integrity.f1
- sql12.swb.maint.integrity.f1
helpviewer_keywords:
- Check Database Integrity Task dialog box
ms.assetid: 3534494a-5dfe-4738-b49a-e7fabd731c47
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f786755a3b7ed5d991b4cf0e32c067e355c111ae
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643324"
---
# <a name="check-database-integrity-task-maintenance-plan"></a><span data-ttu-id="7850d-102">データベースの整合性確認タスク (メンテナンス プラン)</span><span class="sxs-lookup"><span data-stu-id="7850d-102">Check Database Integrity Task (Maintenance Plan)</span></span>
  <span data-ttu-id="7850d-103">**[データベースの整合性確認タスク]** ダイアログを使用すると、 `DBCC CHECKDB`[!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを実行することにより、ユーザーおよびシステム テーブルの割り当ておよび構造の整合性、データベース内のインデックスを確認できます。</span><span class="sxs-lookup"><span data-stu-id="7850d-103">Use the **Check Database Integrity Task** dialog to check the allocation and structural integrity of user and system tables, and indexes in the database, by running the `DBCC CHECKDB`[!INCLUDE[tsql](../../includes/tsql-md.md)] statement.</span></span> <span data-ttu-id="7850d-104">`DBCC` を実行することにより、データベース整合性に問題があった場合にレポートし、システム管理者またはデータベースの所有者によって対処できます。</span><span class="sxs-lookup"><span data-stu-id="7850d-104">Running `DBCC` ensures that any integrity problems with the database are reported, thereby allowing them to be addressed later by a system administrator or database owner.</span></span>  
  
## <a name="options"></a><span data-ttu-id="7850d-105">Options</span><span class="sxs-lookup"><span data-stu-id="7850d-105">Options</span></span>  
 <span data-ttu-id="7850d-106">**接続**</span><span class="sxs-lookup"><span data-stu-id="7850d-106">**Connection**</span></span>  
 <span data-ttu-id="7850d-107">このタスクを実行するときに使用するサーバー接続を選択します。</span><span class="sxs-lookup"><span data-stu-id="7850d-107">Select the server connection to use when performing this task.</span></span>  
  
 <span data-ttu-id="7850d-108">**[新規作成]**</span><span class="sxs-lookup"><span data-stu-id="7850d-108">**New**</span></span>  
 <span data-ttu-id="7850d-109">このタスクを実行するときに使用する新しいサーバー接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="7850d-109">Create a new server connection to use when performing this task.</span></span> <span data-ttu-id="7850d-110">**[新しい接続]** ダイアログ ボックスについては、後で説明します。</span><span class="sxs-lookup"><span data-stu-id="7850d-110">The **New Connection** dialog box is described below.</span></span>  
  
 <span data-ttu-id="7850d-111">**データベース**</span><span class="sxs-lookup"><span data-stu-id="7850d-111">**Databases**</span></span>  
 <span data-ttu-id="7850d-112">このタスクで操作するデータベースを指定します。</span><span class="sxs-lookup"><span data-stu-id="7850d-112">Specify the databases affected by this task.</span></span>  
  
-   <span data-ttu-id="7850d-113">**[すべてのデータベース]**</span><span class="sxs-lookup"><span data-stu-id="7850d-113">**All databases**</span></span>  
  
     <span data-ttu-id="7850d-114">すべての [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベース (**tempdb** を除く) を対象として、メンテナンス タスクを実行するメンテナンス プランを生成します。</span><span class="sxs-lookup"><span data-stu-id="7850d-114">Generate a maintenance plan that runs maintenance tasks against all [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases except **tempdb**.</span></span>  
  
-   <span data-ttu-id="7850d-115">**[すべてのシステム データベース]**</span><span class="sxs-lookup"><span data-stu-id="7850d-115">**All system databases**</span></span>  
  
     <span data-ttu-id="7850d-116">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のシステム データベース ( **tempdb**を除く) を対象として、メンテナンス タスクを実行するメンテナンス プランを生成します。</span><span class="sxs-lookup"><span data-stu-id="7850d-116">Generate a maintenance plan that runs maintenance tasks against each of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system databases except **tempdb**.</span></span> <span data-ttu-id="7850d-117">ユーザーが作成したデータベースではメンテナンス タスクは実行されません。</span><span class="sxs-lookup"><span data-stu-id="7850d-117">No maintenance tasks are run against user-created databases.</span></span>  
  
-   <span data-ttu-id="7850d-118">**[すべてのユーザー データベース]**</span><span class="sxs-lookup"><span data-stu-id="7850d-118">**All user databases**</span></span>  
  
     <span data-ttu-id="7850d-119">ユーザーが作成したすべてのデータベースを対象として、メンテナンス タスクを実行するメンテナンス プランを生成します。</span><span class="sxs-lookup"><span data-stu-id="7850d-119">Generate a maintenance plan that runs maintenance tasks against all user-created databases.</span></span> <span data-ttu-id="7850d-120">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のシステム データベースではメンテナンス タスクは実行されません。</span><span class="sxs-lookup"><span data-stu-id="7850d-120">No maintenance tasks are run against the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system databases.</span></span>  
  
-   <span data-ttu-id="7850d-121">**[これらのデータベース]**</span><span class="sxs-lookup"><span data-stu-id="7850d-121">**These specific databases**</span></span>  
  
     <span data-ttu-id="7850d-122">選択されたデータベースだけを対象として、メンテナンス タスクを実行するメンテナンス プランを生成します。</span><span class="sxs-lookup"><span data-stu-id="7850d-122">Generate a maintenance plan that runs maintenance tasks against only those databases that are selected.</span></span> <span data-ttu-id="7850d-123">このオプションをオンにする場合は、少なくとも 1 つのデータベースが一覧内で選択されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="7850d-123">At least one database in the list must be selected if this option is chosen.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="7850d-124">メンテナンス プランは、互換性レベルが 80 以上に設定されているデータベースに対してのみ実行されます。</span><span class="sxs-lookup"><span data-stu-id="7850d-124">Maintenance plans only run against databases set to compatibility level 80 or higher.</span></span> <span data-ttu-id="7850d-125">互換性レベルが 70 以下に設定されているデータベースは表示されません。</span><span class="sxs-lookup"><span data-stu-id="7850d-125">Databases set to compatibility level 70 or lower are not displayed.</span></span>  
  
 <span data-ttu-id="7850d-126">**[インデックスを含める]**</span><span class="sxs-lookup"><span data-stu-id="7850d-126">**Include indexes**</span></span>  
 <span data-ttu-id="7850d-127">すべてのインデックス ページおよびテーブル データ ページの整合性を確認します。</span><span class="sxs-lookup"><span data-stu-id="7850d-127">Check the integrity of all the index pages as well as the table data pages.</span></span>  
  
 <span data-ttu-id="7850d-128">**[T-SQL の表示]**</span><span class="sxs-lookup"><span data-stu-id="7850d-128">**View T-SQL**</span></span>  
 <span data-ttu-id="7850d-129">選択したオプションに基づき、このタスクでサーバーに対して実行される [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを表示します。</span><span class="sxs-lookup"><span data-stu-id="7850d-129">View the [!INCLUDE[tsql](../../includes/tsql-md.md)] statements performed against the server for this task, based on the selected options.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7850d-130">影響を受けるオブジェクトが大量にある場合は、表示にかなりの時間を要する場合があります。</span><span class="sxs-lookup"><span data-stu-id="7850d-130">When the number of objects affected is large, this display can take a considerable amount of time.</span></span>  
  
## <a name="new-connection-dialog-box"></a><span data-ttu-id="7850d-131">[新しい接続] ダイアログ ボックス</span><span class="sxs-lookup"><span data-stu-id="7850d-131">New Connection Dialog Box</span></span>  
 <span data-ttu-id="7850d-132">**接続名**</span><span class="sxs-lookup"><span data-stu-id="7850d-132">**Connection name**</span></span>  
 <span data-ttu-id="7850d-133">新しい接続の名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="7850d-133">Enter a name for the new connection.</span></span>  
  
 <span data-ttu-id="7850d-134">**[サーバー名の選択または入力]**</span><span class="sxs-lookup"><span data-stu-id="7850d-134">**Select or enter a server name**</span></span>  
 <span data-ttu-id="7850d-135">このタスクを実行するときに接続するサーバーを選択します。</span><span class="sxs-lookup"><span data-stu-id="7850d-135">Select a server to connect to when performing this task.</span></span>  
  
 <span data-ttu-id="7850d-136">**[更新]**</span><span class="sxs-lookup"><span data-stu-id="7850d-136">**Refresh**</span></span>  
 <span data-ttu-id="7850d-137">使用できるサーバーの一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="7850d-137">Refresh the list of available servers.</span></span>  
  
 <span data-ttu-id="7850d-138">**[サーバーにログオンするための情報の入力]**</span><span class="sxs-lookup"><span data-stu-id="7850d-138">**Enter information to log on to the server**</span></span>  
 <span data-ttu-id="7850d-139">サーバーの認証情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="7850d-139">Specify how to authenticate against the server.</span></span>  
  
 <span data-ttu-id="7850d-140">**[Windows NT の統合セキュリティを使用する]**</span><span class="sxs-lookup"><span data-stu-id="7850d-140">**Use Windows integrated security**</span></span>  
 <span data-ttu-id="7850d-141">Windows 認証を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="7850d-141">Connect to an instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] with Windows Authentication.</span></span>  
  
 <span data-ttu-id="7850d-142">**[特定のユーザー名とパスワードを使用する]**</span><span class="sxs-lookup"><span data-stu-id="7850d-142">**Use a specific user name and password**</span></span>  
 <span data-ttu-id="7850d-143">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="7850d-143">Connect to an instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="7850d-144">このオプションは利用できません。</span><span class="sxs-lookup"><span data-stu-id="7850d-144">This option is not available.</span></span>  
  
 <span data-ttu-id="7850d-145">**ユーザー名**</span><span class="sxs-lookup"><span data-stu-id="7850d-145">**User name**</span></span>  
 <span data-ttu-id="7850d-146">認証に使用する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインを指定します。</span><span class="sxs-lookup"><span data-stu-id="7850d-146">Provide a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login to use when authenticating.</span></span> <span data-ttu-id="7850d-147">このオプションは利用できません。</span><span class="sxs-lookup"><span data-stu-id="7850d-147">This option is not available.</span></span>  
  
 <span data-ttu-id="7850d-148">**パスワード**</span><span class="sxs-lookup"><span data-stu-id="7850d-148">**Password**</span></span>  
 <span data-ttu-id="7850d-149">認証に使用するパスワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="7850d-149">Provide a password to use when authenticating.</span></span> <span data-ttu-id="7850d-150">このオプションは利用できません。</span><span class="sxs-lookup"><span data-stu-id="7850d-150">This option is not available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7850d-151">参照</span><span class="sxs-lookup"><span data-stu-id="7850d-151">See Also</span></span>  
 [<span data-ttu-id="7850d-152">DBCC CHECKDB &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="7850d-152">DBCC CHECKDB &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql)  
  
  
