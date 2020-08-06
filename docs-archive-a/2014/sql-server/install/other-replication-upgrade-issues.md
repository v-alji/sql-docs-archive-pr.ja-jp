---
title: レプリケーションのアップグレードに関するその他の問題 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- system tables [SQL Server], replication
- passwords [SQL Server replication]
- versions [SQL Server replication]
- connections [SQL Server replication]
- scripts [SQL Server replication]
- ActiveX controls [SQL Server replication]
ms.assetid: 8a5e74be-4992-4f17-b20c-c3dce8f49329
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: e8ce3f35ead9d3322c636462f682ef391703cfe2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644285"
---
# <a name="other-replication-upgrade-issues"></a><span data-ttu-id="4e7ad-102">レプリケーションのアップグレードに関するその他の問題</span><span class="sxs-lookup"><span data-stu-id="4e7ad-102">Other Replication Upgrade Issues</span></span>
  <span data-ttu-id="4e7ad-103">このトピックでは、アップグレード アドバイザーによって報告されない多くのアップグレード問題について説明します。</span><span class="sxs-lookup"><span data-stu-id="4e7ad-103">This topic covers a number of upgrade issues that are not reported by Upgrade Advisor.</span></span>  
  
## <a name="versions-supported"></a><span data-ttu-id="4e7ad-104">サポートされているバージョン</span><span class="sxs-lookup"><span data-stu-id="4e7ad-104">Versions Supported</span></span>  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="4e7ad-105">では、レプリケートされたデータベースを以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] からアップグレードできます。</span><span class="sxs-lookup"><span data-stu-id="4e7ad-105">supports upgrading replicated databases from earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="4e7ad-106">ノードのアップグレード中に、その他のノードでの操作を停止する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="4e7ad-106">You do not have to stop activity at other nodes while a node is being upgraded.</span></span> <span data-ttu-id="4e7ad-107">トポロジでサポートされるバージョンに関する以下の規則に従っていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="4e7ad-107">Ensure that you adhere to the rules regarding which versions are supported in a topology.</span></span>  
  
 <span data-ttu-id="4e7ad-108">またはの異なるバージョン間でレプリケートする場合、通常は、使用され [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ている最も古いバージョンの機能に制限されます。</span><span class="sxs-lookup"><span data-stu-id="4e7ad-108">When you replicate between or among different versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you are usually limited to the functionality of the earliest version that is being used.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4e7ad-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のディスク上ストレージ形式は、64 ビット環境と 32 ビット環境で同じため、レプリケーション トポロジでは、32 ビット環境で実行されているサーバー インスタンスと 64 ビット環境で実行されているサーバー インスタンスを組み合わせることができます。</span><span class="sxs-lookup"><span data-stu-id="4e7ad-109">Because the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on-disk storage format is the same in the 64-bit and 32-bit environments, a replication topology can combine server instances that run in a 32-bit environment and server instances that run in a 64-bit environment.</span></span>  
  
 <span data-ttu-id="4e7ad-110">どの種類のレプリケーションでも、ディストリビューターのバージョンがパブリッシャーのバージョン以上である必要があります </span><span class="sxs-lookup"><span data-stu-id="4e7ad-110">For all types of replication, the Distributor version must be no earlier than the Publisher version.</span></span> <span data-ttu-id="4e7ad-111">(多くの場合、ディストリビューターはパブリッシャーと同じインスタンスです)。</span><span class="sxs-lookup"><span data-stu-id="4e7ad-111">(Frequently, the Distributor is the same instance as the Publisher.)</span></span>  
  
 <span data-ttu-id="4e7ad-112">トランザクション レプリケーションの場合、トランザクション パブリケーションのサブスクライバーは、2 つのパブリッシャー バージョンのうちどちらでも使用できます。</span><span class="sxs-lookup"><span data-stu-id="4e7ad-112">For transactional replication, a Subscriber to a transactional publication can be any version within two versions of the Publisher version.</span></span>  
  
 <span data-ttu-id="4e7ad-113">マージ レプリケーションの場合、マージ パブリケーションのサブスクライバーは、パブリッシャーのバージョン以前であればどのバージョンでも使用できます。</span><span class="sxs-lookup"><span data-stu-id="4e7ad-113">For merge replication, a Subscriber to a merge publication can be any version no later than the Publisher version.</span></span>  
  
## <a name="merge-replication-batches-changes"></a><span data-ttu-id="4e7ad-114">マージ レプリケーションのバッチの変更</span><span class="sxs-lookup"><span data-stu-id="4e7ad-114">Merge Replication Batches Changes</span></span>  
 <span data-ttu-id="4e7ad-115">マージ エージェントによって行われた変更がパフォーマンス向上のためにバッチ処理されるため、1 つのステートメント内で複数の行を挿入、更新、または削除できます。</span><span class="sxs-lookup"><span data-stu-id="4e7ad-115">Changes that are made by the Merge Agent are batched to improve performance; therefore, more than one row can be inserted, updated, or deleted within a single statement.</span></span> <span data-ttu-id="4e7ad-116">パブリケーション データベースまたはサブスクリプション データベースでパブリッシュされたテーブルにトリガーがある場合には、トリガーによって複数行の挿入、更新、および削除が処理されることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="4e7ad-116">If any published tables in the publication or subscription databases have triggers, ensure that the triggers can handle multirow inserts, updates, and deletes.</span></span> <span data-ttu-id="4e7ad-117">詳細については、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックの「DML トリガーの複数行に関する注意点」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4e7ad-117">For more information, see "Multirow Considerations for DML Triggers" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="activex-control-changes"></a><span data-ttu-id="4e7ad-118">ActiveX コントロールの変更</span><span class="sxs-lookup"><span data-stu-id="4e7ad-118">ActiveX Control Changes</span></span>  
 <span data-ttu-id="4e7ad-119">レプリケーション ActiveX コントロールに対する変更は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="4e7ad-119">The following changes have been made for replication ActiveX controls:</span></span>  
  
-   <span data-ttu-id="4e7ad-120">すべての ActiveX コントロールに、スクリプトおよび初期化に対して安全でないことを示すマークが付けられます。</span><span class="sxs-lookup"><span data-stu-id="4e7ad-120">All ActiveX controls are marked as unsafe for scripting and initialization.</span></span>  
  
-   <span data-ttu-id="4e7ad-121">スナップショット ActiveX コントロールはサポートされなくなりました。</span><span class="sxs-lookup"><span data-stu-id="4e7ad-121">The Snapshot ActiveX control has been dropped.</span></span> <span data-ttu-id="4e7ad-122">スナップショットを作成および管理するには、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用するか、レプリケーション ストアド プロシージャを使用してプログラムによって実行します。</span><span class="sxs-lookup"><span data-stu-id="4e7ad-122">You can create and manage snapshots by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or programmatically by using replication stored procedures.</span></span> <span data-ttu-id="4e7ad-123">詳細については、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] オンライン ブックの「初期スナップショットを作成および適用する方法 ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)])」および「初期スナップショットを作成する方法 (レプリケーション Transact-SQL プログラミング)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4e7ad-123">For more information, see the topics "How to: Create and Apply the Initial Snapshot ([!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)])" and "How to: Create the Initial Snapshot (Replication Transact-SQL Programming)" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
-   <span data-ttu-id="4e7ad-124">ディストリビューション ActiveX コントロールおよびマージ ActiveX コントロールは非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="4e7ad-124">The Distribution ActiveX control and Merge ActiveX control have been deprecated.</span></span> <span data-ttu-id="4e7ad-125">同様の機能は、レプリケーション管理オブジェクト (RMO) を使用したマネージド コード アプリケーションに提供されます。</span><span class="sxs-lookup"><span data-stu-id="4e7ad-125">Similar functionality is provided for managed code applications using Replication Management Objects (RMO).</span></span> <span data-ttu-id="4e7ad-126">詳細については、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックの「サブスクリプションの同期 (RMO プログラミング)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4e7ad-126">For more information, see "Synchronizing Subscriptions (RMO Programming)" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e7ad-127">参照</span><span class="sxs-lookup"><span data-stu-id="4e7ad-127">See Also</span></span>  
 [<span data-ttu-id="4e7ad-128">レプリケーションのアップグレードに関する問題</span><span class="sxs-lookup"><span data-stu-id="4e7ad-128">Replication Upgrade Issues</span></span>](../../../2014/sql-server/install/replication-upgrade-issues.md)  
  
  
