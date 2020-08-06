---
title: レプリケーション モニターの開始 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Replication Monitor, starting
ms.assetid: e037bd27-cc87-4ee9-9e5f-83f6d717cfa4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: cff23206923825d0e86e47ad6921c19f45e68b35
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741826"
---
# <a name="start-the-replication-monitor"></a><span data-ttu-id="d9989-102">レプリケーション モニターの開始</span><span class="sxs-lookup"><span data-stu-id="d9989-102">Start the Replication Monitor</span></span>
  <span data-ttu-id="d9989-103">レプリケーション モニターは、 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] から [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]の任意のインスタンスに対して起動するか、コマンド プロンプトから起動できます。</span><span class="sxs-lookup"><span data-stu-id="d9989-103">Replication Monitor can be started from [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] on any instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], or from the command prompt.</span></span> <span data-ttu-id="d9989-104">レプリケーション モニターを起動した後、1 つ以上のパブリッシャーをモニターに追加します。</span><span class="sxs-lookup"><span data-stu-id="d9989-104">After starting Replication Monitor, add one or more Publishers to monitor.</span></span> <span data-ttu-id="d9989-105">詳細については、「 [レプリケーション モニターのパブリッシャーの追加および削除](add-and-remove-publishers-from-replication-monitor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d9989-105">For more information, see [Add and Remove Publishers from Replication Monitor](add-and-remove-publishers-from-replication-monitor.md).</span></span>  
  
### <a name="to-start-replication-monitor-from-sql-server-management-studio"></a><span data-ttu-id="d9989-106">SQL Server Management Studio からレプリケーション モニターを起動するには</span><span class="sxs-lookup"><span data-stu-id="d9989-106">To start Replication Monitor from SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="d9989-107">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] で [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]のインスタンスに接続して、サーバー ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="d9989-107">Connect to an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="d9989-108">**[レプリケーション]** フォルダーまたはそのサブフォルダーを右クリックして、 **[レプリケーション モニターの起動]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d9989-108">Right-click the **Replication** folder or any of its subfolders, and then click **Launch Replication Monitor**.</span></span>  
  
### <a name="to-start-replication-monitor-from-the-command-prompt"></a><span data-ttu-id="d9989-109">コマンド プロンプトからレプリケーション モニターを起動するには</span><span class="sxs-lookup"><span data-stu-id="d9989-109">To start Replication Monitor from the command prompt</span></span>  
  
1.  <span data-ttu-id="d9989-110">コマンド プロンプトで、ツールをインストールしたディレクトリに移動します。</span><span class="sxs-lookup"><span data-stu-id="d9989-110">From the command prompt, navigate to the tools installation directory.</span></span> <span data-ttu-id="d9989-111">既定のパスは [!INCLUDE[ssInstallPath](../../../includes/ssinstallpath-md.md)]Tools\Binn\ です。</span><span class="sxs-lookup"><span data-stu-id="d9989-111">The default path is [!INCLUDE[ssInstallPath](../../../includes/ssinstallpath-md.md)]Tools\Binn\ .</span></span>  
  
2.  <span data-ttu-id="d9989-112">sqlmonitor.exe を実行します。</span><span class="sxs-lookup"><span data-stu-id="d9989-112">Run sqlmonitor.exe.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9989-113">参照</span><span class="sxs-lookup"><span data-stu-id="d9989-113">See Also</span></span>  
 [<span data-ttu-id="d9989-114">レプリケーションの監視</span><span class="sxs-lookup"><span data-stu-id="d9989-114">Monitoring Replication</span></span>](../monitoring-replication.md)  
  
  
