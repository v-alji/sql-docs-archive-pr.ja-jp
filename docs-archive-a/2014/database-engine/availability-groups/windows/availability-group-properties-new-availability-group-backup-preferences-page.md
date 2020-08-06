---
title: '[可用性グループのプロパティ]: [新しい可用性グループ] ([バックアップの設定] ページ)Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilitygroupproperties.backuppreferences.f1
helpviewer_keywords:
- read-only routing
ms.assetid: 65fff22d-5963-4a8c-8b31-fe9ab247a03e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 7914d4b1d7af06bcaf4f3fd05a260138e3edf5fc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632122"
---
# <a name="availability-group-properties-new-availability-group-backup-preferences-page"></a><span data-ttu-id="c9961-102">可用性グループのプロパティ:新しい可用性グループ ([バックアップの設定] ページ)</span><span class="sxs-lookup"><span data-stu-id="c9961-102">Availability Group Properties: New Availability Group (Backup Preferences Page)</span></span>
  <span data-ttu-id="c9961-103">このダイアログ ボックスを使用して、選択した可用性グループのバックアップのユーザー設定を表示および変更します。</span><span class="sxs-lookup"><span data-stu-id="c9961-103">Use this dialog box to view and change the backup preferences of the selected availability group.</span></span>  
  
 <span data-ttu-id="c9961-104">**可用性グループのプロパティを表示するには**</span><span class="sxs-lookup"><span data-stu-id="c9961-104">**To view availability group properties**</span></span>  
  
