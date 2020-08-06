---
title: ログ ファイルの表示 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- Log File Viewer
ms.assetid: a4ea7fc8-1cb2-4c98-bc86-8991c5e748b2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5139a32838070b817fce3bccf22b9fe08b5012e2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639500"
---
# <a name="log-file-viewer"></a><span data-ttu-id="e2442-102">ログ ファイルの表示</span><span class="sxs-lookup"><span data-stu-id="e2442-102">Log File Viewer</span></span>
  <span data-ttu-id="e2442-103">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] の [ログ ファイルの表示] を使用して、ログ ファイルに記録されたエラーおよびイベントに関する情報にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="e2442-103">Log File Viewer in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] is used to access information about errors and events that are captured in log files.</span></span>  
  
## <a name="benefits-of-using-log-file-viewer"></a><span data-ttu-id="e2442-104">[ログ ファイルの表示] を使用する利点</span><span class="sxs-lookup"><span data-stu-id="e2442-104">Benefits of using Log File Viewer</span></span>  
 <span data-ttu-id="e2442-105">対象となるインスタンスがオフラインの場合または開始できない場合に、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログ ファイルを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のローカルまたはリモート インスタンスから表示できます。</span><span class="sxs-lookup"><span data-stu-id="e2442-105">You can view [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] log files from a local or remote instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] when the target instance is offline or cannot start.</span></span> <span data-ttu-id="e2442-106">登録済みサーバーから、またはプログラムにより WMI および WQL (WMI Query Language) クエリを通じて、オフラインのログ ファイルにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="e2442-106">You can access the offline log files from Registered Servers, or programmatically through WMI and WQL (WMI Query Language) queries.</span></span> <span data-ttu-id="e2442-107">詳細については、「 [オフライン ログ ファイルの表示](view-offline-log-files.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e2442-107">For more information, see [View Offline Log Files](view-offline-log-files.md).</span></span> <span data-ttu-id="e2442-108">[ログ ファイルの表示] を使用してアクセスできるログ ファイルの種類は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="e2442-108">Following are the types of log files you can access using Log File Viewer:</span></span>  
  
-   <span data-ttu-id="e2442-109">監査コレクション</span><span class="sxs-lookup"><span data-stu-id="e2442-109">Audit Collection</span></span>  
  
-   <span data-ttu-id="e2442-110">データ収集</span><span class="sxs-lookup"><span data-stu-id="e2442-110">Data Collection</span></span>  
  
-   <span data-ttu-id="e2442-111">データベース メール</span><span class="sxs-lookup"><span data-stu-id="e2442-111">Database Mail</span></span>  
  
-   <span data-ttu-id="e2442-112">ジョブ履歴</span><span class="sxs-lookup"><span data-stu-id="e2442-112">Job History</span></span>  
  
-   <span data-ttu-id="e2442-113">メンテナンス プラン</span><span class="sxs-lookup"><span data-stu-id="e2442-113">Maintenance Plans</span></span>  
  
-   <span data-ttu-id="e2442-114">リモート メンテナンス プラン</span><span class="sxs-lookup"><span data-stu-id="e2442-114">Remote Maintenance Plans</span></span>  
  
-   <span data-ttu-id="e2442-115">SQL Server</span><span class="sxs-lookup"><span data-stu-id="e2442-115">SQL Server</span></span>  
  
-   <span data-ttu-id="e2442-116">SQL Server エージェント</span><span class="sxs-lookup"><span data-stu-id="e2442-116">SQL Server Agent</span></span>  
  
-   <span data-ttu-id="e2442-117">Windows NT (イベント ビューアーからアクセスできる Windows イベントもあります)</span><span class="sxs-lookup"><span data-stu-id="e2442-117">Windows NT (These are Windows events that can also be accessed from Event Viewer.)</span></span>  
  
## <a name="log-file-viewer-tasks"></a><span data-ttu-id="e2442-118">[ログ ファイルの表示] のタスク</span><span class="sxs-lookup"><span data-stu-id="e2442-118">Log File Viewer Tasks</span></span>  
  
|<span data-ttu-id="e2442-119">タスクの説明</span><span class="sxs-lookup"><span data-stu-id="e2442-119">Task Description</span></span>|<span data-ttu-id="e2442-120">トピック</span><span class="sxs-lookup"><span data-stu-id="e2442-120">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="e2442-121">表示する情報に応じていくつかの方法で [ログ ファイルの表示] を開く方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e2442-121">Describes how to open Log File Viewer depending on the information that you want to view.</span></span>|<span data-ttu-id="e2442-122">[[ログ ファイルの表示] を開く](open-log-file-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="e2442-122">[Open Log File Viewer](open-log-file-viewer.md)</span></span>|  
|<span data-ttu-id="e2442-123">登録済みサーバーを通じてオフラインのログ ファイルを表示する方法と、WMI 権限を確認する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e2442-123">Describes how to view offline log files through registered servers and how to verify WMI permissions.</span></span>|[<span data-ttu-id="e2442-124">オフライン ログ ファイルの表示</span><span class="sxs-lookup"><span data-stu-id="e2442-124">View Offline Log Files</span></span>](view-offline-log-files.md)|  
|<span data-ttu-id="e2442-125">[ログ ファイルの表示] の F1 ヘルプを提供します。</span><span class="sxs-lookup"><span data-stu-id="e2442-125">Provides Log File Viewer F1 Help.</span></span>|<span data-ttu-id="e2442-126">[[ログ ファイルの表示] の F1 ヘルプ](log-file-viewer-f1-help.md)</span><span class="sxs-lookup"><span data-stu-id="e2442-126">[Log File Viewer F1 Help](log-file-viewer-f1-help.md)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e2442-127">参照</span><span class="sxs-lookup"><span data-stu-id="e2442-127">See Also</span></span>  
 <span data-ttu-id="e2442-128">[SQL Server Audit &#40;データベース エンジン&#41;](../security/auditing/sql-server-audit-database-engine.md) </span><span class="sxs-lookup"><span data-stu-id="e2442-128">[SQL Server Audit &#40;Database Engine&#41;](../security/auditing/sql-server-audit-database-engine.md) </span></span>  
 [<span data-ttu-id="e2442-129">SQL Server エージェント エラー ログ</span><span class="sxs-lookup"><span data-stu-id="e2442-129">SQL Server Agent Error Log</span></span>](../../ssms/agent/sql-server-agent-error-log.md)  
  
  
