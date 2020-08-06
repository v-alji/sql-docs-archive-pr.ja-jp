---
title: データ コレクションを有効または無効にする方法 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- data collector [SQL Server], disabling
- data collector [SQL Server], enabling
ms.assetid: 0137971b-fb48-4a3e-822a-3df2b9bb09d7
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: af5cc647a63d3a9451086fc9e2211dec809e88fb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633162"
---
# <a name="enable-or-disable-data-collection"></a><span data-ttu-id="6c96b-102">データ コレクションを有効または無効にする方法</span><span class="sxs-lookup"><span data-stu-id="6c96b-102">Enable or Disable Data Collection</span></span>
  <span data-ttu-id="6c96b-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して、データ コレクションを有効または無効にする方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="6c96b-103">This topic describes how to enable or disable data collection in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="6c96b-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="6c96b-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="6c96b-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="6c96b-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="6c96b-106">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="6c96b-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="6c96b-107">**データ コレクションを有効または無効にする方法:**</span><span class="sxs-lookup"><span data-stu-id="6c96b-107">**To enable or disable data collection, using:**</span></span>  
  
     [<span data-ttu-id="6c96b-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="6c96b-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="6c96b-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="6c96b-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="6c96b-110">はじめに</span><span class="sxs-lookup"><span data-stu-id="6c96b-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="6c96b-111">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="6c96b-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="6c96b-112">Permissions</span><span class="sxs-lookup"><span data-stu-id="6c96b-112">Permissions</span></span>  
 <span data-ttu-id="6c96b-113">このプロシージャを実行するには、(EXECUTE 権限を持つ) **dc_admin** または **dc_operator** 固定データベース ロールのメンバーシップが必要です。</span><span class="sxs-lookup"><span data-stu-id="6c96b-113">Requires membership in the **dc_admin** or **dc_operator** (with EXECUTE permission) fixed database role to execute this procedure.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="6c96b-114">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="6c96b-114">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-enable-the-data-collector"></a><span data-ttu-id="6c96b-115">データ コレクターを有効にするには</span><span class="sxs-lookup"><span data-stu-id="6c96b-115">To enable the data collector</span></span>  
  
1.  <span data-ttu-id="6c96b-116">オブジェクト エクスプローラーで、 **[管理]** ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="6c96b-116">In Object Explorer, expand the **Management** node.</span></span>  
  
2.  <span data-ttu-id="6c96b-117">**[データ コレクション]** を右クリックし、 **[データ コレクションの有効化]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6c96b-117">Right-click **Data Collection**, and then click **Enable Data Collection**.</span></span>  
  
#### <a name="to-disable-the-data-collector"></a><span data-ttu-id="6c96b-118">データ コレクターを無効にするには</span><span class="sxs-lookup"><span data-stu-id="6c96b-118">To disable the data collector</span></span>  
  
1.  <span data-ttu-id="6c96b-119">オブジェクト エクスプローラーで、 **[管理]** ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="6c96b-119">In Object Explorer, expand the **Management** node.</span></span>  
  
2.  <span data-ttu-id="6c96b-120">**[データ コレクション]** を右クリックし、 **[データ コレクションの無効化]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6c96b-120">Right-click **Data Collection**, and then click **Disable Data Collection**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="6c96b-121">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="6c96b-121">Using Transact-SQL</span></span>  
  
#### <a name="to-enable-the-data-collector"></a><span data-ttu-id="6c96b-122">データ コレクターを有効にするには</span><span class="sxs-lookup"><span data-stu-id="6c96b-122">To enable the data collector</span></span>  
  
1.  <span data-ttu-id="6c96b-123">[!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="6c96b-123">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="6c96b-124">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6c96b-124">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="6c96b-125">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6c96b-125">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="6c96b-126">この例では [sp_syscollector_enable_collector](/sql/relational-databases/system-stored-procedures/sp-syscollector-enable-collector-transact-sql) を使用してデータ コレクターを有効にします。</span><span class="sxs-lookup"><span data-stu-id="6c96b-126">This example uses [sp_syscollector_enable_collector](/sql/relational-databases/system-stored-procedures/sp-syscollector-enable-collector-transact-sql) to enable the data collector.</span></span>  
  
```sql  
USE msdb;  
GO  
EXEC dbo.sp_syscollector_enable_collector ;  
```  
  
#### <a name="to-disable-the-data-collector"></a><span data-ttu-id="6c96b-127">データ コレクターを無効にするには</span><span class="sxs-lookup"><span data-stu-id="6c96b-127">To disable the data collector</span></span>  
  
1.  <span data-ttu-id="6c96b-128">[!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="6c96b-128">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="6c96b-129">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6c96b-129">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="6c96b-130">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6c96b-130">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="6c96b-131">この例では [sp_syscollector_disable_collector](/sql/relational-databases/system-stored-procedures/sp-syscollector-disable-collector-transact-sql) を使用してデータ コレクターを無効にします。</span><span class="sxs-lookup"><span data-stu-id="6c96b-131">This example uses [sp_syscollector_disable_collector](/sql/relational-databases/system-stored-procedures/sp-syscollector-disable-collector-transact-sql) to disable the data collector.</span></span>  
  
```sql  
USE msdb;  
GO  
EXEC dbo.sp_syscollector_disable_collector;  
```  
  
## <a name="see-also"></a><span data-ttu-id="6c96b-132">参照</span><span class="sxs-lookup"><span data-stu-id="6c96b-132">See Also</span></span>  
 <span data-ttu-id="6c96b-133">[[データ コレクション]](data-collection.md) </span><span class="sxs-lookup"><span data-stu-id="6c96b-133">[Data Collection](data-collection.md) </span></span>  
 [<span data-ttu-id="6c96b-134">システム ストアド プロシージャ &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="6c96b-134">System Stored Procedures &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/system-stored-procedures-transact-sql)  
  
  
