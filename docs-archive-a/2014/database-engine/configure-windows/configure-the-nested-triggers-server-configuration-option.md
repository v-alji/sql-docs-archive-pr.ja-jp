---
title: nested triggers サーバー構成オプションの構成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- nested triggers option
ms.assetid: 29d7372b-d406-4a5b-80c6-a2d231d25211
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 7b27e185b0833f2e51be16393ff4d59a81046970
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642307"
---
# <a name="configure-the-nested-triggers-server-configuration-option"></a><span data-ttu-id="c6506-102">nested triggers サーバー構成オプションの構成</span><span class="sxs-lookup"><span data-stu-id="c6506-102">Configure the nested triggers Server Configuration Option</span></span>
  <span data-ttu-id="c6506-103">このトピックでは、 **で** または [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] を使用して、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] nested triggers [!INCLUDE[tsql](../../includes/tsql-md.md)]サーバー構成オプションを構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c6506-103">This topic describes how to configure the **nested triggers** server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="c6506-104">**nested triggers** オプションは、AFTER トリガーを連鎖できるかどうかを制御します。</span><span class="sxs-lookup"><span data-stu-id="c6506-104">The **nested triggers** option controls whether an AFTER trigger can cascade.</span></span> <span data-ttu-id="c6506-105">つまり、1 つの操作が別のトリガーを開始し、開始されたトリガーからさらに別のトリガーを開始するなどの動作ができるかどうかを制御します。</span><span class="sxs-lookup"><span data-stu-id="c6506-105">That is, perform an action that initiates another trigger, which initiates another trigger, and so on.</span></span> <span data-ttu-id="c6506-106">**nested triggers** を 0 に設定すると、AFTER トリガーは連鎖できません。</span><span class="sxs-lookup"><span data-stu-id="c6506-106">When **nested triggers** is set to 0, AFTER triggers cannot cascade.</span></span> <span data-ttu-id="c6506-107">**nested triggers** を 1 (既定値) に設定すると、AFTER トリガーは 32 レベルまで連鎖できます。</span><span class="sxs-lookup"><span data-stu-id="c6506-107">When **nested triggers** is set to 1 (the default), AFTER triggers can cascade to as many as 32 levels.</span></span> <span data-ttu-id="c6506-108">INSTEAD OF トリガーは、このオプションの設定に関係なく入れ子にできます。</span><span class="sxs-lookup"><span data-stu-id="c6506-108">INSTEAD OF triggers can be nested regardless of the setting of this option.</span></span>  
  
 <span data-ttu-id="c6506-109">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="c6506-109">**In This Topic**</span></span>  
  
-   <span data-ttu-id="c6506-110">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="c6506-110">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="c6506-111">Security</span><span class="sxs-lookup"><span data-stu-id="c6506-111">Security</span></span>](#Security)  
  
-   <span data-ttu-id="c6506-112">**以下を使用して nested triggers オプションを構成するには:**</span><span class="sxs-lookup"><span data-stu-id="c6506-112">**To configure the nested triggers option, using:**</span></span>  
  
     [<span data-ttu-id="c6506-113">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="c6506-113">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="c6506-114">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="c6506-114">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="c6506-115">**補足情報:** [nested triggers オプションを構成した後](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="c6506-115">**Follow Up:**  [After you configure the nested triggers option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="c6506-116">はじめに</span><span class="sxs-lookup"><span data-stu-id="c6506-116">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="c6506-117">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="c6506-117">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="c6506-118">Permissions</span><span class="sxs-lookup"><span data-stu-id="c6506-118">Permissions</span></span>  
 <span data-ttu-id="c6506-119">パラメーターなしで、または最初のパラメーターだけを指定して **sp_configure** を実行する権限は、既定ですべてのユーザーに付与されます。</span><span class="sxs-lookup"><span data-stu-id="c6506-119">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="c6506-120">両方のパラメーターを指定して **sp_configure** を実行し構成オプションを変更したり RECONFIGURE ステートメントを実行したりするには、ALTER SETTINGS サーバーレベル権限がユーザーに付与されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="c6506-120">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="c6506-121">ALTER SETTINGS 権限は、 **sysadmin** 固定サーバー ロールと **serveradmin** 固定サーバー ロールでは暗黙のうちに付与されています。</span><span class="sxs-lookup"><span data-stu-id="c6506-121">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="c6506-122">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="c6506-122">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-nested-triggers-option"></a><span data-ttu-id="c6506-123">nested triggers オプションを構成するには</span><span class="sxs-lookup"><span data-stu-id="c6506-123">To configure the nested triggers option</span></span>  
  
1.  <span data-ttu-id="c6506-124">**オブジェクト エクスプローラー**で、サーバーを右クリックし、 **[プロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="c6506-124">In **Object Explorer**, right-click a server, and then select **Properties**.</span></span>  
  
2.  <span data-ttu-id="c6506-125">**[詳細設定]** ページで、 **[トリガーから他のトリガーの起動を許可する]** オプションを **[True]** (既定) または **[False]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="c6506-125">On the **Advanced** page, set the **Allow Triggers to Fire Others** option to **True** (the default) or **False**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="c6506-126">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="c6506-126">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-nested-triggers-option"></a><span data-ttu-id="c6506-127">nested triggers オプションを構成するには</span><span class="sxs-lookup"><span data-stu-id="c6506-127">To configure the nested triggers option</span></span>  
  
1.  <span data-ttu-id="c6506-128">[!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="c6506-128">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="c6506-129">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c6506-129">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="c6506-130">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c6506-130">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="c6506-131">この例では、 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) を使用して、 `nested triggers` オプションの値を `0`に設定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="c6506-131">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to set the value of the `nested triggers` option to `0`.</span></span>  
  
```wmimof  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE ;  
GO  
EXEC sp_configure 'nested triggers', 0 ;  
GO  
RECONFIGURE;  
GO  
  
```  
  
 <span data-ttu-id="c6506-132">詳細については、「 [サーバー構成オプション &#40;SQL Server&#41;](server-configuration-options-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c6506-132">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-you-configure-the-nested-triggers-option"></a><a name="FollowUp"></a><span data-ttu-id="c6506-133">補足情報: nested triggers オプションを構成した後</span><span class="sxs-lookup"><span data-stu-id="c6506-133">Follow Up: After you configure the nested triggers option</span></span>  
 <span data-ttu-id="c6506-134">新しい設定は、サーバーを再起動しなくてもすぐに有効になります。</span><span class="sxs-lookup"><span data-stu-id="c6506-134">The setting takes effect immediately without restarting the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6506-135">参照</span><span class="sxs-lookup"><span data-stu-id="c6506-135">See Also</span></span>  
 <span data-ttu-id="c6506-136">[入れ子になったトリガーの作成](../../relational-databases/triggers/create-nested-triggers.md) </span><span class="sxs-lookup"><span data-stu-id="c6506-136">[Create Nested Triggers](../../relational-databases/triggers/create-nested-triggers.md) </span></span>  
 <span data-ttu-id="c6506-137">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c6506-137">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="c6506-138">[サーバー構成オプション &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="c6506-138">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="c6506-139">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="c6506-139">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
