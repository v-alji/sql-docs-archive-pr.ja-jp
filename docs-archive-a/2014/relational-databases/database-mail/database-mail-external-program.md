---
title: データベース メール外部プログラム | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- external programs [Database Mail]
- DatabaseMail90.exe
- Database Mail [SQL Server], external programs
ms.assetid: bc124164-eb6e-4b7f-bf66-98a3113d02f7
author: stevestein
ms.author: sstein
ms.openlocfilehash: 698fc8d97a565b4181552691a0260486c9c43bfd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742269"
---
# <a name="database-mail-external-program"></a><span data-ttu-id="0ffd6-102">データベース メール外部プログラム</span><span class="sxs-lookup"><span data-stu-id="0ffd6-102">Database Mail External Program</span></span>
  <span data-ttu-id="0ffd6-103">データベース メール外部実行可能ファイルは **DatabaseMail.exe**です。このファイルは、 **インストール環境の** MSSQL\Binn ディレクトリ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] にあります。</span><span class="sxs-lookup"><span data-stu-id="0ffd6-103">The Database Mail external executable is **DatabaseMail.exe**, located in the **MSSQL\Binn directory** of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation.</span></span> <span data-ttu-id="0ffd6-104">データベース メールでは、処理する電子メール メッセージがあるときに、Service Broker のアクティブ化を使用して外部プログラムが起動されます。</span><span class="sxs-lookup"><span data-stu-id="0ffd6-104">Database Mail uses Service Broker activation to start the external program when there are e-mail messages to be processed.</span></span> <span data-ttu-id="0ffd6-105">次に、データベース メールによって外部プログラムの 1 つのインスタンスが開始されます。</span><span class="sxs-lookup"><span data-stu-id="0ffd6-105">Database Mail starts one instance of the external program.</span></span> <span data-ttu-id="0ffd6-106">外部プログラムは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のサービス アカウントのセキュリティ コンテキストで実行されます。</span><span class="sxs-lookup"><span data-stu-id="0ffd6-106">The external program runs in the security context of the service account for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="0ffd6-107">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="0ffd6-107">**In this Topic:**</span></span>  
  
-   [<span data-ttu-id="0ffd6-108">データベース メール外部プログラムの概念</span><span class="sxs-lookup"><span data-stu-id="0ffd6-108">Database Mail External Program Concepts</span></span>](#ComponentsAndConcepts)  
  
-   [<span data-ttu-id="0ffd6-109">データベース メール外部プログラムの構成に関連するタスク</span><span class="sxs-lookup"><span data-stu-id="0ffd6-109">Tasks Related to Configuring Database Mail External Program</span></span>](#RelatedTasks)  
  
##  <a name="database-mail-external-program-concepts"></a><a name="ComponentsAndConcepts"></a> <span data-ttu-id="0ffd6-110">データベース メール外部プログラムの概念</span><span class="sxs-lookup"><span data-stu-id="0ffd6-110">Database Mail External Program Concepts</span></span>  
 <span data-ttu-id="0ffd6-111">外部プログラムが開始されるときに、プログラムによって Windows 認証を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] への接続が行われ、電子メール メッセージの処理が開始されます。</span><span class="sxs-lookup"><span data-stu-id="0ffd6-111">When the external program starts, the program connects to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using Windows Authentication and begins processing e-mail messages.</span></span> <span data-ttu-id="0ffd6-112">指定されたタイムアウト期間内に送信するメッセージがなくなると、プログラムが終了します。</span><span class="sxs-lookup"><span data-stu-id="0ffd6-112">When there have been no messages to send for the specified time-out period, the program exits.</span></span> <span data-ttu-id="0ffd6-113">データベース メール構成ウィザードまたはデータベース メール ストアド プロシージャのいずれかを使用して、プログラムが終了するまでの時間を構成できます。</span><span class="sxs-lookup"><span data-stu-id="0ffd6-113">You can configure the amount of time that the program waits before exiting by using either Database Mail Configuration Wizard or the Database Mail stored procedures.</span></span> <span data-ttu-id="0ffd6-114">詳細については、「 [sysmail_configure_sp &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sysmail-configure-sp-transact-sql)のサービス アカウントのセキュリティ コンテキストで実行されます。</span><span class="sxs-lookup"><span data-stu-id="0ffd6-114">For more information, see [sysmail_configure_sp &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sysmail-configure-sp-transact-sql).</span></span>  
  
 <span data-ttu-id="0ffd6-115">外部プログラムは、 **msdb** データベースのシステム テーブルに情報を保存します。</span><span class="sxs-lookup"><span data-stu-id="0ffd6-115">The external program stores information in system tables in the **msdb** database.</span></span> <span data-ttu-id="0ffd6-116">外部プログラムが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]と通信できない場合は、プログラムによって、Microsoft Windows アプリケーション イベント ログにエラーが記録されます。</span><span class="sxs-lookup"><span data-stu-id="0ffd6-116">If the external program cannot communicate with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the program logs errors to the Microsoft Windows application event log.</span></span> <span data-ttu-id="0ffd6-117">**データベース メール構成ウィザード** の **[システム パラメーターの構成]** ダイアログ ボックスでログのレベルを **[詳細]** に設定している場合、詳細なメッセージ ログが記録されます。</span><span class="sxs-lookup"><span data-stu-id="0ffd6-117">Additional message logging is provided when the logging level is set to **Verbose** in the **Configure System Parameters** dialog box of the **Database Mail Configuration Wizard**.</span></span>  
  
 <span data-ttu-id="0ffd6-118">外部プログラムでは、効率を上げるために、アカウントやプロファイルに関する情報がキャッシュされることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="0ffd6-118">Notice that, for efficiency, the external program caches account and profile information.</span></span> <span data-ttu-id="0ffd6-119">そのため、アカウントやプロファイルの構成を変更しても、その変更が数分間、外部プログラムに反映されないことがあります。</span><span class="sxs-lookup"><span data-stu-id="0ffd6-119">Therefore, configuration changes to accounts and profiles may not be reflected in the external program for a few minutes.</span></span>  
  
