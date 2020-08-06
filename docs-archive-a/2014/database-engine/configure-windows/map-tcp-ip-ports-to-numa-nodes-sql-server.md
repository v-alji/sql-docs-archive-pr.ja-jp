---
title: NUMA ノードへの TCP/IP ポートのマッピング (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- NUMA
- memory [SQL Server], NUMA
- affinity NUMA
- ports [SQL Server], working with NUMA
- CPU [SQL Server], NUMA support
- NUMA, How to map a port to a NUMA node
- NUMA affinity
- TCP/IP [SQL Server], NUMA support
- non-uniform memory access
ms.assetid: 07727642-0266-4cbc-8c55-3c367e4458ca
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: cf4a1bd7e02719d3884011ad3faa20a1ccc6466a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712373"
---
# <a name="map-tcp-ip-ports-to-numa-nodes-sql-server"></a><span data-ttu-id="1b911-102">NUMA ノードへの TCP/IP ポートのマッピング (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="1b911-102">Map TCP IP Ports to NUMA Nodes (SQL Server)</span></span>
  <span data-ttu-id="1b911-103">このトピックでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーを使用して、TCP/IP ポートを NUMA (non-uniform memory access) ノードにマップする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="1b911-103">This topic describes how to map TCP/IP ports to non-uniform memory access (NUMA) nodes by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span> <span data-ttu-id="1b911-104">[!INCLUDE[ssDE](../../includes/ssde-md.md)] では、起動時にノード情報をエラー ログに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="1b911-104">On startup, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] writes the node information to the error log.</span></span>  
  
 <span data-ttu-id="1b911-105">使用するノードのノード番号を調べるには、エラー ログまたは **sys.dm_os_schedulers** ビューからノード情報を読み取ります。</span><span class="sxs-lookup"><span data-stu-id="1b911-105">To determine the node number of the node you want to use, either read the node information from the error log, or from the **sys.dm_os_schedulers** view.</span></span> <span data-ttu-id="1b911-106">1 つのノードまたは複数のノードに対して TCP/IP アドレスとポートを設定するには、ポート番号の後に、ノード ID ビットマップ (関係マスク) を角かっこで囲んで追加します。</span><span class="sxs-lookup"><span data-stu-id="1b911-106">To set a TCP/IP address and port to single or multiple nodes, append a node identification bitmap (an affinity mask) in brackets after the port number.</span></span> <span data-ttu-id="1b911-107">ノードは、10 進数形式または 16 進数形式で指定できます。</span><span class="sxs-lookup"><span data-stu-id="1b911-107">Nodes can be specified in either decimal or hexadecimal format.</span></span> <span data-ttu-id="1b911-108">ビットマップを作成するには、ノードに対して右から左に、76543210 のように 0 から番号を付けます。</span><span class="sxs-lookup"><span data-stu-id="1b911-108">To create the bitmap, first number the nodes from right to left starting with zero, as in 76543210.</span></span> <span data-ttu-id="1b911-109">使用するノードには 1、使用しないノードには 0 を指定して、ノード リストのバイナリ表記を作成します。</span><span class="sxs-lookup"><span data-stu-id="1b911-109">Create a binary representation of the node list, providing 1 for nodes you want to use, and 0 for nodes you do not want to use.</span></span> <span data-ttu-id="1b911-110">たとえば、0 番、2 番、および 5 番の NUMA ノードを使用するには、00100101 と指定します。</span><span class="sxs-lookup"><span data-stu-id="1b911-110">For example, to use NUMA nodes 0, 2, and 5, specify 00100101.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1b911-111">NUMA ノード番号</span><span class="sxs-lookup"><span data-stu-id="1b911-111">NUMA node number</span></span>|<span data-ttu-id="1b911-112">76543210</span><span class="sxs-lookup"><span data-stu-id="1b911-112">76543210</span></span>|  
