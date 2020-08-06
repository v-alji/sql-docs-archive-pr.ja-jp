---
title: データベースをシングル ユーザー モードに設定する | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- single-user mode [SQL Server], database option
ms.assetid: fb5254eb-b635-4b39-8361-136fd36f2b1f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 16281b5fa7d4f6698bb6c498915bfa84779b3e14
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712014"
---
# <a name="set-a-database-to-single-user-mode"></a><span data-ttu-id="90024-102">データベースをシングル ユーザー モードに設定する</span><span class="sxs-lookup"><span data-stu-id="90024-102">Set a Database to Single-user Mode</span></span>
  <span data-ttu-id="90024-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して、 [!INCLUDE[tsql](../../includes/tsql-md.md)]のユーザー定義のデータベースをシングル ユーザー モードに設定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="90024-103">This topic describes how to set a user-defined database to single-user mode in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="90024-104">シングル ユーザー モードでは、一度に 1 人のユーザーだけがデータベースにアクセスでき、一般にはメンテナンス操作のために使用されます。</span><span class="sxs-lookup"><span data-stu-id="90024-104">Single-user mode specifies that only one user at a time can access the database and is generally used for maintenance actions.</span></span>  
  
 <span data-ttu-id="90024-105">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="90024-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="90024-106">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="90024-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="90024-107">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="90024-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="90024-108">前提条件</span><span class="sxs-lookup"><span data-stu-id="90024-108">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="90024-109">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="90024-109">Security</span></span>](#Security)  
  
