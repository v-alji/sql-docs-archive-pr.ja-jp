---
title: 同期中のスクリプトの実行 (レプリケーション Transact-SQL プログラミング) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- synchronization [SQL Server replication], scripts
- scripts [SQL Server replication], synchronization and
- sp_addscriptexec
ms.assetid: b58a0877-4e43-4fab-a281-24e6022d3fb1
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4bc217ad160a0238cc4247600d65eb32f156071f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632358"
---
# <a name="execute-scripts-during-synchronization-replication-transact-sql-programming"></a><span data-ttu-id="d4c04-102">同期中のスクリプトの実行 (レプリケーション Transact-SQL プログラミング)</span><span class="sxs-lookup"><span data-stu-id="d4c04-102">Execute Scripts During Synchronization (Replication Transact-SQL Programming)</span></span>
  <span data-ttu-id="d4c04-103">レプリケーションでは、トランザクション パブリケーションおよびマージ パブリケーションのサブスクライバーに対し、要求時にスクリプトを実行できます。</span><span class="sxs-lookup"><span data-stu-id="d4c04-103">Replication supports on demand script execution for Subscribers to transactional and merge publications.</span></span> <span data-ttu-id="d4c04-104">スクリプトはレプリケーションの作業ディレクトリにコピーされ、サブスクライバー側で **sqlcmd** を使って適用されます。</span><span class="sxs-lookup"><span data-stu-id="d4c04-104">This functionality copies the script to the replication working directory and then uses **sqlcmd** to apply the script at the Subscriber.</span></span> <span data-ttu-id="d4c04-105">トランザクション パブリケーションのサブスクリプションに対してスクリプトを適用しているときにエラーが発生した場合、既定では、ディストリビューション エージェントの実行が停止します。</span><span class="sxs-lookup"><span data-stu-id="d4c04-105">By default, if there is a failure when applying the script for a subscription to a transactional publication, the Distribution Agent will stop.</span></span> <span data-ttu-id="d4c04-106">レプリケーションのストアド プロシージャを使用すると、指定した [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプトをプログラムから実行できます。</span><span class="sxs-lookup"><span data-stu-id="d4c04-106">You can specify a [!INCLUDE[tsql](../../includes/tsql-md.md)] script to execute programmatically using replication stored procedures.</span></span>  
  
### <a name="to-specify-a-script-to-run-for-all-subscribers-to-a-snapshot-transactional-or-merge-publication"></a><span data-ttu-id="d4c04-107">スナップショット、トランザクション、マージ パブリケーションのすべてのサブスクライバーに対して実行するスクリプトを指定するには</span><span class="sxs-lookup"><span data-stu-id="d4c04-107">To specify a script to run for all Subscribers to a snapshot, transactional or merge publication</span></span>  
  
1.  <span data-ttu-id="d4c04-108">要求時に実行する [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプトを作成およびテストします。</span><span class="sxs-lookup"><span data-stu-id="d4c04-108">Compose and test the [!INCLUDE[tsql](../../includes/tsql-md.md)] script that will be executed on demand.</span></span>  
  
2.  <span data-ttu-id="d4c04-109">スクリプト ファイルを、パブリケーションのスナップショット エージェントがアクセスできる場所に保存します。</span><span class="sxs-lookup"><span data-stu-id="d4c04-109">Save the script file to a location where it can be accessed by the Snapshot Agent for the publication.</span></span>  
  
3.  <span data-ttu-id="d4c04-110">パブリッシャー側のパブリケーション データベースに対して、[sp_addscriptexec &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addscriptexec-transact-sql) を実行します。</span><span class="sxs-lookup"><span data-stu-id="d4c04-110">At the Publisher on the publication database, execute [sp_addscriptexec &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addscriptexec-transact-sql).</span></span> <span data-ttu-id="d4c04-111">[ \*\* \@ パブリケーション**] を指定し、 \*\* \@ scriptfile**に手順 2. で作成した完全な UNC パスを含むスクリプトファイルの名前と、 \*\* \@ skiperror\*\*に次の値のいずれかを指定します。</span><span class="sxs-lookup"><span data-stu-id="d4c04-111">Specify **\@publication**, the name of the script file with full UNC path created in step 2 for **\@scriptfile**, and one of the following values for **\@skiperror**:</span></span>  
  
    -   <span data-ttu-id="d4c04-112">**0** - エラーが発生した場合、エージェントがスクリプトの実行を停止します。</span><span class="sxs-lookup"><span data-stu-id="d4c04-112">**0** - the agent will stop executing the script if an error is encountered.</span></span>  
  
    -   <span data-ttu-id="d4c04-113">**1** - エラーが発生した場合、エージェントによってエラー ログが記録され、スクリプトの実行が継続されます。</span><span class="sxs-lookup"><span data-stu-id="d4c04-113">**1** - the agent will log errors and continue executing the script when errors are encountered.</span></span>  
  
4.  <span data-ttu-id="d4c04-114">指定したスクリプトは、エージェントが次にサブスクリプションを同期するときに、各サブスクライバーで実行されます。</span><span class="sxs-lookup"><span data-stu-id="d4c04-114">The specified script will be executed at each Subscriber when the agent next runs to synchronize the subscription.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4c04-115">参照</span><span class="sxs-lookup"><span data-stu-id="d4c04-115">See Also</span></span>  
 [<span data-ttu-id="d4c04-116">データの同期</span><span class="sxs-lookup"><span data-stu-id="d4c04-116">Synchronize Data</span></span>](synchronize-data.md)  
  
  
