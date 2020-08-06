---
title: '[ログ配布モニターの設定] | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.databaseproperties.logshipping.settings.monitor.f1
ms.assetid: 45e2ba7d-b3aa-4643-9451-bcb991572314
author: stevestein
ms.author: sstein
ms.openlocfilehash: 162fdc1b8b0ef850a7e58d1380c533426e16539c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742185"
---
# <a name="log-shipping-monitor-settings"></a><span data-ttu-id="0abb8-102">[ログ配布モニターの設定]</span><span class="sxs-lookup"><span data-stu-id="0abb8-102">Log Shipping Monitor Settings</span></span>
  <span data-ttu-id="0abb8-103">このページを使用すると、ログ配布監視サーバーのプロパティを構成および変更できます。</span><span class="sxs-lookup"><span data-stu-id="0abb8-103">Use this page to configure and to modify the properties of the log shipping monitor server.</span></span>  
  
 <span data-ttu-id="0abb8-104">ログ配布の概念については、「 [ログ配布について &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0abb8-104">For an explanation of log shipping concepts, see [About Log Shipping &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="0abb8-105">オプション</span><span class="sxs-lookup"><span data-stu-id="0abb8-105">Options</span></span>  
 <span data-ttu-id="0abb8-106">**[監視サーバー インスタンス]**</span><span class="sxs-lookup"><span data-stu-id="0abb8-106">**Monitor server instance**</span></span>  
 <span data-ttu-id="0abb8-107">ログ配布構成の監視サーバーとして現在構成されているサーバー インスタンスの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="0abb8-107">Displays the name of the server instance that is currently configured as the monitor server for the log shipping configuration.</span></span>  
  
 <span data-ttu-id="0abb8-108">**のインスタンスに接続するときには、**</span><span class="sxs-lookup"><span data-stu-id="0abb8-108">**Connect**</span></span>  
 <span data-ttu-id="0abb8-109">監視サーバーとして使用する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスを選択して接続します。</span><span class="sxs-lookup"><span data-stu-id="0abb8-109">Choose and connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to be used as the monitor server.</span></span> <span data-ttu-id="0abb8-110">接続に使用するアカウントは、セカンダリ サーバーのインスタンスの sysadmin 固定サーバー ロールのメンバーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="0abb8-110">The account used to connect must be a member of the sysadmin fixed server role on the secondary server instance.</span></span>  
  
 <span data-ttu-id="0abb8-111">**[ジョブのプロキシ アカウントを借用する]**</span><span class="sxs-lookup"><span data-stu-id="0abb8-111">**By impersonating the proxy account of the job**</span></span>  
 <span data-ttu-id="0abb8-112">監視サーバー インスタンスに接続するときに、ログ配布で SQL Server エージェントのプロキシ アカウントを借用します。</span><span class="sxs-lookup"><span data-stu-id="0abb8-112">Have log shipping impersonate the SQL Server Agent proxy account when connecting to the monitor server instance.</span></span> <span data-ttu-id="0abb8-113">バックアップ、コピー、および復元プロセスでは、監視サーバーに接続してログ配布操作の状態を更新できなければなりません。</span><span class="sxs-lookup"><span data-stu-id="0abb8-113">The backup, copy, and restore processes must be able to connect to the monitor server to update the status of log shipping operations.</span></span>  
  
 <span data-ttu-id="0abb8-114">**[次の SQL Server ログインを使用する]**</span><span class="sxs-lookup"><span data-stu-id="0abb8-114">**Using the following SQL Server login**</span></span>  
 <span data-ttu-id="0abb8-115">監視サーバー インスタンスに接続するときに、ログ配布で特定の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインを使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="0abb8-115">Allow log shipping to use a specific [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login when connecting to the monitor server instance.</span></span> <span data-ttu-id="0abb8-116">バックアップ、コピー、および復元プロセスでは、監視サーバーに接続してログ配布操作の状態を更新できなければなりません。</span><span class="sxs-lookup"><span data-stu-id="0abb8-116">The backup, copy, and restore processes must be able to connect to the monitor server to update the status of log shipping operations.</span></span> <span data-ttu-id="0abb8-117">ログ配布で特定の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインを使用する場合にこのオプションを選択し、ログインおよびパスワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="0abb8-117">Choose this option if you want log shipping to use a specific [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login and then specify the login and password.</span></span>  
  
 <span data-ttu-id="0abb8-118">**[次の期間以後の履歴を削除する]**</span><span class="sxs-lookup"><span data-stu-id="0abb8-118">**Delete history after**</span></span>  
 <span data-ttu-id="0abb8-119">ログ配布履歴情報を削除する前に、監視サーバー上に保持する期間を指定します。</span><span class="sxs-lookup"><span data-stu-id="0abb8-119">Specify the amount of time to retain log shipping history information on the monitor server before it is deleted.</span></span>  
  
 <span data-ttu-id="0abb8-120">**ジョブ名**</span><span class="sxs-lookup"><span data-stu-id="0abb8-120">**Job name**</span></span>  
 <span data-ttu-id="0abb8-121">バックアップまたは復元しきい値が超過したときに、警告を発行するためにログ配布によって使用される SQL Server エージェントの警告ジョブの名前を示します。</span><span class="sxs-lookup"><span data-stu-id="0abb8-121">Indicates the name of the SQL Server Agent alert job used by log shipping to raise alerts when backup or restore thresholds have been exceeded.</span></span> <span data-ttu-id="0abb8-122">このジョブを作成しているときは、ボックスに入力することで名前を変更できます。</span><span class="sxs-lookup"><span data-stu-id="0abb8-122">When first creating this job, you can change the name by typing in the box.</span></span>  
  
 <span data-ttu-id="0abb8-123">**[スケジュール]**</span><span class="sxs-lookup"><span data-stu-id="0abb8-123">**Schedule**</span></span>  
 <span data-ttu-id="0abb8-124">SQL Server エージェントの警告ジョブの現在のスケジュールを示します。</span><span class="sxs-lookup"><span data-stu-id="0abb8-124">Indicates the current schedule of the SQL Server Agent alert job.</span></span>  
  
 <span data-ttu-id="0abb8-125">**[編集]**</span><span class="sxs-lookup"><span data-stu-id="0abb8-125">**Edit**</span></span>  
 <span data-ttu-id="0abb8-126">SQL Server エージェントの警告ジョブのパラメーターを変更します。</span><span class="sxs-lookup"><span data-stu-id="0abb8-126">Modify the SQL Server Agent alert job parameters.</span></span>  
  
 <span data-ttu-id="0abb8-127">**[このジョブを無効にする]**</span><span class="sxs-lookup"><span data-stu-id="0abb8-127">**Disable this job**</span></span>  
 <span data-ttu-id="0abb8-128">SQL Server エージェントの警告ジョブを中断します。</span><span class="sxs-lookup"><span data-stu-id="0abb8-128">Suspend the SQL Server Agent alert job.</span></span>  
  
  