-   <span data-ttu-id="90024-110">**以下を使用してデータベースをシングル ユーザー モードに設定するには:**</span><span class="sxs-lookup"><span data-stu-id="90024-110">**To set a database to single-user mode, using:**</span></span>  
  
     [<span data-ttu-id="90024-111">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="90024-111">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="90024-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="90024-112">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="90024-113">はじめに</span><span class="sxs-lookup"><span data-stu-id="90024-113">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="90024-114">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="90024-114">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="90024-115">データベースをシングル ユーザー モードに設定したときに他のユーザーがデータベースに接続していると、データベースに対する接続は警告なく切断されます。</span><span class="sxs-lookup"><span data-stu-id="90024-115">If other users are connected to the database at the time that you set the database to single-user mode, their connections to the database will be closed without warning.</span></span>  
  
-   <span data-ttu-id="90024-116">このオプションを設定したユーザーがログオフしても、データベースはシングル ユーザー モードのままです。</span><span class="sxs-lookup"><span data-stu-id="90024-116">The database remains in single-user mode even if the user that set the option logs off.</span></span> <span data-ttu-id="90024-117">そのユーザーがログオフした時点で、他のユーザーが 1 人だけデータベースに接続できます。</span><span class="sxs-lookup"><span data-stu-id="90024-117">At that point, a different user, but only one, can connect to the database.</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="90024-118">前提条件</span><span class="sxs-lookup"><span data-stu-id="90024-118">Prerequisites</span></span>  
  
-   <span data-ttu-id="90024-119">データベースを SINGLE_USER に設定する前に、AUTO_UPDATE_STATISTICS_ASYNC オプションが OFF に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="90024-119">Before you set the database to SINGLE_USER, verify that the AUTO_UPDATE_STATISTICS_ASYNC option is set to OFF.</span></span> <span data-ttu-id="90024-120">このオプションが ON に設定されていると、統計の更新に使用されるバックグラウンド スレッドによってデータベースへの接続が使用されるため、シングル ユーザー モードではデータベースにアクセスできなくなります。</span><span class="sxs-lookup"><span data-stu-id="90024-120">When this option is set to ON, the background thread that is used to update statistics takes a connection against the database, and you will be unable to access the database in single-user mode.</span></span> <span data-ttu-id="90024-121">詳細については、「[ALTER DATABASE の SET オプション &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="90024-121">For more information, see [ALTER DATABASE SET Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="90024-122">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="90024-122">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="90024-123">Permissions</span><span class="sxs-lookup"><span data-stu-id="90024-123">Permissions</span></span>  
 <span data-ttu-id="90024-124">データベースに対する ALTER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="90024-124">Requires ALTER permission on the database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="90024-125">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="90024-125">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-set-a-database-to-single-user-mode"></a><span data-ttu-id="90024-126">データベースをシングル ユーザー モードに設定するには</span><span class="sxs-lookup"><span data-stu-id="90024-126">To set a database to single-user mode</span></span>  
  
1.  <span data-ttu-id="90024-127">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]のインスタンスに接続し、そのインスタンスを展開します。</span><span class="sxs-lookup"><span data-stu-id="90024-127">In **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="90024-128">変更するデータベースを右クリックして、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="90024-128">Right-click the database to change, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="90024-129">**[データベースのプロパティ]** ダイアログ ボックスで、 **[オプション]** ページをクリックします。</span><span class="sxs-lookup"><span data-stu-id="90024-129">In the **Database Properties** dialog box, click the **Options** page.</span></span>  
  
4.  <span data-ttu-id="90024-130">**[アクセスの制限]** オプションで、 **[Single]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="90024-130">From the **Restrict Access** option, select **Single**.</span></span>  
  
5.  <span data-ttu-id="90024-131">他のユーザーがデータベースに接続していると、 **"接続を開く"** というメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="90024-131">If other users are connected to the database, an **Open Connections** message will appear.</span></span> <span data-ttu-id="90024-132">プロパティを変更して他のすべての接続を閉じるには、 **[はい]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="90024-132">To change the property and close all other connections, click **Yes**.</span></span>  
  
 <span data-ttu-id="90024-133">この手順を使用して、データベースを複数アクセス モードまたは制限アクセス モードに設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="90024-133">You can also set the database to Multiple or Restricted access by using this procedure.</span></span> <span data-ttu-id="90024-134">[アクセス制限] オプションの詳細については、「[[データベースのプロパティ] &#40;[オプション] ページ&#41;](database-properties-options-page.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="90024-134">For more information about the Restrict Access options, see [Database Properties &#40;Options Page&#41;](database-properties-options-page.md).</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="90024-135">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="90024-135">Using Transact-SQL</span></span>  
  
#### <a name="to-set-a-database-to-single-user-mode"></a><span data-ttu-id="90024-136">データベースをシングル ユーザー モードに設定するには</span><span class="sxs-lookup"><span data-stu-id="90024-136">To set a database to single-user mode</span></span>  
  
1.  <span data-ttu-id="90024-137">[!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="90024-137">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="90024-138">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="90024-138">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="90024-139">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="90024-139">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="90024-140">この例では、排他的アクセスを取得するために、データベースを `SINGLE_USER` モードに設定します。</span><span class="sxs-lookup"><span data-stu-id="90024-140">This example sets the database to `SINGLE_USER` mode to obtain exclusive access.</span></span> <span data-ttu-id="90024-141">次に、 [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] データベースの状態を `READ_ONLY` に設定し、データベースへのアクセス権をすべてのユーザーに戻します。終了オプション `WITH ROLLBACK IMMEDIATE` は、最初の `ALTER DATABASE` ステートメントで指定しています。</span><span class="sxs-lookup"><span data-stu-id="90024-141">The example then sets the state of the [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] database to `READ_ONLY` and returns access to the database to all users.The termination option `WITH ROLLBACK IMMEDIATE` is specified in the first `ALTER DATABASE` statement.</span></span> <span data-ttu-id="90024-142">これですべての未完了のトランザクションがロールバックされ、 [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] データベースへの他のすべての接続は直ちに解除されます。</span><span class="sxs-lookup"><span data-stu-id="90024-142">This will cause all incomplete transactions to be rolled back and any other connections to the [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] database to be immediately disconnected.</span></span>  
  
 [!code-sql[DatabaseDDL#AlterDatabase8](../../snippets/tsql/SQL14/tsql/databaseddl/transact-sql/alterdatabase.sql#alterdatabase8)]  
  
## <a name="see-also"></a><span data-ttu-id="90024-143">参照</span><span class="sxs-lookup"><span data-stu-id="90024-143">See Also</span></span>  
 [<span data-ttu-id="90024-144">ALTER DATABASE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="90024-144">ALTER DATABASE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-database-transact-sql)  
  
  