|<span data-ttu-id="1b911-113">右から数えて 0 番、2 番、および 5 番をマスク</span><span class="sxs-lookup"><span data-stu-id="1b911-113">Mask for 0, 2, and 5 counting from right</span></span>|<span data-ttu-id="1b911-114">00100101</span><span class="sxs-lookup"><span data-stu-id="1b911-114">00100101</span></span>|  
  
 <span data-ttu-id="1b911-115">バイナリ表記 (00100101) を 10 進数 `[37]`または 16 進数 `[0x25]`に変換します。</span><span class="sxs-lookup"><span data-stu-id="1b911-115">Convert the binary representation (00100101), into decimal `[37]`, or hexadecimal `[0x25]`.</span></span> <span data-ttu-id="1b911-116">すべてのノードでリッスンするには、ノード識別子を指定しません。</span><span class="sxs-lookup"><span data-stu-id="1b911-116">To listen on all nodes, provide no node identifier.</span></span>  
  
 <span data-ttu-id="1b911-117">ポートが複数の NUMA ノードにマッピングされている場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] はノード間での負荷分散を試行することなくラウンド ロビン方式でノードに接続を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="1b911-117">If a port is mapped to more than one NUMA node, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] assigns connections to nodes in a round-robin fashion without attempting to balance load across the nodes.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1b911-118">各 IP アドレスの複数の TCP ポートでのリッスンを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で有効にするには、「 [複数の TCP ポートでリッスンするデータベース エンジンの構成](configure-the-database-engine-to-listen-on-multiple-tcp-ports.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1b911-118">To enable [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to listen on multiple TCP ports for each IP address, see [Configure the Database Engine to Listen on Multiple TCP Ports](configure-the-database-engine-to-listen-on-multiple-tcp-ports.md).</span></span>  
  
##  <a name="using-sql-server-configuration-manager"></a><a name="SSMSProcedure"></a> <span data-ttu-id="1b911-119">SQL Server 構成マネージャーの使用</span><span class="sxs-lookup"><span data-stu-id="1b911-119">Using SQL Server Configuration Manager</span></span>  
  
#### <a name="to-map-a-tcpip-port-to-a-numa-node"></a><span data-ttu-id="1b911-120">NUMA ノードに TCP/IP ポートをマッピングするには</span><span class="sxs-lookup"><span data-stu-id="1b911-120">To map a TCP/IP port to a NUMA node</span></span>  
  
1.  <span data-ttu-id="1b911-121">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーで、 **[SQL Server ネットワークの構成]** を展開し、 **[** *\<instance name> のプロトコル]* をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1b911-121">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, expand **SQL Server Network Configuration**, and then click **Protocols for** *\<instance name>*.</span></span>  
  
2.  <span data-ttu-id="1b911-122">詳細ペインで、 **[TCP/IP]** をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="1b911-122">In the details pane, double-click **TCP/IP**.</span></span>  
  
3.  <span data-ttu-id="1b911-123">**[IP アドレス]** タブで、構成する IP アドレスに対応するセクションの **[TCP ポート]** ボックスで、ポート番号の後に NUMA ノード識別子を角かっこで囲んで追加します。</span><span class="sxs-lookup"><span data-stu-id="1b911-123">On the **IP Addresses** tab, in the section corresponding to the IP address to configure, in the **TCP Port** box, add the NUMA node identifier in brackets after the port number.</span></span> <span data-ttu-id="1b911-124">たとえば、TCP ポート 1500 とノード 0 番、2 番、5 番の場合、`1500[37]`、または `1500[0x25]` を使用します。</span><span class="sxs-lookup"><span data-stu-id="1b911-124">For example, for TCP port 1500 and nodes 0, 2, and 5, use `1500[37]`, or `1500[0x25]`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b911-125">参照</span><span class="sxs-lookup"><span data-stu-id="1b911-125">See Also</span></span>  
 [<span data-ttu-id="1b911-126">ソフト NUMA &#40;SQL Server を使用するように SQL Server を構成する&#41;</span><span class="sxs-lookup"><span data-stu-id="1b911-126">Configure SQL Server to Use Soft-NUMA &#40;SQL Server&#41;</span></span>](soft-numa-sql-server.md)  
  
  
