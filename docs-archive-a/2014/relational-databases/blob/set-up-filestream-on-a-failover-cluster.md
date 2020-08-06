---
title: フェールオーバー クラスターでの FILESTREAM の設定 | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.technology: filestream
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- FILESTREAM [SQL Server], setting up on a failover cluster
ms.assetid: 6721f780-20b7-4109-8ddb-ac327310699e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 29541bbcfd323a85a3fa751f60904fd1a26e1199
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712042"
---
# <a name="set-up-filestream-on-a-failover-cluster"></a><span data-ttu-id="176cd-102">フェールオーバー クラスターでの FILESTREAM の設定</span><span class="sxs-lookup"><span data-stu-id="176cd-102">Set Up FILESTREAM on a Failover Cluster</span></span>
  <span data-ttu-id="176cd-103">このトピックでは、フェールオーバー クラスターで FILESTREAM を有効にする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="176cd-103">This topic describes how to enable FILESTREAM on a failover cluster.</span></span> <span data-ttu-id="176cd-104">この手順を実行する前に、 [フェールオーバー クラスタリング](../../sql-server/failover-clusters/windows/always-on-failover-cluster-instances-sql-server.md) について理解し、FILESTREAM を有効にしておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="176cd-104">Before you try this procedure, you should understand [failover clustering](../../sql-server/failover-clusters/windows/always-on-failover-cluster-instances-sql-server.md) and have FILESTREAM enabled.</span></span> <span data-ttu-id="176cd-105">FILESTREAM を有効にする方法の詳細については、「 [FILESTREAM の有効化と構成](enable-and-configure-filestream.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="176cd-105">For information about how to enable FILESTREAM, see [Enable and Configure FILESTREAM](enable-and-configure-filestream.md).</span></span>  
  
### <a name="to-set-up-filestream-on-a-failover-cluster"></a><span data-ttu-id="176cd-106">フェールオーバー クラスターで FILESTREAM を設定するには</span><span class="sxs-lookup"><span data-stu-id="176cd-106">To set up FILESTREAM on a failover cluster</span></span>  
  
1.  <span data-ttu-id="176cd-107">フェールオーバー クラスターのプライマリ ノードを設定します。</span><span class="sxs-lookup"><span data-stu-id="176cd-107">Set up the primary node for the failover cluster.</span></span>  
  
     <span data-ttu-id="176cd-108">設定が完了したら、 **SQL Server 構成マネージャー**を使用してプライマリ ノードで FILESTREAM を有効にします。</span><span class="sxs-lookup"><span data-stu-id="176cd-108">After the setup finishes, enable FILESTREAM on the primary node by using **SQL Server Configuration Manager**.</span></span> <span data-ttu-id="176cd-109">これにより、Windows Admin 権限を必要とする設定が有効になります。</span><span class="sxs-lookup"><span data-stu-id="176cd-109">This enables the settings that require Windows Admin privileges.</span></span> <span data-ttu-id="176cd-110">リモート アクセスが必要な場合は、 **[リモート クライアントに FILESTREAM データへのストリーム アクセスを許可する]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="176cd-110">If remote access is required, select **Allow remote clients to have streaming access to FILESTREAM data**.</span></span> <span data-ttu-id="176cd-111">これにより、ファイル共有クラスター リソースが作成されます。</span><span class="sxs-lookup"><span data-stu-id="176cd-111">This will create a file-share cluster resource.</span></span>  
  
2.  <span data-ttu-id="176cd-112">パッシブ ノードを設定します。</span><span class="sxs-lookup"><span data-stu-id="176cd-112">Set up a passive node.</span></span>  
  
     <span data-ttu-id="176cd-113">設定が完了したら、 **SQL Server 構成マネージャー**を使用してパッシブ ノードで FILESTREAM を有効にします。</span><span class="sxs-lookup"><span data-stu-id="176cd-113">After the setup finishes, enable FILESTREAM on the passive node by using **SQL Server Configuration Manager**.</span></span> <span data-ttu-id="176cd-114">**[Windows 共有名]** に指定する名前は、クラスター内のすべてのノードで同じにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="176cd-114">The name that you specify for **Windows Share Name** must be the same across all nodes in the cluster.</span></span>  
  
3.  <span data-ttu-id="176cd-115">パッシブ ノードをさらに追加するには、手順 2. を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="176cd-115">To add more passive nodes, repeat step 2.</span></span>  
  
4.  <span data-ttu-id="176cd-116">すべてのノードを追加したら、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の各インスタンスで sp_configure ストアド プロシージャを実行して処理を完了します。</span><span class="sxs-lookup"><span data-stu-id="176cd-116">After all the nodes are added, complete the process by executing the sp_configure stored procedure on each instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
5.  <span data-ttu-id="176cd-117">クラスターに別のノードを追加して有効にするには、いつでも手順 2.、3.、および 4. を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="176cd-117">To add and enable additional nodes to the cluster at any time, you can repeat steps 2, 3, and 4.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="176cd-118">参照</span><span class="sxs-lookup"><span data-stu-id="176cd-118">See Also</span></span>  
 <span data-ttu-id="176cd-119">[サーバー構成オプション &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="176cd-119">[Server Configuration Options &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="176cd-120">[新しい SQL Server フェールオーバー クラスターの作成 &#40;セットアップ&#41;](../../sql-server/failover-clusters/install/create-a-new-sql-server-failover-cluster-setup.md) </span><span class="sxs-lookup"><span data-stu-id="176cd-120">[Create a New SQL Server Failover Cluster &#40;Setup&#41;](../../sql-server/failover-clusters/install/create-a-new-sql-server-failover-cluster-setup.md) </span></span>  
 <span data-ttu-id="176cd-121">[SQL Server のフェールオーバー クラスター インスタンスの削除 &#40;セットアップ&#41;](../../sql-server/failover-clusters/install/remove-a-sql-server-failover-cluster-instance-setup.md) </span><span class="sxs-lookup"><span data-stu-id="176cd-121">[Remove a SQL Server Failover Cluster Instance &#40;Setup&#41;](../../sql-server/failover-clusters/install/remove-a-sql-server-failover-cluster-instance-setup.md) </span></span>  
 [<span data-ttu-id="176cd-122">SQL Server フェールオーバー クラスターでのノードの追加または削除 &#40;セットアップ&#41;</span><span class="sxs-lookup"><span data-stu-id="176cd-122">Add or Remove Nodes in a SQL Server Failover Cluster &#40;Setup&#41;</span></span>](../../sql-server/failover-clusters/install/add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md)  
  
  