##  <a name="tasks-related-to-configuring-database-mail-external-program"></a><a name="RelatedTasks"></a> <span data-ttu-id="0ffd6-120">データベース メール外部プログラムの構成に関連するタスク</span><span class="sxs-lookup"><span data-stu-id="0ffd6-120">Tasks Related to Configuring Database Mail External Program</span></span>  
  
|<span data-ttu-id="0ffd6-121">構成タスク</span><span class="sxs-lookup"><span data-stu-id="0ffd6-121">Configuration Task</span></span>|<span data-ttu-id="0ffd6-122">トピック</span><span class="sxs-lookup"><span data-stu-id="0ffd6-122">Topic Link</span></span>|  
|------------------------|----------------|  
|<span data-ttu-id="0ffd6-123">外部プログラムが終了するまでの時間を指定します。</span><span class="sxs-lookup"><span data-stu-id="0ffd6-123">Specify the time that the External Program before exiting.</span></span>|[<span data-ttu-id="0ffd6-124">sysmail_configure_sp &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="0ffd6-124">sysmail_configure_sp &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sysmail-configure-sp-transact-sql)|  
  
## <a name="see-also"></a><span data-ttu-id="0ffd6-125">参照</span><span class="sxs-lookup"><span data-stu-id="0ffd6-125">See Also</span></span>  
 <span data-ttu-id="0ffd6-126">[SQL Server Service Broker (SQL Server Service Broker)](../../database-engine/configure-windows/sql-server-service-broker.md) </span><span class="sxs-lookup"><span data-stu-id="0ffd6-126">[SQL Server Service Broker](../../database-engine/configure-windows/sql-server-service-broker.md) </span></span>  
 <span data-ttu-id="0ffd6-127">[データベース メールのログ記録と監査](database-mail-log-and-audits.md) </span><span class="sxs-lookup"><span data-stu-id="0ffd6-127">[Database Mail Log and Audits](database-mail-log-and-audits.md) </span></span>  
 [<span data-ttu-id="0ffd6-128">データベース メール</span><span class="sxs-lookup"><span data-stu-id="0ffd6-128">Database Mail</span></span>](database-mail.md)  
  
  
