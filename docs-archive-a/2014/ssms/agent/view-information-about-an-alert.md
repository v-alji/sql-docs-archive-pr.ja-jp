---
title: 警告に関する情報を表示する方法 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, alerts
- viewing alerts
- alerts [SQL Server], viewing
- displaying alerts
- status information [SQL Server], alerts
ms.assetid: a0e3a8c4-e3c2-42a5-b2f8-aa06061d3fa6
author: stevestein
ms.author: sstein
ms.openlocfilehash: ee72512a507299e71f13fee689709a9403bb04e4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634778"
---
# <a name="view-information-about-an-alert"></a><span data-ttu-id="628eb-102">View Information About an Alert</span><span class="sxs-lookup"><span data-stu-id="628eb-102">View Information About an Alert</span></span>
  <span data-ttu-id="628eb-103">このトピック [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] は、またはを使用して、でエージェントの警告に関する情報を表示する方法について説明し [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="628eb-103">This topic describes how to view information about [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent alerts in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="628eb-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="628eb-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="628eb-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="628eb-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="628eb-106">Security</span><span class="sxs-lookup"><span data-stu-id="628eb-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="628eb-107">**警告に関する情報を表示する方法:**</span><span class="sxs-lookup"><span data-stu-id="628eb-107">**To view information about an alert, using:**</span></span>  
  
     [<span data-ttu-id="628eb-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="628eb-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="628eb-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="628eb-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="628eb-110">はじめに</span><span class="sxs-lookup"><span data-stu-id="628eb-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="628eb-111">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="628eb-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="628eb-112">Permissions</span><span class="sxs-lookup"><span data-stu-id="628eb-112">Permissions</span></span>  
 <span data-ttu-id="628eb-113">既定では、警告に関する情報を表示できるのは、 **sysadmin** 固定サーバー ロールのメンバーだけです。</span><span class="sxs-lookup"><span data-stu-id="628eb-113">By default, members of the **sysadmin** fixed server role can view information about an alert.</span></span> <span data-ttu-id="628eb-114">それ以外のユーザーには、 **msdb** データベースの **SQLAgentOperatorRole** 固定サーバー ロールを与える必要があります。</span><span class="sxs-lookup"><span data-stu-id="628eb-114">Other users must be granted the **SQLAgentOperatorRole** fixed database role in the **msdb** database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="628eb-115">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="628eb-115">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-information-about-an-alert"></a><span data-ttu-id="628eb-116">警告に関する情報を表示するには</span><span class="sxs-lookup"><span data-stu-id="628eb-116">To view information about an alert</span></span>  
  
1.  <span data-ttu-id="628eb-117">**オブジェクト エクスプローラー** で、プラス記号をクリックして、警告に関する情報を表示するサーバーを展開します。</span><span class="sxs-lookup"><span data-stu-id="628eb-117">In **Object Explorer,** click the plus sign to expand the server where you want to view information about an alert.</span></span>  
  
2.  <span data-ttu-id="628eb-118">プラス記号をクリックして **[SQL Server エージェント]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="628eb-118">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="628eb-119">プラス記号をクリックして **[警告]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="628eb-119">Click the plus sign to expand the **Alerts** folder.</span></span>  
  
4.  <span data-ttu-id="628eb-120">表示する情報がある警告を右クリックし、**[プロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="628eb-120">Right-click the alert that has the information you want to view and select **Properties**.</span></span>  
  
     <span data-ttu-id="628eb-121">[_alert_name_**警告のプロパティ**] ダイアログ ボックスに表示される使用可能なオプションの詳細については、以下を参照してください。</span><span class="sxs-lookup"><span data-stu-id="628eb-121">For more information on the available options contained in the _alert_name_**alert properties** dialog box, see:</span></span>  
  
    -   <span data-ttu-id="628eb-122">[[アラートのプロパティ]-[新しいアラート &#40;全般] ページ&#41;](../../integration-services/general-page-of-integration-services-designers-options.md)</span><span class="sxs-lookup"><span data-stu-id="628eb-122">[Alert Properties-New Alert &#40;General Page&#41;](../../integration-services/general-page-of-integration-services-designers-options.md)</span></span>  
  
    -   <span data-ttu-id="628eb-123">[[アラートのプロパティ]-[新しい警告 &#40;応答] ページ&#41;](alert-properties-new-alert-response-page.md)</span><span class="sxs-lookup"><span data-stu-id="628eb-123">[Alert Properties-New Alert &#40;Response Page&#41;](alert-properties-new-alert-response-page.md)</span></span>  
  
    -   <span data-ttu-id="628eb-124">[[アラートのプロパティ]: [新しい警告 &#40;オプション] ページ&#41;](alert-properties-new-alert-options-page.md)</span><span class="sxs-lookup"><span data-stu-id="628eb-124">[Alert Properties: New Alert &#40;Options Page&#41;](alert-properties-new-alert-options-page.md)</span></span>  
  
    -   <span data-ttu-id="628eb-125">[[警告のプロパティ] ([履歴] ページ)](alert-properties-history-page.md)</span><span class="sxs-lookup"><span data-stu-id="628eb-125">[Alert Properties &#40;History Page&#41;](alert-properties-history-page.md)</span></span>  
  
5.  <span data-ttu-id="628eb-126">完了したら、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="628eb-126">When finished, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="628eb-127">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="628eb-127">Using Transact-SQL</span></span>  
  
#### <a name="to-view-information-about-an-alert"></a><span data-ttu-id="628eb-128">警告に関する情報を表示するには</span><span class="sxs-lookup"><span data-stu-id="628eb-128">To view information about an alert</span></span>  
  
1.  <span data-ttu-id="628eb-129">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="628eb-129">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="628eb-130">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="628eb-130">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="628eb-131">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="628eb-131">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- reports information about the Demo: Sev. 25 Errors alert  
    -- This example assumes that the 'Demo: Sev. 25 Errors' alert exists.  
    USE msdb ;  
    GO  
  
    EXEC sp_help_alert @alert_name = 'Demo: Sev. 25 Errors'  
    GO  
    ```  
  
 <span data-ttu-id="628eb-132">詳細については、「 [sp_help_alert &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-help-alert-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="628eb-132">For more information, see [sp_help_alert &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-alert-transact-sql).</span></span>  
  
  
