---
title: ログ配布レポートの表示 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- viewing log shipping reports
- displaying log shipping reports
- log shipping [SQL Server], monitoring
- log shipping [SQL Server], viewing reports
ms.assetid: 3b549f2f-3683-45e5-b8e8-8095276c41ab
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0d6c372a9b1f9af9e5948732e3bfb9384362f545
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645791"
---
# <a name="view-the-log-shipping-report-sql-server-management-studio"></a><span data-ttu-id="dd41c-102">ログ配布レポートの表示 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="dd41c-102">View the Log Shipping Report (SQL Server Management Studio)</span></span>
  <span data-ttu-id="dd41c-103">このトピックでは、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でトランザクション ログの配布の状態レポートを表示する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="dd41c-103">This topic explains how to view the Transaction Log Shipping Status report in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="dd41c-104">状態レポートは、監視サーバー、プライマリ サーバー、またはセカンダリ サーバーで実行できます。</span><span class="sxs-lookup"><span data-stu-id="dd41c-104">You can run a status report at a monitor server, primary server, or secondary server.</span></span> <span data-ttu-id="dd41c-105">ログ配布構成に関する完全な情報を表示するには、監視サーバーのインスタンスでレポートを表示します。</span><span class="sxs-lookup"><span data-stu-id="dd41c-105">To see the  most complete information about your log shipping configuration, view the report at the monitor server instance.</span></span>  
  
 <span data-ttu-id="dd41c-106">このレポートには、接続先のサーバー インスタンスから使用できるログ配布の利用状況の状態が表示されます。</span><span class="sxs-lookup"><span data-stu-id="dd41c-106">The report displays the status of any log shipping activity whose status is available from the server instance to which you are connected.</span></span> <span data-ttu-id="dd41c-107">接続先のサーバー インスタンスが複数の構成に関与しており、それぞれ異なる役割が与えられている場合 (あるデータベースでは監視サーバーとして機能し、別のデータベースではセカンダリ サーバーとして機能する場合など) は、それぞれの役割から見た各構成の情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="dd41c-107">If that server instance is involved in multiple configurations in different roles (such as serving as a monitor for one database and a secondary for another database), the displayed results contain the information of every configuration from the perspective of each role.</span></span> <span data-ttu-id="dd41c-108">ストアド プロシージャから特定のログ配布構成の監視サーバー インスタンスに接続できる場合、レポートにはその構成の状態がさらに多く表示されます。</span><span class="sxs-lookup"><span data-stu-id="dd41c-108">If the stored procedure can connect to the monitor server instance for a given log shipping configuration, the report displays additional status for that configuration.</span></span>  
  
 <span data-ttu-id="dd41c-109">現在のサーバー インスタンスによって実行される役割ごとに、次の情報を表示できます。</span><span class="sxs-lookup"><span data-stu-id="dd41c-109">For each role performed by the current server instance, you can view the following information:</span></span>  
  
