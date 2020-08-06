---
title: SQL Server エージェントのエラー メッセージの送信 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- messages [SQL Server], SQL Server Agent
- sending messages
- SQL Server Agent, errors
- errors [SQL Server Agent]
ms.assetid: 2597d0d7-951a-48cf-989f-abb67b9fdb36
author: stevestein
ms.author: sstein
ms.openlocfilehash: 03e38b02188eaced65a86b22ed4f22cb6984ce0e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642497"
---
# <a name="send-sql-server-agent-error-messages"></a><span data-ttu-id="4493b-102">Send SQL Server Agent Error Messages</span><span class="sxs-lookup"><span data-stu-id="4493b-102">Send SQL Server Agent Error Messages</span></span>
  <span data-ttu-id="4493b-103">このトピックでは、を使用して、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で net send を使用してエラーメッセージを送信するようにエージェントを構成する方法について説明し [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="4493b-103">This topic describes how to how to configure [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to send its error messages by way of net send in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="4493b-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="4493b-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="4493b-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="4493b-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="4493b-106">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="4493b-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="4493b-107">Security</span><span class="sxs-lookup"><span data-stu-id="4493b-107">Security</span></span>](#Security)  
  
-   [<span data-ttu-id="4493b-108">SQL Server Management Studio を使用して SQL Server エージェントのエラー メッセージを送信するには</span><span class="sxs-lookup"><span data-stu-id="4493b-108">To send SQL Server Agent error messages using SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="4493b-109">はじめに</span><span class="sxs-lookup"><span data-stu-id="4493b-109">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="4493b-110">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="4493b-110">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="4493b-111">オブジェクト エクスプローラーに [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ノードが表示されるのは、このノードの使用権限がある場合に限られます。</span><span class="sxs-lookup"><span data-stu-id="4493b-111">Object Explorer only displays the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent node if you have permission to use it.</span></span>  
  
-   <span data-ttu-id="4493b-112">net send イベントを受信するには、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Messenger サービスを実行している必要があります。</span><span class="sxs-lookup"><span data-stu-id="4493b-112">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Messenger service must be running to receive net send events.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="4493b-113">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="4493b-113">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="4493b-114">Permissions</span><span class="sxs-lookup"><span data-stu-id="4493b-114">Permissions</span></span>  
 <span data-ttu-id="4493b-115">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントの機能を実行するには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]固定サーバー ロールの **sysadmin** のメンバーであるアカウントの資格情報を使用するように構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4493b-115">To perform its functions, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent must be configured to use the credentials of an account that is a member of the **sysadmin** fixed server role in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="4493b-116">このアカウントには、次の Windows 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="4493b-116">The account must have the following Windows permissions:</span></span>  
  
-   <span data-ttu-id="4493b-117">サービスとしてログオン (SeServiceLogonRight)</span><span class="sxs-lookup"><span data-stu-id="4493b-117">Log on as a service (SeServiceLogonRight)</span></span>  
  
-   <span data-ttu-id="4493b-118">プロセス レベル トークンを置き換える (SeAssignPrimaryTokenPrivilege)</span><span class="sxs-lookup"><span data-stu-id="4493b-118">Replace a process-level token (SeAssignPrimaryTokenPrivilege)</span></span>  
  
-   <span data-ttu-id="4493b-119">スキャン チェックを行わない (SeChangeNotifyPrivilege)</span><span class="sxs-lookup"><span data-stu-id="4493b-119">Bypass traverse checking (SeChangeNotifyPrivilege)</span></span>  
  
-   <span data-ttu-id="4493b-120">プロセスに対してメモリ クォータを調整する (SeIncreaseQuotaPrivilege)</span><span class="sxs-lookup"><span data-stu-id="4493b-120">Adjust memory quotas for a process (SeIncreaseQuotaPrivilege)</span></span>  
  
 <span data-ttu-id="4493b-121">エージェントサービスアカウントに必要な Windows アクセス許可の詳細については [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、「 [SQL Server エージェントサービスのアカウントの選択](select-an-account-for-the-sql-server-agent-service.md)」および「 [Windows サービスアカウントとアクセス許可の構成](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4493b-121">For more information about the Windows permissions required for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service account, see [Select an Account for the SQL Server Agent Service](select-an-account-for-the-sql-server-agent-service.md) and [Configure Windows Service Accounts and Permissions](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="4493b-122">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="4493b-122">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-send-sql-server-agent-error-messages"></a><span data-ttu-id="4493b-123">SQL Server エージェントのエラー メッセージを送信するには</span><span class="sxs-lookup"><span data-stu-id="4493b-123">To send SQL Server Agent error messages</span></span>  
  
1.  <span data-ttu-id="4493b-124">**オブジェクト エクスプローラー**で、プラス記号をクリックして、net send によるエラー メッセージの送信元となる [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのエラー ログを含むサーバーを展開します。</span><span class="sxs-lookup"><span data-stu-id="4493b-124">In **Object Explorer**, click the plus sign to expand the server that contains the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent error log from which you want to send error messages via net send.</span></span>  
  
2.  <span data-ttu-id="4493b-125">**[SQL Server エージェント]** を右クリックし、 **[プロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="4493b-125">Right-click **SQL Server Agent** and select **Properties**.</span></span>  
  
3.  <span data-ttu-id="4493b-126">[ **SQL Server エージェントのプロパティ-**_server_name_ ] ダイアログボックスの [**全般**] ページで、[**エラーログ**] の下の [ **Net send 受信者**] ボックスに、エラーメッセージの送信先となるユーザー名またはコンピューター名を入力します。</span><span class="sxs-lookup"><span data-stu-id="4493b-126">In the **SQL Server Agent Properties -**_server_name_ dialog box, under **Error log** on the **General** page, , type the user name or computer name to which you want to send error messages in the **Net send recipient** box.</span></span>  
  
4.  <span data-ttu-id="4493b-127">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4493b-127">Click **OK**.</span></span>  
  
  
