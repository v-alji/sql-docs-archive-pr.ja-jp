---
title: SQL Server エージェントのエラー ログの名前の変更 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- logs [SQL Server], SQL Server Agent
- renaming SQL Server Agent error log
- SQL Server Agent, errors
- errors [SQL Server Agent]
ms.assetid: dee2b199-48af-44cb-9177-d029a5edb169
author: stevestein
ms.author: sstein
ms.openlocfilehash: c1c85550a29bfff316ffc275ba2d4e4df10686d7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645310"
---
# <a name="rename-a-sql-server-agent-error-log-sql-server-management-studio"></a><span data-ttu-id="eea96-102">Rename a SQL Server Agent Error Log (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="eea96-102">Rename a SQL Server Agent Error Log (SQL Server Management Studio)</span></span>
  <span data-ttu-id="eea96-103">このトピックでは、を使用して、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントエラーが書き込まれるファイルの名前を変更する方法について説明し [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="eea96-103">This topic describes how to rename the file where [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent errors are written in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="eea96-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="eea96-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="eea96-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="eea96-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="eea96-106">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="eea96-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="eea96-107">Security</span><span class="sxs-lookup"><span data-stu-id="eea96-107">Security</span></span>](#Security)  
  
-   [<span data-ttu-id="eea96-108">SQL Server Management Studio を使用して SQL Server エージェントのエラー ログの名前を変更する方法</span><span class="sxs-lookup"><span data-stu-id="eea96-108">To rename a SQL Server Agent error log using SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="eea96-109">はじめに</span><span class="sxs-lookup"><span data-stu-id="eea96-109">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="eea96-110">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="eea96-110">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="eea96-111">オブジェクト エクスプローラーに [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ノードが表示されるのは、このノードの使用権限がある場合に限られます。</span><span class="sxs-lookup"><span data-stu-id="eea96-111">Object Explorer only displays the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent node if you have permission to use it.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="eea96-112">エージェント サービスを再開しないと、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントから新しいログ ファイルに書き込まれません。</span><span class="sxs-lookup"><span data-stu-id="eea96-112">Agent will not write to the new log file until the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service is restarted.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="eea96-113">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="eea96-113">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="eea96-114">Permissions</span><span class="sxs-lookup"><span data-stu-id="eea96-114">Permissions</span></span>  
 <span data-ttu-id="eea96-115">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントの機能を実行するには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]固定サーバー ロールの **sysadmin** のメンバーであるアカウントの資格情報を使用するように構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="eea96-115">To perform its functions, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent must be configured to use the credentials of an account that is a member of the **sysadmin** fixed server role in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="eea96-116">このアカウントには、次の Windows 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="eea96-116">The account must have the following Windows permissions:</span></span>  
  
-   <span data-ttu-id="eea96-117">サービスとしてログオン (SeServiceLogonRight)</span><span class="sxs-lookup"><span data-stu-id="eea96-117">Log on as a service (SeServiceLogonRight)</span></span>  
  
-   <span data-ttu-id="eea96-118">プロセス レベル トークンを置き換える (SeAssignPrimaryTokenPrivilege)</span><span class="sxs-lookup"><span data-stu-id="eea96-118">Replace a process-level token (SeAssignPrimaryTokenPrivilege)</span></span>  
  
-   <span data-ttu-id="eea96-119">スキャン チェックを行わない (SeChangeNotifyPrivilege)</span><span class="sxs-lookup"><span data-stu-id="eea96-119">Bypass traverse checking (SeChangeNotifyPrivilege)</span></span>  
  
-   <span data-ttu-id="eea96-120">プロセスに対してメモリ クォータを調整する (SeIncreaseQuotaPrivilege)</span><span class="sxs-lookup"><span data-stu-id="eea96-120">Adjust memory quotas for a process (SeIncreaseQuotaPrivilege)</span></span>  
  
 <span data-ttu-id="eea96-121">エージェントサービスアカウントに必要な Windows アクセス許可の詳細については [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、「 [SQL Server エージェントサービスのアカウントの選択](select-an-account-for-the-sql-server-agent-service.md)」および「 [Windows サービスアカウントとアクセス許可の構成](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eea96-121">For more information about the Windows permissions required for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service account, see [Select an Account for the SQL Server Agent Service](select-an-account-for-the-sql-server-agent-service.md) and [Configure Windows Service Accounts and Permissions](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="eea96-122">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="eea96-122">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-rename-a-sql-server-agent-error-log"></a><span data-ttu-id="eea96-123">SQL Server エージェント エラー ログの名前を変更するには</span><span class="sxs-lookup"><span data-stu-id="eea96-123">To rename a SQL Server Agent error log</span></span>  
  
1.  <span data-ttu-id="eea96-124">**オブジェクト エクスプローラー**で、名前を変更する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント エラー ログを含むサーバーをプラス記号をクリックして展開します。</span><span class="sxs-lookup"><span data-stu-id="eea96-124">In **Object Explorer**, click the plus sign to expand the server that contains the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent error log that you want to rename.</span></span>  
  
2.  <span data-ttu-id="eea96-125">プラス記号をクリックして **[SQL Server エージェント]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="eea96-125">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="eea96-126">**[エラー ログ]** フォルダーを右クリックし、 **[構成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eea96-126">Right-click the **Error Logs** folder and select **Configure**.</span></span>  
  
4.  <span data-ttu-id="eea96-127">**[SQL Server エージェント エラー ログの構成]** ダイアログ ボックスの **[エラー ログ ファイル]** ボックスに、エラー ログの新しいファイル パスとファイル名を入力します。</span><span class="sxs-lookup"><span data-stu-id="eea96-127">In the **Configure SQL Server Agent Error Logs** dialog box, in the **Error log file** box, enter the new file path and file name for the error log.</span></span> <span data-ttu-id="eea96-128">または、省略記号ボタン ( **[...]** ) をクリックして **[エージェント エラー ログの場所の指定]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="eea96-128">Alternately, click the ellipsis **(...)** to open the **Specify agent error log location** dialog box.</span></span>  
  
5.  <span data-ttu-id="eea96-129">完了したら、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eea96-129">When finished, click **OK**.</span></span>  
  
  
