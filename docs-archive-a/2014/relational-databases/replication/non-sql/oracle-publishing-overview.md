---
title: Oracle パブリッシングの概要 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- publishing [SQL Server replication], Oracle publishing
- snapshot replication [SQL Server], Oracle publishing
- Oracle publishing [SQL Server replication]
- transactional replication, Oracle publishing
- Oracle publishing [SQL Server replication], about Oracle publishing
ms.assetid: 2e013259-0022-4897-a08d-5f8deb880fa8
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b59b12dfcba1472cb6f9d6ecfc51a7df8104fb0b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643239"
---
# <a name="oracle-publishing-overview"></a><span data-ttu-id="1d12a-102">Oracle パブリッシングの概要</span><span class="sxs-lookup"><span data-stu-id="1d12a-102">Oracle Publishing Overview</span></span>
  <span data-ttu-id="1d12a-103">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 以降では、Oracle Version 9i を始めとした、Oracle パブリッシャーをレプリケーション トポロジに含めることができます。</span><span class="sxs-lookup"><span data-stu-id="1d12a-103">Beginning with [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], you can include Oracle Publishers in your replication topology, starting with Oracle version 9i.</span></span> <span data-ttu-id="1d12a-104">パブリッシング サーバーは、Oracle 対応の任意のハードウェアおよびオペレーティング システムに配置できます。</span><span class="sxs-lookup"><span data-stu-id="1d12a-104">Publishing servers can be deployed on any Oracle supported hardware and operating system.</span></span> <span data-ttu-id="1d12a-105">この機能は、既に確立されている [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のスナップショット レプリケーションとトランザクション レプリケーションを基礎としており、同様のパフォーマンスと使い勝手が実現されています。</span><span class="sxs-lookup"><span data-stu-id="1d12a-105">The feature is built on the well-established foundation of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] snapshot replication and transactional replication, providing similar performance and usability.</span></span>  
  
 <span data-ttu-id="1d12a-106">Oracle パブリッシングは非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="1d12a-106">Oracle Publishing is deprecated.</span></span> <span data-ttu-id="1d12a-107">SQL Server 以外のサブスクライバーへの異種レプリケーションは非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="1d12a-107">Heterogeneous replication to non-SQL Server subscribers is deprecated.</span></span> <span data-ttu-id="1d12a-108">データを移動するには、変更データ キャプチャと [!INCLUDE[ssIS](../../../includes/ssis-md.md)]を使用してソリューションを作成します。</span><span class="sxs-lookup"><span data-stu-id="1d12a-108">To move data, create solutions using change data capture and [!INCLUDE[ssIS](../../../includes/ssis-md.md)].</span></span>  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  
## <a name="snapshot-replication-for-oracle"></a><span data-ttu-id="1d12a-109">Oracle のスナップショット レプリケーション</span><span class="sxs-lookup"><span data-stu-id="1d12a-109">Snapshot Replication for Oracle</span></span>  
 <span data-ttu-id="1d12a-110">Oracle のスナップショット パブリケーションは、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のスナップショット パブリケーションと同じような方法で実装されます。</span><span class="sxs-lookup"><span data-stu-id="1d12a-110">Oracle snapshot publications are implemented in a manner similar to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] snapshot publications.</span></span> <span data-ttu-id="1d12a-111">Oracle パブリケーションに対してスナップショット エージェントが実行されると、エージェントは Oracle パブリッシャーに接続し、パブリケーションの各テーブルを処理します。</span><span class="sxs-lookup"><span data-stu-id="1d12a-111">When the Snapshot Agent runs for an Oracle publication, it connects to the Oracle Publisher and processes each table in the publication.</span></span> <span data-ttu-id="1d12a-112">各テーブルの処理では、テーブルの行が取得され、スキーマ スクリプトが作成されます。これらは、パブリケーションのスナップショット共有に格納されます。</span><span class="sxs-lookup"><span data-stu-id="1d12a-112">When processing each table, the agent retrieves the table rows and creates schema scripts, which are then stored on the publication's snapshot share.</span></span> <span data-ttu-id="1d12a-113">スナップショット エージェントが実行されるたびにデータの完全なセットが作成されるため、Oracle テーブルにはトランザクション レプリケーションのように変更追跡のトリガーは追加されません。</span><span class="sxs-lookup"><span data-stu-id="1d12a-113">The entire set of data is created each time the Snapshot Agent runs, so change tracking triggers are not added to the Oracle tables as they are with transactional replication.</span></span> <span data-ttu-id="1d12a-114">スナップショット レプリケーションは、パブリッシング システムへの影響を最小限に抑えながらデータを移行するのに便利です。</span><span class="sxs-lookup"><span data-stu-id="1d12a-114">Snapshot replication provides a convenient way to migrate data with minimal impact on the publishing system.</span></span>  
  