-   [<span data-ttu-id="c9961-105">可用性グループのプロパティの表示 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="c9961-105">View Availability Group Properties &#40;SQL Server&#41;</span></span>](view-availability-group-properties-sql-server.md)  
  
-   [<span data-ttu-id="c9961-106">AlwaysOn ダッシュボードの使用 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="c9961-106">Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;</span></span>](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
## <a name="where-should-backups-occur"></a><span data-ttu-id="c9961-107">バックアップを実行する場所</span><span class="sxs-lookup"><span data-stu-id="c9961-107">Where should backups occur?</span></span>  
 <span data-ttu-id="c9961-108">**[セカンダリを優先]**</span><span class="sxs-lookup"><span data-stu-id="c9961-108">**Prefer Secondary**</span></span>  
 <span data-ttu-id="c9961-109">オンラインのレプリカがプライマリ レプリカのみである場合を除き、セカンダリ レプリカでバックアップを実行することを指定します。</span><span class="sxs-lookup"><span data-stu-id="c9961-109">Specifies that backups should occur on a secondary replica except when the primary replica is the only replica online.</span></span> <span data-ttu-id="c9961-110">オンラインのレプリカがプライマリ レプリカのみである場合は、プライマリ レプリカでバックアップを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c9961-110">In that case, the backup should occur on the primary replica.</span></span> <span data-ttu-id="c9961-111">既定のオプションです。</span><span class="sxs-lookup"><span data-stu-id="c9961-111">This is the default option.</span></span>  
  
 <span data-ttu-id="c9961-112">**[セカンダリのみ]**</span><span class="sxs-lookup"><span data-stu-id="c9961-112">**Secondary only**</span></span>  
 <span data-ttu-id="c9961-113">バックアップをプライマリ レプリカでは実行しないことを指定します。</span><span class="sxs-lookup"><span data-stu-id="c9961-113">Specifies that backups should never be performed on the primary replica.</span></span> <span data-ttu-id="c9961-114">オンラインのレプリカがプライマリ レプリカだけの場合、バックアップは実行されません。</span><span class="sxs-lookup"><span data-stu-id="c9961-114">If the primary replica is the only replica online, the backup should not occur.</span></span>  
  
 <span data-ttu-id="c9961-115">**プライマリ**</span><span class="sxs-lookup"><span data-stu-id="c9961-115">**Primary**</span></span>  
 <span data-ttu-id="c9961-116">バックアップを常にプライマリ レプリカで実行することを指定します。</span><span class="sxs-lookup"><span data-stu-id="c9961-116">Specifies that the backups should always occur on the primary replica.</span></span> <span data-ttu-id="c9961-117">このオプションは、差分バックアップの作成など、バックアップがセカンダリ レプリカで実行されたときにはサポートされないバックアップ機能が必要な場合に役に立ちます。</span><span class="sxs-lookup"><span data-stu-id="c9961-117">This option is useful if you need backup features, such as creating differential backups, that are not supported when backup is run on a secondary replica.</span></span>  
  
 <span data-ttu-id="c9961-118">**[任意のレプリカ]**</span><span class="sxs-lookup"><span data-stu-id="c9961-118">**Any Replica**</span></span>  
 <span data-ttu-id="c9961-119">バックアップを実行するレプリカを選択するときにバックアップ ジョブが可用性レプリカのロールを無視するように指定します。</span><span class="sxs-lookup"><span data-stu-id="c9961-119">Specifies that you prefer that backup jobs ignore the role of the availability replicas when choosing the replica to perform backups.</span></span> <span data-ttu-id="c9961-120">バックアップ ジョブは、動作状態および接続状態と組み合わせて、各可用性レプリカのバックアップ優先順位などの他の要素を評価する場合があります。</span><span class="sxs-lookup"><span data-stu-id="c9961-120">Note backup jobs might evaluate other factors such as backup priority of each availability replica in combination with its operational state and connected state.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="c9961-121">バックアップに関するユーザー設定は適用されません。</span><span class="sxs-lookup"><span data-stu-id="c9961-121">There is no enforcement of the backup-preference setting.</span></span> <span data-ttu-id="c9961-122">この優先設定の解釈は、特定の可用性グループのデータベースに対するバックアップ ジョブのスクリプトでのロジックに依存します (ある場合)。</span><span class="sxs-lookup"><span data-stu-id="c9961-122">The interpretation of this preference depends on the logic, if any, that you script into back jobs for the databases in a given availability group.</span></span> <span data-ttu-id="c9961-123">詳細については、「[アクティブなセカンダリ: セカンダリレプリカでのバックアップ (AlwaysOn 可用性グループ)](active-secondaries-backup-on-secondary-replicas-always-on-availability-groups.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c9961-123">For more information, see [Active Secondaries: Backup on Secondary Replicas (AlwaysOn Availability Groups)](active-secondaries-backup-on-secondary-replicas-always-on-availability-groups.md).</span></span>  
  
## <a name="replica-backup-priorities"></a><span data-ttu-id="c9961-124">レプリカのバックアップの優先順位</span><span class="sxs-lookup"><span data-stu-id="c9961-124">Replica backup priorities</span></span>  
 <span data-ttu-id="c9961-125">このグリッドには、可用性グループのレプリカをホストする各サーバー インスタンスの現在のバックアップの優先順位が表示されます。</span><span class="sxs-lookup"><span data-stu-id="c9961-125">This grid displays the current backup priority of each server instance that hosts a replica for the availability group.</span></span> <span data-ttu-id="c9961-126">このグリッドを使用して、1 つまたは複数の可用性レプリカのバックアップの優先順位を変更します。</span><span class="sxs-lookup"><span data-stu-id="c9961-126">Use this grid to change the backup priority of one or more availability replicas.</span></span>  
  
 <span data-ttu-id="c9961-127">**サーバー インスタンス**</span><span class="sxs-lookup"><span data-stu-id="c9961-127">**Server Instance**</span></span>  
 <span data-ttu-id="c9961-128">可用性レプリカをホストする [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスの名前。</span><span class="sxs-lookup"><span data-stu-id="c9961-128">The name of the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that hosts the availability replica.</span></span>  
  
 <span data-ttu-id="c9961-129">**[バックアップ優先度 (最小 = 1、最高 = 100)]**</span><span class="sxs-lookup"><span data-stu-id="c9961-129">**Backup Priority (Lowest=1, Highest=100)**</span></span>  
 <span data-ttu-id="c9961-130">同じ可用性グループ内の他のレプリカと比較して、このレプリカでバックアップを実行する優先順位を指定します。</span><span class="sxs-lookup"><span data-stu-id="c9961-130">Specifies your priority for performing backups on this replica relative to the other replicas in the same availability group.</span></span> <span data-ttu-id="c9961-131">値は 0 ～ 100 の範囲の整数です。</span><span class="sxs-lookup"><span data-stu-id="c9961-131">The value is an integer in the range of 0..100.</span></span> <span data-ttu-id="c9961-132">1 は最も低い優先順位を示し、100 は最も高い優先順位を示します。</span><span class="sxs-lookup"><span data-stu-id="c9961-132">1 indicates the lowest priority, and 100 indicates the highest priority.</span></span> <span data-ttu-id="c9961-133">たとえば、 **Backup Priority** = 1 の場合、現在使用可能な可用性レプリカにそれより高い優先順位のものがない場合にのみ、その可用性レプリカがバックアップの実行に対して選択されます。</span><span class="sxs-lookup"><span data-stu-id="c9961-133">If **Backup Priority** = 1, the availability replica would be chosen for performing backups only if no higher priority availability replicas are currently available.</span></span>  
  
 <span data-ttu-id="c9961-134">**[レプリカの除外]**</span><span class="sxs-lookup"><span data-stu-id="c9961-134">**Exclude Replica**</span></span>  
 <span data-ttu-id="c9961-135">バックアップの実行時にこの可用性レプリカを選択しない場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="c9961-135">Select if you never want this availability replica to be chosen for performing backups.</span></span> <span data-ttu-id="c9961-136">これは、たとえば、バックアップをフェールオーバーすることがないリモート可用性レプリカのような場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="c9961-136">This is useful, for example, for a remote availability replica to which you never want backups to fail over.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9961-137">参照</span><span class="sxs-lookup"><span data-stu-id="c9961-137">See Also</span></span>  
 <span data-ttu-id="c9961-138">[アクティブなセカンダリ: セカンダリレプリカでのバックアップ (AlwaysOn 可用性グループ)](active-secondaries-backup-on-secondary-replicas-always-on-availability-groups.md) </span><span class="sxs-lookup"><span data-stu-id="c9961-138">[Active Secondaries: Backup on Secondary Replicas (AlwaysOn Availability Groups)](active-secondaries-backup-on-secondary-replicas-always-on-availability-groups.md) </span></span>  
 [<span data-ttu-id="c9961-139">ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="c9961-139">ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-availability-group-transact-sql)  
  
  
