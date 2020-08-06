---
title: SQL Server エージェントのエラーログに実行トレースメッセージを書き込む (SQL Server Management Studio) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- logs [SQL Server], SQL Server Agent
- writing trace messages
- traces [SQL Server], SQL Server Agent logs
- SQL Server Agent, errors
- errors [SQL Server Agent]
ms.assetid: 90e3731e-6fae-43db-833e-9accecdd1c03
author: stevestein
ms.author: sstein
ms.openlocfilehash: 38b08452ef2680b654dd735b901488cb5f5f5f97
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719365"
---
# <a name="write-execution-trace-messages-to-the-sql-server-agent-error-log-sql-server-management-studio"></a><span data-ttu-id="a2f88-102">Write Execution Trace Messages to the SQL Server Agent Error Log (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="a2f88-102">Write Execution Trace Messages to the SQL Server Agent Error Log (SQL Server Management Studio)</span></span>
  <span data-ttu-id="a2f88-103">このトピックでは、を使用して、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のエラーログに実行トレースメッセージを含めるようにエージェントを構成する方法について説明し [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="a2f88-103">This topic describes how to configure [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to include execution trace messages in its error log in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="a2f88-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="a2f88-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="a2f88-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="a2f88-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="a2f88-106">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="a2f88-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="a2f88-107">Security</span><span class="sxs-lookup"><span data-stu-id="a2f88-107">Security</span></span>](#Security)  
  
-   [<span data-ttu-id="a2f88-108">SQL Server Management Studio を使用して SQL Server エージェント エラー ログに実行トレース メッセージを書き込むには</span><span class="sxs-lookup"><span data-stu-id="a2f88-108">To write execution trace messages to the SQL Server Agent Error Log using SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="a2f88-109">はじめに</span><span class="sxs-lookup"><span data-stu-id="a2f88-109">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="a2f88-110">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="a2f88-110">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="a2f88-111">オブジェクト エクスプローラーに [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ノードが表示されるのは、このノードの使用権限がある場合に限られます。</span><span class="sxs-lookup"><span data-stu-id="a2f88-111">Object Explorer only displays the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent node if you have permission to use it.</span></span>  
  
-   <span data-ttu-id="a2f88-112">このオプションを有効にするとエラー ログが大きくなるので、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に関する特定の問題を調査する場合にのみ、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのエラー ログに実行トレース メッセージを書き込むようにしてください。</span><span class="sxs-lookup"><span data-stu-id="a2f88-112">Because this option can cause the error log to become large, only include execution trace messages in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent error logs when investigating a specific [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent problem.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="a2f88-113">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="a2f88-113">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="a2f88-114">Permissions</span><span class="sxs-lookup"><span data-stu-id="a2f88-114">Permissions</span></span>  
 <span data-ttu-id="a2f88-115">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントの機能を実行するには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]固定サーバー ロールの **sysadmin** のメンバーであるアカウントの資格情報を使用するように構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a2f88-115">To perform its functions, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent must be configured to use the credentials of an account that is a member of the **sysadmin** fixed server role in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="a2f88-116">このアカウントには、次の Windows 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="a2f88-116">The account must have the following Windows permissions:</span></span>  
  
-   <span data-ttu-id="a2f88-117">サービスとしてログオン (SeServiceLogonRight)</span><span class="sxs-lookup"><span data-stu-id="a2f88-117">Log on as a service (SeServiceLogonRight)</span></span>  
  
-   <span data-ttu-id="a2f88-118">プロセス レベル トークンを置き換える (SeAssignPrimaryTokenPrivilege)</span><span class="sxs-lookup"><span data-stu-id="a2f88-118">Replace a process-level token (SeAssignPrimaryTokenPrivilege)</span></span>  
  
-   <span data-ttu-id="a2f88-119">スキャン チェックを行わない (SeChangeNotifyPrivilege)</span><span class="sxs-lookup"><span data-stu-id="a2f88-119">Bypass traverse checking (SeChangeNotifyPrivilege)</span></span>  
  
-   <span data-ttu-id="a2f88-120">プロセスに対してメモリ クォータを調整する (SeIncreaseQuotaPrivilege)</span><span class="sxs-lookup"><span data-stu-id="a2f88-120">Adjust memory quotas for a process (SeIncreaseQuotaPrivilege)</span></span>  
  
 <span data-ttu-id="a2f88-121">エージェントサービスアカウントに必要な Windows アクセス許可の詳細については [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、「 [SQL Server エージェントサービスのアカウントの選択](select-an-account-for-the-sql-server-agent-service.md)」および「 [Windows サービスアカウントとアクセス許可の構成](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a2f88-121">For more information about the Windows permissions required for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service account, see [Select an Account for the SQL Server Agent Service](select-an-account-for-the-sql-server-agent-service.md) and [Configure Windows Service Accounts and Permissions](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).</span></span>  
  
##  <a name="SSMSProcedure"></a>   
#### <a name="to-write-execution-trace-messages-to-the-sql-server-agent-error-log"></a><span data-ttu-id="a2f88-122">SQL Server エージェントのエラー ログに実行トレース メッセージを書き込むには</span><span class="sxs-lookup"><span data-stu-id="a2f88-122">To write execution trace messages to the SQL Server Agent error log</span></span>  
  
1.  <span data-ttu-id="a2f88-123">**オブジェクト エクスプローラー**で、プラス記号をクリックして、実行トレース メッセージの書き込み先となる [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのエラー ログを含むサーバーを展開します。</span><span class="sxs-lookup"><span data-stu-id="a2f88-123">In **Object Explorer**, click the plus sign to expand the server that contains the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent error log to which you want to write execution trace messages.</span></span>  
  
2.  <span data-ttu-id="a2f88-124">**[SQL Server エージェント]** を右クリックし、 **[プロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="a2f88-124">Right-click **SQL Server Agent** and select **Properties**.</span></span>  
  
3.  <span data-ttu-id="a2f88-125">[ **SQL Server エージェントのプロパティ-**_server_name_ ] ダイアログボックスの [**全般**] ページで、[**エラーログ**] の下にある [**実行トレースメッセージを含める**] チェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="a2f88-125">In the **SQL Server Agent Properties -**_server_name_ dialog box, under **Error log** on the **General** page, select the **Include execution trace messages** check box.</span></span>  
  
4.  <span data-ttu-id="a2f88-126">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a2f88-126">Click **OK**.</span></span>  
  
  