## <a name="transactional-replication-for-oracle"></a><span data-ttu-id="1d12a-115">Oracle のトランザクション レプリケーション</span><span class="sxs-lookup"><span data-stu-id="1d12a-115">Transactional Replication for Oracle</span></span>  
 <span data-ttu-id="1d12a-116">Oracle のトランザクション パブリケーションは、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]のトランザクション パブリッシング アーキテクチャを使用して実装されます。ただし、変更の追跡は、Oracle データベースのデータベース トリガーとログ リーダー エージェントの組み合わせによって行われます。</span><span class="sxs-lookup"><span data-stu-id="1d12a-116">Oracle transactional publications are implemented using the transactional publishing architecture of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]; however, changes are tracked using a combination of database triggers on the Oracle database and the Log Reader Agent.</span></span> <span data-ttu-id="1d12a-117">Oracle トランザクション パブリケーションのサブスクライバーは、スナップショット レプリケーションを使用して自動的に初期化されます。その後の変更はログ リーダー エージェントによって追跡され、変更が発生するとサブスクライバーに配信されます。</span><span class="sxs-lookup"><span data-stu-id="1d12a-117">Subscribers to an Oracle transactional publication are automatically initialized using snapshot replication; subsequent changes are tracked and delivered to Subscribers as they occur via the Log Reader Agent.</span></span>  
  
 <span data-ttu-id="1d12a-118">Oracle パブリケーションを作成すると、Oracle データベース内のパブリッシュされた各テーブルに対してトリガーと追跡テーブルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="1d12a-118">When an Oracle publication is created, triggers and tracking tables are created for each published table within the Oracle database.</span></span> <span data-ttu-id="1d12a-119">パブリッシュされたテーブルのデータが変更されると、テーブルのデータベース トリガーが起動されて、変更された各行の情報がレプリケーション追跡テーブルに挿入されます。</span><span class="sxs-lookup"><span data-stu-id="1d12a-119">When data changes are made to the published tables, the database triggers on the tables fire and insert information into the replication tracking tables for each modified row.</span></span> <span data-ttu-id="1d12a-120">その後、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ディストリビューターのログ リーダー エージェントが、そのデータ変更情報を追跡テーブルからディストリビューターのディストリビューション データベースへと移動します。</span><span class="sxs-lookup"><span data-stu-id="1d12a-120">The Log Reader Agent on the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Distributor then moves the data change information from the tracking tables to the distribution database on the Distributor.</span></span> <span data-ttu-id="1d12a-121">最後に、標準のトランザクション レプリケーションと同じように、ディストリビューション エージェントが変更をディストリビューターからサブスクライバーに移動します。</span><span class="sxs-lookup"><span data-stu-id="1d12a-121">Finally, as in standard transactional replication, the Distribution Agent moves changes from the Distributor to the Subscribers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d12a-122">参照</span><span class="sxs-lookup"><span data-stu-id="1d12a-122">See Also</span></span>  
 <span data-ttu-id="1d12a-123">[Oracle パブリッシャーの構成](configure-an-oracle-publisher.md) </span><span class="sxs-lookup"><span data-stu-id="1d12a-123">[Configure an Oracle Publisher](configure-an-oracle-publisher.md) </span></span>  
 <span data-ttu-id="1d12a-124">[Oracle パブリッシングの用語](glossary-of-terms-for-oracle-publishing.md) </span><span class="sxs-lookup"><span data-stu-id="1d12a-124">[Glossary of Terms for Oracle Publishing](glossary-of-terms-for-oracle-publishing.md) </span></span>  
 [<span data-ttu-id="1d12a-125">異種データベース レプリケーション</span><span class="sxs-lookup"><span data-stu-id="1d12a-125">Heterogeneous Database Replication</span></span>](heterogeneous-database-replication.md)  
  
  
