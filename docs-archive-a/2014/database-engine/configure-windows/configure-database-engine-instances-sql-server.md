---
title: データベース エンジンのインスタンスの構成 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 84e36fcb-2c78-48e8-8e4b-bf784a3ee557
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: af7408ff66d1f0e41369ba095ce51ea590d316e7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645857"
---
# <a name="configure-database-engine-instances-sql-server"></a><span data-ttu-id="ae18d-102">データベース エンジンのインスタンスの構成 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="ae18d-102">Configure Database Engine Instances (SQL Server)</span></span>
  <span data-ttu-id="ae18d-103">[!INCLUDE[ssDE](../../includes/ssde-md.md)] の各インスタンスは、インスタンスによってホストされているデータベース用に定義されているパフォーマンスと可用性の要件を満たすように構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ae18d-103">Each instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] must be configured to meet the performance and availability requirements defined for the databases hosted by the instance.</span></span> <span data-ttu-id="ae18d-104">[!INCLUDE[ssDE](../../includes/ssde-md.md)] には、リソースの使用などの動作や、監査またはトリガー再帰などの機能の可用性を制御する構成オプションがあります。</span><span class="sxs-lookup"><span data-stu-id="ae18d-104">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] includes configuration options that control behaviors such as resource usage and the availability of features such as auditing or trigger recursion.</span></span>  
  
## <a name="instance-configuration"></a><span data-ttu-id="ae18d-105">[インスタンスの構成]</span><span class="sxs-lookup"><span data-stu-id="ae18d-105">Instance Configuration</span></span>  
 <span data-ttu-id="ae18d-106">データベースを実稼働環境に配置するときには、多くの場合、データベースが必要とするパフォーマンス レベルや、データベースの必要な可用性レベルなどの分野が、サービス レベル契約 (SLA) で定義されます。</span><span class="sxs-lookup"><span data-stu-id="ae18d-106">When a database is deployed into production there is often a service level agreement (SLA) defining areas such as the levels of performance required from the database and the required availability level of the database.</span></span> <span data-ttu-id="ae18d-107">SLA の条件によって、通常はインスタンスの構成要件が決まります。</span><span class="sxs-lookup"><span data-stu-id="ae18d-107">The terms of the SLA typically drive configuration requirements for the instance.</span></span>  
  
 <span data-ttu-id="ae18d-108">インスタンスは、通常、インストールの直後に構成されます。</span><span class="sxs-lookup"><span data-stu-id="ae18d-108">An instance is usually configured immediately after it has been installed.</span></span> <span data-ttu-id="ae18d-109">初期構成は、インスタンスに配置されることになる種類のデータベースの SLA 要件によって決められるのが一般的です。</span><span class="sxs-lookup"><span data-stu-id="ae18d-109">The initial configuration is usually determined by the SLA requirements of the types of databases planned to be deployed to the instance.</span></span> <span data-ttu-id="ae18d-110">データベースの配置後、データベース管理者はインスタンスのパフォーマンスを監視し、インスタンスが SLA 要件を満たしていないことをパフォーマンス指標が示している場合は、必要に応じて構成設定を調整します。</span><span class="sxs-lookup"><span data-stu-id="ae18d-110">After the databases have been deployed, the database administrators monitor the performance of the instance and adjust the configuration settings as needed if the performance metrics show the instance is not meeting the SLA requirements.</span></span>  
  
## <a name="configuration-tasks"></a><span data-ttu-id="ae18d-111">構成のタスク</span><span class="sxs-lookup"><span data-stu-id="ae18d-111">Configuration Tasks</span></span>  
  
|<span data-ttu-id="ae18d-112">タスクの説明</span><span class="sxs-lookup"><span data-stu-id="ae18d-112">Task Description</span></span>|<span data-ttu-id="ae18d-113">トピック</span><span class="sxs-lookup"><span data-stu-id="ae18d-113">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="ae18d-114">インスタンスの各種構成オプションとその表示方法、変更方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ae18d-114">Describes the various instance configuration options and how to view or change these options.</span></span>|[<span data-ttu-id="ae18d-115">サーバー構成オプション &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ae18d-115">Server Configuration Options &#40;SQL Server&#41;</span></span>](server-configuration-options-sql-server.md)|  
|<span data-ttu-id="ae18d-116">インスタンス内の新しいデータ ファイルとログ ファイルの既定の場所を表示および構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ae18d-116">Describes how to view and configure the default locations of new data and log files in the instance.</span></span>|[<span data-ttu-id="ae18d-117">データ ファイルとログ ファイルの既定の場所の表示または変更 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="ae18d-117">View or Change the Default Locations for Data and Log Files &#40;SQL Server Management Studio&#41;</span></span>](view-or-change-the-default-locations-for-data-and-log-files.md)|  
|<span data-ttu-id="ae18d-118">ソフト NUMA を使用するための SQL Server の構成方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ae18d-118">Describes how to configure SQL Server to use soft-NUMA.</span></span>|[<span data-ttu-id="ae18d-119">ソフト NUMA &#40;SQL Server を使用するように SQL Server を構成する&#41;</span><span class="sxs-lookup"><span data-stu-id="ae18d-119">Configure SQL Server to Use Soft-NUMA &#40;SQL Server&#41;</span></span>](soft-numa-sql-server.md)|  
|<span data-ttu-id="ae18d-120">TCP/IP ポートを NUMA (non-uniform memory access) ノード関係にマップする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ae18d-120">Describes how to map a TCP/IP port to non-uniform memory access (NUMA) node affinity.</span></span>|[<span data-ttu-id="ae18d-121">NUMA ノードへの TCP/IP ポートのマッピング &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ae18d-121">Map TCP IP Ports to NUMA Nodes &#40;SQL Server&#41;</span></span>](map-tcp-ip-ports-to-numa-nodes-sql-server.md)|  
|<span data-ttu-id="ae18d-122">Windows の "メモリ内のページのロック" ポリシーを有効にする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ae18d-122">Describes how to enable the Windows Lock Pages In Memory policy.</span></span> <span data-ttu-id="ae18d-123">このポリシーにより、プロセスを使用して物理メモリにデータを保持できるアカウントを指定し、ディスク上の仮想メモリへのデータのページングを防止します。</span><span class="sxs-lookup"><span data-stu-id="ae18d-123">This policy determines which accounts can use a process to keep data in physical memory, preventing the system from paging the data to virtual memory on disk.</span></span>|[<span data-ttu-id="ae18d-124">Lock Pages in Memory オプションの有効化 &#40;Windows&#41;</span><span class="sxs-lookup"><span data-stu-id="ae18d-124">Enable the Lock Pages in Memory Option &#40;Windows&#41;</span></span>](enable-the-lock-pages-in-memory-option-windows.md)|  
  
## <a name="see-also"></a><span data-ttu-id="ae18d-125">参照</span><span class="sxs-lookup"><span data-stu-id="ae18d-125">See Also</span></span>  
 [<span data-ttu-id="ae18d-126">データベース エンジンのインスタンス &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ae18d-126">Database Engine Instances &#40;SQL Server&#41;</span></span>](database-engine-instances-sql-server.md)  
  
  
