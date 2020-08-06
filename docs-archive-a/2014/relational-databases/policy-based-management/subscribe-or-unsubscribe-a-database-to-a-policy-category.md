---
title: ポリシー カテゴリへのデータベースのサブスクライブまたはアンサブスクライブ | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.dmf.groupsubscription.f1
ms.assetid: d2c31769-7098-428e-ad9c-ef56541b7c52
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2b4ca6f804352b57b30b42012da93e0d031be8d4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715190"
---
# <a name="subscribe-or-unsubscribe-a-database--to-a-policy-category"></a><span data-ttu-id="be276-102">ポリシー カテゴリへのデータベースのサブスクライブまたはアンサブスクライブ</span><span class="sxs-lookup"><span data-stu-id="be276-102">Subscribe or Unsubscribe a Database  to a Policy Category</span></span>
  <span data-ttu-id="be276-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して、ポリシー カテゴリにデータベースをサブスクライブまたはアンサブスクライブする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="be276-103">This topic describes how to subscribe or unsubscribe a database to a policy category.in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="be276-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="be276-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="be276-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="be276-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="be276-106">Security</span><span class="sxs-lookup"><span data-stu-id="be276-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="be276-107">**ポリシー カテゴリにデータベースをサブスクライブまたはアンサブスクライブするために使用するもの:**</span><span class="sxs-lookup"><span data-stu-id="be276-107">**To subscribe or unsubscribe a database to a policy category., using:**</span></span>  
  
     [<span data-ttu-id="be276-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="be276-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="be276-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="be276-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="be276-110">はじめに</span><span class="sxs-lookup"><span data-stu-id="be276-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="be276-111">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="be276-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="be276-112">Permissions</span><span class="sxs-lookup"><span data-stu-id="be276-112">Permissions</span></span>  
 <span data-ttu-id="be276-113">db_owner 固定データベース ロールのメンバーシップが必要です。</span><span class="sxs-lookup"><span data-stu-id="be276-113">Requires membership in the db_owner fixed database role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="be276-114">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="be276-114">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-subscribe-or-unsubscribe-a-database-to-a-policy-category"></a><span data-ttu-id="be276-115">ポリシー カテゴリにデータベースをサブスクライブまたはアンサブスクライブするには</span><span class="sxs-lookup"><span data-stu-id="be276-115">To subscribe or unsubscribe a database to a policy category</span></span>  
  
1.  <span data-ttu-id="be276-116">**オブジェクト エクスプローラー**で、カテゴリのサブスクリプションを管理するデータベースが格納されているサーバーをプラス記号をクリックして展開します。</span><span class="sxs-lookup"><span data-stu-id="be276-116">In **Object Explorer**, click the plus sign to expand the server that contains the database wherein you want to manage category subscriptions.</span></span>  
  
2.  <span data-ttu-id="be276-117">プラス記号をクリックして **[データベース]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="be276-117">Click the plus sign to expand the **Databases** folder.</span></span>  
  
3.  <span data-ttu-id="be276-118">カテゴリのサブスクリプションを管理するデータベースを右クリックし、 **[ポリシー]** をポイントし、 **[カテゴリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="be276-118">Right-click the database wherein you want to manage category subscriptions, point to **Policies**, and select **Categories**</span></span>  
  
     <span data-ttu-id="be276-119">**[カテゴリ]** ダイアログ ボックスでは、次のオプションを使用できます。</span><span class="sxs-lookup"><span data-stu-id="be276-119">The following options are available in the **Categories** dialog box:</span></span>  
  
     <span data-ttu-id="be276-120">[列の展開]</span><span class="sxs-lookup"><span data-stu-id="be276-120">Expand column</span></span>  
     <span data-ttu-id="be276-121">クリックすると、ポリシー カテゴリが展開され、</span><span class="sxs-lookup"><span data-stu-id="be276-121">Click to expand a policy category.</span></span> <span data-ttu-id="be276-122">カテゴリに含まれているすべてのポリシーが一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="be276-122">This lists all the policies that are included in the category.</span></span>  
  
     <span data-ttu-id="be276-123">**名前**</span><span class="sxs-lookup"><span data-stu-id="be276-123">**Name**</span></span>  
     <span data-ttu-id="be276-124">ポリシー カテゴリの名前です。</span><span class="sxs-lookup"><span data-stu-id="be276-124">The name of the policy category.</span></span>  
  
     <span data-ttu-id="be276-125">**まだ**</span><span class="sxs-lookup"><span data-stu-id="be276-125">**Subscribed**</span></span>  
     <span data-ttu-id="be276-126">対象がポリシー カテゴリにサブスクライブしているかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="be276-126">Indicates whether the target has subscribed to the policy category.</span></span> <span data-ttu-id="be276-127">このチェック ボックスが無効になっている場合、ポリシー カテゴリの **[データベースのサブスクリプションの要求]** が設定されています。</span><span class="sxs-lookup"><span data-stu-id="be276-127">If this check box is disabled, the policy category is set for **Mandate Database Subscriptions**.</span></span> <span data-ttu-id="be276-128">つまり、ポリシー カテゴリはサーバー上のすべてのデータベースに適用されます。</span><span class="sxs-lookup"><span data-stu-id="be276-128">This means that the policy category applies to all databases on the server.</span></span>  
  
     <span data-ttu-id="be276-129">**ポリシー**</span><span class="sxs-lookup"><span data-stu-id="be276-129">**Policy**</span></span>  
     <span data-ttu-id="be276-130">ポリシー グループを展開すると、ポリシー カテゴリ内のポリシーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="be276-130">When policy groups are expanded, displays the policies in the policy category.</span></span>  
  
     <span data-ttu-id="be276-131">**有効**</span><span class="sxs-lookup"><span data-stu-id="be276-131">**Enabled**</span></span>  
     <span data-ttu-id="be276-132">ポリシーが有効であるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="be276-132">Indicates whether the policies are enabled or disabled.</span></span>  
  
     <span data-ttu-id="be276-133">**[実行モード]**</span><span class="sxs-lookup"><span data-stu-id="be276-133">**Execution Mode**</span></span>  
     <span data-ttu-id="be276-134">ポリシーの実行モードが表示されます。</span><span class="sxs-lookup"><span data-stu-id="be276-134">Displays the execution mode of the policy.</span></span>  
  
     <span data-ttu-id="be276-135">**HISTORY**</span><span class="sxs-lookup"><span data-stu-id="be276-135">**History**</span></span>  
     <span data-ttu-id="be276-136">ログ ファイル ビューアーを開いてポリシー履歴を確認するには、[履歴の表示] ハイパーリンクをクリックします。</span><span class="sxs-lookup"><span data-stu-id="be276-136">Click the View History hyperlink to open the Log File Viewer to see the policy history.</span></span>  
  
4.  <span data-ttu-id="be276-137">ポリシー ベースの管理カテゴリにサブスクライブするには、 **[サブスクライブ済み]** 列の下のカテゴリのチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="be276-137">To subscribe to a Policy-Based Management category, select the category's check box under the **Subscribed** column.</span></span> <span data-ttu-id="be276-138">カテゴリからアンサブスクライブするには、チェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="be276-138">To unsubscribe from a category, clear the check box.</span></span>  
  
5.  <span data-ttu-id="be276-139">完了したら、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="be276-139">When finished, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="be276-140">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="be276-140">Using Transact-SQL</span></span>  
  
#### <a name="to-subscribe-a-database-to-a-policy-category"></a><span data-ttu-id="be276-141">ポリシー カテゴリにデータベースをサブスクライブするには</span><span class="sxs-lookup"><span data-stu-id="be276-141">To subscribe a database to a policy category</span></span>  
  
1.  <span data-ttu-id="be276-142">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="be276-142">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="be276-143">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="be276-143">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="be276-144">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="be276-144">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    -- Adds a subscription to the 'Finance' policy category for the AdventureWorks2012 database.  
    EXEC sys.sp_syspolicy_subscribe_to_policy_category @policy_category = N'Finance';  
    GO  
    ```  
  
 <span data-ttu-id="be276-145">詳細については、「[sp_syspolicy_subscribe_to_policy_category &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syspolicy-subscribe-to-policy-category-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="be276-145">For more information, see [sp_syspolicy_subscribe_to_policy_category &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syspolicy-subscribe-to-policy-category-transact-sql).</span></span>  
  
#### <a name="to-unsubscribe-a-database-to-a-policy-category"></a><span data-ttu-id="be276-146">ポリシー カテゴリからデータベースをアンサブスクライブするには</span><span class="sxs-lookup"><span data-stu-id="be276-146">To unsubscribe a database to a policy category</span></span>  
  
1.  <span data-ttu-id="be276-147">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="be276-147">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="be276-148">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="be276-148">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="be276-149">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="be276-149">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    -- Deletes a subscription to the 'Finance' policy category for the AdventureWorks2012 database.  
    EXEC sys.sp_syspolicy_unsubscribe_from_policy_category @policy_category = N'Finance';  
    GO  
    ```  
  
 <span data-ttu-id="be276-150">詳細については、「[sp_syspolicy_unsubscribe_from_policy_category &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syspolicy-unsubscribe-from-policy-category-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="be276-150">For more information, see [sp_syspolicy_unsubscribe_from_policy_category &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syspolicy-unsubscribe-from-policy-category-transact-sql).</span></span>  
  
  
