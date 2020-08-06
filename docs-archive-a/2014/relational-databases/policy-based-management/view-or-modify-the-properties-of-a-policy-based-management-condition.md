---
title: ポリシー ベースの管理条件のプロパティの表示または変更 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, view policy conditions
- Policy-Based Management, modify policy conditions
ms.assetid: 890d7384-8444-4767-bb6f-f5debb155747
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 08baec48bd13445ef56ea6a29520d23ebaf683b1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634439"
---
# <a name="view-or-modify-the-properties-of-a-policy-based-management-condition"></a><span data-ttu-id="2acb0-102">ポリシー ベースの管理条件のプロパティの表示または変更</span><span class="sxs-lookup"><span data-stu-id="2acb0-102">View or Modify the Properties of a Policy-Based Management Condition</span></span>
  <span data-ttu-id="2acb0-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して、 [!INCLUDE[tsql](../../includes/tsql-md.md)]でポリシー ベースの管理条件のプロパティを表示または変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="2acb0-103">This topic describes how to view or modify the properties of a Policy-Based Management condition in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="2acb0-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="2acb0-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="2acb0-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="2acb0-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="2acb0-106">Security</span><span class="sxs-lookup"><span data-stu-id="2acb0-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="2acb0-107">**以下を使用して条件のプロパティを表示または変更するには:**</span><span class="sxs-lookup"><span data-stu-id="2acb0-107">**To view or modify a condition's properties, using:**</span></span>  
  
     [<span data-ttu-id="2acb0-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="2acb0-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="2acb0-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="2acb0-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="2acb0-110">はじめに</span><span class="sxs-lookup"><span data-stu-id="2acb0-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="2acb0-111">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="2acb0-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="2acb0-112">Permissions</span><span class="sxs-lookup"><span data-stu-id="2acb0-112">Permissions</span></span>  
 <span data-ttu-id="2acb0-113">msdb データベースの PolicyAdministratorRole ロールのメンバーシップが必要です。</span><span class="sxs-lookup"><span data-stu-id="2acb0-113">Requires membership in the PolicyAdministratorRole role in the msdb database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="2acb0-114">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="2acb0-114">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-or-modify-a-conditions-properties"></a><span data-ttu-id="2acb0-115">条件のプロパティを表示または変更するには</span><span class="sxs-lookup"><span data-stu-id="2acb0-115">To view or modify a condition's properties</span></span>  
  
1.  <span data-ttu-id="2acb0-116">**オブジェクト エクスプローラー**で、表示または変更する条件を含むサーバーをプラス記号をクリックして展開します。</span><span class="sxs-lookup"><span data-stu-id="2acb0-116">In **Object Explorer**, click the plus sign to expand the server that contains the condition that you want to view or modify.</span></span>  
  
2.  <span data-ttu-id="2acb0-117">プラス記号をクリックして **[管理]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="2acb0-117">Click the plus sign to expand the **Management** folder.</span></span>  
  
3.  <span data-ttu-id="2acb0-118">プラス記号をクリックして **[ポリシー管理]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="2acb0-118">Click the plus sign to expand **Policy Management**.</span></span>  
  
4.  <span data-ttu-id="2acb0-119">プラス記号をクリックして **[条件]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="2acb0-119">Click the plus sign to expand the **Conditions** folder.</span></span>  
  
5.  <span data-ttu-id="2acb0-120">表示または編集する条件を右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2acb0-120">Right-click the condition that you want to view or edit and select **Properties**.</span></span> <span data-ttu-id="2acb0-121">[_Condition_name_ **条件を開く**] ダイアログボックスで使用可能なオプションの詳細については、「[新しい条件の作成] または [条件を開く] ダイアログボックス[、[全般] ページ](../../integration-services/general-page-of-integration-services-designers-options.md)、[条件を開く] ダイアログボックス、[[説明] ページ](create-new-condition-or-open-condition-dialog-box-description-page.md)」、および[「高度な編集 &#40;条件&#41; ダイアログボックス](advanced-edit-condition-dialog-box.md)」を参照してください。 [Open Condition Dialog Box, Dependent Policies Page](open-condition-dialog-box-dependent-policies-page.md)</span><span class="sxs-lookup"><span data-stu-id="2acb0-121">For more information on the available options in the **Open Condition -**_condition_name_ dialog box, see [Create New Condition or Open Condition Dialog Box, General Page](../../integration-services/general-page-of-integration-services-designers-options.md), [Open Condition Dialog Box, Dependent Policies Page](open-condition-dialog-box-dependent-policies-page.md), [Create New Condition or Open Condition Dialog Box, Description Page](create-new-condition-or-open-condition-dialog-box-description-page.md), and [Advanced Edit &#40;Condition&#41; Dialog Box](advanced-edit-condition-dialog-box.md).</span></span>  
  
6.  <span data-ttu-id="2acb0-122">完了したら、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2acb0-122">When finished, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="2acb0-123">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="2acb0-123">Using Transact-SQL</span></span>  
  
#### <a name="to-view-a-conditions-properties"></a><span data-ttu-id="2acb0-124">条件のプロパティを表示するには</span><span class="sxs-lookup"><span data-stu-id="2acb0-124">To view a condition's properties</span></span>  
  
1.  <span data-ttu-id="2acb0-125">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="2acb0-125">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="2acb0-126">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2acb0-126">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="2acb0-127">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2acb0-127">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE msdb;  
    GO  
    SELECT name,  
       description,  
       facet,  
       expression,  
       is_name_condition,  
       obj_name  
    FROM syspolicy_conditions;  
    GO  
  
    ```  
  
 <span data-ttu-id="2acb0-128">詳細については、「[syspolicy_conditions &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/syspolicy-conditions-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2acb0-128">For more information, see [syspolicy_conditions &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/syspolicy-conditions-transact-sql).</span></span>  
  
  
