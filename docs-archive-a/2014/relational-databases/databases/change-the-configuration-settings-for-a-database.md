---
title: データベースの構成設定の変更 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- database configuration [SQL Server]
- configuration options [SQL Server], databases
- modifying database configuration settings
ms.assetid: c29c3385-5043-400f-bb4e-044a4c9a9a4b
author: stevestein
ms.author: sstein
ms.openlocfilehash: f9edecefae5154bb66a65e38724d9e77a94fdbb4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742230"
---
# <a name="change-the-configuration-settings-for-a-database"></a><span data-ttu-id="cb9c4-102">データベースの構成設定の変更</span><span class="sxs-lookup"><span data-stu-id="cb9c4-102">Change the Configuration Settings for a Database</span></span>
  <span data-ttu-id="cb9c4-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して、 [!INCLUDE[tsql](../../includes/tsql-md.md)]のデータベース レベルのオプションを変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="cb9c4-103">This topic describes how to change database-level options in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="cb9c4-104">データベース オプションは各データベースに一意であり、他のデータベースには影響しません。</span><span class="sxs-lookup"><span data-stu-id="cb9c4-104">These options are unique to each database and do not affect other databases.</span></span>  
  
 <span data-ttu-id="cb9c4-105">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="cb9c4-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="cb9c4-106">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="cb9c4-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="cb9c4-107">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="cb9c4-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="cb9c4-108">Security</span><span class="sxs-lookup"><span data-stu-id="cb9c4-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="cb9c4-109">**以下を使用してデータベースのオプション設定を変更するには:**</span><span class="sxs-lookup"><span data-stu-id="cb9c4-109">**To change the option settings for a database, using:**</span></span>  
  
     [<span data-ttu-id="cb9c4-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="cb9c4-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="cb9c4-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="cb9c4-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="cb9c4-112">はじめに</span><span class="sxs-lookup"><span data-stu-id="cb9c4-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="cb9c4-113">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="cb9c4-113">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="cb9c4-114">これらのオプションを変更できるのは、システム管理者、データベース所有者、または **sysadmin** 固定サーバー ロールおよび **dbcreator** 固定サーバー ロールと **db_owner** 固定データベース ロールのメンバーだけです。</span><span class="sxs-lookup"><span data-stu-id="cb9c4-114">Only the system administrator, database owner, members of the **sysadmin** and **dbcreator** fixed server roles and **db_owner** fixed database roles can modify these options.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="cb9c4-115">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="cb9c4-115">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="cb9c4-116">Permissions</span><span class="sxs-lookup"><span data-stu-id="cb9c4-116">Permissions</span></span>  
 <span data-ttu-id="cb9c4-117">データベースに対する ALTER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="cb9c4-117">Requires ALTER permission on the database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="cb9c4-118">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="cb9c4-118">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-change-the-option-settings-for-a-database"></a><span data-ttu-id="cb9c4-119">データベースのオプション設定を変更するには</span><span class="sxs-lookup"><span data-stu-id="cb9c4-119">To change the option settings for a database</span></span>  
  
1.  <span data-ttu-id="cb9c4-120">オブジェクト エクスプローラーで、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンスに接続し、サーバーを展開して **[データベース]** を展開します。データベースを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cb9c4-120">In Object Explorer, connect to a [!INCLUDE[ssDE](../../includes/ssde-md.md)] instance, expand the server, expand **Databases**, right-click a database, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="cb9c4-121">**[データベースのプロパティ]** ダイアログ ボックスで、 **[オプション]** をクリックします。ほとんどの構成設定にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="cb9c4-121">In the **Database Properties** dialog box, click **Options** to access most of the configuration settings.</span></span> <span data-ttu-id="cb9c4-122">ファイルとファイル グループの構成、ミラーリングとログ配布の設定については、それぞれ専用のページにあります。</span><span class="sxs-lookup"><span data-stu-id="cb9c4-122">File and filegroup configurations, mirroring and log shipping are on their respective pages.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="cb9c4-123">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="cb9c4-123">Using Transact-SQL</span></span>  
  
#### <a name="to-change-the-option-settings-for-a-database"></a><span data-ttu-id="cb9c4-124">データベースのオプション設定を変更するには</span><span class="sxs-lookup"><span data-stu-id="cb9c4-124">To change the option settings for a database</span></span>  
  
1.  <span data-ttu-id="cb9c4-125">[!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="cb9c4-125">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="cb9c4-126">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cb9c4-126">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="cb9c4-127">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cb9c4-127">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="cb9c4-128">この例では、 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] サンプル データベースに対して、復旧モデルおよびデータ ページ検証のオプションを設定します。</span><span class="sxs-lookup"><span data-stu-id="cb9c4-128">This example sets the recovery model and data page verification options for the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample database.</span></span>  
  
 [!code-sql[DatabaseDDL#AlterDatabase7](../../snippets/tsql/SQL14/tsql/databaseddl/transact-sql/alterdatabase.sql#alterdatabase7)]  
  
 <span data-ttu-id="cb9c4-129">詳細については、「[ALTER DATABASE SET Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cb9c4-129">For more examples, see [ALTER DATABASE SET Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb9c4-130">参照</span><span class="sxs-lookup"><span data-stu-id="cb9c4-130">See Also</span></span>  
 <span data-ttu-id="cb9c4-131">[ALTER DATABASE 互換性レベル &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level) </span><span class="sxs-lookup"><span data-stu-id="cb9c4-131">[ALTER DATABASE Compatibility Level &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level) </span></span>  
 <span data-ttu-id="cb9c4-132">[ALTER DATABASE データベース ミラーリング &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring) </span><span class="sxs-lookup"><span data-stu-id="cb9c4-132">[ALTER DATABASE Database Mirroring &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring) </span></span>  
 <span data-ttu-id="cb9c4-133">[ALTER DATABASE SET HADR &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-hadr) </span><span class="sxs-lookup"><span data-stu-id="cb9c4-133">[ALTER DATABASE SET HADR &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-hadr) </span></span>  
 <span data-ttu-id="cb9c4-134">[データベースの名前変更](rename-a-database.md) </span><span class="sxs-lookup"><span data-stu-id="cb9c4-134">[Rename a Database](rename-a-database.md) </span></span>  
 [<span data-ttu-id="cb9c4-135">データベースの圧縮</span><span class="sxs-lookup"><span data-stu-id="cb9c4-135">Shrink a Database</span></span>](shrink-a-database.md)  
  
  
