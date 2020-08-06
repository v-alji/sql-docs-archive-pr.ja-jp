---
title: リモート サーバー接続オプションの表示または構成 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- remote servers [SQL Server], connection options
- servers [SQL Server], remote
- connections [SQL Server], remote servers
ms.assetid: 356d3e6b-8514-4bd2-a683-9de147949b2b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 73fe5e484d62cde025d1a560937e8cbcf5ec361d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713466"
---
# <a name="view-or-configure-remote-server-connection-options-sql-server"></a><span data-ttu-id="12e82-102">リモート サーバー接続オプションの表示または構成 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="12e82-102">View or Configure Remote Server Connection Options (SQL Server)</span></span>
  <span data-ttu-id="12e82-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して、 [!INCLUDE[tsql](../../includes/tsql-md.md)]でサーバー レベルのリモート サーバー接続オプションを表示または構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="12e82-103">This topic describes how to view or configure remote server connection options at the server level in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="12e82-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="12e82-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="12e82-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="12e82-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="12e82-106">Security</span><span class="sxs-lookup"><span data-stu-id="12e82-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="12e82-107">**リモート サーバー接続オプションを構成する方法:**</span><span class="sxs-lookup"><span data-stu-id="12e82-107">**To view or configure remote server connection options, using:**</span></span>  
  
     [<span data-ttu-id="12e82-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="12e82-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="12e82-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="12e82-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="12e82-110">**補足情報:** [リモート サーバー接続オプションを構成した後](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="12e82-110">**Follow Up:**  [After you configure remote server connection options](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="12e82-111">はじめに</span><span class="sxs-lookup"><span data-stu-id="12e82-111">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="12e82-112">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="12e82-112">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="12e82-113">Permissions</span><span class="sxs-lookup"><span data-stu-id="12e82-113">Permissions</span></span>  
 <span data-ttu-id="12e82-114">**sp_serveroption** を実行するには、サーバーに対する ALTER ANY LINKED SERVER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="12e82-114">Executing **sp_serveroption** requires ALTER ANY LINKED SERVER permission on the server.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="12e82-115">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="12e82-115">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-or-configure-remote-server-connection-options"></a><span data-ttu-id="12e82-116">リモート サーバー接続オプションを表示または構成するには</span><span class="sxs-lookup"><span data-stu-id="12e82-116">To view or configure remote server connection options</span></span>  
  
1.  <span data-ttu-id="12e82-117">オブジェクト エクスプローラーでサーバーを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="12e82-117">In Object Explorer, right-click a server, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="12e82-118">**[SQL Server Properties - \<***server_name***>]** ダイアログ ボックスで、 **[接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="12e82-118">In the **SQL Server Properties - \<***server_name***>** dialog box, click **Connections**.</span></span>  
  
3.  <span data-ttu-id="12e82-119">**[接続]** ページで、 **[リモート サーバー接続]** の設定を確認し、必要に応じて変更します。</span><span class="sxs-lookup"><span data-stu-id="12e82-119">On the **Connections** page, review the **Remote server connections** settings, and modify them if necessary.</span></span>  
  
4.  <span data-ttu-id="12e82-120">リモート サーバー ペアのもう一方のサーバーに対して、手順 1. ～ 3. を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="12e82-120">Repeat steps 1 through 3 on the other server of the remote server pair.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="12e82-121">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="12e82-121">Using Transact-SQL</span></span>  
  
#### <a name="to-view-remote-server-connection-options"></a><span data-ttu-id="12e82-122">リモート サーバー接続オプションを表示するには</span><span class="sxs-lookup"><span data-stu-id="12e82-122">To view remote server connection options</span></span>  
  
1.  <span data-ttu-id="12e82-123">[!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="12e82-123">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="12e82-124">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="12e82-124">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="12e82-125">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="12e82-125">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="12e82-126">この例では、 [sp_helpserver](/sql/relational-databases/system-stored-procedures/sp-helpserver-transact-sql) を使用して、すべてのリモート サーバーに関する情報を返します。</span><span class="sxs-lookup"><span data-stu-id="12e82-126">This example uses [sp_helpserver](/sql/relational-databases/system-stored-procedures/sp-helpserver-transact-sql) to return information about all remote servers.</span></span>  
  
```sql  
USE master;  
GO  
EXEC sp_helpserver ;  
```  
  
#### <a name="to-configure-remote-server-connection-options"></a><span data-ttu-id="12e82-127">リモート サーバー接続オプションを構成するには</span><span class="sxs-lookup"><span data-stu-id="12e82-127">To configure remote server connection options</span></span>  
  
1.  <span data-ttu-id="12e82-128">[!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="12e82-128">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="12e82-129">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="12e82-129">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="12e82-130">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="12e82-130">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="12e82-131">この例では、 [sp_serveroption](/sql/relational-databases/system-stored-procedures/sp-serveroption-transact-sql) を使用して、リモート サーバーを構成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="12e82-131">This example shows how to use [sp_serveroption](/sql/relational-databases/system-stored-procedures/sp-serveroption-transact-sql) to configure a remote server.</span></span> <span data-ttu-id="12e82-132">この例では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の別のインスタンスに対応するリモート サーバー `SEATTLE3`を、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のローカル インスタンスと互換性のある照合順序になるように構成します。</span><span class="sxs-lookup"><span data-stu-id="12e82-132">The example configures a remote server corresponding to another instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], `SEATTLE3`, to be collation compatible with the local instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
```sql  
USE master;  
EXEC sp_serveroption 'SEATTLE3', 'collation compatible', 'true';  
```  
  
##  <a name="follow-up-after-you-configure-remote-server-connection-options"></a><a name="FollowUp"></a><span data-ttu-id="12e82-133">補足情報: リモート サーバー接続オプションを構成した後</span><span class="sxs-lookup"><span data-stu-id="12e82-133">Follow Up: After you configure remote server connection options</span></span>  
 <span data-ttu-id="12e82-134">設定を有効にするには、リモート サーバーを停止し、再起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="12e82-134">The remote server must be stopped and restarted before the setting can take effect.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12e82-135">参照</span><span class="sxs-lookup"><span data-stu-id="12e82-135">See Also</span></span>  
 <span data-ttu-id="12e82-136">[サーバー構成オプション &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="12e82-136">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="12e82-137">[リモート サーバー](remote-servers.md) </span><span class="sxs-lookup"><span data-stu-id="12e82-137">[Remote Servers](remote-servers.md) </span></span>  
 <span data-ttu-id="12e82-138">[リンク サーバー &#40;データベース エンジン&#41;](../../relational-databases/linked-servers/linked-servers-database-engine.md) </span><span class="sxs-lookup"><span data-stu-id="12e82-138">[Linked Servers &#40;Database Engine&#41;](../../relational-databases/linked-servers/linked-servers-database-engine.md) </span></span>  
 <span data-ttu-id="12e82-139">[sp_linkedservers &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-linkedservers-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="12e82-139">[sp_linkedservers &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-linkedservers-transact-sql) </span></span>  
 <span data-ttu-id="12e82-140">[sp_helpserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpserver-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="12e82-140">[sp_helpserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpserver-transact-sql) </span></span>  
 [<span data-ttu-id="12e82-141">sp_serveroption &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="12e82-141">sp_serveroption &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-serveroption-transact-sql)  
  
  
