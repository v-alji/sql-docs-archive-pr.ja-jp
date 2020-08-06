---
title: SQL Server エージェントの自動起動 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, starting
- autostart SQL Server Agent
ms.assetid: 2ea332da-0ede-4d2b-b122-c4c10eaca191
author: stevestein
ms.author: sstein
ms.openlocfilehash: a39c7c7a112370797a965cfa601bc07f983a7a37
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642505"
---
# <a name="autostart-sql-server-agent-sql-server-management-studio"></a><span data-ttu-id="56d51-102">Autostart SQL Server Agent (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="56d51-102">Autostart SQL Server Agent (SQL Server Management Studio)</span></span>
  <span data-ttu-id="56d51-103">このトピックでは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で予期せず停止した場合にエージェントが自動的に再起動するように構成する方法について説明し [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="56d51-103">This topic describes how to configure [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to automatically restart if it should stop unexpectedly in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
 <span data-ttu-id="56d51-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="56d51-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="56d51-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="56d51-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="56d51-106">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="56d51-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="56d51-107">Security</span><span class="sxs-lookup"><span data-stu-id="56d51-107">Security</span></span>](#Security)  
  
-   [<span data-ttu-id="56d51-108">SQL Server Management Studio を使用して、自動的に再起動するように SQL Server エージェントを構成するには</span><span class="sxs-lookup"><span data-stu-id="56d51-108">To configure SQL Server Agent to automatically restart, using SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="56d51-109">はじめに</span><span class="sxs-lookup"><span data-stu-id="56d51-109">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="56d51-110">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="56d51-110">Limitations and Restrictions</span></span>  
 <span data-ttu-id="56d51-111">オブジェクト エクスプローラーに [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ノードが表示されるのは、このノードの使用権限がある場合に限られます。</span><span class="sxs-lookup"><span data-stu-id="56d51-111">Object Explorer only displays the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent node if you have permission to use it.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="56d51-112">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="56d51-112">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="56d51-113">Permissions</span><span class="sxs-lookup"><span data-stu-id="56d51-113">Permissions</span></span>  
 <span data-ttu-id="56d51-114">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントの機能を実行するには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]固定サーバー ロールの **sysadmin** のメンバーであるアカウントの資格情報を使用するように構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="56d51-114">To perform its functions, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent must be configured to use the credentials of an account that is a member of the **sysadmin** fixed server role in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="56d51-115">このアカウントには、次の Windows 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="56d51-115">The account must have the following Windows permissions:</span></span>  
  
-   <span data-ttu-id="56d51-116">サービスとしてログオン (SeServiceLogonRight)</span><span class="sxs-lookup"><span data-stu-id="56d51-116">Log on as a service (SeServiceLogonRight)</span></span>  
  
-   <span data-ttu-id="56d51-117">プロセス レベル トークンを置き換える (SeAssignPrimaryTokenPrivilege)</span><span class="sxs-lookup"><span data-stu-id="56d51-117">Replace a process-level token (SeAssignPrimaryTokenPrivilege)</span></span>  
  
-   <span data-ttu-id="56d51-118">スキャン チェックを行わない (SeChangeNotifyPrivilege)</span><span class="sxs-lookup"><span data-stu-id="56d51-118">Bypass traverse checking (SeChangeNotifyPrivilege)</span></span>  
  
-   <span data-ttu-id="56d51-119">プロセスに対してメモリ クォータを調整する (SeIncreaseQuotaPrivilege)</span><span class="sxs-lookup"><span data-stu-id="56d51-119">Adjust memory quotas for a process (SeIncreaseQuotaPrivilege)</span></span>  
  
 <span data-ttu-id="56d51-120">エージェントサービスアカウントに必要な Windows アクセス許可の詳細については [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、「 [SQL Server エージェントサービスのアカウントの選択](select-an-account-for-the-sql-server-agent-service.md)」および「 [Windows サービスアカウントとアクセス許可の構成](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="56d51-120">For more information about the Windows permissions required for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service account, see [Select an Account for the SQL Server Agent Service](select-an-account-for-the-sql-server-agent-service.md) and [Configure Windows Service Accounts and Permissions](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="56d51-121">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="56d51-121">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-sql-server-agent-to-automatically-restart"></a><span data-ttu-id="56d51-122">自動的に再起動するように SQL Server エージェントを構成するには</span><span class="sxs-lookup"><span data-stu-id="56d51-122">To configure SQL Server Agent to automatically restart</span></span>  
  
1.  <span data-ttu-id="56d51-123">**オブジェクト エクスプ ローラー**で、プラス記号をクリックして、自動的に再起動するように構成する SQL Server エージェントを展開します。</span><span class="sxs-lookup"><span data-stu-id="56d51-123">In **Object Explorer**, click the plus sign to expand the server where you want to configure SQL Server Agent to automatically restart.</span></span>  
  
2.  <span data-ttu-id="56d51-124">**[SQL Server エージェント]** を右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="56d51-124">Right-click **SQL Server Agent**, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="56d51-125">**[全般]** ページで、 **[予期しない停止時に SQL Server エージェントを自動的に再起動する]** をオンにします。</span><span class="sxs-lookup"><span data-stu-id="56d51-125">On the **General** page, check **Auto restart SQL Server Agent if it stops unexpectedly**.</span></span>  
  
  
