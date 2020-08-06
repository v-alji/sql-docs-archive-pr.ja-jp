---
title: ポリシー ベースの管理の全般プロパティの構成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.dmf.PolicyManagement.f1
helpviewer_keywords:
- Policy-Based Management, configure properties
ms.assetid: 6d1e0e37-29ea-408a-a055-384984d884be
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: a2efb37fafa29bcb043dedbcfa8719d0092b1c77
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715202"
---
# <a name="configure-the-general-properties-of-policy-based-management"></a><span data-ttu-id="e7183-102">ポリシー ベースの管理の全般プロパティの構成</span><span class="sxs-lookup"><span data-stu-id="e7183-102">Configure the General Properties of Policy-Based Management</span></span>
  <span data-ttu-id="e7183-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して、 [!INCLUDE[tsql](../../includes/tsql-md.md)]でポリシー ベースの管理のプロパティを構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e7183-103">This topic describes how to configure the properties for Policy-Based Management in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="e7183-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="e7183-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="e7183-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="e7183-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="e7183-106">Security</span><span class="sxs-lookup"><span data-stu-id="e7183-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="e7183-107">**ポリシー ベースの管理を構成するために使用するもの:**</span><span class="sxs-lookup"><span data-stu-id="e7183-107">**To configure Policy-Based Management, using:**</span></span>  
  
     [<span data-ttu-id="e7183-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="e7183-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="e7183-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="e7183-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="e7183-110">はじめに</span><span class="sxs-lookup"><span data-stu-id="e7183-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="e7183-111">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="e7183-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="e7183-112">Permissions</span><span class="sxs-lookup"><span data-stu-id="e7183-112">Permissions</span></span>  
 <span data-ttu-id="e7183-113">PolicyAdministratorRole 固定データベース ロールのメンバーシップが必要です。</span><span class="sxs-lookup"><span data-stu-id="e7183-113">Requires membership in the PolicyAdministratorRole fixed database role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="e7183-114">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="e7183-114">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-policy-based-management"></a><span data-ttu-id="e7183-115">ポリシー ベースの管理を構成するには</span><span class="sxs-lookup"><span data-stu-id="e7183-115">To configure Policy-Based Management</span></span>  
  
1.  <span data-ttu-id="e7183-116">**オブジェクト エクスプローラー**で、プラス記号をクリックして、ポリシー ベースの管理のプロパティを構成するサーバーを展開します。</span><span class="sxs-lookup"><span data-stu-id="e7183-116">In **Object Explorer**, click the plus sign to expand the server where you want to configure Policy-Based Management properties.</span></span>  
  
2.  <span data-ttu-id="e7183-117">プラス記号をクリックして **[管理]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="e7183-117">Click the plus sign to expand the **Management** folder.</span></span>  
  
3.  <span data-ttu-id="e7183-118">**[ポリシー管理]** を右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e7183-118">Right-click **Policy Management** and select **Properties**.</span></span>  
  
     <span data-ttu-id="e7183-119">**[ポリシー管理のプロパティ]** ダイアログ ボックスでは、次のオプションを使用できます。</span><span class="sxs-lookup"><span data-stu-id="e7183-119">The following options are available in **Policy Management Properties** dialog box.</span></span>  
  
     <span data-ttu-id="e7183-120">**有効**</span><span class="sxs-lookup"><span data-stu-id="e7183-120">**Enabled**</span></span>  
     <span data-ttu-id="e7183-121">ポリシー ベースの管理を有効にするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="e7183-121">Specifies whether Policy-Based Management is enabled.</span></span>  
  
     <span data-ttu-id="e7183-122">**HistoryRetentionInDays**</span><span class="sxs-lookup"><span data-stu-id="e7183-122">**HistoryRetentionInDays**</span></span>  
     <span data-ttu-id="e7183-123">ポリシー評価履歴を保持する日数を指定します。</span><span class="sxs-lookup"><span data-stu-id="e7183-123">Specifies the number of days that policy evaluation history should be retained.</span></span> <span data-ttu-id="e7183-124">この値が 0 (既定値) の場合、履歴は自動的には削除されません。</span><span class="sxs-lookup"><span data-stu-id="e7183-124">If this value is 0 (the default), the history will not be automatically removed.</span></span>  
  
     <span data-ttu-id="e7183-125">**LogOnSuccess**</span><span class="sxs-lookup"><span data-stu-id="e7183-125">**LogOnSuccess**</span></span>  
     <span data-ttu-id="e7183-126">ポリシー ベースの管理のログに成功したポリシー評価を記録するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="e7183-126">Specifies whether Policy-Based Management logs successful policy evaluations.</span></span>  
  
    -   <span data-ttu-id="e7183-127">この値が false (既定値) の場合、失敗したポリシー評価だけが記録されます。</span><span class="sxs-lookup"><span data-stu-id="e7183-127">When this value is false (the default), only failed policy evaluations are logged.</span></span>  
  
    -   <span data-ttu-id="e7183-128">この値が true の場合、成功したポリシー評価と失敗したポリシー評価の両方が記録されます。</span><span class="sxs-lookup"><span data-stu-id="e7183-128">When this value is true, both successful and failed policy evaluations are logged.</span></span>  
  
4.  <span data-ttu-id="e7183-129">完了したら、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e7183-129">When finished, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="e7183-130">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="e7183-130">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-policy-based-management"></a><span data-ttu-id="e7183-131">ポリシー ベースの管理を構成するには</span><span class="sxs-lookup"><span data-stu-id="e7183-131">To configure Policy-Based Management</span></span>  
  
1.  <span data-ttu-id="e7183-132">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="e7183-132">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="e7183-133">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e7183-133">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="e7183-134">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e7183-134">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- enables Policy-Based Management   
    USE msdb;  
    GO  
    EXEC dbo.sp_syspolicy_configure   
         @name = N'Enabled',   
         @value = 1;  
    GO  
    ```  
  
 <span data-ttu-id="e7183-135">詳細については、「[sp_syspolicy_configure &#40;Transact SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syspolicy-configure-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e7183-135">For more information, see [sp_syspolicy_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syspolicy-configure-transact-sql).</span></span>  
  
  
