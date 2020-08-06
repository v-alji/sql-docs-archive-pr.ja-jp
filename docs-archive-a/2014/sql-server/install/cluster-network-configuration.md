---
title: クラスターネットワークの構成 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- cluster network selection, Setup
- cluster network selection
ms.assetid: 579482ef-a023-45b2-9176-b4a4188adf9d
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 17ab563817a3b9b476dfd566f4a7f2beda98ca26
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640462"
---
# <a name="cluster-network-configuration"></a><span data-ttu-id="5abfc-102">クラスター ネットワークの構成</span><span class="sxs-lookup"><span data-stu-id="5abfc-102">Cluster Network Configuration</span></span>
  <span data-ttu-id="5abfc-103">フェールオーバー クラスター インスタンスのネットワーク リソースを指定するには、 **[クラスター ネットワークの選択]** ページを使用します。</span><span class="sxs-lookup"><span data-stu-id="5abfc-103">Use the **Cluster Network Selection** page to specify the network resources for your failover cluster instance.</span></span>  
  
## <a name="options"></a><span data-ttu-id="5abfc-104">Options</span><span class="sxs-lookup"><span data-stu-id="5abfc-104">Options</span></span>  
 <span data-ttu-id="5abfc-105">\*\* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] フェールオーバークラスターのネットワーク名\*\*-これは、ネットワーク上のフェールオーバークラスターインスタンスを識別するために使用される名前です。</span><span class="sxs-lookup"><span data-stu-id="5abfc-105">**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Failover Cluster Network Name** - This is the name used to identify your failover cluster instance on the network.</span></span>  
  
 <span data-ttu-id="5abfc-106">**[ネットワークの設定]** - フェールオーバー クラスター インスタンスの IP の種類と IP アドレスを指定します。</span><span class="sxs-lookup"><span data-stu-id="5abfc-106">**Network Settings** - Specify the IP type and IP address for your failover cluster instance.</span></span>  
  
 <span data-ttu-id="5abfc-107">ノードの追加またはノードの削除を実行すると、その操作が進行している間、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] フェールオーバー クラスターの既存の IP アドレスを示した読み取り専用の一覧が [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によって表示されます。</span><span class="sxs-lookup"><span data-stu-id="5abfc-107">During the Add Node and Remove Node operations, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] displays a read-only list of the existing IP addresses for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster.</span></span>  
  
