---
title: SQL Server エージェントサービス (SQL Server Management Studio) の SQL Server 接続を設定します。Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, connections
- connections [SQL Server], SQL Server Agent service
ms.assetid: 28b6178b-0a9e-4f2c-8562-7a62d2d2a285
author: stevestein
ms.author: sstein
ms.openlocfilehash: 30f68967d6bdb8b0495cbddb1a5b0bd447cd5168
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645981"
---
# <a name="set-the-sql-server-connection-for-the-sql-server-agent-service-sql-server-management-studio"></a><span data-ttu-id="9b058-102">SQL Server エージェント サービスの SQL Server 接続の設定 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="9b058-102">Set the SQL Server Connection for the SQL Server Agent Service (SQL Server Management Studio)</span></span>
  <span data-ttu-id="9b058-103">このトピックでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で [!INCLUDE[ssDE](../../includes/ssde-md.md)] を使用して、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] エージェントと [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]間の接続を設定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9b058-103">This topic describes how to set the connection between [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent and the [!INCLUDE[ssDE](../../includes/ssde-md.md)] in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="9b058-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービスでは、Windows 認証を使用して、SQL Server のローカル インスタンスに接続できます。</span><span class="sxs-lookup"><span data-stu-id="9b058-104">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service can connect to a local instance of SQL Server by using Windows Authentication.</span></span>  
  
 <span data-ttu-id="9b058-105">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="9b058-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="9b058-106">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="9b058-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="9b058-107">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="9b058-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="9b058-108">Security</span><span class="sxs-lookup"><span data-stu-id="9b058-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="9b058-109">**SQL Server エージェントの SQL Server 接続を設定するために使用するもの:**</span><span class="sxs-lookup"><span data-stu-id="9b058-109">**To set the SQL Server Connection for the SQL Server Agent, using:**</span></span>  
  
     [<span data-ttu-id="9b058-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="9b058-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="9b058-111">はじめに</span><span class="sxs-lookup"><span data-stu-id="9b058-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="9b058-112">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="9b058-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="9b058-113">オブジェクト エクスプローラーに [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ノードが表示されるのは、このノードの使用権限がある場合に限られます。</span><span class="sxs-lookup"><span data-stu-id="9b058-113">Object Explorer only displays the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent node if you have permission to use it.</span></span>  
  
-   <span data-ttu-id="9b058-114">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]以降は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証がサポートされません。</span><span class="sxs-lookup"><span data-stu-id="9b058-114">Beginning with [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent does not support [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="9b058-115">このオプションは、以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を管理している場合にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="9b058-115">This option is available only when you administer an earlier version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="9b058-116">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="9b058-116">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="9b058-117">Permissions</span><span class="sxs-lookup"><span data-stu-id="9b058-117">Permissions</span></span>  
 <span data-ttu-id="9b058-118">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントの機能を実行するには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]固定サーバー ロールの **sysadmin** のメンバーであるアカウントの資格情報を使用するように構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9b058-118">To perform its functions, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent must be configured to use the credentials of an account that is a member of the **sysadmin** fixed server role in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="9b058-119">このアカウントには、次の Windows 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="9b058-119">The account must have the following Windows permissions:</span></span>  
  
-   <span data-ttu-id="9b058-120">サービスとしてログオン (SeServiceLogonRight)</span><span class="sxs-lookup"><span data-stu-id="9b058-120">Log on as a service (SeServiceLogonRight)</span></span>  
  
-   <span data-ttu-id="9b058-121">プロセス レベル トークンを置き換える (SeAssignPrimaryTokenPrivilege)</span><span class="sxs-lookup"><span data-stu-id="9b058-121">Replace a process-level token (SeAssignPrimaryTokenPrivilege)</span></span>  
  
-   <span data-ttu-id="9b058-122">スキャン チェックを行わない (SeChangeNotifyPrivilege)</span><span class="sxs-lookup"><span data-stu-id="9b058-122">Bypass traverse checking (SeChangeNotifyPrivilege)</span></span>  
  
-   <span data-ttu-id="9b058-123">プロセスに対してメモリ クォータを調整する (SeIncreaseQuotaPrivilege)</span><span class="sxs-lookup"><span data-stu-id="9b058-123">Adjust memory quotas for a process (SeIncreaseQuotaPrivilege)</span></span>  
  
 <span data-ttu-id="9b058-124">エージェントサービスアカウントに必要な Windows アクセス許可の詳細については [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、「 [SQL Server エージェントサービスのアカウントの選択](select-an-account-for-the-sql-server-agent-service.md)」および「 [Windows サービスアカウントとアクセス許可の構成](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9b058-124">For more information about the Windows permissions required for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service account, see [Select an Account for the SQL Server Agent Service](select-an-account-for-the-sql-server-agent-service.md) and [Configure Windows Service Accounts and Permissions](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="9b058-125">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="9b058-125">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-set-the-sql-server-connection"></a><span data-ttu-id="9b058-126">SQL Server の接続を設定するには</span><span class="sxs-lookup"><span data-stu-id="9b058-126">To set the SQL Server connection</span></span>  
  
1.  <span data-ttu-id="9b058-127">**オブジェクト エクスプローラー**で、SQL Server エージェント サービスへの接続を設定するサーバーをプラス記号をクリックして展開します。</span><span class="sxs-lookup"><span data-stu-id="9b058-127">In **Object Explorer**, click the plus sign to expand the server that you want to set up with a connection to its SQL Server Agent Service.</span></span>  
  
2.  <span data-ttu-id="9b058-128">**[SQL Server エージェント]** を右クリックし、 **[プロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="9b058-128">Right-click **SQL Server Agent** and select **Properties**.</span></span>  
  
3.  <span data-ttu-id="9b058-129">**[SQL Server エージェントのプロパティ]** ダイアログ ボックスの **[ページの選択]** で **[接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9b058-129">In the **SQL Server Agent Properties** dialog box, under **Select a page**, click **Connection**.</span></span>  
  
4.  <span data-ttu-id="9b058-130">**[SQL Server 接続]** で、**[Windows 認証を使用する]** を選択して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントが  Windows 認証を使用して [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンスに接続できるようにします。</span><span class="sxs-lookup"><span data-stu-id="9b058-130">Under **SQL Server connection**, select **Use Windows Authentication** to enable [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to connect to an instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] with [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Authentication.</span></span> <span data-ttu-id="9b058-131">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降のデータベースへの接続には Windows 認証が必要です。</span><span class="sxs-lookup"><span data-stu-id="9b058-131">Connections to [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later databases require Windows Authentication.</span></span>  
  
  
