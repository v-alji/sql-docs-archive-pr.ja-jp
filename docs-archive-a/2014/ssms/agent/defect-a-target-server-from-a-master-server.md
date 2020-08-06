---
title: マスター サーバーからのターゲット サーバーの参加の解除 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, target servers
- target servers [SQL Server], defecting
- SQL Server Agent jobs, master servers
- master servers [SQL Server], defecting target servers
- defecting target servers
ms.assetid: a6da262b-7b38-4ce4-bfd6-6a557c6e8a84
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2b17703fa87f5c0d3e7146a1660ac1ca7c7c1d81
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715046"
---
# <a name="defect-a-target-server-from-a-master-server"></a><span data-ttu-id="723dc-102">マスター サーバーからのターゲット サーバーの参加の解除</span><span class="sxs-lookup"><span data-stu-id="723dc-102">Defect a Target Server from a Master Server</span></span>
  <span data-ttu-id="723dc-103">このトピックでは、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、[!INCLUDE[tsql](../../includes/tsql-md.md)]、または SQL Server 管理オブジェクト (SMO) を使用して、マスター サーバーからターゲット サーバーの参加を解除する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="723dc-103">This topic describes how to defect a target server from a master server in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or SQL Server Management Objects (SMO).</span></span> <span data-ttu-id="723dc-104">この手順はターゲット サーバーから実行します。</span><span class="sxs-lookup"><span data-stu-id="723dc-104">Run this procedure from the target server.</span></span>  
  
 <span data-ttu-id="723dc-105">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="723dc-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="723dc-106">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="723dc-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="723dc-107">Security</span><span class="sxs-lookup"><span data-stu-id="723dc-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="723dc-108">**マスター サーバーからターゲット サーバーの参加を解除するために使用するもの:**</span><span class="sxs-lookup"><span data-stu-id="723dc-108">**To defect a target server, using:**</span></span>  
  
     [<span data-ttu-id="723dc-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="723dc-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="723dc-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="723dc-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="723dc-111">SMO</span><span class="sxs-lookup"><span data-stu-id="723dc-111">SMO</span></span>](#PowerShellProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="723dc-112">はじめに</span><span class="sxs-lookup"><span data-stu-id="723dc-112">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="723dc-113">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="723dc-113">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="723dc-114">Permissions</span><span class="sxs-lookup"><span data-stu-id="723dc-114">Permissions</span></span>  
 <span data-ttu-id="723dc-115">このストアド プロシージャを実行するには、`sysadmin` 固定サーバー ロールのメンバーであることが必要です。</span><span class="sxs-lookup"><span data-stu-id="723dc-115">To execute this stored procedure, a user must be a member of the `sysadmin` fixed server role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="723dc-116">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="723dc-116">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-defect-a-target-server-from-a-master-server"></a><span data-ttu-id="723dc-117">マスター サーバーからターゲット サーバーの参加を解除するには</span><span class="sxs-lookup"><span data-stu-id="723dc-117">To defect a target server from a master server</span></span>  
  
1.  <span data-ttu-id="723dc-118">**オブジェクト エクスプローラー**で、ターゲット サーバーとして構成するサーバーを展開します。</span><span class="sxs-lookup"><span data-stu-id="723dc-118">In **Object Explorer**, expand a server that is configured as a target server.</span></span>  
  
2.  <span data-ttu-id="723dc-119">**[SQL Server エージェント]** を右クリックし、 **[マルチ サーバーの管理]** をポイントして、 **[参加解除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="723dc-119">Right-click **SQL Server Agent**, point to **Multi Server Administration**, and then click **Defect**.</span></span>  
  
3.  <span data-ttu-id="723dc-120">**[はい]** をクリックして、マスター サーバーからこのターゲット サーバーの参加を解除することを確認します。</span><span class="sxs-lookup"><span data-stu-id="723dc-120">Click **Yes** to confirm that you want to defect this target server from a master server.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="723dc-121">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="723dc-121">Using Transact-SQL</span></span>  
  
#### <a name="to-defect-a-target-server-from-a-master-server"></a><span data-ttu-id="723dc-122">マスター サーバーからターゲット サーバーの参加を解除するには</span><span class="sxs-lookup"><span data-stu-id="723dc-122">To defect a target server from a master server</span></span>  
  
1.  <span data-ttu-id="723dc-123">[!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="723dc-123">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="723dc-124">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="723dc-124">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="723dc-125">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="723dc-125">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
```sql
sp_msx_defect ;  
```  
  
 <span data-ttu-id="723dc-126">詳細については、「 [sp_msx_defect &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-msx-defect-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="723dc-126">For more information, see [sp_msx_defect &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-msx-defect-transact-sql).</span></span>  
  
##  <a name="using-sql-server-management-objects-smo"></a><a name="PowerShellProcedure"></a><span data-ttu-id="723dc-127">SQL Server 管理オブジェクト (SMO) の使用</span><span class="sxs-lookup"><span data-stu-id="723dc-127">Using SQL Server Management Objects (SMO)</span></span>  
 <span data-ttu-id="723dc-128">`MsxDefect Method` を使用します。</span><span class="sxs-lookup"><span data-stu-id="723dc-128">Use the `MsxDefect Method`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="723dc-129">参照</span><span class="sxs-lookup"><span data-stu-id="723dc-129">See Also</span></span>  
 <span data-ttu-id="723dc-130">[マルチサーバー環境の作成](create-a-multiserver-environment.md) </span><span class="sxs-lookup"><span data-stu-id="723dc-130">[Create a Multiserver Environment](create-a-multiserver-environment.md) </span></span>  
 <span data-ttu-id="723dc-131">[エンタープライズ全体の管理の自動化](automated-administration-across-an-enterprise.md) </span><span class="sxs-lookup"><span data-stu-id="723dc-131">[Automated Administration Across an Enterprise](automated-administration-across-an-enterprise.md) </span></span>  
 [<span data-ttu-id="723dc-132">マスター サーバーからの複数のターゲット サーバーの参加の解除</span><span class="sxs-lookup"><span data-stu-id="723dc-132">Defect Multiple Target Servers from a Master Server</span></span>](defect-multiple-target-servers-from-a-master-server.md)  
