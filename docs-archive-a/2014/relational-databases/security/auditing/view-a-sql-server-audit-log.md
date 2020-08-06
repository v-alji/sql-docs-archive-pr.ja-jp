---
title: SQL Server 監査ログの表示 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- audits [SQL Server], viewing logs
- viewing audit logs
- logs [SQL Server], audit
ms.assetid: e8feaca0-7852-422b-895a-319b965d8d9b
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 8f9902a4fc92ef0b35bae62eb80170762c52fdec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633031"
---
# <a name="view-a-sql-server-audit-log"></a><span data-ttu-id="01a67-102">SQL Server 監査ログの表示</span><span class="sxs-lookup"><span data-stu-id="01a67-102">View a SQL Server Audit Log</span></span>
  <span data-ttu-id="01a67-103">このトピックでは、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] を使用して [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]で SQL Server 監査ログを表示する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="01a67-103">This topic describes how to view a SQL Server audit log in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="01a67-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="01a67-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="01a67-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="01a67-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="01a67-106">Security</span><span class="sxs-lookup"><span data-stu-id="01a67-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="01a67-107">**SQL Server 監査ログを表示する方法:**</span><span class="sxs-lookup"><span data-stu-id="01a67-107">**To view a SQL Server audit log, using:**</span></span>  
  
     [<span data-ttu-id="01a67-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="01a67-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="01a67-109">はじめに</span><span class="sxs-lookup"><span data-stu-id="01a67-109">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="01a67-110">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="01a67-110">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="01a67-111">Permissions</span><span class="sxs-lookup"><span data-stu-id="01a67-111">Permissions</span></span>  
 <span data-ttu-id="01a67-112">`CONTROL SERVER` アクセス許可が必要です。</span><span class="sxs-lookup"><span data-stu-id="01a67-112">Requires the `CONTROL SERVER` permission.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="01a67-113">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="01a67-113">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-a-sql-server-audit-log"></a><span data-ttu-id="01a67-114">SQL Server 監査ログを表示するには</span><span class="sxs-lookup"><span data-stu-id="01a67-114">To view a SQL Server audit log</span></span>  
  
1.  <span data-ttu-id="01a67-115">オブジェクト エクスプローラーで、 **[セキュリティ]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="01a67-115">In Object Explorer, expand the **Security** folder.</span></span>  
  
2.  <span data-ttu-id="01a67-116">**[監査]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="01a67-116">Expand the **Audits** folder.</span></span>  
  
3.  <span data-ttu-id="01a67-117">表示する監査ログを右クリックし、 **[監査ログの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="01a67-117">Right-click the audit log that you want to view and select **View Audit Logs**.</span></span> <span data-ttu-id="01a67-118">[**ログファイルの表示-**_server_name_ ] ダイアログボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="01a67-118">This opens the **Log File Viewer -**_server_name_ dialog box.</span></span> <span data-ttu-id="01a67-119">詳細については、「 [Log File Viewer F1 Help](../../logs/log-file-viewer-f1-help.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="01a67-119">For more information, see [Log File Viewer F1 Help](../../logs/log-file-viewer-f1-help.md).</span></span>  
  
4.  <span data-ttu-id="01a67-120">完了したら、 **[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="01a67-120">When finished, click **Close**.</span></span>  
  
 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] <span data-ttu-id="01a67-121">では、[ログ ファイルの表示] を使用して監査ログを表示することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="01a67-121">recommends viewing the audit log by using the Log File Viewer.</span></span> <span data-ttu-id="01a67-122">ただし、自動監視システムを作成している場合、[sys.fn_get_audit_file &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-get-audit-file-transact-sql) 関数を使用して監査ファイルの情報を直接読み取ることができます。</span><span class="sxs-lookup"><span data-stu-id="01a67-122">However, if you are creating an automated monitoring system, the information in the audit file can be read directly by using the [sys.fn_get_audit_file &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-get-audit-file-transact-sql) function.</span></span> <span data-ttu-id="01a67-123">ファイルを直接読み取ると、わずかに異なる (処理されていない) 形式でデータが返されます。</span><span class="sxs-lookup"><span data-stu-id="01a67-123">Reading the file directly returns data in a slightly different (unprocessed) format.</span></span> <span data-ttu-id="01a67-124">詳細については、「fn_get_audit_file」を参照してください **。**</span><span class="sxs-lookup"><span data-stu-id="01a67-124">See **sys.fn_get_audit_file** for more information</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01a67-125">参照</span><span class="sxs-lookup"><span data-stu-id="01a67-125">See Also</span></span>  
 <span data-ttu-id="01a67-126">[SQL Server Audit &#40;データベース エンジン&#41;](sql-server-audit-database-engine.md) </span><span class="sxs-lookup"><span data-stu-id="01a67-126">[SQL Server Audit &#40;Database Engine&#41;](sql-server-audit-database-engine.md) </span></span>  
 [<span data-ttu-id="01a67-127">セキュリティ ログへの SQL Server 監査イベントの書き込み</span><span class="sxs-lookup"><span data-stu-id="01a67-127">Write SQL Server Audit Events to the Security Log</span></span>](write-sql-server-audit-events-to-the-security-log.md)  
  
  