-   <span data-ttu-id="5abfc-108">統合インストール:</span><span class="sxs-lookup"><span data-stu-id="5abfc-108">Integrated Install:</span></span>  
  
    -   <span data-ttu-id="5abfc-109">追加しようとしているノードが、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] フェールオーバー クラスターの既存のノードとまったく同じ一連のネットワーク サブネットをサポートする場合、他の IP アドレスは追加できません。</span><span class="sxs-lookup"><span data-stu-id="5abfc-109">If you are adding a node that supports an identical set of network subnets supported by the existing nodes of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster, no additional IP addresses can be added.</span></span> <span data-ttu-id="5abfc-110">依存関係の設定は変更されません。</span><span class="sxs-lookup"><span data-stu-id="5abfc-110">The dependency setting remains unchanged.</span></span>  
  
    -   <span data-ttu-id="5abfc-111">追加しようとしているノードが、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] フェールオーバー クラスターの既存のノードがサポートしているサブネットの一部のみをサポートする場合、他の IP アドレス リソースは追加できません。</span><span class="sxs-lookup"><span data-stu-id="5abfc-111">If you are adding a node that supports a subset of the subnets supported by the existing nodes on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster, no additional IP address resources can be added.</span></span> <span data-ttu-id="5abfc-112">指定された IP アドレスが一部のクラスター ノードでは無効であるという事実を反映するために、IP アドレス リソースの依存関係は [OR] に設定されます。</span><span class="sxs-lookup"><span data-stu-id="5abfc-112">The IP address resource dependency is set to OR to reflect that all the specified IP addresses are not valid on all the cluster nodes.</span></span>  
  
    -   <span data-ttu-id="5abfc-113">追加しようとしているノードが、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] フェールオーバー クラスターの既存のノードによって既にサポートされている以外のサブネットもサポートする場合、新しい有効な IP アドレスを追加することを選択できます。</span><span class="sxs-lookup"><span data-stu-id="5abfc-113">If you are adding a node that supports subnets in addition to the subnets already supported by the existing nodes on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster, you have the option of adding new valid IP addresses.</span></span> <span data-ttu-id="5abfc-114">新しい IP アドレスが指定された場合、指定された IP アドレスが一部のクラスター ノードでは無効であるという事実を反映するために、IP アドレス リソースの依存関係は [OR] に設定されます。</span><span class="sxs-lookup"><span data-stu-id="5abfc-114">If new IP addresses are specified, the IP address resource dependency is set to OR to reflect that all the specified IP addresses are not valid on all the cluster nodes.</span></span>  
  
    -   <span data-ttu-id="5abfc-115">追加しようとしているノードが、他のネットワーク サブネットをサポートしている場合で、なおかつ、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] フェールオーバー クラスターの既存のノードによってサポートされたサブネットは一切サポートしないという場合、別途 IP アドレスを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5abfc-115">If you are adding a node that supports additional network subnets, but supports none of the subnets supported by the existing nodes on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster, you are required to add additional IP addresses.</span></span> <span data-ttu-id="5abfc-116">指定された IP アドレスが一部のクラスター ノードでは無効であるという事実を反映するために、IP アドレス リソースの依存関係は [OR] に設定されます。</span><span class="sxs-lookup"><span data-stu-id="5abfc-116">The IP address resource dependency is set to OR to reflect that all the specified IP addresses are not valid on all the cluster nodes.</span></span>  
  
-   <span data-ttu-id="5abfc-117">詳細設定インストール: インストールの完了手順で、フェールオーバー クラスター インスタンスのすべてのノードおよびサブネットについて、対応する IP アドレスを指定します。</span><span class="sxs-lookup"><span data-stu-id="5abfc-117">Advanced Install: During the Complete step of the installation, specify the IP address for all the nodes and subnets for your failover cluster instance.</span></span> <span data-ttu-id="5abfc-118">マルチサブネット フェールオーバー クラスターの場合は複数の IP アドレスを指定できますが、サポートされる IP アドレスは、1 つのサブネットにつき 1 つだけです。</span><span class="sxs-lookup"><span data-stu-id="5abfc-118">You can specify multiple IP addresses for a multi-subnet failover cluster, but only one IP address per subnet is supported.</span></span> <span data-ttu-id="5abfc-119">準備の対象となるすべてのノードは、少なくとも 1 つの IP アドレスを所有している必要があります。</span><span class="sxs-lookup"><span data-stu-id="5abfc-119">Every prepared node should be an owner of at least one IP address.</span></span> <span data-ttu-id="5abfc-120">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] フェールオーバー クラスター内に複数のサブネットが存在する場合、IP アドレス リソースの依存関係を [OR] に設定するように求められます。ノードの削除:</span><span class="sxs-lookup"><span data-stu-id="5abfc-120">If you have multiple subnets in your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster, you are prompted to set the IP address resource dependency to OR.Remove Node:</span></span>  
  
    -   <span data-ttu-id="5abfc-121">残りの IP アドレスが、残りのすべてのノードでサポートされている場合は、IP アドレス リソースの依存関係を [AND] に設定するように求められます。</span><span class="sxs-lookup"><span data-stu-id="5abfc-121">If the remaining IP addresses are supported on all the remaining nodes, you are prompted to set the IP address resource dependencyto AND.</span></span>  
  
    -   <span data-ttu-id="5abfc-122">残りの IP アドレスが、残りのすべてのノードでサポートされていない場合は、IP アドレス リソースの依存関係は [OR] のままとなります。</span><span class="sxs-lookup"><span data-stu-id="5abfc-122">If the remaining IP addresses are not supported on all the remaining nodes, the IP address resource dependency is left as OR.</span></span>  
  
  
