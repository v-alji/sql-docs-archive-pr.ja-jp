---
title: ユーティリティ コントロール ポイントの削除 (SQL Server ユーティリティ) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: c048a416-900e-4c77-8243-e0f0d8b94068
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: fe4ebb9de3f7644b4cff5c7dbfb34e50be7e8993
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645594"
---
# <a name="remove-a-utility-control-point-sql-server-utility"></a><span data-ttu-id="7ec8d-102">ユーティリティ コントロール ポイントの削除 (SQL Server ユーティリティ)</span><span class="sxs-lookup"><span data-stu-id="7ec8d-102">Remove a Utility Control Point (SQL Server Utility)</span></span>
  <span data-ttu-id="7ec8d-103">このトピックでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を使用して、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] のインスタンスから [!INCLUDE[tsql](../../includes/tsql-md.md)]ユーティリティ コントロール ポイント (UCP) を削除する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7ec8d-103">This topic describes how to remove a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utility control point (UCP) from the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="7ec8d-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="7ec8d-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="7ec8d-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="7ec8d-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="7ec8d-106">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="7ec8d-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="7ec8d-107">Security</span><span class="sxs-lookup"><span data-stu-id="7ec8d-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="7ec8d-108">**ユーティリティ コントロール ポイントを削除する方法:**</span><span class="sxs-lookup"><span data-stu-id="7ec8d-108">**To remove a Utility Control Point, using:**</span></span>  
  
     [<span data-ttu-id="7ec8d-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="7ec8d-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="7ec8d-110">はじめに</span><span class="sxs-lookup"><span data-stu-id="7ec8d-110">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="7ec8d-111">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="7ec8d-111">Limitations and Restrictions</span></span>  
 <span data-ttu-id="7ec8d-112">この手順を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーティリティから UCP を削除する前に、次の要件を確認してください。</span><span class="sxs-lookup"><span data-stu-id="7ec8d-112">Before you use this procedure to remove the UCP from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility, note the following requirements.</span></span> <span data-ttu-id="7ec8d-113">ストアド プロシージャでは、操作の一部として前提条件がチェックされます。</span><span class="sxs-lookup"><span data-stu-id="7ec8d-113">The stored procedure will run prerequisite checks as part of the operation.</span></span>  
  
-   <span data-ttu-id="7ec8d-114">この手順を実行する前に、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のマネージド インスタンスをすべて UCP から削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7ec8d-114">Before you run this procedure, all managed instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] must be removed from the UCP.</span></span> <span data-ttu-id="7ec8d-115">UCP は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のマネージド インスタンスの 1 つです。</span><span class="sxs-lookup"><span data-stu-id="7ec8d-115">Note that the UCP is a managed instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="7ec8d-116">詳細については、「 [SQL Server ユーティリティからの SQL Server のインスタンスの削除](remove-an-instance-of-sql-server-from-the-sql-server-utility.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7ec8d-116">From more information, see [Remove an Instance of SQL Server from the SQL Server Utility](remove-an-instance-of-sql-server-from-the-sql-server-utility.md).</span></span>  
  
-   <span data-ttu-id="7ec8d-117">このプロシージャは、UCP として構成されたコンピューターで実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7ec8d-117">This procedure must be run on a computer that is a UCP.</span></span>  
  
-   <span data-ttu-id="7ec8d-118">UCP を削除した [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスにユーティリティ以外のデータ コレクション セットがある場合、このプロシージャでは UMDW データベース (sysutility_mdw) が削除されません。</span><span class="sxs-lookup"><span data-stu-id="7ec8d-118">If the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] where the UCP was removed has a non-Utility data collection set, the UMDW database (sysutility_mdw) will not be dropped by the procedure.</span></span> <span data-ttu-id="7ec8d-119">この場合、再度 UCP を作成するには、あらかじめ手動で UMDW データベース (sysutility_mdw) を削除しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="7ec8d-119">If this is the case, the UMDW database (sysutility_mdw) must be dropped manually before the UCP can be created again.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="7ec8d-120">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="7ec8d-120">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="7ec8d-121">Permissions</span><span class="sxs-lookup"><span data-stu-id="7ec8d-121">Permissions</span></span>  
 <span data-ttu-id="7ec8d-122">このプロシージャは、`sysadmin` 権限を持つユーザーが実行する必要があります。この権限は、UCP の作成に必要な権限と同じです。</span><span class="sxs-lookup"><span data-stu-id="7ec8d-122">This procedure must be run by a user with `sysadmin` permissions; the same permissions required to create a UCP.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="7ec8d-123">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="7ec8d-123">Using Transact-SQL</span></span>  
  
#### <a name="to-remove-a-utility-control-point"></a><span data-ttu-id="7ec8d-124">ユーティリティ コントロール ポイントを削除するには</span><span class="sxs-lookup"><span data-stu-id="7ec8d-124">To remove a Utility Control Point</span></span>  
  
1.  <span data-ttu-id="7ec8d-125">[!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="7ec8d-125">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="7ec8d-126">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7ec8d-126">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="7ec8d-127">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7ec8d-127">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
```  
EXEC msdb.dbo.sp_sysutility_ucp_remove;  
```  
  
## <a name="see-also"></a><span data-ttu-id="7ec8d-128">参照</span><span class="sxs-lookup"><span data-stu-id="7ec8d-128">See Also</span></span>  
 <span data-ttu-id="7ec8d-129">[SQL Server ユーティリティの機能とタスク](sql-server-utility-features-and-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="7ec8d-129">[SQL Server Utility Features and Tasks](sql-server-utility-features-and-tasks.md) </span></span>  
 <span data-ttu-id="7ec8d-130">[ユーティリティ エクスプローラーを使用した SQL Server ユーティリティの管理](use-utility-explorer-to-manage-the-sql-server-utility.md) </span><span class="sxs-lookup"><span data-stu-id="7ec8d-130">[Use Utility Explorer to Manage the SQL Server Utility](use-utility-explorer-to-manage-the-sql-server-utility.md) </span></span>  
 [<span data-ttu-id="7ec8d-131">SQL Server ユーティリティのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="7ec8d-131">Troubleshoot the SQL Server Utility</span></span>](../../database-engine/troubleshoot-the-sql-server-utility.md)  
  
  
