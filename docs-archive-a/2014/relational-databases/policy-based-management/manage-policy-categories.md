---
title: ポリシー カテゴリの管理 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.dmf.policycategories.f1
ms.assetid: d188a819-731f-4029-98aa-780d3299a0ce
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 168d05dd88286263da1dca5456a2c6072e946786
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634461"
---
# <a name="manage-policy-categories"></a><span data-ttu-id="e95bd-102">ポリシー カテゴリの管理</span><span class="sxs-lookup"><span data-stu-id="e95bd-102">Manage Policy Categories</span></span>
  <span data-ttu-id="e95bd-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して、カテゴリ内の使用可能な、いずれかまたはすべてのポリシーを [!INCLUDE[tsql](../../includes/tsql-md.md)]のインスタンス全体に適用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e95bd-103">This topic describes how to apply any or all available policies in a category to the whole instance of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="e95bd-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="e95bd-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="e95bd-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="e95bd-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="e95bd-106">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="e95bd-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="e95bd-107">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="e95bd-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="e95bd-108">**カテゴリ ポリシーを SQL Server インスタンスに適用するために使用するもの:**</span><span class="sxs-lookup"><span data-stu-id="e95bd-108">**To apply category policies to a SQL Server instance, using:**</span></span>  
  
     [<span data-ttu-id="e95bd-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="e95bd-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="e95bd-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="e95bd-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="e95bd-111">はじめに</span><span class="sxs-lookup"><span data-stu-id="e95bd-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="e95bd-112">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="e95bd-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="e95bd-113">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]を使用している場合、 **[データベースのサブスクリプションの要求]** チェック ボックスがオフになっているときには、サーバーの関連部分 (1 つ以上のデータベースやテーブルなど) にポリシー カテゴリを個別に適用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e95bd-113">When using [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], if the **Mandate Database Subscriptions** check box is not selected, the policy category must be individually applied to each relevant portion of the server, such as one or more databases or tables.</span></span>  
  
-   <span data-ttu-id="e95bd-114">存在しないポリシー カテゴリを指定すると、新しいポリシー カテゴリが作成され、ストアド プロシージャの実行時にすべてのデータベースに対してサブスクリプションが要求されます。</span><span class="sxs-lookup"><span data-stu-id="e95bd-114">If you specify a policy category that does not exist, a new policy category is created and the subscription is mandated for all databases when you execute the stored procedure.</span></span> <span data-ttu-id="e95bd-115">新しいカテゴリに要求されたサブスクリプションをクリアすると、そのサブスクリプションは、 *target_object*で指定したデータベースにのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="e95bd-115">If you then clear the mandated subscription for the new category, the subscription will only apply for the database that you specified as the *target_object*.</span></span> <span data-ttu-id="e95bd-116">要求されたサブスクリプションの設定を変更する方法の詳細については、「[sp_syspolicy_update_policy_category &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syspolicy-update-policy-category-subscription-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e95bd-116">For more information about how to change a mandated subscription setting, see [sp_syspolicy_update_policy_category &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syspolicy-update-policy-category-subscription-transact-sql).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="e95bd-117">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="e95bd-117">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="e95bd-118">Permissions</span><span class="sxs-lookup"><span data-stu-id="e95bd-118">Permissions</span></span>  
 <span data-ttu-id="e95bd-119">このストアド プロシージャは、ストアド プロシージャの現在の所有者のコンテキストで実行されます。</span><span class="sxs-lookup"><span data-stu-id="e95bd-119">This stored procedure runs in the context of the current owner of the stored procedure.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="e95bd-120">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="e95bd-120">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-apply-category-policies-to-a-sql-server-instance"></a><span data-ttu-id="e95bd-121">カテゴリ ポリシーを SQL Server インスタンスに適用するには</span><span class="sxs-lookup"><span data-stu-id="e95bd-121">To apply category policies to a SQL Server instance</span></span>  
  
1.  <span data-ttu-id="e95bd-122">**オブジェクト エクスプ ローラー**で、プラス記号をクリックして、カテゴリ ポリシーを適用するサーバーを展開します。</span><span class="sxs-lookup"><span data-stu-id="e95bd-122">In **Object Explorer**, click the plus sign to expand the server where you will apply category policies.</span></span>  
  
2.  <span data-ttu-id="e95bd-123">プラス記号をクリックして **[管理]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="e95bd-123">Click the plus sign to expand the **Management** folder.</span></span>  
  
3.  <span data-ttu-id="e95bd-124">**[ポリシー管理]** を右クリックし、 **[カテゴリの管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e95bd-124">Right-click **Policy Management** and select **Manage Categories**.</span></span>  
  
     <span data-ttu-id="e95bd-125">**[ポリシー カテゴリの管理]** ダイアログ ボックスには、次の情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="e95bd-125">The following information is available in the **Manage Policy Categories** dialog box:</span></span>  
  
     <span data-ttu-id="e95bd-126">**Name**</span><span class="sxs-lookup"><span data-stu-id="e95bd-126">**Name**</span></span>  
     <span data-ttu-id="e95bd-127">ポリシー カテゴリの名前です。</span><span class="sxs-lookup"><span data-stu-id="e95bd-127">The name of the policy category.</span></span>  
  
     <span data-ttu-id="e95bd-128">**[データベースのサブスクリプションの要求]**</span><span class="sxs-lookup"><span data-stu-id="e95bd-128">**Mandate Database Subscriptions**</span></span>  
     <span data-ttu-id="e95bd-129">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスのすべてのデータベースに、ポリシー カテゴリ内のポリシーを強制的に適用します。</span><span class="sxs-lookup"><span data-stu-id="e95bd-129">Forces all databases on the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to enforce policies in the policy category.</span></span>  
  
4.  <span data-ttu-id="e95bd-130">ポリシー カテゴリを SQL Server インスタンスに適用するために、 **[データベースのサブスクリプションの要求]** の下のいずれかまたはすべてのチェック ボックスをオンまたはオフにします。</span><span class="sxs-lookup"><span data-stu-id="e95bd-130">Select or clear any or all check boxes under **Mandate Database Subscriptions** to apply that policy category to the SQL Server instance.</span></span>  
  
5.  <span data-ttu-id="e95bd-131">完了したら、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e95bd-131">When finished, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="e95bd-132">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="e95bd-132">Using Transact-SQL</span></span>  
  
#### <a name="to-apply-category-policies-to-a-sql-server-instance"></a><span data-ttu-id="e95bd-133">カテゴリ ポリシーを SQL Server インスタンスに適用するには</span><span class="sxs-lookup"><span data-stu-id="e95bd-133">To apply category policies to a SQL Server instance</span></span>  
  
1.  <span data-ttu-id="e95bd-134">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="e95bd-134">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="e95bd-135">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e95bd-135">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="e95bd-136">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e95bd-136">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE msdb;  
    GO  
    -- configures the specified database to subscribe to a policy category that is named 'Table Naming Policies'.  
    EXEC dbo.sp_syspolicy_add_policy_category_subscription @target_type = N'DATABASE'  
    , @target_object = N'AdventureWorks2012'  
    , @policy_category = N'Table Naming Policies';  
    GO  
    ```  
  
 <span data-ttu-id="e95bd-137">詳細については、「[sp_syspolicy_add_policy_category_subscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syspolicy-add-policy-category-subscription-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e95bd-137">For more information, see [sp_syspolicy_add_policy_category_subscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syspolicy-add-policy-category-subscription-transact-sql).</span></span>  
  
  