|<span data-ttu-id="dd41c-110">Role</span><span class="sxs-lookup"><span data-stu-id="dd41c-110">Role</span></span>|<span data-ttu-id="dd41c-111">表示される情報</span><span class="sxs-lookup"><span data-stu-id="dd41c-111">Information displayed</span></span>|  
|----------|---------------------------|  
|<span data-ttu-id="dd41c-112">モニター</span><span class="sxs-lookup"><span data-stu-id="dd41c-112">Monitor</span></span>|<span data-ttu-id="dd41c-113">このサーバー インスタンスを監視サーバーとして使用するすべてのプライマリ サーバーとセカンダリ サーバーの名前と状態。</span><span class="sxs-lookup"><span data-stu-id="dd41c-113">The name and status of every primary server and secondary server that uses this server instance as its monitor server.</span></span>|  
|<span data-ttu-id="dd41c-114">プライマリ</span><span class="sxs-lookup"><span data-stu-id="dd41c-114">Primary</span></span>|<span data-ttu-id="dd41c-115">プライマリ データベースごとの、現在のサーバー インスタンスの (プライマリ サーバーとしての) 状態と名前、およびプライマリ データベース名。</span><span class="sxs-lookup"><span data-stu-id="dd41c-115">For each primary database, the status and name of the current server instance (as the primary server), along with the primary database name.</span></span> <span data-ttu-id="dd41c-116">このレポートには、(プライマリ サーバーのローカルに格納された) バックアップ ジョブの状態が表示されます。</span><span class="sxs-lookup"><span data-stu-id="dd41c-116">The report displays the status of the backup job (which is stored locally on the primary server).</span></span><br /><br /> <span data-ttu-id="dd41c-117">また、このレポートには、対応するセカンダリ サーバーごとに 1 行のデータが含まれます。</span><span class="sxs-lookup"><span data-stu-id="dd41c-117">The report also contains a row for each of the corresponding secondary servers.</span></span> <span data-ttu-id="dd41c-118">構成に監視サーバーを使用していて、ストアド プロシージャからそのモニターに接続できる場合は、これらの行に最新のログ バックアップのコピー状態と復元状態が表示されます。</span><span class="sxs-lookup"><span data-stu-id="dd41c-118">If the configuration uses a monitor server and the stored procedure can connect to the monitor, these rows display the copy status and restore status for the most recent log backup.</span></span>|  
|<span data-ttu-id="dd41c-119">セカンダリ</span><span class="sxs-lookup"><span data-stu-id="dd41c-119">Secondary</span></span>|<span data-ttu-id="dd41c-120">セカンダリ データベースごとの、現在のサーバー インスタンスの (セカンダリ サーバーとしての) 状態と名前、およびセカンダリ データベース名。</span><span class="sxs-lookup"><span data-stu-id="dd41c-120">For each secondary database, the status and name of the current server instance (as the secondary server), along with the secondary database name.</span></span><br /><br /> <span data-ttu-id="dd41c-121">このレポートには、セカンダリ サーバーでのコピー ジョブと復元ジョブの状態が表示されます。</span><span class="sxs-lookup"><span data-stu-id="dd41c-121">The report displays the status of the copy and restore jobs at the secondary server.</span></span><br /><br /> <span data-ttu-id="dd41c-122">また、このレポートには、対応するプライマリ サーバーのデータが 1 行含まれます。</span><span class="sxs-lookup"><span data-stu-id="dd41c-122">The report also contains a row for the corresponding primary server.</span></span> <span data-ttu-id="dd41c-123">構成に監視サーバーを使用していて、ストアド プロシージャからそのモニターに接続できる場合は、この行に最新のログ バックアップの状態が表示されます。</span><span class="sxs-lookup"><span data-stu-id="dd41c-123">If the configuration uses a monitor server and the stored procedure can connect to the monitor, this row displays the status of the most recent log backup.</span></span>|  
  
 <span data-ttu-id="dd41c-124">表示される情報は、サーバー インスタンスが監視サーバー、プライマリ サーバー、セカンダリ サーバーのいずれであるかによって異なります。</span><span class="sxs-lookup"><span data-stu-id="dd41c-124">The information displayed depends on whether the server instance is a monitor server, primary server, or secondary server.</span></span> <span data-ttu-id="dd41c-125">使用できる情報がない場合は、対応するセルがグレーで表示されます。</span><span class="sxs-lookup"><span data-stu-id="dd41c-125">If information is not available, the corresponding cells are grayed out.</span></span>  
  
 <span data-ttu-id="dd41c-126">レポートでは、**sp_help_log_shipping_monitor** を呼び出してデータを取得します。</span><span class="sxs-lookup"><span data-stu-id="dd41c-126">The report calls **sp_help_log_shipping_monitor** to get the data.</span></span> <span data-ttu-id="dd41c-127">必要なアクセス許可については、「[sp_help_log_shipping_monitor &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-log-shipping-monitor-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dd41c-127">For information about the required permissions, see [sp_help_log_shipping_monitor &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-log-shipping-monitor-transact-sql).</span></span>  
  
### <a name="to-display-the-transaction-log-shipping-status-report-on-a-server-instance"></a><span data-ttu-id="dd41c-128">サーバー インスタンスでのトランザクション ログの配布の状態レポートを表示するには</span><span class="sxs-lookup"><span data-stu-id="dd41c-128">To display the Transaction Log Shipping Status report on a server instance</span></span>  
  
1.  <span data-ttu-id="dd41c-129">監視サーバー、プライマリ サーバー、またはセカンダリ サーバーのいずれかに接続します。</span><span class="sxs-lookup"><span data-stu-id="dd41c-129">Connect to a monitor server, primary server, or secondary server.</span></span>  
  
2.  <span data-ttu-id="dd41c-130">オブジェクト エクスプローラーで、サーバー インスタンスを右クリックして **[レポート]** をポイントし、 **[標準レポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dd41c-130">Right-click the server instance in Object Explorer, point to **Reports**, and point to **Standard Reports**.</span></span>  
  
3.  <span data-ttu-id="dd41c-131">**[トランザクション ログの配布の状態]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dd41c-131">Click **Transaction Log Shipping Status**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd41c-132">参照</span><span class="sxs-lookup"><span data-stu-id="dd41c-132">See Also</span></span>  
 [<span data-ttu-id="dd41c-133">ログ配布の監視 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="dd41c-133">Monitor Log Shipping &#40;Transact-SQL&#41;</span></span>](monitor-log-shipping-transact-sql.md)  
  
  
