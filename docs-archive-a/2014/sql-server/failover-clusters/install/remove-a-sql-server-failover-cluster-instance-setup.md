---
title: SQL Server のフェールオーバー クラスター インスタンスの削除 (セットアップ) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- clusters [SQL Server], removing failover clustered instance
- failover clustering [SQL Server], removing failover clustered instance
- uninstalling failover clustered instances
- removing failover clustered instances
ms.assetid: bf63353b-69cf-4c5c-98ea-7b151e36537f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a4d0ae492481b0677be2d2692fbda0fbc8eb604b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640554"
---
# <a name="remove-a-sql-server-failover-cluster-instance-setup"></a><span data-ttu-id="4252d-102">SQL Server のフェールオーバー クラスター インスタンスの削除 (セットアップ)</span><span class="sxs-lookup"><span data-stu-id="4252d-102">Remove a SQL Server Failover Cluster Instance (Setup)</span></span>
  <span data-ttu-id="4252d-103">この手順を使用して、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のフェールオーバー クラスター インスタンスをアンインストールします。</span><span class="sxs-lookup"><span data-stu-id="4252d-103">Use this procedure to uninstall a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] failover clustered instance.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="4252d-104">フェールオーバー クラスターのすべてのノードにサービスとしてログインする権限を持つローカル管理者だけが、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] フェールオーバー クラスターを更新または削除できます。</span><span class="sxs-lookup"><span data-stu-id="4252d-104">To update or remove a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] failover cluster, you must be a local administrator with permission to login as a service on all nodes of the failover cluster.</span></span>  
  
 <span data-ttu-id="4252d-105">**Before you begin**</span><span class="sxs-lookup"><span data-stu-id="4252d-105">**Before you begin**</span></span>  
  
 <span data-ttu-id="4252d-106">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] フェールオーバー クラスターをアンインストールする前に、次の重要な点について検討します。</span><span class="sxs-lookup"><span data-stu-id="4252d-106">Consider the following important points before you uninstall a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] failover cluster:</span></span>  
  
-   <span data-ttu-id="4252d-107">誤って [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client をアンインストールすると、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] リソースを起動できなくなります。</span><span class="sxs-lookup"><span data-stu-id="4252d-107">If [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client is uninstalled by accident, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] resources will fail to start.</span></span> <span data-ttu-id="4252d-108">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client を再インストールするには、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] セットアップ プログラムを実行し、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] に必要なコンポーネントをインストールします。</span><span class="sxs-lookup"><span data-stu-id="4252d-108">To reinstall [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, run the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Setup program to install [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] prerequisites.</span></span>  
  
-   <span data-ttu-id="4252d-109">複数の SQL IP クラスター リソースを持つフェールオーバー クラスターをアンインストールする場合は、クラスター アドミニストレーターを使用してすべての SQL IP リソースを削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4252d-109">If you uninstall a failover cluster that has more than one SQL IP cluster resource, you must remove the additional SQL IP resources using cluster administrator.</span></span>  
  
 <span data-ttu-id="4252d-110">コマンドプロンプトの構文の詳細については、「 [Install SQL Server 2014 from The Command prompt](../../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4252d-110">For information about command prompt syntax, see [Install SQL Server 2014 from the Command Prompt](../../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md).</span></span>  
  
### <a name="to-uninstall-a-ssnoversion-failover-cluster"></a><span data-ttu-id="4252d-111">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] フェールオーバー クラスターをアンインストールには</span><span class="sxs-lookup"><span data-stu-id="4252d-111">To uninstall a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] failover cluster</span></span>  
  
1.  <span data-ttu-id="4252d-112">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] フェールオーバー クラスターをアンインストールするには、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] セットアップによって提供されるノードの削除機能を使用して、各ノードを個別に削除します。</span><span class="sxs-lookup"><span data-stu-id="4252d-112">To uninstall a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] failover cluster, use the Remove Node functionality provided by [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Setup to remove each node individually.</span></span> <span data-ttu-id="4252d-113">詳細については、「[SQL Server フェールオーバー クラスターでのノードの追加または削除 &#40;Setup&#41;](add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4252d-113">For more information, see [Add or Remove Nodes in a SQL Server Failover Cluster &#40;Setup&#41;](add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4252d-114">参照</span><span class="sxs-lookup"><span data-stu-id="4252d-114">See Also</span></span>  
 [<span data-ttu-id="4252d-115">SQL Server セットアップ ログ ファイルの表示と読み取り</span><span class="sxs-lookup"><span data-stu-id="4252d-115">View and Read SQL Server Setup Log Files</span></span>](../../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md)  
  
  
